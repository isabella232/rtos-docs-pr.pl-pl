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
# <a name="overview-of-azure-rtos-netx-duo"></a>Omówienie Azure RTOS NetX Duo

Azure RTOS NetX Duo osadzony stos sieciowy TCP/IP to zaawansowany stos sieciowy TCP/IP klasy przemysłowej firmy Microsoft, podwójny stos sieciowy IPv4 i IPv6 TCP/IP zaprojektowany specjalnie z myślą o aplikacjach osadzonych, w czasie rzeczywistym i aplikacjach IoT. NetX Duo zapewnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, IPv6, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu. Azure RTOS NetX Duo oferuje zabezpieczenia za pośrednictwem dodatkowych produktów zabezpieczających, takich jak Azure RTOS NetX Secure IPsec i Azure RTOS NetX Secure SSL/TLS/DTLS. Wszystko to w połączeniu z niewielkim zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawiają, że Azure RTOS NetX Duo jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="mqtt"></a>MQTT

* Transport telemetrii kolejki komunikatów (MQTT)
* Minimalna 2,7 KB pamięci FLASH

### <a name="auto-ip"></a>Automatyczny adres IP

* Automatyczne przypisywanie adresów IPv4
* Minimalna 1,2 KB, 300 bajtów pamięci RAM

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* Protokół HTTP (Hypertext Transfer Protocol)
* Minimalna 2,8 KB do 4,8 KB pamięci FLASH / od 0,4 KB do 1,0 KB pamięci RAM
* Obsługa klientów i serwerów

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* Protokół HTTP (Hypertext Transfer Protocol)
* Minimalna ilość pamięci FLASH od 3,0 KB do 9,5 KB / od 0,5 KB do 2 KB pamięci RAM
* Obsługa klientów i serwerów
* Wiele przychodzących sesji klientów
* Zwykły tekst i zaszyfrowany protokół HTTPS
* Obsługa połączeń trwałych
* Przekazywanie plików wieloczęściowych
* W pełni zintegrowane z Azure RTOS NetX Secure TLS

### <a name="smtp"></a>SMTP

* Simple Transfer Protocol (SMTP)
* Minimalnie 4,1 KB i 0,6 KB pamięci RAM
* Obsługa klienta

### <a name="dhcp"></a>DHCP

* Protokół DHCP
* Minimalna ilość pamięci FLASH od 3,6 KB do 4,6 KB, 2,7 KB pamięci RAM
* Obsługa klientów i serwerów
* Obsługa protokołu IPv4 i IPv6

### <a name="nat"></a>NAT

* Translator adresów sieciowych (NAT)
* Minimalnie 3,5 K6 i 0,6 KB pamięci RAM
* Obsługa adresów IPv4
* NaT jest dostępny tylko w Azure RTOS NetX Duo

### <a name="snmp"></a>SNMP

* Protokół SNMP (Simple Network Management Protocol)
* Minimalna 10,9 KB i 2,6 KB pamięci RAM
* Obsługa agentów dla wersji VI, V2 i V3

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* System nazw domen (DNS)
* Multiemisja systemu nazw domen (mDNS)
* Odnajdywanie usług oparte na systemie DNS (DNS-SD)
* DNS Minimalnie od 2,4 KB do 3 KB pamięci FLASH, 1 KB pamięci RAM
* Obsługa klientów
* Serwery mDNS i DNS-SD są dostępne tylko w Azure RTOS NetX Duo

### <a name="p0p3"></a>P0P3

* Protokół POST Office w wersji 3 (POP3)
* Minimalnie 8,1 KB i 1,4 KB pamięci RAM
* Obsługa klientów

### <a name="telnet"></a>Telnet

* Minimalnie 0,5 KB i 0,3 KB pamięci RAM
* Obsługa klientów i serwerów
* Intuicyjne interfejsy API Telnet: *nx_telnet_ \**

### <a name="ftp-tftp"></a>FTP, TFTP

* protokół transferu plików (FTP)
* Protokół TFTP (Trivial File Transfer Protocol)
* MINIMALNA PAMIĘĆ FLASH FTP od 1,8 KB do 7,2 KB, od 0,6 KB do 2,1 KB pamięci RAM
* TFTP minimalnie od 1,7 KB do 2,4 KB pamięci FLASH, od 0,3 KB do 1,8 KB pamięci RAM
* Obsługa klientów i serwerów
* Intuicyjne interfejsy API FTP i TFTP: *nx_ftp_ \** lub *nx_tftp_ \**

### <a name="ppp-pppoe"></a>PPP, PPPoE

* Polnt-to-PoInt Protocol (PPP)
* Point-to-Point Protocol przez Ethernet (PPPoE)
* Minimalnie 7,1 KB i 3,8 KB pamięci RAM
* Intuicyjne interfejsy API PPP: *nx_ppp_ \**

* PpPoE jest dostępne tylko w Azure RTOS NetX Duo

### <a name="sntp"></a>SNTP

* Simple Network Time Protocol (SNTP)
* Minimalna 4 KB i 0,5 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API SNTP: *nx_sntp_ \**

### <a name="azure-rtos-netx-duo-api"></a>Azure RTOS NetX Duo API

* Intuicyjny i spójny interfejs API
* Konwencja nazewnictwa rzeczowników
* Szybka implementacja interfejsu API bez kopiowania
* Wszystkie interfejsy API mają wiodące <i>nx_*</i> do łatwego identyfikowania jako Azure RTOS NetX
* Interfejsy API blokowania mają opcjonalny limit czasu wątku
* Aby [uzyskać więcej Azure RTOS, zobacz podręcznik użytkownika](about-this-guide.md) aplikacji NetX Duo
* Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda

### <a name="igmp"></a>Igmp

* Protokół IGMP (Internet Group Management Protocol)
* Minimalna pamięć FLASH 2,5 KB
* Obsługa grup multiemisji IPv4
* Zweryfikowane przez IxANVL IXANVL
* Opcjonalne statystyki IGMP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS ThreadX
* Intuicyjne interfejsy API IGMP: *nx_igmp_ \**

### <a name="azure-rtos-netx-secure-dtls"></a>Azure RTOS NetX Secure DTLS

* Datagram Transport Layer Security (DTLS) 1.0 i 1.2
* Minimalna 11 KB pamięci FLASH
* Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz
* Uproszczona implementacja X.509
* W pełni zintegrowane z Azure RTOS NetX Duo UDP
* Sprzętowa obsługa kryptografii
* Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521
* Obsługa zaszyfrowanych kluczy (zależna od sprzętu)

### <a name="azure-rtos-netx-secure-tls"></a>Azure RTOS NetX Secure TLS

* Transport Layer Security (TLS) 1.0, 1.1 i 1.2
* Minimalna 8,8 KB pamięci FLASH
* Szybki, programowy 2048-bitowy rozmiar klucza RSA ok. 1 sekundy @120MHz
* Uproszczona implementacja X.509
* W pełni zintegrowane z Azure RTOS TCP NetX Duo
* Sprzętowa obsługa kryptografii
* Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywanie) i ECDH (szyfrowanie), w tym krzywe P 192/224/256/384/521
* Obsługa zaszyfrowanych kluczy (zależna od sprzętu)

### <a name="icmp"></a>ICMP

* Protokół ICMP (Internet Control Message Protocol)
* Minimalna pamięć FLASH 2,5 KB
* Obsługa protokołu IPv4 i IPv6
* Zweryfikowane przez IxANVL IXANVL
* Żądanie ping i odpowiedź ping
* Opcjonalne zawieszenie wątku na żądaniach ping
* Opcjonalny limit czasu dla całego zawieszenia
* Opcjonalne statystyki ICMP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
* Intuicyjne interfejsy API ICMP: *nx_icmp_ \**

### <a name="udp"></a>UDP

* Protokół UDP (User Datagram Protocol)
* Minimalna pamięć FLASH 2,5 KB, 124 gniazda w bajtach pamięci RAM na gniazdo
* Szybkie przetwarzanie pakietów TCP w pobliżu wire speed:
    * RX 95 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 14% wykorzystanie MIKROU
    * TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 10% wykorzystanie MIKROU
* Szybka ścieżka UDP™ technologia
* Brak limitów liczby protokołu UDP
* Zweryfikowane przez IxANVL IxANVL
* Opcjonalne zawieszenie podczas odbierania gniazda
* Opcjonalny limit czasu dla całego zawieszenia
* Opcjonalne statystyki UDP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
* Intuicyjne interfejsy API UDP: *nx_udp_ \**

### <a name="tcp"></a>TCP

* Transmission Control Protocol (TCP)
* Minimalnie od 10,5 KB do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo
* Szybkie, prawie wlre speed przetwarzanie pakietów TCP:
    * Rx 93 Mb/s na Ethernet 100 Mb/s, @100MHz MIKROU, 20% wykorzystanie MIKROU
    * TX 94 Mb/s przy 100 Mb/s Ethernet, @100MHz MIKROU, 27% wykorzystanie mikrojądek
* Niezawodne połączenie
* Brak limitów liczby gniazd TCP
* Zweryfikowane przez IxANVL IxANVL
* Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda
* Opcjonalny limit czasu dla całego zawieszenia
* Opcjonalne statystyki TCP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
* Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**

### <a name="arprarp"></a>ARP/RARP

* Protokół rozpoznawania adresów (ARP)
* Protokół RARP (Reverse Address Resolution Protocol)
* Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM
* Dynamiczna rozdzielczość 32-blt adresów IPv4 i 48 blt adresów MAC
* Zweryfikowane przez IxANVL IXANVL
* Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP
* Obsługa dużych ARP
* Opcjonalne statystyki ARP/RARP określone przez aplikację
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
* Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *\* nx_rarp_*

### <a name="ipv4-amp-ipv6"></a>Protokół &amp; IPv6 protokołu IPv4

* Protokół internetowy (IP)
* Minimalna ilość pamięci FLASH od 3,5 KB do 8,5 KB, od 2 KB do 3 KB pamięci RAM
* Piconet™ architektura
* Szybka wydajność prawie z wire speed
* Obsługa wielu interfejsów
* Obsługa wielunadresowych
* Obsługa routingu statycznego
* Obsługa fragmentacji/ponownego zsadu ADRESÓW IP
* Obsługa adresów IPv4 i IPv6
* Zweryfikowane przez IxANVL IxANVL
* Certyfikacja gotowego logo IPv6 fazy II
* Opcjonalne statystyki adresów IP
* Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
* Intuicyjne interfejsy API warstwy IP: *nx_ip_, \** *\** *\** nxd_ip_, nxd_ipv6_
* Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304, klasa C, ISO 26262 ASIL D i EN 50128 SW-SIL4

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure RTOS NetX Secure IPSEC

* Zabezpieczenia protokołu internetowego (IPSEC)
* Warstwa IP
* Sprzętowa obsługa kryptografii
* Obsługa kryptografii oprogramowania, w tym:
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* Internet Key Exchange (IKE) w wersji 2
* Intuicyjne interfejsy API protokołu IPsec: *nx_ipsec_ \**
* IPsec jest dostępne tylko w Azure RTOS NetX Duo

## <a name="safe-and-secure"></a>Bezpieczne i bezpieczne

Azure RTOS NetX Duo jest bezpieczne. Zabezpieczenia te są udostępniane za pośrednictwem produktów zabezpieczeń dodatków, w tym protokołu IPsec, protokołu SSL, protokołu TLS i protokołu DTLS. Ponadto aplikacja ma pełną kontrolę nad całym dostępem zewnętrznym do aplikacji Azure RTOS NetX Duo, co znacznie ułatwia określanie ryzyka bezpieczeństwa.

Microsoft Azure RTOS zapewnia producentom OEM składniki do zabezpieczania komunikacji oraz tworzenia izolacji kodu i danych przy użyciu podstawowych mechanizmów ochrony sprzętowej MCU/MPU. Konstruktor urządzenia ostatecznie odpowiada za zapewnienie, że urządzenie w pełni spełnia zmieniające się wymagania dotyczące zabezpieczeń związane z konkretnym przypadekem użycia.


## <a name="interoperability-verification"></a>Weryfikacja współdziałania

NetX Duo jest zgodny ze standardami RFC i oferuje pełne współdziałanie z urządzeniami dla większości dostawców.

![Logo gotowe do użycia IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo jest jednym z jedynych osadzonych stosów TCP/IP do osiągnięcia rygorystycznego certyfikatu IPv6-Ready Logo, dowodu na to, że przeszedł testy zgodności i współdziałania, administrowane i weryfikowane przez forum IPv6. NetX Duo korzysta również ze standardu branżowego IxANVL (Automated Network Validation Library) do implementacji podstawowego protokołu TCP/IP NetX Duo.

## <a name="comprehensive-iot-solution"></a>Kompleksowe rozwiązanie IoT

NetX Duo ma jedną z najbardziej kompleksowych sieci TCP/IP dla głęboko osadzonych aplikacji IoT. Ta obsługa obejmuje następujące produkty protokołu dodatku.

MQTT, CoAP, SMTPM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>Zaawansowana technologia

Azure RTOS NetX Duo to zaawansowana technologia, która obejmuje:

* Piconet™ architektura
* Automatyczne skalowanie
* Technologia Fast-Path UDP™
* Elastyczne zarządzanie pakietami
* Interfejs API bez kopiowania i implementacja
* Obsługa wielunadresowych
* Opcjonalny limit czasu dla całego zawieszenia
* Obsługa routingu statycznego
* IPsec
* SSL/TLS/DTLS
* Azure RTOS analizy systemu TraceX

## <a name="related-services"></a>Powiązane usługi

Moduł Azure Security Center zabezpieczeń IoT RTOS zapewnia kompleksowe rozwiązanie zabezpieczeń dla Azure RTOS mobilnych. Moduł zabezpieczeń dla usługi Azure RTOS oferuje wykrywanie złośliwych działań sieciowych, dostosowywanie niestandardowego zachowania urządzenia opartego na alertach i pomaga zwiększyć higienę zabezpieczeń urządzeń. Dowiedz się więcej na temat [modułu zabezpieczeń](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) dla Azure RTOS lub rozpoczynanie pracy z konfigurowaniem modułu zabezpieczeń na Azure RTOS [Szybki](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) start.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat netx duo, zacznij od [podręcznika użytkownika Azure RTOS NetX Duo.](about-this-guide.md)
