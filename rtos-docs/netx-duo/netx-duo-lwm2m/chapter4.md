---
title: Rozdział 4 — Opis usług klienta LWM2M
description: Ten rozdział zawiera opis wszystkich usług LWM2M Client w porządku alfabetycznym.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821834"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Rozdział 4 Opis usług klienta LWM2M

Ten rozdział zawiera opis wszystkich usług klienta LWM2M wymienionych poniżej w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione**  **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

**LWM2M zarządzanie klientami:**

- nx_lwm2m_client_create: *Utwórz klienta lwm2m*

- nx_lwm2m_client_delete: *Usuwanie klienta lwm2m*

- nx_lwm2m_client_lock: *Zablokuj klienta lwm2m*

- nx_lwm2m_client_unlock: *Odblokuj klienta lwm2m*

**LWM2M zarządzanie sesją klienta:**

- nx_lwm2m_client_session_create: *Utwórz sesję klienta lwm2m*

- nx_lwm2m_client_session_delete: *usuwanie sesji klienta lwm2m*

- nx_lwm2m_client_session_bootstrap: *Uruchamianie sesji z serwerem Bootstrap*

- nx_lwm2m_client_session_bootstrap_dtls: *Rozpoczynanie bezpiecznej sesji z serwerem Bootstrap*

- nx_lwm2m_client_session_register_info_get: *pobieranie informacji o rejestrowaniu serwera lwm2m*

- nx_lwm2m_client_session_register: *Uruchamianie sesji z serwerem lwm2m*

- nx_lwm2m_client_session_register_dtls: *Rozpoczynanie bezpiecznej sesji z serwerem lwm2m*

- nx_lwm2m_client_session_update: *Aktualizowanie sesji przy użyciu serwera lwm2m*

- nx_lwm2m_client_session_deregister: *przerywanie sesji z serwerem lwm2m*

- nx_lwm2m_client_session_error_get: *Pobierz ostatni błąd sesji*

**Implementacja obiektu urządzenia:**

- nx_lwm2m_client_device_callbacks_set: *Ustaw wywołania zwrotne aplikacji obiektu urządzenia*

- nx_lwm2m_client_device_error_push: *Dodaj kod błędu do obiektu urządzenia*

- nx_lwm2m_client_device_error_reset: *Resetowanie kodów błędów obiektu urządzenia*

- nx_lwm2m_client_device_resource_changed: *zmiana sygnału zasobu obiektu urządzenia*

**Implementacja obiektu aktualizacji oprogramowania układowego:**

- nx_lwm2m_firmware_create: *Tworzenie obiektu aktualizacji oprogramowania układowego*

- nx_lwm2m_firmware_package_info_set: *Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego*

- nx_lwm2m_firmware_result_set: *Ustaw wynik aktualizacji oprogramowania układowego*

- nx_lwm2m_firmware_state_set: *Ustaw stan aktualizacji oprogramowania układowego*

**Implementacja obiektów niestandardowych:**

- nx_lwm2m_client_object_add: *Dodawanie implementacji obiektu do klienta lwm2m*

- nx_lwm2m_client_object_remove: *usuwanie implementacji obiektu z klienta lwm2m*

- nx_lwm2m_client_object_instance_add: *Dodaj wystąpienie obiektu do Lwm2m klienta*

- nx_lwm2m_client_object_instance_remove: *usuwanie wystąpienia obiektu z klienta lwm2m*

- nx_lwm2m_object_resource_changed: *zmiana sygnału dla wartości zasobu wystąpienia obiektu*

**Zarządzanie urządzeniami lokalnymi**

- nx_lwm2m_client_object_create: *Utwórz nowe wystąpienie obiektu*

- nx_lwm2m_client_object_delete: *usuwanie wystąpienia obiektu*

- nx_lwm2m_client_object_discover: *odnajdywanie zasobów wystąpienia obiektu*

- nx_lwm2m_client_object_execute: *wykonywanie zasobu wystąpienia obiektu*

- nx_lwm2m_client_object_next_get: *Pobieranie listy obiektów wdrożonych przez klienta lwm2m*

- nx_lwm2m_client_object_instance_next_get: *Pobieranie listy wystąpień obiektu*

- nx_lwm2m_client_object_read: *Odczytywanie wartości zasobów wystąpienia obiektu*

- nx_lwm2m_client_object_write: *zmiana wartości zasobów wystąpienia obiektu*

**Ustawienia informacji o zasobach i wartości:**

- nx_lwm2m_client_resource_info_set: *Ustaw informacje o zasobie*

- nx_lwm2m_client_resource_string_set: *Ustaw wartość zasobu jako ciąg*

- nx_lwm2m_client_resource_integer32_set: *Ustaw wartość zasobu jako 32-bitową liczbę całkowitą*

- nx_lwm2m_client_resource_integer64_set: *Ustaw wartość zasobu jako 64-bitową liczbę całkowitą*

- nx_lwm2m_client_resource_float32_set: *Ustaw wartość zasobu jako 32-bitową zmiennoprzecinkową*

- nx_lwm2m_client_resource_float64_set: *Ustaw wartość zasobu jako 64-bitową zmiennoprzecinkową*

- nx_lwm2m_client_resource_boolean_set: *Ustaw wartość zasobu jako logiczną*

- nx_lwm2m_client_resource_objlnk_set: *Ustaw wartość zasobu jako link do obiektu*

- nx_lwm2m_client_resource_opaque_set: *Ustaw wartość zasobu jako nieprzezroczystą*

- nx_lwm2m_client_resource_instance_set: *Ustaw wartość zasobu jako wystąpienie dla wielu zasobów*
-
- nx_lwm2m_client_resource_dim_set: *Ustaw wymiar zasobu dla wielu zasobów.*

**Informacje o zasobach i wartości:**

- nx_lwm2m_client_resource_info_get: *Uzyskiwanie informacji o zasobie*

- nx_lwm2m_client_resource_string_get: *pobieranie wartości zasobu ciągu*

- nx_lwm2m_client_resource_integer32_get: *pobieranie wartości 32-bitowego zasobu liczb całkowitych*

- nx_lwm2m_client_resource_integer64_get: *pobieranie wartości 64-bitowego zasobu liczb całkowitych*

- nx_lwm2m_client_resource_float32_get: *pobieranie wartości 32-bitowego zasobu zmiennoprzecinkowego*

- nx_lwm2m_client_resource_float64_get: *pobieranie wartości 64-bitowego zasobu zmiennoprzecinkowego*

- nx_lwm2m_client_resource_boolean_get: *pobieranie wartości zasobu logicznego*

- nx_lwm2m_client_resource_objlnk_get: *pobieranie wartości zasobu linku do obiektu*

- nx_lwm2m_client_resource_opaque_get: *Pobierz wartość nieprzezroczystego zasobu*

- nx_lwm2m_client_resource_instance_get: *Pobieranie wystąpienia zasobu dla wielu zasobów*

- nx_lwm2m_client_resource_dim_get: *Pobierz wymiar zasobu dla wielu zasobów.*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Tworzy klienta LWM2M.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta LWM2M, które działa w kontekście jego własnego wątku ThreadX.

Klient LWM2M implementuje następujące obiekty OMA LWM2M: Security (0), Server (1), Access Control (2) i Device (3). Inne implementacje obiektów muszą być dodane przez aplikację.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_pool_ptr** Wskaźnik do domyślnej puli pakietów dla tego klienta LWM2M.
- **name_ptr** Wskaźnik do LWM2M nazwa punktu końcowego klienta.
- **name_length** Długość nazwy punktu końcowego klienta LWM2M.
- **msisdn_ptr** Wskaźnik do MSISDN, w którym można nawiązać połączenie z klientem LWM2M do użycia z powiązaniem programu SMS, może mieć wartość NULL, Jeśli powiązanie programu SMS nie jest obsługiwane.
- **msisdn_length** Długość numeru MSISDN.
- **binding_modes** Powiązanie i tryby obsługiwane przez klienta LWM2M muszą być kombinacją flag NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S i NX_LWM2M_BINDING_SQ.
- **stack_ptr** Wskaźnik do obszaru stosu wątku klienta LWM2M.
- **stack_size** Rozmiar stosu wątku klienta LWM2M.
- **priorytet** Priorytet klienta LWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Klient LWM2M został pomyślnie utworzony.
- **NX_LWM2M_CLIENT_ERROR** Wystąpił błąd podczas tworzenia klienta LWM2M.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.
- **NX_SIZE_ERROR** Nieprawidłowy rozmiar stosu.
- **NX_OPTION_ERROR** Nieprawidłowy priorytet.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Usuwa klienta LWM2M.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta LWM2M.

Wszystkie sesje, które są obecnie dołączone do klienta, są również usuwane przez to wywołanie.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Klient LWM2M został pomyślnie usunięty.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

Ustawia wywołanie zwrotne aplikacji obiektu urządzenia.

### <a name="prototype"></a>Prototype

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Opis

Ta usługa służy do instalowania wywołania zwrotnego aplikacji w celu zaimplementowania operacji na zasobach obiektów urządzenia LWM2M, które nie są obsługiwane przez klienta LWM2M.

Klient LWM2M implementuje następujące zasoby: kod błędu (11), resetowanie kodu błędu (12) i obsługiwane powiązania i tryby (16), operacje innych zasobów są przekierowywane do aplikacji.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **operation_callback** Wywołanie zwrotne operacji dla "read", "Discovery", "Write" i "Execute".

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Wywołanie zwrotne operacji zostało pomyślnie ustawione.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
Dodaje kod błędu do obiektu urządzenia.

### <a name="prototype"></a>Prototype

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Opis

Ta usługa dodaje nowe wystąpienie do zasobu kod błędu (11) urządzenia obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **kod** Nowy kod błędu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

Maksymalna liczba przechowywanych kodów błędów ma

został osiągnięty.

NX_PTR_ERROR nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Resetuje kody błędów obiektu urządzenia.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie wystąpienia zasobów kodu błędu z obiektu urządzenia. Jest to równoznaczne z wykonaniem kodu błędu resetowania zasobu (12).

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Sygnalizuje zmianę zasobu obiektu urządzenia.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Opis

Usługa jest używana przez aplikację do sygnalizowania klienta LWM2M, że zasób urządzenia obiektu został zmieniony. Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **zasób** Wskaźnik do struktury opisującej zasób, który został zmieniony.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Utwórz obiekt oprogramowania układowego klienta LWM2M. 

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>Opis

Usługa jest używana przez aplikację do tworzenia obiektu oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.
- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **Protokoły** Obsługiwane protokoły.
- **package_callback** Wywołanie zwrotne pakietu.
- **package_uri_callback** Wywołanie zwrotne URI pakietu.
- **update_callback** Wywołanie zwrotne aktualizacji.

### <a name="return-values"></a>Wartości zwrócone

**NX_SUCCESS** Operacja zakończona pomyślnie.
**NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

Ustawia informacje o pakiecie oprogramowania układowego klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Opis

Ta usługa jest używana przez aplikację do ustawiania zasobów informacji o pakiecie dla obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.
- **Nazwa** Nazwa pakietu oprogramowania układowego.
- **name_length** Długość nazwy.
- **wersja** Wersja pakietu oprogramowania układowego.
- **version_length** Długość wersji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

Ustawia zasób wynik aktualizacji dla obiektu aktualizacji oprogramowania układowego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Opis

Ta usługa jest używana przez aplikację do ustawiania zasobu wynik aktualizacji dla obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.
- **wynik** Wynik aktualizacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Ustawia zasób wynik aktualizacji dla obiektu aktualizacji oprogramowania układowego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Opis

Ta usługa jest używana przez aplikację do ustawiania stanu obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.
- **stan** Stan obiektu oprogramowania układowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Blokuje klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa blokuje klienta LWM2M, aby zapobiec współbieżnemu dostępowi do obiektów LWM2M z serwerów lub z innego wątku aplikacji.

Jeśli klient LWM2M jest obecnie zablokowany przez inny wątek, funkcja zostanie Zablokowani do momentu odblokowania klienta LWM2M.

Wywołania ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** par mogą być zagnieżdżane.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Dodaje implementację obiektu do klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Opis

Ta usługa dodaje nową implementację obiektu do klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.
- **object_id** Identyfikator obiektu.
- **object_operation** Funkcja wywołania zwrotnego operacji obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Tworzy nowe wystąpienie obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Create" na obiekcie klienta LWM2M, aby utworzyć nowe wystąpienie obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_id_ptr** Wskaźnik na identyfikator nowego wystąpienia może mieć **wartość null** , jeśli klient LWM2M musi przypisać identyfikator wystąpienia. Jeśli identyfikator jest wartością zarezerwowaną 65535, klient LWM2M przypisze identyfikator wystąpienia. Jeśli wartość nie jest równa NULL, przypisany identyfikator jest zwracany po wywołaniu.
- **num_values** Liczba wartości do ustawienia.
- **values_ptr** Wskaźnik na tablicę wartości zasobów, aby zainicjować nowe wystąpienie obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator wystąpienia obiektu już istnieje.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Obiekt nie obsługuje tworzenia wystąpień.
- **NX_LWM2M_CLIENT_NO_MEMORY** Nie można przydzielić pamięci do zapisania nowego wystąpienia.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Usuwa wystąpienie obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Delete" na wystąpieniu obiektu klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_ID** Identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Obiekt nie obsługuje usuwania wystąpienia.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Odnajduje zasoby wystąpienia obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Discover" na wystąpieniu obiektu klienta LWM2M, która zwraca listę zasobów implementowanych przez obiekt.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_ID** Identyfikator wystąpienia obiektu.
- **num_resources** Przy wprowadzaniu rozmiaru buforu docelowego w danych wyjściowych liczba elementów zapisywana w buforze.
- **zasoby** Wskaźnik do bufora docelowego.

### <a name="return-values"></a>Wartości zwrócone

- *NX_SUCCESS** operacja powiodła się.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Bufor zasobów jest za mały, aby można było przechowywać listę zasobów.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Wykonuje operację "Execute" na zasobie wystąpienia obiektu Object.

### <a name="prototype"></a>Prototype

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Execute" na zasobie wystąpienia obiektu klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_ID** Identyfikator wystąpienia obiektu.
- **resource_id** Identyfikator zasobu.
- **arguments_ptr** Wskaźnik do argumentów operacji Execute. Może mieć wartość NULL, jeśli arguments_length wynosi zero.
- **arguments_length** Długość argumentów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Bufor zasobów jest za mały, aby można było przechowywać listę zasobów.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

Dodaje implementację wystąpienia obiektu do obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje nową implementację wystąpienia obiektu do klienta LWM2M. Jeśli wartość instance_id_ptr jest **NX_LWM2M_CLIENT_RESERVED_ID**, klient LWM2M automatycznie przypisze nieużywany identyfikator wystąpienia, w przeciwnym razie klient LWM2M będzie używał zestawu aplikacji wartości. Po pomyślnym dodaniu nowego wystąpienia instance_id zostanie wypełnione instance_id_ptr, aby powrócić do aplikacji.

### <a name="parameters"></a>Parametry

- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.
- **instance_ptr** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.
- **instance_id_ptr** Wskaźnik na identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

Pobiera następne wystąpienie obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego wystąpienia obiektu danego obiektu. Jeśli bieżący identyfikator wystąpienia ma wartość NX_LWM2M_RESERVED_ID (65535) zwracany jest identyfikator pierwszego wystąpienia.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_id_ptr** Wskaźnik do bieżącego identyfikatora wystąpienia obiektu. On return zawiera identyfikator następnego wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_CLIENT_LWM2M_NOT_FOUND** Dany identyfikator wystąpienia jest ostatnim obiektem lub identyfikator obiektu nie jest zaimplementowany.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

Usuwa implementację wystąpienia obiektu z obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie obiektu z obiektu.

### <a name="parameters"></a>Parametry

- ***object_ptr*** Wskaźnik do struktury definiującej implementację obiektu.
- **instance_ptr** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

Pobiera następny obiekt klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego obiektu implementowanego przez klienta LWM2M. Jeśli bieżący identyfikator obiektu jest ustawiony na NX_LWM2M_RESERVED_ID (65535), zwracany jest pierwszy identyfikator obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id_ptr** Wskaźnik do bieżącego identyfikatora obiektu. On return zawiera następny identyfikator obiektu zaimplementowany przez klienta LWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_NOT_FOUND** Określony identyfikator obiektu jest ostatnim z baz danych.
**NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Odczytuje wartości resource's wystąpienia obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "read" na wystąpieniu obiektu klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_ID** Identyfikator wystąpienia obiektu.
- **num_values** Liczba zasobów do odczytania.
- **values_ptr** Wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Zasób nie obsługuje operacji odczytu.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

Usuwa implementację wystąpienia obiektu z obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa obiekt z klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.
- **NX_LWM2M_CLIENT_FORBIDDEN** Usuwanie obiektu wewnętrznego jest zabronione.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

Sygnalizuje zmianę zasobu obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Opis

Usługa jest używana przez aplikację do sygnalizowania klienta LWM2M, że zasób obiektu został zmieniony. Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.

### <a name="parameters"></a>Parametry

- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.
- ***instance_ptr*** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.
- **zasób** Wskaźnik do struktury opisującej zasób, który został zmieniony.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Zmienia wartości zasobu wystąpienia obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Write" na wystąpieniu obiektu klienta LWM2M.

Do parametru *write_op* można określić następujące operacje zapisu.

| Wartość | &nbsp;Operacja zapisu | Opis |
| --- | ---| --- |
| 0 | Aktualizacja częściowa | Dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Zamień wystąpienie | Zamienia wystąpienie obiektu na nowe podane wartości zasobów. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Zastąp zasób | Zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Zapis ładowania początkowego | Wskazuje wywołanie z sekwencji ładowania początkowego. |

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.
- **object_id** Identyfikator obiektu.
- **instance_ID** Identyfikator wystąpienia obiektu.
- **num_values** Liczba zasobów do zapisania.
- **values_ptr** Wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów, typy i wartości do zapisania.
- **write_op** Typ operacji zapisu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Typ zasobu jest nieprawidłowy.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Długość wartości jest zbyt duża, aby można było ją zapisać w wystąpieniu.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Zasób nie obsługuje operacji zapisu.
- **NX_LWM2M_CLIENT_NO_MEMORY** Nie można przydzielić pamięci do przechowywania wartości zasobu.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Wartość zasobu jest nieprawidłowa.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- **NX_OPTION_ERROR** Nieprawidłowy typ operacji zapisu. 
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

Pobiera wartość zasobu logicznego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość zasobu logicznego.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do opisu wartości zasobu.
- **bool_ptr** Wskaźnik do docelowej wartości logicznej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

Ustawia wartość zasobu logicznego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość zasobu logicznego.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **bool_data** Dane logiczne.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

Pobiera wymiar zasobu dla wielu zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Opis

Usługa pobiera wymiar zasobu dla wielu zasobów.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **Przyciemnij** wskaźnik do wymiaru docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

Ustawia wymiar zasobu dla wielu zasobów.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Opis

Usługa ustawia wymiar zasobu dla wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość** Wskaźnik do opisu wartości zasobu.
- wartość wymiaru **Dim** .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Pobiera wartość 32-bitowego zasobu **zmiennoprzecinkowego**

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 32-bitowego zasobu **zmiennoprzecinkowego** .

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **float32_ptr** Wskaźnik do docelowej 32-bitowej wartości **zmiennoprzecinkowej** .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Ustawia wartość 32-bitowego zasobu **zmiennoprzecinkowego**

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 32-bitowego zasobu **zmiennoprzecinkowego** .

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **float32_data** 32-bitowe dane **zmiennoprzecinkowe** .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Pobiera wartość 64-bitowego zasobu zmiennoprzecinkowego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 64-bitowego zasobu **zmiennoprzecinkowego** .

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **float64_ptr** Wskaźnik do docelowej 64-bitowej wartości **zmiennoprzecinkowej** .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością zmiennoprzecinkową.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Ustawia wartość 64-bitowego zasobu **zmiennoprzecinkowego** .

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 64-bitowego zasobu **zmiennoprzecinkowego** .

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **float64_data** 64-bitowe dane **zmiennoprzecinkowe** .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Pobiera informacje o zasobach.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Opis

Usługa pobiera informacje o zasobach.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **resource_id** Wskaźnik na identyfikator zasobu docelowego.
- **operacja** Wskaźnik do operacji zasobu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Ustawia informacje o zasobach.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Opis

Usługa ustawia informacje o zasobach.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **resource_id** Identyfikator zasobu.
- **operacja** Operacja zasobu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

Pobiera wystąpienie wielu zasobów.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>Opis

Usługa pobiera informacje o zasobach.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **resource_instances** Wskaźnik na identyfikator zasobu docelowego.
- **Liczba** Wskaźnik do liczby.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_LWM2M_CLIENT_NO_MEMORY** Brak pamięci do wypełniania wystąpień.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

Ustawia wystąpienia zasobów.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Opis

Usługa ustawia wystąpienia zasobów dla wielu zasobów.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **resource_instance** Wskaźnik do wystąpień zasobów.
- **Liczba** Liczba wystąpień zasobów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Pobiera wartość 32-bitowego zasobu liczby całkowitej.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 32-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **integer32_ptr** Wskaźnik na 32-bitową wartość całkowitą.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością całkowitą.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Ustawia wartość 32-bitowego zasobu liczby całkowitej.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 32-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **integer32_data** 32-bitowe dane całkowite.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Pobiera wartość 64-bitowego zasobu liczby całkowitej.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 64-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **integer64_ptr** Wskaźnik na 64-bitową wartość całkowitą.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest 64-bitową wartością całkowitą.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Ustaw wartość 64-bitowego zasobu liczb całkowitych

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 64-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **integer64_data** 64-bitowa liczba całkowita.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Pobiera wartość zasobu linku do obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość linku do obiektu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **object_id** Wskaźnik na identyfikator obiektu.
- **instance_ID** Wskaźnik na identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością linku obiektu.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

Ustawia wystąpienia zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Opis

Usługa ustawia wartość zasobu linku do obiektu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **object_id** Identyfikator obiektu.
- **instance_ID** Identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

Pobiera wartość nieprzezroczystego zasobu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Opis

Usługa Pobiera wartość nieprzezroczystego zasobu. Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **opaque_ptr** Wskaźnik na dane nieprzezroczyste.
- **opaque_length** Wskaźnik na nieprzezroczystą długość danych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest zasobem nieprzezroczystym.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

Ustawia wartość nieprzezroczystego zasobu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Opis

Usługa ustawia wartość nieprzezroczystego zasobu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **opaque_ptr** Wskaźnik na dane nieprzezroczyste.
- **opaque_length** Długość nieprzezroczystych danych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Pobiera wartość zasobu ciągu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość zasobu ciągu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **string_ptr** Wskaźnik na wskaźnik ciągu docelowego.
- **string_length** Wskaźnik na długość ciągu docelowego. Może mieć **wartość null** , jeśli ciąg jest zakończony znakiem null.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością ciągu.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Ustawia wartość zasobu ciągu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 64-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik na zasób.
- **string_ptr** Wskaźnik na ciąg.
- **string_length** Długość ciągu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Uruchamia sesję z serwerem Bootstrap.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję z serwerem Bootstrap. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.
- **security_id** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na NX_LWM2M_RESERVED_ID (65535), jeśli na serwerze Bootstrap nie zdefiniowano wystąpienia zabezpieczeń.
- **IP_address** Adres IP serwera programu.
- **port** Port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Uruchamia bezpieczną sesję z serwerem Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję z serwerem Bootstrap przy użyciu bezpiecznego połączenia DTLS. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza. Należy zdefiniować **NX_SECURE_ENABLE_DTLS** .

Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta. 

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.
- **security_id** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na **NX_LWM2M_RESERVED_ID** (65535), jeśli na serwerze Bootstrap nie zdefiniowano wystąpienia zabezpieczeń.
- **IP_address** Adres IP serwera programu.
- **port** Port UDP serwera.
- **dtls_session_ptr** Sesja DTLS używana dla sesji Bootstrap.
- **dtls_local_port** Lokalny port UDP używany do sesji DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Tworzy sesję klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Opis

Ta usługa tworzy nową sesję klienta LWM2M dołączoną do istniejącego klienta LWM2M. Sesja jest używana przez klienta LWM2M do komunikacji z serwerem Bootstrap lub serwerem LWM2M. 

Aplikacja musi udostępniać funkcję wywołania zwrotnego, która będzie wywoływana, gdy stan sesji zostanie zaktualizowany.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.
- **client_ptr** Wskaźnik do wcześniej utworzonego klienta LWM2M.
- **state_callback** Wywołanie zwrotne aplikacji wywoływane w przypadku zmiany stanu sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Usuwa sesję klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa sesję klienta LWM2M.

Po usunięciu klienta LWM2M przez wywołanie nx_lwm2m_client_delete wszystkie sesje dołączone do klienta również zostaną usunięte.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Kończy sesję z serwerem LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Wyrejestrowanie" na serwerze LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klient nie jest zarejestrowany na serwerze.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Pobiera ostatni błąd sesji.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca kod błędu sesji, gdy sesja jest w stanie błędu.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Sesja nie jest w stanie błędu.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** Nieprawidłowy adres serwera.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Ładunek żądania nie mieści się w buforze sieciowym.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** Nie można ustanowić bezpiecznego połączenia z serwerem.
- **NX_LWM2M_ CLIENT_ERROR** Nieokreślony błąd.
- **NX_LWM2M_ CLIENT_FORBIDDEN** Odmowa rejestracji przez serwer.
- **NX_LWM2M_ CLIENT_NOT_FOUND** Nie odnaleziono klienta przez serwer podczas aktualizowania/wyrejestrowywania.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Wystąpienie obiektu serwera odpowiadające sesji zostało usunięte.
- **NX_LWM2M_ CLIENT_TIMED_OUT** Brak odpowiedzi z serwera.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Uruchamia sesję z serwerem LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Opis

Ta usługa wykonuje operację "Register" na serwerze LWM2M. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.

Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.
- **server_id** Krótki identyfikator serwera LWM2M.
- **IP_address** Adres IP serwera programu.
- **port** Port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Uruchamia bezpieczną sesję z serwerem LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Register" na serwerze LWM2M przy użyciu bezpiecznego połączenia usługi DTLS. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.

Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza. Należy zdefiniować **NX_SECURE_ENABLE_DTLS** .

Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.
- **server_id** Krótki identyfikator serwera LWM2M.
- **IP_address** Adres IP serwera programu.
- **port** Port UDP serwera.
- **dtls_session_ptr** Sesja DTLS używana na potrzeby sesji LWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Uruchamia bezpieczną sesję z serwerem LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>Opis

Po ustanowieniu sesji komunikacji z serwerem Bootstrap. Aplikacja może wywołać ten interfejs API, aby uzyskać informacje o serwerze i zabezpieczeniach dla kolejnego kroku rejestracji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.
- **security_instance_id** Identyfikator wystąpienia zabezpieczeń.
- **server_id** Wskaźnik na identyfikator serwera docelowego.
- **server_uri** Wskaźnik na identyfikator URI serwera docelowego.
- **server_uri_len** Wskaźnik na długość identyfikatora URI serwera docelowego.
- **security_mode** Wskaźnik do docelowego trybu zabezpieczeń.
- **pub_key_or_id** Wskaźnik na docelowy klucz publiczny lub tożsamość.
- **pub_key_or_id_len** Wskaźnik na docelowy klucz publiczny lub długość tożsamości.
- **server_pub_key** Wskaźnik na klucz publiczny serwera docelowego.
- **server_pub_key_len** Wskaźnik na długość klucza publicznego serwera docelowego.
- **SECRET_KEY** Wskaźnik na docelowy klucz tajny.
- **secret_key_len** Wskaźnik na długość docelowego klucza tajnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_NOT_FOUND** Brak wystąpienia obiektu zabezpieczeń.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Aktualizuje sesję z serwerem LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Update" na serwerze LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klient nie jest zarejestrowany na serwerze.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Odblokowuje klienta LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa odblokowuje klienta LWM2M poprzednio zablokowany przez wywołanie do ***nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja zakończona pomyślnie.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```