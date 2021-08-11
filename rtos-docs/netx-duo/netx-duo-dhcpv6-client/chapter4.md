---
title: Rozdział 4 — Azure RTOS klienta DhCPv6 NetX Duo
description: Ten rozdział zawiera opis wszystkich usług klienta Azure RTOS NetX Duo DHCPv6 (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6caf943f990f8fe5cbd2cd6139a1253fcaf47dc207141963e31a9e31864ef839
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791741"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Rozdział 4 — Azure RTOS klienta DhCPv6 NetX Duo

Ten rozdział zawiera opis wszystkich usług klienta Azure RTOS NetX Duo DHCPv6 (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_dhcpv6_client_create: tworzenie** *wystąpienia klienta DHCPv6* 

- **nx_dhcpv6_client_delete:** *usuwanie wystąpienia klienta DHCPv6* 

- **nx_dhcpv6_create_ client_duid: tworzenie** *duidu klienta DHCPv6* 

- **nx_dhcpv6 _add_client_ia:** dodawanie adresu tożsamości klienta *(IA) DHCPv6* 

- **nx_dhcpv6 _create_client_ia:** ( Starsza wersja dodawania adresu tożsamości klienta *DHCPv6 (IA))* 

- **nx_dhcpv6_create_client_iana: tworzenie** *skojarzenia tożsamości klienta DHCPv6 dla adresów nie tymczasowych (IANA)* 

- **nx_dhcpv6_get_client_duid_time_id:** pobierz identyfikator czasu z identyfikatora DUID klienta *DHCPv6* 

- **nx_dhcpv6_client_set_interface: ustaw** *interfejs sieciowy klienta na komunikację z serwerem DHCPv6* 

- **nx_dhcpv6_get_IP_address:** *uzyskiwanie globalnego adresu IPv6 przypisanego do klienta DHCPv6* 

- **nx_dhcpv6_get_lease_time_data: Uzyskiwanie** *T1, T2, prawidłowych* i preferowanych okresów istnienia dla globalnego adresu IPv6 klienta

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *uzyskiwanie T1, T2,* prawidłowych i preferowanych okresów istnienia dla adresu IPv6 klienta DHCPv6 według indeksu adresów 

- **nx_dhcpv6_get_iana_lease_time: uzyskiwanie** T1 i T2 w skojarzenia tożsamości (IANA) dzierżawionych *do klienta DHCPv6* 

- **nx_dhcpv6_get_other_option_data:** *Pobierz dane określonej opcji, np.* nazwę domeny lub serwer strefy czasowej 

- **nx_dhcpv6_get_DNS_server_address:** *pobierz adres serwera DNS o określonym indeksie do listy serwerów DNS klienta DHCPv6* 

- **nx_dhcpv6_get_time_accrued:** Uzyskiwanie czasu, przez który globalna dzierżawa adresu IPv6 została powiązana *z klientem DHCPv6* 

- **nx_dhcpv6_get_time_server_address:** pobierz adres serwera czasu w określonym indeksie na listę serwerów czasu klienta *DHCPv6*

- **nx_dhcpv6_get_valid_ip_address_count:** *uzyskiwanie liczby adresów IPv6 przypisanych do klienta DHCPv6* 

- **nx_dhcpv6_reinitialize:** ponowne zainicjowanie protokołu DHCPv6 w celu ponownego uruchomienia maszyny stanu klienta DHCPv6 i ponownego uruchomienia protokołu *DHCPv6* 

- **nx_dhcpv6_request_confirm:** *Wyślij żądanie POTWIERDŹ do serwera* 

- **nx_dhcpv6_request_inform_request:** Zakończ *komunikat INFORM REQUEST na serwerze* 

- **nx_dhcpv6_request_release:** *Wyślij żądanie RELEASE do serwera* 

- **nx_dhcpv6_request_option_DNS_server:** *Dodaj opcję serwera DNS* do opcji Klient żądaj danych w komunikatach żądań do serwera 

- **nx_dhcpv6_request_option_FQDN:** *Dodaj opcję FQDN* do opcji Klient żądaj danych w komunikatach żądań do serwera 

- **nx_dhcpv6_request_option_domain_name:** Dodaj opcję nazwy domeny do opcji Klient żądaj *danych w komunikatach żądań do serwera* 

- **nx_dhcpv6_request_option_time_server:** Dodaj opcję serwera czasu do opcji *Klient żądaj danych w komunikatach żądań do serwera* 

- **nx_dhcpv6_request_option_timezone:** Dodaj opcję strefy czasowej do opcji *Klient żądaj danych w komunikatach żądań do serwera* 

- **nx_dhcpv6_request_solicit: Wyślij** *żądanie DHCPv6 SOLICIT do dowolnego serwera w sieci klienta (emisji)* 

- **nx_dhcpv6_request_solicit_rapid: Wyślij** *żądanie SOLICIT DHCPv6* do dowolnego serwera w sieci klienta (emisji) z zestawu opcji szybkie zatwierdzanie 

- **nx_dhcpv6_resume: Wznawianie** *przetwarzania klienta DHCPv6* 

- **nx_dhcpv6_start:** *Uruchom zadanie wątku klienta DHCPv6. Należy zauważyć, że nie jest to równoważne uruchamianiu maszyny stanu DHCPv6* i nie wysyła żądania SOLICIT 

- **nx_dhcpv6_stop: Zatrzymaj** *zadanie wątku klienta DHCPv6* 

- **nx_dhcpv6_suspend:** *Wstrzymywanie zadania wątku klienta DHCPv6* 

- **nx_dhcpv6_set_time_accrued:** ustaw czas naliczany w globalnej dzierżawie adresu *IPv6 klienta w rekordzie Klient.*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

Tworzenie wystąpienia klienta DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta DHCPv6, w tym funkcje wywołania zwrotnego.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do bloku sterowania DHCPv6  

- **ip_ptr** Wskaźnik do wystąpienia adresu IP klienta  

- **name_ptr** Wskaźnik do nazwy wystąpienia DHCPv6

- **packet_pool_ptr** Wskaźnik do puli pakietów klienta

- **stack_ptr** Wskaźnik do pamięci stosu klienta

- **stack_size** Rozmiar pamięci stosu klienta

- **dhcpv6_state_change_notify** Wskaźnik do funkcji wywołania zwrotnego wywoływanej, gdy klient inicjuje nowe żądanie DHCPv6 do serwera

- **dhcpv6_server_error_handler** Wskaźnik do funkcji wywołania zwrotnego wywoływanej, gdy klient otrzymuje stan błędu z serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

Usuwanie wystąpienia klienta DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta DHCPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie protokołu DHCPv6

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

Zestawy interfejsu sieciowego klienta dla DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Opis

Ta usługa ustawia interfejs sieciowy klienta do komunikacji z serwerami DHCPv6 na określony indeks interfejsu wejściowego.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **interface_index** Indeks wskazujący interfejs sieciowy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Interface successfully set

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowe dane wejściowe indeksu interfejsu

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

Ustawia adres docelowy, do którego ma zostać wysłany komunikat DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres docelowy, do którego ma zostać wysłany komunikat DHCPv6. Domyślnie jest to ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **destination_address** Adres docelowy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Interfejs został pomyślnie ustawiony

- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

- NX_DHCPV6_PARAM_ERROR (0xE93) Parament

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

Tworzenie obiektu DUID klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Opis

Ta usługa tworzy duid klienta z parametrami wejściowymi. Jeśli dane wejściowe czasu nie zostaną podane, a typ duid wskazuje warstwę łącza z czasem, ta funkcja będzie dostarczać czas, który zawiera współczynnik losowania dla unikatowości. Typy duid przypisane do dostawcy (enterprise) nie są obsługiwane.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **duid_type** Typ duidu (sprzęt, przedsiębiorstwo itp.)

- **hardware_type** Sprzęt sieciowy, np. IEEE 802

- **czas** Wartość używana do tworzenia unikatowego identyfikatora

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie utworzono duid klienta

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID nieznany lub nie jest obsługiwany 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID nieznany lub nie jest obsługiwany

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

Dodawanie skojarzenia tożsamości do klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Opis

Ta usługa jest taka sama jak *nx_dhcpv6_add_client_ia* usługi. Dodaje on skojarzenie tożsamości klienta, wypełniając rekord Client dostarczonymi parametrami. Aby zażądać maksymalnej liczby preferowanych i prawidłowych okresów istnienia, ustaw te parametry na nieskończoność. Aby dodać więcej niż jedno IA do klienta DHCPv6, NX_DHCPV6_MAX_IA_ADDRESS wartość wyższa niż wartość domyślna 1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **ipv6_address** Wskaźnik do bloku adresów IP NetX Duo

- **preferred_lifetime** Czas, po który adres IP jest przestarzały

- **valid_lifetime** Czas przed wygaśnięciem adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dodano pomyślne we/wy klienta

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Zduplikowany adres IA 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA przekracza maksymalną wartość, z których może przechowywać klient IAS

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Nieprawidłowy (np. null) adres IA w IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

Tworzenie skojarzenia tożsamości (nie tymczasowego) dla klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Opis

Ta usługa tworzy skojarzenie IANA (Non Temporary Identity Association) klienta z podanych parametrów. Aby ustawić maksymalny czas T1 i T2 (nieskończoność) w żądaniach klienta DHCPv6, ustaw te parametry na wartość NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> Klient ma tylko jedną usługę IANA.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **IA_ident** Unikatowy identyfikator skojarzenia tożsamości

- **T1** Kiedy klient musi uruchomić odnawianie adresu IPv6

- **T2** Kiedy klient musi uruchomić ponowne powiązycie adresu IPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie utworzono IANA

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

Dodawanie skojarzenia tożsamości do klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Opis

Ta usługa dodaje skojarzenie tożsamości klienta, wypełniając rekord Client dostarczonymi parametrami. Aby zażądać maksymalnej liczby preferowanych i prawidłowych okresów istnienia, ustaw te parametry na nieskończoność. Aby dodać więcej niż jedno IA do klienta DHCPv6, NX_DHCPV6_MAX_IA_ADDRESS wartość wyższa niż wartość domyślna 1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **ipv6_address** Wskaźnik do bloku adresów IP NetX Duo

- **preferred_lifetime** Czas, po który adres IP jest przestarzały

- **valid_lifetime** Czas przed wygaśnięciem adresu IP 

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dodano pomyślne we/wy klienta

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Zduplikowany adres IA 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA przekracza maksymalną wartość, która może przechowywać klient IAS

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Nieprawidłowy (np. null) adres IA w IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika

 
### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

Pobiera identyfikator czasu z identyfikatora DUID klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Opis

Ta usługa pobiera pole identyfikatora czasu z identyfikatora DUID klienta. Jeśli aplikacja musi najpierw wywołać nx_dhcpv6_create_client_duid *,* aby wypełnić identyfikator DUID klienta w wystąpieniu klienta DHCPv6, lub będzie mieć wartość null dla tego pola. Intencją aplikacji jest zapisanie tych danych i przedstawienie na serwerze tego samego wartości DUID klienta, w tym pola czasu, po ponownym uruchomieniu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **time_id** Wskaźnik do pola czasu DUID klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) adresu IP zostały pomyślnie pobrane

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

Pobiera globalny adres IPv6 klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera globalny adres IPv6 klienta. Jeśli klient nie ma prawidłowego adresu, zwracany jest stan błędu. Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracany jest podstawowy adres IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **ip_address** Wskaźnik do adresu IPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) adres IPv6 został pomyślnie przypisany

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 jest nieprawidłowy

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

Pobiera dane czasu dzierżawy adresu IA klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Opis

Ta usługa pobiera globalne dane czasu IA klienta. Jeśli stan adresu IA klienta jest nieprawidłowy, dane czasu są ustawione na zero i zwracany jest stan pomyślnego ukończenia. Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracane są dane podstawowego adresu IA.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **T1** Wskaźnik do czasu odnowienia adresu IA

- **T2** Wskaźnik do czasu ponownego wiązania adresu IA

- **preferred_lifetime** Wskaźnik czasu, gdy adres IA jest przestarzały

- **valid_lifetime** Wskaźnik czasu wygaśnięcia adresu IA

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dane dzierżawy IA zostały pomyślnie pobrane

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana lease_time

Pobieranie danych czasu dzierżawy IANA klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Opis

Ta usługa pobiera globalne dane czasu dzierżawy IA-NA klienta (T1 i T2). Jeśli żaden z adresów IA-NA klienta nie ma prawidłowego stanu adresu, dane czasu są ustawione na zero i zwracany jest stan pomyślnego ukończenia. Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracane są dane podstawowego adresu IA.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **T1** Wskaźnik czasu do rozpoczęcia odnawiania dzierżawy

- **T2** Wskaźnik czasu do ponownego wiązania dzierżawy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) IANA lease data successfully retrieved (Pomyślnie pobrano dane dzierżawy IANA)

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

Pobieranie liczby prawidłowych adresów IA klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Opis

Ta usługa pobiera liczbę prawidłowych adresów IPv6 klienta. Prawidłowy adres IPv6 jest powiązany (przypisany) do klienta i zarejestrowany w wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **address_count** Wskaźnik do liczby adresów do zwrócenia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) IANA lease data successfully retrieved (Pomyślnie pobrano dane dzierżawy IANA)

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

Pobieranie danych IA klienta według indeksu adresów

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Opis

Ta usługa pobiera adres IA klienta i dane dzierżawy według indeksu adresów. Jeśli zostanie podany nieprawidłowy indeks lub adres IPv6 w tym indeksie jest nieprawidłowy, usługa zwraca stan NX_DHCPV6_IA_ADDRESS_NOT_VALID błędu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **address_index** Indeksowanie w tabeli IA protokołu DHCPv6

- **ip_address** Wskaźnik do adresu IPv6 do pobrania

- **preferred_lifetime** Wskaźnik czasu, gdy adres IA jest przestarzały

- **valid_lifetime** Wskaźnik czasu wygaśnięcia adresu IA

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) IANA pomyślnie pobrano

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Nieprawidłowy indeks lub brak prawidłowego adresu IPv6 w dostarczonym indeksie 

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

Pobiera adres serwera DNS 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera dane adresu IPv6 serwera DNS w określonym indeksie na liście klient. Jeśli lista nie zawiera adresu serwera w indeksie, zwracany jest błąd. Indeks nie może przekraczać rozmiaru listy serwerów DNS jest określony przez użytkownika konfigurowalne NX_DHCPV6_NUM_DNS_SERVERS.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **indeks** Indeksowanie na liście serwerów DNS

- **server_address** Wskaźnik do bufora adresów serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Adres został pomyślnie pobrany

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

Pobiera dane opcji DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Opis

Ta usługa pobiera dane opcji DHCPv6 z komunikatu DHCPv6 dla określonego kodu opcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **kod** opcji Kod opcji, dla którego dane mają zostać pobrane

- **bufor** Wskaźnik do buforu, do których mają być kopiowane dane 

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dane opcji zostały pomyślnie pobrane

- **NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Nieznany/nieobsługiwany kod opcji

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

Pobiera czas naliczony dla dzierżawy adresu IP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Opis

Ta usługa pobiera czas naliczany w dzierżawie adresu IPv6 klienta. Funkcja sprawdza wszystkie adresy IPv6 przypisane do klienta dla pierwszego prawidłowego adresu. Jeśli nie znaleziono prawidłowych adresów, zwracana jest wartość zero dla czasu naliczania.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **time_accrued** Wskaźnik do czasu naliczonego w dzierżawie ip

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Czas naliczony został pomyślnie pobrany

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

Pobiera adres serwera czasu 

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera dane adresu IPv6 serwera czasu w określonym indeksie na liście klient. Jeśli lista nie zawiera adresu serwera w indeksie, zwracany jest błąd. Indeks nie może przekraczać rozmiaru listy Serwer czasu jest określony przez konfigurowalna opcja NX_DHCPV6_NUM_TIME_SERVERS.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **indeks** Indeksowanie na liście serwera czasu

- **server_address** Wskaźnik do bufora adresów serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** adres (0x00) został pomyślnie pobrany

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

Usuń adres IP klienta z tabeli ADRESÓW IP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa ponownie inicjalizuje klienta w celu ponownego uruchomienia maszyny stanu DHCPv6 i ponownego uruchomienia protokołu DHCPv6. Nie jest to konieczne, jeśli klient nie uruchomił wcześniej maszyny stanu DHPCv6 lub nie przypisano żadnych adresów IPv6. Adresy zapisane w kliencie DHCPv6, a także zarejestrowane w wystąpieniu adresu IP, zostaną wyczyszone.

> [!NOTE]
> Aplikacja musi nadal uruchomić klienta DHCPv6 przy użyciu usługi *nx_dhcpv6_start* i rozpocząć żądanie przypisania adresu IPv6, *wywołując* nx_dhcpv6_request_solicit .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Adres został pomyślnie usunięty

- **NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 jest już uruchomiony

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

Przetwarzanie stanu POTWIERDŹ klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie POTWIERDŹ. Jeśli serwer otrzyma odpowiedź, klient DHCPv6 aktualizuje parametry dzierżawy przy użyciu odebranych danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) POTWIERDZENIE pomyślnego wysłania i przetworzenia komunikatu

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

Przetwarzanie stanu ŻĄDANIA INFORM klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat INFORM REQUEST. Jeśli zostanie odebrana odpowiedź, po jej otrzymaniu odpowiedź jest przetwarzana w celu ustalenia, czy jest prawidłowa, a serwer przyznał żądanie. Następnie wystąpienie klienta jest aktualizowane przy użyciu informacji o serwerze zgodnie z potrzebami.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Informuj o żądaniu pomyślnie utworzony i przetworzony

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

Dodawanie serwera DNS do żądania opcji DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję żądania informacji o serwerze DNS do żądania opcji DHCPv6. Jeśli odpowiedź serwera zawiera dane serwera DNS, klient będzie przechowywać serwer DNS, jeśli ma do tego miejsce. Liczba serwerów DNS, które klient może przechowywać, zależy od konfigurowalnej opcji, NX_DHCPV6_NUM_DNS_SERVERS której wartość domyślna to 2.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwera DNS jest uwzględniona

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

Dodawanie opcji W pełni kwalifikowana nazwa domeny do listy żądań opcji

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję dodawania w pełni kwalifikowanej nazwy domeny klienta do żądania opcji DHCPv6. Istnieją trzy opcje dla opcji FQDN:

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Zaktualizuj mapowanie adresów FQDN na IPv6 dla nazw FQDN i adresów używanych przez klienta.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Zaktualizuj mapowanie adresów FQDN na IPv6 dla nazw FQDN i adresów używanych przez klienta na serwerze.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Zażądaj, aby serwer nie przeprowadzał żadnych aktualizacji DNS w imieniu klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **domain_name** Ciąg zawierający nazwę domeny

- **op (op)** Typ opcji WQDN do zastosowania (zobacz listę powyżej)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) jest uwzględniona opcja WQDN

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

Dodawanie opcji nazwy domeny do żądania opcji DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję nazwy domeny do żądania opcji w komunikatach żądania klienta. Jeśli odpowiedź serwera zawiera dane nazwy domeny, klient będzie przechowywać informacje o nazwie domeny, jeśli rozmiar nazwy domeny znajduje się w rozmiarze buforu do przechowywania nazwy domeny. Ten rozmiar buforu jest konfigurowalna opcja (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) z wartością domyślną 30 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Nazwa domeny zestaw opcji

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

Ustawianie danych serwera czasu jako żądania opcjonalnego

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję informacji o serwerze czasu do żądania opcji komunikatów żądania klienta. Jeśli odpowiedź serwera zawiera dane serwera tim, klient będzie przechowywać serwer czasu, jeśli ma do tego miejsce. Liczba serwerów czasu, które klient może przechowywać, zależy od konfigurowalnej opcji

NX_DHCPV6_NUM_TIME _SERVERS której wartość domyślna to 1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Serwer czasu dodana

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

Ustawianie danych strefy czasowej jako żądania opcjonalnego

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję żądania informacji o strefie czasowej do żądania opcji Klient. Jeśli odpowiedź serwera zawiera dane strefy czasowej, klient będzie przechowywać informacje o strefie czasowej, jeśli rozmiar strefy czasowej znajduje się w rozmiarze buforu do przechowywania strefy czasowej. Ten rozmiar buforu jest konfigurowalna opcja (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) z wartością domyślną 10 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dodano opcję Strefa czasowa

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

Wysyłanie komunikatu o wydaniu protokołu DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat RELEASE w sieci klienta. Jeśli komunikat zostanie pomyślnie wysłany, zostanie zwrócony stan powodzenia. Pomyślne ukończenie nie oznacza, że klient otrzymał odpowiedź lub ma jeszcze udzielony adres IPv6. Zadanie wątku klienta DHCPv6 czeka na odpowiedź z serwera DHCPv6. Jeśli zostanie odebrany, sprawdza, czy odpowiedź jest prawidłowa, i zapisuje dane w rekordzie Client.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) RELEASE został pomyślnie wysłany

- **NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client nie zostało uruchomione

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) nie jest powiązany z klientem

- **NX_INVALID_INTERFACE** (0x4C) Nie znaleziono w tabeli adresów IP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

Wysyłanie komunikatu SOLICIT

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat SOLICIT do sieci. Jeśli komunikat zostanie pomyślnie wysłany, zostanie zwrócony stan powodzenia. Pomyślne ukończenie nie oznacza, że klient otrzymał odpowiedź lub ma jeszcze udzielony adres IPv6. Zadanie wątku klienta DHCPv6 czeka na odpowiedź (komunikat ANONS) z serwera DHCPv6. Jeśli zostanie odebrany, sprawdza, czy odpowiedź jest prawidłowa, zapisuje dane w rekordzie Client i podniesie klienta do stanu REQUEST.

> [!NOTE] 
> Jeśli opcja szybkiego zatwierdzania jest ustawiona, klient DHCPv6 zostanie przejść bezpośrednio do powiązanego stanu, jeśli odbiera prawidłowy komunikat ANONS SERWERA. Aby uzyskać więcej informacji, *zobacz opis nx_dhcpv6_request_solicit_rapid* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) SOLICIT został pomyślnie wysłany

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Wysyłanie komunikatu SOLICIT z opcją szybkiego zatwierdzania

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat SOLICIT w sieci z ustawioną opcją szybkiego zatwierdzania. Jeśli komunikat zostanie pomyślnie wysłany, zostanie zwrócony stan powodzenia. Pomyślne ukończenie nie oznacza, że klient otrzymał odpowiedź lub ma jeszcze udzielony adres IPv6. Zadanie wątku klienta DHCPv6 czeka na odpowiedź (komunikat ANONS) z serwera DHCPv6. Jeśli zostanie odebrany, sprawdza, czy odpowiedź jest prawidłowa, zapisuje dane w rekordzie Client i podniesie klienta do stanu BOUND.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) SOLICIT został pomyślnie wysłany

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

Wznawianie zadania klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wznawia zadanie wątku klienta DHCPv6. Zostanie przetworzony bieżący stan klienta DHCPv6 (np. Bound, Solicit)

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- NX_SUCCESS (0x00) client successfully resumed (Klient usługi **0x00)** został pomyślnie wznowiony

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_ time_accrued

Ustawia czas naliczany w dzierżawie adresu IP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Opis

Ta usługa ustawia czas naliczany na globalny adres IP klienta, ponieważ został on przypisany przez serwer. Tej wartości należy używać tylko wtedy, gdy klient jest obecnie powiązany z przypisanym adresem IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **time_accrued** Czas naliczony w dzierżawie adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Czas naliczony pomyślnie

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

Uruchamianie zadania klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia zadanie klienta DHCPv6 i przygotowuje klienta do uruchomienia protokołu DHCPv6. Sprawdza, czy wystąpienie klienta ma wystarczającą ilość informacji (takich jak identyfikator DUID klienta), tworzy i wiąże gniazda UDP do wysyłania i odbierania komunikatów DHCPv6 i aktywuje czasomierze do śledzenia czasu sesji i po wygaśnięciu bieżącej dzierżawy IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Client successfully started

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Brak wymaganych opcji klienta

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

Zatrzymywanie zadania klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje zadanie klienta DHCPv6 i czyszczy liczbę ponownych transmisji, maksymalne interwały retransmisji, dezaktywuje czasomierze wygaśnięcia sesji i dzierżawy oraz odłącza port gniazda klienta DHCPv6. Aby ponownie uruchomić klienta, należy najpierw zatrzymać i opcjonalnie ponownie zainicjować klienta przed rozpoczęciem innej sesji z dowolnym serwerem DHCPv6. Aby uzyskać więcej informacji, zobacz sekcję Mały przykład.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Client successfully stopped (Klient usługi 0x00) został pomyślnie zatrzymany

- **NX_DHCPV6_NOT_STARTED** (0xE92) Wątek klienta nie został uruchomiony

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

Wstrzymywanie zadania klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wstrzymuje zadanie klienta DHCPv6 i wszelkie żądania, które były w trakcie przetwarzania. Czasomierze są dezaktywowane, a stan klienta jest ustawiony na nieak uruchomiony.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Klient został pomyślnie zawieszony

- **NX_DHCPV6_NOT_STARTED** (0XE92) Klient nie jest uruchomiony, więc nie można go zawiesić

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi być wywoływana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
