---
title: Rozdział 3 — Opis usługi Azure RTO TraceX
description: W tym rozdziale opisano ogólne funkcje narzędzia do analizy systemu Azure RTO TraceX, w tym ogólne funkcje jego graficznego interfejsu użytkownika.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1c974b353c92e0a3cf51c92818794197cf999582
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823527"
---
# <a name="chapter-3---description-of-azure-rtos-tracex"></a>Rozdział 3 — Opis usługi Azure RTO TraceX

W tym rozdziale opisano ogólne funkcje narzędzia do analizy systemu Azure RTO TraceX, w tym ogólne funkcje jego graficznego interfejsu użytkownika. 

## <a name="display-overview"></a>Przegląd wyświetlania

Na **rysunku 4** przedstawiono główne okno wyświetlania narzędzia do analizy systemu TraceX. Układ jest prosty — konteksty wykonywania są reprezentowane przez pionowe elementy po lewej stronie; na przykład inicjowanie, przerwanie, bezczynne i różne wpisy wątku. Zdarzenia, które mają miejsce w każdym kontekście, są wyświetlane w poziomie w tym samym wierszu kontekstu. Na przykład zdarzenia **QR** pokazane poniżej pokazują, że **_wątek 2_*_ czyni kolejne wywołania do _*_tx_queue_receive_**.

![Zrzut ekranu przedstawiający główne okno wyświetlania narzędzia do analizy systemu TraceX.](./media/user-guide/screen_shot_10.png)


**RYSUNEK 5**

Zmiany kontekstu są reprezentowane przez pionowe, czarne linie łączące linie kontekstowe. Aktualnie wybrane zdarzenie jest reprezentowane przez ciągłą czerwoną linię pionową. W tym przykładzie wybrano zdarzenie 494.

## <a name="title-bar"></a>pasek tytułu

Pasek tytułu TraceX zawiera kilka przydatnych informacji. Pierwsza to bieżąca wersja TraceX. Sekundę jest pełną ścieżką aktualnie otwartego pliku śledzenia. Przykład na **rysunku 6** pokazuje **_TraceX_*_ wersja*__ 6.0.0_*_ wyświetla plik śledzenia _*_demo_threadx. TRX_** .

![Zrzut ekranu przedstawiający pasek tytułu TraceX.](./media/user-guide/screen_shot_11.png)

**RYSUNEK 6.**

## <a name="tool-bar"></a>Pasek narzędzi

Pasek narzędzi TraceX zawiera kilka przycisków służących do otwierania plików śledzenia i elementów kontroli ich wyświetlania.

![Zrzut ekranu przedstawiający pasek narzędzi TraceX.](./media/user-guide/screen_shot_12.png)


**RYSUNEK 7**

Przyciski paska narzędzi TraceX — od lewej do prawej — są zdefiniowane w następujący sposób:
                                             
| **Przycisk**                         | **Funkcja** |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![Przycisk otwierania pliku śledzenia](./media/user-guide/screen_shot_13.png)      | Otwórz plik śledzenia |
| ![Przycisk otwierania podręcznika użytkownika](./media/user-guide/screen_shot_14.png)      | Otwórz ten przewodnik użytkownika |
| ![Przycisk Generuj profil wykonywania](./media/user-guide/screen_shot_15.png)       | Generuj profil wykonywania |
| ![ Przycisk generowania statystyk wydajności](./media/user-guide/screen_shot_16.png)       | Generuj statystyki wydajności |
| ![Przycisk Wygeneruj użycie stosu wątku](./media/user-guide/screen_shot_17.png)       | Generuj użycie stosu wątków |
| ![Przycisk wyświetlania wybranego zdarzenia](./media/user-guide/screen_shot_18.png)       | Wyświetl aktualnie wybrane zdarzenie |
| ![Wyszukiwanie przycisku](./media/user-guide/screen_shot_19.png)      | Wyszukaj zdarzenia |
| ![Przycisk Powiększ](./media/user-guide/screen_shot_20.png)      | Powiększ. |
| ![Przycisk powiększenia ekranu](./media/user-guide/screen_shot_21.png)      | Wybierz procent powiększenia ekranu, gdzie 100% oznacza, że cały plik śledzenia jest wyświetlany w bieżącym widoku. |
| ![Przycisk Powiększ](./media/user-guide/screen_shot_22.png)      | Pomniejsz. |
| ![Przycisk wybierania pierwszego zdarzenia](./media/user-guide/screen_shot_23.png)      | Wybierz pierwsze zdarzenie. |
| ![Przycisk wyświetlania poprzedniej strony zdarzenia](./media/user-guide/screen_shot_24.png)      | Wyświetl poprzednią stronę zdarzeń. |
| ![Wyświetl Poprzedni przycisk zdarzenia](./media/user-guide/screen_shot_25.png)      | Wyświetl poprzednie zdarzenie. |
| ![Następny/Poprzedni przycisk nawigacji](./media/user-guide/screen_shot_26.png)      | Określ, jak działają następne/poprzednie przyciski nawigacji. Jeśli ***Event** _ jest zaznaczone, Nawigacja odbywa się na następnym/powyższym zdarzeniu. W przypadku wybrania _*_kontekstu_*_ nawigacja jest wykonywana na następnym/powyższym zdarzeniu w określonym kontekście. Jeśli wybrano _*_obiekt_*_ , Nawigacja odbywa się na następnym/powyższym zdarzeniu określonego obiektu; na przykład zdarzenia skojarzone z określoną kolejką. Jeśli wybrane są _*_przełączniki_*_ , Nawigacja odbywa się na następnej/poprzedniej zmianie w kontekście. Jeśli została wybrana wartość _ *_ID_**, Nawigacja odbywa się w następnym/poprzednim zdarzeniu określonego identyfikatora zdarzenia. |
| ![Przycisk wyświetlania następnego zdarzenia](./media/user-guide/screen_shot_27.png)      | Wyświetl następne zdarzenie. |
| ![Przycisk wyświetlania następnej strony zdarzenia](./media/user-guide/screen_shot_28.png)      | Wyświetl następną stronę zdarzeń. |
| ![Przycisk wybierania ostatniego zdarzenia](./media/user-guide/screen_shot_29.png)      | Wybierz ostatnie zdarzenie. |

## <a name="display-mode-tabs"></a>Karty trybu wyświetlania

TraceX wyświetla zdarzenia systemowe na dwa różne sposoby: *sekwencyjny* i *czas względny*. Domyślny tryb jest sekwencyjny i jest trybem pokazanym na **rysunku 8**.

Zmiana trybu jest prosta, ponieważ wybierasz karty ***Widok sekwencyjny** _ lub _*_godzina_*_ w oknie TraceX. _*Rysunek 8** pokazuje karty **_sekwencyjny widok_*_ i _ *_godzina_**.

![Zrzut ekranu przedstawiający karty Widok sekwencyjny i widok czasu.](./media/user-guide/screen_shot_30.png)

**RYSUNEK 8.**

## <a name="sequential-view-mode"></a>Tryb widoku sekwencyjnego

Tryb widoku sekwencyjnego jest wybierany przez kartę ***sekwencyjny widok** _ przedstawiony w _ * rysunek 8 * *. Jest to tryb domyślny. W tym trybie do zdarzeń są wyświetlane wiadomości błyskawiczne. /mediately od siebie, niezależnie od czasu, jaki upłynął. Zwróć uwagę na również linijkę powyżej obszaru wyświetlania na **rysunku 8**. Pokazuje względny numer zdarzenia od początku śledzenia.

Ten tryb jest trybem domyślnym i jest przydatny do uzyskania dobrego omówienia tego, co się dzieje w systemie.

## <a name="time-view-mode"></a>Tryb widoku czasu

Tryb widoku czasu jest wybierany przez przycisk ***czas** _. _ *Rysunek 9** pokazuje ten sam ślad zdarzenia co **rysunek 8** z wyjątkiem trybu widoku czasu. W tym trybie zdarzenia są wyświetlane w sposób względny, a pełny zielony pasek służy do wyświetlania wykonywania między zdarzeniami. Ten tryb jest przydatny do sprawdzenia, gdzie odbywa się przetwarzanie zbiorcze w systemie, co może ułatwić deweloperom dostrajanie systemu w celu zwiększenia wydajności i/lub czasu odpowiedzi.

![Zrzut ekranu przedstawiający kartę Widok czasu.](./media/user-guide/screen_shot_31.png)

**RYSUNEK 9.**

Zwróć uwagę na to, że na **rysunku 9** zostanie również wyświetlona linijka powyżej zdarzenia. Ta linijka pokazuje względne Takty od początku śledzenia, jak wynika z sygnatury czasowej przystosowanej do rejestrowania śledzenia zdarzeń w programie ThreadX. Jeśli sygnatury czasowe są zbyt bliskie (czasomierz o niskiej częstotliwości), zdarzenia zostaną uruchomione razem. Odwrotnie, jeśli sygnatury czasowe są zbyt daleko od siebie (czasomierz o wysokiej częstotliwości), zdarzenia będą zbyt daleko od siebie. Wybór sygnatury czasowej właściwej częstotliwości jest ważnym zagadnieniem w przypadku, gdy widok względny czasowo ma znaczenie.

## <a name="system-summary-line"></a>Wiersz podsumowania systemu

TraceX udostępnia również pojedynczy wiersz podsumowania (górny kontekst na **rysunku 10**) obejmujący wszystkie zdarzenia w tym samym wierszu. Dzięki temu można łatwo zapoznać się z omówieniem złożonego systemu. Pasek podsumowania jest szczególnie korzystny w systemach, które mają wiele wątków. Bez takiego wiersza podsumowania należy wykonać złożone interakcje systemowe przy użyciu pionowego paska przewijania, aby postępować zgodnie z kontekstem wykonania.

![Zrzut ekranu przedstawiający wiersz podsumowanie systemu na karcie Widok sekwencyjny.](./media/user-guide/screen_shot_32.png)


**RYSUNEK 10**

Wiersz podsumowania zawiera podsumowanie kontekstu oraz odpowiednie podsumowanie zdarzeń poniżej. W przykładzie pokazanym na **rysunku 10** można łatwo sprawdzić, czy **_wątek 2_*_ jest wykonywany i przerwany. Przerwanie powoduje przeprowadzenie przez _*_wątku 3_**, ***wątku 6** _, _*_wątku 4_*_ i _*_wątku 7_*_, po którym zostanie wznowione wykonywanie *_wątku 2_**.

## <a name="system-contexts"></a>Konteksty systemu

TraceX wyświetla konteksty systemowe po lewej stronie ekranu, jak pokazano na **rysunku 11**. Zdarzenia, które wystąpiły w określonym kontekście, są wyświetlane w linii poziomej z prawej strony tego kontekstu. W ten sposób można łatwo ustalić, który kontekst wystąpił zdarzenie, a także obserwować ten wiersz kontekstu, aby zobaczyć wszystkie zdarzenia, które wystąpiły w określonym kontekście.

Pierwsze wpisy kontekstu ciągnięcia to zawsze ***Interrupt** _ i _*_Initialize/bezczynnych_*_ kontekstów. Kontekst _*_przerwania_*_ reprezentuje wszystkie zdarzenia systemowe wykonane z procedur usługi przerwania (IRS). Kontekst _*_inicjalizacji/bezczynności_*_ reprezentuje dwa konteksty w ThreadX. Zdarzenia, które wystąpiły w trakcie _*_tx_application_define_*_, są kontekstem _*_inicjalizacji/bezczynności_*_ . Jeśli system jest bezczynny i w związku z tym nie są wykonywane żadne zdarzenia, zielony pasek reprezentujący _*_uruchomienie_*_ w widoku Time jest rysowany w kontekście _ *_Initialize/Idle_**.

![Zrzut ekranu kontekstów systemu po lewej stronie ekranu.](./media/user-guide/screen_shot_33.png)

**RYSUNEK 11**

W przykładzie na **rysunku 11** znajdują się dziewięć kontekstów wątków, rozpoczynając od **_wątku czasomierza systemowego_*_ kontekstu. Dodatkowe informacje o pojedynczym kontekście są dostępne przez umieszczenie myszy w tym kontekście. Informacje dodatkowe obejmują początkowy wątek wątku, końcowy adres stosu, łączny rozmiar, procent użycia, względny procent wykonania, liczbę wstrzymania, wznowienia i jego najwyższy i najniższy priorytet podczas śledzenia. _* Ilustracja 12** przedstawia informacje dotyczące **_wątku 0_**.

![Zrzut ekranu przedstawiający informacje dotyczące wątku 0.](./media/user-guide/screen_shot_34.png)


**RYSUNEK 12**

Konteksty mogą być również przenoszone do grupy o większym stopniu zainteresowania. Jest to realizowane przez przeciąganie i upuszczanie kontekstu lub kliknięcie prawym przyciskiem myszy kontekstu. Kliknięcie prawym przyciskiem myszy kontekst powoduje wyświetlenie okna dialogowego służącego do przesuwania kontekstu do góry lub do dołu. 

Wybranie pozycji ***Przenieś do góry** _ powoduje przeniesienie kontekstu _*_wątku 3_*_ na początek listy kontekstowej, jak pokazano w _ * Rysunek 13 * *.

![Zrzut ekranu przedstawiający kontekst przeniesiony na początek listy kontekstowej.](./media/user-guide/screen_shot_35.png)


**RYSUNEK 13**

## <a name="thread-status-information"></a>Informacje o stanie wątku

Po włączeniu TraceX wyświetla stan każdego wątku za pośrednictwem kolorowego wiersza w kontekście wątku. Zielona linia wskazuje, że wątek jest w stanie "gotowe", podczas gdy linia dowolnego innego koloru wskazuje, że wątek jest zawieszony. W przypadku zawieszonych wątków kolor linii wskazuje typ obiektu ThreadX, w którym jest wstrzymany wątek. Na przykład na **rysunku 13** zielony wiersz w **_kontekście wątku czasomierza systemowego_,*rozpoczynając od zdarzenia 147 pokazuje, że _* jest gotowy _wątek czasomierza systemowego_ _ *. Przed zdarzeniem 147 i po zdarzeniu 154 brak zielonego wiersza wskazuje, że _* jest gotowy _wątek czasomierza systemowego_*_. Przed zdarzeniem 147 i po zdarzeniu 154 brak zielonego wiersza wskazuje* na wstrzymanie _wątku czasomierza systemu_ _** .

![Zrzut ekranu przedstawiający stan każdego wątku za pośrednictwem kolorowego wiersza w kontekście wątku.](./media/user-guide/screen_shot_36.png)

**RYSUNEK 14**

Istnieją trzy tryby wyświetlania stanu wątku, które są dostępne w menu ***Options->**. Opcja _*_tylko gotowe_*_ pokazuje tylko gotowe (zielone) linie stanu, ale nie wyświetla żadnych wierszy stanu zawieszenia. Jest to opcja domyślna dla TraceX. Opcja _ *_All on_** włącza wyświetlanie wszystkich linii stanu (gotowych i zawieszeń).

Na koniec opcja ***wszystkie*** wyłącza powoduje wyłączenie wyświetlania wszystkich wierszy stanu.

## <a name="event-information-display"></a>Wyświetlanie informacji o zdarzeniach

TraceX zawiera szczegółowe informacje na temat niektórych zdarzeń czasu wykonywania 600, w tym ThreadX, FileX, NetX, NetX Duo i wywołań interfejsu API USBX oraz zdarzeń wewnętrznych. TraceX obsługuje także do dodatkowych unikatowych zdarzeń zdefiniowanych przez użytkownika 61 439.

Bez względu na to, czy jest zaznaczony tryb wyświetlania sekwencyjne i czasowe, wskaźnik myszy nad dowolnym zdarzeniem w obszarze wyświetlania powoduje wyświetlenie szczegółowych informacji o zdarzeniu wyświetlanych blisko zdarzenia. Wskaźnik myszy nad wydarzeniem 143 w pliku śledzenia ***demo_threadx. TRX** _ zostanie wyświetlony w _ * rysunek 15 * *:

![Zrzut ekranu przedstawiający wskaźnik myszy nad zdarzeniem 143 w przykładowym pliku śledzenia](./media/user-guide/screen_shot_37.png)

**RYSUNEK 15**

Każde wyświetlane zdarzenie zawiera informacje standardowe o wartości ***Context** _ i zarówno w _*_względnym czasie_*_ , jak i w _*_sygnaturze czasowej_*_. Pole kontekstowe pokazuje, jakiego kontekstu miało miejsce zdarzenie. Istnieje dokładnie cztery konteksty: wątek, bezczynny, ISR i Inicjalizacja. Po umieszczeniu zdarzenia w kontekście wątku nazwa wątku i jego priorytet w tym czasie są zbierane i wyświetlane, jak pokazano powyżej. _*_Czas względny_*_ pokazuje względną liczbę cykli czasomierza od początku śledzenia. _ *_Pierwotna sygnatura czasowa_** zawiera pierwotne źródło czasu dla zdarzenia. Na koniec zostaną wyświetlone wszystkie informacje specyficzne dla zdarzenia. Te informacje są szczegółowo opisane w dalszej części tego rozdziału.

Szczegółowe informacje o zdarzeniu są również dostępne przez dwukrotne kliknięcie dowolnego zdarzenia. Dwukrotne kliknięcie zdarzenia 143 przedstawiono na **rysunku 16**:

![Zrzut ekranu przedstawiający szczegółowe informacje o zdarzeniu po dwukrotnym kliknięciu zdarzenia.](./media/user-guide/screen_shot_38.png)

**RYSUNEK 16**

Jednoczesne wyświetlanie wielu zdarzeń daje użytkownikowi znacznie bogatszy widok tego, co się stało. Oglądanie ich obok siebie jest bardzo przydatne, ponieważ wiele zdarzeń jest wzajemnie powiązanych. Jest to realizowane przez dwukrotne kliknięcie wielu zdarzeń.

## <a name="current-event-display"></a>Bieżące Wyświetlanie zdarzeń

TraceX wyświetla bieżące zdarzenie — w osobnym oknie — w przypadku wybrania przez użytkownika za pośrednictwem ***widoku — > bieżące zdarzenie*** lub klikając przycisk bieżące zdarzenie na pasku narzędzi. Po wybraniu TraceX Wyświetla aktualnie wybrane zdarzenie w oknie autonomicznym i odświeża to okno za każdym razem, gdy zostanie wybrane inne zdarzenie.

## <a name="event-searching"></a>Wyszukiwanie zdarzeń

TraceX zapewnia rozbudowaną funkcję wyszukiwania zdarzeń. Pola Identyfikator zdarzenia i informacje każdego zdarzenia są głównymi parametrami wyszukiwania. Nie określono wartości parametru Search wskazuje, że parametr skutecznie usuwa ten parametr z wyszukiwania. Ponadto wyszukiwanie może być wykonywane w taki sposób, że każdy znaleziony parametr będzie spełniał wyszukiwanie, lub wszystkie parametry muszą zostać znalezione, aby spełnić kryteria wyszukiwania. Wyszukiwanie może być również ograniczone do określonego kontekstu lub obejmować wszystkie konteksty śledzenia. Wywoływanie wyszukiwania zdarzeń można wykonać, wybierając przycisk ***Wyszukaj według wartości** _ na pasku narzędzi, jak pokazano na stronie _* rysunek 17 * *. Po wybraniu wyświetla się okno dialogowe wyszukiwania, które określa wszystkie parametry wyszukiwania. Przyciski **_dalej_*_ i _*_Wstecz_*_ w oknie dialogowym wyszukiwania można następnie użyć, aby znaleźć następne i poprzednie zdarzenia zgodne z określonymi kryteriami wyszukiwania. _ *Ilustracja 17** wyświetla okno dialogowe wyszukiwania.

![Zrzut ekranu przedstawiający wyszukiwanie zdarzeń.](./media/user-guide/screen_shot_39.png)

**RYSUNEK 17**

![Zrzut ekranu przedstawiający okno dialogowe wyszukiwania.](./media/user-guide/screen_shot_40.png)

**RYSUNEK 18**

## <a name="zooming-in-and-out"></a>Powiększanie i pomniejszanie

Domyślnie TraceX wyświetla zdarzenia w ich pełnym rozmiarze. W razie potrzeby możesz powiększyć lub pomniejszyć. Powiększanie jest przydatne, aby zobaczyć ogólne zdarzenia przechwycone w ślad, natomiast powiększanie jest przydatne w warunkach, w których zdarzenia nakładają się z powodu rozpoznania źródła sygnatury czasowej. **Rysunek 19** przedstawia plik **_demo_threadx. TRX_** , który został powiększony, aby pokazywać 100% pliku śledzenia.

![Zrzut ekranu przedstawiający przykładowy plik, który został powiększony, aby pokazywać 100% pliku śledzenia.](./media/user-guide/screen_shot_41.png)

**RYSUNEK 19.**

W przypadku powiększania o 100%, aby pokazać cały ślad w obrębie bieżącej strony wyświetlania, można łatwo zobaczyć wszystkie uruchomienia kontekstu przechwycone w ślad, a także ogólne zdarzenia występujące w tych kontekstach. Zwróć uwagę na **rysunek 16** , że **_wątki 1_*_ i _*_2_** są wykonywane najczęściej. Niebieskie kolorowanie swoich zdarzeń sugeruje również, że te wątki powodują wywołania usługi kolejki (zdarzenia w kolejce są niebieskie w kolorze).

Przywracanie do widoku pełnej ikony jest równie proste; Przycisk powiększania może być wybierany wielokrotnie lub może zostać wprowadzony jakiś współczynnik 100.

## <a name="delta-ticks-between-events"></a>Takty różnic między zdarzeniami

Określanie liczby taktów między różnymi zdarzeniami w TraceX jest proste — kliknij zdarzenie początkowe i przeciągnij wskaźnik myszy do końcowego zdarzenia. Liczba różnic między zdarzeniami jest wyświetlana w prawym górnym rogu ekranu, jak pokazano na **rysunku 17**.

![Zrzut ekranu przedstawiający liczbę cykli między zdarzeniami.](./media/user-guide/screen_shot_42.png)

**RYSUNEK 17**

Cykle różnicowe pokazane na **rysunku 17** pokazują, że 5032 Takty upłynęło między zdarzenie 125 a zdarzenie 154. Można to również obliczyć ręcznie, sprawdzając względne sygnatury czasowe w każdym zdarzeniu i odejmując, ale przy użyciu graficznego interfejsu użytkownika jest to proste i natychmiastowe.

## <a name="actual-time-display"></a>Rzeczywiste wyświetlanie czasu

Gdy ta funkcja jest włączona, TraceX wyświetla rzeczywisty czas w mikrosekundach w ***widoku czasu** _ i dla różnych informacji czasu różnicowego wyświetlanych przez TraceX. Domyślnie wyświetlacz czasu rzeczywistego jest wyłączony. Aby włączyć rzeczywistą wartość wyświetlania czasu, liczba taktów na mikrosekundowych musi być wprowadzona za pośrednictwem *_opcji _ opcje-> Takty na mikrosekundowych_** (wartość do wprowadzenia jest określana przez źródło czasomierza sprzętowego używane dla rejestrowania zdarzeń TraceX na serwerze docelowym).

## <a name="priority-inversions"></a>Priorytetowe wersje

TraceX automatycznie wyświetla wersje priorytetu wykryte w pliku śledzenia. Priorytetowe wersje są definiowane jako warunki, w których wątek o wyższym priorytecie jest blokowany, próbując uzyskać element mutex, który jest obecnie własnością wątku o niższym priorytecie. Ten warunek jest *deterministyczny*, ponieważ system został skonfigurowany w taki sposób, aby działał w ten sposób. Aby poinformować użytkownika, TraceX pokazuje zakres niewersji priorytetu *deterministyczny* jako jasny kolor łososia.

TraceX również wyświetla w *niedeterministycznych* wersjach priorytetów. Te wersje nie różnią się od priorytetu *deterministycznych* wersji, w których inny wątek o innym poziomie priorytetu został wykonany w połowie nieużywanej *wersji priorytetu* , co sprawia, że czas w nieokreślonym priorytecie jest nieco *Niedeterministyczny*. Ten stan jest często nieznany dla użytkownika i może być bardzo istotny. Aby ostrzec użytkownika o tym stanie, TraceX wyświetla *niedeterministyczne* wersje priorytetowe jako jaśniejszy kolor łososia. **Ilustracja 18** pokazuje *deterministyczne* i *niedeterministyczne* w wersji priorytetowej.

![Zrzut ekranu przedstawiający wersję priorytetu w pliku śledzenia.](./media/user-guide/screen_shot_43.png)

**RYSUNEK 18**

Na **rysunku 18** przedstawiono *nieprawidłową wersję* priorytetu z zdarzenia 398 za pośrednictwem zdarzenia 402. W tym zakresie, bloki o wyższym priorytecie ***Thread 0** _ w elemencie mutex należącym do wątku o niższym priorytecie _*_1_*_. W przypadku zdarzenia 402, _ *_wątek 1_** zwalnia element mutex i w ten sposób zamyka niewersję priorytetu.

Jaśniejszy obszar zawiera *niedeterministyczną* wersję priorytetu między zdarzeniem 408 za pomocą zdarzenia 420. Co sprawia, że w *przypadku* , gdy ***wątek 1** _ ma zablokowany obiekt mutex o wyższym priorytecie _*_0_*_ , występuje przerwanie, które wznawia działanie _ *_wątku 2_* *, które następnie wykonuje i wydłuża czas braku wersji systemu. Ten stan może być bardzo poważny i trudny do zidentyfikowania; Jednak dzięki TraceX jest on łatwo identyfikowany.
