---
title: Rozdział 3 — Opis usług Azure RTO NetX Duo SNMP Agent
description: Ten rozdział zawiera opis wszystkich usług agenta SNMP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821672"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Rozdział 3 — Opis usług Azure RTO NetX Duo SNMP Agent

Ten rozdział zawiera opis wszystkich usług agenta SNMP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Określ klucz uwierzytelniania (tylko protokół SNMP v3) dla komunikatów pułapki*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Określ klucz uwierzytelniania (tylko protokół SNMP v3) dla komunikatów odpowiedzi*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Pobierz nazwę społeczności*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Ustaw aparat kontekstu (tylko protokół SNMP v3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Ustaw nazwę kontekstu (tylko protokół SNMP v3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Utwórz agenta SNMP*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Pobierz wersję protokołu SNMP odebranego pakietu*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Wskaż, czy ostatnie żądanie SNMP ma typ GET lub SET*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Określ, czy ciąg jest zgodny z prywatnym ciągiem agenta*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Określ, czy ciąg jest zgodny z publicznym ciągiem agenta*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Ustawianie interfejsu sieciowego dla obsługi komunikatów SNMP*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Ustaw ciąg społeczności prywatnej agenta SNMP*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Ustaw publiczny ciąg społeczności agenta SNMP*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Ustaw stan agenta SNMP dla wszystkich wersji SNMP*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Usuń agenta SNMP*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Utwórz klucz MD5 (tylko protokół SNMP v3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Utwórz klucz MD5 (tylko protokół SNMP v3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Określ klucz szyfrowania (tylko protokół SNMP v3) dla komunikatów pułapki*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Określ klucz szyfrowania (tylko protokół SNMP v3) dla komunikatów odpowiedzi*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Utwórz klucz SHA (tylko protokół SNMP v3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Utwórz klucz SHA (tylko protokół SNMP v3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Uruchom agenta SNMP*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Zatrzymaj agenta SNMP*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Wyślij pułapkę SNMP v1 (tylko IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Wyślij pułapkę SNMP v2 (tylko IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Wyślij pułapkę SNMP v2 (tylko IPv4) określającą identyfikator OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Wyślij pułapkę SNMP v3 (tylko IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Wyślij pułapkę SNMP v2 (tylko IPv4) określającą identyfikator OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Wyślij pułapkę SNMP v1 (IPv4 i IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Wyślij pułapkę SNMP v2 (IPv4 i IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Wyślij pułapkę SNMP v2 (IPv4/IPv6) określającą identyfikator OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Wyślij pułapkę SNMP v3 (IPv4 i IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Wyślij pułapkę SNMP v2 (IPv4/IPv6) określającą identyfikator OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Ustaw liczbę ponownych uruchomień*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Porównaj dwa obiekty*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Porównaj dwa obiekty*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Kopiowanie obiektu*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Kopiowanie obiektu*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Pobierz obiekt licznika*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Ustaw obiekt licznika*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Pobierz 64-bitowy obiekt licznika*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Ustaw 64-bitowy obiekt licznika*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Ustaw wartość końca MIB*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Pobierz obiekt miernika*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Ustaw obiekt miernika*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Pobierz identyfikator obiektu*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Ustaw identyfikator obiektu*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Pobierz obiekt typu Integer*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Ustaw obiekt liczb całkowitych*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Pobierz obiekt adresu IP (tylko IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Ustawianie obiektu adresu IP (tylko IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Pobieranie obiektu adresu IP (tylko protokół IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Ustawianie obiektu adresu IP (tylko protokół IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Ustaw wartość bez wystąpienia*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Ustaw wartość nie znaleziono*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Pobieranie obiektu ciągu oktetowego*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Ustawianie obiektu ciągu oktetowego*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Pobierz obiekt ciągu ASCII*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Ustaw obiekt ciągu ASCII*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *Pobierz obiekt timetics*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *Ustaw obiekt timetics*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
Określ klucz uwierzytelniania dla komunikatów pułapki

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Opis

Ta usługa określa klucz, który ma być używany do ustawiania parametrów uwierzytelniania w nagłówku zabezpieczeń SNMPv3 w komunikatach pułapki. Podanie wartości NX_NULL klucza powoduje wyłączenie uwierzytelniania.

> [!NOTE]
> Należy wcześniej utworzyć klucz. Zobacz nx_snmp_agent_md5_key_create lub nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **klucz** Wskaźnik do wcześniej utworzonego klucza MD5 lub SHA.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne uwierzytelnianie zestawu kluczy.
- **NX_NOT_ENABLED** (0X14) zabezpieczenia protokołu SNMP wyłączone 
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta SNMP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
Określ klucz uwierzytelniania dla komunikatów odpowiedzi

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Opis

Ta usługa określa klucz, który ma być używany dla parametrów uwierzytelniania w parametrze zabezpieczeń SNMPv3 dla wszystkich żądań wykonanych po jej ustawieniu. Podanie wartości NX_NULL klucza powoduje wyłączenie uwierzytelniania.

> [!NOTE]
> Należy wcześniej utworzyć klucz. Zobacz nx_snmp_agent_md5_key_create lub nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **klucz** Wskaźnik do wcześniej utworzonego klucza MD5 lub SHA.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawiono klucz SNMP.
- **NX_NOT_ENABLED** (0X14) zabezpieczenia protokołu SNMP wyłączone
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta SNMP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Pobierz nazwę społeczności

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera nazwę społeczności z najnowszego żądania SNMP otrzymanego przez agenta SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **community_string_ptr** Wskaźnik na wskaźnik ciągu, aby zwrócić ciąg identyfikacyjny agenta SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie pobiera społeczność SNMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa wskazuje, czy najnowsze żądanie od menedżera SNMP to GET (GET, GetNext lub GetBulk) lub typu zestawu. Jest ona przeznaczona do użycia z wywołaniem zwrotnym nazwy użytkownika, w którym aplikacja SNMPv1 lub SNMPv2 będzie chcieć porównać otrzymany ciąg identyfikacyjny z publicznym ciągiem agenta SNMP, jeśli żądanie jest typu GET lub do prywatnego ciągu agenta SNMP, jeśli żądanie jest typem zestawu.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **is_get_type** Wskaźnik do stanu typu żądania:  
NX_TRUE Jeśli typ pobrania  
NX_FALSE Jeśli typ zestawu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zwrócił typ
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Ustaw aparat kontekstu (tylko protokół SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Opis

Ta usługa ustawia aparat kontekstu agenta SNMP. Ma to zastosowanie tylko w przypadku przetwarzania SNMPv3. Należy to wywołać przed utworzeniem kluczy zabezpieczeń, jeśli aplikacja korzysta z uwierzytelniania i szyfrowania, ponieważ w procesie tworzenia klucza jest używany identyfikator aparatu kontekstu. Jeśli nie, NetX Duo SNMP zapewnia domyślny identyfikator aparatu kontekstu w górnej części *nxd_snmp. c:*

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **context_engine** Wskaźnik na ciąg aparatu kontekstu.
- **context_engine_size** Rozmiar ciągu aparatu kontekstu. Należy zauważyć, że maksymalna liczba bajtów w aparacie kontekstu jest definiowana przez NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) zestaw aparatów kontekstu SNMP zakończony pomyślnie.
- **NX_NOT_ENABLED** (0X14) SNMPv3 nie jest włączona
- Błąd rozmiaru aparatu **NX_SNMP_ERROR** (0x100).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Ustaw nazwę kontekstu (tylko protokół SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę kontekstu agenta SNMP. Ma to zastosowanie tylko w przypadku przetwarzania SNMPv3. Jeśli nie zostanie wywołana, Agent SNMP NetX Duo pozostawi pustej nazwy kontekstu.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **context_name** Wskaźnik na ciąg nazwy kontekstu.
- **context_name_size** Rozmiar ciągu nazwy kontekstu. Należy zauważyć, że maksymalna liczba bajtów w nazwie kontekstu jest definiowana przez NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślna Nazwa kontekstu SNMP.
- Błąd rozmiaru nazwy kontekstu **NX_SNMP_ERROR** (0x100).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
Utwórz agenta SNMP

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

Ta usługa tworzy agenta SNMP dla określonego wystąpienia IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **snmp_agent_name** Wskaźnik do ciągu nazwy agenta SNMP.
- **ip_ptr** Wskaźnik na wystąpienie adresu IP.
- **stack_ptr** Wskaźnik do wskaźnika stosu wątku agenta SNMP.
- **stack_size** Rozmiar stosu w bajtach.
- **pool_ptr** Wskaźnik domyślnej puli pakietów dla tego agenta SNMP.
- **snmp_agent_username_process** Wskaźnik funkcji do procedury obsługi nazwy użytkownika aplikacji.
- **snmp_agent_get_process** Wskaźnik funkcji do procedury obsługi żądania GET.
- **snmp_agent_getnext_process** Wskaźnik funkcji do procedury obsługi GetNext Request dla aplikacji.
- **snmp_agent_set_process** Wskaźnik funkcji do procedury obsługi żądania zestawu aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie agenta SNMP.
- **NX_SNMP_ERROR** (0x100) wystąpił błąd podczas tworzenia agenta SNMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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
Pobierz wersję pakietu SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wersję protokołu SNMP przeanalizowane z ostatniego odebranego pakietu SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **wersja** Wskaźnik do wersji SNMP przeanalizowanej z odebranego pakietu SNMP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie wersji SNMP
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

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
Sprawdź, czy ciąg prywatny jest zgodny z prywatnym ciągiem agenta

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Opis

Ta usługa porównuje ciąg identyfikacyjny zakończony zerem o wartości null z prywatnym ciągiem agenta SNMP i wskazuje, czy są one zgodne.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **community_string** Wskaźnik do ciągu do porównania
- **is_private** Wskaźnik do wyniku porównania  
Dopasowania ciągu NX_TRUE  
NX_FALSE — ciąg nie jest zgodny

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne porównanie **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

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
Sprawdź, czy otrzymany ciąg publiczny jest zgodny z publicznym ciągiem agenta

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Opis

Ta usługa porównuje ciąg identyfikacyjny zakończony zerem o wartości null z publicznym ciągiem agenta SNMP i wskazuje, czy są one zgodne.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **community_string** Wskaźnik do ciągu do porównania
- **is_public** Wskaźnik do wyniku porównania  
Dopasowania ciągu NX_TRUE  
NX_FALSE — ciąg nie jest zgodny

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne porównanie **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

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
Ustaw stan agenta SNMP dla każdej wersji SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Opis

Ta usługa ustawia stan (włączony/wyłączony) dla każdego z wersji SNMP, v1, v2 i V3 w agencie SNMP. Należy pamiętać, że opcje konfigurowane przez użytkownika, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 i NX_SNMP_DISABLE_V3, przesłonią te ustawienia czasu wykonywania. Domyślnie Agent SNMP jest włączony dla wszystkich trzech wersji.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **enabled_v1** Ustawia stan włączenia protokołu SNMP v1 na Włącz/Wyłącz.
- **enabled_v2** Ustawia stan włączenia protokołu SNMP V2 na Włącz/Wyłącz.
- **enabled_v3** Ustawia stan włączenia protokołu SNMP V3 na Włącz/Wyłącz.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne Ustawianie wersji SNMP
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

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
Ustaw ciąg prywatny agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Opis

Ta usługa ustawia ciąg społeczności prywatnej agenta SNMP z ciągiem zakończonym zerem o wartości null. Wartość domyślna to NULL (bez prywatnego zestawu parametrów), w taki sposób, że żaden pakiet SNMP otrzymany z "prywatnym" ciągiem Wspólnoty nie zostanie zaakceptowany przez agenta SNMP na potrzeby dostępu do odczytu i zapisu. Ciąg wejściowy musi być mniejszy niż lub równy użytkownikowi konfigurowalnemu NX_SNMP_MAX_USER_NAME-1 (aby można było pozostawić miejsce na zakończenie o wartości null).

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **community_string** Wskaźnik do prywatnego ciągu do przypisania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił ciąg prywatny
- Rozmiar ciągu **NX_SNMP_ERROR_TOOBIG** (0x01) jest zbyt duży 
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

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
Ustawianie ciągu publicznego agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Opis

Ta usługa ustawia ciąg społeczności publicznej agenta SNMP z ciągiem zakończonym zerem o wartości null. Ciąg identyfikacyjny nie może być mniejszy niż lub równy użytkownikowi konfigurowalnemu NX_SNMP_MAX_USER_NAME-1 (aby można było zwolnić miejsce na zakończenie o wartości null).

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **community_string** Wskaźnik na ciąg publiczny do przypisania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił ciąg publiczny
- Rozmiar ciągu **NX_SNMP_ERROR_TOOBIG** (0x01) jest zbyt duży
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

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
Usuń agenta SNMP

### <a name="prototype"></a>Prototype

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzonego agenta SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie agenta SNMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Ustaw interfejs sieciowy agenta SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Opis

Ta usługa ustawia interfejs sieciowy SNMP dla agenta SNMP określony przez indeks interfejsu wejściowego. Jest to przydatne tylko w przypadku aplikacji hosta SNMP z NetX Duo 5,6 lub nowszymi, które obsługują wiele interfejsów sieciowych. Wartość domyślna, jeśli nie zostanie określona przez hosta, wynosi zero dla interfejsu podstawowego.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **If_index** Indeks określający interfejs SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawiono interfejs SNMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Utwórz klucz MD5 (tylko protokół SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz MD5, który może służyć do uwierzytelniania i szyfrowania.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_snmp_agent_md5_key_create_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **hasło** Wskaźnik na ciąg hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).
- Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Utwórz klucz MD5 (tylko protokół SNMP v3)

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

Ta usługa zastępuje *nx_snmp_agent_md5_key_create ().* Ta wersja wymaga, aby obiekt wywołujący dostarczał długość hasła.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **hasło** Wskaźnik na ciąg hasła.
- **password_length** Długość ciągu hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).
- Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).
- **NX_SNMP_FAILED** (0X102) SNMP nie powiodło się.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Określ klucz szyfrowania dla komunikatów pułapki

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Opis

Ta usługa określa, że wcześniej utworzony klucz prywatności ma być używany do szyfrowania i odszyfrowywania komunikatów pułapki SNMPv3.

> [!NOTE]
> *Należy wcześniej utworzyć klucz authentictation. W przypadku protokołu SNMP v3 (szyfrowanie) wymagane jest uwierzytelnienie. Aby uzyskać szczegółowe informacje, zobacz nx_snmp_agent_auth_trap_key_use.*

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **klucz** Wskaźnik do wcześniej utworzonego klucza.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawiono klucz prywatności.
- Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Określ klucz szyfrowania dla komunikatów odpowiedzi

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Opis

Ta usługa określa, że utworzony wcześniej klucz ma być używany do szyfrowania i odszyfrowywania komunikatów odpowiedzi SNMPv3.

> [!NOTE]
> *Należy wcześniej określić klucz uwierzytelniania. Szyfrowanie SNMP v3 wymaga również utworzenia klucza uwierzytelniania. Aby uzyskać szczegółowe informacje, zobacz nx_snmp_agent_authentiation_key_use.*

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **klucz** Wskaźnik do wcześniej utworzonego klucza.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawiono klucz prywatności.
- Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
Utwórz klucz SHA (tylko protokół SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz SHA, który może być używany do uwierzytelniania i szyfrowania.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_snmp_agent_sha_key_create_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **hasło** Wskaźnik na ciąg hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).
- Błąd tworzenia klucza **NX_SNMP_ERROR** (0x100).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta lub klucza SNMP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
Utwórz klucz SHA (tylko protokół SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Opis

Ta usługa tworzy klucz SHA, który może być używany do uwierzytelniania i szyfrowania.

Ta usługa zastępuje *nx_snmp_agent_sha_key_create ().* Ta wersja wymaga, aby obiekt wywołujący dostarczał długość hasła.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **hasło** Wskaźnik na ciąg hasła.
- **password_length** Długość ciągu hasła.
- **destination_key** Wskaźnik do struktury danych klucza SNMP.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).
- Błąd tworzenia klucza **NX_SNMP_ERROR** (0x100).
- Tworzenie klucza **NX_SNMP_FAILED** (0x102) nie powiodło się.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta lub klucza SNMP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
Uruchom agenta SNMP 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Opis

Ta usługa wiąże gniazdo UDP z portem SNMP 161 i uruchamia zadanie wątku agenta SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie agenta SNMP.
- **NX_SNMP_ERROR** (0x100) błąd uruchamiania agenta SNMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
Zatrzymaj agenta SNMP 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Opis

Ta usługa przerywa zadanie wątku agenta SNMP i rozwiąże gniazdo UDP z portem SNMP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zatrzymanie agenta SNMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta SNMP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Wyślij pułapki SNMPv1 *(tylko IPv4)*

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP do menedżera SNMP na określonym adresie IPv4. Preferowaną metodą wysyłania pułapki SNMP w NetX Duo jest użycie usługi *nxd_snmp_agent_trap_send* . *nx_snmp_agent_trap_send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IPv4 menedżera SNMP.
- **przedsiębiorstwo** Ciąg identyfikatora obiektu przedsiębiorstwa (sysObectID).
- **trap_type** Typ żądania pułapki w następujący sposób:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** Konkretny kod pułapki.
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0X14) SNMPv1 nie jest włączona.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

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
Wyślij pułapki SNMPv1 *(IPv4 i IPv6)*

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMP do menedżera SNMP na określonym adresie IP. Równoważną metodą wysyłania pułapki SNMP w NetX jest usługa *nxd_snmp_agent_trap_send* .

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IPv4 lub IPv6 menedżera SNMP.
- **przedsiębiorstwo** Ciąg identyfikatora obiektu przedsiębiorstwa (sysObectID).
- **trap_type** Typ żądania pułapki w następujący sposób:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** Konkretny kod pułapki.
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0X14) SNMPv1 nie jest włączona.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

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
Wyślij pułapkę SNMPv2 (tylko IPv4)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv2 do menedżera SNMP na określonym adresie IPv4. Preferowaną metodą wysyłania pułapki SNMP w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv2_send* . *nx_snmp_agent_trapv2_send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IPv4 menedżera SNMP.
- **społeczność** Nazwa Wspólnoty (username).
- **trap_type**  
   Typ żądanego pułapki. Standardowe zdarzenia to:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   W przypadku danych zastrzeżonych:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)
   
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0X14) SNMPv2 nie jest włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

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
Wysyłanie pułapki SNMPv2 Określanie identyfikatora OID bezpośrednio 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapkę SNMPv2 do menedżera SNMP pod określonym adresem IP (tylko IPv4) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID. Preferowaną metodą wysyłania pułapki SNMP z określonym identyfikatorem OID w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv2_oid_send* . *nx_snmp_agent_trapv2_oid_ Send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IP menedżera SNMP.
- **społeczność** Nazwa Wspólnoty (username).
- **Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.
- **NX_OPTION_ERROR** (0X0a) nieprawidłowy parametr.

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

Ta usługa wysyła do menedżera SNMP pułapkę SNMP v2 o określonym adresie IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IP (IPv4 lub IPv6) menedżera SNMP.
- **społeczność** Nazwa Wspólnoty (username).
- **trap_type**  
   Typ żądanego pułapki. Standardowe zdarzenia to:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   W przypadku danych zastrzeżonych:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)

- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0X14) SNMPv2 nie jest włączony.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) nieobsługiwana wersja protokołu IP
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

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
Wysyłanie pułapki SNMPv2 Określanie identyfikatora OID bezpośrednio 

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

Ta usługa wysyła pułapkę protokołu SNMP v2 do menedżera SNMP pod określonym adresem IP (IPv4/IPv6) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IP menedżera SNMP (IPv4/IPv6).
- **społeczność** Nazwa Wspólnoty (username).
- **Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.
- **NX_OPTION_ERROR** (0X0a) nieprawidłowy parametr.

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
Wyślij pułapkę SNMPv3 (tylko IPv4)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pułapki SNMPv3 do menedżera SNMP na określonym adresie IPv4. Preferowaną metodą wysyłania pułapki SNMP w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv3_send* . *nx_snmp_agent_trapv3_send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IPv4 menedżera SNMP.
- **Nazwa użytkownika** Nazwa Wspólnoty (username).
- **trap_type**  
   Typ żądanego pułapki. Standardowe zdarzenia to:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   W przypadku danych zastrzeżonych:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)

- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0X14) SNMPv3 nie jest włączona.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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
Wysyłanie pułapki SNMPv3 Określanie identyfikatora OID bezpośrednio 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Opis

Ta usługa wysyła pułapki SNMPv3 do menedżera SNMP pod określonym adresem IP (tylko IPv4) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID. Preferowaną metodą wysyłania pułapki SNMP z określonym identyfikatorem OID w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv3_oid_send* . *nx_snmp_agent_trapv3_oid_ Send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IP menedżera SNMP.
- **Nazwa użytkownika** Nazwa Wspólnoty (username).
- **Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.
- **NX_OPTION_ERROR** (0X0a) nieprawidłowy parametr.

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

Ta usługa wysyła pułapkę SNMP do menedżera SNMP na określonym adresie IP. Ta Pułapka jest zasadniczo taka sama jak pułapka SNMP v2, z wyjątkiem tego, że format komunikatu pułapki jest zawarty w jednostce PDU protokołu SNMP v3.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Adres IP (IPv4 lub IPv6) menedżera SNMP.
- **Nazwa użytkownika** Nazwa Wspólnoty (username).
- **trap_type**  
   Typ żądanego pułapki. Standardowe zdarzenia to:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   W przypadku danych zastrzeżonych:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)

- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_NOT_ENABLED** (0X14) SNMPv3 nie jest włączona.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) nieobsługiwana wersja protokołu IP
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

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
Wysyłanie pułapki SNMPv3 Określanie identyfikatora OID bezpośrednio 

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

Ta usługa wysyła pułapki SNMPv3 do menedżera SNMP przy użyciu określonego adresu IP (IPv4/IPv6) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.
- **IP_address** Wskaźnik na adres IP menedżera SNMP.
- **Nazwa użytkownika** Nazwa użytkownika (nazwa Wspólnoty).
- **Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.
- **elapsed_time** System czasu został osiągnięty (sysUpTime).
- **object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP. Lista została zakończona NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.
- **NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.
- **NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.

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
Ustaw liczbę ponownych uruchomień (Jeśli włączono funkcję SNMPv3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Opis

Ta usługa ustawia liczbę ponownych uruchomień zarejestrowanych przez agenta SNMP. Ta usługa jest dostępna tylko wtedy, gdy dla agenta SNMP jest włączona funkcja SNMPv3, ponieważ liczba rozruchowych jest używana tylko w protokole SNMPv3.

### <a name="input-parameters"></a>Parametry wejściowe

- **agent_ptr** Wskaźnik do bloku sterowania agentami SNMP
- **rozruch** Wartość, dla której ma zostać ustawiona liczba rozruchowych agentów SNMP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił liczbę rozruchów
- **NX_SNMP_ERROR** (0x100) — Ustawianie błędu liczby rozruchowych
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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
Porównaj dwa obiekty 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Opis

Ta usługa porównuje podany identyfikator obiektu z IDENTYFIKATORem obiektu odwołania. Oba identyfikatory obiektów znajdują się w notacji typu ASCII SMI, np. oba obiekty muszą zaczynać się od ciągu ASCII "1.3.6".

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_snmp_object_compare_extended ().*

### <a name="input-parameters"></a>Parametry wejściowe

- **obiekt** Wskaźnik do obiektu ID.
- **reference_object** Wskaźnik na identyfikator obiektu odwołania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt jest zgodny z obiektem Reference.
- **NX_SNMP_NEXT_ENTRY** (0x101) obiekt jest mniejszy niż obiekt Reference.
- **NX_SNMP_ERROR** (0x100) obiekt jest większy niż obiekt Reference.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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
Porównaj dwa obiekty 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Opis

Ta usługa porównuje podany identyfikator obiektu z IDENTYFIKATORem obiektu odwołania. Oba identyfikatory obiektów znajdują się w notacji typu ASCII SMI, np. oba obiekty muszą zaczynać się od ciągu ASCII "1.3.6".

Ta usługa zastępuje *nx_snmp_object_compare ().* Ta wersja wymaga, aby wywołujący dostarczali informacje o długości.

### <a name="input-parameters"></a>Parametry wejściowe

- **request_object** Wskaźnik do żądania identyfikatora obiektu.
- **request_object_length** Długość identyfikatora obiektu żądania.
- **reference_object** Wskaźnik na identyfikator obiektu odwołania.
- **reference_object_length** Długość identyfikatora obiektu odwołania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt jest zgodny z obiektem Reference.
- **NX_SNMP_NEXT_ENTRY** (0x101) obiekt jest mniejszy niż obiekt Reference.
- **NX_SNMP_ERROR** (0x100) obiekt jest większy niż obiekt Reference.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa kopiuje obiekt źródłowy w notacji programu ASCII SIM do obiektu docelowego.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_snmp_object_copy_extended ().*

### <a name="input-parameters"></a>Parametry wejściowe

- **source_object_name** Wskaźnik na identyfikator obiektu źródłowego.
- **destination_object_name** Wskaźnik do docelowego identyfikatora obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **rozmiar** Liczba bajtów skopiowanych do nazwy docelowej. Jeśli błąd, zwracana jest wartość zero.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa kopiuje obiekt źródłowy w notacji programu ASCII SIM do obiektu docelowego.

Ta usługa zastępuje *nx_snmp_object_copy ().* Ta wersja wymaga, aby wywołujący dostarczali informacje o długości.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_object_name** Wskaźnik na identyfikator obiektu źródłowego.
- **source_object_name_length** Długość identyfikatora obiektu źródłowego.
- **destination_object_name_buffer** Wskaźnik do buforu obiektów docelowych.
- **destination_object_name_buffer_size** Rozmiar buforu obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **rozmiar** Liczba bajtów skopiowanych do nazwy docelowej. Jeśli błąd, zwracana jest wartość zero.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa pobiera obiekt licznika pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła licznika.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt licznika został pomyślnie pobrany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa ustawia licznik na adres określony przez wskaźnik docelowy z wartością licznika w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do elementu docelowego licznika.
- **object_data** Wskaźnik do struktury obiektu źródłowego licznika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt licznika został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
Pobierz 64-bitowy obiekt licznika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera 64-bitowy obiekt licznika pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła licznika.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt licznika został pomyślnie pobrany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
Ustaw 64-bitowy obiekt licznika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Opis

Ta usługa ustawia 64-bitowy licznik na adres określony przez wskaźnik docelowy z wartością licznika w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do elementu docelowego licznika.
- **object_data** Wskaźnik do struktury obiektu źródłowego licznika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt licznika został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Ustaw wartość końca MIB 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy obiekt sygnalizujący koniec MIB i jest zazwyczaj wywoływany z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt końca bazy MIB został pomyślnie skompilowany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Pobierz obiekt miernika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt miernika pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła miernika.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt miernika został pomyślnie pobrany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Ustaw obiekt miernika 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia miernik na adres określony przez wskaźnik docelowy z wartością miernika w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego miernika.
- **object_data** Wskaźnik do struktury obiektu źródłowego miernika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt miernika został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
Pobierz identyfikator obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa Pobiera identyfikator obiektu (w notacji ASCII SIM) pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła identyfikatora obiektu.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) identyfikator obiektu został pomyślnie pobrany.
- **NX_SNMP_ERROR** (0X100) Nieprawidłowa długość obiektu
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
Ustaw identyfikator obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia identyfikator obiektu (w notacji XML SIM) na adres określony przez wskaźnik docelowy z IDENTYFIKATORem obiektu w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do obiektu docelowego o IDENTYFIKATORze.
- **object_data** Wskaźnik do struktury obiektu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) identyfikator obiektu został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Pobierz obiekt typu Integer 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt liczby całkowitej na adres określony przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik na źródło wartości całkowitej.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnie pobrano obiekt typu Integer.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Ustaw obiekt liczb całkowitych 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia liczbę całkowitą na adres określony przez wskaźnik docelowy za pomocą wartości całkowitej w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik na miejsce docelowe liczby całkowitej.
- **object_data** Wskaźnik do struktury obiektów źródłowych w postaci liczby całkowitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnie ustawiono obiekt typu Integer.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Pobierz obiekt adresu IP (tylko IPv4)

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt adresu IP pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik na źródło adresów IPv4.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt adresu IP został pomyślnie pobrany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Pobieranie obiektu adresu IP (tylko protokół IPv6)

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera obiekt adresu IPv6 pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.
Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik na źródło adresów IPv6.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt adresu IP został pomyślnie pobrany.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) nieprawidłowy wejściowy kod obiektu SNMP
- **NX_NOT_ENABLED** (0X14) protokół IPv6 nie jest włączony
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa ustawia adres IPv4 na adres określony przez wskaźnik docelowy przy użyciu adresu IP w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik na adres IP, który ma zostać ustawiony.
- **object_data** Wskaźnik do struktury obiektów adresów IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt adresu IP został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa ustawia adres IPv6 pod adresem wskazanym przez wskaźnik docelowy przy użyciu adresu IP w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik na adres IP, który ma zostać ustawiony.
- **object_data** Wskaźnik do struktury obiektów adresów IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) adres IPv6 został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_NOT_ENABLED** (0X14) protokół IPv6 nie jest włączony
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Ustaw obiekt bez wystąpienia 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy obiekt sygnalizujący, że nie ma żadnego wystąpienia określonego obiektu i jest zazwyczaj wywoływany z procedury wywołania zwrotnego GET lub GetNext Application.

### <a name="input-parameters"></a>Parametry wejściowe

- **not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt bez wystąpienia został pomyślnie skompilowany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Nie znaleziono obiektu 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy obiekt sygnalizujący, że obiekt nie został odnaleziony i jest zazwyczaj wywoływany z procedury wywołania zwrotnego GET lub GetNext Application.

### <a name="input-parameters"></a>Parametry wejściowe

- **not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt, który nie został znaleziony, został pomyślnie skompilowany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Pobieranie obiektu ciągu oktetowego 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Opis

Ta usługa Pobiera ciąg oktetowy pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik na źródło ciągu oktetowego.
- **object_data** Wskaźnik do struktury obiektu docelowego.
- **Długość** Liczba bajtów w ciągu oktetu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt ciągu oktetowego został pomyślnie pobrany.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Ustawianie obiektu ciągu oktetowego 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia ciąg oktetu na adres określony przez wskaźnik docelowy z ciągiem oktetu w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik na miejsce docelowe ciągu oktetowego.
- **object_data** Wskaźnik na strukturę obiektu źródłowego ciągu oktetowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt ciągu oktetowego został pomyślnie ustawiony.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa Pobiera ciąg ASCII pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła ciągu ASCII.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt ciągu ASCII został pomyślnie pobrany.
- Ciąg **NX_SNMP_ERROR** (0x100) jest zbyt duży  
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Ustaw obiekt ciągu ASCII 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia ciąg ASCII na adres określony przez wskaźnik docelowy z ciągiem ASCII w strukturze danych obiektów NetX. Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do miejsca docelowego ciągu ASCII.
- **object_data** Wskaźnik do struktury obiektu źródłowego ciągu ASCII.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) obiekt ciągu ASCII został pomyślnie ustawiony.
- Ciąg **NX_SNMP_ERROR** (0x100) jest zbyt duży.
- **NX_SNMP_ERROR_BADVALUE** (0X03) nieprawidłowy znak w ciągu
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
Pobierz obiekt timetics 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa pobiera timetics pod adresem określonym przez wskaźnik źródła i umieszcza je w strukturze danych obiektów NetX. Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **source_ptr** Wskaźnik do źródła timetics.
- **object_data** Wskaźnik do struktury obiektu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnie pobrano obiekt timetics.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
Ustaw obiekt timetics 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Opis

Ta usługa ustawia zmienną timetics na adres określony przez wskaźnik docelowy z timetics w strukturze danych obiektów NetX.
Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **destination_ptr** Wskaźnik do lokalizacji docelowej timetics.
- **object_data** Wskaźnik do timetics struktury obiektów źródłowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnie ustawiono obiekt timetics.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```