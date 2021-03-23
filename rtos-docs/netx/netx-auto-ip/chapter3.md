---
title: Rozdział 3 — Opis usług Azure RTO NetX AutoIP Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX AutoIP Services (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822752"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a><span data-ttu-id="2fd39-103">Rozdział 3 — Opis usług Azure RTO NetX AutoIP Services</span><span class="sxs-lookup"><span data-stu-id="2fd39-103">Chapter 3 - Description of Azure RTOS NetX AutoIP services</span></span>

<span data-ttu-id="2fd39-104">Ten rozdział zawiera opis wszystkich usług Azure RTO NetX AutoIP Services (wymienionych poniżej) w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="2fd39-104">This chapter contains a description of all Azure RTOS NetX AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2fd39-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="2fd39-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2fd39-106">**nx_auto_ip_create**: *Tworzenie wystąpienia AutoIP*</span><span class="sxs-lookup"><span data-stu-id="2fd39-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="2fd39-107">**nx_auto_ip_delete**: *usuwanie wystąpienia AutoIP*</span><span class="sxs-lookup"><span data-stu-id="2fd39-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="2fd39-108">**nx_auto_ip_get_address**: *Pobierz bieżący adres AutoIP*</span><span class="sxs-lookup"><span data-stu-id="2fd39-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="2fd39-109">**nx_auto_ip_set_interface**: *Ustaw interfejs IP wymagający adresu AutoIP*</span><span class="sxs-lookup"><span data-stu-id="2fd39-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="2fd39-110">**nx_auto_ip_start**: *Uruchamianie przetwarzania AutoIP*</span><span class="sxs-lookup"><span data-stu-id="2fd39-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="2fd39-111">**nx_auto_ip_stop**: *Zatrzymywanie przetwarzania AutoIP*</span><span class="sxs-lookup"><span data-stu-id="2fd39-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="2fd39-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="2fd39-112">nx_auto_ip_create</span></span>

<span data-ttu-id="2fd39-113">Utwórz wystąpienie AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2fd39-114">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fd39-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a><span data-ttu-id="2fd39-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd39-115">Description</span></span>

<span data-ttu-id="2fd39-116">Ta usługa tworzy wystąpienie AutoIP na określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

- <span data-ttu-id="2fd39-117">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-117">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2fd39-118">**name**: nazwa wystąpienia AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-118">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="2fd39-119">**ip_ptr**: wskaźnik do wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-119">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="2fd39-120">**stack_ptr**: wskaźnik do obszaru stosu wątku AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-120">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="2fd39-121">**stack_size**: rozmiar obszaru stosu wątku AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-121">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="2fd39-122">**priorytet**: priorytet wątku AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-122">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="2fd39-123">Jeśli używany jest protokół DHCP, wątek DHCP musi mieć wyższy priorytet niż wątek wystąpienia IP i wątek AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-123">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fd39-124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2fd39-124">Return Values</span></span>

- <span data-ttu-id="2fd39-125">**NX_SUCCESS**: (0X00) pomyślne utworzenie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-125">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="2fd39-126">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP tworzenia błędu.</span><span class="sxs-lookup"><span data-stu-id="2fd39-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="2fd39-127">NX_PTR_ERROR: (0x16) nieprawidłowy AutoIP, ip_ptr lub wskaźnik stosu.</span><span class="sxs-lookup"><span data-stu-id="2fd39-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="2fd39-128">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd39-128">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fd39-129">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2fd39-129">Allowed From</span></span>

<span data-ttu-id="2fd39-130">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="2fd39-130">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fd39-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fd39-131">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="2fd39-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd39-132">See Also</span></span>

<span data-ttu-id="2fd39-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2fd39-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="2fd39-134">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="2fd39-134">nx_auto_ip_delete</span></span>

<span data-ttu-id="2fd39-135">Usuń wystąpienie AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-135">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2fd39-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fd39-136">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2fd39-137">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd39-137">Description</span></span>

<span data-ttu-id="2fd39-138">Ta usługa usuwa wcześniej utworzone wystąpienie AutoIP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-138">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fd39-139">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2fd39-139">Input Parameters</span></span>

- <span data-ttu-id="2fd39-140">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-140">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fd39-141">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2fd39-141">Return Values</span></span>

- <span data-ttu-id="2fd39-142">**NX_SUCCESS**: (0X00) pomyślne usunięcie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-142">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="2fd39-143">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd usuwania.</span><span class="sxs-lookup"><span data-stu-id="2fd39-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="2fd39-144">NX_PTR_ERROR (0x16): nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-144">NX_PTR_ERROR (0x16): Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2fd39-145">NX_CALLER_ERROR (0x11): nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd39-145">NX_CALLER_ERROR (0x11): Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fd39-146">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2fd39-146">Allowed From</span></span>

<span data-ttu-id="2fd39-147">Wątki</span><span class="sxs-lookup"><span data-stu-id="2fd39-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fd39-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fd39-148">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="2fd39-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd39-149">See Also</span></span>

<span data-ttu-id="2fd39-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2fd39-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="2fd39-151">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="2fd39-151">nx_auto_ip_get_address</span></span>

<span data-ttu-id="2fd39-152">Pobierz bieżący adres AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-152">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2fd39-153">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fd39-153">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="2fd39-154">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd39-154">Description</span></span>

<span data-ttu-id="2fd39-155">Ta usługa pobiera aktualnie skonfigurowany adres AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-155">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="2fd39-156">Jeśli nie istnieje, zwracany jest adres IP 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="2fd39-156">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fd39-157">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2fd39-157">Input Parameters</span></span>

- <span data-ttu-id="2fd39-158">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-158">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2fd39-159">**local_ip_address**: miejsce docelowe dla zwrotnego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-159">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fd39-160">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2fd39-160">Return Values</span></span>

- <span data-ttu-id="2fd39-161">**NX_SUCCESS**: (0X00) pomyślne pobieranie adresu AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-161">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="2fd39-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) nieprawidłowy adres AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="2fd39-163">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-163">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2fd39-164">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd39-164">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fd39-165">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2fd39-165">Allowed From</span></span>

<span data-ttu-id="2fd39-166">Inicjalizacja, czasomierze, wątki, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="2fd39-166">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2fd39-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fd39-167">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="2fd39-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd39-168">See Also</span></span>

<span data-ttu-id="2fd39-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2fd39-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="2fd39-170">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="2fd39-170">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="2fd39-171">Ustaw interfejs sieciowy dla AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-171">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="2fd39-172">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fd39-172">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2fd39-173">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd39-173">Description</span></span>

<span data-ttu-id="2fd39-174">Ta usługa ustawia indeks dla interfejsu sieciowego, AutoIP będzie sondować dla sieciowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-174">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="2fd39-175">Wartość domyślna to zero (podstawowy interfejs sieciowy).</span><span class="sxs-lookup"><span data-stu-id="2fd39-175">The default is zero (the primary network interface).</span></span> <span data-ttu-id="2fd39-176">Dotyczy tylko urządzeń z wieloma adresami.</span><span class="sxs-lookup"><span data-stu-id="2fd39-176">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fd39-177">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2fd39-177">Input Parameters</span></span>

- <span data-ttu-id="2fd39-178">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-178">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2fd39-179">**interface_index**: interfejs do sondowania adresu IP dla</span><span class="sxs-lookup"><span data-stu-id="2fd39-179">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="2fd39-180">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2fd39-180">Return Values</span></span>

- <span data-ttu-id="2fd39-181">**NX_SUCCESS**: (0X00) pomyślnie ustawiono interfejs AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-181">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="2fd39-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0XA02) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="2fd39-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface</span></span> 
- <span data-ttu-id="2fd39-183">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-183">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2fd39-184">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd39-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fd39-185">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2fd39-185">Allowed From</span></span>

<span data-ttu-id="2fd39-186">Inicjalizacja, czasomierze, wątki, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="2fd39-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2fd39-187">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fd39-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a><span data-ttu-id="2fd39-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd39-188">See Also</span></span>

<span data-ttu-id="2fd39-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2fd39-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="2fd39-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2fd39-190">nx_auto_ip_start</span></span>

<span data-ttu-id="2fd39-191">Rozpocznij przetwarzanie AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2fd39-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fd39-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="2fd39-193">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd39-193">Description</span></span>

<span data-ttu-id="2fd39-194">Ta usługa uruchamia protokół AutoIP na wcześniej utworzonym wystąpieniu usługi AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fd39-195">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2fd39-195">Input Parameters</span></span>

- <span data-ttu-id="2fd39-196">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2fd39-197">**starting_local_address**: opcjonalny adres początkowy AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="2fd39-198">Wartość IP_ADDRESS (0, 0, 0, 0) określa, że losowy adres AutoIP powinien być pochodny.</span><span class="sxs-lookup"><span data-stu-id="2fd39-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="2fd39-199">W przeciwnym razie, jeśli określono prawidłowy adres AutoIP, NetX AutoIP próbuje przypisać ten adres.</span><span class="sxs-lookup"><span data-stu-id="2fd39-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fd39-200">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2fd39-200">Return Values</span></span>

- <span data-ttu-id="2fd39-201">**NX_SUCCESS**: (0X00) pomyślne uruchomienie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="2fd39-202">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="2fd39-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="2fd39-203">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2fd39-204">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd39-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fd39-205">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2fd39-205">Allowed From</span></span>

<span data-ttu-id="2fd39-206">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="2fd39-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fd39-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fd39-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="2fd39-208">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd39-208">See Also</span></span>

<span data-ttu-id="2fd39-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2fd39-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="2fd39-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2fd39-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="2fd39-211">Zatrzymaj przetwarzanie AutoIP</span><span class="sxs-lookup"><span data-stu-id="2fd39-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2fd39-212">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fd39-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2fd39-213">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd39-213">Description</span></span>

<span data-ttu-id="2fd39-214">Ta usługa umożliwia zatrzymanie protokołu AutoIP na wcześniej utworzonym i uruchomionym wystąpieniu usługi AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="2fd39-215">Ta usługa jest zwykle używana, gdy adres IP zostanie zmieniony za pośrednictwem protokołu DHCP lub ręcznie na adres inny niż AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fd39-216">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2fd39-216">Input Parameters</span></span>

- <span data-ttu-id="2fd39-217">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fd39-218">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2fd39-218">Return Values</span></span>

- <span data-ttu-id="2fd39-219">**NX_SUCCESS**: (0X00) pomyślne zatrzymywanie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="2fd39-220">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="2fd39-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="2fd39-221">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2fd39-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2fd39-222">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd39-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fd39-223">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2fd39-223">Allowed From</span></span>

<span data-ttu-id="2fd39-224">Wątki</span><span class="sxs-lookup"><span data-stu-id="2fd39-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fd39-225">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fd39-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="2fd39-226">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd39-226">See Also</span></span>

<span data-ttu-id="2fd39-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2fd39-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>