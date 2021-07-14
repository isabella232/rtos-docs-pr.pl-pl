---
title: Opis Azure RTOS ThreadX
description: Azure ThreadX to zaawansowany system operacyjny czasu rzeczywistego (RTOS) zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 938619170ef51d354fa970134328c17407ae846a
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754866"
---
# <a name="overview-of-azure-rtos-threadx"></a>Omówienie Azure RTOS ThreadX

Azure RTOS ThreadX to zaawansowany system operacyjny Real-Time klasy przemysłowej (RTOS) firmy Microsoft zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych, działających w czasie rzeczywistym i IoT. Azure RTOS ThreadX zapewnia zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwami. Ponadto system Azure RTOS ThreadX ma wiele zaawansowanych funkcji, takich jak picokernel™ architektura, próg wywłaszczania™ planowanie, łańcuch zdarzeń, profilowanie wykonywania ™, metryki wydajności i śledzenie zdarzeń systemu. W połączeniu z doskonałą łatwością użycia, Azure RTOS ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych. Od 2017 r. firma Azure RTOS ThreadX ma ponad 6,2 miliarda wdrożeń w wielu różnych produktach, w tym urządzeniach konsumenckich, urządzeniach elektronicznych i przemysłowych urządzeniach sterujących.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="azure-rtos-threadx-services"></a>Azure RTOS ThreadX Services

* Dynamiczne tworzenie wątku
* Brak limitów liczby wątków
* Interfejsy API głównego wątku obejmują:
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* Dodatkowe informacje i interfejsy API wydajności

### <a name="message-queues"></a>Kolejki komunikatów

* Dynamiczne tworzenie kolejki
* Brak limitów liczby kolejek
* Komunikaty skopiowane przez wartość (lub przez odwołanie za pośrednictwem wskaźnika)
* Rozmiary komunikatów od 1 do 16 słów 32-bitowych
* Opcjonalne wstrzymanie wątku przy pustym i pełnym
* Opcjonalny limit czasu dla całego zawieszenia
* Interfejsy API kolejki komunikatów głównych obejmują:
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* Dodatkowe informacje i interfejsy API wydajności

### <a name="counting-semaphores"></a>Zliczanie semaforów

* Dynamiczne tworzenie semaforów
* Brak limitów liczby semaforów
* 32-bitowe zliczanie semaforów (od 0 do 4 294 967 295)
* Obsługuje ochronę konsumentów i producentów zasobów
* Opcjonalne zawieszenie wątku, gdy semafor jest niedostępny
* Opcjonalny limit czasu dla całego zawieszenia
* Główne interfejsy API semaforów obejmują:
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* Dodatkowe informacje i interfejsy API wydajności

### <a name="mutexes"></a>Muteksy

* Dynamiczne tworzenie obiektu mutex
* Brak limitów liczby mutexes
* Obsługiwana ochrona zagnieżdżonych zasobów
* Obsługiwane opcjonalne dziedziczenie priorytetów
* Opcjonalne zawieszenie wątku, gdy element mutex jest niedostępny
* Opcjonalny limit czasu dla całego zawieszenia
* Główne interfejsy API mutex obejmują:
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* Dodatkowe informacje i interfejsy API wydajności

### <a name="event-flags"></a>Flagi zdarzeń

* Dynamiczne tworzenie grupy flag zdarzeń
* Brak limitów liczby grup flag zdarzeń
* Synchronizacja jednego wątku lub wielu wątków
* Niepodzielne uzyskiwanie i wyczyść obsługiwane
* Opcjonalne zawieszenie wielowątkowe dla zestawu zdarzeń AND/OR
* Opcjonalny limit czasu dla całego zawieszenia
* Główne interfejsy API flag zdarzeń obejmują:
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* Dodatkowe informacje i interfejsy API wydajności

### <a name="block-memory-pools"></a>Blokuj pule pamięci

* Dynamiczne tworzenie puli bloków
* Brak limitów liczby pul bloków
* Brak limitów rozmiaru bloków o stałym rozmiarze lub rozmiaru puli
* Najszybsza możliwa alokacja pamięci/deal-location
* Opcjonalne zawieszenie wątku w pustej puli
* Opcjonalny limit czasu dla całego zawieszenia
* Główne interfejsy API puli bloków obejmują:
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* Dodatkowe informacje i interfejsy API wydajności

### <a name="byte-memory-pools"></a>Pule pamięci bajtów

* Dynamiczne tworzenie puli bajtów
* Brak limitów liczby pul bajtów
* Brak limitów rozmiaru puli bajtów
* Najbardziej elastyczna alokacja pamięci o zmiennej długości/co deallocation
* Obsługiwana lokalizacja rozmiaru alokacji
* Opcjonalne zawieszenie wątku w pustej puli
* Opcjonalny limit czasu dla całego zawieszenia
* Interfejsy API puli bajtów głównych obejmują:
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* Dodatkowe informacje i interfejsy API wydajności

### <a name="application-timers"></a>Czasomierze aplikacji

* Dynamiczne tworzenie czasomierza
* Brak limitów liczby czasomierzy
* Obsługiwane czasomierze okresowe lub czasomierze jednozmijowe
* Czasomierze okresowe mogą mieć inną wartość początkowego wygaśnięcia
* Brak wyszukiwania w przypadku aktywacji lub dezaktywacji czasomierza
* Wszystkie czasomierze sterowane przez jedno sprzętowe przerwanie czasomierza
* Główne interfejsy API czasomierza obejmują:
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* Dodatkowe informacje i interfejsy API wydajności

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure RTOS ThreadX Core Scheduler

* Minimalna ilość pamięci FLASH 2 KB, 1 KB pamięci RAM
* Szybki, podrzędny mikrosekundowy przełącznik kontekstowy
* W pełni deterministyczne, niezależnie od liczby wątków
* Oparte na priorytetach, w pełni wywłaszczujące planowanie
* 32 domyślne poziomy priorytetów, opcjonalnie do 1024 poziomów
* Planowanie wspólne na poziomie priorytetu (FIFO)
* Technologia progu wywłaszczenia
* Opcjonalne usługi czasomierza, w tym:
  * Opcjonalny wycinek czasu dla każdego wątku
  * Opcjonalny limit czasu dla wszystkich blokad
  * Interfejsy API wymagają przerwania czasomierza sprzętowego
* Profilowanie wykonywania
* Śledzenie na poziomie systemu
* Bezpieczeństwo certyfikowane przez wiele standardów

## <a name="threadx-footprint"></a>Ślad ThreadX

Azure RTOS ThreadX wymaga bardzo małego obszaru instrukcji 2KB i 1 KB pamięci RAM w celu jego minimalnego zużycie. Wynika to głównie z niewarstwowej architektury picokernel™ automatycznego skalowania. Automatyczne skalowanie oznacza, że w końcowym obrazie w czasie łączenia uwzględniane są tylko usługi (i infrastruktura obsługująca) używane przez aplikację.

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

Azure RTOS ThreadX osiąga przełącznik kontekstu podrzędnego mikrosekund na najpopularniejszych procesorach i jest znacznie szybszy ogólnie niż inne komercyjne cele RTOS. Oprócz tego, że jest ona szybka, Azure RTOS ThreadX jest również wysoce deterministyczna. Zapewnia ona taką samą wydajność, niezależnie od tego, czy jest gotowych 200 wątków, czy tylko jeden.

Poniżej podano niektóre typowe charakterystyki wydajności Azure RTOS ThreadX:

* Szybki rozruch: Azure RTOS ThreadX uruchamia się w mniej niż 120 cyklach.
* Opcjonalne usunięcie podstawowego sprawdzania błędów: podstawowe Azure RTOS sprawdzania błędów ThreadX można pominąć w czasie kompilacji. Może to być przydatne, gdy kod aplikacji jest weryfikowany i nie wymaga już sprawdzania błędów dla każdego parametru. Należy pamiętać, że można to zrobić w jednostce kompilacji, a nie w całym systemie.
* Picokernel™ Design: Usługi nie są nakładane na siebie, eliminując niepotrzebne obciążenia wywołań funkcji.
* *Zoptymalizowane przetwarzanie przerwań: tylko rejestry scratch są zapisywane/przywracane podczas wejścia/wyjścia isr, chyba że wywłaszczenie jest konieczne.
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

Azure RTOS ThreadX to zaawansowana technologia, której najważniejszą funkcją jest planowanie próg wywłaszczania. Ta funkcja jest unikatowa dla Azure RTOS ThreadX i była przedmiotem rozległych badań akademickich. Zobacz na przykład [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)(Planowanie zadań z progiem wywłaściwości), a ich autorstwa: Yun Wang, University Of Ichia University i Manas Saksena z Uniwersytetu Pittsburgh.

Weź pod uwagę możliwości Azure RTOS ThreadX.

* Kompletne i kompleksowe obiekty wielozadaniowości
  * Wątki, czasomierze aplikacji, kolejki komunikatów, zliczanie semaforów, mutexów, flag zdarzeń, blokowych i bajtowych pul pamięci
* Priority-Based planowanie wywłaszcze
* Elastyczność priorytetu — do 1024 poziomów priorytetów
* Wspólne planowanie
* Próg wywłaszczania™ — unikatowy dla Azure RTOS ThreadX, pomaga ograniczyć przełączniki kontekstu i pomóc w zagwarantowaniu możliwości planowania (na badania akademickie)
* Ochrona pamięci za pośrednictwem Azure RTOS ThreadX MODULES
* W pełni deterministyczny
* Śledzenie zdarzeń — przechwytywanie *ostatnich n* zdarzeń systemu/aplikacji
* Łańcuch zdarzeń™ — rejestrowanie funkcji wywołania zwrotnego "notify" specyficznej dla aplikacji dla każdego obiektu komunikacji lub synchronizacji Azure RTOS ThreadX
* Azure RTOS moduły ThreadX z opcjonalną ochroną pamięci
* Run-Time metryk wydajności
  * Liczba wznowień wątków
  * Liczba zawieszenia wątków
  * Liczba wywłaszczeń wątków na żądanie
  * Liczba asynchronicznych wywłaszcze przerwań wątków
  * Liczba inwersji priorytetów wątków
  * Liczba wątków
* Execution Profile Kit (EPK)
* Oddzielny stos przerwań
* Run-Time Stack Analysis
* Zoptymalizowane przetwarzanie przerwań czasomierza

## <a name="multicore-support-amp--smp"></a>Obsługa wielu rdzeni (AMP & SMP)

Standard Azure RTOS ThreadX jest często używany w asymetrycznym wieloprocesorowym przetwarzaniu (AMP), gdzie oddzielna kopia pliku Azure RTOS ThreadX i aplikacji (lub Linux) jest wykonywana na każdym rdzeniu i komunikuje się ze sobą za pośrednictwem pamięci współdzielonego lub mechanizmu komunikacji między procesorami, takiego jak OpenAMP (Azure RTOS ThreadX obsługuje openAMP). Jest to najbardziej typowa konfiguracja wielordzeniowa korzystająca z Azure RTOS ThreadX i może być najbardziej wydajna, jeśli aplikacja jest w stanie efektywnie załadować procesory.

W środowiskach, w których ładowanie procesorów jest bardzo dynamiczne, Azure RTOS ThreadX Symetric Multiprocessing (SMP) jest dostępny dla następujących rodzin procesorów:

* Arm Cortex-Ax
* Arm Cortex-Rx
* Arm Cortex-A5x 64-bitowy
* MIPS 34K, 1004K i interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP wykonuje dynamiczne równoważenie obciążenia między *n* procesorami i umożliwia dostęp do wszystkich zasobów Azure RTOS ThreadX (kolejek, semaforów, flag zdarzeń, pul pamięci itp.) przez dowolny wątek na dowolnym rdzeniu. Azure RTOS ThreadX SMP umożliwia pełny interfejs API Azure RTOS ThreadX na wszystkich rdzeniach i wprowadza następujące nowe interfejsy API dotyczące operacji SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Ochrona pamięci za pośrednictwem Azure RTOS ThreadX

Dodatek o nazwie Azure RTOS ThreadX MODULES umożliwia dołączanie co najmniej jednego wątków aplikacji do "modułu", który może być dynamicznie ładowany i uruchamiany (lub wykonywany w miejscu) w miejscu docelowym.

Moduły umożliwiają uaktualnianie pól, naprawianie usterek i partycjonowanie programów, aby umożliwić dużym aplikacjom zajmowanie tylko pamięci wymaganej przez aktywne wątki.

Moduły mają również całkowicie oddzieloną przestrzeń adresową od Azure RTOS ThreadX. Dzięki temu Azure RTOS ThreadX może chronić pamięć (za pośrednictwem modułu MPU lub MMU) w taki sposób, że przypadkowy dostęp poza modułem nie będzie mógł uszkodzić żadnego innego składnika oprogramowania.

## <a name="misra-compliant"></a>Zgodne ze standardem MISRA

Azure RTOS ThreadX i Azure RTOS SMP ThreadX są zgodne ze standardem MISRA-C:2004 i MISRA C:2012. MISRA C to zestaw wytycznych dotyczących programowania dla systemów krytycznych korzystających z języka programowania C. Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji samochodowych. Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa. Azure RTOS ThreadX jest zgodny ze wszystkimi wymaganymi i obowiązkowymi regułami MISRA-C:2004 i MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certyfikacja Misra":::

## <a name="supports-most-popular-tools"></a>Obsługuje najpopularniejsze narzędzia

Azure RTOS ThreadX obsługuje najpopularniejsze osadzone narzędzia programowe, w tym embedded Workbench™ systemu IAR, który ma również najbardziej kompleksową świadomość jądra Azure RTOS ThreadX. Dodatkowa integracja narzędzi obejmuje GNU (GCC), ARM DS-5/uVision®, GreenRow MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogiczne.

## <a name="adaptation-layer-for-threadx"></a>Warstwa adaptacji dla ThreadX

System ThreadX usługi Azure RTOS to zaawansowany system operacyjny czasu rzeczywistego zaprojektowany specjalnie pod kątem głęboko osadzonych aplikacji. Aby ułatwić migrację aplikacji do systemu Auzre RTOS, ThreadX udostępnia warstwy adaptacji dla różnych starszych interfejsów API RTOS (FreeRTOS, POSIX, OSEK itp.) [](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)
