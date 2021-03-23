---
title: Rozdział 4 — interfejsy API modułów
author: philmea
ms.author: philmea
description: Ten artykuł zawiera podsumowanie dodatkowych interfejsów API dostępnych dla modułu.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821391"
---
# <a name="chapter-4---module-apis"></a>Rozdział 4 — interfejsy API modułów

## <a name="summary-of-module-apis"></a>Podsumowanie interfejsów API modułów

Istnieje kilka dodatkowych funkcji interfejsu API dostępnych dla modułu w następujący sposób:

- ***txm_module_application_request** _-_Application żądania specyficzne dla kodu rezydentnego *
- ***txm_module_object_allocate** _-_Allocate pamięci poza modułem dla obiektu *
- ***txm_module_object_deallocate** _-_Deallocate wcześniej przydzieloną pamięć obiektu *
- ***txm_module_object_pointer_get** _-_Find obiektu systemowego i Pobierz wskaźnik obiektu *
- ***txm_module_object_pointer_get_extended** _-_Find obiektu systemowego i Pobierz wskaźnik obiektu, bezpieczeństwo długości nazwy *

## <a name="return-values"></a>Wartości zwracane

Dodatkowe kody błędów są zwracane dla niektórych interfejsów API usługi Azure RTO. Te dodatkowe kody błędów są zdefiniowane w następujący sposób:

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): wskazuje, że moduł nie ma poprawnych właściwości do wywołania interfejsu API. Na przykład wywoływanie interfejsów API śledzenia w trybie użytkownika.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): wskazuje, że pamięć dostarczona przez moduł jest nieprawidłowa lub znajduje się w nieprawidłowej lokalizacji. Na przykład w modułach chronionych pamięci bloki kontroli obiektów nie mogą znajdować się w pamięci, do której moduł może uzyskać dostęp.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): wywołanie zwrotne określone w interfejsie API znajduje się poza zakresem kodu modułu i dlatego jest nieprawidłowe.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Specyficzne dla aplikacji żądanie dotyczące kodu rezydentnego.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Opis

Ta usługa wysyła określone żądanie do rezydentnej części aplikacji. Przyjęto założenie, że struktura żądania jest przygotowywana przed wywołaniem. Rzeczywiste przetwarzanie żądania odbywa się w kodzie rezydentnym w funkcji ***_txm_module_manager_application_request***. Domyślnie ta funkcja jest pozostawiona puste i jest przeznaczona dla dewelopera aplikacji rezydentnych do zmodyfikowania.

### <a name="input-parameters"></a>Parametry wejściowe

- **żądanie** Identyfikator żądania (zdefiniowane przez aplikację)
- **Param_1** Pierwszy parametr
- **param_2** Drugi parametr
- **param_3** Trzeci parametr

### <a name="return-values"></a>Wartości zwracane

- Żądanie powiodło się **TX_SUCCESS** (0x00).
- Żądanie **TX_NOT_AVAILABLE** (0x1D) nie jest obsługiwane przez kod rezydentny.

### <a name="allowed-from"></a>Dozwolone z

Wątki modułu

### <a name="example"></a>Przykład

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Przydziel pamięć w puli obiektów (utworzona przez aplikację rezydentną) dla bloku sterowania obiektami modułu.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Opis

Ta usługa przydziela pamięć dla obiektu modułu z pamięci poza modułem, co pomaga zapobiegać uszkodzeniu bloku kontroli obiektów przez kod modułu. W systemach chronionych pamięci wszystkie bloki sterujące obiektów muszą być przydzielenia przy użyciu tego interfejsu API, zanim będzie można je utworzyć.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_ptr** Miejsce docelowe wskaźnika obiektu w przypadku pomyślnego przydzielenia.
- **object_size** Rozmiar w bajtach obiektu do przydzielenia.

### <a name="return-values"></a>Wartości zwracane

- Pomyślna alokacja obiektu **TX_SUCCESS** (0x00).
- **TX_NO_MEMORY** (0x10) za mało pamięci.
- Menedżer modułu **TX_NOT_AVAILABLE** (0x1D) nie utworzył puli obiektów do przydzielenia

### <a name="allowed-from"></a>Dozwolone z

Wątki modułu

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

Cofnij przydział wcześniej przydzieloną pamięć obiektu

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Opis

***Ta usługa jest przestarzała, ponieważ nie jest już wymagana***.

Pamięć, która została wcześniej przyznana za pośrednictwem ***txm_module_object_allocate **_, jest cofana w* \_ usłudze _delete/TX***.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_ptr** Wskaźnik obiektu do cofnięcia alokacji.

### <a name="return-values"></a>Wartości zwracane

- Pomyślna alokacja obiektu **TX_SUCCESS** (0x00).

### <a name="allowed-from"></a>Dozwolone z

Wątki modułu

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

Znajdź obiekt systemowy i Pobierz wskaźnik obiektu

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wskaźnik obiektu określonego typu z określoną nazwą. Jeśli obiekt nie zostanie znaleziony, zwracany jest błąd. W przeciwnym razie, jeśli obiekt zostanie znaleziony, adres tego obiektu zostanie umieszczony w "object_ptr". Ten wskaźnik może być następnie używany do wykonywania wywołań usługi systemowej w celu współpracy z kodem rezydentnym i/lub innymi załadowanymi modułami w systemie.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_type** Zażądano typu obiektu ThreadX. Prawidłowe typy są następujące:
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
- **Nazwa** Nazwa obiektu specyficzna dla aplikacji określona podczas tworzenia obiektu.
- **object_ptr** Miejsce docelowe dla wskaźnika obiektu.

### <a name="return-values"></a>Wartości zwracane

- Pomyślna operacja pobrania obiektu **TX_SUCCESS** (0x00).
- **TX_OPTION_ERROR** (0X08) Nieprawidłowy typ obiektu.
- **TX_PTR_ERROR** (0X03) Nieprawidłowa lokalizacja docelowa.
- **TX_SIZE_ERROR** (0X05) Nieprawidłowy rozmiar.
- Nie znaleziono obiektu **TX_NO_INSTANCE** (0x0D).

### <a name="allowed-from"></a>Dozwolone z

Wątki modułu

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

Znajdź obiekt systemowy i Pobierz wskaźnik obiektu

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wskaźnik obiektu określonego typu z określoną nazwą. Jeśli obiekt nie zostanie znaleziony, zwracany jest błąd. W przeciwnym razie, jeśli obiekt zostanie znaleziony, adres tego obiektu zostanie umieszczony w "object_ptr". Ten wskaźnik może być następnie używany do wykonywania wywołań usługi systemowej w celu współpracy z kodem rezydentnym i/lub innymi załadowanymi modułami w systemie.

### <a name="input-parameters"></a>Parametry wejściowe

- **object_type** Zażądano typu obiektu ThreadX. Prawidłowe typy są następujące:
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
- **Nazwa** Nazwa obiektu specyficzna dla aplikacji określona podczas tworzenia obiektu.
- **name_length** Długość nazwy.
- **object_ptr** Miejsce docelowe dla wskaźnika obiektu.

### <a name="return-values"></a>Wartości zwracane

- Pomyślna operacja pobrania obiektu **TX_SUCCESS** (0x00).
- **TX_OPTION_ERROR** (0X08) Nieprawidłowy typ obiektu.
- **TX_PTR_ERROR** (0X03) Nieprawidłowa lokalizacja docelowa.
- **TX_SIZE_ERROR** (0X05) Nieprawidłowy rozmiar.
- Nie znaleziono obiektu **TX_NO_INSTANCE** (0x0D).

### <a name="allowed-from"></a>Dozwolone z

Wątki modułu

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
