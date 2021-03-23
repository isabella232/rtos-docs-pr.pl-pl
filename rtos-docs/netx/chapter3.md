---
title: Rozdział 3 — funkcjonalne składniki platformy Azure RTO NetX
description: Ten rozdział zawiera opis stosu TCP/IP o wysokiej wydajności usługi Azure RTO NetX z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db23aa152b2765ac7cc9be098723fc5df0947484
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822789"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx"></a>Rozdział 3 — funkcjonalne składniki platformy Azure RTO NetX

Ten rozdział zawiera opis stosu TCP/IP o wysokiej wydajności usługi Azure RTO NetX z perspektywy funkcjonalnej. 

## <a name="execution-overview"></a>Przegląd wykonywania

Istnieje pięć typów wykonywania programu w ramach aplikacji NetX: inicjalizacja, wywołania interfejsu aplikacji, wewnętrzny wątek IP, okresowe czasomierze IP i sterownik sieciowy.

> [!IMPORTANT]
> NetX wymaga instalacji ThreadX i zależy od jej wykonywania, zawieszania, okresowych czasomierzy i wzajemnych wykluczeń.

### <a name="initialization"></a>Inicjalizacja

Przed wywołaniem innej usługi NetX należy wywołać usługę ***nx_system_initialize** _. Inicjalizację systemu można wywołać z ThreadX _ *_tx_application_define_** procedury lub z wątków aplikacji.

Po znaku ***nx_system_initialize** _ system jest gotowy do tworzenia pul pakietów i wystąpień adresów IP. Ponieważ utworzenie wystąpienia adresu IP wymaga domyślnej puli pakietów, musi istnieć co najmniej jedna pula pakietów NetX przed utworzeniem wystąpienia adresu IP. Tworzenie pul pakietów i wystąpień adresów IP jest dozwolone z funkcji inicjowania ThreadX _ *_tx_application_define_** i z wątków aplikacji.

Wewnętrznie Tworzenie wystąpienia IP jest realizowane w dwóch częściach. Pierwsza część jest wykonywana w kontekście obiektu wywołującego, z ***tx_application_define*** lub z kontekstu wątku aplikacji. Obejmuje to Konfigurowanie struktury danych IP i tworzenie różnych zasobów IP, w tym wewnętrznego wątku IP. Druga część jest wykonywana podczas początkowego wykonywania z wewnętrznego wątku IP. Jest to miejsce, w którym sterownik sieciowy dostarczony podczas pierwszej części tworzenia IP jest najpierw wywoływany. Wywołanie sterownika sieci z wewnętrznego wątku IP umożliwia sterownikowi wykonywanie operacji we/wy i wstrzymywanie podczas przetwarzania inicjalizacji. Gdy sterownik sieciowy wraca z przetwarzania inicjowania, tworzenie adresu IP zostało zakończone.

> [!IMPORTANT]
> **Nx_ip_status_check** usługi NetX jest dostępna, aby uzyskać informacje o wystąpieniu adresu IP i jego podstawowym stanie interfejsu. Takie informacje o stanie obejmują, czy łącze jest inicjowane, włączone oraz czy adres IP jest rozpoznawany. Te informacje służą do synchronizowania wątków aplikacji, które wymagają użycia nowo utworzonego wystąpienia adresu IP. W przypadku systemów z wieloma systemami prywatnymi Zobacz "Pomoc techniczna z wieloma domem" poniżej. **nx_ip_interface_status_check** jest dostępny do uzyskania informacji o określonym interfejsie.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Wywołania z aplikacji są wykonywane w dużej mierze od wątków aplikacji uruchomionych w ramach ThreadX RTO. Jednak niektóre inicjalizacje, tworzenie i Włączanie usług mogą być wywoływane z ***tx_application_define***. Sekcje "dozwolone z" w rozdziale 4 wskazują, z której może być wywoływana każda usługa NetX.

W większości przypadków działania z intensywnym przetwarzaniem, takie jak obliczanie sum kontrolnych, są wykonywane w kontekście wątku wywołującego — bez blokowania dostępu innych wątków do wystąpienia IP. Na przykład podczas transmisji, obliczenia sumy kontrolnej UDP są wykonywane w ramach usługi ***nx_udp_socket_send*** , przed wywołaniem podstawowej funkcji wysyłania adresów IP. W przypadku odebranego pakietu suma kontrolna UDP jest obliczana w ramach usługi ***nx_udp_socket_receive*** wykonywanej w kontekście wątku aplikacji. Pomaga to zapobiegać zapewnieniu żądań sieci przez wątki o wyższym priorytecie z powodu przetwarzania obliczeń sum kontrolnych o niższym priorytecie.

Wartości, takie jak adresy IP i numery portów, są przesyłane do funkcji interfejsu API w kolejności bajtów hosta. Wewnętrznie te wartości są przechowywane w kolejności bajtów hosta. Dzięki temu deweloperzy mogą łatwo wyświetlać wartości za pomocą debugera. Gdy te wartości są programowane do ramki do transmisji, są konwertowane na kolejność bajtów sieci.

### <a name="internal-ip-thread"></a>Wewnętrzny wątek IP

Jak wspomniano, każde wystąpienie protokołu IP w NetX ma swój własny wątek. Priorytet i rozmiar stosu wewnętrznego wątku IP są zdefiniowane w usłudze ***nx_ip_create*** . Wewnętrzny wątek IP jest tworzony w trybie gotowym do wykonania. Jeśli wątek IP ma wyższy priorytet niż wątek wywołujący, może wystąpić zastępujący w wywołaniu IP Create.

Punkt wejścia wewnętrznego wątku IP jest w wewnętrznej funkcji ***_nx_ip_thread_entry***. Po uruchomieniu wewnętrzny wątek IP najpierw kończy inicjalizację sterownika sieci, która składa się z trzech wywołań sterownika sieci specyficznego dla aplikacji. Pierwsze wywołanie polega na dołączeniu sterownika sieci do wystąpienia IP, po którym następuje wywołanie inicjacji, które umożliwia sterownikowi sieciowe przechodzenie przez proces inicjalizacji. Po powrocie sterownika sieci z inicjacji (może on zostać zawieszony podczas oczekiwania na prawidłowe skonfigurowanie sprzętu), wewnętrzny wątek IP wywołuje ponownie sterownik sieciowy, aby włączyć link. 

Po powrocie sterownika sieci z wywołania Włącz łącze, wewnętrzny wątek IP wprowadza pętlę nieskończoną dla różnych zdarzeń, które wymagają przetworzenia dla tego wystąpienia IP. Zdarzenia przetwarzane w tej pętli obejmują odroczony przyjmowanie pakietów IP, zestaw fragmentów pakietów IP, przetwarzanie ping protokołu ICMP, przetwarzanie protokołu IGMP, przetwarzanie kolejki pakietów TCP, przetwarzanie przez TCP, przekroczenie limitu czasu zestawu fragmentów adresów IP oraz okresowe przetwarzanie IGMP. Zdarzenia obejmują również działania dotyczące rozpoznawania adresów: Przetwarzanie pakietów ARP i okresowe przetwarzanie ARP w sieci IP.

> [!NOTE]
> *Funkcje wywołania zwrotnego NetX, w tym nasłuchiwanie i rozłączane wywołania zwrotne, są wywoływane z wewnętrznego wątku IP — a nie oryginalnego wątku wywołującego. Aplikacja musi zadbać o to, aby nie wstrzymywać wewnątrz żadnej funkcji wywołania zwrotnego NetX.*

### <a name="ip-periodic-timers"></a>Okresowe czasomierze IP
Dla każdego wystąpienia IP są używane dwa okresowe czasomierze ThreadX. Pierwszy z nich to jednorazowy czasomierz dla protokołu ARP, protokołu IGMP, limitu czasu protokołu TCP, a także dyski reasemblera fragmentu IP. Drugi czasomierz to czasomierz 100 ms, który umożliwia przekroczenie limitu czasu ponownej transmisji protokołu TCP.

### <a name="network-driver"></a>Sterownik sieciowy
Każde wystąpienie IP w NetX ma interfejs podstawowy, który jest identyfikowany przez jego sterownik urządzenia określony w usłudze ***nx_ip_create*** . Sterownik sieciowy jest odpowiedzialny za obsługę różnych żądań NetX, w tym transmisja pakietów, odbieranie pakietów i żądania dotyczące stanu i kontroli.

W przypadku systemu wieloznacznego wystąpienie protokołu IP zawiera wiele interfejsów, z których każdy jest skojarzony ze sterownikiem sieciowym wykonującym te zadania dla odpowiedniego interfejsu.

Sterownik sieciowy musi również obsługiwać zdarzenia asynchroniczne występujące na nośniku. Zdarzenia asynchroniczne z nośnika obejmują odbieranie pakietów, uzupełnianie transmisji pakietów i zmiany stanu. NetX udostępnia sterownik sieciowy z kilkoma funkcjami dostępu do obsługi różnych zdarzeń. Te funkcje są przeznaczone do wywoływania z części procedury usługi przerwania sterownika sieci. W przypadku sieci IP sterownik sieciowy powinien przesłać dalej wszystkie pakiety ARP odebrane do funkcji wewnętrznej ***_nx_arp_packet_deferred_receive** _. Wszystkie pakiety RARP powinny być przekazywane do _ *_ _nx_rarp_packet_deferred_receive_* _ funkcji wewnętrznej. Dostępne są dwie opcje pakietów IP. Jeśli jest wymagane szybkie wysyłanie pakietów IP, przychodzące pakiety IP powinny być przekazywane do _ _ *_nx_ip_packet_receive_* _ do natychmiastowego przetwarzania. Znacznie poprawia to wydajność NetX w obsłudze pakietów IP. W przeciwnym razie sterownik sieciowy powinien przekazywać pakiety IP do _ * _ _nx_ip_packet_deferred_receive_* *. Ta usługa umieszcza pakiet IP w odroczonej kolejce przetwarzania, w której jest następnie obsługiwany przez wewnętrzny wątek IP, co skutkuje mniejszą ilością czasu przetwarzania ISR.

Sterownik sieciowy może również odroczyć przetwarzanie przerwania w celu uruchomienia z kontekstu wątku IP. W tym trybie procedura ISR zapisze niezbędne informacje, wywołaj wewnętrzną funkcję ***_nx_ip_driver_deferred_processing*** i Potwierdź kontroler przerwań. Ta usługa powiadamia wątek IP w celu zaplanowania wywołania zwrotnego sterownika urządzenia, aby zakończyć przetwarzanie zdarzenia, które powoduje przerwanie.

Niektóre kontrolery sieci mogą wykonywać obliczenia i weryfikację sum kontrolnych nagłówka TCP/IP na sprzęcie bez uwzględniania cennych zasobów procesora CPU. Aby skorzystać z funkcji sprzętowej, NetX oferuje opcje włączania lub wyłączania obliczeń sum kontrolnych oprogramowania w czasie kompilacji, a także włączania lub wyłączania obliczeń sum kontrolnych w czasie wykonywania. Aby uzyskać bardziej szczegółowe informacje na temat pisania sterowników sieciowych NetX, zobacz "[rozdział 5 NetX Network Drivers](chapter5.md)".

### <a name="multihome-support"></a>Obsługa wielostrona
NetX obsługuje systemy połączone z wieloma urządzeniami fizycznymi przy użyciu jednego wystąpienia IP. Każdy interfejs fizyczny jest przypisany do bloku sterowania interfejsem w wystąpieniu IP. Aplikacje chcące korzystać z systemu wieloznacznego muszą definiować wartość **NX_MAX_PHSYCIAL_INTERFACES** do liczby urządzeń fizycznych podłączonych do systemu i ponownie kompilować bibliotekę NetX. Domyślnie **NX_MAX_PHYSICAL_INTERFACES** jest ustawiona na jeden, tworząc jeden blok sterowania interfejsem w wystąpieniu IP.

Aplikacja NetX tworzy pojedyncze wystąpienie adresu IP dla urządzenia podstawowego przy użyciu usługi ***nx_ip_create** _. Dla każdego dodatkowego urządzenia sieciowego aplikacja dołącza urządzenie do wystąpienia IP przy użyciu usługi _ *_nx_ip_interface_attach_**.

Każda struktura interfejsu sieciowego zawiera podzestaw informacji o sieci o interfejsie sieciowym, który znajduje się w bloku kontroli IP, w tym adres IP interfejsu, maskę podsieci, rozmiar IP jednostki MTU i informacje o adresie warstwy MAC.

> [!IMPORTANT]
> *NetX z obsługą wielodomu jest zgodna z poprzednimi wersjami NetX. Usługi, które nie pobierają domyślnych informacji o interfejsie, do podstawowego urządzenia sieciowego.*

Interfejs podstawowy ma indeks zero na liście wystąpień adresów IP. Do każdego kolejnego urządzenia dołączonego do wystąpienia protokołu IP jest przypisywany następny indeks.

Wszystkie usługi protokołów warstwy wyższej, dla których jest włączone wystąpienie protokołu IP, w tym protokoły TCP, UDP, ICMP i IGMP, są dostępne dla wszystkich dołączonych urządzeń.

W większości przypadków NetX może określić najlepszy adres źródłowy do użycia podczas przesyłania pakietu. Wybór adresów źródłowych jest oparty na adresie docelowym. Usługi NetX Services są udostępniane, aby umożliwić aplikacjom określenie określonego adresu źródłowego, w przypadkach, gdy najbardziej odpowiedni dla nich nie może być określony przez adres docelowy. Przykładem może być w systemie z wieloma lokalizacjami, aplikacja musi wysłać pakiet do adresów IP emisji lub multiemisji.

Usługi przeznaczone do tworzenia aplikacji multihomed:

*nx_igmp_multicast_interface_join nx_ip_driver_interface_direct_command nx_ip_interface_address_get nx_ip_interface_address_set nx_ip_interface_attach nx_ip_interface_info_get nx_ip_interface_status_check nx_ip_raw_packet_interface_send nx_udp_socket_interface_send*

Te usługi zostały omówione bardziej szczegółowo w[rozdziale 4 — Opis usług Azure RTO NetX Services](chapter4.md).

### <a name="loopback-interface"></a>Interfejs sprzężenia zwrotnego
Interfejs sprzężenia zwrotnego jest specjalnym interfejsem sieciowym bez linku fizycznego dołączonego do. Interfejs sprzężenia zwrotnego umożliwia aplikacjom komunikowanie się przy użyciu adresu IP sprzężenia zwrotnego 127.0.0.1

Aby użyć logicznego interfejsu sprzężenia zwrotnego, upewnij się, że opcja konfigurowalne ***NX_DISABLE_LOOPBACK_INTERFACE*** nie jest ustawiona.

### <a name="interface-control-blocks"></a>Bloki sterujące interfejsu
Liczba bloków sterujących interfejsem w wystąpieniu IP jest liczbą interfejsów fizycznych (zdefiniowanych przez ***NX_MAX_PHYSICAL_INTERFACES** _) i interfejsem sprzężenia zwrotnego, jeśli jest włączony. Łączna liczba interfejsów jest zdefiniowana w _ *_NX_MAX_IP_INTERFACES_* *.

## <a name="protocol-layering"></a>Warstwy protokołu

Protokół TCP/IP zaimplementowany przez NetX jest protokołem warstwowym, co oznacza, że bardziej złożone protokoły są zbudowane w oparciu o prostsze protokoły bazowe. W przypadku protokołu TCP/IP najniższy protokół warstwy znajduje się w *warstwie linku* i jest obsługiwany przez sterownik sieciowy. Ten poziom jest zwykle przeznaczony do sieci Ethernet, ale może być również Fiber, serial lub praktycznie dowolnym nośnikiem fizycznym.

W górnej części warstwy linku znajduje się *warstwa sieciowa*. W przypadku protokołu TCP/IP jest to adres IP, który jest zasadniczo odpowiedzialny za wysyłanie i otrzymywanie prostych pakietów, w sposób optymalny w całej sieci. Protokoły typu zarządzania, takie jak ICMP i IGMP, są zazwyczaj klasyfikowane jako warstwy sieci, nawet jeśli są oparte na adresie IP do wysyłania i otrzymywania.

*Warstwa transportu* jest zareszcie warstwy sieciowej. Ta warstwa jest odpowiedzialna za zarządzanie przepływem danych między hostami w sieci. Istnieją dwa typy usług transportowych obsługiwane przez NetX: UDP i TCP. Usługi UDP zapewniają optymalny sposób wysyłania i otrzymywania danych między dwoma hostami bez połączenia, natomiast protokół TCP zapewnia niezawodne usługi zorientowane na połączenia między dwiema jednostkami hosta.

Ta warstwa jest odzwierciedlana w rzeczywistych pakietach danych sieciowych. Każda warstwa w protokole TCP/IP zawiera blok informacji o nazwie header. Ta technika otaczających danych (i prawdopodobnie informacji o protokole) z nagłówkiem jest zazwyczaj nazywana hermetyzacją danych. Rysunek 1 pokazuje przykład warstw NetX i rysunek 2 przedstawia powstający hermetyzację danych dla wysyłanych danych UDP.

![Warstwy protokołu](./media/user-guide/protocol-layering.png)

**RYSUNEK 1. Warstwy protokołu**

![Hermetyzacja danych UDP](./media/user-guide/udp-data-encapsulation.png)

**RYSUNEK 2. Hermetyzacja danych UDP**

## <a name="packet-pools"></a>Pule pakietów

Przydzielanie pakietów w sposób szybki i deterministyczny jest zawsze wyzwaniem w aplikacjach sieci w czasie rzeczywistym. Z tego względu NetX zapewnia możliwość tworzenia wielu pul pakietów o stałym rozmiarze i zarządzania nimi.

Ponieważ pule pakietów NetX składają się z bloków pamięci o stałym rozmiarze, nigdy nie występują żadne wewnętrzne problemy z defragmentacją. Oczywiście fragmentacja powoduje, że zachowanie, które jest niedeterministyczne.

Ponadto czas wymagany do przydzielenia i zwolnienia pakietu NetX do prostego manipulowania listą. Ponadto alokacja i cofanie pakietów odbywa się na końcu listy dostępnych. Zapewnia to najszybszy możliwy do przetwarzania listy połączonej.

Brak elastyczności jest zazwyczaj główną wadą dla pul pakietów o stałym rozmiarze. Określenie optymalnego rozmiaru ładunku pakietu, który również obsługuje pakiet przychodzący najgorszego przypadku, jest trudnym zadaniem. Pakiety NetX dotyczą tego problemu z opcjonalną funkcją o nazwie tworzenie *łańcucha pakietów*. Rzeczywisty pakiet sieciowy można połączyć z jednym lub wieloma połączonymi ze sobą pakietami NetX. Ponadto nagłówek pakietu zachowuje wskaźnik na górze pakietu. Po dodaniu dodatkowych protokołów wskaźnik ten jest po prostu przenoszony do tyłu, a nowy nagłówek jest zapisywana bezpośrednio przed danymi. Bez elastycznej technologii pakietów, stos będzie musiał przydzielić inny bufor i skopiować dane do nowego buforu z nowym nagłówkiem, który przetwarza intensywne przetwarzanie.

Ponieważ każdy rozmiar ładunku pakietu został ustalony dla danej puli pakietów, dane aplikacji o rozmiarze większym niż rozmiar ładunku wymagają wielu pakietów połączonych ze sobą. Podczas wypełniania pakietu przy użyciu danych użytkownika aplikacja musi używać ***nx_packet_data_append*** usługi. Ta usługa przenosi dane aplikacji do pakietu. W sytuacjach, gdy pakiet nie wystarcza do przechowywania danych użytkownika, dodatkowe pakiety są przydzieleni do przechowywania danych użytkownika. Aby można było korzystać z łańcucha pakietów, Sterownik musi mieć możliwość odbierania lub przesyłania z połączonych pakietów.

Każda pula pamięci pakietu NetX jest zasobem publicznym. NetX nie ma żadnych ograniczeń dotyczących sposobu używania pul pakietów.

### <a name="packet-pool-memory-area"></a>Obszar pamięci puli pakietów
Obszar pamięci dla puli pakietów jest określany podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci dla obiektów ThreadX i NetX, może ona znajdować się w dowolnym miejscu w przestrzeni adresowej docelowej. Jest to ważna funkcja ze względu na znaczną elastyczność zapewnianą przez aplikację. Załóżmy na przykład, że produkt komunikacyjny ma obszar pamięci o dużej szybkości dla buforów sieciowych. Ten obszar pamięci jest łatwo wykorzystywany przez umieszczenie go w puli pamięci pakietu NetX.

### <a name="creating-packet-pools"></a>Tworzenie pul pakietów
Pule pakietów są tworzone podczas inicjalizacji lub podczas wykonywania przez wątki aplikacji. Nie ma ograniczeń dotyczących liczby pul pamięci pakietów w aplikacji NetX.

### <a name="packet-header-nx_packet"></a>NX_PACKET nagłówka pakietu
Domyślnie NetX umieszcza nagłówek pakietu bezpośrednio przed obszarem ładunku pakietu. Pula pamięci pakietu jest zasadniczo serią pakietów — nagłówkami, a następnie bezpośrednio przez ładunek pakietu. Nagłówek pakietu (***NX_PACKET***) i układ puli pakietów są przedstawiane na rysunku 3.

W przypadku sterownika urządzeń sieciowych, który jest w stanie wykonać zero operacji kopiowania, zazwyczaj adres początkowy obszaru ładunku pakietu jest zaprogramowany do logiki DMA. Niektóre aparaty DMA mają wymagania dotyczące wyrównania w obszarze ładunku.

> [!IMPORTANT]
> * Sterownik sieciowy musi wywołać funkcję ***nx_packet_transmit_release** _, gdy transmisja pakietu zostanie zakończona. Ta funkcja sprawdza, czy pakiet nie jest częścią kolejki wyjściowej TCP, zanim zostanie w rzeczywistości umieszczony w dostępnej puli. Nieoczekiwane wywołanie tej funkcji może spowodować nieprzewidywalną behavior._

![Układ nagłówka i puli pakietów](./media/user-guide/packet-header-packet-pool-layout.png)

**RYSUNEK 3. Układ nagłówka i puli pakietów**

Pola nagłówka pakietu są zdefiniowane, jak pokazano w poniższej tabeli. Należy zauważyć, że ta tabela nie jest kompletną listą wszystkich elementów członkowskich w strukturze *NX_PACKET* .

| Nagłówek pakietu          | Przeznaczenie                                                                                                                                                                                                                                                                                                                            |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *nx_packet_pool_owner*   | To pole wskazuje pulę pakietów, do której należy ten konkretny pakiet. Po wydaniu pakiet jest on wydawany do tej określonej puli. Mając własność puli wewnątrz każdego pakietu, istnieje możliwość, że datagram obejmuje wiele pakietów z wielu pul pakietów.                                                         |
| *nx_packet_next*         | To pole wskazuje następny pakiet w obrębie tej samej ramki. Jeśli wartość jest równa NULL, nie ma dodatkowych pakietów, które są częścią ramki. |
| *nx_packet_last*         | To pole wskazuje ostatni pakiet w ramach tego samego pakietu sieciowego. Jeśli wartość jest równa NULL, ten pakiet reprezentuje cały pakiet sieciowy.  |
| *nx_packet_length*       | To pole zawiera łączną liczbę bajtów w całym pakiecie sieciowym, w tym łączną liczbę wszystkich bajtów we wszystkich pakietach połączonych przez element członkowski *nx_packet_next* . |
| *nx_packet_ip_interface* | To pole jest blokiem sterowania interfejsem przypisanym do pakietu, gdy jest odbierany przez sterownik interfejsu i przez NetX dla pakietów wychodzących. Blok sterowania interfejsem opisuje interfejs, np. adres sieciowy, adres MAC, adres IP i stan interfejsu, takie jak link włączony i wymagane jest mapowanie fizyczne. |
| *nx_packet_data_start*   | To pole wskazuje początek obszaru fizycznego ładunku tego pakietu. Nie musi ona występować bezpośrednio po nagłówku NX_PACKET, ale jest to wartość domyślna dla usługi ***nx_packet_pool_create*** . |
| *nx_packet_data_end*     | To pole wskazuje koniec obszaru fizycznego ładunku tego pakietu. Różnica między tym polem a polem nx_packet_data_start reprezentuje rozmiar ładunku. |
| *nx_packet_prepend_ptr*  | To pole wskazuje lokalizację, w której dane pakietów, nagłówek protokołu lub rzeczywiste dane, są dodawane przed istniejącymi danymi pakietu (jeśli istnieją) w obszarze ładunku pakietu. Wartość musi być większa niż lub równa *nx_packet_data_start* lokalizacji wskaźnika i mniejsza lub równa *nx_packet_append_ptr* wskaźnika.  *Ze względu na wydajność NetX zakłada, że gdy pakiet jest przekazywany do usługi NetX Services do transmisji, wskaźnik poprzedź wskazuje na długi adres wyrównany do wyrazu.* |
| *nx_packet_append_ptr*    | To pole wskazuje koniec danych znajdujących się obecnie w obszarze ładunku pakietu. Musi znajdować się między lokalizacją pamięci wskazywaną przez *nx_packet_prepend_ptr* i *nx_packet_data_end*. Różnica między tym polem a polem *nx_packet_prepend_ptr* reprezentuje ilość danych w tym pakiecie. |
| *nx_packet_fragment_next* | To pole jest używane do przechowywania pofragmentowanych pakietów do momentu, w którym cały pakiet będzie można ponownie połączyć. |
| *nx_packet_pad*           | Te pola definiują długość wypełnienia w przypadku wyrazów 4-bajtowych w celu osiągnięcia wymaganego wymagania dotyczącego wyrównania. To pole jest usuwane, jeśli nie zdefiniowano *NX_PACKET_HEADER_PAD* . |
|  |  |

### <a name="packet-header-offsets"></a>Przesunięcia nagłówka pakietu

Rozmiar nagłówka pakietu jest zdefiniowany w celu zapewnienia wystarczającej ilości miejsca, aby pomieścić rozmiar nagłówka. Usługa *nx_packet_allocate* jest używana do przydzielania pakietu i dostosowywania wskaźnika dołączania w pakiecie zgodnie z typem określonego pakietu. Typ pakietu informuje NetX o przesunięciu wymaganym do wstawienia nagłówka protokołu (na przykład UDP, TCP lub ICMP) przed danymi protokołu.

Następujące typy są zdefiniowane w NetX w celu uwzględnienia nagłówka IP i nagłówek warstwy fizycznej (Ethernet) w pakiecie. W drugim przypadku zakłada się, że jest to 16 bajtów z uwzględnieniem wymaganego 4-bajtowego wyrównania. Pakiety IP są nadal zdefiniowane w NetX for Applications do alokowania pakietów dla sieci IP. W poniższej tabeli przedstawiono zdefiniowane symbole:

| Typ pakietu   | Wartość |
|---------------|-------|
| NX_IP_PACKET  | 0x24  |
| NX_UDP_PACKET | 0x2c  |
| NX_TCP_PACKET | 0x38  |
|               |       |

### <a name="pool-capacity"></a>Pojemność puli
Liczba pakietów w puli pakietów jest funkcją rozmiaru ładunku i łączną liczbą bajtów w obszarze pamięci dostarczonym do usługi tworzenia puli pakietów. Pojemność puli jest obliczana przez podzielenie rozmiaru pakietu (w tym rozmiaru nagłówka NX_PACKET, rozmiaru ładunku i właściwego wyrównania) do całkowitej liczby bajtów w podanym obszarze pamięci.

### <a name="thread-suspension"></a>Zawieszenie wątku
Wątki aplikacji mogą wstrzymywać się podczas oczekiwania na pakiet z pustej puli. Gdy pakiet jest zwracany do puli, zawieszony wątek zostaje przyznany i wznowiony.

Jeśli wiele wątków jest zawieszonych w tej samej puli pakietów, zostaną wznowione w kolejności, w której zostały wstrzymane (FIFO).

### <a name="pool-statistics-and-errors"></a>Statystyki i błędy puli
Jeśli ta opcja jest włączona, **Błędy** oprogramowania do zarządzania pakietami NetX śledzą kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla pul pakietów są obsługiwane następujące raporty statystyczne i błędy:

* Łączna liczba pakietów w puli
* Bezpłatne pakiety w puli
* Puste żądania alokacji puli
* Zawieszanie pustej alokacji puli
* Nieprawidłowe wersje pakietów

Wszystkie te statystyki i raporty o błędach, z wyjątkiem całkowitej i bezpłatnej liczby pakietów w puli, są wbudowane w bibliotekę NetX, chyba że określono ***NX_DISABLE_PACKET_INFO** _. Te dane są dostępne dla aplikacji za pomocą usługi _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>NX_PACKET_POOL bloku kontroli puli pakietów

Charakterystyka każdej puli pamięci pakietów znajduje się w bloku sterowania. Zawiera on przydatne informacje, takie jak połączona lista bezpłatnych pakietów, Liczba bezpłatnych pakietów i rozmiar ładunku dla pakietów w tej puli. Ta struktura jest zdefiniowana w pliku *nx_api. h* .

Bloki sterujące puli pakietów mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną przez definiowanie jej poza zakresem dowolnej funkcji.

## <a name="ip-protocol"></a>Protokół IP

Składnik protokołu internetowego (IP) NetX jest odpowiedzialny za wysyłanie i otrzymywanie pakietów IP w Internecie. W NetX jest to składnik, który jest ostatecznie odpowiedzialny za wysyłanie i otrzymywanie komunikatów TCP, UDP, ICMP i IGMP przy użyciu podstawowego sterownika sieciowego.

NetX obsługuje protokół IP (RFC 791)

### <a name="ip-addresses"></a>Adresy IP

Każdy host w Internecie ma unikatowy identyfikator 32-bitowy o nazwie adres IP. Istnieje pięć klas adresów IP, zgodnie z opisem na rysunku 4. Zakresy pięciu klas adresów IP są następujące:

| Klasa | Zakres                        |
|-------|------------------------------|
| A     | od 0.0.0.0 do 127.255.255.255   |
| B     | 128.0.0.0 do 191.255.255.255 |
| C     | 192.0.0.0 do 223.255.255.255 |
| D     | od 224.0.0.0 do 239.255.255.255 |
| E     | 240.0.0.0 do 247.255.255.255 |

**7 bitów 24 bity**

![Struktura adresów IP](./media/user-guide/ip-address-structure.png)

**RYSUNEK 4. Struktura adresów IP**

Istnieją również trzy typy specyfikacji adresów: *emisja pojedyncza*, *emisja* i *Multiemisja*. Adresy emisji pojedynczej to adresy IP, które identyfikują określonego hosta w Internecie. Adresy emisji pojedynczej mogą być źródłem lub docelowym adresem IP. Adres emisji identyfikuje wszystkie hosty w określonej sieci lub podsieci i może być używany tylko jako adresy docelowe. Adresy emisji są określane przez posiadanie części adresu hosta ustawionej na wartość. Adresy multiemisji (Klasa D) określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączać się i zostawiać w dowolnym momencie.

> [!IMPORTANT]
> *Tylko protokoły bezpołączeniowe, takie jak UDP za pośrednictwem protokołu IP, mogą korzystać z emisji i ograniczonej możliwości emisji grupy multiemisji.*

> [!IMPORTANT]
> *Makro* IP_address *jest zdefiniowany w*  * **nx_api. h** _. Umożliwia łatwą specyfikację adresów IP przy użyciu przecinków zamiast kropek. Na przykład IP_ADDRESS (128, 0, 0, 0) _specifies pierwszy adres klasy B przedstawiony na rysunku 4. *

### <a name="ip-gateway-address"></a>Adres bramy IP

Bramy sieci ułatwiają hostom w ich sieciach przekazywanie pakietów przeznaczonych do miejsc docelowych poza domeną lokalną. Każdy węzeł ma pewną wiedzę na temat tego, w którym następnym przeskoku ma być wysyłany, do lokalizacji docelowej jednego z jej sąsiadów lub za pomocą wstępnie zaprogramowanej tabeli routingu statycznego. Jeśli jednak te podejścia zakończą się niepowodzeniem, węzeł powinien przekazać pakiet do bramy domyślnej, która zawiera więcej informacji na temat sposobu kierowania pakietu do jego miejsca docelowego. Należy pamiętać, że brama domyślna musi być bezpośrednio dostępna za pomocą jednego z interfejsów fizycznych dołączonych do wystąpienia protokołu IP. Aplikacja wywołuje ***nx_ip_gateway_address_set*** , aby skonfigurować adres IP bramy domyślnej.

### <a name="ip-header"></a>Nagłówek IP

Każdy pakiet IP do wysłania przez Internet musi mieć nagłówek IP. Gdy protokoły wyższego poziomu (UDP, TCP, ICMP lub IGMP) wywołują składnik IP w celu wysłania pakietu, moduł przesyłania IP umieszcza nagłówek IP przed danymi. Z drugiej strony, gdy pakiety IP są odbierane z sieci, składnik IP usuwa nagłówek IP z pakietu przed dostarczeniem do protokołów wyższego poziomu. Rysunek 5 przedstawia format nagłówka IP.

![Format nagłówka adresu IP](./media/user-guide/ip-header-format.png)

**RYSUNEK 5. Format nagłówka adresu IP**

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji TCP/IP mają być w formacie big endian. W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym. Na przykład 4-bitowa wersja i 4-bitowe długości nagłówka IP muszą znajdować się na pierwszym bajcie nagłówka.*

Pola nagłówka IP są zdefiniowane w następujący sposób:

**Cel pola nagłówka adresu IP**

***4-bitowa wersja*** To pole zawiera wersję protokołu IP reprezentowanego przez ten nagłówek. W przypadku protokołu IP w wersji 4, który jest obsługiwany przez NetX, wartość tego pola to 4.

***4-bitowa Długość nagłówka*** To pole określa liczbę 32-bitowych wyrazów w nagłówku IP. Jeśli nie ma żadnych opcji, wartość dla tego pola to 5.

***8-bitowy typ usługi (TOS)*** To pole określa typ usługi żądany dla tego pakietu IP. Prawidłowe żądania są następujące:

| **Żądanie OT**     | **Wartość** |
| ------------------- | --------- |
| Normalne              | 0x00      |
| Minimalne opóźnienie       | 0x10      |
| Maksymalne dane        | 0x08      |
| Maksymalna niezawodność | 0x04      |
| Koszt minimalny        | 0x02      |

***16-bitowa łączna długość*** To pole zawiera łączną długość datagramu IP w bajtach, z uwzględnieniem nagłówka IP. Datagram IP to podstawowa jednostka informacji dostępnych w Internecie TCP/IP. Zawiera adres docelowy i źródłowy oprócz danych. Ponieważ jest to pole 16-bitowe, maksymalny rozmiar datagramu IP to 65 535 bajtów.

***Identyfikacja 16-bitowa*** Pole to numer używany do unikatowego identyfikowania każdego datagramu IP wysyłanego z hosta. Ta liczba jest zwykle zwiększana po wysłaniu datagramu IP. Jest to szczególnie przydatne w przypadku asemblera odebranych fragmentów pakietów IP.

***flagi 3-bitowe*** To pole zawiera informacje o fragmentacji adresów IP. Bit 14 to bit "Nie fragmentuj". Jeśli ten bit jest ustawiony, wychodzący datagram IP nie zostanie pofragmentowany. Bit 13 to bit "więcej fragmentów". Jeśli ten bit jest ustawiony, zawiera więcej fragmentów. Jeśli ten bit jest wyczyszczony, jest to ostatni fragment pakietu IP.

**Cel pola nagłówka adresu IP**

***13-bitowe przesunięcie fragmentu*** To pole zawiera górne 13 bitów przesunięcia fragmentu. Z tego powodu przesunięcia fragmentów są dozwolone tylko dla granic 8-bajtowych. Pierwszy fragment pofragmentowanego datagramu IP będzie miał ustawiony bit "więcej fragmentów" i ma przesunięcie 0.

***8-bitowy czas wygaśnięcia (TTL)*** To pole zawiera liczbę routerów, które mogą być przekazywane przez ten datagram, co ogranicza okres istnienia datagramu.

***Protokół 8-bitowy*** To pole określa, który protokół korzysta z datagramu IP. Poniżej znajduje się lista prawidłowych protokołów i ich wartości:

| Protokół | Wartość |
|----------|-------|
| ICMP     | 0x01  |
| IGMP     | 0x02  |
| TCP      | 0X06  |
| UDP      | 0X11  |
|          |       |


***16-bitowa suma kontrolna*** To pole zawiera 16-bitową sumę kontrolną obejmującą tylko nagłówek IP. Istnieją dodatkowe sumy kontrolne w protokołach wyższego poziomu, które obejmują ładunek IP.

***32-bitowy źródłowy adres IP*** To pole zawiera adres IP nadawcy i zawsze jest adresem hosta.

***32-bitowy docelowy adres IP*** To pole zawiera adres IP odbiorcy lub odbiorników, jeśli adres jest adresem emisji lub multiemisji.

### <a name="creating-ip-instances"></a>Tworzenie wystąpień adresów IP

Wystąpienia adresów IP są tworzone podczas inicjowania lub podczas wykonywania przez wątki aplikacji. Początkowy adres IP, maska sieci, domyślna pula pakietów, sterownik nośnika oraz rozmiar pamięci i priorytet wewnętrznego wątku IP są zdefiniowane przez usługę *nx_ip_create* . Jeśli aplikacja inicjuje wystąpienie IP z ustawionym adresem IP na nieprawidłowy adres (0.0.0.0), zakłada się, że adres interfejsu jest rozpoznawany przez ręczną konfigurację później, za pośrednictwem RARP lub za pośrednictwem protokołu DHCP lub podobnych protokołów.

W przypadku systemów z wieloma interfejsami sieciowymi interfejs podstawowy jest wyznaczany podczas wywoływania *nx_ip_create*. Każdy dodatkowy interfejs można dołączyć do tego samego wystąpienia IP, wywołując *nx_ip_interface_attach*. Ta usługa przechowuje informacje o interfejsie sieciowym (takim jak adres IP, maska sieci) w bloku sterowania interfejsem i kojarzy wystąpienie sterownika z blokiem sterowania interfejsem w wystąpieniu protokołu IP. Ponieważ sterownik odbiera pakiet danych, musi przechowywać informacje o interfejsie w strukturze NX_PACKET przed przekazaniem ich do logiki odbioru adresów IP. Przed dołączeniem interfejsów należy pamiętać o utworzeniu wystąpienia adresu IP.

 ### <a name="ip-send"></a>Wysyłanie IP
 Przetwarzanie wysyłania IP w NetX jest bardzo usprawnione.

Wskaźnik dołączania w pakiecie jest przenoszony do tyłu w celu uwzględnienia nagłówka IP. Nagłówek IP zostanie ukończony (ze wszystkimi opcjami określonymi przez warstwę protokołu wywołującego), suma kontrolna adresu IP jest obliczana w wierszu, a pakiet jest wysyłany do skojarzonego sterownika sieciowego. Ponadto wychodząca fragmentacja jest również koordynowana z poziomu przetwarzania wysyłania adresów IP.

W przypadku protokołu IP NetX inicjuje żądania ARP, jeśli do docelowego adresu IP jest wymagana mapowanie fizyczne.

> [!IMPORTANT]
> *W przypadku połączeń IP pakiety wymagające rozpoznawania adresów IP (tj. mapowanie fizyczne) są umieszczane w kolejce protokołu ARP do momentu, aż liczba pakietów w kolejce przekroczy głębokość kolejki ARP (zdefiniowana przez* *Symbol **NX_ARP_MAX_QUEUE_DEPTH**). Jeśli* *osiągnięto głębokość kolejki, NetX usunie najstarszy pakiet w kolejce i kontynuuje oczekiwanie na rozpoznanie adresu dla pozostałych pakietów w kolejce. Z drugiej strony, Jeśli wpis ARP nie zostanie rozwiązany, oczekujące pakiety we wpisie ARP zostaną wydane po upływie limitu czasu wpisu ARP.*

W przypadku systemów z wieloma interfejsami sieciowymi NetX wybiera interfejs oparty na docelowym adresie IP. Poniższa procedura dotyczy procesu wyboru:

1. Jeśli adres docelowy to emisja IP lub Multiemisja, a jeśli określono prawidłowy interfejs wychodzący, należy użyć tego interfejsu. W przeciwnym razie używany jest pierwszy interfejs fizyczny.

2. Jeśli w statycznej tabeli routingu zostanie znaleziony adres docelowy, używany jest interfejs skojarzony z bramą.

3. Jeśli miejsce docelowe jest połączone z linkiem, używany jest interfejs on-link.

4. Jeśli adres docelowy jest adresem sprzężenia zwrotnego 127.0.0.1, używany jest interfejs sprzężenia zwrotnego.

5. Jeśli Brama domyślna jest prawidłowo skonfigurowana, użyj interfejsu skojarzonego z bramą domyślną, aby przesłać pakiet.

6. Pakiet wyjściowy jest usuwany w przypadku powyższego poziomu.

### <a name="ip-receive"></a>Odbieranie adresów IP

Przetwarzanie odbierania adresów IP jest wywoływane ze sterownika sieci lub wewnętrznego wątku IP (na potrzeby przetwarzania pakietów w odroczonej kolejce odebranych pakietów). Przetwarzanie odbierania adresów IP bada pole Protokół i próbuje wysłać pakiet do odpowiedniego składnika protokołu. Zanim pakiet zostanie faktycznie wysłany, Nagłówek IP zostanie usunięty przez przeciąganie wskaźnika dołączania do nagłówka IP.

Przetwarzanie odbierania adresów IP również wykrywa pofragmentowane pakiety IP i wykonuje niezbędne kroki, aby ponownie je połączyć w przypadku włączenia fragmentacji. Jeśli fragmentacja jest potrzebna, ale nie jest włączona, pakiet zostanie porzucony.

NetX określa odpowiedni interfejs sieciowy w oparciu o interfejs określony w pakiecie. Jeśli interfejs pakietu ma wartość NULL, NetX domyślnie interfejs podstawowy. Jest to realizowane w celu zagwarantowania zgodności ze starszymi sterownikami NetX Ethernet.

### <a name="raw-ip-send"></a>Wysyłanie nieprzetworzonego adresu IP

Pakiet Raw IP jest ramką IP, która zawiera ładunek protokołu warstwy wyższej nie jest bezpośrednio obsługiwany (i przetwarzany) przez NetX. Pakiet Raw umożliwia deweloperom Definiowanie własnych aplikacji opartych na protokole IP. Aplikacja może wysyłać pakiety pierwotnych adresów IP bezpośrednio przy użyciu usługi ***nx_ip_raw_packet_send** _, jeśli w usłudze _*_nx_ip_raw_packet_enabled_*_ włączono przetwarzanie pakietów pierwotnych adresów IP. Jeśli adres docelowy jest adresem multiemisji lub emisji, NetX Domyślnie pierwszy (podstawowy) interfejs. W związku z tym, aby wysłać takie pakiety w interfejsach pomocniczych, aplikacja musi używać usługi _ *_nx_ip_raw_packet_interface_send_**, aby określić adres źródłowy do użycia dla pakietu wychodzącego.

### <a name="raw-ip-receive"></a>Nieprzetworzony adres IP

Jeśli przetwarzanie pakietów pierwotnych adresów IP jest włączone, aplikacja może odbierać pakiety pierwotnych adresów IP za pomocą usługi ***nx_ip_raw_packet_receive** _. Wszystkie pakiety przychodzące są przetwarzane zgodnie z protokołem określonym w nagłówku IP. Jeśli protokół określa UDP, TCP, IGMP lub ICMP, NetX przetworzy pakiet przy użyciu odpowiedniego programu obsługi dla typu protokołu pakietu. Jeśli protokół nie jest jednym z tych protokołów, a odbieranie pierwotnego adresu IP jest włączone, pakiet przychodzący zostanie umieszczony w kolejce pakietów nieprzetworzonych, oczekując na uzyskanie przez aplikację za pośrednictwem _ *_nx_ip_raw_packet_receive_** usługi. Ponadto wątki aplikacji mogą wstrzymywać z opcjonalnym limitem czasu podczas oczekiwania na pakiet Raw IP.

### <a name="default-packet-pool"></a>Domyślna pula pakietów

Każde wystąpienie IP otrzymuje domyślną pulę pakietów podczas tworzenia. Ta Pula pakietów służy do przydzielania pakietów dla protokołów ARP, RARP, ICMP, IGMP, różnych pakietów kontroli TCP (takich jak SYN, ACK). Jeśli domyślna pula pakietów jest pusta, gdy NetX wymaga przydzielenia pakietu, NetX może być konieczne przerwanie określonej operacji i zwrócenie komunikatu o błędzie, jeśli jest to możliwe.

### <a name="ip-helper-thread"></a>Wątek pomocnika IP

Każde wystąpienie protokołu IP ma wątek pomocnika. Ten wątek jest odpowiedzialny za obsługę całego odroczonego przetwarzania pakietów i całego przetwarzania okresowego. Wątek pomocnika IP jest tworzony w ***nx_ip_create.*** Jest to miejsce, w którym wątek otrzymuje swój stos i priorytet. Należy zauważyć, że pierwsze przetwarzanie w wątku pomocnika IP to zakończenie inicjowania sterownika sieci skojarzonego z usługą IP Create. Po zakończeniu inicjalizacji sterownika sieci wątek pomocniczy uruchamia nieskończoną pętlę, aby przetwarzać pakiety i okresowo żądania.

> [!IMPORTANT]
> *Jeśli w wątku pomocnika adresów IP jest widoczne niewyjaśnione zachowanie, zwiększenie rozmiaru stosu w trakcie tworzenia usługi IP to pierwszy krok debugowania. Jeśli stos jest za mały, wątek pomocnika IP może spowodować zastępowanie pamięci, co może prowadzić do nietypowych problemów.*

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać podczas próby odbierania pakietów pierwotnych adresów IP. Po odebraniu pakietu RAW nowy pakiet jest przyznany do pierwszego wątku zawieszanego i ten wątek zostaje wznowiony. Usługi NetX dla wszystkich odbieranych pakietów mają opcjonalny limit czasu zawieszenia. Po odebraniu pakietu lub upływie limitu czasu wątek aplikacji zostaje wznowiony z odpowiednim stanem ukończenia.

### <a name="ip-statistics-and-errors"></a>Statystyka i błędy adresów IP

Jeśli ta opcja jest włączona, NetX śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia IP są obsługiwane następujące raporty statystyczne i błędy:

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

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_ip_info_get*** .

### <a name="ip-control-block-nx_ip"></a>NX_IP bloku kontroli adresów IP

Charakterystyka każdego wystąpienia IP znajduje się w jego bloku sterowania. Zawiera ona przydatne informacje, takie jak adresy IP i maski sieci poszczególnych urządzeń sieciowych, a także tabela z oddzielnym adresem IP sąsiada i fizycznymi adresami sprzętowymi. Ta struktura jest zdefiniowana w ***nx_api. h*** bloki sterujące wystąpieniem IP mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną, definiując ją poza zakresem dowolnej funkcji.

### <a name="static-ip-routing"></a>Statyczny routing adresów IP

Funkcja statycznego routingu umożliwia aplikacji określenie adresu IP sieci i następnego przeskoku dla określonych poza siecią docelowych adresów IP. Jeśli routing statyczny jest włączony, NetX wyszukuje w statycznej tabeli routingu wpis pasujący do adresu docelowego pakietu do wysłania. Jeśli nie zostanie znalezione dopasowanie, NetX przeszukuje listę interfejsów fizycznych i wybiera źródłowy adres IP i adres następnego przeskoku na podstawie docelowego adresu IP i maski sieci. Jeśli miejsce docelowe nie jest zgodne z żadnym z adresów IP sterowników sieciowych dołączonych do wystąpienia IP, NetX wybiera interfejs, który jest bezpośrednio połączony z bramą domyślną, i używa adresu IP interfejsu jako adresu źródłowego i bramy domyślnej jako następnego przeskoku.

Wpisy można dodawać i usuwać z tabeli routingu statycznego odpowiednio przy użyciu ***nx_ip_static_route_add*** i ***nx_ip_static_route_delete** _ usług. Aby można było używać routingu statycznego, aplikacja hosta musi włączyć tę funkcję, definiując _ *_NX_ENABLE_IP_STATIC_ROUTING_*. *

> [!IMPORTANT]
> *Podczas dodawania wpisu do statycznej tabeli routingu NetX sprawdza pasujący wpis dla określonego adresu docelowego, który znajduje się już w tabeli. Jeśli taki istnieje, zapewnia preferencję dla wpisu z mniejszą siecią (dłuższym prefiksem) w masce sieci.*

### <a name="ip-fragmentation"></a>Fragmentacja IP

Urządzenie sieciowe może mieć limity rozmiaru pakietów wychodzących. Ten limit jest określany jako maksymalna jednostka transmisji (MTU). Jednostka MTU protokołu IP to największy rozmiar ramki IP, który sterownik warstwy linku jest w stanie przesłać bez fragmentacji pakietu IP. Podczas fazy inicjowania sterownika urządzenia moduł sterownika musi skonfigurować jego rozmiar jednostki MTU dla adresu IP za pośrednictwem usługi ***nx_ip_interface_mtu_set**. *

Chociaż nie jest to zalecane, aplikacja może generować datagramy większe niż bazowa Jednostka MTU IP obsługiwana przez urządzenie. Przed przesłaniem takiego datagramu IP warstwa IP musi być pofragmentowana tych pakietów. W przypadku odebrania pofragmentowanych ramek IP na końcu musi być przechowywane wszystkie pofragmentowane ramki IP o tym samym IDENTYFIKATORze fragmentacji, a następnie ponownie nastąpić ich umieszczenie w określonej kolejności. Jeśli logika odbierania IP nie może zebrać wszystkich fragmentów, aby przywrócić pierwotną ramkę IP w czasie, wszystkie fragmenty zostaną wydane. Jest on do protokołu warstwy wyższej, aby wykryć tę utratę pakietów i odzyskać ją z niej.

Aby można było obsługiwać fragmentację i operacje ponownego montażu IP, projektant systemu musi włączyć funkcję fragmentacji IP w NetX przy użyciu usługi ***nx_ip_fragment_enable*** . Jeśli ta funkcja nie jest włączona, przychodzące pofragmentowane pakiety IP są odrzucane, a także pakiety, które przekraczają jednostkę MTU sterownika sieci.

> [!IMPORTANT]
> *Logikę fragmentacji adresów IP można całkowicie usunąć, definiując*  * **NX_DISABLE_FRAGMENTATION** _ _when kompilowania biblioteki theNetX. Wykonanie tej czynności pomaga zmniejszyć rozmiar kodu NetX. *

## <a name="address-resolution-protocol-arp-in-ip"></a>Protokół ARP (Address Resolution Protocol) w adresie IP

Protokół ARP (Address Resolution Protocol) jest odpowiedzialny za dynamiczne mapowanie 32-bitowych adresów IP na podstawowe nośniki fizyczne (RFC 826). Ethernet jest najbardziej typowym nośnikiem fizycznym i obsługuje adresy 48-bitowe. Potrzeba protokołu ARP jest określana przez sterownik sieciowy dostarczany do usługi ***nx_ip_create*** . Jeśli wymagane jest mapowanie fizyczne, Sterownik sieciowy musi ustawić flagę ***nx_interface_address_mapping_needed*** w interfejsie logiczna.

### <a name="arp-enable"></a>Włączanie protokołu ARP
Aby protokół ARP działał prawidłowo, musi on być najpierw włączony przez aplikację z usługą ***nx_arp_enable*** . Ta usługa konfiguruje różne struktury danych na potrzeby przetwarzania ARP, w tym tworzenie obszaru pamięci podręcznej ARP z pamięci dostarczonej do usługi ARP Enable.

### <a name="arp-cache"></a>Pamięć podręczna ARP
Pamięć podręczna ARP może być wyświetlana jako tablica wewnętrznych struktur danych mapowania ARP. Każda struktura wewnętrzna może utrzymywać relacje między adresem IP a fizycznym adresem sprzętowym. Ponadto każda struktura danych ma wskaźniki łączy, więc może być częścią wielu połączonych list.

Aplikacja może wyszukiwać adres IP z pamięci podręcznej ARP przez dostarczenie sprzętowego adresu MAC przy użyciu usługi ***nx_arp_ip_address_find** _, jeśli mapowanie istnieje w tabeli ARP. Podobnie usługa _ *_nx_arp_hardware_address_find_** zwraca adres MAC dla danego adresu IP.


### <a name="arp-dynamic-entries"></a>Dynamiczne wpisy ARP

Domyślnie usługa ARP Enable umieszcza wszystkie wpisy w pamięci podręcznej ARP na liście dostępnych dynamicznych wpisów ARP. Dynamiczny wpis ARP jest przypisywany z tej listy przez NetX w przypadku wykrycia żądania wysłania do niemapowanego adresu IP. Po przydzieleniu wpis ARP zostaje skonfigurowany, a żądanie ARP jest wysyłane do nośnika fizycznego.

Wpis dynamiczny może być również utworzony przez ***nx_arp_dynamic_entry_set*** usługi.

> [!IMPORTANT]
> *Jeśli wszystkie dynamiczne wpisy ARP są używane, co najmniej ostatnio używany wpis ARP zostanie zastąpiony nowym mapowaniem.*

### <a name="arp-static-entries"></a>Statyczne wpisy ARP
Aplikacja może również skonfigurować statyczne mapowanie ARP przy użyciu usługi ***nx_arp_static_entry_create*** . Ta usługa przydziela wpis ARP z listy dynamicznego wpisu ARP i umieszcza ją na liście statycznej z informacjami o mapowaniu dostarczanymi przez aplikację. Statyczne wpisy ARP nie mogą być ponownie używane ani przedawnianie. Aplikacja może usunąć wpis statyczny przy użyciu ***nx_arp_static_entry_delete*** usługi.
Aby usunąć wszystkie wpisy statyczne w tabeli ARP, aplikacja może używać ***nx_arp_static_entries_delete*** usługi.

### <a name="automatic-arp-entry"></a>Wpis automatyczny ARP
NetX rejestruje mapowanie adresów IP/MAC elementu równorzędnego po odpowiedzi elementu równorzędnego na żądanie protokołu ARP. NetX implementuje również funkcję automatycznego wpisu ARP, gdzie rejestruje adresy IP równorzędnego mapowania adresów MAC na podstawie niezamówionych żądań ARP z sieci. Ta funkcja umożliwia wypełnienie tabeli ARP informacjami o komunikacji równorzędnej, co zmniejsza opóźnienie potrzebne do przechodzenia przez cykl żądania/odpowiedzi ARP. Jednak minusem z włączaniem automatycznego protokołu ARP polega na tym, że tabela ARP jest w stanie szybko zapełniać się siecią z wieloma węzłami w łączu lokalnym, co ostatecznie doprowadziłoby do zamiany pozycji ARP.

Ta funkcja jest domyślnie włączona. Aby go wyłączyć, biblioteka NetX musi być skompilowana przy użyciu zdefiniowanego symbolu ***NX_DISABLE_ARP_AUTO_ENTRY*** .

### <a name="arp-messages"></a>Komunikaty ARP

Jak wspomniano wcześniej, komunikat żądania ARP jest wysyłany, gdy zadanie IP wykryje, że mapowanie jest niezbędne dla adresu IP. Żądania ARP są wysyłane okresowo (co ***NX_ARP_UPDATE_RATE** _ sekund) do momentu otrzymania odpowiedniej odpowiedzi ARP. Całkowita liczba żądań ARP wynosząca _ *_NX_ARP_MAXIMUM_RETRIES_** przed porzucić próbą ARP. Po odebraniu odpowiedzi ARP skojarzone informacje o adresie fizycznym są przechowywane we wpisie ARP, który znajduje się w pamięci podręcznej.

W przypadku systemów wielodomowych NetX określa, który interfejs wysyła żądania ARP i odpowiedzi na podstawie określonego adresu docelowego.

> [!IMPORTANT]
> *Wychodzące pakiety IP są umieszczane w kolejce, podczas gdy NetX czeka na odpowiedź ARP. Liczba wychodzących pakietów IP* *umieszczonych w kolejce jest definiowana przez stałą*  * **NX_ARP_MAX_QUEUE_DEPTH**. *

NetX reaguje także na żądania ARP z innych węzłów w lokalnej sieci IP. Gdy zostanie wprowadzone zewnętrzne żądanie ARP zgodne z bieżącym adresem IP interfejsu, który odbiera żądanie ARP, NetX kompiluje komunikat odpowiedzi ARP zawierający bieżący adres fizyczny.

Formaty żądań i odpowiedzi Ethernet ARP przedstawiono na rysunku 6 i opisano poniżej:

| Pole żądania/odpowiedzi       | Przeznaczenie    |
|------------------------------|-----------------|
| Adres docelowy sieci Ethernet | To 6-bajtowe pole zawiera adres docelowy odpowiedzi ARP i jest emisją (wszystkie) dla żądań ARP. To pole jest konfiguracją przez sterownik sieciowy. |
| Adres źródłowy sieci Ethernet      | To 6-bajtowe pole zawiera adres nadawcy żądania lub odpowiedzi ARP i jest skonfigurowany przez sterownik sieciowy. |
| Typ ramki                   | To pole 2-bajtowe zawiera typ ramki Ethernet, a w przypadku żądań i odpowiedzi ARP jest to równe 0x0806. Jest to ostatnie pole, za pomocą którego sterownik sieciowy jest odpowiedzialny za konfigurowanie. |
| Typ sprzętu                | To pole 2-bajtowe zawiera typ sprzętu, który jest 0x0001 dla sieci Ethernet. |
| Typ protokołu                | To pole 2-bajtowe zawiera typ protokołu, który jest 0x0800 dla adresów IP. |
| Rozmiar sprzętu                | To pole 1-bajtowe zawiera rozmiar sprzętowy, który jest 6 dla adresów Ethernet. |


![Format pakietu ARP](./media/user-guide/arp-packet-format.png)

**RYSUNEK 6. Format pakietu ARP**

| Pole żądania/odpowiedzi | Przeznaczenie  |
|---|---|
| Rozmiar protokołu | To pole 1-bajtowe zawiera rozmiar adresu IP, czyli 4 dla adresów IP.  |
| Kod operacji | To pole 2-bajtowe zawiera operację dla tego pakietu ARP. W żądaniu ARP jest określana wartość 0x0001, podczas gdy odpowiedź ARP jest reprezentowana przez wartość 0x0002.  |
| Adres Ethernet nadawcy | To 6-bajtowe pole zawiera adres Ethernet nadawcy. |
| Adres IP nadawcy | To pole 4-bajtowe zawiera adres IP nadawcy. |
| Docelowy adres ethernetowy | To pole 6-bajtowe zawiera adres Ethernet docelowy. |
| Docelowy adres IP | To pole 4-bajtowe zawiera adres IP miejsca docelowego. |

> [!IMPORTANT]
> *Żądania i odpowiedzi ARP są pakietami na poziomie sieci Ethernet. Wszystkie inne pakiety TCP/IP są hermetyzowane przez nagłówek pakietu IP.*

> [!IMPORTANT]
> *Oczekuje się, że wszystkie komunikaty ARP w implementacji protokołu TCP/IP mają być w formacie big endian. W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="arp-aging"></a>Przedawnianie protokołu ARP

NetX obsługuje automatyczne unieważnianie wpisów dynamicznego ARP. ***NX_ARP_EXPIRATION_RATE** _specifies liczbę sekund, przez które ustanowiony adres IP dla mapowania fizycznego pozostaje prawidłowy. Po wygaśnięciu wpis ARP zostanie usunięty z pamięci podręcznej ARP. Kolejna próba wysłania do odpowiedniego adresu IP spowoduje powstanie nowego żądania protokołu ARP. Ustawienie _ *_NX_ARP_EXPIRATION_RATE_** na zero powoduje wyłączenie przedawnienia ARP, co jest konfiguracją domyślną.

### <a name="arp-defend"></a>Obrona protokołu ARP

Po odebraniu żądania ARP lub pakietu odpowiedzi ARP, gdy nadawca ma ten sam adres IP, który powoduje konflikt z adresem IP tego węzła, NetX wysyła żądanie ARP dla tego adresu jako obronność. Jeśli pakiet rozwiązywania konfliktów ARP jest odbierany więcej niż raz w ciągu 10 sekund, NetX nie wyśle więcej pakietów obrony. Domyślny interwał 10 sekund można zdefiniować ponownie przez ***NX_ARP_DEFEND_INTERVAL** _. To zachowanie jest zgodne z zasadami określonymi w 2.4 (c) RFC5227. Ponieważ system Windows XP ignoruje anons protokołu ARP jako odpowiedź na sondę ARP, użytkownik może zdefiniować _ *_NX_ARP_DEFEND_BY_REPLY_* *, aby wysłać odpowiedź ARP jako dodatkową obronę.

### <a name="arp-statistics-and-errors"></a>Statystyki i błędy dotyczące protokołu ARP

Jeśli ta opcja jest włączona, oprogramowanie NetX ARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i błędy są obsługiwane dla każdego przetwarzania ARP IP:

- Całkowita liczba wysłanych żądań ARP
- Całkowita liczba odebranych żądań ARP
- Całkowita liczba wysłanych odpowiedzi ARP
- Całkowita liczba odebranych odpowiedzi ARP
- Łączna liczba wpisów dynamicznych ARP
- Łączna liczba wpisów statycznych ARP
- Łączna liczba przestarzałych wpisów ARP
- Całkowita liczba nieprawidłowych komunikatów ARP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_arp_info_get*** .

## <a name="reverse-address-resolution-protocol-rarp-in-ip"></a>Protokół odwrotnego rozpoznawania adresów (RARP) w adresie IP

Protokół odwrotnego rozpoznawania adresów (RARP) to protokół służący do żądania przypisania sieci na 32-bitowe adresy IP hosta (RFC 903). Odbywa się to za pomocą żądania RARP i kontynuuje okresowo, dopóki członek sieci przypisze adres IP do interfejsu sieciowego hosta w odpowiedzi RARP. Aplikacja tworzy wystąpienie IP przez usługę ***nx_ip_create*** z zerowym adresem IP. Jeśli RARP jest włączona przez aplikację, może użyć protokołu RARP, aby zażądać adresu IP z serwera sieciowego dostępnego za pośrednictwem interfejsu, który ma zerowy adres IP.

### <a name="rarp-enable"></a>Włącz RARP

Aby użyć RARP, aplikacja musi utworzyć wystąpienie IP z adresem IP zerowym, a następnie włączyć RARP przy użyciu ***nx_rarp_enable*** usługi. W przypadku systemów wielodomowych co najmniej jedno urządzenie sieciowe skojarzone z wystąpieniem IP musi mieć adres IP równy zero. Przetwarzanie RARP okresowo wysyła komunikaty żądania RARP dla systemu NetX wymagającego adresu IP do momentu otrzymania prawidłowej odpowiedzi RARP z wydzielonym adresem IP w sieci. W tym momencie przetwarzanie RARP zostało zakończone.

Po włączeniu RARP jest on automatycznie wyłączany po rozwiązaniu wszystkich adresów interfejsu. Aplikacja może wymusić zakończenie RARP przy użyciu usługi ***nx_rarp_disable***.

###  <a name="rarp-request"></a>Żądanie RARP

Format pakietu żądania RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku 6 w temacie [komunikaty ARP](#arp-messages). Jedyną różnicą jest pole Typ ramki to 0x8035, a pole *kod operacji* to 3, które wyznacza żądanie RARP. Jak wspomniano wcześniej, żądania RARP będą wysyłane okresowo (co ***NX_RARP_UPDATE_RATE*** sekund) do momentu otrzymania odpowiedzi RARP z przypisanym adresem IP sieci.

> [!IMPORTANT]
> *Oczekuje się, że wszystkie komunikaty RARP w implementacji protokołu TCP/IP będą w formacie big endian. W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="rarp-reply"></a>Odpowiedź RARP

Komunikaty odpowiedzi RARP są odbierane z sieci i zawierają adres IP przypisany do sieci dla tego hosta. Format pakietu odpowiedzi RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku 6. Jedyną różnicą jest pole Typ ramki to 0x8035, a pole *kod operacji* to 4, które wyznacza odpowiedź RARP. Po odebraniu adres IP jest skonfigurowany w wystąpieniu IP, okresowe żądanie RARP jest wyłączone, a wystąpienie protokołu IP jest teraz gotowe do normalnego działania sieci.

W przypadku hostów wielomacierzystych adres IP jest stosowany do żądającego interfejsu sieciowego. Jeśli inne interfejsy sieciowe nadal żądają przypisania adresu IP, okresowa usługa RARP będzie kontynuowana do momentu rozwiązania wszystkich żądań adresów IP interfejsu.

> [!IMPORTANT]
> *Aplikacja nie powinna używać wystąpienia protokołu IP do momentu ukończenia przetwarzania RARP. **Nx_ip_status_check** mogą być używane przez aplikacje w celu oczekiwania na ukończenie RARP. W przypadku systemów wielodomowych aplikacja nie powinna używać interfejsu żądającego do momentu ukończenia przetwarzania RARP w tym interfejsie. Stan adresu IP na urządzeniu pomocniczym można sprawdzić za pomocą usługi **nx_ip_interface_status_check** .*

### <a name="rarp-statistics-and-errors"></a>RARP statystyk i błędów

Jeśli to ustawienie jest włączone, oprogramowanie NetX RARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i błędy są obsługiwane dla każdego RARP IP:

- Całkowita liczba wysłanych żądań RARP
- Całkowita liczba odebranych odpowiedzi RARP
- Całkowita liczba nieprawidłowych komunikatów RARP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_rarp_info_get*** .

## <a name="internet-control-message-protocol-icmp"></a>Protokół ICMP (Internet Control Message Protocol)

Protokół komunikacyjnego sterowania Internetem dla protokołu IP (ICMP) jest ograniczony do przekazywania informacji o błędach i kontroli między członkami sieci IP.

Podobnie jak w przypadku większości innych komunikatów warstwy aplikacji (np. protokołu TCP/IP), komunikaty ICMP są hermetyzowane przez nagłówek IP przy użyciu oznaczenia protokołu ICMP.

### <a name="icmp-statistics-and-errors"></a>Statystyki i błędy protokołu ICMP

Jeśli ta opcja jest włączona, NetX śledzi kilka statystyk ICMP i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i komunikaty o błędach są obsługiwane dla każdego przetworzenia protokołu ICMP IP:

- Całkowita liczba wysłanych poleceń ping protokołu ICMP
- Łączny limit czasu polecenia ping protokołu ICMP
- Całkowita liczba wstrzymanych wątków ping protokołu ICMP
- Całkowita liczba odebranych odpowiedzi ping protokołu ICMP
- Całkowita liczba błędów sumy kontrolnej protokołu ICMP
- Całkowita liczba nieobsłużonych komunikatów protokołu ICMP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_icmp_info_get*** .

### <a name="icmp-enable"></a>Włączanie protokołu ICMP
Przed przetworzeniem komunikatów ICMP przez NetX aplikacja musi wywołać usługę ***nx_icmp_enable*** , aby umożliwić przetwarzanie protokołu ICMP. Po wykonaniu tej czynności aplikacja może wysyłać żądania ping i przychodzące pakiety ping.

### <a name="icmp-echo-request"></a>Żądanie echa ICMP
Żądanie echa to jeden typ komunikatu ICMP, który jest zazwyczaj używany do sprawdzania istnienia określonego węzła w sieci, zgodnie z jego adresem IP hosta. Popularne polecenie ping jest zaimplementowane przy użyciu komunikatów żądania echa ICMP/echo odpowiedzi. Jeśli określony host jest obecny, jego stos sieciowy przetwarza żądanie ping i odpowiedzi z odpowiedzią ping. Rysunek 7. Szczegóły formatu wiadomości ping protokołu ICMP.

![Komunikat ping protokołu ICMP](./media/user-guide/icmp-ping-message.png)

**RYSUNEK 7. Komunikat ping protokołu ICMP**

> [!IMPORTANT]
> *Oczekuje się, że wszystkie komunikaty ICMP w implementacji protokołu TCP/IP będą w formacie big endian. W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

W poniższej tabeli opisano format nagłówka ICMP:

| Pole nagłówka    | Przeznaczenie |
|-----------------|---------------------------------------------------|
| Typ            | To pole określa komunikat ICMP (BITS 31-24). Najczęstsze: 0 echo odpowiedź 8 żądanie echa |
| Kod            | To pole jest specyficzne dla kontekstu w polu Typ (bity 23-16). Dla żądania echa lub Odpowiedz kod jest ustawiony na zero. |
| Suma kontrolna        | To pole zawiera 16-bitową sumę kontrolną łącznej wartości tego komunikatu ICMP, w tym cały nagłówek ICMP, zaczynając od pola typ. Przed wygenerowaniem sumy kontrolnej, pole sumy kontrolnej jest wyczyszczone.                 |
| Identyfikacja  | To pole zawiera wartość identyfikatora identyfikującą hosta; Host powinien używać identyfikatora wyodrębnionego z żądania echa w odpowiedzi echa (bity 31-16). |
| Numer sekwencyjny | To pole zawiera wartość identyfikatora; Host powinien używać identyfikatora wyodrębnionego z żądania echa w odpowiedzi echa (bity 31-16). W przeciwieństwie do pola identyfikatora ta wartość zmieni się w kolejnych żądaniach ECHA z tego samego hosta (bity 15-0). |


### <a name="icmp-echo-response"></a>Odpowiedź echa ICMP
Odpowiedź ping to inny typ komunikatu ICMP, który jest generowany wewnętrznie przez składnik ICMP w odpowiedzi na zewnętrzne żądanie ping. Oprócz potwierdzenia, odpowiedź na polecenie ping zawiera również kopię danych użytkownika dostarczonych w żądaniu ping.

## <a name="internet-group-management-protocol-igmp"></a>Protokół IGMP (Internet Group Management Protocol)

Protokół IGMP (Internet Group Management Protocol) udostępnia urządzenie do komunikowania się z jego sąsiadami i routerami, które zamierzają odebrać lub dołączyć do grupy multiemisji IP (RFC 1112 i RFC 2236). Grupa multiemisji jest zasadniczo dynamicznym zbiorem elementów członkowskich sieci i jest reprezentowana przez adres IP klasy D. Członkowie grupy multiemisji mogą opuścić w dowolnym momencie, a nowi członkowie mogą dołączyć w dowolnym momencie. Koordynacja związana z przyłączaniem i opuszczeniem grupy jest odpowiedzialna za IGMP.

### <a name="igmp-enable"></a>Włączanie IGMP

Przed rozpoczęciem dowolnego działania multiemisji w NetX, aplikacja musi wywoływać usługę ***nx_igmp_enable*** . Ta usługa wykonuje podstawowe inicjowanie protokołu IGMP w przygotowaniu do obsługi żądań multiemisji.

### <a name="multicast-ip-addressing"></a>Adresowanie IP multiemisji

Jak wspomniano wcześniej, adresy multiemisji w rzeczywistości są adresami IP klasy D, jak pokazano na rysunku 4 na stronie 58. Mniejsze 28 bitów adresu klasy D odpowiada IDENTYFIKATORowi grupy multiemisji. Istnieje szereg wstępnie zdefiniowanych adresów multiemisji. Jednak *adres wszystkich hostów* (244.0.0.1) jest szczególnie istotny dla przetwarzania IGMP. *Adres wszystkie hosty* jest używany przez routery do wysyłania zapytań do wszystkich elementów członkowskich multiemisji w celu raportowania, do których grup multiemisji należą.

### <a name="physical-address-mapping-in-ip"></a>Mapowanie adresów fizycznych w adresie IP

Adresy multiemisji klasy D mapują bezpośrednio do fizycznych adresów Ethernet od 01.00.5 e. 00.00.00 do 01.00.5 e. 7F. FF. FF. Mniejsze 23 bity adresu multiemisji IP są mapowane bezpośrednio do mniejszej liczby 23 bitów adresu Ethernet.

### <a name="multicast-group-join"></a>Przyłączanie do grupy multiemisji

Aplikacje, które muszą przyłączyć się do konkretnej grupy multiemisji, mogą to zrobić, wywołując usługę ***nx_igmp_multicast_join*** . Ta usługa śledzi liczbę żądań dołączenia do tej grupy multiemisji. Jeśli jest to pierwsze żądanie aplikacji do dołączenia do grupy multiemisji, raport IGMP jest wysyłany w sieci podstawowej wskazującej zamiar tego hosta do przyłączenia do grupy. Następnie sterownik sieciowy jest wywoływany w celu skonfigurowania nasłuchiwania pakietów z adresem Ethernet dla tej grupy multiemisji.

W systemie wielodostępnym, jeśli grupa multiemisji jest dostępna za pośrednictwem określonego interfejsu, aplikacja użyje ***nx_igmp_multicast_interface_join*** usługi zamiast ***nx_igmp_multicast_join**, * który jest ograniczony do grup multiemisji w sieci podstawowej.

### <a name="multicast-group-leave"></a>Opuszczenie grupy multiemisji

Aplikacje, które muszą opuścić wcześniej dołączoną grupę multiemisji, mogą to zrobić, wywołując usługę ***nx_igmp_multicast_leave*** . Ta usługa zmniejsza liczbę wewnętrzną skojarzoną z tym, ile razy Grupa została przyłączona. Jeśli nie ma żadnych oczekujących żądań dołączenia do grupy, Sterownik sieciowy jest wywoływany, aby wyłączyć nasłuchiwanie pakietów z adresem Ethernet tego grupy multiemisji

### <a name="multicast-loopback"></a>Sprzężenie zwrotne multiemisji

Aplikacja może chcieć odebrać ruch multiemisji pochodzący z jednego ze źródeł w tym samym węźle. Wymaga to, aby składnik multiemisji protokołu IP miał włączoną funkcję sprzężenia zwrotnego przy użyciu ***nx_igmp_loopback_enable*** usługi.

### <a name="igmp-report-message"></a>Komunikat raportu IGMP

Gdy aplikacja jest dołączana do grupy multiemisji, komunikat raportu IGMP jest wysyłany za pośrednictwem sieci, aby wskazać zamiar hosta do przyłączenia do określonej grupy multiemisji. Format komunikatu IGMP jest przedstawiony na rysunku 8. Adres grupy multiemisji jest używany zarówno w komunikacie grupy w komunikacie z raportem IGMP, jak i docelowym adresie IP.

![Komunikat raportu IGMP](./media/user-guide/igmp-report-message.png)

**RYSUNEK 8. Komunikat raportu IGMP**

Na powyższym rysunku (rysunek 8) nagłówek IGMP zawiera pole Version/Type, maksymalny czas odpowiedzi, pole sumy kontrolnej i pole adres grupy multiemisji. W przypadku komunikatów IGMPv1 wartość pola Maksymalny czas odpowiedzi jest zawsze równa zero, ponieważ nie jest to część protokołu IGMPv1. Pole Maksymalny czas odpowiedzi jest ustawiane, gdy host odbierze komunikat IGMP i wyczyszczony, gdy host odbierze komunikat typu raport innego hosta określony przez protokół IGMPv2.

Poniżej opisano format nagłówka IGMP:

| **Pole nagłówka**          | **Cel** |
|-----------------------|--------------------------------------------------------------------|
| Wersja               | To pole określa wersję protokołu IGMP (BITS 31-28).                                                                               |
| Typ                  | To pole określa typ komunikatu IGMP (bity 27 -24).                                                                       |
| Maksymalny czas odpowiedzi | Nieużywane w IGMPv1. W IGMPv2 to pole służy jako maksymalny czas odpowiedzi.                                                      |
| Suma kontrolna              | To pole zawiera 16-bitową sumę kontrolną podsumowania dla komunikatu IGMP rozpoczynającego się od wersji IGMP (bity 0-15). |
| Adres grupy         | 32-bitowy adres IP grupy klasy D |


Komunikaty raportów IGMP są również wysyłane w odpowiedzi na komunikaty zapytania IGMP wysyłane przez router multiemisji. Routery multiemisji okresowo wysyłają komunikaty zapytania, aby zobaczyć, które hosty nadal wymagają członkostwa w grupie. Komunikaty zapytania mają taki sam format, jak komunikat raportu IGMP przedstawiony na rysunku 8. Jedyną różnicą jest to, że typ IGMP jest równy 1, a pole adres grupy jest ustawione na 0. Komunikaty protokołu IGMP są wysyłane do adresu IP *wszystkie hosty* przez router multiemisji. Host, który nadal chce zachować członkostwo w grupie odpowiada, wysyłając inny komunikat raportu IGMP.

> [!IMPORTANT]
> *Oczekuje się, że wszystkie komunikaty w implementacji protokołu TCP/IP będą w formacie **big endian** . W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="igmp-statistics-and-errors"></a>Statystyka i błędy IGMP

Jeśli ta opcja jest włączona, oprogramowanie NetX IGMP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące raporty statystyczne i błędy są obsługiwane dla każdego przetwarzania IGMP IP:

- Całkowita liczba wysłanych raportów IGMP
- Całkowita liczba odebranych zapytań IGMP
- Łączna liczba błędów sum kontrolnych IGMP
- Łączna liczba przyłączonych bieżących grup protokołu IGMP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_igmp_info_get*** .

## <a name="user-datagram-protocol-udp"></a>User Datagram Protocol (UDP)

Protokół UDP (User Datagram Protocol) zapewnia najprostszą formę transferu danych między elementami członkowskimi sieci (RFC 768). Pakiety danych UDP są wysyłane z jednego członka sieci do innego w najlepszym wysiłku. oznacza to, że nie ma wbudowanego mechanizmu potwierdzania przez odbiorcę pakietu. Ponadto wysyłanie pakietu UDP nie wymaga wcześniejszego nawiązania połączenia. Z tego powodu transmisja pakietów UDP jest bardzo wydajna.

### <a name="udp-header"></a>Nagłówek UDP
Protokół UDP umieszcza prosty nagłówek pakietu przed danymi aplikacji podczas transmisji i usuwa podobny nagłówek UDP z pakietu przy odbiorze przed dostarczeniem odebranego pakietu UDP do aplikacji. Protokół UDP korzysta z protokołu IP do wysyłania i otrzymywania pakietów, co oznacza, że na początku nagłówka UDP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 9 przedstawia format nagłówka UDP.

![Nagłówek UDP](./media/user-guide/udp-header.png)

**RYSUNEK 9. Nagłówek UDP**

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji protokołu UDP/IP mają być w formacie big endian. W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

Poniżej opisano format nagłówka UDP:

| Pole nagłówka                   | Przeznaczenie |
|--------------------------------|---------------------------------------------|
| 16-bitowy numer portu źródłowego      | To pole zawiera port, z którego jest wysyłany pakiet UDP. Prawidłowe porty UDP mieszczą się w zakresie od 1 do 0xFFFF. |
| 16-bitowy numer portu docelowego | To pole zawiera port UDP, do którego jest wysyłany pakiet. Prawidłowe porty UDP mieszczą się w zakresie od 1 do 0xFFFF.   |
| 16-bitowa długość protokołu UDP   | To pole zawiera liczbę bajtów w pakiecie UDP, w tym rozmiar nagłówka UDP.                                  |
| 16-bitowa suma kontrolna UDP | To pole zawiera 16-bitową sumę kontrolną pakietu, w tym nagłówek UDP, obszar danych pakietu i nagłówek pseudo IP. |

### <a name="udp-enable"></a>Włączanie protokołu UDP

Przed przekazaniem pakietów UDP aplikacja musi najpierw włączyć protokół UDP, wywołując usługę ***nx_udp_enable*** . Po włączeniu aplikacja jest bezpłatna do wysyłania i odbierania pakietów UDP.

### <a name="udp-socket-create"></a>Tworzenie gniazda UDP

Gniazda UDP są tworzone podczas inicjowania lub podczas wykonywania przez wątki aplikacji. Początkowy typ usługi, czas wygaśnięcia i głębokość kolejki odbierania są zdefiniowane przez usługę ***nx_udp_socket_create*** . Liczba gniazd UDP w aplikacji nie jest ograniczona.

### <a name="udp-checksum"></a>Suma kontrolna UDP

Protokół UDP określa 16-bitową sumę kontrolną, która pokrywa się z pseudo nagłówka adresu IP (składa się ze źródłowego adresu IP, docelowego adresu IP oraz słowa protokołu IP o długości), nagłówka UDP i danych pakietów UDP. Jeśli obliczona suma kontrolna UDP to 0, jest ona przechowywana jako wszystkie (0xFFFF). Jeśli gniazdo wysyłania ma wyłączoną logikę sumy kontrolnej UDP, wartość zero jest umieszczana w polu sumy kontrolnej UDP, aby wskazać, że suma kontrolna nie została obliczona. Jeśli suma kontrolna UDP nie jest zgodna z obliczoną sumą kontrolną przez odbiorcę, pakiet UDP jest po prostu odrzucony.

W sieci IP suma kontrolna UDP jest opcjonalna. NetX umożliwia aplikacji Włączanie lub wyłączanie obliczeń sum kontrolnych UDP na podstawie gniazda. Domyślnie logika sumy kontrolnej gniazda UDP jest włączona. Aplikacja może wyłączyć logikę sumy kontrolnej dla określonego gniazda UDP przez wywołanie usługi ***nx_udp_socket_checksum_disable*** .

Niektóre kontrolery Ethernet mogą generować sumę kontrolną UDP na bieżąco. Jeśli system może korzystać z funkcji obliczeń sum kontrolnych sprzętowych, biblioteka NetX może być skompilowana bez logiki sumy kontrolnej. Aby wyłączyć sumę kontrolną oprogramowania UDP, biblioteka NetX musi być skompilowana z następującymi zdefiniowanymi symbolami: ***NX_DISABLE_UDP_TX_CHECKSUM*** i ***NX_DISABLE_UDP_RX_CHECKSUM **_ (opisane w [rozdziale 2](chapter2.md)). Opcje konfiguracji usuwają logikę sum kontrolnych UDP ze NetX całkowicie, podczas gdy wywołanie _* nx_udp_socket_checksum_disable*** pozwala aplikacji wyłączyć przetwarzanie sum kontrolnych protokołu IP protokołu UDP dla każdego gniazda.

### <a name="udp-ports-and-binding"></a>Porty i powiązania UDP

Port UDP jest logicznym punktem końcowym protokołu UDP. Istnieje 65 535 prawidłowych portów w składniku UDP NetX z zakresu od 1 do 0xFFFF. Aby wysłać lub odebrać dane UDP, aplikacja musi najpierw utworzyć gniazdo UDP, a następnie powiązać ją z żądanym portem. Po powiązaniu gniazda UDP z portem aplikacja może wysyłać i odbierać dane w tym gnieździe.

### <a name="udp-fast-pathtrade"></a>Szybka ścieżka UDP&trade;

Szybka ścieżka UDP &trade; to nazwa małej ścieżki narzutu na pakiety przez implementację protokołu UDP NetX. Wysyłanie pakietu UDP wymaga tylko kilku wywołań funkcji: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_ i ostatecznego wywołania sterownika sieci. _*_nx_udp_socket_send_*_ jest dostępny w NetX dla istniejących aplikacji NetX i ma zastosowanie tylko do pakietów IP. Preferowaną metodą jest jednak użycie _ *_nx_udp_socket_send_** usługi omówionej poniżej. W przypadku odbierania pakietów UDP pakiet UDP jest umieszczany w odpowiedniej kolejce odbioru gniazda UDP lub dostarczany do zawieszonego wątku aplikacji w ramach pojedynczego wywołania funkcji z przetwarzania przerwań odbieranych przez sterownik sieciowy. Ta wysoce zoptymalizowana logika do wysyłania i otrzymywania pakietów UDP jest istotą technologii szybkiego ścieżki UDP.

### <a name="udp-packet-send"></a>Wysyłanie pakietów UDP

Wysyłanie danych UDP za pośrednictwem sieci IP jest łatwo realizowane przez wywołanie funkcji ***nx_udp_socket_send** _. Obiekt wywołujący musi ustawić wersję protokołu IP w polu _IP Address *. NetX określi najlepszy adres źródłowy przesyłanych pakietów UDP na podstawie docelowego adresu IP. Ta usługa umieszcza nagłówek UDP przed danymi pakietu i wysyła je do sieci przy użyciu procedury wysyłania wewnętrznego adresu IP. Nie ma zawieszania wątku podczas wysyłania pakietów UDP, ponieważ wszystkie transporty pakietów UDP są przetwarzane natychmiast.

W przypadku docelowych multiemisji lub emisji aplikacja powinna określić źródłowy adres IP, który ma być używany, jeśli urządzenie NetX ma wiele adresów IP do wyboru. Można to zrobić za pomocą usług ***nx_udp_socket_interface_send.***

> [!IMPORTANT]
> *Jeśli **nx_udp_socket_send** jest używany do przesyłania pakietów multiemisji lub emisji, adres IP pierwszego interfejsu jest używany jako adres źródłowy.*

> [!IMPORTANT]
> *Jeśli dla tego gniazda jest włączona logika sumy kontrolnej UDP, operacja sumy kontrolnej jest wykonywana w kontekście wątku wywołującego bez blokowania dostępu do struktur danych protokołu UDP lub IP.*

> [!NOTE]
> *Dane ładunku UDP znajdujące się w strukturze **NX_PACKET** powinny znajdować się na granicy długiego wyrazu. Aplikacja musi pozostawić wystarczającą ilość miejsca między wskaźnikiem dołączania i wskaźnikiem początkowym danych dla NetX, aby umieścić nagłówki UDP, IP i nośnika fizycznego.*

### <a name="udp-packet-receive"></a>Odbieranie pakietów UDP

Wątki aplikacji mogą odbierać pakiety UDP z określonego gniazda przez wywołanie ***nx_udp_socket_receive***. Funkcja odbioru gniazda udostępnia najstarszy pakiet w kolejce odbioru gniazda. Jeśli w kolejce odbierania nie ma pakietów, wątek wywołujący może zawiesić (z opcjonalnym limitem czasu) do momentu otrzymania pakietu.

Przetwarzanie pakietów protokołu UDP odbierane (zwykle wywoływane z procedury obsługi przerwania odbierania przez sterownik sieciowy) jest odpowiedzialne za umieszczenie pakietu w kolejce odbioru gniazda UDP lub dostarczenie go do pierwszego wstrzymanego wątku oczekującego na pakiet. Jeśli pakiet jest umieszczany w kolejce, przetwarzanie odbiera również sprawdza maksymalną głębokość kolejki odbierania skojarzoną z gniazdem. Jeśli ten nowo umieszczony w kolejce pakiet przekracza głębokość kolejki, najstarszy pakiet w kolejce zostanie odrzucony.

### <a name="udp-receive-notify"></a>Powiadomienie o odebraniu protokołu UDP

Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, należy użyć funkcji ***nx_udp_socket_receive_notify*** . Ta funkcja rejestruje funkcję odbierania pakietów wywołania zwrotnego dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, funkcja wywołania zwrotnego jest wykonywana.

Zawartość funkcji wywołania zwrotnego jest specyficzna dla aplikacji. Jednak najprawdopodobniej zawiera logikę do informowania wątku przetwarzania, że pakiet jest teraz dostępny w odpowiednim gnieździe.

### <a name="peer-address-and-port"></a>Adres i port elementu równorzędnego

W przypadku odebrania pakietu UDP aplikacja może znaleźć adres IP i numer portu nadawcy przy użyciu ***nx_udp_packet_info_extract*** usługi. Po pomyślnym powrocie usługa ta udostępnia informacje o adresie IP nadawcy, numerze portu nadawcy i interfejsie lokalnym, za pomocą którego został odebrany pakiet.

### <a name="thread-suspension"></a>Zawieszenie wątku

Jak wspomniano wcześniej, wątki aplikacji mogą wstrzymywać się podczas próby odebrania pakietu UDP na określonym porcie UDP. Po odebraniu pakietu na tym porcie jest on przyznany do pierwszego wątku, a następnie wznowiony. Opcjonalny limit czasu jest dostępny w przypadku zawieszania pakietu odbioru protokołu UDP, który jest funkcją dostępną dla większości usług NetX.

### <a name="udp-socket-statistics-and-errors"></a>Statystyka i błędy gniazda UDP

Jeśli to ustawienie jest włączone, oprogramowanie NetX UDP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/UDP są obsługiwane następujące raporty statystyczne i błędy:

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

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_udp_info_get*** dla statystyk UDP amassed przez wszystkie gniazda UDP i usługę ***NX_UDP_SOCKET_INFO_GET*** dla statystyk UDP w określonym gnieździe UDP.

### <a name="udp-socket-control-block-nx_udp_socket"></a>Blok sterowania gniazdem UDP NX_UDP_SOCKET

Cechy poszczególnych gniazd UDP są dostępne w skojarzonym bloku sterowania **NX_UDP_SOCKET** . Zawiera użyteczne informacje, takie jak link do struktury danych IP, interfejs sieciowy dla ścieżki wysyłania i odbierania, port powiązany i kolejka odbierania pakietów. Ta struktura jest zdefiniowana w pliku **_nx_api. h_** .

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Transmission Control Protocol (TCP) zapewnia niezawodny transfer danych przesyłanych strumieniowo między dwoma członkami sieci (RFC 793). Wszystkie dane wysyłane z jednego członka sieci są weryfikowane i potwierdzane przez element członkowski odbiorcy. Ponadto dwóch członków musi nawiązać połączenie przed jakimkolwiek transferem danych. Wszystkie te wyniki są niezawodnym transferem danych; jednak wymaga to znacznie więcej obciążenia niż poprzednio opisany w tym transfer danych UDP.

### <a name="tcp-header"></a>Nagłówek TCP

W przypadku przesyłania nagłówek TCP jest umieszczany przed danymi od użytkownika. Przy odbiorze nagłówek TCP zostaje usunięty z przychodzącego pakietu, pozostawiając tylko te dane użytkownika, które są dostępne dla aplikacji. Protokół TCP korzysta z protokołu IP do wysyłania i odbierania pakietów, co oznacza, że na początku nagłówka TCP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 10 przedstawia format nagłówka TCP.

![Nagłówek TCP](./media/user-guide/tcp-header.png)

**RYSUNEK 10. Nagłówek TCP**

Poniżej opisano format nagłówka TCP:

| Pole nagłówka | Przeznaczenie |
|---|---|
| 16-bitowy numer portu źródłowego | To pole zawiera port, na którym jest wysyłany pakiet TCP. Prawidłowe porty TCP mieszczą się w zakresie od 1 do 0xFFFF. |
| 16-bitowy numer portu docelowego | To pole zawiera port TCP, na który jest wysyłany pakiet. Prawidłowe porty TCP mieszczą się w zakresie od 1 do 0xFFFF. |
| 32-bitowy numer sekwencji | To pole zawiera numer sekwencyjny dla danych wysyłanych z tego końca połączenia. Oryginalna sekwencja jest określana podczas początkowej sekwencji połączeń między dwoma węzłami TCP. Każdy transfer danych od tego momentu powoduje zwiększenie liczby sekwencji o ilość wysłanych bajtów. |
| 32-bitowy numer potwierdzenia | To pole zawiera numer sekwencyjny odpowiadający ostatniemu bajtowi odebranemu po tej stronie połączenia. Służy do określenia, czy dane wysłane wcześniej zostały pomyślnie odebrane przez inne zakończenie połączenia. |
| 4-bitowa Długość nagłówka           | To pole zawiera liczbę 32-bitowych wyrazów w nagłówku TCP. Jeśli w nagłówku TCP nie ma żadnych opcji, to pole ma wartość 5. |
| 6-bitowe bity kodu               | To pole zawiera sześć różnych bitów kodu używanych do wskazywania różnych informacji o kontroli skojarzonych z połączeniem. Bity sterujące są zdefiniowane w następujący sposób: |



| Nazwa | Bit | Znaczenie                                                     |
|------|-----|-------------------------------------------------------------|
| URG  | 21  | Pilne dane obecne                                         |
| KOMUNIKATY  | 20  | Numer potwierdzenia jest prawidłowy                             |
| PSH —  | 19  | Natychmiast Obsługuj te dane                                |
| RST  | 18  | Zresetuj połączenie                                        |
| SYN  | 17  | Synchronizuj numery sekwencji (używane do nawiązania połączenia) |
| FIN  | 16  | Nadawca zakończył wysyłanie (używane do zamknięcia połączenia) |

**okno 16-bitowe**

To pole jest używane do sterowania przepływem. Zawiera ilość bajtów, które gniazdo może obecnie odbierać. Ta w istocie jest używana do sterowania przepływem. Nadawca jest odpowiedzialny za upewnienie się, że dane do wysłania mieszczą się w oknie anonsowanym odbiorcy.

| **Pole nagłówka**          | **Cel** |
| ------------------------- | --- |
| **16-bitowa suma kontrolna TCP**   | To pole zawiera 16-bitową sumę kontrolną pakietu, w tym nagłówek TCP, obszar danych pakietu i nagłówek pseudo IP.                |
| **16-bitowy wskaźnik pilny** | To pole zawiera dodatnie przesunięcie ostatniego bajtu pilnych danych. To pole jest prawidłowe tylko wtedy, gdy w nagłówku jest ustawiony bit kodu URG. |

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji TCP/IP mają być w formacie big endian. W tym formacie najbardziej znaczący bajt słowa znajduje się na najniższym adresie bajtowym.*

### <a name="tcp-enable"></a>Włączanie protokołu TCP

Przed przystąpieniem do połączeń TCP i przesyłania pakietów aplikacja musi najpierw włączyć protokół TCP, wywołując usługę nx_tcp_enable. Po włączeniu aplikacja jest bezpłatna, aby uzyskać dostęp do wszystkich usług TCP.

### <a name="tcp-socket-create"></a>Tworzenie gniazda TCP

Gniazda TCP są tworzone podczas inicjowania lub podczas wykonywania przez wątki aplikacji. Początkowy typ usługi, czas wygaśnięcia i rozmiar okna są zdefiniowane przez usługę ***nx_tcp_socket_create*** . W aplikacji nie ma ograniczeń dotyczących liczby gniazd TCP.

### <a name="tcp-checksum"></a>Suma kontrolna TCP

Protokół TCP określa 16-bitową sumę kontrolną, która pokrywa się z pseudo nagłówka IP (składa się ze źródłowego adresu IP, docelowego adresu IP oraz słowa IP protokołu/długości), nagłówka TCP i danych pakietu TCP.

Niektóre kontrolery sieci mogą wykonywać obliczenia sum kontrolnych TCP i walidację sprzętu. W przypadku takich systemów aplikacje mogą chcieć używać logiki sum kontrolnych sprzętowych, jak to możliwe, aby zmniejszyć obciążenie środowiska uruchomieniowego. Aplikacje mogą wyłączać logikę obliczeń sum kontrolnych protokołu TCP z biblioteki NetX w czasie kompilacji, definiując **NX_DISABLE_TCP_TX_CHECKSUM** i **NX_DISABLE_TCP_RX_CHECKSUM**. W ten sposób kod sumy kontrolnej protokołu TCP nie jest kompilowany w.

### <a name="tcp-port"></a>Port TCP

Port TCP jest logicznym punktem połączenia w protokole TCP. Istnieje 65 535 prawidłowych portów w składniku TCP NetX, z zakresu od 1 do 0xFFFF. W przeciwieństwie do protokołu UDP, w którym dane z jednego portu mogą być wysyłane do dowolnego innego portu docelowego, port TCP jest połączony z innym określonym portem TCP i tylko wtedy, gdy połączenie jest nawiązywane, może mieć miejsce transfer danych — i tylko między dwoma portami.

> [!IMPORTANT]
> *Porty TCP są całkowicie niezależne od portów UDP; na przykład port UDP numer 1 nie ma powiązania z portem TCP o numerze 1.*

## <a name="client-server-model"></a>Model Client-Server

Aby można było korzystać z protokołu TCP na potrzeby transferu danych, należy najpierw nawiązać połączenie między dwoma gniazdami TCP. Ustanowienie połączenia odbywa się na serwerze klienta. Po stronie klienta połączenia znajduje się Strona, która inicjuje połączenie, a po stronie serwera po prostu czeka na żądania połączenia klienta przed ukończeniem przetwarzania.

> [!IMPORTANT]
> *W przypadku urządzeń z wieloma domem NetX automatycznie określa adres źródłowy do użycia w połączeniu, a adres następnego przeskoku na podstawie docelowego adresu IP połączenia.*

### <a name="tcp-socket-state-machine"></a>Komputer stanu gniazda TCP

Połączenie między dwoma gniazdami TCP (jeden klient i jeden serwer) jest złożone i jest zarządzane w sposób komputerowy. Każde gniazdo TCP zostanie uruchomione w stanie ZAMKNIĘTYm. Za pośrednictwem zdarzeń połączeń każda maszyna stanu gniazda jest migrowana w stan USTANOWIONy, który jest miejscem, w którym odbywa się zbiorczo transfer danych w protokole TCP. Gdy jedna strona połączenia nie chce już wysyłać danych, zostanie odłączona. Po rozłączeniu z drugą stroną, gdy gniazdo TCP powróci do stanu ZAMKNIĘTEgo. Ten proces jest powtarzany za każdym razem, gdy klient i serwer TCP nawiązują połączenie. Rysunek 11 przedstawia różne stany komputera stanu TCP.

![Stany komputera stanu TCP](./media/user-guide/states-tcp-state-machine.png)

### <a name="figure-11-states-of-the-tcp-state-machine"></a>RYSUNEK 11. Stany komputera stanu TCP

### <a name="tcp-client-connection"></a>Połączenie klienta TCP

Jak wspomniano wcześniej, po stronie klienta połączenia TCP zostaje zainicjowany żądanie połączenia z serwerem TCP. Aby można było wykonać żądanie połączenia, należy włączyć protokół TCP w wystąpieniu adresu IP klienta. Ponadto należy utworzyć gniazdo TCP klienta przy użyciu usługi ***nx_tcp_socket_create** _ i powiązana z portem za pośrednictwem usługi _*_nx_tcp_client_socket_bind_*_ . Gdy gniazdo klienta jest powiązane, usługa _ *_nx_tcp_client_socket_connect_** zostanie użyta do nawiązania połączenia z serwerem TCP. Należy pamiętać, że gniazdo musi być w stanie ZAMKNIĘTYm, aby można było zainicjować próbę połączenia. Ustanowienie połączenia rozpoczyna się od NetX wystawiającego pakiet SYN, a następnie oczekiwanie na zwrotny pakiet SYN ACK z serwera, który oznacza akceptację żądania połączenia. Po otrzymaniu potwierdzenia SYN NetX reaguje na pakiet ACK i promuje gniazdo klienta do stanu ustanowione.

### <a name="tcp-client-disconnection"></a>Odłączanie klienta TCP

Zamykanie połączenia odbywa się przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie określono zawieszenia, gniazdo klienta wysyła do gniazda serwerowego pakiet RST i umieszcza gniazdo w stanie ZAMKNIĘTYm. W przeciwnym razie, jeśli zażądano zawieszenia, zostaje wykonany pełny protokół Disconnect protokołu TCP w następujący sposób:

- Jeśli serwer zainicjował wcześniej żądanie rozłączenia (gniazdo klienta już otrzymał pakiet FIN, odpowiedział na ACK i znajduje się w stanie oczekiwania na zamknięcie), NetX podwyższa stan gniazda TCP klienta do ostatniego potwierdzenia i wysyła pakiet FIN. Następnie czeka na potwierdzenie z serwera przed ukończeniem rozłączenia i przeprowadzeniem stanu ZAMKNIĘTEgo.

- Jeśli z drugiej strony, klient jest pierwszym zainicjowaniem żądania rozłączenia (serwer nie został odłączony, a gniazdo nadal jest w stanie), NetX wysyła pakiet FIN do zainicjowania rozłączenia i czeka na otrzymanie elementu FIN i ACK z serwera przed ukończeniem rozłączenia i umieszczenie gniazda w stanie ZAMKNIĘTYm.

Jeśli w kolejce transmisji gniazda nadal istnieją pakiety, NetX zawiesza się dla określonego limitu czasu, aby umożliwić potwierdzenie pakietów. Jeśli limit czasu wygaśnie, NetX opróżnia kolejkę transmisji gniazda klienta.

Aby usunąć powiązanie portu z gniazda klienta, aplikacja wywołuje ***nx_tcp_client_socket_unbind***. Gniazdo musi znajdować się w stanie ZAMKNIĘTYm lub w trakcie rozłączania (tj. czas oczekiwania na stan) przed zwolnieniem portu; w przeciwnym razie zwracany jest błąd.

Na koniec, jeśli aplikacja nie potrzebuje już gniazda klienta, wywołuje ***nx_tcp_socket_delete*** , aby usunąć gniazdo.

### <a name="tcp-server-connection"></a>Połączenie z serwerem TCP

Po stronie serwera połączenia TCP jest pasywny; oznacza to, że serwer czeka na zainicjowanie żądania połączenia przez klienta. Aby zaakceptować połączenie z klientem, należy najpierw włączyć protokół TCP w wystąpieniu adresu IP, wywołując usługę ***nx_tcp_enable** _. Następnie aplikacja musi utworzyć gniazdo TCP przy użyciu usługi _ *_nx_tcp_socket_create_**.

Należy również skonfigurować gniazdo serwera do nasłuchiwania żądań połączeń. Jest to realizowane za pomocą usługi ***nx_tcp_server_socket_listen*** . Ta usługa umieszcza gniazdo serwera w stanie nasłuchiwania i wiąże określony port serwera z gniazdem.

> [!IMPORTANT]
> *Aby ustawić procedurę wywołania zwrotnego gniazda Socket, aplikacja określa odpowiednią funkcję wywołania zwrotnego dla tcp_listen_callback argumentu usługi **nx_tcp_server_socket_listen** . Ta funkcja wywołania zwrotnego aplikacji jest następnie wykonywana przez NetX za każdym razem, gdy na tym porcie serwera zostanie żądane nowe połączenie. Przetwarzanie w wywołaniu zwrotnym jest pod kontrolą aplikacji.*

Aby akceptować żądania połączenia klienta, aplikacja wywołuje usługę ***nx_tcp_server_socket_accept** _. Gniazdo serwera musi znajdować się w stanie nasłuchiwania lub zostać ODEBRANe (tj. serwer jest w stanie nasłuchiwania i odebrał pakiet SYN z klienta wysyłającego żądanie połączenia) w celu wywołania usługi Accept. Pomyślne zwrócenie stanu z _ *_nx_tcp_server_socket_accept_** wskazuje, że połączenie zostało skonfigurowane i że gniazdo serwera jest w stanie nawiązane.

Gdy gniazdo serwera ma prawidłowe połączenie, dodatkowe żądania połączenia klientów są umieszczane w kolejce do głębokości określonej przez *listen_queue_size*, przekazaną do usługi ***nx_tcp_server_socket_listen** _. W celu przetworzenia kolejnych połączeń na porcie serwera aplikacja musi wywołać _ *_nx_tcp_server_socket_relisten_** z dostępnym gniazdem (tj. gniazdem w stanie zamkniętym). Należy pamiętać, że tego samego gniazda serwerowego można użyć, jeśli poprzednie połączenie skojarzone z gniazdem zostanie zakończone, a gniazdo jest w stanie ZAMKNIĘTYm.

### <a name="tcp-server-disconnection"></a>Odłączanie serwera TCP

Zamykanie połączenia odbywa się przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie określono zawieszenia, gniazdo serwera wysyła do gniazda klienta parametr RST i umieszcza gniazdo w stanie ZAMKNIĘTYm. W przeciwnym razie, jeśli zażądano zawieszenia, zostaje wykonany pełny protokół Disconnect protokołu TCP w następujący sposób: |

- Jeśli klient zainicjował wcześniej żądanie rozłączenia (gniazdo serwera już odebrał pakiet FIN, odpowiedział na ACK i znajduje się w stanie oczekiwania na zamknięcie), NetX podwyższa stan gniazda TCP do ostatniego potwierdzenia i wysyła pakiet FIN. Następnie czeka na potwierdzenie z klienta przed ukończeniem rozłączenia i przeprowadzeniem stanu ZAMKNIĘTEgo.

- Jeśli z drugiej strony, serwer jest pierwszym zainicjowaniem żądania rozłączenia (klient nie został odłączony, a gniazdo nadal jest w stanie), NetX wysyła pakiet FIN do zainicjowania rozłączenia i czeka na odebranie noty i potwierdzenie od klienta przed ukończeniem odłączenia i umieszczenie gniazda w stanie ZAMKNIĘTYm.

Jeśli w kolejce transmisji gniazda nadal istnieją pakiety, NetX zawiesza się dla określonego limitu czasu, aby umożliwić potwierdzenie tych pakietów. Jeśli limit czasu wygaśnie, NetX opróżnia kolejkę transmisji w gnieździe serwera.

Po zakończeniu przetwarzania rozłączenia, gdy gniazdo serwera jest w stanie ZAMKNIĘTYm, aplikacja musi wywoływać usługę ***nx_tcp_server_socket_unaccept*** , aby zakończyć skojarzenie tego gniazda z portem serwera. Należy pamiętać, że ta usługa musi być wywoływana przez aplikację, nawet jeśli ***nx_tcp_socket_disconnect*** lub ***nx_tcp_server_socket_accept** _ zwróci stan błędu. Po powrocie _ *_nx_tcp_server_socket_unaccept_** gniazdo może być używane jako gniazdo klienta lub serwera, a nawet usunięte, jeśli nie jest już potrzebne. Jeśli pożądane jest zaakceptowanie innego połączenia klienta na tym samym porcie serwera, usługa ***nx_tcp_server_socket_relisten*** powinna być wywoływana w tym gnieździe.

Poniższy segment kodu ilustruje sekwencję wywołań typowego serwera TCP używa:

```c
/* Set up a previously created TCP socket to listen on port 12 */

nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1) {

    /* Wait for a client socket connection request for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on the port. */

    nx_tcp_server_socket_unaccept(&server_socket);

    /* Set up server socket to relisten on the same port for the next
    client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>Sprawdzanie poprawności

Maksymalny rozmiar segmentu (Maximum) to maksymalna ilość bajtów odbieranych przez hosta TCP bez fragmentacji przez podstawową warstwę adresów IP. Podczas fazy ustanowienia połączenia TCP oba punkty końcowe wymieniają własną wartość TCP, tak że nadawca nie wyśle segmentu danych TCP, który jest większy niż rozmiar tego odbiorcy. Moduł TCP NetX będzie opcjonalnie sprawdzać anonsowaną wartość tego obiektu równorzędnego przed nawiązaniem połączenia. Domyślnie NetX nie zezwala na takie sprawdzenie. W przypadku aplikacji, które chcą wykonać weryfikację o kluczu, należy zdefiniować ***NX_ENABLE_TCP_MSS_CHECKING** _ podczas kompilowania biblioteki NetX, a wartość minimalna powinna być zdefiniowana w _*_NX_TCP_MSS_MINIMUM_*_. Przychodzące połączenia TCP o wartościach o wielkości/mniej więcej niż _ *_NX_TCP_MSS_MINIMUM_** są porzucane.

### <a name="stop-listening-on-a-server-port"></a>Zatrzymaj nasłuchiwanie na porcie serwera

Jeśli aplikacja nie chce już nasłuchiwać żądań połączenia klienta na porcie serwera, który został wcześniej określony przez wywołanie usługi ***nx_tcp_server_socket_listen** _, aplikacja po prostu wywołuje usługę _ *_nx_tcp_server_socket_unlisten_**. Ta usługa umieszcza wszystkie gniazda oczekujące na połączenie z powrotem w stanie ZAMKNIĘTYm i zwalnia wszystkie pakiety żądań połączeń klienta umieszczonych w kolejce.

### <a name="tcp-window-size"></a>Rozmiar okna TCP

Podczas fazy instalacji i transferu danych połączenia każdy port raportuje ilość danych, które może obsłużyć, czyli rozmiar okna. Gdy dane są odbierane i przetwarzane, rozmiar tego okna jest dostosowywany dynamicznie. W przypadku protokołu TCP nadawca może wysłać tylko ilość danych, które pasują do okna odbiorcy. W zasadzie rozmiar okna zapewnia kontrolę przepływu na potrzeby transferu danych w każdym kierunku połączenia.

### <a name="tcp-packet-send"></a>Wysyłanie pakietów TCP

Wysyłanie danych TCP jest łatwo realizowane przez wywołanie funkcji ***nx_tcp_socket_send*** . Jeśli rozmiar przesyłanych danych jest większy niż wartość rozmiaru w gnieździe lub bieżący rozmiar okna odbioru elementu równorzędnego, w zależności od tego, który z nich jest mniejszy, wewnętrzna logika TCP carves dane, które pasują do minimalnej (rozmiaru pasma, okna odbierania równorzędnego) do transmisji. Ta usługa następnie kompiluje nagłówek TCP przed pakietem (w tym obliczenia sumy kontrolnej). Jeśli rozmiar okna odbiornika jest różny od zera, obiekt wywołujący wyśle tyle danych, ile może wypełnić rozmiar okna odbiornika. Jeśli okno odbierania przestanie być równe zero, wywołujący może zawiesić się i zaczekać, aż rozmiar okna odbiornika zostanie odpowiednio zwiększony dla tego pakietu. W danym momencie wiele wątków może zawiesić się podczas próby wysłania danych za pomocą tego samego gniazda.

> [!IMPORTANT]
> *Dane TCP znajdujące się w strukturze NX_PACKET powinny znajdować się na granicy długiego wyrazu. Ponadto musi być wystarczająca ilość miejsca między wskaźnikiem dołączania i wskaźnikiem początku danych do umieszczenia nagłówków TCP, IP i nośnika fizycznego.*

### <a name="tcp-packet-retransmit"></a>Ponowne przesyłanie pakietów TCP

Wcześniej przesłane pakiety TCP wysłane faktycznie przechowywane wewnętrznie do momentu zwrócenia potwierdzenia po drugiej stronie połączenia. Jeśli przesyłane dane nie są potwierdzone w określonym limicie czasu, przechowywany pakiet jest ponownie wysyłany i ustawiany jest następny limit czasu. Po odebraniu potwierdzenia wszystkie pakiety objęte numerem potwierdzenia w wewnętrznej kolejce transmisji są ostatecznie wydane.

> [!IMPORTANT]
> * Aplikacja nie wykorzystuje ponownie pakietu lub nie zmienia zawartości pakietu po powrocie funkcji ***nx_tcp_socket_send** _ z NX_SUCCESS. Przesłany pakiet jest ostatecznie uwalniany przez NetX przetwarzanie wewnętrzne po potwierdzeniu danych przez inne end._

### <a name="tcp-keepalive"></a>Utrzymywanie aktywności TCP

Funkcja utrzymywania aktywności protokołu TCP umożliwia gnieździi wykrywanie, czy jego element równorzędny rozłącza się bez poprawnego zakończenia (na przykład awaria elementu równorzędnego), czy też uniemożliwiać określonym obiektom monitorowania sieci przerwanie połączenia przez długie okresy bezczynności. Ruch przychodzący TCP działa przez okresowe wysyłanie ramki TCP bez danych, a numer sekwencyjny jest ustawiony na jeden mniejszy niż bieżący numer sekwencyjny. Po odebraniu takiej ramki utrzymania protokołu TCP odbiorca (Jeśli nadal działa) odpowiedzi z POTWIERDZENIEm dla bieżącego numeru sekwencji. Spowoduje to zakończenie transakcji utrzymywania aktywności.

Domyślnie funkcja utrzymywania aktywności nie jest włączona. Aby można było korzystać z tej funkcji, biblioteka NetX musi być skompilowana przy użyciu funkcji ***NX_ENABLE_TCP_KEEPALIVE** _ zdefiniowanej. Symbol _ *_NX_TCP_KEEPALIVE_INITIAL_** określa liczbę sekund braku aktywności przed zainicjowaniem ramki utrzymywania aktywności.

### <a name="tcp-packet-receive"></a>Odbieranie pakietów TCP

Przetwarzanie pakietów odbioru protokołu TCP (wywoływane z wątku pomocnika adresów IP) jest odpowiedzialne za obsługę różnych akcji połączenia i rozłączania, a także przesyłanie potwierdzenia. Ponadto przetwarzanie pakietów odbioru protokołu TCP jest odpowiedzialne za umieszczanie pakietów z danymi odbieranymi w odpowiedniej kolejce lub dostarczenie pakietu do pierwszego wstrzymanego wątku, oczekując na pakiet.

### <a name="tcp-receive-notify"></a>Powiadomienie o odebraniu protokołu TCP

Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, należy użyć funkcji ***nx_tcp_socket_receive_notify*** . Ta funkcja rejestruje funkcję odbierania pakietów wywołania zwrotnego dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, funkcja wywołania zwrotnego jest wykonywana.

Zawartość funkcji wywołania zwrotnego jest specyficzna dla aplikacji; Jednak funkcja najprawdopodobniej zawiera logikę do informowania wątku przetwarzania, że pakiet jest dostępny w odpowiednim gnieździe.

### <a name="thread-suspension"></a>Zawieszenie wątku

Jak wspomniano wcześniej, wątki aplikacji mogą wstrzymywać się podczas próby odebrania danych z określonego portu TCP. Po odebraniu pakietu na tym porcie jest on przyznany do pierwszego wątku, a następnie wznowiony. Opcjonalny limit czasu jest dostępny w przypadku zawieszania pakietu odbioru TCP, który jest funkcją dostępną dla większości usług NetX.

Zawieszenie wątku jest również dostępne dla połączenia (zarówno klienta, jak i serwera), powiązania klienta i usług odłączania.

### <a name="tcp-socket-statistics-and-errors"></a>Statystyka i błędy gniazda TCP

W przypadku włączenia oprogramowania NetX TCP Socket śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/TCP są obsługiwane następujące raporty statystyczne i błędy:

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

## <a name="tcp-socket-control-block-nx_tcp_socket"></a>NX_TCP_SOCKET bloku sterowania gniazdem TCP

Cechy poszczególnych gniazd TCP znajdują się w skojarzonym bloku sterowania *NX_TCP_SOCKET* , który zawiera przydatne informacje, takie jak link do struktury danych IP, interfejs połączenia sieciowego, port powiązany i kolejka odbierania pakietów. Ta struktura jest zdefiniowana w pliku ***nx_api. h*** .
