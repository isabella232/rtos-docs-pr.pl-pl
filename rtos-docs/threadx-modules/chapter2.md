---
title: Rozdział 2 — wymagania dotyczące modułów
description: Ten artykuł zawiera opis wymagań dotyczących kompilowania modułu ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32288d78ceffb74ab088a1d720dbac657f6d3ed4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821397"
---
# <a name="chapter-2---module-requirements"></a>Rozdział 2 — wymagania dotyczące modułów

Moduł ThreadX zawiera preambułę, która definiuje podstawowe cechy modułu. Po preambule następuje obszar instrukcji modułu. Moduły mogą być wykonywane w miejscu lub mogą być ładowane do obszaru pamięci modułu przez Menedżera modułów przed wykonaniem. Jedyny wymóg polega na tym, że Preambuła zawsze znajduje się na pierwszym adresie modułu. Rysunek 2 ilustruje podstawowy układ modułu.

| Układ modułu |
|:---:|
| \[Preambuła modułu\]         |
| \[obszar instrukcji modułu\] |
| \[obszar pamięci RAM modułu\]         |

**Rysunek 2** — układ modułu

> [!NOTE]
> Moduły muszą być kompilowane przy użyciu odpowiednich kodów niezależnych od pozycji i kompilatora danych/konsolidatora. Dzięki temu można wykonać moduł w dowolnym obszarze pamięci.

Po utworzeniu wątku modułu zostaje przypisana druga przestrzeń stosu do użycia, gdy wątek znajduje się w jądrze chronionym w pamięci. Rozmiar obszaru stosu jądra wątku jest konfigurowalny przez użytkownika przy użyciu **TXM_MODULE_KERNEL_STACK_SIZE** w **_txm_module_port. h_*_. Pozwala to na użycie mniejszego rozmiaru stosu podczas tworzenia wątku modułu, ponieważ stos określony przez użytkownika podczas wywoływania _*_tx_thread_create_** jest używany tylko w module.

> [!NOTE]
> Góra stosu wątków modułu zawiera strukturę informacji o wpisie wątku (**TXM_MODULE_THREAD_ENTRY_INFO**), dzięki czemu rozmiar dostępnego stosu jest zmniejszany o rozmiar tej struktury. Podczas tworzenia wątku w module należy zwiększyć jego rozmiar stosu, co najmniej ten rozmiar tej struktury.

Poniższe kroki są wymagane do utworzenia i skompilowania modułu ThreadX (każdy krok został szczegółowo opisany poniżej).

1. Wszystkie pliki C w module muszą #define **TXM_MODULE** przed dołączeniem **_txm_module. h_**. Można to osiągnąć w pliku źródłowym kompilowanym lub w ramach ustawień projektu. W ten sposób ponownie mapuje wywołania interfejsu API ThreadX do wersji interfejsu API specyficznej dla modułu, która wywołuje funkcję wysyłania w Menedżerze modułu rezydentnego w celu wykonania wywołania do rzeczywistej funkcji interfejsu API.
2. Każdy moduł musi mieć preambułę według pierwszego adresu obszaru instrukcji, który definiuje cechy i wymagania dotyczące zasobów modułu.
3. Każdy moduł musi połączyć preambułę na początku obszaru instrukcji modułu.
4. Każdy moduł musi łączyć się z biblioteką modułu (***TXM. a***), która zawiera funkcje specyficzne dla modułu używane do współpracy z ThreadX.

## <a name="module-sources"></a>Źródła modułów

Moduły ThreadX mają własny zestaw plików źródłowych, które zostały zaprojektowane tak, aby były połączone i znajdować się bezpośrednio z kodem źródłowym modułu. Te pliki zapewniają mostek między oddzielnym modułem i menedżerem rezydentów modułu. Pliki modułów są następujące.

| Nazwa pliku | Zawartość |
|---|---|
| **txm_module. h** | Plik dołączany, który definiuje informacje o module. |
| **txm_module_port. h** | Plik dołączany, który definiuje informacje o module specyficznym dla portów. |
| **txm_module_user. h** | Definiuje i wartości, które użytkownik może dostosować. |
| **txm_module_initialize. s [1] [3]** | Wywołuje funkcje wewnętrzne do modułu uruchomieniowego. |
| **txm_module_preamble. \{ s/S/68\}** | Plik zestawu preambuły modułu. Ten plik definiuje różne atrybuty specyficzne dla modułu i jest połączony z kodem aplikacji modułu. |
| **txm_module_application_request. c [1]** | Funkcja żądania aplikacji modułu wysyła do kodu rezydentnego żądanie specyficzne dla aplikacji. |
| **txm_module_callback_request_thread_entry. c &nbsp; [1]** | Wątek wywołania zwrotnego modułu, który jest odpowiedzialny za przetwarzanie wywołań zwrotnych żądanych przez moduł, w tym czasomierzy i wywołania zwrotne powiadomień. |
| **txm_ *. c [1] [2]** | Standardowe usługi interfejsu API ThreadX, które wywołują dyspozytora jądra.
| **txm_module_object_allocate. c [1]** | Funkcja modułu służąca do przydzielania pamięci dla obiektów modułów znajdujących się w puli pamięci Menedżera. |
| **txm_module_object_deallocate. c [1]** | Funkcja modułu służąca do cofania alokacji pamięci dla obiektów modułów znajdujących się w puli pamięci Menedżera. |
| **txm_module_object_pointer_get. c [1]** | Funkcja modułu do pobierania wskaźnika do obiektu systemowego. |
| **txm_module_object_pointer_get_extended. c [1]** | Funkcja modułu służąca do pobierania wskaźnika do obiektu systemowego, o długości nazwy. |
| **txm_module_thread_shell_entry. c [1]** | Funkcja wprowadzania wątku modułu. |
| **txm_module_thread_system_suspend. c [1]** | Funkcja modułu służąca do wstrzymywania wątku. |

**[1]** znajduje się w bibliotece **_TXM. a_**.

**[2]** te pliki mają taką samą nazwę jak pliki interfejsu API ThreadX, z prefiksem **txm_** , a nie prefiksem **TX_** .

**[3]** plik **txm_module_initialize. s** jest tylko dla portów korzystających z narzędzi ARM.

## <a name="module-preamble"></a>Preambuła modułu

Preambuła modułu definiuje charakterystyki i zasoby modułu. Informacje, takie jak początkowa funkcja wprowadzania wątku i początkowy obszar pamięci skojarzony z wątkiem, są zdefiniowane w preambule. Przykłady z preambuły specyficzne dla portów znajdują się w [dodatku](appendix.md). Rysunek 3 przedstawia przykład preambuły modułu ThreadX dla ogólnego celu (wiersze zaczynające się od * są wartościami zwykle modyfikowanymi przez aplikację):

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

**Rysunek 3**

W większości przypadków Deweloper musi definiować tylko wątek początkowy (offset 0x1C), identyfikator modułu (offset 0x10), priorytet uruchamiania/zatrzymywania wątku (offset 0x24) i początkowy/zatrzymany rozmiar stosu wątku (offset 0x28). Powyższa prezentacja jest skonfigurowana w taki sposób, że początkowy wątek modułu to ***demo_module_start** _, identyfikator modułu to _*_0x12345678 również_*_, a wątek początkowy ma priorytet _*_1_*_, a rozmiar stosu wynoszący _ *_2048_** b.

Niektóre aplikacje mogą opcjonalnie definiować wątek zatrzymania, który jest wykonywany, gdy Menedżer modułów zatrzymuje moduł. Ponadto niektóre aplikacje mogą korzystać z pola właściwości modułu zdefiniowanego w następujący sposób.

## <a name="module-properties-bit-map"></a>Mapa bitów właściwości modułu

W poniższej tabeli przedstawiono przykład mapy bitowej właściwości. Mapy bitowe właściwości specyficzne dla portów znajdują się w [dodatku](appendix.md).

| Bit | Wartość | Znaczenie |
|---|---|---|
| 0 | 0<br />1 | Wykonywanie trybu uprzywilejowanego<br />Wykonywanie w trybie użytkownika |
| 1 | 0<br />1 | Brak ochrony MPU<br />Ochrona MPU (musi być wybrana w trybie użytkownika) |
| 2 | 0<br />1 | Wyłącz dostęp do pamięci współdzielonej/zewnętrznej<br />Włącz dostęp do pamięci współdzielonej/zewnętrznej |
| [23-3] | 0 | Zarezerwowany
| [31-24] | <br />0x01<br />0x02<br />0x03 | **Identyfikator kompilatora**<br />IAR<br />ARM<br />GNU |


## <a name="module-linker-control-file"></a>Plik sterowania konsolidatorem modułu

Podczas kompilowania modułu Preambuła modułu musi być umieszczona przed każdą inną sekcją kodu. Moduł musi być skompilowany przy użyciu kodu niezależnego od pozycji i sekcji danych. Przykładowe pliki konsolidatora specyficzne dla portów znajdują się w [dodatku](appendix.md).

## <a name="module-threadx-library"></a>Biblioteka ThreadX modułu

Każdy moduł musi być połączony z specjalną, skoncentrowaną na module biblioteką ThreadX. Ta biblioteka zapewnia dostęp do usług ThreadX Services w kodzie rezydentnym. Większość dostępu jest realizowana za pośrednictwem plików ***txm_ \* . c*** . Poniżej znajduje się przykład wywołania dostępu do modułu dla funkcji API ThreadX **_tx_thread_relinquish_* _ (w _*_ \_ txm_thread_relinquish. c * * * \* ).

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

W tym przykładzie wskaźnik funkcji dostarczony przez Menedżera modułów jest używany do wywołania funkcji wysyłania Menedżera modułów z IDENTYFIKATORem skojarzonym z usługą ***tx_thread_relinquish*** . Ta usługa nie przyjmuje żadnych parametrów.

## <a name="module-example"></a>Przykład modułu

Poniżej znajduje się przykład standardowej demonstracji ThreadX w postaci modułu. Główne różnice między standardową prezentacją ThreadX a demonstracją modułu są.

1. Zastąpienie elementu ***tx_api. h** _ znakiem _ *_txm_module. h_**
2. Dodanie **#define TXM_MODULE** przed **_txm_module. h_**
3. Zastąpienie ***Main** _ i _ *tx_application_define** z **_demo_module_start_**
4. Deklarowanie *wskaźników* do obiektów ThreadX, a nie samych obiektów.

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a>Kompilowanie modułów

Kompilowanie modułu jest zależne od używanego łańcucha narzędzi. Zobacz [dodatek](appendix.md) dla przykładów specyficznych dla portów. Typowe działania dotyczące wszystkich portów obejmują następujące elementy:

- Kompilowanie biblioteki modułów
- Kompilowanie aplikacji modułu

Każdy moduł musi mieć **txm_module_preamble** (konfigurację specyficzną dla modułu) i bibliotekę modułów (na przykład **_TXM. a_**).
