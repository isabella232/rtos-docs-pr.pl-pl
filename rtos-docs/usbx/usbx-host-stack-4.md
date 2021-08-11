---
title: Rozdział 4 — Opis usług hosta USBX
description: Dowiedz się więcej o usługach hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6cbeff83d8e3812f13aa3f8f66d4013b70490d556911939186b4b43840aac50d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790687"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Rozdział 4 — Opis usług hosta USBX

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Zaimicjuj usbx dla operacji hosta.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Opis

Ta funkcja spowoduje zainicjowanie stosu hosta USB. Podany obszar pamięci zostanie skonfigurować do użytku wewnętrznego USBX. Jeśli UX_SUCCESS zwracany, USBX jest gotowy do rejestracji kontrolera hosta i klasy.

### <a name="input-parameter"></a>Parametr wejściowy

- **system_change_function** Wskaźnik do opcjonalnej procedury wywołania zwrotnego do powiadamiania o zmianach w urządzeniu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **UX_MEMORY_INSUFFICIENT** (0x12) Alokacja pamięci nie powiodła się.

### <a name="example"></a>Przykład

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Przerwać wszystkie transakcje dołączone do żądania przeniesienia dla punktu końcowego.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Opis

Ta funkcja anuluje wszystkie aktywne lub oczekujące transakcje dla określonego żądania przeniesienia dołączonego do punktu końcowego. Żądanie przeniesienia ma dołączona funkcję wywołania zwrotnego. Funkcja wywołania zwrotnego zostanie wywołana ze stanem UX_TRANSACTION_ABORTED zwrotnego.

### <a name="input-parameter"></a>Parametr wejściowy

- **punkt końcowy** Wskaźnik do punktu końcowego.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Brak błędów.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Punkt końcowy jest nieprawidłowy.

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

Pobierz wskaźnik do kontenera klasy.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Opis

Ta funkcja zwraca wskaźnik do kontenera klas. Klasa musi uzyskać swój kontener ze stosu USB, aby wyszukiwać wystąpienia, gdy klasa lub aplikacja chce otworzyć urządzenie.

> [!NOTE]
> Ciąg znaków C class_name być zakończony wartością NULL, a jego długość (bez samego terminatora NULL) nie może być większa niż UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Parametry

- **class_name** Wskaźnik do nazwy klasy.
- **klasa** Wskaźnik zaktualizowany przez wywołanie funkcji, które zawiera kontener klas dla nazwy klasy.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Brak błędów, po zwróceniu pole klasy jest zwracane ze wskaźnikiem do kontenera klas.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Klasa jest nieznana przez stos.

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

Ta funkcja rejestruje klasę USB w stosie USB. Klasa musi określić punkt wejścia dla stosu USB do wysyłania poleceń, takich jak poniższe.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> Ciąg ciągu języka C *class_name* być zakończony wartością NULL, a jego długość (bez samego terminatora NULL) nie może być większa **niż UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametry

- **class_name** Wskaźnik do nazwy klasy, prawidłowe wpisy znajdują się w pliku ux_system_initialize.c w klasach USBX.
- **class_entry_address** Adres funkcji entry klasy .

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Class installed successfully (Klasa UX_SUCCESS (0x00) została zainstalowana pomyślnie.
- **UX_MEMORY_ARRAY_FULL** (0x1a) Brak pamięci do przechowywania tej klasy.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host jest już zainstalowana.

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

Ta funkcja tworzy nowe wystąpienie klasy dla kontenera klas. Wystąpienie klasy nie jest zawarte w kodzie klasy, aby zmniejszyć złożoność klasy. Zamiast tego każde wystąpienie klasy jest dołączone do kontenera klas znajdującego się w stosie głównym.

### <a name="parameters"></a>Parametry

- **klasa** Wskaźnik do kontenera klas.
- **class_instance** Wskaźnik do wystąpienia klasy do utworzenia.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Wystąpienie klasy zostało dołączone do kontenera klas.

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

Niszczenie wystąpienia klasy dla kontenera klas.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Opis

Ta funkcja niszczy wystąpienie klasy dla kontenera klas.

### <a name="parameters"></a>Parametry

- **klasa** Wskaźnik do kontenera klas.
- **class_instance** Wskaźnik do wystąpienia, aby zniszczyć.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Wystąpienie klasy zostało zniszczona.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Wystąpienie klasy nie jest dołączone do kontenera klas.

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

Uzyskiwanie wskaźnika wystąpienia klasy dla określonej klasy.

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

- **klasa** Wskaźnik do kontenera klas.
- **class_index** Indeks, który ma być używany przez wywołanie funkcji na liście dołączonych klas do kontenera.
- **class_instance** Wskaźnik do wystąpienia, które ma zostać zwrócone przez wywołanie funkcji.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Znaleziono wystąpienie klasy.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Nie ma już żadnych wystąpień klas dołączonych do kontenera klas.

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

Uzyskaj wskaźnik do kontenera konfiguracji.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener konfiguracji na podstawie dojścia urządzenia i indeksu konfiguracji.

### <a name="parameters"></a>Parametry

- **urządzenie** Wskaźnik do kontenera urządzenia, który jest właścicielem żądanej konfiguracji.
- **configuration_index** Indeks konfiguracji do przeszukania.
- **konfiguracja** Adres wskaźnika do kontenera konfiguracji, który ma zostać zwrócony.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Znaleziono konfigurację.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) Kontener urządzenia nie istnieje.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Dojście do konfiguracji indeksu nie istnieje.

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

Wybierz określoną konfigurację dla urządzenia.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Opis

Ta funkcja wybiera określoną konfigurację dla urządzenia. Gdy ta konfiguracja jest ustawiona na urządzenie, domyślnie każdy interfejs urządzenia i skojarzone z nim alternatywne ustawienie 0 jest aktywowane na urządzeniu. Jeśli klasa urządzenia/interfejsu chce zmienić ustawienie określonego interfejsu, musi wydać wywołanie **ux_host_stack_interface_setting_select** usługi.

### <a name="parameters"></a>Parametry

- **konfiguracja** Wskaźnik do kontenera konfiguracji, który ma być włączony dla tego urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Wybór konfiguracji został pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Dojście do konfiguracji nie istnieje.
- **UX_OVER_CURRENT_CONDITION** (0x43) W magistrali dla tej konfiguracji istnieje warunek over current.

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

Uzyskiwanie wskaźnika do kontenera urządzenia.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener urządzenia na podstawie jego indeksu. Indeks urządzeń zaczyna się od 0. Należy pamiętać, że indeks jest programem ULONG, ponieważ możemy mieć kilka kontrolerów, a indeks bajtów może nie być wystarczający. Indeks urządzenia nie powinien być mylony z adresem urządzenia, który jest specyficzny dla magistrali.

### <a name="parameters"></a>Parametry

- **device_index** Indeks urządzenia.
- **urządzenie** Adres wskaźnika dla kontenera urządzenia, który ma być zwracany.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Kontener urządzenia istnieje i jest zwracany
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) Urządzenie nieznane

### <a name="example"></a>Przykład

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Pobierz kontener punktu końcowego.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener punktu końcowego na podstawie dojścia interfejsu i indeksu punktu końcowego. Zakłada się, że alternatywne ustawienie interfejsu zostało wybrane lub ustawienie domyślne jest używane przed wyszukiwaniem punktów końcowych.

### <a name="parameters"></a>Parametry

- **interfejs** Wskaźnik do kontenera interfejsu, który zawiera żądany punkt końcowy.
- **endpoint_index** Indeks punktu końcowego w tym interfejsie.
- **punkt końcowy** Adres kontenera punktu końcowego do zwrócenia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Kontener punktu końcowego istnieje i jest zwracany.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Określony interfejs nie istnieje.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Punkt końcowy nie istnieje.

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

Ta funkcja rejestruje kontroler USB w stosie USB. Przydziela głównie pamięć używaną przez ten kontroler i przekazuje do kontrolera polecenie inicjowania.

### <a name="parameters"></a>Parametry

- **hcd_name** Nazwa kontrolera hosta
- **hcd_function** Funkcja w kontrolerze hosta odpowiedzialna za inicjowanie.
- **hcd_param1** Zasób we/wy lub pamięci używany przez hcd.
- **hcd_param2** IrQ używany przez kontroler hosta.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Kontroler został zainicjowany prawidłowo.
- **UX_MEMORY_INSUFFICIENT** (0x12) Za mało pamięci dla tego kontrolera.
- **UX_PORT_RESET_FAILED** (0x31) Resetowanie kontrolera nie powiodło się.
- **UX_CONTROLLER_INIT_FAILED** (0x32) Kontroler nie zainicjował się prawidłowo.

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

Uzyskiwanie wskaźnika kontenera interfejsu.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Opis

Ta funkcja zwraca kontener interfejsu na podstawie dojścia konfiguracji, indeksu interfejsu i indeksu ustawień alternatywnych.

### <a name="parameters"></a>Parametry

- **konfiguracja** Wskaźnik do kontenera konfiguracji, który jest właścicielem interfejsu.
- **interface_index** Indeks interfejsu do przeszukania.
- **alternate_setting_index** Alternatywne ustawienie w interfejsie do wyszukiwania.
- **interfejs** Adres wskaźnika kontenera interfejsu, który ma zostać zwrócony.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Znaleziono i zwrócono kontener interfejsu dla indeksu interfejsu i alternatywne ustawienie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Konfiguracja nie istnieje.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interfejs nie istnieje.

### <a name="example"></a>Przykład

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

Wybierz alternatywne ustawienie interfejsu.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Opis

Ta funkcja wybiera konkretne alternatywne ustawienie dla danego interfejsu należącego do wybranej konfiguracji. Ta funkcja jest używana do zmiany z domyślnego alternatywnego ustawienia na nowe lub do powrotu do domyślnego ustawienia alternatywnego. Po wybraniu nowego ustawienia alternatywnego poprzednie charakterystyki punktu końcowego są nieprawidłowe i powinny zostać ponownie załadowane.

### <a name="input-parameter"></a>Parametr wejściowy

- **interfejs** Wskaźnik do kontenera interfejsu, którego alternatywne ustawienie ma zostać wybrane.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Alternatywne ustawienie dla tego interfejsu zostało pomyślnie wybrane.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interfejs nie istnieje.

### <a name="example"></a>Przykład

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Przerwać oczekujące żądanie przeniesienia.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Opis

Ta funkcja przerywa oczekujące żądanie przeniesienia, które zostało wcześniej przesłane. Ta funkcja anuluje tylko określone żądanie przeniesienia. Wywołanie funkcji będzie mieć UX_TRANSFER REQUEST_STATUS_ABORT stanu.

### <a name="parameters"></a>Parametry

- **żądanie przeniesienia** Wskaźnik do żądania przeniesienia, które ma zostać przerwane.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Anulowano transfer USB dla tego żądania transferu.

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

Ta funkcja wykonuje transakcję USB. Po wpisie żądania przeniesienia przekazuje potok punktu końcowego wybrany dla tej transakcji oraz parametry skojarzone z transferem (ładunek danych, długość transakcji). W przypadku potoku sterowania transakcja jest blokowana i będzie zwracana tylko wtedy, gdy zostały ukończone trzy fazy transferu kontroli lub jeśli wystąpił poprzedni błąd. W przypadku innych potoków stos USB zaplanuje transakcję na USB, ale nie będzie czekać na jej ukończenie. Każde żądanie transferu dla potoków nieblokacyjnych musi określać procedurę obsługi procedury ukończenia.

Gdy wywołanie funkcji zwraca, należy sprawdzić stan żądania przeniesienia, ponieważ zawiera on wynik transakcji.

### <a name="input-parameter"></a>Parametr wejściowy

- **transfer_request** Wskaźnik do żądania przeniesienia. Żądanie przeniesienia zawiera wszystkie informacje niezbędne do przeniesienia.

### <a name="return-values"></a>Wartości zwrócone

- **UX_SUCCESS** (0x00) Poprawnie zaplanowano transfer USB dla tego żądania transferu. Kod stanu żądania przeniesienia powinien zostać przeanalizowany po zakończeniu żądania przeniesienia.
- **UX_MEMORY_INSUFFICIENT** (0x12) Za mało pamięci do przydzielenia niezbędnych zasobów kontrolera.
- **UX_TRANSFER_NOT_READY** (0x25) Urządzenie było w nieprawidłowym stanie — musi być DOŁĄCZONE, ADRESOWANE lub SKONFIGUROWANE.

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
