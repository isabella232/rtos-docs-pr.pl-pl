---
title: Opis usługi Azure RTO NetX Duo
description: Usługa Azure RTO NetX Duo to zaawansowany stos sieci TCP/IP klasy przemysłowej zaprojektowany specjalnie z myślą o głęboko osadzonych aplikacjach w czasie rzeczywistym i IoT.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822830"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="20d0b-103">Omówienie usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="20d0b-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="20d0b-104">Azure RTO NetX Duo — osadzony stos sieci TCP/IP jest zaawansowanym, przemysłowym stosem protokołów TCP/IP firmy Microsoft, który jest przeznaczony specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i dla IoT.</span><span class="sxs-lookup"><span data-stu-id="20d0b-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="20d0b-105">NetX Duo oferuje aplikacje osadzone z podstawowymi protokołami sieciowymi, takimi jak IPv4, IPv6, TCP i UDP, a także kompletny pakiet dodatkowych protokołów dodatków o wyższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="20d0b-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="20d0b-106">Usługa Azure RTO NetX Duo oferuje zabezpieczenia za pośrednictwem dodatkowych produktów zabezpieczeń, w tym Azure RTO NetX Secure IPsec i Azure RTO NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="20d0b-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="20d0b-107">Wszystkie te połączone z małą ilością, szybkim wykonaniem i najbardziej łatwym w obsłużeniu, dzięki czemu usługa Azure RTO NetX Duo najlepiej sprawdza się w przypadku najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="20d0b-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="20d0b-108">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="20d0b-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="20d0b-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="20d0b-109">MQTT</span></span>

* <span data-ttu-id="20d0b-110">Transport telemetrii kolejki komunikatów (MQTT)</span><span class="sxs-lookup"><span data-stu-id="20d0b-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="20d0b-111">Minimum 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="20d0b-112">Intuicyjne interfejsy API MQTT: *nx_mqtt_*\*</span><span class="sxs-lookup"><span data-stu-id="20d0b-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="20d0b-113">Adres IP</span><span class="sxs-lookup"><span data-stu-id="20d0b-113">Auto IP</span></span>

* <span data-ttu-id="20d0b-114">Automatyczne przypisywanie adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="20d0b-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="20d0b-115">Minimalny 1,2 KB, 300 bajtów pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="20d0b-116">Intuicyjne interfejsy API AutoIP: *nx_autoip_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="20d0b-117">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="20d0b-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="20d0b-118">HTTP 1,0</span><span class="sxs-lookup"><span data-stu-id="20d0b-118">HTTP 1.0</span></span>

* <span data-ttu-id="20d0b-119">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="20d0b-120">Minimum 2,8 KB do 4,8 KB FLASH/0,4 KB do 1,0 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="20d0b-121">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="20d0b-121">Client and server support</span></span>
* <span data-ttu-id="20d0b-122">Intuicyjne interfejsy API: *nx_http_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="20d0b-123">HTTP/HTTPS 1,1</span><span class="sxs-lookup"><span data-stu-id="20d0b-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="20d0b-124">Protokół HTTP (Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="20d0b-125">Minimum 3,0 KB do 9,5 KB FLASH/0,5 KB do 2 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="20d0b-126">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="20d0b-126">Client and server support</span></span>
* <span data-ttu-id="20d0b-127">Wiele przychodzących sesji klienta</span><span class="sxs-lookup"><span data-stu-id="20d0b-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="20d0b-128">Zwykły tekst i szyfrowany protokół HTTPS</span><span class="sxs-lookup"><span data-stu-id="20d0b-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="20d0b-129">Obsługa połączeń trwałych</span><span class="sxs-lookup"><span data-stu-id="20d0b-129">Persistent connection support</span></span>
* <span data-ttu-id="20d0b-130">Przekazywanie wieloczęściowego pliku</span><span class="sxs-lookup"><span data-stu-id="20d0b-130">Multipart file upload</span></span>
* <span data-ttu-id="20d0b-131">W pełni zintegrowana z usługą Azure RTO NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="20d0b-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="20d0b-132">Intuicyjne interfejsy API: *nx_web_http \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="20d0b-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="20d0b-133">SMTP</span></span>

* <span data-ttu-id="20d0b-134">Simple Pasażing Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="20d0b-135">Minimum 4,1 KB i 0,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-136">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="20d0b-136">Client support</span></span>
* <span data-ttu-id="20d0b-137">Intuicyjne interfejsy API SMTP: *nx_smtp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="20d0b-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="20d0b-138">DHCP</span></span>

* <span data-ttu-id="20d0b-139">Protokół DHCP</span><span class="sxs-lookup"><span data-stu-id="20d0b-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="20d0b-140">Minimum 3,6 KB do 4,6 KB FLASH, rozmiar pamięci RAM 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-141">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="20d0b-141">Client and server support</span></span>
* <span data-ttu-id="20d0b-142">Obsługa protokołów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="20d0b-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="20d0b-143">Intuicyjne interfejsy API DHCP: *nx_dhcp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="20d0b-144">NAT</span><span class="sxs-lookup"><span data-stu-id="20d0b-144">NAT</span></span>

* <span data-ttu-id="20d0b-145">Translator adresów sieciowych (NAT)</span><span class="sxs-lookup"><span data-stu-id="20d0b-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="20d0b-146">Minimalne rozmiary pamięci RAM: 3,5 K6 i 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-147">Obsługa adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="20d0b-147">IPv4 address support</span></span>
* <span data-ttu-id="20d0b-148">Intuicyjne interfejsy API translatora adresów sieciowych: *nx_nat_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="20d0b-149">Translator adresów sieciowych jest dostępny tylko w przypadku platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="20d0b-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="20d0b-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="20d0b-150">SNMP</span></span>

* <span data-ttu-id="20d0b-151">Protokół SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="20d0b-152">Minimum 10,9 KB i 2,6 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-153">Obsługa agentów dla VI, v2 i V3</span><span class="sxs-lookup"><span data-stu-id="20d0b-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="20d0b-154">Intuicyjne interfejsy API protokołu SNMP: *nx_snmp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="20d0b-155">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="20d0b-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="20d0b-156">System nazw domen (DNS)</span><span class="sxs-lookup"><span data-stu-id="20d0b-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="20d0b-157">System nazw domen multiemisji (mDNS)</span><span class="sxs-lookup"><span data-stu-id="20d0b-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="20d0b-158">Odnajdowanie usług oparte na systemie DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="20d0b-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="20d0b-159">Minimalna 2,4 KB do 3 KB, pojemność pamięci RAM: 1 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-160">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="20d0b-160">Client support</span></span>
* <span data-ttu-id="20d0b-161">Intuicyjne interfejsy API: *nx_dns_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="20d0b-162">usługi mDNS i DNS-SD są dostępne tylko w usłudze Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="20d0b-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="20d0b-163">P0P3</span><span class="sxs-lookup"><span data-stu-id="20d0b-163">P0P3</span></span>

* <span data-ttu-id="20d0b-164">Post Office Protocol w wersji 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="20d0b-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="20d0b-165">Minimum 8,1 KB i 1,4 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-166">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="20d0b-166">Client support</span></span>
* <span data-ttu-id="20d0b-167">Intuicyjne interfejsy API P0P3: *nx_pop3_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="20d0b-168">Program</span><span class="sxs-lookup"><span data-stu-id="20d0b-168">TELNET</span></span>

* <span data-ttu-id="20d0b-169">Minimum 0,5 KB i 0,3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-170">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="20d0b-170">Client and server support</span></span>
* <span data-ttu-id="20d0b-171">Intuicyjne interfejsy API programu Telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="20d0b-172">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="20d0b-172">FTP, TFTP</span></span>

* <span data-ttu-id="20d0b-173">Protokół transferu plików (FTP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="20d0b-174">Protokół TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="20d0b-175">FTP minimum 1,8 KB do 7,2 KB FLASH, 0,6 KB do 2,1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-176">TFTP minimum 1,7 KB do 2,4 KB FLASH, 0,3 KB do 1,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-177">Obsługa klienta i serwera</span><span class="sxs-lookup"><span data-stu-id="20d0b-177">Client and server support</span></span>
* <span data-ttu-id="20d0b-178">Intuicyjne interfejsy API FTP i TFTP: *nx_ftp_ \** lub *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="20d0b-179">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="20d0b-179">PPP, PPPoE</span></span>

* <span data-ttu-id="20d0b-180">Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="20d0b-181">Point-to-Point Protocol przez sieć Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="20d0b-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="20d0b-182">Minimum 7,1 KB i 3,8 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-183">Intuicyjne interfejsy API protokołu PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="20d0b-184">Protokół PPPoE jest dostępny tylko w przypadku platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="20d0b-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="20d0b-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="20d0b-185">SNTP</span></span>

* <span data-ttu-id="20d0b-186">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="20d0b-187">Minimalna 4 KB i 0,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="20d0b-188">Obsługa klienta</span><span class="sxs-lookup"><span data-stu-id="20d0b-188">Client support</span></span>
* <span data-ttu-id="20d0b-189">Intuicyjne interfejsy API SNTP: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="20d0b-190">Interfejs API usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="20d0b-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="20d0b-191">Intuicyjny i spójny interfejs API</span><span class="sxs-lookup"><span data-stu-id="20d0b-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="20d0b-192">W konwencji nazewnictwa czasowników</span><span class="sxs-lookup"><span data-stu-id="20d0b-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="20d0b-193">Szybka, zerowa — implementacja interfejsu API</span><span class="sxs-lookup"><span data-stu-id="20d0b-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="20d0b-194">Wszystkie interfejsy API mają wiodące <i>nx_ \*</i> do łatwej identyfikacji jako Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="20d0b-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="20d0b-195">Blokowanie interfejsów API ma opcjonalny limit czasu wątku</span><span class="sxs-lookup"><span data-stu-id="20d0b-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="20d0b-196">Aby uzyskać więcej informacji, zobacz [Podręcznik użytkownika usługi Azure RTO NetX Duo](about-this-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="20d0b-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="20d0b-197">Opcjonalna warstwa BSD do przenoszenia kodu gniazda starszej wersji</span><span class="sxs-lookup"><span data-stu-id="20d0b-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="20d0b-198">IGMP</span><span class="sxs-lookup"><span data-stu-id="20d0b-198">IGMP</span></span>

* <span data-ttu-id="20d0b-199">Protokół IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="20d0b-200">Minimum 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="20d0b-201">Obsługa grup multiemisji IPv4</span><span class="sxs-lookup"><span data-stu-id="20d0b-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="20d0b-202">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="20d0b-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="20d0b-203">Opcjonalne statystyki IGMP</span><span class="sxs-lookup"><span data-stu-id="20d0b-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="20d0b-204">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="20d0b-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="20d0b-205">Intuicyjne interfejsy API protokołu IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="20d0b-206">Usługa Azure RTO NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="20d0b-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="20d0b-207">Datagram Transport Layer Security (DTLS) 1,0 i 1,2</span><span class="sxs-lookup"><span data-stu-id="20d0b-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="20d0b-208">Minimum 11 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="20d0b-209">Fast, RSA 2048-bitowy rozmiar klucza ~ 1 sekunda @120MHz</span><span class="sxs-lookup"><span data-stu-id="20d0b-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="20d0b-210">Ulepszona implementacja X. 509</span><span class="sxs-lookup"><span data-stu-id="20d0b-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="20d0b-211">W pełni zintegrowane z usługą Azure RTO NetX Duo UDP Sockets</span><span class="sxs-lookup"><span data-stu-id="20d0b-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="20d0b-212">Obsługa kryptografii sprzętowej</span><span class="sxs-lookup"><span data-stu-id="20d0b-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="20d0b-213">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="20d0b-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="20d0b-214">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywaniem) i ECDH (szyfrowanie), w tym P-krzywe 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="20d0b-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="20d0b-215">Obsługa zaszyfrowanych kluczy (zależnych od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="20d0b-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="20d0b-216">Azure RTO NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="20d0b-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="20d0b-217">Transport Layer Security (TLS) 1,0, 1,1 i 1,2</span><span class="sxs-lookup"><span data-stu-id="20d0b-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="20d0b-218">Minimum 8,8 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="20d0b-219">Fast, RSA 2048-bitowy rozmiar klucza ~ 1 sekunda @120MHz</span><span class="sxs-lookup"><span data-stu-id="20d0b-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="20d0b-220">Ulepszona implementacja X. 509</span><span class="sxs-lookup"><span data-stu-id="20d0b-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="20d0b-221">W pełni zintegrowane z usługą Azure RTO NetX Duo TCP Sockets</span><span class="sxs-lookup"><span data-stu-id="20d0b-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="20d0b-222">Obsługa kryptografii sprzętowej</span><span class="sxs-lookup"><span data-stu-id="20d0b-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="20d0b-223">Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="20d0b-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="20d0b-224">Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywaniem) i ECDH (szyfrowanie), w tym P-krzywe 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="20d0b-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="20d0b-225">Obsługa zaszyfrowanych kluczy (zależnych od sprzętu)</span><span class="sxs-lookup"><span data-stu-id="20d0b-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="20d0b-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="20d0b-226">ICMP</span></span>

* <span data-ttu-id="20d0b-227">Protokół ICMP (Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="20d0b-228">Minimum 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="20d0b-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="20d0b-229">Obsługa protokołów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="20d0b-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="20d0b-230">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="20d0b-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="20d0b-231">Żądanie ping i odpowiedź ping</span><span class="sxs-lookup"><span data-stu-id="20d0b-231">Ping request and ping response</span></span>
* <span data-ttu-id="20d0b-232">Opcjonalne zawieszenie wątku w żądaniach ping</span><span class="sxs-lookup"><span data-stu-id="20d0b-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="20d0b-233">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="20d0b-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="20d0b-234">Opcjonalne statystyki protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="20d0b-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="20d0b-235">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="20d0b-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="20d0b-236">Intuicyjne interfejsy API protokołu ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="20d0b-237">UDP</span><span class="sxs-lookup"><span data-stu-id="20d0b-237">UDP</span></span>

* <span data-ttu-id="20d0b-238">User Datagram Protocol (UDP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="20d0b-239">Minimalny 2,5 KB, 124 gniazd bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="20d0b-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="20d0b-240">Szybkie przetwarzanie pakietów TCP w bliskiej WireSpeed:</span><span class="sxs-lookup"><span data-stu-id="20d0b-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="20d0b-241">Odbieranie 95 MB/s na 100 MB/s, MIKROKONTROLERY @100MHz , 14% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="20d0b-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="20d0b-242">TX 94 MB/s w dniu 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 10% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="20d0b-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="20d0b-243">Szybka ścieżka UDP™ technologia</span><span class="sxs-lookup"><span data-stu-id="20d0b-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="20d0b-244">Brak limitów liczby UDP</span><span class="sxs-lookup"><span data-stu-id="20d0b-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="20d0b-245">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="20d0b-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="20d0b-246">Opcjonalne zawieszenie dla odbioru gniazda</span><span class="sxs-lookup"><span data-stu-id="20d0b-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="20d0b-247">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="20d0b-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="20d0b-248">Opcjonalne statystyki protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="20d0b-248">Optional UDP statistics</span></span>
* <span data-ttu-id="20d0b-249">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="20d0b-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="20d0b-250">Intuicyjne interfejsy API protokołu UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="20d0b-251">TCP</span><span class="sxs-lookup"><span data-stu-id="20d0b-251">TCP</span></span>

* <span data-ttu-id="20d0b-252">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="20d0b-253">Minimalna 10,5 K8 do 12,5 KB FLASH, 280 bajtów pamięci RAM na gniazdo</span><span class="sxs-lookup"><span data-stu-id="20d0b-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="20d0b-254">Szybkie przetwarzanie pakietów TCP w bliskiej wlrespeed:</span><span class="sxs-lookup"><span data-stu-id="20d0b-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="20d0b-255">Odbieranie 93 MB/s na 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 20% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="20d0b-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="20d0b-256">TX 94 MB/s w dniu 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 27% mikrokontrolery</span><span class="sxs-lookup"><span data-stu-id="20d0b-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="20d0b-257">Niezawodne połączenie</span><span class="sxs-lookup"><span data-stu-id="20d0b-257">Reliable connection</span></span>
* <span data-ttu-id="20d0b-258">Brak limitów liczby gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="20d0b-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="20d0b-259">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="20d0b-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="20d0b-260">Opcjonalne zawieszenie dla odbioru i wysyłania gniazd</span><span class="sxs-lookup"><span data-stu-id="20d0b-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="20d0b-261">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="20d0b-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="20d0b-262">Opcjonalne statystyki TCP</span><span class="sxs-lookup"><span data-stu-id="20d0b-262">Optional TCP statistics</span></span>
* <span data-ttu-id="20d0b-263">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="20d0b-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="20d0b-264">Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="20d0b-265">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="20d0b-265">ARP/RARP</span></span>

* <span data-ttu-id="20d0b-266">Protokół ARP (Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="20d0b-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="20d0b-267">Protokół odwrotnego rozpoznawania adresów (RARP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="20d0b-268">Minimum 1,7 KB, rozmiar pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="20d0b-269">Dynamiczne rozpoznawanie 32 BLT IPv4 i 48-BLT adresów MAC</span><span class="sxs-lookup"><span data-stu-id="20d0b-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="20d0b-270">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="20d0b-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="20d0b-271">Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP</span><span class="sxs-lookup"><span data-stu-id="20d0b-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="20d0b-272">Obsługa klienta w usłudze ARP</span><span class="sxs-lookup"><span data-stu-id="20d0b-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="20d0b-273">Opcjonalna Statystyka ARP/RARP określona przez aplikację</span><span class="sxs-lookup"><span data-stu-id="20d0b-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="20d0b-274">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="20d0b-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="20d0b-275">Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *nx_rarp_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="20d0b-276">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="20d0b-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="20d0b-277">Protokół internetowy (IP)</span><span class="sxs-lookup"><span data-stu-id="20d0b-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="20d0b-278">Minimum 3,5 KB do 8,5 KB FLASH, Powierzchnia 2 KB do 3 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="20d0b-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="20d0b-279">Architektura™ Piconet</span><span class="sxs-lookup"><span data-stu-id="20d0b-279">Piconet™ architecture</span></span>
* <span data-ttu-id="20d0b-280">Szybka, prawie wirespeeda wydajność</span><span class="sxs-lookup"><span data-stu-id="20d0b-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="20d0b-281">Obsługa wielu interfejsów</span><span class="sxs-lookup"><span data-stu-id="20d0b-281">Multiple interface support</span></span>
* <span data-ttu-id="20d0b-282">Obsługa wieloadresowa</span><span class="sxs-lookup"><span data-stu-id="20d0b-282">Multihomed support</span></span>
* <span data-ttu-id="20d0b-283">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="20d0b-283">Static routing support</span></span>
* <span data-ttu-id="20d0b-284">Obsługa fragmentacji/odzestawów IP</span><span class="sxs-lookup"><span data-stu-id="20d0b-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="20d0b-285">Obsługa adresów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="20d0b-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="20d0b-286">Zweryfikowano IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="20d0b-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="20d0b-287">Certyfikacja logo gotowej do fazy II IPv6</span><span class="sxs-lookup"><span data-stu-id="20d0b-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="20d0b-288">Opcjonalne statystyki adresów IP</span><span class="sxs-lookup"><span data-stu-id="20d0b-288">Optional IP statistics</span></span>
* <span data-ttu-id="20d0b-289">Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej</span><span class="sxs-lookup"><span data-stu-id="20d0b-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="20d0b-290">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="20d0b-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="20d0b-291">Intuicyjne interfejsy API warstwy IP: *\* nx_ip_*, *nxd_ip_ \**, *nxd_ipv6_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="20d0b-292">Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D i EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="20d0b-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="20d0b-293">Azure RTO NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="20d0b-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="20d0b-294">Zabezpieczenia protokołu internetowego (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="20d0b-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="20d0b-295">Warstwa IP</span><span class="sxs-lookup"><span data-stu-id="20d0b-295">IP layer</span></span>
* <span data-ttu-id="20d0b-296">Obsługa kryptografii sprzętowej</span><span class="sxs-lookup"><span data-stu-id="20d0b-296">Hardware crypto support</span></span>
* <span data-ttu-id="20d0b-297">Obsługa kryptografii oprogramowania, w tym:</span><span class="sxs-lookup"><span data-stu-id="20d0b-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="20d0b-298">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="20d0b-298">DES, 3DES</span></span>
    * <span data-ttu-id="20d0b-299">AES</span><span class="sxs-lookup"><span data-stu-id="20d0b-299">AES</span></span>
    * <span data-ttu-id="20d0b-300">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="20d0b-300">HMAC-MD5</span></span>
    * <span data-ttu-id="20d0b-301">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="20d0b-301">HMAC-SHA1</span></span>
* <span data-ttu-id="20d0b-302">Obsługa usługi Internet Key Exchange (IKE) w wersji 2</span><span class="sxs-lookup"><span data-stu-id="20d0b-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="20d0b-303">Intuicyjne interfejsy API protokołu IPsec: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="20d0b-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="20d0b-304">Protokół IPsec jest dostępny tylko w przypadku platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="20d0b-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="20d0b-305">Niewielkie rozmiary</span><span class="sxs-lookup"><span data-stu-id="20d0b-305">Small-footprint</span></span>

<span data-ttu-id="20d0b-306">Usługa Azure RTO NetX Duo ma niewielkie rozmiary w wysokości 9 KB do 15 KB w przypadku podstawowych obsługi protokołów IP i UDP.</span><span class="sxs-lookup"><span data-stu-id="20d0b-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="20d0b-307">Do obsługi funkcji TCP jest wymagana dodatkowa ilość pamięci o wartości 10 KB do 13 KB.</span><span class="sxs-lookup"><span data-stu-id="20d0b-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="20d0b-308">Użycie pamięci RAM usługi Azure RTO NetX Duo zazwyczaj mieści się w zakresie od 2,6 KB do 3,6 KB oraz pamięci puli pakietów zdefiniowanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="20d0b-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="20d0b-309">Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar platformy Azure RTO NetX Duo jest automatycznie skalowany w oparciu o usługi używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="20d0b-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="20d0b-310">To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.</span><span class="sxs-lookup"><span data-stu-id="20d0b-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="20d0b-311">Szybkie wykonywanie</span><span class="sxs-lookup"><span data-stu-id="20d0b-311">Fast execution</span></span>

<span data-ttu-id="20d0b-312">Usługa Azure RTO NetX Duo oferuje implementację typu "wysyłanie i odbieranie pakietów o zerowej kopii", które są wysoce zintegrowane z platformą Azure RTO ThreadX, aby osiągnąć największą możliwą wydajność.</span><span class="sxs-lookup"><span data-stu-id="20d0b-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="20d0b-313">Na przykład usługa Azure RTO NetX Duo może zazwyczaj osiągnąć niemal WireSpeed transferów danych na procesorze 80 MHz (lub mniej), jednocześnie używając tylko niewielkiej części cykli procesora.</span><span class="sxs-lookup"><span data-stu-id="20d0b-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="20d0b-314">Proste i łatwe w użyciu</span><span class="sxs-lookup"><span data-stu-id="20d0b-314">Simple, easy-to-use</span></span>

<span data-ttu-id="20d0b-315">Interfejs API usługi Azure RTO NetX Duo jest intuicyjny, prosty i wysoce funkcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20d0b-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="20d0b-316">Nazwy interfejsów API są prawdziwe mówiące i nie są nazwami "zup alfabetu" ani o dużej liczbie skróconych, które są często używane w innych produktach sieciowych.</span><span class="sxs-lookup"><span data-stu-id="20d0b-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="20d0b-317">Wszystkie interfejsy API usługi Azure RTO NetX Duo mają wiodące *nx_* i są zgodne z konwencją nazewnictwa czasowników.</span><span class="sxs-lookup"><span data-stu-id="20d0b-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="20d0b-318">Ponadto istnieje spójność funkcjonalna w całym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="20d0b-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="20d0b-319">Na przykład wszystkie funkcje interfejsu API, które zawieszają, mają opcjonalny limit czasu, który działa w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="20d0b-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="20d0b-320">W przypadku starszych aplikacji usługa Azure RTO NetX Duo oferuje dodatkową warstwę zgodną z gniazdem BSD.</span><span class="sxs-lookup"><span data-stu-id="20d0b-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="20d0b-321">Ta warstwa ułatwia deweloperom łatwe Migrowanie dużych aplikacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="20d0b-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="20d0b-322">Bezpieczne i bezpieczne</span><span class="sxs-lookup"><span data-stu-id="20d0b-322">Safe and secure</span></span>

<span data-ttu-id="20d0b-323">Usługa Azure RTO NetX Duo jest bezpieczna.</span><span class="sxs-lookup"><span data-stu-id="20d0b-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="20d0b-324">Zabezpieczenia te są udostępniane za pośrednictwem produktów zabezpieczeń dodatku, takich jak IPsec, SSL, TLS i DTLS.</span><span class="sxs-lookup"><span data-stu-id="20d0b-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="20d0b-325">Ponadto aplikacja ma pełną kontrolę nad całym dostępem zewnętrznym do usługi Azure RTO NetX Duo, co znacznie ułatwia określanie zagrożeń bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="20d0b-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="20d0b-326">Microsoft Azure RTO udostępnia producentom OEM składniki do zabezpieczania komunikacji i tworzenia izolacji kodu i danych przy użyciu podstawowych mechanizmów ochrony sprzętu MIKROKONTROLERY/MPU.</span><span class="sxs-lookup"><span data-stu-id="20d0b-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="20d0b-327">W celu zapewnienia, że urządzenie jest w pełni zgodne z rozwijającymi się wymaganiami dotyczącymi bezpieczeństwa związanymi z konkretnym przypadkiem użycia, jest obowiązkiem konstruktora urządzeń.</span><span class="sxs-lookup"><span data-stu-id="20d0b-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="20d0b-328">Wstępnie certyfikowane przez TUV i UL do wielu standardów bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="20d0b-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="20d0b-329">Usługa Azure RTO NetX Duo została certyfikowana przez moimi-TUV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-62304, Klasa bezpieczeństwa SW, ISO 26262 ASIL D i EN 50128.</span><span class="sxs-lookup"><span data-stu-id="20d0b-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="20d0b-330">Certyfikat potwierdza, że usługa Azure RTO NetX Duo może zostać użyta w przypadku rozwoju oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności zabezpieczeń IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem".</span><span class="sxs-lookup"><span data-stu-id="20d0b-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="20d0b-331">MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, weryfikowania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="20d0b-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="20d0b-332">Standard bezpieczeństwa przemysłowego IEC 61508, a także wszystkie standardy, które są od niego pochodzące, w tym IEC-62304, ISO 26262 i EN 50128, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.</span><span class="sxs-lookup"><span data-stu-id="20d0b-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="MOIMI — certyfikat TUV":::

<span data-ttu-id="20d0b-334">Usługa Azure RTO NetX Duo została rozpoznana przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku h, CSA E60730-1 załącznik H, IEC 60730-1 w załączniku H, UL 60335-1 Załącznik R, IEC 60335-1, załącznik R i standardy bezpieczeństwa UL 1998 dla oprogramowania w składnikach programowalnych.</span><span class="sxs-lookup"><span data-stu-id="20d0b-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="20d0b-335">UL to globalna, niezależna firma zajmująca się ochroną bezpieczeństwa, która ma więcej niż wiek fachowych rozwiązań w zakresie bezpieczeństwa, od publicznego wdrożenia energii elektrycznej, aby nawiązać przełom w zakresie trwałości, odnawialnych energii i nanotechnologii.</span><span class="sxs-lookup"><span data-stu-id="20d0b-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU certyfikat UL":::

<span data-ttu-id="20d0b-337">Artefakty (certyfikat, Podręcznik bezpieczeństwa, raport testowy itp.) skojarzone z certyfikatami TUV i UL są dostępne do sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="20d0b-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="20d0b-338">W przypadku, gdy aplikacja wymaga dodatkowej certyfikacji, usługa certyfikacji jest dostępna w firmie Microsoft w celu zapewnienia certyfikacji klucza dla różnych standardów przy użyciu rzeczywistej platformy sprzętowej, a nawet w odniesieniu do kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20d0b-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="20d0b-339">Skontaktuj się z nami, aby uzyskać więcej informacji na temat naszej usługi certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="20d0b-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="20d0b-340">Criteria EAL4 + typowe kryteria certyfikacji zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="20d0b-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="20d0b-341">Usługa Azure RTO uzyskała certyfikaty zabezpieczeń Criteria EAL4 + Common kryteria.</span><span class="sxs-lookup"><span data-stu-id="20d0b-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="20d0b-342">Obiekt docelowy evalution (TOE) obejmuje platformę Azure RTO ThreadX, Azure RTO NetX Duo, Azure RTO NetX Secure TLS i Azure RTO NetX MQTT.</span><span class="sxs-lookup"><span data-stu-id="20d0b-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="20d0b-343">Reprezentuje to najbardziej typowe protokoły IoT wymagane przez głęboko osadzone czujniki, urządzenia, routery brzegowe i bramy.</span><span class="sxs-lookup"><span data-stu-id="20d0b-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Certyfikat EAL":::

<span data-ttu-id="20d0b-345">Funkcja oceny zabezpieczeń IT używana na potrzeby certyfikacji Microsoft Azure RTO SC Brightsight BV i urząd certyfikacji to SERTIT.</span><span class="sxs-lookup"><span data-stu-id="20d0b-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="20d0b-346">Sprawdzanie poprawności FIPS 140-2</span><span class="sxs-lookup"><span data-stu-id="20d0b-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="20d0b-347">Biblioteki kryptograficzne usługi Azure RTO NetX uzyskały certyfikat FIPS 140-2 140-2 dla oprogramowania, które określa wymagania dotyczące modułów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="20d0b-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="20d0b-348">Standard FIPS 140-2 wymaga, aby wszystkie federalne agencje rządowe i działy korzystające z zabezpieczeń opartych na kryptografii spełniały określone standardy dotyczące siły szyfrowania i możliwości.</span><span class="sxs-lookup"><span data-stu-id="20d0b-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="20d0b-349">Te standardy zabezpieczeń oparte na kryptografii są również rozpoznawane w Kanadzie i Unii Europejskiej.</span><span class="sxs-lookup"><span data-stu-id="20d0b-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="20d0b-350">Laboratorium oceny zabezpieczeń informacji używane na potrzeby bibliotek kryptograficznych usługi Azure RTO NetX było atsec, a urząd certyfikacji to Narodowy Instytut standardów i technologii (NIST).</span><span class="sxs-lookup"><span data-stu-id="20d0b-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="20d0b-351">Aby uzyskać dodatkowe informacje, przejrzyj [witrynę sieci Web NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) .</span><span class="sxs-lookup"><span data-stu-id="20d0b-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="20d0b-352">Weryfikacja współdziałania</span><span class="sxs-lookup"><span data-stu-id="20d0b-352">Interoperability verification</span></span>

<span data-ttu-id="20d0b-353">NetX Duo jest zgodna ze standardami RFC i oferuje pełną współdziałanie z urządzeniami dla większości dostawców.</span><span class="sxs-lookup"><span data-stu-id="20d0b-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logo gotowe do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="20d0b-355">Usługa Azure RTO NetX Duo to jeden z wbudowanych stosów TCP/IP, aby uzyskać rygorystyczne certyfikaty logo IPv6-Ready, dowód, że przeszedł zgodność i testy interoperacyjności, administrowane i zweryfikowane przez forum IPv6.</span><span class="sxs-lookup"><span data-stu-id="20d0b-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="20d0b-356">NetX Duo wykorzystuje również standardową bibliotekę usługi IxANVL (zautomatyzowanej weryfikacji sieci) dla implementacji protokołu TCP/IP w programie NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="20d0b-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="20d0b-357">Kompleksowe rozwiązanie IoT</span><span class="sxs-lookup"><span data-stu-id="20d0b-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="20d0b-358">Usługa Azure RTO NetX Duo ma niewielkie rozmiary w wysokości 9 KB do 15 KB w przypadku podstawowych obsługi protokołów IP i UDP.</span><span class="sxs-lookup"><span data-stu-id="20d0b-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="20d0b-359">NetX Duo ma jedną z najbardziej kompleksowych sieci TCP/IP dla głęboko osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="20d0b-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="20d0b-360">Ta obsługa obejmuje następujące produkty dodatków:</span><span class="sxs-lookup"><span data-stu-id="20d0b-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="20d0b-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="20d0b-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="20d0b-362">Technologia zaawansowana</span><span class="sxs-lookup"><span data-stu-id="20d0b-362">Advanced technology</span></span>

<span data-ttu-id="20d0b-363">Azure RTO NetX Duo to zaawansowana technologia, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="20d0b-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="20d0b-364">Architektura™ Piconet</span><span class="sxs-lookup"><span data-stu-id="20d0b-364">Piconet™ architecture</span></span>
* <span data-ttu-id="20d0b-365">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="20d0b-365">Automatic scaling</span></span>
* <span data-ttu-id="20d0b-366">™ Fast-Path technologii UDP</span><span class="sxs-lookup"><span data-stu-id="20d0b-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="20d0b-367">Elastyczne zarządzanie pakietami</span><span class="sxs-lookup"><span data-stu-id="20d0b-367">Flexible packet management</span></span>
* <span data-ttu-id="20d0b-368">Interfejs API kopiowania i implementacja protokołu zero</span><span class="sxs-lookup"><span data-stu-id="20d0b-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="20d0b-369">Obsługa wieloadresowa</span><span class="sxs-lookup"><span data-stu-id="20d0b-369">Multihomed support</span></span>
* <span data-ttu-id="20d0b-370">Opcjonalny limit czasu dla wszystkich zawieszeń</span><span class="sxs-lookup"><span data-stu-id="20d0b-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="20d0b-371">Obsługa routingu statycznego</span><span class="sxs-lookup"><span data-stu-id="20d0b-371">Static routing support</span></span>
* <span data-ttu-id="20d0b-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="20d0b-372">IPsec</span></span>
* <span data-ttu-id="20d0b-373">PROTOKÓŁ SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="20d0b-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="20d0b-374">Obsługa analizy systemu Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="20d0b-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="20d0b-375">Najszybszy czas wprowadzenia na rynek</span><span class="sxs-lookup"><span data-stu-id="20d0b-375">Fastest time-to-market</span></span>

<span data-ttu-id="20d0b-376">Usługa Azure RTO NetX Duo jest łatwa do zainstalowania, uczenia, używania, debugowania, weryfikowania, certyfikowania i konserwowania.</span><span class="sxs-lookup"><span data-stu-id="20d0b-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="20d0b-377">W efekcie NetX Duo jest jednym z najpopularniejszych stosów TCP/IP dla osadzonych urządzeń IoT, w tym wielu SoC z Broadcom, Gainspan itd. Nasza spójna przedział czasu na rynek jest oparta na:</span><span class="sxs-lookup"><span data-stu-id="20d0b-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="20d0b-378">Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO NetX Duo](about-this-guide.md) i zapoznaj się z Tobą.</span><span class="sxs-lookup"><span data-stu-id="20d0b-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="20d0b-379">Ukończ dostępność kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="20d0b-379">Complete source code availability</span></span>
* <span data-ttu-id="20d0b-380">Łatwy w użyciu interfejs API</span><span class="sxs-lookup"><span data-stu-id="20d0b-380">Easy-to-use API</span></span>
* <span data-ttu-id="20d0b-381">Kompleksowy i zaawansowany zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="20d0b-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="20d0b-382">Jedna prosta licencja</span><span class="sxs-lookup"><span data-stu-id="20d0b-382">One Simple License</span></span>

<span data-ttu-id="20d0b-383">Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.</span><span class="sxs-lookup"><span data-stu-id="20d0b-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="20d0b-384">Pełny kod źródłowy o najwyższej jakości</span><span class="sxs-lookup"><span data-stu-id="20d0b-384">Full, highest-quality source code</span></span>

<span data-ttu-id="20d0b-385">W ciągu lat kod źródłowy usługi Azure RTO NetX Duo ustawił na pasku jakość i łatwość interpretacji.</span><span class="sxs-lookup"><span data-stu-id="20d0b-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="20d0b-386">Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.</span><span class="sxs-lookup"><span data-stu-id="20d0b-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="20d0b-387">Obsługuje najpopularniejsze architektury</span><span class="sxs-lookup"><span data-stu-id="20d0b-387">Supports most popular architectures</span></span>

<span data-ttu-id="20d0b-388">Usługa Azure RTO NetX Duo działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, z uwzględnieniem następujących architektur zaawansowanych:</span><span class="sxs-lookup"><span data-stu-id="20d0b-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="20d0b-389">**Urządzenia analogowe**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="20d0b-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="20d0b-390">**Andes rdzeń**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="20d0b-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="20d0b-391">**Ambiqmicro**: Pollo MCUs</span><span class="sxs-lookup"><span data-stu-id="20d0b-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="20d0b-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="20d0b-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="20d0b-393">**Erze**: Xtensa, romb</span><span class="sxs-lookup"><span data-stu-id="20d0b-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="20d0b-394">**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="20d0b-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="20d0b-395">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="20d0b-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="20d0b-396">**EnSilica**: ESI-RISC</span><span class="sxs-lookup"><span data-stu-id="20d0b-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="20d0b-397">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="20d0b-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="20d0b-398">**Intel & Intel FPGA**: X36/Pentium, XScale, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="20d0b-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="20d0b-399">**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="20d0b-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="20d0b-400">**Mikrośrednik**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="20d0b-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="20d0b-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="20d0b-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="20d0b-402">**Renesas**: sh, HS, V850, RX, rz, synergia</span><span class="sxs-lookup"><span data-stu-id="20d0b-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="20d0b-403">**Krzem** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="20d0b-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="20d0b-404">**SynopSYS**: Arc 600, 700, łuk em, łuk HS</span><span class="sxs-lookup"><span data-stu-id="20d0b-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="20d0b-405">**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="20d0b-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="20d0b-406">**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="20d0b-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="20d0b-407">**Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="20d0b-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="20d0b-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="20d0b-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="20d0b-409">*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacunkami i mogą być inne na platformie deweloperskiej.*</span><span class="sxs-lookup"><span data-stu-id="20d0b-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="20d0b-410">Powiązane usługi</span><span class="sxs-lookup"><span data-stu-id="20d0b-410">Related services</span></span>

<span data-ttu-id="20d0b-411">Azure Security Center dla modułu zabezpieczeń IoT RTO to kompleksowe rozwiązanie zabezpieczeń dla urządzeń RTO platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="20d0b-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="20d0b-412">Moduł zabezpieczeń usługi Azure RTO oferuje złośliwe Wykrywanie aktywności sieciowej, niestandardowe zachowanie urządzenia oparte na alertach określania poziomu odniesienia i pomaga w ulepszaniu higieny bezpieczeństwa urządzeń.</span><span class="sxs-lookup"><span data-stu-id="20d0b-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="20d0b-413">Dowiedz się więcej na temat [modułu zabezpieczeń platformy Azure RTO](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) lub zacznij korzystać z przewodnika [konfigurowania modułu zabezpieczeń dla usługi Azure RTO](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) .</span><span class="sxs-lookup"><span data-stu-id="20d0b-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="20d0b-414">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="20d0b-414">Next steps</span></span>

<span data-ttu-id="20d0b-415">Aby dowiedzieć się więcej o NetX Duo, Zacznij od [podręcznika użytkownika platformy Azure RTO NetX](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="20d0b-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
