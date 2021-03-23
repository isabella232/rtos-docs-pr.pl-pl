---
title: Rozdział 3 — Opis usług klienta DHCP w usłudze Azure RTO NetX
description: Ten rozdział zawiera opis wszystkich usług DHCP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822699"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="ccb1f-103">Rozdział 3 — Opis usług klienta DHCP w usłudze Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="ccb1f-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="ccb1f-104">Ten rozdział zawiera opis wszystkich usług DHCP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ccb1f-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ccb1f-106">**nx_dhcp_create**: *Tworzenie wystąpienia DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="ccb1f-107">**nx_dhcp_clear_broadcast_flag**: Wyczyść flagę emisji na komunikatach klienta</span><span class="sxs-lookup"><span data-stu-id="ccb1f-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="ccb1f-108">**nx_dhcp_delete**: *usuwanie wystąpienia DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="ccb1f-109">**nx_dhcp_decline**: Wyślij *komunikat odrzucania do serwera*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="ccb1f-110">**nx_dhcp_force_renew**: *Wyślij komunikat odnowienia Force*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="ccb1f-111">**nx_dhcp_packet_pool_set**: *Ustaw pulę pakietów klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="ccb1f-112">**nx_dhcp_release**: Wyślij *komunikat o zwolnieniu do serwera*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="ccb1f-113">**nx_dhcp_reinitialize**: *Wyczyść parametry sieciowe klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="ccb1f-114">**nx_dhcp_request_client_ip**: *Określ konkretny adres IP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="ccb1f-115">**nx_dhcp_send_request**: *Wyślij komunikat DHCP do serwera*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="ccb1f-116">**nx_dhcp_server_address_get**: *pobieranie adresu serwera DHCP klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="ccb1f-117">**nx_dhcp_set_interface_index**: *Określ interfejs sieciowy klienta*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="ccb1f-118">**nx_dhcp_start**: *Uruchamianie przetwarzania DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="ccb1f-119">**nx_dhcp_state_change_notify**: *powiadamianie o zmianie stanu protokołu DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="ccb1f-120">**nx_dhcp_stop**: *ZAtrzymywanie przetwarzania DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="ccb1f-121">**nx_dhcp_user_option_retrieve**: *pobieranie opcji DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="ccb1f-122">**nx_dhcp_user_option_convert**: *przekonwertuj cztery BAJTy na ULONG*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="ccb1f-123">Usługi klienta DHCP specyficzne dla interfejsu:</span><span class="sxs-lookup"><span data-stu-id="ccb1f-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="ccb1f-124">**nx_dhcp_interface_clear_broadcast_flag**: *Wyczyść flagę emisji na komunikatach klienta w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="ccb1f-125">**nx_dhcp_interface_enable**: *Włącz interfejs do uruchamiania protokołu DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-126">**nx_dhcp_interface_disable**: *Wyłącz interfejs do uruchamiania protokołu DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-127">**nx_dhcp_interface_decline**: *Wyślij komunikat odrzucania do serwera w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-128">**nx_dhcp_interface_force_renew**: *Wyślij komunikat wymuszania odnowienia w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-129">**nx_dhcp_interface_reinitialize**: *Wyczyść parametry sieciowe klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-130">**nx_dhcp_interface_release**: *wysyła komunikat o zwolnieniu do serwera w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-131">**nx_dhcp_interface_request_client_ip**: *Określ konkretny adres IP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-132">**nx_dhcp_interface_send_request**: *Wyślij komunikat DHCP do serwera w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-133">**nx_dhcp_interface_server_address_get**: *Pobierz adres IP serwera DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-134">**nx_dhcp_interface_start**: *Uruchamianie przetwarzania klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-135">**nx_dhcp_interface_stop**: *Zatrzymywanie przetwarzania klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-136">**nx_dhcp_interface_state_change_notify**: *Ustaw funkcję wywołania zwrotnego, gdy stan DHCP zostanie zmieniony w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-137">**nx_dhcp_interface_user_option_retrieve**: *Pobierz określoną opcję DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="ccb1f-138">Usługi klienta DHCP, jeśli NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:</span><span class="sxs-lookup"><span data-stu-id="ccb1f-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ccb1f-139">**nx_dhcp_resume**: *Wznów poprzednio ustanowiony stan klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="ccb1f-140">**nx_dhcp_suspend**: *wstrzymywanie przetwarzania stanu klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="ccb1f-141">**nx_dhcp_client_get_record**: *Utwórz rekord stanu klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="ccb1f-142">**nx_dhcp_client_restore_record**: *przywracanie wcześniej zapisanego rekordu do klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="ccb1f-143">**nx_dhcp_client_update_time_remaining**: *zaktualizuj pozostały czas w bieżącym stanie DHCP*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="ccb1f-144">Specyficzne dla interfejsu usługi klienta DHCP, jeśli NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:</span><span class="sxs-lookup"><span data-stu-id="ccb1f-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ccb1f-145">**nx_dhcp_client_interface_get_record**: *Utwórz rekord stanu klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-146">**nx_dhcp_client_interface_restore_record**: *przywracanie wcześniej zapisanego rekordu do klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="ccb1f-147">**nx_dhcp_client_interface_update_time_remaining**: *zaktualizuj pozostały czas w bieżącym stanie DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="ccb1f-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="ccb1f-148">nx_dhcp_create</span></span>

<span data-ttu-id="ccb1f-149">Tworzenie wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-151">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-151">Description</span></span>

<span data-ttu-id="ccb1f-152">Ta usługa tworzy wystąpienie DHCP dla utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="ccb1f-153">Domyślnie interfejs podstawowy jest włączony do uruchamiania protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="ccb1f-154">Nazwy wejściowe, które nie są używane w implementacji NetX klienta DHCP, muszą być zgodne z kryteriami RFC 1035 dla nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="ccb1f-155">Łączna długość nie może przekraczać 255 znaków, etykiety oddzielone kropkami muszą zaczynać się literą i kończyć literą lub cyfrą i mogą zawierać łączniki, ale nie inny znak inny niż alfanumeryczny.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="ccb1f-156">Jeśli aplikacja ma uruchamiać inne interfejsy zarejestrowane przy użyciu wystąpienia protokołu IP (przy użyciu *nx_ip_interface_attach*), aplikacja może wywoływać *nx_dhcp_set_interface_index* , aby uruchomić usługę DHCP tylko na tym interfejsie, lub *nx_dhcp_interface_enable* do uruchamiania protokołu DHCP również w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="ccb1f-157">Aby uzyskać więcej informacji, zobacz opis tych usług.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="ccb1f-158">Aplikacja musi upewnić się, że ładunek puli pakietów klienta DHCP może obsługiwać minimalny rozmiar komunikatu DHCP określony w sekcji RFC 2131 (548 bajtów danych komunikatów DHCP oraz nagłówków protokołu UDP, adresu IP i ramki sieci fizycznej).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-159">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-159">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-160">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ccb1f-161">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="ccb1f-162">**name_ptr** Wskaźnik na nazwę hosta dla wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-163">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-163">Return Values</span></span>

- <span data-ttu-id="ccb1f-164">**NX_SUCCESS** (0X00) pomyślne utworzenie protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="ccb1f-165">**NX_DHCP_INVALID_NAME** (0XA8) Nieprawidłowa nazwa hosta</span><span class="sxs-lookup"><span data-stu-id="ccb1f-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="ccb1f-166">Ładunek **NX_DHCP_INVALID_PAYLOAD** (0x9C) jest za mały dla komunikatu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="ccb1f-167">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-168">Allowed From</span></span>

<span data-ttu-id="ccb1f-169">**Wątki,** Zainicjować</span><span class="sxs-lookup"><span data-stu-id="ccb1f-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="ccb1f-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="ccb1f-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="ccb1f-172">Włącz określony interfejs do uruchamiania protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ccb1f-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-174">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-174">Description</span></span>

<span data-ttu-id="ccb1f-175">Ta usługa umożliwia określony interfejs do uruchamiania protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="ccb1f-176">Domyślnie interfejs podstawowy jest włączony dla klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="ccb1f-177">W tym momencie można uruchomić protokół DHCP w tym interfejsie przez wywołanie *nx_dhcp_interface_start* lub uruchomienie protokołu DHCP we wszystkich włączonych interfejsach *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="ccb1f-178">Zwróć uwagę, że aplikacja musi najpierw zarejestrować ten interfejs z wystąpieniem IP przy użyciu *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="ccb1f-179">Ponadto w celu dodania tego interfejsu do listy włączonych interfejsów musi istnieć dostępny interfejs klienta DHCP "rekord".</span><span class="sxs-lookup"><span data-stu-id="ccb1f-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="ccb1f-180">Domyślnie NX_DHCP_CLIENT_MAX_RECORDS jest zdefiniowana na 1.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="ccb1f-181">Ustaw tę opcję na maksymalną liczbę interfejsów oczekiwanych na równoczesne uruchomienie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="ccb1f-182">Zwykle NX_DHCP_CLIENT_MAX_RECORDS będzie równa NX_MAX_PHYSICAL_INTERFACES; Jeśli jednak urządzenie ma więcej interfejsów fizycznych niż oczekuje na uruchomienie klienta DHCP, może zaoszczędzić pamięć przez ustawienie NX_DHCP_CLIENT_MAX_RECORDS na mniejszą niż ten numer.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="ccb1f-183">Nie istnieje jeden do jednego mapowanie interfejsów fizycznych z rekordami interfejsu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="ccb1f-184">Różnica między tą usługą a *nx_dhcp_set_interface_index* to ta, która powoduje, że tylko jeden interfejs do uruchamiania protokołu DHCP, podczas gdy ta usługa po prostu dodaje określony interfejs do listy interfejsów klienta włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ccb1f-185">Aby wyłączyć interfejs dla protokołu DHCP, aplikacja może wywołać usługę *nx_dhcp_interface_disable* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-186">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-186">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-187">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ccb1f-188">**interface_index** Indeks interfejsu umożliwiającego włączenie protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-189">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-189">Return Values</span></span>

- <span data-ttu-id="ccb1f-190">**NX_SUCCESS** (0X00) pomyślne włączenie protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="ccb1f-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) Brak dostępnego rekordu dla innego interfejsu, który ma zostać włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-192">Interfejs **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) z włączonym protokołem DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-193">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-194">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-195">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-195">Allowed From</span></span>

<span data-ttu-id="ccb1f-196">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ccb1f-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="ccb1f-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="ccb1f-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="ccb1f-199">Wyłączenie określonego interfejsu w celu uruchomienia protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ccb1f-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-201">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-201">Description</span></span>

<span data-ttu-id="ccb1f-202">Ta usługa wyłącza określony interfejs na potrzeby uruchamiania protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="ccb1f-203">Ponownie inicjuje klienta DHCP w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="ccb1f-204">Aby ponownie uruchomić klienta DHCP, aplikacja musi ponownie włączyć interfejs przy użyciu *nx_dhcp_interface_enable* i ponownie uruchomić usługę DHCP, wywołując *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-205">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-205">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-206">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ccb1f-207">**interface_index** Indeks interfejsu w celu wyłączenia protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-208">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-208">Return Values</span></span>

- <span data-ttu-id="ccb1f-209">**NX_SUCCESS** (0X00) pomyślne utworzenie protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="ccb1f-210">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-211">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-212">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ccb1f-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ccb1f-213">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-214">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-214">Allowed From</span></span>

<span data-ttu-id="ccb1f-215">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="ccb1f-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ccb1f-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="ccb1f-218">Ustaw flagę emisji DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ccb1f-220">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-220">Description</span></span>

<span data-ttu-id="ccb1f-221">Ta usługa ustawia lub czyści flagę emisji w nagłówku komunikatu DHCP dla wszystkich interfejsów włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-222">W przypadku niektórych komunikatów DHCP (np. DISCOVER) flaga emisji jest ustawiona na emisję, ponieważ klient nie ma adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="ccb1f-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="ccb1f-223">__clear_flag__</span></span>


- <span data-ttu-id="ccb1f-224">Flaga emisji **NX_TRUE** jest wyczyszczona (Żądaj odpowiedzi emisji pojedynczej)</span><span class="sxs-lookup"><span data-stu-id="ccb1f-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="ccb1f-225">Ustawiono flagę emisji **NX_FALSE** (odpowiedź na żądanie emisji)</span><span class="sxs-lookup"><span data-stu-id="ccb1f-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="ccb1f-226">Ta usługa jest przeznaczona dla klientów DHCP, którzy muszą przejść przez router, aby uzyskać dostęp do serwera DHCP, gdzie router odrzuca komunikaty emisji przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-227">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-227">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-228">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="ccb1f-229">**clear_flag** Wartość, dla której ma zostać ustawiona flaga emisji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-230">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-230">Return Values</span></span>

- <span data-ttu-id="ccb1f-231">**NX_SUCCESS** (0X00) pomyślnie zaktualizował flagę emisji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="ccb1f-232">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-233">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ccb1f-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-234">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-234">Allowed From</span></span>

<span data-ttu-id="ccb1f-235">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ccb1f-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-236">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="ccb1f-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ccb1f-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="ccb1f-238">Ustaw lub wyczyść flagę emisji w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-239">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ccb1f-240">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-240">Description</span></span>

<span data-ttu-id="ccb1f-241">Ta usługa umożliwia aplikacji hosta klienta DHCP Ustawianie lub czyszczenie flagi emisji w komunikatach klienta DHCP na serwerze DHCP w określonym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="ccb1f-242">Aby uzyskać więcej informacji, zobacz **nx_dhcp_clear_broadcast_flag**</span><span class="sxs-lookup"><span data-stu-id="ccb1f-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-243">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-243">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-244">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="ccb1f-245">**interface_index** Indeks interfejsu służący do ustawiania flagi emisji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="ccb1f-246">**clear_flag** Wartość, dla której ma zostać ustawiona flaga emisji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-247">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-247">Return Values</span></span>

- <span data-ttu-id="ccb1f-248">**NX_SUCCESS** (0X00) pomyślnie zaktualizował flagę emisji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="ccb1f-249">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-250">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-251">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-252">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-252">Allowed From</span></span>

<span data-ttu-id="ccb1f-253">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ccb1f-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-254">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="ccb1f-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="ccb1f-255">nx_dhcp_delete</span></span>

<span data-ttu-id="ccb1f-256">Usuwanie wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-257">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-258">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-258">Description</span></span>

<span data-ttu-id="ccb1f-259">Ta usługa usuwa wcześniej utworzone wystąpienie usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-260">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-260">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-261">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-262">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-262">Return Values</span></span>

- <span data-ttu-id="ccb1f-263">**NX_SUCCESS** (0X00) pomyślne usunięcie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="ccb1f-264">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-265">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-266">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-266">Allowed From</span></span>

<span data-ttu-id="ccb1f-267">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-268">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="ccb1f-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="ccb1f-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="ccb1f-270">Wyślij komunikat Force o odnowieniu</span><span class="sxs-lookup"><span data-stu-id="ccb1f-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="ccb1f-271">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-272">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-272">Description</span></span>

<span data-ttu-id="ccb1f-273">Ta usługa umożliwia aplikacji hosta wysyłanie komunikatów Force w celu odnowienia na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-274">Klient DHCP musi być w stanie powiązanym.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="ccb1f-275">Ta funkcja ustawia stan do ODNOWIENIa, aby klient DHCP próbował odnowić działanie przed upływem limitu czasu T1.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="ccb1f-276">Aby wysłać Force w określonym interfejsie, gdy jest włączona obsługa protokołu DHCP w wielu interfejsach, użyj *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-277">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-277">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-278">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-279">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-279">Return Values</span></span>

- <span data-ttu-id="ccb1f-280">**NX_SUCCESS** (0X00) pomyślnie wysłał wymuszenie odnowienia.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="ccb1f-281">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-282">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-283">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-283">Allowed From</span></span>

<span data-ttu-id="ccb1f-284">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-285">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="ccb1f-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="ccb1f-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="ccb1f-287">Wyślij komunikat Wymuś odnowienie w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-289">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-289">Description</span></span>

<span data-ttu-id="ccb1f-290">Ta usługa umożliwia aplikacji hosta wysyłanie komunikatów Force (Wymuś odnowienie) w interfejsie wejściowym, o ile ten interfejs został włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ccb1f-291">Klient DHCP w określonym interfejsie musi być w stanie powiązanym.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="ccb1f-292">Ta funkcja ustawia stan do ODNOWIENIa, aby klient DHCP próbował odnowić działanie przed upływem limitu czasu T1.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-293">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-293">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-294">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-295">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-295">Return Values</span></span>

- <span data-ttu-id="ccb1f-296">**NX_SUCCESS** (0X00) pomyślnie wysłał wymuszenie odnowienia.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="ccb1f-297">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-298">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-299">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-300">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-300">Allowed From</span></span>

<span data-ttu-id="ccb1f-301">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-302">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="ccb1f-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="ccb1f-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="ccb1f-304">Ustawianie puli pakietów klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-305">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-306">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-306">Description</span></span>

<span data-ttu-id="ccb1f-307">Ta usługa umożliwia aplikacji utworzenie puli pakietów klienta DHCP, przekazując wskaźnik do wcześniej utworzonej puli pakietów w ramach tego wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="ccb1f-308">Aby można było użyć tej funkcji, aplikacja hosta musi definiować NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="ccb1f-309">Po zdefiniowaniu usługa *nx_dhcp_create* nie utworzy puli pakietów klienta.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="ccb1f-310">Należy pamiętać, że aplikacja zaleca się użycie wartości domyślnych dla ładunku puli pakietów klienta DHCP zdefiniowanego jako NX_DHCP_PACKET_PAYLOAD w *nx_dhcp. h* podczas tworzenia puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-311">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-311">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-312">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ccb1f-313">**packet_pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów</span><span class="sxs-lookup"><span data-stu-id="ccb1f-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-314">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-314">Return Values</span></span>

- <span data-ttu-id="ccb1f-315">**NX_SUCCESS** (0x00) Pula pakietów klienta DHCP jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="ccb1f-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="ccb1f-316">Usługa **NX_NOT_ENABLED** (0x14) nie jest włączona</span><span class="sxs-lookup"><span data-stu-id="ccb1f-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="ccb1f-317">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-318">Ładunek NX_DHCP_INVALID_PAYLOAD (0x9C) jest za mały</span><span class="sxs-lookup"><span data-stu-id="ccb1f-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-319">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-319">Allowed From</span></span>

<span data-ttu-id="ccb1f-320">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-321">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="ccb1f-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ccb1f-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="ccb1f-323">Ustaw żądany adres IP dla wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-324">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ccb1f-325">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-325">Description</span></span>

<span data-ttu-id="ccb1f-326">Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP przy pierwszym interfejsie włączonym dla protokołu DHCP w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="ccb1f-327">Jeśli flaga *skip_discover_message* jest ustawiona, klient DHCP pomija komunikat odnajdywania i wysyła komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="ccb1f-328">Aby ustawić żądanie dla określonego adresu IP dla komunikatów DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_request_client_ip* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-329">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-329">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-330">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ccb1f-331">**client_ip_address** Adres IP do żądania z serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="ccb1f-332">**skip_discover_message** W przypadku wartości true klient DHCP wysyła komunikat żądania</span><span class="sxs-lookup"><span data-stu-id="ccb1f-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="ccb1f-333">W przypadku wartości false wysyła komunikat odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-334">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-334">Return Values</span></span>

- <span data-ttu-id="ccb1f-335">**NX_SUCCESS** (0x00) wybrano żądany adres IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="ccb1f-336">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-337">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-338">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="ccb1f-339">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-339">Allowed From</span></span>

<span data-ttu-id="ccb1f-340">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-341">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="ccb1f-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ccb1f-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="ccb1f-343">Ustaw żądany adres IP dla wystąpienia DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-344">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ccb1f-345">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-345">Description</span></span>

<span data-ttu-id="ccb1f-346">Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ccb1f-347">Jeśli flaga *skip_discover_message* jest ustawiona, klient DHCP pomija komunikat odnajdywania i wysyła komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-348">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-348">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-349">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ccb1f-350">**Interface_index** Indeks interfejsu do żądania adresu IP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="ccb1f-351">**client_ip_address** Adres IP do żądania z serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="ccb1f-352">**skip_discover_message** W przypadku wartości true klient DHCP wysyła komunikat żądania; w przeciwnym razie zostanie wysłany komunikat odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-353">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-353">Return Values</span></span>

- <span data-ttu-id="ccb1f-354">**NX_SUCCESS** (0x00) wybrano żądany adres IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="ccb1f-355">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-356">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-357">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ccb1f-358">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-358">Allowed From</span></span>

<span data-ttu-id="ccb1f-359">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-360">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="ccb1f-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ccb1f-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="ccb1f-362">Wyczyść parametry sieci klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="ccb1f-363">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-364">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-364">Description</span></span>

<span data-ttu-id="ccb1f-365">Ta usługa czyści parametry sieciowe aplikacji hosta (adres IP, adres sieciowy i maska sieci), a następnie czyści stan klienta DHCP we wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-366">Jest on używany w połączeniu z *nx_dhcp_stop* i *nx_dhcp_start* do "ponownego uruchomienia" komputera stanu DHCP:</span><span class="sxs-lookup"><span data-stu-id="ccb1f-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="ccb1f-367">nx_dhcp_stop (&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="ccb1f-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="ccb1f-368">nx_dhcp_reinitialize (&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="ccb1f-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="ccb1f-369">nx_dhcp_start (&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="ccb1f-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="ccb1f-370">Aby ponownie zainicjować klienta DHCP w określonym interfejsie, gdy na serwerze DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_reinitialize* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-371">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-371">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-372">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-373">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-373">Return Values</span></span>

- <span data-ttu-id="ccb1f-374">**NX_SUCCESS** (0X00) protokół DHCP został pomyślnie zainicjowany ponownie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="ccb1f-375">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-376">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-376">Allowed From</span></span>

<span data-ttu-id="ccb1f-377">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-378">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="ccb1f-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ccb1f-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="ccb1f-380">Wyczyść parametry sieciowe klienta DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="ccb1f-381">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-382">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-382">Description</span></span>

<span data-ttu-id="ccb1f-383">Ta usługa czyści parametry sieci (adres IP, adres sieciowy i maska sieci) w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ccb1f-384">Aby uzyskać więcej informacji, zobacz *nx_dhcp_reinitialize* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-385">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-385">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-386">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia usługi DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="ccb1f-387">**interface_index** Indeks interfejsu, który ma zostać ponownie zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-388">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-388">Return Values</span></span>

- <span data-ttu-id="ccb1f-389">Pomyślnie zainicjowano Interfejs **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="ccb1f-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="ccb1f-390">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-391">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-392">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ccb1f-393">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-394">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-394">Allowed From</span></span>

<span data-ttu-id="ccb1f-395">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-396">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="ccb1f-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="ccb1f-397">nx_dhcp_release</span></span>

<span data-ttu-id="ccb1f-398">Zwolnij adres IP dzierżawy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-399">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-400">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-400">Description</span></span>

<span data-ttu-id="ccb1f-401">Ta usługa zwalnia adres IP uzyskany z serwera DHCP, wysyłając do niego komunikat o wersji.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="ccb1f-402">Następnie ponownie inicjuje klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="ccb1f-403">Ta usługa jest stosowana do wszystkich interfejsów włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ccb1f-404">Aplikacja może ponownie uruchomić klienta DHCP, wywołując *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="ccb1f-405">Aby zwolnić adres z powrotem do serwera DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_release*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-406">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-406">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-407">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-408">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-408">Return Values</span></span>

- <span data-ttu-id="ccb1f-409">**NX_SUCCESS** (0X00) pomyślne wydanie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="ccb1f-410">**NX_DHCP_NOT_BOUND** (0x94) adres IP nie został wydzierżawiony, więc nie można go zwolnić.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="ccb1f-411">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-412">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-413">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-413">Allowed From</span></span>

<span data-ttu-id="ccb1f-414">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-415">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="ccb1f-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="ccb1f-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="ccb1f-417">Zwolnij adres IP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-418">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-419">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-419">Description</span></span>

<span data-ttu-id="ccb1f-420">Ta usługa zwalnia adres IP uzyskany z serwera DHCP w określonym interfejsie i ponownie inicjuje klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="ccb1f-421">Klienta DHCP można uruchomić ponownie, wywołując *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-422">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-422">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-423">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-424">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-424">Return Values</span></span>

- <span data-ttu-id="ccb1f-425">**NX_SUCCESS** (0X00) pomyślne wydanie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="ccb1f-426">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-427">**NX_DHCP_NOT_BOUND** (0x94) adres IP nie został wydzierżawiony, więc nie można go zwolnić.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="ccb1f-428">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-429">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ccb1f-430">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-431">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-431">Allowed From</span></span>

<span data-ttu-id="ccb1f-432">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-433">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="ccb1f-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="ccb1f-434">nx_dhcp_decline</span></span>

<span data-ttu-id="ccb1f-435">Odrzuć adres IP z serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-436">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-437">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-437">Description</span></span>

<span data-ttu-id="ccb1f-438">Ta usługa odrzuca adres IP dzierżawiony z serwera DHCP na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-439">W przypadku zdefiniowania NX_DHCP_CLIENT_ SEND_ ARP_PROBE klient DHCP wyśle komunikat o ODRZUCENIu, jeśli wykryje, że adres IP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="ccb1f-440">Zobacz **sondy protokołu ARP** w rozdziale 1, aby uzyskać więcej informacji na temat konfiguracji sondowania ARP w kliencie DHCP NetX.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="ccb1f-441">Aplikacja może korzystać z tej usługi, aby odrzucić swój adres IP, jeśli odnajdzie adres jest używany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="ccb1f-442">Ta usługa ponownie inicjalizuje klienta DHCP, aby mógł on zostać oduruchamiany przez wywołanie *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-443">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-443">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-444">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-445">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-445">Return Values</span></span>

- <span data-ttu-id="ccb1f-446">Odrzucanie **NX_SUCCESS** (0x00) zostało pomyślnie wysłane</span><span class="sxs-lookup"><span data-stu-id="ccb1f-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="ccb1f-447">**NX_DHCP_NOT_STARTED** (0x96) wystąpienie DHCP nie zostało uruchomione</span><span class="sxs-lookup"><span data-stu-id="ccb1f-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="ccb1f-448">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-449">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ccb1f-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-450">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-450">Allowed From</span></span>

<span data-ttu-id="ccb1f-451">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-452">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="ccb1f-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="ccb1f-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="ccb1f-454">Odrzuć adres IP z serwera DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-455">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-456">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-456">Description</span></span>

<span data-ttu-id="ccb1f-457">Ta usługa wysyła do serwera komunikat o ODRZUCENIu, aby odrzucić adres IP przypisany przez serwer DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="ccb1f-458">Powoduje również ponowne zainicjowanie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="ccb1f-459">Aby uzyskać więcej informacji, zobacz *nx_dhcp_decline* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-460">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-460">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-461">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-462">**Interface_index** Indeks interfejsu do odrzucania adresu IP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-463">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-463">Return Values</span></span>

- <span data-ttu-id="ccb1f-464">**NX_SUCCESS** (0x00) wysłano komunikat o ODRZUCENIu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="ccb1f-465">Klient DHCP **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="ccb1f-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="ccb1f-466">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-467">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-468">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ccb1f-469">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-470">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-470">Allowed From</span></span>

<span data-ttu-id="ccb1f-471">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-472">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="ccb1f-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="ccb1f-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="ccb1f-474">Wyślij komunikat DHCP do serwera</span><span class="sxs-lookup"><span data-stu-id="ccb1f-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-475">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="ccb1f-476">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-476">Description</span></span>

<span data-ttu-id="ccb1f-477">Ta usługa wysyła określony komunikat DHCP do serwera DHCP przy pierwszym interfejsie z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ccb1f-478">Aby wysłać wiadomość wydania lub odrzucić, aplikacja musi odpowiednio używać *nx_dhcp [_interface] _release*() lub *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ccb1f-479">Aby można było używać tej usługi, należy uruchomić klienta DHCP, z wyjątkiem wysyłania komunikatu INFORM_REQUEST typu.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="ccb1f-480">Ta usługa nie jest przeznaczona dla aplikacji hosta na dysk, na którym znajduje się komputer stanu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-481">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-481">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-482">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ccb1f-483">**dhcp_message_type** Żądanie komunikatu (zdefiniowane w *nx_dhcp. h*)</span><span class="sxs-lookup"><span data-stu-id="ccb1f-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-484">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-484">Return Values</span></span>

- <span data-ttu-id="ccb1f-485">**NX_SUCCESS** (0x00) wysłano komunikat DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="ccb1f-486">**NX_DHCP_NOT_STARTED** (0X96) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="ccb1f-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="ccb1f-487">**NX_DHCP_INVALID_MESSAGE** (0X9B) Nieprawidłowy typ komunikatu do wysłania</span><span class="sxs-lookup"><span data-stu-id="ccb1f-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="ccb1f-488">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ccb1f-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-489">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-489">Allowed From</span></span>

<span data-ttu-id="ccb1f-490">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-491">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="ccb1f-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="ccb1f-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="ccb1f-493">Wyślij komunikat DHCP do serwera w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-494">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="ccb1f-495">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-495">Description</span></span>

<span data-ttu-id="ccb1f-496">Ta usługa wysyła komunikat do serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-497">Aby wysłać wiadomość wydania lub odrzucić, aplikacja musi odpowiednio używać *nx_dhcp [_interface] _release*() lub *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ccb1f-498">Aby korzystać z tej usługi, należy uruchomić klienta DHCP, z wyjątkiem wysyłania komunikatu żądania INFORM protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="ccb1f-499">Ta usługa nie jest przeznaczona dla aplikacji hosta na dysk, na którym znajduje się komputer stanu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-500">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-500">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-501">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ccb1f-502">**Interface_index** Indeks interfejsu, na którym ma zostać wysłany komunikat</span><span class="sxs-lookup"><span data-stu-id="ccb1f-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="ccb1f-503">**dhcp_message_type** Żądanie komunikatu (zdefiniowane w *nx_dhcp. h*)</span><span class="sxs-lookup"><span data-stu-id="ccb1f-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-504">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-504">Return Values</span></span>

- <span data-ttu-id="ccb1f-505">**NX_SUCCESS** (0x00) wysłano komunikat DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="ccb1f-506">**NX_DHCP_NOT_STARTED** (0X96) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="ccb1f-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="ccb1f-507">**NX_DHCP_INVALID_MESSAGE** (0X9B) Nieprawidłowy typ komunikatu do wysłania</span><span class="sxs-lookup"><span data-stu-id="ccb1f-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="ccb1f-508">Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-509">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-510">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ccb1f-511">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-512">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-512">Allowed From</span></span>

<span data-ttu-id="ccb1f-513">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-514">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="ccb1f-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ccb1f-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="ccb1f-516">Pobierz adres IP serwera DHCP klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-517">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ccb1f-518">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-518">Description</span></span>

<span data-ttu-id="ccb1f-519">Ta usługa Pobiera adres IP serwera DHCP klienta DHCP na pierwszym interfejsie z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ccb1f-520">Obiekt wywołujący może korzystać tylko z tej usługi po powiązaniu klienta DHCP z adresem IP przydzielonym przez serwer DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="ccb1f-521">Aplikacja hosta może użyć usługi *nx_ip_status_check* , aby sprawdzić, czy adres IP jest ustawiony, lub użyć *nx_dhcp_state_change_notify* i zbadać stan klienta DHCP, NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ccb1f-522">Zobacz *nx_dhcp_state_change_notify* , aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="ccb1f-523">Aby znaleźć serwer DHCP w określonym interfejsie, gdy dla klienta DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-524">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-524">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-525">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ccb1f-526">**server_address** Wskaźnik na adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="ccb1f-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-527">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-527">Return Values</span></span>

- <span data-ttu-id="ccb1f-528">**NX_SUCCESS** (0x00) zwrócony adres serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="ccb1f-529">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="ccb1f-530">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-531">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-531">Allowed From</span></span>

<span data-ttu-id="ccb1f-532">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-533">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="ccb1f-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ccb1f-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="ccb1f-535">Pobierz adres IP serwera DHCP klienta DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-536">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ccb1f-537">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-537">Description</span></span>

<span data-ttu-id="ccb1f-538">Ta usługa Pobiera adres IP serwera DHCP klienta DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-539">Klient DHCP musi znajdować się w stanie związanym.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="ccb1f-540">Po uruchomieniu klienta DHCP w tym interfejsie aplikacja hosta może użyć usługi *nx_ip_status_check* do sprawdzenia, czy adres IP jest ustawiony, lub może użyć wywołania zwrotnego zmiany stanu klienta DHCP i wysłać zapytanie o stan klienta dhcp, NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ccb1f-541">Zobacz *nx_dhcp_state_change_notify* , aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-542">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-542">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-543">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ccb1f-544">**Interface_index** Indeks interfejsu w celu uzyskania adresu IP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="ccb1f-545">**server_address** Wskaźnik na adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="ccb1f-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-546">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-546">Return Values</span></span>

- <span data-ttu-id="ccb1f-547">**NX_SUCCESS** (0x00) zwrócony adres serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="ccb1f-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-549">Klient DHCP **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="ccb1f-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="ccb1f-550">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ccb1f-551">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ccb1f-552">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-553">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-553">Allowed From</span></span>

<span data-ttu-id="ccb1f-554">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-555">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="ccb1f-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="ccb1f-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="ccb1f-557">Ustaw interfejs sieciowy dla wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-559">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-559">Description</span></span>

<span data-ttu-id="ccb1f-560">Ta usługa ustawia interfejs sieciowy dla wystąpienia DHCP, aby połączyć się z serwerem DHCP w przypadku uruchamiania klienta DHCP skonfigurowanego dla jednego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="ccb1f-561">Domyślnie klient DHCP jest uruchamiany w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="ccb1f-562">Aby uruchomić protokół DHCP w usłudze dodatkowej, Użyj tej usługi, aby ustawić interfejs pomocniczy jako interfejs klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="ccb1f-563">Aplikacja musi wcześniej zarejestrować określony interfejs w wystąpieniu IP przy użyciu usługi *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="ccb1f-564">Należy zauważyć, że ta usługa jest przeznaczona dla aplikacji, które zamierzają uruchamiać klienta DHCP tylko na jednym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="ccb1f-565">Aby uruchomić protokół DHCP na wielu interfejsach, zobacz *nx_dhcp_interface_enable* , aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-566">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-566">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-567">**dhcp_ptr** Wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ccb1f-568">**indeks** Indeks interfejsu sieciowego urządzenia</span><span class="sxs-lookup"><span data-stu-id="ccb1f-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-569">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-569">Return Values</span></span>

- <span data-ttu-id="ccb1f-570">Interfejs **NX_SUCCESS** (0x00) został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="ccb1f-571">**NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="ccb1f-572">Interfejs **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) z włączonym protokołem DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) Brak dostępnego rekordu dla innego</span><span class="sxs-lookup"><span data-stu-id="ccb1f-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="ccb1f-574">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-575">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-575">Allowed From</span></span>

<span data-ttu-id="ccb1f-576">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-577">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="ccb1f-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="ccb1f-578">nx_dhcp_start</span></span>

<span data-ttu-id="ccb1f-579">Uruchamianie przetwarzania DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-580">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-581">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-581">Description</span></span>

<span data-ttu-id="ccb1f-582">Ta usługa uruchamia przetwarzanie DHCP na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-583">Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ccb1f-584">Aby sprawdzić, kiedy wystąpienie protokołu IP jest powiązane z adresem IP w interfejsie klienta DHCP, należy użyć *nx_ip_status_check* , aby sprawdzić, czy adres IP jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="ccb1f-585">Jeśli istnieją inne interfejsy, na których jest już uruchomiony protokół DHCP, ta usługa nie będzie mieć na nie wpływu.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="ccb1f-586">Aby uruchomić protokół DHCP w określonym interfejsie, jeśli włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_start* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-587">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-587">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-588">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-589">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-589">Return Values</span></span>

- <span data-ttu-id="ccb1f-590">**NX_SUCCESS** (0X00) pomyślne uruchomienie usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="ccb1f-591">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP jest już uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="ccb1f-592">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-593">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-594">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-594">Allowed From</span></span>

<span data-ttu-id="ccb1f-595">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-596">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="ccb1f-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="ccb1f-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="ccb1f-598">Uruchom przetwarzanie DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-599">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-600">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-600">Description</span></span>

<span data-ttu-id="ccb1f-601">Ta usługa uruchamia przetwarzanie DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-602">Aby uzyskać więcej informacji na temat włączania interfejsu protokołu DHCP, zobacz *nx_dhcp_interface_enable*().</span><span class="sxs-lookup"><span data-stu-id="ccb1f-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="ccb1f-603">Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="ccb1f-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ccb1f-604">Jeśli nie ma innych interfejsów z uruchomionym klientem DHCP, ta usługa uruchomi/wznowi wątek klienta DHCP i (ponownie) uaktywni czasomierz klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="ccb1f-605">Aplikacja powinna używać *nx_ip_status_check* , aby sprawdzić, czy uzyskano adres IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-606">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-606">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-607">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-608">**Interface_index** Indeks, na którym ma zostać uruchomiony klient DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-609">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-609">Return Values</span></span>

- <span data-ttu-id="ccb1f-610">**NX_SUCCESS** (0X00) pomyślne uruchomienie usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="ccb1f-611">**NX_DHCP_ALREADY_STARTED** (0x93) wystąpienie usługi DHCP zostało już uruchomione.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="ccb1f-612">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-613">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="ccb1f-614">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-615">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-615">Allowed From</span></span>

<span data-ttu-id="ccb1f-616">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-617">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="ccb1f-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ccb1f-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="ccb1f-619">Ustawianie funkcji wywołania zwrotnego zmiany stanu protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-620">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ccb1f-621">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-621">Description</span></span>

<span data-ttu-id="ccb1f-622">Ta usługa rejestruje określoną funkcję wywołania zwrotnego dhcp_state_change_notify w celu powiadomienia aplikacji o zmianach stanu protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ccb1f-623">Funkcja wywołania zwrotnego dostarcza stan, do którego przeszedł klient DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="ccb1f-624">Poniżej przedstawiono wartości skojarzone z różnymi stanami DHCP:</span><span class="sxs-lookup"><span data-stu-id="ccb1f-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="ccb1f-625">Stan</span><span class="sxs-lookup"><span data-stu-id="ccb1f-625">State</span></span>                             | <span data-ttu-id="ccb1f-626">Wartość</span><span class="sxs-lookup"><span data-stu-id="ccb1f-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="ccb1f-627">\_rozruch stanu protokołu DHCP NX \_ \_</span><span class="sxs-lookup"><span data-stu-id="ccb1f-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="ccb1f-628">1</span><span class="sxs-lookup"><span data-stu-id="ccb1f-628">1</span></span>     |
| <span data-ttu-id="ccb1f-629">\_ \_ init stanu DHCP \_ NX</span><span class="sxs-lookup"><span data-stu-id="ccb1f-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="ccb1f-630">2</span><span class="sxs-lookup"><span data-stu-id="ccb1f-630">2</span></span>     |
| <span data-ttu-id="ccb1f-631">\_wybór stanu protokołu DHCP NX \_ \_</span><span class="sxs-lookup"><span data-stu-id="ccb1f-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="ccb1f-632">3</span><span class="sxs-lookup"><span data-stu-id="ccb1f-632">3</span></span>     |
| <span data-ttu-id="ccb1f-633">\_ \_ żądanie stanu DHCP \_ NX</span><span class="sxs-lookup"><span data-stu-id="ccb1f-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="ccb1f-634">4</span><span class="sxs-lookup"><span data-stu-id="ccb1f-634">4</span></span>     |
| <span data-ttu-id="ccb1f-635">\_ \_ powiązano stan DHCP \_ NX</span><span class="sxs-lookup"><span data-stu-id="ccb1f-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="ccb1f-636">5</span><span class="sxs-lookup"><span data-stu-id="ccb1f-636">5</span></span>     |
| <span data-ttu-id="ccb1f-637">\_ \_ odnawianie stanu protokołu DHCP NX \_</span><span class="sxs-lookup"><span data-stu-id="ccb1f-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="ccb1f-638">6</span><span class="sxs-lookup"><span data-stu-id="ccb1f-638">6</span></span>     |
| <span data-ttu-id="ccb1f-639">ponowne \_ \_ wiązanie stanu \_ DHCP NX</span><span class="sxs-lookup"><span data-stu-id="ccb1f-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="ccb1f-640">7</span><span class="sxs-lookup"><span data-stu-id="ccb1f-640">7</span></span>     |
| <span data-ttu-id="ccb1f-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="ccb1f-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="ccb1f-642">8</span><span class="sxs-lookup"><span data-stu-id="ccb1f-642">8</span></span>     |
| <span data-ttu-id="ccb1f-643">\_ \_ \_ sondowanie adresu stanu protokołu DHCP NX \_</span><span class="sxs-lookup"><span data-stu-id="ccb1f-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="ccb1f-644">9</span><span class="sxs-lookup"><span data-stu-id="ccb1f-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="ccb1f-645">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-645">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-646">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-647">**dhcp_state_change_notify** Wskaźnik funkcji wywołania zwrotnego zmiany stanu</span><span class="sxs-lookup"><span data-stu-id="ccb1f-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-648">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-648">Return Values</span></span>

- <span data-ttu-id="ccb1f-649">Pomyślna konfiguracja wywołania zwrotnego **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="ccb1f-650">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-651">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-652">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-652">Allowed From</span></span>

<span data-ttu-id="ccb1f-653">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ccb1f-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-654">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="ccb1f-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ccb1f-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="ccb1f-656">Ustaw funkcję wywołania zwrotnego zmiany stanu DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-657">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ccb1f-658">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-658">Description</span></span>

<span data-ttu-id="ccb1f-659">Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu powiadomienia aplikacji o zmianach stanu protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ccb1f-660">Argumenty wejściowe ATANH wywołania zwrotnego są indeksem interfejsu i stanem, w którym klient DHCP przeszedł w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="ccb1f-661">Aby uzyskać więcej informacji na temat funkcji zmiany stanu, zobacz *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="ccb1f-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-662">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-662">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-663">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-664">**dhcp_interface_state_change_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji</span><span class="sxs-lookup"><span data-stu-id="ccb1f-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-665">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-665">Return Values</span></span>

- <span data-ttu-id="ccb1f-666">Pomyślna konfiguracja wywołania zwrotnego **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="ccb1f-667">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-668">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-668">Allowed From</span></span>

<span data-ttu-id="ccb1f-669">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ccb1f-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-670">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="ccb1f-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="ccb1f-671">nx_dhcp_stop</span></span>

<span data-ttu-id="ccb1f-672">Powoduje zatrzymanie przetwarzania protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-673">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-674">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-674">Description</span></span>

<span data-ttu-id="ccb1f-675">Ta usługa powoduje zatrzymanie przetwarzania protokołu DHCP na wszystkich interfejsach, które uruchomiły przetwarzanie DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="ccb1f-676">Jeśli nie ma żadnych interfejsów przetwarzających protokół DHCP, ta usługa zawiesza wątek klienta DHCP i dezaktywuje czasomierz klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="ccb1f-677">Aby zatrzymać usługę DHCP w określonym interfejsie, jeśli dla usługi DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_stop* .</span><span class="sxs-lookup"><span data-stu-id="ccb1f-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-678">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-678">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-679">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-680">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-680">Return Values</span></span>

- <span data-ttu-id="ccb1f-681">**NX_SUCCESS** (0X00) POMYŚLNE zatrzymanie DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="ccb1f-682">**NX_DHCP_NOT_STARTED** (0x96) wystąpienie DHCP nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="ccb1f-683">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-684">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-685">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-685">Allowed From</span></span>

<span data-ttu-id="ccb1f-686">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-687">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="ccb1f-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="ccb1f-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="ccb1f-689">Zatrzymaj przetwarzanie DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-690">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ccb1f-691">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-691">Description</span></span>

<span data-ttu-id="ccb1f-692">Ta usługa powoduje zatrzymanie przetwarzania DHCP w określonym interfejsie, jeśli usługa DHCP jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="ccb1f-693">Jeśli nie ma innych interfejsów z uruchomionym protokołem DHCP, wątek i czasomierz DHCP są wstrzymywane.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-694">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-694">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-695">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-696">**Interface_index** Interfejs, na którym ma zostać zatrzymane przetwarzanie DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-697">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-697">Return Values</span></span>

- <span data-ttu-id="ccb1f-698">**NX_SUCCESS** (0X00) POMYŚLNE zatrzymanie DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="ccb1f-699">**NX_DHCP_NOT_STARTED** (0X96) DHCP nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="ccb1f-700">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-701">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="ccb1f-702">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-703">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-703">Allowed From</span></span>

<span data-ttu-id="ccb1f-704">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-705">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="ccb1f-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ccb1f-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="ccb1f-707">Pobierz opcję DHCP z ostatniej odpowiedzi serwera</span><span class="sxs-lookup"><span data-stu-id="ccb1f-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-708">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ccb1f-709">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-709">Description</span></span>

<span data-ttu-id="ccb1f-710">Ta usługa pobiera określoną opcję DHCP z bufora opcji DHCP pierwszego interfejsu z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="ccb1f-711">Jeśli to się powiedzie, dane opcji są kopiowane do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-712">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-712">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-713">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="ccb1f-714">**request_option** Opcja DHCP określona przez specyfikacje RFC.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ccb1f-715">Zobacz opcję NX_DHCP_OPTION w *nx_dhcp. h*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="ccb1f-716">**destination_ptr** Wskaźnik do miejsca docelowego dla ciągu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="ccb1f-717">**destination_size** Wskaźnik na rozmiar lokalizacji docelowej i w przypadku powrotu, miejsce docelowe, do którego zostanie umieszczona liczba zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-718">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-718">Return Values</span></span>

- <span data-ttu-id="ccb1f-719">**NX_SUCCESS** (0x00) — pomyślne pobranie opcji.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="ccb1f-720">Klient DHCP **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="ccb1f-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ccb1f-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="ccb1f-722">Miejsce docelowe **NX_DHCP_DEST_TO_SMALL** (0x95) jest za małe, aby można było przetrzymać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="ccb1f-723">W odpowiedzi serwera nie znaleziono opcji DHCP **NX_DHCP_PARSE_ERROR** (0x97).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="ccb1f-724">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="ccb1f-725">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-726">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-726">Allowed From</span></span>

<span data-ttu-id="ccb1f-727">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-728">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="ccb1f-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ccb1f-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="ccb1f-730">Pobierz opcję DHCP z ostatniej odpowiedzi serwera w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ccb1f-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-731">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ccb1f-732">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-732">Description</span></span>

<span data-ttu-id="ccb1f-733">Ta usługa pobiera określoną opcję DHCP z bufora opcji DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ccb1f-734">Jeśli to się powiedzie, dane opcji są kopiowane do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-735">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-735">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-736">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-737">**Interface_index** Indeks, na którym ma zostać pobrana określona opcja</span><span class="sxs-lookup"><span data-stu-id="ccb1f-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="ccb1f-738">**request_option** Opcja DHCP określona przez specyfikacje RFC.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ccb1f-739">Zobacz opcję NX_DHCP_OPTION w *nx_dhcp. h*.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="ccb1f-740">**destination_ptr** Wskaźnik do miejsca docelowego dla ciągu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="ccb1f-741">**destination_size** Wskaźnik na rozmiar lokalizacji docelowej i w przypadku powrotu, miejsce docelowe, do którego zostanie umieszczona liczba zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-742">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-742">Return Values</span></span>

- <span data-ttu-id="ccb1f-743">**NX_SUCCESS** (0x00) — pomyślne pobranie opcji.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="ccb1f-744">Adres IP **NX_DHCP_NOT_BOUND** (0x94) nie jest przypisany</span><span class="sxs-lookup"><span data-stu-id="ccb1f-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="ccb1f-745">Bufor **NX_DHCP_DEST_TO_SMALL** (0x95) jest za mały</span><span class="sxs-lookup"><span data-stu-id="ccb1f-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="ccb1f-746">W odpowiedzi serwera nie znaleziono opcji DHCP **NX_DHCP_PARSE_ERROR** (0x97).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="ccb1f-747">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ccb1f-748">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="ccb1f-749">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ccb1f-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-750">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-750">Allowed From</span></span>

<span data-ttu-id="ccb1f-751">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-752">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="ccb1f-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="ccb1f-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="ccb1f-754">Konwertuj cztery bajty na ULONG</span><span class="sxs-lookup"><span data-stu-id="ccb1f-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-755">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="ccb1f-756">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-756">Description</span></span>

<span data-ttu-id="ccb1f-757">Ta usługa konwertuje cztery znaki wskazywane przez "option_string_ptr" na wartość długą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="ccb1f-758">Jest to szczególnie przydatne w przypadku obecności adresów IP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-759">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-759">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-760">**option_string_ptr** Wskaźnik do wcześniej pobranego ciągu opcji.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-761">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-761">Return Values</span></span>

- <span data-ttu-id="ccb1f-762">**Wartość** Wartość czterech pierwszych bajtów.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-763">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-763">Allowed From</span></span>

<span data-ttu-id="ccb1f-764">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-765">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="ccb1f-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="ccb1f-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="ccb1f-767">Ustaw funkcję wywołania zwrotnego w celu dodania opcji dostarczonych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="ccb1f-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="ccb1f-768">Prototype</span><span class="sxs-lookup"><span data-stu-id="ccb1f-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="ccb1f-769">Opis</span><span class="sxs-lookup"><span data-stu-id="ccb1f-769">Description</span></span>

<span data-ttu-id="ccb1f-770">Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu dodania opcji dostarczonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="ccb1f-771">Jeśli określono funkcję wywołania zwrotnego, aplikacje mogą dodać opcje dostarczone przez użytkownika do pakietu, iface_index i message_type.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="ccb1f-772">W procedurze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-772">In user’s routine.</span></span> <span data-ttu-id="ccb1f-773">W przypadku dodawania opcji dostarczonych przez użytkownika aplikacje muszą być zgodne z formatem opcji DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="ccb1f-774">Łączny rozmiar opcji użytkownika musi być mniejszy lub równy user_option_length i aktualizować user_option_length jako rzeczywistą długość opcji.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="ccb1f-775">Zwróć NX_TRUE w przypadku pomyślnego dodania opcji, w przeciwnym razie Zwróć NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ccb1f-776">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ccb1f-776">Input Parameters</span></span>

- <span data-ttu-id="ccb1f-777">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ccb1f-778">**dhcp_user_option_add** Wskaźnik do opcji użytkownika Dodaj funkcję.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ccb1f-779">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ccb1f-779">Return Values</span></span>

- <span data-ttu-id="ccb1f-780">Pomyślna konfiguracja wywołania zwrotnego **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="ccb1f-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="ccb1f-781">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ccb1f-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ccb1f-782">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ccb1f-782">Allowed From</span></span>

<span data-ttu-id="ccb1f-783">Wątki</span><span class="sxs-lookup"><span data-stu-id="ccb1f-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ccb1f-784">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb1f-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
