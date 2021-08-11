---
title: Dodatek F — usługi powiązań GUIX RTOS
description: Dowiedz się więcej o usługach powiązania GUIX RTOS.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7928e1781be03969de25901ebbe728e6554e96befb59c860f4ea53663c28932d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784601"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>Dodatek F — usługi powiązań GUIX RTOS

Interfejs GUIX wymaga usług wątków lub zadań, mutex, kolejki zdarzeń i usług chronometrażu oferowanych przez bazowy system RTOS. Domyślnie interfejs GUIX jest skonfigurowany do korzystania z systemu operacyjnego ThreadX w czasie rzeczywistym w celu świadczenia tych usług. Aby przeportować interfejs GUIX do innego systemu operacyjnego, deweloper powinien # zdefiniować dyrektywę preprocesorów GX_DISABLE_THREADX_BINDING i ponownie skompilować bibliotekę GUIX w celu usunięcia zależności ThreadX. Ponadto deweloper będzie musiał podać następujące definicje makr i funkcje dodatkowe. Przykłady tych definicji makr i funkcji wspierających można znaleźć w plikach gx_system_rtos_bind.h i gx_system_rtos_bind.c, które stanowią przykład ogólnej integracji rtos.

Makra integracji systemu:

**GX_RTOS_BINDING_INITIALIZE**

To makro jest wywoływane podczas inicjowania systemu. Należy zdefiniować makro, aby przed użyciem wywołać dowolną funkcję potrzebną do przygotowania usług systemowych lub zasobów rtos. Jest to możliwość powiązania w celu przygotowania zasobów rtos, z których będzie korzystać graficzny interfejs użytkownika.

**GX_SYSTEM_THREAD_START**

To makro jest wywoływane, gdy zadanie GUIX lub wątek powinien rozpocząć wykonywanie. To makro powinno być zdefiniowane w celu wywołania funkcji, która spowoduje uruchomienie wątku GUIX. Punkt wejścia do wątku GUIX jest przekazywany do wywoływanej funkcji. Podpis wywoływanej funkcji musi być

**UINT *function_name*(VOID (thread_entry_point)(VOID));**

Ta funkcja powinna zwrócić GX_SUCCESS, jeśli wątek został pomyślnie uruchomiony lub GX_FAILURE.

**GX_EVENT_PUSH**

To makro jest wywoływane w celu wypchania zdarzenia do kolejki zdarzeń FIFO używanej przez interfejs GUIX. Podczas przenoszenia do nowej kolejki zdarzeń odpowiadasz za zaimplementowanie tej kolejki zdarzeń w sposób bezpieczny wątkowo. GX_EVENT muszą zostać skopiowane do tej kolejki i skopiowane z tej kolejki, tzn. kolejka wskaźników GX_EVENT nie będzie działać, ponieważ zdarzenia GUIX mogą być zmiennymi automatycznymi z widoku producenta zdarzeń. Podpis funkcji wywoływanej przez to makro musi być:

**UINT *function_name* (GX_EVENT *event_ptr);**

Ta funkcja powinna zwrócić GX_SUCCESS, jeśli zdarzenie zostanie wypchniętą do kolejki zdarzeń. W przeciwnym razie powinna zwrócić GX_FAILURE.

**GX_EVENT_POP**

To makro jest wywoływane w celu usunięcia zdarzenia head (najstarsze) z kolejki zdarzeń GUIX i skopiowania go do żądanej lokalizacji. Ta funkcja musi mieć możliwość opcjonalnego blokowania lub oczekiwania na zdarzenie, jeśli żadne zdarzenia nie znajdują się obecnie w kolejce zdarzeń. Podpis funkcji wywoływanej przez to makro musi być

UINT function_name(GX_EVENT *put_event, GX_BOOL wait)

Jeśli parametr wait == GX_TRUE, funkcja nie powinna zwracać danych, dopóki nie zostanie podane zdarzenie. Jeśli parametr wait jest GX_FALSE, funkcja powinna zwracać natychmiast ze zdarzeniem lub bez niego.

Jeśli zdarzenie zostanie pobrane z kolejki, powinno zostać skopiowane do lokalizacji put_event, a zwracany stan to GX_SUCCESS. W przeciwnym razie powinien zostać zwrócony GX_FAILURE.

**GX_EVENT_FOLD**

To makro jest wywoływane przez interfejs GUIX w celu składania zdarzenia do kolejki zdarzeń FIFO. Składanie zdarzenia oznacza, że jeśli zdarzenie tego samego typu już istnieje w kolejce, ten wpis jest uaktualniany tak, aby zawierał ładunek nowego zdarzenia. Jeśli istniejące zdarzenie tego samego typu nie zostanie znalezione w kolejce, nowe zdarzenie zostanie wypchniętą do kolejki. 

W przypadku powiązań, które nie mogą implementować funkcji składania zdarzeń, dopuszczalne jest po prostu wywołanie GX_EVENT_PUSH.

**GX_TIMER_START**

To makro jest wywoływane, gdy interfejs GUIX musi odbierać okresowe dane wejściowe czasomierza. To makro powinno wywoływać usługę, która uruchamia okresową usługę czasomierza niskiego poziomu RTOS. Jeśli nie można łatwo zatrzymać i rozpocząć usługi czasomierza RTOS, akceptowalne jest, ale mniej wydajne pozostawienie tej usługi uruchomionej przez cały czas.

Gdy usługa czasomierza niskiego poziomu RTOS okresowo wygasa, powiązanie musi wywołać funkcję systemową GUIX _gx_system_timer_expiration(0); Okresowe wywoływanie tej funkcji jest elementem, który kieruje usługami czasomierza wysokiego poziomu dla czasomierza GUIX.

**GX_TIMER_STOP**

To makro jest wywoływane, gdy graficzny interfejs użytkownika nie wymaga już czasomierza okresowego (tzn. nie są uruchomione żadne aktywne czasomierze GUIX). Jeśli nie można łatwo zatrzymać i rozpocząć usługi czasomierza RTOS, akceptowalne jest, ale mniej wydajne pozostawienie tej usługi uruchomionej przez cały czas i zdefiniowanie tego makra, aby nic nie robiło.

**GX_SYSTEM_MUTEX_LOCK**

To makro jest wywoływane przez interfejs GUIX podczas krytycznych sekcji kodu, aby zapobiec przesłonieniu i zmodyfikowaniu wspólnych struktur danych przez inne zadanie, co potencjalnie może spowodować uszkodzenie. To makro powinno wywołać funkcję, która implementuje odpowiednią usługę blokowania zasobów RTOS.

Jeśli nigdy nie korzystasz z żadnych usług interfejsu API GUIX poza wątkiem GUIX, możesz zdefiniować to makro, aby nic nie robić.

**GX_SYSTEM_MUTEX_UNLOCK**

To makro jest wywoływane na końcu krytycznych sekcji kodu i powinno odblokować zasób GUIX przy użyciu odpowiedniej bazowej usługi RTOS. Jeśli nigdy nie korzystasz z żadnych usług interfejsu API GUIX poza wątkiem GUIX, możesz zdefiniować to makro, aby nic nie robić.

**GX_SYSTEM_TIME_GET**

To makro powinno wywołać funkcję, która zwraca bieżący czas systemowy "takty systemowe", czyli zwykle liczbę przerwań czasomierza niskiego poziomu, które wystąpiły od czasu uruchomienia systemu. Ta usługa jest używana do obliczania szybkości pióra zdarzeń dotykowych dla gestów wprowadzania dotykowego. Podpis funkcji wywoływanej przez to makro musi być:

**ULONG *function_name*(VOID);**

**GX_CURRENT_THREAD**

To makro jest wywoływane w celu zidentyfikowania aktualnie wykonywanego wątku. Usługa wywoływana przez to makro musi zwracać void *, co oznacza, że typ danych używany przez system operacyjny do identyfikowania bieżącego wątku wykonywania musi być rzutowany na void *, aby został zwrócony do GUX.

Kompletny przykład ogólnego powiązania RTOS jest implementowane w owych gx_system_rtos_bind.h i gx_system_rtos_bind.c