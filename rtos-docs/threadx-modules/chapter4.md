---
title: Rozdział 4 — Interfejsy API modułu
author: philmea
ms.author: philmea
description: Ten artykuł zawiera podsumowanie dodatkowych interfejsów API dostępnych dla modułu.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1c7590d0ccddc606a6cacdfeb3b3a99631e125554b524c4ce65c8154e65a20ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799136"
---
# <a name="chapter-4---module-apis"></a>Rozdział 4 — Interfejsy API modułu

## <a name="summary-of-module-apis"></a>Podsumowanie interfejsów API modułu

Istnieje kilka dodatkowych funkcji interfejsu API dostępnych dla modułu w następujący sposób:

- ***txm_module_application_request** _ — _Application specyficzne dla kodu źródłowego*
- ***txm_module_object_allocate** _ — _Allocate pamięci poza modułem dla obiektu *
- ***txm_module_object_deallocate** _ — _Deallocate wcześniej przydzielonej pamięci obiektu*
- ***txm_module_object_pointer_get** _ — _Find obiektu systemowego i pobieranie wskaźnika obiektu*
- ***txm_module_object_pointer_get_extended** _ — _Find obiektu systemowego i pobieranie wskaźnika obiektu, bezpieczeństwo długości nazwy*

## <a name="return-values"></a>Wartości zwracane

Dodatkowe kody błędów są zwracane dla niektórych interfejsów API Azure RTOS API. Te dodatkowe kody błędów są zdefiniowane w następujący sposób:

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): wskazuje, że moduł nie ma poprawnych właściwości do wywołania interfejsu API. Na przykład wywoływanie interfejsów API śledzenia w trybie użytkownika.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): wskazuje, że pamięć dostarczona przez moduł jest nieprawidłowa lub znajduje się w nieprawidłowej lokalizacji. Na przykład w modułach chronionych pamięci bloki sterowania obiektami nie mogą być umieszczone w pamięci, do których moduł może uzyskać dostęp.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): wywołanie zwrotne określone w interfejsie API znajduje się poza zakresem kodu modułu i dlatego jest nieprawidłowe.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Specyficzne dla aplikacji żądanie kodu stałego.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Opis

Ta usługa wykonuje określone żądanie do części aplikacji, która jest w stanie rezydowania. Zakłada się, że struktura żądania jest przygotowywana przed wywołaniem. Rzeczywiste przetwarzanie żądania odbywa się w kodzie rezyduacyjną w funkcji ***_txm_module_manager_application_request***. Domyślnie ta funkcja pozostaje pusta i jest przeznaczona do modyfikowania przez dewelopera aplikacji istniejącej.

### <a name="input-parameters"></a>Parametry wejściowe

- **żądanie** Identyfikator żądania (zdefiniowany przez aplikację)
- **param_1** Pierwszy parametr
- **param_2** Drugi parametr
- **param_3** Trzeci parametr

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Żądanie pomyślne.
- **TX_NOT_AVAILABLE** (0x1D) Żądanie nie jest obsługiwane przez kod źródłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki modułów

### <a name="example"></a>Przykład

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Przydziel pamięć w puli obiektów (utworzonej przez aplikację rezyduacyjną) dla bloku sterowania obiektu modułu.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Opis

Ta usługa przydziela pamięć dla obiektu modułu z pamięci poza modułem, co pomaga zapobiegać uszkodzeniem bloku sterowania obiektem przez kod modułu. W systemach chronionych pamięcią wszystkie bloki sterowania obiektami muszą zostać przydzielone za pomocą tego interfejsu API, zanim będzie można je utworzyć.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_ptr** Miejsce docelowe wskaźnika obiektu na pomyślną alokację.
- **object_size** Rozmiar w bajtach obiektu do przydzielenia.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne przydzielenie obiektu.
- **TX_NO_MEMORY** (0x10) Za mało pamięci.
- **TX_NOT_AVAILABLE** (0x1D) Menedżer modułów nie utworzył puli obiektów do przydzielenia

### <a name="allowed-from"></a>Dozwolone z

Wątki modułów

### <a name="example"></a>Przykład

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>Zobacz także

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

Cofniesz alokację wcześniej przydzielonej pamięci obiektu

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Opis

***Ta usługa jest przestarzała, ponieważ nie jest już potrzebna.***

Alokacja pamięci, która została wcześniej przydzielona za pośrednictwem txm_module_object_allocate* _ jest cofana w ****_*_tx_ \_ _delete usługi***.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_ptr** Wskaźnik obiektu do cofniania alokacji.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne przydzielenie obiektu.

### <a name="allowed-from"></a>Dozwolone z

Wątki modułów

### <a name="example"></a>Przykład

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>Zobacz także

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

Znajdowanie obiektu systemowego i pobieranie wskaźnika obiektu

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera wskaźnik obiektu określonego typu o określonej nazwie. Jeśli obiekt nie zostanie znaleziony, zostanie zwrócony błąd. W przeciwnym razie, jeśli obiekt zostanie znaleziony, adres tego obiektu jest umieszczany w "object_ptr". Tego wskaźnika można następnie użyć do wywołania usługi systemowej, interakcji z kodem rezydowania i/lub innych załadowanych modułów w systemie.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_type** Żądany typ obiektu ThreadX. Prawidłowe typy są następujące:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name (nazwa)** Nazwa obiektu specyficzna dla aplikacji zgodnie z definicją podczas tworzenia obiektu.
- **object_ptr** Miejsce docelowe wskaźnika obiektu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne uzyskiwanie obiektu.
- **TX_OPTION_ERROR** (0x08) Nieprawidłowy typ obiektu.
- **TX_PTR_ERROR** (0x03) Nieprawidłowe miejsce docelowe.
- **TX_SIZE_ERROR** (0x05) Nieprawidłowy rozmiar.
- **TX_NO_INSTANCE** (0x0D) Nie znaleziono obiektu.

### <a name="allowed-from"></a>Dozwolone z

Wątki modułów

### <a name="example"></a>Przykład

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

Znajdowanie obiektu systemowego i pobieranie wskaźnika obiektu

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera wskaźnik obiektu określonego typu o określonej nazwie. Jeśli obiekt nie zostanie znaleziony, zwracany jest błąd. W przeciwnym razie, jeśli obiekt zostanie znaleziony, adres tego obiektu zostanie umieszczony w "object_ptr". Tego wskaźnika można następnie użyć do wywołania usługi systemowej, interakcji z kodem rezyduacyjnym i/lub innych załadowanych modułów w systemie.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_type** Żądany typ obiektu ThreadX. Prawidłowe typy są następujące:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name (nazwa)** Nazwa obiektu specyficzna dla aplikacji zgodnie z definicją podczas tworzenia obiektu.
- **name_length** Długość nazwy.
- **object_ptr** Miejsce docelowe wskaźnika obiektu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne uzyskiwanie obiektu.
- **TX_OPTION_ERROR** (0x08) Nieprawidłowy typ obiektu.
- **TX_PTR_ERROR** (0x03) Nieprawidłowe miejsce docelowe.
- **TX_SIZE_ERROR** (0x05) Nieprawidłowy rozmiar.
- **TX_NO_INSTANCE** (0x0D) Nie znaleziono obiektu.

### <a name="allowed-from"></a>Dozwolone z

Wątki modułów

### <a name="example"></a>Przykład

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_object_pointer_get
