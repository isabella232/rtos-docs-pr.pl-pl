---
title: Rozdział 3 — Omówienie funkcjonalne GUIX
description: Ten rozdział zawiera omówienie funkcjonalnego interfejsu użytkownika GUIX o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 53ffc900debd3bfaa1a38d792ddf294b2ce92461
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550307"
---
# <a name="chapter-3---functional-overview-of-guix"></a>Rozdział 3 — Omówienie funkcjonalne GUIX

Ten rozdział zawiera omówienie funkcjonalnego interfejsu użytkownika GUIX o wysokiej wydajności. 

## <a name="execution-overview"></a>Przegląd wykonywania

GUIX implementuje model programowania oparty na zdarzeniach. Oznacza to, że platforma GUIX jest przede wszystkim oparta na przyjęciu zdarzeń wypychanych do kolejki zdarzeń GUIX. Przetwarzanie tych zdarzeń odbywa się w kontekście wątku GUIX, który jest wątkiem ThreadX utworzonym podczas inicjowania systemu GUIX.

Aplikacje GUIX definiują interfejs użytkownika przez wywoływanie funkcji interfejsu API GUIX w celu tworzenia widżetów systemu Windows i elementów podrzędnych oraz dostosowywania wyglądu tych widżetów przez wywoływanie dodatkowych funkcji interfejsu API służących do definiowania kolorów, stylów, czcionek i różnych innych atrybutów każdego okna lub typu widżetu. Jeśli używasz programu GUIX Studio do tworzenia wyglądu ekranów interfejsu użytkownika, większość tej pracy wywołującej funkcje interfejsu API GUIX do tworzenia ekranu jest wykonywana przez aplikację GUIX Studio.

Aplikacje GUIX współpracują z użytkownikiem systemu i z zewnętrzną logiką biznesową przez obsługę zdarzeń pobranych z kolejki zdarzeń GUIX.
Te zdarzenia są zwykle tworzone przez GUIX widżety, ale mogą być również tworzone przez wątki zewnętrzne. Po wypchnięciu typowego przycisku GUIX ten przycisk wysyła zdarzenie do okna nadrzędnego przycisku. Program aplikacji będzie działać na tym przycisku, dostarczając procedurę obsługi dla zdarzenia push przycisku.

Dodatkowe wątki GUIX są często tworzone dla takich elementów jak sterowniki wejściowe. Typowy sterownik ekranu dotykowego jest wykonywany jako wątek autonomiczny poza głównym wątkiem GUIX. Sterownik wprowadzania dotykowego wysyła informacje dotykowe do wątku GUIX przez wysyłanie zdarzeń do kolejki zdarzeń GUIX.

Ponieważ wiele operacji interfejsu użytkownika, takich jak animacje wymagają dokładnej informacji o chronometrażu, GUIX implementuje także prosty i łatwy w użyciu interfejs czasomierza. Ten interfejs czasomierza jest oparty na usłudze czasomierza ThreadX i jest konfigurowany automatycznie podczas uruchamiania systemu.

Większość oprogramowania GUIX jest niezależna od wszelkich zależności sprzętowych. Struktura wymaga sprzętowych sterowników wejściowych i sterowników graficznych specyficznych dla sprzętu. Szczegółowe informacje o sposobie implementacji tych sterowników określonych dla sprzętu są odroczone do rozdziału 5.

## <a name="initialization"></a>Inicjalizacja 

***Gx_system_initialize*** usługi musi zostać wywołana przed wywołaniem innej usługi GUIX. Inicjalizację systemu GUIX można wywołać z procedury ThreadX ***tx_application_define*** (kontekstu inicjowania) lub z wątków aplikacji. Funkcja ***gx_system_initialize*** tworzy kolejkę zdarzeń GUIX, inicjuje obiekt Timer GUIX, tworzy główny wątek systemu GUIX i inicjuje różne struktury danych UTRZYMYWANE przez GUIX podczas wykonywania aplikacji.

Po powrocie ***gx_system_initialize*** aplikacja jest gotowa do tworzenia ekranów, kanw, okien, widżetów i dostosowywania właściwości wszystkich obiektów GUIX. Wiele interfejsów API tworzenia obiektów GUIX można wywołać z ***tx_application_define*** lub z wątków aplikacji.

## <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji 

Wywołania z aplikacji są wykonywane w dużej mierze od ***tx_application_define*** (kontekstu inicjowania) lub z wątków aplikacji. Zapoznaj się z sekcją "dozwolone od" każdego interfejsu API GUIX opisanej w rozdziale 4, aby określić kontekst, z którego może zostać wywołana.

W większości przypadków działania z intensywnym przetwarzaniem są odroczone do wewnętrznego wątku GUIX, łącznie z przetwarzaniem zdarzeń oraz rysunkiem widżetu/okna.

Funkcje interfejsu API GUIX mogą być wywoływane z dowolnego wątku w dowolnym momencie.
Jednak zazwyczaj uważa się, że jest to lepsza architektura do rozdzielenia logiki biznesowej o kluczowym znaczeniu dla logiki interfejsu użytkownika. Ponieważ operacje rysowania interfejsu użytkownika mogą czasami zająć dużo czasu, w zależności od rozmiaru ekranu i wydajności procesora, zazwyczaj nie chcesz, aby wątki o kluczowym znaczeniu były opóźnione, oczekując na ukończenie operacji rysowania.

## <a name="internal-guix-thread"></a>Wewnętrzny wątek GUIX 

Jak wspomniano, GUIX ma wewnętrzny wątek, który wykonuje zbiorcze przetwarzanie graficznego interfejsu użytkownika. Ten wątek jest tworzony przez oprogramowanie aplikacji przez wywołanie ***gx_system_initialize** _, a następnie _ *_gx_system_start_* *.

Priorytet wewnętrznego wątku GUIX jest określany przez `#define GX_SYSTEM_THREAD_PRIORITY` . Ta wartość jest domyślnie równa 16 (priorytet środkowy), ale można ją zmodyfikować, określając tę wartość w pliku nagłówkowym gx_port. h lub gx_user. h, zastępując wartość domyślną.

Wycinek czasu wątku GUIX jest w podobny sposób definiowany przez `#define GX_SYSTEM_THREAD_TIMESLICE` , który domyślnie jest wartością 10 ms.

Stos sie przez wątek systemowy jest określany przez `#define GX_THREAD_STACK_SIZE` , który znajduje się w pliku nagłówkowym ***gx_port. h*** , ale może być również przesłonięty przez określenie tej wartości w pliku nagłówkowym gx_user. h.

Wewnętrzna pętla wykonywania wątku GUIX składa się z trzech akcji.
Najpierw GUIX pobiera zdarzenia z kolejki zdarzeń GUIX i wysyła te zdarzenia do przetwarzania przez system Windows i widżety GUIX. Zdarzenia są zazwyczaj wypychane do kolejki zdarzeń GUIX przez okresowe czasomierze, urządzenia wejściowe, takie jak ekran dotykowy lub klawiatura, i przez GUIX widżety same podczas przetwarzania danych wejściowych użytkownika. Następnie po przetworzeniu wszystkich zdarzeń GUIX określa, czy jest wymagane odświeżenie ekranu, a jeśli tak, to wykonuje przetwarzanie niezbędne do zaktualizowania wyświetlanych danych graficznych, głównie przez wywołanie funkcji rysowania tych okien i widżetów, które zostały oznaczone jako zanieczyszczone. Na koniec GUIX zawiesza wątek GUIX do momentu nadejścia nowego zdarzenia wejściowego lub zdarzenia.

## <a name="event-processing"></a>Przetwarzanie zdarzeń 

Zdarzenia wprowadzania dotykowego lub pióra są przetwarzane przez określenie najwyższego okna lub widżetu pod pozycją kolor dotykowy lub pióra wejściowego i wywołanie funkcji przetwarzania zdarzeń tego okna/elementu widget. Jeśli widżet zrozumie zdarzenia wejściowe pióra, będzie przetwarzać zdarzenie zgodnie z odpowiednim typem widżetu. Jeśli nie, widżetu najwyższego poziomu zostanie przekazane Zdarzenie wejściowe dotknięcia lub piórem do elementu nadrzędnego widżetu w celu przetworzenia. To przekazanie zdarzenia w górę łańcucha kontynuuje działanie, dopóki zdarzenie nie zostanie obsłużone lub zdarzenie zostanie odebrane w oknie głównym, w tym przypadku zdarzenie jest odrzucane.

Zdarzenia klawiatury są wysyłane do okna/widżetu, który ma fokus wprowadzania. Stan fokusu wprowadzania jest obsługiwany przez składnik gx_system GUIX.

Zdarzenia czasomierza są zawsze wysyłane do okna lub widżetu, który jest właścicielem czasomierza do przetwarzania.

Wygenerowane wewnętrznie zdarzenia, takie jak zdarzenia kliknięcia lub zdarzenia zmiany wartości suwaka, są zawsze wysyłane do obiektu nadrzędnego widżetu generującego zdarzenie. Jeśli element nadrzędny nie przetwarza zdarzenia, zostanie on przeszukany w łańcuchu podobnym do zdarzeń wejściowych touch lub pióra.

## <a name="drawing"></a>Rysowanie 

Po zakończeniu przetwarzania wszystkich zdarzeń, wewnętrzny wątek GUIX określa, czy jest wymagana jakakolwiek aktualizacja wyświetlania, a jeśli tak, to odpowiednie funkcje rysowania okna/widżetu są wywoływane. Po zakończeniu rysowania, wewnętrzny wątek GUIX po prostu czeka na swoją kolejkę zdarzeń dla następnego zdarzenia GUIX do przetworzenia.

GUIX implementuje koncepcję *zanieczyszczonych obszarów*, które są obszarami, które należy ponownie narysować dla każdego widżetu i kanwy. Widżet może być rysowany tylko w obszarach, które wcześniej zostały oznaczone jako zanieczyszczone. Gdy wywoływana jest funkcja rysowania widżetu, wszystkie operacje rysowania są wewnętrznie przycinane do wcześniej zdefiniowanego, zanieczyszczonego prostokąta.
Próba rysowania poza tym obszarem jest ignorowana.

Widżety i okna są oznaczane jako zanieczyszczone przez wywołanie funkcji interfejsu API ***gx_system_dirty_mark***. Ta funkcja oznacza cały widżet lub okno jako wymagające odrysowania. Druga funkcja, ***gx_system_dirty_partial_add***, może być wywoływana jako alternatywa do oznaczania tylko części okna lub widżetu jako zanieczyszczony.

Ten model oznaczania widżetów jako zanieczyszczony, a następnie przeciągnieć te elementy widget tylko wtedy, gdy wszystkie zdarzenia wejściowe zostały przetworzone jako *odłożone*. Algorytm rysowania odroczonego GUIX i konserwacja listy zanieczyszczonej zaprojektowano w celu poprawy wydajności rysowania. Ponieważ operacje rysowania są zazwyczaj kosztowne, GUIX działa trudno, aby zapobiec niepotrzebnemu rysowaniu.

Rysowanie odbywa się na *kanwie* GUIX. Kanwa to obszar pamięci zarezerwowany do przechowywania danych graficznych. Kanwa może lub nie może być bezpośrednio połączony z buforem klatek sprzętowych, w zależności od architektury systemu i ograniczeń pamięci. Przed wystąpieniem dowolnego rysunku, należy najpierw otworzyć kanwę do rysowania, wywołując funkcję API ***gx_canvas_drawing_initiate*** . Ten interfejs API przygotowuje kanwę do rysowania i ustanowienia bieżącego *kontekstu rysowania*. Gdy GUIX wykonuje odświeżanie kanwy systemu, Kanwa jest otwierana do rysowania i kontekst rysowania ustanowiony przed wywołaniem interfejsów API rysowania na poziomie widżetu. W związku z tym widżety nie muszą inicjować rysowania na kanwie w ramach funkcji rysowania widżetu.

Jeśli jednak aplikacja chce przeprowadzić natychmiastowe rysowanie na kanwie poza przepływem standardowego GUIXego algorytmu rysowania, aplikacja musi bezpośrednio wywołać ***gx_canvas_drawing_initiate*** przed wywołaniem innych funkcji interfejsu API rysowania i musi wywołać ***gx_canvas_drawing_complete*** po zakończeniu natychmiastowego rysowania.

## <a name="user-input"></a>Dane wejściowe użytkownika 

GUIX obsługuje urządzenia dotykowe ekranu, myszy i klawiatury ze wstępnie zdefiniowanymi typami zdarzeń. Dodatkowe urządzenia wejściowe mogą być wykorzystywane przez Definiowanie niestandardowych typów zdarzeń lub mapowanie niestandardowego urządzenia wejściowego na wstępnie zdefiniowane typy zdarzeń.

Akcje skojarzone z tymi urządzeniami są tłumaczone na zdarzenia, które są przetwarzane przez wewnętrzny wątek GUIX. Oprogramowanie na poziomie sterowników przeznaczone do obsługi ekranu dotykowego musi przygotowywać i wysyłać do zdarzeń kolejki zdarzeń GUIX, aby uzyskać pióro, pióro i operacje przeciągania piórem. Analogicznie sterownik wejścia klawiaturowego musi generować zdarzenia dla naciśnięcia klawisza i wejścia do wydania klucza.

## <a name="modal-dialog-execution"></a>Wykonywanie dialogu modalnego 

Wykonywanie dialogu modalnego odwołuje się do przedniego okna użytkownikowi, który musi zostać zamknięty w jakiś sposób, zanim inne GUIX Windows lub widżety mogą odbierać dane wejściowe użytkownika. Modalne okna dialogowe przechwytują wszystkie dane wejściowe użytkownika, gdy okno dialogowe jest wyświetlane, niezależnie od położenia x, y zdarzeń wprowadzania dotykowego lub myszy.

Modalne okna dialogowe są wywoływane przez oprogramowanie aplikacji przez pierwsze utworzenie okna w normalny sposób przez wywołanie ***gx_window_create***, a następnie wywołanie funkcji interfejsu API GUIX ***gx_window_execute.***

Gdy wywoływana jest funkcja ***gx_window_execute*** , GUIX wprowadza lokalną pętlę przetwarzania zdarzeń. Funkcja ***gx_window_execute*** nie zwraca do obiektu wywołującego, dopóki okno dialogowe nie zostanie zamknięte ani przez dane wejściowe użytkownika, ani wywołując ***gx_window_close***. Z tego powodu bardzo ważne jest, aby nigdy nie wywoływać funkcji ***gx_window_execute*** z dowolnego wątku innego niż wewnętrzny wątek GUIX.

## <a name="periodic-processing"></a>Okresowe przetwarzanie 

W celu zapewnienia efektów wyświetlania, animacji Sprite i obsługi żądań okresowych aplikacji GUIX używa jednego czasomierza ThreadX. Ten pojedynczy czasomierz jest używany do określenia wszystkich GUIX potrzeb związanych z czasem. Domyślnie częstotliwość przetwarzania czasomierza wewnętrznego GUIX jest ustawiona na 20ms za pośrednictwem stałej **GX_SYSTEM_TIMER_MS**, która jest zdefiniowana w **_gx_api. h_**, chyba że stała jest wcześniej zdefiniowana w gx_port. h lub gx_user. h. Częstotliwość domyślna może zostać zmieniona przez aplikację za pośrednictwem opcji kompilacji podczas kompilowania biblioteki GUIX lub poprzez jawne ponowne zdefiniowanie jej w ***gx_user. h***.

> [!IMPORTANT]
> Należy zauważyć, że częstotliwość czasomierza GUIX jest wyrażona w taktach czasomierza RTO i jest definiowana przez stałą **GX_SYSTEM_TIMER_TICKS**. Wartość **GX_SYSTEM_TIMER_TICKS** jest obliczana przy użyciu **GX_SYSTEM_TIMER_MS** i **TX_TIMER_TICKS_PER_SECOND**. Użytkownik może ponownie zdefiniować dowolne z tych wartości w ***gx_port. h** _ lub _ *_gx_user. h_**, aby dostosować częstotliwość i rozdzielczość czasomierza GUIX.

## <a name="display-driver"></a>Sterownik ekranu 

Sterowniki wyświetlania są odpowiedzialne za dostarczanie zestawu funkcji rysowania do podstawowego kodu GUIX. Implementacja każdej z tych funkcji rysowania jest określana przez sterownik i gdy jest to możliwe, implementacja będzie korzystać z funkcji przyspieszenia sprzętowego. Ogólnie rzecz biorąc, funkcja rysowania działa przez zapisanie danych pikseli w buforze pamięci, który może być buforem ramki fizycznej lub może być buforem pomocniczym w zależności od architektury sterowników. Wiele sterowników implementuje podwójne buforowanie przy użyciu dwóch buforów ramek, a te bufory są przełączane przez wywołanie funkcji przełączania buforu. GUIX wywołuje te funkcje wewnętrznie w odpowiednim czasie. W przypadku systemów z ograniczoną ilością pamięci funkcje rysowania mogą zapisywać tylko w buforze klatek pojedynczej pamięci.

Program GUIX zapewnia domyślne implementacje poszczególnych funkcji rysowania na niskim poziomie w każdej głębi kolorów i formacie. Te funkcje są wywoływane za pośrednictwem wskaźników funkcji, które są obsługiwane w strukturze **GX_DISPLAY** . W przypadku tworzenia sterowników specyficznych dla sprzętu zazwyczaj zastąpią one kilka funkcji, które są specyficzne dla sprzętu docelowego.

Typowy sterownik ekranu sprzętowego jest implementowany przez utworzenie domyślnego sterownika wyświetlania GUIX dla wymaganej głębi kolorów i formatu.
Następnie sterownik sprzętu zamieni te funkcje, które muszą być zoptymalizowane lub dostosowane do określonej implementacji sprzętowej.

GUIX obsługuje formaty kolorów pikseli z przedziału od 1 do BPP monochromatyczny do 32-BPP a:r: g:b. GUIX obsługuje również wiele odmian w ramach każdej szerokiej kategorii głębi kolorów, na przykład r:g: b i b:g: kolejność bajtów w języku r, opakowany piksel i formaty pikseli wyrównane do tekstu oraz kanały alfa. Obecnie są obsługiwane 25 odrębnych formatów kolorów, ale ta lista rośnie w miarę jak producenci sprzętu dostarczają nowe odmiany.

## <a name="display-memory-architectures"></a>Wyświetlanie architektur pamięci

Różne elementy docelowe sprzętu i wyświetlacze wykorzystują różne architektury pamięci wyświetlanej, w zależności od ograniczeń pamięci docelowej i wymagań dotyczących funkcjonalności aplikacji. W tym miejscu będziemy konspektować niektóre popularne architektury pamięci z krótkim opisem każdego z nich.

Model 1) brak buforu ramki, dane grafiki przechowywane w zewnętrznym GRAMie:

![Brak buforu ramki, dane grafiki przechowywane w zewnętrznym GRAMie](./media/guix/user-guide/no-frame-buffer.png)

W modelu powyżej nie istnieje pamięć dla bufora klatek w pamięci lokalnej dla procesora CPU. Wszystkie dane grafiki są przechowywane w zewnętrznym GRAMu, który jest włączony do samego wyświetlania. Interfejs do zewnętrznego GRAMa może być równoległy lub szeregowy. Ten typ architektury jest bardzo niski. Jednak może to mieć niepożądany efekt, gdy dane graficzne zostaną zaktualizowane.

Model 2) jeden bufor lokalnej ramki:

![Jeden lokalny bufor ramki](./media/guix/user-guide/one-local-frame-buffer.png)

W tym modelu pamięć dla danych graficznych jest przydzielana z pamięci o dostępie losowym, która jest bezpośrednio dostępna dla procesora CPU. Dedykowany sprzęt musi być obecny, aby wielokrotnie przesyłać dane graficzne (wraz z sygnałami chronometrażu) z pamięci lokalnej do ekranu. Ten model różni się od modelu 1 w tym, że pamięć graficzna jest blokiem lokalnej pamięci DRAM lub pamięci RAM dostępnej dla procesora CPU. Może to być taka sama pamięć, w której znajdują się zmienne stosu i programu na żywo.

Model 3) bufor klatek lokalnych + zewnętrzny GRAM:

![Bufor klatek lokalnych + zewnętrzny GRAM](./media/guix/user-guide/local-frame-buffer-external-gram.png)

Model 3 jest kombinacją dwóch pierwszych. W tym modelu wystarcza pamięć lokalna do przechowywania jednego buforu ramek. Ponadto urządzenie wyświetlające udostępnia zewnętrzny GRAM i automatycznie odświeża siebie przy użyciu danych z danego GRAMu. Ta architektura przynosi korzyści z poprawy wydajności aktualizacji, ponieważ można przenieść zmodyfikowaną część lokalnego buforu ramek do zewnętrznego GRAMa w jednym transferze blokowym, często korzystając z dołączanych kanałów DMA. Ten model eliminuje również pęknięcia i migotanie, które mogą znajdować się w każdym z pierwszych dwóch modeli, ponieważ tylko ukończona zawartość graficzna jest kopiowana do zewnętrznego GRAMu.

Model 4) bufory ramek polecenia ping-pong:

![Polecenie ping — bufory ramek pong](./media/guix/user-guide/ping-pong-frame-buffers.png)

W modelu 4 dostępna jest wystarczająca ilość pamięci, aby zapewnić dwa lokalne bufory ramek. W tym przypadku GUIX traktuje jeden bufor ramki jako aktywny bufor ramek, a drugi jako bufor ramki roboczej. Gdy operacja wyświetlania aktualizacji lub rysowania jest w toku, odbywa się ona w buforze roboczym. Po zakończeniu operacji rysowania bufory są przełączane, a bufor roboczy jest aktywnym buforem, a aktywny bufor jest buforem roboczym. Ten model eliminuje również migotanie ekranu i rozerwanie, które mogą być zaobserwowane w jednym zbuforowanym systemie.

Model 5) bufory polecenia ping-pong z założeniami kanwy:

![Polecenie ping-pong bufory ze składową kanwy](./media/guix/user-guide/ping-pong-buffers-canvas-composting.png)

W modelu 5 można utworzyć dowolną liczbę kanw, do limitu dostępnej pamięci. Kanwy mogą być nałożone lub połączone w sposób zdefiniowany przez aplikację w celu utworzenia kompozytu kanwy. Po utworzeniu nowego projektu złożonego po wykonaniu operacji odświeżania ekranu, aktywne i działające złożone bufory są przełączane w operacji identycznej ze standardową architekturą bufora ping-pong. Model 5 dodaje możliwość zanikania ekranu i mieszania operacji poprzez mieszanie kanw do końcowego kompozytu wyjściowego.

Model 6) składanie kanwy z zewnętrznym GRAMem:

![Składanie kanwy z zewnętrznym GRAMem](./media/guix/user-guide/canvas-compositing-external-gram.png)

Model 6 to niewielka odmiana modelu 5, w której wymagany jest tylko jeden bufor złożony, a następnie złożony bufor jest przenoszony do zewnętrznego GRAMu. Ten model obsługuje również pełne mieszanie i nakładki ekranu.

## <a name="string-encoding"></a>Kodowanie ciągu 

GUIX domyślnie obsługuje kodowanie ciągu formatu UTF8. Obsługę kodowania ciągów UTF8 można wyłączyć, definiując **GX_DISABLE_UTF8_SUPPORT** w pliku nagłówkowym ***gx_user. h*** . Jeśli kodowanie UTF8 jest wyłączone, GUIX będzie wewnętrznie używać tylko standardowego 8-bitowego kodu ASCII Plus kodowania znaków strony kodowej Latin-1. Wyłączenie kodowania ciągów UTF8 skutkuje nieco mniejszym rozmiarem biblioteki GUIX i nieco szybsze wykonywanie funkcji obsługi ciągów i rysowania tekstu.

Kodowanie ciągu UTF8 ma następujące cechy:

  - Ciągi ASCII nie pobierają więcej miejsca do magazynowania niż standardowe 7-bitowe kodowanie ASCII.

  - Większość funkcji ciągów ANSI-C współpracuje z kodowaniem ciągu UTF8 bez modyfikacji.

Wszystkie aktywne zestawy znaków na świecie, w tym zestawy znaków kanji, mogą być reprezentowane przy użyciu kodowania ciągu UTF8.

### <a name="static-and-dynamic-strings"></a>Ciągi statyczne i dynamiczne 

Ciągi przypisane do widżetów GUIX, które obsługują wyświetlanie tekstu, mogą być statycznie zdefiniowanymi ciągami, które są zwykle umieszczane w stałym magazynie, jako część tabeli ciągów GUIX opisana poniżej, i dynamicznie definiowanych ciągów, które są ciągami generowanymi w czasie wykonywania przy użyciu usług takich jak ***sprintf —** _ lub _ *_gx_utility_ltoa_* *.

Przykłady ciągów dynamicznych mogą zawierać wartość wyświetlaną jako liczbę w widżecie GUIX monitu lub ciąg "czas/data", który jest dynamicznie formatowany na podstawie preferencji lokalizacji i formatu użytkownika. Jeśli tworzysz ciągi w środowisku uruchomieniowym, które zostaną przypisane do widżetów GUIX, takich jak **GX_PROMPT** lub **GX_TEXT_BUTTON**, musisz wybrać statyczną alokację magazynu dla tych ciągów generowanych przez środowisko uruchomieniowe (tj.
globalne tablice znaków) lub można zdefiniować i zainstalować funkcję alokatora pamięci dynamicznej i użyć **GX_STYLE_TEXT_COPY** stylu, który instruuje te widżety do utworzenia prywatnej kopii ciągów tekstowych przypisanych.

Jest to błąd programistyczny służący do przechowywania tymczasowego magazynu, takiego jak automatyczna tablica znaków, do przechowywania dynamicznie generowanego ciągu, a następnie przypisywania tego ciągu do widżetu, który nie ma stylu **GX_STYLE_TEXT_COPY** . Gdy ten styl nie jest włączony, widżet po prostu kopiuje podany wskaźnik ciągu, a dane ciągu muszą być przydzieloną statycznie lub wskaźnik ciągu widżetu prawdopodobnie zakończy się, wskazując na nieprzewidywalne wyniki.

### <a name="passing-gx_string-arguments"></a>Przekazywanie GX_STRING argumentów 

Funkcje interfejsu API GUIX, które akceptują parametr GX_STRING, zawsze weryfikują, że długość ciągu wskazywanego przez pole **GX_STRING. gx_string_ptr** pasuje do wartości pola **GX_STRING. gx_string_length** . Jeśli dwa pola są niespójne, zwracany jest błąd **GX_INVALID_STRING_LENGTH** i interfejs API o nazwie Returns nie akceptuje przypisania ciągu.

Ze względów bezpieczeństwa oprogramowanie GUIX nigdy nie używa wewnętrznie standardowego języka C, takiego jak ***strlen** _ lub _ *_strcpy_* *. Te funkcje są znane jako podatne na złośliwe ataki, gdy dane ciągów są uzyskiwane dynamicznie, co jest często stosowane w przypadku połączonych aplikacji.

GUIX wersje biblioteki przed wydaniem 5,6 zdefiniowane funkcje interfejsu API, które zaakceptowały ( `GX_CONST GX_CHAR *text` ) jako parametr. Te funkcje, które nadal są obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami, zostały przestarzałe i zastąpione przez preferowane funkcje interfejsu API, które akceptują ( `GX_CONST GX_STRING *string` ) jako parametr wejściowy.

Domyślnie przestarzały interfejs API obsługi tekstu jest włączony, co umożliwia czyszczenie wszystkich wcześniej pisanych aplikacji z najnowszymi aktualizacjami biblioteki GUIX. Aby wyłączyć interfejs API obsługi tekstu przestarzałego, definicja **GX_DISABLE_DEPRECATED_STRING_API** powinna zostać dodana do **pliku nagłówkowego _gx_user. h_*_. Wszystkie nowe aplikacje powinny definiować _* GX_DISABLE_DEPRECATED_STRING_API** i powinny używać tylko zastępujące funkcje interfejsu API. Wszystkie pliki wyjściowe wygenerowane przez GUIX Studio for GUIX Library w wersji 5,6 lub nowszej będą korzystać tylko z funkcji API zastępującej.

W poniższej tabeli wymieniono przestarzałe i nowo zdefiniowane nazwy funkcji API zastępujących:

| **Przestarzała nazwa funkcji**              | **Zamieniono na**                              |
| ------------------------------------------ | ----------------------------------------------- |
| gx_binres_language_table_load          | gx_binres_language_table_load_ext          |
| gx_canvas_rotated_text_draw            | gx_canvas_rotated_text_draw_ext            |
| gx_canvas_text_draw                     | gx_canvas_text_draw_ext                     |
| gx_context_string_get                   | gx_context_string_get_ext                   |
| gx_display_language_table_get          | gx_display_language_table_get_ext          |
| gx_display_language_table_set          | gx_display_language_table_set_ext          |
| gx_display_string_get                   | gx_display_string_get_ext                   |
| gx_display_string_table_get            | gx_display_string_table_get_ext            |
| gx_multi_line_text_button_text_set   | gx_multi_line_text_button_text_set_ext   |
| gx_multi_line_text_input_char_insert | gx_multi_line_text_input_char_insert_ext |
| gx_multi_line_text_input_text_set    | gx_multi_line_text_input_text_set_ext    |
| gx_multi_line_text_view_text_set     | gx_multi_line_text_view_text_set_ext     |
| gx_prompt_text_get                      | gx_prompt_text_get_ext                      |
| gx_prompt_text_set                      | gx_prompt_text_set_ext                      |
| gx_single_line_text_input_text_set   | gx_single_line_text_input_text_set_ext   |
| gx_system_string_width_get             | gx_system_string_width_get_ext             |
| gx_system_version_string_get           | gx_system_version_string_get_ext           |
| gx_text_button_text_get                | gx_text_button_text_get_ext                |
| gx_text_button_text_set                | gx_text_button_text_set_ext                |
| gx_text_scroll_wheel_callback_set     | gx_text_scroll_wheel_callback_set_ext     |
| gx_utility_string_to_alphamap          | gx_utility_string_to_alphamap_ext          |
| gx_widget_string_get                    | gx_widget_string_get_ext                    |
| gx_widget_text_blend                    | gx_widget_text_blend_ext                    |
| gx_widget_text_draw                     | gx_widget_text_draw_ext                     |

### <a name="guix-string-table"></a>Tabela ciągów GUIX 

Tabela ciągów GUIX i zasoby ciągów są rejestrowane przy użyciu wystąpienia GUIX Display.

Każdy ekran w systemie z obsługą wielu monitorów ma własną tabelę ciągów, a każdy z nich może być uruchamiany w wybranym języku. Inne typy zasobów GUIX (kolory, czcionki i pixelmaps) są również obsługiwane przez składnik GUIX Display, ponieważ te typy zasobów są specyficzne dla każdego formatu koloru wyświetlania i głębi kolorów.

Mimo że można ręcznie utworzyć tabelę ciągów aplikacji, najczęściej wyświetlana tabela ciągów jest definiowana przez aplikację GUIX Studio jako część pliku zasobów projektu. Dostępne języki są również zdefiniowane w pliku nagłówkowym zasobu. Tabela ciągów wyświetlanych to wielokolumnowa tabela wskaźników do ciągów aplikacji. Każda kolumna tabeli ciągów reprezentuje jeden język obsługiwany przez aplikację.
Jeśli aplikacja obsługuje tylko jeden język, na przykład w języku angielskim, tabela ciągów będzie mieć tylko jedną kolumnę. Nadal możesz w dowolnym momencie dodać obsługę dodatkowych języków bez modyfikowania oprogramowania aplikacji.

Aktywna tabela ciągów jest przypisywana przez wywołanie funkcji API ***gx_display_string_table_set*** . Ta funkcja jest wywoływana automatycznie przez program GUIX Studio wygenerowany kod uruchamiania, ale może być również wywoływana bezpośrednio przez aplikację w celu zmiany aktywnej tabeli ciągów.

Język aktywny jest przypisywany przez wywołanie funkcji API ***gx_display_active_language_set*** . Ta funkcja określa, która kolumna tabeli ciągów wyświetlanych jest aktywna.

Gdy ta funkcja jest wywoływana, zdarzenie **GX_EVENT_LANGUAGE_CHANGE** jest wysyłane do wszystkich widocznych widżetów GUIX, co pozwala na ich aktualizację, aby wyświetlały nowo aktywne dane ciągu.

Elementy widget i oprogramowanie aplikacji rozwiązują statycznie zdefiniowane ciągi przy użyciu wartości identyfikatorów ciągów i funkcji interfejsu API ***gx_display_string_get_ext*** lub ***gx_widget_string_get_ext*** . Te funkcje zwracają **GX_STRING** skojarzone z danym identyfikatorem ciągu i aktualnie aktywnym językiem.

### <a name="bi-directional-text-display"></a>Dwukierunkowe wyświetlanie tekstu 

GUIX zapewniają dwie strategie obsługi tekstu dwukierunkowego.

Jedną z opcji jest zmiana kolejności tekstu dwukierunkowego w aplikacji GUIX Studio. Użycie tej opcji GUIX Studio jest odpowiedzialne za Generowanie tekstu dwukierunkowego w pliku wyjściowym w jego kolejności wyświetlania. To rozwiązanie nie ma wpływu na wydajność środowiska uruchomieniowego i nie wymaga żadnych dodatków do biblioteki środowiska uruchomieniowego GUIX. Aby umożliwić programowi GUIX Studio generowanie displayorderych ciągów tekstu dwukierunkowego, należy zaznaczyć pole wyboru **Generuj tekst dwukierunkowy w kolejności wyświetlania** w oknie dialogowym konfiguracji języka programu GUIX Studio:

![Konfigurowanie języków](./media/guix/user-guide/configure-languages.png)

Po wybraniu tych opcji wygenerowany plik zasobów będzie zawierać ciągi dwukierunkowe wygenerowane w kolejności wyświetlania, a żadne dodatkowe przetwarzanie nie jest wymagane w ramach biblioteki środowiska uruchomieniowego GUIX.

Drugą opcją jest zmiana kolejności tekstu dwukierunkowego w czasie wykonywania. Ta opcja jest obsługiwana dla tych aplikacji, które muszą obsługiwać ciąg tekstowy dwukierunkowego, który jest definiowany dynamicznie i niegenerowany przez aplikację GUIX Studio. W takim przypadku Biblioteka środowiska uruchomieniowego GUIX jest odpowiedzialna za zmianę kolejności tekstu dwukierunkowego przed rysowaniem każdego ciągu tekstowego. To rozwiązanie ma wydajność i wpływ na pamięć środowiska uruchomieniowego. W procesie zmiany kolejności tekstu dwukierunkowego musi być dostępna wystarczająca ilość pamięci dynamicznej. To rozwiązanie wymaga zdefiniowania warunkowego GX_DYNAMIC_BIDI_TEXT_SUPPORT podczas kompilowania biblioteki GUIX. Dwie funkcje interfejsu API ***gx_system_bidi_text_enable*** i ***gx_system_bidi_text_disable*** są udostępniane do włączania/wyłączania obsługi tekstu dwukierunkowego w czasie wykonywania.

Nie należy używać obu **GX_DYNAMIC_BIDI_TEXT_SUPPORT** i skonfigurować program GUIX Studio do generowania tekstu dwukierunkowego w kolejności wyświetlania. Należy wybrać jedną strategię lub drugą do obsługi ciągu tekstu dwukierunkowego.

## <a name="memory-usage"></a>Użycie pamięci 

GUIX się wraz z programem aplikacji. W związku z tym użycie pamięci statycznej (lub stałej pamięci) GUIX jest określane przez narzędzia programistyczne. na przykład kompilator, konsolidator i lokalizator. Użycie pamięci dynamicznej (lub pamięci w czasie wykonywania) jest kontrolowane bezpośrednio przez aplikację.

### <a name="static-memory-usage"></a>Użycie pamięci statycznej 

Większość narzędzi programistycznych dzieli obraz programu aplikacji na pięć podstawowych obszarów: *instrukcje*, *stałe*, *zainicjowane dane*, *niezainicjowane dane* i *stos wątku GUIX*. Na rysunku X na stronie X przedstawiono przykład tych obszarów pamięci.

Ważne jest, aby zrozumieć, że jest to tylko przykład. Rzeczywisty układ pamięci statycznej jest specyficzny dla procesora, narzędzi programistycznych, sprzętu podstawowego i samej aplikacji.

Obszar instrukcji zawiera wszystkie instrukcje procesora programu. Ten obszar często znajduje się w pamięci ROM.

Obszar stałych zawiera różne skompilowane stałe, które w programie GUIX zawierają ustawienia domyślne i wszystkie zasoby aplikacji (obrazy, ciągi, czcionki i kolory). Ponadto ten obszar zawiera "początkową kopię" zainicjowanego obszaru danych. Podczas inicjowania kompilatora, ta część stałego obszaru służy do konfigurowania globalnie zainicjowanych danych w pamięci RAM. Stałe miejsce jest zwykle największe i zazwyczaj następuje w obszarze instrukcji i często znajduje się w pamięci ROM.

GUIX pixelmaps i czcionki zwykle wymagają dużych ilości magazynu danych stałych. Te duże obszary danych statycznych są zwykle przechowywane w pamięci ROM lub na platformie FLASH.

Stos wątku GUIX jest zdefiniowany w niezainicjowanym obszarze danych (jako zmienna globalna) w pliku ***gx_system. h*** w następujący sposób:

```C
_gx_system_thread_stack[GX_THREAD_STACK_SIZE];
```

**GX_THREAD_STACK_SIZE** jest zdefiniowana w **_gx_port. h_**, ale może zostać przesłonięta przez aplikację przez zdefiniowanie tego symbolu w pliku nagłówkowym ***gx_user. h*** lub za pomocą opcji projektu lub parametrów wiersza polecenia. Rozmiar stosu musi być wystarczająco duży, aby obsługiwał obsługę zdarzeń najgorszego przypadku i zagnieżdżone wywołania rysowania.

### <a name="dynamic-memory-usage"></a>Użycie pamięć dynamiczna 

Jak wspomniano wcześniej, użycie pamięci dynamicznej jest kontrolowane bezpośrednio przez aplikację. Bloki kontroli i pamięć skojarzona z kanwami itp. mogą być umieszczane w dowolnym miejscu w przestrzeni pamięci docelowej. Jest to ważna funkcja, ponieważ ułatwia ona łatwe wykorzystanie różnych typów pamięci fizycznej — w czasie wykonywania.

Załóżmy na przykład, że w docelowym środowisku sprzętowym występuje szybka pamięć i wolna pamięć. Jeśli aplikacja wymaga dodatkowej wydajności do rysowania, pamięć kanwy można jawnie umieścić w obszarze pamięci o dużej szybkości w celu uzyskania najlepszej wydajności.

Niektóre opcjonalne usługi i funkcje GUIX wymagają mechanizmu alokacji pamięci dynamicznej środowiska uruchomieniowego, nazywanego często stertą. Te usługi i funkcje są całkowicie opcjonalne i wiele aplikacji GUIX nie korzysta z żadnych stert i nie definiują mechanizmu alokacji pamięci środowiska uruchomieniowego.

Jeśli będą używane usługi wymagające alokacji pamięci środowiska uruchomieniowego, należy zainstalować funkcje, które GUIX będą wywoływały, gdy pamięć musi być dynamicznie przydzielana lub zwalniana. Można zaimplementować te funkcje zgodnie z preferencjami, tak aby nawet w tym przypadku lokalizacja puli pamięci dynamicznej była pod kontrolą aplikacji. Aby zainstalować obsługę dynamicznego przydzielania pamięci, aplikacja powinna wywołać usługę interfejsu API ***gx_system_memory_allocator_set*** podczas uruchamiania programu, aby zdefiniować alokację pamięci i usługi wolne od pamięci. Pełny przykład można znaleźć w dokumentacji tego interfejsu API.

Usługi GUIX, które wymagają alokacji pamięci środowiska uruchomieniowego i usługi cofnięcia alokacji, obejmują:

  - Ładowanie zasobów binarnych z magazynu zewnętrznego do środowiska uruchomieniowego GUIX.

  - Dekoder obrazu JPEG środowiska uruchomieniowego oprogramowania.

  - Dekoder obrazu PNG środowiska uruchomieniowego oprogramowania.

  - Używanie widżetów tekstowych z GX_STYLE_TEXT_COPY.

  - Funkcje narzędzia do zmiany rozmiaru i rotacji środowiska uruchomieniowego pixemap.
  - Alokacja bloku ekranu i widżetu środowiska uruchomieniowego.

W przypadku mniejszych aplikacji GUIX zasoby są zwykle kompilowane i statycznie łączone w ramach obrazu aplikacji, a instalacja zasobów binarnych nie jest wymagana. Zasoby binarne pozwalają aplikacji instalować zasoby (czcionki, obrazy, języki) w czasie wykonywania załadowane z lokalizacji magazynu, na przykład na dysku flash lub w adresie URL.

Dekodery JPEG i PNG są opcjonalnymi składnikami. Większość aplikacji GUIX umożliwia narzędziu GUIX Studio wstępne dekodowanie wszystkich wymaganych plików obrazów i przechowywanie ich jako własnościowe zasoby danych GUIX Pixemap. Te usługi zapewniają kompletność dla tych aplikacji, które wymagają konwersji w czasie wykonywania obrazów JPEG i/lub PNG do formatu Pixelmap.

**GX_STYLE_TEXT_COPY** umożliwia użytkownikowi określenie, że określony widżet lub widżety będą zachować własną prywatną kopię dynamicznie przypisanego tekstu. Użycie tej opcji wymaga zainstalowania mechanizmu alokacji pamięci przed użyciem. Jeśli flaga stylu **<span class="underline">nie</span>** zostanie podana podczas tworzenia widżetu typu text, aplikacja musi przydzielić statyczne obszary magazynu dla wszystkich dynamicznie utworzonych i przypisanych ciągów tekstowych. W tym przypadku zmienne automatyczne nie powinny być używane w celu przechowywania danych ciągu wygenerowanych przez środowisko uruchomieniowe. Jeśli **GX_STYLE_TEXT_COPY** styl jest włączony, zmienne automatyczne mogą być używane do przechowywania danych ciągu przypisanych do GUIX widżetów, ponieważ każdy widżet utworzy własną kopię przypisanego tekstu.

Funkcje narzędzia do zmiany rozmiaru i rotacji Pixelmap zwracają wynikowe tłumaczone Pixelmap jako nowe Pixelmap dostępne dla aplikacji.
Jeśli są używane te usługi, musi być dostępna wystarczająca ilość pamięci dynamicznej do przechowywania tych bloków danych Pixelmap.

Na koniec bloki sterujące dla ekranów i widżetów GUIX można statycznie lub dynamicznie przydzielać. W przypadku mniejszych aplikacji często można utworzyć wszystkie ekrany aplikacji podczas uruchamiania programu i użyć statycznie przyznanych bloków sterujących. W przypadku dużych aplikacji często istnieje możliwość dynamicznego tworzenia ekranów i podrzędnych kontrolek widżetu. Dynamicznie przydzielane bloki sterujące są określane przez zaznaczenie pola wyboru **Przydziel w środowisku uruchomieniowym** w widoku właściwości programu GUIX Studio lub przekazanie do flagi stylu **GX_STYLE_DYNAMICALLY_ALLOCATED** podczas tworzenia widżetu za pośrednictwem standardowego interfejsu API. Użycie dynamicznie przydzielonych bloków kontrolek widżetu wymaga, aby alokacja pamięci i usługi cofania alokacji zostały zdefiniowane zgodnie z powyższym opisem.

## <a name="guix-components"></a>Składniki GUIX 

Interfejsy API GUIX są podzielone i zorganizowane w kilka podstawowych grup, które odpowiadają podstawowym składnikom systemu GUIX. Podstawowe składniki obejmują:

| Składniki  | Opis  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GX_SYSTEM  | Składnik systemu GUIX, odpowiedzialny za inicjalizację, zdarzenia, czasomierze i tabele ciągów oraz Zarządzanie hierarchią widżetów widocznych.                                                                                                                                                                                                                                                                      |
| GX_CANVAS  | Obszar rysowania. Kanwa może być cienką abstrakcją buforu klatek sprzętowych lub może być również czystą kanwą pamięci. Typ kanwy jest określany przez parametry przesłane do funkcji API gx_canvas_create.                                                                                                                                                                                   |
| GX_CONTEXT | Składnik kontekstu rysowania. Kontekst rysowania zawiera informacje dotyczące ekranu, kanwy i pędzla oraz obszaru wycinków dla bieżących operacji rysowania.                                                                                                                                                                                                                                      |
| GX_DISPLAY | Udostępnia interfejsy API i implementacje na poziomie sterowników umożliwiające aplikacji i widżetom GUIX wykonywanie rysowania na kanwie. GX_DISPLAY jest zaimplementowana w celu poprawnego renderowania grafiki na każdej kanwie przy użyciu wymaganego formatu koloru tej kanwy. Składnik GX_DISPLAY zarządza także zasobami (kolorami, czcionkami i pixelmaps) dostępnymi dla rysunków widget do kanw połączonych z każdym ekranem. |
| GX_WIDGET  | Podstawowy widoczny obiekt widget i skojarzone z nim interfejsy API. Wszystkie typy widżetów GUIX są oparte na typie podstawowego GX_WIDGET lub pochodnym.                                                                                                                                                                                                                                                                      |
| GX_UTILITY | W tej grupie są zawarte funkcje narzędziowe do pracy z prostokątami, funkcje konwersji ciągów i funkcje matematyczne inne niż ANSI.                                                                                                                                                                                                                                                         |

Oprócz tych podstawowych składników GUIX zawiera interfejsy API, które są unikatowe dla każdego typu widżetu dostępnego w bibliotece. Te interfejsy API są opisane w rozdziale 4 tego podręcznika użytkownika "Opis usług GUIX Services".

## <a name="guix-system-component"></a>Składnik systemu GUIX

Składnik System GUIX zawiera kilka usług, które są globalne dla aplikacji interfejsu użytkownika. Te usługi obejmują: *Inicjowanie, zarządzanie zdarzeniami, zarządzanie wyświetlaniem, zarządzanie zasobami, zarządzanie czasomierzami* i *Zarządzanie widżetem*. Każda usługa jest istotna dla organizacji programu aplikacji. te usługi są szczegółowo opisane w poniższych podsekcjach.

### <a name="initialization"></a>Inicjalizacja 

Inicjalizacja GUIX jest realizowana przez aplikację wywołującą ***gx_system_initialize*** usługi, która może być wywoływana przez aplikację z procedury ThreadX ***tx_application_define*** (kontekstu inicjowania) lub z wątków aplikacji. Funkcja ***gx_system_initialize*** inicjuje wszystkie globalne struktury danych GUIX i tworzy element MUTEX systemu GUIX, kolejkę zdarzeń, czasomierz i wątek. Gdy ***gx_system_initialize*** zwraca, aplikacja może używać GUIX.

### <a name="thread-processing"></a>Przetwarzanie wątku 

Wewnętrzny wątek GUIX — tworzony podczas inicjowania — jest odpowiedzialny za większość przetwarzania w GUIX. Przetwarzanie w tym wątku najpierw kończy wszelkie dodatkowe inicjalizacje wymagane przez podstawowy sterownik ekranu. Po zakończeniu tego procesu wątek GUIX wprowadza pętlę, która najpierw przetwarza wszystkie zdarzenia znajdujące się w kolejce zdarzeń GUIX, a następnie odświeża ekran, jeśli jest to wymagane. Odświeżanie ekranu wykonuje wymagane funkcje rysowania GUIX na podstawie tego, co jest widoczne, i zostało oznaczone jako zanieczyszczone, co jest wymagane do narysowania. Gdy nie ma żadnych zdarzeń i nie pozostało do odświeżenia na ekranie, wątek GUIX zostanie zawieszony, czekając na nadejście następnego zdarzenia GUIX.

### <a name="rtos-binding"></a>Powiązanie RTO 

Składnik systemu GUIX jest domyślnie skonfigurowany do korzystania z systemu operacyjnego ThreadX w czasie rzeczywistym dla usług takich jak usługi wątków, usługi kolejkowania zdarzeń i usługi czasomierza. GUIX można łatwo przenieść do innych systemów operacyjnych za pomocą dyrektywy preprocesora GX_DISABLE_THREADX_BINDING i ponownie skompilować bibliotekę GUIX. Spowoduje to usunięcie zależności ThreadX z kodu źródłowego GUIX i umożliwia deweloperom aplikacji zaimplementowanie wymaganych usług systemu operacyjnego za pomocą dowolnych RTOów udostępnianych przez system docelowy. [Dodatek F-GUIX RTO Binding Services](appendix-f.md) opisuje usługi, które należy zaimplementować do portu GUIX, do systemu operacyjnego innego niż ThreadX systemu operacyjnego.

### <a name="multithread-safety"></a>Bezpieczeństwo wielowątkowej 

Interfejs API GUIX jest dostępny z kontekstu wątku GUIX oraz innych wątków aplikacji. Wątki aplikacji mogą korzystać z wątku GUIX przez wysyłanie i otrzymywanie zdarzeń, przez dostęp do zmiennych udostępnionych i za pomocą funkcji interfejsu API GUIX. GUIX używa wewnętrznego obiektu mutex ThreadX do ochrony wielowątkowych zasobów. Ponadto GUIX zapobiega modyfikowaniu wewnętrznej struktury widocznych elementów widget po rozpoczęciu operacji odświeżania ekranu. Interfejsy API, które mogłyby modyfikować drzewo widocznych obiektów, są blokowane, gdy operacje rysowania są w toku i są wydawane po zakończeniu odświeżania ekranu.

### <a name="system-timers"></a>Czasomierze systemu 

GUIX udostępnia aplikację z okresowymi czasomierzami, które są często używane do okresowej aktualizacji danych wyświetlanych w systemie GUIX. Jest to realizowane za pośrednictwem ThreadXego czasomierza okresowego, który jest również używany do wykonywania GUIXych efektów na poziomie systemu, takich jak zanikanie ekranu/out itp.

Aplikacja może tworzyć czasomierze i korzystać z tej samej funkcji czasomierza, która jest używana wewnętrznie przez GUIX. Oczywiście aplikacja może również bezpośrednio tworzyć i używać czasomierzy ThreadX, jeśli jest to wymagane. Zaletą czasomierzy GUIX jest bardzo łatwa w użyciu i wstępnie skonfigurowana do pracy w systemie przetwarzania opartego na zdarzeniach GUIX.

Aby utworzyć i uruchomić czasomierz GUIX, aplikacja powinna wywołać funkcję ***gx_system_timer_start***. Parametry tej funkcji obejmują wskaźnik do elementu widget wywołującego, identyfikator czasomierza (Zezwalanie jednemu elementowi widget na uruchomienie wielu czasomierzy) oraz początkowe i ponownie zaplanowane wartości limitu czasu. Jeśli wartość limitu czasu ponownego harmonogramu wynosi 0, czasomierz zostanie uruchomiony tylko raz i zostanie usunięty z aktywnej listy czasomierzy po jego wygaśnięciu.

Po uruchomieniu czasomierz GUIX wyśle zdarzenia GX_EVENT_TIMEOUT do właściciela czasomierza, raz lub okresowo, w zależności od wartości ponowne zaplanowanie czasomierza. Czasomierz GUIX można zatrzymać, wywołując funkcję interfejsu API ***gx_system_timer_stop***.

### <a name="pen-speed-configuration"></a>Konfiguracja szybkości pióra 

Składnik systemu GUIX przechowuje informacje o konfiguracji związane ze śledzeniem szybkości pióra. GUIX wewnętrznie generowane zdarzenia **GX_EVENT_VERTICAL_FLICK** i **GX_EVENT_HORIZONTAL_FLICK** na podstawie szybkości i odległości zdarzeń PEN_DOWN generowanych przez sterownik wejścia dotykowego (jeśli istnieją). Aplikacja może skonfigurować minimalną odległość i szybkość wymaganą do wyzwalania tych wewnętrznie wygenerowane zdarzenia przy użyciu funkcji interfejsu API **_gx_system_pen_configure_** .

### <a name="screen-stack"></a>Stos ekranu 

Składnik systemu GUIX zapewnia usługi związane z stosem ekranu GUIX, który jest opcjonalną funkcją obsługującą stos wirtualnego widżetu, na którym ekrany mogą być wypychane, zdjęte i pobierane w czasie wykonywania przez aplikację. Stos ekranu jest przydatny do zarządzania złożonymi systemami menu, co w przypadku, gdy trasa, w której użytkownik może dotrzeć do różnych stanów w systemie menu, jest różna. Powrót do poprzedniego stanu w systemie menu można łatwo wykonać przez wypchnięcie poprzedniego stanu ekranu, a następnie wyświetlenie nowego ekranu i umożliwienie nowemu ekranowi wyskakującego poprzedniego stanu z stosu ekranu, gdy bieżący ekran zostanie odrzucony.

### <a name="clipboard-maintenance"></a>Obsługa schowka 

GUIX obsługuje schowek do kopiowania i wklejania tekstu podczas wykonywania. Ta pomoc techniczna jest świadczona przez składnik systemu GUIX.

### <a name="dirty-list-maintenance"></a>Konserwacja listy zanieczyszczonej 

GUIX przechowuje listę zanieczyszczonych elementów widget, czyli elementów widget, które są widoczne i muszą być ponownie rysowane ze względu na zmiany stanu lub nowe widoczne. Ta lista zanieczyszczona poprawia wydajność dzięki umożliwieniu GUIX do wykonania jednej operacji odświeżania kanwy, aby odzwierciedlić wszystkie bieżące zmiany stanu interfejsu użytkownika, a nie odświeżać kanwę w miarę wprowadzania zmian w interfejsie użytkownika.
Ta lista zanieczyszczona jest również obsługiwana przez składnik System GUIX.

### <a name="animation-control-block-pool"></a>Pula bloków formantów animacji 

Aplikacje często żądają wykonywania wielu sekwencji animacji, często równolegle. GUIX utrzymuje pulę bloków sterujących animacji, z których aplikacja może alokować i używać. Spowoduje to zwolnienie aplikacji ze statycznie definiujących te bloki kontroli i umożliwia ich ponowne użycie w różnym czasie, zamiast definiować unikatowy blok kontrolny animacji dla każdej animacji, którą może zdefiniować aplikacja. Pula bloków formantów animacji jest również utrzymywana przez składnik systemu GUIX.

### <a name="system-error-handling"></a>Obsługa błędów systemu 

Program obsługi błędów systemu GUIX ma pomóc w znalezieniu wewnętrznych błędów systemu w GUIX, które mogą być trudniejsze do ustalenia z perspektywy interfejsu API. Za każdym razem, gdy w GUIX wystąpi błąd systemu, wywoływana jest funkcja wewnętrzna ***_gx_system_error_process*** . Ta funkcja zapisuje podany kod błędu i zwiększa łączną liczbę wykrytych błędów systemu. Zmienne błędów systemowych są zdefiniowane w następujący sposób:

UINT **_gx_system_last_error**;

ULONG **_gx_system_error_count**;

Jeśli aplikacja GUIX zachowuje się dziwnie, warto przyjrzeć się zmiennej licznika błędów w debugerze. Jeśli jest ustawiona, dobrym sposobem rozwiązania problemu jest ustawienie punktu przerwania w funkcji ***_gx_system_error_process*** i sprawdzenie, czy jest on wywoływany.

## <a name="guix-canvas-component"></a>Składnik kanwy GUIX

Składnik kanwy jest odpowiedzialny za wszystkie procesy związane z kanwą. Kanwa jest wydajnym buforem ramek. Aplikacja musi utworzyć co najmniej jedną kanwę w celu utworzenia grafiki wyjściowej.
Zazwyczaj należy utworzyć co najmniej jedną kanwę dla każdego fizycznego ekranu obsługiwanego przez system.

Wszystkie rysowanie GUIX odbywa się na kanwie. W systemach z ograniczeniami lub z ograniczoną ilością pamięci istnieje prawdopodobnie tylko jedna Kanwa, która może być bezpośrednio połączona z widocznym buforem ramek, natomiast systemy z większą ilością pamięci i bardziej zaawansowane wymagania dotyczące grafiki mogą wymagać wielu kanw. Udostępnienie wielu kanw dla jednego ekranu umożliwia korzystanie z takich funkcji, jak efekt zanikania ekranu i okna i zanikania.
Kanwy mogą być jednym z dwóch typów głównych, prostych lub zarządzanych.

Prosta Kanwa to obszar rysowania poza ekranem używany przez aplikację.
GUIX nic nie bezpośrednio z prostą kanwą, ale aplikacja może użyć prostej kanwy do renderowania złożonego rysunku do buforu poza ekranem, a następnie użyć tego buforu poza ekranem, aby odświeżyć widoczną kanwę w razie potrzeby.

Zarządzana Kanwa jest automatycznie wyświetlana w buforze ramki sprzętowej przez GUIX. Zarządzana Kanwa jest dołączona do tworzenia kanwy złożonej dla systemów z wystarczającą ilością pamięci do obsługi wielu zarządzanych kanw. Zarządzane kanwy mają porządek osi Z obsługiwany przez GUIX, a przycinanie widoków jest wymuszane na wszystkich zarządzanych kanwach.

Kanwa różni się od buforu ramki, tak aby był bardziej ogólny. W systemach z ograniczoną ilością pamięci może istnieć tylko jedna Kanwa, a pamięć dla tej kanwy może być widoczną pamięcią buforu ramek. Jednak w przypadku bardziej złożonych systemów obsługujących bardziej zaawansowane nakładki graficzne i wiele kanwy zarządzanymi kanwami są przydzielone obszary pamięci, które różnią się od pamięci buforu ramki sprzętowej.
Te zarządzane kanwy są renderowane w buforze ramki widocznej podczas operacji odświeżania lub przełączania buforu ramki.

W przypadku sprzętu obsługującego wiele warstw graficznych, czyli wielu przyłożonych buforów ramek, aplikacja może powiązać jedną lub większą liczbę kanw z sprzętową warstwą grafiki przy użyciu interfejsu API ***gx_canvas_hardware_layer_bind*** . Ta usługa informuje kanwę, że jest ona połączona z konkretną sprzętową warstwą grafiki, a po powiązaniu tej kanwy podejmie próbę wykorzystania obsługi sprzętu na potrzeby widoczności kanwy (tj. gx_canvas_show, gx_canvas_hide), kanwy alfa (tj. ***gx_canvas_alpha_set***) i przesunięcie kanwy w obrębie ekranu (***gx_canvas_offset_set***).

W przypadku architektur innych niż najprostsza organizacja pojedynczego kanwy/pojedynczej ramki, rozmiar kanwy jest określany przez aplikację i może być różna od ustalonego rozmiaru buforu ramek.
Może być również przesunięte wybrane przez aplikację. Inne informacje, takie jak porządek osi Z, są utrzymywane na kanwie. Po zakończeniu rysowania kanwy zawartość kanwy przenosi się do ekranu fizycznego przez sterownik wyświetlania. W niektórych systemach, które nie mają wystarczającej ilości pamięci dla oddzielnego obszaru pamięci kanwy i bufora ramek, aktualizacja kanwy jest faktycznie wprowadzana bezpośrednio do ekranu fizycznego za pośrednictwem sterownika wyświetlania.

### <a name="canvas-creation"></a>Tworzenie kanwy 

Obiekt kanwy można utworzyć podczas inicjowania lub w dowolnym czasie podczas wykonywania wątków aplikacji. Nie ma limitu liczby obiektów kanwy, które mogą zostać utworzone przez aplikację. Większość aplikacji, jednak spowoduje utworzenie tylko jednego obiektu kanwy dla całego rysunku GUIX.

### <a name="canvas-control-block"></a>Blok kontrolny kanwy 

Cechy poszczególnych obiektów kanwy znajdują się w bloku sterowania **GX_CANVAS** i są zdefiniowane w **_gx_api. h_**. Pamięć wymagana dla obiektu kanwy jest udostępniana przez aplikację i może znajdować się w dowolnym miejscu w pamięci. Jest to jednak najczęstsze, aby blok sterowania obiektem kanwy i obszar rysowania były globalną strukturą przez definiowanie ich poza zakresem dowolnej funkcji.

### <a name="canvas-alpha-channel"></a>Kanał alfa kanwy

GUIX obsługuje alfa-mieszanie kolorów pierwszego planu i tła na wielu poziomach, łącznie z kanałem alfa mapy bitowej, który określa współczynnik mieszania na piksel, alfa Alpha, który określa współczynnik mieszania dla pędzla na 16 BPP i wyższych głębi kolorów oraz kanwę alfa, która określa współczynnik mieszania dla kanwy nakładki.

Wartość alfa kanwy jest używana, gdy istnieje wiele kanw, które są połączone ze sobą do wyświetlania w buforze ramek. Jeśli Kanwa Z kolejnością jest taka, że Kanwa znajduje się powyżej innych kanw, wartość alfa kanwy może być ustawiona na mieszanie kanwy z tymi, które znajdują się w tym samym miejscu. Szybkie modyfikowanie wartości alfa kanwy służy do zapewnienia "zanikania" efektów przejścia ekranu, ale na wiele sposobów można używać kanwy alfa.

Jeśli Kanwa jest powiązana z sprzętową warstwą grafiki przy użyciu gx_canvas_hardware_layer_bind (), GUIX podejmie próbę zaimplementowania funkcji kanwy alfa, wykorzystując obsługę sprzętową, minimalizując obciążenie oprogramowania związane z mieszaniem kanwy nakładki.

Wartości alfa mieszczą się w przedziale od 0 do 255, gdzie wartość 0 oznacza, że piksel jest w pełni przezroczysty, a wartości większe niż 0 zwiększają mniej przezroczystą wartość alfa kanwy, mogą być obsługiwane tylko dla sterowników ekranu, które działają w 16-BPP i wyższych, chyba że jest dostępna pomoc sprzętowa do mieszania kanwy.

### <a name="canvas-offset"></a>Przesunięcie kanwy 

Kanwa może być przesunięta w ramach widocznego buforu ramki przez wywołanie usługi API ***gx_canvas_offset_set*** . Przesunięcia kanwy są zwykle używane do implementowania animacji Sprite. Jeśli Kanwa jest powiązana z sprzętową warstwą grafiki przez wywołanie funkcji API ***gx_canvas_hardware_layer_bind*** , GUIX podejmie próbę zaimplementowania zmian przesunięcia kanwy przy użyciu obsługi sprzętu, co minimalizuje obciążenie oprogramowania związane z przesuwaniem położenia kanwy.

### <a name="canvas-drawing"></a>Rysowanie kanwy 

Składnik kanwy GUIX zapewnia pełen interfejs API do aplikacji. Przed wywołaniem interfejsów API rysowania, takich jak ***gx_canvas_line_draw*** lub ***gx_canvas_pixelmap_draw*** , należy otworzyć kanwę docelową do rysowania przez wywołanie funkcji interfejsu API ***gx_canvas_drawing_initiate*** . Ta funkcja przygotowuje kanwę do rysowania i tworzenia ***kontekstu rysowania***.

Do rysowania interfejsów API, które są renderowane na kanwie, takich jak ***gx_canvas_line_draw** _ lub _*_gx_canvas_text_draw_*_, użyj parametrów znajdujących się w bieżącym pędzlu kontekstu rysowania, aby zdefiniować styl linii, Szerokość i kolory. Te parametry pędzla są modyfikowane przez wywołanie _*_gx_context_brush_define_*_, _* _gx_context_brush_set_* *, ***gx_context_brush_style_set**_ i podobnych funkcji interfejsu API po ustanowieniu kontekstu rysowania przez wywołanie _ *_gx_canvas_drawing_initiate_* *.

Gdy GUIX wywołuje funkcje rysowania okna i widżetu jako część operacji odświeżania kanwy, zostanie otwarta Kanwa docelowa do rysowania przed wywołaniem funkcji rysowania widżetu. W związku z tym standardowe funkcje rysowania widżetu nie są wymagane do otwarcia docelowej kanwy.

W niektórych przypadkach aplikacja może chcieć wymusić natychmiastowe rysowanie na kanwie. W takim przypadku aplikacja może wykonać następujące czynności.

1. Wywołaj funkcję interfejsu API ***gx_canvas_drawing_initiate*** , przekazując na kanwie docelowej i prostokąt w obrębie tej kanwy, w której aplikacja chce narysować. 

2. Wywołaj dowolną liczbę interfejsów API rysowania kanwy do osiągnięcia żądanego rysunku.

3. Wywołaj funkcję API ***gx_canvas_drawing_complete*** , aby sygnalizować, że rysowanie zostało wykonane. Spowoduje to opróżnienie kanwy do widocznego buforu ramek i/lub wyzwolenie operacji przełączania buforu, w zależności od architektury pamięci systemowej.

### <a name="drawing-apis"></a>Rysowanie interfejsów API 

Istnieje kilka obiektów podstawowych rysowania, które są wymagane przez GUIX do rysowania wszystkich elementów wizualizacji na ekranie. Te rysunkowe interfejsy API mogą być również wywoływane przez oprogramowanie aplikacji, zazwyczaj jako część niestandardowej funkcji rysowania widżetu. Te interfejsy API rysowania kanwy GUIX sprawdzają poprawność i przycinanie parametrów, a następnie przekażą Współrzędne rysowania przyciętego do sterownika wyświetlania dla implementacji rysowania dla sprzętu i formatu kolorów. Te funkcje interfejsu API rysowania są zdefiniowane w następujący sposób.

- gx_canvas_alpha_set
- gx_canvas_arc_draw
- gx_canvas_block_move
- gx_canvas_circle_draw
- gx_canvas_ellipse_draw
- gx_canvas_glyphs_draw
- gx_canvas_hardware_layer_bind
- gx_canvas_hide
- gx_canvas_line_draw
- gx_canvas_offset_set
- gx_canvas_pie_draw
- gx_canvas_pixel_draw
- gx_canvas_pixelmap_blend
- gx_canvas_pixelmap_rotate
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_rotated_text_draw
- gx_canvas_shift
- gx_canvas_show
- gx_canvas_text_draw

Interfejs API rysowania jest wywoływany za pośrednictwem interfejsu API kanwy GUIX i wszystkie rysunki są wykonywane przy użyciu funkcji interfejsu API gx_canvas_ *. Rysowanie odbywa się przy użyciu bieżącego pędzla w bieżącym kontekście rysowania. Wszystkie powyższe funkcje rysowania kształtów mogą być konturowe, wypełnione kolorem kryjącym lub Pixelmap wypełnione zgodnie z definicją bieżącego pędzla. Aby zmodyfikować szerokość, kolor lub wypełnienie konturu kształtu, użyj funkcji interfejsu API gx_context_brush_ *, aby zdefiniować pędzel w bieżącym kontekście rysowania.

Powyższe elementy API rysowania na poziomie aplikacji nie wykonują rzeczywistego rysowania na kanwie, ale zamiast tego weryfikują parametry obiektu wywołującego przed wywołaniem funkcji rysowania poziomu sterownika wyświetlania. Funkcja rysowania na poziomie sterownika faktycznie zapisuje dane pikseli w pamięci kanwy.

GUIX udostępnia funkcje rysowania sterowników podstawowych lub ogólnych dla różnych głębi kolorów, w tym 1, 2, 4, 8, 16, 24 i 32 bitów na piksel (BPP). W niektórych przypadkach domyślna implementacja rysowania oprogramowania jest zastępowana przez przyspieszone wdrożenia sprzętowe dla tych docelowych sprzętowych, które udostępniają akcelerator rysowania 2D.

### <a name="color-depth"></a>Głębokość koloru 

GUIX obsługuje głębie kolorów do 32-BPP oraz monochromatycznych i odcieni szarości. Typ głębi kolorów jest obsługiwany w dużej mierze przez funkcje podstawowego ekranu, a także ma wpływ na ilość pamięci wymaganą dla obszaru rysowania kanwy. Poniżej znajduje się lista wsparcia głębi kolorów wraz z krótkim opisem zmian w tej głębi kolorów.

| &nbsp;Format koloru       | Opis                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| 1-bitowe Monochromatycznie   | 1-bitowe na format opakowany pikseli.                                                                                                   |
| 2-bitowa Skala szarości    | 4 szare poziomy, spakowane cztery piksele na bajt.                                                                                      |
| 4-bitowa Skala szarości    | 16 szarych poziomów, spakowane dwa piksele na bajt.                                                                                      |
| 4-bitowy kolor        | W formacie VGA organizacja pamięci.                                                                                         |
| 8-bitowa Skala szarości    | 256 poziomów szarości                                                                                                                  |
| Tryb palety 8-bitowej | 1 bajt na piksel używany jako indeks palety                                                                                           |
| 8-bitowy r:g: b tryb   | Rzadziej używany format 2:3:2 r:g: b.                                                                                         |
| 16-bitowy             | Każdy piksel wymaga dwóch bajtów. Może to być r:g: b lub b:g: r porządkowania bajtów. Zwykle 5:6:5 strukturę, ale może również mieć strukturę 5:5:5 lub 4:4:4:4 a:r: g:b Structure. |
| 24-bitowe             | Każdy piksel wymaga 3 (spakowanego formatu) lub 4 (unpacked format) bajtów. Może być w r:g: b lub b:g: r o kolejności bajtów zgodnie z wymaganiami sprzętowymi. |
| 32-bitowa             | Każdy piksel wymaga 4 bajtów z kanałem alfa. Może być a:r: g:b lub b:g: r:AA kolejność bajtów i określana przez sprzęt.              |

### <a name="mouse-support"></a>Obsługa myszy 

GUIX obsługuje rysowanie kursora myszy na dowolnej z żądanych kanw. Kursor myszy może być rysowany w oprogramowaniu lub może być obsługiwany przez nakładkę kursora sprzętowego. W obu przypadkach interfejs API udostępniany aplikacji powiązanej z kursorem myszy jest taki sam, niezależnie od tego, czy używasz oprogramowania lub sprzętu kursora myszy.

Obsługa myszy GUIX jest włączona tylko wtedy, gdy `#define GX_MOUSE_SUPPORT` jest zdefiniowana w pliku nagłówkowym gx_user. h przed skompilowaniem biblioteki GUIX.

Aplikacja musi definiować kursor myszy i hotspot przy użyciu funkcji ***gx_canvas_mouse_define*** API. Ten interfejs API akceptuje wskaźnik do kanwy, w której obraz kursora powinien być rysowany, oraz wskaźnik do struktury **GX_MOUSE_CURSOR_INFO** , która definiuje obraz kursora myszy i punkt aktywny obrazu myszy względem lewego górnego rogu obrazu.

## <a name="guix-display-component"></a>Składnik GUIX Display 

Składnik Display jest podstawowy w GUIX, ponieważ zarządza przetwarzaniem wszystkich obiektów wyświetlanych, co w sobie zawiera jedną lub więcej kanw, widżety i okna. Składnik ekranu współdziała również z podstawowym sterownikiem ekranu sprzętowego skojarzonym z każdym wyświetlaczem przez serię wskaźników funkcji.

### <a name="display-creation"></a>Tworzenie ekranu 

Obiekt wyświetlany może być tworzony podczas inicjowania lub w dowolnym czasie podczas wykonywania wątków aplikacji. Zazwyczaj aplikacja tworzy jeden obiekt wyświetlany do zarządzania każdym ekranem fizycznym. Jeśli używasz programu GUIX Studio do definiowania aplikacji i dostępnego fizycznego wyświetlania, będziesz używać funkcji interfejsu API gx_studio_display_configure, aby utworzyć i zainicjować wszystkie ekrany.

### <a name="display-control-block"></a>Wyświetl blok sterowania 

Charakterystyki poszczególnych obiektów wyświetlanych znajdują się w jego bloku sterowania ***GX_DISPLAY** _ i są zdefiniowane w _ *_gx_api. h_* *. Pamięć wymagana dla obiektu wyświetlanego jest udostępniana przez aplikację i może znajdować się w dowolnym miejscu w pamięci. Jednak najbardziej typowym sposobem, aby formant wyświetlania blokował strukturę globalną przez definiowanie go poza zakresem dowolnej funkcji.

### <a name="resource-management"></a>Zarządzanie zasobami 

Zasoby to składniki interfejsu użytkownika, które są używane przez aplikację, ale nie są one kodem aplikacji. Zasoby są danymi aplikacji i są zwykle definiowane statycznie. Typy zasobów obejmują pixelmaps, czcionki, kolory i ciągi. Te zasoby można zmienić w dowolnym momencie, zazwyczaj bez zmiany oprogramowania aplikacji. Ważne jest, aby przechowywać magazyn i odwołania do zasobów oddzielonych od oprogramowania aplikacji, aby umożliwić zmianę wyglądu interfejsu użytkownika bez zmiany kodu aplikacji, ponieważ zmiany oprogramowania aplikacji zwykle wymagają skojarzonych ponownych testów i weryfikacji tego oprogramowania.

Moduł ***wyświetlania*** GUIX umożliwia zarządzanie zasobami dla wszystkich zasobów, które są zależne od głębi kolorów i formatu wyświetlania. Te obiekty obejmują obsługę aktywnej tabeli Pixelmap, aktywnej tabeli czcionek i aktywnej tabeli kolorów. Zasób tabeli ciągów jest obsługiwany przez moduł systemu GUIX, ponieważ zasoby ciągów nie muszą być zwykle zmieniane na podstawie głębi kolorów i formatu.

Oprogramowanie aplikacji odwołuje się do zasobów według identyfikatora zasobu, który jest indeksem w odpowiedniej tabeli zasobów. Pozwala to na zmianę tabeli, na przykład tabela kolorów może zostać zmieniona, gdy produkt zmieni się z "tryb dzień" na "tryb nocny", ale wartości identyfikatora koloru pozostają takie same.

Zasoby aplikacji są zapisywane w pliku zasobów (lub zbiorze plików zasobów) przez aplikację GUIX Studio. Domyślne kolory, pixelmaps i czcionki są udostępniane automatycznie podczas tworzenia nowego projektu GUIX Studio, ale te wartości domyślne są łatwo zastępowane podczas definiowania wyglądu i sposobu działania aplikacji.

Należy pamiętać, że identyfikatory zasobów dla kolorów, czcionek i pixelmaps nie mogą być rozpoznawane jako ich rzeczywiste kolory, czcionki ani wartości Pixelmap, dopóki nie jest znany aktywny składnik ekranu. Ponieważ architektura GUIX obsługuje wiele aktywnych wyświetlaczy, identyfikatory zasobów można rozpoznać tylko do wartości zasobów, gdy widżet i skojarzony z nim identyfikator zasobu można rozpoznać na określonym ekranie. Ta właściwość jest znana jako powiązanie dynamiczne. Identyfikator zasobu dla właściwości, takiej jak kolor tekstu, na przykład identyfikator zasobu **GX_COLOR_ID_TEXT,** może zostać rozpoznany jako 16-bitowa R:G: B wartość biały, gdy jest używany na jednym ekranie, ale ten sam identyfikator koloru może zostać rozpoznany jako czarny kolor czerni, gdy jest używany na innym ekranie.

W ramach tej metody dynamiczne powiązanie identyfikatorów zasobów z wartościami zasobów oznacza, że oprogramowanie aplikacji i GUIX elementy wewnętrzne powinny często rozwiązywać tylko identyfikatory zasobów do wartości zasobów w aktywnym kontekście rysowania. Aktywny kontekst rysowania określa aktualnie aktywne wyświetlanie, co pozwala GUIX na rozpoznawanie każdego identyfikatora zasobu do określonej wartości zasobu. Jeśli oprogramowanie aplikacji jest wymagane do znalezienia określonej wartości zasobu poza kontekstem rysowania, można to zrobić również dla widocznych widżetów. Widoczne widżety są połączone z oknem głównym, które mogą być również używane do rozpoznawania aktywnej kanwy i wyświetlania dla tego widżetu.

Jeśli widżet został utworzony, ale nie został jeszcze wyświetlony (tj. nie został połączony z żadnym oknem głównym ani innym widocznym elementem nadrzędnym), nie można rozpoznać żadnych identyfikatorów zasobów skojarzonych z tym widżetem do określonej wartości zasobu innej niż przez bezpośrednie przeindeksowanie do tabeli zasobów przypisanej do określonego ekranu. Bezpośredni dostęp do konkretnej tabeli zasobów może być bezpiecznie wykonywany przez oprogramowanie aplikacji, ale nigdy nie jest wykonywane w wewnętrznym oprogramowaniu biblioteki GUIX.

### <a name="widget-defaults"></a>Ustawienia domyślne widżetu 

Składnik GUIX Display zawiera również domyślne definicje dla różnych atrybutów widżetu. O ile nie określono inaczej w aplikacji, widżety/okna są tworzone z tymi atrybutami systemowymi. Te atrybuty systemowe składają się głównie z czcionek, kolorów i map bitowych przechowywanych w tabelach zasobów systemowych. Dodatkowe atrybuty domyślnego wyglądu paska przewijania są również obsługiwane przez składnik GUIX Display.

Domyślne ustawienia kolorów są definiowane przez tabelę kolorów przypisaną do każdego ekranu oraz wstępnie zdefiniowanymi domyślnymi identyfikatorami kolorów. Te domyślne identyfikatory kolorów obejmują następujące elementy.

| Identyfikator koloru | Opis |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| GX_COLOR_ID_CANVAS | Kolor domyślnej kanwy (tj. tła wyświetlania) |
| GX_COLOR_ID_WIDGET_FILL | Domyślny kolor wypełnienia widżetu |
| GX_COLOR_ID_WINDOW_FILL | Kolor wypełnienia okna domyślnego |
| GX_COLOR_ID_DISABLED_FILL | Kolor wypełnienia domyślnego wyłączonego widżetu |
| GX_COLOR_ID_DEFAULT_BORDER | Domyślny kolor obramowania widżetu |
| GX_COLOR_ID_WINDOW_BORDER | Domyślny kolor obramowania okna |
| GX_COLOR_ID_TEXT | Domyślny kolor tekstu |
| GX_COLOR_ID_SELECTED_TEXT | Domyślny wybrany kolor tekstu |
| GX_COLOR_ID_DISABLED_TEXT | Domyślny kolor wyłączonego tekstu |
| GX_COLOR_ID_SELECTED_TEXT_FILL | Domyślny kolor wypełnienia zaznaczonego tekstu |
| GX_COLOR_ID_READONLY_TEXT | Domyślny kolor tekstu tylko do odczytu |
| GX_COLOR_ID_READONLY_FILL | Domyślny kolor wypełnienia tekstu w trybie tylko do odczytu |
| GX_COLOR_ID_SCROLL_FILL |    Kolor wypełnienia paska przewijania |
| GX_COLOR_ID_SCROLL_BUTTON | Kolor wypełnienia przycisku paska przewijania |
| GX_COLOR_ID_SHADOW | Domyślny kolor cienia |
| GX_COLOR_ID_SHINE | Domyślny kolor wyróżnienia |
| GX_COLOR_ID_BUTTON_BORDER | Kolor obramowania widżetu przycisku. |
| GX_COLOR_ID_BUTTON_UPPER | Górny kolor wypełnienia widżetu przycisku |
| GX_COLOR_ID_BUTTON_LOWER | Kolor dolnego wypełnienia widżetu przycisku |
| GX_COLOR_ID_BUTTON_TEXT | Kolor tekstu widżetu przycisku. |
| GX_COLOR_ID_TEXT_INPUT_TEXT | Kolor tekstu widżetu wprowadzania tekstu |
| GX_COLOR_ID_TEXT_INPUT_FILL | Kolor wypełnienia tekstu wejściowego |
| GX_COLOR_ID_SLIDER_TICK | Kolor używany do rysowania znaczników suwaka. |
| GX_COLOR_ID_SLIDER_GROOVE_BOTTOM | Kolor używany do rysowania rowka suwaka |
| GX_COLOR_ID_SLIDER_NEEDLE_OUTLINE | Kolor używany do rysowania konspektu wskazówki |
| GX_COLOR_ID_SLIDER_NEEDLE_FILL | Kolor używany do wypełnienia wskazówki suwaka |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE1 | Kolor używany do rysowania podświetlenia wskazówki |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE2 | Kolor używany do rysowania cienia wskazówki |

Te wartości identyfikatora koloru są mapowane na określoną wartość koloru, zgodnie z definicją tabeli kolorów przypisanej do każdego ekranu. Te wartości domyślne można zmienić jako grupę jednego wyświetlania, wywołując funkcję API ***gx_display_color_table_set*** . Jeśli używasz programu GUIX Studio, tabela kolorów wyświetlania jest automatycznie inicjowana, gdy aplikacja wywoła funkcję ***gx_studio_display_configure*** .

Składnik GUIX Display utrzymuje również domyślną tabelę czcionek. Domyślna tabela czcionek definiuje czcionkę używaną przez każdy typ widżetu, chyba że jest to określone przez aplikację. Wstępnie zdefiniowane identyfikatory tabeli czcionek wyświetlanych zawierają następujące wartości.

| &nbsp;Identyfikator czcionki | Opis |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------|
| GX_FONT_ID_DEFAULT | Domyślna czcionka używana, gdy nie jest zdefiniowana określona czcionka |
| GX_FONT_ID_BUTTON | Domyślna czcionka używana dla całego tekstu na przyciskach |
| GX_FONT_ID_TEXT_INPUT | Domyślna czcionka używana dla pól edycji tekstu |

Identyfikator czcionki używany przez widżet typu text można ponownie przypisać przy użyciu **gx_<widget_type>_font_set** interfejsu API dla każdego typu widżetu powiązanego z tekstem. Całą tabelę czcionek można ponownie przypisać, wywołując funkcję API **gx_display_font_table_set** .

### <a name="scrollbar-appearance"></a>Wygląd paska przewijania 

GUIX Display obsługuje również domyślne ustawienia wyglądu ScrollBar dla tego ekranu. Te ustawienia są definiowane przez strukturę **GX_SCROLLBAR_APPEARANCE** , która została zdefiniowana poniżej. GUIX Display zachowuje jedną strukturę wyglądu ScrollBar dla pionowych pasków przewijania i drugą strukturę dla poziomego paska przewijania. Aplikacja może zmodyfikować domyślny wygląd ScrollBar dla dowolnego ekranu, inicjując strukturę **GX_SCROLLBAR_APPEARANCE** i wywołując funkcję interfejsu API ***gx_display_scroll_appearance_set***.

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```
| GX_SCROLLBAR_APPEARANCE składowa struktury | Opis |
| --- | --- |
| gx_scroll_width | Szerokość pionowego paska przewijania lub wysokości poziomego paska przewijania w pikselach. |
| gx_scroll_thumb_width | Szerokość przycisków windy i End w pikselach. |
| gx_scroll_thumb_travel_max | Przesunięcie od końca paska przewijania do maksymalnego punktu podróży przycisku przewijania. |
| gx_scroll_fill_pixelmap | Pixelmap używany do wypełnienia tła przewijania. |
| gx_scroll_thumb_pixelmap | Pixelmap używany do rysowania przycisku przewijania. |
| gx_scroll_up_pixelmap | Pixelmap używany do rysowania przycisku przewijania w górę. |
| gx_scroll_down_pixelmap | Pixelmap używany do rysowania przycisku przewijania w dół. |
| gx_scroll_fill_color | Identyfikator koloru koloru używany do wypełnienia tła paska przewijania. |
| gx_scroll_button_color | Identyfikator koloru koloru używany do wypełniania przycisku kciuka paska przewijania. |

Oprócz tych domyślnych ustawień czcionek, kolorów i stylów, aplikacja może określić dowolne parametry w przypadku, gdy jest to potrzebne, przy użyciu interfejsu API dostarczonego przez każdy typ widżetu.

### <a name="skinning-and-themes"></a>Karnacje i motywy

Tworzenie karnacji umożliwia GUIX widżetów i systemu Windows łatwe zmienianie wyglądu podstawowego, tj. zmiana "skórka" w jednym miejscu spowoduje zmianę wyglądu podstawowych wszystkich skojarzonych widżetów i okien.

Ponowne tworzenie karnacji aplikacji GUIX wymaga podania nowego koloru, czcionki lub tabeli Pixelmap do tabel zasobów wyświetlania GUIX. Ponieważ wszystkie widżety GUIX odnoszą się do ich koloru, mapy bitowej lub czcionki według identyfikatora zasobu, dzięki czemu Nowa tabela zasobów automatycznie powoduje, że wszystkie widżety GUIX zaczynają korzystać z nowych kolorów i pixelmaps, gdy narysują się na żądanym ekranie.

Nowy zestaw czcionek, kolorów i pixelmaps, które są zaprojektowane tak, aby zapewnić atrakcyjny wygląd, nazywa się *motywem*. Motyw definiuje zestaw tabel zasobów i rozmiar każdej tabeli zasobów. Można zdefiniować dowolną liczbę motywów dla dowolnego ekranu za pomocą aplikacji GUIX Studio. Należy przekazać początkowy indeks motywu do ***gx_studio_display_configure*** funkcji wygenerowanej przez program GUIX Studio, która instaluje początkowy motyw w utworzonym ekranie. Aktywny motyw dla dowolnego ekranu można zmienić w dowolnym momencie, wywołując funkcję ***gx_display_theme_install***.

### <a name="root-window"></a>Okno główne

Dla każdej widocznej kanwy utworzonej przez aplikację, aplikacja musi również utworzyć jedno okno główne dla tej kanwy. To specjalne okno zasadniczo działa jako kontener dla wszystkich okien i elementów widget najwyższego poziomu. Główne okno rysuje tło kanwy, a ponieważ okno główne pochodzi od klasy **GX_WINDOW** , okno główne może również mieć tapetę. Aby zmienić kolor tła ekranu lub kanwy, wystarczy zmienić kolor wypełnienia głównego okna dołączonego do tej kanwy.

W przypadku korzystania z funkcji wygenerowanej przez program GUIX Studio o nazwie ***gx_studio_display_configure*** w celu skonfigurowania ekranów, Kanwa i okno główne dla każdego ekranu są tworzone jako część tej funkcji inicjującej.

### <a name="anti-aliasing"></a>Wygładzanie 

Wygładzanie to funkcja opcjonalna w GUIX, która jest używana do wygładzania linii, krzywych i czcionek. Wygładzanie jest obsługiwane tylko w przypadku uruchamiania z sterownikiem wyświetlania korzystającym z 16-BPP lub większej głębi kolorów.

Rysowanie linii z wygładzonymi aliasami jest włączane przez ustawienie **GX_BRUSH_ALIAS** Flash w aktywnym pędzlu. Dotyczy to linii rysowanych bezpośrednio, a także do linii rysowanych jako obramowanie wielokąta lub okręgu.

Obraz z wygładzonymi aliasami jest włączany przy użyciu czcionki z aliasami, która jest generowana przez aplikację GUIX Studio. Należy określić, czy czcionka ma być generowana jako antyaliasowa, czy binarna podczas tworzenia czcionki.
Czcionki antyaliasowe w programie GUIX wykorzystują 16 poziomów przezroczystości dla każdego piksela.

### <a name="clipping"></a>Wycinka 

Przycinanie jest obsługiwane wewnętrznie przez składnik GUIX Display, a w warstwach okna i widżetu według architektury nadrzędny-podrzędny obsługiwanej przez widżety GUIX. Żadne okno ani widżet nie mogą być narysowane poza obszarem tego widżetu, a element widget nie może być rysowany poza obszarem nadrzędnym tego widżetu.

Zapobiega to również rysowaniu elementów widget ze współrzędnych pikseli, które wykraczają poza pamięć kanwy, co może prowadzić do uszkodzenia pamięci lub awarii systemu. Elementy widget nie mogą rysować poza obszarem elementu widget, obszaru nadrzędnego widżetu lub poza zakresem kanwy.

Ponadto Widżety mogą być rysowane tylko w obszarach, które wcześniej zostały oznaczone jako zanieczyszczone. Pozwala to uniknąć rysowania całego okna, na przykład po wyjęciu tylko rogu okna. Tylko część okna, która rzeczywiście wymaga odświeżenia, jest oznaczona jako zanieczyszczona i dlatego funkcja rysowania okna tylko w rzeczywistości odświeża piksele w obszarze zanieczyszczonym.

Składnik wyświetlania GUIX wymusza te algorytmy przycinające przed wywołaniem funkcji rysowania na poziomie sterownika.

### <a name="views"></a>Widoki 

GUIX zawsze utrzymuje zestaw widoków dla każdego głównego okna i każdego okna podrzędnego okna głównego. Widoki to dynamiczny, ustalony w czasie wykonywania obszar przycinania, który zmienia się w miarę pozycji okna i porządek osi Z.
GUIX używa widoków, aby zapobiec rysowaniu okna lub widżetu w tle z rysowania na wierzchu okna lub widżetu na pierwszym planie. Widoki wymuszają dyscyplinę porządku osi Z. Ponadto widoki są ważne dla wydajności, ponieważ uniemożliwiają przełączenie okna w tle do dowolnego obszaru kanwy, którego nie można zobaczyć. Jeśli okno jest w pełni pokrywane przez inne okno, przedziały czasu nie będzie można rysować na kanwie, nawet jeśli zostanie podjęta próba wykonania tej czynności.

### <a name="display-driver-interface"></a>Interfejs wyświetlania sterowników 

Sterowniki wyświetlania GUIX są odpowiedzialne za wszystkie interakcje z podstawowym ekranem fizycznym. Sterowniki wyświetlania mają trzy podstawowe funkcje: inicjalizacja, rysowanie i wyświetlanie buforu ramek.
Inicjalizacja jest odpowiedzialna za przygotowanie fizycznego sprzętu do wyświetlania, informując o GUIX właściwości fizycznego sprzętu ekranu oraz o wykorzystaniu GUIX, które określone funkcje rysowania powinny być używane. Główna Inicjalizacja sterownika ekranu jest wywoływana z funkcji GUIX ***gx_display_create*** . Ponadto wątek GUIX będzie również wywoływał inicjalizację pomocniczego sterownika wyświetlania z kontekstu wątku. Ten pomocniczy sterownik ekranu jest wymagany tylko wtedy, gdy sterownik wymaga usług RTO podczas jego inicjowania, np. przerwanie urządzenia lub ***tx_thread_sleep*** żądania opóźnienia między krokami procesu inicjowania.

Po zakończeniu inicjalizacji sterownik ekranu jest odpowiedzialny za dowolne bezpośrednie rysowanie, które można wykonać za pomocą fizycznego ekranu sprzętowego.
Na koniec sterownik ekranu jest odpowiedzialny za wyświetlanie buforu ramek.

## <a name="guix-widget-component"></a>Składnik widżetu GUIX

Widżet GUIX jest widocznym elementem graficznym. Istnieją składniki GUIX, które nie są widoczne, takie jak czasomierze i funkcje narzędzia matematycznego.
Jednak wszystkie widoczne składniki są uzyskiwane z podstawowego składnika widżetu GUIX. Widżet GUIX jest głównym blokiem konstrukcyjnym wyświetlania GUIX — wszystkie inne elementy graficzne są wyprowadzane z podstawowej funkcjonalności widżetu.

Widżety GUIX są implementowane w sposób zorientowany obiektowo z pełnym wsparciem dziedziczenia. Jest to realizowane przy użyciu ANSI C, co skutkuje najmniejszą możliwą ilością pamięci i wymaganiem do przetwarzania. Gdy będziemy mówić do jednego z elementów widget, takich jak **GX_BUTTON**, są one *uzyskiwane z* innego widżetu, takiego jak **GX_WIDGET** podstawowy, co oznacza, że struktura kontrolki **GX_BUTTON** zawiera wszystkie zmienne składowe i wskaźniki funkcji **GX_WIDGET**, z pewnymi dodatkowymi zmiennymi, które są specyficzne dla **GX_BUTTON**. GUIX kompiluje warstwy widżetów w ten sposób, aby bardziej złożone widżety były zawsze oparte na prostszym widżecie przed nimi. Ten hierarchiczny model wyprowadzania ułatwia naukę interfejsów API służących do modyfikowania parametrów widżetu. Jeśli chcesz zmodyfikować kolor przycisku, użyj tego samego interfejsu API, który służy do modyfikowania koloru widżetu, mianowicie ***gx_widget_fill_color_set***.

Organizacja widocznych widżetów jest utrzymywana w sposób nadrzędny-podrzędny przy użyciu list strukturalnych drzewa łączenie elementów widgetów podrzędnych z ich elementami nadrzędnymi. Elementy podrzędne dziedziczą cechy z obiektów nadrzędnych, takich jak widoki, do których mogą się rysować, oraz kanwę, na której narysują.
Elementy widget podrzędne mogą mieć własne widżety podrzędne i ponownie dziedziczyć różne cechy z elementu nadrzędnego. Charakterystyki dowolnego widżetu można jawnie zdefiniować za pomocą różnych wywołań interfejsu API GUIX.

### <a name="widget-creation"></a>Tworzenie widżetu 

Obiekt widget można utworzyć podczas inicjalizacji lub w dowolnym czasie podczas wykonywania wątków aplikacji. Nie ma limitu liczby obiektów widżetów, które mogą zostać utworzone przez aplikację. Nie ma również żadnego limitu liczby elementów podrzędnych dowolnego elementu widget, w granicach pamięci sprzętu docelowego.

Każdy typ widżetu ma własną funkcję Create, taką jak ***gx_button_create** _ lub _ *_gx_prompt_create_* *. Trzy pierwsze parametry tych funkcji są zawsze takie same, jak wskaźnik do struktury kontrolki widget, wskaźnik ciągu do nazwy widżetu i wskaźnik do elementu nadrzędnego widżetu. Każda funkcja Create może mieć dowolną liczbę dodatkowych parametrów w zależności od wymagań tego typu widżetu.

### <a name="widget-control-block"></a>Element widget — blok 

Charakterystyka każdego obiektu widget znajduje się w jego bloku sterowania **GX_WIDGET** i są zdefiniowane w **_gx_api. h_**. Pamięć wymagana dla obiektu widget jest udostępniana przez aplikację i może znajdować się w dowolnym miejscu w pamięci. Jednak najczęściej jest to, że formant obiektu widget blokuje strukturę globalną, definiując ją poza zakresem dowolnej funkcji. Jeśli używasz programu GUIX Studio, bloki kontrolne widżetu mogą być przydzielane statycznie w pliku specyfikacji programu Studio lub mogą być przydzielane dynamicznie przez aplikację.

### <a name="dynamic-widget-control-block-allocation-and-de-allocation"></a>Alokacja bloku dynamicznego formantu widget i cofnięcie alokacji 

W przypadku korzystania z alokacji bloku dynamicznej kontroli należy zdefiniować dwie funkcje, które będą używane przez GUIX do przydzielania i zwalniania pamięci wymaganej dla bloków formantów widżetu. Funkcje zarządzania pamięcią są przesyłane do składnika systemu GUIX za pośrednictwem funkcji interfejsu API ***gx_system_memory_allocator_set*** . Ta funkcja umożliwia przekazanie dwóch wskaźników funkcji do GUIX: pierwszy jest wskaźnikiem do funkcji alokacji pamięci, a drugi jest wskaźnikiem do funkcji wolnej od pamięci. W większości przypadków te funkcje zostaną wdrożone przy użyciu pul ThreadX bajtów, ale konstrukcja GUIX umożliwia zaimplementowanie dynamicznego zarządzania pamięcią w dowolny preferowany sposób.

Dynamiczna alokacja widżetu jest najczęściej wykorzystywana w pliku specyfikacji aplikacji wygenerowanych przez program Studio, po wybraniu opcji "dynamicznie przydzielone" w polu właściwości widżetu Studio. Można jednak również użyć alokacji bloku dynamicznej kontroli w aplikacji. Jeśli używasz alokacji bloku kontroli dynamicznej w aplikacji, należy wywołać funkcję API ***gx_widget_allocate** _, aby przydzielić blok kontrolki elementu widget. Następnie podczas tworzenia widżetu upewnij się, że flaga stylu _ *GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** (wraz z innymi wymaganymi flagami stylu) została przekazana do funkcji widget Create. Ta flaga służy do oznaczania widżetu jako dynamicznego przydzielenia w polu Stan widżetu. Gdy element widget zostanie później usunięty przy użyciu **_gx_widget_delete_**, GUIX sprawdzi to pole stanu i automatycznie wywołaj funkcję dealokatora pamięci, aby upewnić się, że nie ma żadnych przecieków pamięci.

> [!IMPORTANT]
> Widżet utworzony przy użyciu dynamicznie przydzielnego bloku sterowania musi być utworzony przy użyciu flagi **GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** stylu, aby zapobiec utracie pamięci.

### <a name="types"></a>Typy

GUIX zapewnia bogaty i w pełni funkcjonalny zestaw wbudowanych elementów widget. Jak wspomniano wcześniej, wszystkie wyspecjalizowane elementy widget pochodzą od podstawowego elementu widget. Poniżej znajduje się lista wbudowanych elementów widget w programie GUIX:

**GX_TYPE_WIDGET**

**GX_TYPE_BUTTON**

**GX_TYPE_TEXT_BUTTON**

**GX_TYPE_MULTI_LINE_TEXT_BUTTON**

**GX_TYPE_RADIO_BUTTON**

**GX_TYPE_CHECKBOX**

**GX_TYPE_PIXELMAP_BUTTON**

**GX_TYPE_ICON_BUTTON**

**GX_TYPE_ICON**

**GX_TYPE_SPRITE**

**GX_TYPE_SLIDER**

**GX_TYPE_PIXELMAP_SLIDER**

**GX_TYPE_VERTICAL_SCROLL**

**GX_TYPE_HORIZONTAL_SCROLL**

**GX_TYPE_PROGRESS_BAR**

**GX_TYPE_PROMPT**

**GX_TYPE_NUMERIC_PROMPT**

**GX_TYPE_PIXELMAP_PROMPT**

**GX_TYPE_NUMERIC_PIXELMAP_PROMPT**

**GX_TYPE_SINGLE_LINE_TEXT_INPUT**

**GX_TYPE_MULTI_LINE_TEXT_VIEW**

**GX_TYPE_MULTI_LINE_TEXT_INPUT**

**GX_TYPE_WINDOW**

**GX_TYPE_ROOT_WINDOW**

**GX_TYPE_VERTICAL_LIST**

**GX_TYPE_HORIZONTAL_LIST**

**GX_TYPE_POPUP_LIST**

**GX_TYPE_DROP_LIST**

**GX_TYPE_LINE_CHART**

**GX_TYPE_DIALOG**

**GX_TYPE_KEYBOARD**

**GX_TYPE_SCROLL_WHEEL**

**GX_TYPE_TEXT_SCROLL_WHEEL**

**GX_TYPE_STRING_SCROLL_WHEEL**

**GX_TYPE_NUMERIC_SCROLL_WHEEL**

**GX_TYPE_CIRCULAR_GAUGE**

**GX_TYPE_RADIAL_PROGRESS_BAR**

**GX_TYPE_RADIAL_SLIDER**

**GX_TYPE_MENU_LIST**

**GX_TYPE_MENU**

**GX_TYPE_ACCORDION_MENU**

**GX_TYPE_TREE_VIEW**


### <a name="styles"></a>Style

Style widżetu składają się z elementów, takich jak właściwości obramowania (wywoływane, wgłębienie, cienkie, grube lub bez planszy), a także właściwości dla określonych typów widżetów, jak wymieniono wcześniej. Flagi stylu widżetu oferują najprostszą metodę modyfikowania wyglądu dowolnego widżetu.
Początkowy styl widżetu jest zawsze parametrem przesłanym do funkcji Create dla typu widget.

### <a name="colors"></a>Kolory 

Widżety rysują same kolory zdefiniowane w tabeli koloru systemu.
Identyfikatory kolorów są definiowane dla tła kanwy, domyślnego koloru wypełnienia widżetu, koloru wypełnienia przycisku, koloru wypełnienia widżetu, koloru okna i kilku innych wartości domyślnych koloru. Ponadto obiekty **GX_WINDOW** obsługują wyświetlanie mapy bitowej lub tapety w miarę wypełniania klienta okna.

Najprostszą metodą zmiany domyślnego schematu kolorów jest użycie programu GUIX Studio i utworzenie lub zdefiniowanie schematu kolorów spełniającego Twoje wymagania.
Możesz również zdefiniować schemat kolorów ręcznie, tworząc tablicę wartości GX_COLOR i wywołując funkcję interfejsu API gx_system_color_table_set.

### <a name="event-notification"></a>Powiadomienie o zdarzeniu 

Zdarzenia GUIX są żądaniami skierowanymi do co najmniej jednego widżetu w celu wykonania określonej akcji i powiadomień w celu powiadomienia widżetów o zmianach stanu systemu. Na przykład gdy widżet uzyska fokus, **GX_EVENT_FOCUS_GAINED** jest wysyłany do widżetu za pośrednictwem usługi ***gx_system_event_send*** API.

Zdarzenia są przesyłane przez kolejkę zdarzeń GUIX, a każde zdarzenie jest wystąpieniem struktury danych **GX_EVENT** . Struktura danych **GX_EVENT** jest definiowana w ***gx_api. h***, jednak najważniejsze pola struktury to **gx_event_type**, **gx_event_sender**, **gx_event_target** i **gx_event_payload**.

Pole **gx_event_type** służy do identyfikowania konkretnej klasy zdarzeń. Typ zdarzenia wskazuje, czy jest to na przykład zdarzenie **GX_EVENT_PEN_DOWN** lub zdarzenie **GX_EVENT_TIMER** . **Gx_event_payload** jest złożeniem różnych pól danych i nie są one prawidłowe dla każdego typu zdarzenia.
Najpierw należy użyć pola Typ zdarzenia przed zbadaniem innych pól danych zdarzenia.

Pole **gx_event_sender** zawiera identyfikator widżetu, który wygenerował zdarzenie, jeśli zdarzenie jest powiadomieniem dla widżetu podrzędnego.

Pole **gx_event_target** może służyć do kierowania zdarzeń zdefiniowanych przez użytkownika do określonego okna lub widżetu. Jeśli chcesz wysłać zdarzenie do określonego okna, należy nadać oknie unikatową wartość identyfikatora (aby można było zidentyfikować ją pozytywnie) i podczas kompilowania zdarzenia umieścić wartość identyfikatora okna w polu **gx_event_target** . Jeśli nie znasz identyfikatora obiektu docelowego lub jeśli chcesz, aby zdarzenie było kierowane do widżetu z fokusem wprowadzania, upewnij się, że pole **gx_event_target** ma wartość 0.

Na koniec pole **gx_event_payload** jest złożeniem różnych typów danych. W przypadku zdarzeń **GX_EVENT_PEN_DOWN** i **GX_EVENT_PEN_UP** pole **gx_event_pointdata** zawiera współrzędne x, y, które przesuwają położenie pióra. Dla zdarzeń czasomierza pole **gx_event_timer_id** zawiera identyfikator wygasłego czasomierza. Inne pola danych ładunku są wykorzystywane dla innych typów zdarzeń. Kompletna lista wstępnie zdefiniowanych typów zdarzeń i ich pól ładunku jest definiowana w [załączniku E-GUIX opisy zdarzeń](appendix-e.md).

Aplikacja może również dodać własne zdarzenia niestandardowe, rozpoczynając od wartości numerycznej po stałej **GX_FIRST_APP_EVENT**. Wszystkie numery zdarzeń po tej stałej są zarezerwowane do użytku aplikacji. Oczywiście program obsługi zdarzeń widżetu aplikacji musi mieć przetwarzanie dla zdarzeń aplikacji.

### <a name="event-processing"></a>Przetwarzanie zdarzeń 

Istnieje domyślna funkcja przetwarzania zdarzeń widżetu dla każdego elementu widget i każdego widżetu o nazwie ***gx_<widżecie-type>_event_process***. W większości przypadków aplikacja nie musi martwić się o obsługę zdarzeń dla danego widżetu. Jednak w sytuacjach, gdy aplikacja wymaga niestandardowego lub uzupełniającego przetwarzania zdarzeń, aplikacja może zastąpić domyślną funkcję przetwarzania za pomocą interfejsu API GUIX ***gx_widget_event_process_set***. Ta funkcja przesłania domyślną funkcję przetwarzania zdarzeń za pomocą funkcji przetwarzania funkcji zdarzeń określonej w interfejsie API.

> [!IMPORTANT]
> Funkcje przetwarzania zdarzeń aplikacji mogą korzystać z zalet (tj. nieduplikowania przetwarzania) w domyślnym przetwarzaniu przez bezpośrednie wywoływanie domyślnego przetwarzania ***gx_widget_event_process*** .

Przetwarzanie zdarzeń jest wywoływane wyłącznie z kontekstu wewnętrznego wątku systemowego GUIX. W ten sposób wymagania dotyczące stosu do przetwarzania obsługi zdarzeń dotyczą tylko wątku GUIX.

### <a name="implementing-custom-event-processing-example"></a>Implementowanie niestandardowego przetwarzania zdarzeń (przykład) 

Możesz zapewnić własną funkcję przetwarzania zdarzeń dla dowolnego widżetu lub okna w systemie GUIX. Jeśli tworzysz własny niestandardowy typ widżetu, zwykle zainstalujesz niestandardowy program obsługi zdarzeń w funkcji tworzenia widżetu. Jeśli po prostu rozszerzasz lub modyfikujesz operację istniejącego widżetu lub okna, możesz wywołać funkcję interfejsu API gx_widget_event_process_set po utworzeniu widżetu lub okna. Prawie zawsze zapewnimy obsługę zdarzeń dla okien najwyższego poziomu (nazywanych również ekranami), aby przetwarzać zdarzenia generowane przez kontrolki podrzędne. Przetwarzanie zdarzeń generowanych przez kontrolki podrzędne ekranu jest głównym sposobem dodawania funkcji do aplikacji GUIX.

Załóżmy na przykład, że zdefiniujesz ekran najwyższego poziomu o nazwie "main_menu".
Ten ekran można zdefiniować za pomocą programu GUIX Studio lub można utworzyć ten ekran w kodzie aplikacji. Jeśli zdefiniujesz ekran w programie GUIX Studio, po prostu wpisz nazwę programu obsługi zdarzeń w polu właściwości Studio dla tego ekranu, a kod specyfikacji wygenerowany przez Studio automatycznie zainstaluje procedurę obsługi zdarzeń. W takim przypadku wywołamy niestandardową procedurę obsługi zdarzeń ***main_menu_event_handler*** i powinny być one kodowane w następujący sposób:

```C
int main_menu_item; /* example: variable to keep track of selected item */

UINT main_menu_event_handler(GX_WINDOW *main_screen, GX_EVENT *event_ptr)
{
    UINT status = GX_SUCCESS;

    switch(event_ptr->gx_event_type)
    {
    /* this is an example for catching events from a child button */
    case GX_SIGNAL(IDB_CHILD_BUTTON, GX_EVENT_CLICKED):
        /* insert your button handler code here */
        break;

    case GX_EVENT_SHOW:
        /* add functionality to the show event handler */
        /* first, do default processing */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */

        /* now add my own processing */
        main_menu_item = 0;
        break;

    default:
        /* pass all other events to base processing function */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */
        break;
    }
    return status;
}
```

W powyższym przykładzie należy zauważyć, że w przypadku zdarzeń systemowych, takich jak **GX_EVENT_SHOW** (zdarzenia wygenerowane wewnętrznie w celu powiadomienia widżetu o zmianie stanu), aplikacja musi przekazać te zdarzenia do podstawowej funkcji przetwarzania zdarzeń widżetu, aby upewnić się, że wykonywane jest normalne przetwarzanie. Następnie aplikacja może dodać dodatkową logikę zgodnie z potrzebami. Wszystkie zdarzenia, które nie są obsługiwane przez aplikację (przypadek domyślny powyżej), powinny być również przesyłane do podstawowej funkcji przetwarzania zdarzeń. Ponieważ ten przykład dotyczył ekranu najwyższego poziomu na podstawie **GX_WINDOW**, domyślna funkcja przetwarzania zdarzeń jest gx_window_event_process.

### <a name="drawing-function"></a>Funkcja rysowania 

Wszystkie rysunki widżetu są wykonywane niezależnie od obsługi zdarzeń. Jest to bardziej wydajne, ponieważ rysowanie jest zazwyczaj kosztowne w odniesieniu do cykli procesora. Implementując algorytm odroczonego rysowania, wszystkie zdarzenia oczekujące i skojarzone zmiany wyświetlania mogą zostać wykonane przed ukończeniem rysowania, co eliminuje marnowanie rysunku. Podobnie jak w przypadku przetwarzania zdarzeń, istnieje domyślna funkcja rysowania widżetu dla większości widżetów o nazwie ***gx_<widżecie-type>_draw***, gdzie xxx jest typem widgetu. W większości przypadków aplikacja nie musi martwić się o funkcję rysowania danego widżetu. Jednak w sytuacjach, gdy aplikacja wymaga niestandardowego lub uzupełniającego rysowania, aplikacja może przesłonić domyślną funkcję rysowania za pomocą interfejsu API GUIX ***gx_widget_draw_set***. Ta funkcja umożliwia aplikacji udostępnianie własnej niestandardowej funkcji rysowania dla dowolnego elementu widget. Dzięki temu aplikacja może definiować wszystkie nowe typy widżetów.

> [!IMPORTANT]
> Funkcje rysowania aplikacji mogą korzystać z zalet (tj. nieduplikowania kodowania) domyślnego rysowania przez wywołanie go bezpośrednio z zastąpionej funkcji rysowania.

Rysunek widżetu jest wywoływany wyłącznie z kontekstu wewnętrznego wątku systemowego GUIX. W ten sposób wymagania dotyczące chronometrażu i stosu do przeprowadzenia rysowania dotyczą tylko wątku GUIX.

### <a name="implementing-custom-drawing-example"></a>Implementowanie niestandardowego rysowania (przykład) 

Funkcja rysowania dla każdego elementu widget jest przywoływana przez pośredni wskaźnik funkcji, który jest elementem członkowskim bloku sterowania GX_WIDGET. Jeśli używasz programu GUIX Studio do definiowania widżetu, możesz zainstalować własny wskaźnik funkcji, wpisując nazwę funkcji w parametrze "funkcja rysowania" właściwości widżetu, a program Studio zainstaluje wskaźnik funkcji dla użytkownika po utworzeniu elementu widget. Jeśli utworzysz widżet w kodzie aplikacji, musisz użyć funkcji API ***gx_widget_draw_set*** , aby zainstalować funkcję niestandardowego rysowania po utworzeniu elementu widget.

Na potrzeby tego przykładu Załóżmy, że chcesz dostosować wygląd przycisku. Ten przycisk będzie wyglądać bardzo podobnie do **GX_TEXT_BUTTON**, ale dodamy Rozrysowanie małej zielonej mapy bitowej "LED_ON" w prawej części przycisku po naciśnięciu przycisku, a mała Mapa bitowa "LED_OFF", gdy przycisk nie zostanie wciśnięty. Chcemy utworzyć przycisk, który wygląda jak ilustracje poniżej.

![Zrzut ekranu przedstawiający zielony przycisk na włączony.](./media/guix/image4.jpg) przycisk niestandardowy "on"

![Zrzut ekranu przedstawiający czerwony przycisk na wyłączony.](./media/guix/image5.jpg) przycisk niestandardowy "off"

W takim przypadku będziemy pisać funkcję rysowania przycisku, która wygląda podobnie do poniższego.

```C
UINT my_button_draw(GX_TEXT_BUTTON *button)
{
    GX_PIXELMAP *map;
    ULONG button_style;
    INT xpos;
    INT ypos;

    /* first, do the normal text button drawing */
    gx_text_button_draw(button);

    /* now add our extra pixelmap */

    gx_widget_style_get(button, &button_style);

    if (button_style & GX_STYLE_BUTTON_PUSHED)
    {
        /* use the ON pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_ON, &map);
    }
    else
    {
        /* use the OFF pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_OFF, &map);
    }
    if (map)
    {
        /* draw it 20 pixels in from right edge */
        xpos = button->gx_widget_size.gx_rectangle_right;
        xpos -= map->gx_pixelmap_width + 20;

        /* and draw 10 pixels from the top edge */
        ypos = button->gx_widget_size.gx_rectangle_top + 10;

        /* draw the extra pixelmap on top of the button */
        gx_canvas_pixelmap_draw(xpos, ypos, map);
    }
}
```

## <a name="guix-drawing-context-component"></a>Składnik kontekstu rysowania GUIX 

Kontekst rysowania jest tworzony dynamicznie w czasie wykonywania, ponieważ GUIX wykonuje każdą operację odświeżania kanwy. Kontekst rysowania łączy się ze kanwą, sterownikiem ekranu i pędzlem używanym do wykonywania bieżących operacji rysowania.

Kontekst rysowania jest definiowany przez strukturę **GX_DRAW_CONTEXT** .
Ta struktura zawiera zmienne, które definiują przycinanie i widok bieżącej operacji rysowania, definiują bieżącą kanwę i definiują aktualnie używany sterownik ekranu. Struktura **GX_DRAW_CONTEXT** również zawiera pędzel używany do rysowania. Pędzel kontekstu rysowania jest członkiem, który będzie bezpośrednio działać w niestandardowych funkcjach rysowania. Struktura pędzla jest zdefiniowana, jak pokazano w poniższym kodzie.

```C
typedef struct GX_BRUSH_STRUCT
{
    GX_PIXELMAP *gx_brush_pixelmap;
    GX_FONT     *gx_brush_font;
    ULONG        gx_brush_line_pattern;
    ULONG        gx_brush_pattern_mask;
    GX_COLOR     gx_brush_fill_color;  
    GX_COLOR     gx_brush_line_color;  
    UINT         gx_brush_style;
    GX_VALUE     gx_brush_width;
    UCHAR        gx_brush_alpha;  
} GX_BRUSH;
```

Pole **gx_brush_pixelmap** definiuje Pixelmap do użycia na potrzeby wypełniania prostokąta i wielokąta. Ten element członkowski nie jest używany, chyba że **gx_brush_style** zawiera styl **GX_BRUSH_PIXELMAP** .

Element członkowski **gx_brush_font** definiuje czcionkę używaną do rysowania tekstu.
Element członkowski **gx_brush_line_pattern** definiuje wzorzec używany dla linii kreskowanych.
Element członkowski **gx_brush_style** jest zestawem flag stylu, które mogą być lub ze sobą, aby w pełni zdefiniować atrybuty pędzla. Dostępne są następujące flagi stylu pędzla.

**GX_BRUSH_OUTLINE**  
**GX_BRUSH_SOLID_FILL**  
**GX_BRUSH_PIXELMAP_FILL**  
**GX_BRUSH_ALIAS**  
**GX_BRUSH_UNDERLINE**  
**GX_BRUSH_ROUND**

Element członkowski **gx_brush_width** definiuje wiersz z opcją for line Rysowanie lub szerokość konturu dla obramowanego kształtu.

Element członkowski **gx_brush_line_color** definiuje kolor pierwszego planu rysowania linii i rysowania tekstu.

Element członkowski **gx_brush_fill_color** definiuje kolor wypełnienia pełnego używany do wypełniania kształtu. Składnik kontekstu GUIX zawiera zestaw interfejsów API, które ułatwiają modyfikowanie bieżącego pędzla w aktywnym kontekście. Te interfejsy API obejmują **gx_context_brush_define**, **gx_context_line_color_set**, **gx_context_fill_color_set**, **gx_context_font_set** i wiele innych.

Kontekst rysowania obiektu nadrzędnego jest dziedziczony przez obiekty podrzędne. W rzeczywistości klon nadrzędnego kontekstu rysowania jest dziedziczony przez obiekty podrzędne po wywołaniu ich funkcji rysowania. Element podrzędny może zmodyfikować kontekst bez wpływu na rysowanie nadrzędne, ale może również odziedziczyć informacje z elementu nadrzędnego, takiego jak kolor i styl pędzla.

## <a name="guix-window-component"></a>Składnik okna GUIX 

Składnik okna jest odpowiedzialny za wszystkie przetwarzanie okien w GUIX. Okno GUIX jest zasadniczo odrębnym obszarem wyświetlania, który może zawierać co najmniej jeden element widget podrzędny. W programie GUIX okno jest w rzeczywistości tylko specjalną formą podstawowego obiektu widget.

Okna GUIX są implementowane w sposób zorientowany obiektowo z pełnym wsparciem dziedziczenia. Jest to realizowane przy użyciu ANSI C, co skutkuje najmniejszą możliwą ilością pamięci i wymaganiem do przetwarzania.

GUIX systemu Windows rozszerzając funkcję widżetu GUIX głównie przez dodanie obsługi przewijania poziomego i pionowego. Obiekty okna GUIX mogą automatycznie tworzyć i wyświetlać paski przewijania i odpowiadać na dane wejściowe paska przewijania. Ruchome okna zostały również wbudowane w obsługę zdarzeń, aby umożliwić przenoszenie lub przeciąganie przedziału na podstawie zdarzeń wejściowych pióra.
Na koniec okno GUIX reaguje na otrzymywanie fokusu wprowadzania przez przeniesienie okna do przodu okna z kolejnością.

Okno GUIX zachowuje koncepcję *obszaru klienta*, która jest wewnętrzną częścią okna, gdy obramowanie okna i obiekty nieklienckie, takie jak paski przewijania, są usuwane z dostępnego obszaru. Widżety podrzędne obszaru klienckiego są przycinane do obszaru klienckiego systemu Windows, podczas gdy elementy podrzędne, takie jak paski przewijania, są dozwolone do rysowania poza obszarem klienckim, ale są nadal przycinane do wymiarów okna zewnętrznego.

Okna są przechowywane w sposób nadrzędny-podrzędny, gdzie elementy podrzędne dziedziczą cechy z ich elementu nadrzędnego. Okna podrzędne mogą mieć własne okna podrzędne i ponownie dziedziczyć różne cechy z elementu nadrzędnego. Cechy dowolnego okna można jawnie zdefiniować ponownie za pośrednictwem różnych wywołań interfejsu API GUIX.

### <a name="window-creation"></a>Tworzenie okna 

Obiekt window może być tworzony podczas inicjowania lub w dowolnym czasie podczas wykonywania wątków aplikacji. Nie ma żadnego limitu liczby obiektów okien, które mogą zostać utworzone przez aplikację. Nie ma również żadnego limitu liczby elementów podrzędnych, które mogą mieć dowolne okno.

### <a name="window-control-block"></a>Blok sterowania oknem 

Charakterystyka każdego obiektu okna znajduje się w bloku sterowania **GX_WINDOW** i są zdefiniowane w **_gx_api. h_**. Pamięć wymagana dla obiektu okna jest udostępniana przez aplikację i może znajdować się w dowolnym miejscu w pamięci. Jest to jednak najczęstsze, aby formant obiektu okna blokował strukturę globalną przez definiowanie jej poza zakresem dowolnej funkcji.

### <a name="root-window"></a>Okno główne 

GUIX wymaga, aby nazwa była oknem głównym dla każdej kanwy. Okno główne ma bez obramowania i ma takie same wymiary jak Kanwa, do której jest dołączona. Jest używany głównie jako kontener dla wszystkich elementów widget pierwszego poziomu i systemu Windows. Okno główne jest zazwyczaj tworzone przez aplikację za pośrednictwem funkcji API ***gx_window_root_create***, wkrótce po utworzeniu ekranu i kanwy. Jeśli używasz funkcji wygenerowanej przez Studio gx_studio_display_configure, adres okna głównego może być zwracany w lokalizacji przekazana jako ostatni parametr do tej funkcji.

Okno główne jest domyślnie nieruchome, a w najprostszym przypadku okno główne jest rozmiarem kanwy. Okno główne w efekcie rysuje tło wyświetlania, więc aby zmienić kolor tła wyświetlania lub wyświetlić tapetę tła, należy przypisać kolor lub tapetę do okna głównego.

Jeśli okno główne jest ruchome, przesuwa się nie przez zmianę jego pozycji na kanwie jako okna podrzędnego, ale przez przeniesienie kanwy.
Ta funkcja umożliwia korzystanie z sprzętu obsługującego wiele buforów ramek z rejestrami przesunięcia sprzętu w oknie głównym GUIX.

### <a name="background"></a>Tło 

Tła okien są pełnymi kolorami lub obrazami mapy bitowej. Na poziomie systemu istnieje domyślne tło okna, które zapewnia domyślny zestaw systemu Windows. Oczywiście każde tło okna można zmienić za pośrednictwem interfejsu API GUIX.

Aby zmienić tło pełnego koloru okna, użyj interfejsu API ***gx_widget_fill_color_set*** . Aby przypisać tapetę w tle do okna, użyj interfejsu API ***gx_window_wallpaper_set*** .

### <a name="scrolling"></a>Przewijanie 

GUIX obsługuje przewijanie okna standardowego, gdy obszar wymagany do wyświetlenia elementów podrzędnych okna przekracza bieżący rozmiar okna — w poziomie i/lub w pionie. Aby włączyć przewijanie, aplikacja musi utworzyć żądane paski przewijania i dołączyć je do okna.

Składnik okna GUIX zapewnia domyślną implementację przewijania na podstawie rozmiaru obszaru klienta okna i zakresu elementów widget wszystkich elementów podrzędnych. Aplikacje mogą również udostępniać własne implementacje i interpretację przewijania, zastępując funkcję ***gx_window_scroll_info_get*** dla określonego okna.

### <a name="event-notification"></a>Powiadomienie o zdarzeniu 

Domyślna funkcja przetwarzania zdarzeń systemu Windows różni się od przetwarzania zdarzeń GX_WIDGET przede wszystkim w obsłudze zdarzeń przewijania i zmiany rozmiarów. GX_WINDOW zapewnić obsługę defalt dla zdarzeń przewijania i zmiany rozmiarów.

Aplikacja może również dodać własne zdarzenia niestandardowe, rozpoczynając od wartości numerycznej po stałej **GX_FIRST_APP_EVENT**. Wszystkie numery zdarzeń po tej stałej są zarezerwowane do użytku aplikacji. Oczywiście program obsługi zdarzeń w oknie aplikacji musi mieć przetwarzanie dla zdarzeń aplikacji.

### <a name="event-processing"></a>Przetwarzanie zdarzeń 

Podobnie jak w przypadku wszystkich innych typów widżetów dla każdego okna istnieje domyślna funkcja przetwarzania zdarzeń systemu Windows o nazwie ***gx_window_event_process***. Zwykle ta funkcja obsługi zdarzeń zostanie przesłonięta przy użyciu własnego programu obsługi zdarzeń w tworzonym systemie Windows. W ten sposób będziesz reagować na zdarzenia i podejmować działania na podstawie zdarzeń wygenerowanych przez kontrolki podrzędne okna.

Ważne jest, aby pamiętać, aby wywoływać funkcję podstawową ***gx_window_event_process*** dla zdarzeń systemu GUIX w przypadku zastąpienia tego programu obsługi zdarzeń, aby zezwolić na działanie domyślnej obsługi zdarzeń poza dowolną akcją dodawaną do programu obsługi zdarzeń. Na przykład jeśli podasz niestandardową procedurę obsługi dla zdarzenia **GX_EVENT_SHOW** i nie przekażesz tego zdarzenia do ***gx_window_event_process***, okno nigdy nie staną się widoczne.
Aby zapewnić niestandardową obsługę zdarzeń dla okna, należy użyć funkcji ***gx_widget_event_process_set*** , aby zdefiniować adres programu obsługi zdarzeń. Ta funkcja przesłania domyślną funkcję przetwarzania zdarzeń za pomocą funkcji przetwarzania funkcji zdarzeń określonej w interfejsie API.

> [!IMPORTANT]
> Funkcje przetwarzania zdarzeń aplikacji mogą korzystać z zalet (tj. nieduplikowania przetwarzania) w domyślnym przetwarzaniu przez bezpośrednie wywoływanie domyślnego ***gx_window_event_process*** .

Przetwarzanie zdarzeń jest wywoływane wyłącznie z kontekstu wewnętrznego wątku systemowego GUIX. W ten sposób wymagania dotyczące stosu do przetwarzania obsługi zdarzeń dotyczą tylko wątku GUIX.

## <a name="guix-image-reader-component"></a>Składnik czytnika obrazu GUIX 

Składnik czytnik obrazu udostępnia narzędzia i funkcje interfejsu API do dekompresji nieprzetworzonych skompresowanych obrazów do formatu GUIX Pixelmap. Obsługiwane są dane obrazu sformatowanego JPEG i PNG z dodatkowymi formatami zarezerwowanymi dla przyszłych wersji.

Należy pamiętać, że w przypadku większości aplikacji GUIX składnik czytnika obrazu GUIX nie jest wymagany. Większość aplikacji korzysta z aplikacji GUIX Studio w celu konwertowania zasobów grafiki w formacie JPEG i PNG na zgodne z GUIXami **GX_PIXELMAP** . Składnik czytnika obrazu GUIX jest używany, gdy zasoby grafiki RAW są znane tylko w czasie wykonywania, lub gdy ograniczenia magazynu systemu uniemożliwiają przechowywanie zasobów w formacie **GX_PIXELMAP** . Dane obrazu w formacie JPEG i PNG są zwykle bardziej kompaktowe niż format **GX_PIXELMAP** , jednak znacznie obciąża środowisko uruchomieniowe związane z wykonywaniem dekompresji i konwersją przestrzeni kolorów dla tych typów obrazów.

Jeśli obrazy w formacie RAW lub PNG są przesyłane do funkcji gx_canvas_pixelmap_draw API, GUIX dynamicznie dekompresuje i rysuje dane JPEG lub PNG. Należy zauważyć, że będzie to miało znaczny negatywny wpływ na szybkość rysowania w czasie wykonywania i przekazywanie nieprzetworzonych danych obrazu do funkcji gx_canvas_pixelmap_draw nie jest zalecane, chyba że jest używany sprzętowy obiekt docelowy obsługujący sprzętową kompresję JPEG lub PNG.

> [!IMPORTANT]
> Przekazywanie obrazów RAW w formacie JPEG lub PNG do interfejsu API gx_canvas_pixelmap_draw wiąże się z znaczącym obciążeniem środowiska uruchomieniowego dla większości sprzętu docelowego.

Alternatywnie dane pierwotne JPEG i PNG mogą być konwertowane do formatu GX_PIXELMAP w czasie wykonywania przy użyciu składnika czytnika obrazu.
Pixelmaps utworzone w ten sposób mogą być używane i rysowane podobnie jak Pixelmaps utworzone przez Studio i zawarte w pliku zasobów. Dzięki temu aplikacja może przeprowadzić kompresję obrazu, symulowanie i konwersję przestrzeni kolorów jednorazowo (zazwyczaj podczas uruchamiania programu), zamiast wykonywać te operacje przy każdym rysowaniu obrazu.

Funkcje składnika czytnika obrazu obejmują:

***gx_image_reader_create***  
***gx_image_reader_palette_set***  
***gx_image_reader_start***

## <a name="guix-animation-component"></a>Składnik animacji GUIX 

Składnik animacji GUIX to zestaw funkcji i usług służących do automatyzowania automatyzacji przejścia ekranu i widżetu. Składnik animacji GUIX obsługuje zanikanie, zanikanie i przesuwanie lub przesuwanie animacji typu dla dowolnego typu widżetu.

Animacje typu zanikania mogą być obsługiwane przez zmianę wewnętrznej wartości alfa widgetu zanikania (Jeśli **GX_BRUSH_ALPHA_SUPPORT** jest włączona) lub przez rysowanie dowolnej kolekcji widżetów do oddzielnej kanwy pamięci, gdy program zostanie zmieszany z tłem. W przypadku docelowych sprzętowych, które obsługują wiele sprzętowych warstw graficznych, obsługa płynnych efektów zanikania jest najlepiej realizowana przy użyciu tego podejścia do mieszania kanwy, często z niewielką ilością wymaganej przepustowości procesora. Dla celów sprzętowych, które nie obsługują wielu warstw graficznych, mieszanie przy użyciu wartości alfa pędzla GUIX jest obsługiwane w przypadku uruchamiania o 16 BPP i większej głębi kolorów.

Jeśli animacja powinna używać oddzielnej kanwy rysowania, składnik animacji GUIX zapewnia usługę interfejsu API gx_animation_canvas_define do tego celu. Inne typy animacji nie wymagają oddzielnej kanwy, ale będą używać go, jeśli jest dostępny. Dzięki temu najlepszym możliwym do zastosowania dowolna Obsługa sprzętu dla wielu powierzchni sprzętowych.

Zmienne kontrolujące animację są definiowane przez dwa bloki sterujące. Najpierw blok sterowania **GX_ANIMATION** , który definiuje kontroler animacji. Kontroler animacji to silnik łączący, który wykonuje zdefiniowaną sekwencję animacji. Pojedynczy kontroler animacji może być wielokrotnie używany do uruchamiania wielu różnych sekwencji animacji. Jeśli musisz jednocześnie uruchomić wiele sekwencji animacji, możesz utworzyć wiele kontrolerów animacji **GX_ANIMATION** .

Składnik systemu GUIX może udostępnić blok **GX_ANIMATION** struktur kontroli, który może być żądany przez aplikację, gdy wymagana jest animacja i jest automatycznie zwracana do puli systemu po zakończeniu sekwencji animacji. Spowoduje to zwolnienie aplikacji ze statycznie definiującej strukturę **GX_ANIMATION** dla każdej animacji, która może zostać zaimplementowana. Rozmiar tej puli struktur **GX_ANIMATION** jest zdefiniowany przez stałą **GX_ANIMATION_POOL_SIZE**, która domyślnie jest równa 6, co oznacza, że domyślnie 6 równoczesnych animacji można przydzielyć z puli systemu. Ta stała może być ponownie zdefiniowana w pliku nagłówkowym gx_user. h jest wymagana większa liczba animacji. Jeśli wartość **GX_ANIMATION_POOL_SIZE** jest równa zero, składnik systemu GUIX nie udostępnia puli animacji ani powiązanych usług.

Drugi blok kontrolny lub struktura służąca do definiowania animacji jest strukturą **GX_ANIMATION_INFO** . Ta struktura służy do definiowania jednej konkretnej sekwencji animacji. Tę strukturę informacji można przekazać do kontrolera animacji w celu zainicjowania sekwencji animacji przy użyciu usługi interfejsu API gx_animation_start. Struktura **GX_ANIMATION_INFO** zawiera następujące pola:

```C
typedef struct GX_ANIMATION_INFO_STRUCT
{
    GX_WIDGET *gx_animation_target;
    GX_WIDGET *gx_animation_parent;
    GX_WIDGET *gx_animation_screen_list;
    USHORT gx_animation_style;
    USHORT gx_animation_id;
    USHORT gx_animation_start_delay;
    USHORT gx_animation_frame_interval;
    GX_POINT gx_animation_start_position;
    GX_POINT gx_animation_end_position;
    GX_UBYTE gx_animation_start_alpha;
    GX_UBYTE gx_animation_end_alpha;
    GX_UBYTE gx_animation_steps;
} GX_ANIMATION_INFO;
```

Element członkowski **gx_animation_target** definiuje widżet docelowy, na którym będzie działać kontroler animacji.

Element członkowski **gx_animation_parent** definiuje element widget elementu nadrzędnego (jeśli istnieje), do którego zostanie dołączony widżet docelowy po zakończeniu sekwencji animacji. Gx_animation_parent jest również odbiorcą zdarzenia GX_ANIMATION_COMPLETE, które jest generowane po zakończeniu animacji.

Element członkowski **gx_animation_screen_list** definiuje listę widżetów dla animacji slajdów ekranu opartych na danych wejściowych pióra. Lista widge powinna kończyć się wskaźnikiem GX_NULL, a każdy widżet na liście powinien mieć te same wymiary x, y co gx_animation_parent.

**Gx_animation_style** jest maską bitów definiującą typ animacji, która ma zostać wykonana i skojarzone opcje. Flagi stylu animacji obejmują następujące elementy:

| &nbsp;Flaga stylu &nbsp; animacji | Opis |
| --- | --- |
| GX_ANIMATION_TRANSLATE | Żądaj animacji typu slajdu lub zanikania. |
| GX_ANIMATION_SCREEN_DRAG | Żądaj animacji przeciągnięcia ekranu sterowanego piórem. |

Poniższe flagi mogą być używane w połączeniu z animacją typu **SCREEN_DRAG** .

| &nbsp;Flagi przeciągania &nbsp; ekranu | Opis |
| --- | --- |
| GX_ANIMATION_WRAP | Lista ekranu powinna być zawijana z powrotem do menu Start. |
| GX_ANIMATION_HORIZONTAL | Przeciąganie ekranu dozwolone w poziomie.  |
| GX_ANIMATION_VERTICAL | Przeciąganie ekranu dozwolone w kierunku pionowym. |

Następująca Flaga może być używana w połączeniu z funkcją tłumaczenia animacji.

| Tłumaczenie &nbsp; &nbsp; flag animacji | Opis |
| --- | --- |
| GX_ANIMATION_DETACH | Odłącz obiekt docelowy animacji od elementu nadrzędnego animacji po zakończeniu animacji. Jeśli obiekt docelowy został dynamicznie przydzielony i utworzony przez program GUIX Studio wygenerował automatyczne obsłudze zdarzeń, obiekt docelowy zostanie usunięty po odłączeniu. |
| GX_ANIMATION_TRANSLATE | Typy animacji to animacje zależne od czasomierza. Aplikacja definiuje pozycję początkową i końcową oraz początkową i końcową wartość alfa widżetu docelowego, a Menedżer animacji tworzy czasomierz, który będzie obsługiwał i jako siłę ruchu w celu wykonania animacji.
| GX_ANIMATION_SCREEN_DRAG | Różni się od animacji **translacji** , w których ten typ animacji jest oparty na zdarzeniach wejściowych pióra. Ten typ animacji śledzi wraz z danymi wejściowymi ekranu dotykowego, aby szybko przesunąć widżet docelowy, gdy użytkownik przeciągnie piórem lub piórem na ekranie wprowadzania dotykowego. Aby można było użyć tego typu animacji, aplikacja powinna wywołać interfejs API **_gx_animation_drag_enable_** , aby włączyć tę animację. |

Wartość **gx_animation_id** jest przenoszona z powrotem do elementu nadrzędnego animacji w polu event.gx_event_sender zdarzenia **GX_ANIMATION_COMPLETE** . Ta wartość jest używana przez element nadrzędny animacji, aby określić, które z możliwych animacji podrzędnych są raportowane. Ta wartość może być równa 0, a Animacja z wartością identyfikatora 0 nie spowoduje wygenerowania zdarzenia **ANIMATION_COMPLETE** .

Wartość **gx_animation_start_delay** jest liczbą cykli GUIX wskazującą liczbę cykli czasomierza do opóźnienia po ***wywołaniu metody gx_animation_start _ przed faktycznym wykonaniem animacji. Wartość może być równa 0, aby uruchomić animację natychmiast po wywołaniu _*_gx_animation_start_**.

Pole **gx_animation_frame_interval** definiuje liczbę cykli czasomierza GUIX (wielokrotność podstawowej stawki systemu operacyjnego) na opóźnienie między każdą klatką sekwencji animacji. Wartość minimalna to 1.

**Gx_animation_start_position** definiuje punkt początkowy lewego górnego rogu elementu widget dla animacji.

**Gx_animation_end_position** definiuje pozycję końcową lewego górnego rogu widżetu docelowego dla animacji typu tłumaczenia.

Pole **gx_animation_start_alpha** definiuje wartość alfa początkowej kanwy dla animacji typu translacji.

Pole **gx_animation_end_alpha** definiuje wartość alfa kanwy końcowej dla animacji typu translacji.

Pole **gx_animation_steps** definiuje, ile kroków lub klatek ma być wykonywanych przez kontroler dla animacji tłumaczenia. Większa liczba kroków daje gładszy wygląd i/lub zanikanie, ale również wymaga większej przepustowości systemu.

Aby zaimplementować efekty animacji w aplikacji, musisz najpierw wywołać ***gx_animation_create*** , aby zainicjować kontrolera animacji. Jeśli animacja będzie używać pomocniczej kanwy, zainicjuj tę kanwę, wywołując gx_animation_canvas_define. Następnie należy zainicjować strukturę **GX_ANIMATION_INFO** , aby zdefiniować określony typ animacji, która ma zostać wykonana, oraz inne parametry animacji. Na koniec Wywołaj gx_animation_start, aby wyzwolić sekwencję animacji.

Gdy kontroler animacji ukończy sekwencję animacji, wysyła zdarzenie **GX_ANIMATION_COMPLETE** do widżetu nadrzędnego, co pozwala na ukończenie dowolnego żądanego oczyszczenia kanwy animacji.

## <a name="guix-utility-component"></a>Składnik Narzędzia GUIX 

Składnik narzędzia jest odpowiedzialny za wszystkie typowe funkcje narzędzi w programie GUIX. Są to typowe funkcje, które są przydatne narzędzia i mogą być wywoływane z dowolnego miejsca w aplikacji lub wewnętrznego kodu GUIX. Funkcje składnika narzędzia obejmują następujące elementy.

***gx_utility_canvas_to_bmp***

***gx_utility_circle_point_get***

***gx_utility_alphamap_create***

***gx_utility_gradient_create***

***gx_utility_gradient_delete***

***gx_utlity_ltoa***

***gx_utility_math_acos***

***gx_utility_math_asin***

***gx_utility_math_cos***

***gx_utility_math_sin***

***gx_utility_math_sqrt***

***gx_utility_pixelmap_resize***

***gx_utility_pixelmap_rotate***

***gx_utility_pixelmap_simple_rotate***

***gx_utility_rectangle_center***

***gx_utility_rectangle_center_find***

***gx_utility_rectangle_combine***

***gx_utility_rectangle_compare***

***gx_utility_rectangle_define***

***gx_utility_rectangle_overlap_detect***

***gx_utility_rectangle_point_detect***

***gx_utility_rectangle_resize***

***gx_utility_rectangle_shift***

***gx_utility_string_to_alphamap***
