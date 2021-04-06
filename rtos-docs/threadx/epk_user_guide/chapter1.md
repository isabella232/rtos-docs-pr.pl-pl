---
title: Rozdział 1 — wprowadzenie do zestawu profilów wykonywania
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO ThreadX Execution profile Kit (EPK).
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30676437535229ad5bdbca10dcc9ca009d6e74
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377653"
---
# <a name="chapter-1--introduction-to-the-execution-profile-kit"></a>Rozdział 1 wprowadzenie do zestawu profilów wykonywania

Zestaw profilów wykonywania ThreadX (EPK) oferuje infrastrukturę aplikacji do dynamicznego śledzenia czasu wykonywania wątków, procedur usługi przerwania (procedury ISR) i bezczynnych warunków systemu. Jest to szczególnie przydatne w przypadku optymalizacji i dostrajania aplikacji pod kątem maksymalnej wydajności. Jest to jednak również cenna pomoc w debugowaniu.

EPK zależy od \" punktów zaczepienia \" wbudowanych w logikę planowania ThreadX w kodzie zestawu, który jest wywoływany przy wpisie wątku, zamknięciu wątku, wpisie ISR i wyjściu do procedury ISR. Procedury EPK obliczają czas między takimi zdarzeniami i przechowują czas Delta w zmiennych globalnych, jak również elementy członkowskie bloku sterowania **TX_THREAD** .

> [!NOTE]
> *Deweloper może modyfikować lub nawet zamieniać te funkcje haka na własne, aby przełączać numery PIN we/wy w celu zapewnienia widoczności sprzętowej działającej aplikacji ThreadX*.

## 

## <a name="epk-requirements"></a>Wymagania EPK

EPK wymaga ThreadX 6,0 (lub więcej) do działania. EPK wymaga również \" rozsądnej \" rozdzielczości, zwiększając czas sprzętowy źródła. Najbardziej rozsądne rozwiązanie zwykle będzie coś w skali mikrosekundowych. Jeśli rozwiązanie jest zbyt duże, liczniki EPK będą zbyt szybko maksymalne. Z drugiej strony, jeśli rozwiązanie jest zbyt małe, dokładne chronometraże nie jest możliwe. Źródło czasu aplikacji jest zdefiniowane w ***tx_execution_profile. h** _ przez makro _ * TX_EXECUTION_TIME_SOURCE * *.

Kompilator języka C musi obsługiwać typ \" unsigned long long \" for unsigned 64-bit Total Counters. Ponadto EPK zakłada, że zmienne globalne są inicjowane przez kod uruchamiania kompilatora w czasie wykonywania. Jeśli tak się nie dzieje, zmienne globalne zdefiniowane w ***tx_execution_profile. c*** muszą być zainicjowane do 0 przez aplikację.

## <a name="epk-installation"></a>Instalacja EPK

Aby zainstalować ThreadX EPK, wykonaj poniższe kroki i ponownie skompiluj całą bibliotekę ThreadX i aplikację.

1. Uwzględnij pliki źródłowe EPK (***tx_execution_profile. h** _ i _*_tx_execution_profile. c_*_) w projekcie kompilacji biblioteki ThreadX. Te pliki mogą znajdować się w [repozytorium usługi Azure RTO ThreadX](<https://github.com/azure-rtos/threadx>) w folderze _ *_Utility/Execution_Profile_**).

1. W ***tx_port. h** _ Zdefiniuj makro _ *TX_THREAD_EXTENSION_3** w następujący sposób.
```
    #define TX_THREAD_EXTENSION_3 unsigned long long tx_thread_execution_time_total; \
    unsigned long tx_thread_execution_time_last_start;
```

3. Zdefiniuj makro **TX_EXECUTION_TIME_SOURCE** w **_tx_execution_profile. h_** , aby mapować do źródła czasu sprzętowego.

1. Upewnij się, że środowisko kompilacji definiuje **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** , dzięki czemu punkty zaczepienia planowania są wywoływane z kodu zestawu ThreadX.

1. Jeśli chcesz użyć 64-bitowego źródła czasu, przejrzyj plik ***tx_execution_profile. h*** , aby uzyskać instrukcje dotyczące sposobu jego wykonania.

1. Skompiluj ponownie całą bibliotekę i aplikację, tak aby wszystkie te opcje zostały prawidłowo skompilowane.

Teraz możesz przystąpić do używania EPK z aplikacją.

##  <a name="epk-example"></a>Przykład EPK 

Poniżej znajduje się przykład EPK używany w standardowej demonstracji ThreadX skonfigurowany przy użyciu 32-bitowego źródła czasomierza, które zwiększa 7,2 razy na mikrosekundowych. 

Makro **TX_EXECUTION_TIME_SOURCE** zostało zdefiniowane w celu pobrania rejestru czasomierza zamapowanego na pamięć w 0xE0001004, jak pokazano poniżej.
```
(EXECUTION_TIME_SOURCE_TYPE) \*((ULONG \*) 0xE0001004)
```

Umożliwienie pokazania przebiegu przez pięć sekund daje następujące wyniki.

![Wyniki umożliwiające uruchomienie demonstracji.](media/demo_results.png)

Ponieważ standardowa Demonstracja ThreadX nie ma czasu bezczynności (wątki 1 i 2 działają w sposób ciągły), EPK prawidłowo zgłasza zero jako czas bezczynności. Łączny czas i wartości wątku ISR mogą być podzielone przez 7,2 w celu uzyskania mikrosekund dla każdej kategorii wykonania. EPK udostępnia również interfejsy API umożliwiające dostęp do tych informacji (zobacz [rozdział 2](chapter2.md)).