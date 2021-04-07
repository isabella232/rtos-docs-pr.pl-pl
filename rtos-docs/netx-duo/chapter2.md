---
title: Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem stosu sieci o wysokiej wydajności Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8ee9d16c71d6c207de2098d688d49e6482c8b780
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550154"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem stosu sieci o wysokiej wydajności Azure RTO NetX Duo, w tym: 

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Projektowanie osadzone jest zwykle wykonywane na komputerach hostów z systemem Windows lub Linux (UNIX). Gdy aplikacja zostanie skompilowana, połączona, a plik wykonywalny jest generowany na hoście, zostanie pobrany na docelowy sprzęt do wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia deweloperskiego. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM). Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem). Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy dla NetX Duo jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

NetX Duo wymaga od 5 kilobajtów do 45 Read-Only KB pamięci (ROM) w miejscu docelowym. Kolejną 5KBytes pamięci docelowej (RAM) jest wymagana dla stosu wątku NetX Duo i innych struktur danych globalnych.

Ponadto NetX Duo wymaga użycia dwóch obiektów czasomierza ThreadX i jednego obiektu mutex ThreadX. Te obiekty są używane do okresowego przetwarzania i ochrony wątków w stosie protokołu NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO NetX Duo można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/netxduo/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

**nx_api. h**  
Plik nagłówkowy języka C zawierający wszystkie równe systemowe, struktury danych i prototypy usługi.

**nx_port. h** Plik nagłówkowy języka C zawierający wszystkie definicje i targetspecific danych. 

**demo_netx. c** Plik C zawierający małą aplikację demonstracyjną.

**NX. a (lub NX. lib)**  
Wersja binarna biblioteki NetX C, która jest dystrybuowana z pakietem standardowym.

## <a name="netx-duo-installation"></a>Instalacja NetX Duo

NetX Duo jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium NetX Duo na komputerze:

```c
    git clone https://github.com/azure-rtos/netxduo
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki NetX Duo na pierwszej stronie repozytorium online.

> [!IMPORTANT]
> *Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki NetX Duo (zazwyczaj **NX. a** lub **NX. lib**) i plików dołączanych C **nx_api. h i nx_port. h**. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do obszaru projektowania aplikacji.*

## <a name="using-netx-duo"></a>Korzystanie z programu NetX Duo

Korzystanie z programu NetX Duo jest proste. Zasadniczo kod aplikacji musi zawierać ***nx_api. h** _ podczas kompilacji i link z biblioteką NetX Duo _*_NX. a_*_ (lub _ *_NX. lib_*) *.

Poniżej przedstawiono cztery proste kroki wymagane do skompilowania aplikacji NetX Duo:

[!div class="mx-tdCol2BreakAll"]

| Krok  | Opis  |
|---|---|
|Krok &nbsp; 1: |Uwzględnij plik ***nx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług NetX Duo lub struktur danych.|
|Krok &nbsp; 2: |Zainicjuj system NetX Duo, wywołując ***nx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.|
|Krok &nbsp; 3. |Utwórz wystąpienie adresu IP, Włącz protokół ARP (Address Resolution Protocol), w razie potrzeby, i wszelkie gniazda po wywołaniu ***nx_system_initialize*** .|
|Krok &nbsp; 4. |Skompiluj Źródło aplikacji i połącz ją z biblioteką uruchomieniową NetX Duo ***NX. a** _ (lub _ *_NX. lib_* *). Obraz wyników można pobrać do elementu docelowego i wykonać!|

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port NetX Duo jest dostarczany z co najmniej jedną prezentacją, która jest wykonywana w rzeczywistej sieci lub za pośrednictwem symulowanego sterownika sieciowego. Zawsze dobrym pomysłem jest rozpoczęcie pierwszego uruchomienia systemu demonstracyjnego.

Jeśli system demonstracyjny nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić ten problem:

1. Określ, jaka część demonstracji jest uruchomiona.
2. Zwiększ rozmiary stosu w nowych wątkach aplikacji.
3. Skompiluj ponownie bibliotekę NetX Duo z odpowiednimi opcjami debugowania wymienionymi w sekcji opcji konfiguracji.
4. Sprawdź strukturę NX_IP, aby sprawdzić, czy pakiety są wysyłane lub odbierane.
5. Sprawdź domyślną pulę pakietów, aby sprawdzić, czy są dostępne pakiety.
6. Upewnij się, że sterownik sieciowy dostarcza pakiety ARP i IP ze swoimi nagłówkami w 4-bajtowych granicach dla aplikacji wymagających łączności IPv4 lub IPv6.
7. Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie. Takie informacje powinny być przydatne dla inżynierów pomocy technicznej firmy Microsoft.

Postępuj zgodnie z procedurami opisanymi w sekcji "czego potrzebujemy" na stronie 12, aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki NetX Duo i aplikacji przy użyciu programu NetX Duo istnieje kilka opcji konfiguracji. Opcje konfiguracji można definiować w źródle aplikacji, w wierszu polecenia lub w pliku ***nx_user. h*** , o ile nie określono inaczej.

> [!NOTE]
> *Opcje zdefiniowane w **nx_user. h** są stosowane tylko wtedy, gdy biblioteka aplikacji i NetX Duo zostały skompilowane przy użyciu* **NX_INCLUDE_USER_DEFINE_FILE** zdefiniowanych. *

W poniższych sekcjach wymieniono opcje konfiguracji dostępne w NetX Duo. W pierwszej kolejności są wyświetlane opcje ogólne dotyczące protokołów IPv4 i IPv6, a następnie opcje specyficzne dla protokołu IPv6.

### <a name="system-configuration-options"></a>Opcje konfiguracji systemu

| Opcja  | Opis  |
|---|---|
| NX_ASSERT_FAIL    | Symbol definiujący instrukcję Debug, która ma zostać użyta, gdy potwierdzenie nie powiedzie się.                               |
| NX_DEBUG           | Zdefiniowane, umożliwia opcjonalne informacje debugowania drukowania dostępne ze sterownika sieci Ethernet w pamięci RAM. |
| NX_DEBUG_PACKET   | Zdefiniowane, umożliwia zatopienie opcjonalnego pakietu debugowania w sterowniku sieci Ethernet w pamięci RAM.      |
| NX_DISABLE_ASSERT | Zdefiniowane, wyłącza sprawdzanie potwierdzenia w kodzie źródłowym. Domyślnie ta opcja nie jest zdefiniowana.            |
|NX_DISABLE_ERROR_CHECKING | Zdefiniowane, usuwa interfejs API podstawowego sprawdzania błędów NetX Duo i zwiększa wydajność. Kody powrotne interfejsu API, których nie dotyczy wyłączenie sprawdzania błędów, są wymienione w pogrubionym kroju pisma w definicji interfejsu API. Ta definicja jest zwykle używana, gdy aplikacja jest odpowiednio debugowana, a jej użycie zwiększa wydajność i zmniejsza rozmiar kodu.|
|NX_DRIVER_DEFERRED_PROCESSING | Zdefiniowane, umożliwia obsługę pakietów sterownika sieci odroczonej. Dzięki temu sterownik sieciowy może umieścić pakiet w wystąpieniu IP i mieć rzeczywistą procedurę przetwarzania wywołana z wątku pomocnika wewnętrznego adresu IP NetX Duo.|
|NX_DUAL_PACKET_POOL_ENABLE | Zmieniono nazwę na ***NX_ENABLE_DUAL_PACKET_POOL** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_DUAL_PACKET_POOL_* *.|
|NX_ENABLE_DUAL_PACKET_POOL | Zdefiniowane, umożliwia stosowi używanie dwóch pul pakietów, z których jeden ma duży rozmiar ładunku i jeden o mniejszym rozmiarze ładunku. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| Zdefiniowane, włącza więcej punktów zaczepienia wywołania zwrotnego w stosie. Te funkcje wywołania zwrotnego są używane przez warstwę otoki BSD. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_ENABLE_INTERFACE_CAPABILITY| Zdefiniowane, umożliwia sterownikowi urządzenia interfejsu określenie dodatkowych informacji o możliwościach, takich jak suma kontrolna w trakcie ładowania. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| Zdefiniowany, umożliwia sprawdzenie adresu źródłowego pakietu przychodzącego. Domyślnie ta opcja jest wyłączona.|
| NX_IPSEC_ENABLE  | Zdefiniowane, umożliwia bibliotece NetX Duo obsługę operacji protokołu IPsec. Ta funkcja wymaga opcjonalnego modułu IPsec NetX Duo. Domyślnie ta funkcja nie jest włączona.            |
| NX_LITTLE_ENDIAN | Zdefiniowane, wykonuje konieczność wymiany bajtów w środowiskach little endian, aby upewnić się, że nagłówki protokołu są w prawidłowym formacie big endian. Uwaga domyślna jest zazwyczaj instalacją w ***nx_port. h***.|
|NX_MAX_PHYSICAL_INTERFACES | Określa łączną liczbę fizycznych interfejsów sieciowych na urządzeniu. Wartość domyślna to 1 i jest definiowana w ***nx_api. h***; urządzenie musi mieć co najmniej jeden interfejs fizyczny. Należy zauważyć, że nie obejmuje to interfejsu sprzężenia zwrotnego.|
| NX_NAT_ENABLE | Zdefiniowane, NetX Duo została skompilowana przy użyciu procesu NAT. Domyślnie ta opcja nie jest zdefiniowana.|
| NX_PHYSICAL_HEADER  | Określa rozmiar w bajtach fizycznego nagłówka ramki. Wartość domyślna to 16 (oparta na typowym 14-bajtowym ramce Ethernet wyrównanym do 32-bitowej granicy) i jest zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed _*_nx_api. h_*_ , na przykład _ *_nx_user. h_*. * |
| NX_PHYSICAL_TRAILER | Określa rozmiar w bajtach wystawcy pakietu fizycznego i jest zazwyczaj używany do rezerwowania magazynu dla elementów, takich jak Ethernet CRCs itp. Wartość domyślna to 4 i jest definiowana w ***nx_api. h***.|

### <a name="arp-configuration-options"></a>Opcje konfiguracji protokołu ARP

| Opcja  | Opis  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | Zdefiniowane, umożliwia NetX Duo do obrony swojego adresu IP przez wysłanie odpowiedzi ARP.|
|NX_ARP_DEFEND_INTERVAL| Definiuje interwał (w sekundach), w którym moduł ARP wysyła następny pakiet obrony w odpowiedzi na przychodzący komunikat protokołu ARP wskazujący, że adres jest w konflikcie.|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  Zmieniono nazwę na ***NX_DISABLE_ARP_AUTO_ENTRY** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ARP_AUTO_ENTRY_* *.|
|NX_ARP_EXPIRATION_RATE| Określa liczbę sekund wygaśnięcia wpisów ARP. Wartość domyślna zero wyłącza wygasanie lub przedawnianie wpisów ARP i jest zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Zmieniono nazwę na ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_* *.|
|NX_ARP_MAX_QUEUE_DEPTH | Określa maksymalną liczbę pakietów, które można umieścić w kolejce podczas oczekiwania na odpowiedź ARP. Wartość domyślna to 4 i jest definiowana w ***nx_api. h***.|
|NX_ARP_MAXIMUM_RETRIES | Określa maksymalną liczbę ponownych prób protokołu ARP bez odpowiedzi ARP. Wartość domyślna to 18 i jest definiowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_ARP_UPDATE_RATE | Określa liczbę sekund między ponownymi próbami ARP. Wartość domyślna to 10, która reprezentuje 10 sekund, i jest zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_DISABLE_ARP_AUTO_ENTRY | Zdefiniowane, wyłącza wprowadzanie informacji o żądaniu ARP w pamięci podręcznej ARP.|
|NX_DISABLE_ARP_INFO | Zdefiniowane, wyłącza zbieranie informacji o ARP.|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| Zdefiniowane, umożliwia protokółowi ARP wywołaj funkcję powiadamiania o wywołaniu zwrotnym przy wykrywaniu adresu MAC.|

### <a name="icmp-configuration-options"></a>Opcje konfiguracji protokołu ICMP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_ICMP_INFO| Zdefiniowane, wyłącza zbieranie informacji protokołu ICMP.|
|NX_DISABLE_ICMP_RX_CHECKSUM| Zdefiniowane, wyłącza obliczenia sum kontrolnych ICMPv4 i ICMPv6 dla odebranych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego może zweryfikować sumę kontrolną ICMPv4 i ICMPv6, a aplikacja nie korzysta z funkcji fragmentacji IP ani funkcji IPsec. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMP_TX_CHECKSUM | Zdefiniowane, wyłącza obliczenia sum kontrolnych ICMPv4 i ICMPv6 dla przesyłanych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego może obliczyć sumę kontrolną ICMPv4 i ICMPv6,
Aplikacja nie używa funkcji fragmentacji IP ani funkcji IPsec. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | Zdefiniowane, NetX Duo nie wysyła komunikatów o błędach ICMPv4 w odpowiedzi na warunki błędów, takie jak nieprawidłowo sformatowany nagłówek IPv4. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych ICMPv4 dla odebranych pakietów ICMP. Ta opcja jest definiowana automatycznie, jeśli ***NX_DISABLE_ICMP_RX_CHECKSUM*** jest zdefiniowana. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ICMPV4_RX_CHECKSUM_* *.|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych ICMPv4 w wysłanych pakietach ICMP. Ta opcja jest definiowana automatycznie, jeśli ***NX_DISABLE_ICMP_TX_CHECKSUM*** jest zdefiniowana. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _.</br>Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ICMPV4_TX_CHECKSUM_* *.|
|NX_ENABLE_ICMP_ADDRESS_CHECK | Zdefiniowany adres docelowy pakietu ICMP jest sprawdzany. Domyślne ustawienie to Wyłączony. Żądanie echa ICMP przeznaczone do adresu IP emisji lub multiemisji IP zostanie odrzucone w trybie dyskretnym.|

### <a name="igmp-configuration-options"></a>Opcje konfiguracji protokołu IGMP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_IGMP_INFO | Zdefiniowane, wyłącza zbieranie informacji IGMP.|
|NX_DISABLE_IGMPV2 | Zdefiniowane, wyłącza obsługę IGMPv2, a NetX Duo obsługuje tylko IGMPv1. Domyślnie ta opcja nie jest ustawiona i jest definiowana w ***nx_api. h***.|
|NX_MAX_MULTICAST_GROUPS | Określa maksymalną liczbę grup multiemisji, które mogą być sprzężone. Wartość domyślna to 7 i została zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|

### <a name="ip-configuration-options"></a>Opcje konfiguracji protokołu IP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_FRAGMENTATION | Zdefiniowane, powoduje wyłączenie fragmentacji protokołów IPv4 i IPv6 oraz logiki ponownego zestawu.|
| NX_DISABLE_IPV4     | Zdefiniowane, wyłącza funkcje protokołu IPv4. Tej opcji można użyć do kompilowania NetX Duo tylko do suupport protokołu IPv6. Domyślnie ta opcja nie jest zdefiniowana. |
| NX_DISABLE_IP_INFO | Zdefiniowane, wyłącza zbieranie informacji o adresie IP.|
|NX_DISABLE_IP_RX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej dla odebranych pakietów IPv4. Jest to przydatne, jeśli urządzenie sieciowe może zweryfikować sumę kontrolną IPv4, a aplikacja nie będzie mogła używać fragmentacji IP ani protokołu IPsec.|
|NX_DISABLE_IP_TX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej w wysłanych pakietach IPv4. Jest to przydatne w sytuacjach, w których bazowe urządzenie sieciowe może generować sumę kontrolną nagłówka IPv4, a aplikacja nie powinna używać fragmentacji IP ani protokołu IPsec.|
|NX_DISABLE_LOOPBACK_INTERFACE | Zdefiniowane, wyłącza obsługę NetX Duo dla interfejsu sprzężenia zwrotnego.|
|NX_DISABLE_RX_SIZE_CHECKING | Zdefiniowane, wyłącza sprawdzanie rozmiaru odebranych pakietów.|
|NX_ENABLE_IP_RAW_PACKET_FILTER | Zdefiniowane, umożliwia korzystanie z funkcji filtru uzyskiwania pakietów pierwotnych IP. Aplikacje wymagające większej kontroli nad typem pierwotnych pakietów IP do odebrania mogą używać tej funkcji. Funkcja filtr pakietów RAW protokołu IP obsługuje również niesformatowaną operację gniazda w warstwie zgodności BSD. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_ENABLE_IP_STATIC_ROUTING | Zdefiniowane, umożliwia routing statyczny IPv4, w którym adres docelowy można przypisać do określonego adresu następnego przeskoku. Domyślnie Statyczny routing IPv4 jest wyłączony.|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | Zdefiniowane, umożliwia logikę ponownego asemblowania protokołów IPv4 i IPv6 po odebraniu fragmentu IP. Domyślnie ta opcja nie jest zdefiniowana.|
|NX_IP_MAX_REASSEMBLY_TIME | Symbol kontrolujący maksymalny czas, w którym można ponownie połączyć fragment IPv4 i fragment IPv6. Należy pamiętać, że wartość zdefiniowana w tym miejscu zastępuje zarówno ***NX_IPV4_MAX_REASSEMBLY_TIME** _ i _ *_NX_IPV6_MAX_REASSEMBLY_TIME_* *.|
|NX_IP_PERIODIC_RATE | Zdefiniowane, określa liczbę cykli czasomierza ThreadX w jednej sekundzie. Wartość domyślna jest pochodną od symbolu ThreadX ***TX_TIMER_TICKS_PER_SECOND,** a domyślnie ma wartość 100 (czasomierz 10 ms). Podczas modyfikowania tej wartości aplikacje sprawdzają poprawność w przypadku, gdy pozostałe moduły NetX Duo uzyskują informacje o chronometrażu od _ *_NX_IP_PERIODIC_RATE_.**|
|NX_IP_RAW_MAX_QUEUE_DEPTH | Symbol kontrolujący liczbę nieprzetworzonych pakietów IP można umieścić w kolejce dla nieprzetworzonej kolejki odbierania pakietów. Domyślnie wartość jest równa 20.| 
|NX_IP_ROUTING_TABLE_SIZE | Zdefiniowane, ustawia maksymalną liczbę wpisów w statycznej tabeli routingu IPv4, która jest listą interfejsu wychodzącego i adresów następnego przeskoku dla danego adresu docelowego. Wartość domyślna to 8 i została zdefiniowana w ***nx_api. h.** _ Ten symbol jest używany tylko wtedy, gdy jest zdefiniowany _ *_NX_ENABLE_IP_STATIC_ROUTING_**.|
|NX_IPV4_MAX_REASSEMBLY_TIME | Symbol kontrolujący maksymalny czas, który może ponownie połączyć fragment IPv4. Należy zauważyć, że wartość zdefiniowana w NX_IP_MAX_REASSEMBLY_TIME zastępuje tę wartość.|

### <a name="packet-configuration-options"></a>Opcje konfiguracji pakietu

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | Zdefiniowane, powoduje wyłączenie logiki łańcucha pakietów. Domyślnie to nie jest zdefiniowane.|
|NX_DISABLE_PACKET_INFO | Zdefiniowane, powoduje wyłączenie zbierania informacji o puli pakietów.|
|NX_ENABLE_LOW_WATERMARK | Zdefiniowane, włącza funkcję dolnego limitu puli pakietów NetX Duo. Aplikacja ustawia dolny limit wartości. W przypadku odebrania pakietów TCP, jeśli zostanie osiągnięty dolny limit puli pakietów, NetX Duo dyskretnie odrzuca pakiet, zwalniając go, uniemożliwiając zablokowanie puli pakietów. Domyślnie ta funkcja nie jest włączona.|
|NX_ENABLE_PACKET_DEBUG_INFO | Zdefiniowane, rejestruje informacje debugowania pakietu.|
|NX_PACKET_ALIGNMENT | Zdefiniowane, określa wymaganie wyrównania (w bajtach) dla początkowego adresu obszaru ładunku pakietu. Ta opcja jest przestarzała ***NX_PACKET_HEADER_PAD** _ i _ *_NX_PACKET_HEADER_PAD_SIZE_* *. Domyślnie ta opcja jest zdefiniowana jako 4, co oznacza, że adres początkowy obszaru ładunku jest wyrównany do 4 bajtów.|
|NX_PACKET_HEADER_PAD | Zdefiniowane, umożliwia uzupełnienie do końca bloku sterowania NX_PACKET. Liczba słów ULONG do zablokowania jest definiowana przez ***NX_PACKET_HEADER_PAD_SIZE** _. Zwróć uwagę, że ta opcja jest amortyzowana przez _ *_NX_PACKET_ALIGNMENT_* *.|
|NX_PACKET_HEADER_PAD_SIZE | Ustawia liczbę słów ULONG, które mają być uzupełnione do struktury NX_PACKET, co pozwala na rozpoczęcie obszaru ładunku pakietu przy odpowiednim wyrównaniu. Ta funkcja jest przydatna, gdy Odbierz punkty deskryptorów buforów bezpośrednio do obszaru ładunku NX_PACKET, a logika odbierania interfejsu sieciowego lub logika operacji pamięci podręcznej oczekuje, że adres początkowy buforu spełnia pewne wymagania dotyczące wyrównania. Ta wartość jest prawidłowa tylko wtedy, gdy jest zdefiniowany znak ***NX_PACKET_HEADER_PAD** _. Zwróć uwagę, że ta opcja jest przestarzała przez _ *_NX_PACKET_ALIGNMENT_* *.|

### <a name="rarp-configuration-options"></a>RARP opcje konfiguracji

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_RARP_INFO | Zdefiniowane, wyłącza zbieranie informacji RARP.|

### <a name="tcp-configuration-options"></a>Opcje konfiguracji protokołu TCP

| Opcja | Opis |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | Zdefiniowane, wyłącza przetwarzanie Reset podczas rozłączania, gdy podana wartość limitu czasu zostanie określona jako ***NX_NO_WAIT***.|
|NX_DISABLE_TCP_INFO | Zdefiniowane, wyłącza zbieranie informacji TCP.|
|NX_DISABLE_TCP_RX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej dla odebranych pakietów TCP. Jest to przydatne tylko w sytuacjach, w których warstwa linku ma niezawodną sumę kontrolną lub przetwarzanie CRC, albo sterownik interfejsu może zweryfikować sumę kontrolną protokołu TCP w sprzęcie, a aplikacja nie korzysta z protokołu IPsec.|
|NX_DISABLE_TCP_TX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej do wysyłania pakietów TCP. Jest to przydatne tylko w sytuacjach, w których węzeł sieci odbiorczej otrzymał wyłączone logiki sum kontrolnych TCP lub źródłowy sterownik sieciowy może generować sumę kontrolną TCP, a aplikacja nie korzysta z protokołu IPsec.|
|NX_ENABLE_TCP_KEEPALIVE | Zdefiniowany, włącza opcjonalny czasomierz aktywności TCP. Ustawienia domyślne nie są włączone.|
|NX_ENABLE_TCP_MSS_CHECK | Zdefiniowane, umożliwia weryfikację minimalnej liczby elementów równorzędnych przed zaakceptowaniem połączenia TCP. Aby użyć tej funkcji, należy zdefiniować symbol ***NX_ENABLE_TCP_MSS_MINIMUM*** . Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| Zdefiniowane, umożliwia aplikacji zainstalowanie funkcji wywołania zwrotnego, która jest wywoływana, gdy głębokość kolejki przesyłania protokołu TCP nie przekracza maksymalnej wartości. To wywołanie zwrotne służy jako wskazanie, że gniazdo TCP jest gotowe do przesyłania większej ilości danych. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_TCP_WINDOW_SCALING | Włącza opcję skalowania okna dla aplikacji TCP. Jeśli jest zdefiniowany, opcja skalowania okna jest negocjowana podczas fazy połączenia TCP, a aplikacja może określić rozmiar okna większy niż 64 KB. Ustawienie domyślne nie jest włączone (nie określono).|
|NX_MAX_LISTEN_REQUESTS | Określa maksymalną liczbę żądań nasłuchiwania serwera. Wartość domyślna to 10 i została zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_ACK_EVERY_N_PACKETS | Określa liczbę pakietów TCP do odebrania przed wysłaniem potwierdzenia. Uwaga Jeśli ***NX_TCP_IMMEDIATE_ACK** _ jest włączona, ale _ *_NX_TCP_ACK_EVERY_N_PACKETS_** nie jest, wartość ta jest automatycznie ustawiana na 1 w celu zapewnienia zgodności z poprzednimi wersjami.|
|NX_TCP_ACK_TIMER_RATE | Określa, w jaki sposób liczba cykli systemu (NX_IP_PERIODIC_RATE) jest dzielona, aby obliczyć szybkość czasomierza dla przetwarzania opóźnionego ACK protokołu TCP. Wartość domyślna to 5, która reprezentuje 200ms i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_ENABLE_KEEPALIVE | Zmieniono nazwę na ***NX_ENABLE_TCP_KEEPALIVE** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_TCP_KEEPALIVE_* *.|
|NX_TCP_ENABLE_MSS_CHECK | Zmieniono nazwę na ***NX_ENABLE_TCP_MSS_CHECK** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_TCP_MSS_CHECK._**|
|NX_TCP_ENABLE_WINDOW_SCALING | Zmieniono nazwę na ***NX_ENABLE_TCP_WINDOW_SCALING** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_TCP_WINDOW_SCALING_* *.|
|NX_TCP_FAST_TIMER_RATE | Określa, jak liczba wewnętrznych taktów NetX Duo (NX_IP_PERIODIC_RATE) jest dzielona w celu obliczenia szybkości szybkiego czasomierza TCP. Szybki Zegar TCP jest używany do kierowania różnych czasomierzy TCP, w tym czasomierza opóźnionego ACK. Wartość domyślna to 10, która reprezentuje 100 ms przy założeniu, że czasomierz ThreadX jest uruchomiony w 10 ms. Ta wartość jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_IMMEDIATE_ACK| Zdefiniowane, włącza opcjonalne przetwarzanie odpowiedzi protokołu TCP natychmiastowe potwierdzenie. Definiowanie tego symbolu jest równoznaczne z zdefiniowaniem  ***NX_TCP_ACK_EVERY_N_PACKETS*** równego 1.|
|NX_TCP_KEEPALIVE_INITIAL | Określa liczbę sekund braku aktywności przed aktywowaniem czasomierza utrzymywania aktywności. Wartość domyślna to 7200, która reprezentuje 2 godziny, i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_KEEPALIVE_RETRIES | Określa, ile ponownych prób jest dozwolonych, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_KEEPALIVE_RETRY | Określa liczbę sekund między ponownymi próbami czasomierza aktywności, przy założeniu, że druga strona połączenia nie odpowiada. Wartość domyślna to 75, która reprezentuje 75 sekund między ponownymi próbami i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol definiujący maksymalną liczbę pakietów TCP poza kolejnością, które można przechowywać w kolejce odbioru gniazda TCP. Ten symbol może służyć do ograniczania liczby pakietów umieszczonych w kolejce w gnieździe odbioru TCP, uniemożliwiając Starved puli pakietów. Domyślnie ten symbol nie jest zdefiniowany, więc nie ma żadnego limitu liczby pakietów poza kolejnością w gnieździe TCP.|
|NX_TCP_MAXIMUM_RETRIES | Określa, ile ponownych prób transmisji danych jest dozwolonych, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_MAXIMUM_RX_QUEUE | Symbol, który definiuje maksymalną kolejkę odbierania dla gniazd TCP Sockets. Ta funkcja jest włączona przez ***NX_ENABLE_LOW_WATERMARK***.|
|NX_TCP_MAXIMUM_TX_QUEUE | Określa maksymalną głębokość kolejki transmisji protokołu TCP przed wstrzymaniem lub odrzuceniem żądań wysłania protokołu TCP. Wartość domyślna to 20, co oznacza, że maksymalnie 20 pakietów może znajdować się w kolejce transmisji w danym momencie. Zwróć uwagę na to, że pakiety pozostają w kolejce transmisji do momentu potwierdzenia, który obejmuje niektóre lub wszystkie dane pakietu są otrzymywane od drugiej strony połączenia. Ta stała jest definiowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_MSS_MINIMUM | Symbol, który definiuje minimalną wartość parametru NetX Duo akceptowaną przez moduł TCP. Ta funkcja jest włączona przez ***NX_ENABLE_TCP_MSS_CHECK***.|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | Zmieniono nazwę na ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_* *.|
|NX_TCP_RETRY_SHIFT | Określa sposób zmiany okresu ponownego przesyłania czasu między ponownymi próbami. Jeśli ta wartość wynosi 0, początkowy limit czasu ponownego przesyłania jest taki sam, jak kolejne limity czasu ponownego przesyłania. Jeśli ta wartość jest równa 1, każde kolejne ponowne przesłanie jest dwa razy dłuższe. Jeśli ta wartość jest równa 2, każdy kolejny limit czasu ponownego przesyłania jest dłuższy niż cztery razy. Wartość domyślna to 0 i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|
|NX_TCP_TRANSMIT_TIMER_RATE | Określa, jak liczba cykli systemu (***NX_IP_PERIODIC_RATE** _) jest podzielona, aby obliczyć szybkość czasomierza dla przetwarzania ponawiania prób transmisji protokołu TCP. Wartość domyślna to 1, która reprezentuje 1 sekundę, i jest zdefiniowana w _*_nx_tcp. h_*_. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.|

### <a name="udp-configuration-options"></a>Opcje konfiguracji protokołu UDP

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_UDP_INFO | Zdefiniowane, wyłącza zbieranie informacji o UDP.|
|NX_DISABLE_UDP_RX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych UDP dla przychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego może zweryfikować sumę kontrolną nagłówka UDP w sprzęcie, a aplikacja nie włącza logiki protokołu IPsec lub fragmentacji adresów IP.|
|NX_DISABLE_UDP_TX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych UDP dla wychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego może obliczać sumę kontrolną nagłówka UDP i wstawiać wartość w nagłówku IP przed przekazaniem danych, a aplikacja nie włącza logiki protokołu IPsec lub fragmentacji adresów IP.|

### <a name="ipv6-options"></a>Opcje protokołu IPv6  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_IPV6 | Wyłącza funkcję IPv6 podczas kompilowania biblioteki NetX Duo. W przypadku aplikacji, które nie wymagają protokołu IPv6, pozwala to uniknąć ściągania kodu i dodatkowego miejsca do magazynowania potrzebnego do obsługi protokołu IPv6.|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | Zdefiniowane, wyłącza odnajdywanie MTU ścieżki, który jest używany do określenia maksymalnej MTU w ścieżce do obiektu docelowego w tabeli docelowej hosta NetX Duo. Dzięki temu Host NetX Duo może wysłać największy możliwy pakiet, który nie wymaga fragmentacji. Domyślnie ta opcja jest zdefiniowana (Jednostka MTU ścieżki jest wyłączona).|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | Zdefiniowane, umożliwia wywoływanie funkcji wywołania zwrotnego, gdy adres IPv6 zostanie zmieniony. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_IPV6_MULTICAST | Zdefiniowane, włącza funkcję sprzężenia multiemisji IPv6/opuszczenie. Domyślnie ta opcja nie jest włączona.|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | Zdefiniowane, włącza funkcję odnajdywania MTU ścieżki IPv6. Domyślnie ta opcja nie jest włączona.|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | Zmieniono nazwę na ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_* *.|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | Określa liczbę wpisów w tabeli routingu IPv6. Dla domyślnego routera jest wymagany wpis co najmniej. Zdefiniowane w ***nx_api. h***, wartość domyślna to 8.|
|NX_IPV6_DESTINATION_TABLE_SIZE | Określa liczbę wpisów w tabeli docelowej IPv6. Przechowuje informacje o adresach następnego przeskoku dla adresów IPv6. Zdefiniowane w ***nx_api. h***, wartość domyślna to 8.|
|NX_IPV6_MAX_REASSEMBLY_TIME | Symbol kontrolujący maksymalny dozwolony czas ponownego tworzenia fragmentu IPv6.|
|NX_IPV6_MULTICAST_ENABLE | Zmieniono nazwę na ***NX_ENABLE_IPV6_MULTICAST** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ENABLE_IPV6_MULTICAST_* *.|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | Określa rozmiar tabeli prefiksów. Informacje o prefiksie są uzyskiwane z anonsów routera i są częścią konfiguracji adresu IPv6. Zdefiniowane w ***nx_api. h***, wartość domyślna to 8.|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | Zdefiniowane, umożliwia NetX Duo wyłączenie funkcji automatycznej konfiguracji adresu bezstanowego. Domyślnie ta opcja nie jest włączona.|
|NX_MAX_IPV6_ADDRESSES | Określa liczbę wpisów w puli adresów IPv6. Podczas konfigurowania interfejsu NetX Duo używa wpisów IPv6 z puli. Wartość domyślna to (NX_MAX_PHYSICAL_INTERFACES \* 3), aby każdy interfejs miał co najmniej jeden lokalny adres i dwa adresy globalne. Należy pamiętać, że wszystkie interfejsy współużytkują pulę adresów IPv6.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Określa interwał oczekiwania w taktach czasomierza, aby zresetować jednostkę MTU ścieżki dla określonego elementu docelowego w tabeli docelowej. Jeśli ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY*** jest zdefiniowany, definiowanie tego symbolu nie ma żadnego wpływu.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Symbol określający interwał oczekiwania (w sekundach) resetowania wartości MTU ścieżki dla wpisu tabeli docelowej. Jest on prawidłowy tylko wtedy, gdy ***NX_ENABLE_IPV6_PATH_MTU_DISCOVERY*** jest zdefiniowany. Domyślnie ta wartość jest ustawiona na 600 (w sekundach).|

### <a name="neighbor-cache-configuration-options"></a>Opcje konfiguracji pamięci podręcznej sąsiadów

| Opcja  | Opis  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | Określa opóźnienie w sekundach przed wysłaniem pierwszego żądania dla wpisu pamięci podręcznej w nieodświeżonym stanie. Zdefiniowane w ***nx_nd_cache. h***, wartość domyślna to 5.|
|NX_DISABLE_IPV6_DAD | Zdefiniowana, ta opcja powoduje wyłączenie wykrywania zduplikowanych adresów (DAD) podczas przypisywania adresów IPv6. Adresy są ustawiane przez konfigurację ręczną lub przez autokonfigurację adresów bezstanowych.|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | Zdefiniowana, ta opcja uniemożliwia NetX Duo przed usunięciem starszych wpisów tabeli pamięci podręcznej przed upływem limitu czasu, aby zwolnić miejsce na nowe wpisy, gdy tabela jest pełna. Wpisy statyczne i routery nigdy nie są czyszczone.|
|NX_IPV6_DAD_TRANSMITS | Określa liczbę komunikatów żądania sąsiada, które mają zostać wysłane przed NetX Duo oznacza adres interfejsu jako prawidłowy. Jeśli ***NX_DISABLE_IPV6_DAD** _ jest zdefiniowany (tata wyłączony), ustawienie tej opcji nie ma żadnego efektu. Alternatywnie, wartość zero (0) wyłącza Tato, ale pozostawia funkcje DAD w NetX Duo. Zdefiniowane w _ *_nx_api. h_* *, wartość domyślna to 3.|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | Zmieniono nazwę na ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_* *.|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | Określa liczbę wpisów w tabeli pamięci podręcznej sąsiadów IPv6. Zdefiniowane w ***nx_nd_cache. h***, wartość domyślna to 16.|
|NX_MAX_MULTICAST_SOLICIT | Określa liczbę komunikatów żądań sąsiada NetX Duo przesyłanych w ramach protokołu IPv6 Neighbor Discovery w przypadku, gdy wymagane jest mapowanie między adresem IPv6 i adresem MAC. Zdefiniowane w ***nx_nd_cache. h***, wartość domyślna to 3.|
|NX_MAX_UNICAST_SOLICIT | Określa liczbę komunikatów żądań sąsiada NetX Duo, które są przesyłane w celu określenia możliwości uzyskania określonego sąsiada. Zdefiniowane w ***nx_nd_cache. h***, wartość domyślna to 3.|
|NX_ND_MAX_QUEUE_DEPTH | Symbol definiujący maksymalną liczbę pakietów umieszczonych w kolejce w celu rozpoznania pamięci podręcznej ND. Domyślnie ten symbol jest ustawiony na 4.|
|NX_REACHABLE_TIME | Określa limit czasu (w sekundach), po którym wpis pamięci podręcznej ma istnieć w stanie OSIĄGALNy bez pakietów odebranych z docelowego adresu IPv6 pamięci podręcznej. Zdefiniowane w ***nx_nd_cache. h***, wartość domyślna to 30.|
|NX_RETRANS_TIMER  | Określa w milisekundach Długość opóźnienia między pakietami żądań wysyłanymi przez NetX Duo. Zdefiniowane w ***nx_nd_cache. h***, wartość domyślna to 1000.|
| NXDUO_DISABLE_DAD | Zmieniono nazwę na ***NX_DISABLE_IPV6_DAD** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_IPV6_DAD_* *.|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | Zmieniono nazwę na ***NX_IPV6_DAD_TRANSMITS** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_IPV6_DAD_TRANSMITS_* *.|

### <a name="miscellaneous-icmpv6-configuration-options"></a>Różne opcje konfiguracji protokołu ICMPv6

| Opcja  | Opis  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | Zdefiniowane, wyłącza funkcję NetX Duo wysyłającą komunikat o błędzie ICMPv6 w odpowiedzi na pakiet problemu (np. nieprawidłowo sformatowany nagłówek lub typ nagłówka pakietu jest przestarzały) otrzymany z innego hosta.|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | Zdefiniowane, wyłącza przetwarzanie pakietów przekierowywania ICMPv6. NetX Duo domyślnie przetwarza komunikaty i aktualizuje tabelę docelową przy użyciu informacji o adresie IP następnego przeskoku.|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | Zdefiniowane, wyłącza NetX Duo z przetwarzania informacji odebranych w pakietach anonsów routera IPv6.|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | Zdefiniowane, wyłącza NetX Duo od wysyłania komunikatów żądania routera IPv6 w regularnych odstępach czasu do routera.|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych ICMPv6 dla odebranych pakietów ICMP.|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_CMPV6_RX_CHECKSUM_* *.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Definiuje, wyłącza i oblicza sumę kontrolną ICMPv6 w wysłanych pakietach ICMP.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ICMPV6_TX_CHECKSUM_* *.|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | Zdefiniuj maksymalną liczbę żądań routera wysyłanych przez hosta do momentu odebrania odpowiedzi routera. Jeśli odpowiedź nie zostanie odebrana, host nie zawiera żadnego routera. Wartość domyślna to 3.|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | Określa maksymalne opóźnienie początkowej żądania routera w sekundach.|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | Określa interwał między dwoma komunikatami żądania routera. Wartość domyślna to 4.|
|NXDUO_DESTINATION_TABLE_SIZE | Zmieniono nazwę na ***NX_IPV6_DESTINATION_TABLE_SIZE** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_IPV6_DESTINATION_TABLE_SIZE_* *.|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ICMPV6_ERROR_MESSAGE_* *.|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _. Mimo że jest to nadal obsługiwane, zaleca się, aby nowe projekty używały _ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_**|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| Zmieniono nazwę na ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_* *.|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | Zmieniono nazwę na ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_* *.|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | Zmieniono nazwę na ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do użycia _ *_NX_ICMPV6_MAX_RTR_SOLICITATIONS_* *.|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | Zmieniono nazwę na ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _. Ten symbol jest amortyzowany. Mimo że jest to nadal obsługiwane, zaleca się, aby nowe projekty używały _ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_**|

## <a name="netx-duo-version-id"></a>Identyfikator wersji NetX Duo

Bieżąca wersja NetX Duo jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania. Możesz uzyskać wersję NetX Duo z badania pliku **nx_port. h** . Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję NetX Duo, badając ciąg globalny _* *_nx_version_id_*_ w _ *_nx_port. h_* *.

Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych przedstawionych poniżej zdefiniowanych w ***nx_api. h***.

Te stałe określają bieżącą wersję produktu według nazwy i wersję główną i pomocniczą produktu.

\#Zdefiniuj EL_PRODUCT_NETXDUO  
\#Zdefiniuj NETXDUO_MAJOR_VERSION  
\#Zdefiniuj NETXDUO_MINOR_VERSION