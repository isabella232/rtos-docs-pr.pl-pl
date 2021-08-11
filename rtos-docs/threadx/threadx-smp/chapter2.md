---
title: Rozdział 2 — & użycia Azure RTOS ThreadX SMP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem wysokiej wydajności Azure RTOS SMP ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d0a63f3798adbc634a43cdda7e9d44941de655d9333f9ae0fb4181f1a6c0566e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801907"
---
# <a name="chapter-2---installation--use-of-azure-rtos-threadx-smp"></a>Rozdział 2 — & użycia Azure RTOS ThreadX SMP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem wysokiej wydajności Azure RTOS SMP ThreadX.

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Oprogramowanie osadzone jest zwykle opracowywane na Windows komputerach hostów z systemem Linux (Unix). Gdy aplikacja zostanie skompilowana, połączona i zlokalizowana na hoście, zostanie pobrana na docelowy sprzęt w celu wykonania.

Zazwyczaj pobieranie docelowe jest wykonywane z poziomu debugera narzędzia dewelopera. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, halt, breakpoint itp.), a także dostępu do rejestrów pamięci i procesora.

Większość debugerów narzędzi deweloperskie komunikuje się ze sprzętem docelowym za pośrednictwem połączeń debugowania na mikroukładach (OCD), takich jak JTAG (IEEE 1149.1) i tryb debugowania w tle (BDM). Debugerzy komunikują się również ze sprzętem docelowym za pośrednictwem In-Circuit emulacji (ICE). Połączenia OCD i ICE zapewniają niezawodne rozwiązania z minimalnym wtargnięciem do docelowego oprogramowania.

Podobnie jak w przypadku zasobów używanych na hoście kod źródłowy dla SMP ThreadX jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

> [!IMPORTANT]
> Zapoznaj się z **dostarczonymreadme_threadx.txt,** aby zapoznać się z dodatkowymi zagadnieniami i opcjami systemu hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

ThreadX SMP wymaga od 2 KB do 20 KB pamięci tylko do odczytu (ROM) na docelowym. Kolejne 1–2 KB pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla stosu systemu SMP ThreadX i innych globalnych struktur danych.

W przypadku funkcji związanych z czasomierzem, takich jak przechyły czasu wywołania usługi, czasomierze czasu i czasomierze aplikacji do działania, podstawowy sprzęt docelowy musi zapewniać okresowe źródło przerwań. Jeśli procesor ma tę możliwość, jest ona wykorzystywana przez SMP ThreadX. W przeciwnym razie, jeśli procesor docelowy nie ma możliwości generowania okresowych przerwań, sprzęt użytkownika musi je udostępnić. Instalacja i konfiguracja przerwań czasomierza zwykle znajduje się w ***pliku tx_initialize_low_level*** w dystrybucji SMP ThreadX.

> [!IMPORTANT]
> ThreadX SMP nadal działa, nawet jeśli nie jest dostępne źródło okresowych przerwań czasomierza. Jednak żadna z usług związanych z czasomierzem nie działa. Zapoznaj się z **dostarczonymreadme_threadx.txt,** aby zapoznać się z dodatkowymi zagadnieniami i/lub opcjami systemu hosta.

## <a name="product-distribution"></a>Dystrybucja produktów

Dokładna zawartość dysku dystrybucji zależy od procesora docelowego, narzędzi deweloperskie i zakupionego pakietu SMP ThreadX. Jednak poniżej znajduje się lista kilku ważnych plików, które są wspólne dla większości dystrybucji produktów:

### <a name="threadx_express_startuppdf"></a>ThreadX_Express_Startup.pdf

Ten plik PDF zawiera prostą, czteroetapową procedurę uruchamiania pliku SMP ThreadX na określonym docelowym procesorze/tablicy i określonych narzędziach deweloperskie.

### <a name="readme_threadxtxt"></a>readme_threadx.txt

Plik tekstowy zawierający określone informacje o porcie SMP ThreadX, w tym informacje o procesorze docelowym i narzędziach deweloperskie.

| Narzędzie | Opis |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **tx_api.h**  | Plik nagłówkowy języka C zawierający wszystkie elementy systemowe, struktury danych i prototypy usług.             |
| **tx_port.h** | Plik nagłówkowy języka C zawierający wszystkie definicje i struktury danych dla celów i narzędzia deweloperskiego. |
|**demo_threadx.c**| Plik C zawierający małą aplikację demonstracyjną.|
|**tx.a (lub tx.lib)**| Wersja binarna biblioteki ThreadX SMP C dystrybuowanej za pomocą *pakietu standardowego.*|

> [!IMPORTANT]
> Wszystkie nazwy plików są małe. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy programowe Linux (Unix).

## <a name="threadx-smp-installation"></a>ThreadX SMP Installation

Instalacja SMP ThreadX jest prosta. Zapoznaj się z plikami ***ThreadX_Express_Startup.pdf** _ i _ *_readme_threadx.txt_**, aby uzyskać szczegółowe informacje na temat instalowania threadX SMP dla określonego środowiska.

> [!IMPORTANT]
> Pamiętaj, aby wrócić do kopii zapasowej dysku dystrybucji SMP ThreadX i zapisać go w bezpiecznej lokalizacji.

> [!IMPORTANT]
> Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki SMP ThreadX (zazwyczaj **tx.a** lub **tx.lib),** a pliki dołączane W **tx_api.h** **i tx_port.h**. W tym celu należy wybrać odpowiednią ścieżkę dla narzędzi programistyki lub skopiować te pliki do obszaru projektowania aplikacji.

## <a name="using-threadx-smp"></a>Używanie SMP ThreadX

Korzystanie z SMP ThreadX jest łatwe. Zasadniczo kod aplikacji musi zawierać plik ***tx_api.h** _ podczas kompilacji i łączyć się z biblioteką run-time ThreadX SMP _*_tx.a_*_ (lub _*_tx.lib)_**.

Do skompilowania aplikacji SMP ThreadX wymagane są cztery kroki:

Dołącz plik ***tx_api.h do*** wszystkich plików aplikacji, które używają usług SMP ThreadX lub struktur danych.

Utwórz standardową funkcję C ***main** _. Ta funkcja musi ostatecznie wywołać funkcję _ *_tx_kernel_enter_**, aby uruchomić threadX SMP. Inicjalizacja specyficzna dla aplikacji, która nie obejmuje SMP ThreadX, może zostać dodana przed wprowadzeniem jądra.

> [!IMPORTANT]
> Funkcja wpisu SMP ThreadX **tx_kernel_enter** nie zwraca. Dlatego pamiętaj, aby nie umieszczać za nim żadnych wywołań przetwarzania ani funkcji.

Utwórz funkcję ***tx_application_define.*** W tym miejscu są tworzone początkowe zasoby systemowe. Przykłady zasobów systemowych obejmują wątki, kolejki, pule pamięci, grupy flag zdarzeń, mutexe i semafory.

Skompiluj źródło aplikacji i połącz go za pomocą biblioteki run-time ThreadX SMP ***tx.lib.*** Wynikowy obraz można pobrać do obiektu docelowego i wykonać.

## <a name="small-example-system"></a>Mały przykładowy system

Mały przykładowy system na rysunku 1 na stronie 28 pokazuje utworzenie pojedynczego wątku o priorytecie 3. Wątek wykonuje, zwiększa licznik, a następnie uśpije dla jednego takt zegara. Ten proces będzie kontynuowany w nieskończoność.

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
**RYSUNEK 1. Szablon do tworzenia aplikacji**

Chociaż jest to prosty przykład, jest to dobry szablon do tworzenia rzeczywistych aplikacji. Ponownie zapoznaj się z ***plikiemreadme_threadx.txt,*** aby uzyskać dodatkowe informacje.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port SMP ThreadX jest dostarczany z aplikacją demonstracyjną. Zawsze dobrym pomysłem jest uruchomienie systemu demonstracyjnego — na rzeczywistym sprzęcie docelowym lub w środowisku symulowanym.

> [!IMPORTANT]
> Zobacz plik **readme_threadx.txt** dostarczany z dystrybucją, aby uzyskać bardziej szczegółowe informacje dotyczące systemu pokazowego.

Jeśli system pokazowy nie działa prawidłowo, poniżej przedstawiono wskazówki dotyczące rozwiązywania problemów:

  - Określ, jaka część pokazu to run-ning.

  - Zwiększ rozmiary stosów (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w pokazie).

  - Ponownie skompilować bibliotekę SMP ThreadX TX_ENABLE_STACK_CHECKING zdefiniowane. Umożliwi to wbudowane sprawdzanie stosu SMP ThreadX.

  - Tymczasowo pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub zmienia się. Takie informacje powinny okazać się przydatne dla inżynierów pomocy technicznej.

Postępuj zgodnie z procedurami opisanymi w tece "Czego potrzebujemy od Ciebie" na stronie 12, aby wysłać informacje zebrane w krokach rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki SMP ThreadX i aplikacji przy użyciu narzędzia ThreadX SMP. Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w ***pliku dołączania tx_user.h.***

> [!IMPORTANT]
> Opcje zdefiniowane w **programie tx_user.h** są stosowane tylko wtedy, gdy aplikacja i biblioteka SMP ThreadX **są** budowane TX_INCLUDE_USER_DEFINE_FILE zdefiniowane.

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
W celu najszybszego wykonania te same opcje konfiguracji, które były wcześniej używane dla najmniejszej konfiguracji, ale przy tej opcji również rozważyliśmy:

- TX_REACTIVATE_INLINE

Przejrzyj plik ***readme_threadx.txt,*** aby uzyskać dodatkowe opcje dla określonej wersji pliku SMP ThreadX. Szczegółowe opcje konfiguracji są opisane począwszy od strony 28.

### <a name="global-time-source"></a>Globalne źródło czasu  
W przypadku innych produktów Azure RTOS (FileX, NetX, GUIX, USBX itp.) threadX SMP definiuje liczbę taktów czasomierza SMP ThreadX, które reprezentują jedną sekundę. Inne wyprowadzają swoje wymagania dotyczące czasu na podstawie tej stałej. Domyślnie wartość jest 100 przy założeniu 10ms okresowego przerwania. Użytkownik może zastąpić tę wartość przez zdefiniowanie TX_TIMER_TICKS_PER_SECOND z żądaną wartością w ***tx_port.h*** lub w ide lub wierszu polecenia.

### <a name="detailed-configuration-options"></a>Szczegółowe opcje konfiguracji

- **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO:** Po zdefiniowanym program umożliwia zbieranie informacji o wydajności pul bloków. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO:** po definicji umożliwia zbieranie informacji o wydajności pul bajtów. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_ERROR_CHECKING:** pomija podstawowe sprawdzanie błędów wywołania usługi. W przypadku definicji w źródle aplikacji wszystkie podstawowe sprawdzanie błędów parametrów jest wyłączone. Może to poprawić wydajność nawet o 30%, a także zmniejszyć rozmiar obrazu.

> [!NOTE]
> *Można bezpiecznie wyłączyć sprawdzanie błędów tylko wtedy, gdy aplikacja może całkowicie zagwarantować, że wszystkie parametry wejściowe są zawsze prawidłowe we wszystkich okolicznościach, w tym parametry wejściowe pochodzące z zewnętrznych danych wejściowych. Jeśli do interfejsu API zostanie dostarczone nieprawidłowe dane wejściowe z wyłączonym sprawdzaniem błędów, wynikowe zachowanie jest niezdefiniowane i może spowodować uszkodzenie pamięci lub awarię systemu.*

> [!NOTE]
> *Wartości zwracane interfejsu API SMP ThreadX, na które nie ma wpływu wyłączenie sprawdzania błędów, są wyświetlane pogrubioną czcionką w sekcji "Wartości zwracane" każdego opisu interfejsu API w rozdziale 4. Wartości zwracane bezboleczne są nieważne, jeśli sprawdzanie błędów zostało wyłączone przy użyciu TX_DISABLE_ERROR_CHECKING opcji.*
- **TX_DISABLE_NOTIFY_CALLBACKS:** po definicji program wyłącza wywołania zwrotne powiadamiania dla różnych obiektów SMP ThreadX. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_PREEMPTION_THRESHOLD:** Po definicji wyłącza funkcję próg wywłaszczenia i nieco zmniejsza rozmiar kodu i zwiększa wydajność. Oczywiście możliwości wywłaszcze są już niedostępne. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_REDUNDANT_CLEARING:** w przypadku definicji program usuwa logikę inicjowania globalnych struktur danych SMP ThreadX do zera. Tej opcji należy używać tylko wtedy, gdy kod inicjowania kompilatora ustawia wszystkie nie zainicjowane dane globalne języka C na zero. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność podczas inicjowania. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_DISABLE_STACK_FILLING:** Po zdefiniowanym wyłącza umieszczanie 0xEF w każdym bajtie stosu każdego wątku po utworzeniu. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_ENABLE_EVENT_TRACE:** Po definicji threadX SMP włącza kod zbierania zdarzeń w celu utworzenia buforu śledzenia TraceX. Aby uzyskać więcej informacji, zobacz Podręcznik użytkownika programu TraceX.
- **TX_ENABLE_STACK_CHECKING:** po zdefiniowanym programie włącza sprawdzanie stosu w czasie uruchamiania SMP ThreadX, co obejmuje analizę użytego stosu i badanie "ogrodzeń" wzorca danych przed obszarem stosu i po nim. Jeśli zostanie wykryty błąd stosu, wywoływana jest procedura obsługi błędów zarejestrowanego stosu aplikacji. Ta opcja powoduje nieco większe obciążenie i rozmiar kodu. Aby uzyskać więcej **_informacji, zapoznaj_ się z thread_stack_error_notify_** API tx - thread_stack_error_notify_. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO:** po definicji umożliwia zbieranie informacji o wydajności dla grup flag zdarzeń. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_INLINE_THREAD_RESUME_SUSPEND:** Po zdefiniowany, SMP ThreadX ulepsza wywołania interfejsu API tx_thread_resume _ i ***_*_tx_thread_suspend_** za pośrednictwem kodu w wierszu. Zwiększa to rozmiar kodu, ale zwiększa wydajność tych dwóch wywołań interfejsu API.
- **TX_MAX_PRIORITIES:** definiuje poziomy priorytetów dla SMP ThreadX. Wartości prawne wahają się od 32 do 1024 (włącznie) i muszą być równomiernie podzielne przez 32. Zwiększenie liczby obsługiwanych poziomów priorytetów zwiększa użycie pamięci RAM o 128 bajtów dla każdej grupy 32 priorytetów. Jednak istnieje tylko niewielki wpływ na wydajność. Domyślnie ta wartość jest ustawiona na 32 poziomy priorytetu.
- **TX_MINIMUM_STACK:** definiuje minimalny rozmiar stosu (w bajtach). Służy do sprawdzania błędów podczas tworzenia wątków. Wartość domyślna jest specyficzna dla portu i znajduje się w **_tx_port.h._**
- **TX_MISRA_ENABLE:** Po zdefiniowanym węźle ThreadX SMP wykorzystuje konwencje zgodne ze standardem MISRA C. Zapoznaj się z **_ThreadX_MISRA_Compliance.pdf,_** aby uzyskać szczegółowe informacje.
- **TX_MUTEX_ENABLE_PERFORMANCE_INFO:** Po zdefiniowanym umożliwia zbieranie informacji o wydajności w mutexes. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_NO_TIMER:** po definicji logika czasomierza SMP ThreadX jest całkowicie wyłączona. Jest to przydatne w przypadkach, gdy funkcje czasomierza SMP ThreadX (uśpienie wątku, limity czasu interfejsu API, czasomierze czasu i czasomierze aplikacji) nie są używane.
- **TX_NOT_INTERRUPTABLE:** Po definicji, SMP ThreadX nie próbuje zminimalizować czasu blokady przerwań. Skutkuje to szybszym wykonywaniem, ale nieznacznie zwiększa czas blokady przerwań.
- **TX_QUEUE_ENABLE_PERFORMANCE_INFO:** Po zdefiniowanym program umożliwia zbieranie informacji o wydajności w kolejkach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_REACTIVATE_INLINE:** w przypadku definicji funkcja wykonuje ponowną aktywację czasomierzy SMP ThreadX w wierszu zamiast przy użyciu wywołania funkcji. Zwiększa to wydajność, ale nieco zwiększa rozmiar kodu. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO:** Po definicji umożliwia zbieranie informacji o wydajności na semaforach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_THREAD_ENABLE_PERFORMANCE_INFO:** po definicji umożliwia zbieranie informacji o wydajności w wątkach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_THREAD_SMP_CORE_MASK:** definiuje maskę mapy bitowej dla wykluczenia core. Na przykład środowisko 4-rdzeniowe ma wartość 0xF dla tego zdefiniowania.
- **TX_THREAD_SMP_DEBUG_ENABLE:** po definicji informacje debugowania threadX SMP są zapisywane w buforze cyklicznym.
- **TX_THREAD_SMP_DYNAMIC_CORE_MAX:** Po definicji program włącza dynamiczną maksymalną liczbę rdzeni, które można dostosować w czasie pracy.
- **TX_THREAD_SMP_EQUAL_PRIORITY:** Po definicji threadX SMP planuje równolegle tylko wątki o równym priorytecie. Należy to zdefiniować przed sbudowania biblioteki SMP ThreadX.
- **TX_THREAD_SMP_INTER_CORE_INTERRUPT:** Po zdefiniować, ThreadX SMP generuje przerwań międzyrdzeniowych.
- **TX_THREAD_SMP_MAX_CORES:** definiuje maksymalną liczbę rdzeni.
- **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT:** po definicji SMP ThreadX domyślnie wszystkie wątki i czasomierze są domyślnie wykonywane tylko w rdzeniu 0. Aplikacja może zastąpić to przez wywołanie podstawowych interfejsów API wykluczania. Należy to zdefiniować przed sbudowania biblioteki SMP ThreadX.
- **TX_THREAD_SMP_WAKEUP_LOGIC:** po definicji wywoływane jest makro aplikacji wznawiania rdzenia "i". Należy to zdefiniować przed dodaniem **_tx_port.h._**
- **TX_THREAD_SMP_WAKEUP(i)** : definiuje makro aplikacji, aby wznowić rdzeń "i". Należy to zdefiniować przed dodaniem **_tx_port.h._**
- **TX_TIMER_ENABLE_PERFORMANCE_INFO:** Po definicji umożliwia zbieranie informacji o wydajności na czasomierzach. Domyślnie ta opcja nie jest zdefiniowana.
- **TX_TIMER_PROCESS_IN_ISR:** Po definicji eliminuje wewnętrzny wątek czasomierza systemu dla SMP ThreadX. Powoduje to zwiększenie wydajności zdarzeń czasomierza i mniejsze wymagania dotyczące pamięci RAM, ponieważ stos czasomierza i blok sterujący nie są już potrzebne. Jednak użycie tej opcji powoduje przeniesienie całego przetwarzania wygaśnięcia czasomierza na poziom isr czasomierza. Domyślnie ta opcja nie jest zdefiniowana.

    > [!NOTE]
    > Usługi dozwolone z czasomierzy mogą być niedozwolone od isR i w związku z tym mogą być niedozwolone w przypadku korzystania z tej opcji.

- **TX_TIMER_THREAD_PRIORITY:** definiuje priorytet wewnętrznego wątku czasomierza systemu SMP ThreadX. Wartość domyślna to priority 0 — najwyższy priorytet w threadx SMP. Wartość domyślna jest zdefiniowana w **_tx_port.h._**
- **TX_TIMER_THREAD_STACK_SIZE:** definiuje rozmiar stosu (w bajtach) wewnętrznego wątku czasomierza systemu SMP ThreadX. Ten wątek przetwarza wszystkie żądania uśpienia wątku, a także wszystkie limity czasu wywołania usługi. Ponadto wszystkie procedury wywołania zwrotnego czasomierza aplikacji są wywoływane z tego kontekstu. Wartość domyślna jest specyficzna dla portu i znajduje się w **_tx_port.h._**

## <a name="threadx-smp-version-id"></a>Identyfikator wersji SMP ThreadX

Identyfikator wersji SMP ThreadX można znaleźć w pliku ***readme_threadx.txt** _. Ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję SMP ThreadX, sprawdzając globalny ciąg _ *_ _tx_version_id._**