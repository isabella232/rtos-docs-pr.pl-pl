---
title: Rozdział 3 — Opis usług klienta RTO NetX PPPoE platformy Azure
description: Ten rozdział zawiera opis wszystkich usług klienta usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821493"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="361d9-103">Rozdział 3 — Opis usług klienta RTO NetX PPPoE platformy Azure</span><span class="sxs-lookup"><span data-stu-id="361d9-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="361d9-104">Ten rozdział zawiera opis wszystkich usług klienta usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="361d9-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="361d9-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="361d9-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="361d9-106">**nx_pppoe_client_create** *utworzyć wystąpienia klienta PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="361d9-107">**nx_pppoe_client_delete** *usunąć wystąpienia klienta PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="361d9-108">**nx_pppoe_client_host_uniq_set** *ustawić hosta unikatowego dla klienta PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="361d9-109">**nx_pppoe_client_host_uniq_set_extended** *ustawić hosta unikatowego dla klienta PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="361d9-110">**nx_pppoe_client_service_name_set** *ustawić nazwę usługi dla klienta PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="361d9-111">**nx_pppoe_client_service_name_set_extended** *ustawić nazwę usługi dla klienta PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="361d9-112">**nx_pppoe_client_session_connect** *łączenie sesji klienta PPPoE z serwerem PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="361d9-113">**nx_pppoe_client_session_packet_send** *wysłać pakietu sesji PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="361d9-114">**nx_pppoe_client_session_terminate** *przerywanie sesji PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="361d9-115">**nx_pppoe_client_session_get** *uzyskać określonego pliku inf sesji PPPoE*</span><span class="sxs-lookup"><span data-stu-id="361d9-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="361d9-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="361d9-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="361d9-117">Tworzenie wystąpienia klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-118">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="361d9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-119">Description</span></span>

<span data-ttu-id="361d9-120">Ta usługa tworzy wystąpienie klienta PPPoE z dostarczonym przez użytkownika sterownikiem linku dla określonego wystąpienia NetX IP.</span><span class="sxs-lookup"><span data-stu-id="361d9-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="361d9-121">Jeśli sterownik łącza nie został zainicjowany i włączono, oprogramowanie klienckie PPPoE jest odpowiedzialne za Inicjowanie sterownika łącza.</span><span class="sxs-lookup"><span data-stu-id="361d9-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="361d9-122">Ponadto aplikacja musi dostarczyć wcześniej utworzoną pulę pakietów dla wystąpienia klienta PPPoE, które ma być używane na potrzeby wewnętrznej alokacji pakietów.</span><span class="sxs-lookup"><span data-stu-id="361d9-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-123">Ogólnie dobrym pomysłem jest utworzenie wątku IP NetX o wyższym priorytecie niż priorytet wątku klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="361d9-124">Aby uzyskać więcej informacji na temat określania priorytetu wątku IP, zapoznaj się z usługą *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="361d9-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-125">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-125">Input Parameters</span></span>

 - <span data-ttu-id="361d9-126">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-127">**Nazwa** Nazwa tego wystąpienia klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="361d9-128">**ip_ptr** Wskaźnik sterowania blokiem dla wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="361d9-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="361d9-129">**interface_index** Indeks interfejsu.</span><span class="sxs-lookup"><span data-stu-id="361d9-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="361d9-130">**pool_ptr** Wskaźnik do puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="361d9-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="361d9-131">**stack_ptr** Wskaźnik do początku obszaru stosu wątku klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="361d9-132">**stack_size** Rozmiar w bajtach w stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="361d9-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="361d9-133">**priorytet** Priorytet wewnętrznych wątków klienta PPPoE (1-31).</span><span class="sxs-lookup"><span data-stu-id="361d9-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="361d9-134">**pppoe_link_driver** Sterownik linku dostarczony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="361d9-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="361d9-135">**pppoe_packet_receive** Funkcja odbierania pakietów dostarczonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="361d9-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-136">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-136">Return Values</span></span>

 - <span data-ttu-id="361d9-137">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie utworzono klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="361d9-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) nieprawidłowy klient PPPoE, adres IP, Pula pakietów lub wskaźnik stosu.</span><span class="sxs-lookup"><span data-stu-id="361d9-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="361d9-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Nieprawidłowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="361d9-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="361d9-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Nieprawidłowy rozmiar ładunku puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="361d9-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="361d9-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Nieprawidłowy rozmiar pamięci.</span><span class="sxs-lookup"><span data-stu-id="361d9-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="361d9-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) nieprawidłowy priorytet wątku klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-143">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-143">Allowed From</span></span>

<span data-ttu-id="361d9-144">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="361d9-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="361d9-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="361d9-147">Usuwanie wystąpienia klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="361d9-149">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-149">Description</span></span>

<span data-ttu-id="361d9-150">Ta usługa usuwa poprzednio utworzone wystąpienie klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-151">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-151">Input Parameters</span></span>

 - <span data-ttu-id="361d9-152">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-153">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-153">Return Values</span></span>

 - <span data-ttu-id="361d9-154">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślne usunięcie klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="361d9-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-156">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-156">Allowed From</span></span>

<span data-ttu-id="361d9-157">Wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="361d9-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="361d9-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="361d9-160">Ustaw unikatowy Host klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="361d9-162">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-162">Description</span></span>

<span data-ttu-id="361d9-163">Ta usługa ustawia unikatowy Host klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="361d9-164">Host-Uniq jest używana przez hosta do unikatowego kojarzenia koncentratora dostępu z określonym żądaniem hosta.</span><span class="sxs-lookup"><span data-stu-id="361d9-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="361d9-165">Mogą to być dane binarne dowolnej wartości i długości wybranych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="361d9-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-166">unikatowy host musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-167">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="361d9-167">This service is deprecated.</span></span> <span data-ttu-id="361d9-168">Deweloperzy są zachęcani do migracji do *nx_pppoe_client_host_uniq_set_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="361d9-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-169">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-169">Input Parameters</span></span>

 - <span data-ttu-id="361d9-170">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-171">**host_uniq** Na hoście unikatowym wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="361d9-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="361d9-172">Unikatowy host musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-173">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-173">Return Values</span></span>

 - <span data-ttu-id="361d9-174">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiony unikatowy Host klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="361d9-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-176">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-176">Allowed From</span></span>

<span data-ttu-id="361d9-177">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="361d9-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="361d9-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="361d9-180">Ustaw unikatowy Host klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="361d9-182">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-182">Description</span></span>

<span data-ttu-id="361d9-183">Ta usługa ustawia unikatowy Host klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="361d9-184">Host-Uniq jest używana przez hosta do unikatowego kojarzenia koncentratora dostępu z określonym żądaniem hosta.</span><span class="sxs-lookup"><span data-stu-id="361d9-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="361d9-185">Mogą to być dane binarne dowolnej wartości i długości wybranych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="361d9-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-186">unikatowy host musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-187">Ta usługa zastępuje *nx_pppoe_client_host_uniq_set ()*.</span><span class="sxs-lookup"><span data-stu-id="361d9-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="361d9-188">Ta wersja dostarcza dodatkowe informacje o długości do usługi.</span><span class="sxs-lookup"><span data-stu-id="361d9-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-189">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-189">Input Parameters</span></span>

 - <span data-ttu-id="361d9-190">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-191">**host_uniq** Na hoście unikatowym wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="361d9-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="361d9-192">Unikatowy host musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="361d9-193">**host_uniq_length** Długość host_uniq</span><span class="sxs-lookup"><span data-stu-id="361d9-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-194">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-194">Return Values</span></span>

 - <span data-ttu-id="361d9-195">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiony unikatowy Host klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="361d9-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="361d9-197">Sprawdzanie **NX_SIZE_ERROR** (0x09) nie powiodło się host_uniq_length</span><span class="sxs-lookup"><span data-stu-id="361d9-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-198">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-198">Allowed From</span></span>

<span data-ttu-id="361d9-199">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-200">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="361d9-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="361d9-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="361d9-202">Ustaw nazwę usługi klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-203">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="361d9-204">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-204">Description</span></span>

<span data-ttu-id="361d9-205">Ta usługa ustawia nazwę usługi klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="361d9-206">Service-Name wskazujący usługę żądaną przez hosta.</span><span class="sxs-lookup"><span data-stu-id="361d9-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="361d9-207">Jeśli nie ustawiono Service-Name, oznacza to, że host będzie akceptować dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="361d9-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-208">Nazwa usługi musi być ciągiem zakończonym wartością null</span><span class="sxs-lookup"><span data-stu-id="361d9-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-209">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="361d9-209">This service is deprecated.</span></span> <span data-ttu-id="361d9-210">Deweloperzy są zachęcani do migracji do *nx_pppoe_client_service_name_set_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="361d9-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-211">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-211">Input Parameters</span></span>

 - <span data-ttu-id="361d9-212">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-213">**service_name** Wskaźnik na nazwę usługi.</span><span class="sxs-lookup"><span data-stu-id="361d9-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="361d9-214">Nazwa usługi musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-215">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-215">Return Values</span></span>

 - <span data-ttu-id="361d9-216">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiono nazwę usługi klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="361d9-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-218">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-218">Allowed From</span></span>

<span data-ttu-id="361d9-219">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-220">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="361d9-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="361d9-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="361d9-222">Ustaw nazwę usługi klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-223">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="361d9-224">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-224">Description</span></span>

<span data-ttu-id="361d9-225">Ta usługa ustawia nazwę usługi klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="361d9-226">Service-Name wskazujący usługę żądaną przez hosta.</span><span class="sxs-lookup"><span data-stu-id="361d9-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="361d9-227">Jeśli nie ustawiono Service-Name, oznacza to, że host będzie akceptować dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="361d9-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-228">Nazwa usługi musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-229">Ta usługa zastępuje *nx_pppoe_client_service_name_set ()*.</span><span class="sxs-lookup"><span data-stu-id="361d9-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="361d9-230">Ta wersja dostarcza dodatkowe informacje o długości nazwy usługi do funkcji.</span><span class="sxs-lookup"><span data-stu-id="361d9-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-231">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-231">Input Parameters</span></span>

 - <span data-ttu-id="361d9-232">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-233">**service_name** Wskaźnik na nazwę usługi.</span><span class="sxs-lookup"><span data-stu-id="361d9-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="361d9-234">Nazwa usługi musi mieć ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="361d9-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="361d9-235">**service_name_length** Długość service_name</span><span class="sxs-lookup"><span data-stu-id="361d9-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-236">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-236">Return Values</span></span>

 - <span data-ttu-id="361d9-237">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiono nazwę usługi klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="361d9-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="361d9-239">Sprawdzanie **NX_SIZE_ERROR** (0x09) nie powiodło się service_name_length</span><span class="sxs-lookup"><span data-stu-id="361d9-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-240">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-240">Allowed From</span></span>

<span data-ttu-id="361d9-241">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-242">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="361d9-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="361d9-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="361d9-244">Łączenie sesji klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="361d9-246">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-246">Description</span></span>

<span data-ttu-id="361d9-247">Ta usługa umożliwia połączenie sesji PPPoE przy użyciu wcześniej utworzonego klienta PPPoE z określonym serwerem PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="361d9-248">Ta funkcja musi być wywoływana po *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* i *nx_pppoe_client_service_name_set*.</span><span class="sxs-lookup"><span data-stu-id="361d9-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-249">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-249">Input Parameters</span></span>

 - <span data-ttu-id="361d9-250">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-251">**WAIT_OPTION** Opcja oczekiwania podczas ustanawiania połączenia.</span><span class="sxs-lookup"><span data-stu-id="361d9-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-252">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-252">Return Values</span></span>

 - <span data-ttu-id="361d9-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) pomyślna sesja klienta z klientem PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="361d9-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-255">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-255">Allowed From</span></span>

<span data-ttu-id="361d9-256">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-257">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="361d9-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="361d9-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="361d9-259">Wyślij pakiet klienta PPPoE do określonej sesji</span><span class="sxs-lookup"><span data-stu-id="361d9-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-260">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="361d9-261">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-261">Description</span></span>

<span data-ttu-id="361d9-262">Ta usługa wysyła pakiet PPPoE przy użyciu określonego identyfikatora sesji.</span><span class="sxs-lookup"><span data-stu-id="361d9-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-263">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-263">Input Parameters</span></span>

 - <span data-ttu-id="361d9-264">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-265">**packet_ptr** Wskaźnik na pakiet PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-266">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-266">Return Values</span></span>

 - <span data-ttu-id="361d9-267">**NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślne wysłanie pakietu klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="361d9-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="361d9-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) nieprawidłowy pakiet klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="361d9-270">Sesja PPPoE NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) nie została ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="361d9-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-271">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-271">Allowed From</span></span>

<span data-ttu-id="361d9-272">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-273">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="361d9-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="361d9-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="361d9-275">Przerwij sesję klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-276">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="361d9-277">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-277">Description</span></span>

<span data-ttu-id="361d9-278">Ta usługa kończy określoną sesję PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-279">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-279">Input Parameters</span></span>

 - <span data-ttu-id="361d9-280">**pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-281">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-281">Return Values</span></span>

 - <span data-ttu-id="361d9-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) pomyślna przerwa sesja klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="361d9-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-284">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-284">Allowed From</span></span>

<span data-ttu-id="361d9-285">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-286">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="361d9-287">nx_pppoe_client_session_get</span><span class="sxs-lookup"><span data-stu-id="361d9-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="361d9-288">Pobierz informacje o określonej sesji PPPoE</span><span class="sxs-lookup"><span data-stu-id="361d9-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="361d9-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="361d9-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="361d9-290">Opis</span><span class="sxs-lookup"><span data-stu-id="361d9-290">Description</span></span>

<span data-ttu-id="361d9-291">Ta usługa pobiera określone informacje o sesji PPPoE, adres fizyczny serwera i identyfikator sesji.</span><span class="sxs-lookup"><span data-stu-id="361d9-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="361d9-292">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="361d9-292">Input Parameters</span></span>

 - <span data-ttu-id="361d9-293">**pppoe_server_ptr** Wskaźnik do bloku kontroli klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="361d9-294">**server_mac_msw** Wskaźnik MSW adresu fizycznego serwera.</span><span class="sxs-lookup"><span data-stu-id="361d9-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="361d9-295">**server_mac_lsw** Wskaźnik MSW adresu fizycznego serwera.</span><span class="sxs-lookup"><span data-stu-id="361d9-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="361d9-296">**session_id** Wskaźnik identyfikatora sesji.</span><span class="sxs-lookup"><span data-stu-id="361d9-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="361d9-297">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="361d9-297">Return Values</span></span>

 - <span data-ttu-id="361d9-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) pomyślna sesja klienta PPPoE get.</span><span class="sxs-lookup"><span data-stu-id="361d9-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="361d9-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.</span><span class="sxs-lookup"><span data-stu-id="361d9-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="361d9-300">Sesja PPPoE NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) nie została ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="361d9-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="361d9-301">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="361d9-301">Allowed From</span></span>

<span data-ttu-id="361d9-302">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="361d9-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="361d9-303">Przykład</span><span class="sxs-lookup"><span data-stu-id="361d9-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
