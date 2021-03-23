---
title: Rozdział 3 — funkcjonalne składniki platformy Azure RTO ThreadX
description: Ten rozdział zawiera opis RTO jądra ThreadX o wysokiej wydajności z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: aa66ad392171958e5d2cc765992fd1a9e41250a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823275"
---
# <a name="chapter-3---functional-components-of-azure-rtos-threadx"></a>Rozdział 3 — funkcjonalne składniki platformy Azure RTO ThreadX

Ten rozdział zawiera opis RTO jądra ThreadX o wysokiej wydajności z perspektywy funkcjonalnej. Każdy składnik funkcjonalny jest prezentowany w zrozumiały sposób.

## <a name="execution-overview"></a>Przegląd wykonywania

Istnieją cztery typy wykonywania programu w ramach aplikacji ThreadX: Inicjowanie, wykonywanie wątków, procedury usługi przerwania (procedury ISR) i czasomierze aplikacji.

Rysunek 2 przedstawia każdy inny typ wykonywania programu. Bardziej szczegółowe informacje na temat każdego z tych typów znajdują się w kolejnych sekcjach tego rozdziału.

### <a name="initialization"></a>Inicjalizacja

Jak nazywa się, jest to pierwszy typ wykonywania programu w aplikacji ThreadX. Inicjalizacja obejmuje wykonywanie wszystkich programów między resetowaniem procesora i punktem wejścia *pętli planowania wątku.*

### <a name="thread-execution"></a>Wykonywanie wątku

Po zakończeniu inicjalizacji ThreadX wprowadza swoją pętlę planowania wątków. Pętla planowania wyszukuje wątek aplikacji gotowy do wykonania. Po znalezieniu gotowego wątku ThreadX przenosi do niego kontrolkę. Po zakończeniu wątku (lub przeniesieniu innego wątku wyższego priorytetu) wykonywanie jest wykonywane z powrotem do pętli planowania wątku, aby znaleźć wątek gotowy do następnego priorytetu.

Proces ciągłego wykonywania i planowania wątków jest najpopularniejszym typem wykonywania programów w aplikacjach ThreadX.

### <a name="interrupt-service-routines-isr"></a>Procedury usługi przerwania (ISR)

Przerwania są podstawą systemów w czasie rzeczywistym. Bez przeszkód bardzo trudne jest reagowanie na zmiany w świecie zewnętrznym w odpowiednim czasie. W przypadku wykrywania przerwania procesor zapisuje kluczowe informacje o bieżącym wykonaniu programu (zwykle na stosie), a następnie przenosi formant do obszaru wstępnie zdefiniowanego programu. Ten wstępnie zdefiniowany obszar programu jest często nazywany procedurą usługi przerwania. W większości przypadków przerwania występują podczas wykonywania wątku (lub w pętli planowania wątku). Przerwania mogą jednak wystąpić w trakcie wykonywania procedury ISR lub czasomierza aplikacji.

![Typy wykonywania programu](./media/user-guide/types-program-execution.png)

**RYSUNEK 2. Typy wykonywania programu**

### <a name="application-timers"></a>Czasomierze aplikacji

Czasomierze aplikacji są podobne do procedury ISR, z wyjątkiem tego, że implementacja sprzętowa (zazwyczaj jest używany pojedynczy okresowe przerwanie sprzętowe) jest ukryta w aplikacji. Takie czasomierze są używane przez aplikacje do wykonywania limitów czasu, okresowych i/lub usług alarmowych. Podobnie jak procedury ISR, czasomierze aplikacji najczęściej przerywają wykonywanie wątków. W przeciwieństwie do procedury ISR, jednak czasomierze aplikacji nie mogą przerwać siebie nawzajem.

## <a name="memory-usage"></a>Użycie pamięci

ThreadX się wraz z programem aplikacji. W związku z tym użycie pamięci statycznej (lub stałej pamięci) ThreadX jest określane przez narzędzia programistyczne. na przykład kompilator, konsolidator i lokalizator. Użycie pamięci dynamicznej (lub pamięci w czasie wykonywania) jest kontrolowane bezpośrednio przez aplikację.

### <a name="static-memory-usage"></a>Użycie pamięci statycznej

Większość narzędzi programistycznych dzieli obraz programu aplikacji na pięć podstawowych obszarów: *instrukcje*, *stałe*, *zainicjowane dane*, *niezainicjowane dane* i *stos systemu*. Rysunek 3 przedstawia przykład tych obszarów pamięci.

Ważne jest, aby zrozumieć, że jest to tylko przykład. Rzeczywisty układ pamięci statycznej jest specyficzny dla procesora, narzędzi programistycznych i bazowego sprzętu.

Obszar instrukcji zawiera wszystkie instrukcje procesora programu. Ten obszar jest zwykle największą i często znajduje się w pamięci ROM.

Obszar stałych zawiera różne skompilowane stałe, w tym ciągi zdefiniowane lub przywoływane w programie. Ponadto ten obszar zawiera "początkową kopię" zainicjowanego obszaru danych. W trakcie procesu inicjowania kompilatora *użycia pamięci* ta część obszaru stałego służy do konfigurowania zainicjowanego obszaru danych w pamięci RAM. Obszar stałych zwykle jest zgodny z obszarem instrukcji i często znajduje się w pamięci ROM.

Zainicjowane dane i niezainicjowane obszary danych zawierają wszystkie zmienne globalne i statyczne. Obszary te są zawsze zlokalizowane w pamięci RAM.

Stos systemowy jest zwykle ustawiany bezpośrednio po zainicjowaniu i niezainicjowanym obszarze danych.

Stos systemu jest używany przez kompilator podczas inicjacji, a następnie przez ThreadX podczas inicjowania, a następnie w przypadku przetwarzania w procesie ISR.

![Przykład obszaru pamięci](./media/user-guide/memory-area-example.png)

**RYSUNEK 3. Przykład obszaru pamięci**

### <a name="dynamic-memory-usage"></a>Użycie pamięć dynamiczna

Jak wspomniano wcześniej, użycie pamięci dynamicznej jest kontrolowane bezpośrednio przez aplikację. Bloki kontroli i obszary pamięci skojarzone z stosami, kolejkami i pulami pamięci można umieścić w dowolnym miejscu w obszarze pamięci docelowej. Jest to ważna funkcja, ponieważ ułatwia ona łatwe wykorzystanie różnych typów pamięci fizycznej.

Załóżmy na przykład, że w docelowym środowisku sprzętowym występuje szybka pamięć i wolna pamięć. Jeśli aplikacja wymaga dodatkowej wydajności dla wątku o wysokim priorytecie, jego blok sterowania (TX_THREAD) i stos można umieścić w obszarze szybkiej pamięci, co może znacząco wzmocnić jego wydajność.

## <a name="initialization"></a>Inicjalizacja

Zrozumienie procesu inicjowania jest ważne. Początkowe środowisko sprzętowe jest skonfigurowane w tym miejscu. Ponadto jest to miejsce, w którym aplikacja ma swoją wstępną osobowość.

> [!NOTE]
> *ThreadX próbuje użyć (o ile to możliwe) kompletnego procesu inicjowania narzędzia deweloperskiego. Dzięki temu można łatwiej uaktualniać do nowych wersji narzędzi programistycznych w przyszłości.*

### <a name="system-reset-vector"></a>Wektor resetowania systemu

Wszystkie mikroprocesory mają logikę resetowania. W przypadku wyzerowania (sprzętowego lub programowego) adres punktu wejścia aplikacji jest pobierany z określonej lokalizacji pamięci. Po pobraniu punktu wejścia procesor przetransferuje kontrolkę do tej lokalizacji. Punkt wejścia aplikacji jest bardzo często pisany w natywnym języku asemblera i jest zwykle dostarczany przez narzędzia programistyczne (co najmniej w formularzu szablonu). W niektórych przypadkach specjalna wersja programu wprowadzania jest dostarczana z ThreadX.

### <a name="development-tool-initialization"></a>Inicjowanie narzędzia programistycznego

Po zakończeniu inicjalizacji niskiego poziomu należy kontrolować transfery do inicjalizacji wysokiego poziomu narzędzia deweloperskiego. Zwykle jest to miejsce, w którym są skonfigurowane zmienne globalne i statyczne języka C. Należy pamiętać, że ich początkowe wartości są pobierane z obszaru stałego. Dokładne przetwarzanie inicjowania jest specyficzne dla narzędzia deweloperskiego.

### <a name="main-function"></a>Funkcja Main

Po zakończeniu inicjowania narzędzia deweloperskiego należy kontrolować transfery do funkcji *głównej* dostarczonej przez użytkownika. W tym momencie aplikacja kontroluje, co się stanie dalej. W przypadku większości aplikacji funkcja Main po prostu wywołuje *tx_kernel_enter*, który jest wpisem do ThreadX. Jednak aplikacje mogą wykonać wstępne przetwarzanie (zwykle w przypadku inicjowania sprzętowego) przed wprowadzeniem ThreadX.

> [!IMPORTANT]
> *Wywołanie tx_kernel_enter nie zwraca, dlatego nie należy umieszczać żadnego przetwarzania po nim.*

### <a name="tx_kernel_enter"></a>tx_kernel_enter

Funkcja wejścia koordynuje inicjalizację różnych wewnętrznych struktur danych ThreadX, a następnie wywołuje funkcję definicji aplikacji ***tx_application_define***.

Gdy ***tx_application_define*** zwraca, kontrola jest przekazywana do pętli planowania wątku. Oznacza to koniec inicjalizacji.

### <a name="application-definition-function"></a>Funkcja definicji aplikacji

Funkcja ***tx_application_define*** definiuje wszystkie początkowe wątki aplikacji, kolejki, semafory, muteksy, flagi zdarzeń, Pule pamięci i czasomierze. Istnieje również możliwość tworzenia i usuwania zasobów systemowych z wątków podczas normalnego działania aplikacji. Wszystkie początkowe zasoby aplikacji są jednak zdefiniowane w tym miejscu.

Funkcja ***tx_application_define** _ ma jeden parametr wejściowy, a jego wartość różni się od siebie. Adres pamięci RAM _first dostępny * jest jedynym parametrem wejściowym tej funkcji. Jest zazwyczaj używany jako punkt wyjścia dla początkowych alokacji pamięci w czasie wykonywania dla stosów wątków, kolejek i pul pamięci.

> [!NOTE]
> *Po zakończeniu inicjalizacji tylko wątek wykonawczy może tworzyć i usuwać zasoby systemowe, w tym inne wątki. W związku z tym należy utworzyć co najmniej jeden wątek podczas inicjalizacji.*

### <a name="interrupts"></a>Przerwań

Przerwania są pozostawiane wyłączone podczas całego procesu inicjowania. Jeśli aplikacja w dowolny sposób włącza przerwania, może wystąpić nieprzewidywalne zachowanie. Na rysunku 4 przedstawiono cały proces inicjalizacji od resetowania systemu przy użyciu inicjalizacji specyficznej dla aplikacji.

## <a name="thread-execution"></a>Wykonywanie wątku

Planowanie i wykonywanie wątków aplikacji jest najważniejszym działaniem ThreadX. Wątek jest zwykle definiowany jako segment częściowo niezależnego programu z dedykowanym przeznaczeniem. Połączone przetwarzanie wszystkich wątków tworzy aplikację.

Wątki są tworzone dynamicznie przez wywołanie ***tx_thread_create** _ podczas inicjowania lub podczas wykonywania wątku. Wątki są tworzone w stanie _ready * lub *wstrzymania* .

![Proces inicjalizacji](./media/user-guide/initialization-process.png)

**RYSUNEK 4. Proces inicjalizacji**

### <a name="thread-execution-states"></a>Stany wykonywania wątków

Zrozumienie różnych stanów przetwarzania wątków jest kluczowym elementem opisującym całe środowisko wielowątkowości. W programie ThreadX istnieje pięć odrębnych Stanów wątków: *gotowy*, *zawieszony*, *wykonywany*, *zakończony* i *zakończony.* Rysunek 5 przedstawia diagram przejścia stanu wątku dla ThreadX.

![Przejście stanu wątku](./media/user-guide/thread-state-transition.png)

**RYSUNEK 5. Przejście stanu wątku**

Wątek jest w stanie *gotowości* , gdy jest gotowy do wykonania. Wątek gotowy nie jest wykonywany, dopóki nie jest to wątek o najwyższym priorytecie w stanie gotowe. Gdy tak się stanie, ThreadX wykonuje wątek, a następnie zmienia jego stan na *wykonywanie*.

Jeśli wątek o wyższym priorytecie stanie się gotowy, wątek wykonawczy powróci do stanu *gotowości* . Nowo przygotowany wątek o wysokim priorytecie jest następnie wykonywany, co powoduje zmianę jego stanu logicznego na *wykonanie*. To przejście między Stanami *gotowe* i *wykonawcze* odbywa się za każdym razem, gdy wystąpi zastępujący wątek.

W danym momencie tylko jeden wątek jest w stanie *wykonywania* . Dzieje się tak, ponieważ wątek w stanie *wykonywania* ma kontrolę nad podstawowym procesorem.

Wątki w stanie *wstrzymania* nie kwalifikują się do wykonania. Przyczyny *wstrzymania* w stanie zawieszenia obejmują zawieszenie czasu, komunikatów w kolejce, semaforów, muteksów, flag zdarzeń, pamięci i zawieszenia wątku podstawowego. Po usunięciu przyczyny zawieszenia wątek zostanie umieszczony w stanie *gotowości* .

Wątek w stanie *ukończone* jest wątkiem, który ukończył przetwarzanie i zwraca z funkcji wejścia. Funkcja wprowadzania jest określana podczas tworzenia wątku. Wątek w stanie *ukończenia* nie może zostać ponownie wykonany.

Wątek jest w stanie *przerwania* , ponieważ inny wątek lub sam wątek o nazwie Usługa *tx_thread_terminate* . Wątek w stanie *przerwania* nie może zostać ponownie wykonany.

> [!IMPORTANT]
> *Jeśli pożądane jest ponowne uruchomienie wątku zakończony lub zakończony, aplikacja musi najpierw usunąć wątek. Następnie można go ponownie utworzyć i ponownie uruchomić.*

### <a name="thread-entryexit-notification"></a>Powiadomienie o wejściu/wyjściu wątku

Niektóre aplikacje mogą otrzymywać powiadomienia, gdy określony wątek zostanie wprowadzony po raz pierwszy, po jego zakończeniu lub zostanie zakończony. ThreadX zapewnia tę możliwość za pomocą usługi ***tx_thread_entry_exit_notify*** . Ta usługa rejestruje funkcję powiadamiania aplikacji dla określonego wątku, który jest wywoływany przez ThreadX za każdym razem, gdy wątek zacznie działać, kończy lub zostaje zakończony. Po wywołaniu Funkcja powiadomień aplikacji może wykonać przetwarzanie specyficzne dla aplikacji. Zwykle polega to na poinformowaniu innego wątku aplikacji za pośrednictwem elementu podstawowego synchronizacji ThreadX.

### <a name="thread-priorities"></a>Priorytety wątków

Jak wspomniano wcześniej, wątek jest niezależnym segmentem programu z dedykowanym przeznaczeniem. Jednak wszystkie wątki nie są tworzone jako równe! Dedykowany cel niektórych wątków jest znacznie ważniejszy niż inne. Ten heterogeniczny typ ważności wątków to Hallmark osadzonych aplikacji w czasie rzeczywistym.

ThreadX określa ważność wątku, gdy tworzony jest wątek przez przypisanie wartości liczbowej reprezentującej jej *priorytet*. Maksymalna liczba priorytetów ThreadX można konfigurować z 32 do 1024 w przyrostach wynoszących 32. Rzeczywista Maksymalna liczba priorytetów jest określana na podstawie stałej **TX_MAX_PRIORITIES** podczas kompilowania biblioteki ThreadX. Posiadanie większej liczby priorytetów nie powoduje znacznego zwiększenia obciążenia związanego z przetwarzaniem. Jednak dla każdej grupy poziomów priorytetów 32 do zarządzania nimi jest wymagane dodatkowe 128 bajtów pamięci RAM. Na przykład 32 poziomów priorytetów wymaga 128 bajtów pamięci RAM, 64 poziomy priorytetu wymagają 256 bajtów pamięci RAM, a poziom priorytetu 96 wymaga 384 bajtów pamięci RAM.

Domyślnie ThreadX ma 32 poziomów priorytetów, od priorytetu od 0 do 31. Mniejsze wartości liczbowe oznaczają wyższy priorytet. W związku z tym priorytet 0 reprezentuje najwyższy priorytet, a priorytet (**TX_MAX_PRIORITIES**-1) reprezentuje najniższy priorytet.

Wiele wątków może mieć ten sam priorytet polegający na planowaniu współdziałania lub wycinku czasu. Ponadto priorytety wątków można zmieniać w czasie wykonywania.

### <a name="thread-scheduling"></a>Planowanie wątków

ThreadX planuje wątki na podstawie ich priorytetu. Wątek gotowy z najwyższym priorytetem jest wykonywany jako pierwszy. Jeśli jest gotowych wiele wątków o takim samym priorytecie, są one wykonywane w sposób *pierwszy-pierwszy-wyewidencjonowany* (FIFO).

### <a name="round-robin-scheduling"></a>Planowanie okrężne

ThreadX obsługuje *Planowanie okrężne* wielu wątków mających taki sam priorytet. Jest to realizowane poprzez wywołania wspólne do ***tx_thread_relinquish** _. Ta usługa udostępnia wszystkie inne gotowe wątki o takim samym priorytecie, które można wykonać przed ponownym uruchomieniem programu _ *_tx_thread_relinquish_**.

### <a name="time-slicing"></a>Time-Slicing

*Cięcie czasu* jest kolejną formą planowania działania okrężnego. Wycinek czasu określa maksymalną liczbę taktów czasomierza (przerwań czasomierza), którą wątek można wykonać bez podawania procesora. W ThreadX skalowanie czasu jest dostępne dla każdego wątku. Wycinek czasu wątku jest przypisywany podczas tworzenia i może być modyfikowany w czasie wykonywania. Gdy wycinek czasu wygaśnie, wszystkie inne gotowe wątki o tym samym poziomie priorytetu otrzymają szansę wykonania przed ponownym uruchomieniem wątku.

Po zawieszeniu, że wycinek jest odświeżany przez cały wątek, zwalnia, sprawia, że wywołanie usługi ThreadX powoduje zastępujące lub sama jest wycinkiem.

Po przeniesieniu wątku z podziałem czasowym zostanie ono wznowione przed innymi gotowe wątki o równym priorytecie dla pozostałej części czasu.

> [!NOTE]
> *Korzystanie z wycinków czasu powoduje niewielkie obciążenie systemu. Ponieważ podział czasu jest przydatny tylko w przypadkach, w których wiele wątków ma ten sam priorytet, w wątkach mających unikatowy priorytet nie należy przypisywać wycinków czasu.*

### <a name="preemption"></a>Wywłaszczania

Zastępujący jest procesem tymczasowego przerwania wykonywania wątku na rzecz wątku o wyższym priorytecie. Ten proces jest niewidoczny dla wątku wykonawczego. Po zakończeniu wątku o wyższym priorytecie kontrola jest przekazywana z powrotem do dokładnego miejsca, w którym nastąpiło przemieszczenie. Jest to bardzo ważna funkcja w systemach w czasie rzeczywistym, ponieważ ułatwia ona szybkie reagowanie na ważne zdarzenia aplikacji. Mimo że jest to bardzo ważna funkcja, zastępujący może być również źródłem różnych problemów, w tym przeciążania, nadmiernego obciążenia i niewersjami priorytetów.

### <a name="preemption-thresholdtrade"></a>Próg przekroczenia&trade;

Aby uprościć niektóre z nietypowych problemów związanych z zastępując, ThreadX zapewnia unikatową i zaawansowaną funkcję o nazwie *próg* przekroczenia.

Próg przekroczenia umożliwia wątek określający *priorytet dla* wyłączenia zastępujący. Wątki, które mają wyższe priorytety niż limit, nadal mogą być przełożone, podczas gdy nie mogą być przełożone na mniejsze niż górny limit.

Załóżmy na przykład, że wątek o priorytecie 20 współdziała tylko z grupą wątków o priorytetach od 15 do 20. W jej sekcjach krytycznych wątek o priorytecie 20 może ustawić jego próg przekroczenia na 15, uniemożliwiając tym samym przepełnianie ze wszystkich wątków, z którymi się komunikują. Nadal pozwala to na naprawdę ważne wątki (od 0 do 14), aby przewyższyć ten wątek podczas przetwarzania sekcji krytycznej, co skutkuje znacznie większą szybkością przetwarzania.

Oczywiście nadal jest możliwe, aby wątek wyłączył wszystkie przekroczenia przez ustawienie jego progu zastępujące na 0. Dodatkowo można zmienić próg zastępujący w czasie wykonywania.

> [!NOTE]
> *Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.*

### <a name="priority-inheritance"></a>Dziedziczenie priorytetów

ThreadX również obsługuje dziedziczenie opcjonalnego priorytetu w ramach usług muteksów opisanych w dalszej części tego rozdziału. Dziedziczenie priorytetowe umożliwia wątek o niższym priorytecie w celu tymczasowego założenia priorytetu wątku wysokiego priorytetu, który oczekuje na element mutex należący do wątku o niższym priorytecie. Ta funkcja ułatwia aplikacji uniknięcie niedeterministycznych priorytetów, eliminując zastępujące priorytety wątku pośredniego. Oczywiście *próg zastępujący* może być używany do osiągnięcia podobnego wyniku.

### <a name="thread-creation"></a>Tworzenie wątku

Wątki aplikacji są tworzone podczas inicjowania lub podczas wykonywania innych wątków aplikacji. Nie ma żadnego limitu liczby wątków, które mogą zostać utworzone przez aplikację.

### <a name="thread-control-block-tx_thread"></a>TX_THREAD bloku sterowania wątku

Charakterystyki każdego wątku są zawarte w jego bloku sterowania. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Blok sterowania wątku może znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

Lokalizowanie bloku sterowania w innych obszarach wymaga nieco więcej informacji, podobnie jak wszystkie dynamicznie przydzieloną pamięć. Jeśli blok sterowania jest przypisywany w ramach funkcji języka C, skojarzona z nim pamięć jest częścią stosu wywołującego wątku. Ogólnie rzecz biorąc, Unikaj używania lokalnego magazynu dla bloków kontroli, ponieważ po powrocie funkcji jest wydawana cała jego przestrzeń stosów zmiennych lokalnych, niezależnie od tego, czy inny wątek używa go dla bloku sterowania.

W większości przypadków aplikacja jest Oblivious do zawartości bloku sterowania wątku. Istnieją jednak sytuacje, szczególnie podczas debugowania, które są przydatne w przypadku niektórych elementów członkowskich. Poniżej przedstawiono niektóre z bardziej przydatnych elementów członkowskich bloku sterowania.

**tx_thread_run_count** zawiera Licznik liczby wystąpień wątku, który został zaplanowany. Rosnący licznik wskazuje, że wątek jest zaplanowany i wykonywany.

**tx_thread_state** zawiera stan skojarzonego wątku. Poniżej wymieniono możliwe stany wątków.

|  Stan wątku   | Wartość |
| --------------- | ------ |
| TX_READY       | 0x00 |
| TX_COMPLETED   | 0x01 |
| TX_TERMINATED  | 0x02 |
| TX_SUSPENDED   | (0x03) |
| TX_SLEEP       | (0x04) |
| TX_QUEUE_SUSP | (0x05) |
| TX_SEMAPHORE_SUSP | (0x06) |
| TX_EVENT_FLAG   | (0x07) |
| TX_BLOCK_MEMORY | (0x08) |
| TX_BYTE_MEMORY  | 0x09 |
| TX_MUTEX_SUSP   | 0x0D |

> [!NOTE]
> *Oczywiście istnieje wiele innych interesujących pól w bloku sterowania wątku, w tym Wskaźnik stosu, wartość wycinka czasu, priorytety itp. Użytkownicy mogą przeglądać elementy członkowskie bloku kontrolki, ale modyfikacje są absolutnie zabronione.*

> [!IMPORTANT]
> *Nie ma żadnego elementu równego dla stanu "Executing" wymienionego wcześniej w tej sekcji. Nie jest to konieczne, ponieważ w danym momencie istnieje tylko jeden wykonywany wątek. Stan wątku wykonywania jest również* **TX_READY**.

### <a name="currently-executing-thread"></a>Aktualnie wykonywany wątek

Jak wspomniano wcześniej, w danym momencie jest wykonywany tylko jeden wątek. Istnieje kilka sposobów identyfikacji wątku wykonującego, w zależności od tego, który wątek wykonuje żądanie.
Segment programu może uzyskać adres bloku sterowania wykonywanego wątku przez wywołanie ***tx_thread_identify***. Jest to przydatne w przypadku udostępnionych części kodu aplikacji, które są wykonywane z wielu wątków.

W sesji debugowania użytkownicy mogą przeanalizować wewnętrzny wskaźnik ThreadX ***_tx_thread_current_ptr***. Zawiera adres bloku kontroli aktualnie wykonywanego wątku. Jeśli ten wskaźnik ma wartość NULL, żaden wątek aplikacji nie jest wykonywany; oznacza to, że ThreadX oczekuje w pętli planowania, aby wątek stał się gotowy.

### <a name="thread-stack-area"></a>Obszar stosu wątków

Każdy wątek musi mieć własny stos do zapisywania kontekstu ostatniego wykonywania i użycia kompilatora. Większość kompilatorów języka C używa stosu do tworzenia wywołań funkcji i tymczasowej alokacji zmiennych lokalnych. Rysunek 6 przedstawia stos typowego wątku.

Miejsce, w którym stos wątków znajduje się w pamięci, jest do aplikacji. Obszar stosu jest określany podczas tworzenia wątku i może znajdować się w dowolnym miejscu w przestrzeni adresowej docelowej. Jest to ważna funkcja, ponieważ umożliwia aplikacjom Ulepszanie wydajności ważnych wątków przez umieszczenie ich stosu w dużej szybkości pamięci RAM.

**Obszar pamięci stosu** (przykład)

![Typowy stos wątków](./media/user-guide/typical-thread-stack.png)

**RYSUNEK 6. Typowy stos wątków**

Jak duży stos powinien być jednym z najczęściej zadawanych pytań dotyczących wątków. Obszar stosu wątku musi być wystarczająco duży, aby pomieścić najgorsze wywołanie funkcji, alokację zmiennej lokalnej i zapisanie jej ostatniego kontekstu wykonania.

Minimalny rozmiar stosu, **TX_MINIMUM_STACK**, jest definiowany przez ThreadX. Stos tego rozmiaru obsługuje zapisywanie kontekstu wątku i minimalnej liczby wywołań funkcji i alokacji zmiennych lokalnych.

W przypadku większości wątków jednak minimalny rozmiar stosu jest zbyt mały, a użytkownik musi upewnić się, że wymaganie rozmiaru najgorszej wielkości liter poprzez sprawdzenie zagnieżdżenia wywołań funkcji i alokacji zmiennych lokalnych. Oczywiście lepiej jest zacząć od większego obszaru stosu.

Po debugowaniu aplikacji można dostosować rozmiary stosu wątków, jeśli ilość pamięci jest nietrwała. Ulubioną lewę jest to, aby ustawić wszystkie obszary stosu z łatwym do zidentyfikowania wzorcem danych, takim jak (0xEFEF) przed utworzeniem wątków. Po dokładnym umieszczeniu aplikacji przez tępy obszary stosu można sprawdzić, aby zobaczyć, jak dużo stosu zostało faktycznie zużyte przez znalezienie obszaru stosu, w którym wzorzec danych jest wciąż nienaruszony. Rysunek 7 przedstawia ustawienia wstępne stosu 0xEFEF po dokładnym wykonaniu wątku.

**Obszar pamięci stosu** (inny przykład)

![Ustawienia wstępne stosu do 0xEFEF *](./media/user-guide/stack-preset.png)

**RYSUNEK 7. Ustawienia wstępne stosu do 0xEFEF**

> [!IMPORTANT]
> *Domyślnie ThreadX inicjuje każdy bajt każdego stosu wątku z wartością 0xEF.*

### <a name="memory-pitfalls"></a>Pułapek pamięci

Wymagania dotyczące stosu dla wątków mogą być duże. W związku z tym ważne jest, aby zaprojektować aplikację w celu uzyskania odpowiedniej liczby wątków. Ponadto należy podjąć pewne czynności, aby uniknąć nadmiernego użycia stosu w wątkach. Należy unikać stosowania algorytmów cyklicznych i dużych lokalnych struktur danych.

W większości przypadków nadmiarowy stos sprawia, że wykonanie wątku powoduje uszkodzenie pamięci sąsiedniej (zwykle przed) jej obszaru stosu. Wyniki są nieprzewidywalne, ale większość często powoduje nienaturalną zmianę w liczniku programu. Jest to często nazywane "przechodzeniem do chwastów". Oczywiście jedynym sposobem na uniknięcie tego jest upewnienie się, że wszystkie stosy wątków są wystarczająco duże.

### <a name="optional-run-time-stack-checking"></a>Opcjonalne sprawdzanie stosu czasu wykonywania

ThreadX zapewnia możliwość sprawdzania stosu każdego wątku w celu uszkodzenia w czasie wykonywania. Domyślnie ThreadX wypełnia każdy bajt stosów wątków przy użyciu wzorca danych 0xEF podczas tworzenia. Jeśli aplikacja kompiluje bibliotekę ThreadX z definicją **TX_ENABLE_STACK_CHECKING** , ThreadX będzie przeanalizować stos każdego wątku pod kątem uszkodzenia w miarę jego wstrzymania lub wznowienia. Jeśli wykryto uszkodzenie stosu, ThreadX wywoła procedurę obsługi błędów stosu aplikacji określoną przez wywołanie do **_tx_thread_stack_error_notify_*_. W przeciwnym razie, jeśli nie określono żadnej procedury obsługi błędów stosu, ThreadX wywoła procedurę wewnętrzną _* _ _tx_thread_stack_error_handler_** .

### <a name="reentrancy"></a>Ponowne wejścia

Jednym z prawdziwych Beauties wielowątkowości jest to, że ta sama funkcja języka C może być wywoływana z wielu wątków. Zapewnia to doskonałe możliwości, a także pomaga zmniejszyć ilość miejsca w kodzie. Jednak wymaga to, aby funkcje języka C wywoływane z wielu wątków były *współużytkowane*.

Zasadniczo funkcja współużytkowania przechowuje adres zwrotny obiektu wywołującego na bieżącym stosie i nie bazuje na globalnych lub statycznych zmiennych języka C, które wcześniej zostały skonfigurowane. Większość kompilatorów umieszcza adres zwrotny na stosie. W związku z tym deweloperzy aplikacji mogą martwić się o użycie *Globals* i elementów *statycznych*.

Przykładem funkcji, która nie jest współużytkowana, jest funkcja tokenu ciągu ***strtok*** znaleziona w standardowej bibliotece C. Ta funkcja "zapamiętuje" poprzedni wskaźnik ciągu dla kolejnych wywołań. Robi to ze statycznym wskaźnikiem ciągu. Jeśli ta funkcja jest wywoływana z wielu wątków, prawdopodobnie zwróci nieprawidłowy wskaźnik.

### <a name="thread-priority-pitfalls"></a>Priorytet wątku pułapek

Wybór priorytetów wątków jest jednym z najważniejszych aspektów wielowątkowości. Czasami bardzo zachęca się do przypisywania priorytetów na podstawie postrzeganych koncepcji o znaczeniu wątku zamiast określania, co jest dokładnie wymagane w czasie wykonywania. Nieprawidłowe użycie priorytetów wątków może zablokować dostęp inne wątki, utworzyć niewersję priorytetu, zmniejszyć przepustowość przetwarzania i sprawić, że zachowanie w czasie wykonywania aplikacji jest trudne do zrozumienia.

Jak wspomniano wcześniej, ThreadX zapewnia oparty na priorytetach algorytm planowania z przeznaczeniem. Wątki o niższym priorytecie nie są wykonywane, dopóki nie są gotowe do wykonania żadne wątki o wyższym priorytecie. Jeśli wątek o wyższym priorytecie zawsze jest gotowy, wątki o niższym priorytecie nigdy nie są wykonywane. Ten warunek jest nazywany *przetrzymaniem wątku*.

Większość problemów z zablokowanie wątków jest wykrywanych wczesnie w debugowaniu i można je rozwiązać przez zapewnienie, że priorytety o wyższym priorytecie nie są stale wykonywane. Alternatywnie można dodać logikę do aplikacji, która stopniowo podnosi priorytet wątków Starved do momentu uzyskania szansy do wykonania.

Inna Pitfall skojarzona z priorytetami wątków jest w *wersji priorytetowej*. Priorytetowa wersja ma miejsce, gdy wątek o wyższym priorytecie jest zawieszony, ponieważ wątek o niższym priorytecie ma wymagany zasób. Oczywiście w niektórych przypadkach jest konieczne, aby dwa wątki o różnym priorytecie współdzielą wspólne zasoby. Jeśli te wątki są jedynymi aktywnymi, czas niewersji priorytetu jest ograniczany przez czas, w którym wątek niższego priorytetu utrzymuje zasób. Ten warunek jest deterministyczny i całkiem normalny. Jeśli jednak wątki o priorytecie pośrednim staną się aktywne w stanie niewersji priorytetu, czas braku wersji nie jest już deterministyczny i może spowodować błąd aplikacji.

Istnieją głównie trzy różne metody uniemożliwiające niedeterministyczną wersję priorytetu w ThreadX. Najpierw wybór priorytetu aplikacji oraz zachowanie w czasie wykonywania mogą być zaprojektowane w sposób, który uniemożliwia problem z nieprawidłową wersją. Drugi, wątki o niższym priorytecie mogą korzystać z *progu* przekroczenia, aby blokować przekroczenie z wątków pośrednich, a współużytkują zasoby o wyższym priorytecie. Na koniec wątki korzystające z obiektów mutex ThreadX do ochrony zasobów systemowych mogą korzystać z opcjonalnego *dziedziczenia priorytetu* muteksu w celu wyeliminowania niedeterministycznej wersji priorytetu.

### <a name="priority-overhead"></a>Priorytetowe narzuty

Jednym z najczęstszych sposobów zmniejszenia obciążenia w wielowątkowości jest zmniejszenie liczby przełączeń kontekstu. Jak wspomniano wcześniej, przełącznik kontekstu występuje, gdy wykonywanie wątku o wyższym priorytecie jest preferowane przez wykonywany wątek. Należy zauważyć, że wątki o wyższym priorytecie mogą stać się gotowe jako wynik obu zdarzeń zewnętrznych (na przykład przerwań) i od wywołań usługi wykonanych przez wątek wykonujący.

W celu zilustrowania priorytetów wątków związanych z przełączaniem kontekstu należy założyć trzy środowiska wątku z wątkami o nazwie *thread_1*, *thread_2* i *thread_3*. Załóżmy, że wszystkie wątki w stanie zawieszania oczekują na komunikat. Gdy thread_1 otrzymuje komunikat, natychmiast przekaże go do thread_2. Następnie Thread_2 przekazuje komunikat do thread_3. Thread_3 po prostu odrzuca komunikat. Gdy każdy wątek przetwarza swój komunikat, wraca i czeka na kolejną wiadomość.

Przetwarzanie wymagane do wykonania tych trzech wątków różni się znacznie w zależności od ich priorytetów. Jeśli wszystkie wątki mają ten sam priorytet, przełączenie do jednego kontekstu następuje przed wykonaniem każdego wątku. Przełącznik kontekstu występuje, gdy każdy wątek zawiesza się w pustej kolejce komunikatów.

Jeśli jednak thread_2 ma wyższy priorytet niż thread_1, a thread_3 jest wyższym priorytetem niż thread_2, Liczba przełączeń kontekstu podwaja się. Jest to spowodowane tym, że inny przełącznik kontekstu występuje w ramach usługi *tx_queue_send* , gdy wykryje, że jest teraz gotowy wątek o wyższym priorytecie.

Mechanizm przekroczenia ThreadXu może uniknąć tych dodatkowych przełączników kontekstowych i nadal zezwalać na wcześniej wymienione priorytety. Jest to ważna funkcja, ponieważ pozwala ona na kilka priorytetów wątków podczas planowania, jednocześnie eliminując niektóre niechciane przełączanie kontekstu między nimi podczas wykonywania wątku.

### <a name="run-time-thread-performance-information"></a>Informacje o wydajności wątku czasu wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności wątku czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych **TX_THREAD_ENABLE_PERFORMANCE_INFO** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

  - wznowienia wątków

  - zawieszenie wątku

  - zastępujące wywołania usług

  - zastępujące przerwania

  - priorytetowe wersje

  - wycinki czasu

  - braki

  - limity czasu wątków

  - przerwania zawieszenia

  - bezczynne zwracanie systemu

  - bezczynne przywrócenie systemu

Łączna liczba dla każdego wątku:

  - Dzięki wznawianiu

  - zawieszeniach

  - zastępujące wywołania usług

  - zastępujące przerwania

  - priorytetowe wersje

  - wycinki czasu

  - zrzeczenia się wątków

  - limity czasu wątków

  - przerwania zawieszenia

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_thread_performance_info_get** _ i _ *_tx_thread_performance_system_info_get_* *. Informacje o wydajności wątków są przydatne podczas ustalania, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo wysoka liczba przeniesień wywołań usług może zasugerować priorytet wątku i/lub przekroczenie — próg jest zbyt niski. Ponadto stosunkowo niska liczba bezczynnych funkcji zwracanych przez system może sugerować, że wątki o niższym priorytecie nie są wystarczająco zawieszone.

### <a name="debugging-pitfalls"></a>Debugowanie pułapek

Debugowanie aplikacji wielowątkowych jest nieco trudniejsze, ponieważ ten sam kod programu może być wykonywany z wielu wątków. W takich przypadkach sama punkt przerwania może być niewystarczająca. Debuger musi również wyświetlać wskaźnik bieżącego wątku **_tx_thread_current_ptr** przy użyciu warunkowego punktu przerwania, aby sprawdzić, czy wywoływany wątek jest obiektem do debugowania.

Większość z nich jest obsługiwana w pakietach obsługi wielowątkowości oferowanych przez różnych dostawców narzędzi programistycznych. Ze względu na prosty projekt integrowanie ThreadX z różnymi narzędziami programistycznymi jest stosunkowo proste.

Rozmiar stosu jest zawsze ważnym tematem debugowania w wielowątkowości. Zawsze, gdy zaobserwowano niewyjaśnione zachowanie, zwykle jest to dobre pierwsze odgadnięcie w celu zwiększenia rozmiaru stosu dla wszystkich wątków — szczególnie rozmiaru stosu dla ostatniego wątku do wykonania.

> [!TIP]
> *Dobrym pomysłem jest również skompilowanie biblioteki ThreadX z definicją **TX_ENABLE_STACK_CHECKING** . Pomoże to w wyizolowaniu problemów z uszkodzeniem stosu tak wcześnie jak to możliwe.*

## <a name="message-queues"></a>Kolejki komunikatów

Kolejki komunikatów są podstawowym sposobem komunikacji między wątkami w ThreadX. Co najmniej jeden komunikat może znajdować się w kolejce komunikatów. Kolejka komunikatów, która przechowuje pojedynczy komunikat, jest zazwyczaj nazywana *skrzynką pocztową*.

Komunikaty są kopiowane do kolejki przez ***tx_queue_send** _ i kopiowane z kolejki przez _ *_tx_queue_receive_* *. Jedynym wyjątkiem jest zawieszenie wątku podczas oczekiwania na komunikat w pustej kolejce. W takim przypadku Następna wiadomość wysłana do kolejki zostanie umieszczona bezpośrednio w obszarze docelowym wątku.

Każda kolejka komunikatów jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń dotyczących sposobu używania kolejek komunikatów.

### <a name="creating-message-queues"></a>Tworzenie kolejek komunikatów

Kolejki komunikatów są tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. Nie ma limitu liczby kolejek komunikatów w aplikacji.

### <a name="message-size"></a>Rozmiar komunikatu

Każda kolejka komunikatów obsługuje wiele komunikatów o ustalonym rozmiarze. Dostępne rozmiary wiadomości to od 1 do 16 32-bitowych słów włącznie. Rozmiar komunikatu jest określany podczas tworzenia kolejki. Komunikaty aplikacji o więcej niż 16 wyrazach muszą być przesyłane przez wskaźnik. W tym celu można utworzyć kolejkę z rozmiarem komunikatu wynoszącym 1 wyraz (wystarczająco mały, aby pomieścić wskaźnik), a następnie wysyłać i odbierać wskaźniki komunikatów zamiast całego komunikatu.

### <a name="message-queue-capacity"></a>Pojemność kolejki komunikatów

Liczba komunikatów, które mogą być przechowywane w kolejce jest funkcją rozmiaru komunikatu oraz rozmiarem obszaru pamięci dostarczonego podczas tworzenia. Całkowita pojemność wiadomości w kolejce jest obliczana przez podzielenie liczby bajtów w poszczególnych komunikatach na całkowitą liczbę bajtów w podanym obszarze pamięci.

Na przykład, jeśli kolejka komunikatów obsługująca rozmiar komunikatu 1 32-bit (4 bajty) jest tworzona z obszarem pamięci 100 bajtów, jego pojemność to 25 komunikatów.

### <a name="queue-memory-area"></a>Obszar pamięci kolejki

Jak wspomniano wcześniej, obszar pamięci do buforowania komunikatów jest określany podczas tworzenia kolejki. Podobnie jak w przypadku innych obszarów pamięci w ThreadX, może ona znajdować się w dowolnym miejscu w przestrzeni adresowej docelowej.

Jest to ważna funkcja, ponieważ zapewnia znaczną elastyczność aplikacji. Na przykład aplikacja może zlokalizować obszar pamięci ważnej kolejki w pamięci RAM o dużej szybkości, aby zwiększyć wydajność.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać podczas próby wysłania lub odebrania komunikatu z kolejki. Zazwyczaj zawieszenie wątku obejmuje oczekiwanie na komunikat z pustej kolejki. Istnieje również możliwość zawieszenia przez wątek próby wysłania komunikatu do pełnej kolejki.

Po rozwiązaniu problemu z zawieszeniem żądana usługa zostanie zakończona, a wątek Oczekujący zostanie wznowiony. Jeśli wiele wątków jest zawieszonych w tej samej kolejce, zostaną wznowione w kolejności, w której zostały wstrzymane (FIFO).

Jednak możliwość wznowienia priorytetu jest również możliwa, jeśli aplikacja wywołuje ***tx_queue_prioritize*** przed usługą kolejki, która zawieszania wątku Wind. Usługa Queue priorytetyzacji usługi umieszcza wątek o najwyższym priorytecie na początku listy zawieszania, pozostawiając wszystkie pozostałe zawieszone wątki w tej samej kolejności FIFO.

Limity czasu są również dostępne dla wszystkich zawieszeń kolejki. W zasadzie limit czasu określa maksymalną liczbę cykli czasomierza, przez jaką wątek pozostanie zawieszony. W przypadku wystąpienia limitu czasu wątek zostaje wznowiony, a usługa zwraca odpowiedni kod błędu.

### <a name="queue-send-notification"></a>Powiadomienie o wysłaniu kolejki

Niektóre aplikacje mogą otrzymywać powiadomienia za każdym razem, gdy komunikat zostanie umieszczony w kolejce. ThreadX zapewnia tę możliwość za pomocą usługi ***tx_queue_send_notify*** . Ta usługa rejestruje podaną funkcję powiadamiania aplikacji z określoną kolejką. ThreadX następnie wywoła funkcję powiadamiania o tej aplikacji za każdym razem, gdy komunikat zostanie wysłany do kolejki. Dokładne przetwarzanie w ramach funkcji powiadomień aplikacji jest określane przez aplikację; jednak zwykle składa się z wznawiania odpowiedniego wątku w celu przetworzenia nowej wiadomości.

### <a name="queue-event-chainingtrade"></a>Tworzenie łańcucha zdarzeń kolejki&trade;

Funkcje powiadamiania w programie ThreadX mogą służyć do łańcucha różnych zdarzeń synchronizacji razem. Jest to zazwyczaj przydatne, gdy pojedynczy wątek musi przetwarzać wiele zdarzeń synchronizacji.

Załóżmy na przykład, że jeden wątek jest odpowiedzialny za przetwarzanie komunikatów z pięciu różnych kolejek i musi również zostać zawieszony, gdy nie są dostępne żadne komunikaty. Jest to łatwo realizowane przez zarejestrowanie funkcji powiadomień aplikacji dla każdej kolejki i wprowadzenie dodatkowego semafora zliczania. W odróżnieniu od tego, czy funkcja powiadamiania aplikacji wykonuje *tx_semaphore_put* przy każdym wywołaniu (liczba semaforów reprezentuje łączną liczbę komunikatów we wszystkich pięciu kolejkach). Wątek przetwarzania zawiesza się w tym semaforze za pośrednictwem usługi *tx_semaphore_get* . Gdy semafor jest dostępny (w tym przypadku, gdy komunikat jest dostępny!), wątek przetwarzania zostaje wznowiony. Następnie interrogates każdą kolejkę dla wiadomości, przetwarza znaleziony komunikat i wykonuje inne ***tx_semaphore_get*** , aby oczekiwać na następny komunikat. Ukończenie tego procesu bez łańcucha zdarzeń jest dość trudne i prawdopodobnie będzie wymagało większej liczby wątków i/lub dodatkowego kodu aplikacji.

Ogólnie rzecz biorąc, *łańcuch zdarzeń* powoduje zmniejszenie liczby wątków, mniejsze obciążenie i mniejsze wymagania dotyczące pamięci RAM. Zapewnia również wysoce elastyczny mechanizm obsługujący wymagania dotyczące synchronizacji bardziej złożonych systemów.

### <a name="run-time-queue-performance-information"></a>Informacje o wydajności kolejki czasu wykonywania
ThreadX zapewnia opcjonalne informacje o wydajności kolejki czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych ***TX_QUEUE_ENABLE_PERFORMANCE_INFO*** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

  - Wysłane komunikaty

  - odebrane komunikaty

  - zawieszanie pustych kolejek

  - pełne zawieszenie kolejki

  - błąd pełnej kolejki (zawieszenie nie zostało określone)

  - limity czasu kolejki

Łączna liczba dla każdej kolejki:

  - Wysłane komunikaty

  - odebrane komunikaty

  - zawieszanie pustych kolejek

  - pełne zawieszenie kolejki

  - błąd pełnej kolejki (zawieszenie nie zostało określone)

  - limity czasu kolejki

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_queue_performance_info_get** _ i _ *_tx_queue_performance_system_info_get_* *. Informacje o wydajności kolejki są przydatne podczas ustalania, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo wysoka liczba zawieszeń "queue fulls" sugeruje zwiększenie rozmiaru kolejki może być korzystne.

### <a name="queue-control-block-tx_queue"></a>Blok kontrolny kolejki TX_QUEUE

Charakterystyka każdej kolejki komunikatów znajduje się w jego bloku sterowania. Zawiera interesujące informacje, takie jak liczba komunikatów w kolejce. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Bloki sterujące kolejki komunikatów mogą również znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną przez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="message-destination-pitfall"></a>Pitfall miejsca docelowego wiadomości

Jak wspomniano wcześniej, komunikaty są kopiowane między obszarami kolejki i danymi aplikacji. Należy upewnić się, że miejsce docelowe odebranej wiadomości jest wystarczająco duże, aby pomieścić całą wiadomość. W przeciwnym razie pamięć następująca po miejscu docelowym wiadomości prawdopodobnie zostanie uszkodzona.

> [!NOTE]
> *Jest to szczególnie ważne, gdy na stosie znajduje się zbyt małe miejsce docelowe komunikatów — nic jak uszkodzenie adresu zwrotnego funkcji!*

## <a name="counting-semaphores"></a>Zliczanie semaforów

ThreadX zapewnia 32-bitowe semafory zliczania, które mają wartość z zakresu od 0 do 4 294 967 295. Istnieją dwie operacje zliczania semaforów: *tx_semaphore_get* i *tx_semaphore_put*. Operacja get zmniejsza semafor o jeden. Jeśli semafor ma wartość 0, operacja get nie powiedzie się. Odwrotność operacji pobierania jest operacją Put.
Zwiększa semafor o jeden.

Każdy semafor zliczania jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń dotyczących sposobu używania semaforów zliczania.

Licznik semaforów jest zwykle używany do *wzajemnego wykluczania*. Jednak zliczanie semaforów może być również używane jako metoda powiadamiania o zdarzeniach.

### <a name="mutual-exclusion"></a>Wzajemne wykluczenie

 Wzajemne wykluczenie dotyczy kontroli dostępu wątków do określonych obszarów aplikacji (nazywanych także *sekcjami krytycznymi* lub *zasobami aplikacji*). W przypadku użycia do wzajemnego wykluczania "Bieżąca liczba" semafora reprezentuje łączną liczbę wątków, które są dozwolone. W większości przypadków zliczanie semaforów używanych do wzajemnego wykluczania będzie miało wartość początkową 1, co oznacza, że tylko jeden wątek może uzyskać dostęp do skojarzonego zasobu w danym momencie. Zliczanie semaforów, które mają tylko wartości 0 lub 1, są zwykle nazywane *semaforami binarnymi*.

> [!IMPORTANT]
> *Jeśli jest używany semafor binarny, użytkownik musi uniemożliwić wykonanie operacji get przez ten sam wątek na semaforze, który jest już właścicielem. Druga wartość nie powiedzie się i może spowodować niepowodzenie zawieszenia wątku wywołującego i trwałej niedostępności zasobu.*

### <a name="event-notification"></a>Powiadomienie o zdarzeniu

Można również użyć zliczania semaforów jako powiadomienia o zdarzeniach, w sposób przeznaczony dla konsumentów. Odbiorca podejmuje próbę uzyskania semafora zliczania, gdy producent zwiększa semafor, gdy coś jest dostępne. Takie semafory zwykle mają wartość początkową 0 i nie zostaną zwiększone do momentu, gdy producent ma coś gotowego dla konsumenta. Semafory używane na potrzeby powiadomień o zdarzeniach mogą również korzystać z wywołania usługi ***tx_semaphore_ceiling_put*** . Ta usługa zapewnia, że liczba semaforów nigdy nie przekracza wartości podanej w wywołaniu.

### <a name="creating-counting-semaphores"></a>Tworzenie semaforów zliczania

Zliczanie semaforów jest tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. Początkowa liczba semaforów jest określana podczas tworzenia. Nie ma żadnego limitu liczby semaforów zliczania w aplikacji.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać podczas próby wykonania operacji get na semaforze z bieżącą liczbą 0.

Po wykonaniu operacji put jest wykonywana operacja pobrania zawieszonego wątku, a wątek zostaje wznowiony. Jeśli wiele wątków jest zawieszonych na tym samym semaforze zliczania, zostaną wznowione w tej samej kolejności, w jakiej zostały wstrzymane (FIFO).

Jednak możliwość wznowienia priorytetu jest również możliwa, jeśli aplikacja wywołuje ***tx_semaphore_prioritize*** przed wywołaniem semafora, które zawiesić wątek dźwigu. Usługa semafor priorytetyzacji powoduje umieszczenie wątku o najwyższym priorytecie na początku listy zawieszania, pozostawiając wszystkie pozostałe zawieszone wątki w tej samej kolejności FIFO.

### <a name="semaphore-put-notification"></a>Powiadomienie o wprowadzeniu semafora

Niektóre aplikacje mogą otrzymywać powiadomienia o każdym umieszczeniu semafora. ThreadX zapewnia tę możliwość za pomocą usługi ***tx_semaphore_put_notify*** . Ta usługa rejestruje podaną funkcję powiadamiania aplikacji z określonym semaforem. ThreadX następnie wywoła tę funkcję powiadamiania aplikacji za każdym razem, gdy semafor zostanie umieszczony. Dokładne przetwarzanie w ramach funkcji powiadomień aplikacji jest określane przez aplikację; jednak zwykle składa się z wznawiania odpowiedniego wątku do przetwarzania nowego zdarzenia Put.

### <a name="semaphore-event-chainingtrade"></a>Łańcuch zdarzeń semaforów&trade;

Funkcje powiadamiania w programie ThreadX mogą służyć do łańcucha różnych zdarzeń synchronizacji razem. Jest to zazwyczaj przydatne, gdy pojedynczy wątek musi przetwarzać wiele zdarzeń synchronizacji.

Na przykład zamiast konieczności zawieszania oddzielnych wątków dla komunikatu kolejki, flag zdarzeń i semafora aplikacja może zarejestrować procedurę powiadamiania dla każdego obiektu. Po wywołaniu procedura powiadamiania aplikacji może następnie wznowić pojedynczy wątek, który może przejrzeć każdy obiekt, aby znaleźć i przetworzyć nowe zdarzenie.

Ogólnie rzecz biorąc, *łańcuch zdarzeń* powoduje zmniejszenie liczby wątków, mniejsze obciążenie i mniejsze wymagania dotyczące pamięci RAM. Zapewnia również wysoce elastyczny mechanizm obsługujący wymagania dotyczące synchronizacji bardziej złożonych systemów.

### <a name="run-time-semaphore-performance-information"></a>Informacje o wydajności semafora czasu wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności semaforów czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

  - Umieszczanie semaforów

  - Pobieranie semafora

  - zawieszenie pobierania semaforów

  - limity czasu pobierania semaforów

Łączna liczba dla każdego semafora:

  - Umieszczanie semaforów

  - Pobieranie semafora

  - zawieszenie pobierania semaforów

  - limity czasu pobierania semaforów

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_semaphore_performance_info_get** _ i _ *_tx_semaphore_performance_system_info_get_* *. Informacje o wydajności semaforów są przydatne w ustaleniu, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo wysoka liczba przekroczeń limitu czasu "Semafor" może sugerować, że inne wątki są zbyt długie.

### <a name="semaphore-control-block-tx_semaphore"></a>Blok sterowania semaforem TX_SEMAPHORE

Charakterystyka każdego semafora zliczania znajduje się w jego bloku sterowania. Zawiera informacje, takie jak bieżąca liczba semaforów. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Bloki sterujące semaforów mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="deadly-embrace"></a>Deadly

Jednym z najbardziej interesujących i niebezpiecznych pułapek związanych z semaforami używanymi do wzajemnego wykluczania jest *Deadly*. Deadly to *warunek, w* którym co najmniej dwa wątki są zawieszane w nieskończoność podczas próby uzyskania semaforów, które są już własnością siebie.

Ten warunek jest najlepiej zilustrowany przez dwa wątki, dwa przykładowe semafory. Załóżmy, że pierwszy wątek jest właścicielem pierwszego semafora, a drugi wątek jest właścicielem drugiego semafora. Jeśli pierwszy wątek próbuje uzyskać drugi semafor i w tym samym czasie drugi wątek próbuje uzyskać pierwszy semafor, oba wątki wprowadzają warunek zakleszczenia. Ponadto, jeśli te wątki pozostają nieznacznie zawieszone, ich skojarzone zasoby są domyślnie zablokowane. Rysunek 8 ilustruje ten przykład.

**Deadly** (przykład)

![Przykład zawieszonych wątków](./media/user-guide/example-suspended-threads.png)

**RYSUNEK 8. Przykład zawieszonych wątków**

W przypadku systemów w czasie rzeczywistym Deadly można zapobiec, wprowadzając pewne ograniczenia dotyczące sposobu, w jaki wątki uzyskują semafory. Wątki mogą mieć tylko jeden semafor jednocześnie. Alternatywnie wątki mogą mieć wiele semaforów, jeśli zbierają je w takiej samej kolejności. W poprzednim przykładzie, jeśli pierwszy i drugi wątek uzyskuje pierwszy i drugi semafor w kolejności, wdrożenie Deadly jest uniemożliwione.

> [!TIP]
> *Można również użyć limitu czasu zawieszenia skojarzonego z operacją pobierania, aby odzyskać z Deadly.*

### <a name="priority-inversion"></a>Priorytetowa wersja

Inna Pitfall skojarzona z wzajemnymi semaforami wykluczeń jest w wersji priorytetowej. Ten temat został omówiony w pełni w sekcji "[priorytet wątku pułapek](#thread-priority-pitfalls)".

Podstawowy problem wynika z sytuacji, w której wątek o niższym priorytecie ma semafor, którego potrzebuje wątek o wyższym priorytecie. Jest to normalne. Jednak wątki z priorytetami między nimi mogą spowodować, że priorytet Inwersja do ostatniego niedeterministycznego czasu. Może to być obsługiwane przez staranne wybranie priorytetów wątków, użycie wartości progowej przechodzenia i tymczasowe zwiększenie priorytetu wątku, który jest właścicielem zasobu, do tego wątku o wysokim priorytecie.

## <a name="mutexes"></a>Muteksy

Oprócz semaforów ThreadX udostępnia również obiekt mutex. Mutex jest zasadniczo binarny semafor, co oznacza, że tylko jeden wątek może być właścicielem obiektu mutex jednocześnie. Ponadto ten sam wątek może wykonać pomyślną operację pobrania muteksa na należącym do obiektu mutex wiele razy, 4 294 967 295. Istnieją dwie operacje na obiekcie mutex: ***tx_mutex_get** _ i _ *_tx_mutex_put_* *. Operacja get uzyskuje mutex, który nie należy do innego wątku, podczas gdy operacja Put zwalnia poprzednio uzyskany obiekt mutex. W przypadku wątku do zwolnienia muteksu liczba operacji Put musi być równa liczbie wcześniejszych operacji pobierania.

Każdy mutex jest zasobem publicznym. ThreadX nie nakłada żadnych ograniczeń dotyczących sposobu używania muteksów.

Muteksy ThreadX są używane wyłącznie do *wzajemnego wykluczania*. W przeciwieństwie do zliczania semaforów, muteksy nie mają zastosowania jako metody powiadamiania o zdarzeniach.

### <a name="mutex-mutual-exclusion"></a>Wzajemne wykluczenie obiektu mutex

Podobnie jak w przypadku dyskusji w sekcji zliczanie semaforów, wzajemne wykluczenia dotyczy kontroli dostępu wątków do określonych obszarów aplikacji (nazywanych także *sekcjami krytycznymi* lub *zasobami aplikacji*). Jeśli jest dostępny, ThreadX mutex będzie miał liczbę własności równą 0. Po uzyskaniu elementu mutex przez wątek licznik własności jest zwiększany raz dla każdego pomyślnego wykonania operacji pobrania dla obiektu mutex i zmniejszany dla każdej pomyślnej operacji Put.

### <a name="creating-mutexes"></a>Tworzenie muteksów

ThreadX muteksy są tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. Początkowy warunek elementu mutex jest zawsze dostępny. Można również utworzyć element mutex z wybranym *dziedziczeniem priorytetu* .

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać się podczas próby wykonania operacji get na elemencie mutex, który jest już własnością innego wątku.

Po wykonaniu tej samej liczby operacji Put przez wątek będącego właścicielem zostanie wykonana operacja pobrania zawieszonego wątku, która nadaje mu własność elementu mutex, a wątek zostaje wznowiony. Jeśli wiele wątków jest zawieszonych na tym samym elemencie mutex, są wznawiane w tej samej kolejności, w jakiej zostały zawieszone (FIFO).

Jednak wznowienie priorytetu odbywa się automatycznie, jeśli podczas tworzenia wybrano dziedziczenie priorytetu obiektu mutex. Możliwe jest również wznowienie priorytetu, jeśli aplikacja wywołuje ***tx_mutex_prioritize*** przed wywołaniem obiektu mutex, które zawieszania wątku Wind. Usługa określania priorytetów obiektów mutex umieszcza wątek o najwyższym priorytecie na początku listy zawieszania, pozostawiając wszystkie pozostałe zawieszone wątki w tej samej kolejności FIFO.

### <a name="run-time-mutex-performance-information"></a>Informacje o wydajności muteksu w czasie wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności muteksu w czasie wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych **TX_MUTEX_ENABLE_PERFORMANCE_INFO** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

- Umieszczanie obiektów mutex

- Pobieranie obiektu mutex

- wstrzymanie pobierania obiektu mutex

- limity czasu pobierania dla obiektu mutex

- Brak wersji priorytetu obiektu mutex

- Dziedziczenie priorytetu obiektu mutex

Łączna liczba dla każdego muteksu:

  - Umieszczanie obiektów mutex

  - Pobieranie obiektu mutex

  - wstrzymanie pobierania obiektu mutex

  - limity czasu pobierania dla obiektu mutex

  - Brak wersji priorytetu obiektu mutex

  - Dziedziczenie priorytetu obiektu mutex

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_mutex_performance_info_get** _ i _ *_tx_mutex_performance_system_info_get_* *. Informacje o wydajności muteksu są przydatne podczas ustalania, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo wysoka liczba przekroczeń limitu czasu "mutex" może sugerować, że inne wątki są zbyt długie.

### <a name="mutex-control-block-tx_mutex"></a>Blok sterowania muteksem TX_MUTEX

Charakterystyki każdego obiektu mutex są dostępne w jego bloku sterowania. Zawiera informacje, takie jak bieżąca liczba własności obiektu mutex oraz wskaźnik wątku, który jest właścicielem obiektu mutex. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** . Bloki sterujące muteksem mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="deadly-embrace"></a>Deadly

Jednym z najbardziej interesujących i niebezpiecznych pułapek związanych z własnością obiektu mutex jest *Deadly*. Deadly, lub *zakleszczenie*, to warunek, w którym co najmniej dwa wątki są zawieszane w nieskończoność podczas próby uzyskania obiektu mutex, który jest już własnością innych wątków. Dyskusja dotycząca *Deadly* i ich środki zaradcze są całkowicie prawidłowe dla obiektu mutex.

### <a name="priority-inversion"></a>Priorytetowa wersja

Jak wspomniano wcześniej, głównym pitfallą skojarzoną z wzajemnym wykluczeniem jest priorytetowa wersja. Ten temat został omówiony w pełni w sekcji "[priorytet wątku pułapek](#thread-priority-pitfalls)".

Podstawowy problem wynika z sytuacji, w której wątek o niższym priorytecie ma semafor, którego potrzebuje wątek o wyższym priorytecie. Jest to normalne. Jednak wątki z priorytetami między nimi mogą spowodować, że priorytet Inwersja do ostatniego niedeterministycznego czasu. W przeciwieństwie do semaforów omówionych wcześniej, obiekt mutex ThreadX ma opcjonalne *dziedziczenie priorytetu*. Podstawowym pomysłem związanym z dziedziczeniem priorytetu jest to, że priorytet wątku o niższym priorytecie jest tymczasowo podniesiony do priorytetu wątku o wysokim priorytecie, który chce mieć ten sam mutex, którego właścicielem jest wątek o niższym priorytecie. Gdy wątek o niższym priorytecie zwalnia element mutex, jego oryginalny priorytet jest następnie przywracany, a wątek o wyższym priorytecie otrzymuje własność obiektu mutex. Ta funkcja eliminuje niedeterministyczną wersję priorytetu, zależnie od ilości inwersji do momentu, w którym wątek o niższym priorytecie utrzymuje element mutex. Oczywiście techniki omówione wcześniej w tym rozdziale do obsługi niedeterministycznych nieposiadanych priorytetów są również prawidłowe dla muteksów.

## <a name="event-flags"></a>Flagi zdarzeń

Flagi zdarzeń zapewniają zaawansowane narzędzie do synchronizacji wątków. Każda flaga zdarzenia jest reprezentowana przez jeden bit. Flagi zdarzeń są rozmieszczone w grupach 32. Wątki mogą obsługiwać wszystkie flagi zdarzeń 32 w grupie w tym samym czasie. Zdarzenia są ustawiane przez ***tx_event_flags_set** _ i pobierane przez _ *_tx_event_flags_get_* *.

Ustawianie flag zdarzeń odbywa się z użyciem operacji logicznej i/lub między bieżącymi flagami zdarzenia i nowymi flagami zdarzenia. Typ operacji logicznej (i lub lub) jest określony w wywołaniu ***tx_event_flags_set*** .

Istnieją podobne opcje logiczne do pobierania flag zdarzeń. Żądanie Get może określać, że wszystkie określone flagi zdarzeń są wymagane (logiczne i).

Alternatywnie żądanie Get może określać, że dowolne z określonych flag zdarzeń będzie spełniać żądanie (logiczne lub). Typ operacji logicznej skojarzonej z pobieraniem flag zdarzeń jest określany w wywołaniu ***tx_event_flags_get*** .

> [!IMPORTANT]
> *Flagi zdarzeń, które spełniają żądanie Get, są używane, tj. ustawione na zero, jeśli* **TX_OR_CLEAR** *lub* **TX_AND_CLEAR** *są określone przez żądanie.*

Każda grupa flag zdarzeń jest zasobem publicznym. ThreadX nie wprowadza żadnych ograniczeń dotyczących sposobu używania grup flag zdarzeń.

### <a name="creating-event-flags-groups"></a>Tworzenie grup flag zdarzeń

Grupy flag zdarzeń są tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. W momencie ich tworzenia wszystkie flagi zdarzeń w grupie mają ustawioną wartość zero. Nie ma żadnego limitu liczby grup flag zdarzeń w aplikacji.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać się podczas próby pobrania logicznej kombinacji flag zdarzeń z grupy. Po ustawieniu flagi zdarzenia żądania GET wszystkich zawieszonych wątków są przeglądane. Wszystkie wątki, które mają teraz wymagane flagi zdarzeń, są wznawiane.

> [!NOTE]
> *Wszystkie zawieszone wątki w grupie flag zdarzeń są przeglądane po ustawieniu flag zdarzeń. Oczywiście wprowadzają dodatkowe koszty. W związku z tym dobrym sposobem jest ograniczenie liczby wątków przy użyciu tej samej grupy flag zdarzeń do odpowiedniej liczby.*

### <a name="event-flags-set-notification"></a>Powiadomienie o ustawieniu flag zdarzeń

Niektóre aplikacje mogą otrzymywać powiadomienia, gdy flaga zdarzenia jest ustawiona. ThreadX zapewnia tę możliwość za pomocą usługi ***tx_event_flags_set_notify*** . Ta usługa rejestruje podaną funkcję powiadamiania aplikacji z określoną grupą flag zdarzeń. ThreadX następnie wywoła tę funkcję powiadamiania aplikacji za każdym razem, gdy flaga zdarzenia w grupie zostanie ustawiona. Dokładne przetwarzanie w ramach funkcji powiadomień aplikacji jest określane przez aplikację, ale zazwyczaj polega na wznowieniu odpowiedniego wątku w celu przetworzenia nowej flagi zdarzenia.

### <a name="event-flags-event-chainingtrade"></a>Tworzenie łańcucha zdarzeń flag zdarzeń&trade;

Możliwości powiadomień w programie ThreadX mogą służyć do łączenia różnych zdarzeń synchronizacji ze sobą. Jest to zazwyczaj przydatne, gdy pojedynczy wątek musi przetwarzać wiele zdarzeń synchronizacji.

Na przykład zamiast konieczności zawieszania oddzielnych wątków dla komunikatu kolejki, flag zdarzeń i semafora aplikacja może zarejestrować procedurę powiadamiania dla każdego obiektu. Po wywołaniu procedura powiadamiania aplikacji może następnie wznowić pojedynczy wątek, który może przejrzeć każdy obiekt, aby znaleźć i przetworzyć nowe zdarzenie.

Ogólnie rzecz biorąc, *łańcuch zdarzeń* powoduje zmniejszenie liczby wątków, mniejsze obciążenie i mniejsze wymagania dotyczące pamięci RAM. Zapewnia również wysoce elastyczny mechanizm obsługujący wymagania dotyczące synchronizacji bardziej złożonych systemów.

### <a name="run-time-event-flags-performance-information"></a>Informacje o wydajności flag zdarzeń czasu wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności flag w czasie wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

  - Zestawy flag zdarzeń

  - flagi zdarzeń są pobierane

  - flagi zdarzeń pobieranie zawieszeń

  - flagi zdarzeń pobierają limity czasu

Łączna liczba dla każdej grupy flag zdarzeń:

  - Zestawy flag zdarzeń

  - flagi zdarzeń są pobierane

  - flagi zdarzeń pobieranie zawieszeń

  - flagi zdarzeń pobierają limity czasu

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_event_flags_performance_info_get** _ i _*_tx_event_flags_performance_system_info_get_*_. Informacje o wydajności flag zdarzeń są przydatne w ustaleniu, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo duża liczba przekroczeń limitu czasu w usłudze _ *_tx_event_flags_get_** może sugerować, że limit czasu zawieszenia flag zdarzeń jest za krótki.

### <a name="event-flags-group-control-block-tx_event_flags_group"></a>Flagi zdarzeń grupuje blok sterowania TX_EVENT_FLAGS_GROUP

Właściwości każdej grupy flag zdarzeń znajdują się w bloku sterowania. Zawiera informacje takie jak bieżące ustawienia flag zdarzeń oraz liczbę wątków zawieszonych dla zdarzeń. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Bloki sterujące grupą zdarzeń mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną przez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="memory-block-pools"></a>Pule bloków pamięci

Przydzielanie pamięci w sposób szybki i deterministyczny jest zawsze wyzwaniem w aplikacjach w czasie rzeczywistym. Z tego względu ThreadX zapewnia możliwość tworzenia wielu pul bloków pamięci o stałym rozmiarze i zarządzania nimi.

Ponieważ pule bloków pamięci składają się z bloków o stałym rozmiarze, nigdy nie występują żadne problemy z fragmentacją. Oczywiście fragmentacja powoduje, że zachowanie, które jest niedeterministyczne. Ponadto czas wymagany do przydzielenia i zwolnienia bloku pamięci o ustalonym rozmiarze jest porównywalny z tym, że proste manipulowanie listą. Ponadto alokacja bloku pamięci i cofnięcie alokacji są wykonywane na końcu listy dostępnych. Zapewnia to najszybszy możliwy do przetwarzania listy połączonej i może pomóc zachować rzeczywisty blok pamięci w pamięci podręcznej.

Brak elastyczności jest główną wadą dla pul pamięci o stałym rozmiarze. Rozmiar bloku puli musi być wystarczająco duży, aby obsługiwał najgorsze wymagania dotyczące pamięci dla swoich użytkowników. Oczywiście pamięć może być tracona, jeśli wiele żądań pamięci o różnych rozmiarach jest wykonywanych w tej samej puli. Możliwe rozwiązanie polega na utworzeniu kilku różnych pul bloków pamięci, które zawierają różne rozmiary bloków pamięci.

Każda pula bloków pamięci jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń dotyczących sposobu używania pul.

### <a name="creating-memory-block-pools"></a>Tworzenie pul bloków pamięci

Pule bloków pamięci są tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. Nie ma limitu liczby pul bloków pamięci w aplikacji.

### <a name="memory-block-size"></a>Rozmiar bloku pamięci

Jak wspomniano wcześniej, pule bloków pamięci zawierają wiele bloków o stałym rozmiarze. Rozmiar bloku (w bajtach) jest określany podczas tworzenia puli.

> [!NOTE]
> *ThreadX dodaje niewielki nakład pracy — rozmiar wskaźnika C — do każdego bloku pamięci w puli. Ponadto ThreadX może być konieczne uzupełnienie rozmiaru bloku, aby zachować początek każdego bloku pamięci na odpowiednim wyrównaniu.*

### <a name="pool-capacity"></a>Pojemność puli

Liczba bloków pamięci w puli jest funkcją rozmiaru bloku i łączną liczbę bajtów w obszarze pamięci dostarczonym podczas tworzenia. Pojemność puli jest obliczana przez podzielenie rozmiaru bloku (włącznie z uzupełnieniem i wskaźnikiem bajtów) do całkowitej liczby bajtów w podanym obszarze pamięci.

### <a name="pools-memory-area"></a>Obszar pamięci puli

Jak wspomniano wcześniej, obszar pamięci dla puli bloków jest określany podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci w ThreadX, może ona znajdować się w dowolnym miejscu w przestrzeni adresowej docelowej.

Jest to ważna funkcja ze względu na znaczną elastyczność, którą zapewnia. Załóżmy na przykład, że produkt komunikacyjny ma obszar pamięci HighSpeed dla operacji we/wy. Ten obszar pamięci jest łatwo zarządzany przez umieszczenie go w puli bloków pamięci ThreadX.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać się podczas oczekiwania na blok pamięci z pustej puli. Gdy blok jest zwracany do puli, zawieszony wątek otrzymuje ten blok, a wątek zostaje wznowiony.

Jeśli wiele wątków jest zawieszonych w tej samej puli bloków pamięci, zostaną wznowione w kolejności, w której zostały wstrzymane (FIFO).

Jednak możliwość wznowienia priorytetu jest również możliwa, jeśli aplikacja wywołuje ***tx_block_pool_prioritize*** przed wywołaniem bloku zwalniania wątku Wind. Usługa Blocking Pool priorytetyzacja powoduje umieszczenie wątku o najwyższym priorytecie na początku listy zawieszania, pozostawiając wszystkie pozostałe zawieszone wątki w tej samej kolejności FIFO.

### <a name="run-time-block-pool-performance-information"></a>Informacje o wydajności bloku blokowego czasu wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności puli bloku czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

  - przydzielono bloki

  - bloki wydane

  - zawieszenie alokacji

  - limity czasu alokacji

Łączna liczba dla każdej puli bloków:

  - przydzielono bloki

  - bloki wydane

  - zawieszenie alokacji

  - limity czasu alokacji

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_block_pool_performance_info_get** _ i _ *_tx_block_pool_performance_system_info_get_* *. Informacje o wydajności puli bloku są przydatne podczas ustalania, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo wysoka liczba "zawieszeń alokacji" może sugerować, że Pula bloków jest za mała.

### <a name="memory-block-pool-control-block-tx_block_pool"></a>Blok sterowania puli bloków pamięci TX_BLOCK_POOL

Charakterystyki każdej puli bloków pamięci znajdują się w bloku sterowania. Zawiera informacje, takie jak liczba dostępnych bloków pamięci i rozmiar bloku puli pamięci. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Bloki sterujące puli mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="overwriting-memory-blocks"></a>Zastępowanie bloków pamięci

Ważne jest, aby upewnić się, że użytkownik przydzielony blok pamięci nie zapisuje poza granicami. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj następnym) obszarze pamięci. Wyniki są nieprzewidywalne i często krytyczne dla aplikacji.

## <a name="memory-byte-pools"></a>Pule bajtów pamięci

Pule bajtów pamięci ThreadX są podobne do standardowej sterty języka C. W przeciwieństwie do standardowej sterty C, możliwe jest posiadanie wielu pul bajtów pamięci. Ponadto wątki mogą wstrzymywać się w puli, dopóki żądana pamięć nie jest dostępna.

Alokacje z pul bajtów pamięci są podobne do tradycyjnych ***malloc** _ wywołań, które obejmują ilość żądanej pamięci (w bajtach). Pamięć jest przydzielna z puli w postaci, w której występuje _first. oznacza to, że jest używany pierwszy blok wolnej pamięci, który spełnia żądanie. Nadmierna ilość pamięci z tego bloku jest konwertowana na nowy blok i umieszczana z powrotem na liście wolnej pamięci. Ten proces jest nazywany *fragmentacją*.

Sąsiadujące bloki wolnej pamięci są *scalane* podczas kolejnego wyszukiwania alokacji dla dużej ilości wolnego bloku pamięci. Ten proces jest nazywany *defragmentacją*.

Każda pula bajtów pamięci jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń dotyczących sposobu używania pul, z tą różnicą, że nie można wywoływać usług bajtów pamięci z procedury ISR.

### <a name="creating-memory-byte-pools"></a>Tworzenie pul bajtów pamięci

Pule bajtów pamięci są tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. Nie ma żadnego limitu liczby pul bajtów pamięci w aplikacji.

### <a name="pool-capacity"></a>Pojemność puli

Liczba bajtów do przydzielenia w puli bajtów pamięci jest nieco mniejsza niż wartość określona podczas tworzenia. Wynika to z faktu, że zarządzanie obszarem wolnej pamięci wprowadza pewne obciążenie. Każdy blok wolnej pamięci w puli wymaga odpowiedniku dwóch wskaźników C w obciążeniu. Ponadto Pula jest tworzona z dwoma blokami, dużym bezpłatnym blokiem i niewielkim trwale przydzielonym blokiem na końcu obszaru pamięci. Ten przydzielony blok służy do poprawienia wydajności algorytmu alokacji. Eliminuje to konieczność ciągłego sprawdzania pod kątem końca obszaru puli podczas scalania.

W czasie wykonywania ilość narzutów w puli zwykle rośnie. Alokacje nieparzystej liczby bajtów są uzupełniane w celu zapewnienia prawidłowego wyrównania następnego bloku pamięci. Dodatkowo narzuty zwiększają się, ponieważ pula jest bardziej pofragmentowana.

### <a name="pools-memory-area"></a>Obszar pamięci puli

Obszar pamięci dla puli bajtów pamięci jest określany podczas tworzenia. Podobnie jak w przypadku innych obszarów pamięci w ThreadX, może ona znajdować się w dowolnym miejscu w przestrzeni adresowej docelowej. Jest to ważna funkcja ze względu na znaczną elastyczność, którą zapewnia. Na przykład jeśli sprzęt docelowy ma obszar pamięci o dużej szybkości i obszar pamięci o małej szybkości, użytkownik może zarządzać alokacją pamięci dla obu obszarów, tworząc pulę w każdym z nich.

### <a name="thread-suspension"></a>Zawieszenie wątku

Wątki aplikacji mogą wstrzymywać się podczas oczekiwania na bajty pamięci z puli. Gdy dostępna jest wystarczająca ciągła pamięć, zawieszone wątki otrzymują żądaną pamięć, a wątki są wznawiane.

Jeśli wiele wątków jest zawieszonych w tej samej puli bajtów pamięci, zostanie określona pamięć (wznowiona) w kolejności, w jakiej zostały wstrzymane (FIFO).

Jednak możliwość wznowienia priorytetu jest również możliwa, jeśli aplikacja wywołuje ***tx_byte_pool_prioritize*** przed wywołaniem zwolnienia bajtów, które zawieszania wątku Wind. Priorytet puli bajtów Usługa umieszcza wątek o najwyższym priorytecie na początku listy zawieszania, pozostawiając wszystkie pozostałe zawieszone wątki w tej samej kolejności FIFO.

### <a name="run-time-byte-pool-performance-information"></a>Informacje o wydajności puli bajtów czasu wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności puli bajtów w czasie wykonywania. Jeśli biblioteka i aplikacja ThreadX została skompilowana przy użyciu zdefiniowanych ***TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO*** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

  - alokacji

  - wersje

  - fragmenty przeszukane

  - fragmenty scalone

  - utworzone fragmenty

  - zawieszenie alokacji

  - limity czasu alokacji

Łączna liczba dla każdej puli bajtów:

  - alokacji

  - wersje

  - fragmenty przeszukane

  - fragmenty scalone

  - utworzone fragmenty

  - zawieszenie alokacji

  - limity czasu alokacji

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_byte_pool_performance_info_get** _ i _ *_tx_byte_pool_performance_system_info_get_* *. Informacje o wydajności puli bajtów są przydatne podczas ustalania, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji. Na przykład stosunkowo wysoka liczba "zawieszeń alokacji" może sugerować, że Pula bajtów jest za mała.

### <a name="memory-byte-pool-control-block-tx_byte_pool"></a>Blok kontroli puli bajtów pamięci TX_BYTE_POOL

Charakterystyki każdej puli bajtów pamięci znajdują się w bloku sterowania. Zawiera użyteczne informacje, takie jak liczba bajtów dostępnych w puli. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Bloki sterujące puli mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="nondeterministic-behavior"></a>Zachowanie niedeterministyczne

Chociaż pule bajtów pamięci zapewniają największą elastyczną alokację pamięci, mogą również mieć nieco niedeterministyczne zachowanie. Na przykład Pula bajtów pamięci może mieć 2 000 bajtów pamięci, ale może nie być w stanie spełnić żądania alokacji o 1 000 bajtów. Wynika to z faktu, że liczba wolnych bajtów jest ciągła. Nawet jeśli istnieje blok o numerze 1 000 bajtów, nie ma żadnych gwarancji dotyczących czasu, w którym może upłynąć, aby znaleźć blok. W całości jest możliwe, że cała pula pamięci będzie musiała zostać przeszukana w celu znalezienia bloku bajtów 1 000.

> [!TIP]
> *W wyniku niedeterministycznych zachowań pul bajtów pamięci zwykle warto unikać używania usług bajtów pamięci w obszarach, w których jest wymagane jednoznaczne zachowanie w czasie rzeczywistym. Wiele aplikacji wstępnie przydzieli wymaganą pamięć w czasie inicjalizacji lub konfiguracji czasu wykonywania.*

### <a name="overwriting-memory-blocks"></a>Zastępowanie bloków pamięci

Ważne jest, aby upewnić się, że użytkownik przydzieloną pamięć nie zapisuje poza granicami. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj następnym) obszarze pamięci. Wyniki są nieprzewidywalne i często występujące w wyniku wykonywania programu.

## <a name="application-timers"></a>Czasomierze aplikacji

Szybka odpowiedź na asynchroniczne zdarzenia zewnętrzne to najważniejsze funkcje aplikacji osadzonych w czasie rzeczywistym. Jednak wiele z tych aplikacji musi również wykonywać pewne działania w ustalonych odstępach czasu.

Czasomierze aplikacji ThreadX zapewniają aplikacjom możliwość wykonywania funkcji C w określonych odstępach czasu. Istnieje również możliwość wygaśnięcia czasomierza aplikacji tylko raz. Ten typ czasomierza jest nazywany *czasomierzem z jednym zrzutem*, podczas gdy powtarzające się czasomierze interwału są określane jako *okresowe czasomierze*.

Każdy czasomierz aplikacji jest zasobem publicznym. ThreadX nie ma żadnych ograniczeń dotyczących sposobu używania czasomierzy aplikacji.

### <a name="timer-intervals"></a>Interwały czasomierza

Interwały czasu ThreadX są mierzone przez okresowe przerwania czasomierza. Każdy przerwa czasomierza jest nazywany *cyklem* czasomierza. Rzeczywisty czas między taktami czasomierza jest określany przez aplikację, ale 10 MS jest normą dla większości implementacji. Konfiguracja czasomierza okresowego zazwyczaj znajduje się w pliku zestawu ***tx_initialize_low_level*** .

Warto zauważyć, że podstawowy sprzęt musi mieć możliwość generowania okresowych przerwań dla czasomierzy aplikacji. W niektórych przypadkach procesor ma wbudowaną funkcję okresowego przerwania. Jeśli procesor nie ma takiej możliwości, tablica użytkownika musi mieć urządzenie peryferyjne, które może generować okresowe przerwania.

> [!IMPORTANT]
> *ThreadX może nadal działać nawet bez okresowego źródła przerwań. Jednak wszystkie przetwarzanie związane z czasomierzem jest następnie wyłączone. Obejmuje to timeslicing, czas zawieszenia i usługi czasomierza.*

### <a name="timer-accuracy"></a>Dokładność czasomierza

Czas wygaśnięcia czasomierza jest określany w warunkach taktów. Określona wartość wygaśnięcia jest zmniejszana o jeden w każdym taktie czasomierza. Ponieważ czasomierz aplikacji może być włączony tuż przed przerwaniem czasomierza (lub cyklem czasomierza), rzeczywisty czas wygaśnięcia może być wcześniejszy niż jeden cykl.

Jeśli częstotliwość taktu czasomierza to 10 ms, czasomierze aplikacji mogą wygasnąć do 10 ms wczesnej. Jest to bardziej znaczące w przypadku czasomierzy 10 ms niż 1 sekunda czasomierza. Oczywiście zwiększenie częstotliwości przerwań czasomierza zmniejsza ten margines błędu.

### <a name="timer-execution"></a>Wykonywanie czasomierza

Czasomierze aplikacji są wykonywane w kolejności, w jakiej stają się aktywne. Na przykład jeśli trzy czasomierze są tworzone z tą samą wartością wygaśnięcia i aktywowane, odpowiednie funkcje wygasania są gwarantowane w kolejności, w jakiej zostały aktywowane.

### <a name="creating-application-timers"></a>Tworzenie czasomierzy aplikacji

Czasomierze aplikacji są tworzone podczas inicjacji lub w czasie wykonywania przez wątki aplikacji. Nie ma limitu liczby czasomierzy aplikacji w aplikacji.

### <a name="run-time-application-timer-performance-information"></a>Informacje o wydajności czasomierza aplikacji czasu wykonywania

ThreadX zapewnia opcjonalne informacje o wydajności czasomierza aplikacji czasu wykonywania. Jeśli biblioteka i aplikacja ThreadX zostały skompilowane przy użyciu zdefiniowanych **TX_TIMER_ENABLE_PERFORMANCE_INFO** , ThreadX gromadzi poniższe informacje.

Łączna liczba dla całego systemu:

- aktywacji

- dezaktywacje

- ponowne aktywacje (okresowe czasomierze)

- wygaśnięcia

- Korekta wygaśnięcia

Łączna liczba dla każdego czasomierza aplikacji:

- aktywacji

- dezaktywacje

- ponowne aktywacje (okresowe czasomierze)

- wygaśnięcia

- Korekta wygaśnięcia

Te informacje są dostępne w czasie wykonywania za pomocą usług ***tx_timer_performance_info_get** _ i _ *_tx_timer_performance_system_info_get_* *. Informacje o wydajności czasomierza aplikacji są przydatne w ustaleniu, czy aplikacja działa prawidłowo. Jest on również przydatny do optymalizowania aplikacji.

### <a name="application-timer-control-block-tx_timer"></a>Blok sterowania czasomierzem aplikacji TX_TIMER

Charakterystyka każdego czasomierza aplikacji znajduje się w jego bloku sterowania. Zawiera ona przydatne informacje, takie jak 32-bitowe wartości identyfikacyjne wygaśnięcia. Ta struktura jest zdefiniowana w pliku ***tx_api. h*** .

Bloki sterujące czasomierzem aplikacji mogą znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną przez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="excessive-timers"></a>Nadmierne czasomierze

Domyślnie czasomierze aplikacji są wykonywane z ukrytego wątku systemowego, który działa z priorytetem zero, który jest zazwyczaj wyższy niż dowolny wątek aplikacji. Z tego powodu przetwarzanie wewnątrz czasomierzy aplikacji powinno być ograniczone do minimum.

Ważne jest również, aby uniknąć czasomierzy, który wygasa każdy cykl czasomierza. Takie sytuacje mogą powodować nadmierne obciążenie aplikacji.

> [!IMPORTANT]
> *Jak wspomniano wcześniej, czasomierze aplikacji są wykonywane z ukrytego wątku systemowego. W związku z tym ważne jest, aby nie wybierać zawieszenia dla dowolnych wywołań usługi ThreadX wykonanych z funkcji wygaśnięcia czasomierza aplikacji.*

## <a name="relative-time"></a>Czas względny

Oprócz czasomierzy aplikacji wymienionych wcześniej ThreadX zapewnia jeden ciągły przyrost licznika 32-bitowego. Licznik lub *czas* jest zwiększany o jeden w każdym przerwaniu czasomierza.

Aplikacja może odczytywać lub ustawiać Ten licznik 32-bitowy przez wywołania do ***tx_time_get** _ i _ *_tx_time_set_* *, odpowiednio. Użycie tego licznika jest całkowicie określane przez aplikację. Nie jest on używany wewnętrznie przez ThreadX.

## <a name="interrupts"></a>Przerwań

Szybka odpowiedź na zdarzenia asynchroniczne to główna funkcja aplikacji osadzonych w czasie rzeczywistym. Aplikacja wie, że takie zdarzenie jest obecne za pomocą przerwań sprzętowych.

Przerwanie to asynchroniczna zmiana w wykonywaniu procesora. Zwykle, gdy wystąpi przerwanie, procesor *przerwań* zapisuje niewielką część bieżącego wykonania na stosie i przenosi formant do odpowiedniego wektora przerwań. Wektor przerwania jest w zasadzie tylko adresem procedury odpowiedzialnej za obsługę określonego przerwania typu. Dokładna procedura obsługi przerwania jest zależna od procesora.

### <a name="interrupt-control"></a>Kontrola przerwania

Usługa ***tx_interrupt_control*** umożliwia aplikacjom Włączanie i wyłączanie przerwań. Ta usługa zwróci poprzednią wartość Enable/Disable stan. Należy zauważyć, że kontrola przerwania ma wpływ tylko na aktualnie wykonywany segment programu. Na przykład jeśli wątek wyłącza przerwania, zostaną one wyłączone tylko podczas wykonywania tego wątku.

> [!NOTE]
> *Przerwanie z maską (NMI) to przerwanie, które nie może zostać wyłączone przez sprzęt. Takie przerwanie może być używane przez aplikacje ThreadX. Jednak procedura obsługi NMI aplikacji nie może używać funkcji zarządzania kontekstem ThreadX ani żadnych usług API.*

### <a name="threadx-managed-interrupts"></a>ThreadX zarządzane przerwania

ThreadX udostępnia aplikacje z kompletnym zarządzaniem przerwami. To zarządzanie obejmuje zapisanie i przywrócenie kontekstu przerwanego wykonania. Ponadto ThreadX umożliwia wywoływanie niektórych usług z poziomu procedur usługi przerwania (procedury ISR). Poniżej znajduje się lista usług ThreadX Services, które są dozwolone w aplikacji procedury ISR.

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
> *Zawieszenie nie jest dozwolone z procedury ISR. W związku z tym, parametr **WAIT_OPTION** dla wszystkich wywołań usługi ThreadX wykonanych z procedury ISR musi być ustawiony na **TX_NO_WAIT**.*

### <a name="isr-template"></a>Szablon ISR

Aby zarządzać przerwami aplikacji, należy wywołać kilka narzędzi ThreadX na początku i na końcu aplikacji procedury ISR. Dokładny format obsługi przerwań zależy od portów.

Następujący mały segment kodu jest typowy dla większości ThreadX zarządzanych procedury ISR. W większości przypadków to przetwarzanie jest w języku asemblera.

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

### <a name="high-frequency-interrupts"></a>Przerwania o wysokiej częstotliwości

Niektóre przerwania są wykonywane z taką dużą częstotliwością, że zapis i przywrócenie pełnego kontekstu dla każdego przerwania zużywa nadmierną przepustowość przetwarzania. W takich przypadkach często aplikacja ma mały język zestawu procedur ISR, który wykonuje ograniczoną ilość przetwarzania dla większości przerwań o wysokiej częstotliwości.

Od pewnego momentu małe procedury ISR mogą wymagać współpracy z ThreadX. Jest to realizowane przez wywołanie funkcji wejścia i wyjścia opisanych w powyższym szablonie.

### <a name="interrupt-latency"></a>Opóźnienie przerwania

ThreadX blokuje przerwania w krótkim okresie czasu. Maksymalna liczba przerwań czasu jest wyłączona w kolejności czasu wymaganej do zapisania lub przywrócenia kontekstu wątku.
