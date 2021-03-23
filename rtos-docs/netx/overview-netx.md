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
# <a name="overview-of-azure-rtos-netx"></a>Omówienie usługi Azure RTO NetX

Azure RTO NetX to stos sieciowy oparty na protokole TCP/IP IPv4 opartym na sieci, zaprojektowany specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i IoT. Azure RTO NetX to oryginalny stos sieci IPv4 firmy Microsoft i jest zasadniczo podzbiorem usługi Azure RTO. NetX udostępnia aplikacje osadzone z podstawowymi protokołami sieciowymi, takimi jak IPv4, TCP i UDP, a także kompletnym pakietem dodatkowych protokołów dodatków o wyższym poziomie. Niewielki wpływ, szybkie wykonywanie i doskonałe łatwość użycia sprawiają, że usługa Azure RTO NetX idealny wybór dla najbardziej wymagających osadzonych aplikacji IoT.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="telnet"></a>Program

* Minimum 0,5 KB i 0,3 KB pamięci RAM
* Obsługa klienta i serwera
* Intuicyjne interfejsy API programu Telnet: *nx_telnet_ \**

### <a name="auto-ip"></a>Adres IP

* Automatyczne przypisywanie adresów IPv4
* Minimalny 1,2 KB, 300 bajtów pamięci RAM
* Intuicyjne interfejsy API AutoIP: *nx_autoip_ \**

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP-Hypertext Transfer Protocol (HTTP)

* Minimalny 2,8 KB do 4,8 KBFLASH, 0,4 KB do 1,0 KB pamięci RAM
* Obsługa klienta i serwera
* Intuicyjne interfejsy API protokołu HTTP: *nx_http_ \**

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP — Simple Mail Transfer Protocol (SMTP)

* Minimum 4,1 KB i 0,6 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API SMTP: *nx_smtp_ \**

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP — Dynamic Host Configuration Protocol (DHCP)

* Minimum 3,6 KB do 4,6 KB FLASH, rozmiar pamięci RAM 2,7 KB
* Obsługa klienta i serwera
* Obsługa protokołu IPv4
* Intuicyjne interfejsy API DHCP: *nx_dhcp_ \**

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 — wersja 3 (POP3)

* Minimum 8,1 KB i 1,4 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API P0P3: *nx_pop3_ \**

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP-Simple Network Management Protocol (SNMP)

* Minimum 10,9 KB i 2,6 KB pamięci RAM
* Obsługa agentów dla VI, v2 i V3
* Intuicyjne interfejsy API protokołu SNMP: *nx_snmp_ \**

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP-protokół transferu plików (FTP), Trivial File Transfer Protocol (TFTP)

* FTP minimum 1,8 KB do 7.2 KBFLASH, 0,6 KB do 2,1 KB pamięci RAM
* TFTP minimum 1,7 KB do 2.4 KBFLASH, 0,3 KB do 1,8 KB pamięci RAM
* Obsługa klienta i serwera
* Intuicyjne interfejsy API FTP i TFTP: <i>nx_ftp_ *</i> lub <i>nx_tftp_*</i>

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP-Polnt-to-PoInt Protocol (PPP)

* Minimum 7,1 KB i 3,8 KB pamięci RAM
* Intuicyjne interfejsy API protokołu PPP: *nx_ppp_ \**

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP — Simple Network Time Protocol (SNTP)

* Minimalna 4 KB i 0,5 KB pamięci RAM
* Obsługa klienta
* Intuicyjne interfejsy API SNTP: *nx_sntp_ \**

### <a name="azure-rtos-netx-api"></a>Interfejs API usługi Azure RTO NetX

* Intuicyjny i spójny interfejs API
* W konwencji nazewnictwa czasowników
* Szybka, zerowa — implementacja interfejsu API
* Wszystkie funkcje interfejsu API mają wiodące <i>nx_ *</i> do łatwej identyfikacji jako Azure RTO NetX
* Blokowanie funkcji interfejsu API ma opcjonalny limit czasu wątku
* Opcjonalna warstwa BSD do przenoszenia kodu gniazda starszej wersji

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP — protokół IGMP (Internet Group Management Protocol)

* Minimum 2,5 KB
* Obsługa grup multiemisji IPv4
* Zweryfikowano IXIA IxANVL
* Opcjonalne statystyki IGMP
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API protokołu IGMP: *nx_igmp_ \**

### <a name="udp---user-datagram-protocol-udp"></a>UDP-User Datagram Protocol (UDP)

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

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP-Transmission Control Protocol (TCP)

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

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP — protokół ICMP (Internet Control Message Protocol)

* Minimum 2,5 KB
* Obsługa protokołu IPv4
* Zweryfikowano IXIA IxANVL
* Żądanie ping i odpowiedź ping
* Opcjonalne zawieszenie wątku w żądaniach ping
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Opcjonalne statystyki protokołu ICMP
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API protokołu ICMP: *nx_icmp_ \**

### <a name="ipv4---internet-protocol-ip"></a>IPv4 — protokół internetowy (IP)

* Minimum 3,5 KB do 8,5 KB FLASH, Powierzchnia 2 KB do 3 KB pamięci RAM
* Architektura™ Piconet
* Szybka, prawie wirespeeda wydajność
* Obsługa wielu interfejsów
* Obsługa wieloadresowa
* Obsługa routingu statycznego
* Obsługa fragmentacji/odzestawów IP
* Obsługa protokołu IPv4
* Zweryfikowano IXIA IxANVL
* Certyfikacja logo gotowego do fazy II
* Opcjonalne statystyki adresów IP
* Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API warstwy IP: *nx_ip_ \**, *nxd_ip_ \**
* Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D i EN 50128 SW-SIL4

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP — Protokół rozpoznawania adresów (ARP), odwrotny Protokół rozpoznawania adresów (RARP)

* Minimum 1,7 KB, rozmiar pamięci RAM
* Dynamiczne rozpoznawanie 32 BLT IPv4 i 48-BLT adresów MAC
* Zweryfikowano IXIA IxANVL
* Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP
* Obsługa klienta w usłudze ARP
* Opcjonalna Statystyka ARP/RARP określona przez aplikację
* Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
* Intuicyjne interfejsy API ARP/RARP: *nx_arp_ \**, *nx_rarp_ \**

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, Wi-Fi, BLUETOOTH LE, 15,4 itd.

## <a name="small-footprint"></a>Niewielkie rozmiary

Usługa Azure RTO NetX ma niewielki zasięg z 9 KB do 15 KB w przypadku podstawowej obsługi protokołów IP i UDP. Do obsługi funkcji TCP jest wymagana dodatkowa ilość pamięci o wartości 10 KB do 13 KB. Użycie pamięci RAM usługi Azure RTO NetX zazwyczaj mieści się w zakresie od 2,6 KB do 3,6 KB oraz pamięci puli pakietów zdefiniowanej przez aplikację. Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar usługi Azure RTO NetX jest automatycznie skalowany w oparciu o usługi używane przez aplikację. To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.

## <a name="fast-execution"></a>Szybkie wykonywanie

Usługa Azure RTO NetX zapewnia implementację wysyłania/odbierania pakietów o zerowej kopii i ma wysoką integrację z usługą Azure RTO ThreadX w celu uzyskania najszybszej możliwej wydajności. Na przykład usługa Azure RTO NetX może zazwyczaj osiągnąć niemal WireSpeed transfery danych na procesorze 80 MHz (lub mniej), jednocześnie używając tylko małego procentu cykli procesora.

## <a name="simple-easy-to-use"></a>Proste i łatwe w użyciu

Korzystanie z usługi Azure RTO NetX jest proste. Interfejs API usługi Azure RTO NetX jest intuicyjny i wysoce funkcjonalny. Nazwy interfejsów API składają się z prawdziwych słów, a nie "alfabetu" (zup) ani nazw o wysokim skrócie, które są często używane w innych produktach sieciowych. Wszystkie interfejsy API usługi Azure RTO NetX mają wiodące *nx_* i są zgodne z konwencją nazewnictwa czasowników. Ponadto istnieje spójność funkcjonalna w całym interfejsie API. Na przykład wszystkie funkcje interfejsu API, które zawieszają, mają opcjonalny limit czasu, który działa w taki sam sposób. W przypadku starszych aplikacji usługa Azure RTO NetX oferuje dodatkową warstwę zgodną z gniazdem BSD. Ta warstwa ułatwia deweloperom łatwe Migrowanie dużych aplikacji sieciowych.

## <a name="interoperability-verification"></a>Weryfikacja współdziałania

Usługa Azure RTO NetX jest zgodna ze standardami RFC i oferuje pełną współdziałanie z urządzeniami dla większości dostawców. Usługa Azure RTO NetX korzysta również z standardowej w branży IxANVL (zautomatyzowanej biblioteki sprawdzania poprawności sieci) dla implementacji protokołu TCP/IP w ramach platformy Azure RTO NetX.

## <a name="advanced-technology"></a>Technologia zaawansowana

Usługa Azure RTO NetX jest zaawansowaną technologią obejmującą następujące możliwości:

* Architektura™ Piconet
* Skalowanie automatyczne
* ™ Fast-Path technologii UDP
* elastyczne zarządzanie pakietami
* Interfejs API kopiowania i implementacja protokołu zero
* Obsługa wieloadresowa
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Obsługa routingu statycznego
* Obsługa analizy systemu Azure RTO TraceX

## <a name="fastest-time-to-market"></a>Najszybszy czas wprowadzenia na rynek

Usługa Azure RTO NetX umożliwia łatwe instalowanie, uczenie się, używanie, debugowanie, weryfikowanie, certyfikowanie i konserwowanie. W związku z tym usługa Azure RTO NetX jest jednym z najpopularniejszych stosów TCP/IP dla osadzonych urządzeń IoT, w tym wielu SoC z usługi Broadcom, Gainspan i tak dalej. Nasza spójna przedział czasu na rynek jest oparta na:

* Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO NetX](about-this-guide.md) i zapoznaj się z Tobą.
* Ukończ dostępność kodu źródłowego
* łatwy w użyciu interfejs API
* kompleksowy i zaawansowany zestaw funkcji

## <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.

## <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy o najwyższej jakości

W ciągu lat kod źródłowy usługi Azure RTO NetX ustawił na pasku jakość i łatwość interpretacji. Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.

## <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Usługa Azure RTO NetX działa dla najpopularniejszych mikroprocesorów 32-bitowych, wbudowanych, w pełni przetestowanych i w pełni obsługiwanych, w tym następujących architektur zaawansowanych:

**Urządzenia analogowe**: SHARC, Blackfin, CM4xx

**Andes rdzeń**: RISC-V

**Ambiqmicro**: Apollo MCUs

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Erze**: Xtensa, romb

**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi

**Cypress**: RISC-V

**EnSilica**: ESI-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10

**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32

**Mikrośrednik**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: sh, HS, V850, RX, rz, synergia

**Krzem Labs**: EFM32

**SynopSYS**: Arc 600, 700, łuk em, łuk HS

**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C

**Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacunkami i mogą być inne na platformie deweloperskiej.*
