---
title: Rozdział 4 — Opis usług urządzenia USBX
description: Dowiedz się więcej na temat usług urządzenia USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824042"
---
# <a name="description-of-usbx-device-services"></a>Opis usług urządzenia USBX

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Pobierz bieżące ustawienie alternatywne dla wartości interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta USB do uzyskiwania bieżącego alternatywnego ustawienia dla określonej wartości interfejsu. Jest on wywoływany przez sterownik kontrolera po odebraniu żądania **GET_INTERFACE** .

### <a name="input-parameter"></a>Parametr wejściowy

- **Interface_value** Wartość interfejsu, dla którego jest wysyłane zapytanie do bieżącego ustawienia alternatywnego

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) transfer danych został ukończony.
- **UX_ERROR** (0Xff) Nieprawidłowa wartość interfejsu.

### <a name="example"></a>Przykład

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Ustaw bieżące ustawienie alternatywne dla wartości interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta USB do ustawiania bieżącego alternatywnego ustawienia dla określonej wartości interfejsu. Jest on wywoływany przez sterownik kontrolera po odebraniu żądania **SET_INTERFACE** . Po zakończeniu **SET_INTERFACE** wartości ustawień alternatywnych są stosowane do klasy.

Stos urządzeń będzie wystawiał **UX_SLAVE_CLASS_COMMAND_CHANGE** do klasy, która jest właścicielem tego interfejsu w celu odzwierciedlenia zmiany ustawienia alternatywnego.

### <a name="parameters"></a>Parametry

- **interface_value**: wartość interfejsu, dla którego ustawiono bieżące ustawienie alternatywne.
- **alternate_setting_value**: Nowa wartość ustawienia alternatywnego.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) transfer danych został ukończony.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0X52) brak dołączonego interfejsu.
- Urządzenie **UX_FUNCTION_NOT_SUPPORTED** (0x54) nie jest skonfigurowane.
- **UX_ERROR** (0Xff) Nieprawidłowa wartość interfejsu.

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

Ta funkcja jest używana przez aplikację do zarejestrowania nowej klasy urządzenia USB. Ta rejestracja uruchamia kontener klasy, a nie wystąpienie klasy. Klasa powinna mieć aktywny wątek i być dołączona do określonego interfejsu.

Niektóre klasy oczekują parametru lub listy parametrów. Na przykład Klasa magazynu urządzenia powinna oczekiwać geometrii urządzenia magazynującego, które próbuje emulować. W związku z tym pole parametru jest zależne od wymaganej klasy i może być wartością lub wskaźnikiem do struktury wypełnionej wartościami klasy.

> [!NOTE]
> Ciąg C class_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametry

- **class_name** Nazwa klasy
- **class_entry_function** Funkcja wejścia klasy.
- **configuration_number** Numer konfiguracji, do której jest dołączona Ta klasa.
- **interface_number** Numer interfejsu, do którego jest dołączona Ta klasa.
- **parametr** Wskaźnik do listy parametrów specyficznych dla klasy.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Klasa została zarejestrowana
- **UX_MEMORY_INSUFFICIENT** (0X12) nie pozostało wpisów w tabeli klas.
- **UX_THREAD_ERROR** (0X16) nie może utworzyć wątku klasy.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Wyrejestrowywanie klasy urządzenia USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez aplikację do wyrejestrowywania klasy urządzenia USB.

> [!NOTE]
> Ciąg C class_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametry

- **class_name**: Nazwa klasy
- **class_entry_function**: funkcja wejścia klasy.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) wyrejestrowano klasę.
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

Ta funkcja jest używana przez hosta w celu uzyskania bieżącej konfiguracji uruchomionej na urządzeniu.

### <a name="input-parameter"></a>Parametr wejściowy

Brak

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) transfer danych został ukończony.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

Ustaw bieżącą konfigurację

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez hosta do ustawiania bieżącej konfiguracji działającej na urządzeniu. Po odebraniu tego polecenia stos urządzeń USB uaktywni ustawienie alternatywny 0 każdego interfejsu połączonego z tą konfiguracją.

### <a name="input-parameter"></a>Parametr wejściowy

- **configuration_value** Wartość konfiguracji wybrana przez hosta.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) konfiguracja została pomyślnie ustawiona.

### <a name="example"></a>Przykład

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

Wyślij deskryptor do hosta

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Opis

Ta funkcja jest używana przez stronę urządzenia do zwrócenia deskryptora do hosta. Ten deskryptor może być deskryptorem urządzenia, deskryptorem konfiguracji lub deskryptorem ciągu.

### <a name="parameters"></a>Parametry

- **descriptor_type**: typ deskryptora. Musi mieć jedną z następujących wartości.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index**: indeks deskryptora.
- **host_length**: długość wymagana przez hosta.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) transfer danych został ukończony.
- **UX_ERROR** (0xFF) transfer nie został ukończony.

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

Odłącz stos urządzeń

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Opis

Menedżer VBUS wywołuje tę funkcję w przypadku odłączenia urządzenia. Stos urządzeń będzie powiadamiał wszystkie klasy zarejestrowane na tym urządzeniu i następnie zwolni wszystkie zasoby urządzenia.

### <a name="input-parameter"></a>Parametr wejściowy

Brak

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) urządzenie zostało rozłączone.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Warunek zatrzymania punktu końcowego żądania

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana przez klasę urządzenia USB, gdy punkt końcowy powinien zwrócić warunek parkingowy do hosta.

### <a name="input-parameter"></a>Parametr wejściowy

- **punkt końcowy** Punkt końcowy, dla którego zażądano warunku parkingowego.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR** (0xFF) urządzenie jest w nieprawidłowym stanie.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Wznawianie działania hosta

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy urządzenie chce wznowić działanie hosta. To polecenie jest prawidłowe tylko wtedy, gdy urządzenie jest w trybie wstrzymania. Aby określić, kiedy ma wznowić hosta USB, należy do aplikacji urządzenia. Na przykład modem USB może wznowić Host po wykryciu sygnału PIERŚCIENIowego w linii telefonicznej.

### <a name="input-parameter"></a>Parametr wejściowy

Brak

### <a name="return-values"></a>Wartości zwracane

- **UX_SUCCESS** (0x00) wywołanie zakończyło się pomyślnie.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) wywołanie nie powiodło się (urządzenie prawdopodobnie nie jest w trybie zawieszenia).

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Zainicjuj stos urządzeń USB

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

Ta funkcja jest wywoływana przez aplikację w celu zainicjowania stosu urządzeń USB. Nie inicjuje żadnych klas ani żadnych kontrolerów. Należy to zrobić z oddzielnymi wywołaniami funkcji. To wywołanie głównie zapewnia stos z platformą urządzenia dla funkcji USB. Obsługuje zarówno wysoką, jak i pełną szybkość, z możliwością posiadania całkowicie oddzielnej struktury urządzenia dla każdej szybkości. Obsługiwane są struktury ciągów i wiele języków.

### <a name="parameters"></a>Parametry

- **device_framework_high_speed**: wskaźnik do struktury o dużej szybkości.
- **device_framework_length_high_speed**: długość platformy o dużej szybkości.
- **device_framework_full_speed**: wskaźnik do struktury pełnej prędkości.
- **device_framework_length_full_speed**: długość struktury pełnej prędkości.
- **string_framework**: wskaźnik do struktury String.
- **string_framework_length**: długość struktury ciągu.
- **language_id_framework**: wskaźnik do struktury języka ciągu.
- **language_id_framework_length**: długość struktury języka String.
- **ux_system_slave_change_function**: funkcja, która ma być wywoływana w przypadku zmiany stanu urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci, aby zainicjować stos.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) deskryptor jest nieprawidłowy.

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

Aplikacja może zażądać wywołania zwrotnego, gdy kontroler zmieni swój stan. Dwa główne Stany kontrolera to:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Jeśli aplikacja nie wymaga sygnałów wstrzymywania/wznawiania, może dostarczyć funkcję UX_NULL.

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

Ta funkcja jest wywoływana, gdy interfejs powinien zostać usunięty. Interfejs jest usuwany podczas wyodrębniania urządzenia lub po zresetowaniu magistrali lub gdy jest dostępne nowe ustawienie alternatywne.

### <a name="input-parameter"></a>Parametr wejściowy

- **interfejs**: wskaźnik do interfejsu, który ma zostać usunięty.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Pobierz bieżącą wartość interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy Host wysyła zapytanie do bieżącego interfejsu. Urządzenie zwraca bieżącą wartość interfejsu.

> [!NOTE]
> Ta funkcja jest przestarzała. Jest on dostępny dla starszego oprogramowania, ale zamiast tego należy użyć funkcji ***ux_device_stack_alternate_setting_get*** .

### <a name="input-parameter"></a>Parametr wejściowy

- **interface_value** Wartość interfejsu do zwrócenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR** (0Xff) nie istnieje interfejs.

### <a name="example"></a>Przykład

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Zmiana alternatywnego ustawienia interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy host żąda zmiany ustawienia alternatywnego dla interfejsu.

### <a name="parameters"></a>Parametry

- **device_framework**: adres platformy urządzenia dla tego interfejsu.
- **device_framework_length**: długość platformy urządzeń.
- **alternate_setting_value**: wartość ustawienia alternatywnego, która ma być używana przez ten interfejs.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR** (0Xff) nie istnieje interfejs.

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

Rozpocznij wyszukiwanie klasy jako należącej do wystąpienia interfejsu

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy interfejs został wybrany przez hosta, a stos urządzenia musi wyszukać klasę urządzenia, aby było to wystąpienie tego interfejsu.

### <a name="input-parameter"></a>Parametr wejściowy

- **interfejs**: wskaźnik do utworzonego interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_NO_CLASS_MATCH** (0X57) nie istnieje Klasa dla tego interfejsu.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

Żądanie przeniesienia danych do hosta

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy Klasa lub stos chce przesłać dane do hosta. Host zawsze sonduje urządzenie, ale urządzenie może z wyprzedzeniem przygotować dane.

### <a name="parameters"></a>Parametry

- **transfer_request**: wskaźnik do żądania transferu.
- **slave_length**: długość urządzenia chce zwrócić.
- **host_length**: długość żądania hosta.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_TRANSFER_NOT_READY** (0x25) urządzenie jest w nieprawidłowym stanie; należy ją **dołączyć**, **skonfigurować** lub **rozwiązać**.
- Błąd transportu **UX_ERROR** (0xFF).

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

Ta funkcja jest wywoływana, gdy aplikacja musi anulować żądanie transferu lub kiedy stos musi przerwać żądanie transferu skojarzone z punktem końcowym.

### <a name="parameters"></a>Parametry

- **transfer_request**: wskaźnik do żądania transferu.
- **completion_code**: kod błędu do zwrócenia do klasy oczekującej na ukończenie tego żądania transferu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

Stos Unitialize

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja wymaga unitialize stosu urządzeń USBX — wszystkie zasoby stosu urządzeń są zwolnione. Ta nazwa powinna być wywoływana po wyrejestrowaniu wszystkich klas za pośrednictwem ux_device_stack_class_unregister.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-value"></a>Wartość zwracana

**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
