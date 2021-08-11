---
title: Rozdział 3 — opis Azure RTOS TraceX
description: W tym rozdziale opisano ogólną funkcjonalność narzędzia Azure RTOS TraceX, w tym ogólną funkcjonalność graficznego interfejsu użytkownika.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: bb466427374659027bf91c7bb46c74e7d2ff561d200db9dab1a2bddbe6635ef4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789541"
---
# <a name="chapter-3---description-of-azure-rtos-tracex"></a>Rozdział 3 — opis Azure RTOS TraceX

W tym rozdziale opisano ogólną funkcjonalność narzędzia Azure RTOS TraceX, w tym ogólną funkcjonalność graficznego interfejsu użytkownika. 

## <a name="display-overview"></a>Omówienie wyświetlania

**Rysunek 4** przedstawia główne okno wyświetlania narzędzia do analizy systemu TraceX. Układ jest prosty — konteksty wykonywania są reprezentowane przez elementy pionowe po lewej stronie; np. inicjalizacja, przerwanie, bezczynność i różne wpisy wątku. Zdarzenia, które mają miejsce w każdym kontekście, są wyświetlane w poziomie w tym samym wierszu kontekstu. Na przykład zdarzenia **QR pokazane** poniżej pokazują, że wątek **_2_*_*** wywołuje kolejne wywołania funkcji _ tx_queue_receive .

![Zrzut ekranu przedstawiający główne okno wyświetlania narzędzia do analizy systemu TraceX.](./media/user-guide/screen_shot_10.png)


**RYSUNEK 5**

Zmiany kontekstu są reprezentowane przez pionowe czarne linie, które łączą wiersze kontekstu. Aktualnie wybrane zdarzenie jest reprezentowane przez ciągłą czerwoną linię pionową. W tym przykładzie wybrano zdarzenie 494.

## <a name="title-bar"></a>pasek tytułu

Pasek tytułu TraceX zawiera kilka przydatnych informacji. Pierwszy to bieżąca wersja traceX. Druga to pełna ścieżka aktualnie otwartego pliku śledzenia. Na rysunku **6 przedstawiono** przykład **_TraceX_*_ version _*_6.0.0_ _ wyświetla plik *śledzenia _*_demo_threadx.trx._**

![Zrzut ekranu przedstawiający pasek tytułu TraceX.](./media/user-guide/screen_shot_11.png)

**RYSUNEK 6**

## <a name="tool-bar"></a>Pasek narzędzi

Pasek narzędzi TraceX udostępnia kilka przycisków do otwierania plików śledzenia i elementów sterowania ich wyświetlania.

![Zrzut ekranu przedstawiający pasek narzędzi TraceX.](./media/user-guide/screen_shot_12.png)


**RYSUNEK 7**

Przyciski paska narzędzi TraceX — od lewej do prawej — są zdefiniowane w następujący sposób:
                                             
| **Przycisk**                         | **Funkcja** |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![Przycisk Otwórz plik śledzenia](./media/user-guide/screen_shot_13.png)      | Otwieranie pliku śledzenia |
| ![Przycisk Otwórz podręcznik użytkownika](./media/user-guide/screen_shot_14.png)      | Otwórz ten podręcznik użytkownika |
| ![Przycisk Generuj profil wykonywania](./media/user-guide/screen_shot_15.png)       | Generowanie profilu wykonywania |
| ![ Przycisk Generuj statystyki wydajności](./media/user-guide/screen_shot_16.png)       | Generowanie statystyk wydajności |
| ![Przycisk Generuj użycie stosu wątków](./media/user-guide/screen_shot_17.png)       | Generowanie użycia stosu wątków |
| ![Wyświetlanie przycisku wybranego zdarzenia](./media/user-guide/screen_shot_18.png)       | Wyświetlanie aktualnie wybranego zdarzenia |
| ![Wyszukiwanie przycisku](./media/user-guide/screen_shot_19.png)      | Wyszukiwanie zdarzeń |
| ![Przycisk Powiększanie](./media/user-guide/screen_shot_20.png)      | Powiększ. |
| ![Wyświetlanie przycisku powiększenia](./media/user-guide/screen_shot_21.png)      | Wybierz wartość procentową powiększenia ekranu, gdzie 100% oznacza, że cały plik śledzenia jest wyświetlany w bieżącym widoku. |
| ![Przycisk Pomniejszanie](./media/user-guide/screen_shot_22.png)      | Pomniejsz. |
| ![Wybieranie przycisku pierwszego zdarzenia](./media/user-guide/screen_shot_23.png)      | Wybierz pierwsze zdarzenie. |
| ![Przycisk Wyświetl poprzednią stronę zdarzenia](./media/user-guide/screen_shot_24.png)      | Wyświetlanie poprzedniej strony zdarzenia. |
| ![Przycisk Wyświetl poprzednie zdarzenie](./media/user-guide/screen_shot_25.png)      | Wyświetl poprzednie zdarzenie. |
| ![Przycisk nawigacji Dalej/Wstecz](./media/user-guide/screen_shot_26.png)      | Określ sposób działania przycisków nawigacji next/previous. Jeśli **wybrano** element * Event _, nawigacja odbywa się w przypadku następnego/poprzedniego zdarzenia. Jeśli _*_wybrano_*_ opcję Kontekst, nawigacja jest wykonywana dla następnego/poprzedniego zdarzenia w określonym kontekście. Jeśli _*_wybrano_*_ obiekt, nawigacja odbywa się przy następnym/poprzednim zdarzeniu określonego obiektu; na przykład zdarzenia skojarzone z określoną kolejką. Jeśli _*_wybrano_*_ opcję Przełączniki, nawigacja odbywa się w przypadku następnej/poprzedniej zmiany w kontekście. Jeśli *_wybrano_* wartość _ ID *, nawigacja odbywa się w przypadku następnego/poprzedniego zdarzenia określonego identyfikatora zdarzenia. |
| ![Przycisk Wyświetl następne zdarzenie](./media/user-guide/screen_shot_27.png)      | Wyświetl następne zdarzenie. |
| ![Przycisk Wyświetl następną stronę zdarzenia](./media/user-guide/screen_shot_28.png)      | Wyświetl stronę następnego zdarzenia. |
| ![Wybieranie przycisku ostatnie zdarzenie](./media/user-guide/screen_shot_29.png)      | Wybierz ostatnie zdarzenie. |

## <a name="display-mode-tabs"></a>Karty trybu wyświetlania

TraceX wyświetla zdarzenia systemowe na dwa różne *sposoby:* sekwencyjny i *względny czas*. Tryb domyślny jest sekwencyjny i jest to tryb pokazany na rysunku **8.**

Zmiana trybu jest prosta: wystarczy wybrać karty * Widok **sekwencyjny** _ lub _*_Widok czasu_*_ w oknie TraceX. _*Rysunek 8** przedstawia karty **_Widok sekwencyjny_*_ i _ *_Widok czasu_**.

![Zrzut ekranu przedstawiający karty Widok sekwencyjny i Widok czasu.](./media/user-guide/screen_shot_30.png)

**RYSUNEK 8**

## <a name="sequential-view-mode"></a>Sekwencyjny tryb widoku

Sekwencyjny tryb widoku jest wybierany przez kartę ***Widok sekwencyjny** _ pokazaną na rysunku _*Rysunek 8**. Jest to tryb domyślny. W tym trybie zdarzenia są wyświetlane jako im.. /mediately następujące po sobie, niezależnie od czasu, który upłynął między nimi. Zwróć również uwagę na linijkę nad obszarem wyświetlania na **rysunku 8.** Pokazuje względny numer zdarzenia od początku śledzenia.

Ten tryb jest trybem domyślnym i jest przydatny podczas uzyskiwania dobrego przeglądu tego, co dzieje się w systemie.

## <a name="time-view-mode"></a>Tryb widoku czasu

Tryb widoku czasu jest wybierany przez przycisk ***Widok** czasu _. _ *Rysunek 9** przedstawia ten sam ślad zdarzenia co **rysunek 8,** z wyjątkiem trybu widoku czasu. W tym trybie zdarzenia są wyświetlane w sposób względny pod względem czasu, a pełny zielony pasek służy do pokazywania wykonywania między zdarzeniami. Ten tryb jest przydatny do zobaczenia, gdzie odbywa się większość przetwarzania w systemie, co może ułatwić deweloperom dostrojenie systemu w celu zwiększenia wydajności i/lub czasu odpowiedzi.

![Zrzut ekranu przedstawiający kartę Widok czasu.](./media/user-guide/screen_shot_31.png)

**RYSUNEK 9**

Zwróć również uwagę na linijkę nad zdarzeniem wyświetlanym na **rysunku 9.** Ten linijka pokazuje względne takty od początku śledzenia, które pochodzą od sygnatury czasowej instrumentowane w rejestrowaniu śledzenia zdarzeń wewnątrz ThreadX. Jeśli sygnatury czasowe są zbyt blisko (czasomierz o niskiej częstotliwości), zdarzenia będą uruchamiane razem. Z drugiej jednak, jeśli sygnatury czasowe są zbyt od siebie odejmują (czasomierz o wysokiej częstotliwości), to zdarzenia będą zbyt od siebie. Wybór właściwej sygnatury czasowej częstotliwości jest ważną kwestią podczas tworzenia zrozumiałego widoku względnego czasu.

## <a name="system-summary-line"></a>Wiersz podsumowania systemu

TraceX udostępnia również pojedynczy wiersz podsumowania (górny kontekst na rysunku **10),** który zawiera wszystkie zdarzenia w tym samym wierszu. Dzięki temu można łatwo zobaczyć przegląd złożonego systemu. Pasek podsumowania jest szczególnie korzystny w systemach, które mają wiele wątków. Bez takiego wiersza podsumowania należy śledzić złożone interakcje systemowe przy użyciu pionowego paska przewijania, aby śledzić kontekst wykonywania.

![Zrzut ekranu przedstawiający wiersz podsumowania systemu na karcie Widok sekwencyjny.](./media/user-guide/screen_shot_32.png)


**RYSUNEK 10**

Wiersz podsumowania zawiera podsumowanie kontekstu oraz odpowiednie podsumowanie zdarzeń poniżej. W przykładzie przedstawionym na rysunku **10** można łatwo zobaczyć, że wątek **_2_ _ jest *wykonywany i przerywany. Przerwanie powoduje wywłaszczenie*** przez _ wątek 3 , * wątek **6** _, wątek _*_4_*_ i wątek _*_7_*_, po którym _ wątek *_2_** wznawia wykonywanie.

## <a name="system-contexts"></a>Konteksty systemu

TraceX wyświetla konteksty systemowe po lewej stronie ekranu, jak pokazano na rysunku **11.** Zdarzenia występujące w określonym kontekście są wyświetlane na poziomej linii z prawej strony tego kontekstu. W ten sposób można łatwo ustalić, w którym kontekście wystąpiło zdarzenie, a także postępować zgodnie z tym wierszem kontekstu, aby wyświetlić wszystkie zdarzenia, które wystąpiły w określonym kontekście.

Pierwsze wpisy kontekstu to zawsze ***Przerwań** _ i _*_Inicjowanie/Bezczynne_*_ konteksty. _*_Kontekst_*_ przerwań reprezentuje wszystkie zdarzenia systemowe wykonane z procedur usługi przerwań (IRS). _*_Kontekst inicjowania/bezczynności_*_ reprezentuje dwa konteksty w ThreadX. Zdarzenia występujące podczas _*_tx_application_define_*_ są _*_kontekstem inicjowania/bezczynności._*_ Jeśli system jest bezczynny i w związku z _**_ tym nie występują żadne zdarzenia, zielony pasek reprezentujący Running (Uruchomione) w widoku czasu jest rysowany w kontekście _ *_Initialize/Idle_**.

![Zrzut ekranu przedstawiający konteksty systemowe po lewej stronie ekranu.](./media/user-guide/screen_shot_33.png)

**RYSUNEK 11**

W przykładzie na **rysunku 11** istnieje dziewięć kontekstów wątków, począwszy od kontekstu _czasomierza ***systemowego. Dodatkowe informacje o poszczególnym kontekście są dostępne po umieszczeniu myszy na tym kontekście. Dodatkowe informacje obejmują adres stosu początkowego wątku, końcowy adres stosu, całkowity rozmiar, procent użytego procentu, względny procent wykonania, liczbę wstrzymania, wznowienia oraz najwyższy i najniższy priorytet podczas śledzenia. _* Rysunek 12 przedstawia** informacje dla **_wątku 0._**

![Zrzut ekranu przedstawiający informacje dotyczące wątku 0.](./media/user-guide/screen_shot_34.png)


**RYSUNEK 12**

Konteksty można również przenosić w celu grupowania tych, które są bardziej interesujące. Można to zrobić, przeciągając i upuszczając kontekst lub klikając kontekst prawym przyciskiem myszy. Kliknięcie prawym przyciskiem myszy kontekstu daje okno dialogowe do przenoszenia kontekstu na górę lub do dołu. 

Wybranie opcji ***Przenieś do góry** _ powoduje przeniesienie kontekstu wątku _*_3_*_ na górę listy kontekstowej, jak pokazano na rysunku _*Rysunek 13**.

![Zrzut ekranu przedstawiający kontekst przenoszony na górę listy kontekstów.](./media/user-guide/screen_shot_35.png)


**RYSUNEK 13**

## <a name="thread-status-information"></a>Informacje o stanie wątku

Po włączeniu traceX wyświetla stan każdego wątku za pośrednictwem kolorowej linii w kontekście wątku. Zielona linia wskazuje, że wątek jest w stanie "gotowym", a linia innego koloru wskazuje, że wątek jest zawieszony. W przypadku zawieszonych wątków kolor linii wskazuje typ obiektu ThreadX, na który jest zawieszony wątek. Na przykład na rysunku **13** zielona linia w kontekście _czasomierza systemu rozpoczynającego się od zdarzenia ***147* pokazuje, że _ _System Timer Thread_ _ jest *gotowy. Przed zdarzeniem 147* i po zdarzeniu 154 brak zielonej linii wskazuje, że _ _System Timer Thread_ _ jest *gotowy. Przed zdarzeniem 147*** i po zdarzeniu 154 brak zielonej linii wskazuje, że _ systemowy wątek czasomierza jest zawieszony.

![Zrzut ekranu przedstawiający stan każdego wątku za pośrednictwem kolorowej linii w kontekście wątku.](./media/user-guide/screen_shot_36.png)

**RYSUNEK 14**

Istnieją trzy tryby wyświetlania stanu wątku dostępne za pośrednictwem menu * Opcje **-> Status Lines** _. Opcja _*_Tylko gotowe_*_ pokazuje tylko gotowe (zielone) linie stanu, ale nie wyświetla żadnych linii stanu zawieszenia. Jest to opcja domyślna dla TraceX. Opcja *__All On_** umożliwia wyświetlanie wszystkich wierszy stanu (gotowych i wstrzymanych).

Na koniec ***opcja Wszystkie wyłączone*** wyłącza wyświetlanie wszystkich wierszy stanu.

## <a name="event-information-display"></a>Wyświetlanie informacji o zdarzeniu

TraceX zawiera szczegółowe informacje na temat niektórych 600 zdarzeń w czasie uruchomieniowym, w tym ThreadX, FileX, NetX, NetX Duo i wywołań interfejsu API USBX oraz zdarzeń wewnętrznych. TraceX obsługuje również do dodatkowych 61 439 unikatowych zdarzeń zdefiniowanych przez użytkownika.

Niezależnie od tego, czy jest wybrany tryb wyświetlania sekwencyjnego czy czasowego, kliknięcie kursorem myszy na dowolne zdarzenie w obszarze wyświetlania powoduje wyświetlenie szczegółowych informacji o zdarzeniu w pobliżu zdarzenia. Wskaźnik myszy dla zdarzenia 143 w pokazie ***demo_threadx.trx** _ trace jest wyświetlany na rysunku _*Rysunek 15**:

![Zrzut ekranu przedstawiający wskaźnik myszy zdarzenia 143 w przykładowym pliku śledzenia](./media/user-guide/screen_shot_37.png)

**RYSUNEK 15**

Każde wyświetlane zdarzenie zawiera standardowe informacje o ***context** _ i _*_sygnaturze czasowej względnej_*_ i _*_sygnaturze czasowej_*_. Pole Kontekst pokazuje kontekst, w którym miało miejsce zdarzenie. Istnieją dokładnie cztery konteksty: wątek, bezczynny, ISR i inicjalizacja. Gdy zdarzenie ma miejsce w kontekście wątku, nazwa wątku i jego priorytet w tym czasie są zbierane i wyświetlane, jak pokazano powyżej. Pole _*_Czas względny_*_ pokazuje względną liczbę takt czasomierzy od początku śledzenia. *_Nieprzetworzone sygnatury czasowe_** wyświetla nieprzetworzone źródło czasu zdarzenia. Na koniec zostaną wyświetlone wszystkie informacje specyficzne dla zdarzenia. Te informacje są szczegółowo opisane w pozostałej części tego rozdziału.

Szczegółowe informacje o zdarzeniach są również dostępne przez dwukrotne kliknięcie dowolnego zdarzenia. Dwukrotne kliknięcie zdarzenia 143 zostało pokazane na **rysunku 16:**

![Zrzut ekranu przedstawiający szczegółowe informacje o zdarzeniu po dwukrotnym kliknięciu zdarzenia.](./media/user-guide/screen_shot_38.png)

**RYSUNEK 16**

Możliwość wyświetlania wielu zdarzeń jednocześnie zapewnia użytkownikowi znacznie bogatszy obraz tego, co się stało. Wyświetlanie ich obok siebie jest bardzo przydatne, ponieważ wiele zdarzeń jest powiązanych. Jest to realizowane przez dwukrotne kliknięcie wielu zdarzeń.

## <a name="current-event-display"></a>Wyświetlanie bieżącego zdarzenia

TraceX wyświetla bieżące zdarzenie — w osobnym oknie — po wybraniu przez użytkownika za pomocą polecenia ***View -> Current Event*** (Wyświetl bieżące zdarzenie) lub klikając przycisk bieżącego zdarzenia na pasku narzędzi. Po wybraniu traceX wyświetla aktualnie wybrane zdarzenie w oknie autonomicznym i odświeża to okno za każdym razem, gdy zostanie wybrane inne zdarzenie.

## <a name="event-searching"></a>Wyszukiwanie zdarzeń

TraceX zapewnia rozbudowane możliwości wyszukiwania zdarzeń. Identyfikator zdarzenia i pola informacji każdego zdarzenia są podstawowymi parametrami wyszukiwania. Nieo określenie wartości parametru wyszukiwania wskazuje, że parametr skutecznie usuwa ten parametr z wyszukiwania. Ponadto wyszukiwanie może odbywać się w taki sposób, że dowolny znaleziony parametr spełni kryteria wyszukiwania lub wszystkie parametry muszą zostać znalezione, aby spełnić kryteria wyszukiwania. Wyszukiwanie może być również ograniczone do określonego kontekstu lub obejmować wszystkie konteksty w śladach. W celu wywołania wyszukiwania zdarzeń wybierz przycisk ***** Wyszukaj według wartości _ na pasku narzędzi, jak pokazano na rysunku _17**. Po wybraniu zostanie wyświetlone okno dialogowe wyszukiwania, które określa wszystkie parametry wyszukiwania. Przycisków **_Dalej_*_ _*_i_*_ Poprzedni w oknie dialogowym wyszukiwania można następnie użyć do znalezienia następnych i poprzednich zdarzeń, które spełniają określone kryteria wyszukiwania. _ *Rysunek 17** pokazuje okno dialogowe wyszukiwania.

![Zrzut ekranu przedstawiający wyszukiwanie zdarzeń.](./media/user-guide/screen_shot_39.png)

**RYSUNEK 17**

![Zrzut ekranu przedstawiający okno dialogowe wyszukiwania.](./media/user-guide/screen_shot_40.png)

**RYSUNEK 18**

## <a name="zooming-in-and-out"></a>Powiększanie i pomniejszanie

Domyślnie traceX wyświetla zdarzenia w pełnym rozmiarze. Możesz powiększać lub pomniejszać zgodnie z potrzebami. Pomniejszenie przydaje się do zobaczenia ogólnych zdarzeń przechwyconych w śladach, natomiast powiększanie jest przydatne w warunkach, w których zdarzenia nakładają się ze względu na rozdzielczość źródła sygnatury czasowej. **Rysunek 19** przedstawia **_pomniejszony demo_threadx.trx,_** dzięki czemu jest wyświetlana 100% pliku śledzenia.

![Zrzut ekranu przedstawiający pomniejszony przykładowy plik w celu pokazywania 100% pliku śledzenia.](./media/user-guide/screen_shot_41.png)

**RYSUNEK 19**

Po pomniejszeniu o 100% w celu wyświetlenia całego śladu na bieżącej stronie wyświetlania można łatwo zobaczyć wszystkie wykonania kontekstu przechwycone w śladach, a także ogólne zdarzenia występujące w tych kontekstach. Zwróć **uwagę, że na rysunku 16** wątek **_1_*_ i _ wątek*_2_** są wykonywane najczęściej. Niebieskie kolorowanie ich zdarzeń sugeruje również, że te wątki są wywołaniami usługi kolejki (zdarzenia kolejki mają kolor niebieski).

Przywracanie do pełnego widoku ikony jest równie proste. Przycisk powiększania może być wybierany wielokrotnie lub może zostać wprowadzony współczynnik 100.

## <a name="delta-ticks-between-events"></a>Delta Ticks Between Events

Określanie liczby takt między różnymi zdarzeniami w traceX jest łatwe — kliknij zdarzenie początkowe i przeciągnij myszą do zdarzenia końcowego. Liczba różnicowa takt między zdarzeniami jest wyświetlana w prawym górnym rogu ekranu, jak pokazano na rysunku **17.**

![Zrzut ekranu przedstawiający różnicowe liczby takt między zdarzeniami.](./media/user-guide/screen_shot_42.png)

**RYSUNEK 17**

Takty różnicowe pokazane na rysunku **17** pokazują, że upłynął czas między zdarzeniem 125 a zdarzeniem 154. Można to również obliczyć ręcznie, analizując względne sygnatury czasowe w każdym zdarzeniu i odejmując, ale korzystanie z graficznego interfejsu użytkownika jest łatwe i natychmiastowe.

## <a name="actual-time-display"></a>Wyświetlanie czasu rzeczywistego

Po włączeniu traceX wyświetla rzeczywisty czas w mikrosekundach w ***** widoku czasu _ i dla różnych informacji o czasie różnicy wyświetlanych przez TraceX. Domyślnie wyświetlany czas rzeczywisty jest wyłączony. Aby włączyć wyświetlanie czasu rzeczywistego, należy wprowadzić liczbę takt na mikrosekundę za pośrednictwem menu _ *_Options -> Ticks per Microsecond_** (wartość do wprowadzenia jest określana przez źródło czasomierza sprzętowego używane do rejestrowania zdarzeń TraceX na docelowym).

## <a name="priority-inversions"></a>Inversions priorytetu

TraceX automatycznie wyświetla inversions priorytet wykryte w pliku śledzenia. Wywłaszczenia priorytetów są definiowane jako warunki, w których wątek o wyższym priorytecie jest blokowany, próbując uzyskać mutex, który jest obecnie własnością wątku o niższym priorytecie. Ten warunek jest *terminem deterministycznym*, ponieważ system został ustawiony do działania w ten sposób. Aby poinformować użytkownika, traceX pokazuje *zakresy odwrócenia priorytetu* deterministycznego jako jasny kolor nabłoku.

TraceX wyświetla również *nie deterministyczne inversions* priorytetów. Te inwersje  priorytetu różnią się od deterministycznych wywłaszczeń priorytetów tym,  że inny wątek o innym poziomie priorytetu został wykonany w trakcie tego, co było deterministyczną inwersją priorytetu, dzięki czemu czas w ramach priorytetu inversion nieco nie *deterministyczne*. Ten warunek jest często nieznany użytkownikowi i może być bardzo poważny. Aby zaalarmować użytkownika o tym stanie, program TraceX pokazuje nie *deterministyczne* odwrócenia priorytetów jako jaśniejszy kolor koloru koloru. **Rysunek 18** przedstawia *zarówno deterministyczne,* jak i nie *deterministyczne* odwrócenia priorytetów.

![Zrzut ekranu przedstawiający odwrócenie priorytetu w pliku śledzenia.](./media/user-guide/screen_shot_43.png)

**RYSUNEK 18**

**Rysunek 18** przedstawia *deterministyczną odwrócenie* priorytetu ze zdarzenia 398 do zdarzenia 402. W tym zakresie bloków o wyższym priorytecie * wątku **0** _ na mutex należące do wątku o niższym _*_priorytecie 1_*_. W przypadku zdarzenia 402 _ *_wątek 1_** zwalnia mutex i w związku z tym kończy inversion priorytetu.

Jaśniejszy zacieniony obszar pokazuje *nieterministyczną* odwrócenie priorytetu między zdarzeniem od 408 do zdarzenia 420. To, co sprawia, że ten nie *deterministyczny* jest to, że podczas * wątku **1** _ zawiera element mutex, na którym jest zablokowany wątek _*_0_*_ o wyższym priorytecie, występuje przerwanie, które wznawia _* wątek _2_**, który następnie wykonuje i wydłuża czas, w którym system jest w inwersji priorytetu. Ten stan może być dość poważny i trudny do zidentyfikowania. Jednak za pomocą traceX można go łatwo zidentyfikować.
