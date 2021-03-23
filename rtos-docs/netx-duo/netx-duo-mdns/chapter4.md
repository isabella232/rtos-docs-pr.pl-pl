---
title: Rozdział 4 — Opis usług mDNS
description: Ten rozdział zawiera opis wszystkich usług NetX mDNS
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821822"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="c49ca-103">Rozdział 4 — Opis usług mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="c49ca-104">Ten rozdział zawiera opis wszystkich usług NetX mDNS (wymienionych poniżej).</span><span class="sxs-lookup"><span data-stu-id="c49ca-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="c49ca-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c49ca-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="c49ca-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="c49ca-106">nx_mdns_create</span></span>

<span data-ttu-id="c49ca-107">Tworzenie wystąpienia mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="c49ca-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-109">Description</span></span>

<span data-ttu-id="c49ca-110">Ta usługa tworzy wystąpienie mDNS dla określonego wystąpienia IP i skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c49ca-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="c49ca-111">Tworzony jest również wątek do obsługi przychodzących komunikatów mDNS, reagowanie na zapytania i okresowe przesyłanie komunikatów zapytań.</span><span class="sxs-lookup"><span data-stu-id="c49ca-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-112">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-112">Input Parameters</span></span>

- <span data-ttu-id="c49ca-113">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-114">**ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="c49ca-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="c49ca-115">**packet_pool** Wskaźnik do prawidłowej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="c49ca-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="c49ca-116">**priorytet** Priorytet wątku mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="c49ca-117">**stack_ptr** Wskaźnik do obszaru stosu dla wątku mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="c49ca-118">**stack_size** Rozmiar obszaru stosu.</span><span class="sxs-lookup"><span data-stu-id="c49ca-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="c49ca-119">**HOST_NAME** Nazwa hosta przypisana do tego węzła.</span><span class="sxs-lookup"><span data-stu-id="c49ca-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="c49ca-120">**local_service_cache** Miejsce do magazynowania lokalnych usług zarejestrowanych.</span><span class="sxs-lookup"><span data-stu-id="c49ca-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="c49ca-121">**local_service_cache_size** Rozmiar pamięci podręcznej usługi lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="c49ca-122">**peer_service_cache** Odebrano miejsce do magazynowania informacji o usłudze</span><span class="sxs-lookup"><span data-stu-id="c49ca-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="c49ca-123">**peer_service_cache_size** Rozmiar pamięci podręcznej usługi równorzędnej</span><span class="sxs-lookup"><span data-stu-id="c49ca-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="c49ca-124">**probing_notify** Opcjonalna funkcja wywołania zwrotnego wywołana na końcu operacji sondowania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="c49ca-125">Powiadamia o tym, czy nazwa hosta (w przypadku włączania usługi mDNS w interfejsie lokalnym), czy nazwa usługi (po zarejestrowaniu usłudze) jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="c49ca-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-126">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-126">Return Values</span></span>

- <span data-ttu-id="c49ca-127">**NX_SUCCESS** (0X00) pomyślnie utworzył wystąpienie mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-128">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-128">Allowed From</span></span>

<span data-ttu-id="c49ca-129">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="c49ca-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="c49ca-131">nx_mdns_delete</span></span>

<span data-ttu-id="c49ca-132">Usuwanie wystąpienia programu mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-133">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="c49ca-134">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-134">Description</span></span>

<span data-ttu-id="c49ca-135">Ta usługa usuwa wystąpienie usługi mDNS i zwalnia jego zasoby.</span><span class="sxs-lookup"><span data-stu-id="c49ca-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-136">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-136">Input Parameters</span></span>

- <span data-ttu-id="c49ca-137">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-138">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-138">Return Values</span></span>

- <span data-ttu-id="c49ca-139">**NX_SUCCESS** (0X00) pomyślnie usunął wystąpienie mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-140">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-140">Allowed From</span></span>

<span data-ttu-id="c49ca-141">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="c49ca-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="c49ca-143">nx_mdns_enable</span></span>

<span data-ttu-id="c49ca-144">Uruchom usługę mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-145">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="c49ca-146">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-146">Description</span></span>

<span data-ttu-id="c49ca-147">Ten interfejs API umożliwia włączenie usługi mDNS w określonym interfejsie fizycznym.</span><span class="sxs-lookup"><span data-stu-id="c49ca-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="c49ca-148">Po włączeniu usługi moduł mDNS najpierw sonduje wszystkie unikatowe nazwy usług w sieci przed odpowiedzią na zapytania odebrane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-149">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-149">Input Parameters</span></span>

- <span data-ttu-id="c49ca-150">**mdns_ptr** Wskaźnik do bloku sterowania wystąpieniem mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="c49ca-151">**interface_index** Indeksowanie do interfejsu, w którym usługa jest włączona</span><span class="sxs-lookup"><span data-stu-id="c49ca-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-152">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-152">Return Values</span></span>

- <span data-ttu-id="c49ca-153">**NX_SUCCESS** (0X00) pomyślnie włączył usługę.</span><span class="sxs-lookup"><span data-stu-id="c49ca-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-154">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-154">Allowed From</span></span>

<span data-ttu-id="c49ca-155">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="c49ca-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="c49ca-157">nx_mdns_disable</span></span>

<span data-ttu-id="c49ca-158">Wyłącz usługę mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="c49ca-160">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-160">Description</span></span>

<span data-ttu-id="c49ca-161">Ten interfejs API powoduje wyłączenie usługi mDNS w określonym interfejsie fizycznym.</span><span class="sxs-lookup"><span data-stu-id="c49ca-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="c49ca-162">Po wyłączeniu usługi Usługa mDNS wysyła komunikaty "pożegnania" dla każdej usługi lokalnej do sieci dołączonej do interfejsu, dzięki czemu węzły sąsiednie zostaną powiadomione.</span><span class="sxs-lookup"><span data-stu-id="c49ca-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-163">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-163">Input Parameters</span></span>

- <span data-ttu-id="c49ca-164">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-165">**interface_index** Indeksowanie do interfejsu, w którym usługa ma zostać wyłączona</span><span class="sxs-lookup"><span data-stu-id="c49ca-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-166">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-166">Return Values</span></span>

- <span data-ttu-id="c49ca-167">**NX_SUCCESS** (0X00) pomyślnie wyłączyła usługę.</span><span class="sxs-lookup"><span data-stu-id="c49ca-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-168">Allowed From</span></span>

<span data-ttu-id="c49ca-169">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="c49ca-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="c49ca-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="c49ca-172">Instaluje funkcję pełnego powiadamiania pamięci podręcznej mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="c49ca-174">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-174">Description</span></span>

<span data-ttu-id="c49ca-175">Ta usługa instaluje funkcję wywołania zwrotnego, która jest wywoływana, gdy lokalna pamięć podręczna lub pamięć podręczna usługi równorzędnej staną się pełne.</span><span class="sxs-lookup"><span data-stu-id="c49ca-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="c49ca-176">Gdy pamięć podręczna usługi jest pełna, nie można dodać więcej rekordów zasobów usług mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="c49ca-177">Należy pamiętać, że pamięć podręczna usługi może stać się pełna w wyniku wewnętrznej fragmentacji, gdy zostaną dodane i usunięte usługi o różnych długościach ciągu.</span><span class="sxs-lookup"><span data-stu-id="c49ca-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="c49ca-178">W przypadku odebrania pamięci podręcznej pełnych powiadomień w pamięci podręcznej usługi równorzędnej aplikacja może używać usługi "*nx_mdns_service_cache_clear"* do wymazywania wszystkich wpisów w pamięci podręcznej usługi równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-179">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-179">Input Parameters</span></span>

- <span data-ttu-id="c49ca-180">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-181">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-181">Return Values</span></span>

- <span data-ttu-id="c49ca-182">**NX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego powiadomienia pamięci podręcznej mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-183">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-183">Allowed From</span></span>

<span data-ttu-id="c49ca-184">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="c49ca-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="c49ca-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="c49ca-187">Wyczyść funkcję pełnego powiadamiania pamięci podręcznej usługi mDNS</span><span class="sxs-lookup"><span data-stu-id="c49ca-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="c49ca-189">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-189">Description</span></span>

<span data-ttu-id="c49ca-190">Ta usługa czyści funkcję wywołania zwrotnego powiadomienia pamięci podręcznej usługi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c49ca-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-191">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-191">Input Parameters</span></span>

- <span data-ttu-id="c49ca-192">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-193">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-193">Return Values</span></span>

- <span data-ttu-id="c49ca-194">**NX_SUCCESS** (0X00) pomyślnie wyczyścił funkcję wywołania zwrotnego powiadomienia pamięci podręcznej usługi mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-195">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-195">Allowed From</span></span>

<span data-ttu-id="c49ca-196">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="c49ca-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="c49ca-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="c49ca-199">Ustawia nazwę domeny</span><span class="sxs-lookup"><span data-stu-id="c49ca-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="c49ca-201">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-201">Description</span></span>

<span data-ttu-id="c49ca-202">Ta usługa ustawia domyślną nazwę domeny lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="c49ca-203">Po utworzeniu wystąpienia programu mDNS domyślna nazwa domeny lokalnej jest ustawiona na wartość ". local".</span><span class="sxs-lookup"><span data-stu-id="c49ca-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="c49ca-204">Ten interfejs API umożliwia aplikacji zastąpienie domyślnej nazwy domeny lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-205">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-205">Input Parameters</span></span>

- <span data-ttu-id="c49ca-206">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-207">**domain_name** Nazwa domeny, która ma zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="c49ca-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-208">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-208">Return Values</span></span>

- <span data-ttu-id="c49ca-209">**NX_SUCCESS** (0X00) pomyślnie skonfigurował domenę lokalną.</span><span class="sxs-lookup"><span data-stu-id="c49ca-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-210">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-210">Allowed From</span></span>

<span data-ttu-id="c49ca-211">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-212">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="c49ca-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="c49ca-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="c49ca-214">Ustawia parametry czasu dla komunikatów anonsów usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-215">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="c49ca-216">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-216">Description</span></span>

<span data-ttu-id="c49ca-217">Ta usługa ponownie konfiguruje parametry chronometrażu wykorzystywane przez usługę mDNS podczas wysyłania anonsów usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="c49ca-218">Okres publikacji rozpoczyna się od *t* taktów i może być rozszerzony telescopically z 2 do potęgi współczynnika *k* .</span><span class="sxs-lookup"><span data-stu-id="c49ca-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="c49ca-219">Liczba powtórzeń na anonsie to *p*, interwał między każdym powtarzanym anonsem to cykle *interwału* , a liczba okresów anonsu jest max_time.</span><span class="sxs-lookup"><span data-stu-id="c49ca-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="c49ca-220">Domyślnie okres początkowy jest ustawiony na 1 sekundę, z k = 1 (okres podwaja się za każdym razem), *p = 1* (bez powtórzenia), retrans_interval = 0 (bez interwału czasu), Period_interval = 0xFFFFFFFF (interwał okresu maksymalnego) i max_time = 3 (liczba anonsów).</span><span class="sxs-lookup"><span data-stu-id="c49ca-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-221">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-221">Input Parameters</span></span>

- <span data-ttu-id="c49ca-222">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-223">**Liczba** taktów dla okresu początkowego.</span><span class="sxs-lookup"><span data-stu-id="c49ca-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="c49ca-224">Wartość domyślna to 100 Takty dla 1 sekundy.</span><span class="sxs-lookup"><span data-stu-id="c49ca-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="c49ca-225">**Liczba** powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="c49ca-225">**p** Number of repetitions.</span></span> <span data-ttu-id="c49ca-226">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="c49ca-226">Default value is 1.</span></span>
- <span data-ttu-id="c49ca-227">**TELESCOPIC.**</span><span class="sxs-lookup"><span data-stu-id="c49ca-227">**k** Telescopic factor.</span></span> <span data-ttu-id="c49ca-228">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="c49ca-228">Default value is 1.</span></span>
- <span data-ttu-id="c49ca-229">**retrans_interval** Liczba taktów oczekiwania przed wysłaniem kolejnych komunikatów powiadomień.</span><span class="sxs-lookup"><span data-stu-id="c49ca-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="c49ca-230">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="c49ca-230">Default value is 0.</span></span>
- <span data-ttu-id="c49ca-231">**period_interval** Liczba znaczników między dwoma okresami anonsu.</span><span class="sxs-lookup"><span data-stu-id="c49ca-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="c49ca-232">Wartość domyślna to 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="c49ca-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="c49ca-233">**max_time** Liczba okresów anonsów, które mają być używane w anonsie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="c49ca-234">Po upływie *max_time* okresy anonsów nie są wysyłane żadne komunikaty o anonsie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="c49ca-235">Wartość domyślna to 3.</span><span class="sxs-lookup"><span data-stu-id="c49ca-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-236">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-236">Return Values</span></span>

- <span data-ttu-id="c49ca-237">**NX_SUCCESS** (0X00) pomyślnie ustawia wartości chronometrażu.</span><span class="sxs-lookup"><span data-stu-id="c49ca-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-238">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-238">Allowed From</span></span>

<span data-ttu-id="c49ca-239">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-240">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="c49ca-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="c49ca-241">nx_mdns_service_add</span></span>

<span data-ttu-id="c49ca-242">Dodawanie usługi lokalnej</span><span class="sxs-lookup"><span data-stu-id="c49ca-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-243">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="c49ca-244">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-244">Description</span></span>

<span data-ttu-id="c49ca-245">Ten interfejs API rejestruje usługę oferowaną przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c49ca-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="c49ca-246">Jeśli flaga *is_unique* jest ustawiona, usługa mDNS sonduje nazwę usługi, aby upewnić się, że jest unikatowa w sieci lokalnej przed rozpoczęciem anonsowania usługi w sieci.</span><span class="sxs-lookup"><span data-stu-id="c49ca-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="c49ca-247">*Wystąpienie* jest częścią nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="c49ca-248">*Usługa* jest częścią nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="c49ca-249">Na przykład "_http. _tcp" to usługa.</span><span class="sxs-lookup"><span data-stu-id="c49ca-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="c49ca-250">Aby opisać usługę z podtypem, obiekt wywołujący musi używać parametru *podtypu* .</span><span class="sxs-lookup"><span data-stu-id="c49ca-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="c49ca-251">Na przykład jeśli żądana usługa to "_PRINTER. _sub. _http. _tcp", pole usługi to "_http. _tcp:, a pole podtyp ma wartość" _PRINTER ".</span><span class="sxs-lookup"><span data-stu-id="c49ca-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-252">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-252">Input Parameters</span></span>

- <span data-ttu-id="c49ca-253">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-254">**wystąpienie** Wskaźnik na nazwę wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="c49ca-255">**Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="c49ca-256">**podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="c49ca-257">**priorytet** Priorytet usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-257">**priority** Service priority</span></span>
- <span data-ttu-id="c49ca-258">**waga** Waga usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-258">**weight** Service weight</span></span>
- <span data-ttu-id="c49ca-259">**port** Numer portu TCP lub UDP używający usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="c49ca-260">**tekst** Dodatkowe informacje tekstowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-260">**text** Additional text information</span></span>
- <span data-ttu-id="c49ca-261">**is_unique** Flaga logiczna wskazująca, czy usługa jest udostępniona, czy unikatowa.</span><span class="sxs-lookup"><span data-stu-id="c49ca-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="c49ca-262">W przypadku usług zarejestrowanych jako unikatowy usługa mDNS musi sondować usługę w sieci przed rozpoczęciem jej tworzenia.</span><span class="sxs-lookup"><span data-stu-id="c49ca-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="c49ca-263">**Interface_index** Interfejs fizyczny oferowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="c49ca-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="c49ca-264">W przypadku usługi, która jest oferowana za pomocą dowolnych dołączonych usług, wartość *NX_MDNS_ALL_INTERFACES* jest używana.</span><span class="sxs-lookup"><span data-stu-id="c49ca-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-265">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-265">Return Values</span></span>

- <span data-ttu-id="c49ca-266">**NX_SUCCESS** (0X00) pomyślnie zarejestrowała usługę.</span><span class="sxs-lookup"><span data-stu-id="c49ca-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-267">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-267">Allowed From</span></span>

<span data-ttu-id="c49ca-268">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-269">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="c49ca-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="c49ca-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="c49ca-271">Usuwanie poprzedniej zarejestrowanej usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-272">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="c49ca-273">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-273">Description</span></span>

<span data-ttu-id="c49ca-274">Ten interfejs API umożliwia usunięcie poprzedniej zarejestrowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="c49ca-275">Po usunięciu usługi do sieci lokalnej są wysyłane komunikaty "pożegnania", dzięki czemu węzły sąsiednie zostaną powiadomione.</span><span class="sxs-lookup"><span data-stu-id="c49ca-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-276">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-276">Input Parameters</span></span>

- <span data-ttu-id="c49ca-277">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-278">**wystąpienie** Wskaźnik na nazwę wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="c49ca-279">**Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="c49ca-280">**podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-281">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-281">Return Values</span></span>

- <span data-ttu-id="c49ca-282">**NX_SUCCESS** (0X00) pomyślnie usunął usługę.</span><span class="sxs-lookup"><span data-stu-id="c49ca-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-283">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-283">Allowed From</span></span>

<span data-ttu-id="c49ca-284">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-285">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="c49ca-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="c49ca-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="c49ca-287">Inicjowanie odnajdywania usługi w jednym zrzucie</span><span class="sxs-lookup"><span data-stu-id="c49ca-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c49ca-289">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-289">Description</span></span>

<span data-ttu-id="c49ca-290">Ta usługa wykonuje jednorazowe zapytanie mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="c49ca-291">Jeśli określona usługa zostanie znaleziona w pamięci podręcznej usługi równorzędnej, zostanie zwrócone pierwsze wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="c49ca-292">Jeśli żadne usługi nie zostaną znalezione w lokalnej pamięci podręcznej usługi równorzędnej, moduł mDNS wystawia polecenie zapytania i poczeka na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="c49ca-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="c49ca-293">Usługa jest blokowana do momentu odebrania pierwszej odpowiedzi lub przeprowadzenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-294">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-294">Input Parameters</span></span>

- <span data-ttu-id="c49ca-295">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-296">**wystąpienie** Wskaźnik na nazwę wystąpienia usługi, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="c49ca-297">**Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="c49ca-298">Aplikacja musi określić typ usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-298">the application must specify the service type.</span></span>
- <span data-ttu-id="c49ca-299">**podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="c49ca-300">**service_ptr** Wskaźnik podanego przez użytkownika do struktury NX_MDNS_SERVICE, która przechowuje wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="c49ca-301">**WAIT_OPTION** Ilość czasu (w taktach) oczekiwania na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="c49ca-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-302">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-302">Return Values</span></span>

- <span data-ttu-id="c49ca-303">**NX_SUCCESS** (0X00) pomyślnie uzyskał informacje o usłudze.</span><span class="sxs-lookup"><span data-stu-id="c49ca-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-304">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-304">Allowed From</span></span>

<span data-ttu-id="c49ca-305">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-306">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="c49ca-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="c49ca-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="c49ca-308">Inicjowanie ciągłego odnajdowania usług</span><span class="sxs-lookup"><span data-stu-id="c49ca-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-309">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="c49ca-310">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-310">Description</span></span>

<span data-ttu-id="c49ca-311">Ta usługa uruchamia ciągłe zapytanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-311">This service starts a continuous query.</span></span> <span data-ttu-id="c49ca-312">Należy pamiętać, że usługa wraca natychmiast.</span><span class="sxs-lookup"><span data-stu-id="c49ca-312">Note that the service returns immediately.</span></span> <span data-ttu-id="c49ca-313">Po wydaniu ciągłego zapytania aplikacja może pobrać rekord usługi przy użyciu *nx_mdns_service_lookup* interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="c49ca-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="c49ca-314">Aby zatrzymać ciągłe zapytania, aplikacja może używać interfejsu API *nx_mdns_service_query_stop*</span><span class="sxs-lookup"><span data-stu-id="c49ca-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-315">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-315">Input Parameters</span></span>

- <span data-ttu-id="c49ca-316">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-317">**wystąpienie** Wskaźnik na nazwę wystąpienia usługi, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="c49ca-318">**Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="c49ca-319">**podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-320">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-320">Return Values</span></span>

- <span data-ttu-id="c49ca-321">**NX_SUCCESS** (0X00) pomyślnie rozpoczęła zapytanie Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="c49ca-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-322">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-322">Allowed From</span></span>

<span data-ttu-id="c49ca-323">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-324">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="c49ca-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="c49ca-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="c49ca-326">Zaniechanie poprzednio wystawionego ciągłego odnajdowania usług</span><span class="sxs-lookup"><span data-stu-id="c49ca-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-327">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="c49ca-328">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-328">Description</span></span>

<span data-ttu-id="c49ca-329">Ten interfejs API kończy poprzednie wygenerowane ciągłe odnajdywanie usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-330">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-330">Input Parameters</span></span>

- <span data-ttu-id="c49ca-331">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-332">**wystąpienie** Wskaźnik na nazwę wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="c49ca-333">**Usługa** Wskaźnik do typu usługi mDNS, informacje o podtypie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="c49ca-334">**podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-335">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-335">Return Values</span></span>

- <span data-ttu-id="c49ca-336">**NX_SUCCESS** (0X00) pomyślnie zatrzymano zapytanie Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="c49ca-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-337">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-337">Allowed From</span></span>

<span data-ttu-id="c49ca-338">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-339">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="c49ca-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="c49ca-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="c49ca-341">Pobiera usługę z lokalnej pamięci podręcznej usługi równorzędnej</span><span class="sxs-lookup"><span data-stu-id="c49ca-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-342">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="c49ca-343">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-343">Description</span></span>

<span data-ttu-id="c49ca-344">Ta usługa wyszukuje usługi pasujące do nazwy wystąpienia (jeśli jest podany) i typu usługi w lokalnej pamięci podręcznej usługi równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="c49ca-345">Aplikacja uruchamia wyszukiwanie usługi z *instance_index* ustawiona na zero dla pierwszej usługi w pamięci podręcznej, która jest zgodna z opisem.</span><span class="sxs-lookup"><span data-stu-id="c49ca-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="c49ca-346">Aplikacja utrzymuje korzystanie z tej usługi z rosnącą *instance_index* wartością dla dodatkowych usług znalezionych w pamięci podręcznej, aż usługa zwróci *NX_NO_MORE_ENTRIES*, co wskazuje na koniec pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-347">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-347">Input Parameters</span></span>

- <span data-ttu-id="c49ca-348">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-349">**wystąpienie** Wskaźnik na nazwę wystąpienia usługi, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="c49ca-350">**Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="c49ca-351">**podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="c49ca-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="c49ca-352">**Instance_index** Numer indeksu do wystąpienia, które ma zostać zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c49ca-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="c49ca-353">**service_ptr** Wskaźnik podanego przez użytkownika do struktury NX_MDNS_SERVICE, która przechowuje wyniki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-354">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-354">Return Values</span></span>

- <span data-ttu-id="c49ca-355">**NX_SUCCESS** (0X00) pomyślnie pobrała usługę</span><span class="sxs-lookup"><span data-stu-id="c49ca-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="c49ca-356">**NX_NO_MORE_ENTRIES** (0X17) nie znaleziono wpisu usługi o określonym numerze indeksu.</span><span class="sxs-lookup"><span data-stu-id="c49ca-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="c49ca-357">Ten kod błędu wskazuje koniec wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-358">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-358">Allowed From</span></span>

<span data-ttu-id="c49ca-359">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-360">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="c49ca-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="c49ca-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="c49ca-362">Konfiguruje zestaw ignorowanych usług</span><span class="sxs-lookup"><span data-stu-id="c49ca-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-363">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="c49ca-364">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-364">Description</span></span>

<span data-ttu-id="c49ca-365">Ten interfejs API konfiguruje maskę w celu ignorowania usług określonych przez *service_maską* maskę bitów.</span><span class="sxs-lookup"><span data-stu-id="c49ca-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="c49ca-366">Użytkownik może opcjonalnie użyć service_mask, aby wybrać typy usług, które nie mają być buforowane.</span><span class="sxs-lookup"><span data-stu-id="c49ca-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="c49ca-367">Lista usług jest definiowana w tabeli *nx_mdns_service_types* w *nxd_mdns. c.*</span><span class="sxs-lookup"><span data-stu-id="c49ca-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="c49ca-368">Odpowiednia maska pierwszego typu usługi w nx_mdns_service_types [] jest 0x00000001, maska drugiego typu usługi to 0x00000002 itd.</span><span class="sxs-lookup"><span data-stu-id="c49ca-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-369">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-369">Input Parameters</span></span>

- <span data-ttu-id="c49ca-370">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-371">**service_mask** Typy usług zdefiniowane przez użytkownika do ignorowania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="c49ca-372">Maska jest 32-bitowym typem ULONG.</span><span class="sxs-lookup"><span data-stu-id="c49ca-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="c49ca-373">Każdy bit reprezentuje wpis w tablicy *nx_mdns_service_types* zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c49ca-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="c49ca-374">Jeśli ustawiono bit, odpowiedni typ usługi określony w tablicy *nx_mdns_service_type* nie będzie przechowywany w pamięci podręcznej usługi równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-375">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-375">Return Values</span></span>

- <span data-ttu-id="c49ca-376">**NX_SUCCESS** (0X00) pomyślnie Ustawia maskę ignorowania usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-377">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-377">Allowed From</span></span>

<span data-ttu-id="c49ca-378">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-379">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="c49ca-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="c49ca-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="c49ca-381">Konfiguruje funkcję wywołania zwrotnego powiadomienia o zmianie usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-382">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="c49ca-383">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-383">Description</span></span>

<span data-ttu-id="c49ca-384">Ten interfejs API umożliwia skonfigurowanie funkcji wywołania zwrotnego powiadomienia o zmianie usługi.</span><span class="sxs-lookup"><span data-stu-id="c49ca-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="c49ca-385">Ta funkcja wywołania zwrotnego jest wywoływana, gdy usługa oferowana przez inne węzły w sieci zostanie dodana, zmieniona lub nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="c49ca-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="c49ca-386">Użytkownik może opcjonalnie użyć service_mask, aby wybrać typy usług, które chcą monitorować.</span><span class="sxs-lookup"><span data-stu-id="c49ca-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="c49ca-387">Lista monitorowanych usług jest trwale kodowana w tabeli *nx_mdns_service_types* w *nxd_mdns. c.*</span><span class="sxs-lookup"><span data-stu-id="c49ca-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="c49ca-388">Odpowiednia maska pierwszego typu usługi w nx_mdns_service_types [] jest 0x00000001, maska drugiego typu usługi to 0x00000002 itd.</span><span class="sxs-lookup"><span data-stu-id="c49ca-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-389">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-389">Input Parameters</span></span>

- <span data-ttu-id="c49ca-390">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-391">**service_mask** Zdefiniowane przez użytkownika typy usługi do monitorowania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="c49ca-392">Maska jest 32-bitowym typem ULONG.</span><span class="sxs-lookup"><span data-stu-id="c49ca-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="c49ca-393">Każdy bit reprezentuje wpis w tablicy *nx_mdns_service_types* .</span><span class="sxs-lookup"><span data-stu-id="c49ca-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="c49ca-394">**service_change_notify** Funkcja wywołania zwrotnego do wywołania, gdy określona usługa zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="c49ca-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="c49ca-395">Szczegółowe informacje o usłudze są zwracane w pamięci wskazywanej przez *service_ptr.*</span><span class="sxs-lookup"><span data-stu-id="c49ca-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="c49ca-396">Należy zauważyć, że zawartość pamięci jest nieprawidłowa po powrocie z funkcji powiadamiania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c49ca-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-397">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-397">Return Values</span></span>

- <span data-ttu-id="c49ca-398">**NX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c49ca-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-399">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-399">Allowed From</span></span>

<span data-ttu-id="c49ca-400">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-401">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="c49ca-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="c49ca-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="c49ca-403">Wyczyść funkcję wywołania zwrotnego powiadomienia o zmianie usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="c49ca-405">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-405">Description</span></span>

<span data-ttu-id="c49ca-406">Ten interfejs API czyści funkcję wywołania zwrotnego powiadomienia o zmianie usługi i.</span><span class="sxs-lookup"><span data-stu-id="c49ca-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-407">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-407">Input Parameters</span></span>

- <span data-ttu-id="c49ca-408">**mdns_ptr** Wskaźnik do bloku sterowania mDNS...</span><span class="sxs-lookup"><span data-stu-id="c49ca-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-409">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-409">Return Values</span></span>

- <span data-ttu-id="c49ca-410">**NX_SUCCESS** (0X00) pomyślnie wyczyścił funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c49ca-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-411">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-411">Allowed From</span></span>

<span data-ttu-id="c49ca-412">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-413">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="c49ca-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="c49ca-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="c49ca-415">Pobierz adres hosta</span><span class="sxs-lookup"><span data-stu-id="c49ca-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-416">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c49ca-417">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-417">Description</span></span>

<span data-ttu-id="c49ca-418">Ta usługa wykonuje zapytanie mDNS dotyczące adresów IPv4 hosta i IPv6.</span><span class="sxs-lookup"><span data-stu-id="c49ca-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="c49ca-419">Jeśli adres określonej nazwy hosta zostanie znaleziony w pamięci podręcznej usługi równorzędnej, zostanie zwrócony adres.</span><span class="sxs-lookup"><span data-stu-id="c49ca-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="c49ca-420">Jeśli żaden adres nie zostanie znaleziony w pamięci podręcznej usługi równorzędnej, moduł mDNS wystawia zapytania typu AAAA i i poczeka na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="c49ca-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="c49ca-421">Ten interfejs API blokuje do momentu odebrania odpowiedzi lub przełączenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-422">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-422">Input Parameters</span></span>

- <span data-ttu-id="c49ca-423">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="c49ca-424">**HOST_NAME** Wskaźnik na nazwę hosta.</span><span class="sxs-lookup"><span data-stu-id="c49ca-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="c49ca-425">**ipv4_address** Wskaźnik na adres 4-bajtowy wyrównany do miejsca do magazynowania adresów IPv4.</span><span class="sxs-lookup"><span data-stu-id="c49ca-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="c49ca-426">Użytkownik przydziela 4 bajty miejsca na adres IPv4.</span><span class="sxs-lookup"><span data-stu-id="c49ca-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="c49ca-427">Adres NX_NULL można przesłać do tego interfejsu API, jeśli aplikacja nie musi pobrać adresu IPv4.</span><span class="sxs-lookup"><span data-stu-id="c49ca-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="c49ca-428">**ipv6_address** Wskaźnik na adres IPv6 dla miejsca do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="c49ca-429">Użytkownik przydziela 16-bajtowe miejsce dla adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="c49ca-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="c49ca-430">Adres NX_NULL można przesłać do tego interfejsu API, jeśli aplikacja nie musi pobrać adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="c49ca-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="c49ca-431">**WAIT_OPTION** Ilość czasu (w taktach) oczekiwania na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="c49ca-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-432">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-432">Return Values</span></span>

- <span data-ttu-id="c49ca-433">**NX_SUCCESS** (0X00) pomyślnie uzyskał adres hosta.</span><span class="sxs-lookup"><span data-stu-id="c49ca-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-434">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-434">Allowed From</span></span>

<span data-ttu-id="c49ca-435">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-436">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="c49ca-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="c49ca-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="c49ca-438">Wymaż wszystkie usługi lokalne</span><span class="sxs-lookup"><span data-stu-id="c49ca-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-439">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="c49ca-440">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-440">Description</span></span>

<span data-ttu-id="c49ca-441">Ta usługa czyści wszystkie wpisy w lokalnej pamięci podręcznej usługi po wysłaniu wiadomości do pożegnania.</span><span class="sxs-lookup"><span data-stu-id="c49ca-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-442">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-442">Input Parameters</span></span>

- <span data-ttu-id="c49ca-443">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-444">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-444">Return Values</span></span>

- <span data-ttu-id="c49ca-445">**NX_SUCCESS** (0X00) pomyślnie wymazuje wszystkie wpisy w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-446">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-446">Allowed From</span></span>

<span data-ttu-id="c49ca-447">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-448">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="c49ca-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="c49ca-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="c49ca-450">Wymaż wszystkie odnalezione usługi</span><span class="sxs-lookup"><span data-stu-id="c49ca-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="c49ca-451">Prototype</span><span class="sxs-lookup"><span data-stu-id="c49ca-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="c49ca-452">Opis</span><span class="sxs-lookup"><span data-stu-id="c49ca-452">Description</span></span>

<span data-ttu-id="c49ca-453">Ta usługa czyści wszystkie wpisy w pamięci podręcznej usługi równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c49ca-454">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c49ca-454">Input Parameters</span></span>

- <span data-ttu-id="c49ca-455">**mdns_ptr** Wskaźnik do bloku sterowania mDNS.</span><span class="sxs-lookup"><span data-stu-id="c49ca-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c49ca-456">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c49ca-456">Return Values</span></span>

- <span data-ttu-id="c49ca-457">**NX_SUCCESS** (0X00) pomyślnie wymazuje wszystkie wpisy w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c49ca-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c49ca-458">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c49ca-458">Allowed From</span></span>

<span data-ttu-id="c49ca-459">Wątki</span><span class="sxs-lookup"><span data-stu-id="c49ca-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c49ca-460">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49ca-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
