---
title: Rozdział 3 — interfejsy API ThreadX dla ARMv8-M
description: Ten rozdział zawiera opis usług ThreadX specyficznych dla ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99633db55a5d93eb32ce4fb5429f3fe2f9ab5137cffc30b27982f702cece1ca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791503"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>Interfejsy API ThreadX rozdziału 3 dla ARMv8-M

Ten rozdział zawiera opis usług ThreadX specyficznych dla ARMv8-M w kolejności alfabetycznej. Ich nazwy zostały zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. W sekcji "Wartości zwracane" w poniższych  opisach wartości  z poGRUBIENIEM nie mają wpływu na wartość zdefiniowaną przez TX_DISABLE_ERROR_CHECKING używaną do wyłączania sprawdzania błędów interfejsu API; Wartości wyświetlane bez pogrubienia są całkowicie wyłączone.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Przydziel stos wątków w bezpiecznej pamięci.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Stos wolnych wątków w bezpiecznej pamięci

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Przydziel stos wątków w bezpiecznej pamięci.

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Opis

Ta usługa przydziela stos rozmiaru do stack_size bajtów w bezpiecznej pamięci. Ta funkcja powinna być wywoływana dla każdego wątku, który wywołuje bezpieczne funkcje.

### <a name="input-parameters"></a>Parametry wejściowe

- **thread_ptr** Wskaźnik do wcześniej utworzonego wątku.

- **stack_size** Rozmiar bezpiecznego stosu.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0x00) Żądanie pomyślne.

- **TX_SIZE_ERROR** (0x05) Rozmiar stosu poza zakresem.

- **TX_THREAD_ERROR** (0x0E) Nieprawidłowy wskaźnik wątku.

- **TX_NO_MEMORY** (0x10) Nie można przydzielić pamięci.

- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący tę usługę.

- **TX_FEATURE_NOT_ENABLED** (0xFF) System został skompilowany w celu uruchomienia w trybie bezpiecznym.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>Zobacz też

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

Wolne stosu wątków w bezpiecznej pamięci. 

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Opis

Ta usługa pozwala uwolnić bezpieczny stos wątku w bezpiecznej pamięci. Ta funkcja powinna być wywoływana, jeśli wątek ma bezpieczny stos i gdy wątek nie musi już wywołać bezpiecznych funkcji lub wątek zostanie usunięty.

### <a name="input-parameters"></a>Parametry wejściowe

- **thread_ptr** Wskaźnik do wcześniej utworzonego wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0x00) Żądanie pomyślne.

- **TX_THREAD_ERROR** (0x0E) Nieprawidłowy wskaźnik wątku.

- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący tę usługę.

- **TX_FEATURE_NOT_ENABLED** (0xFF) System został skompilowany w celu uruchomienia w trybie bezpiecznym.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>Zobacz też

tx_thread_secure_stack_allocate
