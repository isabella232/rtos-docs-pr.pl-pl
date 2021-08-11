---
title: Rozdział 3 — omówienie funkcjonalności graficznego interfejsu użytkownika
description: Ten rozdział zawiera funkcjonalny przegląd produktu interfejsu użytkownika GUIX o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 37c1103d6b690350b6fa0794b9c719f31a112ff3babf88f125d3735f8ef935b6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785231"
---
# <a name="chapter-3---functional-overview-of-guix"></a>Rozdział 3 — omówienie funkcjonalności graficznego interfejsu użytkownika

Ten rozdział zawiera funkcjonalny przegląd produktu interfejsu użytkownika GUIX o wysokiej wydajności. 

## <a name="execution-overview"></a>Omówienie wykonywania

GuiX implementuje model programowania oparty na zdarzeniach. Oznacza to, że framework GUIX jest oparty głównie na odebraniu zdarzeń wypchnięć do kolejki zdarzeń GUIX. Przetwarzanie tych zdarzeń odbywa się w kontekście wątku GUIX, który jest wątkiem ThreadX utworzonym podczas inicjowania systemu GUIX.

Aplikacje GUIX definiują interfejs użytkownika, wywołując funkcje interfejsu API GUIX w celu tworzenia widżetów okien i elementów podrzędnych, a także dostosowywać wygląd tych widżetów, wywołując dodatkowe funkcje interfejsu API służące do definiowania kolorów, stylów, czcionek i różnych innych atrybutów każdego typu okna lub widżetu. Jeśli używasz programu GUIX Studio do tworzenia wyglądu ekranów interfejsu użytkownika, większość pracy z wywoływaniem funkcji interfejsu API GUIX w celu utworzenia wyświetlania jest wykonywana przez aplikację GUIX Studio.

Aplikacje GUIX współdziałają z użytkownikiem systemu i z zewnętrzną logiką biznesową przez obsługę zdarzeń pobranych z kolejki zdarzeń GUIX.
Te zdarzenia są zwykle tworzone przez widżety GUIX, ale można je również tworzyć za pomocą zewnętrznych wątków. Po wypchnięciu typowego przycisku GUIX ten przycisk wysyła zdarzenie do okna nadrzędnego przycisku. Program aplikacji będzie działać na tym przycisku przez udostępnienie procedury obsługi zdarzenia wypychania przycisku.

Dodatkowe wątki GUIX są często tworzone dla takich rzeczy jak sterowniki wejściowe. Typowy sterownik wejściowy ekranu dotykowego jest wykonywany jako autonomiczny wątek zewnętrzny niż główny wątek GUIX. Sterownik wprowadzania dotykowego wysyła informacje dotykowe do wątku GUIX, wysyłając zdarzenia do kolejki zdarzeń GUIX.

Ponieważ wiele operacji interfejsu użytkownika, takich jak animacje, wymaga dokładnych informacji o chronometrażu, guix implementuje również prosty i łatwy w użyciu interfejs czasomierza. Ten interfejs czasomierza jest zbudowany na usłudze czasomierza ThreadX i jest konfigurowany automatycznie podczas uruchamiania systemu.

Ogromna większość oprogramowania GUIX jest niezależna od wszelkich zależności sprzętowych. Ta platforma wymaga sterowników wejściowych specyficznych dla sprzętu i sterowników graficznych specyficznych dla sprzętu. Szczegóły dotyczące sposobu implementować te sterowniki specyficzne dla sprzętu są odroczone do rozdziału 5.

## <a name="initialization"></a>Inicjalizacja 

Przed ***wywoływaniem dowolnej*** innej usługi GUIX należy gx_system_initialize wywoływana nazwa usługi. Inicjowanie systemu GUIX można nazwać z procedury tx_application_define ***ThreadX*** (kontekstu inicjowania) lub z wątków aplikacji. Funkcja ***gx_system_initialize*** tworzy kolejkę zdarzeń GUIX, inicjuje funkcję czasomierza GUIX, tworzy główny wątek systemu GUIX i inicjuje różne struktury danych utrzymywane przez guix podczas wykonywania aplikacji.

Po ***gx_system_initialize*** aplikacja jest gotowa do tworzenia ekranów, kanw, okien i widżetów oraz dostosowywania właściwości wszystkich obiektów GUIX. Większość interfejsu API tworzenia obiektów GUIX można nazwać ***z*** tx_application_define lub wątków aplikacji.

## <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji 

Wywołania z aplikacji są w dużym stopniu tx_application_define ***(kontekst*** inicjowania) lub z wątków aplikacji. Zobacz sekcję "Dozwolone z" każdego interfejsu API GUIX opisanego w rozdziale 4, aby określić kontekst, z jakiego interfejsu można go nazwać.

W większości przypadków działania intensywnie korzystające z przetwarzania są odroczone do wewnętrznego wątku GUIX, w tym całego przetwarzania zdarzeń i rysowania widżetów/okien.

Funkcje interfejsu API GUIX mogą być wywoływane z dowolnego wątku w dowolnym momencie.
Jednak zazwyczaj uważa się, że jest to lepsza architektura, aby oddzielić logikę biznesową o kluczowym znaczeniu dla czasu od logiki interfejsu użytkownika. Ponieważ operacje rysowania interfejsu użytkownika czasami mogą zająć dużo czasu w zależności od rozmiaru ekranu i wydajności procesora CPU, zwykle nie chcesz, aby wątki krytyczne dla czasu opóźniły oczekiwanie na zakończenie operacji rysowania.

## <a name="internal-guix-thread"></a>Wewnętrzny wątek GUIX 

Jak wspomniano, GUIX ma wewnętrzny wątek, który wykonuje większość przetwarzania graficznego interfejsu użytkownika. Ten wątek jest tworzony przez oprogramowanie aplikacji przez wywołanie ***gx_system_initialize** _, a następnie __*_ gx_system_start **.

Priorytet wewnętrznego wątku GUIX jest określany przez `#define GX_SYSTEM_THREAD_PRIORITY` . Wartość domyślna to 16 (środkowy priorytet), ale można ją zmodyfikować, określając tę wartość w pliku nagłówka gx_port.h lub gx_user.h, zastępując wartość domyślną.

Wycinek czasu wątku GUIX jest podobnie definiowany przez , który `#define GX_SYSTEM_THREAD_TIMESLICE` domyślnie ma wartość 10 ms.

Stos wątku systemowego jest określany przez , który znajduje się w pliku nagłówka gx_port.h, ale można go również przesłonić, określając tę wartość w pliku nagłówka `#define GX_THREAD_STACK_SIZE` ***gx_user.h.***

Wewnętrzna pętla wykonywania wątków GUIX składa się z trzech akcji.
Najpierw guix pobiera zdarzenia z kolejki zdarzeń GUIX i wysyła te zdarzenia do przetwarzania przez okna i widżety GUIX. Zdarzenia są zwykle wypychane do kolejki zdarzeń GUIX przez okresowe czasomierze, urządzenia wejściowe, takie jak ekran dotykowy lub klawiatura, oraz przez same widżety GUIX podczas przetwarzania danych wejściowych użytkownika. Następnie po przetworzeniu wszystkich zdarzeń graficzny interfejs GUIX określa, czy jest wymagane odświeżenie ekranu, a jeśli tak, wykonuje przetwarzanie niezbędne do zaktualizowania wyświetlanych danych graficznych, głównie przez wywołanie funkcji rysowania tych okien i widżetów, które zostały oznaczone jako zanieczyszczone. Na koniec GUIX wstrzymuje wątek GUIX do momentu, gdy pojawi się nowe zdarzenie wejściowe lub zdarzenia.

## <a name="event-processing"></a>Przetwarzanie zdarzeń 

Zdarzenia wprowadzania dotykowego lub piórem są przetwarzane przez określenie najwyższego okna lub widżetu pod położeniem dotykowego lub pióra w pikselach wejściowych i wywołanie funkcji przetwarzania zdarzeń tego okna/widżetu. Jeśli widżet rozumie zdarzenia wprowadzania piórem, będzie przetwarzać zdarzenie zgodnie z potrzebami tego typu widżetu. Jeśli tak nie jest, górny widżet przekaże zdarzenie wprowadzania piórem lub do elementu nadrzędnego widżetu w celu przetworzenia. To przekazanie zdarzenia w górę łańcucha jest kontynuowane, dopóki zdarzenie nie zostanie obsłużone lub zdarzenie dotrze do głównego okna, w którym to przypadku zdarzenie zostanie odrzucone.

Zdarzenia klawiatury są wysyłane do okna/widżetu z fokusem wejściowym. Stan fokusu wejściowego jest utrzymywany przez składnik guix gx_system guix.

Zdarzenia czasomierza są zawsze wysyłane do okna lub widżetu, który jest właścicielem czasomierza do przetwarzania.

Zdarzenia generowane wewnętrznie, takie jak zdarzenia kliknięcia przycisku lub zdarzenia zmiany wartości suwaka, są zawsze wysyłane do elementu nadrzędnego widżetu generującego zdarzenie. Jeśli element nadrzędny nie przetwarza zdarzenia, jest przekazywany łańcuch podobny do zdarzeń wprowadzania piórem lub dotykową.

## <a name="drawing"></a>Rysowanie 

Po zakończeniu całego przetwarzania zdarzeń wewnętrzny wątek GUIX określa, czy jest potrzebna jakakolwiek aktualizacja wyświetlania, a jeśli tak, wywoływane są odpowiednie funkcje rysowania okien/widżetów. Po zakończeniu rysowania wewnętrzny wątek GUIX po prostu czeka w kolejce zdarzeń na przetwarzanie następnego zdarzenia GUIX.

GUIX implementuje koncepcję zanieczyszczonych *obszarów*, które są obszarami, które należy narysować ponownie, dla każdego widżetu i kanwy. Widżet może rysować tylko te obszary, które zostały wcześniej oznaczone jako zanieczyszczone. Po wywołaniu funkcji rysowania widżetu wszystkie operacje rysowania są wewnętrznie przycinane do wcześniej zdefiniowanego zanieczyszczonego prostokąta.
Próby narysowania poza tym obszarem są ignorowane.

Widżety i okna są oznaczane jako zanieczyszczone przez wywołanie funkcji interfejsu API ***gx_system_dirty_mark***. Ta funkcja oznacza cały widżet lub okno jako wymaga ponownego narysowania. Drugą funkcję, ***gx_system_dirty_partial_add***, można wywołać jako alternatywę oznaczania tylko części okna lub widżetu jako zanieczyszczonej.

Ten model oznaczania widżetów jako zanieczyszczonych, a następnie ponownego narysowania tych widżetów tylko wtedy, gdy wszystkie zdarzenia wejściowe zostały przetworzone, jest określany jako *odroczone rysowanie*. Algorytm odroczonego rysowania GUIX i konserwacja zanieczyszczonej listy zostały zaprojektowane w celu zwiększenia wydajności rysowania. Ponieważ operacje rysowania są zwykle kosztowne, graficzny interfejs użytkownika (GUIX) ciężko pracuje, aby zapobiec niepotrzebnemu rysowaniu.

Rysowanie odbywa się na kanwie *GUIX.* Kanwa to obszar pamięci zarezerwowany do przechowywania danych graficznych. Kanwa może być połączona bezpośrednio z sprzętowym buforem ramowym, w zależności od architektury systemu i ograniczeń pamięci. Zanim będzie można narysować kanwę, należy najpierw otworzyć kanwę do rysowania, wywołując ***funkcję interfejsu*** API gx_canvas_drawing_initiate API. Ten interfejs API przygotowuje kanwę do rysowania i ustanowiono bieżący *kontekst rysowania*. Gdy guix wykonuje odświeżanie kanwy systemu, kanwa jest otwierana do rysowania i kontekst rysowania ustalony przed wywołaniem interfejsów API rysowania na poziomie widżetu. W związku z tym widżety nie muszą inicjować rysowania na kanwie w ramach funkcji rysowania widżetów.

Jeśli jednak aplikacja chce wykonywać natychmiastowe rysowanie na kanwie, poza przepływem standardowego algorytmu odroczonego rysowania GUIX, aplikacja musi bezpośrednio wywołać interfejs ***gx_canvas_drawing_initiate*** przed wywołaniem jakichkolwiek innych funkcji interfejsu API rysowania i musi wywołać interfejs ***gx_canvas_drawing_complete*** po zakończeniu bezpośredniego rysowania.

## <a name="user-input"></a>Dane wejściowe użytkownika 

Interfejs GUIX obsługuje urządzenia z ekranem dotykowym, myszą i klawiaturą ze wstępnie zdefiniowanymi typami zdarzeń. Dodatkowe urządzenia wejściowe mogą być używane przez definiowanie niestandardowych typów zdarzeń lub mapowanie niestandardowego urządzenia wejściowego na wstępnie zdefiniowane typy zdarzeń.

Akcje skojarzone z tymi urządzeniami są tłumaczone na zdarzenia przetwarzane przez wewnętrzny wątek GUIX. Oprogramowanie na poziomie sterownika napisane w celu obsługi ekranu dotykowego musi przygotowywać zdarzenia kolejki zdarzeń GUIX i wysyłać je do zdarzeń kolejki zdarzeń GUIX w celu obsługi operacji pen-down, pen-up i pen-drag. Podobnie sterownik wejściowy klawiatury musi generować zdarzenia dla danych wejściowych naciśnięcia klawisza i wydania klawisza.

## <a name="modal-dialog-execution"></a>Wykonywanie modalnego okna dialogowego 

Modalne wykonywanie okna dialogowego odnosi się do prezentowania użytkownikowi okna, które musi zostać zamknięte w jakiś sposób, aby inne okna GUIX lub widżety mogą odbierać dane wejściowe użytkownika. Modalne okna dialogowe przechwytują wszystkie dane wejściowe użytkownika podczas wyświetlania okna dialogowego, niezależnie od położenia x,y zdarzeń wejściowych myszy lub dotyku.

Modalne okna dialogowe są wyzwalane przez oprogramowanie aplikacji, najpierw tworząc okno w normalny sposób, wywołując gx_window_create , ***a*** następnie wywołując funkcję interfejsu API GUIX ***gx_window_execute.***

Gdy ***gx_window_execute*** wywoływana jest funkcja GUIX, wchodzi w lokalną pętlę przetwarzania zdarzeń. Funkcja ***gx_window_execute*** nie wraca do wywołującego, dopóki okno dialogowe nie zostanie zamknięte przez dane wejściowe użytkownika lub przez wywołanie ***metody gx_window_close***. Z tego powodu bardzo ważne jest, aby nigdy nie wywołać ***funkcji gx_window_execute*** z dowolnego wątku innego niż wątek wewnętrzny GUIX.

## <a name="periodic-processing"></a>Okresowe przetwarzanie 

Aby zapewnić efekty wyświetlania, animację sprite i obsługę okresowych żądań aplikacji, guix używa jednego czasomierza ThreadX. Ten pojedynczy czasomierz służy do kierowania wszystkimi potrzebami związanymi z czasem GUIX. Domyślnie częstotliwość wewnętrznego przetwarzania czasomierza GUIX jest ustawiona na 20ms za pośrednictwem stałej **GX_SYSTEM_TIMER_MS**, która jest zdefiniowana w **_pliku gx_api.h,_** chyba że stała jest wcześniej zdefiniowana w nagłówku gx_port.h lub gx_user.h. Częstotliwość domyślna może zostać zmieniona przez aplikację za pośrednictwem opcji kompilacji podczas kompilowania biblioteki GUIX lub jawnego ponownego definiowania jej w ***gx_user.h.***

> [!IMPORTANT]
> Należy pamiętać, że częstotliwość czasomierza GUIX jest wyrażona w taktach czasomierza RTOS i jest definiowana przez stałą **GX_SYSTEM_TIMER_TICKS**. Wartość właściwości **GX_SYSTEM_TIMER_TICKS** jest obliczana przy **użyciu** GX_SYSTEM_TIMER_MS i **TX_TIMER_TICKS_PER_SECOND**. Użytkownik może ponownie zdefiniować dowolną z tych wartości w ***gx_port.h** _ lub _ *_gx_user.h_**, aby dostosować częstotliwość i rozdzielczość czasomierza GUIX.

## <a name="display-driver"></a>Sterownik wyświetlania 

Sterowniki wyświetlania są odpowiedzialne za dostarczenie zestawu funkcji rysowania do podstawowego kodu GUIX. Implementacja każdej z tych funkcji rysowania jest określana przez sterownik i w miarę możliwości implementacja będzie korzystać z obsługi przyspieszania sprzętowego. Ogólnie rzecz biorąc, funkcja rysowania działa przez zapisywanie danych pikseli w buforze pamięci, który może być buforem ramek fizycznych lub może być buforem pomocniczym w zależności od architektury sterownika. Wiele sterowników implementuje podwójne buforowanie przy użyciu dwóch buforów ramek, a te bufory są przełączane przez wywołania funkcji przełączania buforu. GuiX wywołuje te funkcje wewnętrznie w odpowiednim czasie. W przypadku systemów ograniczonych pamięci funkcje rysowania mogą zapisywać tylko w jednym buforze ramek pamięci.

Graficzny interfejs użytkownika udostępnia domyślne implementacje oprogramowania każdej funkcji rysowania niskiego poziomu na każdej głębokości i formacie kolorów. Te funkcje są wywoływane za pośrednictwem wskaźników funkcji utrzymywanych w **GX_DISPLAY** struktury. Po utworzeniu sterowników specyficznych dla sprzętu zwykle zastępują one niektóre wskaźniki funkcji funkcjami specyficznym dla sprzętu docelowego.

Typowy sprzętowy sterownik wyświetlania jest implementowany przez utworzenie domyślnego sterownika wyświetlania GUIX dla wymaganej głębokości koloru i formatu.
Następnie sterownik sprzętowy zastąpi te funkcje, które należy zoptymalizować lub dostosować do określonej implementacji sprzętu.

Interfejs GUIX obsługuje formaty kolorów pikseli od monochromatycznych 1-bpp do formatu 32-bpp a:r:g:b. GuiX obsługuje również wiele odmian w każdej szerokiej kategorii głębokości kolorów, takich jak r:g:b i b:g:r kolejności bajtów, zapakowane piksele i formaty pikseli wyrównane do wyrazów oraz kanały alfa. Obecnie obsługiwanych jest 25 różnych formatów kolorów, ale ta lista rośnie wraz z dostarczaniem nowych odmian przez dostawców sprzętu.

## <a name="display-memory-architectures"></a>Architektury pamięci wyświetlanej

Różne obiekty docelowe i ekrany sprzętowe wykorzystują różne architektury pamięci wyświetlanej, w zależności od ograniczeń pamięci obiektu docelowego i wymagań dotyczących funkcjonalności aplikacji. Poniżej przedstawiono niektóre typowe architektury pamięci z krótkim opisem każdej z nich.

Model 1) Brak buforu ramek, dane graficzne przechowywane w zewnętrznym gramie:

![Brak buforu ramek, dane graficzne przechowywane w zewnętrznym gramie](./media/guix/user-guide/no-frame-buffer.png)

W powyższym modelu pamięć bufora ramowego nie istnieje w pamięci lokalnej dla procesora CPU. Wszystkie dane graficzne są przechowywane w zewnętrznym gramie, który jest wbudowany w sam ekran. Interfejs zewnętrznego grama może być równoległy lub szeregowy. Ten typ architektury jest bardzo niski koszt. Jednak może ono mieć niepożądany efekt odrywania podczas aktualizowania danych graficznych.

Model 2) Jeden bufor ramek lokalnych:

![Jeden lokalny bufor ramek](./media/guix/user-guide/one-local-frame-buffer.png)

W tym modelu pamięć dla danych graficznych jest przydzielana z pamięci o dostępie losowym, która jest bezpośrednio dostępna dla procesora CPU. Dedykowany sprzęt musi być obecny, aby wielokrotnie przesyłać dane graficzne (wraz z sygnałami chronometrażu) z pamięci lokalnej do ekranu. Ten model różni się od modelu 1 tym, że pamięć grafiki jest blokiem lokalnej pamięci SRAM lub pamięci DRAM dostępnej dla procesora CPU. Może to być ta sama pamięć, w której zmienne stosu i programu są zmienne.

Model 3) Lokalny bufor ramki + zewnętrzny GRAM:

![Lokalny bufor ramki + zewnętrzny gram](./media/guix/user-guide/local-frame-buffer-external-gram.png)

Model 3 jest kombinacją pierwszych dwóch. W tym modelu istnieje wystarczająca ilość pamięci lokalnej do przechowywania jednego buforu ramek. Ponadto urządzenie wyświetlające udostępnia zewnętrzny gram i automatycznie odświeża się przy użyciu danych podanych w gramie. Ta architektura korzysta z ulepszonej wydajności aktualizacji, ponieważ można przenieść zmodyfikowaną część lokalnego bufora ramki do zewnętrznego gragramów w ramach transferu jednego bloku, często przy użyciu dołączanych kanałów DMA. Ten model eliminuje również odrywanie i migotanie, które mogą być obecne w jednym z pierwszych dwóch modeli, ponieważ tylko ukończona zawartość grafiki jest kopiowana do zewnętrznego gragramów.

Model 4) Bufory ramek ping-pong:

![Bufory ramowe ping-pong](./media/guix/user-guide/ping-pong-frame-buffers.png)

W modelu 4 jest wystarczająca ilość pamięci, aby zapewnić dwa bufory ramek lokalnych. W takim przypadku GUIX traktuje jeden bufor ramek jako aktywny bufor ramek, a drugi jako bufor ramek roboczych. Gdy operacja wyświetlania aktualizacji lub rysowania jest w toku, odbywa się w buforze pracy. Po zakończeniu operacji rysowania bufory są przełączane, a bufor roboczy staje się aktywnym buforem, a aktywny bufor staje się buforem pracy. Ten model eliminuje również migotanie ekranu i odrywanie, które można zaobserwować w jednym buforowanych systemach.

Model 5) Bufory ping-pong ze składaniem kanwy:

![Bufory ping-pong ze składaniem kanwy](./media/guix/user-guide/ping-pong-buffers-canvas-composting.png)

W modelu 5 można utworzyć dowolną liczbę kanwy, maksymalnie do limitów dostępnej pamięci. Kanwy można na siebie nałocić lub zmieszać zgodnie z definicją aplikacji w celu utworzenia złożonego obszaru roboczego. Po utworzeniu nowego złożonego buforu po operacji odświeżania ekranu aktywne i robocze bufory złożone są przełączane w operacji identycznej ze standardową architekturą buforu ping-pong. Model 5 dodaje możliwość wykonywania operacji zanikania ekranu i mieszania przez wtopienie kanwy do końcowego złożonego wyniku.

Model 6) Składanie kanwy z zewnętrznym gramem:

![Składanie kanwy z zewnętrznym gramem](./media/guix/user-guide/canvas-compositing-external-gram.png)

Model 6 jest nieznaczną odmianą modelu 5, w którym wymagany jest tylko jeden bufor złożony, a bufor złożony jest następnie przesyłany do zewnętrznego gragramów. Ten model obsługuje również mieszanie pełnoekranowe i nakładki.

## <a name="string-encoding"></a>Kodowanie ciągów 

Domyślnie guix obsługuje kodowanie ciągów w formacie UTF8. Obsługę kodowania ciągów UTF8 można wyłączyć przez zdefiniowanie GX_DISABLE_UTF8_SUPPORT **w** pliku ***gx_user.h.*** Jeśli kodowanie UTF8 jest wyłączone, interfejs GUIX będzie wewnętrznie używać tylko standardowego 8-bitowego kodowania znaków ASCII oraz kodowanie znaków strony kodowej Latin-1. Wyłączenie kodowania ciągów UTF8 powoduje nieco mniejsze zużycie biblioteki GUIX i nieco szybsze wykonywanie w czasie wykonywania obsługi ciągów i funkcji rysowania tekstu.

Kodowanie ciągów UTF8 ma następujące cechy:

  - Ciągi ASCII nie mają więcej miejsca do magazynowania niż standardowe 7-bitowe kodowanie ASCII.

  - Większość funkcji ciągów ANSI-C działa z kodowaniem ciągów UTF8 bez modyfikacji.

Wszystkie aktywne zestawy znaków na świecie, w tym zestawy znaków Kanji, mogą być reprezentowane przy użyciu kodowania ciągów UTF8.

### <a name="static-and-dynamic-strings"></a>Ciągi statyczne i dynamiczne 

Ciągi przypisane do widżetów GUIX, które obsługują wyświetlanie tekstu, mogą być statycznie zdefiniowanymi stałymi ciągami, które zwykle są umieszczane w magazynie stałym w ramach tabeli ciągów GUIX opisanej poniżej, oraz dynamicznie definiowanych ciągów, które są ciągami generowanymi w czasie wykonywania przy użyciu usług takich jak ***sprintf** _ lub _*_gx_utility_ltoa_**.

Przykłady ciągów dynamicznych mogą obejmować wartość wyświetlaną jako liczba w widżecie monitu GUIX lub ciąg "godzina/data", który jest dynamicznie formatowany na podstawie preferencji lokalizacji i formatu użytkownika. Jeśli tworzysz ciągi w czasie wykonywania, które zostaną przypisane do widżetów GUIX, takich jak widżety **GX_PROMPT** lub GX_TEXT_BUTTON, musisz wybrać statyczny przydział magazynu dla tych ciągów wygenerowanych w środowisku uruchomieniowym **(tj.**
globalne tablice znaków) lub zdefiniować i zainstalować funkcję alokatora pamięci dynamicznej i użyć stylu **GX_STYLE_TEXT_COPY,** który nakazuje tym widżetom utworzenie prywatnej kopii przypisanych ciągów tekstowych.

Użycie magazynu tymczasowego, takiego jak automatyczna tablica znaków, do przechowywania dynamicznie generowanego ciągu, a następnie przypisanie tego ciągu do widżetu, który nie ma stylu GX_STYLE_TEXT_COPY programowania, jest **błędem** programistycznym. Jeśli ten styl nie jest włączony, widżet po prostu kopiuje podany wskaźnik ciągu, a dane ciągu muszą być przydzielone statycznie. W przypadku, gdy wskaźnik ciągu widżetu prawdopodobnie wskaże nieprzewidywalne wyniki, dane dotyczące elementów bezużytecznym.

### <a name="passing-gx_string-arguments"></a>Przekazywanie GX_STRING argumentów 

Funkcje interfejsu API GUIX, które akceptują parametr GX_STRING, zawsze sprawdzają, czy długość ciągu wskazywanego przez pole **GX_STRING.gx_string_ptr** odpowiada wartości pola **GX_STRING.gx_string_length.** Jeśli dwa pola nie są spójne, zwracany jest błąd **GX_INVALID_STRING_LENGTH,** a interfejs API o nazwie zwraca wartość bez akceptowania przypisania ciągu.

Ze względów bezpieczeństwa oprogramowanie GUIX nigdy nie używa wewnętrznie standardowych funkcji ciągów języka C, takich jak ***strlen** _ lub _*_strcpy_**. Wiadomo, że te funkcje są podatne na złośliwe ataki, gdy dane ciągu są zbierane dynamicznie, co często zdarza się w połączonych aplikacjach.

Biblioteki GUIX w wersjach wcześniejszych niż wersja 5.6 zdefiniować funkcje interfejsu API, które akceptowały ( `GX_CONST GX_CHAR *text` ) jako parametr. Te funkcje, mimo że są nadal obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami, zostały przestarzałe i zastąpione przez preferowane funkcje interfejsu API, które akceptują ( `GX_CONST GX_STRING *string` ) jako parametr wejściowy.

Domyślnie przestarzały interfejs API obsługi tekstu jest włączony, co pozwala na czyste kompilowanie wszystkich wcześniej napisanych aplikacji za pomocą najnowszych aktualizacji biblioteki GUIX. Aby wyłączyć przestarzały interfejs API obsługi tekstu, GX_DISABLE_DEPRECATED_STRING_API **należy** dodać definicję **_do pliku nagłówka gx_user.h_._*Wszystkie nowe aplikacje powinny definiować _GX_DISABLE_DEPRECATED_STRING_API*** i powinny używać tylko zastępczych funkcji interfejsu API. Wszystkie pliki wyjściowe wygenerowane przez program GUIX Studio dla biblioteki GUIX w wersji 5.6 lub nowszej będą korzystać tylko z zastępczych funkcji interfejsu API.

W poniższej tabeli wymieniono przestarzałe i nowo zdefiniowane zastępcze nazwy funkcji interfejsu API:

| **Nazwa przestarzałej funkcji**              | **Zastąpione przez**                              |
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

Tabela ciągów GUIX i zasoby ciągów są rejestrowane w wystąpieniu wyświetlania GUIX.

Każdy ekran w systemie z wieloma ekranami ma własną tabelę ciągów, a każdy ekran może być uruchamiany we własnym wybranym języku. Inne typy zasobów GUIX (kolory, czcionki i mapy pikseli) są również utrzymywane przez składnik wyświetlania GUIX, ponieważ te typy zasobów są specyficzne dla każdego formatu kolorów wyświetlania i głębokości koloru.

Chociaż można ręcznie utworzyć tabelę ciągów aplikacji, najczęściej tabela ciągów wyświetlanych jest definiowana przez aplikację GUIX Studio jako część pliku zasobów projektu. Dostępne języki są również zdefiniowane w pliku nagłówka zasobu. Tabela ciągów wyświetlanych jest wielo kolumnową tabelą wskaźników do ciągów aplikacji. Każda kolumna tabeli ciągów reprezentuje jeden język obsługiwany przez aplikację.
Jeśli aplikacja obsługuje tylko jeden język, na przykład angielski, tabela ciągów będzie mieć tylko jedną kolumnę. W dowolnym momencie można dodać obsługę dodatkowych języków bez konieczności modyfikowania oprogramowania aplikacji.

Aktywna tabela ciągów jest przypisywana przez wywołanie ***gx_display_string_table_set*** API. Ta funkcja jest wywoływana automatycznie przez kod startowy generowany przez program GUIX Studio, ale może być również wywoływana bezpośrednio przez aplikację w celu zmiany tabeli ciągów aktywnych.

Aktywny język jest przypisywany przez wywołanie funkcji ***interfejsu*** API gx_display_active_language_set API. Ta funkcja określa, która kolumna tabeli ciągów wyświetlanych jest aktywna.

Po wywołaniu tej funkcji  do wszystkich widocznych widżetów GUIX jest wysyłane zdarzenie GX_EVENT_LANGUAGE_CHANGE, co umożliwia ich aktualizację w celu wyświetlenia nowo aktywnych danych ciągu.

Widżety i oprogramowanie aplikacji rozwiązują statycznie zdefiniowane ciągi przy użyciu wartości identyfikatora ciągu i ***gx_display_string_get_ext*** lub ***gx_widget_string_get_ext*** api. Te funkcje zwracają **GX_STRING** skojarzone z danym identyfikatorem ciągu i aktualnie aktywnym językiem.

### <a name="bi-directional-text-display"></a>Dwukierunkowe wyświetlanie tekstu 

Graficzny interfejs użytkownika (GUIX) zapewnia dwie strategie obsługi dwukierunkowego tekstu.

Jedną z opcji jest zmiana kolejności tekstu oferty w aplikacji GUIX Studio. Przy użyciu tej opcji GUIX Studio jest odpowiedzialny za generowanie tekstu bidi do pliku wyjściowego w jego kolejności wyświetlania. To rozwiązanie nie ma żadnego wpływu na wydajność środowiska uruchomieniowego i nie wymaga żadnych dodatków do biblioteki środowiska uruchomieniowego GUIX. Aby umożliwić programowi GUIX Studio generowanie ciągów tekstowych displayorder bidi, zaznacz pole wyboru Generuj tekst **Bidi** w kolejności wyświetlania w oknie dialogowym konfiguracji języka GUIX Studio:

![Konfigurowanie języków](./media/guix/user-guide/configure-languages.png)

Po wybraniu tych opcji wygenerowany plik zasobów będzie zawierać ciągi Bidi wygenerowane w kolejności wyświetlania i dodatkowe przetwarzanie nie jest wymagane w bibliotece środowiska uruchomieniowego GUIX.

Drugą opcją jest zmiana kolejności tekstu oferty w czasie wykonywania. Ta opcja jest obsługiwana w przypadku aplikacji, które muszą obsługiwać ciąg tekstowy bidi, które są dynamicznie zdefiniowane i nie są generowane przez aplikację GUIX Studio. W takim przypadku biblioteka środowiska uruchomieniowego GUIX jest odpowiedzialna za zmianę kolejności tekstu oferty przed rysowaniem każdego ciągu tekstowego. To rozwiązanie ma wpływ na wydajność środowiska uruchomieniowego i pamięć. Dla procesu zmiany kolejności tekstu oferty musi być dostępna wystarczająca ilość pamięci dynamicznej. To rozwiązanie wymaga, aby GX_DYNAMIC_BIDI_TEXT_SUPPORT warunkowe podczas tworzenia biblioteki GUIX. Dwie funkcje ***interfejsu API gx_system_bidi_text_enable*** i ***gx_system_bidi_text_disable*** do włączania/wyłączania obsługi tekstu ofert w czasie wykonywania.

Nie należy używać obu tych **GX_DYNAMIC_BIDI_TEXT_SUPPORT** i skonfigurować guix studio do generowania tekstu Bidi w kolejności wyświetlania. Należy wybrać jedną lub drugą strategię do obsługi ciągów tekstowych.

## <a name="memory-usage"></a>Użycie pamięci 

GuiX znajduje się wraz z programem aplikacji. W związku z tym użycie pamięci statycznej (lub pamięci stałej) graficznego interfejsu użytkownika jest określane przez narzędzia programowe; na przykład kompilator, linker i lokalizator. Użycie pamięci dynamicznej (lub pamięci w czasie uruchamiania) podlega bezpośredniej kontroli nad aplikacją.

### <a name="static-memory-usage"></a>Użycie pamięci statycznej 

Większość narzędzi deweloperskimi dzieli obraz programu aplikacji na pięć podstawowych obszarów: *instrukcji* *,* stałej, zainicjowanych danych, *niezainicjowanych* danych i stosu *wątków GUIX.*  Na poniższej ilustracji przedstawiono jeden z możliwych układów tych obszarów pamięci:

![Układ pamięci](./media/guix/user-guide/memory-area-example.png)

Ważne jest, aby zrozumieć, że jest to tylko przykład. Rzeczywisty układ pamięci statycznej jest specyficzny dla procesora, narzędzi programisttycznych, bazowego sprzętu i samej aplikacji.

Obszar instrukcji zawiera wszystkie instrukcje procesora programu. Ten obszar często znajduje się w pamięci ROM.

Stały obszar zawiera różne skompilowane stałe, które w graficznym interfejsie UŻYTKOWNIKA zawierają ustawienia domyślne i wszystkie zasoby aplikacji (obrazy, ciągi, czcionki i kolory). Ponadto ten obszar zawiera "początkową kopię" zainicjowanych obszarów danych. Podczas procesu inicjowania kompilatora ta część stałego obszaru jest używana do skonfigurowania globalnie zainicjowanych danych w pamięci RAM. Stały obszar jest zwykle największy i zazwyczaj następuje po obszarze instrukcji i często znajduje się w pamięci ROM.

Mapy pikseli GUIX i czcionki zwykle wymagają dużej ilości stałego magazynu danych. Te duże statyczne obszary danych są zwykle przechowywane w pamięci ROM lub FLASH.

Stos wątków GUIX jest zdefiniowany w niezainicjowany obszar danych (jako zmienna globalna) ***w pliku gx_system.h*** w następujący sposób:

```C
_gx_system_thread_stack[GX_THREAD_STACK_SIZE];
```

**GX_THREAD_STACK_SIZE** jest zdefiniowany w pliku **_gx_port.h,_** ale może zostać zastąpiony przez aplikację przez zdefiniowanie tego symbolu w pliku nagłówka ***gx_user.h*** lub za pośrednictwem opcji projektu lub parametrów wiersza polecenia. Rozmiar stosu musi być wystarczająco duży, aby obsłużyć obsługę zdarzeń najgorszego przypadku i zagnieżdżone wywołania rysowania.

### <a name="dynamic-memory-usage"></a>pamięć dynamiczna użycia 

Jak wspomniano wcześniej, dynamiczne użycie pamięci jest pod bezpośrednią kontrolą aplikacji. Bloki sterujące i pamięć skojarzoną z kanwami itp. można umieścić w dowolnym miejscu w przestrzeni pamięci obiektu docelowego. Jest to ważna funkcja, ponieważ ułatwia wykorzystanie różnych typów pamięci fizycznej — w czasie uruchamiania.

Załóżmy na przykład, że docelowe środowisko sprzętowe ma zarówno szybką, jak i powolną pamięć. Jeśli aplikacja wymaga dodatkowej wydajności na potrzeby rysowania, pamięć kanwy można jawnie umieścić w obszarze pamięci o dużej szybkości, aby uzyskać najlepszą wydajność.

Kilka opcjonalnych usług i funkcji GUIX wymaga mechanizmu alokacji pamięci dynamicznej środowiska uruchomieniowego, powszechnie nazywanego stertą. Te usługi i funkcje są całkowicie opcjonalne, a wiele aplikacji GUIX nie używa żadnego stosu i nie definiuje mechanizmu alokacji pamięci środowiska uruchomieniowego.

Jeśli będziesz używać usług, które wymagają alokacji pamięci środowiska uruchomieniowego, musisz zainstalować funkcje, które interfejs GUIX wywoła, gdy pamięć musi być przydzielana dynamicznie lub wolna. Możesz zaimplementować te funkcje w preferowany sposób, tak aby nawet w tym przypadku lokalizacja puli pamięci dynamicznej była pod kontrolą aplikacji. Aby zainstalować obsługę dynamicznej alokacji pamięci, aplikacja powinna wywołać usługę interfejsu API gx_system_memory_allocator_set ***podczas*** uruchamiania programu w celu zdefiniowania alokacji pamięci i usług bez pamięci. Pełny przykład można znaleźć w dokumentacji tego interfejsu API.

Usługi GUIX, które wymagają alokacji pamięci środowiska uruchomieniowego i usługi cokołu alokacji, obejmują:

  - Ładowanie zasobów binarnych z magazynu zewnętrznego do środowiska uruchomieniowego GUIX.

  - Dekoder obrazów JPEG środowiska uruchomieniowego oprogramowania.

  - Dekoder obrazu png środowiska uruchomieniowego oprogramowania.

  - Używanie widżetów tekstowych z GX_STYLE_TEXT_COPY.

  - Funkcje narzędzia do zmiany rozmiaru i rotacji mapy środowiska uruchomieniowego.
  - Alokacja bloku kontrolki ekranu środowiska uruchomieniowego i widżetu.

W przypadku mniejszych aplikacji zasoby GUIX są zwykle kompilowane i łączone statycznie jako część obrazu aplikacji, a instalacja zasobów binarnych nie jest wymagana. Zasoby binarne umożliwiają aplikacji instalowanie zasobów (czcionek, obrazów, języków) w czasie wykonywania załadowanych z niektórych lokalizacji magazynu, takich jak dysk flash lub adres URL.

Dekodery plików JPEG i PNG środowiska uruchomieniowego są składnikami opcjonalnymi. Większość aplikacji GUIX umożliwia narzędziu GUIX Studio wstępne dekodowanie wszystkich wymaganych plików obrazów i przechowywanie ich jako zastrzeżonych zasobów danych GUIX Pixemap. Te usługi są zapewniane w celu wykonania tych aplikacji, które wymagają konwersji w czasie wykonywania obrazów JPEG i/lub PNG do formatu pixelmap.

**GX_STYLE_TEXT_COPY** użytkownik może określić, że określony widżet lub widżet będzie przechowywać własną prywatną kopię dynamicznie przypisywanego tekstu. Użycie tej opcji wymaga zainstalowania mechanizmu alokacji pamięci przed użyciem. Jeśli ta flaga stylu nie zostanie podano podczas tworzenia widżetu typu tekstu, aplikacja musi przydzielić statyczne obszary magazynowania dla wszystkich dynamicznie utworzonych i przypisanych ciągów tekstowych. **<span class="underline"></span>** Zmiennych automatycznych nie należy używać w tym przypadku do przechowywania danych ciągu wygenerowanych w czasie wykonywania. Jeśli styl **GX_STYLE_TEXT_COPY** jest włączony, automatyczne zmienne mogą służyć do przechowywania danych ciągu przypisanych do widżetów GUIX, ponieważ każdy widżet utworzy własną kopię przypisanego tekstu.

Funkcje narzędzia do zmiany rozmiaru i obrotu mapy pikseli zwracają wynikową przetłumaczoną mapę pikseli jako nową mapę pikseli dostępną dla aplikacji.
Jeśli te usługi są używane, musi być dostępna wystarczająca ilość pamięci dynamicznej do przechowywania tych bloków danych mapy pikseli wygenerowanych w środowisku uruchomieniowym.

Na koniec bloki sterujące ekranów GUIX i widżetów można przydzielać statycznie lub dynamicznie. W przypadku mniejszych aplikacji często tworzy się wszystkie ekrany aplikacji podczas uruchamiania programu i używa statycznie przydzielonych bloków sterujących. W przypadku dużych aplikacji często tworzy się ekran i podrzędne kontrolki widżetu dynamicznie na podstawie zgodnie z potrzebami. Dynamicznie przydzielane bloki sterujące są  określane przez zaznaczenie pola wyboru **Przydziel** środowisko uruchomieniowe w widoku właściwości programu GUIX Studio lub przez przekazanie flagi stylu GX_STYLE_DYNAMICALLY_ALLOCATED podczas tworzenia widżetu za pośrednictwem standardowego interfejsu API. Korzystanie z dynamicznie przydzielanych bloków sterowania widżetu wymaga, aby usługi alokacji pamięci i co deallokacji zostały zdefiniowane zgodnie z powyższym opisem.

## <a name="guix-components"></a>Składniki GUIX 

Interfejsy API GUIX są podzielone i zorganizowane w kilka podstawowych grup, które odpowiadają podstawowym składnikom systemu GUIX. Podstawowe składniki to:

| Składniki  | Opis  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GX_SYSTEM  | Składnik systemu GUIX odpowiedzialny za inicjowanie, zdarzenia, czasomierze, tabele ciągów i widoczne zarządzanie hierarchią widżetów.                                                                                                                                                                                                                                                                      |
| GX_CANVAS  | Obszar rysowania. Kanwa może być zuchybną abstrakcją sprzętowego bufora ramowego lub może być również kanwą czystej pamięci. Typ kanwy jest określany przez parametry przekazane do gx_canvas_create API.                                                                                                                                                                                   |
| GX_CONTEXT | Składnik kontekstu rysowania. Kontekst rysowania zawiera informacje o ekranie, kanwie i pędzlu oraz obszarze przycinania dla bieżących operacji rysowania.                                                                                                                                                                                                                                      |
| GX_DISPLAY | Udostępnia interfejsy API i implementacje na poziomie sterownika, aby umożliwić aplikacji i widżetom GUIX wykonywanie rysowania na kanwie. GX_DISPLAY jest implementowana w celu poprawnego renderowania grafiki na każdej kanwie przy użyciu wymaganego formatu kolorów tej kanwy. Składnik GX_DISPLAY zarządza również zasobami (kolorami, czcionkami i mapami pikseli) dostępnymi dla widżetów rysowanych na kanwach połączonych z każdym ekranem. |
| GX_WIDGET  | Podstawowy widoczny obiekt widżetu i skojarzone interfejsy API. Wszystkie typy widżetów GUIX są oparte na podstawowym typie elementów widget lub GX_WIDGET typu.                                                                                                                                                                                                                                                                      |
| GX_UTILITY | W tej grupie znajdują się funkcje narzędzi do pracy z prostokątami, funkcje do konwersji ciągów i funkcje matematyczne inne niż ANSI.                                                                                                                                                                                                                                                         |

Oprócz tych podstawowych składników interfejs GUIX zawiera interfejsy API unikatowe dla każdego typu widżetu dostępnego w bibliotece. Te interfejsy API są opisane w rozdziale 4 tego Podręcznika użytkownika, "Opis usług GUIX".

## <a name="guix-system-component"></a>GuiX System, składnik

Składnik systemu GUIX udostępnia kilka usług, które są globalne dla aplikacji interfejsu użytkownika. Usługi te obejmują *inicjowanie, zarządzanie zdarzeniami, zarządzanie wyświetlaniem, zarządzanie zasobami, zarządzanie czasomierzem* i *zarządzanie widżetami.* Każda usługa jest istotna dla organizacji programu aplikacji, a te usługi zostały bardziej szczegółowo opisane w poniższych sekcjach.

### <a name="initialization"></a>Inicjalizacja 

Inicjowanie guix jest realizowane przez aplikację wywołującą usługę ***gx_system_initialize***, która może być wywoływana przez aplikację z procedury tx_application_define ***ThreadX*** (kontekst inicjowania) lub z wątków aplikacji. Funkcja ***gx_system_initialize*** inicjuje wszystkie globalne struktury danych GUIX i tworzy mutex systemu GUIX, kolejkę zdarzeń, czasomierz i wątek. Gdy ***gx_system_initialize*** zwraca, aplikacja może używać graficznego interfejsu użytkownika.

### <a name="thread-processing"></a>Przetwarzanie wątków 

Wewnętrzny wątek GUIX — utworzony podczas inicjowania — jest odpowiedzialny za większość przetwarzania w graficznym interfejsie użytkownika. Przetwarzanie w tym wątku najpierw kończy wszelkie dodatkowe inicjowanie wymagane przez podstawowy sterownik wyświetlania. Po zakończeniu tego procesu wątek GUIX przechodzi w pętlę, która najpierw przetwarza wszystkie zdarzenia obecne w kolejce zdarzeń GUIX, a następnie odświeża ekran w razie potrzeby. Odświeżanie ekranu wykonuje niezbędne funkcje rysowania GUIX w oparciu o to, co jest widoczne i zostało oznaczone jako zanieczyszczone, co oznacza, że należy je ponownie wykreślić. Jeśli na ekranie nie ma żadnych zdarzeń i nic nie pozostało do odświeżenia, wątek GUIX zostanie wstrzymany, czekając na kolejne zdarzenie GUIX.

### <a name="rtos-binding"></a>Powiązanie RTOS 

Składnik systemu GUIX jest domyślnie skonfigurowany do korzystania z systemu operacyjnego ThreadX w czasie rzeczywistym dla usług, takich jak usługi wątków, usługi kolejki zdarzeń i usługi czasomierza. Interfejs GUIX można łatwo przetworzyć do innych systemów operacyjnych przy użyciu dyrektywy preprocesora GX_DISABLE_THREADX_BINDING i ponownie utworzyć bibliotekę GUIX. Spowoduje to usunięcie zależności ThreadX z kodu źródłowego GUIX i umożliwi deweloperowi aplikacji zaimplementowanie wymaganych usług systemu operacyjnego przy użyciu dowolnego systemu RTOS dostarczonego przez system docelowy. [Dodatek F — GUIX RTOS Binding Services](appendix-f.md) opisuje usługi, które należy zaimplementować do portu GUIX do systemu operacyjnego innego niż system operacyjny ThreadX.

### <a name="multithread-safety"></a>Bezpieczeństwo wielowątkowych 

Interfejs API GUIX jest dostępny w kontekście wątku GUIX, a także w innych wątkach aplikacji. Wątki aplikacji mogą wchodzić w interakcje z wątkiem GUIX przez wysyłanie i odbieranie zdarzeń, przez dostęp do udostępnionych zmiennych i za pomocą funkcji interfejsu API GUIX. GuiX używa wewnętrznego obiektu mutex ThreadX do ochrony zasobów wielowątkowych. Ponadto guix zapobiega modyfikacji wewnętrznej struktury widocznych widżetów po zakończeniu operacji odświeżania ekranu. Interfejsy API, które modyfikują drzewo widocznych obiektów, są blokowane podczas operacji rysowania i zwalniane po zakończeniu odświeżania ekranu.

### <a name="system-timers"></a>Czasomierze systemowe 

GuiX udostępnia aplikacji okresowe czasomierze, które są często używane do okresowej aktualizacji danych wyświetlanych w oknach GUIX. Jest to realizowane za pomocą czasomierza okresowego ThreadX, który jest również używany do wykonywania efektów na poziomie systemu GUIX, takich jak zanikanie/wygasanie ekranu itp.

Aplikacja może tworzyć czasomierze i korzystać z tej samej funkcji czasomierza, która jest używana wewnętrznie przez guix. Oczywiście aplikacja może również bezpośrednio tworzyć czasomierze ThreadX i używać ich w razie potrzeby. Zaletą czasomierzy GUIX jest to, że są bardzo łatwe w użyciu i są wstępnie skonfigurowane do pracy w systemie przetwarzania sterowanego zdarzeniami GUIX.

Aby utworzyć i uruchomić czasomierz GUIX, aplikacja powinna wywołać funkcję gx_system_timer_start ***.*** Parametry tej funkcji obejmują wskaźnik do wywołującego widżetu, identyfikator czasomierza (umożliwiający uruchamianie wielu czasomierzy przez jeden widżet) oraz początkowe i ponownie mierzące limity czasu. Jeśli wartość limitu czasu ponownego harmonogramu wynosi 0, czasomierz zostanie uruchomiony tylko raz i usunie się z listy aktywnych czasomierzy po jego wygaśnięciu.

Po zakończeniu czasomierz GUIX będzie wysyłać zdarzenia GX_EVENT_TIMEOUT do właściciela czasomierza, raz lub okresowo w zależności od wartości ponownego harmonogramu czasomierza. Czasomierz GUIX można zatrzymać, wywołując funkcję interfejsu API ***gx_system_timer_stop***.

### <a name="pen-speed-configuration"></a>Konfiguracja szybkości pióra 

Składnik systemu GUIX przechowuje informacje o konfiguracji związane ze śledzeniem szybkości pióra. Graficzny interfejs GUIX generowany wewnętrznie **GX_EVENT_VERTICAL_FLICK** zdarzeń GX_EVENT_HORIZONTAL_FLICK **na** podstawie szybkości i odległości zdarzeń PEN_DOWN generowanych przez sterownik wprowadzania dotykowego, jeśli takie są. Aplikacja może skonfigurować minimalną odległość i szybkość wymaganą do wyzwolenia tych zdarzeń generowanych wewnętrznie przy użyciu **_gx_system_pen_configure_** API.

### <a name="screen-stack"></a>Stos ekranu 

Składnik systemu GUIX udostępnia usługi związane ze stosem ekranu GUIX, który jest opcjonalną funkcjonalnością obsługową wirtualnego stosu widżetu, na który aplikacja może wypychać, wypychać i pobierać ekrany w czasie wykonywania. Stos ekranu jest przydatny do zarządzania złożonymi systemami menu, w którym trasa, za pomocą której użytkownik może docierać do różnych stanów w systemie menu, jest zróżnicowana. Powrót do poprzedniego stanu w systemie menu można łatwo wykonać, najpierw wypychając poprzedni stan ekranu, a następnie wyświetlając nowy ekran i umożliwiając nowemu ekranowi wyskakowanie poprzedniego stanu ze stosu ekranu po odjęniu bieżącego ekranu.

### <a name="clipboard-maintenance"></a>Konserwacja schowka 

Interfejs GUIX obsługuje schowek do kopiowania i wklejania tekstu podczas wykonywania w czasie wykonywania. Ta obsługa jest zapewniana przez składnik systemu GUIX.

### <a name="dirty-list-maintenance"></a>Konserwacja zanieczyszczonej listy 

GuiX utrzymuje listę zanieczyszczonych widżetów, co oznacza, że widżety są widoczne i muszą zostać ponownie wycofane ze względu na zmiany stanu lub nowo widoczne. Ta zanieczyszczona lista poprawia wydajność rysowania, umożliwiając graficznego interfejsu użytkownika wykonanie jednej operacji odświeżania kanwy w celu odzwierciedlenia wszystkich bieżących zmian stanu interfejsu użytkownika, zamiast wykonywania odświeżania kanwy w przypadku każdej zmiany interfejsu użytkownika.
Ta zanieczyszczona lista jest również utrzymywana przez składnik systemu GUIX.

### <a name="animation-control-block-pool"></a>Pula bloków kontrolek animacji 

Aplikacje często chcą wykonywać wiele sekwencji animacji, często równolegle. GuiX utrzymuje pulę bloków sterowania animacji, z których aplikacja może przydzielać i używać. Dzięki temu aplikacja nie może statycznie definiować tych bloków sterujących i umożliwia ich ponowne używanie w różnych momentach, zamiast definiować unikatowy blok sterowania animacji dla każdej animacji, która może zostać zdefiniowana przez aplikację. Pula bloków sterowania animacją jest również utrzymywana przez składnik systemu GUIX.

### <a name="system-error-handling"></a>Obsługa błędów systemu 

Program obsługi błędów systemu GUIX ma pomóc aplikacji w znalezieniu wewnętrznych błędów systemowych w graficznym interfejsie użytkownika, które mogą być trudniejsze do określenia z perspektywy interfejsu API. Za każdym razem, gdy w graficznym interfejsie użytkownika wystąpi błąd ***systemu, wywoływana jest _gx_system_error_process*** funkcja wewnętrzna. Ta funkcja zapisuje podany kod błędu i zwiększa łączną liczbę wykrytych błędów systemowych. Zmienne błędów systemu są zdefiniowane w następujący sposób:

UINT **_gx_system_last_error**;

ULONG **_gx_system_error_count**;

Jeśli aplikacja GUIX zachowuje się dziwnie, warto przyjrzeć się zmiennej liczby błędów w debugerze. Jeśli jest on ustawiony, dobrym sposobem rozwiązania problemu jest ustawienie punktu przerwania w funkcji ***_gx_system_error_process*** i zobaczenie, kiedy/gdzie jest wywoływany.

## <a name="guix-canvas-component"></a>Składnik kanwy GUIX

Składnik kanwy jest odpowiedzialny za wszystkie przetwarzanie związane z kanwą. Kanwa jest wirtualnym buforem ramek. Aby utworzyć graficzne dane wyjściowe, aplikacja musi utworzyć co najmniej jedną kanwę.
Zazwyczaj należy utworzyć co najmniej jedną kanwę dla każdego fizycznego ekranu obsługiwanego przez system.

Wszystkie rysowanie GUIX odbywa się na kanwie. W prostszych lub ograniczonych systemach pamięci będzie prawdopodobnie tylko jedna kanwa, która może być bezpośrednio połączona z widocznym buforem ramowym, natomiast systemy z większą pamięcią i bardziej zaawansowanymi wymaganiami graficznymi mogą wymagać wielu kanw. Udostępnianie wielu kanwy dla jednego ekranu umożliwia korzystanie z funkcji, takich jak zanikanie ekranu i okna oraz efekty zanikania.
Kanwy mogą być jednym z dwóch głównych typów, prostym lub zarządzanym.

Prosta kanwa to obszar rysowania poza ekranem używany przez aplikację.
GuiX nie robi nic bezpośrednio z prostą kanwą, ale aplikacja może użyć prostej kanwy do renderowania złożonego rysowania w buforze poza ekranem, a następnie użyć tego buforu poza ekranem, aby odświeżyć widoczną kanwę w razie potrzeby.

Zarządzana kanwa jest automatycznie wyświetlana w buforze ramek sprzętowych przez guix. Zarządzana kanwa jest zawarta w budowania kanwy złożonej dla tych systemów z wystarczającą pamięcią do obsługi wielu zarządzanych kanw. Zarządzane kanwy mają porządek Z utrzymywany przez graficzny interfejs użytkownika, a przycinanie widoku jest wymuszane na wszystkich zarządzanych kanwach.

Kanwa różni się od buforu ramowego tym, że jest bardziej ogólna. W systemach ograniczonych pamięci może być tylko jedna kanwa, a pamięć dla tej kanwy może być widoczną pamięcią bufora ramowego. Jednak w przypadku bardziej złożonych systemów, które obsługują bardziej zaawansowane graficzne nakładki i wiele kanwy, do zarządzanych kanw przydziela się własne obszary pamięci, które różnią się od pamięci bufora ramek sprzętowych.
Te zarządzane kanwy są renderowane w widocznym buforze ramek podczas operacji odświeżania buforu ramki lub przełączania.

W przypadku sprzętu, który obsługuje wiele warstw graficznych, tj. wiele nakładek buforów ramowych, aplikacja może powiązać co najmniej jedną kanwę ze sprzętową warstwą grafiki przy użyciu interfejsu ***API*** gx_canvas_hardware_layer_bind API. Ta usługa informuje kanwę o tym, że jest połączona z określoną sprzętową warstwą grafiki, a po jej nawiązać połączenia podejmie próbę wykorzystania obsługi sprzętu w celu widoczności kanwy (tj. gx_canvas_show, gx_canvas_hide), mieszania alfa kanwy (np. ***gx_canvas_alpha_set***) i przesunięcia kanwy na ekranie (***gx_canvas_offset_set***).

W przypadku architektur innych niż najprostsza organizacja buforu pojedynczej kanwy/pojedynczej ramki rozmiar kanwy jest określany przez aplikację i może być inny niż stały rozmiar bufora ramowego.
Może również być przy przesuniętej wybranej przez aplikację. Inne informacje, takie jak kolejność Z, są zachowywane na kanwie. Po zakończeniu rysowania kanwy zawartość kanwy jest przesyłana do ekranu fizycznego przez sterownik wyświetlania. W niektórych systemach, które nie mają wystarczającej ilości pamięci dla oddzielnych obszarów pamięci bufora kanwy i ramek, aktualizacja kanwy jest w rzeczywistości bezpośrednio na ekranie fizycznym za pośrednictwem sterownika wyświetlania.

### <a name="canvas-creation"></a>Tworzenie kanwy 

Obiekt kanwy można utworzyć podczas inicjowania lub w dowolnym momencie podczas wykonywania wątków aplikacji. Nie ma żadnego limitu liczby obiektów kanwy, które mogą zostać utworzone przez aplikację. Jednak większość aplikacji utworzy tylko jeden obiekt kanwy dla całego rysunku GUIX.

### <a name="canvas-control-block"></a>Blok kontrolki kanwy 

Charakterystyka każdego obiektu kanwy znajduje się w bloku sterowania GX_CANVAS **i** jest zdefiniowana w **_gx_api.h_**. Pamięć wymagana dla obiektu kanwy jest dostarczana przez aplikację i może być zlokalizowana w dowolnym miejscu w pamięci. Jednak najczęściej blok sterowania obiektami kanwy i obszar rysowania są strukturą globalną przez definiowanie ich poza zakresem dowolnej funkcji.

### <a name="canvas-alpha-channel"></a>Canvas Alpha Channel

GuiX obsługuje alfa-mieszanie kolorów pierwszego planu i tła na wielu poziomach, w tym kanał alfa mapy bitowej, który określa współczynnik mieszania na piksel, brush alpha, który określa współczynnik mieszania pędzla o głębokości 16 bpp i wyższych głębokościach kolorów, oraz kanwę alfa, która określa współczynnik mieszania dla kanwy nakładki.

Wartość alfa kanwy jest używana, gdy istnieje wiele kanwy, które są ze sobą złożone w celu wyświetlenia w buforze ramek. Jeśli kolejność kanwy Z jest taka, że kanwa znajduje się nad innymi kanwami, można ustawić wartość alfa kanwy, aby wtopić kanwę z tymi, które się za nią znajdują. Szybkie modyfikowanie wartości alfa kanwy jest używane w celu zapewnienia "zanikania" efektów przejścia ekranu, ale kanwy alfa może być używana na wiele sposobów.

Jeśli kanwa jest powiązana ze sprzętową warstwą grafiki przy użyciu funkcji gx_canvas_hardware_layer_bind(), guix podejmie próbę zaimplementowania mieszania alfa kanwy przy użyciu obsługi sprzętu, minimalizując obciążenie związane z mieszaniem kanwy nakładki.

Wartości alfa mogą mieć zakres od 0 do 255, gdzie wartość 0 oznacza, że piksel jest w pełni przezroczysty, a wartości większe niż 0 zwiększające mniej przezroczystą wartość alfa kanwy mogą być obsługiwane tylko w przypadku sterowników ekranu działających w 16-bpp i wyższych, chyba że zapewniana jest pomoc sprzętowa dla mieszania kanwy.

### <a name="canvas-offset"></a>Przesunięcie kanwy 

Kanwę można przesunięć w widocznym buforze ramek przez wywołania ***gx_canvas_offset_set*** API. Przesunięcia kanwy są zwykle używane do implementowania animacji sprite'u. Jeśli kanwa jest powiązana ze sprzętową warstwą grafiki przez wywołania funkcji interfejsu API usługi ***gx_canvas_hardware_layer_bind,*** guix podejmie próbę zaimplementowania zmian przesunięcia kanwy przy użyciu obsługi sprzętu, minimalizując obciążenie związane z przesuwaniem pozycji kanwy.

### <a name="canvas-drawing"></a>Rysowanie kanwy 

Składnik kanwy GUIX zapewnia aplikacji pełny interfejs API rysowania. Przed wywołaniem interfejsów API rysowania, takich jak ***gx_canvas_line_draw*** lub ***gx_canvas_pixelmap_draw,*** należy otworzyć kanwę docelową do rysowania, wywołując funkcję interfejsu ***API*** gx_canvas_drawing_initiate API. Ta funkcja przygotowuje kanwę do rysowania i tworzy kontekst ***rysowania***.

Interfejsy API rysowania renderowane na kanwie, takie jak ***gx_canvas_line_draw** _ lub _*_gx_canvas_text_draw,_*_ używają parametrów znalezionych w bieżącym pędzlu kontekstowym do definiowania stylu, szerokości i kolorów linii. Te parametry pędzla są modyfikowane przez wywołanie funkcji _*_gx_context_brush_define_*_, _* _gx_context_brush_set_**, ***gx_context_brush_style_set**_ i podobnych funkcji interfejsu API po nakreśleniu kontekstu rysowania przez wywołanie funkcji __*_ gx_canvas_drawing_initiate **.

Gdy guix wywołuje funkcje rysowania okien i widżetów w ramach operacji odroczonego odświeżania kanwy, kanwa docelowa jest otwierana do rysowania przed wywołaniem funkcji rysowania widżetów. W związku z tym standardowe funkcje rysowania widżetów nie są wymagane do otwierania kanwy docelowej. Zostało to zrobione dla nich.

W niektórych przypadkach aplikacja może chcieć wymusić natychmiastowe rysowanie na kanwie. W takim przypadku aplikacja może wykonać następujące kroki.

1. Wywołaj ***funkcję gx_canvas_drawing_initiate*** API, przekazując docelową kanwę i prostokąt w obrębie tej kanwy, na której aplikacja chce narysować. 

2. Wywołaj dowolną liczbę interfejsów API rysowania kanwy, aby osiągnąć żądany rysunek.

3. Wywołaj ***funkcję gx_canvas_drawing_complete*** API, aby zasygnalizować, że rysowanie zostało zakończone. Powoduje to opróżnienie kanwy do widocznego bufora ramek i/lub wyzwolenie operacji przełączania buforu w zależności od architektury pamięci systemowej.

### <a name="drawing-apis"></a>Rysowanie interfejsów API 

Istnieje kilka podstawowych elementów podstawowych rysowania, które są wymagane przez graficzny interfejs użytkownika do rysowania wszystkich elementów wizualnych na ekranie. Te interfejsy API rysowania mogą być również wywoływane przez oprogramowanie aplikacji, zazwyczaj jako część niestandardowej funkcji rysowania widżetów. Te interfejsy API rysowania kanwy GUIX wykonują walidację i przycinanie parametrów, a następnie przekażą obcięty współrzędny rysowania do sterownika wyświetlania dla implementacji rysowania specyficznych dla sprzętu i formatu kolorów. Te funkcje interfejsu API rysowania są zdefiniowane w następujący sposób.

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

Interfejs API rysowania jest wywoływany za pośrednictwem interfejsu API kanwy GUIX, a całe rysowanie odbywa się przy użyciu gx_canvas_* interfejsu API. Rysowanie odbywa się przy użyciu bieżącego pędzla w bieżącym kontekście rysowania. Każdą z powyższych funkcji rysowania kształtów można zakreślić, wypełnić kolorem pełnym lub wypełnić mapę pikseli zgodnie z definicją bieżącego pędzla. Aby zmodyfikować szerokość, kolor lub wypełnienie konturu kształtu, użyj funkcji interfejsu API gx_context_brush_*, aby zdefiniować pędzl w bieżącym kontekście rysowania.

Powyższe interfejsy API rysowania na poziomie aplikacji nie robią rzeczywistego rysowania na kanwie, ale zamiast tego sprawdzają parametry wywołującego przed wywołaniem funkcji rysowania na poziomie sterownika wyświetlania. Funkcja rysowania na poziomie sterownika w rzeczywistości zapisuje dane pikseli w pamięci kanwy.

GuiX zapewnia podstawowe lub ogólne funkcje rysowania sterowników wyświetlania dla różnych głębokości kolorów, w tym 1, 2, 4, 8, 16, 24 i 32 bitów na piksel (bpp). W niektórych przypadkach domyślna implementacja rysowania oprogramowania jest zastępowana przez implementacje przyspieszone sprzętowo dla tych obiektów docelowych sprzętu, które zapewniają akcelerator rysowania 2D.

### <a name="color-depth"></a>Głębokość koloru 

GuiX obsługuje głębokość kolorów do 32 bpp, a także monochromatyczny i skali szarości. Typ obsługi głębokości kolorów w dużej mierze zależy od możliwości bazowego ekranu fizycznego, a także ma wpływ na ilość pamięci wymaganej dla obszaru rysowania kanwy. Poniżej znajduje się lista obsługi głębokości kolorów wraz z krótkim opisem odmian w obrębie tej głębokości kolorów.

| Format &nbsp; koloru       | Opis                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Monochromatyczna 1-bitowa   | 1-bitowy format na piksel w pakiecie.                                                                                                   |
| 2-bitowa skala szarości    | 4 poziomy szarości, spakowane cztery piksele na bajt.                                                                                      |
| 4-bitowa skala szarości    | 16 poziomów szarości, spakowane dwa piksele na bajt.                                                                                      |
| Kolor 4-bitowy        | Organizacja pamięci planowej w formacie VGA.                                                                                         |
| 8-bitowa skala szarości    | 256 szarych poziomów                                                                                                                  |
| 8-bitowy tryb palety | 1 bajt na piksel używany jako indeks palety                                                                                           |
| 8-bitowy tryb r:g:b   | Rzadziej używany format 2:3:2 r:g:b.                                                                                         |
| 16-bitowy             | Każdy piksel wymaga dwóch bajtów. Może być r:g:b lub b:g:r kolejności bajtów. Zwykle struktura 5:6:5, ale może być również strukturą 5:5:5 lub strukturą 4:4:4:4 a:r:g:b. |
| 24-bitowy             | Każdy piksel wymaga 3 bajtów (w formacie zapakowanym) lub 4 (w formacie rozpakowanych). Może być w kolejności bajtów r:g:b lub b:g:r zgodnie z wymaganiami sprzętu. |
| 32-bitowa             | Każdy piksel wymaga 4 bajtów z kanałem alfa. Może to być a:r:g:b lub b:g:r:a kolejność bajtów i określana przez sprzęt.              |

### <a name="mouse-support"></a>Obsługa myszy 

Interfejs GUIX obsługuje rysowanie kursora myszy na dowolnej żądanej kanwie. Kursor myszy może być rysowany w oprogramowaniu lub może być obsługiwany przez nakładkę sprzętową kursora. W obu przypadkach interfejs API dostarczony do aplikacji związany z obsługą kursora myszy jest taki sam niezależnie od tego, czy jest on rysowany za pomocą programowego, czy sprzętowego kursora myszy.

Obsługa myszy GUIX jest włączona tylko wtedy, gdy jest zdefiniowana w `#define GX_MOUSE_SUPPORT` pliku nagłówka gx_user.h przed sbudowania biblioteki GUIX.

Aplikacja musi zdefiniować kursor myszy i obszar hotspot przy użyciu ***gx_canvas_mouse_define*** API. Ten interfejs API akceptuje wskaźnik do kanwy, na której powinien być rysowany obraz **kursora, oraz** wskaźnik do struktury GX_MOUSE_CURSOR_INFO, która definiuje obraz kursora myszy i obszar hotspot obrazu myszy względem obrazu w lewym górnym rogu.

## <a name="guix-display-component"></a>Składnik wyświetlania GUIX 

Składnik wyświetlania ma podstawowe znaczenie w graficznym interfejsie użytkownika, ponieważ zarządza przetwarzaniem wszystkich obiektów wyświetlanych, które same w sobie zawierają co najmniej jedną kanwę, widżety i okna. Składnik wyświetlania współdziała również ze źródłowym sterownikiem ekranu sprzętu skojarzonym z każdym ekranem za pośrednictwem serii wskaźników funkcji.

### <a name="display-creation"></a>Tworzenie ekranu 

Obiekt wyświetlany można utworzyć podczas inicjowania lub w dowolnym momencie podczas wykonywania wątków aplikacji. Zazwyczaj aplikacja tworzy jeden obiekt wyświetlania do zarządzania każdym ekranem fizycznym. Jeśli do zdefiniowania aplikacji i dostępnych fizycznych ekranów używasz programu GUIX Studio, do utworzenia i zainicjowania każdego z ekranów użyjemy funkcji interfejsu GX_STUDIO_DISPLAY_CONFIGURE API.

### <a name="display-control-block"></a>Wyświetlanie bloku kontrolki 

Właściwości każdego obiektu wyświetlanego znajdują się w bloku sterowania ***GX_DISPLAY** _ i są zdefiniowane w _*_gx_api.h_**. Pamięć wymagana dla obiektu wyświetlanego jest dostarczana przez aplikację i może być zlokalizowana w dowolnym miejscu w pamięci. Jednak najczęściej kontrolka wyświetlania blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji.

### <a name="resource-management"></a>Zarządzanie zasobami 

Zasoby to składniki interfejsu użytkownika, które są wymagane przez aplikację, ale nie są kodem aplikacji. Zasoby są danymi aplikacji i zwykle są definiowane statycznie. Typy zasobów obejmują mapy pikseli, czcionki, kolory i ciągi. Te zasoby można zmienić w dowolnym momencie, zazwyczaj bez zmiany oprogramowania aplikacji. Ważne jest, aby przechowywać odwołania do zasobów i oddzielone od oprogramowania aplikacji, aby umożliwić zmianę wyglądu interfejsu użytkownika bez zmiany kodu aplikacji, ponieważ zmiany w oprogramowaniu aplikacji zwykle wymagają skojarzonego ponownego testowania i weryfikacji tego oprogramowania.

Moduł ***wyświetlania*** GUIX udostępnia funkcje zarządzania zasobami dla wszystkich zasobów, które są zależne od głębokości koloru i formatu ekranu. Te obiekty obejmują utrzymywanie tabeli aktywnej mapy pikseli, aktywnej tabeli czcionek i tabeli aktywnych kolorów. Zasób tabeli ciągów jest utrzymywany przez moduł systemowy GUIX, ponieważ zasobów ciągów zwykle nie trzeba zmieniać na podstawie głębokości kolorów i formatu.

Oprogramowanie aplikacji odwołuje się do zasobów według identyfikatora zasobu, który jest indeksem odpowiedniej tabeli zasobów. Dzięki temu można zmienić tabelę, na przykład można zmienić tabelę kolorów, gdy produkt zmieni się z "trybu dnia" na "tryb nocy", ale wartości identyfikatorów kolorów pozostaną takie same.

Zasoby aplikacji są zapisywane w pliku zasobów (lub zestawie plików zasobów) przez aplikację GUIX Studio. Kolory domyślne, mapy pikseli i czcionki są udostępniane automatycznie podczas tworzenia nowego projektu GUIX Studio, ale te wartości domyślne są łatwo zastępowane podczas definiowania wyglądu i działania aplikacji.

Należy pamiętać, że identyfikatory zasobów kolorów, czcionek i map pikseli nie mogą być rozpoznawane jako rzeczywiste wartości koloru, czcionki lub mapy pikseli, dopóki aktywny składnik Wyświetlania nie będzie znany. Ponieważ architektura GUIX obsługuje wiele aktywnych ekranów, identyfikatory zasobów można rozpoznać tylko na wartości zasobów, gdy widżet i skojarzony z nim identyfikator zasobu mogą zostać rozpoznane jako określony ekran. Ta właściwość jest znana jako powiązanie dynamiczne. Identyfikator zasobu dla właściwości, takiej jak kolor tekstu, na przykład identyfikator zasobu **GX_COLOR_ID_TEXT, może** zostać rozpoznany jako 16-bitowa wartość R:G:B dla koloru białego, gdy jest używana na jednym ekranie, ale ten sam identyfikator koloru może zostać rozpoznany jako monochromatyczna wartość koloru czarnego w przypadku użycia na innym ekranie.

W praktyce to dynamiczne powiązanie identyfikatorów zasobów z wartościami zasobów oznacza, że oprogramowanie aplikacji i składniki wewnętrzne GUIX powinny najczęściej rozwiązują tylko identyfikatory zasobów jako wartości zasobów w aktywnym kontekście rysowania. Aktywny kontekst rysowania określa aktualnie aktywny ekran, co umożliwia graficznemu interfejsowi użytkownika (GUIX) określenie określonej wartości zasobu dla każdego identyfikatora zasobu. Jeśli oprogramowanie aplikacji musi znaleźć określoną wartość zasobu poza kontekstem rysowania, można to również zrobić dla widocznych widżetów. Widoczne widżety są połączone z oknem głównym, które może być również używane do rozpoznawania aktywnej kanwy i wyświetlania dla tego widżetu.

Jeśli widżet został utworzony, ale nie został jeszcze wyświetlony (tj. nie został połączony z żadnym oknem głównym lub innym widocznym elementem nadrzędnym), nie można rozpoznać żadnych identyfikatorów zasobów skojarzonych z tym widżetem do określonej wartości zasobu innej niż poprzez bezpośrednie indeksowanie do tabeli zasobów przypisanej do określonego wyświetlania. Ten bezpośredni dostęp do określonej tabeli zasobów może być bezpiecznie zapewniany przez oprogramowanie aplikacji, ale nigdy nie odbywa się w wewnętrznym oprogramowaniu biblioteki GUIX.

### <a name="widget-defaults"></a>Wartości domyślne widżetu 

Składnik wyświetlania GUIX udostępnia również definicje domyślne dla różnych atrybutów widżetu. Jeśli nie określono inaczej przez aplikację, widżety/okna są tworzone przy użyciu tych atrybutów systemowych. Te atrybuty systemowe składają się głównie z czcionek, kolorów i map bitowych utrzymywanych w tabelach zasobów systemowych. Dodatkowe atrybuty domyślnego wyglądu paska przewijania są również utrzymywane przez składnik wyświetlania GUIX.

Domyślne ustawienia kolorów są definiowane przez tabelę kolorów przypisaną do każdego ekranu oraz wstępnie zdefiniowane domyślne identyfikatory kolorów. Te domyślne identyfikatory kolorów są następujące.

| Identyfikator koloru | Opis |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| GX_COLOR_ID_CANVAS | Domyślny kolor kanwy (tj. wyświetlania tła) |
| GX_COLOR_ID_WIDGET_FILL | Domyślny kolor wypełnienia widżetu |
| GX_COLOR_ID_WINDOW_FILL | Domyślny kolor wypełnienia okna |
| GX_COLOR_ID_DISABLED_FILL | Domyślny wyłączony kolor wypełnienia widżetu |
| GX_COLOR_ID_DEFAULT_BORDER | Domyślny kolor obramowania widżetu |
| GX_COLOR_ID_WINDOW_BORDER | Domyślny kolor obramowania okna |
| GX_COLOR_ID_TEXT | Domyślny kolor tekstu |
| GX_COLOR_ID_SELECTED_TEXT | Domyślny wybrany kolor tekstu |
| GX_COLOR_ID_DISABLED_TEXT | Domyślny wyłączony kolor tekstu |
| GX_COLOR_ID_SELECTED_TEXT_FILL | Domyślny kolor wypełnienia zaznaczonego tekstu |
| GX_COLOR_ID_READONLY_TEXT | Domyślny kolor tekstu tylko do odczytu |
| GX_COLOR_ID_READONLY_FILL | Domyślny kolor wypełnienia tekstu tylko do odczytu |
| GX_COLOR_ID_SCROLL_FILL |    Kolor wypełnienia paska przewijania |
| GX_COLOR_ID_SCROLL_BUTTON | Kolor wypełnienia przycisku paska przewijania |
| GX_COLOR_ID_SHADOW | Domyślny kolor cienia |
| GX_COLOR_ID_SHINE | Domyślny kolor wyróżnienia |
| GX_COLOR_ID_BUTTON_BORDER | Kolor obramowania widżetu przycisku |
| GX_COLOR_ID_BUTTON_UPPER | Kolor górnego wypełnienia widżetu przycisku |
| GX_COLOR_ID_BUTTON_LOWER | Dolny kolor wypełnienia widżetu przycisku |
| GX_COLOR_ID_BUTTON_TEXT | Kolor tekstu widżetu przycisku |
| GX_COLOR_ID_TEXT_INPUT_TEXT | Kolor tekstu widżetu wprowadzania tekstu |
| GX_COLOR_ID_TEXT_INPUT_FILL | Kolor wypełnienia wprowadzania tekstu |
| GX_COLOR_ID_SLIDER_TICK | Kolor używany do narysowania znaczników suwaka. |
| GX_COLOR_ID_SLIDER_GROOVE_BOTTOM | Kolor używany do rysowania suwaka |
| GX_COLOR_ID_SLIDER_NEEDLE_OUTLINE | Kolor używany do narysowania konturu szprychy |
| GX_COLOR_ID_SLIDER_NEEDLE_FILL | Kolor używany do wypełniania suwaka |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE1 | Kolor używany do narysowania wyróżnienia na szprychy |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE2 | Kolor używany do narysowania cienia naiwnych |

Te wartości identyfikatorów kolorów są mapowane na określoną wartość koloru zgodnie z definicją w tabeli kolorów przypisanej do poszczególnych ekranów. Te wartości domyślne można zmienić jako grupę dla jednego ekranu, wywołując funkcję ***gx_display_color_table_set*** API. Jeśli używasz programu GUIX Studio, tabela kolorów wyświetlania jest automatycznie inicjowana, gdy aplikacja ***wywołuje gx_studio_display_configure*** funkcji.

Składnik wyświetlania GUIX zachowuje również domyślną tabelę czcionek. Domyślna tabela czcionek definiuje czcionkę używaną przez każdy typ widżetu, chyba że zostanie określona przez aplikację. Wstępnie zdefiniowane identyfikatory tabeli czcionek wyświetlania zawierają następujące wartości.

| Identyfikator &nbsp; czcionki | Opis |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------|
| GX_FONT_ID_DEFAULT | Domyślna czcionka używana, gdy nie zdefiniowano określonej czcionki |
| GX_FONT_ID_BUTTON | Domyślna czcionka używana dla całego tekstu na przyciskach |
| GX_FONT_ID_TEXT_INPUT | Domyślna czcionka używana w polach edycji tekstu |

Identyfikator czcionki używany przez dowolny widżet typu tekstu można ponownie przypisać przy użyciu interfejsu **API** gx_<widget_type>_font_set dla każdego typu widżetu związanego z tekstem. Całą tabelę czcionek można ponownie przypisać, wywołując funkcję **gx_display_font_table_set** API.

### <a name="scrollbar-appearance"></a>Wygląd paska przewijania 

Ekran GUIX zachowuje również domyślne ustawienia wyglądu paska przewijania dla tego ekranu. Te ustawienia są definiowane przez **GX_SCROLLBAR_APPEARANCE** zdefiniowaną poniżej. Ekran GUIX zachowuje jedną strukturę wyglądu paska przewijania dla pionowych pasków przewijania i drugą strukturę poziomych pasków przewijania. Aplikacja może modyfikować domyślny wygląd paska przewijania dla  dowolnego ekranu, inicjując strukturę GX_SCROLLBAR_APPEARANCE i inicjując funkcję interfejsu API ***gx_display_scroll_appearance_set***.

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
| GX_SCROLLBAR_APPEARANCE, składowa struktury | Opis |
| --- | --- |
| gx_scroll_width | Szerokość pionowego paska przewijania lub wysokość poziomego paska przewijania w pikselach. |
| gx_scroll_thumb_width | Szerokość przycisków windy i przycisków końcowych w pikselach. |
| gx_scroll_thumb_travel_max | Przesunięcie od końca paska przewijania do maksymalnego punktu podróży przycisku miniatury. |
| gx_scroll_fill_pixelmap | Mapa pikseli używana do wypełniania tła przewijania. |
| gx_scroll_thumb_pixelmap | Mapa pikseli używana do rysowania przycisku przewijania. |
| gx_scroll_up_pixelmap | Mapa pikseli używana do rysowania przycisku przewijania w górę. |
| gx_scroll_down_pixelmap | Mapa pikseli używana do rysowania przycisku przewijania w dół. |
| gx_scroll_fill_color | Identyfikator koloru używany do wypełniania tła paska przewijania. |
| gx_scroll_button_color | Identyfikator koloru używany do wypełnienia przycisku przewijania na pasku przewijania. |

Oprócz tych domyślnych ustawień czcionek, kolorów i stylów aplikacja może określić dowolny z parametrów dla poszczególnych przypadków zgodnie z potrzebami przy użyciu interfejsu API dostarczonego przez każdy typ widżetu.

### <a name="skinning-and-themes"></a>Osłanianie i motywy

Zmiana koloru umożliwia widżetom i okienom GUIX łatwe zmienianie podstawowego wyglądu, tj. zmiana "koloru" w jednym miejscu spowoduje zmianę podstawowego wyglądu wszystkich skojarzonych widżetów i okien.

Ponowne przesłodzenie aplikacji GUIX wymaga podania nowego koloru, czcionki i tabeli pixelmap w tabelach zasobów guix display. Ponieważ wszystkie widżety GUIX odwołują się do ich koloru, mapy bitowej lub czcionki według identyfikatora zasobu, udostępnienie nowej tabeli zasobów automatycznie powoduje, że wszystkie widżety GUIX zaczynają korzystać z nowych kolorów i map pikseli, gdy narysują się do żądanego wyświetlenia.

Nowy zestaw czcionek, kolorów i map pikseli zaprojektowanych do wspólnej pracy w celu zapewnienia atrakcyjnego wyglądu nosi nazwę *motywu*. Motyw definiuje zestaw tabel zasobów i rozmiar każdej tabeli zasobów. Dowolną liczbę motywów można zdefiniować dla dowolnego ekranu przy użyciu aplikacji GUIX Studio. Należy przekazać początkowy indeks motywu do funkcji wygenerowanej przez program GUIX Studio ***gx_studio_display_configure***, która instaluje motyw początkowy na utworzonym ekranie. Aktywny motyw dla dowolnego ekranu można zmienić w dowolnym momencie, wywołując funkcję ***gx_display_theme_install***.

### <a name="root-window"></a>Okno główne

Dla każdej widocznej kanwy utworzonej przez aplikację aplikacja musi również utworzyć jedno okno główne dla tej kanwy. To specjalne okno zasadniczo działa jako kontener dla wszystkich okien i widżetów aplikacji najwyższego poziomu. Okno główne rysuje tło kanwy, a ponieważ okno główne pochodzi z klasy **GX_WINDOW,** okno główne może również mieć tapetę. Aby zmienić kolor tła ekranu lub kanwy, wystarczy zmienić kolor wypełnienia okna głównego dołączonego do tej kanwy.

Jeśli do skonfigurowania ekranów używasz funkcji wygenerowanej przez program GUIX Studio o nazwie ***gx_studio_display_configure,*** kanwa i okno główne dla każdego ekranu są tworzone jako część tej funkcji inicjowania.

### <a name="anti-aliasing"></a>Anty aliasing 

Anty aliasing to opcjonalna funkcja w graficznym interfejsie użytkownika, która służy do wygładania linii, krzywych i czcionek. Anty aliasy są obsługiwane tylko w przypadku pracy ze sterownikami wyświetlania korzystającymi z głębi kolorów 16-bpp lub wyższej.

Rysowanie linii o aliasach jest włączane przez ustawienie **GX_BRUSH_ALIAS** w aktywnym pędzlu. Dotyczy to linii rysowanych bezpośrednio, a także linii rysowanych jako obramowanie wielokąta lub okręgu.

Rysowanie tekstu o aliasach jest włączane przy użyciu czcionki o anty aliasach, która jest wytwarzanych przez aplikację GUIX Studio. Podczas tworzenia czcionki określasz, czy czcionka ma być generowana jako antyaliased, czy binarna.
Czcionki o aliasach w graficznym interfejsie użytkownika wykorzystują 16 poziomów przezroczystości dla każdego piksela.

### <a name="clipping"></a>Przycinania 

Przycinanie jest obsługiwane wewnętrznie przez składnik wyświetlania GUIX oraz w warstwach okna i widżetu przez architekturę nadrzędny-podrzędny obsługiwaną przez widżety GUIX. Żadne okno ani widżet nie mogą być rysowane poza obszarem tego widżetu, a widżet nigdy nie może być rysowany poza obszarem nadrzędnym tego widżetu.

Zapobiega to również rysowaniu przez widżety współrzędnych pikseli, które są poza pamięcią kanwy, co prawdopodobnie prowadzi do uszkodzenia pamięci lub awarii systemu. Widżety nie mogą rysować poza obszarem widżetu, obszarem nadrzędnym widżetu ani poza zakresem kanwy.

Ponadto widżety mogą rysować tylko te obszary, które wcześniej zostały oznaczone jako zanieczyszczone. Zapobiega to narysowywaniu całego okna, na przykład gdy zostanie ujawniony tylko róg okna. Tylko część okna, która faktycznie musi zostać odświeżona, jest oznaczona jako zanieczyszczona, więc funkcja rysowania okien naprawdę odświeża piksele w zanieczyszczonym obszarze.

Składnik wyświetlania GUIX wymusza te algorytmy przycinania przed wywołaniami funkcji rysowania na poziomie sterownika.

### <a name="views"></a>Widoki 

GuiX zawsze utrzymuje zestaw widoków dla każdego okna głównego i każdego okna podrzędnego okna głównego. Widoki są dynamicznym obszarem przycinania określanym w czasie uruchamiania, który zmienia się wraz ze zmianą położenia okna i kolejności Z.
Interfejs GUIX używa widoków, aby uniemożliwić rysowanie okna lub widżetu w tle na oknie lub widżecie na pierwszym planie. Widoki wymuszają dyscyplinę porządku Z. Ponadto widoki są ważne ze względu na wydajność, ponieważ uniemożliwiają rysowanie okna w tle w dowolnym obszarze kanwy, który nie jest widoczny. Jeśli okno jest całkowicie objęte innym oknem, nie będzie ono w ogóle dozwolone do narysowania na kanwie, nawet jeśli próbuje to zrobić.

### <a name="display-driver-interface"></a>Interfejs sterownika wyświetlania 

Sterowniki wyświetlania GUIX są odpowiedzialne za całą interakcję z bazowym ekranem fizycznym. Sterowniki wyświetlania mają trzy podstawowe funkcje: inicjowanie, rysowanie i wyświetlanie buforu ramki.
Inicjowanie jest odpowiedzialne za przygotowanie fizycznego sprzętu do wyświetlania, poinformowanie graficznego interfejsu UŻYTKOWNIKA o właściwościach fizycznego sprzętu do wyświetlania oraz poinformowanie graficznego interfejsu użytkownika o konkretnych funkcjach rysowania, które powinny być używane. Inicjalizacja głównego sterownika wyświetlania jest wywoływana z interfejsu GUIX ***gx_display_create*** funkcji. Ponadto wątek GUIX wywoła również inicjację pomocniczego sterownika wyświetlania z kontekstu wątku. Ten pomocniczy sterownik wyświetlania jest wymagany tylko wtedy, gdy podczas inicjowania sterownik wymaga ***usług*** RTOS, np. przerwań urządzenia lub żądania tx_thread_sleep opóźnienia między krokami w procesie inicjowania.

Po zakończeniu inicjowania sterownik wyświetlania jest odpowiedzialny za wszelkie bezpośrednie rysowanie, które można wykonać na fizycznym sprzęcie wyświetlania.
Na koniec sterownik wyświetlania jest odpowiedzialny za wyświetlanie buforu ramki.

## <a name="guix-widget-component"></a>Składnik widżetu GUIX

Widżet GUIX jest widocznym elementem graficznym. Istnieją składniki GUIX, które nie są widoczne, takie jak czasomierze i funkcje matematyczne.
Jednak wszystkie widoczne składniki pochodzą z podstawowego składnika widżetu GUIX. Widżet GUIX to podstawowy blok blokowy wyświetlania guix — wszystkie inne elementy graficzne pochodzą z funkcji podstawowego widżetu.

Widżety GUIX są implementowane w sposób zorientowany obiektowo z pełną obsługą dziedziczenia. Jest to realizowane przy użyciu ansi C, co powoduje najmniejsze możliwe wymagania dotyczące pamięci i przetwarzania. Gdy mówimy o jednym konkretnym widżecie,  takim jak **GX_BUTTON,** pochodzącym z innego widżetu, takiego jak podstawowy element **GX_WIDGET,** oznacza **to,** że struktura kontrolki GX_BUTTON zawiera wszystkie zmienne składowe i wskaźniki funkcji elementu **GX_WIDGET** z pewnymi dodatkowymi zmiennymi specyficznymi dla GX_BUTTON **.** Graficzny interfejs użytkownika (GUIX) tworzy warstwy widżetów w ten sposób, dzięki czemu bardziej złożone widżety są zawsze oparte na prostszym widżecie przed nimi. Ten hierarchiczny model wyprowadzenia ułatwia naukę interfejsów API używanych do modyfikowania parametrów widżetu. Jeśli chcesz zmodyfikować kolor przycisku, użyj tego samego interfejsu API, którego używasz do modyfikowania koloru widżetu, a gx_widget_fill_color_set ***.***

Organizacja widocznych widżetów jest utrzymywana w sposób nadrzędny-podrzędny przy użyciu list strukturalnych drzewa łączących widżety podrzędne z ich elementami nadrzędnymi. Dzieci dziedziczą cechy po swoich rodziców, takie jak widoki, w których mogą być rysowane, i kanwa, na której są rysowane.
Widżety podrzędne mogą mieć własne widżety podrzędne, ponownie dziedziczące różne właściwości z elementu nadrzędnego. Właściwości dowolnego widżetu można jawnie ponownie zdefiniować za pośrednictwem różnych wywołań interfejsu API GUIX.

### <a name="widget-creation"></a>Tworzenie widżetu 

Obiekt widżetu można utworzyć podczas inicjowania lub w dowolnym momencie podczas wykonywania wątków aplikacji. Nie ma żadnego limitu liczby obiektów widżetów, które mogą być tworzone przez aplikację. W ramach limitów pamięci sprzętu docelowego nie ma również limitu liczby elementów children, które mogą mieć elementy widget.

Każdy typ widżetu ma własną funkcję tworzenia, taką jak ***gx_button_create** _ lub __*_ gx_prompt_create **. Pierwsze trzy parametry tych funkcji są zawsze takie same: wskaźnik do struktury sterowania widżetem, wskaźnik ciągu do nazwy widżetu i wskaźnik do elementu nadrzędnego widżetu. Każda funkcja tworzenia może mieć dowolną liczbę dodatkowych parametrów w zależności od wymagań danego typu widżetu.

### <a name="widget-control-block"></a>Blok kontrolki widżetu 

Właściwości każdego obiektu widżetu znajdują się w bloku sterowania GX_WIDGET **i** są zdefiniowane w **_gx_api.h_**. Pamięć wymagana dla obiektu widżetu jest dostarczana przez aplikację i może być zlokalizowana w dowolnym miejscu w pamięci. Najczęściej jednak kontrolka obiektu widżetu blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji. Jeśli używasz programu GUIX Studio, bloki sterowania widżetu mogą być przydzielane statycznie w pliku specyfikacji wygenerowanym przez program Studio lub mogą być dynamicznie przydzielane przez aplikację.

### <a name="dynamic-widget-control-block-allocation-and-de-allocation"></a>Alokacja bloku kontrolki widżetu dynamicznego i cokadlenie alokacji 

Jeśli używasz dynamicznej alokacji bloków sterowania, musisz zdefiniować dwie funkcje, których guix użyje do przydzielenia i wolnego pamięci wymaganej dla bloków kontrolek widżetu. Funkcje zarządzania pamięcią są przekazywane do składnika systemu GUIX za ***pośrednictwem gx_system_memory_allocator_set*** API. Ta funkcja umożliwia przekazania dwóch wskaźników funkcji do graficznego interfejsu użytkownika: pierwszy jest wskaźnikiem do funkcji alokacji pamięci, a drugi jest wskaźnikiem do funkcji wolnej od pamięci. Najczęściej te funkcje są implementowane przy użyciu pul bajtów ThreadX, ale projekt GUIX umożliwia implementowanie dynamicznego zarządzania pamięcią w dowolny sposób.

Dynamiczne przydzielanie widżetów jest najczęściej stosowane w pliku specyfikacji aplikacji wygenerowanym w programie Studio po wybraniu opcji "przydzielane dynamicznie" w polu właściwości widżetu programu Studio. Można jednak również używać dynamicznej alokacji bloków sterowania w aplikacji. Jeśli używasz dynamicznej alokacji bloków sterowania w aplikacji, należy wywołać funkcję ***gx_widget_allocate** _ API, aby przydzielić blok sterowania widżetem. Następnie podczas tworzenia widżetu upewnij się, że flaga stylu *_GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** (wraz z innymi wymaganymi flagami stylów) jest do funkcji tworzenia widżetu. Ta flaga służy do oznaczania widżetu jako przydzielanego dynamicznie w polu stanu widżetu. Jeśli widżet zostanie później usunięty przy użyciu narzędzia **_gx_widget_delete,_** guix sprawdzi to pole stanu i automatycznie wywoła funkcję cokołu alokacji pamięci, aby się nie przesłonić pamięci.

> [!IMPORTANT]
> Aby zapobiec utracie pamięci, należy utworzyć widżet utworzony przy użyciu dynamicznie **przydzielonego** bloku GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED style.

### <a name="types"></a>Typy

Graficzny interfejs użytkownika udostępnia bogaty, w pełni funkcjonalny zestaw wbudowanych widżetów. Jak wspomniano wcześniej, wszystkie wyspecjalizowane widżety pochodzą z podstawowego widżetu. Poniżej znajduje się lista wbudowanych widżetów w graficznym interfejsie użytkownika:

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

Style widżetu składają się z elementów, takich jak właściwości obramowania (podniesione, wywłaszczane, zgrubne, grube lub w ogóle bez tablicy), a także właściwości dla określonych typów widżetów, jak podano wcześniej. Flagi stylu widżetu oferują najprostszą metodę modyfikowania wyglądu dowolnego widżetu.
Początkowy styl widżetu jest zawsze parametrem przekazywanym do funkcji create specyficznej dla typu widżetu.

### <a name="colors"></a>Kolory 

Widżety rysują się przy użyciu kolorów zdefiniowanych w tabeli kolorów systemu.
Identyfikatory kolorów są definiowane dla tła kanwy, domyślnego koloru wypełnienia widżetu, koloru wypełnienia przycisku, koloru wypełnienia widżetu tekstu, koloru wypełnienia okna i kilku innych domyślnych wartości kolorów. Ponadto obiekty **GX_WINDOW** obsługują wyświetlanie mapy bitowej lub tapety po wypełnieniu klienta okna.

Najprostszą metodą zmiany domyślnego schematu kolorów jest użycie programu GUIX Studio i utworzenie lub zdefiniowanie schematu kolorów spełniającego wymagania.
Schemat kolorów można również zdefiniować ręcznie, tworząc tablicę wartości GX_COLOR i invoking gx_system_color_table_set API.

### <a name="event-notification"></a>Powiadomienie o zdarzeniu 

Zdarzenia GUIX to żądania wysyłane do co najmniej jednego widżetu w celu wykonania określonej akcji i powiadomień w celu powiadamiania widżetów o zmianach wprowadzonych przez użytkownika i wewnętrznych stanach systemu. Na przykład gdy element widget przejmie fokus, **GX_EVENT_FOCUS_GAINED** zostanie wysłany do widżetu za ***pośrednictwem gx_system_event_send*** API.

Zdarzenia są przekazywane przez kolejkę zdarzeń GUIX, a każde zdarzenie jest wystąpieniem GX_EVENT **danych.** Struktura **GX_EVENT** danych jest zdefiniowana w ***gx_api.h,*** jednak najważniejsze pola struktury to **gx_event_type**, **gx_event_sender**, **gx_event_target** **i gx_event_payload**.

Pole **gx_event_type** służy do identyfikowania określonej klasy zdarzeń. Typ zdarzenia wskazuje, czy jest to  na przykład zdarzenie GX_EVENT_PEN_DOWN **lub** GX_EVENT_TIMER zdarzenia. Ta **gx_event_payload** jest uniią różnych pól danych i nie wszystkie są prawidłowe dla każdego typu zdarzenia.
Należy najpierw użyć pola typu zdarzenia przed zbadaniem innych pól danych zdarzenia.

Pole **gx_event_sender** zawiera identyfikator widżetu, który wygenerował zdarzenie, jeśli zdarzenie jest powiadomieniem podrzędnego widżetu.

Pole **gx_event_target** może służyć do przekierowywu zdarzeń zdefiniowanych przez użytkownika do określonego okna lub widżetu. Jeśli chcesz wysłać zdarzenie do określonego okna, należy podać w oknie unikatową wartość identyfikatora (aby można ją było zidentyfikować pozytywnie), a podczas tworzenia zdarzenia umieść wartość identyfikatora okna w polu **identyfikator** gx_event_target danych. Jeśli nie znasz identyfikatora docelowego lub chcesz tylko, aby zdarzenie zostało skierowane do widżetu z fokusem wejściowym, upewnij się, że pole gx_event_target **wartość** 0.

Na koniec **pole gx_event_payload** jest uniią różnych typów danych. W **GX_EVENT_PEN_DOWN** i **GX_EVENT_PEN_UP,** pole gx_event_pointdata  zawiera współrzędną x,y pikseli położenia pióra. W przypadku zdarzeń **czasomierza gx_event_timer_id** zawiera identyfikator wygasłego czasomierza. Inne pola danych ładunku są używane dla innych typów zdarzeń. Pełna lista wstępnie zdefiniowanych typów zdarzeń i ich pól ładunku jest zdefiniowana w dodatku [E - GUIX opisy zdarzeń](appendix-e.md).

Aplikacja może również dodawać własne zdarzenia niestandardowe, zaczynając numerycznie po stałej **GX_FIRST_APP_EVENT**. Wszystkie numery zdarzeń po tej stałej są zarezerwowane do użytku przez aplikację. Oczywiście procedura obsługi zdarzeń widżetu aplikacji musi mieć przetwarzanie dla takich zdarzeń aplikacji.

### <a name="event-processing"></a>Przetwarzanie zdarzeń 

Istnieje domyślna funkcja przetwarzania zdarzeń widżetu dla każdego widżetu o ***nazwie gx_<typu widżetu>_event_process***. W większości przypadków aplikacja nie musi martwić się o obsługę zdarzeń w żadnym z widżetów. Jednak w sytuacjach, gdy aplikacja wymaga niestandardowego lub uzupełniającego przetwarzania zdarzeń, aplikacja może zastąpić domyślną funkcję przetwarzania własną za pośrednictwem interfejsu ***API*** GUIX gx_widget_event_process_set . Ta funkcja zastępuje domyślną funkcję przetwarzania zdarzeń funkcją przetwarzania funkcji zdarzeń określoną w interfejsie API.

> [!IMPORTANT]
> Funkcje przetwarzania zdarzeń aplikacji mogą korzystać z zalet (tj. nie duplikować przetwarzania) przetwarzania domyślnego przez bezpośrednie wywołanie domyślnego ***gx_widget_event_process*** przetwarzania.

Przetwarzanie zdarzeń jest wywoływane wyłącznie z kontekstu wewnętrznego wątku systemu GUIX. W ten sposób wymagania dotyczące stosu do przetwarzania obsługi zdarzeń dotyczą tylko wątku GUIX.

### <a name="implementing-custom-event-processing-example"></a>Implementowanie niestandardowego przetwarzania zdarzeń (przykład) 

Możesz udostępnić własną funkcję przetwarzania zdarzeń dla dowolnego widżetu lub okna w systemie GUIX. Jeśli tworzysz własny niestandardowy typ widżetu, zwykle zainstalujesz niestandardową obsługę zdarzeń w funkcji tworzenia widżetu. Jeśli tylko rozszerzasz lub modyfikujesz działanie istniejącego widżetu lub okna, możesz wywołać funkcję interfejsu API interfejsu gx_widget_event_process_set po utworzeniu widżetu lub okna. Prawie zawsze zapewniasz własną obsługę zdarzeń dla okien najwyższego poziomu (nazywanych również ekranami) w celu przetwarzania zdarzeń generowanych przez kontrolki podrzędne. Przetwarzanie zdarzenia generowanego przez kontrolki podrzędne ekranu to główny sposób dodawania funkcji do aplikacji GUIX.

Załóżmy na przykład, że definiujesz ekran najwyższego poziomu o nazwie "main_menu".
Ten ekran może być zdefiniowany przy użyciu programu GUIX Studio lub można go utworzyć w kodzie aplikacji. Jeśli zdefiniujesz ekran w programie GUIX Studio, wystarczy wpisać nazwę procedury obsługi zdarzeń w polu właściwości programu Studio dla tego ekranu, a kod specyfikacji wygenerowany przez program Studio automatycznie zainstaluje program obsługi zdarzeń. W tym przypadku wywołamy niestandardową obsługę zdarzeń main_menu_event_handler ***i*** powinna ona być zakodowana w ten sposób:

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

W powyższym przykładzie należy zauważyć, że w przypadku zdarzeń systemowych, takich jak **GX_EVENT_SHOW** (zdarzenia generowane wewnętrznie w celu powiadomienia widżetu o zmianie stanu), aplikacja musi przekazać te zdarzenia do podstawowej funkcji przetwarzania zdarzeń widżetu, aby zapewnić, że odbywa się normalne przetwarzanie. Następnie aplikacja może dodać dodatkową logikę zgodnie z potrzebami. Wszystkie zdarzenia, które nie są obsługiwane przez aplikację (przypadek domyślny powyżej), również powinny być przekazywane do podstawowej funkcji przetwarzania zdarzeń. Ponieważ ten przykład dotyczy ekranu najwyższego poziomu opartego na GX_WINDOW **,** domyślną funkcją przetwarzania zdarzeń jest gx_window_event_process.

### <a name="drawing-function"></a>Drawing, funkcja 

Wszystkie rysowanie widżetów odbywa się niezależnie od obsługi zdarzeń. Jest to bardziej wydajne, ponieważ rysowanie jest zwykle kosztowne pod względem cykli procesora CPU. Dzięki zaimplementowaniu algorytmu odroczonego rysowania wszystkie zaległe zdarzenia i skojarzone zmiany wyświetlania można wykonać przed wykonaniem jakiegokolwiek rysowania, eliminując w ten sposób marnowanie rysowania. Podobnie jak w przypadku przetwarzania zdarzeń, istnieje domyślna funkcja rysowania widżetów dla większości widżetów o ***nazwie gx_<typu widżetu>_draw***, gdzie xxx jest typem widżetu. W większości przypadków aplikacja nie musi martwić się o funkcję rysowania żadnego z widżetów. Jednak w sytuacjach, gdy aplikacja wymaga niestandardowego lub uzupełniającego rysowania, aplikacja może zastąpić domyślną funkcję rysowania własną za pośrednictwem interfejsu ***API*** GUIX gx_widget_draw_set . Ta funkcja umożliwia aplikacji zapewnienie własnej, dostosowanej funkcji rysowania dla dowolnego widżetu. Dzięki temu aplikacja może definiować całe nowe typy widżetów.

> [!IMPORTANT]
> Funkcje rysowania aplikacji mogą korzystać z zalet (czyli nie duplikować kodowania) domyślnego rysunku, po prostu wywołując je bezpośrednio z przesłoniętą funkcją rysowania.

Rysowanie widżetów jest wywoływane wyłącznie z kontekstu wewnętrznego wątku systemu GUIX. W ten sposób wymagania dotyczące chronometrażu i stosu do wykonania rysowania dotyczą tylko wątku GUIX.

### <a name="implementing-custom-drawing-example"></a>Implementowanie rysowania niestandardowego (przykład) 

Funkcja rysowania dla dowolnego widżetu jest przywołyowana za pośrednictwem wskaźnika funkcji pośredniej, który jest elementem członkowskim GX_WIDGET sterowania. Jeśli do definiowania widżetu używasz programu GUIX Studio, możesz zainstalować własny wskaźnik funkcji, wpisując nazwę funkcji w parametrze "Drawing Function" właściwości widżetu, a program Studio zainstaluje wskaźnik funkcji po utworzeniu widżetu. Jeśli tworzysz widżet w kodzie aplikacji, musisz użyć funkcji interfejsu API gx_widget_draw_set, aby ***zainstalować*** niestandardową funkcję rysowania po utworzeniu widżetu.

W tym przykładzie załóżmy, że chcesz dostosować wygląd przycisku. Przycisk będzie wyglądać bardzo podobnie do GX_TEXT_BUTTON, **ale** gdy przycisk nie zostanie naciśnięty, dodamy małą zieloną mapę bitową "LED_ON" w prawej części przycisku po naciśnięciu przycisku oraz małą mapę bitową "LED_OFF". Chcemy utworzyć przycisk, który wygląda jak na ilustracjach poniżej.

![Zrzut ekranu przedstawiający zielony przycisk dla opcji Wł.](./media/guix/image4.jpg) niestandardowy przycisk "on"

![Zrzut ekranu przedstawiający czerwony przycisk Wył.](./media/guix/image5.jpg) niestandardowy przycisk "off"

W tym przypadku napiszemy funkcję rysowania przycisku, która wygląda podobnie do poniższej.

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

Kontekst rysowania jest tworzony dynamicznie w czasie wykonywania, ponieważ guix wykonuje każdą operację odświeżania kanwy. Kontekst rysowania łączy ze sobą kanwę, sterownik ekranu i pędzl używany do wykonywania bieżących operacji rysowania.

Kontekst rysowania jest definiowany przez **GX_DRAW_CONTEXT** struktury.
Ta struktura zawiera zmienne, które definiują przycinanie i widok bieżącej operacji rysowania, definiują bieżącą kanwę i definiują bieżący sterownik ekranu w użyciu. Struktura **GX_DRAW_CONTEXT** zawiera również pędzl używany do rysowania. Pędzl kontekstowy rysowania jest członkiem, z który będziesz pracować bezpośrednio w niestandardowych funkcjach rysowania. Struktura pędzla jest zdefiniowana tak, jak pokazano w poniższym kodzie.

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

Pole **gx_brush_pixelmap** definiuje mapę pikseli do użycia dla wypełnienia prostokątem i wielokątem. Ten członek nie jest używany, **chyba że gx_brush_style** zawiera styl **GX_BRUSH_PIXELMAP** danych.

Symbol **gx_brush_font** definiuje czcionkę używaną do rysowania tekstu.
Wzorzec **gx_brush_line_pattern** definiuje wzorzec używany dla linii przerywanych.
Gx_brush_style  jest zestawem flag stylu, które mogą być lub mogą być połączone w celu pełnego zdefiniowania atrybutów pędzla. Dostępne są następujące flagi stylu pędzla.

**GX_BRUSH_OUTLINE**  
**GX_BRUSH_SOLID_FILL**  
**GX_BRUSH_PIXELMAP_FILL**  
**GX_BRUSH_ALIAS**  
**GX_BRUSH_UNDERLINE**  
**GX_BRUSH_ROUND**

Linia **gx_brush_width** definiuje linię za pomocą dla rysowania liniowego lub szerokość konturu dla konturu rysowania kształtów.

Składowa **gx_brush_line_color** definiuje kolor pierwszego planu dla rysowania linii i rysowania tekstu.

Członek **gx_brush_fill_color** definiuje kolor wypełnienia stałego używany do wypełniania kształtem. Składnik kontekstu GUIX udostępnia zestaw interfejsów API zaprojektowanych w celu bardzo łatwego modyfikowania bieżącego pędzla w aktywnym kontekście. Te interfejsy API **obejmują gx_context_brush_define**, **gx_context_line_color_set**, **gx_context_fill_color_set**, **gx_context_font_set** i wiele innych.

Kontekst rysowania obiektu nadrzędnego jest dziedziczony przez obiekty dzieci. W rzeczywistości klon nadrzędnego kontekstu rysowania jest dziedziczony przez obiekty podrzędne podczas wywoływania ich funkcji rysowania. Element podrzędny może modyfikować kontekst bez wpływu na rysunek nadrzędny, ale w razie potrzeby może również dziedziczyć informacje z elementu nadrzędnego, takie jak kolor pędzla i styl.

## <a name="guix-window-component"></a>Składnik okna GUIX 

Składnik okna jest odpowiedzialny za wszystkie przetwarzanie okien w graficznym interfejsie użytkownika. Okno GUIX to zasadniczo odrębny obszar wyświetlania, który może zawierać co najmniej jeden widżet podrzędny. W graficznym interfejsie użytkownika okno jest w rzeczywistości specjalną formą podstawowego obiektu widżetu.

Okna GUIX są implementowane w sposób obiektowy z pełną obsługą dziedziczenia. Jest to realizowane przy użyciu ansi C, co powoduje najmniejsze wymagania dotyczące pamięci i przetwarzania.

Okna GUIX rozszerzają funkcjonalność widżetu GUIX głównie przez dodanie obsługi przewijania w poziomie i w pionie. Obiekty okna GUIX mogą automatycznie tworzyć i wyświetlać paski przewijania oraz reagować na dane wejściowe paska przewijania. Okna wymienne mają również wbudowaną obsługę zdarzeń, która umożliwia przenoszenie lub przeciąganie okna na podstawie zdarzeń wprowadzania piórem.
Na koniec okno GUIX reaguje na odbieranie fokusu wejściowego, przenosząc okno na przód okna w kolejności Z.

Okno GUIX zachowuje koncepcję obszaru klienta *,* który jest wewnętrzną częścią okna po obramowania okna, a obiekty inne niż klienta, takie jak paski przewijania, są usuwane z dostępnego obszaru. Widżety podrzędne obszaru klienta są obcinane do obszaru klienta okna, podczas gdy elementy podrzędne inne niż klienta, takie jak paski przewijania, mogą być rysowane poza obszarem klienta, ale nadal są obcinane do wymiarów zewnętrznych okna.

Windows są utrzymywane w sposób nadrzędny-podrzędny, gdzie dzieci dziedziczą właściwości z ich elementu nadrzędnego. Okna podrzędne mogą mieć własne okna podrzędne, ponownie dziedziczące różne cechy po elementach nadrzędnych. Cechy każdego okna można jawnie ponownie zdefiniować za pośrednictwem różnych wywołań interfejsu API GUIX.

### <a name="window-creation"></a>Tworzenie okna 

Obiekt okna można utworzyć podczas inicjowania lub w dowolnym momencie podczas wykonywania wątków aplikacji. Nie ma żadnego limitu liczby obiektów okien, które mogą zostać utworzone przez aplikację. Nie ma również żadnego limitu liczby dzieci, które może mieć okno.

### <a name="window-control-block"></a>Blok sterowania okna 

Właściwości każdego obiektu okna znajdują się  w jego bloku sterowania GX_WINDOW i są zdefiniowane w **_gx_api.h_**. Pamięć wymagana dla obiektu okna jest dostarczana przez aplikację i może być zlokalizowana w dowolnym miejscu w pamięci. Najczęściej jednak kontrolka obiektu okna blokuje globalną strukturę, definiując ją poza zakresem dowolnej funkcji.

### <a name="root-window"></a>Okno główne 

Interfejs GUIX wymaga tak zwanego okna głównego dla każdej kanwy. Okno główne jest bez obramowania i ma takie same wymiary jak kanwa, do której jest dołączona. Jest ona używana głównie jako kontener dla wszystkich widżetów pierwszego poziomu i okien. Okno główne jest zazwyczaj tworzone przez aplikację za pośrednictwem funkcji interfejsu API ***gx_window_root_create***, wkrótce po utworzeniu ekranu i kanwy. Jeśli używasz funkcji wygenerowanej w programie Studio gx_studio_display_configure, adres okna głównego może zostać zwrócony w lokalizacji przekazanej jako ostatni parametr do tej funkcji.

Okno główne domyślnie nie może być przenoszalne, a w najprostszym przypadku okno główne jest rozmiarem kanwy. Okno główne w efekcie rysuje tło ekranu, więc aby zmienić kolor tła wyświetlania lub wyświetlić tapetę tła, należy przypisać kolor lub tapetę do okna głównego.

Jeśli okno główne można przenosić, nie zmienia się jego położenie na kanwie tak jak robiłoby to okno podrzędne, ale przez przeniesienie samej kanwy.
Ta funkcja umożliwia oknie głównym GUIX wykorzystanie sprzętu obsługującego wiele buforów ramek z rejestrami przesunięcia sprzętowego.

### <a name="background"></a>Tło 

Tła okien to pełne kolory lub obrazy map bitowych. Na poziomie systemu istnieje domyślne tło okna, które udostępnia domyślne ustawienie dla początkowego zestawu okien. Oczywiście każde tło okna można zmienić za pomocą interfejsu API GUIX.

Aby zmienić pełne tło okna, użyj interfejsu API ***gx_widget_fill_color_set*** API. Aby przypisać tapetę do okna, użyj interfejsu API ***gx_window_wallpaper_set*** API.

### <a name="scrolling"></a>Przewijanie 

Interfejs GUIX obsługuje standardowe przewijanie okien, gdy obszar wymagany do wyświetlenia dzieci okna przekracza bieżący rozmiar okna — w poziomie i/lub w pionie. Aby włączyć przewijanie, aplikacja musi utworzyć żądane paski przewijania i dołączyć je do okna.

Składnik okna GUIX zapewnia domyślną implementację przewijania na podstawie rozmiaru obszaru klienta okna i zakresu wszystkich widżetów podrzędnych. Aplikacje mogą również zapewnić własną implementację i interpretację z przewijaniem, przesłaniając ***gx_window_scroll_info_get*** funkcji dla określonego okna.

### <a name="event-notification"></a>Powiadomienie o zdarzeniu 

Funkcja przetwarzania zdarzeń domyślnego okna różni się od GX_WIDGET przetwarzania zdarzeń głównie w przypadku obsługi zdarzeń przewijania i zmiany rozmiaru. GX_WINDOW obsługi dla zdarzeń przewijania i zmiany rozmiaru.

Aplikacja może również dodawać własne zdarzenia niestandardowe, rozpoczynając numerycznie po stałej **GX_FIRST_APP_EVENT**. Wszystkie numery zdarzeń po tej stałej są zarezerwowane do użytku przez aplikację. Oczywiście procedura obsługi zdarzeń okna aplikacji musi mieć przetwarzanie dla takich zdarzeń aplikacji.

### <a name="event-processing"></a>Przetwarzanie zdarzeń 

Podobnie jak wszystkie inne typy widżetów, istnieje domyślna funkcja przetwarzania zdarzeń okna dla każdego okna o ***nazwie gx_window_event_process***. Zazwyczaj zastąpisz tę funkcję obsługi zdarzeń własnym programem obsługi zdarzeń w tworzyć oknach. W ten sposób będziesz reagować na zdarzenia i podjąć działania na podstawie zdarzeń generowanych przez kontrolki podrzędne okna.

Ważne jest, aby pamiętać o wywołaniu podstawowej funkcji ***gx_window_event_process*** dla zdarzeń systemowych GUIX w przypadku zastąpienia tej procedury obsługi zdarzeń, aby umożliwić obsługę zdarzeń domyślnych oprócz każdej akcji, która jest dodawania do programu obsługi zdarzeń. Jeśli na przykład udostępnisz niestandardową obsługę zdarzenia **GX_EVENT_SHOW** i nie przekażemy tego zdarzenia do gx_window_event_process ***,*** okno nigdy nie stanie się widoczne.
Aby udostępnić niestandardowy program obsługi zdarzeń dla okna, użyj ***funkcji gx_widget_event_process_set,*** aby zdefiniować adres procedury obsługi zdarzeń. Ta funkcja zastępuje domyślną funkcję przetwarzania zdarzeń funkcją przetwarzania funkcji zdarzeń określoną w interfejsie API.

> [!IMPORTANT]
> Funkcje przetwarzania zdarzeń aplikacji mogą korzystać z zalet (tj. nie duplikować przetwarzania) przetwarzania domyślnego, po prostu wywołując domyślne gx_window_event_process ***bezpośrednio.***

Przetwarzanie zdarzeń jest wywoływane wyłącznie z kontekstu wewnętrznego wątku systemu GUIX. W ten sposób wymagania dotyczące stosu do przetwarzania obsługi zdarzeń dotyczą tylko wątku GUIX.

## <a name="guix-image-reader-component"></a>Składnik czytnika obrazów GUIX 

Składnik czytnika obrazów udostępnia narzędzia i funkcje interfejsu API służące do dekompresowania nieprzetworzonych skompresowanych obrazów do formatu GUIX pixelmap. Obsługiwane są nieprzetworzone dane obrazu w formacie JPEG i PNG, a dodatkowe formaty są zarezerwowane do przyszłych wersji.

Należy pamiętać, że w przypadku większości aplikacji GUIX składnik czytnika obrazów GUIX nie jest wymagany. Większość aplikacji korzysta z aplikacji GUIX Studio w celu konwertowania zasobów graficznych w formacie JPEG i PNG na zasoby GX_PIXELMAP **GUIX.** Składnik czytnika obrazów GUIX jest używany, gdy nieprzetworzone zasoby graficzne są znane tylko w czasie wykonywania lub gdy ograniczenia magazynu systemu uniemożliwiają przechowywanie zasobów w **GX_PIXELMAP** formacie. Dane obrazu w formacie JPEG i PNG są zwykle bardziej kompaktowa niż format **GX_PIXELMAP,** jednak wykonywanie dekompresji i dynamicznej konwersji przestrzeni kolorów tych typów obrazów wiąże się ze znacznym obciążeniem środowiska uruchomieniowego.

Jeśli nieprzetworzone obrazy JPEG lub PNG są przekazywane do funkcji interfejsu API gx_canvas_pixelmap_draw, plik GUIX dynamicznie dekompresuje i pobiera dane JPEG lub PNG. Należy pamiętać, że będzie to mieć znaczący negatywny wpływ na szybkość rysowania w czasie wykonywania, a przekazywanie danych obrazu w formacie RAW do funkcji gx_canvas_pixelmap_draw nie jest zalecane, chyba że używasz sprzętowego obiektu docelowego obsługującego dekompresję sprzętową plików JPEG lub PNG.

> [!IMPORTANT]
> Przekazywanie nieprzetworzonych obrazów w formacie JPEG lub PNG do interfejsu API gx_canvas_pixelmap_draw wiąże się ze znacznym obciążeniem środowiska uruchomieniowego dla większości sprzętu docelowego.

Alternatywnie nieprzetworzone dane JPEG i PNG można przekonwertować na format GX_PIXELMAP czasie wykonywania przy użyciu składnika Czytnik obrazów.
Mapy pikseli opracowane w ten sposób mogą być używane i rysowane podobnie jak mapy pikseli opracowane przez program Studio i zawarte w pliku zasobów. Dzięki temu aplikacja może wykonać dekompresję, dithering i konwersję przestrzeni kolorów jeden raz (zazwyczaj podczas uruchamiania programu) zamiast wykonywać te operacje za każdym razem, gdy obraz zostanie narysowany.

Funkcje składnika Czytnik obrazów obejmują:

***gx_image_reader_create***  
***gx_image_reader_palette_set***  
***gx_image_reader_start***

## <a name="guix-animation-component"></a>Składnik animacji GUIX 

Składnik animacji GUIX to zestaw funkcji i usług używanych do automatyzowania automatyzacji przechodzenia ekranu i widżetu. Składnik Animacja GUIX obsługuje zanikanie, zanikanie i przesuwanie lub animacje typu slajdu dowolnego typu widżetu.

Animacje typu zanikania mogą być obsługiwane przez zmianę wewnętrznej wartości alfa widżetów zanikania (jeśli jest włączona funkcja **GX_BRUSH_ALPHA_SUPPORT)** lub przez rysowanie dowolnej kolekcji widżetów do oddzielnej kanwy pamięci, gdy następnie jest wmieszana z tłem. W przypadku obiektów docelowych sprzętu, które obsługują wiele warstw grafiki sprzętowej, obsługę płynnych efektów zanikania najlepiej osiągnąć przy użyciu tej metody mieszania kanwy, często przy bardzo małej wymaganej przepustowości procesora. W przypadku obiektów docelowych sprzętu, które nie obsługują wielu warstw graficznych, w przypadku korzystania z 16 bpp i wyższych głębokości kolorów obsługiwane jest mieszanie przy użyciu wartości alfa pędzla GUIX.

Jeśli animacja powinna używać oddzielnej kanwy do rysowania, składnik animacji GUIX udostępnia w tym celu gx_animation_canvas_define interfejsu API. Inne typy animacji nie wymagają oddzielnej kanwy, ale będą z nich korzystać, jeśli są dostępne. To sprawia, że najlepsze możliwe użycie dowolnej bazowej obsługi sprzętu dla wielu powierzchni sprzętowych.

Zmienne kontrolujące animację są definiowane przez dwa bloki sterujące. Najpierw należy **GX_ANIMATION** sterowania, który definiuje kontroler animacji. Kontroler animacji jest aparatem sterowania, który wykonuje zdefiniowaną sekwencję animacji. Pojedynczy kontroler animacji może być wielokrotnie ponownie używany do uruchamiania wielu różnych sekwencji animacji. Jeśli musisz uruchomić wiele sekwencji animacji jednocześnie, możesz utworzyć wiele GX_ANIMATION **animacji.**

Składnik systemu GUIX może zapewnić blok wielokrotnego użytku struktur sterujących programu **GX_ANIMATION, który** może być żądany przez aplikację, gdy jest potrzebna, i animacja jest potrzebna i są automatycznie zwracane do puli systemowej po zakończeniu sekwencji animacji. Dzięki temu aplikacja nie będzie statycznie definiowała struktury **GX_ANIMATION** każdej animacji, która może zostać zaimplementowana. Rozmiar tej puli  struktur GX_ANIMATION jest definiowany przez stałą **GX_ANIMATION_POOL_SIZE**, która domyślnie ma wartość 6, co oznacza, że domyślnie z puli systemowej można przydzielać 6 równoczesnych animacji. Ta stała może być oczywiście ponownie zdefiniowana w pliku nagłówka gx_user.h jest wymagana większa liczba równoczesnych animacji. Jeśli **GX_ANIMATION_POOL_SIZE** jest równa zero, składnik systemu GUIX nie zapewnia puli animacji ani powiązanych usług.

Drugim blokiem sterującym lub strukturą używaną do definiowania animacji jest **GX_ANIMATION_INFO** struktura. Ta struktura służy do definiowania jednej konkretnej sekwencji animacji. Tę strukturę informacji można przekazać do kontrolera animacji, aby zainicjować sekwencję animacji przy użyciu gx_animation_start api. Struktura **GX_ANIMATION_INFO** zawiera następujące pola:

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

Element **gx_animation_target** definiuje element widget docelowy, na których będzie działać kontroler animacji.

Element **gx_animation_parent** definiuje widżet nadrzędny, jeśli istnieje, do którego zostanie dołączony widżet docelowy po zakończeniu sekwencji animacji. Adres gx_animation_parent jest również odbiorcą zdarzenia GX_ANIMATION_COMPLETE, które jest generowane po zakończeniu animacji.

Element **gx_animation_screen_list** definiuje listę widżetów dla animacji slajdów ekranu sterowanych piórem. Lista widge powinna być zakończona wskaźnikiem GX_NULL, a każdy widżet na liście powinien mieć te same wymiary x,y co gx_animation_parent.

Ten **gx_animation_style** to maski bitów definiujące typ animacji do wykonania i skojarzone opcje. Flagi stylu animacji są następujące.

| Flaga &nbsp; stylu &nbsp; animacji | Opis |
| --- | --- |
| GX_ANIMATION_TRANSLATE | Zażądaj animacji slajdu lub zanikanie typu. |
| GX_ANIMATION_SCREEN_DRAG | Zażądaj animacji przeciągania ekranu sterowanej wprowadzaniem piórem. |

Poniższe flagi mogą być używane w połączeniu z **animacjami SCREEN_DRAG** typu.

| Flagi &nbsp; &nbsp; przeciągania ekranu | Opis |
| --- | --- |
| GX_ANIMATION_WRAP | Lista ekranów powinna być zawijany od końca do początku. |
| GX_ANIMATION_HORIZONTAL | Dozwolone przeciąganie ekranu w kierunku poziomym.  |
| GX_ANIMATION_VERTICAL | Dozwolone przeciąganie ekranu w kierunku pionowym. |

Poniższej flagi można używać w połączeniu z animacjami tłumaczenia.

| Tłumaczenie &nbsp; flag &nbsp; animacji | Opis |
| --- | --- |
| GX_ANIMATION_DETACH | Odłącz obiekt docelowy animacji od elementu nadrzędnego animacji po zakończeniu animacji. Jeśli obiekt docelowy został dynamicznie przydzielony i utworzony przez zautomatyzowaną obsługę zdarzeń wygenerowaną przez program GUIX Studio, obiekt docelowy zostanie usunięty po odłączeniu. |
| GX_ANIMATION_TRANSLATE | Typy animacji to animacje sterowane czasomierzem. Aplikacja definiuje pozycję początkową i końcową oraz początkową i końcową wartość alfa dla widżetu docelowego, a menedżer animacji tworzy czasomierz, który będzie służyć jako siła wymuszania wykonywania animacji.
| GX_ANIMATION_SCREEN_DRAG | Różni się od **animacji TRANSLATE** tym, że ten typ animacji jest oparty na zdarzeniach wprowadzania piórem. Ten typ animacji śledzi wraz z wprowadzaniem ekranu dotykowego w celu przesunięcia widżetu docelowego, gdy użytkownik przeciąga piórem lub piórem po wejściowym ekranie dotykowym. Aby korzystać z tego typu animacji, aplikacja powinna wywołać interfejs **_API_** gx_animation_drag_enable, aby włączyć tę animację. |

Wartość **gx_animation_id** jest przekazywana z powrotem do elementu nadrzędnego animacji event.gx_event_sender polu GX_ANIMATION_COMPLETE **zdarzenia.** Ta wartość jest używana przez element nadrzędny animacji do określenia, która z kilku animacji child zgłasza ukończenie. Ta wartość może być 0, a animacja z wartością identyfikatora 0 nie wygeneruje ANIMATION_COMPLETE **zdarzenia.**

Wartość **gx_animation_start_delay** jest liczbą znaczników GUIX wskazującą liczbę takt czasomierza, które mają zostać opóźnione po wywołaniu gx_animation_start _ przed wykonaniem ***animacji. Wartość może być 0, aby rozpocząć animację natychmiast po wywołaniu*** funkcji _ gx_animation_start .

Pole **gx_animation_frame_interval** definiuje liczbę takt czasomierza GUIX (wielokrotność taktowania bazowego systemu operacyjnego), które mają być opóźnione między każdą ramką sekwencji animacji. Wartość minimalna to 1.

Element **gx_animation_start_position** definiuje lewy górny punkt początkowy widżetu docelowego dla animacji tłumaczenia.

Element **gx_animation_end_position** definiuje lewą górną pozycję końcową widżetu docelowego dla animacji typu tłumaczenia.

Pole **gx_animation_start_alpha** definiuje początkową wartość alfa kanwy dla animacji typu tłumaczenia.

Pole **gx_animation_end_alpha** definiuje końcową wartość alfa kanwy dla animacji typu tłumaczenia.

Pole **gx_animation_steps** definiuje, ile kroków lub ramek kontroler powinien wykonać na animacje tłumaczenia. Większa liczba kroków zapewnia gładszy slajd i/lub zanikanie, ale wymaga również większej przepustowości systemu.

Aby zaimplementować efekty animacji w aplikacji, należy najpierw wywołać ***gx_animation_create,*** aby zainicjować kontroler animacji. Jeśli animacja będzie używać kanwy pomocniczej, zaimicjuj tę kanwę, wywołując gx_animation_canvas_define. Następnie należy zainicjować strukturę **GX_ANIMATION_INFO,** aby zdefiniować określony typ animacji do wykonania oraz inne parametry animacji. Na koniec wywołaj gx_animation_start, aby wyzwolić sekwencję animacji.

Gdy kontroler animacji ukończy sekwencję animacji, wysyła zdarzenie GX_ANIMATION_COMPLETE do widżetu nadrzędnego, co pozwala na dowolne oczyszczanie kanwy animacji w tym czasie. 

## <a name="guix-utility-component"></a>Składnik narzędzia GUIX 

Składnik narzędzia jest odpowiedzialny za wszystkie typowe funkcje narzędzi w graficznym interfejsie użytkownika. Są to typowe funkcje, które są przydatnymi narzędziami i mogą być wywoływane z dowolnego miejsca w aplikacji lub wewnętrznego kodu GUIX. Funkcje składników narzędzia obejmują następujące elementy.

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
