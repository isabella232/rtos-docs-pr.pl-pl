---
title: Rozdział 3 — Opis usług serwera DHCP w usłudze Azure RTO NetX
description: Ten rozdział zawiera opis wszystkich usług serwera DHCP usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822687"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="ec1f3-103">Rozdział 3 — Opis usług serwera DHCP w usłudze Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="ec1f3-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="ec1f3-104">Ten rozdział zawiera opis wszystkich NetX usługi serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="ec1f3-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ec1f3-106">**nx_dhcp_server_create**: *Tworzenie wystąpienia serwera DHCP*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="ec1f3-107">**nx_dhcp_set_interface_network_parameters**: *Ustaw opcje serwera DHCP dla krytycznych parametrów sieciowych dla określonego interfejsu*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="ec1f3-108">**nx_dhcp_create_server_ip_address_list**: *Utwórz pulę dostępnych adresów IP do przypisania do interfejsu klientów DHCP*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="ec1f3-109">**nx_dhcp_clear_client_record**: *Usuwanie rekordu klienta w bazie danych serwera*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="ec1f3-110">**nx_dhcp_server_delete**: *usuwanie wystąpienia dhcpserver*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="ec1f3-111">**nx_dhcp_server_start**: *Uruchamianie lub wznawianie przetwarzania serwera DHCP*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="ec1f3-112">**nx_dhcp_server_stop**: *Zatrzymywanie przetwarzania serwera DHCP*</span><span class="sxs-lookup"><span data-stu-id="ec1f3-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="ec1f3-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="ec1f3-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="ec1f3-114">Tworzenie wystąpienia serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-115">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ec1f3-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-116">Description</span></span>

<span data-ttu-id="ec1f3-117">Ta usługa tworzy wystąpienie serwera DHCP z wcześniej utworzonym wystąpieniem adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec1f3-118">Aplikacja musi upewnić się, że Pula pakietów utworzona dla usługi IP Create ma ładunek bajtów minimum548, bez uwzględniania nagłówków UDP, IP i Ethernet.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-119">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-119">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-120">**dhcp_ptr**: wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="ec1f3-121">**ip_ptr**: wskaźnik do wystąpienia IP serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="ec1f3-122">**stack_ptr**: wskaźnik lokalizacji serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="ec1f3-123">**stack_size**: rozmiar stosu serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="ec1f3-124">**input_address_list**: wskaźnik do listy adresów IP serwera</span><span class="sxs-lookup"><span data-stu-id="ec1f3-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="ec1f3-125">**name_ptr**: wskaźnik do nazwy serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="ec1f3-126">**packet_pool_ptr**: wskaźnik do puli pakietów serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-127">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-127">Return Values</span></span>

- <span data-ttu-id="ec1f3-128">**NX_SUCCESS**: (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ec1f3-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) zbyt mały błąd ładunku pakietu</span><span class="sxs-lookup"><span data-stu-id="ec1f3-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="ec1f3-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) lista opcji serwera jest pusta</span><span class="sxs-lookup"><span data-stu-id="ec1f3-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="ec1f3-131">NX_DHCP_PARAMETER_ERROR: (0x92) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ec1f3-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="ec1f3-132">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ec1f3-133">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-134">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-134">Allowed From</span></span>

<span data-ttu-id="ec1f3-135">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="ec1f3-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="ec1f3-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="ec1f3-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="ec1f3-138">Tworzenie puli adresów IP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-139">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="ec1f3-140">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-140">Description</span></span>

<span data-ttu-id="ec1f3-141">Ta usługa tworzy interfejsu sieciowego określoną pulę dostępnych adresów IP dla określonego serwera DHCP do przypisania.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="ec1f3-142">Początkowe i końcowe adresy IP muszą być zgodne z określonym interfejsem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="ec1f3-143">Rzeczywista liczba dodanych adresów IP może być mniejsza od łącznego adresu, jeśli lista adresów IP nie jest wystarczająco duża (która jest ustawiana w *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametr konfigurowalny przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="ec1f3-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-144">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-144">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-145">**dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="ec1f3-146">**iface_index**: indeks odpowiadający interfejsowi sieciowemu</span><span class="sxs-lookup"><span data-stu-id="ec1f3-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="ec1f3-147">**start_ip_address**: pierwszy dostępny adres IP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="ec1f3-148">**end_ip_address**: ostatni dostępny adres IP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="ec1f3-149">**addresses_added**: liczba adresów IP dodanych do listy</span><span class="sxs-lookup"><span data-stu-id="ec1f3-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-150">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-150">Return Values</span></span>

- <span data-ttu-id="ec1f3-151">**NX_SUCCESS**: (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ec1f3-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0XA1) indeks nie jest zgodny z adresami</span><span class="sxs-lookup"><span data-stu-id="ec1f3-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="ec1f3-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0X99) nieprawidłowe dane wejściowe adresu</span><span class="sxs-lookup"><span data-stu-id="ec1f3-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="ec1f3-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) illogical adresy Start/End</span><span class="sxs-lookup"><span data-stu-id="ec1f3-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="ec1f3-155">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-156">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-156">Allowed From</span></span>

<span data-ttu-id="ec1f3-157">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="ec1f3-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="ec1f3-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="ec1f3-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="ec1f3-160">Usuń rekord klienta z bazy danych serwera</span><span class="sxs-lookup"><span data-stu-id="ec1f3-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="ec1f3-162">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-162">Description</span></span>

<span data-ttu-id="ec1f3-163">Ta usługa czyści rekord klienta z bazy danych serwera.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-164">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-164">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-165">**dhcp_ptr**: wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="ec1f3-166">**dhcp_client_ptr**: wskaźnik do usunięcia klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-167">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-167">Return Values</span></span>

- <span data-ttu-id="ec1f3-168">**NX_SUCCESS**: (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ec1f3-169">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ec1f3-170">NX_CALLER_ERROR: (0x11) nie wywołujący wątku usługi</span><span class="sxs-lookup"><span data-stu-id="ec1f3-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-171">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-171">Allowed From</span></span>

<span data-ttu-id="ec1f3-172">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="ec1f3-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-173">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="ec1f3-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="ec1f3-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="ec1f3-175">Ustawianie parametrów sieci dla opcji DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-176">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="ec1f3-177">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-177">Description</span></span>

<span data-ttu-id="ec1f3-178">Ta usługa ustawia wartości domyślne dla parametrów krytycznych dla sieci dla określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="ec1f3-179">Serwer DHCP będzie uwzględniał te opcje w swojej OFERcie i ACK odpowiedzi do klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="ec1f3-180">Jeśli zestaw parametrów interfejsu hosta, na którym jest uruchomiony serwer DHCP, parametry te są ustawiane domyślnie w następujący sposób: router jest ustawiony na bramę interfejsu podstawowego serwera DHCP, adres serwera DNS do samego serwera DHCP, a maska podsieci, która jest taka sama jak interfejs serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-181">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-181">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-182">**dhcp_ptr**: wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="ec1f3-183">**iface_index**: indeks odpowiadający interfejsowi sieciowemu</span><span class="sxs-lookup"><span data-stu-id="ec1f3-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="ec1f3-184">**subnet_mask**: Maska podsieci dla sieci klienta</span><span class="sxs-lookup"><span data-stu-id="ec1f3-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="ec1f3-185">**default_gateway_address**: adres IP routera klienta</span><span class="sxs-lookup"><span data-stu-id="ec1f3-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="ec1f3-186">**dns_server_address**: serwer DNS dla sieci klienta</span><span class="sxs-lookup"><span data-stu-id="ec1f3-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-187">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-187">Return Values</span></span>

- <span data-ttu-id="ec1f3-188">**NX_SUCCESS**: (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ec1f3-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0XA1) indeks nie jest zgodny z adresami</span><span class="sxs-lookup"><span data-stu-id="ec1f3-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="ec1f3-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0XA3) nieprawidłowe parametry sieci</span><span class="sxs-lookup"><span data-stu-id="ec1f3-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="ec1f3-191">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-192">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-192">Allowed From</span></span>

<span data-ttu-id="ec1f3-193">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="ec1f3-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-194">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="ec1f3-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="ec1f3-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="ec1f3-196">Usuwanie wystąpienia serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-197">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec1f3-198">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-198">Description</span></span>

<span data-ttu-id="ec1f3-199">Ta usługa usuwa wcześniej utworzone wystąpienie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-200">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-200">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-201">**dhcp_ptr**: wskaźnik do wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-202">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-202">Return Values</span></span>

- <span data-ttu-id="ec1f3-203">**NX_SUCCESS**: (0X00) pomyślne usunięcie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="ec1f3-204">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ec1f3-205">NX_DHCP_PARAMETER_ERROR: (0x92) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ec1f3-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="ec1f3-206">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-207">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-207">Allowed From</span></span>

<span data-ttu-id="ec1f3-208">Wątki</span><span class="sxs-lookup"><span data-stu-id="ec1f3-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-209">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="ec1f3-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="ec1f3-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="ec1f3-211">Uruchamianie przetwarzania serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-212">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec1f3-213">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-213">Description</span></span>

<span data-ttu-id="ec1f3-214">Ta usługa uruchamia przetwarzanie serwera DHCP, w tym tworzenie gniazda UDP serwera, powiązanie portu DHCP i oczekiwanie na odbieranie żądań DHCP klienta.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-215">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-215">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-216">**dhcp_ptr**: wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-217">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-217">Return Values</span></span>

- <span data-ttu-id="ec1f3-218">**NX_SUCCESS**: (0X00) pomyślne uruchomienie serwera.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="ec1f3-219">**NX_DHCP_ALREADY_STARTED**: (0X93) usługa DHCP jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ec1f3-220">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ec1f3-221">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ec1f3-222">NX_DHCP_PARAMETER_ERROR: (0x92) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ec1f3-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-223">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-223">Allowed From</span></span>

<span data-ttu-id="ec1f3-224">Wątki</span><span class="sxs-lookup"><span data-stu-id="ec1f3-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-225">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="ec1f3-226">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec1f3-226">See Also</span></span>

<span data-ttu-id="ec1f3-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="ec1f3-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="ec1f3-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="ec1f3-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="ec1f3-229">Powoduje zatrzymanie przetwarzania serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="ec1f3-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ec1f3-230">Prototype</span><span class="sxs-lookup"><span data-stu-id="ec1f3-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec1f3-231">Opis</span><span class="sxs-lookup"><span data-stu-id="ec1f3-231">Description</span></span>

<span data-ttu-id="ec1f3-232">Ta usługa umożliwia zatrzymanie przetwarzania serwera DHCP, który obejmuje otrzymywanie żądań klientów DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec1f3-233">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-233">Input Parameters</span></span>

- <span data-ttu-id="ec1f3-234">**dhcp_ptr**: wskaźnik do wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec1f3-235">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ec1f3-235">Return Values</span></span>

- <span data-ttu-id="ec1f3-236">**NX_SUCCESS**: (0X00) pomyślne zatrzymanie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="ec1f3-237">**NX_DHCP_ALREADY_STARTED**: (0X93) usługa DHCP jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ec1f3-238">NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ec1f3-239">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ec1f3-240">NX_DHCP_PARAMETER_ERROR: (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec1f3-241">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ec1f3-241">Allowed From</span></span>

<span data-ttu-id="ec1f3-242">Wątki</span><span class="sxs-lookup"><span data-stu-id="ec1f3-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec1f3-243">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1f3-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
