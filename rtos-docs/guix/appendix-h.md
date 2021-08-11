---
title: Dodatek H — flagi konfiguracji Build-Time GUIX
description: Dowiedz się więcej o flagach konfiguracji czasu kompilacji GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ecd4d86fbc6fb1ebaa002675e66492758edaf14ed90aa03fc9f4cf4abb87e661
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784210"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>Dodatek H — flagi konfiguracji Build-Time GUIX

Interfejs GUIX obsługuje kilka opcji kompilacji warunkowej i wartości konfiguracji. Domyślne ustawienie tych wartości warunkowych i konfiguracyjnych można przesłonić, wstępnie definiując wartość w pliku nagłówka gx_user.h lub w wierszu polecenia kompilatora.

**GX_DISABLE_THREADX_BINDING**
- Ustawienie domyślne: Niezdefiniowane
- Opis: Ten warunek może służyć do wyłączania domyślnego powiązania ThreadX RTOS. Jeśli chcesz uruchomić interfejs GUIX z systemem RTOS innym niż ThreadX, musisz #define GX_DISABLE_THREADX_BINDING i udostępnić własne usługi powiązań RTOS.

GX_SYSTEM_TIMER_MS
- Wartość domyślna: 20
- Opis: Ta wartość definiuje żądany interwał lub dokładność czasomierza GUIX.

TX_TIMER_TICKS_PER_SECOND
- Wartość domyślna: 100
- Opis: ta wartość definiuje liczbę częstotliwości przerwań czasomierza TX. Ponieważ domyślny czasomierz interwału ThreadX to 10 ms, wartość domyślna to częstotliwość 100 Hz.

GX_DISABLE_MULTITHREAD_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano
- Opis: Tego warunkowego czasu kompilacji można użyć, aby wyłączyć obsługę interfejsu API GUIX dla wielu wątków jednocześnie wywołania interfejsu API GUIX. Jeśli tylko jeden wątek aplikacji będzie kiedykolwiek korzystać z interfejsu API GUIX, należy zdefiniować tę flagę, aby zmniejszyć obciążenie systemu związane z ochroną krytycznych sekcji kodu.

GX_DISABLE_UTF8_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Tego warunkowego czasu kompilacji można użyć do usunięcia wewnętrznej obsługi guix kodowania ciągów formatu UTF8. Jeśli w aplikacji używasz tylko wartości znaków M-0xff, włączenie tej funkcji #define zmniejszy rozmiar kodu i zmniejszy obciążenie związane z obsługą kodowania ciągów w formacie UTF8.

GX_DISABLE_ARC_DRAWING_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Ten warunek może służyć do zmniejszenia rozmiaru kodu biblioteki GUIX i rozmiaru struktury GX_DISPLAY przez usunięcie obsługi okręgu funkcji rysowania arcy, łuku, koła i wielokropka. Te funkcje nie są wymagane przez domyślny zestaw widżetów GUIX.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Ten warunek można zdefiniować w celu usunięcia obsługi dekodowania oprogramowania JPEG i PNG w środowisku uruchomieniowym biblioteki GUIX. Jeśli aplikacja nie wymaga dekodowania plików jpg lub png w środowisku uruchomieniowym, co oznacza, że aplikacja nie używa map pikseli w formacie RAW tworzonych przez program Studio i nie odczytuje plików obrazów z zewnętrznego systemu plików, możesz włączyć tę #define, aby zmniejszyć rozmiar biblioteki GUIX.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano
- Opis: Ten warunek może służyć do usuwania obsługi biblioteki GUIX na temat ładowania danych zasobów binarnych. Zasoby binarne mogą służyć do powiązania środowiska uruchomieniowego danych zasobów za pomocą aplikacji GUIX. Jeśli używasz tylko plików zasobów w formacie kodu źródłowego C, możesz zdefiniować ten warunek, aby zmniejszyć rozmiar biblioteki GUIX.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: W przypadku korzystania z 16 bpp i wyższych głębokości kolorów interfejs GUIX opcjonalnie obsługuje rysowanie grafiki nie arc, map pikseli i czcionek z wartością alfa zdefiniowaną przez pędzl kontekstowy do rysowania. Obsługa tego trybu rysowania wprowadza niewielkie obciążenie środowiska uruchomieniowego i zwiększa rozmiar biblioteki, co można wyeliminować przez zdefiniowanie tej flagi, jeśli nie wymaga się obsługi mieszania alfa. Pamiętaj, że mapy pikseli z kanałem alfa, czcionkami anty aliasami i innymi trybami rysowania anty aliasów są nadal obsługiwane niezależnie od tego ustawienia warunkowego.

GX_DISABLE_THREADX_TIMER_SOURCE
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Ten warunek może służyć do wyłączania źródła czasomierza ThreadX. Należy zdefiniować GX_DISABLE_THREADX_TIMER_SOURCE, jeśli chcesz użyć innego źródła czasomierza.

GX_REPEAT_BUTTON_INITIAL_TICS
- Wartość domyślna: 10.
- Opis: Jeśli przycisk ma styl GX_STYLE_BUTTON_REPEAT, ta wartość określa, jak długo przycisk czeka przed rozpoczęciem wysyłania powtarzanych GX_EVENT_CLICKED zdarzeń.

GX_MAX_QUEUE_EVENTS
- Wartość domyślna: 48.
- Opis: definiuje rozmiar kolejki zdarzeń GUIX w jednostkach wpisów struktury zdarzeń. W przypadku przepełnienia kolejki zdarzeń zdarzenia wypychane do kolejki są odrzucane, a GX_SYSTEM_ERROR zwracane przez funkcję gx_system_event_send().

GX_MAX_DIRTY_AREAS
- Wartość domyślna: 64.
- Opis: definiuje maksymalną liczbę unikatowych, zanieczyszczonych wpisów listy, które mogą być utrzymywane przez jedną kanwę. Gdy zanieczyszczona lista przepełnia się, guix domyślnie oznacza okno główne kanwy jako zanieczyszczone, co jest mniej wydajne niż rysowanie poszczególnych widżetów podrzędnych.

GX_MAX_CONTEXT_NESTING
- Wartość domyślna: 8.
- Opis: definiuje maksymalne zagnieżdżanie stosu kontekstu rysowania. Jest to odpowiednik maksymalnego zagnieżdżania widżetów nadrzędny/podrzędny/podrzędny/podrzędny w definicji interfejsu użytkownika.

GX_MAX_INPUT_CAPTURE_NESTING
- Wartość domyślna: 4.
- Opis: definiuje rozmiar stosu używanego do obsługi listy widżetów, które przechwytują dane wejściowe użytkownika (mysz i klawiatura).

GX_SYSTEM_THREAD_PRIORITY
- Wartość domyślna: 16.
- Opis: definiuje priorytet wątku GUIX utworzonego podczas gx_system_initialize().

GX_SYSTEM_THREAD_TIMESLICE
- Wartość domyślna: 10.
- Opis: definiuje czasomierz GUIX w kontekście taktówek czasomierza RTOS. Jeśli inne wątki są zdefiniowane z tym samym priorytetem co wątek GUIX, ta wartość określa, jak często konkurujące wątki mają kontrolę procesora CPU.

GX_CURSOR_BLINK_INTERVAL
- Wartość domyślna: 20.
- Opis: definiuje szybkość migania kursora wejściowego dla widżetów wprowadzania tekstu. Ta wartość jest określana jako takty czasomierza GUIX, która domyślnie jest zdefiniowana jako 50 ms, więc wartość 20 wskazuje, że kursor wejściowy miga raz na sekundę.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- Wartość domyślna: 32.
- Opis: definiuje rozmiar pamięci podręcznej indeksu list-start utrzymywanej przez wielo wierszowy widok tekstowy i wielo wierszowe widżety wprowadzania tekstu. Ta pamięć podręczna służy do szybkiego przewijania w pionie widżetów tekstowych z wieloma wierszami. Aby uzyskać najlepszą wydajność, rozmiar pamięci podręcznej powinien być większy niż liczba widocznych wierszy największego widżetu tekstu wielo wierszowego zdefiniowanego przez aplikację. Jeśli na przykład najbardziej widoczne wiersze dla dowolnego widżetu tekstu to 20 wierszy, aplikacja może zdefiniować rozmiar pamięci podręcznej 32 (wartość domyślna), co umożliwia guix przewijanie w pionie bez ponownego obliczania wszystkich indeksów uruchamiania wiersza.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- Wartość domyślna: 4.
- Opis: Blok sterujący wielo wierszowego przycisku tekstowego utrzymuje wskaźnik do każdego wiersza tekstu, który ma być wyświetlany przez przycisk. Ta wartość określa liczbę wskaźników tekstowych wymaganych przez przycisk tekstu wielo wierszowego najgorszego przypadku.

GX_POLYGON_MAX_EDGE_NUM
- Wartość domyślna: 10.
- Opis: Ta wartość określa najbardziej złożony wielokąt, który może być rysowany przez GUIX. Algorytm rysowania wielokątów określa linie potrzebne do zdefiniowania krawędzi wielokąta, a ta definicja definiuje maksymalną liczbę obsługiwanych krawędzi.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- Wartość domyślna: 16.
- Opis: W przypadku kółka przewijania liczby widżet kółka przewijania konwertuje wartości całkowite na ciągi ascii. Ta wartość określa maksymalną długość ciągu wymaganego do wyświetlenia przypisanych wartości całkowitych.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- Wartość domyślna: 5.
- Opis: definiuje liczbę znaczników czasomierza GUIX (50 ms) między aktualizacjami okrągłych mierników skonfigurowanych do animowania ruchu wskaźnika od ostatniej do bieżącej pozycji kątowej.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- Wartość domyślna: 16.
- Opis: Monit liczbowy przydziela bufor w celu przekonwertowania wartości całkowitej przypisanej do monitu na ciąg ascii. Ta definicja definiuje rozmiar tego buforu znaków.

GX_ANIMATION_POOL_SIZE
- Wartość domyślna: 6.
- Opis: GUIX definiuje pulę animacji, z której struktury informacji animacji mogą być dynamicznie przydzielane i zwracane przy użyciu interfejsów API gx_system_animation_get i gx_system_animation_free(). Ta definicja definiuje rozmiar tej puli bloków sterujących animacją.

GX_MOUSE_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Ta definicja umożliwia obsługę danych wejściowych myszy. Mysz programowa wymaga, aby sterownik wyświetlania narysować i śledzić kursor myszy, co zwiększa dodatkowe obciążenie sterownika wyświetlania. Tę definicję należy zdefiniować tylko wtedy, gdy musi być obsługiwana mysz (nie ekran dotykowy).

GX_HARDWARE_MOUSE_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Po zdefiniowaniu tej definicji sterownik wyświetlania GUIX korzysta ze sprzętowej obsługi rysowania kursorem myszy. Zmniejsza to ilość pamięci wymaganej do przechwycenia pamięci kanwy pod kursorem myszy i poprawia wydajność systemu dla tych celów sprzętowych obsługuje warstwę grafiki nakładek myszy.

GX_FONT_KERNING_SUPPORT
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: tę definicję można zdefiniować, aby włączyć obsługę kerningu czcionek. Kerning czcionki poprawia odstępy między symbolami dla niektórych kombinacji symbolu. Ta obsługa powoduje dodanie niewielkiego obciążenia do funkcji rysowania ciągów w czasie wykonywania, a także niewielkie rozmiary struktur danych czcionek.

GX_WIDGET_USER_DATA
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Jeśli jest zdefiniowana, powoduje to dodanie pola danych zdefiniowanego przez użytkownika do GX_WIDGET kontroli. To pole danych można przypisać przy użyciu widoku właściwości w programie GUIX Studio. To pole danych jest ignorowane wewnętrznie przez graficzny interfejs użytkownika, ale może być używane przez oprogramowanie aplikacji do wielu celów.

GUIX_5_4_0_COMPATIBILITY
- Ustawienie domyślne: Nie zdefiniowano.
- Opis: Niektóre interfejsy API graficznego interfejsu użytkownika zostały zmodyfikowane po wydaniu wersji 5.4.0 w celu dodania obsługi wyłączonych kolorów tekstu i zwiększenia dokładności niektórych funkcji matematycznych przy użyciu parametrów dopasowania punktu stałego. Te zmiany sprawiają, że wydania biblioteki GUIX po wersji 5.4.0 są niezgodne z poprzednimi wersjami. Jednak włączając tę bibliotekę #define, można skompilować bibliotekę w taki sposób, aby interfejsy API były w pełni zgodne z wersjami <= 5.4.0, co oznacza, że żadne zmiany nie są wymagane w istniejących aplikacjach do kompilacji z najnowszą biblioteką GUIX.

GX_MAX_STRING_LENGTH
- Ustawienie domyślne: 102400
- Opis: definiuje maksymalną długość ciągu, który jest używany do testowania nieprawidłowych ciągów. Jeśli ciąg wejściowy przekracza maksymalną długość ciągu, będzie on uważany za nieprawidłowy.