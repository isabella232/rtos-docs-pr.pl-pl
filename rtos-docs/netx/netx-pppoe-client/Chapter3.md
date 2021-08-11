---
title: Rozdział 3 — Opis Azure RTOS klienta NetX PPPoE
description: Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8310006b7c188fa63402c931459ffd84ebb776c207dc520959208449862fe27f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790211"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Rozdział 3 — Opis Azure RTOS klienta NetX PPPoE

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX PPPoE (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_pppoe_client_create** *tworzenie wystąpienia klienta PPPoE*
- **nx_pppoe_client_delete** *klienta PPPoE*
- **nx_pppoe_client_host_uniq_set** *ustawić hosta unikatowego dla klienta PPPoE*
- **nx_pppoe_client_host_uniq_set_extended** *ustawić hosta unikatowego dla klienta PPPoE*
- **nx_pppoe_client_service_name_set** *ustaw nazwę usługi dla klienta PPPoE*
- **nx_pppoe_client_service_name_set_extended** *ustaw nazwę usługi dla klienta PPPoE*
- **nx_pppoe_client_session_connect** *Połączenie klienta PPPoE z serwerem PPPoE*
- **nx_pppoe_client_session_packet_send** *wysyłania pakietów sesji PPPoE*
- **nx_pppoe_client_session_terminate** *zakończenie sesji PPPoE*
- **nx_pppoe_client_session_get** *pobrać określoną sesję PPPoE inf*

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

Ta usługa tworzy wystąpienie klienta PPPoE z dostarczonym przez użytkownika sterownikem łącza dla określonego wystąpienia adresu IP NetX. Jeśli sterownik łącza nie został zainicjowany i włączony, oprogramowanie klienta PPPoE jest odpowiedzialne za inicjowanie sterownika łącza.

Ponadto aplikacja musi podać wcześniej utworzoną pulę pakietów dla wystąpienia klienta PPPoE do użycia na użytek wewnętrznej alokacji pakietów.

> [!NOTE]
> Ogólnie dobrym pomysłem jest utworzenie wątku ip NetX o wyższym priorytecie niż priorytet wątku klienta PPPoE. Zapoznaj się z *usługą nx_ip_create,* aby uzyskać więcej informacji na temat określania priorytetu wątku ip.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **name (nazwa)** Nazwa tego wystąpienia klienta PPPoE.
 - **ip_ptr** Wskaźnik do bloku sterowania dla wystąpienia adresu IP.
 - **interface_index** Indeks interfejsu.
 - **pool_ptr** Wskaźnik do puli pakietów.
 - **stack_ptr** Wskaźnik do początku obszaru stosu wątku klienta PPPoE.
 - **stack_size** Rozmiar w bajtach w stosie wątku.
 - **priorytet** Priorytet wewnętrznych wątków klienta PPPoE (1–31).
 - **pppoe_link_driver** Sterownik linku podany przez użytkownika.
 - **pppoe_packet_receive** Funkcja odbierania pakietów dostarczonych przez użytkownika.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Pomyślne utworzenie klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy klient PPPoE, adres IP, pula pakietów lub wskaźnik stosu.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Nieprawidłowy interfejs.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Nieprawidłowy rozmiar ładunku puli pakietów.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Nieprawidłowy rozmiar pamięci.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Nieprawidłowy priorytet wątku klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

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

Ta usługa usuwa wcześniej utworzone wystąpienie klienta PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Pomyślne usunięcie klienta PPPoE.
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

Ustawianie unikatowego hosta klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Opis

Ta usługa ustawia unikatowy host klienta PPPoE. Host-Uniq jest używany przez hosta do unikatowego skojarzenia z określonym żądaniem hosta.
Mogą to być dane binarne o dowolnej wartości i długości wybieranej przez hosta.

> [!NOTE]
> Unikatowy host musi być ciągiem zakończonym z wartością Null.

> [!NOTE]
> Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_pppoe_client_host_uniq_set_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **host_uniq** Wskaźnik do hosta jest unikatowy. Unikatowy host musi być ciągiem z zakończeniem o wartości Null.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Unikatowy zestaw pomyślnego hosta klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Ustawianie unikatowego hosta klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Opis

Ta usługa ustawia unikatowy host klienta PPPoE. Host-Uniq jest używany przez hosta do unikatowego skojarzenia z określonym żądaniem hosta.
Mogą to być dane binarne o dowolnej wartości i długości wybieranej przez hosta.

> [!NOTE]
> Unikatowy host musi być ciągiem zakończonym z wartością Null.

> [!NOTE]
> Ta usługa zastępuje *nx_pppoe_client_host_uniq_set()*. Ta wersja dostarcza do usługi dodatkowe informacje o długości.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **host_uniq** Wskaźnik do hosta jest unikatowy. Unikatowy host musi być ciągiem z zakończeniem o wartości Null.
 - **host_uniq_length** Długość host_uniq

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Unikatowy zestaw pomyślnego hosta klienta PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - **NX_SIZE_ERROR** (0x09) Sprawdzanie host_uniq_length niepowodzeniem

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Ustawianie nazwy usługi klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę usługi klienta PPPoE. Komunikat Service-Name wskazujący usługę żądaną przez hosta. Jeśli Service-Name nie jest ustawiona, oznacza to, że host będzie akceptował dowolną liczbę usług.

> [!NOTE]
> Nazwa usługi musi być ciągiem zakończonym z wartością null

> [!NOTE]
> Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_pppoe_client_service_name_set_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **service_name** Wskaźnik do nazwy usługi. Nazwa usługi musi być ciągiem zakończonym z wartością Null.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set (Pomyślna nazwa usługi klienta PPPoE).
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Ustawianie nazwy usługi klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę usługi klienta PPPoE. Komunikat Service-Name wskazujący usługę żądaną przez hosta. Jeśli Service-Name nie jest ustawiona, oznacza to, że host będzie akceptował dowolną liczbę usług.

> [!NOTE]
> Nazwa usługi musi być ciągiem zakończonym wartością null.

> [!NOTE]
> Ta usługa zastępuje *nx_pppoe_client_service_name_set()*. Ta wersja dostarcza do funkcji dodatkowe informacje o długości nazwy usługi.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **service_name** Wskaźnik do nazwy usługi. Nazwa usługi musi być ciągiem zakończonym z wartością Null.
 - **service_name_length** Długość service_name

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set (Pomyślna nazwa usługi klienta PPPoE).
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - **NX_SIZE_ERROR** (0x09) Sprawdzanie service_name_length niepowodzeniem

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Połączenie Sesja klienta PPPoE

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

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **wait_option** Opcja Czekaj podczas nawiązynia połączenia.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Pomyślne połączenie sesji klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Wysyłanie pakietu klienta PPPoE do określonej sesji

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet PPPoE przy użyciu określonego identyfikatora sesji.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **packet_ptr** Wskaźnik do pakietu PPPoE.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Pomyślne wysłanie pakietu klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Nieprawidłowy pakiet klienta PPPoE.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE nie jest ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Zakończenie sesji klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa kończy określoną sesję PPPoE.

### <a name="input-parameters"></a>Parametry wejściowe

 - **pppoe_client_ptr** Wskaźnik do bloku sterowania klienta PPPoE.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Pomyślne zakończenie sesji klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

Uzyskiwanie informacji o określonej sesji PPPoE

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

 - **pppoe_server_ptr** Wskaźnik do bloku sterowania klienta PPPoE.
 - **server_mac_msw** Wskaźnik MSW adresu fizycznego serwera.
 - **server_mac_lsw** Wskaźnik MSW adresu fizycznego serwera.
 - **session_id** Wskaźnik identyfikatora sesji.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Pomyślne uzyskiwanie sesji klienta PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Nieprawidłowy wskaźnik klienta PPPoE.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE nie jest ustanowiona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
