---
title: Rozdział 3 — Opis usług serwera Azure RTO NetX PPPoE
description: Ten rozdział zawiera opis wszystkich usług serwera usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822506"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Rozdział 3 — Opis usług serwera Azure RTO NetX PPPoE

Ten rozdział zawiera opis wszystkich usług serwera usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_pppoe_server_create**: *Tworzenie wystąpienia serwera PPPoE*

- **nx_pppoe_server_ac_name_set**: *Ustaw nazwę koncentratora dostępu*

- **nx_pppoe_server_delete**: *usuwanie wystąpienia serwera PPPoE*

- **nx_pppoe_server_enable**: *Włączanie usług serwera PPPoE*

- **nx_pppoe_server_disable**: *Wyłącz usługi serwera PPPoE*

- **nx_pppoe_server_callback_notify_set**: *Ustaw funkcje powiadamiania wywołania zwrotnego serwera PPPoE*

- **nx_pppoe_server_service_name_set**: *Ustaw nazwę usługi serwera PPPoE*

- **nx_pppoe_server_session_send**: *Wyślij dane serwera PPPoE do określonej sesji*

- **nx_pppoe_server_session_packet_send**: *Wyślij pakiet serwera PPPoE do określonej sesji*

- **nx_pppoe_server_session_terminate**: *Przerwij określoną sesję PPPoE*

- **nx_pppoe_server_session_get**: *Pobierz informacje o określonej sesji*

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

Ta usługa tworzy wystąpienie serwera PPPoE z udostępnionym przez użytkownika sterownikiem linku dla określonego wystąpienia NetX IP. Jeśli sterownik łącza nie został zainicjowany i włączono, oprogramowanie serwera PPPoE jest odpowiedzialne za Inicjowanie sterownika łącza.

Ponadto aplikacja musi dostarczyć wcześniej utworzoną pulę pakietów dla wystąpienia serwera PPPoE, które ma być używane na potrzeby wewnętrznej alokacji pakietów.

Należy pamiętać, że zwykle dobrym pomysłem jest utworzenie wątku IP NetX o wyższym priorytecie niż priorytet wątku serwera PPPoE. Aby uzyskać więcej informacji na temat określania priorytetu wątku IP, zapoznaj się z usługą *nx_ip_create* .

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **name**: Nazwa tego wystąpienia serwera PPPoE.
- **ip_ptr**: wskaźnik sterowania bloku dla wystąpienia IP.
- **interface_index**: indeks interfejsu.
- **pppoe_link_driver**: Sterownik łącza podany przez użytkownika.
- **pool_ptr**: wskaźnik do puli pakietów.
- **stack_ptr**: wskaźnik do początku obszaru stosu wątku serwera PPPoE.
- **stack_size**: rozmiar w bajtach w stosie wątku.
- **priorytet**: priorytet wewnętrznych wątków serwera PPPoE (1-31).

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślnie utworzono serwer PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) nieprawidłowy serwer PPPoE, adres IP, pulę pakietów lub wskaźnik stosu.
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Nieprawidłowy interfejs.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Nieprawidłowy rozmiar ładunku puli pakietów.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Nieprawidłowy rozmiar pamięci.
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) nieprawidłowy priorytet wątku serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa usuwa wcześniej utworzone wystąpienie serwera PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
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

Włącz usługę serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza usługi serwera PPPoE.

> [!NOTE]
> Ta funkcja musi być wywoływana po *nx_pppoe_server_create* i *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

Wyłącz usługę serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza usługi serwera PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Ustaw funkcje powiadamiania zwrotnego serwera PPPoE 

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
> Ta funkcja musi zostać wywołana przed *nx_pppoe_server_enabl, a* wskaźnik funkcji pppoe_data_receive_notify musi być ustawiony, jeśli nie, *nx_pppoe_server_enable* będzie niepowodzenie.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **pppoe_discover_initiation_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat o rozpoczęciu odnajdywania PPPoE. Jeśli ta wartość jest RÓWNa NULL, funkcja wywołania zwrotnego inicjacji jest wyłączona.
- **pppoe_discover_request_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat żądania odnajdowania PPPoE. Jeśli ta wartość jest RÓWNa NULL, funkcja wywołania zwrotnego żądania wykrywania jest wyłączona.
- **pppoe_discover_terminate_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat zakończenia odnajdywania PPPoE. Jeśli ta wartość jest RÓWNa NULL, funkcja Wykryj zakończenie wywołania zwrotnego jest wyłączona.
- **pppoe_discover_terminate_confirm**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie wysłany komunikat zakończenia odnajdywania PPPoE. Jeśli ta wartość jest RÓWNa NULL, funkcja Wykryj zakończenie wywołania zwrotnego jest wyłączona.
- **pppoe_data_receive_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie odebrany komunikat danych PPPoE. Ta wartość nie może być równa zero.
- **pppoe_data_send_notify**: funkcja aplikacji wywoływana za każdym razem, gdy zostanie wysłany komunikat danych PPPoE. Jeśli ta wartość jest RÓWNa NULL, funkcja wywołania zwrotnego wysyłania danych jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE lub wskaźnik funkcji.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ustaw nazwę koncentratora dostępu

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Opis

Ta funkcja służy do ustawiania wywołania funkcji nazwa koncentratora dostępu.

> [!NOTE]
> Ciąg ac_name musi być zakończony wartością NULL i długość ac_name jest zgodna z długością określoną na liście argumentów.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **ac_name**: Nazwa koncentratora dostępu.
- **ac_name_length**: długość ac_ame.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślnie ustawiono serwer PPPoE.
- **NX_PPPOE_SERVER_PTR_ERROR**: (0XC1) nieprawidłowy serwer PPPoE, adres IP, pulę pakietów lub wskaźnik stosu.
- **NX_SIZE_ERROR**: (0X09) sprawdzanie name_length nie powiodło się.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Ustaw nazwę usługi serwera PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę usługi serwera PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Wyślij dane serwera PPPoE do określonej sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Opis

Ta usługa wysyła ramkę PPPoE przy użyciu określonego identyfikatora sesji.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **session_index**: indeks sesji.
- **data_ptr**: Wskaźnik początku ramki danych serwera PPPoE.
- **data_length**: długość ramki danych serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) usługa serwerowa PPPoE nie jest włączona.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Wyślij pakiet serwera PPPoE do określonej sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet PPPoE przy użyciu określonego identyfikatora sesji.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **session_index**: indeks sesji.
- **packet_ptr**: wskaźnik do pakietu PPPoE.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) nieprawidłowy pakiet serwera PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) usługa serwerowa PPPoE nie jest włączona.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

Przerwij określoną sesję PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Opis

Ta usługa kończy określoną sesję PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **session_index**: indeks sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) usługa serwerowa PPPoE nie jest włączona.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Pobierz informacje o określonej sesji PPPoE

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

- **pppoe_server_ptr**: wskaźnik do bloku kontroli serwera PPPoE.
- **session_index**: indeks sesji.
- **client_mac_msw**: MSW adres fizyczny klienta.
- **client_mac_lsw**: MSW adres fizyczny klienta.
- **session_id**: wskaźnik identyfikatora sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) pomyślne usunięcie serwera PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Nieprawidłowy wskaźnik serwera PPPoE.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Nieprawidłowy indeks sesji PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sesja PPPoE nie została ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Skonfiguruj domyślną nazwę usługi

### <a name="prototype"></a>Prototype

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić programowi TTP skonfigurowanie "domyślnej nazwy usługi", która ma być używana przez protokół PPPoE do filtrowania przychodzących żądań PADI. Oprogramowanie PPPoE powinno pamiętać o tych informacjach i w przypadku odebrania pakietu PADI zawierającego nazwę usługi, która jest zgodna z PppDiscoverReq.

### <a name="input-parameters"></a>Parametry wejściowe

- **Długość**: długość domyślnej nazwy usługi.
- **aData**: domyślna nazwa usługi.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Zdefiniuj pole Nazwa usługi dla pakietu PADO

### <a name="prototype"></a>Prototype

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić programowi TTP Definiowanie pola Nazwa usługi w pakiecie PADO. Oprogramowanie PPPoE nie powinno wysyłać PADO do momentu wywołania PppDiscoverCnf.

Pakiet PADO musi zawierać nazwę koncentratora dostępu (przy użyciu identyfikatora znacznika 0x0102, zgodnie z definicją w RFC2516), zdefiniowaną podczas inicjalizacji oprogramowania PPPoE.

Wiele nazw usług można przekazywać w aData, a każda nazwa powinna być zakończona wartością null.

Znak null jest używany jako separator, aby zapewnić maksymalną elastyczność w przypadku, gdy inne polecenia muszą zostać przesłane jako część nazwy usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **Długość**: długość domyślnej nazwy usługi.
- **aData**: domyślna nazwa usługi.
- **interfaceHandle**: dojście do interfejsu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Oprogramowanie PPPoE będzie uwidaczniać tę funkcję, aby umożliwić oprogramowaniu TTP akceptowanie lub odrzucanie sesji PPPoE.  W odpowiedzi na ten stos PPPoE powinna akceptować połączenie i przypisywać unikatowy numer Session_ID PPPoE skojarzony z interfaceHandle.

### <a name="input-parameters"></a>Parametry wejściowe

- **Zaakceptuj**: NX_TRUE, jeśli połączenie ma zostać zaakceptowane.
- **interfaceHandle**: dojście do interfejsu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić programowi protokołu TTP zamknięcie sesji PPPoE.

Oprogramowanie PPPoE wskaże ciąg kodu przyczyny w tagu Generic-Error (0x0203) w komunikacie PADT

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle**: dojście do interfejsu.
- **causeCode**: pusty ciąg zakończony znakiem null służący do wysyłania informacji o przyczynie zamknięcia połączenia z serwera PPPoE.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Upewnij się, że dojście zostało zwolnione

### <a name="prototype"></a>Prototype

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić oprogramowaniu TTP potwierdzenie, że dojście zostało zwolnione.

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle**: dojście do interfejsu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Zezwalaj na potwierdzenie poprzednich danych PPP

### <a name="prototype"></a>Prototype

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby umożliwić potwierdzenie poprzedzających PppTransmitDataReq.  Oznacza to, że oprogramowanie TTP jest gotowe do nowej ramki PPP z PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle**: dojście do interfejsu.
- **aData**: wskaźnik bufora danych PPP, który został zaakceptowany.
- **Packet_id**: identyfikator pakietu.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Odbieraj dane z przesyłania za pośrednictwem sieci Ethernet

### <a name="prototype"></a>Prototype

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Opis

Oprogramowanie PPPoE udostępni tę funkcję, aby odbierać dane do transmisji za pośrednictwem sieci Ethernet

### <a name="input-parameters"></a>Parametry wejściowe

- **interfaceHandle**: dojście do interfejsu.
- **Długość**: liczba bajtów w aData.
- **aData**: bufor danych zawierający ramkę danych PPP.

### <a name="return-values"></a>Wartości zwrócone

**Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```