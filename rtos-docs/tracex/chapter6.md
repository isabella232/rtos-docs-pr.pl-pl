---
title: Rozdział 6 — Azure RTOS zdarzeń śledzenia ThreadX
description: W tym rozdziale opisano Azure RTOS ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 9fefc43002d4e0d6df817ad56d79b3e41a3d649504be50f5a39f67c1896b2e9a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116800337"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>Rozdział 6 — Azure RTOS zdarzeń śledzenia ThreadX

W tym rozdziale opisano Azure RTOS ThreadX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

Poniżej znajduje się lista zdarzeń ThreadX wyświetlanych przez traceX:

| **Ikona**                         | **Znaczenie** |
| -------------------------------- | ------------------------------------- |
| ![Ikona wznawiania wątku wewnętrznego](./media/user-guide/tx-events/image1.png)    | Wznawianie wątku wewnętrznego  |
| ![Ikona wstrzymania wątku wewnętrznego](./media/user-guide/tx-events/image2.png)    | Wstrzymywanie wątku wewnętrznego |
| ![Ikona wprowadzania procedury przerywania usługi](./media/user-guide/tx-events/image3.png)    | Wprowadź procedurę przerywania usługi (ISR) |
| ![Ikona zakończenia procedury przerywania obsługi](./media/user-guide/tx-events/image4.png)    | Zakończenie procedury przerywania usługi (ISR)  |
| ![Ikona wewnętrznego fragmentu czasu](./media/user-guide/tx-events/image5.png)    | Wewnętrzny wycinek czasu |
| ![Ikona uruchamiania](./media/user-guide/tx-events/image6.png)    | Uruchomienie |
| ![Ikona blokuj przydzielanie puli](./media/user-guide/tx-events/image7.png)    | **Blokuj przydzielanie puli** (*tx_block_allocate*)  |
| ![Ikona blokuj tworzenie puli](./media/user-guide/tx-events/image8.png)    | **Blokuj tworzenie puli** (*tx_block_pool_create*) |
| ![Ikona Blokuj usuwanie puli](./media/user-guide/tx-events/image9.png)    | **Blokuj usuwanie puli** (*tx_block_pool_delete*) |
| ![Ikona blokuj uzyskiwanie informacji o puli](./media/user-guide/tx-events/image10.png)    | **Blokuj uzyskiwanie informacji o puli** (*tx_block_pool_info_get*) |
| ![Blokuj informacje o wydajności puli get con](./media/user-guide/tx-events/image11.png)    | **Blokuj uzyskiwanie informacji o wydajności puli** (*tx_block_pool_performance_info_get*) |
| ![Ikona blokuj informacje o wydajności systemu puli](./media/user-guide/tx-events/image12.png)    | **Blokuj informacje o wydajności systemu puli get** (*tx_block_pool_performance_system_info_get*) |
| ![Ikona blokuj priorytetyzację puli](./media/user-guide/tx-events/image13.png)    | **Blokuj priorytety puli** (*tx_block_pool_prioritize*) |
| ![Ikona Blokuj wydanie w puli](./media/user-guide/tx-events/image14.png)    | **Blokuj zwalnianie do puli** (*tx_block_release*) |
| ![Ikona przydzielania pamięci w puli bajtów](./media/user-guide/tx-events/image15.png)    | **Przydzielanie pamięci puli bajtów** (*tx_byte_allocate*) |
| ![Ikona tworzenia puli bajtów](./media/user-guide/tx-events/image16.png)    | **Tworzenie puli bajtów** *(tx_byte_pool_create*) |
| ![Ikona usuwania puli bajtów](./media/user-guide/tx-events/image17.png)    | **Usuwanie puli bajtów** *(tx_byte_pool_delete*) |
| ![Ikona pobierz informacje o puli bajtów](./media/user-guide/tx-events/image18.png)    | **Uzyskiwanie informacji o puli bajtów** *(tx_byte_pool_info_get*) |
| ![Ikona pobierz informacje o wydajności puli bajtów](./media/user-guide/tx-events/image19.png)    | **Informacje o wydajności puli bajtów get** (*tx_byte_pool_performance_info_get*) |
| ![Ikona pobierz informacje o wydajności systemu puli bajtów](./media/user-guide/tx-events/image20.png)    | **Informacje o wydajności systemu puli bajtów get** (*tx_byte_pool_performance_system_info_get*) |
| ![*Ikona priorytetów puli bajtów](./media/user-guide/tx-events/image21.png)    | **Priorytet puli bajtów** *(tx_byte_pool_prioritize*) |
| ![Ikona zwolnienia pamięci bajtów w puli](./media/user-guide/tx-events/image22.png)    | **Wydanie pamięci bajtowej do puli** (*tx_byte_release*) |
| ![Ikona tworzenia flag zdarzeń](./media/user-guide/tx-events/image23.png)    | **Tworzenie flag zdarzeń** (*tx_event_flags_create*) |
| ![Ikona usuwania flag zdarzeń](./media/user-guide/tx-events/image24.png)    | **Usuwanie flag zdarzeń** (*tx_event_flags_delete*) |
| ![Ikona pobierz flagi zdarzeń](./media/user-guide/tx-events/image25.png)    | **Flagi zdarzeń get** (*tx_event_flags_get*) |
| ![Ikona pobierz informacje o flagach zdarzeń](./media/user-guide/tx-events/image26.png)    | **Informacje o flagach zdarzeń get** (*tx_event_flags_info_get*) |
| ![Ikona pobierz informacje o wydajności flag zdarzeń](./media/user-guide/tx-events/image27.png)    | **Informacje o wydajności flag zdarzeń get** (*tx_event_flags_performance_info_get*) |
| ![Ikona pobierz informacje o wydajności systemu flag zdarzeń](./media/user-guide/tx-events/image28.png)    | **Informacje o wydajności systemu flag zdarzeń get** (*tx_event_flags_performance_system_info_get*) |
| ![Ikona zestawu flag zdarzeń](./media/user-guide/tx-events/image29.png)    | **Zestaw flag zdarzeń** (*tx_event_flags_set*) |
| ![Ikona powiadamiania o ustawianych flagach zdarzeń](./media/user-guide/tx-events/image30.png)    | **Powiadomienie o zestawie flag zdarzeń** (*tx_event_flags_set_notify*) |
| ![Ikona włączania/wyłączania przerwań](./media/user-guide/tx-events/image31.png)    | **Włączanie/wyłączanie przerwań** *(tx_interrupt_control*) |
| ![Ikona tworzenia obiektu Mutex](./media/user-guide/tx-events/image32.png)    | **Mutex create** *(tx_mutex_create*) |
| ![Ikona usuwania mutex](./media/user-guide/tx-events/image33.png)    | **Usuwanie mutex** *(tx_mutex_delete*) |
| ![Ikona mutex get](./media/user-guide/tx-events/image34.png)    | **Mutex get** (*tx_mutex_get*) |
| ![Ikona pobierz informacje o symbolu mutex](./media/user-guide/tx-events/image35.png)    | **Informacje o mutex get** (*tx_mutex_info_get*) |
| ![Ikona pobierz informacje o wydajności obiektu Mutex](./media/user-guide/tx-events/image36.png)    | **Informacje o wydajności obiektu Mutex get** (*tx_mutex_performance_info_get*) |
| ![Ikona pobierz informacje o wydajności systemu Mutex](./media/user-guide/tx-events/image37.png)    | **Informacje o wydajności systemu Mutex get** (*tx_mutex_performance_system_info_get*) |
| ![Ikona priorytetów mutex](./media/user-guide/tx-events/image38.png)    | **Priorytet mutex** *(tx_mutex_prioritize*) |
| ![Ikona umieść mutex](./media/user-guide/tx-events/image39.png)    | **Mutex put** (*tx_mutex_put*) |
| ![Ikona tworzenia kolejki](./media/user-guide/tx-events/image40.png)    | **Tworzenie kolejki** (*tx_queue_create*) |
| ![Ikona usuwania kolejki](./media/user-guide/tx-events/image41.png)    | **Usuwanie kolejki** *(tx_queue_delete*) |
| ![Ikona opróżnionych kolejek](./media/user-guide/tx-events/image42.png)    | **Opróżnienie kolejki** (*tx_queue_flush*) |
| ![Ikona wysyłania z przodu w kolejce](./media/user-guide/tx-events/image43.png)    | **Wysyłanie przed kolejką** (*tx_queue_front_send*) |
| ![Ikona pobierania informacji o kolejce](./media/user-guide/tx-events/image44.png)    | **Uzyskiwanie informacji o kolejce** *(tx_queue_info_get*) |
| ![Ikona pobierania informacji o wydajności kolejki](./media/user-guide/tx-events/image45.png)    | **Uzyskiwanie informacji o wydajności kolejki** (*tx_queue_performance_info_get*) |
| ![Ikona pobierania informacji o wydajności systemu kolejki](./media/user-guide/tx-events/image46.png)    | **Informacje o wydajności systemu kolejki get** (*tx_queue_performance_system_info_get*) |
| ![Ikona priorytetów kolejki](./media/user-guide/tx-events/image47.png)    | **Priorytetyzowanie kolejki** *(tx_queue_prioritize*) |
| ![Ikona komunikatu o odbierania w kolejce](./media/user-guide/tx-events/image48.png)    | **Komunikat o odbierania w** *kolejce (tx_queue_receive*) |
| ![Ikona komunikatu wysyłania w kolejce](./media/user-guide/tx-events/image49.png)    | **Komunikat wysyłania w kolejce** (*tx_queue_send*) |
| ![Ikona powiadomienia o wysłaniu w kolejce](./media/user-guide/tx-events/image50.png)    | **Powiadomienie o wysłaniu w** *kolejce*( tx_queue_send_notify ) |
| ![Semaphore ceiling put icon (Ikona ułomna limitu Semaphore)](./media/user-guide/tx-events/image51.png)    | **Semaphore ceiling put** (*tx_semaphore_ceiling_put*) |
| ![Ikona tworzenia semafora](./media/user-guide/tx-events/image52.png)    | **Semaphore create** (*tx_semaphore_create*) |
| ![Ikona usuwania semafora](./media/user-guide/tx-events/image53.png)    | **Usuwanie semafora** *(tx_semaphore_delete*) |
| ![Ikona get Semaphore](./media/user-guide/tx-events/image54.png)    | **Semaphore get** (*tx_semaphore_get*) |
| ![Ikona pobierz informacje o semaforze](./media/user-guide/tx-events/image55.png)    | **Informacje o semaforze get** (*tx_semaphore_info_get*) |
| ![Ikona pobierz informacje o wydajności semafora](./media/user-guide/tx-events/image56.png)    | **Informacje o wydajności semafora get** (*tx_semaphroe_performance_info_get*) |
| ![Ikona pobierz informacje o wydajności systemu Semaphore](./media/user-guide/tx-events/image57.png)    | **Informacje o wydajności systemu Semaphore get** (*tx_semaphore_performance_system_info_get*) |
| ![Ikona priorytetów semafora](./media/user-guide/tx-events/image58.png)    | **Semaphore prioritize** *(tx_semaphore_prioritize*) |
| ![Ikona put Semaphore](./media/user-guide/tx-events/image59.png)    | **Semaphore put** (*tx_semaphore_put*) |
| ![Ikona powiadomienia put semaphore](./media/user-guide/tx-events/image60.png)    | **Semaphore put notify** (*tx_semaphore_put_notify*) |
| ![Ikona tworzenia wątku](./media/user-guide/tx-events/image61.png)    | **Tworzenie wątku** *(tx_thread_create*) |
| ![Ikona usuwania wątku](./media/user-guide/tx-events/image62.png)    | **Usuwanie wątku** *(tx_thread_delete*) |
| ![Ikona powiadamiania o zamykaniu/wejściu wątku](./media/user-guide/tx-events/image63.png)    | **Powiadomienie o wyejściu/wejściu** *wątku (tx_thread_entry_exit_notify*) |
| ![Ikona identyfikacji wątku](./media/user-guide/tx-events/image64.png)    | **Identyfikacja wątku** *(tx_thread_identify*) |
| ![Ikona pobierz informacje o wątku](./media/user-guide/tx-events/image65.png)    | **Informacje o wątku get** (*tx_thread_info_get*) |
| ![Ikona pobierz informacje o wydajności wątku](./media/user-guide/tx-events/image66.png)    | **Informacje o wydajności wątku get** (*tx_thread_performance_info_get*) |
| ![Ikona pobierz informacje o systemie wydajności wątków](./media/user-guide/tx-events/image67.png)    | **Informacje o systemie wydajności wątku get** (*tx_thread_performance_system_info_get*) |
| ![Ikona zmiany wywłaszczego wątku](./media/user-guide/tx-events/image68.png)    | **Zmiana wywłasznia wątku** (*tx_thread_preemption_change*) |
| ![Ikona zmiany priorytetu wątku](./media/user-guide/tx-events/image69.png)    | **Zmiana priorytetu wątku** (*tx_thread_priority_change*) |
| ![Ikona rezygnacji wątku](./media/user-guide/tx-events/image70.png)    | **Relinquish wątku** (*tx_thread_relinquish*) |
| ![Ikona resetowania wątku](./media/user-guide/tx-events/image71.png)    | **Resetowanie wątków** (*tx_thread_reset*) |
| ![*Ikona wznawiania wątku](./media/user-guide/tx-events/image72.png)    | **Wznawianie wątku** (**tx_thread_resume*) |
| ![Ikona uśpienia wątku](./media/user-guide/tx-events/image73.png)    | **Uśpienie wątku** (*tx_thread_sleep*)* |
| ![Ikona powiadamiania o błędzie stosu wątków](./media/user-guide/tx-events/image74.png)    | **Powiadomienie o błędzie stosu wątków** (*tx_thread_stack_error_notify*) |
| ![Ikona wstrzymania wątku](./media/user-guide/tx-events/image75.png)    | **Wstrzymywanie** wątku *(tx_thread_suspend*) |
| ![Ikona zakończenia wątku](./media/user-guide/tx-events/image76.png)    | **Zakończenie wątku** *(tx_thread_terminate*) |
| ![Ikona zmiany w wycinku czasu wątku](./media/user-guide/tx-events/image77.png)    | **Zmiana wycinka czasu wątku** (*tx_thread_time_slice_change*) |
| ![Ikona przerwania oczekiwania wątku](./media/user-guide/tx-events/image78.png)    | **Przerwanie oczekiwania wątku** (*tx_thread_wait_abort*) |
| ![Ikona pobierz czas](./media/user-guide/tx-events/image79.png)    | **Czas get** *(tx_time_get*) |
| ![Ikona zestawu czasu](./media/user-guide/tx-events/image80.png)    | **Zestaw czasu** *(tx_time_set*) |
| ![*Ikona aktywowania czasomierza](./media/user-guide/tx-events/image81.png)    | **Aktywacja czasomierza** *(tx_timer_activate*) |
| ![Ikona zmiany czasomierza](./media/user-guide/tx-events/image82.png)    | **Zmiana czasomierza** *(tx_timer_change*) |
| ![Ikona tworzenia czasomierza](./media/user-guide/tx-events/image83.png)    | **Tworzenie czasomierza** *(tx_timer_create*) |
| ![Ikona dezaktywacji czasomierza](./media/user-guide/tx-events/image84.png)    | **Dezaktywacja** *czasomierza (tx_timer_deactivate*) |
| ![Ikona usuwania czasomierza](./media/user-guide/tx-events/image85.png)    | **Usuwanie czasomierza** *(tx_timer_delete*) |
| ![Ikona pobierz informacje o czasomierzu](./media/user-guide/tx-events/image86.png)    | **Informacje o czasomierzu get** (*tx_timer_info_get*) |
| ![Ikona pobierz informacje o wydajności czasomierza](./media/user-guide/tx-events/image87.png)    | **Informacje o wydajności czasomierza get** (*tx_timer_performance_info_get*) |
| ![*Informacje o systemie wydajności czasomierza ikona pobierz](./media/user-guide/tx-events/image88.png)    | **Informacje o systemie wydajności czasomierza get** (*tx_timer_performance_system_info_get*) |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | **Zdarzenie zdefiniowane przez użytkownika** (patrz rozdział 10)    |

## <a name="event-descriptions"></a>Opisy zdarzeń

### <a name="internal-thread-resume"></a>Wznawianie wątku wewnętrznego

#### <a name="internal-thread-resume"></a>Wznawianie wątku wewnętrznego

**Ikona** ![ Ikona wznawiania wątku wewnętrznego](./media/user-guide/tx-events/image1.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wznawia wątek do wykonania. Jeśli określony wątek ma najwyższy priorytet, a próg wywłaszczenia nie blokuje jego wykonywania, system rozpocznie wykonywanie tego nowo gotowego wątku.

**Pola informacji**

- Pole informacji 1: wskaźnik do wznawiania wątku.
- Pole informacji 2: Poprzedni stan wznawiania wątku w następujący sposób:

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

- Pole informacyjne 3: stosuj wartość wskaźnika podczas wywołania. 
- Pole informacji 4: Wskaźnik do następnego wątku o najwyższym priorytecie do wykonania.

### <a name="internal-thread-suspend"></a>Wstrzymywanie wątku wewnętrznego

#### <a name="internal-thread-suspend"></a>Wstrzymywanie wątku wewnętrznego

**Ikona** ![ Ikona wstrzymania wątku wewnętrznego](./media/user-guide/tx-events/image2.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wstrzymuje wykonywanie wątku. Następny wątek o najwyższym priorytecie gotowy do wykonania znajduje się w czwartym polu informacji. Jeśli ta wartość ma wartość NULL, nie ma innego wątku gotowego do wykonania i system jest bezczynny.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do wstrzymanego wątku.
- Pole informacyjne 2: nowy stan zawieszania wątku w następujący sposób:

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

- Pole informacyjne 3: stosuj wartość wskaźnika podczas wywołania. Pole informacji 4: Wskaźnik do następnego wątku o najwyższym priorytecie do wykonania. Jeśli ma wartość NULL, system jest bezczynny.

### <a name="interrupt-service-routine-isr-enter"></a>Wprowadź procedurę przerywania usługi (ISR) 

#### <a name="enter-isr"></a>Wprowadź isr 

**Ikona** ![ Enter I S R icon (Wprowadź ikonę I S R)](./media/user-guide/tx-events/image3.png)

**Opis**

To zdarzenie reprezentuje wprowadzenie procedury usługi przerwań (ISR) w aplikacji. Rutynowe wykonywanie usługi przerwania jest kontynuowane do momentu wystąpienia zdarzenia zakończenia isr.

**Pola informacji**

- Pole informacyjne 1: wartość wskaźnika stosu podczas wywołania.
- Pole informacyjne 2: zdefiniowany przez aplikację numer ISR (opcjonalnie).
- Pole informacyjne 3: Liczba zagnieżdżonych przerwań.
- Pole informacji 4: flaga wyłączania wewnętrznego wywłaszczego.

### <a name="interrupt-service-routine-isr-exit"></a>Zakończenie procedury przerywania usługi (ISR) 

#### <a name="exit-isr"></a>Wyjdź z isr

**Ikona** ![ Ikona końnia pracy z kodem R](./media/user-guide/tx-events/image4.png)

**Opis**

To zdarzenie reprezentuje zakończenie procedury usługi przerwań (ISR) w aplikacji.

**Pola informacji**

- Pole informacyjne 1: wartość wskaźnika stosu podczas wywołania.
- Pole informacyjne 2: zdefiniowany przez aplikację numer ISR (opcjonalnie).
- Pole informacyjne 3: Liczba zagnieżdżonych przerwań.
- Pole informacji 4: flaga wyłączania wewnętrznego wywłaszczego.

### <a name="internal-time-slice"></a>Wewnętrzny fragment czasu

#### <a name="internal-time-slice"></a>Wewnętrzny fragment czasu

**Ikona** ![ Wewnętrzna ikona wycinka czasu](./media/user-guide/tx-events/image5.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wykonuje operację wycinka czasu. Następny wątek o tym samym priorytecie jest umieszczany w pierwszym polu informacji. Jeśli ta wartość jest taka sama jak bieżący wątek, nie wykonano żadnego wycinka czasu.

- Pole informacji 1: wskaźnik do następnego wątku do wykonania.
- Pole informacyjne 2: Liczba zagnieżdżonych przerwań.
- Pole informacji 3: flaga wyłączania wewnętrznego wywłaszczego.
- Info Field 4: Stack pointer value during the call (Pole informacyjne 4: stosuj wartość wskaźnika podczas wywołania).

### <a name="running"></a>Uruchomienie

#### <a name="running-in-context"></a>Uruchamianie w kontekście

**Ikona** ![ Ikona uruchamiania](./media/user-guide/tx-events/image6.png)

**Opis**

To zdarzenie reprezentuje uruchamianie w kontekście wątku lub bezczynny system. Służy do zilustrować kolejne zmiany w kontekście w wyniku przerwania.

**Pola informacji**
- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="block-allocate"></a>Blokuj przydzielanie 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**Ikona** ![ Ikona Blokuj przydzielanie](./media/user-guide/tx-events/image7.png)

**Opis**

To zdarzenie reprezentuje przydzielenie bloku pamięci za pośrednictwem tx_block_allocate. Jeśli to się powiedzie, adres przydzielonego bloku jest zwracany w drugim polu informacji.

**Pola informacji**
- Pole informacyjne 1: wskaźnik do odpowiedniej puli bloków.
- Pole informacyjne 2: Wskaźnik do zwróconego bloku pamięci (jeśli to się powiodło).
- Pole informacji 3: opcja oczekiwania dostarczona do tx_block_allocate wywołania.
- Pole informacyjne 4: Pozostałe dostępne bloki w puli po tej alokacji.

### <a name="block-pool-create"></a>Blokuj tworzenie puli

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**Ikona** ![ Ikona Blokuj tworzenie puli](./media/user-guide/tx-events/image8.png)

**Opis**

To zdarzenie reprezentuje tworzenie puli bloków pamięci za pośrednictwem tx_block_pool_create.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do odpowiedniego bloku sterowania puli bloków.
- Pole informacyjne 2: Wskaźnik do początkowego obszaru pamięci puli.
- Pole informacyjne 3: liczba bloków w puli. Pole informacyjne 4: rozmiar każdego bloku w puli w bajtach.

### <a name="block-pool-delete"></a>Blokuj usuwanie puli

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**Ikona** ![ Ikona Blokuj usuwanie puli](./media/user-guide/tx-events/image9.png)

**Opis**

To zdarzenie reprezentuje usunięcie puli bloków pamięci za pośrednictwem tx_block_pool_delete.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do bloku sterowania puli bloków.
- Pole informacyjne 2: wartość wskaźnika stosu podczas wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="block-pool-information-get"></a>Blokuj uzyskiwanie informacji o puli 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**Ikona** ![ Ikona blokuj uzyskiwanie informacji o puli](./media/user-guide/tx-events/image10.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o puli bloków pamięci za pośrednictwem tx_block_pool_info_get.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do bloku sterowania puli bloków.
- Pole informacyjne 2: wartość wskaźnika stosu podczas wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="block-pool-performance-information-get"></a>Uzyskiwanie informacji o wydajności puli bloków

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**Ikona** ![ Ikona blokuj informacje o wydajności puli](./media/user-guide/tx-events/image11.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności puli bloków pamięci za pośrednictwem tx_block_pool_performance_info_get.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do bloku sterowania puli bloków.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="block-pool-performance-system-information-get"></a>Blokuj wydajność puli Informacje o systemie get

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**Ikona** ![ Blokuj informacje o systemie wydajności puli ikona pobierz](./media/user-guide/tx-events/image12.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności wszystkich pul bloków pamięci za pośrednictwem tx_block_pool_performance_system_info_get.

**Pola informacji**
- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="block-pool-prioritize"></a>Blokuj priorytety puli

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**Ikona** ![ Ikona blokuj priorytetyzację puli](./media/user-guide/tx-events/image13.png)

**Opis**

To zdarzenie reprezentuje umieszczenie wątku z najwyższą ceną wstrzymaną na początku listy wstrzymania puli bloków. Jeśli zostanie to zrobione przed wywołaniem tx_block_release, wątek o najwyższym priorytecie zawieszony otrzyma zwalniany blok.

**Pola informacji**
- Pole informacyjne 1: Wskaźnik puli bloków pamięci.
- Pole informacyjne 2: liczba wątków zawieszonych w tej puli bloków.
- Pole informacyjne 3: wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="block-release"></a>Blokuj wydanie 

#### <a name="tx_block_release"></a>tx_block_release

**Ikona** ![ Ikona blokuj wydanie](./media/user-guide/tx-events/image14.png)

**Opis**

To zdarzenie reprezentuje zwolnienie wcześniej przydzielonego bloku z powrotem do puli bloków.

**Pola informacji**

- Pole informacyjne 1: Wskaźnik puli bloków pamięci.
- Info Field 2: Pointer to block to release (Pole informacyjne 2: wskaźnik do bloku do wydania).
- Pole informacyjne 3: liczba wątków zawieszonych w tej puli bloków.
- Pole informacyjne 4: wskaźnik stosu w czasie wywołania.

### <a name="byte-allocate"></a>Przydzielanie bajtów 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**Ikona** ![ Ikona przydzielania bajtów](./media/user-guide/tx-events/image15.png)

**Opis**

To zdarzenie reprezentuje przydzielanie pamięci za pośrednictwem tx_byte_allocate. Jeśli to się powiedzie, adres przydzielonej pamięci jest zwracany w drugim polu informacji.

**Pola informacji**
- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: wskaźnik do zwróconej pamięci (jeśli się powiodła).
- Pole informacji 3: liczba żądanych bajtów. Pole informacji 4: opcja oczekiwania dostarczona do tx_byte_allocate wywołania.

### <a name="byte-pool-create"></a>Tworzenie puli bajtów

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**Ikona** ![ Ikona tworzenia puli bajtów](./media/user-guide/tx-events/image16.png)

**Opis**

To zdarzenie reprezentuje tworzenie puli bajtów za pośrednictwem tx_byte_pool_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacyjne 2: Wskaźnik do początku obszaru pamięci. Pole informacyjne 3: liczba bajtów w puli bajtów.
- Pole informacyjne 4: wskaźnik stosu w czasie wywołania.

### <a name="byte-pool-delete"></a>Usuwanie puli bajtów 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**Ikona** ![ Ikona usuwania puli bajtów](./media/user-guide/tx-events/image17.png)

**Opis**

To zdarzenie reprezentuje usunięcie puli bajtów za pośrednictwem tx_byte_pool_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacyjne 2: wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="byte-pool-information-get"></a>Uzyskiwanie informacji o puli bajtów

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikona** ![ Ikona pobierz informacje o puli bajtów](./media/user-guide/tx-events/image18.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o puli bajtów za pośrednictwem tx_byte_pool_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="byte-pool-performance-info-get"></a>Uzyskiwanie informacji o wydajności puli bajtów 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności puli bajtów](./media/user-guide/tx-events/image19.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności puli bajtów za pośrednictwem tx_byte_pool_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="byte-pool-performance-system-info-get"></a>Uzyskiwanie informacji o systemie wydajności puli bajtów 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**Ikona** ![ Ikona pobierz informacje o systemie wydajności puli bajtów](./media/user-guide/tx-events/image20.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o systemie wydajności puli bajtów za pośrednictwem tx_byte_pool_performance_system_info_get.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="byte-pool-prioritize"></a>Priorytet puli bajtów

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**Ikona** ![ Ikona priorytetów puli bajtów](./media/user-guide/tx-events/image21.png)

**Opis**

To zdarzenie reprezentuje priorytetyzowanie listy wstrzymania puli bajtów za pośrednictwem tx_byte_pool_prioritize.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacyjne 2: liczba wątków obecnie zawieszonych w puli bajtów.
- Pole informacyjne 3: wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="byte-release"></a>Wersja bajtowa

#### <a name="tx_byte_release"></a>tx_byte_release

**Ikona** ![ Ikona wydania bajtu](./media/user-guide/tx-events/image22.png)

**Opis**

To zdarzenie reprezentuje zwolnienie bloku pamięci przydzielonego z puli bajtów za pośrednictwem tx_byte_release.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.
- Pole informacyjne 2: Wskaźnik do wcześniej przydzielonej pamięci puli bajtów.
- Pole informacyjne 3: liczba wątków zawieszonych w tej puli bajtów.
- Pole informacyjne 4: liczba dostępnych bajtów pamięci.

### <a name="event-flags-create"></a>Tworzenie flag zdarzeń 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**Ikona** ![ Ikona tworzenia flag zdarzeń](./media/user-guide/tx-events/image23.png)

**Opis**

To zdarzenie reprezentuje tworzenie nowej grupy flag zdarzeń za pośrednictwem tx_event_flags_create.

**Pola informacji** 
- Pole informacji 1: wskaźnik do bloku sterowania grupy flag zdarzeń.
- Pole informacyjne 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="event-flags-delete"></a>Usuwanie flag zdarzeń 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**Ikona** ![ Ikona usuwania flag zdarzeń](./media/user-guide/tx-events/image24.png)

**Opis**

To zdarzenie reprezentuje usunięcie grupy flag zdarzeń za pośrednictwem tx_event_flags_delete.

**Pola informacji** 

- Info Field 1: Pointer to event flags group (Pole informacji 1: wskaźnik do grupy flag zdarzeń).
- Pole informacyjne 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="event-flags-get"></a>Pobierz flagi zdarzeń 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**Ikona** ![ Flagi zdarzeń ikona gt](./media/user-guide/tx-events/image25.png)

**Opis**

To zdarzenie reprezentuje pobieranie flag zdarzeń z istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_get.

**Pola informacji**

- Info Field 1: Pointer to event flags group (Pole informacji 1: wskaźnik do grupy flag zdarzeń).
- Pole informacji 2: żądane flagi zdarzeń.
- Pole informacji 3: flagi zdarzeń są obecnie ustawione w grupie.
- Pole informacji 4: żądana opcja dla flag zdarzeń pobierz.

### <a name="event-flags-information-get"></a>Pobierz informacje o flagach zdarzeń

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**Ikona** ![ Ikona pobierz informacje o flagach zdarzeń](./media/user-guide/tx-events/image26.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_info_get.

**Pola informacji**

- Pole informacji 1: Wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="event-flags-performance-information-get"></a>Uzyskiwanie informacji o wydajności flag zdarzeń 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności flag zdarzeń](./media/user-guide/tx-events/image27.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_performance_info_get.

**Pola informacji** 
- Pole informacji 1: Wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="event-flags-performance-system-info-get"></a>Informacje o systemie wydajności flag zdarzeń Get

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**Ikona** ![ Ikona pobierz informacje o systemie wydajności flag zdarzeń](./media/user-guide/tx-events/image28.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_performance_system_info_get.

**Pola informacji**
- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="event-flags-set"></a>Zestaw flag zdarzeń 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**Ikona** ![ Ikona zestawu flag zdarzeń](./media/user-guide/tx-events/image29.png)

**Opis**

To zdarzenie reprezentuje ustawienie (lub wyczyszczenie) flag zdarzeń w istniejącej grupie flag zdarzeń za pośrednictwem tx_event_flags_set.

**Pola informacji**

- Pole informacji 1: Wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: flagi zdarzeń do ustawienia (lub wyczyszczenia).
- Pole informacji 3: opcja flagi zdarzenia AND lub OR.
- Info Field 4: Number of threads suspended on event flag group (Pole informacji 4: liczba wątków zawieszonych w grupie flag zdarzeń).

### <a name="event-flags-set-notify"></a>Powiadomienie o ustawianych flagach zdarzeń

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**Ikona** ![ Ikona powiadamiania o ustawianych flagach zdarzeń](./media/user-guide/tx-events/image30.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie wywołania zwrotnego powiadomienia dla dowolnej operacji zestawu flag zdarzeń dla istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_set_notify.

**Pola informacji**

- Pole informacji 1: Wskaźnik do grupy flag zdarzeń.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="interrupt-control"></a>Sterowanie przerwaniami 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**Ikona** ![ Ikona sterowania przerwań](./media/user-guide/tx-events/image31.png)

**Opis**

To zdarzenie reprezentuje zmianę blokowania przerwań procesora za pośrednictwem tx_interrupt_control.

**Pola informacji**

- Pole informacji 1: Nowa postawa przerwań.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="mutex-create"></a>Mutex Create 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**Ikona** ![ Ikona tworzenia obiektu Mutex](./media/user-guide/tx-events/image32.png)

**Opis**

To zdarzenie reprezentuje tworzenie mutex za pośrednictwem tx_mutex_create.

**Pola informacji**

- Info Field 1: Pointer to mutex control block (Pole informacji 1: wskaźnik do bloku sterowania mutex).
- Pole informacji 2: opcja dziedziczenia priorytetów
- (TX_INHERIT lub TX_NO_INHERIT).
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="mutex-delete"></a>Usuwanie mutex 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**Ikona** ![ Ikona usuwania mutex](./media/user-guide/tx-events/image33.png)

**Opis**

To zdarzenie reprezentuje usuwanie mutex za pośrednictwem tx_mutex_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do mutex.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="mutex-get"></a>Mutex Get 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**Ikona** ![ Ikona mutex get](./media/user-guide/tx-events/image34.png)

**Opis**

To zdarzenie reprezentuje uzyskanie mutex za pośrednictwem tx_mutex_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do mutex.
- Pole informacji 2: opcja oczekiwania dostarczona do tx_mutex_get wywołania.
- Pole informacji 3: Wskaźnik do wątku, który jest właścicielem mutex (NULL oznacza, że mutex nie jest własnością).
- Pole informacji 4: liczba wywołań wątku,który jest właścicielem, tx_mutex_get.

### <a name="mutex-information-get"></a>Uzyskiwanie informacji o mutex

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**Ikona** ![ Ikona pobierz informacje o symbolu mutex](./media/user-guide/tx-events/image35.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o mutex za pośrednictwem tx_mutex_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do mutex.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="mutex-performance-information-get"></a>Uzyskiwanie informacji o wydajności obiektu Mutex 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności obiektu Mutex](./media/user-guide/tx-events/image36.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności mutex za pośrednictwem tx_mutex_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do mutex.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="mutex-performance-system-info-get"></a>Mutex Performance System Info Get

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**Ikona** ![ Ikona pobierz informacje o systemie wydajności obiektu Mutex](./media/user-guide/tx-events/image37.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności systemu mutex za pośrednictwem tx_mutex_performance_system_info_get.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="mutex-prioritize"></a>Priorytet mutex 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**Ikona** ![ Ikona priorytetów mutex](./media/user-guide/tx-events/image38.png)

**Opis**

To zdarzenie reprezentuje priorytetyzowanie listy zawieszenia mutex za pośrednictwem tx_mutex_prioritize.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiadającego mutex.
- Pole informacji 2: liczba wątków aktualnie zawieszonych na mutexie.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="mutex-put"></a>Mutex Put 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**Ikona** ![ Ikona umieść mutex](./media/user-guide/tx-events/image39.png)

**Opis**

To zdarzenie reprezentuje wydanie wcześniej należącego mutex za pośrednictwem tx_mutex_put.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiadającego mutex.
- Pole informacji 2: Wskaźnik wątku, który jest właścicielem mutex.
- Pole informacji 3: liczba zaległych żądań get mutex.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="queue-create"></a>Tworzenie kolejki 

#### <a name="tx_queue_create"></a>tx_queue_create

**Ikona** ![ Ikona tworzenia kolejki](./media/user-guide/tx-events/image40.png)

**Opis**

To zdarzenie reprezentuje tworzenie kolejki komunikatów za pośrednictwem tx_queue_create.

**Pola informacji**

- Info Field 1: Pointer to queue control block (Pole informacji 1: wskaźnik do bloku sterowania kolejką).
- Pole informacji 2: rozmiar komunikatu — w kontekście słów 32-bitowych.
- Pole informacji 3: Wskaźnik do rozpoczęcia obszaru pamięci kolejki.
- Pole informacji 4: liczba bajtów w obszarze pamięci kolejki.

### <a name="queue-delete"></a>Usuwanie kolejki 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**Ikona** ![ Ikona usuwania kolejki](./media/user-guide/tx-events/image41.png)

**Opis**

To zdarzenie reprezentuje usunięcie kolejki za pośrednictwem tx_queue_delete.

**Pola informacji**

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="queue-flush"></a>Opróżnienie kolejki 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**Ikona** ![ Ikona opróżnionych kolejek](./media/user-guide/tx-events/image42.png)

**Opis**

To zdarzenie reprezentuje opróżnienie (wyczyszczenie całej zawartości kolejki) kolejki za pośrednictwem tx_queue_flush.

**Pola informacji**

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="queue-front-send"></a>Wysyłanie z przodu do kolejki 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**Ikona** ![ Ikona wysyłania z przodu w kolejce](./media/user-guide/tx-events/image43.png)

**Opis**

To zdarzenie reprezentuje wysyłanie komunikatu na przód kolejki za pośrednictwem tx_queue_front_send.

**Pola informacji**

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: Wskaźnik do rozpoczęcia komunikatu.
- Pole informacji 3: Opcja oczekiwania dostarczona do
- tx_queue_front_send wywołania.
- Pole informacji 4: liczba komunikatów, które są już w kolejkach.

### <a name="queue-information-get"></a>Uzyskiwanie informacji o kolejce 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**Ikona** ![ Ikona pobierania informacji o kolejce](./media/user-guide/tx-events/image44.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o kolejce za pośrednictwem tx_queue_info_get.

**Pola informacji** 
- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="queue-performance-info-get"></a>Uzyskiwanie informacji o wydajności kolejki 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**Ikona** ![ Ikona pobierania informacji o wydajności kolejki](./media/user-guide/tx-events/image45.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności kolejki za pośrednictwem tx_queue_performance_info_get.

**Pola informacji** 

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="queue-performance-system-info-get"></a>Uzyskiwanie informacji o systemie wydajności kolejki 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**Ikona** ![ Ikona pobierania informacji o systemie wydajności kolejki](./media/user-guide/tx-events/image46.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności systemu o wszystkich kolejkach w systemie.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="queue-prioritize"></a>Określanie priorytetów kolejki 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**Ikona** ![ Ikona priorytetów kolejki](./media/user-guide/tx-events/image47.png)

**Opis**

To zdarzenie reprezentuje priorytetyzowanie listy zawieszenia kolejki za pośrednictwem tx_queue_prioritize.

**Pola informacji** 

- Pole informacji 1: wskaźnik do odpowiedniej kolejki.
- Pole informacji 2: liczba wątków, które są obecnie wstrzymane w kolejce.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

#### <a name="queue-receive"></a>Odbieranie w kolejce 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**Ikona** ![ Ikona odbierania w kolejce](./media/user-guide/tx-events/image48.png)

**Opis**

To zdarzenie reprezentuje odbieranie komunikatu z kolejki za pośrednictwem tx_queue_receive.

**Pola informacji** 

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: wskaźnik do miejsca docelowego komunikatu. Pole informacji 3: Opcja oczekiwania dostarczona do wywołania.
- Pole informacji 4: liczba komunikatów aktualnie w kolejce.

### <a name="queue-send"></a>Wysyłanie w kolejce 

#### <a name="tx_queue_send"></a>tx_queue_send

**Ikona** ![ Ikona wysyłania w kolejce](./media/user-guide/tx-events/image49.png)

**Opis**

To zdarzenie reprezentuje wysyłanie komunikatu do kolejki za pośrednictwem tx_queue_send.

**Pola informacji** 

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: Wskaźnik do komunikatu.
- Pole informacji 3: Opcja oczekiwania dostarczona do wywołania.
- Pole informacji 4: liczba komunikatów aktualnie w kolejce.

### <a name="queue-send-notify"></a>Powiadomienie o wysyłaniu w kolejce 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**Ikona** ![ Ikona powiadamiania o wysyłaniu w kolejce](./media/user-guide/tx-events/image50.png)

**Opis**

<p>To zdarzenie reprezentuje rejestrowanie wywołania zwrotnego za pośrednictwem tx_queue_send_notify wywoływanego za każdym razem, gdy komunikat jest wysyłany do kolejki.

**Pola informacji** 

- Info Field 1: Pointer to queue (Pole informacji 1: wskaźnik do kolejki).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-ceiling-put"></a>Semaphore Ceiling Put 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**Ikona** ![ Ikona put limitu Semaphore](./media/user-guide/tx-events/image51.png)

**Opis**

To zdarzenie reprezentuje wprowadzenie do semafora za pośrednictwem tx_semaphore_ceiling_put. Różni się to tx_semaphore_put tym, że maksymalna wartość semafora jest sprawdzana w taki sposób, że operacja put nie może przekroczyć maksymalnej wartości lub limitu.

**Pola informacji**

- Pole informacji 1: Wskaźnik do semafora.
- Pole informacji 2: Bieżąca liczba semaforów.
- Pole informacji 3: liczba wątków zawieszonych na semaforze.
- Pole informacyjne 4: limit limitu podanego w wywołaniu.

#### <a name="semaphore-create"></a>Semaphore Create 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**Ikona** ![ Ikona tworzenia semafora](./media/user-guide/tx-events/image52.png)

**Opis**

To zdarzenie reprezentuje tworzenie semafora za pośrednictwem tx_semaphore_create.

**Pola informacji**

- Pole informacji 1: Wskaźnik do bloku sterowania semaforem.
- Pole informacji 2: początkowa liczba semaforów.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-delete"></a>Semaphore Delete 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**Ikona** ![ Ikona usuwania semafora](./media/user-guide/tx-events/image53.png)

**Opis**

To zdarzenie reprezentuje usunięcie semafora za pośrednictwem tx_semaphore_delete.

**Pola informacji**

- Pole informacji 1: Wskaźnik do semafora.
- nfo Pole 2: wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-get"></a>Semaphore Get 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**Ikona** ![ Ikona get Semaphore](./media/user-guide/tx-events/image54.png)

**Opis**

To zdarzenie reprezentuje uzyskanie semafora za pośrednictwem tx_semaphore_get.

**Pola informacji**

- Pole informacji 1: Wskaźnik do semafora.
- Pole informacji 2: opcja oczekiwania dostarczona do wywołania.
- Pole informacji 3: Bieżąca liczba semaforów.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="semaphore-information-get"></a>Uzyskiwanie informacji o semaforach 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**Ikona** ![ Ikona pobierz informacje o semaforze](./media/user-guide/tx-events/image55.png)

**Opis**

To zdarzenie reprezentuje uzyskiwanie informacji o semaforze za pośrednictwem tx_semaphore_info_get.

**Pola informacji**

- Pole informacji 1: Wskaźnik do semafora.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-performance-info-get"></a>Uzyskiwanie informacji o wydajności semafora 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności semafora](./media/user-guide/tx-events/image56.png)

**Opis**

To zdarzenie reprezentuje uzyskiwanie informacji o wydajności semafora za pośrednictwem tx_semaphore_performance_info_get.

**Pola informacji**

- Pole informacji 1: Wskaźnik do semafora.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-performance-system-info"></a>Informacje o systemie wydajności Semaphore 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**Ikona** ![ Ikona informacji o systemie wydajności Semaphore](./media/user-guide/tx-events/image57.png)

**Opis**

To zdarzenie reprezentuje uzyskiwanie informacji o wydajności wszystkich semaforów w systemie za pośrednictwem tx_semaphore_performance_system_info_get.

**Pola informacji** 

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-prioritize"></a>Semaphore Prioritize 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**Ikona** ![ Ikona priorytetów semafora](./media/user-guide/tx-events/image58.png)

**Opis**

To zdarzenie reprezentuje priorytetyzowanie listy zawieszenia semafora za pośrednictwem tx_semaphore_prioritize.

**Pola informacji**

- Pole informacji 1: wskaźnik do odpowiedniego semafora.
- Pole informacji 2: liczba wątków aktualnie zawieszonych na semaforze.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="semaphore-put"></a>Semaphore Put 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**Ikona** ![ Ikona put Semaphore](./media/user-guide/tx-events/image59.png)

**Opis**

To zdarzenie reprezentuje wydanie wystąpienia semafora za pośrednictwem tx_semaphore_put.

**Pola informacji** 

- Pole informacji 1: wskaźnik do odpowiedniego semafora. Pole informacji 2: Bieżąca liczba semaforów.
- Pole informacji 3: liczba wątków zawieszonych na semaforze.
- Pole informacji 4: Wskaźnik stosu w czasie wywołania.

### <a name="semaphore-put-notify"></a>Semaphore Put Notify 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**Ikona** ![ Ikona powiadomienia put semaphore](./media/user-guide/tx-events/image60.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie wywołania zwrotnego za pośrednictwem tx_semaphore_put_notify wywoływanego za każdym razem, gdy zostanie wprowadzone wystąpienie semafora.

**Pola informacji** 

- Pole informacji 1: Wskaźnik do semafora.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-create"></a>Tworzenie wątku 

#### <a name="tx_thread_create"></a>tx_thread_create

**Ikona** ![ Ikona tworzenia wątku](./media/user-guide/tx-events/image61.png)

**Opis**

To zdarzenie reprezentuje tworzenie wątku za pośrednictwem tx_thread_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do bloku sterowania wątkami.
- Pole informacji 2: Priorytet wątku.
- Pole informacyjne 3: Wskaźnik stosu dla wątku.
- nfo Pole 4: rozmiar stosu w bajtach.

### <a name="thread-delete"></a>Usuwanie wątku 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**Ikona** ![ Ikona usuwania wątku](./media/user-guide/tx-events/image62.png)

**Opis**

To zdarzenie reprezentuje usuwanie wątku za pośrednictwem tx_thread_delete.

**Pola informacji** 

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-entryexit-notify"></a>Powiadomienie o wejściu/wyjściu wątku 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**Ikona** ![ Ikona powiadamiania o wejściu/wyjściu wątku](./media/user-guide/tx-events/image63.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie wywołania zwrotnego za pośrednictwem tx_thread_entry_exit_notify wywoływanego za każdym razem, gdy wątek jest wprowadzany lub zamykany.

**Pola informacji** 

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie rejestracji.
- Info Field 3: Pointer to stack at time of call (Pole informacji 3: wskaźnik do stosu w czasie wywołania).
- Pole informacji 4: nie jest używane.

#### <a name="thread-identify"></a>Identyfikowanie wątku 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**Ikona** ![ Ikona identyfikacji wątku](./media/user-guide/tx-events/image64.png)

**Opis**

To zdarzenie reprezentuje pobieranie bieżącego wskaźnika wątku za pośrednictwem tx_thread_identify.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-information-get"></a>Uzyskiwanie informacji o wątku 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**Ikona** ![ Ikona pobierz informacje o wątku](./media/user-guide/tx-events/image65.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o określonym wątku za pośrednictwem tx_thread_info_get.

**Pola informacji**

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

#### <a name="thread-performance-information-get"></a>Uzyskiwanie informacji o wydajności wątku 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności wątku](./media/user-guide/tx-events/image66.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności określonego wątku za pośrednictwem tx_thread_performance_info_get.

**Pola informacji**

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-performance-system-info-get"></a>Uzyskiwanie informacji o systemie wydajności wątku 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**Ikona** ![ Ikona get informacji o systemie wydajności wątków](./media/user-guide/tx-events/image67.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o wydajności wszystkich wątków za pośrednictwem tx_thread_performance_system_info_get.

**Pola informacji** 

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-preemption-change"></a>Zmiana wywłaszczego wątku 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**Ikona** ![ Ikona zmiany wywłaszczego wątku](./media/user-guide/tx-events/image68.png)

**Opis**

To zdarzenie reprezentuje zmianę progu wywłaszczenia wątku za pośrednictwem tx_thread_preemption_change.

**Pola informacji** 

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacyjne 2: Nowy próg wywłaszczenia.
- Pole informacji 3: Poprzedni próg wywłaszczenia.
- Pole informacji 4: stan wątku w czasie wywołania.

### <a name="thread-priority-change"></a>Zmiana priorytetu wątku 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**Ikona** ![ Ikona zmiany priorytetu wątku](./media/user-guide/tx-events/image69.png)

**Opis**

To zdarzenie reprezentuje zmianę priorytetu wątku za pośrednictwem tx_thread_priority_change.

- Pola informacji 
- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: Nowy priorytet.
- Pole informacji 3: Poprzedni priorytet.
- Pole informacji 4: stan wątku w czasie wywołania.

### <a name="thread-relinquish"></a>Relinquish wątku 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**Ikona** ![ Ikona rezygnacji wątku](./media/user-guide/tx-events/image70.png)

**Opis**

To zdarzenie reprezentuje rezygnację procesora z wątku za pośrednictwem tx_thread_relinquish.

**Pola informacji**

- Pole informacji 1: wskaźnik stosu w czasie wywołania.
- Pole informacji 2: wskaźnik do następnego wątku do wykonania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-reset"></a>Resetowanie wątku 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**Ikona** ![ Ikona resetowania wątku](./media/user-guide/tx-events/image71.png)

**Opis**

To zdarzenie reprezentuje resetowanie ukończonego lub zakończonego wątku za pośrednictwem tx_thread_reset.

**Pola informacji**

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

#### <a name="thread-resume"></a>Wznawianie wątku 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**Ikona** ![ Ikona wznawiania wątku](./media/user-guide/tx-events/image72.png)

**Opis**

To zdarzenie reprezentuje wznowienie wstrzymanego wątku za pośrednictwem tx_thread_resume.

**Pola informacji**

- Pole informacji 1: Wskaźnik do wątku.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="thread-sleep"></a>Uśpienie wątku 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**Ikona** ![ Ikona uśpienia wątku](./media/user-guide/tx-events/image73.png)

**Opis**

To zdarzenie reprezentuje wstrzymanie bieżącego wątku dla określonej liczby takt czasomierzy za pośrednictwem tx_thread_sleep.

**Pola informacji**

- Pole informacji 1: liczba znaczników do wstrzymania.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="thread-stack-error-notify"></a>Powiadamianie o błędzie stosu wątków 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**Ikona** ![ Ikona powiadamiania o błędzie stosu wątków](./media/user-guide/tx-events/image74.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie procedury powiadamiania o błędach stosu wątków za pośrednictwem tx_thread_stack_error_notify_event.

**Pola informacji** 

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="thread-suspend"></a>Wstrzymywanie wątku 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**Ikona** ![ Ikona wstrzymania wątku](./media/user-guide/tx-events/image75.png)

**Opis**

To zdarzenie reprezentuje wstrzymanie wątku za pośrednictwem tx_thread_suspend.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wątku w celu wstrzymania.
- Pole informacji 2: stan wątku w czasie wywołania.
- Pole informacji 3: Wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="thread-terminate"></a>Zakończenie wątku 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**Ikona** ![ Ikona zakończenia wątku](./media/user-guide/tx-events/image76.png)

**Opis**

To zdarzenie reprezentuje zakończenie wątku za pośrednictwem tx_thread_terminate.

**Pola informacji** 

- Info Field 1: Pointer to thread to terminate (Pole informacji 1: wskaźnik do wątku do zakończenia).
- Pole informacji 2: Stan wątku w czasie wywołania.
- Pole informacyjne 3: wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="thread-time-slice-change"></a>Zmiana Time-Slice wątków 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**Ikona** ![ Ikona zmiany w wycinku czasu wątku](./media/user-guide/tx-events/image77.png)

**Opis**

To zdarzenie reprezentuje zmianę wycinka czasu wątku za pośrednictwem tx_thread_time_slice_change.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do wątku.
- Pole informacyjne 2: Nowy wycinek czasu.
- Pole informacji 3: Poprzedni wycinek czasu.
- Pole informacji 4: nie jest używane.

### <a name="thread-wait-abort"></a>Przerwanie oczekiwania wątku 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**Ikona** ![ Ikona przerwania oczekiwania wątku](./media/user-guide/tx-events/image78.png)

**Opis**

To zdarzenie reprezentuje przerwanie zawieszenia wątku za pośrednictwem tx_thread_wait_abort.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do wątku.
- Pole informacji 2: Stan wątku w czasie wywołania.
- Pole informacyjne 3: wskaźnik stosu w czasie wywołania.
- Pole informacji 4: nie jest używane.

### <a name="time-get"></a>Time Get 

#### <a name="tx_time_get"></a>tx_time_get

**Ikona** ![ Ikona pobierz czas](./media/user-guide/tx-events/image79.png)

**Opis**

To zdarzenie reprezentuje pobieranie bieżącej liczby takt czasomierza za pośrednictwem tx_time_get.

**Pola informacji**

- Pole informacyjne 1: Bieżąca liczba takt czasomierza.
- Pole informacyjne 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="time-set"></a>Zestaw czasu 

#### <a name="tx_time_set"></a>tx_time_set

**Ikona** ![ Ikona zestawu czasu](./media/user-guide/tx-events/image80.png)

**Opis**

To zdarzenie reprezentuje ustawienie bieżącej liczby znaczników czasomierza za pośrednictwem tx_time_set.

**Pola informacji**

- Pole informacyjne 1: Nowa liczba takt czasomierza.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="timer-activate"></a>Aktywacja czasomierza 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**Ikona** ![ Ikona aktywowania czasomierza](./media/user-guide/tx-events/image81.png)

**Opis**

To zdarzenie reprezentuje aktywowanie określonego czasomierza za pośrednictwem tx_timer_activate.

**Pola informacji**

- Info Field 1: Pointer to timer (Pole informacyjne 1: wskaźnik do czasomierza).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="timer-change"></a>Zmiana czasomierza 

#### <a name="tx_timer_change"></a>tx_timer_change

**Ikona** ![ Ikona zmiany czasomierza](./media/user-guide/tx-events/image82.png)

**Opis**

To zdarzenie reprezentuje zmianę określonego czasomierza za pośrednictwem tx_timer_change.

**Pola informacji**

- Info Field 1: Pointer to timer (Pole informacyjne 1: wskaźnik do czasomierza).
- Pole informacyjne 2: Początkowe takty wygasania.
- Pole informacji 3: Ponowne harmonogram wygasania znaczników.
- Pole informacji 4: nie jest używane.

### <a name="timer-create"></a>Tworzenie czasomierza 

#### <a name="tx_timer_create"></a>tx_timer_create

**Ikona** ![ Ikona tworzenia czasomierza](./media/user-guide/tx-events/image83.png)

**Opis**

To zdarzenie reprezentuje tworzenie czasomierza za pośrednictwem tx_timer_create.

**Pola informacji**

- Info Field 1: Pointer to timer control block (Pole informacyjne 1: wskaźnik do bloku sterowania czasomierzem).
- Pole informacyjne 2: Początkowe takty wygasania.
- Pole informacji 3: Ponowne harmonogram wygasania znaczników.
- Pole informacji 4: Wartość włączania automatycznego — TX_AUTO_ACTIVATE (1) lub TX_NO_ACTIVATE (0).

### <a name="timer-deactivate"></a>Dezaktywacja czasomierza 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**Ikona** ![ Ikona dezaktywacji czasomierza](./media/user-guide/tx-events/image84.png)

**Opis**

To zdarzenie reprezentuje dezaktywowanie czasomierza za pośrednictwem tx_timer_deactivate.

**Pola informacji**

- Info Field 1: Pointer to timer (Pole informacyjne 1: wskaźnik do czasomierza).
- Pole informacyjne 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="timer-delete"></a>Usuwanie czasomierza 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**Ikona** ![ Ikona usuwania czasomierza](./media/user-guide/tx-events/image85.png)

**Opis**

To zdarzenie reprezentuje usunięcie czasomierza za pośrednictwem tx_timer_delete.

**Pola informacji** 

- Info Field 1: Pointer to timer (Pole informacyjne 1: wskaźnik do czasomierza).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="timer-information-get"></a>Uzyskiwanie informacji o czasomierzu 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**Ikona** ![ Ikona czasomierza w celu uzyskania informacji](./media/user-guide/tx-events/image86.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o czasomierzu za pośrednictwem tx_timer_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="timer-performance-information-get"></a>Uzyskiwanie informacji o wydajności czasomierza 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności czasomierza](./media/user-guide/tx-events/image87.png)

**Opis** 

To zdarzenie reprezentuje pobieranie informacji o wydajności czasomierza za pośrednictwem tx_timer_performance_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do czasomierza.
- Pole informacji 2: Wskaźnik stosu w czasie wywołania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="timer-system-performance-info-get"></a>Uzyskiwanie informacji o wydajności systemu czasomierza 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**Ikona** ![ Ikona pobierz informacje o wydajności systemu czasomierza](./media/user-guide/tx-events/image88.png)


**Opis** 

To zdarzenie reprezentuje pobieranie wszystkich informacji o wydajności czasomierza za pośrednictwem tx_timer_performance_system_info_get.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.