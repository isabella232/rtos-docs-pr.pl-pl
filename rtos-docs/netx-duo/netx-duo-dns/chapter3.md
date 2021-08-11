---
title: Rozdział 3 — Opis Azure RTOS klienta DNS NetX Duo
description: Ten rozdział zawiera opis wszystkich usług DNS Azure RTOS NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 10368edf3cdf15d32bddbd5bd943681b3ff3dd1aa1a7042d1b9bb2bf0e71699f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791910"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a>Rozdział 3 — Opis Azure RTOS klienta DNS NetX Duo

Ten rozdział zawiera opis wszystkich usług DNS Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_dns_authority_zone_start_get** *Odszukaj początek strefy urzędu skojarzonej z określoną nazwą hosta*

- **nx_dns_cache_initialize** *zainicjować pamięć podręczną DNS.*

- **nx_dns_cache_notify_clear** *wyczyść funkcję powiadamiania o pełnej pamięci podręcznej.*

- **nx_dns_cache_notify_set** *ustaw funkcję powiadamiania o pełnej pamięci podręcznej.*

- **nx_dns_cname_get** *wyszukiwania nazwy domeny kanonicznej dla aliasu nazwy domeny wejściowej*

- **nx_dns_create** *tworzenie wystąpienia klienta DNS*

- **nx_dns_delete** *usuwanie wystąpienia klienta DNS*

- **nx_dns_domain_name_server_get** *Wyszukiwania serwerów nazw autorytatywnych dla strefy domeny wejściowej*

- **nx_dns_domain_mail_exchange_get** *sprawdź, czy wymiana poczty skojarzona z określoną nazwą hosta.*

- **nx_dns_domain_service_get** *Wyszukiwania usług skojarzonych z określoną nazwą hosta*

- **nx_dns_get_serverlist_size** *zwraca rozmiar listy serwerów klientów DNS*

- **nx_dns_info_by_name_get** *zwracany adres IP, wykonywanie zapytań na porcie przy nazwie hosta wejściowego*

- **nx_dns_ipv4_address_by_name_get** *Wyszukiwania adresu IPv4 z określonej nazwy hosta*

- **nxd_dns_ipv6_address_by_name_get** *wyszukiwania adresu IPv6 z określonej nazwy hosta*

- **nx_dns_host_by_address_get** wrapper dla nxd_dns_host_by_address_get do wyszukiwania nazwy hosta z określonego adresu *IP (obsługuje tylko adresy IPv4)*

- **nxd_dns_host_by_address_get** adres IP z nazwy hosta wejściowego (obsługuje adresy *IPv4 i IPv6)*

- **nx_dns_host_by_name_get** wrapper dla nxd_dns_host_by_address_get do wyszukiwania nazwy hosta z określonego adresu *(obsługuje tylko adresy IPv4)*

- **nxd_dns_host_by_name_get** adres IP z nazwy hosta wejściowego *(obsługuje adresy IPv4 i IPv6)*

- **nx_dns_host_text_get** *Wyszukiwania danych tekstowych dla nazwy domeny wejściowej*

- **nx_dns_packet_pool_set** *ustawić pulę pakietów klienta DNS*

- **nx_dns_server_add** *wrapper dla nxd_dns_server_add,* aby dodać serwer DNS pod określonym adresem do listy *klientów (obsługuje tylko protokół IPv4)*

- **nxd_dns_server_add** dodaj serwer DNS o określonym adresie IP do listy Serwer klienta (obsługuje adresy *IPv4 lub IPv6)*

- **nx_dns_server_get** *zwrócić serwer DNS na liście Klient (obsługuje tylko adresy IPv4)*

- **nxd_dns_server_get** *zwrócić serwer DNS na liście Klient (obsługuje adresy IPv4 i IPv6)*

- **nx_dns_server_remove** *Wrapper nxd_dns_server_remove usunąć serwer DNS z listy klientów*

- **nxd_dns_server_remove** usuń serwer DNS określonego adresu IP z listy Klient (obsługuje zarówno *adresy IPv4, jak i IPv6)*

- **nx_dns_server_remove_all** *usunąć wszystkie serwery DNS z listy klientów*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Przeszukaj początek strefy urzędu dla hosta wejściowego

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a>Opis

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES, usługa wysyła zapytanie typu SOA o określonej nazwie domeny, aby uzyskać początek strefy urzędu dla nazwy domeny wejściowej. Klient DNS kopiuje rekordy SOA zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.

> [!NOTE]
> Aby *record_buffer* dane, musi być wyrównana o 4 bajty.

W kliencie DNS NetX Duo typ rekordu SOA NX_DNS_SOA_ENTRY jest zapisywany jako siedem 4-bajtowych parametrów, łącznie 28 bajtów:

- **nx_dns_soa_host_mname_ptr** Wskaźnik do podstawowego źródła danych dla tej strefy.
- **nx_dns_soa_host_rname_ptr** Wskaźnik do skrzynki pocztowej odpowiedzialnej za tę strefę
- **nx_dns_soa_serial** Numer wersji strefy
- **nx_dns_soa_refresh** Interwał odświeżania
- **nx_dns_soa_retry** Interwał między kolejnymi próbami zapytania SOA
- **nx_dns_soa_expire** Czas trwania po wygaśnięciu soa
- **nx_dns_soa_minmum** Pole minimalnego TTL w komunikatach odpowiedzi DNS nazwy hosta SOA

Poniżej przedstawiono magazyn dwóch rekordów SOA. Rekordy SOA zawierające dane o stałej długości są wprowadzane od góry buforu. Wskaźniki MNAME i RNAME wskazują dane o zmiennej długości (nazwy hostów), które są przechowywane w dolnej części buforu. Dodatkowe rekordy SOA są wprowadzane po pierwszym rekordzie ("dodatkowe rekordy SOA..."), a ich dane o zmiennej długości są przechowywane powyżej danych o zmiennej długości ostatniego wpisu ("dodatkowe dane o zmiennej długości SOA"):

![Magazyn dwóch rekordów SOA](media/image4.png)

Jeśli dane *record_buffer* nie mogą przechowywać wszystkich danych SOA w  odpowiedzi serwera, record_buffer przechowuje tyle rekordów, ile zmieści się i zwraca liczbę rekordów w buforze.

Dzięki liczbie rekordów SOA zwróconych w **record_count aplikacja* może analizowanie danych z usługi *record_buffer* i wyodrębniać początek ciągów nazw hostów urzędu strefy.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name** Wskaźnik do nazwy hosta w celu uzyskania danych SOA dla
- **record_buffer** Wskaźnik do lokalizacji, do których mają być wyodrębnione dane SOA
- **buffer_size** Rozmiar buforu do przechowywania danych SOA
- **record_count** Wskaźnik do liczby pobranych rekordów SOA
- **wait_option** Opcja oczekiwania na otrzymanie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane SOA
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klientów jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

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

[Output]
----------------------------------------------------
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
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy i inicjuje pamięć podręczną DNS.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.
- **cache_ptr** Wskaźnik do pamięci podręcznej DNS.
- **cache_size** Rozmiar pamięci podręcznej DNS w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pamięci podręcznej DNS została pomyślnie zainicjowana
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_DNS_CACHE_ERROR (0xB7) Nieprawidłowy wskaźnik pamięci podręcznej.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik DNS. 
- NX_DNS_ERROR (0xA0) Pamięć podręczna nie jest wyrównana do 4 bajtów.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Wyczyść funkcję powiadamiania o pełnej pamięci podręcznej DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyczyści funkcję powiadamiania o pełnej pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pamięć podręczna DNS powiadamiania o pomyślnym skonfigurowaniu
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik DNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Ustawianie funkcji powiadamiania o pełnej pamięci podręcznej DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Opis

Ta usługa ustawia funkcję powiadamiania o pełnej pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.
- **cache_full_notify_cb** Funkcja wywołania zwrotnego, która ma zostać wywołana, gdy pamięć podręczna zostanie zapełniona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) dns cache notify successfully set (Powiadamianie o pomyślnym skonfigurowaniu pamięci podręcznej DNS)
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik DNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Poszukaj nazwy kanonicznej dla wejściowej nazwy hosta

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES w pliku *nxd_dns.h,* ta usługa wysyła zapytanie typu CNAME z określoną nazwą domeny w celu uzyskania nazwy domeny kanonicznej. Klient DNS kopiuje ciąg CNAME zwrócony w odpowiedzi serwera DNS do *lokalizacji record_buffer* pamięci.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name** Wskaźnik do nazwy hosta w celu uzyskania danych CNAME dla
- **record_buffer** Wskaźnik do lokalizacji w celu wyodrębnienia danych CNAME do
- **buffer_size** Rozmiar buforu do przechowywania danych CNAME
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane CNAME
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a>nx_dns_create

Tworzenie wystąpienia klienta DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta DNS dla wcześniej utworzonego wystąpienia adresu IP.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że ładunek pakietu puli pakietów używanej przez klienta DNS jest wystarczająco duży, aby zapewnić maksymalnie 512-bajtowy komunikat DNS oraz nagłówki UDP, IP i Ethernet. Jeśli klient DNS tworzy własną pulę pakietów, jest ona definiowana przez NX_DNS_PACKET_PAYLOAD i NX_DNS_PACKET_POOL_SIZE.

Jeśli aplikacja klienta DNS preferuje podanie wcześniej utworzonej puli pakietów, ładunek klienta DNS IPv4 powinien być 512 bajtów dla maksymalnego serwera DNS i 20 bajtów dla nagłówka IP, 8 bajtów dla nagłówka UDP i 14 bajtów dla nagłówka Ethernet. W przypadku protokołu IPv6 jedyną różnicą jest nagłówek IP 40 bajtów, dlatego pakiet musi obsłużyć nagłówek IPv6 o rozmiarze 40 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.  
- **domain_name** Wskaźnik do nazwy domeny dla wystąpienia DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie systemu DNS
- **NX_DNS_ERROR** (0xA0) DNS create error
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a>nx_dns_delete

Usuwanie wystąpienia klienta DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta DNS i usuwa jego zasoby. 

> [!NOTE]
> Jeśli NX_DNS_CLIENT_USER_CREATE_PACKET_POOL i klientowi DNS przypisano pulę pakietów zdefiniowaną przez użytkownika, usunięcie puli pakietów klienta DNS, jeśli nie jest już potrzebne, należy do aplikacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie klienta DNS.
- NX_PTR_ERROR (0x07) Nieprawidłowy adres IP lub wskaźnik klienta DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Poszukaj autorytatywnych serwerów nazw dla strefy domeny danych wejściowych

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu NS z określoną nazwą domeny w celu uzyskania serwerów nazw dla nazwy domeny wejściowej. Klient DNS kopiuje rekordy NS zwrócone w odpowiedzi serwera DNS do *lokalizacji record_buffer* pamięci.

> [!NOTE]
> Aby *record_buffer* dane, dane muszą być wyrównane o 4 bajty.

W kliencie DNS NetX Duo typ danych NS(NX_DNS_NS_ENTRY) jest zapisywany jako dwa 4-bajtowe parametry:

- **nx_dns_ns_ipv4_address** Adres IPv4 serwera nazw
- **nx_dns_ns_hostname_ptr** Wskaźnik do nazwy hosta serwera nazw

Bufor przedstawiony poniżej zawiera cztery rekordy NX_DNS_NS_ENTRY danych. Wskaźnik do ciągu nazwy hosta w każdym wpisie wskazuje odpowiedni ciąg nazwy hosta w dolnej połowie buforu:

![Zawiera cztery NX_DNS_NS_ENTRY rekordów](media/image5.png)

Jeśli dane *record_buffer* nie mogą przechowywać wszystkich danych NS w odpowiedzi serwera, serwer *record_buffer* przechowuje tyle rekordów, ile zmieści się i zwraca liczbę rekordów w buforze.

Po zwróceniu liczby rekordów NS w tabeli **record_count* aplikacja może rejestrować adres IP i nazwę hosta każdego rekordu w record_buffer *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name** Wskaźnik do nazwy hosta w celu uzyskania danych NS dla
- **record_buffer** Wskaźnik do lokalizacji w celu wyodrębnienia danych NS do
- **buffer_size** Rozmiar buforu do przechowywania danych NS
- **record_count** Wskaźnik do liczby pobranych rekordów NS
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane NS
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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

[Output]
------------------------------------------------------
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

Poszukaj nazw hostów wejściowych w wymianach poczty

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES, usługa wysyła zapytanie typu MX z określoną nazwą domeny w celu uzyskania wymiany poczty dla nazwy domeny wejściowej. Klient DNS kopiuje rekordy MX zwrócone w odpowiedzi serwera DNS do *lokalizacji record_buffer* pamięci. 

> [!NOTE]
> Aby *record_buffer* dane, dane muszą być wyrównane o 4 bajty.

W kliencie DNS NetX Duo typ rekordu wymiany poczty e-mail, NX_DNS_MAIL_EXCHANGE_ENTRY, jest zapisywany jako cztery parametry, łącznie 12 bajtów:

- **nx_dns_mx_ipv4_address** Adres IPv4 wymiany poczty 4 bajty
- **nx_dns_mx_preference** Preferencje 2 bajty
- **nx_dns_mx_reserved0** Zarezerwowane 2 bajty
- **nx_dns_mx_hostname_ptr** Wskaźnik do nazwy hosta serwera poczty exchange 4 bajty

Poniżej przedstawiono bufor zawierający cztery rekordy MX. Każdy rekord zawiera dane o stałej długości z powyższej listy. Wskaźnik do nazwy hosta serwera poczty exchange wskazuje odpowiednią nazwę hosta w dolnej części buforu.

![Bufor zawierający cztery rekordy MX](media/image6.png)

Jeśli dane *wejściowe record_buffer* nie mogą przechowywać wszystkich danych MX  w odpowiedzi serwera, record_buffer przechowuje tyle rekordów, ile zmieści się i zwraca liczbę rekordów w buforze.

Po zwróceniu liczby rekordów MX w rekordzie **record_count* aplikacja może rejestrować parametry MX, w tym nazwę hosta poczty dla każdego rekordu w record_buffer *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name** Wskaźnik do nazwy hosta w celu uzyskania danych MX dla
- **record_buffer** Wskaźnik do lokalizacji, do których mają być wyodrębnione dane MX
- **buffer_size** Rozmiar buforu do przechowywania danych MX
- **record_count** Wskaźnik do liczby pobranych rekordów MX
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane MX
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
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

Poszukaj usług dostarczonych przez nazwę hosta wejściowego

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Opis

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SRV z określoną nazwą domeny w celu wyszukiwania usług i ich numeru portu skojarzonego z określoną domeną. Klient DNS kopiuje rekordy SRV zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci. 

> [!NOTE]
> Aby *record_buffer* dane, dane muszą być wyrównane o 4 bajty.

W kliencie DNS NetX Duo typ rekordu usługi NX_DNS_SRV_ ENTRY jest zapisywany jako sześć parametrów, łącznie 16 bajtów. Dzięki temu dane SRV o zmiennej długości mogą być przechowywane w wydajny sposób w pamięci:

- **Adres IPv4 serwera** nx_dns_srv_ipv4_address 4 bajty
- **Priorytet serwera** nx_dns_srv_priority 2 bajty
- **Waga serwera** nx_dns_srv_weight 2 bajty
- **Numer portu usługi nx_dns_srv_port_number** 2 bajty
- **Zarezerwowane do wyrównania do 4 bajtów** nx_dns_srv_reserved0 2 bajty
- **Wskaźnik do nazwy hosta serwera** *nx_dns_srv_hostname_ptr 4 bajty

Cztery rekordy SRV są przechowywane w dostarczonym buforze. Każdy NX_DNS_SRV_ENTRY zawiera wskaźnik, *nx_dns_srv_hostname_ptr*, który wskazuje odpowiedni ciąg nazwy hosta w dolnej części buforu rekordu:

![Cztery rekordy SRV](media/image7.png)

Jeśli dane *record_buffer* nie mogą przechowywać wszystkich danych SRV w  odpowiedzi serwera, record_buffer przechowuje tyle rekordów, ile zmieści się i zwraca liczbę rekordów w buforze.

Po zwróceniu liczby rekordów SRV w tabeli **record_count* aplikacja może rejestrować parametry SRV, w tym nazwę hosta serwera każdego rekordu w record_buffer *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name** Wskaźnik do nazwy hosta w celu uzyskania danych SRV dla
- **record_buffer** Wskaźnik do lokalizacji w celu wyodrębnienia danych SRV do
- **buffer_size** Rozmiar buforu do przechowywania danych SRV
- **record_count** Wskaźnik do liczby pobranych rekordów SRV
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane SRV
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowy parametr bez wskaźnika.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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

[Output]
----------------------------------------------------
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

Zwracanie rozmiaru listy serwerów klienta DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a>Opis

Ta usługa zwraca liczbę prawidłowych serwerów DNS (zarówno IPv4, jak i IPv6) na liście Klient.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS  
- **rozmiar** Zwraca liczbę serwerów na liście

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwera DNS został pomyślnie zwrócony
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Zwracanie adresu IP i portu serwera DNS według nazwy hosta

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zwraca adres IP serwera i port (rekord usługi) na podstawie nazwy hosta wejściowego przez zapytanie DNS. Jeśli rekord usługi nie zostanie znaleziony, ta procedura zwraca zerowy adres IP we wskaźniku adresu wejściowego, a stan błędu jest niezerowy, aby zasygnalizować błąd.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS  
- **host_name** Wskaźnik do bufora nazw hostów
- **host_address_ptr** Wskaźnik do adresu do zwrócenia
- **host_port_ptr** Wskaźnik do portu do zwrócenia
- **wait_option** Opcja oczekiwania na odpowiedź DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwera DNS został pomyślnie zwrócony
- **NX_DNS_NO_SERVER** (0xA1) Brak serwera DNS zarejestrowanego w kliencie w celu wysyłania zapytania o nazwę hosta
- **NX_DNS_QUERY_FAILED** (0xA3) DNS nie powiodło się; Dla wejściowej nazwy hosta nie jest dostępna żadna odpowiedź z żadnych serwerów DNS na liście klient lub nie jest dostępny żaden rekord usługi.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Poszukaj adresu IPv4 dla nazwy hosta wejściowego

### <a name="prototype"></a>Prototype
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła zapytanie typu A o określonej nazwie hosta, aby uzyskać adresy IP dla nazwy hosta wejściowego. Klient DNS kopiuje adres IPv4 z rekordów A zwróconych w odpowiedzi serwera DNS do *lokalizacji record_buffer* pamięci.

> [!NOTE]
> Aby *record_buffer* dane, dane muszą być wyrównane o 4 bajty.

Wiele adresów IPv4 jest przechowywanych w buforze wyrównany o rozmiarze 4 bajtów, jak pokazano poniżej:

![bufor wyrównany z wieloma adresami o rozmiarze 4 bajtów](media/image8.png)

Jeśli dostarczony bufor nie może przechowywać wszystkich danych adresu IP, pozostałe rekordy A nie są przechowywane w *record_buffer*. Dzięki temu aplikacja może pobrać jeden lub wszystkie dostępne dane adresu IP w odpowiedzi serwera.

Dzięki liczbie rekordów A zwróconych w tabeli **record_count* aplikacja może analizowanie danych adresu IPv4 z record_buffer *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name_ptr** Wskaźnik do nazwy hosta w celu uzyskania adresu IPv4
- **bufor** Wskaźnik do lokalizacji w celu wyodrębnienia danych IPv4 do
- **buffer_size** Rozmiar buforu do przechowywania danych IPv4
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane IPv4
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowy parametr bez wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
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

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a>nxd_dns_ipv6_address_by_name_get

Poszukaj adresu IPv6 dla nazwy hosta wejściowego

### <a name="prototype"></a>Prototype
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła zapytanie typu AAAA z określoną nazwą domeny, aby uzyskać adresy IP dla nazwy domeny wejściowej. Klient DNS kopiuje adres IPv6 z rekordów AAAA zwróconych w odpowiedzi serwera DNS do *lokalizacji record_buffer* pamięci. 

> [!NOTE]
> Aby *record_buffer* dane, dane muszą być wyrównane o 4 bajty.

Poniżej przedstawiono format adresów IPv6 przechowywanych w buforze wyrównanym o rozmiarze 4 bajtów:

![Bufor wyrównany w formacie IPv6 z 4 bajtami](media/image9.png)

Jeśli dane *wejściowe record_buffer* nie mogą przechowywać wszystkich danych AAAA  w odpowiedzi serwera, record_buffer przechowuje tyle rekordów, ile zmieści się i zwraca liczbę rekordów w buforze.

Po zwróceniu liczby rekordów AAAA w tabeli **record_count* aplikacja może rejestrować adresy IPv6 z każdego rekordu w record_buffer *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name_ptr** Wskaźnik do nazwy hosta w celu uzyskania adresu IPv6
- **bufor** Wskaźnik do lokalizacji w celu wyodrębnienia danych IPv6 do
- **buffer_size** Rozmiar buforu do przechowywania danych IPv6
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano dane IPv6
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowy parametr bez wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Wyszukiwania nazwy hosta z adresu IP

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa żąda rozpoznawania nazw podanego adresu IP z co najmniej jednego serwera DNS określonego wcześniej przez aplikację. Jeśli to się powiedzie, nazwa hosta z zakończeniem o wartości NULL jest zwracana w ciągu określonym przez *host_name_ptr*. Jest to funkcja otoki dla usługi *nxd_dns_host_by_address_get* i nie akceptuje adresów IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DNS.
- **ip_address** Adres IP do rozpoznania jako nazwa
- **host_name_ptr** Wskaźnik do obszaru docelowego dla nazwy hosta
- **max_host_name_size** Rozmiar obszaru docelowego dla nazwy hosta
- **wait_option** Definiuje czas oczekiwania usługi w taktach czasomierza na odpowiedź serwera DNS po każdym zapytaniu DNS i ponowieniu zapytania. Opcje oczekiwania są zdefiniowane w następujący sposób:

  wartość limitu czasu (0x00000001 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer DNS nie odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na rozpoznawanie nazw DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne rozpoznawanie nazw DNS  
- **NX_DNS_TIMEOUT** (0xA2) — użyło czasu podczas uzyskiwania obiektu mutex DNS
- **NX_DNS_NO_SERVER** (0xA1) Nie określono adresu serwera DNS
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano odpowiedzi na zapytanie
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) o wartości null
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Indeks wskazuje nieprawidłowy typ adresu (np. IPv6)
- **NX_DNS_PARAM_ERROR** (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

**Przykład**
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a>nxd_dns_host_by_address_get

Look up a host name from the IP address (Poszukaj nazwy hosta na adresie IP)

### <a name="prototype"></a>Prototype
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa żąda rozpoznawania nazw adresu IPv6 lub IPv4 w *argumentie* wejściowym ip_address z co najmniej jednego serwera DNS określonego wcześniej przez aplikację. Jeśli to się powiedzie, nazwa hosta z zakończeniem o wartości NULL jest zwracana w ciągu określonym przez *host_name_ptr*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DNS.
- **ip_address** Adres IP do rozpoznania jako nazwa
- **host_name_ptr** Wskaźnik do obszaru docelowego dla nazwy hosta
- **max_host_name_size** Rozmiar obszaru docelowego dla nazwy hosta
- **wait_option** Definiuje czas oczekiwania usługi w taktach czasomierza na odpowiedź serwera DNS po każdym zapytaniu DNS i ponowieniu zapytania. Opcje oczekiwania są zdefiniowane w następujący sposób:

  wartość limitu czasu (0x00000001 do 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer DNS nie odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na rozpoznawanie nazw DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne rozpoznawanie nazw DNS  
- **NX_DNS_TIMEOUT** (0xA2) — użyło czasu podczas uzyskiwania obiektu mutex DNS
- **NX_DNS_NO_SERVER** (0xA1) Nie określono adresu serwera DNS
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano odpowiedzi na zapytanie
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) o wartości null
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

**Przykład**
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Look up an IP address from the host name (Poszukaj adresu IP na nazwie hosta)

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa żąda rozpoznawania nazw podanej nazwy z co najmniej jednego serwera DNS określonego wcześniej przez aplikację. Jeśli to się powiedzie, skojarzony adres IP jest zwracany w miejscu docelowym wskazywanym przez host_address_ptr. Jest to funkcja otoki dla usługi *nxd_dns_host_by_name_get* i jest ograniczona do danych wejściowych adresu IPv4.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DNS.
- **host_name** Wskaźnik do nazwy hosta
- **host_address_ptr** Zwrócony adres IP serwera DNS
- **wait_option** Określa, jak długo usługa będzie czekać na rozpoznawanie nazw DNS. Opcje oczekiwania są zdefiniowane w następujący sposób:

  wartość limitu czasu (0x00000001 do 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer DNS nie odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na rozpoznawanie nazw DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne rozpoznawanie nazw DNS.
- **NX_DNS_NO_SERVER** (0xA1) Nie określono adresu serwera DNS
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano odpowiedzi na zapytanie
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

**Przykład**
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a>nxd_dns_host_by_name_get

Lookup an IP address from the host name (Odnośnik do adresu IP na przykład nazwy hosta)

### <a name="prototype"></a>Prototype
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a>Opis

Ta usługa żąda rozpoznawania nazw podanego adresu IP z co najmniej jednego serwera DNS określonego wcześniej przez aplikację. Jeśli to się powiedzie, skojarzony adres IP jest zwracany w NXD_ADDRESS wskazywanym przez *host_address_ptr*. Jeśli wywołujący specjalnie ustawia dane wejściowe lookup_type na NX_IP_VERSION_V6, ta usługa wyśle zapytanie dotyczące adresu IPv6 hosta (rekord AAAA). Jeśli wywołujący specjalnie ustawia dane wejściowe lookup_type na NX_IP_VERSION_V4, ta usługa wyśle zapytanie dotyczące adresu IPv4 hosta (rekordU).

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta DNS.
- **host_name** Wskaźnik do nazwy hosta, aby znaleźć adres IP
- **host_address_ptr** Wskaźnik do miejsca docelowego NXD_ADDRESS zawierającego adres IP
- **wait_option** Definiuje czas oczekiwania usługi w taktach czasomierza dla odpowiedzi serwera DNS dla każdego zapytania transmisji i retransmisji. Opcje oczekiwania są zdefiniowane w następujący sposób:

  wartość limitu czasu (0x00000001 do 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer DNS nie odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na rozpoznawanie nazw DNS.

- **lookup_type** Wskazuje typ wyszukiwania (A a a AAAA).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne rozpoznawanie nazw DNS.
- **NX_DNS_NO_SERVER** (0xA1) Nie określono adresu serwera DNS
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano odpowiedzi na zapytanie
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) o wartości null
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

**Przykład**
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

Poniżej przedstawiono inny przykład użycia tej usługi czasowej, tym razem używającej adresów IPv4 i typów rekordów A:
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Poszukaj ciągu tekstowego dla nazwy domeny wejściowej

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła zapytanie typu TXT z określoną nazwą domeny i buforem, aby uzyskać dowolne dane ciągu.

Klient DNS kopiuje ciąg tekstowy w rekordzie TXT w odpowiedzi serwera DNS do *lokalizacji record_buffer* pamięci. 

> [!NOTE]
> Aby record_buffer dane, nie musi być wyrównany o 4 bajty.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do klienta DNS.  
- **host_name** Wskaźnik do nazwy hosta do wyszukania
- **record_buffer** Wskaźnik do lokalizacji, do których mają być wyodrębnione dane TXT
- **buffer_size** Rozmiar buforu do przechowywania danych TXT
- **wait_option** Opcja oczekiwania na odbieranie odpowiedzi serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskany ciąg TXT
- **NX_DNS_NO_SERVER** (0xA1) Lista serwerów klienckich jest pusta
- **NX_DNS_QUERY_FAILED** (0xA3) Nie odebrano prawidłowej odpowiedzi DNS
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

######   
Przykład
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Ustawianie puli pakietów klienta DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów klienta DNS. Klient DNS będzie używać tej puli pakietów do wysyłania zapytań DNS, więc ładunek pakietu nie powinien być mniejszy niż NX_DNS_PACKET_PAYLOAD który zawiera nagłówki Ethernet, IP i UDP i jest zdefiniowany w pliku *nxd_dns.h.* 

> [!NOTE]
> *Klient* DNS jest usuwany, pula pakietów nie jest usuwana wraz z nim i aplikacja jest odpowiedzialna za usunięcie puli pakietów, gdy nie jest już jej potrzebuje.
>
> Ta usługa jest dostępna tylko wtedy, gdy opcja NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest zdefiniowana w *pliku nxd_dns.h*

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta DNS.
- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne ukończenie.
- **NX_NOT_ENABLED** (0x14) Nie skonfigurowano klienta dla tej opcji
- NX_PTR_ERROR (0x07) Nieprawidłowy adres IP lub wskaźnik klienta DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Dodawanie adresu IP serwera DNS

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Opis

Ta usługa dodaje serwer DNS IPv4 do listy serwerów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.  
- **server_address** Adres IP serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Server successfully added (Serwer NX_SUCCESS (0x00) został pomyślnie dodany
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) Koniec z dozwolonymi serwerami DNS (lista jest pełna)
- **NX_DNS_PARAM_ERROR** (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) Dane wejściowe adresu serwera o wartości null

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a>nxd_dns_server_add

Dodawanie serwera DNS do listy klientów

### <a name="prototype"></a>Prototype
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Opis

Ta usługa dodaje adres IP serwera DNS do listy serwerów klientów DNS. Adres server_address być adresem IPv4 lub IPv6. Jeśli klient chce mieć dostęp do tego samego serwera za pomocą adresu IPv4 lub IPv6, powinien dodać oba adresy IP jako wpisy do listy serwerów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.
- **server_address** Wskaźnik do NXD_ADDRESS zawierający adres IP serwera DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Server successfully added (Serwer NX_SUCCESS (0x00) został pomyślnie dodany
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) Brak dozwolonych serwerów DNS (lista jest pełna) 
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- **NX_DNS_PARAM_ERROR** (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) Dane wejściowe adresu serwera o wartości null
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Indeks wskazuje nieprawidłowy typ adresu (np. IPv6)

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Zwracanie serwera DNS IPv4 z listy klientów

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a>Opis

Ta usługa zwraca adres serwera DNS IPv4 z listy serwerów w określonym indeksie. 

> [!NOTE]
> Indeks jest oparty na zeru. Jeśli indeks wejściowy przekracza rozmiar listy klientów DNS, w tym indeksie zostanie znaleziony adres IPv6 lub w określonym indeksie zostanie znaleziony adres null, zostanie zwrócony błąd. Usługa *nx_dns_get_serverlist_size* może zostać wywołana jako pierwsza, uzyskać liczbę serwerów DNS na liście klient.

Ta usługa obsługuje tylko adresy IPv4. Wywołuje ona *usługę nxd_dns_server_get,* która obsługuje zarówno adresy IPv4, jak i IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS  
- **indeks** Indeksowanie na liście serwerów klienta DNS
- **dns_server_address** Wskaźnik do adresu IP serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zwrócony serwer pomyślnie
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Indeks wskazuje puste miejsce
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Indeks wskazuje na adres Null
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Indeks wskazuje nieprawidłowy typ adresu (np. IPv6)
- **NX_DNS_PARAM_ERROR** (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a>nxd_dns_server_get

Zwracanie serwera DNS z listy klientów

### <a name="prototype"></a>Prototype
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a>Opis

Ta usługa zwraca adres IP serwera DNS z listy serwerów w określonym indeksie. 

> [!NOTE]
> Indeks jest oparty na zeru. Jeśli indeks wejściowy przekracza rozmiar listy klientów DNS lub w określonym indeksie zostanie znaleziony adres o wartości null, zwracany jest błąd. Usługa *nx_dns_get_serverlist_size* może zostać wywołana jako pierwsza, aby uzyskać liczbę serwerów DNS na liście serwerów.

Ta usługa obsługuje adresy IPv4 i IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS  
- **indeks** Indeksowanie na liście serwerów klienta DNS
- **dns_server_address** Wskaźnik do adresu IP serwera DNS

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zwrócony adres IP serwera
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Index wskazuje puste miejsce
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index wskazuje na adres serwera o wartości null
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) wskazuje nieprawidłowy typ adresu (np. IPv6)
- **NX_DNS_PARAM_ERROR** (0xA8) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Usuwanie serwera DNS IPv4 z listy klient

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Opis

Ta usługa usuwa serwer DNS IPv4 z listy Klient. Jest to funkcja otoki *dla* nxd_dns_server_remove .

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.
- **server_address** Adres IP serwera DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwer DNS został pomyślnie usunięty
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Nie ma na liście klientów
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Dane wejściowe adresu serwera o wartości null
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a>nxd_dns_server_remove

Usuwanie serwera DNS z listy klient

### <a name="prototype"></a>Prototype
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Opis

Ta usługa usuwa serwer DNS określonego adresu IP z listy Klient. Wejściowy adres IP akceptuje adresy IPv4 i IPv6. Po usunięciu serwera pozostałe serwery przenieś w dół o jeden indeks na liście, aby wypełnić wolne miejsce.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.
- **server_address** Wskaźnik do serwera DNS NXD_ADDRESS danych zawierających adres IP serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwer DNS został pomyślnie usunięty
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Nie ma na liście klientów
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Dane wejściowe adresu serwera o wartości null
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Nie można przetworzyć rekordu z wyłączonym protokółem IPv6
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Indeks wskazuje nieprawidłowy typ adresu (np. IPv6)

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Usuń wszystkie serwery DNS z listy klient

### <a name="prototype"></a>Prototype
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wszystkie serwery DNS z listy Klient.

### <a name="input-parameters"></a>Parametry wejściowe

- **dns_ptr** Wskaźnik do bloku sterowania DNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) serwery DNS zostały pomyślnie usunięte
- **NX_DNS_ERROR** (0xA0) Nie można uzyskać mutex ochrony
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik IP lub DNS.
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```