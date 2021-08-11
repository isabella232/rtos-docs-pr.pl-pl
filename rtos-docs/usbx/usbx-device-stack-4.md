---
title: Rozdział 4 — Opis usług urządzeń USBX
description: Dowiedz się więcej o usługach urządzeń USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9d88d9bd177a251a00fec6757fc1f1494b56bab9655a55f973481f273f0683ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797555"
---
# <a name="description-of-usbx-device-services"></a>Opis usług urządzeń USBX

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Uzyskiwanie bieżącego alternatywnego ustawienia dla wartości interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta USB w celu uzyskania bieżącego alternatywnego ustawienia dla określonej wartości interfejsu. Jest on wywoływany przez sterownik kontrolera po **GET_INTERFACE** żądania.

### <a name="input-parameter"></a>Parametr wejściowy

- **Interface_value** Wartość interfejsu, dla której jest wyszukiwane bieżące alternatywne ustawienie

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Transfer danych został ukończony.
- **UX_ERROR** (0xFF) Nieprawidłowa wartość interfejsu.

### <a name="example"></a>Przykład

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Ustawianie bieżącego alternatywnego ustawienia dla wartości interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta USB do ustawiania bieżącego alternatywnego ustawienia dla określonej wartości interfejsu. Jest on wywoływany przez sterownik kontrolera po **SET_INTERFACE** żądania. Po **SET_INTERFACE,** wartości alternatywnych ustawień są stosowane do klasy.

Stos urządzeń wyemifikuje **UX_SLAVE_CLASS_COMMAND_CHANGE** do klasy, która jest właścicielem tego interfejsu, aby odzwierciedlić zmianę ustawienia alternatywnego.

### <a name="parameters"></a>Parametry

- **interface_value:** wartość interfejsu, dla której ustawiono bieżące alternatywne ustawienie.
- **alternate_setting_value:** nowa wartość ustawienia alternatywnego.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Transfer danych został ukończony.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Brak dołączonego interfejsu.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Urządzenie nie jest skonfigurowane.
- **UX_ERROR** (0xFF) Nieprawidłowa wartość interfejsu.

### <a name="example"></a>Przykład

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

Rejestrowanie nowej klasy urządzeń USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez aplikację do rejestrowania nowej klasy urządzeń USB. Ta rejestracja uruchamia kontener klasy, a nie wystąpienie klasy. Klasa powinna mieć aktywny wątek i być dołączona do określonego interfejsu.

Niektóre klasy oczekują parametru lub listy parametrów. Na przykład klasa magazynu urządzeń oczekuje geometrii urządzenia magazynującego, które próbuje emulować. Pole parametru jest w związku z tym zależne od wymagania klasy i może być wartością lub wskaźnikiem do struktury wypełnionej wartościami klasy.

> [!NOTE]
> Ciąg ciągu języka C class_name być zakończony wartością NULL, a jego długość (bez samego terminatora NULL) nie może być większa **niż UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametry

- **class_name** Nazwa klasy
- **class_entry_function** Funkcja entry klasy .
- **configuration_number** Numer konfiguracji, do który jest dołączona ta klasa.
- **interface_number** Numer interfejsu, do który jest dołączona ta klasa.
- **parametr** Wskaźnik do listy parametrów specyficznych dla klasy.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Zarejestrowano klasę
- **UX_MEMORY_INSUFFICIENT** (0x12) Brak wpisów w tabeli klas.
- **UX_THREAD_ERROR** (0x16) Nie można utworzyć wątku klasy.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Wyrejestruj klasę urządzenia USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez aplikację do wyrejestrniania klasy urządzenia USB.

> [!NOTE]
> Ciąg ciągu języka C class_name być zakończony wartością NULL, a jego długość (bez samego terminatora NULL) nie może być większa **niż UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametry

- **class_name:** Nazwa klasy
- **class_entry_function:** funkcja entry klasy .

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Klasa została wyrejestrowana.
- **UX_NO_CLASS_MATCH** (0x57) Klasa nie jest zarejestrowana.

### <a name="example"></a>Przykład

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

Pobierz bieżącą konfigurację

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta do uzyskiwania bieżącej konfiguracji uruchomionej na urządzeniu.

### <a name="input-parameter"></a>Parametr wejściowy

Brak

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Transfer danych został ukończony.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

Ustawianie bieżącej konfiguracji

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta do ustawienia bieżącej konfiguracji uruchomionej na urządzeniu. Po otrzymaniu tego polecenia stos urządzenia USB aktywuje alternatywne ustawienie 0 każdego interfejsu podłączonego do tej konfiguracji.

### <a name="input-parameter"></a>Parametr wejściowy

- **configuration_value** Wartość konfiguracji wybrana przez hosta.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Konfiguracja została pomyślnie ustawiona.

### <a name="example"></a>Przykład

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

Wysyłanie deskryptora do hosta

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez stronę urządzenia w celu zwrócenia deskryptora do hosta. Ten deskryptor może być deskryptorem urządzenia, deskryptorem konfiguracji lub deskryptorem ciągu.

### <a name="parameters"></a>Parametry

- **descriptor_type:** typ deskryptora. Musi mieć jedną z następujących wartości.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index:** indeks deskryptora.
- **host_length:** długość wymagana przez hosta.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Zakończono transfer danych.
- **UX_ERROR** (0xFF) Transfer nie został ukończony.

### <a name="example"></a>Przykład

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

Rozłącz stos urządzeń

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Opis

Menedżer VBUS wywołuje tę funkcję w przypadku rozłączenia urządzenia. Stos urządzenia poinformuje wszystkie klasy zarejestrowane na tym urządzeniu i zwolni wszystkie zasoby urządzenia.

### <a name="input-parameter"></a>Parametr wejściowy

Brak

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Urządzenie zostało odłączone.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Warunek wstrzymania punktu końcowego żądania

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana przez klasę urządzenia USB, gdy punkt końcowy powinien zwrócić warunek wsadu do hosta.

### <a name="input-parameter"></a>Parametr wejściowy

- **punkt końcowy** Punkt końcowy, w którym żądany jest warunek Zatrzymaj.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) Urządzenie jest w nieprawidłowym stanie.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Wznawianie hosta

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy urządzenie chce wznowić działanie hosta. To polecenie jest prawidłowe tylko wtedy, gdy urządzenie jest w trybie wstrzymania. To aplikacja urządzenia decyduje o tym, kiedy chce wznowić hosta USB. Na przykład modem USB może wznowić hosta po wykryciu sygnału RING na linii telefonicznej.

### <a name="input-parameter"></a>Parametr wejściowy

Brak

### <a name="return-values"></a>Wartości zwracane

- **UX_SUCCESS** (0x00) Wywołanie powiodło się.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Wywołanie nie powiodło się (urządzenie prawdopodobnie nie było w trybie zawieszonym).

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Inicjowanie stosu urządzenia USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana przez aplikację w celu zainicjowania stosu urządzenia USB. Nie inicjuje żadnych klas ani żadnych kontrolerów. Należy to zrobić przy użyciu oddzielnych wywołań funkcji. To wywołanie głównie zapewnia stos z platformą urządzenia dla funkcji USB. Obsługuje zarówno wysoką, jak i pełną szybkość, z możliwością uzyskania całkowicie oddzielnej struktury urządzeń dla każdej szybkości. Obsługiwane są struktury ciągów i wiele języków.

### <a name="parameters"></a>Parametry

- **device_framework_high_speed:** Wskaźnik do struktury o dużej szybkości.
- **device_framework_length_high_speed:** długość struktury o dużej szybkości.
- **device_framework_full_speed:** Wskaźnik do struktury o pełnej szybkości.
- **device_framework_length_full_speed:** długość struktury o pełnej szybkości.
- **string_framework:** Wskaźnik do struktury ciągów.
- **string_framework_length:** długość struktury ciągów.
- **language_id_framework:** Wskaźnik do struktury języka ciągów.
- **language_id_framework_length:** długość struktury języka ciągów.
- **ux_system_slave_change_function:** funkcja wywoływana po zmianie stanu urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_MEMORY_INSUFFICIENT** (0x12) Za mało pamięci do zainicjowania stosu.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) Deskryptor jest nieprawidłowy.

### <a name="example"></a>Przykład

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Aplikacja może zażądać wywołania, gdy kontroler zmieni swój stan. Dwa główne stany kontrolera to:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Jeśli aplikacja nie potrzebuje sygnałów Wstrzymaj/Wznów, będzie dostarczać UX_NULL funkcji.

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

Usuwanie interfejsu stosu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy należy usunąć interfejs. Interfejs jest usuwany, gdy urządzenie jest wyodrębnione, po zresetowaniu magistrali lub gdy istnieje nowe ustawienie alternatywne.

### <a name="input-parameter"></a>Parametr wejściowy

- **interface**: wskaźnik do interfejsu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Uzyskiwanie bieżącej wartości interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy host wysyła zapytanie do bieżącego interfejsu. Urządzenie zwraca bieżącą wartość interfejsu.

> [!NOTE]
> Ta funkcja jest przestarzała. Jest ona dostępna dla starszego oprogramowania, ale nowe oprogramowanie powinno używać ***ux_device_stack_alternate_setting_get*** zamiast tego.

### <a name="input-parameter"></a>Parametr wejściowy

- **interface_value** Wartość interfejsu do zwrócenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) Interfejs nie istnieje.

### <a name="example"></a>Przykład

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Zmienianie alternatywnego ustawienia interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy host żąda zmiany alternatywnego ustawienia interfejsu.

### <a name="parameters"></a>Parametry

- **device_framework:** adres struktury urządzeń dla tego interfejsu.
- **device_framework_length:** długość struktury urządzenia.
- **alternate_setting_value:** wartość ustawienia alternatywnego, która ma być używana przez ten interfejs.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) Interfejs nie istnieje.

### <a name="example"></a>Przykład

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

Rozpocznij wyszukiwanie klasy, która ma być właścicielem wystąpienia interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy interfejs został wybrany przez hosta, a stos urządzenia musi wyszukać klasę urządzenia, aby być właścicielem tego wystąpienia interfejsu.

### <a name="input-parameter"></a>Parametr wejściowy

- **interface**: wskaźnik do utworzonego interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_NO_CLASS_MATCH** (0x57) Dla tego interfejsu nie istnieje żadna klasa.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

Żądanie transferu danych do hosta

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa lub stos chce przesłać dane do hosta. Host zawsze sonduje urządzenie, ale urządzenie może przygotować dane z wyprzedzeniem.

### <a name="parameters"></a>Parametry

- **transfer_request:** Wskaźnik do żądania przeniesienia.
- **slave_length:** długość urządzenia, która ma zostać zwrócona.
- **host_length:** długość żądana przez hosta.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_TRANSFER_NOT_READY** (0x25) Urządzenie jest w nieprawidłowym stanie; Musi być **DOŁĄCZONY,** **SKONFIGUROWANY** lub **ADRESOWANY**.
- **UX_ERROR** (0xFF) transport.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

Anulowanie żądania przeniesienia

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi anulować żądanie przeniesienia lub gdy stos musi przerwać żądanie przeniesienia skojarzone z punktem końcowym.

### <a name="parameters"></a>Parametry

- **transfer_request:** Wskaźnik do żądania przeniesienia.
- **completion_code:** Kod błędu, który ma zostać zwrócony do klasy oczekującej na ukończenie żądania przeniesienia.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

Unitialize stack

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi jednolicieć stos urządzeń USBX — wszystkie zasoby stosu urządzenia są wolne. Ta nazwa powinna być wywoływana po wyrejestrowyniu wszystkich klas za pośrednictwem ux_device_stack_class_unregister.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-value"></a>Wartość zwracana

**UX_SUCCESS** (0x00) Ta operacja powiodła się.
