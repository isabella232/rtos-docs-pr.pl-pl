---
title: Rozdział 3 — Opis usług klienta DNS w usłudze Azure RTO NetX
description: Ten rozdział zawiera opis wszystkich usług DNS usługi Azure RTO NetX (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822656"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a>Rozdział 3 — Opis usług klienta DNS w usłudze Azure RTO NetX

Ten rozdział zawiera opis wszystkich usług DNS usługi Azure RTO NetX (wymienionych poniżej) w porządku alfabetycznym.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_dns_authority_zone_start_get**: *Wyszukiwanie początku strefy urzędu skojarzonej z określoną nazwą hosta*
- **nx_dns_cache_initialize**: *zainicjuj pamięć podręczną DNS.*
- **nx_dns_cache_notify_clear**: *Wyczyść funkcję pełnego powiadamiania pamięci podręcznej.*
- **nx_dns_cache_notify_set**: *Ustaw funkcję pełnego powiadamiania pamięci podręcznej.*
- **nx_dns_cname_get**: *wyszukuje nazwę domeny kanonicznej dla aliasu nazwy domeny wejściowej*
- **nx_dns_create**: *Tworzenie wystąpienia klienta DNS*
- **nx_dns_delete**: *usuwanie wystąpienia klienta DNS*
- **nx_dns_domain_name_server_get**: *Wyszukiwanie autorytatywnych serwerów nazw dla strefy domeny wejściowej*
- **nx_dns_domain_mail_exchange_get**: *Wyszukaj wymianę poczty skojarzoną z określoną nazwą hosta.*
- **nx_dns_domain_service_get**: *Wyszukaj usługi skojarzone z określoną nazwą hosta*
- **nx_dns_get_serverlist_size**: *Zwróć rozmiar listy serwerów klienta DNS*
- **nx_dns_info_by_name_get**: *zwrotny adres IP, badanie portu dla wejściowej nazwy hosta*
- **nx_dns_ipv4_address_by_name_get**: *wyszukuje adres IPv4 z określonej nazwy hosta*
- **nx_dns_host_by_address_get**: *Wyszukiwanie nazwy hosta na podstawie określonego adresu IP*
- **nx_dns_host_by_name_get**: *wyszukuje adres IPv4 z określonej nazwy hosta*
- **nx_dns_host_text_get**: *wyszukiwanie danych tekstowych dla nazwy domeny wejściowej*
- **nx_dns_packet_pool_set**: *Ustaw pulę pakietów klienta DNS*
- **nx_dns_server_add**: *Dodaj serwer DNS o określonym adresie do listy klientów*
- **nx_dns_server_get**: *Zwróć serwer DNS na liście klientów*
- **nx_dns_server_remove**: *usuwanie serwera DNS z listy klientów*
- **nx_dns_server_remove_all**: *Usuń wszystkie serwery DNS z listy klientów*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Wyszukiwanie początku strefy urzędu dla hosta wejściowego

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a>Opis

Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SOA z określoną nazwą domeny w celu uzyskania początku strefy urzędu dla nazwy domeny wejściowej. Klient DNS kopiuje rekordy SOA zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci. 
>[!NOTE]
> *Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.

W NetX klienta DNS typ rekordu SOA NX_DNS_SOA_ENTRY jest zapisywany jako parametry 7 4 bajtów, łącznie 28 bajtów:

- **nx_dns_soa_host_mname_ptr**: wskaźnik do podstawowego źródła danych dla tej strefy
- **nx_dns_soa_host_rname_ptr**: wskaźnik do skrzynki pocztowej odpowiedzialnej za tę strefę
- **nx_dns_soa_serial**: numer wersji strefy
- **nx_dns_soa_refresh**: interwał odświeżania
- **nx_dns_soa_retry**: interwał między ponownymi próbami zapytania SOA
- **nx_dns_soa_expire**: czas trwania czasu wygaśnięcia SOA
- **nx_dns_soa_minmum**: minimalne pole czasu wygaśnięcia w komunikatach odpowiedzi DNS nazwy hosta SOA

Poniżej przedstawiono magazyn dwóch rekordów SOA. Rekordy SOA zawierające dane o stałej długości są wprowadzane Zaczynając od góry buforu. Wskaźniki MNAME i RNAME wskazują na dane o zmiennej długości (nazwy hostów), które są przechowywane w dolnej części buforu. Dodatkowe rekordy SOA są wprowadzane po pierwszym rekordzie ("dodatkowe rekordy SOA..."), a ich dane o zmiennej długości są przechowywane powyżej danych o zmiennej długości ("dodatkowe dane długości zmiennej SOA"):

![Diagram przedstawiający magazyn dwóch rekordów A](media/image2.png)

Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych SOA w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.

Wraz z liczbą rekordów SOA zwróconych w programie **record_count* aplikacja może analizować dane z *record_buffer* i wyodrębnić początki ciągów nazw hosta urzędu certyfikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **HOST_NAME**: wskaźnik do nazwy hosta w celu uzyskania danych SOA
- **record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane SOA
- **buffer_size**: rozmiar buforu do przechowywania danych SOA
- **record_count**: wskaźnik do liczby pobranych rekordów SOA
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskano dane SOA
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi
- NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

/* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    
    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

```

```Output
Test SOA:
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```


## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

Inicjowanie pamięci podręcznej DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a>Opis

Ta usługa tworzy i inicjuje pamięć podręczną DNS.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS.
- **cache_ptr**: wskaźnik do pamięci podręcznej DNS.
- **cache_size**: rozmiar pamięci podręcznej DNS, w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pamięć podręczna DNS została pomyślnie zainicjowana
- NX_DNS_ERROR: (0xA0) pamięć podręczna nie ma 4-bajtowego wyrównania.
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Wyczyść funkcję pełnego powiadamiania pamięci podręcznej DNS

### <a name="prototype"></a>Prototype

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a>Opis

Ta usługa czyści funkcję pełnego powiadamiania pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie ustawiono powiadomienie pamięci podręcznej DNS
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik DNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Ustaw funkcję pełnego powiadamiania pamięci podręcznej DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Opis

Ta usługa ustawia funkcję pełnego powiadamiania pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS.
- **cache_full_notify_cb**: funkcja wywołania zwrotnego, która ma być wywoływana po zapełnieniu pamięci podręcznej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie ustawiono powiadomienie pamięci podręcznej DNS
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik DNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Wyszukiwanie nazwy kanonicznej dla nazwy hosta wejściowego

### <a name="prototype"></a>Prototype
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest zdefiniowana w *nx_dns. h*, ta usługa wysyła zapytanie typu CNAME z określoną nazwą domeny w celu uzyskania nazwy domeny kanonicznej. Klient DNS kopiuje ciąg CNAME zwrócony w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **HOST_NAME**: wskaźnik do nazwy hosta, aby uzyskać dane CNAME
- **record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane CNAME
- **buffer_size**: rozmiar buforu do przechowywania danych CNAME
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskały dane CNAME
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a>nx_dns_create

Tworzenie wystąpienia klienta DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta DNS dla utworzonego wcześniej wystąpienia adresu IP.

>[!NOTE]
>Aplikacja musi upewnić się, że ładunek pakietu puli pakietów używany przez klienta DNS jest wystarczająco duży dla maksymalnego 512 bajtowego komunikatu DNS oraz nagłówków UDP, IP i Ethernet. Jeśli klient DNS tworzy własną pulę pakietów, jest definiowana przez NX_DNS_PACKET_POOL_SIZE i NX_DNS_PACKET_PAYLOAD. Jeśli aplikacja kliencka DNS preferuje dostarczenie wcześniej utworzonej puli pakietów, ładunek dla klienta DNS IPv4 powinien mieć 512 bajtów dla maksymalnej wartości DNS Plus 20 bajtów dla nagłówka IP, 8 bajtów dla nagłówka UDP i 14 bajtów dla nagłówka Ethernet.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **ip_ptr**: wskaźnik do wcześniej utworzonego wystąpienia adresu IP.  
- **domain_name**: wskaźnik do nazwy domeny dla wystąpienia DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) POMYŚLNE utworzenie DNS
- **NX_DNS_ERROR**: (0xa0) błąd tworzenia DNS
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a>nx_dns_delete

Usuwanie wystąpienia klienta DNS

### <a name="prototype"></a>Prototype

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta DNS i zwalnia jego zasoby. 
>[!NOTE]
> Jeśli **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** jest zdefiniowany i klient DNS ma przypisaną pulę pakietów zdefiniowany przez użytkownika, w celu usunięcia puli pakietów klienta DNS nie jest już potrzebny.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia **klienta** DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne usunięcie klienta DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub klienta DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Wyszukiwanie autorytatywnych serwerów nazw dla strefy domeny wejściowej

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu NS z określoną nazwą domeny w celu uzyskania serwerów nazw dla nazwy domeny wejściowej. Klient DNS kopiuje rekordy NS zwrócone w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* . 

>[!NOTE]
>*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.

W NetX DNS Client typ danych NS NX_DNS_NS_ENTRY, jest zapisywany jako parametry 2 4-bajtowe:

- **nx_dns_ns_ipv4_address**: adres IPv4 serwera nazw
- **nx_dns_ns_hostname_ptr**: wskaźnik do nazwy hosta serwera nazw

Bufor przedstawiony poniżej zawiera cztery NX_DNS_NS_ENTRY rekordy. Wskaźnik do ciągu nazwy hosta w każdym punkcie wejścia wskazuje odpowiadający ciąg nazwy hosta w dolnej połowie buforu:

![Diagram bufora zawierający cztery rekordy wpisów w liczbie N X D n s.](media/image3.png)

Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych NS w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.

Wraz z liczbą rekordów NS zwróconych w programie **record_count* aplikacja może analizować adres IP i nazwę hosta każdego rekordu w *record_buffer*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **HOST_NAME**: wskaźnik do nazwy hosta, w której mają zostać uzyskane dane NS
- **record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane NS
- **buffer_size**: rozmiar buforu do przechowywania danych NS
- **record_count**: wskaźnik do liczby pobranych rekordów NS
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskał dane NS
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        }
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

Wyszukaj wymianę poczty dla wejściowej nazwy hosta

### <a name="prototype"></a>Prototype
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a>Opis

Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu MX z określoną nazwą domeny w celu uzyskania wymiany poczty dla nazwy domeny wejściowej. Klient DNS kopiuje rekordy MX zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.

>[!NOTE]
>*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.

W NetX klienta DNS typ rekordu wymiany poczty NX_DNS_MAIL_EXCHANGE_ENTRY, został zapisany jako cztery parametry, łącznie 12 bajtów:

- **nx_dns_mx_ipv4_address**: adres IPv4 wymiany poczty 4 bajty
- **nx_dns_mx_preference**: preferencja 2 bajtów
- **nx_dns_mx_reserved0**: zarezerwowane 2 bajty
- **nx_dns_mx_hostname_ptr**: wskaźnik do poczty e-mail nazwa hosta 4 bajty

Poniżej przedstawiono bufor zawierający cztery rekordy MX. Każdy rekord zawiera dane o stałej długości z powyższej listy. Wskaźnik do nazwy hosta serwera Exchange Server wskazuje odpowiednią nazwę hosta u dołu buforu.

![Diagram przedstawiający bufor zawierający cztery X M rekordów.](media/image4.png)

Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych MX w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.

Dzięki liczbie rekordów MX zwróconych w programie **record_count* aplikacja może analizować parametry MX, w tym nazwę hosta poczty każdego rekordu w *record_buffer*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **HOST_NAME**: wskaźnik do nazwy hosta, aby uzyskać dane MX
- **record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane MX
- **buffer_size**: rozmiar buforu do przechowywania danych MX
- **record_count**: wskaźnik do liczby pobranych rekordów MX
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskał dane MX
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```


## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

Wyszukaj usługi dostarczone przez nazwę hosta wejściowego

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SRV z określoną nazwą domeny w celu wyszukania usług i numery portów skojarzone z określoną domeną. Klient DNS kopiuje rekordy SRV zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci. 

>[!NOTE]
>*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.

W NetX klienta DNS typ rekordu usługi, wpis NX_DNS_SRV_, jest zapisywany jako sześć parametrów, łącznie 16 bajtów. Dzięki temu dane SRV o zmiennej długości mogą być przechowywane w wydajny sposób pamięci:

- **Adres IPv4 serwera**: nx_dns_srv_ipv4_address 4 bajty
- **Priorytet serwera**: nx_dns_srv_priority 2 bajty
- **Waga serwera**: nx_dns_srv_weight 2 bajty
- **Numer portu usługi**: nx_dns_srv_port_number 2 bajty
- **Zarezerwowane dla 4-bajtowego wyrównania**: nx_dns_srv_reserved0 2 bajty
- **Wskaźnik do nazwy hosta serwera**: * nx_dns_srv_hostname_ptr 4 bajty

Cztery rekordy SRV są przechowywane w podanym buforze. Każdy rekord NX_DNS_SRV_ENTRY zawiera wskaźnik *nx_dns_srv_hostname_ptr*, który wskazuje odpowiadający ciąg nazwy hosta w dolnej części buforu rekordu:

![Diagram czterech rekordów języka R V przechowywanych w podanym buforze.](media/image5.png)

Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych SRV w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.

Wraz z liczbą rekordów SRV zwróconych w programie **record_count* aplikacja może analizować parametry SRV, w tym nazwę hosta serwera każdego rekordu w *record_buffer*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **HOST_NAME**: wskaźnik do nazwy hosta, aby uzyskać dane SRV
- **record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane SRV
- **buffer_size**: rozmiar buforu do przechowywania danych SRV
- **record_count**: wskaźnik do liczby pobranych rekordów SRV
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskał dane SRV
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

       printf("port number = %d\n", 
               nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
               printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
       printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

       if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
       {
            printf("hostname = %s\n", 
            nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        }
       else
            printf("hostname is not set\n");
    }
}
```

```Output
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

Zwróć rozmiar listy serwerów klienta DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a>Opis

Ta usługa zwraca liczbę prawidłowych serwerów DNS na liście klientów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS  
- **size**: zwraca liczbę serwerów na liście

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie zwrócono rozmiar listy serwerów DNS
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Zwrotny adres IP i port serwera DNS według nazwy hosta

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zwraca adres IP serwera i port (rekord usługi) na podstawie kwerendy wejściowej nazwy hosta według zapytania DNS. Jeśli rekord usługi nie zostanie znaleziony, ta procedura zwraca zerowy adres IP w wskaźniku adresu wejściowego, a stan błędu różny od zera zwraca, aby sygnalizować błąd.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS  
- **HOST_NAME**: wskaźnik do buforu nazw hosta
- **host_address_ptr**: wskaźnik do adresu do zwrócenia
- **host_port_ptr**: wskaźnik do portu w celu zwrócenia Wait_option opcji oczekiwania dla odpowiedzi DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) rekord serwera DNS został pomyślnie zwrócony
- **NX_DNS_NO_SERVER**: (0XA1) nie zarejestrowano serwera DNS z klientem w celu wysłania zapytania na hoście
- **NX_DNS_QUERY_FAILED**: (0xA3) nie można wykonać zapytania DNS; Brak odpowiedzi z dowolnego serwera DNS na liście klientów lub nie jest dostępny żaden rekord usługi dla wejściowej nazwy hosta.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Wyszukaj adres IPv4 dla nazwy hosta wejściowego

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła zapytanie typu A z określoną nazwą hosta, aby uzyskać adresy IP dla wejściowej nazwy hosta. Klient DNS Kopiuje adres IPv4 z rekordu A zwróconego w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* . 

>[!NOTE]
>*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.

Wiele adresów IPv4 jest przechowywanych w buforze wyrównanym 4-bajtowym, jak pokazano poniżej:

![Diagram z wieloma adresami I P v 4, które są przechowywane w buforze wyrównanym 4 bajty.](media/image6.png)

Jeśli podany bufor nie może zawierać wszystkich danych adresów IP, pozostałe rekordy nie są przechowywane w *record_buffer*. Dzięki temu aplikacja może pobrać jeden, niektóre lub wszystkie dostępne dane adresu IP w odpowiedzi serwera.

Wraz z liczbą rekordów zwróconych w programie **record_count* aplikacja może analizować dane adresów IPv4 z *record_buffer*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **host_name_ptr**: wskaźnik do nazwy hosta, aby uzyskać wskaźnik buforu adresów IPv4 do lokalizacji, w której mają zostać wyodrębnione dane IPv4
- **buffer_size**: rozmiar buforu do przechowywania danych IPv4
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskano dane IPv4
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowy parametr wejściowy.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }
}
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Wyszukiwanie nazwy hosta na podstawie adresu IP

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa żąda rozpoznawania nazw podanego adresu IP z co najmniej jednego serwera DNS określonego wcześniej przez aplikację. Jeśli to się powiedzie, nazwa hosta zakończona wartością NULL zostanie zwrócona w ciągu określonym przez *host_name_ptr*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.
- **IP_address**: adres IP do rozpoznania w nazwie
- **host_name_ptr**: wskaźnik do obszaru docelowego dla nazwy hosta
- **max_host_name_size**: rozmiar obszaru docelowego dla nazwy hosta
- **WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać w taktach czasomierza odpowiedzi serwera DNS po każdej kwerendzie DNS i ponowieniu zapytania. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość limitu czasu**: (0X00000001-0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozpoznawanie nazw DNS.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer DNS odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne ROZPOZNAnie DNS  
- **NX_DNS_TIMEOUT**: (0XA2) upłynął limit czasu podczas uzyskiwania obiektu mutex usługi DNS
- **NX_DNS_NO_SERVER**: (0XA1) nie określono adresu serwera DNS
- **NX_DNS_QUERY_FAILED**: (0xA3) nie otrzymał odpowiedzi na zapytanie
- **NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) wartość null — adres wejściowy
- **NX_DNS_INVALID_ADDRESS_TYPE**: (0XB2) Indeks wskazuje na nieprawidłowy typ adresu (np. IPv6)
- **NX_DNS_PARAM_ERROR**: (0XA8) nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Wyszukaj adres IP z nazwy hosta

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa żąda rozpoznawania nazw o podanej nazwie wskazywanej przez *HOST_NAME*, z co najmniej jednego serwera DNS określonego wcześniej przez aplikację. Jeśli to się powiedzie, skojarzony adres IP jest zwracany w miejscu docelowym wskazywanym przez *host_address_ptr*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.
- **HOST_NAME**: wskaźnik do nazwy hosta
- **host_address_ptr**: wskaźnik do adresu IP hosta DNS
- **WAIT_OPTION**: określa, jak długo usługa będzie czekać na rozwiązanie DNS. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozpoznawanie nazw DNS.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer DNS odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne rozpoznanie DNS.
- **NX_DNS_NO_SERVER**: (0XA1) nie określono adresu serwera DNS
- **NX_DNS_QUERY_FAILED**: (0xA3) nie otrzymał odpowiedzi na zapytanie
- NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Wyszukaj ciąg tekstowy dla nazwy domeny wejściowej

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła zapytanie typu TXT z określoną nazwą domeny i buforem, aby uzyskać dowolne dane ciągu.

Klient DNS kopiuje ciąg tekstowy z rekordu TXT w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* . 

>[!NOTE]
>*Record_buffer* nie musi być wyrównany 4-bajtowo w celu uzyskania danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do klienta DNS.  
- **HOST_NAME**: wskaźnik do nazwy hosta do wyszukania
- **record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane txt
- **buffer_size**: rozmiar buforu do przechowywania danych txt
- **WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie uzyskano ciąg txt
- **NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta
- **NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi
- NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Ustawianie puli pakietów klienta DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów **klienta** DNS. Klient DNS użyje tej puli pakietów do wysyłania zapytań DNS, więc ładunek pakietu nie powinien być mniejszy niż NX_DNS_PACKET_PAYLOAD_UNALIGNED, który obejmuje ramki Ethernet, nagłówki IP i UDP i jest zdefiniowany w *nx_dns. h*.
 
>[!NOTE]
>Po usunięciu klienta DNS Pula pakietów nie jest usuwana i jest odpowiedzialna za usunięcie puli pakietów, gdy nie jest już potrzebna.

>[!NOTE]
>Ta usługa jest dostępna tylko wtedy, gdy opcja konfiguracji NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest zdefiniowana w *nx_dns. h*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia **klienta** DNS.
- **pool_ptr**: wskaźnik do wcześniej utworzonej puli pakietów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne zakończenie.
- **NX_NOT_ENABLED**: nie skonfigurowano klienta (0x14) dla tej opcji
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub **klienta** DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Dodaj adres IP serwera DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Opis

Ta usługa dodaje serwer DNS IPv4 do listy serwerów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS.  
- **server_address**: adres IP serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie dodano serwer **NX_SUCCESS**: (0x00)
- **NX_DNS_DUPLICATE_ENTRY** lub **NX_NO_MORE_ENTRIES**: (0X17) nie są dozwolone dodatkowe serwery DNS (lista jest pełna)
- **NX_DNS_PARAM_ERROR**: (0XA8) nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi
- NX_DNS_BAD_ADDRESS_ERROR: (0xA4) dane wejściowe adresu serwera o wartości null

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Zwracanie serwera DNS IPv4 z listy klientów

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a>Opis

Ta usługa zwraca adres serwera DNS IPv4 z listy serwerów o określonym indeksie. Należy zauważyć, że indeks jest oparty na zero. Jeśli indeks wejściowy przekracza rozmiar listy klienta DNS, zwracany jest błąd. Usługa *nx_dns_get_serverlist_size* może zostać wywołana najpierw uzyskać liczbę serwerów DNS na liście klientów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS  
- **indeks**: indeks na liście serwerów klienta DNS
- **dns_server_address**: wskaźnik do adresu IP serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) zwracany serwer zakończony powodzeniem
- **NX_DNS_SERVER_NOT_FOUND**: (0XA9) Indeks wskazuje na puste miejsce
- **NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) Indeks wskazuje na adres null
- **NX_DNS_PARAM_ERROR**: (0XA8) indeks przekracza rozmiar listy
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Usuwanie serwera DNS IPv4 z listy klientów

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Opis

Ta usługa usuwa serwer DNS IPv4 z listy klientów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS.
- **server_address**: adres IP serwera DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) serwer DNS został pomyślnie usunięty
- **NX_DNS_SERVER_NOT_FOUND**: (0XA9) serwer nie znajduje się na liście klientów
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) dane wejściowe adresu serwera o wartości null
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Usuń wszystkie serwery DNS z listy klientów

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie serwery DNS z listy klientów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr**: wskaźnik do bloku kontroli DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) serwery DNS zostały pomyślnie usunięte
- **NX_DNS_ERROR**: (0XA0) nie można uzyskać obiektu mutex ochrony
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```