---
title: Opis Azure RTOS NetX
description: Azure RTOS NetX to implementacja standardów protokołu TCP/IP o wysokiej wydajności, w pełni zintegrowana z platformą Azure RTOS ThreadX i dostępna dla wszystkich obsługiwanych procesorów.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a5dd020daeb336f264bf611fc3a515e55dbc5dab6f9afbcfdbf3733baa66de26
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782782"
---
# <a name="overview-of-azure-rtos-netx"></a>Omówienie Azure RTOS NetX

Azure RTOS NetX to osadzony stos sieciowy TCP/IP IPv4 klasy przemysłowej zaprojektowany specjalnie z myślą o aplikacjach osadzonych, osadzonych w czasie rzeczywistym i aplikacjach IoT. Azure RTOS NetX jest oryginalnym stosem sieciowym protokołu IPv4 firmy Microsoft i zasadniczo jest podzbiorem Azure RTOS. NetX udostępnia osadzone aplikacje z podstawowymi protokołami sieci, takimi jak IPv4, TCP i UDP, a także kompletny zestaw dodatkowych protokołów dodatków wyższego poziomu. Niewielkie zużycie pamięci, szybkie wykonywanie i najwyższa łatwość użycia sprawiają, że Azure RTOS NetX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.

## <a name="api-protocols"></a>Protokoły interfejsu API
Azure RTOS NetX zapewnia obsługę następujących czynności.

### <a name="telnet"></a>Telnet

* Minimalna 0,5 KB i 0,3 KB pamięci RAM.
* Obsługa klientów i serwerów.

### <a name="auto-ip"></a>Automatyczny adres IP

* Automatyczne przypisywanie adresów IPv4.
* Minimalna 1,2 KB, 300 bajtów pamięci RAM.

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP — protokół HTTP (Hypertext Transfer Protocol)

* Minimalnie od 2,8 KB do 4,8 KB UKOŚNIKA, od 0,4 KB do 1,0 KB pamięci RAM.
* Obsługa klientów i serwerów.

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP — Simple Mail Transfer Protocol (SMTP)

* Minimalnie 4,1 KB i 0,6 KB pamięci RAM
* Obsługa klientów

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP — Dynamic Host Configuration Protocol (DHCP)

* Minimalnie od 3,6 KB do 4,6 KB pamięci FLASH, 2,7 KB pamięci RAM
* Obsługa klientów i serwerów
* Obsługa protokołu IPv4

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 — protokół post Office w wersji 3 (POP3)

* Minimalnie 8,1 KB i 1,4 KB pamięci RAM
* Obsługa klientów

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP — Simple Network Management Protocol (SNMP)

* Minimalnie 10,9 KB i 2,6 KB pamięci RAM
* Obsługa agentów dla wersji VI, V2 i V3

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP — protokół transferu plików (FTP), Trivial File Transfer Protocol (TFTP)

* FTP Minimalnie od 1,8 KB do 7,2 KB UKOŚNIKA, od 0,6 KB do 2,1 KB pamięci RAM
* TFTP minimalnie od 1,7 KB do 2,4 KB UKOŚNIKA, od 0,3 KB do 1,8 KB pamięci RAM
* Obsługa klientów i serwerów

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP — protokół Polnt-to-PoInt (PPP)

* Minimalnie 7,1 KB i 3,8 KB pamięci RAM
* Niezawodna i niezawodna.

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP — prosty protokół czasu sieciowego (SNTP)

* Minimalna 4 KB i 0,5 KB pamięci RAM
* Obsługa klientów

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* Szybka implementacja interfejsu API bez kopiowania
* Opcjonalna warstwa BSD do przenoszenia starszego kodu gniazda

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP — protokół IGMP (Internet Group Management Protocol)

* Minimalna 2,5 KB pamięci FLASH
* Obsługa grup multiemisji protokołu IPv4
* Zweryfikowane przez IxANVL IxANVL
* Opcjonalne statystyki IGMP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX

### <a name="udp---user-datagram-protocol-udp"></a>UDP — protokół UDP (User Datagram Protocol)

* Minimalna pamięć FLASH 2,5 KB, 124 bajty pamięci RAM na gniazdo
* Szybkie przetwarzanie pakietów TCP prawie z wire speed:
* RX 95 Mb/s na Ethernet 100 Mb/s, @100MHz MIKROU, 14% wykorzystanie MIKROU
* TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 10% wykorzystanie mikrojądek
* Technologia Szybka ścieżka UDP™ technologii
* Brak limitów liczby protokołu UDP
* Zweryfikowane przez IxANVL IxANVL
* Opcjonalne zawieszenie podczas odbierania gniazda
* Opcjonalny limit czasu dla całego zawieszenia
* Opcjonalne statystyki UDP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP — Transmission Control Protocol (TCP)

* Minimalnie od 10,5 KB do 12,5 KB pamięci FLASH, 280 bajtów pamięci RAM na gniazdo
* Szybkie, prawie wlre speed przetwarzanie pakietów TCP:
* RX 93 Mb/s na Ethernet 100 Mb/s, @100MHz MCU, 20% wykorzystanie MIKROU
* TX 94 Mb/s w sieci Ethernet 100 Mb/s, @100MHz MIKROU, 27% wykorzystanie mikrojądek
* Niezawodne połączenie
* Brak limitów liczby gniazd TCP
* Zweryfikowane przez IxANVL IxANVL
* Opcjonalne zawieszenie podczas odbierania/przesyłania gniazda
* Opcjonalny limit czasu dla całego zawieszenia
* Opcjonalne statystyki TCP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP — protokół ICMP (Internet Control Message Protocol)

* Minimalna 2,5 KB pamięci FLASH
* Obsługa protokołu IPv4
* Zweryfikowane przez IxANVL IxANVL
* Żądanie ping i odpowiedź ping
* Opcjonalne wstrzymanie wątku dla żądań ping
* Opcjonalny limit czasu dla całego zawieszenia
* Opcjonalne statystyki ICMP
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX

### <a name="ipv4---internet-protocol-ip"></a>IPv4 — protokół internetowy (IP)

* Minimalnie od 3,5 KB do 8,5 KB pamięci FLASH, od 2 KB do 3 KB pamięci RAM.
* Piconet™ Architecture (Architektura aplikacji Piconet).
* Szybka, prawie wire speed wydajność.
* Obsługa wielu interfejsów.
* Obsługa wielu domów.
* Obsługa routingu statycznego.
* Obsługa fragmentacji/ponownegoassembly adresu IP.
* Obsługa protokołu IPv4.
* Zweryfikowane przez IxANVL IxANVL.
* Certyfikacja gotowego logo fazy II.
* Opcjonalne statystyki adresów IP.
* Dobrze zdefiniowany, intuicyjny interfejs sterownika warstwy fizycznej.
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX.

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP — protokół rozpoznawania adresów (ARP, Address Resolution Protocol), rarp (Reverse Address Resolution Protocol)

* Minimalna pamięć FLASH 1,7 KB, rozmiar pamięci RAM.
* Dynamiczna rozdzielczość 32-blt adresów IPv4 i 48-blt adresów MAC.
* Zweryfikowane przez IxANVL IXANVL.
* Elastyczna, zdefiniowana przez użytkownika pamięć podręczna ARP.
* Niesłabnące wsparcie dla ARP.
* Opcjonalne statystyki ARP/RARP określone przez aplikację.
* Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX.

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, WiFi, BLUETOOTH LE, 15.4 itp.

## <a name="interoperability-verification"></a>Weryfikacja współdziałania

Azure RTOS NetX jest zgodna ze standardami RFC i oferuje pełne współdziałanie z urządzeniami większości dostawców. Azure RTOS NetX korzysta również ze standardowej w branży biblioteki IxANVL (Automated Network Validation Library) na Azure RTOS implementacji podstawowego protokołu TCP/IP netx core.

## <a name="advanced-technology"></a>Zaawansowana technologia

Azure RTOS NetX to zaawansowana technologia, która obejmuje następujące elementy.
* Piconet™ architektury.
* Automatyczne skalowanie.
* Technologia Fast-Path UDP™.
* Elastyczne zarządzanie pakietami.
* Interfejs API bez kopiowania i implementacja.
* Obsługa wielu domu.
* Opcjonalny limit czasu dla całego zawieszenia.
* Obsługa routingu statycznego.
* Azure RTOS analizy systemu TraceX.
