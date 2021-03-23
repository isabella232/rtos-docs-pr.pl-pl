---
title: Rozdział 6 — zdarzenia śledzenia usługi Azure RTO ThreadX
description: W tym rozdziale opisano zdarzenia usługi Azure RTO ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823460"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>Rozdział 6 — zdarzenia śledzenia usługi Azure RTO ThreadX

W tym rozdziale opisano zdarzenia usługi Azure RTO ThreadX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

Poniżej znajduje się lista zdarzeń ThreadX wyświetlanych przez TraceX:

| **Ikona**                         | **Znaczenie** |
| -------------------------------- | ------------------------------------- |
| ![Ikona wznowienia wątku wewnętrznego](./media/user-guide/tx-events/image1.png)    | Wewnętrzny wznowienie wątku  |
| ![Ikona wstrzymania wątku wewnętrznego](./media/user-guide/tx-events/image2.png)    | Zawieszenie wątku wewnętrznego |
| ![Ikona przejścia do procedury usługi przerwania](./media/user-guide/tx-events/image3.png)    | Wejście procedury usługi przerwania (ISR) |
| ![Ikona zakończenia procedury usługi przerwania](./media/user-guide/tx-events/image4.png)    | Zakończenie procedury usługi przerwania (ISR)  |
| ![Ikona wewnętrznego wycinka czasu](./media/user-guide/tx-events/image5.png)    | Wewnętrzny czas wycinka |
| ![Ikona uruchamiania](./media/user-guide/tx-events/image6.png)    | Uruchomienie |
| ![Ikona blokowania alokacji puli](./media/user-guide/tx-events/image7.png)    | **Przydziel pulę bloków** (*tx_block_allocate*)  |
| ![Ikona tworzenia puli blokowej](./media/user-guide/tx-events/image8.png)    | **Blokuj Tworzenie puli** (*tx_block_pool_create*) |
| ![Ikona usuwania puli blokowej](./media/user-guide/tx-events/image9.png)    | **Blokuj Usuwanie puli** (*tx_block_pool_delete*) |
| ![Ikona uzyskiwania informacji o puli bloku](./media/user-guide/tx-events/image10.png)    | **Pobierz informacje o puli bloków** (*tx_block_pool_info_get*) |
| ![Informacje o wydajności puli bloku](./media/user-guide/tx-events/image11.png)    | **Uzyskaj informacje o wydajności puli bloku** (*tx_block_pool_performance_info_get*) |
| ![Ikona blokowania informacji o wydajności systemu puli](./media/user-guide/tx-events/image12.png)    | **Odczytaj informacje o wydajności systemu puli** (*tx_block_pool_performance_system_info_get*) |
| ![Ikona zablokowania priorytetów puli](./media/user-guide/tx-events/image13.png)    | **Zablokuj priorytety puli** (*tx_block_pool_prioritize*) |
| ![Ikona blokowania wersji do puli](./media/user-guide/tx-events/image14.png)    | **Blokuj wydanie do puli** (*tx_block_release*) |
| ![Ikona pamięci przydziału puli bajtów](./media/user-guide/tx-events/image15.png)    | **Alokacja pamięci w puli bajtów** (*tx_byte_allocate*) |
| ![Ikona tworzenia puli bajtów](./media/user-guide/tx-events/image16.png)    | **Tworzenie puli bajtów** (*tx_byte_pool_create*) |
| ![Ikona usuwania puli bajtów](./media/user-guide/tx-events/image17.png)    | **Usuwanie puli bajtów** (*tx_byte_pool_delete*) |
| ![Ikona pobierania informacji o puli bajtów](./media/user-guide/tx-events/image18.png)    | **Pobieranie informacji o puli bajtów** (*tx_byte_pool_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności puli bajtów](./media/user-guide/tx-events/image19.png)    | **Pobieranie informacji o wydajności puli bajtów** (*tx_byte_pool_performance_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności systemu puli bajtów](./media/user-guide/tx-events/image20.png)    | **Pobieranie informacji o wydajności systemu w puli bajtów** (*tx_byte_pool_performance_system_info_get*) |
| ![Ikona priorytet puli bajtów](./media/user-guide/tx-events/image21.png)    | **Priorytetyzacja puli bajtów** (*tx_byte_pool_prioritize*) |
| ![Ikona zwalniania pamięci do puli](./media/user-guide/tx-events/image22.png)    | **Zwolnij pamięć w puli** (*tx_byte_release*) |
| ![Ikona tworzenia flag zdarzeń](./media/user-guide/tx-events/image23.png)    | **Flagi zdarzeń Create** (*tx_event_flags_create*) |
| ![Ikona usuwania flag zdarzeń](./media/user-guide/tx-events/image24.png)    | **Flagi zdarzenia Delete** (*tx_event_flags_delete*) |
| ![Ikona pobierania flag zdarzeń](./media/user-guide/tx-events/image25.png)    | **Flagi zdarzenia Get** (*tx_event_flags_get*) |
| ![Ikona uzyskiwania informacji o flagach zdarzeń](./media/user-guide/tx-events/image26.png)    | **Informacje o flagach zdarzenia Get** (*tx_event_flags_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności flag zdarzeń](./media/user-guide/tx-events/image27.png)    | **Informacje o wydajności flag zdarzeń Get** (*tx_event_flags_performance_info_get*) |
| ![Ikona zdarzenia informacje o wydajności systemu](./media/user-guide/tx-events/image28.png)    | **Flagi zdarzeń pobieranie informacji o wydajności systemu** (*tx_event_flags_performance_system_info_get*) |
| ![Ikona zestawu flag zdarzeń](./media/user-guide/tx-events/image29.png)    | **Ustawione flagi zdarzeń** (*tx_event_flags_set*) |
| ![Ikona powiadomienia ustawiona flaga zdarzenia](./media/user-guide/tx-events/image30.png)    | **Ustawianie flag zdarzeń powiadamiania** (*tx_event_flags_set_notify*) |
| ![Ikona włączania/wyłączania przerwań](./media/user-guide/tx-events/image31.png)    | **Włącz/Wyłącz przerwania** (*tx_interrupt_control*) |
| ![Ikona tworzenia obiektu mutex](./media/user-guide/tx-events/image32.png)    | **Tworzenie obiektu mutex** (*tx_mutex_create*) |
| ![Ikona usuwania muteksu](./media/user-guide/tx-events/image33.png)    | **Usuwanie obiektu mutex** (*tx_mutex_delete*) |
| ![Ikona pobierania muteksu](./media/user-guide/tx-events/image34.png)    | **Pobieranie obiektu mutex** (*tx_mutex_get*) |
| ![Ikona pobierania informacji o muteksie](./media/user-guide/tx-events/image35.png)    | **Pobieranie informacji o muteksie** (*tx_mutex_info_get*) |
| ![Ikona pobierania informacji o wydajności muteksu](./media/user-guide/tx-events/image36.png)    | **Pobieranie informacji o wydajności muteksu** (*tx_mutex_performance_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności systemu muteksu](./media/user-guide/tx-events/image37.png)    | **Pobieranie informacji o wydajności systemu muteksu** (*tx_mutex_performance_system_info_get*) |
| ![Ikona priorytetyzacji obiektu mutex](./media/user-guide/tx-events/image38.png)    | **Priorytetyzacja obiektu mutex** (*tx_mutex_prioritize*) |
| ![Ikona Put obiektu mutex](./media/user-guide/tx-events/image39.png)    | **Put muteksu** (*tx_mutex_put*) |
| ![Ikona tworzenia kolejki](./media/user-guide/tx-events/image40.png)    | **Tworzenie kolejki** (*tx_queue_create*) |
| ![Ikona usuwania kolejki](./media/user-guide/tx-events/image41.png)    | **Usuwanie kolejki** (*tx_queue_delete*) |
| ![Ikona opróżniania kolejki](./media/user-guide/tx-events/image42.png)    | **Opróżnianie kolejki** (*tx_queue_flush*) |
| ![Ikona wysyłania z kolejki](./media/user-guide/tx-events/image43.png)    | **Wyślij fronton kolejki** (*tx_queue_front_send*) |
| ![Ikona pobierania informacji o kolejce](./media/user-guide/tx-events/image44.png)    | **Pobieranie informacji o kolejce** (*tx_queue_info_get*) |
| ![Ikona pobierania informacji o wydajności kolejki](./media/user-guide/tx-events/image45.png)    | **Pobierz informacje o wydajności kolejki** (*tx_queue_performance_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności systemu kolejkowania](./media/user-guide/tx-events/image46.png)    | **Pobierz informacje o wydajności systemu** (*tx_queue_performance_system_info_get*) |
| ![Ikona priorytetyzacji kolejki](./media/user-guide/tx-events/image47.png)    | **Priorytetyzacja kolejki** (*tx_queue_prioritize*) |
| ![Ikona komunikatu odbierania kolejki](./media/user-guide/tx-events/image48.png)    | **Komunikat odbioru kolejki** (*tx_queue_receive*) |
| ![Ikona wysyłania komunikatu w kolejce](./media/user-guide/tx-events/image49.png)    | **Wyślij wiadomość do kolejki** (*tx_queue_send*) |
| ![Ikona powiadomienia o wysłaniu kolejki](./media/user-guide/tx-events/image50.png)    | **Powiadomienie o wysłaniu kolejki** (*tx_queue_send_notify*) |
| ![Ikona umieszczenia sufitu semafora](./media/user-guide/tx-events/image51.png)    | **Umieszczenie sufitu semafora** (*tx_semaphore_ceiling_put*) |
| ![Ikona tworzenia semafora](./media/user-guide/tx-events/image52.png)    | **Tworzenie semafora** (*tx_semaphore_create*) |
| ![Ikona usuwania semafora](./media/user-guide/tx-events/image53.png)    | **Usuwanie semafora** (*tx_semaphore_delete*) |
| ![Ikona pobierania semafora](./media/user-guide/tx-events/image54.png)    | **Pobieranie semafora** (*tx_semaphore_get*) |
| ![Ikona pobierania informacji o semaforach](./media/user-guide/tx-events/image55.png)    | **Pobieranie informacji o semaforze** (*tx_semaphore_info_get*) |
| ![Ikona pobierania informacji o wydajności semafora](./media/user-guide/tx-events/image56.png)    | **Pobieranie informacji o wydajności semaforów** (*tx_semaphroe_performance_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności systemu semafora](./media/user-guide/tx-events/image57.png)    | **Pobieranie informacji o wydajności systemu semaforów** (*tx_semaphore_performance_system_info_get*) |
| ![Ikona priorytetyzacji semaforów](./media/user-guide/tx-events/image58.png)    | **Priorytetyzacja semaforów** (*tx_semaphore_prioritize*) |
| ![Ikona umieszczenia semafora](./media/user-guide/tx-events/image59.png)    | **Umieszczenie semafora** (*tx_semaphore_put*) |
| ![Ikona powiadomienia dotyczącego umieszczenia semafora](./media/user-guide/tx-events/image60.png)    | **Powiadomienie o wprowadzeniu semafora** (*tx_semaphore_put_notify*) |
| ![Ikona tworzenia wątku](./media/user-guide/tx-events/image61.png)    | **Tworzenie wątku** (*tx_thread_create*) |
| ![Ikona usuwania wątku](./media/user-guide/tx-events/image62.png)    | **Usuwanie wątku** (*tx_thread_delete*) |
| ![Ikona powiadomienia o wyjściu/wprowadzeniu wątku](./media/user-guide/tx-events/image63.png)    | **Powiadomienie o wyjściu/wprowadzeniu wątku** (*tx_thread_entry_exit_notify*) |
| ![Ikona identyfikacji wątku](./media/user-guide/tx-events/image64.png)    | **Identyfikator wątku** (*tx_thread_identify*) |
| ![Ikona pobierania informacji o wątkach](./media/user-guide/tx-events/image65.png)    | **Pobieranie informacji o wątku** (*tx_thread_info_get*) |
| ![Ikona uzyskiwania informacji o wydajności wątków](./media/user-guide/tx-events/image66.png)    | **Informacje o wydajności wątku Get** (*tx_thread_performance_info_get*) |
| ![Ikona uzyskiwania informacji o systemie wydajności wątków](./media/user-guide/tx-events/image67.png)    | **Informacje o systemie wydajności wątku Get** (*tx_thread_performance_system_info_get*) |
| ![Ikona zmiany zastępujący wątek](./media/user-guide/tx-events/image68.png)    | **Zmiana zastępujący wątek** (*tx_thread_preemption_change*) |
| ![Ikona zmiany priorytetu wątku](./media/user-guide/tx-events/image69.png)    | **Zmiana priorytetu wątku** (*tx_thread_priority_change*) |
| ![Ikona zrzeczenia wątku](./media/user-guide/tx-events/image70.png)    | **Zrzeka się wątku** (*tx_thread_relinquish*) |
| ![Ikona resetowania wątku](./media/user-guide/tx-events/image71.png)    | **Resetowanie wątku** (*tx_thread_reset*) |
| ![* Ikona wznowienia wątku](./media/user-guide/tx-events/image72.png)    | **Wznowienie wątku** (**tx_thread_resume*) |
| ![Ikona uśpienia wątku](./media/user-guide/tx-events/image73.png)    | **Wątek uśpienia** (*tx_thread_sleep*) * |
| ![Ikona powiadomienia o błędzie stosu wątku](./media/user-guide/tx-events/image74.png)    | **Powiadomienie o błędzie stosu wątku** (*tx_thread_stack_error_notify*) |
| ![Ikona wstrzymania wątku](./media/user-guide/tx-events/image75.png)    | **Wstrzymywanie wątku** (*tx_thread_suspend*) |
| ![Ikona zakończenia wątku](./media/user-guide/tx-events/image76.png)    | **Zakończenie wątku** (*tx_thread_terminate*) |
| ![Ikona zmiany czasu wątku](./media/user-guide/tx-events/image77.png)    | **Zmiana wycinka czasu wątku** (*tx_thread_time_slice_change*) |
| ![Ikona przerwania oczekiwania wątku](./media/user-guide/tx-events/image78.png)    | **Przerwanie oczekiwania wątku** (*tx_thread_wait_abort*) |
| ![Ikona uzyskiwania czasu](./media/user-guide/tx-events/image79.png)    | **Czas Get** (*tx_time_get*) |
| ![Ikona zestawu czasu](./media/user-guide/tx-events/image80.png)    | **Zestaw czasu** (*tx_time_set*) |
| ![* Ikona aktywowania czasomierza](./media/user-guide/tx-events/image81.png)    | **Aktywowanie czasomierza** (*tx_timer_activate*) |
| ![Ikona zmiany czasomierza](./media/user-guide/tx-events/image82.png)    | **Zmiana czasomierza** (*tx_timer_change*) |
| ![Ikona tworzenia czasomierza](./media/user-guide/tx-events/image83.png)    | **Tworzenie czasomierza** (*tx_timer_create*) |
| ![Ikona dezaktywacji czasomierza](./media/user-guide/tx-events/image84.png)    | **Dezaktywacja czasomierza** (*tx_timer_deactivate*) |
| ![Ikona usuwania czasomierza](./media/user-guide/tx-events/image85.png)    | **Usuwanie czasomierza** (*tx_timer_delete*) |
| ![Ikona pobierania informacji o czasomierzu](./media/user-guide/tx-events/image86.png)    | **Pobieranie informacji o czasomierzu** (*tx_timer_info_get*) |
| ![Ikona pobierania informacji o wydajności czasomierza](./media/user-guide/tx-events/image87.png)    | **Informacje o wydajności czasomierza Pobierz** (*tx_timer_performance_info_get*) |
| ![* Ikona pobierania informacji o systemie wydajności czasomierza](./media/user-guide/tx-events/image88.png)    | **Informacje o systemie wydajności czasomierza Get** (*tx_timer_performance_system_info_get*) |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | **Zdarzenie zdefiniowane przez użytkownika** (zobacz rozdział 10)    |

## <a name="event-descriptions"></a>Opisy zdarzeń

### <a name="internal-thread-resume"></a>Wewnętrzny wznowienie wątku

#### <a name="internal-thread-resume"></a>Wewnętrzny wznowienie wątku

**Ikona** ![ Ikona wznowienia wątku wewnętrznego](./media/user-guide/tx-events/image1.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wznawia wątek do wykonania. Jeśli określony wątek jest najwyższym priorytetem i przekroczenie — próg nie blokuje jego wykonywania, System rozpocznie wykonywanie tego nowo przygotowanego wątku.

**Pola informacji**

- Pole informacji 1: wskaźnik wznawiania wątku.
- Pole informacji 2: poprzedni stan wznawianego wątku w następujący sposób:

  |  Stan wątku                     | Wartość        |
  |---------------------------------- | --------|
  |  TX_READY                         | 0       |
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Pole informacji 3: wartość wskaźnika stosu podczas wywołania. 
- Pole informacji 4: wskaźnik do następnego priorytetu wątku do wykonania.

### <a name="internal-thread-suspend"></a>Zawieszenie wątku wewnętrznego

#### <a name="internal-thread-suspend"></a>Zawieszenie wątku wewnętrznego

**Ikona** ![ Ikona wstrzymania wątku wewnętrznego](./media/user-guide/tx-events/image2.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wstrzymuje wykonywanie wątku. Kolejny wątek o najwyższym priorytecie gotowy do wykonania jest umieszczany w czwartym polu informacji. Jeśli ta wartość jest RÓWNa NULL, nie istnieje żaden inny wątek gotowy do wykonania i system jest bezczynny.

**Pola informacji**

- Pole informacji 1: wskaźnik do wstrzymanego wątku.
- Pole informacji 2: nowy stan zawieszenia wątku w następujący sposób:

  |  Stan wątku                     | Wartość        |
  |---------------------------------- | --------|
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Pole informacji 3: wartość wskaźnika stosu podczas wywołania. Pole informacji 4: wskaźnik do następnego priorytetu wątku do wykonania. Jeśli wartość jest równa NULL, system jest bezczynny.

### <a name="interrupt-service-routine-isr-enter"></a>Wejście procedury usługi przerwania (ISR) 

#### <a name="enter-isr"></a>Wprowadź ISR 

**Ikona** ![ Ikona wprowadzania I S](./media/user-guide/tx-events/image3.png)

**Opis**

To zdarzenie przedstawia wprowadzenie procedury usługi przerwania (ISR) w aplikacji. Wykonanie procedury usługi przerwania jest kontynuowane do momentu zakończenia zdarzenia ISR.

**Pola informacji**

- Pole informacji 1: wartość wskaźnika stosu podczas wywołania.
- Pole informacji 2: zdefiniowany przez aplikację numer ISR (opcjonalnie).
- Pole informacji 3: zagnieżdżona liczba przerwań.
- Pole informacji 4: Flaga wyłączenia wewnętrznej zastępujące.

### <a name="interrupt-service-routine-isr-exit"></a>Zakończenie procedury usługi przerwania (ISR) 

#### <a name="exit-isr"></a>Wyjdź z procedury ISR

**Ikona** ![ Ikona zamykania I języka R](./media/user-guide/tx-events/image4.png)

**Opis**

To zdarzenie reprezentuje zakończenie procedury usługi przerwania (ISR) w aplikacji.

**Pola informacji**

- Pole informacji 1: wartość wskaźnika stosu podczas wywołania.
- Pole informacji 2: zdefiniowany przez aplikację numer ISR (opcjonalnie).
- Pole informacji 3: zagnieżdżona liczba przerwań.
- Pole informacji 4: Flaga wyłączenia wewnętrznej zastępujące.

### <a name="internal-time-slice"></a>Wewnętrzny czas wycinka

#### <a name="internal-time-slice"></a>Wewnętrzny czas wycinka

**Ikona** ![ Ikona wewnętrznego wycinka czasu](./media/user-guide/tx-events/image5.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wykonuje operację wycinka czasu. Następny wątek o takim samym priorytecie jest umieszczany w pierwszym polu informacji. Jeśli ta wartość jest taka sama jak bieżący wątek, nie wykonano wycinka czasu.

- Pole informacji 1: wskaźnik do następnego wątku do wykonania.
- Pole informacji 2: zagnieżdżona liczba przerwań.
- Pole informacji 3: Flaga wyłączenia wewnętrznej zastępujące.
- Pole informacji 4: wartość wskaźnika stosu podczas wywołania.

### <a name="running"></a>Uruchomienie

#### <a name="running-in-context"></a>Uruchamianie w kontekście

**Ikona** ![ Ikona uruchamiania](./media/user-guide/tx-events/image6.png)

**Opis**

To zdarzenie reprezentuje działające w kontekście wątku lub bezczynnym systemie. Służy do zilustrowania kolejnych zmian w kontekście w wyniku przerwania.

**Pola informacji**
- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="block-allocate"></a>Zablokuj alokację 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**Ikona** ![ Ikona blokowania alokacji](./media/user-guide/tx-events/image7.png)

**Opis**

To zdarzenie reprezentuje przypisanie bloku pamięci za pośrednictwem tx_block_allocate. Jeśli to się powiedzie, adres przydzielony blok jest zwracany w drugim polu informacji.

**Pola informacji**
- Pole informacji 1: wskaźnik do odpowiedniej puli bloków.
- Pole informacji 2: wskaźnik do zwróconego bloku pamięci (Jeśli powodzenie).
- Pole informacji 3: opcja oczekiwania dostarczona do wywołania tx_block_allocate.
- Pole informacji 4: pozostałe dostępne bloki w puli po tej alokacji.

### <a name="block-pool-create"></a>Tworzenie puli blokowej

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**Ikona** ![ Ikona tworzenia puli blokowej](./media/user-guide/tx-events/image8.png)

**Opis**

To zdarzenie reprezentuje Tworzenie puli bloków pamięci za pośrednictwem tx_block_pool_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiadającego bloku sterowania puli bloku.
- Pole informacji 2: wskaźnik do obszaru pamięci początkowej puli.
- Pole informacji 3: liczba bloków w puli. Pole informacji 4: rozmiar każdego bloku w puli w bajtach.

### <a name="block-pool-delete"></a>Blokuj Usuwanie puli

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**Ikona** ![ Ikona usuwania puli blokowej](./media/user-guide/tx-events/image9.png)

**Opis**

To zdarzenie reprezentuje usunięcie puli bloków pamięci za pośrednictwem tx_block_pool_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku kontroli puli blokowej.
- Pole informacji 2: wartość wskaźnika stosu podczas wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="block-pool-information-get"></a>Uzyskaj informacje o puli bloku 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**Ikona** ![ Ikona uzyskiwania informacji o puli bloku](./media/user-guide/tx-events/image10.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o puli bloków pamięci za pośrednictwem tx_block_pool_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku kontroli puli blokowej.
- Pole informacji 2: wartość wskaźnika stosu podczas wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="block-pool-performance-information-get"></a>Uzyskaj informacje o wydajności puli bloku

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**Ikona** ![ Ikona uzyskiwania informacji o wydajności puli blokowych](./media/user-guide/tx-events/image11.png)

**Opis**

To zdarzenie reprezentuje informacje o wydajności puli bloków pamięci za pośrednictwem tx_block_pool_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku kontroli puli blokowej.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="block-pool-performance-system-information-get"></a>Uzyskaj informacje o wydajności systemu dla puli

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**Ikona** ![ Ikona uzyskiwania informacji o systemie wydajności puli blokowej](./media/user-guide/tx-events/image12.png)

**Opis**

To zdarzenie reprezentuje informacje o wydajności wszystkich pul bloków pamięci za pośrednictwem tx_block_pool_performance_system_info_get.

**Pola informacji**
- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="block-pool-prioritize"></a>Priorytet puli bloków

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**Ikona** ![ Ikona zablokowania priorytetów puli](./media/user-guide/tx-events/image13.png)

**Opis**

To zdarzenie przedstawia umieszczenie wątku zawieszenia HighestPriority na początku listy zawieszania puli bloku. Jeśli jest to wykonywane przed wywołaniem tx_block_release, wątek o najwyższym priorytecie zostanie odebrany.

**Pola informacji**
- Pole informacji 1: wskaźnik puli bloków pamięci.
- Pole informacji 2: liczba wątków zawieszonych w tej puli bloku.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="block-release"></a>Blokuj wydanie 

#### <a name="tx_block_release"></a>tx_block_release

**Ikona** ![ Ikona bloku wersji](./media/user-guide/tx-events/image14.png)

**Opis**

To zdarzenie reprezentuje wydawanie wcześniej przydzielonych bloków z powrotem do puli blokowej.

**Pola informacji**

- Pole informacji 1: wskaźnik puli bloków pamięci.
- Pole informacji 2: wskaźnik do zablokowania do wydania.
- Pole informacji 3: liczba wątków zawieszonych w tej puli bloku.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="byte-allocate"></a>Przydział bajtów 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**Ikona** ![ Ikona przydziału bajtów](./media/user-guide/tx-events/image15.png)

**Opis**

To zdarzenie reprezentuje przydzielenie pamięci za pośrednictwem tx_byte_allocate. Jeśli to się powiedzie, adres przydzielenia pamięci jest zwracany w drugim polu informacji.

**Pola informacji**
- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: wskaźnik do zwróconej pamięci (Jeśli powodzenie).
- Pole informacji 3: Liczba żądanych bajtów. Pole informacji 4: opcja oczekiwania dostarczona do wywołania tx_byte_allocate.

### <a name="byte-pool-create"></a>Tworzenie puli bajtów

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**Ikona** ![ Ikona tworzenia puli bajtów](./media/user-guide/tx-events/image16.png)

**Opis**

To zdarzenie reprezentuje Tworzenie puli bajtów za pośrednictwem tx_byte_pool_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: wskaźnik do początku obszaru pamięci. Pole informacji 3: liczba bajtów w puli bajtów.
- Pole informacji 4: Wskaźnik stosu w momencie wywołania.

### <a name="byte-pool-delete"></a>Usuwanie puli bajtów 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**Ikona** ![ Ikona usuwania puli bajtów](./media/user-guide/tx-events/image17.png)

**Opis**

To zdarzenie reprezentuje Usuwanie puli bajtów za pośrednictwem tx_byte_pool_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: Wskaźnik stosu w momencie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="byte-pool-information-get"></a>Pobieranie informacji o puli bajtów

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikona** ![ Ikona pobierania informacji o puli bajtów](./media/user-guide/tx-events/image18.png)

**Opis**

To zdarzenie reprezentuje informacje o puli bajtów za pośrednictwem tx_byte_pool_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="byte-pool-performance-info-get"></a>Pobieranie informacji o wydajności puli bajtów 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikona** ![ Ikona uzyskiwania informacji o wydajności puli bajtów](./media/user-guide/tx-events/image19.png)

**Opis**

To zdarzenie reprezentuje informacje o wydajności puli bajtów za pośrednictwem tx_byte_pool_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="byte-pool-performance-system-info-get"></a>Pobieranie informacji o systemie wydajności puli bajtów 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**Ikona** ![ Ikona pobierania informacji o systemie wydajności puli bajtów](./media/user-guide/tx-events/image20.png)

**Opis**

To zdarzenie reprezentuje informacje o systemie wydajności puli bajtów za pośrednictwem tx_byte_pool_performance_system_info_get.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="byte-pool-prioritize"></a>Priorytetyzacja puli bajtów

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**Ikona** ![ Ikona priorytetyzacji puli bajtów](./media/user-guide/tx-events/image21.png)

**Opis**

To zdarzenie reprezentuje priorytet listy zawieszania puli bajtów za pośrednictwem tx_byte_pool_prioritize.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: liczba wątków zawieszonych obecnie w puli bajtów.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="byte-release"></a>Wydanie bajtów

#### <a name="tx_byte_release"></a>tx_byte_release

**Ikona** ![ Ikona zwolnienia bajtów](./media/user-guide/tx-events/image22.png)

**Opis**

To zdarzenie reprezentuje blok pamięci przydzielony z puli bajtów za pośrednictwem tx_byte_release.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: wskaźnik do wcześniej przydzieloną pamięć puli bajtów.
- Pole informacji 3: liczba wątków zawieszonych w tej puli bajtów.
- Pole informacji 4: liczba dostępnych bajtów pamięci.

### <a name="event-flags-create"></a>Tworzenie flag zdarzeń 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**Ikona** ![ Ikona tworzenia flag zdarzeń](./media/user-guide/tx-events/image23.png)

**Opis**

To zdarzenie reprezentuje Tworzenie nowej grupy flag zdarzeń za pośrednictwem tx_event_flags_create.

**Pola informacji** 
- Pole informacji 1: wskaźnik do flagi zdarzenia w bloku sterowania grupą.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="event-flags-delete"></a>Usuwanie flag zdarzeń 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**Ikona** ![ Ikona usuwania flag zdarzeń](./media/user-guide/tx-events/image24.png)

**Opis**

To zdarzenie reprezentuje usunięcie grupy flag zdarzeń za pośrednictwem tx_event_flags_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="event-flags-get"></a>Pobieranie flag zdarzeń 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**Ikona** ![ Ikona zdarzenia gt](./media/user-guide/tx-events/image25.png)

**Opis**

To zdarzenie przedstawia pobieranie flag zdarzeń z istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: zażądano flag zdarzeń.
- Pole informacji 3: flagi zdarzeń obecnie ustawione w grupie.
- Pole informacji 4: zażądano opcji dla flag zdarzeń get.

### <a name="event-flags-information-get"></a>Informacje o flagach zdarzenia

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**Ikona** ![ Ikona uzyskiwania informacji o flagach zdarzeń](./media/user-guide/tx-events/image26.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="event-flags-performance-information-get"></a>Informacje o wydajności flag zdarzeń 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**Ikona** ![ Ikona uzyskiwania informacji o wydajności flag zdarzeń](./media/user-guide/tx-events/image27.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_performance_info_get.

**Pola informacji** 
- Pole informacji 1: wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="event-flags-performance-system-info-get"></a>Flagi zdarzeń informacje o systemie wydajności pobieranie

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**Ikona** ![ Flagi zdarzeń informacje o systemie wydajności pobieranie](./media/user-guide/tx-events/image28.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_performance_system_info_get.

**Pola informacji**
- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="event-flags-set"></a>Ustawione flagi zdarzeń 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**Ikona** ![ Ikona zestawu flag zdarzeń](./media/user-guide/tx-events/image29.png)

**Opis**

To zdarzenie reprezentuje flagę zdarzenia ustawienia (lub wyczyszczenia) w istniejącej grupie flag zdarzeń za pośrednictwem tx_event_flags_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: flagi zdarzeń do ustawienia (lub wyczyść).
- Pole informacji 3: i lub opcja flagi zdarzenia.
- Pole informacji 4: liczba wątków zawieszonych w grupie flag zdarzeń.

### <a name="event-flags-set-notify"></a>Ustawione powiadomienia flag zdarzeń

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**Ikona** ![ Ikona powiadomienia ustawiona flaga zdarzenia](./media/user-guide/tx-events/image30.png)

**Opis**

To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego powiadomienia dla każdej operacji zestawu flag zdarzeń w istniejącej grupie flag zdarzeń za pośrednictwem tx_event_flags_set_notify.

**Pola informacji**

- Pole informacji 1: wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="interrupt-control"></a>Kontrola przerwania 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**Ikona** ![ Ikona kontrolki przerwania](./media/user-guide/tx-events/image31.png)

**Opis**

To zdarzenie reprezentuje zmianę stan blokady przerwania procesora za pośrednictwem tx_interrupt_control.

**Pola informacji**

- Pole informacji 1: nowe przerwanie stan.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="mutex-create"></a>Tworzenie obiektu mutex 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**Ikona** ![ Ikona tworzenia obiektu mutex](./media/user-guide/tx-events/image32.png)

**Opis**

To zdarzenie reprezentuje Tworzenie elementu mutex za pośrednictwem tx_mutex_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku sterowania muteksem.
- Pole informacji 2: priorytet — opcja dziedziczenia
- (TX_INHERIT lub TX_NO_INHERIT).
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="mutex-delete"></a>Usuwanie obiektu mutex 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**Ikona** ![ Ikona usuwania muteksu](./media/user-guide/tx-events/image33.png)

**Opis**

To zdarzenie reprezentuje usunięcie elementu mutex za pośrednictwem tx_mutex_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do elementu mutex.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="mutex-get"></a>Pobieranie obiektu mutex 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**Ikona** ![ Ikona pobierania muteksu](./media/user-guide/tx-events/image34.png)

**Opis**

To zdarzenie reprezentuje uzyskanie elementu mutex za pośrednictwem tx_mutex_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do elementu mutex.
- Pole informacji 2: opcja oczekiwania dostarczona do wywołania tx_mutex_get.
- Pole informacji 3: wskaźnik do wątku, do którego należy element mutex (wartość NULL oznacza, że mutex nie jest własnością).
- Pole informacji 4: liczba wystąpień wątku będącego właścicielem, tx_mutex_get.

### <a name="mutex-information-get"></a>Pobieranie informacji o muteksie

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**Ikona** ![ Ikona pobierania informacji o muteksie](./media/user-guide/tx-events/image35.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o muteksie za pośrednictwem tx_mutex_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do elementu mutex.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="mutex-performance-information-get"></a>Pobieranie informacji o wydajności muteksu 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**Ikona** ![ Ikona pobierania informacji o wydajności muteksu](./media/user-guide/tx-events/image36.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności obiektu mutex za pośrednictwem tx_mutex_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do elementu mutex.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="mutex-performance-system-info-get"></a>Pobieranie informacji o systemie wydajności muteksu

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**Ikona** ![ Ikona uzyskiwania informacji o systemie wydajności muteksu](./media/user-guide/tx-events/image37.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności systemu muteksów za pośrednictwem tx_mutex_performance_system_info_get.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="mutex-prioritize"></a>Priorytet obiektu mutex 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**Ikona** ![ Ikona priorytetyzacji obiektu mutex](./media/user-guide/tx-events/image38.png)

**Opis**

To zdarzenie reprezentuje określanie priorytetów listy zawieszeń obiektu mutex za pośrednictwem tx_mutex_prioritize.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiadającego mu obiektu mutex.
- Pole informacji 2: liczba wątków zawieszonych obecnie w elemencie mutex.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="mutex-put"></a>Put mutex 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**Ikona** ![ Ikona Put obiektu mutex](./media/user-guide/tx-events/image39.png)

**Opis**

To zdarzenie reprezentuje wydawanie poprzednio posiadanego obiektu mutex za pośrednictwem tx_mutex_put.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiadającego mu obiektu mutex.
- Pole informacji 2: wskaźnik wątku będącego właścicielem obiektu mutex.
- Pole informacji 3: Liczba oczekujących żądań pobrania obiektu mutex.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="queue-create"></a>Tworzenie kolejki 

#### <a name="tx_queue_create"></a>tx_queue_create

**Ikona** ![ Ikona tworzenia kolejki](./media/user-guide/tx-events/image40.png)

**Opis**

To zdarzenie reprezentuje Tworzenie kolejki komunikatów za pośrednictwem tx_queue_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku sterowania kolejką.
- Pole informacji 2: rozmiar komunikatu — w odniesieniu do 32-bitowych wyrazów.
- Pole informacji 3: Wskaźnik początku obszaru pamięci kolejki.
- Pole informacji 4: liczba bajtów w obszarze pamięci kolejki.

### <a name="queue-delete"></a>Usuwanie kolejki 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**Ikona** ![ Ikona usuwania kolejki](./media/user-guide/tx-events/image41.png)

**Opis**

To zdarzenie reprezentuje usunięcie kolejki za pośrednictwem tx_queue_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="queue-flush"></a>Opróżnianie kolejki 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**Ikona** ![ Ikona opróżniania kolejki](./media/user-guide/tx-events/image42.png)

**Opis**

To zdarzenie reprezentuje opróżnianie (czyszczenie całej zawartości kolejki) kolejki za pośrednictwem tx_queue_flush.

**Pola informacji**

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="queue-front-send"></a>Wysyłanie frontonu kolejki 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**Ikona** ![ Ikona wysyłania z kolejki](./media/user-guide/tx-events/image43.png)

**Opis**

To zdarzenie reprezentuje Wysyłanie komunikatu z przodu kolejki za pośrednictwem tx_queue_front_send.

**Pola informacji**

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: wskaźnik do początku komunikatu.
- Pole informacji 3: Poczekaj na polecenie
- tx_queue_front_send wywołanie.
- Pole informacji 4: liczba komunikatów, które zostały już w kolejce.

### <a name="queue-information-get"></a>Pobieranie informacji o kolejce 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**Ikona** ![ Ikona pobierania informacji o kolejce](./media/user-guide/tx-events/image44.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o kolejce za pośrednictwem tx_queue_info_get.

**Pola informacji** 
- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="queue-performance-info-get"></a>Pobieranie informacji o wydajności kolejki 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**Ikona** ![ Ikona pobierania informacji o wydajności kolejki](./media/user-guide/tx-events/image45.png)

**Opis**

To zdarzenie reprezentuje informacje o wydajności kolejki za pośrednictwem tx_queue_performance_info_get.

**Pola informacji** 

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="queue-performance-system-info-get"></a>Informacje o systemie wydajności kolejki pobieranie 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**Ikona** ![ Ikona pobierania informacji o systemie wydajności kolejki](./media/user-guide/tx-events/image46.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności systemu na wszystkich kolejkach w systemie.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="queue-prioritize"></a>Priorytety kolejki 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**Ikona** ![ Ikona priorytetyzacji kolejki](./media/user-guide/tx-events/image47.png)

**Opis**

To zdarzenie reprezentuje wyznaczanie priorytetów listy zawieszania kolejki za pośrednictwem tx_queue_prioritize.

**Pola informacji** 

- Pole informacji 1: wskaźnik do odpowiedniej kolejki.
- Pole informacji 2: liczba wątków zawieszonych obecnie w kolejce.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

#### <a name="queue-receive"></a>Odbieranie kolejki 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**Ikona** ![ Ikona odbierania kolejki](./media/user-guide/tx-events/image48.png)

**Opis**

To zdarzenie reprezentuje odebranie komunikatu z kolejki za pośrednictwem tx_queue_receive.

**Pola informacji** 

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: wskaźnik do elementu docelowego dla komunikatu. Pole informacji 3: Poczekaj na wywołanie.
- Pole informacji 4: liczba komunikatów, które są obecnie w kolejce.

### <a name="queue-send"></a>Wysyłanie kolejki 

#### <a name="tx_queue_send"></a>tx_queue_send

**Ikona** ![ Ikona wysyłania kolejki](./media/user-guide/tx-events/image49.png)

**Opis**

To zdarzenie reprezentuje Wysyłanie komunikatu do kolejki za pośrednictwem tx_queue_send.

**Pola informacji** 

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: wskaźnik do komunikatu.
- Pole informacji 3: Poczekaj na wywołanie.
- Pole informacji 4: liczba komunikatów, które są obecnie w kolejce.

### <a name="queue-send-notify"></a>Powiadomienie o wysłaniu kolejki 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**Ikona** ![ Ikona powiadomienia o wysłaniu kolejki](./media/user-guide/tx-events/image50.png)

**Opis**

<p>To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego za pomocą tx_queue_send_notify, który jest wywoływany za każdym razem, gdy komunikat jest wysyłany do kolejki.

**Pola informacji** 

- Pole informacji 1: wskaźnik do kolejki.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="semaphore-ceiling-put"></a>Nakładanie limitu semafora 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**Ikona** ![ Ikona umieszczenia sufitu semafora](./media/user-guide/tx-events/image51.png)

**Opis**

To zdarzenie reprezentuje umieszczenie w semaforze za pośrednictwem tx_semaphore_ceiling_put. Różni się to od tx_semaphore_put, że maksymalna wartość semafora jest sprawdzana w taki sposób, że operacja Put nie może przekroczyć maksymalnej wartości lub limitu.

**Pola informacji**

- Pole informacji 1: wskaźnik do semafora.
- Pole informacji 2: Bieżąca liczba semaforów.
- Pole informacji 3: liczba wątków zawieszonych w semaforze.
- Pole informacji 4: limit sufitu podany w wywołaniu.

#### <a name="semaphore-create"></a>Tworzenie semafora 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**Ikona** ![ Ikona tworzenia semafora](./media/user-guide/tx-events/image52.png)

**Opis**

To zdarzenie reprezentuje tworzenie semafora za pośrednictwem tx_semaphore_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku sterowania semaforem.
- Pole informacji 2: początkowa liczba semaforów.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="semaphore-delete"></a>Usuwanie semafora 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**Ikona** ![ Ikona usuwania semafora](./media/user-guide/tx-events/image53.png)

**Opis**

To zdarzenie reprezentuje usuwanie semafora za pośrednictwem tx_semaphore_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do semafora.
- NFO pole 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="semaphore-get"></a>Pobieranie semafora 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**Ikona** ![ Ikona pobierania semafora](./media/user-guide/tx-events/image54.png)

**Opis**

To zdarzenie reprezentuje uzyskanie semafora za pośrednictwem tx_semaphore_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do semafora.
- Pole informacji 2: Poczekaj na wywołanie.
- Pole informacji 3: Bieżąca liczba semaforów.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="semaphore-information-get"></a>Pobieranie informacji o semaforze 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**Ikona** ![ Ikona pobierania informacji o semaforach](./media/user-guide/tx-events/image55.png)

**Opis**

To zdarzenie reprezentuje uzyskanie informacji o semaforze za pośrednictwem tx_semaphore_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do semafora.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="semaphore-performance-info-get"></a>Pobieranie informacji o wydajności semafora 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**Ikona** ![ Ikona pobierania informacji o wydajności semafora](./media/user-guide/tx-events/image56.png)

**Opis**

To zdarzenie reprezentuje uzyskanie informacji o wydajności semafora za pośrednictwem tx_semaphore_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do semafora.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="semaphore-performance-system-info"></a>Informacje o systemie wydajności semafora 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**Ikona** ![ Ikona informacji o systemie wydajności semafora](./media/user-guide/tx-events/image57.png)

**Opis**

To zdarzenie reprezentuje uzyskanie informacji o wydajności wszystkich semaforów w systemie za pośrednictwem tx_semaphore_performance_system_info_get.

**Pola informacji** 

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="semaphore-prioritize"></a>Priorytetyzacja semaforów 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**Ikona** ![ Ikona priorytetyzacji semaforów](./media/user-guide/tx-events/image58.png)

**Opis**

To zdarzenie reprezentuje określanie priorytetów listy zawieszania semafora za pośrednictwem tx_semaphore_prioritize.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniego semafora.
- Pole informacji 2: liczba wątków zawieszonych obecnie w semaforze.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="semaphore-put"></a>Umieszczenie semafora 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**Ikona** ![ Ikona umieszczenia semafora](./media/user-guide/tx-events/image59.png)

**Opis**

To zdarzenie reprezentuje zwolnienie wystąpienia semafora za pośrednictwem tx_semaphore_put.

**Pola informacji** 

- Pole informacji 1: wskaźnik do odpowiedniego semafora. Pole informacji 2: Bieżąca liczba semaforów.
- Pole informacji 3: liczba wątków zawieszonych w semaforze.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="semaphore-put-notify"></a>Powiadomienie o przeniesieniu semafora 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**Ikona** ![ Ikona powiadomienia dotyczącego umieszczenia semafora](./media/user-guide/tx-events/image60.png)

**Opis**

To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego za pomocą tx_semaphore_put_notify, który jest wywoływany za każdym razem, gdy wystąpienie semafora jest umieszczane.

**Pola informacji** 

- Pole informacji 1: wskaźnik do semafora.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-create"></a>Tworzenie wątku 

#### <a name="tx_thread_create"></a>tx_thread_create

**Ikona** ![ Ikona tworzenia wątku](./media/user-guide/tx-events/image61.png)

**Opis**

To zdarzenie reprezentuje tworzenie wątku za pośrednictwem tx_thread_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku sterowania wątkiem.
- Pole informacji 2: priorytet wątku.
- Pole informacji 3: Wskaźnik stosu dla wątku.
- NFO pole 4: rozmiar stosu w bajtach.

### <a name="thread-delete"></a>Usuwanie wątku 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**Ikona** ![ Ikona usuwania wątku](./media/user-guide/tx-events/image62.png)

**Opis**

To zdarzenie reprezentuje usuwanie wątku za pośrednictwem tx_thread_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-entryexit-notify"></a>Powiadomienie o wejściu/wyjściu wątku 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**Ikona** ![ Ikona powiadomienia o wejściu/wyjściu wątku](./media/user-guide/tx-events/image63.png)

**Opis**

To zdarzenie reprezentuje rejestrację wywołania zwrotnego za pomocą tx_thread_entry_exit_notify, która jest wywoływana za każdym razem, gdy wątek zostanie wprowadzony lub zostanie zakończony.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie rejestracji.
- Pole informacji 3: wskaźnik do stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

#### <a name="thread-identify"></a>Identyfikator wątku 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**Ikona** ![ Ikona identyfikacji wątku](./media/user-guide/tx-events/image64.png)

**Opis**

To zdarzenie reprezentuje wskaźnik bieżącego wątku za pośrednictwem tx_thread_identify.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-information-get"></a>Pobieranie informacji o wątku 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**Ikona** ![ Ikona pobierania informacji o wątkach](./media/user-guide/tx-events/image65.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o określonym wątku za pośrednictwem tx_thread_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

#### <a name="thread-performance-information-get"></a>Pobieranie informacji o wydajności wątków 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**Ikona** ![ Ikona uzyskiwania informacji o wydajności wątków](./media/user-guide/tx-events/image66.png)

**Opis**

To zdarzenie reprezentuje informacje o wydajności określonego wątku za pośrednictwem tx_thread_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-performance-system-info-get"></a>Pobieranie informacji o systemie wydajności wątków 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**Ikona** ![ Ikona pobierania informacji o systemie wydajności wątków](./media/user-guide/tx-events/image67.png)

**Opis**

To zdarzenie reprezentuje informacje o wydajności wszystkich wątków za pośrednictwem tx_thread_performance_system_info_get.

**Pola informacji** 

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-preemption-change"></a>Zmiana zastępujący wątek 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**Ikona** ![ Ikona zmiany zastępujący wątek](./media/user-guide/tx-events/image68.png)

**Opis**

To zdarzenie reprezentuje próg zastępujący wątku za pośrednictwem tx_thread_preemption_change.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: nowy przekroczenie — próg.
- Pole informacji 3: poprzednie przekroczenie — próg.
- Pole informacji 4: stan wątku w czasie wywołania.

### <a name="thread-priority-change"></a>Zmiana priorytetu wątku 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**Ikona** ![ Ikona zmiany priorytetu wątku](./media/user-guide/tx-events/image69.png)

**Opis**

To zdarzenie reprezentuje zmianę priorytetu wątku za pośrednictwem tx_thread_priority_change.

- Pola informacji 
- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: nowy priorytet.
- Pole informacji 3: poprzedni priorytet.
- Pole informacji 4: stan wątku w czasie wywołania.

### <a name="thread-relinquish"></a>Zrzeka się wątku 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**Ikona** ![ Ikona zrzeczenia wątku](./media/user-guide/tx-events/image70.png)

**Opis**

To zdarzenie reprezentuje procesor z wątku za pośrednictwem tx_thread_relinquish.

**Pola informacji**

- Pole informacji 1: Wskaźnik stosu w czasie wywołania.
- Pole informacji 2: wskaźnik do następnego wątku do wykonania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-reset"></a>Resetowanie wątku 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**Ikona** ![ Ikona resetowania wątku](./media/user-guide/tx-events/image71.png)

**Opis**

To zdarzenie reprezentuje zresetowanie ukończonego lub zakończonego wątku za pośrednictwem tx_thread_reset.

**Pola informacji**

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

#### <a name="thread-resume"></a>Wznowienie wątku 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**Ikona** ![ Ikona wznowienia wątku](./media/user-guide/tx-events/image72.png)

**Opis**

To zdarzenie reprezentuje wznawianie zawieszonego wątku za pośrednictwem tx_thread_resume.

**Pola informacji**

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="thread-sleep"></a>Wątek uśpienia 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**Ikona** ![ Ikona uśpienia wątku](./media/user-guide/tx-events/image73.png)

**Opis**

To zdarzenie reprezentuje wstrzymanie bieżącego wątku dla określonej liczby taktów czasomierza za pośrednictwem tx_thread_sleep.

**Pola informacji**

- Pole informacji 1: liczba taktów do zawieszenia.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="thread-stack-error-notify"></a>Powiadomienie o błędzie stosu wątku 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**Ikona** ![ Ikona powiadomienia o błędzie stosu wątku](./media/user-guide/tx-events/image74.png)

**Opis**

To zdarzenie reprezentuje procedurę rejestrowania błędu stosu wątku za pośrednictwem tx_thread_stack_error_notify_event.

**Pola informacji** 

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="thread-suspend"></a>Wstrzymywanie wątku 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**Ikona** ![ Ikona wstrzymania wątku](./media/user-guide/tx-events/image75.png)

**Opis**

To zdarzenie reprezentuje zawieszenie wątku za pośrednictwem tx_thread_suspend.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wątku, który ma zostać wstrzymany.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="thread-terminate"></a>Zakończenie wątku 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**Ikona** ![ Ikona zakończenia wątku](./media/user-guide/tx-events/image76.png)

**Opis**

To zdarzenie reprezentuje zakończenie wątku za pośrednictwem tx_thread_terminate.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wątku do przerwania.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="thread-time-slice-change"></a>Time-Slice zmiany wątku 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**Ikona** ![ Ikona zmiany czasu wątku](./media/user-guide/tx-events/image77.png)

**Opis**

To zdarzenie reprezentuje zmianę wycinka czasu wątku za pośrednictwem tx_thread_time_slice_change.

**Pola informacji**

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: nowy plasterek czasu.
- Pole informacji 3: poprzedni czas wycinka.
- Pole informacji 4: nieużywane.

### <a name="thread-wait-abort"></a>Przerwanie oczekiwania wątku 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**Ikona** ![ Ikona przerwania oczekiwania wątku](./media/user-guide/tx-events/image78.png)

**Opis**

To zdarzenie reprezentuje przerwanie zawieszenia wątku za pośrednictwem tx_thread_wait_abort.

**Pola informacji**

- Pole informacji 1: wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nieużywane.

### <a name="time-get"></a>Czas Get 

#### <a name="tx_time_get"></a>tx_time_get

**Ikona** ![ Ikona uzyskiwania czasu](./media/user-guide/tx-events/image79.png)

**Opis**

To zdarzenie reprezentuje bieżącą liczbę cykli czasomierza za pośrednictwem tx_time_get.

**Pola informacji**

- Pole informacji 1: Bieżąca liczba taktów czasomierza.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="time-set"></a>Zestaw czasu 

#### <a name="tx_time_set"></a>tx_time_set

**Ikona** ![ Ikona zestawu czasu](./media/user-guide/tx-events/image80.png)

**Opis**

To zdarzenie reprezentuje ustawienie bieżącej liczby taktów czasomierza za pośrednictwem tx_time_set.

**Pola informacji**

- Pole informacji 1: Nowa liczba taktów czasomierza.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="timer-activate"></a>Aktywuj czasomierz 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**Ikona** ![ Ikona aktywacji czasomierza](./media/user-guide/tx-events/image81.png)

**Opis**

To zdarzenie reprezentuje aktywację określonego czasomierza za pośrednictwem tx_timer_activate.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="timer-change"></a>Zmiana czasomierza 

#### <a name="tx_timer_change"></a>tx_timer_change

**Ikona** ![ Ikona zmiany czasomierza](./media/user-guide/tx-events/image82.png)

**Opis**

To zdarzenie reprezentuje zmianę określonego czasomierza za pośrednictwem tx_timer_change.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: początkowe cykle wygasania.
- Pole informacji 3: ponowne planowanie taktów wygasania.
- Pole informacji 4: nieużywane.

### <a name="timer-create"></a>Tworzenie czasomierza 

#### <a name="tx_timer_create"></a>tx_timer_create

**Ikona** ![ Ikona tworzenia czasomierza](./media/user-guide/tx-events/image83.png)

**Opis**

To zdarzenie reprezentuje tworzenie czasomierza za pośrednictwem tx_timer_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku sterowania czasomierzem.
- Pole informacji 2: początkowe cykle wygasania.
- Pole informacji 3: ponowne planowanie taktów wygasania.
- Pole informacji 4: Automatyczne włączanie wartości — albo TX_AUTO_ACTIVATE (1), albo TX_NO_ACTIVATE (0).

### <a name="timer-deactivate"></a>Dezaktywacja czasomierza 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**Ikona** ![ Ikona dezaktywacji czasomierza](./media/user-guide/tx-events/image84.png)

**Opis**

To zdarzenie reprezentuje dezaktywowanie czasomierza za pośrednictwem tx_timer_deactivate.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="timer-delete"></a>Usuwanie czasomierza 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**Ikona** ![ Ikona usuwania czasomierza](./media/user-guide/tx-events/image85.png)

**Opis**

To zdarzenie reprezentuje usunięcie czasomierza za pośrednictwem tx_timer_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="timer-information-get"></a>Pobieranie informacji o czasomierzu 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**Ikona** ![ Ikona uzyskiwania informacji o czasomierzu](./media/user-guide/tx-events/image86.png)

**Opis**

To zdarzenie reprezentuje informacje o czasomierzu za pośrednictwem tx_timer_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="timer-performance-information-get"></a>Pobieranie informacji o wydajności czasomierza 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**Ikona** ![ Ikona pobierania informacji o wydajności czasomierza](./media/user-guide/tx-events/image87.png)

**Opis** 

To zdarzenie reprezentuje informacje o wydajności czasomierza za pośrednictwem tx_timer_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="timer-system-performance-info-get"></a>Czasomierz informacji o wydajności systemu 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**Ikona** ![ Ikona uzyskiwania informacji o wydajności systemu czasomierza](./media/user-guide/tx-events/image88.png)


**Opis** 

To zdarzenie reprezentuje pobieranie wszystkich informacji o wydajności czasomierza za pośrednictwem tx_timer_performance_system_info_get.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.