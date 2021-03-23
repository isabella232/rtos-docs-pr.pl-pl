---
title: Rozdział 4 — Opis usług translatora adresów sieciowych
description: Ten rozdział zawiera opis wszystkich usług interfejsu API NAT NetX Duo w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821756"
---
# <a name="chapter-4---description-of-nat-services"></a><span data-ttu-id="8ca32-103">Rozdział 4 — Opis usług translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-103">Chapter 4 - Description of NAT services</span></span>

<span data-ttu-id="8ca32-104">Ten rozdział zawiera opis wszystkich usług interfejsu API translacji adresów sieciowych NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="8ca32-104">This chapter contains a description of all NetX Duo NAT API services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="8ca32-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8ca32-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_nat_create"></a><span data-ttu-id="8ca32-106">nx_nat_create</span><span class="sxs-lookup"><span data-stu-id="8ca32-106">nx_nat_create</span></span>

<span data-ttu-id="8ca32-107">Tworzenie serwera NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-107">Create a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-108">Prototype</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a><span data-ttu-id="8ca32-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-109">Description</span></span>

<span data-ttu-id="8ca32-110">Ta usługa tworzy wystąpienie serwera NAT.</span><span class="sxs-lookup"><span data-stu-id="8ca32-110">This service creates an instance of the NAT server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-111">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-111">Input Parameters</span></span>

- <span data-ttu-id="8ca32-112">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych do utworzenia</span><span class="sxs-lookup"><span data-stu-id="8ca32-112">**nat_ptr** Pointer to NAT instance to create</span></span>
- <span data-ttu-id="8ca32-113">**Ip_ptr wskaźnika** do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="8ca32-113">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="8ca32-114">**global_interface_index** Indeksowanie do globalnego interfejsu sieciowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-114">**global_interface_index** Index to the global network interface</span></span>
- <span data-ttu-id="8ca32-115">**dynamic_cache_memory** Wskaźnik obszaru pamięci na tabelę NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-115">**dynamic_cache_memory** Pointer memory area to NAT table</span></span>
- <span data-ttu-id="8ca32-116">**dynamic_cache_size** Rozmiar obszaru pamięci dla tabeli NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-116">**dynamic_cache_size** Size of memory area for NAT table</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-117">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-117">Return Values</span></span>

- <span data-ttu-id="8ca32-118">**NX_SUCCESS** (0x00) serwer NAT został pomyślnie utworzony</span><span class="sxs-lookup"><span data-stu-id="8ca32-118">**NX_SUCCESS** (0x00) NAT server successfully created</span></span>
- <span data-ttu-id="8ca32-119">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-119">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="8ca32-120">NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="8ca32-120">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>
- <span data-ttu-id="8ca32-121">NX_NAT_CACHE_ERROR (0xD02) Nieprawidłowa wejściowa wskaźnik pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8ca32-121">NX_NAT_CACHE_ERROR (0xD02) Invalid cache pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-122">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-122">Allowed From</span></span>

<span data-ttu-id="8ca32-123">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-123">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-124">Example</span></span>

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a><span data-ttu-id="8ca32-125">nx_nat_delete</span><span class="sxs-lookup"><span data-stu-id="8ca32-125">nx_nat_delete</span></span>

<span data-ttu-id="8ca32-126">Usuwanie serwera NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-126">Delete a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-127">Prototype</span></span>

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="8ca32-128">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-128">Description</span></span>

<span data-ttu-id="8ca32-129">Ta usługa usuwa wcześniej utworzony serwer NAT.</span><span class="sxs-lookup"><span data-stu-id="8ca32-129">This service deletes a previously created NAT Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-130">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-130">Input Parameters</span></span>

- <span data-ttu-id="8ca32-131">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych do usunięcia</span><span class="sxs-lookup"><span data-stu-id="8ca32-131">**nat_ptr** Pointer to NAT instance to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-132">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-132">Return Values</span></span>

- <span data-ttu-id="8ca32-133">Pomyślnie usunięto translator adresów sieciowych **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8ca32-133">**NX_SUCCESS** (0x00) NAT successfully deleted</span></span>
- <span data-ttu-id="8ca32-134">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-134">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-135">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-135">Allowed From</span></span>

<span data-ttu-id="8ca32-136">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-136">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-137">Example</span></span>

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a><span data-ttu-id="8ca32-138">nx_nat_enable</span><span class="sxs-lookup"><span data-stu-id="8ca32-138">nx_nat_enable</span></span>

<span data-ttu-id="8ca32-139">Włącz wystąpienie protokołu IP dla translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-139">Enable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-140">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-140">Prototype</span></span>

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="8ca32-141">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-141">Description</span></span>

<span data-ttu-id="8ca32-142">Ta usługa włącza wystąpienie protokołu IP dla translatora adresów sieciowych (np. pakiety odebrane dalej do serwera NAT).</span><span class="sxs-lookup"><span data-stu-id="8ca32-142">This service enables the IP instance for NAT (e.g. forward received packets to the NAT server).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-143">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-143">Input Parameters</span></span>

- <span data-ttu-id="8ca32-144">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-144">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-145">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-145">Return Values</span></span>

- <span data-ttu-id="8ca32-146">**NX_SUCCESS** (0x00) translator adresów sieciowych został pomyślnie włączony</span><span class="sxs-lookup"><span data-stu-id="8ca32-146">**NX_SUCCESS** (0x00) NAT successfully enabled</span></span>
- <span data-ttu-id="8ca32-147">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-147">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-148">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-148">Allowed From</span></span>

<span data-ttu-id="8ca32-149">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-149">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-150">Example</span></span>

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a><span data-ttu-id="8ca32-151">nx_nat_disable</span><span class="sxs-lookup"><span data-stu-id="8ca32-151">nx_nat_disable</span></span>

<span data-ttu-id="8ca32-152">Wyłącz wystąpienie protokołu IP dla translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-152">Disable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-153">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-153">Prototype</span></span>

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="8ca32-154">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-154">Description</span></span>

<span data-ttu-id="8ca32-155">Ta usługa wyłącza translator adresów sieciowych w wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="8ca32-155">This service disables NAT on the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-156">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-156">Input Parameters</span></span>

- <span data-ttu-id="8ca32-157">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-157">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-158">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-158">Return Values</span></span>

- <span data-ttu-id="8ca32-159">**NX_SUCCESS** (0x00) translator adresów sieciowych został pomyślnie wyłączony</span><span class="sxs-lookup"><span data-stu-id="8ca32-159">**NX_SUCCESS** (0x00) NAT successfully disabled</span></span>
- <span data-ttu-id="8ca32-160">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-160">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-161">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-161">Allowed From</span></span>

<span data-ttu-id="8ca32-162">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-162">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-163">Example</span></span>

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a><span data-ttu-id="8ca32-164">nx_nat_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="8ca32-164">nx_nat_cache_notify_set</span></span>

<span data-ttu-id="8ca32-165">Ustawianie funkcji wywołania zwrotnego pełnych powiadomień pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8ca32-165">Set a cache full notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-166">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-166">Prototype</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a><span data-ttu-id="8ca32-167">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-167">Description</span></span>

<span data-ttu-id="8ca32-168">Ta usługa rejestruje pełne wywołanie zwrotne pamięci podręcznej za pomocą wskaźnika funkcji wejściowej cache_full_notify_cb, który wskazuje na zdefiniowaną przez użytkownika funkcję pełnego powiadamiania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8ca32-168">This service registers the cache full callback with the input function pointer cache_full_notify_cb which points to a user defined cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-169">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-169">Input Parameters</span></span>

- <span data-ttu-id="8ca32-170">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-170">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="8ca32-171">**cache_full_notify_cb** Wskaźnik do funkcji pełnego powiadamiania pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8ca32-171">**cache_full_notify_cb** Pointer to cache full notify function</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-172">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-172">Return Values</span></span>

- <span data-ttu-id="8ca32-173">Pomyślnie ustawiono pełną funkcję powiadamiania pamięci podręcznej **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8ca32-173">**NX_SUCCESS** (0x00) Cache full notify function successfully set</span></span>
- <span data-ttu-id="8ca32-174">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-174">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="8ca32-175">NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="8ca32-175">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-176">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-176">Allowed From</span></span>

<span data-ttu-id="8ca32-177">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-177">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-178">Example</span></span>

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a><span data-ttu-id="8ca32-179">nx_nat_inbound_entry_create</span><span class="sxs-lookup"><span data-stu-id="8ca32-179">nx_nat_inbound_entry_create</span></span>

<span data-ttu-id="8ca32-180">Tworzenie wpisu przychodzącego w tabeli translacji NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-180">Create an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-181">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a><span data-ttu-id="8ca32-182">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-182">Description</span></span>

<span data-ttu-id="8ca32-183">Ta usługa tworzy wpis przychodzący jako statyczny (trwały wpis, nigdy nie wygasa) i dodaje go do tabeli translacji NAT.</span><span class="sxs-lookup"><span data-stu-id="8ca32-183">This service creates an inbound entry as static (permanent entry, never expires) and adds it to the NAT translation table.</span></span> <span data-ttu-id="8ca32-184">Te wpisy są zwykle tworzone dla serwerów hosta lokalnego, w których połączenie jest inicjowane z hosta w sieci zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="8ca32-184">These entries are usually created for local host servers where a connection is initiated from a host on the outside network.</span></span> <span data-ttu-id="8ca32-185">Serwer NAT sprawdza, czy port zewnętrzny nie jest już używany w tabeli translacji lub jest powiązany przez wcześniej istniejące gniazdo NetX Duo tego samego protokołu.</span><span class="sxs-lookup"><span data-stu-id="8ca32-185">The NAT server checks that the external port is not already in use in the translation table or bound by a previously existing NetX Duo socket of the same protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-186">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-186">Input Parameters</span></span>

- <span data-ttu-id="8ca32-187">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-187">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="8ca32-188">**entry_ptr** Wskaźnik do wpisu tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="8ca32-188">**entry_ptr** Pointer to translation entry</span></span>
- <span data-ttu-id="8ca32-189">**local_ip_address** Adres IP hosta lokalnego</span><span class="sxs-lookup"><span data-stu-id="8ca32-189">**local_ip_address** Local host IP address</span></span>
- <span data-ttu-id="8ca32-190">**external_port** Port docelowy w sieci zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="8ca32-190">**external_port** Destination port on the external network</span></span>
- <span data-ttu-id="8ca32-191">**local_port** Port źródłowy (hosta lokalnego)</span><span class="sxs-lookup"><span data-stu-id="8ca32-191">**local_port** Source (local host) port</span></span>
- <span data-ttu-id="8ca32-192">**Protokół** Protokół pakietów (np. TCP)</span><span class="sxs-lookup"><span data-stu-id="8ca32-192">**protocol** Packet protocol (e.g TCP)</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-193">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-193">Return Values</span></span>

- <span data-ttu-id="8ca32-194">Pomyślnie utworzono wpis **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8ca32-194">**NX_SUCCESS** (0x00) Entry successfully created</span></span>
- <span data-ttu-id="8ca32-195">**NX_NAT_PORT_UNAVAILABLE** (0XD0D) nieprawidłowy port zewnętrzny</span><span class="sxs-lookup"><span data-stu-id="8ca32-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) Invalid external port</span></span>
- <span data-ttu-id="8ca32-196">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-196">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="8ca32-197">NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="8ca32-197">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-198">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-198">Allowed From</span></span>

<span data-ttu-id="8ca32-199">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-199">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-200">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-200">Example</span></span>

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a><span data-ttu-id="8ca32-201">nx_nat_inbound_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8ca32-201">nx_nat_inbound_entry_delete</span></span>

<span data-ttu-id="8ca32-202">Usuwanie wpisu przychodzącego w tabeli translacji NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-202">Delete an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="8ca32-203">Prototype</span><span class="sxs-lookup"><span data-stu-id="8ca32-203">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a><span data-ttu-id="8ca32-204">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca32-204">Description</span></span>

<span data-ttu-id="8ca32-205">Ta usługa usuwa określony wpis przychodzący z tabeli translacji.</span><span class="sxs-lookup"><span data-stu-id="8ca32-205">This service deletes the specified inbound entry from the translation table.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8ca32-206">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8ca32-206">Input Parameters</span></span>

- <span data-ttu-id="8ca32-207">**nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych</span><span class="sxs-lookup"><span data-stu-id="8ca32-207">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="8ca32-208">**delete_entry_ptr** Wskaźnik do wpisu translacji NAT</span><span class="sxs-lookup"><span data-stu-id="8ca32-208">**delete_entry_ptr** Pointer to the NAT translation entry</span></span>

### <a name="return-values"></a><span data-ttu-id="8ca32-209">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8ca32-209">Return Values</span></span>

- <span data-ttu-id="8ca32-210">Pomyślnie usunięto wpis **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8ca32-210">**NX_SUCCESS** (0x00) Entry successfully deleted</span></span>
- <span data-ttu-id="8ca32-211">Nie znaleziono wpisu **NX_NAT_ENTRY_NOT_FOUND** (0xD04)</span><span class="sxs-lookup"><span data-stu-id="8ca32-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entry does not found</span></span>
- <span data-ttu-id="8ca32-212">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="8ca32-212">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="8ca32-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Nieprawidłowy typ tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="8ca32-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Invalid translation type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8ca32-214">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8ca32-214">Allowed From</span></span>

<span data-ttu-id="8ca32-215">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ca32-215">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8ca32-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca32-216">Example</span></span>

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
