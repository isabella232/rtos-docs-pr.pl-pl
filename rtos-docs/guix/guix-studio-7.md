---
title: Definiowanie ekranu Flow
description: Program GUIX Studio obsługuje automatyczne generowanie i wykonywanie logiki przejścia ekranu.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1df90acd86b4446d96a66ab3ee21545afcd9824e28efb40204c2966cb075c501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785613"
---
# <a name="chapter-7-defining-screen-flow"></a>Rozdział 7. Definiowanie Flow

Program GUIX Studio obsługuje automatyczne generowanie i wykonywanie logiki przejścia ekranu. Użytkownik definiuje logikę przejścia ekranu, tworząc i edytując graficzny diagram przepływu ekranu. Po dodaniu diagramu przepływu ekranu do projektu włączane są dwie ważne funkcje: 1) Aplikacja może być wykonywana z poziomu środowiska Studio i 2) Studio automatycznie generuje programy obsługi zdarzeń i logikę przejścia ekranu w celu zaimplementowania wyznaczonego przepływu ekranu w wygenerowanym pliku specifications.c, usuwając to obciążenie z programu aplikacji. 

Uruchamianie aplikacji na pulpicie z poziomu środowiska studio jest przydatną funkcją, która pozwala zaoszczędzić czas dzięki temu, że nie trzeba przechodzić przez cykl kompilowania/łączenia w celu wykonania aplikacji. Oczywiście istnieją ograniczenia dotyczące tego, co można zrobić bez kompilowania aplikacji. Niestandardowe funkcje rysowania, niestandardowe programy obsługi zdarzeń i złożona obsługa zdarzeń nie są dostępne podczas uruchamiania aplikacji z poziomu środowiska GUIX Studio. Mimo to ta funkcja umożliwia automatyczne generowanie logiki przejścia ekranu i wykonywanie animacji programu w celu przejścia z jednego ekranu na inny. Te efekty i animacje można zaobserwować bezpośrednio w środowisku GUIX Studio.

Pamiętaj, że podczas definiowania przepływu ekranu, wyzwalaczy i akcji, które opiszemy w poniższych akapitach, nie tylko umożliwiasz wykonywanie interfejsu użytkownika z poziomu środowiska Studio, ale także umożliwiasz programowi GUIX Studio generowanie logiki w pliku specyfikacji, która będzie obsługiwać zdarzenia i podjąć akcje na podstawie tych zdarzeń.  na przykład przejście z jednego ekranu na inny.

## <a name="configuring-screen-flow"></a>Konfigurowanie ustawień Flow

Aby można było wykonać aplikację w środowisku studio, należy zdefiniować kilka rzeczy. Najpierw należy wskazać ekran najwyższego poziomu lub ekrany, które powinny być wyświetlane podczas uruchamiania programu, wybierając właściwość "Widoczne podczas uruchamiania" w widoku właściwości programu Studio. Ta flaga wskazuje, że ten ekran powinien być początkowo wyświetlany podczas uruchamiania programu. W razie potrzeby więcej niż jeden ekran może mieć to oznaczenie.

Po zdefiniowaniu ekranów, które są widoczne podczas uruchamiania, użytkownik może zdefiniować sposób przepływu aplikacji interfejsu użytkownika z ekranu do ekranu. Program GUIX Studio udostępnia graficzny diagram przepływu ekranu do definiowania logiki przejścia ekranu. Wystarczy wybrać menu ***Konfiguruj,** Ekran Flow _, aby wyświetlić okno dialogowe edycji przepływu ekranu, zobacz zrzut ekranu na rysunku _*_Rysunek 30_**.

![Zrzut ekranu przedstawiający okno dialogowe Flow GUIX Studio.](./media/guix-studio/config_screen_flow.png)

**Rysunek 30**

Każdy ekran najwyższego poziomu zdefiniowany w projekcie będzie wyświetlany jako pole z nazwą ekranu. To pole jest symbolem zastępczym reprezentującym każdy ekran najwyższego poziomu zdefiniowany w projekcie. Te pola można przenosić i zmieniać ich rozmiar zgodnie z potrzebami. Po zdefiniowanym przejściu z jednego ekranu najwyższego poziomu do innego zostanie zdefiniowana linia połączenia ze strzałką między dwoma ekranami wskazująca przejścia między ekranami.

Widok drzewa po lewej stronie diagramu przepływu ekranu przedstawia każdy ekran najwyższego poziomu i można wybrać ekrany najwyższego poziomu, które mają być rysowane na diagramie przepływu ekranu.

Diagram przepływu ekranu można przewijać. Możesz przeciągnąć dowolny blok ekranu w dół i bezpośrednio poza widocznym obszarem, aby powiększyć okno przewijane. Po powiększeniu okna z możliwością przewijania możesz pomniejszyć okno, aby dopasować je do widocznego obszaru, przewijając koło myszy w dół. Jeśli okno przewijane jest pomniejszone, możesz sprawić, że będzie wystarczająco duże, aby pomieścić wszystkie bloki, przewijając kółka myszy w górę.

Aby zdefiniować przejścia dla ekranu, kliknij prawym przyciskiem myszy symbol zastępczy tego ekranu, aby wyświetlić okno dialogowe Edytowanie listy wyzwalaczy, zobacz ***Rysunek 31.***

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie listy wyzwalaczy w programie GUIX Studio.](./media/guix-studio/edit_trigger_list.png)

**Rysunek 31**

W oknie dialogowym edycji wyzwalacza są wyświetlane zdarzenia zdefiniowane przez użytkownika, które wyzwalają przejście ekranu, dlatego wywołujemy wyzwalacze tych zdarzeń. Wyzwalacze to zwykle sygnały generowane przez co najmniej jeden element widget podrzędny wybranego ekranu.

Aby zdefiniować nowy wyzwalacz, wybierz przycisk ***** Dodaj nowy wyzwalacz _ w oknie dialogowym Edytowanie listy wyzwalaczy, aby wyświetlić okno dialogowe Dodawanie wyzwalacza wyświetlane na rysunku _*_Rysunek 32_**.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie wyzwalacza w programie GUIX Studio.](./media/guix-studio/add_trigger_for.png)

**Rysunek 32**

Można zdefiniować typ zdarzenia, który spowoduje wyzwolenie nowego zestawu akcji, i zdefiniować akcje, które zostaną wykonane po otrzymaniu tego zdarzenia wyzwalacza.

Po zdefiniowaniu typu zdarzenia, którego chcesz użyć do wyzwolenia nowego przejścia ekranu animacji, zapisz ten nowy wyzwalacz i będzie on wyświetlany w oknie dialogowym Edytowanie listy wyzwalaczy.

To zdarzenie można zmodyfikować (bez modyfikowania powiązanych akcji, które mają zostać ***wykonane),*** wybierając zdarzenie w oknie dialogowym Edytowanie listy wyzwalaczy i wybierając przycisk Edytuj zdarzenie wyzwalacza.

Podobnie możesz usunąć dowolne zdarzenie wyzwalacza z listy, wybierając zdarzenie i klikając przycisk ***Usuń wybrany wyzwalacz.***

Aby określić animację lub przejście ekranu na podstawie określonego zdarzenia wyzwalacza, wybierz to zdarzenie wyzwalacza i kliknij przycisk ***Edytuj akcje.*** Należy pamiętać, że można wyzwolić więcej niż jedną akcję na podstawie każdego zdefiniowanego wyzwalacza.

Przycisk **Edytuj akcje powoduje** uruchomienie okna dialogowego Edytowanie akcji dla wyzwalacza, jak pokazano na rysunku 33: 

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie akcji wyzwalacza w programie GUIX Studio.](./media/guix-studio/edit_actions_for_trigger.png)

**Rysunek 33**

To okno dialogowe umożliwia zdefiniowanie dowolnej liczby akcji do zaimplementowania na podstawie tego zdarzenia wyzwalacza. Każdą akcję można nadać znaczącej nazwie, aby ułatwić skojarzenie każdej definicji akcji z animacją wizualną lub przejściem. W powyższym przykładzie zdefiniowałyśmy dwie akcje o nazwach "fade_in_text_screen" i "fade_out_button_screen".

Zdefiniuj nową akcję do zaimplementowania, kliknij przycisk Dodaj nową akcję, który powoduje wyświetlone okno dialogowe Wybieranie akcji, Rysunek 34:

![Zrzut ekranu przedstawiający okno dialogowe Wybieranie akcji w programie GUIX Studio.](./media/guix-studio/select_action.png)

**Rysunek 34**

Dostępne typy akcji obejmują:

- **Animacja:** rozpocznij animację z określonymi informacjami.
- **Dołącz:** dołącz ekran docelowy do ekranu nadrzędnego. Jeśli nie zostanie określony ekran nadrzędny, ekran docelowy zostanie dołączony do okna głównego.
- **Odłącz:** odłączanie ekranu docelowego od jego ekranu nadrzędnego.
- **Ukryj:** ukrywa ekran docelowy.
- **Pop stosu ekranu:** Pop ekranu ze stosu ekranu wewnętrznego.
- **Wypychanie stosu ekranu:** wypychanie wskaźnika ekranu do stosu ekranu wewnętrznego.
- **Resetowanie stosu ekranu:** usuń wszystkie wskaźniki ekranu ze stosu ekranu wewnętrznego.
- **Pokaż:** pokaż ekran docelowy.
- **Przełącznik:** dołącz ekran docelowy do elementu nadrzędnego bieżącego ekranu i odłącz bieżący ekran od jego elementu nadrzędnego.
- **Wykonanie okna:** modalnie wykonuje ekran docelowy.
- **Zatrzymaj wykonywanie okna:** zakończ modalne wykonywanie bieżącego ekranu.

Po zdefiniować akcję do podjęcia na podstawie wybranego zdarzenia wyzwalacza ta akcja zostanie wyświetlona w oknie dialogowym Edytowanie akcji dla wyzwalacza. Możesz wybrać tę akcję, aby zmodyfikować parametry tej akcji, jak pokazano na rysunku 35.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie akcji wyzwalacza w programie GUIX Studio.](./media/guix-studio/edit_actions_for_trigger.png)

**Rysunek 35**

Jeśli typ akcji jest animacją, zestaw parametrów animacji jest wyświetlany po prawej stronie, aby umożliwić zdefiniowanie animacji typu slajdu i/lub zanikanie do wykonania. Po zakończeniu akcji animacji można również określić, czy animacja powinna być automatycznie odsełana od elementu nadrzędnego i/lub wypychana do wewnętrznego stosu ekranu, co jest często przydatne podczas definiowania wielowarstwowych systemów menu.

W przypadku animacji suwaka i zanikania można również zdefiniować funkcję easingu do użycia, wybierając przycisk Easing Func Select .... Funkcje easingu to różne krzywe zaprojektowane tak, aby dokładniej naśladować rzeczywiste zdarzenia ruchu. Wybranie tego przycisku powoduje pojawienie się okna dialogowego **Wybieranie funkcji easingu,** Rysunek 36:

![Zrzut ekranu przedstawiający okno dialogowe Wybieranie funkcji easing w programie GUIX Studio.](./media/guix-studio/easing_function_select.png)

**Rysunek 36**

Jeśli definiujesz wiele akcji do skojarzenia z jednym zdarzeniem wyzwalacza, przydatne może być przypisanie każdej akcji znaczącej nazwy. Nazwy akcji muszą być zgodne z regułami nazewnictwa składni języka C, ponieważ te nazwy będą używane w wygenerowanym pliku specyfikacji do definiowania tabel zdarzeń i akcji.

Podczas definiowania zdarzeń wyzwalacza i akcji w programie GUIX Studio automatyczne programy obsługi zdarzeń są generowane w pliku specyfikacji projektu w celu obsługi tych zdarzeń i wykonywania określonych akcji. Oznacza to, że NIE trzeba obsługiwać tych zdarzeń w kodzie aplikacji, chociaż zdarzenia wyzwalacza są nadal przekazywane do dowolnych zdefiniowanych niestandardowych programów obsługi zdarzeń. Innymi słowy, programy obsługi zdarzeń wygenerowane w programie Studio rozszerzają, a nie zastępują własne niestandardowe procedury obsługi zdarzeń.

## <a name="running-the-application"></a>Uruchamianie aplikacji

Po utworzeniu ekranów startowych i diagramu przepływu ekranu możesz uruchomić aplikację w programie Studio, wybierając pozycję "Uruchom aplikację"

![Zrzut ekranu przedstawiający przycisk Uruchom aplikację.](./media/guix-studio/image68.jpg)

na pasku narzędzi, wybierając pozycję Edytuj | Uruchom aplikację z menu projektu lub wybierając przycisk Uruchom w dolnej części okna dialogowego Flow ekranu.

Po uruchomieniu aplikacji w nowym oknie zobaczysz ekrany oznaczone jako "Widoczne podczas uruchamiania". Widżety podrzędne na tych ekranach są w pełni operacyjne. Możesz klikać przyciski, obsługiwać suwaki i przewijać kółka itp. Jeśli zdefiniowano niestandardowe funkcje rysowania lub obsługę zdarzeń klienta dla dowolnego z tych widżetów, oczywiście NIE zobaczysz tego podczas uruchamiania aplikacji w tym trybie. Jeśli jednak zdefiniowano diagram przepływu ekranu ze zdarzeniami i akcjami wyzwalacza, te wyzwalacze będą działać, a ekrany będą się przechodzić zgodnie z definicją, w tym wszelkie animacje, które być może zostały zdefiniowane.
