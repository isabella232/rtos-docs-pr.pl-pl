---
title: Rozdział 3 — Opis usług serwera DHCP w systemie Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług serwera DHCP w programie NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822009"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a>Rozdział 3 — Opis usług serwera DHCP w systemie Azure RTO NetX Duo

Ten rozdział zawiera opis wszystkich usług serwera DHCP w programie NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

> [!NOTE]
> W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

## <a name="nx_dhcp_server-create"></a>nx_dhcp_server Utwórz

Tworzenie wystąpienia serwera DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera DHCP z wcześniej utworzonym wystąpieniem adresu IP.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że Pula pakietów utworzona dla usługi IP Create ma minimalny 548-bajtowy ładunek, bez uwzględniania nagłówków UDP, IP i Ethernet.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.
- **ip_ptr** Wskaźnik do wystąpienia IP serwera DHCP.
- **stack_ptr** Wskaźnik lokalizacji serwera DHCP na stosie.
- **Stack_size rozmiar input_address_list stosu serwera DHCP** do listy adresów IP serwera
- **Name_ptr wskaźnik do nazwy serwera dhcp** packet_pool_ptr wskaźnik do puli pakietów serwera DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.
- Wystąpił zbyt mały błąd ładunku pakietu **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9)
- Lista opcji serwera **NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) jest pusta
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Tworzenie puli adresów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Opis

Ta usługa tworzy specyficzną dla interfejsu sieciowego pulę dostępnych adresów IP dla określonego serwera DHCP do przypisania. Początkowe i końcowe adresy IP muszą być zgodne z określonym interfejsem sieciowym. Rzeczywista liczba dodanych adresów IP może być mniejsza od łącznego adresu, jeśli lista adresów IP nie jest wystarczająco duża (która jest ustawiana w *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametr konfigurowalny przez użytkownika).

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.
- **iface_index** Indeks odpowiadający interfejsowi sieciowemu
- **start_ip_address** Pierwszy dostępny adres IP
- **end_ip_address** Ostatni dostępny adres IP
- **addresses_added** Liczba adresów IP dodanych do listy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.
- Indeks **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xa1) nie jest zgodny z adresami
- **NX_DHCP_INVALID_IP_ADDRESS_LIST** (0X99) nieprawidłowe dane wejściowe adresu
- Adresy początkowe/końcowe NX_DHCP_INVALID_IP_ADDRESS (0x9B) illogical
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Usuń rekord klienta z bazy danych serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści rekord klienta z bazy danych serwera.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.
- **dhcp_client_ptr wskaźnika do usuwania klienta DHCP**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) nie wywołujący wątku usługi

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Ustawianie parametrów sieci dla opcji DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia wartości domyślne dla parametrów krytycznych dla sieci dla określonego interfejsu. Serwer DHCP będzie uwzględniał te opcje w swojej OFERcie i ACK odpowiedzi do klienta DHCP. Jeśli zestaw parametrów interfejsu hosta, na którym jest uruchomiony serwer DHCP, parametry te są ustawiane domyślnie w następujący sposób: router jest ustawiony na bramę interfejsu podstawowego serwera DHCP, adres serwera DNS do samego serwera DHCP, a maska podsieci, która jest taka sama jak interfejs serwera DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku kontroli serwera DHCP.
- **iface_index** Indeks odpowiadający interfejsowi sieciowemu
- **subnet_mask** Maska podsieci dla sieci klienta
- **default_gateway_address** Adres IP routera klienta
- **dns_server_address** Serwer DNS dla sieci klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera DHCP.
- Indeks **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xa1) nie jest zgodny z adresami
- **NX_DHCP_INVALID_NETWORK_PARAMETERS** (0XA3) nieprawidłowe parametry sieci
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Usuwanie wystąpienia serwera DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie serwera DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie serwera DHCP.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Uruchamianie przetwarzania serwera DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia przetwarzanie serwera DHCP, w tym tworzenie gniazda UDP serwera, powiązanie portu DHCP i oczekiwanie na odbieranie żądań DHCP klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie serwera.
- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP jest już uruchomiony.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Powoduje zatrzymanie przetwarzania serwera DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia zatrzymanie przetwarzania serwera DHCP, który obejmuje otrzymywanie żądań klientów DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zatrzymanie protokołu DHCP.
- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP jest już uruchomiony.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
