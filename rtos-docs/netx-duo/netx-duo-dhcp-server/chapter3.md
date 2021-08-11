---
title: Rozdział 3 — opis Azure RTOS serwera DHCP NetX Duo
description: Ten rozdział zawiera opis wszystkich usług serwera DHCP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8496d9158c06e79ed86cb2f09ed9986a4eae5ed176352ff01c317df9f2399127
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788443"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a>Rozdział 3 — opis Azure RTOS serwera DHCP NetX Duo

Ten rozdział zawiera opis wszystkich usług serwera DHCP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

> [!NOTE]
> W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

## <a name="nx_dhcp_server-create"></a>nx_dhcp_server tworzenia

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
> Aplikacja musi upewnić się, że pula pakietów utworzona dla usługi tworzenia adresów IP ma ładunek o rozmiarze co najmniej 548 bajtów, bez uwzględnienia nagłówków UDP, IP i Ethernet.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania serwera DHCP.
- **ip_ptr** Wskaźnik do wystąpienia adresu IP serwera DHCP.
- **stack_ptr** Lokalizacja stosu serwera DHCP wskaźnika.
- **stack_size stosu serwera DHCP input_address_list** wskaźnik do listy adresów IP serwera
- **name_ptr wskaźnik do nazwy serwera DHCP packet_pool_ptr** wskaźnik do puli pakietów serwera DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DHCP.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Błąd Zbyt mały ładunek pakietu
- **NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Lista opcji serwera jest pusta
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.
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

Ta usługa tworzy specyficzną dla interfejsu sieciowego pulę dostępnych adresów IP dla określonego serwera DHCP do przypisania. Adresy IP początku i końca muszą być zgodne z określonym interfejsem sieciowym. Rzeczywista liczba dodanych adresów IP może być mniejsza niż *łączna* liczba adresów, jeśli lista adresów IP nie jest wystarczająco duża (co jest ustawiane w konfigurowalnym przez użytkownika NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE parametru).

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania serwera DHCP.
- **iface_index** Indeks odpowiadający interfejsowi siecioweowi
- **start_ip_address** Pierwszy dostępny adres IP
- **end_ip_address** Ostatni z dostępnych adresów IP
- **addresses_added** Liczba adresów IP dodanych do listy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DHCP.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Indeks nie jest zgodne z adresami
- **NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Nieprawidłowe dane wejściowe adresu
- NX_DHCP_INVALID_IP_ADDRESS (0x9B) Nielogiczne adresy rozpoczęcia/zakończenia
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

Usuwanie rekordu klienta z bazy danych serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyczyści rekord Client z bazy danych serwera.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania serwera DHCP.
- **dhcp_client_ptr do klienta DHCP do usunięcia**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DHCP.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) Niewątkowy wywołujący usługę

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

Ta usługa ustawia wartości domyślne parametrów krytycznych dla sieci dla określonego interfejsu. Serwer DHCP uwzględni te opcje w odpowiedziach OFFER i ACK na klienta DHCP. Jeśli host ustawi parametry interfejsu, na których jest uruchomiony serwer DHCP, parametry zostaną domyślne w następujący sposób: router ustawi bramę interfejsu podstawowego dla samego serwera DHCP, adres serwera DNS na sam serwer DHCP i maskę podsieci na taką samą jak skonfigurowany interfejs serwera DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania serwera DHCP.
- **iface_index** Indeks odpowiadający interfejsowi siecioweowi
- **subnet_mask** Maska podsieci dla sieci klienta
- **default_gateway_address** Adres IP routera klienta
- **dns_server_address** Serwer DNS dla sieci klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DHCP.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Indeks nie jest zgodne z adresami
- **NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Nieprawidłowe parametry sieci
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

Ta usługa usuwa utworzone wcześniej wystąpienie serwera DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie serwera DHCP.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

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

Ta usługa uruchamia przetwarzanie serwera DHCP, co obejmuje tworzenie gniazda UDP serwera, powiązanie portu DHCP i oczekiwanie na odbieranie żądań DHCP klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uruchomienie serwera.
- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP jest już uruchomiony.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Zatrzymuje przetwarzanie serwera DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje przetwarzanie serwera DHCP, w tym odbieranie żądań klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie protokołu DHCP.
- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP jest już uruchomiony.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.
- NX_DHCP_PARAMETER_ERROR (0x92) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
