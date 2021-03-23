---
title: Rozdział 3 — Opis usług serwera DHCP w systemie Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług serwera DHCP w programie NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822009"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a><span data-ttu-id="5c83d-103">Rozdział 3 — Opis usług serwera DHCP w systemie Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="5c83d-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Server Services</span></span>

<span data-ttu-id="5c83d-104">Ten rozdział zawiera opis wszystkich usług serwera DHCP w programie NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="5c83d-104">This chapter contains a description of all NetX Duo DHCP Server services (listed below) in alphabetic order.</span></span>

> [!NOTE]
> <span data-ttu-id="5c83d-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5c83d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_dhcp_server-create"></a><span data-ttu-id="5c83d-106">nx_dhcp_server Utwórz</span><span class="sxs-lookup"><span data-stu-id="5c83d-106">nx_dhcp_server create</span></span>

<span data-ttu-id="5c83d-107">Tworzenie wystąpienia serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="5c83d-107">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-108">Prototype</span></span>

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="5c83d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-109">Description</span></span>

<span data-ttu-id="5c83d-110">Ta usługa tworzy wystąpienie serwera DHCP z wcześniej utworzonym wystąpieniem adresu IP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-110">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5c83d-111">Aplikacja musi upewnić się, że Pula pakietów utworzona dla usługi IP Create ma minimalny 548-bajtowy ładunek, bez uwzględniania nagłówków UDP, IP i Ethernet.</span><span class="sxs-lookup"><span data-stu-id="5c83d-111">The application must make sure the packet pool created for the IP create service has a minimum 548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-112">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-112">Input Parameters</span></span>

- <span data-ttu-id="5c83d-113">**dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-113">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="5c83d-114">**ip_ptr** Wskaźnik do wystąpienia IP serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-114">**ip_ptr** Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="5c83d-115">**stack_ptr** Wskaźnik lokalizacji serwera DHCP na stosie.</span><span class="sxs-lookup"><span data-stu-id="5c83d-115">**stack_ptr** Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="5c83d-116">**Stack_size rozmiar input_address_list stosu serwera DHCP** do listy adresów IP serwera</span><span class="sxs-lookup"><span data-stu-id="5c83d-116">**stack_size Size of DHCP Server stack** input_address_list Pointer to Server’s list of IP addresses</span></span>
- <span data-ttu-id="5c83d-117">**Name_ptr wskaźnik do nazwy serwera dhcp** packet_pool_ptr wskaźnik do puli pakietów serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="5c83d-117">**name_ptr Pointer to DHCP Server name** packet_pool_ptr Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-118">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-118">Return Values</span></span>

- <span data-ttu-id="5c83d-119">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-119">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="5c83d-120">Wystąpił zbyt mały błąd ładunku pakietu **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9)</span><span class="sxs-lookup"><span data-stu-id="5c83d-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="5c83d-121">Lista opcji serwera **NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) jest pusta</span><span class="sxs-lookup"><span data-stu-id="5c83d-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Server option list is empty</span></span>
- <span data-ttu-id="5c83d-122">NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="5c83d-122">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="5c83d-123">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="5c83d-123">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="5c83d-124">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-124">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-125">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-125">Allowed From</span></span>

<span data-ttu-id="5c83d-126">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="5c83d-126">Application</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-127">Example</span></span>

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="5c83d-128">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="5c83d-128">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="5c83d-129">Tworzenie puli adresów IP</span><span class="sxs-lookup"><span data-stu-id="5c83d-129">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-130">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-130">Prototype</span></span>

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="5c83d-131">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-131">Description</span></span>

<span data-ttu-id="5c83d-132">Ta usługa tworzy specyficzną dla interfejsu sieciowego pulę dostępnych adresów IP dla określonego serwera DHCP do przypisania.</span><span class="sxs-lookup"><span data-stu-id="5c83d-132">This service creates a network interface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="5c83d-133">Początkowe i końcowe adresy IP muszą być zgodne z określonym interfejsem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="5c83d-133">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="5c83d-134">Rzeczywista liczba dodanych adresów IP może być mniejsza od łącznego adresu, jeśli lista adresów IP nie jest wystarczająco duża (która jest ustawiana w *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametr konfigurowalny przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="5c83d-134">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-135">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-135">Input Parameters</span></span>

- <span data-ttu-id="5c83d-136">**dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-136">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="5c83d-137">**iface_index** Indeks odpowiadający interfejsowi sieciowemu</span><span class="sxs-lookup"><span data-stu-id="5c83d-137">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="5c83d-138">**start_ip_address** Pierwszy dostępny adres IP</span><span class="sxs-lookup"><span data-stu-id="5c83d-138">**start_ip_address** First available IP address</span></span>
- <span data-ttu-id="5c83d-139">**end_ip_address** Ostatni dostępny adres IP</span><span class="sxs-lookup"><span data-stu-id="5c83d-139">**end_ip_address** Last of the available IP address</span></span>
- <span data-ttu-id="5c83d-140">**addresses_added** Liczba adresów IP dodanych do listy</span><span class="sxs-lookup"><span data-stu-id="5c83d-140">**addresses_added** Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-141">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-141">Return Values</span></span>

- <span data-ttu-id="5c83d-142">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-142">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="5c83d-143">Indeks **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xa1) nie jest zgodny z adresami</span><span class="sxs-lookup"><span data-stu-id="5c83d-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="5c83d-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0X99) nieprawidłowe dane wejściowe adresu</span><span class="sxs-lookup"><span data-stu-id="5c83d-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Invalid address input</span></span>
- <span data-ttu-id="5c83d-145">Adresy początkowe/końcowe NX_DHCP_INVALID_IP_ADDRESS (0x9B) illogical</span><span class="sxs-lookup"><span data-stu-id="5c83d-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="5c83d-146">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-146">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-147">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-147">Allowed From</span></span>

<span data-ttu-id="5c83d-148">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="5c83d-148">Application</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-149">Example</span></span>

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="5c83d-150">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="5c83d-150">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="5c83d-151">Usuń rekord klienta z bazy danych serwera</span><span class="sxs-lookup"><span data-stu-id="5c83d-151">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-152">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-152">Prototype</span></span>

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="5c83d-153">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-153">Description</span></span>

<span data-ttu-id="5c83d-154">Ta usługa czyści rekord klienta z bazy danych serwera.</span><span class="sxs-lookup"><span data-stu-id="5c83d-154">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-155">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-155">Input Parameters</span></span>

- <span data-ttu-id="5c83d-156">**dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-156">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="5c83d-157">**dhcp_client_ptr wskaźnika do usuwania klienta DHCP**</span><span class="sxs-lookup"><span data-stu-id="5c83d-157">**dhcp_client_ptr Pointer to DHCP Client to remove**</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-158">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-158">Return Values</span></span>

- <span data-ttu-id="5c83d-159">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-159">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="5c83d-160">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-160">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="5c83d-161">NX_CALLER_ERROR (0x11) nie wywołujący wątku usługi</span><span class="sxs-lookup"><span data-stu-id="5c83d-161">NX_CALLER_ERROR (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-162">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-162">Allowed From</span></span>

<span data-ttu-id="5c83d-163">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="5c83d-163">Application</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-164">Example</span></span>

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="5c83d-165">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="5c83d-165">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="5c83d-166">Ustawianie parametrów sieci dla opcji DHCP</span><span class="sxs-lookup"><span data-stu-id="5c83d-166">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-167">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="5c83d-168">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-168">Description</span></span>

<span data-ttu-id="5c83d-169">Ta usługa ustawia wartości domyślne dla parametrów krytycznych dla sieci dla określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5c83d-169">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="5c83d-170">Serwer DHCP będzie uwzględniał te opcje w swojej OFERcie i ACK odpowiedzi do klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-170">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="5c83d-171">Jeśli zestaw parametrów interfejsu hosta, na którym jest uruchomiony serwer DHCP, parametry te są ustawiane domyślnie w następujący sposób: router jest ustawiony na bramę interfejsu podstawowego serwera DHCP, adres serwera DNS do samego serwera DHCP, a maska podsieci, która jest taka sama jak interfejs serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-171">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-172">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-172">Input Parameters</span></span>

- <span data-ttu-id="5c83d-173">**dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-173">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="5c83d-174">**iface_index** Indeks odpowiadający interfejsowi sieciowemu</span><span class="sxs-lookup"><span data-stu-id="5c83d-174">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="5c83d-175">**subnet_mask** Maska podsieci dla sieci klienta</span><span class="sxs-lookup"><span data-stu-id="5c83d-175">**subnet_mask** Subnet mask for Client network</span></span>
- <span data-ttu-id="5c83d-176">**default_gateway_address** Adres IP routera klienta</span><span class="sxs-lookup"><span data-stu-id="5c83d-176">**default_gateway_address** Client’s router IP address</span></span>
- <span data-ttu-id="5c83d-177">**dns_server_address** Serwer DNS dla sieci klienta</span><span class="sxs-lookup"><span data-stu-id="5c83d-177">**dns_server_address** DNS server for Client’s network</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-178">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-178">Return Values</span></span>

- <span data-ttu-id="5c83d-179">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-179">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="5c83d-180">Indeks **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xa1) nie jest zgodny z adresami</span><span class="sxs-lookup"><span data-stu-id="5c83d-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="5c83d-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0XA3) nieprawidłowe parametry sieci</span><span class="sxs-lookup"><span data-stu-id="5c83d-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="5c83d-182">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-182">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-183">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-183">Allowed From</span></span>

<span data-ttu-id="5c83d-184">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="5c83d-184">Application</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-185">Example</span></span>

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="5c83d-186">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="5c83d-186">nx_dhcp_server_delete</span></span>

<span data-ttu-id="5c83d-187">Usuwanie wystąpienia serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="5c83d-187">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-188">Prototype</span></span>

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="5c83d-189">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-189">Description</span></span>

<span data-ttu-id="5c83d-190">Ta usługa usuwa wcześniej utworzone wystąpienie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-190">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-191">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-191">Input Parameters</span></span>

- <span data-ttu-id="5c83d-192">**dhcp_ptr** Wskaźnik do wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-192">**dhcp_ptr** Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-193">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-193">Return Values</span></span>

- <span data-ttu-id="5c83d-194">**NX_SUCCESS** (0X00) pomyślne usunięcie serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-194">**NX_SUCCESS** (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="5c83d-195">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-195">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="5c83d-196">NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="5c83d-196">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="5c83d-197">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="5c83d-197">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-198">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-198">Allowed From</span></span>

<span data-ttu-id="5c83d-199">Wątki</span><span class="sxs-lookup"><span data-stu-id="5c83d-199">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-200">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-200">Example</span></span>

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="5c83d-201">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="5c83d-201">nx_dhcp_server_start</span></span>

<span data-ttu-id="5c83d-202">Uruchamianie przetwarzania serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="5c83d-202">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-203">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-203">Prototype</span></span>

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="5c83d-204">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-204">Description</span></span>

<span data-ttu-id="5c83d-205">Ta usługa uruchamia przetwarzanie serwera DHCP, w tym tworzenie gniazda UDP serwera, powiązanie portu DHCP i oczekiwanie na odbieranie żądań DHCP klienta.</span><span class="sxs-lookup"><span data-stu-id="5c83d-205">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-206">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-206">Input Parameters</span></span>

- <span data-ttu-id="5c83d-207">**dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-207">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-208">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-208">Return Values</span></span>

- <span data-ttu-id="5c83d-209">**NX_SUCCESS** (0X00) pomyślne uruchomienie serwera.</span><span class="sxs-lookup"><span data-stu-id="5c83d-209">**NX_SUCCESS** (0x00) Successful Server start.</span></span>
- <span data-ttu-id="5c83d-210">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP jest już uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5c83d-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="5c83d-211">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-211">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="5c83d-212">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="5c83d-212">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="5c83d-213">NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="5c83d-213">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-214">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-214">Allowed From</span></span>

<span data-ttu-id="5c83d-215">Wątki</span><span class="sxs-lookup"><span data-stu-id="5c83d-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-216">Example</span></span>

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="5c83d-217">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="5c83d-217">nx_dhcp_server_stop</span></span>

<span data-ttu-id="5c83d-218">Powoduje zatrzymanie przetwarzania serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="5c83d-218">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="5c83d-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="5c83d-219">Prototype</span></span>

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="5c83d-220">Opis</span><span class="sxs-lookup"><span data-stu-id="5c83d-220">Description</span></span>

<span data-ttu-id="5c83d-221">Ta usługa umożliwia zatrzymanie przetwarzania serwera DHCP, który obejmuje otrzymywanie żądań klientów DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-221">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5c83d-222">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c83d-222">Input Parameters</span></span>

- <span data-ttu-id="5c83d-223">**dhcp_ptr** Wskaźnik do wystąpienia serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-223">**dhcp_ptr** Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5c83d-224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="5c83d-224">Return Values</span></span>

- <span data-ttu-id="5c83d-225">**NX_SUCCESS** (0X00) pomyślne zatrzymanie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="5c83d-225">**NX_SUCCESS** (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="5c83d-226">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP jest już uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5c83d-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="5c83d-227">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="5c83d-227">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="5c83d-228">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="5c83d-228">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="5c83d-229">NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="5c83d-229">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5c83d-230">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="5c83d-230">Allowed From</span></span>

<span data-ttu-id="5c83d-231">Wątki</span><span class="sxs-lookup"><span data-stu-id="5c83d-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5c83d-232">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c83d-232">Example</span></span>

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
