---
title: Rozdział 3 — interfejsy API ThreadX dla ARMv8-M
description: W tym rozdziale znajduje się opis ARMv8-M-określonych usług ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377599"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>Rozdział 3 ThreadX interfejsy API dla ARMv8-M

Ten rozdział zawiera opis usług ThreadX specyficznych dla ARMv8-M w porządku alfabetycznym. Ich nazwy są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. W sekcji "wartości zwracane" w następujących opisach wartości **pogrubienia** nie mają wpływać na **TX_DISABLE_ERROR_CHECKING** Definiowanie używane do wyłączania sprawdzania błędów interfejsu API; podczas gdy wartości wyświetlane w trybie niepogrubionym są całkowicie wyłączone.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Przydziel stos wątków w bezpiecznej pamięci.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Bezpłatny stos wątków w bezpiecznej pamięci

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Przydziel stos wątków w bezpiecznej pamięci.

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Opis

Ta usługa przydziela stos rozmiaru stack_size bajtów w bezpiecznej pamięci. Ta funkcja powinna być wywoływana dla każdego wątku, który wywołuje bezpieczne funkcje.

### <a name="input-parameters"></a>Parametry wejściowe

- **thread_ptr** Wskaźnik do wcześniej utworzonego wątku.

- **stack_size** Rozmiar bezpiecznego stosu.

### <a name="return-values"></a>Wartości zwrócone

- Żądanie powiodło się **TX_SUCCESS** (0x00).

- Rozmiar stosu **TX_SIZE_ERROR** (0x05) poza zakresem.

- **TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku.

- **TX_NO_MEMORY** (0X10) nie może przydzielić pamięci.

- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.

- **TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany do uruchomienia w trybie zabezpieczonym.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Zwolnij stos wątków w bezpiecznej pamięci. 

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwolni bezpieczny stos wątku w bezpiecznej pamięci. Ta funkcja powinna być wywoływana, jeśli wątek ma bezpieczny stos i gdy wątek już nie musi wywoływać bezpiecznych funkcji lub wątek został usunięty.

### <a name="input-parameters"></a>Parametry wejściowe

- **thread_ptr** Wskaźnik do wcześniej utworzonego wątku.

### <a name="return-values"></a>Wartości zwrócone

- Żądanie powiodło się **TX_SUCCESS** (0x00).

- **TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku.

- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.

- **TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany do uruchomienia w trybie zabezpieczonym.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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
