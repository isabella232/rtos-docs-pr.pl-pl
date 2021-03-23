---
title: Rozdział 3 — Opis usługi Azure RTO NetX Duo AutoIP Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Duo AutoIP Services (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822069"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a>Rozdział 3 — Opis usługi Azure RTO NetX Duo AutoIP Services

Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Duo AutoIP Services (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_auto_ip_create**: *Tworzenie wystąpienia AutoIP*
- **nx_auto_ip_delete**: *usuwanie wystąpienia AutoIP*
- **nx_auto_ip_get_address**: *Pobierz bieżący adres AutoIP*
- **nx_auto_ip_set_interface**: *Ustaw interfejs IP wymagający adresu AutoIP*
- **nx_auto_ip_start**: *Uruchamianie przetwarzania AutoIP*
- **nx_auto_ip_stop**: *Zatrzymywanie przetwarzania AutoIP*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Utwórz wystąpienie AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie AutoIP na określonym wystąpieniu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.
- **name**: nazwa wystąpienia AutoIP.
- **ip_ptr**: wskaźnik do wystąpienia adresu IP.
- **stack_ptr**: wskaźnik do obszaru stosu wątku AutoIP.
- **stack_size**: rozmiar obszaru stosu wątku AutoIP.
- **priorytet**: priorytet wątku AutoIP.

> [!NOTE]
> Jeśli używany jest protokół DHCP, wątek DHCP musi mieć wyższy priorytet niż wątek wystąpienia IP i wątek AutoIP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne utworzenie AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP tworzenia błędu.
- NX_PTR_ERROR: (0x16) nieprawidłowy AutoIP, ip_ptr lub wskaźnik stosu.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

Usuń wystąpienie AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie AutoIP w określonym wystąpieniu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne usunięcie AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd usuwania.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

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

Pobierz bieżący adres AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera aktualnie skonfigurowany adres AutoIP. Jeśli nie istnieje, zwracany jest adres IP 0.0.0.0.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.
- **local_ip_address**: miejsce docelowe dla zwrotnego adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne pobieranie adresu AutoIP.
- **NX_AUTO_IP_NO_LOCAL**: (0xA01) nieprawidłowy adres AutoIP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, czasomierze, wątki, procedury ISR

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

Ustaw interfejs sieciowy dla AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa ustawia indeks dla interfejsu sieciowego, AutoIP będzie sondować dla sieciowego adresu IP. Wartość domyślna to zero (podstawowy interfejs sieciowy). Dotyczy tylko urządzeń z wieloma adresami.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.
- **interface_index**: interfejs do sondowania adresu IP dla

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie ustawiono interfejs AutoIP
- **NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0XA02) Nieprawidłowy interfejs sieciowy NX_PTR_ERROR (0X16) Nieprawidłowy wskaźnik AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, czasomierze, wątki, procedury ISR

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

Rozpocznij przetwarzanie AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Opis

Ta usługa uruchamia protokół AutoIP na wcześniej utworzonym wystąpieniu usługi AutoIP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.
- **starting_local_address**: opcjonalny adres początkowy AutoIP. Wartość IP_ADDRESS (0, 0, 0, 0) określa, że losowy adres AutoIP powinien być pochodny. W przeciwnym razie, jeśli określono prawidłowy adres AutoIP, NetX AutoIP próbuje przypisać ten adres.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne uruchomienie AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd uruchomienia.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>Zobacz też

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

Zatrzymaj przetwarzanie AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia zatrzymanie protokołu AutoIP na wcześniej utworzonym i uruchomionym wystąpieniu usługi AutoIP. Ta usługa jest zwykle używana, gdy adres IP zostanie zmieniony za pośrednictwem protokołu DHCP lub ręcznie na adres inny niż AutoIP.

### <a name="input-parameters"></a>Parametry wejściowe

- **auto_ip_ptr**: wskaźnik do bloku sterowania AutoIP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne zatrzymywanie AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP błąd zatrzymania.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik AutoIP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

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