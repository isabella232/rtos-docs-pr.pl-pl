---
title: Opis usługi Azure RTO NetX
description: Azure RTO NetX to implementacja standardów protokołów TCP/IP o wysokiej wydajności, w pełni zintegrowana z usługą Azure RTO ThreadX i dostępna dla wszystkich obsługiwanych procesorów.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821487"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="4628e-103">Omówienie usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="4628e-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="4628e-104">Azure RTO NetX to stos sieciowy oparty na protokole TCP/IP IPv4 opartym na sieci, zaprojektowany specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i IoT.</span><span class="sxs-lookup"><span data-stu-id="4628e-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="4628e-105">Azure RTO NetX to oryginalny stos sieci IPv4 firmy Microsoft i jest zasadniczo podzbiorem usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="4628e-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="4628e-106">NetX udostępnia aplikacje osadzone z podstawowymi protokołami sieciowymi, takimi jak IPv4, TCP i UDP, a także kompletnym pakietem dodatkowych protokołów dodatków o wyższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="4628e-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="4628e-107">Niewielki wpływ, szybkie wykonywanie i doskonałe łatwość użycia sprawiają, że usługa Azure RTO NetX idealny wybór dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="4628e-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="4628e-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="4628e-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="4628e-109">Program</span><span class="sxs-lookup"><span data-stu-id="4628e-109">TELNET</span></span>

* <span data-ttu-id="4628e-110">Minimum 0,5 KB i 0,3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-111">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="4628e-111">Client and server support</span></span>
* <span data-ttu-id="4628e-112">Intuicyjne interfejsy API programu Telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="4628e-113">Adres IP</span><span class="sxs-lookup"><span data-stu-id="4628e-113">Auto IP</span></span>

* <span data-ttu-id="4628e-114">Automatyczne przypisywanie adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="4628e-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="4628e-115">Minimalny 1,2 KB, 300 bajtów pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="4628e-116">Intuicyjne interfejsy API AutoIP: *nx_autoip_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="4628e-117">HTTP-Hypertext Transfer Protocol (HTTP)</span><span class="sxs-lookup"><span data-stu-id="4628e-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="4628e-118">Minimalny 2,8 KB do 4,8 KBFLASH, 0,4 KB do 1,0 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-119">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="4628e-119">Client and server support</span></span>
* <span data-ttu-id="4628e-120">Intuicyjne interfejsy API protokołu HTTP: *nx_http_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="4628e-121">SMTP — Simple Mail Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="4628e-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="4628e-122">Minimum 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-123">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="4628e-123">Client support</span></span>
* <span data-ttu-id="4628e-124">Intuicyjne interfejsy API SMTP: *nx_smtp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="4628e-125">DHCP — Dynamic Host Configuration Protocol (DHCP)</span><span class="sxs-lookup"><span data-stu-id="4628e-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="4628e-126">Minimum 3,6 KB do 4,6 KB FLASH, rozmiar pamięci RAM 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="4628e-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-127">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="4628e-127">Client and server support</span></span>
* <span data-ttu-id="4628e-128">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="4628e-128">IPv4 support</span></span>
* <span data-ttu-id="4628e-129">Intuicyjne interfejsy API DHCP: *nx_dhcp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="4628e-130">P0P3 — wersja 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="4628e-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="4628e-131">Minimum 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-132">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="4628e-132">Client support</span></span>
* <span data-ttu-id="4628e-133">Intuicyjne interfejsy API P0P3: *nx_pop3_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="4628e-134">SNMP-Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="4628e-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="4628e-135">Minimum 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-136">Obsługa agentów dla VI, v2 i V3</span><span class="sxs-lookup"><span data-stu-id="4628e-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="4628e-137">Intuicyjne interfejsy API protokołu SNMP: *nx_snmp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="4628e-138">FTP, TFTP-protokół transferu plików (FTP), Trivial File Transfer Protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="4628e-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="4628e-139">FTP minimum 1,8 KB do 7.2 KBFLASH, 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-140">TFTP minimum 1,7 KB do 2.4 KBFLASH, 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-141">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="4628e-141">Client and server support</span></span>
* <span data-ttu-id="4628e-142">Intuicyjne interfejsy API FTP i TFTP: <i>nx_ftp_ *</i> lub <i>nx_tftp_*</i></span><span class="sxs-lookup"><span data-stu-id="4628e-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="4628e-143">PPP-Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="4628e-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="4628e-144">Minimum 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-145">Intuicyjne interfejsy API protokołu PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="4628e-146">SNTP — Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="4628e-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="4628e-147">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="4628e-148">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="4628e-148">Client support</span></span>
* <span data-ttu-id="4628e-149">Intuicyjne interfejsy API SNTP: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="4628e-150">Interfejs API usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="4628e-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="4628e-151">Intuicyjny i spójny interfejs API</span><span class="sxs-lookup"><span data-stu-id="4628e-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="4628e-152">W konwencji nazewnictwa czasowników</span><span class="sxs-lookup"><span data-stu-id="4628e-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="4628e-153">Szybka, zerowa — implementacja interfejsu API</span><span class="sxs-lookup"><span data-stu-id="4628e-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="4628e-154">Wszystkie funkcje interfejsu API mają wiodące <i>nx_ \*</i> do łatwej identyfikacji jako Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="4628e-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="4628e-155">Blokowanie funkcji interfejsu API ma opcjonalny limit czasu wątku</span><span class="sxs-lookup"><span data-stu-id="4628e-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="4628e-156">Opcjonalna warstwa BSD do przenoszenia kodu gniazda starszej wersji</span><span class="sxs-lookup"><span data-stu-id="4628e-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="4628e-157">IGMP — protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="4628e-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="4628e-158">Minimum 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="4628e-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="4628e-159">Obsługa grup multiemisji IPv4</span><span class="sxs-lookup"><span data-stu-id="4628e-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="4628e-160">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="4628e-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="4628e-161">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="4628e-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="4628e-162">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="4628e-163">Intuicyjne interfejsy API protokołu IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="4628e-164">UDP-User Datagram Protocol (UDP)</span><span class="sxs-lookup"><span data-stu-id="4628e-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="4628e-165">Minimalny 2,5 KB, 124 gniazd bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="4628e-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="4628e-166">Szybkie przetwarzanie pakietów TCP w bliskiej WireSpeed:</span><span class="sxs-lookup"><span data-stu-id="4628e-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="4628e-167">Odbieranie 95 MB/s na 100 MB/s, MIKROKONTROLERY @100MHz , 14% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="4628e-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="4628e-168">TX 94 MB/s w dniu 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 10% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="4628e-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="4628e-169">Szybka ścieżka UDP™ technologia</span><span class="sxs-lookup"><span data-stu-id="4628e-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="4628e-170">Brak limitów liczby UDP</span><span class="sxs-lookup"><span data-stu-id="4628e-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="4628e-171">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="4628e-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="4628e-172">Opcjonalne zawieszenie dla odbioru gniazda</span><span class="sxs-lookup"><span data-stu-id="4628e-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="4628e-173">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="4628e-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="4628e-174">Opcjonalne statystyki protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="4628e-174">Optional UDP statistics</span></span>
* <span data-ttu-id="4628e-175">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="4628e-176">Intuicyjne interfejsy API protokołu UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="4628e-177">TCP-Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="4628e-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="4628e-178">Minimalna 10,5 K8 do 12,5 KB FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="4628e-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="4628e-179">Szybkie przetwarzanie pakietów TCP w bliskiej wlrespeed:</span><span class="sxs-lookup"><span data-stu-id="4628e-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="4628e-180">Odbieranie 93 MB/s na 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 20% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="4628e-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="4628e-181">TX 94 MB/s w dniu 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 27% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="4628e-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="4628e-182">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="4628e-182">Reliable connection</span></span>
* <span data-ttu-id="4628e-183">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="4628e-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="4628e-184">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="4628e-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="4628e-185">Opcjonalne zawieszenie dla odbioru i wysyłania gniazd</span><span class="sxs-lookup"><span data-stu-id="4628e-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="4628e-186">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="4628e-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="4628e-187">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="4628e-187">Optional TCP statistics</span></span>
* <span data-ttu-id="4628e-188">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="4628e-189">Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="4628e-190">ICMP — protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="4628e-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="4628e-191">Minimum 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="4628e-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="4628e-192">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="4628e-192">IPv4 support</span></span>
* <span data-ttu-id="4628e-193">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="4628e-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="4628e-194">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="4628e-194">Ping request and ping response</span></span>
* <span data-ttu-id="4628e-195">Opcjonalne zawieszenie wątku w żądaniach ping</span><span class="sxs-lookup"><span data-stu-id="4628e-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="4628e-196">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="4628e-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="4628e-197">Opcjonalne statystyki protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="4628e-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="4628e-198">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="4628e-199">Intuicyjne interfejsy API protokołu ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="4628e-200">IPv4 — protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="4628e-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="4628e-201">Minimum 3,5 KB do 8,5 KB FLASH, Powierzchnia 2 KB do 3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="4628e-202">Architektura™ Piconet</span><span class="sxs-lookup"><span data-stu-id="4628e-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="4628e-203">Szybka, prawie wirespeeda wydajność</span><span class="sxs-lookup"><span data-stu-id="4628e-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="4628e-204">Obsługa wielu interfejsów</span><span class="sxs-lookup"><span data-stu-id="4628e-204">Multiple interface support</span></span>
* <span data-ttu-id="4628e-205">Obsługa wieloadresowa</span><span class="sxs-lookup"><span data-stu-id="4628e-205">Multihomed support</span></span>
* <span data-ttu-id="4628e-206">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="4628e-206">Static routing support</span></span>
* <span data-ttu-id="4628e-207">Obsługa fragmentacji/odzestawów IP</span><span class="sxs-lookup"><span data-stu-id="4628e-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="4628e-208">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="4628e-208">IPv4 Support</span></span>
* <span data-ttu-id="4628e-209">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="4628e-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="4628e-210">Certyfikacja logo gotowego do fazy II</span><span class="sxs-lookup"><span data-stu-id="4628e-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="4628e-211">Opcjonalne statystyki adresów IP</span><span class="sxs-lookup"><span data-stu-id="4628e-211">Optional IP statistics</span></span>
* <span data-ttu-id="4628e-212">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej</span><span class="sxs-lookup"><span data-stu-id="4628e-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="4628e-213">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="4628e-214">Intuicyjne interfejsy API warstwy IP: *nx_ip_ \**, *nxd_ip_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="4628e-215">Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D i EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="4628e-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="4628e-216">ARP/RARP — Protokół rozpoznawania adresów (ARP), odwrotny Protokół rozpoznawania adresów (RARP)</span><span class="sxs-lookup"><span data-stu-id="4628e-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="4628e-217">Minimum 1,7 KB, rozmiar pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="4628e-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="4628e-218">Dynamiczne rozpoznawanie 32 BLT IPv4 i 48-BLT adresów MAC</span><span class="sxs-lookup"><span data-stu-id="4628e-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="4628e-219">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="4628e-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="4628e-220">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP</span><span class="sxs-lookup"><span data-stu-id="4628e-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="4628e-221">Obsługa klienta w usłudze ARP</span><span class="sxs-lookup"><span data-stu-id="4628e-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="4628e-222">Opcjonalna Statystyka ARP/RARP określona przez aplikację</span><span class="sxs-lookup"><span data-stu-id="4628e-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="4628e-223">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="4628e-224">Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *nx_rarp_ \**</span><span class="sxs-lookup"><span data-stu-id="4628e-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="4628e-225">ETHERNET, Wi-Fi, BLUETOOTH LE, 15,4 itd.</span><span class="sxs-lookup"><span data-stu-id="4628e-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="4628e-226">Niewielkie rozmiary</span><span class="sxs-lookup"><span data-stu-id="4628e-226">Small-footprint</span></span>

<span data-ttu-id="4628e-227">Usługa Azure RTO NetX ma niewielki zasięg z 9 KB do 15 KB w przypadku podstawowej obsługi protokołów IP i UDP.</span><span class="sxs-lookup"><span data-stu-id="4628e-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="4628e-228">Do obsługi funkcji TCP jest wymagana dodatkowa ilość pamięci o wartości 10 KB do 13 KB.</span><span class="sxs-lookup"><span data-stu-id="4628e-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="4628e-229">Użycie pamięci RAM usługi Azure RTO NetX zazwyczaj mieści się w zakresie od 2,6 KB do 3,6 KB oraz pamięci puli pakietów zdefiniowanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4628e-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="4628e-230">Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar usługi Azure RTO NetX jest automatycznie skalowany w oparciu o usługi używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4628e-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="4628e-231">To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.</span><span class="sxs-lookup"><span data-stu-id="4628e-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="4628e-232">Szybkie wykonywanie</span><span class="sxs-lookup"><span data-stu-id="4628e-232">Fast execution</span></span>

<span data-ttu-id="4628e-233">Usługa Azure RTO NetX zapewnia implementację wysyłania/odbierania pakietów o zerowej kopii i ma wysoką integrację z usługą Azure RTO ThreadX w celu uzyskania najszybszej możliwej wydajności.</span><span class="sxs-lookup"><span data-stu-id="4628e-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="4628e-234">Na przykład usługa Azure RTO NetX może zazwyczaj osiągnąć niemal WireSpeed transfery danych na procesorze 80 MHz (lub mniej), jednocześnie używając tylko małego procentu cykli procesora.</span><span class="sxs-lookup"><span data-stu-id="4628e-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="4628e-235">Proste i łatwe w użyciu</span><span class="sxs-lookup"><span data-stu-id="4628e-235">Simple, easy-to-use</span></span>

<span data-ttu-id="4628e-236">Korzystanie z usługi Azure RTO NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="4628e-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="4628e-237">Interfejs API usługi Azure RTO NetX jest intuicyjny i wysoce funkcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4628e-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="4628e-238">Nazwy interfejsów API składają się z prawdziwych słów, a nie "alfabetu" (zup) ani nazw o wysokim skrócie, które są często używane w innych produktach sieciowych.</span><span class="sxs-lookup"><span data-stu-id="4628e-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="4628e-239">Wszystkie interfejsy API usługi Azure RTO NetX mają wiodące *nx_* i są zgodne z konwencją nazewnictwa czasowników.</span><span class="sxs-lookup"><span data-stu-id="4628e-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="4628e-240">Ponadto istnieje spójność funkcjonalna w całym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="4628e-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="4628e-241">Na przykład wszystkie funkcje interfejsu API, które zawieszają, mają opcjonalny limit czasu, który działa w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="4628e-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="4628e-242">W przypadku starszych aplikacji usługa Azure RTO NetX oferuje dodatkową warstwę zgodną z gniazdem BSD.</span><span class="sxs-lookup"><span data-stu-id="4628e-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="4628e-243">Ta warstwa ułatwia deweloperom łatwe Migrowanie dużych aplikacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="4628e-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="4628e-244">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="4628e-244">Interoperability verification</span></span>

<span data-ttu-id="4628e-245">Usługa Azure RTO NetX jest zgodna ze standardami RFC i oferuje pełną współdziałanie z urządzeniami dla większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="4628e-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="4628e-246">Usługa Azure RTO NetX korzysta również z standardowej w branży IxANVL (zautomatyzowanej biblioteki sprawdzania poprawności sieci) dla implementacji protokołu TCP/IP w ramach platformy Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="4628e-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="4628e-247">Technologia zaawansowana</span><span class="sxs-lookup"><span data-stu-id="4628e-247">Advanced technology</span></span>

<span data-ttu-id="4628e-248">Usługa Azure RTO NetX jest zaawansowaną technologią obejmującą następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="4628e-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="4628e-249">Architektura™ Piconet</span><span class="sxs-lookup"><span data-stu-id="4628e-249">Piconet™ architecture</span></span>
* <span data-ttu-id="4628e-250">Skalowanie automatyczne</span><span class="sxs-lookup"><span data-stu-id="4628e-250">automatic scaling</span></span>
* <span data-ttu-id="4628e-251">™ Fast-Path technologii UDP</span><span class="sxs-lookup"><span data-stu-id="4628e-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="4628e-252">elastyczne zarządzanie pakietami</span><span class="sxs-lookup"><span data-stu-id="4628e-252">flexible packet management</span></span>
* <span data-ttu-id="4628e-253">Interfejs API kopiowania i implementacja protokołu zero</span><span class="sxs-lookup"><span data-stu-id="4628e-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="4628e-254">Obsługa wieloadresowa</span><span class="sxs-lookup"><span data-stu-id="4628e-254">multihomed support</span></span>
* <span data-ttu-id="4628e-255">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="4628e-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="4628e-256">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="4628e-256">static routing support</span></span>
* <span data-ttu-id="4628e-257">Obsługa analizy systemu Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4628e-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="4628e-258">Najszybszy czas wprowadzenia na rynek</span><span class="sxs-lookup"><span data-stu-id="4628e-258">Fastest time-to-market</span></span>

<span data-ttu-id="4628e-259">Usługa Azure RTO NetX umożliwia łatwe instalowanie, uczenie się, używanie, debugowanie, weryfikowanie, certyfikowanie i konserwowanie.</span><span class="sxs-lookup"><span data-stu-id="4628e-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="4628e-260">W związku z tym usługa Azure RTO NetX jest jednym z najpopularniejszych stosów TCP/IP dla osadzonych urządzeń IoT, w tym wielu SoC z usługi Broadcom, Gainspan i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="4628e-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="4628e-261">Nasza spójna przedział czasu na rynek jest oparta na:</span><span class="sxs-lookup"><span data-stu-id="4628e-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="4628e-262">Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO NetX](about-this-guide.md) i zapoznaj się z Tobą.</span><span class="sxs-lookup"><span data-stu-id="4628e-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="4628e-263">Ukończ dostępność kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="4628e-263">complete source code availability</span></span>
* <span data-ttu-id="4628e-264">łatwy w użyciu interfejs API</span><span class="sxs-lookup"><span data-stu-id="4628e-264">easy-to-use API</span></span>
* <span data-ttu-id="4628e-265">kompleksowy i zaawansowany zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="4628e-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="4628e-266">Jedna prosta licencja</span><span class="sxs-lookup"><span data-stu-id="4628e-266">One Simple License</span></span>

<span data-ttu-id="4628e-267">Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.</span><span class="sxs-lookup"><span data-stu-id="4628e-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="4628e-268">Pełny kod źródłowy o najwyższej jakości</span><span class="sxs-lookup"><span data-stu-id="4628e-268">Full, highest-quality source code</span></span>

<span data-ttu-id="4628e-269">W ciągu lat kod źródłowy usługi Azure RTO NetX ustawił na pasku jakość i łatwość interpretacji.</span><span class="sxs-lookup"><span data-stu-id="4628e-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="4628e-270">Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.</span><span class="sxs-lookup"><span data-stu-id="4628e-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="4628e-271">Obsługuje najpopularniejsze architektury</span><span class="sxs-lookup"><span data-stu-id="4628e-271">Supports most popular architectures</span></span>

<span data-ttu-id="4628e-272">Usługa Azure RTO NetX działa dla najpopularniejszych mikroprocesorów 32-bitowych, wbudowanych, w pełni przetestowanych i w pełni obsługiwanych, w tym następujących architektur zaawansowanych:</span><span class="sxs-lookup"><span data-stu-id="4628e-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="4628e-273">**Urządzenia analogowe**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="4628e-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="4628e-274">**Andes rdzeń**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="4628e-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="4628e-275">**Ambiqmicro**: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="4628e-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="4628e-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="4628e-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="4628e-277">**Erze**: Xtensa, romb</span><span class="sxs-lookup"><span data-stu-id="4628e-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="4628e-278">**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="4628e-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="4628e-279">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="4628e-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="4628e-280">**EnSilica**: ESI-RISC</span><span class="sxs-lookup"><span data-stu-id="4628e-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="4628e-281">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="4628e-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="4628e-282">**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="4628e-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="4628e-283">**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="4628e-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="4628e-284">**Mikrośrednik**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="4628e-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="4628e-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="4628e-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="4628e-286">**Renesas**: sh, HS, V850, RX, rz, synergia</span><span class="sxs-lookup"><span data-stu-id="4628e-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="4628e-287">**Krzem Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="4628e-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="4628e-288">**SynopSYS**: Arc 600, 700, łuk em, łuk HS</span><span class="sxs-lookup"><span data-stu-id="4628e-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="4628e-289">**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="4628e-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="4628e-290">**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="4628e-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="4628e-291">**Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="4628e-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="4628e-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="4628e-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="4628e-293">*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacunkami i mogą być inne na platformie deweloperskiej.*</span><span class="sxs-lookup"><span data-stu-id="4628e-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
