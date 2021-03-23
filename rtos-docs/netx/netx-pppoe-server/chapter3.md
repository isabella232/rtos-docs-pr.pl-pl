---
title: Rozdział 3 — Opis usług serwera Azure RTO NetX PPPoE
description: Ten rozdział zawiera opis wszystkich usług serwera usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822506"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="502d5-103">Rozdział 3 — Opis usług serwera Azure RTO NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="502d5-104">Ten rozdział zawiera opis wszystkich usług serwera usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="502d5-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="502d5-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="502d5-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="502d5-106">**nx_pppoe_server_create**: *Tworzenie wystąpienia serwera PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="502d5-107">**nx_pppoe_server_ac_name_set**: *Ustaw nazwę koncentratora dostępu*</span><span class="sxs-lookup"><span data-stu-id="502d5-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="502d5-108">**nx_pppoe_server_delete**: *usuwanie wystąpienia serwera PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="502d5-109">**nx_pppoe_server_enable**: *Włączanie usług serwera PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="502d5-110">**nx_pppoe_server_disable**: *Wyłącz usługi serwera PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="502d5-111">**nx_pppoe_server_callback_notify_set**: *Ustaw funkcje powiadamiania wywołania zwrotnego serwera PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="502d5-112">**nx_pppoe_server_service_name_set**: *Ustaw nazwę usługi serwera PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="502d5-113">**nx_pppoe_server_session_send**: *Wyślij dane serwera PPPoE do określonej sesji*</span><span class="sxs-lookup"><span data-stu-id="502d5-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="502d5-114">**nx_pppoe_server_session_packet_send**: *Wyślij pakiet serwera PPPoE do określonej sesji*</span><span class="sxs-lookup"><span data-stu-id="502d5-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="502d5-115">**nx_pppoe_server_session_terminate**: *Przerwij określoną sesję PPPoE*</span><span class="sxs-lookup"><span data-stu-id="502d5-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="502d5-116">**nx_pppoe_server_session_get**: *Pobierz informacje o określonej sesji*</span><span class="sxs-lookup"><span data-stu-id="502d5-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="502d5-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="502d5-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="502d5-118">Tworzenie wystąpienia serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-119">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="502d5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-120">Description</span></span>

<span data-ttu-id="502d5-121">Ta usługa tworzy wystąpienie serwera PPPoE z udostępnionym przez użytkownika sterownikiem linku dla określonego wystąpienia NetX IP.</span><span class="sxs-lookup"><span data-stu-id="502d5-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="502d5-122">Jeśli sterownik łącza nie został zainicjowany i włączono, oprogramowanie serwera PPPoE jest odpowiedzialne za Inicjowanie sterownika łącza.</span><span class="sxs-lookup"><span data-stu-id="502d5-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="502d5-123">Ponadto aplikacja musi dostarczyć wcześniej utworzoną pulę pakietów dla wystąpienia serwera PPPoE, które ma być używane na potrzeby wewnętrznej alokacji pakietów.</span><span class="sxs-lookup"><span data-stu-id="502d5-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="502d5-124">Należy pamiętać, że zwykle dobrym pomysłem jest utworzenie wątku IP NetX o wyższym priorytecie niż priorytet wątku serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="502d5-125">Aby uzyskać więcej informacji na temat określania priorytetu wątku IP, zapoznaj się z usługą *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="502d5-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-126">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-126">Input Parameters</span></span>

- <span data-ttu-id="502d5-127">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-128">**name**: Nazwa tego wystąpienia serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="502d5-129">**ip_ptr**: wskaźnik sterowania bloku dla wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="502d5-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="502d5-130">**interface_index**: indeks interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="502d5-131">**pppoe_link_driver**: Sterownik łącza podany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="502d5-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="502d5-132">**pool_ptr**: wskaźnik do puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="502d5-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="502d5-133">**stack_ptr**: wskaźnik do początku obszaru stosu wątku serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="502d5-134">**stack_size**: rozmiar w bajtach w stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="502d5-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="502d5-135">**priorytet**: priorytet wewnętrznych wątków serwera PPPoE (1-31).</span><span class="sxs-lookup"><span data-stu-id="502d5-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-136">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-136">Return Values</span></span>

- <span data-ttu-id="502d5-137">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślnie utworzono serwer PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="502d5-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) nieprawidłowy serwer PPPoE, adres IP, pulę pakietów lub wskaźnik stosu.</span><span class="sxs-lookup"><span data-stu-id="502d5-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="502d5-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Nieprawidłowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="502d5-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="502d5-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Nieprawidłowy rozmiar ładunku puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="502d5-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="502d5-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Nieprawidłowy rozmiar pamięci.</span><span class="sxs-lookup"><span data-stu-id="502d5-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="502d5-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) nieprawidłowy priorytet wątku serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-143">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-143">Allowed From</span></span>

<span data-ttu-id="502d5-144">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="502d5-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="502d5-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="502d5-147">Usuwanie wystąpienia serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="502d5-149">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-149">Description</span></span>

<span data-ttu-id="502d5-150">Ta usługa usuwa wcześniej utworzone wystąpienie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-151">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-151">Input Parameters</span></span>

- <span data-ttu-id="502d5-152">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-153">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-153">Return Values</span></span>

- <span data-ttu-id="502d5-154">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-156">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-156">Allowed From</span></span>

<span data-ttu-id="502d5-157">Wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="502d5-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="502d5-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="502d5-160">Włącz usługę serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="502d5-162">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-162">Description</span></span>

<span data-ttu-id="502d5-163">Ta usługa włącza usługi serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="502d5-164">Ta funkcja musi być wywoływana po *nx_pppoe_server_create* i *nx_pppoe_server_callback_notify_set*.</span><span class="sxs-lookup"><span data-stu-id="502d5-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-165">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-165">Input Parameters</span></span>

- <span data-ttu-id="502d5-166">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-167">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-167">Return Values</span></span>

- <span data-ttu-id="502d5-168">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-170">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-170">Allowed From</span></span>

<span data-ttu-id="502d5-171">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="502d5-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="502d5-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="502d5-174">Wyłącz usługę serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="502d5-176">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-176">Description</span></span>

<span data-ttu-id="502d5-177">Ta usługa wyłącza usługi serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-178">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-178">Input Parameters</span></span>

- <span data-ttu-id="502d5-179">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-180">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-180">Return Values</span></span>

- <span data-ttu-id="502d5-181">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-183">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-183">Allowed From</span></span>

<span data-ttu-id="502d5-184">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="502d5-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="502d5-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="502d5-187">Ustaw funkcje powiadamiania zwrotnego serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="502d5-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="502d5-189">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-189">Description</span></span>

<span data-ttu-id="502d5-190">Ta usługa ustawia funkcje powiadamiania zwrotnego serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="502d5-191">Ta funkcja musi zostać wywołana przed *nx_pppoe_server_enabl, a* wskaźnik funkcji pppoe_data_receive_notify musi być ustawiony, jeśli nie, *nx_pppoe_server_enable* będzie niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="502d5-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-192">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-192">Input Parameters</span></span>

- <span data-ttu-id="502d5-193">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-194">**pppoe_discover_initiation_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat o rozpoczęciu odnajdywania PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="502d5-195">Jeśli ta wartość jest RÓWNa NULL, funkcja wywołania zwrotnego inicjacji jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="502d5-196">**pppoe_discover_request_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat żądania odnajdowania PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="502d5-197">Jeśli ta wartość jest RÓWNa NULL, funkcja wywołania zwrotnego żądania wykrywania jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="502d5-198">**pppoe_discover_terminate_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat zakończenia odnajdywania PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="502d5-199">Jeśli ta wartość jest RÓWNa NULL, funkcja Wykryj zakończenie wywołania zwrotnego jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="502d5-200">**pppoe_discover_terminate_confirm**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie wysłany komunikat zakończenia odnajdywania PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="502d5-201">Jeśli ta wartość jest RÓWNa NULL, funkcja Wykryj zakończenie wywołania zwrotnego jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="502d5-202">**pppoe_data_receive_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat danych PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="502d5-203">Ta wartość nie może być równa zero.</span><span class="sxs-lookup"><span data-stu-id="502d5-203">This value must not be zero.</span></span>
- <span data-ttu-id="502d5-204">**pppoe_data_send_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie wysłany komunikat danych PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="502d5-205">Jeśli ta wartość jest RÓWNa NULL, funkcja wywołania zwrotnego wysyłania danych jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-206">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-206">Return Values</span></span>

- <span data-ttu-id="502d5-207">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE lub wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="502d5-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-209">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-209">Allowed From</span></span>

<span data-ttu-id="502d5-210">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-211">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="502d5-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="502d5-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="502d5-213">Ustaw nazwę koncentratora dostępu</span><span class="sxs-lookup"><span data-stu-id="502d5-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-214">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="502d5-215">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-215">Description</span></span>

<span data-ttu-id="502d5-216">Ta funkcja służy do ustawiania wywołania funkcji nazwa koncentratora dostępu.</span><span class="sxs-lookup"><span data-stu-id="502d5-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="502d5-217">Ciąg ac_name musi być zakończony wartością NULL i długość ac_name jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="502d5-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-218">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-218">Input Parameters</span></span>

- <span data-ttu-id="502d5-219">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-220">**ac_name**: Nazwa koncentratora dostępu.</span><span class="sxs-lookup"><span data-stu-id="502d5-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="502d5-221">**ac_name_length**: długość ac_ame.</span><span class="sxs-lookup"><span data-stu-id="502d5-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-222">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-222">Return Values</span></span>

- <span data-ttu-id="502d5-223">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślnie ustawiono serwer PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="502d5-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0XC1) nieprawidłowy serwer PPPoE, adres IP, pulę pakietów lub wskaźnik stosu.</span><span class="sxs-lookup"><span data-stu-id="502d5-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="502d5-225">**NX_SIZE_ERROR**: (0X09) sprawdzanie name_length nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="502d5-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-226">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-226">Allowed From</span></span>

<span data-ttu-id="502d5-227">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-228">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="502d5-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="502d5-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="502d5-230">Ustaw nazwę usługi serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-231">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="502d5-232">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-232">Description</span></span>

<span data-ttu-id="502d5-233">Ta usługa ustawia nazwę usługi serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-234">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-234">Input Parameters</span></span>

- <span data-ttu-id="502d5-235">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-236">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-236">Return Values</span></span>

- <span data-ttu-id="502d5-237">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-239">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-239">Allowed From</span></span>

<span data-ttu-id="502d5-240">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-241">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="502d5-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="502d5-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="502d5-243">Wyślij dane serwera PPPoE do określonej sesji</span><span class="sxs-lookup"><span data-stu-id="502d5-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-244">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="502d5-245">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-245">Description</span></span>

<span data-ttu-id="502d5-246">Ta usługa wysyła ramkę PPPoE przy użyciu określonego identyfikatora sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-247">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-247">Input Parameters</span></span>

- <span data-ttu-id="502d5-248">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-249">**session_index**: indeks sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="502d5-250">**data_ptr**: Wskaźnik początku ramki danych serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="502d5-251">**data_length**: długość ramki danych serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-252">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-252">Return Values</span></span>

- <span data-ttu-id="502d5-253">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="502d5-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) usługa serwerowa PPPoE nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="502d5-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="502d5-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="502d5-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-258">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-258">Allowed From</span></span>

<span data-ttu-id="502d5-259">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-260">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="502d5-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="502d5-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="502d5-262">Wyślij pakiet serwera PPPoE do określonej sesji</span><span class="sxs-lookup"><span data-stu-id="502d5-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-263">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="502d5-264">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-264">Description</span></span>

<span data-ttu-id="502d5-265">Ta usługa wysyła pakiet PPPoE przy użyciu określonego identyfikatora sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-266">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-266">Input Parameters</span></span>

- <span data-ttu-id="502d5-267">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-268">**session_index**: indeks sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="502d5-269">**packet_ptr**: wskaźnik do pakietu PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-270">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-270">Return Values</span></span>

- <span data-ttu-id="502d5-271">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="502d5-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) nieprawidłowy pakiet serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="502d5-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) usługa serwerowa PPPoE nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="502d5-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="502d5-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="502d5-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-277">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-277">Allowed From</span></span>

<span data-ttu-id="502d5-278">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-279">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="502d5-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="502d5-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="502d5-281">Przerwij określoną sesję PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-282">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="502d5-283">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-283">Description</span></span>

<span data-ttu-id="502d5-284">Ta usługa kończy określoną sesję PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-285">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-285">Input Parameters</span></span>

- <span data-ttu-id="502d5-286">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-287">**session_index**: indeks sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-288">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-288">Return Values</span></span>

- <span data-ttu-id="502d5-289">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="502d5-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) usługa serwerowa PPPoE nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="502d5-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="502d5-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="502d5-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="502d5-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-294">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-294">Allowed From</span></span>

<span data-ttu-id="502d5-295">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-296">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="502d5-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="502d5-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="502d5-298">Pobierz informacje o określonej sesji PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-299">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="502d5-300">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-300">Description</span></span>

<span data-ttu-id="502d5-301">Ta usługa pobiera określone informacje o sesji PPPoE, adres fizyczny klienta i identyfikator sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-302">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-302">Input Parameters</span></span>

- <span data-ttu-id="502d5-303">**pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="502d5-304">**session_index**: indeks sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="502d5-305">**client_mac_msw**: MSW adres fizyczny klienta.</span><span class="sxs-lookup"><span data-stu-id="502d5-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="502d5-306">**client_mac_lsw**: MSW adres fizyczny klienta.</span><span class="sxs-lookup"><span data-stu-id="502d5-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="502d5-307">**session_id**: wskaźnik identyfikatora sesji.</span><span class="sxs-lookup"><span data-stu-id="502d5-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-308">Return Values</span></span>

- <span data-ttu-id="502d5-309">**NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="502d5-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="502d5-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="502d5-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="502d5-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-313">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-313">Allowed From</span></span>

<span data-ttu-id="502d5-314">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-315">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="502d5-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="502d5-316">PppInitInd</span></span>

<span data-ttu-id="502d5-317">Skonfiguruj domyślną nazwę usługi</span><span class="sxs-lookup"><span data-stu-id="502d5-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="502d5-319">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-319">Description</span></span>

<span data-ttu-id="502d5-320">Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić programowi TTP skonfigurowanie "domyślnej nazwy usługi", która ma być używana przez protokół PPPoE do filtrowania przychodzących żądań PADI.</span><span class="sxs-lookup"><span data-stu-id="502d5-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="502d5-321">Oprogramowanie PPPoE powinno pamiętać o tych informacjach i w przypadku odebrania pakietu PADI zawierającego nazwę usługi, która jest zgodna z PppDiscoverReq.</span><span class="sxs-lookup"><span data-stu-id="502d5-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-322">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-322">Input Parameters</span></span>

- <span data-ttu-id="502d5-323">**Długość**: długość domyślnej nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="502d5-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="502d5-324">**aData**: domyślna nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="502d5-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-325">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-325">Return Values</span></span>

<span data-ttu-id="502d5-326">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-327">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-327">Allowed From</span></span>

<span data-ttu-id="502d5-328">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-329">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="502d5-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="502d5-330">PppDiscoverCnf</span></span>

<span data-ttu-id="502d5-331">Zdefiniuj pole Nazwa usługi dla pakietu PADO</span><span class="sxs-lookup"><span data-stu-id="502d5-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-332">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="502d5-333">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-333">Description</span></span>

<span data-ttu-id="502d5-334">Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić programowi TTP Definiowanie pola Nazwa usługi w pakiecie PADO.</span><span class="sxs-lookup"><span data-stu-id="502d5-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="502d5-335">Oprogramowanie PPPoE nie powinno wysyłać PADO do momentu wywołania PppDiscoverCnf.</span><span class="sxs-lookup"><span data-stu-id="502d5-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="502d5-336">Pakiet PADO musi zawierać nazwę koncentratora dostępu (przy użyciu identyfikatora znacznika 0x0102, zgodnie z definicją w RFC2516), zdefiniowaną podczas inicjalizacji oprogramowania PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="502d5-337">Wiele nazw usług można przekazywać w aData, a każda nazwa powinna być zakończona wartością null.</span><span class="sxs-lookup"><span data-stu-id="502d5-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="502d5-338">Znak null jest używany jako separator, aby zapewnić maksymalną elastyczność w przypadku, gdy inne polecenia muszą zostać przesłane jako część nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="502d5-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-339">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-339">Input Parameters</span></span>

- <span data-ttu-id="502d5-340">**Długość**: długość domyślnej nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="502d5-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="502d5-341">**aData**: domyślna nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="502d5-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="502d5-342">**interfaceHandle**: dojście do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-343">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-343">Return Values</span></span>

<span data-ttu-id="502d5-344">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-345">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-345">Allowed From</span></span>

<span data-ttu-id="502d5-346">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-347">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="502d5-348">PppOpenCnf</span><span class="sxs-lookup"><span data-stu-id="502d5-348">PppOpenCnf</span></span>

<span data-ttu-id="502d5-349">Akceptowanie lub odrzucanie sesji PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-350">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="502d5-351">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-351">Description</span></span>

<span data-ttu-id="502d5-352">Oprogramowanie PPPoE będzie uwidaczniać tę funkcję, aby umożliwić oprogramowaniu TTP akceptowanie lub odrzucanie sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="502d5-353">W odpowiedzi na ten stos PPPoE powinna akceptować połączenie i przypisywać unikatowy numer Session_ID PPPoE skojarzony z interfaceHandle.</span><span class="sxs-lookup"><span data-stu-id="502d5-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-354">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-354">Input Parameters</span></span>

- <span data-ttu-id="502d5-355">**Zaakceptuj**: NX_TRUE, jeśli połączenie ma zostać zaakceptowane.</span><span class="sxs-lookup"><span data-stu-id="502d5-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="502d5-356">**interfaceHandle**: dojście do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-357">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-357">Return Values</span></span>

<span data-ttu-id="502d5-358">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-359">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-359">Allowed From</span></span>

<span data-ttu-id="502d5-360">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-361">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="502d5-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="502d5-362">PppCloseInd</span></span>

<span data-ttu-id="502d5-363">Zamykanie sesji PPPoE</span><span class="sxs-lookup"><span data-stu-id="502d5-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="502d5-365">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-365">Description</span></span>

<span data-ttu-id="502d5-366">Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić programowi protokołu TTP zamknięcie sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="502d5-367">Oprogramowanie PPPoE wskaże ciąg kodu przyczyny w tagu Generic-Error (0x0203) w komunikacie PADT</span><span class="sxs-lookup"><span data-stu-id="502d5-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-368">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-368">Input Parameters</span></span>

- <span data-ttu-id="502d5-369">**interfaceHandle**: dojście do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="502d5-370">**causeCode**: pusty ciąg zakończony znakiem null służący do wysyłania informacji o przyczynie zamknięcia połączenia z serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-371">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-371">Return Values</span></span>

<span data-ttu-id="502d5-372">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-373">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-373">Allowed From</span></span>

<span data-ttu-id="502d5-374">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-375">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="502d5-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="502d5-376">PppCloseCnf</span></span>

<span data-ttu-id="502d5-377">Upewnij się, że dojście zostało zwolnione</span><span class="sxs-lookup"><span data-stu-id="502d5-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-378">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="502d5-379">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-379">Description</span></span>

<span data-ttu-id="502d5-380">Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić oprogramowaniu TTP potwierdzenie, że dojście zostało zwolnione.</span><span class="sxs-lookup"><span data-stu-id="502d5-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-381">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-381">Input Parameters</span></span>

- <span data-ttu-id="502d5-382">**interfaceHandle**: dojście do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-383">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-383">Return Values</span></span>

<span data-ttu-id="502d5-384">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-385">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-385">Allowed From</span></span>

<span data-ttu-id="502d5-386">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-387">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="502d5-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="502d5-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="502d5-389">Zezwalaj na potwierdzenie poprzednich danych PPP</span><span class="sxs-lookup"><span data-stu-id="502d5-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-390">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="502d5-391">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-391">Description</span></span>

<span data-ttu-id="502d5-392">Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić potwierdzenie poprzedzających PppTransmitDataReq.</span><span class="sxs-lookup"><span data-stu-id="502d5-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="502d5-393">Oznacza to, że oprogramowanie TTP jest gotowe do nowej ramki PPP z PPPoE.</span><span class="sxs-lookup"><span data-stu-id="502d5-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-394">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-394">Input Parameters</span></span>

- <span data-ttu-id="502d5-395">**interfaceHandle**: dojście do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="502d5-396">**aData**: wskaźnik bufora danych PPP, który został zaakceptowany.</span><span class="sxs-lookup"><span data-stu-id="502d5-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="502d5-397">**Packet_id**: identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="502d5-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-398">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-398">Return Values</span></span>

<span data-ttu-id="502d5-399">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-400">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-400">Allowed From</span></span>

<span data-ttu-id="502d5-401">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-402">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="502d5-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="502d5-403">PppReceiveDataInd</span></span>

<span data-ttu-id="502d5-404">Odbieraj dane z przesyłania za pośrednictwem sieci Ethernet</span><span class="sxs-lookup"><span data-stu-id="502d5-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="502d5-405">Prototype</span><span class="sxs-lookup"><span data-stu-id="502d5-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="502d5-406">Opis</span><span class="sxs-lookup"><span data-stu-id="502d5-406">Description</span></span>

<span data-ttu-id="502d5-407">Oprogramowanie PPPoE udostępni tę funkcję, aby odbierać dane do transmisji za pośrednictwem sieci Ethernet</span><span class="sxs-lookup"><span data-stu-id="502d5-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="502d5-408">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="502d5-408">Input Parameters</span></span>

- <span data-ttu-id="502d5-409">**interfaceHandle**: dojście do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="502d5-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="502d5-410">**Długość**: liczba bajtów w aData.</span><span class="sxs-lookup"><span data-stu-id="502d5-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="502d5-411">**aData**: bufor danych zawierający ramkę danych PPP.</span><span class="sxs-lookup"><span data-stu-id="502d5-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="502d5-412">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="502d5-412">Return Values</span></span>

<span data-ttu-id="502d5-413">**Brak**</span><span class="sxs-lookup"><span data-stu-id="502d5-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="502d5-414">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="502d5-414">Allowed From</span></span>

<span data-ttu-id="502d5-415">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="502d5-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="502d5-416">Przykład</span><span class="sxs-lookup"><span data-stu-id="502d5-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```