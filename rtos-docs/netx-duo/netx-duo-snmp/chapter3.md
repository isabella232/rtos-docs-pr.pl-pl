---
title: Rozdział 3 — opis Azure RTOS agentów NetX Duo SNMP
description: Ten rozdział zawiera opis wszystkich usług agenta SNMP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b24776c2eb25a53195ea4eb452497b23b933e4ab3f9f0a379ea64d8469c1c971
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790126"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Rozdział 3 — opis Azure RTOS agentów NetX Duo SNMP

Ten rozdział zawiera opis wszystkich usług Azure RTOS agenta NetX Duo SNMP (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Określanie klucza uwierzytelniania (tylko SNMP v3) dla komunikatów pułapek*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Określanie klucza uwierzytelniania (tylko SNMP v3) dla komunikatów odpowiedzi*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Pobieranie nazwy społeczności*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Ustawianie aparatu kontekstu (tylko SNMP v3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Ustawianie nazwy kontekstu (tylko SNMP v3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Tworzenie agenta SNMP*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Pobierz wersję SNMP odebranego pakietu*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Wskaż, czy ostatnie żądanie SNMP ma typ GET lub SET*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Określanie, czy ciąg pasuje do ciągu prywatnego agenta*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Określanie, czy ciąg pasuje do ciągu publicznego agenta*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Ustawianie interfejsu sieciowego dla komunikatów SNMP*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Ustawianie prywatnego ciągu społeczności agenta SNMP*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Ustawianie publicznego ciągu społeczności agenta SNMP*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Ustawianie stanu agenta SNMP dla wszystkich wersji SNMP*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Usuwanie agenta SNMP*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Tworzenie klucza md5 (tylko SNMP v3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Tworzenie klucza md5 (tylko SNMP v3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Określanie klucza szyfrowania (tylko SNMP v3) dla komunikatów pułapek*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Określanie klucza szyfrowania (tylko SNMP v3) dla komunikatów odpowiedzi*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Tworzenie klucza sha (tylko SNMP v3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Tworzenie klucza sha (tylko SNMP v3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Uruchamianie agenta SNMP*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Zatrzymywanie agenta SNMP*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Wysyłanie pułapki SNMP v1 (tylko protokół IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Wysyłanie pułapki SNMP v2 (tylko protokół IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Wysyłanie pułapki SNMP v2 (tylko protokół IPv4) z określeniem OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Wysyłanie pułapki SNMP v3 (tylko protokół IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Wysyłanie pułapki SNMP v2 (tylko protokół IPv4) z określeniem OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Wysyłanie pułapki SNMP v1 (IPv4 i IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Wysyłanie pułapki SNMP v2 (IPv4 i IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Wysyłanie pułapki SNMP v2 (IPv4/IPv6) z określeniem OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Wysyłanie pułapki SNMP v3 (IPv4 i IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Wysyłanie pułapki SNMP v2 (IPv4/IPv6) z określeniem OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Ustawianie liczby ponownych uruchomień*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Porównywanie dwóch obiektów*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Porównywanie dwóch obiektów*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Kopiowanie obiektu*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Kopiowanie obiektu*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Uzyskiwanie obiektu licznika*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Ustaw obiekt licznika*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Pobierz obiekt licznika 64-bitowego*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Ustaw obiekt licznika 64-bitowego*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Ustawianie wartości końca mib*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Uzyskiwanie obiektu miernika*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Ustawianie obiektu miernika*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Uzyskiwanie identyfikatora obiektu*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Ustawianie identyfikatora obiektu*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Uzyskiwanie obiektu liczby całkowitej*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Ustawianie obiektu liczby całkowitej*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Uzyskiwanie obiektu adresu IP (tylko protokół IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Ustawianie obiektu adresu IP (tylko protokół IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Uzyskiwanie obiektu adresu IP (tylko protokół IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Ustawianie obiektu adresu IP (tylko protokół IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Ustawianie wartości bez wystąpienia*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Ustawianie wartości nie znaleziono*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Uzyskiwanie obiektu ciągu oktetu*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Ustawianie obiektu ciągu oktetu*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Uzyskiwanie obiektu ciągu ASCII*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Ustawianie obiektu ciągu ASCII*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *Uzyskiwanie obiektu timetics*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *Ustawianie obiektu timetics*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
Określanie klucza uwierzytelniania dla komunikatów pułapek

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Opis

Ta usługa określa klucz, który ma być używany do ustawiania parametrów uwierzytelniania w nagłówku zabezpieczeń SNMPv3 w komunikatach pułapek. Dostarczenie wartości NX_NULL klucza powoduje wyłączenie uwierzytelniania.

> [!NOTE]
> Klucz musi zostać utworzony wcześniej. Zobacz nx_snmp_agent_md5_key_create lub nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **klucz** Wskaźnik do wcześniej utworzonego klucza MD5 lub SHA.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw kluczy uwierzytelniania pomyślne.
- **NX_NOT_ENABLED** (0x14) SNMP Security disabled (Wyłączone zabezpieczenia SNMP) 
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik agenta SNMP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
Określanie klucza uwierzytelniania dla komunikatów odpowiedzi

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Opis

Ta usługa określa klucz, który ma być używany dla parametrów uwierzytelniania w parametrze zabezpieczeń SNMPv3 dla wszystkich żądań wykonanych po jego skonfigurowaniu. Dostarczenie wartości NX_NULL klucza powoduje wyłączenie uwierzytelniania.

> [!NOTE]
> Klucz musi zostać utworzony wcześniej. Zobacz nx_snmp_agent_md5_key_create lub nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **klucz** Wskaźnik do wcześniej utworzonego klucza MD5 lub SHA.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw kluczy SNMP powodzenie.
- **NX_NOT_ENABLED** (0x14) SNMP Security disabled (Wyłączone zabezpieczenia SNMP)
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik agenta SNMP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Pobieranie nazwy społeczności

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera nazwę społeczności z ostatniego żądania SNMP otrzymanego przez agenta SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **community_string_ptr** Wskaźnik do wskaźnika ciągu w celu zwrócenia ciągu społeczności agenta SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie przez społeczność SNMP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
Wskaż, czy ostatnie żądanie SNMP ma typ GET lub SET

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Opis

Ta usługa wskazuje, czy najnowsze żądanie z Menedżera SNMP ma typ GET (GET, GETNEXT lub GETBULK) lub SET. Jest on przeznaczony do użycia z wywołaniem zwrotny nazwy użytkownika, w którym aplikacja SNMPv1 lub SNMPv2 będzie chciała porównać otrzymany ciąg społeczności z ciągiem publicznym agenta SNMP, jeśli żądanie jest typem GET, lub z prywatnym ciągiem agenta SNMP, jeśli żądanie jest typem ZESTAWU.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **is_get_type** Wskaźnik do stanu typu żądania:  
NX_TRUE, jeśli typ GET  
NX_FALSE jeśli typ SET

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zwrócony typ
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Ustawianie aparatu kontekstu (tylko SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Opis

Ta usługa ustawia aparat kontekstu agenta SNMP. Ma zastosowanie tylko do przetwarzania SNMPv3. Należy to zrobić przed utworzeniem kluczy zabezpieczeń, jeśli aplikacja korzysta z uwierzytelniania i szyfrowania, ponieważ identyfikator aparatu kontekstu jest używany w procesie tworzenia klucza. Jeśli nie, NetX Duo SNMP udostępnia domyślny identyfikator aparatu kontekstu na początku *nxd_snmp.c:*

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **context_engine** Wskaźnik do ciągu aparatu kontekstu.
- **context_engine_size** Rozmiar ciągu aparatu kontekstu. Należy pamiętać, że maksymalna liczba bajtów w a aparatze kontekstu jest definiowana przez NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw aparatu kontekstu SNMP z powodzeniem.
- **NX_NOT_ENABLED** (0x14) SNMPv3 nie jest włączony
- **NX_SNMP_ERROR** (0x100) Błąd rozmiaru aparatu kontekstu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Ustawianie nazwy kontekstu (tylko SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę kontekstu agenta SNMP. Ma zastosowanie tylko do przetwarzania SNMPv3. Jeśli nie zostanie wywołana, agent NETX Duo SNMP pozostawi pustą nazwę kontekstu.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **context_name** Wskaźnik do ciągu nazwy kontekstu.
- **context_name_size** Rozmiar ciągu nazwy kontekstu. Należy pamiętać, że maksymalna liczba bajtów w nazwie kontekstu jest definiowana przez NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych nazw kontekstowych SNMP.
- **NX_SNMP_ERROR** (0x100) Rozmiar nazwy kontekstu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
Tworzenie agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a>Opis

Ta usługa tworzy agenta SNMP dla określonego wystąpienia adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **snmp_agent_name** Wskaźnik do ciągu nazwy agenta SNMP.
- **ip_ptr** Wskaźnik do wystąpienia adresu IP.
- **stack_ptr** Wskaźnik do wskaźnika stosu wątku agenta SNMP.
- **stack_size** Rozmiar stosu w bajtach.
- **pool_ptr** Wskaźnik domyślnej puli pakietów dla tego agenta SNMP.
- **snmp_agent_username_process** Wskaźnik funkcji do procedury obsługi nazwy użytkownika aplikacji.
- **snmp_agent_get_process** Wskaźnik funkcji do procedury obsługi żądań GET aplikacji.
- **snmp_agent_getnext_process** Wskaźnik funkcji do procedury obsługi żądań GETNEXT aplikacji.
- **snmp_agent_set_process** Wskaźnik funkcji do procedury obsługi żądań SET aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie agenta SNMP.
- **NX_SNMP_ERROR** (0x100) SNMP Agent create error (Błąd tworzenia agenta SNMP).
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
Uzyskiwanie wersji pakietu SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Opis

Ta usługa pobiera analizowane wersje SNMP z najnowszego odebranego pakietu SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **wersja** Wskaźnik do wersji SNMP analizowane z odebranego pakietu SNMP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie wersji SNMP
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
Sprawdzanie, czy ciąg prywatny pasuje do ciągu prywatnego agenta

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Opis

Ta usługa porównuje ciąg wejściowy społeczności zakończony z wartością null z prywatnym ciągiem agenta SNMP i wskazuje, czy są zgodne.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **community_string** Wskaźnik do ciągu do porównania
- **is_private** Wskaźnik do wyniku porównania  
NX_TRUE — dopasowania ciągów  
NX_FALSE — ciąg nie jest zgodne

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Porównanie powodzenia
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
Sprawdzanie, czy odebrany ciąg publiczny pasuje do ciągu publicznego agenta

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Opis

Ta usługa porównuje ciąg wejściowy społeczności zakończony z wartością null z publicznym ciągiem agenta SNMP i wskazuje, czy są zgodne.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **community_string** Wskaźnik do ciągu do porównania
- **is_public** Wskaźnik do wyniku porównania  
NX_TRUE — dopasowania ciągów  
NX_FALSE — ciąg nie jest zgodne

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Porównanie powodzenia
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
Ustawianie stanu agenta SNMP dla każdej wersji SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Opis

Ta usługa ustawia stan (włączony/wyłączony) dla każdej wersji SNMP, V1, V2 i V3 agenta SNMP. Należy pamiętać, że opcje konfigurowalne przez użytkownika, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 i NX_SNMP_DISABLE_V3, zastąpią te ustawienia czasu uruchamiania. Domyślnie agent SNMP jest włączony dla wszystkich trzech wersji.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **enabled_v1** Ustawia włączony stan dla SNMP V1 wł./wył.
- **enabled_v2** Ustawia włączony stan dla SNMP V2 wł./wył.
- **enabled_v3** Ustawia włączony stan dla SNMP V3 wł./wył.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych wersji SNMP
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
Ustawianie prywatnego ciągu agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Opis

Ta usługa ustawia prywatny ciąg społeczności agenta SNMP przy użyciu wejściowego ciągu zakończonego z wartością null. Wartość domyślna to NULL (bez zestawu ciągów prywatnych), tak aby żaden pakiet SNMP otrzymany z "prywatnym" ciągiem społeczności nie został zaakceptowany przez agenta SNMP na potrzeby dostępu do odczytu/zapisu. Ciąg wejściowy musi być mniejszy lub równy rozmiarowi konfigurowalnego przez użytkownika NX_SNMP_MAX_USER_NAME-1 (w celu umożliwienia zakończenia wartości null).

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **community_string** Wskaźnik do ciągu prywatnego do przypisania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono ciąg prywatny
- **NX_SNMP_ERROR_TOOBIG** (0x01) Rozmiar ciągu jest zbyt duży 
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
Ustawianie publicznego ciągu agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Opis

Ta usługa ustawia publiczny ciąg społeczności agenta SNMP na wejściowy ciąg zakończony z wartością null. Ciąg społeczności musi być mniejszy lub równy rozmiarowi konfigurowalnego przez użytkownika NX_SNMP_MAX_USER_NAME-1 (w celu umożliwienia zakończenia wartości null).

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **community_string** Wskaźnik do ciągu publicznego do przypisania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono ciąg publiczny
- **NX_SNMP_ERROR_TOOBIG** (0x01) Rozmiar ciągu jest zbyt duży
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
Usuwanie agenta SNMP

### <a name="prototype"></a>Prototype

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzonego agenta SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie agenta SNMP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Ustawianie interfejsu sieciowego agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Opis

Ta usługa ustawia interfejs sieciowy SNMP dla agenta SNMP określony przez indeks interfejsu wejściowego. Jest to przydatne tylko w przypadku aplikacji hosta SNMP z NetX Duo 5.6 lub wyższym, które obsługują wiele interfejsów sieciowych. Wartość domyślna, jeśli nie zostanie określona przez hosta jest zero dla interfejsu podstawowego.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **If_index** Indeks określający interfejs SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw interfejsów SNMP pomyślnie.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Tworzenie klucza md5 (tylko SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz MD5, który może służyć do uwierzytelniania i szyfrowania.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_snmp_agent_md5_key_create_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **hasło** Wskaźnik do ciągu hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klucza.
- **NX_NOT_ENABLED** (0x14) Zabezpieczenia nie są włączone.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Tworzenie klucza md5 (tylko SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz MD5, który może służyć do uwierzytelniania i szyfrowania.

Ta usługa zastępuje *nx_snmp_agent_md5_key_create().* Ta wersja wymaga, aby wywołujący podał długość hasła.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **hasło** Wskaźnik do ciągu hasła.
- **password_length** Długość ciągu hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klucza.
- **NX_NOT_ENABLED** (0x14) Zabezpieczenia nie są włączone.
- **NX_SNMP_FAILED** (0x102) SNMP nie powiodło się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Określanie klucza szyfrowania dla komunikatów pułapek

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Opis

Ta usługa określa, że wcześniej utworzony klucz prywatności ma być używany do szyfrowania i odszyfrowywania komunikatów pułapek SNMPv3.

> [!NOTE]
> *Klucz uwierzytelniania musi zostać utworzony wcześniej. Prywatność SNMP v3 (szyfrowanie) wymaga uwierzytelniania. Zobacz nx_snmp_agent_auth_trap_key_use, aby uzyskać szczegółowe informacje.*

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **klucz** Wskaźnik do wcześniej utworzyć klucz.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw kluczy prywatności Powodzenie.
- **NX_NOT_ENABLED** (0x14) Zabezpieczenia nie są włączone.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Określanie klucza szyfrowania dla komunikatów odpowiedzi

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Opis

Ta usługa określa, że wcześniej utworzony klucz ma być używany do szyfrowania i odszyfrowywania komunikatów odpowiedzi SNMPv3.

> [!NOTE]
> *Klucz uwierzytelniania musi zostać wcześniej określony. Szyfrowanie SNMP v3 wymaga również utworzenia klucza uwierzytelniania. Zobacz nx_snmp_agent_authentiation_key_use, aby uzyskać szczegółowe informacje.*

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **klucz** Wskaźnik do wcześniej utworzyć klucz.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw kluczy prywatności Powodzenie.
- **NX_NOT_ENABLED** (0x14) Zabezpieczenia nie są włączone.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
Tworzenie klucza SHA (tylko SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz SHA, który może służyć do uwierzytelniania i szyfrowania.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_snmp_agent_sha_key_create_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **hasło** Wskaźnik do ciągu hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klucza.
- **NX_SNMP_ERROR** (0x100) Błąd tworzenia klucza.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy agent SNMP lub wskaźnik klucza.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
Tworzenie klucza SHA (tylko SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz SHA, który może służyć do uwierzytelniania i szyfrowania.

Ta usługa zastępuje *nx_snmp_agent_sha_key_create().* Ta wersja wymaga, aby wywołujący podał długość hasła.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **hasło** Wskaźnik do ciągu hasła.
- **password_length** Długość ciągu hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klucza.
- **NX_SNMP_ERROR** (0x100) Błąd tworzenia klucza.
- **NX_SNMP_FAILED** (0x102) Tworzenie klucza nie powiodło się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy agent SNMP lub wskaźnik klucza.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
Uruchamianie agenta SNMP 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Opis

Ta usługa wiąże gniazdo UDP z portem SNMP 161 i uruchamia zadanie wątku agenta SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne rozpoczęcie agenta SNMP.
- **NX_SNMP_ERROR** (0x100) snmp agent start.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
Zatrzymywanie agenta SNMP 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Opis

Ta usługa zatrzymuje zadanie wątku agenta SNMP i odłącza gniazdo UDP od portu SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie agenta SNMP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik agenta SNMP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Wysyłanie pułapki SNMPv1 *(tylko protokół IPv4)*

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP do Menedżera SNMP pod określonym adresem IPv4. Preferowaną metodą wysyłania pułapki SNMP w netX Duo jest użycie *usługi nxd_snmp_agent_trap_send* sieciowej. *nx_snmp_agent_trap_send* jest dołączony do netx duo w celu obsługi istniejących aplikacji agentów NetX SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IPv4 Menedżera SNMP.
- **enterprise** Enterprise identyfikator obiektu (sysObectID).
- **trap_type** Żądany typ pułapki w następujący sposób:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** Określony kod pułapki.
- **elapsed_time** System czasu został już działania (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości, które mają zostać uwzględnione w pułapce SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv1 nie jest włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
Wysyłanie pułapki SNMPv1 *(IPv4 i IPv6)*

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP do Menedżera SNMP pod określonym adresem IP. Równoważną metodą wysyłania pułapki SNMP w NetX jest *nxd_snmp_agent_trap_send* usługa.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IPv4 lub IPv6 Menedżera SNMP.
- **enterprise** Enterprise identyfikator obiektu (sysObectID).
- **trap_type** Żądany typ pułapki w następujący sposób:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** Określony kod pułapki.
- **elapsed_time** System czasu został już działania (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości, które mają zostać uwzględnione w pułapce SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv1 nie jest włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
Wysyłanie pułapki SNMPv2 (tylko protokół IPv4)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv2 do Menedżera SNMP pod określonym adresem IPv4. Preferowaną metodą wysyłania pułapki SNMP w netX Duo jest użycie *usługi nxd_snmp_agent_trapv2_send* sieciowej. *nx_snmp_agent_trapv2_send* jest dołączony do netX Duo w celu obsługi istniejących aplikacji agentów NetX SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IPv4 Menedżera SNMP.
- **nazwa** Community społeczności (nazwa użytkownika).
- **trap_type**  
   Żądany typ pułapki. Zdarzenia standardowe to:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   W przypadku danych zastrzeżonych:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp.h*)
   
- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapek SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv2 nie jest włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
Wysyłanie pułapki SNMPv2 z bezpośrednim określeniem OID 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv2 do Menedżera SNMP pod określonym adresem IP (tylko IPv4) i umożliwia obiektowi wywołującemu bezpośrednie określenie OID. Preferowaną metodą wysyłania pułapki SNMP z określonym OID w NetX Duo *jest* użycie nxd_snmp_agent_trapv2_oid_send danych. *nx_snmp_agent_trapv2_oid_ do usługi NetX* Duo do obsługi istniejących aplikacji agenta NetX SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IP menedżera SNMP.
- **nazwa** Community społeczności (nazwa użytkownika).
- **oid** Wskaźnik do buforu zawierającego OID.
- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapek SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0x16) Nieprawidłowy agent SNMP lub wskaźnik parametru.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy docelowy adres IP.
- **NX_OPTION_ERROR** (0x0a) Nieprawidłowy parametr.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
Wysyłanie pułapki SNMPv2 (IPv4 i IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP V2 do Menedżera SNMP pod określonym adresem IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IP (IPv4 lub IPv6) menedżera SNMP.
- **nazwa** Community społeczności (nazwa użytkownika).
- **trap_type**  
   Żądany typ pułapki. Zdarzenia standardowe to:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   W przypadku danych zastrzeżonych:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp.h*)

- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapek SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv2 nie jest włączony.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Nieobsługiwana wersja adresu IP
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
Wysyłanie pułapki SNMPv2 z bezpośrednim określeniem OID 

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP v2 do Menedżera SNMP pod określonym adresem IP (IPv4/IPv6) i umożliwia obiektowi wywołującemu bezpośrednie określenie OID.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IP menedżera SNMP (IPv4/IPv6).
- **nazwa** Community społeczności (nazwa użytkownika).
- **oid** Wskaźnik do buforu zawierającego OID.
- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapek SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0x16) Nieprawidłowy agent SNMP lub wskaźnik parametru.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy docelowy adres IP.
- **NX_OPTION_ERROR** (0x0a) Nieprawidłowy parametr.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
Wysyłanie pułapki SNMPv3 (tylko protokół IPv4)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv3 do Menedżera SNMP pod określonym adresem IPv4. Preferowaną metodą wysyłania pułapki SNMP w netX Duo jest użycie *nxd_snmp_agent_trapv3_send* usługi. *nx_snmp_agent_trapv3_send* jest dołączony do usługi NetX Duo w celu obsługi istniejących aplikacji agenta NetX SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IPv4 Menedżera SNMP.
- **nazwa** Community nazwa użytkownika (nazwa użytkownika).
- **trap_type**  
   Żądany typ pułapki. Zdarzenia standardowe to:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   W przypadku danych zastrzeżonych:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp.h*)

- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv3 nie jest włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
Wysyłanie pułapki SNMPv3 z bezpośrednim określeniem OID 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv3 do Menedżera SNMP pod określonym adresem IP (tylko IPv4) i umożliwia obiektowi wywołującemu bezpośrednie określenie OID. Preferowaną metodą wysyłania pułapki SNMP z określonym OID w NetX Duo *jest* użycie nxd_snmp_agent_trapv3_oid_send danych. *nx_snmp_agent_trapv3_oid_ jest dołączony* do usługi NetX Duo w celu obsługi istniejących aplikacji agenta NetX SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IP menedżera SNMP.
- **nazwa** Community nazwa użytkownika (nazwa użytkownika).
- **oid** Wskaźnik do buforu zawierającego OID.
- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0x16) Nieprawidłowy agent SNMP lub wskaźnik parametru.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy docelowy adres IP.
- **NX_OPTION_ERROR** (0x0a) Nieprawidłowy parametr.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
Wysyłanie pułapki SNMPv3 (IPv4 i IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP do Menedżera SNMP pod określonym adresem IP. Ta pułapka jest zasadniczo taka sama jak pułapka SNMP v2, z tą różnicą, że format komunikatu pułapki jest zawarty w pdu SNMP v3.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Adres IP (IPv4 lub IPv6) menedżera SNMP.
- **nazwa** Community nazwa użytkownika (nazwa użytkownika).
- **trap_type**  
   Żądany typ pułapki. Zdarzenia standardowe to:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   W przypadku danych zastrzeżonych:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp.h*)

- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv3 nie jest włączony.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Nieobsługiwana wersja adresu IP
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
Wysyłanie pułapki SNMPv3 z bezpośrednim określeniem OID 

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv3 do Menedżera SNMP pod określonym adresem IP (IPv4/IPv6) i umożliwia obiektowi wywołującemu bezpośrednie określenie OID.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP.
- **ip_address** Wskaźnik do adresu IP menedżera SNMP.
- **nazwa użytkownika** Nazwa użytkownika (nazwa społeczności).
- **oid** Wskaźnik do buforu zawierającego OID.
- **elapsed_time** System czasu został w górę (sysUpTime).
- **object_list_ptr** Tablica obiektów i skojarzonych z nimi wartości do dołączona do pułapki SNMP. Lista zostanie NX_NULL zakończona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny wysyłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0x100) Błąd wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0x16) Nieprawidłowy agent SNMP lub wskaźnik parametru.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy docelowy adres IP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
Ustaw liczbę ponownych uruchomień (jeśli włączono protokół SNMPv3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Opis

Ta usługa ustawia liczbę ponownych uruchomień zarejestrowanych przez agenta SNMP. Ta usługa jest dostępna tylko wtedy, gdy protokół SNMPv3 jest włączony dla agenta SNMP, ponieważ liczba rozruchów jest używana tylko w protokole SNMPv3.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agenta SNMP
- **boots (uruchamia się)** Wartość, na która ma być ustawiona liczba rozruchów agenta SNMP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono liczbę rozruchów
- **NX_SNMP_ERROR** (0x100) Liczba rozruchów ustawienia błędu
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
Porównywanie dwóch obiektów 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Opis

Ta usługa porównuje podany identyfikator obiektu z identyfikatorem obiektu referencyjnego. Oba identyfikatory obiektów znajdują się w notacji SMI ASCII, np. oba obiekty muszą zaczynać się ciągiem ASCII "1.3.6".

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_snmp_object_compare_extended().*

### <a name="input-parameters"></a>Parametry wejściowe

- **obiekt** Wskaźnik do identyfikatora obiektu.
- **reference_object** Wskaźnik do identyfikatora obiektu odniesienia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt pasuje do obiektu odwołania.
- **NX_SNMP_NEXT_ENTRY** (0x101) Obiekt jest mniejszy niż obiekt odwołania.
- **NX_SNMP_ERROR** (0x100) Obiekt jest większy niż obiekt odwołania.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
Porównywanie dwóch obiektów 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Opis

Ta usługa porównuje podany identyfikator obiektu z identyfikatorem obiektu referencyjnego. Oba identyfikatory obiektów znajdują się w notacji SMI ASCII, np. oba obiekty muszą zaczynać się ciągiem ASCII "1.3.6".

Ta usługa zastępuje *nx_snmp_object_compare().* Ta wersja wymaga, aby wywołujący podali informacje o długości.

### <a name="input-parameters"></a>Parametry wejściowe

- **request_object** Wskaźnik do żądania identyfikatora obiektu.
- **request_object_length** Długość identyfikatora obiektu żądania.
- **reference_object** Wskaźnik do identyfikatora obiektu odniesienia.
- **reference_object_length** Długość identyfikatora obiektu odniesienia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt pasuje do obiektu odwołania.
- **NX_SNMP_NEXT_ENTRY** (0x101) Obiekt jest mniejszy niż obiekt odwołania.
- **NX_SNMP_ERROR** (0x100) Obiekt jest większy niż obiekt odwołania.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
Kopiowanie obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>Opis

Ta usługa kopiuje obiekt źródłowy w notacji SIM ASCII do obiektu docelowego.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_snmp_object_copy_extended().*

### <a name="input-parameters"></a>Parametry wejściowe

- **source_object_name** Wskaźnik do identyfikatora obiektu źródłowego.
- **destination_object_name** Wskaźnik do identyfikatora obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **rozmiar** Liczba bajtów skopiowanych do nazwy docelowej. Jeśli wystąpi błąd, zwracane jest zero.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
Kopiowanie obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>Opis

Ta usługa kopiuje obiekt źródłowy w notacji SIM ASCII do obiektu docelowego.

Ta usługa zastępuje *nx_snmp_object_copy().* Ta wersja wymaga, aby wywołujący podali informacje o długości.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_object_name** Wskaźnik do identyfikatora obiektu źródłowego.
- **source_object_name_length** Długość identyfikatora obiektu źródłowego.
- **destination_object_name_buffer** Wskaźnik do buforu obiektu docelowego.
- **destination_object_name_buffer_size** Rozmiar buforu obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **rozmiar** Liczba bajtów skopiowanych do nazwy docelowej. Jeśli wystąpi błąd, zwracane jest zero.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
Pobierz obiekt licznika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Opis

Ta usługa pobiera obiekt licznika pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła licznika.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt licznika został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
Ustaw obiekt licznika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia licznik pod adresem określonym przez wskaźnik docelowy z wartością licznika w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego licznika.
- **object_data** Wskaźnik do struktury obiektu źródłowego licznika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt licznika został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
Pobierz obiekt licznika 64-bitowego 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera 64-bitowy obiekt licznika pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła licznika.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt licznika został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
Ustaw obiekt licznika 64-bitowego 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Opis

Ta usługa ustawia licznik 64-bitowy pod adresem określonym przez wskaźnik docelowy z wartością licznika w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego licznika.
- **object_data** Wskaźnik do struktury obiektu źródłowego licznika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt licznika został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Ustawianie wartości końca mib 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy obiekt sygnalizjący koniec mib i jest zwykle wywoływany z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt końca mib został pomyślnie sbudowaną.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Uzyskiwanie obiektu miernika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt miernika pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła miernika.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt miernika został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Ustawianie obiektu miernika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia miernik pod adresem określonym przez wskaźnik docelowy przy użyciu wartości miernika w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego miernika.
- **object_data** Wskaźnik do miernika struktury obiektu źródłowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt miernika został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
Uzyskiwanie identyfikatora obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera identyfikator obiektu (w notacji SIM ASCII) pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła identyfikatora obiektu.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Identyfikator obiektu został pomyślnie pobrany.
- **NX_SNMP_ERROR** (0x100) Nieprawidłowa długość obiektu
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
Ustawianie identyfikatora obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia identyfikator obiektu (w notacji SIM ASCII) pod adresem określonym przez wskaźnik docelowy z identyfikatorem obiektu w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego identyfikatora obiektu.
- **object_data** Wskaźnik do struktury obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Identyfikator obiektu został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Uzyskiwanie obiektu liczby całkowitej 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt całkowity pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła liczb całkowitych.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt całkowity został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Ustawianie obiektu liczby całkowitej 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia liczbę całkowitą pod adresem określonym przez wskaźnik docelowy przy użyciu wartości całkowitej w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego liczby całkowitej.
- **object_data** Wskaźnik do struktury obiektu źródłowego liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt całkowity został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Uzyskiwanie obiektu adresu IP (tylko protokół IPv4)

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt adresu IP pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła adresu IPv4.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt adresu IP został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Uzyskiwanie obiektu adresu IP (tylko protokół IPv6)

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt adresu IPv6 pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX.
Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła adresu IPv6.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt adresu IP został pomyślnie pobrany.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy wejściowy kod obiektu SNMP
- **NX_NOT_ENABLED** (0x14) protokół IPv6 nie jest włączony
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
Ustawianie obiektu adresu IPv4 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IPv4 pod adresem określonym przez wskaźnik docelowy przy użyciu adresu IP w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do adresu IP do ustawienia.
- **object_data** Wskaźnik do struktury obiektu adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt adresu IP został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
Ustawianie obiektu adresu IPv6 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IPv6 pod adresem określonym przez wskaźnik docelowy przy użyciu adresu IP w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do adresu IP do ustawienia.
- **object_data** Wskaźnik do struktury obiektu adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono adres IPv6.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_NOT_ENABLED** (0x14) IPv6 nie jest włączony
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Ustawianie obiektu bez wystąpienia 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy obiekt sygnalizjący, że nie istnieje żadne wystąpienie określonego obiektu i jest zwykle wywoływany z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt no-instance został pomyślnie sbudowaną.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Ustaw nie znaleziono obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy obiekt sygnalizjący, że obiekt nie został znaleziony i jest zwykle wywoływany z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Nie znaleziono obiektu został pomyślnie s zbudowana.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Pobierz obiekt ciągu oktetu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Opis

Ta usługa pobiera ciąg oktetu pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła ciągu oktetu.
- **object_data** Wskaźnik do struktury obiektu docelowego.
- **długość** Liczba bajtów w ciągu oktetu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt ciągu oktetu został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Ustaw obiekt ciągu oktetu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia ciąg oktetu na adres określony przez wskaźnik docelowy z ciągiem oktetu w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego ciągu oktetu.
- **object_data** Wskaźnik do struktury obiektu źródłowego ciągu oktetu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt ciągu oktetu został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
Pobierz obiekt ciągu ASCII 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera ciąg ASCII pod adresem określonym przez wskaźnik źródłowy i umieszcza go w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła ciągu ASCII.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt ciągu ASCII został pomyślnie pobrany.
- **NX_SNMP_ERROR** (0x100) Ciąg jest zbyt duży  
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Ustawianie obiektu ciągu ASCII 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia ciąg ASCII pod adresem określonym przez wskaźnik docelowy przy użyciu ciągu ASCII w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego ciągu ASCII.
- **object_data** Wskaźnik do struktury obiektu źródłowego ciągu ASCII.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt ciągu ASCII został pomyślnie ustawiony.
- **NX_SNMP_ERROR** (0x100) Ciąg jest zbyt duży.
- **NX_SNMP_ERROR_BADVALUE** (0x03) Nieprawidłowy znak w ciągu
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
Uzyskiwanie obiektu timetics 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera czasy pod adresem określonym przez wskaźnik źródłowy i umieszcza je w strukturze danych obiektu NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji GET lub GETNEXT.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła czasowego.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt timetics został pomyślnie pobrany.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
Ustawianie obiektu timetics 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia zmienną czasową pod adresem określonym przez wskaźnik docelowy za pomocą timetics w strukturze danych obiektu NetX.
Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego aplikacji SET.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego timetics.
- **object_data** Wskaźnik do struktury obiektu źródłowego timetics.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Obiekt timetics został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```