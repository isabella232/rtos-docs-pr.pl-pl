---
title: Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem stosu sieciowego o wysokiej wydajności Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 942250cf864fca3c35b97ae731549c070ac2f2f2ef3ef8897e5cbf1e705e7c6a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801807"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem stosu sieciowego o wysokiej wydajności Azure RTOS NetX.

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Opracowywanie osadzone jest zwykle wykonywane na komputerach Windows komputerach hostów z systemem Linux (Unix). Gdy aplikacja zostanie skompilowana, połączona, a plik wykonywalny zostanie wygenerowany na hoście, zostanie pobrany na docelowy sprzęt w celu wykonania.

Zazwyczaj pobieranie docelowe jest wykonywane z poziomu debugera narzędzia dewelopera. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, halt, breakpoint itp.), a także dostępu do rejestrów pamięci i procesora.

Większość debugerów narzędzi deweloperskie komunikuje się ze sprzętem docelowym za pośrednictwem połączeń debugowania na mikroukładach (OCD), takich jak JTAG (IEEE 1149.1) i tryb debugowania w tle (BDM). Debugerzy komunikują się również ze sprzętem docelowym za pośrednictwem In-Circuit emulacji (ICE). Połączenia OCD i ICE zapewniają niezawodne rozwiązania z minimalnym wtargnięciem do docelowego oprogramowania.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy netx jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

NetX wymaga od 5 KB do 45 KB pamięci Read-Only pamięci (ROM) na komputerze docelowym. Kolejne od 1 do 5 KB pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla stosu wątków NetX i innych globalnych struktur danych.

Ponadto NetX wymaga użycia dwóch obiektów czasomierza ThreadX i jednego obiektu mutex ThreadX. Te obiekty są używane do okresowego przetwarzania i ochrony wątków w stosie protokołu NetX.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS NetX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/netx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

- ***nx_api.h:*** plik nagłówkowy C zawierający wszystkie elementy systemowe, struktury danych i prototypy usług.
- ***nx_port.h:*** plik nagłówkowy C zawierający wszystkie definicje i struktury danych specyficzne dla poszczególnych narzędzi deweloperskich i docelowych.  
- ***demo_netx.c:*** plik C zawierający małą aplikację demonstracyjną.
- ***nx.a (lub nx.lib)** _: wersja binarna biblioteki NetX C dystrybuowana za pomocą pakietu _standard*.             |

## <a name="netx-installation"></a>Instalacja NetX

Platformę NetX można zainstalować, klonjąc repozytorium GitHub na maszynę lokalną. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium NetX na komputerze:

```c
    git clone https://github.com/azure-rtos/netx
```

Możesz też pobrać kopię repozytorium przy  użyciu przycisku Pobierz na GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki NetX można również znaleźć na pierwszej stronie repozytorium online.

> [!IMPORTANT]
> Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki NetX (zazwyczaj ***nx.a** _ lub _*_nx.lib_*_), a pliki dołączane w języku C _*_nx_api.h i nx_port.h_**. W tym celu należy wybrać odpowiednią ścieżkę dla narzędzi deweloperskie lub skopiować te pliki do obszaru projektowania aplikacji.

## <a name="using-netx"></a>Korzystanie z netx

Aby można było korzystać z netX, kod aplikacji musi zawierać plik ***nx_api.h** _ podczas kompilacji i połączyć go z biblioteką NetX _*_nx.a_*_ (lub _ *_nx.lib_*)*.

Poniżej przedstawiono cztery wymagane kroki tworzenia aplikacji NetX:

1. Dołącz plik ***nx_api.h*** do wszystkich plików aplikacji, które korzystają z usług NetX lub struktur danych.
1. Zaimicjuj system NetX, wywołując funkcję ***nx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.  
1. Utwórz wystąpienie adresu IP, włącz protokół rozpoznawania adresów (ARP), jeśli to konieczne, oraz wszelkie gniazda po ***nx_system_initialize*** wywoływania.  
1. Kompilowanie źródła aplikacji i łączenie za pomocą biblioteki środowiska uruchomieniowego NetX ***nx.a** _ (lub _*_nx.lib_**). Wynikowy obraz można pobrać do obiektu docelowego i wykonać.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port NetX jest dostarczany z co najmniej jednym przykładem, który jest wykonywany w rzeczywistej sieci lub za pośrednictwem symulowanego sterownika sieciowego. Zawsze dobrym pomysłem jest uruchomienie przykładowego systemu w pierwszej kolejności.

Jeśli przykładowy system nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić problem:

1. Określ, jaka część przykładu jest uruchomiona.
2. Zwiększ rozmiary stosów we wszystkich nowych wątkach aplikacji.
3. Skompiluj ponownie bibliotekę NetX przy użyciu odpowiednich opcji debugowania wymienionych w sekcji opcji konfiguracji.
4. Sprawdź strukturę **NX_IP,** aby sprawdzić, czy pakiety są wysyłane lub odbierane.
5. Sprawdź domyślną pulę pakietów, aby sprawdzić, czy są dostępne pakiety.
6. Upewnij się, że sterownik sieciowy dostarcza pakiety ARP i IP z jego nagłówkami w granicach 4-bajtowych dla aplikacji wymagających łączności IP.
7. Tymczasowo pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub zmienia się. Takie informacje powinny okazać się przydatne dla naszych inżynierów pomocy technicznej.

Postępuj zgodnie z procedurami opisanymi w [temacie Centrum obsługi](about-this-guide.md) klienta, aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki NetX i aplikacji przy użyciu narzędzia NetX. Opcje konfiguracji można zdefiniować w źródle aplikacji, w wierszu polecenia lub w pliku ***dołączania nx_user.h, chyba*** że określono inaczej.

> [!IMPORTANT]
> Opcje zdefiniowane w ***nx_user.h** _ są stosowane tylko wtedy, gdy aplikacja i biblioteka NetX są budowaną za pomocą zdefiniowanej wartości _ *NX_INCLUDE_USER_DEFINE_FILE**.

W poniższych sekcjach przedstawiono opcje konfiguracji dostępne w programie NetX.

### <a name="system-configuration-options"></a>Opcje konfiguracji systemu  

| Opcja  | Opis  |
|---|---|
| X_DEBUG | Zdefiniowano , włącza opcjonalne informacje debugowania drukowania dostępne ze sterownika sieci Ethernet pamięci RAM. |
| NX_DISABLE_ERROR_CHECKING | Zdefiniowano , usuwa podstawowy interfejs API sprawdzania błędów NetX i poprawia wydajność. Kody powrotne interfejsu API, na które nie ma wpływu wyłączenie sprawdzania błędów, są wyświetlane pogrubioną czcionką w definicji interfejsu API. Ta definicja jest zwykle używana po debugowaniu aplikacji i gdy jej użycie zwiększa wydajność i zmniejsza rozmiar kodu. |
| NX_DRIVER_DEFERRED_PROCESSING | Zdefiniowane umożliwia odroczoną obsługę pakietów sterowników sieciowych. Dzięki temu sterownik sieciowy umieszcza pakiet w wystąpieniu adresu IP i ma rzeczywistą procedurę przetwarzania o nazwie z wątku pomocnika wewnętrznego adresu IP NetX. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | Włącza więcej wpięć wywołania zwrotnego w stosie. Te funkcje wywołania zwrotnego są używane przez warstwę otoki BSD. Domyślnie ta opcja nie jest zdefiniowana. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | Zdefiniowane umożliwia sprawdzanie adresu źródłowego pakietu przychodzącego. Domyślnie ta opcja jest wyłączona. |
| NX_LITTLE_ENDIAN | Zdefiniowane, wykonuje niezbędne wymiany bajtów w środowiskach little endian, aby upewnić się, że nagłówki protokołu są we właściwym big endian formatu. Pamiętaj, że wartość domyślna jest zwykle konfigurowana ***w nx_port.h.*** |
| NX_MAX_PHYSICAL_INTERFACES | Określa łączną liczbę fizycznych interfejsów sieciowych na urządzeniu. Wartość domyślna to 1 i jest zdefiniowana w ***nx_api.h.*** Urządzenie musi mieć co najmniej jeden interfejs fizyczny. Pamiętaj, że nie obejmuje to interfejsu sprzężenia zwrotnego. |
| NX_PHYSICAL_HEADER | Określa rozmiar w bajtach fizycznego nagłówka ramki. Wartość domyślna to 16 (na podstawie typowej 14-bajtowej ramki Ethernet wyrównanej do granicy 32-bitowej) i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed _*_nx_api.h,_*_ na przykład w _ *_nx_user.h.*_* |

### <a name="arp-configuration-options"></a>Opcje konfiguracji ARP  

| Opcja  | Opis  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | Zdefiniowane umożliwia platformie NetX obronę swojego adresu IP przez wysyłanie odpowiedzi ARP. |
| NX_ARP_DEFEND_INTERVAL | Definiuje interwał, w sekundach, moduł ARP wysyła następny pakiet obrony w odpowiedzi na przychodzący komunikat ARP, który wskazuje adres w konflikcie. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | Zmieniono nazwę **na NX_DISABLE_ARP_AUTO_ENTRY**. Mimo że ta wersja jest nadal obsługiwana, zachęcamy do korzystania z nowych projektów **NX_DISABLE_ARP_AUTO_ENTRY**.
| NX_ARP_EXPIRATION_RATE | Określa liczbę sekund, przez które wpisy ARP pozostają prawidłowe. Wartość domyślna zero wyłącza wygasanie lub przedawnianie wpisów ARP i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem _ *_nx_api.h*._*
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Zmieniono nazwę **na NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. Mimo że jest ona nadal obsługiwana, zachęcamy do korzystania z nowych projektów **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. |
| NX_ARP_MAX_QUEUE_DEPTH | Określa maksymalną liczbę pakietów, które mogą być kolejkowane podczas oczekiwania na odpowiedź ARP. Wartość domyślna to 4 i jest zdefiniowana w ***nx_api.h.*** |
| NX_ARP_MAXIMUM_RETRIES | Określa maksymalną liczbę ponownych prób ARP wykonanych bez odpowiedzi ARP. Wartość domyślna to 18 i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem _*_nx_api.h_**. |
| NX_ARP_UPDATE_RATE | Określa liczbę sekund między ponownych prób ARP. Wartość domyślna to 10, która reprezentuje 10 sekund i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem _*_nx_api.h_**. |
| NX_DISABLE_ARP_AUTO_ENTRY | Zdefiniowane wyłącza wprowadzanie informacji o żądaniu ARP w pamięci podręcznej ARP. |
| NX_DISABLE_ARP_INFO | Zdefiniowane wyłącza zbieranie informacji przez usługę ARP. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | Zdefiniowane umożliwia URP wywoływanie funkcji powiadamiania o wywołaniu zwrotnych po wykryciu, że adres MAC został zaktualizowany. |

### <a name="icmp-configuration-options"></a>Opcje konfiguracji ICMP  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_ICMP_INFO | Zdefiniowane wyłącza zbieranie informacji ICMP. |
| NX_DISABLE_ICMP_RX_CHECKSUM | Wyłącza obliczanie sumy kontrolnej ICMP dla odebranych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego jest w stanie zweryfikować sumy kontrolne ICMP, a aplikacja nie używa funkcji fragmentacji adresów IP. Domyślnie ta opcja nie jest zdefiniowana. |
| NX_DISABLE_ICMP_TX_CHECKSUM | Wyłącza obliczanie sumy kontrolnej ICMP dla przesyłanych pakietów ICMP. Ta opcja jest przydatna, gdy sterownik interfejsu sieciowego jest w stanie obliczyć sumy kontrolne ICMP, a aplikacja nie używa funkcji fragmentacji adresów IP. Domyślnie ta opcja nie jest zdefiniowana. |

### <a name="igmp-configuration-options"></a>Opcje konfiguracji IGMP  

| Opcja  | Opis  |
|---|---| 
| NX_DISABLE_IGMP_INFO | Zdefiniowane wyłącza zbieranie informacji IGMP. |
| NX_DISABLE_IGMPV2 | Zdefiniowano, wyłącza obsługę protokołu IGMPv2, a netX obsługuje tylko protokół IGMPv1. Domyślnie ta opcja nie jest ustawiona i jest zdefiniowana w ***nx_api.h.*** |
| NX_MAX_MULTICAST_GROUPS | Określa maksymalną liczbę grup multiemisji, które mogą być połączone. Wartość domyślna to 7 i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem _ *_nx_api.h*._* |

### <a name="ip-configuration-options"></a>Opcje konfiguracji adresu IP

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_FRAGMENTATION | Zdefiniowane wyłącza fragmentację adresów IP i logikę ponownego zsadowania. |
| NX_DISABLE_IP_INFO | Zdefiniowane wyłącza zbieranie informacji o adresie IP. |
| NX_DISABLE_IP_RX_CHECKSUM | Zdefiniowane wyłącza logikę sumy kontrolnej dla odebranych pakietów IP. Jest to przydatne, jeśli urządzenie sieciowe jest w stanie zweryfikować sumy kontrolne nagłówka IP, a aplikacja nie używa fragmentacji adresu IP. |
| NX_DISABLE_IP_TX_CHECKSUM | Zdefiniowane wyłącza logikę sumy kontrolnej dla wysyłanych pakietów IP. Jest to przydatne w sytuacjach, w których bazowe urządzenie sieciowe jest w stanie wygenerować sumy kontrolne nagłówka IP, a aplikacja nie używa fragmentacji adresu IP. |
| NX_DISABLE_LOOPBACK_INTERFACE | Zdefiniowane wyłącza obsługę NetX dla interfejsu sprzężenia zwrotnego. |
| NX_DISABLE_RX_SIZE_CHECKING | Zdefiniowane wyłącza sprawdzanie rozmiaru odebranych pakietów. |
| NX_ENABLE_IP_STATIC_ROUTING | Zdefiniowane umożliwia routing statyczny IP, w którym adresowi docelowemu można przypisać określony adres następnego przeskoku. Domyślnie statyczny routing IP jest wyłączony. |
| NX_IP_PERIODIC_RATE | Zdefiniowane określa liczbę takt czasomierza ThreadX w ciągu jednej sekundy. Wartość domyślna jest pochodną symbolu ThreadX **TX_TIMER_TICKS_PER_SECOND,** która domyślnie jest ustawiona na 100 (czasomierz 10ms). Aplikacje powinny zachować ostrożność podczas modyfikowania tej wartości, ponieważ pozostałe moduły NetX wyprowadzają informacje o chronometrażu **z NX_IP_PERIODIC_RATE*.** |
| NX_IP_ROUTING_TABLE_SIZE | Zdefiniowane, ustawia maksymalną liczbę wpisów w tabeli routingu statycznego IP, która jest listą interfejsu wychodzącego i następnym przeskoku
adresy dla danego adresu docelowego. Wartość domyślna to 8 i jest zdefiniowana w ***nx_api.h.** _ Ten symbol jest używany tylko wtedy,*gdy zdefiniowano NX_ENABLE_IP_STATIC_ROUTING** . |

### <a name="packet-configuration-options"></a>Opcje konfiguracji pakietów  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_PACKET_INFO | Zdefiniowane wyłącza zbieranie informacji o puli pakietów. | 
| NX_PACKET_HEADER_PAD | Zdefiniowane, umożliwia wypełnienie pod koniec NX_PACKET sterowania. Liczba wyrazów **do dosyłania** w programie ULONG jest definiowana przez **NX_PACKET_HEADER_PAD_SIZE**. |
| NX_PACKET_HEADER_PAD_SIZE | Ustawia liczbę wyrazów **ULONG,** które mają zostać doliszowane do struktury NX_PACKET, dzięki czemu obszar ładunku pakietu może zaczynać się od żądanego
Wyrównanie. Ta funkcja jest przydatna, gdy deskryptory buforu odbierania wskazują bezpośrednio do obszaru ładunku usługi NX_PACKET, a logika odbierania interfejsu sieciowego lub logika operacji pamięci podręcznej oczekuje, że adres początkowy buforu spełnia określone wymagania wyrównania. Ta wartość staje się prawidłowa tylko **wtedy, NX_PACKET_HEADER_PAD** jest zdefiniowana. |

### <a name="rarp-configuration-options"></a>Opcje konfiguracji RARP  

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_RARP_INFO | Zdefiniowane wyłącza zbieranie informacji RARP. |

### <a name="tcp-configuration-options"></a>Opcje konfiguracji protokołu TCP

| Opcja  | Opis  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | Zdefiniowany, wyłącza przetwarzanie resetowania podczas rozłączania, gdy podana wartość limitu czasu jest określona jako **NX_NO_WAIT**. |
| NX_DISABLE_TCP_INFO | Zdefiniowane, wyłącza zbieranie informacji TCP. |
| NX_DISABLE_TCP_RX_CHECKSUM | Zdefiniowano, wyłącza logikę sumy kontrolnej dla odebranych pakietów TCP. Jest to przydatne tylko w sytuacjach, w których warstwa łącza ma niezawodną sumy kontrolnej lub CRC przetwarzania lub sterownik interfejsu jest w stanie zweryfikować sumy kontrolne TCP w sprzęcie. |
| NX_DISABLE_TCP_TX_CHECKSUM | Zdefiniowano, wyłącza logikę sumy kontrolnej do wysyłania pakietów TCP. Jest to przydatne tylko w sytuacjach, w których węzeł sieci odbierający ma odebraną logikę sumy kontrolnej TCP wyłączona lub źródłowy sterownik sieci jest w stanie wygenerować sumy kontrolne TCP. |
| NX_ENABLE_TCP_KEEPALIVE | Zdefiniowany parametr włącza opcjonalny czasomierz utrzymania aktywności protokołu TCP. Ustawienia domyślne nie są włączone. |
| NX_ENABLE_TCP_MSS_CHECKING | Zdefiniowane umożliwia weryfikację minimalnej równorzędnej usługi MSS przed zaakceptowaniem połączenia TCP. Aby można było korzystać z tej funkcji, **NX_ENABLE_TCP_MSS_MINIMUM** musi być zdefiniowana. Domyślnie ta opcja nie jest włączona. |
NX_ENABLE_TCP_WINDOW_SCALING | Włącza opcję skalowania okien dla aplikacji TCP. Jeśli ta opcja jest zdefiniowana, opcja skalowania okien jest negocjowana w fazie połączenia TCP, a aplikacja może określić rozmiar okna większy niż 64K. Ustawienie domyślne nie jest włączone (nie zdefiniowano). |
| NX_MAX_LISTEN_REQUESTS | Określa maksymalną liczbę żądań nasłuchiwać serwera. Wartość domyślna to 10 i jest zdefiniowana w ***nx_api.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._* |
| NX_TCP_ACK_EVERY_N_PACKETS | Określa liczbę pakietów TCP do odbierania przed wysłaniem ACK. Jeśli ta **NX_TCP_IMMEDIATE_ACK** włączona, NX_TCP_ACK_EVERY_N_PACKETS **jest** włączona, ta wartość jest automatycznie ustawiana na 1 w celu zapewnienia zgodności z poprzednimi wersjami. |
| NX_TCP_ACK_TIMER_RATE | Określa, w jaki sposób liczba taktów systemowych (NX_IP_PERIODIC_RATE) jest dzielona w celu obliczenia szybkości czasomierza dla opóźnionego przetwarzania ACK protokołu TCP. Wartość domyślna to 5, która reprezentuje 200ms i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed uwzględnieniem wartości _*_nx_api.h_**. |
| NX_TCP_ENABLE_KEEPALIVE | Zmieniono nazwę **na NX_ENABLE_TCP_KEEPALIVE**. Mimo że ta wersja jest nadal obsługiwana, zachęcamy do korzystania z nowych projektów **NX_ENABLE_TCP_KEEPALIVE**. |
| NX_TCP_ENABLE_WINDOW_SCALING | Zmieniono nazwę na **NX_ENABLE_TCP_WINDOW_SCALING**. Mimo że ta wersja jest nadal obsługiwana, zachęcamy do korzystania z nowych projektów **NX_ENABLE_TCP_WINDOW_SCALING**. |
| NX_TCP_FAST_TIMER_RATE | Określa, w jaki sposób liczba wewnętrznych taktowania NetX (NX_IP_PERIODIC_RATE) jest dzielona w celu obliczenia szybkości czasomierza TCP. Szybki czasomierz TCP jest używany do kierowania różnymi czasomierzami TCP, w tym opóźnionym czasomierzem ACK. Wartość domyślna to 10, która reprezentuje 100ms przy założeniu, że czasomierz ThreadX jest uruchomiony na 10ms. Ta wartość jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed uwzględnieniem wartości _*_nx_api.h_**. |
| NX_TCP_IMMEDIATE_ACK | Zdefiniowane umożliwia opcjonalne natychmiastowe przetwarzanie odpowiedzi ACK protokołu TCP. Zdefiniowanie tego symbolu jest równoważne zdefiniowaniu **NX_TCP_ACK_EVERY_N_PACKETS** na 1. |
| NX_TCP_KEEPALIVE_INITIAL | Określa liczbę sekund braku aktywności przed aktywowanie czasomierza utrzymania aktywności. Wartość domyślna to 7200, która reprezentuje 2 godziny i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed uwzględnieniem wartości _*_nx_api.h_**. |
| NX_TCP_KEEPALIVE_RETRIES | Określa, ile prób utrzymania aktywności jest dozwolonych, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._* |
| NX_TCP_KEEPALIVE_RETRY | Określa liczbę sekund między ponownych prób czasomierza utrzymania aktywności przy założeniu, że druga strona połączenia nie odpowiada. Wartość domyślna to 75, która reprezentuje 75 sekund między ponownych prób i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem wartości _ *_nx_api.h*._* |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol definiujący maksymalną liczbę poza kolejnością pakietów TCP, które mogą być przechowywane w kolejce odbierania gniazd TCP. Ten symbol może służyć do ograniczania liczby pakietów w kolejce w gnieździe odbierania TCP, zapobiegając utracie puli pakietów. Domyślnie ten symbol nie jest zdefiniowany, w związku z tym nie ma limitu liczby pakietów poza kolejnością, które są kolejkowane w gnieździe TCP. |
| NX_TCP_MAXIMUM_RETRIES | Określa, ile danych przesyła ponowne próby, zanim połączenie zostanie uznane za przerwane. Wartość domyślna to 10, która reprezentuje 10 ponownych prób i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed uwzględnieniem wartości _*_nx_api.h_**. |
| NX_TCP_MAXIMUM_TX_QUEUE | Określa maksymalną głębokość kolejki przesyłania TCP, zanim żądania wysyłania TCP zostaną wstrzymane lub odrzucone. Wartość domyślna to 20, co oznacza, że w kolejce przesyłania może w danym momencie być maksymalnie 20 pakietów. Należy pamiętać, że pakiety pozostają w kolejce przesyłania, dopóki nie zostanie odebrany ACK, który obejmuje część lub wszystkie dane pakietów z drugiej strony połączenia. Ta stała jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może zastąpić wartość domyślną, definiując wartość przed dopisem _*_nx_api.h_**. |
| X_TCP_MSS_CHECKING_ENABLED | Zmieniono nazwę **na NX_ENABLE_TCP_MSS_CHECKING**. Mimo że nadal jest ona obsługiwana, zachęcamy do korzystania z nowych projektów **NX_ENABLE_TCP_MSS_CHECKING**. |
| NX_TCP_MSS_MINIMUM | Symbol definiujący minimalną wartość MSS akceptowaną przez moduł TCP NetX. Ta funkcja jest włączana **przez NX_ENABLE_TCP_MSS_CHECK** |
| NX_TCP_RETRY_SHIFT | Określa, jak zmienia się limit czasu retransmisji między ponownymi próbami. Jeśli ta wartość wynosi 0, początkowy limit czasu ponownego przetłumaczenia jest taki sam jak kolejne limity czasu ponownego przetłumaczenia. Jeśli ta wartość wynosi 1, każdy kolejny retransmisja jest dwa razy dłuższy. Jeśli ta wartość wynosi 2, każdy kolejny limit czasu ponownego przetłumaczenia jest cztery razy dłuższy. Wartość domyślna to 0 i jest zdefiniowana w ***nx_tcp.h** _. Aplikacja może przesłonić wartość domyślną, definiując wartość przed uwzględnieniem wartości _*_nx_api.h_**. |
| NX_TCP_TRANSMIT_TIMER_RATE| Określa, jak liczba takty systemu **NX_IP_PERIODIC_RATE**) jest dzielona w celu obliczenia szybkości czasomierza dla przetwarzania ponowienia przesyłania TCP. Wartość domyślna to 1, która reprezentuje 1 sekundę i jest zdefiniowana w **_nx_tcp.h_*_. Aplikacja może przesłonić wartość domyślną, definiując wartość przed dopisem _*_nx_api.h._** |

### <a name="udp-configuration-options"></a>Opcje konfiguracji UDP
| Opcja  | Opis  |
|---|---|
| NX_DISABLE_UDP_INFO | Zdefiniowane, wyłącza zbieranie informacji UDP. |
| NX_DISABLE_UDP_RX_CHECKSUM | Zdefiniowano , wyłącza obliczanie sumy kontrolnej UDP dla przychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego jest w stanie zweryfikować sumy kontrolne nagłówka UDP na sprzęcie, a aplikacja nie włącza logiki fragmentacji adresu IP. |
| NX_DISABLE_UDP_TX_CHECKSUM | Zdefiniowane wyłącza obliczanie sumy kontrolnej UDP dla wychodzących pakietów UDP. Jest to przydatne, jeśli sterownik interfejsu sieciowego może obliczyć sumy kontrolne nagłówka UDP i wstawić wartość w nagłówku adresu IP przed przesyłaniem danych, a aplikacja nie włączy logiki fragmentacji adresu IP. |

## <a name="netx-version-id"></a>Identyfikator wersji NetX

Bieżąca wersja oprogramowania NetX jest dostępna zarówno dla użytkownika, jak i dla oprogramowania aplikacji w czasie wykonywania. Programista może uzyskać wersję NetX z **pliku nx_port.h.** Ponadto ten plik zawiera historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję NetX, sprawdzając globalny ciąg _nx_version_id **w** **_nx_port.h._**  

Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych pokazanych poniżej, które są zdefiniowane w ***nx_api.h**.*

Te stałe identyfikują bieżące wydanie produktu według nazwy oraz wersji pomocniczej i wersji pomocniczej produktu.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```