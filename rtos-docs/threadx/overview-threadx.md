---
title: Opis Azure RTOS ThreadX
description: Dowiedz się więcej o usłudze Azure ThreadX, zaawansowanym systemie operacyjnym czasu rzeczywistego (RTOS) zaprojektowanym specjalnie z myślą o aplikacjach głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 8c0bec2bb3b699b3a8d39d85eb322f3bbd95515a
ms.sourcegitcommit: 8b03df42920bdd544fb4195ab818043f6c71969e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2021
ms.locfileid: "114436750"
---
# <a name="overview-of-azure-rtos-threadx"></a>Omówienie Azure RTOS ThreadX

Azure RTOS ThreadX to zaawansowany system operacyjny Real-Time (RTOS) firmy Microsoft. Jest przeznaczona specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i aplikacji IoT. Azure RTOS ThreadX zapewnia zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwami. Ponadto system Azure RTOS ThreadX ma wiele zaawansowanych funkcji, takich jak picokernel™ architektura, próg wywłaszczania™ planowanie, łańcuch zdarzeń, profilowanie wykonywania ™, metryki wydajności i śledzenie zdarzeń systemu. W połączeniu z doskonałą łatwością obsługi Azure RTOS ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych. Azure RTOS ThreadX ma miliardy wdrożeń w wielu różnych produktach, w tym urządzeniach konsumenckich, elektronicznych urządzeniach medycznych i przemysłowym sprzęcie sterującym.

## <a name="threadx-footprint"></a>Ślad ThreadX

Azure RTOS ThreadX ma bardzo mały obszar instrukcji o rozmiarze 2 KB i 1 KB pamięci RAM o minimalnej pamięci RAM. Ten niewielki rozmiar jest w dużej mierze spowodowany niewarstwową architekturą picokernel i automatycznym skalowaniem. Automatyczne skalowanie oznacza, że w końcowej ilustracji w czasie łączenia uwzględniane są tylko usługi (i infrastruktura obsługująca) używane przez aplikację.

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

Azure RTOS ThreadX osiąga przełącznik kontekstu submicrosecond na najpopularniejszych procesorach i jest szybszy ogólnie niż inne komercyjne RTOSs. Oprócz tego, że jest ona szybka, Azure RTOS ThreadX jest również wysoce deterministyczna. Zapewnia ona taką samą szybkość działania niezależnie od tego, czy jest gotowych 200 wątków, czy tylko jeden.

Poniżej podano niektóre typowe charakterystyki wydajności Azure RTOS ThreadX:

* Szybki rozruch: Azure RTOS ThreadX uruchamia się w mniej niż 120 cyklach.
* Opcjonalne usunięcie podstawowego sprawdzania błędów: podstawowe Azure RTOS sprawdzania błędów ThreadX można pominąć w czasie kompilacji. Może to być przydatne, gdy kod aplikacji jest weryfikowany i nie wymaga już sprawdzania błędów dla każdego parametru. Pomijanie sprawdzania błędów można wykonać w jednostce kompilacji, a nie w całym systemie.
* Projekt Picokernel: Usługi nie są nakładane na siebie, eliminując niepotrzebne obciążenia wywołań funkcji.
* Zoptymalizowane przetwarzanie przerwań: podczas wejścia/wyjścia isr są zapisywane/przywracane tylko rejestry scratch, chyba że wywłaszczenie jest konieczne.
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

Azure RTOS ThreadX jest notowalny ze względu na planowanie progu wywłaszczania. Ta funkcja jest unikatowa dla Azure RTOS ThreadX i była przedmiotem rozległych badań akademickich. Więcej informacji można znaleźć w dokumencie [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)(Planowanie zadań z progiem wywłaściwości), a ich autorstwa: Yun Wang (Uniwersytet Wanga) i Manas Saksena (Uniwersytet Pittsburgh).

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
* Łańcuch zdarzeń — rejestrowanie funkcji wywołania zwrotnego "notify" specyficznej dla aplikacji dla każdego obiektu komunikacji lub synchronizacji Azure RTOS ThreadX
* Azure RTOS moduły ThreadX z opcjonalną ochroną pamięci
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

Azure RTOS SMP ThreadX wykonuje dynamiczne równoważenie obciążenia między *n* procesorów. Umożliwia dostęp Azure RTOS zasobów ThreadX (kolejek, semaforów, flag zdarzeń, pul pamięci itp.) przez dowolny wątek na dowolnym rdzeniu. Azure RTOS ThreadX SMP umożliwia pełny interfejs API Azure RTOS ThreadX na wszystkich rdzeniach i wprowadza następujące nowe interfejsy API dotyczące operacji SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Ochrona pamięci za pośrednictwem Azure RTOS ThreadX

Produkt dodatku o nazwie Azure RTOS ThreadX Modules umożliwia dołączanie co najmniej jednego wątków aplikacji do "modułu", który może być dynamicznie ładowany i uruchamiany (lub wykonywany w miejscu) w miejscu docelowym.

Moduły umożliwiają uaktualnianie pól, naprawianie usterek i partycjonowanie programów, aby umożliwić dużym aplikacjom zajmowanie tylko pamięci wymaganej przez aktywne wątki.

Moduły mają również oddzielną przestrzeń adresową od Azure RTOS ThreadX. Dzięki temu Azure RTOS ThreadX może chronić pamięć (za pośrednictwem modułu MPU lub MMU) w taki sposób, że przypadkowy dostęp poza modułem nie będzie mógł uszkodzić żadnego innego składnika oprogramowania.

## <a name="misra-compliant"></a>Zgodne ze standardem MISRA

Azure RTOS ThreadX i Azure RTOS SMP ThreadX są zgodne ze standardem MISRA-C: 2004 i MISRA C:2012. MISRA C to zestaw wytycznych programowania dla systemów krytycznych korzystających z języka programowania C. Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji samochodowych. Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do każdej aplikacji o krytycznym znaczeniu dla bezpieczeństwa. Azure RTOS ThreadX jest zgodny ze wszystkimi wymaganymi i obowiązkowymi regułami MISRA-C: 2004 i MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certyfikacja Misra":::

## <a name="supports-most-popular-tools"></a>Obsługuje najpopularniejsze narzędzia

Azure RTOS ThreadX obsługuje najpopularniejsze osadzone narzędzia programowe, w tym osadzoną usługę Workbench w programie IAR, która ma również najbardziej kompleksową świadomość jądra Azure RTOS ThreadX. Inne integracje narzędzi obejmują GNU (GCC), ARM DS-5/uVision®, Green Gnu MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogiczne.

## <a name="adaptation-layer-for-threadx"></a>Warstwa adaptacji dla ThreadX

Problemy z migracją aplikacji można ułatwić Azure RTOS, korzystając z warstw adaptacji [ThreadX](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) dla różnych starszych interfejsów API RTOS (FreeRTOS, POSIX, OSEK itp.)

> [!div class="nextstepaction"]
> [Wprowadzenie do Azure RTOS ThreadX](chapter1.md)