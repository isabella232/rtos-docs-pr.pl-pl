---
title: Rozdział 3 — Opis usług klienta DHCP w systemie Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług klienta DHCP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822021"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="ab9a6-103">Rozdział 3 — Opis usług klienta DHCP w systemie Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ab9a6-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="ab9a6-104">Ten rozdział zawiera opis wszystkich usług klienta DHCP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ab9a6-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ab9a6-106">**nx_dhcp_create**: *Tworzenie wystąpienia DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="ab9a6-107">**nx_dhcp_clear_broadcast_flag**: *Wyczyść flagę emisji na komunikatach klienta*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="ab9a6-108">**nx_dhcp_delete**: *usuwanie wystąpienia DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="ab9a6-109">**nx_dhcp_force_renew**: *Wyślij komunikat o wymuszeniu odnowienia*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="ab9a6-110">**nx_dhcp_packet_pool_set**: *Ustaw pulę pakietów klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="ab9a6-111">**nx_dhcp_decline**: Wyślij *komunikat odrzucania do serwera*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="ab9a6-112">**nx_dhcp_release**: Wyślij *komunikat o zwolnieniu do serwera*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="ab9a6-113">**nx_dhcp_reinitialize**: *Wyczyść parametry sieciowe klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="ab9a6-114">**nx_dhcp_request_client_ip**: *Określ konkretny adres IP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="ab9a6-115">**nx_dhcp_send_request**: *Wyślij komunikat DHCP do serwera*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="ab9a6-116">**nx_dhcp_start**: *Uruchamianie przetwarzania klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="ab9a6-117">**nx_dhcp_stop**: *Zatrzymywanie przetwarzania klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="ab9a6-118">**nx_dhcp_set_interface_index**: *Ustaw interfejs do uruchamiania klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="ab9a6-119">**nx_dhcp_server_address_get**: *Pobierz adres IP serwera DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="ab9a6-120">**nx_dhcp_state_change_notify**: *Ustaw funkcję wywołania zwrotnego w przypadku zmiany stanu DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="ab9a6-121">**nx_dhcp_user_option_retrieve**: *Pobierz określoną opcję DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="ab9a6-122">**nx_dhcp_user_option_convert**: *przekonwertuj cztery BAJTy na ULONG*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="ab9a6-123">Usługi klienta DHCP specyficzne dla interfejsu:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="ab9a6-124">**nx_dhcp_interface_clear_broadcast_flag**: *Wyczyść flagę emisji na komunikatach klienta w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="ab9a6-125">**nx_dhcp_interface_enable**: *Włącz interfejs do uruchamiania protokołu DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-126">**nx_dhcp_interface_disable**: *Wyłącz interfejs do uruchamiania protokołu DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-127">**nx_dhcp_interface_decline**: *Wyślij komunikat odrzucania do serwera w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-128">**nx_dhcp_interface_force_renew**: *Wyślij komunikat wymuszania odnowienia w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-129">**nx_dhcp_interface_reinitialize**: *Wyczyść parametry sieciowe klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-130">**nx_dhcp_interface_release**: *wysyła komunikat o zwolnieniu do serwera w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-131">**nx_dhcp_interface_request_client_ip**: *Określ konkretny adres IP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-132">**nx_dhcp_interface_send_request**: *Wyślij komunikat DHCP do serwera w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-133">**nx_dhcp_interface_server_address_get**: *Pobierz adres IP serwera DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-134">**nx_dhcp_interface_start**: *Uruchamianie przetwarzania klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-135">**nx_dhcp_interface_stop**: *Zatrzymywanie przetwarzania klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-136">**nx_dhcp_interface_state_change_notify**: *Ustaw funkcję wywołania zwrotnego, gdy stan DHCP zostanie zmieniony w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-137">**nx_dhcp_interface_user_option_retrieve**: *Pobierz określoną opcję DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="ab9a6-138">Usługi klienta DHCP, jeśli NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ab9a6-139">**nx_dhcp_resume**: *Wznów poprzednio ustanowiony stan klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="ab9a6-140">**nx_dhcp_suspend**: *wstrzymywanie przetwarzania stanu klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="ab9a6-141">**nx_dhcp_client_get_record**: *Utwórz rekord stanu klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="ab9a6-142">**nx_dhcp_client_restore_record**: *przywracanie wcześniej zapisanego rekordu do klienta DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="ab9a6-143">**nx_dhcp_client_update_time_remaining**: *zaktualizuj pozostały czas w bieżącym stanie DHCP*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="ab9a6-144">Specyficzne dla interfejsu usługi klienta DHCP, jeśli NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ab9a6-145">**nx_dhcp_client_interface_get_record**: *Utwórz rekord stanu klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-146">**nx_dhcp_client_interface_restore_record**: *przywracanie wcześniej zapisanego rekordu do klienta DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="ab9a6-147">**nx_dhcp_client_interface_update_time_remaining**: *zaktualizuj pozostały czas w bieżącym stanie DHCP w określonym interfejsie*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="ab9a6-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="ab9a6-148">nx_dhcp_create</span></span>

<span data-ttu-id="ab9a6-149">Tworzenie wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-151">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-151">Description</span></span>

<span data-ttu-id="ab9a6-152">Ta usługa tworzy wystąpienie DHCP dla utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="ab9a6-153">Domyślnie interfejs podstawowy jest włączony do uruchamiania protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="ab9a6-154">Nazwy wejściowe, które nie są używane w implementacji NetX Duo klienta DHCP, muszą być zgodne z kryteriami RFC 1035 dla nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="ab9a6-155">Łączna długość nie może przekraczać 255 znaków, etykiety oddzielone kropkami muszą zaczynać się literą i kończyć literą lub cyfrą i mogą zawierać łączniki, ale nie inny znak inny niż alfanumeryczny.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="ab9a6-156">Jeśli aplikacja ma uruchamiać inne interfejsy zarejestrowane przy użyciu wystąpienia protokołu IP (przy użyciu *nx_ip_interface_attach*), aplikacja może wywoływać *nx_dhcp_set_interface_index* , aby uruchomić usługę DHCP tylko na tym interfejsie, lub *nx_dhcp_interface_enable* do uruchamiania protokołu DHCP również w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="ab9a6-157">Aby uzyskać więcej informacji, zobacz opis tych usług.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="ab9a6-158">Aplikacja musi upewnić się, że ładunek puli pakietów klienta DHCP może obsługiwać minimalny rozmiar komunikatu DHCP określony w sekcji RFC 2131 (548 bajtów danych komunikatów DHCP oraz nagłówków protokołu UDP, adresu IP i ramki sieci fizycznej).</span><span class="sxs-lookup"><span data-stu-id="ab9a6-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-159">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-159">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-160">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="ab9a6-161">**ip_ptr**: wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="ab9a6-162">**name_ptr**: wskaźnik do nazwy hosta dla wystąpienia usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-163">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-163">Return Values</span></span>

- <span data-ttu-id="ab9a6-164">**NX_SUCCESS**: (0X00) POMYŚLNE utworzenie DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="ab9a6-165">**NX_DHCP_INVALID_NAME**: (0XA8) Nieprawidłowa nazwa hosta</span><span class="sxs-lookup"><span data-stu-id="ab9a6-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="ab9a6-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) jest za mały dla komunikatu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="ab9a6-167">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-168">Allowed From</span></span>

<span data-ttu-id="ab9a6-169">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="ab9a6-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="ab9a6-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="ab9a6-172">Włącz określony interfejs do uruchamiania protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ab9a6-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-174">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-174">Description</span></span>

<span data-ttu-id="ab9a6-175">Ta usługa umożliwia określony interfejs do uruchamiania protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="ab9a6-176">Domyślnie interfejs podstawowy jest włączony dla klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="ab9a6-177">W tym momencie można uruchomić protokół DHCP w tym interfejsie przez wywołanie *nx_dhcp_interface_start* lub uruchomienie protokołu DHCP we wszystkich włączonych interfejsach *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="ab9a6-178">Aplikacja musi najpierw zarejestrować ten interfejs z wystąpieniem IP przy użyciu *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="ab9a6-179">Ponadto w celu dodania tego interfejsu do listy włączonych interfejsów musi istnieć dostępny interfejs klienta DHCP "rekord".</span><span class="sxs-lookup"><span data-stu-id="ab9a6-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="ab9a6-180">Domyślnie NX_DHCP_CLIENT_MAX_RECORDS jest zdefiniowana na 1.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="ab9a6-181">Ustaw tę opcję na maksymalną liczbę interfejsów oczekiwanych na równoczesne uruchomienie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="ab9a6-182">Zwykle NX_DHCP_CLIENT_MAX_RECORDS będzie równa NX_MAX_PHYSICAL_INTERFACES; Jeśli jednak urządzenie ma więcej interfejsów fizycznych niż oczekuje na uruchomienie klienta DHCP, może zaoszczędzić pamięć przez ustawienie NX_DHCP_CLIENT_MAX_RECORDS na mniejszą niż ten numer.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="ab9a6-183">Nie istnieje jeden do jednego mapowanie interfejsów fizycznych z rekordami interfejsu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="ab9a6-184">Różnica między tą usługą a *nx_dhcp_set_interface_index* to ta, która powoduje, że tylko jeden interfejs do uruchamiania protokołu DHCP, podczas gdy ta usługa po prostu dodaje określony interfejs do listy interfejsów klienta włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ab9a6-185">Aby wyłączyć interfejs dla protokołu DHCP, aplikacja może wywołać</span><span class="sxs-lookup"><span data-stu-id="ab9a6-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="ab9a6-186">Usługa *nx_dhcp_interface_disable* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-187">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-187">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-188">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ab9a6-189">**interface_index**: indeks interfejsu umożliwiającego włączenie protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-190">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-190">Return Values</span></span>

- <span data-ttu-id="ab9a6-191">**NX_SUCCESS**: (0X00) pomyślne włączenie protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="ab9a6-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0XA7) Brak dostępnego rekordu dla innego interfejsu, który ma zostać włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) włączono interfejs dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-194">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-195">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-196">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-196">Allowed From</span></span>

<span data-ttu-id="ab9a6-197">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-198">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="ab9a6-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="ab9a6-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="ab9a6-200">Wyłączenie określonego interfejsu w celu uruchomienia protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ab9a6-201">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-202">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-202">Description</span></span>

<span data-ttu-id="ab9a6-203">Ta usługa wyłącza określony interfejs na potrzeby uruchamiania protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="ab9a6-204">Ponownie inicjuje klienta DHCP w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="ab9a6-205">Aby ponownie uruchomić klienta DHCP, aplikacja musi ponownie włączyć interfejs przy użyciu *nx_dhcp_interface_enable* i ponownie uruchomić usługę DHCP, wywołując *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-206">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-206">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-207">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ab9a6-208">**interface_index**: indeks interfejsu, na którym ma zostać wyłączona usługa DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-209">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-209">Return Values</span></span>

- <span data-ttu-id="ab9a6-210">**NX_SUCCESS**: (0X00) POMYŚLNE utworzenie DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="ab9a6-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-212">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-213">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ab9a6-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ab9a6-214">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-215">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-215">Allowed From</span></span>

<span data-ttu-id="ab9a6-216">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-217">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="ab9a6-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ab9a6-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="ab9a6-219">Ustaw flagę emisji DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-220">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ab9a6-221">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-221">Description</span></span>

<span data-ttu-id="ab9a6-222">Ta usługa ustawia lub czyści flagę emisji w nagłówku komunikatu DHCP dla wszystkich interfejsów włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-223">W przypadku niektórych komunikatów DHCP (np. DISCOVER) flaga emisji jest ustawiona na emisję, ponieważ klient nie ma adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="ab9a6-224">wartości clear_flag:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-224">clear_flag values:</span></span> 

- <span data-ttu-id="ab9a6-225">**NX_TRUE**: Flaga emisji została wyczyszczona (Żądaj odpowiedzi emisji pojedynczej)</span><span class="sxs-lookup"><span data-stu-id="ab9a6-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="ab9a6-226">**NX_FALSE**: ustawiono flagę emisji (odpowiedź na żądanie emisji)</span><span class="sxs-lookup"><span data-stu-id="ab9a6-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="ab9a6-227">Ta usługa jest przeznaczona dla klientów DHCP, którzy muszą przejść przez router, aby uzyskać dostęp do serwera DHCP, gdzie router odrzuca komunikaty emisji przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-228">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-228">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-229">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="ab9a6-230">**clear_flag**: wartość, do której ma zostać ustawiona flaga emisji</span><span class="sxs-lookup"><span data-stu-id="ab9a6-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-231">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-231">Return Values</span></span>

- <span data-ttu-id="ab9a6-232">**NX_SUCCESS**: (0X00) pomyślnie ustawiono flagę</span><span class="sxs-lookup"><span data-stu-id="ab9a6-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="ab9a6-233">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-234">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-234">Allowed From</span></span>

<span data-ttu-id="ab9a6-235">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-236">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="ab9a6-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ab9a6-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="ab9a6-238">Ustaw lub wyczyść flagę emisji w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-239">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ab9a6-240">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-240">Description</span></span>

<span data-ttu-id="ab9a6-241">Ta usługa umożliwia aplikacji hosta klienta DHCP Ustawianie lub czyszczenie flagi emisji w komunikatach klienta DHCP na serwerze DHCP w określonym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="ab9a6-242">Aby uzyskać więcej informacji, zobacz **nx_dhcp_clear_broadcast_flag**.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-243">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-243">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-244">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="ab9a6-245">**interface_index**: indeks interfejsu służący do ustawiania flagi emisji</span><span class="sxs-lookup"><span data-stu-id="ab9a6-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="ab9a6-246">**clear_flag**: wartość, do której ma zostać ustawiona flaga emisji</span><span class="sxs-lookup"><span data-stu-id="ab9a6-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-247">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-247">Return Values</span></span>

- <span data-ttu-id="ab9a6-248">**NX_SUCCESS**: (0X00) pomyślnie ustawiono flagę</span><span class="sxs-lookup"><span data-stu-id="ab9a6-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="ab9a6-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-250">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-251">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-252">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-252">Allowed From</span></span>

<span data-ttu-id="ab9a6-253">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-254">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="ab9a6-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="ab9a6-255">nx_dhcp_delete</span></span>

<span data-ttu-id="ab9a6-256">Usuwanie wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-257">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-258">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-258">Description</span></span>

<span data-ttu-id="ab9a6-259">Ta usługa usuwa wcześniej utworzone wystąpienie usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-260">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-260">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-261">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-262">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-262">Return Values</span></span>

- <span data-ttu-id="ab9a6-263">**NX_SUCCESS**: (0X00) pomyślne usunięcie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="ab9a6-264">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-265">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-266">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-266">Allowed From</span></span>

<span data-ttu-id="ab9a6-267">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-268">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="ab9a6-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="ab9a6-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="ab9a6-270">Wyślij komunikat Force o odnowieniu</span><span class="sxs-lookup"><span data-stu-id="ab9a6-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="ab9a6-271">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-272">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-272">Description</span></span>

<span data-ttu-id="ab9a6-273">Ta usługa umożliwia aplikacji hosta wysyłanie komunikatów Force w celu odnowienia na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-274">Klient DHCP musi być w stanie powiązanym.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="ab9a6-275">Ta funkcja ustawia stan do ODNOWIENIa, aby klient DHCP próbował odnowić działanie przed upływem limitu czasu T1.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="ab9a6-276">Aby wysłać Force w określonym interfejsie, gdy jest włączona obsługa protokołu DHCP w wielu interfejsach, użyj *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-277">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-277">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-278">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-279">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-279">Return Values</span></span>

- <span data-ttu-id="ab9a6-280">**NX_SUCCESS**: (0X00) pomyślnie wysłano wymuszenie odnowienia.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="ab9a6-281">**NX_DHCP_NOT_BOUND**: (0x94) adres IP klienta nie jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="ab9a6-282">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-283">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-284">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-284">Allowed From</span></span>

<span data-ttu-id="ab9a6-285">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-286">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="ab9a6-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="ab9a6-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="ab9a6-288">Wyślij komunikat Wymuś odnowienie w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-290">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-290">Description</span></span>

<span data-ttu-id="ab9a6-291">Ta usługa umożliwia aplikacji hosta wysyłanie komunikatów Force (Wymuś odnowienie) w interfejsie wejściowym, o ile ten interfejs został włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ab9a6-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ab9a6-292">Klient DHCP w określonym interfejsie musi być w stanie powiązanym.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="ab9a6-293">Ta funkcja ustawia stan do ODNOWIENIa, aby klient DHCP próbował odnowić działanie przed upływem limitu czasu T1.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-294">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-294">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-295">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-296">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-296">Return Values</span></span>

- <span data-ttu-id="ab9a6-297">**NX_SUCCESS**: (0X00) pomyślnie wysłano wymuszenie odnowienia.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="ab9a6-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-299">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-300">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-301">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-301">Allowed From</span></span>

<span data-ttu-id="ab9a6-302">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-303">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="ab9a6-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="ab9a6-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="ab9a6-305">Ustawianie puli pakietów klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-307">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-307">Description</span></span>

<span data-ttu-id="ab9a6-308">Ta usługa umożliwia aplikacji utworzenie puli pakietów klienta DHCP, przekazując wskaźnik do wcześniej utworzonej puli pakietów w ramach tego wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="ab9a6-309">Aby można było użyć tej funkcji, aplikacja hosta musi definiować NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="ab9a6-310">Po zdefiniowaniu usługa *nx_dhcp_create* nie utworzy puli pakietów klienta.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="ab9a6-311">Aplikacja jest zalecana do używania wartości domyślnych dla ładunku puli pakietów klienta DHCP zdefiniowanego jako NX_DHCP_PACKET_PAYLOAD w *nxd_dhcp_client. h* podczas tworzenia puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-312">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-312">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-313">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ab9a6-314">**packet_pool_ptr**: wskaźnik do wcześniej utworzonej puli pakietów</span><span class="sxs-lookup"><span data-stu-id="ab9a6-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-315">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-315">Return Values</span></span>

- <span data-ttu-id="ab9a6-316">**NX_SUCCESS**: (0x00) Pula pakietów klienta DHCP jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="ab9a6-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="ab9a6-317">**NX_NOT_ENABLED**: usługa (0x14) nie jest włączona</span><span class="sxs-lookup"><span data-stu-id="ab9a6-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="ab9a6-318">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-319">Ładunek NX_DHCP_INVALID_PAYLOAD: (0x9C) jest za mały</span><span class="sxs-lookup"><span data-stu-id="ab9a6-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-320">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-320">Allowed From</span></span>

<span data-ttu-id="ab9a6-321">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab9a6-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-322">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="ab9a6-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ab9a6-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="ab9a6-324">Ustaw żądany adres IP dla wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-325">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ab9a6-326">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-326">Description</span></span>

<span data-ttu-id="ab9a6-327">Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP przy pierwszym interfejsie włączonym dla protokołu DHCP w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="ab9a6-328">Jeśli flaga *skip_discover_message* jest ustawiona, klient DHCP pomija komunikat odnajdywania i wysyła komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="ab9a6-329">Aby ustawić żądanie dla określonego adresu IP dla komunikatów DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_request_client_ip* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-330">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-330">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-331">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ab9a6-332">**client_ip_address**: adres IP do żądania z serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="ab9a6-333">**skip_discover_message**:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="ab9a6-334">W przypadku wartości true klient DHCP wysyła komunikat żądania</span><span class="sxs-lookup"><span data-stu-id="ab9a6-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="ab9a6-335">W przypadku wartości false wysyła komunikat odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-336">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-336">Return Values</span></span>

- <span data-ttu-id="ab9a6-337">**NX_SUCCESS**: (0X00) żądany adres IP jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="ab9a6-338">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) żądanie ZEROWEgo adresu IP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-340">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-340">Allowed From</span></span>

<span data-ttu-id="ab9a6-341">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-342">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="ab9a6-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ab9a6-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="ab9a6-344">Ustaw żądany adres IP dla wystąpienia DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-345">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ab9a6-346">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-346">Description</span></span>

<span data-ttu-id="ab9a6-347">Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ab9a6-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ab9a6-348">Jeśli flaga *skip_discover_message* jest ustawiona, klient DHCP pomija komunikat odnajdywania i wysyła komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-349">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-349">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-350">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ab9a6-351">**Interface_index**: indeks interfejsu do żądania adresu IP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="ab9a6-352">**client_ip_address**: adres IP do żądania z serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="ab9a6-353">**skip_discover_message**: w przypadku wartości true klient DHCP wysyła komunikat żądania; w przeciwnym razie zostanie wysłany komunikat odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-354">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-354">Return Values</span></span>

- <span data-ttu-id="ab9a6-355">**NX_SUCCESS**: (0X00) żądany adres IP jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="ab9a6-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-357">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-358">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-359">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-359">Allowed From</span></span>

<span data-ttu-id="ab9a6-360">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-361">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="ab9a6-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ab9a6-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="ab9a6-363">Wyczyść parametry sieci klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="ab9a6-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-365">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-365">Description</span></span>

<span data-ttu-id="ab9a6-366">Ta usługa czyści parametry sieciowe aplikacji hosta (adres IP, adres sieciowy i maska sieci), a następnie czyści stan klienta DHCP we wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-367">Jest on używany w połączeniu z *nx_dhcp_stop* i *nx_dhcp_start* do "ponownego uruchomienia" komputera stanu DHCP:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="ab9a6-368">Aby ponownie zainicjować klienta DHCP w określonym interfejsie, gdy na serwerze DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_reinitialize* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-369">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-369">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-370">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-371">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-371">Return Values</span></span>

- <span data-ttu-id="ab9a6-372">**NX_SUCCESS**: (0x00) pomyślnie zainicjowano serwer DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="ab9a6-373">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-374">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-374">Allowed From</span></span>

<span data-ttu-id="ab9a6-375">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-376">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="ab9a6-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ab9a6-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="ab9a6-378">Wyczyść parametry sieciowe klienta DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="ab9a6-379">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-380">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-380">Description</span></span>

<span data-ttu-id="ab9a6-381">Ta usługa czyści parametry sieci (adres IP, adres sieciowy i maska sieci) w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ab9a6-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ab9a6-382">Aby uzyskać więcej informacji, zobacz *nx_dhcp_reinitialize* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-383">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-383">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-384">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia usługi DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="ab9a6-385">**interface_index**: indeks interfejsu do ponownego zainicjowania</span><span class="sxs-lookup"><span data-stu-id="ab9a6-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-386">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-386">Return Values</span></span>

- <span data-ttu-id="ab9a6-387">**NX_SUCCESS**: (0X00) interfejs został pomyślnie zainicjowany ponownie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="ab9a6-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-389">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-390">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab9a6-391">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-392">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-392">Allowed From</span></span>

<span data-ttu-id="ab9a6-393">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-394">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="ab9a6-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="ab9a6-395">nx_dhcp_release</span></span>

<span data-ttu-id="ab9a6-396">Zwolnij adres IP dzierżawy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-397">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-398">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-398">Description</span></span>

<span data-ttu-id="ab9a6-399">Ta usługa zwalnia adres IP uzyskany z serwera DHCP, wysyłając do niego komunikat o wersji.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="ab9a6-400">Następnie ponownie inicjuje klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="ab9a6-401">Ta usługa jest stosowana do wszystkich interfejsów włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ab9a6-402">Aplikacja może ponownie uruchomić klienta DHCP, wywołując *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="ab9a6-403">Aby zwolnić adres z powrotem do serwera DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_release*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-404">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-404">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-405">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-406">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-406">Return Values</span></span>

- <span data-ttu-id="ab9a6-407">**NX_SUCCESS**: (0X00) pomyślne wydanie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="ab9a6-408">**NX_DHCP_NOT_BOUND**: (0x94) adres IP nie został wydzierżawiony, dlatego nie można go zwolnić.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="ab9a6-409">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-410">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-411">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-411">Allowed From</span></span>

<span data-ttu-id="ab9a6-412">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-413">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="ab9a6-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="ab9a6-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="ab9a6-415">Zwolnij adres IP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-416">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-417">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-417">Description</span></span>

<span data-ttu-id="ab9a6-418">Ta usługa zwalnia adres IP uzyskany z serwera DHCP w określonym interfejsie i ponownie inicjuje klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="ab9a6-419">Klienta DHCP można uruchomić ponownie, wywołując *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-420">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-420">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-421">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-422">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-422">Return Values</span></span>

- <span data-ttu-id="ab9a6-423">**NX_SUCCESS**: (0X00) pomyślne wydanie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="ab9a6-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-425">**NX_DHCP_NOT_BOUND**: (0x94) adres IP nie został wydzierżawiony, dlatego nie można go zwolnić.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="ab9a6-426">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-427">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab9a6-428">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-429">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-429">Allowed From</span></span>

<span data-ttu-id="ab9a6-430">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-431">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="ab9a6-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="ab9a6-432">nx_dhcp_decline</span></span>

<span data-ttu-id="ab9a6-433">Odrzuć adres IP z serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-434">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-435">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-435">Description</span></span>

<span data-ttu-id="ab9a6-436">Ta usługa odrzuca adres IP dzierżawiony z serwera DHCP na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-437">W przypadku zdefiniowania NX_DHCP_CLIENT_ SEND_ ARP_PROBE klient DHCP wyśle komunikat o ODRZUCENIu, jeśli wykryje, że adres IP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="ab9a6-438">Zobacz **sondy protokołu ARP** w rozdziale 1, aby uzyskać więcej informacji na temat konfiguracji sondowania ARP w kliencie DHCP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="ab9a6-439">Aplikacja może korzystać z tej usługi, aby odrzucić swój adres IP, jeśli odnajdzie adres jest używany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="ab9a6-440">Ta usługa ponownie inicjalizuje klienta DHCP, aby mógł on zostać oduruchamiany przez wywołanie *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-441">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-441">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-442">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-443">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-443">Return Values</span></span>

- <span data-ttu-id="ab9a6-444">**NX_SUCCESS**: (0x00) odrzucanie zostało pomyślnie wysłane</span><span class="sxs-lookup"><span data-stu-id="ab9a6-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="ab9a6-445">**NX_DHCP_NOT_BOUND**: (0X94) klient DHCP nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="ab9a6-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="ab9a6-446">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-447">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ab9a6-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-448">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-448">Allowed From</span></span>

<span data-ttu-id="ab9a6-449">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-450">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="ab9a6-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="ab9a6-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="ab9a6-452">Odrzuć adres IP z serwera DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-453">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-454">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-454">Description</span></span>

<span data-ttu-id="ab9a6-455">Ta usługa wysyła do serwera komunikat o ODRZUCENIu, aby odrzucić adres IP przypisany przez serwer DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="ab9a6-456">Powoduje również ponowne zainicjowanie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="ab9a6-457">Aby uzyskać więcej informacji, zobacz *nx_dhcp_decline* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-458">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-458">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-459">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-460">**Interface_index**: indeks interfejsu do odrzucania adresu IP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-461">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-461">Return Values</span></span>

- <span data-ttu-id="ab9a6-462">**NX_SUCCESS**: (0x00) wysłany komunikat o ODRZUCENIu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="ab9a6-463">**NX_DHCP_NOT_BOUND**: (0X94) klient DHCP nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="ab9a6-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="ab9a6-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-465">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-466">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab9a6-467">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-468">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-468">Allowed From</span></span>

<span data-ttu-id="ab9a6-469">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-470">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="ab9a6-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="ab9a6-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="ab9a6-472">Wyślij komunikat DHCP do serwera</span><span class="sxs-lookup"><span data-stu-id="ab9a6-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-473">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="ab9a6-474">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-474">Description</span></span>

<span data-ttu-id="ab9a6-475">Ta usługa wysyła określony komunikat DHCP do serwera DHCP przy pierwszym interfejsie z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ab9a6-476">Aby wysłać wiadomość wydania lub odrzucić, aplikacja musi odpowiednio używać *nx_dhcp [_interface] _release*() lub *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ab9a6-477">Aby można było używać tej usługi, należy uruchomić klienta DHCP, z wyjątkiem wysyłania komunikatu INFORM_REQUEST typu.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="ab9a6-478">Ta usługa nie jest przeznaczona dla aplikacji hosta na dysk, na którym znajduje się komputer stanu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-479">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-479">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-480">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ab9a6-481">**dhcp_message_type**: żądanie komunikatu (zdefiniowane w *nxd_dhcp_client. h*)</span><span class="sxs-lookup"><span data-stu-id="ab9a6-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-482">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-482">Return Values</span></span>

- <span data-ttu-id="ab9a6-483">**NX_SUCCESS**: (0x00) wysłano komunikat DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="ab9a6-484">**NX_DHCP_NOT_STARTED**: (0X96) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="ab9a6-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="ab9a6-485">**NX_DHCP_INVALID_MESSAGE**: (0X9B) Nieprawidłowy typ komunikatu do wysłania</span><span class="sxs-lookup"><span data-stu-id="ab9a6-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="ab9a6-486">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ab9a6-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-487">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-487">Allowed From</span></span>

<span data-ttu-id="ab9a6-488">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-489">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="ab9a6-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="ab9a6-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="ab9a6-491">Wyślij komunikat DHCP do serwera w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-492">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="ab9a6-493">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-493">Description</span></span>

<span data-ttu-id="ab9a6-494">Ta usługa wysyła komunikat do serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-495">Aby wysłać wiadomość wydania lub odrzucić, aplikacja musi odpowiednio używać *nx_dhcp [_interface] _release*() lub *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ab9a6-496">Aby korzystać z tej usługi, należy uruchomić klienta DHCP, z wyjątkiem wysyłania komunikatu żądania INFORM protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="ab9a6-497">Ta usługa nie jest przeznaczona dla aplikacji hosta na dysk, na którym znajduje się komputer stanu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-498">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-498">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-499">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ab9a6-500">**Interface_index**: indeks interfejsu, na którym ma zostać wysłany komunikat</span><span class="sxs-lookup"><span data-stu-id="ab9a6-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="ab9a6-501">**dhcp_message_type**: żądanie komunikatu (zdefiniowane w nxd_dhcp_client. h)</span><span class="sxs-lookup"><span data-stu-id="ab9a6-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-502">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-502">Return Values</span></span>

- <span data-ttu-id="ab9a6-503">**NX_SUCCESS**: (0x00) wysłano komunikat DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="ab9a6-504">**NX_DHCP_NOT_STARTED**: (0X96) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="ab9a6-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="ab9a6-505">**NX_DHCP_INVALID_MESSAGE**: (0X9B) Nieprawidłowy typ komunikatu do wysłania</span><span class="sxs-lookup"><span data-stu-id="ab9a6-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="ab9a6-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: interfejs (0xA4) nie jest włączony dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-507">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-508">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab9a6-509">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-510">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-510">Allowed From</span></span>

<span data-ttu-id="ab9a6-511">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-512">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="ab9a6-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ab9a6-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="ab9a6-514">Pobierz adres IP serwera DHCP klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-515">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ab9a6-516">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-516">Description</span></span>

<span data-ttu-id="ab9a6-517">Ta usługa Pobiera adres IP serwera DHCP klienta DHCP na pierwszym interfejsie z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ab9a6-518">Obiekt wywołujący może korzystać tylko z tej usługi po powiązaniu klienta DHCP z adresem IP przydzielonym przez serwer DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="ab9a6-519">Aplikacja hosta może użyć usługi *nx_ip_status_check* , aby sprawdzić, czy adres IP jest ustawiony, lub użyć *_dhcp_state_change_notify* NX i zbadać stan klienta DHCP, NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ab9a6-520">Zobacz *nx_dhcp_state_change_notify* , aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="ab9a6-521">Aby znaleźć serwer DHCP w określonym interfejsie, gdy dla klienta DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-522">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-522">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-523">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ab9a6-524">**server_address**: wskaźnik do adresu IP serwera</span><span class="sxs-lookup"><span data-stu-id="ab9a6-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-525">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-525">Return Values</span></span>

- <span data-ttu-id="ab9a6-526">**NX_SUCCESS**: (0x00) zwrócony adres serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="ab9a6-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-528">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="ab9a6-529">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-530">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-530">Allowed From</span></span>

<span data-ttu-id="ab9a6-531">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-532">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="ab9a6-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ab9a6-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="ab9a6-534">Pobierz adres IP serwera DHCP klienta DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-535">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ab9a6-536">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-536">Description</span></span>

<span data-ttu-id="ab9a6-537">Ta usługa Pobiera adres IP serwera DHCP klienta DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-538">Klient DHCP musi znajdować się w stanie związanym.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="ab9a6-539">Po uruchomieniu klienta DHCP w tym interfejsie aplikacja hosta może użyć usługi *nx_ip_status_check* do sprawdzenia, czy adres IP jest ustawiony, lub może użyć wywołania zwrotnego zmiany stanu klienta DHCP i wysłać zapytanie o stan klienta dhcp, NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ab9a6-540">Zobacz *nx_dhcp_state_change_notify* , aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-541">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-541">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-542">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ab9a6-543">**Interface_index**: indeks interfejsu w celu uzyskania adresu IP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="ab9a6-544">**server_address**: wskaźnik do adresu IP serwera</span><span class="sxs-lookup"><span data-stu-id="ab9a6-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-545">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-545">Return Values</span></span>

- <span data-ttu-id="ab9a6-546">**NX_SUCCESS**: (0x00) zwrócony adres serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="ab9a6-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-548">**NX_DHCP_NOT_BOUND**: (0X94) klient DHCP nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="ab9a6-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="ab9a6-549">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ab9a6-550">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab9a6-551">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-552">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-552">Allowed From</span></span>

<span data-ttu-id="ab9a6-553">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-554">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="ab9a6-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="ab9a6-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="ab9a6-556">Ustaw interfejs sieciowy dla wystąpienia DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-557">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-558">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-558">Description</span></span>

<span data-ttu-id="ab9a6-559">Ta usługa ustawia interfejs sieciowy dla wystąpienia DHCP, aby połączyć się z serwerem DHCP w przypadku uruchamiania klienta DHCP skonfigurowanego dla jednego interfejsu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="ab9a6-560">Domyślnie klient DHCP jest uruchamiany w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="ab9a6-561">Aby uruchomić protokół DHCP w usłudze dodatkowej, Użyj tej usługi, aby ustawić interfejs pomocniczy jako interfejs klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="ab9a6-562">Aplikacja musi wcześniej zarejestrować określony interfejs w wystąpieniu IP przy użyciu usługi *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="ab9a6-563">Ta usługa jest przeznaczona dla aplikacji, które zamierzają uruchamiać klienta DHCP tylko na jednym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="ab9a6-564">Aby uruchomić protokół DHCP na wielu interfejsach, zobacz *nx_dhcp_interface_enable* , aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-565">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-565">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-566">**dhcp_ptr**: wskaźnik do bloku sterowania DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ab9a6-567">**indeks**: indeks interfejsu sieciowego urządzenia</span><span class="sxs-lookup"><span data-stu-id="ab9a6-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-568">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-568">Return Values</span></span>

- <span data-ttu-id="ab9a6-569">**NX_SUCCESS**: (0X00) interfejs został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="ab9a6-570">**NX_INVALID_INTERFACE**: (0X4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="ab9a6-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) włączono interfejs dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0XA7) Brak dostępnego rekordu dla innego</span><span class="sxs-lookup"><span data-stu-id="ab9a6-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="ab9a6-573">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-574">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-574">Allowed From</span></span>

<span data-ttu-id="ab9a6-575">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-576">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="ab9a6-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="ab9a6-577">nx_dhcp_start</span></span>

<span data-ttu-id="ab9a6-578">Uruchamianie przetwarzania DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-579">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-580">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-580">Description</span></span>

<span data-ttu-id="ab9a6-581">Ta usługa uruchamia przetwarzanie DHCP na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-582">Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ab9a6-583">Aby sprawdzić, kiedy wystąpienie protokołu IP jest powiązane z adresem IP w interfejsie klienta DHCP, należy użyć *nx_ip_status_check* , aby sprawdzić, czy adres IP jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="ab9a6-584">Jeśli istnieją inne interfejsy, na których jest już uruchomiony protokół DHCP, ta usługa nie będzie mieć na nie wpływu.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="ab9a6-585">Aby uruchomić protokół DHCP w określonym interfejsie, jeśli włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_start* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-586">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-586">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-587">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-588">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-588">Return Values</span></span>

- <span data-ttu-id="ab9a6-589">**NX_SUCCESS**: (0X00) pomyślne uruchomienie usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="ab9a6-590">**NX_DHCP_ALREADY_STARTED**: (0X93) usługa DHCP jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ab9a6-591">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-592">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-593">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-593">Allowed From</span></span>

<span data-ttu-id="ab9a6-594">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-595">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="ab9a6-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="ab9a6-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="ab9a6-597">Uruchom przetwarzanie DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-598">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-599">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-599">Description</span></span>

<span data-ttu-id="ab9a6-600">Ta usługa uruchamia przetwarzanie DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-601">Aby uzyskać więcej informacji na temat włączania interfejsu protokołu DHCP, zobacz *nx_dhcp_interface_enable*().</span><span class="sxs-lookup"><span data-stu-id="ab9a6-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="ab9a6-602">Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="ab9a6-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ab9a6-603">Jeśli nie ma innych interfejsów z uruchomionym klientem DHCP, ta usługa uruchomi/wznowi wątek klienta DHCP i (ponownie) uaktywni czasomierz klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="ab9a6-604">Aplikacja powinna używać *nx_ip_status_check* , aby sprawdzić, czy uzyskano adres IP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-605">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-605">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-606">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-607">**Interface_index**: indeks, na którym ma zostać uruchomiony klient DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-608">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-608">Return Values</span></span>

- <span data-ttu-id="ab9a6-609">**NX_SUCCESS**: (0X00) pomyślne uruchomienie usługi DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="ab9a6-610">**NX_DHCP_ALREADY_STARTED**: (0X93) usługa DHCP jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ab9a6-611">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-612">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ab9a6-613">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-614">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-614">Allowed From</span></span>

<span data-ttu-id="ab9a6-615">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-616">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="ab9a6-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ab9a6-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="ab9a6-618">Ustawianie funkcji wywołania zwrotnego zmiany stanu protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-619">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ab9a6-620">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-620">Description</span></span>

<span data-ttu-id="ab9a6-621">Ta usługa rejestruje określoną funkcję wywołania zwrotnego dhcp_state_change_notify w celu powiadomienia aplikacji o zmianach stanu protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ab9a6-622">Funkcja wywołania zwrotnego dostarcza stan, do którego przeszedł klient DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="ab9a6-623">Poniżej przedstawiono wartości skojarzone z różnymi stanami DHCP:</span><span class="sxs-lookup"><span data-stu-id="ab9a6-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="ab9a6-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="ab9a6-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="ab9a6-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="ab9a6-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="ab9a6-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="ab9a6-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="ab9a6-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="ab9a6-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="ab9a6-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="ab9a6-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="ab9a6-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="ab9a6-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="ab9a6-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="ab9a6-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="ab9a6-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="ab9a6-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="ab9a6-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="ab9a6-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-633">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-633">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-634">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-635">**dhcp_state_change_notify**: wskaźnik funkcji wywołania zwrotnego zmiany stanu</span><span class="sxs-lookup"><span data-stu-id="ab9a6-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-636">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-636">Return Values</span></span>

- <span data-ttu-id="ab9a6-637">**NX_SUCCESS**: (0X00) pomyślne ustawienie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="ab9a6-638">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-639">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-640">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-640">Allowed From</span></span>

<span data-ttu-id="ab9a6-641">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-642">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="ab9a6-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ab9a6-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="ab9a6-644">Ustaw funkcję wywołania zwrotnego zmiany stanu DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-645">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ab9a6-646">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-646">Description</span></span>

<span data-ttu-id="ab9a6-647">Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu powiadomienia aplikacji o zmianach stanu protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ab9a6-648">Argumenty wejściowe ATANH wywołania zwrotnego są indeksem interfejsu i stanem, w którym klient DHCP przeszedł w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="ab9a6-649">Aby uzyskać więcej informacji na temat funkcji zmiany stanu, zobacz *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="ab9a6-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-650">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-650">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-651">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-652">**dhcp_interface_state_change_notify**: wskaźnik funkcji wywołania zwrotnego aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab9a6-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-653">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-653">Return Values</span></span>

- <span data-ttu-id="ab9a6-654">**NX_SUCCESS**: (0X00) pomyślne ustawienie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="ab9a6-655">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-656">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-656">Allowed From</span></span>

<span data-ttu-id="ab9a6-657">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-658">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="ab9a6-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="ab9a6-659">nx_dhcp_stop</span></span>

<span data-ttu-id="ab9a6-660">Powoduje zatrzymanie przetwarzania protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-661">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-662">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-662">Description</span></span>

<span data-ttu-id="ab9a6-663">Ta usługa powoduje zatrzymanie przetwarzania protokołu DHCP na wszystkich interfejsach, które uruchomiły przetwarzanie DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="ab9a6-664">Jeśli nie ma żadnych interfejsów przetwarzających protokół DHCP, ta usługa zawiesza wątek klienta DHCP i dezaktywuje czasomierz klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="ab9a6-665">Aby zatrzymać usługę DHCP w określonym interfejsie, jeśli dla usługi DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_stop* .</span><span class="sxs-lookup"><span data-stu-id="ab9a6-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-666">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-666">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-667">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-668">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-668">Return Values</span></span>

- <span data-ttu-id="ab9a6-669">**NX_SUCCESS**: (0X00) POMYŚLNE zatrzymanie DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="ab9a6-670">**NX_DHCP_NOT_STARTED**: (0x96) wystąpienie DHCP nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="ab9a6-671">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-672">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-673">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-673">Allowed From</span></span>

<span data-ttu-id="ab9a6-674">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-675">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="ab9a6-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="ab9a6-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="ab9a6-677">Zatrzymaj przetwarzanie DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-678">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ab9a6-679">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-679">Description</span></span>

<span data-ttu-id="ab9a6-680">Ta usługa powoduje zatrzymanie przetwarzania DHCP w określonym interfejsie, jeśli usługa DHCP jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="ab9a6-681">Jeśli nie ma innych interfejsów z uruchomionym protokołem DHCP, wątek i czasomierz DHCP są wstrzymywane.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-682">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-682">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-683">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-684">**Interface_index**: interfejs, w którym ma zostać zatrzymane przetwarzanie DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-685">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-685">Return Values</span></span>

- <span data-ttu-id="ab9a6-686">**NX_SUCCESS**: (0X00) POMYŚLNE zatrzymanie DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="ab9a6-687">**NX_DHCP_NOT_STARTED**: (0X96) serwer DHCP nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="ab9a6-688">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-689">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ab9a6-690">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-691">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-691">Allowed From</span></span>

<span data-ttu-id="ab9a6-692">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-693">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="ab9a6-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ab9a6-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="ab9a6-695">Pobierz opcję DHCP z ostatniej odpowiedzi serwera</span><span class="sxs-lookup"><span data-stu-id="ab9a6-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-696">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ab9a6-697">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-697">Description</span></span>

<span data-ttu-id="ab9a6-698">Ta usługa pobiera określoną opcję DHCP z bufora opcji DHCP pierwszego interfejsu z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="ab9a6-699">Jeśli to się powiedzie, dane opcji są kopiowane do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-700">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-700">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-701">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="ab9a6-702">**request_option**: opcja DHCP, zgodnie z opisem w specyfikacjach RFC.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ab9a6-703">Zobacz opcję NX_DHCP_OPTION w *nxd_dhcp_client. h*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="ab9a6-704">**destination_ptr**: wskaźnik do miejsca docelowego dla ciągu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="ab9a6-705">**destination_size**: wskaźnik do rozmiaru miejsca docelowego i na Return, miejsce docelowe, do którego zostanie umieszczona liczba zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-706">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-706">Return Values</span></span>

- <span data-ttu-id="ab9a6-707">**NX_SUCCESS**: (0x00) pobieranie opcji powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="ab9a6-708">**NX_DHCP_NOT_BOUND**: (0X94) klient DHCP nie jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="ab9a6-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="ab9a6-710">**NX_DHCP_DEST_TO_SMALL**: (0X95) miejsce docelowe jest zbyt małe, aby można było przetrzymać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="ab9a6-711">W odpowiedzi serwera nie znaleziono opcji **NX_DHCP_PARSE_ERROR**: (0x97).</span><span class="sxs-lookup"><span data-stu-id="ab9a6-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="ab9a6-712">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="ab9a6-713">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-714">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-714">Allowed From</span></span>

<span data-ttu-id="ab9a6-715">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-716">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="ab9a6-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ab9a6-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="ab9a6-718">Pobierz opcję DHCP z ostatniej odpowiedzi serwera w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="ab9a6-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-719">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ab9a6-720">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-720">Description</span></span>

<span data-ttu-id="ab9a6-721">Ta usługa pobiera określoną opcję DHCP z bufora opcji DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ab9a6-722">Jeśli to się powiedzie, dane opcji są kopiowane do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-723">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-723">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-724">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-725">**Interface_index**: indeks, na którym ma zostać pobrana określona opcja</span><span class="sxs-lookup"><span data-stu-id="ab9a6-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="ab9a6-726">**request_option**: opcja DHCP, zgodnie z opisem w specyfikacjach RFC.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ab9a6-727">Zobacz NX_DHCP_OPTION opcji: w *nxd_dhcp_client. h*.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="ab9a6-728">**destination_ptr**: wskaźnik do miejsca docelowego dla ciągu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="ab9a6-729">**destination_size**: wskaźnik do rozmiaru miejsca docelowego i na Return, miejsce docelowe, do którego zostanie umieszczona liczba zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-730">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-730">Return Values</span></span>

- <span data-ttu-id="ab9a6-731">**NX_SUCCESS**: (0x00) pobieranie opcji powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="ab9a6-732">**NX_DHCP_NOT_BOUND**: (0x94) nie przypisano adresu IP</span><span class="sxs-lookup"><span data-stu-id="ab9a6-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="ab9a6-733">Bufor **NX_DHCP_DEST_TO_SMALL**: (0x95) jest za mały</span><span class="sxs-lookup"><span data-stu-id="ab9a6-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="ab9a6-734">**NX_DHCP_PARSE_ERROR**: w odpowiedzi serwera nie znaleziono opcji DHCP (0x97).</span><span class="sxs-lookup"><span data-stu-id="ab9a6-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="ab9a6-735">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ab9a6-736">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ab9a6-737">NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="ab9a6-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-738">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-738">Allowed From</span></span>

<span data-ttu-id="ab9a6-739">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-740">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="ab9a6-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="ab9a6-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="ab9a6-742">Konwertuj cztery bajty na ULONG</span><span class="sxs-lookup"><span data-stu-id="ab9a6-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-743">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="ab9a6-744">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-744">Description</span></span>

<span data-ttu-id="ab9a6-745">Ta usługa konwertuje cztery znaki wskazywane przez "option_string_ptr" na wartość długą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="ab9a6-746">Jest to szczególnie przydatne, gdy adresy IP są</span><span class="sxs-lookup"><span data-stu-id="ab9a6-746">It is especially useful when IP addresses are</span></span>  
<span data-ttu-id="ab9a6-747">aktualny.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-747">present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-748">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-748">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-749">**option_string_ptr**: wskaźnik do wcześniej pobranego ciągu opcji.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-750">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-750">Return Values</span></span>

- <span data-ttu-id="ab9a6-751">**Wartość**: wartość pierwszych czterech bajtów.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-752">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-752">Allowed From</span></span>

<span data-ttu-id="ab9a6-753">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-754">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="ab9a6-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="ab9a6-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="ab9a6-756">Ustaw funkcję wywołania zwrotnego w celu dodania opcji dostarczonych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="ab9a6-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="ab9a6-757">Prototype</span><span class="sxs-lookup"><span data-stu-id="ab9a6-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="ab9a6-758">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9a6-758">Description</span></span>

<span data-ttu-id="ab9a6-759">Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu dodania opcji dostarczonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="ab9a6-760">Jeśli określono funkcję wywołania zwrotnego, aplikacje mogą dodać opcje dostarczone przez użytkownika do pakietu, iface_index i message_type.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="ab9a6-761">W procedurze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-761">In user’s routine.</span></span> <span data-ttu-id="ab9a6-762">W przypadku dodawania opcji dostarczonych przez użytkownika aplikacje muszą być zgodne z formatem opcji DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="ab9a6-763">Łączny rozmiar opcji użytkownika musi być mniejszy lub równy user_option_length i aktualizować user_option_length jako rzeczywistą długość opcji.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="ab9a6-764">Zwróć NX_TRUE w przypadku pomyślnego dodania opcji, w przeciwnym razie Zwróć NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab9a6-765">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ab9a6-765">Input Parameters</span></span>

- <span data-ttu-id="ab9a6-766">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ab9a6-767">**dhcp_user_option_add**: wskaźnik do opcji użytkownika Dodaj funkcję.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab9a6-768">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ab9a6-768">Return Values</span></span>

- <span data-ttu-id="ab9a6-769">**NX_SUCCESS**: (0X00) pomyślne ustawienie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="ab9a6-770">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab9a6-771">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ab9a6-771">Allowed From</span></span>

<span data-ttu-id="ab9a6-772">Wątki</span><span class="sxs-lookup"><span data-stu-id="ab9a6-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab9a6-773">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab9a6-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

