---
title: Rozdział 3 — wymagania dotyczące programu module Manager
description: Ten artykuł zawiera opis czynności wymaganych do utworzenia Menedżera modułu ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822500"
---
# <a name="chapter-3---module-manager-requirements"></a>Rozdział 3 — wymagania dotyczące programu module Manager

Program ThreadX module Manager znajduje się w rezydentnej części aplikacji wraz z RTO ThreadX. Jest on odpowiedzialny za uruchamianie modułu, a także pole i wysyłanie żądań wszystkich modułów dla usług interfejsu API ThreadX.

> [!NOTE]
> Pliki źródłowe **Menedżera** modułów ThreadX (C i Assembly) należy dodać do projektu biblioteki ThreadX "**TX**".

Poniższe kroki są wymagane do utworzenia Menedżera modułu ThreadX (każdy krok został szczegółowo opisany poniżej).

1. Aby uwzględnić informacje o module, należy rozszerzyć blok sterowania **TX_THREAD** . Najprostszym sposobem na to jest zamienienie definicji **TX_THREAD_EXTENSION_2** w **pliku _tx_port. h_*_ z TX_THREAD_EXTENSION_2 _*** znalezionym w **_txm_module_port. h_**. Zobacz [dodatek](appendix.md) dotyczący rozszerzeń specyficznych dla portów.

Przykładowe rozszerzenie:

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   Następujące rozszerzenia muszą być zdefiniowane w ***tx_port. h***.

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. Dodaj wszystkie ***txm_module_manager_ \**** C i pliki zestawu **_do projektu biblioteki_** ThreadX.
3. Kompiluj ponownie wszystkie biblioteki i projekty wykonywalne. Jeśli NetX Duo jest wymagana, wszystkie kody modułów i modułów w języku C powinny być skompilowane przy użyciu zdefiniowanych **TXM_MODULE_ENABLE_NETX_DUO** .

## <a name="module-manager-sources"></a>Źródła Menedżera modułów

Menedżer modułu ThreadX ma zestaw plików źródłowych, które zostały zaprojektowane tak, aby można je było łączyć i znajdować bezpośrednio w kodzie rezydentnym ThreadX. Te pliki umożliwiają uruchamianie modułu i kolejnych żądań interfejsu API ThreadX z modułu. Pliki menedżera modułów są następujące.

| **Nazwa pliku** |  **Zawartość** |
|-------------- | ------------- |
| ***txm_module. h*** | Plik dołączany, który definiuje informacje o module (również zawarte w kodzie źródłowym modułu). |
| ***txm_module_manager_dispatch. h*** | Plik dołączany, który definiuje funkcje pomocnika wysyłania.|
| ***txm_module_manager_util. h*** | Plik dołączany, który definiuje wewnętrzne makra pomocnika narzędzi & funkcje. |
| ***txm_module_port. h*** | Plik dołączany, który definiuje informacje o module specyficznym dla portów (również zawarte w kodzie źródłowym modułu). |
| ***tx_initialize_low_level. \[ s, S, 68 \]** _ | Zamienia istniejący plik biblioteki ThreadX. Zaktualizowano tabelę wektorów i dodatkowe programy obsługi wektorów dla wyjątków Menedżera modułów i pamięci. Plik _This jest tylko w Cortex-nr/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR. *|
| ***tx_thread_context_restore. s** _ | Zamienia istniejący plik biblioteki ThreadX. Przywróć kontekst wątku po przetworzeniu przerwań. Plik _This jest tylko w Cortex-Cortex/ARM, Cortex-R4/ARM,-R4/IAR. *|
| ***tx_thread_schedule. \[ s, S, 68\]*** | Zamienia istniejący plik biblioteki ThreadX. Rozszerzony kod harmonogramu, w tym przypadku jest używany do aktualizacji rejestrów zarządzania pamięcią. |
| ***tx_thread_stack_build. s** _ | Zamienia istniejący plik biblioteki ThreadX. Kompiluje ramkę stosu wątku. Plik _This jest tylko w Cortex-Cortex/ARM, Cortex-R4/ARM,-R4/IAR. *|
| ***txm_module_manager_thread_stack_build. \[ s, S, 68\]*** | Kompiluje wszystkie początkowe stosy modułów, w tym Instalatora dla dostępu do danych na pozycji. |
| ***txm_module_manager_user_mode_entry. \[ s, S \]** _ | Umożliwia modułowi wprowadzanie trybu jądra. Plik _This jest tylko w Cortex-Cortex/ARM, Cortex-R4/ARM,-R4/IAR. *|
| ***txm_module_manager_alignment_adjust. c*** | Obsługuje wymagania dotyczące wyrównania charakterystyczne dla portów.|
| ***txm_module_manager_application_request. c*** | Obsługuje żądania specyficzne dla aplikacji w kodzie rezydentnym. |
| ***txm_module_manager_callback_request. c*** | Wysyła żądanie wywołania zwrotnego do modułu. |
| ***txm_module_manager_event_flags_notify_trampoline. c*** | Przetwarza flagi zdarzeń ustawia wywołanie powiadomienia z ThreadX. |
| ***txm_module_manager_external_memory_enable. c*** | Tworzy wpis w tabeli zarządzania pamięcią dla współdzielonego miejsca w pamięci, do którego moduł może uzyskać dostęp. |
| ***txm_module_manager_file_load. c*** | Przydziela i ładuje plik modułu binarnego do obszaru pamięci modułu i przygotowuje go do wykonania. |
| ***txm_module_manager_in_place_load. c*** | Przydziela obszar danych modułu i przygotowuje się do wykonania modułu z podanego adresu kodu. |
| ***txm_module_manager_initialize. c*** | Inicjuje menedżera modułów, w tym specyfikację obszaru pamięci modułu dostępną do ładowania i uruchamiania modułów. |
| ***txm_module_manager_initialize_mmu. c** _ | Zainicjuj pamięcią. Użytkownicy mogą edytować ten plik według mapy pamięci. Plik _This jest tylko w Cortex-nr/ARM * |
| ***txm_module_manager_mm_initialize. c** _ | Zainicjuj MPU/pamięcią. Użytkownicy mogą edytować ten plik według mapy pamięci. Plik _This jest tylko w Cortex-nr/ARM * |
| ***txm_module_manager_kernel_dispatch. c*** | Obsługuje żądania interfejsu API modułu na podstawie identyfikatora żądania. |
| ***txm_module_manager_maximum_module_priority_set. c*** | Ustawia maksymalny priorytet wątku dozwolony w module. |
| ***txm_module_manager_memory_fault_handler. c*** | Obsługuje błędy pamięci wykryte w module wykonywanym. |
| ***txm_module_manager_memory_fault_notify. c*** | Rejestruje wywołanie zwrotne powiadomień aplikacji przy każdym wystąpieniu błędu pamięci. |
| ***txm_module_manager_memory_load. c*** | Przydziela i ładuje kod i dane modułu oraz przygotowuje moduł do wykonania. |
| ***txm_module_manager_mm_register_setup. c*** | Konfiguruje rejestry MPU/pamięcią dla modułu w zależności od tego, gdzie jest ładowany kod i dane. |
| ***txm_module_manager_object_allocate. c*** | Przydziela pamięć dla obiektu modułu. |
| ***txm_module_manager_object_deallocate. c*** | Cofa alokację pamięci dla obiektu modułu. |
| ***txm_module_manager_object_pointer_get. c*** | Wyszukuje podany typ obiektu i nazwę, a jeśli zostanie znaleziona, zwraca wskaźnik obiektu. |
| ***txm_module_manager_object_pointer_get_extended. c*** | Wyszukuje podany typ obiektu i nazwę, a jeśli zostanie znaleziona, zwraca wskaźnik obiektu. Długość nazwy określona dla bezpieczeństwa. |
| ***txm_module_manager_object_pool_create. c***  | Tworzy pulę obiektów poza obszarem danych modułu, z którego mogą być przydzielane aplikacje modułu. |
| ***txm_module_manager_properties_get. c*** | Pobiera właściwości określonego modułu. |
| ***txm_module_manager_queue_notify_trampoline. c*** | Przetwarza wywołanie powiadomienia kolejki z ThreadX. |
| ***txm_module_manager_semaphore_notify_trampoline. c*** | Przetwarza wywołanie powiadomienia o wprowadzeniu semafora z ThreadX.|
| ***txm_module_manager_start. c*** | Uruchamia wykonywanie modułu. |
| ***txm_module_manager_stop. c*** | Powoduje zatrzymanie wykonywania modułu. |
| ***txm_module_manager_thread_create. c*** | Tworzy wszystkie wątki modułu. |
| ***txm_module_manager_thread_notify_trampoline. c*** | Przetwarza wywołanie powiadomienia o wejściu/wyjściu wątku z ThreadX. |
| ***txm_module_manager_thread_reset. c*** | Zresetuj wątek modułu. |
| ***txm_module_manager_timer_notify_trampoline. c*** | Przetwarza wygaśnięcia czasomierza z ThreadX. |
| ***txm_module_manager_unload. c*** | Zwalnia moduł z obszaru pamięci modułu. |
| ***txm_module_manager_util. c*** | Wewnętrzne funkcje pomocnika dla Menedżera. |

## <a name="module-manager-initialization"></a>Inicjowanie Menedżera modułów

Rezydentna część aplikacji jest odpowiedzialna za wywoływanie funkcji inicjowania Menedżera modułów ***txm_module_manager_initialize***. Ta funkcja konfiguruje wewnętrzne struktury do ładowania i wyładowywania modułów, w tym konfigurowania obszaru pamięci używanego do przydzielania pamięci modułu.

## <a name="module-manager-loading"></a>Ładowanie Menedżera modułów

Menedżer modułów może dynamicznie ładować moduły do pamięci modułu z plików modułów binarnych lub z sekcji kodu modułu, która znajduje się już w obszarze rezydentów. Ponadto Menedżer modułów może wykonać kod w miejscu, to znaczy, że tylko dane modułu są przydzieleni do pamięci modułu, a wykonywanie kodu jest wykonywane. Dostępne są następujące funkcje interfejsu API ładowania programu module Manager.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

Wersja chroniona pamięci Menedżera modułów gwarantuje również, że moduł jest ładowany z odpowiednim wyrównaniem, a rejestry zarządzania pamięcią są poprawnie skonfigurowane dla każdego modułu. Gdy ochrona pamięci jest włączona za pomocą opcji preambuły modułu, dostęp do pamięci modułu jest ograniczony do kodu modułu i obszarów danych.

## <a name="module-manager-starting"></a>Uruchamianie Menedżera modułów

Menedżer modułów inicjuje wykonywanie poprzednio załadowanego modułu za pomocą funkcji ***txm_module_manager_start*** API. Aby zainicjować wykonywanie modułu, ta funkcja tworzy wątek, który przechodzi do modułu w lokalizacji początkowej określonej w preambule modułu. Priorytet i rozmiar stosu tego wątku jest również określony w preambule modułu.

## <a name="module-manager-stopping"></a>Zatrzymywanie Menedżera modułów

Menedżer modułów kończy wykonywanie wcześniej załadowanych i wykonywanych modułów za pośrednictwem funkcji ***txm_module_manager_stop*** . Ta funkcja interfejsu API najpierw kończy działanie i usuwa początkowy wątek początkowy. Jeśli Preambuła modułu określa wątek zatrzymania, ten wątek jest tworzony i wykonywany. Menedżer modułu czeka przez ustalony czas na ukończenie wątku zatrzymania. Po zakończeniu wszystkie zasoby systemowe utworzone przez moduł zostaną usunięte, a moduł zostanie umieszczony w stanie uśpienia, z którego może zostać ponownie uruchomiony lub zwolniony.

## <a name="module-manager-unloading"></a>Zwalnianie Menedżera modułów

Menedżer modułów zwalnia poprzednio załadowany moduł, ale nie wykonuje go za pośrednictwem funkcji ***txm_module_manager_unload*** . Ten interfejs API zwalnia całą pamięć skojarzoną z modułem, zwalniając ją do użycia z innym modułem w przyszłości.

## <a name="module-manager-requests"></a>Żądania Menedżera modułów

Żądania wykonywane przez moduły do Menedżera modułów są wykonywane za pośrednictwem makr w ***txm_module. h*** , które mapują wszystkie wywołania ThreadX w celu wywołania funkcji wysyłania Menedżera modułów za pośrednictwem wskaźnika funkcji dostarczonego do modułu przez Menedżera modułów.

Dodatkowe usługi specyficzne dla aplikacji wykonywane za pośrednictwem modułu wywołującego ***txm_module_application_request*** są obsługiwane przez ten sam mechanizm makro, który jest używany przez interfejs API ThreadX. Domyślnie ta funkcja obsługi w Menedżerze modułów jest pusta i zaprojektowana w taki sposób, że aplikacja dodaje kod niezbędny do przetwarzania żądań specyficznych dla aplikacji.

Jeśli żądanie nie zostanie zaimplementowane przez Menedżera modułów, Menedżer modułów zwróci wartość **TX_NOT_AVAILABLE** stan błędu. Ten kod błędu jest również zwracany, jeśli moduł żąda operacji, która znajduje się poza zakresem dostępu modułu. Na przykład moduł nie może utworzyć czasomierza z blokiem sterowania czasomierzem lub adresem wywołania zwrotnego poza obszarem kodu modułu.

## <a name="module-manager-example"></a>Przykład Menedżera modułów

Poniżej znajduje się przykładowy kod Menedżera modułów, który uruchamia przykładowy moduł zdefiniowany wcześniej w rozdziale 2. Zakłada się, że moduł jest już załadowany, najprawdopodobniej przez debuger, pod adresem ROM 0x00800000.

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a>Kompilowanie Menedżera modułów

Pliki źródłowe ***txm_module_manager_ \**** należy dodać do biblioteki ThreadX.

Aplikacja ThreadX module Manager jest efektywnie taka sama jak standardowa aplikacja ThreadX, która jest co najmniej jednym plikami aplikacji połączonym razem z biblioteką ThreadX ***TX. a***. Kompilowanie aplikacji Menedżera modułów jest zależne od używanego łańcucha narzędzi. Zobacz [dodatek](appendix.md) dla przykładów specyficznych dla portów.
