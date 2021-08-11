---
title: Rozdział 2 — Wymagania dotyczące modułu
description: Ten artykuł zawiera opis wymagań dotyczących kompilowania modułu ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b814e7c2b510093b809b70b02d9a11ed39996d114f2306e0993893799453cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791962"
---
# <a name="chapter-2---module-requirements"></a>Rozdział 2 — Wymagania dotyczące modułu

Moduł ThreadX zawiera aksję, która definiuje podstawowe cechy modułu. Po niej następuje obszar instrukcji modułu. Moduły mogą być wykonywane na miejscu lub przed wykonaniem mogą zostać załadowane do obszaru pamięci modułu przez Menedżera modułów. Jedynym wymaganiem jest, aby zawsze znajdował się on pod pierwszym adresem modułu. Rysunek 2 ilustruje podstawowy układ modułu.

| Układ modułu |
|:---:|
| \[module module\]         |
| \[obszar instrukcji modułu\] |
| \[obszar pamięci RAM modułu\]         |

**Rysunek 2.** Układ modułu

> [!NOTE]
> Moduły muszą być budowaną z odpowiednim kodem niezależnym od pozycji i opcjami kompilatora danych/łączenia. Umożliwia to wykonywanie modułu w dowolnym obszarze pamięci.

Po utworzeniu wątku modułu przydzielane jest drugie miejsce na stos, gdy wątek znajduje się w jądrze chronionym pamięcią. Rozmiar obszaru stosu jądra wątku można skonfigurować przez użytkownika przy użyciu TXM_MODULE_KERNEL_STACK_SIZE **w** **_txm_module_port.h_*_. Dzięki temu mniejszy rozmiar stosu* może być używany podczas tworzenia wątku modułu, ponieważ stos określony przez użytkownika podczas wywoływania funkcji _ _tx_thread_create_** jest używany tylko w module .

> [!NOTE]
> Górna część stosu wątku modułu zawiera strukturę informacji o wpisie wątku (**TXM_MODULE_THREAD_ENTRY_INFO**), więc rozmiar dostępnego stosu jest zmniejszany o rozmiar tej struktury. Podczas tworzenia wątku w module zwiększ jego rozmiar stosu przynajmniej o ten rozmiar tej struktury.

Poniższe kroki są wymagane do tworzenia i budowania modułu ThreadX (każdy krok został opisany bardziej szczegółowo poniżej).

1. Wszystkie pliki C w module muszą zostać #define **TXM_MODULE** przed dodaniem **_pliku txm_module.h._** Można to zrobić w kompilowanym pliku źródłowym lub w ramach ustawień projektu. W ten sposób ponownie mapuje wywołania interfejsu API ThreadX do wersji interfejsu API specyficznej dla modułu, która wywołuje funkcję dispatch w menedżerze modułów w rezyduacyjną, aby wykonać wywołanie rzeczywistej funkcji interfejsu API.
2. Każdy moduł musi mieć swój pierwszy adres obszaru instrukcji, który definiuje charakterystykę i wymagania dotyczące zasobów modułu.
3. Każdy moduł musi łączyć instrukcje na początku obszaru instrukcji modułu.
4. Każdy moduł musi łączyć się z biblioteką modułów ***(txm.a),*** która zawiera funkcje specyficzne dla modułu używane do interakcji z ThreadX.

## <a name="module-sources"></a>Źródła modułów

Moduły ThreadX mają własny zestaw plików źródłowych, które są przeznaczone do linku i znajdują się bezpośrednio z kodem źródłowym modułu. Te pliki zapewniają most między oddzielnym modułem a menedżerem modułów. Pliki modułu są następujące.

| Nazwa pliku | Zawartość |
|---|---|
| **txm_module.h** | Dołącz plik, który definiuje informacje o module. |
| **txm_module_port.h** | Dołącz plik, który definiuje informacje o module specyficznym dla portu. |
| **txm_module_user.h** | Definiuje i wartości, które użytkownik może dostosować. |
| **txm_module_initialize.s [1][3]** | Wywołuje funkcje wewnętrzne do modułu uruchamiania. |
| **txm_module_preamble. \{ s/S/68\}** | Plik zestawu chłoniaka modułu. Ten plik definiuje różne atrybuty specyficzne dla modułu i jest połączony z kodem aplikacji modułu. |
| **txm_module_application_request.c [1]** | Funkcja żądania aplikacji modułu wysyła żądanie specyficzne dla aplikacji do kodu źródłowego. |
| **txm_module_callback_request_thread_entry.c &nbsp; [1]** | Wątek wywołania zwrotnego modułu odpowiedzialny za przetwarzanie wywołań zwrotnych żądanych przez moduł, w tym czasomierze i wywołania zwrotne powiadomień. |
| **txm_*.c [1][2]** | Standardowe usługi interfejsu API ThreadX, które wywołują dyspozytor jądra.
| **txm_module_object_allocate.c [1]** | Funkcja Module do przydzielania pamięci dla obiektów modułu znajdujących się w puli pamięci menedżera. |
| **txm_module_object_deallocate.c [1]** | Funkcja Module do cofniania alokacji pamięci dla obiektów modułu znajdujących się w puli pamięci menedżera. |
| **txm_module_object_pointer_get.c [1]** | Funkcja Module pobiera wskaźnik do obiektu systemowego. |
| **txm_module_object_pointer_get_extended.c [1]** | Funkcja Module pobiera wskaźnik do obiektu systemowego, bezpieczeństwo długości nazwy. |
| **txm_module_thread_shell_entry.c [1]** | Funkcja wpisu wątku modułu. |
| **txm_module_thread_system_suspend.c [1]** | Funkcja Module do zawieszania wątku. |

**[1]** Znajduje się w **_bibliotece txm.a_**.

**[2]** Te pliki mają taką samą nazwę jak pliki interfejsu API ThreadX z prefiksem **txm_** zamiast **prefiksu tx_** prefiksu.

**[3]** **Plik txm_module_initialize.s** jest tylko dla portów korzystających z narzędzi arm.

## <a name="module-preamble"></a>Modułu

Podczas pracy z modułem zdefiniowano charakterystyki i zasoby modułu. Informacje, takie jak funkcja wpisu początkowego wątku i początkowy obszar pamięci skojarzony z wątkiem, są zdefiniowane w wątku. Przykłady specyficzne dla portu znajdują się w [dodatku](appendix.md). Rysunek 3 przedstawia przykład modułu ThreadX dla ogólnego obiektu docelowego (wiersze rozpoczynające się od * są wartościami zwykle modyfikowanymi przez aplikację):

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

W większości przypadków deweloper musi tylko zdefiniować wątek początkowy modułu (przesunięcie 0x1C), identyfikator modułu (przesunięcie 0x10), priorytet wątku uruchamiania/zatrzymania (przesunięcie 0x24) i rozmiar stosu wątku uruchamiania/zatrzymania (przesunięcie 0x28). Powyższy pokaz jest tak ustawiony, że początkowy wątek modułu to ***demo_module_start** _, identyfikator modułu _*_to 0x12345678 , a_*_ wątek początkowy ma priorytet _*_1_*_, a rozmiar stosu to _ *_2048_** bajtów.

Niektóre aplikacje mogą opcjonalnie definiować wątek zatrzymywania, który jest wykonywany w momencie zatrzymania modułu przez Menedżera modułów. Ponadto niektóre aplikacje mogą korzystać z pola Właściwości modułu zdefiniowanego w następujący sposób.

## <a name="module-properties-bit-map"></a>Mapa bitowa właściwości modułu

W poniższej tabeli przedstawiono przykład mapy bitowej właściwości. Mapy bitowe właściwości specyficzne dla portu znajdują się w [dodatku](appendix.md).

| Bitowych | Wartość | Znaczenie |
|---|---|---|
| 0 | 0<br />1 | Wykonywanie w trybie uprzywilejowanym<br />Wykonywanie w trybie użytkownika |
| 1 | 0<br />1 | Brak ochrony mpu<br />Ochrona w trybie MPU (musi być wybrany tryb użytkownika) |
| 2 | 0<br />1 | Wyłączanie dostępu do pamięci udostępnionej/zewnętrznej<br />Włączanie dostępu do pamięci udostępnionej/zewnętrznej |
| [23-3] | 0 | Zarezerwowany
| [31-24] | <br />0x01<br />0x02<br />0x03 | **Identyfikator kompilatora**<br />Iar<br />ARM<br />Gnu |


## <a name="module-linker-control-file"></a>Plik sterowania linkerem modułu

Podczas tworzenia modułu należy umieścić go przed inną sekcją kodu. Moduł musi być budowaną sekcją kodu i danych niezależną od pozycji. Przykładowe pliki linkera specyficznego dla portu znajdują się w [dodatku](appendix.md).

## <a name="module-threadx-library"></a>Biblioteka ThreadX modułu

Każdy moduł musi łączyć się ze specjalną, zorientowaną na moduł biblioteką ThreadX. Ta biblioteka zapewnia dostęp do usług ThreadX w kodzie źródłowym. Większość dostępu jest zapewniana za pośrednictwem ***txm_ \* .c.*** Poniżej przedstawiono przykład wywołania dostępu do modułu dla funkcji interfejsu API ThreadX **_tx_thread_relinquish_* _ (w _*_ \_ txm_thread_relinquish.c \* ).).

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

W tym przykładzie wskaźnik funkcji dostarczony przez menedżera modułów służy do wywoływania  funkcji wysyłania menedżera modułów z identyfikatorem skojarzonym z tx_thread_relinquish modułem. Ta usługa nie przyjmuje żadnych parametrów.

## <a name="module-example"></a>Przykład modułu

Poniżej przedstawiono przykład standardowego pokazu ThreadX w postaci modułu. Główne różnice między standardowym pokazem ThreadX i pokazem modułów są.

1. Zamiana ***tx_api.h** _ na _ *_txm_module.h_**
2. Dodanie **#define TXM_MODULE** przed **_txm_module.h_**
3. Zastąpienie ***main** _ i _ *tx_application_define** z **_demo_module_start_**
4. *Deklarowanie wskaźników* do obiektów ThreadX, a nie do samych obiektów.

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

## <a name="building-modules"></a>Tworzenie modułów

Tworzenie modułu zależy od używanego łańcucha narzędzi. Zobacz [dodatek,](appendix.md) aby uzyskać przykłady specyficzne dla portu. Typowe działania dla wszystkich portów są następujące.

- Tworzenie biblioteki modułów
- Tworzenie aplikacji modułu

Każdy moduł musi mieć bibliotekę **txm_module_preamble** (konfigurację specjalnie dla tego modułu) i bibliotekę modułów (na przykład **_txm.a)._**
