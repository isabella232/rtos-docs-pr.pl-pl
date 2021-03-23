---
title: Rozdział 4 — usługi klienta DHCPv6 platformy Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług klienta DHCPv6 usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821978"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Rozdział 4 — usługi klienta DHCPv6 platformy Azure RTO NetX Duo

Ten rozdział zawiera opis wszystkich usług klienta DHCPv6 usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_dhcpv6_client_create:** *Tworzenie wystąpienia klienta DHCPv6* 

- **nx_dhcpv6_client_delete:** *usuwanie wystąpienia klienta DHCPv6* 

- **nx_dhcpv6_create_ client_duid:** *Tworzenie identyfikatora DUID klienta DHCPv6* 

- **nx_dhcpv6 _add_client_ia:** *Dodawanie adresu tożsamości klienta DHCPv6 (IA)* 

- **nx_dhcpv6 _create_client_ia:** (*starsze Dodawanie adresu tożsamości klienta DHCPv6 (IA))* 

- **nx_dhcpv6_create_client_iana:** *Utwórz skojarzenie tożsamości klienta Dhcpv6 dla adresów innych niż tymczasowe (IANA)* 

- **nx_dhcpv6_get_client_duid_time_id:** *Pobierz identyfikator czasu z identyfikatora DUID klienta DHCPv6* 

- **nx_dhcpv6_client_set_interface:** *Ustaw interfejs sieciowy klienta na potrzeby komunikacji z serwerem DHCPv6* 

- **nx_dhcpv6_get_IP_address:** *pobieranie globalnego adresu IPv6 przypisanego do klienta DHCPv6* 

- **nx_dhcpv6_get_lease_time_data:** *Pobierz T1, T2, prawidłowych i preferowanych okresów istnienia dla globalnego adresu IPv6 klienta*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *Uzyskaj T1, T2, prawidłowy i preferowany okres istnienia dla adresu IPv6 klienta DHCPv6 według indeksu adresu* 

- **nx_dhcpv6_get_iana_lease_time:** *Pobierz T1 i T2 w ramach SKOJARZENIA tożsamości (IANA) z klientem DHCPv6* 

- **nx_dhcpv6_get_other_option_data:** *Pobierz określone dane opcji, np. nazwę domeny lub serwer strefy czasowej* 

- **nx_dhcpv6_get_DNS_server_address:** *Pobierz adres serwera DNS z określonym indeksem na listę serwerów DNS klienta protokołu DHCPv6* 

- **nx_dhcpv6_get_time_accrued:** *uzyskaj czas naliczania dzierżawy globalnego adresu IPv6 został powiązany z klientem DHCPv6* 

- **nx_dhcpv6_get_time_server_address:** *Pobierz adres serwera czasu o określonym indeksie na listę serwerów czasu klienta DHCPv6*

- **nx_dhcpv6_get_valid_ip_address_count:** *pobieranie liczby adresów IPv6 przypisanych do klienta DHCPv6* 

- **nx_dhcpv6_reinitialize:** *zainicjuj ponownie protokół DHCPv6 w celu ponownego uruchomienia komputera stanu klienta DHCPv6 i uruchomienia protokołu DHCPv6* 

- **nx_dhcpv6_request_confirm:** *Wyślij żądanie potwierdzenia do serwera* 

- **nx_dhcpv6_request_inform_request:** S *Zakończ komunikat żądania inform na serwerze* 

- **nx_dhcpv6_request_release:** *Wyślij żądanie wydania do serwera* 

- **nx_dhcpv6_request_option_DNS_server:** *Dodaj opcję serwer DNS do żądania opcji klienta dane w żądaniach wysyłanych do serwera* 

- **nx_dhcpv6_request_option_FQDN:** *Dodaj opcję FQDN do żądania opcji klienta dane w żądaniach wysyłanych do serwera* 

- **nx_dhcpv6_request_option_domain_name:** *Dodaj opcję nazwy domeny do żądania opcji klienta dane w żądaniach wysyłanych do serwera* 

- **nx_dhcpv6_request_option_time_server:** *Dodaj opcję serwer czasu do żądania opcji klienta dane w żądaniach wysyłanych do serwera* 

- **nx_dhcpv6_request_option_timezone:** *Dodaj opcję strefy czasowej do żądania opcji klienta dane w żądaniach wysyłanych do serwera* 

- **nx_dhcpv6_request_solicit:** *Wyślij żądanie protokołu Dhcpv6 do dowolnego serwera w sieci klienta (emisja)* 

- **nx_dhcpv6_request_solicit_rapid:** *Wyślij żądanie protokołu Dhcpv6 do dowolnego serwera w sieci klienta (emisji) z ustawioną opcją szybkiego zatwierdzania* 

- **nx_dhcpv6_resume:** *Wznów przetwarzanie klienta DHCPv6* 

- **nx_dhcpv6_start:** *Uruchom zadanie wątku klienta DHCPv6. Zwróć uwagę, że nie jest to równoznaczne z uruchomieniem komputera stanu DHCPv6 i nie wysyła żądania żądanie* 

- **nx_dhcpv6_stop:** *Zatrzymaj zadanie wątku klienta DHCPv6* 

- **nx_dhcpv6_suspend:** *Wstrzymywanie zadania wątku klienta DHCPv6* 

- **nx_dhcpv6_set_time_accrued:** *Ustaw czas naliczania dla dzierżawy globalnego adresu IPv6 klienta w rekordzie klienta.*

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

- **name_ptr** Wskaźnik do nazwy dla wystąpienia DHCPv6

- **packet_pool_ptr** Wskaźnik do puli pakietów klienta

- **stack_ptr** Wskaźnik do pamięci stosu klienta

- **stack_size** Rozmiar pamięci stosu klienta

- **dhcpv6_state_change_notify** Wskaźnik do funkcji wywołania zwrotnego wywoływany, gdy klient inicjuje nowe żądanie DHCPv6 na serwerze

- **dhcpv6_server_error_handler** Wskaźnik do funkcji wywołania zwrotnego wywoływany, gdy klient otrzymuje stan błędu z serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne utworzenie klienta

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem

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

- **NX_SUCCESS** (0X00) pomyślne usunięcie DHCPv6

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem

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

Ustawia interfejs sieciowy klienta dla protokołu DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Opis

Ta usługa ustawia interfejs sieciowy klienta na potrzeby komunikacji z serwerami DHCPv6 do określonego indeksu interfejsu wejściowego.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **interface_index** Indeks wskazujący interfejs sieciowy

### <a name="return-values"></a>Wartości zwrócone

- Interfejs **NX_SUCCESS** (0x00) został pomyślnie ustawiony

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_INVALID_INTERFACE (0x4C) nieprawidłowe dane wejściowe indeksu interfejsu

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

Ustawia adres docelowy, na który powinien zostać wysłany komunikat protokołu DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres docelowy, na który powinien zostać wysłany komunikat protokołu DHCPv6. Domyślnie jest ALL_DHCP_Relay_Agents_and_Servers (FF02:: 1:2).

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **destination_address** Adres docelowy

### <a name="return-values"></a>Wartości zwrócone

- Interfejs **NX_SUCCESS** (0x00) został pomyślnie ustawiony

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- Błąd akapitu NX_DHCPV6_PARAM_ERROR (0xE93)

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

Utwórz obiekt identyfikatora DUID klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Opis

Ta usługa tworzy identyfikator DUID klienta z parametrami wejściowymi. Jeśli dane wejściowe czasu nie zostaną podane, a Typ identyfikatora DUID wskazuje warstwę łącza z czasem, ta funkcja będzie dostarczać czas, który zawiera losowy współczynnik unikatowości. Typy identyfikatora DUID przypisane przez dostawcę (Enterprise) nie są obsługiwane.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **duid_type** Typ identyfikatora DUID (sprzęt, przedsiębiorstwo itp.)

- **hardware_type** Sprzęt sieciowy, np. IEEE 802

- **czas** Wartość używana podczas tworzenia unikatowego identyfikatora

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie utworzono identyfikator DUID klienta

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- Typ identyfikatora DUID NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) nieznany lub nieobsługiwany 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) identyfikator DUID typu sprzętu nieznany lub nieobsługiwany

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

Ta usługa jest taka sama jak usługa *nx_dhcpv6_add_client_ia* . Dodaje skojarzenie tożsamości klienta, wypełniając rekord klienta podanymi parametrami. Aby zażądać maksymalnych preferowanych i prawidłowych okresów istnienia, ustaw dla tych parametrów nieskończoność. Aby dodać więcej niż jeden element IA do klienta DHCPv6, należy ustawić NX_DHCPV6_MAX_IA_ADDRESS wartość wyższą niż domyślna wartość 1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **ipv6_address** Wskaźnik do bloku adresów IP NetX Duo

- **preferred_lifetime** Długość czasu przed przestarzałym adresem IP

- **valid_lifetime** Długość czasu przed wygaśnięciem adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie klienta IA

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) zduplikowany adres IA 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA przekracza maksymalny klient IAs może przechowywać

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) nieprawidłowy adres (np. null) IA w IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem


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

Utwórz skojarzenie tożsamości (nietymczasowe) dla klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Opis

Ta usługa tworzy nietymczasowym skojarzeniem tożsamości (IANA) klienta z podanych parametrów. Aby ustawić czas T1 i T2 na maksymalny (nieskończoność) w żądaniach klientów DHCPv6, ustaw te parametry na NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> Klient ma tylko jednego organizację IANA.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **IA_ident** Unikatowy identyfikator skojarzenia tożsamości

- **T1** Gdy klient musi uruchomić Odnawianie adresu IPv6

- **T2** Gdy klient musi uruchomić ponowne wiązanie adresu theIPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie utworzył organizację IANA

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem

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

Ta usługa dodaje skojarzenie tożsamości klienta, wypełniając rekord klienta podanymi parametrami. Aby zażądać maksymalnych preferowanych i prawidłowych okresów istnienia, ustaw dla tych parametrów nieskończoność. Aby dodać więcej niż jeden element IA do klienta DHCPv6, należy ustawić NX_DHCPV6_MAX_IA_ADDRESS wartość wyższą niż domyślna wartość 1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **ipv6_address** Wskaźnik do bloku adresów IP NetX Duo

- **preferred_lifetime** Długość czasu przed przestarzałym adresem IP

- **valid_lifetime** Długość czasu przed wygaśnięciem adresu IP 

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie klienta IA

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) zduplikowany adres IA 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA przekracza maksymalny klient IAs może przechowywać

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) nieprawidłowy adres (np. null) IA w IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem

 
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

Ta usługa pobiera pole identyfikatora czasu z identyfikatora DUID klienta. Jeśli aplikacja musi najpierw wywołać *nx_dhcpv6_create_client_duid*, aby wypełnić identyfikator DUID klienta w wystąpieniu klienta DHCPv6 lub będzie mieć wartość null dla tego pola. Celem jest zapisanie tych danych przez aplikację i zaprezentowanie tego samego identyfikatora DUID klienta na serwerze, w tym pola czasowego, w przypadku ponownego uruchomienia.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **TIME_ID** Wskaźnik do pola czasu identyfikatora DUID klienta

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie pobrano dane dzierżawy IP **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

- **IP_address** Wskaźnik na adres IPv6

### <a name="return-values"></a>Wartości zwrócone

- Adres IPv6 **NX_SUCCESS** (0x00) został pomyślnie przypisany

- Adres IPv6 **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) jest nieprawidłowy

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Pobiera dane czasu dzierżawy adresu (IA) klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Opis

Ta usługa pobiera dane o globalnym czasie adresu klienta. Jeśli stan adresu klienta IA jest nieprawidłowy, dane czasu są ustawiane na zero i zwracany jest stan pomyślnego zakończenia. Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracane są dane podstawowych adresów IA.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **T1** Wskaźnik na czas odnowienia adresu (IA)

- **T2** Wskaźnik do ponownego powiązania adresu IA

- **preferred_lifetime** Wskaźnik do czasu, gdy adres IA jest przestarzały

- **valid_lifetime** Wskaźnik do czasu wygaśnięcia okresu IA

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnie pobrano dane DZIERŻAWy IA

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Pobieranie danych czasu dzierżawy organizacji klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Opis

Ta usługa pobiera dane globalne czasu dzierżawy (T1 i T2) klienta. Jeśli żaden z adresów klienta IA-NA nie ma prawidłowego stanu adresu, dane czasu są ustawione na zero i zwracany jest stan pomyślnego zakończenia. Jeśli klient ma więcej niż jeden globalny adres IPv6, zwracane są dane podstawowych adresów IA.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **T1** Wskaźnik do momentu rozpoczęcia odnawiania dzierżawy

- **T2** Wskaźnik do czasu rozpoczęcia ponownego powiązania dzierżawy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) dane dzierżawy organizacji Iana zostały pomyślnie pobrane

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Pobierz liczbę prawidłowych adresów (IA) klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Opis

Ta usługa Pobiera liczbę prawidłowych adresów IPv6 klienta. Prawidłowy adres IPv6 jest powiązany (przypisany) do klienta i zarejestrowany w wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **address_count** Wskaźnik do liczby adresów do zwrócenia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) dane dzierżawy organizacji Iana zostały pomyślnie pobrane

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Pobieranie danych klienta IA przez indeks adresu

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Opis

Ta usługa Pobiera adres IA klienta i dane dzierżawy według indeksu adresu. Jeśli podano nieprawidłowy indeks lub adres IPv6 w tym indeksie jest nieprawidłowy, usługa zwróci NX_DHCPV6_IA_ADDRESS_NOT_VALID stanu błędu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **address_index** Indeksowanie w tabeli protokołu DHCPv6 IA

- **IP_address** Wskaźnik na adres IPv6 do pobrania

- **preferred_lifetime** Wskaźnik do czasu, gdy adres IA jest przestarzały

- **valid_lifetime** Wskaźnik do czasu wygaśnięcia okresu IA

### <a name="return-values"></a>Wartości zwrócone

- Dane dotyczące **NX_SUCCESS** (0X00) Iana zostały pomyślnie pobrane

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Nieprawidłowy indeks lub nie ma prawidłowego adresu IPv6 pod podanym indeksem 

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Ta usługa pobiera dane adresów IPv6 serwera DNS z określonym indeksem na liście klientów. Jeśli lista nie zawiera adresu serwera w indeksie, zwracany jest błąd. Indeks nie może przekroczyć rozmiaru listy serwerów DNS zdefiniowanej przez użytkownika NX_DHCPV6_NUM_DNS_SERVERS opcję konfigurowalną.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **indeks** Indeksuj na listę serwerów DNS

- **server_address** Wskaźnik do buforu adresów serwera

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie pobrano adres **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Pobiera dane opcji protokołu DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Opis

Ta usługa pobiera dane z opcji DHCPv6 z komunikatu protokołu DHCPv6 dla określonego kodu opcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **kod opcji kodu opcji** , dla którego dane mają zostać pobrane

- **bufor** Wskaźnik do buforu, do którego mają zostać skopiowane dane 

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie pobrano dane opcji **NX_SUCCESS** (0x00)

- **NX_DHCPV6_UNKNOWN_OPTION** (0XEAB) nieznany/nieobsługiwany kod opcji

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_DHCPV6_PARAM_ERROR (0xE93) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Pobiera czas naliczany przez dzierżawę adresu IP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Opis

Ta usługa Pobiera czas naliczony przez dzierżawę adresu IPv6 klienta. Funkcja sprawdza wszystkie adresy IPv6 przypisane do klienta pod kątem pierwszego prawidłowego adresu. Jeśli nie zostanie znaleziony prawidłowy adres, zwracana jest wartość zero dla naliczonego czasu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **time_accrued** Wskaźnik na czas naliczany w dzierżawie IP

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie pobrano naliczony czas **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Ta usługa pobiera dane adresów IPv6 serwera czasu o określonym indeksie na liście klientów. Jeśli lista nie zawiera adresu serwera w indeksie, zwracany jest błąd. Indeks nie może przekroczyć rozmiaru listy serwerów czasu określonego przez użytkownika NX_DHCPV6_NUM_TIME_SERVERS opcji konfigurowalnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **indeks** Indeksuj na listę serwerów czasu

- **server_address** Wskaźnik do buforu adresów serwera

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie pobrano adres **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Usuń adres IP klienta z tabeli IP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa ponownie inicjuje klienta programu w celu ponownego uruchomienia komputera stanu DHCPv6 i ponownego uruchomienia protokołu DHCPv6. Nie jest to konieczne, jeśli klient nie uruchomił wcześniej DHPCv6 stanu komputera ani nie przypisał żadnego adresu IPv6. Adresy zapisane na kliencie DHCPv6 oraz zarejestrowane z wystąpieniem IP są wyczyszczone.

> [!NOTE]
> Aplikacja musi nadal uruchamiać klienta DHCPv6 przy użyciu *usługi nx_dhcpv6_start* i rozpocząć żądanie przypisywania adresów IPv6 przez wywołanie *nx_dhcpv6_request_solicit*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto adres **NX_SUCCESS** (0x00)

- **NX_DHCPV6_ALREADY_STARTED** (0XE91) klient DHCPv6 jest już uruchomiony

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Przetwórz stan potwierdzenia klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie potwierdzenia. W przypadku otrzymania odpowiedzi z serwera klient DHCPv6 aktualizuje swoje parametry dzierżawy o odebranych danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Komunikat POTWIERDZAjący **NX_SUCCESS** (0x00) został pomyślnie wysłany i przetworzony

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Przetwarzaj stan żądania poinformowania klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat z PROŚBą o powiadomienie. W przypadku odebrania odpowiedzi, gdy zostanie odebrana, odpowiedź jest przetwarzana w celu ustalenia, czy serwer udzielił żądania. Wystąpienie klienta zostaje następnie zaktualizowane informacjami o serwerze zgodnie z wymaganiami.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) komunikat żądania inform został pomyślnie utworzony i przetworzony

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Dodaj serwer DNS do żądania opcji protokołu DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję żądania informacji o serwerze DNS do żądania opcji protokołu DHCPv6. Jeśli odpowiedź serwera zawiera dane serwera DNS, klient będzie przechowywał serwer DNS, jeśli ma to miejsce. Liczba serwerów DNS, które mogą być przechowywane przez klienta, zależy od konfigurowalnej opcji NX_DHCPV6_NUM_DNS_SERVERS której wartość domyślna to 2.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Opcja serwera DNS **NX_SUCCESS** (0x00) jest dołączona

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Dodaj w pełni kwalifikowaną opcję nazwy domeny do listy żądań opcji

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję dodawania w pełni kwalifikowanej nazwy domeny klienta do żądania opcji protokołu DHCPv6. Dostępne są trzy opcje dla opcji FQDN:

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Aktualizowanie mapowania adresów FQDN-IPv6 dla nazwy FQDN i adresów używanych przez klienta.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 zaktualizuj mapowanie adresów FQDN-IPv6 dla nazwy FQDN i adresów używanych przez klienta na serwerze programu.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Zażądaj, aby serwer nie wykonywał aktualizacji DNS w imieniu klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **domain_name** Ciąg przechowujący nazwę domeny

- **operacja** Typ opcji FQDN do zastosowania (patrz lista powyżej)

### <a name="return-values"></a>Wartości zwrócone

- Opcja nazwy FQDN **NX_SUCCESS** (0x00) jest uwzględniona

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Dodaj opcję nazwy domeny do żądania opcji protokołu DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję nazwy domeny do żądania opcji w komunikatach żądania klienta. Jeśli odpowiedź serwera zawiera dane nazwy domeny, klient będzie przechowywał informacje o nazwie domeny, jeśli rozmiar nazwy domeny mieści się w rozmiarze buforu na potrzeby przechowywania nazwy domeny. Ten rozmiar buforu jest konfigurowalną opcją (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) o wartości domyślnej 30 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) ustawienie opcji nazwy domeny

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Ustaw dane serwera jako opcjonalne żądanie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję Informacje o serwerze czasu do żądania opcji komunikatów żądania klienta. Jeśli odpowiedź serwera zawiera dane serwera Tim, klient będzie przechowywał serwer czasu, jeśli ma to miejsce. Liczba serwerów, które mogą być przechowywane przez klienta, zależy od opcji konfigurowalnej

NX_DHCPV6_NUM_TIME _SERVERS których wartość domyślna to 1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Dodano opcję serwera czasu **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Ustaw dane strefy czasowej jako opcjonalne żądanie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje opcję żądania informacji o strefie czasowej do żądania opcji klienta. Jeśli odpowiedź serwera zawiera dane strefy czasowej, klient będzie przechowywał informacje o strefie czasowej, jeśli rozmiar strefy czasowej mieści się w rozmiarze buforu do przechowywania strefy czasowej. Ten rozmiar buforu jest konfigurowalną opcją (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) o wartości domyślnej 10 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Dodano opcję strefy czasowej **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Wysyłanie komunikatu o ZWOLNIeniu protokołu DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat o wersji w sieci klienta. Jeśli komunikat został pomyślnie wysłany, zwracany jest stan "powodzenie". Pomyślne zakończenie nie oznacza, że klient otrzymał odpowiedź lub że został jeszcze przydzielony adres IPv6. Zadanie wątku klienta DHCPv6 czeka na odpowiedź z serwera DHCPv6. Jeśli zostanie odebrana, sprawdza, czy odpowiedź jest prawidłowa i zapisuje dane w rekordzie klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Komunikat o wersji **NX_SUCCESS** (0x00) został pomyślnie wysłany

- **NX_DHCPV6_NOT_STARTED** (0xE92) nie uruchomiono zadania klienta protokołu DHCPv6

- Adres **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) nie jest powiązany z klientem

- Nie znaleziono **NX_INVALID_INTERFACE** (0x4C) w tabeli adresów IP

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Wyślij komunikat żądania

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat żądania w sieci. Jeśli komunikat został pomyślnie wysłany, zwracany jest stan "powodzenie". Pomyślne zakończenie nie oznacza, że klient otrzymał odpowiedź lub że został jeszcze przydzielony adres IPv6. Zadanie wątku klienta DHCPv6 czeka na odpowiedź (komunikat ADVERTISE) z serwera DHCPv6. Jeśli zostanie on odebrany, sprawdza, czy odpowiedź jest prawidłowa, przechowuje dane w rekordzie klienta i promuje klienta do stanu żądania.

> [!NOTE] 
> Jeśli opcja szybkie zatwierdzanie zostanie ustawiona, klient DHCPv6 przejdzie bezpośrednio do stanu powiązanego, Jeśli odbierze prawidłowy komunikat ANONSowania serwera. Aby uzyskać więcej informacji, zobacz Opis usługi dla *nx_dhcpv6_request_solicit_rapid* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Komunikat żądania **NX_SUCCESS** (0x00) został pomyślnie wysłany

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Wyślij komunikat z PROŚBą o opcję szybkiego zatwierdzania

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat żądania w sieci z ustawioną opcją szybkiego zatwierdzania. Jeśli komunikat został pomyślnie wysłany, zwracany jest stan "powodzenie". Pomyślne zakończenie nie oznacza, że klient otrzymał odpowiedź lub że został jeszcze przydzielony adres IPv6. Zadanie wątku klienta DHCPv6 czeka na odpowiedź (komunikat ADVERTISE) z serwera DHCPv6. Jeśli zostanie on odebrany, sprawdza, czy odpowiedź jest prawidłowa, przechowuje dane w rekordzie klienta i promuje klienta do stanu POWIĄZANEgo.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Komunikat żądania **NX_SUCCESS** (0x00) został pomyślnie wysłany

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Wznów zadanie klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa wznawia zadanie wątku klienta protokołu DHCPv6. Bieżący stan klienta DHCPv6 zostanie przetworzony (np. powiązano, żądanie)

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie wznowiono działanie klienta **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Ustawia czas naliczania w dzierżawie adresu IP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Opis

Ta usługa ustawia czas naliczania na globalny adres IP klienta, ponieważ został przypisany przez serwer. Tego elementu należy używać tylko w przypadku, gdy klient jest aktualnie powiązany z przypisanym adresem IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

- **time_accrued** Czas naliczania dzierżawy adresów IP

### <a name="return-values"></a>Wartości zwrócone

- Czas **NX_SUCCESS** (0x00) został pomyślnie ustawiony

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

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

Uruchom zadanie klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia zadanie klienta DHCPv6 i przygotowuje klienta do uruchomienia protokołu DHCPv6. Sprawdza, czy wystąpienie klienta ma wystarczające informacje (na przykład identyfikator DUID klienta), tworzy i wiąże gniazdo UDP do wysyłania i otrzymywania komunikatów DHCPv6 oraz uaktywnia czasomierze w celu śledzenia czasu sesji i wygaśnięcia bieżącej dzierżawy protokołu IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślnie uruchomiono klienta

- Klient **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) nie ma wymaganych opcji

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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

Zatrzymaj zadanie klienta DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa zadanie klienta protokołu DHCPv6 i czyści liczbę ponownych transmisji, maksymalne interwały retransmisji, wyłącza sesje i czasomierze wygaśnięcia dzierżawy oraz usuwa powiązanie portu gniazda klienta DHCPv6. Aby ponownie uruchomić klienta, należy najpierw zatrzymać i opcjonalnie zainicjować klienta przed rozpoczęciem kolejnej sesji z dowolnym serwerem DHCPv6. Więcej informacji można znaleźć w sekcji małego przykładu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) klient został pomyślnie zatrzymany

- Wątek klienta **NX_DHCPV6_NOT_STARTED** (0xE92) nie został uruchomiony

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku


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

Ta usługa zawiesza zadanie klienta DHCPv6 i wszystkie żądania, które były w trakcie przetwarzania. Czasomierze są dezaktywowane i stan klienta jest ustawiony na Nieuruchomiony.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do wystąpienia klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- Klient **NX_SUCCESS** (0x00) pomyślnie zawiesił

- Klient **NX_DHCPV6_NOT_STARTED** (0XE92) nie działa, więc nie można go wstrzymać

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) musi zostać wywołana z wątku

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
