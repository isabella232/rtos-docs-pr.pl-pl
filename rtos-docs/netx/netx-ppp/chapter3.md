---
title: Rozdział 3 — Opis usług Azure RTOS NetX Point-to-Point Protocol (PPP)
description: Ten rozdział zawiera opis wszystkich usług AZURE RTOS NetX PPP (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 980348b5c50acfb82b2d8fda8786a1d48bf59c69e7949b6f62b64515b59bf42d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798762"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a>Rozdział 3 — Opis usług Azure RTOS NetX Point-to-Point Protocol (PPP)

Ten rozdział zawiera opis wszystkich usług AZURE RTOS NetX PPP (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_ppp_byte_receive:** *odbieranie bajtu z szeregowego isr*
- **nx_ppp_chap_challenge:** Generowanie *wyzwania protokołu CHAP*
- **nx_ppp_chap_enable:** Włączanie *uwierzytelniania protokołu CHAP*
- **nx_ppp_create:** Tworzenie *wystąpienia protokołu PPP*
- **nx_ppp_delete:** Usuwanie *wystąpienia PROTOKOŁU PPP*
- **nx_ppp_dns_address_get:** Uzyskiwanie *adresu IP DNS*
- **nx_ppp_dns_address_set:***ustaw adres IP serwera DNS*
- **nx_ppp_secondary_dns_address_get:** uzyskiwanie *pomocniczego adresu IP serwera DNS*
- **nx_ppp_secondary_dns_address_set:** ustaw *Secondary_DNS IP serwera*
- **nx_ppp_interface_index_get:** Uzyskiwanie *indeksu interfejsu IP*
- **nx_ppp_ip_address_assign:** *Przypisywanie adresów IP dla ipcp*
- **nx_ppp_link_down_notify:** *Powiadamianie aplikacji przy linku*
- **nx_ppp_link_up_notify:** *Powiadamianie aplikacji o linku*
- **nx_ppp_nak_authentication_notify:** *powiadamianie aplikacji o otrzymaniu uwierzytelniania NAK*
- **nx_ppp_pap_enable:** Włączanie *uwierzytelniania PAP*
- **nx_ppp_ping_request:** Wysyłanie *żądania echa LCP*
- **nx_ppp_raw_string_send:** Wyślij *ciąg niebędący ciągiem PROTOKOŁU PPP*
- **nx_ppp_restart:** Ponowne *uruchamianie przetwarzania PROTOKOŁU PPP*
- **nx_ppp_start:** Uruchamianie *przetwarzania PROTOKOŁU PPP*
- **nx_ppp_status_get:** *Uzyskiwanie bieżącego stanu PROTOKOŁU PPP*
- **nx_ppp_stop:** *Zatrzymaj przetwarzanie PROTOKOŁU PPP*
- **nx_ppp_packet_receive:** Odbieranie *pakietu PPP*
- **nx_ppp_packet_send_set:** *Ustaw funkcję wysyłania pakietów PPP*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Odbieranie bajtu od szeregowego isr

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Opis

Ta usługa jest zwykle wywoływana z procedury obsługi przerwań (ISR) sterownika szeregowego aplikacji w celu przekazania odebranego bajtu do protokołu PPP. Gdy ta procedura jest wywoływana, umieszcza odebrany bajt w cyklicznym buforze bajtów i powiadamia odpowiedni wątek PPP do przetworzenia.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **bajt: bajt** odebrany z urządzenia szeregowego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne odbieranie bajtów PPP.
- **NX_PPP_BUFFER_FULL:**(0xB1) Bufor szeregowy PPP jest już pełny.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Wątki, isRs

### <a name="example"></a>Przykład

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

Generowanie wyzwania protokołu CHAP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa inicjuje wyzwanie protokołu CHAP, gdy połączenie PPP jest już uruchomione. Dzięki temu aplikacja może okresowo weryfikować autentyczność połączenia. Jeśli wyzwanie nie powiedzie się, link PPP zostanie zamknięty.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zainicjowanie pomyślnego wyzwania PPP.
- **NX_PPP_FAILURE:**(0xB0) Nieprawidłowe wyzwanie PPP, protokół CHAP został włączony tylko dla odpowiedzi.
- **NX_NOT_IMPLEMENTED:** logika protokołu CHAP (0x80) została wyłączona za pośrednictwem NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

Włączanie uwierzytelniania protokołu CHAP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>Opis

Ta usługa włącza protokół Challenge-Handshake Authentication Protocol (CHAP) dla określonego wystąpienia protokołu PPP.

Jeśli określono wskaźniki funkcji "***get_challenge_values**" i _" get_verification_values_**", protokół CHAP jest wymagany * przez to wystąpienie protokołu PPP. W przeciwnym razie protokół CHAP odpowiada tylko na żądania wyzwania elementu równorzędnego.

Istnieje kilka elementów danych przywołynych poniżej w wymaganych funkcjach wywołania zwrotnego. Klucz tajny elementów *danych,* *nazwa* i *system* powinny być ciągami zakończonymi wartością NULL o maksymalnym rozmiarze NX_PPP_NAME_SIZE-1. Oczekuje *się, rand_value* element danych będzie ciągiem zakończonym wartością NULL o maksymalnym rozmiarze NX_PPP_VALUE_SIZE-1. Identyfikator elementu *danych jest* prostym typem znaku bez znaku.

>[!NOTE]
> Ta funkcja musi być wywoływana po *nx_ppp_create* ale przed nx_ip_create lub *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **get_challenge_values:** Wskaźnik do funkcji aplikacji w celu pobrania wartości użytych do zadania. Pamiętaj, *że rand_value*, *id* i *secret* muszą zostać skopiowane do podanych miejsc docelowych.
- **get_responder_values:** Wskaźnik do funkcji aplikacji, która pobiera wartości używane do reagowania na wyzwanie. Należy pamiętać, *że wartości systemowe*, *nazwy* i *tajne* muszą zostać skopiowane do podanych miejsc docelowych.
- **get_verification_values:** Wskaźnik do funkcji aplikacji, która pobiera wartości używane do weryfikowania odpowiedzi na wyzwanie. Należy pamiętać, *że wartości systemowe*,*nazwy* i *tajne* muszą zostać skopiowane do podanych miejsc docelowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne włączenie protokołu CHAP protokołu PPP
- **NX_NOT_IMPLEMENTED:** logika protokołu CHAP (0x80) została wyłączona za pośrednictwem NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji wywołania zwrotnego. Należy pamiętać, *że get_challenge_values* jest określona, należy *get_verification_values* również podać funkcję.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a>nx_ppp_create

Tworzenie wystąpienia protokołu PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie protokołu PPP dla określonego wystąpienia adresu IP NetX.

>[!NOTE]
> Zazwyczaj dobrym pomysłem jest utworzenie wątku ip NetX o wyższym priorytecie niż priorytet wątku PPP. Zapoznaj się z *usługą nx_ip_create,* aby uzyskać więcej informacji na temat określania priorytetu wątku ip.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **name**: nazwa tego wystąpienia PROTOKOŁU PPP.
- **ip_ptr:** Wskaźnik do bloku sterowania dla jeszcze nie utworzonego wystąpienia adresu IP.
- **stack_memory_ptr:** Wskaźnik do rozpoczęcia obszaru stosu wątku PPP.
- **stack_size:** rozmiar w bajtach w stosie wątku.
- **pool_ptr:** Wskaźnik do domyślnej puli pakietów.
- **thread_priority:** Priorytet wewnętrznych wątków PPP (1–31).
- **ppp_invalid_packet_handler:** Wskaźnik funkcji do programu obsługi aplikacji dla wszystkich pakietów innych niż PPP. Protokół NETX PPP zazwyczaj wywołuje tę procedurę podczas inicjowania. W tym miejscu aplikacja może reagować na polecenia modemu lub w przypadku programu Windows XP aplikacja NETX PPP może zainicjować protokół PPP, odpowiadając przy użyciu "SERWERA KLIENTA" na początkowy "KLIENT" wysyłany przez Windows XP.
- **ppp_byte_send:** wskaźnik funkcji do procedury danych wyjściowych bajtów seryjnych aplikacji.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik funkcji PPP, IP lub bajtów wyjściowych.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

Usuwanie wystąpienia PROTOKOŁU PPP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Uzyskiwanie adresu IP DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera adres IP DNS dostarczony przez elementu równorzędnego. Jeśli element równorzędny nie podał żadnego adresu IP, zwracany jest adres IP 0.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **dns_address_ptr:** miejsce docelowe dla adresu IP DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne uzyskiwanie adresu PPP.
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) PPP nie zakończyło negocjacji z elementu równorzędnego.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Uzyskiwanie pomocniczego adresu IP serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera pomocniczy adres IP DNS dostarczony przez elementu równorzędnego w uściśliwce IPCP. Jeśli element równorzędny nie podał żadnego adresu IP, zwracany jest adres IP 0.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **dns_address_ptr:** miejsce docelowe dla pomocniczego adresu serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne uzyskiwanie adresu DNS.
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) PPP nie zakończyło negocjacji z elementu równorzędnego.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Ustawianie podstawowego adresu IP serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP serwera DNS. Jeśli komunikacja równorzędna wysyła żądanie opcji serwera DNS w stanie IPCP, ten host udostępni informacje.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **dns_address:** adres serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zestaw pomyślnych adresów DNS.
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) PPP nie zakończyło negocjacji z elementu równorzędnego.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Ustawianie pomocniczego adresu IP serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia pomocniczy adres IP serwera DNS. Jeśli komunikacja równorzędna wysyła żądanie opcji pomocniczego serwera DNS w stanie IPCP, ten host udostępni informacje.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **dns_address:** pomocniczy adres serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zestaw pomyślnych adresów DNS. 
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) PPP nie zakończyło negocjacji z elementu równorzędnego.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Uzyskiwanie indeksu interfejsu IP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera indeks interfejsu IP skojarzony z tym wystąpieniem PROTOKOŁU PPP. Jest to przydatne tylko wtedy, gdy wystąpienie protokołu PPP nie jest podstawowym interfejsem wystąpienia adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **index_ptr:** miejsce docelowe indeksu interfejsu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne uzyskiwanie indeksu PROTOKOŁU PPP.
- **NX_IN_PROGRESS:**(0x37) Ppp nie zakończyło inicjowania.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

Przypisywanie adresów IP dla protokołu IPCP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>Opis

Ta usługa konfiguruje lokalne i równorzędne adresy IP do użycia w protokole IPCP (Internet Protocol Control Protocol). Aplikacja PPP powinna wywoływać tę usługę w wystąpieniu PROTOKOŁU PPP z prawidłowymi adresami IP dla siebie i drugiego elementu równorzędnego.  Jeśli żadne prawidłowe adresy nie są zarejestrowane w wystąpieniu protokołu PPP, musi on polegać na równorzędnej protokołu PPP w celu zdefiniowania jego adresu IP.


### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **local_ip_address:** lokalny adres IP.
- **peer_ip_address:** adres IP elementu równorzędnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne przypisanie adresu PROTOKOŁU PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Powiadamianie aplikacji przy linku w dół

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje wywołanie zwrotne powiadomień w dół połączenia aplikacji z określonym wystąpieniem protokołu PPP. W przypadku wartości innych niż NULL funkcja wywołania zwrotnego łączenia w dół aplikacji jest wywoływana za każdym razem, gdy połączenie nie działa.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **link_down_callback:** wskaźnik funkcji powiadomienia link w dół aplikacji. W przypadku wartości NULL powiadomienie o linku jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślna rejestracja wywołania zwrotnego powiadomień w linku.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

Powiadamianie aplikacji o linku

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Opis

Ta usługa rejestruje wywołanie zwrotne powiadomień łączenia aplikacji z określonym wystąpieniem protokołu PPP. W przypadku wartości innych niż NULL funkcja wywołania zwrotnego łączenia aplikacji jest wywoływana za każdym razem, gdy pojawia się link.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **link_up_callback:** wskaźnik funkcji łączenia aplikacji z funkcją powiadomień. W przypadku wartości NULL powiadomienie o linku jest wyłączone.**

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne połączenie rejestracji wywołania zwrotnego powiadomień.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

Powiadamianie aplikacji o otrzymaniu nak uwierzytelniania

### <a name="prototype"></a>Prototype

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Opis

Ta usługa rejestruje wywołanie zwrotne powiadomień nak uwierzytelniania aplikacji przy użyciu określonego wystąpienia protokołu PPP. W przypadku wartości innych niż NULL ta funkcja wywołania zwrotnego jest wywoływana za każdym razem, gdy wystąpienie protokołu PPP odbiera nakłońcowy podczas uwierzytelniania.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **nak_authentication_notify:** Wskaźnik do funkcji wywoływanej, gdy wystąpienie protokołu PPP odbiera nakłoń uwierzytelniania. W przypadku wartości NULL powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślna rejestracja wywołania zwrotnego powiadomień.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

Włączanie uwierzytelniania PAP

### <a name="prototype"></a>Prototype

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>Opis

Ta usługa włącza protokół uwierzytelniania haseł (PAP) dla określonego wystąpienia protokołu PPP. Jeśli określono wskaźnik funkcji ***"verify_login",*** to wystąpienie protokołu PPP wymaga protokołu PAP. W przeciwnym razie PAP odpowiada tylko na wymagania pap elementu równorzędnego określone podczas negocjacji LCP.

Istnieje kilka elementów danych przywołynych poniżej w wymaganych funkcjach wywołania zwrotnego. Oczekuje się, *że nazwa* elementu danych będzie ciągiem zakończonym z wartością NULL i maksymalnym rozmiarem NX_PPP_NAME_SIZE-1. Oczekuje się *również,* że hasło elementu danych będzie ciągiem zakończonym z wartością NULL i maksymalnym rozmiarem NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Ta funkcja musi być wywoływana po *nx_ppp_create* ale przed nx_ip_create *lub* *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **generate_login:** wskaźnik do funkcji aplikacji, która tworzy *nazwę* i *hasło na* celu uwierzytelnianie przez elementu równorzędnego. Należy pamiętać, *że wartości* nazwy *i* hasła muszą zostać skopiowane do podanych miejsc docelowych.
- **verify_login:** wskaźnik do funkcji aplikacji, która weryfikuje *nazwę* *i hasło* dostarczone przez elementu równorzędnego. Ta procedura musi porównać *podaną nazwę i* *hasło*. Jeśli ta procedura NX_SUCCESS, nazwa i hasło są poprawne, a protokół PPP może przejść do następnego kroku. W przeciwnym razie ta procedura zwraca NX_PPP_ERROR i PPP po prostu czeka na inną nazwę i hasło.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne włączenie protokołu PPP PAP.
- **NX_NOT_IMPLEMENTED:**(0x80) Logika PAP została wyłączona za pośrednictwem NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP lub wskaźnik funkcji aplikacji.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

Wysyłanie żądania ping LCP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie ping LCP i ustawia flagę, że urządzenie PPP oczekuje na odpowiedź echa. Usługa zwraca wartość natychmiast po wysłaniu żądania. Nie czeka na odpowiedź. 

Po otrzymaniu pasującej odpowiedzi echa zadanie wątku PPP wyczyści flagę . Urządzenie PPP musi ukończyć część LCP negocjacji PROTOKOŁU PPP.

Ta usługa jest przydatna w przypadku konfiguracji PROTOKOŁU PPP, w przypadku których sondowanie sprzętu pod celu ustalenia stanu łącza może być niemożliwe.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **data**: Wskaźnik do danych do wysłania w żądaniu echa.
- **data_size:** Rozmiar danych do wysłania wait_option czas oczekiwania na wysłanie komunikatu echa LCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Żądanie echa wysłane pomyślnie.
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) Połączenie PROTOKOŁU PPP nie zostało nawiązane.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP lub wskaźnik funkcji aplikacji.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki aplikacji

### <a name="example"></a>Przykład

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  strlen("username ");

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

Wysyłanie nieprzetworzowego ciągu ASCII

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła ciąg ASCII bez protokołu PPP bezpośrednio z interfejsu PPP. Jest on zwykle używany po otrzymaniu przez protokół PPP pakietu bez protokołu PPP, który zawiera informacje o kontrolce modemu.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **string_ptr:** Wskaźnik do ciągu do wysłania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne wysłanie nieprzetworznych ciągów PROTOKOŁU PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP lub wskaźnik ciągu.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

Ponowne uruchamianie przetwarzania PROTOKOŁU PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa ponownie uruchamia przetwarzanie protokołu PPP. Zwykle jest on wywoływany, gdy należy ponownie nawiązać połączenie z wywołania zwrotnego połączenia lub przez komunikat modemu inny niż PPP wskazujący, że komunikacja została utracona.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zainicjowanie pomyślnego ponownego uruchomienia protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

Uruchamianie przetwarzania PROTOKOŁU PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa rozpoczyna przetwarzanie protokołu PPP. Zazwyczaj jest on wywoływany po wywołaniu nx_ppp_stop().

>[!NOTE]
> Protokół PPP automatycznie uruchamia przetwarzanie protokołu PPP, gdy połączenie jest włączone.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zainicjowanie pomyślnego uruchomienia protokołu PPP. 
- **NX_PPP_ALREADY_STARTED:**(0xb9) PPP została już uruchomiona.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

Uzyskiwanie bieżącego stanu protokołu PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>Opis

Ta usługa pobiera bieżący stan określonego wystąpienia protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PROTOKOŁU PPP.
- **status_ptr:** Miejsce docelowe stanu PROTOKOŁU PPP, możliwe są następujące wartości stanu:
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> Stan jest prawidłowy tylko wtedy, gdy interfejs API zwraca NX_SUCCESS. Ponadto jeśli zostaną zwrócone jakiekolwiek *_FAILED stanu, przetwarzanie PROTOKOŁU PPP zostanie skutecznie zatrzymane do momentu ponownego uruchomienia przez aplikację.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne żądanie stanu PROTOKOŁU PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PROTOKOŁU PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="example"></a>Przykład

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

Rozpoczynanie przetwarzania PROTOKOŁU PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje przetwarzanie protokołu PPP. Użytkownik może również wywołuje nx_ppp_start(), aby w razie potrzeby rozpocząć przetwarzanie protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zainicjowano pomyślne rozpoczęcie protokołu PPP. 
- **NX_PPP_ALREADY_STOPPED:**(0xb8) PPP zostało już zatrzymane.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

Odbieranie pakietu PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>Opis

Ta usługa odbiera pakiet PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **packet_ptr:** Wskaźnik do pakietu PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne żądanie stanu PROTOKOŁU PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Ustawianie funkcji wysyłania pakietów PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Opis

Ta usługa ustawia funciton wysyłania pakietów PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr:** Wskaźnik do bloku sterowania PPP.
- **nx_ppp_packet_send:** Procedura wysyłania pakietu PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne żądanie stanu PROTOKOŁU PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```