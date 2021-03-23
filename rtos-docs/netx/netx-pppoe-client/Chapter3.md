---
title: Rozdział 3 — Opis usług klienta RTO NetX PPPoE platformy Azure
description: Ten rozdział zawiera opis wszystkich usług klienta usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821493"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Rozdział 3 — Opis usług klienta RTO NetX PPPoE platformy Azure

Ten rozdział zawiera opis wszystkich usług klienta usługi Azure RTO NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_pppoe_client_create** *utworzyć wystąpienia klienta PPPoE*
- **nx_pppoe_client_delete** *usunąć wystąpienia klienta PPPoE*
- **nx_pppoe_client_host_uniq_set** *ustawić hosta unikatowego dla klienta PPPoE*
- **nx_pppoe_client_host_uniq_set_extended** *ustawić hosta unikatowego dla klienta PPPoE*
- **nx_pppoe_client_service_name_set** *ustawić nazwę usługi dla klienta PPPoE*
- **nx_pppoe_client_service_name_set_extended** *ustawić nazwę usługi dla klienta PPPoE*
- **nx_pppoe_client_session_connect** *łączenie sesji klienta PPPoE z serwerem PPPoE*
- **nx_pppoe_client_session_packet_send** *wysłać pakietu sesji PPPoE*
- **nx_pppoe_client_session_terminate** *przerywanie sesji PPPoE*
- **nx_pppoe_client_session_get** *uzyskać określonego pliku inf sesji PPPoE*

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

Tworzenie wystąpienia klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta PPPoE z dostarczonym przez użytkownika sterownikiem linku dla określonego wystąpienia NetX IP. Jeśli sterownik łącza nie został zainicjowany i włączono, oprogramowanie klienckie PPPoE jest odpowiedzialne za Inicjowanie sterownika łącza.

Ponadto aplikacja musi dostarczyć wcześniej utworzoną pulę pakietów dla wystąpienia klienta PPPoE, które ma być używane na potrzeby wewnętrznej alokacji pakietów.

> [!NOTE]
> Ogólnie dobrym pomysłem jest utworzenie wątku IP NetX o wyższym priorytecie niż priorytet wątku klienta PPPoE. Aby uzyskać więcej informacji na temat określania priorytetu wątku IP, zapoznaj się z usługą *nx_ip_create* .

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **Nazwa** Nazwa tego wystąpienia klienta PPPoE.
 - **ip_ptr** Wskaźnik sterowania blokiem dla wystąpienia IP.
 - **interface_index** Indeks interfejsu.
 - **pool_ptr** Wskaźnik do puli pakietów.
 - **stack_ptr** Wskaźnik do początku obszaru stosu wątku klienta PPPoE.
 - **stack_size** Rozmiar w bajtach w stosie wątku.
 - **priorytet** Priorytet wewnętrznych wątków klienta PPPoE (1-31).
 - **pppoe_link_driver** Sterownik linku dostarczony przez użytkownika.
 - **pppoe_packet_receive** Funkcja odbierania pakietów dostarczonych przez użytkownika.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie utworzono klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) nieprawidłowy klient PPPoE, adres IP, Pula pakietów lub wskaźnik stosu.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Nieprawidłowy interfejs.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Nieprawidłowy rozmiar ładunku puli pakietów.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Nieprawidłowy rozmiar pamięci.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) nieprawidłowy priorytet wątku klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

Usuwanie wystąpienia klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa poprzednio utworzone wystąpienie klienta PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślne usunięcie klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

Ustaw unikatowy Host klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Opis

Ta usługa ustawia unikatowy Host klienta PPPoE. Host-Uniq jest używana przez hosta do unikatowego kojarzenia koncentratora dostępu z określonym żądaniem hosta.
Mogą to być dane binarne dowolnej wartości i długości wybranych przez hosta.

> [!NOTE]
> unikatowy host musi mieć ciąg zakończony znakiem null.

> [!NOTE]
> Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_pppoe_client_host_uniq_set_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **host_uniq** Na hoście unikatowym wskaźnikiem. Unikatowy host musi mieć ciąg zakończony znakiem null.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiony unikatowy Host klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Ustaw unikatowy Host klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Opis

Ta usługa ustawia unikatowy Host klienta PPPoE. Host-Uniq jest używana przez hosta do unikatowego kojarzenia koncentratora dostępu z określonym żądaniem hosta.
Mogą to być dane binarne dowolnej wartości i długości wybranych przez hosta.

> [!NOTE]
> unikatowy host musi mieć ciąg zakończony znakiem null.

> [!NOTE]
> Ta usługa zastępuje *nx_pppoe_client_host_uniq_set ()*. Ta wersja dostarcza dodatkowe informacje o długości do usługi.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **host_uniq** Na hoście unikatowym wskaźnikiem. Unikatowy host musi mieć ciąg zakończony znakiem null.
 - **host_uniq_length** Długość host_uniq

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiony unikatowy Host klienta PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - Sprawdzanie **NX_SIZE_ERROR** (0x09) nie powiodło się host_uniq_length

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Ustaw nazwę usługi klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę usługi klienta PPPoE. Service-Name wskazujący usługę żądaną przez hosta. Jeśli nie ustawiono Service-Name, oznacza to, że host będzie akceptować dowolną liczbę usług.

> [!NOTE]
> Nazwa usługi musi być ciągiem zakończonym wartością null

> [!NOTE]
> Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_pppoe_client_service_name_set_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **service_name** Wskaźnik na nazwę usługi. Nazwa usługi musi mieć ciąg zakończony znakiem null.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiono nazwę usługi klienta PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Ustaw nazwę usługi klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę usługi klienta PPPoE. Service-Name wskazujący usługę żądaną przez hosta. Jeśli nie ustawiono Service-Name, oznacza to, że host będzie akceptować dowolną liczbę usług.

> [!NOTE]
> Nazwa usługi musi mieć ciąg zakończony znakiem null.

> [!NOTE]
> Ta usługa zastępuje *nx_pppoe_client_service_name_set ()*. Ta wersja dostarcza dodatkowe informacje o długości nazwy usługi do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **service_name** Wskaźnik na nazwę usługi. Nazwa usługi musi mieć ciąg zakończony znakiem null.
 - **service_name_length** Długość service_name

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślnie ustawiono nazwę usługi klienta PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - Sprawdzanie **NX_SIZE_ERROR** (0x09) nie powiodło się service_name_length

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Łączenie sesji klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa umożliwia połączenie sesji PPPoE przy użyciu wcześniej utworzonego klienta PPPoE z określonym serwerem PPPoE.

> [!NOTE]
> Ta funkcja musi być wywoływana po *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* i *nx_pppoe_client_service_name_set*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **WAIT_OPTION** Opcja oczekiwania podczas ustanawiania połączenia.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) pomyślna sesja klienta z klientem PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Wyślij pakiet klienta PPPoE do określonej sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet PPPoE przy użyciu określonego identyfikatora sesji.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **packet_ptr** Wskaźnik na pakiet PPPoE.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) pomyślne wysłanie pakietu klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) nieprawidłowy pakiet klienta PPPoE.
 - Sesja PPPoE NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) nie została ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Przerwij sesję klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa kończy określoną sesję PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku kontroli klienta PPPoE.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) pomyślna przerwa sesja klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

Pobierz informacje o określonej sesji PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Opis

Ta usługa pobiera określone informacje o sesji PPPoE, adres fizyczny serwera i identyfikator sesji.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_server_ptr** Wskaźnik do bloku kontroli klienta PPPoE.
 - **server_mac_msw** Wskaźnik MSW adresu fizycznego serwera.
 - **server_mac_lsw** Wskaźnik MSW adresu fizycznego serwera.
 - **session_id** Wskaźnik identyfikatora sesji.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) pomyślna sesja klienta PPPoE get.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - Sesja PPPoE NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) nie została ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
