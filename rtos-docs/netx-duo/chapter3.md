---
title: Rozdział 3 — funkcjonalne składniki platformy Azure RTO NetX Duo
description: Ten rozdział zawiera opis stosu TCP/IP o wysokiej wydajności usługi Azure RTO NetX Duo z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 31900c7b822c88079e4b9fe28a8a388d20f819aa
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549848"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx-duo"></a>Rozdział 3 — funkcjonalne składniki platformy Azure RTO NetX Duo

Ten rozdział zawiera opis stosu TCP/IP o wysokiej wydajności usługi Azure RTO NetX Duo z perspektywy funkcjonalnej. 

## <a name="execution-overview"></a>Przegląd wykonywania

W aplikacji NetX Duo istnieje pięć typów wykonywania programu: inicjalizacja, wywołania interfejsu aplikacji, wewnętrzny wątek IP, okresowe czasomierze IP i sterownik sieciowy.

> [!NOTE]
> *NetX Duo zakłada istnienie ThreadX i zależy od jej wykonywania, zawieszania, okresowych czasomierzy i wzajemnych wykluczeń.*

### <a name="initialization"></a>Inicjalizacja

Przed wywołaniem innej usługi NetX Duo należy wywołać usługę ***nx_system_initialize** _. Inicjalizację systemu można wywołać z funkcji ThreadX _ *_tx_application_define_** lub z wątków aplikacji.

Po znaku ***nx_system_initialize** _ system jest gotowy do tworzenia pul pakietów i wystąpień adresów IP. Ponieważ utworzenie wystąpienia adresu IP wymaga domyślnej puli pakietów, musi istnieć co najmniej jedna pula pakietów NetX Duo przed utworzeniem wystąpienia adresu IP. Tworzenie pul pakietów i wystąpień adresów IP jest dozwolone z funkcji inicjowania ThreadX _ *_tx_application_define_** i z wątków aplikacji.

Wewnętrznie Tworzenie wystąpienia IP jest realizowane w dwóch częściach: Pierwsza część jest wykonywana w kontekście obiektu wywołującego, z ***tx_application_define*** lub z kontekstu wątku aplikacji. Obejmuje to Konfigurowanie struktury danych IP i tworzenie różnych zasobów IP, w tym wewnętrznego wątku IP. Druga część jest wykonywana podczas początkowego wykonywania z wewnętrznego wątku IP. Jest to miejsce, w którym sterownik sieciowy dostarczony podczas pierwszej części tworzenia IP jest najpierw wywoływany. Wywołanie sterownika sieci z wewnętrznego wątku IP umożliwia sterownikowi wykonywanie operacji we/wy i wstrzymywanie podczas przetwarzania inicjalizacji.

Gdy sterownik sieciowy wraca z przetwarzania inicjowania, tworzenie adresu IP zostało zakończone.

Inicjalizacja protokołu IPv6 w NetX Duo wymaga kilku dodatkowych usług NetX Duo. Są one opisane bardziej szczegółowo w sekcji [IPv6 w NetX Duo](#ipv6-in-netx-duo) w dalszej części tego rozdziału.

> [!NOTE]
> ***Nx_ip_status_check** usługi NetX Duo jest dostępna, aby uzyskać informacje dotyczące wystąpienia adresu IP i jego stanu podstawowego interfejsu. Takie informacje o stanie obejmują, czy łącze jest inicjowane, włączone i rozwiązane. Te informacje służą do synchronizowania wątków aplikacji, które wymagają użycia nowo utworzonego wystąpienia adresu IP. W przypadku systemów z wieloma systemami prywatnymi Zobacz artykuł [Obsługa wieloznacznych](#multihome-support). **nx_ip_interface_status_check** jest dostępny do uzyskania 3information w określonym interfejsie.*

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Wywołania z aplikacji są wykonywane w dużej mierze od wątków aplikacji uruchomionych w ramach ThreadX RTO. Jednak niektóre inicjalizacje, tworzenie i Włączanie usług mogą być wywoływane z ***tx_application_define***. Sekcje "dozwolone z" w [rozdziale 4 — Opis usług Azure RTO NetX Duo](chapter4.md) wskazują, na podstawie których można wywołać każdą usługę NetX Duo.

W większości przypadków przetwarzanie intensywnych działań, takich jak obliczanie sum kontrolnych, odbywa się w kontekście wątku wywołującego — bez blokowania dostępu do innych wątków do wystąpienia IP. Na przykład podczas transmisji obliczenia sumy kontrolnej UDP są wykonywane w ramach usługi ***nx_udp_socket_send** _ przed wywołaniem podstawowej funkcji wysyłania adresów IP. W przypadku odebranego pakietu suma kontrolna UDP jest obliczana w usłudze _ *_nx_udp_socket_receive_**, wykonywanej w wątku aplikacji. Pomaga to zapobiegać zapewnieniu żądań sieci przez wątki o wyższym priorytecie z powodu przetwarzania obliczeń sum kontrolnych o niższym priorytecie.

Wartości, takie jak adresy IP i numery portów, są przesyłane do interfejsów API w kolejności bajtów hosta. Wewnętrznie te wartości są przechowywane w kolejności bajtów hosta. Dzięki temu deweloperzy mogą łatwo wyświetlać wartości za pomocą debugera. Gdy te wartości są programowane do ramki do transmisji, są konwertowane na kolejność bajtów sieci.

### <a name="internal-ip-thread"></a>Wewnętrzny wątek IP

Jak wspomniano, każde wystąpienie protokołu IP w NetX Duo ma swój własny wątek. Priorytet i rozmiar stosu wewnętrznego wątku IP są zdefiniowane w usłudze ***nx_ip_create*** . Wewnętrzny wątek IP jest tworzony w trybie gotowym do wykonania. Jeśli wątek IP ma wyższy priorytet niż wątek wywołujący, może wystąpić zastępujący w wywołaniu IP Create.

Punkt wejścia wewnętrznego wątku IP znajduje się w funkcji wewnętrznej _ ***nx_ip_thread_entry***. Po uruchomieniu wewnętrzny wątek IP najpierw kończy inicjalizację sterownika sieci, która składa się z trzech wywołań sterownika sieci specyficznego dla aplikacji. Pierwsze wywołanie polega na dołączeniu sterownika sieci do wystąpienia IP, po którym następuje wywołanie inicjacji, które umożliwia sterownikowi sieciowe przechodzenie przez proces inicjalizacji. Po powrocie sterownika sieci z inicjacji (może on zostać zawieszony podczas oczekiwania na prawidłowe skonfigurowanie sprzętu), wewnętrzny wątek IP wywołuje ponownie sterownik sieciowy, aby włączyć link. Po powrocie sterownika sieci z wywołania Włącz łącze, wewnętrzny wątek IP wprowadza pętlę nieskończoną dla różnych zdarzeń, które wymagają przetworzenia dla tego wystąpienia IP. Zdarzenia przetwarzane w tej pętli obejmują odroczony przyjmowanie pakietów IP, zestaw fragmentów pakietów IP, przetwarzanie ping protokołu ICMP, przetwarzanie protokołu IGMP, przetwarzanie kolejki pakietów TCP, przetwarzanie przez TCP, przekroczenie limitu czasu zestawu fragmentów adresów IP oraz okresowe przetwarzanie IGMP. Zdarzenia obejmują również działania dotyczące rozpoznawania adresów; Przetwarzanie pakietów ARP i okresowe przetwarzanie ARP w protokole IPv4, wykrywanie duplikatów adresów, żądanie routera i odnajdowanie sąsiadów w protokole IPv6.

> [!CAUTION]
> *Funkcje wywołania zwrotnego NetX Duo, w tym nasłuchiwanie i rozłączane wywołania zwrotne, są wywoływane z wewnętrznego wątku IP — a nie oryginalnego wątku wywołującego. Aplikacja musi zadbać o to, aby nie zawiesić się wewnątrz żadnej funkcji wywołania zwrotnego NetX Duo.*

### <a name="ip-periodic-timers"></a>Okresowe czasomierze IP

Dla każdego wystąpienia IP są używane dwa okresowe czasomierze ThreadX. Pierwszy z nich to jednorazowy czasomierz dla protokołu ARP, protokołu IGMP, limitu czasu protokołu TCP, a także dyski reasemblera fragmentu IP. Drugi czasomierz to 100 ms czasomierza, który umożliwia przekroczenie limitu czasu ponownej transmisji protokołu TCP i operacji związanych z protokołem IPv6.

### <a name="network-driver"></a>Sterownik sieciowy

Każde wystąpienie IP w NetX Duo ma interfejs podstawowy, który jest identyfikowany przez jego sterownik urządzenia określony w usłudze ***nx_ip_create*** . Sterownik sieciowy jest odpowiedzialny za obsługę różnych żądań NetX Duo, w tym przesyłanie pakietów, odbieranie pakietów i żądania dotyczące stanu i kontroli. 

W przypadku systemu wieloznacznego wystąpienie protokołu IP zawiera wiele interfejsów, z których każdy jest skojarzony ze sterownikiem sieciowym wykonującym te zadania dla odpowiedniego interfejsu.

Sterownik sieciowy musi również obsługiwać zdarzenia asynchroniczne występujące na nośniku. Zdarzenia asynchroniczne z nośnika obejmują odbieranie pakietów, uzupełnianie transmisji pakietów i zmiany stanu. NetX Duo udostępnia sterownik sieciowy z kilkoma funkcjami dostępu do obsługi różnych zdarzeń. Te funkcje są przeznaczone do wywoływania z części procedury usługi przerwania sterownika sieci. W przypadku sieci IPv4 sterownik sieciowy powinien przesłać dalej wszystkie pakiety ARP odebrane do funkcji wewnętrznej ***_nx_arp_packet_deferred_receive*** . Wszystkie pakiety RARP powinny być przekazywane do funkcji wewnętrznej ***_nx_rarp_packet_deferred_receive** _. Dostępne są dwie opcje pakietów IP. Jeśli jest wymagane szybkie wysyłanie pakietów IP, przychodzące pakiety IP powinny być przekazywane do _ _ *_nx_ip_packet_receive_* _ do natychmiastowego przetwarzania. Znacznie poprawia to wydajność NetX Duo w obsłudze pakietów IP. W przeciwnym razie należy wykonać przekazywanie pakietów IP do _ *_ _nx_ip_packet_deferred_receive_**. Ta usługa umieszcza pakiet IP w odroczonej kolejce przetwarzania, w której jest następnie obsługiwany przez wewnętrzny wątek IP, co skutkuje mniejszą ilością czasu przetwarzania ISR.

Sterownik sieciowy może również odroczyć przetwarzanie przerwania w celu uruchomienia z kontekstu wątku IP. W tym trybie procedura ISR zapisze niezbędne informacje, wywołaj wewnętrzną funkcję ***_nx_ip_driver_deferred_processing*** i Potwierdź kontroler przerwań. Ta usługa powiadamia wątek IP w celu zaplanowania wywołania zwrotnego sterownika urządzenia, aby zakończyć proces zdarzenia, które powoduje przerwanie.

Niektóre kontrolery sieci mogą wykonywać obliczenia i weryfikację sum kontrolnych nagłówka TCP/IP na sprzęcie bez uwzględniania cennych zasobów procesora CPU. Aby skorzystać z funkcji sprzętowej, NetX Duo oferuje opcje włączania lub wyłączania obliczeń sum kontrolnych oprogramowania w czasie kompilacji, a także włączania lub wyłączania obliczeń sum kontrolnych w czasie wykonywania, jeśli sterownik urządzenia może komunikować się z warstwą IP w systemie to możliwości sprzętowe. Aby uzyskać bardziej szczegółowe informacje na temat pisania sterowników sieciowych NetX Duo, zobacz [rozdział 5 — sterowniki sieciowe usługi Azure RTO NetX Duo](chapter5.md) .

### <a name="multihome-support"></a>Obsługa wielostrona

NetX Duo obsługuje systemy połączone z wieloma urządzeniami fizycznymi przy użyciu jednego wystąpienia IP. Każdy interfejs fizyczny jest przypisany do bloku sterowania interfejsem w wystąpieniu IP. Aplikacje chcące korzystać z systemu wieloznacznego muszą definiować wartość parametru ***NX_MAX_PHSYCIAL_INTERFACES** _ do liczby urządzeń fizycznych podłączonych do systemu i ponownie kompilować bibliotekę NetX Duo. Domyślnie _ *_NX_MAX_PHYSICAL_INTERFACES_** jest ustawiona na jeden, tworząc jeden blok sterowania interfejsem w wystąpieniu IP.

Aplikacja NetX Duo tworzy pojedyncze wystąpienie adresu IP dla urządzenia podstawowego przy użyciu usługi ***nx_ip_create** _. Dla każdego dodatkowego urządzenia sieciowego aplikacja dołącza urządzenie do wystąpienia IP przy użyciu usługi _ *_nx_ip_interface_attach_**.

Każda struktura interfejsu sieciowego zawiera podzestaw informacji o sieci o interfejsie sieciowym, który znajduje się w bloku kontroli IP, w tym adres IPv4 interfejsu, maskę podsieci, rozmiar IP jednostki MTU i informacje o adresie warstwy MAC.

> [!NOTE]
> *NetX Duo z obsługą wielodomu jest zgodna z poprzednimi wersjami NetX Duo. Usługi, które nie pobierają domyślnych informacji o interfejsie, do podstawowego urządzenia sieciowego.*

Interfejs podstawowy ma indeks zero na liście wystąpień adresów IP. Do każdego kolejnego urządzenia dołączonego do wystąpienia protokołu IP jest przypisywany następny indeks.

Wszystkie usługi protokołów warstwy wyższej, dla których jest włączone wystąpienie protokołu IP, w tym protokoły TCP, UDP, ICMP i IGMP, są dostępne dla wszystkich dołączonych urządzeń.

W większości przypadków NetX Duo może określić najlepszy adres źródłowy do użycia podczas przesyłania pakietu. Wybór adresów źródłowych jest oparty na adresie docelowym. Usługi NetX Duo są dodawane, aby umożliwić aplikacjom określenie określonego adresu źródłowego, w przypadkach, gdy najbardziej odpowiedni dla nich nie może być określony przez adres docelowy. Przykładem może być w systemie z wieloma lokalizacjami, aplikacja musi wysłać pakiet do adresu IPv4 lub multiemisji.

Usługi przeznaczone do tworzenia aplikacji multihomed:

- *nx_igmp_multicast_interface_join*
- *nx_igmp_multicast_interface_leave*
- *nx_ip_driver_interface_direct_command*
- *nx_ip_interface_address_get*
- *nx_ip_interface_address_mapping_configure*
- *nx_ip_interface_address_set*  
- *nx_ip_interface_attach*
- *nx_ip_interface_capability_get* 
- *nx_ip_interface_capability_set*
- *nx_ip_interface_detach*
- *nx_ip_interface_info_get*
- *nx_ip_interface_mtu_set*
- *nx_ip_interface_physical_address_get*
- *nx_ip_interface_physical_address_set*
- *nx_ip_interface_status_check*
- *nx_ip_raw_packet_source_send*
- *nx_ipv4_multicast_interface_join*
- *nx_ipv4_multicast_interface_leave*
- *nx_udp_socket_source_send*
- *nxd_ipv6_multicast_interface_join*
- *nxd_ipv6_multicast_interface_leave* 
- *nxd_udp_socket_source_send*
- *nxd_icmp_source_ping*
- *nxd_ip_raw_packet_source_send*
- *nxd_udp_socket_source_send*

Te usługi zostały omówione bardziej szczegółowo w [opisie usług NetX Duo](chapter4.md).

### <a name="loopback-interface"></a>Interfejs sprzężenia zwrotnego

Interfejs sprzężenia zwrotnego jest specjalnym interfejsem sieciowym bez linku fizycznego dołączonego do. Interfejs sprzężenia zwrotnego umożliwia aplikacjom komunikowanie się przy użyciu adresu sprzężenia zwrotnego IPv4 127.0.0.1 do wykorzystania logicznego interfejsu sprzężenia zwrotnego, upewnij się, że konfigurowalne ***NX_DISABLE_LOOPBACK_INTERFACE*** nie jest ustawione.

### <a name="interface-control-blocks"></a>Bloki sterujące interfejsu

Liczba bloków sterujących interfejsem w wystąpieniu IP jest liczbą interfejsów fizycznych (zdefiniowanych przez ***NX_MAX_PHYSICAL_INTERFACES** _) i interfejsem sprzężenia zwrotnego, jeśli jest włączony. Łączna liczba interfejsów jest zdefiniowana w _ *_NX_MAX_IP_INTERFACES_* *.

## <a name="protocol-layering"></a>Warstwy protokołu

Protokół TCP/IP zaimplementowany przez NetX Duo jest protokołem warstwowym, co oznacza, że bardziej złożone protokoły są zbudowane w oparciu o prostsze protokoły bazowe. W przypadku protokołu TCP/IP najniższy protokół warstwy jest na *poziomie łącza* i jest obsługiwany przez sterownik sieciowy. Ten poziom jest zwykle przeznaczony do sieci Ethernet, ale może być również Fiber, serial lub praktycznie dowolnym nośnikiem fizycznym.

W górnej części warstwy linku znajduje się *warstwa sieciowa*. W przypadku protokołu TCP/IP jest to adres IP, który jest zasadniczo odpowiedzialny za wysyłanie i otrzymywanie prostych pakietów — w sposób optymalny — w sieci. Protokoły typu zarządzania, takie jak ICMP i IGMP, są zazwyczaj klasyfikowane jako warstwy sieci, nawet jeśli są one oparte na adresie IP do wysyłania i otrzymywania.

*Warstwa transportu* jest zareszcie warstwy sieciowej. Ta warstwa jest odpowiedzialna za zarządzanie przepływem danych między hostami w sieci. Istnieją dwa typy usług transportowych obsługiwane przez NetX Duo: UDP i TCP. Usługi UDP zapewniają optymalny sposób wysyłania i otrzymywania danych między dwoma hostami bez połączenia, natomiast protokół TCP zapewnia niezawodne usługi zorientowane na połączenia między dwiema jednostkami hosta.

Ta warstwa jest odzwierciedlana w rzeczywistych pakietach danych sieciowych. Każda warstwa w protokole TCP/IP zawiera blok informacji o nazwie header. Ta technika otaczających danych (i prawdopodobnie informacji o protokole) z nagłówkiem jest zazwyczaj nazywana hermetyzacją danych. Na rysunku 1 przedstawiono przykład użycia warstw NetX Duo i rysunek 2 przedstawia powstający hermetyzację danych dla wysyłanych danych UDP.

![Warstwy protokołu](./media/user-guide/image12.jpg)

**RYSUNEK 1. Warstwy protokołu**

## <a name="packet-pools"></a>Pule pakietów

Przydzielanie pakietów w sposób szybki i deterministyczny jest zawsze wyzwaniem w aplikacjach sieci w czasie rzeczywistym. Z tego względu NetX Duo zapewnia możliwość tworzenia wielu pul pakietów o stałym rozmiarze i zarządzania nimi.

Ponieważ pule pakietów NetX Duo składają się z bloków pamięci o stałym rozmiarze, nigdy nie występują żadne wewnętrzne problemy z defragmentacją. Oczywiście fragmentacja powoduje, że zachowanie, które jest niedeterministyczne. Ponadto czas wymagany do przydzielenia i zwolnienia pakietu NetX Duo do prostego manipulowania listą. Ponadto alokacja i cofanie pakietów odbywa się na końcu listy dostępnych. Zapewnia to najszybszy możliwy do przetwarzania listy połączonej.

![Hermetyzacja danych UDP](./media/user-guide/image13.png)

**RYSUNEK 2. Hermetyzacja danych UDP**

Brak elastyczności jest zazwyczaj główną wadą dla pul pakietów o stałym rozmiarze. Określenie optymalnego rozmiaru ładunku pakietu, który również obsługuje pakiet przychodzący najgorszego przypadku, jest trudnym zadaniem. Pakiety NetX Duo dotyczą tego problemu z opcjonalną funkcją o nazwie tworzenie łańcucha pakietów. Rzeczywisty pakiet sieciowy może być utworzony z co najmniej jednym pakietem NetX Duo połączonych ze sobą. Ponadto nagłówek pakietu zachowuje wskaźnik na górze pakietu. Po dodaniu dodatkowych protokołów wskaźnik ten jest po prostu przenoszony do tyłu, a nowy nagłówek jest zapisywana bezpośrednio przed danymi. Bez elastycznej technologii pakietów, stos będzie musiał przydzielić inny bufor i skopiować dane do nowego buforu z nowym nagłówkiem, który przetwarza intensywne przetwarzanie.

Ponieważ każdy rozmiar ładunku pakietu został ustalony dla danej puli pakietów, dane aplikacji o rozmiarze większym niż rozmiar ładunku będą wymagały łączenia wielu pakietów jednocześnie. Podczas wypełniania pakietu przy użyciu danych użytkownika aplikacja korzysta z ***nx_packet_data_append*** usługi. Ta usługa przenosi dane aplikacji do pakietu. W sytuacjach, gdy pakiet nie wystarcza do przechowywania danych użytkownika, dodatkowe pakiety są przydzieleni do przechowywania danych użytkownika. Aby można było korzystać z łańcucha pakietów, Sterownik musi mieć możliwość odbierania lub przesyłania z połączonych pakietów.

W przypadku systemów osadzonych, które nie muszą korzystać z funkcji łańcucha pakietów, biblioteka NetX Duo może być skompilowana za pomocą ***NX_DISABLE_PACKET_CHAIN** _, aby usunąć logikę łańcucha pakietów. Należy pamiętać, że funkcja fragmentacji i reasemblera IP może potrzebować użycia funkcji łańcucha w łańcuchu. W związku z tym Definiowanie _*_NX_DISABLE_PACKET_CHAIN_*_ wymaga zdefiniowania _ *_NX_DISABLE_FRAGMENTATION_**. 

Każda pula pamięci pakietu NetX Duo jest zasobem publicznym. NetX Duo nie wprowadza żadnych ograniczeń dotyczących sposobu używania pul pakietów. 

### <a name="packet-pool-memory-area"></a>Obszar pamięci puli pakietów

Obszar pamięci dla puli pakietów jest określany podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci dla obiektów ThreadX i NetX Duo, może ona znajdować się w dowolnym miejscu w przestrzeni adresowej miejsca docelowego. 

Jest to ważna funkcja ze względu na znaczną elastyczność zapewnianą przez aplikację. Załóżmy na przykład, że produkt komunikacyjny ma obszar pamięci o dużej szybkości dla buforów sieciowych. Ten obszar pamięci jest łatwo wykorzystywany przez umieszczenie go w puli pamięci pakietu NetX Duo.

### <a name="creating-packet-pools"></a>Tworzenie pul pakietów

Pule pakietów są tworzone podczas inicjalizacji lub podczas wykonywania przez wątki aplikacji. W aplikacji NetX Duo nie ma ograniczeń dotyczących liczby pul pamięci pakietów.

### <a name="dual-packet-pool"></a>Podwójna Pula pakietów

Zwykle rozmiar ładunku domyślnej puli pakietów IP jest wystarczająco duży, aby pomieścić rozmiar ramki do jednostki MTU interfejsu sieciowego. Podczas normalnej operacji wątek IP musi wysyłać komunikaty, takie jak ARP, komunikaty sterujące TCP, Komunikaty IGMP, komunikaty ICMPv6. Te komunikaty używają pakietów przyznanych z domyślnej puli pakietów w wystąpieniu protokołu IP. W systemie ograniczonym do pamięci, w którym ilość pamięci dostępnej dla puli pakietów jest ograniczona, użycie pojedynczej puli pakietów (z dużym rozmiarem ładunku do dopasowania rozmiaru MTU) może nie być rozwiązaniem optymalnym. NetX Duo umożliwia aplikacji zainstalowanie pomocniczej puli pakietów, gdzie rozmiar ładunku jest mniejszy. Po zainstalowaniu pomocniczej puli pakietów wątek pomocnika IP przydzieli pakiety z domyślnej puli pakietów lub pomocniczej puli, w zależności od rozmiaru wysyłanej wiadomości. W przypadku pomocniczej puli pakietów rozmiar ładunku 200 bajtów będzie działał z większością komunikatów przesyłanych przez wątek pomocnika IP.

Domyślnie Biblioteka NetX Duo została skompilowana bez włączania podwójnej puli pakietów. Aby włączyć tę funkcję, skompiluj bibliotekę z definicją ***NX_DUAL_PACKET_POOL_ENABLE** _. Następnie pomocniczą pulę pakietów można ustawić przez wywołanie _ *_nx_ip_auxiliary_packet_pool_set_* *.

Istnieje również możliwość utworzenia więcej niż jednej puli pakietów. Przykładowo zostanie utworzona Pula pakietów przesyłana z optymalnym rozmiarem ładunku dla oczekiwanych rozmiarów komunikatów. Pula pakietów odbioru jest tworzona w sterowniku z rozmiarem ładunku ustawionym na jednostkę MTU sterownika, ponieważ jeden z nich nie może przewidzieć rozmiaru odebranych pakietów.

### <a name="packet-header-nx_packet"></a>NX_PACKET nagłówka pakietu   
Domyślnie NetX Duo umieszcza nagłówek pakietu bezpośrednio przed obszarem ładunku pakietu. Pula pamięci pakietu jest zasadniczo serią pakietów — nagłówkami, a następnie bezpośrednio przez ładunek pakietu. Nagłówek pakietu (***NX_PACKET***) i układ puli pakietów są przedstawiane na rysunku 3.

W przypadku sterownika urządzeń sieciowych, który jest w stanie wykonać zero operacji kopiowania, zazwyczaj adres początkowy obszaru ładunku pakietu jest zaprogramowany do logiki DMA. Niektóre aparaty DMA mają wymagania dotyczące wyrównania w obszarze ładunku. Aby adres początkowy obszaru ładunku był wyrównany prawidłowo dla aparatu DMA lub operacji pamięci podręcznej, użytkownik może zdefiniować symbol ***NX_PACKET_ALIGNMENT***.

> [!WARNING]
> *Ważne jest, aby sterownik sieciowy korzystał z funkcji **nx_packet_transmit_release** , gdy transmisja pakietu zostanie zakończona. Ta funkcja sprawdza, czy pakiet nie jest częścią kolejki wyjściowej TCP, zanim zostanie w rzeczywistości umieszczony w dostępnej puli.*

![Układ nagłówka i puli pakietów](./media/user-guide/image14.jpg)

**RYSUNEK 3. Układ nagłówka i puli pakietów**

Pola nagłówka pakietu są zdefiniowane w następujący sposób. Należy zauważyć, że ta tabela nie jest kompletną listą wszystkich elementów członkowskich w strukturze *NX_PACKET* .

|Nagłówek pakietu | Przeznaczenie |
|---|---|
|***nx_packet_pool_owner***|To pole wskazuje pulę pakietów, do której należy ten konkretny pakiet. Po wydaniu pakiet jest on wydawany do tej określonej puli. Mając własność puli wewnątrz każdego pakietu, istnieje możliwość, że datagram obejmuje wiele pakietów z wielu pul pakietów.|
|***nx_packet_next** _|To pole wskazuje następny pakiet w obrębie tej samej ramki. Jeśli wartość jest równa NULL, nie ma dodatkowych pakietów, które są częścią ramki. To pole jest również używane do przechowywania pofragmentowanych pakietów do momentu, w którym cały pakiet będzie można ponownie połączyć. jest ona usuwana, jeśli określono _ *_NX_DISABLE_PACKET_CHAIN_* *.|
|***nx_packet_last** _|To pole wskazuje ostatni pakiet w ramach tego samego pakietu sieciowego. Jeśli wartość jest równa NULL, ten pakiet reprezentuje cały pakiet sieciowy. To pole jest usuwane, jeśli określono _ *_NX_DISABLE_PACKET_CHAIN_* *.|
|***nx_packet_length** _| To pole zawiera łączną liczbę bajtów w całym pakiecie sieciowym, w tym łączną liczbę wszystkich bajtów we wszystkich pakietach połączonych przez element członkowski _nx_packet_next *.|
|***nx_packet_ip_interface***| To pole jest blokiem sterowania interfejsem przypisanym do pakietu, gdy jest odbierany przez sterownik interfejsu i przez NetX Duo dla pakietów wychodzących. Blok sterowania interfejsem opisuje interfejs, np. adres sieciowy, adres MAC, adres IP i stan interfejsu, takie jak link włączony i wymagane jest mapowanie fizyczne.|
|***nx_packet_data_start** _| To pole wskazuje początek obszaru fizycznego ładunku tego pakietu. Nie musi ona występować bezpośrednio po nagłówku NX_PACKET, ale jest wartością domyślną dla usługi _ *_nx_packet_pool_create_**.|
|***nx_packet_data_end** _|To pole wskazuje koniec obszaru fizycznego ładunku tego pakietu. Różnica między tym polem a polem _nx_packet_data_start * reprezentuje rozmiar ładunku.|
|***nx_packet_prepend_ptr** _|To pole wskazuje lokalizację, w której dane pakietów, nagłówek protokołu lub rzeczywiste dane, są dodawane przed istniejącymi danymi pakietu (jeśli istnieją) w obszarze ładunku pakietu. Wartość musi być większa niż lub równa _nx_packet_data_start * lokalizacji wskaźnika i mniejsza lub równa *nx_packet_append_ptr* wskaźnika.|
> [!CAUTION]
> *Ze względu na wydajność NetX Duo zakłada, że gdy pakiet jest przekazywany do usługi NetX Duo do transmisji, wskaźnik poprzedź wskazuje na długi adres wyrównany do wyrazu.*

| Nagłówek pakietu | Przeznaczenie |
|---|---|
|***nx_packet_append_ptr** _|To pole wskazuje koniec danych znajdujących się obecnie w obszarze ładunku pakietu. Musi znajdować się między lokalizacją pamięci wskazywaną przez _nx_packet_prepend_ptr * i *nx_packet_data_end.* Różnica między tym polem a polem *nx_packet_prepend_ptr* reprezentuje ilość danych w tym pakiecie.|
|***nx_packet_packet_pad** _|Te pola definiują długość wypełnienia w przypadku wyrazów 4-bajtowych w celu osiągnięcia wymaganego wymagania dotyczącego wyrównania. To pole jest usuwane, jeśli nie zdefiniowano _*_NX_PACKET_HEADER_PAD_*_ . Można również użyć _*_NX_PACKET_ALIGNMENT_*_ zamiast definiować _nx_packet_header_pad. *|

### <a name="packet-header-offsets"></a>Przesunięcia nagłówka pakietu

Rozmiar nagłówka pakietu jest zdefiniowany w celu zapewnienia wystarczającej ilości miejsca, aby pomieścić rozmiar nagłówka. Usługa ***nx_packet_allocate*** jest używana do przydzielania pakietu i dostosowywania wskaźnika dołączania w pakiecie zgodnie z typem określonego pakietu. Typ pakietu informuje NetX Duo o przesunięciu wymaganym do wstawienia nagłówka protokołu (na przykład UDP, TCP lub ICMP) przed danymi protokołu.

Następujące typy są zdefiniowane w NetX Duo w celu uwzględnienia nagłówka IP i nagłówków warstwy fizycznej (Ethernet) w pakiecie. W drugim przypadku zakłada się, że jest to 16 bajtów z uwzględnieniem wymaganego 4-bajtowego wyrównania. Pakiety IPv4 są nadal zdefiniowane w NetX Duo dla aplikacji w celu przydzielenia pakietów dla sieci IPv4. Należy pamiętać, że jeśli biblioteka NetX Duo została skompilowana z włączonym protokołem IPv6, typy pakietów ogólnych (takie jak NX_IP_PACKET) są mapowane na wersję protokołu IPv6. Jeśli biblioteka NetX Duo została skompilowana bez włączonego protokołu IPv6, te typy pakietów ogólnych są mapowane na wersję IPv4.

W poniższej tabeli przedstawiono symbole zdefiniowane przy użyciu protokołu IPv6:

|**Typ pakietu** |**Wartość** |
|---|---|
|NX_IPv6_PACKET (NX_IP_PACKET) | 0x38 |
|NX_UDPv6_PACKET (NX_UDP_PACKET) |0x40 |
|NX_TCPv6_PACKET (NX_TCP_PACKET) |0x4c |
|NX_IPv4_PACKET |0x24 |
|NX_IPv4_UDP_PACKET |0x2c |
|NX_IPv4_TCP_PACKET |0x38 |

W poniższej tabeli przedstawiono symbole zdefiniowane przy użyciu protokołu IPv6:

|**Typ pakietu** |**Wartość** |
|---|---|
|NX_IPv4_PACKET (NX_IP_PACKET) |0x24 |
|NX_IPv4_UDP_PACKET (NX_UDP_PACKET) |0x2c |
|NX_IPv4_TCP_PACKET (NX_TCP_PACKET) |0x38 |

Należy zauważyć, że te wartości zmienią się, jeśli *NX_IPSEC_ENABLE* jest zdefiniowany. W przypadku aplikacji korzystających z protokołu IPsec zapoznaj się z podręcznikiem użytkownika NetX Duo IPsec, aby uzyskać więcej informacji.

### <a name="pool-capacity"></a>Pojemność puli

Liczba pakietów w puli pakietów jest funkcją rozmiaru ładunku i łączną liczbą bajtów w obszarze pamięci dostarczonym do usługi tworzenia puli pakietów. Pojemność puli jest obliczana przez podzielenie rozmiaru pakietu (w tym rozmiaru nagłówka NX_PACKET, rozmiaru ładunku i właściwego wyrównania) do całkowitej liczby bajtów w podanym obszarze pamięci.

### <a name="payload-area-alignment"></a>Wyrównanie obszaru ładunku

Projektowanie puli pakietów w programie NetX Duo obsługuje kopiowanie zerowe. Na poziomie sterownika urządzenia sterownik może przypisać obszar ładunku bezpośrednio do deskryptorów buforu na potrzeby odbierania danych. Czasami aparat DMA lub mechanizm synchronizacji pamięci podręcznej wymaga, aby adres początkowy obszaru ładunku miał pewne wymagania dotyczące wyrównania. Można to osiągnąć przez zdefiniowanie żądanego wymagania dotyczącego wyrównania (w bajtach) w ***NX_PACKET_ALIGNMENT***. Podczas tworzenia puli pakietów początkowy adres obszaru ładunku będzie wyrównany do tej wartości. Domyślnie adres początkowy to 4-bajtowy wyrównany.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać się podczas oczekiwania na pakiet z pustej puli. Gdy pakiet jest zwracany do puli, zawieszony wątek zostaje przyznany i wznowiony.

Jeśli wiele wątków jest zawieszonych w tej samej puli pakietów, wznowione w kolejności, w której zostały wstrzymane (FIFO).

### <a name="pool-statistics-and-errors"></a>Statystyki i błędy puli

Jeśli ta opcja jest włączona, oprogramowanie do zarządzania pakietami NetX Duo śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla pul pakietów są obsługiwane następujące raporty statystyczne i błędy:

- Łączna liczba pakietów w puli
- Bezpłatne pakiety w puli
- Łączna liczba przydziałów pakietów
- Puste żądania alokacji puli
- Zawieszanie pustej alokacji puli
- Nieprawidłowe wersje pakietów

Wszystkie te statystyki i raporty o błędach, z wyjątkiem całkowitej i bezpłatnej liczby pakietów w puli, są wbudowane w bibliotekę NetX Duo, chyba że określono ***NX_DISABLE_PACKET_INFO** _. Te dane są dostępne dla aplikacji za pomocą usługi _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>NX_PACKET_POOL bloku kontroli puli pakietów

Charakterystyka każdej puli pamięci pakietów znajduje się w bloku sterowania. Zawiera on przydatne informacje, takie jak połączona lista bezpłatnych pakietów, Liczba bezpłatnych pakietów i rozmiar ładunku dla pakietów w tej puli. Ta struktura jest zdefiniowana w pliku ***nx_api. h*** .

Bloki sterujące puli pakietów mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną przez definiowanie jej poza zakresem dowolnej funkcji.

## <a name="ipv4-protocol"></a>Protokół IPv4

Składnik protokołu internetowego (IP) NetX Duo jest odpowiedzialny za wysyłanie i otrzymywanie pakietów IPv4 w Internecie. W NetX Duo jest to składnik, który jest ostatecznie odpowiedzialny za wysyłanie i otrzymywanie komunikatów TCP, UDP, ICMP i IGMP przy użyciu podstawowego sterownika sieciowego.

NetX Duo obsługuje zarówno protokół IPv4 (RFC 791), jak i protokół IPv6 (RFC 2460). W tej sekcji omówiono protokół IPv4. Protokół IPv6 został omówiony w następnej sekcji.

### <a name="ipv4-addresses"></a>Adresy IPv4

Każdy host w Internecie ma unikatowy identyfikator 32-bitowy o nazwie adres IP. Istnieje pięć klas adresów IPv4, zgodnie z opisem na rysunku 4. Zakresy pięciu klas adresów IPv4 są następujące:

|Klasa|Zakres|
|---|---|
|A |od 0.0.0.0 do 127.255.255.255|
|B |128.0.0.0 do 191.255.255.255|
|C |192.0.0.0 do 223.255.255.255|
|D |od 224.0.0.0 do 239.255.255.255|
|E |240.0.0.0 do 247.255.255.255|

![Diagram struktury adresów IPv4.](./media/user-guide/ipv4-address-structure.png)

### <a name="figure-4-ipv4-address-structure"></a>RYSUNEK 4. Struktura adresów IPv4

Istnieją również trzy typy specyfikacji adresów: *emisja pojedyncza*, *emisja* i *Multiemisja*. Adresy emisji pojedynczej są adresami IPv4, które identyfikują określonego hosta w Internecie. Adresy emisji pojedynczej mogą być źródłem lub docelowym adresem IPv4. Adres emisji identyfikuje wszystkie hosty w określonej sieci lub podsieci i może być używany tylko jako adresy docelowe. Adresy emisji są określane przez posiadanie części adresu hosta ustawionej na wartość. Adresy multiemisji (Klasa D) określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączać się i zostawiać w dowolnym momencie.

> [!IMPORTANT]
> *Tylko protokoły bezpołączeniowe, takie jak UDP przez IPv4, mogą korzystać z emisji i ograniczonej możliwości emisji grupy multiemisji.*

> [!IMPORTANT]
> * Makro *IP_address* jest zdefiniowane w ***nx_api. h** _. Umożliwia łatwą specyfikację adresów IPv4 przy użyciu przecinków zamiast kropek. Na przykład _IP_ADDRESS (128, 0, 0, 0) * określa pierwszy adres klasy B przedstawiony na rysunku 4. *

### <a name="ipv4-gateway-address"></a>Adres bramy IPv4

Bramy sieci ułatwiają hostom w ich sieciach przekazywanie pakietów przeznaczonych do miejsc docelowych poza domeną lokalną. Każdy węzeł ma pewną wiedzę na temat tego, w którym następnym przeskoku ma być wysyłany, do lokalizacji docelowej jednego z jej sąsiadów lub za pomocą wstępnie zaprogramowanej tabeli routingu statycznego. Jeśli jednak te podejścia zakończą się niepowodzeniem, węzeł powinien przekazać pakiet do bramy domyślnej, która ma lepszą wiedzę na temat sposobu kierowania pakietu do jego miejsca docelowego. Należy pamiętać, że brama domyślna musi być bezpośrednio dostępna za pomocą jednego z interfejsów fizycznych dołączonych do wystąpienia protokołu IP. Aplikacja wywołuje ***nx_ip_gateway_address_set** _, aby skonfigurować adres bramy domyślnej IPv4. Użyj _*_nx_ip_gateway_address_get_*_ usługi, aby pobrać bieżące ustawienia bramy IPv4. Aplikacja używa usługi _ *_nx_ip_gateway_address_clear_**, aby wyczyścić ustawienie bramy.

### <a name="ipv4-header"></a>Nagłówek IPv4

Dla dowolnego pakietu IPv4, który ma być wysyłany przez Internet, musi mieć nagłówek IPv4. Gdy protokoły wyższego poziomu (UDP, TCP, ICMP lub IGMP) wywołują składnik IP w celu wysłania pakietu, moduł przesyłania protokołu IPv4 umieszcza nagłówek IPv4 przed danymi. Z drugiej strony, gdy pakiety IP są odbierane z sieci, składnik IP usuwa nagłówek IPv4 z pakietu przed dostarczeniem do protokołów wyższego poziomu. Rysunek 5 przedstawia format nagłówka IP.

![Format nagłówka IPv4](./media/user-guide/ipv4-header-format.png)

### <a name="figure-5-ipv4-header-format"></a>RYSUNEK 5. Format nagłówka IPv4

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji TCP/IP mają być w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym. Na przykład 4-bitowa wersja i 4-bitowe długości nagłówka IP muszą znajdować się na pierwszym bajcie nagłówka.*

Pola nagłówka IPv4 są zdefiniowane w następujący sposób:

|&nbsp;Pole nagłówka &nbsp; IPv4 |Przeznaczenie |
|---|---|
|***4-bitowa wersja*** |To pole zawiera wersję protokołu IP reprezentowanego przez ten nagłówek. W przypadku protokołu IP w wersji 4, który jest obsługiwany przez NetX Duo, wartość tego pola to 4. |
|***4-bitowa Długość nagłówka*** |To pole określa liczbę 32-bitowych wyrazów w nagłówku IP. Jeśli nie ma żadnych opcji, wartość dla tego pola to 5. |
|***8-bitowy typ usługi (TOS)*** |To pole określa typ usługi żądany dla tego pakietu IP. Prawidłowe żądania są następujące:<br />-Normal: 0x00 <br />-Minimalne opóźnienie: 0x00<br />-Maksymalna ilość danych: 0x08<br />-Maksymalna niezawodność: 0x04<br />— Koszt minimalny: 0x02 |
|***16-bitowa łączna długość*** |To pole zawiera łączną długość datagramu IP w bajtach, z uwzględnieniem nagłówka IP. Datagram IP to podstawowa jednostka informacji dostępnych w Internecie TCP/IP. Zawiera adres docelowy i źródłowy oprócz danych. Ponieważ jest to pole 16-bitowe, maksymalny rozmiar datagramu IP to 65 535 bajtów.|
|***Identyfikacja 16-bitowa*** |Pole to numer używany do unikatowego identyfikowania każdego datagramu IP wysyłanego z hosta. Ta liczba jest zwykle zwiększana po wysłaniu datagramu IP. Jest to szczególnie przydatne w przypadku asemblera odebranych fragmentów pakietów IP.|
|***flagi 3-bitowe*** |To pole zawiera informacje o fragmentacji adresów IP. Bit 14 to bit "Nie fragmentuj". Jeśli ten bit jest ustawiony, wychodzący datagram IP nie zostanie pofragmentowany. Bit 13 to bit "więcej fragmentów". Jeśli ten bit jest ustawiony, zawiera więcej fragmentów. Jeśli ten bit jest wyczyszczony, jest to ostatni fragment pakietu IP.|
|***13-bitowe przesunięcie fragmentu*** |To pole zawiera górne 13 bitów przesunięcia fragmentu. Z tego powodu przesunięcia fragmentów są dozwolone tylko dla granic 8-bajtowych. Pierwszy fragment pofragmentowanego datagramu IP będzie miał ustawiony bit "więcej fragmentów" i ma przesunięcie 0.|
|***8-bitowy czas wygaśnięcia (TTL)*** |To pole zawiera liczbę routerów, które mogą być przekazywane przez ten datagram, co w istocie ogranicza okres istnienia datagramu.|
|***Protokół 8-bitowy***|To pole określa, który protokół korzysta z datagramu IP. Poniżej znajduje się lista prawidłowych protokołów i ich wartości:<br />-ICMP: 0x01 <br />-IGMP: 0x02<br />-TCP: 0X06<br />-UDP: 0X11 |
|***16-bitowa suma kontrolna*** |To pole zawiera 16-bitową sumę kontrolną obejmującą tylko nagłówek IP. Istnieją dodatkowe sumy kontrolne w protokołach wyższego poziomu, które obejmują ładunek IP. |
|***32-bitowy źródłowy adres IP*** |To pole zawiera adres IP nadawcy i zawsze jest adresem hosta. |
|***32-bitowy docelowy adres IP*** |To pole zawiera adres IP odbiorcy lub odbiorników, jeśli adres jest adresem emisji lub multiemisji. |

### <a name="creating-ip-instances"></a>Tworzenie wystąpień adresów IP

Wystąpienia adresów IP są tworzone podczas inicjowania lub podczas wykonywania przez wątki aplikacji. Początkowy adres IPv4, maskę sieci, domyślną pulę pakietów, sterownik nośnika oraz rozmiar pamięci i priorytet wewnętrznego wątku IP są definiowane przez usługę ***nx_ip_create***, nawet jeśli aplikacja nie będzie korzystać tylko z sieci IPv6. Jeśli aplikacja inicjuje wystąpienie IP z ustawionym adresem IPv4 jako nieprawidłowy adres (0.0.0.0), zakłada się, że adres interfejsu jest rozpoznawany przez ręczną konfigurację później, za pośrednictwem RARP lub za pośrednictwem protokołu DHCP lub podobnych protokołów.

W przypadku systemów z wieloma interfejsami sieciowymi interfejs podstawowy jest wyznaczany podczas wywoływania ***nx_ip_create** _. Każdy dodatkowy interfejs może być dołączony do tego samego wystąpienia IP przez wywołanie _ *_nx_ip_interface_attach_* *. Ta usługa przechowuje informacje o interfejsie sieciowym (takim jak adres IP, maska sieci) w bloku sterowania interfejsem i kojarzy wystąpienie sterownika z blokiem sterowania interfejsem w wystąpieniu protokołu IP. Ponieważ sterownik odbiera pakiet danych, musi przechowywać informacje o interfejsie w strukturze NX_PACKET przed przekazaniem ich do logiki odbioru adresów IP. Przed dołączeniem interfejsów należy pamiętać o utworzeniu wystąpienia adresu IP.

Usługi IPv6 nie są uruchamiane po wywołaniu ***nx_ip_create** _. Aplikacje chcące korzystać z usług IPv6 muszą wywoływać usługę _ *_nx_ipv6_enable_**, aby uruchomić protokół IPv6.

W sieci IPv6 każdy interfejs w wystąpieniu IP może mieć wiele adresów globalnych IPv6. Oprócz używania protokołu DHCPv6 do przypisywania adresów IPv6 urządzenie może również korzystać z automatycznej konfiguracji adresu bezstanowego. Więcej informacji można znaleźć w sekcjach "blok kontroli IP" i "rozpoznawanie adresów IPv6" w dalszej części tego rozdziału.

### <a name="ip-send"></a>Wysyłanie IP

Przetwarzanie wysyłania IP w NetX Duo jest bardzo usprawnione. Wskaźnik dołączania w pakiecie jest przenoszony do tyłu w celu uwzględnienia nagłówka IP. Nagłówek IP zostanie ukończony (ze wszystkimi opcjami określonymi przez warstwę protokołu wywołującego), suma kontrolna protokołu IP jest obliczana w wierszu (tylko dla pakietów IPv4), a pakiet jest wysyłany do skojarzonego sterownika sieciowego. Ponadto wychodząca fragmentacja jest również koordynowana z poziomu przetwarzania wysyłania adresów IP.

W przypadku protokołu IPv4 NetX Duo inicjuje żądania ARP, jeśli dla docelowego adresu IP jest wymagana mapowanie fizyczne. Protokół IPv6 używa funkcji odnajdywania sąsiadów dla mapowania IPv6-Address-tophysical-Address.

> [!NOTE]
> *W przypadku połączenia IPv4 pakiety wymagające rozpoznawania adresów IP (tj. mapowanie fizyczne) są umieszczane w kolejce protokołu ARP do momentu, aż liczba pakietów w kolejce przekroczy głębokość kolejki ARP (zdefiniowana przez symbol **NX_ARP_MAX_QUEUE_DEPTH**). Jeśli osiągnięto głębokość kolejki, NetX Duo usunie najstarszy pakiet w kolejce i kontynuuje oczekiwanie na rozpoznanie adresu dla pozostałych pakietów w kolejce. Z drugiej strony, Jeśli wpis ARP nie zostanie rozwiązany, oczekujące pakiety we wpisie ARP zostaną wydane po upływie limitu czasu wpisu ARP.*

W przypadku systemów z wieloma interfejsami sieciowymi NetX Duo wybiera interfejs oparty na docelowym adresie IP. Poniższa procedura dotyczy procesu wyboru:

1. Jeśli nadawca określa interfejs wychodzący, a interfejs jest prawidłowy, użyj tego interfejsu.
2. Jeśli adres docelowy to emisja IPv4 lub Multiemisja, zostanie użyty pierwszy włączony interfejs fizyczny.
3. Jeśli w statycznej tabeli routingu zostanie znaleziony adres docelowy, używany jest interfejs skojarzony z bramą.
4. Jeśli miejsce docelowe jest połączone z linkiem, używany jest interfejs on-link.
5. Jeśli adres docelowy jest adresem lokalnym łącza (169.254.0.0/16), używany jest pierwszy prawidłowy interfejs.
6. Jeśli Brama domyślna jest skonfigurowana, użyj interfejsu skojarzonego z bramą domyślną, aby przesłać pakiet.
7. Na koniec, jeśli jeden z prawidłowych adresów IP interfejsu jest adresem lokalnym linku (169.254.0.0/16), ten interfejs jest używany jako adres źródłowy transmisji.
8. Pakiet wyjściowy zostanie porzucony w przypadku niepowodzenia wszystkich powyższych elementów.

### <a name="ip-receive"></a>Odbieranie adresów IP

Przetwarzanie odbierania adresów IP jest wywoływane ze sterownika sieci lub wewnętrznego wątku IP (na potrzeby przetwarzania pakietów w odroczonej kolejce odebranych pakietów). Przetwarzanie odbierania adresów IP bada pole Protokół i próbuje wysłać pakiet do odpowiedniego składnika protokołu. Zanim pakiet zostanie faktycznie wysłany, Nagłówek IP zostanie usunięty przez przeciąganie wskaźnika dołączania do nagłówka IP.

Przetwarzanie odbierania adresów IP również wykrywa pofragmentowane pakiety IP i wykonuje niezbędne kroki, aby ponownie je połączyć w przypadku włączenia fragmentacji. Jeśli fragmentacja jest potrzebna, ale nie jest włączona, pakiet zostanie porzucony.

NetX Duo określa odpowiedni interfejs sieciowy w oparciu o interfejs określony w pakiecie. Jeśli interfejs pakietu ma wartość NULL, NetX Duo domyślnie jest interfejsem podstawowym. Jest to realizowane w celu zagwarantowania zgodności ze starszymi sterownikami Ethernet NetX Duo.

### <a name="raw-ip-send"></a>Wysyłanie nieprzetworzonego adresu IP

Pakiet Raw IP jest ramką IP, która zawiera ładunek protokołu warstwy wyższej, który nie jest bezpośrednio obsługiwany (i przetwarzany) przez NetX Duo. Pakiet Raw umożliwia deweloperom Definiowanie własnych aplikacji opartych na protokole IP. Aplikacja może wysyłać pakiety pierwotnych adresów IP bezpośrednio przy użyciu usługi ***nxd_ip_raw_packet_send** _, jeśli w usłudze _*_nx_ip_raw_packet_enabled_*_ włączono przetwarzanie pakietów pierwotnych adresów IP. Podczas transmisji pakietu emisji pojedynczej w sieci IPv6 NetX Duo automatycznie określa najlepszy źródłowy adres IPv6 do użycia w celu wysyłania pakietów na podstawie adresu docelowego. Jeśli adres docelowy jest adresem multiemisji (lub emisji dla protokołu IPv4), NetX Duo będzie domyślnie miał pierwszy (podstawowy) interfejs. W związku z tym, aby wysłać takie pakiety w interfejsach pomocniczych, aplikacja musi używać usługi _ *_nx_ip_raw_packet_source_send_**, aby określić adres źródłowy do użycia dla pakietu wychodzącego.

### <a name="raw-ip-receive"></a>Nieprzetworzony adres IP

Jeśli przetwarzanie pakietów pierwotnych adresów IP jest włączone, aplikacja może odbierać pakiety pierwotnych adresów IP za pomocą usługi ***nx_ip_raw_packet_receive** _. Wszystkie pakiety przychodzące są przetwarzane zgodnie z protokołem określonym w nagłówku IP. Jeśli protokół określa UDP, TCP, IGMP lub ICMP, NetX Duo przetworzy pakiet przy użyciu odpowiedniego programu obsługi dla typu protokołu pakietu. Jeśli protokół nie jest jednym z tych protokołów, a odbieranie pierwotnego adresu IP jest włączone, pakiet przychodzący zostanie umieszczony w kolejce pakietów nieprzetworzonych, oczekując na odbiór aplikacji za pośrednictwem _usługi *_nx_ip_raw_packet_receive_**. Ponadto wątki aplikacji mogą wstrzymywać z opcjonalnym limitem czasu podczas oczekiwania na pakiet Raw IP. Liczba pakietów, które można umieścić w kolejce w nieprzetworzonej kolejce pakietów, jest ograniczona. Wartość maksymalna jest zdefiniowana w ***NX_IP_RAW_MAX_QUEUE_DEPTH**_, której wartością domyślną jest 20. Aplikacja może zmienić wartość maksymalną przez wywołanie _ *_nx_ip_raw_receive_queue_max_set_** usługi.

Alternatywnie Biblioteka NetX Duo może być skompilowana przy użyciu ***NX_ENABLE_IP_RAW_PACKET_FILTER *.** W tym trybie działania aplikacja udostępnia funkcję wywołania zwrotnego, która jest wywoływana za każdym razem, gdy jest odbierany pakiet z nieobsługiwanym typem protokołu. Logika odbierania adresów IP przekazuje pakiet do procedury filtru uzyskiwania pakietów nieprzetworzonych przez użytkownika. Procedura filtrowania decyduje o tym, czy zachować nieprzetworzony pakiet dla przyszłego procesu. Wartość zwracana z procedury wywołania zwrotnego wskazuje, czy pakiet został przetworzony przez filtr odbierania pakietów nieprzetworzonych. Jeśli pakiet jest przetwarzany przez funkcję wywołania zwrotnego, pakiet powinien zostać wydzierżawiony po zakończeniu aplikacji z pakietem. W przeciwnym razie NetX Duo jest odpowiedzialny za wydanie pakietu. Zapoznaj się z **_nx_ip_raw_packet_filter_set_** , aby uzyskać więcej informacji na temat używania nieprzetworzonej funkcji filtru pakietów.

> [!NOTE]
> * Funkcja otoki BSD dla NetX Duo korzysta z funkcji nieprzetworzonego filtru pakietów do obsługi niesformatowanych gniazd BSD. W związku z tym, aby obsługiwać surowy gniazd w otoki BSD, biblioteka NetX Duo musi być skompilowana przy użyciu funkcji ***NX_ENABLE_IP_RAW_PACKET_FILTER** _ zdefiniowanej, a aplikacja nie powinna używać _*_nx_ip_raw_packet_filter_set_*_ do instalowania własnych nieprzetworzonych filtrów pakietów Functions._

### <a name="default-packet-pool"></a>Domyślna pula pakietów

Każde wystąpienie IP otrzymuje domyślną pulę pakietów podczas tworzenia. Ta Pula pakietów służy do przydzielania pakietów dla protokołów ARP, RARP, ICMP, IGMP, różnych pakietów kontroli TCP (SYN, ACK itd.), odnajdywania sąsiadów, odnajdywania routera i wykrywania zduplikowanych adresów. Jeśli domyślna pula pakietów jest pusta, gdy NetX Duo wymaga przydzielenia pakietu, NetX Duo może być konieczne przerwanie określonej operacji i zwrócenie komunikatu o błędzie, jeśli jest to możliwe.

### <a name="ip-helper-thread"></a>Wątek pomocnika IP

Każde wystąpienie protokołu IP ma wątek pomocnika. Ten wątek jest odpowiedzialny za obsługę całego odroczonego przetwarzania pakietów i całego przetwarzania okresowego. Wątek pomocnika IP jest tworzony w ***nx_ip_create.*** Jest to miejsce, w którym wątek otrzymuje swój stos i priorytet. Należy zauważyć, że pierwsze przetwarzanie w wątku pomocnika IP to zakończenie inicjowania sterownika sieci skojarzonego z usługą IP Create. Po zakończeniu inicjalizacji sterownika sieci wątek pomocniczy uruchamia nieskończoną pętlę, aby przetwarzać pakiety i okresowo żądania.

> [!IMPORTANT]
> *Jeśli w wątku pomocnika adresów IP jest widoczne niewyjaśnione zachowanie, zwiększenie rozmiaru stosu w trakcie tworzenia usługi IP to pierwszy krok debugowania. Jeśli stos jest za mały, wątek pomocnika IP może spowodować zastępowanie pamięci, co może prowadzić do nietypowych problemów.*

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać podczas próby odbierania pakietów pierwotnych adresów IP. Po odebraniu pakietu RAW nowy pakiet jest przyznany do pierwszego wątku zawieszanego i ten wątek zostaje wznowiony. Usługi NetX Duo dla odbieranych pakietów mają opcjonalny limit czasu zawieszenia. Po odebraniu pakietu lub upływie limitu czasu wątek aplikacji zostaje wznowiony z odpowiednim stanem ukończenia.

### <a name="ip-statistics-and-errors"></a>Statystyka i błędy adresów IP

Jeśli ta opcja jest włączona, NetX Duo śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia IP są obsługiwane następujące raporty statystyczne i błędy:

- Całkowita liczba wysłanych pakietów IP
- Całkowita liczba wysłanych bajtów IP
- Całkowita liczba odebranych pakietów IP
- Całkowita liczba odebranych bajtów IP
- Łączna liczba nieprawidłowych pakietów adresu IP
- Całkowita liczba porzuconych pakietów odebranych adresów IP
- Łączne błędy sum kontrolnych odbierania adresów IP
- Całkowita liczba porzuconych pakietów wysłanych przez protokół IP
- Całkowita liczba wysłanych fragmentów adresów IP
- Całkowita liczba odebranych fragmentów adresów IP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_ip_info_get***.

### <a name="ip-control-block-nx_ip"></a>NX_IP bloku kontroli adresów IP

Charakterystyka każdego wystąpienia IP znajduje się w jego bloku sterowania. Zawiera ona przydatne informacje, takie jak adresy IP i maski sieci poszczególnych urządzeń sieciowych, a także tabela z oddzielnym adresem IP sąsiada i fizycznymi adresami sprzętowymi. Ta struktura jest zdefiniowana w _file ***nx_api. h**. Jeśli protokół IPv6 jest włączony, zawiera również tablicę adresów IPv6, która jest określana przez użytkownika, który można skonfigurować za pomocą opcji% *_NX_MAX_IPV6_ADDRESSES_* *. Wartość domyślna pozwala każdemu fizycznemu interfejsowi sieci na posiadanie trzech adresów IPv6.

Bloki kontroli wystąpień IP mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="static-ipv4-routing"></a>Statyczny routing IPv4

Funkcja statycznego routingu umożliwia aplikacji określenie sieci IPv4 i adresu następnego przeskoku dla określonych brakujących docelowych adresów IP. Jeśli routing statyczny jest włączony, NetX Duo przeszukuje tabelę routingu statycznego dla wpisu zgodnego z adresem docelowym pakietu do wysłania. Jeśli nie zostanie znalezione dopasowanie, NetX Duo przeszukuje listę interfejsów fizycznych i wybiera źródłowy adres IP i adres następnego przeskoku na podstawie docelowego adresu IP i maski sieci. Jeśli miejsce docelowe nie jest zgodne z żadnym z adresów IP sterowników sieciowych dołączonych do wystąpienia IP, NetX Duo wybiera interfejs, który jest bezpośrednio połączony z bramą domyślną, i używa adresu IP interfejsu jako adresu źródłowego i bramy domyślnej jako następnego przeskoku.

Wpisy można dodawać i usuwać ze statycznej tabeli routingu odpowiednio przy użyciu ***nx_ip_static_route_add** _ i _ *_nx_ip_static_route_delete_** usług. Aby można było używać routingu statycznego, aplikacja hosta musi włączyć tę funkcję, definiując ***NX_ENABLE_IP_STATIC_ROUTING.***

> [!NOTE]
> *Podczas dodawania wpisu do statycznej tabeli routingu NetX Duo sprawdza pasujący wpis dla określonego adresu docelowego, który znajduje się już w tabeli. Jeśli taki istnieje, zapewnia preferencję dla wpisu z mniejszą siecią (dłuższym prefiksem) w masce sieci.*

### <a name="ipv4-forwarding"></a>Przekazywanie IPv4

Jeśli przychodzący pakiet IPv4 nie jest przeznaczony dla tego węzła i włączono funkcję przekazywania protokołu IPv4, NetX Duo podejmie próbę przesłania pakietu za pośrednictwem innych interfejsów.  

### <a name="ip-fragmentation"></a>Fragmentacja IP

Urządzenie sieciowe może mieć limity rozmiaru pakietów wychodzących. Ten limit jest określany jako maksymalna jednostka transmisji (MTU). Jednostka MTU protokołu IP to największy rozmiar ramki IP, który sterownik warstwy linku jest w stanie przesłać bez fragmentacji pakietu IP. Podczas fazy inicjowania sterownika urządzenia moduł sterownika musi skonfigurować jego rozmiar jednostki adresów IP przy użyciu ***nx_ip_interface_mtu_set usługi.***

Chociaż nie jest to zalecane, aplikacja może generować datagramy większe niż bazowa Jednostka MTU IP obsługiwana przez urządzenie. Przed przesłaniem takiego datagramu IP warstwa IP musi być pofragmentowana tych pakietów. W przypadku odebrania pofragmentowanych ramek IP na końcu musi być przechowywane wszystkie pofragmentowane ramki IP o tym samym IDENTYFIKATORze fragmentacji, a następnie ponownie nastąpić ich umieszczenie w określonej kolejności. Jeśli logika odbierania IP nie może zebrać wszystkich fragmentów, aby przywrócić pierwotną ramkę IP w czasie, wszystkie fragmenty zostaną wydane. Jest on do protokołu warstwy wyższej, aby wykryć tę utratę pakietów i odzyskać ją z niej.

Fragmentacja IP dotyczy zarówno pakietów IPv4, jak i IPv6.

Aby można było obsługiwać fragmentację i operacje ponownego montażu IP, projektant systemu musi włączyć funkcję fragmentacji IP w NetX Duo przy użyciu usługi ***nx_ip_fragment_enable*** . Jeśli ta funkcja nie jest włączona, przychodzące pofragmentowane pakiety IP są odrzucane, a także pakiety, które przekraczają jednostkę MTU sterownika sieci.

> [!NOTE]
> * Logika fragmentacji IP można całkowicie usunąć, definiując ***NX_DISABLE_FRAGMENTATION** _ podczas kompilowania biblioteki NetX Duo. Pozwoli to zmniejszyć rozmiar kodu NetX Duo. Należy zauważyć, że w takiej sytuacji zarówno funkcja fragmentacji protokołu IPv4, jak i IPv6 są disabled._

> [!NOTE]
> *Jeśli zdefiniowano **NX_DISABLE_CHAINED_PACKET** , fragmentacja IP musi być wyłączona.*

> [!NOTE]
> *W sieci IPv6 routery nie pofragmentowanie datagramu, jeśli rozmiar datagramu przekroczy minimalny rozmiar jednostki MTU. W związku z tym do urządzenia wysyłającego należy określić minimalną wartość MTU między źródłem a miejscem docelowym, a w celu upewnienia się, że rozmiar datagramu IP nie przekracza ścieżki MTU. W NetX Duo można włączyć odnajdowanie MTU ścieżki IPv6, tworząc bibliotekę NetX Duo z zdefiniowanym symbolem **NX_ENABLE_IPV6_PATH_MTU_DISCOVERY** .*

## <a name="address-resolution-protocol-arp-in-ipv4"></a>Protokół ARP (Address Resolution Protocol) w protokole IPv4

Protokół ARP (Address Resolution Protocol) jest odpowiedzialny za dynamiczne mapowanie 32-bitowych adresów IPv4 na te, które są bazowego nośnika fizycznego (RFC 826). Ethernet jest najbardziej typowym nośnikiem fizycznym i obsługuje adresy 48-bitowe. Potrzeba protokołu ARP jest określana przez sterownik sieciowy dostarczony do usługi ***nx_ip_create** _. Jeśli wymagane jest mapowanie fizyczne, Sterownik sieciowy musi używać usługi _ *_nx_interface_address_mapping_needed_** do prawidłowego konfigurowania interfejsu sterownika.

### <a name="arp-enable"></a>Włączanie protokołu ARP

Aby protokół ARP działał prawidłowo, musi on być najpierw włączony przez aplikację z usługą ***nx_arp_enable*** . Ta usługa konfiguruje różne struktury danych na potrzeby przetwarzania ARP, w tym tworzenie obszaru pamięci podręcznej ARP z pamięci dostarczonej do usługi ARP Enable.

### <a name="arp-cache"></a>Pamięć podręczna ARP

Pamięć podręczna ARP może być wyświetlana jako tablica wewnętrznych struktur danych mapowania ARP. Każda struktura wewnętrzna może utrzymywać relacje między adresem IP a fizycznym adresem sprzętowym. Ponadto każda struktura danych ma wskaźniki łączy, więc może być częścią wielu połączonych list.

Aplikacja może wyszukiwać adres IP z pamięci podręcznej ARP przez dostarczenie sprzętowego adresu MAC przy użyciu usługi ***nx_arp_ip_address_find** _, jeśli mapowanie istnieje w tabeli ARP. Podobnie usługa _ *_nx_arp_hardware_address_find_** zwraca adres MAC dla danego adresu IP.

### <a name="arp-dynamic-entries"></a>Dynamiczne wpisy ARP

Domyślnie usługa ARP Enable umieszcza wszystkie wpisy w pamięci podręcznej ARP na liście dostępnych dynamicznych wpisów ARP. Dynamiczny wpis ARP jest przypisywany z tej listy przez NetX Duo w przypadku wykrycia żądania wysłania do niemapowanego adresu IP. Po przydzieleniu wpis ARP zostaje skonfigurowany, a żądanie ARP jest wysyłane do nośnika fizycznego.

Wpis dynamiczny może być również utworzony przez ***nx_arp_dynamic_entry_set*** usługi.

> [!IMPORTANT]
> *Jeśli wszystkie dynamiczne wpisy ARP są używane, co najmniej ostatnio używany wpis ARP zostanie zastąpiony nowym mapowaniem.*

### <a name="arp-static-entries"></a>Statyczne wpisy ARP

Aplikacja może również skonfigurować statyczne mapowanie ARP przy użyciu _service ***nx_arp_static_entry_create**. Ta usługa przydziela wpis ARP z listy dynamicznego wpisu ARP i umieszcza ją na liście statycznej z informacjami o mapowaniu dostarczanymi przez aplikację. Statyczne wpisy ARP nie mogą być ponownie używane ani przedawnianie. Aplikacja może usunąć wpis statyczny przy użyciu _*_nx_arp_static_entry_delete_*_ usługi. Aby usunąć wszystkie wpisy statyczne w tabeli ARP, aplikacja może używać usługi _ *_nx_arp_static_entries_delete_* *.

### <a name="automatic-arp-entry"></a>Wpis automatyczny ARP

NetX Duo rejestruje mapowanie IP/MAC elementu równorzędnego po odpowiedzi równorzędnych na żądanie ARP. NetX Duo implementuje również funkcję automatycznego wpisu ARP, gdzie rejestruje adresy IP równorzędnego mapowania adresów MAC na podstawie niezamówionych żądań ARP z sieci. Ta funkcja umożliwia wypełnienie tabeli ARP informacjami o komunikacji równorzędnej, co zmniejsza opóźnienie potrzebne do przechodzenia przez cykl żądania/odpowiedzi ARP. Jednak minusem z włączaniem automatycznego protokołu ARP polega na tym, że tabela ARP jest w stanie szybko zapełniać się siecią z wieloma węzłami w łączu lokalnym, co ostatecznie doprowadziłoby do zamiany pozycji ARP.

Ta funkcja jest domyślnie włączona. Aby go wyłączyć, należy skompilować bibliotekę NetX Duo z zdefiniowanym symbolem ***NX_DISABLE_ARP_AUTO_ENTRY***.</p>

### <a name="arp-messages"></a>Komunikaty ARP

Jak wspomniano wcześniej, komunikat żądania ARP jest wysyłany, gdy zadanie IP wykryje, że mapowanie jest niezbędne dla adresu IP. Żądania ARP są wysyłane okresowo (co ***NX_ARP_UPDATE_RATE** _ sekund) do momentu otrzymania odpowiedniej odpowiedzi ARP. Całkowita liczba żądań ARP wynosząca _ *_NX_ARP_MAXIMUM_RETRIES_** przed porzucić próbą ARP. Po odebraniu odpowiedzi ARP skojarzone informacje o adresie fizycznym są przechowywane we wpisie ARP, który znajduje się w pamięci podręcznej.

W przypadku systemów wielodomowych NetX Duo określa interfejs do wysyłania żądań i odpowiedzi ARP na podstawie określonego adresu docelowego.

> [!NOTE]
> *Wychodzące pakiety IP są umieszczane w kolejce, podczas gdy NetX Duo czeka na odpowiedź ARP. Liczba wychodzących pakietów IP umieszczonych w kolejce jest definiowana przez stałą **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX Duo reaguje także na żądania ARP z innych węzłów w lokalnej sieci IPv4. Po utworzeniu zewnętrznego żądania ARP zgodnego z bieżącym adresem IP interfejsu, który odbiera żądanie ARP, NetX Duo kompiluje komunikat odpowiedzi ARP zawierający bieżący adres fizyczny.

Formaty żądań i odpowiedzi Ethernet ARP przedstawiono na rysunku 6 i opisano poniżej.

| **Pole żądania/odpowiedzi &nbsp;**         | **Cel**            |
| ---------------------------------- | ---------------------- |
| ***Adres docelowy sieci Ethernet*** | To 6-bajtowe pole zawiera adres docelowy odpowiedzi ARP i jest emisją (wszystkie) dla żądań ARP. To pole jest konfiguracją przez sterownik sieciowy. 
| ***Adres źródłowy sieci Ethernet***      | To 6-bajtowe pole zawiera adres nadawcy żądania lub odpowiedzi ARP i jest skonfigurowany przez sterownik sieciowy. |
| ***Typ ramki*** | To pole 2-bajtowe zawiera typ ramki Ethernet, a w przypadku żądań i odpowiedzi ARP jest to równe 0x0806. Jest to ostatnie pole, za pomocą którego sterownik sieciowy jest odpowiedzialny za konfigurowanie. |
| ***Typ sprzętu*** | To pole 2-bajtowe zawiera typ sprzętu, który jest 0x0001 dla sieci Ethernet. |
| ***Typ protokołu*** | To pole 2-bajtowe zawiera typ protokołu, który jest 0x0800 dla adresów IP. |
| ***Rozmiar sprzętu*** | To pole 1-bajtowe zawiera rozmiar sprzętowy, który jest 6 dla adresów Ethernet. |

![Diagram formatu pakietu ARP.](./media/user-guide/arp-packet-format.png)

**RYSUNEK 6. Format pakietu ARP**

| Pole żądania/odpowiedzi &nbsp; | Przeznaczenie |
|---|---|
| ***Rozmiar protokołu*** | To pole 1-bajtowe zawiera rozmiar adresu IP, czyli 4 dla adresów IP. |
| ***Kod operacji*** | To pole 2-bajtowe zawiera operację dla tego pakietu ARP. W żądaniu ARP jest określana wartość 0x0001, podczas gdy odpowiedź ARP jest reprezentowana przez wartość 0x0002. |
| ***Adres Ethernet nadawcy*** | To 6-bajtowe pole zawiera adres Ethernet nadawcy. |
| ***Adres IP nadawcy*** | To pole 4-bajtowe zawiera adres IP nadawcy. |
| ***Docelowy adres ethernetowy*** | To pole 6-bajtowe zawiera adres Ethernet docelowy. |
| ***Docelowy adres IP*** | To pole 4-bajtowe zawiera adres IP miejsca docelowego. |

> [!NOTE]
> *Żądania i odpowiedzi ARP są pakietami na poziomie sieci Ethernet. Wszystkie inne pakiety TCP/IP są hermetyzowane przez nagłówek pakietu IP.*

> [!NOTE]
> *Oczekuje się, że wszystkie komunikaty ARP w implementacji protokołu TCP/IP mają być w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="arp-aging"></a>Przedawnianie protokołu ARP

NetX obsługuje automatyczne unieważnianie wpisów dynamicznego ARP. ***NX_ARP_EXPIRATION_RATE** _ określa liczbę sekund, przez jaką ustanowiony adres IP dla mapowania fizycznego pozostaje prawidłowy. Po wygaśnięciu wpis ARP zostanie usunięty z pamięci podręcznej ARP. Kolejna próba wysłania do odpowiedniego adresu IP spowoduje powstanie nowego żądania protokołu ARP. Ustawienie _ *_NX_ARP_EXPIRATION_RATE_** na zero powoduje wyłączenie przedawnienia ARP, co jest konfiguracją domyślną.

### <a name="arp-defend"></a>Obrona protokołu ARP

Po odebraniu żądania ARP lub pakietu odpowiedzi ARP, gdy nadawca ma ten sam adres IP, który powoduje konflikt z adresem IP tego węzła, NetX Duo wysyła żądanie ARP dla tego adresu jako obronność. Jeśli pakiet rozwiązywania konfliktów ARP jest odbierany więcej niż raz w ciągu 10 sekund, NetX Duo nie wyśle więcej pakietów obrony. Domyślny interwał 10 sekund można zdefiniować ponownie przez ***NX_ARP_DEFEND_INTERVAL** _. To zachowanie jest zgodne z zasadami określonymi w 2.4 (c) RFC5227. Ponieważ system Windows XP ignoruje anons protokołu ARP jako odpowiedź na sondę ARP, użytkownik może zdefiniować _ *_NX_ARP_DEFEND_BY_REPLY_**, aby wysłać odpowiedź ARP jako dodatkową obronę.

### <a name="arp-statistics-and-errors"></a>Statystyki i błędy dotyczące protokołu ARP

Jeśli ta opcja jest włączona, oprogramowanie NetX Duo ARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i błędy są obsługiwane dla każdego przetwarzania ARP IP:

- Całkowita liczba wysłanych żądań ARP
- Całkowita liczba odebranych żądań ARP
- Całkowita liczba wysłanych odpowiedzi ARP 
- Całkowita liczba odebranych odpowiedzi ARP 
- Łączna liczba wpisów dynamicznych ARP 
- Łączna liczba wpisów statycznych ARP 
- Łączna liczba przestarzałych wpisów ARP 
- Całkowita liczba nieprawidłowych komunikatów ARP 

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_arp_info_get*** .

## <a name="reverse-address-resolution-protocol-rarp-in-ipv4"></a>Protokół odwrotnego rozpoznawania adresów (RARP) w protokole IPv4

Protokół odwrotnego rozpoznawania adresów (RARP) to protokół służący do żądania przypisania sieci na 32-bitowe adresy IP hosta (RFC 903). Odbywa się to za pomocą żądania RARP i kontynuuje okresowo, dopóki członek sieci przypisze adres IP do interfejsu sieciowego hosta w odpowiedzi RARP. Aplikacja tworzy wystąpienie IP przez usługę ***nx_ip_create*** z zerowym adresem IP. Jeśli RARP jest włączona przez aplikację, może użyć protokołu RARP, aby zażądać adresu IP z serwera sieciowego dostępnego za pośrednictwem interfejsu, który ma zerowy adres IP.

### <a name="rarp-enable"></a>Włącz RARP

Aby użyć RARP, aplikacja musi utworzyć wystąpienie IP z adresem IP zerowym, a następnie włączyć RARP przy użyciu ***nx_rarp_enable*** usługi. W przypadku systemów wielodomowych co najmniej jedno urządzenie sieciowe skojarzone z wystąpieniem IP musi mieć adres IP równy zero. Przetwarzanie RARP okresowo wysyła komunikaty żądania RARP dla systemu NetX Duo wymagające adresu IP do momentu otrzymania prawidłowej odpowiedzi RARP z wydzielonym adresem IP sieci. W tym momencie przetwarzanie RARP zostało zakończone.

Po włączeniu RARP jest on automatycznie wyłączany po rozwiązaniu wszystkich adresów interfejsu. Aplikacja może wymusić zakończenie RARP przy użyciu usługi ***nx_rarp_disable***.

### <a name="rarp-request"></a>Żądanie RARP

Format pakietu żądania RARP jest niemal identyczny z pakietem ARP pokazanym na [rysunku 6](#arp-messages). Jedyną różnicą jest pole Typ ramki to 0x8035, a pole *kod operacji* to 3, które wyznacza żądanie RARP. Jak wspomniano wcześniej, żądania RARP będą wysyłane okresowo (co ***NX_RARP_UPDATE_RATE*** sekund) do momentu otrzymania odpowiedzi RARP z przypisanym adresem IP sieci.

> [!NOTE]
> *Oczekuje się, że wszystkie komunikaty RARP w implementacji protokołu TCP/IP będą w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="rarp-reply"></a>Odpowiedź RARP

Komunikaty odpowiedzi RARP są odbierane z sieci i zawierają adres IP przypisany do sieci dla tego hosta. Format pakietu odpowiedzi RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku 6. Jedyną różnicą jest pole Typ ramki to 0x8035, a pole *kod operacji* to 4, które wyznacza odpowiedź RARP. Po odebraniu adres IP jest skonfigurowany w wystąpieniu IP, okresowe żądanie RARP jest wyłączone, a wystąpienie protokołu IP jest teraz gotowe do normalnego działania sieci.

W przypadku hostów wielomacierzystych adres IP jest stosowany do żądającego interfejsu sieciowego. Jeśli inne interfejsy sieciowe nadal żądają przypisania adresu IP, okresowa usługa RARP będzie kontynuowana do momentu rozwiązania wszystkich żądań adresów IP interfejsu.

> [!NOTE]
> *Aplikacja nie powinna używać wystąpienia protokołu IP do momentu ukończenia przetwarzania RARP. **Nx_ip_status_check** mogą być używane przez aplikacje w celu oczekiwania na ukończenie RARP. W przypadku systemów wielodomowych aplikacja nie powinna używać interfejsu żądającego do momentu ukończenia przetwarzania RARP w tym interfejsie. Stan adresu IP na urządzeniu pomocniczym można sprawdzić za pomocą usługi **nx_ip_interface_status_check** .*

### <a name="rarp-statistics-and-errors"></a>RARP statystyk i błędów

Jeśli to ustawienie jest włączone, oprogramowanie NetX Duo RARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i błędy są obsługiwane dla każdego RARP IP:

- Całkowita liczba wysłanych żądań RARP
- Całkowita liczba odebranych odpowiedzi RARP
- Całkowita liczba nieprawidłowych komunikatów RARP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_rarp_info_get*** .

## <a name="internet-control-message-protocol-icmp"></a>Protokół ICMP (Internet Control Message Protocol)

Protokół ICMP (Internet Control Message Protocol) dla protokołu IPv4 jest ograniczony do przekazywania informacji o błędach i kontroli między członkami sieci IP. Protokół komunikatów kontroli Internetu dla protokołu IPv6 (ICMPv6) obsługuje również informacje o błędach i kontrolach i jest wymagany w przypadku protokołów rozpoznawania adresów, takich jak wykrywanie zduplikowanych adresów (DAD) i bezstanowe Autokonfiguracja adresu.

Podobnie jak większość innych komunikatów warstwy aplikacji (np. TCP/IP), komunikaty ICMP i ICMPv6 są hermetyzowane przy użyciu nagłówka IP z oznaczeniem protokołu ICMP (lub ICMPv6).

### <a name="icmp-statistics-and-errors"></a>Statystyki i błędy protokołu ICMP

Jeśli ta opcja jest włączona, NetX Duo śledzi kilka statystyk ICMP i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i komunikaty o błędach są obsługiwane dla każdego przetworzenia protokołu ICMP IP: 

- Całkowita liczba wysłanych poleceń ping protokołu ICMP  
- Łączny limit czasu polecenia ping protokołu ICMP 
- Całkowita liczba wstrzymanych wątków ping protokołu ICMP 
- Całkowita liczba odebranych odpowiedzi ping protokołu ICMP 
- Całkowita liczba błędów sumy kontrolnej protokołu ICMP 
- Całkowita liczba nieobsłużonych komunikatów protokołu ICMP 

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_icmp_info_get*** .

## <a name="icmpv4-services-in-netx-duo"></a>Usługi ICMPv4 w NetX Duo

### <a name="icmpv4-enable"></a>Włączanie ICMPv4

Przed przetworzeniem komunikatów ICMPv4 przez NetX Duo aplikacja musi wywoływać usługę ***nx_icmp_enable*** , aby umożliwić przetwarzanie ICMPv4. Po wykonaniu tej czynności aplikacja może wysyłać żądania ping i przychodzące pakiety ping.  

### <a name="icmpv4-echo-request"></a>Żądanie echa ICMPv4

Żądanie echa to jeden typ komunikatu ICMPv4, który jest zazwyczaj używany do sprawdzania istnienia określonego węzła w sieci, zgodnie z jego adresem IP hosta. Popularne polecenie ping jest zaimplementowane przy użyciu komunikatów żądania echa ICMP/echo odpowiedzi. Jeśli określony host jest obecny, jego stos sieciowy przetwarza żądanie ping i odpowiedzi z odpowiedzią ping. Rysunek 7. Szczegóły formatu wiadomości ping protokołu ICMPv4.

![Komunikat ICMPv4 ping](./media/user-guide/icmpv4-ping-message.png)  

**RYSUNEK 7. Komunikat ICMPv4 ping**

> [!NOTE]
> *Oczekuje się, że wszystkie komunikaty ICMPv4 w implementacji protokołu TCP/IP będą w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

Poniżej opisano format nagłówka ICMPv4:

|Pole nagłówka |Przeznaczenie |
|---|---|
|**Typ** |To pole określa komunikat ICMPv4 (bity 31-24). Najczęstsze są następujące:<br />-0: echo odpowiedzi<br />-3: miejsce docelowe jest nieosiągalne<br />-8: żądanie echa<br />-11: przekroczono czas<br />-12: problem z parametrem |
|**Kod** |To pole jest specyficzne dla kontekstu w polu Typ (bity 23-16). Dla żądania echa lub Odpowiedz kod jest ustawiony na zero.|
|**Suma** |To pole zawiera 16-bitową sumę kontrolną łącznej wartości w wiadomości ICMPv4, łącznie z całym nagłówkiem ICMPv4 rozpoczynającym się od pola Type. Przed wygenerowaniem sumy kontrolnej, pole sumy kontrolnej jest wyczyszczone.|
|**Identyfikacja** | To pole zawiera wartość identyfikatora identyfikującą hosta; Host powinien używać identyfikatora wyodrębnionego z żądania echa w odpowiedzi echa (bity 31-16).|
|**Numer sekwencyjny** |To pole zawiera wartość identyfikatora; Host powinien używać identyfikatora wyodrębnionego z żądania echa w odpowiedzi echa (bity 31-16). W przeciwieństwie do pola identyfikatora ta wartość zmieni się w kolejnych żądaniach ECHA z tego samego hosta (bity 15-0).|

### <a name="icmpv4-echo-response"></a>Odpowiedź na ruch ICMPv4    
Odpowiedź ping to inny typ komunikatu ICMP, który jest generowany wewnętrznie przez składnik ICMP w odpowiedzi na zewnętrzne żądanie ping. Oprócz potwierdzenia, odpowiedź na polecenie ping zawiera również kopię danych użytkownika dostarczonych w żądaniu ping.

### <a name="icmpv4-error-messages"></a>Komunikaty o błędach ICMPv4   
W NetX Duo są obsługiwane następujące komunikaty o błędach ICMPv4: 
- Miejsce docelowe jest nieosiągalne 
- Czas przekroczenia 
- Problem z parametrem

## <a name="internet-group-management-protocol-igmp"></a>Protokół IGMP (Internet Group Management Protocol)

Protokół IGMP (Internet Group Management Protocol) udostępnia urządzenie do komunikowania się z jego sąsiadami i routerami, które zamierza otrzymać lub dołączyć do grupy multiemisji IPv4 (RFC 1112 i RFC 2236). Grupa multiemisji jest zasadniczo dynamicznym zbiorem elementów członkowskich sieci i jest reprezentowana przez adres IP klasy D. Członkowie grupy multiemisji mogą opuścić w dowolnym momencie, a nowi członkowie mogą dołączyć w dowolnym momencie. Koordynacja związana z przyłączaniem i opuszczeniem grupy jest odpowiedzialna za IGMP.

> [!NOTE]
> *Protokół IGMP jest przeznaczony tylko dla grup multiemisji IPv4. Nie można jej używać w sieci IPv6.*

### <a name="igmp-enable"></a>Włączanie IGMP     
Przed rozpoczęciem dowolnego działania multiemisji w NetX Duo aplikacja musi wywołać usługę ***nx_igmp_enable*** . Ta usługa wykonuje podstawowe inicjowanie protokołu IGMP w przygotowaniu do obsługi żądań multiemisji.

### <a name="multicast-ipv4-addressing"></a>Adres IPv4 multiemisji  
Jak wspomniano wcześniej, adresy multiemisji w rzeczywistości są adresami IP klasy D, jak pokazano na [rysunku 4](#ipv4-addresses). Mniejsze 28 bitów adresu klasy D odpowiada IDENTYFIKATORowi grupy multiemisji. Istnieje szereg wstępnie zdefiniowanych adresów multiemisji; jednak *adres wszystkich hostów* (244.0.0.1) jest szczególnie istotny dla przetwarzania IGMP. *Adres wszystkie hosty* jest używany przez routery do wysyłania zapytań do wszystkich elementów członkowskich multiemisji w celu raportowania, do których grup multiemisji należą.  

### <a name="physical-address-mapping-in-ipv4"></a>Mapowanie adresów fizycznych w protokole IPv4
Adresy multiemisji klasy D mapują bezpośrednio do fizycznych adresów Ethernet od 01.00.5 e. 00.00.00 do 01.00.5 e. 7F. FF. FF. Mniejsze 23 bity adresu multiemisji IP są mapowane bezpośrednio do mniejszej liczby 23 bitów adresu Ethernet.

### <a name="multicast-group-join"></a>Przyłączanie do grupy multiemisji
Aplikacje, które muszą przyłączyć się do konkretnej grupy multiemisji, mogą to zrobić, wywołując usługę ***nx_igmp_multicast_join*** . Ta usługa śledzi liczbę żądań dołączenia do tej grupy multiemisji. Jeśli jest to pierwsza aplikacja requestto dołączenia do grupy multiemisji, raport IGMP jest wysyłany w sieci podstawowej wskazującej zamiar tego hosta do przyłączenia do grupy. Następnie sterownik sieciowy jest wywoływany w celu skonfigurowania nasłuchiwania pakietów z adresem Ethernet dla tej grupy multiemisji.

W systemie wielodostępnym, jeśli grupa multiemisji jest dostępna za pośrednictwem określonego interfejsu, aplikacja będzie używać usługi ***nx_igmp_multicast_interface_join** _ zamiast _ *_nx_igmp_multicast_join_* *, która jest ograniczona do grup multiemisji w sieci podstawowej.

### <a name="multicast-group-leave"></a>Opuszczenie grupy multiemisji   
Aplikacje, które muszą opuścić wcześniej dołączoną grupę multiemisji, mogą to zrobić, wywołując usługę ***nx_igmp_multicast_leave*** . Ta usługa zmniejsza liczbę wewnętrzną skojarzoną z tym, ile razy Grupa została przyłączona. Jeśli nie ma żadnych oczekujących żądań dołączenia do grupy, Sterownik sieciowy jest wywoływany, aby wyłączyć nasłuchiwanie pakietów z adresem Ethernet tego grupy multiemisji.

### <a name="multicast-loopback"></a>Sprzężenie zwrotne multiemisji    
Aplikacja może chcieć odebrać ruch multiemisji pochodzący z jednego ze źródeł w tym samym węźle. Wymaga to, aby składnik multiemisji protokołu IP miał włączoną funkcję sprzężenia zwrotnego przy użyciu ***nx_igmp_loopback_enable*** usługi.

### <a name="igmp-report-message"></a>Komunikat raportu IGMP      
Gdy aplikacja jest dołączana do grupy multiemisji, komunikat raportu IGMP jest wysyłany za pośrednictwem sieci, aby wskazać zamiar hosta do przyłączenia do określonej grupy multiemisji. Format komunikatu IGMP jest przedstawiony na rysunku 8. Adres grupy multiemisji jest używany zarówno w komunikacie grupy w komunikacie z raportem IGMP, jak i docelowym adresie IP.

Na powyższym rysunku (rysunek 8) nagłówek IGMP zawiera pole wersji/typu, maksymalną odpowiedź

![Diagram komunikatów raportu IGMP.](./media/user-guide/image17.jpg)

**RYSUNEK 8. Komunikat raportu IGMP**

godzina, pole sumy kontrolnej i pole adres grupy multiemisji. W przypadku komunikatów IGMPv1 wartość pola Maksymalny czas odpowiedzi jest zawsze równa zero, ponieważ nie jest to część protokołu IGMPv1. Pole Maksymalny czas odpowiedzi jest ustawiane, gdy host odbierze komunikat IGMP i wyczyszczony, gdy host odbierze komunikat typu raport innego hosta określony przez protokół IGMPv2.

Poniżej opisano format nagłówka IGMP:

|Pole nagłówka|Przeznaczenie|
|---|---|
|**Wersja** |To pole określa wersję protokołu IGMP (BITS 31-28).|
|**Typ** |To pole określa typ komunikatu IGMP (bity 27 -24).|
|**Maksymalny czas odpowiedzi** |Nieużywane w protokole IGMP v1. W protokole IGMP V2 to pole służy jako maksymalny czas odpowiedzi.|
|**Suma** |To pole zawiera 16-bitową sumę kontrolną podsumowania dla komunikatu IGMP rozpoczynającego się od wersji IGMP (bity 0-15).|
|**Adres grupy** |32-bitowy adres IP grupy klasy D|

Komunikaty raportów IGMP są również wysyłane w odpowiedzi na komunikaty zapytania IGMP wysyłane przez router multiemisji. Routery multiemisji okresowo wysyłają komunikaty zapytania, aby zobaczyć, które hosty nadal wymagają członkostwa w grupie. Komunikaty zapytania mają taki sam format, jak komunikat raportu IGMP przedstawiony na rysunku 8. Jedyną różnicą jest to, że typ IGMP jest równy 1, a pole adres grupy jest ustawione na 0. Komunikaty protokołu IGMP są wysyłane do adresu IP *wszystkie hosty* przez router multiemisji. Host, który nadal chce zachować członkostwo w grupie odpowiada, wysyłając inny komunikat raportu IGMP.

> [!NOTE]
> *Oczekuje się, że wszystkie komunikaty w implementacji protokołu TCP/IP będą w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="igmp-statistics-and-errors"></a>Statystyka i błędy IGMP    
<th><p>Jeśli to ustawienie jest włączone, oprogramowanie IGMP NetX Duo śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i błędy są obsługiwane dla każdego przetwarzania IGMP IP: 

- Całkowita liczba wysłanych raportów IGMP 
- Całkowita liczba odebranych zapytań IGMP 
- Łączna liczba błędów sum kontrolnych IGMP 
- Łączna liczba przyłączonych bieżących grup protokołu IGMP 

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_igmp_info_get***. 

### <a name="multicast-without-igmp"></a>Multiemisja bez protokołu IGMP  
Aplikacja wymagająca ruchu multiemisji IPv4 może przyłączyć się do adresu grupy multiemisji bez wywoływania komunikatów IGMP przy użyciu usługi ***nx_ipv4_multicast_interface_join***. Ta usługa instruuje warstwę IPv4 i źródłowy sterownik interfejsu, aby akceptować pakiety ze wskazanego adresu IPv4 multiemisji. Nie ma jednak żadnych komunikatów zarządzania grupami IGMP, które są wysyłane lub przetwarzane dla tej grupy.

Aplikacja nie chce już odbierać ruchu z grupy, może używać ***nx_ipv4_multicast_interface_leave usługi.***

## <a name="ipv6-in-netx-duo"></a>IPv6 w NetX Duo

### <a name="ipv6-addresses"></a>Adresy IPv6   
Adresy IPv6 to 128 bitów. Architektura adresu IPv6 jest opisana w dokumencie RFC 4291. Adres jest podzielony na prefiks zawierający najbardziej znaczące bity i adres hosta zawierający mniejsze bity. Prefiks wskazuje typ adresu i jest w przybliżeniu odpowiednikiem adresu sieciowego w sieci IPv4.

Protokół IPv6 ma trzy typy specyfikacji adresów: emisja pojedyncza (nieobsługiwana w NetX Duo) i multiemisja. Adresy emisji pojedynczej to adresy IP, które identyfikują określonego hosta w Internecie. Adresy emisji pojedynczej mogą być źródłem lub docelowym adresem IP. Adresy multiemisji określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączać się i zostawiać w dowolnym momencie.

Protokół IPv6 nie jest odpowiednikiem mechanizmu emisji IPv4. Możliwość wysyłania pakietu do wszystkich hostów można osiągnąć, wysyłając pakiet do grupy multiemisji wszystkie hosty na wszystkich hostach.

Protokół IPv6 korzysta z adresów multiemisji w celu przeprowadzenia procedury odnajdywania sąsiadów, odnajdywania routera i bezstanowego usuwania adresów.

Istnieją dwa typy adresów emisji pojedynczej IPv6: Połącz adresy lokalne, zazwyczaj skonstruowane przez połączenie dobrze znanego prefiksu lokalnego linku z adresem MAC interfejsu i globalnych adresów IP, które również zawiera część prefiksu i część identyfikatora hosta. Adres globalny można skonfigurować ręcznie lub za pomocą autokonfiguracji adresu bezstanowego lub protokołu DHCPv6. NetX Duo obsługuje zarówno adres lokalny łącza, jak i adres globalny.

W celu uwzględnienia formatów protokołów IPv4 i IPv6 NetX Duo udostępnia nowy typ danych, NXD_ADDRESS do przechowywania adresów IPv4 i IPv6. Definicja tej struktury jest pokazana poniżej. Pole adres jest związkiem adresów IPv4 i IPv6.

```c
typedef struct NXD_ADDRESS_STRUCT
{
    ULONG nxd_ip_version;
    union
    {
        ULONG v4;
        ULONG v6[4];
    } nxd_ip_address;
} NXD_ADDRESS;
```

W strukturze NXD_ADDRESS pierwszy element, *nxd_ip_version*, wskazuje wersję IPv4 lub IPv6. Obsługiwane wartości to NX_IP_VERSION_V4 lub NX_IP_VERSION_V6. *nxd_ip_version* wskazuje, które pole w Unii *nxd_ip_address* ma być używane jako adres IP. Usługi interfejsu API NetX Duo zazwyczaj przyjmują wskaźnik do NXD_ADDRESS struktury jako argument wejściowy zamiast adresu IP ULONG (32-bitowy).

### <a name="link-local-addresses"></a>Połącz adresy lokalne     
Adres lokalny link jest prawidłowy tylko w sieci lokalnej. Urządzenie może wysyłać i odbierać pakiety do innego urządzenia w tej samej sieci po przypisaniu prawidłowego adresu lokalnego łącza. Aplikacja przypisuje adres lokalny łącza, wywołując usługę NetX Duo ***nxd_ipv6_address_set***, z parametrem Length prefiksem ustawionym na 10. Aplikacja może dostarczyć adres lokalny dla linku do usługi lub może po prostu użyć NX_NULL jako adresu lokalnego linku i zezwolić NetX Duo na konstruowanie adresu lokalnego łącza na podstawie adresu MAC urządzenia.

Poniższy przykład instruuje NetX Duo, aby skonfigurować adres lokalny łącza z prefiksem 10 na urządzeniu podstawowym (indeks 0) przy użyciu adresu MAC:

```c
nxd_ipv6_address_set(ip_ptr, 0, NX_NULL, 10, NX_NULL);
```
W powyższym przykładzie, jeśli adres MAC interfejsu to 54:32:10:1A: BC: 67, odpowiedni adres lokalny łącza:

```c
FE80::5632:10FF:FE1A:BC67
```
Zwróć uwagę, że część identyfikatora hosta adresu IPv6 (**5632:10FF: FE1A: BC67**) składa się z 6-bajtowego adresu Mac z następującymi modyfikacjami:

- **0xFFFE** wstawiona między bajtami 3 i 4 adresu Mac
- Drugi najniższy bit pierwszego bajtu adresu MAC (bit U/L) jest ustawiony na 1

Aby uzyskać więcej informacji na temat konstruowania części hosta adresu IPv6 przy użyciu adresu MAC interfejsu, zobacz RFC 2464 (przesyłanie pakietów IPv6 przez sieć Ethernet).

Istnieje kilka specjalnych adresów multiemisji do wysyłania komunikatów multiemisji do co najmniej jednego hosta w protokole IPv6:

| Group (Grupa)  | Adres   | Opis  |
|---|---|---|
|Grupa wszystkich węzłów |**FF02:: 1** |Wszystkie hosty w sieci lokalnej|
|Grupa wszystkich routerów |**FF02:: 2** |Wszystkie routery w sieci lokalnej|
|Żądanie-węzeł |**FF02:: 1: FF00:0/104** |Wyjaśniono poniżej|

Adres multiemisji węzła na żądanie jest przeznaczony dla konkretnych hostów w łączu lokalnym, a nie na wszystkich hostach IPv6. Składa się z prefiksu **FF02:: 1: FF00:0/104**, czyli 104 bitów i ostatnich 24 bitów docelowego adresu IPv6. Na przykład adres IPv6 **205B: 209D: D028:: F058: D1C8:1024** ma adres multiemisji solicitednode o adresie **FF02:: 1: FFC8:1024**.

> [!IMPORTANT]
> *Notacja podwójnego dwukropka wskazuje, że wystąpiły bity są równe zero. **FF02:: 1: FF00:0/104** w pełni rozwinięte wygląda jak* **FF02:0000:** 0000:0000:0000:0,001: FF00:0000

### <a name="global-addresses"></a>Adresy globalne    
Przykładem globalnego adresu IPv6 jest **2001:0123:4567:89AB: CDEF:: 1** NetX Duo przechowuje adresy IPv6 w strukturze NXD_ADDRESS. W poniższym przykładzie zmienna NXD_ADDRESS **global_ipv6_address** zawiera adres IPv6 emisji pojedynczej. Poniższy przykład przedstawia urządzenie NetX Duo, które tworzy określony adres globalny IPv6 dla swojego urządzenia podstawowego:

```c
NXD_ADDRESS global_ipv6_address;
UINT        primary_interface_index = 0;

global_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
global_ipv6_address.nxd_ip_address.v6[0] = 0x20010123;
global_ipv6_address.nxd_ip_address.v6[1] = 0x456789AB;
global_ipv6_address.nxd_ip_address.v6[2] = 0xCDEF0000;
global_ipv6_address.nxd_ip_address.v6[3] = 0x00000001;

status = nxd_ipv6_address_set(
            &ip_0,
            primary_interface_index,
            &global_ipv6_address,
            64,
            NX_NULL);
```
Należy pamiętać, że prefiks tego adresu IPv6 to **2001:0123:4567:89AB**, który jest 64 bitów Long i jest wspólną długością prefiksu dla globalnych adresów IPv6 emisji pojedynczej w sieci Ethernet.

Struktura NXD_ADDRESS również zawiera adresy IPv4. Adres IP **192.1.168.10** (**0xC001A80A**) przechowywany w global_ipv4_address będzie miał następujący układ pamięci:

|Pole |Wartość |
|---|---|
|global_ipv4_address global_ipv4_address.nxd_ip_version |NX_IP_VERSION_V4|
|global_ipv4_address global_ipv4_address.nxd_ip_address. v4 |0xC001A80A|

Gdy aplikacja przekazuje adres do usług NetX Duo, w polu *nxd_ip_version* należy określić prawidłową wersję protokołu IP, aby zapewnić obsługę odpowiednich pakietów.

Aby była zgodna z poprzednimi wersjami istniejących aplikacji NetX, NetX Duo obsługuje wszystkie usługi NetX. Wewnętrznie NetX Duo konwertuje typ adresu IPv4 ULONG na typ danych NXD_ADDRESS przed przekazaniem go do rzeczywistej usługi NetX Duo.

Poniższy przykład ilustruje podobieństwo i różnice między usługami w NetX i NetX Duo.

```c
/* Make a connection to the destination IPv4 address
   192.1.168.12 through an already created TCP socket bound
   to the well known HTTP port number 80. */

global_ipv4_address.nxd_ip_version = NX_IP_VERSION_V4;
global_ipv4_address.nxd_ip_address.v4 = 0xC001A80C;

nxd_tcp_client_socket_connect(&tcp_socket,
                              &global_ipv4_address,
                              port_number,
                              NX_WAIT_FOREVER);
```

Poniżej przedstawiono odpowiedni interfejs API NetX:

```c
ULONG         server_ip = 0xC001A80C;
NX_TCP_SOCKET tcp_socket;
UINT          port_number = 80;

nx_tcp_client_socket_connect(&tcp_socket,
                             server_ip,
                             port_number,
                             NX_WAIT_FOREVER); 
```

> [!IMPORTANT]
> *Deweloperzy aplikacji zachęcają do korzystania z wersji NXD tych interfejsów API*.

### <a name="ipv6-default-routers"></a>Routery domyślne IPv6    
Protokół IPv6 używa domyślnego routera do przekazywania pakietów do miejsc docelowych offlink. ***Nxd_ipv6_default_router_add*** usługa NetX Duo umożliwia aplikacji dodanie routera IPv6 do tabeli routera domyślnego. Zobacz rozdział 4 "Opis usług", aby uzyskać więcej domyślnych usług routera oferowanych przez NetX Duo.  

W przypadku przekazywania pakietów IPv6 NetX Duo najpierw sprawdza, czy w miejscu docelowym pakietu znajduje się link. Jeśli nie, NetX Duo sprawdza domyślną tabelę routingu dla prawidłowego routera do przesyłania dalej do usługi.  

Aby usunąć router z tabeli routera domyślnego IPv6, aplikacja używa usługi ***nxd_ipv6_default_router_delete** _. Aby uzyskać wpisy domyślnej tabeli routera IPv6, należy użyć usługi _ *_nxd_ipv6_default_router_entry_get_* *.

### <a name="ipv6-header"></a>Nagłówek IPv6    
Nagłówek IPv6 został zmodyfikowany z nagłówka IPv4. Podczas alokowania pakietu obiekt wywołujący określa protokół aplikacji (np. UDP, TCP), rozmiar buforu w bajtach i limit przeskoków.   

Rysunek 9 przedstawia format nagłówka IPv6 i tabelę wyświetla listę składników nagłówka.

![Diagram formatu nagłówka IPv6.](./media/user-guide/image18.png)

**RYSUNEK 9. Format nagłówka IPv6**

|Nagłówek IP | Przeznaczenie |
|---|---|
|Wersja |pole 4-bitowe dla wersji IP. W przypadku sieci IPv6 wartość w tym polu musi wynosić 6; W przypadku sieci IPv4 musi być 4.|
|Klasa ruchu |pole 8-bitowe przechowujące informacje o klasie ruchu. To pole nie jest używane przez NetX Duo.|
|Etykieta przepływu |pole 20-bitowe do unikatowego identyfikowania przepływu, z którym jest skojarzony pakiet. Wartość zerowa wskazuje, że pakiet nie należy do określonego przepływu. To pole zastępuje pole *OT* w protokole IPv4.|
|Długość ładunku |pole 16-bitowe wskazujące ilość danych w bajtach pakietu IPv6 po nagłówku podstawowym IPv6. Obejmuje to wszystkie hermetyzowane nagłówki protokołu i dane.|
|Następny nagłówek | pole 8-bitowe wskazujące typ nagłówka rozszerzenia, który następuje po nagłówku bazowym IPv6. To pole zastępuje pole *Protokół* w protokole IPv4.|
|Limit przeskoków |pole 8-bitowe ograniczające liczbę routerów, przez które może przejść pakiet. To pole zastępuje pole *czasu wygaśnięcia* w protokole IPv4.|
|Adres źródłowy |128 — pole bitowe, które przechowuje adres IPv6 nadawcy.|
|Adres docelowy |128-bitowe pole, które Sores adres IPv6 miejsca docelowego.|

### <a name="enabling-ipv6-in-netx-duo"></a>Włączanie protokołu IPv6 w NetX Duo    
Domyślnie protokół IPv6 jest włączony w NetX Duo. Usługi IPv6 są włączone w NetX Duo, jeśli konfigurowalna opcja ***NX_DISABLE_IPV6** _ w _nx_user. h * nie została zdefiniowana. Jeśli ***NX_DISABLE_IPV6*** jest zdefiniowany, NetX Duo będzie oferować tylko usługi IPv4, a wszystkie moduły i usługi związane z protokołem IPv6 nie są wbudowane w bibliotekę NetX Duo.

Następująca usługa jest świadczona dla aplikacji w celu skonfigurowania adresu IPv6 urządzenia: ***nxd_ipv6_address_set***

Oprócz ręcznego ustawiania adresów IPv6 urządzenia, system może również korzystać z automatycznej konfiguracji adresów bezstanowych. Aby można było użyć tej opcji, aplikacja musi wywoływać ***nxd_ipv6_enable** _, aby uruchomić usługi IPv6 na urządzeniu. Ponadto usługi ICMPv6 muszą zostać uruchomione przez wywołanie _*_nxd_icmp_enable_*_, co umożliwia NetX Duo wykonywanie usług takich jak żądanie routera, odnajdowanie sąsiadów i wykrywanie duplikatów adresów. Należy pamiętać, że _*_nx_icmp_enable_*_ uruchamia tylko protokół ICMP dla usług IPv4. _*_nxd_icmp_enable_*_ uruchamia usługi ICMP dla protokołów IPv4 i IPv6. Jeśli system nie potrzebuje usług ICMPv6, można użyć _ *_nx_icmp_enable_**, aby moduł ICMPv6 nie był połączony z systemem.

W poniższym przykładzie przedstawiono typową procedurę inicjowania protokołu IPv6 NetX Duo.

```c
/* Assume ip_0 has been created and IPv4 services (such as ARP,
   ICMP, have been enabled. */
#define SECONDARY_INTERFACE 1

/* Enable IPv6 */
status = nxd_ipv6_enable(&ip_0);

if(status != NX_SUCCESS)
{
    /* nxd_ipv6_enable failed. */
}

/* Enable ICMPv6 */
status = nxd_icmp_enable(&ip_0);
if(status != NX_SUCCESS)
{
    /* nxd_icmp_enable failed. */
}

/* Configure the link local address on the primary interface. */
status = nxd_ipv6_address_set(&ip_0, 0, NX_NULL, 10, NX_NULL);

/* Configure ip_0 primary interface global address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6
ip_address.nxd_ip_address.v6[0] = 0x20010db8;
ip_address.nxd_ip_address.v6[1] = 0x0000f101;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 0x202;

/* Configure global address of the primary interface. */
status = nxd_ipv6_address_set(&ip_0, SECONDARY_INTERFACE,
                              &ip_address, 64, NX_NULL);
```                              

Protokoły warstwy wyższej (takie jak TCP i UDP) można włączyć przed uruchomieniem protokołu IPv6 lub po nim.

> [!IMPORTANT]  
> *Usługi IPv6 są dostępne tylko po zainicjowaniu wątku IP i włączeniu urządzenia.*

Po włączeniu interfejsu (tj. sterownik urządzenia interfejsu jest gotowy do wysyłania i odbierania danych, a uzyskano prawidłowy adres lokalny linku), urządzenie może uzyskać globalne adresy IPv6 przy użyciu jednej z następujących metod:

- Bezstanowa Konfiguracja automatycznej konfiguracji;  
- Ręczna konfiguracja adresów IPv6;  
- Konfiguracja adresu za pośrednictwem protokołu DHCPv6 (z opcjonalnym pakietem DHCPv6)

Dwie pierwsze metody są opisane poniżej. Metoda trzecia (DHCPv6) jest opisana w pakiecie DHCP.

### <a name="stateless-address-autoconfiguration-using-router-solicitation"></a>Autokonfiguracja adresu bezstanowego przy użyciu żądania routera      
Urządzenia NetX Duo mogą automatycznie konfigurować ich interfejsy w przypadku połączenia z siecią IPv6 przy użyciu routera dostarczającego informacje o prefiksie. Urządzenia, które wymagają bezstanowej automatycznej konfiguracji wysyłania komunikatów żądań routera (RS). Routery w sieci odpowiadają za pomocą komunikatów na żądanie anonsowania routera (RA). Komunikaty RA anonsują prefiksy, które identyfikują adresy sieciowe skojarzone z linkiem. Następnie urządzenia generują unikatowy identyfikator sieci, do której jest dołączone urządzenie. Adres jest tworzony przez połączenie prefiksu i jego unikatowego identyfikatora. W ten sposób w przypadku otrzymywania wiadomości urzędu rejestrowania hosty generują adresy IP. Routery mogą również wysyłać okresowe niechciane komunikaty urzędu rejestrowania. 

> [!WARNING]
> *NetX Duo umożliwia aplikacji włączenie lub wyłączenie automatycznej konfiguracji adresu bezstanowego w czasie wykonywania. Aby włączyć tę funkcję, biblioteka NetX Duo musi być skompilowana ze zdefiniowanym **NX_IPV6_STATELESS_AUTOCONFIG_CONTROL** . Po włączeniu tej funkcji aplikacje mogą używać **nxd_ipv6_stateless_address_autoconfigure_enable** i **nxd_ipv6_stateless_address_autocofigure_disable** do włączania lub wyłączania automatycznej konfiguracji adresów IPv6*.

### <a name="manual-ipv6-address-configuration"></a>Ręczna konfiguracja adresu IPv6     
Jeśli wymagany jest konkretny adres IPv6, aplikacja może używać ***nxd_ipv6_address_set*** do ręcznego konfigurowania adresu IPv6. Interfejs sieciowy może mieć wiele adresów IPv6. Należy jednak pamiętać, że łączna liczba adresów IPv6 w systemie uzyskanych za pomocą automatycznej konfiguracji adresów bezstanowych lub przez konfigurację ręczną nie może przekroczyć ***NX_MAX_IPV6_ADDRESSES***.

Poniższy przykład ilustruje sposób ręcznego konfigurowania adresu globalnego w podstawowym interfejsie (urządzenie 0) w ip_0:

```c
NXD_ADDRESS global_address;
global_address.nxd_ip_version = NX_IP_VERSION_V6;
global_address.nxd_ip_address.v6[0] = 0x20010000;
global_address.nxd_ip_address.v6[1] = 0x00000000;
global_address.nxd_ip_address.v6[2] = 0x00000000;
global_address.nxd_ip_address.v6[3] = 0x0000ABCD;
```

Następnie Host wywoła następującą usługę NetX Duo, aby przypisać ten adres jako globalny adres IP:

```c
status = nxd_ipv6_address_set(&ip_0, 0,  
                              &global_address, 64
                              NX_NULL);
```

### <a name="duplicate-address-detection-dad"></a>Wykrywanie zduplikowanych adresów (tata)    
Gdy system skonfiguruje swój adres IPv6, adres zostanie oznaczony jako *niepewny*. W przypadku wykrycia zduplikowanego adresu (DAD), opisanego w dokumencie RFC 4862, NetX Duo automatycznie wysyła komunikaty żądania sąsiada (NS) przy użyciu tego nieakceptowanego adresu jako miejsca docelowego. Jeśli żadne hosty w sieci nie odpowiadają na te komunikaty NS w danym okresie, zakłada się, że adres jest unikatowy w łączu lokalnym, a jego stan jest prawidłowy. W tym momencie aplikacja może zacząć używać tego adresu IP do komunikacji.  

Funkcje DAD są częścią modułu ICMPv6. W związku z tym aplikacja musi włączyć usługi ICMPv6, zanim nowo skonfigurowany adres będzie mógł przejść przez proces DAD. Alternatywnie, proces DAD może być wyłączony przez zdefiniowanie opcji ***NX_DISABLE_IPV6_DAD** _ w środowisku kompilacji biblioteki NetX Duo (zdefiniowanej jako _*_nx_user. h_*_). Podczas procesu DAD parametr _*_NX_IPV6_DAD_TRANSMITS_*_ określa liczbę komunikatów NS wysłanych przez NetX Duo bez otrzymywania odpowiedzi w celu ustalenia, czy adres jest unikatowy. Domyślnie i zalecane przez RFC 4862, _ *_NX_IPV6_DAD_TRANSMITS_** jest ustawiony na 3. Ustawienie tego symbolu na zero powoduje wyłączenie DAD.

Jeśli protokół ICMPv6 lub tata nie jest włączony w momencie, gdy aplikacja przypisze adres IPv6, tato nie zostanie wykonana i NetX Duo ustawi natychmiastowy stan adresu IPv6.

NetX Duo nie może komunikować się w sieci IPv6, dopóki adres lokalny i/lub globalny linku nie są prawidłowe. Po uzyskaniu prawidłowego adresu NetX Duo próbuje dopasować adres docelowy pakietu przychodzącego do jednego ze skonfigurowanych adresów IPv6 lub z włączonym adresem multiemisji. Jeśli nie zostaną znalezione żadne dopasowania, pakiet zostanie porzucony. 

> [!WARNING]  
> * W trakcie procesu DAD liczba pakietów DAD NS do przesłania jest definiowana przez ***NX_IPV6_DAD_TRANSMITS**_, która domyślnie jest równa 3, a w przypadku gdy wysyłana jest jedna sekunda opóźnienia między każdą zawartą w niej wiadomości NS. W związku z tym w systemie z włączonym tata, po przypisaniu adresu IPv6 (przy założeniu, że nie jest to zduplikowany adres), istnieje około 3 sekund opóźnienia, zanim adres IP będzie w PRAWIDŁOWYm stanie i jest gotowy do komunikacji._

Aplikacje mogą chcieć otrzymywać powiadomienia o zmianie adresów IPv6 w systemie. Aby włączyć funkcję powiadamiania o zmianie adresu IPv6, biblioteka NetX Duo musi być skompilowana przy użyciu zdefiniowanego symbolu **NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** . Po włączeniu tej funkcji aplikacje mogą instalować funkcję wywołania zwrotnego za pomocą usługi **_nxd_ipv6_address_change_notify_** .

Gdy adres IPv6 zostanie zmieniony lub przestanie być nieprawidłowy, funkcja wywołania zwrotnego wprowadzona przez użytkownika zostanie wywołana z następującymi informacjami:

| Funkcja  | Opis  |
|---|---|
|ip_ptr |Wskaźnik do wystąpienia adresu IP|
|interface_index |Indeksuj do interfejsu sieciowego, z którym jest skojarzony ten adres IPv6
|ipv6_addr_index |Indeksowanie tabeli adresów IPv6|
|ipv6_address |Wskaźnik na adres IPv6 w postaci tablicy czterech ULONG liczb całkowitych. Adresy Pv6 są prezentowane w kolejności bajtów hosta.|

### <a name="ipv6-multicast-support-in-netx-duo"></a>Obsługa multiemisji IPv6 w programie NetX Duo      
Adresy multiemisji określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączać się i zostawiać w dowolnym momencie. NetX Duo implementuje kilka protokołów ICMPv6, w tym wykrywanie zduplikowanych adresów, odnajdywanie sąsiadów i odnajdywanie routerów, które wymagają możliwości multiemisji IP. W związku z tym NetX Duo oczekuje, że podstawowy sterownik urządzenia obsługuje operacje multiemisji.

Gdy NetX Duo musi przyłączyć się do grupy multiemisji lub opuścić ją (na przykład adres multiemisji z całego węzła i adres multiemisji na *żądanie* ), wysyła polecenie sterownika do sterownika urządzenia, aby dołączyć lub pozostawić adres MAC multiemisji. Polecenie sterownika służące do przyłączania adresu multiemisji to ***NX_LINK_MULTICAST_JOIN** _. Aby opuścić adres multiemisji, NetX Duo wystawia polecenie sterownika _ *_NX_LINK_MULTICAST_LEAVE_* *. Aby protokoły ICMPv6 działały prawidłowo, sterownik urządzenia musi zaimplementować te dwa polecenia.

Aplikacje mogą dołączać do grupy multiemisji IPv6 za pomocą usługi ***nxd_ipv6_multicast_interface_join *.** Ta usługa rejestruje adres multiemisji przy użyciu stosu IP, a następnie powiadamia określony sterownik urządzenia w adresie multiemisji IPv6. Aby opuścić grupę multiemisji, aplikacje używają ***nxd_ipv6_multicast_interface_leave usługi.***

### <a name="neighbor-discovery-nd"></a>Odnajdywanie sąsiadów (ND)    
Funkcja odnajdywania sąsiadów to protokół w sieciach IPv6 służący do mapowania adresów fizycznych na adresy IPv6 (adres globalny lub adres lokalny łącza). To mapowanie jest zachowywane w pamięci podręcznej odnajdowania sąsiadów (w pamięci podręcznej ND). Proces ND jest odpowiednikiem procesu ARP w protokole IPv4, a pamięć podręczna ND jest podobna do tabeli ARP. Węzeł IPv6 może uzyskać adres MAC swojego sąsiada przy użyciu protokołu Neighbor Discovery (ND). Wysyła komunikat żądania sąsiada (NS) do adresu multiemisji węzła żądanego przez węzeł i czeka na odpowiedni komunikat anonsu sąsiada (NA). Adres MAC uzyskany za pomocą tego procesu jest przechowywany w pamięci podręcznej ND.

Każde wystąpienie IP ma jedną pamięć podręczną ND. Pamięć podręczna ND jest utrzymywana jako tablica wpisów. Rozmiar tablicy jest definiowany w czasie kompilacji przez ustawienie opcji ***NX_IPV6_NEIGHBOR_CACHE_SIZE** _, w _ *_nx_user. h_* *. Należy zauważyć, że wszystkie interfejsy dołączone do wystąpienia IP korzystają z tej samej pamięci podręcznej ND.

Cała pamięć podręczna ND jest pusta, gdy zostanie uruchomione NetX Duo. Gdy system zostanie uruchomiony, NetX Duo automatycznie aktualizuje pamięć podręczną ND, dodając i usuwając wpisy zgodnie z protokołem ND. Jednak aplikacja może również zaktualizować pamięć podręczną ND, ręcznie dodając i usuwając wpisy pamięci podręcznej przy użyciu następujących usług NetX Duo:

- ***nxd_nd_cache_entry_delete***  
- ***nxd_nd_cache_entry_set***   
- ***nxd_nd_cache_invalidate***

W przypadku wysyłania i otrzymywania pakietów IPv6 NetX Duo automatycznie aktualizuje tabelę pamięci podręcznej ND.

## <a name="internet-control-message-protocol-in-ipv6-icmpv6"></a>Protokół komunikatów kontroli Internetu w protokole IPv6 (ICMPv6)  

Rola ICMPv6 w protokole IPv6 została znacznie rozszerzona w celu obsługi mapowania adresów IPv6 i odnajdywania routera. Dodatkowo NetX Duo ICMPv6 obsługuje żądanie echa i odpowiedzi, raporty błędów ICMPv6 i komunikaty ICMPv6 redirect.

### <a name="icmpv6-enable"></a>Włączenie ICMPv6    
Aby komunikaty ICMPv6 mogły być przetwarzane przez NetX Duo, aplikacja musi wywoływać usługę ***nxd_icmp_enable*** , aby umożliwić przetwarzanie ICMPv6 w sposób opisany wcześniej. 

### <a name="icmpv6-messages"></a>Komunikaty ICMPv6     
Struktura nagłówka ICMPv6 jest podobna do struktury nagłówka ICMPv4. Jak pokazano poniżej, podstawowy nagłówek ICMPv6 zawiera trzy pola, typ, kod i sumę kontrolną, a także zmienną długość danych opcji ICMPv6. 

![Diagram podstawowego nagłówka ICMPv6.](./media/user-guide/image19.png)

**RYSUNEK 10. Podstawowy nagłówek ICMPv6**

|Pole |Rozmiar (w bajtach) |Opis |
|-----|-----|-----|
|     | 1   |Identyfikuje typ komunikatu ICMPv6; |
|     |     |1 miejsce docelowe jest nieosiągalne |
|     |     |Zbyt duży pakiet 2 |
|     |     |3 przekroczenia czasu |
|     |     |4 problem z parametrem |
|     |     |128 żądanie echa |
|     |     |129 odpowiedzi echa |
|     |     |Żądanie routera 133 |
|     |     |Anons routera 134 |
|     |     |135 żądanie sąsiada |
|     |     |136 anons sąsiada |
|     |     |137 komunikat przekierowania |
|Kod | 1   |Umożliwia dalsze zakwalifikowanie typu komunikatu ICMPv6. Zwykle używany z komunikatami o błędach. Jeśli nie zostanie użyta, jest ustawiona na zero. Komunikaty żądania echa/odpowiedzi i NS nie są używane.|
|Suma kontrolna | 2 |16-bitowe pole sumy kontrolnej dla nagłówka ICMP. Jest to 16-bitowy uzupełniający cały komunikat ICMPv6, w tym nagłówek ICMPv6. Zawiera również pseudo nagłówka adresu źródłowego IPv6, adresu docelowego i długości ładunku pakietu. |

Poniżej przedstawiono przykładowy nagłówek żądania sąsiada.

![Diagram przykładowego nagłówka żądania sąsiada.](./media/user-guide/image20.jpg)

**RYSUNEK 11. Nagłówek ICMPv6 dla komunikatu żądania sąsiada**

|Pole |Rozmiar (w bajtach) |Opis |
|-----|-----|-----|
|Typ | 1   |Identyfikuje typ komunikatu ICMPv6 dla komunikatów żądania sąsiada. Wartość to 135. |
|Kod | 1   |Nie używany. Ustaw wartość 0. |
|Suma kontrolna | 2  |16-bitowe pole sumy kontrolnej dla nagłówka ICMPv6. |
|Zarezerwowany | 4  |4 zarezerwowane bajty ustawione na 0. |
|Adres docelowy | 16  |Adres IPv6 obiektu docelowego żądania. W przypadku rozpoznawania adresów IPv6 jest to rzeczywisty adres IP emisji pojedynczej urządzenia, którego adres warstwy łącza musi zostać rozpoznany. |
|Opcje | Zmienna |Opcjonalne informacje określone przez protokół Neighbor Discovery Protocol. |

### <a name="icmpv6-ping-request"></a>Żądanie ping ICMPv6
W aplikacjach NetX Duo Użyj ***nxd_icmp_ping*** , aby wystawić żądania ping IPv6 lub IPv4 na podstawie docelowego adresu IP określonego w parametrach.  

### <a name="icmpv6-ping-response"></a>Odpowiedź ping protokołu ICMPv6
Odpowiedź na polecenie ping protokołu ICMPv6 jest innym typem komunikatu ICMPv6, który jest generowany wewnętrznie przez składnik ICMPv6 w odpowiedzi na zewnętrzne żądanie ping ICMPv6. Aby uzyskać dodatkowe potwierdzenie, odpowiedź na polecenie ping protokołu ICMPv6 również zawiera kopię danych użytkownika dostarczonych w żądaniu ping ICMPv6.  

### <a name="thread-suspension"></a>Zawieszenie wątku
Wątki aplikacji mogą wstrzymywać podczas próby wysłania polecenia ping do innego elementu członkowskiego sieci. Po odebraniu odpowiedzi ping komunikat odpowiedzi ping jest przyznany do pierwszego wątku zawieszonego i ten wątek zostaje wznowiony. Podobnie jak w przypadku wszystkich usług NetX Duo, zawieszenie żądania ping ma opcjonalny limit czasu.  

### <a name="other-icmpv6-messages"></a>Inne komunikaty ICMPv6
Komunikaty ICMPv6 są wymagane dla następujących funkcji:  

- Odnajdywanie sąsiadów  
- Autokonfiguracja adresu bezstanowego 
- Odnajdywanie routera 
- Wykrywanie nieosiągalności sąsiadów  

### <a name="neighbor-unreachability-router-and-prefix-discovery"></a>Nieosiągalność sąsiada, Wykrywanie routera i prefiksów    
Wykrywanie nieosiągalności sąsiadów, odnajdywanie routera i odnajdowanie prefiksów opiera się na protokole Neighbor Discovery i opisano poniżej. 

***Wykrywanie nieosiągalności sąsiada:*** Urządzenie IPv6 przeszukuje pamięć podręczną odnajdowania sąsiadów (ND) dla adresu warstwy łącza docelowego, gdy chce wysłać pakiet. Bezpośrednie miejsce docelowe, nazywane czasem "następnym przeskokiem", może być rzeczywistym miejscem docelowym tego samego linku lub może być routerem, jeśli miejsce docelowe jest wyłączone. Wpis pamięci podręcznej ND zawiera stan dla możliwości uzyskania dostępu.

Stan OSIĄGALNy oznacza, że sąsiad jest uznawany za osiągalny. Sąsiad jest osiągalny, jeśli niedawno otrzymał potwierdzenie, że pakiety wysłane do sąsiada zostały odebrane. Potwierdzenie w NetX Duo przyjmuje formę odebrania komunikatu NA brak z sąsiada w odpowiedzi na komunikat NS Wysłany przez urządzenie NetX Duo. NetX Duo zmieni stan sąsiada na dostępny, jeśli aplikacja wywoła usługę NetX Duo ***nxd_nd_cache_entry_set*** ręcznie wprowadzić rekord pamięci podręcznej.

***Odnajdywanie routera:*** Urządzenie IPv6 używa routera do przesyłania dalej wszystkich pakietów przeznaczonych do łączenia miejsc docelowych. Mogą również używać informacji wysyłanych przez router, takich jak komunikaty Anons routera (RA), w celu skonfigurowania globalnych adresów IPv6.

Urządzenie w sieci może inicjować proces odnajdywania routera, wysyłając komunikat żądania routera (RS) do adresu multiemisji wszystkich routerów (FF01:: 2). Może też oczekiwać na adres multiemisji wszystkich węzłów (FF:: 1) dla okresowego urzędu rejestrowania z routerów.

Komunikat urzędu rejestrowania zawiera informacje o prefiksie służące do konfigurowania adresu IPv6 dla tej sieci. W NetX Duo żądanie routera jest domyślnie włączone i można je wyłączyć przez ustawienie opcji konfiguracji ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ w _ *_nx_user. h_* *. Aby uzyskać więcej informacji na temat ustawiania parametrów żądania routera, zobacz Opcje konfiguracji w rozdziale "Instalacja i użycie programu NetX Duo". 

***Odnajdywanie prefiksu***: urządzenie IPv6 używa odnajdywania prefiksów, aby dowiedzieć się, które hosty docelowe są dostępne bezpośrednio bez przechodzenia przez router. Te informacje są udostępniane urządzeniu IPv6 z komunikatów urzędu rejestrowania z routera. Urządzenie IPv6 zapisuje informacje o prefiksach w tabeli prefiksów. Funkcja odnajdywania prefiksów dopasowuje prefiks z tabeli prefiksów urządzeń IPv6 do adresu docelowego. Prefiks jest zgodny z adresem docelowym, jeśli wszystkie bity w prefiksie pasują do najbardziej znaczących bitów adresu docelowego. Jeśli więcej niż jeden prefiks obejmuje adres, wybierany jest najdłuższy prefiks.

### <a name="icmpv6-error-messages"></a>Komunikaty o błędach ICMPv6    
W NetX Duo są obsługiwane następujące komunikaty o błędach ICMPv6:  

- Miejsce docelowe jest nieosiągalne  
- Zbyt duży pakiet  
- Czas przekroczenia  
- Problem z parametrem  

## <a name="user-datagram-protocol-udp"></a>User Datagram Protocol (UDP)

Protokół UDP (User Datagram Protocol) zapewnia najprostszą formę transferu danych między elementami członkowskimi sieci (RFC 768). Pakiety danych UDP są wysyłane z jednego członka sieci do innego w najlepszym wysiłku. oznacza to, że nie ma wbudowanego mechanizmu potwierdzania przez odbiorcę pakietu. Ponadto wysyłanie pakietu UDP nie wymaga wcześniejszego nawiązania połączenia. Z tego powodu transmisja pakietów UDP jest bardzo wydajna.

Deweloperzy migrujeli aplikacje NetX do NetX Duo istnieją tylko pewne podstawowe zmiany w funkcji UDP między NetX i NetX Duo. Wynika to z tego, że protokół IPv6 jest przede wszystkim objęty podstawową warstwą IP. Wszystkie usługi UDP NetX Duo mogą być używane na potrzeby łączności IPv4 lub IPv6.

### <a name="udp-header"></a>Nagłówek UDP       
Protokół UDP umieszcza prosty nagłówek pakietu przed danymi aplikacji podczas transmisji i usuwa podobny nagłówek UDP z pakietu przy odbiorze przed dostarczeniem odebranego pakietu UDP do aplikacji. Protokół UDP korzysta z protokołu IP do wysyłania i otrzymywania pakietów, co oznacza, że na początku nagłówka UDP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 12 przedstawia format nagłówka UDP.

![Diagram formatu nagłówka UDP.](./media/user-guide/image21.png)

### <a name="figure-12-udp-header"></a>RYSUNEK 12. Nagłówek UDP

> [!NOTE]
> *Oczekuje się, że wszystkie nagłówki w implementacji protokołu UDP/IP mają być w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

Poniżej opisano format nagłówka UDP:

|Pole nagłówka |Przeznaczenie |
|---|---|
|**16-bitowy numer portu źródłowego** |To pole zawiera port, z którego jest wysyłany pakiet UDP. Prawidłowe porty UDP mieszczą się w zakresie od 1 do 0xFFFF. |
|**16-bitowy numer portu docelowego** |To pole zawiera port UDP, do którego jest wysyłany pakiet. Prawidłowe porty UDP mieszczą się w zakresie od 1 do 0xFFFF. |
|**16-bitowa długość protokołu UDP** |To pole zawiera liczbę bajtów w pakiecie UDP, w tym rozmiar nagłówka UDP. |
|**16-bitowa suma kontrolna UDP** |To pole zawiera 16-bitową sumę kontrolną pakietu, w tym nagłówek UDP, obszar danych pakietu i nagłówek pseudo IP. |

### <a name="udp-enable"></a>Włączanie protokołu UDP   
Przed przekazaniem pakietów UDP aplikacja musi najpierw włączyć protokół UDP, wywołując usługę ***nx_udp_enable*** . Po włączeniu aplikacja jest bezpłatna do wysyłania i odbierania pakietów UDP.  

### <a name="udp-socket-create"></a>Tworzenie gniazda UDP    
Gniazda UDP są tworzone podczas inicjowania lub podczas wykonywania przez wątki aplikacji. Początkowy typ usługi, czas wygaśnięcia i głębokość kolejki odbierania są zdefiniowane przez usługę ***nx_udp_socket_create*** . Liczba gniazd UDP w aplikacji nie jest ograniczona.

### <a name="udp-checksum"></a>Suma kontrolna UDP   
Protokół IPv6 wymaga obliczeń sum kontrolnych nagłówka UDP w danych pakietu, natomiast w protokole IPv4, który jest opcjonalny.  

Protokół UDP określa 16-bitową sumę kontrolną, która pokrywa się z pseudo nagłówka adresu IP (składa się ze źródłowego adresu IP, docelowego adresu IP oraz słowa protokołu IP o długości), nagłówka UDP i danych pakietów UDP. Jedyne różnice sum kontrolnych nagłówka pakietów UDP IPv4 i IPv6 polega na tym, że źródłowe i docelowe adresy IP są 32 bitowe w protokole IPv4, a w protokole IPv6 mają 128 bit. Jeśli obliczona suma kontrolna UDP to 0, jest ona przechowywana jako wszystkie (0xFFFF). Jeśli gniazdo wysyłania ma wyłączoną logikę sumy kontrolnej UDP, wartość zero jest umieszczana w polu sumy kontrolnej UDP, aby wskazać, że suma kontrolna nie została obliczona.

Jeśli suma kontrolna UDP nie jest zgodna z obliczoną sumą kontrolną przez odbiorcę, pakiet UDP jest po prostu odrzucony.

W sieci IPv4 suma kontrolna UDP jest opcjonalna. NetX Duo umożliwia aplikacji Włączanie lub wyłączanie obliczeń sum kontrolnych UDP na podstawie gniazda. Domyślnie logika sumy kontrolnej gniazda UDP jest włączona. Aplikacja może wyłączyć logikę sumy kontrolnej dla określonego gniazda UDP, wywołując usługę ***nx_udp_socket_checksum_disable** _. W sieci IPv6 jednak suma kontrolna UDP jest obowiązkowa. W związku z tym usługa _ *_nx_udp_socket_checksum_disable_** nie wyłączy logiki sum kontrolnych UDP podczas wysyłania pakietu za pomocą sieci IPv6.

Niektóre kontrolery Ethernet mogą generować sumę kontrolną UDP na bieżąco. Jeśli system może korzystać z funkcji obliczeń sum kontrolnych sprzętowych, biblioteka NetX Duo może być skompilowana bez logiki sumy kontrolnej. Aby wyłączyć sumę kontrolną oprogramowania UDP, biblioteka NetX Duo musi być skompilowana z następującymi zdefiniowanymi symbolami: ***NX_DISABLE_UDP_TX_CHECKSUM** _ i _*_NX_DISABLE_UDP_RX_CHECKSUM_*_ (opisane w rozdziale dwa). Opcje konfiguracji usuwają logikę sum kontrolnych UDP z NetX Duo całkowicie, podczas gdy wywołanie _ *_nx_udp_socket_checksum_disable_** pozwala aplikacji wyłączyć przetwarzanie sum kontrolnych UDP protokołu IPv4 dla każdego gniazda.

### <a name="udp-ports-and-binding"></a>Porty i powiązania UDP      
Port UDP jest logicznym punktem końcowym protokołu UDP. W składniku UDP programu NetX Duo istnieją 65 535 prawidłowe porty z zakresu od 1 do 0xFFFF. Aby wysłać lub odebrać dane UDP, aplikacja musi najpierw utworzyć gniazdo UDP, a następnie powiązać ją z żądanym portem. Po powiązaniu gniazda UDP z portem aplikacja może wysyłać i odbierać dane w tym gnieździe.

### <a name="udp-fast-pathtrade"></a>Szybka ścieżka UDP&trade;   
Szybka ścieżka UDP &trade; to nazwa małej ścieżki narzutu na pakiety przez implementację protokołu UDP NetX Duo. Wysyłanie pakietu UDP wymaga tylko kilku wywołań funkcji: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_ i ostatecznego wywołania sterownika sieci. _*_nx_udp_socket_send_*_ jest dostępny w NetX Duo dla istniejących aplikacji NetX i ma zastosowanie tylko w przypadku pakietów IPv4. Preferowaną metodą jest jednak użycie _ *_nxd_udp_socket_send_** usługi omówionej poniżej. W przypadku odbierania pakietów UDP pakiet UDP jest umieszczany w odpowiedniej kolejce odbioru gniazda UDP lub dostarczany do zawieszonego wątku aplikacji w ramach pojedynczego wywołania funkcji z przetwarzania przerwań odbieranych przez sterownik sieciowy. Ta wysoce zoptymalizowana logika do wysyłania i otrzymywania pakietów UDP jest istotą technologii szybkiego ścieżki UDP.  

### <a name="udp-packet-send"></a>Wysyłanie pakietów UDP    
Wysyłanie danych UDP za pośrednictwem protokołu IPv6 lub sieci IPv4 jest łatwo realizowane przez wywołanie funkcji ***nxd_udp_socket_send** _. Obiekt wywołujący musi ustawić wersję protokołu IP w polu _nx_ip_version * parametru wskaźnika NXD_ADDRESS. NetX Duo określi najlepszy adres źródłowy przesyłanych pakietów UDP na podstawie docelowego adresu IPv4/IPv6. Ta usługa umieszcza nagłówek UDP przed danymi pakietu i wysyła je do sieci przy użyciu procedury wysyłania wewnętrznego adresu IP. Nie ma zawieszania wątku podczas wysyłania pakietów UDP, ponieważ wszystkie transporty pakietów UDP są przetwarzane natychmiast. 

W przypadku docelowych multiemisji lub emisji aplikacja powinna określić źródłowy adres IP, który ma być używany, jeśli urządzenie NetX Duo ma wiele adresów IP do wyboru. Można to zrobić za pomocą usług ***nxd_udp_socket_source_send.***

> [!IMPORTANT]    
> *Jeśli **nx_udp_socket_send** jest używany do przesyłania pakietów multiemisji lub emisji, adres IP pierwszego włączonego interfejsu jest używany jako adres źródłowy*.

> [!NOTE] 
> *Jeśli dla tego gniazda jest włączona logika sumy kontrolnej UDP, operacja sumy kontrolnej jest wykonywana w kontekście wątku wywołującego bez blokowania dostępu do struktur danych protokołu UDP lub IP*. 

> [!WARNING]    
> *Dane ładunku UDP znajdujące się w strukturze NX_PACKET powinny znajdować się na granicy długiego wyrazu. Aplikacja musi pozostawić wystarczającą ilość miejsca między wskaźnikiem dołączania i wskaźnikiem rozpoczęcia danych dla NetX Duo, aby umieścić nagłówki UDP, IP i nośnika fizycznego*.

### <a name="udp-packet-receive"></a>Odbieranie pakietów UDP    
Wątki aplikacji mogą odbierać pakiety UDP z określonego gniazda przez wywołanie ***nx_udp_socket_receive***. Funkcja odbioru gniazda udostępnia najstarszy pakiet w kolejce odbioru gniazda. Jeśli w kolejce odbierania nie ma pakietów, wątek wywołujący może zawiesić (z opcjonalnym limitem czasu) do momentu otrzymania pakietu.

Przetwarzanie pakietów protokołu UDP odbierane (zwykle wywoływane z procedury obsługi przerwania odbierania przez sterownik sieciowy) jest odpowiedzialne za umieszczenie pakietu w kolejce odbioru gniazda UDP lub dostarczenie go do pierwszego wstrzymanego wątku oczekującego na pakiet. Jeśli pakiet jest umieszczany w kolejce, przetwarzanie odbiera również sprawdza maksymalną głębokość kolejki odbierania skojarzoną z gniazdem. Jeśli ten nowo umieszczony w kolejce pakiet przekracza głębokość kolejki, najstarszy pakiet w kolejce zostanie odrzucony.

### <a name="udp-receive-notify"></a>Powiadomienie o odebraniu protokołu UDP   
Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, należy użyć funkcji ***nx_udp_socket_receive_notify*** . Ta funkcja rejestruje funkcję odbierania pakietów wywołania zwrotnego dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, funkcja wywołania zwrotnego jest wykonywana.

Zawartość funkcji wywołania zwrotnego to applicationspecific; jednak najprawdopodobniej zawiera logikę do informowania wątku przetwarzania, że pakiet jest teraz dostępny w odpowiednim gnieździe.

### <a name="peer-address-and-port"></a>Adres i port elementu równorzędnego   
W przypadku odebrania pakietu UDP aplikacja może znaleźć adres IP i numer portu nadawcy przy użyciu ***nx_udp_packet_info_extract*** usługi. Po pomyślnym powrocie usługa ta udostępnia informacje o adresie IP nadawcy, numerze portu nadawcy i interfejsie lokalnym, za pomocą którego został odebrany pakiet.  

### <a name="thread-suspension"></a>Zawieszenie wątku   
Jak wspomniano wcześniej, wątki aplikacji mogą wstrzymywać się podczas próby odebrania pakietu UDP na określonym porcie UDP. Po odebraniu pakietu na tym porcie jest on przyznany do pierwszego wątku, a następnie wznowiony. Opcjonalny limit czasu jest dostępny w przypadku zawieszania pakietu odbioru protokołu UDP, który jest funkcją dostępną dla większości usług NetX Duo.  

### <a name="udp-socket-statistics-and-errors"></a>Statystyka i błędy gniazda UDP     
Jeśli ta opcja jest włączona, oprogramowanie Socket NetX Duo UDP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/UDP są obsługiwane następujące raporty statystyczne i błędy:

- Całkowita liczba wysłanych pakietów UDP  
- Całkowita liczba wysłanych bajtów UDP  
- Całkowita liczba odebranych pakietów UDP   
- Całkowita liczba odebranych bajtów UDP  
- Całkowita liczba nieprawidłowych pakietów UDP  
- Całkowita liczba porzuconych pakietów odbioru protokołu UDP  
- Łączne błędy sum kontrolnych odbierania UDP  
- Wysłane pakiety gniazd UDP  
- Wysłane bajty gniazda UDP  
- Odebrane pakiety UDP Socket   
- Odebrane bajty gniazda UDP  
- Pakiety gniazd UDP w kolejce  
- Odebrane pakiety UDP w gnieździe  
- Błędy sum kontrolnych gniazda UDP  

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_udp_info_get** _ dla statystyk UDP amassed za pośrednictwem wszystkich gniazd UDP i _ *_nx_udp_socket_info_get_** usługi dla statystyk UDP w określonym gnieździe UDP.

### <a name="udp-socket-control-block-nx_udp_socket"></a>Blok sterowania gniazdem UDP NX_UDP_SOCKET
Cechy poszczególnych gniazd UDP są dostępne w skojarzonym bloku sterowania NX_UDP_SOCKET. Zawiera użyteczne informacje, takie jak link do struktury danych IP, interfejs sieciowy dla ścieżki wysyłania i odbierania, port powiązany i kolejka odbierania pakietów. Ta struktura jest zdefiniowana w pliku ***nx_api. h*** .

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Transmission Control Protocol (TCP) zapewnia niezawodny transfer danych przesyłanych strumieniowo między dwoma członkami sieci (RFC 793). Wszystkie dane wysyłane z jednego członka sieci są weryfikowane i potwierdzane przez element członkowski odbiorcy. Ponadto dwóch członków musi nawiązać połączenie przed jakimkolwiek transferem danych. Wszystkie te wyniki są niezawodnym transferem danych; jednak wymaga to znacznie więcej obciążenia niż poprzednio opisany w tym transfer danych UDP.

Z wyjątkiem sytuacji, w których nie wprowadzono żadnych zmian w usługach interfejsu API protokołu TCP między NetX i NetX Duo, ponieważ protokół IPv6 jest głównie objęty podstawową warstwą IP. Wszystkie usługi TCP NetX Duo mogą być używane dla połączeń IPv4 lub IPv6.

### <a name="tcp-header"></a>Nagłówek TCP   
W przypadku przesyłania nagłówek TCP jest umieszczany przed danymi od użytkownika. Przy odbiorze nagłówek TCP zostaje usunięty z przychodzącego pakietu, pozostawiając tylko te dane użytkownika, które są dostępne dla aplikacji. Protokół TCP korzysta z protokołu IP do wysyłania i odbierania pakietów, co oznacza, że na początku nagłówka TCP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 13 przedstawia format nagłówka TCP.

![Diagram formatu nagłówka TCP.](./media/user-guide/image22.png)

### <a name="figure-13-tcp-header"></a>RYSUNEK 13. Nagłówek TCP

Poniżej opisano format nagłówka TCP:

|&nbsp;Pole nagłówka |Przeznaczenie |
|------|------|
| **16-bitowy numer portu źródłowego** | To pole zawiera port, na którym jest wysyłany pakiet TCP. Prawidłowe porty TCP mieszczą się w zakresie od 1 do 0xFFFF. |
| **16-bitowy port docelowy** | To pole zawiera port TCP, na który jest wysyłany pakiet. Prawidłowe porty TCP mieszczą się w zakresie od 1 do 0xFFFF. |
| **32-bitowy numer sekwencji** | To pole zawiera numer sekwencyjny dla danych wysyłanych z tego końca połączenia. Oryginalna sekwencja jest określana podczas początkowej sekwencji połączeń między dwoma węzłami TCP. Każdy transfer danych od tego momentu powoduje zwiększenie liczby sekwencji o ilość wysłanych bajtów. |
| **32-bitowy numer potwierdzenia** | To pole zawiera numer sekwencyjny odpowiadający ostatniemu bajtowi odebranemu po tej stronie połączenia. Służy do określenia, czy dane wysłane wcześniej zostały pomyślnie odebrane przez inne zakończenie połączenia. |
| **4-bitowa Długość nagłówka** | To pole zawiera liczbę 32-bitowych wyrazów w nagłówku TCP. Jeśli w nagłówku TCP nie ma żadnych opcji, to pole ma wartość 5. |
| **6-bitowe bity kodu** |To pole zawiera sześć różnych bitów kodu używanych do wskazywania różnych informacji o kontroli skojarzonych z połączeniem. Bity sterujące są zdefiniowane w następujący sposób: <br \> -URG (21): pilne presen danych<br \> -ACK (20): numer potwierdzenia jest prawidłowy<br \> -PSH — (19): należy bezpośrednio obsłużyć te dane<br \> -RST (18): Resetowanie połączenia<br \> -syn (17): synchronizacja numerów sekwencyjnych (użytych do ustanowienia połączenia) <br \> -FIN (16): nadawca zakończył przesyłanie |
|**okno 16-bitowe** |To pole jest używane do sterowania przepływem. Zawiera ilość bajtów, które gniazdo może obecnie odbierać. Ta w istocie jest używana do sterowania przepływem. Nadawca jest odpowiedzialny za upewnienie się, że dane do wysłania mieszczą się w oknie anonsowanym odbiorcy. |
|**16-bitowa suma kontrolna TCP** |To pole zawiera 16-bitową sumę kontrolną pakietu, w tym nagłówek TCP, obszar danych pakietu i nagłówek pseudo IP. |
|**16-bitowy wskaźnik pilny** |To pole zawiera dodatnie przesunięcie ostatniego bajtu pilnych danych. To pole jest prawidłowe tylko wtedy, gdy w nagłówku jest ustawiony bit kodu URG. |

> [!NOTE]  
> *Oczekuje się, że wszystkie nagłówki w implementacji TCP/IP mają być w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym*.

### <a name="tcp-enable"></a>Włączanie protokołu TCP       
Przed przystąpieniem do połączeń TCP i przesyłania pakietów aplikacja musi najpierw włączyć protokół TCP, wywołując usługę ***nx_tcp_enable*** . Po włączeniu aplikacja jest bezpłatna, aby uzyskać dostęp do wszystkich usług TCP.  

### <a name="tcp-socket-create"></a>Tworzenie gniazda TCP    
Gniazda TCP są tworzone podczas inicjowania lub podczas wykonywania przez wątki aplikacji. Początkowy typ usługi, czas wygaśnięcia i rozmiar okna są zdefiniowane przez usługę ***nx_tcp_socket_create*** . W aplikacji nie ma ograniczeń dotyczących liczby gniazd TCP.  

### <a name="tcp-checksum"></a>Suma kontrolna TCP     
Protokół TCP określa 16-bitową sumę kontrolną, która pokrywa się z pseudo nagłówka IP (składa się ze źródłowego adresu IP, docelowego adresu IP oraz słowa IP protokołu/długości), nagłówka TCP i danych pakietu TCP. Jedyną różnicą sum kontrolnych nagłówka pakietów TCP i IPv6 jest to, że źródłowy i docelowy adres IP to 32 bit w IPv4 i 128 bit w protokole IPv6. 

Niektóre kontrolery sieci mogą wykonywać obliczenia sum kontrolnych TCP i walidację sprzętu. W przypadku takich systemów aplikacje mogą chcieć używać logiki sum kontrolnych sprzętowych, jak to możliwe, aby zmniejszyć obciążenie środowiska uruchomieniowego. Aplikacje mogą wyłączyć logikę obliczeń sum kontrolnych protokołu TCP z biblioteki NetX Duo w czasie kompilacji, definiując ***NX_DISABLE_TCP_TX_CHECKSUM** _ i _ *_NX_DISABLE_TCP_RX_CHECKSUM_* *. W ten sposób kod sumy kontrolnej protokołu TCP nie jest kompilowany w. Jednak należy zachować ostrożność, jeśli zainstalowano opcjonalny pakiet IPsec NetX Duo, a połączenie TCP może wymagać przechodzenia przez bezpieczny kanał. W takim przypadku dane w pakietach należących do połączenia TCP są już zaszyfrowane i większość sprzętowych modułów sumy kontrolnej TCP znajdujących się w sterowniku sieciowym nie jest w stanie wygenerować prawidłowej wartości sumy kontrolnej z zaszyfrowanego ładunku TCP.

Aby rozwiązać ten problem, aplikacja utrzymuje logikę sum kontrolnych TCP dostępną w bibliotece i używa funkcji interfejsu. W przypadku włączenia funkcji interfejsu w module TCP jest znane, jak prawidłowo obsługiwać sumę kontrolną TCP, jeśli sterownik może również obliczyć sumę kontrolną:

1) Jeśli pakiet TCP nie podlega procesowi IPsec, sprzęt interfejsu sieciowego może obliczyć sumę kontrolną. W związku z tym moduł TCP nie próbuje obliczyć sumy kontrolnej;

2) Jeśli pakiet protokołu IPsec jest zainstalowany, a pakiet TCP podlega procesowi IPsec, moduł TCP oblicza sumę kontrolną w oprogramowaniu przed wysłaniem pakietu do warstwy protokołu IPsec.

### <a name="tcp-port"></a>Port TCP     
Port TCP jest logicznym punktem połączenia w protokole TCP. W składniku TCP programu NetX Duo istnieją 65 535 prawidłowe porty z zakresu od 1 do 0xFFFF. W przeciwieństwie do protokołu UDP, w którym dane z jednego portu mogą być wysyłane do dowolnego innego portu docelowego, port TCP jest połączony z innym określonym portem TCP i tylko wtedy, gdy połączenie jest nawiązywane, może mieć miejsce transfer danych — i tylko między dwoma portami.

> [!IMPORTANT]
> *Porty TCP są całkowicie oddzielone od portów UDP, np. numer portu UDP 1 nie ma powiązania z portem TCP o numerze 1*.

### <a name="client-server-model"></a>Model Client-Server     
Aby można było korzystać z protokołu TCP na potrzeby transferu danych, należy najpierw nawiązać połączenie między dwoma gniazdami TCP. Ustanowienie połączenia odbywa się na serwerze klienta. Po stronie klienta połączenia znajduje się Strona, która inicjuje połączenie, a po stronie serwera po prostu czeka na żądania połączenia klienta przed ukończeniem przetwarzania.

> [!IMPORTANT]
> *W przypadku urządzeń z wieloma lokalizacjami funkcja NetX Duo automatycznie określa adres źródłowy do użycia w połączeniu, a adres następnego przeskoku na podstawie docelowego adresu IP połączenia. Ponieważ protokół TCP jest ograniczony do wysyłania pakietów do emisji pojedynczej (np. "nieemisyjne") adresów docelowych, NetX Duo nie wymaga "podpowiedzi" do wybierania źródłowego adresu IPv6*.

### <a name="tcp-socket-state-machine"></a>Komputer stanu gniazda TCP      
Połączenie między dwoma gniazdami TCP (jeden klient i jeden serwer) jest złożone i jest zarządzane w sposób komputerowy. Każde gniazdo TCP zostanie uruchomione w stanie ZAMKNIĘTYm. Za pośrednictwem zdarzeń połączeń każda maszyna stanu gniazda jest migrowana w stan USTANOWIONy, który jest miejscem, w którym odbywa się zbiorczo transfer danych w protokole TCP. Gdy jedna strona połączenia nie chce już wysyłać danych, zostanie odłączona. Po rozłączeniu z drugą stroną, gdy gniazdo TCP powróci do stanu ZAMKNIĘTEgo. Ten proces jest powtarzany za każdym razem, gdy klient i serwer TCP nawiązują połączenie. Rysunek 14 przedstawia różne stany komputera stanu TCP.

### <a name="tcp-client-connection"></a>Połączenie klienta TCP       
Jak wspomniano wcześniej, po stronie klienta połączenia TCP zostaje zainicjowany żądanie połączenia z serwerem TCP. Aby można było wykonać żądanie połączenia, należy włączyć protokół TCP w wystąpieniu adresu IP klienta. Ponadto gniazdo TCP klienta musi być utworzone za pomocą usługi ***nx_tcp_socket_create** _ i powiązana z portem za pośrednictwem _ *_nx_tcp_client_socket_bind_** usługi.

Po powiązaniu gniazda klienta usługa ***nxd_tcp_client_socket_connect*** zostanie użyta do nawiązania połączenia z serwerem TCP. Należy pamiętać, że gniazdo musi być w stanie ZAMKNIĘTYm, aby można było zainicjować próbę połączenia. Ustanowienie połączenia rozpoczyna się od NetX Duo wystawiającego pakiet SYN, a następnie czeka na powrót z powrotem do pakietu ACK z serwera, który oznacza akceptację żądania połączenia. Po otrzymaniu potwierdzenia SYN NetX Duo reaguje na pakiet ACK i promuje gniazdo klienta do określonego stanu.

![Diagram stanów komputera stanu TCP.](./media/user-guide/image24.png)   

**RYSUNEK 14. Stany komputera stanu TCP**


> [!WARNING]
> *Aplikacje powinny używać **nxd_tcp_client_socket_connect** dla połączeń TCP i IPv6 z protokołem IPv4. Aplikacje mogą nadal używać **nx_tcp_client_socket_connect** dla połączeń TCP IPv4, ale zachęca się deweloperów do korzystania z **nxd_tcp_client_socket_connect** , ponieważ **nx_tcp_client_socket_connect** będzie ostatecznie przestarzałe*.

*Podobnie **nxd_tcp_socket_peer_info_get** współpracuje z połączeniami TCP IPv4 lub IPv6. Jednak **nx_tcp_socket_peer_info_get** nadal są dostępne dla starszych aplikacji. Deweloperzy są zachęcani do korzystania z **nxd_tcp_socket_peer_info_get** przechodzenia do przodu*.

### <a name="tcp-client-disconnection"></a>Odłączanie klienta TCP    
Zamykanie połączenia odbywa się przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie określono zawieszenia, gniazdo klienta wysyła do gniazda serwerowego pakiet RST i umieszcza gniazdo w stanie ZAMKNIĘTYm. W przeciwnym razie, jeśli zażądano zawieszenia, zostaje wykonany pełny protokół Disconnect protokołu TCP w następujący sposób: 

- Jeśli serwer zainicjował wcześniej żądanie rozłączenia (gniazdo klienta już otrzymał pakiet FIN, odpowiedział na ACK i jest w stanie oczekiwania na zamknięcie), NetX Duo podnosi stan gniazda TCP klienta do ostatniego potwierdzenia i wysyła pakiet FIN. Następnie czeka na potwierdzenie z serwera przed ukończeniem rozłączenia i przeprowadzeniem stanu ZAMKNIĘTEgo.

- Jeśli z drugiej strony, klient jest pierwszym zainicjowaniem żądania rozłączenia (serwer nie został odłączony, a gniazdo nadal jest w stanie), NetX Duo wysyła pakiet FIN w celu zainicjowania rozłączenia i czeka na otrzymanie elementu FIN i ACK z serwera przed ukończeniem rozłączenia i umieszczenie gniazda w stanie ZAMKNIĘTYm.

Jeśli w kolejce transmisji gniazda nadal istnieją pakiety, NetX Duo zawiesza się dla określonego limitu czasu, aby umożliwić potwierdzenie pakietów. Jeśli limit czasu wygaśnie, NetX Duo opróżnia kolejkę transmisji gniazda klienta. 

Aby usunąć powiązanie portu z gniazda klienta, aplikacja wywołuje ***nx_tcp_client_socket_unbind***. Gniazdo musi znajdować się w stanie ZAMKNIĘTYm lub w trakcie rozłączania (tj. czas oczekiwania na stan) przed zwolnieniem portu; w przeciwnym razie zwracany jest błąd.

Na koniec, jeśli aplikacja nie potrzebuje już gniazda klienta, wywołuje ***nx_tcp_socket_delete*** , aby usunąć gniazdo.

### <a name="tcp-server-connection"></a>Połączenie z serwerem TCP      
Po stronie serwera połączenia TCP jest pasywny; oznacza to, że serwer czeka na zainicjowanie żądania połączenia przez klienta. Aby zaakceptować połączenie z klientem, należy najpierw włączyć protokół TCP w wystąpieniu adresu IP, wywołując usługę ***nx_tcp_enable** _. Następnie aplikacja musi utworzyć gniazdo TCP przy użyciu usługi _ *_nx_tcp_socket_create_**.  

Należy również skonfigurować gniazdo serwera do nasłuchiwania żądań połączeń. Jest to realizowane za pomocą usługi ***nx_tcp_server_socket_listen*** . Ta usługa umieszcza gniazdo serwera w stanie nasłuchiwania i wiąże określony port serwera z gniazdem.

> [!NOTE] 
> *Aby ustawić procedurę wywołania zwrotnego gniazda Socket, aplikacja określa odpowiednią funkcję wywołania zwrotnego dla tcp_listen_callback argumentu usługi **nx_tcp_server_socket_listen** . Ta funkcja wywołania zwrotnego aplikacji jest następnie wykonywana przez NetX Duo, gdy na tym porcie serwera zażądano nowego połączenia. Przetwarzanie w wywołaniu zwrotnym jest pod kontrolą aplikacji.*

Aby akceptować żądania połączenia klienta, aplikacja wywołuje usługę ***nx_tcp_server_socket_accept** _. Gniazdo serwera musi znajdować się w stanie nasłuchiwania lub zostać ODEBRANe (tj. serwer jest w stanie nasłuchiwania i odebrał pakiet SYN z klienta wysyłającego żądanie połączenia) w celu wywołania usługi Accept. Pomyślne zwrócenie stanu z _ *_nx_tcp_server_socket_accept_** wskazuje, że połączenie zostało skonfigurowane i że gniazdo serwera jest w stanie nawiązane.

Gdy gniazdo serwera ma prawidłowe połączenie, dodatkowe żądania połączenia klienta są umieszczane w kolejce do głębokości określonej przez *listen_queue_size,* do  * usługi **nx_tcp_server_socket_listen** _. W celu przetworzenia kolejnych połączeń na porcie serwera aplikacja musi wywołać _ *_nx_tcp_server_socket_relisten_** z dostępnym gniazdem (tj. gniazdem w stanie zamkniętym). Należy pamiętać, że tego samego gniazda serwerowego można użyć, jeśli poprzednie połączenie skojarzone z gniazdem zostanie zakończone, a gniazdo jest w stanie ZAMKNIĘTYm.

### <a name="tcp-server-disconnection"></a>Odłączanie serwera TCP     
Zamykanie połączenia odbywa się przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie określono zawieszenia, gniazdo serwera wysyła do gniazda klienta parametr RST i umieszcza gniazdo w stanie ZAMKNIĘTYm. W przeciwnym razie, jeśli zażądano zawieszenia, zostaje wykonany pełny protokół Disconnect protokołu TCP w następujący sposób:

- Jeśli klient zainicjował wcześniej żądanie rozłączenia (gniazdo serwera już otrzymał pakiet FIN, odpowiedział na ACK i jest w stanie oczekiwania na zamknięcie), NetX Duo podnosi stan gniazda TCP do ostatniego potwierdzenia i wysyła pakiet FIN. Następnie czeka na potwierdzenie z klienta przed ukończeniem rozłączenia i przeprowadzeniem stanu ZAMKNIĘTEgo.

- Jeśli z drugiej strony, serwer jest pierwszym zainicjowaniem żądania rozłączenia (klient nie został odłączony, a gniazdo nadal jest w stanie), NetX Duo wyśle pakiet FIN w celu zainicjowania rozłączenia i czeka na otrzymanie elementu FIN i ACK z klienta przed ukończeniem odłączenia i umieszczenie gniazda w stanie ZAMKNIĘTYm.

Jeśli w kolejce transmisji gniazda nadal istnieją pakiety, NetX Duo zawiesza się dla określonego limitu czasu, aby umożliwić potwierdzenie tych pakietów. Jeśli limit czasu wygaśnie, NetX Duo opróżnia kolejkę przesyłania w gnieździe serwera.

Po zakończeniu przetwarzania rozłączenia, gdy gniazdo serwera jest w stanie ZAMKNIĘTYm, aplikacja musi wywołać usługę ***nx_tcp_server_socket_unaccept** _, aby zakończyć skojarzenie tego gniazda z portem serwera. Należy pamiętać, że ta usługa musi być wywoływana przez aplikację, nawet jeśli _*_nx_tcp_socket_disconnect_*_ lub _*_nx_tcp_server_socket_accept_*_ zwracają stan błędu. Po powrocie _*_nx_tcp_server_socket_unaccept_*_ gniazdo może być używane jako gniazdo klienta lub serwera, a nawet usunięte, jeśli nie jest już potrzebne. Jeśli pożądane jest zaakceptowanie innego połączenia klienta na tym samym porcie serwera, usługa _ *_nx_tcp_server_socket_relisten_** powinna być wywoływana w tym gnieździe.

Poniższy segment kodu ilustruje sekwencję wywołań typowego serwera TCP używa:

```c
/* Set up a previously created TCP socket to
   listen on port 12 */
nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1)
{
    /* Wait for a client socket connection request
       for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP
       client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on
       the port. */
    nx_tcp_server_socket_unaccept(&server_socket);
    /* Set up server socket to relisten on the
       same port for the next client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>Sprawdzanie poprawności      
Maksymalny rozmiar segmentu (Maximum) to maksymalna ilość bajtów odbieranych przez hosta TCP bez fragmentacji przez podstawową warstwę adresów IP. Podczas fazy ustanowienia połączenia TCP oba punkty końcowe wymieniają własną wartość TCP, tak że nadawca nie wyśle segmentu danych TCP, który jest większy niż rozmiar tego odbiorcy. Moduł TCP NetX Duo będzie opcjonalnie sprawdzać anonsowaną wartość tego obiektu równorzędnego przed nawiązaniem połączenia. Domyślnie NetX Duo nie zezwala na takie sprawdzenie. W przypadku aplikacji, które chcą wykonać weryfikację o kluczu, należy zdefiniować ***NX_ENABLE_TCP_MSS_CHECK** _ podczas kompilowania biblioteki NetX Duo, a wartość minimalna powinna być zdefiniowana w _*_NX_TCP_MSS_MINIMUM_*_. Przychodzące połączenia TCP o wartościach o wielkości/mniej więcej niż _ *_NX_TCP_MSS_MINIMUM_** są porzucane.

### <a name="stop-listening-on-a-server-port"></a>Zatrzymaj nasłuchiwanie na porcie serwera    
Jeśli aplikacja nie chce już nasłuchiwać żądań połączenia klienta na porcie serwera, który został wcześniej określony przez wywołanie usługi ***nx_tcp_server_socket_listen** _, aplikacja po prostu wywołuje usługę _ *_nx_tcp_server_socket_unlisten_**. Ta usługa umieszcza wszystkie gniazda oczekujące na połączenie z powrotem w stanie ZAMKNIĘTYm i zwalnia wszystkie pakiety żądań połączeń klienta umieszczonych w kolejce. 

### <a name="tcp-window-size"></a>Rozmiar okna TCP   
Podczas fazy instalacji i transferu danych połączenia każdy port raportuje ilość danych, które może obsłużyć, czyli rozmiar okna. Gdy dane są odbierane i przetwarzane, rozmiar tego okna jest dostosowywany dynamicznie. W przypadku protokołu TCP nadawca może wysłać tylko ilość danych, które pasują do okna odbiorcy. W zasadzie rozmiar okna zapewnia kontrolę przepływu na potrzeby transferu danych w każdym kierunku połączenia.   

### <a name="tcp-packet-send"></a>Wysyłanie pakietów TCP     
Wysyłanie danych TCP jest łatwo realizowane przez wywołanie funkcji ***nx_tcp_socket_send*** . Jeśli rozmiar przesyłanych danych jest większy niż wartość rozmiaru w gnieździe lub bieżący rozmiar okna odbioru elementu równorzędnego, w zależności od tego, który z nich jest mniejszy, wewnętrzna logika TCP carves dane, które pasują do minimalnej (rozmiaru pasma, okna odbierania równorzędnego) do transmisji. Ta usługa następnie kompiluje nagłówek TCP przed pakietem (w tym obliczenia sumy kontrolnej). Jeśli rozmiar okna odbiornika jest różny od zera, obiekt wywołujący wyśle tyle danych, ile może wypełnić rozmiar okna odbiornika. Jeśli okno odbierania przestanie być równe zero, wywołujący może zawiesić się i zaczekać, aż rozmiar okna odbiornika zostanie odpowiednio zwiększony dla tego pakietu. W danym momencie wiele wątków może zawiesić się podczas próby wysłania danych za pomocą tego samego gniazda. 

> [!WARNING]  
> *Dane TCP znajdujące się w strukturze NX_PACKET powinny znajdować się na granicy długiego wyrazu. Ponadto musi być wystarczająca ilość miejsca między wskaźnikiem dołączania i wskaźnikiem początku danych do umieszczenia nagłówków TCP, IP i nośnika fizycznego*.

### <a name="tcp-packet-retransmit"></a>Ponowne przesyłanie pakietów TCP      
Wcześniej przesłane pakiety TCP wysłane faktycznie przechowywane wewnętrznie do momentu zwrócenia potwierdzenia po drugiej stronie połączenia. Jeśli przesyłane dane nie są potwierdzone w określonym limicie czasu, przechowywany pakiet jest ponownie wysyłany i ustawiany jest następny limit czasu. Po odebraniu potwierdzenia wszystkie pakiety objęte numerem potwierdzenia w wewnętrznej kolejce transmisji są ostatecznie wydane.  

> [!WARNING]   
> *Aplikacja nie korzysta ponownie z pakietu ani nie zmienia zawartości pakietu po nx_tcp_socket_send () zwraca z NX_SUCCESS. Przesłany pakiet jest ostatecznie uwalniany przez przetwarzanie wewnętrzne NetX Duo po potwierdzeniu danych przez inne zakończenie*.

### <a name="tcp-keepalive"></a>Utrzymywanie aktywności TCP     
Funkcja utrzymywania aktywności protokołu TCP umożliwia gnieździi wykrywanie, czy jego element równorzędny rozłącza się bez poprawnego zakończenia (na przykład awaria elementu równorzędnego), czy też uniemożliwiać określonym obiektom monitorowania sieci przerwanie połączenia przez długie okresy bezczynności. Ruch przychodzący TCP działa przez okresowe wysyłanie ramki TCP bez danych, a numer sekwencyjny jest ustawiony na jeden mniejszy niż bieżący numer sekwencyjny. Po odebraniu takiej ramki utrzymania protokołu TCP odbiorca (Jeśli nadal działa) odpowiedzi z POTWIERDZENIEm dla bieżącego numeru sekwencji. Spowoduje to zakończenie transakcji utrzymywania aktywności.  

Domyślnie funkcja utrzymywania aktywności nie jest włączona. Aby można było użyć tej funkcji, biblioteka NetX Duo musi być skompilowana przy użyciu funkcji ***NX_ENABLE_TCP_KEEPALIVE** _ zdefiniowanej. Symbol _ *_NX_TCP_KEEPALIVE_INITIAL_** określa liczbę sekund braku aktywności przed zainicjowaniem ramki utrzymywania aktywności.  

### <a name="tcp-packet-receive"></a>Odbieranie pakietów TCP   
Przetwarzanie pakietów odbioru protokołu TCP (wywoływane z wątku pomocnika adresów IP) jest odpowiedzialne za obsługę różnych akcji połączenia i rozłączania, a także przesyłanie potwierdzenia. Ponadto przetwarzanie pakietów odbioru protokołu TCP jest odpowiedzialne za umieszczanie pakietów z danymi odbieranymi w odpowiedniej kolejce lub dostarczenie pakietu do pierwszego wstrzymanego wątku, oczekując na pakiet.

### <a name="tcp-receive-notify"></a>Powiadomienie o odebraniu protokołu TCP     
Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, należy użyć funkcji ***nx_tcp_socket_receive_notify*** . Ta funkcja rejestruje funkcję odbierania pakietów wywołania zwrotnego dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, funkcja wywołania zwrotnego jest wykonywana.  

Zawartość funkcji wywołania zwrotnego to applicationspecific; Jednak funkcja najprawdopodobniej zawiera logikę do informowania wątku przetwarzania, że pakiet jest dostępny w odpowiednim gnieździe. 

### <a name="thread-suspension"></a>Zawieszenie wątku      
Jak wspomniano wcześniej, wątki aplikacji mogą wstrzymywać się podczas próby odebrania danych z określonego portu TCP. Po odebraniu pakietu na tym porcie jest on przyznany do pierwszego wątku, a następnie wznowiony. Opcjonalny limit czasu jest dostępny w przypadku zawieszania pakietu odbioru TCP, który jest funkcją dostępną dla większości usług NetX Duo.  

Zawieszenie wątku jest również dostępne dla połączenia (zarówno klienta, jak i serwera), powiązania klienta i usług odłączania.  

### <a name="tcp-socket-statistics-and-errors"></a>Statystyka i błędy gniazda TCP     
Jeśli ta opcja jest włączona, oprogramowanie NetX Duo TCP Socket śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/TCP są obsługiwane następujące raporty statystyczne i błędy:   

- Całkowita liczba wysłanych pakietów TCP  
- Całkowita liczba wysłanych bajtów TCP  
- Całkowita liczba odebranych pakietów TCP   
- Całkowita liczba odebranych bajtów TCP   
- Całkowita liczba nieprawidłowych pakietów TCP   
- Całkowita liczba porzuconych pakietów odbioru protokołu TCP    
- Łączne błędy sum kontrolnych odbioru TCP   
- Łączna liczba połączeń TCP   
- Łączna liczba rozłączeń TCP   
- Całkowita liczba porzuconych połączeń TCP    
- Łączna liczba retransmisji pakietów TCP   
- Wysłane pakiety gniazda TCP   
- Wysłane bajty gniazda TCP   
- Odebrane pakiety TCP Socket   
- Odebrane bajty gniazda TCP   
- Ponowne przesyłanie pakietów TCP Socket    
- Pakiety gniazd TCP dodane do kolejki    
- Błędy sum kontrolnych gniazda TCP    
- Stan gniazda TCP    
- Głębokość kolejki transmisji gniazda TCP    
- Rozmiar okna wysyłania gniazda TCP    
- Rozmiar okna odbierania gniazda TCP    

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_tcp_info_get** _ dla łącznej liczby statystyk TCP oraz usługi _ *_nx_tcp_socket_info_get_** dla statystyk TCP na gniazdo.

### <a name="tcp-socket-control-block-nx_tcp_socket"></a>NX_TCP_SOCKET bloku sterowania gniazdem TCP      
Cechy poszczególnych gniazd TCP znajdują się w skojarzonym bloku sterowania *NX_TCP_SOCKET* , który zawiera przydatne informacje, takie jak link do struktury danych IP, interfejs połączenia sieciowego, port powiązany i kolejka odbierania pakietów. Ta struktura jest zdefiniowana w pliku ***nx_api. h*** .