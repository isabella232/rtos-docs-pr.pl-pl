---
title: Rozdział 4 — Opis usług Azure RTO NetX Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821546"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="8dd59-103">Rozdział 4 — Opis usług Azure RTO NetX Services</span><span class="sxs-lookup"><span data-stu-id="8dd59-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="8dd59-104">Ten rozdział zawiera opis wszystkich usług Azure RTO NetX w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="8dd59-105">Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="8dd59-106">Na przykład wszystkie usługi ARP znajdują się na początku tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="8dd59-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="8dd59-107">*Należy pamiętać, że interfejs API usługi BSD-Compatible Socket jest dostępny dla starszego kodu aplikacji, który nie może w pełni korzystać z interfejsu API NetX o wysokiej wydajności. Aby uzyskać więcej informacji na temat interfejsu API BSD-Compatible gniazda, zobacz Dodatek D.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="8dd59-108">W sekcji "wartości zwracane" w każdym opisie wartości **pogrubione** nie wpływają na wartość opcji NX_DISABLE_ERROR_CHECKING używanej do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości w trybie niepogrubionym są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="8dd59-109">Sekcje "dozwolone od" wskazują, z których można wywołać każdą usługę NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="8dd59-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="8dd59-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="8dd59-111">Unieważnienie wszystkich wpisów dynamicznych w pamięci podręcznej ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-112">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-113">Description</span></span>

<span data-ttu-id="8dd59-114">Ta usługa unieważnia wszystkie dynamiczne wpisy ARP znajdujące się obecnie w pamięci podręcznej ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-115">Parameters</span></span>

- <span data-ttu-id="8dd59-116">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-117">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-117">Return Values</span></span>

- <span data-ttu-id="8dd59-118">**NX_SUCCESS** (0X00) pomyślne unieważnienie pamięci podręcznej ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="8dd59-119">**NX_NOT_ENABLED** (0X14) ARP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="8dd59-120">**NX_PTR_ERROR** (0X07) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-121">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-122">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-122">Allowed From</span></span>

<span data-ttu-id="8dd59-123">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-124">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-124">Preemption Possible</span></span>

<span data-ttu-id="8dd59-125">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-125">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-127">See Also</span></span>

- <span data-ttu-id="8dd59-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="8dd59-129">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="8dd59-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="8dd59-133">Ustawianie dynamicznego wpisu ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-134">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="8dd59-135">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-135">Description</span></span>

<span data-ttu-id="8dd59-136">Ta usługa przydziela dynamiczny wpis z pamięci podręcznej ARP i konfiguruje określony adres IP na potrzeby mapowania adresów fizycznych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="8dd59-137">Jeśli określony jest zerowy adres fizyczny, do sieci wysyłane jest rzeczywiste żądanie ARP w celu rozpoznania adresu fizycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="8dd59-138">Należy również zauważyć, że ten wpis zostanie usunięty, jeśli przedawnienie ARP jest aktywne lub jeśli pamięć podręczna ARP jest wyczerpana i jest to najmniej ostatnio używany wpis ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-139">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-139">Parameters</span></span>

- <span data-ttu-id="8dd59-140">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-141">**IP_address** Adres IP do zamapowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="8dd59-142">**physical_msw** Pierwsze 16 bitów (47-32) adresu fizycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="8dd59-143">**physical_lsw** Mniejsza 32 bitów (31-0) adresu fizycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-144">Return Values</span></span>

- <span data-ttu-id="8dd59-145">**NX_SUCCESS** (0X00) pomyślnie dynamiczny zestaw wpisów ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="8dd59-146">**NX_NO_MORE_ENTRIES** (0X17) nie ma więcej wpisów ARP w pamięci podręcznej ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="8dd59-147">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-148">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="8dd59-149">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-150">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-151">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-151">Allowed From</span></span>

<span data-ttu-id="8dd59-152">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-153">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-153">Preemption Possible</span></span>

<span data-ttu-id="8dd59-154">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-154">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-156">See Also</span></span>

- <span data-ttu-id="8dd59-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="8dd59-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="8dd59-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="8dd59-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="8dd59-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-161">nx_arp_enable</span></span>

<span data-ttu-id="8dd59-162">Włącza protokół ARP (Address Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="8dd59-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-163">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="8dd59-164">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-164">Description</span></span>

<span data-ttu-id="8dd59-165">Ta usługa inicjuje składnik ARP NetX dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="8dd59-166">Inicjowanie protokołu ARP obejmuje skonfigurowanie pamięci podręcznej ARP i różnych procedur przetwarzania ARP niezbędnych do wysyłania i otrzymywania wiadomości ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-167">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-167">Parameters</span></span>

- <span data-ttu-id="8dd59-168">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-169">**arp_cache_memory** Wskaźnik do obszaru pamięci, w którym ma zostać umieszczona pamięć podręczna ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="8dd59-170">**arp_cache_size** Każdy wpis ARP o rozmiarze 52 bajtów, Łączna liczba wpisów ARP, w związku z tym rozmiar podzielony przez 52.</span><span class="sxs-lookup"><span data-stu-id="8dd59-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-171">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-171">Return Values</span></span>

- <span data-ttu-id="8dd59-172">**NX_SUCCESS** (0X00) pomyślne włączenie protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="8dd59-173">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8dd59-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="8dd59-174">**NX_SIZE_ERROR** (0x09) podana przez użytkownika pamięć podręczna ARP jest za mała.</span><span class="sxs-lookup"><span data-stu-id="8dd59-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="8dd59-175">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-176">**NX_ALREADY_ENABLED** (0X15) ten składnik został już włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-177">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-177">Allowed From</span></span>

<span data-ttu-id="8dd59-178">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-179">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-179">Preemption Possible</span></span>

<span data-ttu-id="8dd59-180">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-180">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-181">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-182">See Also</span></span>

- <span data-ttu-id="8dd59-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="8dd59-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="8dd59-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="8dd59-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="8dd59-188">Wyślij żądanie żądania ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-189">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-190">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-190">Description</span></span>

<span data-ttu-id="8dd59-191">Ta usługa przechodzi przez wszystkie interfejsy fizyczne, aby przesyłać żądania żądań ARP, o ile adres IP interfejsu jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="8dd59-192">Jeśli odpowiedź ARP zostanie następnie odebrana, dostarczona procedura obsługi odpowiedzi jest wywoływana, aby przetworzyć odpowiedź na żądanie w ramach protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-193">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-193">Parameters</span></span>

- <span data-ttu-id="8dd59-194">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-195">**response_handler** Wskaźnik do funkcji obsługi odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="8dd59-196">Jeśli podano NX_NULL, odpowiedzi są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-197">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-197">Return Values</span></span>

- <span data-ttu-id="8dd59-198">**NX_SUCCESS** (0X00) pomyślne wysyłanie bezpłatnego protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="8dd59-199">**NX_NO_PACKET** (0X01) Brak dostępnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="8dd59-200">**NX_NOT_ENABLED** (0X14) ARP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="8dd59-201">**NX_IP_ADDRESS_ERROR** (0X21) bieżący adres IP jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="8dd59-202">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-203">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-204">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-204">Allowed From</span></span>

<span data-ttu-id="8dd59-205">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-206">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-206">Preemption Possible</span></span>

<span data-ttu-id="8dd59-207">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-207">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-209">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-209">See Also</span></span>

- <span data-ttu-id="8dd59-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="8dd59-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="8dd59-215">Lokalizowanie fizycznego adresu sprzętowego danego adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="8dd59-217">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-217">Description</span></span>

<span data-ttu-id="8dd59-218">Ta usługa próbuje znaleźć fizyczny adres sprzętowy w pamięci podręcznej ARP, która jest skojarzona z podanym adresem IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-219">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-219">Parameters</span></span>

- <span data-ttu-id="8dd59-220">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-221">**IP_address** Adres IP do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="8dd59-222">**physical_msw** Wskaźnik do zmiennej w celu zwrócenia pierwszych 16 bitów (47-32) adresu fizycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="8dd59-223">**physical_lsw** Wskaźnik do zmiennej zwraca niższą 32 bitów (31-0) adresu fizycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-224">Return Values</span></span>

- <span data-ttu-id="8dd59-225">**NX_SUCCESS** (0X00) pomyślne znalezienie adresu sprzętowego ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="8dd59-226">W pamięci podręcznej ARP nie znaleziono mapowania **NX_ENTRY_NOT_FOUND** (0x16).</span><span class="sxs-lookup"><span data-stu-id="8dd59-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="8dd59-227">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-228">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="8dd59-229">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-230">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-231">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-231">Allowed From</span></span>

<span data-ttu-id="8dd59-232">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-233">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-233">Preemption Possible</span></span>

<span data-ttu-id="8dd59-234">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-234">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-235">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-236">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-236">See Also</span></span>

- <span data-ttu-id="8dd59-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="8dd59-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-241">nx_arp_info_get</span></span>

<span data-ttu-id="8dd59-242">Pobierz informacje o działaniach ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-243">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="8dd59-244">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-244">Description</span></span>

<span data-ttu-id="8dd59-245">Ta usługa pobiera informacje o działaniach ARP dla skojarzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="8dd59-246">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-247">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-247">Parameters</span></span>

- <span data-ttu-id="8dd59-248">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-249">**arp_requests_sent** Wskaźnik do miejsca docelowego dla łącznej liczby żądań ARP wysyłanych z tego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="8dd59-250">**arp_requests_received** Wskaźnik do miejsca docelowego dla łącznej liczby odebranych żądań ARP od sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="8dd59-251">**arp_responses_sent** Wskaźnik do miejsca docelowego dla łącznej liczby odpowiedzi ARP wysyłanych z tego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="8dd59-252">**arp_responses_received** Wskaźnik do miejsca docelowego dla łącznej odpowiedzi ARP odebranych z sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="8dd59-253">**arp_dynamic_entries** Wskaźnik do lokalizacji docelowej dla bieżącej liczby dynamicznych wpisów ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="8dd59-254">**arp_static_entries** Wskaźnik do lokalizacji docelowej dla bieżącej liczby statycznych wpisów ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="8dd59-255">**arp_aged_entries** Wskaźnik do lokalizacji docelowej łącznej liczby wpisów ARP, które mają przestarzałe i stały się nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="8dd59-256">**arp_invalid_messages** Wskaźnik do lokalizacji docelowej całkowitej liczby odebranych komunikatów ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-257">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-257">Return Values</span></span>

- <span data-ttu-id="8dd59-258">**NX_SUCCESS** (0X00) pomyślne pobranie informacji o ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="8dd59-259">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-260">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-261">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-262">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-262">Allowed From</span></span>

<span data-ttu-id="8dd59-263">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-264">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-264">Preemption Possible</span></span>

<span data-ttu-id="8dd59-265">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-265">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-266">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-267">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-267">See Also</span></span>

- <span data-ttu-id="8dd59-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-269">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="8dd59-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span><span class="sxs-lookup"><span data-stu-id="8dd59-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="8dd59-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="8dd59-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="8dd59-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="8dd59-274">Zlokalizuj adres IP przy użyciu adresu fizycznego</span><span class="sxs-lookup"><span data-stu-id="8dd59-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-275">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="8dd59-276">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-276">Description</span></span>

<span data-ttu-id="8dd59-277">Ta usługa próbuje znaleźć adres IP w pamięci podręcznej ARP, która jest skojarzona z podanym adresem fizycznym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-278">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-278">Parameters</span></span>

- <span data-ttu-id="8dd59-279">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-280">**IP_address** Wskaźnik do zwracanego adresu IP, jeśli został znaleziony, który został zamapowany.</span><span class="sxs-lookup"><span data-stu-id="8dd59-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="8dd59-281">**physical_msw** Pierwsze 16 bitów (47-32) adresu fizycznego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="8dd59-282">**physical_lsw** Niższy 32 bitów (31-0) adresu fizycznego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-283">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-283">Return Values</span></span>

- <span data-ttu-id="8dd59-284">**NX_SUCCESS** (0X00) pomyślne Znajdowanie adresu IP ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="8dd59-285">W pamięci podręcznej ARP nie znaleziono mapowania **NX_ENTRY_NOT_FOUND** (0x16).</span><span class="sxs-lookup"><span data-stu-id="8dd59-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="8dd59-286">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="8dd59-287">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-288">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są równe 0.</span><span class="sxs-lookup"><span data-stu-id="8dd59-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-290">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-290">Allowed From</span></span>

<span data-ttu-id="8dd59-291">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-292">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-292">Preemption Possible</span></span>

<span data-ttu-id="8dd59-293">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-293">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-294">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-295">See Also</span></span>

- <span data-ttu-id="8dd59-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-297">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="8dd59-298">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-299">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="8dd59-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="8dd59-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="8dd59-302">Usuń wszystkie statyczne wpisy ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-303">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-304">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-304">Description</span></span>

<span data-ttu-id="8dd59-305">Ta usługa usuwa wszystkie wpisy statyczne w pamięci podręcznej ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-306">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-306">Parameters</span></span>

- <span data-ttu-id="8dd59-307">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-308">Return Values</span></span>

- <span data-ttu-id="8dd59-309">Wpisy statyczne **NX_SUCCESS** (0x00) są usuwane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="8dd59-310">**NX_PTR_ERROR** (0X07) nieprawidłowy wskaźnik ip_ptr.</span><span class="sxs-lookup"><span data-stu-id="8dd59-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="8dd59-311">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-312">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-313">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-313">Allowed From</span></span>

<span data-ttu-id="8dd59-314">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-315">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-315">Preemption Possible</span></span>

<span data-ttu-id="8dd59-316">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-316">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-317">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-318">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-318">See Also</span></span>

- <span data-ttu-id="8dd59-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-320">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="8dd59-321">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="8dd59-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="8dd59-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="8dd59-325">Tworzenie statycznego adresu IP na potrzeby mapowania sprzętowego w pamięci podręcznej ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-326">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="8dd59-327">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-327">Description</span></span>

<span data-ttu-id="8dd59-328">Ta usługa tworzy statyczne mapowanie adresów IP na fizyczne w pamięci podręcznej ARP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="8dd59-329">Statyczne wpisy ARP nie podlegają okresowym aktualizacji protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-330">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-330">Parameters</span></span>

- <span data-ttu-id="8dd59-331">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-332">**IP_address** Adres IP do zamapowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="8dd59-333">**physical_msw** Pierwsze 16 bitów (47-32) adresu fizycznego do mapowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="8dd59-334">**physical_lsw** Mniejsza 32 bitów (31-0) adresu fizycznego do mapowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-335">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-335">Return Values</span></span>

- <span data-ttu-id="8dd59-336">**NX_SUCCESS** (0X00) pomyślne utworzenie wpisu statycznego ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="8dd59-337">**NX_NO_MORE_ENTRIES** (0X17) nie ma więcej wpisów ARP w pamięci podręcznej ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="8dd59-338">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-339">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-340">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-341">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są równe 0.</span><span class="sxs-lookup"><span data-stu-id="8dd59-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-343">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-343">Allowed From</span></span>

<span data-ttu-id="8dd59-344">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-345">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-345">Preemption Possible</span></span>

<span data-ttu-id="8dd59-346">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-346">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-347">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-348">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-348">See Also</span></span>

- <span data-ttu-id="8dd59-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-350">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="8dd59-351">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="8dd59-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="8dd59-355">Usuń statyczny adres IP do mapowania sprzętowego w pamięci podręcznej ARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-356">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="8dd59-357">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-357">Description</span></span>

<span data-ttu-id="8dd59-358">Ta usługa wyszukuje i usuwa wcześniej utworzone mapowanie statycznego adresu IP na adres fizyczny w pamięci podręcznej ARP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-359">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-359">Parameters</span></span>

- <span data-ttu-id="8dd59-360">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-361">**IP_address** Statyczny adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="8dd59-362">**physical_msw** 16 najważniejszych bitów (47 – 32) adresów fizycznych, które zostały zmapowane statycznie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="8dd59-363">**physical_lsw** Niższy 32 bitów (31-0) adresu fizycznego, który został zamapowany statycznie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-364">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-364">Return Values</span></span>

- <span data-ttu-id="8dd59-365">**NX_SUCCESS** (0X00) pomyślne usunięcie wpisu statycznego ARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="8dd59-366">W pamięci podręcznej ARP nie znaleziono wpisu statycznego ARP **NX_ENTRY_NOT_FOUND** (0x16).</span><span class="sxs-lookup"><span data-stu-id="8dd59-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="8dd59-367">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-368">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-369">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-370">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są równe 0.</span><span class="sxs-lookup"><span data-stu-id="8dd59-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-372">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-372">Allowed From</span></span>

<span data-ttu-id="8dd59-373">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-374">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-374">Preemption Possible</span></span>

<span data-ttu-id="8dd59-375">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-375">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-376">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-377">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-377">See Also</span></span>

- <span data-ttu-id="8dd59-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="8dd59-379">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="8dd59-380">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="8dd59-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="8dd59-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="8dd59-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-383">nx_icmp_enable</span></span>

<span data-ttu-id="8dd59-384">Włącz protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="8dd59-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-386">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-386">Description</span></span>

<span data-ttu-id="8dd59-387">Ta usługa włącza składnik ICMP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="8dd59-388">Składnik ICMP jest odpowiedzialny za obsługę internetowych komunikatów o błędach i żądań ping i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-389">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-389">Parameters</span></span>

- <span data-ttu-id="8dd59-390">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-391">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-391">Return Values</span></span>

- <span data-ttu-id="8dd59-392">**NX_SUCCESS** (0X00) pomyślne włączenie protokołu ICMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="8dd59-393">**NX_ALREADY_ENABLED** (0X15) Protokół ICMP jest już włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="8dd59-394">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-395">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-396">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-396">Allowed From</span></span>

<span data-ttu-id="8dd59-397">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-398">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-398">Preemption Possible</span></span>

<span data-ttu-id="8dd59-399">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-399">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-400">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-401">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-401">See Also</span></span>

- <span data-ttu-id="8dd59-402">nx_icmp_info_get, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="8dd59-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="8dd59-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-403">nx_icmp_info_get</span></span>

<span data-ttu-id="8dd59-404">Pobierz informacje o działaniach ICMP</span><span class="sxs-lookup"><span data-stu-id="8dd59-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-405">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="8dd59-406">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-406">Description</span></span>

<span data-ttu-id="8dd59-407">Ta usługa pobiera informacje o działaniach ICMP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-408">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-409">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-409">Parameters</span></span>

- <span data-ttu-id="8dd59-410">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-411">**pings_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="8dd59-412">**ping_timeouts** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu polecenia ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="8dd59-413">**ping_threads_suspended** Wskaźnik do lokalizacji docelowej łącznej liczby wątków zawieszonych w żądaniach ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="8dd59-414">**ping_responses_received** Wskaźnik do Estination o całkowitej liczbie odebranych odpowiedzi ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="8dd59-415">**icmp_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej protokołu ICMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="8dd59-416">**icmp_unhandled_messages** Wskaźnik do Estination całkowitej liczby nieobsłużonych komunikatów ICMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-417">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-417">Return Values</span></span>

- <span data-ttu-id="8dd59-418">**NX_SUCCESS** (0X00) pomyślne pobranie informacji protokołu ICMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="8dd59-419">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-420">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-421">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-422">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-422">Allowed From</span></span>

<span data-ttu-id="8dd59-423">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-424">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-424">Preemption Possible</span></span>

<span data-ttu-id="8dd59-425">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-425">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-426">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-427">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-427">See Also</span></span>

- <span data-ttu-id="8dd59-428">nx_icmp_enable, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="8dd59-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="8dd59-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="8dd59-429">nx_icmp_ping</span></span>

<span data-ttu-id="8dd59-430">Wyślij żądanie ping do określonego adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-432">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-432">Description</span></span>

<span data-ttu-id="8dd59-433">Ta usługa wysyła żądanie ping do określonego adresu IP i czeka przez określony czas dla komunikatu odpowiedzi na polecenie ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="8dd59-434">Jeśli odpowiedź nie zostanie odebrana, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="8dd59-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="8dd59-435">W przeciwnym razie cały komunikat odpowiedzi jest zwracany w zmiennej wskazywanej przez response_ptr.</span><span class="sxs-lookup"><span data-stu-id="8dd59-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="8dd59-436">*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-437">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-437">Parameters</span></span>

- <span data-ttu-id="8dd59-438">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-439">**IP_address** Adres IP w kolejności bajtów hosta do ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="8dd59-440">Wskaźnik danych do obszaru danych dla wiadomości ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="8dd59-441">**data_size** Liczba bajtów w danych ping</span><span class="sxs-lookup"><span data-stu-id="8dd59-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="8dd59-442">**response_ptr** Wskaźnik na wskaźnik pakietu, aby przywrócić komunikat odpowiedzi ping w.</span><span class="sxs-lookup"><span data-stu-id="8dd59-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="8dd59-443">**WAIT_OPTION** Określa czas oczekiwania na odpowiedź na polecenie ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="8dd59-444">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="8dd59-445">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="8dd59-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="8dd59-447">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-448">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-448">Return Values</span></span>

- <span data-ttu-id="8dd59-449">**NX_SUCCESS** (0x00) — pomyślne polecenie ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="8dd59-450">Wskaźnik komunikatu odpowiedzi został umieszczony w zmiennej wskazywanej przez response_ptr.</span><span class="sxs-lookup"><span data-stu-id="8dd59-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="8dd59-451">**NX_NO_PACKET** (0X01) nie może przydzielić pakietu żądania ping.</span><span class="sxs-lookup"><span data-stu-id="8dd59-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="8dd59-452">**NX_OVERFLOW** (0X03) określony obszar danych przekracza domyślny rozmiar pakietu dla tego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="8dd59-453">**NX_NO_RESPONSE** (0X29) żądany adres IP nie odpowiedział.</span><span class="sxs-lookup"><span data-stu-id="8dd59-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="8dd59-454">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-455">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-456">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="8dd59-457">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-458">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-459">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-459">Allowed From</span></span>

<span data-ttu-id="8dd59-460">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-461">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-461">Preemption Possible</span></span>

<span data-ttu-id="8dd59-462">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-462">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-463">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-464">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-464">See Also</span></span>

- <span data-ttu-id="8dd59-465">nx_icmp_enable, nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="8dd59-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-466">nx_igmp_enable</span></span>

<span data-ttu-id="8dd59-467">Włącz protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="8dd59-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-468">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-469">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-469">Description</span></span>

<span data-ttu-id="8dd59-470">Ta usługa włącza składnik IGMP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="8dd59-471">Składnik IGMP jest odpowiedzialny za zapewnienie wsparcia dla operacji zarządzania grupami multiemisji IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-472">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-472">Parameters</span></span>

- <span data-ttu-id="8dd59-473">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-474">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-474">Return Values</span></span>

- <span data-ttu-id="8dd59-475">**NX_SUCCESS** (0X00) pomyślne włączenie protokołu IGMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="8dd59-476">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-477">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-478">**NX_ALREADY_ENABLED** (0X15) ten składnik został już włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-479">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-479">Allowed From</span></span>

<span data-ttu-id="8dd59-480">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-481">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-481">Preemption Possible</span></span>

<span data-ttu-id="8dd59-482">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-482">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-483">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-484">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-484">See Also</span></span>

- <span data-ttu-id="8dd59-485">nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="8dd59-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="8dd59-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="8dd59-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-488">nx_igmp_info_get</span></span>

<span data-ttu-id="8dd59-489">Pobierz informacje o działaniach IGMP</span><span class="sxs-lookup"><span data-stu-id="8dd59-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-490">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="8dd59-491">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-491">Description</span></span>

<span data-ttu-id="8dd59-492">Ta usługa pobiera informacje o działaniach IGMP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-493">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-494">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-494">Parameters</span></span>

- <span data-ttu-id="8dd59-495">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-496">**igmp_reports_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych raportów ICMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="8dd59-497">**igmp_queries_received** Wskaźnik do miejsca docelowego dla łącznej liczby zapytań odebranych przez router multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="8dd59-498">**igmp_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej IGMP dla pakietów odebranych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="8dd59-499">**current_groups_joined** Wskaźnik do lokalizacji docelowej bieżącej liczby grup przyłączonych za pomocą tego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-500">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-500">Return Values</span></span>

- <span data-ttu-id="8dd59-501">**NX_SUCCESS** (0X00) pomyślnie pobiera informacje o protokole IGMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="8dd59-502">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-503">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-504">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-505">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-505">Allowed From</span></span>

<span data-ttu-id="8dd59-506">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-507">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-507">Preemption Possible</span></span>

<span data-ttu-id="8dd59-508">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-508">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-509">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-510">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-510">See Also</span></span>

- <span data-ttu-id="8dd59-511">nx_igmp_enable, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="8dd59-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="8dd59-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="8dd59-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="8dd59-515">Wyłącz sprzężenie zwrotne protokołu IGMP</span><span class="sxs-lookup"><span data-stu-id="8dd59-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-516">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-517">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-517">Description</span></span>

<span data-ttu-id="8dd59-518">Ta usługa wyłącza sprzężenie zwrotne protokołu IGMP dla wszystkich kolejnych grup multiemisji przyłączonych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-519">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-519">Parameters</span></span>

- <span data-ttu-id="8dd59-520">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-521">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-521">Return Values</span></span>
- <span data-ttu-id="8dd59-522">**NX_SUCCESS** (0X00) pomyślne wyłączenie sprzężenia zwrotnego protokołu IGMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="8dd59-523">**NX_NOT_ENABLED** (0X14) protokół IGMP nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="8dd59-524">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-525">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.</span><span class="sxs-lookup"><span data-stu-id="8dd59-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-526">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-526">Allowed From</span></span>

<span data-ttu-id="8dd59-527">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-528">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-528">Preemption Possible</span></span>

<span data-ttu-id="8dd59-529">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-529">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-530">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-531">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-531">See Also</span></span>

- <span data-ttu-id="8dd59-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="8dd59-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="8dd59-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="8dd59-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="8dd59-536">Włączanie sprzężenia zwrotnego IGMP</span><span class="sxs-lookup"><span data-stu-id="8dd59-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-537">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-538">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-538">Description</span></span>

<span data-ttu-id="8dd59-539">Ta usługa włącza sprzężenie zwrotne protokołu IGMP dla wszystkich kolejnych grup multiemisji przyłączonych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-540">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-540">Parameters</span></span>

- <span data-ttu-id="8dd59-541">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-542">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-542">Return Values</span></span>
- <span data-ttu-id="8dd59-543">**NX_SUCCESS** (0X00) pomyślne wyłączenie sprzężenia zwrotnego protokołu IGMP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="8dd59-544">**NX_NOT_ENABLED** (0X14) protokół IGMP nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="8dd59-545">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-546">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.</span><span class="sxs-lookup"><span data-stu-id="8dd59-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-547">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-547">Allowed From</span></span>

<span data-ttu-id="8dd59-548">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-549">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-549">Preemption Possible</span></span>

<span data-ttu-id="8dd59-550">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-550">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-551">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-552">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-552">See Also</span></span>

- <span data-ttu-id="8dd59-553">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="8dd59-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="8dd59-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="8dd59-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="8dd59-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="8dd59-557">Dołącz wystąpienie IP do określonej grupy multiemisji za pośrednictwem interfejsu</span><span class="sxs-lookup"><span data-stu-id="8dd59-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8dd59-559">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-559">Description</span></span>

<span data-ttu-id="8dd59-560">Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji za pośrednictwem określonego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="8dd59-561">Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa została przyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="8dd59-562">Po dołączeniu do grupy multiemisji składnik IGMP zezwoli na odbieranie pakietów IP z tym adresem grupy za pośrednictwem określonego interfejsu sieciowego, a także zgłaszanie do routerów, do których ten adres IP jest członkiem tej grupy multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="8dd59-563">Komunikaty przyłączenia do członkostwa w protokole IGMP, raport i opuszczenie są również wysyłane za pośrednictwem określonego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-564">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-564">Parameters</span></span>

- <span data-ttu-id="8dd59-565">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-566">**group_address** Adres grupy multiemisji IP klasy D do przyłączenia w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="8dd59-567">**interface_index** Indeks interfejsu dołączonego do wystąpienia NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-568">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-568">Return Values</span></span>

- <span data-ttu-id="8dd59-569">**NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="8dd59-570">**NX_NO_MORE_ENTRIES** (0X17) nie można przyłączyć więcej grup multiemisji, Przekroczono maksymalną liczbę.</span><span class="sxs-lookup"><span data-stu-id="8dd59-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="8dd59-571">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-572">Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="8dd59-573">Podany adres grupy multiemisji **NX_IP_ADDRESS_ERROR** (0x21) nie jest prawidłowym adresem klasy D.</span><span class="sxs-lookup"><span data-stu-id="8dd59-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="8dd59-574">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-575">**NX_NOT_ENABLED** (0x14) obsługa multiemisji IP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-576">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-576">Allowed From</span></span>

<span data-ttu-id="8dd59-577">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-578">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-578">Preemption Possible</span></span>

<span data-ttu-id="8dd59-579">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-579">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-580">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-581">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-581">See Also</span></span>

- <span data-ttu-id="8dd59-582">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="8dd59-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="8dd59-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="8dd59-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="8dd59-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="8dd59-586">Dołącz wystąpienie adresu IP do określonej grupy multiemisji</span><span class="sxs-lookup"><span data-stu-id="8dd59-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-587">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="8dd59-588">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-588">Description</span></span>

<span data-ttu-id="8dd59-589">Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="8dd59-590">Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa została przyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="8dd59-591">Sterownik jest poleceniem, aby wysłać raport IGMP, jeśli jest to pierwsze połączenie w sieci wskazujące zamiar hosta do przyłączenia do grupy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="8dd59-592">Po dołączeniu składnik IGMP zezwoli na odbieranie pakietów IP z tym adresem grupy i raport na routerach, do których ten adres IP jest członkiem tej grupy multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="8dd59-593">*Aby dołączyć do grupy multiemisji na urządzeniu niebędącym podstawowym, należy użyć **nx_igmp_multicast_interface_join usługi.***</span><span class="sxs-lookup"><span data-stu-id="8dd59-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="8dd59-594">**Parametry**</span><span class="sxs-lookup"><span data-stu-id="8dd59-594">**Parameters**</span></span>

- <span data-ttu-id="8dd59-595">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-596">**group_address** Adres grupy multiemisji IP klasy D do przyłączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-597">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-597">Return Values</span></span>

- <span data-ttu-id="8dd59-598">**NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="8dd59-599">**NX_NO_MORE_ENTRIES** (0X17) nie można przyłączyć więcej grup multiemisji, Przekroczono maksymalną liczbę.</span><span class="sxs-lookup"><span data-stu-id="8dd59-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="8dd59-600">Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="8dd59-601">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres grupy adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="8dd59-602">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-603">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-604">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-605">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-605">Allowed From</span></span>

<span data-ttu-id="8dd59-606">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-607">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-607">Preemption Possible</span></span>

<span data-ttu-id="8dd59-608">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-608">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-609">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-610">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-610">See Also</span></span>

- <span data-ttu-id="8dd59-611">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="8dd59-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="8dd59-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="8dd59-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="8dd59-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="8dd59-615">Przyczyna opuszczenia określonej grupy multiemisji przez wystąpienie protokołu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-616">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="8dd59-617">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-617">Description</span></span>

<span data-ttu-id="8dd59-618">Ta usługa powoduje, że wystąpienie IP opuszcza określoną grupę multiemisji, jeśli liczba żądań opuszczenia jest zgodna z liczbą żądań dołączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="8dd59-619">W przeciwnym razie wewnętrzna liczba sprzężeń jest po prostu zmniejszana.</span><span class="sxs-lookup"><span data-stu-id="8dd59-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-620">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-620">Parameters</span></span>

- <span data-ttu-id="8dd59-621">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-622">**group_address** Grupa multiemisji do opuszczenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-623">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-623">Return Values</span></span>

- <span data-ttu-id="8dd59-624">**NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="8dd59-625">Nie znaleziono poprzedniego żądania Join **NX_ENTRY_NOT_FOUND** (0x16).</span><span class="sxs-lookup"><span data-stu-id="8dd59-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="8dd59-626">Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="8dd59-627">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres grupy adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="8dd59-628">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-629">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-630">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-631">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-631">Allowed From</span></span>

<span data-ttu-id="8dd59-632">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-633">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-633">Preemption Possible</span></span>

<span data-ttu-id="8dd59-634">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-634">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-635">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="8dd59-636">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-636">See Also</span></span>

- <span data-ttu-id="8dd59-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="8dd59-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="8dd59-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="8dd59-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="8dd59-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="8dd59-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="8dd59-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="8dd59-641">Powiadamiaj aplikację, jeśli zmienią się adresy IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="8dd59-643">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-643">Description</span></span>

<span data-ttu-id="8dd59-644">Ta usługa rejestruje funkcję powiadamiania aplikacji, która jest wywoływana za każdym razem, gdy adres IP zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-645">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-645">Parameters</span></span>

- <span data-ttu-id="8dd59-646">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-647">**CHANGE_NOTIFY** Wskaźnik na funkcję powiadamiania o zmianie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="8dd59-648">Jeśli ten parametr jest NX_NULL, powiadomienie o zmianie adresu IP jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="8dd59-649">**additional_info** Wskaźnik do opcjonalnych dodatkowych informacji, które są również dostarczane do funkcji powiadomień, gdy adres IP zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-650">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-650">Return Values</span></span>

- <span data-ttu-id="8dd59-651">Pomyślne powiadomienie o zmianie adresu IP **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="8dd59-652">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-653">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-654">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-654">Allowed From</span></span>

<span data-ttu-id="8dd59-655">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-656">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-656">Preemption Possible</span></span>

<span data-ttu-id="8dd59-657">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-657">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-658">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-659">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-659">See Also</span></span>

- <span data-ttu-id="8dd59-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="8dd59-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="8dd59-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="8dd59-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="8dd59-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-664">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="8dd59-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-665">nx_ip_address_get</span></span>

<span data-ttu-id="8dd59-666">Pobieranie adresu IP i maski sieci</span><span class="sxs-lookup"><span data-stu-id="8dd59-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-667">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="8dd59-668">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-668">Description</span></span>

<span data-ttu-id="8dd59-669">Ta usługa Pobiera adres IP i maskę podsieci podstawowego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="8dd59-670">\* Aby uzyskać informacje na temat urządzenia pomocniczego, Użyj usługi</span><span class="sxs-lookup"><span data-stu-id="8dd59-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="8dd59-671">**nx_ip_interface_address_get**. \*</span><span class="sxs-lookup"><span data-stu-id="8dd59-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-672">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-672">Parameters</span></span>

- <span data-ttu-id="8dd59-673">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-674">**IP_address** Wskaźnik do miejsca docelowego dla adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="8dd59-675">**network_mask** Wskaźnik do miejsca docelowego dla maski sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-676">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-676">Return Values</span></span>

- <span data-ttu-id="8dd59-677">**NX_SUCCESS** (0X00) pomyślne pobieranie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="8dd59-678">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub zmiennej Return.</span><span class="sxs-lookup"><span data-stu-id="8dd59-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="8dd59-679">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-680">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-680">Allowed From</span></span>

<span data-ttu-id="8dd59-681">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-682">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-682">Preemption Possible</span></span>

<span data-ttu-id="8dd59-683">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-683">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-684">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-685">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-685">See Also</span></span>

- <span data-ttu-id="8dd59-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="8dd59-687">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="8dd59-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="8dd59-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="8dd59-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-692">nx_ip_address_set</span></span>

<span data-ttu-id="8dd59-693">Ustawianie adresu IP i maski sieci</span><span class="sxs-lookup"><span data-stu-id="8dd59-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-694">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="8dd59-695">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-695">Description</span></span>

<span data-ttu-id="8dd59-696">Ta usługa ustawia adres IP i maskę sieci dla podstawowego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="8dd59-697">*Aby ustawić adres IP i maskę sieci dla urządzenia pomocniczego, użyj **nx_ip_interface_address_set** usługi.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-698">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-698">Parameters</span></span>

- <span data-ttu-id="8dd59-699">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-700">**IP_address** Nowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="8dd59-701">**network_mask** Nowa maska sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-702">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-702">Return Values</span></span>

- <span data-ttu-id="8dd59-703">Pomyślny zestaw adresów IP **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="8dd59-704">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-705">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-706">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-707">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-707">Allowed From</span></span>

<span data-ttu-id="8dd59-708">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-709">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-709">Preemption Possible</span></span>

<span data-ttu-id="8dd59-710">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-710">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-711">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-712">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-712">See Also</span></span>

- <span data-ttu-id="8dd59-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="8dd59-714">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="8dd59-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="8dd59-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="8dd59-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-719">nx_ip_create</span></span>

<span data-ttu-id="8dd59-720">Tworzenie wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-721">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="8dd59-722">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-722">Description</span></span>

<span data-ttu-id="8dd59-723">Ta usługa tworzy wystąpienie IP przy użyciu adresu IP i sterownika sieci dostarczonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8dd59-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="8dd59-724">Ponadto aplikacja musi dostarczyć wcześniej utworzoną pulę pakietów dla wystąpienia IP, które ma być używane na potrzeby wewnętrznej alokacji pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="8dd59-725">Należy pamiętać, że podany sterownik sieciowy aplikacji nie jest wywoływany do momentu wykonania wątku tego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-726">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-726">Parameters</span></span>

- <span data-ttu-id="8dd59-727">**ip_ptr** Wskaźnik do bloku sterującego, aby utworzyć nowe wystąpienie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="8dd59-728">**Nazwa** Nazwa nowego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="8dd59-729">**IP_address** Adres IP dla tego nowego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="8dd59-730">**network_mask** Maskowanie, aby odróżnić część sieci adresu IP dla podsieci i użycia w ramach wykorzystania pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="8dd59-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="8dd59-731">**default_pool** Wskaźnik sterujący blokiem utworzonej wcześniej puli pakietów NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="8dd59-732">**ip_network_driver** Sterownik sieciowy dostarczony przez użytkownika używany do wysyłania i odbierania pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="8dd59-733">**memory_ptr** Wskaźnik do obszaru pamięci dla obszaru stosu wątku pomocnika IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="8dd59-734">**memory_size** Liczba bajtów w obszarze pamięci dla stosu wątku pomocnika IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="8dd59-735">**priorytet** Priorytet wątku pomocnika adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-736">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-736">Return Values</span></span>
- <span data-ttu-id="8dd59-737">**NX_SUCCESS** (0X00) pomyślne utworzenie wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="8dd59-738">Biblioteka NetX **NX_NOT_IMPLEMENTED** (0x4A) jest niepoprawnie skonfigurowana.</span><span class="sxs-lookup"><span data-stu-id="8dd59-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="8dd59-739">**NX_PTR_ERROR** (0X07) nieprawidłowy adres IP, wskaźnik funkcji sterownika sieci, Pula pakietów lub wskaźnik pamięci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="8dd59-740">**NX_SIZE_ERROR** (0x09) podany rozmiar stosu jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="8dd59-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="8dd59-741">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-742">**NX_IP_ADDRESS_ERROR** (0x21) podany adres IP jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="8dd59-743">**NX_OPTION_ERROR** (0x21) podany priorytet wątku IP jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-744">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-744">Allowed From</span></span>

<span data-ttu-id="8dd59-745">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-746">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-746">Preemption Possible</span></span>

<span data-ttu-id="8dd59-747">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-747">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-748">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-749">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-749">See Also</span></span>

- <span data-ttu-id="8dd59-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-751">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="8dd59-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="8dd59-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="8dd59-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-756">nx_ip_delete</span></span>

<span data-ttu-id="8dd59-757">Usuń poprzednio utworzone wystąpienie adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-758">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-759">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-759">Description</span></span>

<span data-ttu-id="8dd59-760">Ta usługa usuwa wcześniej utworzone wystąpienie protokołu IP i zwalnia wszystkie zasoby systemowe należące do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-761">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-761">Parameters</span></span>
- <span data-ttu-id="8dd59-762">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-763">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-763">Return Values</span></span>

- <span data-ttu-id="8dd59-764">Pomyślnie usunięto adres IP **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="8dd59-765">**NX_SOCKETS_BOUND** (0X28) to wystąpienie protokołu IP nadal ma powiązane z nim gniazda UDP lub TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="8dd59-766">Przed usunięciem wystąpienia adresu IP wszystkie gniazda muszą zostać anulowane i usunięte.</span><span class="sxs-lookup"><span data-stu-id="8dd59-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="8dd59-767">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-768">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-769">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-769">Allowed From</span></span>

<span data-ttu-id="8dd59-770">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-771">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-771">Preemption Possible</span></span>

<span data-ttu-id="8dd59-772">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-773">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-774">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-774">See Also</span></span>

- <span data-ttu-id="8dd59-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-776">nx_ip_create, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="8dd59-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="8dd59-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="8dd59-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="8dd59-782">Wydaj polecenie do sterownika sieciowego</span><span class="sxs-lookup"><span data-stu-id="8dd59-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-783">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-784">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-784">Description</span></span>

<span data-ttu-id="8dd59-785">Ta usługa udostępnia interfejs bezpośredni do podstawowego sterownika interfejsu sieciowego aplikacji określonego podczas wywołania ***nx_ip_create*** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="8dd59-786">Polecenia specyficzne dla aplikacji mogą służyć do podawania wartości liczbowych, które są większe lub równe NX_LINK_USER_COMMAND.</span><span class="sxs-lookup"><span data-stu-id="8dd59-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="8dd59-787">*Aby wydać polecenie dla urządzenia pomocniczego, Użyj usługi **nx_ip_driver_interface_direct_command** .*</span><span class="sxs-lookup"><span data-stu-id="8dd59-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-788">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-788">Parameters</span></span>

- <span data-ttu-id="8dd59-789">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-790">**polecenie** Kod polecenia numerycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-790">**command** Numeric command code.</span></span> <span data-ttu-id="8dd59-791">Polecenia standardowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="8dd59-792">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="8dd59-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="8dd59-793">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="8dd59-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="8dd59-794">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="8dd59-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="8dd59-795">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="8dd59-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="8dd59-796">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="8dd59-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="8dd59-797">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="8dd59-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="8dd59-798">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="8dd59-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="8dd59-799">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="8dd59-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="8dd59-800">**return_value_ptr** Wskaźnik do zwrócenia zmiennej w obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-801">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-801">Return Values</span></span>

- <span data-ttu-id="8dd59-802">**NX_SUCCESS** (0X00) pomyślne polecenie sterownika sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="8dd59-803">**NX_UNHANDLED_COMMAND** (0x44) nieobsłużone lub niezaimplementowane polecenie sterownika sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="8dd59-804">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="8dd59-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="8dd59-805">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-806">**NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-807">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-807">Allowed From</span></span>

<span data-ttu-id="8dd59-808">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-808">Threads</span></span>

- <span data-ttu-id="8dd59-809">**Możliwe przeprowadzenie**</span><span class="sxs-lookup"><span data-stu-id="8dd59-809">**Preemption Possible**</span></span>

<span data-ttu-id="8dd59-810">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-810">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-811">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-812">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-812">See Also</span></span>

- <span data-ttu-id="8dd59-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="8dd59-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="8dd59-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-817">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="8dd59-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="8dd59-819">Wydaj polecenie do sterownika sieciowego</span><span class="sxs-lookup"><span data-stu-id="8dd59-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-820">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-821">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-821">Description</span></span>

<span data-ttu-id="8dd59-822">Ta usługa udostępnia bezpośrednie polecenie do sterownika urządzenia sieciowego aplikacji w wystąpieniu protokołu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="8dd59-823">Polecenia specyficzne dla aplikacji mogą służyć do podawania wartości liczbowych, które są większe lub równe *NX_LINK_USER_COMMAND*.</span><span class="sxs-lookup"><span data-stu-id="8dd59-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-824">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-824">Parameters</span></span>

- <span data-ttu-id="8dd59-825">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-826">**polecenie** Kod polecenia numerycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-826">**command** Numeric command code.</span></span> <span data-ttu-id="8dd59-827">Polecenia standardowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="8dd59-828">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="8dd59-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="8dd59-829">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="8dd59-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="8dd59-830">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="8dd59-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="8dd59-831">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="8dd59-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="8dd59-832">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="8dd59-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="8dd59-833">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="8dd59-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="8dd59-834">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="8dd59-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="8dd59-835">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="8dd59-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="8dd59-836">**interface_index** Indeks interfejsu sieciowego, do którego ma zostać wysłane polecenie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="8dd59-837">**return_value_ptr** Wskaźnik do zwrócenia zmiennej w obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-838">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-838">Return Values</span></span>
- <span data-ttu-id="8dd59-839">**NX_SUCCESS** (0X00) pomyślne polecenie sterownika sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="8dd59-840">**NX_UNHANDLED_COMMAND** (0x44) nieobsłużone lub niezaimplementowane polecenie sterownika sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="8dd59-841">**NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="8dd59-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="8dd59-842">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="8dd59-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="8dd59-843">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-844">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-844">Allowed From</span></span>

<span data-ttu-id="8dd59-845">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-846">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-846">Preemption Possible</span></span>

<span data-ttu-id="8dd59-847">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-847">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-848">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-849">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-849">See Also</span></span>

- <span data-ttu-id="8dd59-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="8dd59-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-854">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="8dd59-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="8dd59-856">Wyłącz przekazywanie pakietów IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-857">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-858">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-858">Description</span></span>

<span data-ttu-id="8dd59-859">Ta usługa wyłącza przekazywanie pakietów IP wewnątrz składnika IP NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="8dd59-860">Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-861">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-861">Parameters</span></span>

- <span data-ttu-id="8dd59-862">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-863">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-863">Return Values</span></span>

- <span data-ttu-id="8dd59-864">**NX_SUCCESS** (0X00) pomyślne wyłączenie przekazywania adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="8dd59-865">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-866">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-867">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-867">Allowed From</span></span>

<span data-ttu-id="8dd59-868">Inicjalizacja, wątki, czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-869">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-869">Preemption Possible</span></span>

<span data-ttu-id="8dd59-870">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-870">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-871">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-872">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-872">See Also</span></span>

- <span data-ttu-id="8dd59-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="8dd59-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-877">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="8dd59-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="8dd59-879">Włączanie przekazywania pakietów IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-880">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-881">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-881">Description</span></span>

<span data-ttu-id="8dd59-882">Ta usługa umożliwia przekazywanie pakietów IP w składniku IP NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="8dd59-883">Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-884">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-884">Parameters</span></span>

- <span data-ttu-id="8dd59-885">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-886">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-886">Return Values</span></span>
- <span data-ttu-id="8dd59-887">**NX_SUCCESS** (0X00) pomyślne włączenie przekazywania adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="8dd59-888">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-889">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-890">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-890">Allowed From</span></span>

<span data-ttu-id="8dd59-891">Inicjalizacja, wątki, czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-892">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-892">Preemption Possible</span></span>

<span data-ttu-id="8dd59-893">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-893">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-894">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-895">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-895">See Also</span></span>

- <span data-ttu-id="8dd59-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-900">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="8dd59-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="8dd59-902">Wyłącz fragmentację pakietu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-903">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-904">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-904">Description</span></span>

<span data-ttu-id="8dd59-905">Ta usługa wyłącza funkcję fragmentacji i ponownego składania pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="8dd59-906">W przypadku pakietów, które oczekują na ponowną złożenie, ta usługa zwalnia te pakiety.</span><span class="sxs-lookup"><span data-stu-id="8dd59-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="8dd59-907">Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-908">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-908">Parameters</span></span>

- <span data-ttu-id="8dd59-909">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-910">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-910">Return Values</span></span>
- <span data-ttu-id="8dd59-911">**NX_SUCCESS** (0x00) — wyłączono pomyślne fragmenty adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="8dd59-912">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-913">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-914">**NX_NOT_ENABLED** (0X14) fragmentacja IP nie jest włączona w wystąpieniu adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-915">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-915">Allowed From</span></span>

<span data-ttu-id="8dd59-916">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-917">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-917">Preemption Possible</span></span>

<span data-ttu-id="8dd59-918">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-918">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-919">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-920">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-920">See Also</span></span>

- <span data-ttu-id="8dd59-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-925">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="8dd59-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="8dd59-927">Włącz fragmentację pakietów IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-928">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-929">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-929">Description</span></span>

<span data-ttu-id="8dd59-930">Ta usługa umożliwia fragmentację i remontowanie pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="8dd59-931">Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-932">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-932">Parameters</span></span>

- <span data-ttu-id="8dd59-933">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-934">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-934">Return Values</span></span>

- <span data-ttu-id="8dd59-935">**NX_SUCCESS** (0x00), pomyślne włączenie FRAGMENTU adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="8dd59-936">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-937">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-938">Funkcje fragmentacji adresów IP **NX_NOT_ENABLED** (0x14) nie są kompilowane do NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-939">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-939">Allowed From</span></span>

<span data-ttu-id="8dd59-940">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-941">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-941">Preemption Possible</span></span>

<span data-ttu-id="8dd59-942">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-942">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-943">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-944">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-944">See Also</span></span>

- <span data-ttu-id="8dd59-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="8dd59-949">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="8dd59-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="8dd59-951">Ustaw adres IP bramy</span><span class="sxs-lookup"><span data-stu-id="8dd59-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-952">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="8dd59-953">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-953">Description</span></span>

<span data-ttu-id="8dd59-954">Ta usługa ustawia adres IP bramy IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="8dd59-955">Cały ruch poza siecią jest kierowany do tej bramy na potrzeby transmisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="8dd59-956">Brama musi być bezpośrednio dostępna za pomocą jednego z interfejsów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-957">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-957">Parameters</span></span>

- <span data-ttu-id="8dd59-958">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-959">**IP_address** Adres IP bramy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-960">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-960">Return Values</span></span>

- <span data-ttu-id="8dd59-961">**NX_SUCCESS** (0x00) — pomyślny zbiór adresów IP bramy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="8dd59-962">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="8dd59-963">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-964">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-965">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-965">Allowed From</span></span>

<span data-ttu-id="8dd59-966">Inicjalizacja, wątek</span><span class="sxs-lookup"><span data-stu-id="8dd59-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-967">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-967">Preemption Possible</span></span>

<span data-ttu-id="8dd59-968">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-968">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-969">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="8dd59-970">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-970">See Also</span></span>

- <span data-ttu-id="8dd59-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="8dd59-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-972">nx_ip_info_get</span></span>

<span data-ttu-id="8dd59-973">Pobierz informacje o działaniach IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-974">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="8dd59-975">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-975">Description</span></span>

<span data-ttu-id="8dd59-976">Ta usługa pobiera informacje o działaniach IP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-977">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-978">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-978">Parameters</span></span>

- <span data-ttu-id="8dd59-979">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-980">**ip_total_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="8dd59-981">**ip_total_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="8dd59-982">**ip_total_packets_received** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów odbioru adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="8dd59-983">**ip_total_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych bajtów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="8dd59-984">**ip_invalid_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="8dd59-985">**ip_receive_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów odebranych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="8dd59-986">**ip_receive_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej w pakietach odbierania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="8dd59-987">**ip_send_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów do wysłania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="8dd59-988">**ip_total_fragments_sent** Wskaźnik do lokalizacji docelowej łącznej liczby wysłanych fragmentów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="8dd59-989">**ip_total_fragments_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych fragmentów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-990">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-990">Return Values</span></span>

- <span data-ttu-id="8dd59-991">**NX_SUCCESS** (0X00) pomyślne pobieranie informacji o adresie IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="8dd59-992">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-993">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-994">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-994">Allowed From</span></span>

<span data-ttu-id="8dd59-995">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-996">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-996">Preemption Possible</span></span>

<span data-ttu-id="8dd59-997">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-997">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-998">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-999">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-999">See Also</span></span>

- <span data-ttu-id="8dd59-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="8dd59-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="8dd59-1006">Pobieranie adresu IP interfejsu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1007">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="8dd59-1008">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1008">Description</span></span>

<span data-ttu-id="8dd59-1009">Ta usługa Pobiera adres IP określonego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="8dd59-1010">*Określone urządzenie, jeśli nie urządzenie podstawowe, musi być wcześniej dołączone do wystąpienia IP.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1011">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1011">Parameters</span></span>

- <span data-ttu-id="8dd59-1012">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1013">**interface_index** Indeks interfejsu, taka sama jak wartość indeksu do interfejsu sieciowego dołączonego do wystąpienia protokołu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="8dd59-1014">**IP_address** Wskaźnik do miejsca docelowego dla adresu IP interfejsu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="8dd59-1015">**network_mask** Wskaźnik do miejsca docelowego dla maski sieci interfejsu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1016">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1016">Return Values</span></span>

- <span data-ttu-id="8dd59-1017">**NX_SUCCESS** (0X00) pomyślne pobieranie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="8dd59-1018">**NX_INVALID_INTERFACE** (0X4C) określony interfejs sieciowy jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="8dd59-1019">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1020">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1021">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1021">Allowed From</span></span>

<span data-ttu-id="8dd59-1022">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1023">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1023">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1024">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1025">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1026">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1026">See Also</span></span>

- <span data-ttu-id="8dd59-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="8dd59-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="8dd59-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="8dd59-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="8dd59-1031">Ustaw adres IP interfejsu i maskę sieci</span><span class="sxs-lookup"><span data-stu-id="8dd59-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1032">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="8dd59-1033">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1033">Description</span></span>

<span data-ttu-id="8dd59-1034">Ta usługa ustawia adres IP i maskę sieci dla określonego interfejsu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="8dd59-1035">*Określony interfejs musi być wcześniej dołączony do wystąpienia IP.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1036">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1036">Parameters</span></span>

- <span data-ttu-id="8dd59-1037">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1038">**interface_index** Indeks interfejsu dołączonego do wystąpienia NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="8dd59-1039">**IP_address** Nowy adres IP interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="8dd59-1040">**network_mask** Nowa maska sieci interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1041">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1041">Return Values</span></span>

- <span data-ttu-id="8dd59-1042">Pomyślny zestaw adresów IP **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="8dd59-1043">**NX_INVALID_INTERFACE** (0X4C) określony interfejs sieciowy jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="8dd59-1044">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1045">**NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="8dd59-1046">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1047">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1047">Allowed From</span></span>

<span data-ttu-id="8dd59-1048">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1049">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1049">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1050">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1051">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1052">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1052">See Also</span></span>

- <span data-ttu-id="8dd59-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="8dd59-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="8dd59-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="8dd59-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="8dd59-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="8dd59-1057">Dołącz interfejs sieciowy do wystąpienia protokołu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="8dd59-1059">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1059">Description</span></span>

<span data-ttu-id="8dd59-1060">Ta usługa dodaje fizyczny interfejs sieciowy do interfejsu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="8dd59-1061">Należy zauważyć, że wystąpienie IP jest tworzone przy użyciu interfejsu podstawowego, więc każdy dodatkowy interfejs jest pomocniczy dla interfejsu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="8dd59-1062">Łączna liczba interfejsów sieciowych dołączonych do wystąpienia IP (łącznie z interfejsem podstawowym) nie może przekroczyć **NX_MAX_PHYSICAL_INTERFACES**.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="8dd59-1063">Jeśli wątek IP nie został jeszcze uruchomiony, interfejsy pomocnicze zostaną zainicjowane w ramach procesu uruchamiania wątku IP, który inicjuje wszystkie interfejsy fizyczne.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="8dd59-1064">Jeśli wątek IP nie jest jeszcze uruchomiony, interfejs pomocniczy jest inicjowany w ramach usługi ***nx_ip_interface_attach*** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="8dd59-1065">*ip_ptr musi wskazywać prawidłową strukturę adresu IP NetX.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="8dd59-1066">*Należy skonfigurować **NX_MAX_PHYSICAL_INTERFACES** dla liczby interfejsów sieciowych dla wystąpienia protokołu IP. Wartość domyślna to 1.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1067">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1067">Parameters</span></span>

- <span data-ttu-id="8dd59-1068">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1069">**INTERFACE_NAME** Wskaźnik do ciągu nazwy interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="8dd59-1070">**IP_address** Adres IP urządzenia w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="8dd59-1071">**network_mask** Maska sieci urządzenia w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="8dd59-1072">**ip_link_driver** Sterownik Ethernet dla interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1073">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1073">Return Values</span></span>

- <span data-ttu-id="8dd59-1074">Wpis **NX_SUCCESS** (0x00) jest dodawany do statycznej tabeli routingu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="8dd59-1075">**NX_NO_MORE_ENTRIES** (0X17) Maksymalna liczba interfejsów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="8dd59-1076">Przekroczono **NX_MAX_PHYSICAL_INTERFACES** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="8dd59-1077">**NX_DUPLICATED_ENTRY** (0x52) podany adres IP jest już używany w tym wystąpieniu adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="8dd59-1078">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1079">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="8dd59-1080">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowe dane wejściowe adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1081">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1081">Allowed From</span></span>

<span data-ttu-id="8dd59-1082">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1083">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1083">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1084">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1085">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1086">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1086">See Also</span></span>

- <span data-ttu-id="8dd59-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="8dd59-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="8dd59-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="8dd59-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="8dd59-1091">Pobierz parametry interfejsu sieciowego</span><span class="sxs-lookup"><span data-stu-id="8dd59-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-1092">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="8dd59-1093">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1093">Description</span></span>

<span data-ttu-id="8dd59-1094">Ta usługa pobiera informacje o parametrach sieci dla określonego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="8dd59-1095">Wszystkie dane są pobierane w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="8dd59-1096">*ip_ptr musi wskazywać prawidłową strukturę adresu IP NetX. Określony interfejs, jeśli nie jest interfejsem podstawowym, musi być wcześniej dołączony do wystąpienia IP.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1097">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1097">Parameters</span></span>

- <span data-ttu-id="8dd59-1098">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1099">**interface_index** Indeks określający interfejs sieciowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="8dd59-1100">**INTERFACE_NAME** Wskaźnik do buforu, który zawiera nazwę interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="8dd59-1101">**IP_address** Wskaźnik do lokalizacji docelowej dla adresu IP interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="8dd59-1102">**network_mask** Wskaźnik do miejsca docelowego dla maski sieci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="8dd59-1103">**mtu_size** Wskaźnik do miejsca docelowego dla maksymalnej jednostki transferu dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="8dd59-1104">**physical_address_msw** Wskaźnik do miejsca docelowego dla pierwszych 16 bitów adresu MAC urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="8dd59-1105">**physical_address_lsw** Wskaźnik do miejsca docelowego dla niższych 32 bitów adresu MAC urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-1106">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1106">Return Values</span></span>
- <span data-ttu-id="8dd59-1107">Uzyskano informacje o interfejsie **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="8dd59-1108">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="8dd59-1109">**NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1110">Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1111">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1111">Allowed From</span></span>

<span data-ttu-id="8dd59-1112">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1113">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1113">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1114">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1115">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1116">See Also</span></span>

- <span data-ttu-id="8dd59-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="8dd59-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="8dd59-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="8dd59-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="8dd59-1121">Sprawdź stan wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-1122">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1123">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1123">Description</span></span>

<span data-ttu-id="8dd59-1124">Ta usługa sprawdza i opcjonalnie czeka na określony stan interfejsu sieciowego utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1125">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1125">Parameters</span></span>

- <span data-ttu-id="8dd59-1126">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1127">**interface_index** Numer indeksu interfejsu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="8dd59-1128">**needed_status** Żądany stan adresu IP, zdefiniowany w postaci mapy bitowej, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="8dd59-1129">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="8dd59-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="8dd59-1131">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="8dd59-1132">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="8dd59-1133">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="8dd59-1134">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="8dd59-1135">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="8dd59-1136">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="8dd59-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="8dd59-1138">**actual_status** Wskaźnik do miejsca docelowego rzeczywistego zestawu bitów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="8dd59-1139">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądane bity stanu są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="8dd59-1140">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8dd59-1141">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="8dd59-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8dd59-1143">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1144">Return Values</span></span>

- <span data-ttu-id="8dd59-1145">Sprawdzanie stanu IP **NX_SUCCESS** (0x00) powiodło się.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="8dd59-1146">Żądanie stanu **NX_NOT_SUCCESSFUL** (0x43) nie było spełnione w określonym limicie czasu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="8dd59-1147">Wskaźnik IP **NX_PTR_ERROR** (0x07) ma wartość lub jest nieprawidłowy lub rzeczywisty wskaźnik stanu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="8dd59-1148">**NX_OPTION_ERROR** (0X0a) Nieprawidłowa opcja stanu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="8dd59-1149">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="8dd59-1151">lub interfejs jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1152">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1152">Allowed From</span></span>

<span data-ttu-id="8dd59-1153">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1154">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1154">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1155">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1156">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1157">See Also</span></span>

- <span data-ttu-id="8dd59-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="8dd59-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="8dd59-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="8dd59-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="8dd59-1162">Ustaw funkcję wywołania zwrotnego powiadomienia o zmianie stanu łącza</span><span class="sxs-lookup"><span data-stu-id="8dd59-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1163">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="8dd59-1164">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1164">Description</span></span>

<span data-ttu-id="8dd59-1165">Ta usługa umożliwia skonfigurowanie funkcji wywołania zwrotnego powiadomienia o zmianie stanu łącza.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="8dd59-1166">Procedura *link_status_change_notify* podana przez użytkownika jest wywoływana, gdy zostanie zmieniony stan podstawowego lub pomocniczego interfejsu (na przykład adres IP jest zmieniany). Jeśli *link_status_change_notify* ma wartość null, funkcja wywołania zwrotnego powiadomienia o zmianie stanu łącza jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1167">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1167">Parameters</span></span>

- <span data-ttu-id="8dd59-1168">**ip_ptr** Wskaźnik bloku kontroli adresów IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="8dd59-1169">**link_status_change_notify** Funkcja wywołania zwrotnego dostarczonego przez użytkownika, która ma być wywoływana po zmianie interfejsu fizycznego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-1170">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1170">Return Values</span></span>

- <span data-ttu-id="8dd59-1171">Pomyślne ustawienie **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="8dd59-1172">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP lub Nowy wskaźnik adresu fizycznego</span><span class="sxs-lookup"><span data-stu-id="8dd59-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="8dd59-1173">Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="8dd59-1174">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1174">Allowed From</span></span>

<span data-ttu-id="8dd59-1175">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1176">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1176">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1177">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1178">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1179">See Also</span></span>

- <span data-ttu-id="8dd59-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="8dd59-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="8dd59-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="8dd59-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="8dd59-1184">Wyłącz wysyłanie/otrzymywanie pakietów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="8dd59-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-1185">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1186">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1186">Description</span></span>

<span data-ttu-id="8dd59-1187">Ta usługa wyłącza przekazywanie i odbieranie nieprzetworzonych pakietów IP dla tego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="8dd59-1188">Jeśli usługa pakietów RAW była wcześniej włączona, a w kolejce odbierania istnieją pakiety RAW, ta usługa zwolni wszystkie Odebrane pakiety pierwotne.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1189">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1189">Parameters</span></span>

- <span data-ttu-id="8dd59-1190">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1191">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1191">Return Values</span></span>

- <span data-ttu-id="8dd59-1192">**NX_SUCCESS** (0X00) pomyślnie wyłączono pakiet pierwotny IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="8dd59-1193">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1194">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1195">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1195">Allowed From</span></span>

<span data-ttu-id="8dd59-1196">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1197">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1197">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1198">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1199">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1200">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1200">See Also</span></span>

- <span data-ttu-id="8dd59-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="8dd59-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="8dd59-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="8dd59-1204">Włącz przetwarzanie pakietów nieprzetworzonych</span><span class="sxs-lookup"><span data-stu-id="8dd59-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-1205">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1206">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1206">Description</span></span>

<span data-ttu-id="8dd59-1207">Ta usługa umożliwia przekazywanie i odbieranie nieprzetworzonych pakietów IP dla tego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="8dd59-1208">Przychodzące pakiety TCP, UDP, ICMP i IGMP są nadal przetwarzane przez NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="8dd59-1209">Pakiety z nieznanymi typami protokołów warstwy wyższej są przetwarzane przez nieprzetworzoną procedurę odbierania pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1210">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1210">Parameters</span></span>

- <span data-ttu-id="8dd59-1211">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1212">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1212">Return Values</span></span>

- <span data-ttu-id="8dd59-1213">**NX_SUCCESS** (0X00) pomyślne włączenie pakietów pierwotnych adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="8dd59-1214">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1215">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1216">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1216">Allowed From</span></span>

<span data-ttu-id="8dd59-1217">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1218">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1218">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1219">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1220">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1221">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1221">See Also</span></span>

- <span data-ttu-id="8dd59-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="8dd59-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="8dd59-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="8dd59-1225">Wyślij pakiet Raw IP za poorednictwem określonego interfejsu sieciowego</span><span class="sxs-lookup"><span data-stu-id="8dd59-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1226">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="8dd59-1227">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1227">Description</span></span>

<span data-ttu-id="8dd59-1228">Ta usługa wysyła pakiet pierwotnego adresu IP do docelowego adresu IP przy użyciu określonego lokalnego adresu IP jako adresu źródłowego i za pośrednictwem skojarzonego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="8dd59-1229">Należy zauważyć, że ta procedura wraca natychmiast, a tym samym nie wiadomo, czy pakiet IP został faktycznie wysłany.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="8dd59-1230">Sterownik sieciowy będzie odpowiedzialny za wydanie pakietu, gdy transmisja zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="8dd59-1231">Ta usługa różni się od innych usług, ponieważ nie ma możliwości znajomości, czy pakiet został faktycznie wysłany.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="8dd59-1232">Może on zostać utracony przez Internet.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="8dd59-1233">*Należy pamiętać, że przetwarzanie Raw IP musi być włączone.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="8dd59-1234">*Ta usługa jest podobna do **nx_ip_raw_packet_send**, z tą różnicą, że ta usługa umożliwia aplikacji wysyłanie pakietów pierwotnych adresów IP z określonych interfejsów fizycznych.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1235">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1235">Parameters</span></span>

- <span data-ttu-id="8dd59-1236">**ip_ptr** Wskaźnik do wcześniej utworzonego zadania IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="8dd59-1237">**packet_ptr** Wskaźnik do pakietu do przesłania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="8dd59-1238">**destination_ip** Adres IP do wysłania pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="8dd59-1239">**address_index** Indeks adresu interfejsu, dla którego ma zostać wysłany pakiet.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="8dd59-1240">**Type_of_Service** Typ usługi dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1241">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1241">Return Values</span></span>

- <span data-ttu-id="8dd59-1242">Pomyślnie przesłano pakiet **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="8dd59-1243">**NX_IP_ADDRESS_ERROR** (0X21) nie jest dostępny odpowiedni interfejs wychodzący.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="8dd59-1244">**NX_NOT_ENABLED** (0x14) przetwarzanie pakietów Raw IP nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="8dd59-1245">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1246">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="8dd59-1247">**NX_OPTION_ERROR** (0x0A) określono nieprawidłowy typ usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="8dd59-1248">**NX_OVERFLOW** (0X03) Nieprawidłowy wskaźnik dołączania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="8dd59-1249">**NX_UNDERFLOW** (0X02) Nieprawidłowy wskaźnik dołączania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="8dd59-1250">**NX_INVALID_INTERFACE** (0x4C) określono nieprawidłowy indeks interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1251">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1251">Allowed From</span></span>

<span data-ttu-id="8dd59-1252">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1253">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1253">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1254">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1255">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1256">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1256">See Also</span></span>

- <span data-ttu-id="8dd59-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="8dd59-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="8dd59-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="8dd59-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="8dd59-1260">Odbierz pakiet pierwotnego adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1261">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1262">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1262">Description</span></span>

<span data-ttu-id="8dd59-1263">Ta usługa odbiera pakiet Raw IP od określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="8dd59-1264">Jeśli istnieją pakiety IP w kolejce odbierania pakietów nieprzetworzonych, pierwszy (najstarszy) pakiet jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="8dd59-1265">W przeciwnym razie, jeśli żaden pakiet nie jest dostępny, obiekt wywołujący może zawiesić się zgodnie z opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="8dd59-1266">*Jeśli NX_SUCCESS, jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1267">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1267">Parameters</span></span>

- <span data-ttu-id="8dd59-1268">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1269">**packet_ptr** Wskaźnik do wskaźnika, aby umieścić odebrany pakiet pierwotnego adresu IP w programie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="8dd59-1270">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli nie ma dostępnych pakietów pierwotnych adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="8dd59-1271">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1272">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1274">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1275">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1275">Return Values</span></span>

- <span data-ttu-id="8dd59-1276">**NX_SUCCESS** (0x00) odbieranie nieprzetworzonych pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="8dd59-1277">**NX_NO_PACKET** (0X01) Brak dostępnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="8dd59-1278">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-1279">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-1280">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pakietu zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="8dd59-1281">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="8dd59-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1282">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1282">Allowed From</span></span>

<span data-ttu-id="8dd59-1283">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1284">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1284">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1285">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1286">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1287">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1287">See Also</span></span>

- <span data-ttu-id="8dd59-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="8dd59-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="8dd59-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="8dd59-1291">Wyślij pakiet Raw IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1292">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="8dd59-1293">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1293">Description</span></span>

<span data-ttu-id="8dd59-1294">Ta usługa wysyła pakiet Raw IP do docelowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="8dd59-1295">Należy zauważyć, że ta procedura wraca natychmiast i dlatego nie wiadomo, czy pakiet IP został faktycznie wysłany.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="8dd59-1296">Sterownik sieciowy będzie odpowiedzialny za wydanie pakietu, gdy transmisja zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="8dd59-1297">W przypadku systemu wielodostępnego NetX używa docelowego adresu IP do znalezienia odpowiedniego interfejsu sieciowego i używa adresu IP interfejsu jako adresu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="8dd59-1298">Jeśli docelowy adres IP jest emisji lub multiemisji, używany jest pierwszy prawidłowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="8dd59-1299">Aplikacje używają ***nx_ip_raw_packet_interface_send*** w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="8dd59-1300">*Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po przekazaniu.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1301">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1301">Parameters</span></span>

- <span data-ttu-id="8dd59-1302">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1303">**packet_ptr** Wskaźnik na pakiet Raw IP do wysłania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="8dd59-1304">**destination_ip** Docelowy adres IP, który może być określonym adresem IP hosta, emisją sieci, pętlą wewnętrzną lub adresem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="8dd59-1305">**Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="8dd59-1306">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1307">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="8dd59-1308">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="8dd59-1309">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="8dd59-1310">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-1311">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1311">Return Values</span></span>

- <span data-ttu-id="8dd59-1312">**NX_SUCCESS** (0X00) pomyślnie zainicjowano wysyłanie pakietów pierwotnych adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="8dd59-1313">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-1314">Funkcja Raw IP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="8dd59-1315">**NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="8dd59-1316">**NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca do dołączania nagłówka IP do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="8dd59-1317">Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="8dd59-1318">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="8dd59-1319">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1320">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1320">Allowed From</span></span>

<span data-ttu-id="8dd59-1321">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1322">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1322">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1323">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1324">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1325">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1325">See Also</span></span>

- <span data-ttu-id="8dd59-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="8dd59-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="8dd59-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="8dd59-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="8dd59-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="8dd59-1330">Dodawanie trasy statycznej do tabeli routingu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1331">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="8dd59-1332">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1332">Description</span></span>

<span data-ttu-id="8dd59-1333">Ta usługa dodaje wpis do statycznej tabeli routingu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="8dd59-1334">Należy pamiętać, że adres *next_hop* musi być bezpośrednio dostępny z jednego z lokalnych urządzeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="8dd59-1335">*Należy zauważyć, że ip_ptr musi wskazywać prawidłową strukturę IP NetX, a Biblioteka NetX musi być skompilowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING zdefiniowanej do korzystania z tej usługi. Domyślnie NetX jest zbudowany bez zdefiniowanego NX_ENABLE_IP_STATIC_ROUTING.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1336">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1336">Parameters</span></span>

- <span data-ttu-id="8dd59-1337">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1338">**network_address** Docelowy adres sieciowy w kolejności bajtów hosta</span><span class="sxs-lookup"><span data-stu-id="8dd59-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="8dd59-1339">**net_mask** Docelowa maska sieci w kolejności bajtów hosta</span><span class="sxs-lookup"><span data-stu-id="8dd59-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="8dd59-1340">**next_hop** Adres następnego skoku dla sieci docelowej w kolejności bajtów hosta</span><span class="sxs-lookup"><span data-stu-id="8dd59-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1341">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1341">Return Values</span></span>

- <span data-ttu-id="8dd59-1342">Wpis **NX_SUCCESS** (0x00) jest dodawany do statycznej tabeli routingu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="8dd59-1343">Tabela routingu statycznego **NX_OVERFLOW** (0x03) jest pełna.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="8dd59-1344">**NX_NOT_SUPPORTED** (0X4B) Ta funkcja nie jest skompilowana w programie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="8dd59-1345">**NX_IP_ADDRESS_ERROR** (0X21) następnym przeskokiem nie jest bezpośrednio dostępny za pośrednictwem interfejsów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="8dd59-1346">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1347">**NX_PTR_ERROR** (0X07) nieprawidłowy wskaźnik ip_ptr.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1348">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1348">Allowed From</span></span>

<span data-ttu-id="8dd59-1349">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1350">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1350">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1351">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1352">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1353">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1353">See Also</span></span>

- <span data-ttu-id="8dd59-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="8dd59-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="8dd59-1356">Usuń trasę statyczną z tabeli routingu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1357">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="8dd59-1358">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1358">Description</span></span>

<span data-ttu-id="8dd59-1359">Ta usługa usuwa wpis z statycznej tabeli routingu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="8dd59-1360">*Należy zauważyć, że ip_ptr musi wskazywać prawidłową strukturę IP NetX, a Biblioteka NetX musi być skompilowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING zdefiniowanej do korzystania z tej usługi. Domyślnie NetX jest zbudowany bez zdefiniowanego NX_ENABLE_IP_STATIC_ROUTING.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1361">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1361">Parameters</span></span>

- <span data-ttu-id="8dd59-1362">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1363">**network_address** Docelowy adres sieciowy w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="8dd59-1364">**net_mask** Docelowa maska sieci w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1365">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1365">Allowed From</span></span>

<span data-ttu-id="8dd59-1366">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1367">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1367">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1368">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1369">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1370">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1370">See Also</span></span>

- <span data-ttu-id="8dd59-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="8dd59-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="8dd59-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-1372">nx_ip_status_check</span></span>

<span data-ttu-id="8dd59-1373">Sprawdź stan wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1374">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1375">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1375">Description</span></span>

<span data-ttu-id="8dd59-1376">Ta usługa sprawdza i opcjonalnie czeka na określony stan podstawowego interfejsu sieciowego utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="8dd59-1377">Aby uzyskać stan w interfejsach pomocniczych, aplikacje używają ***nx_ip_interface_status_check usługi.***</span><span class="sxs-lookup"><span data-stu-id="8dd59-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1378">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1378">Parameters</span></span>

- <span data-ttu-id="8dd59-1379">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1380">**needed_status** Żądany stan adresu IP, zdefiniowany w postaci mapy bitowej, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="8dd59-1381">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="8dd59-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="8dd59-1383">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="8dd59-1384">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="8dd59-1385">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="8dd59-1386">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="8dd59-1387">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="8dd59-1388">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="8dd59-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="8dd59-1390">**actual_status** Wskaźnik do miejsca docelowego rzeczywistego zestawu bitów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="8dd59-1391">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądane bity stanu są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="8dd59-1392">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1393">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1395">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1396">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1396">Return Values</span></span>

- <span data-ttu-id="8dd59-1397">Sprawdzanie stanu IP **NX_SUCCESS** (0x00) powiodło się.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="8dd59-1398">Żądanie stanu **NX_NOT_SUCCESSFUL** (0x43) nie było spełnione w określonym limicie czasu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="8dd59-1399">Wskaźnik IP **NX_PTR_ERROR** (0x07) ma wartość lub jest nieprawidłowy lub rzeczywisty wskaźnik stanu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="8dd59-1400">**NX_OPTION_ERROR** (0X0a) Nieprawidłowa opcja stanu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="8dd59-1401">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1402">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1402">Allowed From</span></span>

<span data-ttu-id="8dd59-1403">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1404">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1404">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1405">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1406">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1407">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1407">See Also</span></span>

- <span data-ttu-id="8dd59-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="8dd59-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="8dd59-1413">nx_packet_allocate</span></span>

<span data-ttu-id="8dd59-1414">Przydziel pakiet z określonej puli</span><span class="sxs-lookup"><span data-stu-id="8dd59-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1415">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1416">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1416">Description</span></span>

<span data-ttu-id="8dd59-1417">Ta usługa przydziela pakiet z określonej puli i dostosowuje wskaźnik dołączania w pakiecie zgodnie z typem określonego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="8dd59-1418">Jeśli pakiet nie jest dostępny, usługa zawiesza się zgodnie z podaną opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1419">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1419">Parameters</span></span>

- <span data-ttu-id="8dd59-1420">**pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="8dd59-1421">**packet_ptr** Wskaźnik do wskaźnika przydzieloną wskaźnik pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="8dd59-1422">**packet_type** Definiuje typ żądanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="8dd59-1423">Zobacz sekcję "pule pakietów" na stronie 49 w rozdziale 3, aby zapoznać się z listą obsługiwanych typów pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="8dd59-1424">**WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="8dd59-1425">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1426">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1428">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1429">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1429">Return Values</span></span>

- <span data-ttu-id="8dd59-1430">Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="8dd59-1431">**NX_NO_PACKET** (0X01) Brak dostępnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="8dd59-1432">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-1433">Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="8dd59-1434">**NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="8dd59-1435">**NX_PTR_ERROR** (0X07) Nieprawidłowa Pula lub wskaźnik powrotu pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="8dd59-1436">**NX_CALLER_ERROR** (0X11) Nieprawidłowa opcja oczekiwania z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1437">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1437">Allowed From</span></span>

<span data-ttu-id="8dd59-1438">Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="8dd59-1439">Opcja oczekiwania musi być NX_NO_WAIT, gdy jest używana w trybie ISR lub w kontekście czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1440">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1440">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1441">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1442">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1443">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1443">See Also</span></span>

- <span data-ttu-id="8dd59-1444">nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="8dd59-1447">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="8dd59-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="8dd59-1449">nx_packet_copy</span></span>

<span data-ttu-id="8dd59-1450">Kopiuj pakiet</span><span class="sxs-lookup"><span data-stu-id="8dd59-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1451">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1452">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1452">Description</span></span>

<span data-ttu-id="8dd59-1453">Ta usługa kopiuje informacje z dostarczonego pakietu do jednego lub kilku nowych pakietów, które są przydzielono z dostarczonej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="8dd59-1454">Jeśli to się powiedzie, wskaźnik do nowego pakietu jest zwracany w miejscu docelowym wskazywanym przez **new_packet_ptr**.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1455">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1455">Parameters</span></span>

- <span data-ttu-id="8dd59-1456">**packet_ptr** Wskaźnik na pakiet źródłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="8dd59-1457">**new_packet_ptr** Wskaźnik do miejsca docelowego, do którego ma zostać zwrócony wskaźnik do nowej kopii pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="8dd59-1458">**pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów, która jest używana do przydzielenia jednego lub większej liczby pakietów do kopiowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="8dd59-1459">**WAIT_OPTION** Definiuje, w jaki sposób usługa czeka, jeśli nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="8dd59-1460">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1461">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1463">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1464">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1464">Return Values</span></span>
- <span data-ttu-id="8dd59-1465">Pomyślna kopia pakietu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="8dd59-1466">Pakiet **NX_NO_PACKET** (0x01) nie jest dostępny do kopiowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="8dd59-1467">**NX_INVALID_PACKET** (0X12) pusty pakiet źródłowy lub kopiowanie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="8dd59-1468">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-1469">Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="8dd59-1470">**NX_PTR_ERROR** (0X07) Nieprawidłowa Pula, pakiet lub wskaźnik docelowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="8dd59-1471">**NX_UNDERFLOW** (0X02) Nieprawidłowy wskaźnik dołączania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="8dd59-1472">**NX_OVERFLOW** (0X03) Nieprawidłowy wskaźnik dołączania pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="8dd59-1473">**NX_CALLER_ERROR** (0x11) opcja oczekiwania została określona w inicjalizacji lub w ramach procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1474">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1474">Allowed From</span></span>

<span data-ttu-id="8dd59-1475">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1476">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1476">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1477">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1478">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1479">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1479">See Also</span></span>

- <span data-ttu-id="8dd59-1480">nx_packet_allocate, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="8dd59-1483">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="8dd59-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1485">nx_packet_data_append</span></span>

<span data-ttu-id="8dd59-1486">Dołącz dane do końca pakietu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1487">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1488">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1488">Description</span></span>

<span data-ttu-id="8dd59-1489">Ta usługa dołącza dane na końcu określonego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="8dd59-1490">Dostarczony obszar danych jest kopiowany do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="8dd59-1491">Jeśli jest za mało dostępnej pamięci, a funkcja pakiet łańcucha jest włączona, co najmniej jeden pakiet zostanie przydzielony do spełnienia żądania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="8dd59-1492">Jeśli funkcja pakietu łańcucha nie jest włączona, zostanie zwrócona *NX_SIZE_ERROR* .</span><span class="sxs-lookup"><span data-stu-id="8dd59-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1493">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1493">Parameters</span></span>

- <span data-ttu-id="8dd59-1494">**packet_ptr** Wskaźnik pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="8dd59-1495">**data_start** Wskaźnik na początek obszaru danych użytkownika do dołączenia do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="8dd59-1496">**data_size** Rozmiar obszaru danych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="8dd59-1497">**pool_ptr** Wskaźnik do puli pakietów, z której ma zostać przydzielony inny pakiet, jeśli w bieżącym pakiecie nie ma wystarczającej ilości miejsca.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="8dd59-1498">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="8dd59-1499">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1500">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1502">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1503">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1503">Return Values</span></span>

- <span data-ttu-id="8dd59-1504">**NX_SUCCESS** (0x00) pomyślnego dołączenia do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="8dd59-1505">**NX_NO_PACKET** (0X01) Brak dostępnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="8dd59-1506">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="8dd59-1507">Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="8dd59-1508">Wskaźnik prefiksu **NX_UNDERFLOW** (0x02) jest mniejszy niż początek ładunku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="8dd59-1509">**NX_OVERFLOW** (0x03) dołączany wskaźnik jest większy niż koniec ładunku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="8dd59-1510">**NX_PTR_ERROR** (0X07) Nieprawidłowa Pula, pakiet lub wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="8dd59-1511">**NX_SIZE_ERROR** (0X09) Nieprawidłowy rozmiar danych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="8dd59-1512">**NX_CALLER_ERROR** (0X11) Nieprawidłowa opcja oczekiwania z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1513">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1513">Allowed From</span></span>

<span data-ttu-id="8dd59-1514">Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1515">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1515">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1516">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1517">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="8dd59-1518">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1518">See Also</span></span>

- <span data-ttu-id="8dd59-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="8dd59-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="8dd59-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="8dd59-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="8dd59-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="8dd59-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="8dd59-1524">Wyodrębnij dane z pakietu za pośrednictwem przesunięcia</span><span class="sxs-lookup"><span data-stu-id="8dd59-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1525">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="8dd59-1526">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1526">Description</span></span>

<span data-ttu-id="8dd59-1527">Ta usługa kopiuje dane z pakietu NetX (lub łańcucha pakietów), rozpoczynając od określonego przesunięcia od wskaźnika dołączania pakietu o określonym rozmiarze w bajtach do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="8dd59-1528">Liczba bajtów w rzeczywistości kopiowanych jest zwracana w *bytes_copied.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="8dd59-1529">Ta usługa nie usuwa danych z pakietu ani nie dostosowuje wskaźnika dołączania ani innych informacji o stanie wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1530">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1530">Parameters</span></span>

- <span data-ttu-id="8dd59-1531">**packet_ptr** Wskaźnik do pakietu do wyodrębnienia</span><span class="sxs-lookup"><span data-stu-id="8dd59-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="8dd59-1532">**przesunięcie** Przesunięcie od bieżącego wskaźnika dołączania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="8dd59-1533">**buffer_start** Wskaźnik do początku zapisu bufora</span><span class="sxs-lookup"><span data-stu-id="8dd59-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="8dd59-1534">**BUFFER_LENGTH** Liczba bajtów do skopiowania</span><span class="sxs-lookup"><span data-stu-id="8dd59-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="8dd59-1535">**bytes_copied** Liczba bajtów rzeczywiście skopiowanych</span><span class="sxs-lookup"><span data-stu-id="8dd59-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1536">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1536">Return Values</span></span>

- <span data-ttu-id="8dd59-1537">Pomyślna kopia pakietu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="8dd59-1538">**NX_PACKET_OFFSET_ERROR** (0x53) podano nieprawidłową wartość przesunięcia</span><span class="sxs-lookup"><span data-stu-id="8dd59-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="8dd59-1539">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu lub wskaźnik buforu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1540">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1540">Allowed From</span></span>

<span data-ttu-id="8dd59-1541">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1542">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1542">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1543">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1544">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1545">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1545">See Also</span></span>

- <span data-ttu-id="8dd59-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="8dd59-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="8dd59-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="8dd59-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="8dd59-1551">Pobieranie danych z pakietu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1552">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="8dd59-1553">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1553">Description</span></span>

<span data-ttu-id="8dd59-1554">Ta usługa kopiuje dane z dostarczonego pakietu do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="8dd59-1555">Rzeczywista liczba skopiowanych bajtów jest zwracana w miejscu docelowym wskazywanym przez **bytes_copied**.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="8dd59-1556">Należy zauważyć, że ta usługa nie zmienia wewnętrznego stanu pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="8dd59-1557">Pobierane dane są nadal dostępne w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="8dd59-1558">*Bufor docelowy musi być wystarczająco duży, aby można było przechowywać zawartość pakietu. W przeciwnym razie pamięć zostanie uszkodzona, powodując nieprzewidywalne wyniki.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1559">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1559">Parameters</span></span>

- <span data-ttu-id="8dd59-1560">**packet_ptr** Wskaźnik na pakiet źródłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="8dd59-1561">**buffer_start** Wskaźnik na początek obszaru bufora.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="8dd59-1562">**bytes_copied** Wskaźnik do miejsca docelowego dla liczby kopiowanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1563">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1563">Return Values</span></span>

- <span data-ttu-id="8dd59-1564">**NX_SUCCESS** (0X00) pomyślne pobranie danych pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="8dd59-1565">**NX_INVALID_PACKET** (0X12) nieprawidłowy pakiet.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="8dd59-1566">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik skopiowanego pakietu, uruchomienia buforu lub bajtów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1567">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1567">Allowed From</span></span>

<span data-ttu-id="8dd59-1568">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1569">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1569">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1570">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1571">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1572">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1572">See Also</span></span>

- <span data-ttu-id="8dd59-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="8dd59-1575">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="8dd59-1576">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="8dd59-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1578">nx_packet_length_get</span></span>

<span data-ttu-id="8dd59-1579">Pobierz długość danych pakietu</span><span class="sxs-lookup"><span data-stu-id="8dd59-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1580">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="8dd59-1581">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1581">Description</span></span>

<span data-ttu-id="8dd59-1582">Ta usługa Pobiera długość danych w określonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1583">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1583">Parameters</span></span>

- <span data-ttu-id="8dd59-1584">**packet_ptr** Wskaźnik do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="8dd59-1585">**Długość** Wartość docelowa dla długości pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1586">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1586">Allowed From</span></span>

<span data-ttu-id="8dd59-1587">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1588">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1588">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1589">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1590">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1591">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1591">See Also</span></span>

- <span data-ttu-id="8dd59-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1594">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="8dd59-1595">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="8dd59-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="8dd59-1598">Utwórz pulę pakietów w określonym obszarze pamięci</span><span class="sxs-lookup"><span data-stu-id="8dd59-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1599">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="8dd59-1600">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1600">Description</span></span>

<span data-ttu-id="8dd59-1601">Ta usługa tworzy pulę pakietów o określonym rozmiarze pakietu w obszarze pamięci dostarczonym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1602">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1602">Parameters</span></span>

- <span data-ttu-id="8dd59-1603">**pool_ptr** Wskaźnik do bloku kontroli puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="8dd59-1604">**Nazwa** Wskaźnik do nazwy aplikacji dla puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="8dd59-1605">**payload_size** Liczba bajtów w każdym pakiecie w puli.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="8dd59-1606">Ta wartość musi być równa co najmniej 40 bajtów i musi być również niewidoczna przez 4.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="8dd59-1607">**memory_ptr** Wskaźnik do obszaru pamięci, w którym ma zostać umieszczona Pula pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="8dd59-1608">Wskaźnik powinien być wyrównany na granicy ULONG.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="8dd59-1609">**memory_size** Rozmiar obszaru pamięci puli.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1610">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1610">Return Values</span></span>

- <span data-ttu-id="8dd59-1611">**NX_SUCCESS** (0X00) pomyślnie utworzono pulę pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="8dd59-1612">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik puli lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="8dd59-1613">**NX_SIZE_ERROR** (0X09) Nieprawidłowy rozmiar bloku lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="8dd59-1614">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1615">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1615">Allowed From</span></span>

<span data-ttu-id="8dd59-1616">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1617">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1617">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1618">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1619">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1620">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1620">See Also</span></span>

- <span data-ttu-id="8dd59-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="8dd59-1624">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="8dd59-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="8dd59-1626">Usuń wcześniej utworzoną pulę pakietów</span><span class="sxs-lookup"><span data-stu-id="8dd59-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1627">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1628">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1628">Description</span></span>

<span data-ttu-id="8dd59-1629">Ta usługa usuwa wcześniej utworzoną pulę pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="8dd59-1630">NetX sprawdza, czy wszystkie wątki są aktualnie zawieszone w pakietach w puli pakietów i czyści zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1631">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1631">Parameters</span></span>

- <span data-ttu-id="8dd59-1632">**pool_ptr** Wskaźnik bloku kontroli puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1633">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1633">Return Values</span></span>

- <span data-ttu-id="8dd59-1634">**NX_SUCCESS** (0X00) pomyślne usunięcie puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="8dd59-1635">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik puli.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="8dd59-1636">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1637">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1637">Allowed From</span></span>

<span data-ttu-id="8dd59-1638">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1639">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1639">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1640">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1641">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1642">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1642">See Also</span></span>

- <span data-ttu-id="8dd59-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1645">nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="8dd59-1646">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="8dd59-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="8dd59-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="8dd59-1649">Pobieranie informacji o puli pakietów</span><span class="sxs-lookup"><span data-stu-id="8dd59-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1650">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="8dd59-1651">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1651">Description</span></span>

<span data-ttu-id="8dd59-1652">Ta usługa pobiera informacje o określonej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="8dd59-1653">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1654">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1654">Parameters</span></span>

- <span data-ttu-id="8dd59-1655">**pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="8dd59-1656">**total_packets** Wskaźnik do miejsca docelowego dla łącznej liczby pakietów w puli.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="8dd59-1657">**free_packets** Wskaźnik do miejsca docelowego dla łącznej liczby aktualnie bezpłatnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="8dd59-1658">**empty_pool_requests** Wskaźnik do lokalizacji docelowej łącznej liczby żądań alokacji, gdy pula była pusta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="8dd59-1659">**empty_pool_suspensions** Wskaźnik do lokalizacji docelowej łącznej liczby pustych zawieszeń puli.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="8dd59-1660">**invalid_packet_releases** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1661">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1661">Return Values</span></span>

- <span data-ttu-id="8dd59-1662">**NX_SUCCESS** (0x00) pobieranie informacji o puli pakietów powiodło się.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="8dd59-1663">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1664">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1665">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1665">Allowed From</span></span>

<span data-ttu-id="8dd59-1666">Inicjalizacja, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1667">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1667">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1668">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1669">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1670">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1670">See Also</span></span>

- <span data-ttu-id="8dd59-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="8dd59-1674">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="8dd59-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1675">nx_packet_release</span></span>

<span data-ttu-id="8dd59-1676">Zwolnij wcześniej przydzieloną pakietów</span><span class="sxs-lookup"><span data-stu-id="8dd59-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1677">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1678">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1678">Description</span></span>

<span data-ttu-id="8dd59-1679">Ta usługa zwalnia pakiet, w tym wszystkie dodatkowe pakiety powiązane z określonym pakietem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="8dd59-1680">Jeśli inny wątek jest blokowany w alokacji pakietów, otrzymuje pakiet i został wznowiony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="8dd59-1681">*Aplikacja musi uniemożliwiać zwolnienie pakietu więcej niż raz, ponieważ takie działanie spowoduje nieprzewidywalne wyniki.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1682">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1682">Parameters</span></span>

- <span data-ttu-id="8dd59-1683">**packet_ptr** Wskaźnik pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-1684">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1684">Return Values</span></span>
- <span data-ttu-id="8dd59-1685">**NX_SUCCESS** (0X00) pomyślne wydanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="8dd59-1686">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="8dd59-1687">Wskaźnik prefiksu **NX_UNDERFLOW** (0x02) jest mniejszy niż początek ładunku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="8dd59-1688">**NX_OVERFLOW** (0x03) dołączany wskaźnik jest większy niż koniec ładunku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1689">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1689">Allowed From</span></span>

<span data-ttu-id="8dd59-1690">Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1691">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1691">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1692">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1693">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1694">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1694">See Also</span></span>

- <span data-ttu-id="8dd59-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="8dd59-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="8dd59-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="8dd59-1700">Zwolnij przesłany pakiet</span><span class="sxs-lookup"><span data-stu-id="8dd59-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1701">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1702">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1702">Description</span></span>

<span data-ttu-id="8dd59-1703">W przypadku pakietów innych niż TCP ta usługa zwalnia przesyłany pakiet, w tym wszystkie dodatkowe pakiety połączone z określonym pakietem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="8dd59-1704">Jeśli inny wątek jest blokowany w alokacji pakietów, otrzymuje pakiet i został wznowiony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="8dd59-1705">W przypadku przesyłanego pakietu TCP pakiet jest oznaczany jako przesyłany, ale nie jest uwalniany do momentu potwierdzenia pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="8dd59-1706">Ta usługa jest zwykle wywoływana ze sterownika sieci aplikacji po przesłaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="8dd59-1707">*Sterownik sieciowy powinien usunąć nagłówek nośnika fizycznego i dostosować długość pakietu przed wywołaniem tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1708">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1708">Parameters</span></span>

- <span data-ttu-id="8dd59-1709">**packet_ptr** Wskaźnik pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1710">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1710">Return Values</span></span>

- <span data-ttu-id="8dd59-1711">**NX_SUCCESS** (0x00) pomyślna transmisja pakietów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="8dd59-1712">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="8dd59-1713">Wskaźnik prefiksu **NX_UNDERFLOW** (0x02) jest mniejszy niż początek ładunku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="8dd59-1714">**NX_OVERFLOW** (0x03) dołączany wskaźnik jest większy niż koniec ładunku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1715">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1715">Allowed From</span></span>

<span data-ttu-id="8dd59-1716">Inicjalizacja, wątki, czasomierze, sterowniki sieciowe aplikacji (w tym procedury ISR)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1717">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1717">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1718">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1719">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1720">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1720">See Also</span></span>

- <span data-ttu-id="8dd59-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="8dd59-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="8dd59-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="8dd59-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="8dd59-1724">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="8dd59-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="8dd59-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-1725">nx_rarp_disable</span></span>

<span data-ttu-id="8dd59-1726">Wyłącz protokół odwrotnego rozpoznawania adresów (RARP)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1727">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1728">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1728">Description</span></span>

<span data-ttu-id="8dd59-1729">Ta usługa wyłącza składnik RARP elementu NetX dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="8dd59-1730">W przypadku systemu wielodomowego ta usługa wyłącza RARP na wszystkich interfejsach.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1731">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1731">Parameters</span></span>

- <span data-ttu-id="8dd59-1732">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1733">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1733">Return Values</span></span>

- <span data-ttu-id="8dd59-1734">**NX_SUCCESS** (0X00) POMYŚLNE wyłączenie RARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="8dd59-1735">Nie włączono **NX_NOT_ENABLED** (0X14) RARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="8dd59-1736">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1737">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1738">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1738">Allowed From</span></span>

<span data-ttu-id="8dd59-1739">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1740">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1740">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1741">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1742">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1743">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1743">See Also</span></span>

- <span data-ttu-id="8dd59-1744">nx_rarp_enable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="8dd59-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-1745">nx_rarp_enable</span></span>

<span data-ttu-id="8dd59-1746">Włącz protokół odwrotnego rozpoznawania adresów (RARP)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1747">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1748">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1748">Description</span></span>

<span data-ttu-id="8dd59-1749">Ta usługa włącza składnik RARP NetX dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="8dd59-1750">Składniki RARP przeszukują wszystkie podłączone interfejsy sieciowe dla zerowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="8dd59-1751">Zerowy adres IP wskazuje, że interfejs nie ma jeszcze przypisywania adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="8dd59-1752">RARP próbuje rozpoznać adres IP, włączając proces RARP w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1753">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1753">Parameters</span></span>

- <span data-ttu-id="8dd59-1754">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1755">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1755">Return Values</span></span>

- <span data-ttu-id="8dd59-1756">**NX_SUCCESS** (0X00) POMYŚLNE włączenie RARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="8dd59-1757">Adres IP **NX_IP_ADDRESS_ERROR** (0x21) jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="8dd59-1758">**NX_ALREADY_ENABLED** (0X15) RARP został już włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="8dd59-1759">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1760">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1761">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1761">Allowed From</span></span>

<span data-ttu-id="8dd59-1762">Inicjalizacja, wątki, czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1763">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1763">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1764">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1765">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1766">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1766">See Also</span></span>

- <span data-ttu-id="8dd59-1767">nx_rarp_disable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="8dd59-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="8dd59-1769">Pobierz informacje o działaniach RARP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1770">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="8dd59-1771">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1771">Description</span></span>

<span data-ttu-id="8dd59-1772">Ta usługa pobiera informacje o działaniach RARP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-1773">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1774">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1774">Parameters</span></span>

- <span data-ttu-id="8dd59-1775">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1776">**rarp_requests_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych żądań RARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="8dd59-1777">**rarp_responses_received** Wskaźnik do miejsca docelowego dla łącznej liczby odebranych odpowiedzi RARP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="8dd59-1778">**rarp_invalid_messages** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-1779">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1779">Return Values</span></span>
- <span data-ttu-id="8dd59-1780">**NX_SUCCESS** (0X00) pomyślnie RARP pobieranie informacji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="8dd59-1781">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1782">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-1783">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1784">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1784">Allowed From</span></span>

<span data-ttu-id="8dd59-1785">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1786">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1786">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1787">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1788">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1789">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1789">See Also</span></span>

- <span data-ttu-id="8dd59-1790">nx_rarp_disable, nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="8dd59-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="8dd59-1791">nx_system_initialize</span></span>

<span data-ttu-id="8dd59-1792">Zainicjuj system NetX</span><span class="sxs-lookup"><span data-stu-id="8dd59-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1793">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="8dd59-1794">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1794">Description</span></span>

<span data-ttu-id="8dd59-1795">Ta usługa inicjuje podstawowe zasoby systemowe NetX w przygotowaniu do użycia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="8dd59-1796">Powinien być wywoływany przez aplikację podczas inicjowania i przed innymi wywołaniami NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1797">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1797">Parameters</span></span>

<span data-ttu-id="8dd59-1798">Brak</span><span class="sxs-lookup"><span data-stu-id="8dd59-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1799">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1799">Return Values</span></span>

<span data-ttu-id="8dd59-1800">Brak</span><span class="sxs-lookup"><span data-stu-id="8dd59-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1801">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1801">Allowed From</span></span>

<span data-ttu-id="8dd59-1802">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1803">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1803">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1804">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1805">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1806">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1806">See Also</span></span>

- <span data-ttu-id="8dd59-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="8dd59-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="8dd59-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="8dd59-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="8dd59-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="8dd59-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="8dd59-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="8dd59-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="8dd59-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="8dd59-1813">Powiąż gniazdo TCP klienta z portem TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1814">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1815">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1815">Description</span></span>

<span data-ttu-id="8dd59-1816">Ta usługa wiąże wcześniej utworzone gniazdo klienta TCP z określonym portem TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="8dd59-1817">Prawidłowy zakres TCP Sockets należy do zakresu od 0 do 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="8dd59-1818">Jeśli określony port TCP jest niedostępny, usługa zawiesza się zgodnie z podaną opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1819">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1819">Parameters</span></span>

- <span data-ttu-id="8dd59-1820">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-1821">**port** Numer portu do powiązania (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="8dd59-1822">Jeśli numer portu to NX_ANY_PORT (0x0000), wystąpienie protokołu IP wyszuka następny bezpłatny port i użyje go do powiązania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="8dd59-1823">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli port jest już powiązany z innym gniazdem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="8dd59-1824">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1825">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1827">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1828">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1828">Return Values</span></span>

- <span data-ttu-id="8dd59-1829">**NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="8dd59-1830">**NX_ALREADY_BOUND** (0X22) to gniazdo jest już powiązane z innym portem TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="8dd59-1831">Port **NX_PORT_UNAVAILABLE** (0x23) jest już powiązany z innym gniazdem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="8dd59-1832">**NX_NO_FREE_PORTS** (0X45) brak wolnego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="8dd59-1833">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="8dd59-1834">**NX_INVALID_PORT** (0X46) nieprawidłowy port.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="8dd59-1835">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-1836">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1837">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1838">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1838">Allowed From</span></span>

<span data-ttu-id="8dd59-1839">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1840">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1840">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1841">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1842">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1843">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1843">See Also</span></span>

- <span data-ttu-id="8dd59-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="8dd59-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="8dd59-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="8dd59-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="8dd59-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="8dd59-1855">Połącz gniazdo TCP klienta</span><span class="sxs-lookup"><span data-stu-id="8dd59-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1856">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-1857">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1857">Description</span></span>

<span data-ttu-id="8dd59-1858">Ta usługa łączy wcześniej utworzone i powiązane gniazdo klienta TCP z portem określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="8dd59-1859">Prawidłowe porty serwera TCP mieszczą się w zakresie od 0 do 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="8dd59-1860">Jeśli połączenie nie zakończy się natychmiast, usługa zawiesza się zgodnie z podaną opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1861">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1861">Parameters</span></span>

- <span data-ttu-id="8dd59-1862">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-1863">**server_IP** Adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="8dd59-1864">**SERVER_PORT** Numer portu serwera, z którym ma zostać nawiązane połączenie (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="8dd59-1865">**WAIT_OPTION** Definiuje sposób zachowania usługi podczas ustanawiania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="8dd59-1866">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-1867">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-1869">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1870">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1870">Return Values</span></span>

- <span data-ttu-id="8dd59-1871">**NX_SUCCESS** (0x00) pomyślnego nawiązania połączenia z gniazdem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="8dd59-1872">Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="8dd59-1873">Gniazdo **NX_NOT_CLOSED** (0x35) nie jest w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="8dd59-1874">**NX_IN_PROGRESS** (0X37) nie określono oczekiwania, próba połączenia jest w toku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="8dd59-1875">**NX_INVALID_INTERFACE** (0x4C) podano nieprawidłowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="8dd59-1876">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-1877">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="8dd59-1878">**NX_INVALID_PORT** (0X46) nieprawidłowy port.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="8dd59-1879">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-1880">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1881">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1882">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1882">Allowed From</span></span>

<span data-ttu-id="8dd59-1883">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1884">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1884">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1885">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1886">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1887">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1887">See Also</span></span>

- <span data-ttu-id="8dd59-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="8dd59-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="8dd59-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="8dd59-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="8dd59-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="8dd59-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="8dd59-1899">Pobieranie numeru portu powiązanego z gniazdem TCP klienta</span><span class="sxs-lookup"><span data-stu-id="8dd59-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1900">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1901">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1901">Description</span></span>

<span data-ttu-id="8dd59-1902">Ta usługa Pobiera numer portu skojarzony z gniazdem, który jest przydatny do znajdowania portu przydzielonego przez NetX w sytuacjach, w których NX_ANY_PORT został określony w momencie powiązania gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1903">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1903">Parameters</span></span>

- <span data-ttu-id="8dd59-1904">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-1905">**port_ptr** Wskaźnik do miejsca docelowego dla numeru portu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="8dd59-1906">Prawidłowe numery portów to (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1907">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1907">Return Values</span></span>

- <span data-ttu-id="8dd59-1908">**NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="8dd59-1909">**NX_NOT_BOUND** (0X24) to gniazdo nie jest powiązane z portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="8dd59-1910">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda lub zwracany przez port wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="8dd59-1911">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1912">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1913">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1913">Allowed From</span></span>

<span data-ttu-id="8dd59-1914">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1915">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1915">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1916">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1917">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1918">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1918">See Also</span></span>

- <span data-ttu-id="8dd59-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="8dd59-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="8dd59-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="8dd59-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="8dd59-1930">Usuń powiązanie gniazda klienta TCP z portu TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1931">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1932">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1932">Description</span></span>

<span data-ttu-id="8dd59-1933">Ta usługa zwalnia powiązanie między gniazdem klienta TCP i portem TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="8dd59-1934">Jeśli istnieją inne wątki oczekujące na powiązanie innego gniazda z tym samym numerem portu, pierwszy zawieszony wątek zostanie powiązany z tym portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1935">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1935">Parameters</span></span>

- <span data-ttu-id="8dd59-1936">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1937">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1937">Return Values</span></span>

- <span data-ttu-id="8dd59-1938">**NX_SUCCESS** (0x00) odpinanie gniazda zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="8dd59-1939">Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="8dd59-1940">Gniazdo **NX_NOT_CLOSED** (0x35) nie zostało odłączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="8dd59-1941">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-1942">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-1943">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1944">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1944">Allowed From</span></span>

<span data-ttu-id="8dd59-1945">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1946">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1946">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1947">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1948">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1949">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1949">See Also</span></span>

- <span data-ttu-id="8dd59-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="8dd59-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="8dd59-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-1960">nx_tcp_enable</span></span>

<span data-ttu-id="8dd59-1961">Włącz składnik TCP elementu NetX</span><span class="sxs-lookup"><span data-stu-id="8dd59-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1962">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1963">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1963">Description</span></span>

<span data-ttu-id="8dd59-1964">Ta usługa włącza składnik Transmission Control Protocol (TCP) NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="8dd59-1965">Po włączeniu połączenia TCP mogą być nawiązywane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1966">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1966">Parameters</span></span>

- <span data-ttu-id="8dd59-1967">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-1968">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-1968">Return Values</span></span>

- <span data-ttu-id="8dd59-1969">**NX_SUCCESS** (0X00) pomyślne włączenie protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="8dd59-1970">**NX_ALREADY_ENABLED** (0X15) TCP jest już włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="8dd59-1971">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-1972">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-1973">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-1973">Allowed From</span></span>

<span data-ttu-id="8dd59-1974">Inicjalizacja, wątki, czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-1975">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1975">Preemption Possible</span></span>

<span data-ttu-id="8dd59-1976">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-1977">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-1978">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-1978">See Also</span></span>

- <span data-ttu-id="8dd59-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="8dd59-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="8dd59-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="8dd59-1990">Znajdź następny dostępny port TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-1991">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-1992">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-1992">Description</span></span>

<span data-ttu-id="8dd59-1993">Ta usługa próbuje zlokalizować bezpłatny port TCP (niepowiązany), rozpoczynając od portu dostarczonego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="8dd59-1994">Logika wyszukiwania zostanie zawinięty, jeśli wyszukiwanie nastąpi do osiągnięcia maksymalnej wartości maksymalnego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="8dd59-1995">Jeśli wyszukiwanie zakończyło się pomyślnie, port wolny jest zwracany w zmiennej wskazywanej przez *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="8dd59-1996">*Ta usługa może być wywoływana z innego wątku i ma ten sam port. Aby uniknąć tego warunku wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda klienta w ramach ochrony obiektu mutex.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-1997">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-1997">Parameters</span></span>

- <span data-ttu-id="8dd59-1998">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-1999">**port** Numer portu, aby rozpocząć wyszukiwanie (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="8dd59-2000">**free_port_ptr** Wskaźnik na wartość zwrotną wolnego portu docelowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2001">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2001">Return Values</span></span>

- <span data-ttu-id="8dd59-2002">**NX_SUCCESS** (0X00) pomyślne znalezienie bezpłatnego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="8dd59-2003">**NX_NO_FREE_PORTS** (0X45) nie znaleziono wolnych portów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="8dd59-2004">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-2005">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2006">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-2007">**NX_INVALID_PORT** (0x46) określony numer portu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2008">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2008">Allowed From</span></span>

<span data-ttu-id="8dd59-2009">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2010">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2010">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2011">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2012">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2013">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2013">See Also</span></span>

- <span data-ttu-id="8dd59-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="8dd59-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="8dd59-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="8dd59-2025">Pobierz informacje o działaniach TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2026">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="8dd59-2027">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2027">Description</span></span>

<span data-ttu-id="8dd59-2028">Ta usługa pobiera informacje o działaniach TCP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-2029">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2030">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2030">Parameters</span></span>

- <span data-ttu-id="8dd59-2031">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2032">**tcp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="8dd59-2033">**tcp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych bajtów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="8dd59-2034">**tcp_packets_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="8dd59-2035">**tcp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych bajtów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="8dd59-2036">**tcp_invalid_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="8dd59-2037">**tcp_receive_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów TCP odbioru.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="8dd59-2038">**tcp_checksum_errors** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów TCP z błędami sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="8dd59-2039">**tcp_connections** Wskaźnik do lokalizacji docelowej łącznej liczby połączeń TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="8dd59-2040">**tcp_disconnections** Wskaźnik do lokalizacji docelowej łącznej liczby odniesień protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="8dd59-2041">**tcp_connections_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych połączeń TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="8dd59-2042">**tcp_retransmit_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby przesłanych pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2043">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2043">Return Values</span></span>

- <span data-ttu-id="8dd59-2044">**NX_SUCCESS** (0X00) pomyślne pobieranie informacji TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="8dd59-2045">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-2046">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2047">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2048">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2048">Allowed From</span></span>

<span data-ttu-id="8dd59-2049">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2050">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2050">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2051">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2052">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2053">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2053">See Also</span></span>

- <span data-ttu-id="8dd59-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="8dd59-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="8dd59-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="8dd59-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="8dd59-2065">Zaakceptuj połączenie TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2066">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-2067">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2067">Description</span></span>

<span data-ttu-id="8dd59-2068">Ta usługa akceptuje (lub przygotowuje do akceptowania) żądanie połączenia gniazda klienta TCP dla portu, który został wcześniej skonfigurowany do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="8dd59-2069">Ta usługa może być wywoływana natychmiast po wywołaniu przez aplikację nasłuchiwania lub ponownego nasłuchiwania albo gdy wywoływana jest procedura wywołania zwrotnego Listen, gdy połączenie z klientem jest rzeczywiście obecne.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="8dd59-2070">Jeśli połączenie nie może być od razu ustanowione, usługa zawiesza się zgodnie z podaną opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="8dd59-2071">*Aplikacja musi wywoływać **nx_tcp_server_socket_unaccept** , gdy połączenie nie jest już potrzebne do usunięcia powiązania gniazda serwera z portem serwera.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="8dd59-2072">*Procedury wywołania zwrotnego aplikacji są wywoływane z wewnątrz wątku pomocnika IP.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2073">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2073">Parameters</span></span>

- <span data-ttu-id="8dd59-2074">**socket_ptr** Wskaźnik do bloku sterowania gniazda serwera TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="8dd59-2075">**WAIT_OPTION** Definiuje sposób zachowania usługi podczas ustanawiania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="8dd59-2076">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2077">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-2079">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-2080">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2080">Return Values</span></span>
- <span data-ttu-id="8dd59-2081">**NX_SUCCESS** (0X00) pomyślne zaakceptowanie gniazda serwera TCP (połączenie pasywne).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="8dd59-2082">**NX_NOT_LISTEN_STATE** (0x36) dostarczony gniazdo serwera nie jest w stanie nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="8dd59-2083">**NX_IN_PROGRESS** (0X37) nie określono oczekiwania, próba połączenia jest w toku.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="8dd59-2084">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="8dd59-2085">Błąd wskaźnika gniazda **NX_PTR_ERROR** (0x07).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="8dd59-2086">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2087">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2088">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2088">Allowed From</span></span>

<span data-ttu-id="8dd59-2089">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2090">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2090">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2091">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2092">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2093">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2093">See Also</span></span>

- <span data-ttu-id="8dd59-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="8dd59-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="8dd59-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="8dd59-2105">Włącz nasłuchiwanie połączenia klienta na porcie TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2106">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="8dd59-2107">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2107">Description</span></span>

<span data-ttu-id="8dd59-2108">Ta usługa umożliwia nasłuchiwanie żądania połączenia klienta na określonym porcie TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="8dd59-2109">Po odebraniu żądania połączenia z klientem podane gniazdo serwera jest powiązane z określonym portem i wywoływana funkcja wywołania zwrotnego nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="8dd59-2110">Przetwarzanie procedury wywołania zwrotnego Listen jest całkowicie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="8dd59-2111">Może on zawierać logikę do wznowienia wątku aplikacji, który następnie wykonuje operację akceptacji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="8dd59-2112">Jeśli aplikacja ma już zawieszony wątek przy akceptowaniu przetwarzania dla tego gniazda, procedura wywołania zwrotnego odbiornika może nie być wymagana.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="8dd59-2113">Jeśli aplikacja chce obsługiwać dodatkowe połączenia klientów na tym samym porcie, ***nx_tcp_server_socket_relisten*** musi zostać wywołana z dostępnym gniazdem (gniazdo w stanie zamkniętym) dla następnego połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="8dd59-2114">Do momentu wywołania usługi ponownego nasłuchiwania dodatkowe połączenia klienckie są umieszczane w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="8dd59-2115">Po przekroczeniu maksymalnej głębokości kolejki żądanie najstarszego połączenia zostanie porzucone na rzecz kolejkowania nowego żądania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="8dd59-2116">Maksymalna głębokość kolejki jest określona przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="8dd59-2117">*Procedury wywołania zwrotnego aplikacji są wywoływane z wątku pomocnika wewnętrznego adresu IP.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2118">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2118">Parameters</span></span>

- <span data-ttu-id="8dd59-2119">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2120">**port** Numer portu, na którym nasłuchuje nasłuchiwanie (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="8dd59-2121">**socket_ptr** Wskaźnik do gniazda, który ma być używany w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="8dd59-2122">**listen_queue_size** Liczba żądań połączenia klienta, które można umieścić w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="8dd59-2123">**listen_callback** Funkcja aplikacji do wywołania po odebraniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="8dd59-2124">Jeśli określono wartość NULL, funkcja wywołania zwrotnego Listen jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2125">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2125">Return Values</span></span>

- <span data-ttu-id="8dd59-2126">**NX_SUCCESS** (0X00) pomyślne włączenie nasłuchiwania portu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="8dd59-2127">**NX_MAX_LISTEN** (0X33) nie ma więcej dostępnych struktur żądań nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="8dd59-2128">Stała NX_MAX_LISTEN_REQUESTS w nx_api. h definiuje liczbę aktywnych żądań nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="8dd59-2129">**NX_NOT_CLOSED** (0x35) dostarczony gniazdo serwera nie jest w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="8dd59-2130">**NX_ALREADY_BOUND** (0x22) dostarczony gniazdo serwera jest już powiązany z portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="8dd59-2131">**NX_DUPLICATE_LISTEN** (0X34) istnieje już aktywne żądanie nasłuchiwania dla tego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="8dd59-2132">**NX_INVALID_PORT** (0x46) określono nieprawidłowy port.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="8dd59-2133">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="8dd59-2134">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2135">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2136">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2136">Allowed From</span></span>

<span data-ttu-id="8dd59-2137">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2138">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2138">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2139">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2140">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2141">See Also</span></span>

- <span data-ttu-id="8dd59-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="8dd59-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="8dd59-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="8dd59-2153">Ponowne nasłuchiwanie połączenia klienta na porcie TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2154">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-2155">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2155">Description</span></span>

<span data-ttu-id="8dd59-2156">Ta usługa jest wywoływana po odebraniu połączenia na porcie, który został wcześniej skonfigurowany do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="8dd59-2157">Głównym celem tej usługi jest udostępnienie nowego gniazda serwera dla następnego połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="8dd59-2158">Jeśli żądanie połączenia jest kolejkowane, połączenie zostanie przetworzone natychmiast w trakcie tego wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="8dd59-2159">*Ta sama procedura wywołania zwrotnego określona przez oryginalne żądanie Listen jest również wywoływana, gdy istnieje połączenie dla tego nowego gniazda serwera.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2160">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2160">Parameters</span></span>

- <span data-ttu-id="8dd59-2161">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2162">**port** Numer portu do ponownego nasłuchiwania (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="8dd59-2163">**socket_ptr** Gniazdo do użycia dla następnego połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2164">Return Values</span></span>
- <span data-ttu-id="8dd59-2165">**NX_SUCCESS** (0X00) pomyślne ponowne nasłuchiwanie portu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="8dd59-2166">**NX_NOT_CLOSED** (0x35) dostarczony gniazdo serwera nie jest w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="8dd59-2167">**NX_ALREADY_BOUND** (0x22) dostarczony gniazdo serwera jest już powiązany z portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="8dd59-2168">**NX_INVALID_RELISTEN** (0X47) istnieje już prawidłowy wskaźnik gniazda dla tego portu lub określony port nie ma aktywnego żądania listen.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="8dd59-2169">**NX_CONNECTION_PENDING** (0X48) taka sama jak NX_SUCCESS, z wyjątkiem tego, że wystąpiło żądanie połączenia w kolejce i zostało przetworzone w trakcie tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="8dd59-2170">**NX_INVALID_PORT** (0x46) określono nieprawidłowy port.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="8dd59-2171">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wywołania zwrotnego adresu IP lub nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="8dd59-2172">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2173">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2174">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2174">Allowed From</span></span>

<span data-ttu-id="8dd59-2175">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2176">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2176">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2177">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2178">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2179">See Also</span></span>

- <span data-ttu-id="8dd59-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="8dd59-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="8dd59-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="8dd59-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="8dd59-2191">Usuń skojarzenie gniazda z portem nasłuchiwania</span><span class="sxs-lookup"><span data-stu-id="8dd59-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2192">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-2193">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2193">Description</span></span>

<span data-ttu-id="8dd59-2194">Ta usługa usuwa skojarzenie między tym gniazdem serwera i określonym portem serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="8dd59-2195">Aplikacja musi wywołać tę usługę po rozwiązaniu lub po niepomyślnym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2196">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2196">Parameters</span></span>

- <span data-ttu-id="8dd59-2197">**socket_ptr** Wskaźnik do wcześniej instalacyjnego wystąpienia gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2198">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2198">Return Values</span></span>

- <span data-ttu-id="8dd59-2199">**NX_SUCCESS** (0X00) pomyślne nieakceptowanie gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="8dd59-2200">Gniazdo serwera **NX_NOT_LISTEN_STATE** (0x36) jest w niewłaściwym stanie i prawdopodobnie nie jest odłączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="8dd59-2201">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2202">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2203">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2204">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2204">Allowed From</span></span>

<span data-ttu-id="8dd59-2205">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2206">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2206">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2207">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2208">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2209">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2209">See Also</span></span>

- <span data-ttu-id="8dd59-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="8dd59-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="8dd59-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="8dd59-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="8dd59-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="8dd59-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="8dd59-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="8dd59-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="8dd59-2220">Wyłącz nasłuchiwanie połączenia klienta na porcie TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2221">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="8dd59-2222">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2222">Description</span></span>

<span data-ttu-id="8dd59-2223">Ta usługa wyłącza nasłuchiwanie żądania połączenia klienta na określonym porcie TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2224">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2224">Parameters</span></span>

- <span data-ttu-id="8dd59-2225">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2226">**port** Liczba portów do wyłączenia nasłuchiwania (od 0 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2227">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2227">Return Values</span></span>

- <span data-ttu-id="8dd59-2228">**NX_SUCCESS** (0x00) — wyłączanie nasłuchiwania protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="8dd59-2229">Nasłuchiwanie **NX_ENTRY_NOT_FOUND** (0x16) nie zostało włączone dla określonego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="8dd59-2230">**NX_INVALID_PORT** (0x46) określono nieprawidłowy port.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="8dd59-2231">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-2232">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2233">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2234">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2234">Allowed From</span></span>

<span data-ttu-id="8dd59-2235">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2236">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2236">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2237">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2238">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2239">See Also</span></span>

- <span data-ttu-id="8dd59-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="8dd59-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="8dd59-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="8dd59-2251">Pobiera liczbę bajtów dostępnych do pobrania</span><span class="sxs-lookup"><span data-stu-id="8dd59-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2252">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="8dd59-2253">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2253">Description</span></span>

<span data-ttu-id="8dd59-2254">Ta usługa uzyskuje liczbę bajtów dostępnych do pobrania w określonym gnieździe TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="8dd59-2255">Należy pamiętać, że gniazdo TCP musi już być połączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2256">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2256">Parameters</span></span>

- <span data-ttu-id="8dd59-2257">**socket_ptr** Wskaźnik do wcześniej utworzonego i połączonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="8dd59-2258">**bytes_available** Wskaźnik do miejsca docelowego dla dostępnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2259">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2259">Return Values</span></span>

- <span data-ttu-id="8dd59-2260">Usługa **NX_SUCCESS** (0x00) została wykonana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="8dd59-2261">Liczba bajtów dostępnych do odczytu jest zwracana do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="8dd59-2262">Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest w stanie połączonym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="8dd59-2263">**NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="8dd59-2264">**NX_NOT_ENABLED** (0X14) TCP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="8dd59-2265">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2266">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2266">Allowed From</span></span>

<span data-ttu-id="8dd59-2267">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2268">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2268">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2269">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2270">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2271">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2271">See Also</span></span>

- <span data-ttu-id="8dd59-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="8dd59-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="8dd59-2283">Utwórz klienta TCP lub gniazdo serwera</span><span class="sxs-lookup"><span data-stu-id="8dd59-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2284">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-2285">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2285">Description</span></span>

<span data-ttu-id="8dd59-2286">Ta usługa tworzy gniazdo klienta TCP lub serwera dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-2287">*Procedury wywołania zwrotnego aplikacji są wywoływane z wątku skojarzonego z tym wystąpieniem adresu IP.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2288">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2288">Parameters</span></span>

- <span data-ttu-id="8dd59-2289">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2290">**socket_ptr** Wskaźnik do nowego bloku sterowania gniazdem TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="8dd59-2291">**Nazwa** Nazwa aplikacji dla tego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="8dd59-2292">**Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="8dd59-2293">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2294">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="8dd59-2295">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="8dd59-2296">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="8dd59-2297">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="8dd59-2298">**fragment**  Określa, czy jest dozwolone fragmentacja adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="8dd59-2299">Jeśli określono NX_FRAGMENT_OKAY (0x0), jest dozwolone fragmentacja adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="8dd59-2300">Jeśli określono NX_DONT_FRAGMENT (0x4000), fragmentacja adresów IP jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="8dd59-2301">**time_to_live** Określa 8-bitową wartość, która definiuje liczbę routerów, które ten pakiet może przekazać przed wyrzucaniem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="8dd59-2302">Wartość domyślna jest określana przez NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="8dd59-2303">**window_size** Określa maksymalną dozwoloną liczbę bajtów w kolejce odbierania dla tego gniazda</span><span class="sxs-lookup"><span data-stu-id="8dd59-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="8dd59-2304">**urgent_data_callback** Funkcja aplikacji, która jest wywoływana za każdym razem, gdy w strumieniu odbioru zostanie wykryte pilne dane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="8dd59-2305">Jeśli ta wartość jest NX_NULL, pilne dane zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="8dd59-2306">**disconnect_callback** Funkcja aplikacji, która jest wywoływana za każdym razem, gdy łącznik zostanie wystawiony przez gniazdo na drugim końcu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="8dd59-2307">Jeśli ta wartość jest NX_NULL, funkcja odłączania wywołania zwrotnego jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2308">Return Values</span></span>
- <span data-ttu-id="8dd59-2309">**NX_SUCCESS** (0X00) pomyślnie utworzono gniazdo klienta TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="8dd59-2310">**NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ usługi, fragment, nieprawidłowy rozmiar okna lub opcja czasu tolive.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="8dd59-2311">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="8dd59-2312">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2313">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2314">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2314">Allowed From</span></span>

<span data-ttu-id="8dd59-2315">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2316">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2316">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2317">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2318">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2319">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2319">See Also</span></span>

- <span data-ttu-id="8dd59-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="8dd59-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="8dd59-2331">Usuń gniazdo TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2332">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-2333">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2333">Description</span></span>

<span data-ttu-id="8dd59-2334">Ta usługa usuwa wcześniej utworzone gniazdo TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="8dd59-2335">Jeśli gniazdo jest nadal powiązane lub połączone, usługa zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2336">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2336">Parameters</span></span>

- <span data-ttu-id="8dd59-2337">**socket_ptr** Poprzednio utworzone gniazdo TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2338">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2338">Return Values</span></span>

- <span data-ttu-id="8dd59-2339">**NX_SUCCESS** (0X00) pomyślne usunięcie gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="8dd59-2340">Gniazdo **NX_NOT_CREATED** (0x27) nie zostało utworzone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="8dd59-2341">Gniazdo **NX_STILL_BOUND** (0x42) jest nadal powiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="8dd59-2342">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2343">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2344">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2345">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2345">Allowed From</span></span>

<span data-ttu-id="8dd59-2346">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2347">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2347">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2348">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2349">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2350">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2350">See Also</span></span>

- <span data-ttu-id="8dd59-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="8dd59-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="8dd59-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="8dd59-2362">Rozłączanie połączeń klienta i gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="8dd59-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2363">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-2364">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2364">Description</span></span>

<span data-ttu-id="8dd59-2365">Ta usługa rozłącza ustanowione połączenie z gniazdem klienta lub serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="8dd59-2366">Po rozłączeniu gniazda serwera powinno następować żądanie nieakceptowane, a gniazdo klienta, które zostało odłączone, pozostaje w stanie gotowym do innego żądania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="8dd59-2367">Jeśli proces rozłączenia nie może zakończyć się natychmiast, usługa zawiesza się zgodnie z podaną opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2368">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2368">Parameters</span></span>

- <span data-ttu-id="8dd59-2369">**socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="8dd59-2370">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, gdy trwa odłączanie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="8dd59-2371">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2372">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-2374">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2375">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2375">Return Values</span></span>

- <span data-ttu-id="8dd59-2376">**NX_SUCCESS** (0X00) pomyślne rozłączenie gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="8dd59-2377">Określone gniazdo **NX_NOT_CONNECTED** (0x38) nie jest połączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="8dd59-2378">**NX_IN_PROGRESS** (0x37) rozłączenie jest w toku, nie określono oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="8dd59-2379">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-2380">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2381">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2382">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2383">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2383">Allowed From</span></span>

<span data-ttu-id="8dd59-2384">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2385">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2385">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2386">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2387">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2388">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2388">See Also</span></span>

- <span data-ttu-id="8dd59-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="8dd59-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="8dd59-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="8dd59-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="8dd59-2399">Zainstaluj funkcję wywołania zwrotnego powiadomienia o rozłączeniu protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2400">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-2401">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2401">Description</span></span>

<span data-ttu-id="8dd59-2402">Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po zakończeniu operacji rozłączenia gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="8dd59-2403">Funkcja wywołania zwrotnego rozłączenia gniazda TCP jest dostępna, jeśli NetX jest skompilowana przy użyciu opcji</span><span class="sxs-lookup"><span data-stu-id="8dd59-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="8dd59-2404">Zdefiniowano ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2405">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2405">Parameters</span></span>

- <span data-ttu-id="8dd59-2406">**socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="8dd59-2407">**tcp_disconnect_complete_notify** Funkcja wywołania zwrotnego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2408">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2408">Return Values</span></span>
- <span data-ttu-id="8dd59-2409">**NX_SUCCESS** (0X00) pomyślnie zarejestrował funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="8dd59-2410">**NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotekę NetX</span><span class="sxs-lookup"><span data-stu-id="8dd59-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="8dd59-2411">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2412">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2413">Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2414">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2414">Allowed From</span></span>

<span data-ttu-id="8dd59-2415">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2416">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2416">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2417">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2418">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2419">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2419">See Also</span></span>

- <span data-ttu-id="8dd59-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="8dd59-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="8dd59-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="8dd59-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="8dd59-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2424">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="8dd59-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="8dd59-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="8dd59-2427">Ustaw funkcję wywołania zwrotnego powiadomienia o ustanowieniu protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2428">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-2429">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2429">Description</span></span>

<span data-ttu-id="8dd59-2430">Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po nawiązaniu połączenia przez gniazdo TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="8dd59-2431">Funkcja wywołania zwrotnego gniazda TCP jest dostępna, jeśli NetX jest skompilowana przy użyciu opcji zdefiniowanej ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2432">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2432">Parameters</span></span>

- <span data-ttu-id="8dd59-2433">**socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="8dd59-2434">**tcp_establish_notify** Wywoływanie funkcji wywołania zwrotnego po nawiązaniu połączenia TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2435">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2435">Return Values</span></span>

- <span data-ttu-id="8dd59-2436">**NX_SUCCESS** (0X00) pomyślnie ustawia funkcję powiadamiania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="8dd59-2437">**NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotekę NetX</span><span class="sxs-lookup"><span data-stu-id="8dd59-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="8dd59-2438">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2439">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2440">**NX_NOT_ENABLED** (0X14) TCP nie został włączony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2441">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2441">Allowed From</span></span>

<span data-ttu-id="8dd59-2442">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2443">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2443">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2444">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2445">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2446">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2446">See Also</span></span>

- <span data-ttu-id="8dd59-2447">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="8dd59-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="8dd59-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="8dd59-2454">Pobierz informacje o działaniach gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2455">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="8dd59-2456">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2456">Description</span></span>

<span data-ttu-id="8dd59-2457">Ta usługa pobiera informacje o działaniach gniazda TCP dla określonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="8dd59-2458">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2459">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2459">Parameters</span></span>

- <span data-ttu-id="8dd59-2460">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-2461">**tcp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby pakietów TCP wysłanych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="8dd59-2462">**tcp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby bajtów TCP wysłanych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="8dd59-2463">**tcp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP odebranych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="8dd59-2464">**tcp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby bajtów TCP odebranych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="8dd59-2465">**tcp_retransmit_packets** Wskaźnik do lokalizacji docelowej łącznej liczby ponownych transmisji pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="8dd59-2466">**tcp_packets_queued** Wskaźnik do lokalizacji docelowej łącznej liczby pakietów TCP umieszczonych w kolejce w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="8dd59-2467">**tcp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP z błędami sumy kontrolnej w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="8dd59-2468">**tcp_socket_state** Wskaźnik do miejsca docelowego bieżącego stanu gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="8dd59-2469">**tcp_transmit_queue_depth** Wskaźnik do miejsca docelowego całkowitej liczby pakietów nadawczych oczekujących w kolejce na potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="8dd59-2470">**tcp_transmit_window** Wskaźnik do miejsca docelowego bieżącego rozmiaru okna wysyłania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="8dd59-2471">**tcp_receive_window** Wskaźnik do miejsca docelowego bieżącego rozmiaru okna odbierania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2472">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2472">Return Values</span></span>

- <span data-ttu-id="8dd59-2473">**NX_SUCCESS** (0X00) pomyślne pobieranie informacji o gnieździe TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="8dd59-2474">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2475">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2476">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2477">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2478">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2478">Allowed From</span></span>

<span data-ttu-id="8dd59-2479">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2480">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2480">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2481">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2482">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2483">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2483">See Also</span></span>

- <span data-ttu-id="8dd59-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="8dd59-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="8dd59-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="8dd59-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="8dd59-2494">Pobierz rozmiar pasma gniazda</span><span class="sxs-lookup"><span data-stu-id="8dd59-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2495">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="8dd59-2496">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2496">Description</span></span>

<span data-ttu-id="8dd59-2497">Ta usługa pobiera lokalny maksymalny rozmiar segmentu określonego gniazda (Maximum).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2498">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2498">Parameters</span></span>

- <span data-ttu-id="8dd59-2499">**socket_ptr** Wskaźnik do wcześniej utworzonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="8dd59-2500"> rozmiar/rozmiar Miejsce docelowe zwracające rozmiar urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2501">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2501">Return Values</span></span>

- <span data-ttu-id="8dd59-2502">**NX_SUCCESS** (0X00) pomyślne pobieranie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="8dd59-2503">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik miejsca docelowego gniazda lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="8dd59-2504">**NX_NOT_ENABLED** (0X14) TCP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="8dd59-2505">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2506">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2506">Allowed From</span></span>

<span data-ttu-id="8dd59-2507">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2508">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2508">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2509">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2510">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2511">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2511">See Also</span></span>

- <span data-ttu-id="8dd59-2512">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2513">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="8dd59-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="8dd59-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2517">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="8dd59-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="8dd59-2520">Pobierz rozmiar pasma równorzędnego gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2521">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="8dd59-2522">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2522">Description</span></span>

<span data-ttu-id="8dd59-2523">Ta usługa pobiera maksymalny rozmiar segmentu (Maximum) anonsowany przez gniazdo równorzędne.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2524">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2524">Parameters</span></span>

- <span data-ttu-id="8dd59-2525">**socket_ptr** Wskaźnik do wcześniej utworzonego i połączonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="8dd59-2526"> rozmiar/rozmiar Miejsce docelowe zwracające rozmiar tego samego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-2527">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2527">Return Values</span></span>

- <span data-ttu-id="8dd59-2528">**NX_SUCCESS** (0X00) pomyślne pobieranie elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="8dd59-2529">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik miejsca docelowego gniazda lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="8dd59-2530">**NX_NOT_ENABLED** (0X14) TCP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="8dd59-2531">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2532">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2532">Allowed From</span></span>

<span data-ttu-id="8dd59-2533">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2534">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2534">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2535">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2536">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2537">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2537">See Also</span></span>

- <span data-ttu-id="8dd59-2538">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2539">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="8dd59-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2543">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="8dd59-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="8dd59-2546">Ustaw rozmiar pasma gniazda</span><span class="sxs-lookup"><span data-stu-id="8dd59-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2547">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="8dd59-2548">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2548">Description</span></span>

<span data-ttu-id="8dd59-2549">Ta usługa ustawia maksymalny rozmiar segmentu określonego gniazda (Maximum).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="8dd59-2550">Należy pamiętać, że wartość parametru/limit musi znajdować się w zakresie jednostki MTU interfejsu sieciowego, co pozwala na pozostawienie miejsca na nagłówki IP i TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="8dd59-2551">Ta usługa powinna zostać użyta, zanim gniazdo TCP rozpocznie proces nawiązywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="8dd59-2552">Jeśli usługa jest używana po nawiązaniu połączenia TCP, Nowa wartość nie ma wpływu na połączenie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2553">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2553">Parameters</span></span>

- <span data-ttu-id="8dd59-2554">**socket_ptr** Wskaźnik do wcześniej utworzonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="8dd59-2555"> rozmiar/rozmiar Wartość parametru o wartości do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2556">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2556">Return Values</span></span>

- <span data-ttu-id="8dd59-2557">**NX_SUCCESS** (0x00) — zestaw o pomyślnym przeprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="8dd59-2558">Wartość parametru **NX_SIZE_ERROR** (0x09) jest zbyt duża.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="8dd59-2559">**NX_NOT_CONNECTED** (0x38) połączenie TCP nie zostało nawiązane</span><span class="sxs-lookup"><span data-stu-id="8dd59-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="8dd59-2560">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2561">**NX_NOT_ENABLED** (0X14) TCP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="8dd59-2562">Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2563">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2563">Allowed From</span></span>

<span data-ttu-id="8dd59-2564">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2565">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2565">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2566">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2567">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2568">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2568">See Also</span></span>

- <span data-ttu-id="8dd59-2569">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2570">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="8dd59-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2574">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="8dd59-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="8dd59-2577">Pobierz informacje o gnieździe równorzędnym TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2578">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="8dd59-2579">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2579">Description</span></span>

<span data-ttu-id="8dd59-2580">Ta usługa pobiera informacje o adresie IP i porcie elementu równorzędnego dla połączonego gniazda TCP przez sieć IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2581">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2581">Parameters</span></span>

- <span data-ttu-id="8dd59-2582">**socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="8dd59-2583">**peer_ip_address** Wskaźnik do lokalizacji docelowej dla adresu IP elementu równorzędnego w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="8dd59-2584">**peer_port** Wskaźnik do lokalizacji docelowej dla numeru portu elementu równorzędnego w kolejności bajtów hosta.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2585">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2585">Return Values</span></span>

- <span data-ttu-id="8dd59-2586">Usługa **NX_SUCCESS** (0x00) została wykonana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="8dd59-2587">Adres IP i numer portu elementu równorzędnego są zwracane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="8dd59-2588">Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest w stanie połączonym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="8dd59-2589">**NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="8dd59-2590">**NX_NOT_ENABLED** (0X14) TCP nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="8dd59-2591">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2592">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2592">Allowed From</span></span>

<span data-ttu-id="8dd59-2593">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2594">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2594">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2595">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2596">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2597">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2597">See Also</span></span>

- <span data-ttu-id="8dd59-2598">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2599">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="8dd59-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2603">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="8dd59-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="8dd59-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="8dd59-2606">Odbieranie danych z gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2607">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-2608">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2608">Description</span></span>

<span data-ttu-id="8dd59-2609">Ta usługa odbiera dane TCP z określonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="8dd59-2610">Jeśli żadne dane nie są umieszczane w określonym gnieździe, obiekt wywołujący zawiesza się na podstawie podanej opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="8dd59-2611">*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2612">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2612">Parameters</span></span>

- <span data-ttu-id="8dd59-2613">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-2614">**packet_ptr** Wskaźnik na wskaźnik pakietu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="8dd59-2615">**WAIT_OPTION** Definiuje, jak działa usługa, jeśli żadne dane nie są obecnie umieszczane w kolejce w tym gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="8dd59-2616">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2617">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-2619">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2620">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2620">Return Values</span></span>
- <span data-ttu-id="8dd59-2621">**NX_SUCCESS** (0x00) odbieranie danych gniazda zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="8dd59-2622">Gniazdo **NX_NOT_BOUND** (0x24) nie jest jeszcze powiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="8dd59-2623">**NX_NO_PACKET** (0X01) nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="8dd59-2624">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-2625">**NX_NOT_CONNECTED** (0x38) gniazdo nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="8dd59-2626">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik lub pakiet zwrotny pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="8dd59-2627">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2628">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2629">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2629">Allowed From</span></span>

<span data-ttu-id="8dd59-2630">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2631">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2631">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2632">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2633">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2633">Example</span></span>

<span data-ttu-id="8dd59-2634">/\* Odbieraj pakiet z wcześniej utworzonego i połączonego gniazda klienta TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="8dd59-2635">Jeśli żaden pakiet nie jest dostępny, poczekaj na 200 Takty czasomierza przed pokazaniem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="8dd59-2636">\*/status = nx_tcp_socket_receive (&client_socket, &packet_ptr, 200);</span><span class="sxs-lookup"><span data-stu-id="8dd59-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="8dd59-2637">/\* Jeśli stan jest NX_SUCCESS, otrzymany pakiet jest wskazywany przez "packet_ptr".</span><span class="sxs-lookup"><span data-stu-id="8dd59-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="8dd59-2638">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2638">See Also</span></span>

- <span data-ttu-id="8dd59-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="8dd59-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="8dd59-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="8dd59-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="8dd59-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="8dd59-2649">Powiadamiaj aplikację o odebranych pakietach</span><span class="sxs-lookup"><span data-stu-id="8dd59-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="8dd59-2650">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-2651">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2651">Description</span></span>

<span data-ttu-id="8dd59-2652">Ta usługa konfiguruje wskaźnik Odbierz funkcję powiadamiania za pomocą funkcji wywołania zwrotnego określonego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="8dd59-2653">Ta funkcja wywołania zwrotnego jest następnie wywoływana za każdym razem, gdy co najmniej jeden pakiet jest odbierany w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="8dd59-2654">Jeśli zostanie dostarczony NX_NULL wskaźnik, funkcja powiadamiania jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2655">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2655">Parameters</span></span>

- <span data-ttu-id="8dd59-2656">**socket_ptr** Wskaźnik na gniazdo TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="8dd59-2657">**tcp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji, który jest wywoływany, gdy co najmniej jeden pakiet jest odbierany w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2658">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2658">Return Values</span></span>

- <span data-ttu-id="8dd59-2659">**NX_SUCCESS** (0x00) powiadomienie o pomyślnym odebraniu gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="8dd59-2660">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2661">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2662">Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2663">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2663">Allowed From</span></span>

<span data-ttu-id="8dd59-2664">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2665">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2665">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2666">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2667">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2668">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2668">See Also</span></span>

- <span data-ttu-id="8dd59-2669">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2670">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="8dd59-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2674">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="8dd59-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="8dd59-2677">Wysyłanie danych za pośrednictwem gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2678">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-2679">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2679">Description</span></span>

<span data-ttu-id="8dd59-2680">Ta usługa wysyła dane TCP za pośrednictwem wcześniej połączonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="8dd59-2681">Jeśli rozmiar okna o ostatnio anonsowanym odbiorniku jest mniejszy niż to żądanie, usługa opcjonalnie zawiesza się na podstawie podanej opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="8dd59-2682">Ta usługa gwarantuje, że do warstwy IP nie są wysyłane żadne dane pakietu o rozmiarze większym niż wartość maksymalna.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="8dd59-2683">*Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy podejmie również próbę zwolnienia pakietu po transmisji.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2684">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2684">Parameters</span></span>

- <span data-ttu-id="8dd59-2685">**socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-2686">**packet_ptr** Wskaźnik pakietu danych TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="8dd59-2687">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądanie jest większe niż rozmiar okna odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="8dd59-2688">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2689">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-2691">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2692">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2692">Return Values</span></span>

- <span data-ttu-id="8dd59-2693">**NX_SUCCESS** (0X00) pomyślne wysłanie gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="8dd59-2694">Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="8dd59-2695">**NX_NO_INTERFACE_ADDRESS** (0X50) nie znaleziono odpowiedniego interfejsu wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="8dd59-2696">Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="8dd59-2697">Żądanie **NX_WINDOW_OVERFLOW** (0x39) jest większe niż anonsowany rozmiar okna odbiornika w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="8dd59-2698">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-2699">Pakiet **NX_INVALID_PACKET** (0x12) nie jest przydzielony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="8dd59-2700">Osiągnięto maksymalną głębokość kolejki przesyłania **NX_TX_QUEUE_DEPTH** (0x49).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="8dd59-2701">Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="8dd59-2702">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2703">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2704">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-2705">Wskaźnik dołączania pakietu **NX_UNDERFLOW** (0x02) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2706">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2706">Allowed From</span></span>

<span data-ttu-id="8dd59-2707">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2708">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2708">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2709">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2710">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2711">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2711">See Also</span></span>

- <span data-ttu-id="8dd59-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="8dd59-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="8dd59-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="8dd59-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="8dd59-2722">Poczekaj, aż gniazdo TCP przeniesie określony stan</span><span class="sxs-lookup"><span data-stu-id="8dd59-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2723">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8dd59-2724">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2724">Description</span></span>

<span data-ttu-id="8dd59-2725">Ta usługa czeka, aż gniazdo przejdzie do żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="8dd59-2726">Jeśli gniazdo nie jest w żądanym stanie, usługa zawiesza się zgodnie z podaną opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2727">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2727">Parameters</span></span>

- <span data-ttu-id="8dd59-2728">**socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="8dd59-2729">**desired_state** Żądany stan protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="8dd59-2730">Prawidłowe Stany gniazda TCP są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2731">NX_TCP_CLOSED (0x01)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="8dd59-2732">NX_TCP_LISTEN_STATE (0x02)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="8dd59-2733">NX_TCP_SYN_SENT (0x03)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="8dd59-2734">NX_TCP_SYN_RECEIVED (0x04)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="8dd59-2735">NX_TCP_ESTABLISHED (0x05)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="8dd59-2736">NX_TCP_CLOSE_WAIT (0x06)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="8dd59-2737">NX_TCP_FIN_WAIT_1 (0x07)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="8dd59-2738">NX_TCP_FIN_WAIT_2 (0x08)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="8dd59-2739">NX_TCP_CLOSING (0x09)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="8dd59-2740">NX_TCP_TIMED_WAIT (0x0A)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="8dd59-2741">NX_TCP_LAST_ACK (0x0B)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="8dd59-2742">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądany stan nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="8dd59-2743">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2744">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-2746">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2747">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2747">Return Values</span></span>
- <span data-ttu-id="8dd59-2748">Zaczekanie na **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="8dd59-2749">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2750">**NX_NOT_SUCCESSFUL** (0x43) nie występuje w określonym czasie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="8dd59-2751">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-2752">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2753">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-2754">**NX_OPTION_ERROR** (0x0A) żądany stan gniazda jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2755">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2755">Allowed From</span></span>

<span data-ttu-id="8dd59-2756">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2757">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2757">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2758">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2759">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2760">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2760">See Also</span></span>

- <span data-ttu-id="8dd59-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="8dd59-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="8dd59-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="8dd59-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="8dd59-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="8dd59-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="8dd59-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="8dd59-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="8dd59-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="8dd59-2771">Instalacja wywołania zwrotnego dla stanu oczekiwania, który upłynął</span><span class="sxs-lookup"><span data-stu-id="8dd59-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2772">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-2773">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2773">Description</span></span>

<span data-ttu-id="8dd59-2774">Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana, gdy gniazdo TCP jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="8dd59-2775">Aby można było korzystać z tej usługi, biblioteka NetX musi być skompilowana przy użyciu opcji zdefiniowanej ***NX_ENABLE_EXTENDED_NOTIFY*** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2776">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2776">Parameters</span></span>

- <span data-ttu-id="8dd59-2777">**socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="8dd59-2778">**tcp_timed_wait_callback** Funkcja wywołania zwrotnego czasu oczekiwania</span><span class="sxs-lookup"><span data-stu-id="8dd59-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2779">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2779">Return Values</span></span>

- <span data-ttu-id="8dd59-2780">**NX_SUCCESS** (0X00) pomyślnie rejestruje gniazdo funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="8dd59-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="8dd59-2781">**NX_NOT_SUPPORTED** (0X4B) NetX Library została skompilowana bez włączonej funkcji rozszerzonego powiadamiania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="8dd59-2782">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2783">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2784">Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2785">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2785">Allowed From</span></span>

<span data-ttu-id="8dd59-2786">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2787">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2787">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2788">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2789">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2790">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2790">See Also</span></span>

- <span data-ttu-id="8dd59-2791">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2792">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="8dd59-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-2796">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="8dd59-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="8dd59-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="8dd59-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="8dd59-2799">Konfiguruj parametry transmisji gniazda</span><span class="sxs-lookup"><span data-stu-id="8dd59-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2800">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="8dd59-2801">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2801">Description</span></span>

<span data-ttu-id="8dd59-2802">Ta usługa konfiguruje różne parametry transmisji określonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2803">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2803">Parameters</span></span>

- <span data-ttu-id="8dd59-2804">**socket_ptr** Wskaźnik na gniazdo TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="8dd59-2805">**max_queue_depth** Maksymalna liczba pakietów, które mogą być umieszczone w kolejce na potrzeby transmisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="8dd59-2806">**limit czasu** Liczba czasomierzy ThreadXa jest oczekiwana przez potwierdzenie przed ponownym wysłaniem pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="8dd59-2807">**max_retries** Maksymalna dozwolona liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="8dd59-2808">**timeout_shift** Wartość służąca do zmiany limitu czasu dla każdej kolejnej próby.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="8dd59-2809">Wartość 0 powoduje ten sam limit czasu między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="8dd59-2810">Wartość 1 powoduje podwojony limit czasu między ponownymi próbami.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2811">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2811">Return Values</span></span>
- <span data-ttu-id="8dd59-2812">**NX_SUCCESS** (0x00) pomyślna Konfiguracja gniazda transmisji.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="8dd59-2813">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-2814">**NX_OPTION_ERROR** (0X0a) Nieprawidłowa opcja głębokości kolejki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="8dd59-2815">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2816">Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2817">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2817">Allowed From</span></span>

<span data-ttu-id="8dd59-2818">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2819">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2819">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2820">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2821">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2822">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2822">See Also</span></span>

- <span data-ttu-id="8dd59-2823">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2824">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="8dd59-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-2828">nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="8dd59-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="8dd59-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="8dd59-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="8dd59-2831">Powiadamianie o aktualizacjach rozmiaru okna</span><span class="sxs-lookup"><span data-stu-id="8dd59-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2832">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-2833">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2833">Description</span></span>

<span data-ttu-id="8dd59-2834">Ta usługa instaluje procedurę wywołania zwrotnego aktualizacji okna gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="8dd59-2835">Ta procedura jest wywoływana automatycznie za każdym razem, gdy określone gniazdo odbierze pakiet wskazujący wzrost rozmiaru okna hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2836">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2836">Parameters</span></span>

- <span data-ttu-id="8dd59-2837">**socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="8dd59-2838">**tcp_window_update_notify** Procedura wywołania zwrotnego, która ma zostać wywołana, gdy zmienia się rozmiar okna.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="8dd59-2839">Wartość NULL powoduje wyłączenie zmiany okna.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2840">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2840">Return Values</span></span>
- <span data-ttu-id="8dd59-2841">Procedura wywołania zwrotnego **NX_SUCCESS** (0x00) jest instalowana w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="8dd59-2842">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2843">**NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="8dd59-2844">Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="8dd59-2845">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2845">Allowed From</span></span>

<span data-ttu-id="8dd59-2846">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2847">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2847">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2848">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2849">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2850">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2850">See Also</span></span>

- <span data-ttu-id="8dd59-2851">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="8dd59-2852">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="8dd59-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="8dd59-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="8dd59-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="8dd59-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="8dd59-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-2857">nx_udp_enable</span></span>

<span data-ttu-id="8dd59-2858">Włącz składnik UDP elementu NetX</span><span class="sxs-lookup"><span data-stu-id="8dd59-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2859">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-2860">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2860">Description</span></span>

<span data-ttu-id="8dd59-2861">Ta usługa włącza składnik UDP (User Datagram Protocol) NetX.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="8dd59-2862">Po włączeniu protokołu UDP datagramy mogą być wysyłane i odbierane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2863">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2863">Parameters</span></span>

- <span data-ttu-id="8dd59-2864">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2865">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2865">Return Values</span></span>

- <span data-ttu-id="8dd59-2866">**NX_SUCCESS** (0X00) pomyślne włączenie protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="8dd59-2867">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-2868">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2869">**NX_ALREADY_ENABLED** (0X15) ten składnik został już włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2870">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2870">Allowed From</span></span>

<span data-ttu-id="8dd59-2871">Inicjalizacja, wątki, czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2872">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2872">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2873">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2874">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2875">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2875">See Also</span></span>

- <span data-ttu-id="8dd59-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="8dd59-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="8dd59-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="8dd59-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="8dd59-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="8dd59-2885">Znajdź następny dostępny port UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2886">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-2887">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2887">Description</span></span>

<span data-ttu-id="8dd59-2888">Ta usługa szuka bezpłatnego portu UDP (niepowiązanego) rozpoczynającego się od dostarczonej przez aplikację numeru portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="8dd59-2889">Logika wyszukiwania zostanie zawinięty, jeśli wyszukiwanie osiągnie maksymalną wartość dla wartości 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="8dd59-2890">Jeśli wyszukiwanie zakończyło się pomyślnie, port wolny jest zwracany w zmiennej wskazywanej przez *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="8dd59-2891">*Ta usługa może być wywoływana z innego wątku i może mieć ten sam port. Aby uniknąć tego warunku wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda w ramach ochrony obiektu mutex.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2892">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2892">Parameters</span></span>

- <span data-ttu-id="8dd59-2893">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2894">**port** Numer portu do rozpoczęcia wyszukiwania (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="8dd59-2895">**free_port_ptr** Wskaźnik na zmienną zwrotną wolnego portu docelowego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="8dd59-2896">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2896">Return Values</span></span>

- <span data-ttu-id="8dd59-2897">**NX_SUCCESS** (0X00) pomyślne znalezienie bezpłatnego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="8dd59-2898">**NX_NO_FREE_PORTS** (0X45) nie znaleziono wolnych portów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="8dd59-2899">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-2900">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2901">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="8dd59-2902">**NX_INVALID_PORT** (0X46) określony numer portu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2903">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2903">Allowed From</span></span>

<span data-ttu-id="8dd59-2904">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2905">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2905">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2906">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2907">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2908">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2908">See Also</span></span>

- <span data-ttu-id="8dd59-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="8dd59-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="8dd59-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="8dd59-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2917">nx_udp_info_get</span></span>

<span data-ttu-id="8dd59-2918">Pobierz informacje o działaniach UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2919">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="8dd59-2920">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2920">Description</span></span>

<span data-ttu-id="8dd59-2921">Ta usługa pobiera informacje o działaniach UDP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="8dd59-2922">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2923">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2923">Parameters</span></span>

- <span data-ttu-id="8dd59-2924">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-2925">**udp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="8dd59-2926">**udp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych bajtów UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="8dd59-2927">**udp_packets_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych pakietów UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="8dd59-2928">**udp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych bajtów UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="8dd59-2929">**udp_invalid_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych pakietów UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="8dd59-2930">**udp_receive_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="8dd59-2931">**udp_checksum_errors** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów UDP z błędami sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2932">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2932">Return Values</span></span>

- <span data-ttu-id="8dd59-2933">**NX_SUCCESS** (0X00) pomyślne pobieranie informacji o UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="8dd59-2934">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="8dd59-2935">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-2936">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="8dd59-2937">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2937">Allowed From</span></span>

<span data-ttu-id="8dd59-2938">Inicjalizacja, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2939">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2939">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2940">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2941">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2942">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2942">See Also</span></span>

- <span data-ttu-id="8dd59-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="8dd59-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="8dd59-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="8dd59-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="8dd59-2952">Wyodrębnij parametry sieci z pakietu UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2953">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="8dd59-2954">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2954">Description</span></span>

<span data-ttu-id="8dd59-2955">Ta usługa wyodrębnia parametry sieci, takie jak adres IP, numer portu równorzędnego, typ protokołu (usługa zawsze zwraca typ UDP) z pakietu otrzymanego w interfejsie przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2956">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2956">Parameters</span></span>

- <span data-ttu-id="8dd59-2957">**packet_ptr** Wskaźnik do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="8dd59-2958">**IP_address** Wskaźnik na adres IP nadawcy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="8dd59-2959">**Protokół** Wskaźnik do protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="8dd59-2960">**port** Wskaźnik na numer portu nadawcy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="8dd59-2961">**interface_index** Wskaźnik do odbioru indeksu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2962">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2962">Return Values</span></span>

- <span data-ttu-id="8dd59-2963">Pomyślnie wyodrębniono dane interfejsu pakietu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="8dd59-2964">Pakiet **NX_INVALID_PACKET** (0x12) nie zawiera ramki adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="8dd59-2965">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8dd59-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8dd59-2966">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-2967">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-2967">Allowed From</span></span>

<span data-ttu-id="8dd59-2968">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-2969">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2969">Preemption Possible</span></span>

<span data-ttu-id="8dd59-2970">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-2971">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-2972">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-2972">See Also</span></span>

- <span data-ttu-id="8dd59-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="8dd59-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="8dd59-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="8dd59-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="8dd59-2982">Powiąż gniazdo UDP z portem UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-2983">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-2984">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-2984">Description</span></span>

<span data-ttu-id="8dd59-2985">Ta usługa wiąże wcześniej utworzone gniazdo UDP z określonym portem UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="8dd59-2986">Prawidłowy zakres UDP wynosi od 0 do 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="8dd59-2987">Jeśli żądany numer portu jest powiązany z innym gniazdem, ta usługa czeka przez określony czas, w którym gniazdo ma usunąć powiązanie z numerem portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-2988">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-2988">Parameters</span></span>

- <span data-ttu-id="8dd59-2989">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="8dd59-2990">**port** Numer portu, z którym ma zostać utworzone powiązanie (od 1 do 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="8dd59-2991">Jeśli numer portu to NX_ANY_PORT (0x0000), wystąpienie protokołu IP wyszuka następny bezpłatny port i użyje go do powiązania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="8dd59-2992">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli port jest już powiązany z innym gniazdem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="8dd59-2993">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-2994">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-2996">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-2997">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-2997">Return Values</span></span>

- <span data-ttu-id="8dd59-2998">**NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="8dd59-2999">**NX_ALREADY_BOUND** (0X22) to gniazdo jest już powiązane z innym portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="8dd59-3000">Port **NX_PORT_UNAVAILABLE** (0x23) jest już powiązany z innym gniazdem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="8dd59-3001">**NX_NO_FREE_PORTS** (0X45) brak wolnego portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="8dd59-3002">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="8dd59-3003">**NX_INVALID_PORT** (0x46) określono nieprawidłowy port.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="8dd59-3004">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-3005">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3006">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3007">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3007">Allowed From</span></span>

<span data-ttu-id="8dd59-3008">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3009">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3009">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3010">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3011">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3012">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3012">See Also</span></span>

- <span data-ttu-id="8dd59-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="8dd59-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="8dd59-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="8dd59-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="8dd59-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="8dd59-3022">Pobiera liczbę bajtów dostępnych do pobrania</span><span class="sxs-lookup"><span data-stu-id="8dd59-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3023">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="8dd59-3024">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3024">Description</span></span>

<span data-ttu-id="8dd59-3025">Ta usługa Pobiera liczbę bajtów dostępnych do odbioru w określonym gnieździe UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3026">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3026">Parameters</span></span>

- <span data-ttu-id="8dd59-3027">**socket_ptr** Wskaźnik do wcześniej utworzonego gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="8dd59-3028">**bytes_available** Wskaźnik do miejsca docelowego dla dostępnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3029">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3029">Return Values</span></span>

- <span data-ttu-id="8dd59-3030">Pomyślne pobieranie odebranych bajtów **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="8dd59-3031">Gniazdo **NX_NOT_SUCCESSFUL** (0x43) nie jest powiązane z portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="8dd59-3032">**NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="8dd59-3033">Funkcja UDP **NX_NOT_ENABLED** (0x14) nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="8dd59-3034">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3035">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3035">Allowed From</span></span>

<span data-ttu-id="8dd59-3036">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3037">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3037">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3038">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3039">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3040">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3040">See Also</span></span>

- <span data-ttu-id="8dd59-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="8dd59-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="8dd59-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="8dd59-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="8dd59-3050">Wyłącz sumę kontrolną dla gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3051">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-3052">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3052">Description</span></span>

<span data-ttu-id="8dd59-3053">Ta usługa wyłącza logikę sumy kontrolnej na potrzeby wysyłania i otrzymywania pakietów w określonym gnieździe UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="8dd59-3054">Gdy logika sum kontrolnych jest wyłączona, wartość zero jest ładowana do pola sumy kontrolnej nagłówka UDP dla wszystkich pakietów wysyłanych za pomocą tego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="8dd59-3055">Wartość sumy kontrolnej zero wartości w nagłówku UDP sygnalizuje odbiornikowi, że suma kontrolna nie jest obliczana dla tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="8dd59-3056">Należy również zauważyć, że nie ma to żadnego efektu, jeśli ***NX_DISABLE_UDP_RX_CHECKSUM** _ i _ *_NX_DISABLE_UDP_TX_CHECKSUM_** są zdefiniowane podczas otrzymywania i wysyłania pakietów UDP odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3057">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3057">Parameters</span></span>

- <span data-ttu-id="8dd59-3058">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3059">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3059">Return Values</span></span>

- <span data-ttu-id="8dd59-3060">**NX_SUCCESS** (0x00) — Wyłącz sumę kontrolną gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="8dd59-3061">Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="8dd59-3062">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-3063">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3064">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3065">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3065">Allowed From</span></span>

<span data-ttu-id="8dd59-3066">Inicjalizacja, wątki, czasomierz</span><span class="sxs-lookup"><span data-stu-id="8dd59-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3067">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3067">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3068">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3069">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3070">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3070">See Also</span></span>

- <span data-ttu-id="8dd59-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="8dd59-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="8dd59-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="8dd59-3080">Włącz sumę kontrolną dla gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3081">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-3082">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3082">Description</span></span>

<span data-ttu-id="8dd59-3083">Ta usługa umożliwia logikę sumy kontrolnej na potrzeby wysyłania i otrzymywania pakietów w określonym gnieździe UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="8dd59-3084">Suma kontrolna obejmuje cały obszar danych UDP oraz nagłówek pseudo IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="8dd59-3085">Należy również pamiętać, że nie ma to wpływu, jeśli **NX_DISABLE_UDP_RX_CHECKSUM** i **NX_DISABLE_UDP_TX_CHECKSUM** są zdefiniowane podczas otrzymywania i wysyłania pakietów UDP odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3086">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3086">Parameters</span></span>

- <span data-ttu-id="8dd59-3087">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3088">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3088">Return Values</span></span>

- <span data-ttu-id="8dd59-3089">**NX_SUCCESS** (0x00) włączono pomyślne włączenie sumy kontrolnej gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="8dd59-3090">Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="8dd59-3091">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-3092">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3093">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3094">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3094">Allowed From</span></span>

<span data-ttu-id="8dd59-3095">Inicjalizacja, wątki, czasomierz</span><span class="sxs-lookup"><span data-stu-id="8dd59-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3096">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3096">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3097">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3098">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3099">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3099">See Also</span></span>

- <span data-ttu-id="8dd59-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="8dd59-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="8dd59-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="8dd59-3109">Utwórz gniazdo UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3110">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="8dd59-3111">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3111">Description</span></span>

<span data-ttu-id="8dd59-3112">Ta usługa tworzy gniazdo UDP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3113">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3113">Parameters</span></span>

- <span data-ttu-id="8dd59-3114">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8dd59-3115">**socket_ptr** Wskaźnik do nowej kontrolki gniazda UDP blo.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="8dd59-3116">**Nazwa** Nazwa aplikacji dla tego gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="8dd59-3117">**Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:</span><span class="sxs-lookup"><span data-stu-id="8dd59-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="8dd59-3118">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="8dd59-3119">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="8dd59-3120">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="8dd59-3121">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="8dd59-3122">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="8dd59-3123">**fragment** Określa, czy jest dozwolone fragmentacja adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="8dd59-3124">Jeśli określono NX_FRAGMENT_OKAY (0x0), jest dozwolone fragmentacja adresów IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="8dd59-3125">Jeśli określono NX_DONT_FRAGMENT (0x4000), fragmentacja adresów IP jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="8dd59-3126">**time_to_live** Określa 8-bitową wartość, która definiuje liczbę routerów, które ten pakiet może przekazać przed wyrzucaniem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="8dd59-3127">Wartość domyślna jest określana przez NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="8dd59-3128">**queue_maximum** Określa maksymalną liczbę datagramów UDP, która może być umieszczona w kolejce dla tego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="8dd59-3129">Po osiągnięciu limitu kolejki dla każdego nowego pakietu odebrano najstarszy pakiet UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3130">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3130">Return Values</span></span>

- <span data-ttu-id="8dd59-3131">**NX_SUCCESS** (0X00) pomyślnie utworzono gniazdo UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="8dd59-3132">**NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ usługi, fragmentu lub opcji Time-to-Live.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="8dd59-3133">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="8dd59-3134">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3135">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3136">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3136">Allowed From</span></span>

<span data-ttu-id="8dd59-3137">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3138">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3138">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3139">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3140">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3141">See Also</span></span>

- <span data-ttu-id="8dd59-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="8dd59-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="8dd59-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="8dd59-3149">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="8dd59-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="8dd59-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="8dd59-3151">Usuń gniazdo UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3152">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-3153">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3153">Description</span></span>

<span data-ttu-id="8dd59-3154">Ta usługa usuwa wcześniej utworzone gniazdo UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="8dd59-3155">Jeśli gniazdo zostało powiązane z portem, gniazdo musi być najpierw niepowiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3156">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3156">Parameters</span></span>

- <span data-ttu-id="8dd59-3157">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3158">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3158">Return Values</span></span>

- <span data-ttu-id="8dd59-3159">**NX_SUCCESS** (0X00) pomyślne usunięcie gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="8dd59-3160">Gniazdo **NX_STILL_BOUND** (0x42) jest nadal powiązane.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="8dd59-3161">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-3162">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3163">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3164">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3164">Allowed From</span></span>

<span data-ttu-id="8dd59-3165">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3166">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3166">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3167">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3168">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3169">See Also</span></span>

- <span data-ttu-id="8dd59-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="8dd59-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="8dd59-3177">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="8dd59-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="8dd59-3179">Pobierz informacje o działaniach gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3180">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="8dd59-3181">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3181">Description</span></span>

<span data-ttu-id="8dd59-3182">Ta usługa pobiera informacje o działaniach gniazda UDP dla określonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="8dd59-3183">*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3184">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3184">Parameters</span></span>

- <span data-ttu-id="8dd59-3185">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="8dd59-3186">**udp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby pakietów UDP wysłanych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="8dd59-3187">**udp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby bajtów UDP wysłanych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="8dd59-3188">**udp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP odebranych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="8dd59-3189">**udp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby bajtów UDP odebranych w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="8dd59-3190">**udp_packets_queued** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów UDP umieszczonych w kolejce w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="8dd59-3191">**udp_receive_packets_dropped** Wskaźnik do lokalizacji docelowej łącznej liczby pakietów odbioru protokołu UDP porzuconych dla gniazda z powodu przekroczenia rozmiaru kolejki.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="8dd59-3192">**udp_checksum_errors** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów UDP z błędami sumy kontrolnej w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3193">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3193">Return Values</span></span>

- <span data-ttu-id="8dd59-3194">**NX_SUCCESS** (0X00) pomyślne pobranie informacji o gnieździe UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="8dd59-3195">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-3196">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3197">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3198">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3198">Allowed From</span></span>

<span data-ttu-id="8dd59-3199">Inicjalizacja, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8dd59-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3200">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3200">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3201">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3202">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3203">See Also</span></span>

- <span data-ttu-id="8dd59-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="8dd59-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="8dd59-3211">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="8dd59-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="8dd59-3213">Wybierz numer portu powiązany z gniazdem UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3214">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-3215">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3215">Description</span></span>

<span data-ttu-id="8dd59-3216">Ta usługa Pobiera numer portu skojarzony z gniazdem, który jest przydatny do znajdowania portu przydzielonego przez NetX w sytuacjach, w których NX_ANY_PORT został określony w momencie powiązania gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3217">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3217">Parameters</span></span>

- <span data-ttu-id="8dd59-3218">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="8dd59-3219">**port_ptr** Wskaźnik do miejsca docelowego dla numeru portu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="8dd59-3220">Prawidłowe numery portów to (1-0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="8dd59-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3221">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3221">Return Values</span></span>

- <span data-ttu-id="8dd59-3222">**NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="8dd59-3223">**NX_NOT_BOUND** (0X24) to gniazdo nie jest powiązane z portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="8dd59-3224">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda lub zwracany przez port wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="8dd59-3225">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3226">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3227">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3227">Allowed From</span></span>

<span data-ttu-id="8dd59-3228">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3229">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3229">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3230">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3231">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3232">See Also</span></span>

- <span data-ttu-id="8dd59-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="8dd59-3240">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="8dd59-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="8dd59-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="8dd59-3242">Odbieranie datagramu z gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3243">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8dd59-3244">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3244">Description</span></span>

<span data-ttu-id="8dd59-3245">Ta usługa odbiera datagram UDP od określonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="8dd59-3246">Jeśli żaden datagram nie jest umieszczony w określonym gnieździe, obiekt wywołujący zawiesza się na podstawie podanej opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="8dd59-3247">*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*</span><span class="sxs-lookup"><span data-stu-id="8dd59-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3248">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3248">Parameters</span></span>

- <span data-ttu-id="8dd59-3249">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="8dd59-3250">**packet_ptr** Wskaźnik na wskaźnik pakietu datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="8dd59-3251">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli datagram nie jest obecnie umieszczony w tym gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="8dd59-3252">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8dd59-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="8dd59-3253">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="8dd59-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="8dd59-3255">wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3256">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3256">Allowed From</span></span>

<span data-ttu-id="8dd59-3257">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3258">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3258">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3259">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3260">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3261">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3261">See Also</span></span>

- <span data-ttu-id="8dd59-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="8dd59-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="8dd59-3269">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="8dd59-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="8dd59-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="8dd59-3271">Powiadamiaj aplikację o każdym odebranym pakiecie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3272">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="8dd59-3273">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3273">Description</span></span>

<span data-ttu-id="8dd59-3274">Ta usługa ustawia wskaźnik funkcji Odbierz powiadomienie na funkcję wywołania zwrotnego określonego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="8dd59-3275">Ta funkcja wywołania zwrotnego jest wywoływana za każdym razem, gdy pakiet jest odbierany w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="8dd59-3276">Jeśli zostanie dostarczony NX_NULL wskaźnik, funkcja Odbierz powiadomienie jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3277">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3277">Parameters</span></span>

- <span data-ttu-id="8dd59-3278">**socket_ptr** Wskaźnik na gniazdo UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="8dd59-3279">**udp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji, który jest wywoływany, gdy pakiet jest odbierany w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3280">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3280">Allowed From</span></span>

<span data-ttu-id="8dd59-3281">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3282">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3282">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3283">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3284">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3285">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3285">See Also</span></span>

- <span data-ttu-id="8dd59-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="8dd59-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="8dd59-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="8dd59-3295">Wysyłanie datagramu UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3296">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="8dd59-3297">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3297">Description</span></span>

<span data-ttu-id="8dd59-3298">Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="8dd59-3299">NetX znajduje odpowiedni lokalny adres IP jako adres źródłowy na podstawie docelowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="8dd59-3300">Aby określić konkretny interfejs i źródłowy adres IP, aplikacja powinna używać usługi **nx_udp_socket_interface_send** .</span><span class="sxs-lookup"><span data-stu-id="8dd59-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="8dd59-3301">Należy zauważyć, że ta usługa wraca natychmiast niezależnie od tego, czy datagram UDP został pomyślnie wysłany.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="8dd59-3302">Gniazdo musi być powiązane z portem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3303">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3303">Parameters</span></span>

- <span data-ttu-id="8dd59-3304">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="8dd59-3305">**packet_ptr** Wskaźnik pakietu datagramu UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="8dd59-3306">**IP_address** Docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="8dd59-3307">**port** Prawidłowy numer portu docelowego z zakresu od 1 do 0xFFFF) w kolejności bajtów hosta</span><span class="sxs-lookup"><span data-stu-id="8dd59-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3308">Return Values</span></span>

- <span data-ttu-id="8dd59-3309">**NX_SUCCESS** (0X00) pomyślne wysłanie gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="8dd59-3310">Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane z żadnym portem</span><span class="sxs-lookup"><span data-stu-id="8dd59-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="8dd59-3311">**NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="8dd59-3312">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="8dd59-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="8dd59-3313">**NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca na nagłówek UDP w pakiecie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="8dd59-3314">Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="8dd59-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="8dd59-3315">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda</span><span class="sxs-lookup"><span data-stu-id="8dd59-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="8dd59-3316">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="8dd59-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8dd59-3317">Nie włączono protokołu UDP **NX_NOT_ENABLED** (0x14)</span><span class="sxs-lookup"><span data-stu-id="8dd59-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="8dd59-3318">Numer portu **NX_INVALID_PORT** (0x46) nie należy do prawidłowego zakresu</span><span class="sxs-lookup"><span data-stu-id="8dd59-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3319">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3319">Allowed From</span></span>

<span data-ttu-id="8dd59-3320">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3321">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3321">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3322">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3323">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3324">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3324">See Also</span></span>

- <span data-ttu-id="8dd59-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="8dd59-3332">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="8dd59-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="8dd59-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="8dd59-3334">Wyślij datagram za poorednictwem gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3335">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="8dd59-3336">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3336">Description</span></span>

<span data-ttu-id="8dd59-3337">Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP za pomocą interfejsu sieciowego z określonym adresem IP jako adresem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="8dd59-3338">Należy pamiętać, że usługa wraca natychmiast, niezależnie od tego, czy datagram UDP został pomyślnie wysłany.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3339">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3339">Parameters</span></span>

- <span data-ttu-id="8dd59-3340">**socket_ptr** Gniazdo umożliwiające przesłanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="8dd59-3341">**packet_ptr** Wskaźnik do pakietu do przesłania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="8dd59-3342">**IP_address** Docelowy adres IP do wysłania pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="8dd59-3343">**port** Port docelowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3343">**port** Destination port.</span></span>
- <span data-ttu-id="8dd59-3344">**address_index** Indeks adresu skojarzonego z interfejsem, na którym ma zostać wysłany pakiet.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3345">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3345">Return Values</span></span>

- <span data-ttu-id="8dd59-3346">Pomyślnie wysłano pakiet **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8dd59-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="8dd59-3347">Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane z portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="8dd59-3348">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="8dd59-3349">Nie włączono przetwarzania UDP **NX_NOT_ENABLED** (0x14).</span><span class="sxs-lookup"><span data-stu-id="8dd59-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="8dd59-3350">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="8dd59-3351">**NX_OVERFLOW** (0X03) Nieprawidłowy wskaźnik dołączania pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="8dd59-3352">**NX_UNDERFLOW** (0X02) Nieprawidłowy wskaźnik dołączania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="8dd59-3353">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3354">**NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks adresu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="8dd59-3355">**NX_INVALID_PORT** (0x46) numer portu przekracza maksymalny numer portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3356">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3356">Allowed From</span></span>

<span data-ttu-id="8dd59-3357">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3358">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3358">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3359">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3360">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3361">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3361">See Also</span></span>

- <span data-ttu-id="8dd59-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="8dd59-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="8dd59-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="8dd59-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="8dd59-3371">Usuń powiązanie gniazda UDP z portu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3372">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="8dd59-3373">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3373">Description</span></span>

<span data-ttu-id="8dd59-3374">Ta usługa zwalnia powiązanie między gniazdem UDP i portem UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="8dd59-3375">Wszystkie odebrane pakiety przechowywane w kolejce odbierania zostaną wydane jako część operacji usuwania powiązania.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="8dd59-3376">Jeśli istnieją inne wątki oczekujące na powiązanie innego gniazda z niezwiązanym portem, pierwszy zawieszony wątek zostaje następnie powiązany z nowym niezwiązanym portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3377">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3377">Parameters</span></span>

- <span data-ttu-id="8dd59-3378">**socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3379">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3379">Return Values</span></span>

- <span data-ttu-id="8dd59-3380">**NX_SUCCESS** (0x00) odpinanie gniazda zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="8dd59-3381">Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="8dd59-3382">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="8dd59-3383">**NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="8dd59-3384">**NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3385">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3385">Allowed From</span></span>

<span data-ttu-id="8dd59-3386">Wątki</span><span class="sxs-lookup"><span data-stu-id="8dd59-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3387">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3387">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3388">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd59-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3389">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3390">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3390">See Also</span></span>

- <span data-ttu-id="8dd59-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="8dd59-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="8dd59-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="8dd59-3400">Wyodrębnij adres IP i Wyślij port z datadatagramu UDP</span><span class="sxs-lookup"><span data-stu-id="8dd59-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="8dd59-3401">Prototype</span><span class="sxs-lookup"><span data-stu-id="8dd59-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="8dd59-3402">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd59-3402">Description</span></span>

<span data-ttu-id="8dd59-3403">Ta usługa wyodrębnia adres IP i numer portu nadawcy z nagłówków IP i UDP dostarczonego datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="8dd59-3404">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd59-3404">Parameters</span></span>

- <span data-ttu-id="8dd59-3405">**packet_ptr** Wskaźnik pakietu datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="8dd59-3406">**IP_address** Prawidłowy wskaźnik do zmiennej zwracanego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="8dd59-3407">**port** Prawidłowy wskaźnik do zmiennej portu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="8dd59-3408">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8dd59-3408">Return Values</span></span>

- <span data-ttu-id="8dd59-3409">**NX_SUCCESS** (0X00) pomyślne oddzielenie adresu IP/portu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="8dd59-3410">**NX_INVALID_PACKET** (0x12) podany pakiet jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="8dd59-3411">**NX_PTR_ERROR** (0X07) nieprawidłowy pakiet lub adres IP lub port docelowy.</span><span class="sxs-lookup"><span data-stu-id="8dd59-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8dd59-3412">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8dd59-3412">Allowed From</span></span>

<span data-ttu-id="8dd59-3413">Inicjalizacja, wątki, czasomierze, ISR</span><span class="sxs-lookup"><span data-stu-id="8dd59-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8dd59-3414">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3414">Preemption Possible</span></span>

<span data-ttu-id="8dd59-3415">Nie</span><span class="sxs-lookup"><span data-stu-id="8dd59-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="8dd59-3416">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dd59-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="8dd59-3417">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dd59-3417">See Also</span></span>

- <span data-ttu-id="8dd59-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="8dd59-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="8dd59-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="8dd59-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="8dd59-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="8dd59-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="8dd59-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="8dd59-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="8dd59-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="8dd59-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="8dd59-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>