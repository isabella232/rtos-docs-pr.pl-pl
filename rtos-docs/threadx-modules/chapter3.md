---
title: Rozdział 3 — Wymagania menedżera modułów
description: Ten artykuł zawiera opis kroków wymaganych do sbudowania Menedżera modułów ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6c4d0993284c8e0b8264020d721ac12bdfe8117df4480fb54ee4d5b20a1f677e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799187"
---
# <a name="chapter-3---module-manager-requirements"></a>Rozdział 3 — Wymagania menedżera modułów

Menedżer modułów ThreadX znajduje się w części aplikacji w rezydualnej części wraz z threadX RTOS. Jest on odpowiedzialny za uruchomienie modułu, a także wysyłanie wszystkich żądań modułu do usług interfejsu API ThreadX i wysyłanie ich.

> [!NOTE]
> Pliki źródłowe **Menedżera** modułów ThreadX (C i zestaw) należy dodać do projektu biblioteki ThreadX "**tx**".

Poniższe kroki są wymagane do budowania Menedżera modułów ThreadX (każdy krok został opisany bardziej szczegółowo poniżej).

1. Blok **TX_THREAD** sterowania musi zostać rozszerzony, aby zawierał informacje o module. Najprostszym sposobem osiągnięcia tego celu jest  zastąpienie definicji TX_THREAD_EXTENSION_2 w pliku **_tx_port.h_*_*** plikiem _ TX_THREAD_EXTENSION_2 w pliku **_txm_module_port.h._** Zobacz [dodatek](appendix.md) dla rozszerzeń specyficznych dla portu.

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

   Następujące rozszerzenia muszą być zdefiniowane w pliku ***tx_port.h.***

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

2. Dodaj wszystkie pliki ***txm_module_manager_ \**** C i zestawu do projektu biblioteki ThreadX **_tx_**.
3. Ponownie skompilować wszystkie biblioteki i projekty wykonywalne. Jeśli netX Duo jest wymagany, cały kod języka C modułu i menedżera modułów powinien zostać sbudowaną **z** TXM_MODULE_ENABLE_NETX_DUO zdefiniowanym.

## <a name="module-manager-sources"></a>Źródła menedżera modułów

Menedżer modułów ThreadX zawiera zestaw plików źródłowych, które są przeznaczone do linku i znajdują się bezpośrednio z kodem ThreadX rezyduacyjną. Te pliki zapewniają możliwość uruchamiania modułu i pól kolejnych żądań interfejsu API ThreadX z modułu. Pliki menedżera modułów są następujące.

| **Nazwa pliku** |  **Zawartość** |
|-------------- | ------------- |
| ***txm_module.h*** | Dołącz plik definiujący informacje o module (również zawarte w kodzie źródłowym modułu). |
| ***txm_module_manager_dispatch.h*** | Dołącz plik definiujący funkcje pomocnika wysyłania.|
| ***txm_module_manager_util.h*** | Dołącz plik, który definiuje wewnętrzne makra pomocnika narzędzia & funkcji. |
| ***txm_module_port.h*** | Dołącz plik, który definiuje informacje o module specyficzne dla portu (zawarte również w kodzie źródłowym modułu). |
| ***tx_initialize_low_level. \[ s,S,68 \]** _ | Zastępuje istniejący plik biblioteki ThreadX. Zaktualizowano tabelę wektorów i dodatkowe procedury obsługi wektorów dla wyjątków menedżera modułów i pamięci. _This znajduje się tylko w: Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.*|
| ***tx_thread_context_restore.s** _ | Zastępuje istniejący plik biblioteki ThreadX. Przywracanie kontekstu wątku po zakończeniu przetwarzania przerwania. _This znajduje się tylko w systemie Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***tx_thread_schedule. \[ s,S,68\]*** | Zastępuje istniejący plik biblioteki ThreadX. Rozszerzony kod harmonogramu, który w tym przypadku jest używany do aktualizowania rejestrów zarządzania pamięcią. |
| ***tx_thread_stack_build.s** _ | Zastępuje istniejący plik biblioteki ThreadX. Tworzy ramkę stosu wątku. _This znajduje się tylko w systemie Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_thread_stack_build. \[ s,S,68\]*** | Tworzy wszystkie początkowe stosy modułu, obejmuje konfigurację dostępu do danych niezależnych od pozycji. |
| ***txm_module_manager_user_mode_entry. \[ s, \] S** _ | Zezwala modułowi na wejście w tryb jądra. _This znajduje się tylko w systemie Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_alignment_adjust.c*** | Obsługuje wymagania dotyczące wyrównania specyficzne dla portu.|
| ***txm_module_manager_application_request.c*** | Obsługuje żądania specyficzne dla aplikacji do kodu źródłowego. |
| ***txm_module_manager_callback_request.c*** | Wysyła żądanie wywołania zwrotnego do modułu. |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | Przetwarza wywołanie powiadomienia zestawu flag zdarzeń z ThreadX. |
| ***txm_module_manager_external_memory_enable.c*** | Tworzy wpis w tabeli zarządzania pamięcią dla udostępnionej przestrzeni pamięci, do których moduł może uzyskać dostęp. |
| ***txm_module_manager_file_load.c*** | Przydziela i ładuje plik modułu binarnego do obszaru pamięci modułu i przygotowuje go do wykonania. |
| ***txm_module_manager_in_place_load.c*** | Przydziela obszar danych modułu i przygotowuje się do wykonania modułu z podanego adresu kodu. |
| ***txm_module_manager_initialize.c*** | Inicjuje Menedżera modułów, w tym specyfikację obszaru pamięci modułu dostępnego do ładowania i uruchamiania modułów. |
| ***txm_module_manager_initialize_mmu.c** _ | Inicjowanie programu MMU. Użytkownicy mogą edytować ten plik zgodnie z mapą pamięci. _This znajduje się tylko w systemie Cortex-A7/ARM* |
| ***txm_module_manager_mm_initialize.c** _ | Zaimicjuj mpu/MMU. Użytkownicy mogą edytować ten plik zgodnie z mapą pamięci. _This znajduje się tylko w systemie Cortex-A7/ARM* |
| ***txm_module_manager_kernel_dispatch.c*** | Obsługuje żądania interfejsu API modułu na podstawie identyfikatora żądania. |
| ***txm_module_manager_maximum_module_priority_set.c*** | Ustawia maksymalny priorytet wątku dozwolony w module. |
| ***txm_module_manager_memory_fault_handler.c*** | Obsługuje błędy pamięci wykryte w module wykonującym. |
| ***txm_module_manager_memory_fault_notify.c*** | Rejestruje wywołanie zwrotne powiadomień aplikacji za każdym razem, gdy wystąpi błąd pamięci. |
| ***txm_module_manager_memory_load.c*** | Przydziela i ładuje kod i dane modułu oraz przygotowuje moduł do wykonania. |
| ***txm_module_manager_mm_register_setup.c*** | Konfiguruje rejestracje MPU/MMU dla modułu na podstawie tego, gdzie kod i dane są ładowane. |
| ***txm_module_manager_object_allocate.c*** | Przydziela pamięć dla obiektu modułu. |
| ***txm_module_manager_object_deallocate.c*** | Cofa alokację pamięci dla obiektu modułu. |
| ***txm_module_manager_object_pointer_get.c*** | Wyszukuje podany typ i nazwę obiektu, a jeśli zostanie znaleziony, zwraca wskaźnik obiektu. |
| ***txm_module_manager_object_pointer_get_extended.c*** | Wyszukuje podany typ i nazwę obiektu, a jeśli zostanie znaleziony, zwraca wskaźnik obiektu. Długość nazwy określona dla bezpieczeństwa. |
| ***txm_module_manager_object_pool_create.c***  | Tworzy pulę obiektów poza obszarem danych modułu, z których mogą przydzielać aplikacje modułu. |
| ***txm_module_manager_properties_get.c*** | Pobiera właściwości określonego modułu. |
| ***txm_module_manager_queue_notify_trampoline.c*** | Przetwarza wywołanie powiadomienia w kolejce z threadX. |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | Przetwarza wywołanie powiadomienia put semaphore z ThreadX.|
| ***txm_module_manager_start.c*** | Rozpoczyna wykonywanie modułu. |
| ***txm_module_manager_stop.c*** | Zatrzymuje wykonywanie modułu. |
| ***txm_module_manager_thread_create.c*** | Tworzy wszystkie wątki modułów. |
| ***txm_module_manager_thread_notify_trampoline.c*** | Przetwarza wywołanie powiadomienia o wejściu/wyjściu wątku z ThreadX. |
| ***txm_module_manager_thread_reset.c*** | Resetowanie wątku modułu. |
| ***txm_module_manager_timer_notify_trampoline.c*** | Przetwarza wygaśnięcia czasomierza z ThreadX. |
| ***txm_module_manager_unload.c*** | Zwalnia moduł z obszaru pamięci modułu. |
| ***txm_module_manager_util.c*** | Wewnętrzne funkcje pomocnika dla menedżera. |

## <a name="module-manager-initialization"></a>Inicjowanie menedżera modułów

Część aplikacji rezyduacyjna jest odpowiedzialna za wywoływanie funkcji inicjowania programu Module Manager ***txm_module_manager_initialize***. Ta funkcja konfiguruje wewnętrzne struktury do ładowania i zwalniania modułów, w tym konfigurowanie obszaru pamięci używanego do przydzielania pamięci modułu.

## <a name="module-manager-loading"></a>Ładowanie Menedżera modułów

Menedżer modułów może dynamicznie ładować moduły do pamięci modułu z plików modułów binarnych lub z sekcji kodu modułu, która jest już obecna w obszarze kodu rezydowania. Ponadto menedżer modułów może wykonywać kod w miejscu, czyli tylko dane modułu są przydzielane w pamięci modułu, a wykonywanie kodu jest wykonywane na miejscu. Dostępne są następujące funkcje interfejsu API ładowania programu Module Manager.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

Wersja Menedżera modułów chroniona pamięcią zapewnia również, że moduł został załadowany z odpowiednim dopasowaniem, a rejestry zarządzania pamięcią są prawidłowo skonfigurowane dla każdego modułu. Gdy ochrona pamięci jest włączona za pośrednictwem opcji ochrony modułu, dostęp do pamięci modułu jest ograniczony do kodu modułu i obszarów danych.

## <a name="module-manager-starting"></a>Uruchamianie Menedżera modułów

Menedżer modułów inicjuje wykonywanie wcześniej załadowanego modułu za pośrednictwem ***txm_module_manager_start*** API. Aby zainicjować wykonywanie modułu, ta funkcja tworzy wątek, który wchodzi do modułu w lokalizacji wyjściowej określonej w module. Priorytet i rozmiar stosu tego wątku są również określone w module.

## <a name="module-manager-stopping"></a>Zatrzymywanie menedżera modułów

Menedżer modułów przerywa wykonywanie wcześniej załadowanego i wykonującego modułu za pośrednictwem ***txm_module_manager_stop*** modułu. Ta funkcja interfejsu API najpierw kończy i usuwa początkowy wątek początkowy. Jeśli moduł określa wątek zatrzymania, ten wątek jest tworzony i wykonywany. Menedżer modułów czeka przez ustalony czas na zakończenie wątku zatrzymania. Po zakończeniu wszystkie zasoby systemowe utworzone przez moduł zostaną usunięte, a moduł zostanie umieszczony w stanie uśpienia, z którego można go ponownie uruchomić lub zwolnić.

## <a name="module-manager-unloading"></a>Zwalnianie Menedżera modułów

Menedżer modułów zwalnia wcześniej załadowany moduł, ale nie jest wykonywany za pośrednictwem ***txm_module_manager_unload*** modułu. Ten interfejs API zwalnia całą pamięć skojarzoną z modułem, zwalniając ją do użycia z innym modułem w przyszłości.

## <a name="module-manager-requests"></a>Żądania menedżera modułów

Żądania wysyłane przez moduły do menedżera modułów są wykonywane za pośrednictwem makr w programie ***txm_module.h,*** które mapują wszystkie wywołania ThreadX w celu wywołania funkcji wysyłania menedżera modułów za pośrednictwem wskaźnika funkcji dostarczonego do modułu przez menedżera modułów.

Dodatkowe usługi specyficzne dla aplikacji wykonane za pośrednictwem modułu wywołującego txm_module_application_request ***są*** obsługiwane przez ten sam mechanizm makra, który jest używany dla interfejsu API ThreadX. Domyślnie ta funkcja obsługi w menedżerze modułów jest pusta i zaprojektowana tak, aby aplikacja dodała kod niezbędny do przetwarzania żądań specyficznych dla aplikacji.

Jeśli żądanie nie jest implementowane przez menedżera modułów, menedżer modułów **TX_NOT_AVAILABLE** zwraca wartość stanu błędu. Ten kod błędu jest również zwracany, jeśli moduł zażąda operacji spoza zakresu dostępu do modułu. Na przykład moduł nie może tworzyć czasomierza z blokiem sterowania czasomierzem lub adresem wywołania zwrotnego poza obszarem kodu modułu.

## <a name="module-manager-example"></a>Przykład menedżera modułów

Poniżej przedstawiono przykład kodu programu Module Manager, który uruchamia przykładowy moduł zdefiniowany wcześniej w rozdziale 2. Zakłada się, że moduł jest już załadowany, prawdopodobnie przez debuger, pod adresem ROM 0x00800000.

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

## <a name="module-manager-building"></a>Tworzenie menedżera modułów

Pliki ***txm_module_manager_ \**** źródłowe należy dodać do biblioteki ThreadX.

Aplikacja Menedżera modułów ThreadX działa tak samo jak standardowa aplikacja ThreadX, która jest co najmniej jednym plikiem aplikacji połączonym razem z biblioteką ThreadX ***tx.a.*** Tworzenie aplikacji menedżera modułów zależy od używanego łańcucha narzędzi. Zobacz [dodatek,](appendix.md) aby uzyskać przykłady specyficzne dla portu.
