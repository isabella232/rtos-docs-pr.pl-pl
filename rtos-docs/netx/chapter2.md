---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem stosu sieci o wysokiej wydajności Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80d6ba18f47ad2b017dfa32260c83ba074a6dbac
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821541"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem stosu sieci o wysokiej wydajności Azure RTO NetX.

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Projektowanie osadzone jest zwykle wykonywane na komputerach hostów z systemem Windows lub Linux (UNIX). Gdy aplikacja zostanie skompilowana, połączona, a plik wykonywalny jest generowany na hoście, zostanie pobrany na docelowy sprzęt do wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia deweloperskiego. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM). Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem). Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy dla NetX jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

NetX wymaga od 5 kilobajtów do 45 Read-Only KB pamięci (ROM) w miejscu docelowym. Dla stosu wątku NetX i innych globalnych struktur danych wymagane są inne od 1 do 5 kilobajtów pamięci RAM docelowego.

Ponadto NetX wymaga użycia dwóch obiektów czasomierza ThreadX i jednego obiektu mutex ThreadX. Te obiekty są używane do okresowego przetwarzania i ochrony wątków w stosie protokołu NetX.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO NetX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/netx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

- ***nx_api. h***: plik nagłówkowy C zawierający wszystkie równe systemowe, struktury danych i prototypy usługi.
- ***nx_port. h***: plik nagłówkowy C zawierający wszystkie narzędzia deweloperskie oraz definicje i struktury danych specyficzne dla elementów docelowych.  
- Plik ***demo_netx. c***: c zawierający małą aplikację demonstracyjną.
- ***NX. a (lub NX. lib)** _: wersja binarna biblioteki NetX C, która jest dystrybuowana z pakietem _standard *.             |

## <a name="netx-installation"></a>Instalacja NetX

Możesz zainstalować NetX przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium NetX na komputerze:

```c
    git clone https://github.com/azure-rtos/netx
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku **Pobierz** na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki NetX na stronie frontonu repozytorium online.

> [!IMPORTANT]
> Oprogramowanie aplikacji wymaga dostępu do pliku biblioteki NetX (zazwyczaj ***NX. a** _ lub _*_NX. lib_*_) oraz plików C include _ *_nx_api. h i nx_port. h_* *. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do obszaru projektowania aplikacji.

## <a name="using-netx"></a>Korzystanie z NetX

Aby użyć NetX, kod aplikacji musi zawierać znak ***nx_api. h** _ podczas kompilacji i łączyć się z biblioteką NetX _*_NX. a_*_ (lub _ *_NX. lib_*) *.

Poniżej przedstawiono cztery kroki wymagane do kompilowania aplikacji NetX:

1. Uwzględnij plik ***nx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług NetX Services lub struktur danych.
1. Zainicjuj system NetX przez wywołanie ***nx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.  
1. Utwórz wystąpienie adresu IP, Włącz protokół ARP (Address Resolution Protocol), w razie potrzeby, i wszelkie gniazda po wywołaniu ***nx_system_initialize*** .  
1. Skompiluj Źródło aplikacji i połącz je z biblioteką uruchomieniową NetX ***NX. a** _ (lub _ *_NX. lib_* *). Obraz wyników można pobrać do elementu docelowego i wykonać!

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port NetX jest dostarczany z co najmniej jednym przykładem wykonywanym w rzeczywistej sieci lub za pośrednictwem symulowanego sterownika sieciowego. Zawsze dobrym pomysłem jest rozpoczęcie pierwszego uruchomienia systemu przykładowego.

Jeśli przykładowy system nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić ten problem:

1. Określ, jaka część przykładu jest uruchomiona.
2. Zwiększ rozmiary stosu w nowych wątkach aplikacji.
3. Ponownie skompiluj bibliotekę NetX z odpowiednimi opcjami debugowania wymienionymi w sekcji opcji konfiguracji.
4. Sprawdź strukturę **NX_IP** , aby sprawdzić, czy pakiety są wysyłane lub odbierane.
5. Sprawdź domyślną pulę pakietów, aby sprawdzić, czy są dostępne pakiety.
6. Upewnij się, że sterownik sieciowy dostarcza pakiety ARP i IP ze swoimi nagłówkami w 4-bajtowych granicach dla aplikacji wymagających łączności IP.
7. Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie. Takie informacje powinny być przydatne dla inżynierów pomocy technicznej.

Wykonaj procedury opisane w temacie [centrum pomocy technicznej](about-this-guide.md) , aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki NetX i aplikacji przy użyciu NetX istnieje kilka opcji konfiguracji. Opcje konfiguracji można definiować w źródle aplikacji, w wierszu polecenia lub w pliku ***nx_user. h*** , o ile nie określono inaczej.

> [!IMPORTANT]
> Opcje zdefiniowane w ***nx_user. h** _ są stosowane tylko wtedy, gdy aplikacja i Biblioteka NetX zostały skompilowane przy użyciu _ *NX_INCLUDE_USER_DEFINE_FILE** zdefiniowanej.

W poniższych sekcjach wymieniono opcje konfiguracji dostępne w NetX.

### <a name="system-configuration-options"></a>Opcje konfiguracji systemu  

| Opcja  | Opis  |
|---|---|
| X_DEBUG | Zdefiniowane, umożliwia opcjonalne informacje debugowania drukowania dostępne ze sterownika sieci Ethernet w pamięci RAM. |
| NX_DISABLE_ERROR_CHECKING | Zdefiniowane, usuwa interfejs API podstawowego NetX sprawdzanie błędów i zwiększa wydajność. Kody powrotne interfejsu API, które nie mają wpływ na wyłączanie sprawdzania błędów, są wymienione w pogrubionym kroju pisma w definicji interfejsu API. Ta definicja jest zwykle używana po debugowaniu aplikacji i w przypadku zwiększenia wydajności i zmniejszenia rozmiaru kodu. |
| NX_DRIVER_DEFERRED_PROCESSING | Zdefiniowane, umożliwia obsługę pakietów sterownika sieci odroczonej. Dzięki temu sterownik sieciowy może umieścić pakiet w wystąpieniu IP i mieć rzeczywistą procedurę przetwarzania wywoływaną z wątku pomocnika wewnętrznego adresu IP NetX. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | Włącza więcej punktów zaczepienia wywołania zwrotnego w stosie. Te funkcje wywołania zwrotnego są używane przez warstwę otoki BSD. Domyślnie ta opcja nie jest zdefiniowana. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | Zdefiniowany, umożliwia sprawdzenie adresu źródłowego pakietu przychodzącego. Domyślnie ta opcja jest wyłączona. |
| NX_LITTLE_ENDIAN | Zdefiniowane, wykonuje konieczność wymiany bajtów w środowiskach little endian, aby upewnić się, że nagłówki protokołu są w prawidłowym formacie big endian. Uwaga domyślna jest zazwyczaj instalacją w ***nx_port. h***. |
| NX_MAX_PHYSICAL_INTERFACES | Określa łączną liczbę fizycznych interfejsów sieciowych na urządzeniu. Wartość domyślna to 1 i jest definiowana w ***nx_api. h***. Urządzenie musi mieć co najmniej jeden interfejs fizyczny. Należy zauważyć, że nie obejmuje to interfejsu sprzężenia zwrotnego. |
| NX_PHYSICAL_HEADER | Określa rozmiar w bajtach fizycznego nagłówka ramki. Wartość domyślna to 16 (oparta na typowym 14-bajtowym ramce Ethernet wyrównanym do 32-bitowej granicy) i jest zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed _*_nx_api. h_*_ , na przykład _ *_nx_user. h_*. * |

### <a name="arp-configuration-options"></a>Opcje konfiguracji protokołu ARP  

| Opcja  | Opis  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | Zdefiniowane, umożliwia NetX obrony swojego adresu IP, wysyłając odpowiedź ARP. |
| NX_ARP_DEFEND_INTERVAL | Definiuje interwał (w sekundach), w którym moduł ARP wysyła następny pakiet obrony w odpowiedzi na przychodzący komunikat protokołu ARP wskazujący, że adres jest w konflikcie. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | Zmieniono nazwę na **NX_DISABLE_ARP_AUTO_ENTRY**. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do korzystania z **NX_DISABLE_ARP_AUTO_ENTRY**.
| NX_ARP_EXPIRATION_RATE | Określa liczbę sekund wygaśnięcia wpisów ARP. Wartość domyślna zero wyłącza wygasanie lub przedawnianie wpisów ARP i jest zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona.
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Zmieniono nazwę na **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do korzystania z **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. |
| NX_ARP_MAX_QUEUE_DEPTH | Określa maksymalną liczbę pakietów, które można umieścić w kolejce podczas oczekiwania na odpowiedź ARP. Wartość domyślna to 4 i jest definiowana w ***nx_api. h***. |
| NX_ARP_MAXIMUM_RETRIES | Określa maksymalną liczbę ponownych prób protokołu ARP bez odpowiedzi ARP. Wartość domyślna to 18 i jest definiowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_ARP_UPDATE_RATE | Określa liczbę sekund między ponownymi próbami ARP. Wartość domyślna to 10, która reprezentuje 10 sekund, i jest zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_DISABLE_ARP_AUTO_ENTRY | Zdefiniowane, wyłącza wprowadzanie informacji o żądaniu ARP w pamięci podręcznej ARP. |
| NX_DISABLE_ARP_INFO | Zdefiniowane, wyłącza zbieranie informacji o ARP. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | Zdefiniowane, umożliwia protokółowi ARP wywołaj funkcję powiadamiania o wywołaniu zwrotnym przy wykrywaniu adresu MAC. |

### <a name="icmp-configuration-options"></a>Opcje konfiguracji protokołu ICMP  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_ICMP_INFO | Zdefiniowane, wyłącza zbieranie informacji protokołu ICMP. |
| NX_DISABLE_ICMP_RX_CHECKSUM | Wyłącza Obliczanie sumy kontrolnej protokołu ICMP dla odebranych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego może zweryfikować sumę kontrolną protokołu ICMP, a aplikacja nie korzysta z funkcji fragmentacji adresów IP. Domyślnie ta opcja nie jest zdefiniowana. |
| NX_DISABLE_ICMP_TX_CHECKSUM | Wyłącza Obliczanie sum kontrolnych protokołu ICMP dla wysłanych pakietów protokołu ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego może obliczyć sumę kontrolną protokołu ICMP, a aplikacja nie korzysta z funkcji fragmentacji IP. Domyślnie ta opcja nie jest zdefiniowana. |

### <a name="igmp-configuration-options"></a>Opcje konfiguracji protokołu IGMP  

| Opcja  | Opis  |
|---|---| 
| NX_DISABLE_IGMP_INFO | Zdefiniowane, wyłącza zbieranie informacji IGMP. |
| NX_DISABLE_IGMPV2 | Zdefiniowane, wyłącza obsługę IGMPv2, a NetX obsługuje tylko IGMPv1. Domyślnie ta opcja nie jest ustawiona i jest definiowana w ***nx_api. h***. |
| NX_MAX_MULTICAST_GROUPS | Określa maksymalną liczbę grup multiemisji, które mogą być sprzężone. Wartość domyślna to 7 i została zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona. |

### <a name="ip-configuration-options"></a>Opcje konfiguracji protokołu IP

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_FRAGMENTATION | Zdefiniowane, wyłącza fragmentację IP i logikę ponownego zestawu. |
| NX_DISABLE_IP_INFO | Zdefiniowane, wyłącza zbieranie informacji o adresie IP. |
| NX_DISABLE_IP_RX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej dla odebranych pakietów IP. Jest to przydatne, jeśli urządzenie sieciowe może zweryfikować sumę kontrolną nagłówka IP, a aplikacja nie korzysta z fragmentacji adresów IP. |
| NX_DISABLE_IP_TX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej dla wysłanych pakietów IP. Jest to przydatne w sytuacjach, w których bazowe urządzenie sieciowe może generować sumę kontrolną nagłówka IP, a aplikacja nie korzysta z fragmentacji adresów IP. |
| NX_DISABLE_LOOPBACK_INTERFACE | Zdefiniowane, wyłącza obsługę NetX dla interfejsu sprzężenia zwrotnego. |
| NX_DISABLE_RX_SIZE_CHECKING | Zdefiniowane, wyłącza sprawdzanie rozmiaru odebranych pakietów. |
| NX_ENABLE_IP_STATIC_ROUTING | Zdefiniowane, umożliwia statycznego routingu IP, w którym adres docelowy może być przypisany do określonego adresu następnego przeskoku. Domyślnie statyczny Routing adresów IP jest wyłączony. |
| NX_IP_PERIODIC_RATE | Zdefiniowane, określa liczbę cykli czasomierza ThreadX w jednej sekundzie. Wartość domyślna pochodzi od symbolu ThreadX **TX_TIMER_TICKS_PER_SECOND,** który domyślnie jest ustawiony na 100 (10 ms Timer). W przypadku modyfikowania tej wartości aplikacje sprawdzają pozostałą ostrożność, ponieważ pozostałe moduły NetX uzyskują informacje o chronometrażu z **NX_IP_PERIODIC_RATE *.** |
| NX_IP_ROUTING_TABLE_SIZE | Zdefiniowane, ustawia maksymalną liczbę wpisów w statycznej tabeli routingu IP, która jest listą interfejsu wychodzącego i następnego przeskoku
adresy dla danego adresu docelowego. Wartość domyślna to 8 i została zdefiniowana w ***nx_api. h.** _ Ten symbol jest używany tylko wtedy, gdy jest zdefiniowany _ *NX_ENABLE_IP_STATIC_ROUTING**. |

### <a name="packet-configuration-options"></a>Opcje konfiguracji pakietu  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_PACKET_INFO | Zdefiniowane, powoduje wyłączenie zbierania informacji o puli pakietów. | 
| NX_PACKET_HEADER_PAD | Zdefiniowane, umożliwia uzupełnienie do końca bloku sterowania NX_PACKET. Liczba słów **ULONG** do zablokowania jest definiowana przez **NX_PACKET_HEADER_PAD_SIZE**. |
| NX_PACKET_HEADER_PAD_SIZE | Ustawia liczbę słów **ULONG** , które mają być uzupełnione do struktury NX_PACKET, co pozwala na rozpoczęcie działania obszaru ładunku pakietu
struktury. Ta funkcja jest przydatna, gdy Odbierz punkty deskryptorów buforów bezpośrednio do obszaru ładunku NX_PACKET, a logika odbierania interfejsu sieciowego lub logika operacji pamięci podręcznej oczekuje, że adres początkowy buforu spełnia pewne wymagania dotyczące wyrównania. Ta wartość jest prawidłowa tylko wtedy, gdy **NX_PACKET_HEADER_PAD** jest zdefiniowana. |

### <a name="rarp-configuration-options"></a>RARP opcje konfiguracji  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_RARP_INFO | Zdefiniowane, wyłącza zbieranie informacji RARP. |

### <a name="tcp-configuration-options"></a>Opcje konfiguracji protokołu TCP

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | Zdefiniowane, wyłącza przetwarzanie Reset podczas rozłączania, gdy podana wartość limitu czasu zostanie określona jako **NX_NO_WAIT**. |
| NX_DISABLE_TCP_INFO | Zdefiniowane, wyłącza zbieranie informacji TCP. |
| NX_DISABLE_TCP_RX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej dla odebranych pakietów TCP. Jest to przydatne tylko w sytuacjach, w których warstwa linku ma niezawodną sumę kontrolną lub przetwarzanie CRC, albo sterownik interfejsu może zweryfikować sumę kontrolną protokołu TCP na sprzęcie. |
| NX_DISABLE_TCP_TX_CHECKSUM | Zdefiniowane, powoduje wyłączenie logiki sumy kontrolnej do wysyłania pakietów TCP. Jest to przydatne tylko w sytuacjach, w których węzeł sieci odbiorczej ma wyłączony licznik sum kontrolnych TCP lub źródłowy sterownik sieciowy może generować sumę kontrolną protokołu TCP. |
| NX_ENABLE_TCP_KEEPALIVE | Zdefiniowany, włącza opcjonalny czasomierz aktywności TCP. Ustawienia domyślne nie są włączone. |
| NX_ENABLE_TCP_MSS_CHECKING | Zdefiniowane, umożliwia weryfikację minimalnej liczby elementów równorzędnych przed zaakceptowaniem połączenia TCP. Aby użyć tej funkcji, należy zdefiniować symbol **NX_ENABLE_TCP_MSS_MINIMUM** . Domyślnie ta opcja nie jest włączona. |
NX_ENABLE_TCP_WINDOW_SCALING | Włącza opcję skalowania okna dla aplikacji TCP. W przypadku zdefiniowania opcji skalowania okna jest negocjowane w fazie połączenia TCP, a aplikacja może określić rozmiar okna większy niż 64 KB. Ustawienie domyślne nie jest włączone (nie określono). |
| NX_MAX_LISTEN_REQUESTS | Określa maksymalną liczbę żądań nasłuchiwania serwera. Wartość domyślna to 10 i została zdefiniowana w ***nx_api. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona. |
| NX_TCP_ACK_EVERY_N_PACKETS | Określa liczbę pakietów TCP do odebrania przed wysłaniem potwierdzenia. Uwaga Jeśli **NX_TCP_IMMEDIATE_ACK** jest włączona, ale **NX_TCP_ACK_EVERY_N_PACKETS** nie jest, ta wartość jest automatycznie ustawiana na 1 w celu zapewnienia zgodności z poprzednimi wersjami. |
| NX_TCP_ACK_TIMER_RATE | Określa, w jaki sposób liczba cykli systemu (NX_IP_PERIODIC_RATE) jest dzielona, aby obliczyć szybkość czasomierza dla przetwarzania opóźnionego ACK protokołu TCP. Wartość domyślna to 5, która reprezentuje 200ms i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_TCP_ENABLE_KEEPALIVE | Zmieniono nazwę na **NX_ENABLE_TCP_KEEPALIVE**. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do korzystania z **NX_ENABLE_TCP_KEEPALIVE**. |
| NX_TCP_ENABLE_WINDOW_SCALING | Zmieniono nazwę na **NX_ENABLE_TCP_WINDOW_SCALING**. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do korzystania z **NX_ENABLE_TCP_WINDOW_SCALING**. |
| NX_TCP_FAST_TIMER_RATE | Określa, jak liczba wewnętrznych taktów NetX (NX_IP_PERIODIC_RATE) jest dzielona do obliczenia szybkości szybkiego czasomierza TCP. Szybki Zegar TCP jest używany do kierowania różnych czasomierzy TCP, w tym czasomierza opóźnionego ACK. Wartość domyślna to 10, która reprezentuje 100 ms przy założeniu, że czasomierz ThreadX jest uruchomiony w 10 ms. Ta wartość jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_TCP_IMMEDIATE_ACK | Zdefiniowane, włącza opcjonalne przetwarzanie odpowiedzi protokołu TCP natychmiastowe potwierdzenie. Definiowanie tego symbolu jest równoznaczne z zdefiniowaniem **NX_TCP_ACK_EVERY_N_PACKETS** równego 1. |
| NX_TCP_KEEPALIVE_INITIAL | Określa liczbę sekund braku aktywności przed aktywowaniem czasomierza utrzymywania aktywności. Wartość domyślna to 7200, która reprezentuje 2 godziny, i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_TCP_KEEPALIVE_RETRIES | Określa, ile ponownych prób jest dozwolonych, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona. |
| NX_TCP_KEEPALIVE_RETRY | Określa liczbę sekund między ponownymi próbami czasomierza aktywności, przy założeniu, że druga strona połączenia nie odpowiada. Wartość domyślna to 75, która reprezentuje 75 sekund między ponownymi próbami i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne, definiując wartość przed _ *_nx_api. h_** jest uwzględniona. |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol definiujący maksymalną liczbę pakietów TCP poza kolejnością, które mogą być przechowywane w kolejce odbioru gniazda TCP. Ten symbol może służyć do ograniczania liczby pakietów umieszczonych w kolejce w gnieździe odbioru TCP, uniemożliwiając Starved puli pakietów. Domyślnie ten symbol nie jest zdefiniowany, więc nie ma żadnego limitu liczby pakietów poza kolejnością w gnieździe TCP. |
| NX_TCP_MAXIMUM_RETRIES | Określa, ile ponownych prób transmisji danych jest dozwolonych, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_TCP_MAXIMUM_TX_QUEUE | Określa maksymalną głębokość kolejki transmisji protokołu TCP przed wstrzymaniem lub odrzuceniem żądań wysłania protokołu TCP. Wartość domyślna to 20, co oznacza, że maksymalnie 20 pakietów może znajdować się w kolejce transmisji w danym momencie. Zwróć uwagę na to, że pakiety pozostają w kolejce transmisji do momentu potwierdzenia, który obejmuje niektóre lub wszystkie dane pakietu są otrzymywane od drugiej strony połączenia. Ta stała jest definiowana w ***nx_tcp. h** _. Aplikacja może przesłonić wartość domyślną przez zdefiniowanie wartości przed uwzględnieniem _ *_nx_api. h_* *. |
| X_TCP_MSS_CHECKING_ENABLED | Zmieniono nazwę na **NX_ENABLE_TCP_MSS_CHECKING**. Mimo że jest to nadal obsługiwane, zachęcamy nowe projekty do korzystania z **NX_ENABLE_TCP_MSS_CHECKING**. |
| NX_TCP_MSS_MINIMUM | Symbol, który definiuje minimalną wartość NetX, która akceptuje moduł TCP. Ta funkcja jest włączona przez **NX_ENABLE_TCP_MSS_CHECK** |
| NX_TCP_RETRY_SHIFT | Określa sposób zmiany okresu ponownego przesyłania czasu między ponownymi próbami. Jeśli ta wartość wynosi 0, początkowy limit czasu ponownego przesyłania jest taki sam, jak kolejne limity czasu ponownego przesyłania. Jeśli ta wartość jest równa 1, każde kolejne ponowne przesłanie jest dwa razy dłuższe. Jeśli ta wartość jest równa 2, każdy kolejny limit czasu ponownego przesyłania jest dłuższy niż cztery razy. Wartość domyślna to 0 i jest zdefiniowana w ***nx_tcp. h** _. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed dołączeniem _ *_nx_api. h_* *. |
| NX_TCP_TRANSMIT_TIMER_RATE| Określa, jak liczba cykli systemu **NX_IP_PERIODIC_RATE**) jest podzielona, aby obliczyć szybkość czasomierza dla przetwarzania ponawiania prób transmisji protokołu TCP. Wartość domyślna to 1, która reprezentuje 1 sekundę, i jest zdefiniowana w **_nx_tcp. h_*_. Aplikacja może przesłonić domyślne przez zdefiniowanie wartości przed uwzględnieniem _*_nx_api. h_**. |

### <a name="udp-configuration-options"></a>Opcje konfiguracji protokołu UDP
| Opcja  | Opis  |
|---|---|
| NX_DISABLE_UDP_INFO | Zdefiniowane, wyłącza zbieranie informacji o UDP. |
| NX_DISABLE_UDP_RX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych UDP dla przychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego może zweryfikować sumę kontrolną nagłówka UDP w sprzęcie, a aplikacja nie włącza logiki fragmentacji adresów IP. |
| NX_DISABLE_UDP_TX_CHECKSUM | Zdefiniowane, wyłącza Obliczanie sum kontrolnych UDP dla wychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego może obliczać sumę kontrolną nagłówka UDP i wstawiać wartość w nagłówku IP przed przekazaniem danych, a aplikacja nie włącza logiki fragmentacji adresów IP. |

## <a name="netx-version-id"></a>Identyfikator wersji NetX

Bieżąca wersja programu NetX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji podczas wykonywania. Programista może uzyskać wersję NetX z pliku **nx_port. h** . Ponadto ten plik zawiera historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję NetX, badając ciąg globalny **_nx_version_id** w **_nx_port. h_**.  

Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych przedstawionych poniżej, które są zdefiniowane w ***nx_api. h**. *

Te stałe określają bieżącą wersję produktu według nazwy i wersję główną i pomocniczą produktu.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```