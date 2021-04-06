---
title: Rozdział 2 — Dokumentacja interfejsu API zestawu profilów wykonywania
description: Ten rozdział dokumentuje funkcje interfejsu API udostępniane przez EPK.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a198e48bdacbc141fb3de4670cc7ea5ba079612d
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377600"
---
#  <a name="chapter-2--execution-profile-kit-api-references"></a>Rozdział 2 — Dokumentacja interfejsu API zestawu profilów wykonywania

ThreadX EPK zapewnia funkcje dostępu do uzyskiwania informacji o profilu wykonania w następujący sposób.

| &nbsp;Nazwa funkcji | Opis |
| --- | --- |
| _tx_execution_thread_time_reset | Zresetuj łączny czas dla wątku. |
| _tx_execution_thread_total_time_reset | Zresetuj łączny czas wątku. |
| _tx_execution_isr_time_reset | Zresetuj skumulowany czas ISR. |
| _tx_execution_idle_time_reset | Zresetuj skumulowany czas bezczynności. |
| _tx_execution_thread_time_get uzyskać skumulowany czas dla wątku. |
| _tx_execution_thread_total_time_get | Pobierz łączny czas wątku. |
| _tx_execution_isr_time_get | Pobierz skumulowany czas ISR. |
| _tx_execution_idle_time_get | Uzyskaj skumulowany czas bezczynności. |

##  <a name="_tx_execution_thread_time_reset"></a>_tx_execution_thread_time_reset

Zresetuj łączny czas dla wątku.

### <a name="prototype"></a>Prototype

```C
UINT _tx_execution_thread_time_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Opis

Ta usługa ustawia skumulowany czas wykonywania wątku z powrotem na zero.

### <a name="input-parameters"></a>Parametry wejściowe

- **thread_ptr** Wskaźnik do wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
/* Reset the execution time for thread_0.  */
status =  tx_execution_thread_time_reset(&thread_0);

/* If status is TX_SUCCESS thread_0's execution time is now 0.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_total_time_reset"></a>_tx_execution_thread_total_time_reset

Zresetuj całkowity skumulowany czas wątku.

### <a name="prototype"></a>Prototype
```c
UINT _tx_execution_thread_total_time_reset(void);
```

### <a name="description"></a>Opis

Ta usługa ustawia łączny czas wykonania wątku z powrotem na zero.

### <a name="input-parameters"></a>Parametry wejściowe

Brak.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.

### <a name="allowed-from"></a>Dozwolone z

- Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
/* Reset the total execution time for all threads.  */
status =  tx_execution_thread_total_time_reset();

/* If status is TX_SUCCESS the total thread execution time is now 0.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_isr_time_reset"></a>_tx_execution_isr_time_reset

Zresetuj skumulowany czas ISR.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_isr_time_reset(void);
```

### <a name="description"></a>Opis

Ta usługa ustawia skumulowany łączny czas wykonywania ISR z powrotem na zero.

### <a name="input-parameters"></a>Parametry wejściowe

Brak.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.

**Dozwolone z**

- Wątki, czasomierze i procedury ISR

**Przykład**

```c
/* Reset the total ISR execution time.  */
status =  tx_execution_isr_time_reset();

/* If status is TX_SUCCESS the total ISR execution time is now 0.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_idle_time_reset"></a>_tx_execution_idle_time_reset

Zresetuj skumulowany czas bezczynności.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_idle_time_reset(void);
```

### <a name="description"></a>Opis

Ta usługa ustawia skumulowany łączny czas wykonywania bezczynności z powrotem na zero.

### <a name="input-parameters"></a>Parametry wejściowe

Brak.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.

### <a name="allowed-from"></a>Dozwolone z

- Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
/* Reset the total idle execution time.  */
status =  tx_execution_idle_time_reset();

/* If status is TX_SUCCESS the total idle execution time is now 0.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_time_get"></a>_tx_execution_thread_time_get

Pobierz czas skumulowany dla wątku.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_thread_time_get(
    TX_THREAD *thread_ptr,
    EXECUTION_TIME *total_time);
```

### <a name="description"></a>Opis

Ta usługa pobiera skumulowany czas wykonywania dla wątku.

### <a name="input-parameters"></a>Parametry wejściowe

- **thread_ptr** Wskaźnik do wątku.

- **TOTAL_TIME** Miejsce docelowe dla \' czasu wykonywania wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c

/* Get the total thread execution time for thread_0.  */
status =  tx_execution_thread_time_get(&thread_0, &execution_time);

/* If status is TX_SUCCESS, execution_time contains the thread's
   execution time.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_total_time_get"></a>_tx_execution_thread_total_time_get

Pobierz łączny czas skumulowany wątku.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_thread_total_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Opis

Ta usługa pobiera łączny czas wykonywania wątku.

### <a name="input-parameters"></a>Parametry wejściowe

- **TOTAL_TIME** Miejsce docelowe dla łącznego czasu wykonywania wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.

### <a name="allowed-from"></a>Dozwolone z

- Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
EXECUTION_TIME *execution_time;

/* Get the total thread execution time.  */
status =  tx_execution_thread_total_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the thread
   execution time.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_isr_time_get"></a>_tx_execution_isr_time_get

Pobierz skumulowany czas ISR.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_isr_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Opis

Ta usługa pobiera skumulowany czas wykonywania procedury ISR.

### <a name="input-parameters"></a>Parametry wejściowe

- **TOTAL_TIME** Miejsce docelowe dla łącznego czasu wykonywania procedury ISR.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
EXECUTION_TIME  *execution_time;

/* Get the total ISR execution time.  */
status =  tx_execution_isr_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the ISR
   execution time.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_idle_time_get"></a>_tx_execution_idle_time_get

### <a name="get-the-accumulated-idle-time"></a>Uzyskaj skumulowany czas bezczynności

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_idle_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Opis

Ta usługa pobiera skumulowany czas wykonywania bezczynności.

### <a name="input-parameters"></a>Parametry wejściowe

- **TOTAL_TIME** Miejsce docelowe dla łącznego czasu wykonywania bezczynności.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.

### <a name="allowed-from"></a>Dozwolone z

- Wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
EXECUTION_TIME  *execution_time;

/* Get the total idle execution time.  */
status =  tx_execution_idle_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the idle
   execution time.  */
```

### <a name="see-also"></a>Zobacz też

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
