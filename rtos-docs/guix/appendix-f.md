---
title: Dodatek F-GUIX RTO Binding Services
description: Dowiedz się więcej na temat usług powiązań GUIX RTO.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d94dbb9d7d53ec3e1900188142974cc981dfea9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823173"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>Dodatek F-GUIX RTO Binding Services

GUIX wymaga usług wątków lub zadań, obiektu mutex, kolejki zdarzeń i usługi chronometrażu dostarczanych przez bazowe RTO. Domyślnie GUIX jest skonfigurowany do korzystania z systemu operacyjnego ThreadX w czasie rzeczywistym w celu świadczenia tych usług. Aby przenieść GUIX do innego systemu operacyjnego, deweloper powinien # zdefiniować dyrektywę preprocesora GX_DISABLE_THREADX_BINDING i ponownie skompilować bibliotekę GUIX, aby usunąć zależności ThreadX. Ponadto Deweloper musi dostarczyć następujące definicje makr i funkcje pomocnicze. Przykłady tych definicji makr i funkcji pomocniczych można znaleźć w plikach gx_system_rtos_bind. h i gx_system_rtos_bind. c, które zapewniają przykładową rtoą integrację.

Makra integracji systemu:

**GX_RTOS_BINDING_INITIALIZE**

To makro jest wywoływane podczas inicjowania systemu. Makro należy zdefiniować, aby wywołać dowolną funkcję potrzebną do przygotowania usług systemu RTO lub zasobów RTO przed użyciem. Jest to powiązanie umożliwiające przygotowanie zasobów RTO, które będą używane przez GUIX.

**GX_SYSTEM_THREAD_START**

To makro jest wywoływane, gdy zostanie rozpoczęte wykonywanie zadania lub wątku GUIX. To makro należy zdefiniować, aby wywołać funkcję, która uruchomi wątek GUIX uruchomiony. Punkt wejścia do wątku GUIX jest przesyłany do wywołanej funkcji. Sygnatura wywołanej funkcji musi być

**UINT *function_name*(void (thread_entry_point) (void));**

Ta funkcja powinna zwracać GX_SUCCESS, jeśli wątek został pomyślnie uruchomiony lub GX_FAILURE.

**GX_EVENT_PUSH**

To makro jest wywoływane w celu wypchnięcia zdarzenia do kolejki zdarzeń FIFO używanej przez GUIX. W przypadku przenoszenia do nowego rtoa jest odpowiedzialna za wdrożenie tej kolejki zdarzeń w sposób bezpieczny dla wątków. Struktury GX_EVENT muszą być skopiowane do tej kolejki i skopiowane z tej kolejki, czyli kolejki wskaźników GX_EVENT nie będą działać, ponieważ zdarzenia GUIX mogą być automatycznie zmiennymi z widoku producenta zdarzeń. Sygnatura funkcji wywoływanej przez to makro musi być:

**UINT *function_name* (GX_EVENT *event_ptr);**

Ta funkcja powinna zwracać GX_SUCCESS, jeśli zdarzenie jest wypychane do kolejki zdarzeń, w przeciwnym razie powinna zwracać GX_FAILURE.

**GX_EVENT_POP**

To makro jest wywoływane, aby usunąć zdarzenie głowy (najstarsze) z kolejki zdarzeń GUIX i skopiować je do wybranej lokalizacji. Ta funkcja musi mieć możliwość opcjonalnego blokowania lub oczekiwania na zdarzenie, jeśli w kolejce zdarzeń nie ma żadnych zdarzeń. Sygnatura funkcji wywoływanej przez to makro musi być

UINT function_name (GX_EVENT * put_event, GX_BOOL oczekiwanie)

Jeśli parametr wait = = GX_TRUE, funkcja nie powinna zostać zwrócona, dopóki nie zostanie dostarczone zdarzenie. Jeśli parametr wait jest GX_FALSE, funkcja powinna zwrócić bezpośrednio z lub bez zdarzenia.

Jeśli zdarzenie jest pobierane z kolejki, powinno zostać skopiowane do lokalizacji put_event, a stan powrotu to GX_SUCCESS. W przeciwnym razie stan powrotu powinien być GX_FAILURE.

**GX_EVENT_FOLD**

To makro jest wywoływane przez GUIX w celu złożenia zdarzenia w kolejce zdarzeń FIFO. Złożenia zdarzenia oznacza, że jeśli zdarzenie tego samego typu już istnieje w kolejce, ten wpis jest aktualizowany, aby zawierał ładunek nowego zdarzenia. Jeśli istniejące zdarzenie tego samego typu nie zostanie odnalezione w kolejce, nowe zdarzenie jest wypychane do kolejki. 

W przypadku powiązań, które nie mogą implementować funkcji składania zdarzeń, można po prostu wywołać GX_EVENT_PUSH.

**GX_TIMER_START**

To makro jest wywoływane, gdy GUIX musi odbierać okresowe dane wejściowe czasomierza. To makro powinno wywołać usługę, która uruchamia usługę czasomierza okresowego RTO niskiego poziomu. Jeśli usługa czasomierza RTO nie może być łatwo zatrzymywana i uruchomiona, jest akceptowalna, ale mniej wydajna w przypadku pozostawienia tej usługi przez cały czas.

Gdy usługa czasomierza RTO niskiego poziomu okresowo wygasa, powiązanie musi wywołać funkcję systemu GUIX _gx_system_timer_expiration (0); Okresowe wywoływanie tej funkcji polega na tym, co jest dyskiem usługi czasomierza widżetu GUIX wysokiego poziomu.

**GX_TIMER_STOP**

To makro jest wywoływane, gdy GUIX nie potrzebuje już czasomierza okresowego (tj. nie ma aktywnych czasomierzy GUIX uruchomionych). Jeśli usługa czasomierza RTO nie może być łatwo zatrzymywana i uruchomiona, jest akceptowalna, ale mniej wydajna, aby pozostawić tę usługę przez cały czas i zdefiniować to makro, aby nic nie robić.

**GX_SYSTEM_MUTEX_LOCK**

To makro jest wywoływane przez GUIX podczas krytycznych sekcji kodu, aby zapobiec wystąpieniu innego zadania sprzed Empting i modyfikacji wspólnych struktur danych, co może spowodować uszkodzenie. To makro powinno wywołać funkcję implementującą odpowiednią usługę blokowania zasobów RTO.

Jeśli nie korzystasz z żadnych usług interfejsu API GUIX poza wątkiem GUIX, możesz zdefiniować to makro, aby nic nie robić.

**GX_SYSTEM_MUTEX_UNLOCK**

To makro jest wywoływane na końcu krytycznych sekcji kodu i należy odblokować zasób GUIX przy użyciu odpowiedniej usługi RTO. Jeśli nie korzystasz z żadnych usług interfejsu API GUIX poza wątkiem GUIX, możesz zdefiniować to makro, aby nic nie robić.

**GX_SYSTEM_TIME_GET**

To makro powinno wywołać funkcję, która zwraca bieżący czas systemowy to "cykle systemu", która zazwyczaj jest liczbą przerwań czasomierza niskiego poziomu, które wystąpiły od momentu uruchomienia systemu. Ta usługa służy do obliczania szybkości pióra zdarzeń dotykowych dla gestów wprowadzania dotykowego. Sygnatura funkcji wywoływanej przez to makro musi być:

**ULONG *function_name*(void);**

**GX_CURRENT_THREAD**

To makro jest wywoływane, aby zidentyfikować aktualnie wykonywany wątek. Usługa wywołana przez to makro musi zwrócić wartość void *, co oznacza, że typ danych używany przez system operacyjny do identyfikowania bieżącego wątku wykonywania musi być rzutowany na wartość typu void *, aby można było zwrócić do GUX.

Kompletny przykład ogólnego powiązania RTO jest implementowany w zachowanych gx_system_rtos_bind. h i gx_system_rtos_bind. c