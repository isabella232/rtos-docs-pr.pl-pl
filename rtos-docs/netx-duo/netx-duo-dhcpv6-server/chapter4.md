---
title: Rozdział 4 — usługi serwera Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług NetX Duo DHCPv6Server Services
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821931"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Rozdział 4 — usługi serwera Azure RTO NetX Duo

Ten rozdział zawiera opis wszystkich usług NetX Duo DHCPv6Server (wymienionych poniżej).

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- nx_dhcpv6_server_create *utworzyć ServerInstance protokołu DHCPv6*
- nx_dhcpv6_server_delete *usunąć ServerInstance protokołu DHCPv6*
- nx_dhcpv6_server_start *uruchomić zadanie serwera DHCPv6*
- nx_dhcpv6_server_suspend *Wstrzymywanie zadania serwera DHCPv6*
- nx_dhcpv6_server_resume *wznowić przetwarzania klienta DHCPv6*
- nx_dhcpv6_server_suspend *wstrzymywanie przetwarzania klienta DHCPv6*
- nx_dhcpv6_create_dns_address *ustawić serwer DNS dla żądań opcji*
- nx_dhcpv6_create_ip_address_range *utworzyć zakres adresów IP do wydzierżawienia*
- nx_dhcpv6_reserve_ip_address_range *Zarezerwuj zakres adresów IP na liście serwerów*
- nx_dhcpv6_set_server_duid *ustawić identyfikatora DUID serwera dla pakietów DHCPv6*
- nx_dhcpv6_add_ip_address_lease *dodać rekordu dzierżawy do tabeli serwera DHCPv6*
- Nx_dhcpv6_retrieve_ip_address_lease *pobrać rekordu dzierżawy adresów IP z tabeli serwera*
- nx_dhcpv6_add_client_record *dodać rekordu klienta DHCPv6 do tabeli serwera*
- nx_dhcpv6_retrieve_client_record *pobrać rekordu klienta z tabeli serwera*
- nx_dhcpv6_server_interface_set *ustawić indeksu interfejsu dla usług Dhcpv6 serwera*
- nx_dhcpv6_server_option_request_handler_set *ustawić obsługi żądania opcji*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Ustawianie serwera DNS sieci

**Prototype**

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

- **NX_SUCCESS** (0X00) DNS Serversaved do wystąpienia serwera DHCPv6
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) podano nieprawidłowy adres
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

**Prototype**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Opis**

Ta usługa tworzy listę adresów IP określoną przez początkowe i końcowe adresy zakresu adresów, do którego można przypisać serwer. Adresy początkowy i końcowy muszą być zgodne z prefiksem adresu interfejsu serwera (musi być na tym samym linku co interfejs protokołu DHCPv6 serwera). Zwracana jest liczba adresów w rzeczywistości.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **start_ipv6_address** Początek adresów do dodania
- **end_ipv6_address** Koniec adresów do dodania
- ***addresses_added** Dane wyjściowe adresów dodanych

**Wartości zwracane**

- Pomyślnie utworzono listę adresów IP **NX_SUCCESS** (0x00)
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) podano nieprawidłowy adres
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

### <a name="reserve-specified-range-of-ip-addresses"></a>Zarezerwuj określony zakres adresów IP

**Prototype**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Opis**

Ta usługa rezerwuje zakres adresów IP określony przez adres początkowy i końcowy. Te adresy muszą znajdować się w obrębie wcześniej utworzonego zakresu adresów IP serwera. Te adresy nie będą przypisywane do żadnych klientów przez serwer DHCPv6. Adresy początkowy i końcowy muszą być zgodne z prefiksem adresu interfejsu serwera (musi być w tym samym łączu co serwerowy interfejs sieciowy protokołu DHCPv6). Zwracana jest liczba adresów w rzeczywistości zarezerwowanej.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **start_ipv6_address** Początek adresów do zarezerwowania
- **end_ipv6_address** Koniec adresów do zarezerwowania
- ***addresses_reserved** Liczba zarezerwowanych adresów

**Wartości zwracane**

- Komunikat o wersji **NX_SUCCESS** (0x00) został pomyślnie utworzony i przetworzony
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) podano nieprawidłowy adres
- Nie znaleziono adresu początkowego **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) na liście adresów serwera.
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

**Prototype**

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

Ta usługa tworzy zadanie serwera DHCPv6 z określonym danymi wejściowymi. Programy obsługi wywołania zwrotnego są opcjonalnymi danymi wejściowymi. Wymagane są dane wejściowe wskaźnika stosu, wystąpienia protokołu IP i puli pakietów. Należy już utworzyć wystąpienie IP i pulę pakietów.

Użytkownik zachęca do wywoływania nx_dhcpv6_server_option_request_handler_set w celu ustawienia obsługi żądania opcji.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **ip_ptr** Wskaźnik do wystąpienia adresu IP
- **name_str** Wskaźnik do nazwy serwera
- **packet_pool_ptr** Wskaźnik do puli pakietów serwera
- **stack_ptr** Wskaźnik do pamięci stosu serwera
- **stack_size** Rozmiar pamięci stosu serwera
- **dhcpv6_address_declined_handler** Wskaźnik do programu obsługi komunikatów o odrzuceniu lub zwolnieniu klienta
- **dhcpv6_option_request_handler** Procedura obsługi opcji żądania wskaźnika do opcji

**Wartości zwracane**

- Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika
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

**Prototype**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa usuwa zadanie serwera DHCPv6 i wszystkie żądania, które przetworzył serwer.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- Pomyślnie usunięto serwer **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

**Prototype**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa wznawia zadanie serwera DHCPv6 i wszystkie żądania, które przetworzył serwer.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)
- Serwer **NX_DHCPV6_ALREADY_STARTED** (0xE91) jest już uruchomiony
- **stan** błędu (Variable) ThreadX i NetX Duo
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Zawstrzymywanie zadania serwera DHCPv6 

**Prototype**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa zawiesza zadanie serwera DHCPv6 i wszystkie żądania, które przetworzył serwer.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)
- Serwer **NX_DHCPV6_NOT_STARTED** (0xE92) nie został uruchomiony 
- **Stan** błędu (Variable) ThreadX i NetX Duo
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

**Prototype**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Opis**

Ta usługa uruchamia zadanie serwera DHCPv6 i odczytuje serwer, aby przetwarzać żądania aplikacji do otrzymywania komunikatów klienta DHCPv6. Sprawdza, czy wystąpienie serwera ma wystarczające informacje (serwer DUID), tworzy i wiąże gniazdo UDP do wysyłania i otrzymywania komunikatów DHCPv6 oraz aktywuje czasomierze do śledzenia czasu sesji i wygaśnięcia dzierżawy adresów IP.

>[!NOTE] 
> Aby można było uruchomić serwer DHCPv6, aplikacja hosta jest odpowiedzialna za tworzenie zakresu adresów IP, z którego serwer może przypisywać adresy IP. Jest również odpowiedzialny za ustawienie identyfikatora DUID serwera i interfejsu protokołu DHCPv6 (zobacz odpowiednio *nx_dhcpv6_server_duid_set* i *nx_dhcpv6_server_interface_set* .

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)
- Serwer **NX_DHCPV6_ALREADY_STARTED** (0xE91) jest już uruchomiony
- Serwer **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) nie ma adresów do przypisania do dzierżawy
- Nie ustawiono globalnego indeksu adresów **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97)
- **NX_DHCPV6_NO_SERVER_DUID** (0XE92) nie utworzono identyfikatora DUID serwera 
- **stan** błędu (Variable) ThreadX i NetX Duo
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Pobierz dzierżawę adresu IP z tabeli serwerów

**Prototype**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Opis**

Ta usługa pobiera rekord dzierżawy adresu IP z tabeli serwerów w określonej lokalizacji indeksu tabeli. Można to zrobić przed lub po pobraniu danych rekordu klienta.

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6. Nie ma żadnych różnic w kolejności, w jakiej dane dzierżawy adresów IP i dane rekordu klienta są zapisywane w pamięci nieulotnej.

>[!NOTE] 
> Nie zaleca się kopiowania danych do lub z tabel serwerowych bez uprzedniego zatrzymywania ani zawieszania serwera DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **table_index** Indeks tabeli do przechowania dzierżawy w
- **lease_IP_address** Wskaźnik na adres IP dzierżawiony do klienta
- **T1** Klient zażądał czasu odnowienia
- **T2** Klient zażądał ponownego powiązania czasu
- **valid_lifetime** Dzierżawa klienta staje się przestarzała
- **preferred_lifetime** Dzierżawa klienta jest nieprawidłowa

**Wartości zwracane**

- Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)
- **NX_DHCPV6_PARAMETER_ERROR** (0XE93) nieprawidłowe dane wejściowe dzierżawy adresów IP
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Dodawanie dzierżawy adresu IP do tabeli serwerów

**Prototype**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Opis**

Ta usługa ładuje dane dzierżawy protokołu IP z poprzedniej sesji serwera DHCPv6 z nietrwałej pamięci do tabeli dzierżawy serwera. Nie jest to konieczne, jeśli serwer jest uruchomiony po raz pierwszy i nie ma wcześniejszych danych dzierżawy. W takim przypadku aplikacja hosta musi utworzyć zakres adresów IP na potrzeby przypisywania adresów IP przy użyciu usługi *nx_dhcpv6_create_ip_address_range*. Dane są wystarczające do odtworzenia rekordu dzierżawy protokołu DHCPv6. Nie trzeba określać indeksu tabeli. W przypadku ustawienia wartości 0xFFFFFFFF (nieskończoność) serwer DHCPv6 znajdzie następne dostępne miejsce, do którego zostaną skopiowane dane.

>[!NOTE] 
> Przekazywanie danych dzierżawy adresów IP należy wykonać przed przekazaniem rekordów klienta; Oba te elementy należy wykonać przed ponownym uruchomieniem serwera DHCPv6.

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **table_index** Indeks tabeli do przechowania dzierżawy w
- **lease_IP_address** Wskaźnik na adres IP dzierżawiony do klienta
- **T1** Klient zażądał czasu odnowienia
- **T2** Klient zażądał ponownego powiązania czasu
- **valid_lifetime** Dzierżawa klienta staje się przestarzała
- **preferred_lifetime** Dzierżawa klienta jest nieprawidłowa

**Wartości zwracane**

- Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)
- **NX_DHCPV6_TABLE_FULL** (0XEC4) brak miejsca do uzyskania większej ilości danych dzierżawy * *
- Dane dzierżawy **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) nie są dostępne w połączeniu z interfejsem DHCPv6 serwera
- **NX_DHCPV6_PARAM_ERROR** (0XE93) nieprawidłowe dane wejściowe dzierżawy adresów IP
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

### <a name="add-a-client-record-to-the-server-table"></a>Dodawanie rekordu klienta do tabeli serwera

**Prototype**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**Opis**

Ta usługa kopiuje dane klienta z nietrwałej pamięci do tabeli serwera po jednym rekordzie w danym momencie. Jest to konieczne tylko wtedy, gdy serwer jest ponownie uruchamiany i ma dane klienta z poprzedniej sesji w celu przywrócenia z pamięci. Jeśli serwer nie ma wcześniejszych danych, serwer DHCPv6 zainicjuje tabelę klienta, aby umożliwić Dodawanie rekordów klientów.

Nie trzeba określać indeksu tabeli. W przypadku ustawienia wartości 0xFFFFFFFF (nieskończoność) serwer DHCPv6 zlokalizuje następne dostępne miejsce. Serwer DHCPv6 może odtworzyć rekord klienta na podstawie tych danych.

>[!NOTE] 
> Aplikacja hosta musi przekazać dane dzierżawy IP przed rekordem klienta. Jest tak dlatego, że wewnętrznie serwer DHCPv6 może przełączać tabele w taki sposób, aby każdy rekord klienta był przyłączony do odpowiadającego mu rekordu dzierżawy adresów IP w odpowiednich tabelach. Zobacz *nx_dhcpv6_add_ip_address_lease* , aby uzyskać szczegółowe informacje dotyczące przekazywania danych dzierżawy adresów IP z pamięci.

>[!NOTE] 
> W zależności od typu identyfikatora DUID nie wszystkie dane muszą zostać dostarczone. Jeśli na przykład klient ma typ identyfikatora DUID przypisany przez dostawcę, może wysłać wartość zero dla parametrów warstwy łącza identyfikatora DUID (adres MAC, typ sprzętu, czas DUID).

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)
- **NX_ INVALID_PARAMETERS** (0x4D) nieprawidłowe dane wejściowe bez wskaźnika * *
- **NX_DHCPV6_TABLE_FULL** (0XEC4) nie ma pustych miejsc do dodania innego rekordu klienta
- W tabeli dzierżawy serwera nie znaleziono adresu przypisanego przez klienta **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8).
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

### <a name="retrieve-a-client-record-from-the-server-table"></a>Pobieranie rekordu klienta z tabeli serwera

**Prototype**

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

Ta usługa kopiuje podstawowe dane z tabeli rekordów klientów serwera dla magazynu do pamięci nieulotnej. Serwer może odtworzyć odpowiedni rekord klienta z takich danych w procesie odwrotnym (przekazywanie danych do tabeli serwera). Bez względu na typ identyfikatora DUID, żaden ze wskaźników nie może być wskaźnikami ZEROWYmi; dane są inicjowane do zera dla wszystkich parametrów. Na przykład, jeśli typ identyfikatora DUID klienta to warstwa łącza wraz z czasem, numer dostawcy jest zwracany jako zero, a prywatny identyfikator jest ciągiem pustym.

Możliwość przechowywania i pobierania danych między serwerem DHCPv6 a nielotną pamięcią jest wymagana przez protokół DHCPv6. Nie ma żadnych różnic w kolejności, w jakiej dane dzierżawy adresów IP i dane rekordu klienta są zapisywane w pamięci nieulotnej.

>[!NOTE] 
> Nie zaleca się kopiowania danych do lub z tabel serwerowych bez uprzedniego zatrzymywania ani zawieszania serwera DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **table_index** Indeksowanie w tabeli klienta serwera
- **message_xid** Identyfikator transakcji serwera klienta
- **client_address** Adres IPv6 wydzierżawiony do klienta
- **client_state** Stan protokołu DHCPv6 klienta (np. powiązane)
- **IP_lease_time_accrued** Czas wygaśnięcia dzierżawy jest już **dhcpv6_server_ptr** wskaźnikiem do serwera DHCPv6
- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6

**Wartości zwracane**

- Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)
- **NX_DHCPV6_INVALID_DUID** (0xECC) — nieprawidłowe lub niespójne dane identyfikatora DUID
- **NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika
- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

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

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Indeks interfejsu setthe dla interfejsu protokołu DHCPv6 serwera

**Prototype**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Opis**

Ta usługa ustawia interfejs sieciowy, na którym serwer DHCPv6 obsługuje żądania klientów DHCPv6. Nie w przypadku wersji NetX Duo, które nie obsługują wielodostępności, wartość interfejsu jest domyślnie równa zero. Globalny indeks adresów jest potrzebny do uzyskania adresu globalnego serwera w interfejsie DHCPv6. Jest ona używana przez logikę protokołu DHCPv6 do zapewnienia, że adresy dzierżaw i inne dane protokołu DHCPv6 są połączone z serwerem DHCPv6.

Ta funkcja musi zostać wywołana przed uruchomieniem serwera DHCPv6, nawet w przypadku aplikacji na pojedynczych urządzeniach z systemem lub bez pomocy technicznej wieloznacznej.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **iface_index** Interfejs serwera DHCPv6 serwera
- **ga_address_index** Indeks adresu globalnego serwera w tabeli adresów IP serwera

**Wartości zwracane**

- Pomyślnie uruchomiono serwer **NX_SUCCESS** (0x00)
- Interfejs **NX_INVALID_INTERFACE** (0x4C) nie istnieje
- Indeks globalny NX_NO_INTERFACE_ADDRESS (0x50) przekracza maksymalne adresy IPv6 (NX_MAX_IPV6_ADDRESSES) wystąpienia adresu IP
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Ustaw identyfikator DUID serwera dla pakietów DHCPv6

**Prototype**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Opis**

Ta usługa ustawia identyfikator DUID serwera i musi być wywoływana przed uruchomieniem serwera przez aplikację hosta. W przypadku typów identyfikatora DUID warstwy łącza i łącza aplikacja hosta musi podawać dane typu sprzętu i adresu MAC. W przypadku DUIDs warstwy łącza, wskaźnik czasu musi wskazywać prawidłowy czas. Liczba sekund od 1 stycznia 2000 jest typową wartością inicjatora. Jeśli typ identyfikatora DUID serwera to Enterprise, typ przypisany przez dostawcę, identyfikator DUID zostanie utworzony na podstawie opcji konfigurowalnych przez użytkownika NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID i NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, a wartości czasu i adresu MAC można ustawić na wartość NULL.

>[!NOTE] 
> Jest on odpowiedzialny za zapisywanie parametrów identyfikatora DUID serwera w pamięci nieulotnej, tak że używa tego samego identyfikatora DUID w komunikatach dla klientów między ponownymi uruchomieniami. Jest to wymaganie protokołu DHCPv6 (RFC 3315).

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **duid_type** Typ identyfikatora DUID serwera DHCPv6
- **hardware_type** Typ sprzętu (np. Ethernet)
- **mac_address_msw** Wskaźnik do serwera DHCPv6
- **mac_address_lsw** Wskaźnik do serwera DHCPv6
- **czas** Wartość czasu dla identyfikatora DUID

**Wartości zwracane**

- Pomyślnie wstrzymano serwer **NX_SUCCESS** (0x00)
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) nieznany lub nieobsługiwany typ identyfikatora DUID
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Ustaw obsługę żądania opcji dla wystąpienia serwera DHCPv6 

**Prototype**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**Opis**

Ta usługa ustawia procedurę obsługi żądania opcji rozszerzonej serwera DHCPv6.

**Parametry wejściowe**

- **dhcpv6_server_ptr** Wskaźnik do serwera DHCPv6
- **dhcpv6_option_request_handler_extended** Wskaźnik do procedury obsługi żądania opcji rozszerzonych

**Wartości zwracane**

- Pomyślnie wznowiono serwer **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Kod aplikacji

**Przykład**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```