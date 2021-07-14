---
title: Opis Azure RTOS NetX
description: Azure RTOS NetX to implementacja standardów protokołu TCP/IP o wysokiej wydajności, w pełni zintegrowana z platformą Azure RTOS ThreadX i dostępna dla wszystkich obsługiwanych procesorów.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754849"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="d9a7e-103">Omówienie Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="d9a7e-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="d9a7e-104">Azure RTOS NetX to osadzony stos sieciowy TCP/IP IPv4 klasy przemysłowej zaprojektowany specjalnie z myślą o aplikacjach osadzonych, osadzonych w czasie rzeczywistym i aplikacjach IoT.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="d9a7e-105">Azure RTOS NetX jest oryginalnym stosem sieciowym protokołu IPv4 firmy Microsoft i zasadniczo jest podzbiorem Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="d9a7e-106">NetX udostępnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="d9a7e-107">Niewielkie zużycie pamięci, szybkie wykonywanie i najwyższa łatwość użycia sprawiają, że Azure RTOS NetX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="d9a7e-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="d9a7e-108">API protocols</span></span>
<span data-ttu-id="d9a7e-109">Azure RTOS NetX zapewnia obsługę następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-109">Azure RTOS NetX provides support for the following.</span></span>

### <a name="telnet"></a><span data-ttu-id="d9a7e-110">Telnet</span><span class="sxs-lookup"><span data-stu-id="d9a7e-110">TELNET</span></span>

* <span data-ttu-id="d9a7e-111">Minimalna 0,5 KB i 0,3 KB pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-111">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="d9a7e-112">Obsługa klientów i serwerów.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-112">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="d9a7e-113">Automatyczny adres IP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-113">Auto IP</span></span>

* <span data-ttu-id="d9a7e-114">Automatyczne przypisywanie adresów IPv4.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-114">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="d9a7e-115">Minimalna 1,2 KB, 300 bajtów pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-115">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="d9a7e-116">HTTP — protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-116">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="d9a7e-117">Minimalnie od 2,8 KB do 4,8 KB UKOŚNIKA, od 0,4 KB do 1,0 KB pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-117">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="d9a7e-118">Obsługa klientów i serwerów.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-118">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="d9a7e-119">SMTP — Simple Mail Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-119">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="d9a7e-120">Minimalnie 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-120">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-121">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="d9a7e-121">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="d9a7e-122">DHCP — Dynamic Host Configuration Protocol (DHCP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-122">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="d9a7e-123">Minimalnie od 3,6 KB do 4,6 KB pamięci FLASH, 2,7 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-123">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-124">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="d9a7e-124">Client and server support</span></span>
* <span data-ttu-id="d9a7e-125">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="d9a7e-125">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="d9a7e-126">P0P3 — protokół post Office w wersji 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-126">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="d9a7e-127">Minimalnie 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-127">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-128">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="d9a7e-128">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="d9a7e-129">SNMP — Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-129">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="d9a7e-130">Minimalna 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-130">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-131">Obsługa agentów dla wersji VI, V2 i V3</span><span class="sxs-lookup"><span data-stu-id="d9a7e-131">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="d9a7e-132">FTP, TFTP — protokół transferu plików (FTP), Trivial File Transfer Protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-132">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="d9a7e-133">FTP Minimalnie od 1,8 KB do 7,2 KB UKOŚNIKA, od 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-133">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-134">TFTP minimalnie od 1,7 KB do 2,4 KB UKOŚNIKA, od 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-134">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-135">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="d9a7e-135">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="d9a7e-136">PPP — protokół Polnt-to-PoInt (PPP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-136">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="d9a7e-137">Minimalnie 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-137">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="d9a7e-138">Niezawodna i niezawodna.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-138">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="d9a7e-139">SNTP — prosty protokół czasu sieciowego (SNTP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-139">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="d9a7e-140">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="d9a7e-140">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="d9a7e-141">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="d9a7e-141">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="d9a7e-142">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="d9a7e-142">Azure RTOS NetX API</span></span>

* <span data-ttu-id="d9a7e-143">Szybka implementacja interfejsu API bez kopiowania</span><span class="sxs-lookup"><span data-stu-id="d9a7e-143">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="d9a7e-144">Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda</span><span class="sxs-lookup"><span data-stu-id="d9a7e-144">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="d9a7e-145">IGMP — protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-145">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="d9a7e-146">Minimalna 2,5 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="d9a7e-146">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="d9a7e-147">Obsługa grup multiemisji protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="d9a7e-147">IPv4 multicast group support</span></span>
* <span data-ttu-id="d9a7e-148">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="d9a7e-148">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d9a7e-149">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-149">Optional IGMP statistics</span></span>
* <span data-ttu-id="d9a7e-150">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d9a7e-150">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="d9a7e-151">UDP — protokół UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-151">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="d9a7e-152">Minimalna pamięć FLASH 2,5 KB, 124 bajty pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="d9a7e-152">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="d9a7e-153">Szybkie przetwarzanie pakietów TCP prawie z wire speed:</span><span class="sxs-lookup"><span data-stu-id="d9a7e-153">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="d9a7e-154">RX 95 Mb/s na 100 Mb/s Ethernet, @100MHz MCU, 14% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="d9a7e-154">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="d9a7e-155">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 10% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="d9a7e-155">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="d9a7e-156">Technologia Szybka ścieżka UDP™ technologii</span><span class="sxs-lookup"><span data-stu-id="d9a7e-156">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="d9a7e-157">Brak limitów liczby protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-157">No limits on the number of UDP</span></span>
* <span data-ttu-id="d9a7e-158">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="d9a7e-158">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d9a7e-159">Opcjonalne zawieszenie podczas odbierania gniazda</span><span class="sxs-lookup"><span data-stu-id="d9a7e-159">Optional suspension on socket receive</span></span>
* <span data-ttu-id="d9a7e-160">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="d9a7e-160">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d9a7e-161">Opcjonalne statystyki UDP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-161">Optional UDP statistics</span></span>
* <span data-ttu-id="d9a7e-162">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d9a7e-162">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="d9a7e-163">TCP — Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-163">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="d9a7e-164">Minimalnie od 10,5 KB do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="d9a7e-164">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="d9a7e-165">Szybkie, prawie wlre speed przetwarzanie pakietów TCP:</span><span class="sxs-lookup"><span data-stu-id="d9a7e-165">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="d9a7e-166">RX 93 Mb/s na 100 Mb/s Ethernet, @100MHz MCU, 20% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="d9a7e-166">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="d9a7e-167">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 27% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="d9a7e-167">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="d9a7e-168">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="d9a7e-168">Reliable connection</span></span>
* <span data-ttu-id="d9a7e-169">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-169">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="d9a7e-170">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="d9a7e-170">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d9a7e-171">Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda</span><span class="sxs-lookup"><span data-stu-id="d9a7e-171">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="d9a7e-172">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="d9a7e-172">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d9a7e-173">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-173">Optional TCP statistics</span></span>
* <span data-ttu-id="d9a7e-174">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d9a7e-174">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="d9a7e-175">ICMP — protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-175">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="d9a7e-176">Minimalna 2,5 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="d9a7e-176">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="d9a7e-177">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="d9a7e-177">IPv4 support</span></span>
* <span data-ttu-id="d9a7e-178">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="d9a7e-178">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d9a7e-179">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="d9a7e-179">Ping request and ping response</span></span>
* <span data-ttu-id="d9a7e-180">Opcjonalne wstrzymanie wątku dla żądań ping</span><span class="sxs-lookup"><span data-stu-id="d9a7e-180">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="d9a7e-181">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="d9a7e-181">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d9a7e-182">Opcjonalne statystyki ICMP</span><span class="sxs-lookup"><span data-stu-id="d9a7e-182">Optional ICMP statistics</span></span>
* <span data-ttu-id="d9a7e-183">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d9a7e-183">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="d9a7e-184">IPv4 — protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-184">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="d9a7e-185">Minimalnie od 3,5 KB do 8,5 KB pamięci FLASH, od 2 KB do 3 KB pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-185">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="d9a7e-186">Piconet™ Architecture (Architektura aplikacji Piconet).</span><span class="sxs-lookup"><span data-stu-id="d9a7e-186">Piconet™ Architecture.</span></span>
* <span data-ttu-id="d9a7e-187">Szybka, prawie wire speed wydajność.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-187">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="d9a7e-188">Obsługa wielu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-188">Multiple interface support.</span></span>
* <span data-ttu-id="d9a7e-189">Obsługa wielu domów.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-189">Multi-homed support.</span></span>
* <span data-ttu-id="d9a7e-190">Obsługa routingu statycznego.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-190">Static routing support.</span></span>
* <span data-ttu-id="d9a7e-191">Obsługa fragmentacji/ponownego zsembmbowania adresów IP.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-191">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="d9a7e-192">Obsługa protokołu IPv4.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-192">IPv4 Support.</span></span>
* <span data-ttu-id="d9a7e-193">Zweryfikowane przez IxANVL IxANVL.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-193">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="d9a7e-194">Certyfikacja gotowego logo fazy II.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-194">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="d9a7e-195">Opcjonalne statystyki adresów IP.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-195">Optional IP statistics.</span></span>
* <span data-ttu-id="d9a7e-196">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-196">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="d9a7e-197">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-197">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="d9a7e-198">ARP/RARP — protokół rozpoznawania adresów (ARP, Address Resolution Protocol), rarp (Reverse Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="d9a7e-198">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="d9a7e-199">Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-199">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="d9a7e-200">Dynamiczna rozdzielczość 32-blt adresów IPv4 i 48-blt adresów MAC.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-200">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="d9a7e-201">Zweryfikowane przez IxANVL IxANVL.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-201">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="d9a7e-202">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-202">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="d9a7e-203">Obsługa szosowego ARP.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-203">Gratuitous ARP support.</span></span>
* <span data-ttu-id="d9a7e-204">Opcjonalne statystyki ARP/RARP określone przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-204">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="d9a7e-205">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-205">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="d9a7e-206">Ethernet, Wi-Fi, BLUETOOTH LE, 15.4 itp.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-206">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="d9a7e-207">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="d9a7e-207">Interoperability verification</span></span>

<span data-ttu-id="d9a7e-208">Azure RTOS NetX jest zgodna ze standardami RFC i oferuje pełne współdziałanie z urządzeniami większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-208">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices from most vendors.</span></span> <span data-ttu-id="d9a7e-209">Azure RTOS NetX korzysta również ze standardowej w branży biblioteki IxANVL (Automated Network Validation Library) do implementacji podstawowego protokołu TCP/IP Azure RTOS NetX NetX Core.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-209">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="d9a7e-210">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="d9a7e-210">Advanced technology</span></span>

<span data-ttu-id="d9a7e-211">Azure RTOS NetX to zaawansowana technologia, która obejmuje następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-211">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="d9a7e-212">Piconet™ architektura.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-212">Piconet™ architecture.</span></span>
* <span data-ttu-id="d9a7e-213">Automatyczne skalowanie.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-213">Automatic scaling.</span></span>
* <span data-ttu-id="d9a7e-214">Technologia Fast-Path UDP™.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-214">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="d9a7e-215">Elastyczne zarządzanie pakietami.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-215">Flexible packet management.</span></span>
* <span data-ttu-id="d9a7e-216">Interfejs API bez kopiowania i implementacja.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-216">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="d9a7e-217">Obsługa wielu domów.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-217">Multi-homed support.</span></span>
* <span data-ttu-id="d9a7e-218">Opcjonalny limit czasu dla całego zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-218">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="d9a7e-219">Obsługa routingu statycznego.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-219">Static routing support.</span></span>
* <span data-ttu-id="d9a7e-220">Azure RTOS analizy systemu TraceX.</span><span class="sxs-lookup"><span data-stu-id="d9a7e-220">Azure RTOS TraceX system analysis support.</span></span>
