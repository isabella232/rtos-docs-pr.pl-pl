---
title: Rozdział 3 — Opis usług Azure RTO NetX Point-to-Point Protocol (PPP)
description: Ten rozdział zawiera opis wszystkich usług protokołu PPP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f24d7366d27a8223b069a54ef7b93f6b3e38bf3a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822555"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a>Rozdział 3 — Opis usług Azure RTO NetX Point-to-Point Protocol (PPP)

Ten rozdział zawiera opis wszystkich usług protokołu PPP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_ppp_byte_receive**: *odebranie bajtu z SZEREGowego procedury ISR*
- **nx_ppp_chap_challenge**: *generowanie wyzwania protokołu CHAP*
- **nx_ppp_chap_enable**: *Włączanie uwierzytelniania CHAP*
- **nx_ppp_create**: *Tworzenie wystąpienia protokołu PPP*
- **nx_ppp_delete**: *usuwanie wystąpienia protokołu PPP*
- **nx_ppp_dns_address_get**: *uzyskiwanie adresu IP DNS*
- **nx_ppp_dns_address_set**:*Ustaw adres IP serwera DNS*
- **nx_ppp_secondary_dns_address_get**: *Pobierz adres IP POMOCNICZego serwera DNS*
- **nx_ppp_secondary_dns_address_set**: *Ustaw adres IP serwera Secondary_DNS*
- **nx_ppp_interface_index_get**: *Pobierz indeks interfejsu IP*
- **nx_ppp_ip_address_assign**: *Przypisz adresy IP do protokołu IPCP*
- **nx_ppp_link_down_notify**: *Powiadamiaj aplikację przy połączeniu w dół*
- **nx_ppp_link_up_notify**: *Powiadom aplikację przy połączeniu*
- **nx_ppp_nak_authentication_notify**: *Powiadamiaj aplikację w przypadku ODEBRANia uwierzytelniania nak*
- **nx_ppp_pap_enable**: *Włączanie uwierzytelniania PAP*
- **nx_ppp_ping_request**: *Wyślij żądanie echa LCP*
- **nx_ppp_raw_string_send**: *Wyślij ciąg NIEbędący protokołem PPP*
- **nx_ppp_restart**: *Ponowne uruchamianie przetwarzania PPP*
- **nx_ppp_start**: *Uruchamianie przetwarzania PPP*
- **nx_ppp_status_get**: *Pobierz bieżący stan protokołu PPP*
- **nx_ppp_stop**: *ZAtrzymywanie przetwarzania PPP*
- **nx_ppp_packet_receive**: *odbieranie pakietu PPP*
- **nx_ppp_packet_send_set**: *Ustaw funkcję wysyłania pakietów PPP*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Odbierz bajt od szeregu ISR

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Opis

Ta usługa jest zazwyczaj wywoływana z procedury usługi przerwania sterownika szeregowego aplikacji (ISR) do transferu odebranego bajtu do PPP. Gdy jest wywoływana, ta procedura umieszcza odebrany bajt w buforze bajtów cyklicznych i powiadamia odpowiedni wątek PPP do przetwarzania.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **Byte**: bajt odebrany z urządzenia szeregowego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne odebranie BAJTOWEGO protokołu PPP.
- **NX_PPP_BUFFER_FULL**: bufor szeregowy PPP (0xB1) jest już zapełniony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Wątki, procedury ISR

### <a name="example"></a>Przykład

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

Generuj wyzwanie CHAP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa inicjuje wyzwanie protokołu CHAP po nawiązaniu połączenia PPP i uruchomieniu go. Dzięki temu aplikacja ma możliwość regularnego weryfikowania autentyczności połączenia. Jeśli test nie powiedzie się, łącze PPP zostanie zamknięte.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie zainicjowano żądanie PPP.
- **NX_PPP_FAILURE**: (0XB0) nieprawidłowe wyzwanie protokołu PPP, protokół CHAP został włączony tylko dla odpowiedzi.
- **NX_NOT_IMPLEMENTED**: (0x80) logika protokołu CHAP została wyłączona za pośrednictwem NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

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

Włącz uwierzytelnianie CHAP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>Opis

Ta usługa włącza protokół uwierzytelniania Challenge-Handshake (CHAP) dla określonego wystąpienia protokołu PPP.

Jeśli określono wskaźniki funkcji "***get_challenge_values**_" i "_ * _get_verification_values_* *", protokół CHAP jest wymagany przez to wystąpienie protokołu PPP. W przeciwnym razie protokół CHAP odpowiada tylko na żądania wyzwania elementu równorzędnego.

Poniżej przedstawiono kilka elementów danych, do których odwołuje się wymagana funkcja wywołania zwrotnego. Parametry *tajne*, *Nazwa* i *system* elementów danych mają być ciągiem zakończonym wartością null o maksymalnym rozmiarze NX_PPP_NAME_SIZE-1. Oczekiwanym *rand_valuem* elementu danych będzie ciąg zakończony znakiem null o maksymalnym rozmiarze NX_PPP_VALUE_SIZE-1. *Identyfikator* elementu danych to prosty typ znaku bez znaku.

>[!NOTE]
> Ta funkcja musi być wywoływana po *nx_ppp_create* , ale przed nx_ip_create lub *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **get_challenge_values**: wskaźnik do funkcji aplikacji, aby pobrać wartości używane dla wyzwania. Należy pamiętać, że wartości *rand_value*, *ID* i *Secret* muszą zostać skopiowane do dostarczonych miejsc docelowych.
- **get_responder_values**: wskaźnik do funkcji aplikacji, która pobiera wartości używane do reagowania na wyzwanie. Należy zauważyć, że wartości *system*, *name* i *Secret* muszą zostać skopiowane do dostarczonych miejsc docelowych.
- **get_verification_values**: wskaźnik do funkcji aplikacji pobierającej wartości używane do weryfikowania odpowiedzi na wezwanie. Należy zauważyć, że wartości *system*,*name* i *Secret* muszą zostać skopiowane do dostarczonych miejsc docelowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne włączenie protokołu CHAP PPP
- **NX_NOT_IMPLEMENTED**: (0x80) logika protokołu CHAP została wyłączona za pośrednictwem NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji wywołania zwrotnego. Należy pamiętać, że jeśli *get_challenge_values* jest określony, należy również podać funkcję *get_verification_values* .
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa tworzy wystąpienie protokołu PPP dla określonego wystąpienia NetX IP.

>[!NOTE]
> Zwykle dobrym pomysłem jest utworzenie wątku IP NetX o wyższym priorytecie niż priorytet wątku PPP. Aby uzyskać więcej informacji na temat określania priorytetu wątku IP, zapoznaj się z usługą *nx_ip_create* .

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **name**: Nazwa tego wystąpienia protokołu PPP.
- **ip_ptr**: wskaźnik kontroli dla niejeszcze utworzonego wystąpienia adresu IP.
- **stack_memory_ptr**: wskaźnik do początku obszaru stosu wątku PPP.
- **stack_size**: rozmiar w bajtach w stosie wątku.
- **pool_ptr**: wskaźnik do domyślnej puli pakietów.
- **thread_priority**: priorytet wewnętrznych wątków PPP (1-31).
- **ppp_invalid_packet_handler**: wskaźnik funkcji do obsługi aplikacji dla wszystkich pakietów innych niż PPP. NetX PPP zazwyczaj wywołuje tę procedurę podczas inicjacji. Jest to miejsce, w którym aplikacja może odpowiadać na polecenia modemowe lub w przypadku systemu Windows XP aplikacja NetX PPP może inicjować protokół PPP przez odpowiadanie na początkowy "klient", który jest wysyłany przez system Windows XP.
- **ppp_byte_send**: wskaźnik funkcji do procedury wyjściowej bajtów szeregowych aplikacji.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne utworzenie protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik funkcji danych wyjściowych PPP, IP lub Byte.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

Usuwanie wystąpienia protokołu PPP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa poprzednio utworzone wystąpienie protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne usunięcie protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Pobierz adres IP DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera adres IP DNS dostarczony przez element równorzędny. Jeśli adres IP nie został dostarczony przez element równorzędny, zwracany jest adres IP 0.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **dns_address_ptr**: miejsce docelowe dla adresu IP DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne pobieranie adresu PPP.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

### <a name="example"></a>Przykład

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Pobierz adres IP pomocniczego serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera pomocniczy adres IP serwera DNS dostarczony przez element równorzędny w uzgadnianiu IPCP. Jeśli adres IP nie został dostarczony przez element równorzędny, zwracany jest adres IP 0.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **dns_address_ptr**: miejsce docelowe dla adresu pomocniczego serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne uzyskanie adresu DNS.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

### <a name="example"></a>Przykład

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Ustaw adres IP podstawowego serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP serwera DNS. Jeśli element równorzędny wyśle żądanie opcji serwera DNS w stanie IPCP, ten host dostarczy informacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **dns_address**: adres serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślny zbiór adresów DNS.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Ustaw adres IP pomocniczego serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP pomocniczego serwera DNS. Jeśli element równorzędny wyśle żądanie dodatkowej opcji serwera DNS w stanie IPCP, ten host dostarczy informacje.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **dns_address**: pomocniczy adres serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślny zbiór adresów DNS. 
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Pobierz indeks interfejsu IP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera indeks interfejsu IP skojarzony z tym wystąpieniem protokołu PPP. Jest to przydatne tylko wtedy, gdy wystąpienie protokołu PPP nie jest podstawowym interfejsem wystąpienia IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **index_ptr**: miejsce docelowe dla indeksu interfejsu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne pobieranie indeksu PPP.
- **NX_IN_PROGRESS**: (0X37) Protokół PPP nie ukończył inicjacji.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

### <a name="example"></a>Przykład

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

Przypisywanie adresów IP do protokołu IPCP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>Opis

Ta usługa konfiguruje lokalne i równorzędne adresy IP do użycia w protokole protokołu IPCP (Internet Protocol Control Protocol). Aplikacja PPP powinna wywołać tę usługę w wystąpieniu protokołu PPP z prawidłowymi adresami IP dla siebie i innych elementów równorzędnych.  Jeśli w wystąpieniu PPP nie zarejestrowano prawidłowych adresów, musi on polegać na równorzędnym protokole PPP do określenia jego adresu IP.


### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **local_ip_address**: lokalny adres IP.
- **peer_ip_address**: adres IP elementu równorzędnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne przypisanie adresu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Powiadamiaj aplikację o linku w dół

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje wywołanie zwrotne powiadomienia o podłączeniu aplikacji z określonym wystąpieniem PPP. Jeśli wartość nie jest równa NULL, funkcja wywołania zwrotnego łącza aplikacji jest wywoływana za każdym razem, gdy link zostanie wyłączony.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **link_down_callback**: wskaźnik funkcji powiadomień dla aplikacji. Jeśli wartość jest równa NULL, powiadomienie o linku w dół jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne łącze rejestracji wywołania zwrotnego powiadomienia.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

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

Powiadamiaj aplikację przy połączeniu

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Opis

Ta usługa rejestruje połączenie zwrotne powiadomienia aplikacji z określonym wystąpieniem PPP. Jeśli wartość jest inna niż NULL, funkcja wywołania zwrotnego linku aplikacji jest wywoływana za każdym razem, gdy zostanie wyświetlony link.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **link_up_callback**: wskaźnik funkcji powiadomień dla aplikacji. Jeśli wartość jest równa NULL, powiadomienie o linku jest wyłączone. * *

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne łączenie rejestracji wywołania zwrotnego powiadomień.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

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

Powiadamiaj aplikację o otrzymaniu NAK uwierzytelniania

### <a name="prototype"></a>Prototype

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Opis

Ta usługa rejestruje wywołanie zwrotne powiadomienia nak uwierzytelniania aplikacji z określonym wystąpieniem PPP. Jeśli wartość jest inna niż NULL, ta funkcja wywołania zwrotnego jest wywoływana za każdym razem, gdy wystąpienie protokołu PPP odbiera NAK podczas authentiaction.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **nak_authentication_notify**: wskaźnik do funkcji wywoływana, gdy wystąpienie protokołu PPP odbiera nak uwierzytelniania. Jeśli wartość jest równa NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślna Rejestracja wywołania zwrotnego powiadomienia.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

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

Włącz uwierzytelnianie PAP

### <a name="prototype"></a>Prototype

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>Opis

Ta usługa włącza protokół uwierzytelniania hasła (PAP) dla określonego wystąpienia protokołu PPP. Jeśli jest określony wskaźnik funkcji "***verify_login***", protokół PAP jest wymagany przez to wystąpienie protokołu PPP. W przeciwnym razie protokół PAP odpowiada wymaganiom protokołu PAP elementu równorzędnego określonym podczas negocjacji protokołu LCP.

Poniżej przedstawiono kilka elementów danych, do których odwołuje się wymagana funkcja wywołania zwrotnego. Oczekiwano, że *Nazwa* elementu danych ma być ciągiem ZAKOŃCZONYM wartością null o maksymalnym rozmiarze NX_PPP_NAME_SIZE-1. Oczekiwane jest również, że *hasło* elementu danych będzie ciągiem ZAKOŃCZONYM wartością null o maksymalnym rozmiarze NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Ta funkcja musi być wywoływana po *nx_ppp_create* , ale przed *nx_ip_create* lub *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **generate_login**: wskaźnik do funkcji aplikacji, która tworzy *nazwę* i *hasło* na potrzeby uwierzytelniania przez element równorzędny. Należy pamiętać, że wartości *nazwy* i *hasła* muszą być skopiowane do dostarczonych miejsc docelowych.
- **verify_login**: wskaźnik do funkcji aplikacji, która weryfikuje *nazwę* i *hasło* dostarczone przez element równorzędny. Ta procedura musi porównać podaną *nazwę* i *hasło*. Jeśli ta procedura zwróci NX_SUCCESS, nazwa i hasło są poprawne, a protokół PPP może przejść do następnego kroku. W przeciwnym razie ta procedura zwraca NX_PPP_ERROR i PPP czeka na inną nazwę i hasło.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne włączenie protokołu PPP PAP.
- **NX_NOT_IMPLEMENTED**: (0x80) logika PAP została wyłączona za pośrednictwem NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji aplikacji.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Wysyłanie żądania ping protokołu LCP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie ping protokołu LCP i ustawia flagę, którą urządzenie PPP oczekuje na odpowiedź ECHA. Usługa wraca natychmiast po wysłaniu żądania. Nie czeka na odpowiedź. 

Po otrzymaniu zgodnej odpowiedzi echa zadanie wątku PPP wyczyści flagę. Urządzenie PPP musi zakończyć część LCP negocjacji protokołu PPP.

Ta usługa jest przydatna w przypadku zestawów PPP, w których sondowanie sprzętu pod kątem stanu linku może nie być możliwe.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **dane**: wskaźnik do danych do wysłania w żądaniu ECHA.
- **data_size**: rozmiar danych do wysłania WAIT_OPTION czas oczekiwania na wysłanie komunikatu LCP echo.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie wysłano żądanie echa.
- **NX_PPP_NOT_ESTABLISHED**: nie ustanowiono połączenia PPP (0xB5).
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji aplikacji.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

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

Wyślij nieprzetworzony ciąg ASCII

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła ciąg ASCII bez protokołu PPP bezpośrednio poza interfejsem PPP. Jest zazwyczaj używany po odebraniu przez protokół PPP pakietu, który zawiera informacje o kontrolkach modemu.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **string_ptr**: wskaźnik do ciągu do wysłania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne wysyłanie ciągów nieprzetworzonych PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik ciągu.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

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

Uruchom ponownie przetwarzanie PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa ponownie uruchamia przetwarzanie PPP. Jest on zazwyczaj wywoływany, gdy połączenie musi zostać ponownie nawiązane przy użyciu wywołania zwrotnego linku lub komunikatu z modemem innym niż PPP informującego o utracie komunikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie zainicjowano ponowne uruchomienie protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

Uruchom przetwarzanie PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia przetwarzanie PPP. Jest on zazwyczaj wywoływany po wywołaniu nx_ppp_stop ().

>[!NOTE]
> Protokół PPP automatycznie uruchamia przetwarzanie PPP, gdy łącze jest włączone.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie zainicjowano uruchamianie protokołu PPP. 
- **NX_PPP_ALREADY_STARTED**: (0XB9) Protokół PPP jest już uruchomiony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

Pobierz bieżący stan protokołu PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>Opis

Ta usługa Pobiera bieżący stan określonego wystąpienia protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **STATUS_PTR**: miejsce docelowe dla stanu protokołu PPP, dostępne są następujące wartości stanu:
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
> Stan jest prawidłowy tylko wtedy, gdy interfejs API zwraca NX_SUCCESS. Ponadto, jeśli dowolna z wartości stanu * _FAILED jest zwracana, przetwarzanie PPP jest skutecznie przerywane, dopóki nie zostanie ponownie uruchomione przez aplikację.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne żądanie stanu protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

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

Uruchom przetwarzanie PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa przetwarzanie PPP. Użytkownik może także wywoływać nx_ppp_start (), aby uruchomić przetwarzanie PPP w razie potrzeby.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie zainicjowano uruchamianie protokołu PPP. 
- **NX_PPP_ALREADY_STOPPED**: (0XB8) Protokół PPP został już zatrzymany.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

Odbieranie pakietu protokołu PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>Opis

Ta usługa odbiera pakiet protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **packet_ptr**: wskaźnik do pakietu PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne żądanie stanu protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Ustaw funkcję wysyłania pakietów protokołu PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Opis

Ta usługa ustawia ATANH wysyłania pakietów protokołu PPP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ppp_ptr**: wskaźnik do bloku kontroli PPP.
- **nx_ppp_packet_send**: procedura wysyłania pakietu protokołu PPP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne żądanie stanu protokołu PPP.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```