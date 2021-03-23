---
title: Opis usługi Azure RTO ThreadX
description: Azure ThreadX to zaawansowany system operacyjny w czasie rzeczywistym (RTO) zaprojektowany specjalnie dla aplikacji głęboko Embedded.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823250"
---
# <a name="overview-of-azure-rtos-threadx"></a>Omówienie usługi Azure RTO ThreadX

Usługa Azure RTO ThreadX to zaawansowane Real-Time przemysłowe systemu operacyjnego firmy Microsoft przeznaczone specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i IoT. Usługa Azure RTO ThreadX oferuje zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwaniem. Ponadto usługa Azure RTO ThreadX ma wiele zaawansowanych funkcji, w tym ich architektury picokernel™,™ planowanie, tworzenie łańcucha zdarzeń, profilowanie wykonywania™, metryki wydajności i śledzenie zdarzeń systemu. W połączeniu z najbardziej łatwym w użyciu usługą Azure RTO ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych. Począwszy od 2017, usługa Azure RTO ThreadX ma ponad 6 200 000 000 wdrożeń w wielu różnych produktach, w tym na urządzeniach konsumenckich, elektroniki medycznej i urządzeniach kontroli przemysłowej.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="azure-rtos-threadx-api"></a>Interfejs API usługi Azure RTO ThreadX

* Intuicyjny i spójny interfejs API
* W konwencji nazewnictwa czasowników
* Wszystkie interfejsy API mają wiodące *TX_* do łatwej identyfikacji jako Azure RTO ThreadX
* Blokowanie interfejsów API ma opcjonalny limit czasu wątku
* Wiele interfejsów API jest dostępnych bezpośrednio z aplikacji procedury ISR

### <a name="azure-rtos-threadx-services"></a>Usługi Azure RTO ThreadX

* Dynamiczne tworzenie wątków
* Brak limitów liczby wątków
* Główne interfejsy API wątku obejmują:
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

* Tworzenie kolejki dynamicznej
* Brak limitów liczby kolejek
* Komunikaty skopiowane przez wartość (lub przez odwołanie przez wskaźnik)
* Rozmiary komunikatów od 1 do 16 32 — wyrazy bitowe
* Opcjonalne zawieszenie wątku dla pustych i pełnych
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Główne interfejsy API kolejki komunikatów obejmują:
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
* 32-bitowe semafory zliczania (od 0 do 4 294 967 295)
* Obsługa ochrony przed producentami i zasobami
* Opcjonalne zawieszenie wątku, gdy semafor jest niedostępny
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Główne interfejsy API semaforów obejmują:
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* Dodatkowe informacje i interfejsy API wydajności

### <a name="mutexes"></a>Muteksy

* Dynamiczne tworzenie obiektów mutex
* Brak limitów liczby muteksów
* Obsługiwana jest zagnieżdżona ochrona zasobów
* Obsługiwane dziedziczenie opcjonalnego priorytetu
* Opcjonalne zawieszenie wątku, gdy element mutex jest niedostępny
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Główne interfejsy API muteksu obejmują:
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* Dodatkowe informacje i interfejsy API wydajności

### <a name="event-flags"></a>Flagi zdarzeń

* Tworzenie grupy flag zdarzeń dynamicznych
* Brak limitów liczby grup flag zdarzeń
* Synchronizacja jednego wątku lub wielu wątków
* Obsługiwane są niepodzielne operacje get i Clear
* Opcjonalne zawieszenie wielowątkowej dla i/lub zbioru zdarzeń
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Najważniejsze interfejsy API flagi zdarzenia:
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* Dodatkowe informacje i interfejsy API wydajności

### <a name="block-memory-pools"></a>Blokuj Pule pamięci

* Tworzenie puli bloków dynamicznych
* Brak limitów liczby pul bloków
* Brak limitów rozmiaru bloków o stałym rozmiarze lub rozmiaru puli
* Najszybszy możliwy przydział pamięci/lokalizacja transakcji
* Opcjonalne zawieszenie wątku w pustej puli
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Główne interfejsy API puli bloków obejmują:
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* Dodatkowe informacje i interfejsy API wydajności

### <a name="byte-memory-pools"></a>Pule pamięci bajtów

* Tworzenie puli bajtów dynamicznych
* Brak limitów liczby pul bajtów
* Brak ograniczeń dotyczących rozmiaru puli bajtów
* Większość elastycznej alokacji pamięci o zmiennej długości lub cofnięcia alokacji
* Obsługiwany lokalnie rozmiar alokacji
* Opcjonalne zawieszenie wątku w pustej puli
* Opcjonalny limit czasu dla wszystkich zawieszeń
* Interfejsy API głównej puli bajtów obejmują:
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* Dodatkowe informacje i interfejsy API wydajności

### <a name="application-timers"></a>Czasomierze aplikacji

* Tworzenie czasomierza dynamicznego
* Brak limitów liczby czasomierzy
* Obsługiwane są czasomierze okresowe lub jednorazowe
* Okresowe czasomierze mogą mieć inną początkową wartość wygaśnięcia
* Brak wyszukiwania w przypadku aktywacji lub dezaktywacji czasomierza
* Wszystkie czasomierze oparte na jednym przerwaniu czasomierza sprzętowego
* Główne interfejsy API Timer obejmują:
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* Dodatkowe informacje i interfejsy API wydajności

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure RTO ThreadX — podstawowy harmonogram

* Minimum 2KB FLASH, rozmiarze 1 KB pamięci RAM
* Fast, sub-mikrosekundowych — przełącznik kontekstu
* W pełni deterministyczne niezależnie od liczby wątków
* Oparte na priorytetach, w pełni zastępujące — planowanie
* 32 domyślne poziomy priorytetów, opcjonalnie do 1024 poziomów
* Wspólne planowanie na poziomie priorytetu (FIFO)
* Technologia progu zastępujące
* Opcjonalne usługi czasomierza, w tym:
  * Opcjonalny czas dla wątku
  * Opcjonalny limit czasu dla wszystkich blokad
  * Interfejsy API wymagają przerwania czasomierza sprzętowego
* Profilowanie wykonywania
* Śledzenie na poziomie systemu
* Bezpieczeństwo certyfikowane dla wielu standardów

## <a name="most-deployed-rtos"></a>Większość wdrożonych RTO

Usługa Azure RTO ThreadX ma ponad 6 200 000 000 wdrożeń na całym świecie, zgodnie z wiodącym w firmie M2M przedsiębiorstwie analizy rynku, VDC Research. Popularność usługi Azure RTO ThreadX jest świadczy do jej niezawodności, jakości, rozmiaru, wydajności, zaawansowanych funkcji, łatwość użycia i ogólnych korzyści związanych z tym rynkiem.

> *"Trajektorii wzrost THREADX na rynkach sieci bezprzewodowych i IoT od momentu, w którym wykryto firmę, i coraz częściej się nie naciskaj przez szeroko wdrażaną branżę THREADX".* — Krzysztof Rommel, wiceprezes wykonawczy, VDC Research

## <a name="small-footprint"></a>Niewielkie rozmiary

Usługa Azure RTO ThreadX wymaga, aby niezwykle mały 2KB obszar instrukcji i rozmiarze 1 KB pamięci RAM. Jest to duże ze względu na niewarstwowe™ picokernel architektury i skalowanie automatyczne. Automatyczne skalowanie oznacza, że tylko usługi (i infrastruktura pomocnicza) używane przez aplikację są uwzględniane w końcowym obrazie w czasie konsolidacji.

Poniżej przedstawiono niektóre typowe charakterystyki rozmiaru usługi Azure RTO ThreadX:

|Usługa Azure RTO ThreadX  |Typowy rozmiar w bajtach  |
|---------|---------|
|Podstawowe usługi (wymagane) |2000  |
|Usługi kolejki  |900  |
|Usługi flag zdarzeń  |900  |
|Usługi semaforów  |450  |
|Usługi muteksów  |1200  |
|Blokuj usługi pamięci  |550  |
|Usługi pamięci bajtów  |900  |

## <a name="fast-execution"></a>Szybkie wykonywanie

Usługa Azure RTO ThreadX zapewnia przełącznik kontekstu sub-mikrosekundowych na najpopularniejszych procesorach i jest znacznie szybszy w porównaniu z innymi komercyjnymi RTOSesami. Oprócz szybkiego, usługa Azure RTO ThreadX jest również wysoce deterministyczna. Zapewnia to taką samą szybką wydajność, niezależnie od tego, czy istnieją 200 wątki gotowe, czy tylko jeden.

Poniżej przedstawiono niektóre typowe cechy wydajności usługi Azure RTO ThreadX:

* Szybki rozruch: usługa Azure RTO ThreadX uruchamiana w mniej niż 120 cyklach.
* Opcjonalne usuwanie podstawowego sprawdzania błędów: podstawowe sprawdzanie błędów usługi Azure RTO ThreadX można pominąć w czasie kompilacji. Może to być przydatne, gdy kod aplikacji jest zweryfikowany i nie wymaga już sprawdzenia błędów dla każdego parametru. Należy pamiętać, że można to zrobić w jednostce kompilacji, a nie na poziomie całego systemu.
* Picokernel™: usługi nie są nakładane na siebie, co eliminuje zbędne obciążenie wywołania funkcji.
* * Zoptymalizowane przetwarzanie przerwań: tylko rejestry wyjściowe są zapisywane/przywracane podczas wejścia/wyjścia ISR, chyba że jest to konieczne.
* Zoptymalizowane przetwarzanie interfejsu API:

    |Usługa Azure RTO ThreadX  |Czas pracy usługi w mikrosekundach *  |
    |---------|---------|
    |Wstrzymywanie wątku  |0,6  |
    |Wznowienie wątku  |0,6  |
    |Wysyłanie kolejki  |0.3  |
    |Odbieranie kolejki  |0.3  |
    |Pobierz semafor  |0,2  |
    |Umieść semafor  |0,2  |
    |Przełączanie kontekstu  |0,4  |
    |Odpowiedź przerwania  |0,0 – 0,6  |

    *Wyniki *w oparciu o typowy procesor działający pod adresem 200MHz*.

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Wstępnie certyfikowane przez TUV i UL do wielu standardów bezpieczeństwa

Usługi Azure RTO ThreadX i Azure RTO ThreadX SMP zostały certyfikowane przez moimi-TUV Saar do użycia w systemach o krytycznym znaczeniu bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-50128 26262 62304. Certyfikat potwierdza, że usługi Azure RTO ThreadX i Azure RTO ThreadX SMP mogą być używane w celu rozwoju oprogramowania związanego z bezpieczeństwem na najwyższym poziomie integralności systemów IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemu związanego z bezpieczeństwem". MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, sprawdzania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które pochodzą z niego, w tym IEC-62304, ISO 26262 i EN 50128, służą do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="MOIMI TUV SAAR":::

Usługa Azure RTO ThreadX i usługa Azure RTO ThreadX SMP zostały rozpoznane przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku H, CSA E60730-1 załącznik H, IEC 1998 60335-1 60335-1 60730-1, UL to globalna, niezależna firma zajmująca się ochroną bezpieczeństwa, która ma więcej niż wiek fachowych rozwiązań w zakresie bezpieczeństwa, od publicznego wdrożenia energii elektrycznej, aby nawiązać przełom w zakresie trwałości, odnawialnych energii i nanotechnologii.

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="Certyfikat UL":::

Artefakty (certyfikat, Podręcznik bezpieczeństwa, raport testowy itp.) skojarzone z certyfikatami TUV i UL są dostępne do sprzedaży.

## <a name="eal4-common-criteria-security-certification"></a>Criteria EAL4 + typowe kryteria certyfikacji zabezpieczeń

Usługa Azure RTO uzyskała certyfikaty zabezpieczeń Criteria EAL4 + Common kryteria. Obiekt docelowy evalution (TOE) obejmuje platformę Azure RTO ThreadX, Azure RTO NetX-Duo, Azure RTO NetX Secure TLS i Azure RTO NetX MQTT. Reprezentuje to najbardziej typowe protokoły IoT wymagane przez głęboko osadzone czujniki, urządzenia, routery brzegowe i bramy.

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="Certyfikat EAL":::

Funkcja oceny zabezpieczeń IT używana na potrzeby certyfikacji usługi Azure RTO Security ma Brightsight BV i urząd certyfikacji to SERTIT.

## <a name="simple-easy-to-use"></a>Proste i łatwe w użyciu

Korzystanie z usługi Azure RTO ThreadX jest bardzo proste. Interfejs API usługi Azure RTO ThreadX jest intuicyjny i wysoce funkcjonalny. Nazwy interfejsów API są prawdziwymi wyrazami, a nie alfabetem (zup) o silnie skróconych nazwach, które są powszechnie używane w innych produktach RTO. Wszystkie interfejsy API usługi Azure RTO ThreadX mają wiodące `tx_` i zgodne konwencje nazewnictwa czasowników. Ponadto istnieje spójność funkcjonalna w całym interfejsie API. Na przykład wszystkie interfejsy API, które zawieszają się, mają opcjonalny limit czasu, który działa w taki sam sposób w przypadku interfejsów API.

Tworzenie aplikacji usługi Azure RTO ThreadX jest proste. Aplikacja musi uwzględniać *tx_api. h*, wywoływać `tx_kernel_enter` z Main, definiować `tx_application_define` funkcję i tworzyć jeden wątek, definiować funkcję punktu wejścia wątku oraz łączyć się z biblioteką ThreadX usługi Azure RTO (zazwyczaj *TX. a*).

Usługa Azure RTO ThreadX także boasts najwyższy Caliber dostępnych dokumentów. 

## <a name="advanced-technology"></a>Technologia zaawansowana

Usługa Azure RTO ThreadX jest zaawansowaną technologią, której najbardziej istotną funkcją jest zastępujące planowanie progowe. Ta funkcja jest unikatowa dla usługi Azure RTO ThreadX i była przedmiotem obszernych badań akademickich. Na przykład zapoznaj się z tematem [planowanie Fixed-Priority zadań z progiem](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)przekroczenia, Yun Wang, Concordia University i Manas Saksena, University of Pittsburgh.

Weź pod uwagę możliwości usługi Azure RTO ThreadX:

* Kompletne i kompleksowe funkcje wielu zadań
  * Wątki, czasomierze aplikacji, kolejki komunikatów, zliczanie semaforów, muteksy, flagi zdarzeń, Pule pamięci blokowej i bajtowej
* Priority-Based planowanie zastępujące
* Elastyczność o priorytecie do 1024 poziomów priorytetów
* Planowanie współpracy
* ™ Progu zastępujący — unikatowy dla usługi Azure RTO ThreadX, pomaga ograniczyć przełączenia kontekstu i pomóc w zapewnieniu schedulability (na potrzeby badań akademickich)
* Ochrona pamięci za pomocą modułów ThreadX usługi Azure RTO
* W pełni deterministyczny
* Śledzenie zdarzeń — Przechwyć ostatnie *n* zdarzeń systemowych/aplikacji
* Tworzenie łańcucha zdarzeń™ — rejestrowanie funkcji wywołania zwrotnego "powiadamiania" dotyczącej określonych aplikacji dla każdego obiektu komunikacji lub synchronizacji usługi Azure RTO ThreadX
* Moduły ThreadX usługi Azure RTO z opcjonalną ochroną pamięci
* Metryki wydajności Run-Time
  * Liczba wznowień wątków
  * Liczba zawieszeń wątków
  * Liczba zastępujący żądania wątku
  * Liczba asynchronicznych przerwań wątku
  * Liczba niewersji priorytetu wątku
  * Liczba zrzeka się wątków
* Zestaw profilów wykonywania (EPK)
* Oddzielny stos przerwań
* Analiza stosu Run-Time
* Zoptymalizowane przetwarzanie przerwań czasomierza

## <a name="multicore-support-amp--smp"></a>Obsługa wielordzeniowa (AMP & SMP)

Standardowa usługa Azure RTO ThreadX jest często używana w przypadku asymetrycznego przetwarzania wieloprocesowego (AMP), gdzie oddzielna kopia usługi Azure RTO ThreadX i aplikacji (lub Linux) jest uruchamiana na poszczególnych rdzeńch i komunikuje się ze sobą za pośrednictwem pamięci współdzielonej lub mechanizmu komunikacji między procesorami, takiego jak OpenAMP (platforma Azure RTO ThreadX obsługuje OpenAMP). Jest to najbardziej Typowa konfiguracja wielordzeniowa korzystająca z usługi Azure RTO ThreadX i może być najbardziej wydajna, jeśli aplikacja jest w stanie skutecznie ładować procesory.

W przypadku środowisk, w których ładowanie procesorów jest wysoce dynamiczne, usługa Azure RTO ThreadX symetrycznego wiele procesów (SMP) jest dostępna dla następujących rodzin procesorów:

* Cortex-Ax ARM
* Cortex-Rx ARM
* ARM Cortex-A5x 64-bit
* MIPS 34K, 1004K i interAptiv
* PowerPC
* SynopSYS łuk HS
* x86

Usługa Azure RTO ThreadX SMP przeprowadza dynamiczne Równoważenie obciążenia na *n* procesorach i umożliwia dostęp do wszystkich zasobów usługi Azure RTO ThreadX (kolejek, semaforów, flag zdarzeń, pul pamięci itp.) przy użyciu dowolnego wątku na dowolnym rdzeniu. Usługa Azure RTO ThreadX SMP umożliwia kompletny interfejs API usługi Azure RTO ThreadX na wszystkich rdzeniach i wprowadza następujący nowy interfejs API dotyczący operacji SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Ochrona pamięci za pomocą modułów ThreadX usługi Azure RTO

Produkt dodatkowy o nazwie Azure RTO ThreadX MODULEs umożliwia dołączenie co najmniej jednego wątku aplikacji do "modułu", który może być dynamicznie ładowany i uruchamiany (lub wykonywany w miejscu) na serwerze docelowym.

Moduły umożliwiają uaktualnianie pól, naprawianie błędów i partycjonowanie programów, aby umożliwić duże aplikacje zajmowanie tylko pamięci wymaganej przez aktywne wątki.

Moduły mają również całkowicie oddzielną przestrzeń adresową z usługi Azure RTO ThreadX. Dzięki temu usługa Azure RTO ThreadX może umieścić ochronę pamięci (za pośrednictwem MPU lub pamięcią) wokół modułu, tak że przypadkowe uzyskanie dostępu poza modułem nie będzie mogło uszkodzić żadnego innego składnika oprogramowania.

## <a name="fastest-time-to-market"></a>Najszybszy czas wprowadzenia na rynek

Usługa Azure RTO ThreadX jest łatwa do zainstalowania, uczenia się, używania, debugowania, weryfikowania, certyfikowania i konserwowania. W związku z tym usługa Azure RTO ThreadX była wiodącym RTOem czasu na rynku w ciągu ostatnich siedmiu kolejnych lat w ramach ankiety dla osadzonych prognoz rynkowych (EMF). Ankiety regularnie pokazują, że 70% projektów korzystających z usługi Azure RTO ThreadX na rynku — przekroczenie wszystkich innych RTOSes.

Poniżej przedstawiono przyczyny spójnego czasu na korzystanie z usługi:

* Dokumentacja dotycząca jakości
* Ukończ dostępność kodu źródłowego
* Łatwy w użyciu interfejs API
* Kompleksowy i zaawansowany zestaw funkcji
* Integracja z szeroką liczbą narzędzi innych firm — szczególnie IAR osadzonych Workbench™

## <a name="royalty-free"></a>Bezpłatnie

Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.

## <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy o najwyższej jakości

Od bardzo początku usługa Azure RTO ThreadX została zaprojektowana jako Klasa branżowa RTO, dystrybuowana z pełnym kodem źródłowym języka C. Kod źródłowy usługi Azure RTO ThreadX ustawił na pasku jakość i łatwość interpretacji. Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.

Usługa Azure RTO ThreadX jest zgodna z rygorystycznymi konwencjami kodowania, włącznie z wymaganiem, że każdy wiersz kodu języka C ma znaczący komentarz. Ponadto Źródło ThreadX usługi Azure RTO zostało certyfikowane do najwyższych standardów.

## <a name="misra-compliant"></a>Zgodne MISRA

Usługa Azure RTO ThreadX i usługa Azure RTO ThreadX SMP Źródło są zgodne z MISRA-C:2004 i MISRA C:2012. MISRA C to zestaw wytycznych programistycznych dotyczących krytycznych systemów przy użyciu języka programowania C. Oryginalne wytyczne dotyczące języka MISRA C były głównie przeznaczone do aplikacji motoryzacyjnych; jednak MISRA C jest teraz szeroko uznawane za mające zastosowanie do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa. Usługa Azure RTO ThreadX jest zgodna ze wszystkimi wymaganymi i obowiązkowymi regułami MISRA-C:2004 i MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certyfikat Misra":::

## <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Usługa Azure RTO ThreadX działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, w tym:

* Urządzenia analogowe: SHARC, Blackfin, CM4xx
* Andes rdzeń: RISC-V
* Ambiqmicro: Apollo MCUs
* ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M
* Erze: Xtensa, romb
* CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED Wi-Fi
* Cypress: RISC-V
* EnSilica: eSi-RISC
* Infineon: XMC1000, XMC4000, TriCore
* Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10
* Chip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32
* Mikrośrednik: RISC-V
* NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4
* Renesas: SH, HS, V850, RX, RZ, synergia
* Krzem Labs: EFM32
* SynopSYS: ARC 600, 700, łuk EM, łuk HS
* ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7
* : C5xxx, C6xxx, Stellaris, Sitara, Tiva-C
* Przetwarzanie Wave: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5 K, microAptiv, interAptiv, proAptiv, Klasa M
* Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="supports-most-popular-tools"></a>Obsługuje najpopularniejsze narzędzia

Usługa Azure RTO ThreadX obsługuje najpopularniejsze, osadzone narzędzia programistyczne, w tym IAR osadzonych Workbench™, które również mają najbardziej kompleksową świadomość jądra platformy Azure RTO. Dodatkowa Integracja narzędzi obejmuje GNU (w zatoce), ARM DS-5/uVision®, zielony Hills®, wiatr rzeki Workbench™, wyobraźnię Codescape, Renesas e2studio, meta-™ SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogowe.
