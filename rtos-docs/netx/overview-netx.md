---
title: Opis Azure RTOS NetX
description: Azure RTOS NetX to implementacja standardów protokołu TCP/IP o wysokiej wydajności, w pełni zintegrowana z platformą Azure RTOS ThreadX i dostępna dla wszystkich obsługiwanych procesorów.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 7c864c23f019e4841ddb3096fde663c8039baf44
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171322"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="9f292-103">Omówienie Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="9f292-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="9f292-104">Azure RTOS NetX to osadzony stos sieciowy TCP/IP IPv4 klasy przemysłowej zaprojektowany specjalnie z myślą o aplikacjach osadzonych, osadzonych w czasie rzeczywistym i aplikacjach IoT.</span><span class="sxs-lookup"><span data-stu-id="9f292-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="9f292-105">Azure RTOS NetX jest oryginalnym stosem sieciowym protokołu IPv4 firmy Microsoft i zasadniczo jest podzbiorem Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="9f292-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="9f292-106">NetX udostępnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="9f292-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="9f292-107">Niewielkie zużycie pamięci, szybkie wykonywanie i najwyższa łatwość użycia sprawiają, że Azure RTOS NetX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="9f292-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="9f292-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="9f292-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="9f292-109">Telnet</span><span class="sxs-lookup"><span data-stu-id="9f292-109">TELNET</span></span>

* <span data-ttu-id="9f292-110">Minimalna 0,5 KB i 0,3 KB pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="9f292-110">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="9f292-111">Obsługa klientów i serwerów.</span><span class="sxs-lookup"><span data-stu-id="9f292-111">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="9f292-112">Automatyczny adres IP</span><span class="sxs-lookup"><span data-stu-id="9f292-112">Auto IP</span></span>

* <span data-ttu-id="9f292-113">Automatyczne przypisywanie adresów IPv4.</span><span class="sxs-lookup"><span data-stu-id="9f292-113">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="9f292-114">Minimalna 1,2 KB, 300 bajtów pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="9f292-114">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="9f292-115">HTTP — protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="9f292-115">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="9f292-116">Minimalnie od 2,8 KB do 4,8 KB UKOŚNIKA, od 0,4 KB do 1,0 KB pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="9f292-116">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="9f292-117">Obsługa klientów i serwerów.</span><span class="sxs-lookup"><span data-stu-id="9f292-117">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="9f292-118">SMTP — Simple Mail Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="9f292-118">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="9f292-119">Minimalnie 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-119">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-120">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="9f292-120">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="9f292-121">DHCP — Dynamic Host Configuration Protocol (DHCP)</span><span class="sxs-lookup"><span data-stu-id="9f292-121">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="9f292-122">Minimalna ilość pamięci FLASH od 3,6 KB do 4,6 KB, 2,7 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-122">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-123">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="9f292-123">Client and server support</span></span>
* <span data-ttu-id="9f292-124">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="9f292-124">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="9f292-125">P0P3 — protokół Post Office Protocol w wersji 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="9f292-125">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="9f292-126">Minimalnie 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-126">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-127">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="9f292-127">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="9f292-128">SNMP — Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="9f292-128">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="9f292-129">Minimalna 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-129">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-130">Obsługa agentów dla wersji VI, V2 i V3</span><span class="sxs-lookup"><span data-stu-id="9f292-130">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="9f292-131">FTP, TFTP — protokół transferu plików (FTP), Trivial File Transfer Protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="9f292-131">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="9f292-132">FTP minimalnie od 1,8 KB do 7,2 KBFLASH, od 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-132">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-134">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="9f292-134">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="9f292-135">PPP — Protokół Polnt-to-PoInt (PPP)</span><span class="sxs-lookup"><span data-stu-id="9f292-135">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="9f292-136">Minimalnie 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-136">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="9f292-137">Niezawodna i niezawodna.</span><span class="sxs-lookup"><span data-stu-id="9f292-137">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="9f292-138">SNTP — prosty protokół czasu sieciowego (SNTP)</span><span class="sxs-lookup"><span data-stu-id="9f292-138">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="9f292-139">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="9f292-139">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="9f292-140">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="9f292-140">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="9f292-141">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="9f292-141">Azure RTOS NetX API</span></span>

* <span data-ttu-id="9f292-142">Szybka implementacja interfejsu API bez kopiowania</span><span class="sxs-lookup"><span data-stu-id="9f292-142">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="9f292-143">Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda</span><span class="sxs-lookup"><span data-stu-id="9f292-143">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="9f292-144">IGMP — protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="9f292-144">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="9f292-145">Minimalna 2,5 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="9f292-145">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="9f292-146">Obsługa grup multiemisji protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="9f292-146">IPv4 multicast group support</span></span>
* <span data-ttu-id="9f292-147">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="9f292-147">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="9f292-148">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="9f292-148">Optional IGMP statistics</span></span>
* <span data-ttu-id="9f292-149">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="9f292-149">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="9f292-150">UDP — protokół UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="9f292-150">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="9f292-151">Minimalna pamięć FLASH 2,5 KB, 124 bajty pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="9f292-151">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="9f292-152">Szybkie przetwarzanie pakietów TCP przy użyciu ruchu najbliższego wire speed:</span><span class="sxs-lookup"><span data-stu-id="9f292-152">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="9f292-153">RX 95 Mb/s na Ethernet 100 Mb/s, @100MHz MIKROU, 14% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="9f292-153">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="9f292-154">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 10% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="9f292-154">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="9f292-155">Technologia Szybka ścieżka UDP™ technologii</span><span class="sxs-lookup"><span data-stu-id="9f292-155">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="9f292-156">Brak limitów liczby protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="9f292-156">No limits on the number of UDP</span></span>
* <span data-ttu-id="9f292-157">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="9f292-157">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="9f292-158">Opcjonalne zawieszenie podczas odbierania gniazda</span><span class="sxs-lookup"><span data-stu-id="9f292-158">Optional suspension on socket receive</span></span>
* <span data-ttu-id="9f292-159">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="9f292-159">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9f292-160">Opcjonalne statystyki UDP</span><span class="sxs-lookup"><span data-stu-id="9f292-160">Optional UDP statistics</span></span>
* <span data-ttu-id="9f292-161">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="9f292-161">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="9f292-162">TCP — Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="9f292-162">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="9f292-163">Minimalna ilość pamięci RAM od 10,5 K8 do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="9f292-163">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="9f292-164">Szybkie przetwarzanie pakietów TCP w pobliżu wlre speed:</span><span class="sxs-lookup"><span data-stu-id="9f292-164">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="9f292-165">RX 93 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, wykorzystanie 20% MIKROU</span><span class="sxs-lookup"><span data-stu-id="9f292-165">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="9f292-166">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 27% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="9f292-166">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="9f292-167">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="9f292-167">Reliable connection</span></span>
* <span data-ttu-id="9f292-168">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="9f292-168">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="9f292-169">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="9f292-169">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="9f292-170">Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda</span><span class="sxs-lookup"><span data-stu-id="9f292-170">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="9f292-171">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="9f292-171">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9f292-172">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="9f292-172">Optional TCP statistics</span></span>
* <span data-ttu-id="9f292-173">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="9f292-173">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="9f292-174">ICMP — protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="9f292-174">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="9f292-175">Minimalna pamięć FLASH 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="9f292-175">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="9f292-176">Obsługa protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="9f292-176">IPv4 support</span></span>
* <span data-ttu-id="9f292-177">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="9f292-177">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="9f292-178">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="9f292-178">Ping request and ping response</span></span>
* <span data-ttu-id="9f292-179">Opcjonalne zawieszenie wątku na żądaniach ping</span><span class="sxs-lookup"><span data-stu-id="9f292-179">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="9f292-180">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="9f292-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9f292-181">Opcjonalne statystyki ICMP</span><span class="sxs-lookup"><span data-stu-id="9f292-181">Optional ICMP statistics</span></span>
* <span data-ttu-id="9f292-182">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="9f292-182">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="9f292-183">IPv4 — protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="9f292-183">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="9f292-184">Minimalnie od 3,5 KB do 8,5 KB pamięci FLASH, od 2 KB do 3 KB pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="9f292-184">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="9f292-185">Piconet™ Architecture (Architektura aplikacji Piconet).</span><span class="sxs-lookup"><span data-stu-id="9f292-185">Piconet™ Architecture.</span></span>
* <span data-ttu-id="9f292-186">Szybka, prawie wire speed wydajność.</span><span class="sxs-lookup"><span data-stu-id="9f292-186">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="9f292-187">Obsługa wielu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9f292-187">Multiple interface support.</span></span>
* <span data-ttu-id="9f292-188">Obsługa wielu domów.</span><span class="sxs-lookup"><span data-stu-id="9f292-188">Multi-homed support.</span></span>
* <span data-ttu-id="9f292-189">Obsługa routingu statycznego.</span><span class="sxs-lookup"><span data-stu-id="9f292-189">Static routing support.</span></span>
* <span data-ttu-id="9f292-190">Obsługa fragmentacji/ponownego zsembmbowania adresów IP.</span><span class="sxs-lookup"><span data-stu-id="9f292-190">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="9f292-191">Obsługa protokołu IPv4.</span><span class="sxs-lookup"><span data-stu-id="9f292-191">IPv4 Support.</span></span>
* <span data-ttu-id="9f292-192">Zweryfikowane przez IxANVL IxANVL.</span><span class="sxs-lookup"><span data-stu-id="9f292-192">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="9f292-193">Certyfikacja gotowego logo fazy II.</span><span class="sxs-lookup"><span data-stu-id="9f292-193">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="9f292-194">Opcjonalne statystyki adresów IP.</span><span class="sxs-lookup"><span data-stu-id="9f292-194">Optional IP statistics.</span></span>
* <span data-ttu-id="9f292-195">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej.</span><span class="sxs-lookup"><span data-stu-id="9f292-195">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="9f292-196">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="9f292-196">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="9f292-197">ARP/RARP — protokół rozpoznawania adresów (ARP, Address Resolution Protocol), rarp (Reverse Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="9f292-197">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="9f292-198">Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="9f292-198">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="9f292-199">Dynamiczna rozdzielczość 32-blt adresów IPv4 i 48-blt adresów MAC.</span><span class="sxs-lookup"><span data-stu-id="9f292-199">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="9f292-200">Zweryfikowane przez IxANVL IxANVL.</span><span class="sxs-lookup"><span data-stu-id="9f292-200">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="9f292-201">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP.</span><span class="sxs-lookup"><span data-stu-id="9f292-201">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="9f292-202">Obsługa dużych ARP.</span><span class="sxs-lookup"><span data-stu-id="9f292-202">Gratuitous ARP support.</span></span>
* <span data-ttu-id="9f292-203">Opcjonalne statystyki ARP/RARP określone przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9f292-203">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="9f292-204">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="9f292-204">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="9f292-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4 itp.</span><span class="sxs-lookup"><span data-stu-id="9f292-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="9f292-206">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="9f292-206">Interoperability verification</span></span>

<span data-ttu-id="9f292-207">Azure RTOS NetX jest zgodna ze standardami RFC i oferuje pełne współdziałanie z urządzeniami dla większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="9f292-207">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="9f292-208">Azure RTOS NetX korzysta również ze standardowej w branży biblioteki IxANVL (Automated Network Validation Library) na Azure RTOS implementacji podstawowego protokołu TCP/IP NetX Core.</span><span class="sxs-lookup"><span data-stu-id="9f292-208">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="9f292-209">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="9f292-209">Advanced technology</span></span>

<span data-ttu-id="9f292-210">Azure RTOS NetX to zaawansowana technologia, która obejmuje następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="9f292-210">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="9f292-211">Piconet™ architektury.</span><span class="sxs-lookup"><span data-stu-id="9f292-211">Piconet™ architecture.</span></span>
* <span data-ttu-id="9f292-212">Automatyczne skalowanie.</span><span class="sxs-lookup"><span data-stu-id="9f292-212">Automatic scaling.</span></span>
* <span data-ttu-id="9f292-213">Technologia Fast-Path UDP™.</span><span class="sxs-lookup"><span data-stu-id="9f292-213">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="9f292-214">Elastyczne zarządzanie pakietami.</span><span class="sxs-lookup"><span data-stu-id="9f292-214">Flexible packet management.</span></span>
* <span data-ttu-id="9f292-215">Interfejs API bez kopiowania i implementacja.</span><span class="sxs-lookup"><span data-stu-id="9f292-215">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="9f292-216">Obsługa wielu domu.</span><span class="sxs-lookup"><span data-stu-id="9f292-216">Multi-homed support.</span></span>
* <span data-ttu-id="9f292-217">Opcjonalny limit czasu dla całego zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="9f292-217">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="9f292-218">Obsługa routingu statycznego.</span><span class="sxs-lookup"><span data-stu-id="9f292-218">Static routing support.</span></span>
* <span data-ttu-id="9f292-219">Azure RTOS analizy systemu TraceX.</span><span class="sxs-lookup"><span data-stu-id="9f292-219">Azure RTOS TraceX system analysis support.</span></span>
