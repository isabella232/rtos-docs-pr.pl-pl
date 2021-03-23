---
title: Rozdział 1 — wprowadzenie do klienta DHCP usługi Azure RTO NetX
description: W NetX adres IP aplikacji jest jednym z podanych parametrów wywołania usługi nx_ip_create.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 44eb764c84a15a1bc96cf94bcbc8f81be7b41eef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822710"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="b30f7-103">Rozdział 1 — wprowadzenie do klienta DHCP usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="b30f7-103">Chapter 1 - Introduction to Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="b30f7-104">W NetX adres IP aplikacji jest jednym z podanych parametrów wywołania usługi *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="b30f7-104">In NetX, the application’s IP address is one of the supplied parameters to the *nx_ip_create* service call.</span></span> <span data-ttu-id="b30f7-105">Dostarczenie adresu IP nie powoduje żadnych problemów, jeśli adres IP jest znany aplikacji, statycznie lub przez konfigurację użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b30f7-105">Supplying the IP address poses no problem if the IP address is known to the application, either statically or through user configuration.</span></span> <span data-ttu-id="b30f7-106">Istnieją jednak pewne wystąpienia, w których aplikacja nie wie ani nie ponosi jego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-106">However, there are some instances where the application doesn’t know or care what its IP address is.</span></span> <span data-ttu-id="b30f7-107">W takich sytuacjach do funkcji *nx_ip_create* należy dostarczyć zerowy adres IP, a protokół klienta DHCP usługi Azure RTO powinien być używany do dynamicznego uzyskiwania adresu IP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-107">In such situations, a zero IP address should be supplied to the *nx_ip_create* function and the Azure RTOS DHCP Client protocol should be used to dynamically obtain an IP address.</span></span>

## <a name="dynamic-ip-address-assignment"></a><span data-ttu-id="b30f7-108">Dynamiczne przypisywanie adresów IP</span><span class="sxs-lookup"><span data-stu-id="b30f7-108">Dynamic IP Address Assignment</span></span>

<span data-ttu-id="b30f7-109">Podstawowa usługa używana do uzyskiwania dynamicznego adresu IP z sieci to protokół odwrotnego rozpoznawania adresów (RARP).</span><span class="sxs-lookup"><span data-stu-id="b30f7-109">The basic service used to obtain a dynamic IP address from the network is the Reverse Address Resolution Protocol (RARP).</span></span> <span data-ttu-id="b30f7-110">Ten protokół jest podobny do protokołu ARP, z tą różnicą, że został zaprojektowany w celu uzyskania adresu IP dla samego siebie zamiast wyszukiwania adresu MAC dla innego węzła sieci.</span><span class="sxs-lookup"><span data-stu-id="b30f7-110">This protocol is similar to ARP, except it is designed to obtain an IP address for itself instead of finding the MAC address for another network node.</span></span> <span data-ttu-id="b30f7-111">Komunikat RARP niskiego poziomu jest emitowany w sieci lokalnej i jest odpowiedzialny za serwer w sieci, aby odpowiedzieć na odpowiedź z RARP, która zawiera dynamicznie przydzieloną adres IP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-111">The low-level RARP message is broadcast on the local network and it is the responsibility of a server on the network to respond with an RARP response, which contains a dynamically allocated IP address.</span></span>

<span data-ttu-id="b30f7-112">Mimo że usługa RARP udostępnia usługę dynamicznego przydzielania adresów IP, ma kilka wad.</span><span class="sxs-lookup"><span data-stu-id="b30f7-112">Although RARP provides a service for dynamic allocation of IP addresses, it has several shortcomings.</span></span> <span data-ttu-id="b30f7-113">Większość niedoborów odblasku polega na tym, że RARP zapewnia tylko dynamiczną alokację adresu IP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-113">The most glaring deficiency is that RARP only provides dynamic allocation of the IP address.</span></span> <span data-ttu-id="b30f7-114">W większości sytuacji więcej informacji jest konieczna, aby urządzenie mogło prawidłowo uczestniczyć w sieci.</span><span class="sxs-lookup"><span data-stu-id="b30f7-114">In most situations, more information is necessary in order for a device to properly participate on a network.</span></span> <span data-ttu-id="b30f7-115">Oprócz adresu IP większość urządzeń wymaga maski sieci i adresu IP bramy.</span><span class="sxs-lookup"><span data-stu-id="b30f7-115">In addition to an IP address, most devices need the network mask and the gateway IP address.</span></span> <span data-ttu-id="b30f7-116">Może być również wymagany adres IP serwera DNS i inne informacje o sieci.</span><span class="sxs-lookup"><span data-stu-id="b30f7-116">The IP address of a DNS server and other network information may also be needed.</span></span> <span data-ttu-id="b30f7-117">RARP nie ma możliwości podania tych informacji.</span><span class="sxs-lookup"><span data-stu-id="b30f7-117">RARP does not have the ability to provide this information.</span></span>

## <a name="rarp-alternatives"></a><span data-ttu-id="b30f7-118">RARP alternatywy</span><span class="sxs-lookup"><span data-stu-id="b30f7-118">RARP Alternatives</span></span>

<span data-ttu-id="b30f7-119">W celu pokonania wad RARP pracownicy opracowanli bardziej kompleksowy mechanizm alokacji adresów IP o nazwie protokół Bootstrap (BOOTP).</span><span class="sxs-lookup"><span data-stu-id="b30f7-119">In order to overcome the deficiencies of RARP, researchers developed a more comprehensive IP address allocation mechanism called the Bootstrap Protocol (BOOTP).</span></span> <span data-ttu-id="b30f7-120">Ten protokół ma możliwość dynamicznego przydzielenia adresu IP, a także zapewnienia dodatkowych ważnych informacji o sieci.</span><span class="sxs-lookup"><span data-stu-id="b30f7-120">This protocol has the ability to dynamically allocate an IP address and also provide additional important network information.</span></span> <span data-ttu-id="b30f7-121">Jednak protokół BOOTP ma wady, które są przeznaczone do konfiguracji sieci statycznych.</span><span class="sxs-lookup"><span data-stu-id="b30f7-121">However, BOOTP has the drawback of being designed for static network configurations.</span></span> <span data-ttu-id="b30f7-122">Nie zezwala na szybkie lub automatyczne przypisywanie adresów.</span><span class="sxs-lookup"><span data-stu-id="b30f7-122">It does not allow for quick or automated address assignment.</span></span>

<span data-ttu-id="b30f7-123">Jest to miejsce, w którym Dynamic Host Configuration Protocol (DHCP) jest niezwykle przydatna.</span><span class="sxs-lookup"><span data-stu-id="b30f7-123">This is where the Dynamic Host Configuration Protocol (DHCP) is extremely useful.</span></span> <span data-ttu-id="b30f7-124">Usługa DHCP została zaprojektowana w celu rozbudowania podstawowych funkcji protokołu BOOTP w taki sposób, aby obejmowały całkowicie zautomatyzowaną alokację serwera IP i całkowicie dynamiczną alokację adresów IP za pomocą "dzierżawy" adresu IP do klienta przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="b30f7-124">DHCP is designed to extend the basic functionality of BOOTP to include completely automated IP server allocation and completely dynamic IP address allocation through “leasing” an IP address to a client for a specified period of time.</span></span> <span data-ttu-id="b30f7-125">Protokół DHCP można również skonfigurować tak, aby przydzielał adresy IP w sposób statyczny, jak w przypadku protokołu BOOTP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-125">DHCP can also be configured to allocate IP addresses in a static manner like BOOTP.</span></span>

## <a name="dhcp-messages"></a><span data-ttu-id="b30f7-126">Komunikaty DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-126">DHCP Messages</span></span>

<span data-ttu-id="b30f7-127">Mimo że usługa DHCP znacznie rozszerza funkcjonalność protokołu BOOTP, protokół DHCP używa tego samego formatu komunikatów co BOOTP i obsługuje te same opcje dostawcy co protokół BOOTP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-127">Although DHCP greatly enhances the functionality of BOOTP, DHCP uses the same message format as BOOTP and supports the same vendor options as BOOTP.</span></span> <span data-ttu-id="b30f7-128">Aby można było wykonać swoją funkcję, usługa DHCP wprowadza siedem nowych opcji specyficznych dla protokołu DHCP w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b30f7-128">In order to perform its function, DHCP introduces seven new DHCP-specific options, as follows:</span></span>

- <span data-ttu-id="b30f7-129">ODNAJDYWAnie (1) (wysyłane przez klienta DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-129">DISCOVER (1) (sent by DHCP Client)</span></span>

- <span data-ttu-id="b30f7-130">Oferta (2) (wysłana przez serwer DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-130">OFFER (2) (sent by DHCP Server)</span></span>

- <span data-ttu-id="b30f7-131">ŻĄDANIE (3) (wysyłane przez klienta DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-131">REQUEST (3) (sent by DHCP Client)</span></span>

- <span data-ttu-id="b30f7-132">Odrzuć (4) (Wysłany przez klienta DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-132">DECLINE (4) (sent by DHCP Client)</span></span>

- <span data-ttu-id="b30f7-133">ACK (5) (wysyłany przez serwer DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-133">ACK (5) (sent by DHCP Server)</span></span>

- <span data-ttu-id="b30f7-134">NACK (6) (wysyłanych przez serwer DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-134">NACK (6) (sent by DHCP Server)</span></span>

- <span data-ttu-id="b30f7-135">WYDANIE (7) (wysyłane przez klienta DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-135">RELEASE (7) (sent by DHCP Client)</span></span>

- <span data-ttu-id="b30f7-136">Informowanie (8) (wysyłane przez klienta DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-136">INFORM (8) (sent by DHCP Client)</span></span>

- <span data-ttu-id="b30f7-137">FORCERENEW (9) (wysyłane przez klienta DHCP)</span><span class="sxs-lookup"><span data-stu-id="b30f7-137">FORCERENEW (9) (sent by DHCP Client)</span></span>

## <a name="dhcp-communication"></a><span data-ttu-id="b30f7-138">Komunikacja DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-138">DHCP Communication</span></span>

<span data-ttu-id="b30f7-139">Protokół DHCP korzysta z protokołu UDP do wysyłania żądań i odpowiedzi pól.</span><span class="sxs-lookup"><span data-stu-id="b30f7-139">DHCP utilizes the UDP protocol to send requests and field responses.</span></span> <span data-ttu-id="b30f7-140">Przed przystąpieniem do adresu IP komunikaty UDP przenoszące informacje DHCP są wysyłane i odbierane przy użyciu adresu IP o wartości 255.255.255.255.</span><span class="sxs-lookup"><span data-stu-id="b30f7-140">Prior to having an IP address, UDP messages carrying the DHCP information are sent and received by utilizing the IP broadcast address of 255.255.255.255.</span></span>

## <a name="dhcp-client-state-machine"></a><span data-ttu-id="b30f7-141">Komputer stanu klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-141">DHCP Client State Machine</span></span>

<span data-ttu-id="b30f7-142">Klient DHCP jest zaimplementowany jako komputer stanu.</span><span class="sxs-lookup"><span data-stu-id="b30f7-142">The DHCP Client is implemented as a state machine.</span></span> <span data-ttu-id="b30f7-143">Komputer stanu jest przetwarzany przez wewnętrzny wątek DHCP, który jest tworzony podczas przetwarzania *nx_dhcp_create* .</span><span class="sxs-lookup"><span data-stu-id="b30f7-143">The state machine is processed by an internal DHCP thread that is created during *nx_dhcp_create* processing.</span></span> <span data-ttu-id="b30f7-144">Główne Stany klienta DHCP są następujące:</span><span class="sxs-lookup"><span data-stu-id="b30f7-144">The main states of DHCP Client are as follows:</span></span>


- <span data-ttu-id="b30f7-145">**NX_DHCP_STATE_BOOT** Począwszy od poprzedniego adresu IP</span><span class="sxs-lookup"><span data-stu-id="b30f7-145">**NX_DHCP_STATE_BOOT** Starting with a previous IP address</span></span>

- <span data-ttu-id="b30f7-146">**NX_DHCP_STATE_INIT** Rozpoczynając od braku poprzedniej wartości adresu IP</span><span class="sxs-lookup"><span data-stu-id="b30f7-146">**NX_DHCP_STATE_INIT** Starting with no previous   IP address value</span></span>

- <span data-ttu-id="b30f7-147">**NX_DHCP_STATE_SELECTING** Oczekiwanie na odpowiedź z dowolnego serwera DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-147">**NX_DHCP_STATE_SELECTING** Waiting for a response from any DHCP server</span></span>

- <span data-ttu-id="b30f7-148">**NX_DHCP_STATE_REQUESTING** Zidentyfikowano serwer DHCP, wysłane żądanie adresu IP</span><span class="sxs-lookup"><span data-stu-id="b30f7-148">**NX_DHCP_STATE_REQUESTING** DHCP Server identified, IP address request sent</span></span>

- <span data-ttu-id="b30f7-149">**NX_DHCP_STATE_BOUND** Ustanowiono dzierżawę adresu IP DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-149">**NX_DHCP_STATE_BOUND** DHCP IP Address lease established</span></span>

- <span data-ttu-id="b30f7-150">**NX_DHCP_STATE_RENEWING** Upłynął czas odnawiania dzierżawy adresu IP DHCP, żądanie odnowienia</span><span class="sxs-lookup"><span data-stu-id="b30f7-150">**NX_DHCP_STATE_RENEWING** DHCP IP Address lease renewal time elapsed, renewal requested</span></span>

- <span data-ttu-id="b30f7-151">**NX_DHCP_STATE_REBINDING** Upłynął czas ponownego wiązania dzierżawy adresu IP DHCP, żądanie odnowienia</span><span class="sxs-lookup"><span data-stu-id="b30f7-151">**NX_DHCP_STATE_REBINDING** DHCP IP Address lease rebind time elapsed, renewal requested</span></span>

- <span data-ttu-id="b30f7-152">**NX_DHCP_STATE_FORCERENEW** Ustanowiono dzierżawę adresu IP DHCP, Wymuś odnowienie przez serwer (obecnie nie jest to obsługiwane) lub przez aplikację wywołującą nx_dhcp_force_renew</span><span class="sxs-lookup"><span data-stu-id="b30f7-152">**NX_DHCP_STATE_FORCERENEW** DHCP IP Address lease established, force renewal by server (currently not supported) or by the application calling nx_dhcp_force_renew</span></span>

- <span data-ttu-id="b30f7-153">**NX_DHCP_STATE_ADDRESS_PROBING** Badanie adresu IP DHCP, Wyślij sondę ARP w celu wykrycia konfliktu adresów IP.</span><span class="sxs-lookup"><span data-stu-id="b30f7-153">**NX_DHCP_STATE_ADDRESS_PROBING** DHCP IP Address probing, send the ARP probe to detect IP address conflict.</span></span>

## <a name="dhcp-client-multiple-interface-support"></a><span data-ttu-id="b30f7-154">Obsługa wielu interfejsów klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-154">DHCP Client Multiple Interface Support</span></span>

<span data-ttu-id="b30f7-155">Klient DHCP został wcześniej zaimplementowany do uruchomienia tylko na jednym interfejsie sieciowym.</span><span class="sxs-lookup"><span data-stu-id="b30f7-155">The DHCP Client was previously implemented to run on only a single network interface.</span></span> <span data-ttu-id="b30f7-156">Zachowanie domyślne to (i nadal), aby klient DHCP był uruchamiany w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="b30f7-156">The default behavior was (and still is) for the DHCP Client to run on the primary interface.</span></span> <span data-ttu-id="b30f7-157">Wywołując *nx_dhcp_set_interface_index*, aplikacja może (i nadal może) uruchomić usługę DHCP na pomocniczym interfejsie sieciowym, a nie w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="b30f7-157">By calling *nx_dhcp_set_interface_index*, the application could (and still can) run DHCP on a secondary network interface instead of the primary interface.</span></span>

<span data-ttu-id="b30f7-158">Teraz obsługuje protokół DHCP działający w wielu interfejsach równolegle.</span><span class="sxs-lookup"><span data-stu-id="b30f7-158">It now supports DHCP running on multiple interfaces in parallel.</span></span> <span data-ttu-id="b30f7-159">Zobacz **klienta DHCP na wielu interfejsach jednocześnie** w rozdziale dwa, aby uzyskać szczegółowe informacje dotyczące sposobu uruchamiania klienta DHCP w więcej niż jednym interfejsie fizycznym.</span><span class="sxs-lookup"><span data-stu-id="b30f7-159">See **DHCP Client on Multiple Interfaces Simultaneously** in Chapter Two for specific details how to run DHCP Client on more than one physical interface simultaneously.</span></span>

## <a name="dhcp-user-request"></a><span data-ttu-id="b30f7-160">Żądanie użytkownika DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-160">DHCP User Request</span></span>

<span data-ttu-id="b30f7-161">Gdy serwer DHCP przydzieli adres IP, przetwarzanie klienta DHCP może żądać dodatkowych parametrów — pojedynczo — przy użyciu usługi *nx_dhcp_user_option_request* .</span><span class="sxs-lookup"><span data-stu-id="b30f7-161">Once the DHCP server grants an IP address, the DHCP client processing can request additional parameters — one at a time — by using the *nx_dhcp_user_option_request* service.</span></span>

## <a name="dhcp-client-socket-queue"></a><span data-ttu-id="b30f7-162">Kolejka gniazda klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-162">DHCP Client Socket Queue</span></span> 

<span data-ttu-id="b30f7-163">Klient DHCP automatycznie czyści pakiety emisji z serwerów DHCP przeznaczonych dla innych klientów DHCP z kolejki odbierania gniazda podczas oczekiwania na odpowiedź serwera na siebie.</span><span class="sxs-lookup"><span data-stu-id="b30f7-163">The DHCP Client automatically clears broadcast packets from DHCP Servers intended for other DHCP Clients from its socket receive queue while waiting for Server to respond to itself.</span></span> <span data-ttu-id="b30f7-164">W przypadku zajętej sieci nie może to spowodować porzucenia pakietów przeznaczonych dla klienta.</span><span class="sxs-lookup"><span data-stu-id="b30f7-164">In a busy network, not doing so could cause packets intended for the Client to be dropped.</span></span>

## <a name="dhcp-rfcs"></a><span data-ttu-id="b30f7-165">Specyfikacje RFC protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="b30f7-165">DHCP RFCs</span></span>

<span data-ttu-id="b30f7-166">NetX DHCP jest zgodny z RFC2132, RFC2131 i powiązanymi specyfikacjami RFC.</span><span class="sxs-lookup"><span data-stu-id="b30f7-166">NetX DHCP is compliant with RFC2132, RFC2131, and related RFCs.</span></span>

