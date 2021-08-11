---
title: Opis Azure RTOS ThreadX
description: Dowiedz się więcej o usłudze Azure ThreadX, zaawansowanym systemie operacyjnym czasu rzeczywistego (RTOS) zaprojektowanym specjalnie z myślą o aplikacjach głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 300307a82cfde9c74ec0a2499528898b384076676f75bd592fa2840bc5ac53a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796308"
---
# <a name="overview-of-azure-rtos-threadx"></a>Omówienie Azure RTOS ThreadX

Azure RTOS ThreadX to zaawansowany system operacyjny Real-Time (RTOS) firmy Microsoft. Została zaprojektowana specjalnie z myślą o aplikacjach głęboko osadzonych, w czasie rzeczywistym i aplikacjach IoT. Azure RTOS ThreadX zapewnia zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwami. Ponadto system Azure RTOS ThreadX ma wiele zaawansowanych funkcji, takich jak picokernel™ architektura, próg wywłaszczania™ planowanie, łańcuch zdarzeń, profilowanie wykonywania ™, metryki wydajności i śledzenie zdarzeń systemu. W połączeniu z doskonałą łatwością obsługi, Azure RTOS ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych. Azure RTOS ThreadX ma miliardy wdrożeń w wielu różnych produktach, w tym urządzeniach konsumenckich, medycznych urządzeniach elektronicznych i przemysłowych urządzeniach sterujących.

## <a name="threadx-footprint"></a>Ślad ThreadX

Azure RTOS ThreadX ma bardzo mały obszar instrukcji o rozmiarze 2 KB i minimalny rozmiar pamięci RAM 1 KB. Ten niewielki rozmiar wynika głównie z niewarstwowej architektury picokernel i automatycznego skalowania. Automatyczne skalowanie oznacza, że w końcowym obrazie w czasie łączenia uwzględniane są tylko usługi (i infrastruktura obsługująca) używane przez aplikację.

Oto kilka typowych cech Azure RTOS ThreadX.

|Azure RTOS ThreadX Service  |Typowy rozmiar w bajtach  |
|---------|---------|
|Usługi podstawowe (wymagane) |2000  |
|Queue Services  |900  |
|Event Flag Services  |900  |
|Usługi Semaphore  |450  |
|Usługi Mutex  |1200  |
|Blokuj usługi pamięci  |550  |
|Usługi pamięci bajtowej  |900  |

## <a name="threadx-execution-speed"></a>Szybkość wykonywania ThreadX

Azure RTOS ThreadX osiąga przełącznik kontekstu podrzędnego mikrosekund na najpopularniejszych procesorach i jest szybszy ogólnie niż inne komercyjne cele RTOS. Oprócz tego, że są one szybkie, Azure RTOS ThreadX jest również wysoce deterministyczny. Zapewnia ona taką samą wydajność, niezależnie od tego, czy jest gotowych 200 wątków, czy tylko jeden.

Oto kilka typowych cech wydajności Azure RTOS ThreadX:

* Szybki rozruch: Azure RTOS ThreadX uruchamia się w mniej niż 120 cyklach.
* Opcjonalne usunięcie podstawowego sprawdzania błędów: podstawowe Azure RTOS sprawdzania błędów ThreadX można pominąć w czasie kompilacji. Może to być przydatne, gdy kod aplikacji jest weryfikowany i nie wymaga już sprawdzania błędów każdego parametru. Pomijanie sprawdzania błędów można wykonać w jednostce kompilacji, a nie w całym systemie.
* Projekt Picokernel: Usługi nie są nakładane na siebie, eliminując niepotrzebne obciążenia wywołań funkcji.
* Zoptymalizowane przetwarzanie przerwań: podczas wejścia/wyjścia isr są zapisywane/przywracane tylko rejestry scratch, chyba że wywłaszczenie jest konieczne.
* Zoptymalizowane przetwarzanie interfejsu API:

    |Azure RTOS ThreadX Service  |Czas usługi w mikrosekundach*  |
    |---------|---------|
    |Wstrzymywanie wątku  |0,6  |
    |Wznowienie wątku  |0,6  |
    |Wysyłanie w kolejce  |0.3  |
    |Odbieranie w kolejce  |0.3  |
    |Uzyskiwanie semafora  |0,2  |
    |Umieść Semafor  |0,2  |
    |Przełącznik kontekstu  |0,4  |
    |Odpowiedź na przerwanie  |0.0 – 0.6  |

    **Wartości wydajności oparte na typowym procesorze z częstotliwością 200 MHz.*

## <a name="advanced-technology"></a>Zaawansowana technologia

Azure RTOS ThreadX jest notowalny ze względu na planowanie progu wywłaszczania. Ta funkcja jest unikatowa dla Azure RTOS ThreadX i była przedmiotem rozbudowanych badań akademickich. Więcej informacji można znaleźć w dokumencie [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://ieeexplore.ieee.org/document/811269)(Planowanie zadań z progiem wywłaściwości), a ich imieniu są Yun Wang (Uniwersytet Wanga) i Manas Saksena (Uniwersytet Pittsburgh).

Kluczowe możliwości funkcji Azure RTOS ThreadX:

* Kompletne i kompleksowe obiekty wielozadaniowości
  * Wątki, czasomierze aplikacji, kolejki komunikatów, zliczanie semaforów, mutexes, flag zdarzeń, bloków i pul pamięci bajtów
* Priority-Based Planowanie wywłaszcze
* Elastyczność priorytetu — do 1024 poziomów priorytetów
* Planowanie wspólne
* Preemption-Threshold — unikatowa dla Azure RTOS ThreadX, pomaga zmniejszyć przełączniki kontekstu i pomóc w zagwarantować możliwości planowania (na badania akademickie)
* Ochrona pamięci za pośrednictwem Azure RTOS ThreadX MODULES
* W pełni deterministyczny
* Śledzenie zdarzeń — przechwytywanie *ostatnich n* zdarzeń systemu/aplikacji
* Łańcuch zdarzeń — rejestrowanie funkcji wywołania zwrotnego "notify" specyficznej dla aplikacji dla każdego obiektu Azure RTOS ThreadX lub obiektu synchronizacji
* Azure RTOS moduły ThreadX z opcjonalną ochroną pamięci
* Run-Time metryki wydajności
  * Liczba wznowień wątków
  * Liczba wstrzymanych wątków
  * Liczba wywłaszczań wątków na żądanie
  * Liczba asynchronicznych wywłaszczyń przerwań wątków
  * Liczba inversions priorytetów wątków
  * Liczba wątków
* Execution Profile Kit (EPK)
* Oddzielny stos przerwań
* Run-Time Stack Analysis
* Zoptymalizowane przetwarzanie przerwań czasomierza

## <a name="multicore-support-amp--smp"></a>Obsługa wielu rdzeni (AMP & SMP)

Standard Azure RTOS ThreadX jest często używany w asymetrycznym przetwarzaniu wieloprocesorowym (AMP), gdzie oddzielna kopia pliku Azure RTOS ThreadX i aplikacja (lub Linux) są wykonywane na każdym rdzeniu i komunikują się ze sobą za pośrednictwem pamięci współdzielonego lub mechanizmu komunikacji między procesorami, takiego jak OpenAMP (Azure RTOS ThreadX obsługuje openAMP).

W środowiskach, w których ładowanie procesorów jest wysoce dynamiczne, Azure RTOS symetrycznego przetwarzania wieloprocesorowego ThreadX (SMP) jest dostępny dla następujących rodzin procesorów:

* Arm Cortex-Ax
* Arm Cortex-Rx
* Arm Cortex-A5x 64-bitowy
* MIPS 34 K, 1004 K i interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP wykonuje dynamiczne równoważenie obciążenia między *n* procesorów. Dzięki temu wszystkie Azure RTOS ThreadX (kolejki, semafory, flagi zdarzeń, pule pamięci itp.) mogą być dostępne dla dowolnego wątku na dowolnym rdzeniu. Azure RTOS ThreadX SMP umożliwia pełny interfejs API Azure RTOS ThreadX na wszystkich rdzeniach i wprowadza następujące nowe interfejsy API dotyczące operacji SMP:

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

Azure RTOS ThreadX obsługuje najpopularniejsze osadzone narzędzia programskie, w tym osadzoną usługę Workbench systemu IAR, która ma również najbardziej Azure RTOS świadomości jądra ThreadX. Inne narzędzia integracji obejmują GNU (GCC), ARM DS-5/uVision®, GreenRow MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogiczne.

## <a name="adaptation-layer-for-threadx"></a>Warstwa adaptacji dla ThreadX

Problemy z migracją aplikacji można ułatwić Azure RTOS, korzystając z warstw adaptowania [ThreadX](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) dla różnych starszych interfejsów API RTOS (FreeRTOS, POSIX, OSEK itp.)

> [!div class="nextstepaction"]
> [Wprowadzenie do Azure RTOS ThreadX](chapter1.md)