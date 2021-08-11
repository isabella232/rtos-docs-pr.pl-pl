---
title: Rozdział 4 — Azure RTOS wydajności traceX
description: W tym rozdziale opisano Azure RTOS do analizy wydajności narzędzia TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 719f27ef54091e2db9eefa982ce0c27561079b5b3a254d3fd09cc46d8f66f252
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788641"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a>Rozdział 4 — Azure RTOS wydajności traceX

W tym rozdziale opisano Azure RTOS do analizy wydajności narzędzia TraceX:

## <a name="performance-analysis"></a>Analiza wydajności

TraceX zapewnia wbudowaną analizę wydajności plików śledzenia. Informacje takie *jak* profil *wykonywania,* popularne *usługi,* użycie stosu wątków i różne statystyki *wydajności,* w tym statystyki FileX i NetX, są łatwo dostępne. Te informacje są dostępne za pośrednictwem ***elementu*** menu Widok. 


## <a name="execution-profile"></a>Profil wykonywania

Wybranie przycisku ***Wygeneruj** profil wykonania _ lub _*_Wyświetl profil wykonania_*_ powoduje wyświetlenie profilu wykonywania TraceX dla aktualnie załadowanego pliku śledzenia. Profil wykonywania skojarzony z przykładowym śladem pokazu ThreadX jest wyświetlany na rysunku _*Rysunek 19**.

![Zrzut ekranu przedstawiający profil wykonywania skojarzony z przykładowym śladem pokazu ThreadX.](./media/user-guide/execution_profile.png)

**RYSUNEK 19**

Przykład przedstawiony na rysunku **19** wskazuje, że prawie 45% czasu przetwarzania znajduje się wewnątrz wątku 2 _, a prawie 51% czasu przetwarzania znajduje się wewnątrz ***wątku _thread*_1._** Jest to logiczne, ponieważ większość śledzenia pokazuje te wątki wysyłające i odbierające komunikaty. W tym przykładzie pozostałe konteksty wykonywania mają tylko niewielką ilość czasu wykonywania.

## <a name="popular-services"></a>Popularne usługi

Wybranie opcji ***View ->Popularne usługi** _ wyświetla popularne usługi w aktualnie załadowanym pliku śledzenia. Domyślnie te informacje są wyświetlane dla całego systemu. Dostępne są jednak również popularne usługi dla określonych wątków. Popularne usługi w przykładowym śladzie pokazu ThreadX przedstawiono na rysunku _*Rysunek 20**.

![Zrzut ekranu przedstawiający popularne usługi w przykładowym śladzie pokazu ThreadX.](./media/user-guide/popular_services.png)

**RYSUNEK 20**

Przykład przedstawiony na rysunku **20** wskazuje, że tx_queue_send _ i ***_*_tx_queue_receive_** to dwie najpopularniejsze usługi w tym śladzie. Jest to zgodne z zachowaniem standardowej demonstracji ThreadX, z której został przechwycony ten ślad.

Do tej analizy można wybrać konkretne wątki, korzystając z listy rozwijanej w górnej części tego okna. **Rysunek 21 przedstawia** tę analizę dla **_wątku 3._**

![Zrzut ekranu przedstawiający analizę popularnych usług TraceX.](./media/user-guide/popular_services_thread3.png)

**RYSUNEK 21**

## <a name="thread-stack-usage-analysis-for-thread-3"></a>Użycie stosu wątków ![Analiza wątku 3.](./media/user-guide/screen_shot_17.png)

Wybranie przycisku ***Wygeneruj** użycie stosu wątku _ lub _*_Wyświetl -> użycie_*_ stosu wątków powoduje wyświetlenie użycia stosu dla każdego wątku w pliku śledzenia. Jest to realizowane przez ThreadX, w tym bieżący wskaźnik stosu wątku w wielu wpisach śledzenia w pliku. Użycie stosu na poziomie 100% wskazuje, że stos został przepełniony i musi zostać poprawiony w aplikacji. Jeśli w tym pliku śledzenia nie ma wykonywania wątku, użycie stosu dla tego wątku jest wyświetlane na poziomie 0%. Użycie stosu wątków w przykładowym śladzie pokazu ThreadX jest pokazane na rysunku _*Rysunek 22**.

![Zrzut ekranu przedstawiający użycie stosu wątków TraceX.](./media/user-guide/thread_stack_usage.png)

**RYSUNEK 22**

Przykład przedstawiony na rysunku **22** wskazuje, że większość wątków w tym śladzie ma od 9% do 12% użycia stosu.

## <a name="performance-statistics"></a>Statystyka wydajności

Wybranie przycisku ***Generuj** statystyki wydajności _ lub _ *_Widok -> Statystyka_* wydajności * powoduje wyświetlenie statystyk wydajności aktualnie załadowanego pliku śledzenia. Domyślnie te informacje są wyświetlane dla całego systemu. Jednak statystyki wydajności są również dostępne dla każdego konkretnego wątku.

Statystyki wydajności przykładowego śledzenia pokazu ThreadX przedstawiono na rysunku **23.**

![Zrzut ekranu przedstawiający statystyki wydajności traceX.](./media/user-guide/performance_statistics.png)

**RYSUNEK 23**

Przykład przedstawiony na rysunku **23** wskazuje, że w tym pliku śledzenia znajduje się 18 przełączników kontekstowych, a także pięć wywłaszków wątków, 16 zawieszenia wątków, 19 wznowień wątków i trzy przerwania. W tym pliku śledzenia nie znaleziono żadnych wywłaszczeń priorytetów. Zwróć uwagę na dwie kategorie inwersji priorytetów: *deterministyczną* i *niedeterministyczną*. Deterministyczne wywłaszczenia priorytetu to odwrócenie priorytetu, w którym wątek jest blokowany w węzłem mutex należącym do wątku o niższym priorytecie. Niedeterministyczna odwrócenie priorytetu to miejsce, w którym inny wątek o niższym priorytecie jest uruchamiany podczas inwersji priorytetu deterministycznego. Późniejsze mogą spowodować nieprzewidziane zachowanie chronometrażu w aplikacji i należy je dokładnie zbadać.

## <a name="filex-statistics"></a>Statystyka FileX

Wybranie ***Widok -> Statystyka FileX** _ przedstawia statystykę wydajności FileX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu na wszystkich otwartych . /media objects. Statystyki wydajności przykładowego śledzenia pokazu FileX są wyświetlane na rysunku _*Rysunek 24**.

![Zrzut ekranu przedstawiający statystyki pliku FileX.](./media/user-guide/filex_statistics.png)

**RYSUNEK 24**

Przykład przedstawiony na rysunku **27** wskazuje, że istnieje 19 .. Zostanie otwarte okno /media, 19 .. /media closes, 19 .. /media flushes, 18 odczytów katalogu, 19 zapisu w katalogu i 18 chybień pamięci podręcznej katalogów. Informacje dodatkowe można wyświetlić, przewijając w dół w oknie statystyk.

## <a name="netx-statistics"></a>Statystyka NetX

Wybranie opcji ***Wyświetl statystyki -NetX** _ przedstawia statystyki wydajności NetX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu. Statystyki wydajności przykładowego śledzenia pokazu NetX są wyświetlane na rysunku _*Rysunek 25**.

![Zrzut ekranu przedstawiający statystykę NetX.](./media/user-guide/netx_statistics.png)

**RYSUNEK 25**

Przykład przedstawiony na rysunku **25** wskazuje, że nie było żadnych zdarzeń ARP, Ping ani UDP, ale wysłano 30 pakietów IP, wysłano 1368 bajtów IP, odebrano 30 pakietów IP i odebrano 1360 bajtów adresów IP.

## <a name="trace-file-information"></a>Informacje o pliku śledzenia

Wybranie opcji ***View -> Trace File Information** _ (Wyświetl — informacje o pliku śledzenia) zawiera podstawowe informacje dotyczące otwartego pliku śledzenia. Te informacje obejmują kolejność bajtów pliku, rozmiar źródła czasu, maksymalną liczbę bajtów dla każdej nazwy obiektu i podstawowy adres wszystkich wskaźników pliku śledzenia. _ *Rysunek 26** przedstawia informacje o pliku śledzenia dla standardowego **_demo_threadx.trx_** śledzenia.

![Zrzut ekranu przedstawiający informacje o pliku TraceX.](./media/user-guide/trace_file_info.png)

**RYSUNEK 26**

## <a name="raw-trace-dump"></a>Nieprzetworzone zrzuty śledzenia

Wybranie opcji ***Widok -> zrzutu** śledzenia _ wyświetla okno dialogowe z nazwą pliku zawierającego nieprzetworzone zrzuty śledzenia. Po wprowadzeniu nazwy pliku i ścieżki traceX tworzy nieprzetworzone pliki śledzenia _*_w formacie_*_ tekstowym i uruchamianotepad.exe, aby go wyświetlić. _ *Rysunek 27** przedstawia nieprzetworzone zrzutu pliku śledzenia dla standardowego **_demo_threadx.trx_** śledzenia.

![Zrzut ekranu przedstawiający zrzut śledzenia nieprzetworzone.](./media/user-guide/raw_trace_dump.png)

**RYSUNEK 27**
