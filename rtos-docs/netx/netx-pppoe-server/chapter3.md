---
title: Rozdział 3 — Opis Azure RTOS NetX PPPoE Server Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX PPPoE Server (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d184fc3c5e6ed74ef25045561b1613e280672f77385fbb13b8e84bccf051b301
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782816"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Rozdział 3 — Opis Azure RTOS NetX PPPoE Server Services

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX PPPoE Server (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_pppoe_server_create:** Tworzenie *wystąpienia serwera PPPoE*

- **nx_pppoe_server_ac_name_set:** Ustaw *nazwę podmiotu dostępu*

- **nx_pppoe_server_delete:** Usuwanie *wystąpienia serwera PPPoE*

- **nx_pppoe_server_enable:** Włączanie *usług serwera PPPoE*

- **nx_pppoe_server_disable:** *Wyłączanie usług serwera PPPoE*

- **nx_pppoe_server_callback_notify_set:** Ustawianie funkcji powiadamiania zwrotnego *wywołania zwrotnego serwera PPPoE*

- **nx_pppoe_server_service_name_set:** Ustaw *nazwę usługi serwera PPPoE*

- **nx_pppoe_server_session_send:** Wysyłanie *danych serwera PPPoE do określonej sesji*

- **nx_pppoe_server_session_packet_send:** Wyślij *pakiet serwera PPPoE do określonej sesji*

- **nx_pppoe_server_session_terminate:** Zakończenie *określonej sesji PPPoE*

- **nx_pppoe_server_session_get:** uzyskiwanie *informacji o określonej sesji*

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

Tworzenie wystąpienia serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera PPPoE z dostarczonym przez użytkownika sterownikem linku dla określonego wystąpienia adresu IP NetX. Jeśli sterownik łącza nie został zainicjowany i włączony, oprogramowanie Sever PPPoE jest odpowiedzialne za inicjowanie sterownika łącza.

Ponadto aplikacja musi podać wcześniej utworzoną pulę pakietów dla wystąpienia serwera PPPoE do użycia na użytek wewnętrznej alokacji pakietów.

Należy pamiętać, że zazwyczaj dobrym pomysłem jest utworzenie wątku ip NetX o wyższym priorytecie niż priorytet wątku serwera PPPoE. Zapoznaj się z *usługą nx_ip_create,* aby uzyskać więcej informacji na temat określania priorytetu wątku ip.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **name**: nazwa tego wystąpienia serwera PPPoE.
- **ip_ptr:** Wskaźnik do bloku sterowania dla wystąpienia adresu IP.
- **interface_index:** Indeks interfejsu.
- **pppoe_link_driver:** sterownik linku podany przez użytkownika.
- **pool_ptr:** wskaźnik do puli pakietów.
- **stack_ptr:** Wskaźnik do rozpoczęcia obszaru stosu wątku pppoE serwera.
- **stack_size:** rozmiar w bajtach w stosie wątku.
- **priority:** priorytet wewnętrznych wątków serwera PPPoE (1–31).

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne utworzenie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE, adresu IP, puli pakietów lub stosu.
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Nieprawidłowy interfejs.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Nieprawidłowy rozmiar ładunku puli pakietów.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Nieprawidłowy rozmiar pamięci.
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Nieprawidłowy priorytet wątku serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

Usuwanie wystąpienia serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie serwera PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

Włączanie usługi serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia korzystanie z usług serwera PPPoE.

> [!NOTE]
> Ta funkcja musi być wywoływana po *nx_pppoe_server_create* i *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

Wyłączanie usługi serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza usługi serwera PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Ustawianie funkcji powiadamiania zwrotnego serwera PPPoE 

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>Opis

Ta usługa ustawia funkcje powiadamiania zwrotnego serwera PPPoE.

> [!NOTE]
> Ta funkcja musi być wywoływana przed *nx_pppoe_server_enabl,* a wskaźnik pppoe_data_receive_notify funkcji musi być ustawiony, jeśli *nie,* nx_pppoe_server_enable się niepowodzeniem.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **pppoe_discover_initiation_notify:** Funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat inicjacji odnajdywania PPPoE. Jeśli ta wartość to NULL, odnajdywanie funkcji wywołania zwrotnego inicjacji jest wyłączona.
- **pppoe_discover_request_notify:** Funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat żądania odnajdywania PPPoE. Jeśli ta wartość to NULL, odnajdowanie funkcji wywołania zwrotnego żądania jest wyłączone.
- **pppoe_discover_terminate_notify:** Funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat zakończenia odnajdywania PPPoE. Jeśli ta wartość to NULL, odnajdowanie funkcji wywołania zwrotnego terminate jest wyłączone.
- **pppoe_discover_terminate_confirm:** Funkcja aplikacji, która jest wywoływana przy każdym wysłaniu komunikatu zakończenia odnajdywania PPPoE. Jeśli ta wartość to NULL, odnajdywanie funkcji wywołania zwrotnego zakończenia jest wyłączone.
- **pppoe_data_receive_notify:** funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat danych PPPoE. Ta wartość nie może być równa zero.
- **pppoe_data_send_notify:** funkcja aplikacji wywoływana za każdym razem, gdy jest wysyłany komunikat danych PPPoE. Jeśli ta wartość ma wartość NULL, funkcja wywołania zwrotnego wysyłania danych jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE lub wskaźnik funkcji.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

Ustawianie nazwy programu Access Naimki

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Opis

Ta funkcja ustawiła wywołanie funkcji Access Naimek.

> [!NOTE]
> Ciąg znaków ac_name musi mieć wartość NULL, a długość ac_name odpowiada długości określonej na liście argumentów.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **ac_name:** Uzyskaj dostęp do nazwy inicjatora.
- **ac_name_length:** długość ac_ame.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Zestaw pomyślnego serwera PPPoE.
- **NX_PPPOE_SERVER_PTR_ERROR:**(0xC1) Nieprawidłowy serwer PPPoE, adres IP, pula pakietów lub wskaźnik stosu.
- **NX_SIZE_ERROR:**(0x09) Sprawdzanie name_length niepowodzeniem.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Ustawianie nazwy usługi serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę usługi serwera PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

Wysyłanie danych serwera PPPoE do określonej sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Opis

Ta usługa wysyła ramkę PPPoE przy użyciu określonego identyfikatora sesji.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **session_index:** indeks sesji.
- **data_ptr:** wskaźnik do początku ramki danych serwera PPPoE.
- **data_length:** długość ramki danych serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) Serwer PPPoE nie jest włączona.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie jest ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Wysyłanie pakietu serwera PPPoE do określonej sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet PPPoE przy użyciu określonego identyfikatora sesji.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **session_index:** indeks sesji.
- **packet_ptr:** wskaźnik do pakietu PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Nieprawidłowy pakiet serwera PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) Serwer PPPoE nie jest włączona.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie jest ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

Zakończenie określonej sesji PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Opis

Ta usługa kończy określoną sesję PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **session_index:** indeks sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) Serwer PPPoE nie jest włączona.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie jest ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Uzyskiwanie informacji o określonej sesji PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Opis

Ta usługa pobiera określone informacje o sesji PPPoE, adres fizyczny klienta i identyfikator sesji.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr:** wskaźnik do bloku sterowania serwera PPPoE.
- **session_index:** indeks sesji.
- **client_mac_msw:** Wskaźnik MSW adresu fizycznego klienta.
- **client_mac_lsw:** Wskaźnik MSW adresu fizycznego klienta.
- **session_id:** Wskaźnik identyfikatora sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS:**(0x00) Pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie jest ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Konfigurowanie domyślnej nazwy usługi

### <a name="prototype"></a>Prototype

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE uwidacznia tę funkcję, aby umożliwić oprogramowaniu TTP skonfigurowanie "domyślnej nazwy usługi", która powinna być używana przez ppPoE do filtrowania przychodzących żądań PADI. Oprogramowanie PPPoE powinno zapamiętać te informacje, a jeśli zostanie odebrany pakiet PADI zawierający nazwę usługi, która jest taka sama, powinien wywołać nazwę PppDiscoverReq.

### <a name="input-parameters"></a>Parametry wejściowe

- **length:** długość domyślnej nazwy usługi.
- **aData:** domyślna nazwa usługi.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Definiowanie pola Nazwa usługi pakietu PADO

### <a name="prototype"></a>Prototype

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić oprogramowaniu TTP zdefiniowanie pola Nazwa usługi pakietu PADO. Oprogramowanie PPPoE nie powinno wysyłać pado, dopóki nie zostanie wywołana nazwa PppDiscoverCnf.

Pakiet PADO musi zawierać nazwę rezydatora dostępu (przy użyciu identyfikatora tagu 0x0102 zdefiniowanego w dokumencie RFC2516) zdefiniowaną podczas inicjowania oprogramowania PPPoE.

W pliku aData można określić wiele nazw usług, a każda nazwa zostanie zakończona zerową.

Znak null jest używany jako separator, aby zapewnić maksymalną elastyczność na wypadek, gdy inne polecenia muszą zostać przekazane jako część nazwy usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **length:** długość domyślnej nazwy usługi.
- **aData:** domyślna nazwa usługi.
- **interfaceHandle:** Dojście do interfejsu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpenCnf

Akceptowanie lub odrzucanie sesji PPPoE

### <a name="prototype"></a>Prototype

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić oprogramowaniu TTP akceptowanie lub odrzucanie sesji PPPoE.  W odpowiedzi na to stos PPPoE powinien zaakceptować połączenie i przypisać unikatowy numer PPPoE Session_ID skojarzony z interfaceHandle.

### <a name="input-parameters"></a>Parametry wejściowe

- **Zaakceptuj**: NX_TRUE, jeśli połączenie ma zostać zaakceptowane.
- **interfaceHandle:** Dojście do interfejsu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

Zamykanie sesji PPPoE

### <a name="prototype"></a>Prototype

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić oprogramowaniu TTP zamknięcie sesji PPPoE.

Oprogramowanie PPPoE wskaże ciąg kodu przyczyny w Generic-Error tagu (0x0203) w komunikacie PADT

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle:** Dojście do interfejsu.
- **causeCode:** ciąg zakończony wartością null do wysyłania informacji o przyczynie zamknięcia połączenia z serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Upewnij się, że dojście zostało wolne

### <a name="prototype"></a>Prototype

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić oprogramowaniu TTP potwierdzenie, że dojście zostało wolne.

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle:** Dojście do interfejsu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Zezwalaj na potwierdzenie poprzednich danych PROTOKOŁU PPP

### <a name="prototype"></a>Prototype

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić potwierdzenie poprzedniej funkcji PppTransmitDataReq.  Oznacza to, że oprogramowanie TTP jest gotowe do nowej ramki PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle:** Dojście do interfejsu.
- **aData:** wskaźnik buforu danych PPP, który został zaakceptowany.
- **Packet_id:** Identyfikator pakietu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Odbieranie danych z transmisji za pośrednictwem sieci Ethernet

### <a name="prototype"></a>Prototype

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE uwidacznia tę funkcję w celu odbierania danych do transmisji za pośrednictwem sieci Ethernet

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle:** Dojście do interfejsu.
- **length:** liczba bajtów w aData.
- **aData:** bufor danych zawierający ramkę danych PPP.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```