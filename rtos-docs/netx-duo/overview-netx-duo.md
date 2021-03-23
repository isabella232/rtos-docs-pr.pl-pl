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
# <a name="overview-of-azure-rtos-netx-duo"></a>Omówienie usługi Azure RTO NetX Duo

Azure RTO NetX Duo — osadzony stos sieci TCP/IP jest zaawansowanym, przemysłowym stosem protokołów TCP/IP firmy Microsoft, który jest przeznaczony specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i dla IoT. NetX Duo oferuje aplikacje osadzone z podstawowymi protokołami sieciowymi, takimi jak IPv4, IPv6, TCP i UDP, a także kompletny pakiet dodatkowych protokołów dodatków o wyższym poziomie. Usługa Azure RTO NetX Duo oferuje zabezpieczenia za pośrednictwem dodatkowych produktów zabezpieczeń, w tym Azure RTO NetX Secure IPsec i Azure RTO NetX Secure SSL/TLS/DTLS. Wszystkie te połączone z małą ilością, szybkim wykonaniem i najbardziej łatwym w obsłużeniu, dzięki czemu usługa Azure RTO NetX Duo najlepiej sprawdza się w przypadku najbardziej wymagających osadzonych aplikacji IoT.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="mqtt"></a>MQTT

* Transport telemetrii kolejki komunikatów (MQTT)
* Minimum 2,7 KB
* Intuicyjne interfejsy API MQTT: *nx_mqtt_*\*

### <a name="auto-ip"></a>Adres IP

* Automatyczne przypisywanie adresów IPv4
* Minimalny 1,2 KB, 300 bajtów pamięci RAM
* Intuicyjne interfejsy API AutoIP: *nx_autoip_ \**

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1,0

* Protokół HTTP (Hypertext Transfer Protocol)
* Minimum 2,8 KB do 4,8 KB FLASH/0,4 KB do 1,0 KB pamięci RAM
* Obsługa klienta i serwera
* Intuicyjne interfejsy API: *nx_http_ \**

#### <a name="httphttps-11"></a>HTTP/HTTPS 1,1

* Protokół HTTP (Hypertext Transfer Protocol)
* Minimum 3,0 KB do 9,5 KB FLASH/0,5 KB do 2 KB pamięci RAM
* Obsługa klienta i serwera
* Wiele przychodzących sesji klienta
* Zwykły tekst i szyfrowany protokół HTTPS
* Obsługa połączeń trwałych
* Przekazywanie wieloczęściowego pliku
* W pełni zintegrowana z usługą Azure RTO NetX Secure TLS
* Intuicyjne interfejsy API: *nx_web_http \**

### <a name="smtp"></a>SMTP

* Simple Pasażing Protocol (SMTP)
* Minimum 4,1 KB i 0,6 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API SMTP: *nx_smtp_ \**

### <a name="dhcp"></a>DHCP

* Protokół DHCP
* Minimum 3,6 KB do 4,6 KB FLASH, rozmiar pamięci RAM 2,7 KB
* Obsługa klienta i serwera
* Obsługa protokołów IPv4 i IPv6
* Intuicyjne interfejsy API DHCP: *nx_dhcp_ \**

### <a name="nat"></a>NAT

* Translator adresów sieciowych (NAT)
* Minimalne rozmiary pamięci RAM: 3,5 K6 i 0,6 KB
* Obsługa adresów IPv4
* Intuicyjne interfejsy API translatora adresów sieciowych: *nx_nat_ \**
* Translator adresów sieciowych jest dostępny tylko w przypadku platformy Azure RTO NetX Duo

### <a name="snmp"></a>SNMP

* Protokół SNMP (Simple Network Management Protocol)
* Minimum 10,9 KB i 2,6 KB pamięci RAM
* Obsługa agentów dla VI, v2 i V3
* Intuicyjne interfejsy API protokołu SNMP: *nx_snmp_ \**

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* System nazw domen (DNS)
* System nazw domen multiemisji (mDNS)
* Odnajdowanie usług oparte na systemie DNS (DNS-SD)
* Minimalna 2,4 KB do 3 KB, pojemność pamięci RAM: 1 KB
* Obsługa klienta
* Intuicyjne interfejsy API: *nx_dns_ \**
* usługi mDNS i DNS-SD są dostępne tylko w usłudze Azure RTO NetX Duo

### <a name="p0p3"></a>P0P3

* Post Office Protocol w wersji 3 (POP3)
* Minimum 8,1 KB i 1,4 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API P0P3: *nx_pop3_ \**

### <a name="telnet"></a>Program

* Minimum 0,5 KB i 0,3 KB pamięci RAM
* Obsługa klienta i serwera
* Intuicyjne interfejsy API programu Telnet: *nx_telnet_ \**

### <a name="ftp-tftp"></a>FTP, TFTP

* Protokół transferu plików (FTP)
* Protokół TFTP (Trivial File Transfer Protocol)
* FTP minimum 1,8 KB do 7,2 KB FLASH, 0,6 KB do 2,1 KB pamięci RAM
* TFTP minimum 1,7 KB do 2,4 KB FLASH, 0,3 KB do 1,8 KB pamięci RAM
* Obsługa klienta i serwera
* Intuicyjne interfejsy API FTP i TFTP: *nx_ftp_ \** lub *nx_tftp_ \**

### <a name="ppp-pppoe"></a>PPP, PPPoE

* Polnt-to-PoInt Protocol (PPP)
* Point-to-Point Protocol przez sieć Ethernet (PPPoE)
* Minimum 7,1 KB i 3,8 KB pamięci RAM
* Intuicyjne interfejsy API protokołu PPP: *nx_ppp_ \**

* Protokół PPPoE jest dostępny tylko w przypadku platformy Azure RTO NetX Duo

### <a name="sntp"></a>SNTP

* Simple Network Time Protocol (SNTP)
* Minimalna 4 KB i 0,5 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API SNTP: *nx_sntp_ \**

### <a name="azure-rtos-netx-duo-api"></a>Interfejs API usługi Azure RTO NetX Duo

* Intuicyjny i spójny interfejs API
* W konwencji nazewnictwa czasowników
* Szybka, zerowa — implementacja interfejsu API
* Wszystkie interfejsy API mają wiodące <i>nx_ *</i> do łatwej identyfikacji jako Azure RTO NetX
* Blokowanie interfejsów API ma opcjonalny limit czasu wątku
* Aby uzyskać więcej informacji, zobacz [Podręcznik użytkownika usługi Azure RTO NetX Duo](about-this-guide.md) .
* Opcjonalna warstwa BSD do przenoszenia kodu gniazda starszej wersji

### <a name="igmp"></a>IGMP

* Protokół IGMP (Internet Group Management Protocol)
* Minimum 2,5 KB
* Obsługa grup multiemisji IPv4
* Zweryfikowano IXIA IxANVL
* Opcjonalne statystyki IGMP
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO ThreadX
* Intuicyjne interfejsy API protokołu IGMP: *nx_igmp_ \**

### <a name="azure-rtos-netx-secure-dtls"></a>Usługa Azure RTO NetX Secure DTLS

* Datagram Transport Layer Security (DTLS) 1,0 i 1,2
* Minimum 11 KB
* Fast, RSA 2048-bitowy rozmiar klucza ~ 1 sekunda @120MHz
* Ulepszona implementacja X. 509
* W pełni zintegrowane z usługą Azure RTO NetX Duo UDP Sockets
* Obsługa kryptografii sprzętowej
* Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywaniem) i ECDH (szyfrowanie), w tym P-krzywe 192/224/256/384/521
* Obsługa zaszyfrowanych kluczy (zależnych od sprzętu)

### <a name="azure-rtos-netx-secure-tls"></a>Azure RTO NetX Secure TLS

* Transport Layer Security (TLS) 1,0, 1,1 i 1,2
* Minimum 8,8 KB
* Fast, RSA 2048-bitowy rozmiar klucza ~ 1 sekunda @120MHz
* Ulepszona implementacja X. 509
* W pełni zintegrowane z usługą Azure RTO NetX Duo TCP Sockets
* Obsługa kryptografii sprzętowej
* Obsługa kryptografii oprogramowania: RSA (wszystkie rozmiary kluczy), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Kryptografia krzywej eliptycznej (ECC) z ECDSA (podpisywaniem) i ECDH (szyfrowanie), w tym P-krzywe 192/224/256/384/521
* Obsługa zaszyfrowanych kluczy (zależnych od sprzętu)

### <a name="icmp"></a>ICMP

* Protokół ICMP (Internet Control Message Protocol)
* Minimum 2,5 KB
* Obsługa protokołów IPv4 i IPv6
* Zweryfikowano IXIA IxANVL
* Żądanie ping i odpowiedź ping
* Opcjonalne zawieszenie wątku w żądaniach ping
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Opcjonalne statystyki protokołu ICMP
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API protokołu ICMP: *nx_icmp_ \**

### <a name="udp"></a>UDP

* User Datagram Protocol (UDP)
* Minimalny 2,5 KB, 124 gniazd bajtów pamięci RAM na gniazdo
* Szybkie przetwarzanie pakietów TCP w bliskiej WireSpeed:
    * Odbieranie 95 MB/s na 100 MB/s, MIKROKONTROLERY @100MHz , 14% mikrokontrolery
    * TX 94 MB/s w dniu 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 10% mikrokontrolery
* Szybka ścieżka UDP™ technologia
* Brak limitów liczby UDP
* Zweryfikowano IXIA IxANVL
* Opcjonalne zawieszenie dla odbioru gniazda
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Opcjonalne statystyki protokołu UDP
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API protokołu UDP: *nx_udp_ \**

### <a name="tcp"></a>TCP

* Transmission Control Protocol (TCP)
* Minimalna 10,5 K8 do 12,5 KB FLASH, 280 bajtów pamięci RAM na gniazdo
* Szybkie przetwarzanie pakietów TCP w bliskiej wlrespeed:
    * Odbieranie 93 MB/s na 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 20% mikrokontrolery
    * TX 94 MB/s w dniu 100 MB/s Ethernet, MIKROKONTROLERY @100MHz , 27% mikrokontrolery
* Niezawodne połączenie
* Brak limitów liczby gniazd TCP
* Zweryfikowano IXIA IxANVL
* Opcjonalne zawieszenie dla odbioru i wysyłania gniazd
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Opcjonalne statystyki TCP
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API protokołu TCP: *nx_tcp_ \**

### <a name="arprarp"></a>ARP/RARP

* Protokół ARP (Address Resolution Protocol)
* Protokół odwrotnego rozpoznawania adresów (RARP)
* Minimum 1,7 KB, rozmiar pamięci RAM
* Dynamiczne rozpoznawanie 32 BLT IPv4 i 48-BLT adresów MAC
* Zweryfikowano IXIA IxANVL
* Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP
* Obsługa klienta w usłudze ARP
* Opcjonalna Statystyka ARP/RARP określona przez aplikację
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *nx_rarp_ \**

### <a name="ipv4-amp-ipv6"></a>IPv4 &amp; IPv6

* Protokół internetowy (IP)
* Minimum 3,5 KB do 8,5 KB FLASH, Powierzchnia 2 KB do 3 KB pamięci RAM
* Architektura™ Piconet
* Szybka, prawie wirespeeda wydajność
* Obsługa wielu interfejsów
* Obsługa wieloadresowa
* Obsługa routingu statycznego
* Obsługa fragmentacji/odzestawów IP
* Obsługa adresów IPv4 i IPv6
* Zweryfikowano IXIA IxANVL
* Certyfikacja logo gotowej do fazy II IPv6
* Opcjonalne statystyki adresów IP
* Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API warstwy IP: *\* nx_ip_*, *nxd_ip_ \**, *nxd_ipv6_ \**
* Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D i EN 50128 SW-SIL4

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure RTO NetX Secure IPSEC

* Zabezpieczenia protokołu internetowego (IPSEC)
* Warstwa IP
* Obsługa kryptografii sprzętowej
* Obsługa kryptografii oprogramowania, w tym:
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* Obsługa usługi Internet Key Exchange (IKE) w wersji 2
* Intuicyjne interfejsy API protokołu IPsec: *nx_ipsec_ \**
* Protokół IPsec jest dostępny tylko w przypadku platformy Azure RTO NetX Duo

## <a name="small-footprint"></a>Niewielkie rozmiary

Usługa Azure RTO NetX Duo ma niewielkie rozmiary w wysokości 9 KB do 15 KB w przypadku podstawowych obsługi protokołów IP i UDP. Do obsługi funkcji TCP jest wymagana dodatkowa ilość pamięci o wartości 10 KB do 13 KB. Użycie pamięci RAM usługi Azure RTO NetX Duo zazwyczaj mieści się w zakresie od 2,6 KB do 3,6 KB oraz pamięci puli pakietów zdefiniowanej przez aplikację. Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar platformy Azure RTO NetX Duo jest automatycznie skalowany w oparciu o usługi używane przez aplikację. To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.

## <a name="fast-execution"></a>Szybkie wykonywanie

Usługa Azure RTO NetX Duo oferuje implementację typu "wysyłanie i odbieranie pakietów o zerowej kopii", które są wysoce zintegrowane z platformą Azure RTO ThreadX, aby osiągnąć największą możliwą wydajność. Na przykład usługa Azure RTO NetX Duo może zazwyczaj osiągnąć niemal WireSpeed transferów danych na procesorze 80 MHz (lub mniej), jednocześnie używając tylko niewielkiej części cykli procesora.

## <a name="simple-easy-to-use"></a>Proste i łatwe w użyciu

Interfejs API usługi Azure RTO NetX Duo jest intuicyjny, prosty i wysoce funkcjonalny.

Nazwy interfejsów API są prawdziwe mówiące i nie są nazwami "zup alfabetu" ani o dużej liczbie skróconych, które są często używane w innych produktach sieciowych. Wszystkie interfejsy API usługi Azure RTO NetX Duo mają wiodące *nx_* i są zgodne z konwencją nazewnictwa czasowników. Ponadto istnieje spójność funkcjonalna w całym interfejsie API. Na przykład wszystkie funkcje interfejsu API, które zawieszają, mają opcjonalny limit czasu, który działa w taki sam sposób.

W przypadku starszych aplikacji usługa Azure RTO NetX Duo oferuje dodatkową warstwę zgodną z gniazdem BSD. Ta warstwa ułatwia deweloperom łatwe Migrowanie dużych aplikacji sieciowych.

## <a name="safe-and-secure"></a>Bezpieczne i bezpieczne

Usługa Azure RTO NetX Duo jest bezpieczna. Zabezpieczenia te są udostępniane za pośrednictwem produktów zabezpieczeń dodatku, takich jak IPsec, SSL, TLS i DTLS. Ponadto aplikacja ma pełną kontrolę nad całym dostępem zewnętrznym do usługi Azure RTO NetX Duo, co znacznie ułatwia określanie zagrożeń bezpieczeństwa.

Microsoft Azure RTO udostępnia producentom OEM składniki do zabezpieczania komunikacji i tworzenia izolacji kodu i danych przy użyciu podstawowych mechanizmów ochrony sprzętu MIKROKONTROLERY/MPU. W celu zapewnienia, że urządzenie jest w pełni zgodne z rozwijającymi się wymaganiami dotyczącymi bezpieczeństwa związanymi z konkretnym przypadkiem użycia, jest obowiązkiem konstruktora urządzeń.

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Wstępnie certyfikowane przez TUV i UL do wielu standardów bezpieczeństwa

Usługa Azure RTO NetX Duo została certyfikowana przez moimi-TUV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-62304, Klasa bezpieczeństwa SW, ISO 26262 ASIL D i EN 50128. Certyfikat potwierdza, że usługa Azure RTO NetX Duo może zostać użyta w przypadku rozwoju oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności zabezpieczeń IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, weryfikowania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508, a także wszystkie standardy, które są od niego pochodzące, w tym IEC-62304, ISO 26262 i EN 50128, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="MOIMI — certyfikat TUV":::

Usługa Azure RTO NetX Duo została rozpoznana przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku h, CSA E60730-1 załącznik H, IEC 60730-1 w załączniku H, UL 60335-1 Załącznik R, IEC 60335-1, załącznik R i standardy bezpieczeństwa UL 1998 dla oprogramowania w składnikach programowalnych. UL to globalna, niezależna firma zajmująca się ochroną bezpieczeństwa, która ma więcej niż wiek fachowych rozwiązań w zakresie bezpieczeństwa, od publicznego wdrożenia energii elektrycznej, aby nawiązać przełom w zakresie trwałości, odnawialnych energii i nanotechnologii.

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU certyfikat UL":::

Artefakty (certyfikat, Podręcznik bezpieczeństwa, raport testowy itp.) skojarzone z certyfikatami TUV i UL są dostępne do sprzedaży.

W przypadku, gdy aplikacja wymaga dodatkowej certyfikacji, usługa certyfikacji jest dostępna w firmie Microsoft w celu zapewnienia certyfikacji klucza dla różnych standardów przy użyciu rzeczywistej platformy sprzętowej, a nawet w odniesieniu do kodu aplikacji. Skontaktuj się z nami, aby uzyskać więcej informacji na temat naszej usługi certyfikacji.

## <a name="eal4-common-criteria-security-certification"></a>Criteria EAL4 + typowe kryteria certyfikacji zabezpieczeń

Usługa Azure RTO uzyskała certyfikaty zabezpieczeń Criteria EAL4 + Common kryteria. Obiekt docelowy evalution (TOE) obejmuje platformę Azure RTO ThreadX, Azure RTO NetX Duo, Azure RTO NetX Secure TLS i Azure RTO NetX MQTT. Reprezentuje to najbardziej typowe protokoły IoT wymagane przez głęboko osadzone czujniki, urządzenia, routery brzegowe i bramy.

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Certyfikat EAL":::

Funkcja oceny zabezpieczeń IT używana na potrzeby certyfikacji Microsoft Azure RTO SC Brightsight BV i urząd certyfikacji to SERTIT.

## <a name="fips-140-2-validated"></a>Sprawdzanie poprawności FIPS 140-2

Biblioteki kryptograficzne usługi Azure RTO NetX uzyskały certyfikat FIPS 140-2 140-2 dla oprogramowania, które określa wymagania dotyczące modułów kryptograficznych. Standard FIPS 140-2 wymaga, aby wszystkie federalne agencje rządowe i działy korzystające z zabezpieczeń opartych na kryptografii spełniały określone standardy dotyczące siły szyfrowania i możliwości. Te standardy zabezpieczeń oparte na kryptografii są również rozpoznawane w Kanadzie i Unii Europejskiej.

Laboratorium oceny zabezpieczeń informacji używane na potrzeby bibliotek kryptograficznych usługi Azure RTO NetX było atsec, a urząd certyfikacji to Narodowy Instytut standardów i technologii (NIST). Aby uzyskać dodatkowe informacje, przejrzyj [witrynę sieci Web NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) .

## <a name="interoperability-verification"></a>Weryfikacja współdziałania

NetX Duo jest zgodna ze standardami RFC i oferuje pełną współdziałanie z urządzeniami dla większości dostawców.

![Logo gotowe do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

Usługa Azure RTO NetX Duo to jeden z wbudowanych stosów TCP/IP, aby uzyskać rygorystyczne certyfikaty logo IPv6-Ready, dowód, że przeszedł zgodność i testy interoperacyjności, administrowane i zweryfikowane przez forum IPv6. NetX Duo wykorzystuje również standardową bibliotekę usługi IxANVL (zautomatyzowanej weryfikacji sieci) dla implementacji protokołu TCP/IP w programie NetX Duo.

## <a name="comprehensive-iot-solution"></a>Kompleksowe rozwiązanie IoT

Usługa Azure RTO NetX Duo ma niewielkie rozmiary w wysokości 9 KB do 15 KB w przypadku podstawowych obsługi protokołów IP i UDP. NetX Duo ma jedną z najbardziej kompleksowych sieci TCP/IP dla głęboko osadzonych aplikacji IoT. Ta obsługa obejmuje następujące produkty dodatków:

MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>Technologia zaawansowana

Azure RTO NetX Duo to zaawansowana technologia, która obejmuje:

* Architektura™ Piconet
* Automatyczne skalowanie
* ™ Fast-Path technologii UDP
* Elastyczne zarządzanie pakietami
* Interfejs API kopiowania i implementacja protokołu zero
* Obsługa wieloadresowa
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Obsługa routingu statycznego
* IPsec
* PROTOKÓŁ SSL/TLS/DTLS
* Obsługa analizy systemu Azure RTO TraceX

## <a name="fastest-time-to-market"></a>Najszybszy czas wprowadzenia na rynek

Usługa Azure RTO NetX Duo jest łatwa do zainstalowania, uczenia, używania, debugowania, weryfikowania, certyfikowania i konserwowania. W efekcie NetX Duo jest jednym z najpopularniejszych stosów TCP/IP dla osadzonych urządzeń IoT, w tym wielu SoC z Broadcom, Gainspan itd. Nasza spójna przedział czasu na rynek jest oparta na:

* Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO NetX Duo](about-this-guide.md) i zapoznaj się z Tobą.
* Ukończ dostępność kodu źródłowego
* Łatwy w użyciu interfejs API
* Kompleksowy i zaawansowany zestaw funkcji

## <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.

## <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy o najwyższej jakości

W ciągu lat kod źródłowy usługi Azure RTO NetX Duo ustawił na pasku jakość i łatwość interpretacji. Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.

## <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Usługa Azure RTO NetX Duo działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, z uwzględnieniem następujących architektur zaawansowanych:

**Urządzenia analogowe**: SHARC, Blackfin, CM4xx

**Andes rdzeń**: RISC-V

**Ambiqmicro**: Pollo MCUs

**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Erze**: Xtensa, romb

**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi

**Cypress**: RISC-V

**EnSilica**: ESI-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel & Intel FPGA**: X36/Pentium, XScale, Nios II, Cyclone, Arria 10

**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32

**Mikrośrednik**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: sh, HS, V850, RX, rz, synergia

**Krzem** Labs: EFM32

**SynopSYS**: Arc 600, 700, łuk em, łuk HS

**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C

**Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacunkami i mogą być inne na platformie deweloperskiej.*

## <a name="related-services"></a>Powiązane usługi

Azure Security Center dla modułu zabezpieczeń IoT RTO to kompleksowe rozwiązanie zabezpieczeń dla urządzeń RTO platformy Azure. Moduł zabezpieczeń usługi Azure RTO oferuje złośliwe Wykrywanie aktywności sieciowej, niestandardowe zachowanie urządzenia oparte na alertach określania poziomu odniesienia i pomaga w ulepszaniu higieny bezpieczeństwa urządzeń. Dowiedz się więcej na temat [modułu zabezpieczeń platformy Azure RTO](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) lub zacznij korzystać z przewodnika [konfigurowania modułu zabezpieczeń dla usługi Azure RTO](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) .

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o NetX Duo, Zacznij od [podręcznika użytkownika platformy Azure RTO NetX](about-this-guide.md).
