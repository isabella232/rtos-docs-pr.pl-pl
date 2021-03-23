---
title: Rozdział 3 — Opis usługi Azure RTO NetX Duo AutoIP Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Duo AutoIP Services (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822069"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="8953b-103">Rozdział 3 — Opis usługi Azure RTO NetX Duo AutoIP Services</span><span class="sxs-lookup"><span data-stu-id="8953b-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="8953b-104">Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Duo AutoIP Services (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="8953b-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="8953b-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8953b-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="8953b-106">**nx_auto_ip_create**: *Tworzenie wystąpienia AutoIP*</span><span class="sxs-lookup"><span data-stu-id="8953b-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="8953b-107">**nx_auto_ip_delete**: *usuwanie wystąpienia AutoIP*</span><span class="sxs-lookup"><span data-stu-id="8953b-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="8953b-108">**nx_auto_ip_get_address**: *Pobierz bieżący adres AutoIP*</span><span class="sxs-lookup"><span data-stu-id="8953b-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="8953b-109">**nx_auto_ip_set_interface**: *Ustaw interfejs IP wymagający adresu AutoIP*</span><span class="sxs-lookup"><span data-stu-id="8953b-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="8953b-110">**nx_auto_ip_start**: *Uruchamianie przetwarzania AutoIP*</span><span class="sxs-lookup"><span data-stu-id="8953b-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="8953b-111">**nx_auto_ip_stop**: *Zatrzymywanie przetwarzania AutoIP*</span><span class="sxs-lookup"><span data-stu-id="8953b-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="8953b-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="8953b-112">nx_auto_ip_create</span></span>

<span data-ttu-id="8953b-113">Utwórz wystąpienie AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8953b-114">Prototype</span><span class="sxs-lookup"><span data-stu-id="8953b-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="8953b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8953b-115">Description</span></span>

<span data-ttu-id="8953b-116">Ta usługa tworzy wystąpienie AutoIP na określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="8953b-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8953b-117">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8953b-117">Input Parameters</span></span>

- <span data-ttu-id="8953b-118">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="8953b-119">**name**: nazwa wystąpienia AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="8953b-120">**ip_ptr**: wskaźnik do wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8953b-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="8953b-121">**stack_ptr**: wskaźnik do obszaru stosu wątku AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="8953b-122">**stack_size**: rozmiar obszaru stosu wątku AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="8953b-123">**priorytet**: priorytet wątku AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="8953b-124">Jeśli używany jest protokół DHCP, wątek DHCP musi mieć wyższy priorytet niż wątek wystąpienia IP i wątek AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8953b-125">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8953b-125">Return Values</span></span>

- <span data-ttu-id="8953b-126">**NX_SUCCESS**: (0X00) pomyślne utworzenie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="8953b-127">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP tworzenia błędu.</span><span class="sxs-lookup"><span data-stu-id="8953b-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="8953b-128">NX_PTR_ERROR: (0x16) nieprawidłowy AutoIP, ip_ptr lub wskaźnik stosu.</span><span class="sxs-lookup"><span data-stu-id="8953b-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="8953b-129">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8953b-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8953b-130">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8953b-130">Allowed From</span></span>

<span data-ttu-id="8953b-131">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8953b-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8953b-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="8953b-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="8953b-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8953b-133">See Also</span></span>

<span data-ttu-id="8953b-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="8953b-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="8953b-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="8953b-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="8953b-136">Usuń wystąpienie AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8953b-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="8953b-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8953b-138">Opis</span><span class="sxs-lookup"><span data-stu-id="8953b-138">Description</span></span>

<span data-ttu-id="8953b-139">Ta usługa usuwa wcześniej utworzone wystąpienie AutoIP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="8953b-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8953b-140">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8953b-140">Input Parameters</span></span>

- <span data-ttu-id="8953b-141">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8953b-142">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8953b-142">Return Values</span></span>

- <span data-ttu-id="8953b-143">**NX_SUCCESS**: (0X00) pomyślne usunięcie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="8953b-144">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd usuwania.</span><span class="sxs-lookup"><span data-stu-id="8953b-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="8953b-145">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="8953b-146">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8953b-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8953b-147">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8953b-147">Allowed From</span></span>

<span data-ttu-id="8953b-148">Wątki</span><span class="sxs-lookup"><span data-stu-id="8953b-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8953b-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="8953b-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8953b-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8953b-150">See Also</span></span>

<span data-ttu-id="8953b-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="8953b-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="8953b-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="8953b-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="8953b-153">Pobierz bieżący adres AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8953b-154">Prototype</span><span class="sxs-lookup"><span data-stu-id="8953b-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="8953b-155">Opis</span><span class="sxs-lookup"><span data-stu-id="8953b-155">Description</span></span>

<span data-ttu-id="8953b-156">Ta usługa pobiera aktualnie skonfigurowany adres AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="8953b-157">Jeśli nie istnieje, zwracany jest adres IP 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="8953b-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8953b-158">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8953b-158">Input Parameters</span></span>

- <span data-ttu-id="8953b-159">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="8953b-160">**local_ip_address**: miejsce docelowe dla zwrotnego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8953b-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="8953b-161">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8953b-161">Return Values</span></span>

- <span data-ttu-id="8953b-162">**NX_SUCCESS**: (0X00) pomyślne pobieranie adresu AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="8953b-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) nieprawidłowy adres AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="8953b-164">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="8953b-165">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8953b-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8953b-166">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8953b-166">Allowed From</span></span>

<span data-ttu-id="8953b-167">Inicjalizacja, czasomierze, wątki, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8953b-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8953b-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="8953b-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="8953b-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8953b-169">See Also</span></span>

<span data-ttu-id="8953b-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="8953b-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="8953b-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="8953b-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="8953b-172">Ustaw interfejs sieciowy dla AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="8953b-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="8953b-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8953b-174">Opis</span><span class="sxs-lookup"><span data-stu-id="8953b-174">Description</span></span>

<span data-ttu-id="8953b-175">Ta usługa ustawia indeks dla interfejsu sieciowego, AutoIP będzie sondować dla sieciowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="8953b-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="8953b-176">Wartość domyślna to zero (podstawowy interfejs sieciowy).</span><span class="sxs-lookup"><span data-stu-id="8953b-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="8953b-177">Dotyczy tylko urządzeń z wieloma adresami.</span><span class="sxs-lookup"><span data-stu-id="8953b-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8953b-178">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8953b-178">Input Parameters</span></span>

- <span data-ttu-id="8953b-179">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="8953b-180">**interface_index**: interfejs do sondowania adresu IP dla</span><span class="sxs-lookup"><span data-stu-id="8953b-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="8953b-181">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8953b-181">Return Values</span></span>

- <span data-ttu-id="8953b-182">**NX_SUCCESS**: (0X00) pomyślnie ustawiono interfejs AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="8953b-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0XA02) Nieprawidłowy interfejs sieciowy NX_PTR_ERROR (0X16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="8953b-184">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8953b-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8953b-185">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8953b-185">Allowed From</span></span>

<span data-ttu-id="8953b-186">Inicjalizacja, czasomierze, wątki, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8953b-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8953b-187">Przykład</span><span class="sxs-lookup"><span data-stu-id="8953b-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="8953b-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8953b-188">See Also</span></span>

<span data-ttu-id="8953b-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="8953b-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="8953b-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="8953b-190">nx_auto_ip_start</span></span>

<span data-ttu-id="8953b-191">Rozpocznij przetwarzanie AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8953b-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="8953b-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="8953b-193">Opis</span><span class="sxs-lookup"><span data-stu-id="8953b-193">Description</span></span>

<span data-ttu-id="8953b-194">Ta usługa uruchamia protokół AutoIP na wcześniej utworzonym wystąpieniu usługi AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8953b-195">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8953b-195">Input Parameters</span></span>

- <span data-ttu-id="8953b-196">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="8953b-197">**starting_local_address**: opcjonalny adres początkowy AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="8953b-198">Wartość IP_ADDRESS (0, 0, 0, 0) określa, że losowy adres AutoIP powinien być pochodny.</span><span class="sxs-lookup"><span data-stu-id="8953b-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="8953b-199">W przeciwnym razie, jeśli określono prawidłowy adres AutoIP, NetX AutoIP próbuje przypisać ten adres.</span><span class="sxs-lookup"><span data-stu-id="8953b-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="8953b-200">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8953b-200">Return Values</span></span>

- <span data-ttu-id="8953b-201">**NX_SUCCESS**: (0X00) pomyślne uruchomienie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="8953b-202">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="8953b-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="8953b-203">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="8953b-204">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8953b-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8953b-205">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8953b-205">Allowed From</span></span>

<span data-ttu-id="8953b-206">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="8953b-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8953b-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="8953b-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="8953b-208">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8953b-208">See Also</span></span>

<span data-ttu-id="8953b-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="8953b-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="8953b-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="8953b-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="8953b-211">Zatrzymaj przetwarzanie AutoIP</span><span class="sxs-lookup"><span data-stu-id="8953b-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8953b-212">Prototype</span><span class="sxs-lookup"><span data-stu-id="8953b-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="8953b-213">Opis</span><span class="sxs-lookup"><span data-stu-id="8953b-213">Description</span></span>

<span data-ttu-id="8953b-214">Ta usługa umożliwia zatrzymanie protokołu AutoIP na wcześniej utworzonym i uruchomionym wystąpieniu usługi AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="8953b-215">Ta usługa jest zwykle używana, gdy adres IP zostanie zmieniony za pośrednictwem protokołu DHCP lub ręcznie na adres inny niż AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8953b-216">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="8953b-216">Input Parameters</span></span>

- <span data-ttu-id="8953b-217">**auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8953b-218">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8953b-218">Return Values</span></span>

- <span data-ttu-id="8953b-219">**NX_SUCCESS**: (0X00) pomyślne zatrzymywanie AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="8953b-220">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="8953b-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="8953b-221">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.</span><span class="sxs-lookup"><span data-stu-id="8953b-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="8953b-222">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8953b-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8953b-223">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8953b-223">Allowed From</span></span>

<span data-ttu-id="8953b-224">Wątki</span><span class="sxs-lookup"><span data-stu-id="8953b-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8953b-225">Przykład</span><span class="sxs-lookup"><span data-stu-id="8953b-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="8953b-226">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8953b-226">See Also</span></span>

<span data-ttu-id="8953b-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="8953b-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>