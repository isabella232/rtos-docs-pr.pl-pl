---
title: Rozdział 4 — Azure RTOS serwera DhCPv6 NetX Duo
description: Ten rozdział zawiera opis wszystkich usług NetX Duo DHCPv6Server
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf6b43f70a7159af6c24496ec2ae2276d5e271af2ad3af99687181df3bf6be6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792030"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Rozdział 4 — Azure RTOS serwera DhCPv6 NetX Duo

Ten rozdział zawiera opis wszystkich usług NetX Duo DHCPv6Server (wymienionych poniżej).

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

- nx_dhcpv6_server_create tworzenie *serwera DHCPv6instance*
- nx_dhcpv6_server_delete usuń *serwer DHCPv6wance*
- nx_dhcpv6_server_start uruchom *zadanie serwera DHCPv6*
- nx_dhcpv6_server_suspend *Wstrzymywanie zadania serwera DHCPv6*
- nx_dhcpv6_server_resume *wznawiania przetwarzania klienta DHCPv6*
- nx_dhcpv6_server_suspend *zawieś przetwarzanie klienta DHCPv6*
- nx_dhcpv6_create_dns_address ustawianie *serwera DNS dla żądań opcji*
- nx_dhcpv6_create_ip_address_range Tworzenie *zakresu adresów IP do dzierżawy*
- nx_dhcpv6_reserve_ip_address_range *rezerwy adresów IP na liście serwerów*
- nx_dhcpv6_set_server_duid *ustawić identyfikator DUID serwera dla pakietów DHCPv6*
- nx_dhcpv6_add_ip_address_lease Dodaj *rekord dzierżawy do tabeli serwerów DHCPv6*
- Nx_dhcpv6_retrieve_ip_address_lease pobieranie *rekordu dzierżawy IP z tabeli Serwera*
- nx_dhcpv6_add_client_record dodaj *rekord klienta DHCPv6 do tabeli serwera*
- nx_dhcpv6_retrieve_client_record pobieranie *rekordu klienta z tabeli Serwera*
- nx_dhcpv6_server_interface_set ustawić *indeks interfejsu dla usług DHCPv6 serwera*
- nx_dhcpv6_server_option_request_handler_set *ustawić obsługę żądania opcji*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Ustawianie sieciowego serwera DNS

**Prototyp**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**Opis**

Ta usługa ładuje serwer DHCPv6 z adresem serwera DNS dla interfejsu sieciowego protokołu DHCPv6 serwera.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **dns_ipv6_address** Wskaźnik do serwera DNS

**Wartości zwracane**

- **NX_SUCCESS** (0x00) DNSapisane do wystąpienia serwera DHCPv6
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Podany jest nieprawidłowy adres
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>Tworzenie listy adresów IP serwera

**Prototyp**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Opis**

Ta usługa tworzy listę adresów IP określoną przez adresy startowe i końcowe zakresu adresów, do których można przypisać serwer. Adresy startowe i końcowe muszą być zgodne z prefiksem adresu interfejsu serwera (muszą znajdować się w tym samym linku co interfejs DHCPv6 serwera). Zwracana jest liczba rzeczywiście dodanych adresów.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **start_ipv6_address** Początek adresów do dodania
- **end_ipv6_address** Koniec adresów do dodania
- ***addresses_added** Dodane dane wyjściowe adresów

**Wartości zwracane**

- **NX_SUCCESS** adresu IP 0x00 (0x00)
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Podany jest nieprawidłowy adres
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>Rezerwuj określony zakres adresów IP

**Prototyp**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Opis**

Ta usługa rezerwuje zakres adresów IP określony przez adresy startowe i końcowe. Te adresy muszą znajdować się w wcześniej utworzonym zakresie adresów IP serwera. Te adresy nie zostaną przypisane do żadnych klientów przez serwer DHCPv6. Adresy startowe i końcowe muszą być zgodne z prefiksem adresu interfejsu serwera (muszą znajdować się w tym samym linku co interfejs sieciowy protokołu DHCPv6 serwera). Zwracana jest liczba rzeczywiście zarezerwowanych adresów.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **start_ipv6_address** Początek adresów do zarezerwowania
- **end_ipv6_address** Koniec adresów do zarezerwowania
- ***addresses_reserved** Liczba zarezerwowanych adresów

**Wartości zwracane**

- **NX_SUCCESS** (0x00) RELEASE pomyślnie utworzony i przetworzony
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Podany jest nieprawidłowy adres
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Nie znaleziono adresu początkowego na liście Adres serwera.
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>Tworzenie wystąpienia serwera DHCPv6 

**Prototyp**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**Opis**

Ta usługa tworzy zadanie serwera DHCPv6 z określonymi danych wejściowych. Procedury obsługi wywołania zwrotnego to opcjonalne dane wejściowe. Wymagany jest wskaźnik stosu, wystąpienie adresu IP i dane wejściowe puli pakietów. Wystąpienie adresu IP i pula pakietów muszą już zostać utworzone.

Użytkownik jest zachęcany do wywołania nx_dhcpv6_server_option_request_handler_set, aby ustawić obsługę żądania opcji.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **ip_ptr** Wskaźnik do wystąpienia adresu IP
- **name_str** Wskaźnik do nazwy serwera
- **packet_pool_ptr** Wskaźnik do puli pakietów serwera
- **stack_ptr** Wskaźnik do pamięci stosu serwera
- **stack_size** Rozmiar pamięci stosu serwera
- **dhcpv6_address_declined_handler** Wskaźnik do programu obsługi komunikatów o odmówieniu klienta lub wydaniu
- **dhcpv6_option_request_handler** Wskaźnik do procedury obsługi opcji żądania opcji

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server został pomyślnie wznowiony
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy
- NX_DHCPV6_PARAM_ERROR nieprawidłowe dane wejściowe bez wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>Usuwanie serwera DHCPv6

**Prototyp**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa usuwa zadanie serwera DHCPv6 i wszelkie żądania, które serwer przetwarzał.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully deleted (Serwer usługi NX_SUCCESS (0x00) został pomyślnie usunięty
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>Wznów zadanie serwera DHCPv6 

**Prototyp**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa wznawia zadanie serwera DHCPv6 i wszelkie żądania, które serwer przetwarzał.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully resumed (Serwer 0x00) został pomyślnie wznowiony
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) Server już działa
- **stan** (zmienna) Stan błędu ThreadX i NetX Duo
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Wstrzymywanie zadania serwera DHCPv6 

**Prototyp**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa wstrzymuje zadanie serwera DHCPv6 i wszelkie żądania, które serwer przetwarzał.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully resumed (Serwer 0x00) został pomyślnie wznowiony
- **NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started (Serwer usługi NX_DHCPV6_NOT_STARTED (0xE92) nie jest uruchomiony) 
- **Stan** (zmienna) Stan błędu ThreadX i NetX Duo
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>Uruchamianie zadania serwera DHCPv6 

**Prototyp**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa uruchamia zadanie serwera DHCPv6 i odczytuje serwer do przetwarzania żądań aplikacji w celu odbierania komunikatów klienta DHCPv6. Sprawdza, czy wystąpienie serwera ma wystarczającą ilość informacji (identyfikator DUID serwera), tworzy i wiąże gniazdo UDP do wysyłania i odbierania komunikatów DHCPv6 oraz aktywuje czasomierze do śledzenia czasu sesji i wygaśnięcia dzierżawy IP.

>[!NOTE] 
> Przed uruchomieniem serwera DHCPv6 aplikacja hosta jest odpowiedzialna za utworzenie zakresu adresów IP, z którego serwer może przypisywać adresy IP. Jest on również odpowiedzialny za ustawienie interfejsu DUID serwera i DHCPv6 (zobacz nx_dhcpv6_server_duid_set *i* *nx_dhcpv6_server_interface_set* interfejsu.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully started (Serwer NX_SUCCESS (0x00) został pomyślnie uruchomiony
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) Server już działa
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server nie ma adresów do dzierżawy
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Nie ustawiono globalnego indeksu adresów
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) Nie utworzono żadnych danych DUID serwera 
- **stan** (zmienna) Stan błędu ThreadX i NetX Duo
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Uzyskiwanie dzierżawy adresu IP z tabeli Serwer

**Prototyp**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Opis**

Ta usługa pobiera rekord dzierżawy adresu IP z tabeli Serwer w określonej lokalizacji indeksu tabeli. Można to zrobić przed lub po pobierania danych rekordu klienta.

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 i pamięcią nietrwałą jest wymaganiem protokołu DHCPv6. Nie ma różnicy w tym, jakie dane dzierżawy IP zamówienia i dane rekordu klienta są zapisywane w pamięci nieulotnej.

>[!NOTE] 
> Nie zaleca się kopiowania danych do lub z tabel serwera bez wcześniejszego zatrzymania lub wstrzymania serwera DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **table_index** Indeks tabel do przechowywania dzierżawy
- **lease_IP_address** Wskaźnik na adres IP dzierżawiony do klienta
- **T1** Godzina odnowienia zażądana przez klienta
- **T2** Klient zażądał ponownego wiązania czasu
- **valid_lifetime** Dzierżawa klienta staje się przestarzała
- **preferred_lifetime** Dzierżawa klienta staje się nieprawidłowa

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully started (Serwer NX_SUCCESS (0x00) został pomyślnie uruchomiony
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) Nieprawidłowe dane wejściowe dzierżawy IP
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Dodawanie dzierżawy adresu IP do tabeli Serwer

**Prototyp**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Opis**

Ta usługa ładuje dane dzierżawy IP z poprzedniej sesji serwera DHCPv6 z nietrwałej pamięci do tabeli dzierżawy serwera. Nie jest to konieczne, jeśli serwer jest uruchomiony po raz pierwszy i nie ma żadnych poprzednich danych dzierżawy. W takim przypadku aplikacja hosta musi utworzyć zakres adresów IP do przypisywania adresów IP przy użyciu *nx_dhcpv6_create_ip_address_range* usługi. Dane są wystarczające do odtworzenia rekordu dzierżawy DHCPv6. Nie trzeba określać indeksu tabeli. Jeśli ustawisz 0xFFFFFFFF (nieskończoność), serwer DHCPv6 znajdzie następne dostępne miejsce do skopiowania danych.

>[!NOTE] 
> Przekazywanie danych dzierżawy IP MUSI odbywać się przed przekazaniem rekordów klienta; Oba te tryby MUSZĄ zostać wykonane przed (ponownie)uruchomieniem serwera DHCPv6.

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 i pamięcią nietrwałą jest wymaganiem protokołu DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **table_index** Indeks tabel do przechowywania dzierżawy
- **lease_IP_address** Wskaźnik na adres IP dzierżawiony do klienta
- **T1** Godzina odnowienia zażądana przez klienta
- **T2** Klient zażądał ponownego wiązania czasu
- **valid_lifetime** Dzierżawa klienta staje się przestarzała
- **preferred_lifetime** Dzierżawa klienta staje się nieprawidłowa

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully started (Serwer NX_SUCCESS (0x00) został pomyślnie uruchomiony
- **NX_DHCPV6_TABLE_FULL** (0xEC4) Brak miejsca na więcej danych dzierżawy**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Dane dzierżawy nie są widoczne w linku z interfejsem DHCPv6 serwera
- **NX_DHCPV6_PARAM_ERROR** (0xE93) Nieprawidłowe dane wejściowe dzierżawy IP
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>Dodawanie rekordu Client do tabeli Serwer

**Prototyp**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**Opis**

Ta usługa kopiuje dane klienta z pamięci trwałej do tabeli Serwer po jednym rekordzie na raz. Jest to konieczne tylko wtedy, gdy serwer jest ponownie uruchamiany i ma dane klienta z poprzedniej sesji w celu przywrócenia z pamięci. Jeśli serwer nie ma poprzednich danych, serwer DHCPv6 zaimicjuje tabelę Client, aby móc dodawać rekordy klienta.

Nie trzeba określać indeksu tabeli. Jeśli ustawisz 0xFFFFFFFF (nieskończoność), serwer DHCPv6 zlokalizuje następne dostępne miejsce. Serwer DHCPv6 może odtworzyć rekord klienta na ich pomocą.

>[!NOTE] 
> Aplikacja hosta MUSI przekazać dane dzierżawy IP PRZED rekordem danych klienta. Jest to tak, aby wewnętrznie serwer DHCPv6 można połączyć krzyżowo tabel, tak aby każdy rekord klienta jest sprzężony z odpowiadającym mu rekordem dzierżawy IP w odpowiednich tabelach. Zobacz *nx_dhcpv6_add_ip_address_lease,* aby uzyskać szczegółowe informacje na temat przekazywania danych dzierżawy IP z pamięci.

>[!NOTE] 
> W zależności od typu DUID nie wszystkie dane muszą być dostarczone. Jeśli na przykład klient ma typ DUID przypisany do dostawcy, może wysłać zero dla parametrów warstwy linku DUID (adres MAC, typ sprzętu, czas DUID).

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 i pamięcią nietrwałą jest wymaganiem protokołu DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully started (Serwer NX_SUCCESS (0x00) został pomyślnie uruchomiony
- **NX_ INVALID_PARAMETERS** (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) Brak pustych miejsc do dodawania kolejnego rekordu klienta
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Adres przypisany przez klienta nie można znaleźć w tabeli dzierżawy serwera.
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>Pobieranie rekordu klienta z tabeli Serwer

**Prototyp**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**Opis**

Ta usługa kopiuje podstawowe dane z tabeli rekordów klienta serwera dla magazynu do pamięci trwałej. Serwer może odtworzyć odpowiedni rekord klienta z takich danych w procesie odwrotnym (przekazywania danych do tabeli Serwer). Niezależnie od typu DUID żaden ze wskaźników nie może być wskaźnikiem NULL; Dane są inicjowane do zera dla wszystkich parametrów. Jeśli na przykład typ DUID klienta to Warstwa połączenia plus czas, numer dostawcy jest zwracany jako zero, a prywatny identyfikator jest pustym ciągiem.

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 i pamięcią nietrwałą jest wymaganiem protokołu DHCPv6. Nie ma różnicy w tym, jakie dane dzierżawy IP zamówienia i dane rekordu klienta są zapisywane w pamięci nieulotnej.

>[!NOTE] 
> Nie zaleca się kopiowania danych do lub z tabel serwera bez wcześniejszego zatrzymania lub wstrzymania serwera DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **table_index** Indeksowanie w tabeli klienta serwera
- **message_xid** Identyfikator transakcji serwera klienta
- **client_address** Adres IPv6 dzierżawiony klientowi
- **client_state** Stan protokołu DHCPv6 klienta (np. powiązany)
- **IP_lease_time_accrued** Czas wygaśnięcia dzierżawy już **dhcpv6_server_ptr** wskaźnik do serwera DHCPv6
- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully started (Serwer NX_SUCCESS (0x00) został pomyślnie uruchomiony
- **NX_DHCPV6_INVALID_DUID** (0xECC) Nieprawidłowe lub niespójne dane DUID
- **NX_PTR_ERROR** (0x16) Nieprawidłowe dane wejściowe wskaźnika
- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Ustawianie indeksu interfejsu dla interfejsu DHCPv6 serwera

**Prototyp**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Opis**

Ta usługa ustawia interfejs sieciowy, w którym serwer DHCPv6 obsługuje żądania klienta DHCPv6. Nie jest tak w przypadku wersji NetX Duo, które nie obsługują wieloadresowych aplikacji wieloadresowych, wartość interfejsu jest domyślnie równa zero. Globalny indeks adresów jest niezbędny do uzyskania adresu globalnego serwera w interfejsie DHCPv6. Jest on używany przez logikę DHCPv6 w celu zapewnienia, że adresy dzierżawy i inne dane DHCPv6 są nawiązać połączenie z serwerem DHCPv6.

Ta funkcja musi być wywoływana przed rozpoczęciem pracy serwera DHCPv6, nawet w przypadku aplikacji na urządzeniach jednoadresowych lub bez obsługi wielu firm.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **iface_index** Interfejs serwera DHCPv6 serwera
- **ga_address_index** Indeks globalnego adresu serwera w tabeli adresów IP serwera

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully started (Serwer NX_SUCCESS (0x00) został pomyślnie uruchomiony
- **NX_INVALID_INTERFACE** (0x4C) Interface does not exist (Interfejs NX_INVALID_INTERFACE (0x4C) nie istnieje
- NX_NO_INTERFACE_ADDRESS (0x50) Indeks globalny przekracza maksymalną liczbę adresów IPv6 wystąpienia ip (NX_MAX_IPV6_ADDRESSES)
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Ustawianie identyfikatorów DUID serwera dla pakietów DHCPv6

**Prototyp**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Opis**

Ta usługa ustawia nazwę DUID serwera i musi zostać wywołana przed rozpoczęciem serwera przez aplikację hosta. W przypadku typów DUID warstwy łącza i warstwy łącza czasu aplikacja hosta musi podać typ sprzętu i dane adresów MAC. W przypadku identyfikatorów DUID czasu warstwy łącza wskaźnik czasu musi wskazać prawidłowy czas. Liczba sekund od 1 stycznia 2000 r. jest typową wartością iniekcyjną. Jeśli typ DUID serwera to przedsiębiorstwo, typ przypisany przez dostawcę, identyfikator DUID zostanie utworzony na podstawie konfigurowalnych przez użytkownika opcji NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID i NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, a wartości czasu i adresu MAC można ustawić na NULL.

>[!NOTE] 
> Aplikacja hosta jest odpowiedzialna za zapisywanie parametrów DUID serwera w pamięci nieulotnej w taki sposób, że używa tego samego duid w komunikatach do klientów między ponownymi rozruchami. Jest to wymagane przez protokół DHCPv6 (RFC 3315).

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **duid_type** Typ DUID serwera DHCPv6
- **hardware_type** Typ sprzętu (np. Ethernet)
- **mac_address_msw** Wskaźnik do serwera DHCPv6
- **mac_address_lsw** Wskaźnik do serwera DHCPv6
- **czas** Wartość czasu dla duid

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully suspended (Serwer NX_SUCCESS (0x00) został pomyślnie zawieszony
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Nieznany lub nieobsługiwany typ DUID
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Ustawianie procedury obsługi żądań opcji dla wystąpienia serwera DHCPv6 

**Prototyp**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**Opis**

Ta usługa ustawia program obsługi żądań opcji rozszerzonej DHCPv6 Server.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **dhcpv6_option_request_handler_extended** Wskaźnik do procedury obsługi żądań opcji rozszerzonych

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Server successfully resumed (Serwer 0x00) został pomyślnie wznowiony
- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```