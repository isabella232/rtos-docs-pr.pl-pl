---
title: Rozdział 4 — Opis usług KLIENCKICH SYSTEMU GDYM2M
description: Ten rozdział zawiera opis wszystkich usług klienckich ZESM2M w kolejności alfabetycznej.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0956cb43f4fcd87d5bd4d90b2288ce6f8d5295ee0be8b8a9f4719ad842e00b2a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783445"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Rozdział 4 Opis usług KLIENCKICH ZESM2M

Ten rozdział zawiera opis wszystkich usług klienckich ZESM2M wymienionych poniżej w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

**ZARZĄDZANIE KLIENTEM ZAM2M:**

- nx_lwm2m_client_create: *Tworzenie klienta CELUM2M*

- nx_lwm2m_client_delete: *Usuwanie klienta ZESM2M*

- nx_lwm2m_client_lock: Blokowanie *klienta SYSTEMU LOCKM2M*

- nx_lwm2m_client_unlock: *odblokowywanie klienta SIMM2M*

**ZARZĄDZANIE SESJAMI KLIENTA ZAM2M:**

- nx_lwm2m_client_session_create: *Tworzenie sesji klienta KOMPUTERA 2M*

- nx_lwm2m_client_session_delete: Usuwanie *sesji klienta SYSTEMU PLIKÓW 2M*

- nx_lwm2m_client_session_bootstrap: *rozpoczynanie sesji z serwerem Bootstrap*

- nx_lwm2m_client_session_bootstrap_dtls: Uruchamianie *bezpiecznej sesji z serwerem Bootstrap*

- nx_lwm2m_client_session_register_info_get: Uzyskiwanie *informacji o rejestracji serwera w programie DHCP2M*

- nx_lwm2m_client_session_register: *rozpoczynanie sesji z serwerem SEAM2M*

- nx_lwm2m_client_session_register_dtls: Uruchamianie *bezpiecznej sesji z serwerem SEAM2M*

- nx_lwm2m_client_session_update: aktualizowanie *sesji za pomocą serwera SEAM2M*

- nx_lwm2m_client_session_deregister: Zakończenie *sesji z serwerem DNS2M*

- nx_lwm2m_client_session_error_get: Uzyskiwanie *ostatniego błędu sesji*

**Implementacja obiektu urządzenia:**

- nx_lwm2m_client_device_callbacks_set: *ustawianie wywołań zwrotnych aplikacji obiektu urządzenia*

- nx_lwm2m_client_device_error_push: Dodawanie *kodu błędu do obiektu urządzenia*

- nx_lwm2m_client_device_error_reset: *Resetowanie kodów błędów obiektu urządzenia*

- nx_lwm2m_client_device_resource_changed: *Sygnalizowanie zmiany zasobu obiektu urządzenia*

**Implementacja obiektu aktualizacji oprogramowania układowego:**

- nx_lwm2m_firmware_create: Tworzenie *obiektu aktualizacji oprogramowania układowego*

- nx_lwm2m_firmware_package_info_set: Ustawianie *informacji o pakiecie aktualizacji oprogramowania układowego*

- nx_lwm2m_firmware_result_set: ustaw *wynik aktualizacji oprogramowania układowego*

- nx_lwm2m_firmware_state_set: Ustaw *stan aktualizacji oprogramowania układowego*

**Implementacja obiektów niestandardowych:**

- nx_lwm2m_client_object_add: Dodawanie *implementacji obiektu do klienta PROJEKTUM2M*

- nx_lwm2m_client_object_remove: usuwanie *implementacji obiektu z klienta PROJEKTUM2M*

- nx_lwm2m_client_object_instance_add: Dodawanie *wystąpienia obiektu do klienta KOMPUTERA 2M*

- nx_lwm2m_client_object_instance_remove: usuwanie *wystąpienia obiektu z klienta KOMPUTERA2M*

- nx_lwm2m_object_resource_changed: *Zasygnalizuj zmianę wartości zasobu wystąpienia obiektu*

**Lokalne Zarządzanie urządzeniami**

- nx_lwm2m_client_object_create: tworzenie *nowego wystąpienia obiektu*

- nx_lwm2m_client_object_delete: usuwanie *wystąpienia obiektu*

- nx_lwm2m_client_object_discover: *odnajdywanie zasobów wystąpienia obiektu*

- nx_lwm2m_client_object_execute: Wykonywanie *zasobu wystąpienia obiektu*

- nx_lwm2m_client_object_next_get: *pobierz listę obiektów zaimplementowanych przez klienta SYSTEMU THEM2M*

- nx_lwm2m_client_object_instance_next_get: *uzyskiwanie listy wystąpień obiektu*

- nx_lwm2m_client_object_read: *odczytywanie wartości zasobów wystąpienia obiektu*

- nx_lwm2m_client_object_write: zmienianie *wartości zasobów wystąpienia obiektu*

**Ustawienia informacji o zasobach i wartości:**

- nx_lwm2m_client_resource_info_set: ustawianie *informacji o zasobie*

- nx_lwm2m_client_resource_string_set: *ustaw wartość zasobu jako ciąg*

- nx_lwm2m_client_resource_integer32_set: ustaw *wartość zasobu na 32-bitową liczbę całkowitą*

- nx_lwm2m_client_resource_integer64_set: ustaw *wartość zasobu na 64-bitową liczbę całkowitą*

- nx_lwm2m_client_resource_float32_set: ustaw *wartość zasobu na 32-bitowy zmiennoprzecinkowy*

- nx_lwm2m_client_resource_float64_set: *ustaw wartość zasobu na 64-bitową wartość zmiennoprzecinkową*

- nx_lwm2m_client_resource_boolean_set: *ustaw wartość zasobu jako wartość logiczną*

- nx_lwm2m_client_resource_objlnk_set: ustaw *wartość zasobu jako link obiektu*

- nx_lwm2m_client_resource_opaque_set: ustaw *wartość zasobu jako nieprzezroczystą*

- nx_lwm2m_client_resource_instance_set: ustaw *wartość zasobu jako wystąpienie dla wielu zasobów*
-
- nx_lwm2m_client_resource_dim_set: ustaw *wymiar zasobu dla wielu zasobów.*

**Uzyskiwanie informacji o zasobach i wartości:**

- nx_lwm2m_client_resource_info_get: Uzyskiwanie *informacji o zasobie*

- nx_lwm2m_client_resource_string_get: Uzyskiwanie *wartości zasobu ciągu*

- nx_lwm2m_client_resource_integer32_get: pobierz *wartość 32-bitowego zasobu liczby całkowitej*

- nx_lwm2m_client_resource_integer64_get: *uzyskiwanie wartości 64-bitowego zasobu liczby całkowitej*

- nx_lwm2m_client_resource_float32_get: pobierz *wartość 32-bitowego zasobu zmiennoprzecinkowa*

- nx_lwm2m_client_resource_float64_get: *pobierz wartość 64-bitowego zasobu zmiennoprzecinkowa*

- nx_lwm2m_client_resource_boolean_get: *Uzyskiwanie wartości zasobu logicznych*

- nx_lwm2m_client_resource_objlnk_get: uzyskiwanie *wartości zasobu linku obiektu*

- nx_lwm2m_client_resource_opaque_get: Uzyskiwanie *wartości nieprzezroczystego zasobu*

- nx_lwm2m_client_resource_instance_get: Uzyskiwanie *wystąpienia zasobu dla wielu zasobów*

- nx_lwm2m_client_resource_dim_get: Pobierz *wymiar zasobu dla wielu zasobów.*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Tworzy klienta KOMPUTERA 2M.

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

Ta usługa tworzy wystąpienie klienta KOMPUTERA 2M, które jest uruchamiane w kontekście własnego wątku ThreadX.

Klient SYSTEMM2M implementuje następujące obiekty OMA ZESM2M: Security (0), Server (1), Access Control (2) i Device (3). Inne implementacje obiektów muszą zostać dodane przez aplikację.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_pool_ptr** Wskaźnik do domyślnej puli pakietów dla tego klienta ZESM2M.
- **name_ptr** Wskaźnik do nazwy punktu końcowego klienta APLIKACJIM2M.
- **name_length** Długość nazwy punktu końcowego klienta SYSTEMU DOM2M.
- **msisdn_ptr** Wskaźnik do sieci MSISDN, w której można uzyskać dostęp do klienta MODELUM2M do użycia z powiązaniem SMS, może mieć wartość NULL, jeśli powiązanie SMS nie jest obsługiwane.
- **msisdn_length** Długość numeru MSISDN.
- **binding_modes** Powiązanie i tryby obsługiwane przez klienta MODELUSM2M muszą być kombinacją NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S i NX_LWM2M_BINDING_SQ flagi.
- **stack_ptr** Wskaźnik do obszaru stosu wątku klienta STOSUM2M.
- **stack_size** Rozmiar stosu wątku klienta STOSUM2M.
- **priorytet** Priorytet klienta ZESM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślnie utworzono klienta SYSTEMU THEM2M.
- **NX_LWM2M_CLIENT_ERROR** Błąd tworzenia klienta PODCZASM2M.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.
- **NX_SIZE_ERROR** Nieprawidłowy rozmiar stosu.
- **NX_OPTION_ERROR** Nieprawidłowy priorytet.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Usuwa klienta ZMIM2M.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie klienta z programem PODCZASM2M.

To wywołanie usuwa również wszystkie sesje aktualnie dołączone do klienta.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślnie usunięto klienta ZMIM2M.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa instaluje wywołanie zwrotne aplikacji w celu zaimplementowania operacji na zasobach obiektu urządzenia z systemem SYSTEMM2M, które nie są obsługiwane przez klienta z systemem THEM2M.

Klient RESETM2M implementuje następujące zasoby: Kod błędu (11), Kod błędu resetowania (12) oraz Obsługiwane powiązania i tryby (16), operacje do innych zasobów są przekierowywany do aplikacji.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **operation_callback** Wywołanie zwrotne operacji dla operacji "Read", "Discover", "Write" i "Execute".

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Wywołanie zwrotne operacji zostało pomyślnie ustawione.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa dodaje nowe wystąpienie do zasobu kod błędu (11) urządzenia obiektowego.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **kod** Nowy kod błędu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

Maksymalna liczba przechowywanych kodów błędów

został osiągnięty.

NX_PTR_ERROR nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa usuwa wszystkie wystąpienia zasobów kodu błędu z obiektu urządzenia. Jest to równoważne wykonaniu kodu błędu resetowania zasobu (12).

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Usługa jest używana przez aplikację do sygnalizowania klientowi SIECI 2M, że zasób urządzenia obiektowego uległ zmianie. Jeśli zasób zostanie zaobserwowany przez serwer ZAMIM2M, klient ZM2M wyśle powiadomienie.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **zasób** Wskaźnik do struktury opisującej zmieniony zasób.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Utwórz obiekt oprogramowania układowego klienta KOMPUTERA 2M. 

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

- **firmware_ptr** Wskaźnik do obiektu OPROGRAMOWANIA układowego klienta KOMPUTERAM2M.
- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **protokoły** Obsługiwane protokoły.
- **package_callback** Wywołanie zwrotne pakietu.
- **package_uri_callback** Wywołanie zwrotne URI pakietu.
- **update_callback** Wywołanie zwrotne aktualizacji.

### <a name="return-values"></a>Wartości zwrócone

**NX_SUCCESS** Pomyślna operacja.
**NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ustawia informacje o pakiecie oprogramowania układowego klienta THEM2M.

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

Usługa jest używana przez aplikację do ustawienia zasobów informacji o pakiecie obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do obiektu OPROGRAMOWANIA układowego klienta KOMPUTERAM2M.
- **name (nazwa)** Nazwa pakietu oprogramowania układowego.
- **name_length** Długość nazwy.
- **wersja** Wersja pakietu oprogramowania układowego.
- **version_length** Długość wersji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

Ustawia zasób wyniku aktualizacji obiektu aktualizacji oprogramowania układowego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Opis

Usługa jest używana przez aplikację do ustawienia zasobu wyniku aktualizacji obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do obiektu OPROGRAMOWANIA układowego klienta KOMPUTERAM2M.
- **wynik** Wynik aktualizacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Ustawia zasób wyniku aktualizacji obiektu aktualizacji oprogramowania układowego.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Opis

Usługa jest używana przez aplikację do ustawienia stanu obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr** Wskaźnik do obiektu OPROGRAMOWANIA układowego klienta KOMPUTERAM2M.
- **stan** Stan obiektu oprogramowania układowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Blokuje klienta ZM2M.

### <a name="prototype"></a>Prototype

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa blokuje klienta ZMIM2M, aby uniemożliwić współbieżny dostęp do obiektów THEM2M z serwerów lub innego wątku aplikacji.

Jeśli klient THEM2M jest obecnie zablokowany przez inny wątek, funkcja będzie blokować działanie do momentu odblokowania klienta THEM2M.

Wywołania do ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** pary mogą być zagnieżdżone.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Dodaje implementację obiektu do klienta PROJEKTUM2M.

### <a name="prototype"></a>Prototype

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Opis

Ta usługa dodaje nową implementację obiektu do klienta ZMIM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.
- **object_id** Identyfikator obiektu.
- **object_operation** Funkcja wywołania zwrotnego operacji obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa wykonuje operację "Utwórz" na obiekcie klienta ZMIM2M w celu utworzenia nowego wystąpienia obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id_ptr** Wskaźnik do identyfikatora nowego wystąpienia może być **wartością NULL,** jeśli klient SYSTEMU SYSTEMM2M musi przypisać identyfikator wystąpienia. Jeśli identyfikator jest wartością zarezerwowaną 65535, klient ZM2M przypisze identyfikator wystąpienia. Jeśli nie ma wartości NULL, przypisany identyfikator jest zwracany po wywołaniu.
- **num_values** Liczba wartości do ustawienia.
- **values_ptr** Wskaźnik do tablicy wartości zasobów w celu zainicjowania nowego wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator wystąpienia obiektu już istnieje.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Obiekt nie obsługuje tworzenia wystąpienia.
- **NX_LWM2M_CLIENT_NO_MEMORY** Nie można przydzielić pamięci do przechowywania nowego wystąpienia.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa wykonuje operację "Delete" na wystąpieniu obiektu klienta z elementem THEM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id** Identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Obiekt nie obsługuje usuwania wystąpienia.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa wykonuje operację "Odnajdywanie" na wystąpieniu obiektu klienta KOMPUTERA 2M. Zwraca ona listę zasobów zaimplementowanych przez obiekt .

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id** Identyfikator wystąpienia obiektu.
- **num_resources** Po wejściu rozmiar buforu docelowego, po danych wyjściowych liczba elementów zapisywanych w buforze.
- **zasoby** Wskaźnik do buforu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- *NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Bufor zasobów jest zbyt mały, aby można było przechowywać listę zasobów.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Wykonuje operację "Execute" na zasobie wystąpienia obiektu.

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

Ta usługa wykonuje operację "Execute" na zasobie wystąpienia obiektu klienta THEM2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id** Identyfikator wystąpienia obiektu.
- **resource_id** Identyfikator zasobu.
- **arguments_ptr** Wskaźnik do argumentów operacji wykonywania. Może mieć wartość NULL, arguments_length wartość zero.
- **arguments_length** Długość argumentów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Bufor zasobów jest zbyt mały, aby można było przechowywać listę zasobów.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa dodaje nową implementację wystąpienia obiektu do klienta PROJEKTUM2M. Jeśli wartość właściwości instance_id_ptr to **NX_LWM2M_CLIENT_RESERVED_ID,** klient ZMIM2M automatycznie przypisze nieużywany identyfikator wystąpienia. W przeciwnym razie klient z uprawnieniami DOM2M użyje zestawu aplikacji wartości. Po pomyślnym dodaniu nowego instance_id zostanie wypełniona instance_id_ptr, aby powrócić do aplikacji.

### <a name="parameters"></a>Parametry

- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.
- **instance_ptr** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.
- **instance_id_ptr** Wskaźnik do identyfikatora wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa zwraca identyfikator następnego wystąpienia obiektu danego obiektu. Jeśli bieżący identyfikator wystąpienia jest ustawiony na NX_LWM2M_RESERVED_ID (65535), jest zwracany identyfikator pierwszego wystąpienia.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id_ptr** Wskaźnik do bieżącego identyfikatora wystąpienia obiektu. Zwracany obiekt zawiera następny identyfikator wystąpienia obiektu .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Pomyślna operacja.
- **NX_CLIENT_LWM2M_NOT_FOUND** Podany identyfikator wystąpienia jest ostatnim obiektem lub identyfikator obiektu nie jest zaimplementowany.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

- **NX_SUCCESS** Pomyślna operacja.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

Pobiera następny obiekt klienta THEM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego obiektu zaimplementowanego przez klienta KOMPUTERA 2M. Jeśli bieżący identyfikator obiektu jest ustawiony na wartość NX_LWM2M_RESERVED_ID (65535), zwracany jest pierwszy identyfikator obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id_ptr** Wskaźnik do bieżącego identyfikatora obiektu. W przypadku zwracania zawiera następny identyfikator obiektu zaimplementowany przez klienta SIECI 2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_NOT_FOUND** Podany identyfikator obiektu jest ostatnim z bazy danych.
**NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Odczytuje wartości zasobu wystąpienia obiektu.

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

Ta usługa wykonuje operację "Odczyt" na wystąpieniu obiektu klienta KOMPUTERA 2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id** Identyfikator wystąpienia obiektu.
- **num_values** Liczba zasobów do odczytania.
- **values_ptr** Wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Zasób nie obsługuje operacji odczytu.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa usuwa obiekt z klienta SIECI 2M.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.
- **NX_LWM2M_CLIENT_FORBIDDEN** Usuwanie obiektu wewnętrznego jest zabronione.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Usługa ta jest używana przez aplikację do sygnalizowania klientowi KLASTRA 2M, że zasób obiektu został zmieniony. Jeśli zasób zostanie zaobserwowany przez serwer DHCPM2M, klient NIEM2M wyśle powiadomienie.

### <a name="parameters"></a>Parametry

- **object_ptr** Wskaźnik do struktury definiującej implementację obiektu.
- ***instance_ptr*** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.
- **zasób** Wskaźnik do struktury opisującej zmieniony zasób.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa wykonuje operację "Zapis" na wystąpieniu obiektu klienta KOMPUTERA 2M.

Następujące operacje zapisu można określić w *parametrze write_op* .

| Wartość | Operacja &nbsp; zapisu | Opis |
| --- | ---| --- |
| 0 | Aktualizacja częściowa | Dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Zastępowanie wystąpienia | Zamienia wystąpienie obiektu na nowe podane wartości zasobów. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Zastępowanie zasobu | Zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Zapis ładowania początkowego | Wskazuje wywołanie z sekwencji bootstrap. |

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id** Identyfikator obiektu.
- **instance_id** Identyfikator wystąpienia obiektu.
- **num_values** Liczba zasobów do zapisu.
- **values_ptr** Wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów, typy i wartości do zapisu.
- **write_op** Typ operacji zapisu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Typ zasobu jest nieprawidłowy.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Długość wartości jest zbyt duża, aby można było jej przechowywać w wystąpieniu.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Zasób nie obsługuje operacji zapisu.
- **NX_LWM2M_CLIENT_NO_MEMORY** Nie można przydzielić pamięci do przechowywania wartości zasobu.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Wartość zasobu jest nieprawidłowy.
- **NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- **NX_OPTION_ERROR** Nieprawidłowy typ operacji zapisu. 
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

Pobiera wartość zasobu logicznych.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość zasobu logicznych.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do opisu wartości zasobu.
- **bool_ptr** Wskaźnik do docelowej wartości logicznych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

Ustawia wartość zasobu logicznych.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość zasobu logicznych.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **bool_data** Dane logiczne.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

- **zasób** Wskaźnik do zasobu.
- **dim** Pointer to the destination dimension (wskaźnik do wymiaru docelowego).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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
- dim Dimension value **(wartość** wymiarowa).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Pobiera wartość 32-bitowego zasobu **zmiennoprzecinkowa**

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 32-bitowego zasobu **zmiennoprzecinkowa.**

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **float32_ptr** Wskaźnik do docelowej 32-bitowej wartości **zmiennoprzecinkowa.**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Ustawia wartość 32-bitowego zasobu **zmiennoprzecinkowa**

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 32-bitowego zasobu **zmiennoprzecinkowa.**

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **float32_data** 32-bitowe dane **zmiennoprzecinkowa.**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Pobiera wartość 64-bitowego zasobu zmiennoprzecinkowa.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 64-bitowego zasobu **zmiennoprzecinkowa.**

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **float64_ptr** Wskaźnik do docelowej 64-bitowej wartości **zmiennoprzecinkowa.**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością zmiennoprzecinkową.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Ustawia wartość 64-bitowego zasobu **zmiennoprzecinkowa.**

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 64-bitowego zasobu **zmiennoprzecinkowa.**

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **float64_data** 64-bitowe dane **zmiennoprzecinkowa.**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Pobiera informacje o zasobie.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Opis

Usługa pobiera informacje o zasobie zasobu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **resource_id** Wskaźnik do docelowego identyfikatora zasobu.
- **operacja** Wskaźnik do operacji zasobu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Ustawia informacje o zasobie.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Opis

Usługa ustawia informacje o zasobie.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **resource_id** Identyfikator zasobu.
- **operacja** Działanie zasobu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Usługa pobiera informacje o zasobie zasobu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **resource_instances** Wskaźnik do docelowego identyfikatora zasobu.
- **liczba** Wskaźnik do liczby.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.
- **NX_LWM2M_CLIENT_NO_MEMORY** Brak pamięci do wypełniania wystąpień.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

- **zasób** Wskaźnik do zasobu.
- **resource_instance** Wskaźnik do wystąpień zasobów.
- **liczba** Liczba wystąpień zasobów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Pobiera wartość 32-bitowej liczby całkowitej zasobu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 32-bitowej liczby całkowitej Zasób.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **integer32_ptr** Wskaźnik do wartości 32-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością całkowitą.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Ustawia wartość 32-bitowej liczby całkowitej zasób.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 32-bitowej liczby całkowitej Zasób.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **integer32_data** dane 32-bitowych liczb całkowitych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Pobiera wartość 64-bitowej liczby całkowitej zasobu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 64-bitowej liczby całkowitej Zasób.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **integer64_ptr** Wskaźnik do wartości 64-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest 64-bitową wartością całkowitą.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Ustawianie wartości 64-bitowej liczby całkowitej zasobu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 64-bitowej liczby całkowitej Zasób.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **integer64_data** 64-bitową liczbę całkowitą.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Pobiera wartość zasobu linku obiektu.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Opis

Usługa pobiera wartość linku obiektu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **object_id** Wskaźnik do identyfikatora obiektu.
- **instance_id** Wskaźnik do identyfikatora wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością linku obiektu.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Usługa ustawia wartość zasobu linku obiektu.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **object_id** Identyfikator obiektu.
- **instance_id** Identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Usługa pobiera wartość nieprzezroczystego zasobu. Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **opaque_ptr** Wskaźnik do nieprzezroczystych danych.
- **opaque_length** Wskaźnik do nieprzezroczystej długości danych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest nieprzezroczystym zasobem.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

- **zasób** Wskaźnik do zasobu.
- **opaque_ptr** Wskaźnik do nieprzezroczystych danych.
- **opaque_length** Długość nieprzezroczystych danych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Pobiera wartość ciągu resource.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Opis

Usługa pobiera wartość ciągu Resource.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **string_ptr** Wskaźnik do docelowego wskaźnika ciągu.
- **string_length** Wskaźnik do długości ciągu docelowego. Może mieć **wartość NULL,** jeśli ciąg ma zakończenie o wartości null.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością ciągu.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Ustawia wartość ciągu resource.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Opis

Usługa ustawia wartość 64-bitowej liczby całkowitej Zasób.

### <a name="parameters"></a>Parametry

- **zasób** Wskaźnik do zasobu.
- **string_ptr** Wskaźnik do ciągu.
- **string_length** Długość ciągu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Jeśli zasób "Hold Off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na uruchomienie zainicjowane przez serwer. Jeśli po upływie tego czasu serwer nie zainicjował ładowania początkowego, zostanie wykonana wartość Boostrap zainicjowana przez klienta.

Każda bieżąca aktywna sesja została przerwana przez to wywołanie i zastąpiona przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.
- **security_id** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap należy ustawić na wartość NX_LWM2M_RESERVED_ID (65535), jeśli serwer bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.
- **ip_address** Adres IP serwera.
- **port** Port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa rozpoczyna sesję z serwerem bootstrap przy użyciu bezpiecznego połączenia z usługą DTLS. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza przed wywołaniem tej funkcji. **NX_SECURE_ENABLE_DTLS** musi być zdefiniowany.

Jeśli zasób "Hold Off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na uruchomienie zainicjowane przez serwer, jeśli po upływie tego czasu nie zostanie zainicjowane przez serwer uruchomienie, zostanie wykonana wartość Boostrap zainicjowana przez klienta. 

Każda bieżąca aktywna sesja została przerwana przez to wywołanie i zastąpiona przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.
- **security_id** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap należy ustawić na **wartość NX_LWM2M_RESERVED_ID** (65535), jeśli serwer bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.
- **ip_address** Adres IP serwera.
- **port** Port UDP serwera.
- **dtls_session_ptr** Sesja DTLS do użycia dla sesji bootstrap.
- **dtls_local_port** Lokalny port UDP używany w sesji dtls.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Tworzy sesję klienta KOMPUTERA 2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Opis

Ta usługa tworzy nową sesję klienta SYSTEMU PULPITU 2M dołączona do istniejącego klienta PROGRAMU ONAM2M. Sesja jest używana przez klienta DOM2M do komunikowania się z serwerem Bootstrap lub serwerem THEM2M. 

Aplikacja musi zapewnić funkcję wywołania zwrotnego, która zostanie wywołana po zaktualizowaniu stanu sesji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.
- **client_ptr** Wskaźnik do wcześniej utworzonego klienta SYSTEMU PLIKÓW 2M.
- **state_callback** Wywołanie zwrotne aplikacji, które jest wywoływane po zmianie stanu sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Usuwa SESJM2M sesji klienta.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa sesję klienta KOMPUTERA 2M.

Po usunięciu klienta z programu THEM2M przez wywołanie nx_lwm2m_client_delete zostaną również usunięte wszystkie sesje dołączone do klienta.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Kończy sesję z serwerem ZESM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "De-Register" na serwerze CELUM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klient nie jest zarejestrowany na serwerze.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Sesja nie jest w stanie błędu.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** Nieprawidłowy adres serwera.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Ładunek żądania nie mieści się w buforze sieciowym.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** Nie można nawiązać zabezpieczonego połączenia z serwerem.
- **NX_LWM2M_ CLIENT_ERROR** Nieokreślony błąd.
- **NX_LWM2M_ CLIENT_FORBIDDEN** Rejestracja odrzucona przez serwer.
- **NX_LWM2M_ CLIENT_NOT_FOUND** Klient nie został znaleziony przez serwer podczas aktualizowania/wyrejestrowania.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Wystąpienie obiektu serwera odpowiadające sesji zostało usunięte.
- **NX_LWM2M_ CLIENT_TIMED_OUT** Brak odpowiedzi z serwera.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Uruchamia sesję z serwerem DHCPM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Opis

Ta usługa wykonuje operację "Zarejestruj" na serwerze DNS2M. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwera.

Jeśli rejestracja zakończy się pomyślnie, klient KOMPUTERA2M będzie przetwarzać dalsze operacje z serwera i będzie okresowo wysyłać komunikaty "Aktualizuj", dopóki klient nie zostanie cokoń zarejestrowany.

Każda bieżąca aktywna sesja została przerwana przez to wywołanie i zastąpiona przez nową sesję serwera DHCPM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.
- **server_id** Krótki identyfikator serwera SERWERA THEM2M.
- **ip_address** Adres IP serwera.
- **port** Port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Uruchamia bezpieczną sesję z serwerem DNS2M.

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

Ta usługa wykonuje operację "Zarejestruj" na serwerze CALM2M przy użyciu bezpiecznego połączenia DTLS. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwera.

Sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza przed wywołaniem tej funkcji. **NX_SECURE_ENABLE_DTLS** musi być zdefiniowany.

Jeśli rejestracja zakończy się pomyślnie, klient KOMPUTERA2M będzie przetwarzać dalsze operacje z serwera i będzie okresowo wysyłać komunikaty "Aktualizuj", dopóki klient nie zostanie cokoń zarejestrowany.

Każda bieżąca aktywna sesja została przerwana przez to wywołanie i zastąpiona przez nową sesję serwera DHCPM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.
- **server_id** Krótki identyfikator serwera SERWERA THEM2M.
- **ip_address** Adres IP serwera.
- **port** Port UDP serwera.
- **dtls_session_ptr** Sesja DTLS do użycia dla sesji APARATU2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Uruchamia bezpieczną sesję z serwerem DNS2M.

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

Po nawiązywiono sesję komunikacji z serwerem Bootstrap. Aplikacja może wywołać ten interfejs API, aby uzyskać informacje o serwerze i zabezpieczeniach na następny krok rejestracji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.
- **security_instance_id** Identyfikator wystąpienia zabezpieczeń.
- **server_id** Wskaźnik do identyfikatora serwera docelowego.
- **server_uri** Wskaźnik do docelowego adresu URI serwera.
- **server_uri_len** Wskaźnik do długości adresu URI serwera docelowego.
- **security_mode** Wskaźnik do docelowego trybu zabezpieczeń.
- **pub_key_or_id** Wskaźnik do docelowego klucza publicznego lub tożsamości.
- **pub_key_or_id_len** Wskaźnik do docelowego klucza publicznego lub długości tożsamości.
- **server_pub_key** Wskaźnik do klucza publicznego serwera docelowego.
- **server_pub_key_len** Wskaźnik długości klucza publicznego serwera docelowego.
- **secret_key** Wskaźnik do docelowego klucza tajnego.
- **secret_key_len** Wskaźnik do docelowej długości klucza tajnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_NOT_FOUND** Nie ma wystąpienia obiektu zabezpieczeń.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Aktualizuje sesję za pomocą serwera SEAM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Update" na serwerze WIĘCM2M.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do bloku sterowania sesja klienta APLIKACJI2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klient nie jest zarejestrowany na serwerze.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Odblokowuje klienta SIMM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa odblokowuje klienta THEM2M, który został wcześniej zablokowany przez wywołanie ***nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Parametry

- **client_ptr** Wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** Operacja powiodła się.
- **NX_PTR_ERROR** Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```