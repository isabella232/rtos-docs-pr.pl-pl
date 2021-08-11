---
title: Rozdział 4 — Opis Azure RTOS NetX CELUM2M
description: Ten rozdział zawiera opis wszystkich usług NetX AZURE RTOS (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 171f8577d252027548c24ec92f11f03c1fae768f1676f476256c13b8e8dc4175
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799085"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Rozdział 4 — Opis Azure RTOS NetX CELUM2M

Ten rozdział zawiera opis wszystkich usług NetX AZURE RTOS (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

### <a name="lwm2m-client-management"></a>ZARZĄDZANIE KLIENTEM ZAM2M

- **nx_lwm2m_client_create:** Tworzenie *klienta SYSTEMU DOM2M*
- **nx_lwm2m_client_delete:** Usuwanie *klienta KOMPUTERA 2M*
- **nx_lwm2m_client_lock:** *Zablokuj klienta SYSTEMU PLIKÓW 2M*
- **nx_lwm2m_client_object_add:** Dodawanie *implementacji obiektu do klienta PROJEKTUM2M*
- **nx_lwm2m_client_unlock:** *Odblokowywanie klienta SIMM2M*

### <a name="lwm2m-client-session-management"></a>ZARZĄDZANIE SESJAMI KLIENTA ZAM2M

- **nx_lwm2m_client_session_bootstrap:** *rozpoczynanie sesji z serwerem Bootstrap*
- **nx_lwm2m_client_session_bootstrap_dtls:** Uruchamianie *bezpiecznej sesji z serwerem Bootstrap*
- **nx_lwm2m_client_session_create:** Tworzenie *sesji klienta KOMPUTERA 2M*
- **nx_lwm2m_client_session_delete:** *Usuwanie sesji klienta KOMPUTERA 2M*
- **nx_lwm2m_client_session_deregister:** Zakończenie *sesji z serwerem DNS2M*
- **nx_lwm2m_client_session_error_get:** Uzyskiwanie *ostatniego błędu sesji*
- **nx_lwm2m_client_session_register:** *rozpoczynanie sesji z serwerem SEAM2M*
- **nx_lwm2m_client_session_register_dtls:** Uruchom *bezpieczną sesję z serwerem SEAM2M*
- **nx_lwm2m_client_session_update:** aktualizowanie *sesji za pomocą serwera SEAM2M*

### <a name="security-object-implementation"></a>Implementacja obiektu zabezpieczeń

- **nx_lwm2m_client_security_key_callbacks_set:** Ustawianie *wywołań zwrotnych zarządzania kluczami zabezpieczeń*

### <a name="device-object-implementation"></a>Implementacja obiektu urządzenia

- **nx_lwm2m_client_device_callbacks_set:** ustawianie *wywołań zwrotnych aplikacji* obiektu urządzenia
- **nx_lwm2m_client_device_error_push:** Dodawanie *kodu błędu do obiektu urządzenia*
- **nx_lwm2m_client_device_error_reset:** *Resetowanie kodów błędów obiektu urządzenia*
- **nx_lwm2m_client_device_resource_changed:** *Zasygnalizuj zmianę zasobu obiektu urządzenia*

### <a name="custom-objects-implementation"></a>Implementacja obiektów niestandardowych

- **nx_lwm2m_object_resource_changed:** *zasygnalizuj zmianę wartości zasobu wystąpienia obiektu*

### <a name="local-device-management"></a>Lokalne Zarządzanie urządzeniami

- **nx_lwm2m_client_object_create:** tworzenie *nowego wystąpienia obiektu*
- **nx_lwm2m_client_object_delete:** *usuwanie wystąpienia obiektu*
- **nx_lwm2m_client_object_discover:** *odnajdywanie zasobów wystąpienia obiektu*
- **nx_lwm2m_client_object_execute:** Wykonywanie *zasobu wystąpienia obiektu*
- **nx_lwm2m_client_object_get_next:** pobierz *listę obiektów zaimplementowanych przez klienta SYSTEMU THEM2M*
- **nx_lwm2m_client_object_instance_get_next:** pobierz *listę wystąpień obiektu*
- **nx_lwm2m_client_object_read:** *odczytywanie wartości zasobów wystąpienia obiektu*
- **nx_lwm2m_client_object_write:** zmienianie *wartości zasobów wystąpienia obiektu*

### <a name="resources-values-decoding"></a>Dekodowanie wartości zasobów

- **nx_lwm2m_resource_get_boolean:** *uzyskiwanie wartości zasobu logicznych*
- **nx_lwm2m_resource_get_float32:** pobierz *wartość 32-bitowego zasobu zmiennoprzecinkowego*
- **nx_lwm2m_resource_get_float64:** *pobierz wartość 64-bitowego zasobu zmiennoprzecinkowego*
- **nx_lwm2m_resource_get_integer32:** pobierz *wartość 32-bitowego zasobu liczby całkowitej*
- **nx_lwm2m_resource_get_integer64:** pobierz *wartość 64-bitowego zasobu liczby całkowitej*
- **nx_lwm2m_resource_get_objlnk:** uzyskiwanie *wartości zasobu linku obiektu*
- **nx_lwm2m_resource_get_opaque:** Uzyskiwanie *wartości nieprzezroczystego zasobu*
- **nx_lwm2m_resource_get_string:** uzyskiwanie *wartości zasobu ciągu*
- **nx_lwm2m_resource_multiple_get_boolean:** uzyskiwanie wartości wystąpienia zasobu logicznych z *wieloma zasobami*
- **nx_lwm2m_resource_multiple_get_float32:** pobierz *wartość 32-bitowego* wystąpienia wielu zasobów zmiennoprzecinkowych
- **nx_lwm2m_resource_multiple_get_float64:** pobierz *wartość 64-bitowego* wystąpienia wielu zasobów zmiennoprzecinkowych
- **nx_lwm2m_resource_multiple_get_integer32:** *uzyskiwanie wartości 32-bitowej liczby całkowitej z wieloma wystąpieniami zasobów*
- **nx_lwm2m_resource_multiple_get_integer64:** *pobierz wartość 64-bitowej liczby całkowitej z wieloma wystąpieniami zasobów*
- **nx_lwm2m_resource_multiple_get_objlnk:** uzyskiwanie wartości wystąpienia wielu zasobów *linku obiektu*
- **nx_lwm2m_resource_multiple_get_opaque:** uzyskiwanie *wartości nieprzezroczystego wystąpienia wielu zasobów*
- **nx_lwm2m_resource_multiple_get_string:** uzyskiwanie *wartości wystąpienia wielu* zasobów ciągu

### <a name="firmware-update-object"></a>Obiekt aktualizacji oprogramowania układowego

- **nx_lwm2m_firmware_create:** Tworzenie *obiektu aktualizacji oprogramowania układowego*
- **nx_lwm2m_firmware_package_info_set:** Ustawianie *informacji o pakiecie aktualizacji oprogramowania układowego*
- **nx_lwm2m_firmware_result_set:** ustaw *wynik aktualizacji oprogramowania układowego*
- **nx_lwm2m_firmware_state_set:** ustaw *stan aktualizacji oprogramowania układowego*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Tworzenie klienta SYSTEMU DOM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta KOMPUTERA 2M, które jest uruchamiane w kontekście własnego wątku ThreadX.

Klient SYSTEMM2M implementuje następujące obiekty OMA ZESM2M: Security (0), Server (1), Access Control (2) i Device (3). Inne implementacje obiektów muszą zostać dodane przez aplikację.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **ip_ptr:** wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_pool_ptr:** wskaźnik do domyślnej puli pakietów dla tego klienta KOMPUTERA 2M.
- **local_port:** lokalny port UDP używany do niezabezpieczanej komunikacji.
- **name_ptr:** Wskaźnik do nazwy punktu końcowego klienta KOMPUTERA 2M.
- **msisdn_ptr:** wskaźnik do sieci MSISDN, w której można uzyskać dostęp do klienta KOMPUTERA 2M w celu użycia z powiązaniem SMS, może mieć wartość NULL, jeśli powiązanie SMS nie jest obsługiwane.
- **binding_modes:** Powiązanie i tryby obsługiwane przez klienta KOMPUTERA 2M muszą być kombinacją flag NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S i NX_LWM2M_BINDING_SQ flagi.
- **stack_ptr:** wskaźnik do obszaru stosu wątku klienta STOSUM2M.
- **stack_size:** rozmiar stosu wątku klienta STOSUM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślnie utworzono klienta SYSTEMU DOM2M.
- **NX_LWM2M_ERROR:** błąd tworzenia klienta PRZEZAD2M.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Usuwanie klienta SYSTEMU GDYTM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta KOMPUTERA 2M.

Wszystkie aktualnie dołączone sesje klienta są również usuwane przez to wywołanie.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślnie usunięto klienta SYSTEMU THEM2M.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Ustawianie wywołań zwrotnych aplikacji obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Opis

Ta usługa instaluje wywołania zwrotne aplikacji w celu implementacji operacji na zasobach obiektu urządzeniaFERM2M, które nie są obsługiwane przez klienta DSM2M.

Klient RESETM2M implementuje następujące zasoby: kod błędu (11), kod błędu resetowania (12) i obsługiwane powiązania i tryby (16), operacje do innych zasobów są przekierowywani do aplikacji.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **read_callback:** wywołanie zwrotne metody "Read".
- **discover_callback:** wywołanie zwrotne metody "Discover".
- **write_callback:** wywołanie zwrotne metody "Write".
- **execute_callback:** wywołanie zwrotne metody "Execute".

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Dodawanie kodu błędu do obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Opis

Ta usługa dodaje nowe wystąpienie do zasobu kod błędu (11) urządzenia obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **code:** nowy kod błędu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BUFFER_TOO_SMALL:** osiągnięto maksymalną liczbę przechowywanych kodów błędów.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Kody błędów resetowania obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie wystąpienia zasobów kodu błędu z obiektu urządzenia. Jest to równoważne wykonaniu kodu błędu resetowania zasobu (12).

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Zmiana sygnału zasobu obiektu urządzenia

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Opis

Usługa ta jest używana przez aplikację do sygnalizowania klientowi KOMPUTERA --2M, że zasób urządzenia obiektowego uległ zmianie. Jeśli zasób zostanie zaobserwowany przez serwer DHCPM2M, klient NIEM2M wyśle powiadomienie.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **resource**: wskaźnik do struktury opisującej zmieniony zasób.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Zablokuj klienta PROGRAMULUSM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa blokuje klienta PROGRAMU THEM2M, aby uniemożliwić współbieżny dostęp do obiektów THEM2M z serwerów lub innego wątku aplikacji.

Jeśli klient THEM2M jest obecnie zablokowany przez inny wątek, funkcja będzie blokowana do momentu odblokowania klienta THEM2M.

Wywołania nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() mogą być zagnieżdżone.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Dodawanie implementacji obiektu do klienta PROJEKTUM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje nową implementację obiektu do klienta PROJEKTUM2M.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_ptr:** Wskaźnik do struktury definiującej implementację obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_ALREADY_EXIST:** Identyfikator obiektu już istnieje.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Tworzenie nowego wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Utwórz" na obiekcie klienta SYSTEMM2M w celu utworzenia nowego wystąpienia obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id_ptr:** wskaźnik do identyfikatora nowego wystąpienia, może mieć wartość NULL, jeśli klient JESTM2M musi przypisać identyfikator wystąpienia. Jeśli identyfikator jest wartością zarezerwowaną 65535, klient PROJEKTUM2M przypisze identyfikator wystąpienia. Jeśli nie ma wartości NULL, przypisany identyfikator jest zwracany po wywołaniu.
- **num_values:** liczba wartości do ustawienia.
- **values_ptr:** wskaźnik do tablicy wartości zasobów w celu zainicjowania nowego wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_ALREADY_EXIST:** Identyfikator wystąpienia obiektu już istnieje.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Obiekt nie obsługuje tworzenia wystąpienia.
- **NX_LWM2M_NO_MEMORY:** Nie można przydzielić pamięci do przechowywania nowego wystąpienia.
- **NX_LWM2M_NOT_FOUND:** Identyfikator obiektu nie istnieje.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Usuwanie wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Usuń" na wystąpieniu obiektu klienta KOMPUTERA 2M.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id:** identyfikator wystąpienia obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Obiekt nie obsługuje usuwania wystąpienia.
- **NX_LWM2M_NOT_FOUND:** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
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

Ta usługa wykonuje operację "Odnajdywanie" na wystąpieniu obiektu klienta KOMPUTERA 2M, co zwraca listę zasobów zaimplementowanych przez obiekt .

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id:** identyfikator wystąpienia obiektu.
- **num_resources_ptr:** po wejściu rozmiaru buforu docelowego, w danych wyjściowych liczba elementów zapisywanych w buforze.
- **resources_ptr:** wskaźnik do buforu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Operacja powiodła się.
- **NX_LWM2M_BUFFER_TOO_SMALL:** bufor zasobów jest zbyt mały, aby można było przechowywać listę zasobów.
- **NX_LWM2M_NOT_FOUND:** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Wykonywanie zasobu wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Execute" na zasobie wystąpienia obiektu klienta KOMPUTERA 2M.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id:** identyfikator wystąpienia obiektu.
- **resource_id:** identyfikator zasobu.
- **arguments_ptr:** wskaźnik do argumentów operacji wykonywania. Może mieć wartość NULL, arguments_length wartość zero.
- **arguments_length:** długość argumentów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** zasób nie obsługuje operacji wykonywania.
- **NX_LWM2M_NOT_FOUND:** identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Pobierz listę obiektów zaimplementowanych przez klienta KOMPUTERA 2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego obiektu zaimplementowanego przez klienta KOMPUTERA 2M. Jeśli bieżący identyfikator obiektu jest ustawiony na wartość NX_LWM2M_RESERVED_ID (65535), zwracany jest pierwszy identyfikator obiektu.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id_ptr:** wskaźnik do bieżącego identyfikatora obiektu. W przypadku zwracania zawiera następny identyfikator obiektu zaimplementowany przez klienta SIECI 2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Operacja powiodła się.
- **NX_LWM2M_NOT_FOUND:** podany identyfikator obiektu jest ostatnim z bazy danych.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Uzyskiwanie listy wystąpień obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca identyfikator następnego wystąpienia obiektu danego obiektu. Jeśli bieżący identyfikator wystąpienia jest ustawiony na NX_LWM2M_RESERVED_ID (65535), jest zwracany identyfikator pierwszego wystąpienia.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id_ptr:** wskaźnik do bieżącego identyfikatora wystąpienia obiektu. W przypadku zwracania zawiera następny identyfikator wystąpienia obiektu .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Operacja powiodła się.
- **NX_LWM2M_NOT_FOUND:** podany identyfikator wystąpienia jest ostatnim obiektem lub identyfikator obiektu nie jest zaimplementowany.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Odczytywanie wartości zasobów wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Odczyt" na wystąpieniu obiektu klienta KOMPUTERA 2M.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id:** identyfikator wystąpienia obiektu.
- **num_values:** liczba zasobów do odczytania.
- **values_ptr:** wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Zasób nie obsługuje operacji odczytu.
- **NX_LWM2M_NOT_FOUND:** identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Zmienianie wartości zasobów wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Zapis" na wystąpieniu obiektu klienta KOMPUTERA 2M.

Następujące operacje zapisu można określić  dla write_op parametru:

- **0** Częściowa aktualizacja: dodaje lub aktualizuje zasoby podane w nowej wartości i &mdash; pozostawia inne istniejące zasoby bez zmian.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Zastąp wystąpienie: zastępuje wystąpienie obiektu nowymi dostarczonymi wartościami zasobów.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Zastąp zasób: zastępuje zasoby nowymi wartościami zasobów (używanymi do zastępowania wielu zasobów).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Zapis ładowania początkowego: wskazuje wywołanie z sekwencji bootstrap.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **object_id:** identyfikator obiektu.
- **instance_id:** identyfikator wystąpienia obiektu.
- **num_values:** liczba zasobów do zapisu.
- **values_ptr:** wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów, typy i wartości do zapisu.
- **write_op:** typ operacji zapisu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** typ zasobu jest nieprawidłowy.
- **NX_LWM2M_BUFFER_TOO_SMALL:** długość wartości jest zbyt duża, aby można było jej przechowywać w wystąpieniu.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** zasób nie obsługuje operacji zapisu.
- **NX_LWM2M_NO_MEMORY:** Nie można przydzielić pamięci do przechowywania wartości zasobu.
- **NX_LWM2M_NOT_ACCEPTABLE:** wartość zasobu jest nieprawidłowy.
- **NX_LWM2M_NOT_FOUND:** identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.
- NX_OPTION_ERROR: Nieprawidłowy typ operacji zapisu.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Ustawianie wywołań zwrotnych zarządzania kluczami obiektu zabezpieczeń

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Opis

Ta usługa instaluje wywołania zwrotne aplikacji w celu implementacji operacji na zasobach obiektu zabezpieczeń SYSTEMU THEM2M powiązanych z kluczami zabezpieczeń.

Klient THEM2M deleguje zarządzanie kluczami zabezpieczeń do aplikacji podczas sesji bootstrap. Wywołania zwrotne będą wywoływane, gdy serwer Bootstrap zapisze lub usunie następujące zasoby w wystąpieniu obiektu zabezpieczeń: klucz publiczny lub tożsamość (3), klucz publiczny serwera (4), klucz tajny (5).

Aplikacja jest odpowiedzialna za przechowywanie danych kluczy i konfigurowanie sesji DTLS używanych przez klienta KOMPUTERA 2M.

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta PRZEPŁYWM2M.
- **write_callback:** wywołanie zwrotne metody klucza "Write".
- **delete_callback:** wywołanie zwrotne metody klucza "Delete".

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Rozpoczynanie sesji z serwerem Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Opis

Ta usługa rozpoczyna sesję z serwerem bootstrap. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Jeśli zasób "Hold Off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na uruchomienie zainicjowane przez serwer, jeśli po upływie tego czasu nie zostanie zainicjowane przez serwer uruchomienie, zostanie wykonana wartość Boostrap zainicjowana przez klienta.

Każda bieżąca aktywna sesja została przerwana przez to wywołanie i zastąpiona przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta PROGRAMU PRZEPŁYWM2M.
- **security_id:** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap, musi być ustawiony na wartość NX_LWM2M_RESERVED_ID (65535), jeśli serwer bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.
- **ip_address:** adres IP serwera.
- **port:** port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_NOT_FOUND:** nie ma wystąpienia obiektu zabezpieczeń odpowiadającego identyfikatorowi wystąpienia zabezpieczeń.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Rozpoczynanie bezpiecznej sesji z serwerem Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Opis

Ta usługa rozpoczyna sesję z serwerem bootstrap przy użyciu bezpiecznego połączenia z usługą DTLS. Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.

Sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza przed wywołaniem tej funkcji. NX_SECURE_ENABLE_DTLS musi być zdefiniowany.

Jeśli zasób "Hold Off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na uruchomienie zainicjowane przez serwer, jeśli po upływie tego czasu nie zostanie zainicjowane przez serwer uruchomienie, zostanie wykonana wartość Boostrap zainicjowana przez klienta.

Każda bieżąca aktywna sesja została przerwana przez to wywołanie i zastąpiona przez nową sesję serwera Bootstrap.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta PROGRAMU PRZEPŁYWM2M.
- **security_id:** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap, musi być ustawiony na wartość NX_LWM2M_RESERVED_ID (65535), jeśli serwer bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.
- **ip_address:** adres IP serwera.
- **port:** port UDP serwera.
- **dtls_session_ptr:** sesja DTLS do użycia dla sesji bootstrap.
- **dtls_local_port:** lokalny port UDP używany w sesji protokołu DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_NOT_FOUND:** nie ma wystąpienia obiektu zabezpieczeń odpowiadającego identyfikatorowi wystąpienia zabezpieczeń.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Tworzenie sesji klienta KOMPUTERA 2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Opis

Ta usługa tworzy nową sesję klienta SYSTEMU PULPITU 2M dołączona do istniejącego klienta PROGRAMU ONAM2M. Sesja jest używana przez klienta DOM2M do komunikowania się z serwerem Bootstrap lub serwerem THEM2M.

Aplikacja musi zapewnić funkcję wywołania zwrotnego, która zostanie wywołana po zaktualizowaniu stanu sesji.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta PROGRAMU PRZEPŁYWM2M.
- **client_ptr:** wskaźnik do wcześniej utworzonego klienta KOMPUTERA 2M.
- **state_callback:** wywołanie zwrotne aplikacji, które jest wywoływane po zmianie stanu sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Usuwanie sesji klienta KOMPUTERA 2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa sesję klienta KOMPUTERA 2M.

Po usunięciu klienta z programu THEM2M przez wywołanie nx_lwm2m_client_delete zostaną również usunięte wszystkie sesje dołączone do klienta.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta PROGRAMU PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Przerywanie sesji przy użyciu serwera DNS2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "De-Register" na serwerze CELUM2M.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta PROGRAMU PRZEPŁYWM2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_NOT_REGISTERED:** klient nie jest zarejestrowany na serwerze.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Uzyskiwanie ostatniego błędu sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca kod błędu sesji, gdy sesja jest w stanie błędu.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta KOMPUTERA 2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** sesja nie jest w stanie błędu.
- **NX_LWM2M_ADDRESS_ERROR:** nieprawidłowy adres serwera.
- **NX_LWM2M_BUFFER_TOO_SMALL:** Ładunek żądania nie mieści się w buforze sieciowym.
- **NX_LWM2M_DTLS_ERROR:** Nie można nawiązać zabezpieczonego połączenia z serwerem.
- **NX_LWM2M_ERROR:** Nieokreślony błąd.
- **NX_LWM2M_FORBIDDEN:** Odmowa rejestracji przez serwer.
- **NX_LWM2M_NOT_FOUND:** klient nie został znaleziony przez serwer podczas aktualizowania/wyrejestrowania.
- **NX_LWM2M_SERVER_INSTANCE_DELETED:** wystąpienie obiektu serwera odpowiadające sesji zostało usunięte.
- **NX_LWM2M_TIMED_OUT:** Brak odpowiedzi z serwera.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Rozpoczynanie sesji przy użyciu serwera ICHM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Zarejestruj" na serwerze POM2M. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwera.

Jeśli rejestracja powiedzie się, klient ZM2M będzie przetwarzać dalsze operacje z serwera i będzie okresowo wysyłać komunikaty "Update" do momentu cokołu rejestracji klienta.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera THEM2M.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta KOMPUTERA 2M.
- **server_id:** krótki identyfikator serwera SERWERA THEM2M.
- **ip_address:** adres IP serwera.
- **port:** port UDP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_NOT_FOUND:** Nie ma wystąpienia obiektu serwera odpowiadającego krótkiego identyfikatora serwera.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Rozpoczynanie bezpiecznej sesji przy użyciu serwera DNSM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Zarejestruj" na serwerze POM2M przy użyciu bezpiecznego połączenia DTLS. Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwera.

Sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza przed wywołaniem tej funkcji. NX_SECURE_ENABLE_DTLS należy zdefiniować.

Każda sesja protokołu DTLS używa własnego gniazda UDP do komunikacji, więc port lokalny dtls_local_port musi być inny dla każdej sesji, jeśli aplikacja tworzy kilka bezpiecznych sesji.

Jeśli rejestracja powiedzie się, klient ZM2M będzie przetwarzać dalsze operacje z serwera i będzie okresowo wysyłać komunikaty "Update" do momentu cokołu rejestracji klienta.

Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera THEM2M.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta KOMPUTERA 2M.
- **server_id:** krótki identyfikator serwera SERWERA THEM2M.
- **ip_address:** adres IP serwera.
- **port:** port UDP serwera.
- **dtls_session_ptr:** sesja DTLS do użycia na użytek sesji JEDNOSTKIM2M.
- **dtls_local_port:** lokalny port UDP używany na czas sesji protokołu DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_NOT_FOUND:** Nie ma wystąpienia obiektu serwera odpowiadającego krótkiego identyfikatora serwera.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Aktualizowanie sesji przy użyciu serwera ZARZĄDZANIA 2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wykonuje operację "Update" na serwerze JESTM2M.

### <a name="parameters"></a>Parametry

- **session_ptr:** wskaźnik do bloku sterowania sesji klienta KOMPUTERA 2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_NOT_REGISTERED:** klient nie jest zarejestrowany na serwerze.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Odblokowywanie klienta SIMM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa odblokowuje previoulsy klienta THEM2M zablokowane przez wywołanie nx_lwm2m_client_unlock().

### <a name="parameters"></a>Parametry

- **client_ptr:** wskaźnik do bloku sterowania klienta KOMPUTERAMI2M.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Tworzenie obiektu aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Opis

Ta usługa inicjuje obiekt aktualizacji oprogramowania układowego i dodaje obiekt do wcześniej utworzonego klienta SIECIOWAM2M. Obiekt aktualizacji oprogramowania układowego implementuje zasoby służące do komunikowania się z serwerem THEM2M, ale aplikacja musi zapewnić wywołania zwrotne w celu zaimplementowania rzeczywistych operacji na oprogramowaniu układowym (ładowanie, przechowywanie i aktualizowanie oprogramowania układowego).

Parametr protocols wskazuje, które protokoły są obsługiwane przez aplikację do pobierania oprogramowania układowego za pomocą zasobu "Package URI". Zdefiniowano następujące flagi:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Parametry

- **firmware_ptr:** wskaźnik do bloku sterowania Obiekt oprogramowania układowego.
- **client_ptr:** Wskaźnik do wstępnie utworzonego klienta ZM2M.
- **protocols:** flagi wskazujące, które protokoły są obsługiwane przez zasób URI pakietu.
- **package_callback:** musi mieć wartość NULL [TBD].
- **package_uri_callback:** wywołanie zwrotne używane do implementacji zasobu URI pakietu.
- **update_callback:** wywołanie zwrotne używane do implementacji zasobu Update.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Opis

Ta usługa zmienia wartości zasobów "PkgName" (6) i "PkgVersion" (7) obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr:** wskaźnik do obiektu aktualizacji oprogramowania układowego.
- **name**: nowa wartość nazwy pakietu.
- **version**: nowa wartość wersji pakietu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Ustawianie wyniku aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Opis

Ta usługa zmienia wartość zasobu "Wynik aktualizacji" (5) obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr:** wskaźnik do obiektu aktualizacji oprogramowania układowego.
- **result**: nowa wartość zasobu Update Result.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Ustawianie stanu aktualizacji oprogramowania układowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Opis

Ta usługa zmienia wartość zasobu "Stan" (3) obiektu aktualizacji oprogramowania układowego.

### <a name="parameters"></a>Parametry

- **firmware_ptr:** wskaźnik do obiektu aktualizacji oprogramowania układowego.
- **state:** nowa wartość zasobu State.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Zmiana sygnału wartości zasobu wystąpienia obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Opis

Ta usługa jest używana przez implementację obiektu w celu sygnalizuje klientowi PROJEKTUM2M, że jedna z jego wartości zasobów uległa zmianie. Jeśli zasób zostanie zaobserwowany przez serwer ZAMIM2M, klient ZM2M wyśle powiadomienie.

### <a name="parameters"></a>Parametry

- **object_ptr:** Wskaźnik do implementacji obiektu.
- **instance_ptr:** wskaźnik do wystąpienia obiektu.
- **resource**: wskaźnik do struktury opisującej zmieniony zasób.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- NX_PTR_ERROR: Nieprawidłowy wskaźnik.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Uzyskiwanie wartości zasobu logicznych

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość zasobu logicznych.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **bool_ptr:** Wskaźnik do docelowej wartości logicznych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością logiczną.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Uzyskiwanie wartości 32-bitowego zasobu zmiennoprzecinkowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 32-bitowego zasobu zmiennoprzecinkowego.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **float32_ptr:** wskaźnik do docelowej 32-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Uzyskiwanie wartości 64-bitowego zasobu zmiennoprzecinkowego

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 64-bitowego zasobu zmiennoprzecinkowego.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **float64_ptr:** wskaźnik do docelowej 64-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Uzyskiwanie wartości zasobu 32-bitowej liczby całkowitej

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość zasobu 32-bitowej liczby całkowitej.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **int32_ptr:** wskaźnik do docelowej 32-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością całkowitą lub wartość Liczba całkowita nie mieści się w liczbie 32-bitowej.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Uzyskiwanie wartości zasobu 64-bitowej liczby całkowitej

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 64-bitowego zasobu liczby całkowitej.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **int64_ptr:** wskaźnik do docelowej 64-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością całkowitą.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Uzyskiwanie wartości zasobu linku obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość zasobu linku obiektu.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **objlnk_ptr:** wskaźnik do wartości linku obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością linku obiektu.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Uzyskiwanie wartości nieprzezroczystego zasobu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość nieprzezroczystego zasobu.

Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **opaque_ptr_ptr:** Wskaźnik do docelowego wskaźnika nieprzezroczystego buforu.
- **opaque_length_ptr:** Wskaźnik do docelowej nieprzezroczystej długości buforu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością nieprzezroczystą.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Uzyskiwanie wartości zasobu ciągu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość zasobu ciągu.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości zasobu.
- **string_ptr_ptr:** wskaźnik do docelowego wskaźnika ciągu.
- **string_length_ptr:** wskaźnik do docelowej długości ciągu. Może mieć wartość NULL, jeśli ciąg ma zakończenie o wartości null.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_ENCODING:** wartość zasobu nie jest wartością ciągu.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Uzyskiwanie wartości logicznych wystąpień zasobów z wieloma zasobami

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość logicznych wystąpień zasobów z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **bool_ptr:** wskaźnik do docelowej wartości logicznych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością logiczną.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Uzyskiwanie wartości 32-bitowego wystąpienia wielu zasobów zmiennoprzecinkowych

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 32-bitowego wystąpienia zasobu zmiennoprzecinkowego z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **float32_ptr:** wskaźnik do docelowej 32-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Uzyskiwanie wartości 64-bitowego wystąpienia wielu zasobów zmiennoprzecinkowych

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 64-bitowego wystąpienia zasobu zmiennoprzecinkowego z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **float64_ptr:** wskaźnik do docelowej 64-bitowej wartości zmiennoprzecinkowej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością zmiennoprzecinkową.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Uzyskiwanie wartości 32-bitowej liczby całkowitej z wieloma wystąpieniami zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 32-bitowego całkowitego wystąpienia zasobu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **int32_ptr:** wskaźnik do docelowej 32-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością całkowitą lub wartość Liczba całkowita nie mieści się w liczbie 32-bitowej.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Uzyskiwanie wartości 64-bitowej liczby całkowitej wystąpienia wielu zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość 64-bitowego wystąpienia zasobu liczby całkowitej z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **int64_ptr:** wskaźnik do docelowej 64-bitowej liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością całkowitą.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Uzyskiwanie wartości wystąpienia wielu zasobów linku obiektu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość wystąpienia zasobu linku obiektu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **objlnk_ptr:** wskaźnik do wartości linku obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością linku obiektu.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Uzyskiwanie wartości nieprzezroczystego wystąpienia wielu zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość nieprzezroczystego wystąpienia zasobu z wielu zasobów.

Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **opaque_ptr_ptr:** Wskaźnik do docelowego wskaźnika nieprzezroczystego buforu.
- **opaque_length_ptr:** Wskaźnik do docelowej nieprzezroczystej długości buforu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość zasobu nie jest wartością nieprzezroczystą.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Uzyskiwanie wartości wystąpienia wielu zasobów ciągu

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Opis

Usługa pobiera wartość wystąpienia zasobu ciągu z wielu zasobów.

### <a name="parameters"></a>Parametry

- **value**: Wskaźnik do opisu wartości wielu zasobów.
- **index:** indeks wystąpienia do pobrania w tablicy wartości zasobów.
- **instance_id_ptr:** wskaźnik do docelowego identyfikatora wystąpienia.
- **string_ptr_ptr:** wskaźnik do docelowego wskaźnika ciągu.
- **string_length_ptr:** wskaźnik do docelowej długości ciągu. Może mieć wartość NULL, jeśli ciąg ma zakończenie o wartości null.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:** Pomyślna operacja.
- **NX_LWM2M_BAD_PARAMETER:** Indeks jest poza zakresem.
- **NX_LWM2M_BAD_ENCODING:** Zasób nie jest wieloma zasobami lub wartość wystąpienia nie jest wartością ciągu.
