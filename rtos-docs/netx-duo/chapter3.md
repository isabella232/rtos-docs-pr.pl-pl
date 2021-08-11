---
title: Rozdział 3 — Składniki funkcjonalne Azure RTOS NetX Duo
description: Ten rozdział zawiera opis stosu TCP/IP NetX Duo o wysokiej Azure RTOS wydajności z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32af483db1f97b45bfe3d334b8c79d984dedc8470a37ce1d4164331549b6954c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789052"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx-duo"></a>Rozdział 3 — Składniki funkcjonalne Azure RTOS NetX Duo

Ten rozdział zawiera opis stosu TCP/IP NetX Duo o wysokiej Azure RTOS wydajności z perspektywy funkcjonalnej. 

## <a name="execution-overview"></a>Omówienie wykonywania

W aplikacji NetX Duo istnieje pięć typów wykonywania programów: inicjowanie, wywołania interfejsu aplikacji, wewnętrzny wątek ip, okresowe czasomierze IP i sterownik sieciowy.

> [!NOTE]
> *NetX Duo zakłada istnienie ThreadX i zależy od jego wykonywania wątku, zawieszenia, okresowych czasomierzy i obiektów wzajemnego wykluczania.*

### <a name="initialization"></a>Inicjalizacja

Usługa ***nx_system_initialize** _ musi zostać wywołana przed wywoływaniem jakiejkolwiek innej usługi NetX Duo. Inicjowanie systemu można nazwać z funkcji ThreadX _ *_tx_application_define_** lub z wątków aplikacji.

Po ***nx_system_initialize** _ zwraca, system jest gotowy do tworzenia pul pakietów i wystąpień adresów IP. Ponieważ tworzenie wystąpienia adresu IP wymaga domyślnej puli pakietów, przed utworzeniem wystąpienia adresu IP musi istnieć co najmniej jedna pula pakietów NetX Duo. Tworzenie pul pakietów i wystąpień adresów IP jest dozwolone z funkcji inicjowania ThreadX _ *_tx_application_define_** i z wątków aplikacji.

Wewnętrznie tworzenie wystąpienia adresu IP odbywa się w dwóch częściach: pierwsza część jest wykonywana  w kontekście obiektu wywołującego, z tx_application_define lub z kontekstu wątku aplikacji. Obejmuje to skonfigurowanie struktury danych IP i utworzenie różnych zasobów adresów IP, w tym wewnętrznego wątku adresu IP. Druga część jest wykonywana podczas początkowego wykonywania z wątku wewnętrznego adresu IP. W tym miejscu najpierw jest wywoływany sterownik sieciowy dostarczony podczas pierwszej części tworzenia adresu IP. Wywołanie sterownika sieciowego z wewnętrznego wątku IP umożliwia sterownikowi wykonywanie operacji we/wy i zawieszanie podczas przetwarzania inicjowania.

Gdy sterownik sieci powraca z przetwarzania inicjowania, tworzenie adresu IP jest zakończone.

Inicjowanie protokołu IPv6 w programie NetX Duo wymaga kilku dodatkowych usług NetX Duo. Zostały one bardziej szczegółowo opisane w sekcji [IPv6 w netx duo](#ipv6-in-netx-duo) w dalszej części tego rozdziału.

> [!NOTE]
> *Usługa NetX Duo **nx_ip_status_check** uzyskać informacje o wystąpieniu adresu IP i jego podstawowym stanie interfejsu. Takie informacje o stanie obejmują to, czy łącze jest zainicjowane, włączone i adres IP jest rozpoznawane. Te informacje są używane do synchronizowania wątków aplikacji, które wymagają użycia nowo utworzonego wystąpienia adresu IP. W przypadku systemów wieloadresowych zobacz [Multihome Support](#multihome-support). **nx_ip_interface_status_check** można uzyskać 3informacje w określonym interfejsie.*

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Wywołania z aplikacji są w dużej mierze wykonane z wątków aplikacji działających w ramach threadX RTOS. Jednak niektóre inicjowanie, tworzenie i włączanie usług mogą być wywoływane z tx_application_define ***.*** Sekcje "Dozwolone z" w rozdziale 4 — opis Azure RTOS [NetX Duo Services](chapter4.md) wskazują, z którego można nazwać każdą usługę NetX Duo.

W większości przypadków działania intensywnie przetwarzane, takie jak obliczanie sumy kontrolnej, są wykonywane w kontekście wątku wywołującego — bez blokowania dostępu innych wątków do wystąpienia adresu IP. Na przykład w przypadku transmisji obliczenie sumy kontrolnej UDP jest wykonywane wewnątrz usługi ***nx_udp_socket_send** _, przed wywołaniem podstawowej funkcji wysyłania adresów IP. W odebranym pakiecie sumy kontrolne UDP są obliczane w usłudze _ *_nx_udp_socket_receive_** wykonywanej w wątku aplikacji. Pomaga to zapobiec wsyłaniu żądań sieciowych wątków o wyższym priorytecie z powodu intensywnego przetwarzania obliczeń sumy kontrolnej w wątkach o niższym priorytecie.

Wartości, takie jak adresy IP i numery portów, są przekazywane do interfejsów API w kolejności bajtów hosta. Wewnętrznie te wartości są również przechowywane w kolejności bajtów hosta. Dzięki temu deweloperzy mogą łatwo wyświetlać wartości za pośrednictwem debugera. Gdy te wartości są zaprogramowane w ramkę do transmisji, są one konwertowane na kolejność bajtów sieci.

### <a name="internal-ip-thread"></a>Wewnętrzny wątek adresu IP

Jak wspomniano, każde wystąpienie adresu IP w netx duo ma własny wątek. Priorytet i rozmiar stosu wewnętrznego wątku IP są definiowane w ***usłudze nx_ip_create*** ip. Wewnętrzny wątek adresu IP jest tworzony w trybie gotowym do wykonania. Jeśli wątek IP ma wyższy priorytet niż wątek wywołujący, wywłaszcz może wystąpić wewnątrz wywołania tworzenia adresu IP.

Punkt wejścia wewnętrznego wątku IP znajduje się w funkcji wewnętrznej _ ***nx_ip_thread_entry***. Po zakończeniu wewnętrzny wątek adresu IP najpierw kończy inicjowanie sterownika sieci, który składa się z trzech wywołań sterownika sieci specyficznego dla aplikacji. Pierwsze wywołanie to dołączenie sterownika sieciowego do wystąpienia adresu IP, po którym następuje wywołanie inicjowania, które umożliwia sterownikowi sieciowemu przejść przez proces inicjowania. Po powrocie sterownika sieciowego z inicjowania (może on zostać wstrzymany podczas oczekiwania na prawidłowe skonfigurowanie sprzętu), wewnętrzny wątek ip ponownie wywołuje sterownik sieciowy, aby włączyć połączenie. Po powrocie sterownika sieciowego z wywołania włączania połączenia wewnętrzny wątek adresu IP przechodzi w pętli na zawsze sprawdzając różne zdarzenia, które wymagają przetwarzania dla tego wystąpienia adresu IP. Zdarzenia przetwarzane w tej pętli obejmują odroczone odbiór pakietów IP, zestaw fragmentów pakietów IP, przetwarzanie ping protokołu ICMP, przetwarzanie protokołu IGMP, przetwarzanie kolejki pakietów TCP, okresowe przetwarzanie TCP, limity czasu zestawu fragmentów adresów IP i okresowe przetwarzanie IGMP. Zdarzenia obejmują również działania rozwiązywania adresów; Przetwarzanie pakietów ARP i okresowe przetwarzanie ARP w protokole IPv4, wykrywaniu zduplikowanych adresów, pozyskiwaniu routerów i odnajdywaniu sąsiadów w protokole IPv6.

> [!CAUTION]
> *Funkcje wywołania zwrotnego NetX Duo, w tym wywołania zwrotne nasłuchiwać i rozłączania, są wywoływane z wewnętrznego wątku adresu IP, a nie oryginalnego wątku wywołującego. Aplikacja musi zadbać o to, aby nie zawieszać się wewnątrz żadnej funkcji wywołania zwrotnego NetX Duo.*

### <a name="ip-periodic-timers"></a>Okresowe czasomierze IP

Istnieją dwa czasomierze okresowe ThreadX używane dla każdego wystąpienia adresu IP. Pierwszy z nich to czasomierz z jedną sekundą dla protokołów ARP, IGMP i TCP, a także kieruje przetwarzaniem ponownego zsyłania fragmentów adresów IP. Drugi czasomierz to czasomierz 100ms, który ma na celu przeoczenie limitu czasu retransmisji TCP i operacje związane z protokołem IPv6.

### <a name="network-driver"></a>Sterownik sieciowy

Każde wystąpienie adresu IP w aplikacji NetX Duo ma podstawowy interfejs, który jest identyfikowany przez sterownik urządzenia określony w ***nx_ip_create*** service. Sterownik sieciowy jest odpowiedzialny za obsługę różnych żądań NetX Duo, w tym transmisji pakietów, odbioru pakietów oraz żądań stanu i kontroli. 

W przypadku systemu wieloadomowego wystąpienie adresu IP ma wiele interfejsów, z których każdy ma skojarzony sterownik sieciowy, który wykonuje te zadania dla odpowiedniego interfejsu.

Sterownik sieciowy musi również obsługiwać zdarzenia asynchroniczne występujące na nośniku. Zdarzenia asynchroniczne z nośnika obejmują odbiór pakietów, uzupełnianie transmisji pakietów i zmiany stanu. NetX Duo udostępnia sterownikowi siecioweowi kilka funkcji dostępu do obsługi różnych zdarzeń. Te funkcje są przeznaczone do wywoływania z rutynowej części usługi przerwań sterownika sieciowego. W przypadku sieci IPv4 sterownik sieci powinien przesyłać dalej wszystkie odebrane pakiety ARP ***do*** _nx_arp_packet_deferred_receive funkcji wewnętrznej. Wszystkie pakiety RARP powinny być przekazywane do funkcji ***_nx_rarp_packet_deferred_receive** _internal. Istnieją dwie opcje pakietów IP. Jeśli wymagana jest szybka wysyłka pakietów IP, przychodzące pakiety IP powinny być przekazywane do _ *_ _nx_ip_packet_receive_* _ w celu natychmiastowego przetwarzania. Znacznie poprawia to wydajność netX Duo w obsłudze pakietów IP. W przeciwnym razie należy przekierowyć pakiety IP do _ *_ _nx_ip_packet_deferred_receive_** . Ta usługa umieszcza pakiet IP w kolejce przetwarzania odroczonego, gdzie jest obsługiwany przez wewnętrzny wątek adresu IP, co powoduje najmniejszą ilość czasu przetwarzania ISR.

Sterownik sieciowy może również odroczyć przetwarzanie przerwań, aby zabrakło kontekstu wątku IP. W tym trybie isr musi zapisać niezbędne informacje, wywołać funkcję wewnętrzną _nx_ip_driver_deferred_processing ***i*** potwierdzić kontroler przerwań. Ta usługa powiadamia wątek adresu IP, aby zaplanować wywołanie zwrotne do sterownika urządzenia w celu ukończenia procesu zdarzenia, które powoduje przerwanie.

Niektóre kontrolery sieciowe są w stanie wykonywać obliczenia i weryfikację sumy kontrolnej nagłówka TCP/IP na sprzęcie bez konieczności przyjmowania cennych zasobów procesora CPU. Aby skorzystać z funkcji możliwości sprzętowych, netx Duo udostępnia opcje włączania lub wyłączania różnych obliczeń sumy kontrolnej oprogramowania w czasie kompilacji, a także włączanie lub wyłączanie obliczeń sumy kontrolnej w czasie wykonywania, jeśli sterownik urządzenia jest w stanie komunikować się z warstwą adresów IP o to możliwości sprzętowe. Zobacz [Rozdział 5 — Azure RTOS NetX Duo Network Drivers,](chapter5.md) aby uzyskać bardziej szczegółowe informacje na temat pisania sterowników sieciowych NetX Duo.

### <a name="multihome-support"></a>Obsługa wielunadresowych

NetX Duo obsługuje systemy połączone z wieloma urządzeniami fizycznymi przy użyciu jednego wystąpienia adresu IP. Każdy interfejs fizyczny jest przypisywany do bloku sterowania interfejsem w wystąpieniu adresu IP. Aplikacje, które chcą używać systemu wieloadresowego, muszą zdefiniować wartość ***NX_MAX_PHSYCIAL_INTERFACES** _ dla liczby urządzeń fizycznych dołączonych do systemu i ponownie skompilować bibliotekę NetX Duo. Domyślnie _ *_NX_MAX_PHYSICAL_INTERFACES_** jest ustawiony na jeden, tworząc jeden blok sterowania interfejsem w wystąpieniu adresu IP.

Aplikacja NetX Duo tworzy jedno wystąpienie adresu IP dla urządzenia podstawowego przy użyciu ***nx_ip_create** _service. Dla każdego dodatkowego urządzenia sieciowego aplikacja dołącza urządzenie do wystąpienia adresu IP przy użyciu usługi _ *_nx_ip_interface_attach_**.

Każda struktura interfejsu sieciowego zawiera podzbiór informacji o sieci interfejsu sieciowego, który znajduje się w bloku sterowania ip, w tym adres IPv4 interfejsu, maskę podsieci, rozmiar jednostki MTU ip i informacje o adresie WARSTWY MAC.

> [!NOTE]
> *NetX Duo z obsługą wielunadresowych urządzeń jest wstecznie zgodny ze starszymi wersjami oprogramowania NetX Duo. Usługi, które nie mają jawnych informacji o interfejsie domyślnym dla podstawowego urządzenia sieciowego.*

Interfejs podstawowy ma zero indeksu na liście wystąpień adresów IP. Do każdego kolejnego urządzenia dołączonego do wystąpienia adresu IP jest przypisywany następny indeks.

Wszystkie usługi protokołu górnej warstwy, dla których jest włączone wystąpienie adresu IP, w tym TCP, UDP, ICMP i IGMP, są dostępne dla wszystkich dołączonych urządzeń.

W większości przypadków NetX Duo może określić najlepszy adres źródłowy do użycia podczas przesyłania pakietu. Wybór adresu źródłowego zależy od adresu docelowego. Usługi NetX Duo są dodawane w celu umożliwienia aplikacjom określenia określonego adresu źródłowego do użycia w przypadkach, gdy najbardziej odpowiedni adres nie może zostać określony przez adres docelowy. Przykładem może być system wieloadresowy. Aplikacja musi wysłać pakiet na adresy docelowe emisji IPv4 lub multiemisji.

Usługi przeznaczone specjalnie do tworzenia aplikacji wieloadresowych obejmują:

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

Te usługi zostały szczegółowo opisane w opisie usługi [NetX Duo Services](chapter4.md).

### <a name="loopback-interface"></a>Interfejs sprzężenia zwrotnego

Interfejs sprzężenia zwrotnego to specjalny interfejs sieciowy bez dołączonego fizycznego łącza. Interfejs sprzężenia zwrotnego umożliwia aplikacjom komunikowanie się przy użyciu adresu sprzężenia zwrotnego IPv4 127.0.0.1 Aby korzystać z interfejsu logicznego sprzężenia zwrotnego, upewnij się, że opcja konfigurowalna ***NX_DISABLE_LOOPBACK_INTERFACE*** nie jest ustawiona.

### <a name="interface-control-blocks"></a>Bloki kontrolek interfejsu

Liczba bloków sterowania interfejsu w wystąpieniu adresu IP to liczba interfejsów fizycznych (zdefiniowanych za pomocą funkcji ***NX_MAX_PHYSICAL_INTERFACES** _) oraz interfejs sprzężenia zwrotnego, jeśli jest włączony. Całkowita liczba interfejsów jest zdefiniowana w _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Warstwy protokołów

Protokół TCP/IP implementowany przez NetX Duo jest protokołem warstwowym, co oznacza, że bardziej złożone protokoły są zbudowane na podstawie prostszych protokołów bazowych. W przypadku protokołu TCP/IP protokół najniższej warstwy znajduje się na *poziomie* łącza i jest obsługiwany przez sterownik sieciowy. Ten poziom jest zwykle skierowany do sieci Ethernet, ale może być również światłowodowy, szeregowy lub praktycznie dowolny nośnik fizyczny.

W górnej części warstwy łącza znajduje się *warstwa sieciowa*. W przypadku protokołu TCP/IP jest to adres IP, który zasadniczo jest odpowiedzialny za wysyłanie i odbieranie prostych pakietów — w najlepszy sposób — przez sieć. Protokoły typu zarządzania, takie jak ICMP i IGMP, są zwykle również kategoryzowane jako warstwy sieciowe, mimo że korzystają z adresu IP podczas wysyłania i odbierania.

Warstwa *transportu* jest na wierzchu warstwy sieciowej. Ta warstwa jest odpowiedzialna za zarządzanie przepływem danych między hostami w sieci. NetX Duo obsługuje dwa typy usług transportowych: UDP i TCP. Usługi UDP zapewniają najlepsze wysyłanie i odbieranie danych między dwoma hostami w sposób bez połączenia, a protokół TCP zapewnia niezawodną usługę zorientowaną na połączenie między dwoma jednostkami hosta.

Ta warstwa jest odzwierciedlana w rzeczywistych pakietach danych sieciowych. Każda warstwa protokołu TCP/IP zawiera blok informacji nazywany nagłówkiem. Ta technika otaczającego dane (i prawdopodobnie informacje o protokole) nagłówkiem jest zwykle nazywana hermetyzację danych. Rysunek 1 przedstawia przykład warstw NetX Duo, a na rysunku 2 przedstawiono wynikowe hermetyzację danych wysyłanych przez protokołu UDP.

![Warstwy protokołów](./media/user-guide/image12.jpg)

**RYSUNEK 1. Warstwy protokołów**

## <a name="packet-pools"></a>Pule pakietów

Szybkie i deterministyczne przydzielanie pakietów zawsze stanowi wyzwanie w aplikacjach sieciowych w czasie rzeczywistym. Mając to na uwadze, NetX Duo umożliwia tworzenie wielu pul pakietów sieciowych o stałym rozmiarze i zarządzanie nimi.

Ponieważ pule pakietów NetX Duo składają się z bloków pamięci o stałym rozmiarze, nigdy nie ma żadnych wewnętrznych problemów z fragmentacją. Oczywiście fragmentacja powoduje zachowanie, które jest z założenia niedeterministyczne. Ponadto czas wymagany do przydzielenia i wolnego pakietów NetX Duo jest potrzebny do prostego manipulowania listami połączonymi. Ponadto alokacja pakietów i co najmniej ich co najmniej alokacja odbywa się na początku dostępnej listy. Zapewnia to najszybsze możliwe przetwarzanie listy połączonej.

![Hermetyzacja danych UDP](./media/user-guide/image13.png)

**RYSUNEK 2. Hermetyzacja danych UDP**

Brak elastyczności jest zwykle główną wadą pul pakietów o stałym rozmiarze. Określenie optymalnego rozmiaru ładunku pakietu, który obsługuje również pakiet przychodzący w najgorszym przypadku, jest trudne. Pakiety NetX Duo rozsyłają ten problem za pomocą opcjonalnej funkcji nazywanej łańcuchem pakietów. Rzeczywisty pakiet sieciowy może składać się z co najmniej jednego połączonego pakietu NetX Duo. Ponadto nagłówek pakietu zachowuje wskaźnik na górę pakietu. Po dodaniu dodatkowych protokołów ten wskaźnik jest po prostu przesuwany wstecz, a nowy nagłówek jest zapisywany bezpośrednio przed danymi. Bez technologii pakietów elastycznych stos musiałby przydzielić kolejny bufor i skopiować dane do nowego buforu z nowym nagłówkiem, który intensywnie przetwarza.

Ponieważ każdy rozmiar ładunku pakietu jest stały dla danej puli pakietów, dane aplikacji większe niż rozmiar ładunku będą wymagały wielu pakietów w łańcuchu. Podczas wypełniania pakietu danymi użytkownika aplikacja musi korzystać z usługi ***nx_packet_data_append***. Ta usługa przenosi dane aplikacji do pakietu. W sytuacjach, gdy pakiet nie wystarcza do przechowywania danych użytkownika, przydzielane są dodatkowe pakiety do przechowywania danych użytkownika. Aby można było używać łańcucha pakietów, sterownik musi mieć możliwość odbierania lub przesyłania z pakietów łańcuchowych.

W przypadku systemów osadzonych, które nie muszą korzystać z funkcji łańcucha pakietów, bibliotekę NetX Duo można utworzyć za pomocą funkcji ***NX_DISABLE_PACKET_CHAIN** _, aby usunąć logikę łańcucha pakietów. Należy pamiętać, że funkcja fragmentacji i ponownego zestawu adresów IP może wymagać korzystania z funkcji pakietów łańcuchowych. Dlatego zdefiniowanie _*_NX_DISABLE_PACKET_CHAIN_*_ wymaga *_zdefiniowania NX_DISABLE_FRAGMENTATION_* _ NX_DISABLE_FRAGMENTATION *. 

Każda pula pamięci pakietów NetX Duo jest zasobem publicznym. NetX Duo nie stosuje żadnych ograniczeń co do sposobu, w jaki są używane pule pakietów. 

### <a name="packet-pool-memory-area"></a>Obszar pamięci puli pakietów

Obszar pamięci puli pakietów jest określony podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci dla obiektów ThreadX i NetX Duo, może ona być zlokalizowana w dowolnym miejscu w przestrzeni adresowej obiektu docelowego. 

Jest to ważna funkcja ze względu na dużą elastyczność zapewnianą aplikacji. Załóżmy na przykład, że produkt komunikacyjny ma obszar pamięci o dużej szybkości dla buforów sieciowych. Ten obszar pamięci można łatwo wykorzystać, tworząc go w puli pamięci pakietów NetX Duo.

### <a name="creating-packet-pools"></a>Tworzenie pul pakietów

Pule pakietów są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Nie ma żadnych ograniczeń liczby pul pamięci pakietów w aplikacji NetX Duo.

### <a name="dual-packet-pool"></a>Podwójna pula pakietów

Zazwyczaj rozmiar ładunku domyślnej puli pakietów IP jest wystarczająco duży, aby pomieścić rozmiar ramki aż do jednostki MTU interfejsu sieciowego. Podczas normalnego działania wątek ip musi wysyłać komunikaty, takie jak ARP, komunikaty sterowania TCP, komunikaty IGMP i komunikaty ICMPv6. Te komunikaty używają pakietów przydzielonych z domyślnej puli pakietów w wystąpieniu adresu IP. W systemie z ograniczeniami pamięci, w którym ilość pamięci dostępnej dla puli pakietów jest ograniczona, użycie pojedynczej puli pakietów (o dużym rozmiarze ładunku w celu dopasowania rozmiaru jednostki MTU) może nie być optymalnym rozwiązaniem. NetX Duo umożliwia aplikacji zainstalowanie puli pakietów pomocniczych, w której rozmiar ładunku jest mniejszy. Po zainstalowaniu puli pakietów pomocniczych wątek pomocnika IP przydziela pakiety z domyślnej puli pakietów lub puli pakietów pomocniczych w zależności od rozmiaru przesyłanych komunikatów. W przypadku puli pakietów pomocniczych rozmiar ładunku 200 bajtów będzie działać z większość komunikatów przesyłanych przez wątek pomocnika IP.

Domyślnie biblioteka NetX Duo jest łączona bez włączania podwójnej puli pakietów. Aby włączyć tę funkcję, skompilowaj bibliotekę z **definicją*** NX_DUAL_PACKET_POOL_ENABLE _. Następnie pulę pakietów pomocniczych można ustawić przez wywołanie funkcji _*_nx_ip_auxiliary_packet_pool_set_**.

Istnieje również możliwość utworzenia więcej niż jednej puli pakietów. Na przykład pula pakietów przesyłanych jest tworzona z optymalnym rozmiarem ładunku dla oczekiwanych rozmiarów komunikatów. Pula pakietów odbioru jest tworzona w sterowniku z rozmiarem ładunku ustawionym na jednostkę MTU sterownika, ponieważ nie można przewidzieć rozmiaru odebranych pakietów.

### <a name="packet-header-nx_packet"></a>Nagłówek NX_PACKET   
Domyślnie netX Duo umieszcza nagłówek pakietu bezpośrednio przed obszarem ładunku pakietu. Pula pamięci pakietów jest zasadniczo serią pakietów — nagłówków, po których natychmiast następuje ładunek pakietu. Nagłówek pakietu ***(NX_PACKET***) i układ puli pakietów zostały na rysunku 3.

W przypadku sterowników urządzeń sieciowych, które są w stanie wykonać zero operacji kopiowania, zazwyczaj adres początkowy obszaru ładunku pakietu jest zaprogramowany w logice DMA. Niektóre aparaty DMA mają wymaganie wyrównania w obszarze ładunku. Aby adres początkowy obszaru ładunku był prawidłowo wyrównany dla aparatu DMA lub operacji pamięci podręcznej, użytkownik może zdefiniować ***symbol*** NX_PACKET_ALIGNMENT .

> [!WARNING]
> *Ważne jest, aby sterownik sieciowy używał **funkcji nx_packet_transmit_release** po zakończeniu transmisji pakietu. Ta funkcja sprawdza, czy pakiet nie jest częścią kolejki wyjściowej TCP, zanim zostanie faktycznie umieszczony z powrotem w dostępnej puli.*

![Nagłówek pakietu i układ puli pakietów](./media/user-guide/image14.jpg)

**RYSUNEK 3. Nagłówek pakietu i układ puli pakietów**

Pola nagłówka pakietu są zdefiniowane w następujący sposób. Należy pamiętać, że ta tabela nie jest kompleksową listą wszystkich elementów członkowskich *NX_PACKET* struktury.

|Nagłówek pakietu | Przeznaczenie |
|---|---|
|***nx_packet_pool_owner***|To pole wskazuje pulę pakietów, która jest właścicielem tego konkretnego pakietu. Po zwolnieniu pakiet jest zwalniany do tej konkretnej puli. Mając własność puli wewnątrz każdego pakietu, datagram może obejmować wiele pakietów z wielu pul pakietów.|
|***nx_packet_next** _|To pole wskazuje następny pakiet w tej samej ramce. Jeśli wartość NULL, nie ma żadnych dodatkowych pakietów, które są częścią ramki. To pole jest również używane do przechowywania pofragmentowanych pakietów, dopóki cały pakiet nie zostanie ponownie skomplikowany. Jest on usuwany, jeśli zdefiniowano wartość _*_NX_DISABLE_PACKET_CHAIN_**.|
|***nx_packet_last** _|To pole wskazuje ostatni pakiet w ramach tego samego pakietu sieciowego. Jeśli wartość NULL, ten pakiet reprezentuje cały pakiet sieciowy. To pole jest usuwane, jeśli zdefiniowano wartość _*_NX_DISABLE_PACKET_CHAIN_**.|
|***nx_packet_length** _| To pole zawiera łączną liczbę bajtów w całym pakiecie sieciowym, w tym łączną liczbę wszystkich bajtów we wszystkich pakietach łańcuchowanych razem przez _nx_packet_next*członka.|
|***nx_packet_ip_interface***| To pole to blok sterowania interfejsem, który jest przypisywany do pakietu po jego otrzymaniu przez sterownik interfejsu i przez netX Duo w przypadku pakietów wychodzących. Blok sterowania interfejsem opisuje interfejs, np. adres sieciowy, adres MAC, adres IP i stan interfejsu, taki jak włączony link i wymagane mapowanie fizyczne.|
|***nx_packet_data_start** _| To pole wskazuje początek fizycznego obszaru ładunku tego pakietu. Nie musi być bezpośrednio po nagłówku NX_PACKET, ale jest to wartość domyślna dla usługi _ *_nx_packet_pool_create_**.|
|***nx_packet_data_end** _|To pole wskazuje na koniec obszaru ładunku fizycznego tego pakietu. Różnica między tym polem a polem _nx_packet_data_start* reprezentuje rozmiar ładunku.|
|***nx_packet_prepend_ptr** _|To pole wskazuje lokalizację, w której dane pakietu, nagłówek protokołu lub rzeczywiste dane, są dodawane przed istniejącymi danymi pakietu (jeśli są) w obszarze ładunku pakietu. Musi być większa niż lub równa lokalizacji wskaźnika _nx_packet_data_start* i mniejsza niż lub równa nx_packet_append_ptr *wskaźnika.*|
> [!CAUTION]
> *Ze względu na wydajność NetX Duo zakłada, że gdy pakiet jest przekazywany do usług NetX Duo w celu transmisji, dołączany wskaźnik wskazuje długi adres wyrównany wyrazem.*

| Nagłówek pakietu | Przeznaczenie |
|---|---|
|***nx_packet_append_ptr** _|To pole wskazuje koniec danych obecnie w obszarze ładunku pakietu. Musi znajdować się między lokalizacją pamięci wskazywaną przez _nx_packet_prepend_ptr* i *nx_packet_data_end.* Różnica między tym polem a *polem nx_packet_prepend_ptr* reprezentuje ilość danych w tym pakiecie.|
|***nx_packet_packet_pad** _|Te pola definiują długość wypełnienia w 4-bajtowych wyrazach, aby osiągnąć wymagane wyrównanie. To pole jest usuwane, _*_NX_PACKET_HEADER_PAD_*_ nie jest zdefiniowany. Alternatywnie _*_NX_PACKET_ALIGNMENT_*_ można użyć zamiast definiowania _nx_packet_header_pad.*|

### <a name="packet-header-offsets"></a>Przesunięcia nagłówka pakietów

Rozmiar nagłówka pakietu jest definiowany w celu umożliwienia wystarczającej ilości miejsca, aby pomieścić rozmiar nagłówka. Usługa ***nx_packet_allocate*** służy do przydzielania pakietu i dostosowuje wskaźnik w pakiecie zgodnie z określonym typem pakietu. Typ pakietu informuje netX Duo o przesuniętości wymaganej do wstawienia nagłówka protokołu (takiego jak UDP, TCP lub ICMP) przed danymi protokołu.

Następujące typy są zdefiniowane w programie NetX Duo, aby uwzględnić nagłówek IP i nagłówek warstwy fizycznej (Ethernet) w pakiecie. W drugim przypadku przyjmuje się, że jest to 16 bajtów, biorąc pod uwagę wymagane wyrównanie 4-bajtowe. Pakiety IPv4 są nadal zdefiniowane w programie NetX Duo, aby aplikacje przydzielały pakiety dla sieci IPv4. Pamiętaj, że jeśli biblioteka NetX Duo jest łączona z obsługą protokołu IPv6, typy pakietów ogólnych (takie jak NX_IP_PACKET) są mapowane na wersję IPv6. Jeśli biblioteka NetX Duo jest łączona bez włączonego protokołu IPv6, te typy pakietów ogólnych są mapowane na wersję IPv4.

W poniższej tabeli przedstawiono symbole zdefiniowane z włączonym protokółem IPv6:

|**Typ pakietu** |**Wartość** |
|---|---|
|NX_IPv6_PACKET (NX_IP_PACKET) | 0x38 |
|NX_UDPv6_PACKET (NX_UDP_PACKET) |0x40 |
|NX_TCPv6_PACKET (NX_TCP_PACKET) |0x4c |
|NX_IPv4_PACKET |0x24 |
|NX_IPv4_UDP_PACKET |0x2c |
|NX_IPv4_TCP_PACKET |0x38 |

W poniższej tabeli przedstawiono symbole zdefiniowane z wyłączonym protokółem IPv6:

|**Typ pakietu** |**Wartość** |
|---|---|
|NX_IPv4_PACKET (NX_IP_PACKET) |0x24 |
|NX_IPv4_UDP_PACKET (NX_UDP_PACKET) |0x2c |
|NX_IPv4_TCP_PACKET (NX_TCP_PACKET) |0x38 |

Należy pamiętać, że te wartości zostaną NX_IPSEC_ENABLE *zdefiniowane.* Aby uzyskać więcej informacji na temat aplikacji korzystających z protokołu IPsec, zobacz NetX Duo IPsec User Guide (Podręcznik użytkownika programu NetX Duo IPsec).

### <a name="pool-capacity"></a>Pojemność puli

Liczba pakietów w puli pakietów jest funkcją rozmiaru ładunku i całkowitej liczby bajtów w obszarze pamięci dostarczonym do usługi tworzenia puli pakietów. Pojemność puli jest obliczana przez podzielenie rozmiaru pakietu (w tym rozmiaru nagłówka NX_PACKET, rozmiaru ładunku i odpowiedniego wyrównania) na łączną liczbę bajtów w dostarczonym obszarze pamięci.

### <a name="payload-area-alignment"></a>Wyrównanie obszaru ładunku

Projekt puli pakietów w programie NetX Duo obsługuje kopiowanie zerowe. Na poziomie sterownika urządzenia sterownik może przypisać obszar ładunku bezpośrednio do deskryptorów buforu w celu odbierania danych. Czasami aparat DMA lub mechanizm synchronizacji pamięci podręcznej wymaga, aby adres początkowy obszaru ładunku miał określone wymaganie wyrównania. Można to osiągnąć, definiując wymagane wyrównanie (w bajtach) w ***NX_PACKET_ALIGNMENT***. Podczas tworzenia puli pakietów adres początkowy obszaru ładunku zostanie dopasowany do tej wartości. Domyślnie adres początkowy jest wyrównany o 4 bajty.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas oczekiwania na pakiet z pustej puli. Gdy pakiet jest zwracany do puli, zawieszony wątek jest nadaj temu pakietowi i wznawiany.

Jeśli wiele wątków jest zawieszonych w tej samej puli pakietów, zostały one wznowione w kolejności, w których zostały wstrzymane (FIFO).

### <a name="pool-statistics-and-errors"></a>Statystyki i błędy puli

Jeśli ta opcja jest włączona, oprogramowanie do zarządzania pakietami NetX Duo śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla pul pakietów są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba pakietów w puli
- Pakiety bezpłatne w puli
- Łączna alokacja pakietów
- Puste żądania alokacji puli
- Puste zawieszenie alokacji puli
- Nieprawidłowe wydania pakietów

Wszystkie te statystyki i raporty o błędach,**z** wyjątkiem łącznej i bezpłatnej liczby pakietów w puli, są wbudowane w bibliotekę NetX Duo, chyba że zdefiniowano NX_DISABLE_PACKET_INFO _ . Te dane są dostępne dla aplikacji za pomocą usługi _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>Blok sterowania pulą pakietów NX_PACKET_POOL

Charakterystyka każdej puli pamięci pakietów znajduje się w bloku sterowania. Zawiera on przydatne informacje, takie jak połączona lista pakietów bezpłatnych, liczba wolnych pakietów i rozmiar ładunku pakietów w tej puli. Ta struktura jest zdefiniowana w ***nx_api.h.***

Bloki sterowania puli pakietów mogą się znaleźć w dowolnym miejscu w pamięci, ale najczęściej kontrolka blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji.

## <a name="ipv4-protocol"></a>Protokół IPv4

Składnik protokołu internetowego (IP) firmy NetX Duo jest odpowiedzialny za wysyłanie i odbieranie pakietów IPv4 w Internecie. W netX Duo jest to składnik ostatecznie odpowiedzialny za wysyłanie i odbieranie komunikatów TCP, UDP, ICMP i IGMP przy użyciu podstawowego sterownika sieciowego.

NetX Duo obsługuje zarówno protokół IPv4 (RFC 791), jak i protokół IPv6 (RFC 2460). W tej sekcji omówiono protokół IPv4. Protokół IPv6 został omówiony w następnej sekcji.

### <a name="ipv4-addresses"></a>Adresy IPv4

Każdy host w Internecie ma unikatowy 32-bitowy identyfikator nazywany adresem IP. Istnieje pięć klas adresów IPv4 zgodnie z opisem na rysunku 4. Zakresy pięciu klas adresów IPv4 są następujące:

|Klasa|Zakres|
|---|---|
|A |Od 0.0.0.0 do 127.255.255.255|
|B |Od 128.0.0.0 do 191.255.255.255|
|C |Od 192.0.0.0 do 223.255.255.255|
|D |Od 224.0.0.0 do 239.255.255.255|
|E |Od 240.0.0.0 do 247.255.255.255|

![Diagram struktury adresów IPv4.](./media/user-guide/ipv4-address-structure.png)

### <a name="figure-4-ipv4-address-structure"></a>RYSUNEK 4. Struktura adresów IPv4

Istnieją również trzy typy specyfikacji *adresów:* emisji pojedynczej, *emisji* i *multiemisji*. Adresy emisji pojedynczej to te adresy IPv4, które identyfikują określonego hosta w Internecie. Adresy emisji pojedynczej mogą być źródłowym lub docelowym adresem IPv4. Adres emisji identyfikuje wszystkie hosty w określonej sieci lub podsieć i może być używany tylko jako adresy docelowe. Adresy rozgłasze są określane przez ustawienie części adresu z identyfikatorem hosta na jedynki. Adresy multiemisji (klasa D) określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączyć i opuścić w dowolnym momencie.

> [!IMPORTANT]
> *Tylko protokoły bez połączenia, takie jak UDP za pośrednictwem protokołu IPv4, mogą korzystać z emisji i ograniczonej możliwości emisji grupy multiemisji.*

> [!IMPORTANT]
> *Nazwa *IP_ADDRESS* jest zdefiniowana w ***nx_api.h** _. Umożliwia łatwą specyfikację adresów IPv4 przy użyciu przecinków zamiast kropek. Na przykład _IP_ADDRESS(128,0,0,0)* określa pierwszy adres klasy B pokazany na rysunku 4.*

### <a name="ipv4-gateway-address"></a>Adres bramy IPv4

Bramy sieci pomagają hostom w ich sieciach w przekazywaniu pakietów przeznaczonych do miejsc docelowych poza domeną lokalną. Każdy węzeł ma pewne informacje o tym, do którego następnego przeskoku należy wysłać, do miejsca docelowego jednego z jego sąsiadów lub za pośrednictwem wstępnie zaprogramowanego statycznej tabeli routingu. Jeśli jednak te podejścia nie powiodą się, węzeł powinien przekierowywał pakiet do bramy domyślnej, która ma lepszą wiedzę na temat sposobu przekierowywała pakiet do miejsca docelowego. Należy pamiętać, że brama domyślna musi być bezpośrednio dostępna za pośrednictwem jednego z interfejsów fizycznych dołączonych do wystąpienia adresu IP. Aplikacja wywołuje protokół ***nx_ip_gateway_address_set _,** aby skonfigurować domyślny adres bramy IPv4. Użyj usługi _*_nx_ip_gateway_address_get,_*_ aby pobrać bieżące ustawienia bramy IPv4. Aplikacja musi używać usługi _ *_nx_ip_gateway_address_clear_**, aby wyczyścić ustawienie bramy.

### <a name="ipv4-header"></a>Nagłówek IPv4

Aby dowolny pakiet IPv4 był wysyłany przez Internet, musi mieć nagłówek IPv4. Gdy protokoły wyższego poziomu (UDP, TCP, ICMP lub IGMP) wywołują składnik IP w celu wysłania pakietu, moduł przesyłania IPv4 umieszcza nagłówek IPv4 przed danymi. Z drugiej strony, gdy pakiety IP są odbierane z sieci, składnik IP usuwa nagłówek IPv4 z pakietu przed dostarczeniem do protokołów wyższego poziomu. Rysunek 5 przedstawia format nagłówka adresu IP.

![Format nagłówka IPv4](./media/user-guide/ipv4-header-format.png)

### <a name="figure-5-ipv4-header-format"></a>RYSUNEK 5. Format nagłówka IPv4

> [!IMPORTANT]
> *Wszystkie nagłówki w implementacji TCP/IP powinny być w **big endian** formacie. W tym formacie najbardziej znaczący bajt słowa znajduje się w najniższym adresie bajtowym. Na przykład wersja 4-bitowa i 4-bitowa długość nagłówka adresu IP muszą znajdować się w pierwszym bajtze nagłówka.*

Pola nagłówka IPv4 są zdefiniowane w następujący sposób:

|Pole nagłówka IPv4 &nbsp; &nbsp; |Przeznaczenie |
|---|---|
|***Wersja 4-bitowa*** |To pole zawiera wersję adresu IP, który reprezentuje ten nagłówek. W przypadku adresu IP w wersji 4, która obsługuje platformę NetX Duo, wartość tego pola wynosi 4. |
|***4-bitowa długość nagłówka*** |To pole określa liczbę 32-bitowych wyrazów w nagłówku adresu IP. Jeśli nie ma żadnych wyrazów opcji, wartość tego pola wynosi 5. |
|***8-bitowy typ usługi (TOS)*** |To pole określa typ usługi żądanej dla tego pakietu IP. Prawidłowe żądania są następujące:<br />- Normalne: 0x00 <br />- Minimalne opóźnienie: 0x00<br />- Maksymalna ilość danych: 0x08<br />— Maksymalna niezawodność: 0x04<br />— Koszt minimalny: 0x02 |
|***16-bitowa całkowita długość*** |To pole zawiera łączną długość datagramów adresów IP w bajtach, w tym nagłówek adresu IP. Datagram adresów IP to podstawowa jednostka informacji znalezionych w Internecie TCP/IP. Oprócz danych zawiera ona miejsce docelowe i adres źródłowy. Ponieważ jest to pole 16-bitowe, maksymalny rozmiar datagramu IP to 65 535 bajtów.|
|***16-bitowa identyfikacja*** |Pole to liczba używana do unikatowego identyfikowania każdego datagramu adresu IP wysyłanego z hosta. Ta liczba jest zwykle zwiększana po wysłaniu datagramu IP. Jest to szczególnie przydatne w przypadku składania odebranych fragmentów pakietów IP.|
|***Flagi 3-bitowe*** |To pole zawiera informacje o fragmentacji adresów IP. Bit 14 to bit "nie fragmentuj". Jeśli ten bit jest ustawiony, datagram wychodzącego adresu IP nie zostanie pofragmentowany. Bit 13 jest bitem "więcej fragmentów". Jeśli ten bit jest ustawiony, istnieje więcej fragmentów. Jeśli ten bit jest jasny, jest to ostatni fragment pakietu IP.|
|***Przesunięcie fragmentu 13-bitowego*** |To pole zawiera 13-bitowe górne przesunięcie fragmentu. W związku z tym przesunięcia fragmentów są dozwolone tylko w granicach 8-bajtowych. Pierwszy fragment fragmentu datagramu pofragmentowanych adresów IP będzie miał ustawiony bit "więcej fragmentów" z przesunięciem 0.|
|***8-bitowy czas wygaśnięcia (TTL)*** |To pole zawiera liczbę routerów, które może przekazać ten datagram, co zasadniczo ogranicza okres istnienia datagramu.|
|***Protokół 8-bitowy***|To pole określa, który protokół używa datagramu IP. Poniżej znajduje się lista prawidłowych protokołów i ich wartości:<br />- ICMP: 0x01 <br />- IGMP: 0x02<br />-TCP: 0X06<br />-UDP: 0X11 |
|***16-bitowa sumy kontrolnej*** |To pole zawiera 16-bitową sumy kontrolnej, która obejmuje tylko nagłówek IP. Istnieją dodatkowe sumy kontrolne w protokołach wyższego poziomu, które obejmują ładunek IP. |
|***32-bitowy źródłowy adres IP*** |To pole zawiera adres IP nadawcy i zawsze jest adresem hosta. |
|***32-bitowy docelowy adres IP*** |To pole zawiera adres IP odbiornika lub odbiorników, jeśli adres jest adresem emisji lub multiemisji. |

### <a name="creating-ip-instances"></a>Tworzenie wystąpień IP

Wystąpienia ip są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Początkowy adres IPv4, maska sieci, domyślna pula pakietów, sterownik nośnika oraz pamięć i priorytet wątku wewnętrznego adresu IP są definiowane przez usługę ***nx_ip_create,*** nawet jeśli aplikacja zamierza używać tylko sieci IPv6. Jeśli aplikacja inicjuje wystąpienie adresu IP z adresem IPv4 ustawionym na nieprawidłowy adres (0.0.0.0), zakłada się, że adres interfejsu zostanie później rozwiązany za pomocą konfiguracji ręcznej, za pośrednictwem protokołu RARP lub PROTOKOŁU DHCP lub podobnych protokołów.

W przypadku systemów z wieloma interfejsami sieciowymi interfejs podstawowy jest wyznaczany podczas wywoływania funkcji ***nx_ip_create** _. Każdy dodatkowy interfejs można dołączyć do tego samego wystąpienia adresu IP, wywołując element _*_nx_ip_interface_attach_**. Ta usługa przechowuje informacje o interfejsie sieciowym (takie jak adres IP, maska sieci) w bloku sterowania interfejsem i kojarzy wystąpienie sterownika z blokiem sterowania interfejsem w wystąpieniu adresu IP. Gdy sterownik odbiera pakiet danych, musi przechowywać informacje o interfejsie w strukturze NX_PACKET przed przekazywaniem ich do logiki odbierania adresów IP. Należy pamiętać, że wystąpienie adresu IP musi już zostać utworzone przed dołączenia jakichkolwiek interfejsów.

Usługi IPv6 nie są uruchomione po wywołaniu funkcji ***nx_ip_create** _. Aplikacje, które chcą korzystać z usług IPv6, muszą wywołać usługę _ *_nx_ipv6_enable_** w celu uruchomienia protokołu IPv6.

W sieci IPv6 każdy interfejs w wystąpieniu adresu IP może mieć wiele adresów globalnych IPv6. Oprócz używania protokołu DHCPv6 do przypisywania adresów IPv6 urządzenie może również używać automatycznej konfiguracji adresu bez stanowego. Więcej informacji można znaleźć w sekcjach "Blok sterowania IP" i "Rozwiązanie adresu IPv6" w dalszej części tego rozdziału.

### <a name="ip-send"></a>Wysyłanie adresu IP

Przetwarzanie wysyłania adresów IP w netx duo jest bardzo usprawnione. Dołączany wskaźnik w pakiecie jest przenoszony wstecz w celu uwzględnienia nagłówka IP. Nagłówek IP jest ukończony (ze wszystkimi opcjami określonymi przez warstwę protokołu wywołującego), sumy kontrolne IP są obliczane w wierszu (tylko dla pakietów IPv4), a pakiet jest wysyłany do skojarzonego sterownika sieciowego. Ponadto fragmentacja wychodząca jest również koordynowana z poziomu przetwarzania wysyłania adresów IP.

W przypadku protokołu IPv4 netX Duo inicjuje żądania ARP, jeśli jest wymagane fizyczne mapowanie docelowego adresu IP. Protokół IPv6 używa odnajdywania sąsiadów do mapowania adresów IPv6-adres-fizyczny.

> [!NOTE]
> *W przypadku łączności IPv4 pakiety wymagające rozpoznawania adresów IP (tj. mapowanie fizyczne) są kolejkowane w kolejce ARP, dopóki liczba pakietów w kolejce nie przekroczy głębokości kolejki ARP (zdefiniowanej przez **symbol** NX_ARP_MAX_QUEUE_DEPTH ). Jeśli zostanie osiągnięta głębokość kolejki, rozwiązanie NetX Duo usunie najstarszy pakiet z kolejki i będzie kontynuować oczekiwanie na rozwiązanie adresu dla pozostałych pakietów w kolejce. Z drugiej strony, jeśli wpis ARP nie zostanie rozpoznany, oczekujące pakiety we wpisie ARP są zwalniane po przechyłce czasu wpisu ARP.*

W przypadku systemów z wieloma interfejsami sieciowymi NetX Duo wybiera interfejs na podstawie docelowego adresu IP. Następująca procedura dotyczy procesu wyboru:

1. Jeśli nadawca określa interfejs wychodzący, a interfejs jest prawidłowy, użyj tego interfejsu.
2. Jeśli adres docelowy to emisja IPv4 lub multiemisja, używany jest pierwszy włączony interfejs fizyczny.
3. Jeśli adres docelowy znajduje się w tabeli routingu statycznego, używany jest interfejs skojarzony z bramą.
4. Jeśli miejsce docelowe jest w linku, używany jest interfejs on-link.
5. Jeśli adres docelowy jest adresem lokalnym linku (169.254.0.0/16), używany jest pierwszy prawidłowy interfejs.
6. Jeśli skonfigurowano bramę domyślną, użyj interfejsu skojarzonego z bramą domyślną, aby przesłać pakiet.
7. Na koniec, jeśli jeden z prawidłowych adresów IP interfejsu to adres link-lokalny (169.254.0.0/16), ten interfejs jest używany jako adres źródłowy do transmisji.
8. Pakiet wyjściowy jest porzucany, jeśli wszystkie powyższe nie powiedzie się.

### <a name="ip-receive"></a>Odbieranie adresu IP

Przetwarzanie odbierania adresów IP jest wywoływane ze sterownika sieciowego lub wewnętrznego wątku adresu IP (w przypadku przetwarzania pakietów w kolejce odroczonych odebranych pakietów). Przetwarzanie odbierania adresów IP sprawdza pole protokołu i próbuje wysłać pakiet do odpowiedniego składnika protokołu. Przed wysłaniem pakietu nagłówek IP jest usuwany przez przesuwanie wstępnie otwartego wskaźnika poza nagłówek IP.

Przetwarzanie odbierania adresów IP wykrywa również pofragmentowane pakiety IP i wykonuje niezbędne kroki w celu ich ponownego zbierania, jeśli włączono fragmentację. Jeśli fragmentacja jest potrzebna, ale nie jest włączona, pakiet jest porzucany.

NetX Duo określa odpowiedni interfejs sieciowy na podstawie interfejsu określonego w pakiecie. Jeśli interfejs pakietu ma wartość NULL, NetX Duo domyślnie jest interfejsem podstawowym. Ma to na celu zagwarantowanie zgodności ze starszymi sterownikami NetX Duo Ethernet.

### <a name="raw-ip-send"></a>Nieprzetworzone wysyłanie adresu IP

Nieprzetworzone pakiety IP to ramka ip zawierająca ładunek protokołu górnej warstwy, który nie jest bezpośrednio obsługiwany (i przetwarzany) przez NetX Duo. Pakiet pierwotny umożliwia deweloperom definiowanie własnych aplikacji opartych na adresach IP. Aplikacja może wysyłać nieprzetworzone pakiety IP bezpośrednio przy użyciu usługi ***nxd_ip_raw_packet_send** _, jeśli pierwotne przetwarzanie pakietów IP zostało włączone w _*_usłudze nx_ip_raw_packet_enabled_*_ ip. Podczas przesyłania pakietu emisji pojedynczej w sieci IPv6 rozwiązanie NetX Duo automatycznie określa najlepszy źródłowy adres IPv6 do użycia w celu wysyłania pakietów na podstawie adresu docelowego. Jeśli adres docelowy jest adresem multiemisji (lub emisji dla protokołu IPv4), netX Duo domyślnie będzie mieć pierwszy (podstawowy) interfejs. W związku z tym, aby wysyłać takie pakiety w interfejsach pomocniczych, aplikacja musi użyć usługi _ *_nx_ip_raw_packet_source_send_**, aby określić adres źródłowy do użycia dla pakietu wychodzącego.

### <a name="raw-ip-receive"></a>Nieprzetworzone odbieranie adresu IP

Jeśli przetwarzanie nieprzetworzonych pakietów IP jest włączone, aplikacja może odbierać nieprzetworzone pakiety IP za pośrednictwem usługi ***nx_ip_raw_packet_receive** _. Wszystkie pakiety przychodzące są przetwarzane zgodnie z protokołem określonym w nagłówku adresu IP. Jeśli protokół określa UDP, TCP, IGMP lub ICMP, NetX Duo będzie przetwarzać pakiet przy użyciu odpowiedniej procedury obsługi dla typu protokołu pakietu. Jeśli protokół nie jest jednym z tych protokołów i włączono nieprzetworzoną funkcję odbierania adresów IP, pakiet przychodzący zostanie umieszczany w kolejce pakietów pierwotnych oczekujących na otrzymanie go przez aplikację za pośrednictwem _*_usługi nx_ip_raw_packet_receive_**. Ponadto wątki aplikacji mogą zostać wstrzymane z opcjonalnym limitem czasu podczas oczekiwania na nieprzetworzonych pakietów IP. Liczba pakietów, które można dodać do kolejki pakietów pierwotnych, jest ograniczona. Wartość maksymalna jest zdefiniowana w ***NX_IP_RAW_MAX_QUEUE_DEPTH**_, której wartość domyślna to 20. Aplikacja może zmienić wartość maksymalną, wywołując usługę _ *_nx_ip_raw_receive_queue_max_set_**.

Alternatywnie bibliotekę NetX Duo można sbudowaną za pomocą **NX_ENABLE_IP_RAW_PACKET_FILTER*.** W tym trybie działania aplikacja udostępnia funkcję wywołania zwrotnego, która jest wywoływana za każdym razem, gdy zostanie odebrany pakiet z nieobsługiwanym typem protokołu. Logika odbierania adresu IP przekazuje pakiet do zdefiniowanej przez użytkownika procedury filtrowania odbierania nieprzetworzonych pakietów. Procedura filtrowania decyduje o tym, czy pakiet nieprzetworzonych ma być nadal w przyszłości. Wartość zwracana przez procedurę wywołania zwrotnego wskazuje, czy pakiet został przetworzony przez filtr odbierania nieprzetworzonych pakietów. Jeśli pakiet jest przetwarzany przez funkcję wywołania zwrotnego, pakiet powinien zostać zwolniony po zakończeniu pracy aplikacji z pakietem. W przeciwnym razie NetX Duo jest odpowiedzialny za wydanie pakietu. Zapoznaj się z **_nx_ip_raw_packet_filter_set,_** aby uzyskać więcej informacji na temat używania funkcji nieprzetworzonych filtrów pakietów.

> [!NOTE]
> *Funkcja otoki BSD dla netX Duo opiera się na funkcji nieprzetworzonych filtrów pakietów do obsługi nieprzetworzonych gniazd BSD. W związku z tym, aby zapewnić obsługę gniazda nieprzetworzonych w otoce BSD, biblioteka NetX Duo musi mieć zdefiniowaną wartość ***NX_ENABLE_IP_RAW_PACKET_FILTER** _, a aplikacja nie powinna używać biblioteki _*_nx_ip_raw_packet_filter_set do_*_ instalowania własnych nieprzetworzonych filtrów pakietów functions._

### <a name="default-packet-pool"></a>Domyślna pula pakietów

Każde wystąpienie adresu IP ma domyślną pulę pakietów podczas tworzenia. Ta pula pakietów służy do przydzielania pakietów dla protokołów ARP, RARP, ICMP, IGMP, różnych pakietów sterujących TCP (SYN, ACK itp.), odnajdywania sąsiadów, odnajdywania routerów i wykrywania zduplikowanych adresów. Jeśli domyślna pula pakietów jest pusta, gdy NetX Duo musi przydzielić pakiet, netx Duo może przerwać określoną operację i zwróci komunikat o błędzie, jeśli to możliwe.

### <a name="ip-helper-thread"></a>Wątek pomocnika IP

Każde wystąpienie adresu IP ma wątek pomocnika. Ten wątek jest odpowiedzialny za obsługę całego odroczonego przetwarzania pakietów i wszystkich okresowych przetwarzania. Wątek pomocnika IP jest tworzony w ***nx_ip_create.*** W tym miejscu wątek ma swój stos i priorytet. Należy pamiętać, że pierwsze przetwarzanie w wątku pomocnika IP to zakończenie inicjowania sterownika sieciowego skojarzonego z usługą tworzenia adresu IP. Po zakończeniu inicjowania sterownika sieciowego wątek pomocnika uruchamia nieskończoną pętlę do przetwarzania pakietów i okresowych żądań.

> [!IMPORTANT]
> *Jeśli w wątku pomocnika IP występuje nieeksjalne zachowanie, zwiększenie jego rozmiaru stosu podczas tworzenia adresu IP jest pierwszym krokiem debugowania. Jeśli stos jest zbyt mały, wątek pomocnika IP może powodować nadpisanie pamięci, co może powodować nietypowe problemy.*

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas próby odbierania nieprzetworzonych pakietów IP. Po otrzymaniu pakietu nieprzetworzony nowy pakiet jest nadany do pierwszego wstrzymanego wątku i ten wątek jest wznawiany. Wszystkie usługi NetX Duo do odbierania pakietów mają opcjonalny limit czasu zawieszenia. Po otrzymaniu pakietu lub upłynie limit czasu, wątek aplikacji zostanie wznowiony z odpowiednim stanem ukończenia.

### <a name="ip-statistics-and-errors"></a>Statystyki i błędy adresów IP

Jeśli ta opcja jest włączona, narzędzie NetX Duo śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia adresu IP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych pakietów IP
- Całkowita liczba wysłanych bajtów IP
- Łączna liczba odebranych pakietów IP
- Całkowita liczba odebranych bajtów IP
- Łączna liczba nieprawidłowych pakietów IP
- Łączna liczba porzucanych pakietów odbierania adresów IP
- Łączna liczba błędów sumy kontrolnej odbierania adresu IP
- Łączna liczba porzucanych pakietów wysyłania adresów IP
- Łączna liczba wysłanych fragmentów adresów IP
- Całkowita liczba odebranych fragmentów adresów IP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji za nx_ip_info_get ***usługi.***

### <a name="ip-control-block-nx_ip"></a>Blokuj kontrolę adresów IP NX_IP

Cechy poszczególnych wystąpień adresów IP znajdują się w bloku sterującym. Zawiera on przydatne informacje, takie jak adresy IP i maski sieci poszczególnych urządzeń sieciowych oraz tabela mapowania adresów IP sąsiadów i fizycznego adresu sprzętowego. Ta struktura jest zdefiniowana w ***nx_api.h _file.** Jeśli protokół IPv6 jest włączony, zawiera również tablicę adresów IPv6, których liczba jest określona przez konfigurowalna opcja użytkownika __*_ NX_MAX_IPV6_ADDRESSES **. Wartość domyślna umożliwia każdemu fizycznemu interfejsowi sieciowemu korzystanie z trzech adresów IPv6.

Bloki sterowania wystąpieniami adresów IP mogą być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

### <a name="static-ipv4-routing"></a>Statyczny routing IPv4

Funkcja routingu statycznego umożliwia aplikacji określenie sieci IPv4 i adresu następnego przeskoku dla określonych docelowych adresów IP sieci. Jeśli routing statyczny jest włączony, program NetX Duo przeszukuje statyczną tabelę routingu w poszukiwaniu wpisu pasującego do adresu docelowego pakietu do wysłania. Jeśli dopasowanie nie zostanie znalezione, program NetX Duo przeszukuje listę interfejsów fizycznych i wybiera źródłowy adres IP i adres następnego przeskoku na podstawie docelowego adresu IP i maski sieci. Jeśli miejsce docelowe nie pasuje do żadnego z adresów IP sterowników sieciowych dołączonych do wystąpienia adresu IP, NetX Duo wybierze interfejs, który jest bezpośrednio połączony z bramą domyślną i używa adresu IP interfejsu jako adresu źródłowego, a brama domyślna jako następnego przeskoku.

Wpisy można dodawać i usuwać z tabeli routingu statycznego przy użyciu odpowiednio usług ***nx_ip_static_route_add** _ i _ *_nx_ip_static_route_delete_**. Aby korzystać z routingu statycznego, aplikacja hosta musi włączyć tę funkcję, definiując ***NX_ENABLE_IP_STATIC_ROUTING.***

> [!NOTE]
> *Podczas dodawania wpisu do tabeli routingu statycznego usługa NetX Duo sprawdza, czy w tabeli nie ma pasującego wpisu dla określonego adresu docelowego. Jeśli istnieje, daje preferencję do wpisu z mniejszą siecią (dłuższy prefiks) w masce sieci.*

### <a name="ipv4-forwarding"></a>Przekazywanie IPv4

Jeśli przychodzący pakiet IPv4 nie jest przeznaczony dla tego węzła i funkcja przekazywania IPv4 jest włączona, NetX Duo próbuje przekazuje pakiet za pośrednictwem innych interfejsów.  

### <a name="ip-fragmentation"></a>Fragmentacja adresów IP

Urządzenie sieciowe może mieć ograniczenia dotyczące rozmiaru pakietów wychodzących. Ten limit jest nazywany maksymalną jednostką transmisji (MTU). MTU IP jest największy rozmiar ramki IP sterownik warstwy łącza jest w stanie przesłać bez fragmentacji pakietu IP. Podczas fazy inicjowania sterownika urządzenia moduł sterownika musi skonfigurować rozmiar jednostki MTU adresu IP za pośrednictwem usługi ***nx_ip_interface_mtu_set.***

Chociaż nie jest to zalecane, aplikacja może generować datagramy większe niż podstawowa liczba mtu adresów IP obsługiwana przez urządzenie. Przed przekazaniem takiego datagramu IP warstwa IP musi pofragmentować te pakiety. W przypadku odbierania pofragmentowanych ramek ADRESÓW IP na końcu odbierających muszą być przechowywane wszystkie pofragmentowane ramki ADRESÓW IP z tym samym identyfikatorem fragmentacji i ponownie je zesłać w porządek. Jeśli logika odbierania adresów IP nie może zebrać wszystkich fragmentów w celu przywrócenia oryginalnej ramki adresów IP w czasie, zostaną zwolnione wszystkie fragmenty. Wykrycie utraty pakietów i odzyskanie ich po nim należy do protokołu warstwy górnej.

Fragmentacja adresów IP dotyczy zarówno pakietów IPv4, jak i IPv6.

Aby zapewnić obsługę fragmentacji adresów IP i operacji ponownego zestawu, projektant systemu musi włączyć funkcję fragmentacji adresów IP w netx duo przy ***użyciu usługi nx_ip_fragment_enable*** service. Jeśli ta funkcja nie jest włączona, przychodzące pofragmentowane pakiety IP są odrzucane, a także pakiety, które przekraczają jednostkę MTU sterownika sieciowego.

> [!NOTE]
> *Logikę fragmentacji adresu IP można całkowicie usunąć, definiując ***NX_DISABLE_FRAGMENTATION** _ podczas budowania biblioteki NetX Duo. Dzięki temu można zmniejszyć rozmiar kodu netx duo. Należy pamiętać, że w takiej sytuacji funkcje fragmentacji/ponownego zsembly IPv4 i IPv6 są disabled._

> [!NOTE]
> *Jeśli **NX_DISABLE_CHAINED_PACKET,** fragmentacja adresów IP musi być wyłączona.*

> [!NOTE]
> *W sieci IPv6 routery nie fragmentacji datagramu, jeśli rozmiar datagramu przekracza jego minimalny rozmiar JEDNOSTKI MTU. W związku z tym urządzenie wysyłające musi określić minimalną jednostkę MTU między źródłem i miejscem docelowym oraz upewnić się, że rozmiar datagramu adresu IP nie przekracza ścieżki MTU. W netX Duo odnajdywanie jednostki MTU PATH IPv6 można włączyć, tworząc bibliotekę NetX Duo ze zdefiniowanym **NX_ENABLE_IPV6_PATH_MTU_DISCOVERY.***

## <a name="address-resolution-protocol-arp-in-ipv4"></a>Protokół ARP (Address Resolution Protocol) w protokole IPv4

Protokół rozpoznawania adresów (ARP) jest odpowiedzialny za dynamiczne mapowanie 32-bitowych adresów IPv4 na te z podstawowego nośnika fizycznego (RFC 826). Sieć Ethernet to najbardziej typowy nośnik fizyczny obsługujący adresy 48-bitowe. Potrzeba obsługi ARP jest określana przez sterownik sieciowy dostarczony do usługi ***nx_ip_create** _service. Jeśli wymagane jest fizyczne mapowanie, sterownik sieciowy musi użyć usługi _ *_nx_interface_address_mapping_needed_**, aby prawidłowo skonfigurować interfejs sterownika.

### <a name="arp-enable"></a>Włączanie ARP

Aby usługa ARP działała prawidłowo, musi najpierw zostać włączona przez aplikację przy użyciu ***nx_arp_enable*** usługi. Ta usługa konfiguruje różne struktury danych do przetwarzania ARP, w tym tworzenie obszaru pamięci podręcznej ARP z pamięci dostarczonej do usługi włączania ARP.

### <a name="arp-cache"></a>Pamięć podręczna ARP

Pamięć podręczną ARP można wyświetlić jako tablicę wewnętrznych struktur danych mapowania ARP. Każda struktura wewnętrzna jest w stanie utrzymać relację między adresem IP i fizycznym adresem sprzętowym. Ponadto każda struktura danych ma wskaźniki linków, dzięki czemu może być częścią wielu połączonych list.

Aplikacja może odszukać adres IP z pamięci podręcznej ARP, podając sprzętowy adres MAC przy użyciu usługi ***nx_arp_ip_address_find** _, jeśli mapowanie istnieje w tabeli ARP. Podobnie usługa _ *_nx_arp_hardware_address_find_** zwraca adres MAC dla danego adresu IP.

### <a name="arp-dynamic-entries"></a>Wpisy dynamiczne ARP

Domyślnie usługa włączania ARP umieszcza wszystkie wpisy w pamięci podręcznej ARP na liście dostępnych dynamicznych wpisów ARP. Po wykryciu żądania wysłania na niezamapowany adres IP dynamiczny wpis ARP jest przydzielany z tej listy przez firmę NetX Duo. Po alokacji jest ustawiany wpis ARP, a żądanie ARP jest wysyłane do nośnika fizycznego.

Wpis dynamiczny może również zostać utworzony przez ***usługę*** nx_arp_dynamic_entry_set .

> [!IMPORTANT]
> *Jeśli używane są wszystkie dynamiczne wpisy ARP, najsuchomiej używany wpis ARP jest zastępowany nowym mapowaniem.*

### <a name="arp-static-entries"></a>Wpisy statyczne ARP

Aplikacja może również skonfigurować statyczne mapowanie ARP przy użyciu **nx_arp_static_entry_create** _service. Ta usługa przydziela wpis ARP z dynamicznej listy wpisów ARP i umieszcza go na liście statycznej z informacjami mapowania dostarczonymi przez aplikację. Statyczne wpisy ARP nie mogą być ponownie używane ani starzejące się. Aplikacja może usunąć wpis statyczny przy użyciu usługi _*_nx_arp_static_entry_delete_*_. Aby usunąć wszystkie wpisy statyczne w tabeli ARP, aplikacja może użyć usługi __*_ nx_arp_static_entries_delete **.

### <a name="automatic-arp-entry"></a>Automatyczny wpis ARP

NetX Duo rejestruje mapowanie adresu IP/MAC elementu równorzędnego po odpowiedziach elementu równorzędnego na żądanie ARP. NetX Duo implementuje również funkcję automatycznego wpisu ARP, w której rejestruje mapowanie adresów IP/MAC elementu równorzędnego na podstawie niechcianych żądań ARP z sieci. Ta funkcja umożliwia wypełnianie tabeli ARP informacjami o elementach równorzędnych, co zmniejsza opóźnienie wymagane do przejść przez cykl żądania/odpowiedzi ARP. Jednak minusem włączenia automatycznego ARP jest to, że tabela ARP zwykle szybko wypełnia się w zajętej sieci z wieloma węzłami w linku lokalnym, co ostatecznie prowadzi do zastąpienia wpisu ARP.

Ta funkcja jest domyślnie włączona. Aby ją wyłączyć, biblioteka NetX Duo musi zostać skompilowana przy użyciu zdefiniowanego ***NX_DISABLE_ARP_AUTO_ENTRY.***</p>

### <a name="arp-messages"></a>Komunikaty ARP

Jak wspomniano wcześniej, komunikat żądania ARP jest wysyłany, gdy zadanie adresu IP wykryje, że mapowanie jest wymagane dla adresu IP. Żądania ARP są wysyłane okresowo (co ***NX_ARP_UPDATE_RATE** _sekundy) do momentu otrzymaniu odpowiedniej odpowiedzi ARP. Łączna liczba żądań *_NX_ARP_MAXIMUM_RETRIES_** ARP jest podjęto przed porzuconą próbą ARP. Po otrzymaniu odpowiedzi ARP skojarzone informacje o adresie fizycznym są przechowywane we wpisie ARP, który znajduje się w pamięci podręcznej.

W przypadku systemów wieloadresowych NetX Duo określa interfejs do wysyłania żądań i odpowiedzi ARP na podstawie określonego adresu docelowego.

> [!NOTE]
> *Wychodzące pakiety IP są kolejkowane, gdy NetX Duo czeka na odpowiedź ARP. Liczba wychodzących pakietów IP w kolejce jest definiowana przez stałą **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX Duo odpowiada również na żądania ARP z innych węzłów w lokalnej sieci IPv4. Gdy zostanie wykonane zewnętrzne żądanie ARP, które jest takie, które pasuje do bieżącego adresu IP interfejsu, który odbiera żądanie ARP, NetX Duo tworzy komunikat odpowiedzi ARP zawierający bieżący adres fizyczny.

Formaty żądań i odpowiedzi ARP sieci Ethernet przedstawiono na rysunku 6 i opisano je poniżej.

| **Pole &nbsp; żądania/odpowiedzi**         | **Cel**            |
| ---------------------------------- | ---------------------- |
| ***Adres docelowy sieci Ethernet*** | To 6-bajtowe pole zawiera adres docelowy odpowiedzi ARP i jest emisją (wszystkie jedynki) dla żądań ARP. To pole jest konfigurowany przez sterownik sieciowy. 
| ***Adres źródłowy sieci Ethernet***      | To 6-bajtowe pole zawiera adres nadawcy żądania lub odpowiedzi ARP i jest ono ustawiane przez sterownik sieciowy. |
| ***Typ ramki*** | To 2-bajtowe pole zawiera typ obecnej ramki Ethernet, a w przypadku żądań i odpowiedzi ARP jest to równe 0x0806. Jest to ostatnie pole, które sterownik sieciowy jest odpowiedzialny za konfigurowanie. |
| ***Typ sprzętu*** | To 2-bajtowe pole zawiera typ sprzętu, który jest 0x0001 dla sieci Ethernet. |
| ***Typ protokołu*** | To 2-bajtowe pole zawiera typ protokołu, który jest 0x0800 dla adresów IP. |
| ***Rozmiar sprzętu*** | To 1-bajtowe pole zawiera adres sprzętowy o rozmiarze 6 dla adresów Ethernet. |

![Diagram formatu pakietu ARP.](./media/user-guide/arp-packet-format.png)

**RYSUNEK 6. Format pakietu ARP**

| Pole &nbsp; żądania/odpowiedzi | Przeznaczenie |
|---|---|
| ***Rozmiar protokołu*** | To 1-bajtowe pole zawiera rozmiar adresu IP, czyli 4 dla adresów IP. |
| ***Kod operacji*** | To 2-bajtowe pole zawiera operację dla tego pakietu ARP. Żądanie ARP jest określane z wartością 0x0001, a odpowiedź ARP jest reprezentowana przez wartość 0x0002. |
| ***Adres Ethernet nadawcy*** | To 6-bajtowe pole zawiera adres Ethernet nadawcy. |
| ***Adres IP nadawcy*** | To 4-bajtowe pole zawiera adres IP nadawcy. |
| ***Docelowy adres Ethernet*** | To 6-bajtowe pole zawiera adres Ethernet obiektu docelowego. |
| ***Docelowy adres IP*** | To 4-bajtowe pole zawiera adres IP obiektu docelowego. |

> [!NOTE]
> *Żądania IRP i odpowiedzi są pakietami na poziomie sieci Ethernet. Wszystkie inne pakiety TCP/IP są hermetyzowane przez nagłówek pakietu IP.*

> [!NOTE]
> *Oczekuje się, że wszystkie komunikaty protokołu ARP w implementacji protokołu TCP/IP będą w **big endian** formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

### <a name="arp-aging"></a>Wiekowanie ARP

NetX obsługuje automatyczne dynamiczne unieważnienie wpisu ARP. ***NX_ARP_EXPIRATION_RATE** _ określa liczbę sekund, przez które ustanowione mapowanie adresu IP na fizyczne pozostaje prawidłowe. Po wygaśnięciu wpis ARP jest usuwany z pamięci podręcznej ARP. Przy następnej próbie wysłania na odpowiedni adres IP zostanie skierowane nowe żądanie ARP. Ustawienie wartości *__ NX_ARP_EXPIRATION_RATE_** na zero powoduje wyłączenie przedawniania się zasad ARP, co jest konfiguracją domyślną.

### <a name="arp-defend"></a>Obrona ARP

Gdy zostanie odebrane żądanie ARP lub pakiet odpowiedzi ARP, a nadawca ma ten sam adres IP, co powoduje konflikt z adresem IP tego węzła, NetX Duo wysyła żądanie ARP dla tego adresu jako ochronę. Jeśli pakiet ARP o konflikcie zostanie odebrany więcej niż raz w ciągu 10 sekund, NetX Duo nie wyśle więcej pakietów obronnych. Domyślny interwał 10 sekund może być ponownie definiowany przez ***** NX_ARP_DEFEND_INTERVAL _. To zachowanie jest zgodna z zasadami określonymi w 2.4(c) RFC5227. Ponieważ Windows XP ignoruje anons ARP jako odpowiedź dla sondy ARP, użytkownik może zdefiniować _ *_NX_ARP_DEFEND_BY_REPLY_**, aby wysłać odpowiedź ARP jako dodatkową opłatę.

### <a name="arp-statistics-and-errors"></a>Statystyki i błędy ARP

Jeśli ta opcja jest włączona, oprogramowanie NetX Duo ARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla przetwarzania protokołu ARP każdego adresu IP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych żądań ARP
- Łączna liczba odebranych żądań ARP
- Łączna liczba wysłanych odpowiedzi ARP 
- Łączna liczba odebranych odpowiedzi ARP 
- Łączna liczba wpisów dynamicznych ARP 
- Łączna liczba wpisów statycznych ARP 
- Łączna liczba wpisów Zwęgłego ARP 
- Łączna liczba nieprawidłowych komunikatów ARP 

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji w nx_arp_info_get ***usługi.***

## <a name="reverse-address-resolution-protocol-rarp-in-ipv4"></a>Protokół RARP (Reverse Address Resolution Protocol) w protokole IPv4

Protokół RARP (Reverse Address Resolution Protocol) to protokół żądający przypisania sieci dla 32-bitowych adresów IP hosta (RFC 903). Odbywa się to za pośrednictwem żądania RARP i jest okresowo kontynuowane, dopóki członek sieci nie przypisze adresu IP do interfejsu sieciowego hosta w odpowiedzi PROTOKOŁU RARP. Aplikacja tworzy wystąpienie adresu IP przez ***usługę*** nx_ip_create bez adresu IP. Jeśli protokół RARP jest włączony przez aplikację, może użyć protokołu RARP, aby zażądać adresu IP z serwera sieciowego dostępnego za pośrednictwem interfejsu, który ma zerowy adres IP.

### <a name="rarp-enable"></a>Włączanie rarp

Aby użyć protokołu RARP, aplikacja musi utworzyć wystąpienie ip o adresie IP o wartości 0, a następnie włączyć protokół RARP przy użyciu usługi ***nx_rarp_enable***. W przypadku systemów wieloadresowych co najmniej jedno urządzenie sieciowe skojarzone z wystąpieniem adresu IP musi mieć adres IP o wartości zero. Przetwarzanie RARP okresowo wysyła komunikaty żądań RARP dla systemu NetX Duo wymagające adresu IP, dopóki nie zostanie odebrana prawidłowa odpowiedź RARP z wyznaczonym adresem IP sieci. W tym momencie przetwarzanie RARP jest ukończone.

Po włączeniu funkcji RARP jest ona automatycznie wyłączana po rozpoznaniu wszystkich adresów interfejsu. Aplikacja może wymusić zakończenie obsługi rarp przy użyciu ***usługi*** nx_rarp_disable .

### <a name="rarp-request"></a>Żądanie RARP

Format pakietu żądania RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku [6.](#arp-messages) Jedyną różnicą jest to, że pole typu ramki 0x8035 a pole *Kod* operacji to 3, co oznacza żądanie RARP. Jak wspomniano wcześniej, żądania RARP będą wysyłane okresowo (co NX_RARP_UPDATE_RATE sekund), ***dopóki*** nie zostanie odebrana odpowiedź RARP z przypisanym przez sieć adresem IP.

> [!NOTE]
> *Wszystkie komunikaty RARP w implementacji TCP/IP powinny być w **big endian** formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

### <a name="rarp-reply"></a>Odpowiedź RARP

Komunikaty odpowiedzi RARP są odbierane z sieci i zawierają adres IP przypisany przez sieć dla tego hosta. Format pakietu odpowiedzi RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku 6. Jedyną różnicą jest to, że pole typu ramki jest 0x8035 a pole *Kod* operacji to 4, które wyznacza odpowiedź RARP. Po otrzymaniu adres IP jest konfigurny w wystąpieniu adresu IP, okresowe żądanie RARP jest wyłączone, a wystąpienie adresu IP jest teraz gotowe do normalnego działania sieci.

W przypadku hostów wieloadresowych adres IP jest stosowany do interfejsu sieciowego, który żąda. Jeśli inne interfejsy sieciowe nadal żądają przypisania adresu IP, okresowa usługa RARP będzie kontynuowana do momentu rozwiązania wszystkich żądań adresów IP interfejsu.

> [!NOTE]
> *Aplikacja nie powinna używać wystąpienia adresu IP, dopóki przetwarzanie RARP nie zostanie ukończone. Ta **nx_ip_status_check** może być używana przez aplikacje do oczekiwania na ukończenie procesu RARP. W przypadku systemów wieloadresowych aplikacja nie powinna używać interfejsu żądającego, dopóki przetwarzanie RARP nie zostanie ukończone w tym interfejsie. Stan adresu IP na urządzeniu pomocniczym można sprawdzić za pomocą **nx_ip_interface_status_check** pomocniczej.*

### <a name="rarp-statistics-and-errors"></a>Statystyki i błędy RARP

Jeśli ta opcja jest włączona, oprogramowanie NetX Duo RARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące statystyki i raporty o błędach są utrzymywane dla przetwarzania RARP każdego adresu IP:

- Łączna liczba wysłanych żądań RARP
- Łączna liczba odebranych odpowiedzi RARP
- Łączna liczba nieprawidłowych komunikatów RARP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji w nx_rarp_info_get ***service.***

## <a name="internet-control-message-protocol-icmp"></a>Protokół ICMP (Internet Control Message Protocol)

Protokół komunikatów sterowania Internetem dla protokołu IPv4 (ICMP) jest ograniczony do przekazywania informacji o błędach i kontroli między członkami sieci IP. Protokół komunikatów sterowania Internetem dla protokołu IPv6 (ICMPv6) obsługuje również informacje o błędach i kontroli i jest wymagany w przypadku protokołów rozpoznawania adresów, takich jak WYKRYWANIE zduplikowanych adresów i automatyczna konfiguracja adresów bez stanowych.

Podobnie jak w przypadku większości innych komunikatów warstwy aplikacji (np. TCP/IP), komunikaty ICMP i ICMPv6 są hermetyzowane przez nagłówek ip z oznaczeniem protokołu ICMP (lub ICMPv6).

### <a name="icmp-statistics-and-errors"></a>Statystyki i błędy ICMP

Jeśli ta opcja jest włączona, narzędzie NetX Duo śledzi kilka statystyk ICMP i błędów, które mogą być przydatne dla aplikacji. Dla przetwarzania protokołu ICMP poszczególnych adresów IP są utrzymywane następujące statystyki i raporty o błędach: 

- Łączna liczba wysłanych ping ICMP  
- Łączna liczba limitów czasu ping ICMP 
- Całkowita liczba wstrzymanych wątków ping ICMP 
- Łączna liczba odebranych odpowiedzi ping ICMP 
- Łączna liczba błędów sumy kontrolnej ICMP 
- Łączna liczba nieobsłużonych komunikatów ICMP 

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji za ***nx_icmp_info_get*** usługi.

## <a name="icmpv4-services-in-netx-duo"></a>Usługi ICMPv4 w NetX Duo

### <a name="icmpv4-enable"></a>Włączanie protokołu ICMPv4

Aby komunikaty ICMPv4 można było przetworzyć za pomocą netX Duo, aplikacja musi wywołać usługę ***nx_icmp_enable,*** aby umożliwić przetwarzanie protokołu ICMPv4. Po zakończeniu aplikacja może wysyłać żądania ping i pole przychodzących pakietów ping.  

### <a name="icmpv4-echo-request"></a>Żądanie echa ICMPv4

Żądanie echa jest jednym z typów komunikatów ICMPv4, który jest zwykle używany do sprawdzania istnienia określonego węzła w sieci, identyfikowane przez jego adres IP hosta. Popularne polecenie ping jest implementowane przy użyciu komunikatów żądania echa/odpowiedzi echa ICMP. Jeśli określony host jest obecny, jego stos sieciowy przetwarza żądanie ping i odpowiedzi z odpowiedzią ping. Rysunek 7 zawiera szczegóły dotyczące formatu komunikatu ping ICMPv4.

![Komunikat ping ICMPv4](./media/user-guide/icmpv4-ping-message.png)  

**RYSUNEK 7. Komunikat ping ICMPv4**

> [!NOTE]
> *Wszystkie komunikaty ICMPv4 w implementacji TCP/IP powinny być w **big endian** formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

Poniżej opisano format nagłówka ICMPv4:

|Pole nagłówka |Przeznaczenie |
|---|---|
|**Typ** |To pole określa komunikat ICMPv4 (bity 31–24). Najczęściej spotykane są:<br />-0: Odpowiedzi echa<br />- 3: Miejsce docelowe jest nieosiągalne<br />-8: żądanie echa<br />-11: Przekroczono czas<br />-12: Problem z parametrami |
|**Kod** |To pole jest kontekstem specyficznym dla pola typu (bity 23–16). W przypadku żądania echa lub odpowiedzi kod jest ustawiony na zero.|
|**Suma kontrolna** |To pole zawiera 16-bitową sumę kontrolną sumy uzupełniania komunikatu ICMPv4, w tym cały nagłówek ICMPv4 rozpoczynający się od pola Typ. Przed wygenerowaniem sumy kontrolnej pole sumy kontrolnej jest czyszowane.|
|**Identyfikacja** | To pole zawiera wartość identyfikatora identyfikującą hosta. Host powinien używać identyfikatora wyodrębnionego z żądania ECHO w odpowiedzi ECHA (bity 31–16).|
|**Numer sekwencyjny** |To pole zawiera wartość identyfikatora; Host powinien używać identyfikatora wyodrębnionego z żądania ECHO w odpowiedzi ECHA (bity 31–16). W przeciwieństwie do pola identyfikatora ta wartość zmieni się w kolejnym żądaniu echa z tego samego hosta (bity 15–0).|

### <a name="icmpv4-echo-response"></a>Odpowiedź echa ICMPv4    
Odpowiedź ping to inny typ komunikatu ICMP, który jest generowany wewnętrznie przez składnik ICMP w odpowiedzi na zewnętrzne żądanie ping. Oprócz potwierdzenia odpowiedź ping zawiera również kopię danych użytkownika podanych w żądaniu ping.

### <a name="icmpv4-error-messages"></a>Komunikaty o błędach ICMPv4   
W netX Duo są obsługiwane następujące komunikaty o błędach ICMPv4: 
- Miejsce docelowe jest nieosiągalne 
- Przekroczenie czasu 
- Problem z parametrami

## <a name="internet-group-management-protocol-igmp"></a>Protokół IGMP (Internet Group Management Protocol)

Protokół IGMP (Internet Group Management Protocol) udostępnia urządzenie do komunikowania się ze swoimi sąsiadami i routerami, które zamierza odbierać lub dołączać do grupy multiemisji IPv4 (RFC 1112 i RFC 2236). Grupa multiemisji jest zasadniczo dynamiczną kolekcją składowych sieci i jest reprezentowana przez adres IP klasy D. Członkowie grupy multiemisji mogą odejść w dowolnym momencie, a nowi członkowie mogą dołączyć w dowolnym momencie. Koordynacja biorąca udział w dołączaniu do grupy i opuszczaniu grupy jest odpowiedzialna za IGMP.

> [!NOTE]
> *Protokół IGMP jest przeznaczony tylko dla grup multiemisji IPv4. Nie można go używać w sieci IPv6.*

### <a name="igmp-enable"></a>Włączanie IGMP     
Zanim w NetX Duo będzie można wykonać jakiekolwiek działanie multiemisji, aplikacja musi wywołać nx_igmp_enable ***usługi.*** Ta usługa wykonuje podstawowe inicjowanie IGMP w ramach przygotowania do żądań multiemisji.

### <a name="multicast-ipv4-addressing"></a>Adresowanie IPv4 multiemisji  
Jak wspomniano wcześniej, adresy multiemisji są faktycznie adresami IP klasy D, jak pokazano na rysunku [4](#ipv4-addresses). Niższe 28-bitowe bity adresu klasy D odpowiadają identyfikatorowi grupy multiemisji. Istnieje szereg wstępnie zdefiniowanych adresów multiemisji. jednak wszystkie *hosty adres* (244.0.0.1) jest szczególnie ważne dla przetwarzania IGMP. Adres *wszystkich hostów jest* używany przez routery do wykonywania zapytań o wszystkie elementy członkowskie multiemisji w celu zgłoszenia, do których grup multiemisji należą.  

### <a name="physical-address-mapping-in-ipv4"></a>Mapowanie adresów fizycznych w protokole IPv4
Adresy multiemisji klasy D są mapowe bezpośrednio na fizyczne adresy Ethernet z zakresu od 01.00.5e.00.00.00 do 01.00.5e.7f.ff.ff. Niższe 23 bity adresu IP multiemisji mapować bezpośrednio do niższych 23 bitów adresu Ethernet.

### <a name="multicast-group-join"></a>Przyłączenie do grupy multiemisji
Aplikacje, które muszą dołączyć do określonej grupy multiemisji, mogą to zrobić, wywołując ***usługę nx_igmp_multicast_join*** multiemisji. Ta usługa śledzi liczbę żądań dołączenia do tej grupy multiemisji. Jeśli jest to pierwsze żądanie dołączenia aplikacji do grupy multiemisji, w sieci podstawowej zostanie wysłany raport IGMP wskazujący zamiar dołączenia tego hosta do grupy. Następnie sterownik sieciowy jest wywoływany w celu skonfigurowania nasłuchiwania pakietów z adresem Ethernet dla tej grupy multiemisji.

W systemie wieloadresowym, jeśli grupa multiemisji jest dostępna za pośrednictwem określonego interfejsu, aplikacja musi używać usługi ***nx_igmp_multicast_interface_join** _ zamiast _*_nx_igmp_multicast_join_**, która jest ograniczona do grup multiemisji w sieci podstawowej.

### <a name="multicast-group-leave"></a>Pozostawienie grupy multiemisji   
Aplikacje, które muszą opuścić wcześniej dołączone grupy multiemisji, mogą to zrobić, wywołując ***nx_igmp_multicast_leave*** multiemisji. Ta usługa zmniejsza liczbę wewnętrzną skojarzoną z tym, ile razy grupa została do niej dołączenia. Jeśli nie ma żadnych żądań zaległych sprzężenia dla grupy, sterownik sieciowy jest wywoływany, aby wyłączyć nasłuchiwanie pakietów przy użyciu adresu Ethernet tej grupy multiemisji.

### <a name="multicast-loopback"></a>Sprzężenia zwrotne multiemisji    
Aplikacja może chcieć odbierać ruch multiemisji pochodzący z jednego ze źródeł w tym samym węźle. Wymaga to, aby składnik multiemisji IP miał włączoną sprzężenia zwrotnego przy użyciu usługi ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>Komunikat raportu IGMP      
Gdy aplikacja dołącza do grupy multiemisji, za pośrednictwem sieci jest wysyłany komunikat raportu IGMP, aby wskazać zamiar dołączenia hosta do określonej grupy multiemisji. Format komunikatu raportu IGMP przedstawiono na rysunku 8. Adres grupy multiemisji jest używany zarówno dla komunikatu grupy w komunikacie raportu IGMP, jak i docelowego adresu IP.

Na powyższej ilustracji (Rysunek 8) nagłówek IGMP zawiera pole wersji/typu, maksymalną odpowiedź

![Diagram komunikatu raportu IGMP.](./media/user-guide/image17.jpg)

**RYSUNEK 8. Komunikat raportu IGMP**

czas, pole sumy kontrolnej i pole adresu grupy multiemisji. W przypadku komunikatów IGMPv1 pole Maksymalny czas odpowiedzi jest zawsze ustawione na zero, ponieważ nie jest to część protokołu IGMPv1. Wartość pola Maksymalny czas odpowiedzi jest ustawiana, gdy host odbiera komunikat IGMP typu zapytania i jest czyszczona, gdy host odbiera komunikat typu raportu innego hosta zgodnie z definicją protokołu IGMPv2.

Poniżej opisano format nagłówka IGMP:

|Pole nagłówka|Przeznaczenie|
|---|---|
|**Wersja** |To pole określa wersję IGMP (bity 31–28).|
|**Typ** |To pole określa typ komunikatu IGMP (bity 27–24).|
|**Maksymalny czas odpowiedzi** |Nie jest używany w przypadku IGMP v1. W przypadku IGMP v2 to pole służy jako maksymalny czas odpowiedzi.|
|**Suma kontrolna** |To pole zawiera 16-bitową sumę kontrolną sumy dopełnień komunikatu IGMP, począwszy od wersji IGMP (bity 0–15)|
|**Adres grupy** |32-bitowy adres IP grupy D klasy D|

Komunikaty raportów IGMP są również wysyłane w odpowiedzi na komunikaty zapytań IGMP wysyłane przez router multiemisji. Routery multiemisji okresowo wysyłają komunikaty zapytania, aby zobaczyć, które hosty nadal wymagają członkostwa w grupie. Komunikaty zapytań mają taki sam format jak komunikat raportu IGMP pokazany na rysunku 8. Jedyną różnicą jest to, że typ IGMP jest równy 1, a pole adresu grupy ma wartość 0. Komunikaty zapytania IGMP są wysyłane do adresu IP *wszystkich hostów* przez router multiemisji. Host, który nadal chce zachować członkostwo w grupie, odpowiada przez wysłanie kolejnego komunikatu raportu IGMP.

> [!NOTE]
> *Wszystkie komunikaty w implementacji TCP/IP powinny być w **big endian** formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

### <a name="igmp-statistics-and-errors"></a>Statystyki i błędy IGMP    
<th><p>Jeśli ta opcja jest włączona, oprogramowanie NetX Duo IGMP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla przetwarzania protokołu IGMP każdego adresu IP są utrzymywane następujące statystyki i raporty o błędach: 

- Łączna liczba wysłanych raportów IGMP 
- Łączna liczba odebranych zapytań IGMP 
- Łączna liczba błędów sumy kontrolnej IGMP 
- Całkowita liczba przyłączone bieżących grup IGMP 

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji w ***nx_igmp_info_get*** service. 

### <a name="multicast-without-igmp"></a>Multiemisja bez IGMP  
Aplikacja, która oczekuje ruchu IPv4 w trybie multiemisji, może dołączyć adres grupy multiemisji bez wywołania komunikatów IGMP przy użyciu usługi ***nx_ipv4_multicast_interface_join***. Ta usługa powoduje, że warstwa IPv4 i źródłowy sterownik interfejsu akceptują pakiety z wyznaczonego adresu multiemisji IPv4. Nie ma jednak żadnych komunikatów zarządzania grupą IGMP wysyłanych ani przetwarzanych dla tej grupy.

Aplikacja nie chce już odbierać ruchu z grupy, może używać usługi ***nx_ipv4_multicast_interface_leave.***

## <a name="ipv6-in-netx-duo"></a>Protokół IPv6 w netx duo

### <a name="ipv6-addresses"></a>Adresy IPv6   
Adresy IPv6 mają 128 bitów. Architektura adresu IPv6 jest opisana w dokumencie RFC 4291. Adres jest podzielony na prefiks zawierający najbardziej znaczące bity i adres hosta zawierający niższe bity. Prefiks wskazuje typ adresu i jest w przybliżeniu odpowiednikiem adresu sieciowego w sieci IPv4.

Protokół IPv6 ma trzy typy specyfikacji adresów: emisji pojedynczej, emisji dowolnej (nie jest obsługiwane w NetX Duo) i multiemisji. Adresy emisji pojedynczej to te adresy IP, które identyfikują określonego hosta w Internecie. Adresy emisji pojedynczej mogą być źródłowym lub docelowym adresem IP. Adresy multiemisji określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączyć i opuścić w dowolnym momencie.

Protokół IPv6 nie ma odpowiednika mechanizmu emisji IPv4. Możliwość wysyłania pakietów do wszystkich hostów można osiągnąć, wysyłając pakiet do grupy multiemisji link-local wszystkie hosty.

Protokół IPv6 wykorzystuje adresy multiemisji do wykonywania procedur odnajdywania sąsiadów, odnajdywania routerów i automatycznej konfiguracji adresów bez stanowych.

Istnieją dwa typy adresów emisji pojedynczej IPv6: adresy lokalne łączy, zwykle konstruowane przez połączenie dobrze znanego prefiksu lokalnego linku z adresem MAC interfejsu i globalnych adresów IP, które również mają część prefiksu i część identyfikatora hosta. Adres globalny można skonfigurować ręcznie lub za pomocą automatycznej konfiguracji adresu bez stanowego lub protokołu DHCPv6. NetX Duo obsługuje zarówno adres lokalny linku, jak i adres globalny.

Aby obsłużyć formaty IPv4 i IPv6, netX Duo udostępnia nowy typ danych, NXD_ADDRESS, do przechowywania adresów IPv4 i IPv6. Poniżej przedstawiono definicję tej struktury. Pole adresu jest uniią adresów IPv4 i IPv6.

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

W strukturze NXD_ADDRESS pierwszy element, *nxd_ip_version*, wskazuje wersję protokołu IPv4 lub IPv6. Obsługiwane wartości to NX_IP_VERSION_V4 lub NX_IP_VERSION_V6. *nxd_ip_version* wskazuje, które pole w unii *nxd_ip_address* ma być adres IP. Usługi interfejsu API NetX Duo zazwyczaj zawierają wskaźnik NXD_ADDRESS jako argument wejściowy zamiast adresu IP ULONG (32-bitowego).

### <a name="link-local-addresses"></a>Łączenie adresów lokalnych     
Adres link-local jest prawidłowy tylko w sieci lokalnej. Urządzenie może wysyłać i odbierać pakiety do innego urządzenia w tej samej sieci po przypisaniu prawidłowego adresu lokalnego linku. Aplikacja przypisuje adres link-local, wywołując usługę NetX Duo nxd_ipv6_address_set ***,*** z parametrem długości prefiksu ustawionym na 10. Aplikacja może podać adres link-local do usługi lub po prostu użyć adresu NX_NULL jako adresu link-local i zezwolić platformie NetX Duo na konstruowanie adresu link-local na podstawie adresu MAC urządzenia.

W poniższym przykładzie nakaże platformie NetX Duo skonfigurowanie adresu link-local z prefiksem o długości 10 na urządzeniu podstawowym (indeks 0) przy użyciu jego adresu MAC:

```c
nxd_ipv6_address_set(ip_ptr, 0, NX_NULL, 10, NX_NULL);
```
W powyższym przykładzie, jeśli adres MAC interfejsu to 54:32:10:1A:BC:67, odpowiednim adresem link-local będzie:

```c
FE80::5632:10FF:FE1A:BC67
```
Należy pamiętać, że część identyfikatora hosta adresu IPv6 (**5632:10FF:FE1A:BC67**) składa się z 6-bajtowego adresu MAC z następującymi zmianami:

- **0xFFFE** wstawiony między bajtem 3 i bajtem 4 adresu MAC
- Drugi najniższy bit pierwszego bajtu adresu MAC (bit U/L) jest ustawiony na 1

Zobacz RFC 2464 (Transmission of IPv6 Packets over Ethernet Network) (Transmisja pakietów IPv6 za pośrednictwem sieci Ethernet), aby uzyskać więcej informacji na temat sposobu konstruowania części adresu IPv6 hosta na podstawie adresu MAC interfejsu.

Istnieje kilka specjalnych adresów multiemisji do wysyłania komunikatów multiemisji do jednego lub większej liczby hostów w protokole IPv6:

| Group (Grupa)  | Adres   | Opis  |
|---|---|---|
|Grupa Wszystkie węzły |**FF02::1** |Wszystkie hosty w sieci lokalnej|
|Wszystkie grupy routerów |**FF02::2** |Wszystkie routery w sieci lokalnej|
|Węzeł na żądanie |**FF02::1:FF00:0/104** |Objaśniono poniżej|

Adres multiemisji na żądanie węzła dotyczy określonych hostów w linku lokalnym, a nie wszystkich hostów IPv6. Składa się z **prefiksu FF02::1:FF00:0/104,** który jest 104 bitami i ostatnich 24-bitowych docelowego adresu IPv6. Na przykład adres IPv6 **205B:209D:D028::F058:D1C8:1024** ma adres multiemisji na żądanie o adresie **FF02::1:FFC8:1024.**

> [!IMPORTANT]
> *Notacja z podwójnym dwukropkiem wskazuje, że bity interweniujące są zerami. **FF02::1:FF00:0/104*** w pełni rozwinięte wygląda jak **FF02:0000:0000:0000:0000:0001:FF00:0000**

### <a name="global-addresses"></a>Adresy globalne    
Przykład globalnego adresu IPv6 to **2001:0123:4567:89AB:CDEF::1** Adres IPv6 w strukturze NXD_ADDRESS NetX Duo. W poniższym przykładzie zmienna NXD_ADDRESS, **global_ipv6_address** zawiera adres IPv6 emisji pojedynczej. W poniższym przykładzie pokazano urządzenie NetX Duo tworzące określony globalny adres IPv6 dla swojego urządzenia podstawowego:

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
Należy pamiętać, że prefiks tego adresu IPv6 to **2001:0123:4567:89AB,** który ma długość 64 bitów i jest wspólną długością prefiksu dla globalnych adresów IPv6 emisji pojedynczej w sieci Ethernet.

Struktura NXD_ADDRESS zawiera również adresy IPv4. Adres IP **192.1.168.10** **(0xC001A80A**) przechowywany w układzie global_ipv4_address ma następujący układ pamięci:

|Pole |Wartość |
|---|---|
|global_ipv4_address.nxd_ip_version |NX_IP_VERSION_V4|
|global_ipv4_address.nxd_ip_address.v4 |0xC001A80A|

Gdy aplikacja przekazuje adres do usług NetX Duo, pole nxd_ip_version musi określać poprawną wersję adresu IP dla prawidłowej obsługi pakietów. 

Aby mieć zgodność z poprzednimi wersjami istniejących aplikacji NetX, aplikacja NetX Duo obsługuje wszystkie usługi NetX. Wewnętrznie NetX Duo konwertuje typ adresu IPv4 ULONG na typ danych NXD_ADDRESS przed przekazywaniem go do rzeczywistej usługi NetX Duo.

Poniższy przykład ilustruje podobieństwo i różnice między usługami w netx i NetX Duo.

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

Poniżej przedstawiono równoważny interfejs API NetX:

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
> *Zachęcamy deweloperów aplikacji do korzystania z wersji nxd tych interfejsów API.*

### <a name="ipv6-default-routers"></a>Domyślne routery IPv6    
Protokół IPv6 używa domyślnego routera do przekazywania pakietów do miejsc docelowych odłączyć. Usługa NetX Duo ***nxd_ipv6_default_router_add*** aplikacji na dodanie routera IPv6 do domyślnej tabeli routerów. Zobacz Rozdział 4 "Opis usług", aby uzyskać więcej domyślnych usług routerów oferowanych przez netX Duo.  

Podczas przekazywania pakietów IPv6 program NetX Duo najpierw sprawdza, czy miejsce docelowe pakietu jest w linku. Jeśli nie, NetX Duo sprawdza domyślną tabelę routingu, czy router jest prawidłowy, aby przekierować pakiet poza połączenie.  

Aby usunąć router z tabeli domyślnego routera IPv6, aplikacja musi używać usługi ***nxd_ipv6_default_router_delete** _. Aby uzyskać wpisy tabeli routera domyślnego IPv6, użyj usługi __*_ nxd_ipv6_default_router_entry_get **.

### <a name="ipv6-header"></a>Nagłówek IPv6    
Nagłówek IPv6 został zmodyfikowany z nagłówka IPv4. Podczas przydzielania pakietu wywołujący określa protokół aplikacji (np. UDP, TCP), rozmiar buforu w bajtach i limit przeskoków.   

Rysunek 9 przedstawia format nagłówka IPv6, a tabela zawiera listę składników nagłówka.

![Diagram formatu nagłówka IPv6.](./media/user-guide/image18.png)

**RYSUNEK 9. Format nagłówka IPv6**

|Nagłówek adresu IP | Przeznaczenie |
|---|---|
|Wersja |Pole 4-bitowe dla wersji adresu IP. W przypadku sieci IPv6 wartość w tym polu musi być taka jak 6; W przypadku sieci IPv4 musi to być 4.|
|Klasa ruchu |8-bitowe pole, w których są przechowywane informacje o klasie ruchu. To pole nie jest używane przez netx duo.|
|Flow Etykiety |Pole 20-bitowe do unikatowego identyfikowania przepływu, jeśli istnieje, z który jest skojarzony pakiet. Wartość zero wskazuje, że pakiet nie należy do określonego przepływu. To pole zastępuje pole *TOS w* protokole IPv4.|
|Długość ładunku |Pole 16-bitowe wskazujące ilość danych w bajtach pakietu IPv6 po nagłówku bazowym IPv6. Obejmuje to wszystkie hermetyzowany nagłówek protokołu i dane.|
|Następny nagłówek | Pole 8-bitowe wskazujące typ nagłówka rozszerzenia, który następuje po nagłówku bazowym IPv6. To pole zastępuje pole *Protokół* w protokole IPv4.|
|Limit przeskoku |Pole 8-bitowe, które ogranicza liczbę routerów, przez które pakiet może przejść. To pole zastępuje pole *TTL* w protokole IPv4.|
|Adres źródłowy |Pole 128-bitowe, w których jest przechowywane adres IPv6 nadawcy.|
|Adres docelowy |Pole 128-bitowe, które zawiera adres IPv6 miejsca docelowego.|

### <a name="enabling-ipv6-in-netx-duo"></a>Włączanie protokołu IPv6 w netx duo    
Domyślnie protokół IPv6 jest włączony w programie NetX Duo. Usługi IPv6 są włączone w programie NetX Duo, jeśli konfigurowalna opcja ***NX_DISABLE_IPV6** _ w _nx_user.h* nie jest zdefiniowana. Jeśli ***NX_DISABLE_IPV6,*** NetX Duo będzie oferować tylko usługi IPv4, a wszystkie moduły i usługi związane z IPv6 nie są wbudowane w bibliotekę NetX Duo.

Dla aplikacji jest dostarczana następująca usługa do konfigurowania adresu IPv6 ***urządzenia:*** nxd_ipv6_address_set

Oprócz ręcznego ustawiania adresów IPv6 urządzenia system może również używać automatycznej konfiguracji adresu bez stanowego. Aby użyć tej opcji, aplikacja musi wywołać wywołanie ***nxd_ipv6_enable** _, aby uruchomić usługi IPv6 na urządzeniu. Ponadto usługi ICMPv6 muszą zostać uruchomione przez wywołanie usługi _*_nxd_icmp_enable, co_*_ umożliwia netx Duo wykonywanie usług, takich jak nakierowanie routera, odnajdywanie sąsiadów i wykrywanie zduplikowanych adresów. Należy _*_pamiętać, nx_icmp_enable_*_ uruchamia tylko protokół ICMP dla usług IPv4. _*_nxd_icmp_enable_*_ uruchamia usługi ICMP zarówno dla protokołu IPv4, jak i IPv6. Jeśli system nie potrzebuje usług ICMPv6, można użyć protokołu *__nx_icmp_enable_**, aby moduł ICMPv6 nie został połączony z systemem.

W poniższym przykładzie przedstawiono typową procedurę inicjowania protokołu IPv6 w programie NetX Duo.

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

Protokoły górnej warstwy (takie jak TCP i UDP) można włączyć przed lub po włączeniu protokołu IPv6.

> [!IMPORTANT]  
> *Usługi IPv6 są dostępne tylko po zainicjowaniu wątku ip i włączeniu urządzenia.*

Po włączeniu interfejsu (tj. sterownik urządzenia interfejsu jest gotowy do wysyłania i odbierania danych oraz uzyskano prawidłowy adres lokalny linku), urządzenie może uzyskać globalne adresy IPv6 za pomocą jednej z tych metod:

- Automatyczna konfiguracja adresu bez stanowego;  
- Ręczna konfiguracja adresu IPv6;  
- Konfiguracja adresu za pośrednictwem protokołu DHCPv6 (z opcjonalnym pakietem DHCPv6)

Pierwsze dwie metody zostały opisane poniżej. Metoda 3. (DHCPv6) jest opisana w pakiecie DHCP.

### <a name="stateless-address-autoconfiguration-using-router-solicitation"></a>Automatyczna konfiguracja adresu bez stanowego przy użyciu nakierowania routera      
Urządzenia NetX Duo mogą automatycznie konfigurować swoje interfejsy, gdy są połączone z siecią IPv6 przy użyciu routera, który dostarcza informacje o prefiksach. Urządzenia, które wymagają automatycznej konfiguracji adresu bez stanowego, wysyłają komunikaty na żądanie routera (RS, Stateless Address Autoconfiguration). Routery w sieci odpowiadają za pomocą komunikatów ra (ANONS) routerów na żądanie. Komunikaty ra anonsują prefiksy identyfikujące adresy sieciowe skojarzone z linkiem. Następnie urządzenia generują unikatowy identyfikator sieci, do która jest dołączone. Adres jest tworzymy przez połączenie prefiksu i jego unikatowego identyfikatora. W ten sposób po otrzymaniu komunikatów ra hosty generują swój adres IP. Routery mogą również wysyłać okresowe niechciane komunikaty ra. 

> [!WARNING]
> NetX Duo umożliwia aplikacji włączanie lub wyłączanie automatycznej konfiguracji adresów bez *stanowych w czasie uruchamiania. Aby włączyć tę funkcję, biblioteka NetX Duo musi zostać skompilowana przy **użyciu NX_IPV6_STATELESS_AUTOCONFIG_CONTROL** zdefiniowanej. Po włączeniu tej funkcji aplikacje  mogą używać* funkcji nxd_ipv6_stateless_address_autoconfigure_enable i nxd_ipv6_stateless_address_autocofigure_disable do włączania lub wyłączania automatycznej konfiguracji bez stanu adresu IPv6.

### <a name="manual-ipv6-address-configuration"></a>Ręczna konfiguracja adresu IPv6     
Jeśli jest wymagany określony adres IPv6,  aplikacja może użyć nxd_ipv6_address_set do ręcznego skonfigurowania adresu IPv6. Interfejs sieciowy może mieć wiele adresów IPv6. Należy jednak pamiętać, że łączna liczba adresów IPv6 w systemie uzyskana za pośrednictwem automatycznej konfiguracji adresu bez stanowego lub przy użyciu konfiguracji ręcznej nie może przekroczyć ***NX_MAX_IPV6_ADDRESSES***.

W poniższym przykładzie pokazano, jak ręcznie skonfigurować adres globalny w interfejsie podstawowym (urządzenie 0) w ip_0:

```c
NXD_ADDRESS global_address;
global_address.nxd_ip_version = NX_IP_VERSION_V6;
global_address.nxd_ip_address.v6[0] = 0x20010000;
global_address.nxd_ip_address.v6[1] = 0x00000000;
global_address.nxd_ip_address.v6[2] = 0x00000000;
global_address.nxd_ip_address.v6[3] = 0x0000ABCD;
```

Następnie host wywołuje następującą usługę NetX Duo, aby przypisać ten adres jako globalny adres IP:

```c
status = nxd_ipv6_address_set(&ip_0, 0,  
                              &global_address, 64
                              NX_NULL);
```

### <a name="duplicate-address-detection-dad"></a>Wykrywanie zduplikowanych adresów    
Gdy system skonfiguruje swój adres IPv6, adres zostanie oznaczony jako *NATYWNE*. Jeśli jest włączona funkcja wykrywania zduplikowanych adresów ,opisana w dokumencie RFC 4862, netx Duo automatycznie wysyła komunikaty na żądanie sąsiada (NS) z tym adresem wstępnym jako miejscem docelowym. Jeśli żadne hosty w sieci nie odpowiadają na te komunikaty NS w danym okresie, zakłada się, że adres jest unikatowy w linku lokalnym, a jego stan jest przenoszony do prawidłowego stanu. W tym momencie aplikacja może zacząć używać tego adresu IP do komunikacji.  

Funkcja NFC jest częścią modułu ICMPv6. W związku z tym aplikacja musi włączyć usługi ICMPv6, zanim nowo skonfigurowany adres będzie można przejść przez proces THE. Alternatywnie proces THE można wyłączyć, definiując opcję ***NX_DISABLE_IPV6_DAD** _ w środowisku kompilacji biblioteki NetX Duo (zdefiniowanym jako _*_nx_user.h)._*_ Podczas procesu THE _*_parametr NX_IPV6_DAD_TRANSMITS_*_ określa liczbę komunikatów NS wysyłanych przez netX Duo bez odbierania odpowiedzi w celu określenia, czy adres jest unikatowy. Domyślnie i zalecane przez RFC 4862 wartość *__ NX_IPV6_DAD_TRANSMITS_** jest ustawiona na 3. Ustawienie tego symbolu na zero skutecznie wyłącza FUNKCJĘ DOSTĘPNĄ.

Jeśli protokół ICMPv6 lub FUNKCJA DOSTĘPNA nie są włączone w czasie, gdy aplikacja przypisze adres IPv6, nie zostanie wykonana funkcja PROC, a netX Duo natychmiast ustawia stan adresu IPv6 na PRAWIDŁOWY.

NetX Duo nie może komunikować się w sieci IPv6, dopóki jego lokalny i/lub globalny adres linku nie będzie prawidłowy. Po pozyskaniu prawidłowego adresu NetX Duo próbuje dopasować adres docelowy pakietu przychodzącego do jednego ze skonfigurowanych adresów IPv6 lub włączonego adresu multiemisji. Jeśli nie zostaną znalezione żadne dopasowania, pakiet zostanie porzucony. 

> [!WARNING]  
> *W trakcie procesu JEDNOSTKI SS liczba przesyłanych pakietów NS jest definiowana przez wartość ***NX_IPV6_DAD_TRANSMITS**, która domyślnie wynosi 3, a między każdym komunikatem NS JEST wysyłane jednosek sekundowe _opóźnienie._ W związku z tym w systemie z włączoną łączona funkcja OCHRONY przed prawidłowym adresem IP i gotowością do komunikacji po przypisaniu adresu IPv6 (przy założeniu, że nie jest to zduplikowany adres) opóźnienie wynosi około 3 sekund.

Aplikacje mogą chcieć otrzymywać powiadomienia, gdy adresy IPv6 w systemie zostaną zmienione. Aby włączyć funkcję powiadamiania o zmianie adresu IPv6, należy sbudowaną bibliotekę NetX Duo z **NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY.** Po włączeniu tej funkcji aplikacje mogą instalować funkcję wywołania zwrotnego przy użyciu **_nxd_ipv6_address_change_notify_** usługi.

Gdy adres IPv6 zostanie zmieniony lub stanie się nieprawidłowy, wywoływana jest funkcja wywołania zwrotnego dostarczona przez użytkownika z następującymi informacjami:

| Funkcja  | Opis  |
|---|---|
|ip_ptr |Wskaźnik do wystąpienia adresu IP|
|interface_index |Indeksowanie interfejsu sieciowego, z który jest skojarzony ten adres IPv6
|ipv6_addr_index |Indeksowanie tabeli adresów IPv6|
|ipv6_address |Wskaźnik do adresu IPv6 w postaci tablicy czterech liczb całkowitych ULONG. Adresy Pv6 są prezentowane w kolejności bajtów hosta.|

### <a name="ipv6-multicast-support-in-netx-duo"></a>Obsługa multiemisji protokołu IPv6 w netx duo      
Adresy multiemisji określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączyć i opuścić w dowolnym momencie. NetX Duo implementuje kilka protokołów ICMPv6, w tym wykrywanie zduplikowanych adresów, odnajdywanie sąsiadów i odnajdywanie routerów, które wymagają funkcji multiemisji adresów IP. W związku z tym NetX Duo oczekuje, że podstawowy sterownik urządzenia będzie obsługiwać operacje multiemisji.

Gdy NetX Duo musi dołączyć lub opuścić grupę multiemisji  (taką jak adres multiemisji dla wszystkich węzłów i adres multiemisji na żądanie węzła), wydaje sterownikowi urządzenia polecenie dołączania lub pozostawiania adresu MAC multiemisji. Sterownik polecenie do przyłączenia adresu multiemisji jest ***NX_LINK_MULTICAST_JOIN** _. Aby pozostawić adres multiemisji, netX Duo wydaje polecenie sterownika _*_NX_LINK_MULTICAST_LEAVE_**. Sterownik urządzenia musi zaimplementować te dwa polecenia, aby protokoły ICMPv6 działały prawidłowo.

Aplikacje mogą dołączać do grupy multiemisji IPv6 przy użyciu usługi ***nxd_ipv6_multicast_interface_join*.** Ta usługa rejestruje adres multiemisji ze stosem IP, a następnie powiadamia określonego sterownika urządzenia o adresie multiemisji IPv6. Aby opuścić grupę multiemisji, aplikacje używają usługi ***nxd_ipv6_multicast_interface_leave.***

### <a name="neighbor-discovery-nd"></a>Odnajdywanie sąsiadów (ND)    
Odnajdywanie sąsiadów to protokół w sieciach IPv6 do mapowania adresów fizycznych na adresy IPv6 (adres globalny lub adres lokalny linku). To mapowanie jest zachowywane w pamięci podręcznej odnajdywania sąsiadów (ND Cache). Proces ND jest odpowiednikiem procesu ARP w protokole IPv4, a pamięć podręczna ND jest podobna do tabeli ARP. Węzeł IPv6 może uzyskać adres MAC sąsiada przy użyciu protokołu odnajdywania sąsiadów (ND). Wysyła on komunikat na żądanie sąsiada (NS) na adres multiemisji dla wszystkich węzłów na żądanie i czeka na odpowiedni komunikat anonsu sąsiada (NA). Adres MAC uzyskany w ramach tego procesu jest przechowywany w pamięci podręcznej ND Cache.

Każde wystąpienie adresu IP ma jedną pamięć podręczną ND. Pamięć podręczna ND jest zachowywana jako tablica wpisów. Rozmiar tablicy jest definiowany w czasie kompilacji przez ustawienie opcji ***NX_IPV6_NEIGHBOR_CACHE_SIZE** _which w _*_nx_user.h_**. Należy pamiętać, że wszystkie interfejsy dołączone do wystąpienia adresu IP współdzielą tę samą pamięć podręczną ND.

Cała pamięć podręczna ND Cache jest pusta podczas uruchamiania aplikacji NetX Duo. W przypadku systemu NetX Duo automatycznie aktualizuje pamięć podręczną ND, dodając i usuwając wpisy zgodnie z protokołem ND. Jednak aplikacja może również zaktualizować pamięć podręczną ND, ręcznie dodając i usuwając wpisy pamięci podręcznej przy użyciu następujących usług NetX Duo:

- ***nxd_nd_cache_entry_delete***  
- ***nxd_nd_cache_entry_set***   
- ***nxd_nd_cache_invalidate***

Podczas wysyłania i odbierania pakietów IPv6 program NetX Duo automatycznie aktualizuje tabelę ND Cache.

## <a name="internet-control-message-protocol-in-ipv6-icmpv6"></a>Protokół komunikatów sterowania Internetem w protokole IPv6 (ICMPv6)  

Rola protokołu ICMPv6 w protokole IPv6 została znacznie rozszerzona o obsługę mapowania adresów IPv6 i odnajdywania routerów. Ponadto protokół ICMPv6 netX Duo obsługuje żądania echa i odpowiedzi, raporty o błędach ICMPv6 i komunikaty przekierowania ICMPv6.

### <a name="icmpv6-enable"></a>Włączanie protokołu ICMPv6    
Przed przetworzeniem komunikatów ICMPv6 przez aplikację NetX Duo aplikacja musi wywołać usługę ***nxd_icmp_enable,*** aby włączyć przetwarzanie ICMPv6, jak wyjaśniono wcześniej. 

### <a name="icmpv6-messages"></a>Komunikaty ICMPv6     
Struktura nagłówka ICMPv6 jest podobna do struktury nagłówka ICMPv4. Jak pokazano poniżej, podstawowy nagłówek ICMPv6 zawiera trzy pola, typ, kod i sumy kontrolne oraz zmienną długość danych opcji ICMPv6. 

![Diagram przedstawiający podstawowy nagłówek ICMPv6.](./media/user-guide/image19.png)

**RYSUNEK 10. Podstawowy nagłówek ICMPv6**

|Pole |Rozmiar (w bajtach) |Opis |
|-----|-----|-----|
|     | 1   |Identyfikuje typ komunikatu ICMPv6; |
|     |     |1 Miejsce docelowe jest nieosiągalne |
|     |     |2 Pakiety są zbyt duże |
|     |     |3 Przekroczono czas |
|     |     |4. Problem z parametrami |
|     |     |128 Echo Request |
|     |     |129 Echo Reply |
|     |     |133 Router Solicitation |
|     |     |Anons routera 134 |
|     |     |135 Neighbor Solicitation (Żądanie sąsiada 135) |
|     |     |136 Neighbor Advertisement (Anons sąsiada 136) |
|     |     |Komunikat przekierowania 137 |
|Kod | 1   |Dodatkowo kwalifikuje typ komunikatu ICMPv6. Zwykle używane z komunikatami o błędach. Jeśli nie jest używany, jest ustawiona na zero. Komunikaty żądania echa/odpowiedzi i NS nie używają go.|
|Suma kontrolna | 2 |16-bitowe pole sumy kontrolnej dla nagłówka ICMP. Jest to 16-bitowe uzupełnienie całego komunikatu ICMPv6, w tym nagłówka ICMPv6. Zawiera również pseudo nagłówka adresu źródłowego IPv6, adres docelowy i długość ładunku pakietu. |

Poniżej przedstawiono przykładowy nagłówek żądanie sąsiada.

![Diagram przykładowego nagłówka żądanie sąsiada.](./media/user-guide/image20.jpg)

**RYSUNEK 11. Nagłówek ICMPv6 dla komunikatu na żądanie sąsiada**

|Pole |Rozmiar (w bajtach) |Opis |
|-----|-----|-----|
|Typ | 1   |Identyfikuje typ komunikatu ICMPv6 dla komunikatów na żądanie sąsiada. Wartość to 135. |
|Kod | 1   |Nie używany. Ustaw wartość 0. |
|Suma kontrolna | 2  |16-bitowe pole sumy kontrolnej dla nagłówka ICMPv6. |
|Zarezerwowany | 4  |4 bajty zarezerwowane ustawione na 0. |
|Adres docelowy | 16  |Adres IPv6 obiektu docelowego na żądanie. W przypadku rozpoznawania adresów IPv6 jest to rzeczywisty adres IP emisji pojedynczej urządzenia, którego adres warstwy łącza musi zostać rozpoznany. |
|Opcje | Zmienna |Opcjonalne informacje określone przez protokół odnajdywania sąsiadów. |

### <a name="icmpv6-ping-request"></a>Żądanie ping ICMPv6
W aplikacjach NetX Duo nxd_icmp_ping wysyłać żądania ping IPv6 lub IPv4 na podstawie docelowego adresu IP określonego w parametrach.   

### <a name="icmpv6-ping-response"></a>Odpowiedź ping ICMPv6
Odpowiedź ping ICMPv6 to inny typ komunikatu ICMPv6, który jest generowany wewnętrznie przez składnik ICMPv6 w odpowiedzi na zewnętrzne żądanie ping ICMPv6. Oprócz potwierdzenia odpowiedź ping ICMPv6 zawiera również kopię danych użytkownika podanych w żądaniu ping ICMPv6.  

### <a name="thread-suspension"></a>Zawieszenie wątku
Wątki aplikacji mogą zostać wstrzymane podczas próby ping do innego członka sieci. Po otrzymaniu odpowiedzi ping komunikat odpowiedzi ping jest wyświetlany dla pierwszego wątku wstrzymanego i ten wątek jest wznawiany. Podobnie jak w przypadku wszystkich usług NetX Duo, wstrzymanie żądania ping ma opcjonalny limit czasu.  

### <a name="other-icmpv6-messages"></a>Inne komunikaty ICMPv6
Komunikaty ICMPv6 są wymagane dla następujących funkcji:  

- Odnajdywanie sąsiadów  
- Automatyczna konfiguracja adresu bez stanowego 
- Odnajdywanie routerów 
- Wykrywanie nieosiągalności sąsiadów  

### <a name="neighbor-unreachability-router-and-prefix-discovery"></a>Nieosiągalność sąsiadów, router i odnajdywanie prefiksów    
Wykrywanie nieosiągalności sąsiadów, odnajdywanie routerów i odnajdywanie prefiksów jest oparte na protokole odnajdywania sąsiadów i opisano je poniżej. 

***Wykrywanie nieosiągalności sąsiadów:*** Urządzenie IPv6 wyszukuje w pamięci podręcznej odnajdywania sąsiadów docelowy adres warstwy łącza, gdy chce wysłać pakiet. Bezpośrednie miejsce docelowe, czasami określane jako "następny przeskok", może być rzeczywistym miejscem docelowym w tym samym linku lub routerem, jeśli miejsce docelowe jest poza łączem. Wpis pamięci podręcznej ND zawiera stan osiągalności sąsiada.

Stan OSIĄGALNY wskazuje, że sąsiad jest uznawany za osiągalny. Sąsiad jest osiągalny, jeśli niedawno otrzymał potwierdzenie, że odebrano pakiety wysyłane do sąsiada. Potwierdzenie w NetX Duo ma postać otrzymania komunikatu NA od sąsiada w odpowiedzi na komunikat NS wysłany przez urządzenie NetX Duo. NetX Duo zmieni również stan sąsiada na OSIĄGALNY, jeśli aplikacja wywoła usługę NetX Duo ***nxd_nd_cache_entry_set*** ręczne wprowadzenie rekordu pamięci podręcznej.

***Odnajdywanie routerów:*** Urządzenie IPv6 używa routera do przekazywania wszystkich pakietów przeznaczonych dla lokalizacji docelowych poza łączami. Może również używać informacji wysyłanych przez router, takich jak komunikaty anonsu routera (RA), aby skonfigurować jego globalne adresy IPv6.

Urządzenie w sieci może zainicjować proces odnajdywania routera, wysyłając komunikat na żądanie routera (RS) na adres multiemisji wszystkich routerów (FF01::2). Może też czekać na adres multiemisji dla wszystkich węzłów (FF::1) dla okresowego ra z routerów.

Komunikat ra zawiera informacje prefiksu do konfigurowania adresu IPv6 dla tej sieci. W programie NetX Duo żądanie routera jest domyślnie włączone i można je wyłączyć, ustawiając opcję konfiguracji ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ in _*_nx_user.h_**. Zobacz opcje konfiguracji w rozdziale "Instalacja i używanie netX Duo", aby uzyskać więcej informacji na temat ustawiania parametrów pozyskiwania routerów. 

***Odnajdywanie prefiksów:*** urządzenie IPv6 używa odnajdywania prefiksów, aby dowiedzieć się, które hosty docelowe są dostępne bezpośrednio bez przechodzinia przez router. Te informacje są udostępniane urządzeniu IPv6 z komunikatów ra z routera. Urządzenie IPv6 przechowuje informacje o prefiksach w tabeli prefiksów. Odnajdywanie prefiksów jest zgodne z prefiksem z tabeli prefiksów urządzeń IPv6 do adresu docelowego. Prefiks pasuje do adresu docelowego, jeśli wszystkie bity w prefiksie pasują do najbardziej znaczących bitów adresu docelowego. Jeśli adres obejmuje więcej niż jeden prefiks, wybierany jest najdłuższy prefiks.

### <a name="icmpv6-error-messages"></a>Komunikaty o błędach ICMPv6    
W netX Duo są obsługiwane następujące komunikaty o błędach ICMPv6:  

- Miejsce docelowe jest nieosiągalne  
- Zbyt duży pakiet  
- Przekroczenie czasu  
- Problem z parametrami  

## <a name="user-datagram-protocol-udp"></a>Protokół UDP (User Datagram Protocol)

Protokół UDP (User Datagram Protocol) zapewnia najprostszą formę transferu danych między członkami sieci (RFC 768). Pakiety danych UDP są wysyłane z jednego członka sieci do innego w najlepszy sposób; tj. nie ma wbudowanego mechanizmu potwierdzania przez adresata pakietu. Ponadto wysłanie pakietu UDP nie wymaga wcześniejszego nawiązanego połączenia. W związku z tym transmisja pakietów UDP jest bardzo wydajna.

W przypadku deweloperów migrowania aplikacji NetX do aplikacji NetX Duo istnieje tylko kilka podstawowych zmian funkcjonalności protokołu UDP między platformami NetX i NetX Duo. Wynika to z tego, że protokół IPv6 dotyczy głównie podstawowej warstwy adresów IP. Wszystkie usługi NetX Duo UDP mogą być używane do łączności IPv4 lub IPv6.

### <a name="udp-header"></a>Nagłówek UDP       
Rozwiązanie UDP umieszcza prosty nagłówek pakietu przed danymi aplikacji podczas transmisji i usuwa podobny nagłówek UDP z pakietu w odbiorze przed dostarczeniem odebranego pakietu UDP do aplikacji. Protokół UDP wykorzystuje protokół IP do wysyłania i odbierania pakietów, co oznacza, że przed nagłówkiem UDP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 12 przedstawia format nagłówka UDP.

![Diagram formatu nagłówka UDP.](./media/user-guide/image21.png)

### <a name="figure-12-udp-header"></a>RYSUNEK 12. Nagłówek UDP

> [!NOTE]
> *Wszystkie nagłówki w implementacji protokołu UDP/IP powinny być w **big endian** formacie. W tym formacie najbardziej znaczący bajt słowa znajduje się w najniższym adresie bajtowym.*

Poniżej opisano format nagłówka UDP:

|Pole nagłówka |Przeznaczenie |
|---|---|
|**16-bitowy numer portu źródłowego** |To pole zawiera port, z którego jest wysyłany pakiet UDP. Prawidłowe porty UDP mają zakres od 1 do 0xFFFF. |
|**16-bitowy numer portu docelowego** |To pole zawiera port UDP, do którego jest wysyłany pakiet. Prawidłowe porty UDP mają zakres od 1 do 0xFFFF. |
|**16-bitowa długość protokołu UDP** |To pole zawiera liczbę bajtów w pakiecie UDP, w tym rozmiar nagłówka UDP. |
|**16-bitowa sumy kontrolne UDP** |To pole zawiera 16-bitową sumy kontrolnej dla pakietu, w tym nagłówek UDP, obszar danych pakietu i nagłówek pseudo-IP. |

### <a name="udp-enable"></a>Włączanie protokołu UDP   
Aby możliwe było przesyłanie pakietów UDP, aplikacja musi najpierw włączyć funkcję UDP przez wywołanie ***nx_udp_enable*** usługi. Po włączeniu aplikacja może wysyłać i odbierać pakiety UDP.  

### <a name="udp-socket-create"></a>Tworzenie gniazda UDP    
Gniazda UDP są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Początkowy typ usługi, czas eksploatacji i głębokość kolejki odbierania są definiowane przez nx_udp_socket_create ***usługi.*** Nie ma żadnych ograniczeń liczby gniazd UDP w aplikacji.

### <a name="udp-checksum"></a>Sumy kontrolne UDP   
Protokół IPv6 wymaga obliczenia sumy kontrolnej nagłówka UDP na danych pakietu, natomiast w protokole IPv4 jest to opcjonalne.  

Protokół UDP określa 16-bitową podsumę kontrolną dopełnianą przez użytkownika, która obejmuje nagłówek pseudowłaściwego adresu IP (składający się ze źródłowego adresu IP, docelowego adresu IP i słowa adresu IP protokołu/długości), nagłówka UDP i danych pakietów UDP. Jedyną różnicą między sumy kontrolne nagłówka pakietów IPv4 i IPv6 UDP jest to, że źródłowe i docelowe adresy IP są 32-bitowe w protokole IPv4, a w protokole IPv6 są 128-bitowe. Jeśli obliczona wartość sumy kontrolnej UDP wynosi 0, jest ona przechowywana jako wszystkie (0xFFFF). Jeśli gniazdo wysyłające ma wyłączono logikę sumy kontrolnej UDP, zero jest umieszczane w polu sumy kontrolnej UDP, aby wskazać, że nie obliczono sumy kontrolnej.

Jeśli sumy kontrolne UDP nie są zgodne z obliczoną sumy kontrolnej przez odbiornik, pakiet UDP jest po prostu odrzucany.

W sieci IPv4 sumy kontrolne UDP jest opcjonalne. NetX Duo umożliwia aplikacji włączanie lub wyłączanie obliczeń sumy kontrolnej UDP na gniazdo. Domyślnie logika sumy kontrolnej gniazda UDP jest włączona. Aplikacja może wyłączyć logikę sumy kontrolnej dla określonego gniazda UDP przez wywołanie ***nx_udp_socket_checksum_disable** _service. Jednak w sieci IPv6 sumy kontrolne UDP jest obowiązkowe. W związku z tym usługa _ *_nx_udp_socket_checksum_disable_** nie wyłączy logiki sumy kontrolnej UDP podczas wysyłania pakietu za pośrednictwem sieci IPv6.

Niektóre kontrolery Ethernet są w stanie wygenerować sumy kontrolne UDP na bieżąco. Jeśli system może używać funkcji obliczania sumy kontrolnej sprzętu, bibliotekę NetX Duo można utworzyć bez logiki sumy kontrolnej. Aby wyłączyć sumy kontrolne oprogramowania UDP, biblioteka NetX Duo musi być budowaną z następującymi zdefiniowanymi symbolami: ***NX_DISABLE_UDP_TX_CHECKSUM** _ _*_i NX_DISABLE_UDP_RX_CHECKSUM_*_ (opisane w rozdziale 2). Opcje konfiguracji całkowicie usuwają logikę sumy kontrolnej UDP z programu NetX Duo, a wywołanie usługi *__nx_udp_socket_checksum_disable_** umożliwia aplikacji wyłączenie przetwarzania sumy kontrolnej UDP protokołu IPv4 dla każdego gniazda.

### <a name="udp-ports-and-binding"></a>Porty I powiązanie UDP      
Port UDP to logiczny punkt końcowy w protokole UDP. W składniku UDP netX Duo znajduje się 65 535 prawidłowych portów, od 1 do 0xFFFF. Aby wysyłać lub odbierać dane UDP, aplikacja musi najpierw utworzyć gniazdo UDP, a następnie powiązać je z żądanym portem. Po powiązaniu gniazda UDP z portem aplikacja może wysyłać i odbierać dane na tym gnieździe.

### <a name="udp-fast-pathtrade"></a>Szybka ścieżka protokołu UDP&trade;   
Szybka ścieżka UDP to nazwa ścieżki o małym narzucie &trade; pakietów za pośrednictwem implementacji NetX Duo UDP. Wysłanie pakietu UDP wymaga tylko kilku wywołań funkcji: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_, i eventual call do sterownika sieciowego. _*_nx_udp_socket_send_*_ jest dostępna w programie NetX Duo dla istniejących aplikacji NetX i ma zastosowanie tylko do pakietów IPv4. Preferowaną metodą jest jednak użycie usługi *__nxd_udp_socket_send_** omówionej poniżej. W przypadku odbierania pakietów UDP pakiet UDP jest umieszczany w odpowiedniej kolejce odbierania gniazda UDP lub dostarczany do zawieszonego wątku aplikacji w jednym wywołaniu funkcji z przetwarzania przerwań odbioru sterownika sieciowego. Ta wysoce zoptymalizowana logika wysyłania i odbierania pakietów UDP jest istotą technologii szybka ścieżka UDP.  

### <a name="udp-packet-send"></a>Wysyłanie pakietów UDP    
Wysyłanie danych UDP za pośrednictwem sieci IPv6 lub IPv4 można łatwo wykonać, wywołując funkcję ***nxd_udp_socket_send** _. Obiekt wywołujący musi ustawić wersję adresu IP w _nx_ip_version* parametru NXD_ADDRESS wskaźnika. NetX Duo określi najlepszy adres źródłowy dla przesyłanych pakietów UDP na podstawie docelowego adresu IPv4/IPv6. Ta usługa umieszcza nagłówek UDP przed danymi pakietu i wysyła go do sieci przy użyciu wewnętrznej procedury wysyłania adresów IP. Wysyłanie pakietów UDP nie jest wstrzymane, ponieważ wszystkie transmisje pakietów UDP są przetwarzane natychmiast. 

W przypadku miejsc docelowych multiemisji lub emisji aplikacja powinna określić źródłowy adres IP do użycia, jeśli urządzenie NetX Duo ma wiele adresów IP do wyboru. Można to zrobić za pomocą usługi ***nxd_udp_socket_source_send.***

> [!IMPORTANT]    
> *Jeśli **nx_udp_socket_send** jest używany do* przesyłania pakietów multiemisji lub emisji, adres IP pierwszego włączonego interfejsu jest używany jako adres źródłowy .

> [!NOTE] 
> Jeśli dla tego gniazda jest włączona logika sumy kontrolnej UDP, operacja sumy kontrolnej jest wykonywana w kontekście wątku wywołującego, bez blokowania dostępu do struktur danych *UDP lub IP.* 

> [!WARNING]    
> Dane ładunku UDP przechowywane w NX_PACKET powinny znajdować się *na granicy długich słów. Aplikacja musi pozostawić* wystarczającą ilość miejsca między wskaźnikiem wstępnym a wskaźnikiem uruchamiania danych dla netX Duo, aby umieścić nagłówki UDP, IP i nośnika fizycznego.

### <a name="udp-packet-receive"></a>Odbieranie pakietów UDP    
Wątki aplikacji mogą odbierać pakiety UDP z określonego gniazda przez wywołanie ***nx_udp_socket_receive***. Funkcja odbierania gniazda dostarcza najstarszy pakiet w kolejce odbierania gniazda. Jeśli w kolejce odbierania nie ma pakietów, wywołujący wątek może wstrzymać (z opcjonalnym limitem czasu) do momentu otrzymania pakietu.

Przetwarzanie pakietów odbieranych przez protokołu UDP (zwykle wywoływane z procedury obsługi przerwań odbierania sterowników sieciowych) jest odpowiedzialne za umieszczenie pakietu w kolejce odbierania gniazda UDP lub dostarczenie go do pierwszego wstrzymanego wątku czekającego na pakiet. Jeśli pakiet jest w kolejce, przetwarzanie odbierania sprawdza również maksymalną głębokość kolejki odbierania skojarzoną z gniazdem. Jeśli ten nowo dodany pakiet w kolejce przekroczy głębokość kolejki, najstarszy pakiet w kolejce zostanie odrzucony.

### <a name="udp-receive-notify"></a>Powiadomienie o odbierce UDP   
Jeśli wątek aplikacji musi przetworzyć odebrane dane z więcej niż jednego gniazda, ***należy nx_udp_socket_receive_notify*** funkcji. Ta funkcja rejestruje funkcję wywołania zwrotnego pakietu odbierania dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, wykonywana jest funkcja wywołania zwrotnego.

Zawartość funkcji wywołania zwrotnego ma określonej aplikacji; Jednak najprawdopodobniej zawiera on logikę informową wątek przetwarzania, że pakiet jest teraz dostępny na odpowiednim gnieździe.

### <a name="peer-address-and-port"></a>Adres i port elementu równorzędnego   
Po odebraniu pakietu UDP aplikacja może znaleźć adres IP i numer portu nadawcy przy użyciu usługi nx_udp_packet_info_extract ***.*** Po pomyślnym powrocie ta usługa dostarcza informacje o adresie IP nadawcy, numerze portu nadawcy i interfejsie lokalnym, za pośrednictwem którego odebrano pakiet.  

### <a name="thread-suspension"></a>Zawieszenie wątku   
Jak wspomniano wcześniej, wątki aplikacji mogą zostać wstrzymane podczas próby odbierania pakietu UDP na określonym porcie UDP. Po otrzymaniu pakietu na tym porcie jest on nadany do pierwszego wstrzymanego wątku i ten wątek jest następnie wznawiany. Opcjonalny limit czasu jest dostępny podczas zawieszania na pakiecie odbierania UDP, funkcji dostępnej dla większości usług NetX Duo.  

### <a name="udp-socket-statistics-and-errors"></a>Statystyki gniazd UDP i błędy     
Jeśli ta opcja jest włączona, oprogramowanie NetX Duo UDP socket śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/UDP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych pakietów UDP  
- Całkowita liczba wysłanych bajtów UDP  
- Łączna liczba odebranych pakietów UDP   
- Całkowita liczba odebranych bajtów UDP  
- Łączna liczba nieprawidłowych pakietów UDP  
- Łączna liczba porzucanych pakietów odbierania UDP  
- Łączna liczba błędów sumy kontrolnej odbioru UDP  
- Wysłane pakiety gniazd UDP  
- Wysłane bajty gniazd UDP  
- Odebrane pakiety gniazd UDP   
- Odebrane bajty gniazda UDP  
- Pakiety gniazd UDP w kolejce  
- Porzucone pakiety odbierania gniazd UDP  
- Błędy sumy kontrolnej gniazda UDP  

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_udp_info_get** _ dla statystyk UDP zamaskowanych na wszystkich gniazdach UDP oraz dla usługi *__nx_udp_socket_info_get_** dla statystyk UDP na określonym gnieździe UDP.

### <a name="udp-socket-control-block-nx_udp_socket"></a>Blok sterowania gniazdami UDP NX_UDP_SOCKET
Cechy poszczególnych gniazd UDP znajdują się w skojarzonym bloku NX_UDP_SOCKET sterowania. Zawiera przydatne informacje, takie jak link do struktury danych IP, interfejs sieciowy dla ścieżek wysyłania i odbierania, powiązany port i kolejka pakietów odbioru. Ta struktura jest zdefiniowana ***w nx_api.h.***

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Protokół Transmission Control Protocol (TCP) zapewnia niezawodny transfer danych strumienia między dwoma członkami sieci (RFC 793). Wszystkie dane wysyłane od jednego członka sieci są weryfikowane i potwierdzane przez odbierający. Ponadto dwa elementy członkowskie muszą nawiązyć połączenie przed transferem danych. Wszystko to zapewnia niezawodny transfer danych. Jednak wymaga to znacznie większej liczby narzutów niż opisany wcześniej transfer danych UDP.

Z wyjątkiem przypadków, gdy wspomniano, nie ma żadnych zmian w usługach interfejsu API protokołu TCP między NetX i NetX Duo, ponieważ protokół IPv6 jest głównie zainteresowany bazową warstwą adresów IP. Wszystkie usługi TCP NetX Duo mogą być używane dla połączeń IPv4 lub IPv6.

### <a name="tcp-header"></a>Nagłówek TCP   
W przypadku transmisji nagłówek TCP jest umieszczany przed danymi od użytkownika. W przypadku odbioru nagłówek TCP jest usuwany z pakietu przychodzącego, pozostawiając aplikacji tylko dane użytkownika. Protokół TCP używa protokołu IP do wysyłania i odbierania pakietów, co oznacza, że przed nagłówkiem TCP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 13 przedstawia format nagłówka TCP.

![Diagram formatu nagłówka TCP.](./media/user-guide/image22.png)

### <a name="figure-13-tcp-header"></a>RYSUNEK 13. Nagłówek TCP

Poniżej opisano format nagłówka TCP:

|Pole &nbsp; nagłówka |Przeznaczenie |
|------|------|
| **16-bitowy numer portu źródłowego** | To pole zawiera port, na który jest wysyłany pakiet TCP. Prawidłowe porty TCP mają zakres od 1 do 0xFFFF. |
| **16-bitowy port docelowy** | To pole zawiera port TCP, do który jest wysyłany pakiet. Prawidłowe porty TCP mają zakres od 1 do 0xFFFF. |
| **32-bitowy numer sekwencji** | To pole zawiera numer sekwencji danych wysyłanych z tego końca połączenia. Oryginalna sekwencja jest ustalana podczas początkowej sekwencji połączenia między dwoma węzłami TCP. Każdy transfer danych od tego momentu powoduje przyrost numeru sekwencji o liczbę wysłanych bajtów. |
| **32-bitowy numer potwierdzenia** | To pole zawiera numer sekwencji odpowiadający ostatniej bajtowi odebranemu przez tę stronę połączenia. Służy do określania, czy wcześniej wysłane dane zostały pomyślnie odebrane przez drugi koniec połączenia. |
| **4-bitowa długość nagłówka** | To pole zawiera liczbę 32-bitowych wyrazów w nagłówku TCP. Jeśli w nagłówku TCP nie ma żadnych opcji, to pole ma rozmiar 5. |
| **Bity kodu 6-bitowego** |To pole zawiera sześć różnych bitów kodu używanych do wskazywania różnych informacji sterujących skojarzonych z połączeniem. Bity sterujące są zdefiniowane w następujący sposób: <br \> - URG (21): Pilne presensje danych<br - ACK (20): Numer potwierdzenia jest prawidłowy<br - PSH (19): Natychmiast obsłuż te<dane br — RST (18): Zresetuj połączenie<br — SYN (17): zsynchronizowanie numerów sekwencji (używanych do nawiązania \> \> \> \> połączenia)<br — FIN (16): nadawca kończy przesyłanie \> (służy do zamykania połączenia) |
|**Okno 16-bitowe** |To pole jest używane do sterowania przepływem. Zawiera on liczbę bajtów, które gniazdo może obecnie odbierać. Jest to zasadniczo używane do sterowania przepływem. Nadawca jest odpowiedzialny za to, aby dane do wysłania zmieściły się w oknie anonsowania odbiorcy. |
|**16-bitowa podsuma kontrolna TCP** |To pole zawiera 16-bitową podsumę kontrolną dla pakietu, w tym nagłówek TCP, obszar danych pakietu i nagłówek pseudo-IP. |
|**16-bitowy pilny wskaźnik** |To pole zawiera dodatnie przesunięcie ostatniego bajtu pilnych danych. To pole jest prawidłowe tylko wtedy, gdy bit kodu urlg jest ustawiony w nagłówku. |

> [!NOTE]  
> Oczekuje się, że wszystkie nagłówki w implementacji *TCP/IP będą w **big endian** formacie. W tym formacie najbardziej znaczący bajt* wyrazu znajduje się w najniższym adresie bajtowym .

### <a name="tcp-enable"></a>Włączanie protokołu TCP       
Zanim będzie możliwe połączenie TCP i transmisje pakietów, aplikacja musi najpierw włączyć protokół TCP przez wywołanie ***nx_tcp_enable*** usługi. Po włączeniu tej opcji aplikacja będzie mieć bezpłatny dostęp do wszystkich usług TCP.  

### <a name="tcp-socket-create"></a>Tworzenie gniazda TCP    
Gniazda TCP są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Początkowy typ usługi, czas na żywo i rozmiar okna są definiowane przez nx_tcp_socket_create ***usługi.*** Nie ma żadnych ograniczeń liczby gniazd TCP w aplikacji.  

### <a name="tcp-checksum"></a>Sumy kontrolne TCP     
PROTOKÓŁ TCP określa 16-bitową podsumę kontrolną dopełnianą przez nagłówek pseudowęzmięki IP (składający się ze źródłowego adresu IP, docelowego adresu IP i słowa adresu IP protokołu/długości), nagłówka TCP i danych pakietów TCP. Jedyną różnicą między sumy kontrolne nagłówka pakietu TCP IPv4 i IPv6 jest to, że źródłowe i docelowe adresy IP są 32-bitowe w protokołach IPv4 i 128-bitowych w protokole IPv6. 

Niektóre kontrolery sieci mogą wykonywać obliczenia i walidację sumy kontrolnej TCP na sprzęcie. W przypadku takich systemów aplikacje mogą chcieć jak najbardziej korzystać ze sprzętowej logiki sumy kontrolnej, aby zmniejszyć obciążenie środowiska uruchomieniowego. Aplikacje mogą całkowicie wyłączyć logikę obliczeń sumy kontrolnej TCP z biblioteki NetX Duo w czasie kompilacji, definiując ***NX_DISABLE_TCP_TX_CHECKSUM** _ i __*_ NX_DISABLE_TCP_RX_CHECKSUM **. W ten sposób kod sumy kontrolnej TCP nie jest kompilowany. Należy jednak zachować ostrożność, jeśli jest zainstalowany opcjonalny pakiet NetX Duo IPsec, a połączenie TCP może wymagać przechodzenia przez bezpieczny kanał. W takim przypadku dane w pakietach należących do połączenia TCP są już zaszyfrowane, a większość sprzętowych modułów sumy kontrolnej TCP obecnych w sterowniku sieciowym nie może wygenerować poprawnej wartości sumy kontrolnej z zaszyfrowanego ładunku TCP.

Aby rozwiązać ten problem, aplikacja musi zachować logikę sumy kontrolnej TCP dostępną w bibliotece i korzystać z funkcji możliwości interfejsu. Po włączeniu funkcji możliwości interfejsu moduł TCP wie, jak prawidłowo obsługiwać sumy kontrolne TCP, jeśli sterownik może również obliczyć wartość sumy kontrolnej:

1) Jeśli pakiet TCP nie podlega procesowi protokołu IPsec, sprzęt interfejsu sieciowego może obliczyć sumy kontrolne. W związku z tym moduł TCP nie próbuje obliczyć sumy kontrolnej;

2) Jeśli pakiet IPsec jest zainstalowany, a pakiet TCP podlega procesowi protokołu IPsec, moduł TCP oblicza sumy kontrolne w oprogramowaniu przed wysłaniem pakietu do warstwy IPsec.

### <a name="tcp-port"></a>Port TCP     
Port TCP jest logicznym punktem połączenia w protokole TCP. Składnik TCP netX Duo ma 65 535 prawidłowych portów, od 1 do 0xFFFF. W przeciwieństwie do protokołu UDP, w którym dane z jednego portu mogą być wysyłane do dowolnego innego portu docelowego, port TCP jest połączony z innym konkretnym portem TCP i tylko wtedy, gdy to połączenie zostanie nawiązane, może mieć miejsce dowolny transfer danych — i tylko między dwoma portami, które się na to połączenie.

> [!IMPORTANT]
> Porty TCP są całkowicie oddzielone od portów *UDP, np. port UDP numer 1* nie ma relacji z portem TCP o numerze 1 .

### <a name="client-server-model"></a>Client-Server model     
Aby używać protokołu TCP do transferu danych, należy najpierw nawiązyć połączenie między dwoma gniazdami TCP. Utworzenie połączenia odbywa się w sposób klient-serwer. Strona klienta połączenia to strona, która inicjuje połączenie, podczas gdy strona serwera po prostu czeka na żądania połączenia klienta przed rozpoczęciem jakiegokolwiek przetwarzania.

> [!IMPORTANT]
> W przypadku urządzeń wieloadresowych NetX Duo automatycznie określa adres źródłowy do użycia dla połączenia oraz adres następnego przeskoku na podstawie docelowego adresu *IP połączenia. Ponieważ protokół TCP* jest ograniczony do wysyłania pakietów na adresy docelowe emisji pojedynczej (np. bez emisji), netX Duo nie wymaga "wskazówki" dotyczącej wyboru źródłowego adresu IPv6.

### <a name="tcp-socket-state-machine"></a>Komputer stanu gniazda TCP      
Połączenie między dwoma gniazdami TCP (jednym klientem i jednym serwerem) jest złożone i jest zarządzane w sposób komputera stanu. Każde gniazdo TCP rozpoczyna się w stanie ZAMKNIĘTY. Za pośrednictwem zdarzeń połączenia maszyna stanu każdego gniazda jest migrowana do stanu ESTABLISHED, w którym odbywa się większość transferu danych w protokole TCP. Gdy jedna strona połączenia nie chce już wysyłać danych, rozłącza się. Po rozłączeniu się z drugą stroną gniazdo TCP powróci do stanu CLOSED. Ten proces jest powtarzany za każdym razem, gdy klient i serwer TCP ustanawiają i zamykają połączenie. Rysunek 14 przedstawia różne stany maszyny stanu TCP.

### <a name="tcp-client-connection"></a>Połączenie klienta TCP       
Jak wspomniano wcześniej, strona klienta połączenia TCP inicjuje żądanie połączenia z serwerem TCP. Aby można było wykonać żądanie połączenia, należy włączyć protokół TCP w wystąpieniu adresu IP klienta. Ponadto należy utworzyć gniazdo TCP klienta przy użyciu usługi ***nx_tcp_socket_create** _ i powiązane z portem za pośrednictwem usługi _ *_nx_tcp_client_socket_bind_**.

Po powiązaniu gniazda klienta usługa ***nxd_tcp_client_socket_connect*** służy do nawiązywania połączenia z serwerem TCP. Należy pamiętać, że gniazdo musi być w stanie ZAMKNIĘTY, aby zainicjować próbę połączenia. Nawiązywanie połączenia rozpoczyna się od wystawienia pakietu SYN przez NetX Duo, a następnie oczekiwania na pakiet ACK SYN z serwera, co oznacza akceptację żądania połączenia. Po otrzymaniu pakietu SYN ACK netX Duo odpowiada pakietem ACK i podniesie gniazdo klienta do stanu ESTABLISHED.

![Diagram stanów maszyny stanu TCP.](./media/user-guide/image24.png)   

**RYSUNEK 14. Stany komputera stanu TCP**


> [!WARNING]
> *Aplikacje powinny używać **nxd_tcp_client_socket_connect** połączeń TCP IPv4 i IPv6. Aplikacje nadal mogą  używać protokołu **nx_tcp_client_socket_connect** połączeń TCP IPv4, ale  zachęcamy* deweloperów do korzystania z nxd_tcp_client_socket_connect, ponieważ nx_tcp_client_socket_connect zostanie ostatecznie przestarzała.

*Podobnie  nxd_tcp_socket_peer_info_get działa z połączeniami TCP IPv4 lub IPv6. Jednak **nx_tcp_socket_peer_info_get** jest nadal dostępna dla starszych aplikacji. Zachęcamy deweloperów do korzystania z **nxd_tcp_socket_peer_info_get** przyszłości.*

### <a name="tcp-client-disconnection"></a>Rozłączanie klienta TCP    
Zamknięcie połączenia jest realizowane przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie zostanie określone zawieszenie, gniazdo klienta wysyła pakiet RST do gniazda serwera i umieszcza gniazdo w stanie CLOSED. W przeciwnym razie w przypadku zażądania zawieszenia zostanie wykonany pełny protokół rozłączania TCP w następujący sposób: 

- Jeśli serwer wcześniej zainicjował żądanie rozłączenia (gniazdo klienta otrzymało już pakiet FIN, odpowiedział przy użyciu ACK i jest w stanie CLOSE WAIT), NetX Duo podniesie stan gniazda TCP klienta do stanu OSTATNIEGO ACK i wyśle pakiet FIN. Następnie czeka na ACK z serwera przed ukończeniem rozłączenia i wprowadzeniem stanu CLOSED.

- Jeśli z drugiej strony klient jest pierwszym użytkownikiem, który zainicjował żądanie rozłączenia (serwer nie został odłączony, a gniazdo jest nadal w stanie ESTABLISHED), NetX Duo wysyła pakiet FIN w celu zainicjowania rozłączenia i czeka na otrzymanie danych FIN i ACK z serwera przed zakończeniem rozłączania i umieszczeniem gniazda w stanie ZAMKNIĘTYM.

Jeśli w kolejce przesyłania gniazda nadal znajdują się pakiety, netX Duo zawiesza się na określony limit czasu, aby umożliwić potwierdzenie pakietów. Jeśli limit czasu wygaśnie, aplikacja NetX Duo opróżni kolejkę przesyłaną gniazda klienta. 

Aby odszybować port od gniazda klienta, aplikacja wywołuje ***nx_tcp_client_socket_unbind***. Gniazdo musi być w stanie ZAMKNIĘTYm lub być w trakcie rozłączania (tj. stanu OCZEKIWANIA W CZASIE) przed zwolnieniu portu; W przeciwnym razie zwracany jest błąd.

Na koniec, jeśli aplikacja nie potrzebuje już gniazda klienta, ***wywołuje*** nx_tcp_socket_delete, aby usunąć gniazdo.

### <a name="tcp-server-connection"></a>Połączenie z serwerem TCP      
Strona serwera połączenia TCP jest pasywna; tj. serwer czeka, aż klient zainicjuje żądanie połączenia. Aby zaakceptować połączenie klienta, należy najpierw włączyć protokół TCP w wystąpieniu adresu IP, wywołując usługę ***nx_tcp_enable** _. Następnie aplikacja musi utworzyć gniazdo TCP przy użyciu usługi _ *_nx_tcp_socket_create_**.  

Gniazdo serwera musi być również ustawione do nasłuchiwania żądań połączenia. Jest to osiągane przy użyciu ***nx_tcp_server_socket_listen*** usługi. Ta usługa umieszcza gniazdo serwera w stanie LISTEN i wiąże określony port serwera z gniazdem.

> [!NOTE] 
> *Aby ustawić procedurę wywołania zwrotnego nasłuchiwu gniazda, aplikacja określa odpowiednią funkcję wywołania zwrotnego dla tcp_listen_callback argumentu **nx_tcp_server_socket_listen** usługi. Ta funkcja wywołania zwrotnego aplikacji jest następnie wykonywana przez firmę NetX Duo za każdym razem, gdy na tym porcie serwera jest wymagane nowe połączenie. Przetwarzanie w wywołaniu zwrotym jest pod kontrolą aplikacji.*

Aby akceptować żądania połączenia klienta, aplikacja wywołuje usługę ***nx_tcp_server_socket_accept** _. Gniazdo serwera musi być w stanie LISTEN lub SYN RECEIVED (tj. serwer jest w stanie LISTEN i odebrał pakiet SYN od klienta żądający połączenia), aby wywołać usługę akceptowania. Stan pomyślnego zwrócenia z _ *_nx_tcp_server_socket_accept_** wskazuje, że połączenie zostało ustawione, a gniazdo serwera jest w stanie ESTABLISHED.

Gdy gniazdo serwera ma prawidłowe połączenie, dodatkowe żądania połączenia klienta są kolejkowane do głębokości określonej przez listen_queue_size *przekazywane* do usługi  * **nx_tcp_server_socket_listen** _service. Aby przetwarzać kolejne połączenia na porcie serwera, aplikacja musi wywołać element *__nx_tcp_server_socket_relisten_** z dostępnym gniazdem (tj. gniazdem w stanie ZAMKNIĘTYM). Należy pamiętać, że to samo gniazdo serwera może być używane, jeśli poprzednie połączenie skojarzone z tym gniazdem zostało zakończone, a gniazdo jest w stanie ZAMKNIĘTY.

### <a name="tcp-server-disconnection"></a>Rozłączanie serwera TCP     
Zamknięcie połączenia jest realizowane przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie zostanie określone zawieszenie, gniazdo serwera wysyła pakiet RST do gniazda klienta i umieszcza gniazdo w stanie CLOSED. W przeciwnym razie w przypadku zażądania zawieszenia zostanie wykonany pełny protokół rozłączania TCP w następujący sposób:

- Jeśli klient wcześniej zainicjował żądanie rozłączenia (gniazdo serwera otrzymało już pakiet FIN, odpowiedział przy użyciu ACK i jest w stanie CLOSE WAIT), NetX Duo podniesie stan gniazda TCP do stanu OSTATNIEGO ACK i wyśle pakiet FIN. Następnie czeka na ACK od klienta przed ukończeniem rozłączenia i wprowadzeniem stanu CLOSED.

- Jeśli z drugiej strony serwer jest pierwszym, który zainicjował żądanie rozłączenia (klient nie rozłączył się, a gniazdo jest nadal w stanie ESTABLISHED), NetX Duo wysyła pakiet FIN w celu zainicjowania rozłączenia i czeka na otrzymanie od klienta danych FIN i ACK przed zakończeniem rozłączania i umieszczeniem gniazda w stanie ZAMKNIĘTYM.

Jeśli w kolejce przesyłania gniazda nadal znajdują się pakiety, netX Duo zawiesza się na określony limit czasu, aby umożliwić potwierdzenie tych pakietów. Jeśli limit czasu wygaśnie, netX Duo opróżni kolejkę przesyłania gniazda serwera.

Po zakończeniu przetwarzania rozłączania i w stanie ZAMKNIĘTY gniazda serwera aplikacja musi wywołać usługę ***nx_tcp_server_socket_unaccept** _, aby zakończyć skojarzenie tego gniazda z portem serwera. Należy pamiętać, że ta usługa musi być wywoływana przez aplikację, _*_nawet nx_tcp_socket_disconnect_*_ lub _*_nx_tcp_server_socket_accept_*_ zwracać stan błędu. Po _*_nx_tcp_server_socket_unaccept_*_ gniazda może służyć jako gniazdo klienta lub serwera, a nawet usunięte, jeśli nie jest już potrzebne. Jeśli wymagane jest zaakceptowanie innego połączenia klienta na tym samym porcie serwera, usługa _ *_nx_tcp_server_socket_relisten_** powinna być wywoływana na tym gnieździe.

Następujący segment kodu ilustruje sekwencję wywołań typowego serwera TCP:

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

### <a name="mss-validation"></a>Walidacja mss      
Maksymalny rozmiar segmentu (MSS, Maximum Segment Size) to maksymalna liczba bajtów, które host TCP może odbierać bez fragmentacji przez podstawową warstwę adresów IP. W fazie ustanawiania połączenia TCP oba te połączenia wymieniają własną wartość protokołu TCP MSS, dzięki czemu nadawca nie wysyła segmentu danych TCP, który jest większy niż segment MSS odbiorcy. Moduł TCP NetX Duo opcjonalnie zweryfikuje wartość mss anonsowanego elementu równorzędnego przed nawiązaniem połączenia. Domyślnie netX Duo nie włącza takiego sprawdzenia. Aplikacje, które chcą przeprowadzić walidację MSS, muszą zdefiniować wartość ***NX_ENABLE_TCP_MSS_CHECK** _ podczas budowania biblioteki NetX Duo, a wartość minimalną należy zdefiniować w _*_NX_TCP_MSS_MINIMUM_*_. Przychodzące połączenia TCP z wartościami MSS poniżej *__ NX_TCP_MSS_MINIMUM_** są porzucane.

### <a name="stop-listening-on-a-server-port"></a>Zatrzymywanie nasłuchiwania na porcie serwera    
Jeśli aplikacja nie chce już nasłuchiwać żądań połączenia klienta na porcie serwera, który został wcześniej określony przez wywołanie usługi ***nx_tcp_server_socket_listen** _, aplikacja po prostu wywołuje usługę _ *_nx_tcp_server_socket_unlisten_**. Ta usługa umieszcza każde gniazdo oczekujące na połączenie z powrotem w stanie ZAMKNIĘTE i zwalnia wszystkie pakiety żądań połączenia klienta w kolejce. 

### <a name="tcp-window-size"></a>Rozmiar okna TCP   
Zarówno podczas fazy instalacji, jak i transferu danych połączenia każdy port zgłasza ilość danych, które może obsłużyć, co jest nazywane rozmiarem okna. W przypadku odbierania i przetwarzania danych ten rozmiar okna jest dostosowywany dynamicznie. W przypadku protokołu TCP nadawca może wysłać tylko ilość danych, która mieści się w oknie odbiorcy. W zasadzie rozmiar okna zapewnia sterowanie przepływem transferu danych w każdym kierunku połączenia.   

### <a name="tcp-packet-send"></a>Wysyłanie pakietów TCP     
Wysyłanie danych TCP można łatwo wykonać, wywołując ***nx_tcp_socket_send*** funkcji. Jeśli rozmiar przesyłanych danych jest większy niż wartość MSS gniazda lub bieżącego okna odbierania elementów równorzędnych, w zależności od tego, która wartość jest mniejsza, wewnętrzna logika TCP przekazuje dane, które pasują do minimalnej (MSS, okno odbierania elementów równorzędnych) do transmisji. Następnie ta usługa tworzy nagłówek TCP przed pakietem (w tym obliczenie sumy kontrolnej). Jeśli rozmiar okna odbiornika nie wynosi zero, wywołujący wyśle jak najwięcej danych, aby wypełnić rozmiar okna odbiornika. Jeśli okno odbierania stanie się zerowe, wywołujący może wstrzymać i poczekać na zwiększenie rozmiaru okna odbiornika na tyle, aby ten pakiet został wysłany. W dowolnym momencie wiele wątków może zostać wstrzymanych podczas próby wysłania danych za pośrednictwem tego samego gniazda. 

> [!WARNING]  
> *Dane TCP przechowywane w NX_PACKET powinny znajdować się na granicy długich słów. Ponadto musi być wystarczająca* ilość miejsca między dołączany wskaźnik i wskaźnik uruchamiania danych, aby umieścić nagłówki TCP, IP i nośnika fizycznego.

### <a name="tcp-packet-retransmit"></a>Retransmisja pakietów TCP      
Wcześniej przesłane pakiety TCP rzeczywiście były przechowywane wewnętrznie do momentu zwrócenia ACK z drugiej strony połączenia. Jeśli przesłane dane nie zostaną potwierdzone w ramach limitu czasu, przechowywany pakiet zostanie ponownie wysłany i zostanie ustawiony następny limit czasu. Po otrzymaniu ACK wszystkie pakiety objęte numerem potwierdzenia w wewnętrznej kolejce przesyłania są zwalniane.  

> [!WARNING]   
> Aplikacja nie może ponownie używać pakietu ani zmieniać jego zawartości po *nx_tcp_socket_send() z NX_SUCCESS. Przesłany pakiet jest ostatecznie zwalniany przez* wewnętrzne przetwarzanie NetX Duo po otrzymaniu potwierdzenia danych przez drugi koniec .

### <a name="tcp-keepalive"></a>Utrzymanie aktywności protokołu TCP     
Funkcja utrzymania aktywności protokołu TCP umożliwia gniazdu wykrywanie, czy jego element równorzędny rozłącza się bez prawidłowego zakończenia (na przykład awaria elementu równorzędnego) lub uniemożliwia niektórym obiektom monitorowania sieci przerwanie połączenia na długi czas bezczynności. Utrzymanie aktywności tcp działa przez okresowe wysyłanie ramki TCP bez danych, a numer sekwencji jest ustawiony na jeden mniejszy niż bieżący numer sekwencji. Po otrzymaniu takiej ramki utrzymania aktywności PROTOKOŁU TCP odbiorca, jeśli nadal jest aktywne, otrzymuje odpowiedź z ACK dla bieżącego numeru sekwencji. To kończy transakcję utrzymania aktywności.  

Domyślnie funkcja utrzymania aktywności nie jest włączona. Aby można było korzystać z tej funkcji, biblioteka NetX Duo musi być zbudowana przy **użyciu** NX_ENABLE_TCP_KEEPALIVE _ defined. Symbol _ *_NX_TCP_KEEPALIVE_INITIAL_** określa liczbę sekund braku aktywności przed zainicjowaną ramką utrzymania aktywności.  

### <a name="tcp-packet-receive"></a>Odbieranie pakietów TCP   
Przetwarzanie pakietów odbieranych przez protokół TCP (wywoływane z wątku pomocnika IP) jest odpowiedzialne za obsługę różnych akcji połączenia i rozłączania, a także przesyłanie przetwarzania potwierdzenia. Ponadto przetwarzanie pakietów odbioru TCP jest odpowiedzialne za umieszczanie pakietów z danymi odbierania w kolejce odbierania odpowiedniego gniazda TCP lub dostarczanie pakietu do pierwszego wstrzymanego wątku czekającego na pakiet.

### <a name="tcp-receive-notify"></a>Powiadomienie o odbierania TCP     
Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, ***należy nx_tcp_socket_receive_notify*** funkcji. Ta funkcja rejestruje funkcję wywołania zwrotnego pakietu odbierania dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, wykonywana jest funkcja wywołania zwrotnego.  

Zawartość funkcji wywołania zwrotnego ma określonej aplikacji; Jednak funkcja najprawdopodobniej zawierałaby logikę, aby poinformować wątek przetwarzania, że pakiet jest dostępny na odpowiednim gnieździe. 

### <a name="thread-suspension"></a>Zawieszenie wątku      
Jak wspomniano wcześniej, wątki aplikacji mogą zostać wstrzymane podczas próby odbierania danych z określonego portu TCP. Po otrzymaniu pakietu na tym porcie jest on nadany do pierwszego wstrzymanego wątku i ten wątek jest następnie wznawiany. Opcjonalny limit czasu jest dostępny podczas zawieszania się na pakiecie odbioru TCP, funkcji dostępnej dla większości usług NetX Duo.  

Wstrzymanie wątku jest również dostępne dla połączeń (zarówno klienta, jak i serwera), powiązań klienta i usług rozłączania.  

### <a name="tcp-socket-statistics-and-errors"></a>Błędy i statystyki gniazd TCP     
Jeśli ta opcja jest włączona, oprogramowanie gniazda TCP NetX Duo śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/TCP są utrzymywane następujące statystyki i raporty o błędach:   

- Łączna liczba wysłanych pakietów TCP  
- Całkowita liczba wysłanych bajtów TCP  
- Łączna liczba odebranych pakietów TCP   
- Całkowita liczba odebranych bajtów TCP   
- Łączna liczba nieprawidłowych pakietów TCP   
- Łączna liczba porzucanych pakietów odbioru TCP    
- Łączna liczba błędów sumy kontrolnej odbioru TCP   
- Łączna liczba połączeń TCP   
- Całkowita liczba rozłączeń TCP   
- Łączna liczba porzucanych połączeń TCP    
- Łączna liczba ponownych transmisji pakietów TCP   
- Wysłane pakiety gniazd TCP   
- Wysłane bajty gniazd TCP   
- Odebrane pakiety gniazd TCP   
- Odebrane bajty gniazda TCP   
- Retransmisje pakietów gniazd TCP    
- Pakiety gniazd TCP w kolejce    
- Błędy sumy kontrolnej gniazda TCP    
- Stan gniazda TCP    
- Głębokość kolejki przesyłania gniazd TCP    
- Rozmiar okna przesyłania gniazd TCP    
- Rozmiar okna odbierania gniazd TCP    

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_tcp_info_get** _ dla łącznej statystyki TCP i usługą *__nx_tcp_socket_info_get_** dla statystyk TCP na gniazdo.

### <a name="tcp-socket-control-block-nx_tcp_socket"></a>TCP Socket Control Block NX_TCP_SOCKET      
Cechy poszczególnych gniazd TCP znajdują się w skojarzonym bloku sterowania usługi *NX_TCP_SOCKET,* który zawiera przydatne informacje, takie jak link do struktury danych IP, interfejs połączenia sieciowego, powiązany port i kolejka pakietów odbioru. Ta struktura jest zdefiniowana ***w nx_api.h.***