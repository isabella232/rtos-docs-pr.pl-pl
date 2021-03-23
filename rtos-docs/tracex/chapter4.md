---
title: Rozdział 4 — Analiza wydajności usługi Azure RTO TraceX
description: W tym rozdziale opisano narzędzie analiza wydajności usługi Azure RTO TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823442"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a>Rozdział 4 — Analiza wydajności usługi Azure RTO TraceX

W tym rozdziale opisano narzędzie analiza wydajności usługi Azure RTO TraceX:

## <a name="performance-analysis"></a>Analiza wydajności

TraceX zapewnia wbudowaną analizę wydajności plików śledzenia. Informacje takie jak *profil wykonywania*, *popularne usługi*, *użycie stosu wątków* i różne *statystyki wydajności, w* tym statystyki FileX i NetX *,* są łatwo dostępne. Te informacje są dostępne za pośrednictwem elementu menu ***Widok*** . 


## <a name="execution-profile"></a>Profil wykonywania

Wybranie przycisku ***Generuj profil wykonywania** _ lub _*_profilu wykonywania widoku_*_ przedstawia profil wykonywania TraceX dla aktualnie załadowanego pliku śledzenia. Profil wykonywania skojarzony z przykładowym śladem demonstracyjnym ThreadX jest wyświetlany w _ * rysunek 19 * *.

![Zrzut ekranu przedstawiający profil wykonywania skojarzony z przykładowym śladem demonstracyjnym ThreadX.](./media/user-guide/execution_profile.png)

**RYSUNEK 19.**

Przykład przedstawiony na **rysunku 19** wskazuje, że niemal 45% czasu przetwarzania należy do **_wątku 2_*_, a niemal 51% czasu przetwarzania jest wewnątrz wątku _*_1_** jest to wartość logiczna od momentu, gdy dane śledzenia przedstawiają te wątki wysyłające i otrzymujące komunikaty. W tym przykładzie w pozostałym kontekście wykonania znajduje się tylko niewielki czas wykonania.

## <a name="popular-services"></a>Popularne usługi

Wybranie pozycji ***wyświetl >popularne usługi** _ prezentuje popularne usługi w aktualnie załadowanym pliku śledzenia. Domyślnie te informacje są wyświetlane dla całego systemu. Jednak dostępne są również popularne usługi dla określonych wątków. Popularne usługi w przykładowym śladzie demonstracyjnej ThreadX są wyświetlane w _ * rysunek 20 * *.

![Zrzut ekranu przedstawiający popularne usługi w przykładowym śladzie demonstracyjnej ThreadX.](./media/user-guide/popular_services.png)

**RYSUNEK 20**

Przykład przedstawiony na **rysunku 20** wskazuje, że **_tx_queue_send_*_ i _*_tx_queue_receive_** są dwiema najpopularniejszymi usługami w tym śledzeniu. Jest to zgodne z zachowaniem standardowej demonstracji ThreadX, z którego przechwycono ten ślad.

Dla tej analizy można wybrać określone wątki przy użyciu listy rozwijanej wyboru znajdującej się u góry tego okna. **Rysunek 21** przedstawia tę analizę **_wątku 3_**.

![Zrzut ekranu przedstawiający analizę TraceX popularnych usług.](./media/user-guide/popular_services_thread3.png)

**RYSUNEK 21**

## <a name="thread-stack-usage-analysis-for-thread-3"></a>Użycie stosu wątków ![Analiza wątku 3.](./media/user-guide/screen_shot_17.png)

Wybranie przycisku ***Generuj stos wątków** lub przycisk _*_Wyświetl-> użycie stosu wątku_*_ przedstawia użycie stosu dla każdego wątku w pliku śledzenia. Jest to realizowane przez ThreadX z uwzględnieniem bieżącego wskaźnika stosu wątków w wielu wpisach śledzenia w pliku. Użycie stosu 100% wskazuje, że stos został przepełniony i musi zostać poprawiony w aplikacji. Jeśli w tym pliku śledzenia nie ma wykonania wątku, użycie stosu dla tego wątku jest wyświetlane w 0%. Użycie stosu wątku w przykładowym śladzie demonstracyjnej ThreadX jest pokazane w _ * rysunek 22 * *.

![Zrzut ekranu przedstawiający użycie stosu wątku TraceX.](./media/user-guide/thread_stack_usage.png)

**RYSUNEK 22**

Przykład przedstawiony na **rysunku 22** wskazuje, że większość wątków w tym śladzie ma od 9% do 12% użycia stosu.

## <a name="performance-statistics"></a>Statystyka wydajności

Wybranie przycisku ***Generuj statystykę wydajności** _ przycisk lub _ *_Widok-> statystyki wydajności_** przedstawia dane statystyczne wydajności aktualnie załadowanego pliku śledzenia. Domyślnie te informacje są wyświetlane dla całego systemu. Jednak statystyki wydajności są również dostępne dla każdego określonego wątku.

Statystyka wydajności przykładowego śledzenia demonstracji ThreadX przedstawiono na **rysunku 23**.

![Zrzut ekranu przedstawiający statystyki wydajności TraceX.](./media/user-guide/performance_statistics.png)

**RYSUNEK 23**

Przykład pokazany na **rysunku 23** wskazuje, że wystąpiły 18 przełączników kontekstu w tym pliku śledzenia, a także pięć zawieszeń wątku, zawieszenia 16 wątków, 19 wznowień wątków i trzech przerwań. W tym pliku śledzenia nie znaleziono żadnych wersji priorytetu. Należy zauważyć, że istnieją dwie kategorie niewersji priorytetu, czyli *deterministyczne* i *niedeterministyczne*. Deterministyczne priorytety są niewersjami priorytetowymi, w których wątek jest blokowany w elemencie mutex należącym do wątku o niższym priorytecie. Niedeterministyczna wersja priorytetu polega na tym, że inny wątek o niższym priorytecie jest uruchamiany podczas nieużywanej wersji priorytetu. Później może to spowodować nieprzewidziane zachowanie chronometrażu w aplikacji i należy uważnie przeanalizować.

## <a name="filex-statistics"></a>Statystyka FileX

Wybranie opcji ***View-> FileX Statistics** _ przedstawia statystykę wydajności FileX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu, na wszystkich otwartych.. obiekty/Media. Statystyka wydajności przykładowego śladu demonstracyjnego FileX jest wyświetlana w _ * rysunek 24 * *.

![Zrzut ekranu przedstawiający statystyki FileX.](./media/user-guide/filex_statistics.png)

**RYSUNEK 24**

Przykład przedstawiony na **rysunku 27** wskazuje, że wystąpiły 19. /Media otwiera, 19.. /Media zamyka, 19.. /Media opróżnia, 18 odczyty katalogów, 19 zapisów w katalogu i 18 pamięci podręcznej katalogów. Dodatkowe informacje można wyświetlić, przewijając w dół okna Statystyka.

## <a name="netx-statistics"></a>Statystyka NetX

Wybór ***View-NetX Statistics** _ przedstawia statystykę wydajności NetX aktualnie załadowanego pliku śledzenia. Te informacje są wyświetlane dla całego systemu. Statystyka wydajności przykładowego śladu demonstracyjnego NetX jest wyświetlana w _ * Rysunek 25 * *.

![Zrzut ekranu przedstawiający statystyki NetX.](./media/user-guide/netx_statistics.png)

**RYSUNEK 25**

Przykład przedstawiony na **rysunku nr 25** wskazuje, że nie było zdarzeń ARP, ping lub UDP, ale wystąpiły 30 pakietów IP, wysłano 1 368 bajtów IP, odebrano 30 pakietów IP i odebrano 1 360 bajtów IP.

## <a name="trace-file-information"></a>Informacje o pliku śledzenia

Wybranie opcji ***Wyświetl-> informacje o pliku śledzenia** _ przedstawia pewne podstawowe informacje o otwartym pliku śledzenia. Te informacje obejmują kolejność bajtów pliku, rozmiar źródła czasu, maksymalną liczbę bajtów dla każdej nazwy obiektu i adres podstawowy wszystkich wskaźników plików śledzenia. _ *Ilustracja 26** przedstawia informacje o pliku śledzenia dla standardowego pliku śledzenia **_demo_threadx. TRX_** .

![Zrzut ekranu przedstawiający informacje o pliku TraceX.](./media/user-guide/trace_file_info.png)

**RYSUNEK 26**

## <a name="raw-trace-dump"></a>Nieprzetworzony zrzut śledzenia

Wybranie opcji ***wyświetl > nieprzetworzony zrzut śledzenia** _ przedstawia okno dialogowe z nazwą pliku zawierającego nieprzetworzony zrzut śledzenia. Po wprowadzeniu nazwy pliku i ścieżki TraceX kompiluje Nieprzetworzony plik śledzenia w formacie tekstowym i uruchomi _*_notepad.exe_*_ , aby go wyświetlić. _ *Ilustracja 27** przedstawia nieprzetworzony zrzut pliku śledzenia dla standardowego pliku śledzenia **_demo_threadx. TRX_** .

![Zrzut ekranu przedstawiający nieprzetworzony zrzut śledzenia.](./media/user-guide/raw_trace_dump.png)

**RYSUNEK 27**
