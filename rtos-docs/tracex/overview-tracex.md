---
title: Opis usługi Azure RTO TraceX
description: Azure RTO TraceX to narzędzie do analizy oparte na hoście firmy Microsoft, które udostępnia deweloperom widok graficzny zdarzeń systemu w czasie rzeczywistym i pozwala im wizualizować i lepiej zrozumieć zachowanie ich systemów w czasie rzeczywistym.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 9fd33eec6da69e6dda421a125a2dde5eae93b46d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824529"
---
# <a name="overview-of-azure-rtos-tracex"></a>Omówienie usługi Azure RTO TraceX

Azure RTO TraceX to narzędzie do analizy oparte na hoście firmy Microsoft, które udostępnia deweloperom widok graficzny zdarzeń systemu w czasie rzeczywistym i pozwala im wizualizować i lepiej zrozumieć zachowanie ich systemów w czasie rzeczywistym. Dzięki usłudze Azure RTO TraceX deweloperzy mogą jasno widzieć wystąpienia zdarzeń systemowych, takich jak przerwania i przełączenia kontekstu, które wystąpiły z powodu standardowych narzędzi do debugowania. Możliwość identyfikowania i badania tych zdarzeń oraz do lokalizowania czasu ich występowania w kontekście ogólnej operacji systemu umożliwia deweloperom Rozwiązywanie problemów programistycznych przez znalezienie nieoczekiwanego zachowania i umożliwienie im zbadania określonych obszarów dalsze informacje śledzenia są przechowywane w buforze w systemie docelowym z lokalizacją buforu i rozmiarem określonym przez aplikację w czasie wykonywania. Usługa Azure RTO TraceX może przetwarzać dowolny bufor skonstruowany w odpowiedni sposób, a nie tylko z platformy Azure RTO ThreadX, ale z dowolnej aplikacji lub RTO. Informacje o śledzeniu mogą być przekazywane do hosta na potrzeby analizy w dowolnym momencie — albo w punkcie przerwania. Usługa Azure RTO ThreadX implementuje bufor cykliczny, który umożliwia dostęp do najnowszych zdarzeń "N" do inspekcji w przypadku awarii systemu lub innego istotnego zdarzenia.

![RTO TraceX Single-Core platformy Azure](./media/user-guide/screen_shot_33.png)

**TraceX wyświetlania Single-Core**

## <a name="key-capabilites"></a>Możliwości Key

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Wbudowana analiza systemu Azure RTO TraceX

Usługa Azure RTO TraceX udostępnia wbudowane raporty analityczne systemu, które są dostępne za pośrednictwem jednego przycisku na pasku narzędzi TraceX. Te przyciski i raporty obejmują:

![Generowanie raportu profilu wykonywania](./media/overview-tracex/execution-profile-report-button.jpg) Generowanie raportu profilu wykonywania

![Generowanie raportu statystyki wydajności](./media/overview-tracex/performance-statistics-report-button.jpg) Generowanie raportu statystyki wydajności

![Generowanie raportu użycia stosu wątków](./media/overview-tracex/thread-stack-usage-report-button.jpg) Generowanie raportu użycia stosu wątków

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Dane śledzenia zebrane przez usługę Azure RTO ThreadX

Usługa Azure RTO TraceX została zaprojektowana tak, aby działała z platformą Azure RTO ThreadX, która konstruuje bazę danych "zdarzenia" systemu i aplikacji w systemie docelowym w czasie wykonywania. Te zdarzenia obejmują:

* przełączanie kontekstu wątku
* zastępujące
* zawieszeniach
* zakończenia działania
* przerwania systemowe
* zdarzenia specyficzne dla aplikacji
* wszystkie wywołania interfejsu API usługi Azure RTO ThreadX
* wszystkie wywołania interfejsu API usługi Azure RTO NetX
* wszystkie wywołania interfejsu API usługi Azure RTO FileX
* wszystkie wywołania interfejsu API usługi Azure RTO USBX
* ikony i informacje zdefiniowane przez aplikację

Zdarzenia są rejestrowane w obszarze kontrola programu, z sygnaturami czasowymi i aktywnymi identyfikatorami wątków, dzięki czemu mogą być wyświetlane później w odpowiedniej sekwencji czasowej i skojarzone z odpowiednim wątkiem. Rejestrowanie zdarzeń może zostać zatrzymane i ponownie uruchomione przez program aplikacji, na przykład w przypadku napotkania obszaru zainteresowania. Pozwala to uniknąć bałaganu bazy danych i użycie pamięci docelowej, gdy system działa poprawnie.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Usługa Azure RTO TraceX przypomina Analizator logiki oprogramowania

Po przekazaniu dziennika zdarzeń z pamięci docelowej do hosta usługa Azure RTO TraceX wyświetla zdarzenia graficznie na osi poziomej, z różnymi wątkami aplikacji i procedurami systemowymi, do których są powiązane zdarzenia na osi pionowej. Usługa Azure RTO TraceX tworzy na hoście "Analizator logiki oprogramowania", co sprawia, że zdarzenia systemowe są widoczne. Zdarzenia są reprezentowane przez ikony oznaczone kolorami, które znajdują się w punkcie wystąpienia wzdłuż osi czasu po prawej stronie odpowiedniego wątku lub procedury systemowej. Po wybraniu ikony zdarzenia są wyświetlane odpowiednie informacje dla tego zdarzenia, a także informacje dotyczące dwóch poprzednich i dwóch kolejnych zdarzeń. Dzięki temu można szybko uzyskać dostęp do najbardziej natychmiastowych informacji o zdarzeniu i jego bezpośrednio otaczających zdarzeniach. Usługa Azure RTO TraceX udostępnia widok "Podsumowanie" pokazujący wszystkie zdarzenia systemowe w pojedynczej linii poziomej, aby uprościć analizę systemów z wieloma wątkami.

### <a name="sequential-view-mode"></a>Tryb widoku sekwencyjnego

Tryb widoku sekwencyjnego jest wybierany przez kliknięcie karty "widok sekwencyjny". Jest to tryb domyślny. W tym trybie zdarzenia są wyświetlane bezpośrednio po sobie — niezależnie od czasu, jaki upłynął. Zwróć uwagę również na linijkę powyżej obszaru wyświetlania. Pokazuje względny numer zdarzenia od początku śledzenia. Ten tryb jest trybem domyślnym i jest szczególnie przydatny w Poznaniu tego, co się dzieje w systemie.

![Tryb widoku sekwencyjnego](./media/user-guide/screen_shot_10.png)

**Tryb widoku sekwencyjnego**

### <a name="time-view-mode"></a>Tryb widoku czasu

W tym trybie zdarzenia są wyświetlane w sposób relatywnie — z pełnym zielonym paskiem używanym do wyświetlania wykonywania między zdarzeniami. Ten tryb jest szczególnie przydatny do sprawdzenia, gdzie odbywa się przetwarzanie zbiorcze w systemie, co może ułatwić deweloperom dostrajanie systemu w celu zwiększenia wydajności i/lub czasu reakcji.

Zanotuj również linijkę powyżej wyświetlania zdarzeń. Ta linijka pokazuje względne Takty od początku śledzenia, jak wynika z sygnatury czasowej przystosowanej do rejestrowania śledzenia zdarzeń w usłudze Azure RTO ThreadX. Jeśli sygnatury czasowe są zbyt blisko (czasomierz niskiej częstotliwości), zdarzenia zostaną uruchomione razem. Odwrotnie, jeśli sygnatury czasowe są zbyt daleko od siebie (czasomierz o wysokiej częstotliwości), zdarzenia będą zbyt daleko od siebie. Wybór sygnatury czasowej właściwej częstotliwości jest ważnym zagadnieniem w przypadku, gdy widok względny czasowo ma znaczenie.

![Tryb widoku czasu](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>Wiersz podsumowania systemu

Usługa Azure RTO TraceX udostępnia również jedną linię podsumowania, która obejmuje wszystkie zdarzenia w tym samym wierszu. Wiersz podsumowania zawiera podsumowanie kontekstu oraz odpowiednie podsumowanie zdarzeń poniżej. Dzięki temu można łatwo zapoznać się z omówieniem złożonego systemu. Pasek podsumowania jest szczególnie przydatny w systemach, które mają doskonałą liczbę wątków. Bez tego wiersza podsumowania użytkownik będzie musiał wykonać złożone interakcje systemowe przy użyciu pionowego paska przewijania, aby postępować zgodnie z kontekstem wykonania.

Usługa Azure RTO TraceX wyświetla konteksty systemowe po lewej stronie ekranu.
Zdarzenia, które wystąpiły w określonym kontekście, są wyświetlane w linii poziomej z prawej strony tego kontekstu. W ten sposób użytkownik może łatwo ustalić, który kontekst wystąpił zdarzenie, a także śledzić wszystkie zdarzenia, które wystąpiły w określonym kontekście.

![Wiersz podsumowania systemu](./media/user-guide/screen_shot_32.png)

**Wiersz podsumowania systemu**

Pierwsze dwa wpisy kontekstu są zawsze kontekstami "Interrupt" i "Initialize/Idle". Kontekst "przerwania" reprezentuje wszystkie zdarzenia systemowe wykonane z procedur usługi przerwania (procedury ISR). Kontekst "Initialize/Idle" reprezentuje dwa konteksty w usłudze Azure RTO ThreadX. Zdarzenia, które wystąpiły podczas tx_application_define, są zdarzeniami "Initialize" i są wyświetlane w kontekście "Initialize/Idle". Jeśli system jest bezczynny i w związku z tym nie są wykonywane żadne zdarzenia, zielony pasek reprezentujący "uruchomiony" w widoku Time jest rysowany w kontekście "Inicjowanie/bezczynne".

## <a name="methods-of-navigation"></a>Metody nawigacji

Usługa Azure RTO TraceX umożliwia deweloperowi określenie, jak działają przyciski nawigacyjne "dalej" i "poprzednie".

![Przyciski nawigacji](./media/user-guide/event.png)

Jeśli wybrano opcję "zdarzenie", nawigowanie odbywa się na następnym lub poprzednim zdarzeniu. Jeśli wybrano opcję "kontekst", Nawigacja odbywa się na następnym lub poprzednim zdarzeniu w tym samym kontekście. Jeśli wybrano opcję "obiekt", Nawigacja odbywa się na następnym lub poprzednim zdarzeniu bieżącego obiektu, np. zdarzeniach skojarzonych z określoną kolejką. W przypadku wybrania opcji "przełączniki" Nawigacja jest wykonywana na przełączniku następnego/poprzedniego kontekstu. Jeśli wybrano opcję "ten sam identyfikator", Nawigacja odbywa się na następnym/powyższym zdarzeniu dla tego samego identyfikatora zdarzenia.

### <a name="event-information-display"></a>Wyświetlanie informacji o zdarzeniach

Usługa Azure RTO TraceX zawiera szczegółowe informacje dotyczące niektórych zdarzeń 300. Obejmują one sześć wewnętrznych zdarzeń usługi Azure RTO ThreadX, dwa zdarzenia ISR (wejście i wyjście), 14 wewnętrznych zdarzeń FileX platformy Azure RTO, 42 wewnętrzne zdarzenia platformy Azure RTO NetX i jedno zdarzenie zdefiniowane przez użytkownika. Pozostałe zdarzenia odpowiadają bezpośrednio na usługę Azure RTO ThreadX, Azure RTO FileX i Azure RTO NetX API Services.
Bez względu na to, czy jest zaznaczony tryb wyświetlania sekwencyjne i czasowe, wskaźnik myszy nad dowolnym zdarzeniem w obszarze wyświetlania powoduje wyświetlenie szczegółowych informacji o zdarzeniu wyświetlanych blisko zdarzenia. Wskaźnik myszy nad wydarzeniem 494 w demonstracyjnej demo_threadx. TRX plik śledzenia jest przedstawiony tutaj:

![Mouse-Over Wyświetla więcej informacji](./media/user-guide/screen_shot_37.png)

**Wskaźnik myszy — Wyświetla więcej informacji**

Każde wyświetlane zdarzenie zawiera informacje standardowe dotyczące kontekstu oraz sygnatury czas względny i czas. Pole kontekstowe pokazuje, jakiego kontekstu miało miejsce zdarzenie. Istnieje dokładnie cztery konteksty: wątek, bezczynny, ISR i Inicjalizacja. Po umieszczeniu zdarzenia w kontekście wątku nazwa wątku i jego priorytet w tym czasie są zbierane i wyświetlane, jak pokazano powyżej. Czas względny pokazuje względną liczbę cykli czasomierza od początku śledzenia. Pierwotna sygnatura czasowa wyświetla źródło danych czasu. Na koniec zostaną wyświetlone wszystkie informacje specyficzne dla zdarzenia.

### <a name="zooming-in-and-out"></a>Powiększanie i pomniejszanie

Domyślnie usługa Azure RTO TraceX wyświetla zdarzenia w łatwym do wyświetlenia rozmiarze z mapowaniem 1:1 pikseli: taktu. Użytkownik może powiększyć lub pomniejszyć. Powiększanie do 100% jest przydatne, aby zobaczyć cały ślad w bieżącym widoku wyświetlania, podczas gdy powiększanie jest przydatne w warunkach, w których nakładają się zdarzenia z powodu rozpoznania źródła sygnatury czasowej.

![Aby uzyskać szczegółowe informacje, Zoom-Out widoku do 100% lub Powiększ](./media/user-guide/screen_shot_41.png)

**Powiększ do 100% widoku lub Powiększ, aby uzyskać szczegółowe informacje**

W przypadku powiększania o 100% — Wyświetlanie całego śladu w obrębie bieżącej strony wyświetlania — łatwo jest zobaczyć wszystkie uruchomienia kontekstu przechwycone w ślad, a także ogólne zdarzenia występujące w tych kontekstach. Zauważ, że "Thread 1" i "Thread 2" są wykonywane najczęściej. Niebieskie kolorowanie swoich zdarzeń sugeruje również, że te wątki powodują wywołania usługi kolejki (zdarzenia w kolejce są niebieskie w kolorze).

Przywracanie do widoku pełnej ikony jest równie proste; Przycisk powiększania może być wybierany wielokrotnie lub może zostać wprowadzony jakiś współczynnik 100.

### <a name="delta-ticks-between-events"></a>Takty różnic między zdarzeniami

Określanie liczby taktów między różnymi zdarzeniami w usłudze Azure RTO TraceX jest proste — wystarczy kliknąć zdarzenie początkowe i przeciągnąć wskaźnik myszy do końcowego zdarzenia.
Liczba różnic między zdarzeniami zostanie wyświetlona w prawym górnym rogu ekranu.

![Takty różnicowe](./media/user-guide/screen_shot_42.png)

**Takty różnicowe**

Cykle Delta pokazują, że 5032 Takty upłynęło między zdarzenie 494 a zdarzenie 496. Można to również obliczyć ręcznie, sprawdzając względne sygnatury czasowe w każdym zdarzeniu i odejmując, ale przy użyciu graficznego interfejsu użytkownika jest to proste i natychmiastowe.

### <a name="priority-inversions"></a>Priorytetowe wersje

Usługa Azure RTO TraceX automatycznie wyświetla w pliku śledzenia wykrytych wersji priorytetu. Priorytetowe wersje są definiowane jako warunki, w których wątek o wyższym priorytecie jest blokowany, próbując uzyskać element mutex, który jest obecnie własnością wątku o niższym priorytecie. Ten warunek jest określany jako deterministyczny, ponieważ system został skonfigurowany do działania w ten sposób. W celu poinformowania użytkownika usługa Azure RTO TraceX wyświetla "deterministyczne" priorytetowe zakresy niewersji w postaci jasnego koloru łososia.

W usłudze Azure RTO TraceX są również wyświetlane "niedeterministyczne" priorytety. Te wersje priorytetowe różnią się od "deterministycznych" priorytetów w tym, że inny wątek o różnym priorytecie został wykonany w połowie wersji "deterministycznej" priorytetowej, co sprawia, że czas w nieoczekiwanym wykorzystaniu priorytetu jest nieco Niedeterministyczny. Ten stan jest często nieznany dla użytkownika i może być bardzo istotny. Aby ostrzec użytkownika o tym stanie, usługa Azure RTO TraceX wyświetla "niedeterministycznych" priorytetów jako jaśniejszy kolor łososia.

![Deterministyczna i niedeterministyczna wersja priorytetu](./media/user-guide/screen_shot_43.png)

**Deterministyczna i niedeterministyczna wersja priorytetu**

### <a name="execution-profile"></a>Profil wykonywania

Usługa Azure RTO TraceX udostępnia wbudowany raport profilu wykonywania dla wszystkich kontekstów wykonywania w ramach obecnie załadowanego pliku śledzenia.

![Profil wykonywania](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Statystyka wydajności

Usługa Azure RTO TraceX udostępnia wbudowany raport statystyk wydajności dla aktualnie załadowanego pliku śledzenia.

![Statystyka wydajności](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>Użycie stosu wątków

Usługa Azure RTO TraceX udostępnia wbudowany raport użycia stosu dla wszystkich wątków wykonywanych w ramach obecnie załadowanego pliku śledzenia.

![Użycie stosu](./media/user-guide/thread_stack_usage.png)

Usługa Azure RTO TraceX przedstawia statystyki wydajności usługi Azure RTO FileX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu — dla wszystkich otwartych obiektów multimedialnych.

![Statystyka FileX](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Statystyka usługi Azure RTO NetX

Usługa Azure RTO TraceX przedstawia także statystyki wydajności NetX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu.

![Statystyka NetX](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>Nieprzetworzony zrzut śledzenia

Usługa Azure RTO TraceX może utworzyć Nieprzetworzony plik śledzenia w formacie tekstowym i uruchomić Notatnik, aby go wyświetlić.

![Nieprzetworzony zrzut śledzenia](./media/user-guide/raw_trace_dump.png)

Należy pamiętać, że wszystkie dane o chronometrażu i rozmiarze na liście są szacunkowe i mogą być inne na platformie deweloperskiej
