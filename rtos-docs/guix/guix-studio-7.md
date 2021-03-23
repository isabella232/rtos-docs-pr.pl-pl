---
title: Definiowanie przepływu ekranu
description: Program GUIX Studio obsługuje automatyczne generowanie i wykonywanie logiki przejścia ekranu.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1c590725281c785181bcb4c5852346bc973c24d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822201"
---
# <a name="chapter-7-defining-screen-flow"></a>Rozdział 7: Definiowanie przepływu ekranu

Program GUIX Studio obsługuje automatyczne generowanie i wykonywanie logiki przejścia ekranu. Użytkownik definiuje logikę przejścia ekranu, tworząc i edytując diagram przepływu graficznego. Gdy diagram przepływu ekranu zostanie dodany do projektu, włącza dwie ważne funkcje: 1) aplikacja może być wykonywana z poziomu programu Studio i 2) Studio automatycznie generuje programy obsługi zdarzeń i logikę przejścia ekranu, aby zaimplementować wyznaczony przepływ ekranu w wygenerowanym pliku specyfikacji. c, usuwając ten ciężar z programu aplikacji. 

Uruchamianie aplikacji na pulpicie z poziomu środowiska Studio jest użyteczną funkcją, która oszczędza czas, w którym nie jest wymagane przechodzenie przez cykl kompilowania/łączenia w celu wykonania aplikacji. Istnieją ograniczenia kursowe, które można wykonać bez kompilowania aplikacji. Niestandardowe funkcje rysowania, niestandardowe programy obsługi zdarzeń i skomplikowane obsłudze zdarzeń nie są dostępne podczas uruchamiania aplikacji z poziomu środowiska GUIX Studio. Nadal ta funkcja umożliwia automatyczne generowanie logiki przejścia ekranu i animacji programów do przechodzenia z jednego ekranu do drugiego. Te efekty i animacje można zaobserwować bezpośrednio w środowisku GUIX Studio.

Należy pamiętać, że podczas definiowania przepływu ekranu, wyzwalaczy i akcji, które opisano w poniższych akapitach, nie tylko włączysz wykonywanie interfejsu użytkownika z poziomu środowiska Studio, ale włączasz także GUIX Studio do generowania logiki w pliku specyfikacji, który będzie obsługiwał zdarzenia i podejmować działania na podstawie tych zdarzeń, takich jak przejście z jednego ekranu do drugiego.

## <a name="configuring-screen-flow"></a>Konfigurowanie przepływu ekranu

Aby można było wykonać aplikację z poziomu środowiska Studio, należy zdefiniować kilka rzeczy. Najpierw należy sprawdzić ekran najwyższego poziomu lub ekrany, które powinny być wyświetlane podczas uruchamiania programu, wybierając Właściwość "widoczne przy uruchomieniu" w widoku właściwości Studio. Ta flaga wskazuje, że ten ekran powinien być początkowo wyświetlany podczas uruchamiania programu. W razie potrzeby może istnieć więcej niż jeden ekran.

Po zdefiniowaniu ekranu, które są widoczne podczas uruchamiania, użytkownik może zdefiniować sposób przepływu aplikacji interfejsu użytkownika z ekranu do ekranu. Program GUIX Studio udostępnia graficzny Diagram przepływu na potrzeby definiowania logiki przejścia ekranu. Po prostu wybierz menu wyboru ***Konfiguracja, przepływ ekranu** _, aby wyświetlić okno dialogowe edycji przepływu ekranu, zobacz zrzut ekranu w _ *_rysunek 30_* *.

![Zrzut ekranu okna dialogowego przepływu ekranu programu GUIX Studio.](./media/guix-studio/config_screen_flow.png)

**Rysunek 30**

Każdy ekran najwyższego poziomu zdefiniowany w projekcie będzie wyświetlany jako pole zawierające nazwę ekranu. To pole jest symbolem zastępczym reprezentującym każdy ekran najwyższego poziomu zdefiniowany w projekcie. Te pola można przenosić i zmieniać ich rozmiar odpowiednio do potrzeb. Gdy zostało zdefiniowane przejście z jednego ekranu najwyższego poziomu do innego, zostanie wyświetlona linia połączenia z grotem strzałki między dwoma ekranami, aby wskazać przejścia z jednego ekranu do drugiego.

Widok drzewa po lewej stronie diagramu przepływu ekranu pokazuje każdy ekran najwyższego poziomu i można wybrać, które ekrany najwyższego poziomu mają być rysowane na diagramie przepływu ekranu.

Diagram przepływu ekranu jest przewijany. Możesz przeciągnąć dowolny blok ekranu w dół i bezpośrednio poza widocznym obszarem, aby powiększyć przewijane okno. Po powiększeniu okna przewijania możesz pomniejszyć, aby dopasować go do widocznego obszaru przez przewinięcie kółka myszy w dół. Jeśli okno przewijania jest powiększone, można je odpowiednio przechowywać, aby pomieścić wszystkie bloki, przewijając kółko myszy.

Aby zdefiniować przejścia dla ekranu, kliknij prawym przyciskiem myszy symbol zastępczy dla tego ekranu, aby wyświetlić okno dialogowe Edytowanie listy wyzwalaczy, zobacz ***rysunek 31***.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie listy wyzwalaczy GUIX Studio.](./media/guix-studio/edit_trigger_list.png)

**Rysunek 31**

Okno dialogowe Edytowanie wyzwalacza zawiera listę zdarzeń zdefiniowanych przez użytkownika, które będą wyzwalać przejście ekranu, co oznacza, że są wywoływane te wyzwalacze zdarzeń. Wyzwalacze są zwykle sygnałami wygenerowanymi przez jeden lub więcej podrzędnych elementów widget wybranego ekranu.

Aby zdefiniować nowy wyzwalacz, wybierz przycisk ***Dodaj nowy wyzwalacz** _ w oknie dialogowym Edytowanie listy wyzwalaczy, aby wyświetlić okno dialogowe Dodawanie wyzwalacza wyświetlone w _ *_rysunek 32_* *.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie wyzwalacza programu GUIX Studio.](./media/guix-studio/add_trigger_for.png)

**Rysunek 32**

Można zdefiniować typ zdarzenia, który będzie wyzwalał nowy zestaw akcji i definiuje akcje, które zostaną wykonane po odebraniu zdarzenia wyzwalacza.

Po zdefiniowaniu typu zdarzenia, który ma być używany do wyzwalania nowego przejścia ekranu animacji, Zapisz ten nowy wyzwalacz i będzie on wyświetlany w oknie dialogowym Edytowanie listy wyzwalaczy.

Możesz zmodyfikować to zdarzenie (bez modyfikowania powiązanych akcji, które mają zostać wykonane) przez wybranie zdarzenia w oknie dialogowym Edytowanie listy wyzwalaczy i wybranie przycisku ***Edytuj zdarzenie wyzwalacza*** .

Analogicznie, możesz usunąć każde zdarzenie wyzwalacza z listy, wybierając zdarzenie i klikając przycisk ***Usuń wybrane wyzwalacze*** .

Aby określić animację lub przejście ekranu, które powinny być wykonywane na podstawie określonego zdarzenia wyzwalacza, zaznacz to zdarzenie wyzwalacza i kliknij przycisk ***Edytuj akcje*** . Należy zauważyć, że można wyłączyć więcej niż jedną akcję na podstawie każdego zdefiniowanego wyzwalacza.

Przycisk **Edytuj** akcje wyświetla okno dialogowe Edytowanie akcji dla wyzwalacza, pokazane na rysunku 33: 

![Zrzut ekranu przedstawiający okno dialogowe akcji edytowania GUIX Studio dla wyzwalacza.](./media/guix-studio/edit_actions_for_trigger.png)

**Rysunek 33**

To okno dialogowe pozwala zdefiniować dowolną liczbę akcji do wdrożenia na podstawie tego zdarzenia wyzwalacza. Można nadać każdej akcji zrozumiałą nazwę ułatwiającą kojarzenie każdej definicji akcji z animacją wizualną lub przejściem. W powyższym przykładzie zdefiniowano dwie akcje o nazwie "fade_in_text_screen" i "fade_out_button_screen".

Zdefiniuj nową akcję do wdrożenia, a następnie kliknij przycisk Dodaj nową akcję, który wyświetla okno dialogowe Wybieranie akcji, rysunek 34:

![Zrzut ekranu przedstawiający okno dialogowe akcja wybierania GUIX Studio.](./media/guix-studio/select_action.png)

**Rysunek 34**

Dostępne typy akcji obejmują:

- **Animacja**: Rozpocznij animację z określonymi informacjami.
- **Dołącz**: dołączanie ekranu docelowego do ekranu nadrzędnego, jeśli nie określono ekranu nadrzędnego, ekran docelowy zostanie dołączony do okna głównego.
- **Odłącz**: Odłącz ekran docelowy od jego elementu nadrzędnego.
- **Ukryj**: ukrywa ekran docelowy.
- **Punkt pop stosu ekranu**: wyskakujący ekran z wewnętrznego stosu ekranu.
- **Wypychanie stosu ekranu**: wypchnij wskaźnik ekranu do wewnętrznego stosu ekranu.
- **Resetowanie stosu ekranu**: Usuń wszystkie wskaźniki ekranu z wewnętrznego stosu ekranu.
- **Pokaż**: Pokaż ekran docelowy.
- **Przełącznik**: dołączanie ekranu docelowego do elementu nadrzędnego bieżącego ekranu i odłączanie bieżącego ekranu od jego elementu nadrzędnego.
- **Wykonanie okna**: modalnie wykonuje ekran docelowy.
- **Zatrzymaj wykonywanie okna**: zamyka modalne wykonywanie bieżącego ekranu.

Po zdefiniowaniu akcji do wykonania na podstawie wybranego zdarzenia wyzwalacza ta akcja zostanie wyświetlona w oknie dialogowym Edytowanie akcji dla wyzwalacza. Możesz wybrać tę akcję, aby zmodyfikować parametry tej akcji, jak pokazano na rysunku 35.

![Zrzut ekranu przedstawiający okno dialogowe akcji edytowania GUIX Studio dla wyzwalacza.](./media/guix-studio/edit_actions_for_trigger.png)

**Rysunek 35**

Jeśli typ akcji jest animacją, zestaw parametrów animacji jest wyświetlany po prawej stronie, aby umożliwić zdefiniowanie animacji typu slajd i/lub zanikanie do wykonania. Gdy akcja animacji zostanie zakończona, można także określić, czy animacja ma być automatycznie odłączona od elementu nadrzędnego i/lub wypychana do wewnętrznego stosu ekranu, która jest często przydatna podczas definiowania wielowarstwowych systemów menu.

W przypadku animacji przesuwania i zanikania można także zdefiniować funkcję krzywych napięcia, która ma być używana, wybierając przycisk "krzywa napięcia". Funkcja krzywych napięcia ma różne krzywe zaprojektowane w celu dokładniejszego naśladowania rzeczywistych zdarzeń związanych z ruchem. Wybranie tego przycisku powoduje wyświetlenie okna dialogowego **Wybieranie funkcji napięcia** , rysunek 36:

![Zrzut ekranu przedstawiający okno dialogowe wyboru funkcji krzywych GUIX Studio.](./media/guix-studio/easing_function_select.png)

**Rysunek 36**

Jeśli definiujesz wiele akcji do skojarzenia z jednym zdarzeniem wyzwalacza, może być przydatne przypisanie każdej akcji zrozumiałej nazwy. Nazwy akcji muszą być zgodne z regułami nazewnictwa składni języka C, ponieważ te nazwy będą używane w wygenerowanym pliku specyfikacji do definiowania tabel zdarzeń i akcji.

Podczas definiowania zdarzeń wyzwalacza i akcji w programie GUIX Studio automatyczne programy obsługi zdarzeń są generowane w pliku specyfikacji projektu w celu obsługi tych zdarzeń i wykonywania określonych akcji. Oznacza to, że nie musisz obsługiwać tych zdarzeń w kodzie aplikacji, chociaż zdarzenia wyzwalacza są nadal przesyłane do żadnych zdefiniowanych niestandardowych programów obsługi zdarzeń. Innymi słowy, wygenerowane przez Studio programy obsługi zdarzeń rozszerzają, a nie zastępują, własne niestandardowe programy obsługi zdarzeń.

## <a name="running-the-application"></a>Uruchamianie aplikacji

Po utworzeniu ekranów uruchamiania i diagramu przepływu ekranu można uruchomić aplikację w programie Studio, wybierając pozycję "Uruchom aplikację".

![Zrzut ekranu przedstawiający przycisk Uruchom aplikację.](./media/guix-studio/image68.jpg)

na pasku narzędzi, wybierz pozycję Edytuj | Uruchom aplikację z menu Projekt lub wybierając przycisk Run (Uruchom) w dolnej części okna dialogowego Edytowanie przepływu ekranu.

Po uruchomieniu aplikacji zobaczysz ekran, który został wyznaczony jako "widoczny podczas uruchamiania" w nowym oknie. Elementy widget podrzędne na tym ekranie są w pełni funkcjonalne. Można klikać przyciski, obsługiwać suwaki i przesuwać koła itp. Jeśli zdefiniowano niestandardowe funkcje rysowania lub obsługę zdarzeń klienta dla dowolnego z tych elementów widget, w przypadku uruchamiania aplikacji w tym trybie nie będzie można go zobaczyć. Ale jeśli zdefiniowano Diagram przepływu ekranu z zdarzeniami wyzwalania i akcjami, te wyzwalacze będą działać i Twoje ekrany będą przenoszone zgodnie z definicją, w tym wszystkie zdefiniowane animacje.
