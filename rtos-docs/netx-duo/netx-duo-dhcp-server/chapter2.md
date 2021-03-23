---
title: Rozdział 2 — Instalowanie i korzystanie z serwera DHCP usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika DHCP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 201e8b7e245539c1780ace4c3af4bc063a8485b3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822015"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-dhcp-server"></a><span data-ttu-id="83b2c-103">Rozdział 2 — Instalowanie i korzystanie z serwera DHCP usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-103">Chapter 2 - Installation and use of the Azure RTOS NetX Duo DHCP server</span></span>

<span data-ttu-id="83b2c-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika DHCP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="83b2c-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="83b2c-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="83b2c-105">Product Distribution</span></span>

<span data-ttu-id="83b2c-106">Serwer DHCP NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="83b2c-106">The NetX Duo DHCP Server is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="83b2c-107">Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83b2c-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="83b2c-108">**nxd_dhcp_server. h** Plik nagłówkowy serwera DHCP z NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-108">**nxd_dhcp_server.h** Header file for NetX Duo DHCP Server</span></span>
- <span data-ttu-id="83b2c-109">**nxd_dhcp_server. c** Plik źródłowy C dla serwera DHCP z NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-109">**nxd_dhcp_server.c** C Source file for NetX Duo DHCP Server</span></span>
- <span data-ttu-id="83b2c-110">**nxd_dhcp_server.pdf** Podręcznik użytkownika dla serwera DHCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-110">**nxd_dhcp_server.pdf** User Guide for NetX Duo DHCP Server</span></span>
- <span data-ttu-id="83b2c-111">**demo_netxduo_dhcp. c** Demonstracja serwera DHCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-111">**demo_netxduo_dhcp.c** NetX Duo DHCP Server demonstration</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="83b2c-112">Instalacja DHCP</span><span class="sxs-lookup"><span data-stu-id="83b2c-112">DHCP Installation</span></span>

<span data-ttu-id="83b2c-113">Aby można było korzystać z serwera DHCP z systemem NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="83b2c-113">In order to use NetX Duo DHCP Server, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="83b2c-114">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_dhcp_server. h* i *nxd_dhpc_server. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="83b2c-114">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcp_server.h* and *nxd_dhpc_server.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-dhcp-server"></a><span data-ttu-id="83b2c-115">Korzystanie z serwera DHCP z NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-115">Using NetX Duo DHCP Server</span></span>

<span data-ttu-id="83b2c-116">Korzystanie z serwera DHCP z NetX Duo jest proste.</span><span class="sxs-lookup"><span data-stu-id="83b2c-116">Using NetX Duo DHCP Server is easy.</span></span> <span data-ttu-id="83b2c-117">Zasadniczo kod aplikacji musi zawierać *nx_dhcp_server. h* , po uwzględnieniu *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="83b2c-117">Basically, the application code must include *nx_dhcp_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="83b2c-118">Po dołączeniu *nxd_dhcp_server. h* kod aplikacji będzie następnie mógł określić wywołania funkcji DHCP w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="83b2c-118">Once *nxd_dhcp_server.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="83b2c-119">Aplikacja musi również zawierać *nxd_dhcp_server. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="83b2c-119">The application must also include *nxd_dhcp_server.c* in the build process.</span></span> <span data-ttu-id="83b2c-120">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83b2c-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="83b2c-121">Aby uzyskać więcej informacji na temat korzystania z serwera DHCP z systemem NetX Duo, zobacz poniższe sekcje wymagania dotyczące **serwera** DHCP **w systemie NetX Duo** i ograniczeń serwera DHCP z systemem **NetX Duo**.</span><span class="sxs-lookup"><span data-stu-id="83b2c-121">For more details on using NetX Duo DHCP Server, see the following sections **Requirements of the NetX Duo DHCP** **Server** and **Constraints of the NetX Duo DHCP Server**.</span></span>

<span data-ttu-id="83b2c-122">Należy pamiętać, że ponieważ protokół DHCP korzysta z usług UDP NetX Duo, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-122">Note that since DHCP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

## <a name="requirements-of-the-netx-duo-dhcp-server"></a><span data-ttu-id="83b2c-123">Wymagania dotyczące serwera DHCP z NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-123">Requirements of the NetX Duo DHCP Server</span></span>

<span data-ttu-id="83b2c-124">Serwer DHCP NetX Duo wymaga, aby port gniazda UDP został przypisany do dobrze znanego portu DHCP 67.</span><span class="sxs-lookup"><span data-stu-id="83b2c-124">The NetX Duo DHCP Server requires a UDP socket port assigned to the well known DHCP port 67.</span></span> <span data-ttu-id="83b2c-125">Aby utworzyć serwer DHCP, aplikacja musi utworzyć pulę pakietów z ładunkiem pakietu o co najmniej 548 bajtach, a także nagłówkiem IP, UDP i Ethernet (łącznie 44 bajtów z 4 bajtem).</span><span class="sxs-lookup"><span data-stu-id="83b2c-125">To create the DHCP Server, the application must create a packet pool with packet payload at least 548 bytes plus IP, UDP and Ethernet headers (which total 44 bytes with 4 byte alignment).</span></span>

<span data-ttu-id="83b2c-126">Przyjęto założenie, że serwer i klient używają ustawień adresu sprzętowego sieci Ethernet:</span><span class="sxs-lookup"><span data-stu-id="83b2c-126">It is assumed that the Server and Client are both using Ethernet hardware address settings:</span></span>

- <span data-ttu-id="83b2c-127">Typ sprzętu 1</span><span class="sxs-lookup"><span data-stu-id="83b2c-127">Hardware type 1</span></span>
- <span data-ttu-id="83b2c-128">Długość sprzętu 6</span><span class="sxs-lookup"><span data-stu-id="83b2c-128">Hardware length 6</span></span>
- <span data-ttu-id="83b2c-129">Przeskoki 0</span><span class="sxs-lookup"><span data-stu-id="83b2c-129">Hops 0</span></span>

### <a name="multiple-client-sessions"></a><span data-ttu-id="83b2c-130">Wiele sesji klienta</span><span class="sxs-lookup"><span data-stu-id="83b2c-130">Multiple Client Sessions</span></span>

<span data-ttu-id="83b2c-131">Serwer DHCP z systemem NetX Duo może obsługiwać wiele sesji klientów, zachowując tabelę aktywnych klientów DHCP i jakie "Stany" klient znajduje się na liście. Stany DHCP INICJUJą, URUCHAMIAją, WYBIERAją, ŻĄDAją, ODNAWIAnia itp. Jeśli limit czasu sesji upływa przed odebraniem następnego komunikatu klienta, o ile ten klient nie jest powiązany z dzierżawą IP, serwer wyczyści dane sesji klienta i zwróci przypisany adres IP z powrotem do dostępnej puli.</span><span class="sxs-lookup"><span data-stu-id="83b2c-131">The NetX Duo DHCP Server can handles multiple Client sessions by keeping a table of active DHCP clients and what ‘state’ the Client is in e.g. DHCP states INIT, BOOT, SELECTING, REQUESTING, RENEWING etc. If the session time out expires before receiving the next Client message, unless that Client is bound to an IP lease, the Server will clear the Client session data and return the assigned IP address back to the available pool.</span></span> <span data-ttu-id="83b2c-132">Jeśli serwer odbierze wiele komunikatów ODNAJDYWAnia z tego samego klienta, serwer resetuje limit czasu sesji i utrzymuje adres IP zarezerwowany dla klienta w kolejnych komunikatach żądania.</span><span class="sxs-lookup"><span data-stu-id="83b2c-132">If the Server receives multiple DISCOVER messages from the same Client the Server resets the session time out and keeps the IP address reserved for the Client to accept in a subsequent REQUEST message.</span></span>

<span data-ttu-id="83b2c-133">Serwer DHCP NetX Duo akceptuje również żądanie DHCP klienta pojedynczego stanu, np. klient wysyła tylko komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="83b2c-133">The NetX Duo DHCP Server also accepts the single state Client DHCP request e.g. the Client only sends a REQUEST message.</span></span> <span data-ttu-id="83b2c-134">Przyjęto założenie, że klientowi przypisano wcześniej dzierżawę adresu IP z serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-134">This assumes the Client has been previously assigned an IP lease from the DHCP server.</span></span>

### <a name="setting-interface-specific-network-parameters-server-responses"></a><span data-ttu-id="83b2c-135">Ustawianie specyficznych dla interfejsu parametrów sieciowych odpowiedzi serwera</span><span class="sxs-lookup"><span data-stu-id="83b2c-135">Setting Interface Specific Network Parameters Server Responses</span></span>

<span data-ttu-id="83b2c-136">Aplikacja może ustawić router, maskę podsieci i parametry serwera DNS dla każdego interfejsu, który obsługuje żądania klientów DHCP przy użyciu usługi *nx_dhcp_set_interface_network_parameters* .</span><span class="sxs-lookup"><span data-stu-id="83b2c-136">The application can set the router, subnet mask and DNS server parameters for each interface it handles DHCP Client requests, using the *nx_dhcp_set_interface_network_parameters* service.</span></span> <span data-ttu-id="83b2c-137">W przeciwnym razie te parametry są domyślnie przypisane do bramy IP w interfejsie głównym serwera, jego podsieci sieciowej DHCP i adresu IP serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-137">Otherwise these parameters are defaulted to the IP gateway on the Server’s primary interface, its DHCP network subnet, and DHCP Server IP address, respectively.</span></span>

<span data-ttu-id="83b2c-138">Serwer DHCP zawiera te parametry w danych opcji komunikatów DHCP wysyłanych do klientów DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-138">The DHCP server includes these parameters in the option data of DHCP messages it sends to DHCP clients.</span></span>

### <a name="assigning-ip-addresses-to-the-client"></a><span data-ttu-id="83b2c-139">Przypisywanie adresów IP do klienta</span><span class="sxs-lookup"><span data-stu-id="83b2c-139">Assigning IP addresses to the Client</span></span>

<span data-ttu-id="83b2c-140">Jeśli komunikat ODNAJDYWAnia klienta nie określa żądanego adresu IP, serwer DHCP może użyć jednego z jego własnej puli.</span><span class="sxs-lookup"><span data-stu-id="83b2c-140">If the Client DISCOVER message does not specify a requested IP address, the DHCP Server can use one from its own pool.</span></span> <span data-ttu-id="83b2c-141">Jeśli serwer nie ma dostępnych adresów IP, wyśle klientowi komunikat NACK.</span><span class="sxs-lookup"><span data-stu-id="83b2c-141">If the Server has no available IP addresses it will send the Client a NACK message.</span></span>

<span data-ttu-id="83b2c-142">Serwer DHCP NetX Duo przydzieli żądany adres IP w komunikacie żądania klienta, o ile adres IP jest dostępny i znajduje się w bazie danych adresów IP serwera.</span><span class="sxs-lookup"><span data-stu-id="83b2c-142">The NetX Duo DHCP Server will grant the requested IP address in the Client REQUEST message as long as the IP address is available and can be found in the Server IP address database.</span></span> <span data-ttu-id="83b2c-143">Aplikacja tworzy listę dostępnych adresów IP serwera na potrzeby przypisywania do klientów DHCP przy użyciu usługi *nx_dhcp_create_server_ip_address_list* .</span><span class="sxs-lookup"><span data-stu-id="83b2c-143">The application creates the Server’s list of available IP addresses for assigning to DHCP Clients using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="83b2c-144">Jeśli serwer nie ma żądanych adresów IP lub jest przypisany do innego hosta, wyśle klientowi komunikat NACK.</span><span class="sxs-lookup"><span data-stu-id="83b2c-144">If the Server does not have the requested IP addresses or it is assigned to another host it will send the Client a NACK message.</span></span>

<span data-ttu-id="83b2c-145">Gdy serwer DHCP odbiera żądanie klienta, identyfikuje tego klienta w sposób unikatowy przy użyciu adresu MAC klienta w polu adres MAC klienta w komunikacie DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-145">When the DHCP Server receives a Client request, it identifies that Client uniquely using the Client MAC address in the Client MAC address field in the DHCP message.</span></span> <span data-ttu-id="83b2c-146">Jeśli klient zmieni adres MAC lub zostanie przeniesiony w innym miejscu do innej podsieci, powinien wysłać komunikat o ZWOLNIeniu do serwera w celu zwrócenia adresu IP z powrotem do dostępnej puli i zażądać nowego adresu IP w stanie inicjowania.</span><span class="sxs-lookup"><span data-stu-id="83b2c-146">If the Client changes it’s MAC address or is moved elsewhere onto another subnet it should send a RELEASE message to the Server to return the IP address back to the available pool, and request a new IP address in the INIT state.</span></span>

<span data-ttu-id="83b2c-147">Szczegóły można znaleźć na rysunku 1,1 w **małej sekcji systemowej** .</span><span class="sxs-lookup"><span data-stu-id="83b2c-147">See Figure 1.1 of the **Small Example System** section for details.</span></span> <span data-ttu-id="83b2c-148">Liczba adresów IP zapisanych w wystąpieniu serwera DHCP jest ograniczona do rozmiaru tablicy adresów serwera w bloku kontroli serwera DHCP i jest definiowana przez konfigurowalną NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE opcji.</span><span class="sxs-lookup"><span data-stu-id="83b2c-148">The number of IP addresses saved to the DHCP Server instance is limited to the size of the server address array in the DHCP Server control block, and defined by the configurable option NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span></span>

### <a name="ip-address-lease-times"></a><span data-ttu-id="83b2c-149">Czasy dzierżawy adresów IP</span><span class="sxs-lookup"><span data-stu-id="83b2c-149">IP Address Lease Times</span></span>

<span data-ttu-id="83b2c-150">Serwer DHCP również akceptuje czas dzierżawy klienta żądania, jeśli czas dzierżawy jest krótszy niż domyślny czas dzierżawy serwera, który jest zdefiniowany w opcji konfigurowalne NX_DHCP_DEFAULT_LEASE_TIME.</span><span class="sxs-lookup"><span data-stu-id="83b2c-150">The DHCP Server will also accept the request Client lease time if that lease time is less than the Server default lease time which is defined in configurable option NX_DHCP_DEFAULT_LEASE_TIME.</span></span> <span data-ttu-id="83b2c-151">Odnawianie i ponowne wiązanie czasów przypisanych do klienta wynosi odpowiednio 50% i 85% czasu dzierżawy, chyba że czas dzierżawy jest nieskończony (0xFFFFFFFF), w którym przypadku odnowienie i ponowne wiązanie czasu są również ustawione na nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="83b2c-151">Renewal and rebind times assigned to the Client are 50% and 85% of the lease time, respectively, unless the lease time is infinity (0xFFFFFFFF), in which case renewal and rebind times are also set to infinity.</span></span>

### <a name="dhcp-server-timeouts"></a><span data-ttu-id="83b2c-152">Limity czasu serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="83b2c-152">DHCP Server Timeouts</span></span>

<span data-ttu-id="83b2c-153">Serwer DHCP ma konfigurowalny limit czasu sesji użytkownika, NX_DHCP_CLIENT_SESSION_TIMEOUT w celu oczekiwania na następny komunikat klienta DHCP, chyba że sesja zostanie ukończona.</span><span class="sxs-lookup"><span data-stu-id="83b2c-153">The DHCP Server has a user configurable session timeout, NX_DHCP_CLIENT_SESSION_TIMEOUT, for waiting for the next DHCP Client message unless the session is completed.</span></span> <span data-ttu-id="83b2c-154">Limit czasu jest resetowany, gdy serwer odbierze następny komunikat od klienta, niezależnie od tego, czy wiadomość została wcześniej wysłana.</span><span class="sxs-lookup"><span data-stu-id="83b2c-154">The time out is reset when the Server receives the next message from the Client regardless if is the same message previously sent.</span></span>

### <a name="internal-error-handling"></a><span data-ttu-id="83b2c-155">Wewnętrzna obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="83b2c-155">Internal error handling</span></span>

<span data-ttu-id="83b2c-156">Serwer DHCP odbiera i przetwarza pakiety klienta DHCP w funkcji *nx_dhcp_listen_for_messages* .</span><span class="sxs-lookup"><span data-stu-id="83b2c-156">The DHCP Server receives and processes DHCP Client packets in the *nx_dhcp_listen_for_messages* function.</span></span> <span data-ttu-id="83b2c-157">Ta funkcja nie będzie kontynuować przetwarzania bieżącego pakietu klienta DHCP, jeśli pakiet jest nieprawidłowy lub wystąpił błąd wewnętrzny serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-157">This function will discontinue processing the current DHCP Client packet if the packet is invalid, or the DHCP Server encounters an internal error.</span></span> <span data-ttu-id="83b2c-158">n *x_dhcp_listen_for_messages* zwraca stanu błędu.</span><span class="sxs-lookup"><span data-stu-id="83b2c-158">n *x_dhcp_listen_for_messages* returns an error status.</span></span> <span data-ttu-id="83b2c-159">Wątek serwera DHCP zrzeka się krótkiej kontroli harmonogramu ThreadX przed wywołaniem tej funkcji, aby otrzymać następny komunikat klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-159">The DHCP Server thread relinquishes control briefly of the ThreadX scheduler before calling this function to receive the next DHCP Client message.</span></span> <span data-ttu-id="83b2c-160">W bieżącej wersji nie ma obsługi rejestrowania dla stanu błędu zwraca z *nx_dhcp_listen_for_messages.*</span><span class="sxs-lookup"><span data-stu-id="83b2c-160">In the current release there is no logging support for error status returns from *nx_dhcp_listen_for_messages.*</span></span>

### <a name="option-55-parameter-request-list"></a><span data-ttu-id="83b2c-161">Opcja 55: Lista żądań parametrów</span><span class="sxs-lookup"><span data-stu-id="83b2c-161">Option 55: Parameter Request List</span></span>

<span data-ttu-id="83b2c-162">Serwer DHCP NetX Duo musi być skonfigurowany z zestawem opcji do załadowania do parametru opcja żądania (55) w komunikatach oferta i DHCPACK przesyłanych z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="83b2c-162">The NetX Duo DHCP Server must be configured with a set of options to load to Parameter Request Option (55) list in the OFFER and DHCPACK messages it transmits back to the Client.</span></span> <span data-ttu-id="83b2c-163">Te opcje powinny obejmować dane konfiguracji krytycznej sieci dla sieci klienta i domyślnie zdefiniowane jako adres IP routera, maska podsieci i serwer DNS.</span><span class="sxs-lookup"><span data-stu-id="83b2c-163">These options should include network critical configuration data for the Client network and by default is defined to be router IP address, subnet mask, and DNS server.</span></span> <span data-ttu-id="83b2c-164">Lista opcji jest listą rozdzielaną spacjami i zdefiniowaną w NX_DHCP_DEFAULT_SERVER_OPTION_LIST konfigurowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83b2c-164">The option list is a space delimited list and defined in the user configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span></span> <span data-ttu-id="83b2c-165">Zwróć uwagę, że liczba opcji określona na tej liście musi być równa NX_DHCP_DEFAULT_OPTION_LIST_SIZE, która również jest zdefiniowana przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83b2c-165">Note the number of options specified in this list must equal NX_DHCP_DEFAULT_OPTION_LIST_SIZE which is also user defined.</span></span>

## <a name="constraints-of-the-netx-duo-dhcp-server"></a><span data-ttu-id="83b2c-166">Ograniczenia serwera DHCP z NetX Duo</span><span class="sxs-lookup"><span data-stu-id="83b2c-166">Constraints of the NetX Duo DHCP Server</span></span>

### <a name="dhcp-messages"></a><span data-ttu-id="83b2c-167">Komunikaty DHCP</span><span class="sxs-lookup"><span data-stu-id="83b2c-167">DHCP Messages</span></span>

<span data-ttu-id="83b2c-168">Serwer DHCP NetX Duo nie sprawdza, czy adres IP nie został przypisany w innym miejscu w sieci przed przydzieleniem adresu IP klientowi.</span><span class="sxs-lookup"><span data-stu-id="83b2c-168">The NetX Duo DHCP Server does not verify that an IP address has not been assigned elsewhere on the network before granting the IP address to the Client.</span></span> <span data-ttu-id="83b2c-169">Jeśli istnieje wiele serwerów DHCP, może to być w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="83b2c-169">If there are multiple DHCP servers, this can indeed be the case.</span></span> <span data-ttu-id="83b2c-170">*Zgodnie z dokumentem RFC 2131, jest odpowiedzialny za sprawdzenie, czy adres IP jest unikatowy w sieci* (np. pingowanie adresu).</span><span class="sxs-lookup"><span data-stu-id="83b2c-170">*As per RFC 2131, it is the Client’s responsibility to verify the IP address is unique on its network* (e.g. pinging the address).</span></span> <span data-ttu-id="83b2c-171">Jeśli tak nie jest, serwer powinien odebrać komunikat o ODRZUCENIu o adresie IP, aby zaktualizować jego bazę danych od klienta.</span><span class="sxs-lookup"><span data-stu-id="83b2c-171">If it is not, the Server should receive a DECLINE message with the IP address to update its database from the Client.</span></span>

<span data-ttu-id="83b2c-172">Serwer DHCP NetX Duo nie wydaje komunikatów FORCE_RENEW.</span><span class="sxs-lookup"><span data-stu-id="83b2c-172">The NetX Duo DHCP Server does not issue FORCE_RENEW messages.</span></span> <span data-ttu-id="83b2c-173">Klient DHCP może odnowić dzierżawę adresów IP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-173">It is up to the DHCP Client to renew its IP address lease.</span></span> <span data-ttu-id="83b2c-174">Jednak serwer DHCP monitoruje pozostały czas dla wszystkich przypisanych adresów IP w swojej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="83b2c-174">However, the DHCP Server monitors the time remaining on all the assigned IP addresses in its database.</span></span> <span data-ttu-id="83b2c-175">Gdy dzierżawa adresu IP wygaśnie, ten adres IP jest zwracany do puli dostępnych adresów IP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-175">When an IP address lease expires that IP address is returned to the pool of available IP addresses.</span></span> <span data-ttu-id="83b2c-176">W związku z tym klient może aktywnie odnowić/ponownie powiązać dzierżawę adresów IP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-176">Hence it is up to the Client to actively renew/rebind its IP address lease.</span></span>

<span data-ttu-id="83b2c-177">Dane sesji są wyczyszczone, gdy tylko klient zostanie przydzielony ("powiązany") do dzierżawy IP (lub jest odnawiany istniejący).</span><span class="sxs-lookup"><span data-stu-id="83b2c-177">Session data is cleared as soon as the Client either is granted (“bound”) to an IP lease (or an existing one is renewed).</span></span> <span data-ttu-id="83b2c-178">Jeśli pakiet klienta pozostanie nieprawdziwy lub klient przekroczy limit czasu między odpowiedziami, dane sesji są usuwane.</span><span class="sxs-lookup"><span data-stu-id="83b2c-178">If a Client packet proves bogus, or the Client times out between responses, session data is cleared.</span></span>

### <a name="saving-data-between-reboots"></a><span data-ttu-id="83b2c-179">Zapisywanie danych między ponownymi uruchomieniami</span><span class="sxs-lookup"><span data-stu-id="83b2c-179">Saving Data Between Reboots</span></span>

<span data-ttu-id="83b2c-180">Serwer DHCP NetX Duo zapisuje dane klienta, w tym parametry żądania DHCP w tabeli rekordu klienta.</span><span class="sxs-lookup"><span data-stu-id="83b2c-180">The NetX Duo DHCP Server saves Client data including DHCP request parameters in a Client record table.</span></span> <span data-ttu-id="83b2c-181">Ta tabela nie jest przechowywana w pamięci nieulotnej, dlatego jeśli Host serwera DHCP musi ponownie uruchomić te informacje nie zostaną zapisane między ponownymi uruchomieniami.</span><span class="sxs-lookup"><span data-stu-id="83b2c-181">This table is not stored in non-volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

<span data-ttu-id="83b2c-182">Serwer DHCP NetX Duo zapisuje dane dzierżawy adresów IP w tabeli adresów IP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-182">The NetX Duo DHCP Server saves IP address lease data in a IP address table.</span></span> <span data-ttu-id="83b2c-183">Ta tabela nie jest przechowywana w pamięci nieulotnej, dlatego jeśli Host serwera DHCP musi ponownie uruchomić te informacje nie zostaną zapisane między ponownymi uruchomieniami.</span><span class="sxs-lookup"><span data-stu-id="83b2c-183">This table is not stored in non-volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

### <a name="relay-agents"></a><span data-ttu-id="83b2c-184">Agenci przekazywania</span><span class="sxs-lookup"><span data-stu-id="83b2c-184">Relay Agents</span></span>

<span data-ttu-id="83b2c-185">Serwer DHCP NetX Duo jest skonfigurowany z zerowym adresem IP dla pola "Agent przekazywania", ponieważ nie obsługuje żądań DHCP w sieci.</span><span class="sxs-lookup"><span data-stu-id="83b2c-185">The NetX Duo DHCP Server is configured with a zero IP address for the ‘Relay agent’ field because it does not support out of network DHCP requests.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="83b2c-186">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="83b2c-186">Small Example System</span></span>

<span data-ttu-id="83b2c-187">Przykładem prostej metody korzystania z serwera DHCP z systemem NetX Duo jest opisany poniżej rysunek 1,1.</span><span class="sxs-lookup"><span data-stu-id="83b2c-187">An example of how easy it is to use the NetX Duo DHCP Server is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="83b2c-188">W tym przykładzie plik dołączania DHCP *nxd_dhcp_server. h* jest wprowadzony w wierszu 5.</span><span class="sxs-lookup"><span data-stu-id="83b2c-188">In this example, the DHCP include file *nxd_dhcp_server.h* is brought in at line 5.</span></span> <span data-ttu-id="83b2c-189">Wszystkie linie są zdefiniowane w wierszach 7-13 dla rozmiaru stosu wątków serwera DHCP, rozmiaru stosu wątku IP i rozmiaru stosu wątku testu.</span><span class="sxs-lookup"><span data-stu-id="83b2c-189">DHCP Server thread stack size, IP thread stack size and test thread stack size are all defined in lines 7-13.</span></span>

<span data-ttu-id="83b2c-190">Pierwsze zadanie wątku testu opcjonalne do zatrzymywania, ponownego uruchamiania i ostatecznie usuwania serwera DHCP jest tworzone z użyciem funkcji "*test_thread_entry*" w wierszu 57.</span><span class="sxs-lookup"><span data-stu-id="83b2c-190">First, an optional test thread task for stopping, restarting and eventually deleting the DHCP server is created with the “*test_thread_entry*” function at line 57.</span></span> <span data-ttu-id="83b2c-191">Blok kontroli serwera DHCP "*dhcp_server*" jest zdefiniowany jako zmienna globalna w wierszu 20.</span><span class="sxs-lookup"><span data-stu-id="83b2c-191">A DHCP Server control block “*dhcp_server*” is defined as a global variable at line 20.</span></span> <span data-ttu-id="83b2c-192">Należy zauważyć, że Pula pakietów serwera jest tworzona z pakietami o co najmniej tyle jak standardowy komunikat DHCP (548 bajtów Plus bajty nagłówka IP i UDP).</span><span class="sxs-lookup"><span data-stu-id="83b2c-192">Note that the server packet pool is created with packets having a payload at least as large as the standard DHCP message (548 bytes plus IP and UDP header bytes).</span></span> <span data-ttu-id="83b2c-193">Po pomyślnym utworzeniu wystąpienia IP dla serwera DHCP aplikacja utworzy serwer DHCP w wierszu 96.</span><span class="sxs-lookup"><span data-stu-id="83b2c-193">After successfully creating an IP instance for the DHCP Server, the application creates the DHCP Server in line 96.</span></span> <span data-ttu-id="83b2c-194">Następnie aplikacja włącza wystąpienie protokołu IP serwera do włączenia protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-194">Next, the application enables the Server IP instance to be UDP enabled.</span></span> <span data-ttu-id="83b2c-195">Przed uruchomieniem serwera DHCP, lista dostępnych adresów IP zostanie utworzona w wierszu 137 przy użyciu usługi **nx_dhcp_create_server_ip_address_list** .</span><span class="sxs-lookup"><span data-stu-id="83b2c-195">Before starting the DHCP Server, the available IP address list is created in line 137 using the **nx_dhcp_create_server_ip_address_list** service.</span></span> <span data-ttu-id="83b2c-196">Parametry konfiguracji sieci są ustawiane w następującym wierszu 138 przy użyciu usługi **nx_dhcp_set_interface_network_parameters** . usługi serwera DHCP stają się dostępne, gdy aplikacja wywoła *nx_dhcp_server_start* w wierszu 141.</span><span class="sxs-lookup"><span data-stu-id="83b2c-196">The network configuration parameters are set in the following line 138 using the **nx_dhcp_set_interface_network_parameters** service, DHCP Server services become available when the application calls the *nx_dhcp_server_start* at line 141.</span></span> <span data-ttu-id="83b2c-197">Zadanie wątku testowego ilustruje użycie zatrzymywania i ponownego uruchamiania serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-197">The test thread task demonstrates the use of stopping and restarting the DHCP server.</span></span>

```C
/* This is a small demo of NetX Duo DHCP Server for the high-performance NetX Duo TCP/IP stack.  */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE         2048
#define     DEMO_SERVER_STACK_SIZE  2048
#define     SERVER_IP_ADDRESS_LIST  "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD          1000
#define     PACKET_POOL_SIZE        (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK    2048


/* Define the ThreadX and NetX Duo Duo object control blocks...  */

TX_THREAD test_thread;
NX_PACKET_POOL server_pool;
NX_IP server_ip;
NX_DHCP_SERVER dhcp_server;


/* Define the counters used in the demo application...  */

ULONG state_changes;


/* Define thread prototypes.  */

void test_thread_entry(ULONG thread_input);
void nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define main entry point.  */

int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{
    CHAR    *pointer;
    UINT    status;


    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the test thread.  */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
            pointer, TEST_STACK_SIZE,  1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duosystem.  */
    nx_system_initialize();

    /* Create the DHCP Server packet pool.  */
    status =  nx_packet_pool_create(&server_pool, "NetX Main Packet Pool", PACKET_PAYLOAD,
        pointer, PACKET_POOL_SIZE);
    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error.  */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance.  */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
        0xFFFFFF00UL,  &server_pool, nx_etherDriver_mcf5485, pointer,
        R_IP_THREAD_STACK, 1);

    pointer =  pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors.  */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance.  */
    status =  nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                                     DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic.  */
    status =  nx_udp_enable(&server_ip);

    /* Check for UDP enable errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility.  */
    status =  nx_icmp_enable(&server_ip);

    /* Check for errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

   status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                                 START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

   status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                               NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                               IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server.  */
   status =  nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread.  */
void    test_thread_entry(ULONG thread_input)
{
    UINT status;
    UINT keep_spinning;


    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }


    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);


    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}

```

<span data-ttu-id="83b2c-198">**Rysunek 1,1 przykład aplikacji serwera DHCP NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="83b2c-198">**Figure 1.1 Example NetX Duo DHCP Server application**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="83b2c-199">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="83b2c-199">Configuration Options</span></span>

<span data-ttu-id="83b2c-200">Istnieje kilka opcji konfiguracji do kompilowania serwera DHCP z NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="83b2c-200">There are several configuration options for building NetX Duo DHCP Server.</span></span> <span data-ttu-id="83b2c-201">Poniższa lista zawiera szczegółowy opis:</span><span class="sxs-lookup"><span data-stu-id="83b2c-201">The following list describes each in detail:</span></span>

- <span data-ttu-id="83b2c-202">**NX_DISABLE_ERROR_CHECKING**: Ta opcja usuwa podstawowe sprawdzanie błędów serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-202">**NX_DISABLE_ERROR_CHECKING**: This option removes the basic DHCP error checking.</span></span> <span data-ttu-id="83b2c-203">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83b2c-203">It it typically used after the application is debugged.</span></span>
- <span data-ttu-id="83b2c-204">**NX_DHCP_SERVER_THREAD_PRIORITY**: Ta opcja określa priorytet wątku serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-204">**NX_DHCP_SERVER_THREAD_PRIORITY**: This option specifies the priority of the DHCP Server thread.</span></span> <span data-ttu-id="83b2c-205">Domyślnie ta wartość określa, że wątek DHCP działa z priorytetem 2.</span><span class="sxs-lookup"><span data-stu-id="83b2c-205">By default, this value specifies that the DHCP thread runs at priority 2.</span></span>
- <span data-ttu-id="83b2c-206">**NX_DHCP_TYPE_OF_SERVICE**: Ta opcja określa typ usługi wymaganej przez żądania UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-206">**NX_DHCP_TYPE_OF_SERVICE**: This option specifies the type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="83b2c-207">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-207">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="83b2c-208">**NX_DHCP_FRAGMENT_OPTION**: włączono fragment dla żądań UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-208">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="83b2c-209">Domyślnie ta wartość jest ustawiona na NX_DONT_FRAGMENT, aby wyłączyć fragmentację protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-209">By default, this value is set to NX_DONT_FRAGMENT to disable UDP fragmenting.</span></span>
- <span data-ttu-id="83b2c-210">**NX_DHCP_TIME_TO_LIVE**: określa liczbę routerów, które może przekazać pakiet, zanim zostanie on odrzucony.</span><span class="sxs-lookup"><span data-stu-id="83b2c-210">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers the packet can pass before it is discarded.</span></span> <span data-ttu-id="83b2c-211">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="83b2c-211">The default value is 0x80.</span></span>
- <span data-ttu-id="83b2c-212">**NX_DHCP_QUEUE_DEPTH**: określa liczbę pakietów, które przechowuje gniazdo serwera DHCP przed przystąpieniem do opróżniania kolejki.</span><span class="sxs-lookup"><span data-stu-id="83b2c-212">**NX_DHCP_QUEUE_DEPTH**: Specifies the number of packets that the DHCP Server socket keeps before flushing the queue.</span></span> <span data-ttu-id="83b2c-213">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="83b2c-213">The default value is 5.</span></span>
- <span data-ttu-id="83b2c-214">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: określa limit czasu w taktach czasomierza dla serwera DHCP NetX, aby oczekiwać na przydzielenie pakietu z jego puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="83b2c-214">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: Specifies the timeout in timer ticks for the NetX DHCP Server to wait for allocate a packet from its packet pool.</span></span> <span data-ttu-id="83b2c-215">Wartość domyślna to NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="83b2c-215">The default value is set to NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="83b2c-216">**NX_DHCP_SUBNET_MASK** Jest to maska podsieci, z którą klient DHCP powinien być skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="83b2c-216">**NX_DHCP_SUBNET_MASK** This is the subnet mask the DHCP Client should be configured with.</span></span> <span data-ttu-id="83b2c-217">Wartość domyślna to 0xFFFFFF00.</span><span class="sxs-lookup"><span data-stu-id="83b2c-217">The default value is set to 0xFFFFFF00.</span></span>
- <span data-ttu-id="83b2c-218">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: ten limit czasu jest określany w taktach czasomierza dla szybkiego czasomierza serwera DHCP do sprawdzania pozostałego czasu sesji i obsługi sesji, które przekroczyły limit czasu.</span><span class="sxs-lookup"><span data-stu-id="83b2c-218">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server fast timer to check on session time remaining and handle sessions that have timed out.</span></span>
- <span data-ttu-id="83b2c-219">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: ten limit czasu jest określany w taktach czasomierza serwera DHCP wolne czasomierz, aby sprawdzić pozostały czas dzierżawy adresu IP i obsłużyć dzierżawę, która przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="83b2c-219">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server slow timer to check on IP address lease time remaining and handle lease that have timed out.</span></span>
- <span data-ttu-id="83b2c-220">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: to jest limit czasu czasomierza w taktach, gdy serwer DHCP będzie czekać na następny komunikat klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-220">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: This is timeout period in timer ticks the DHCP Server will wait to receive the next DHCP Client message.</span></span>
- <span data-ttu-id="83b2c-221">**NX_DHCP_DEFAULT_LEASE_TIME**: jest to czas dzierżawy adresów IP (w sekundach) przypisany do klienta DHCP, a także podstawą obliczeń i czasów ponownego powiązania do klienta.</span><span class="sxs-lookup"><span data-stu-id="83b2c-221">**NX_DHCP_DEFAULT_LEASE_TIME**: This is IP Address lease time in seconds assigned to the DHCP Client, and the basis for computing the renewal and rebind times also assigned to the Client.</span></span> <span data-ttu-id="83b2c-222">Wartość domyślna to 0xFFFFFFFF (nieskończoność).</span><span class="sxs-lookup"><span data-stu-id="83b2c-222">The default value is set to 0xFFFFFFFF (infinity).</span></span>
- <span data-ttu-id="83b2c-223">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: rozmiar tablicy serwerów DHCP do przechowywania dostępnych adresów IP na potrzeby przypisywania do klienta.</span><span class="sxs-lookup"><span data-stu-id="83b2c-223">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: This is size of the DHCP Server array for holding available IP addresses for assigning to the Client.</span></span> <span data-ttu-id="83b2c-224">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="83b2c-224">The default value is 20.</span></span>
- <span data-ttu-id="83b2c-225">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: rozmiar tablicy serwera DHCP do przechowywania rekordów klientów.</span><span class="sxs-lookup"><span data-stu-id="83b2c-225">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: This is size of the DHCP Server array for holding Client records.</span></span> <span data-ttu-id="83b2c-226">Wartość domyślna to 50.</span><span class="sxs-lookup"><span data-stu-id="83b2c-226">The default value is 50.</span></span>
- <span data-ttu-id="83b2c-227">**NX_DHCP_CLIENT_OPTIONS_MAX**: rozmiar tablicy w wystąpieniu klienta DHCP w celu przechowywania wszystkich żądanych opcji na liście żądań parametrów w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="83b2c-227">**NX_DHCP_CLIENT_OPTIONS_MAX**: This is size of the array in the DHCP Client instance for holding the all the requested options in the parameter request list in the current session.</span></span> <span data-ttu-id="83b2c-228">Wartość domyślna to 12.</span><span class="sxs-lookup"><span data-stu-id="83b2c-228">The default value is 12.</span></span>
- <span data-ttu-id="83b2c-229">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: jest to bufor zawierający domyślną listę opcji do dostarczenia do bieżącego klienta DHCP na liście żądań parametrów.</span><span class="sxs-lookup"><span data-stu-id="83b2c-229">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: This is the buffer holding the DHCP Server’s default list of options to supply to the current DHCP Client in the parameter request list.</span></span> <span data-ttu-id="83b2c-230">Wartość domyślna to "1 3 6".</span><span class="sxs-lookup"><span data-stu-id="83b2c-230">The default is “1 3 6.”</span></span>
- <span data-ttu-id="83b2c-231">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: jest to rozmiar tablicy przechowującej domyślną listę opcji serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-231">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: This is the size of the array to hold the DHCP Server’s default list of options.</span></span> <span data-ttu-id="83b2c-232">Wartość domyślna to 3.</span><span class="sxs-lookup"><span data-stu-id="83b2c-232">The default value is 3.</span></span>
- <span data-ttu-id="83b2c-233">**NX_DHCP_SERVER_HOSTNAME_MAX**: rozmiar buforu do przechowywania nazwy hosta serwera.</span><span class="sxs-lookup"><span data-stu-id="83b2c-233">**NX_DHCP_SERVER_HOSTNAME_MAX**: This is size of the buffer for holding the Server host name.</span></span> <span data-ttu-id="83b2c-234">Wartość domyślna to 32.</span><span class="sxs-lookup"><span data-stu-id="83b2c-234">The default value is 32.</span></span>
- <span data-ttu-id="83b2c-235">**NX_DHCP_CLIENT_HOSTNAME_MAX**: rozmiar buforu do przechowywania nazwy hosta klienta w bieżącej sesji klienta serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="83b2c-235">**NX_DHCP_CLIENT_HOSTNAME_MAX**: This is size of the buffer for holding the Client host name in the current DHCP Server Client session.</span></span> <span data-ttu-id="83b2c-236">Wartość domyślna to 32.</span><span class="sxs-lookup"><span data-stu-id="83b2c-236">The default value is 32.</span></span>
