---
title: Rozdział 3 — opis Azure RTOS NetX Duo AutoIP
description: Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX Duo AutoIP (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82a186505104983dbe6964f92e89c8e775d545eedb6495e27f21542d7660bf42
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791197"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a>Rozdział 3 — opis Azure RTOS NetX Duo AutoIP

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX Duo AutoIP (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_auto_ip_create:** tworzenie *wystąpienia funkcji AutoIP*
- **nx_auto_ip_delete:** Usuwanie *wystąpienia funkcji AutoIP*
- **nx_auto_ip_get_address:** uzyskiwanie *bieżącego adresu AutoIP*
- **nx_auto_ip_set_interface:** ustaw *interfejs IP wymagający adresu AutoIP*
- **nx_auto_ip_start:** Uruchamianie *przetwarzania autoIP*
- **nx_auto_ip_stop:** *Zatrzymaj przetwarzanie funkcji AutoIP*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Tworzenie wystąpienia funkcji AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie funkcji AutoIP dla określonego wystąpienia adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr:** Wskaźnik do bloku sterowania funkcji AutoIP.
- **name:** Nazwa wystąpienia usługi AutoIP.
- **ip_ptr:** Wskaźnik do wystąpienia adresu IP.
- **stack_ptr:** Wskaźnik do obszaru stosu wątków funkcji AutoIP.
- **stack_size:** rozmiar obszaru stosu wątków funkcji AutoIP.
- **priority:** priorytet wątku autoip.

> [!NOTE]
> Jeśli jest używany protokół DHCP, wątek DHCP musi mieć wyższy priorytet niż wątek wystąpienia ip i wątek autoIP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie funkcji AutoIP.
- **NX_AUTO_IP_ERROR:**(0xA00) Błąd tworzenia funkcji AutoIP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik autoIP, ip_ptr lub stosu.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

Usuwanie wystąpienia funkcji AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie funkcji AutoIP w określonym wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr:** Wskaźnik do bloku sterowania funkcji AutoIP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie funkcji AutoIP.
- **NX_AUTO_IP_ERROR:**(0xA00) AutoIP delete error (Błąd usuwania funkcji AutoIP).
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik funkcji AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

Uzyskiwanie bieżącego adresu AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera obecnie konfigurowy adres AutoIP. Jeśli go nie ma, zwracany jest adres IP 0.0.0.0.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr:** Wskaźnik do bloku sterowania funkcji AutoIP.
- **local_ip_address:** miejsce docelowe dla zwracanych adresów IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne uzyskiwanie adresu autoIP.
- **NX_AUTO_IP_NO_LOCAL:**(0xA01) Brak prawidłowego adresu AutoIP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik funkcji AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, czasomierze, wątki, isr

### <a name="example"></a>Przykład

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

Ustawianie interfejsu sieciowego dla funkcji AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa ustawia indeks dla interfejsu sieciowego, który funkcja AutoIP będzie sondować pod adresem IP sieci. Wartość domyślna to zero (podstawowy interfejs sieciowy). Dotyczy tylko urządzeń wieloadresowych.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr:** Wskaźnik do bloku sterowania funkcji AutoIP.
- **interface_index:** Interfejs sondowania adresu IP dla

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zestaw pomyślnego interfejsu autoIP
- **NX_AUTO_IP_BAD_INTERFACE_INDEX:**(0xA02) Nieprawidłowy wskaźnik autoIP NX_PTR_ERROR (0x16) nieprawidłowy interfejs sieciowy.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, czasomierze, wątki, isr

### <a name="example"></a>Przykład

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

Rozpoczynanie przetwarzania funkcji AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Opis

Ta usługa uruchamia protokół AutoIP we wcześniej utworzonym wystąpieniu funkcji AutoIP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr:** Wskaźnik do bloku sterowania funkcji AutoIP.
- **starting_local_address:** opcjonalny adres początkowy funkcji AutoIP. Wartość właściwości IP_ADDRESS(0,0,0,0) określa, że powinien zostać uzyskany losowy adres AutoIP. W przeciwnym razie, jeśli zostanie określony prawidłowy adres AutoIP, funkcja NetX AutoIP spróbuje przypisać ten adres.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne uruchomienie funkcji AutoIP.
- **NX_AUTO_IP_ERROR:**(0xA00) AutoIP start error (Błąd uruchamiania funkcji AutoIP).
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik funkcji AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

Zatrzymywanie przetwarzania funkcji AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje protokół AutoIP dla wcześniej utworzonego i uruchomionego wystąpienia funkcji AutoIP. Ta usługa jest zwykle używana, gdy adres IP jest zmieniany za pośrednictwem protokołu DHCP lub ręcznie na adres bez funkcji AutoIP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr:** wskaźnik do bloku sterowania autoIP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne zatrzymanie funkcji AutoIP.
- **NX_AUTO_IP_ERROR:**(0xA00) AutoIP stop error (Błąd zatrzymania funkcji AutoIP).
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik funkcji AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start