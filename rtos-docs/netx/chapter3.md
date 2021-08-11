---
title: Rozdział 3 — Składniki funkcjonalne Azure RTOS NetX
description: Ten rozdział zawiera opis wydajności stosu NETX TCP/IP Azure RTOS wydajności z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ebb002bc82d13210acf8db44cafb141d33a1b45fa8710295437e2dd15cbcf22
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784343"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx"></a>Rozdział 3 — Składniki funkcjonalne Azure RTOS NetX

Ten rozdział zawiera opis wydajności stosu NETX TCP/IP Azure RTOS wydajności z perspektywy funkcjonalnej. 

## <a name="execution-overview"></a>Omówienie wykonywania

W aplikacji NetX istnieje pięć typów wykonywania programów: inicjowanie, wywołania interfejsu aplikacji, wewnętrzny wątek adresu IP, okresowe czasomierze IP i sterownik sieciowy.

> [!IMPORTANT]
> NetX wymaga instalacji ThreadX i zależy od jego wykonywania wątku, zawieszenia, okresowych czasomierzy i obiektów wzajemnego wykluczania.

### <a name="initialization"></a>Inicjalizacja

Usługa ***nx_system_initialize** _ musi zostać wywołana przed wywołaną inną usługą NetX. Inicjowanie systemu można nazwać z procedury ThreadX _ *_tx_application_define_** lub z wątków aplikacji.

Po **zwracaniu nx_system_initialize** _ system jest gotowy do tworzenia pul pakietów i wystąpień adresów IP. Ponieważ tworzenie wystąpienia adresu IP wymaga domyślnej puli pakietów, co najmniej jedna pula pakietów NetX musi istnieć przed utworzeniem wystąpienia adresu IP. Tworzenie pul pakietów i wystąpień adresów IP jest dozwolone z funkcji inicjowania ThreadX _ *_tx_application_define_** i z wątków aplikacji.

Wewnętrznie tworzenie wystąpienia adresu IP jest realizowane w dwóch częściach. Pierwsza część jest wykonywana w kontekście wywołującego, z tx_application_define lub z kontekstu wątku aplikacji.  Obejmuje to skonfigurowanie struktury danych IP i utworzenie różnych zasobów adresów IP, w tym wewnętrznego wątku adresu IP. Druga część jest wykonywana podczas początkowego wykonywania z wątku wewnętrznego adresu IP. W tym miejscu najpierw jest wywoływany sterownik sieciowy dostarczony podczas pierwszej części tworzenia adresu IP. Wywołanie sterownika sieciowego z wątku wewnętrznego adresu IP umożliwia sterownikowi wykonanie operacji we/wy i zawieszenie podczas przetwarzania inicjowania. Gdy sterownik sieciowy powraca z przetwarzania inicjowania, tworzenie adresu IP jest ukończone.

> [!IMPORTANT]
> Usługa NetX **nx_ip_status_check** uzyskać informacje o wystąpieniu adresu IP i jego stanie interfejsu podstawowego. Takie informacje o stanie obejmują to, czy łącze jest zainicjowane, włączone i adres IP jest rozpoznawane. Te informacje są używane do synchronizowania wątków aplikacji, które muszą używać nowo utworzonego wystąpienia adresu IP. W przypadku systemów wieloadresowych zobacz "Obsługa wieloadresowa" poniżej. **nx_ip_interface_status_check** uzyskać informacje na temat określonego interfejsu.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Wywołania z aplikacji są w dużej mierze wykonane z wątków aplikacji działających w ramach ThreadX RTOS. Jednak niektóre inicjowanie, tworzenie i włączanie usług mogą być wywoływane z tx_application_define ***.*** Sekcje "Dozwolone z" w rozdziale 4 wskazują, z którego można nazwać każdą usługę NetX.

W większości przypadków działania intensywnie przetwarzane, takie jak obliczanie sumy kontrolnej, są wykonywane w kontekście wątku wywołującego — bez blokowania dostępu innych wątków do wystąpienia adresu IP. Na przykład w przypadku transmisji obliczenie sumy kontrolnej UDP jest wykonywane wewnątrz usługi ***nx_udp_socket_send,*** przed wywołaniem bazowej funkcji wysyłania adresów IP. W odebranym pakiecie sumy kontrolne UDP są obliczane w usłudze ***nx_udp_socket_receive,*** wykonywane w kontekście wątku aplikacji. Dzięki temu można zapobiec wsyłaniu żądań sieciowych wątków o wyższym priorytecie z powodu intensywnego przetwarzania obliczeń sumy kontrolnej w wątkach o niższym priorytecie.

Wartości, takie jak adresy IP i numery portów, są przekazywane do funkcji interfejsu API w kolejności bajtów hosta. Wewnętrznie te wartości są również przechowywane w kolejności bajtów hosta. Dzięki temu deweloperzy mogą łatwo wyświetlać wartości za pośrednictwem debugera. Gdy te wartości są zaprogramowane w ramce do transmisji, są one konwertowane na kolejność bajtów sieciowych.

### <a name="internal-ip-thread"></a>Wątek wewnętrznego adresu IP

Jak wspomniano wcześniej, każde wystąpienie adresu IP w netx ma własny wątek. Priorytet i rozmiar stosu wewnętrznego wątku ip jest zdefiniowany w nx_ip_create ***usługi.*** Wewnętrzny wątek adresu IP jest tworzony w trybie gotowym do wykonania. Jeśli wątek IP ma wyższy priorytet niż wątek wywołujący, wywłaszcz może wystąpić wewnątrz wywołania tworzenia adresu IP.

Punkt wejścia wątku wewnętrznego adresu IP znajduje się w wewnętrznej funkcji ***_nx_ip_thread_entry***. Po jego zakończeniu wewnętrzny wątek adresu IP najpierw kończy inicjowanie sterownika sieciowego, który składa się z wykonania trzech wywołań sterownika sieciowego specyficznego dla aplikacji. Pierwsze wywołanie to dołączenie sterownika sieciowego do wystąpienia adresu IP, po którym następuje wywołanie inicjowania, które umożliwia sterownikowi sieciowemu przechodzić przez proces inicjowania. Po powrocie sterownika sieciowego z inicjowania (może on zostać wstrzymany podczas oczekiwania na prawidłowe skonfigurowanie sprzętu), wewnętrzny wątek adresu IP ponownie wywołuje sterownik sieciowy, aby włączyć połączenie. 

Po powrocie sterownika sieciowego z wywołania włącz połączenie wewnętrzny wątek adresu IP przechodzi w nieskończoną pętlę sprawdzającą różne zdarzenia, które wymagają przetwarzania dla tego wystąpienia adresu IP. Zdarzenia przetwarzane w tej pętli obejmują odroczone odbiór pakietów IP, zestaw fragmentów pakietów IP, przetwarzanie ping protokołu ICMP, przetwarzanie protokołu IGMP, przetwarzanie kolejki pakietów TCP, okresowe przetwarzanie TCP, limity czasu zestawu fragmentów adresów IP i okresowe przetwarzanie IGMP. Zdarzenia obejmują również działania rozwiązywania problemów: przetwarzanie pakietów ARP i okresowe przetwarzanie ARP w sieci IP.

> [!NOTE]
> *Funkcje wywołania zwrotnego NetX, w tym wywołania zwrotne nasłuchiwać i rozłączania, są wywoływane z wewnętrznego wątku adresu IP, a nie oryginalnego wątku wywołującego. Aplikacja musi zadbać o to, aby nie wstrzymywać się wewnątrz żadnej funkcji wywołania zwrotnego NetX.*

### <a name="ip-periodic-timers"></a>Okresowe czasomierze IP
Istnieją dwa okresowe czasomierze ThreadX używane dla każdego wystąpienia adresu IP. Pierwszy z nich to jednosekwencowy czasomierz dla protokołów ARP, IGMP i TCP, a także kieruje przetwarzaniem ponownego zsyłania fragmentów adresów IP. Drugi czasomierz jest czasomierzem 100ms do kierowania limit czasu retransmisji TCP.

### <a name="network-driver"></a>Sterownik sieciowy
Każde wystąpienie adresu IP w NetX ma interfejs podstawowy, który jest identyfikowany przez sterownik urządzenia określony w nx_ip_create ***usługi.*** Sterownik sieciowy jest odpowiedzialny za obsługę różnych żądań NetX, w tym transmisji pakietów, odbioru pakietów oraz żądań stanu i kontroli.

W przypadku systemu wieloadmiarowego wystąpienie adresu IP ma wiele interfejsów, z których każdy ma skojarzony sterownik sieciowy, który wykonuje te zadania dla odpowiedniego interfejsu.

Sterownik sieciowy musi również obsługiwać zdarzenia asynchroniczne występujące na nośniku. Zdarzenia asynchroniczne z nośnika obejmują odbiór pakietów, ukończenie transmisji pakietów i zmiany stanu. NetX udostępnia sterownik sieciowy z kilkoma funkcjami dostępu do obsługi różnych zdarzeń. Te funkcje są przeznaczone do wywoływania z rutynowej części usługi przerwań sterownika sieciowego. W przypadku sieci IP sterownik sieciowy powinien przesyłać wszystkie odebrane pakiety ARP do funkcji ***_nx_arp_packet_deferred_receive** _ internal. Wszystkie pakiety RARP powinny być przekazywane do funkcji _ *__nx_rarp_packet_deferred_receive_* _ internal. Istnieją dwie opcje pakietów IP. Jeśli wymagana jest szybka wysyłka pakietów IP, przychodzące pakiety IP powinny być przekazywane do _ *_ _nx_ip_packet_receive_* _ w celu natychmiastowego przetwarzania. Znacznie poprawia to wydajność NetX w obsłudze pakietów IP. W przeciwnym razie sterownik sieciowy powinien przesyłać pakiety IP do _*_ _nx_ip_packet_deferred_receive_**. Ta usługa umieszcza pakiet IP w kolejce przetwarzania odroczonego, gdzie jest obsługiwany przez wewnętrzny wątek adresu IP, co powoduje najmniejszą ilość czasu przetwarzania isr.

Sterownik sieciowy może również odroczyć przetwarzanie przerwań, aby zabrakło kontekstu wątku IP. W tym trybie isR musi zapisać niezbędne informacje, wywołać funkcję wewnętrzną _nx_ip_driver_deferred_processing ***i*** potwierdzić kontroler przerwań. Ta usługa powiadamia wątek ip, aby zaplanować wywołanie zwrotne do sterownika urządzenia w celu zakończenia przetwarzania zdarzenia, które powoduje przerwanie.

Niektóre kontrolery sieciowe są w stanie wykonywać obliczenia i walidację sumy kontrolnej nagłówka TCP/IP na sprzęcie bez konieczności przyjmowania cennych zasobów procesora CPU. Aby skorzystać z funkcji możliwości sprzętowych, netx udostępnia opcje włączania lub wyłączania różnych obliczeń sumy kontrolnej oprogramowania w czasie kompilacji, a także włączania lub wyłączania obliczeń sumy kontrolnej w czasie wykonywania. Aby uzyskać bardziej szczegółowe informacje na temat pisania sterowników[sieciowych NetX,](chapter5.md)zobacz rozdział 5 Sterowniki sieciowe NetX.

### <a name="multihome-support"></a>Obsługa wieloadresowa
NetX obsługuje systemy połączone z wieloma urządzeniami fizycznymi przy użyciu jednego wystąpienia adresu IP. Każdy interfejs fizyczny jest przypisany do bloku sterowania interfejsem w wystąpieniu adresu IP. Aplikacje, które chcą korzystać z systemu wieloadresowego, muszą zdefiniować wartość NX_MAX_PHSYCIAL_INTERFACES do liczby urządzeń fizycznych dołączonych do systemu i ponownie skompilować bibliotekę NetX.  Domyślnie ustawienie **NX_MAX_PHYSICAL_INTERFACES** na jeden, tworząc jeden blok sterowania interfejsu w wystąpieniu adresu IP.

Aplikacja NetX tworzy pojedyncze wystąpienie adresu IP dla urządzenia podstawowego przy użyciu usługi ***nx_ip_create** _service. Dla każdego dodatkowego urządzenia sieciowego aplikacja dołącza urządzenie do wystąpienia adresu IP przy użyciu usługi _ *_nx_ip_interface_attach_**.

Każda struktura interfejsu sieciowego zawiera podzestaw informacji o sieci interfejsu sieciowego, który znajduje się w bloku sterowania IP, w tym adres IP interfejsu, maskę podsieci, rozmiar jednostki MTU IP i informacje o adresie warstwy MAC.

> [!IMPORTANT]
> *NetX z obsługą wielunadresowych jest wstecznie zgodny ze starszymi wersjami netx. Usługi, które nie przyjmą jawnych informacji o interfejsie domyślnie do podstawowego urządzenia sieciowego.*

Interfejs podstawowy ma zero indeksu na liście wystąpień adresów IP. Każde kolejne urządzenie dołączone do wystąpienia adresu IP jest przypisywane do następnego indeksu.

Wszystkie usługi protokołu górnej warstwy, dla których jest włączone wystąpienie adresu IP, w tym TCP, UDP, ICMP i IGMP, są dostępne dla wszystkich dołączonych urządzeń.

W większości przypadków NetX może określić najlepszy adres źródłowy do użycia podczas przesyłania pakietu. Wybór adresu źródłowego zależy od adresu docelowego. Usługi NetX są udostępniane w celu umożliwienia aplikacjom określenia określonego adresu źródłowego do użycia w przypadkach, gdy najbardziej odpowiedni adres nie może zostać określony przez adres docelowy. Przykładem może być system wieloadresowy, w przypadku którego aplikacja musi wysłać pakiet na adresy docelowe emisji IP lub multiemisji.

Usługi przeznaczone specjalnie do tworzenia aplikacji wieloadresowych obejmują:

*nx_igmp_multicast_interface_join nx_ip_driver_interface_direct_command nx_ip_interface_address_get nx_ip_interface_address_set nx_ip_interface_attach nx_ip_interface_info_get nx_ip_interface_status_check nx_ip_raw_packet_interface_send nx_udp_socket_interface_send*

Te usługi opisano bardziej szczegółowo w rozdziale 4 — opis Azure RTOS[NetX Services.](chapter4.md)

### <a name="loopback-interface"></a>Interfejs sprzężenia zwrotnego
Interfejs sprzężenia zwrotnego to specjalny interfejs sieciowy bez dołączonego fizycznego łącza. Interfejs sprzężenia zwrotnego umożliwia aplikacjom komunikowanie się przy użyciu adresu IP sprzężenia zwrotnego 127.0.0.1

Aby korzystać z interfejsu logicznego sprzężenia zwrotnego, upewnij się, że opcja NX_DISABLE_LOOPBACK_INTERFACE ***nie*** jest ustawiona.

### <a name="interface-control-blocks"></a>Bloki kontrolek interfejsu
Liczba bloków sterowania interfejsem w wystąpieniu adresu IP to liczba interfejsów fizycznych (zdefiniowanych za pomocą funkcji ***NX_MAX_PHYSICAL_INTERFACES** _) oraz interfejs sprzężenia zwrotnego, jeśli jest włączony. Całkowita liczba interfejsów jest zdefiniowana w _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Warstwy protokołów

Protokół TCP/IP implementowany przez NetX jest protokołem warstwowym, co oznacza, że bardziej złożone protokoły są zbudowane na podstawie prostszych protokołów bazowych. W przypadku protokołu TCP/IP protokół najniższej warstwy znajduje się w *warstwie łącza* i jest obsługiwany przez sterownik sieciowy. Ten poziom jest zwykle skierowany do sieci Ethernet, ale może być również światłowodowy, szeregowy lub praktycznie dowolny nośnik fizyczny.

W górnej części warstwy łącza znajduje się warstwa *sieci .* W przypadku protokołu TCP/IP jest to adres IP, który zasadniczo jest odpowiedzialny za wysyłanie i odbieranie prostych pakietów w najlepszy sposób w sieci. Protokoły typu zarządzania, takie jak ICMP i IGMP, są zwykle również kategoryzowane jako warstwy sieciowe, mimo że korzystają z adresu IP podczas wysyłania i odbierania.

Warstwa *Transport* jest na wierzchu warstwy sieciowej. Ta warstwa jest odpowiedzialna za zarządzanie przepływem danych między hostami w sieci. Istnieją dwa typy usług transportu obsługiwanych przez oprogramowanie NetX: UDP i TCP. Usługi UDP zapewniają najlepsze wysyłanie i odbieranie danych między dwoma hostami w sposób bez połączenia, a protokół TCP zapewnia niezawodną usługę zorientowaną na połączenie między dwoma jednostkami hosta.

Ta warstwa jest odzwierciedlana w rzeczywistych pakietach danych sieciowych. Każda warstwa protokołu TCP/IP zawiera blok informacji nazywany nagłówkiem. Ta technika otaczającego dane (i prawdopodobnie informacje o protokole) nagłówkiem jest zwykle nazywana hermetyzację danych. Rysunek 1 przedstawia przykład warstw NetX, a na rysunku 2 przedstawiono wynikowe hermetyzację danych wysyłanych przez protokołu UDP.

![Warstwy protokołów](./media/user-guide/protocol-layering.png)

**RYSUNEK 1. Warstwy protokołów**

![Hermetyzacja danych UDP](./media/user-guide/udp-data-encapsulation.png)

**RYSUNEK 2. Hermetyzacja danych UDP**

## <a name="packet-pools"></a>Pule pakietów

Szybkie i deterministyczne przydzielanie pakietów zawsze stanowi wyzwanie w aplikacjach sieciowych w czasie rzeczywistym. Mając to na uwadze, NetX zapewnia możliwość tworzenia wielu pul pakietów sieciowych o stałym rozmiarze i zarządzania nimi.

Ponieważ pule pakietów NetX składają się z bloków pamięci o stałym rozmiarze, nigdy nie ma żadnych wewnętrznych problemów z fragmentacją. Oczywiście fragmentacja powoduje zachowanie, które jest z założenia niedeterministyczne.

Ponadto czas wymagany do przydzielenia i wolnego ilości pakietów NetX do prostego manipulowania listami połączonymi. Ponadto alokacja pakietów i co najmniej ich co najmniej alokacja odbywa się na początku dostępnej listy. Zapewnia to najszybsze możliwe przetwarzanie listy połączonej.

Brak elastyczności jest zwykle główną wadą pul pakietów o stałym rozmiarze. Określenie optymalnego rozmiaru ładunku pakietu, który obsługuje również pakiet przychodzący w najgorszym przypadku, jest trudne. Pakiety NetX rozsyłają ten problem za pomocą opcjonalnej funkcji *nazywanej łańcuchem pakietów*. Rzeczywisty pakiet sieciowy może składać się z co najmniej jednego połączonego pakietu NetX. Ponadto nagłówek pakietu zachowuje wskaźnik na górę pakietu. Po dodaniu dodatkowych protokołów ten wskaźnik jest po prostu przesuwany wstecz, a nowy nagłówek jest zapisywany bezpośrednio przed danymi. Bez technologii pakietów elastycznych stos musiałby przydzielić kolejny bufor i skopiować dane do nowego buforu z nowym nagłówkiem, który intensywnie przetwarza.

Ponieważ każdy rozmiar ładunku pakietu jest stały dla danej puli pakietów, dane aplikacji większe niż rozmiar ładunku wymagają połączenia wielu pakietów. Podczas wypełniania pakietu danymi użytkownika aplikacja musi używać usługi ***nx_packet_data_append***. Ta usługa przenosi dane aplikacji do pakietu. W sytuacjach, gdy pakiet nie wystarcza do przechowywania danych użytkownika, przydzielane są dodatkowe pakiety do przechowywania danych użytkownika. Aby można było używać łańcucha pakietów, sterownik musi mieć możliwość odbierania lub przesyłania z pakietów łańcuchowych.

Każda pula pamięci pakietów NetX jest zasobem publicznym. NetX nie stosuje żadnych ograniczeń co do sposobu, w jaki są używane pule pakietów.

### <a name="packet-pool-memory-area"></a>Obszar pamięci puli pakietów
Obszar pamięci puli pakietów jest określony podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci dla obiektów ThreadX i NetX, może ona być zlokalizowana w dowolnym miejscu w przestrzeni adresowej obiektu docelowego. Jest to ważna funkcja ze względu na dużą elastyczność zapewnianą aplikacji. Załóżmy na przykład, że produkt komunikacyjny ma obszar pamięci o dużej szybkości dla buforów sieciowych. Ten obszar pamięci można łatwo wykorzystać, dopowiąc go do puli pamięci pakietów NetX.

### <a name="creating-packet-pools"></a>Tworzenie pul pakietów
Pule pakietów są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Nie ma żadnych ograniczeń liczby pul pamięci pakietów w aplikacji NetX.

### <a name="packet-header-nx_packet"></a>Nagłówek NX_PACKET
Domyślnie NetX umieszcza nagłówek pakietu bezpośrednio przed obszarem ładunku pakietu. Pula pamięci pakietów jest zasadniczo serią pakietów — nagłówków, po których natychmiast następuje ładunek pakietu. Nagłówek pakietu ***(NX_PACKET***) i układ puli pakietów zostały na rysunku 3.

W przypadku sterowników urządzeń sieciowych, które są w stanie wykonać zero operacji kopiowania, zazwyczaj adres początkowy obszaru ładunku pakietu jest zaprogramowany w logice DMA. Niektóre aparaty DMA mają wymaganie wyrównania w obszarze ładunku.

> [!IMPORTANT]
> *Sterownik sieciowy, który musi wywołać funkcję ***nx_packet_transmit_release** _, gdy transmisja pakietu zostanie ukończona. Ta funkcja sprawdza, czy pakiet nie jest częścią kolejki wyjściowej TCP, zanim zostanie faktycznie umieszczony z powrotem w dostępnej puli. Niepowodzenie wywołania tej funkcji może spowodować nieprzewidywalne behavior._

![Nagłówek pakietu i układ puli pakietów](./media/user-guide/packet-header-packet-pool-layout.png)

**RYSUNEK 3. Nagłówek pakietu i układ puli pakietów**

Pola nagłówka pakietu są zdefiniowane tak, jak pokazano w poniższej tabeli. Należy pamiętać, że ta tabela nie jest kompleksową listą wszystkich elementów członkowskich *NX_PACKET* struktury.

| Nagłówek pakietu          | Przeznaczenie                                                                                                                                                                                                                                                                                                                            |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *nx_packet_pool_owner*   | To pole wskazuje pulę pakietów, która jest właścicielem tego konkretnego pakietu. Po zwolnieniu pakiet jest zwalniany do tej konkretnej puli. W przypadku własności puli wewnątrz każdego pakietu datagram może obejmować wiele pakietów z wielu pul pakietów.                                                         |
| *nx_packet_next*         | To pole wskazuje następny pakiet w tej samej ramce. Jeśli wartość NULL, nie ma żadnych dodatkowych pakietów, które są częścią ramki. |
| *nx_packet_last*         | To pole wskazuje ostatni pakiet w ramach tego samego pakietu sieciowego. Jeśli wartość NULL, ten pakiet reprezentuje cały pakiet sieciowy.  |
| *nx_packet_length*       | To pole zawiera łączną liczbę bajtów w całym pakiecie sieciowym, w tym łączną  liczbę bajtów we wszystkich pakietach łańcuchowanych razem przez nx_packet_next sieciowego. |
| *nx_packet_ip_interface* | To pole jest blokiem sterowania interfejsu, który jest przypisywany do pakietu po jego otrzymaniu przez sterownik interfejsu i przez NetX dla pakietów wychodzących. Blok sterowania interfejsu opisuje interfejs, np. adres sieciowy, adres MAC, adres IP i stan interfejsu, taki jak włączony link i wymagane mapowanie fizyczne. |
| *nx_packet_data_start*   | To pole wskazuje początek obszaru ładunku fizycznego tego pakietu. Nie musi być bezpośrednio po nagłówku NX_PACKET, ale jest to wartość domyślna dla nx_packet_pool_create ***usługi.*** |
| *nx_packet_data_end*     | To pole wskazuje na koniec obszaru ładunku fizycznego tego pakietu. Różnica między tym polem a polem nx_packet_data_start reprezentuje rozmiar ładunku. |
| *nx_packet_prepend_ptr*  | To pole wskazuje lokalizację, w której dane pakietu , nagłówek protokołu lub rzeczywiste dane, są dodawane przed istniejącymi danymi pakietu (jeśli są) w obszarze ładunku pakietu. Musi być większa niż lub  równa nx_packet_data_start i mniejsza niż lub równa nx_packet_append_ptr *wskaźnika.*  *Ze względu na wydajność NetX zakłada, że gdy pakiet jest przekazywany do usług NetX w celu transmisji, dołączany wskaźnik wskazuje długi adres wyrównany wyrazem.* |
| *nx_packet_append_ptr*    | To pole wskazuje koniec danych obecnie w obszarze ładunku pakietu. Musi znajdować się między lokalizacją pamięci wskazywaną przez nx_packet_prepend_ptr *i* *nx_packet_data_end*. Różnica między tym polem *a polem nx_packet_prepend_ptr* reprezentuje ilość danych w tym pakiecie. |
| *nx_packet_fragment_next* | To pole służy do przechowywania pofragmentowanych pakietów, dopóki cały pakiet nie zostanie ponownie skompliowany. |
| *nx_packet_pad*           | Te pola definiują długość wypełnienia w 4-bajtowych wyrazach, aby osiągnąć wymagane wyrównanie. To pole jest usuwane, *NX_PACKET_HEADER_PAD* nie jest zdefiniowany. |
|  |  |

### <a name="packet-header-offsets"></a>Przesunięcia nagłówka pakietu

Rozmiar nagłówka pakietu jest definiowany w celu umożliwienia wystarczającej ilości miejsca, aby pomieścić rozmiar nagłówka. Usługa *nx_packet_allocate* służy do przydzielania pakietu i dostosowuje wskaźnik dołączany w pakiecie zgodnie z określonym typem pakietu. Typ pakietu informuje NetX przesunięcie wymagane do wstawienia nagłówka protokołu (takiego jak UDP, TCP lub ICMP) przed danymi protokołu.

Następujące typy są zdefiniowane w NetX, aby uwzględnić nagłówek IP i nagłówek warstwy fizycznej (Ethernet) w pakiecie. W drugim przypadku przyjmuje się, że jest to 16 bajtów, biorąc pod uwagę wymagane wyrównanie 4-bajtowe. Pakiety IP są nadal zdefiniowane w Programie NetX, aby aplikacje przydzielały pakiety dla sieci IP. W poniższej tabeli przedstawiono zdefiniowane symbole:

| Typ pakietu   | Wartość |
|---------------|-------|
| NX_IP_PACKET  | 0x24  |
| NX_UDP_PACKET | 0x2c  |
| NX_TCP_PACKET | 0x38  |
|               |       |

### <a name="pool-capacity"></a>Pojemność puli
Liczba pakietów w puli pakietów jest funkcją rozmiaru ładunku i całkowitej liczby bajtów w obszarze pamięci dostarczonym do usługi tworzenia puli pakietów. Pojemność puli jest obliczana przez podzielenie rozmiaru pakietu (w tym rozmiaru nagłówka NX_PACKET, rozmiaru ładunku i odpowiedniego wyrównania) na łączną liczbę bajtów w dostarczonym obszarze pamięci.

### <a name="thread-suspension"></a>Zawieszenie wątku
Wątki aplikacji mogą zostać wstrzymane podczas oczekiwania na pakiet z pustej puli. Gdy pakiet jest zwracany do puli, zawieszony wątek jest nadaj temu pakietowi i wznawiany.

Jeśli wiele wątków jest zawieszonych w tej samej puli pakietów, są one wznawiane w kolejności, w których zostały wstrzymane (FIFO).

### <a name="pool-statistics-and-errors"></a>Statystyki puli i błędy
Jeśli ta opcja jest włączona, oprogramowanie Do zarządzania pakietami NetX **Errors** śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla pul pakietów są utrzymywane następujące statystyki i raporty o błędach:

* Łączna liczba pakietów w puli
* Bezpłatne pakiety w puli
* Puste żądania alokacji puli
* Wstrzymanie alokacji pustej puli
* Nieprawidłowe wydania pakietów

Wszystkie te statystyki i raporty o błędach, z wyjątkiem łącznej i bezpłatnej liczby pakietów w puli, są wbudowane w bibliotekę NetX, chyba że **zdefiniowano** wartość * NX_DISABLE_PACKET_INFO _. Te dane są dostępne dla aplikacji za pomocą usługi _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>Blok sterowania pulą pakietów NX_PACKET_POOL

Charakterystyki każdej puli pamięci pakietów znajdują się w jej bloku sterującym. Zawiera on przydatne informacje, takie jak połączona lista pakietów bezpłatnych, liczba wolnych pakietów i rozmiar ładunku pakietów w tej puli. Ta struktura jest zdefiniowana *w nx_api.h.*

Bloki sterowania puli pakietów mogą się znaleźć w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

## <a name="ip-protocol"></a>Protokół IP

Składnik protokołu internetowego (IP) netx jest odpowiedzialny za wysyłanie i odbieranie pakietów IP w Internecie. W NetX składnik jest ostatecznie odpowiedzialny za wysyłanie i odbieranie komunikatów TCP, UDP, ICMP i IGMP przy użyciu podstawowego sterownika sieciowego.

NetX obsługuje protokół IP (RFC 791)

### <a name="ip-addresses"></a>Adresy IP

Każdy host w Internecie ma unikatowy 32-bitowy identyfikator nazywany adresem IP. Istnieje pięć klas adresów IP zgodnie z opisem na rysunku 4. Zakresy pięciu klas adresów IP są następujące:

| Klasa | Zakres                        |
|-------|------------------------------|
| A     | Od 0.0.0.0 do 127.255.255.255   |
| B     | Od 128.0.0.0 do 191.255.255.255 |
| C     | Od 192.0.0.0 do 223.255.255.255 |
| D     | Od 224.0.0.0 do 239.255.255.255 |
| E     | Od 240.0.0.0 do 247.255.255.255 |

**7 bitów 24 bity**

![Struktura adresów IP](./media/user-guide/ip-address-structure.png)

**RYSUNEK 4. Struktura adresów IP**

Istnieją również trzy typy specyfikacji *adresów:* emisji pojedynczej, *emisji* i *multiemisji*. Adresy emisji pojedynczej to te adresy IP, które identyfikują określonego hosta w Internecie. Adresy emisji pojedynczej mogą być źródłowym lub docelowym adresem IP. Adres emisji identyfikuje wszystkie hosty w określonej sieci lub podsieć i może być używany tylko jako adresy docelowe. Adresy rozgłasze są określane przez ustawienie części adresu z identyfikatorem hosta na jedynki. Adresy multiemisji (klasa D) określają dynamiczną grupę hostów w Internecie. Członkowie grupy multiemisji mogą dołączyć i opuścić w dowolnym momencie.

> [!IMPORTANT]
> *Tylko protokoły bez połączenia, takie jak UDP przez IP, mogą korzystać z emisji i ograniczonej możliwości emisji grupy multiemisji.*

> [!IMPORTANT]
> *Makro* IP_ADDRESS jest *zdefiniowany w*  * **nx_api.h** _. Umożliwia łatwe określenie adresów IP przy użyciu przecinków, a nie kropek. Na przykład IP_ADDRESS(128,0,0,0) _specifies adres pierwszej klasy B pokazany na rysunku 4.*

### <a name="ip-gateway-address"></a>Adres bramy IP

Bramy sieci pomagają hostom w sieciach w przekazywaniu pakietów przeznaczonych do miejsc docelowych spoza domeny lokalnej. Każdy węzeł ma pewne informacje o tym, do którego następnego przeskoku należy wysłać, do lokalizacji docelowej jednego z jego sąsiadów lub za pośrednictwem wstępnie zaprogramowanego statycznej tabeli routingu. Jeśli jednak te podejścia nie powiodą się, węzeł powinien przekierowywał pakiet do bramy domyślnej, która zawiera więcej informacji na temat sposobu rozsyłania pakietu do miejsca docelowego. Należy pamiętać, że brama domyślna musi być bezpośrednio dostępna za pośrednictwem jednego z interfejsów fizycznych dołączonych do wystąpienia adresu IP. Aplikacja wywołuje ***usługę nx_ip_gateway_address_set,*** aby skonfigurować domyślny adres IP bramy.

### <a name="ip-header"></a>Nagłówek IP

Aby dowolny pakiet IP był wysyłany przez Internet, musi mieć nagłówek IP. Gdy protokoły wyższego poziomu (UDP, TCP, ICMP lub IGMP) wywołują składnik IP w celu wysłania pakietu, moduł przesyłania adresów IP umieszcza nagłówek IP przed danymi. Z drugiej strony, gdy pakiety IP są odbierane z sieci, składnik IP usuwa nagłówek IP z pakietu przed dostarczeniem do protokołów wyższego poziomu. Rysunek 5 przedstawia format nagłówka adresu IP.

![Format nagłówka IP](./media/user-guide/ip-header-format.png)

**RYSUNEK 5. Format nagłówka IP**

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji TCP/IP będą w big endian formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym. Na przykład wersja 4-bitowa i 4-bitowa długość nagłówka adresu IP muszą znajdować się w pierwszym bajtze nagłówka.*

Pola nagłówka adresu IP są zdefiniowane w następujący sposób:

**Przeznaczenie pola nagłówka IP**

***Wersja 4-bitowa*** To pole zawiera wersję adresu IP, który reprezentuje ten nagłówek. W przypadku adresu IP w wersji 4, którą obsługuje netx, wartość tego pola wynosi 4.

***4-bitowa długość nagłówka*** To pole określa liczbę 32-bitowych wyrazów w nagłówku adresu IP. Jeśli nie ma żadnych wyrazów opcji, wartość tego pola wynosi 5.

***8-bitowy typ usługi (TOS)*** To pole określa typ usługi żądanej dla tego pakietu IP. Prawidłowe żądania są następujące:

| **Żądanie tos**     | **Wartość** |
| ------------------- | --------- |
| Normalne              | 0x00      |
| Opóźnienie minimalne       | 0x10      |
| Maksymalna ilość danych        | 0x08      |
| Maksymalna niezawodność | 0x04      |
| Koszt minimalny        | 0x02      |

***16-bitowa całkowita długość*** To pole zawiera łączną długość datagramów adresów IP w bajtach, w tym nagłówek adresu IP. Datagram adresów IP to podstawowa jednostka informacji znalezionych w Internecie TCP/IP. Oprócz danych zawiera ona miejsce docelowe i adres źródłowy. Ponieważ jest to pole 16-bitowe, maksymalny rozmiar datagramu IP to 65 535 bajtów.

***16-bitowa identyfikacja*** Pole to liczba używana do unikatowego identyfikowania każdego datagramu adresu IP wysyłanego z hosta. Ta liczba jest zwykle zwiększana po wysłaniu datagramu IP. Jest to szczególnie przydatne w przypadku składania odebranych fragmentów pakietów IP.

***Flagi 3-bitowe*** To pole zawiera informacje o fragmentacji adresów IP. Bit 14 to bit "nie fragmentuj". Jeśli ten bit jest ustawiony, datagram wychodzącego adresu IP nie zostanie pofragmentowany. Bit 13 jest bitem "więcej fragmentów". Jeśli ten bit jest ustawiony, istnieje więcej fragmentów. Jeśli ten bit jest jasny, jest to ostatni fragment pakietu IP.

**Przeznaczenie pola nagłówka adresu IP**

***Przesunięcie fragmentu 13-bitowego*** To pole zawiera 13-bitowe górne przesunięcie fragmentu. W związku z tym przesunięcia fragmentów są dozwolone tylko w granicach 8-bajtowych. Pierwszy fragment fragmentu datagramu pofragmentowanych adresów IP będzie miał ustawiony bit "więcej fragmentów" z przesunięciem 0.

***8-bitowy czas wygaśnięcia (TTL)*** To pole zawiera liczbę routerów, które może przekazać ten datagram, co ogranicza okres istnienia datagramu.

***Protokół 8-bitowy*** To pole określa, który protokół używa datagramu IP. Poniżej znajduje się lista prawidłowych protokołów i ich wartości:

| Protokół | Wartość |
|----------|-------|
| ICMP     | 0x01  |
| Igmp     | 0x02  |
| TCP      | 0X06  |
| UDP      | 0X11  |
|          |       |


***16-bitowa sumy kontrolne*** To pole zawiera 16-bitową sumy kontrolnej, która obejmuje tylko nagłówek IP. Istnieją dodatkowe sumy kontrolne w protokołach wyższego poziomu, które obejmują ładunek IP.

***32-bitowy źródłowy adres IP*** To pole zawiera adres IP nadawcy i zawsze jest adresem hosta.

***32-bitowy docelowy adres IP*** To pole zawiera adres IP odbiorcy lub odbiorników, jeśli adres jest adresem emisji lub multiemisji.

### <a name="creating-ip-instances"></a>Tworzenie wystąpień IP

Wystąpienia IP są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Początkowy adres IP, maska sieci, domyślna *pula pakietów,* sterownik nośnika oraz pamięć i priorytet wewnętrznego wątku IP są definiowane przez nx_ip_create usługi. Jeśli aplikacja inicjuje wystąpienie adresu IP z jego adresem IP ustawionym na nieprawidłowy adres (0.0.0.0), zakłada się, że adres interfejsu zostanie później rozpoznany przez konfigurację ręczną, za pośrednictwem protokołu RARP lub DHCP lub podobnych protokołów.

W przypadku systemów z wieloma interfejsami sieciowymi interfejs podstawowy jest wyznaczany podczas *wywoływania nx_ip_create*. Każdy dodatkowy interfejs można dołączyć do tego samego wystąpienia adresu IP, wywołując *nx_ip_interface_attach*. Ta usługa przechowuje informacje o interfejsie sieciowym (takie jak adres IP, maska sieci) w bloku sterowania interfejsem i kojarzy wystąpienie sterownika z blokiem sterowania interfejsem w wystąpieniu adresu IP. Ponieważ sterownik odbiera pakiet danych, musi przechowywać informacje o interfejsie w strukturze NX_PACKET przed przekazywaniem ich do logiki odbierania adresów IP. Pamiętaj, że wystąpienie adresu IP musi już zostać utworzone przed dołączenia jakichkolwiek interfejsów.

 ### <a name="ip-send"></a>Wysyłanie adresów IP
 Przetwarzanie wysyłania adresów IP w netx jest bardzo uproszczone.

Dołączany wskaźnik w pakiecie jest przenoszony wstecz w celu uwzględnienia nagłówka IP. Nagłówek IP jest ukończony (ze wszystkimi opcjami określonymi przez warstwę protokołu wywołującego), sumy kontrolne IP są obliczane w wierszu, a pakiet jest wysyłany do skojarzonego sterownika sieciowego. Ponadto fragmentacja wychodząca jest również skoordynowana z poziomu przetwarzania wysyłania adresów IP.

W przypadku adresu IP netx inicjuje żądania ARP, jeśli jest wymagane fizyczne mapowanie docelowego adresu IP.

> [!IMPORTANT]
> W przypadku łączności IP pakiety wymagające rozpoznawania adresów IP (tj. mapowania fizycznego) są kolejkowane w kolejce *ARP,* dopóki liczba pakietów w kolejce nie przekroczy głębokości kolejki ARP (zdefiniowanej za pomocą *symbolu **NX_ARP_MAX_QUEUE_DEPTH**). Jeśli zostanie* osiągnięta głębokość kolejki, netx usunie najstarszy pakiet z kolejki i będzie kontynuować oczekiwanie na rozwiązanie adresu dla pozostałych pakietów w *kolejce. Z drugiej strony,* jeśli wpis ARP nie zostanie rozpoznany, oczekujące pakiety we wpisie ARP są zwalniane po przechyłce czasu wpisu ARP.

W przypadku systemów z wieloma interfejsami sieciowymi system NetX wybiera interfejs na podstawie docelowego adresu IP. Następująca procedura dotyczy procesu wyboru:

1. Jeśli adres docelowy to emisja IP lub multiemisja, a jeśli określono prawidłowy interfejs wychodzący, użyj tego interfejsu. W przeciwnym razie używany jest pierwszy interfejs fizyczny.

2. Jeśli adres docelowy znajduje się w tabeli routingu statycznego, używany jest interfejs skojarzony z bramą.

3. Jeśli miejsce docelowe jest w linku, używany jest interfejs on-link.

4. Jeśli adres docelowy jest adresem sprzężenia zwrotnego 127.0.0.1, używany jest interfejs sprzężenia zwrotnego.

5. Jeśli brama domyślna jest prawidłowo skonfigurowana, użyj interfejsu skojarzonego z bramą domyślną, aby przesłać pakiet.

6. Pakiet wyjściowy jest porzucany, jeśli wszystkie powyższe nie powiedzie się.

### <a name="ip-receive"></a>Odbieranie adresu IP

Przetwarzanie odbierania adresów IP jest wywoływane ze sterownika sieci lub wewnętrznego wątku adresu IP (w przypadku przetwarzania pakietów w kolejce odroczonych odebranych pakietów). Przetwarzanie odbierania adresów IP sprawdza pole protokołu i próbuje wysłać pakiet do odpowiedniego składnika protokołu. Przed wysłaniem pakietu nagłówek IP jest usuwany przez przesuwanie wstępnie otwartego wskaźnika poza nagłówek IP.

Przetwarzanie odbierania adresów IP wykrywa również pofragmentowane pakiety IP i wykonuje niezbędne kroki w celu ponownego zbierania ich, jeśli jest włączona fragmentacja. Jeśli fragmentacja jest potrzebna, ale nie jest włączona, pakiet jest porzucany.

NetX określa odpowiedni interfejs sieciowy na podstawie interfejsu określonego w pakiecie. Jeśli interfejs pakietu ma wartość NULL, NetX domyślnie jest interfejsem podstawowym. Ma to na celu zagwarantowanie zgodności ze starszymi sterownikami NetX Ethernet.

### <a name="raw-ip-send"></a>Nieprzetworzone wysyłanie adresów IP

Nieprzetworzone pakiety IP to ramka IP zawierająca ładunek protokołu górnej warstwy, który nie jest bezpośrednio obsługiwany (i przetwarzany) przez platformę NetX. Pakiet pierwotny umożliwia deweloperom definiowanie własnych aplikacji opartych na adresach IP. Aplikacja może wysyłać nieprzetworzone pakiety IP bezpośrednio przy użyciu usługi ***nx_ip_raw_packet_send** _, jeśli włączono przetwarzanie nieprzetworzonych pakietów IP w _*_usłudze nx_ip_raw_packet_enabled_*_ ip. Jeśli jednak adres docelowy jest adresem multiemisji lub emisji, netx domyślnie jest pierwszym interfejsem (podstawowym). W związku z tym, aby wysyłać takie pakiety na interfejsy pomocnicze, aplikacja musi użyć usługi _ *_nx_ip_raw_packet_interface_send_**, aby określić adres źródłowy do użycia dla pakietu wychodzącego.

### <a name="raw-ip-receive"></a>Odbieranie nieprzetworzonych adresów IP

Jeśli przetwarzanie nieprzetworzonych pakietów IP jest włączone, aplikacja możeodbierać nieprzetworzone pakiety IP za pośrednictwem usługi * nx_ip_raw_packet_receive_service. Wszystkie pakiety przychodzące są przetwarzane zgodnie z protokołem określonym w nagłówku adresu IP. Jeśli protokół określa protokół UDP, TCP, IGMP lub ICMP, NetX będzie przetwarzać pakiet przy użyciu odpowiedniej procedury obsługi dla typu protokołu pakietu. Jeśli protokół nie jest jednym z tych protokołów, a pierwotne odbieranie adresów IP jest włączone, pakiet przychodzący zostanie umieszczany w nieprzetworzonych kolejkach pakietów oczekujących na otrzymanie go przez aplikację za pośrednictwem usługi _ *_nx_ip_raw_packet_receive_**. Ponadto wątki aplikacji mogą zostać wstrzymane z opcjonalnym limitem czasu podczas oczekiwania na nieprzetworzonych pakietów IP.

### <a name="default-packet-pool"></a>Domyślna pula pakietów

Każde wystąpienie adresu IP ma domyślną pulę pakietów podczas tworzenia. Ta pula pakietów służy do przydzielania pakietów dla pakietów ARP, RARP, ICMP, IGMP i różnych pakietów sterujących TCP (takich jak SYN, ACK). Jeśli domyślna pula pakietów jest pusta, gdy program NetX musi przydzielić pakiet, może być trzeba przerwać określonej operacji i zwróci komunikat o błędzie, jeśli to możliwe.

### <a name="ip-helper-thread"></a>Wątek pomocnika IP

Każde wystąpienie adresu IP ma wątek pomocnika. Ten wątek jest odpowiedzialny za obsługę całego odroczonego przetwarzania pakietów i wszystkich okresowych przetwarzania. Wątek pomocnika IP jest tworzony w ***nx_ip_create.*** W tym miejscu wątek ma swój stos i priorytet. Należy pamiętać, że pierwsze przetwarzanie w wątku pomocnika IP to zakończenie inicjowania sterownika sieci skojarzonego z usługą tworzenia adresu IP. Po zakończeniu inicjowania sterownika sieci wątek pomocnika uruchamia nieskończoną pętlę do przetwarzania pakietów i okresowych żądań.

> [!IMPORTANT]
> *Jeśli w wątku pomocnika ADRESU IP jest widoczne nieeksjalne zachowanie, zwiększenie jego rozmiaru stosu podczas tworzenia usługi tworzenia adresu IP jest pierwszym krokiem debugowania. Jeśli stos jest zbyt mały, wątek pomocnika IP może prawdopodobnie spowodować nadpisanie pamięci, co może powodować nietypowe problemy.*

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas próby odbierania nieprzetworzonych pakietów IP. Po otrzymaniu pakietu nieprzetworzony nowy pakiet jest nadany do pierwszego wstrzymanego wątku i ten wątek jest wznawiany. Wszystkie usługi NetX do odbierania pakietów mają opcjonalny limit czasu wstrzymania. Po otrzymaniu pakietu lub upłynie limit czasu, wątek aplikacji zostanie wznowiony z odpowiednim stanem ukończenia.

### <a name="ip-statistics-and-errors"></a>Statystyki i błędy adresów IP

Jeśli ta opcja jest włączona, narzędzie NetX śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia adresu IP są utrzymywane następujące statystyki i raporty o błędach:

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

Cechy poszczególnych wystąpień adresów IP znajdują się w bloku sterującym. Zawiera on przydatne informacje, takie jak adresy IP i maski sieci poszczególnych urządzeń sieciowych oraz tabela mapowania adresów IP sąsiadów i fizycznego adresu sprzętowego. Ta struktura jest zdefiniowana w blokach sterowania wystąpienia adresu IP w programie ***nx_api.h,*** które mogą się znaleźć w dowolnym miejscu w pamięci, ale najczęściej kontrolka blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji.

### <a name="static-ip-routing"></a>Statyczny routing IP

Funkcja routingu statycznego umożliwia aplikacji określenie sieci IP i adresu następnego przeskoku dla określonych docelowych adresów IP sieci. Jeśli routing statyczny jest włączony, program NetX przeszukuje statyczną tabelę routingu w poszukiwaniu wpisu pasującego do adresu docelowego pakietu do wysłania. Jeśli dopasowanie nie zostanie znalezione, netx przeszukuje listę interfejsów fizycznych i wybiera źródłowy adres IP i adres następnego przeskoku na podstawie docelowego adresu IP i maski sieci. Jeśli miejsce docelowe nie pasuje do żadnego z adresów IP sterowników sieciowych dołączonych do wystąpienia adresu IP, NetX wybierze interfejs, który jest bezpośrednio połączony z bramą domyślną i używa adresu IP interfejsu jako adresu źródłowego, a brama domyślna jako następny przeskok.

Wpisy można dodawać i usuwać z tabeli routingu statycznego przy użyciu odpowiednio ***nx_ip_static_route_add*** i ***nx_ip_static_route_delete** _ usług. Aby korzystać z routingu statycznego, aplikacja hosta musi włączyć tę funkcję, definiując wartość *__NX_ENABLE_IP_STATIC_ROUTING_*.*

> [!IMPORTANT]
> *Podczas dodawania wpisu do tabeli routingu statycznego program NetX sprawdza, czy istnieje zgodny wpis dla określonego adresu docelowego, który już istnieje w tabeli. Jeśli istnieje, daje preferencję do wpisu z mniejszą siecią (dłuższy prefiks) w masce sieci.*

### <a name="ip-fragmentation"></a>Fragmentacja adresów IP

Urządzenie sieciowe może mieć ograniczenia dotyczące rozmiaru pakietów wychodzących. Ten limit jest nazywany maksymalną jednostką transmisji (MTU). MTU IP jest największy rozmiar ramki IP sterownik warstwy łącza jest w stanie przesłać bez fragmentacji pakietu IP. Podczas fazy inicjowania sterownika urządzenia moduł sterownika musi skonfigurować rozmiar jednostki MTU adresu IP za pośrednictwem usługi ***nx_ip_interface_mtu_set**.*

Chociaż nie jest to zalecane, aplikacja może generować datagramy większe niż podstawowa liczba mtu adresów IP obsługiwana przez urządzenie. Przed przekazaniem takiego datagramu IP warstwa IP musi pofragmentować te pakiety. W przypadku odbierania pofragmentowanych ramek ADRESÓW IP na końcu odbierających muszą być przechowywane wszystkie pofragmentowane ramki ADRESÓW IP z tym samym identyfikatorem fragmentacji i ponownie je zesłać w porządek. Jeśli logika odbierania adresów IP nie może zebrać wszystkich fragmentów w celu przywrócenia oryginalnej ramki adresów IP w czasie, zostaną zwolnione wszystkie fragmenty. Wykrycie utraty pakietów i odzyskanie ich po nim należy do protokołu warstwy górnej.

Aby zapewnić obsługę fragmentacji adresów IP i ponownego zestawu operacji, projektant systemu musi włączyć funkcję fragmentacji adresów IP w systemie NetX przy ***użyciu nx_ip_fragment_enable*** usługi. Jeśli ta funkcja nie jest włączona, przychodzące pofragmentowane pakiety IP są odrzucane, a także pakiety, które przekraczają jednostkę MTU sterownika sieciowego.

> [!IMPORTANT]
> *Logikę fragmentacji adresów IP można całkowicie usunąć, definiując*  * **NX_DISABLE_FRAGMENTATION** _ _when tworzenia bibliotekiNetX. Dzięki temu można zmniejszyć rozmiar kodu NetX.*

## <a name="address-resolution-protocol-arp-in-ip"></a>Protokół ARP (Address Resolution Protocol) w adresie IP

Protokół ARP (Address Resolution Protocol) jest odpowiedzialny za dynamiczne mapowanie 32-bitowych adresów IP na adresy źródłowego nośnika fizycznego (RFC 826). Sieć Ethernet to najbardziej typowy nośnik fizyczny obsługujący adresy 48-bitowe. Potrzeba obsługi ARP jest określana przez sterownik sieciowy dostarczony do ***nx_ip_create*** usługi. Jeśli wymagane jest fizyczne mapowanie, sterownik sieciowy musi ustawić flagę ***nx_interface_address_mapping_needed*** w uchwale interfejsu.

### <a name="arp-enable"></a>Włączanie ARP
Aby usługa ARP działała prawidłowo, musi najpierw zostać włączona przez aplikację przy użyciu ***nx_arp_enable*** usługi. Ta usługa konfiguruje różne struktury danych do przetwarzania ARP, w tym tworzenie obszaru pamięci podręcznej ARP z pamięci dostarczonej do usługi włączania ARP.

### <a name="arp-cache"></a>Pamięć podręczna ARP
Pamięć podręczna ARP może być przeglądana jako tablica wewnętrznych struktur danych mapowania ARP. Każda struktura wewnętrzna jest w stanie utrzymać relację między adresem IP i fizycznym adresem sprzętowym. Ponadto każda struktura danych ma wskaźniki linków, dzięki czemu może być częścią wielu połączonych list.

Aplikacja może odszukać adres IP z pamięci podręcznej ARP, podając sprzętowy adres MAC przy użyciu usługi ***nx_arp_ip_address_find** _, jeśli mapowanie istnieje w tabeli ARP. Podobnie usługa _ *_nx_arp_hardware_address_find_** zwraca adres MAC dla danego adresu IP.


### <a name="arp-dynamic-entries"></a>Wpisy dynamiczne ARP

Domyślnie usługa włączania ARP umieszcza wszystkie wpisy w pamięci podręcznej ARP na liście dostępnych dynamicznych wpisów ARP. Po wykryciu żądania wysłania na niezamapowany adres IP dynamiczny wpis ARP jest przydzielany z tej listy przez platformę NetX. Po alokacji jest ustawiany wpis ARP, a żądanie ARP jest wysyłane do nośnika fizycznego.

Wpis dynamiczny może również zostać utworzony przez ***usługę*** nx_arp_dynamic_entry_set .

> [!IMPORTANT]
> *Jeśli używane są wszystkie dynamiczne wpisy ARP, najsuchomiej używany wpis ARP jest zastępowany nowym mapowaniem.*

### <a name="arp-static-entries"></a>Wpisy statyczne ARP
Aplikacja może również skonfigurować statyczne mapowanie ARP przy użyciu ***nx_arp_static_entry_create*** usługi. Ta usługa przydziela wpis ARP z dynamicznej listy wpisów ARP i umieszcza go na liście statycznej z informacjami mapowania dostarczonymi przez aplikację. Statyczne wpisy ARP nie mogą być ponownie używane ani starzejące się. Aplikacja może usunąć wpis statyczny przy użyciu usługi ***nx_arp_static_entry_delete***.
Aby usunąć wszystkie wpisy statyczne w tabeli ARP, aplikacja może użyć usługi ***nx_arp_static_entries_delete***.

### <a name="automatic-arp-entry"></a>Automatyczny wpis ARP
NetX rejestruje mapowanie adresu IP/MAC elementu równorzędnego po odpowiedziach elementu równorzędnego na żądanie ARP. NetX implementuje również funkcję automatycznego wpisu ARP, w której rejestruje mapowanie adresów IP/MAC elementu równorzędnego na podstawie niechcianych żądań ARP z sieci. Ta funkcja umożliwia wypełnianie tabeli ARP informacjami o elementach równorzędnych, co zmniejsza opóźnienie wymagane do przejścia cyklu żądania/odpowiedzi ARP. Jednak minusem włączenia automatycznego ARP jest to, że tabela ARP zwykle szybko wypełnia się w zajętej sieci z wieloma węzłami w linku lokalnym, co ostatecznie prowadzi do zastąpienia wpisu ARP.

Ta funkcja jest domyślnie włączona. Aby ją wyłączyć, biblioteka NetX musi zostać skompilowana przy użyciu symbolu ***NX_DISABLE_ARP_AUTO_ENTRY*** zdefiniowane.

### <a name="arp-messages"></a>Komunikaty ARP

Jak wspomniano wcześniej, komunikat żądania ARP jest wysyłany, gdy zadanie ADRESU IP wykryje, że mapowanie jest wymagane dla adresu IP. Żądania ARP są wysyłane okresowo (co ***NX_ARP_UPDATE_RATE** _ sekund) do momentu odebrania odpowiedniej odpowiedzi ARP. Łączna liczba żądań *_NX_ARP_MAXIMUM_RETRIES_** ARP jest podjęto przed porzuconą próbą ARP. Po otrzymaniu odpowiedzi ARP skojarzone informacje o adresie fizycznym są przechowywane we wpisie ARP, który znajduje się w pamięci podręcznej.

W przypadku systemów wieloadresowych NetX określa, który interfejs wysyłać żądania IRP i odpowiedzi na podstawie określonego adresu docelowego.

> [!IMPORTANT]
> *Wychodzące pakiety IP są kolejkowane, gdy NetX czeka na odpowiedź ARP. Liczba wychodzących pakietów IP* *w kolejce jest definiowana przez stałą*  * **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX odpowiada również na żądania ARP z innych węzłów w lokalnej sieci IP. Gdy zostanie wykonane zewnętrzne żądanie ARP, które pasuje do bieżącego adresu IP interfejsu, który odbiera żądanie ARP, netx tworzy komunikat odpowiedzi ARP zawierający bieżący adres fizyczny.

Formaty żądań i odpowiedzi ARP sieci Ethernet przedstawiono na rysunku 6 i opisano je poniżej:

| Pole żądania/odpowiedzi       | Przeznaczenie    |
|------------------------------|-----------------|
| Adres docelowy sieci Ethernet | To 6-bajtowe pole zawiera adres docelowy odpowiedzi ARP i jest emisją (wszystkie jedynki) dla żądań ARP. To pole jest konfigurowany przez sterownik sieciowy. |
| Adres źródłowy sieci Ethernet      | To 6-bajtowe pole zawiera adres nadawcy żądania lub odpowiedzi ARP i jest ono ustawiane przez sterownik sieciowy. |
| Typ ramki                   | To 2-bajtowe pole zawiera typ obecnej ramki Ethernet, a w przypadku żądań i odpowiedzi ARP jest to równe 0x0806. Jest to ostatnie pole, które sterownik sieciowy jest odpowiedzialny za konfigurowanie. |
| Typ sprzętu                | To 2-bajtowe pole zawiera typ sprzętu, który jest 0x0001 dla sieci Ethernet. |
| Typ protokołu                | To 2-bajtowe pole zawiera typ protokołu, który jest 0x0800 dla adresów IP. |
| Rozmiar sprzętu                | To 1-bajtowe pole zawiera adres sprzętowy o rozmiarze 6 dla adresów Ethernet. |


![Format pakietu ARP](./media/user-guide/arp-packet-format.png)

**RYSUNEK 6. Format pakietu ARP**

| Pole żądania/odpowiedzi | Przeznaczenie  |
|---|---|
| Rozmiar protokołu | To 1-bajtowe pole zawiera rozmiar adresu IP, czyli 4 dla adresów IP.  |
| Kod operacji | To 2-bajtowe pole zawiera operację dla tego pakietu ARP. Żądanie ARP jest określane z wartością 0x0001, a odpowiedź ARP jest reprezentowana przez wartość 0x0002.  |
| Adres Ethernet nadawcy | To 6-bajtowe pole zawiera adres Ethernet nadawcy. |
| Adres IP nadawcy | To 4-bajtowe pole zawiera adres IP nadawcy. |
| Docelowy adres Ethernet | To 6-bajtowe pole zawiera adres Ethernet obiektu docelowego. |
| Docelowy adres IP | To 4-bajtowe pole zawiera adres IP obiektu docelowego. |

> [!IMPORTANT]
> *Żądania IRP i odpowiedzi są pakietami na poziomie sieci Ethernet. Wszystkie inne pakiety TCP/IP są hermetyzowane przez nagłówek pakietu IP.*

> [!IMPORTANT]
> *Wszystkie komunikaty protokołu ARP w implementacji PROTOKOŁU TCP/IP powinny być w big endian formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

### <a name="arp-aging"></a>Wiekowanie ARP

NetX obsługuje automatyczne dynamiczne unieważnienie wpisu ARP. ***NX_ARP_EXPIRATION_RATE** _specifies liczba sekund, przez które ustanowione mapowanie adresu IP na fizyczne pozostaje prawidłowe. Po wygaśnięciu wpis ARP jest usuwany z pamięci podręcznej ARP. Przy następnej próbie wysłania na odpowiedni adres IP zostanie skierowane nowe żądanie ARP. Ustawienie wartości *__ NX_ARP_EXPIRATION_RATE_** na zero powoduje wyłączenie przedawniania się zasad ARP, co jest konfiguracją domyślną.

### <a name="arp-defend"></a>Obrona ARP

Gdy zostanie odebrane żądanie ARP lub pakiet odpowiedzi ARP, a nadawca ma ten sam adres IP, co powoduje konflikt z adresem IP tego węzła, netx wysyła żądanie ARP dla tego adresu jako ochronę. Jeśli pakiet ARP o konflikcie zostanie odebrany więcej niż raz w ciągu 10 sekund, NetX nie wyśle więcej pakietów obronnych. Domyślny interwał 10 sekund może być ponownie definiowany przez ***** NX_ARP_DEFEND_INTERVAL _. To zachowanie jest zgodna z zasadami określonymi w 2.4(c) RFC5227. Ponieważ Windows XP ignoruje anons ARP jako odpowiedź dla sondy ARP, użytkownik może zdefiniować wartość _*_NX_ARP_DEFEND_BY_REPLY_**, aby wysłać odpowiedź ARP jako dodatkową wiadomość e-mail.

### <a name="arp-statistics-and-errors"></a>Statystyki i błędy ARP

Jeśli ta opcja jest włączona, oprogramowanie NetX ARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla przetwarzania protokołu ARP każdego adresu IP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych żądań ARP
- Łączna liczba odebranych żądań ARP
- Łączna liczba wysłanych odpowiedzi ARP
- Łączna liczba odebranych odpowiedzi ARP
- Łączna liczba wpisów dynamicznych ARP
- Łączna liczba wpisów statycznych ARP
- Łączna liczba wpisów Zwęgłego ARP
- Łączna liczba nieprawidłowych komunikatów ARP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji w nx_arp_info_get ***usługi.***

## <a name="reverse-address-resolution-protocol-rarp-in-ip"></a>Protokół RARP (Reverse Address Resolution Protocol) w adresie IP

Protokół RARP (Reverse Address Resolution Protocol) to protokół żądający przypisania sieci dla 32-bitowych adresów IP hosta (RFC 903). Odbywa się to za pośrednictwem żądania RARP i jest okresowo kontynuowane, dopóki członek sieci nie przypisze adresu IP do interfejsu sieciowego hosta w odpowiedzi PROTOKOŁU RARP. Aplikacja tworzy wystąpienie adresu IP przez ***usługę*** nx_ip_create bez adresu IP. Jeśli protokół RARP jest włączony przez aplikację, może użyć protokołu RARP, aby zażądać adresu IP z serwera sieciowego dostępnego za pośrednictwem interfejsu, który ma zerowy adres IP.

### <a name="rarp-enable"></a>Włączanie rarp

Aby użyć protokołu RARP, aplikacja musi utworzyć wystąpienie ip o adresie IP o wartości 0, a następnie włączyć protokół RARP przy użyciu usługi ***nx_rarp_enable***. W przypadku systemów wieloadresowych co najmniej jedno urządzenie sieciowe skojarzone z wystąpieniem adresu IP musi mieć adres IP o wartości zero. Przetwarzanie RARP okresowo wysyła komunikaty żądań RARP dla systemu NetX wymagającego adresu IP, dopóki nie zostanie odebrana prawidłowa odpowiedź RARP z wyznaczonym adresem IP sieci. W tym momencie przetwarzanie RARP jest ukończone.

Po włączeniu funkcji RARP jest ona automatycznie wyłączana po rozpoznaniu wszystkich adresów interfejsu. Aplikacja może wymusić zakończenie obsługi rarp przy użyciu ***usługi*** nx_rarp_disable .

###  <a name="rarp-request"></a>Żądanie RARP

Format pakietu żądania RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku 6 w temacie [Komunikaty ARP.](#arp-messages) Jedyną różnicą jest to, że pole typu ramki 0x8035 a pole *Kod* operacji to 3, co oznacza żądanie RARP. Jak wspomniano wcześniej, żądania RARP będą wysyłane okresowo (co NX_RARP_UPDATE_RATE sekund), ***dopóki*** nie zostanie odebrana odpowiedź RARP z przypisanym przez sieć adresem IP.

> [!IMPORTANT]
> *Wszystkie komunikaty RARP w implementacji TCP/IP powinny być w big endian formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

### <a name="rarp-reply"></a>Odpowiedź RARP

Komunikaty odpowiedzi RARP są odbierane z sieci i zawierają adres IP przypisany przez sieć dla tego hosta. Format pakietu odpowiedzi RARP jest niemal identyczny z pakietem ARP pokazanym na rysunku 6. Jedyną różnicą jest to, że pole typu ramki jest 0x8035 a pole *Kod* operacji to 4, które wyznacza odpowiedź RARP. Po otrzymaniu adres IP jest konfigurny w wystąpieniu adresu IP, okresowe żądanie RARP jest wyłączone, a wystąpienie adresu IP jest teraz gotowe do normalnego działania sieci.

W przypadku hostów wieloadresowych adres IP jest stosowany do interfejsu sieciowego, który żąda. Jeśli inne interfejsy sieciowe nadal żądają przypisania adresu IP, okresowa usługa RARP będzie kontynuowana do momentu rozwiązania wszystkich żądań adresów IP interfejsu.

> [!IMPORTANT]
> *Aplikacja nie powinna używać wystąpienia adresu IP, dopóki przetwarzanie RARP nie zostanie ukończone. Ta **nx_ip_status_check** może być używana przez aplikacje do oczekiwania na ukończenie procesu RARP. W przypadku systemów wieloadresowych aplikacja nie powinna używać interfejsu żądającego, dopóki przetwarzanie RARP nie zostanie ukończone w tym interfejsie. Stan adresu IP na urządzeniu pomocniczym można sprawdzić za pomocą **nx_ip_interface_status_check** pomocniczej.*

### <a name="rarp-statistics-and-errors"></a>Statystyki i błędy RARP

Jeśli ta opcja jest włączona, oprogramowanie NetX RARP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Następujące statystyki i raporty o błędach są utrzymywane dla przetwarzania RARP każdego adresu IP:

- Łączna liczba wysłanych żądań RARP
- Łączna liczba odebranych odpowiedzi RARP
- Łączna liczba nieprawidłowych komunikatów RARP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji w nx_rarp_info_get ***service.***

## <a name="internet-control-message-protocol-icmp"></a>Protokół ICMP (Internet Control Message Protocol)

Protokół ICMP (Internet Control Message Protocol) jest ograniczony do przekazywania informacji o błędach i kontroli między członkami sieci IP.

Podobnie jak w przypadku większości innych komunikatów warstwy aplikacji (np. TCP/IP), komunikaty ICMP są hermetyzowane przez nagłówek IP z oznaczeniem protokołu ICMP.

### <a name="icmp-statistics-and-errors"></a>Statystyki i błędy ICMP

Jeśli ta opcja jest włączona, netX śledzi kilka statystyk ICMP i błędów, które mogą być przydatne dla aplikacji. Dla przetwarzania protokołu ICMP poszczególnych adresów IP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych ping ICMP
- Łączna liczba limitów czasu ping ICMP
- Całkowita liczba wstrzymanych wątków ping ICMP
- Łączna liczba odebranych odpowiedzi ping ICMP
- Łączna liczba błędów sumy kontrolnej ICMP
- Łączna liczba nieobsłużonych komunikatów ICMP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji za ***nx_icmp_info_get*** usługi.

### <a name="icmp-enable"></a>Włączanie ICMP
Aby komunikaty ICMP można było przetworzyć za pomocą programu NetX, aplikacja musi wywołać usługę ***nx_icmp_enable,*** aby włączyć przetwarzanie ICMP. Po zakończeniu aplikacja może wysyłać żądania ping i pole przychodzących pakietów ping.

### <a name="icmp-echo-request"></a>Żądanie echa ICMP
Żądanie echa to jeden z typów komunikatów ICMP, który jest zwykle używany do sprawdzania istnienia określonego węzła w sieci, identyfikowanego na podstawie jego adresu IP hosta. Popularne polecenie ping jest implementowane przy użyciu komunikatów żądania echa/odpowiedzi echa ICMP. Jeśli określony host jest obecny, jego stos sieciowy przetwarza żądanie ping i odpowiedzi z odpowiedzią ping. Rysunek 7 zawiera szczegóły dotyczące formatu komunikatu ping ICMP.

![Komunikat ping ICMP](./media/user-guide/icmp-ping-message.png)

**RYSUNEK 7. Komunikat ping ICMP**

> [!IMPORTANT]
> *Wszystkie komunikaty ICMP w implementacji TCP/IP powinny być w big endian formatem. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

W poniższej tabeli opisano format nagłówka ICMP:

| Pole nagłówka    | Przeznaczenie |
|-----------------|---------------------------------------------------|
| Typ            | To pole określa komunikat ICMP (bity 31–24). Najczęściej spotykane są: 0 Echo Reply 8 Echo Request |
| Kod            | To pole jest kontekstem specyficznym dla pola typu (bity 23–16). W przypadku żądania echa lub odpowiedzi kod jest ustawiony na zero. |
| Suma kontrolna        | To pole zawiera 16-bitową sumę kontrolną dopełnianą komunikatu ICMP, w tym cały nagłówek ICMP rozpoczynający się od pola Typ. Przed wygenerowaniem sumy kontrolnej pole sumy kontrolnej jest czyszowane.                 |
| Identyfikacja  | To pole zawiera wartość identyfikatora identyfikującą hosta; Host powinien używać identyfikatora wyodrębnionego z żądania ECHO w odpowiedzi ECHO (bity 31–16). |
| Numer sekwencyjny | To pole zawiera wartość identyfikatora; Host powinien używać identyfikatora wyodrębnionego z żądania ECHO w odpowiedzi ECHO (bity 31–16). W przeciwieństwie do pola identyfikatora ta wartość zmieni się w kolejnym żądaniu echa z tego samego hosta (bity 15-0). |


### <a name="icmp-echo-response"></a>Odpowiedź echa ICMP
Odpowiedź ping to inny typ komunikatu ICMP, który jest generowany wewnętrznie przez składnik ICMP w odpowiedzi na zewnętrzne żądanie ping. Oprócz potwierdzenia odpowiedź ping zawiera również kopię danych użytkownika podanych w żądaniu ping.

## <a name="internet-group-management-protocol-igmp"></a>Protokół IGMP (Internet Group Management Protocol)

Protokół IGMP (Internet Group Management Protocol) udostępnia urządzenie do komunikacji ze swoimi sąsiadami i routerami, które zamierza odbierać lub dołączać do grupy multiemisji adresów IP (RFC 1112 i RFC 2236). Grupa multiemisji jest zasadniczo dynamiczną kolekcją składowych sieci i jest reprezentowana przez adres IP klasy D. Członkowie grupy multiemisji mogą odejść w dowolnym momencie, a nowi członkowie mogą dołączyć w dowolnym momencie. Koordynacja biorąca udział w dołączaniu do grupy i opuszczaniu grupy jest odpowiedzialna za IGMP.

### <a name="igmp-enable"></a>Włączanie IGMP

Aby można było wykonać dowolne działanie multiemisji w programie NetX, aplikacja musi wywołać nx_igmp_enable ***usługi.*** Ta usługa wykonuje podstawowe inicjowanie IGMP w ramach przygotowania do żądań multiemisji.

### <a name="multicast-ip-addressing"></a>Adresowanie IP multiemisji

Jak wspomniano wcześniej, adresy multiemisji są w rzeczywistości adresami IP klasy D, jak pokazano na rysunku 4 na stronie 58. Dolne 28-bitowe wartości adresu klasy D odpowiadają identyfikatorowi grupy multiemisji. Istnieje szereg wstępnie zdefiniowanych adresów multiemisji. Jednak wszystkie *hosty adres* (244.0.0.1) jest szczególnie ważne dla przetwarzania IGMP. Adres *wszystkich hostów jest* używany przez routery do wykonywania zapytań o wszystkie elementy członkowskie multiemisji w celu zgłaszania, do których grup multiemisji należą.

### <a name="physical-address-mapping-in-ip"></a>Mapowanie adresów fizycznych w adresie IP

Adresy multiemisji klasy D są mapowe bezpośrednio na fizyczne adresy Ethernet w zakresie od 01.00.5e.00.00 do 01.00.5e.7f.ff.ff. Niższe 23 bity adresu ip multiemisji mapować bezpośrednio do niższych 23 bitów adresu Ethernet.

### <a name="multicast-group-join"></a>Sprzężenia grupy multiemisji

Aplikacje, które muszą dołączyć do określonej grupy multiemisji, mogą to zrobić, wywołując ***usługę nx_igmp_multicast_join*** multiemisji. Ta usługa śledzi liczbę żądań dołączenia do tej grupy multiemisji. Jeśli jest to pierwsze żądanie aplikacji dotyczące dołączenia do grupy multiemisji, w sieci podstawowej zostanie wysłany raport IGMP wskazujący zamiar dołączenia tego hosta do grupy. Następnie sterownik sieciowy jest wywoływany w celu skonfigurowania nasłuchiwania pakietów z adresem Ethernet dla tej grupy multiemisji.

W systemie wieloadresowym, jeśli grupa multiemisji jest dostępna za pośrednictwem określonego interfejsu, aplikacja musi używać usługi ***nx_igmp_multicast_interface_join zamiast*** ***nx_igmp_multicast_join**,*, która jest ograniczona do grup multiemisji w sieci podstawowej.

### <a name="multicast-group-leave"></a>Pozostawienie grupy multiemisji

Aplikacje, które muszą opuścić wcześniej dołączone grupy multiemisji, mogą to zrobić, wywołując ***usługę nx_igmp_multicast_leave*** multiemisji. Ta usługa zmniejsza liczbę wewnętrzną skojarzoną z tym, ile razy grupa została do niej dołączenia. Jeśli nie ma żadnych żądań zaległych sprzężenia dla grupy, sterownik sieciowy jest wywoływany w celu wyłączenia nasłuchiwania pakietów przy użyciu adresu Ethernet tej grupy multiemisji

### <a name="multicast-loopback"></a>Sprzężenia zwrotne multiemisji

Aplikacja może chcieć odbierać ruch multiemisji pochodzący z jednego ze źródeł w tym samym węźle. Wymaga to, aby składnik multiemisji IP miał włączoną sprzężenia zwrotnego przy użyciu usługi ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>Komunikat raportu IGMP

Gdy aplikacja dołącza do grupy multiemisji, za pośrednictwem sieci jest wysyłany komunikat raportu IGMP wskazujący zamiar dołączenia hosta do określonej grupy multiemisji. Format komunikatu raportu IGMP przedstawiono na rysunku 8. Adres grupy multiemisji jest używany zarówno dla komunikatu grupy w komunikacie raportu IGMP, jak i docelowego adresu IP.

![Komunikat raportu IGMP](./media/user-guide/igmp-report-message.png)

**RYSUNEK 8. Komunikat raportu IGMP**

Na powyższej ilustracji (Rysunek 8) nagłówek IGMP zawiera pole wersji/typu, maksymalny czas odpowiedzi, pole sumy kontrolnej i pole adresu grupy multiemisji. W przypadku komunikatów IGMPv1 pole Maksymalny czas odpowiedzi jest zawsze ustawione na zero, ponieważ nie jest to część protokołu IGMPv1. Pole Maksymalny czas odpowiedzi jest ustawiane, gdy host odbiera komunikat IGMP typu zapytania i czyszczy go, gdy host odbiera komunikat o typie raportu innego hosta zgodnie z definicją protokołu IGMPv2.

Poniżej opisano format nagłówka IGMP:

| **Pole nagłówka**          | **Cel** |
|-----------------------|--------------------------------------------------------------------|
| Wersja               | To pole określa wersję IGMP (bity 31–28).                                                                               |
| Typ                  | To pole określa typ komunikatu IGMP (bity 27–24).                                                                       |
| Maksymalny czas odpowiedzi | Nie jest używany w protokole IGMPv1. W przypadku protokołu IGMPv2 to pole służy jako maksymalny czas odpowiedzi.                                                      |
| Suma kontrolna              | To pole zawiera 16-bitową sumę kontrolną dopełnianą komunikatu IGMP rozpoczynającą się od wersji IGMP (bity 0–15) |
| Adres grupy         | 32-bitowy adres IP grupy D klasy D |


Komunikaty raportów IGMP są również wysyłane w odpowiedzi na komunikaty zapytań IGMP wysyłane przez router multiemisji. Routery multiemisji okresowo wysyłają komunikaty zapytania, aby zobaczyć, które hosty nadal wymagają członkostwa w grupie. Komunikaty zapytań mają taki sam format jak komunikat raportu IGMP pokazany na rysunku 8. Jedyną różnicą jest to, że typ IGMP jest równy 1, a pole adresu grupy ma wartość 0. Komunikaty zapytania IGMP są wysyłane do adresu IP *wszystkich* hostów przez router multiemisji. Host, który nadal chce zachować członkostwo w grupie, odpowiada przez wysłanie innego komunikatu raportu IGMP.

> [!IMPORTANT]
> *Wszystkie komunikaty w implementacji TCP/IP powinny być w **big endian** formatem. W tym formacie najbardziej znaczący bajt słowa znajduje się w najniższym adresie bajtowym.*

### <a name="igmp-statistics-and-errors"></a>Statystyki i błędy IGMP

Jeśli ta opcja jest włączona, oprogramowanie NetX IGMP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego przetwarzania protokołu IGMP dla każdego adresu IP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych raportów IGMP
- Łączna liczba odebranych zapytań IGMP
- Łączna liczba błędów sumy kontrolnej IGMP
- Całkowita liczba przyłączone bieżących grup IGMP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji w ***nx_igmp_info_get*** service.

## <a name="user-datagram-protocol-udp"></a>Protokół UDP (User Datagram Protocol)

Protokół UDP (User Datagram Protocol) zapewnia najprostszą formę transferu danych między członkami sieci (RFC 768). Pakiety danych UDP są wysyłane z jednego członka sieci do innego w najlepszy sposób; tj. nie ma wbudowanego mechanizmu potwierdzania przez adresata pakietu. Ponadto wysłanie pakietu UDP nie wymaga wcześniejszego nawiązanego połączenia. W związku z tym transmisja pakietów UDP jest bardzo wydajna.

### <a name="udp-header"></a>Nagłówek UDP
Rozwiązanie UDP umieszcza prosty nagłówek pakietu przed danymi aplikacji podczas transmisji i usuwa podobny nagłówek UDP z pakietu w odbiorze przed dostarczeniem odebranego pakietu UDP do aplikacji. Protokół UDP wykorzystuje protokół IP do wysyłania i odbierania pakietów, co oznacza, że przed nagłówkiem UDP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 9 przedstawia format nagłówka UDP.

![Nagłówek UDP](./media/user-guide/udp-header.png)

**RYSUNEK 9. Nagłówek UDP**

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji protokołu UDP/IP będą w big endian formacie. W tym formacie najbardziej znaczący bajt słowa znajduje się w najniższym adresie bajtowym.*

Poniżej opisano format nagłówka UDP:

| Pole nagłówka                   | Przeznaczenie |
|--------------------------------|---------------------------------------------|
| 16-bitowy numer portu źródłowego      | To pole zawiera port, z którego jest wysyłany pakiet UDP. Prawidłowe porty UDP mają zakres od 1 do 0xFFFF. |
| 16-bitowy numer portu docelowego | To pole zawiera port UDP, do którego jest wysyłany pakiet. Prawidłowe porty UDP mają zakres od 1 do 0xFFFF.   |
| 16-bitowa długość protokołu UDP   | To pole zawiera liczbę bajtów w pakiecie UDP, w tym rozmiar nagłówka UDP.                                  |
| 16-bitowa sumy kontrolne UDP | To pole zawiera 16-bitową sumy kontrolnej dla pakietu, w tym nagłówek UDP, obszar danych pakietu i nagłówek pseudo-IP. |

### <a name="udp-enable"></a>Włączanie protokołu UDP

Aby możliwe było przesyłanie pakietów UDP, aplikacja musi najpierw włączyć funkcję UDP przez wywołanie ***nx_udp_enable*** usługi. Po włączeniu aplikacja może wysyłać i odbierać pakiety UDP.

### <a name="udp-socket-create"></a>Tworzenie gniazda UDP

Gniazda UDP są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Początkowy typ usługi, czas eksploatacji i głębokość kolejki odbierania są definiowane przez nx_udp_socket_create ***usługi.*** Nie ma żadnych ograniczeń liczby gniazd UDP w aplikacji.

### <a name="udp-checksum"></a>Sumy kontrolne UDP

Protokół UDP określa 16-bitową podsumę kontrolną dopełnianą przez użytkownika, która obejmuje nagłówek pseudowłaściwego adresu IP (składający się ze źródłowego adresu IP, docelowego adresu IP i słowa adresu IP protokołu/długości), nagłówka UDP i danych pakietów UDP. Jeśli obliczona wartość sumy kontrolnej UDP wynosi 0, jest ona przechowywana jako wszystkie (0xFFFF). Jeśli gniazdo wysyłające ma wyłączono logikę sumy kontrolnej UDP, zero jest umieszczane w polu sumy kontrolnej UDP, aby wskazać, że nie obliczono sumy kontrolnej. Jeśli sumy kontrolne UDP nie są zgodne z obliczoną sumy kontrolnej przez odbiornik, pakiet UDP jest po prostu odrzucany.

W sieci IP sumy kontrolne UDP są opcjonalne. NetX umożliwia aplikacji włączanie lub wyłączanie obliczeń sumy kontrolnej UDP na podstawie gniazd. Domyślnie logika sumy kontrolnej gniazda UDP jest włączona. Aplikacja może wyłączyć logikę sumy kontrolnej dla określonego gniazda UDP, wywołując ***nx_udp_socket_checksum_disable*** usługę.

Niektóre kontrolery Ethernet są w stanie wygenerować sumy kontrolne UDP na bieżąco. Jeśli system może używać funkcji obliczania sumy kontrolnej sprzętu, bibliotekę NetX można utworzyć bez logiki sumy kontrolnej. Aby wyłączyć sumy kontrolne oprogramowania UDP, biblioteka NetX musi być budowaną z następującymi zdefiniowanymi symbolami: ***NX_DISABLE_UDP_TX_CHECKSUM*** i ***NX_DISABLE_UDP_RX_CHECKSUM* _ (opisane w rozdziale *[2).](chapter2.md) Opcje konfiguracji**** całkowicie usuwają logikę sumy kontrolnej UDP z systemu NetX, podczas gdy wywołanie usługi _nx_udp_socket_checksum_disable umożliwia aplikacji wyłączenie przetwarzania sumy kontrolnej protokołu UDP protokołu IP dla każdego gniazda.

### <a name="udp-ports-and-binding"></a>Porty I powiązanie UDP

Port UDP to logiczny punkt końcowy w protokole UDP. W składniku UDP netX znajduje się 65 535 prawidłowych portów, od 1 do 0xFFFF. Aby wysyłać lub odbierać dane UDP, aplikacja musi najpierw utworzyć gniazdo UDP, a następnie powiązać je z żądanym portem. Po powiązaniu gniazda UDP z portem aplikacja może wysyłać i odbierać dane na tym gnieździe.

### <a name="udp-fast-pathtrade"></a>Szybka ścieżka protokołu UDP&trade;

Szybka ścieżka protokołu UDP to nazwa ścieżki o małym narzucie &trade; pakietów za pośrednictwem implementacji protokołu UDP NetX. Wysłanie pakietu UDP wymaga tylko kilku wywołań funkcji: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_, i eventual call do sterownika sieciowego. _*_nx_udp_socket_send_*_ jest dostępna w programie NetX dla istniejących aplikacji NetX i ma zastosowanie tylko w przypadku pakietów IP. Preferowaną metodą jest jednak użycie usługi *__nx_udp_socket_send_** omówionej poniżej. W przypadku odbierania pakietów UDP pakiet UDP jest umieszczany w odpowiedniej kolejce odbierania gniazda UDP lub dostarczany do zawieszonego wątku aplikacji w jednym wywołaniu funkcji z przetwarzania przerwań odbioru sterownika sieciowego. Ta wysoce zoptymalizowana logika wysyłania i odbierania pakietów UDP jest istotą technologii szybka ścieżka UDP.

### <a name="udp-packet-send"></a>Wysyłanie pakietów UDP

Wysyłanie danych UDP za pośrednictwem sieci IP można łatwo wykonać, wywołując funkcję ***nx_udp_socket_send** _. Obiekt wywołujący musi ustawić wersję adresu IP w _IP adres*. NetX określi najlepszy adres źródłowy dla przesyłanych pakietów UDP na podstawie docelowego adresu IP. Ta usługa umieszcza nagłówek UDP przed danymi pakietu i wysyła go do sieci przy użyciu wewnętrznej procedury wysyłania adresów IP. Wysyłanie pakietów UDP nie jest wstrzymane, ponieważ wszystkie transmisje pakietów UDP są przetwarzane natychmiast.

W przypadku miejsc docelowych multiemisji lub emisji aplikacja powinna określić źródłowy adres IP do użycia, jeśli urządzenie NetX ma wiele adresów IP do wyboru. Można to zrobić za pomocą usługi ***nx_udp_socket_interface_send.***

> [!IMPORTANT]
> *Jeśli **nx_udp_socket_send** jest używany do przesyłania pakietów multiemisji lub emisji, adres IP pierwszego interfejsu jest używany jako adres źródłowy.*

> [!IMPORTANT]
> *Jeśli dla tego gniazda jest włączona logika sumy kontrolnej UDP, operacja sumy kontrolnej jest wykonywana w kontekście wątku wywołującego, bez blokowania dostępu do struktur danych UDP lub IP.*

> [!NOTE]
> *Dane ładunku UDP przechowywane w NX_PACKET **powinny** znajdować się na granicy długich słów. Aplikacja musi pozostawić wystarczającą ilość miejsca między wstępnym wskaźnikiem a wskaźnikiem uruchamiania danych dla netX, aby umieścić nagłówki UDP, IP i nośnika fizycznego.*

### <a name="udp-packet-receive"></a>Odbieranie pakietów UDP

Wątki aplikacji mogą odbierać pakiety UDP z określonego gniazda przez wywołanie ***nx_udp_socket_receive***. Funkcja odbierania gniazda dostarcza najstarszy pakiet w kolejce odbierania gniazda. Jeśli w kolejce odbierania nie ma pakietów, wywołujący wątek może wstrzymać (z opcjonalnym limitem czasu) do momentu otrzymania pakietu.

Przetwarzanie pakietów odbieranych przez protokołu UDP (zwykle wywoływane z procedury obsługi przerwań odbierania sterowników sieciowych) jest odpowiedzialne za umieszczenie pakietu w kolejce odbierania gniazda UDP lub dostarczenie go do pierwszego wstrzymanego wątku czekającego na pakiet. Jeśli pakiet jest w kolejce, przetwarzanie odbierania sprawdza również maksymalną głębokość kolejki odbierania skojarzoną z gniazdem. Jeśli ten nowo dodany pakiet w kolejce przekroczy głębokość kolejki, najstarszy pakiet w kolejce zostanie odrzucony.

### <a name="udp-receive-notify"></a>Powiadomienie o odbierce UDP

Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, ***należy nx_udp_socket_receive_notify*** funkcji. Ta funkcja rejestruje funkcję wywołania zwrotnego pakietów odbioru dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, wykonywana jest funkcja wywołania zwrotnego.

Zawartość funkcji wywołania zwrotnego jest specyficzna dla aplikacji. Jednak najprawdopodobniej zawiera on logikę, która informuje wątek przetwarzania, że pakiet jest teraz dostępny na odpowiednim gnieździe.

### <a name="peer-address-and-port"></a>Adres i port elementu równorzędnego

Po odebraniu pakietu UDP aplikacja może znaleźć adres IP i numer portu nadawcy przy użyciu usługi nx_udp_packet_info_extract ***.*** Po pomyślnym powrocie ta usługa dostarcza informacje o adresie IP nadawcy, numerze portu nadawcy i interfejsie lokalnym, za pośrednictwem którego odebrano pakiet.

### <a name="thread-suspension"></a>Zawieszenie wątku

Jak wspomniano wcześniej, wątki aplikacji mogą zostać wstrzymane podczas próby odbierania pakietu UDP na określonym porcie UDP. Po otrzymaniu pakietu na tym porcie zostaje on nadany do pierwszego wstrzymanego wątku, a następnie wznawiany. Opcjonalny limit czasu jest dostępny w przypadku wstrzymania pakietu odbierania UDP, funkcji dostępnej dla większości usług NetX.

### <a name="udp-socket-statistics-and-errors"></a>Statystyki i błędy gniazd UDP

Jeśli ta opcja jest włączona, oprogramowanie netX UDP socket śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/UDP są utrzymywane następujące statystyki i raporty o błędach:

- Łączna liczba wysłanych pakietów UDP
- Całkowita liczba wysłanych bajtów UDP
- Łączna liczba odebranych pakietów UDP
- Całkowita liczba odebranych bajtów UDP
- Łączna liczba nieprawidłowych pakietów UDP
- Łączna liczba porzucanych pakietów odbierania UDP
- Łączna liczba błędów sumy kontrolnej odbierania UDP
- Wysłane pakiety gniazd UDP
- Wysłane bajty gniazd UDP
- Odebrane pakiety gniazd UDP
- Odebrano bajty gniazda UDP
- Pakiety gniazd UDP w kolejce
- Porzucone pakiety odbierane przez gniazda UDP
- Błędy sumy kontrolnej gniazda UDP

Wszystkie te statystyki i raporty o błędach są dostępne dla aplikacji z usługą ***nx_udp_info_get*** dla statystyk UDP zmassowanych dla wszystkich gniazd UDP oraz dla usługi ***nx_udp_socket_info_get*** dla statystyk UDP na określonym gnieździe UDP.

### <a name="udp-socket-control-block-nx_udp_socket"></a>Blok sterowania gniazdami UDP NX_UDP_SOCKET

Charakterystyka każdego gniazda UDP znajduje się w skojarzonym bloku **NX_UDP_SOCKET** sterowania. Zawiera on przydatne informacje, takie jak link do struktury danych IP, interfejs sieciowy do wysyłania i odbierania ścieżek, powiązany port i kolejka pakietów odbioru. Ta struktura jest zdefiniowana w **_nx_api.h._**

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Protokół Transmission Control Protocol (TCP) zapewnia niezawodny transfer danych strumienia między dwoma członkami sieci (RFC 793). Wszystkie dane wysyłane od jednego członka sieci są weryfikowane i potwierdzane przez odbierający członek. Ponadto dwa elementy członkowskie muszą nawiązane połączenie przed transferem danych. Wszystko to zapewnia niezawodny transfer danych. Jednak wymaga to znacznie większej nakładu pracy niż opisany wcześniej transfer danych UDP.

### <a name="tcp-header"></a>Nagłówek TCP

W przypadku transmisji nagłówek TCP jest umieszczany przed danymi od użytkownika. W przypadku odbioru nagłówek TCP jest usuwany z pakietu przychodzącego, pozostawiając aplikacji tylko dane użytkownika. Protokół TCP używa protokołu IP do wysyłania i odbierania pakietów, co oznacza, że przed nagłówkiem TCP znajduje się nagłówek IP, gdy pakiet znajduje się w sieci. Rysunek 10 przedstawia format nagłówka TCP.

![Nagłówek TCP](./media/user-guide/tcp-header.png)

**RYSUNEK 10. Nagłówek TCP**

Poniżej opisano format nagłówka TCP:

| Pole nagłówka | Przeznaczenie |
|---|---|
| 16-bitowy numer portu źródłowego | To pole zawiera port, na który jest wysyłany pakiet TCP. Prawidłowe porty TCP mają zakres od 1 do 0xFFFF. |
| 16-bitowy numer portu docelowego | To pole zawiera port TCP, do który jest wysyłany pakiet. Prawidłowe porty TCP mają zakres od 1 do 0xFFFF. |
| 32-bitowy numer sekwencji | To pole zawiera numer sekwencji danych wysyłanych z tego końca połączenia. Oryginalna sekwencja jest ustalana podczas początkowej sekwencji połączenia między dwoma węzłami TCP. Każdy transfer danych od tego momentu powoduje przyrost numeru sekwencji o liczbę wysłanych bajtów. |
| 32-bitowy numer potwierdzenia | To pole zawiera numer sekwencji odpowiadający ostatniej bajtowi odebranemu przez tę stronę połączenia. Służy do określania, czy wcześniej wysłane dane zostały pomyślnie odebrane przez drugi koniec połączenia. |
| 4-bitowa długość nagłówka           | To pole zawiera liczbę 32-bitowych wyrazów w nagłówku TCP. Jeśli w nagłówku TCP nie ma żadnych opcji, to pole ma rozmiar 5. |
| Bity kodu 6-bitowego               | To pole zawiera sześć różnych bitów kodu używanych do wskazywania różnych informacji sterujących skojarzonych z połączeniem. Bity sterujące są zdefiniowane w następujący sposób: |



| Nazwa | Bitowych | Znaczenie                                                     |
|------|-----|-------------------------------------------------------------|
| Adres URL  | 21  | Pilne dane są obecne                                         |
| Ack  | 20  | Numer potwierdzenia jest prawidłowy                             |
| Psh  | 19  | Natychmiastowa obsługa tych danych                                |
| Rst  | 18  | Resetowanie połączenia                                        |
| Syn  | 17  | Synchronizowanie numerów sekwencji (używanych do nawiązywania połączenia) |
| FIN  | 16  | Nadawca kończy przesyłanie (używane do zamykania połączenia) |

**Okno 16-bitowe**

To pole jest używane do sterowania przepływem. Zawiera on liczbę bajtów, które gniazdo może obecnie odbierać. Jest to zasadniczo używane do sterowania przepływem. Nadawca jest odpowiedzialny za to, aby dane do wysłania zmieściły się w oknie anonsowania odbiorcy.

| **Pole nagłówka**          | **Cel** |
| ------------------------- | --- |
| **16-bitowa podsuma kontrolna TCP**   | To pole zawiera 16-bitową podsumę kontrolną dla pakietu, w tym nagłówek TCP, obszar danych pakietu i nagłówek pseudo-IP.                |
| **16-bitowy pilny wskaźnik** | To pole zawiera dodatnie przesunięcie ostatniego bajtu pilnych danych. To pole jest prawidłowe tylko wtedy, gdy bit kodu urlg jest ustawiony w nagłówku. |

> [!IMPORTANT]
> *Oczekuje się, że wszystkie nagłówki w implementacji TCP/IP będą w big endian formacie. W tym formacie najbardziej znaczący bajt wyrazu znajduje się w najniższym adresie bajtowym.*

### <a name="tcp-enable"></a>Włączanie protokołu TCP

Zanim będzie możliwe połączenie TCP i transmisje pakietów, aplikacja musi najpierw włączyć protokół TCP, wywołując nx_tcp_enable usługi. Po włączeniu tej opcji aplikacja będzie mieć bezpłatny dostęp do wszystkich usług TCP.

### <a name="tcp-socket-create"></a>Tworzenie gniazda TCP

Gniazda TCP są tworzone podczas inicjowania lub w czasie wykonywania przez wątki aplikacji. Początkowy typ usługi, czas na żywo i rozmiar okna są definiowane przez nx_tcp_socket_create ***usługi.*** Nie ma żadnych ograniczeń liczby gniazd TCP w aplikacji.

### <a name="tcp-checksum"></a>Sumy kontrolne TCP

Protokół TCP określa 16-bitową podsumę kontrolną dopełnianą przez jeden z nich, który obejmuje nagłówek pseudoadresu IP (składający się ze źródłowego adresu IP, docelowego adresu IP i słowa adresu IP protokołu/długości), nagłówka TCP i danych pakietów TCP.

Niektóre kontrolery sieci mogą wykonywać obliczenia i walidację sumy kontrolnej TCP na sprzęcie. W przypadku takich systemów aplikacje mogą chcieć jak najbardziej korzystać ze sprzętowej logiki sumy kontrolnej, aby zmniejszyć obciążenie środowiska uruchomieniowego. Aplikacje mogą całkowicie wyłączyć logikę obliczeń sumy kontrolnej TCP z biblioteki NetX w czasie kompilacji, definiując NX_DISABLE_TCP_TX_CHECKSUM **i** **NX_DISABLE_TCP_RX_CHECKSUM**. W ten sposób kod sumy kontrolnej TCP nie jest kompilowany.

### <a name="tcp-port"></a>Port TCP

Port TCP jest logicznym punktem połączenia w protokole TCP. Składnik TCP netx ma 65 535 prawidłowych portów, od 1 do 0xFFFF. W przeciwieństwie do protokołu UDP, w którym dane z jednego portu mogą być wysyłane do dowolnego innego portu docelowego, port TCP jest połączony z innym konkretnym portem TCP i tylko wtedy, gdy to połączenie zostanie nawiązane, może mieć miejsce dowolny transfer danych — i tylko między dwoma portami, które się na to połączenie.

> [!IMPORTANT]
> *Porty TCP są całkowicie oddzielone od portów UDP; Na przykład numer portu UDP 1 nie ma związku z portem TCP o numerze 1.*

## <a name="client-server-model"></a>Client-Server model

Aby używać protokołu TCP do transferu danych, należy najpierw nawiązyć połączenie między dwoma gniazdami TCP. Utworzenie połączenia odbywa się w sposób klient-serwer. Strona klienta połączenia to strona, która inicjuje połączenie, podczas gdy strona serwera po prostu czeka na żądania połączenia klienta przed rozpoczęciem jakiegokolwiek przetwarzania.

> [!IMPORTANT]
> *W przypadku urządzeń wieloadresowych NetX automatycznie określa adres źródłowy do użycia dla połączenia oraz adres następnego przeskoku na podstawie docelowego adresu IP połączenia.*

### <a name="tcp-socket-state-machine"></a>Komputer stanu gniazda TCP

Połączenie między dwoma gniazdami TCP (jednym klientem i jednym serwerem) jest złożone i jest zarządzane w sposób komputera stanu. Każde gniazdo TCP rozpoczyna się w stanie ZAMKNIĘTY. Za pośrednictwem zdarzeń połączenia maszyna stanu każdego gniazda jest migrowana do stanu ESTABLISHED, w którym odbywa się większość transferu danych w protokole TCP. Gdy jedna strona połączenia nie chce już wysyłać danych, rozłącza się. Po rozłączeniu się po drugiej stronie gniazdo TCP powróci do stanu CLOSED. Ten proces jest powtarzany za każdym razem, gdy klient i serwer TCP ustanawiają i zamykają połączenie. Rysunek 11 przedstawia różne stany maszyny stanu TCP.

![Stany komputera stanu TCP](./media/user-guide/states-tcp-state-machine.png)

### <a name="figure-11-states-of-the-tcp-state-machine"></a>RYSUNEK 11. Stany komputera stanu TCP

### <a name="tcp-client-connection"></a>Połączenie klienta TCP

Jak wspomniano wcześniej, strona klienta połączenia TCP inicjuje żądanie połączenia z serwerem TCP. Przed podjęciem żądania połączenia należy włączyć protokół TCP w wystąpieniu adresu IP klienta. Ponadto należy utworzyć gniazdo TCP klienta przy użyciu usługi ***nx_tcp_socket_create** _ i powiązane z portem za _*_pośrednictwem nx_tcp_client_socket_bind_*_ usługi. Po powiązaniu gniazda klienta usługa _ *_nx_tcp_client_socket_connect_** jest używana do nawiązywania połączenia z serwerem TCP. Należy pamiętać, że gniazdo musi być w stanie CLOSED, aby zainicjować próbę połączenia. Nawiązywanie połączenia rozpoczyna się od wystawienia przez netx pakietu SYN, a następnie oczekiwania na pakiet SYN ACK z powrotem z serwera, co oznacza akceptację żądania połączenia. Po otrzymaniu ACK SYN, NetX odpowiada za pomocą pakietu ACK i podniesie gniazda klienta do stanu ESTABLISHED.

### <a name="tcp-client-disconnection"></a>Rozłączanie klienta TCP

Zamknięcie połączenia jest realizowane przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie określono żadnego zawieszenia, gniazdo klienta wysyła pakiet RST do gniazda serwera i umieszcza gniazdo w stanie CLOSED. W przeciwnym razie, jeśli zostanie zażądane zawieszenie, zostanie wykonany pełny protokół rozłączania TCP w następujący sposób:

- Jeśli serwer wcześniej zainicjował żądanie rozłączenia (gniazdo klienta otrzymało już pakiet FIN, odpowiedział przy użyciu ACK i jest w stanie CLOSE WAIT), NetX podniesie stan gniazda TCP klienta do stanu OSTATNIEGO ACK i wysyła pakiet FIN. Następnie czeka na ACK z serwera przed ukończeniem rozłączenia i wprowadzeniem stanu CLOSED.

- Jeśli z drugiej strony klient jest pierwszym, który zainicjował żądanie rozłączenia (serwer nie został odłączony, a gniazdo jest nadal w stanie ESTABLISHED), netX wysyła pakiet FIN w celu zainicjowania rozłączenia i czeka na otrzymanie fina i ACK z serwera przed zakończeniem rozłączenia i umieszczeniem gniazda w stanie ZAMKNIĘTY.

Jeśli w kolejce przesyłania gniazda nadal znajdują się pakiety, program NetX zawiesza się na określony limit czasu, aby umożliwić potwierdzenie pakietów. Jeśli limit czasu wygaśnie, netx opróżnia kolejkę przesyłania gniazda klienta.

Aby odimówić port od gniazda klienta, aplikacja ***wywołuje nx_tcp_client_socket_unbind***. Gniazdo musi być w stanie CLOSED lub w procesie rozłączania (tj. stanu OCZEKIWANIA z czasem) przed zwolnieniu portu; w przeciwnym razie zwracany jest błąd.

Na koniec, jeśli aplikacja nie potrzebuje już gniazda klienta, ***wywołuje*** nx_tcp_socket_delete, aby usunąć gniazdo.

### <a name="tcp-server-connection"></a>Połączenie z serwerem TCP

Strona serwera połączenia TCP jest pasywna; tj. serwer czeka, aż klient zainicjuje żądanie połączenia. Aby zaakceptować połączenie klienta, należy najpierw włączyć protokół TCP w wystąpieniu adresu IP, wywołując usługę ***nx_tcp_enable** _. Następnie aplikacja musi utworzyć gniazdo TCP przy użyciu usługi _ *_nx_tcp_socket_create_**.

Należy również skonfigurować gniazdo serwera do nasłuchiwania żądań połączenia. Jest to osiągane przy użyciu ***nx_tcp_server_socket_listen*** usługi. Ta usługa umieszcza gniazdo serwera w stanie LISTEN i wiąże określony port serwera z gniazdem.

> [!IMPORTANT]
> *Aby ustawić procedurę wywołania zwrotnego nasłuchiwu gniazda, aplikacja określa odpowiednią funkcję wywołania zwrotnego dla tcp_listen_callback argumentu **nx_tcp_server_socket_listen** usługi. Ta funkcja wywołania zwrotnego aplikacji jest następnie wykonywana przez platformę NetX za każdym razem, gdy na tym porcie serwera jest wymagane nowe połączenie. Przetwarzanie w wywołaniu zwrotym jest pod kontrolą aplikacji.*

Aby akceptować żądania połączenia klienta, aplikacja wywołuje usługę ***nx_tcp_server_socket_accept** _. Gniazdo serwera musi być w stanie LISTEN lub SYN RECEIVED (tj. serwer jest w stanie NASŁUCHIWAĆ i otrzymał pakiet SYN od klienta żądający połączenia), aby wywołać usługę akceptowania. Stan pomyślnego zwrócenia z _ *_nx_tcp_server_socket_accept_** wskazuje, że połączenie zostało ustawione, a gniazdo serwera jest w stanie ESTABLISHED.

Gdy gniazdo serwera ma prawidłowe połączenie, dodatkowe żądania połączenia klienta są kolejkowane do głębokości określonej przez listen_queue_size *,* przekazywane do ***nx_tcp_server_socket_listen** _service. Aby przetwarzać kolejne połączenia na porcie serwera, aplikacja musi wywołać element _ *_nx_tcp_server_socket_relisten_** z dostępnym gniazdem (tj. gniazdem w stanie CLOSED). Należy pamiętać, że to samo gniazdo serwera może być używane, jeśli poprzednie połączenie skojarzone z tym gniazdem zostało zakończone, a gniazdo jest w stanie CLOSED.

### <a name="tcp-server-disconnection"></a>Rozłączanie serwera TCP

Zamknięcie połączenia jest realizowane przez wywołanie ***nx_tcp_socket_disconnect***. Jeśli nie określono żadnego zawieszenia, gniazdo serwera wysyła pakiet RST do gniazda klienta i umieszcza gniazdo w stanie CLOSED. W przeciwnym razie, jeśli zostanie zażądane zawieszenie, zostanie wykonany pełny protokół rozłączania TCP w następujący | sposób:

- Jeśli klient wcześniej zainicjował żądanie rozłączenia (gniazdo serwera otrzymało już pakiet FIN, odpowiedział przy użyciu ACK i jest w stanie CLOSE WAIT), NetX podniesie stan gniazda TCP do stanu LAST ACK i wyśle pakiet FIN. Następnie czeka na ACK od klienta przed ukończeniem rozłączania i wprowadzeniem stanu CLOSED.

- Jeśli z drugiej strony serwer jest pierwszym, który zainicjował żądanie rozłączenia (klient nie został odłączony, a gniazdo jest nadal w stanie ESTABLISHED), netX wysyła pakiet FIN w celu zainicjowania rozłączenia i czeka na otrzymanie od klienta fina i ACK przed zakończeniem rozłączenia i umieszczeniem gniazda w stanie ZAMKNIĘTYm.

Jeśli w kolejce przesyłania gniazda nadal znajdują się pakiety, netx zawiesza się na określony limit czasu, aby umożliwić potwierdzenie tych pakietów. Jeśli limit czasu wygaśnie, netx opróżnia kolejkę przesyłania gniazda serwera.

Po zakończeniu przetwarzania rozłączania, gdy gniazdo serwera jest w stanie CLOSED, aplikacja musi wywołać usługę ***nx_tcp_server_socket_unaccept,*** aby zakończyć skojarzenie tego gniazda z portem serwera. Należy pamiętać, że ta usługa musi być wywoływana przez aplikację, nawet ***jeśli nx_tcp_socket_disconnect*** lub ***nx_tcp_server_socket_accept** _ zwraca stan błędu. Po *_zwracaniu nx_tcp_server_socket_unaccept_** gniazdo może być używane jako gniazdo klienta lub serwera, a nawet usunięte, jeśli nie jest już potrzebne. Jeśli pożądane jest zaakceptowanie innego połączenia klienta na tym samym porcie serwera, ***usługa nx_tcp_server_socket_relisten*** powinna zostać wywołana na tym gnieździe.

Następujący segment kodu ilustruje sekwencję wywołań, których używa typowy serwer TCP:

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

### <a name="mss-validation"></a>Walidacja usługi MSS

Maksymalny rozmiar segmentu (MSS) to maksymalna liczba bajtów, które host TCP może odbierać bez fragmentacji przez podstawową warstwę adresów IP. W fazie ustanawiania połączenia TCP oba kończy wymianę własnej wartości PROTOKOŁU TCP MSS, dzięki czemu nadawca nie wysyła segmentu danych TCP, który jest większy niż mss odbiorcy. Moduł TCP NetX opcjonalnie zweryfikuje anonsowane wartości MSS elementu równorzędnego przed nawiązaniem połączenia. Domyślnie netx nie włącza takiego sprawdzenia. Aplikacje, które chcą przeprowadzić walidację mss, muszą definiować ***NX_ENABLE_TCP_MSS_CHECKING** _ podczas tworzenia biblioteki NetX, a minimalna wartość musi być zdefiniowana w NX_TCP_MSS_MINIMUM _*_._*_ Przychodzące połączenia TCP z wartościami MSS poniżej _ *_NX_TCP_MSS_MINIMUM_** są porzucane.

### <a name="stop-listening-on-a-server-port"></a>Zatrzymywanie nasłuchiwania na porcie serwera

Jeśli aplikacja nie chce już nasłuchiwać żądań połączenia klienta na porcie serwera, który został wcześniej określony przez wywołanie usługi ***nx_tcp_server_socket_listen** _, aplikacja po prostu wywołuje usługę _ *_nx_tcp_server_socket_unlisten_**. Ta usługa umieszcza każde gniazdo oczekujące na połączenie z powrotem w stanie CLOSED i zwalnia wszystkie pakiety żądań połączenia klienta w kolejce.

### <a name="tcp-window-size"></a>Rozmiar okna TCP

Zarówno w fazie instalacji, jak i transferu danych połączenia każdy port zgłasza ilość danych, które może obsłużyć, co jest nazywane rozmiarem okna. W przypadku odbierania i przetwarzania danych ten rozmiar okna jest dostosowywany dynamicznie. W przypadku protokołu TCP nadawca może wysyłać tylko dane, które pasują do okna odbiorcy. W zasadzie rozmiar okna zapewnia sterowanie przepływem transferu danych w każdym kierunku połączenia.

### <a name="tcp-packet-send"></a>Wysyłanie pakietów TCP

Wysyłanie danych TCP można łatwo wykonać, wywołując ***funkcję nx_tcp_socket_send*** tcp. Jeśli rozmiar przesyłanych danych jest większy niż wartość MSS gniazda lub bieżącego okna odbierania elementów równorzędnych, w zależności od tego, który z nich jest mniejszy, wewnętrzna logika TCP odbierze dane, które pasują do minimalnej wartości (MSS, okno odbierania elementów równorzędnych) do transmisji. Następnie ta usługa tworzy nagłówek TCP przed pakietem (w tym obliczenie sumy kontrolnej). Jeśli rozmiar okna odbiornika nie wynosi zero, wywołujący wyśle jak najwięcej danych, aby wypełnić rozmiar okna odbiornika. Jeśli okno odbierania będzie mieć wartość zero, wywołujący może wstrzymać i poczekać, aż rozmiar okna odbiornika zwiększy się wystarczająco, aby ten pakiet został wysłany. W dowolnym momencie wiele wątków może zostać wstrzymanych podczas próby wysłania danych za pośrednictwem tego samego gniazda.

> [!IMPORTANT]
> *Dane TCP przechowywane w NX_PACKET powinny znajdować się na granicy długich słów. Ponadto musi być wystarczająca ilość miejsca między dołączany wskaźnik i wskaźnik uruchamiania danych, aby umieścić nagłówki TCP, IP i nośnika fizycznego.*

### <a name="tcp-packet-retransmit"></a>Retransmisja pakietów TCP

Wcześniej przesyłane pakiety TCP rzeczywiście były przechowywane wewnętrznie do momentu zwrócenia ACK z drugiej strony połączenia. Jeśli przesłane dane nie zostaną potwierdzone w ramach limitu czasu, przechowywany pakiet zostanie ponownie wysłany i zostanie ustawiony następny limit czasu. Po otrzymaniu ACK wszystkie pakiety objęte numerem potwierdzenia w wewnętrznej kolejce przesyłania są zwalniane.

> [!IMPORTANT]
> *Aplikacja nie może ponownie używać pakietu ani zmieniać jego zawartości po zwracaniu przez funkcję ***nx_tcp_socket_send** _ NX_SUCCESS. Przesłany pakiet jest ostatecznie zwalniany przez wewnętrzne przetwarzanie NetX po otrzymaniu potwierdzenia danych przez drugą end._

### <a name="tcp-keepalive"></a>Utrzymanie aktywności protokołu TCP

Funkcja utrzymania aktywności protokołu TCP umożliwia gniazdu wykrywanie, czy jego element równorzędny rozłącza się bez odpowiedniego zakończenia (na przykład awaria elementu równorzędnego) lub uniemożliwia niektórym obiektom monitorowania sieci przerwanie połączenia na długi czas bezczynności. Utrzymanie aktywności tcp działa przez okresowe wysyłanie ramki TCP bez danych, a numer sekwencji ustawiony na o jeden mniej niż bieżący numer sekwencji. Po otrzymaniu takiej ramki utrzymania aktywności TCP odbiorca, jeśli nadal jest aktywne, otrzymuje odpowiedź z ACK dla bieżącego numeru sekwencji. To kończy transakcję utrzymania aktywności.

Domyślnie funkcja utrzymania aktywności nie jest włączona. Aby można było korzystać z tej funkcji, biblioteka NetX musi być budowaną przy **użyciu** NX_ENABLE_TCP_KEEPALIVE _ zdefiniowanej. Symbol _ *_NX_TCP_KEEPALIVE_INITIAL_** określa liczbę sekund braku aktywności przed zainicjowaniem ramki utrzymania aktywności.

### <a name="tcp-packet-receive"></a>Odbieranie pakietów TCP

Przetwarzanie pakietów odbioru TCP (wywoływane z wątku pomocnika IP) jest odpowiedzialne za obsługę różnych akcji połączenia i rozłączania, a także przesyłanie przetwarzania potwierdzenia. Ponadto przetwarzanie pakietów odbierających TCP jest odpowiedzialne za umieszczanie pakietów z danymi odbierania w kolejce odbierania odpowiedniego gniazda TCP lub dostarczanie pakietu do pierwszego wstrzymanego wątku czekającego na pakiet.

### <a name="tcp-receive-notify"></a>Powiadomienie o odbierania tcp

Jeśli wątek aplikacji musi przetwarzać odebrane dane z więcej niż jednego gniazda, ***należy nx_tcp_socket_receive_notify*** funkcji. Ta funkcja rejestruje funkcję wywołania zwrotnego pakietów odbioru dla gniazda. Za każdym razem, gdy pakiet jest odbierany w gnieździe, wykonywana jest funkcja wywołania zwrotnego.

Zawartość funkcji wywołania zwrotnego jest specyficzna dla aplikacji. Jednak funkcja najprawdopodobniej zawierałaby logikę, która informuje wątek przetwarzania, że pakiet jest dostępny na odpowiednim gnieździe.

### <a name="thread-suspension"></a>Zawieszenie wątku

Jak wspomniano wcześniej, wątki aplikacji mogą zostać wstrzymane podczas próby odbierania danych z określonego portu TCP. Po otrzymaniu pakietu na tym porcie zostaje on nadany do pierwszego wstrzymanego wątku, a następnie wznawiany. Opcjonalny limit czasu jest dostępny w przypadku wstrzymania pakietu odbierania TCP, funkcji dostępnej dla większości usług NetX.

Zawieszenie wątku jest również dostępne dla połączeń (klienta i serwera), powiązań klienta i usług rozłączania.

### <a name="tcp-socket-statistics-and-errors"></a>Statystyki i błędy gniazd TCP

Jeśli ta opcja jest włączona, oprogramowanie netx gniazda TCP śledzi kilka statystyk i błędów, które mogą być przydatne dla aplikacji. Dla każdego wystąpienia protokołu IP/TCP są utrzymywane następujące statystyki i raporty o błędach:

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

## <a name="tcp-socket-control-block-nx_tcp_socket"></a>TCP Socket Control Block NX_TCP_SOCKET

Cechy poszczególnych gniazd TCP znajdują się w skojarzonym bloku sterowania usługi *NX_TCP_SOCKET,* który zawiera przydatne informacje, takie jak link do struktury danych IP, interfejs połączenia sieciowego, powiązany port i kolejka pakietów odbioru. Ta struktura jest zdefiniowana ***w nx_api.h.***
