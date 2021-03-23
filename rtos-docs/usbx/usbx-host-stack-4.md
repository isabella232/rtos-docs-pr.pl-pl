---
title: Rozdział 4 — Opis usług hosta USBX
description: Dowiedz się więcej na temat usług hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824360"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Rozdział 4 — Opis usług hosta USBX

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Zainicjuj USBX dla operacji hosta.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Opis

Ta funkcja spowoduje zainicjowanie stosu hosta USB. Dostarczony obszar pamięci zostanie skonfigurowany do użytku wewnętrznego USBX. Jeśli zostanie zwrócona UX_SUCCESS, USBX jest gotowa do rejestracji kontrolerów hosta i klasy.

### <a name="input-parameter"></a>Parametr wejściowy

- **system_change_function** Wskaźnik do opcjonalnej procedury wywołania zwrotnego w celu powiadomienia aplikacji o zmianach urządzenia.

### <a name="return-value"></a>Wartość zwracana

- Pomyślnie zainicjowano **UX_SUCCESS** (0x00).
- **UX_MEMORY_INSUFFICIENT** (0x12) alokacja pamięci nie powiodła się.

### <a name="example"></a>Przykład

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Przerwij wszystkie transakcje dołączone do żądania transferu dla punktu końcowego.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Opis

Ta funkcja spowoduje anulowanie wszystkich transakcji aktywnych lub oczekujących na określone żądanie transferu dołączone do punktu końcowego. Żądanie transferu ma załączoną funkcję wywołania zwrotnego, funkcja wywołania zwrotnego zostanie wywołana ze stanem UX_TRANSACTION_ABORTED.

### <a name="input-parameter"></a>Parametr wejściowy

- **punkt końcowy** Wskaźnik do punktu końcowego.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) nie ma błędów.
- Dojście punktu końcowego **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) jest nieprawidłowe.

### <a name="example"></a>Przykład

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

Pobierz wskaźnik do kontenera klas.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Opis

Ta funkcja zwraca wskaźnik do kontenera klas. Klasa musi uzyskać kontener ze stosu USB, aby wyszukać wystąpienia, gdy Klasa lub aplikacja chcą otworzyć urządzenie.

> [!NOTE]
> Ciąg C class_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Parametry

- **class_name** Wskaźnik na nazwę klasy.
- **Klasa** Wskaźnik zaktualizowany przez wywołanie funkcji, który zawiera kontener klasy dla nazwy klasy.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0X00) Brak błędów, na zwrócić pole klasy jest zgłaszane ze wskaźnikiem do kontenera klas.
- Klasa **UX_HOST_CLASS_UNKNOWN** (0x59) jest nieznana przez stos.

### <a name="example"></a>Przykład

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

Zarejestruj klasę USB na stosie USB.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Opis

Ta funkcja rejestruje klasę USB na stosie USB. Klasa musi określać punkt wejścia dla stosu USB do wysyłania poleceń, takich jak następujące.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> Ciąg C *class_name* musi być zakończony zerem i długością (bez samego terminatora null) nie może być większy niż **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametry

- **class_name** Wskaźnik na nazwę klasy, prawidłowe wpisy znajdują się w pliku ux_system_initialize. c w klasie USB klasy USBX.
- **class_entry_address** Adres funkcji wejścia klasy.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie zainstalowano klasę **UX_SUCCESS** (0x00).
- **UX_MEMORY_ARRAY_FULL** (0X1a) nie więcej pamięci do przechowania tej klasy.
- Klasa hosta **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) jest już zainstalowana.

### <a name="example"></a>Przykład:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

Utwórz nowe wystąpienie klasy dla kontenera klas.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Opis

Ta funkcja tworzy nowe wystąpienie klasy dla kontenera klas. Wystąpienie klasy nie jest zawarte w kodzie klasy, aby zmniejszyć złożoność klasy. Zamiast tego każde wystąpienie klasy jest dołączone do kontenera klas znajdującego się w głównym stosie.

### <a name="parameters"></a>Parametry

- **Klasa** Wskaźnik do kontenera klas.
- **class_instance** Wskaźnik do wystąpienia klasy, które ma zostać utworzone.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) wystąpienie klasy zostało dołączone do kontenera klas.

### <a name="example"></a>Przykład

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

Zniszcz wystąpienie klasy dla kontenera klas.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Opis

Ta funkcja niszczy wystąpienie klasy dla kontenera klas.

### <a name="parameters"></a>Parametry

- **Klasa** Wskaźnik do kontenera klas.
- **class_instance** Wskaźnik do wystąpienia, które ma zostać zniszczone.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) wystąpienie klasy zostało zniszczone.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) wystąpienie klasy nie jest dołączone do kontenera klas.

### <a name="example"></a>Przykład

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

Pobierz wskaźnik wystąpienia klasy dla określonej klasy.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Opis

Ta funkcja zwraca wskaźnik wystąpienia klasy dla określonej klasy. Wystąpienie klasy nie jest zawarte w kodzie klasy, aby zmniejszyć złożoność klasy. Zamiast tego każde wystąpienie klasy jest dołączone do kontenera klas. Ta funkcja służy do wyszukiwania wystąpień klas w kontenerze klas.

### <a name="parameters"></a>Parametry

- **Klasa** Wskaźnik do kontenera klas.
- **class_index** Indeks, który ma być używany przez wywołanie funkcji na liście dołączonych klas do kontenera.
- **class_instance** Wskaźnik do wystąpienia, które ma zostać zwrócone przez wywołanie funkcji.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) wystąpienie klasy zostało znalezione.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie ma więcej wystąpień klasy dołączonych do kontenera klas.

### <a name="example"></a>Przykład

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

Pobierz wskaźnik do kontenera konfiguracji.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener konfiguracji oparty na dojściem urządzenia i indeksie konfiguracji.

### <a name="parameters"></a>Parametry

- **urządzenie** Wskaźnik do kontenera urządzenia, do którego należy żądana konfiguracja.
- **configuration_index** Indeks konfiguracji do przeszukania.
- **Konfiguracja** Adres wskaźnika do zwrócenia kontenera konfiguracji.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) konfiguracja została znaleziona.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) kontener urządzeń nie istnieje.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie istnieje uchwyt konfiguracyjny dla tego indeksu.

### <a name="example"></a>Przykład

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

Wybierz konkretną konfigurację urządzenia.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Opis

Ta funkcja wybiera określoną konfigurację dla urządzenia. Gdy ta konfiguracja jest ustawiona na urządzenie, domyślnie na urządzeniu jest uaktywniany każdy interfejs urządzenia i jego skojarzone ustawienia alternatywne 0. Jeśli Klasa urządzenia/interfejsu chce zmienić ustawienie określonego interfejsu, musi wydać **ux_host_stack_interface_setting_select** wywołanie usługi.

### <a name="parameters"></a>Parametry

- **Konfiguracja** Wskaźnik do kontenera konfiguracji, który ma być włączony dla tego urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) wybór konfiguracji zakończył się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) dojście konfiguracji nie istnieje.
- Na magistrali dla tej konfiguracji **UX_OVER_CURRENT_CONDITION** (0x43) znajduje się nad bieżącym stanem.

### <a name="example"></a>Przykład

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

Pobierz wskaźnik do kontenera urządzeń.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener urządzenia na podstawie jego indeksu. Indeks urządzenia zaczyna się od 0. Należy zauważyć, że indeks jest ULONG, ponieważ może istnieć kilka kontrolerów, a indeks bajtów może być niewystarczający. Nie należy mylić indeksu urządzenia z adresem urządzenia, który jest specyficzny dla magistrali.

### <a name="parameters"></a>Parametry

- **device_index** Indeks urządzenia.
- **urządzenie** Adres wskaźnika dla kontenera urządzenia do zwrócenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) kontener urządzenia istnieje i jest zwracany
- Nieznane urządzenie **UX_DEVICE_HANDLE_UNKNOWN** (0x50)

### <a name="example"></a>Przykład

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Pobieranie kontenera punktów końcowych.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener punktów końcowych na podstawie uchwytu interfejsu i indeksu punktu końcowego. Przyjęto założenie, że zostało wybrane alternatywne ustawienie interfejsu lub domyślne ustawienie jest używane przed przeszukiwaniem punktów końcowych.

### <a name="parameters"></a>Parametry

- **interfejs** Wskaźnik do kontenera interfejsu zawierającego żądany punkt końcowy.
- **endpoint_index** Indeks punktu końcowego w tym interfejsie.
- **punkt końcowy** Adres kontenera punktu końcowego, który ma zostać zwrócony.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) kontener punktu końcowego istnieje i jest zwracany.
- Określony interfejs **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) nie istnieje.
- Indeks punktu końcowego **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) nie istnieje.

### <a name="example"></a>Przykład

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

Zarejestruj kontroler USB na stosie USB.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Opis

Ta funkcja rejestruje kontroler USB na stosie USB. Polega to głównie na przydzieleniu pamięci używanej przez ten kontroler i przekazaniem polecenia inicjującego do kontrolera.

### <a name="parameters"></a>Parametry

- **hcd_name** Nazwa kontrolera hosta
- **hcd_function** Funkcja w kontrolerze hosta odpowiedzialna za inicjalizację.
- **hcd_param1** Zasób we/wy lub pamięć używany przez HCD.
- **hcd_param2** PRZERWAnie używane przez kontroler hosta.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) kontroler został prawidłowo zainicjowany.
- **UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci dla tego kontrolera.
- **UX_PORT_RESET_FAILED** (0x31) resetowanie kontrolera nie powiodło się.
- **UX_CONTROLLER_INIT_FAILED** (0x32) nie można poprawnie zainicjować kontrolera.

### <a name="example"></a>Przykład

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

Pobierz wskaźnik kontenera interfejsu.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener interfejsu na podstawie dojścia do konfiguracji, indeksu interfejsu i alternatywnego indeksu ustawienia.

### <a name="parameters"></a>Parametry

- **Konfiguracja** Wskaźnik do kontenera konfiguracji, który jest właścicielem interfejsu.
- **interface_index** Indeks interfejsu do przeszukania.
- **alternate_setting_index** Alternatywne ustawienie w interfejsie do wyszukania.
- **interfejs** Adres wskaźnika kontenera interfejsu, który ma zostać zwrócony.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) kontener interfejsu dla indeksu interfejsu oraz ustawienia alternatywnego zostały znalezione i zwrócone.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Konfiguracja nie istnieje.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) interfejs nie istnieje.

### <a name="example"></a>Przykład

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

Wybierz alternatywne ustawienie dla interfejsu.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Opis

Ta funkcja wybiera określone ustawienie alternatywne dla danego interfejsu należącego do wybranej konfiguracji. Ta funkcja jest używana do zmiany ustawienia domyślnego alternatywnego na nowe ustawienie lub w celu powrotu do domyślnego ustawienia alternatywnego. W przypadku wybrania nowego ustawienia alternatywnego parametry poprzedniego punktu końcowego są nieprawidłowe i należy je ponownie załadować.

### <a name="input-parameter"></a>Parametr wejściowy

- **interfejs** Wskaźnik do kontenera interfejsu, którego alternatywnym ustawieniem jest wybranie.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) ustawienie alternatywne dla tego interfejsu zostało pomyślnie wybrane.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) interfejs nie istnieje.

### <a name="example"></a>Przykład

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Przerywanie oczekującego żądania transferu.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Opis

Ta funkcja przerywa oczekujące żądanie transferu, które zostało wcześniej przesłane. Ta funkcja tylko Anuluje określone żądanie transferu. Wywołanie z powrotem do funkcji będzie miało stan UX_TRANSFER REQUEST_STATUS_ABORT.

### <a name="parameters"></a>Parametry

- **żądanie transferu** Wskaźnik do żądania przeniesienia, które ma zostać przerwane.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) anulowano transfer USB dla tego żądania transferu.

### <a name="example"></a>Przykład

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

Zażądaj transferu USB.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Opis

Ta funkcja wykonuje transakcję USB. Po wprowadzeniu żądanie transferu zapewnia potok punktu końcowego wybrany dla tej transakcji i parametry skojarzone z transferem (ładunek danych, Długość transakcji). W przypadku potoku kontroli transakcja jest zablokowana i zwróci się tylko wtedy, gdy trzy fazy transferu kontroli zostały zakończone lub wystąpił poprzedni błąd. W przypadku innych potoków stos USB będzie planować transakcję na USB, ale nie czeka na jego zakończenie. Każde żądanie transferu dla potoków nieblokujących musi określać procedurę obsługi procedury uzupełniania.

Gdy wywołanie funkcji zwraca, stan żądania przeniesienia powinien zostać zbadany, ponieważ zawiera wynik transakcji.

### <a name="input-parameter"></a>Parametr wejściowy

- **transfer_request** Wskaźnik na żądanie transferu. Żądanie transferu zawiera wszystkie niezbędne informacje wymagane do przeniesienia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) transfer USB dla tego żądania transferu został zaplanowany prawidłowo. Kod stanu żądania przeniesienia należy sprawdzić po zakończeniu żądania transferu.
- **UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci, aby przydzielić wymagane zasoby kontrolera.
- **UX_TRANSFER_NOT_READY** (0x25) urządzenie było w nieprawidłowym stanie — musi być dołączone, rozkierowane lub skonfigurowane.

### <a name="example"></a>Przykład:

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
