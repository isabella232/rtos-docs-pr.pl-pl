---
title: Dodatek H — GUIX Build-Time flagi konfiguracji
description: Dowiedz się więcej na temat flag konfiguracji czasu kompilacji GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 65095e326bc6809eba6e9472e2d74325351354ca
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822320"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>Dodatek H — GUIX Build-Time flagi konfiguracji

GUIX obsługuje kilka opcji kompilacji warunkowej i wartości konfiguracyjnych. Ustawienie domyślne tych warunków i wartości konfiguracji można zastąpić przez wstępne zdefiniowanie wartości w pliku nagłówkowym gx_user. h lub w wierszu polecenia kompilatora.

**GX_DISABLE_THREADX_BINDING**
- Domyślnie: niezdefiniowane
- Opis: to warunkowe może służyć do wyłączenia domyślnego powiązania ThreadX RTO. Jeśli chcesz uruchomić GUIX z RTOem innym niż ThreadX, należy #define GX_DISABLE_THREADX_BINDING i zapewnić własne usługi powiązań RTO.

GX_SYSTEM_TIMER_MS
- Wartość domyślna: 20
- Opis: Ta wartość definiuje żądany interwał czasomierza GUIX lub precyzję.

TX_TIMER_TICKS_PER_SECOND
- Wartość domyślna: 100
- Opis: Ta wartość definiuje liczbę frequences przerwań czasomierza wysyłania. Ponieważ domyślny czasomierz interwału ThreadX to 10 ms, wartość domyślna to 100-Hz częstotliwość.

GX_SYSTEM_TIMER_TICKS
- Wartość domyślna: ((GX_SYSTEM_TIMER_MS * TX_TIMER_TICKS_PER_SECOND)/1000)
- Opis: Ta wartość definiuje liczbę podstawowych taktów czasomierza RTO na cykl czasomierza GUIX. Wartość domyślna to 2, co oznacza, że interwał czasomierza GUIX wynosi 2 interwały przerwań czasomierza ThreadX lub domyślnie 20 ms.

GX_DISABLE_MULTITHREAD_SUPPORT
- Domyślnie: nie zdefiniowano
- Opis: Ta wartość warunkowa czasu kompilacji może zostać użyta w celu wyłączenia obsługi interfejsu API GUIX dla wielu wątków wywołujących interfejs API GUIX jednocześnie. Jeśli tylko jeden wątek aplikacji będzie używał interfejsu API GUIX, należy zdefiniować tę flagę, aby zmniejszyć obciążenie systemu związane z ochroną krytycznych sekcji kodu.

GX_DISABLE_UTF8_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: Ta wartość warunkowa czasu kompilacji może zostać użyta do usunięcia wewnętrznej obsługi kodowania ciągu formatu UTF8 GUIX. Jeśli używasz tylko wartości znakowych M-0xFF w aplikacji, włączenie tego #define spowoduje zmniejszenie rozmiaru kodu i nakładu związanego z obsługą kodowania ciągu formatu UTF8.

GX_DISABLE_ARC_DRAWING_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: to warunkowe może służyć do zmniejszania rozmiaru kodu biblioteki GUIX i rozmiaru struktury GX_DISPLAY przez usunięcie obsługi funkcji rysowania łuku koła, łuku, koła i elipsy. Te funkcje nie są wymagane przez domyślny zestaw widżetu GUIX.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: to warunkowe można zdefiniować, aby usunąć obsługę dekodera oprogramowania GUIX Library Runtime JPEG i PNG. Jeśli aplikacja nie wymaga dekodowania środowiska uruchomieniowego plików jpg lub PNG, oznacza to, że aplikacja nie korzysta z formatu RAW pixelmaps utworzonego przez program Studio i nie odczytuje plików obrazów z zewnętrznego systemu plików, można włączyć tę #define w celu zmniejszenia rozmiaru biblioteki GUIX.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- Domyślnie: nie zdefiniowano
- Opis: to warunkowe może służyć do usuwania obsługi biblioteki GUIX na potrzeby ładowania binarnych danych zasobów. Zasobów binarnych można użyć do powiązania środowiska uruchomieniowego danych zasobów z aplikacją GUIX. Jeśli używasz tylko plików zasobów w formacie kodu źródłowego C, możesz zdefiniować ten warunek, aby zmniejszyć rozmiary biblioteki GUIX.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: podczas uruchamiania o 16 BPP i większej głębi kolorów, GUIX opcjonalnie obsługuje rysowanie grafiki niebędącej łukiem, pixelmaps i czcionek o wartości alfa zdefiniowanej przez pędzel kontekstu rysowania. Obsługa tego trybu rysowania powoduje wprowadzenie małego obciążenia środowiska uruchomieniowego i wzrostu rozmiaru biblioteki, który można wyeliminować, definiując tę flagę, jeśli nie jest wymagana obsługa rysowania przy użyciu mieszania alfa. Należy zauważyć, że pixelmaps z kanałem alfa, czcionki antyaliasowe i inne tryby rysowania wygładzania są nadal obsługiwane niezależnie od tego ustawienia warunkowego.

GX_DISABLE_THREADX_TIMER_SOURCE
- Wartość domyślna: nie zdefiniowano.
- Opis: to warunkowe może służyć do wyłączania źródła czasomierza ThreadX. Należy zdefiniować GX_DISABLE_THREADX_TIMER_SOURCE, jeśli chcesz użyć innego źródła czasomierza.

GX_REPEAT_BUTTON_INITIAL_TICS
- Wartość domyślna: 10.
- Opis: Jeśli przycisk ma GX_STYLE_BUTTON_REPEAT stylu, ta wartość definiuje, jak długo przycisk czeka przed rozpoczęciem wysyłania powtarzających się zdarzeń GX_EVENT_CLICKED.

GX_MAX_QUEUE_EVENTS
- Wartość domyślna: 48.
- Opis: Określa rozmiar kolejki zdarzeń GUIX w jednostkach wpisów struktury zdarzeń. W przypadku przepełnienia kolejki zdarzeń, zdarzenia przekazywane do kolejki są odrzucane i GX_SYSTEM_ERROR są zwracane przez funkcję gx_system_event_send ().

GX_MAX_DIRTY_AREAS
- Wartość domyślna: 64.
- Opis: określa maksymalną liczbę unikatowych wpisów listy zanieczyszczonych, które mogą być obsługiwane przez jedną kanwę. Gdy przepływa lista zanieczyszczona, GUIX domyślnie oznacza oznaczenie okna głównego kanwy jako zanieczyszczonego, co jest mniej wydajne niż rysowanie pojedynczych widżetów podrzędnych.

GX_MAX_CONTEXT_NESTING
- Wartość domyślna: 8.
- Opis: definiuje maksymalne zagnieżdżenie stosu kontekstu rysowania. Jest to równoznaczne z maksymalną zagnieżdżeniem elementów widget nadrzędny/podrzędny/podrzędny/podrzędny w definicji interfejsu użytkownika.

GX_MAX_INPUT_CAPTURE_NESTING
- Wartość domyślna: 4.
- Opis: Określa rozmiar stosu używany do obsługi listy widżetów, która przechwytuje dane wejściowe użytkownika (myszą i klawiaturą).

GX_SYSTEM_THREAD_PRIORITY
- Wartość domyślna: 16.
- Opis: definiuje priorytet wątku GUIX utworzonego podczas gx_system_initialize ().

GX_SYSTEM_THREAD_TIMESLICE
- Wartość domyślna: 10.
- Opis: definiuje GUIX wątku timeslice pod kątem taktów czasomierza RTO. Jeśli inne wątki są zdefiniowane z takim samym priorytetem jak wątek GUIX, ta wartość określa, jak często te wątki konkurujące są przydzielone do kontroli procesora CPU.

GX_CURSOR_BLINK_INTERVAL
- Wartość domyślna: 20.
- Opis: określa szybkość, z jaką kursor wejściowy miga dla widżetów wprowadzania tekstu. Ta wartość jest w zakresie taktów czasomierza GUIX, która domyślnie jest definiowana jako 50 ms, więc wartość 20 wskazuje, że kursor wejściowy miga na sekundę.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- Wartość domyślna: 32.
- Opis: Określa rozmiar pamięci podręcznej indeksu uruchamiania listy, która jest obsługiwana przez widok tekstu wielowierszowego i widżety wprowadzania tekstu wielowierszowego. Ta pamięć podręczna umożliwia szybkie przewijanie w pionie widżetów tekstu wielowierszowego. W celu uzyskania najlepszej wydajności rozmiar pamięci podręcznej powinien być ustawiony na wartość większą niż liczba widocznych wierszy największego widżetu tekstu wielowierszowego zdefiniowanego przez aplikację. Na przykład, jeśli najbardziej widoczne wiersze dla dowolnego widżetu tekstowego są 20 wierszy, aplikacja może zdefiniować rozmiar pamięci podręcznej 32 (domyślnie), która umożliwia GUIX przewijanie w pionie bez ponownego obliczania wszystkich indeksów uruchamiania wiersza.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- Wartość domyślna: 4.
- Opis: blok formantu wielowierszowego przycisku tekstu zachowuje wskaźnik do każdego wiersza tekstu, który ma być wyświetlany przez przycisk. Ta wartość określa liczbę wskaźników tekstowych wymaganych przez najgorszy przycisk tekstu wielowierszowego.

GX_POLYGON_MAX_EDGE_NUM
- Wartość domyślna: 10.
- Opis: Ta wartość określa najbardziej skomplikowany Wielokąt, który może być rysowany przez GUIX. Algorytm rysowania wielokątów określa linie, które są konieczne do zdefiniowania krawędzi wielokątów, a definicja określa maksymalną liczbę krawędzi, które mogą być obsługiwane.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- Wartość domyślna: 16.
- Opis: dla pokrętła przewijania numeru widżet kółka przewijania konwertuje wartości całkowite na ciągi ASCII. Ta wartość określa maksymalną długość ciągu wymaganą do wyświetlenia przypisanych wartości całkowitych.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- Wartość domyślna: 5.
- Opis: definiuje liczbę cykli czasomierza GUIX (50 ms) między aktualizacjami miernika cyklicznego skonfigurowanego do animowania ruchu wskazówki między ostatnią i bieżącą pozycją kątową.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- Wartość domyślna: 16.
- Opis: monit numeryczny przydziela buforowi konwersję wartości całkowitej przypisanej do monitu do ciągu ASCII. Ta definicja definiuje rozmiar tego buforu znaków.

GX_ANIMATION_POOL_SIZE
- Wartość domyślna: 6.
- Opis: GUIX definiuje pulę animacji, z której struktury informacji o animacji mogą być dynamicznie przydzielane i zwracane przy użyciu gx_system_animation_get i gx_system_animation_free () interfejsów API. Ta definicja definiuje rozmiar tej puli blokowych kontrolek animacji.

GX_MOUSE_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: Ta definicja umożliwia obsługę danych wejściowych myszy. Mysz oprogramowania wymaga, aby sterownik ekranu narysować i śledzić wskaźnik myszy, który dodaje dodatkowe obciążenie do sterownika wyświetlania. Tę definicję należy zdefiniować tylko w przypadku, gdy mysz (a nie ekran dotykowy) musi być obsługiwana.

GX_HARDWARE_MOUSE_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: po zdefiniowaniu tej definicji sterownik wyświetlania GUIX wykorzystuje sprzętową obsługę rysowania kursora myszy. Zmniejsza to ilość pamięci wymaganej do przechwycenia pamięci kanwy poniżej kursora myszy i poprawia wydajność systemu dla tych docelowych sprzętowych obsługuje warstwę grafiki nakładki myszy.

GX_FONT_KERNING_SUPPORT
- Wartość domyślna: nie zdefiniowano.
- Opis: Ta definicja może być zdefiniowana w celu włączenia obsługi kerningu czcionek. Kerning czcionki pozwala zwiększyć odstępy między symbolami dla niektórych kombinacji glifów. Ta obsługa dodaje niewielką ilość obciążenia do funkcji rysowania ciągów czasu wykonywania, a ponadto dodaje niewielką ilość rozmiaru do struktur danych czcionki.

GX_WIDGET_USER_DATA
- Wartość domyślna: nie zdefiniowano.
- Opis: Jeśli jest zdefiniowany, spowoduje to dodanie pola danych zdefiniowanego przez użytkownika do bloku sterowania GX_WIDGET. To pole danych można przypisać za pomocą widoku właściwości w programie GUIX Studio. To pole danych jest ignorowane przez GUIX wewnętrznie, ale może być używane przez oprogramowanie aplikacji w wielu celach.

GUIX_5_4_0_COMPATIBILITY
- Wartość domyślna: nie zdefiniowano.
- Opis: Niektóre interfejsy API graficznego interfejsu użytkownika zostały zmodyfikowane po 5.4.0 wydania, aby dodać obsługę wyłączonych kolorów tekstu i poprawić dokładność niektórych funkcji matematycznych przy użyciu parametrów dopasowania ustalonego. Te zmiany czynią GUIX wersje biblioteki po 5.4.0 niezgodny z poprzednimi wersjami. Jednak przez włączenie tego #define biblioteka może być skompilowana w taki sposób, że interfejsy API w pełni zgodne z wersjami <= 5.4.0, co oznacza, że nie są konieczne żadne zmiany w istniejących aplikacjach do kompilowania przy użyciu najnowszej wersji biblioteki GUIX.

GX_MAX_STRING_LENGTH
- Wartość domyślna: 102400
- Opis: określa maksymalną długość ciągu, który jest używany do testowania nieprawidłowych ciągów. Jeśli ciąg wejściowy przekracza maksymalną długość ciągu, będzie uznawany za nieprawidłowy.