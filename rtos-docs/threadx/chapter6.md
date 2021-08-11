---
title: Rozdział 6 — system pokazu dla Azure RTOS ThreadX
description: Ten rozdział zawiera opis systemu demonstracyjnego, który jest dostarczany ze wszystkimi pakietami obsługi Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 67054d67d0a6babc50a489c4ec4b738abf3efccab10060d307106e8344b00d02
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783377"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a>Rozdział 6 — system pokazu dla Azure RTOS ThreadX

Ten rozdział zawiera opis systemu demonstracyjnego, który jest dostarczany ze wszystkimi pakietami obsługi Azure RTOS ThreadX.

## <a name="overview"></a>Omówienie

Każda dystrybucja produktu ThreadX zawiera system demonstracyjny, który działa na wszystkich obsługiwanych mikroprocesorach.

Ten przykładowy system jest zdefiniowany w pliku dystrybucji ***w pliku demo_threadx.c*** i został zaprojektowany w celu zilustrowania, jak ThreadX jest używany w osadzonym środowisku wielowątkowym. Pokaz składa się z inicjowania, ośmiu wątków, jednej puli bajtów, jednej puli bloków, jednej kolejki, jednego semafora, jednego mutexu i jednej grupy flag zdarzeń.

> [!NOTE]
> *Z wyjątkiem rozmiaru stosu wątku aplikacja demonstracyjna jest identyczna na wszystkich procesorach obsługiwanych przez ThreadX.*

Pełna lista ***demo_threadx.c,*** w tym numery wiersza przywołyne w pozostałej części tego rozdziału.

## <a name="application-define"></a>Application Define

Funkcja ***tx_application_define*** jest wykonywana po zakończeniu podstawowej inicjalizacji ThreadX. Jest on odpowiedzialny za skonfigurowanie wszystkich początkowych zasobów systemowych, w tym wątków, kolejek, semaforów, mutexes, flag zdarzeń i pul pamięci.

Obiekt demonstracyjny ***tx_application_define** _ (_line cyfry 60–164*) tworzy obiekty demonstracyjne w następującej kolejności:

- byte_pool_0
- thread_0
- thread_1
- thread_2
- thread_3
- thread_4
- thread_5
- thread_6
- thread_7
- queue_0
- semaphore_0
- event_flags_0
- mutex_0
- block_pool_0

System demonstracyjny nie tworzy żadnych innych dodatkowych obiektów ThreadX. Jednak rzeczywista aplikacja może tworzyć obiekty systemowe w czasie wykonywania wewnątrz wykonywanych wątków.

### <a name="initial-execution"></a>Wykonanie początkowe

Wszystkie wątki są tworzone za pomocą **TX_AUTO_START** opcji. Dzięki temu są wstępnie gotowe do wykonania. Po ***tx_application_define*** sterowanie jest przekazywane do harmonogramu wątków i z tego do każdego pojedynczego wątku.

Kolejność wykonywania wątków zależy od ich priorytetu i kolejności ich tworzenia. W systemie pokazowym ***thread_0*** najpierw, ponieważ ma najwyższy priorytet (został utworzony *z priorytetem 1*). Po ***thread_0,*** ***thread_5*** jest wykonywany, a następnie wykonywania ***thread_3** _, _*_thread_4_*_, _*_thread_6,_*_ _* _thread_7_**, ***thread_1**_, i na końcu _*_thread_2_**.

> [!NOTE]
> *Mimo że **thread_3** i **thread_4** mają ten sam priorytet (oba utworzone z priorytetem 8), thread_3 najpierw wykonywane.  Jest to spowodowane **tym, thread_3** została utworzona i stała się gotowa przed thread_4 **.** Wątki o równym priorytecie są wykonywane w sposób FIFO.*

## <a name="thread-0"></a>Wątek 0

Funkcja ***thread_0_entry*** punkt wejścia wątku *(wiersze 167–190).* ***Thread_0*** jest pierwszym wątkiem w systemie pokazowym do wykonania. Jej przetwarzanie jest proste: zwiększa swój licznik, uśpije 10 takt czasomierza, ustawia flagę zdarzenia w celu wznowienia thread_5 ***,*** a następnie powtarza sekwencję.

***Thread_0*** to wątek o najwyższym priorytecie w systemie. Po wygaśnięciu żądanego uśpienia wywłaszczy dowolny inny wątek wykonujący w pokazie.

## <a name="thread-1"></a>Wątek 1

Funkcja ***thread_1_entry** _ oznacza punkt wejścia wątku _(wiersze 193–216).****Thread_1*** jest drugim do ostatniego wątkiem w systemie pokazowym do wykonania. Jego przetwarzanie polega na zwiększaniu licznika, wysyłaniu* komunikatu do thread_2 ( za pośrednictwem * ***queue_0***) i powtarzaniu sekwencji. Zwróć uwagę,**że thread_1**_ zawiesza się po _*_queue_0_*_ zapełnieniu (_line 207*).

## <a name="thread-2"></a>Wątek 2

Funkcja ***thread_2_entry*** punkt wejścia wątku *(wiersze 219–243).* ***Thread_2*** jest ostatnim wątkiem w systemie pokazowym do wykonania. Jego przetwarzanie polega na zwiększaniu licznika, uzyskiwaniu komunikatu z thread_1 ***(za*** pośrednictwem queue_0 ***)*** i powtarzaniu sekwencji. Zwróć uwagę,**że wartość * thread_2** _ jest wstrzymywana za każdym _*_razem, queue_0_*_ pusta (_line 233*).

Chociaż ***thread_1** _ i _ *_thread_2_** mają* najniższy priorytet w systemie pokazowym (priorytet 16*), są to wątki *3 i 4*

są również jedynymi wątkami, które są gotowe do wykonania przez większość czasu. Są one również jedynymi wątkami utworzonymi z zastosowaniem licowania w czasie *(wiersze 87 i 93).* Każdy wątek może być wykonywany dla maksymalnie 4 takt czasomierza przed wykonaniem drugiego wątku.

## <a name="threads-3-and-4"></a>Wątki 3 i 4

Funkcja ***thread_3_and_4_entry*** punkt wejścia zarówno ***thread_3** _, jak i _ *_thread_4_** (wiersze 246–280). Oba wątki mają priorytet 8, co sprawia, że są trzecim i czwartym wątkiem w systemie pokazowym do wykonania. Przetwarzanie dla każdego wątku jest takie samo: zwiększanie jego licznika, pobieranie ***semaphore_0,*** uśpienie dla 2 takt czasomierza, zwalnianie semaphore_0 ***i*** powtarzanie sekwencji. Zwróć uwagę, że każdy wątek jest wstrzymywany ***semaphore_0*** gdy jest niedostępny (wiersz 264).

Oba wątki używają tej samej funkcji do głównego przetwarzania.
Nie stanowi to żadnych problemów, ponieważ oba mają własny unikatowy stos, a język C jest naturalnie reentrant. Każdy wątek określa, który jest przez badanie parametru wejściowego wątku (wiersz 258), który jest konfigurowany podczas ich tworzenia (wiersze 102 i 109).

> [!NOTE]
> *Uzasadnione jest również uzyskanie bieżącego punktu wątku podczas wykonywania wątku i porównanie go z adresem bloku sterowania w celu określenia tożsamości wątku.*

## <a name="thread-5"></a>Wątek 5

Funkcja ***thread_5_entry*** punkt wejścia wątku (wiersze 283–305). ***Thread_5*** jest drugim wątkiem w systemie pokazowym do wykonania. Jego przetwarzanie polega na zwiększaniu licznika, uzyskiwaniu flagi zdarzenia z thread_0 ***(za*** pośrednictwem event_flags_0 ***)*** i powtarzaniu sekwencji. Zwróć ***uwagę, thread_5*** zawiesza się, gdy flaga zdarzenia w event_flags_0 ***jest*** dostępna (wiersz 298).

## <a name="threads-6-and-7"></a>Wątki 6 i 7

Funkcja ***thread_6_and_7_entry*** punkt wejścia zarówno ***thread_6** _, jak i _ *_thread_7_** (wiersze 307–358). Oba wątki mają priorytet 8, co sprawia, że są piątym i szóstym wątkiem w systemie pokazowym do wykonania. Przetwarzanie dla każdego wątku jest takie samo: zwiększanie licznika, dwukrotne pobieranie ***mutex_0,*** uśpienie  dla 2 takt czasomierza, dwukrotnie zwalnianie mutex_0 i powtarzanie sekwencji. Zwróć uwagę, że każdy wątek zawiesza ***się, mutex_0*** jest niedostępny (wiersz 325).

Oba wątki używają tej samej funkcji do głównego przetwarzania. Nie stanowi to żadnych problemów, ponieważ oba mają własny unikatowy stos, a język C jest naturalnie reentrant.
Każdy wątek określa, który jest przez badanie parametru wejściowego wątku (wiersz 319), który jest konfigurowany podczas ich tworzenia (wiersze 126 i 133).

## <a name="observing-the-demonstration"></a>Obserwowanie pokazu

Każdy z wątków demonstracyjnych zwiększa swój własny unikatowy licznik.
Aby sprawdzić działanie pokazu, można zbadać następujące liczniki:

- thread_0_counter
- thread_1_counter
- thread_2_counter
- thread_3_counter
- thread_4_counter
- thread_5_counter
- thread_6_counter
- thread_7_counter

Każdy z tych liczników powinien nadal rosnąć w czasie wykonywania pokazu, przy użyciu ***thread_1_counter** _ i _ *_thread_2_counter_** rosnącej z najszybszym szybkością.

## <a name="distribution-file-demo_threadxc"></a>Plik dystrybucji: demo_threadx.c

W tej sekcji jest wyświetlana pełna ***lista demo_threadx.c,*** w tym numery wiersza przywołyne w tym rozdziale.

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
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

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

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
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
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
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

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
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
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
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
