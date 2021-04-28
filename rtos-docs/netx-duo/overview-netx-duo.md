---
title: Understand Azure RTOS NetX Duo
description: Azure RTOS NetX Duo to zaawansowany stos sieciowy klasy przemysłowej TCP/IP zaprojektowany specjalnie z myślą o głęboko osadzonych aplikacjach czasu rzeczywistego i IoT.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e3fe3bcc602f409cc76f3be47aca865bf8116697
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171339"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="28408-103">Omówienie Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="28408-104">Azure RTOS NetX Duo osadzony stos sieciowy TCP/IP to zaawansowany stos sieciowy TCP/IP klasy przemysłowej firmy Microsoft, podwójny stos sieciowy IPv4 i IPv6 TCP/IP zaprojektowany specjalnie z myślą o aplikacjach osadzonych, w czasie rzeczywistym i aplikacjach IoT.</span><span class="sxs-lookup"><span data-stu-id="28408-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="28408-105">NetX Duo zapewnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, IPv6, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="28408-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="28408-106">Azure RTOS NetX Duo oferuje zabezpieczenia za pośrednictwem dodatkowych produktów zabezpieczających, takich jak Azure RTOS NetX Secure IPsec i Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="28408-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="28408-107">Wszystko to w połączeniu z niewielkim zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawiają, że Azure RTOS NetX Duo jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="28408-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="28408-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="28408-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="28408-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="28408-109">MQTT</span></span>

* <span data-ttu-id="28408-110">Transport telemetrii kolejki komunikatów (MQTT)</span><span class="sxs-lookup"><span data-stu-id="28408-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="28408-111">Minimalna 2,7 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="28408-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="28408-112">Automatyczny adres IP</span><span class="sxs-lookup"><span data-stu-id="28408-112">Auto IP</span></span>

* <span data-ttu-id="28408-113">Automatyczne przypisywanie adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="28408-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="28408-114">Minimalna 1,2 KB, 300 bajtów pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="28408-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="28408-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="28408-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="28408-116">HTTP 1.0</span></span>

* <span data-ttu-id="28408-117">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="28408-118">Minimalna 2,8 KB do 4,8 KB pamięci FLASH / od 0,4 KB do 1,0 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="28408-119">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="28408-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="28408-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="28408-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="28408-121">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="28408-122">Minimalna ilość pamięci FLASH od 3,0 KB do 9,5 KB / od 0,5 KB do 2 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="28408-123">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="28408-123">Client and server support</span></span>
* <span data-ttu-id="28408-124">Wiele przychodzących sesji klientów</span><span class="sxs-lookup"><span data-stu-id="28408-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="28408-125">Zwykły tekst i zaszyfrowany protokół HTTPS</span><span class="sxs-lookup"><span data-stu-id="28408-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="28408-126">Obsługa połączeń trwałych</span><span class="sxs-lookup"><span data-stu-id="28408-126">Persistent connection support</span></span>
* <span data-ttu-id="28408-127">Przekazywanie plików wieloczęściowych</span><span class="sxs-lookup"><span data-stu-id="28408-127">Multipart file upload</span></span>
* <span data-ttu-id="28408-128">W pełni zintegrowane z Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="28408-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="28408-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="28408-129">SMTP</span></span>

* <span data-ttu-id="28408-130">Simple Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="28408-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="28408-131">Minimalnie 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="28408-132">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="28408-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="28408-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="28408-133">DHCP</span></span>

* <span data-ttu-id="28408-134">Protokół DHCP</span><span class="sxs-lookup"><span data-stu-id="28408-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="28408-135">Minimalna ilość pamięci FLASH od 3,6 KB do 4,6 KB, 2,7 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="28408-136">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="28408-136">Client and server support</span></span>
* <span data-ttu-id="28408-137">Obsługa protokołu IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="28408-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="28408-138">NAT</span><span class="sxs-lookup"><span data-stu-id="28408-138">NAT</span></span>

* <span data-ttu-id="28408-139">Translator adresów sieciowych (NAT)</span><span class="sxs-lookup"><span data-stu-id="28408-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="28408-140">Minimalnie 3,5 K6 i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="28408-141">Obsługa adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="28408-141">IPv4 address support</span></span>
* <span data-ttu-id="28408-142">NaT jest dostępny tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="28408-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="28408-143">SNMP</span></span>

* <span data-ttu-id="28408-144">Protokół SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="28408-145">Minimalna 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="28408-146">Obsługa agentów dla wersji VI, V2 i V3</span><span class="sxs-lookup"><span data-stu-id="28408-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="28408-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="28408-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="28408-148">System nazw domen (DNS)</span><span class="sxs-lookup"><span data-stu-id="28408-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="28408-149">Multiemisja systemu nazw domen (mDNS)</span><span class="sxs-lookup"><span data-stu-id="28408-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="28408-150">Odnajdywanie usług oparte na systemie DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="28408-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="28408-151">DNS Minimalnie od 2,4 KB do 3 KB pamięci FLASH, 1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="28408-152">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="28408-152">Client support</span></span>
* <span data-ttu-id="28408-153">Serwery mDNS i DNS-SD są dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="28408-154">P0P3</span><span class="sxs-lookup"><span data-stu-id="28408-154">P0P3</span></span>

* <span data-ttu-id="28408-155">Protokół POST Office w wersji 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="28408-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="28408-156">Minimalnie 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="28408-157">Obsługa klientów</span><span class="sxs-lookup"><span data-stu-id="28408-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="28408-158">Telnet</span><span class="sxs-lookup"><span data-stu-id="28408-158">TELNET</span></span>

* <span data-ttu-id="28408-159">Minimalnie 0,5 KB i 0,3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="28408-160">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="28408-160">Client and server support</span></span>
* <span data-ttu-id="28408-161">Intuicyjne interfejsy API Telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="28408-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="28408-162">FTP, TFTP</span></span>

* <span data-ttu-id="28408-163">protokół transferu plików (FTP)</span><span class="sxs-lookup"><span data-stu-id="28408-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="28408-164">Protokół TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="28408-165">MINIMALNA PAMIĘĆ FLASH FTP od 1,8 KB do 7,2 KB, od 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="28408-166">TFTP minimalnie od 1,7 KB do 2,4 KB pamięci FLASH, od 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="28408-167">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="28408-167">Client and server support</span></span>
* <span data-ttu-id="28408-168">Intuicyjne interfejsy API FTP i TFTP: *nx_ftp_ \** lub *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="28408-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="28408-169">PPP, PPPoE</span></span>

* <span data-ttu-id="28408-170">Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="28408-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="28408-171">Point-to-Point Protocol przez Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="28408-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="28408-172">Minimalnie 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="28408-173">Intuicyjne interfejsy API PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="28408-174">PpPoE jest dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="28408-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="28408-175">SNTP</span></span>

* <span data-ttu-id="28408-176">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="28408-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="28408-177">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="28408-178">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="28408-178">Client support</span></span>
* <span data-ttu-id="28408-179">Intuicyjne interfejsy API SNTP: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="28408-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="28408-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="28408-181">Intuicyjny i spójny interfejs API</span><span class="sxs-lookup"><span data-stu-id="28408-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="28408-182">Konwencja nazewnictwa rzeczowników</span><span class="sxs-lookup"><span data-stu-id="28408-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="28408-183">Szybka implementacja interfejsu API bez kopiowania</span><span class="sxs-lookup"><span data-stu-id="28408-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="28408-184">Wszystkie interfejsy API mają wiodące <i>nx_\*</i> do łatwego identyfikowania jako Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="28408-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="28408-185">Interfejsy API blokowania mają opcjonalny limit czasu wątku</span><span class="sxs-lookup"><span data-stu-id="28408-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="28408-186">Aby [uzyskać więcej Azure RTOS, zobacz podręcznik użytkownika](about-this-guide.md) aplikacji NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="28408-187">Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda</span><span class="sxs-lookup"><span data-stu-id="28408-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="28408-188">Igmp</span><span class="sxs-lookup"><span data-stu-id="28408-188">IGMP</span></span>

* <span data-ttu-id="28408-189">Protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="28408-190">Minimalna pamięć FLASH 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="28408-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="28408-191">Obsługa grup multiemisji IPv4</span><span class="sxs-lookup"><span data-stu-id="28408-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="28408-192">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="28408-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="28408-193">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="28408-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="28408-194">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="28408-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="28408-195">Intuicyjne interfejsy API IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="28408-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="28408-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="28408-197">Datagram Transport Layer Security (DTLS) 1.0 i 1.2</span><span class="sxs-lookup"><span data-stu-id="28408-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="28408-198">Minimalna 11 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="28408-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="28408-199">Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz</span><span class="sxs-lookup"><span data-stu-id="28408-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="28408-200">Uproszczona implementacja X.509</span><span class="sxs-lookup"><span data-stu-id="28408-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="28408-201">W pełni zintegrowane z Azure RTOS NetX Duo UDP</span><span class="sxs-lookup"><span data-stu-id="28408-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="28408-202">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="28408-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="28408-203">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="28408-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="28408-204">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="28408-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="28408-205">Obsługa zaszyfrowanych kluczy (zależna od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="28408-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="28408-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="28408-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="28408-207">Transport Layer Security (TLS) 1.0, 1.1 i 1.2</span><span class="sxs-lookup"><span data-stu-id="28408-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="28408-208">Minimalna 8,8 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="28408-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="28408-209">Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz</span><span class="sxs-lookup"><span data-stu-id="28408-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="28408-210">Uproszczona implementacja X.509</span><span class="sxs-lookup"><span data-stu-id="28408-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="28408-211">W pełni zintegrowane z Azure RTOS TCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="28408-212">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="28408-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="28408-213">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="28408-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="28408-214">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="28408-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="28408-215">Obsługa zaszyfrowanych kluczy (zależna od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="28408-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="28408-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="28408-216">ICMP</span></span>

* <span data-ttu-id="28408-217">Protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="28408-218">Minimalna pamięć FLASH 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="28408-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="28408-219">Obsługa protokołu IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="28408-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="28408-220">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="28408-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="28408-221">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="28408-221">Ping request and ping response</span></span>
* <span data-ttu-id="28408-222">Opcjonalne zawieszenie wątku na żądaniach ping</span><span class="sxs-lookup"><span data-stu-id="28408-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="28408-223">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="28408-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="28408-224">Opcjonalne statystyki ICMP</span><span class="sxs-lookup"><span data-stu-id="28408-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="28408-225">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="28408-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="28408-226">Intuicyjne interfejsy API ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="28408-227">UDP</span><span class="sxs-lookup"><span data-stu-id="28408-227">UDP</span></span>

* <span data-ttu-id="28408-228">Protokół UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="28408-229">Minimalna pamięć FLASH 2,5 KB, 124 gniazda w bajtach pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="28408-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="28408-230">Szybkie przetwarzanie pakietów TCP w pobliżu wire speed:</span><span class="sxs-lookup"><span data-stu-id="28408-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="28408-231">RX 95 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 14% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="28408-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="28408-232">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 10% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="28408-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="28408-233">Szybka ścieżka UDP™ technologia</span><span class="sxs-lookup"><span data-stu-id="28408-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="28408-234">Brak limitów liczby protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="28408-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="28408-235">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="28408-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="28408-236">Opcjonalne zawieszenie podczas odbierania gniazda</span><span class="sxs-lookup"><span data-stu-id="28408-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="28408-237">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="28408-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="28408-238">Opcjonalne statystyki UDP</span><span class="sxs-lookup"><span data-stu-id="28408-238">Optional UDP statistics</span></span>
* <span data-ttu-id="28408-239">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="28408-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="28408-240">Intuicyjne interfejsy API UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="28408-241">TCP</span><span class="sxs-lookup"><span data-stu-id="28408-241">TCP</span></span>

* <span data-ttu-id="28408-242">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="28408-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="28408-243">Minimalnie od 10,5 KB do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="28408-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="28408-244">Szybkie, prawie wlre speed przetwarzanie pakietów TCP:</span><span class="sxs-lookup"><span data-stu-id="28408-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="28408-245">Rx 93 Mb/s na Ethernet 100 Mb/s, @100MHz MIKROU, 20% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="28408-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="28408-246">TX 94 Mb/s przy 100 Mb/s Ethernet, @100MHz MIKROU, 27% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="28408-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="28408-247">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="28408-247">Reliable connection</span></span>
* <span data-ttu-id="28408-248">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="28408-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="28408-249">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="28408-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="28408-250">Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda</span><span class="sxs-lookup"><span data-stu-id="28408-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="28408-251">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="28408-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="28408-252">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="28408-252">Optional TCP statistics</span></span>
* <span data-ttu-id="28408-253">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="28408-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="28408-254">Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="28408-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="28408-255">ARP/RARP</span></span>

* <span data-ttu-id="28408-256">Protokół rozpoznawania adresów (ARP)</span><span class="sxs-lookup"><span data-stu-id="28408-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="28408-257">Protokół RARP (Reverse Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="28408-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="28408-258">Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="28408-259">Dynamiczna rozdzielczość 32-blt adresów IPv4 i 48 blt adresów MAC</span><span class="sxs-lookup"><span data-stu-id="28408-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="28408-260">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="28408-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="28408-261">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP</span><span class="sxs-lookup"><span data-stu-id="28408-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="28408-262">Obsługa dużych ARP</span><span class="sxs-lookup"><span data-stu-id="28408-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="28408-263">Opcjonalne statystyki ARP/RARP określone przez aplikację</span><span class="sxs-lookup"><span data-stu-id="28408-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="28408-264">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="28408-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="28408-265">Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="28408-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="28408-266">Protokół &amp; IPv6 protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="28408-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="28408-267">Protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="28408-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="28408-268">Minimalna ilość pamięci FLASH od 3,5 KB do 8,5 KB, od 2 KB do 3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="28408-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="28408-269">Piconet™ architektura</span><span class="sxs-lookup"><span data-stu-id="28408-269">Piconet™ architecture</span></span>
* <span data-ttu-id="28408-270">Szybka wydajność prawie z wire speed</span><span class="sxs-lookup"><span data-stu-id="28408-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="28408-271">Obsługa wielu interfejsów</span><span class="sxs-lookup"><span data-stu-id="28408-271">Multiple interface support</span></span>
* <span data-ttu-id="28408-272">Obsługa wielunadresowych</span><span class="sxs-lookup"><span data-stu-id="28408-272">Multihomed support</span></span>
* <span data-ttu-id="28408-273">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="28408-273">Static routing support</span></span>
* <span data-ttu-id="28408-274">Obsługa fragmentacji/ponownego zsadu ADRESÓW IP</span><span class="sxs-lookup"><span data-stu-id="28408-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="28408-275">Obsługa adresów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="28408-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="28408-276">Zweryfikowane przez IxANVL IxANVL</span><span class="sxs-lookup"><span data-stu-id="28408-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="28408-277">Certyfikacja gotowego logo IPv6 fazy II</span><span class="sxs-lookup"><span data-stu-id="28408-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="28408-278">Opcjonalne statystyki adresów IP</span><span class="sxs-lookup"><span data-stu-id="28408-278">Optional IP statistics</span></span>
* <span data-ttu-id="28408-279">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej</span><span class="sxs-lookup"><span data-stu-id="28408-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="28408-280">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="28408-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="28408-281">Intuicyjne interfejsy API warstwy IP: *nx_ip_, \** *\** *\** nxd_ip_, nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="28408-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="28408-282">Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304, klasa C, ISO 26262 ASIL D i EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="28408-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="28408-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="28408-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="28408-284">Zabezpieczenia protokołu internetowego (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="28408-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="28408-285">Warstwa IP</span><span class="sxs-lookup"><span data-stu-id="28408-285">IP layer</span></span>
* <span data-ttu-id="28408-286">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="28408-286">Hardware crypto support</span></span>
* <span data-ttu-id="28408-287">Obsługa kryptografii oprogramowania, w tym:</span><span class="sxs-lookup"><span data-stu-id="28408-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="28408-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="28408-288">DES, 3DES</span></span>
    * <span data-ttu-id="28408-289">AES</span><span class="sxs-lookup"><span data-stu-id="28408-289">AES</span></span>
    * <span data-ttu-id="28408-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="28408-290">HMAC-MD5</span></span>
    * <span data-ttu-id="28408-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="28408-291">HMAC-SHA1</span></span>
* <span data-ttu-id="28408-292">Internet Key Exchange (IKE) w wersji 2</span><span class="sxs-lookup"><span data-stu-id="28408-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="28408-293">Intuicyjne interfejsy API protokołu IPsec: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="28408-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="28408-294">IPsec jest dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28408-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="28408-295">Bezpieczne i bezpieczne</span><span class="sxs-lookup"><span data-stu-id="28408-295">Safe and secure</span></span>

<span data-ttu-id="28408-296">Azure RTOS NetX Duo jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="28408-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="28408-297">Zabezpieczenia te są udostępniane za pośrednictwem produktów zabezpieczeń dodatków, w tym protokołu IPsec, protokołu SSL, protokołu TLS i protokołu DTLS.</span><span class="sxs-lookup"><span data-stu-id="28408-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="28408-298">Ponadto aplikacja ma pełną kontrolę nad całym dostępem zewnętrznym do aplikacji Azure RTOS NetX Duo, co znacznie ułatwia określanie ryzyka bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="28408-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="28408-299">Microsoft Azure RTOS zapewnia producentom OEM składniki do zabezpieczania komunikacji oraz tworzenia izolacji kodu i danych przy użyciu podstawowych mechanizmów ochrony sprzętowej MCU/MPU.</span><span class="sxs-lookup"><span data-stu-id="28408-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="28408-300">Konstruktor urządzenia ostatecznie odpowiada za zapewnienie, że urządzenie w pełni spełnia zmieniające się wymagania dotyczące zabezpieczeń związane z konkretnym przypadekem użycia.</span><span class="sxs-lookup"><span data-stu-id="28408-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="28408-301">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="28408-301">Interoperability verification</span></span>

<span data-ttu-id="28408-302">NetX Duo jest zgodny ze standardami RFC i oferuje pełne współdziałanie z urządzeniami dla większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="28408-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logo gotowe do użycia IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="28408-304">Azure RTOS NetX Duo jest jednym z jedynych osadzonych stosów TCP/IP do osiągnięcia rygorystycznego certyfikatu IPv6-Ready Logo, dowodu na to, że przeszedł testy zgodności i współdziałania, administrowane i weryfikowane przez forum IPv6.</span><span class="sxs-lookup"><span data-stu-id="28408-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="28408-305">NetX Duo korzysta również ze standardu branżowego IxANVL (Automated Network Validation Library) do implementacji podstawowego protokołu TCP/IP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="28408-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="28408-306">Kompleksowe rozwiązanie IoT</span><span class="sxs-lookup"><span data-stu-id="28408-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="28408-307">NetX Duo ma jedną z najbardziej kompleksowych sieci TCP/IP dla głęboko osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="28408-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="28408-308">Ta obsługa obejmuje następujące produkty protokołu dodatku.</span><span class="sxs-lookup"><span data-stu-id="28408-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="28408-309">MQTT, CoAP, SMTPM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="28408-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="28408-310">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="28408-310">Advanced technology</span></span>

<span data-ttu-id="28408-311">Azure RTOS NetX Duo to zaawansowana technologia, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="28408-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="28408-312">Piconet™ architektura</span><span class="sxs-lookup"><span data-stu-id="28408-312">Piconet™ architecture</span></span>
* <span data-ttu-id="28408-313">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="28408-313">Automatic scaling</span></span>
* <span data-ttu-id="28408-314">Technologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="28408-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="28408-315">Elastyczne zarządzanie pakietami</span><span class="sxs-lookup"><span data-stu-id="28408-315">Flexible packet management</span></span>
* <span data-ttu-id="28408-316">Interfejs API bez kopiowania i implementacja</span><span class="sxs-lookup"><span data-stu-id="28408-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="28408-317">Obsługa wielunadresowych</span><span class="sxs-lookup"><span data-stu-id="28408-317">Multihomed support</span></span>
* <span data-ttu-id="28408-318">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="28408-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="28408-319">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="28408-319">Static routing support</span></span>
* <span data-ttu-id="28408-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="28408-320">IPsec</span></span>
* <span data-ttu-id="28408-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="28408-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="28408-322">Azure RTOS analizy systemu TraceX</span><span class="sxs-lookup"><span data-stu-id="28408-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="28408-323">Powiązane usługi</span><span class="sxs-lookup"><span data-stu-id="28408-323">Related services</span></span>

<span data-ttu-id="28408-324">Moduł Azure Security Center zabezpieczeń IoT RTOS zapewnia kompleksowe rozwiązanie zabezpieczeń dla Azure RTOS mobilnych.</span><span class="sxs-lookup"><span data-stu-id="28408-324">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="28408-325">Moduł zabezpieczeń dla usługi Azure RTOS oferuje wykrywanie złośliwych działań sieciowych, dostosowywanie niestandardowego zachowania urządzenia opartego na alertach i pomaga zwiększyć higienę zabezpieczeń urządzeń.</span><span class="sxs-lookup"><span data-stu-id="28408-325">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="28408-326">Dowiedz się więcej na temat [modułu zabezpieczeń](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) dla Azure RTOS lub rozpoczynanie pracy z konfigurowaniem modułu zabezpieczeń na Azure RTOS [Szybki](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) start.</span><span class="sxs-lookup"><span data-stu-id="28408-326">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="28408-327">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="28408-327">Next steps</span></span>

<span data-ttu-id="28408-328">Aby dowiedzieć się więcej na temat netx duo, zacznij od [podręcznika użytkownika Azure RTOS NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="28408-328">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
