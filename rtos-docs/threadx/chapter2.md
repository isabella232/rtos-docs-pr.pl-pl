---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS ThreadX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem jądra ThreadX o wysokiej Azure RTOS wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a88dc75c3b01e8054f72b3e1475791f064eac0ded02b22ccd18dd46da8c7200a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785043"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS ThreadX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem jądra ThreadX o wysokiej Azure RTOS wydajności.

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Oprogramowanie osadzone jest zwykle opracowywane na komputerach Windows komputerach hostów z systemem Linux (Unix). Gdy aplikacja zostanie skompilowana, połączona i zlokalizowana na hoście, zostanie pobrana na docelowy sprzęt w celu wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia dewelopera. Po zakończeniu pobierania debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, halt, breakpoint itp.), a także dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi deweloperskie komunikuje się ze sprzętem docelowym za pośrednictwem połączeń debugowania na mikroukładach (OCD), takich jak JTAG (IEEE 1149.1) i tryb debugowania w tle (BDM). Debugerzy komunikują się również ze sprzętem docelowym za pośrednictwem In-Circuit emulacji (ICE). Zarówno połączenia OCD, jak i ICE zapewniają niezawodne rozwiązania z minimalnym wtargnięciem do docelowego oprogramowania rezydatora.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy threadX jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

ThreadX wymaga od 2 KB do 20 KB pamięci tylko do odczytu (ROM) na docelowym. Wymaga również kolejnych 1–2 KB pamięci RAM (Random Access Memory) obiektu docelowego dla stosu systemu ThreadX i innych globalnych struktur danych.

W przypadku funkcji związanych z czasomierzem, takich jak przekierowania wywołań usług, czasomierze czasu i czasomierze aplikacji do działania, podstawowy sprzęt docelowy musi zapewniać okresowe źródło przerwań. Jeśli procesor ma tę możliwość, jest on wykorzystywany przez threadX. W przeciwnym razie, jeśli procesor docelowy nie ma możliwości generowania okresowych przerwań, sprzęt użytkownika musi je udostępnić. Instalacja i konfiguracja przerwań czasomierza zwykle znajduje się w ***tx_initialize_low_level*** pliku zestawu w dystrybucji ThreadX.

> [!NOTE]
> *ThreadX nadal działa, nawet jeśli nie jest dostępne źródło okresowych przerwań czasomierza. Jednak żadna z usług związanych z czasomierzem nie działa.*

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS ThreadX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/threadx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium.

| Pod nazwą | Opis |
|------------------- | ----------- |
| **tx_api.h**                      | Plik nagłówkowy języka C zawierający wszystkie elementy systemowe, struktury danych i prototypy usług.                                                             |
| **tx_port.h**                     | Plik nagłówkowy języka C zawierający wszystkie definicje i struktury danych docelowych i narzędzia deweloperskiego.                                                 |
| **demo_threadx.c**                | Plik C zawierający małą aplikację demonstracyjną.                                                                                                       |
| **tx.a (lub tx.lib)**              | Wersja binarna biblioteki ThreadX C dystrybuowanej za pomocą *pakietu standardowego.*                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>*Wszystkie nazwy plików są małe. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy programowe Linux (Unix).*

## <a name="threadx-installation"></a>Instalacja ThreadX

ThreadX jest instalowany przez klonowanie GitHub repozytorium na maszynę lokalną. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium ThreadX na komputerze.

```c
    git clone https://github.com/azure-rtos/threadx
```

Możesz też pobrać kopię repozytorium przy użyciu przycisku pobierania na stronie GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki ThreadX znajdują się również na pierwszej stronie repozytorium online.

> [!NOTE]
> *Oprogramowanie aplikacji wymaga dostępu do pliku biblioteki ThreadX (zazwyczaj **tx.a** lub **tx.lib),** a pliki dołączane języka C **_tx_api.h_* _ _*_i tx_port.h._*_ Można to osiągnąć, ustawiając odpowiednią ścieżkę dla narzędzi programistyki lub kopiując te pliki do aplikacji deweloperskie area._

## <a name="using-threadx"></a>Korzystanie z ThreadX

Aby można było używać threadX, kod aplikacji musi zawierać plik ***tx_api.h** _ podczas kompilacji i połączyć go z biblioteką uruchomieniową ThreadX _*_tx.a_*_ (lub _*_tx.lib_**).

Do skompilowania aplikacji ThreadX są wymagane cztery kroki.

1. Dołącz plik ***tx_api.h*** do wszystkich plików aplikacji, które używają usług ThreadX lub struktur danych.

1. Utwórz standardową funkcję C ***main** _. Ta funkcja musi ostatecznie wywołać funkcję _ *_tx_kernel_enter_**, aby uruchomić threadX. Inicjowanie specyficzne dla aplikacji, które nie obejmuje ThreadX, może zostać dodane przed wprowadzeniem jądra.

      > [!IMPORTANT]
      > *Funkcja wpisu ThreadX ***tx_kernel_enter** _ nie zwraca. Dlatego pamiętaj, aby nie umieszczać żadnych wywołań przetwarzania lub funkcji po it._

1. Utwórz funkcję ***tx_application_define.*** W tym miejscu są tworzone początkowe zasoby systemowe. Przykłady zasobów systemowych to wątki, kolejki, pule pamięci, grupy flag zdarzeń, mutexe i semafory.

1. Skompiluj źródło aplikacji i połącz je za pomocą biblioteki uruchomieniowej ***ThreadX tx.lib.*** Wynikowy obraz można pobrać do obiektu docelowego i wykonać!

## <a name="small-example-system"></a>Mały przykładowy system

Mały przykładowy system na rysunku 1 przedstawia tworzenie pojedynczego wątku o priorytecie 3. Wątek jest wykonywany, zwiększa licznik, a następnie uśpije jeden takt zegara.
Ten proces będzie kontynuowany w nieskończoność.

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
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

Chociaż jest to prosty przykład, jest to dobry szablon do tworzenia rzeczywistych aplikacji.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port ThreadX jest dostarczany z aplikacją demonstracyjną. Zawsze dobrym pomysłem jest uruchomienie systemu pokazowego — na rzeczywistym sprzęcie docelowym lub w środowisku symulowanym.

Jeśli system pokazowy nie działa prawidłowo, poniżej przedstawiono wskazówki dotyczące rozwiązywania problemów.

1. Określ, jaka część pokazu jest uruchomiona.
1. Zwiększ rozmiary stosów (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w przypadku pokazu).
1. Ponownie skompilować bibliotekę ThreadX przy TX_ENABLE_STACK_CHECKING zdefiniowanych. Umożliwia to wbudowane sprawdzanie stosu ThreadX.
1. Tymczasowo pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem zniknie lub zmieni się. Takie informacje powinny okazać się przydatne dla inżynierów pomocy technicznej.

Postępuj zgodnie z procedurami opisanymi w["Centrum obsługi klienta",](about-this-guide.md#customer-support-center)aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki ThreadX i aplikacji przy użyciu threadX. Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w ***pliku dołączania tx_user.h.***

> [!IMPORTANT]
> *Opcje zdefiniowane w ***tx_user.h** _ są stosowane tylko wtedy, gdy aplikacjai biblioteka ThreadX są budowane za pomocą zdefiniowanego TX_INCLUDE_USER_DEFINE_FILE *.*

### <a name="smallest-configuration"></a>Najmniejsza konfiguracja

W przypadku najmniejszego rozmiaru kodu należy wziąć pod uwagę następujące opcje konfiguracji ThreadX (w przypadku braku wszystkich innych opcji).

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a>Najszybsza konfiguracja

W celu najszybszego wykonania te same opcje konfiguracji, które były wcześniej używane dla najmniejszej konfiguracji, ale z tymi opcjami również zostały rozważone.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

[Opisano szczegółowe opcje](#detailed-configuration-options) konfiguracji.

### <a name="global-time-source"></a>Globalne źródło czasu

W przypadku Microsoft Azure produktów RTOS (FileX, NetX, GUIX, USBX itp.) ThreadX definiuje liczbę znaczników czasomierza ThreadX, które reprezentują jedną sekundę. Inne wyprowadzają swoje wymagania dotyczące czasu na podstawie tej stałej. Domyślnie wartość jest 100, przy założeniu 10ms okresowego przerwania. Użytkownik może zastąpić tę wartość przez zdefiniowanie TX_TIMER_TICKS_PER_SECOND żądaną wartością w ***tx_port.h*** lub w obrębie środowiska IDE lub wiersza polecenia.

### <a name="detailed-configuration-options"></a>Szczegółowe opcje konfiguracji

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Jeśli ta opcja jest zdefiniowana, umożliwia zbieranie informacji o wydajności pul bajtów. Domyślnie ta opcja nie jest zdefiniowana.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Jeśli ta opcja jest zdefiniowana, umożliwia zbieranie informacji o wydajności pul bajtów. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_ERROR_CHECKING**

Pomija sprawdzanie błędów podstawowego wywołania usługi. W przypadku definicji w źródle aplikacji wszystkie podstawowe sprawdzanie błędów parametrów jest wyłączone. Może to poprawić wydajność nawet o 30%, a także zmniejszyć rozmiar obrazu.

> [!NOTE]
> *Można bezpiecznie wyłączyć sprawdzanie błędów tylko wtedy, gdy aplikacja może całkowicie zagwarantować, że wszystkie parametry wejściowe są zawsze prawidłowe we wszystkich okolicznościach, w tym parametry wejściowe pochodzące z zewnętrznych danych wejściowych. Jeśli do interfejsu API zostanie dostarczone nieprawidłowe dane wejściowe z wyłączonym sprawdzaniem błędów, wynikowe zachowanie jest niezdefiniowane i może spowodować uszkodzenie pamięci lub awarię systemu.*

> [!NOTE]
> *Wartości zwracane interfejsu API ThreadX, na które nie ma wpływu wyłączenie sprawdzania błędów, są wyświetlane pogrubioną czcionką w sekcji "Wartości zwracane" każdego opisu interfejsu API w rozdziale 4. Wartości zwracane bezboleczne są unieważnione, jeśli sprawdzanie błędów jest wyłączone przy użyciu TX_DISABLE_ERROR_CHECKING wartości.*

**TX_DISABLE_NOTIFY_CALLBACKS**

Gdy zdefiniowano, wyłącza wywołania zwrotne powiadamiania dla różnych obiektów ThreadX. Użycie tej opcji nieco zmniejsza rozmiar kodu i poprawia wydajność. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_PREEMPTION_THRESHOLD**

Gdy ta funkcja jest zdefiniowana, wyłącza funkcję próg wywłaszczenia i nieco zmniejsza rozmiar kodu i zwiększa wydajność. Oczywiście możliwości progu wywłaszczenia nie są już dostępne. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_REDUNDANT_CLEARING**

Po zdefiniowanym usuwa logikę inicjowania globalnych struktur danych Języka C ThreadX do zera. Tej wartości należy używać tylko wtedy, gdy kod inicjowania kompilatora ustawia wszystkie niez inicjalizowane dane globalne języka C na zero. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność podczas inicjowania. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_STACK_FILLING**

Po zdefiniowanym wyłącza umieszczanie 0xEF w każdym bajtze stosu każdego wątku po utworzeniu. Domyślnie ta opcja nie jest zdefiniowana.

**TX_ENABLE_EVENT_TRACE**

W przypadku definicji ThreadX włącza kod zbierania zdarzeń w celu utworzenia bufora śledzenia TraceX.

**TX_ENABLE_STACK_CHECKING**

Po zdefiniowanym program włącza sprawdzanie stosu w czasie uruchamiania ThreadX, co obejmuje analizę użytego stosu i badanie "ogrodzeń" wzorca danych przed obszarem stosu i po nim. W przypadku wykrycia błędu stosu wywoływana jest procedura obsługi błędów zarejestrowanego stosu aplikacji. Ta opcja powoduje nieco większe obciążenie i rozmiar kodu. Zapoznaj się z ***tx_thread_stack_error_notify*** api, aby uzyskać więcej informacji. Domyślnie ta opcja nie jest zdefiniowana.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

Po zdefiniowanym umożliwia zbieranie informacji o wydajności w grupach flag zdarzeń. Domyślnie ta opcja nie jest zdefiniowana.

**TX_INLINE_THREAD_RESUME_SUSPEND**

Po definicji threadX ulepsza wywołania interfejsu API ***tx_thread_resume** _ i _ *_tx_thread_suspend_** za pośrednictwem kodu w wierszu. Zwiększa to rozmiar kodu, ale zwiększa wydajność tych dwóch wywołań interfejsu API.

**TX_MAX_PRIORITIES**

Definiuje poziomy priorytetów dla ThreadX. Wartości prawne to od 32 do 1024 (włącznie) i muszą być równomiernie podzielne przez 32.  Zwiększenie liczby obsługiwanych poziomów priorytetów zwiększa użycie pamięci RAM o 128 bajtów dla każdej grupy 32 priorytetów. Jednak istnieje tylko niewielki wpływ na wydajność. Domyślnie ta wartość jest ustawiona na 32 poziomy priorytetu.

**TX_MINIMUM_STACK**

Definiuje minimalny rozmiar stosu (w bajtach). Służy do sprawdzania błędów podczas tworzenia wątków. Wartość domyślna jest specyficzna dla portu i znajduje się w ***tx_port.h.***

**TX_MISRA_ENABLE**

W przypadku definicji ThreadX wykorzystuje konwencje zgodne ze standardem MISRA C. Aby uzyskać  ***szczegółoweThreadX_MISRA_Compliance.pdf,*** zapoznaj się zThreadX_MISRA_Compliance.pdftematem.

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

Gdy jest zdefiniowana, umożliwia zbieranie informacji o wydajności w mutexes. Domyślnie ta opcja nie jest zdefiniowana.

**TX_NO_TIMER**

W przypadku definicji logika czasomierza ThreadX jest całkowicie wyłączona. Jest to przydatne w przypadkach, gdy funkcje czasomierza ThreadX (uśpienie wątku, limity czasu interfejsu API, czasomierze czasu i czasomierze aplikacji) nie są używane. Jeśli **TX_NO_TIMER** jest określona, należy **TX_TIMER_PROCESS_IN_ISR** także zdefiniować opcję.

**TX_NOT_INTERRUPTABLE**

W przypadku definicji threadX nie próbuje zminimalizować czasu blokady przerwań. Skutkuje to szybszym wykonywaniem, ale nieco zwiększa czas blokady przerwań.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

Po zdefiniowanym program umożliwia zbieranie informacji o wydajności w kolejkach. Domyślnie ta opcja nie jest zdefiniowana.

**TX_REACTIVATE_INLINE**

Gdy ta funkcja jest zdefiniowana, wykonuje ponowną aktywację czasomierzy ThreadX w tekście zamiast używania wywołania funkcji. Zwiększa to wydajność, ale nieco zwiększa rozmiar kodu. Domyślnie ta opcja nie jest zdefiniowana.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

W przypadku definicji umożliwia zbieranie informacji o wydajności na semaforach. Domyślnie ta opcja nie jest zdefiniowana.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

W przypadku definicji umożliwia zbieranie informacji o wydajności w wątkach. Domyślnie ta opcja nie jest zdefiniowana.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

Gdy ta funkcja jest zdefiniowana, umożliwia zbieranie informacji o wydajności czasomierzy. Domyślnie ta opcja nie jest zdefiniowana.

**TX_TIMER_PROCESS_IN_ISR**

W przypadku definicji eliminuje wewnętrzny wątek czasomierza systemu dla ThreadX. Powoduje to zwiększenie wydajności zdarzeń czasomierza i mniejsze wymagania dotyczące pamięci RAM, ponieważ stos czasomierza i blok sterowania nie są już potrzebne. Jednak użycie tej opcji powoduje przeniesienie całego przetwarzania wygasania czasomierza na poziom czasomierza ISR. Domyślnie ta opcja nie jest zdefiniowana.

> [!NOTE]
> *Usługi dozwolone z czasomierzy mogą być niedozwolone od isR i w związku z tym mogą być niedozwolone w przypadku korzystania z tej opcji.*

**TX_TIMER_THREAD_PRIORITY**

Definiuje priorytet wewnętrznego wątku czasomierza systemu ThreadX. Wartość domyślna to priorytet 0 — najwyższy priorytet w ThreadX. Wartość domyślna jest definiowana ***w tx_port.h.***

**TX_TIMER_THREAD_STACK_SIZE**

Definiuje rozmiar stosu (w bajtach) wewnętrznego wątku czasomierza systemu ThreadX. Ten wątek przetwarza wszystkie żądania uśpienia wątku, a także wszystkie limity czasu wywołań usługi. Ponadto wszystkie procedury wywołania zwrotnego czasomierza aplikacji są wywoływane z tego kontekstu. Wartość domyślna jest specyficzna dla portu i znajduje się w ***tx_port.h.***

## <a name="threadx-version-id"></a>Identyfikator wersji ThreadX

Programista może uzyskać wersję ThreadX z badania pliku ***tx_port.h_.** Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję ThreadX, sprawdzając globalny ciąg _*_tx_version_id**.
