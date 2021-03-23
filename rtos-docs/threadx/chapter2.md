---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO ThreadX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem jądra usługi Azure RTO ThreadX o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821360"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO ThreadX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem jądra usługi Azure RTO ThreadX o wysokiej wydajności.

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Oprogramowanie osadzone jest zazwyczaj opracowywane na komputerach hostów z systemem Windows lub Linux (UNIX). Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzi programistycznych. Po zakończeniu pobierania debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM). Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem). Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy dla ThreadX jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

ThreadX wymaga od 2 kilobajtów do 20 kilobajtów pamięci tylko do odczytu (ROM) w miejscu docelowym. Wymaga również od 1 do 2 KB pamięci RAM docelowego (Random Access Memory) dla stosu systemu ThreadX i innych globalnych struktur danych.

W przypadku funkcji związanych z czasomierzem, takich jak limity czasu wywołań usługi, wyróżnianie czasu i czasomierze aplikacji do działania, podstawowy sprzęt docelowy musi dostarczyć okresowe Źródło przerwań. Jeśli procesor ma tę możliwość, jest używany przez ThreadX. W przeciwnym razie, jeśli procesor docelowy nie ma możliwości wygenerowania okresowego przerwania, sprzęt użytkownika musi go udostępnić. Instalacja i konfiguracja przerwania czasomierza zwykle znajduje się w pliku zestawu ***tx_initialize_low_level*** w dystrybucji ThreadX.

> [!NOTE]
> *ThreadX nadal działa nawet wtedy, gdy nie jest dostępne żadne okresowe Źródło przerwań czasomierza. Jednak żadna z usług związanych z czasomierzem nie działa.*

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO ThreadX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/threadx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium.

| Nazwa pliku | Opis |
|------------------- | ----------- |
| **tx_api. h**                      | Plik nagłówkowy języka C zawierający wszystkie równe systemowe, struktury danych i prototypy usługi.                                                             |
| **tx_port. h**                     | Plik nagłówkowy języka C zawierający wszystkie definicje i targetspecific danych.                                                 |
| **demo_threadx. c**                | Plik C zawierający małą aplikację demonstracyjną.                                                                                                       |
| **TX. a (lub TX. lib)**              | Wersja binarna biblioteki ThreadX C, która jest dystrybuowana z pakietem *standardowym* .                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>*Wszystkie nazwy plików są w małych przypadkach. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy deweloperskie systemu Linux (UNIX).*

## <a name="threadx-installation"></a>Instalacja ThreadX

ThreadX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium ThreadX na komputerze.

```c
    git clone https://github.com/azure-rtos/threadx
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki ThreadX na stronie frontonu repozytorium online.

> [!NOTE]
> * Oprogramowanie aplikacji wymaga dostępu do pliku biblioteki ThreadX (zazwyczaj **TX. a** lub **TX. lib**) oraz plików C include **_tx_api. h_* _ i _*_tx_port. h_*_. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do area._ tworzenia aplikacji

## <a name="using-threadx"></a>Korzystanie z ThreadX

Aby użyć ThreadX, kod aplikacji musi zawierać znak ***tx_api. h** _ podczas kompilacji i link do biblioteki wykonawczej ThreadX _*_TX. a_*_ (lub _ *_TX. lib_* *).

Do skompilowania aplikacji ThreadX wymagane są cztery kroki.

1. Uwzględnij plik ***tx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług ThreadX Services lub struktur danych.

1. Utwórz funkcję standard C ***Main** _. Ta funkcja musi ostatecznie wywołać _ *_tx_kernel_enter_**, aby rozpocząć ThreadX. Przed wprowadzeniem jądra można dodać inicjalizację specyficzną dla aplikacji, która nie obejmuje ThreadX.

      > [!IMPORTANT]
      > * Funkcja ThreadX entry ***tx_kernel_enter** _ nie zwraca. Dlatego nie należy umieszczać żadnego wywołania ani wywołań funkcji po it._

1. Utwórz funkcję ***tx_application_define*** . Jest to miejsce, w którym są tworzone początkowe zasoby systemowe. Przykładami zasobów systemowych są wątki, kolejki, Pule pamięci, grupy flag zdarzeń, muteksy i semafory.

1. Skompiluj Źródło aplikacji i połącz ją z biblioteką wykonawczą ThreadX. ***lib***. Obraz wyników można pobrać do elementu docelowego i wykonać!

## <a name="small-example-system"></a>Mały przykładowy system

Mały przykładowy system na rysunku 1 pokazuje tworzenie pojedynczego wątku z priorytetem 3. Wątek wykonuje, zwiększa licznik, a następnie uśpienia dla jednego zegara.
Ten proces kontynuuje się bez ograniczeń.

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

**RYSUNEK 1. Szablon opracowywania aplikacji**

Chociaż jest to prosty przykład, zapewnia dobry szablon do rzeczywistego opracowywania aplikacji.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port ThreadX jest dostarczany z aplikacją demonstracyjną. Zawsze dobrym pomysłem jest uzyskanie uruchomionego systemu demonstracyjnego — na rzeczywistym sprzęcie docelowym lub symulowanym środowisku.

Jeśli system demonstracyjny nie działa prawidłowo, poniżej przedstawiono niektóre wskazówki dotyczące rozwiązywania problemów.

1. Określ, jaka część demonstracji jest uruchomiona.
1. Zwiększ rozmiary stosu (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w przypadku pokazu).
1. Skompiluj ponownie bibliotekę ThreadX z definicją TX_ENABLE_STACK_CHECKING. Umożliwia to wbudowaną kontrolę stosu ThreadX.
1. Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie. Takie informacje powinny być przydatne do obsługi inżynierów.

Postępuj zgodnie z procedurami przedstawionymi w[centrum pomocy technicznej](about-this-guide.md#customer-support-center), aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki ThreadX i aplikacji przy użyciu ThreadX istnieje kilka opcji konfiguracji. Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w pliku ***tx_user. h*** .

> [!IMPORTANT]
> * Opcje zdefiniowane w ***tx_user. h** _ są stosowane tylko wtedy, gdy aplikacja i Biblioteka ThreadX zostały skompilowane przy użyciu _ *TX_INCLUDE_USER_DEFINE_FILE** zdefiniowanej.*

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

Dla najszybszych wykonań te same opcje konfiguracji, które są używane dla najmniejszej konfiguracji wcześniej, ale z tymi opcjami również są brane pod uwagę.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

Opisano [szczegółowe opcje konfiguracji](#detailed-configuration-options) .

### <a name="global-time-source"></a>Globalne źródło czasu

W przypadku innych Microsoft Azure produktów RTO (FileX, NetX, GUIX, USBX itp.), ThreadX definiuje liczbę cykli czasomierza ThreadX, które reprezentują jedną sekundę. Inne korzystają z własnych wymagań czasowych na podstawie tej stałej. Wartością domyślną jest 100, przy założeniu, że 10 ms okresowe przerwanie. Użytkownik może zastąpić tę wartość, definiując TX_TIMER_TICKS_PER_SECOND przy użyciu żądanej wartości w ***tx_port. h*** lub w środowisku IDE lub w wierszu polecenia.

### <a name="detailed-configuration-options"></a>Szczegółowe opcje konfiguracji

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Po zdefiniowaniu ta opcja umożliwia gromadzenie informacji o wydajności w pulach bajtów. Domyślnie ta opcja nie jest zdefiniowana.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Po zdefiniowaniu ta opcja umożliwia gromadzenie informacji o wydajności w pulach bajtów. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_ERROR_CHECKING**

Pomija sprawdzanie błędów wywołania usługi podstawowej. W przypadku zdefiniowania w źródle aplikacji wszystkie podstawowe sprawdzanie błędów parametrów jest wyłączone. Może to zwiększyć wydajność o nawet 30% i może również zmniejszyć rozmiar obrazu.

> [!NOTE]
> *Wyłączenie sprawdzania błędów jest możliwe tylko wtedy, gdy aplikacja może całkowicie zagwarantować, że wszystkie parametry wejściowe są zawsze ważne we wszystkich okolicznościach, włącznie z parametrami wejściowymi pochodzącymi z zewnętrznych danych wejściowych. Jeśli do interfejsu API dostarczono nieprawidłowe dane wejściowe z wyłączonym sprawdzaniem błędów, Wynikowe zachowanie jest niezdefiniowane i może skutkować uszkodzeniem pamięci lub awarią systemu.*

> [!NOTE]
> *Wartości zwracane przez interfejs API ThreadX nie wpływają na wyłączanie sprawdzania błędów są wyświetlane pogrubione w sekcji "wartości zwracane" w opisie interfejsu API w rozdziale 4. Wartości zwrotne Niepogrubione są puste, jeśli sprawdzanie błędów jest wyłączone przy użyciu opcji TX_DISABLE_ERROR_CHECKING.*

**TX_DISABLE_NOTIFY_CALLBACKS**

Po zdefiniowaniu program wyłącza powiadomienia zwrotne dla różnych obiektów ThreadX. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_PREEMPTION_THRESHOLD**

Po zdefiniowaniu program wyłącza funkcję progu zastępują i nieco zmniejsza rozmiar kodu i zwiększa wydajność. Oczywiście funkcje progu zastępujące nie są już dostępne. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_REDUNDANT_CLEARING**

Po zdefiniowaniu program usuwa logikę do inicjowania ThreadX globalnych C struktur danych w wartości zero. Ta wartość powinna być używana tylko wtedy, gdy kod inicjalizacji kompilatora ustawi wszystkie niezainicjowane dane globalne języka C na zero. Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność podczas inicjacji. Domyślnie ta opcja nie jest zdefiniowana.

**TX_DISABLE_STACK_FILLING**

Gdy jest zdefiniowany, wyłącza umieszczanie wartości 0xEF w każdym bajcie stosu każdego wątku po utworzeniu. Domyślnie ta opcja nie jest zdefiniowana.

**TX_ENABLE_EVENT_TRACE**

Po zdefiniowaniu ThreadX włącza kod zbierający zdarzenia do tworzenia buforu śledzenia TraceX.

**TX_ENABLE_STACK_CHECKING**

Gdy jest zdefiniowany, umożliwia sprawdzanie sterty czasu wykonywania ThreadX, w tym analizę ilości stosu i badanie wzorców danych "ogrodzenia" przed i po obszarze stosu. W przypadku wykrycia błędu stosu zostanie wywołana zarejestrowana procedura obsługi błędów stosu aplikacji. Ta opcja powoduje nieco zwiększone obciążenie i rozmiar kodu. Aby uzyskać więcej informacji, przejrzyj funkcję API ***tx_thread_stack_error_notify*** . Domyślnie ta opcja nie jest zdefiniowana.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

Po zdefiniowaniu program włącza zbieranie informacji o wydajności w grupach flag zdarzeń. Domyślnie ta opcja nie jest zdefiniowana.

**TX_INLINE_THREAD_RESUME_SUSPEND**

Po zdefiniowaniu ThreadX ulepsza wywołania interfejsu API ***tx_thread_resume** _ i _ *_tx_thread_suspend_** za pośrednictwem kodu w wierszu. Zwiększa to rozmiar kodu, ale zwiększa wydajność tych dwóch wywołań interfejsu API.

**TX_MAX_PRIORITIES**

Definiuje poziomy priorytetów dla ThreadX. Wartości prawne mieszczą się w zakresie od 32 do 1024 (włącznie) i *muszą* być równo widoczne przez 32. Zwiększenie liczby obsługiwanych poziomów priorytetów zwiększa użycie pamięci RAM o 128 bajtów dla każdej grupy priorytetów 32. Istnieje jednak tylko znaczący wpływ na wydajność. Domyślnie ta wartość jest ustawiana na 32 poziomów priorytetów.

**TX_MINIMUM_STACK**

Określa minimalny rozmiar stosu (w bajtach). Służy do sprawdzania błędów podczas tworzenia wątków. Wartość domyślna to specyficzny dla portu i znajduje się w ***tx_port. h***.

**TX_MISRA_ENABLE**

Po zdefiniowaniu ThreadX wykorzystuje konwencje zgodne z MISRA C. Aby uzyskać szczegółowe informacje, zobacz  ***ThreadX_MISRA_Compliance.pdf*** .

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności dla muteksów. Domyślnie ta opcja nie jest zdefiniowana.

**TX_NO_TIMER**

Po zdefiniowaniu logika czasomierza ThreadX jest całkowicie wyłączona. Jest to przydatne w przypadku, gdy funkcje czasomierza ThreadX (uśpienia wątku, przekroczenia limitu czasu interfejsu API, wyróżniania czasu i przetwarzania aplikacji) nie są używane. Jeśli określono **TX_NO_TIMER** , należy również zdefiniować opcję **TX_TIMER_PROCESS_IN_ISR** .

**TX_NOT_INTERRUPTABLE**

Po zdefiniowaniu ThreadX nie podejmuje próby zminimalizowania czasu blokady przerwań. Powoduje to szybsze wykonywanie, ale nieco wydłuża czas blokady przerwań.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności w kolejkach. Domyślnie ta opcja nie jest zdefiniowana.

**TX_REACTIVATE_INLINE**

Po zdefiniowaniu program wykonuje ponowną aktywację ThreadX czasomierzy wbudowane zamiast używania wywołania funkcji. Poprawia to wydajność, ale nieco zwiększa rozmiar kodu. Domyślnie ta opcja nie jest zdefiniowana.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności dla semaforów. Domyślnie ta opcja nie jest zdefiniowana.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności w wątkach. Domyślnie ta opcja nie jest zdefiniowana.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności na czasomierzach. Domyślnie ta opcja nie jest zdefiniowana.

**TX_TIMER_PROCESS_IN_ISR**

Po zdefiniowaniu eliminuje wewnętrzny wątek czasomierza systemu dla ThreadX. Powoduje to zwiększenie wydajności zdarzeń czasomierza i mniejszych wymagań dotyczących pamięci RAM, ponieważ stos czasomierzy i blok sterowania nie są już potrzebne. Jednak użycie tej opcji przenosi wszystkie operacje przetwarzania wygaśnięcia czasomierza do poziomu ISR czasomierza. Domyślnie ta opcja nie jest zdefiniowana.

> [!NOTE]
> *Usługi dozwolone z czasomierzy mogą nie być dozwolone z procedury ISR i w ten sposób mogą być niedozwolone w przypadku korzystania z tej opcji.*

**TX_TIMER_THREAD_PRIORITY**

Definiuje priorytet wewnętrznego wątku czasomierza systemu ThreadX. Wartość domyślna to priorytet 0 — najwyższy priorytet w ThreadX. Wartość domyślna jest definiowana w ***tx_port. h***.

**TX_TIMER_THREAD_STACK_SIZE**

Określa rozmiar stosu (w bajtach) wewnętrznego wątku czasomierza systemu ThreadX. Ten wątek przetwarza wszystkie żądania uśpienia wątku, a także wszystkie limity czasu wywołań usługi. Ponadto wszystkie procedury wywołania zwrotnego czasomierza aplikacji są wywoływane z tego kontekstu. Wartość domyślna to specyficzny dla portu i znajduje się w ***tx_port. h***.

## <a name="threadx-version-id"></a>Identyfikator wersji ThreadX

Programista może uzyskać wersję ThreadX z badania pliku ***tx_port. h** _. Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję ThreadX, badając ciąg globalny _ * _tx_version_id * *.
