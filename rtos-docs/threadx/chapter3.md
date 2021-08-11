---
title: Rozdział 3 — Składniki funkcjonalne Azure RTOS ThreadX
description: Ten rozdział zawiera opis jądra ThreadX o wysokiej Azure RTOS wydajności z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 906ccb4fb69925f5244192f06521bf508bd15ced2076fb03031649fea638171c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789982"
---
# <a name="chapter-3---functional-components-of-azure-rtos-threadx"></a>Rozdział 3 — Składniki funkcjonalne Azure RTOS ThreadX

Ten rozdział zawiera opis jądra ThreadX o wysokiej Azure RTOS wydajności z perspektywy funkcjonalnej. Każdy składnik funkcjonalny jest przedstawiony w łatwy do zrozumienia sposób.

## <a name="execution-overview"></a>Omówienie wykonywania

Istnieją cztery typy wykonywania programu w aplikacji ThreadX: inicjowanie, wykonywanie wątku, procedury usługi przerwań (ISR) i czasomierze aplikacji.

Rysunek 2 przedstawia każdy inny typ wykonywania programu. Bardziej szczegółowe informacje o każdym z tych typów znajdują się w kolejnych sekcjach tego rozdziału.

### <a name="initialization"></a>Inicjalizacja

Jak sama nazwa wskazuje, jest to pierwszy typ wykonywania programu w aplikacji ThreadX. Inicjowanie obejmuje całe wykonywanie programu między resetowaniem procesora a punktem wejścia pętli *planowania wątków.*

### <a name="thread-execution"></a>Wykonywanie wątku

Po zakończeniu inicjowania threadX wchodzi w pętlę planowania wątków. Pętla planowania szuka wątku aplikacji gotowego do wykonania. Po znalezioniu gotowego wątku threadX przekazuje do niego kontrolkę. Po zakończeniu wątku (lub przygotowaniu innego wątku o wyższym priorytecie) wykonanie jest transferowane z powrotem do pętli planowania wątku, aby znaleźć następny wątek o najwyższym priorytecie.

Ten proces ciągłego wykonywania i planowania wątków jest najbardziej powszechnym typem wykonywania programów w aplikacjach ThreadX.

### <a name="interrupt-service-routines-isr"></a>Procedury przerywania usługi (ISR)

Przerwania są podstawą systemów czasu rzeczywistego. Bez przerwań reagowanie na zmiany w świecie zewnętrznym w terminowy sposób byłoby niezwykle trudne. Po wykryciu przerwania procesor zapisuje kluczowe informacje o bieżącym wykonaniu programu (zazwyczaj na stosie), a następnie przekazuje kontrolę do wstępnie zdefiniowanego obszaru programu. Ten wstępnie zdefiniowany obszar programu jest często nazywany rutyną usługi przerywania. W większości przypadków przerwania występują podczas wykonywania wątku (lub w pętli planowania wątków). Jednak przerwania mogą również wystąpić wewnątrz wykonującego isr lub czasomierza aplikacji.

![Typy wykonywania programu](./media/user-guide/types-program-execution.png)

**RYSUNEK 2. Typy wykonywania programu**

### <a name="application-timers"></a>Czasomierze aplikacji

Czasomierze aplikacji są podobne do isR, z tą różnicą, że implementacja sprzętu (zwykle używane jest jedno okresowe przerwań sprzętowych) jest ukryta przed aplikacją. Takie czasomierze są używane przez aplikacje do wykonywania przekłamań czasu, okresowych i/lub usług watchdog. Podobnie jak w przypadku isrów, czasomierze aplikacji najczęściej przerywają wykonywanie wątku. Jednak w przeciwieństwie do isR czasomierze aplikacji nie mogą wzajemnie przerywać działania.

## <a name="memory-usage"></a>Użycie pamięci

ThreadX znajduje się wraz z programem aplikacji. W związku z tym użycie pamięci statycznej (lub pamięci stałej) threadX jest określane przez narzędzia programowe; na przykład kompilator, linker i lokalizator. Użycie pamięci dynamicznej (lub pamięci w czasie uruchamiania) podlega bezpośredniej kontroli nad aplikacją.

### <a name="static-memory-usage"></a>Użycie pamięci statycznej

Większość narzędzi deweloperskimi dzieli obraz programu aplikacji na pięć podstawowych obszarów: *instrukcji* *,* stałej, danych zainicjowanych, *niezainicjowanych* danych i stosu *systemu*. Rysunek 3 przedstawia przykład tych obszarów pamięci.

Ważne jest, aby zrozumieć, że jest to tylko przykład. Rzeczywisty układ pamięci statycznej jest specyficzny dla procesora, narzędzi programisttycznych i bazowego sprzętu.

Obszar instrukcji zawiera wszystkie instrukcje procesora programu. Ten obszar jest zwykle największy i często znajduje się w pamięci ROM.

Stały obszar zawiera różne skompilowane stałe, w tym ciągi zdefiniowane lub przywołyne w programie. Ponadto ten obszar zawiera "początkową kopię" zainicjowanych obszarów danych. Podczas procesu *inicjowania* kompilatora użycie pamięci ta część stałego obszaru jest używana do skonfigurowania zainicjowanych obszarów danych w pamięci RAM. Stały obszar zwykle następuje po obszarze instrukcji i często znajduje się w pamięci ROM.

Zainicjowane dane i niezainicjowane obszary danych zawierają wszystkie zmienne globalne i statyczne. Te obszary zawsze znajdują się w pamięci RAM.

Stos systemowy jest zwykle ustawiany bezpośrednio po zainicjowanych i niezainicjowanych obszarach danych.

Stos systemowy jest używany przez kompilator podczas inicjowania, następnie przez ThreadX podczas inicjowania, a następnie w przetwarzaniu ISR.

![Przykład obszaru pamięci](./media/user-guide/memory-area-example.png)

**RYSUNEK 3. Przykład obszaru pamięci**

### <a name="dynamic-memory-usage"></a>pamięć dynamiczna użycia

Jak wspomniano wcześniej, dynamiczne użycie pamięci jest pod bezpośrednią kontrolą aplikacji. Bloki sterujące i obszary pamięci skojarzone ze stosami, kolejkami i pulami pamięci można umieścić w dowolnym miejscu w przestrzeni pamięci obiektu docelowego. Jest to ważna funkcja, ponieważ ułatwia wykorzystanie różnych typów pamięci fizycznej.

Załóżmy na przykład, że docelowe środowisko sprzętowe ma zarówno szybką, jak i powolną pamięć. Jeśli aplikacja wymaga dodatkowej wydajności dla wątku o wysokim priorytecie, jej blok sterowania (TX_THREAD) i stos można umieścić w szybkim obszarze pamięci, co może znacznie zwiększyć jej wydajność.

## <a name="initialization"></a>Inicjalizacja

Zrozumienie procesu inicjowania jest ważne. W tym miejscu jest ustawione początkowe środowisko sprzętowe. Ponadto jest to miejsce, w którym aplikacja ma nadaną początkową osobowość.

> [!NOTE]
> *ThreadX próbuje użyć (jeśli to możliwe) pełnego procesu inicjowania narzędzia deweloperacyjnego. Ułatwi to uaktualnienie do nowych wersji narzędzi programistyki w przyszłości.*

### <a name="system-reset-vector"></a>Wektor resetowania systemu

Wszystkie mikroprocesory mają logikę resetowania. W przypadku zresetowania (sprzętu lub oprogramowania) adres punktu wejścia aplikacji jest pobierany z określonej lokalizacji pamięci. Po pobraniu punktu wejścia procesor przekazuje kontrolę do tej lokalizacji. Punkt wejścia aplikacji jest dość często pisany w natywnym języku zestawu i jest zazwyczaj dostarczany przez narzędzia programowe (przynajmniej w postaci szablonu). W niektórych przypadkach specjalna wersja programu wprowadzania jest dostarczana z ThreadX.

### <a name="development-tool-initialization"></a>Inicjalizacja narzędzia programizacyjnego

Po zakończeniu inicjowania niskiego poziomu kontroluj przenoszenie do inicjowania wysokiego poziomu narzędzia dewelopera. Zazwyczaj jest to miejsce, w którym są ustawiane zainicjowane zmienne globalne i statyczne języka C. Pamiętaj, że ich początkowe wartości są pobierane z obszaru stałego. Dokładne przetwarzanie inicjalizacji jest specyficzne dla narzędzia deweloperacyjnego.

### <a name="main-function"></a>main, funkcja

Po zakończeniu inicjowania narzędzia deweloperacyjnego sterowanie jest transferem do funkcji *main dostarczonej przez* użytkownika. W tym momencie aplikacja kontroluje, co się dzieje dalej. W przypadku większości aplikacji funkcja główna po prostu wywołuje *tx_kernel_enter*, która jest wpisem w ThreadX. Jednak aplikacje mogą wykonywać wstępne przetwarzanie (zazwyczaj w przypadku inicjowania sprzętu) przed wprowadzeniem threadX.

> [!IMPORTANT]
> *Wywołanie do tx_kernel_enter nie zwraca, więc nie umieszczaj żadnego przetwarzania po nim.*

### <a name="tx_kernel_enter"></a>tx_kernel_enter

Funkcja entry koordynuje inicjowanie różnych wewnętrznych struktur danych ThreadX, a następnie wywołuje funkcję definicji aplikacji ***tx_application_define***.

Gdy ***tx_application_define*** zwraca, sterowanie jest przenoszone do pętli planowania wątków. Oznacza to koniec inicjowania.

### <a name="application-definition-function"></a>Application Definition, funkcja

Funkcja ***tx_application_define*** definiuje wszystkie początkowe wątki aplikacji, kolejki, semafory, mutexy, flagi zdarzeń, pule pamięci i czasomierze. Istnieje również możliwość tworzenia i usuwania zasobów systemowych z wątków podczas normalnego działania aplikacji. Jednak wszystkie początkowe zasoby aplikacji są zdefiniowane w tym miejscu.

Funkcja ***tx_application_define** _ ma jeden parametr wejściowy i na pewno warto o nim wspomnieć. Adres _first* pamięci RAM jest jedynym parametrem wejściowym dla tej funkcji. Jest ona zwykle używana jako punkt wyjścia dla początkowych alokacji pamięci w czasie rzeczywistym stosów wątków, kolejek i pul pamięci.

> [!NOTE]
> *Po zakończeniu inicjowania tylko wykonujący wątek może tworzyć i usuwać zasoby systemowe, w tym inne wątki. W związku z tym podczas inicjowania należy utworzyć co najmniej jeden wątek.*

### <a name="interrupts"></a>Przerwania

Przerwania są pozostawiane wyłączone podczas całego procesu inicjowania. Jeśli aplikacja w jakiś sposób włącza przerwania, może wystąpić nieprzewidywalne zachowanie. Rysunek 4 przedstawia cały proces inicjowania , od resetowania systemu przez inicjowanie specyficzne dla aplikacji.

## <a name="thread-execution"></a>Wykonywanie wątku

Planowanie i wykonywanie wątków aplikacji jest najważniejszym działaniem threadX. Wątek jest zwykle definiowany jako częściowo niezależny segment programu przeznaczony do celów dedykowanych. Połączone przetwarzanie wszystkich wątków sprawia, że aplikacja.

Wątki są tworzone dynamicznie przez wywołanie ***tx_thread_create** _ podczas inicjowania lub podczas wykonywania wątku. Wątki są tworzone w stanie _ready*  lub wstrzymania.

![Proces inicjowania](./media/user-guide/initialization-process.png)

**RYSUNEK 4. Proces inicjowania**

### <a name="thread-execution-states"></a>Stany wykonywania wątku

Zrozumienie różnych stanów przetwarzania wątków jest kluczowym składnikiem do zrozumienia całego środowiska wielowątkowego. W threadX istnieje pięć odrębnych stanów wątków: *ready*, *suspended*, *executing*, *terminated* i *completed*. Rysunek 5 przedstawia diagram przejścia stanu wątku dla ThreadX.

![Przejście stanu wątku](./media/user-guide/thread-state-transition.png)

**RYSUNEK 5. Przejście stanu wątku**

Wątek jest w stanie *gotowości,* gdy jest gotowy do wykonania. Wątek gotowy nie jest wykonywany, dopóki wątek o najwyższym priorytecie nie jest w stanie gotowości. W takim przypadku ThreadX wykonuje wątek, co następnie zmienia jego stan na *wykonywanie*.

Jeśli wątek o wyższym priorytecie stanie się gotowy, wątek wykonujący powraca do stanu *gotowości.* Nowo gotowy wątek o wysokim priorytecie jest następnie wykonywany, co zmienia jego stan logiczny na *wykonywanie*. To przejście między *stanami gotowości* *i wykonywania* odbywa się za każdym razem, gdy wystąpi wywłaszanie wątku.

W danym momencie tylko jeden wątek jest w *stanie wykonywania.* Wynika to z tego, że wątek w *stanie wykonywania* ma kontrolę nad bazowym procesorem.

Wątki w stanie *zawieszonym* nie kwalifikują się do wykonania. Przyczyny wstrzymania obejmują *wstrzymanie* czasu, komunikaty w kolejce, semafory, elementy mutex, flagi zdarzeń, pamięć i podstawowe zawieszenie wątku. Po usunięciu przyczyny zawieszenia wątek jest z powrotem umieszczany w *stanie* gotowości.

Wątek w stanie *ukończenia* jest wątkiem, który zakończył przetwarzanie i zwrócił z funkcji wpisu. Funkcja entry jest określana podczas tworzenia wątku. Wątek w stanie *ukończenia nie* może zostać ponownie wykonany.

Wątek jest w stanie *zakończenia,* ponieważ inny wątek lub sam wątek jest nazywany tx_thread_terminate *service.* Wątek w stanie *zakończenia nie* może zostać wykonany ponownie.

> [!IMPORTANT]
> *Jeśli wymagane jest ponowne uruchomienie ukończonego lub zakończonego wątku, aplikacja musi najpierw usunąć wątek. Następnie można je ponownie utworzyć i ponownie rozpocząć.*

### <a name="thread-entryexit-notification"></a>Powiadomienie o wejściu/wyjściu wątku

W przypadku niektórych aplikacji korzystne może być powiadomienie, gdy określony wątek zostanie wprowadzony po raz pierwszy, po jego zakończeniu lub jego zakończeniu. ThreadX zapewnia tę możliwość za ***pośrednictwem tx_thread_entry_exit_notify*** usługi. Ta usługa rejestruje funkcję powiadomień aplikacji dla określonego wątku, który jest wywoływany przez ThreadX za każdym razem, gdy wątek zaczyna działać, kończy działanie lub zostaje zakończony. Po wywołaniu funkcja powiadamiania aplikacji może wykonać przetwarzanie specyficzne dla aplikacji. Zwykle obejmuje to informowanie innego wątku aplikacji o zdarzeniu za pośrednictwem prymitywu synchronizacji ThreadX.

### <a name="thread-priorities"></a>Priorytety wątku

Jak wspomniano wcześniej, wątek jest częściowo niezależnym segmentem programów przeznaczonym do dedykowanych celów. Jednak wszystkie wątki nie są tworzone tak samo! Dedykowany cel niektórych wątków jest znacznie ważniejszy niż inne. Ten heterogeniczny typ ważności wątku jest cechą charakterystyczną osadzonych aplikacji w czasie rzeczywistym.

ThreadX określa ważność wątku, gdy wątek jest tworzony przez przypisanie wartości liczbowej reprezentującej jej *priorytet*. Maksymalną liczbę priorytetów ThreadX można skonfigurować z 32 do 1024 w przyrostach 32. Rzeczywista maksymalna liczba priorytetów jest określana przez **TX_MAX_PRIORITIES** podczas kompilacji biblioteki ThreadX. Większa liczba priorytetów nie zwiększa znacząco obciążenia związanego z przetwarzaniem. Jednak w przypadku każdej grupy o 32 poziomach priorytetu do zarządzania nimi jest wymagane dodatkowe 128 bajtów pamięci RAM. Na przykład 32 poziomy priorytetu wymagają 128 bajtów pamięci RAM, 64 poziomy priorytetu wymagają 256 bajtów pamięci RAM, a 96 poziomów priorytetu wymaga 384 bajtów pamięci RAM.

Domyślnie ThreadX ma 32 poziomy priorytetu, od priorytetu 0 do priorytetu 31. Wartości mniejsze numerycznie oznaczają wyższy priorytet. W związku z tym priorytet 0 reprezentuje najwyższy priorytet, a priorytet **(TX_MAX_PRIORITIES**-1) oznacza najniższy priorytet.

Wiele wątków może mieć taki sam priorytet, w zależności od planowania kooperatywnych lub dzielania czasu. Ponadto priorytety wątków można zmieniać w czasie działania.

### <a name="thread-scheduling"></a>Planowanie wątków

ThreadX planuje wątki na podstawie ich priorytetu. Gotowy wątek o najwyższym priorytecie jest wykonywany jako pierwszy. Jeśli wiele wątków o tym samym priorytecie jest gotowych, są one wykonywane w trybie fifo *(first-in-first-out).*

### <a name="round-robin-scheduling"></a>Planowanie okrężne

ThreadX obsługuje *planowanie działania okrężnego* wielu wątków o tym samym priorytecie. Jest to realizowane za pośrednictwem wspólnych połączeń do ***tx_thread_relinquish** _. Ta usługa daje wszystkim innym gotowym wątkom o tym samym priorytecie możliwość *_wykonania_* przed wykonaniem ponownie tx_thread_relinquish _ tx_thread_relinquish *.

### <a name="time-slicing"></a>Time-Slicing

*Tworzenie nacięć czasu* jest kolejną formą planowania z zastosowaniem okrężnego. Wycinek czasu określa maksymalną liczbę takt czasomierzy (przerwań czasomierza), które wątek może wykonać bez rezygnacji z procesora. W threadX, czas- slicowanie jest dostępne dla każdego wątku. Wycinek czasu wątku jest przypisywany podczas tworzenia i może być modyfikowany w czasie uruchamiania. Gdy wycinek czasu wygaśnie, wszystkie inne gotowe wątki na tym samym poziomie priorytetu będą mieć możliwość wykonania przed wykonaniem ponownie wątku z fragmentami czasu.

Wycinek czasu nowego wątku jest nadany do wątku po jego wstrzymaniu, wywłaszczeniu, wywołaniu usługi ThreadX, które powoduje wywłaszczenie lub samo wywłaszczeniu czasu.

Gdy wątek z wycinkiem czasu zostanie wywłaszowany, zostanie wznowiony przed innymi gotowymi wątkami o równym priorytecie dla pozostałej części tego wycinka czasu.

> [!NOTE]
> *Zastosowanie licowania w czasie powoduje niewielkie obciążenie systemu. Ponieważ fragmentowanie w czasie jest przydatne tylko w przypadkach, w których wiele wątków ma ten sam priorytet, wątków o unikatowym priorytecie nie należy przypisywać wycinka czasu.*

### <a name="preemption"></a>Wywłaszczanie

Wywłaszczenie to proces tymczasowego przerywania wykonywania wątku na rzecz wątku o wyższym priorytecie. Ten proces jest niewidoczny dla wątku wykonującego. Po zakończeniu wątku o wyższym priorytecie kontrola jest przenosona z powrotem do miejsca, w którym miało miejsce wywłaszcze. Jest to bardzo ważna funkcja w systemach czasu rzeczywistego, ponieważ ułatwia szybkie reagowanie na ważne zdarzenia aplikacji. Chociaż jest to bardzo ważna funkcja, wywłaszczenie może być również źródłem różnych problemów, takich jak zator, nadmierne obciążenie i odwrócenie priorytetu.

### <a name="preemption-thresholdtrade"></a>Próg wywłaszczenia&trade;

Aby ułatwić niektóre z właściwych problemów wywłaszczenia, ThreadX udostępnia unikatową i zaawansowaną funkcję o nazwie *próg wywłaszczenia*.

Próg wywłaszczenia umożliwia wątkowi określenie limitu *priorytetu* wyłączania wywłaszczenia. Wątki o wyższych priorytetach niż limit nadal mogą wywłaszczeć, podczas gdy te mniejsze niż limit nie mogą wywłaszczeć.

Załóżmy na przykład, że wątek o priorytecie 20 współdziała tylko z grupą wątków o priorytetach od 15 do 20. W sekcjach krytycznych wątek o priorytecie 20 może ustawić próg wywłaszczenia na 15, zapobiegając wywłaszczeniu ze wszystkich wątków, z których wchodzi w interakcję. Dzięki temu naprawdę ważne wątki (o priorytetach od 0 do 14) mogą wywłaszczyć ten wątek podczas jego krytycznego przetwarzania sekcji, co skutkuje znacznie bardziej dynamicznym przetwarzaniem.

Oczywiście nadal jest możliwe, aby wątek wyłączył wszystkie wywłaszczenia, ustawiając jego próg wywłaszczenia na 0. Ponadto próg wywłaszczenia można zmienić w czasie uruchamiania.

> [!NOTE]
> *Przy użyciu próg wywłaszczenia wyłącza cięcie czasu dla określonego wątku.*

### <a name="priority-inheritance"></a>Dziedziczenie priorytetów

ThreadX obsługuje również opcjonalne dziedziczenie priorytetów w ramach usług mutex opisanych w dalszej części tego rozdziału. Dziedziczenie priorytetów umożliwia wątku o niższym priorytecie tymczasowo przyjąć priorytet wątku o wysokim priorytecie, który oczekuje na mutex należące do wątku o niższym priorytecie. Ta funkcja pomaga aplikacji uniknąć niedeterministycznego odwrócenia priorytetu przez wyeliminowanie wywłaszczenia priorytetów wątku pośredniego. Oczywiście do *osiągnięcia podobnego* wyniku można użyć progu wywłaszczenia.

### <a name="thread-creation"></a>Tworzenie wątku

Wątki aplikacji są tworzone podczas inicjowania lub wykonywania innych wątków aplikacji. Nie ma żadnego limitu liczby wątków, które mogą zostać utworzone przez aplikację.

### <a name="thread-control-block-tx_thread"></a>Blok sterowania wątkami TX_THREAD

Cechy poszczególnych wątków znajdują się w bloku sterującym. Ta struktura jest zdefiniowana ***w tx_api.h.***

Blok sterowania wątku może być umieszczony w dowolnym miejscu w pamięci, ale najczęściej formant blokuje globalną strukturę przez zdefiniowanie jej poza zakresem dowolnej funkcji.

Lokalizowanie bloku sterującego w innych obszarach wymaga nieco więcej ostrożności, podobnie jak w przypadku całej pamięci przydzielanej dynamicznie. Jeśli blok sterujący jest przydzielany w ramach funkcji języka C, skojarzona z nim pamięć jest częścią stosu wątku wywołującego. Ogólnie rzecz biorąc, należy unikać używania magazynu lokalnego dla bloków sterujących, ponieważ po zwracaniu funkcji zwalniana jest cała jej przestrzeń stosu zmiennych lokalnych — niezależnie od tego, czy inny wątek używa jej dla bloku sterującego.

W większości przypadków aplikacja jest nieświeższa o zawartości bloku sterowania wątku. Jednak istnieją pewne sytuacje, szczególnie podczas debugowania, w których przydatne jest przyglądanie się niektórym członkom. Poniżej przedstawiono niektóre z bardziej przydatnych elementów członkowskich bloku sterowania.

**tx_thread_run_count** licznik liczby zaplanowanych wątków. Rosnący licznik wskazuje, że wątek jest zaplanowany i wykonywany.

**tx_thread_state** zawiera stan skojarzonego wątku. Poniżej wymieniono możliwe stany wątków.

|  Stan wątku   | Wartość |
| --------------- | ------ |
| TX_READY       | (0x00) |
| TX_COMPLETED   | (0x01) |
| TX_TERMINATED  | (0x02) |
| TX_SUSPENDED   | (0x03) |
| TX_SLEEP       | (0x04) |
| TX_QUEUE_SUSP | (0x05) |
| TX_SEMAPHORE_SUSP | (0x06) |
| TX_EVENT_FLAG   | (0x07) |
| TX_BLOCK_MEMORY | (0x08) |
| TX_BYTE_MEMORY  | (0x09) |
| TX_MUTEX_SUSP   | (0x0D) |

> [!NOTE]
> *Oczywiście blok sterowania wątku zawiera wiele innych interesujących pól, w tym wskaźnik stosu, wartość fragmentu czasu, priorytety itp. Użytkownicy mogą przeglądać elementy członkowskie bloku kontroli, ale modyfikacje są ściśle zabronione.*

> [!IMPORTANT]
> *Nie ma żadnego równika dla stanu "wykonywania" wspomnianego wcześniej w tej sekcji. Nie jest to konieczne, ponieważ w danym momencie wykonywany jest tylko jeden wątek. Stan wątku wykonującego jest również TX_READY* **.**

### <a name="currently-executing-thread"></a>Obecnie wykonywanie wątku

Jak wspomniano wcześniej, w danym momencie wykonywany jest tylko jeden wątek. Istnieje kilka sposobów identyfikowania wątku wykonującego, w zależności od tego, który wątek żąda.
Segment programu może uzyskać adres bloku sterowania wątku wykonującego, wywołując ***tx_thread_identify***. Jest to przydatne w udostępnionych fragmentach kodu aplikacji, które są wykonywane z wielu wątków.

W sesjach debugowania użytkownicy mogą sprawdzać wewnętrzny wskaźnik ThreadX ***_tx_thread_current_ptr***. Zawiera adres bloku sterowania aktualnie wykonywanego wątku. Jeśli ten wskaźnik ma wartość NULL, wątek aplikacji nie jest wykonywany; Tj. ThreadX czeka w pętli planowania, aby wątek stał się gotowy.

### <a name="thread-stack-area"></a>Obszar stosu wątku

Każdy wątek musi mieć własny stos do zapisywania kontekstu jego ostatniego wykonania i użycia kompilatora. Większość kompilatorów języka C używa stosu do tworzenia wywołań funkcji i tymczasowego przydzielania zmiennych lokalnych. Rysunek 6 przedstawia typowy stos wątku.

Miejsce, w którym stos wątków znajduje się w pamięci, należy do aplikacji. Obszar stosu jest określony podczas tworzenia wątku i może być umieszczony w dowolnym miejscu w przestrzeni adresowej obiektu docelowego. Jest to ważna funkcja, ponieważ umożliwia aplikacjom zwiększenie wydajności ważnych wątków przez umieszczenie ich stosu w pamięci RAM o dużej szybkości.

**Obszar pamięci stosu** (przykład)

![Typowy stos wątków](./media/user-guide/typical-thread-stack.png)

**RYSUNEK 6. Typowy stos wątków**

To, jak duży powinien być stos, to jedno z najczęściej zadawanych pytań dotyczących wątków. Obszar stosu wątku musi być wystarczająco duży, aby obsłużyć zagnieżdżanie wywołań funkcji najgorszego przypadku, alokację zmiennych lokalnych i zapisanie kontekstu ostatniego wykonania.

Minimalny rozmiar stosu, **TX_MINIMUM_STACK**, jest definiowany przez ThreadX. Stos o tym rozmiarze obsługuje zapisywanie kontekstu wątku i minimalnej ilości wywołań funkcji oraz alokacji zmiennych lokalnych.

Jednak w przypadku większości wątków minimalny rozmiar stosu jest zbyt mały, a użytkownik musi ustalić wymagania dotyczące rozmiaru w najgorszym przypadku, sprawdzając zagnieżdżanie wywołań funkcji i alokację zmiennych lokalnych. Oczywiście zawsze lepiej jest zacząć od większego obszaru stosu.

Po debugowaniu aplikacji można dostroić rozmiary stosu wątków, jeśli ilość pamięci jest za mało. Ulubioną sztuczką jest wstępne ustawienie wszystkich obszarów stosu za pomocą łatwego do zidentyfikowania wzorca danych, takiego 0xEFEF) przed utworzeniem wątków. Po dokładnym przeanalizowaniu tempa aplikacji można zbadać obszary stosu, aby sprawdzić, ile stosu rzeczywiście zostało użyte, znajdując obszar stosu, w którym wzorzec danych jest nadal nienaruszony. Rysunek 7 przedstawia ustawienie wstępne stosu do 0xEFEF po dokładnym wykonaniu wątku.

**Obszar pamięci stosu** (inny przykład)

![Ustawienie wstępne stosu do 0xEFEF*](./media/user-guide/stack-preset.png)

**RYSUNEK 7. Ustawienie wstępne stosu do 0xEFEF**

> [!IMPORTANT]
> *Domyślnie ThreadX inicjuje każdy bajt każdego stosu wątków o wartości 0xEF.*

### <a name="memory-pitfalls"></a>Pułapki pamięci

Wymagania dotyczące stosu dla wątków mogą być duże. Dlatego ważne jest zaprojektowanie aplikacji tak, aby zawierała rozsądną liczbę wątków. Ponadto należy uważać, aby uniknąć nadmiernego użycia stosu w wątkach. Należy unikać rekursywnych algorytmów i dużych lokalnych struktur danych.

W większości przypadków przepełniony stos powoduje, że wykonanie wątku powoduje uszkodzenie pamięci sąsiadującej (zazwyczaj przed) obszarem stosu. Wyniki są nieprzewidywalne, ale najczęściej skutkują nieoczywislną zmianą w liczniku programu. Jest to często nazywane "skokiem do chwasty". Oczywiście jedynym sposobem, aby temu zapobiec, jest upewnianie się, że wszystkie stosy wątków są wystarczająco duże.

### <a name="optional-run-time-stack-checking"></a>Opcjonalne sprawdzanie stosu czasu uruchamiania

ThreadX zapewnia możliwość sprawdzania stosu każdego wątku pod celu uszkodzenia w czasie wykonywania. Domyślnie ThreadX wypełnia każdy bajt stosów wątków przy użyciu 0xEF danych podczas tworzenia. Jeśli aplikacja tworzy bibliotekę ThreadX ze zdefiniowanymi TX_ENABLE_STACK_CHECKING, ThreadX przeanalizuje stos każdego wątku pod powodu uszkodzenia, ponieważ jest wstrzymany lub wznowiony.  W przypadku wykrycia uszkodzenia stosu ThreadX wywoła procedurę obsługi błędów stosu aplikacji określoną przez wywołanie funkcji **_tx_thread_stack_error_notify_*_. W przeciwnym razie, jeśli nie określono procedury obsługi błędów stosu, ThreadX wywoła* wewnętrzną _ tx_thread_stack_error_handler** procedury.

### <a name="reentrancy"></a>Ponowne wejścia

Jedną z rzeczywistych funkcji wielowątkowych jest możliwość wywoływania tej samej funkcji języka C z wielu wątków. Zapewnia to dużą moc, a także pomaga zmniejszyć ilość miejsca na kod. Jednak funkcja języka C wywoływana z wielu wątków wymaga *ponownego wytłaniania*.

Zasadniczo funkcja reentrant przechowuje adres zwrotny wywołującego na bieżącym stosie i nie polega na zmiennych globalnych lub statycznych języka C, które zostały wcześniej ustawione. Większość kompilatorów umieszcza adres zwrotny na stosie. W związku z tym deweloperzy aplikacji muszą martwić się tylko o używanie *danych globalnych* i *statycznych.*

Przykładem funkcji bez ponownego uwierzytelniania jest funkcja tokenu ***ciągu,*** która znajduje się w standardowej bibliotece języka C. Ta funkcja "zapamiętuje" poprzedni wskaźnik ciągu w kolejnych wywołaniach. Robi to za pomocą statycznego wskaźnika ciągu. Jeśli ta funkcja jest wywoływana z wielu wątków, najprawdopodobniej zwróci nieprawidłowy wskaźnik.

### <a name="thread-priority-pitfalls"></a>Pułapki priorytetów wątków

Wybór priorytetów wątku jest jednym z najważniejszych aspektów wielowątkowania. Czasami przypisywanie priorytetów w oparciu o postrzeganą istotność wątku jest czasami bardzo kuszące, a nie określanie, co dokładnie jest wymagane w czasie działania. Nieprawidłowe wykorzystanie priorytetów wątków może ograniczyć inne wątki, utworzyć odwrócenie priorytetu, zmniejszyć przepustowość przetwarzania i utrudnić zrozumienie zachowania aplikacji w czasie działania.

Jak wspomniano wcześniej, ThreadX zapewnia oparty na priorytecie, wywłaszczony algorytm planowania. Wątki o niższym priorytecie nie są wykonywane, dopóki nie ma wątków o wyższym priorytecie gotowych do wykonania. Jeśli wątek o wyższym priorytecie jest zawsze gotowy, wątki o niższym priorytecie nigdy nie są wykonywane. Ten warunek jest nazywany *wątkową blokowania*.

Większość problemów z wątkami jest wykrywanych na wczesnym etapie debugowania i można je rozwiązać, upewniając się, że wątki o wyższym priorytecie nie są wykonywane w sposób ciągły. Alternatywnie do aplikacji można dodać logikę, która stopniowo zwiększa priorytet wątków z blokowania, dopóki nie zostaną one wykonane.

Kolejną pułapką skojarzoną z priorytetami wątku *jest odwrócenie priorytetu*. Odwrócenie priorytetu ma miejsce, gdy wątek o wyższym priorytecie jest zawieszony, ponieważ wątek o niższym priorytecie ma wymagany zasób. Oczywiście w niektórych przypadkach konieczne jest, aby dwa wątki o różnym priorytecie współużytkować wspólny zasób. Jeśli te wątki są jedynymi aktywnymi, czas odwrócenia priorytetu jest ograniczony przez czas, w który wątek o niższym priorytecie przechowuje zasób. Ten warunek jest deterministyczny i dość normalny. Jeśli jednak wątki o priorytecie pośrednim staną się aktywne podczas tego warunku odwrócenia priorytetu, czas inwersji priorytetu nie będzie już deterministyczny i może spowodować awarię aplikacji.

Istnieją zasadniczo trzy różne metody zapobiegania niedeterministycznej odwrócenia priorytetu w ThreadX. Po pierwsze, wybór priorytetu aplikacji i zachowanie w czasie działania można zaprojektować w taki sposób, aby zapobiec problemowi z odwróceniem priorytetu. Po drugie wątki o  niższym priorytecie mogą wykorzystywać próg wywłaszczenia do blokowania wywłaszczenia z wątków pośrednich, gdy współdzielą zasoby z wątkami o wyższym priorytecie. Na koniec wątki używające obiektów mutex ThreadX do ochrony zasobów systemowych mogą korzystać z opcjonalnego dziedziczenia priorytetów *mutex* w celu wyeliminowania niedeterministycznego odwrócenia priorytetu.

### <a name="priority-overhead"></a>Priorytet narzutowy

Jednym z najczęściej pomijanych sposobów zmniejszenia obciążenia wielowątkowego jest zmniejszenie liczby przełączników kontekstu. Jak wspomniano wcześniej, przełącznik kontekstu występuje, gdy wykonywanie wątku o wyższym priorytecie jest preferowane niż wykonywania wątku. Warto wspomnieć, że wątki o wyższym priorytecie mogą stać się gotowe zarówno w wyniku zdarzeń zewnętrznych (takich jak przerwania), jak i wywołań usługi wykonanych przez wątek wykonujący.

Aby zilustrować wpływ *priorytetów* wątków na obciążenie przełącznika kontekstu, należy założyć trzy środowiska wątków z wątkami o *nazwach thread_1*, thread_2 i *thread_3*. Załóżmy dalej, że wszystkie wątki są w stanie wstrzymania w oczekiwaniu na komunikat. Gdy thread_1 komunikat, natychmiast przekazuje go do thread_2. Thread_2 następnie przekazuje komunikat do thread_3. Thread_3 odrzuca komunikat. Gdy każdy wątek przetwarza swój komunikat, wraca i czeka na inny komunikat.

Przetwarzanie wymagane do wykonania tych trzech wątków różni się znacznie w zależności od ich priorytetów. Jeśli wszystkie wątki mają ten sam priorytet, przed wykonaniem każdego wątku następuje pojedynczy przełącznik kontekstu. Przełączenie kontekstu występuje, gdy każdy wątek zawiesza się w pustej kolejce komunikatów.

Jeśli jednak thread_2 ma wyższy priorytet niż thread_1, thread_3 ma wyższy priorytet niż thread_2, liczba przełączeń kontekstu podwaja się. Jest to spowodowane innym przełączeniem kontekstu wewnątrz usługi *tx_queue_send,* gdy wykryje, że wątek o wyższym priorytecie jest teraz gotowy.

Mechanizm progu wywłaszczania ThreadX może uniknąć tych dodatkowych przełączników kontekstu i nadal zezwalać na wcześniej wymienione opcje priorytetu. Jest to ważna funkcja, ponieważ umożliwia kilka priorytetów wątków podczas planowania, jednocześnie eliminując niektóre niepożądane przełączanie kontekstu między nimi podczas wykonywania wątku.

### <a name="run-time-thread-performance-information"></a>Informacje o wydajności wątków w czasie wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności wątków w czasie wykonywania. Jeśli biblioteka i aplikacja ThreadX są budowane przy **TX_THREAD_ENABLE_PERFORMANCE_INFO,** threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

  - wznowienia wątku

  - zawieszenie wątku

  - wywłaszcze wywołań usługi

  - wywłaszcze przerwań

  - inversions priorytetu

  - wycinki czasu

  - relinquishes

  - limity czasu wątku

  - przerywanie zawieszenia

  - Bezczynne zwracane przez system

  - zwracany przez system bezczynny

Łączna liczba dla każdego wątku:

  - wznowienia

  - Zawieszenia

  - wywłaszcze wywołań usługi

  - wywłaszcze przerwań

  - inversions priorytetu

  - wycinki czasu

  - thread relinquishes

  - limity czasu wątku

  - przerywanie zawieszenia

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_thread_performance_info_get** _ i _*_tx_thread_performance_system_info_get_**. Informacje o wydajności wątków są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba wywłaszków wywołań usług może sugerować, że priorytet i/lub próg wywłaszczenia wątku jest zbyt niski. Ponadto stosunkowo niska liczba bezczynnych wątków systemowych może sugerować, że wątki o niższym priorytecie nie wstrzymują się wystarczająco.

### <a name="debugging-pitfalls"></a>Pułapki debugowania

Debugowanie aplikacji wielowątkowych jest nieco trudniejsze, ponieważ ten sam kod programu można wykonać z wielu wątków. W takich przypadkach sam punkt przerwania może nie być wystarczający. Debuger musi również wyświetlić bieżący wskaźnik wątku, _tx_thread_current_ptr **warunkowego** punktu przerwania, aby sprawdzić, czy wątek wywołujący jest tym, który ma być debugowany.

Większość z tych rozwiązań jest obsługiwanych w wielowątkowych pakietach pomocy technicznej oferowanych przez różnych dostawców narzędzi programistów. Ze względu na prosty projekt integracja narzędzia ThreadX z różnymi narzędziami programistyki jest stosunkowo łatwa.

Rozmiar stosu jest zawsze ważnym tematem debugowania w wielowątkowych. Za każdym razem, gdy obserwowane jest zachowanie niewyjaśnione, zwykle na początku dobrze jest zwiększyć rozmiar stosu dla wszystkich wątków — szczególnie rozmiar stosu ostatniego wątku do wykonania.

> [!TIP]
> *Dobrym pomysłem jest również skompilowanie biblioteki ThreadX przy użyciu **TX_ENABLE_STACK_CHECKING** zdefiniowanych. Pomoże to wyizolować problemy z uszkodzeniem stosu tak wcześnie, jak to możliwe w przetwarzaniu.*

## <a name="message-queues"></a>Kolejki komunikatów

Kolejki komunikatów to podstawowe sposoby komunikacji międzywątkowej w ThreadX. Co najmniej jeden komunikat może znajdować się w kolejce komunikatów. Kolejka komunikatów, która zawiera jeden komunikat, jest często nazywana skrzynką *pocztową*.

Komunikaty są kopiowane do kolejki za pomocą funkcji ***tx_queue_send** _, a komunikaty są kopiowane z kolejki przez _*_tx_queue_receive_**. Jedynym wyjątkiem od tej reguły jest wstrzymanie wątku podczas oczekiwania na komunikat w pustej kolejce. W takim przypadku następny komunikat wysyłany do kolejki jest umieszczany bezpośrednio w obszarze docelowym wątku.

Każda kolejka komunikatów jest zasobem publicznym. ThreadX nie stosuje żadnych ograniczeń co do sposobu, w jaki są używane kolejki komunikatów.

### <a name="creating-message-queues"></a>Tworzenie kolejek komunikatów

Kolejki komunikatów są tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. Nie ma żadnego limitu liczby kolejek komunikatów w aplikacji.

### <a name="message-size"></a>Rozmiar komunikatu

Każda kolejka komunikatów obsługuje wiele komunikatów o stałym rozmiarze. Dostępne rozmiary komunikatów to od 1 do 16 słów 32-bitowych włącznie. Rozmiar komunikatu jest określony podczas tworzenia kolejki. Komunikaty aplikacji większe niż 16 słów muszą być przekazywane przez wskaźnik. Jest to realizowane przez utworzenie kolejki o rozmiarze komunikatu 1 wyrazu (wystarczająco do przechowywania wskaźnika), a następnie wysłanie i odebranie wskaźników komunikatów zamiast całego komunikatu.

### <a name="message-queue-capacity"></a>Pojemność kolejki komunikatów

Liczba komunikatów, które może przechowywać kolejka, jest funkcją rozmiaru komunikatu i rozmiaru obszaru pamięci dostarczonego podczas tworzenia. Całkowita pojemność komunikatu kolejki jest obliczana przez podzielenie liczby bajtów w każdym komunikacie na łączną liczbę bajtów w dostarczonym obszarze pamięci.

Jeśli na przykład kolejka komunikatów, która obsługuje rozmiar komunikatu 1 32-bitowego słowa (4 bajty), zostanie utworzona z 100-bajtowym obszarem pamięci, jej pojemność to 25 komunikatów.

### <a name="queue-memory-area"></a>Obszar pamięci kolejki

Jak wspomniano wcześniej, obszar pamięci do buforowania komunikatów jest określony podczas tworzenia kolejki. Podobnie jak w przypadku innych obszarów pamięci w ThreadX, może ona być zlokalizowana w dowolnym miejscu w przestrzeni adresowej obiektu docelowego.

Jest to ważna funkcja, ponieważ zapewnia aplikacji dużą elastyczność. Na przykład aplikacja może zlokalizować obszar pamięci ważnej kolejki w pamięci RAM o dużej szybkości, aby zwiększyć wydajność.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas próby wysłania lub odbierania komunikatu z kolejki. Zazwyczaj zawieszenie wątku polega na oczekiwaniu na komunikat z pustej kolejki. Jednak wątek może zawiesić próbę wysłania komunikatu do pełnej kolejki.

Po rozpoznaniu warunku zawieszenia żądana usługa jest ukończona i wątek oczekiwania jest wznawiany. Jeśli wiele wątków jest zawieszonych w tej samej kolejce, są one wznawiane w kolejności, w których zostały wstrzymane (FIFO).

Jednak wznowienie priorytetu jest również możliwe, jeśli aplikacja ***wywołuje*** tx_queue_prioritize przed usługą kolejki, która podnosi zawieszenie wątku. Usługa priorytetów kolejki umieszcza wątek o najwyższym priorytecie na początku listy zawieszenia, pozostawiając wszystkie inne wstrzymane wątki w tej samej kolejności FIFO.

Dla wszystkich zawieszeń kolejek dostępne są również przeokierowania. Zasadniczo limit czasu określa maksymalną liczbę takt czasomierzy, które wątek pozostanie zawieszony. W przypadku przechowania czasu wątek jest wznawiany, a usługa wraca z odpowiednim kodem błędu.

### <a name="queue-send-notification"></a>Powiadomienie o wysyłaniu w kolejce

W przypadku niektórych aplikacji korzystne może być powiadomienie za każdym razem, gdy komunikat zostanie umieszczony w kolejce. ThreadX zapewnia tę możliwość za ***pośrednictwem tx_queue_send_notify*** service. Ta usługa rejestruje dostarczoną funkcję powiadomień aplikacji w określonej kolejce. ThreadX będzie następnie wywoływać tę funkcję powiadomień aplikacji za każdym razem, gdy komunikat zostanie wysłany do kolejki. Dokładne przetwarzanie w funkcji powiadomień aplikacji jest określane przez aplikację; Jednak zwykle polega na wznowieniu odpowiedniego wątku do przetwarzania nowego komunikatu.

### <a name="queue-event-chainingtrade"></a>Łańcuch zdarzeń kolejki&trade;

Możliwości powiadomień w ThreadX mogą służyć do łańcucha różnych zdarzeń synchronizacji. Jest to zazwyczaj przydatne, gdy jeden wątek musi przetwarzać wiele zdarzeń synchronizacji.

Załóżmy na przykład, że jeden wątek jest odpowiedzialny za przetwarzanie komunikatów z pięciu różnych kolejek i musi również zostać wstrzymany, gdy żadne komunikaty nie są dostępne. Można to łatwo osiągnąć, rejestrując funkcję powiadomień aplikacji dla każdej kolejki i wprowadzając dodatkowy semafor zliczania. W szczególności funkcja powiadamiania aplikacji wykonuje tx_semaphore_put *zawsze,* gdy jest wywoływana (liczba semaforów reprezentuje łączną liczbę komunikatów we wszystkich pięciu kolejkach). Wątek przetwarzania zawiesza się na tym semaforze za *pośrednictwem tx_semaphore_get* usługi. Gdy semafor jest dostępny (w tym przypadku gdy komunikat jest dostępny!), wątek przetwarzania jest wznawiany. Następnie sprawdza każdą kolejkę dla komunikatu, przetwarza znaleziony komunikat  i wykonuje kolejne tx_semaphore_get oczekiwanie na następny komunikat. Osiągnięcie tego celu bez łańcucha zdarzeń jest dość trudne i prawdopodobnie wymagałoby większej liczby wątków i/lub dodatkowego kodu aplikacji.

Ogólnie rzecz biorąc, *łańcuch zdarzeń* powoduje mniejszą liczbę wątków, mniejsze obciążenie i mniejsze wymagania dotyczące pamięci RAM. Zapewnia również wysoce elastyczny mechanizm do obsługi wymagań dotyczących synchronizacji bardziej złożonych systemów.

### <a name="run-time-queue-performance-information"></a>Informacje o wydajności kolejki w czasie wykonywania
ThreadX udostępnia opcjonalne informacje o wydajności kolejki w czasie wykonywania. Jeśli biblioteka i aplikacja ThreadX zostały skumulowane przy ***TX_QUEUE_ENABLE_PERFORMANCE_INFO,*** threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

  - wysłane komunikaty

  - odebrane komunikaty

  - kolejkowanie pustych zawieszeń

  - pełne zawieszenie kolejki

  - pełne zwracane błędy kolejki (nie określono zawieszenia)

  - limity czasu kolejki

Łączna liczba dla każdej kolejki:

  - wysłane komunikaty

  - odebrane komunikaty

  - kolejkowanie pustych zawieszeń

  - pełne zawieszenie kolejki

  - pełne zwracane błędy kolejki (nie określono zawieszenia)

  - limity czasu kolejki

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_queue_performance_info_get** _ i __*_ tx_queue_performance_system_info_get **. Informacje o wydajności kolejki są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba "zawieszeń pełnych kolejek" sugeruje, że zwiększenie rozmiaru kolejki może być korzystne.

### <a name="queue-control-block-tx_queue"></a>Blok sterowania kolejką TX_QUEUE

Cechy każdej kolejki komunikatów znajdują się w bloku sterującym. Zawiera on interesujące informacje, takie jak liczba komunikatów w kolejce. Ta struktura jest zdefiniowana w ***tx_api.h.***

Bloki sterowania kolejki komunikatów mogą również być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej kontrolka blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji.

### <a name="message-destination-pitfall"></a>Pułapka miejsca docelowego komunikatu

Jak wspomniano wcześniej, komunikaty są kopiowane między obszarem kolejki i obszarami danych aplikacji. Ważne jest, aby upewnić się, że miejsce docelowe odebranego komunikatu jest wystarczająco duże, aby pomieścić cały komunikat. Jeśli tak nie jest, pamięć po miejscu docelowym komunikatu prawdopodobnie będzie uszkodzona.

> [!NOTE]
> *Jest to szczególnie lethal, gdy na stosie znajduje się zbyt małe miejsce docelowe komunikatów — nic takiego jak uszkodzenie adresu zwracanej funkcji.*

## <a name="counting-semaphores"></a>Zliczanie semaforów

ThreadX zapewnia 32-bitowe zliczanie semaforów o wartości od 0 do 4 294 967 295. Istnieją dwie operacje zliczania semaforów:  tx_semaphore_get i *tx_semaphore_put*. Operacja get zmniejsza semafor o jeden. Jeśli semafor ma 0, operacja get nie powiedzie się. Odwrotnością operacji get jest operacja put.
Zwiększa ona semafor o jeden.

Każdy semafor zliczania jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń co do sposobu zliczania semaforów.

Zliczanie semaforów jest zwykle używane do *wzajemnego wykluczania*. Jednak zliczanie semaforów może być również używane jako metoda powiadamiania o zdarzeniach.

### <a name="mutual-exclusion"></a>Wzajemne wykluczanie

 Wzajemne wykluczanie dotyczy kontrolowania dostępu wątków do niektórych obszarów aplikacji (nazywanych również sekcjami krytycznymi *lub* *zasobami aplikacji).* W przypadku wzajemnego wykluczania "bieżąca liczba" semafora reprezentuje łączną liczbę wątków, do których dostęp jest dozwolony. W większości przypadków zliczanie semaforów używanych do wzajemnego wykluczania będzie mieć początkową wartość 1, co oznacza, że tylko jeden wątek może jednocześnie uzyskać dostęp do skojarzonego zasobu. Zliczanie semaforów, które mają tylko wartości 0 lub 1, są często nazywane *semaforami binarnymi*.

> [!IMPORTANT]
> *Jeśli jest używany binarny semafor, użytkownik musi uniemożliwić temu samemu wątku wykonanie operacji get na semaforze, który jest już właścicielem. Drugi get nie powiedzie się i może spowodować nieograniczone zawieszenie wywołującego wątku i trwałą niedostępność zasobu.*

### <a name="event-notification"></a>Powiadomienie o zdarzeniu

Istnieje również możliwość użycia zliczania semaforów jako powiadomienia o zdarzeniach w sposób producent—konsument. Konsument próbuje uzyskać semafor zliczania, podczas gdy producent zwiększa semafor zawsze, gdy coś jest dostępne. Takie semafory zwykle mają wartość początkową 0 i nie zwiększają się, dopóki producent nie będzie miał czegoś gotowego dla konsumenta. Semafory używane do powiadamiania o zdarzeniach mogą również korzystać z wywołania ***tx_semaphore_ceiling_put*** usługi. Ta usługa zapewnia, że liczba semaforów nigdy nie przekracza wartości podanej w wywołaniu.

### <a name="creating-counting-semaphores"></a>Tworzenie semaforów zliczania

Zliczanie semaforów jest tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. Początkowa liczba semafora jest określana podczas tworzenia. Nie ma żadnego limitu liczby semaforów zliczania w aplikacji.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas próby wykonania operacji get na semaforze z bieżącą licznikiem 0.

Po wykonaniu operacji put wykonywana jest operacja get wstrzymanego wątku, a wątek jest wznawiany. Jeśli wiele wątków jest zawieszonych na tym samym zliczeniu semafora, są one wznawiane w tej samej kolejności, w których zostały wstrzymane (FIFO).

Jednak wznowienie priorytetu jest również możliwe, jeśli aplikacja ***wywołuje*** tx_semaphore_prioritize przed wywołaniem semafora put, które podnosi zawieszenie wątku. Priorytet usługi semafora umieszcza wątek o najwyższym priorytecie na początku listy zawieszenia, pozostawiając wszystkie inne wstrzymane wątki w tej samej kolejności FIFO.

### <a name="semaphore-put-notification"></a>Powiadomienie Put Semaphore

W przypadku niektórych aplikacji korzystne może być powiadomienie za każdym razem, gdy zostanie wprowadzone semafor. ThreadX zapewnia tę możliwość za ***pośrednictwem tx_semaphore_put_notify*** usługi. Ta usługa rejestruje dostarczoną funkcję powiadomień aplikacji przy użyciu określonego semafora. ThreadX będzie następnie wywoływać tę funkcję powiadomień aplikacji za każdym razem, gdy zostanie wprowadzone semafor. Dokładne przetwarzanie w funkcji powiadomień aplikacji jest określane przez aplikację; Jednak zazwyczaj składa się on z wznowienie odpowiedniego wątku do przetwarzania nowego zdarzenia put semaphore.

### <a name="semaphore-event-chainingtrade"></a>Łańcuch zdarzeń Semaphore&trade;

Możliwości powiadomień w ThreadX mogą służyć do łańcucha różnych zdarzeń synchronizacji. Jest to zazwyczaj przydatne, gdy jeden wątek musi przetwarzać wiele zdarzeń synchronizacji.

Na przykład zamiast wstrzymywać oddzielne wątki dla komunikatu w kolejce, flag zdarzeń i semafora, aplikacja może zarejestrować procedurę powiadamiania dla każdego obiektu. Po wywołaniu procedura powiadamiania aplikacji może następnie wznowić pojedynczy wątek, który może interrogować każdy obiekt w celu znalezienia i przetworzyć nowe zdarzenie.

Ogólnie rzecz biorąc, *łańcuch zdarzeń* powoduje mniejszą liczbę wątków, mniejsze obciążenie i mniejsze wymagania dotyczące pamięci RAM. Zapewnia również wysoce elastyczny mechanizm do obsługi wymagań dotyczących synchronizacji bardziej złożonych systemów.

### <a name="run-time-semaphore-performance-information"></a>Informacje o wydajności semafora czasu wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności semafora czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX zostały skumulowane przy **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO,** threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

  - semaphore puts

  - semafor pobiera

  - semafor get suspensions

  - Semaphore get timeouts (Uzyskiwanie limitów czasu semafora)

Łączna liczba dla każdego semafora:

  - semaphore puts

  - semafor pobiera

  - semafor get suspensions

  - Semaphore get timeouts (Uzyskiwanie limitów czasu semafora)

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_semaphore_performance_info_get** _ i __*_ tx_semaphore_performance_system_info_get **. Informacje o wydajności Semafora są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba "limitów czasu get semaphore" może sugerować, że inne wątki zbyt długo wstrzymują zasoby.

### <a name="semaphore-control-block-tx_semaphore"></a>Blokuj kontrolki Semaphore TX_SEMAPHORE

Cechy każdego zliczania semafora znajdują się w bloku sterującym. Zawiera informacje, takie jak bieżąca liczba semaforów. Ta struktura jest zdefiniowana ***w tx_api.h.***

Bloki sterujące Semafora mogą być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

### <a name="deadly-embrace"></a>Deadly Embrace

Jedną z najbardziej interesujących i niebezpiecznych pułapek związanych z semaforami używanymi do wzajemnego wykluczania są przyjmy *.* Chłoniak, czyli *zakleszczenie,* to warunek, w którym co najmniej dwa wątki są zawieszane na czas nieokreślony podczas próby uzyskania już należących do siebie semaforów.

Ten warunek najlepiej zilustrować w dwóch wątkach, dwóch przykładach semaforów. Załóżmy, że pierwszy wątek jest właścicielem pierwszego semafora, a drugi wątek jest właścicielem drugiego semafora. Jeśli pierwszy wątek próbuje uzyskać drugi semafor i jednocześnie drugi wątek próbuje uzyskać pierwszy semafor, oba wątki wprowadźą warunek zakleszczenia. Ponadto jeśli te wątki zostaną wstrzymane na zawsze, skojarzone z nimi zasoby również zostaną zablokowane na zawsze. Rysunek 8 ilustruje ten przykład.

**Embrace (przykład)**

![Przykład zawieszonych wątków](./media/user-guide/example-suspended-threads.png)

**RYSUNEK 8. Przykład zawieszonych wątków**

W przypadku systemów czasu rzeczywistego można zapobiec objęciom przez wprowadzenie pewnych ograniczeń dotyczących sposobu uzyskiwania semaforów wątków. Wątki mogą mieć tylko jeden semafor na raz. Alternatywnie wątki mogą być właścicielami wielu semaforów, jeśli zbierają je w tej samej kolejności. W poprzednim przykładzie, jeśli pierwszy i drugi wątek uzyskają pierwszy i drugi semafor w kolejności, można zapobiec przyjęcia przez nich.

> [!TIP]
> *Istnieje również możliwość użycia przeskoku czasu zawieszenia skojarzonego z operacją get w celu odzyskania po wywłaścicieli.*

### <a name="priority-inversion"></a>Odwrócenie priorytetu

Kolejną pułapką związaną z semaforami wzajemnego wykluczania jest odwrócenie priorytetu. Ten temat jest bardziej w pełni omówiony w temacie "[Pułapki priorytetów wątków".](#thread-priority-pitfalls)

Podstawowy problem wynika z sytuacji, w której wątek o niższym priorytecie ma semafor, którego potrzebuje wątek o wyższym priorytecie. To samo w sobie jest normalne. Jednak wątki z priorytetami między nimi mogą spowodować, że inwersja priorytetu będzie trwała przez niedeterministyczny czas. Można to obsłużyć przez staranny wybór priorytetów wątku, użycie progu wywłaszczenia i tymczasowe podwyższenie priorytetu wątku, który jest właścicielem zasobu, do wątku o wysokim priorytecie.

## <a name="mutexes"></a>Muteksy

Oprócz semaforów ThreadX udostępnia również obiekt mutex. Mutex jest zasadniczo semaforem binarnym, co oznacza, że tylko jeden wątek może być jednocześnie właścicielem mutexu. Ponadto ten sam wątek może wielokrotnie wykonać pomyślną operację mutex get na posiadanym mutexie, dokładnie 4 294 967 295. Istnieją dwie operacje na obiekcie mutex: ***tx_mutex_get** _ i _*_tx_mutex_put_**. Operacja get uzyskuje mutex, który nie jest własnością innego wątku, podczas gdy operacja put zwalnia wcześniej uzyskany mutex. Aby wątek zwalniał mutex, liczba operacji put musi być równa liczbie poprzednich operacji get.

Każdy wierzchołek jest zasobem publicznym. ThreadX nie stosuje żadnych ograniczeń co do sposobu, w jaki są używane mutexe.

Mutexes ThreadX są używane wyłącznie do *wzajemnego wykluczania*. W przeciwieństwie do zliczania semaforów, mutexes nie mają zastosowania jako metoda powiadamiania o zdarzeniach.

### <a name="mutex-mutual-exclusion"></a>Wzajemne wykluczanie mutex

Podobnie jak w dyskusji w sekcji zliczania semaforów, wzajemne wykluczanie odnosi się  do kontrolowania dostępu wątków do niektórych obszarów aplikacji (nazywanych również sekcjami krytycznymi lub *zasobami aplikacji).* Jeśli jest dostępny, element mutex ThreadX będzie miał liczbę własności 0. Po wykonaniu mutex przez wątek liczba własności jest zwiększana raz dla każdej pomyślnej operacji get wykonanej na mutex i zmniejszana dla każdej pomyślnej operacji put.

### <a name="creating-mutexes"></a>Tworzenie mutexes

Mutexes ThreadX są tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. Początkowy warunek mutex jest zawsze "dostępny". Można również utworzyć element mutex z wybranym *dziedziczeniem priorytetu.*

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas próby wykonania operacji get na mutex już należącej do innego wątku.

Po wykonaniu tej samej liczby operacji put przez wątek, który jest właścicielem, wykonywana jest operacja get wstrzymanego wątku, dając jej własność mutex, a wątek jest wznawiany. Jeśli wiele wątków jest zawieszonych na tym samym wierzchołku, są one wznawiane w tej samej kolejności, w których zostały wstrzymane (FIFO).

Wznowienie priorytetu jest jednak wykonywane automatycznie, jeśli dziedziczenie priorytetu mutex zostało wybrane podczas tworzenia. Wznowienie priorytetu jest również możliwe,  jeśli aplikacja wywołuje tx_mutex_prioritize przed wywołaniem mutex put, które podnosi zawieszenie wątku. Priorytet usługi mutex umieszcza wątek o najwyższym priorytecie na początku listy zawieszenia, pozostawiając wszystkie inne wstrzymane wątki w tej samej kolejności FIFO.

### <a name="run-time-mutex-performance-information"></a>Informacje o wydajności mutex czasu wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności mutex czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX  są budowane TX_MUTEX_ENABLE_PERFORMANCE_INFO zdefiniowane, threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

- mutex puts

- mutex pobiera

- mutex get suspensions

- mutex get timeouts (limity czasu get mutex)

- mutex priority inversions (inversions priorytetu mutex)

- dziedziczenie priorytetów mutex

Łączna liczba dla każdego obiektu mutex:

  - mutex puts

  - mutex pobiera

  - mutex get suspensions

  - mutex get timeouts (limity czasu get mutex)

  - mutex priority inversions (inversions priorytetu mutex)

  - dziedziczenie priorytetów mutex

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_mutex_performance_info_get** _ i _*_tx_mutex_performance_system_info_get_**. Informacje o wydajności funkcji Mutex są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba "limitów czasu get mutex" może sugerować, że inne wątki zbyt długo wstrzymują zasoby.

### <a name="mutex-control-block-tx_mutex"></a>Blok sterowania mutex TX_MUTEX

Cechy każdego mutexu znajdują się w jego bloku sterującym. Zawiera informacje, takie jak bieżąca liczba własności mutex wraz ze wskaźnikiem wątku, który jest właścicielem mutex. Ta struktura jest zdefiniowana ***w tx_api.h.*** Bloki sterowania mutex mogą być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

### <a name="deadly-embrace"></a>Deadly Embrace

Jedną z najbardziej interesujących i niebezpiecznych pułapek związanych z własnością mutex jest *przyjmowa.* Zakleszczenie to warunek, w którym co najmniej dwa wątki są wsadowe na czas nieokreślony podczas próby uzyskania mutex już należącego do innych wątków. Omówienie *ujścia języka* i jego środków zaradczych jest również całkowicie prawidłowe dla obiektu mutex.

### <a name="priority-inversion"></a>Odwrócenie priorytetu

Jak wspomniano wcześniej, główną pułapką związaną ze wzajemnego wykluczania jest odwrócenie priorytetu. Ten temat został dokładniej omówiony w temacie["Pułapki priorytetów wątków".](#thread-priority-pitfalls)

Podstawowy problem wynika z sytuacji, w której wątek o niższym priorytecie ma semafor, którego potrzebuje wątek o wyższym priorytecie. To samo w sobie jest normalne. Jednak wątki z priorytetami między nimi mogą spowodować, że inwersja priorytetu będzie trwała przez niedeterministyczny czas. W przeciwieństwie do semaforów omówiony wcześniej, obiekt mutex ThreadX ma opcjonalne *dziedziczenie priorytetu*. Podstawowym założeniem dziedziczenia priorytetów jest to, że wątek o niższym priorytecie ma tymczasowo podniesiony priorytet do priorytetu wątku o wysokim priorytecie, który chce mieć ten sam wierzchołek należący do wątku o niższym priorytecie. Gdy wątek o niższym priorytecie zwalnia mutex, jego oryginalny priorytet jest przywracany, a wątek o wyższym priorytecie jest nadawać własność mutex. Ta funkcja eliminuje niedeterministyczne odwrócenie priorytetu przez zmniejszenie wartości inwersji do czasu, gdy wątek o niższym priorytecie zawiera element mutex. Oczywiście techniki omówione wcześniej w tym rozdziale w celu obsługi niedeterministycznego odwrócenia priorytetu są również prawidłowe w przypadku mutexes.

## <a name="event-flags"></a>Flagi zdarzeń

Flagi zdarzeń zapewniają zaawansowane narzędzie do synchronizacji wątków. Każda flaga zdarzenia jest reprezentowana przez pojedynczy bit. Flagi zdarzeń są uporządkowane w grupach po 32. Wątki mogą działać na wszystkich 32 flagach zdarzeń w grupie w tym samym czasie. Zdarzenia są ustawiane przez ***tx_event_flags_set** _ i są pobierane przez _*_tx_event_flags_get_**.

Ustawianie flag zdarzeń jest wykonywane za pomocą operacji logicznej AND/OR między bieżącymi flagami zdarzeń i nowymi flagami zdarzeń. Typ operacji logicznej (AND lub OR) jest określony w ***wywołaniu tx_event_flags_set*** .

Istnieją podobne opcje logiczne pobierania flag zdarzeń. Żądanie get może określać, że wszystkie określone flagi zdarzeń są wymagane (operator logiczny AND).

Alternatywnie żądanie get może określić, że dowolna z określonych flag zdarzeń będzie spełniać żądanie (logiczne OR). Typ operacji logicznej skojarzony z pobieraniem flag zdarzeń jest określony w ***wywołaniu tx_event_flags_get*** zdarzenia.

> [!IMPORTANT]
> *Flagi zdarzeń,*   które spełniają wymagania żądania get, są używane, tj. ustawione na zero, jeśli TX_OR_CLEAR lub **TX_AND_CLEAR** są określone *przez żądanie.*

Każda grupa flag zdarzeń jest zasobem publicznym. ThreadX nie stosuje żadnych ograniczeń co do sposobu, w jaki są używane grupy flag zdarzeń.

### <a name="creating-event-flags-groups"></a>Tworzenie grup flag zdarzeń

Grupy flag zdarzeń są tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. W momencie ich tworzenia wszystkie flagi zdarzeń w grupie są ustawione na zero. Nie ma żadnego limitu liczby grup flag zdarzeń w aplikacji.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas próby uzyskania dowolnej logicznej kombinacji flag zdarzeń z grupy. Po skonfigurowaniu flagi zdarzenia żądania get wszystkich zawieszonych wątków są przeglądane. Wszystkie wątki, które mają teraz wymagane flagi zdarzeń, zostaną wznowione.

> [!NOTE]
> *Wszystkie wstrzymane wątki w grupie flag zdarzeń są przeglądane, gdy są ustawione jej flagi zdarzeń. Oczywiście stanowi to dodatkowe obciążenie. W związku z tym dobrym rozwiązaniem jest ograniczenie liczby wątków używających tej samej grupy flag zdarzeń do rozsądnej liczby.*

### <a name="event-flags-set-notification"></a>Powiadomienie o zestawie flag zdarzeń

W przypadku niektórych aplikacji korzystne może być powiadomienie za każdym razem, gdy jest ustawiona flaga zdarzenia. ThreadX zapewnia tę możliwość za ***pośrednictwem tx_event_flags_set_notify*** usługi. Ta usługa rejestruje dostarczoną funkcję powiadomień aplikacji z określoną grupą flag zdarzeń. ThreadX będzie następnie wywoływać tę funkcję powiadomień aplikacji za każdym razem, gdy zostanie ustawiona flaga zdarzenia w grupie. Dokładne przetwarzanie w ramach funkcji powiadomień aplikacji jest określane przez aplikację, ale zazwyczaj polega na wznowieniu odpowiedniego wątku do przetwarzania nowej flagi zdarzenia.

### <a name="event-flags-event-chainingtrade"></a>Łańcuch zdarzeń flag zdarzeń&trade;

Możliwości powiadomień w ThreadX mogą służyć do "łańcucha" różnych zdarzeń synchronizacji. Jest to zazwyczaj przydatne, gdy jeden wątek musi przetworzyć wiele zdarzeń synchronizacji.

Na przykład zamiast oddzielnych wątków wstrzymywanych dla komunikatu w kolejce, flag zdarzeń i semafora, aplikacja może zarejestrować procedurę powiadamiania dla każdego obiektu. Po wywołaniu procedura powiadamiania aplikacji może następnie wznowić pojedynczy wątek, który może interrogować każdy obiekt w celu znalezienia i przetwarzania nowego zdarzenia.

Ogólnie rzecz biorąc, *łańcuch zdarzeń* powoduje mniejszą liczbę wątków, mniejsze obciążenie i mniejsze wymagania dotyczące pamięci RAM. Zapewnia również wysoce elastyczny mechanizm obsługi wymagań dotyczących synchronizacji w bardziej złożonych systemach.

### <a name="run-time-event-flags-performance-information"></a>Informacje o wydajności flag zdarzeń czasu wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności flag zdarzeń czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX są budowane przy **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO,** threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

  - zestawy flag zdarzeń

  - pobiera flagi zdarzeń

  - flagi event get suspensions

  - Flagi zdarzeń uzyskają limity czasu

Łączna liczba dla każdej grupy flag zdarzeń:

  - zestawy flag zdarzeń

  - pobiera flagi zdarzeń

  - flagi event get suspensions

  - Flagi zdarzeń uzyskają limity czasu

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_event_flags_performance_info_get** _ _*_i tx_event_flags_performance_system_info_get_*_. Informacje o wydajności flag zdarzeń są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba limitów czasu w usłudze _ *_tx_event_flags_get_** może sugerować, że limit czasu wstrzymania flag zdarzeń jest zbyt krótki.

### <a name="event-flags-group-control-block-tx_event_flags_group"></a>Blokuj kontrolki grupy flag zdarzeń TX_EVENT_FLAGS_GROUP

Cechy każdej grupy flag zdarzeń znajdują się w jej bloku sterującym. Zawiera informacje, takie jak bieżące ustawienia flag zdarzeń i liczba wątków wstrzymanych dla zdarzeń. Ta struktura jest zdefiniowana ***w tx_api.h.***

Bloki sterowania grupy zdarzeń mogą być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

### <a name="memory-block-pools"></a>Pule bloków pamięci

Szybkie i deterministyczne przydzielanie pamięci zawsze stanowi wyzwanie w aplikacjach czasu rzeczywistego. Mając to na uwadze, ThreadX zapewnia możliwość tworzenia wielu pul bloków pamięci o stałym rozmiarze i zarządzania nimi.

Ponieważ pule bloków pamięci składają się z bloków o stałym rozmiarze, nigdy nie występują problemy z fragmentacją. Oczywiście fragmentacja powoduje zachowanie, które jest z założenia niedeterministyczne. Ponadto czas wymagany do przydzielenia i wolnego bloku pamięci o stałym rozmiarze jest porównywalny z prostym manipulowaniem listami połączonymi. Ponadto alokacja bloków pamięci i ich co najmniej alokacja odbywa się na początku dostępnej listy. Zapewnia to najszybsze możliwe przetwarzanie połączonych list i może pomóc w zatrzymaniu rzeczywistego bloku pamięci w pamięci podręcznej.

Brak elastyczności jest główną wadą pul pamięci o stałym rozmiarze. Rozmiar bloku puli musi być wystarczająco duży, aby obsłużyć najgorsze wymagania dotyczące pamięci użytkowników. Oczywiście pamięć może zostać zmarnowana, jeśli do tej samej puli zostanie wykonanych wiele żądań pamięci o różnym rozmiarze. Możliwym rozwiązaniem jest użycie kilku różnych pul bloków pamięci, które zawierają bloki pamięci o różnych rozmiarach.

Każda pula bloków pamięci jest zasobem publicznym. ThreadX nie stosuje żadnych ograniczeń co do sposobu, w jaki są używane pule.

### <a name="creating-memory-block-pools"></a>Tworzenie pul bloków pamięci

Pule bloków pamięci są tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. Nie ma żadnego limitu liczby pul bloków pamięci w aplikacji.

### <a name="memory-block-size"></a>Rozmiar bloku pamięci

Jak wspomniano wcześniej, pule bloków pamięci zawierają wiele bloków o stałym rozmiarze. Rozmiar bloku w bajtach jest określony podczas tworzenia puli.

> [!NOTE]
> *ThreadX dodaje niewielki narzut — rozmiar wskaźnika C — do każdego bloku pamięci w puli. Ponadto ThreadX może być konieczne uzupełnienie rozmiaru bloku, aby zachować początek każdego bloku pamięci przy odpowiednim wyrównaniu.*

### <a name="pool-capacity"></a>Pojemność puli

Liczba bloków pamięci w puli jest funkcją rozmiaru bloku i całkowitej liczby bajtów w obszarze pamięci dostarczonym podczas tworzenia. Pojemność puli jest obliczana przez podzielenie rozmiaru bloku (w tym wypełnienia i narzutu wskaźnika w bajtach) na łączną liczbę bajtów w dostarczonym obszarze pamięci.

### <a name="pools-memory-area"></a>Obszar pamięci puli

Jak wspomniano wcześniej, obszar pamięci dla puli bloków jest określony podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci w ThreadX, może ona być zlokalizowana w dowolnym miejscu w przestrzeni adresowej obiektu docelowego.

Jest to ważna funkcja ze względu na dużą elastyczność, która zapewnia. Załóżmy na przykład, że produkt komunikacyjny ma obszar pamięci o dużej szybkości dla we/wy. Tym obszarem pamięci można łatwo zarządzać, przez wprowadzenie go do puli bloków pamięci ThreadX.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas oczekiwania na blok pamięci z pustej puli. Gdy blok jest zwracany do puli, wstrzymany wątek jest podany ten blok i wątek jest wznawiany.

Jeśli wiele wątków jest zawieszonych w tej samej puli bloków pamięci, są one wznawiane w kolejności, w których zostały wstrzymane (FIFO).

Jednak wznowienie priorytetu jest również możliwe, jeśli aplikacja ***wywołuje*** tx_block_pool_prioritize przed wywołaniem wydania bloku, które podnosi zawieszenie wątku. Usługa priorytetów puli bloków umieszcza wątek o najwyższym priorytecie na początku listy zawieszenia, pozostawiając wszystkie inne wstrzymane wątki w tej samej kolejności FIFO.

### <a name="run-time-block-pool-performance-information"></a>Informacje o wydajności puli bloków czasu wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności puli bloków czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX są budowane przy **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO,** threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

  - przydzielone bloki

  - wydane bloki

  - wstrzymanie alokacji

  - limity czasu alokacji

Łączna liczba dla każdej puli bloków:

  - przydzielone bloki

  - wydane bloki

  - wstrzymanie alokacji

  - limity czasu alokacji

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_block_pool_performance_info_get** _ i _*_tx_block_pool_performance_system_info_get_**. Informacje o wydajności puli bloków są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba "zawieszeń alokacji" może sugerować, że pula bloków jest zbyt mała.

### <a name="memory-block-pool-control-block-tx_block_pool"></a>Blokowy blok pamięci blokowy blokowy blokowy blokowy TX_BLOCK_POOL

Cechy każdej puli bloków pamięci znajdują się w jej bloku sterującym. Zawiera informacje, takie jak liczba dostępnych bloków pamięci i rozmiar bloku puli pamięci. Ta struktura jest zdefiniowana ***w tx_api.h.***

Bloki sterowania puli mogą również być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

### <a name="overwriting-memory-blocks"></a>Nadpisanie bloków pamięci

Należy się upewnić, że użytkownik przydzielonego bloku pamięci nie zapisuje poza jego granicami. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) obszarze pamięci. Wyniki są nieprzewidywalne i często krytyczne dla aplikacji.

## <a name="memory-byte-pools"></a>Pule bajtów pamięci

Pule bajtów pamięci ThreadX są podobne do standardowej sterty C. W przeciwieństwie do standardowej sterty C, istnieje możliwość użycia wielu pul bajtów pamięci. Ponadto wątki mogą wstrzymywać się w puli do momentu, aż żądana pamięć będzie dostępna.

Alokacje z pul bajtów pamięci są podobne do tradycyjnych wywołań ***malloc** _, które obejmują żądaną ilość pamięci (w bajtach). Pamięć jest przydzielana z puli w _first dopasować*. oznacza to, że jest używany pierwszy blok wolnej pamięci, który spełnia żądanie. Nadmiarowa pamięć z tego bloku jest konwertowana na nowy blok i umieszczana z powrotem na liście wolnej pamięci. Ten proces jest nazywany *fragmentacją*.

Sąsiadujące bloki wolnej pamięci *są scalane* razem podczas kolejnego wyszukiwania alokacji w celu wyszukania wystarczająco dużego bloku wolnej pamięci. Ten proces jest nazywany *defragmentacją.*

Każda pula bajtów pamięci jest zasobem publicznym. ThreadX nie stosuje żadnych ograniczeń co do sposobu użycia pul, z tą różnicą, że usługi bajtów pamięci nie mogą być wywoływane z serwerów ISR.

### <a name="creating-memory-byte-pools"></a>Tworzenie pul bajtów pamięci

Pule bajtów pamięci są tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. Nie ma żadnego limitu liczby pul bajtów pamięci w aplikacji.

### <a name="pool-capacity"></a>Pojemność puli

Liczba przydzielanych bajtów w puli bajtów pamięci jest nieco mniejsza niż określona podczas tworzenia. Wynika to z tego, że zarządzanie obszarem wolnej pamięci wprowadza pewne obciążenia. Każdy blok wolnej pamięci w puli wymaga odpowiednika dwóch wskaźników obciążenia C. Ponadto pula jest tworzona z dwoma blokami: dużym blokiem swobodnym i małym trwale przydzielonym blokiem na końcu obszaru pamięci. Ten przydzielony blok służy do poprawy wydajności algorytmu alokacji. Eliminuje to konieczność ciągłego sprawdzania końca obszaru puli podczas scalania.

W czasie trwania zwykle zwiększa się obciążenie puli. Alokacje nieparzystej liczby bajtów są dosłaniane w celu zapewnienia odpowiedniego wyrównania następnego bloku pamięci. Ponadto obciążenie zwiększa się, gdy pula staje się bardziej pofragmentowana.

### <a name="pools-memory-area"></a>Obszar pamięci puli

Obszar pamięci dla puli bajtów pamięci jest określony podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci w ThreadX, może ona być zlokalizowana w dowolnym miejscu w przestrzeni adresowej obiektu docelowego. Jest to ważna funkcja ze względu na dużą elastyczność, która zapewnia. Jeśli na przykład sprzęt docelowy ma obszar pamięci o dużej szybkości i obszar pamięci o małej szybkości, użytkownik może zarządzać alokacją pamięci dla obu obszarów, tworząc pulę w każdym z nich.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą zostać wstrzymane podczas oczekiwania na bajty pamięci z puli. Gdy dostępna jest wystarczająca ilość ciągłej pamięci, wstrzymane wątki mają żądaną pamięć i wątki są wznawiane.

Jeśli wiele wątków jest zawieszonych w tej samej puli bajtów pamięci, są one nadane pamięci (wznowione) w kolejności, w których zostały wstrzymane (FIFO).

Jednak wznowienie priorytetu jest również możliwe,  jeśli aplikacja wywołuje tx_byte_pool_prioritize przed wywołaniem wydania bajtów, które podnosi zawieszenie wątku. Usługa priorytetów puli bajtów umieszcza wątek o najwyższym priorytecie na początku listy zawieszenia, pozostawiając wszystkie inne wstrzymane wątki w tej samej kolejności FIFO.

### <a name="run-time-byte-pool-performance-information"></a>Informacje o wydajności puli bajtów czasu wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności puli bajtów czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX  są budowane TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO zdefiniowane, threadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

  - Alokacji

  - wersje

  - przeszukiwane fragmenty

  - scalone fragmenty

  - utworzone fragmenty

  - wstrzymanie alokacji

  - limity czasu alokacji

Łączna liczba dla każdej puli bajtów:

  - Alokacji

  - wersje

  - przeszukiwane fragmenty

  - scalone fragmenty

  - utworzone fragmenty

  - wstrzymanie alokacji

  - limity czasu alokacji

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_byte_pool_performance_info_get** _ i _*_tx_byte_pool_performance_system_info_get_**. Informacje o wydajności puli bajtów są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji. Na przykład stosunkowo duża liczba "zawieszeń alokacji" może sugerować, że pula bajtów jest zbyt mała.

### <a name="memory-byte-pool-control-block-tx_byte_pool"></a>Blok sterowania puli bajtów pamięci TX_BYTE_POOL

Charakterystyki każdej puli bajtów pamięci znajdują się w jej bloku sterującym. Zawiera on przydatne informacje, takie jak liczba dostępnych bajtów w puli. Ta struktura jest zdefiniowana ***w tx_api.h.***

Bloki sterowania puli mogą również być zlokalizowane w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

### <a name="nondeterministic-behavior"></a>Niedeterministyczne zachowanie

Mimo że pule bajtów pamięci zapewniają najbardziej elastyczną alokację pamięci, również mają nieco niedeterministyczne zachowanie. Na przykład pula bajtów pamięci może mieć 2000 bajtów dostępnej pamięci, ale może nie być w stanie spełnić żądania alokacji o 1000 bajtów. Wynika to z tego, że nie ma żadnych gwarancji, ile wolnych bajtów jest ciągłych. Nawet jeśli istnieje blok o długości 1000 bajtów, nie ma gwarancji, jak długo może potrwać znalezienie bloku. Jest całkowicie możliwe, że trzeba przeszukać całą pulę pamięci, aby znaleźć blok 1000 bajtów.

> [!TIP]
> *W wyniku niedeterministycznego zachowania pul bajtów pamięci zazwyczaj dobrym rozwiązaniem jest unikanie korzystania z usług bajtów pamięci w obszarach, w których jest wymagane deterministyczne zachowanie w czasie rzeczywistym. Wiele aplikacji wstępnie przydziela wymaganą pamięć podczas inicjowania lub konfigurowania w czasie działania.*

### <a name="overwriting-memory-blocks"></a>Nadpisanie bloków pamięci

Ważne jest, aby upewnić się, że użytkownik przydzielonej pamięci nie zapisuje poza jego granicami. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) obszarze pamięci. Wyniki są nieprzewidywalne i często katastrofalne dla wykonywania programu.

## <a name="application-timers"></a>Czasomierze aplikacji

Szybka odpowiedź na asynchroniczne zdarzenia zewnętrzne jest najważniejszą funkcją aplikacji osadzonych w czasie rzeczywistym. Jednak wiele z tych aplikacji musi również wykonywać pewne działania we wstępnie określonych odstępach czasu.

Czasomierze aplikacji ThreadX zapewniają aplikacjom możliwość wykonywania funkcji aplikacji C w określonych odstępach czasu. Czasomierz aplikacji może również wygasać tylko raz. Ten typ czasomierza jest nazywany czasomierzem jednozdniowym, a powtarzające się czasomierze interwałów są nazywane *czasomierzami okresowymi*.

Każdy czasomierz aplikacji jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń co do sposobu stosowania czasomierzy aplikacji.

### <a name="timer-intervals"></a>Interwały czasomierza

Interwały czasu ThreadX są mierzone za pomocą okresowych przerwań czasomierza. Każde przerwanie czasomierza jest nazywane taktą *czasomierza*. Rzeczywisty czas między taktami czasomierza jest określony przez aplikację, ale 10 ms jest normą w przypadku większości implementacji. Okresowa konfiguracja czasomierza zwykle znajduje się ***w tx_initialize_low_level*** zestawu.

Warto wspomnieć, że podstawowy sprzęt musi mieć możliwość generowania okresowych przerwań, aby czasomierze aplikacji działały. W niektórych przypadkach procesor ma wbudowaną funkcję okresowych przerwań. Jeśli procesor nie ma takiej możliwości, tablica użytkownika musi mieć urządzenie peryferyjne, które może generować okresowe przerwania.

> [!IMPORTANT]
> *ThreadX może nadal działać nawet bez źródła okresowych przerwań. Jednak całe przetwarzanie związane z czasomierzem jest następnie wyłączone. Obejmuje to użytą usługę timelicing, time timelicing, time-outs zawieszenia i czasomierza.*

### <a name="timer-accuracy"></a>Dokładność czasomierza

Czasy wygaśnięcia czasomierza są określane jako takty. Określona wartość wygaśnięcia jest zmniejszana o jedną na każdej taktce czasomierza. Ponieważ czasomierz aplikacji można włączyć tuż przed przerwaniem czasomierza (lub taktą czasomierza), rzeczywisty czas wygaśnięcia może być nawet o jeden znacznik wcześniej.

Jeśli czasomierz wynosi 10ms, czasomierze aplikacji mogą wygasnąć do 10ms wcześnie. Jest to bardziej znaczące w przypadku czasomierzy 10m niż 1 sekundy. Oczywiście zwiększenie częstotliwości przerwań czasomierza zmniejsza ten margines błędu.

### <a name="timer-execution"></a>Wykonywanie czasomierza

Czasomierze aplikacji są wykonywane w kolejności, w których stają się aktywne. Jeśli na przykład trzy czasomierze zostaną utworzone z taką samą wartością wygaśnięcia i aktywowane, ich odpowiednie funkcje wygasania będą wykonywane w kolejności, w których zostały aktywowane.

### <a name="creating-application-timers"></a>Tworzenie czasomierzy aplikacji

Czasomierze aplikacji są tworzone podczas inicjowania lub w czasie uruchamiania przez wątki aplikacji. Nie ma żadnego limitu liczby czasomierzy aplikacji w aplikacji.

### <a name="run-time-application-timer-performance-information"></a>Informacje o wydajności czasomierza aplikacji w czasie wykonywania

ThreadX udostępnia opcjonalne informacje o wydajności czasomierza aplikacji w czasie wykonywania. Jeśli biblioteka i aplikacja ThreadX są budowane TX_TIMER_ENABLE_PERFORMANCE_INFO **zdefiniowane,** ThreadX gromadzi następujące informacje.

Łączna liczba dla całego systemu:

- Aktywacji

- dezaktywacje

- reaktywacja (czasomierze okresowe)

- Wygasania

- korekty wygasania

Łączna liczba dla każdego czasomierza aplikacji:

- Aktywacji

- dezaktywacje

- reaktywacja (czasomierze okresowe)

- Wygasania

- korekty wygasania

Te informacje są dostępne w czasie rzeczywistym za pośrednictwem usług ***tx_timer_performance_info_get** _ i __*_ tx_timer_performance_system_info_get **. Informacje o wydajności czasomierza aplikacji są przydatne podczas określania, czy aplikacja działa prawidłowo. Jest to również przydatne podczas optymalizacji aplikacji.

### <a name="application-timer-control-block-tx_timer"></a>Blok sterowania czasomierzem aplikacji TX_TIMER

Właściwości każdego czasomierza aplikacji znajdują się w bloku sterowania. Zawiera on przydatne informacje, takie jak 32-bitowa wartość identyfikacji wygaśnięcia. Ta struktura jest zdefiniowana w ***tx_api.h.***

Bloki sterowania czasomierza aplikacji mogą się znaleźć w dowolnym miejscu w pamięci, ale najczęściej kontrolka blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji.

### <a name="excessive-timers"></a>Nadmierne czasomierze

Domyślnie czasomierze aplikacji są wykonywane z poziomu ukrytego wątku systemowego uruchamianego z priorytetem zero, który jest zwykle wyższy niż dowolny wątek aplikacji. W związku z tym przetwarzanie wewnątrz czasomierzy aplikacji powinno być minimalne.

Ważne jest również, aby zawsze, gdy jest to możliwe, unikać czasomierzy, które wygasają po każdym znaczniku czasomierza. Taka sytuacja może powodować nadmierne obciążenie aplikacji.

> [!IMPORTANT]
> *Jak wspomniano wcześniej, czasomierze aplikacji są wykonywane z ukrytego wątku systemowego. Dlatego ważne jest, aby nie wybierać zawieszenia dla żadnych wywołań usługi ThreadX wykonanych z poziomu funkcji wygasania czasomierza aplikacji.*

## <a name="relative-time"></a>Czas względny

Oprócz czasomierzy aplikacji wymienionych wcześniej, ThreadX zapewnia jeden stale powiększający się 32-bitowy licznik taktowy. Licznik taktowy lub *czas jest* zwiększany o jeden na każdym przerwaniu czasomierza.

Aplikacja może odczytywać lub ustawiać ten licznik 32-bitowy za pośrednictwem wywołań odpowiednio do ***tx_time_get** _ i __*_ tx_time_set **. Użycie tego licznika taktowego jest określane całkowicie przez aplikację. Nie jest on używany wewnętrznie przez ThreadX.

## <a name="interrupts"></a>Przerwania

Szybka odpowiedź na zdarzenia asynchroniczne jest główną funkcją aplikacji osadzonych w czasie rzeczywistym. Aplikacja wie, że takie zdarzenie występuje za pośrednictwem przerwań sprzętowych.

Przerwanie to asynchroniczna zmiana w wykonywaniu procesora. Zwykle w przypadku przerwania procesor  przerwań zapisuje niewielką część bieżącego wykonania na stosie i przekazuje sterowanie do odpowiedniego wektora przerwań. Wektor przerwań to po prostu adres procedury odpowiedzialnej za obsługę przerwań określonego typu. Dokładna procedura obsługi przerwań jest specyficzna dla procesora.

### <a name="interrupt-control"></a>Sterowanie przerwaniami

Usługa ***tx_interrupt_control*** umożliwia aplikacjom włączanie i wyłączanie przerwań. Poprzednia przerwa w włączaniu/wyłączaniu jest zwracana przez tę usługę. Należy pamiętać, że kontrola przerwań ma wpływ tylko na aktualnie wykonywany segment programu. Jeśli na przykład wątek wyłączy przerwania, pozostaną one wyłączone tylko podczas wykonywania tego wątku.

> [!NOTE]
> *Przerwanie niemaskowalne (NMI, Non-Maskable Interrupt) to przerwanie, które nie może zostać wyłączone przez sprzęt. Takie przerwanie może być używane przez aplikacje ThreadX. Jednak procedura obsługi interfejsu NMI aplikacji nie może używać zarządzania kontekstem ThreadX ani żadnych usług interfejsu API.*

### <a name="threadx-managed-interrupts"></a>Przerwania zarządzane ThreadX

ThreadX zapewnia aplikacjom pełne zarządzanie przerwami. To zarządzanie obejmuje zapisywanie i przywracanie kontekstu przerwanego wykonywania. Ponadto ThreadX umożliwia wywoływanie niektórych usług z poziomu procedur usługi przerwań (ISR). Poniżej znajduje się lista usług ThreadX dozwolonych od serwerów ISR aplikacji.

```c
tx_block_allocate
tx_block_pool_info_get tx_block_pool_prioritize
tx_block_pool_performance_info_get
tx_block_pool_performance_system_info_get tx_block_release
tx_byte_pool_info_get tx_byte_pool_performance_info_get
tx_byte_pool_performance_system_info_get
tx_byte_pool_prioritize tx_event_flags_info_get
tx_event_flags_get tx_event_flags_set
tx_event_flags_performance_info_get
tx_event_flags_performance_system_info_get
tx_event_flags_set_notify tx_interrupt_control
tx_mutex_performance_info_get
tx_mutex_performance_system_info_get tx_queue_front_send
tx_queue_info_get tx_queue_performance_info_get
tx_queue_performance_system_info_get tx_queue_prioritize
tx_queue_receive tx_queue_send tx_semaphore_get
tx_queue_send_notify tx_semaphore_ceiling_put
tx_semaphore_info_get tx_semaphore_performance_info_get
tx_semaphore_performance_system_info_get
tx_semaphore_prioritize tx_semaphore_put tx_thread_identify
tx_semaphore_put_notify tx_thread_entry_exit_notify
tx_thread_info_get tx_thread_resume
tx_thread_performance_info_get
tx_thread_performance_system_info_get
tx_thread_stack_error_notify tx_thread_wait_abort tx_time_get
tx_time_set tx_timer_activate tx_timer_change
tx_timer_deactivate tx_timer_info_get
tx_timer_performance_info_get
tx_timer_performance_system_info_get
```

> [!IMPORTANT]
> *Wstrzymanie jest niedozwolone od isR. Dlatego parametr **wait_option** dla wszystkich wywołań usługi ThreadX wykonanych z isr musi być ustawiony na **TX_NO_WAIT**.*

### <a name="isr-template"></a>Szablon ISR

Aby zarządzać przerwań aplikacji, na początku i na końcu serwerów ISR aplikacji należy wywołać kilka narzędzi ThreadX. Dokładny format obsługi przerwań różni się między portami.

Następujący mały segment kodu jest typowy dla większości zarządzanych serwerów ISR ThreadX. W większości przypadków to przetwarzanie odbywa się w języku zestawu.

```c
_application_ISR_vector_entry:

; Save context and prepare for

; ThreadX use by calling the ISR

; entry function.

CALL _tx_thread_context_save

; The ISR can now call ThreadX

; services and its own C functions

; When the ISR is finished, context

; is restored (or thread preemption)

; by calling the context restore ; function. Control does not return!

JUMP _tx_thread_context_restore
```

### <a name="high-frequency-interrupts"></a>Przerwań o wysokiej częstotliwości

Niektóre przerwania występują z taką wysoką częstotliwością, że zapisanie i przywrócenie pełnego kontekstu po każdym przerwaniu będzie zużywać nadmierną przepustowość przetwarzania. W takich przypadkach często aplikacja ma niewielki zestawowy język ISR, który w przypadku większości tych przerwań o wysokiej częstotliwości przetwarza ograniczoną ilość danych.

Po pewnym czasie mały isr może wymagać interakcji z ThreadX. Jest to realizowane przez wywołanie funkcji wejścia i wyjścia opisanych w powyższym szablonie.

### <a name="interrupt-latency"></a>Opóźnienie przerwań

ThreadX blokuje przerwania w krótkich okresach czasu. Maksymalny czas wyłączenia przerwań zależy od czasu wymaganego do zapisania lub przywrócenia kontekstu wątku.
