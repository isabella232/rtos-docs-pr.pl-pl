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
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="ead84-103">Rozdział 3 — Opis usług klienta DNS w usłudze Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="ead84-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="ead84-104">Ten rozdział zawiera opis wszystkich usług DNS usługi Azure RTO NetX (wymienionych poniżej) w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="ead84-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ead84-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ead84-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ead84-106">**nx_dns_authority_zone_start_get**: *Wyszukiwanie początku strefy urzędu skojarzonej z określoną nazwą hosta*</span><span class="sxs-lookup"><span data-stu-id="ead84-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="ead84-107">**nx_dns_cache_initialize**: *zainicjuj pamięć podręczną DNS.*</span><span class="sxs-lookup"><span data-stu-id="ead84-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="ead84-108">**nx_dns_cache_notify_clear**: *Wyczyść funkcję pełnego powiadamiania pamięci podręcznej.*</span><span class="sxs-lookup"><span data-stu-id="ead84-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="ead84-109">**nx_dns_cache_notify_set**: *Ustaw funkcję pełnego powiadamiania pamięci podręcznej.*</span><span class="sxs-lookup"><span data-stu-id="ead84-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="ead84-110">**nx_dns_cname_get**: *wyszukuje nazwę domeny kanonicznej dla aliasu nazwy domeny wejściowej*</span><span class="sxs-lookup"><span data-stu-id="ead84-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="ead84-111">**nx_dns_create**: *Tworzenie wystąpienia klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="ead84-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="ead84-112">**nx_dns_delete**: *usuwanie wystąpienia klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="ead84-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="ead84-113">**nx_dns_domain_name_server_get**: *Wyszukiwanie autorytatywnych serwerów nazw dla strefy domeny wejściowej*</span><span class="sxs-lookup"><span data-stu-id="ead84-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="ead84-114">**nx_dns_domain_mail_exchange_get**: *Wyszukaj wymianę poczty skojarzoną z określoną nazwą hosta.*</span><span class="sxs-lookup"><span data-stu-id="ead84-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="ead84-115">**nx_dns_domain_service_get**: *Wyszukaj usługi skojarzone z określoną nazwą hosta*</span><span class="sxs-lookup"><span data-stu-id="ead84-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="ead84-116">**nx_dns_get_serverlist_size**: *Zwróć rozmiar listy serwerów klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="ead84-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="ead84-117">**nx_dns_info_by_name_get**: *zwrotny adres IP, badanie portu dla wejściowej nazwy hosta*</span><span class="sxs-lookup"><span data-stu-id="ead84-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="ead84-118">**nx_dns_ipv4_address_by_name_get**: *wyszukuje adres IPv4 z określonej nazwy hosta*</span><span class="sxs-lookup"><span data-stu-id="ead84-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="ead84-119">**nx_dns_host_by_address_get**: *Wyszukiwanie nazwy hosta na podstawie określonego adresu IP*</span><span class="sxs-lookup"><span data-stu-id="ead84-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="ead84-120">**nx_dns_host_by_name_get**: *wyszukuje adres IPv4 z określonej nazwy hosta*</span><span class="sxs-lookup"><span data-stu-id="ead84-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="ead84-121">**nx_dns_host_text_get**: *wyszukiwanie danych tekstowych dla nazwy domeny wejściowej*</span><span class="sxs-lookup"><span data-stu-id="ead84-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="ead84-122">**nx_dns_packet_pool_set**: *Ustaw pulę pakietów klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="ead84-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="ead84-123">**nx_dns_server_add**: *Dodaj serwer DNS o określonym adresie do listy klientów*</span><span class="sxs-lookup"><span data-stu-id="ead84-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="ead84-124">**nx_dns_server_get**: *Zwróć serwer DNS na liście klientów*</span><span class="sxs-lookup"><span data-stu-id="ead84-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="ead84-125">**nx_dns_server_remove**: *usuwanie serwera DNS z listy klientów*</span><span class="sxs-lookup"><span data-stu-id="ead84-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="ead84-126">**nx_dns_server_remove_all**: *Usuń wszystkie serwery DNS z listy klientów*</span><span class="sxs-lookup"><span data-stu-id="ead84-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="ead84-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="ead84-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="ead84-128">Wyszukiwanie początku strefy urzędu dla hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="ead84-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-129">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="ead84-130">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-130">Description</span></span>

<span data-ttu-id="ead84-131">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SOA z określoną nazwą domeny w celu uzyskania początku strefy urzędu dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="ead84-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="ead84-132">Klient DNS kopiuje rekordy SOA zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.</span><span class="sxs-lookup"><span data-stu-id="ead84-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="ead84-133">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="ead84-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ead84-134">W NetX klienta DNS typ rekordu SOA NX_DNS_SOA_ENTRY jest zapisywany jako parametry 7 4 bajtów, łącznie 28 bajtów:</span><span class="sxs-lookup"><span data-stu-id="ead84-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="ead84-135">**nx_dns_soa_host_mname_ptr**: wskaźnik do podstawowego źródła danych dla tej strefy</span><span class="sxs-lookup"><span data-stu-id="ead84-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="ead84-136">**nx_dns_soa_host_rname_ptr**: wskaźnik do skrzynki pocztowej odpowiedzialnej za tę strefę</span><span class="sxs-lookup"><span data-stu-id="ead84-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="ead84-137">**nx_dns_soa_serial**: numer wersji strefy</span><span class="sxs-lookup"><span data-stu-id="ead84-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="ead84-138">**nx_dns_soa_refresh**: interwał odświeżania</span><span class="sxs-lookup"><span data-stu-id="ead84-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="ead84-139">**nx_dns_soa_retry**: interwał między ponownymi próbami zapytania SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="ead84-140">**nx_dns_soa_expire**: czas trwania czasu wygaśnięcia SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="ead84-141">**nx_dns_soa_minmum**: minimalne pole czasu wygaśnięcia w komunikatach odpowiedzi DNS nazwy hosta SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="ead84-142">Poniżej przedstawiono magazyn dwóch rekordów SOA.</span><span class="sxs-lookup"><span data-stu-id="ead84-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="ead84-143">Rekordy SOA zawierające dane o stałej długości są wprowadzane Zaczynając od góry buforu.</span><span class="sxs-lookup"><span data-stu-id="ead84-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="ead84-144">Wskaźniki MNAME i RNAME wskazują na dane o zmiennej długości (nazwy hostów), które są przechowywane w dolnej części buforu.</span><span class="sxs-lookup"><span data-stu-id="ead84-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="ead84-145">Dodatkowe rekordy SOA są wprowadzane po pierwszym rekordzie ("dodatkowe rekordy SOA..."), a ich dane o zmiennej długości są przechowywane powyżej danych o zmiennej długości ("dodatkowe dane długości zmiennej SOA"):</span><span class="sxs-lookup"><span data-stu-id="ead84-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Diagram przedstawiający magazyn dwóch rekordów A](media/image2.png)

<span data-ttu-id="ead84-147">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych SOA w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="ead84-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ead84-148">Wraz z liczbą rekordów SOA zwróconych w programie \**record_count* aplikacja może analizować dane z *record_buffer* i wyodrębnić początki ciągów nazw hosta urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ead84-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-149">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-149">Input Parameters</span></span>

- <span data-ttu-id="ead84-150">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-151">**HOST_NAME**: wskaźnik do nazwy hosta w celu uzyskania danych SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="ead84-152">**record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="ead84-153">**buffer_size**: rozmiar buforu do przechowywania danych SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="ead84-154">**record_count**: wskaźnik do liczby pobranych rekordów SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="ead84-155">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-156">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-156">Return Values</span></span>

- <span data-ttu-id="ead84-157">**NX_SUCCESS**: (0X00) pomyślnie uzyskano dane SOA</span><span class="sxs-lookup"><span data-stu-id="ead84-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="ead84-158">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-159">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-160">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-161">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ead84-162">NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-163">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-163">Allowed From</span></span>

<span data-ttu-id="ead84-164">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-165">Example</span></span>
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


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="ead84-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="ead84-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="ead84-167">Inicjowanie pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-168">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="ead84-169">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-169">Description</span></span>

<span data-ttu-id="ead84-170">Ta usługa tworzy i inicjuje pamięć podręczną DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-171">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-171">Input Parameters</span></span>

- <span data-ttu-id="ead84-172">**dns_ptr**: wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="ead84-173">**cache_ptr**: wskaźnik do pamięci podręcznej DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="ead84-174">**cache_size**: rozmiar pamięci podręcznej DNS, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ead84-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-175">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-175">Return Values</span></span>

- <span data-ttu-id="ead84-176">**NX_SUCCESS**: (0X00) pamięć podręczna DNS została pomyślnie zainicjowana</span><span class="sxs-lookup"><span data-stu-id="ead84-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="ead84-177">NX_DNS_ERROR: (0xA0) pamięć podręczna nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="ead84-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="ead84-178">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ead84-179">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="ead84-180">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-181">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-181">Allowed From</span></span>

<span data-ttu-id="ead84-182">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-183">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="ead84-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="ead84-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="ead84-185">Wyczyść funkcję pełnego powiadamiania pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-186">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="ead84-187">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-187">Description</span></span>

<span data-ttu-id="ead84-188">Ta usługa czyści funkcję pełnego powiadamiania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ead84-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-189">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-189">Input Parameters</span></span>

- <span data-ttu-id="ead84-190">**dns_ptr**: wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-191">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-191">Return Values</span></span>

- <span data-ttu-id="ead84-192">**NX_SUCCESS**: (0x00) pomyślnie ustawiono powiadomienie pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="ead84-193">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ead84-194">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-195">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-195">Allowed From</span></span>

<span data-ttu-id="ead84-196">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="ead84-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="ead84-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="ead84-199">Ustaw funkcję pełnego powiadamiania pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="ead84-201">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-201">Description</span></span>

<span data-ttu-id="ead84-202">Ta usługa ustawia funkcję pełnego powiadamiania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ead84-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-203">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-203">Input Parameters</span></span>

- <span data-ttu-id="ead84-204">**dns_ptr**: wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="ead84-205">**cache_full_notify_cb**: funkcja wywołania zwrotnego, która ma być wywoływana po zapełnieniu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ead84-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-206">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-206">Return Values</span></span>

- <span data-ttu-id="ead84-207">**NX_SUCCESS**: (0x00) pomyślnie ustawiono powiadomienie pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="ead84-208">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ead84-209">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-210">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-210">Allowed From</span></span>

<span data-ttu-id="ead84-211">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-212">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="ead84-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="ead84-213">nx_dns_cname_get</span></span>

<span data-ttu-id="ead84-214">Wyszukiwanie nazwy kanonicznej dla nazwy hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="ead84-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-215">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-216">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-216">Description</span></span>

<span data-ttu-id="ead84-217">Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest zdefiniowana w *nx_dns. h*, ta usługa wysyła zapytanie typu CNAME z określoną nazwą domeny w celu uzyskania nazwy domeny kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="ead84-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="ead84-218">Klient DNS kopiuje ciąg CNAME zwrócony w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="ead84-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-219">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-219">Input Parameters</span></span>

- <span data-ttu-id="ead84-220">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-221">**HOST_NAME**: wskaźnik do nazwy hosta, aby uzyskać dane CNAME</span><span class="sxs-lookup"><span data-stu-id="ead84-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="ead84-222">**record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane CNAME</span><span class="sxs-lookup"><span data-stu-id="ead84-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="ead84-223">**buffer_size**: rozmiar buforu do przechowywania danych CNAME</span><span class="sxs-lookup"><span data-stu-id="ead84-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="ead84-224">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-225">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-225">Return Values</span></span>

- <span data-ttu-id="ead84-226">**NX_SUCCESS**: (0X00) pomyślnie uzyskały dane CNAME</span><span class="sxs-lookup"><span data-stu-id="ead84-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="ead84-227">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-228">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-229">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-230">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ead84-231">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="ead84-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-232">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-232">Allowed From</span></span>

<span data-ttu-id="ead84-233">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-234">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-234">Example</span></span>

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

## <a name="nx_dns_create"></a><span data-ttu-id="ead84-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="ead84-235">nx_dns_create</span></span>

<span data-ttu-id="ead84-236">Tworzenie wystąpienia klienta DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-237">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="ead84-238">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-238">Description</span></span>

<span data-ttu-id="ead84-239">Ta usługa tworzy wystąpienie klienta DNS dla utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ead84-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="ead84-240">Aplikacja musi upewnić się, że ładunek pakietu puli pakietów używany przez klienta DNS jest wystarczająco duży dla maksymalnego 512 bajtowego komunikatu DNS oraz nagłówków UDP, IP i Ethernet.</span><span class="sxs-lookup"><span data-stu-id="ead84-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="ead84-241">Jeśli klient DNS tworzy własną pulę pakietów, jest definiowana przez NX_DNS_PACKET_POOL_SIZE i NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="ead84-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="ead84-242">Jeśli aplikacja kliencka DNS preferuje dostarczenie wcześniej utworzonej puli pakietów, ładunek dla klienta DNS IPv4 powinien mieć 512 bajtów dla maksymalnej wartości DNS Plus 20 bajtów dla nagłówka IP, 8 bajtów dla nagłówka UDP i 14 bajtów dla nagłówka Ethernet.</span><span class="sxs-lookup"><span data-stu-id="ead84-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-243">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-243">Input Parameters</span></span>

- <span data-ttu-id="ead84-244">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-245">**ip_ptr**: wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ead84-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="ead84-246">**domain_name**: wskaźnik do nazwy domeny dla wystąpienia DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-247">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-247">Return Values</span></span>

- <span data-ttu-id="ead84-248">**NX_SUCCESS**: (0X00) POMYŚLNE utworzenie DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="ead84-249">**NX_DNS_ERROR**: (0xa0) błąd tworzenia DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="ead84-250">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-251">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-252">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-252">Allowed From</span></span>

<span data-ttu-id="ead84-253">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-254">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="ead84-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="ead84-255">nx_dns_delete</span></span>

<span data-ttu-id="ead84-256">Usuwanie wystąpienia klienta DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-257">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="ead84-258">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-258">Description</span></span>

<span data-ttu-id="ead84-259">Ta usługa usuwa wcześniej utworzone wystąpienie klienta DNS i zwalnia jego zasoby.</span><span class="sxs-lookup"><span data-stu-id="ead84-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="ead84-260">Jeśli **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** jest zdefiniowany i klient DNS ma przypisaną pulę pakietów zdefiniowany przez użytkownika, w celu usunięcia puli pakietów klienta DNS nie jest już potrzebny.</span><span class="sxs-lookup"><span data-stu-id="ead84-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-261">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-261">Input Parameters</span></span>

- <span data-ttu-id="ead84-262">**dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia **klienta** DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-263">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-263">Return Values</span></span>

- <span data-ttu-id="ead84-264">**NX_SUCCESS**: (0X00) pomyślne usunięcie klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="ead84-265">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="ead84-266">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ead84-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-267">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-267">Allowed From</span></span>

<span data-ttu-id="ead84-268">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-269">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="ead84-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="ead84-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="ead84-271">Wyszukiwanie autorytatywnych serwerów nazw dla strefy domeny wejściowej</span><span class="sxs-lookup"><span data-stu-id="ead84-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-272">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-273">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-273">Description</span></span>

<span data-ttu-id="ead84-274">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu NS z określoną nazwą domeny w celu uzyskania serwerów nazw dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="ead84-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="ead84-275">Klient DNS kopiuje rekordy NS zwrócone w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="ead84-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ead84-276">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="ead84-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ead84-277">W NetX DNS Client typ danych NS NX_DNS_NS_ENTRY, jest zapisywany jako parametry 2 4-bajtowe:</span><span class="sxs-lookup"><span data-stu-id="ead84-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="ead84-278">**nx_dns_ns_ipv4_address**: adres IPv4 serwera nazw</span><span class="sxs-lookup"><span data-stu-id="ead84-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="ead84-279">**nx_dns_ns_hostname_ptr**: wskaźnik do nazwy hosta serwera nazw</span><span class="sxs-lookup"><span data-stu-id="ead84-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="ead84-280">Bufor przedstawiony poniżej zawiera cztery NX_DNS_NS_ENTRY rekordy.</span><span class="sxs-lookup"><span data-stu-id="ead84-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="ead84-281">Wskaźnik do ciągu nazwy hosta w każdym punkcie wejścia wskazuje odpowiadający ciąg nazwy hosta w dolnej połowie buforu:</span><span class="sxs-lookup"><span data-stu-id="ead84-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Diagram bufora zawierający cztery rekordy wpisów w liczbie N X D n s.](media/image3.png)

<span data-ttu-id="ead84-283">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych NS w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="ead84-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ead84-284">Wraz z liczbą rekordów NS zwróconych w programie \**record_count* aplikacja może analizować adres IP i nazwę hosta każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ead84-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-285">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-285">Input Parameters</span></span>

- <span data-ttu-id="ead84-286">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-287">**HOST_NAME**: wskaźnik do nazwy hosta, w której mają zostać uzyskane dane NS</span><span class="sxs-lookup"><span data-stu-id="ead84-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="ead84-288">**record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane NS</span><span class="sxs-lookup"><span data-stu-id="ead84-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="ead84-289">**buffer_size**: rozmiar buforu do przechowywania danych NS</span><span class="sxs-lookup"><span data-stu-id="ead84-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="ead84-290">**record_count**: wskaźnik do liczby pobranych rekordów NS</span><span class="sxs-lookup"><span data-stu-id="ead84-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="ead84-291">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-292">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-292">Return Values</span></span>

- <span data-ttu-id="ead84-293">**NX_SUCCESS**: (0X00) pomyślnie uzyskał dane NS</span><span class="sxs-lookup"><span data-stu-id="ead84-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="ead84-294">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-295">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-296">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ead84-297">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-298">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-299">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-299">Allowed From</span></span>

<span data-ttu-id="ead84-300">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-301">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-301">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="ead84-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="ead84-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="ead84-303">Wyszukaj wymianę poczty dla wejściowej nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-304">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="ead84-305">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-305">Description</span></span>

<span data-ttu-id="ead84-306">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu MX z określoną nazwą domeny w celu uzyskania wymiany poczty dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="ead84-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="ead84-307">Klient DNS kopiuje rekordy MX zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.</span><span class="sxs-lookup"><span data-stu-id="ead84-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="ead84-308">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="ead84-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ead84-309">W NetX klienta DNS typ rekordu wymiany poczty NX_DNS_MAIL_EXCHANGE_ENTRY, został zapisany jako cztery parametry, łącznie 12 bajtów:</span><span class="sxs-lookup"><span data-stu-id="ead84-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="ead84-310">**nx_dns_mx_ipv4_address**: adres IPv4 wymiany poczty 4 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="ead84-311">**nx_dns_mx_preference**: preferencja 2 bajtów</span><span class="sxs-lookup"><span data-stu-id="ead84-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="ead84-312">**nx_dns_mx_reserved0**: zarezerwowane 2 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="ead84-313">**nx_dns_mx_hostname_ptr**: wskaźnik do poczty e-mail nazwa hosta 4 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="ead84-314">Poniżej przedstawiono bufor zawierający cztery rekordy MX.</span><span class="sxs-lookup"><span data-stu-id="ead84-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="ead84-315">Każdy rekord zawiera dane o stałej długości z powyższej listy.</span><span class="sxs-lookup"><span data-stu-id="ead84-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="ead84-316">Wskaźnik do nazwy hosta serwera Exchange Server wskazuje odpowiednią nazwę hosta u dołu buforu.</span><span class="sxs-lookup"><span data-stu-id="ead84-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Diagram przedstawiający bufor zawierający cztery X M rekordów.](media/image4.png)

<span data-ttu-id="ead84-318">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych MX w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="ead84-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ead84-319">Dzięki liczbie rekordów MX zwróconych w programie \**record_count* aplikacja może analizować parametry MX, w tym nazwę hosta poczty każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ead84-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-320">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-320">Input Parameters</span></span>

- <span data-ttu-id="ead84-321">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-322">**HOST_NAME**: wskaźnik do nazwy hosta, aby uzyskać dane MX</span><span class="sxs-lookup"><span data-stu-id="ead84-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="ead84-323">**record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane MX</span><span class="sxs-lookup"><span data-stu-id="ead84-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="ead84-324">**buffer_size**: rozmiar buforu do przechowywania danych MX</span><span class="sxs-lookup"><span data-stu-id="ead84-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="ead84-325">**record_count**: wskaźnik do liczby pobranych rekordów MX</span><span class="sxs-lookup"><span data-stu-id="ead84-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="ead84-326">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-327">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-327">Return Values</span></span>

- <span data-ttu-id="ead84-328">**NX_SUCCESS**: (0X00) pomyślnie uzyskał dane MX</span><span class="sxs-lookup"><span data-stu-id="ead84-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="ead84-329">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-330">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-331">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ead84-332">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-333">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-334">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-334">Allowed From</span></span>

<span data-ttu-id="ead84-335">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-336">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-336">Example</span></span>
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


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="ead84-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="ead84-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="ead84-338">Wyszukaj usługi dostarczone przez nazwę hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="ead84-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-339">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-340">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-340">Description</span></span>

<span data-ttu-id="ead84-341">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SRV z określoną nazwą domeny w celu wyszukania usług i numery portów skojarzone z określoną domeną.</span><span class="sxs-lookup"><span data-stu-id="ead84-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="ead84-342">Klient DNS kopiuje rekordy SRV zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.</span><span class="sxs-lookup"><span data-stu-id="ead84-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ead84-343">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="ead84-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ead84-344">W NetX klienta DNS typ rekordu usługi, wpis NX_DNS_SRV_, jest zapisywany jako sześć parametrów, łącznie 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="ead84-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="ead84-345">Dzięki temu dane SRV o zmiennej długości mogą być przechowywane w wydajny sposób pamięci:</span><span class="sxs-lookup"><span data-stu-id="ead84-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="ead84-346">**Adres IPv4 serwera**: nx_dns_srv_ipv4_address 4 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="ead84-347">**Priorytet serwera**: nx_dns_srv_priority 2 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="ead84-348">**Waga serwera**: nx_dns_srv_weight 2 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="ead84-349">**Numer portu usługi**: nx_dns_srv_port_number 2 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="ead84-350">**Zarezerwowane dla 4-bajtowego wyrównania**: nx_dns_srv_reserved0 2 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="ead84-351">**Wskaźnik do nazwy hosta serwera**: \* nx_dns_srv_hostname_ptr 4 bajty</span><span class="sxs-lookup"><span data-stu-id="ead84-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="ead84-352">Cztery rekordy SRV są przechowywane w podanym buforze.</span><span class="sxs-lookup"><span data-stu-id="ead84-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="ead84-353">Każdy rekord NX_DNS_SRV_ENTRY zawiera wskaźnik *nx_dns_srv_hostname_ptr*, który wskazuje odpowiadający ciąg nazwy hosta w dolnej części buforu rekordu:</span><span class="sxs-lookup"><span data-stu-id="ead84-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Diagram czterech rekordów języka R V przechowywanych w podanym buforze.](media/image5.png)

<span data-ttu-id="ead84-355">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych SRV w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="ead84-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ead84-356">Wraz z liczbą rekordów SRV zwróconych w programie \**record_count* aplikacja może analizować parametry SRV, w tym nazwę hosta serwera każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ead84-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-357">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-357">Input Parameters</span></span>

- <span data-ttu-id="ead84-358">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-359">**HOST_NAME**: wskaźnik do nazwy hosta, aby uzyskać dane SRV</span><span class="sxs-lookup"><span data-stu-id="ead84-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="ead84-360">**record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane SRV</span><span class="sxs-lookup"><span data-stu-id="ead84-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="ead84-361">**buffer_size**: rozmiar buforu do przechowywania danych SRV</span><span class="sxs-lookup"><span data-stu-id="ead84-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="ead84-362">**record_count**: wskaźnik do liczby pobranych rekordów SRV</span><span class="sxs-lookup"><span data-stu-id="ead84-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="ead84-363">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-364">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-364">Return Values</span></span>

- <span data-ttu-id="ead84-365">**NX_SUCCESS**: (0X00) pomyślnie uzyskał dane SRV</span><span class="sxs-lookup"><span data-stu-id="ead84-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="ead84-366">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-367">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-368">NX_DNS_PARAM_ERROR: (0xA8) Nieprawidłowy identyfikator DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ead84-369">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-370">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-371">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-371">Allowed From</span></span>

<span data-ttu-id="ead84-372">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-373">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-373">Example</span></span>

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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="ead84-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="ead84-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="ead84-375">Zwróć rozmiar listy serwerów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-376">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="ead84-377">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-377">Description</span></span>

<span data-ttu-id="ead84-378">Ta usługa zwraca liczbę prawidłowych serwerów DNS na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="ead84-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-379">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-379">Input Parameters</span></span>

- <span data-ttu-id="ead84-380">**dns_ptr**: wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="ead84-381">**size**: zwraca liczbę serwerów na liście</span><span class="sxs-lookup"><span data-stu-id="ead84-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-382">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-382">Return Values</span></span>

- <span data-ttu-id="ead84-383">**NX_SUCCESS**: (0x00) pomyślnie zwrócono rozmiar listy serwerów DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="ead84-384">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ead84-385">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-386">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-386">Allowed From</span></span>

<span data-ttu-id="ead84-387">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-388">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="ead84-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="ead84-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="ead84-390">Zwrotny adres IP i port serwera DNS według nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-392">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-392">Description</span></span>

<span data-ttu-id="ead84-393">Ta usługa zwraca adres IP serwera i port (rekord usługi) na podstawie kwerendy wejściowej nazwy hosta według zapytania DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="ead84-394">Jeśli rekord usługi nie zostanie znaleziony, ta procedura zwraca zerowy adres IP w wskaźniku adresu wejściowego, a stan błędu różny od zera zwraca, aby sygnalizować błąd.</span><span class="sxs-lookup"><span data-stu-id="ead84-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-395">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-395">Input Parameters</span></span>

- <span data-ttu-id="ead84-396">**dns_ptr**: wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="ead84-397">**HOST_NAME**: wskaźnik do buforu nazw hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="ead84-398">**host_address_ptr**: wskaźnik do adresu do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="ead84-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="ead84-399">**host_port_ptr**: wskaźnik do portu w celu zwrócenia Wait_option opcji oczekiwania dla odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-400">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-400">Return Values</span></span>

- <span data-ttu-id="ead84-401">**NX_SUCCESS**: (0x00) rekord serwera DNS został pomyślnie zwrócony</span><span class="sxs-lookup"><span data-stu-id="ead84-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="ead84-402">**NX_DNS_NO_SERVER**: (0XA1) nie zarejestrowano serwera DNS z klientem w celu wysłania zapytania na hoście</span><span class="sxs-lookup"><span data-stu-id="ead84-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="ead84-403">**NX_DNS_QUERY_FAILED**: (0xA3) nie można wykonać zapytania DNS; Brak odpowiedzi z dowolnego serwera DNS na liście klientów lub nie jest dostępny żaden rekord usługi dla wejściowej nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="ead84-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="ead84-404">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-405">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-406">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-406">Allowed From</span></span>

<span data-ttu-id="ead84-407">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-408">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="ead84-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="ead84-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="ead84-410">Wyszukaj adres IPv4 dla nazwy hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="ead84-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-411">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-412">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-412">Description</span></span>

<span data-ttu-id="ead84-413">Ta usługa wysyła zapytanie typu A z określoną nazwą hosta, aby uzyskać adresy IP dla wejściowej nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="ead84-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="ead84-414">Klient DNS Kopiuje adres IPv4 z rekordu A zwróconego w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="ead84-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ead84-415">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="ead84-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ead84-416">Wiele adresów IPv4 jest przechowywanych w buforze wyrównanym 4-bajtowym, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="ead84-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Diagram z wieloma adresami I P v 4, które są przechowywane w buforze wyrównanym 4 bajty.](media/image6.png)

<span data-ttu-id="ead84-418">Jeśli podany bufor nie może zawierać wszystkich danych adresów IP, pozostałe rekordy nie są przechowywane w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ead84-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="ead84-419">Dzięki temu aplikacja może pobrać jeden, niektóre lub wszystkie dostępne dane adresu IP w odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="ead84-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="ead84-420">Wraz z liczbą rekordów zwróconych w programie \**record_count* aplikacja może analizować dane adresów IPv4 z *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ead84-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-421">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-421">Input Parameters</span></span>

- <span data-ttu-id="ead84-422">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-423">**host_name_ptr**: wskaźnik do nazwy hosta, aby uzyskać wskaźnik buforu adresów IPv4 do lokalizacji, w której mają zostać wyodrębnione dane IPv4</span><span class="sxs-lookup"><span data-stu-id="ead84-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="ead84-424">**buffer_size**: rozmiar buforu do przechowywania danych IPv4</span><span class="sxs-lookup"><span data-stu-id="ead84-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="ead84-425">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-426">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-426">Return Values</span></span>

- <span data-ttu-id="ead84-427">**NX_SUCCESS**: (0X00) pomyślnie uzyskano dane IPv4</span><span class="sxs-lookup"><span data-stu-id="ead84-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="ead84-428">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-429">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-430">NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowy parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="ead84-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="ead84-431">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ead84-432">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-433">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-433">Allowed From</span></span>

<span data-ttu-id="ead84-434">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-435">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-435">Example</span></span>

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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="ead84-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="ead84-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="ead84-437">Wyszukiwanie nazwy hosta na podstawie adresu IP</span><span class="sxs-lookup"><span data-stu-id="ead84-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-438">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-439">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-439">Description</span></span>

<span data-ttu-id="ead84-440">Ta usługa żąda rozpoznawania nazw podanego adresu IP z co najmniej jednego serwera DNS określonego wcześniej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ead84-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="ead84-441">Jeśli to się powiedzie, nazwa hosta zakończona wartością NULL zostanie zwrócona w ciągu określonym przez *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="ead84-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-442">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-442">Input Parameters</span></span>

- <span data-ttu-id="ead84-443">**dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="ead84-444">**IP_address**: adres IP do rozpoznania w nazwie</span><span class="sxs-lookup"><span data-stu-id="ead84-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="ead84-445">**host_name_ptr**: wskaźnik do obszaru docelowego dla nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="ead84-446">**max_host_name_size**: rozmiar obszaru docelowego dla nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="ead84-447">**WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać w taktach czasomierza odpowiedzi serwera DNS po każdej kwerendzie DNS i ponowieniu zapytania. Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ead84-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="ead84-448">**wartość limitu czasu**: (0X00000001-0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozpoznawanie nazw DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="ead84-449">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer DNS odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="ead84-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-450">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-450">Return Values</span></span>

- <span data-ttu-id="ead84-451">**NX_SUCCESS**: (0X00) pomyślne ROZPOZNAnie DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="ead84-452">**NX_DNS_TIMEOUT**: (0XA2) upłynął limit czasu podczas uzyskiwania obiektu mutex usługi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="ead84-453">**NX_DNS_NO_SERVER**: (0XA1) nie określono adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="ead84-454">**NX_DNS_QUERY_FAILED**: (0xA3) nie otrzymał odpowiedzi na zapytanie</span><span class="sxs-lookup"><span data-stu-id="ead84-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="ead84-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) wartość null — adres wejściowy</span><span class="sxs-lookup"><span data-stu-id="ead84-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="ead84-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0XB2) Indeks wskazuje na nieprawidłowy typ adresu (np. IPv6)</span><span class="sxs-lookup"><span data-stu-id="ead84-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="ead84-457">**NX_DNS_PARAM_ERROR**: (0XA8) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="ead84-458">NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ead84-459">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-460">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-460">Allowed From</span></span>

<span data-ttu-id="ead84-461">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-462">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="ead84-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="ead84-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="ead84-464">Wyszukaj adres IP z nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-465">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-466">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-466">Description</span></span>

<span data-ttu-id="ead84-467">Ta usługa żąda rozpoznawania nazw o podanej nazwie wskazywanej przez *HOST_NAME*, z co najmniej jednego serwera DNS określonego wcześniej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ead84-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="ead84-468">Jeśli to się powiedzie, skojarzony adres IP jest zwracany w miejscu docelowym wskazywanym przez *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="ead84-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-469">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-469">Input Parameters</span></span>

- <span data-ttu-id="ead84-470">**dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="ead84-471">**HOST_NAME**: wskaźnik do nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="ead84-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="ead84-472">**host_address_ptr**: wskaźnik do adresu IP hosta DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="ead84-473">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na rozwiązanie DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="ead84-474">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ead84-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="ead84-475">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozpoznawanie nazw DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="ead84-476">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer DNS odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="ead84-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-477">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-477">Return Values</span></span>

- <span data-ttu-id="ead84-478">**NX_SUCCESS**: (0X00) pomyślne rozpoznanie DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="ead84-479">**NX_DNS_NO_SERVER**: (0XA1) nie określono adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="ead84-480">**NX_DNS_QUERY_FAILED**: (0xA3) nie otrzymał odpowiedzi na zapytanie</span><span class="sxs-lookup"><span data-stu-id="ead84-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="ead84-481">NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="ead84-482">NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ead84-483">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-484">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-484">Allowed From</span></span>

<span data-ttu-id="ead84-485">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-486">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-486">Example</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="ead84-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="ead84-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="ead84-488">Wyszukaj ciąg tekstowy dla nazwy domeny wejściowej</span><span class="sxs-lookup"><span data-stu-id="ead84-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-489">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ead84-490">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-490">Description</span></span>

<span data-ttu-id="ead84-491">Ta usługa wysyła zapytanie typu TXT z określoną nazwą domeny i buforem, aby uzyskać dowolne dane ciągu.</span><span class="sxs-lookup"><span data-stu-id="ead84-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="ead84-492">Klient DNS kopiuje ciąg tekstowy z rekordu TXT w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="ead84-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ead84-493">*Record_buffer* nie musi być wyrównany 4-bajtowo w celu uzyskania danych.</span><span class="sxs-lookup"><span data-stu-id="ead84-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-494">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-494">Input Parameters</span></span>

- <span data-ttu-id="ead84-495">**dns_ptr**: wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ead84-496">**HOST_NAME**: wskaźnik do nazwy hosta do wyszukania</span><span class="sxs-lookup"><span data-stu-id="ead84-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="ead84-497">**record_buffer**: wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane txt</span><span class="sxs-lookup"><span data-stu-id="ead84-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="ead84-498">**buffer_size**: rozmiar buforu do przechowywania danych txt</span><span class="sxs-lookup"><span data-stu-id="ead84-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="ead84-499">**WAIT_OPTION**: Poczekaj na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-500">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-500">Return Values</span></span>

- <span data-ttu-id="ead84-501">**NX_SUCCESS**: (0X00) pomyślnie uzyskano ciąg txt</span><span class="sxs-lookup"><span data-stu-id="ead84-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="ead84-502">**NX_DNS_NO_SERVER**: (0xa1) lista serwerów klienta jest pusta</span><span class="sxs-lookup"><span data-stu-id="ead84-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ead84-503">**NX_DNS_QUERY_FAILED**: (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ead84-504">NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ead84-505">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ead84-506">NX_DNS_PARAM_ERROR: (0xA8) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-507">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-507">Allowed From</span></span>

<span data-ttu-id="ead84-508">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-509">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-509">Example</span></span>

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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="ead84-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="ead84-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="ead84-511">Ustawianie puli pakietów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-512">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="ead84-513">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-513">Description</span></span>

<span data-ttu-id="ead84-514">Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów **klienta** DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="ead84-515">Klient DNS użyje tej puli pakietów do wysyłania zapytań DNS, więc ładunek pakietu nie powinien być mniejszy niż NX_DNS_PACKET_PAYLOAD_UNALIGNED, który obejmuje ramki Ethernet, nagłówki IP i UDP i jest zdefiniowany w *nx_dns. h*.</span><span class="sxs-lookup"><span data-stu-id="ead84-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="ead84-516">Po usunięciu klienta DNS Pula pakietów nie jest usuwana i jest odpowiedzialna za usunięcie puli pakietów, gdy nie jest już potrzebna.</span><span class="sxs-lookup"><span data-stu-id="ead84-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="ead84-517">Ta usługa jest dostępna tylko wtedy, gdy opcja konfiguracji NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest zdefiniowana w *nx_dns. h*</span><span class="sxs-lookup"><span data-stu-id="ead84-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-518">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-518">Input Parameters</span></span>

- <span data-ttu-id="ead84-519">**dns_ptr**: wskaźnik do wcześniej utworzonego wystąpienia **klienta** DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="ead84-520">**pool_ptr**: wskaźnik do wcześniej utworzonej puli pakietów</span><span class="sxs-lookup"><span data-stu-id="ead84-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-521">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-521">Return Values</span></span>

- <span data-ttu-id="ead84-522">**NX_SUCCESS**: (0X00) pomyślne zakończenie.</span><span class="sxs-lookup"><span data-stu-id="ead84-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="ead84-523">**NX_NOT_ENABLED**: nie skonfigurowano klienta (0x14) dla tej opcji</span><span class="sxs-lookup"><span data-stu-id="ead84-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="ead84-524">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub **klienta** DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="ead84-525">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ead84-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-526">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-526">Allowed From</span></span>

<span data-ttu-id="ead84-527">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-528">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-528">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="ead84-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="ead84-529">nx_dns_server_add</span></span>

<span data-ttu-id="ead84-530">Dodaj adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-531">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ead84-532">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-532">Description</span></span>

<span data-ttu-id="ead84-533">Ta usługa dodaje serwer DNS IPv4 do listy serwerów.</span><span class="sxs-lookup"><span data-stu-id="ead84-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-534">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-534">Input Parameters</span></span>

- <span data-ttu-id="ead84-535">**dns_ptr**: wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="ead84-536">**server_address**: adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-537">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-537">Return Values</span></span>

- <span data-ttu-id="ead84-538">Pomyślnie dodano serwer **NX_SUCCESS**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="ead84-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="ead84-539">**NX_DNS_DUPLICATE_ENTRY** lub **NX_NO_MORE_ENTRIES**: (0X17) nie są dozwolone dodatkowe serwery DNS (lista jest pełna)</span><span class="sxs-lookup"><span data-stu-id="ead84-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="ead84-540">**NX_DNS_PARAM_ERROR**: (0XA8) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="ead84-541">NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="ead84-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ead84-542">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ead84-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) dane wejściowe adresu serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="ead84-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-544">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-544">Allowed From</span></span>

<span data-ttu-id="ead84-545">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-546">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="ead84-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="ead84-547">nx_dns_server_get</span></span>

<span data-ttu-id="ead84-548">Zwracanie serwera DNS IPv4 z listy klientów</span><span class="sxs-lookup"><span data-stu-id="ead84-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-549">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="ead84-550">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-550">Description</span></span>

<span data-ttu-id="ead84-551">Ta usługa zwraca adres serwera DNS IPv4 z listy serwerów o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="ead84-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="ead84-552">Należy zauważyć, że indeks jest oparty na zero.</span><span class="sxs-lookup"><span data-stu-id="ead84-552">Note that the index is zero based.</span></span> <span data-ttu-id="ead84-553">Jeśli indeks wejściowy przekracza rozmiar listy klienta DNS, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="ead84-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="ead84-554">Usługa *nx_dns_get_serverlist_size* może zostać wywołana najpierw uzyskać liczbę serwerów DNS na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="ead84-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-555">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-555">Input Parameters</span></span>

- <span data-ttu-id="ead84-556">**dns_ptr**: wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="ead84-557">**indeks**: indeks na liście serwerów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="ead84-558">**dns_server_address**: wskaźnik do adresu IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="ead84-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-559">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-559">Return Values</span></span>

- <span data-ttu-id="ead84-560">**NX_SUCCESS**: (0x00) zwracany serwer zakończony powodzeniem</span><span class="sxs-lookup"><span data-stu-id="ead84-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="ead84-561">**NX_DNS_SERVER_NOT_FOUND**: (0XA9) Indeks wskazuje na puste miejsce</span><span class="sxs-lookup"><span data-stu-id="ead84-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="ead84-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) Indeks wskazuje na adres null</span><span class="sxs-lookup"><span data-stu-id="ead84-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="ead84-563">**NX_DNS_PARAM_ERROR**: (0XA8) indeks przekracza rozmiar listy</span><span class="sxs-lookup"><span data-stu-id="ead84-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="ead84-564">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ead84-565">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-566">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-566">Allowed From</span></span>

<span data-ttu-id="ead84-567">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-568">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="ead84-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="ead84-569">nx_dns_server_remove</span></span>

<span data-ttu-id="ead84-570">Usuwanie serwera DNS IPv4 z listy klientów</span><span class="sxs-lookup"><span data-stu-id="ead84-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-571">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ead84-572">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-572">Description</span></span>

<span data-ttu-id="ead84-573">Ta usługa usuwa serwer DNS IPv4 z listy klientów.</span><span class="sxs-lookup"><span data-stu-id="ead84-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-574">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-574">Input Parameters</span></span>

- <span data-ttu-id="ead84-575">**dns_ptr**: wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="ead84-576">**server_address**: adres IP serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-577">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-577">Return Values</span></span>

- <span data-ttu-id="ead84-578">**NX_SUCCESS**: (0X00) serwer DNS został pomyślnie usunięty</span><span class="sxs-lookup"><span data-stu-id="ead84-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="ead84-579">**NX_DNS_SERVER_NOT_FOUND**: (0XA9) serwer nie znajduje się na liście klientów</span><span class="sxs-lookup"><span data-stu-id="ead84-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="ead84-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) dane wejściowe adresu serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="ead84-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="ead84-581">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ead84-582">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-583">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-583">Allowed From</span></span>

<span data-ttu-id="ead84-584">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-585">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="ead84-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="ead84-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="ead84-587">Usuń wszystkie serwery DNS z listy klientów</span><span class="sxs-lookup"><span data-stu-id="ead84-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="ead84-588">Prototype</span><span class="sxs-lookup"><span data-stu-id="ead84-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="ead84-589">Opis</span><span class="sxs-lookup"><span data-stu-id="ead84-589">Description</span></span>

<span data-ttu-id="ead84-590">Ta usługa usuwa wszystkie serwery DNS z listy klientów.</span><span class="sxs-lookup"><span data-stu-id="ead84-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ead84-591">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="ead84-591">Input Parameters</span></span>

- <span data-ttu-id="ead84-592">**dns_ptr**: wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ead84-593">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ead84-593">Return Values</span></span>

- <span data-ttu-id="ead84-594">**NX_SUCCESS**: (0X00) serwery DNS zostały pomyślnie usunięte</span><span class="sxs-lookup"><span data-stu-id="ead84-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="ead84-595">**NX_DNS_ERROR**: (0XA0) nie można uzyskać obiektu mutex ochrony</span><span class="sxs-lookup"><span data-stu-id="ead84-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="ead84-596">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="ead84-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ead84-597">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="ead84-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ead84-598">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ead84-598">Allowed From</span></span>

<span data-ttu-id="ead84-599">Wątki</span><span class="sxs-lookup"><span data-stu-id="ead84-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ead84-600">Przykład</span><span class="sxs-lookup"><span data-stu-id="ead84-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```