---
title: Rozdział 4 — usługi serwera Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług NetX Duo DHCPv6Server Services
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821931"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="a8bd1-103">Rozdział 4 — usługi serwera Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a8bd1-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="a8bd1-104">Ten rozdział zawiera opis wszystkich usług NetX Duo DHCPv6Server (wymienionych poniżej).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="a8bd1-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="a8bd1-106">nx_dhcpv6_server_create *utworzyć ServerInstance protokołu DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="a8bd1-107">nx_dhcpv6_server_delete *usunąć ServerInstance protokołu DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="a8bd1-108">nx_dhcpv6_server_start *uruchomić zadanie serwera DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="a8bd1-109">nx_dhcpv6_server_suspend *Wstrzymywanie zadania serwera DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="a8bd1-110">nx_dhcpv6_server_resume *wznowić przetwarzania klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="a8bd1-111">nx_dhcpv6_server_suspend *wstrzymywanie przetwarzania klienta DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="a8bd1-112">nx_dhcpv6_create_dns_address *ustawić serwer DNS dla żądań opcji*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="a8bd1-113">nx_dhcpv6_create_ip_address_range *utworzyć zakres adresów IP do wydzierżawienia*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="a8bd1-114">nx_dhcpv6_reserve_ip_address_range *Zarezerwuj zakres adresów IP na liście serwerów*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="a8bd1-115">nx_dhcpv6_set_server_duid *ustawić identyfikatora DUID serwera dla pakietów DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="a8bd1-116">nx_dhcpv6_add_ip_address_lease *dodać rekordu dzierżawy do tabeli serwera DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="a8bd1-117">Nx_dhcpv6_retrieve_ip_address_lease *pobrać rekordu dzierżawy adresów IP z tabeli serwera*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="a8bd1-118">nx_dhcpv6_add_client_record *dodać rekordu klienta DHCPv6 do tabeli serwera*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="a8bd1-119">nx_dhcpv6_retrieve_client_record *pobrać rekordu klienta z tabeli serwera*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="a8bd1-120">nx_dhcpv6_server_interface_set *ustawić indeksu interfejsu dla usług Dhcpv6 serwera*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="a8bd1-121">nx_dhcpv6_server_option_request_handler_set *ustawić obsługi żądania opcji*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="a8bd1-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="a8bd1-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="a8bd1-123">Ustawianie serwera DNS sieci</span><span class="sxs-lookup"><span data-stu-id="a8bd1-123">Set the network DNS server</span></span>

<span data-ttu-id="a8bd1-124">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="a8bd1-125">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-125">**Description**</span></span>

<span data-ttu-id="a8bd1-126">Ta usługa ładuje serwer DHCPv6 z adresem serwera DNS dla interfejsu sieciowego protokołu DHCPv6 serwera.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="a8bd1-127">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-127">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-128">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-129">**dns_ipv6_address** Wskaźnik do serwera DNS</span><span class="sxs-lookup"><span data-stu-id="a8bd1-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="a8bd1-130">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-130">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-131">**NX_SUCCESS** (0X00) DNS Serversaved do wystąpienia serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="a8bd1-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) podano nieprawidłowy adres</span><span class="sxs-lookup"><span data-stu-id="a8bd1-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="a8bd1-133">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-134">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-134">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-135">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-135">Application Code</span></span>

<span data-ttu-id="a8bd1-136">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="a8bd1-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="a8bd1-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="a8bd1-138">Tworzenie listy adresów IP serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-138">Create the Server IP address list</span></span>

<span data-ttu-id="a8bd1-139">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="a8bd1-140">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-140">**Description**</span></span>

<span data-ttu-id="a8bd1-141">Ta usługa tworzy listę adresów IP określoną przez początkowe i końcowe adresy zakresu adresów, do którego można przypisać serwer.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="a8bd1-142">Adresy początkowy i końcowy muszą być zgodne z prefiksem adresu interfejsu serwera (musi być na tym samym linku co interfejs protokołu DHCPv6 serwera).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="a8bd1-143">Zwracana jest liczba adresów w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="a8bd1-144">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-144">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-145">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-146">**start_ipv6_address** Początek adresów do dodania</span><span class="sxs-lookup"><span data-stu-id="a8bd1-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="a8bd1-147">**end_ipv6_address** Koniec adresów do dodania</span><span class="sxs-lookup"><span data-stu-id="a8bd1-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="a8bd1-148">\***addresses_added** Dane wyjściowe adresów dodanych</span><span class="sxs-lookup"><span data-stu-id="a8bd1-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="a8bd1-149">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-149">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-150">Pomyślnie utworzono listę adresów IP **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="a8bd1-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) podano nieprawidłowy adres</span><span class="sxs-lookup"><span data-stu-id="a8bd1-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="a8bd1-152">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-153">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-153">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-154">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-154">Application Code</span></span>

<span data-ttu-id="a8bd1-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="a8bd1-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="a8bd1-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="a8bd1-157">Zarezerwuj określony zakres adresów IP</span><span class="sxs-lookup"><span data-stu-id="a8bd1-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="a8bd1-158">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="a8bd1-159">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-159">**Description**</span></span>

<span data-ttu-id="a8bd1-160">Ta usługa rezerwuje zakres adresów IP określony przez adres początkowy i końcowy.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="a8bd1-161">Te adresy muszą znajdować się w obrębie wcześniej utworzonego zakresu adresów IP serwera.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="a8bd1-162">Te adresy nie będą przypisywane do żadnych klientów przez serwer DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="a8bd1-163">Adresy początkowy i końcowy muszą być zgodne z prefiksem adresu interfejsu serwera (musi być w tym samym łączu co serwerowy interfejs sieciowy protokołu DHCPv6).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="a8bd1-164">Zwracana jest liczba adresów w rzeczywistości zarezerwowanej.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="a8bd1-165">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-165">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-166">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-167">**start_ipv6_address** Początek adresów do zarezerwowania</span><span class="sxs-lookup"><span data-stu-id="a8bd1-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="a8bd1-168">**end_ipv6_address** Koniec adresów do zarezerwowania</span><span class="sxs-lookup"><span data-stu-id="a8bd1-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="a8bd1-169">\***addresses_reserved** Liczba zarezerwowanych adresów</span><span class="sxs-lookup"><span data-stu-id="a8bd1-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="a8bd1-170">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-170">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-171">Komunikat o wersji **NX_SUCCESS** (0x00) został pomyślnie utworzony i przetworzony</span><span class="sxs-lookup"><span data-stu-id="a8bd1-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="a8bd1-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) podano nieprawidłowy adres</span><span class="sxs-lookup"><span data-stu-id="a8bd1-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="a8bd1-173">Nie znaleziono adresu początkowego **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) na liście adresów serwera.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="a8bd1-174">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-175">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-175">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-176">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-176">Application Code</span></span>

<span data-ttu-id="a8bd1-177">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="a8bd1-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="a8bd1-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="a8bd1-179">Tworzenie wystąpienia serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="a8bd1-180">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="a8bd1-181">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-181">**Description**</span></span>

<span data-ttu-id="a8bd1-182">Ta usługa tworzy zadanie serwera DHCPv6 z określonym danymi wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="a8bd1-183">Programy obsługi wywołania zwrotnego są opcjonalnymi danymi wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-183">The callback handlers are optional input.</span></span> <span data-ttu-id="a8bd1-184">Wymagane są dane wejściowe wskaźnika stosu, wystąpienia protokołu IP i puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="a8bd1-185">Należy już utworzyć wystąpienie IP i pulę pakietów.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="a8bd1-186">Użytkownik zachęca do wywoływania nx_dhcpv6_server_option_request_handler_set w celu ustawienia obsługi żądania opcji.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="a8bd1-187">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-187">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-188">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-189">**ip_ptr** Wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="a8bd1-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="a8bd1-190">**name_str** Wskaźnik do nazwy serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="a8bd1-191">**packet_pool_ptr** Wskaźnik do puli pakietów serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="a8bd1-192">**stack_ptr** Wskaźnik do pamięci stosu serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="a8bd1-193">**stack_size** Rozmiar pamięci stosu serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="a8bd1-194">**dhcpv6_address_declined_handler** Wskaźnik do programu obsługi komunikatów o odrzuceniu lub zwolnieniu klienta</span><span class="sxs-lookup"><span data-stu-id="a8bd1-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="a8bd1-195">**dhcpv6_option_request_handler** Procedura obsługi opcji żądania wskaźnika do opcji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="a8bd1-196">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-196">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-197">Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="a8bd1-198">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="a8bd1-199">NX_DHCPV6_PARAM_ERROR nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="a8bd1-200">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-200">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-201">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-201">Application Code</span></span>

<span data-ttu-id="a8bd1-202">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="a8bd1-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="a8bd1-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="a8bd1-204">Usuwanie serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-205">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="a8bd1-206">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-206">**Description**</span></span>

<span data-ttu-id="a8bd1-207">Ta usługa usuwa zadanie serwera DHCPv6 i wszystkie żądania, które przetworzył serwer.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="a8bd1-208">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-208">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-209">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-210">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-210">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-211">Pomyślnie usunięto serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="a8bd1-212">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-213">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-213">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-214">Wątki</span><span class="sxs-lookup"><span data-stu-id="a8bd1-214">Threads</span></span>

<span data-ttu-id="a8bd1-215">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="a8bd1-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="a8bd1-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="a8bd1-217">Wznów zadanie serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="a8bd1-218">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="a8bd1-219">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-219">**Description**</span></span>

<span data-ttu-id="a8bd1-220">Ta usługa wznawia zadanie serwera DHCPv6 i wszystkie żądania, które przetworzył serwer.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="a8bd1-221">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-221">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-222">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-223">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-223">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-224">Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="a8bd1-225">Serwer **NX_DHCPV6_ALREADY_STARTED** (0xE91) jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="a8bd1-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="a8bd1-226">**stan** błędu (Variable) ThreadX i NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a8bd1-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="a8bd1-227">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-228">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-228">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-229">Wątki</span><span class="sxs-lookup"><span data-stu-id="a8bd1-229">Threads</span></span>

<span data-ttu-id="a8bd1-230">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="a8bd1-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="a8bd1-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="a8bd1-232">Zawstrzymywanie zadania serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="a8bd1-233">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="a8bd1-234">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-234">**Description**</span></span>

<span data-ttu-id="a8bd1-235">Ta usługa zawiesza zadanie serwera DHCPv6 i wszystkie żądania, które przetworzył serwer.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="a8bd1-236">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-236">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-237">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-238">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-238">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-239">Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="a8bd1-240">Serwer **NX_DHCPV6_NOT_STARTED** (0xE92) nie został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="a8bd1-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="a8bd1-241">**Stan** błędu (Variable) ThreadX i NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a8bd1-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="a8bd1-242">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-243">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-243">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-244">Wątki</span><span class="sxs-lookup"><span data-stu-id="a8bd1-244">Threads</span></span>

<span data-ttu-id="a8bd1-245">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="a8bd1-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="a8bd1-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="a8bd1-247">Uruchamianie zadania serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="a8bd1-248">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="a8bd1-249">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-249">**Description**</span></span>

<span data-ttu-id="a8bd1-250">Ta usługa uruchamia zadanie serwera DHCPv6 i odczytuje serwer, aby przetwarzać żądania aplikacji do otrzymywania komunikatów klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="a8bd1-251">Sprawdza, czy wystąpienie serwera ma wystarczające informacje (serwer DUID), tworzy i wiąże gniazdo UDP do wysyłania i otrzymywania komunikatów DHCPv6 oraz aktywuje czasomierze do śledzenia czasu sesji i wygaśnięcia dzierżawy adresów IP.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-252">Aby można było uruchomić serwer DHCPv6, aplikacja hosta jest odpowiedzialna za tworzenie zakresu adresów IP, z którego serwer może przypisywać adresy IP.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="a8bd1-253">Jest również odpowiedzialny za ustawienie identyfikatora DUID serwera i interfejsu protokołu DHCPv6 (zobacz odpowiednio *nx_dhcpv6_server_duid_set* i *nx_dhcpv6_server_interface_set* .</span><span class="sxs-lookup"><span data-stu-id="a8bd1-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="a8bd1-254">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-254">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-255">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-256">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-256">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-257">Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="a8bd1-258">Serwer **NX_DHCPV6_ALREADY_STARTED** (0xE91) jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="a8bd1-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="a8bd1-259">Serwer **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) nie ma adresów do przypisania do dzierżawy</span><span class="sxs-lookup"><span data-stu-id="a8bd1-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="a8bd1-260">Nie ustawiono globalnego indeksu adresów **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="a8bd1-261">**NX_DHCPV6_NO_SERVER_DUID** (0XE92) nie utworzono identyfikatora DUID serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="a8bd1-262">**stan** błędu (Variable) ThreadX i NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a8bd1-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="a8bd1-263">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-264">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-264">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-265">Wątki</span><span class="sxs-lookup"><span data-stu-id="a8bd1-265">Threads</span></span>

<span data-ttu-id="a8bd1-266">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="a8bd1-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="a8bd1-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="a8bd1-268">Pobierz dzierżawę adresu IP z tabeli serwerów</span><span class="sxs-lookup"><span data-stu-id="a8bd1-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="a8bd1-269">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="a8bd1-270">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-270">**Description**</span></span>

<span data-ttu-id="a8bd1-271">Ta usługa pobiera rekord dzierżawy adresu IP z tabeli serwerów w określonej lokalizacji indeksu tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="a8bd1-272">Można to zrobić przed lub po pobraniu danych rekordu klienta.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="a8bd1-273">Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="a8bd1-274">Nie ma żadnych różnic w kolejności, w jakiej dane dzierżawy adresów IP i dane rekordu klienta są zapisywane w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-275">Nie zaleca się kopiowania danych do lub z tabel serwerowych bez uprzedniego zatrzymywania ani zawieszania serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="a8bd1-276">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-276">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-277">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-278">**table_index** Indeks tabeli do przechowania dzierżawy w</span><span class="sxs-lookup"><span data-stu-id="a8bd1-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="a8bd1-279">**lease_IP_address** Wskaźnik na adres IP dzierżawiony do klienta</span><span class="sxs-lookup"><span data-stu-id="a8bd1-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="a8bd1-280">**T1** Klient zażądał czasu odnowienia</span><span class="sxs-lookup"><span data-stu-id="a8bd1-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="a8bd1-281">**T2** Klient zażądał ponownego powiązania czasu</span><span class="sxs-lookup"><span data-stu-id="a8bd1-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="a8bd1-282">**valid_lifetime** Dzierżawa klienta staje się przestarzała</span><span class="sxs-lookup"><span data-stu-id="a8bd1-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="a8bd1-283">**preferred_lifetime** Dzierżawa klienta jest nieprawidłowa</span><span class="sxs-lookup"><span data-stu-id="a8bd1-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="a8bd1-284">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-284">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-285">Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="a8bd1-286">**NX_DHCPV6_PARAMETER_ERROR** (0XE93) nieprawidłowe dane wejściowe dzierżawy adresów IP</span><span class="sxs-lookup"><span data-stu-id="a8bd1-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="a8bd1-287">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-288">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-288">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-289">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-289">Application code</span></span>

<span data-ttu-id="a8bd1-290">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="a8bd1-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="a8bd1-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="a8bd1-292">Dodawanie dzierżawy adresu IP do tabeli serwerów</span><span class="sxs-lookup"><span data-stu-id="a8bd1-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="a8bd1-293">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="a8bd1-294">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-294">**Description**</span></span>

<span data-ttu-id="a8bd1-295">Ta usługa ładuje dane dzierżawy protokołu IP z poprzedniej sesji serwera DHCPv6 z nietrwałej pamięci do tabeli dzierżawy serwera.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="a8bd1-296">Nie jest to konieczne, jeśli serwer jest uruchomiony po raz pierwszy i nie ma wcześniejszych danych dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="a8bd1-297">W takim przypadku aplikacja hosta musi utworzyć zakres adresów IP na potrzeby przypisywania adresów IP przy użyciu usługi *nx_dhcpv6_create_ip_address_range*.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="a8bd1-298">Dane są wystarczające do odtworzenia rekordu dzierżawy protokołu DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="a8bd1-299">Nie trzeba określać indeksu tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-299">The table index need not be specified.</span></span> <span data-ttu-id="a8bd1-300">W przypadku ustawienia wartości 0xFFFFFFFF (nieskończoność) serwer DHCPv6 znajdzie następne dostępne miejsce, do którego zostaną skopiowane dane.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-301">Przekazywanie danych dzierżawy adresów IP należy wykonać przed przekazaniem rekordów klienta; Oba te elementy należy wykonać przed ponownym uruchomieniem serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="a8bd1-302">Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="a8bd1-303">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-303">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-304">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-305">**table_index** Indeks tabeli do przechowania dzierżawy w</span><span class="sxs-lookup"><span data-stu-id="a8bd1-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="a8bd1-306">**lease_IP_address** Wskaźnik na adres IP dzierżawiony do klienta</span><span class="sxs-lookup"><span data-stu-id="a8bd1-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="a8bd1-307">**T1** Klient zażądał czasu odnowienia</span><span class="sxs-lookup"><span data-stu-id="a8bd1-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="a8bd1-308">**T2** Klient zażądał ponownego powiązania czasu</span><span class="sxs-lookup"><span data-stu-id="a8bd1-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="a8bd1-309">**valid_lifetime** Dzierżawa klienta staje się przestarzała</span><span class="sxs-lookup"><span data-stu-id="a8bd1-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="a8bd1-310">**preferred_lifetime** Dzierżawa klienta jest nieprawidłowa</span><span class="sxs-lookup"><span data-stu-id="a8bd1-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="a8bd1-311">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-311">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-312">Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="a8bd1-313">**NX_DHCPV6_TABLE_FULL** (0XEC4) brak miejsca do uzyskania większej ilości danych dzierżawy \* \*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="a8bd1-314">Dane dzierżawy **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) nie są dostępne w połączeniu z interfejsem DHCPv6 serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="a8bd1-315">**NX_DHCPV6_PARAM_ERROR** (0XE93) nieprawidłowe dane wejściowe dzierżawy adresów IP</span><span class="sxs-lookup"><span data-stu-id="a8bd1-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="a8bd1-316">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-317">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-317">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-318">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-318">Application code</span></span>

<span data-ttu-id="a8bd1-319">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="a8bd1-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="a8bd1-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="a8bd1-321">Dodawanie rekordu klienta do tabeli serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="a8bd1-322">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="a8bd1-323">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-323">**Description**</span></span>

<span data-ttu-id="a8bd1-324">Ta usługa kopiuje dane klienta z nietrwałej pamięci do tabeli serwera po jednym rekordzie w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="a8bd1-325">Jest to konieczne tylko wtedy, gdy serwer jest ponownie uruchamiany i ma dane klienta z poprzedniej sesji w celu przywrócenia z pamięci.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="a8bd1-326">Jeśli serwer nie ma wcześniejszych danych, serwer DHCPv6 zainicjuje tabelę klienta, aby umożliwić Dodawanie rekordów klientów.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="a8bd1-327">Nie trzeba określać indeksu tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="a8bd1-328">W przypadku ustawienia wartości 0xFFFFFFFF (nieskończoność) serwer DHCPv6 zlokalizuje następne dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="a8bd1-329">Serwer DHCPv6 może odtworzyć rekord klienta na podstawie tych danych.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-330">Aplikacja hosta musi przekazać dane dzierżawy IP przed rekordem klienta.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="a8bd1-331">Jest tak dlatego, że wewnętrznie serwer DHCPv6 może przełączać tabele w taki sposób, aby każdy rekord klienta był przyłączony do odpowiadającego mu rekordu dzierżawy adresów IP w odpowiednich tabelach.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="a8bd1-332">Zobacz *nx_dhcpv6_add_ip_address_lease* , aby uzyskać szczegółowe informacje dotyczące przekazywania danych dzierżawy adresów IP z pamięci.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-333">W zależności od typu identyfikatora DUID nie wszystkie dane muszą zostać dostarczone.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="a8bd1-334">Jeśli na przykład klient ma typ identyfikatora DUID przypisany przez dostawcę, może wysłać wartość zero dla parametrów warstwy łącza identyfikatora DUID (adres MAC, typ sprzętu, czas DUID).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="a8bd1-335">Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="a8bd1-336">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-336">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-337">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-338">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-338">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-339">Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="a8bd1-340">**NX_ INVALID_PARAMETERS** (0x4D) nieprawidłowe dane wejściowe bez wskaźnika \* \*</span><span class="sxs-lookup"><span data-stu-id="a8bd1-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="a8bd1-341">**NX_DHCPV6_TABLE_FULL** (0XEC4) nie ma pustych miejsc do dodania innego rekordu klienta</span><span class="sxs-lookup"><span data-stu-id="a8bd1-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="a8bd1-342">W tabeli dzierżawy serwera nie znaleziono adresu przypisanego przez klienta **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="a8bd1-343">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-344">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-344">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-345">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-345">Application code</span></span>

<span data-ttu-id="a8bd1-346">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="a8bd1-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="a8bd1-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="a8bd1-348">Pobieranie rekordu klienta z tabeli serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="a8bd1-349">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="a8bd1-350">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-350">**Description**</span></span>

<span data-ttu-id="a8bd1-351">Ta usługa kopiuje podstawowe dane z tabeli rekordów klientów serwera dla magazynu do pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="a8bd1-352">Serwer może odtworzyć odpowiedni rekord klienta z takich danych w procesie odwrotnym (przekazywanie danych do tabeli serwera).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="a8bd1-353">Bez względu na typ identyfikatora DUID, żaden ze wskaźników nie może być wskaźnikami ZEROWYmi; dane są inicjowane do zera dla wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="a8bd1-354">Na przykład, jeśli typ identyfikatora DUID klienta to warstwa łącza wraz z czasem, numer dostawcy jest zwracany jako zero, a prywatny identyfikator jest ciągiem pustym.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="a8bd1-355">Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="a8bd1-356">Nie ma żadnych różnic w kolejności, w jakiej dane dzierżawy adresów IP i dane rekordu klienta są zapisywane w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-357">Nie zaleca się kopiowania danych do lub z tabel serwerowych bez uprzedniego zatrzymywania ani zawieszania serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="a8bd1-358">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-358">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-359">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-360">**table_index** Indeksowanie w tabeli klienta serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="a8bd1-361">**message_xid** Identyfikator transakcji serwera klienta</span><span class="sxs-lookup"><span data-stu-id="a8bd1-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="a8bd1-362">**client_address** Adres IPv6 wydzierżawiony do klienta</span><span class="sxs-lookup"><span data-stu-id="a8bd1-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="a8bd1-363">**client_state** Stan protokołu DHCPv6 klienta (np. powiązane)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="a8bd1-364">**IP_lease_time_accrued** Czas wygaśnięcia dzierżawy jest już **dhcpv6_server_ptr** wskaźnikiem do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-365">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="a8bd1-366">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-366">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-367">Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="a8bd1-368">**NX_DHCPV6_INVALID_DUID** (0xECC) — nieprawidłowe lub niespójne dane identyfikatora DUID</span><span class="sxs-lookup"><span data-stu-id="a8bd1-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="a8bd1-369">**NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="a8bd1-370">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="a8bd1-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="a8bd1-371">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-371">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-372">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-372">Application code</span></span>

<span data-ttu-id="a8bd1-373">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="a8bd1-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="a8bd1-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="a8bd1-375">Indeks interfejsu setthe dla interfejsu protokołu DHCPv6 serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="a8bd1-376">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="a8bd1-377">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-377">**Description**</span></span>

<span data-ttu-id="a8bd1-378">Ta usługa ustawia interfejs sieciowy, na którym serwer DHCPv6 obsługuje żądania klientów DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="a8bd1-379">Nie w przypadku wersji NetX Duo, które nie obsługują wielodostępności, wartość interfejsu jest domyślnie równa zero.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="a8bd1-380">Globalny indeks adresów jest potrzebny do uzyskania adresu globalnego serwera w interfejsie DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="a8bd1-381">Jest ona używana przez logikę protokołu DHCPv6 do zapewnienia, że adresy dzierżaw i inne dane protokołu DHCPv6 są połączone z serwerem DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="a8bd1-382">Ta funkcja musi zostać wywołana przed uruchomieniem serwera DHCPv6, nawet w przypadku aplikacji na pojedynczych urządzeniach z systemem lub bez pomocy technicznej wieloznacznej.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="a8bd1-383">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-383">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-384">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-385">**iface_index** Interfejs serwera DHCPv6 serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="a8bd1-386">**ga_address_index** Indeks adresu globalnego serwera w tabeli adresów IP serwera</span><span class="sxs-lookup"><span data-stu-id="a8bd1-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="a8bd1-387">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-387">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-388">Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="a8bd1-389">Interfejs **NX_INVALID_INTERFACE** (0x4C) nie istnieje</span><span class="sxs-lookup"><span data-stu-id="a8bd1-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="a8bd1-390">Indeks globalny NX_NO_INTERFACE_ADDRESS (0x50) przekracza maksymalne adresy IPv6 (NX_MAX_IPV6_ADDRESSES) wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="a8bd1-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="a8bd1-391">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-392">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-392">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-393">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-393">Application code</span></span>

<span data-ttu-id="a8bd1-394">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="a8bd1-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="a8bd1-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="a8bd1-396">Ustaw identyfikator DUID serwera dla pakietów DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="a8bd1-397">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="a8bd1-398">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-398">**Description**</span></span>

<span data-ttu-id="a8bd1-399">Ta usługa ustawia identyfikator DUID serwera i musi być wywoływana przed uruchomieniem serwera przez aplikację hosta.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="a8bd1-400">W przypadku typów identyfikatora DUID warstwy łącza i łącza aplikacja hosta musi podawać dane typu sprzętu i adresu MAC.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="a8bd1-401">W przypadku DUIDs warstwy łącza, wskaźnik czasu musi wskazywać prawidłowy czas.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="a8bd1-402">Liczba sekund od 1 stycznia 2000 jest typową wartością inicjatora.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="a8bd1-403">Jeśli typ identyfikatora DUID serwera to Enterprise, typ przypisany przez dostawcę, identyfikator DUID zostanie utworzony na podstawie opcji konfigurowalnych przez użytkownika NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID i NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, a wartości czasu i adresu MAC można ustawić na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="a8bd1-404">Jest on odpowiedzialny za zapisywanie parametrów identyfikatora DUID serwera w pamięci nieulotnej, tak że używa tego samego identyfikatora DUID w komunikatach dla klientów między ponownymi uruchomieniami.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="a8bd1-405">Jest to wymaganie protokołu DHCPv6 (RFC 3315).</span><span class="sxs-lookup"><span data-stu-id="a8bd1-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="a8bd1-406">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-406">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-407">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-408">**duid_type** Typ identyfikatora DUID serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="a8bd1-409">**hardware_type** Typ sprzętu (np. Ethernet)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="a8bd1-410">**mac_address_msw** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-411">**mac_address_lsw** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-412">**czas** Wartość czasu dla identyfikatora DUID</span><span class="sxs-lookup"><span data-stu-id="a8bd1-412">**time** Time value for DUID</span></span>

<span data-ttu-id="a8bd1-413">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-413">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-414">Pomyślnie wstrzymano serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="a8bd1-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) nieznany lub nieobsługiwany typ identyfikatora DUID</span><span class="sxs-lookup"><span data-stu-id="a8bd1-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="a8bd1-416">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="a8bd1-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="a8bd1-417">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-418">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-418">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-419">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-419">Application code</span></span>

<span data-ttu-id="a8bd1-420">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="a8bd1-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="a8bd1-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="a8bd1-422">Ustaw obsługę żądania opcji dla wystąpienia serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="a8bd1-423">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="a8bd1-424">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-424">**Description**</span></span>

<span data-ttu-id="a8bd1-425">Ta usługa ustawia procedurę obsługi żądania opcji rozszerzonej serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a8bd1-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="a8bd1-426">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-426">**Input Parameters**</span></span>

- <span data-ttu-id="a8bd1-427">**dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6</span><span class="sxs-lookup"><span data-stu-id="a8bd1-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="a8bd1-428">**dhcpv6_option_request_handler_extended** Wskaźnik do procedury obsługi żądania opcji rozszerzonych</span><span class="sxs-lookup"><span data-stu-id="a8bd1-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="a8bd1-429">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-429">**Return Values**</span></span>

- <span data-ttu-id="a8bd1-430">Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a8bd1-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="a8bd1-431">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a8bd1-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="a8bd1-432">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-432">**Allowed From**</span></span>

<span data-ttu-id="a8bd1-433">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8bd1-433">Application Code</span></span>

<span data-ttu-id="a8bd1-434">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a8bd1-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```