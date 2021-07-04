---
title: Understand Azure RTOS NetX Duo
description: Azure RTOS NetX Duo to zaawansowany stos sieciowy klasy przemysłowej TCP/IP zaprojektowany specjalnie z myślą o głęboko osadzonych aplikacjach czasu rzeczywistego i IoT.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549338"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="bd9b5-103">Omówienie Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="bd9b5-104">Azure RTOS NetX Duo osadzony stos sieciowy TCP/IP to zaawansowany stos sieciowy TCP/IP klasy przemysłowej firmy Microsoft, podwójny stos sieciowy IPv4 i IPv6 TCP/IP zaprojektowany specjalnie z myślą o aplikacjach osadzonych, w czasie rzeczywistym i aplikacjach IoT.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="bd9b5-105">NetX Duo zapewnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, IPv6, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="bd9b5-106">Azure RTOS NetX Duo oferuje zabezpieczenia za pośrednictwem dodatkowych produktów zabezpieczających, takich jak Azure RTOS NetX Secure IPsec i Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="bd9b5-107">Wszystko to w połączeniu z niewielkim zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawiają, że Azure RTOS NetX Duo jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="bd9b5-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="bd9b5-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="bd9b5-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="bd9b5-109">MQTT</span></span>

* <span data-ttu-id="bd9b5-110">Transport telemetrii kolejki komunikatów (MQTT)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="bd9b5-111">Minimalna 2,7 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="bd9b5-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="bd9b5-112">Automatyczny adres IP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-112">Auto IP</span></span>

* <span data-ttu-id="bd9b5-113">Automatyczne przypisywanie adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="bd9b5-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="bd9b5-114">Minimalna 1,2 KB, 300 bajtów pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="bd9b5-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="bd9b5-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="bd9b5-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="bd9b5-116">HTTP 1.0</span></span>

* <span data-ttu-id="bd9b5-117">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="bd9b5-118">Minimalna 2,8 KB do 4,8 KB pamięci FLASH / od 0,4 KB do 1,0 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="bd9b5-119">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="bd9b5-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="bd9b5-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="bd9b5-121">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="bd9b5-122">Minimalna 3,0 KB do 9,5 KB pamięci FLASH / od 0,5 KB do 2 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="bd9b5-123">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-123">Client and server support</span></span>
* <span data-ttu-id="bd9b5-124">Wiele przychodzących sesji klientów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="bd9b5-125">Zwykły tekst i zaszyfrowany protokół HTTPS</span><span class="sxs-lookup"><span data-stu-id="bd9b5-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="bd9b5-126">Obsługa połączeń trwałych</span><span class="sxs-lookup"><span data-stu-id="bd9b5-126">Persistent connection support</span></span>
* <span data-ttu-id="bd9b5-127">Przekazywanie plików wieloczęściowych</span><span class="sxs-lookup"><span data-stu-id="bd9b5-127">Multipart file upload</span></span>
* <span data-ttu-id="bd9b5-128">W pełni zintegrowane z Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="bd9b5-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="bd9b5-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-129">SMTP</span></span>

* <span data-ttu-id="bd9b5-130">Simple Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="bd9b5-131">Minimalnie 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-132">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="bd9b5-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-133">DHCP</span></span>

* <span data-ttu-id="bd9b5-134">Protokół DHCP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="bd9b5-135">Minimalnie od 3,6 KB do 4,6 KB pamięci FLASH, 2,7 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-136">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-136">Client and server support</span></span>
* <span data-ttu-id="bd9b5-137">Obsługa protokołu IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="bd9b5-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="bd9b5-138">NAT</span><span class="sxs-lookup"><span data-stu-id="bd9b5-138">NAT</span></span>

* <span data-ttu-id="bd9b5-139">Translator adresów sieciowych (NAT)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="bd9b5-140">Minimalnie 3,5 K6 i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-141">Obsługa adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="bd9b5-141">IPv4 address support</span></span>
* <span data-ttu-id="bd9b5-142">NaT jest dostępny tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="bd9b5-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-143">SNMP</span></span>

* <span data-ttu-id="bd9b5-144">Protokół SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="bd9b5-145">Minimalnie 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-146">Obsługa agentów dla wersji VI, V2 i V3</span><span class="sxs-lookup"><span data-stu-id="bd9b5-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="bd9b5-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="bd9b5-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="bd9b5-148">System nazw domen (DNS)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="bd9b5-149">Multiemisja systemu nazw domen (mDNS)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="bd9b5-150">Odnajdywanie usług oparte na systemie DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="bd9b5-151">DNS Minimalnie od 2,4 KB do 3 KB pamięci FLASH, 1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-152">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-152">Client support</span></span>
* <span data-ttu-id="bd9b5-153">Serwery mDNS i DNS-SD są dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="bd9b5-154">POP3</span><span class="sxs-lookup"><span data-stu-id="bd9b5-154">POP3</span></span>

* <span data-ttu-id="bd9b5-155">Post Office Protocol w wersji 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="bd9b5-156">Minimalnie 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-157">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="bd9b5-158">Telnet</span><span class="sxs-lookup"><span data-stu-id="bd9b5-158">TELNET</span></span>

* <span data-ttu-id="bd9b5-159">Minimalnie 0,5 KB i 0,3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-160">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-160">Client and server support</span></span>
* <span data-ttu-id="bd9b5-161">Intuicyjne interfejsy API Telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="bd9b5-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-162">FTP, TFTP</span></span>

* <span data-ttu-id="bd9b5-163">protokół transferu plików (FTP)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="bd9b5-164">Protokół TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="bd9b5-165">MINIMALNA PAMIĘĆ FLASH FTP od 1,8 KB do 7,2 KB, od 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-166">TFTP minimalnie od 1,7 KB do 2,4 KB pamięci FLASH, od 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-167">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-167">Client and server support</span></span>
* <span data-ttu-id="bd9b5-168">Intuicyjne interfejsy API FTP i TFTP: *nx_ftp_ \** lub *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="bd9b5-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="bd9b5-169">PPP, PPPoE</span></span>

* <span data-ttu-id="bd9b5-170">Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="bd9b5-171">Point-to-Point Protocol przez Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="bd9b5-172">Minimalnie 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-173">Intuicyjne interfejsy API PROTOKOŁU PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="bd9b5-174">Tryb PPPoE jest dostępny tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="bd9b5-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-175">SNTP</span></span>

* <span data-ttu-id="bd9b5-176">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="bd9b5-177">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="bd9b5-178">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-178">Client support</span></span>
* <span data-ttu-id="bd9b5-179">Intuicyjne interfejsy API SNTP: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="bd9b5-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="bd9b5-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="bd9b5-181">Intuicyjny i spójny interfejs API</span><span class="sxs-lookup"><span data-stu-id="bd9b5-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="bd9b5-182">Konwencja nazewnictwa czasownik-rzeczownik</span><span class="sxs-lookup"><span data-stu-id="bd9b5-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="bd9b5-183">Szybka implementacja interfejsu API bez kopiowania</span><span class="sxs-lookup"><span data-stu-id="bd9b5-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="bd9b5-184">Wszystkie interfejsy API mają wiodące <i>nx_\*</i> do łatwego identyfikowania jako Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="bd9b5-185">Interfejsy API blokowania mają opcjonalny limit czasu wątku</span><span class="sxs-lookup"><span data-stu-id="bd9b5-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="bd9b5-186">Zobacz [Azure RTOS użytkownika netx duo,](about-this-guide.md) aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="bd9b5-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="bd9b5-187">Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda</span><span class="sxs-lookup"><span data-stu-id="bd9b5-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="bd9b5-188">Igmp</span><span class="sxs-lookup"><span data-stu-id="bd9b5-188">IGMP</span></span>

* <span data-ttu-id="bd9b5-189">Protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="bd9b5-190">Minimalna 2,5 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="bd9b5-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="bd9b5-191">Obsługa grup multiemisji protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="bd9b5-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="bd9b5-192">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="bd9b5-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bd9b5-193">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="bd9b5-194">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="bd9b5-195">Intuicyjne interfejsy API IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="bd9b5-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="bd9b5-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="bd9b5-197">Datagram Transport Layer Security (DTLS) 1.0 i 1.2</span><span class="sxs-lookup"><span data-stu-id="bd9b5-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="bd9b5-198">Minimalna 11 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="bd9b5-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="bd9b5-199">Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz</span><span class="sxs-lookup"><span data-stu-id="bd9b5-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="bd9b5-200">Uproszczona implementacja X.509</span><span class="sxs-lookup"><span data-stu-id="bd9b5-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="bd9b5-201">W pełni zintegrowane z Azure RTOS NetX Duo UDP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="bd9b5-202">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="bd9b5-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="bd9b5-203">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="bd9b5-204">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="bd9b5-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="bd9b5-205">Obsługa zaszyfrowanych kluczy (zależna od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="bd9b5-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="bd9b5-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="bd9b5-207">Transport Layer Security (TLS) 1.0, 1.1 i 1.2</span><span class="sxs-lookup"><span data-stu-id="bd9b5-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="bd9b5-208">Minimalna 8,8 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="bd9b5-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="bd9b5-209">Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz</span><span class="sxs-lookup"><span data-stu-id="bd9b5-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="bd9b5-210">Uproszczona implementacja X.509</span><span class="sxs-lookup"><span data-stu-id="bd9b5-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="bd9b5-211">W pełni zintegrowane z Azure RTOS TCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="bd9b5-212">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="bd9b5-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="bd9b5-213">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="bd9b5-214">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="bd9b5-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="bd9b5-215">Obsługa zaszyfrowanych kluczy (zależna od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="bd9b5-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-216">ICMP</span></span>

* <span data-ttu-id="bd9b5-217">Protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="bd9b5-218">Minimalna 2,5 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="bd9b5-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="bd9b5-219">Obsługa protokołu IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="bd9b5-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="bd9b5-220">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="bd9b5-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bd9b5-221">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="bd9b5-221">Ping request and ping response</span></span>
* <span data-ttu-id="bd9b5-222">Opcjonalne wstrzymanie wątku dla żądań ping</span><span class="sxs-lookup"><span data-stu-id="bd9b5-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="bd9b5-223">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="bd9b5-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bd9b5-224">Opcjonalne statystyki ICMP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="bd9b5-225">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bd9b5-226">Intuicyjne interfejsy API ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="bd9b5-227">UDP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-227">UDP</span></span>

* <span data-ttu-id="bd9b5-228">Protokół UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="bd9b5-229">Minimalna pamięć FLASH 2,5 KB, 124 bajty pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="bd9b5-230">Szybkie przetwarzanie pakietów TCP przy użyciu ruchu najbliższego wire speed:</span><span class="sxs-lookup"><span data-stu-id="bd9b5-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="bd9b5-231">RX 95 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 14% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="bd9b5-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="bd9b5-232">TX 94 Mb/s na 100 Mb/s Ethernet, @100MHz MIKROU, 10% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="bd9b5-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="bd9b5-233">Technologia Szybka ścieżka UDP™ technologii</span><span class="sxs-lookup"><span data-stu-id="bd9b5-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="bd9b5-234">Brak limitów liczby protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="bd9b5-235">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="bd9b5-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bd9b5-236">Opcjonalne zawieszenie podczas odbierania gniazda</span><span class="sxs-lookup"><span data-stu-id="bd9b5-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="bd9b5-237">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="bd9b5-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bd9b5-238">Opcjonalne statystyki UDP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-238">Optional UDP statistics</span></span>
* <span data-ttu-id="bd9b5-239">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bd9b5-240">Intuicyjne interfejsy API UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="bd9b5-241">TCP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-241">TCP</span></span>

* <span data-ttu-id="bd9b5-242">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="bd9b5-243">Minimalnie od 10,5 KB do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="bd9b5-244">Szybkie, prawie wlre speed przetwarzanie pakietów TCP:</span><span class="sxs-lookup"><span data-stu-id="bd9b5-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="bd9b5-245">Rx 93 Mb/s na Ethernet 100 Mb/s, @100MHz MIKROU, 20% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="bd9b5-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="bd9b5-246">TX 94 Mb/s przy 100 Mb/s Ethernet, @100MHz MIKROU, 27% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="bd9b5-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="bd9b5-247">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="bd9b5-247">Reliable connection</span></span>
* <span data-ttu-id="bd9b5-248">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="bd9b5-249">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="bd9b5-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bd9b5-250">Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda</span><span class="sxs-lookup"><span data-stu-id="bd9b5-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="bd9b5-251">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="bd9b5-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bd9b5-252">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-252">Optional TCP statistics</span></span>
* <span data-ttu-id="bd9b5-253">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bd9b5-254">Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="bd9b5-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-255">ARP/RARP</span></span>

* <span data-ttu-id="bd9b5-256">Protokół ARP (Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="bd9b5-257">Protokół RARP (Reverse Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="bd9b5-258">Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="bd9b5-259">Dynamiczna rozdzielczość 32-blt adresów MAC IPv4 i 48-blt</span><span class="sxs-lookup"><span data-stu-id="bd9b5-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="bd9b5-260">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="bd9b5-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bd9b5-261">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="bd9b5-262">Obsługa szosowego ARP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="bd9b5-263">Opcjonalne statystyki ARP/RARP określone przez aplikację</span><span class="sxs-lookup"><span data-stu-id="bd9b5-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="bd9b5-264">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bd9b5-265">Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="bd9b5-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="bd9b5-266">Protokół IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="bd9b5-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="bd9b5-267">Protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="bd9b5-268">Minimalnie od 3,5 KB do 8,5 KB pamięci FLASH, od 2 KB do 3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="bd9b5-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="bd9b5-269">Piconet™ architektura</span><span class="sxs-lookup"><span data-stu-id="bd9b5-269">Piconet™ architecture</span></span>
* <span data-ttu-id="bd9b5-270">Szybka wydajność prawie podejściowa</span><span class="sxs-lookup"><span data-stu-id="bd9b5-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="bd9b5-271">Obsługa wielu interfejsów</span><span class="sxs-lookup"><span data-stu-id="bd9b5-271">Multiple interface support</span></span>
* <span data-ttu-id="bd9b5-272">Obsługa wieloadresowa</span><span class="sxs-lookup"><span data-stu-id="bd9b5-272">Multihomed support</span></span>
* <span data-ttu-id="bd9b5-273">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="bd9b5-273">Static routing support</span></span>
* <span data-ttu-id="bd9b5-274">Obsługa fragmentacji/ponownegoassembly adresu IP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="bd9b5-275">Obsługa adresów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="bd9b5-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="bd9b5-276">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="bd9b5-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bd9b5-277">Certyfikacja gotowego logo IPv6 fazy II</span><span class="sxs-lookup"><span data-stu-id="bd9b5-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="bd9b5-278">Opcjonalne statystyki adresów IP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-278">Optional IP statistics</span></span>
* <span data-ttu-id="bd9b5-279">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej</span><span class="sxs-lookup"><span data-stu-id="bd9b5-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="bd9b5-280">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bd9b5-281">Intuicyjne interfejsy API warstwy IP: *nx_ip_, \** *\** *\** nxd_ip_, nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="bd9b5-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="bd9b5-282">Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304, klasa C, ISO 26262 ASIL D i EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="bd9b5-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="bd9b5-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="bd9b5-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="bd9b5-284">Zabezpieczenia protokołu internetowego (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="bd9b5-285">Warstwa IP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-285">IP layer</span></span>
* <span data-ttu-id="bd9b5-286">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="bd9b5-286">Hardware crypto support</span></span>
* <span data-ttu-id="bd9b5-287">Obsługa kryptografii oprogramowania, w tym:</span><span class="sxs-lookup"><span data-stu-id="bd9b5-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="bd9b5-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="bd9b5-288">DES, 3DES</span></span>
    * <span data-ttu-id="bd9b5-289">AES</span><span class="sxs-lookup"><span data-stu-id="bd9b5-289">AES</span></span>
    * <span data-ttu-id="bd9b5-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="bd9b5-290">HMAC-MD5</span></span>
    * <span data-ttu-id="bd9b5-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="bd9b5-291">HMAC-SHA1</span></span>
* <span data-ttu-id="bd9b5-292">Obsługa usługi Internet Key Exchange (IKE) w wersji 2</span><span class="sxs-lookup"><span data-stu-id="bd9b5-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="bd9b5-293">Intuicyjne interfejsy API protokołu IPsec: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="bd9b5-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="bd9b5-294">IPsec jest dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd9b5-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="bd9b5-295">Sejf i zabezpieczanie</span><span class="sxs-lookup"><span data-stu-id="bd9b5-295">Safe and secure</span></span>

<span data-ttu-id="bd9b5-296">Azure RTOS NetX Duo jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="bd9b5-297">Zabezpieczenia te są udostępniane za pośrednictwem produktów zabezpieczeń dodatków, w tym protokołu IPsec, protokołu SSL, protokołu TLS i protokołu DTLS.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="bd9b5-298">Ponadto aplikacja ma pełną kontrolę nad całym dostępem zewnętrznym do usługi Azure RTOS NetX Duo, co znacznie ułatwia określanie ryzyka bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="bd9b5-299">Microsoft Azure System RTOS udostępnia producentom OEM składniki służące do zabezpieczania komunikacji oraz tworzenia izolacji kodu i danych przy użyciu podstawowych mechanizmów ochrony sprzętowej MIKROU/MPU.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="bd9b5-300">Konstruktor urządzenia ostatecznie odpowiada za zapewnienie, że urządzenie w pełni spełnia zmieniające się wymagania dotyczące zabezpieczeń związane z konkretnym przypadekem użycia.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="bd9b5-301">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="bd9b5-301">Interoperability verification</span></span>

<span data-ttu-id="bd9b5-302">NetX Duo jest zgodny ze standardami RFC i oferuje pełne współdziałanie z urządzeniami dla większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Gotowe logo IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="bd9b5-304">Azure RTOS NetX Duo jest jednym z jedynych osadzonych stosów TCP/IP w celu osiągnięcia rygorystycznego certyfikatu logo IPv6-Ready Logo, co oznacza, że przeszedł testy zgodności i współdziałania, administrowane i weryfikowane przez forum IPv6.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="bd9b5-305">NetX Duo korzysta również ze standardu branżowego IxANVL (Automated Network Validation Library) do implementacji podstawowego protokołu TCP/IP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="bd9b5-306">Kompleksowe rozwiązanie IoT</span><span class="sxs-lookup"><span data-stu-id="bd9b5-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="bd9b5-307">NetX Duo ma jedną z najbardziej kompleksowych sieci TCP/IP dla głęboko osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="bd9b5-308">Ta obsługa obejmuje następujące produkty protokołu dodatku.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="bd9b5-309">MQTT, CoAP, SMTPM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="bd9b5-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="bd9b5-310">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="bd9b5-310">Advanced technology</span></span>

<span data-ttu-id="bd9b5-311">Azure RTOS NetX Duo to zaawansowana technologia, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="bd9b5-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="bd9b5-312">Piconet™ architektura</span><span class="sxs-lookup"><span data-stu-id="bd9b5-312">Piconet™ architecture</span></span>
* <span data-ttu-id="bd9b5-313">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="bd9b5-313">Automatic scaling</span></span>
* <span data-ttu-id="bd9b5-314">Technologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="bd9b5-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="bd9b5-315">Elastyczne zarządzanie pakietami</span><span class="sxs-lookup"><span data-stu-id="bd9b5-315">Flexible packet management</span></span>
* <span data-ttu-id="bd9b5-316">Interfejs API bez kopiowania i implementacja</span><span class="sxs-lookup"><span data-stu-id="bd9b5-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="bd9b5-317">Obsługa wielunadresowych</span><span class="sxs-lookup"><span data-stu-id="bd9b5-317">Multihomed support</span></span>
* <span data-ttu-id="bd9b5-318">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="bd9b5-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bd9b5-319">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="bd9b5-319">Static routing support</span></span>
* <span data-ttu-id="bd9b5-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="bd9b5-320">IPsec</span></span>
* <span data-ttu-id="bd9b5-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="bd9b5-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="bd9b5-322">Azure RTOS analizy systemu TraceX</span><span class="sxs-lookup"><span data-stu-id="bd9b5-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="bd9b5-323">Powiązane usługi</span><span class="sxs-lookup"><span data-stu-id="bd9b5-323">Related services</span></span>

### <a name="azure-iot"></a><span data-ttu-id="bd9b5-324">Azure IoT</span><span class="sxs-lookup"><span data-stu-id="bd9b5-324">Azure IoT</span></span>

<span data-ttu-id="bd9b5-325">NetX Duo zawiera oprogramowanie pośredniczące [Azure IoT](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md)dla usługi Azure RTOS , bibliotekę specyficzną dla platformy, która działa jako warstwa powiązania między usługą Azure RTOS i zestawem Azure SDK dla osadzonego języka C w celu ułatwienia łączności z usługami Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-325">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="bd9b5-326">Poniżej przedstawiono cele oprogramowania pośredniczącego usługi Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-326">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="bd9b5-327">Udostępnij inteligentne interfejsy klienckie (IoTHub_Client, DeviceProvisioning_Client), których deweloperzy potrzebują dla swoich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-327">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="bd9b5-328">Organizowanie interakcji między osadzonym zestawem SDK języka C a platformą.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-328">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="bd9b5-329">Podaj Azure RTOS inicjowania platformy.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-329">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="bd9b5-330">IoT Plug and Play pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-330">IoT Plug and Play support.</span></span>
* <span data-ttu-id="bd9b5-331">Możliwości zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-331">Security capabilities.</span></span>
* <span data-ttu-id="bd9b5-332">Należy pamiętać o ograniczeniach zasobów.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-332">Resource limitation aware.</span></span>
* <span data-ttu-id="bd9b5-333">Obsługa protokołów.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-333">Protocol support.</span></span>

![Azure RTOS związane z netx duo](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="bd9b5-335">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="bd9b5-335">Azure Defender</span></span>

<span data-ttu-id="bd9b5-336">Moduł Azure Defender dla IoT zabezpieczeń zapewnia kompleksowe rozwiązanie zabezpieczeń dla Azure RTOS urządzeń.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-336">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="bd9b5-337">Moduł zabezpieczeń usługi Azure RTOS oferuje wykrywanie złośliwych działań sieciowych, niestandardowe oparte na alertach podstawy zachowania urządzenia i pomaga poprawić higienę zabezpieczeń urządzenia.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-337">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="bd9b5-338">Dowiedz się więcej o module [zabezpieczeń dla Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) lub rozpoczynanie pracy z konfigurowaniem modułu zabezpieczeń dla usługi [Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) Szybki start.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-338">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="bd9b5-339">Aktualizacja urządzenia dla IoT Hub</span><span class="sxs-lookup"><span data-stu-id="bd9b5-339">Device Update for IoT Hub</span></span>

<span data-ttu-id="bd9b5-340">Azure [Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) to usługa, która umożliwia wdrażanie aktualizacji w powietrzu (OTA) dla urządzeń IoT.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-340">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="bd9b5-341">Moduł Device Update for IoT Hub to implementacja aktualizacji urządzenia dla agenta IoT Hub w programie Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-341">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="bd9b5-342">Udostępnia on proste interfejsy API dla konstruktorów urządzeń, które integrują możliwość aktualizacji urządzeń w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-342">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="bd9b5-343">Zapoznaj się z przykładami tablic ewaluacyjnych kluczy, które zawierają przewodniki z wprowadzeniem, aby dowiedzieć się, jak konfigurować, kompilować i wdrażać aktualizacje w powietrzu (OTA) na urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-343">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="bd9b5-344">Możesz też dowiedzieć się więcej na temat używania [aktualizacji urządzenia na IoT Hub z Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="bd9b5-344">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bd9b5-345">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bd9b5-345">Next steps</span></span>

<span data-ttu-id="bd9b5-346">Aby dowiedzieć się więcej o netx duo, zacznij od Azure RTOS NetX Duo User Guide (Podręcznik użytkownika aplikacji [NetX Duo).](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="bd9b5-346">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
