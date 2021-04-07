---
title: Rozdział 2 — Instalacja & użycie usługi Azure RTO ThreadX SMP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem jądra SMP HighPerformance Azure RTO ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cc352ebd7965c84c341d25dfa7bff2671dfb5e66
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550256"
---
# <a name="chapter-2---installation--use-of-azure-rtos-threadx-smp"></a>Rozdział 2 — Instalacja & użycie usługi Azure RTO ThreadX SMP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem jądra SMP HighPerformance Azure RTO ThreadX.

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Oprogramowanie osadzone jest zazwyczaj opracowywane na komputerach hostów z systemem Windows lub Linux (UNIX). Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzi programistycznych. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM). Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem). Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy ThreadX SMP jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

> [!IMPORTANT]
> Zapoznaj się z podanym plikiem **readme_threadx.txt** , aby uzyskać dodatkowe zagadnienia i opcje systemu hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

ThreadX SMP wymaga od 2 KB i 20 kilobajtów pamięci tylko do odczytu (ROM) w miejscu docelowym. Dla stosu systemu ThreadX SMP i innych globalnych struktur danych wymagane są inne od 1 do 2 KB pamięci RAM docelowego.

W przypadku funkcji związanych z czasomierzem, takich jak limity czasu wywołań usługi, wyróżnianie czasu i czasomierze aplikacji do działania, podstawowy sprzęt docelowy musi dostarczyć okresowe Źródło przerwań. Jeśli procesor ma tę możliwość, jest używany przez ThreadX SMP. W przeciwnym razie, jeśli procesor docelowy nie ma możliwości wygenerowania okresowego przerwania, sprzęt użytkownika musi go udostępnić. Instalacja i konfiguracja przerwania czasomierza zwykle znajduje się w pliku zestawu ***tx_initialize_low_level*** w dystrybucji SMP ThreadX.

> [!IMPORTANT]
> ThreadX SMP jest nadal funkcjonalny, nawet jeśli nie jest dostępne żadne okresowe Źródło przerwań czasomierza. Jednak żadna z usług związanych z czasomierzem nie działa. Zapoznaj się z podanym plikiem **readme_threadx.txt** , aby uzyskać dodatkowe zagadnienia i/lub Opcje systemu hosta.

## <a name="product-distribution"></a>Dystrybucja produktu

Dokładna zawartość dysku dystrybucji zależy od docelowego procesora, narzędzi programistycznych i zakupionego pakietu SMP ThreadX. Poniżej przedstawiono jednak listę kilku ważnych plików, które są wspólne dla większości dystrybucji produktu:

### <a name="threadx_express_startuppdf"></a>ThreadX_Express_Startup.pdf

Ten plik PDF zawiera prostą, czwartą procedurę do uzyskania ThreadX SMP działającego na określonym docelowym procesorze/płycie i określonych narzędziach programistycznych.

### <a name="readme_threadxtxt"></a>readme_threadx.txt

Plik tekstowy zawierający określone informacje o porcie SMP ThreadX, w tym informacje o procesorze docelowym i narzędziach programistycznych.

| Narzędzie | Opis |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **tx_api. h**  | Plik nagłówkowy języka C zawierający wszystkie równe systemowe, struktury danych i prototypy usługi.             |
| **tx_port. h** | Plik nagłówkowy języka C zawierający wszystkie definicje i targetspecific danych. |
|**demo_threadx. c**| Plik C zawierający małą aplikację demonstracyjną.|
|**TX. a (lub TX. lib)**| Wersja binarna biblioteki ThreadX SMP C, która jest dystrybuowana z pakietem *standardowym* .|

> [!IMPORTANT]
> Wszystkie nazwy plików są w małych przypadkach. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy deweloperskie systemu Linux (UNIX).

## <a name="threadx-smp-installation"></a>Instalacja ThreadX SMP

Instalacja ThreadX SMP jest prosta. Zapoznaj się z plikiem ***ThreadX_Express_Startup.pdf** _ i _ *_readme_threadx.txt_**, aby uzyskać szczegółowe informacje dotyczące instalowania ThreadX SMP dla danego środowiska.

> [!IMPORTANT]
> Koniecznie Utwórz kopię zapasową dysku dystrybucji SMP ThreadX i Zapisz go w bezpiecznym miejscu.

> [!IMPORTANT]
> Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki SMP ThreadX (zazwyczaj **TX. a** lub **TX. lib**) i plików dołączanych C **tx_api. h** i **tx_port. h**. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do obszaru projektowania aplikacji.

## <a name="using-threadx-smp"></a>Korzystanie z ThreadX SMP

Korzystanie z ThreadX SMP jest proste. W zasadzie kod aplikacji musi zawierać ***tx_api. h** _ podczas kompilacji i połączyć się z biblioteką czasu wykonywania SMP ThreadX _*_. a_*_ (lub _ *_TX. lib)_* *.

Do utworzenia aplikacji ThreadX SMP wymagane są cztery kroki:

Uwzględnij plik ***tx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług ThreadX SMP lub struktur danych.

Utwórz funkcję standard C ***Main** _. Ta funkcja musi ostatecznie wywołać _ *_tx_kernel_enter_**, aby rozpocząć ThreadX SMP. Inicjowanie specyficzne dla aplikacji, które nie obejmuje ThreadX SMP, można dodać przed wprowadzeniem jądra.

> [!IMPORTANT]
> Funkcja wejścia ThreadX SMP **tx_kernel_enter** nie zwraca. Upewnij się, że nie należy umieszczać żadnego wywołania ani wywołań funkcji.

Utwórz funkcję ***tx_application_define*** . Jest to miejsce, w którym są tworzone początkowe zasoby systemowe. Przykładami zasobów systemowych są wątki, kolejki, Pule pamięci, grupy flag zdarzeń, muteksy i semafory.

Skompiluj Źródło aplikacji i połącz ją ***z biblioteką*** uruchomieniową SMP ThreadX. Obraz wyników można pobrać do elementu docelowego i wykonać!

## <a name="small-example-system"></a>Mały przykładowy system

Mały przykładowy system na rysunku 1 na stronie 28 pokazuje, jak utworzyć pojedynczy wątek z priorytetem 3. Wątek wykonuje, zwiększa licznik, a następnie uśpienia dla jednego zegara. Ten proces kontynuuje się bez ograniczeń.

```c
#include              "tx_api.h"

unsigned long         my_thread_counter = 0;
TX_THREAD             my_thread;

main( )
{
      /* Enter the ThreadX SMP kernel. */
      tx_kernel_enter( );
}

void tx_application_define(void *first_unused_memory)
{

      /* Create my_thread! */
      tx_thread_create(&my_thread, "My Thread",
          my_thread_entry, 0x1234, first_unused_memory, 1024,
             3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}

void my_thread_entry(ULONG thread_input)
{
      /* Enter into a forever loop. */
      while(1)
      {

            /* Increment thread counter. */
            my_thread_counter++;

            /* Sleep for 1 tick. */
            tx_thread_sleep(1);
      }
}
```
**RYSUNEK 1. Szablon opracowywania aplikacji**

Chociaż jest to prosty przykład, zapewnia dobry szablon do rzeczywistego opracowywania aplikacji. Jeszcze raz zapoznaj się z plikiem ***readme_threadx.txt*** , aby uzyskać dodatkowe informacje.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port SMP ThreadX jest dostarczany z aplikacją demonstracyjną. Zawsze dobrym pomysłem jest uzyskanie uruchomionego systemu demonstracyjnego — na rzeczywistym sprzęcie docelowym lub symulowanym środowisku.

> [!IMPORTANT]
> Zapoznaj się z plikiem **readme_threadx.txt** dostarczonym z dystrybucją, aby uzyskać bardziej szczegółowe informacje dotyczące systemu demonstracyjnego.

Jeśli system demonstracyjny nie działa prawidłowo, poniżej przedstawiono niektóre wskazówki dotyczące rozwiązywania problemów:

  - Określ, jaka część demonstracji jest uruchamiana — Ning.

  - Zwiększ rozmiary stosu (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w przypadku pokazu).

  - Skompiluj ponownie bibliotekę SMP ThreadX z definicją TX_ENABLE_STACK_CHECKING. Spowoduje to włączenie wbudowanego sprawdzania stosu SMP ThreadX.

  - Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie. Takie informacje powinny być przydatne do obsługi inżynierów.

Wykonaj procedury opisane w sekcji "czego potrzebujemy" na stronie 12, aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki SMP ThreadX i aplikacji przy użyciu ThreadX SMP istnieje kilka opcji konfiguracji. Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w pliku ***tx_user. h*** .

> [!IMPORTANT]
> Opcje zdefiniowane w **tx_user. h** są stosowane tylko wtedy, gdy biblioteka SMP aplikacji i ThreadX została skompilowana przy użyciu zdefiniowanej **TX_INCLUDE_USER_DEFINE_FILE** .

### <a name="smallest-configuration"></a>Najmniejsza konfiguracja
W przypadku najmniejszego rozmiaru kodu należy wziąć pod uwagę następujące opcje konfiguracji SMP ThreadX (w przypadku braku wszystkich innych opcji):

- TX_DISABLE_ERROR_CHECKING
- TX_DISABLE_PREEMPTION_THRESHOLD
- TX_DISABLE_NOTIFY_CALLBACKS 
- TX_DISABLE_REDUNDANT_CLEARING 
- TX_DISABLE_STACK_FILLING 
- TX_NOT_INTERRUPTABLE 
- TX_TIMER_PROCESS_IN_ISR

### <a name="fastest-configuration"></a>Najszybsza konfiguracja 
Dla najszybszych wykonań te same opcje konfiguracji, które są używane dla najmniejszej konfiguracji wcześniej, ale z tą opcją również są brane pod uwagę:

- TX_REACTIVATE_INLINE

Zapoznaj się z plikiem ***readme_threadx.txt*** , aby uzyskać dodatkowe opcje dla określonej wersji ThreadX SMP. Szczegółowe opcje konfiguracji przedstawiono na stronie 28.

### <a name="global-time-source"></a>Globalne źródło czasu  
W przypadku innych produktów platformy Azure RTO (FileX, NetX, GUIX, USBX itp.), ThreadX SMP definiuje liczbę cykli czasomierza, który reprezentuje jedną sekundę. Inne korzystają z własnych wymagań czasowych na podstawie tej stałej. Wartością domyślną jest 100, przy założeniu, że 10 ms okresowe przerwanie. Użytkownik może zastąpić tę wartość, definiując TX_TIMER_TICKS_PER_SECOND przy użyciu żądanej wartości w ***tx_port. h*** lub w środowisku IDE lub w wierszu polecenia.

### <a name="detailed-configuration-options"></a>Szczegółowe opcje konfiguracji

- **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu, umożliwia gromadzenie informacji o wydajności dla pul bloku. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu włącza zbieranie informacji o wydajności w pulach bajtów. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_ERROR_CHECKING**: pomija sprawdzanie błędów wywołania usługi podstawowej. W przypadku zdefiniowania w źródle aplikacji wszystkie podstawowe sprawdzanie błędów parametrów jest wyłączone. Może to zwiększyć wydajność o nawet 30% i może również zmniejszyć rozmiar obrazu.

> [!NOTE]
> *Wyłączenie sprawdzania błędów jest możliwe tylko wtedy, gdy aplikacja może całkowicie zagwarantować, że wszystkie parametry wejściowe są zawsze ważne we wszystkich okolicznościach, włącznie z parametrami wejściowymi pochodzącymi z zewnętrznych danych wejściowych. Jeśli do interfejsu API dostarczono nieprawidłowe dane wejściowe z wyłączonym sprawdzaniem błędów, Wynikowe zachowanie jest niezdefiniowane i może skutkować uszkodzeniem pamięci lub awarią systemu.*

> [!NOTE]
> *Wartości zwracane przez interfejs API SMP ThreadX nie mają wpływ na wyłączanie sprawdzania błędów są wyświetlane pogrubione w sekcji "wartości zwracane" w opisie interfejsu API w rozdziale 4. Wartości zwrotne Niepogrubione są puste, jeśli sprawdzanie błędów jest wyłączone przy użyciu opcji TX_DISABLE_ERROR_CHECKING.*
- **TX_DISABLE_NOTIFY_CALLBACKS** : po zdefiniowaniu wyłącza powiadamianie wywołania zwrotnego dla różnych ThreadXych obiektów SMP. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_PREEMPTION_THRESHOLD** : gdy jest zdefiniowany, wyłącza funkcję progu zastępują i nieco zmniejsza rozmiar kodu i zwiększa wydajność. Oczywiście możliwości preemptionthreshold nie są już dostępne. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_REDUNDANT_CLEARING** : po zdefiniowaniu, usuwa logikę do inicjowania ThreadX SMP Global C struktur danych w wartości zero. Ta wartość powinna być używana tylko wtedy, gdy kod inicjalizacji kompilatora ustawi wszystkie niezainicjowane dane globalne języka C na zero. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność podczas inicjacji. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_STACK_FILLING** : gdy jest zdefiniowany, wyłącza umieszczanie wartości 0xEF w każdym bajcie stosu każdego wątku po utworzeniu. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_ENABLE_EVENT_TRACE** : po zdefiniowaniu ThreadX SMP włącza kod zbierający zdarzenia do tworzenia buforu śledzenia TraceX. Więcej informacji można znaleźć w podręczniku użytkownika TraceX.
- **TX_ENABLE_STACK_CHECKING** : Jeśli jest zdefiniowany, włącza sprawdzanie sterty czasu wykonywania SMP ThreadX, która obejmuje analizę ilości stosu i badania wzorców danych "ogrodzenia" przed i po obszarze stosu. W przypadku wykrycia błędu stosu zostanie wywołana zarejestrowana procedura obsługi błędów stosu aplikacji. Ta opcja powoduje nieco zwiększone obciążenie i rozmiar kodu. Aby uzyskać więcej informacji, zapoznaj się z interfejsem API **_tx_-thread_stack_error_notify_** . Domyślnie ta opcja nie jest zdefiniowana.
- **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu włącza zbieranie informacji o wydajności w grupach flag zdarzeń. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_INLINE_THREAD_RESUME_SUSPEND** : po zdefiniowaniu ThreadX SMP ulepsza **_tx_thread_resume_*_ i _*_tx_thread_suspend_** wywołań interfejsu API za pośrednictwem kodu w wierszu. Zwiększa to rozmiar kodu, ale zwiększa wydajność tych dwóch wywołań interfejsu API.
- **TX_MAX_PRIORITIES** : definiuje poziomy priorytetów dla ThreadX SMP. Wartości prawne mieszczą się w zakresie od 32 do 1024 (włącznie) i muszą być równo widoczne przez 32. Zwiększenie liczby obsługiwanych poziomów priorytetów zwiększa użycie pamięci RAM o 128 bajtów dla każdej grupy priorytetów 32. Istnieje jednak tylko znaczący wpływ na wydajność. Domyślnie ta wartość jest ustawiana na 32 poziomów priorytetów.
- **TX_MINIMUM_STACK** : określa minimalny rozmiar stosu (w bajtach). Służy do sprawdzania błędów podczas tworzenia wątków. Wartość domyślna to specyficzny dla portu i znajduje się w **_tx_port. h._**
- **TX_MISRA_ENABLE** : w przypadku określenia ThreadX SMP wykorzystuje konwencje zgodne z Misra C. Aby uzyskać szczegółowe informacje, zobacz **_ThreadX_MISRA_Compliance.pdf_** .
- **TX_MUTEX_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu włącza zbieranie informacji o wydajności dla muteksów. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_NO_TIMER** : po zdefiniowaniu logika czasomierza SMP ThreadX jest całkowicie wyłączona. Jest to przydatne w przypadku, gdy nie są używane funkcje czasomierza SMP (ThreadX) (tryb uśpienia wątku, przekroczenie limitu czasu interfejsu API, skalowanie czasu i użycie czasomierza aplikacji).
- **TX_NOT_INTERRUPTABLE** : po zdefiniowaniu ThreadX SMP nie próbuje zminimalizować czasu blokady przerwań. Powoduje to szybsze wykonywanie, ale nieco wydłuża czas blokady przerwań.
- **TX_QUEUE_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu włącza zbieranie informacji o wydajności w kolejkach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_REACTIVATE_INLINE** : po zdefiniowaniu program przeprowadza ponowną aktywację ThreadXych czasomierzy SMP w trybie online zamiast używać wywołania funkcji. Poprawia to wydajność, ale nieco zwiększa rozmiar kodu. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu, umożliwia gromadzenie informacji o wydajności dla semaforów. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_THREAD_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu, umożliwia gromadzenie informacji o wydajności w wątkach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_THREAD_SMP_CORE_MASK** : Określa maskę mapy bitowej dla wykluczenia rdzenia. Na przykład środowisko 4-podstawowe ma wartość 0xF dla tego elementu.
- **TX_THREAD_SMP_DEBUG_ENABLE** : po zdefiniowaniu ThreadX informacje debugowania SMP są zapisywane w buforze cyklicznym.
- **TX_THREAD_SMP_DYNAMIC_CORE_MAX** : po zdefiniowaniu włącza dynamiczną maksymalną liczbę rdzeni, które można dostosować w czasie wykonywania.
- **TX_THREAD_SMP_EQUAL_PRIORITY** : po zdefiniowaniu ThreadX SMP tylko planuje współbieżne wątki o równym priorytecie. Ta wartość powinna być zdefiniowana przed utworzeniem biblioteki SMP ThreadX.
- **TX_THREAD_SMP_INTER_CORE_INTERRUPT** : po zdefiniowaniu ThreadX SMP generuje przerwania między rdzeniami.
- **TX_THREAD_SMP_MAX_CORES** : określa maksymalną liczbę rdzeni.
- **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT** : po zdefiniowaniu ThreadX wartość domyślna wszystkich wątków i czasomierzy do wykonania domyślnie tylko na rdzeńch 0. Aplikacja może zastąpić ten program, wywołując podstawowe interfejsy API wykluczenia. Ta wartość powinna być zdefiniowana przed utworzeniem biblioteki SMP ThreadX.
- **TX_THREAD_SMP_WAKEUP_LOGIC** : po zdefiniowaniu zostanie wywołane makro aplikacji w celu wznowienia rdzenia "i". Należy ją zdefiniować przed włączeniem **_tx_port. h._**
- **TX_THREAD_SMP_WAKEUP (i)** : definiuje makro aplikacji w celu wznowienia rdzenia "i". Należy ją zdefiniować przed włączeniem **_tx_port. h._**
- **TX_TIMER_ENABLE_PERFORMANCE_INFO** : po zdefiniowaniu, umożliwia gromadzenie informacji o wydajności na czasomierzach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_TIMER_PROCESS_IN_ISR** : gdy jest zdefiniowany, eliminuje wewnętrzny wątek czasomierza systemu dla ThreadX SMP. Powoduje to zwiększenie wydajności zdarzeń czasomierza i mniejszych wymagań dotyczących pamięci RAM, ponieważ stos czasomierzy i blok sterowania nie są już potrzebne. Jednak użycie tej opcji przenosi wszystkie operacje przetwarzania wygaśnięcia czasomierza do poziomu ISR czasomierza. Domyślnie ta opcja nie jest zdefiniowana.

    > [!NOTE]
    > Usługi dozwolone z czasomierzy mogą nie być dozwolone z procedury ISR i w ten sposób mogą być niedozwolone w przypadku korzystania z tej opcji.

- **TX_TIMER_THREAD_PRIORITY** : określa priorytet wewnętrznego wątku czasomierza systemu SMP ThreadX. Wartość domyślna to priorytet 0 — najwyższy priorytet w ThreadX SMP. Wartość domyślna jest definiowana w **_tx_port. h._**
- **TX_TIMER_THREAD_STACK_SIZE** : Określa rozmiar stosu (w bajtach) wewnętrznego wątku czasomierza systemu SMP ThreadX. Ten wątek przetwarza wszystkie żądania uśpienia wątku, a także wszystkie limity czasu wywołań usługi. Ponadto wszystkie procedury wywołania zwrotnego czasomierza aplikacji są wywoływane z tego kontekstu. Wartość domyślna to specyficzny dla portu i znajduje się w **_tx_port. h._**

## <a name="threadx-smp-version-id"></a>Identyfikator wersji ThreadX SMP

Identyfikator wersji SMP ThreadX można znaleźć w pliku ***readme_threadx.txt** _. Ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję SMP ThreadX, sprawdzając ciąg globalny _ _ *_tx_version_id._**