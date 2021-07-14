---
title: Understand Azure RTOS NetX Duo
description: Azure RTOS NetX Duo to zaawansowany stos sieciowy tcp/IP klasy przemysłowej zaprojektowany specjalnie dla głęboko osadzonych aplikacji w czasie rzeczywistym i aplikacji IoT.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: b40a57bf385ddcf623ff7cbe0d2e798c547227d7
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754900"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="b5e4c-103">Omówienie Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="b5e4c-104">Azure RTOS NetX Duo osadzony stos sieciOWY TCP/IP firmy Microsoft to zaawansowany, przemysłowych podwójny stos sieciowy IPv4 i IPv6 TCP/IP zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych, w czasie rzeczywistym i IoT.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="b5e4c-105">NetX Duo udostępnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, IPv6, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="b5e4c-106">Azure RTOS NetX Duo oferuje zabezpieczenia za pośrednictwem dodatkowych produktów zabezpieczających, takich jak Azure RTOS NetX Secure IPsec i Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="b5e4c-107">Wszystko to w połączeniu z niewielkim zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawiają, że Azure RTOS NetX Duo jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="b5e4c-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="b5e4c-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="b5e4c-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-109">MQTT</span></span>

* <span data-ttu-id="b5e4c-110">Transport telemetrii kolejki komunikatów (MQTT)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="b5e4c-111">Minimalna pamięć FLASH 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="b5e4c-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="b5e4c-112">Automatyczny adres IP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-112">Auto IP</span></span>

* <span data-ttu-id="b5e4c-113">Automatyczne przypisywanie adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="b5e4c-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="b5e4c-114">Minimalna 1,2 KB, 300 bajtów pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="b5e4c-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-115">HTTP, HTTPS</span></span>
<span data-ttu-id="b5e4c-116">NetX Duo obsługuje następujące protokoły HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-116">NetX Duo supports the following HTTP/HTTPS protocols.</span></span>

#### <a name="http-10"></a><span data-ttu-id="b5e4c-117">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="b5e4c-117">HTTP 1.0</span></span>

* <span data-ttu-id="b5e4c-118">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-118">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="b5e4c-119">Minimalna ilość pamięci FLASH od 2,8 KB do 4,8 KB / od 0,4 KB do 1,0 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-119">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="b5e4c-120">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-120">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="b5e4c-121">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="b5e4c-121">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="b5e4c-122">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-122">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="b5e4c-123">Minimalna ilość pamięci FLASH od 3,0 KB do 9,5 KB / od 0,5 KB do 2 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-123">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="b5e4c-124">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-124">Client and server support</span></span>
* <span data-ttu-id="b5e4c-125">Wiele przychodzących sesji klientów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-125">Multiple incoming client sessions</span></span>
* <span data-ttu-id="b5e4c-126">Zwykły tekst i zaszyfrowany protokół HTTPS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-126">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="b5e4c-127">Obsługa połączeń trwałych</span><span class="sxs-lookup"><span data-stu-id="b5e4c-127">Persistent connection support</span></span>
* <span data-ttu-id="b5e4c-128">Przekazywanie plików wieloczęściowych</span><span class="sxs-lookup"><span data-stu-id="b5e4c-128">Multipart file upload</span></span>
* <span data-ttu-id="b5e4c-129">W pełni zintegrowane z Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-129">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="b5e4c-130">SMTP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-130">SMTP</span></span>

* <span data-ttu-id="b5e4c-131">Simple Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-131">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="b5e4c-132">Minimalnie 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-132">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-133">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="b5e4c-133">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="b5e4c-134">DHCP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-134">DHCP</span></span>

* <span data-ttu-id="b5e4c-135">Protokół DHCP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-135">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="b5e4c-136">Minimalna ilość pamięci FLASH od 3,6 KB do 4,6 KB, 2,7 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-136">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-137">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-137">Client and server support</span></span>
* <span data-ttu-id="b5e4c-138">Obsługa protokołu IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="b5e4c-138">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="b5e4c-139">NAT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-139">NAT</span></span>

* <span data-ttu-id="b5e4c-140">Translator adresów sieciowych (NAT)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-140">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="b5e4c-141">Minimalnie 3,5 K6 i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-141">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-142">Obsługa adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="b5e4c-142">IPv4 address support</span></span>
* <span data-ttu-id="b5e4c-143">NaT jest dostępny tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-143">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="b5e4c-144">SNMP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-144">SNMP</span></span>

* <span data-ttu-id="b5e4c-145">Protokół SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-145">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="b5e4c-146">Minimalna 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-146">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-147">Obsługa agentów dla wersji VI, V2 i V3</span><span class="sxs-lookup"><span data-stu-id="b5e4c-147">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="b5e4c-148">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="b5e4c-148">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="b5e4c-149">System nazw domen (DNS)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-149">Domain Name System (DNS)</span></span>
* <span data-ttu-id="b5e4c-150">Multiemisja systemu nazw domen (mDNS)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-150">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="b5e4c-151">Odnajdywanie usług oparte na systemie DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-151">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="b5e4c-152">DNS — minimalna ilość pamięci FLASH od 2,4 KB do 3 KB, 1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-152">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-153">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="b5e4c-153">Client support</span></span>
* <span data-ttu-id="b5e4c-154">Serwery mDNS i DNS-SD są dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-154">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="b5e4c-155">POP3</span><span class="sxs-lookup"><span data-stu-id="b5e4c-155">POP3</span></span>

* <span data-ttu-id="b5e4c-156">Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-156">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="b5e4c-157">Minimalnie 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-157">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-158">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="b5e4c-158">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="b5e4c-159">Telnet</span><span class="sxs-lookup"><span data-stu-id="b5e4c-159">TELNET</span></span>

* <span data-ttu-id="b5e4c-160">Minimalnie 0,5 KB i 0,3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-160">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-161">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-161">Client and server support</span></span>
* <span data-ttu-id="b5e4c-162">Intuicyjne interfejsy API Telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-162">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="b5e4c-163">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-163">FTP, TFTP</span></span>

* <span data-ttu-id="b5e4c-164">protokół transferu plików (FTP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-164">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="b5e4c-165">Protokół TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-165">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="b5e4c-166">MINIMALNA PAMIĘĆ FLASH FTP od 1,8 KB do 7,2 KB, od 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-166">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-167">TFTP Minimalna 1,7 KB do 2,4 KB pamięci FLASH, od 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-167">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-168">Obsługa klientów i serwerów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-168">Client and server support</span></span>
* <span data-ttu-id="b5e4c-169">Intuicyjne interfejsy API FTP i TFTP: *nx_ftp_ \** lub *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-169">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="b5e4c-170">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="b5e4c-170">PPP, PPPoE</span></span>

* <span data-ttu-id="b5e4c-171">Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-171">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="b5e4c-172">Point-to-Point Protocol przez Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-172">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="b5e4c-173">Minimalnie 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-173">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-174">Intuicyjne interfejsy API PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-174">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="b5e4c-175">PpPoE jest dostępne tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-175">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="b5e4c-176">SNTP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-176">SNTP</span></span>

* <span data-ttu-id="b5e4c-177">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-177">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="b5e4c-178">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-178">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="b5e4c-179">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="b5e4c-179">Client support</span></span>
* <span data-ttu-id="b5e4c-180">Intuicyjne interfejsy API SNTP: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-180">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="legacy-code-support"></a><span data-ttu-id="b5e4c-181">Obsługa starszego kodu</span><span class="sxs-lookup"><span data-stu-id="b5e4c-181">Legacy code support</span></span>

* <span data-ttu-id="b5e4c-182">Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda</span><span class="sxs-lookup"><span data-stu-id="b5e4c-182">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="b5e4c-183">Igmp</span><span class="sxs-lookup"><span data-stu-id="b5e4c-183">IGMP</span></span>

* <span data-ttu-id="b5e4c-184">Protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-184">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="b5e4c-185">Minimalna pamięć FLASH 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="b5e4c-185">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="b5e4c-186">Obsługa grup multiemisji IPv4</span><span class="sxs-lookup"><span data-stu-id="b5e4c-186">IPv4 multicast group support</span></span>
* <span data-ttu-id="b5e4c-187">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="b5e4c-187">IXIA IxANVL validated</span></span>
* <span data-ttu-id="b5e4c-188">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-188">Optional IGMP statistics</span></span>
* <span data-ttu-id="b5e4c-189">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-189">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="b5e4c-190">Intuicyjne interfejsy API IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-190">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="b5e4c-191">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-191">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="b5e4c-192">Datagram Transport Layer Security (DTLS) 1.0 i 1.2</span><span class="sxs-lookup"><span data-stu-id="b5e4c-192">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="b5e4c-193">Minimalna pamięć FLASH 11 KB</span><span class="sxs-lookup"><span data-stu-id="b5e4c-193">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="b5e4c-194">Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz</span><span class="sxs-lookup"><span data-stu-id="b5e4c-194">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="b5e4c-195">Uproszczona implementacja X.509</span><span class="sxs-lookup"><span data-stu-id="b5e4c-195">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="b5e4c-196">W pełni zintegrowane z Azure RTOS NetX Duo UDP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-196">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="b5e4c-197">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="b5e4c-197">Hardware Crypto Support</span></span>
* <span data-ttu-id="b5e4c-198">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-198">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="b5e4c-199">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="b5e4c-199">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="b5e4c-200">Obsługa zaszyfrowanych kluczy (zależna od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-200">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="b5e4c-201">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-201">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="b5e4c-202">Transport Layer Security (TLS) 1.0, 1.1 i 1.2</span><span class="sxs-lookup"><span data-stu-id="b5e4c-202">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="b5e4c-203">Minimalna pamięć FLASH 8,8 KB</span><span class="sxs-lookup"><span data-stu-id="b5e4c-203">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="b5e4c-204">Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz</span><span class="sxs-lookup"><span data-stu-id="b5e4c-204">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="b5e4c-205">Uproszczona implementacja X.509</span><span class="sxs-lookup"><span data-stu-id="b5e4c-205">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="b5e4c-206">W pełni zintegrowane z Azure RTOS TCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-206">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="b5e4c-207">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="b5e4c-207">Hardware Crypto Support</span></span>
* <span data-ttu-id="b5e4c-208">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-208">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="b5e4c-209">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="b5e4c-209">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="b5e4c-210">Obsługa zaszyfrowanych kluczy (zależna od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-210">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="b5e4c-211">ICMP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-211">ICMP</span></span>

* <span data-ttu-id="b5e4c-212">Protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-212">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="b5e4c-213">Minimalna pamięć FLASH 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="b5e4c-213">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="b5e4c-214">Obsługa protokołu IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="b5e4c-214">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="b5e4c-215">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="b5e4c-215">IXIA IxANVL validated</span></span>
* <span data-ttu-id="b5e4c-216">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="b5e4c-216">Ping request and ping response</span></span>
* <span data-ttu-id="b5e4c-217">Opcjonalne zawieszenie wątku na żądaniach ping</span><span class="sxs-lookup"><span data-stu-id="b5e4c-217">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="b5e4c-218">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="b5e4c-218">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5e4c-219">Opcjonalne statystyki ICMP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-219">Optional ICMP statistics</span></span>
* <span data-ttu-id="b5e4c-220">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-220">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="b5e4c-221">Intuicyjne interfejsy API ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-221">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="b5e4c-222">UDP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-222">UDP</span></span>

* <span data-ttu-id="b5e4c-223">Protokół UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-223">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="b5e4c-224">Minimalna pamięć FLASH 2,5 KB, 124 gniazda w bajtach pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-224">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="b5e4c-225">Szybkie przetwarzanie pakietów TCP w pobliżu wire speed:</span><span class="sxs-lookup"><span data-stu-id="b5e4c-225">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="b5e4c-226">RX 95 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 14% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="b5e4c-226">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="b5e4c-227">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 10% wykorzystanie MIKROU</span><span class="sxs-lookup"><span data-stu-id="b5e4c-227">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="b5e4c-228">Szybka ścieżka UDP™ technologia</span><span class="sxs-lookup"><span data-stu-id="b5e4c-228">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="b5e4c-229">Brak limitów liczby protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-229">No limits on the number of UDP</span></span>
* <span data-ttu-id="b5e4c-230">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="b5e4c-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="b5e4c-231">Opcjonalne zawieszenie podczas odbierania gniazda</span><span class="sxs-lookup"><span data-stu-id="b5e4c-231">Optional suspension on socket receive</span></span>
* <span data-ttu-id="b5e4c-232">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="b5e4c-232">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5e4c-233">Opcjonalne statystyki UDP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-233">Optional UDP statistics</span></span>
* <span data-ttu-id="b5e4c-234">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-234">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="b5e4c-235">Intuicyjne interfejsy API UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-235">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="b5e4c-236">TCP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-236">TCP</span></span>

* <span data-ttu-id="b5e4c-237">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-237">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="b5e4c-238">Minimalna ilość pamięci RAM od 10,5 K8 do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-238">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="b5e4c-239">Szybkie przetwarzanie pakietów TCP w pobliżu wlre speed:</span><span class="sxs-lookup"><span data-stu-id="b5e4c-239">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="b5e4c-240">RX 93 Mb/s w sieci Ethernet 100 Mb/s, mikrouchem i @100MHz 20% wykorzystania mikroku</span><span class="sxs-lookup"><span data-stu-id="b5e4c-240">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="b5e4c-241">TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 27% wykorzystanie mikrojądek</span><span class="sxs-lookup"><span data-stu-id="b5e4c-241">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="b5e4c-242">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="b5e4c-242">Reliable connection</span></span>
* <span data-ttu-id="b5e4c-243">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-243">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="b5e4c-244">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="b5e4c-244">IXIA IxANVL validated</span></span>
* <span data-ttu-id="b5e4c-245">Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda</span><span class="sxs-lookup"><span data-stu-id="b5e4c-245">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="b5e4c-246">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="b5e4c-246">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5e4c-247">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-247">Optional TCP statistics</span></span>
* <span data-ttu-id="b5e4c-248">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-248">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="b5e4c-249">Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-249">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="b5e4c-250">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-250">ARP/RARP</span></span>

* <span data-ttu-id="b5e4c-251">Protokół rozpoznawania adresów (ARP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-251">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="b5e4c-252">Protokół RARP (Reverse Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-252">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="b5e4c-253">Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-253">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="b5e4c-254">Dynamiczna rozdzielczość 32-blt adresów IPv4 i 48 blt adresów MAC</span><span class="sxs-lookup"><span data-stu-id="b5e4c-254">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="b5e4c-255">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="b5e4c-255">IXIA IxANVL validated</span></span>
* <span data-ttu-id="b5e4c-256">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-256">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="b5e4c-257">Obsługa dużych ARP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-257">Gratuitous ARP support</span></span>
* <span data-ttu-id="b5e4c-258">Opcjonalne statystyki ARP/RARP określone przez aplikację</span><span class="sxs-lookup"><span data-stu-id="b5e4c-258">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="b5e4c-259">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-259">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="b5e4c-260">Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="b5e4c-260">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="b5e4c-261">Protokół &amp; IPv6 protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="b5e4c-261">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="b5e4c-262">Protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-262">Internet Protocol (IP)</span></span>
* <span data-ttu-id="b5e4c-263">Minimalna ilość pamięci FLASH od 3,5 KB do 8,5 KB, od 2 KB do 3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="b5e4c-263">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="b5e4c-264">Piconet™ architektura</span><span class="sxs-lookup"><span data-stu-id="b5e4c-264">Piconet™ architecture</span></span>
* <span data-ttu-id="b5e4c-265">Szybka wydajność prawie z wire speed</span><span class="sxs-lookup"><span data-stu-id="b5e4c-265">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="b5e4c-266">Obsługa wielu interfejsów</span><span class="sxs-lookup"><span data-stu-id="b5e4c-266">Multiple interface support</span></span>
* <span data-ttu-id="b5e4c-267">Obsługa wielunadresowych</span><span class="sxs-lookup"><span data-stu-id="b5e4c-267">Multihomed support</span></span>
* <span data-ttu-id="b5e4c-268">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="b5e4c-268">Static routing support</span></span>
* <span data-ttu-id="b5e4c-269">Obsługa fragmentacji/ponownego zsadu ADRESÓW IP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-269">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="b5e4c-270">Obsługa adresów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="b5e4c-270">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="b5e4c-271">Zweryfikowane przez IxANVL IXANVL</span><span class="sxs-lookup"><span data-stu-id="b5e4c-271">IXIA IxANVL validated</span></span>
* <span data-ttu-id="b5e4c-272">Certyfikacja gotowego logo IPv6 fazy II</span><span class="sxs-lookup"><span data-stu-id="b5e4c-272">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="b5e4c-273">Opcjonalne statystyki adresów IP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-273">Optional IP statistics</span></span>
* <span data-ttu-id="b5e4c-274">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej</span><span class="sxs-lookup"><span data-stu-id="b5e4c-274">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="b5e4c-275">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-275">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="b5e4c-276">Intuicyjne interfejsy API warstwy adresów IP: *nx_ip_, \** *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="b5e4c-276">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="b5e4c-277">Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304, klasa C, ISO 26262 ASIL D i EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="b5e4c-277">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="b5e4c-278">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="b5e4c-278">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="b5e4c-279">Zabezpieczenia protokołu internetowego (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-279">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="b5e4c-280">Warstwa ip</span><span class="sxs-lookup"><span data-stu-id="b5e4c-280">IP layer</span></span>
* <span data-ttu-id="b5e4c-281">Sprzętowa obsługa kryptografii</span><span class="sxs-lookup"><span data-stu-id="b5e4c-281">Hardware crypto support</span></span>
* <span data-ttu-id="b5e4c-282">Obsługa kryptografii oprogramowania, w tym:</span><span class="sxs-lookup"><span data-stu-id="b5e4c-282">Software crypto support, including:</span></span>
    * <span data-ttu-id="b5e4c-283">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="b5e4c-283">DES, 3DES</span></span>
    * <span data-ttu-id="b5e4c-284">AES</span><span class="sxs-lookup"><span data-stu-id="b5e4c-284">AES</span></span>
    * <span data-ttu-id="b5e4c-285">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="b5e4c-285">HMAC-MD5</span></span>
    * <span data-ttu-id="b5e4c-286">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="b5e4c-286">HMAC-SHA1</span></span>
* <span data-ttu-id="b5e4c-287">Obsługa usługi Internet Key Exchange (IKE) w wersji 2</span><span class="sxs-lookup"><span data-stu-id="b5e4c-287">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="b5e4c-288">Intuicyjne interfejsy API protokołu IPsec: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-288">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="b5e4c-289">IPsec jest dostępny tylko w Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b5e4c-289">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="b5e4c-290">Sejf i bezpieczne</span><span class="sxs-lookup"><span data-stu-id="b5e4c-290">Safe and secure</span></span>

<span data-ttu-id="b5e4c-291">Azure RTOS NetX Duo jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-291">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="b5e4c-292">Zabezpieczenia te są udostępniane za pośrednictwem produktów zabezpieczeń dodatków, w tym protokołu IPsec, protokołu SSL, protokołu TLS i protokołu DTLS.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-292">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="b5e4c-293">Ponadto aplikacja ma pełną kontrolę nad całym dostępem zewnętrznym do aplikacji Azure RTOS NetX Duo, co znacznie ułatwia określanie ryzyka bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-293">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="b5e4c-294">Microsoft Azure System RTOS udostępnia producentom OEM składniki do zabezpieczania komunikacji oraz tworzenia kodu i izolacji danych przy użyciu podstawowych mechanizmów ochrony sprzętowej mcu/mpu.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-294">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="b5e4c-295">Konstruktor urządzenia ostatecznie odpowiada za zapewnienie, że urządzenie w pełni spełnia zmieniające się wymagania dotyczące zabezpieczeń związane z konkretnym przypadekem użycia.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-295">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="b5e4c-296">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="b5e4c-296">Interoperability verification</span></span>

<span data-ttu-id="b5e4c-297">NetX Duo jest zgodny ze standardami RFC i oferuje pełne współdziałanie z urządzeniami dla większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-297">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logo gotowe do użycia IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="b5e4c-299">Azure RTOS NetX Duo jest jednym z jedynych osadzonych stosów TCP/IP do osiągnięcia rygorystycznego certyfikatu IPv6-Ready Logo, dowodu na to, że przeszedł testy zgodności i współdziałania, administrowane i weryfikowane przez forum IPv6.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-299">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="b5e4c-300">NetX Duo korzysta również ze standardu branżowego IxANVL (Automated Network Validation Library) do implementacji podstawowego protokołu TCP/IP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-300">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="b5e4c-301">Kompleksowe rozwiązanie IoT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-301">Comprehensive IoT solution</span></span>

<span data-ttu-id="b5e4c-302">NetX Duo ma jedną z najbardziej kompleksowych sieci TCP/IP dla głęboko osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-302">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="b5e4c-303">Ta obsługa obejmuje następujące produkty protokołu dodatku.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-303">This support includes the following add-on protocol products.</span></span>

* <span data-ttu-id="b5e4c-304">MQTT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-304">MQTT</span></span>
* <span data-ttu-id="b5e4c-305">CoAP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-305">CoAP</span></span>
* <span data-ttu-id="b5e4c-306">CELUM2M</span><span class="sxs-lookup"><span data-stu-id="b5e4c-306">LWM2M</span></span>
* <span data-ttu-id="b5e4c-307">6LoWPAN</span><span class="sxs-lookup"><span data-stu-id="b5e4c-307">6LoWPAN</span></span>
* <span data-ttu-id="b5e4c-308">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-308">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="b5e4c-309">IPsec</span><span class="sxs-lookup"><span data-stu-id="b5e4c-309">IPsec</span></span>
* <span data-ttu-id="b5e4c-310">AutoIP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-310">AutoIP</span></span>
* <span data-ttu-id="b5e4c-311">DHCP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-311">DHCP</span></span>
* <span data-ttu-id="b5e4c-312">DNS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-312">DNS</span></span>
* <span data-ttu-id="b5e4c-313">Mdns</span><span class="sxs-lookup"><span data-stu-id="b5e4c-313">mDNS</span></span>
* <span data-ttu-id="b5e4c-314">DNS-SD</span><span class="sxs-lookup"><span data-stu-id="b5e4c-314">DNS-SD</span></span>
* <span data-ttu-id="b5e4c-315">FTP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-315">FTP</span></span>
* <span data-ttu-id="b5e4c-316">HTTP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-316">HTTP</span></span>
* <span data-ttu-id="b5e4c-317">IPsec</span><span class="sxs-lookup"><span data-stu-id="b5e4c-317">IPsec</span></span>
* <span data-ttu-id="b5e4c-318">NAT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-318">NAT</span></span>
* <span data-ttu-id="b5e4c-319">POP3</span><span class="sxs-lookup"><span data-stu-id="b5e4c-319">POP3</span></span>
* <span data-ttu-id="b5e4c-320">Ppp</span><span class="sxs-lookup"><span data-stu-id="b5e4c-320">PPP</span></span>
* <span data-ttu-id="b5e4c-321">Pppoe</span><span class="sxs-lookup"><span data-stu-id="b5e4c-321">PPPoE</span></span>
* <span data-ttu-id="b5e4c-322">SMTP</span><span class="sxs-lookup"><span data-stu-id="b5e4c-322">SMTP</span></span>
* <span data-ttu-id="b5e4c-323">SNMP v1/2/3</span><span class="sxs-lookup"><span data-stu-id="b5e4c-323">SNMP v1/2/3</span></span>
* <span data-ttu-id="b5e4c-324">Protokół Telnet</span><span class="sxs-lookup"><span data-stu-id="b5e4c-324">Telnet</span></span>
* <span data-ttu-id="b5e4c-325">Tftp</span><span class="sxs-lookup"><span data-stu-id="b5e4c-325">TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="b5e4c-326">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="b5e4c-326">Advanced technology</span></span>

<span data-ttu-id="b5e4c-327">Azure RTOS NetX Duo to zaawansowana technologia, która obejmuje następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-327">Azure RTOS NetX Duo is advanced technology that includes the following.</span></span>

* <span data-ttu-id="b5e4c-328">Piconet™ architektura</span><span class="sxs-lookup"><span data-stu-id="b5e4c-328">Piconet™ architecture</span></span>
* <span data-ttu-id="b5e4c-329">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="b5e4c-329">Automatic scaling</span></span>
* <span data-ttu-id="b5e4c-330">Technologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="b5e4c-330">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="b5e4c-331">Elastyczne zarządzanie pakietami</span><span class="sxs-lookup"><span data-stu-id="b5e4c-331">Flexible packet management</span></span>
* <span data-ttu-id="b5e4c-332">Interfejs API bez kopiowania i implementacja</span><span class="sxs-lookup"><span data-stu-id="b5e4c-332">Zero-copy API and implementation</span></span>
* <span data-ttu-id="b5e4c-333">Obsługa wielunadresowych</span><span class="sxs-lookup"><span data-stu-id="b5e4c-333">Multihomed support</span></span>
* <span data-ttu-id="b5e4c-334">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="b5e4c-334">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5e4c-335">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="b5e4c-335">Static routing support</span></span>
* <span data-ttu-id="b5e4c-336">IPsec</span><span class="sxs-lookup"><span data-stu-id="b5e4c-336">IPsec</span></span>
* <span data-ttu-id="b5e4c-337">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="b5e4c-337">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="b5e4c-338">Azure RTOS analizy systemu TraceX</span><span class="sxs-lookup"><span data-stu-id="b5e4c-338">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="b5e4c-339">Powiązane usługi</span><span class="sxs-lookup"><span data-stu-id="b5e4c-339">Related services</span></span>

<span data-ttu-id="b5e4c-340">NetX Duo oferuje następujące dodatkowe usługi.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-340">NetX Duo provides the following additional services.</span></span>

* <span data-ttu-id="b5e4c-341">Oprogramowanie pośredniczące usługi Azure IoT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-341">Azure IoT Middleware</span></span>
* <span data-ttu-id="b5e4c-342">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="b5e4c-342">Azure Defender</span></span>
* <span data-ttu-id="b5e4c-343">Aktualizacja urządzenia dla IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-343">Device update for IoT Hub.</span></span>

### <a name="azure-iot-middleware"></a><span data-ttu-id="b5e4c-344">Oprogramowanie pośredniczące usługi Azure IoT</span><span class="sxs-lookup"><span data-stu-id="b5e4c-344">Azure IoT Middleware</span></span>

<span data-ttu-id="b5e4c-345">NetX Duo zawiera oprogramowanie pośredniczące [Azure IoT](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md)dla usługi Azure RTOS , bibliotekę specyficzną dla platformy, która działa jako warstwa powiązania między usługą Azure RTOS i zestawem Azure SDK dla osadzonego języka C, aby ułatwić łączność z usługami Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-345">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="b5e4c-346">Poniżej przedstawiono cele oprogramowania pośredniczącego usługi Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-346">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="b5e4c-347">Udostępnij inteligentne interfejsy klienckie (IoTHub_Client, DeviceProvisioning_Client), których deweloperzy potrzebują dla swoich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-347">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="b5e4c-348">Organizowanie interakcji między osadzonym zestawem SDK języka C a platformą.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-348">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="b5e4c-349">Podaj Azure RTOS inicjowania platformy.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-349">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="b5e4c-350">IoT Plug and Play pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-350">IoT Plug and Play support.</span></span>
* <span data-ttu-id="b5e4c-351">Możliwości zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-351">Security capabilities.</span></span>
* <span data-ttu-id="b5e4c-352">Należy pamiętać o ograniczeniach zasobów.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-352">Resource limitation aware.</span></span>
* <span data-ttu-id="b5e4c-353">Obsługa protokołów.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-353">Protocol support.</span></span>

![Azure RTOS związane z NetX Duo](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="b5e4c-355">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="b5e4c-355">Azure Defender</span></span>

<span data-ttu-id="b5e4c-356">Moduł Azure Defender dla IoT zabezpieczeń zapewnia kompleksowe rozwiązanie zabezpieczeń dla Azure RTOS urządzeń.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-356">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="b5e4c-357">Moduł zabezpieczeń usługi Azure RTOS oferuje wykrywanie złośliwych działań sieciowych, niestandardowe oparte na alertach podstawy zachowania urządzenia i pomaga poprawić higienę zabezpieczeń urządzenia.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-357">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="b5e4c-358">Dowiedz się więcej o module zabezpieczeń dla [Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) lub rozpoczynanie pracy z konfigurowaniem modułu zabezpieczeń dla usługi [Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) Szybki start.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-358">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="b5e4c-359">Aktualizacja urządzenia dla IoT Hub</span><span class="sxs-lookup"><span data-stu-id="b5e4c-359">Device Update for IoT Hub</span></span>

<span data-ttu-id="b5e4c-360">Azure [Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) to usługa, która umożliwia wdrażanie aktualizacji w powietrzu (OTA) dla urządzeń IoT.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-360">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="b5e4c-361">Moduł Device Update for IoT Hub to implementacja aktualizacji urządzenia dla agenta IoT Hub w programie Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-361">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="b5e4c-362">Udostępnia on proste interfejsy API dla konstruktorów urządzeń, które integrują możliwość aktualizacji urządzeń w swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-362">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="b5e4c-363">Zapoznaj się z przykładami kluczowych tablic ewaluacyjnych, które zawierają przewodniki z wprowadzeniem, aby dowiedzieć się, jak konfigurować, kompilować i wdrażać aktualizacje over-the-air (OTA) na urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-363">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="b5e4c-364">Możesz też dowiedzieć się więcej na temat używania aktualizacji urządzenia na [IoT Hub z Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="b5e4c-364">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5e4c-365">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5e4c-365">Next steps</span></span>

<span data-ttu-id="b5e4c-366">Aby dowiedzieć się więcej na temat netx duo, zacznij od Azure RTOS NetX Duo User Guide (Podręcznik użytkownika aplikacji [NetX Duo).](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="b5e4c-366">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
