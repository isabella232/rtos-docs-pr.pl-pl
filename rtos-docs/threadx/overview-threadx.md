---
title: Opis Azure RTOS ThreadX
description: Dowiedz się więcej o usłudze Azure ThreadX, zaawansowanym systemie operacyjnym czasu rzeczywistego (RTOS) zaprojektowanym specjalnie z myślą o aplikacjach głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 4b6c8df5133f16cf3ed4006c12433ac426453cb5
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178208"
---
# <a name="overview-of-azure-rtos-threadx"></a>Omówienie Azure RTOS ThreadX

Azure RTOS ThreadX to zaawansowany system operacyjny Real-Time (RTOS) firmy Microsoft. Jest przeznaczona specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i aplikacji IoT. Azure RTOS ThreadX zapewnia zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwami. Ponadto system Azure RTOS ThreadX ma wiele zaawansowanych funkcji, takich jak picokernel™ architektura, próg wywłaszczania™ planowanie, łańcuch zdarzeń, profilowanie wykonywania ™, metryki wydajności i śledzenie zdarzeń systemu. W połączeniu z doskonałą łatwością obsługi Azure RTOS ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych. Azure RTOS ThreadX ma miliardy wdrożeń w wielu różnych produktach, w tym urządzeniach konsumenckich, elektronicznych urządzeniach medycznych i przemysłowym sprzęcie sterującym.

## <a name="threadx-footprint"></a>Ślad ThreadX

Azure RTOS ThreadX ma bardzo mały obszar instrukcji 2 KB i 1 KB pamięci RAM o minimalnej pamięci RAM. Ten niewielki rozmiar jest w dużej mierze spowodowany niewarstwową architekturą picokernel i automatycznym skalowaniem. Automatyczne skalowanie oznacza, że w końcowej ilustracji w czasie łączenia uwzględniane są tylko usługi (i infrastruktura obsługująca) używane przez aplikację.

Oto kilka typowych cech Azure RTOS ThreadX.

|Azure RTOS ThreadX Service  |Typowy rozmiar w bajtach  |
|---------|---------|
|Usługi podstawowe (wymagaj) |2000  |
|Queue Services  |900  |
|Event Flag Services  |900  |
|Semaphore Services  |450  |
|Usługi Mutex  |1200  |
|Blokuj usługi pamięci  |550  |
|Usługi pamięci bajtowej  |900  |

## <a name="threadx-execution-speed"></a>Szybkość wykonywania threadX

Azure RTOS ThreadX osiąga przełącznik kontekstu podrzędnego mikrosekund na najpopularniejszych procesorach i jest szybszy ogólnie niż inne komercyjne cele RTOS. Oprócz tego, że jest ona szybka, Azure RTOS ThreadX jest również wysoce deterministyczna. Zapewnia ona taką samą wydajność, niezależnie od tego, czy jest gotowych 200 wątków, czy tylko jeden.

Poniżej podano niektóre typowe charakterystyki wydajności Azure RTOS ThreadX:

* Szybki rozruch: Azure RTOS ThreadX uruchamia się w mniej niż 120 cyklach.
* Opcjonalne usunięcie podstawowego sprawdzania błędów: podstawowe Azure RTOS sprawdzania błędów ThreadX można pominąć w czasie kompilacji. Może to być przydatne, gdy kod aplikacji jest weryfikowany i nie wymaga już sprawdzania błędów dla każdego parametru. Pomijanie sprawdzania błędów można wykonać w jednostce kompilacji, a nie w całym systemie.
* Projekt Picokernel: Usługi nie są nakładane na siebie, eliminując niepotrzebne obciążenia wywołań funkcji.
* Zoptymalizowane przetwarzanie przerwań: tylko rejestry scratch są zapisywane/przywracane podczas wejścia/wyjścia isr, chyba że wywłaszczenie jest konieczne.
* Zoptymalizowane przetwarzanie interfejsu API:

    |Azure RTOS ThreadX Service  |Czas usługi w mikrosekundach*  |
    |---------|---------|
    |Wstrzymywanie wątku  |0,6  |
    |Wznawianie wątku  |0,6  |
    |Wysyłanie w kolejce  |0.3  |
    |Odbieranie w kolejce  |0.3  |
    |Uzyskiwanie Semafora  |0,2  |
    |Umieść Semafor  |0,2  |
    |Przełącznik kontekstu  |0,4  |
    |Odpowiedź na przerwanie  |0.0 – 0.6  |

    **Wartości wydajności oparte na typowym procesorze z częstotliwością 200 MHz.*

## <a name="advanced-technology"></a>Zaawansowana technologia

Azure RTOS ThreadX jest notowalny ze względu na planowanie próg wywłaszczania. Ta funkcja jest unikatowa dla Azure RTOS ThreadX i była przedmiotem rozległych badań akademickich. Więcej informacji można znaleźć w dokumencie [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://ieeexplore.ieee.org/document/811269)(Planowanie zadań przy użyciu progu wywłaściwości), a ich imieniu są Yun Wang (Uniwersytet Wang) i Manas Saksena (Uniwersytet Pittsburgh).

Kluczowe możliwości Azure RTOS ThreadX:

* Kompletne i kompleksowe obiekty wielozadaniowości
  * Wątki, czasomierze aplikacji, kolejki komunikatów, zliczanie semaforów, mutexes, flag zdarzeń, bloków i pul pamięci bajtów
* Priority-Based planowanie wywłaszcze
* Elastyczność priorytetu — do 1024 poziomów priorytetów
* Wspólne planowanie
* Preemption-Threshold — unikatowa w Azure RTOS ThreadX, pomaga zmniejszyć przełączniki kontekstowe i zagwarantować możliwości planowania (na badania akademickie)
* Ochrona pamięci za pośrednictwem Azure RTOS ThreadX MODULES
* W pełni deterministyczny
* Śledzenie zdarzeń — przechwytywanie *ostatnich n* zdarzeń systemowych/aplikacji
* Łańcuch zdarzeń — rejestrowanie funkcji wywołania zwrotnego "notify" specyficznej dla aplikacji dla każdego Azure RTOS threadX lub obiektu synchronizacji
* Azure RTOS ThreadX MODULES z opcjonalną ochroną pamięci
* Run-Time metryk wydajności
  * Liczba wznowień wątków
  * Liczba zawieszenia wątków
  * Liczba wywłaszczania wątków na żądanie
  * Liczba asynchronicznych wywłaszczyń przerwań wątków
  * Liczba inwersji priorytetów wątków
  * Liczba wątków
* Execution Profile Kit (EPK)
* Oddzielny stos przerwań
* Run-Time Stack Analysis
* Zoptymalizowane przetwarzanie przerwań czasomierza

## <a name="multicore-support-amp--smp"></a>Obsługa wielu rdzeni (AMP & SMP)

Standard Azure RTOS ThreadX jest często używany w asymetrycznym wieloprocesorowym przetwarzaniu (AMP), gdzie oddzielna kopia pliku Azure RTOS ThreadX i aplikacja (lub Linux) jest wykonywana na każdym rdzeniu i komunikuje się ze sobą za pośrednictwem pamięci współdzielonego lub mechanizmu komunikacji między procesorami, takiego jak OpenAMP (Azure RTOS ThreadX obsługuje openAMP).

W środowiskach, w których ładowanie procesorów jest wysoce dynamiczne, Azure RTOS symetrycznego przetwarzania wieloprocesorowego ThreadX (SMP) jest dostępna dla następujących rodzin procesorów:

* Arm Cortex-Ax
* Arm Cortex-Rx
* Arm Cortex-A5x 64-bitowy
* MIPS 34 K, 1004 K i interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS SMP ThreadX wykonuje dynamiczne równoważenie obciążenia między *n* procesorów. Umożliwia dostęp Azure RTOS zasobów ThreadX (kolejek, semaforów, flag zdarzeń, pul pamięci itp.) przez dowolny wątek na dowolnym rdzeniu. Azure RTOS ThreadX SMP umożliwia pełną obsługę interfejsu API Azure RTOS ThreadX na wszystkich rdzeniach i wprowadza następujące nowe interfejsy API dotyczące operacji SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Ochrona pamięci za pośrednictwem Azure RTOS ThreadX

Produkt dodatku o nazwie Azure RTOS ThreadX Modules umożliwia dołączanie co najmniej jednego wątków aplikacji do "modułu", który może być dynamicznie ładowany i uruchamiany (lub wykonywany w miejscu) w miejscu docelowym.

Moduły umożliwiają uaktualnianie pól, naprawianie usterek i partycjonowanie programów, aby umożliwić dużym aplikacjom zajmowanie tylko pamięci wymaganej przez aktywne wątki.

Moduły mają również oddzielną przestrzeń adresową od Azure RTOS ThreadX. Dzięki temu Azure RTOS ThreadX może chronić pamięć (za pośrednictwem modułu MPU lub MMU), tak aby przypadkowy dostęp poza modułem nie mógł uszkodzić żadnego innego składnika oprogramowania.

## <a name="misra-compliant"></a>Zgodne ze standardem MISRA

Azure RTOS ThreadX Azure RTOS kod źródłowy SMP ThreadX jest zgodny ze standardem MISRA-C: 2004 i MISRA C:2012. MISRA C to zestaw wytycznych programistycznych dla systemów o krytycznym znaczeniu korzystających z języka programowania C. Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji w przemyśle samochodowym; Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do każdej aplikacji o krytycznym znaczeniu dla bezpieczeństwa. Azure RTOS ThreadX jest zgodny ze wszystkimi wymaganymi i obowiązkowymi regułami MISRA-C: 2004 i MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certyfikacja Misra":::

## <a name="supports-most-popular-tools"></a>Obsługuje najpopularniejsze narzędzia

Azure RTOS ThreadX obsługuje najpopularniejsze osadzone narzędzia programskie, w tym osadzoną usługę Workbench systemu IAR, która ma również najbardziej kompleksową świadomość jądra Azure RTOS ThreadX. Inne narzędzia integracji obejmują GNU (GCC), ARM DS-5/uVision®, GreenRow MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogiczne.

## <a name="adaptation-layer-for-threadx"></a>Warstwa adaptacji dla ThreadX

Problemy z migracją aplikacji można ułatwić Azure RTOS przy użyciu warstw adaptacji [ThreadX](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) dla różnych starszych interfejsów API RTOS (FreeRTOS, POSIX, OSEK itp.)

> [!div class="nextstepaction"]
> [Wprowadzenie do Azure RTOS ThreadX](chapter1.md)