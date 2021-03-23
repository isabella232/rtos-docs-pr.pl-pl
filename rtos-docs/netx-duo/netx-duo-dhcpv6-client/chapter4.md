---
title: Rozdział 4 — usługi klienta DHCPv6 platformy Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług klienta DHCPv6 usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821978"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="69a33-103">Rozdział 4 — usługi klienta DHCPv6 platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="69a33-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="69a33-104">Ten rozdział zawiera opis wszystkich usług klienta DHCPv6 usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="69a33-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="69a33-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="69a33-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="69a33-106">**nx_dhcpv6_client_create:** *Tworzenie wystąpienia klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="69a33-107">**nx_dhcpv6_client_delete:** *usuwanie wystąpienia klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="69a33-108">**nx_dhcpv6_create_ client_duid:** *Tworzenie identyfikatora DUID klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="69a33-109">**nx_dhcpv6 _add_client_ia:** *Dodawanie adresu tożsamości klienta DHCPv6 (IA)*</span><span class="sxs-lookup"><span data-stu-id="69a33-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="69a33-110">**nx_dhcpv6 _create_client_ia:** (*starsze Dodawanie adresu tożsamości klienta DHCPv6 (IA))*</span><span class="sxs-lookup"><span data-stu-id="69a33-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="69a33-111">**nx_dhcpv6_create_client_iana:** *Utwórz skojarzenie tożsamości klienta Dhcpv6 dla adresów innych niż tymczasowe (IANA)*</span><span class="sxs-lookup"><span data-stu-id="69a33-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="69a33-112">**nx_dhcpv6_get_client_duid_time_id:** *Pobierz identyfikator czasu z identyfikatora DUID klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="69a33-113">**nx_dhcpv6_client_set_interface:** *Ustaw interfejs sieciowy klienta na potrzeby komunikacji z serwerem DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="69a33-114">**nx_dhcpv6_get_IP_address:** *pobieranie globalnego adresu IPv6 przypisanego do klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="69a33-115">**nx_dhcpv6_get_lease_time_data:** *Pobierz T1, T2, prawidłowych i preferowanych okresów istnienia dla globalnego adresu IPv6 klienta*</span><span class="sxs-lookup"><span data-stu-id="69a33-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="69a33-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Uzyskaj T1, T2, prawidłowy i preferowany okres istnienia dla adresu IPv6 klienta DHCPv6 według indeksu adresu*</span><span class="sxs-lookup"><span data-stu-id="69a33-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="69a33-117">**nx_dhcpv6_get_iana_lease_time:** *Pobierz T1 i T2 w ramach SKOJARZENIA tożsamości (IANA) z klientem DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="69a33-118">**nx_dhcpv6_get_other_option_data:** *Pobierz określone dane opcji, np. nazwę domeny lub serwer strefy czasowej*</span><span class="sxs-lookup"><span data-stu-id="69a33-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="69a33-119">**nx_dhcpv6_get_DNS_server_address:** *Pobierz adres serwera DNS z określonym indeksem na listę serwerów DNS klienta protokołu DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="69a33-120">**nx_dhcpv6_get_time_accrued:** *uzyskaj czas naliczania dzierżawy globalnego adresu IPv6 został powiązany z klientem DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="69a33-121">**nx_dhcpv6_get_time_server_address:** *Pobierz adres serwera czasu o określonym indeksie na listę serwerów czasu klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="69a33-122">**nx_dhcpv6_get_valid_ip_address_count:** *pobieranie liczby adresów IPv6 przypisanych do klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="69a33-123">**nx_dhcpv6_reinitialize:** *zainicjuj ponownie protokół DHCPv6 w celu ponownego uruchomienia komputera stanu klienta DHCPv6 i uruchomienia protokołu DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="69a33-124">**nx_dhcpv6_request_confirm:** *Wyślij żądanie potwierdzenia do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="69a33-125">**nx_dhcpv6_request_inform_request:** S *Zakończ komunikat żądania inform na serwerze*</span><span class="sxs-lookup"><span data-stu-id="69a33-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="69a33-126">**nx_dhcpv6_request_release:** *Wyślij żądanie wydania do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="69a33-127">**nx_dhcpv6_request_option_DNS_server:** *Dodaj opcję serwer DNS do żądania opcji klienta dane w żądaniach wysyłanych do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="69a33-128">**nx_dhcpv6_request_option_FQDN:** *Dodaj opcję FQDN do żądania opcji klienta dane w żądaniach wysyłanych do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="69a33-129">**nx_dhcpv6_request_option_domain_name:** *Dodaj opcję nazwy domeny do żądania opcji klienta dane w żądaniach wysyłanych do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="69a33-130">**nx_dhcpv6_request_option_time_server:** *Dodaj opcję serwer czasu do żądania opcji klienta dane w żądaniach wysyłanych do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="69a33-131">**nx_dhcpv6_request_option_timezone:** *Dodaj opcję strefy czasowej do żądania opcji klienta dane w żądaniach wysyłanych do serwera*</span><span class="sxs-lookup"><span data-stu-id="69a33-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="69a33-132">**nx_dhcpv6_request_solicit:** *Wyślij żądanie protokołu Dhcpv6 do dowolnego serwera w sieci klienta (emisja)*</span><span class="sxs-lookup"><span data-stu-id="69a33-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="69a33-133">**nx_dhcpv6_request_solicit_rapid:** *Wyślij żądanie protokołu Dhcpv6 do dowolnego serwera w sieci klienta (emisji) z ustawioną opcją szybkiego zatwierdzania*</span><span class="sxs-lookup"><span data-stu-id="69a33-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="69a33-134">**nx_dhcpv6_resume:** *Wznów przetwarzanie klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="69a33-135">**nx_dhcpv6_start:** *Uruchom zadanie wątku klienta DHCPv6. Zwróć uwagę, że nie jest to równoznaczne z uruchomieniem komputera stanu DHCPv6 i nie wysyła żądania żądanie*</span><span class="sxs-lookup"><span data-stu-id="69a33-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="69a33-136">**nx_dhcpv6_stop:** *Zatrzymaj zadanie wątku klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="69a33-137">**nx_dhcpv6_suspend:** *Wstrzymywanie zadania wątku klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="69a33-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="69a33-138">**nx_dhcpv6_set_time_accrued:** *Ustaw czas naliczania dla dzierżawy globalnego adresu IPv6 klienta w rekordzie klienta.*</span><span class="sxs-lookup"><span data-stu-id="69a33-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="69a33-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="69a33-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="69a33-140">Tworzenie wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-141">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="69a33-142">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-142">Description</span></span>

<span data-ttu-id="69a33-143">Ta usługa tworzy wystąpienie klienta DHCPv6, w tym funkcje wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="69a33-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-144">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-144">Input Parameters</span></span>

- <span data-ttu-id="69a33-145">**dhcpv6_ptr** Wskaźnik do bloku sterowania DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="69a33-146">**ip_ptr** Wskaźnik do wystąpienia adresu IP klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="69a33-147">**name_ptr** Wskaźnik do nazwy dla wystąpienia DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="69a33-148">**packet_pool_ptr** Wskaźnik do puli pakietów klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="69a33-149">**stack_ptr** Wskaźnik do pamięci stosu klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="69a33-150">**stack_size** Rozmiar pamięci stosu klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="69a33-151">**dhcpv6_state_change_notify** Wskaźnik do funkcji wywołania zwrotnego wywoływany, gdy klient inicjuje nowe żądanie DHCPv6 na serwerze</span><span class="sxs-lookup"><span data-stu-id="69a33-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="69a33-152">**dhcpv6_server_error_handler** Wskaźnik do funkcji wywołania zwrotnego wywoływany, gdy klient otrzymuje stan błędu z serwera</span><span class="sxs-lookup"><span data-stu-id="69a33-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-153">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-153">Return Values</span></span>

- <span data-ttu-id="69a33-154">**NX_SUCCESS** (0x00) — pomyślne utworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="69a33-155">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-156">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-157">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-157">Allowed From</span></span>

<span data-ttu-id="69a33-158">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-160">See Also</span></span>

- <span data-ttu-id="69a33-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="69a33-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="69a33-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="69a33-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="69a33-163">Usuwanie wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-165">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-165">Description</span></span>

<span data-ttu-id="69a33-166">Ta usługa usuwa wcześniej utworzone wystąpienie klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-167">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-167">Input Parameters</span></span>

- <span data-ttu-id="69a33-168">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-169">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-169">Return Values</span></span>

- <span data-ttu-id="69a33-170">**NX_SUCCESS** (0X00) pomyślne usunięcie DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="69a33-171">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-172">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-173">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-173">Allowed From</span></span>

<span data-ttu-id="69a33-174">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-176">See Also</span></span>

- <span data-ttu-id="69a33-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="69a33-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="69a33-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="69a33-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="69a33-179">Ustawia interfejs sieciowy klienta dla protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-180">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="69a33-181">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-181">Description</span></span>

<span data-ttu-id="69a33-182">Ta usługa ustawia interfejs sieciowy klienta na potrzeby komunikacji z serwerami DHCPv6 do określonego indeksu interfejsu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="69a33-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-183">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-183">Input Parameters</span></span>

- <span data-ttu-id="69a33-184">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-185">**interface_index** Indeks wskazujący interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="69a33-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-186">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-186">Return Values</span></span>

- <span data-ttu-id="69a33-187">Interfejs **NX_SUCCESS** (0x00) został pomyślnie ustawiony</span><span class="sxs-lookup"><span data-stu-id="69a33-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="69a33-188">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-189">NX_INVALID_INTERFACE (0x4C) nieprawidłowe dane wejściowe indeksu interfejsu</span><span class="sxs-lookup"><span data-stu-id="69a33-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-190">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-190">Allowed From</span></span>

<span data-ttu-id="69a33-191">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-192">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-193">See Also</span></span>

- <span data-ttu-id="69a33-194">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="69a33-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="69a33-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="69a33-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="69a33-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="69a33-197">Ustawia adres docelowy, na który powinien zostać wysłany komunikat protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-198">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="69a33-199">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-199">Description</span></span>

<span data-ttu-id="69a33-200">Ta usługa ustawia adres docelowy, na który powinien zostać wysłany komunikat protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="69a33-201">Domyślnie jest ALL_DHCP_Relay_Agents_and_Servers (FF02:: 1:2).</span><span class="sxs-lookup"><span data-stu-id="69a33-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-202">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-202">Input Parameters</span></span>

- <span data-ttu-id="69a33-203">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-204">**destination_address** Adres docelowy</span><span class="sxs-lookup"><span data-stu-id="69a33-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-205">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-205">Return Values</span></span>

- <span data-ttu-id="69a33-206">Interfejs **NX_SUCCESS** (0x00) został pomyślnie ustawiony</span><span class="sxs-lookup"><span data-stu-id="69a33-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="69a33-207">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-208">Błąd akapitu NX_DHCPV6_PARAM_ERROR (0xE93)</span><span class="sxs-lookup"><span data-stu-id="69a33-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-209">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-209">Allowed From</span></span>

<span data-ttu-id="69a33-210">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-211">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-212">See Also</span></span>

- <span data-ttu-id="69a33-213">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="69a33-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="69a33-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="69a33-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="69a33-216">Utwórz obiekt identyfikatora DUID klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-217">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="69a33-218">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-218">Description</span></span>

<span data-ttu-id="69a33-219">Ta usługa tworzy identyfikator DUID klienta z parametrami wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="69a33-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="69a33-220">Jeśli dane wejściowe czasu nie zostaną podane, a Typ identyfikatora DUID wskazuje warstwę łącza z czasem, ta funkcja będzie dostarczać czas, który zawiera losowy współczynnik unikatowości.</span><span class="sxs-lookup"><span data-stu-id="69a33-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="69a33-221">Typy identyfikatora DUID przypisane przez dostawcę (Enterprise) nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="69a33-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-222">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-222">Input Parameters</span></span>

- <span data-ttu-id="69a33-223">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-224">**duid_type** Typ identyfikatora DUID (sprzęt, przedsiębiorstwo itp.)</span><span class="sxs-lookup"><span data-stu-id="69a33-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="69a33-225">**hardware_type** Sprzęt sieciowy, np. IEEE 802</span><span class="sxs-lookup"><span data-stu-id="69a33-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="69a33-226">**czas** Wartość używana podczas tworzenia unikatowego identyfikatora</span><span class="sxs-lookup"><span data-stu-id="69a33-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-227">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-227">Return Values</span></span>

- <span data-ttu-id="69a33-228">**NX_SUCCESS** (0X00) pomyślnie utworzono identyfikator DUID klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="69a33-229">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-230">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="69a33-231">Typ identyfikatora DUID NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) nieznany lub nieobsługiwany</span><span class="sxs-lookup"><span data-stu-id="69a33-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="69a33-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) identyfikator DUID typu sprzętu nieznany lub nieobsługiwany</span><span class="sxs-lookup"><span data-stu-id="69a33-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-233">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-233">Allowed From</span></span>

<span data-ttu-id="69a33-234">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-235">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-236">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-236">See Also</span></span>

- <span data-ttu-id="69a33-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="69a33-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="69a33-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="69a33-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="69a33-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="69a33-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="69a33-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="69a33-241">Dodawanie skojarzenia tożsamości do klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-242">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="69a33-243">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-243">Description</span></span>

<span data-ttu-id="69a33-244">Ta usługa jest taka sama jak usługa *nx_dhcpv6_add_client_ia* .</span><span class="sxs-lookup"><span data-stu-id="69a33-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="69a33-245">Dodaje skojarzenie tożsamości klienta, wypełniając rekord klienta podanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="69a33-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="69a33-246">Aby zażądać maksymalnych preferowanych i prawidłowych okresów istnienia, ustaw dla tych parametrów nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="69a33-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="69a33-247">Aby dodać więcej niż jeden element IA do klienta DHCPv6, należy ustawić NX_DHCPV6_MAX_IA_ADDRESS wartość wyższą niż domyślna wartość 1.</span><span class="sxs-lookup"><span data-stu-id="69a33-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-248">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-248">Input Parameters</span></span>

- <span data-ttu-id="69a33-249">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-250">**ipv6_address** Wskaźnik do bloku adresów IP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="69a33-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="69a33-251">**preferred_lifetime** Długość czasu przed przestarzałym adresem IP</span><span class="sxs-lookup"><span data-stu-id="69a33-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="69a33-252">**valid_lifetime** Długość czasu przed wygaśnięciem adresu IP</span><span class="sxs-lookup"><span data-stu-id="69a33-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-253">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-253">Return Values</span></span>

- <span data-ttu-id="69a33-254">**NX_SUCCESS** (0X00) pomyślne dodanie klienta IA</span><span class="sxs-lookup"><span data-stu-id="69a33-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="69a33-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) zduplikowany adres IA</span><span class="sxs-lookup"><span data-stu-id="69a33-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="69a33-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA przekracza maksymalny klient IAs może przechowywać</span><span class="sxs-lookup"><span data-stu-id="69a33-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="69a33-257">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) nieprawidłowy adres (np. null) IA w IA</span><span class="sxs-lookup"><span data-stu-id="69a33-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="69a33-259">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="69a33-260">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-260">Allowed From</span></span>

<span data-ttu-id="69a33-261">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-262">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-263">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-263">See Also</span></span>

- <span data-ttu-id="69a33-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="69a33-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="69a33-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="69a33-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="69a33-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="69a33-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="69a33-268">Utwórz skojarzenie tożsamości (nietymczasowe) dla klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-269">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="69a33-270">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-270">Description</span></span>

<span data-ttu-id="69a33-271">Ta usługa tworzy nietymczasowym skojarzeniem tożsamości (IANA) klienta z podanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="69a33-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="69a33-272">Aby ustawić czas T1 i T2 na maksymalny (nieskończoność) w żądaniach klientów DHCPv6, ustaw te parametry na NX_DHCPV6_INFINITE_LEASE.</span><span class="sxs-lookup"><span data-stu-id="69a33-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="69a33-273">Klient ma tylko jednego organizację IANA.</span><span class="sxs-lookup"><span data-stu-id="69a33-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-274">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-274">Input Parameters</span></span>

- <span data-ttu-id="69a33-275">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-276">**IA_ident** Unikatowy identyfikator skojarzenia tożsamości</span><span class="sxs-lookup"><span data-stu-id="69a33-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="69a33-277">**T1** Gdy klient musi uruchomić Odnawianie adresu IPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="69a33-278">**T2** Gdy klient musi uruchomić ponowne wiązanie adresu theIPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-279">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-279">Return Values</span></span>

- <span data-ttu-id="69a33-280">**NX_SUCCESS** (0X00) pomyślnie utworzył organizację IANA</span><span class="sxs-lookup"><span data-stu-id="69a33-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="69a33-281">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-282">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-283">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-283">Allowed From</span></span>

<span data-ttu-id="69a33-284">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-285">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-286">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-286">See Also</span></span>

- <span data-ttu-id="69a33-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="69a33-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="69a33-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="69a33-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="69a33-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="69a33-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="69a33-291">Dodawanie skojarzenia tożsamości do klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-292">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="69a33-293">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-293">Description</span></span>

<span data-ttu-id="69a33-294">Ta usługa dodaje skojarzenie tożsamości klienta, wypełniając rekord klienta podanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="69a33-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="69a33-295">Aby zażądać maksymalnych preferowanych i prawidłowych okresów istnienia, ustaw dla tych parametrów nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="69a33-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="69a33-296">Aby dodać więcej niż jeden element IA do klienta DHCPv6, należy ustawić NX_DHCPV6_MAX_IA_ADDRESS wartość wyższą niż domyślna wartość 1.</span><span class="sxs-lookup"><span data-stu-id="69a33-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-297">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-297">Input Parameters</span></span>

- <span data-ttu-id="69a33-298">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-299">**ipv6_address** Wskaźnik do bloku adresów IP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="69a33-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="69a33-300">**preferred_lifetime** Długość czasu przed przestarzałym adresem IP</span><span class="sxs-lookup"><span data-stu-id="69a33-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="69a33-301">**valid_lifetime** Długość czasu przed wygaśnięciem adresu IP</span><span class="sxs-lookup"><span data-stu-id="69a33-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="69a33-302">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-302">Return Values</span></span>

- <span data-ttu-id="69a33-303">**NX_SUCCESS** (0X00) pomyślne dodanie klienta IA</span><span class="sxs-lookup"><span data-stu-id="69a33-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="69a33-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) zduplikowany adres IA</span><span class="sxs-lookup"><span data-stu-id="69a33-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="69a33-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA przekracza maksymalny klient IAs może przechowywać</span><span class="sxs-lookup"><span data-stu-id="69a33-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="69a33-306">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) nieprawidłowy adres (np. null) IA w IA</span><span class="sxs-lookup"><span data-stu-id="69a33-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="69a33-308">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="69a33-309">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-309">Allowed From</span></span>

<span data-ttu-id="69a33-310">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-311">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-312">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-312">See Also</span></span>

- <span data-ttu-id="69a33-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="69a33-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="69a33-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="69a33-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="69a33-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="69a33-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="69a33-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="69a33-317">Pobiera identyfikator czasu z identyfikatora DUID klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="69a33-319">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-319">Description</span></span>

<span data-ttu-id="69a33-320">Ta usługa pobiera pole identyfikatora czasu z identyfikatora DUID klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="69a33-321">Jeśli aplikacja musi najpierw wywołać *nx_dhcpv6_create_client_duid*, aby wypełnić identyfikator DUID klienta w wystąpieniu klienta DHCPv6 lub będzie mieć wartość null dla tego pola.</span><span class="sxs-lookup"><span data-stu-id="69a33-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="69a33-322">Celem jest zapisanie tych danych przez aplikację i zaprezentowanie tego samego identyfikatora DUID klienta na serwerze, w tym pola czasowego, w przypadku ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="69a33-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-323">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-323">Input Parameters</span></span>

- <span data-ttu-id="69a33-324">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-325">**TIME_ID** Wskaźnik do pola czasu identyfikatora DUID klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-326">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-326">Return Values</span></span>

- <span data-ttu-id="69a33-327">Pomyślnie pobrano dane dzierżawy IP **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="69a33-328">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-329">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-330">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-330">Allowed From</span></span>

<span data-ttu-id="69a33-331">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-332">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-333">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-333">See Also</span></span>

- <span data-ttu-id="69a33-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="69a33-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="69a33-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="69a33-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="69a33-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="69a33-339">Pobiera globalny adres IPv6 klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-340">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="69a33-341">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-341">Description</span></span>

<span data-ttu-id="69a33-342">Ta usługa pobiera globalny adres IPv6 klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="69a33-343">Jeśli klient nie ma prawidłowego adresu, zwracany jest stan błędu.</span><span class="sxs-lookup"><span data-stu-id="69a33-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="69a33-344">Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracany jest podstawowy adres IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-345">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-345">Input Parameters</span></span>

- <span data-ttu-id="69a33-346">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-347">**IP_address** Wskaźnik na adres IPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-348">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-348">Return Values</span></span>

- <span data-ttu-id="69a33-349">Adres IPv6 **NX_SUCCESS** (0x00) został pomyślnie przypisany</span><span class="sxs-lookup"><span data-stu-id="69a33-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="69a33-350">Adres IPv6 **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="69a33-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="69a33-351">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-352">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-353">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-353">Allowed From</span></span>

<span data-ttu-id="69a33-354">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-355">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="69a33-356">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-356">See Also</span></span>

- <span data-ttu-id="69a33-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="69a33-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="69a33-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="69a33-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="69a33-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="69a33-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="69a33-362">Pobiera dane czasu dzierżawy adresu (IA) klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-363">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="69a33-364">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-364">Description</span></span>

<span data-ttu-id="69a33-365">Ta usługa pobiera dane o globalnym czasie adresu klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="69a33-366">Jeśli stan adresu klienta IA jest nieprawidłowy, dane czasu są ustawiane na zero i zwracany jest stan pomyślnego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="69a33-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="69a33-367">Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracane są dane podstawowych adresów IA.</span><span class="sxs-lookup"><span data-stu-id="69a33-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-368">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-368">Input Parameters</span></span>

- <span data-ttu-id="69a33-369">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-370">**T1** Wskaźnik na czas odnowienia adresu (IA)</span><span class="sxs-lookup"><span data-stu-id="69a33-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="69a33-371">**T2** Wskaźnik do ponownego powiązania adresu IA</span><span class="sxs-lookup"><span data-stu-id="69a33-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="69a33-372">**preferred_lifetime** Wskaźnik do czasu, gdy adres IA jest przestarzały</span><span class="sxs-lookup"><span data-stu-id="69a33-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="69a33-373">**valid_lifetime** Wskaźnik do czasu wygaśnięcia okresu IA</span><span class="sxs-lookup"><span data-stu-id="69a33-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-374">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-374">Return Values</span></span>

- <span data-ttu-id="69a33-375">**NX_SUCCESS** (0x00) pomyślnie pobrano dane DZIERŻAWy IA</span><span class="sxs-lookup"><span data-stu-id="69a33-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="69a33-376">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-377">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-378">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-378">Allowed From</span></span>

<span data-ttu-id="69a33-379">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-380">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-381">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-381">See Also</span></span>

- <span data-ttu-id="69a33-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="69a33-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="69a33-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="69a33-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="69a33-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="69a33-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="69a33-387">nx_dhcpv6_get_iana lease_time</span><span class="sxs-lookup"><span data-stu-id="69a33-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="69a33-388">Pobieranie danych czasu dzierżawy organizacji klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-389">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="69a33-390">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-390">Description</span></span>

<span data-ttu-id="69a33-391">Ta usługa pobiera dane globalne czasu dzierżawy (T1 i T2) klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="69a33-392">Jeśli żaden z adresów klienta IA-NA nie ma prawidłowego stanu adresu, dane czasu są ustawione na zero i zwracany jest stan pomyślnego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="69a33-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="69a33-393">Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracane są dane podstawowych adresów IA.</span><span class="sxs-lookup"><span data-stu-id="69a33-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-394">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-394">Input Parameters</span></span>

- <span data-ttu-id="69a33-395">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-396">**T1** Wskaźnik do momentu rozpoczęcia odnawiania dzierżawy</span><span class="sxs-lookup"><span data-stu-id="69a33-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="69a33-397">**T2** Wskaźnik do czasu rozpoczęcia ponownego powiązania dzierżawy</span><span class="sxs-lookup"><span data-stu-id="69a33-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-398">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-398">Return Values</span></span>

- <span data-ttu-id="69a33-399">**NX_SUCCESS** (0x00) dane dzierżawy organizacji Iana zostały pomyślnie pobrane</span><span class="sxs-lookup"><span data-stu-id="69a33-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="69a33-400">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-401">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-402">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-402">Allowed From</span></span>

<span data-ttu-id="69a33-403">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-404">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-405">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-405">See Also</span></span>

- <span data-ttu-id="69a33-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="69a33-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="69a33-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="69a33-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="69a33-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="69a33-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="69a33-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="69a33-412">Pobierz liczbę prawidłowych adresów (IA) klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-413">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="69a33-414">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-414">Description</span></span>

<span data-ttu-id="69a33-415">Ta usługa Pobiera liczbę prawidłowych adresów IPv6 klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="69a33-416">Prawidłowy adres IPv6 jest powiązany (przypisany) do klienta i zarejestrowany w wystąpieniu adresu IP.</span><span class="sxs-lookup"><span data-stu-id="69a33-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-417">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-417">Input Parameters</span></span>

- <span data-ttu-id="69a33-418">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-419">**address_count** Wskaźnik do liczby adresów do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="69a33-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-420">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-420">Return Values</span></span>

- <span data-ttu-id="69a33-421">**NX_SUCCESS** (0x00) dane dzierżawy organizacji Iana zostały pomyślnie pobrane</span><span class="sxs-lookup"><span data-stu-id="69a33-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="69a33-422">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-423">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-424">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-424">Allowed From</span></span>

<span data-ttu-id="69a33-425">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-426">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="69a33-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="69a33-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="69a33-428">Pobieranie danych klienta IA przez indeks adresu</span><span class="sxs-lookup"><span data-stu-id="69a33-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-429">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="69a33-430">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-430">Description</span></span>

<span data-ttu-id="69a33-431">Ta usługa Pobiera adres IA klienta i dane dzierżawy według indeksu adresu.</span><span class="sxs-lookup"><span data-stu-id="69a33-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="69a33-432">Jeśli podano nieprawidłowy indeks lub adres IPv6 w tym indeksie jest nieprawidłowy, usługa zwróci NX_DHCPV6_IA_ADDRESS_NOT_VALID stanu błędu.</span><span class="sxs-lookup"><span data-stu-id="69a33-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-433">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-433">Input Parameters</span></span>

- <span data-ttu-id="69a33-434">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-435">**address_index** Indeksowanie w tabeli protokołu DHCPv6 IA</span><span class="sxs-lookup"><span data-stu-id="69a33-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="69a33-436">**IP_address** Wskaźnik na adres IPv6 do pobrania</span><span class="sxs-lookup"><span data-stu-id="69a33-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="69a33-437">**preferred_lifetime** Wskaźnik do czasu, gdy adres IA jest przestarzały</span><span class="sxs-lookup"><span data-stu-id="69a33-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="69a33-438">**valid_lifetime** Wskaźnik do czasu wygaśnięcia okresu IA</span><span class="sxs-lookup"><span data-stu-id="69a33-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-439">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-439">Return Values</span></span>

- <span data-ttu-id="69a33-440">Dane dotyczące **NX_SUCCESS** (0X00) Iana zostały pomyślnie pobrane</span><span class="sxs-lookup"><span data-stu-id="69a33-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="69a33-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Nieprawidłowy indeks lub nie ma prawidłowego adresu IPv6 pod podanym indeksem</span><span class="sxs-lookup"><span data-stu-id="69a33-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="69a33-442">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-443">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-444">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-444">Allowed From</span></span>

<span data-ttu-id="69a33-445">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-446">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="69a33-447">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-447">See Also</span></span>

- <span data-ttu-id="69a33-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="69a33-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="69a33-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="69a33-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="69a33-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="69a33-452">Pobiera adres serwera DNS</span><span class="sxs-lookup"><span data-stu-id="69a33-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-453">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="69a33-454">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-454">Description</span></span>

<span data-ttu-id="69a33-455">Ta usługa pobiera dane adresów IPv6 serwera DNS z określonym indeksem na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="69a33-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="69a33-456">Jeśli lista nie zawiera adresu serwera w indeksie, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="69a33-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="69a33-457">Indeks nie może przekroczyć rozmiaru listy serwerów DNS zdefiniowanej przez użytkownika NX_DHCPV6_NUM_DNS_SERVERS opcję konfigurowalną.</span><span class="sxs-lookup"><span data-stu-id="69a33-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-458">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-458">Input Parameters</span></span>

- <span data-ttu-id="69a33-459">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-460">**indeks** Indeksuj na listę serwerów DNS</span><span class="sxs-lookup"><span data-stu-id="69a33-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="69a33-461">**server_address** Wskaźnik do buforu adresów serwera</span><span class="sxs-lookup"><span data-stu-id="69a33-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-462">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-462">Return Values</span></span>

- <span data-ttu-id="69a33-463">Pomyślnie pobrano adres **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="69a33-464">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-465">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-466">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-466">Allowed From</span></span>

<span data-ttu-id="69a33-467">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-468">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-469">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-469">See Also</span></span>

- <span data-ttu-id="69a33-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="69a33-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="69a33-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="69a33-474">Pobiera dane opcji protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-475">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="69a33-476">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-476">Description</span></span>

<span data-ttu-id="69a33-477">Ta usługa pobiera dane z opcji DHCPv6 z komunikatu protokołu DHCPv6 dla określonego kodu opcji.</span><span class="sxs-lookup"><span data-stu-id="69a33-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-478">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-478">Input Parameters</span></span>

- <span data-ttu-id="69a33-479">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-480">**kod opcji kodu opcji** , dla którego dane mają zostać pobrane</span><span class="sxs-lookup"><span data-stu-id="69a33-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="69a33-481">**bufor** Wskaźnik do buforu, do którego mają zostać skopiowane dane</span><span class="sxs-lookup"><span data-stu-id="69a33-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="69a33-482">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-482">Return Values</span></span>

- <span data-ttu-id="69a33-483">Pomyślnie pobrano dane opcji **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="69a33-484">**NX_DHCPV6_UNKNOWN_OPTION** (0XEAB) nieznany/nieobsługiwany kod opcji</span><span class="sxs-lookup"><span data-stu-id="69a33-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="69a33-485">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-486">NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="69a33-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="69a33-487">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-488">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-488">Allowed From</span></span>

<span data-ttu-id="69a33-489">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-490">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-491">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-491">See Also</span></span>

- <span data-ttu-id="69a33-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="69a33-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="69a33-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="69a33-496">Pobiera czas naliczany przez dzierżawę adresu IP klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-497">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="69a33-498">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-498">Description</span></span>

<span data-ttu-id="69a33-499">Ta usługa Pobiera czas naliczony przez dzierżawę adresu IPv6 klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="69a33-500">Funkcja sprawdza wszystkie adresy IPv6 przypisane do klienta pod kątem pierwszego prawidłowego adresu.</span><span class="sxs-lookup"><span data-stu-id="69a33-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="69a33-501">Jeśli nie zostanie znaleziony prawidłowy adres, zwracana jest wartość zero dla naliczonego czasu.</span><span class="sxs-lookup"><span data-stu-id="69a33-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-502">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-502">Input Parameters</span></span>

- <span data-ttu-id="69a33-503">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-504">**time_accrued** Wskaźnik na czas naliczany w dzierżawie IP</span><span class="sxs-lookup"><span data-stu-id="69a33-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-505">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-505">Return Values</span></span>

- <span data-ttu-id="69a33-506">Pomyślnie pobrano naliczony czas **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="69a33-507">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-508">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-509">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-509">Allowed From</span></span>

<span data-ttu-id="69a33-510">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-511">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-512">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-512">See Also</span></span>

- <span data-ttu-id="69a33-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="69a33-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="69a33-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="69a33-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="69a33-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="69a33-518">Pobiera adres serwera czasu</span><span class="sxs-lookup"><span data-stu-id="69a33-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-519">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="69a33-520">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-520">Description</span></span>

<span data-ttu-id="69a33-521">Ta usługa pobiera dane adresów IPv6 serwera czasu o określonym indeksie na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="69a33-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="69a33-522">Jeśli lista nie zawiera adresu serwera w indeksie, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="69a33-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="69a33-523">Indeks nie może przekroczyć rozmiaru listy serwerów czasu określonego przez użytkownika NX_DHCPV6_NUM_TIME_SERVERS opcji konfigurowalnej.</span><span class="sxs-lookup"><span data-stu-id="69a33-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-524">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-524">Input Parameters</span></span>

- <span data-ttu-id="69a33-525">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-526">**indeks** Indeksuj na listę serwerów czasu</span><span class="sxs-lookup"><span data-stu-id="69a33-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="69a33-527">**server_address** Wskaźnik do buforu adresów serwera</span><span class="sxs-lookup"><span data-stu-id="69a33-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-528">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-528">Return Values</span></span>

- <span data-ttu-id="69a33-529">Pomyślnie pobrano adres **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="69a33-530">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-531">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-532">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-532">Allowed From</span></span>

<span data-ttu-id="69a33-533">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-534">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-535">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-535">See Also</span></span>

- <span data-ttu-id="69a33-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="69a33-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="69a33-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="69a33-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="69a33-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="69a33-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="69a33-541">Usuń adres IP klienta z tabeli IP</span><span class="sxs-lookup"><span data-stu-id="69a33-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-542">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-543">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-543">Description</span></span>

<span data-ttu-id="69a33-544">Ta usługa ponownie inicjuje klienta programu w celu ponownego uruchomienia komputera stanu DHCPv6 i ponownego uruchomienia protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="69a33-545">Nie jest to konieczne, jeśli klient nie uruchomił wcześniej DHPCv6 stanu komputera ani nie przypisał żadnego adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="69a33-546">Adresy zapisane na kliencie DHCPv6 oraz zarejestrowane z wystąpieniem IP są wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="69a33-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="69a33-547">Aplikacja musi nadal uruchamiać klienta DHCPv6 przy użyciu *usługi nx_dhcpv6_start* i rozpocząć żądanie przypisywania adresów IPv6 przez wywołanie *nx_dhcpv6_request_solicit*.</span><span class="sxs-lookup"><span data-stu-id="69a33-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-548">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-548">Input Parameters</span></span>

- <span data-ttu-id="69a33-549">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-550">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-550">Return Values</span></span>

- <span data-ttu-id="69a33-551">Pomyślnie usunięto adres **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="69a33-552">**NX_DHCPV6_ALREADY_STARTED** (0XE91) klient DHCPv6 jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="69a33-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="69a33-553">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-554">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-555">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-555">Allowed From</span></span>

<span data-ttu-id="69a33-556">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-557">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-558">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-558">See Also</span></span>

- <span data-ttu-id="69a33-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="69a33-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="69a33-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="69a33-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="69a33-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="69a33-562">Przetwórz stan potwierdzenia klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-563">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-564">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-564">Description</span></span>

<span data-ttu-id="69a33-565">Ta usługa wysyła żądanie potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="69a33-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="69a33-566">W przypadku otrzymania odpowiedzi z serwera klient DHCPv6 aktualizuje swoje parametry dzierżawy o odebranych danych.</span><span class="sxs-lookup"><span data-stu-id="69a33-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-567">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-567">Input Parameters</span></span>

- <span data-ttu-id="69a33-568">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-569">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-569">Return Values</span></span>

- <span data-ttu-id="69a33-570">Komunikat POTWIERDZAjący **NX_SUCCESS** (0x00) został pomyślnie wysłany i przetworzony</span><span class="sxs-lookup"><span data-stu-id="69a33-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="69a33-571">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-572">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-573">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-573">Allowed From</span></span>

<span data-ttu-id="69a33-574">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-575">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-576">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-576">See Also</span></span>

- <span data-ttu-id="69a33-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="69a33-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="69a33-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="69a33-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="69a33-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="69a33-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="69a33-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="69a33-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="69a33-581">Przetwarzaj stan żądania poinformowania klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-582">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-583">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-583">Description</span></span>

<span data-ttu-id="69a33-584">Ta usługa wysyła komunikat z PROŚBą o powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="69a33-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="69a33-585">W przypadku odebrania odpowiedzi, gdy zostanie odebrana, odpowiedź jest przetwarzana w celu ustalenia, czy serwer udzielił żądania.</span><span class="sxs-lookup"><span data-stu-id="69a33-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="69a33-586">Wystąpienie klienta zostaje następnie zaktualizowane informacjami o serwerze zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="69a33-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-587">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-587">Input Parameters</span></span>

- <span data-ttu-id="69a33-588">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-589">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-589">Return Values</span></span>

- <span data-ttu-id="69a33-590">**NX_SUCCESS** (0x00) komunikat żądania inform został pomyślnie utworzony i przetworzony</span><span class="sxs-lookup"><span data-stu-id="69a33-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="69a33-591">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-592">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-593">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-593">Allowed From</span></span>

<span data-ttu-id="69a33-594">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-595">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-596">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-596">See Also</span></span>

- <span data-ttu-id="69a33-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="69a33-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="69a33-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="69a33-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="69a33-599">Dodaj serwer DNS do żądania opcji protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-600">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-601">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-601">Description</span></span>

<span data-ttu-id="69a33-602">Ta usługa dodaje opcję żądania informacji o serwerze DNS do żądania opcji protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="69a33-603">Jeśli odpowiedź serwera zawiera dane serwera DNS, klient będzie przechowywał serwer DNS, jeśli ma to miejsce.</span><span class="sxs-lookup"><span data-stu-id="69a33-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="69a33-604">Liczba serwerów DNS, które mogą być przechowywane przez klienta, zależy od konfigurowalnej opcji NX_DHCPV6_NUM_DNS_SERVERS której wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="69a33-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-605">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-605">Input Parameters</span></span>

- <span data-ttu-id="69a33-606">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-607">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-607">Return Values</span></span>

- <span data-ttu-id="69a33-608">Opcja serwera DNS **NX_SUCCESS** (0x00) jest dołączona</span><span class="sxs-lookup"><span data-stu-id="69a33-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="69a33-609">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-610">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-611">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-611">Allowed From</span></span>

<span data-ttu-id="69a33-612">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-613">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="69a33-614">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-614">See Also</span></span>

- <span data-ttu-id="69a33-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="69a33-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="69a33-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="69a33-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="69a33-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="69a33-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="69a33-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="69a33-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="69a33-619">Dodaj w pełni kwalifikowaną opcję nazwy domeny do listy żądań opcji</span><span class="sxs-lookup"><span data-stu-id="69a33-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-620">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="69a33-621">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-621">Description</span></span>

<span data-ttu-id="69a33-622">Ta usługa dodaje opcję dodawania w pełni kwalifikowanej nazwy domeny klienta do żądania opcji protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="69a33-623">Dostępne są trzy opcje dla opcji FQDN:</span><span class="sxs-lookup"><span data-stu-id="69a33-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="69a33-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Aktualizowanie mapowania adresów FQDN-IPv6 dla nazwy FQDN i adresów używanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="69a33-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 zaktualizuj mapowanie adresów FQDN-IPv6 dla nazwy FQDN i adresów używanych przez klienta na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="69a33-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="69a33-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Zażądaj, aby serwer nie wykonywał aktualizacji DNS w imieniu klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-627">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-627">Input Parameters</span></span>

- <span data-ttu-id="69a33-628">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-629">**domain_name** Ciąg przechowujący nazwę domeny</span><span class="sxs-lookup"><span data-stu-id="69a33-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="69a33-630">**operacja** Typ opcji FQDN do zastosowania (patrz lista powyżej)</span><span class="sxs-lookup"><span data-stu-id="69a33-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-631">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-631">Return Values</span></span>

- <span data-ttu-id="69a33-632">Opcja nazwy FQDN **NX_SUCCESS** (0x00) jest uwzględniona</span><span class="sxs-lookup"><span data-stu-id="69a33-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="69a33-633">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-634">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-635">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-635">Allowed From</span></span>

<span data-ttu-id="69a33-636">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-637">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="69a33-638">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-638">See Also</span></span>

- <span data-ttu-id="69a33-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="69a33-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="69a33-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="69a33-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="69a33-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="69a33-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="69a33-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="69a33-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="69a33-643">Dodaj opcję nazwy domeny do żądania opcji protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-644">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-645">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-645">Description</span></span>

<span data-ttu-id="69a33-646">Ta usługa dodaje opcję nazwy domeny do żądania opcji w komunikatach żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="69a33-647">Jeśli odpowiedź serwera zawiera dane nazwy domeny, klient będzie przechowywał informacje o nazwie domeny, jeśli rozmiar nazwy domeny mieści się w rozmiarze buforu na potrzeby przechowywania nazwy domeny.</span><span class="sxs-lookup"><span data-stu-id="69a33-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="69a33-648">Ten rozmiar buforu jest konfigurowalną opcją (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) o wartości domyślnej 30 bajtów.</span><span class="sxs-lookup"><span data-stu-id="69a33-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-649">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-649">Input Parameters</span></span>

- <span data-ttu-id="69a33-650">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-651">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-651">Return Values</span></span>

- <span data-ttu-id="69a33-652">**NX_SUCCESS** (0x00) ustawienie opcji nazwy domeny</span><span class="sxs-lookup"><span data-stu-id="69a33-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="69a33-653">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-654">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-655">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-655">Allowed From</span></span>

<span data-ttu-id="69a33-656">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-657">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="69a33-658">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-658">See Also</span></span>

- <span data-ttu-id="69a33-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="69a33-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="69a33-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="69a33-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="69a33-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="69a33-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="69a33-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="69a33-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="69a33-663">Ustaw dane serwera jako opcjonalne żądanie</span><span class="sxs-lookup"><span data-stu-id="69a33-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-664">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-665">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-665">Description</span></span>

<span data-ttu-id="69a33-666">Ta usługa dodaje opcję Informacje o serwerze czasu do żądania opcji komunikatów żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="69a33-667">Jeśli odpowiedź serwera zawiera dane serwera Tim, klient będzie przechowywał serwer czasu, jeśli ma to miejsce.</span><span class="sxs-lookup"><span data-stu-id="69a33-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="69a33-668">Liczba serwerów, które mogą być przechowywane przez klienta, zależy od opcji konfigurowalnej</span><span class="sxs-lookup"><span data-stu-id="69a33-668">The number of time servers the Client can store is determined by the configurable option</span></span>

<span data-ttu-id="69a33-669">NX_DHCPV6_NUM_TIME _SERVERS których wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="69a33-669">NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-670">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-670">Input Parameters</span></span>

- <span data-ttu-id="69a33-671">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-672">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-672">Return Values</span></span>

- <span data-ttu-id="69a33-673">Dodano opcję serwera czasu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="69a33-674">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-675">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-676">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-676">Allowed From</span></span>

<span data-ttu-id="69a33-677">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-678">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="69a33-679">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-679">See Also</span></span>

- <span data-ttu-id="69a33-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="69a33-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="69a33-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="69a33-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="69a33-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="69a33-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="69a33-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="69a33-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="69a33-684">Ustaw dane strefy czasowej jako opcjonalne żądanie</span><span class="sxs-lookup"><span data-stu-id="69a33-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-685">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-686">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-686">Description</span></span>

<span data-ttu-id="69a33-687">Ta usługa dodaje opcję żądania informacji o strefie czasowej do żądania opcji klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="69a33-688">Jeśli odpowiedź serwera zawiera dane strefy czasowej, klient będzie przechowywał informacje o strefie czasowej, jeśli rozmiar strefy czasowej mieści się w rozmiarze buforu do przechowywania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="69a33-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="69a33-689">Ten rozmiar buforu jest konfigurowalną opcją (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) o wartości domyślnej 10 bajtów.</span><span class="sxs-lookup"><span data-stu-id="69a33-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-690">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-690">Input Parameters</span></span>

- <span data-ttu-id="69a33-691">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-692">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-692">Return Values</span></span>

- <span data-ttu-id="69a33-693">Dodano opcję strefy czasowej **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="69a33-694">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-695">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-696">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-696">Allowed From</span></span>

<span data-ttu-id="69a33-697">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-698">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="69a33-699">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-699">See Also</span></span>

- <span data-ttu-id="69a33-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="69a33-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="69a33-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="69a33-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="69a33-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="69a33-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="69a33-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="69a33-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="69a33-704">Wysyłanie komunikatu o ZWOLNIeniu protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-705">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-706">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-706">Description</span></span>

<span data-ttu-id="69a33-707">Ta usługa wysyła komunikat o wersji w sieci klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="69a33-708">Jeśli komunikat został pomyślnie wysłany, zwracany jest stan "powodzenie".</span><span class="sxs-lookup"><span data-stu-id="69a33-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="69a33-709">Pomyślne zakończenie nie oznacza, że klient otrzymał odpowiedź lub że został jeszcze przydzielony adres IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="69a33-710">Zadanie wątku klienta DHCPv6 czeka na odpowiedź z serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="69a33-711">Jeśli zostanie odebrana, sprawdza, czy odpowiedź jest prawidłowa i zapisuje dane w rekordzie klienta.</span><span class="sxs-lookup"><span data-stu-id="69a33-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-712">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-712">Input Parameters</span></span>

- <span data-ttu-id="69a33-713">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-714">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-714">Return Values</span></span>

- <span data-ttu-id="69a33-715">Komunikat o wersji **NX_SUCCESS** (0x00) został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="69a33-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="69a33-716">**NX_DHCPV6_NOT_STARTED** (0xE92) nie uruchomiono zadania klienta protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="69a33-717">Adres **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) nie jest powiązany z klientem</span><span class="sxs-lookup"><span data-stu-id="69a33-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="69a33-718">Nie znaleziono **NX_INVALID_INTERFACE** (0x4C) w tabeli adresów IP</span><span class="sxs-lookup"><span data-stu-id="69a33-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="69a33-719">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-720">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-721">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-721">Allowed From</span></span>

<span data-ttu-id="69a33-722">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-723">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-724">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-724">See Also</span></span>

- <span data-ttu-id="69a33-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="69a33-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="69a33-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="69a33-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="69a33-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="69a33-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="69a33-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="69a33-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="69a33-729">Wyślij komunikat żądania</span><span class="sxs-lookup"><span data-stu-id="69a33-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-730">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-731">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-731">Description</span></span>

<span data-ttu-id="69a33-732">Ta usługa wysyła komunikat żądania w sieci.</span><span class="sxs-lookup"><span data-stu-id="69a33-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="69a33-733">Jeśli komunikat został pomyślnie wysłany, zwracany jest stan "powodzenie".</span><span class="sxs-lookup"><span data-stu-id="69a33-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="69a33-734">Pomyślne zakończenie nie oznacza, że klient otrzymał odpowiedź lub że został jeszcze przydzielony adres IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="69a33-735">Zadanie wątku klienta DHCPv6 czeka na odpowiedź (komunikat ADVERTISE) z serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="69a33-736">Jeśli zostanie on odebrany, sprawdza, czy odpowiedź jest prawidłowa, przechowuje dane w rekordzie klienta i promuje klienta do stanu żądania.</span><span class="sxs-lookup"><span data-stu-id="69a33-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="69a33-737">Jeśli opcja szybkie zatwierdzanie zostanie ustawiona, klient DHCPv6 przejdzie bezpośrednio do stanu powiązanego, Jeśli odbierze prawidłowy komunikat ANONSowania serwera.</span><span class="sxs-lookup"><span data-stu-id="69a33-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="69a33-738">Aby uzyskać więcej informacji, zobacz Opis usługi dla *nx_dhcpv6_request_solicit_rapid* .</span><span class="sxs-lookup"><span data-stu-id="69a33-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-739">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-739">Input Parameters</span></span>

- <span data-ttu-id="69a33-740">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-741">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-741">Return Values</span></span>

- <span data-ttu-id="69a33-742">Komunikat żądania **NX_SUCCESS** (0x00) został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="69a33-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="69a33-743">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-744">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-745">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-745">Allowed From</span></span>

<span data-ttu-id="69a33-746">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-747">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="69a33-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="69a33-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="69a33-749">Wyślij komunikat z PROŚBą o opcję szybkiego zatwierdzania</span><span class="sxs-lookup"><span data-stu-id="69a33-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-750">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-751">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-751">Description</span></span>

<span data-ttu-id="69a33-752">Ta usługa wysyła komunikat żądania w sieci z ustawioną opcją szybkiego zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="69a33-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="69a33-753">Jeśli komunikat został pomyślnie wysłany, zwracany jest stan "powodzenie".</span><span class="sxs-lookup"><span data-stu-id="69a33-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="69a33-754">Pomyślne zakończenie nie oznacza, że klient otrzymał odpowiedź lub że został jeszcze przydzielony adres IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="69a33-755">Zadanie wątku klienta DHCPv6 czeka na odpowiedź (komunikat ADVERTISE) z serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="69a33-756">Jeśli zostanie on odebrany, sprawdza, czy odpowiedź jest prawidłowa, przechowuje dane w rekordzie klienta i promuje klienta do stanu POWIĄZANEgo.</span><span class="sxs-lookup"><span data-stu-id="69a33-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-757">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-757">Input Parameters</span></span>

- <span data-ttu-id="69a33-758">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-759">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-759">Return Values</span></span>

- <span data-ttu-id="69a33-760">Komunikat żądania **NX_SUCCESS** (0x00) został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="69a33-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="69a33-761">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-762">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-763">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-763">Allowed From</span></span>

<span data-ttu-id="69a33-764">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-765">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-766">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-766">See Also</span></span>

- <span data-ttu-id="69a33-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="69a33-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="69a33-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="69a33-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="69a33-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="69a33-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="69a33-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="69a33-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="69a33-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="69a33-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="69a33-772">Wznów zadanie klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-773">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-774">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-774">Description</span></span>

<span data-ttu-id="69a33-775">Ta usługa wznawia zadanie wątku klienta protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="69a33-776">Bieżący stan klienta DHCPv6 zostanie przetworzony (np. powiązano, żądanie)</span><span class="sxs-lookup"><span data-stu-id="69a33-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-777">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-777">Input Parameters</span></span>

- <span data-ttu-id="69a33-778">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-779">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-779">Return Values</span></span>

- <span data-ttu-id="69a33-780">Pomyślnie wznowiono działanie klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="69a33-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="69a33-781">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-782">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-783">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-783">Allowed From</span></span>

<span data-ttu-id="69a33-784">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-785">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-786">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-786">See Also</span></span>

- <span data-ttu-id="69a33-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="69a33-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="69a33-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="69a33-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="69a33-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="69a33-790">nx_dhcpv6_set_ time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="69a33-791">Ustawia czas naliczania w dzierżawie adresu IP klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="69a33-792">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="69a33-793">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-793">Description</span></span>

<span data-ttu-id="69a33-794">Ta usługa ustawia czas naliczania na globalny adres IP klienta, ponieważ został przypisany przez serwer.</span><span class="sxs-lookup"><span data-stu-id="69a33-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="69a33-795">Tego elementu należy używać tylko w przypadku, gdy klient jest aktualnie powiązany z przypisanym adresem IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-796">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-796">Input Parameters</span></span>

- <span data-ttu-id="69a33-797">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="69a33-798">**time_accrued** Czas naliczania dzierżawy adresów IP</span><span class="sxs-lookup"><span data-stu-id="69a33-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-799">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-799">Return Values</span></span>

- <span data-ttu-id="69a33-800">Czas **NX_SUCCESS** (0x00) został pomyślnie ustawiony</span><span class="sxs-lookup"><span data-stu-id="69a33-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="69a33-801">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-802">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-802">Allowed From</span></span>

<span data-ttu-id="69a33-803">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-804">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-805">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-805">See Also</span></span>

- <span data-ttu-id="69a33-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="69a33-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="69a33-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="69a33-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="69a33-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="69a33-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="69a33-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="69a33-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="69a33-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="69a33-811">Uruchom zadanie klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-812">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-813">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-813">Description</span></span>

<span data-ttu-id="69a33-814">Ta usługa uruchamia zadanie klienta DHCPv6 i przygotowuje klienta do uruchomienia protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="69a33-815">Sprawdza, czy wystąpienie klienta ma wystarczające informacje (na przykład identyfikator DUID klienta), tworzy i wiąże gniazdo UDP do wysyłania i otrzymywania komunikatów DHCPv6 oraz uaktywnia czasomierze w celu śledzenia czasu sesji i wygaśnięcia bieżącej dzierżawy protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-816">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-816">Input Parameters</span></span>

- <span data-ttu-id="69a33-817">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-818">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-818">Return Values</span></span>

- <span data-ttu-id="69a33-819">**NX_SUCCESS** (0x00) — pomyślnie uruchomiono klienta</span><span class="sxs-lookup"><span data-stu-id="69a33-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="69a33-820">Klient **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) nie ma wymaganych opcji</span><span class="sxs-lookup"><span data-stu-id="69a33-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="69a33-821">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-822">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-823">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-823">Allowed From</span></span>

<span data-ttu-id="69a33-824">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-825">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-826">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-826">See Also</span></span>

- <span data-ttu-id="69a33-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="69a33-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="69a33-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="69a33-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="69a33-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="69a33-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="69a33-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="69a33-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="69a33-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="69a33-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="69a33-832">Zatrzymaj zadanie klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-833">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-834">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-834">Description</span></span>

<span data-ttu-id="69a33-835">Ta usługa przerywa zadanie klienta protokołu DHCPv6 i czyści liczbę ponownych transmisji, maksymalne interwały retransmisji, wyłącza sesje i czasomierze wygaśnięcia dzierżawy oraz usuwa powiązanie portu gniazda klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="69a33-836">Aby ponownie uruchomić klienta, należy najpierw zatrzymać i opcjonalnie zainicjować klienta przed rozpoczęciem kolejnej sesji z dowolnym serwerem DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="69a33-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="69a33-837">Więcej informacji można znaleźć w sekcji małego przykładu.</span><span class="sxs-lookup"><span data-stu-id="69a33-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-838">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-838">Input Parameters</span></span>

- <span data-ttu-id="69a33-839">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-840">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-840">Return Values</span></span>

- <span data-ttu-id="69a33-841">**NX_SUCCESS** (0X00) klient został pomyślnie zatrzymany</span><span class="sxs-lookup"><span data-stu-id="69a33-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="69a33-842">Wątek klienta **NX_DHCPV6_NOT_STARTED** (0xE92) nie został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="69a33-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="69a33-843">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-844">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="69a33-845">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-845">Allowed From</span></span>

<span data-ttu-id="69a33-846">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-847">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-848">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-848">See Also</span></span>

- <span data-ttu-id="69a33-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="69a33-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="69a33-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="69a33-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="69a33-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="69a33-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="69a33-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="69a33-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="69a33-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="69a33-854">Wstrzymywanie zadania klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="69a33-855">Prototype</span><span class="sxs-lookup"><span data-stu-id="69a33-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="69a33-856">Opis</span><span class="sxs-lookup"><span data-stu-id="69a33-856">Description</span></span>

<span data-ttu-id="69a33-857">Ta usługa zawiesza zadanie klienta DHCPv6 i wszystkie żądania, które były w trakcie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="69a33-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="69a33-858">Czasomierze są dezaktywowane i stan klienta jest ustawiony na Nieuruchomiony.</span><span class="sxs-lookup"><span data-stu-id="69a33-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="69a33-859">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="69a33-859">Input Parameters</span></span>

- <span data-ttu-id="69a33-860">**dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="69a33-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="69a33-861">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="69a33-861">Return Values</span></span>

- <span data-ttu-id="69a33-862">Klient **NX_SUCCESS** (0x00) pomyślnie zawiesił</span><span class="sxs-lookup"><span data-stu-id="69a33-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="69a33-863">Klient **NX_DHCPV6_NOT_STARTED** (0XE92) nie działa, więc nie można go wstrzymać</span><span class="sxs-lookup"><span data-stu-id="69a33-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="69a33-864">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="69a33-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="69a33-865">NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku</span><span class="sxs-lookup"><span data-stu-id="69a33-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="69a33-866">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="69a33-866">Allowed From</span></span>

<span data-ttu-id="69a33-867">Wątki</span><span class="sxs-lookup"><span data-stu-id="69a33-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="69a33-868">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a33-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="69a33-869">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a33-869">See Also</span></span>

- <span data-ttu-id="69a33-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="69a33-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="69a33-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="69a33-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="69a33-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="69a33-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="69a33-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="69a33-873">nx_dhcpv6_stop</span></span>
