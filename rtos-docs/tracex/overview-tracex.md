---
title: Opis Azure RTOS TraceX
description: Azure RTOS TraceX to oparte na hoście narzędzie do analizy firmy Microsoft, które udostępnia deweloperom graficzny widok zdarzeń systemowych w czasie rzeczywistym oraz umożliwia im wizualizowanie i lepsze zrozumienie zachowania systemów czasu rzeczywistego.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 966f3be5ebe34e006067175e422480fbf1ab664bb0ff627d7b01e71036dc5e82
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792184"
---
# <a name="overview-of-azure-rtos-tracex"></a>Omówienie Azure RTOS TraceX

Azure RTOS TraceX to oparte na hoście narzędzie do analizy firmy Microsoft, które udostępnia deweloperom graficzny widok zdarzeń systemowych w czasie rzeczywistym oraz umożliwia im wizualizowanie i lepsze zrozumienie zachowania systemów czasu rzeczywistego. Dzięki Azure RTOS TraceX deweloperzy mogą wyraźnie zobaczyć wystąpienia zdarzeń systemowych, takich jak przerwania i przełączniki kontekstu, które występują poza widokiem standardowych narzędzi debugowania. Możliwość identyfikowania i badania tych zdarzeń oraz określania harmonogramu ich wystąpienia w kontekście ogólnej operacji systemu umożliwia deweloperom rozwiązywanie problemów programistycznych przez znalezienie nieoczekiwanego zachowania i umożliwienie im badania określonych obszarów Dalsze informacje śledzenia są przechowywane w buforze w systemie docelowym z lokalizacją buforu i rozmiarem określonym przez aplikację w czasie wykonywania. Azure RTOS TraceX może przetworzyć dowolny bufor skonstruowany w odpowiedni sposób, nie tylko z Azure RTOS ThreadX, ale również z dowolnej aplikacji lub systemu RTOS. Informacje śledzenia można przekazać do hosta w celu analizy w dowolnym momencie — po zakończeniu analizy lub w punkcie przerwania. Azure RTOS ThreadX implementuje bufor cykliczny, który umożliwia dostęp do najnowszych zdarzeń "N" do inspekcji w przypadku awarii systemu lub innego istotnego zdarzenia.

![Azure RTOS ekranu Single-Core TraceX](./media/user-guide/screen_shot_33.png)

**Ekran Single-Core TraceX**

## <a name="key-capabilites"></a>Kluczowe możliwości

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Azure RTOS wbudowanej analizy systemu TraceX

Azure RTOS TraceX udostępnia wbudowane raporty analizy systemu, które są dostępne za pośrednictwem pojedynczego kliknięcia przycisku na pasku narzędzi TraceX. Te przyciski i raporty obejmują:

![Generowanie raportu profilu wykonywania](./media/overview-tracex/execution-profile-report-button.jpg) Generowanie raportu profilu wykonywania

![Generowanie raportu statystyki wydajności](./media/overview-tracex/performance-statistics-report-button.jpg) Generowanie raportu statystyki wydajności

![Generowanie raportu użycia stosu wątków](./media/overview-tracex/thread-stack-usage-report-button.jpg) Generowanie raportu użycia stosu wątków

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Dane śledzenia zebrane przez Azure RTOS ThreadX

Azure RTOS TraceX jest przeznaczony do pracy z platformą Azure RTOS ThreadX, która tworzy bazę danych "zdarzeń" systemu i aplikacji w systemie docelowym w czasie działania. Zdarzenia te obejmują:

* przełączniki kontekstu wątku
* wywłaszcze
* Zawieszenia
* Końcówki
* przerwań systemowych
* zdarzenia specyficzne dla aplikacji
* wszystkie Azure RTOS interfejsu API ThreadX
* wszystkie Azure RTOS interfejsu API NetX
* wszystkie Azure RTOS api FileX
* wszystkie Azure RTOS interfejsu API USBX
* Ikony i informacje zdefiniowane przez aplikację

Zdarzenia są rejestrowane pod kontrolą programu ze znacznikami czasu i aktywną identyfikacją wątku, dzięki czemu mogą być wyświetlane później w odpowiedniej sekwencji czasu i skojarzone z odpowiednim wątkiem. Rejestrowanie zdarzeń może zostać dynamicznie zatrzymane i ponownie uruchomione przez program aplikacji, na przykład po napotkaniu obszaru zainteresowania. Pozwala to uniknąć zaśmiecania bazy danych i używania pamięci docelowej, gdy system działa prawidłowo.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Azure RTOS TraceX jest jak programowy analizator logiki

Po przesłaniu dziennika zdarzeń z pamięci docelowej do hosta narzędzie Azure RTOS TraceX wyświetla zdarzenia graficznie na osi poziomej reprezentującej czas, z różnymi wątkami aplikacji i procedurami systemowym, z którymi zdarzenia są powiązane wzdłuż osi pionowej. Azure RTOS TraceX tworzy na hoście "programowy analizator logiki", dzięki czemu zdarzenia systemowe są wyraźnie widoczne. Zdarzenia są reprezentowane przez zakodowane kolorami ikony znajdujące się w punkcie wystąpienia wzdłuż poziomej osi czasu po prawej stronie odpowiedniego wątku lub procedury systemowej. Po wybraniu ikony zdarzenia zostaną wyświetlone odpowiednie informacje dotyczące tego zdarzenia, a także informacje dotyczące dwóch poprzednich i dwóch kolejnych zdarzeń. Zapewnia to szybki dostęp jednym kliknięciem do najbardziej natychmiastowych informacji o zdarzeniu i jego natychmiast otaczających zdarzeniach. Azure RTOS TraceX zawiera ekran "Podsumowanie", który pokazuje wszystkie zdarzenia systemowe w pojedynczej linii poziomej, aby uprościć analizę systemów z wieloma wątkami.

### <a name="sequential-view-mode"></a>Sekwencyjny tryb widoku

Tryb widoku sekwencyjnego jest wybierany przez kliknięcie karty "Widok sekwencyjny". Jest to tryb domyślny. W tym trybie zdarzenia są wyświetlane bezpośrednio po sobie — niezależnie od czasu, który upłynął między nimi. Zwróć również uwagę na linijkę nad obszarem wyświetlania. Pokazuje względny numer zdarzenia od początku śledzenia. Ten tryb jest trybem domyślnym i jest szczególnie przydatny podczas uzyskiwania dobrego przeglądu tego, co dzieje się w systemie.

![Sekwencyjny tryb widoku](./media/user-guide/screen_shot_10.png)

**Sekwencyjny tryb widoku**

### <a name="time-view-mode"></a>Tryb widoku czasu

W tym trybie zdarzenia są wyświetlane w sposób względny w czasie — pełny zielony pasek służy do pokazywania wykonywania między zdarzeniami. Ten tryb jest szczególnie przydatny do zobaczenia, gdzie odbywa się większość przetwarzania w systemie, co może ułatwić deweloperom dostrojenie systemu w celu zwiększenia wydajności i/lub czasu odpowiedzi.

Zwróć również uwagę na linijkę nad ekranem zdarzenia. Ten linijka pokazuje względne takty od początku śledzenia, pochodzące od sygnatury czasowej instrumentowane w rejestrowaniu śledzenia zdarzeń wewnątrz Azure RTOS ThreadX. Jeśli sygnatury czasowe są zbyt blisko (czasomierz o niskiej częstotliwości), zdarzenia będą uruchamiane razem. Z kolei jeśli sygnatury czasowe są zbyt duże (czasomierz o wysokiej częstotliwości), zdarzenia będą zbyt duże. Wybór odpowiedniej sygnatury czasowej częstotliwości jest ważną kwestią podczas tworzenia zrozumiałego widoku względnego czasu.

![Tryb widoku czasu](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>Wiersz podsumowania systemu

Azure RTOS TraceX udostępnia również pojedynczy wiersz podsumowania, który zawiera wszystkie zdarzenia w tym samym wierszu. Wiersz podsumowania zawiera podsumowanie kontekstu oraz odpowiednie podsumowanie zdarzeń poniżej. Dzięki temu można łatwo zobaczyć przegląd złożonego systemu. Pasek podsumowania jest szczególnie korzystny w systemach, które mają dużą liczbę wątków. Bez takiego wiersza podsumowania użytkownik musiałby śledzić złożone interakcje systemowe przy użyciu pionowego paska przewijania, aby śledzić kontekst wykonywania.

Azure RTOS TraceX wyświetla konteksty systemowe po lewej stronie ekranu.
Zdarzenia występujące w określonym kontekście są wyświetlane na poziomej linii z prawej strony tego kontekstu. W ten sposób użytkownik może łatwo ustalić, w którym kontekście wystąpiło zdarzenie, a także postępować zgodnie z tym wierszem kontekstu, aby wyświetlić wszystkie zdarzenia, które wystąpiły w określonym kontekście.

![Wiersz podsumowania systemu](./media/user-guide/screen_shot_32.png)

**Wiersz podsumowania systemu**

Pierwsze dwa wpisy kontekstu to zawsze konteksty "Przerwań" i "Inicjowanie/bezczynność". Kontekst "Przerwań" reprezentuje wszystkie zdarzenia systemowe wykonane z procedur usługi przerwań (ISR). Kontekst "Inicjowanie/bezczynność" reprezentuje dwa konteksty w Azure RTOS ThreadX. Zdarzenia występujące podczas tx_application_define są zdarzeniami "Inicjowanie" i są wyświetlane w kontekście "Inicjowanie/bezczynność". Jeśli system jest bezczynny i w związku z tym nie występują żadne zdarzenia, zielony pasek reprezentujący "Running" (Uruchomiony) w widoku czasu jest rysowany w kontekście "Inicjowanie/bezczynność".

## <a name="methods-of-navigation"></a>Metody nawigacji

Azure RTOS TraceX umożliwia deweloperowi określenie sposobu działania przycisków nawigacji "Dalej" i "Poprzedni".

![Przyciski nawigacji](./media/user-guide/event.png)

Jeśli wybrano opcję "Zdarzenie", nawigacja odbywa się w przypadku następnego/poprzedniego zdarzenia. Jeśli wybrano opcję "Kontekst", nawigacja jest wykonywana dla następnego/poprzedniego zdarzenia w tym samym kontekście. Jeśli wybrano opcję "Obiekt", nawigacja odbywa się przy następnym/poprzednim zdarzeniu bieżącego obiektu, np. zdarzeniach skojarzonych z określoną kolejką. Jeśli wybrano opcję "Przełączniki", nawigacja odbywa się przy następnym/poprzednim przełączniku kontekstu. Jeśli wybrano opcję "Ten sam identyfikator", nawigacja zostanie wykonana dla następnego/poprzedniego zdarzenia dla tego samego identyfikatora zdarzenia.

### <a name="event-information-display"></a>Wyświetlanie informacji o zdarzeniu

Azure RTOS TraceX zawiera szczegółowe informacje na temat niektórych 300 zdarzeń. Obejmują one sześć wewnętrznych zdarzeń Azure RTOS ThreadX, dwa zdarzenia ISR (wejście i wyjście), 14 wewnętrznych zdarzeń Azure RTOS FileX, 42 zdarzenia wewnętrzne Azure RTOS NetX i jedno zdarzenie zdefiniowane przez użytkownika. Pozostałe zdarzenia odpowiadają bezpośrednio Azure RTOS ThreadX, Azure RTOS FileX i Azure RTOS api NetX.
Niezależnie od tego, czy jest wybrany tryb wyświetlania sekwencyjnego czy czasowego, kliknięcie kursorem myszy na dowolne zdarzenie w obszarze wyświetlania powoduje wyświetlenie szczegółowych informacji o zdarzeniu w pobliżu zdarzenia. Wskaźnik myszy dla zdarzenia 494 w pliku śledzenia demo_threadx.trx pokazu jest pokazany poniżej:

![Mouse-Over wyświetla więcej informacji](./media/user-guide/screen_shot_37.png)

**Wskaźnik myszy wyświetla więcej informacji**

Każde wyświetlane zdarzenie zawiera standardowe informacje o kontekście oraz o czasie względnym i sygnaturze czasowej. Pole Kontekst pokazuje kontekst, w którym miało miejsce zdarzenie. Istnieją dokładnie cztery konteksty: wątek, bezczynny, ISR i inicjalizacja. Gdy zdarzenie ma miejsce w kontekście wątku, nazwa wątku i jego priorytet w tym czasie są zbierane i wyświetlane, jak pokazano powyżej. Pole Czas względny pokazuje względną liczbę takt czasomierzy od początku śledzenia. Nieprzetworzone sygnatury czasowe wyświetla nieprzetworzone źródło czasu zdarzenia. Na koniec zostaną wyświetlone wszystkie informacje specyficzne dla zdarzenia.

### <a name="zooming-in-and-out"></a>Powiększanie i pomniejszanie

Domyślnie program Azure RTOS TraceX wyświetla zdarzenia w łatwym do wyświetlenia rozmiarze z mapowaniem 1:1 piksela:znacznika. Użytkownik może powiększać lub pomniejszać w razie potrzeby. Pomniejszenie do 100% przydaje się do wyświetlenia całego śladu w bieżącym widoku wyświetlania, natomiast powiększanie jest przydatne w warunkach, w których zdarzenia nakładają się ze względu na rozdzielczość źródła sygnatury czasowej.

![Zoom-Out do 100% wyświetl lub powiększ w celu wyświetlenia szczegółów](./media/user-guide/screen_shot_41.png)

**Pomniejszanie do 100% widoku lub powiększanie w celu wyświetlenia szczegółów**

Po pomniejszeniu o 100% — pokazując cały ślad na bieżącej stronie wyświetlania — można łatwo zobaczyć wszystkie wykonania kontekstu przechwycone w śladach, a także ogólne zdarzenia występujące w tych kontekstach. Zauważ, że "wątek 1" i "wątek 2" są wykonywane najczęściej. Niebieskie kolorowanie ich zdarzeń sugeruje również, że te wątki są wywołaniami usługi kolejki (zdarzenia kolejki mają kolor niebieski).

Przywracanie do pełnego widoku ikony jest równie proste. Przycisk powiększania może być wybierany wielokrotnie lub może zostać wprowadzony współczynnik 100.

### <a name="delta-ticks-between-events"></a>Takty różnicowe między zdarzeniami

Określanie liczby takt między różnymi zdarzeniami w programie Azure RTOS TraceX jest łatwe — wystarczy kliknąć zdarzenie początkowe i przeciągnąć myszą do zdarzenia końcowego.
Liczba różnicowa takt między zdarzeniami będzie wyświetlana w prawym górnym rogu ekranu.

![Delta Ticks](./media/user-guide/screen_shot_42.png)

**Delta Ticks**

Takty różnicowe pokazują, że upłynął czas 5032 taktów między zdarzeniem 494 a zdarzeniem 496. Można to również obliczyć ręcznie, analizując względne sygnatury czasowe w każdym zdarzeniu i odejmując, ale korzystanie z graficznego interfejsu użytkownika jest łatwe i natychmiastowe.

### <a name="priority-inversions"></a>Inversions priorytetu

Azure RTOS TraceX automatycznie wyświetla inversions priorytet wykryte w pliku śledzenia. Wywłaszczenia priorytetów są definiowane jako warunki, w których wątek o wyższym priorytecie jest blokowany, próbując uzyskać mutex, który jest obecnie własnością wątku o niższym priorytecie. Ten warunek jest terminem "deterministyczny", ponieważ system był konfigurowany do działania w ten sposób. Aby poinformować użytkownika, Azure RTOS TraceX pokazuje zakresy odwrócenia priorytetu "deterministyczne" jako jasny kolor koloru.

Azure RTOS TraceX wyświetla również "nie deterministyczne" inversions priorytetu. Te inwersje priorytetu różnią się od "deterministycznych" wywłaszczeń priorytetów tym, że inny wątek innego poziomu priorytetu został wykonany w trakcie co było "deterministyczną" odwróceniem priorytetu, dzięki czemu czas w ramach priorytetu inversion nieco "un-deterministic". Ten warunek jest często nieznany użytkownikowi i może być bardzo poważny. Aby zaalarmować użytkownika o tym stanie, Azure RTOS TraceX wyświetla "nie deterministyczne" inwersje priorytetu jako jaśniejszy kolor cyka.

![Deterministyczna i nie deterministyczna inwersja priorytetu](./media/user-guide/screen_shot_43.png)

**Deterministyczna i nie deterministyczna inwersja priorytetu**

### <a name="execution-profile"></a>Profil wykonywania

Azure RTOS TraceX udostępnia wbudowany raport profilu wykonywania dla wszystkich kontekstów wykonywania w ramach aktualnie załadowanego pliku śledzenia.

![Profil wykonywania](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Statystyki wydajności

Azure RTOS TraceX udostępnia wbudowany raport statystyk wydajności dla aktualnie załadowanego pliku śledzenia.

![Statystyki wydajności](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>Użycie stosu wątków

Azure RTOS TraceX udostępnia wbudowany raport użycia stosu dla wszystkich wątków wykonywanych w ramach aktualnie załadowanego pliku śledzenia.

![Użycie stosu](./media/user-guide/thread_stack_usage.png)

Azure RTOS TraceX przedstawia Azure RTOS wydajności pliku śledzenia aktualnie załadowanego pliku FileX. Te informacje są wyświetlane dla całego systemu — na wszystkich otwartych obiektach nośników.

![Statystyki FileX](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Azure RTOS statystyk NetX

Azure RTOS TraceX przedstawia również statystyki wydajności NetX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu.

![Statystyki NetX](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>Nieprzetworzone zrzuty śledzenia

Azure RTOS TraceX może utworzyć nieprzetworzone pliki śledzenia w formacie tekstowym i uruchomić Notatnik, aby go wyświetlić.

![Nieprzetworzone zrzuty śledzenia](./media/user-guide/raw_trace_dump.png)

Należy pamiętać, że wszystkie wartości chronometrażu i rozmiaru na liście są szacowane i mogą się różnić na platformie dewelopera
