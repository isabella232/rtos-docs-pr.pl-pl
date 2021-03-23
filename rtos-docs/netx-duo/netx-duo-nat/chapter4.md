---
title: Rozdział 4 — Opis usług translatora adresów sieciowych
description: Ten rozdział zawiera opis wszystkich usług interfejsu API NAT NetX Duo w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821756"
---
# <a name="chapter-4---description-of-nat-services"></a>Rozdział 4 — Opis usług translatora adresów sieciowych

Ten rozdział zawiera opis wszystkich usług interfejsu API translacji adresów sieciowych NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

> [!NOTE]
> W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

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

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych do utworzenia
- **Ip_ptr wskaźnika** do wystąpienia adresu IP
- **global_interface_index** Indeksowanie do globalnego interfejsu sieciowego
- **dynamic_cache_memory** Wskaźnik obszaru pamięci na tabelę NAT
- **dynamic_cache_size** Rozmiar obszaru pamięci dla tabeli NAT

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwer NAT został pomyślnie utworzony
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowa wejściowa niebędąca wskaźnikiem
- NX_NAT_CACHE_ERROR (0xD02) Nieprawidłowa wejściowa wskaźnik pamięci podręcznej

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

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych do usunięcia

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto translator adresów sieciowych **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

Włącz wystąpienie protokołu IP dla translatora adresów sieciowych

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza wystąpienie protokołu IP dla translatora adresów sieciowych (np. pakiety odebrane dalej do serwera NAT).

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) translator adresów sieciowych został pomyślnie włączony
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

Wyłącz wystąpienie protokołu IP dla translatora adresów sieciowych

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza translator adresów sieciowych w wystąpieniu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) translator adresów sieciowych został pomyślnie wyłączony
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Ustawianie funkcji wywołania zwrotnego pełnych powiadomień pamięci podręcznej

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Opis

Ta usługa rejestruje pełne wywołanie zwrotne pamięci podręcznej za pomocą wskaźnika funkcji wejściowej cache_full_notify_cb, który wskazuje na zdefiniowaną przez użytkownika funkcję pełnego powiadamiania pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych
- **cache_full_notify_cb** Wskaźnik do funkcji pełnego powiadamiania pamięci podręcznej

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie ustawiono pełną funkcję powiadamiania pamięci podręcznej **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Tworzenie wpisu przychodzącego w tabeli translacji NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Opis

Ta usługa tworzy wpis przychodzący jako statyczny (trwały wpis, nigdy nie wygasa) i dodaje go do tabeli translacji NAT. Te wpisy są zwykle tworzone dla serwerów hosta lokalnego, w których połączenie jest inicjowane z hosta w sieci zewnętrznej. Serwer NAT sprawdza, czy port zewnętrzny nie jest już używany w tabeli translacji lub jest powiązany przez wcześniej istniejące gniazdo NetX Duo tego samego protokołu.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych
- **entry_ptr** Wskaźnik do wpisu tłumaczenia
- **local_ip_address** Adres IP hosta lokalnego
- **external_port** Port docelowy w sieci zewnętrznej
- **local_port** Port źródłowy (hosta lokalnego)
- **Protokół** Protokół pakietów (np. TCP)

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie utworzono wpis **NX_SUCCESS** (0x00)
- **NX_NAT_PORT_UNAVAILABLE** (0XD0D) nieprawidłowy port zewnętrzny
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_PARAM_ERROR (0xD01) Nieprawidłowa wejściowa niebędąca wskaźnikiem

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

Usuwanie wpisu przychodzącego w tabeli translacji NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Opis

Ta usługa usuwa określony wpis przychodzący z tabeli translacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **nat_ptr** Wskaźnik do wystąpienia translatora adresów sieciowych
- **delete_entry_ptr** Wskaźnik do wpisu translacji NAT

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto wpis **NX_SUCCESS** (0x00)
- Nie znaleziono wpisu **NX_NAT_ENTRY_NOT_FOUND** (0xD04)
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Nieprawidłowy typ tłumaczenia

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
