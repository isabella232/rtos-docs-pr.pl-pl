---
title: Rozdział 2 . Instalowanie i używanie Azure RTOS NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem stosu sieciowego o wysokiej wydajności Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ac41672959c0873d90bdafe0d6b959efdddf8ecc
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178225"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>Rozdział 2 . Instalowanie i używanie Azure RTOS NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem stosu sieciowego o wysokiej wydajności Azure RTOS NetX Duo, w tym: 

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Opracowywanie osadzone jest zwykle wykonywane na komputerach Windows komputerach hostów z systemem Linux (Unix). Gdy aplikacja zostanie skompilowana, połączona i plik wykonywalny zostanie wygenerowany na hoście, zostanie on pobrany na docelowy sprzęt w celu wykonania.

Zazwyczaj pobieranie docelowe jest wykonywane z poziomu debugera narzędzia dewelopera. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, halt, breakpoint itp.), a także dostępu do rejestrów pamięci i procesora.

Większość debugerów narzędzi deweloperskie komunikuje się ze sprzętem docelowym za pośrednictwem połączeń debugowania na mikroukładach (OCD), takich jak JTAG (IEEE 1149.1) i tryb debugowania w tle (BDM). Debugerzy komunikują się również ze sprzętem docelowym za pośrednictwem In-Circuit emulacji (ICE). Połączenia OCD i ICE zapewniają niezawodne rozwiązania z minimalnym wtargnięciem do docelowego oprogramowania.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy netX Duo jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

NetX Duo wymaga od 5 KB do 45 KB Read-Only pamięci (ROM) na komputerze docelowym. Kolejne od 1 do 5 KB pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla stosu wątków NetX Duo i innych globalnych struktur danych.

Ponadto NetX Duo wymaga użycia dwóch obiektów czasomierza ThreadX i jednego obiektu mutex ThreadX. Te obiekty są używane do okresowego przetwarzania i ochrony wątków wewnątrz stosu protokołu NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS NetX Duo można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/netxduo/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

**nx_api.h**  
Plik nagłówkowy języka C zawierający wszystkie elementy systemowe, struktury danych i prototypy usług.

**nx_port.h** Plik nagłówkowy języka C zawierający wszystkie definicje i struktury danych dla celów i narzędzia deweloperskiego. 

**demo_netx.c** Plik C zawierający małą aplikację demonstracyjną.

**nx.a (lub nx.lib)**  
Wersja binarna biblioteki NetX C dystrybuowanej za pomocą pakietu standardowego.

## <a name="netx-duo-installation"></a>Instalacja NetX Duo

NetX Duo jest instalowany przez skłodzenie GitHub repozytorium na komputer lokalny. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium NetX Duo na komputerze:

```c
    git clone https://github.com/azure-rtos/netxduo
```

Możesz też pobrać kopię repozytorium przy użyciu przycisku pobierania na stronie GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki NetX Duo znajdziesz również na pierwszej stronie repozytorium online.

> [!IMPORTANT]
> *Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki NetX Duo (zazwyczaj **nx.a** lub **nx.lib),** a pliki dołączane w języku C **nx_api.h i nx_port.h**. W tym celu należy wybrać odpowiednią ścieżkę dla narzędzi deweloperskie lub skopiować te pliki do obszaru projektowania aplikacji.*

## <a name="using-netx-duo"></a>Korzystanie z NetX Duo

Korzystanie z netx duo jest łatwe. Zasadniczo kod aplikacji musi zawierać plik ***nx_api.h** _ podczas kompilacji i łączyć się z biblioteką NetX Duo _*_nx.a_*_ (lub _ *_nx.lib_*)*.

Poniżej przedstawiono cztery proste kroki wymagane do skompilowania aplikacji NetX Duo:

| Krok  | Opis  |
|---|---|
|Krok &nbsp; 1. |Dołącz plik ***nx_api.h*** do wszystkich plików aplikacji, które korzystają z usług NetX Duo lub struktur danych.|
|Krok &nbsp; 2. |Zainicjuj system NetX Duo, wywołując funkcję ***nx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.|
|Krok &nbsp; 3. |Utwórz wystąpienie adresu IP, włącz protokół rozpoznawania adresów (ARP), jeśli to konieczne, oraz wszelkie gniazda po ***nx_system_initialize*** wywoływania.|
|Krok &nbsp; 4. |Skompiluj źródło aplikacji i połącz je za pomocą biblioteki środowiska uruchomieniowego NetX Duo ***nx.a** _ (lub _*_nx.lib_**). Wynikowy obraz można pobrać do obiektu docelowego i wykonać.|

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port NetX Duo jest dostarczany z co najmniej jednym pokazem, który jest wykonywany w rzeczywistej sieci lub za pośrednictwem symulowanego sterownika sieciowego. Zawsze dobrym pomysłem jest uruchomienie najpierw systemu pokazowego.

Jeśli system pokazowy nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić problem:

1. Określ, jaka część pokazu jest uruchomiona.
2. Zwiększ rozmiary stosów we wszystkich nowych wątkach aplikacji.
3. Skompiluj ponownie bibliotekę NetX Duo przy użyciu odpowiednich opcji debugowania wymienionych w sekcji opcji konfiguracji.
4. Sprawdź strukturę NX_IP, aby sprawdzić, czy pakiety są wysyłane lub odbierane.
5. Sprawdź domyślną pulę pakietów, aby sprawdzić, czy są dostępne pakiety.
6. Upewnij się, że sterownik sieciowy dostarcza pakiety ARP i IP z jego nagłówkami w granicach 4-bajtowych dla aplikacji wymagających łączności IPv4 lub IPv6.
7. Tymczasowo pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub zmienia się. Takie informacje powinny okazać się przydatne dla inżynierów pomocy technicznej firmy Microsoft.

Postępuj zgodnie z procedurami opisanymi w "What We Need From You" (Czego potrzebujemy od Ciebie) na stronie 12, aby wysłać informacje zebrane w krokach rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki NetX Duo i aplikacji przy użyciu narzędzia NetX Duo. Opcje konfiguracji można zdefiniować w źródle aplikacji, w wierszu polecenia lub w pliku ***dołączania nx_user.h, chyba*** że określono inaczej.

> [!NOTE]
> *Opcje zdefiniowane w **programie nx_user.h** są* stosowane tylko wtedy, gdy aplikacja i biblioteka NetX Duo **NX_INCLUDE_USER_DEFINE_FILE** zdefiniowane.*

W poniższych sekcjach przedstawiono opcje konfiguracji dostępne w netx duo. Ogólne opcje dotyczące zarówno protokołu IPv4, jak i IPv6 są wymienione jako pierwsze, a następnie opcje specyficzne dla protokołu IPv6.

### <a name="system-configuration-options"></a>Opcje konfiguracji systemu

| Opcja  | Opis  |
|---|---|
| NX_ASSERT_FAIL    | Symbol, który definiuje instrukcje debugowania do użycia, gdy asercja zakończy się niepowodzeniem.                               |
| NX_DEBUG           | Zdefiniowano , włącza opcjonalne informacje debugowania drukowania dostępne ze sterownika sieci Ethernet pamięci RAM. |
| NX_DEBUG_PACKET   | Zdefiniowane umożliwia opcjonalne zrzucanie pakietów debugowania dostępnych w sterowniku sieci Ethernet pamięci RAM.      |
| NX_DISABLE_ASSERT | Zdefiniowane wyłącza sprawdzanie assert w kodzie źródłowym. Domyślnie ta opcja nie jest zdefiniowana.            |
|NX_DISABLE_ERROR_CHECKING | Zdefiniowano, usuwa podstawowy interfejs API sprawdzania błędów NetX Duo i poprawia wydajność. Kody powrotne interfejsu API, na które nie ma wpływu wyłączenie sprawdzania błędów, są wyświetlane pogrubioną czcionką w definicji interfejsu API. Ta definiowanie jest zwykle używana po wystarczającym debugowaniu aplikacji, a jej użycie zwiększa wydajność i zmniejsza rozmiar kodu.|
|NX_DRIVER_DEFERRED_PROCESSING | Zdefiniowane, włącza odroczoną obsługę pakietów sterowników sieciowych. Dzięki temu sterownik sieciowy umieszcza pakiet w wystąpieniu adresu IP i ma rzeczywistą procedurę przetwarzania o nazwie z wątku pomocnika wewnętrznego adresu IP NetX Duo.|
|NX_DUAL_PACKET_POOL_ENABLE | Zmieniono nazwę na ***NX_ENABLE_DUAL_PACKET_POOL** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_ENABLE_DUAL_PACKET_POOL_**.|
|NX_ENABLE_DUAL_PACKET_POOL | Zdefiniowane umożliwia stosowi korzystanie z dwóch pul pakietów, jednej o dużym rozmiarze ładunku i jednej o mniejszym rozmiarze ładunku. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| Zdefiniowane, umożliwia więcej wpięć wywołania zwrotnego w stosie. Te funkcje wywołania zwrotnego są używane przez warstwę otoki BSD. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_ENABLE_INTERFACE_CAPABILITY| Zdefiniowane umożliwia sterownikowi urządzenia interfejsu określenie dodatkowych informacji o możliwościach, takich jak od ładowania sumy kontrolnej. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| Zdefiniowane umożliwia sprawdzanie adresu źródłowego pakietu przychodzącego. Domyślnie ta opcja jest wyłączona.|
| NX_IPSEC_ENABLE  | Zdefiniowane umożliwia bibliotece NetX Duo obsługę operacji protokołu IPsec. Ta funkcja wymaga opcjonalnego modułu NetX Duo IPsec. Domyślnie ta funkcja nie jest włączona.            |
| NX_LITTLE_ENDIAN | Zdefiniowane, wykonuje niezbędne wymiany bajtów w środowiskach little endian, aby upewnić się, że nagłówki protokołu są we właściwym big endian formatu. Pamiętaj, że wartość domyślna jest zwykle konfigurowana ***w nx_port.h.***|
|NX_MAX_PHYSICAL_INTERFACES | Określa łączną liczbę fizycznych interfejsów sieciowych na urządzeniu. Wartość domyślna to 1 i jest zdefiniowana w ***nx_api.h***; urządzenie musi mieć co najmniej jeden interfejs fizyczny. Należy pamiętać, że nie obejmuje to interfejsu sprzężenia zwrotnego.|
| NX_NAT_ENABLE | Zdefiniowany, NetX Duo jest zbudowany z procesu NAT. Domyślnie ta opcja nie jest zdefiniowana.|
| NX_PHYSICAL_HEADER  | Określa rozmiar w bajtach fizycznego nagłówka ramki. Wartość domyślna to 16 (na podstawie typowej 14-bajtowej ramki Ethernet wyrównanej do granicy 32-bitowej) i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed _*_nx_api.h,_*_ na przykład w _ *_nx_user.h_*.* |
| NX_PHYSICAL_TRAILER | Określa rozmiar w bajtach fizycznego przyczepki pakietów i jest zwykle używany do rezerwowania magazynu dla takich rzeczy jak karty ETHERNET CRC itp. Wartość domyślna to 4 i jest zdefiniowana w ***nx_api.h.***|

### <a name="arp-configuration-options"></a>Opcje konfiguracji ARP

| Opcja  | Opis  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | Zdefiniowano , dzięki temu netX Duo może chronić swój adres IP, wysyłając odpowiedź ARP.|
|NX_ARP_DEFEND_INTERVAL| Definiuje interwał, w sekundach, moduł ARP wysyła następny pakiet obrony w odpowiedzi na przychodzący komunikat ARP, który wskazuje adres w konflikcie.|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  Zmieniono nazwę na ***NX_DISABLE_ARP_AUTO_ENTRY** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_DISABLE_ARP_AUTO_ENTRY_**.|
|NX_ARP_EXPIRATION_RATE| Określa liczbę sekund, przez które wpisy ARP pozostają prawidłowe. Wartość domyślna zero wyłącza wygasanie lub przedawnianie wpisów ARP i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Zmieniono nazwę na ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _. Mimo że nadal jest obsługiwany, zachęcamy do korzystania z nowych projektów _*_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_**.|
|NX_ARP_MAX_QUEUE_DEPTH | Określa maksymalną liczbę pakietów, które mogą być kolejkowane podczas oczekiwania na odpowiedź ARP. Wartość domyślna to 4 i jest zdefiniowana ***w nx_api.h.***|
|NX_ARP_MAXIMUM_RETRIES | Określa maksymalną liczbę ponownych prób ARP wykonanych bez odpowiedzi ARP. Wartość domyślna to 18 i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_ARP_UPDATE_RATE | Określa liczbę sekund między ponownych prób ARP. Wartość domyślna to 10, która reprezentuje 10 sekund i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_DISABLE_ARP_AUTO_ENTRY | Zdefiniowane wyłącza wprowadzanie informacji o żądaniu ARP w pamięci podręcznej ARP.|
|NX_DISABLE_ARP_INFO | Zdefiniowane wyłącza zbieranie informacji ARP.|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| Zdefiniowane umożliwia URP wywoływanie funkcji powiadamiania o wywołaniu zwrotny w przypadku wykrycia, że adres MAC został zaktualizowany.|

### <a name="icmp-configuration-options"></a>Opcje konfiguracji ICMP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_ICMP_INFO| Zdefiniowane wyłącza zbieranie informacji ICMP.|
|NX_DISABLE_ICMP_RX_CHECKSUM| Zdefiniowane wyłącza obliczenia sumy kontrolnej ICMPv4 i ICMPv6 odebranych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego jest w stanie zweryfikować sumy kontrolne ICMPv4 i ICMPv6, a aplikacja nie używa funkcji fragmentacji adresów IP ani funkcji IPsec. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMP_TX_CHECKSUM | Zdefiniowano, wyłącza obliczenia sumy kontrolnej ICMPv4 i ICMPv6 dla przesyłanych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego jest w stanie obliczyć sumy kontrolne ICMPv4 i ICMPv6,
a aplikacja nie używa funkcji fragmentacji adresów IP ani funkcji protokołu IPsec. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | Zdefiniowane: NetX Duo nie wysyła komunikatów o błędach ICMPv4 w odpowiedzi na błędy, takie jak nieprawidłowo sformatowany nagłówek IPv4. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | Zdefiniowano, wyłącza obliczanie sumy kontrolnej ICMPv4 dla odebranych pakietów ICMP. Ta opcja jest definiowana ***automatycznie, NX_DISABLE_ICMP_RX_CHECKSUM*** zdefiniowano. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _*_NX_DISABLE_ICMPV4_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | Zdefiniowano, wyłącza obliczanie sumy kontrolnej ICMPv4 dla przesyłanych pakietów ICMP. Ta opcja jest definiowana ***automatycznie, NX_DISABLE_ICMP_TX_CHECKSUM*** zdefiniowano. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _.</br>Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_DISABLE_ICMPV4_TX_CHECKSUM_**.|
|NX_ENABLE_ICMP_ADDRESS_CHECK | Zdefiniowano, że jest sprawdzany adres docelowy pakietu ICMP. Domyślne ustawienie to Wyłączony. Żądanie echa ICMP przeznaczone dla adresu ip emisji lub multiemisji IP zostanie dyskretnie odrzucone.|

### <a name="igmp-configuration-options"></a>Opcje konfiguracji IGMP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_IGMP_INFO | Zdefiniowane wyłącza zbieranie informacji IGMP.|
|NX_DISABLE_IGMPV2 | Zdefiniowane, wyłącza obsługę protokołu IGMPv2, a netX Duo obsługuje tylko protokół IGMPv1. Domyślnie ta opcja nie jest ustawiona i jest zdefiniowana w ***nx_api.h.***|
|NX_MAX_MULTICAST_GROUPS | Określa maksymalną liczbę grup multiemisji, które mogą być połączone. Wartość domyślna to 7 i jest zdefiniowana w ***nx_api.h** _. Aplikacja może zastąpić wartość domyślną, definiując wartość przed dopisem *__ nx_api.h*._*|

### <a name="ip-configuration-options"></a>Opcje konfiguracji adresu IP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_FRAGMENTATION | Zdefiniowane wyłącza fragmentację IPv4 i IPv6 oraz logikę ponownegoassembly.|
| NX_DISABLE_IPV4     | Zdefiniowano, wyłącza funkcję protokołu IPv4. Tej opcji można użyć do skompilowania aplikacji NetX Duo w celu suupportowania tylko protokołu IPv6. Domyślnie ta opcja nie jest zdefiniowana. |
| NX_DISABLE_IP_INFO | Zdefiniowane wyłącza zbieranie informacji o adresie IP.|
|NX_DISABLE_IP_RX_CHECKSUM | Zdefiniowano, wyłącza logikę sumy kontrolnej dla odebranych pakietów IPv4. Jest to przydatne, jeśli urządzenie sieciowe może zweryfikować podsumę kontrolną IPv4, a aplikacja nie oczekuje fragmentacji adresu IP ani protokołu IPsec.|
|NX_DISABLE_IP_TX_CHECKSUM | Zdefiniowano, wyłącza logikę sumy kontrolnej dla wysyłanych pakietów IPv4. Jest to przydatne w sytuacjach, w których bazowe urządzenie sieciowe może wygenerować sumy kontrolne nagłówka IPv4, a aplikacja nie oczekuje fragmentacji adresów IP ani protokołu IPsec.|
|NX_DISABLE_LOOPBACK_INTERFACE | Zdefiniowane wyłącza obsługę interfejsu sprzężenia zwrotnego netX Duo.|
|NX_DISABLE_RX_SIZE_CHECKING | Zdefiniowane wyłącza sprawdzanie rozmiaru odebranych pakietów.|
|NX_ENABLE_IP_RAW_PACKET_FILTER | Zdefiniowano , włącza funkcję filtrowania odbierania nieprzetworzonych pakietów IP. Aplikacje wymagające większej kontroli nad typem nieprzetworzonych pakietów IP, które mają być odbierane, mogą korzystać z tej funkcji. Funkcja filtrowania nieprzetworzonych pakietów IP obsługuje również nieprzetworzone działanie gniazda w warstwie zgodności BSD. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_ENABLE_IP_STATIC_ROUTING | Zdefiniowane, włącza routing statyczny IPv4, w którym adres docelowy można przypisać określony adres następnego przeskoku. Domyślnie routing statyczny IPv4 jest wyłączony.|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | Zdefiniowane umożliwia wykonanie logiki ponownego zbierania IPv4 i IPv6 od razu po otrzymaniu fragmentu adresu IP. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_IP_MAX_REASSEMBLY_TIME | Symbol, który kontroluje maksymalny dozwolony czas ponownego zsyłania fragmentu IPv4 i IPv6. Zwróć uwagę, że wartość zdefiniowana w tym miejscu zastępuje zarówno wartości ***NX_IPV4_MAX_REASSEMBLY_TIME** _, jak i _*_NX_IPV6_MAX_REASSEMBLY_TIME_**.|
|NX_IP_PERIODIC_RATE | Zdefiniowane określa liczbę takt czasomierza ThreadX w ciągu jednej sekundy. Wartość domyślna pochodzi od symbolu ThreadX ***TX_TIMER_TICKS_PER_SECOND,** _ który domyślnie jest ustawiony na 100 (czasomierz 10ms). Aplikacje powinny zachować ostrożność podczas modyfikowania tej wartości, ponieważ pozostałe moduły NetX Duo pochodzą z informacji o chronometrażu _ *_NX_IP_PERIODIC_RATE_.**|
|NX_IP_RAW_MAX_QUEUE_DEPTH | Symbol sterujący liczbą nieprzetworzonych pakietów IP można dodać do kolejki odbierania nieprzetworzonych pakietów. Domyślnie wartość jest ustawiona na 20.| 
|NX_IP_ROUTING_TABLE_SIZE | Zdefiniowane ustawia maksymalną liczbę wpisów w tabeli routingu statycznego IPv4, która jest listą interfejsu wychodzącego i adresami następnego przeskoku dla danego adresu docelowego. Wartość domyślna to 8 i jest zdefiniowana w ***nx_api.h.** _ Ten symbol jest używany tylko *_wtedy, gdy zdefiniowano NX_ENABLE_IP_STATIC_ROUTING_* _ NX_ENABLE_IP_STATIC_ROUTING *.|
|NX_IPV4_MAX_REASSEMBLY_TIME | Symbol, który kontroluje maksymalny dozwolony czas ponownego zsyłania fragmentu protokołu IPv4. Zanotuj wartość zdefiniowaną w NX_IP_MAX_REASSEMBLY_TIME zastępuje tę wartość.|

### <a name="packet-configuration-options"></a>Opcje konfiguracji pakietów

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | Zdefiniowany, wyłącza logikę łańcucha pakietów. Domyślnie nie jest to zdefiniowane.|
|NX_DISABLE_PACKET_INFO | Zdefiniowane wyłącza zbieranie informacji o puli pakietów.|
|NX_ENABLE_LOW_WATERMARK | Zdefiniowano, włącza funkcję niskiego limitu puli pakietów NetX Duo. Aplikacja ustawia niską wartość limitu. W przypadku odbierania pakietów TCP, jeśli zostanie osiągnięty niski limit puli pakietów, program NetX Duo dyskretnie odrzuci pakiet, zwalniając go, uniemożliwiając utracenie puli pakietów. Domyślnie ta funkcja nie jest włączona.|
|NX_ENABLE_PACKET_DEBUG_INFO | Zdefiniowane rejestruje informacje debugowania pakietów.|
|NX_PACKET_ALIGNMENT | Zdefiniowany określa wymaganie wyrównania w bajtach dla adresu początkowego obszaru ładunku pakietu. Ta opcja powoduje deprecję ***NX_PACKET_HEADER_PAD** _ i _*_NX_PACKET_HEADER_PAD_SIZE_**. Domyślnie ta opcja jest zdefiniowana jako 4, dzięki czemu adres początkowy obszaru ładunku jest wyrównany o 4 bajty.|
|NX_PACKET_HEADER_PAD | Zdefiniowane, umożliwia wypełnienie pod koniec NX_PACKET sterowania. Liczba wyrazów do dosyłania w programie ULONG jest definiowana przez ***NX_PACKET_HEADER_PAD_SIZE** _. Pamiętaj, że ta opcja jest amortyzowana przez _*_NX_PACKET_ALIGNMENT_**.|
|NX_PACKET_HEADER_PAD_SIZE | Ustawia liczbę słów ULONG, które mają zostać doliszowane do struktury NX_PACKET, dzięki czemu obszar ładunku pakietu można rozpocząć od żądanego wyrównania. Ta funkcja jest przydatna, gdy deskryptory buforu odbierania wskazują bezpośrednio do obszaru ładunku usługi NX_PACKET, NX_PACKET interfejs sieciowy odbiera logikę odbierania lub logika operacji pamięci podręcznej oczekuje, że adres początkowy buforu spełnia określone wymagania wyrównania. Ta wartość staje się prawidłowa tylko **wtedy, NX_PACKET_HEADER_PAD** _ jest zdefiniowany. Pamiętaj, że ta opcja jest przestarzała przez _*_NX_PACKET_ALIGNMENT_**.|

### <a name="rarp-configuration-options"></a>Opcje konfiguracji RARP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_RARP_INFO | Zdefiniowane wyłącza zbieranie informacji RARP.|

### <a name="tcp-configuration-options"></a>Opcje konfiguracji TCP

| Opcja | Opis |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | Zdefiniowane wyłącza przetwarzanie resetowania podczas rozłączania, gdy podana wartość limitu czasu jest określona jako ***NX_NO_WAIT***.|
|NX_DISABLE_TCP_INFO | Zdefiniowane, wyłącza zbieranie informacji TCP.|
|NX_DISABLE_TCP_RX_CHECKSUM | Zdefiniowano, wyłącza logikę sumy kontrolnej dla odebranych pakietów TCP. Jest to przydatne tylko w sytuacjach, w których warstwa łącza ma niezawodną sumy kontrolnej lub CRC przetwarzania lub sterownik interfejsu jest w stanie zweryfikować sumy kontrolnej TCP na sprzęcie, a aplikacja nie używa protokołu IPsec.|
|NX_DISABLE_TCP_TX_CHECKSUM | Zdefiniowano, wyłącza logikę sumy kontrolnej do wysyłania pakietów TCP. Jest to przydatne tylko w sytuacjach, w których odbierający węzeł sieci otrzymał wyłączoną logikę sumy kontrolnej TCP lub źródłowy sterownik sieci jest w stanie wygenerować sumy kontrolne TCP, a aplikacja nie używa protokołu IPsec.|
|NX_ENABLE_TCP_KEEPALIVE | Zdefiniowany parametr włącza opcjonalny czasomierz utrzymania aktywności protokołu TCP. Ustawienia domyślne nie są włączone.|
|NX_ENABLE_TCP_MSS_CHECK | Zdefiniowane umożliwia weryfikację minimalnej równorzędnej usługi MSS przed zaakceptowaniem połączenia TCP. Aby można było korzystać z tej funkcji, ***NX_ENABLE_TCP_MSS_MINIMUM*** musi być zdefiniowana. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| Zdefiniowane umożliwia aplikacji zainstalowanie funkcji wywołania zwrotnego, która jest wywoływana, gdy głębokość kolejki przesyłania TCP nie ma już maksymalnej wartości. To wywołanie zwrotne służy jako wskazanie, że gniazdo TCP jest gotowe do przesyłania większej liczby danych. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_TCP_WINDOW_SCALING | Włącza opcję skalowania okien dla aplikacji TCP. Jeśli ta opcja jest zdefiniowana, opcja skalowania okien jest negocjowana podczas fazy połączenia TCP, a aplikacja może określić rozmiar okna większy niż 64K. Ustawienie domyślne nie jest włączone (nie zdefiniowano).|
|NX_MAX_LISTEN_REQUESTS | Określa maksymalną liczbę żądań nasłuchiwać serwera. Wartość domyślna to 10 i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_ACK_EVERY_N_PACKETS | Określa liczbę pakietów TCP do odbierania przed wysłaniem ACK. Jeśli wartość ***NX_TCP_IMMEDIATE_ACK** _ jest włączona, ale _ *_NX_TCP_ACK_EVERY_N_PACKETS_** nie, ta wartość jest automatycznie ustawiana na 1 w celu zapewnienia zgodności z poprzednimi wersjami.|
|NX_TCP_ACK_TIMER_RATE | Określa, w jaki sposób liczba taktów systemowych (NX_IP_PERIODIC_RATE) jest dzielona w celu obliczenia szybkości czasomierza dla opóźnionego przetwarzania ACK protokołu TCP. Wartość domyślna to 5, która reprezentuje 200ms i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_ENABLE_KEEPALIVE | Zmieniono nazwę na ***NX_ENABLE_TCP_KEEPALIVE** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_ENABLE_TCP_KEEPALIVE_**.|
|NX_TCP_ENABLE_MSS_CHECK | Zmieniono nazwę na ***NX_ENABLE_TCP_MSS_CHECK** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _ *_NX_ENABLE_TCP_MSS_CHECK._**|
|NX_TCP_ENABLE_WINDOW_SCALING | Zmieniono nazwę na ***NX_ENABLE_TCP_WINDOW_SCALING** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_ENABLE_TCP_WINDOW_SCALING_**.|
|NX_TCP_FAST_TIMER_RATE | Określa, w jaki sposób liczba wewnętrznych taktów (NX_IP_PERIODIC_RATE) NetX Duo jest dzielona w celu obliczenia szybkości czasomierza TCP. Szybki czasomierz TCP jest używany do kierowania różnymi czasomierzami TCP, w tym opóźnionym czasomierzem ACK. Wartość domyślna to 10, która reprezentuje 100ms przy założeniu, że czasomierz ThreadX jest uruchomiony na 10ms. Ta wartość jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_IMMEDIATE_ACK| Zdefiniowane umożliwia opcjonalne natychmiastowe przetwarzanie odpowiedzi ACK protokołu TCP. Zdefiniowanie tego symbolu jest równoważne zdefiniowaniu  ***NX_TCP_ACK_EVERY_N_PACKETS*** na 1.|
|NX_TCP_KEEPALIVE_INITIAL | Określa liczbę sekund braku aktywności przed aktywowanie czasomierza utrzymania aktywności. Wartość domyślna to 7200, która reprezentuje 2 godziny i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_KEEPALIVE_RETRIES | Określa, ile prób utrzymania aktywności jest dozwolonych, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_KEEPALIVE_RETRY | Określa liczbę sekund między ponownych prób czasomierza utrzymania aktywności przy założeniu, że druga strona połączenia nie odpowiada. Wartość domyślna to 75, która reprezentuje 75 sekund między ponownych prób i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol, który definiuje maksymalną liczbę poza kolejnością pakietów TCP, może być przechowywany w kolejce odbierania gniazd TCP. Ten symbol może służyć do ograniczania liczby pakietów w kolejce w gnieździe odbierania TCP, zapobiegając utracie puli pakietów. Domyślnie ten symbol nie jest zdefiniowany, w związku z tym nie ma limitu liczby pakietów poza kolejnością, które są kolejkowane w gnieździe TCP.|
|NX_TCP_MAXIMUM_RETRIES | Określa, ile danych przesyła ponowne próby, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_MAXIMUM_RX_QUEUE | Symbol definiujący maksymalną kolejkę odbierania dla gniazd TCP. Ta funkcja jest włączana ***przez NX_ENABLE_LOW_WATERMARK***.|
|NX_TCP_MAXIMUM_TX_QUEUE | Określa maksymalną głębokość kolejki przesyłania TCP, zanim żądania wysyłania TCP zostaną wstrzymane lub odrzucone. Wartość domyślna to 20, co oznacza, że w kolejce przesyłania może w danym momencie być maksymalnie 20 pakietów. Należy pamiętać, że pakiety pozostają w kolejce przesyłania, dopóki nie zostanie odebrany ACK, który obejmuje część lub wszystkie dane pakietów z drugiej strony połączenia. Ta stała jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_MSS_MINIMUM | Symbol definiujący minimalną wartość MSS akceptowaną przez moduł TCP NetX Duo. Ta funkcja jest włączana przez ***NX_ENABLE_TCP_MSS_CHECK***.|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | Zmieniono nazwę na ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_**.|
|NX_TCP_RETRY_SHIFT | Określa, jak zmienia się limit czasu retransmisji między ponownymi próbami. Jeśli ta wartość wynosi 0, początkowy limit czasu ponownego przetłumaczenia jest taki sam jak kolejne limity czasu ponownego przetłumaczenia. Jeśli ta wartość wynosi 1, każdy kolejny retransmisja jest dwa razy dłuższy. Jeśli ta wartość wynosi 2, każdy kolejny limit czasu ponownego przetłumaczenia jest cztery razy dłuższy. Wartość domyślna to 0 i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|
|NX_TCP_TRANSMIT_TIMER_RATE | Określa, jak liczba takt systemowych (***NX_IP_PERIODIC_RATE** _) jest dzielona w celu obliczenia szybkości czasomierza dla przetwarzania ponowień przesyłania TCP. Wartość domyślna to 1, która reprezentuje 1 sekundę i jest zdefiniowana _*_w nx_tcp.h._*_ Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._*|

### <a name="udp-configuration-options"></a>Opcje konfiguracji UDP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_UDP_INFO | Zdefiniowane, wyłącza zbieranie informacji UDP.|
|NX_DISABLE_UDP_RX_CHECKSUM | Zdefiniowane wyłącza obliczanie sumy kontrolnej UDP przychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego jest w stanie zweryfikować sumy kontrolne nagłówka UDP na sprzęcie, a aplikacja nie włącza logiki fragmentacji adresów IP ani protokołu IPsec.|
|NX_DISABLE_UDP_TX_CHECKSUM | Zdefiniowane wyłącza obliczanie sumy kontrolnej UDP dla wychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego może obliczyć sumy kontrolne nagłówka UDP i wstawić wartość w nagłówku adresu IP przed przesyłaniem danych, a aplikacja nie włącza logiki fragmentacji protokołu IPsec ani adresu IP.|

### <a name="ipv6-options"></a>Opcje protokołu IPv6  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_IPV6 | Wyłącza funkcję protokołu IPv6 podczas budowaną bibliotekę NetX Duo. W przypadku aplikacji, które nie wymagają protokołu IPv6, pozwala to uniknąć ściągania kodu i dodatkowego miejsca do magazynowania potrzebnego do obsługi protokołu IPv6.|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | Zdefiniowane wyłącza odnajdywanie jednostki MTU ścieżki, które służy do określania maksymalnej wartości MTU w ścieżce do obiektu docelowego w tabeli docelowej hosta NetX Duo. Dzięki temu host NetX Duo może wysłać największy możliwy pakiet, który nie będzie wymagał fragmentacji. Domyślnie ta opcja jest zdefiniowana (mtu ścieżki jest wyłączona).|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | Zdefiniowane umożliwia wywoływanie funkcji wywołania zwrotnego po zmianie adresu IPv6. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_IPV6_MULTICAST | Zdefiniowane, włącza funkcję dołączania/opuszczania multiemisji protokołu IPv6. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | Zdefiniowane, włącza funkcję odnajdywania jednostki MTU ścieżki IPv6. Domyślnie ta opcja nie jest włączona.|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | Zmieniono nazwę na ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _. Mimo że nadal jest obsługiwany, zachęcamy do korzystania z nowych projektów _*_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_**.|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | Określa liczbę wpisów w tabeli routingu IPv6. Dla routera domyślnego jest wymagany co najmniej wpis onS. Zdefiniowana ***w nx_api.h*** wartość domyślna to 8.|
|NX_IPV6_DESTINATION_TABLE_SIZE | Określa liczbę wpisów w tabeli docelowej IPv6. Przechowuje informacje o adresach następnego przeskoku dla adresów IPv6. Zdefiniowana ***w nx_api.h*** wartość domyślna to 8.|
|NX_IPV6_MAX_REASSEMBLY_TIME | Symbol, który kontroluje maksymalny dozwolony czas ponownego zsyłania fragmentu protokołu IPv6.|
|NX_IPV6_MULTICAST_ENABLE | Zmieniono nazwę na ***NX_ENABLE_IPV6_MULTICAST** _. Mimo że nadal jest obsługiwany, zachęcamy do korzystania z nowych projektów _*_NX_ENABLE_IPV6_MULTICAST_**.|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | Określa rozmiar tabeli prefiksów. Informacje o prefiksach są uzyskiwane z anonsów routera i są częścią konfiguracji adresu IPv6. Zdefiniowana ***w nx_api.h*** wartość domyślna to 8.|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | Zdefiniowane umożliwia netX Duo wyłączenie funkcji automatycznej konfiguracji adresów bez stanowych. Domyślnie ta opcja nie jest włączona.|
|NX_MAX_IPV6_ADDRESSES | Określa liczbę wpisów w puli adresów IPv6. Podczas konfigurowania interfejsu netX Duo używa wpisów IPv6 z puli. Domyślnie zezwala się na (NX_MAX_PHYSICAL_INTERFACES 3), aby każdy interfejs miał co najmniej jeden adres lokalny linku i \* dwa adresy globalne. Pamiętaj, że wszystkie interfejsy współdzielą pulę adresów IPv6.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Określa interwał oczekiwania w taktach czasomierza, aby zresetować ścieżkę MTU dla określonego obiektu docelowego w tabeli docelowej. Jeśli ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY*** jest zdefiniowany, zdefiniowanie tego symbolu nie ma żadnego efektu.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Symbol określający interwał oczekiwania (w sekundach) na zresetowanie wartości jednostki MTU ścieżki dla wpisu tabeli docelowej. Jest prawidłowa tylko ***wtedy, NX_ENABLE_IPV6_PATH_MTU_DISCOVERY*** jest zdefiniowana. Domyślnie ta wartość jest ustawiona na 600 (sekund).|

### <a name="neighbor-cache-configuration-options"></a>Opcje konfiguracji sąsiada pamięci podręcznej

| Opcja  | Opis  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | Określa opóźnienie (w sekundach) przed wysłaniem pierwszej na żądanie wpisu pamięci podręcznej w stanie NIEAKTUALNE. Zdefiniowana ***w nx_nd_cache.h*** wartość domyślna to 5.|
|NX_DISABLE_IPV6_DAD | Zdefiniowano, ta opcja wyłącza funkcję wykrywania zduplikowanych adresów podczas przypisywania adresów IPv6. Adresy są ustawiane za pomocą konfiguracji ręcznej lub automatycznej konfiguracji adresów bez stanowych.|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | Zdefiniowano, ta opcja uniemożliwia platformie NetX Duo usuwanie starszych wpisów tabeli pamięci podręcznej przed upływem limitu czasu, aby zrobić miejsce na nowe wpisy, gdy tabela jest pełna. Wpisy statyczne i wpisy routera nigdy nie są przeczyszczane.|
|NX_IPV6_DAD_TRANSMITS | Określa liczbę komunikatów na żądanie sąsiada, które mają być wysyłane, zanim NetX Duo oznacza adres interfejsu jako prawidłowy. Jeśli ***NX_DISABLE_IPV6_DAD** _ jest zdefiniowany (FUNKCJA JEST wyłączona), ustawienie tej opcji nie ma wpływu. Alternatywnie wartość zero (0) powoduje wyłączenie funkcji THE, ale pozostawia funkcjonalność THE W NetX Duo. Zdefiniowana w _*_nx_api.h_**, wartość domyślna to 3.|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | Zmieniono nazwę na ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _*_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_**.|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | Określa liczbę wpisów w tabeli sąsiada pamięci podręcznej IPv6. Zdefiniowana ***w nx_nd_cache.h*** wartość domyślna to 16.|
|NX_MAX_MULTICAST_SOLICIT | Określa liczbę komunikatów na żądanie sąsiada przesyłanych przez netX Duo jako część protokołu odnajdywania sąsiadów IPv6, gdy jest wymagane mapowanie między adresem IPv6 i adresem MAC. Zdefiniowana ***w nx_nd_cache.h*** wartość domyślna to 3.|
|NX_MAX_UNICAST_SOLICIT | Określa liczbę komunikatów na żądanie sąsiada przesyłanych przez NetX Duo w celu określenia osiągalności określonego sąsiada. Zdefiniowana ***w nx_nd_cache.h*** wartość domyślna to 3.|
|NX_ND_MAX_QUEUE_DEPTH | Symbol definiujący maksymalną liczbę pakietów w kolejce dla pamięci podręcznej ND do rozwiązania. Domyślnie ten symbol jest ustawiony na 4.|
|NX_REACHABLE_TIME | Określa w sekundach, aby wpis pamięci podręcznej istniał w stanie OSIĄGALNY bez pakietów odebranych z docelowego adresu IPv6 pamięci podręcznej. Zdefiniowana ***w nx_nd_cache.h*** wartość domyślna to 30.|
|NX_RETRANS_TIMER  | Określa w milisekundach długość opóźnienia między pakietami na żądanie wysyłanymi przez NetX Duo. Zdefiniowana ***w nx_nd_cache.h*** wartość domyślna to 1000.|
| NXDUO_DISABLE_DAD | Zmieniono nazwę na ***NX_DISABLE_IPV6_DAD** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _*_NX_DISABLE_IPV6_DAD_**.|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | Zmieniono nazwę na ***NX_IPV6_DAD_TRANSMITS** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_IPV6_DAD_TRANSMITS_**.|

### <a name="miscellaneous-icmpv6-configuration-options"></a>Różne opcje konfiguracji ICMPv6

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | Zdefiniowane wyłącza program NetX Duo możliwość wysyłania komunikatu o błędzie ICMPv6 w odpowiedzi na pakiet problemu (np. nieprawidłowo sformatowany nagłówek lub typ nagłówka pakietu jest przestarzały) odebrany z innego hosta.|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | Zdefiniowane wyłącza ICMPv6 przekierowywanie przetwarzania pakietów. NetX Duo domyślnie przetwarza komunikaty przekierowania i aktualizuje tabelę docelową przy użyciu informacji o adresie IP następnego przeskoku.|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | Zdefiniowane wyłącza program NetX Duo przetwarzanie informacji odebranych w pakietach anonsów routerów IPv6.|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | Zdefiniowane wyłącza netX Duo wysyłanie komunikatów na żądanie routera IPv6 w regularnych odstępach czasu do routera.|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | Zdefiniowano, wyłącza obliczanie sumy kontrolnej ICMPv6 dla odebranych pakietów ICMP.|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_DISABLE_CMPV6_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Zdefiniowane, wyłącza i ICMPv6 obliczeń sumy kontrolnej dla przesłanych pakietów ICMP.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_DISABLE_ICMPV6_TX_CHECKSUM_**.|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | Zdefiniuj maksymalną liczbę na żądanie routerów, które host wysyła do momentu odebrania odpowiedzi routera. Jeśli żadna odpowiedź nie zostanie odebrana, host stwierdzi, że router nie istnieje. Wartość domyślna to 3.|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | Określa maksymalne opóźnienie początkowego na żądanie routera w sekundach.|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | Określa interwał między dwoma komunikatami na żądanie routera. Wartość domyślna to 4.|
|NXDUO_DESTINATION_TABLE_SIZE | Zmieniono nazwę na ***NX_IPV6_DESTINATION_TABLE_SIZE** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_IPV6_DESTINATION_TABLE_SIZE_**.|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_DISABLE_ICMPV6_ERROR_MESSAGE_**.|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_**|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| Zmieniono nazwę na ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _*_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_**.|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _. Mimo że nadal jest ona obsługiwana, zachęcamy do używania nowych projektów _*_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_**.|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | Zmieniono nazwę na ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _*_NX_ICMPV6_MAX_RTR_SOLICITATIONS_**.|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | Zmieniono nazwę na ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _. Ten symbol jest amortyzowany. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów _ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_**|

## <a name="netx-duo-version-id"></a>Identyfikator wersji NetX Duo

Bieżąca wersja oprogramowania NetX Duo jest dostępna zarówno dla użytkownika, jak i dla oprogramowania aplikacji w czasie wykonywania. Wersję NetX Duo można uzyskać podczas badania **pliku nx_port.h.** Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję NetX Duo, sprawdzając globalny ciąg nx_version_id _* ** w_ pliku _*_nx_port.h_**.

Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych pokazanych poniżej zdefiniowanych w ***nx_api.h.***

Te stałe identyfikują bieżące wydanie produktu według nazwy i wersji pomocniczej produktu.

\#definiowanie EL_PRODUCT_NETXDUO  
\#definiowanie NETXDUO_MAJOR_VERSION  
\#definiowanie NETXDUO_MINOR_VERSION