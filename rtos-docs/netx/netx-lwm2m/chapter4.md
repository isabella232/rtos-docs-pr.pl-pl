---
title: Rozdział 4 — Opis usług Azure RTO NetX LWM2M Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX LWM2M Services (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822578"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Rozdział 4 — Opis usług Azure RTO NetX LWM2M Services

Ten rozdział zawiera opis wszystkich usług Azure RTO NetX LWM2M Services (wymienionych poniżej) w porządku alfabetycznym.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

### <a name="lwm2m-client-management"></a>LWM2M zarządzanie klientami

- **nx_lwm2m_client_create**: *Utwórz klienta lwm2m*
- **nx_lwm2m_client_delete**: *Usuwanie klienta lwm2m*
- **nx_lwm2m_client_lock**: *Zablokuj klienta lwm2m*
- **nx_lwm2m_client_object_add**: *Dodawanie implementacji obiektu do klienta lwm2m*
- **nx_lwm2m_client_unlock**: *Odblokuj klienta lwm2m*

### <a name="lwm2m-client-session-management"></a>LWM2M zarządzanie sesją klienta

- **nx_lwm2m_client_session_bootstrap**: *Uruchamianie sesji z serwerem Bootstrap*
- **nx_lwm2m_client_session_bootstrap_dtls**: *Rozpoczynanie bezpiecznej sesji z serwerem Bootstrap*
- **nx_lwm2m_client_session_create**: *Utwórz sesję klienta lwm2m*
- **nx_lwm2m_client_session_delete**: *usuwanie sesji klienta lwm2m*
- **nx_lwm2m_client_session_deregister**: *przerywanie sesji z serwerem lwm2m*
- **nx_lwm2m_client_session_error_get**: *Pobierz ostatni błąd sesji*
- **nx_lwm2m_client_session_register**: *Uruchamianie sesji z serwerem lwm2m*
- **nx_lwm2m_client_session_register_dtls**: *Rozpoczynanie bezpiecznej sesji z serwerem lwm2m*
- **nx_lwm2m_client_session_update**: *Aktualizowanie sesji przy użyciu serwera lwm2m*

### <a name="security-object-implementation"></a>Implementacja obiektu zabezpieczeń

- **nx_lwm2m_client_security_key_callbacks_set**: *Ustaw wywołania zwrotne zarządzania kluczami zabezpieczeń*

### <a name="device-object-implementation"></a>Implementacja obiektu urządzenia

- **nx_lwm2m_client_device_callbacks_set**: *Ustaw wywołania zwrotne aplikacji obiektu urządzenia*
- **nx_lwm2m_client_device_error_push**: *Dodaj kod błędu do obiektu urządzenia*
- **nx_lwm2m_client_device_error_reset**: *Resetowanie kodów błędów obiektu urządzenia*
- **nx_lwm2m_client_device_resource_changed**: *zmiana sygnału zasobu obiektu urządzenia*

### <a name="custom-objects-implementation"></a>Implementacja obiektów niestandardowych

- **nx_lwm2m_object_resource_changed**: *zmiana sygnału dla wartości zasobu wystąpienia obiektu*

### <a name="local-device-management"></a>Zarządzanie urządzeniami lokalnymi

- **nx_lwm2m_client_object_create**: *Utwórz nowe wystąpienie obiektu*
- **nx_lwm2m_client_object_delete**: *usuwanie wystąpienia obiektu*
- **nx_lwm2m_client_object_discover**: *odnajdywanie zasobów wystąpienia obiektu*
- **nx_lwm2m_client_object_execute**: *wykonywanie zasobu wystąpienia obiektu*
- **nx_lwm2m_client_object_get_next**: *Pobieranie listy obiektów wdrożonych przez klienta lwm2m*
- **nx_lwm2m_client_object_instance_get_next**: *Pobieranie listy wystąpień obiektu*
- **nx_lwm2m_client_object_read**: *Odczytywanie wartości zasobów wystąpienia obiektu*
- **nx_lwm2m_client_object_write**: *zmiana wartości zasobów wystąpienia obiektu*

### <a name="resources-values-decoding"></a>Dekodowanie wartości zasobów

- **nx_lwm2m_resource_get_boolean**: *pobieranie wartości zasobu logicznego*
- **nx_lwm2m_resource_get_float32**: *pobieranie wartości 32-bitowego zasobu zmiennoprzecinkowego*
- **nx_lwm2m_resource_get_float64**: *pobieranie wartości 64-bitowego zasobu zmiennoprzecinkowego*
- **nx_lwm2m_resource_get_integer32**: *pobieranie wartości 32-bitowego zasobu liczb całkowitych*
- **nx_lwm2m_resource_get_integer64**: *pobieranie wartości 64-bitowego zasobu liczb całkowitych*
- **nx_lwm2m_resource_get_objlnk**: *pobieranie wartości zasobu linku do obiektu*
- **nx_lwm2m_resource_get_opaque**: *Pobierz wartość nieprzezroczystego zasobu*
- **nx_lwm2m_resource_get_string**: *pobieranie wartości zasobu ciągu*
- **nx_lwm2m_resource_multiple_get_boolean**: *Pobierz wartość zasobu logicznego z wieloma wystąpieniami zasobów*
- **nx_lwm2m_resource_multiple_get_float32**: *pobieranie wartości 32-bitowej liczby zmiennoprzecinkowej wielu wystąpień zasobów*
- **nx_lwm2m_resource_multiple_get_float64**: *pobieranie wartości 64-bitowej liczby zmiennoprzecinkowej wielu wystąpień zasobów*
- **nx_lwm2m_resource_multiple_get_integer32**: *Pobierz wartość 32-bitowej liczby całkowitej wiele wystąpień zasobów*
- **nx_lwm2m_resource_multiple_get_integer64**: *Pobierz wartość 64-bitowej liczby całkowitej wiele wystąpień zasobów*
- **nx_lwm2m_resource_multiple_get_objlnk**: *pobieranie wartości linku do obiektu z wieloma wystąpieniami zasobów*
- **nx_lwm2m_resource_multiple_get_opaque**: *Pobierz wartość nieprzezroczystego wystąpienia wielu zasobów*
- **nx_lwm2m_resource_multiple_get_string**: *Pobierz wartość ciągu z wieloma wystąpieniami zasobów*

### <a name="firmware-update-object"></a>Obiekt aktualizacji oprogramowania układowego

- **nx_lwm2m_firmware_create**: *Tworzenie obiektu aktualizacji oprogramowania układowego*
- **nx_lwm2m_firmware_package_info_set**: *Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego*
- **nx_lwm2m_firmware_result_set**: *Ustaw wynik aktualizacji oprogramowania układowego*
- **nx_lwm2m_firmware_state_set**: *Ustaw stan aktualizacji oprogramowania układowego*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Utwórz klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta LWM2M, które działa w kontekście jego własnego wątku ThreadX.

Klient LWM2M implementuje następujące obiekty OMA LWM2M: Security (0), Server (1), Access Control (2) i Device (3). Inne implementacje obiektów muszą być dodane przez aplikację.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **ip_ptr**: wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_pool_ptr**: wskaźnik do domyślnej puli pakietów dla tego klienta LWM2M.
- **local_port**: lokalny port UDP używany do komunikacji niezabezpieczonej.
- **name_ptr**: wskaźnik do LWM2M nazwa punktu końcowego klienta.
- **msisdn_ptr**: wskaźnik do msisdn, w którym można skontaktować się z klientem LWM2M do użycia z POWIĄZANIEM programu SMS, może mieć wartość null, Jeśli powiązanie programu SMS nie jest obsługiwane.
- **binding_modes**: powiązanie i tryby obsługiwane przez klienta LWM2M muszą być kombinacją flag NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S i NX_LWM2M_BINDING_SQ.
- **stack_ptr**: wskaźnik do LWM2M obszaru stosu wątków klienta.
- **stack_size**: rozmiar stosu wątku klienta LWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: klient LWM2M został pomyślnie utworzony.
- **NX_LWM2M_ERROR**: Wystąpił błąd podczas tworzenia klienta LWM2M.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Usuwanie klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta LWM2M.

Wszystkie sesje, które są obecnie dołączone do klienta, są również usuwane przez to wywołanie.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: klient LWM2M został pomyślnie usunięty.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Ustawianie wywołania zwrotnego aplikacji obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Opis

Ta usługa instaluje wywołania zwrotne aplikacji w celu zaimplementowania operacji na zasobach obiektów urządzenia LWM2M, które nie są obsługiwane przez klienta LWM2M.

Klient LWM2M implementuje następujące zasoby: kod błędu (11), resetowanie kodu błędu (12) i obsługiwane powiązania i tryby (16), operacje innych zasobów są przekierowywane do aplikacji.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **read_callback**: wywołanie zwrotne metody "read".
- **discover_callback**: wywołanie zwrotne metody "Discovery".
- **write_callback**: wywołanie zwrotne metody "Write".
- **execute_callback**: wywołanie zwrotne metody "Execute".

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Dodawanie kodu błędu do obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Opis

Ta usługa dodaje nowe wystąpienie do zasobu kod błędu (11) urządzenia obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **kod**: nowy kod błędu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BUFFER_TOO_SMALL**: osiągnięto maksymalną liczbę przechowywanych kodów błędów.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Resetuj kody błędów obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie wystąpienia zasobów kodu błędu z obiektu urządzenia. Jest to równoznaczne z wykonaniem kodu błędu resetowania zasobu (12).

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Zmiana sygnału zasobu obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Opis

Usługa jest używana przez aplikację do sygnalizowania klienta LWM2M, że zasób urządzenia obiektu został zmieniony. Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **zasób**: wskaźnik do struktury opisującej zasób, który został zmieniony.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Zablokuj klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa blokuje klienta LWM2M, aby uniemożliwić concurent dostęp do obiektów LWM2M z serwerów lub z innego wątku aplikacji.

Jeśli klient LWM2M jest obecnie zablokowany przez inny wątek, funkcja zostanie Zablokowani do momentu odblokowania klienta LWM2M.

Wywołania nx_lwm2m_client_lock ()/nx_lwm2m_client_unlock () mogą być zagnieżdżane.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Dodawanie implementacji obiektu do klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje nową implementację obiektu do klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_ptr**: wskaźnik do struktury definiującej implementację obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_ALREADY_EXIST**: identyfikator obiektu już istnieje.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Utwórz nowe wystąpienie obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Create" na obiekcie klienta LWM2M, aby utworzyć nowe wystąpienie obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_id_ptr**: wskaźnik do identyfikatora nowego wystąpienia może mieć wartość null, jeśli klient LWM2M musi przypisać identyfikator wystąpienia. Jeśli identyfikator jest wartością zarezerwowaną 65535, klient LWM2M przypisze identyfikator wystąpienia. Jeśli wartość nie jest równa NULL, przypisany identyfikator jest zwracany po wywołaniu.
- **num_values**: liczba wartości do ustawienia.
- **values_ptr**: wskaźnik do tablicy wartości zasobów, aby zainicjować nowe wystąpienie obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_ALREADY_EXIST**: identyfikator wystąpienia obiektu już istnieje.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: obiekt nie obsługuje tworzenia wystąpień.
- **NX_LWM2M_NO_MEMORY**: nie można przydzielić pamięci do zapisania nowego wystąpienia.
- **NX_LWM2M_NOT_FOUND**: identyfikator obiektu nie istnieje.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Usuwanie wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Delete" na wystąpieniu obiektu klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_ID**: identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: obiekt nie obsługuje usuwania wystąpienia.
- **NX_LWM2M_NOT_FOUND**: identyfikator obiektu lub identyfikatora wystąpienia obiektu nie istnieje.
- NX_PTR_ERROR nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Odnajdywanie zasobów wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Discover" na wystąpieniu obiektu klienta LWM2M, która zwraca listę zasobów implementowanych przez obiekt.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_ID**: identyfikator wystąpienia obiektu.
- **num_resources_ptr**: przy wprowadzaniu rozmiaru buforu docelowego w danych wyjściowych liczba elementów WRITEN do buforu.
- **resources_ptr**: wskaźnik do bufora docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się..
- **NX_LWM2M_BUFFER_TOO_SMALL**: bufor zasobów jest za mały, aby można było przechowywać listę zasobów.
- **NX_LWM2M_NOT_FOUND**: identyfikator obiektu lub identyfikatora wystąpienia obiektu nie istnieje.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Wykonaj zasób wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Execute" na zasobie wystąpienia obiektu klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_ID**: identyfikator wystąpienia obiektu.
- **resource_id**: Identyfikator zasobu.
- **arguments_ptr**: wskaźnik do argumentów operacji Execute. Może mieć wartość NULL, jeśli arguments_length wynosi zero.
- **arguments_length**: długość argumentów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: zasób nie obsługuje operacji Execute.
- **NX_LWM2M_NOT_FOUND**: identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Pobierz listę obiektów wdrożonych przez klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego obiektu implementowanego przez klienta LWM2M. Jeśli bieżący identyfikator obiektu jest ustawiony na NX_LWM2M_RESERVED_ID (65535), zwracany jest pierwszy identyfikator obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id_ptr**: wskaźnik do bieżącego identyfikatora obiektu. On return zawiera następny identyfikator obiektu zaimplementowany przez klienta LWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się..
- **NX_LWM2M_NOT_FOUND**: dany identyfikator obiektu jest ostatnim z baz danych.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Pobierz listę wystąpień obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego wystąpienia obiektu danego obiektu. Jeśli bieżący identyfikator wystąpienia ma wartość NX_LWM2M_RESERVED_ID (65535) zwracany jest identyfikator pierwszego wystąpienia.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_id_ptr**: wskaźnik do bieżącego identyfikatora wystąpienia obiektu. On return zawiera identyfikator następnego wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się..
- **NX_LWM2M_NOT_FOUND**: dany identyfikator wystąpienia jest ostatnim obiektem lub identyfikator obiektu nie jest zaimplementowany.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Odczytaj wartości zasobów wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "read" na wystąpieniu obiektu klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_ID**: identyfikator wystąpienia obiektu.
- **num_values**: liczba zasobów do odczytania.
- **values_ptr**: wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: zasób nie obsługuje operacji odczytu.
- **NX_LWM2M_NOT_FOUND**: identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Zmiana wartości zasobów wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Write" na wystąpieniu obiektu klienta LWM2M.

Do *write_op* parametru można określić następujące operacje zapisu:

- **0** &mdash; aktualizacja częściowa: dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Zamień wystąpienie: zamienia wystąpienie obiektu na nowe podane wartości zasobów.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Zastąp zasób: zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Zapis ładowania początkowego: wskazuje wywołanie z sekwencji ładowania początkowego.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **object_id**: identyfikator obiektu.
- **instance_ID**: identyfikator wystąpienia obiektu.
- **num_values**: liczba zasobów do zapisania.
- **values_ptr**: wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów, typy i wartości do zapisania.
- **write_op**: typ operacji zapisu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: typ zasobu jest nieprawidłowy.
- **NX_LWM2M_BUFFER_TOO_SMALL**: długość wartości jest zbyt duża, aby można było ją zapisać w wystąpieniu.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: zasób nie obsługuje operacji zapisu.
- **NX_LWM2M_NO_MEMORY**: nie można przydzielić pamięci do przechowywania wartości zasobu.
- **NX_LWM2M_NOT_ACCEPTABLE**: wartość zasobu jest nieprawidłowa.
- **NX_LWM2M_NOT_FOUND**: identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- NX_OPTION_ERROR: nieprawidłowy typ operacji zapisu.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Ustaw wywołania zwrotne zarządzania kluczami obiektów zabezpieczeń

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Opis

Ta usługa instaluje wywołania zwrotne aplikacji w celu zaimplementowania operacji na zasobach obiektów zabezpieczeń LWM2M związanych z kluczami zabezpieczeń.

Klient LWM2M deleguje zarządzanie kluczami zabezpieczeń do aplikacji podczas sesji Bootstrap, wywołania zwrotne będą wywoływane, gdy serwer Bootstrap zapisze lub usunie następujące zasoby w wystąpieniu obiektu zabezpieczeń: klucz publiczny lub tożsamość (3), klucz publiczny serwera (4), klucz tajny (5).

Aplikacja jest odpowiedzialna za przechowywanie danych kluczy i na potrzeby konfigurowania sesji DTLS używanych przez klienta LWM2M.

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.
- **write_callback**: wywołanie zwrotne metody klucza "Write".
- **delete_callback**: wywołanie zwrotne metody klucza "Delete".

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Uruchamianie sesji z serwerem Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję z serwerem Bootstrap. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.
- **security_id**: identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na NX_LWM2M_RESERVED_ID (65535), jeśli serwer Bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.
- **IP_address**: adres IP serwera.
- **port**: port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_NOT_FOUND**: nie ma wystąpienia obiektu zabezpieczeń ODPOWIADAJĄCego identyfikatorowi wystąpienia zabezpieczeń.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Uruchom bezpieczną sesję z serwerem Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję z serwerem Bootstrap przy użyciu bezpiecznego połączenia DTLS. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza. Należy zdefiniować NX_SECURE_ENABLE_DTLS.

Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.
- **security_id**: identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na NX_LWM2M_RESERVED_ID (65535), jeśli serwer Bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.
- **IP_address**: adres IP serwera.
- **port**: port UDP serwera.
- **dtls_session_ptr**: sesja DTLS do użycia w sesji Bootstrap.
- **dtls_local_port**: lokalny port UDP używany do sesji DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_NOT_FOUND**: nie ma wystąpienia obiektu zabezpieczeń ODPOWIADAJĄCego identyfikatorowi wystąpienia zabezpieczeń.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Utwórz sesję klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Opis

Ta usługa tworzy nową sesję klienta LWM2M dołączoną do istniejącego klienta LWM2M. Sesja jest używana przez klienta LWM2M do komunikacji z serwerem Bootstrap lub serwerem LWM2M.

Aplikacja musi udostępniać funkcję wywołania zwrotnego, która będzie wywoływana, gdy stan sesji zostanie zaktualizowany.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.
- **client_ptr**: wskaźnik do wcześniej utworzonego klienta LWM2M.
- **state_callback**: wywołanie zwrotne aplikacji wywoływane w przypadku zmiany stanu sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Usuń sesję klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa sesję klienta LWM2M.

Po usunięciu klienta LWM2M przez wywołanie nx_lwm2m_client_delete wszystkie sesje dołączone do klienta również zostaną usunięte.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Przerywanie sesji z serwerem LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Wyrejestrowanie" na serwerze LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_NOT_REGISTERED**: klient nie jest zarejestrowany na serwerze.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Pobierz ostatni błąd sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca kod błędu sesji, gdy sesja jest w stanie błędu.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: sesja nie jest w stanie błędu.
- **NX_LWM2M_ADDRESS_ERROR**: nieprawidłowy adres serwera.
- **NX_LWM2M_BUFFER_TOO_SMALL**: ładunek żądania nie mieści się w buforze sieciowym.
- **NX_LWM2M_DTLS_ERROR**: nie można ustanowić bezpiecznego połączenia z serwerem.
- **NX_LWM2M_ERROR**: nieokreślony błąd.
- **NX_LWM2M_FORBIDDEN**: Rejestracja została odrzucona przez serwer.
- **NX_LWM2M_NOT_FOUND**: nie znaleziono klienta przez serwer podczas aktualizowania/wyrejestrowywania.
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: wystąpienie obiektu serwera odpowiadające sesji zostało usunięte.
- **NX_LWM2M_TIMED_OUT**: Brak odpowiedzi z serwera.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Uruchamianie sesji z serwerem LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Register" na serwerze LWM2M. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.

Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.
- **server_id**: Krótki identyfikator serwera serwera LWM2M.
- **IP_address**: adres IP serwera.
- **port**: port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się..
- **NX_LWM2M_NOT_FOUND**: nie istnieje wystąpienie obiektu serwera odpowiadające KRÓTKIemu identyfikatorowi serwera.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Uruchamianie bezpiecznej sesji z serwerem LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Register" na serwerze LWM2M przy użyciu bezpiecznego połączenia usługi DTLS. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.

Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza. Należy zdefiniować NX_SECURE_ENABLE_DTLS.

Każda sesja DTLS używa własnego gniazda UDP do komunikacji, dlatego dtls_local_port portów lokalnych musi być inna dla każdej sesji, jeśli aplikacja tworzy kilka bezpiecznych sesji.

Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.
- **server_id**: Krótki identyfikator serwera serwera LWM2M.
- **IP_address**: adres IP serwera.
- **port**: port UDP serwera.
- **dtls_session_ptr**: sesja DTLS używana na potrzeby sesji LWM2M.
- **dtls_local_port**: lokalny port UDP używany do sesji DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_NOT_FOUND**: nie istnieje wystąpienie obiektu serwera odpowiadające KRÓTKIemu identyfikatorowi serwera.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Aktualizowanie sesji przy użyciu serwera LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Update" na serwerze LWM2M.

### <a name="parameters"></a>Parametry

- **session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_NOT_REGISTERED**: klient nie jest zarejestrowany na serwerze.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Odblokuj klienta LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa odblokowuje klienta LWM2M previoulsy zablokowany przez wywołanie do nx_lwm2m_client_unlock ().

### <a name="parameters"></a>Parametry

- **client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Utwórz obiekt aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Opis

Ta usługa inicjuje obiekt aktualizacji oprogramowania układowego i dodaje obiekt do wcześniej utworzonego klienta LWM2M. Obiekt aktualizacji oprogramowania układowego implementuje zasoby do komunikacji z serwerem LWM2M, ale aplikacja musi zapewnić wywołania zwrotne w celu zaimplementowania rzeczywistych operacji na oprogramowaniu układowym (dowloading, przechowywanie i aktualizowanie oprogramowania układowego).

Parametr Protocols wskazuje, które protokoły są obsługiwane przez aplikację do pobierania oprogramowania układowego z zasobem "identyfikator URI pakietu" zdefiniowane są następujące flagi:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Parametry

- **firmware_ptr**: wskaźnik do bloku kontroli obiektów oprogramowania układowego.
- **client_ptr**: wskaźnik do Previsously utworzonego klienta LWM2M.
- **Protokoły**: flagi wskazujące, które protokoły są obsługiwane przez zasób URI pakietu.
- **package_callback**: musi mieć wartość null [TBD].
- **package_uri_callback**: wywołanie zwrotne używane do implementowania zasobu URI pakietu.
- **update_callback**: wywołanie zwrotne używane do implementowania zasobu aktualizacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Opis

Ta usługa zmienia wartości "PkgName" (6) i "PkgVersion" (7) zasobów obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr**: wskaźnik do obiektu aktualizacji oprogramowania układowego.
- **Nazwa**: Nowa wartość nazwy pakietu.
- **wersja**: Nowa wartość wersji pakietu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Ustaw wynik aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Opis

Ta usługa zmienia wartość zasobu "Update Result" (5) dla obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr**: wskaźnik do obiektu aktualizacji oprogramowania układowego.
- **wynik**: Nowa wartość zasobu wynik aktualizacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Ustaw stan aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Opis

Ta usługa zmienia wartość zasobu "State" (3) obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr**: wskaźnik do obiektu aktualizacji oprogramowania układowego.
- **stan**: Nowa wartość zasobu stanu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Zmiana sygnału dla wartości zasobu wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Opis

Ta usługa jest używana przez implementację obiektu do sygnalizowania klienta LWM2M, że jedna z jego wartości zasobów została zmieniona. Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.

### <a name="parameters"></a>Parametry

- **object_ptr**: wskaźnik do implementacji obiektu.
- **instance_ptr**: wskaźnik do wystąpienia obiektu.
- **zasób**: wskaźnik do struktury opisującej zasób, który został zmieniony.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- NX_PTR_ERROR: nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Pobieranie wartości zasobu logicznego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość zasobu logicznego.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **bool_ptr**: wskaźnik do docelowej wartości logicznej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością logiczną.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Pobierz wartość 32-bitowego zasobu zmiennoprzecinkowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 32-bitowego zasobu zmiennoprzecinkowego.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **float32_ptr**: wskaźnik do docelowej 32-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Pobierz wartość 64-bitowego zasobu zmiennoprzecinkowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 64-bitowego zasobu zmiennoprzecinkowego.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **float64_ptr**: wskaźnik do docelowej 64-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Pobierz wartość 32-bitowego zasobu liczb całkowitych

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 32-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **int32_ptr**: wskaźnik do wartości docelowej 32-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością całkowitą lub wartość całkowita nie mieści się w 32-bitowej liczbie.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Pobierz wartość 64-bitowego zasobu liczb całkowitych

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 64-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **int64_ptr**: wskaźnik do wartości docelowej 64-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością całkowitą.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Pobieranie wartości zasobu linku do obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość zasobu linku do obiektu.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **objlnk_ptr**: wskaźnik do wartości linku do obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością linku obiektu.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Pobierz wartość nieprzezroczystego zasobu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość nieprzezroczystego zasobu.

Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **opaque_ptr_ptr**: wskaźnik do docelowego wskaźnika bufora nieprzezroczystości.
- **opaque_length_ptr**: wskaźnik do docelowej długości buforu nieprzezroczystości.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością nieprzezroczystą.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Pobierz wartość zasobu ciągu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość zasobu ciągu.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości zasobu.
- **string_ptr_ptr**: wskaźnik do wskaźnika ciągu docelowego.
- **string_length_ptr**: wskaźnik do docelowej długości ciągu. Może mieć wartość NULL, jeśli ciąg jest zakończony znakiem null.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością ciągu.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Pobierz wartość zasobu logicznego z wieloma wystąpieniami zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość wystąpienia zasobu logicznego z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **bool_ptr**: wskaźnik do docelowej wartości logicznej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub nie jest wartością logiczną.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Pobierz wartość 32-bitowego wystąpienia wielu zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 32-bitowego wystąpienia zasobu zmiennoprzecinkowego z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **float32_ptr**: wskaźnik do docelowej 32-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Pobierz wartość 64-bitowego wystąpienia wielu zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 64-bitowego wystąpienia zasobu zmiennoprzecinkowego z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **float64_ptr**: wskaźnik do docelowej 64-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Pobierz wartość 32-bitowej liczby całkowitej wiele wystąpień zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 32-bitowej liczby całkowitej wystąpienia zasobu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **int32_ptr**: wskaźnik do wartości docelowej 32-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością całkowitą lub wartość całkowita nie mieści się w 32-bitowej liczbie.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Pobierz wartość 64-bitowej liczby całkowitej wiele wystąpień zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość 64-bitowej liczby całkowitej wystąpienia zasobu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **int64_ptr**: wskaźnik do wartości docelowej 64-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością całkowitą.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Pobieranie wartości linku do obiektu z wieloma wystąpieniami zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość wystąpienia zasobu linku do obiektu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **objlnk_ptr**: wskaźnik do wartości linku do obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością linku obiektu.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Pobierz wartość nieprzezroczystego wystąpienia wielu zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość nieprzezroczystego wystąpienia zasobu z wielu zasobów.

Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **opaque_ptr_ptr**: wskaźnik do docelowego wskaźnika bufora nieprzezroczystości.
- **opaque_length_ptr**: wskaźnik do docelowej długości buforu nieprzezroczystości.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością nieprzezroczystą.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Pobierz wartość ciągu z wieloma wystąpieniami zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Opis

Usługa Pobiera wartość wystąpienia zasobu ciągu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **wartość**: wskaźnik do opisu wartości wielu zasobów.
- **index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.
- **instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.
- **string_ptr_ptr**: wskaźnik do wskaźnika ciągu docelowego.
- **string_length_ptr**: wskaźnik do docelowej długości ciągu. Może mieć wartość NULL, jeśli ciąg jest zakończony znakiem null.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: operacja powiodła się.
- **NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub wartość wystąpienia nie jest wartością ciągu.
