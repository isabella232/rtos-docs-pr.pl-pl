---
title: Rozdział 4 — Opis usług NAT
description: Ten rozdział zawiera opis wszystkich usług interfejsu API NAT NetX Duo w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbe2cb25607162b62b048251927bdc7671c5884d2a3b45b6b24bae539e08d24a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797299"
---
# <a name="chapter-4---description-of-nat-services"></a>Rozdział 4 — Opis usług NAT

Ten rozdział zawiera opis wszystkich usług interfejsu API NAT NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

> [!NOTE]
> W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

## <a name="nx_nat_create"></a>nx_nat_create

Tworzenie serwera NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera NAT.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat do utworzenia
- **ip_ptr wskaźnik do** wystąpienia adresu IP
- **global_interface_index** Indeksowanie do globalnego interfejsu sieciowego
- **dynamic_cache_memory** Obszar pamięci wskaźnika do tabeli NAT
- **dynamic_cache_size** Rozmiar obszaru pamięci dla tabeli nat

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) nat został pomyślnie utworzony
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_NAT_CACHE_ERROR (0xD02) Nieprawidłowe dane wejściowe wskaźnika pamięci podręcznej

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

Usuwanie serwera NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzony serwer NAT.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat do usunięcia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) nat został pomyślnie usunięty
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

Włączanie wystąpienia adresu IP dla nat

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia wystąpienie adresu IP dla nat (np. przekazywanie odebranych pakietów do serwera NAT).

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) NAT zostało pomyślnie włączone
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

Wyłączanie wystąpienia adresu IP dla nat

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza nat w wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) NAT zostało pomyślnie wyłączone
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Ustawianie funkcji wywołania zwrotnego powiadamiania o pełnej pamięci podręcznej

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Opis

Ta usługa rejestruje pełne wywołanie zwrotne pamięci podręcznej za pomocą wskaźnika funkcji wejściowej cache_full_notify_cb który wskazuje funkcję powiadamiania pełną pamięć podręczną zdefiniowaną przez użytkownika.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat
- **cache_full_notify_cb** Wskaźnik do buforowania pełnej funkcji powiadamiania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Funkcja powiadamiania o pełnej pamięci podręcznej została pomyślnie ustawiona
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Tworzenie wpisu przychodzącego w tabeli translacji translatora translatora nat

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Opis

Ta usługa tworzy wpis dla ruchu przychodzącego jako statyczny (wpis trwały, nigdy nie wygasa) i dodaje go do tabeli translacji translatora nat. Te wpisy są zwykle tworzone dla lokalnych serwerów hostów, na których połączenie jest inicjowane z hosta w sieci zewnętrznej. Serwer NAT sprawdza, czy port zewnętrzny nie jest jeszcze używany w tabeli translacji ani powiązany przez istniejące wcześniej gniazdo NetX Duo tego samego protokołu.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat
- **entry_ptr** Wskaźnik do wpisu tłumaczenia
- **local_ip_address** Adres IP hosta lokalnego
- **external_port** Port docelowy w sieci zewnętrznej
- **local_port** Port źródłowy (hosta lokalnego)
- **protokół** Protokół pakietów (np. TCP)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Wpis został pomyślnie utworzony
- **NX_NAT_PORT_UNAVAILABLE** (0xD0D) Nieprawidłowy port zewnętrzny
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

Usuwanie wpisu ruchu przychodzącego w tabeli translacji translatora nat

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Opis

Ta usługa usuwa określony wpis ruchu przychodzącego z tabeli tłumaczenia.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia nat
- **delete_entry_ptr** Wskaźnik do wpisu tłumaczenia translatora nat

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Wpis został pomyślnie usunięty
- **NX_NAT_ENTRY_NOT_FOUND** (0xD04) Nie znaleziono wpisu
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Nieprawidłowy typ tłumaczenia

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
