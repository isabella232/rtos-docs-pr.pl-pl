---
title: Rozdział 3 — Opis usług klienta DNS platformy Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług DNS Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821919"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="9c4b0-103">Rozdział 3 — Opis usług klienta DNS platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9c4b0-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="9c4b0-104">Ten rozdział zawiera opis wszystkich usług DNS usługi Azure RTO NetX (wymienionych poniżej) w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="9c4b0-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="9c4b0-106">**nx_dns_authority_zone_start_get** *sprawdzić początkową strefę autoryzacji skojarzoną z określoną nazwą hosta*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="9c4b0-107">**nx_dns_cache_initialize** *zainicjować pamięci podręcznej DNS.*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="9c4b0-108">**nx_dns_cache_notify_clear** *Wyczyść funkcję pełnego powiadamiania pamięci podręcznej.*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="9c4b0-109">**nx_dns_cache_notify_set** *ustawić funkcji pełnego powiadamiania pamięci podręcznej.*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="9c4b0-110">**nx_dns_cname_get** *wyszukać nazwy domeny w postaci kanonicznej dla aliasu nazwy domeny wejściowej*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="9c4b0-111">**nx_dns_create** *utworzyć wystąpienia klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="9c4b0-112">**nx_dns_delete** *usunąć wystąpienia klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="9c4b0-113">**nx_dns_domain_name_server_get** *wyszukać autorytatywne serwery nazw dla strefy domeny wejściowej*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="9c4b0-114">**nx_dns_domain_mail_exchange_get** *wyszukać wymianę poczty skojarzoną z określoną nazwą hosta.*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="9c4b0-115">**nx_dns_domain_service_get** *wyszukać usługi skojarzone z określoną nazwą hosta*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="9c4b0-116">**nx_dns_get_serverlist_size** *zwrócić rozmiaru listy serwerów klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="9c4b0-117">**nx_dns_info_by_name_get** *zwrotny adres IP, badanie portu dla wejściowej nazwy hosta*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="9c4b0-118">**nx_dns_ipv4_address_by_name_get** *wyszukać adres IPv4 z określonej nazwy hosta*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="9c4b0-119">**nxd_dns_ipv6_address_by_name_get** *wyszukać adres IPv6 z określonej nazwy hosta*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="9c4b0-120"> *funkcja otoki nx_dns_host_by_address_get dla nxd_dns_host_by_address_get do wyszukiwania nazwy hosta na podstawie określonego adresu IP (obsługuje tylko adresy IPv4)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="9c4b0-121">**nxd_dns_host_by_address_get** *wyszukać adres IP na podstawie nazwy hosta wejściowego (obsługuje adresy IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="9c4b0-122"> *funkcja otoki nx_dns_host_by_name_get dla nxd_dns_host_by_address_get do wyszukiwania nazwy hosta na podstawie określonego adresu (obsługuje tylko adresy IPv4)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="9c4b0-123">**nxd_dns_host_by_name_get** *wyszukać adres IP na podstawie nazwy hosta wejściowego (obsługuje adresy IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="9c4b0-124">**nx_dns_host_text_get** *wyszukać dane tekstowe dla nazwy domeny wejściowej*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="9c4b0-125">**nx_dns_packet_pool_set** *ustawić puli pakietów klienta DNS*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="9c4b0-126"> *funkcja otoki nx_dns_server_add dla* NXD_DNS_SERVER_ADD *do dodania serwera DNS o określonym adresie do listy klientów (obsługuje tylko protokół IPv4)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="9c4b0-127">**nxd_dns_server_add** *dodać serwer DNS o określonym adresie IP do listy serwerów klienta (obsługuje adresy IPv4 lub IPv6)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="9c4b0-128">**nx_dns_server_get** *zwrócić serwer DNS na liście klientów (obsługuje tylko adresy IPv4)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="9c4b0-129">**nxd_dns_server_get** *zwrócić serwer DNS na liście klientów (obsługuje adresy IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="9c4b0-130"> *funkcja otoki nx_dns_server_remove dla NXD_DNS_SERVER_REMOVE usuwania serwera DNS z listy klientów*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="9c4b0-131">**nxd_dns_server_remove** *usunąć serwera DNS z podanego adresu IP z listy klientów (obsługuje adresy IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="9c4b0-132">**nx_dns_server_remove_all** *usunąć wszystkie serwery DNS z listy klientów*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="9c4b0-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="9c4b0-134">Wyszukiwanie początku strefy urzędu dla hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="9c4b0-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-135">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="9c4b0-136">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-136">Description</span></span>

<span data-ttu-id="9c4b0-137">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SOA z określoną nazwą domeny w celu uzyskania początku strefy urzędu dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="9c4b0-138">Klient DNS kopiuje rekordy SOA zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="9c4b0-139">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9c4b0-140">W przypadku klienta DNS NetX Duo typ rekordu SOA NX_DNS_SOA_ENTRY jest zapisywany jako parametry 7 4 bajty, łącznie 28 bajtów:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="9c4b0-141">**nx_dns_soa_host_mname_ptr** Wskaźnik do podstawowego źródła danych dla tej strefy.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="9c4b0-142">**nx_dns_soa_host_rname_ptr** Wskaźnik do skrzynki pocztowej odpowiedzialnej za tę strefę</span><span class="sxs-lookup"><span data-stu-id="9c4b0-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="9c4b0-143">**nx_dns_soa_serial** Numer wersji strefy</span><span class="sxs-lookup"><span data-stu-id="9c4b0-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="9c4b0-144">**nx_dns_soa_refresh** Interwał odświeżania</span><span class="sxs-lookup"><span data-stu-id="9c4b0-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="9c4b0-145">**nx_dns_soa_retry** Interwał między ponownymi próbami zapytania SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="9c4b0-146">**nx_dns_soa_expire** Czas trwania wygaśnięcia rekordu SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="9c4b0-147">**nx_dns_soa_minmum** Pole minimalnego czasu wygaśnięcia w komunikatach odpowiedzi DNS nazwy hosta SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="9c4b0-148">Poniżej przedstawiono magazyn dwóch rekordów SOA.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="9c4b0-149">Rekordy SOA zawierające dane o stałej długości są wprowadzane Zaczynając od góry buforu.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="9c4b0-150">Wskaźniki MNAME i RNAME wskazują na dane o zmiennej długości (nazwy hostów), które są przechowywane w dolnej części buforu.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="9c4b0-151">Dodatkowe rekordy SOA są wprowadzane po pierwszym rekordzie ("dodatkowe rekordy SOA..."), a ich dane o zmiennej długości są przechowywane powyżej danych o zmiennej długości ("dodatkowe dane długości zmiennej SOA"):</span><span class="sxs-lookup"><span data-stu-id="9c4b0-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Magazyn dwóch rekordów SOA](media/image4.png)

<span data-ttu-id="9c4b0-153">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych SOA w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9c4b0-154">Wraz z liczbą rekordów SOA zwróconych w programie \**record_count* aplikacja może analizować dane z *record_buffer* i wyodrębnić początki ciągów nazw hosta urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-155">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-155">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-156">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-157">**HOST_NAME** Wskaźnik na nazwę hosta, w którym mają zostać uzyskane dane SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="9c4b0-158">**record_buffer** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="9c4b0-159">**buffer_size** Rozmiar buforu do przechowywania danych SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="9c4b0-160">**record_count** Wskaźnik do liczby pobranych rekordów SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="9c4b0-161">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-162">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-162">Return Values</span></span>

- <span data-ttu-id="9c4b0-163">**NX_SUCCESS** (0X00) pomyślnie uzyskały dane SOA</span><span class="sxs-lookup"><span data-stu-id="9c4b0-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="9c4b0-164">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-165">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-166">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-167">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-168">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-169">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-169">Allowed From</span></span>

<span data-ttu-id="9c4b0-170">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-171">Example</span></span>
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

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="9c4b0-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="9c4b0-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="9c4b0-173">Inicjowanie pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-174">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="9c4b0-175">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-175">Description</span></span>

<span data-ttu-id="9c4b0-176">Ta usługa tworzy i inicjuje pamięć podręczną DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-177">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-177">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-178">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="9c4b0-179">**cache_ptr** Wskaźnik do pamięci podręcznej DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="9c4b0-180">**cache_size** Rozmiar pamięci podręcznej DNS w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-181">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-181">Return Values</span></span>

- <span data-ttu-id="9c4b0-182">**NX_SUCCESS** (0X00) pamięć podręczna DNS została pomyślnie zainicjowana</span><span class="sxs-lookup"><span data-stu-id="9c4b0-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="9c4b0-183">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9c4b0-184">NX_DNS_CACHE_ERROR (0xB7) Nieprawidłowy wskaźnik pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="9c4b0-185">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="9c4b0-186">Pamięć podręczna NX_DNS_ERROR (0xA0) nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-187">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-187">Allowed From</span></span>

<span data-ttu-id="9c4b0-188">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="9c4b0-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="9c4b0-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="9c4b0-191">Wyczyść funkcję pełnego powiadamiania pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="9c4b0-193">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-193">Description</span></span>

<span data-ttu-id="9c4b0-194">Ta usługa czyści funkcję pełnego powiadamiania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-195">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-195">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-196">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-197">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-197">Return Values</span></span>

- <span data-ttu-id="9c4b0-198">**NX_SUCCESS** (0x00) pomyślnie ustawiono powiadomienie pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="9c4b0-199">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="9c4b0-200">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-201">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-201">Allowed From</span></span>

<span data-ttu-id="9c4b0-202">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="9c4b0-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="9c4b0-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="9c4b0-205">Ustaw funkcję pełnego powiadamiania pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-206">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="9c4b0-207">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-207">Description</span></span>

<span data-ttu-id="9c4b0-208">Ta usługa ustawia funkcję pełnego powiadamiania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-209">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-209">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-210">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="9c4b0-211">**cache_full_notify_cb** Funkcja wywołania zwrotnego, która ma być wywoływana po zapełnieniu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-212">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-212">Return Values</span></span>

- <span data-ttu-id="9c4b0-213">**NX_SUCCESS** (0x00) pomyślnie ustawiono powiadomienie pamięci podręcznej DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="9c4b0-214">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="9c4b0-215">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-216">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-216">Allowed From</span></span>

<span data-ttu-id="9c4b0-217">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-218">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="9c4b0-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-219">nx_dns_cname_get</span></span>

<span data-ttu-id="9c4b0-220">Wyszukiwanie nazwy kanonicznej dla nazwy hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="9c4b0-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-222">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-222">Description</span></span>

<span data-ttu-id="9c4b0-223">Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest zdefiniowana w *nxd_dns. h*, ta usługa wysyła zapytanie typu CNAME z określoną nazwą domeny w celu uzyskania nazwy domeny kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="9c4b0-224">Klient DNS kopiuje ciąg CNAME zwrócony w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="9c4b0-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-225">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-225">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-226">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-227">**HOST_NAME** Wskaźnik na nazwę hosta, w którym mają zostać uzyskane dane CNAME</span><span class="sxs-lookup"><span data-stu-id="9c4b0-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="9c4b0-228">**record_buffer** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane CNAME</span><span class="sxs-lookup"><span data-stu-id="9c4b0-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="9c4b0-229">**buffer_size** Rozmiar buforu do przechowywania danych CNAME</span><span class="sxs-lookup"><span data-stu-id="9c4b0-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="9c4b0-230">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-231">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-231">Return Values</span></span>

- <span data-ttu-id="9c4b0-232">**NX_SUCCESS** (0X00) pomyślnie uzyskały dane CNAME</span><span class="sxs-lookup"><span data-stu-id="9c4b0-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="9c4b0-233">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-234">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-235">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-236">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-237">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-238">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-238">Allowed From</span></span>

<span data-ttu-id="9c4b0-239">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-240">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-240">Example</span></span>
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

##  <a name="nx_dns_create"></a><span data-ttu-id="9c4b0-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="9c4b0-241">nx_dns_create</span></span>

<span data-ttu-id="9c4b0-242">Tworzenie wystąpienia klienta DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-243">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="9c4b0-244">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-244">Description</span></span>

<span data-ttu-id="9c4b0-245">Ta usługa tworzy wystąpienie klienta DNS dla utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c4b0-246">Aplikacja musi upewnić się, że ładunek pakietu puli pakietów używany przez klienta DNS jest wystarczająco duży dla maksymalnego 512 bajtowego komunikatu DNS oraz nagłówków UDP, IP i Ethernet.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="9c4b0-247">Jeśli klient DNS tworzy własną pulę pakietów, jest definiowana przez NX_DNS_PACKET_PAYLOAD i NX_DNS_PACKET_POOL_SIZE.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="9c4b0-248">Jeśli aplikacja kliencka DNS preferuje dostarczenie wcześniej utworzonej puli pakietów, ładunek dla klienta DNS IPv4 powinien mieć 512 bajtów dla maksymalnej wartości DNS Plus 20 bajtów dla nagłówka IP, 8 bajtów dla nagłówka UDP i 14 bajtów dla nagłówka Ethernet.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="9c4b0-249">W przypadku protokołu IPv6 jedyną różnicą jest nagłówek IP 40 bajtów. w związku z tym pakiet musi obsłużyć nagłówek IPv6 o 40 bajtów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-250">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-250">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-251">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-252">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="9c4b0-253">**domain_name** Wskaźnik do nazwy domeny dla wystąpienia DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-254">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-254">Return Values</span></span>

- <span data-ttu-id="9c4b0-255">**NX_SUCCESS** (0X00) POMYŚLNE utworzenie DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="9c4b0-256">Błąd tworzenia serwera DNS **NX_DNS_ERROR** (0xa0)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="9c4b0-257">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-258">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-259">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-259">Allowed From</span></span>

<span data-ttu-id="9c4b0-260">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-261">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="9c4b0-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="9c4b0-262">nx_dns_delete</span></span>

<span data-ttu-id="9c4b0-263">Usuwanie wystąpienia klienta DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-264">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="9c4b0-265">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-265">Description</span></span>

<span data-ttu-id="9c4b0-266">Ta usługa usuwa wcześniej utworzone wystąpienie klienta DNS i zwalnia jego zasoby.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-267">Jeśli NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest zdefiniowany i klient DNS ma przypisaną pulę pakietów zdefiniowany przez użytkownika, w celu usunięcia puli pakietów klienta DNS nie jest już potrzebny.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-268">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-268">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-269">**dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-270">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-270">Return Values</span></span>

- <span data-ttu-id="9c4b0-271">**NX_SUCCESS** (0X00) pomyślne usunięcie klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="9c4b0-272">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="9c4b0-273">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-274">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-274">Allowed From</span></span>

<span data-ttu-id="9c4b0-275">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-276">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="9c4b0-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="9c4b0-278">Wyszukiwanie autorytatywnych serwerów nazw dla strefy domeny wejściowej</span><span class="sxs-lookup"><span data-stu-id="9c4b0-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-279">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-280">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-280">Description</span></span>

<span data-ttu-id="9c4b0-281">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu NS z określoną nazwą domeny w celu uzyskania serwerów nazw dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="9c4b0-282">Klient DNS kopiuje rekordy NS zwrócone w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="9c4b0-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="9c4b0-283">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9c4b0-284">W systemie DNS NetX Duo, typ danych NS NX_DNS_NS_ENTRY, jest zapisywany jako parametry 2 4-bajtowe:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="9c4b0-285">**nx_dns_ns_ipv4_address** Adres IPv4 serwera nazw</span><span class="sxs-lookup"><span data-stu-id="9c4b0-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="9c4b0-286">**nx_dns_ns_hostname_ptr** Wskaźnik do nazwy hosta serwera nazw</span><span class="sxs-lookup"><span data-stu-id="9c4b0-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="9c4b0-287">Bufor przedstawiony poniżej zawiera cztery NX_DNS_NS_ENTRY rekordy.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="9c4b0-288">Wskaźnik do ciągu nazwy hosta w każdym punkcie wejścia wskazuje odpowiadający ciąg nazwy hosta w dolnej połowie buforu:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Zawiera cztery NX_DNS_NS_ENTRY rekordy](media/image5.png)

<span data-ttu-id="9c4b0-290">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych NS w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9c4b0-291">Wraz z liczbą rekordów NS zwróconych w programie \**record_count* aplikacja może analizować adres IP i nazwę hosta każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-292">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-292">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-293">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-294">**HOST_NAME** Wskaźnik na nazwę hosta, dla którego mają zostać uzyskane dane NS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="9c4b0-295">**record_buffer** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane NS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="9c4b0-296">**buffer_size** Rozmiar buforu do przechowywania danych NS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="9c4b0-297">**record_count** Wskaźnik do liczby pobranych rekordów NS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="9c4b0-298">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-299">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-299">Return Values</span></span>

- <span data-ttu-id="9c4b0-300">**NX_SUCCESS** (0X00) pomyślnie uzyskał dane NS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="9c4b0-301">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-302">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-303">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="9c4b0-304">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-305">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-306">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-306">Allowed From</span></span>

<span data-ttu-id="9c4b0-307">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-308">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-308">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="9c4b0-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="9c4b0-310">Wyszukaj wymianę poczty dla wejściowej nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-311">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-312">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-312">Description</span></span>

<span data-ttu-id="9c4b0-313">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu MX z określoną nazwą domeny w celu uzyskania wymiany poczty dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="9c4b0-314">Klient DNS kopiuje rekordy MX zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-315">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9c4b0-316">W systemie DNS NetX Duo, typ rekordu wymiany poczty NX_DNS_MAIL_EXCHANGE_ENTRY, jest zapisywany jako cztery parametry, łącznie 12 bajtów:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="9c4b0-317">**nx_dns_mx_ipv4_address** Adres IPv4 wymiany poczty 4 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="9c4b0-318">**nx_dns_mx_preference** Preferencja 2 bajtów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="9c4b0-319">**nx_dns_mx_reserved0** Zarezerwowane 2 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="9c4b0-320">**nx_dns_mx_hostname_ptr** Wskaźnik do poczty programu Exchange Server Nazwa hosta 4 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="9c4b0-321">Poniżej przedstawiono bufor zawierający cztery rekordy MX.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="9c4b0-322">Każdy rekord zawiera dane o stałej długości z powyższej listy.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="9c4b0-323">Wskaźnik do nazwy hosta serwera Exchange Server wskazuje odpowiednią nazwę hosta u dołu buforu.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Bufor zawierający cztery rekordy MX](media/image6.png)

<span data-ttu-id="9c4b0-325">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych MX w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9c4b0-326">Dzięki liczbie rekordów MX zwróconych w programie \**record_count* aplikacja może analizować parametry MX, w tym nazwę hosta poczty każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-327">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-327">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-328">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-329">**HOST_NAME** Wskaźnik na nazwę hosta, w którym mają zostać uzyskane dane MX</span><span class="sxs-lookup"><span data-stu-id="9c4b0-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="9c4b0-330">**record_buffer** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane MX</span><span class="sxs-lookup"><span data-stu-id="9c4b0-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="9c4b0-331">**buffer_size** Rozmiar buforu do przechowywania danych MX</span><span class="sxs-lookup"><span data-stu-id="9c4b0-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="9c4b0-332">**record_count** Wskaźnik do liczby pobranych rekordów MX</span><span class="sxs-lookup"><span data-stu-id="9c4b0-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="9c4b0-333">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-334">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-334">Return Values</span></span>

- <span data-ttu-id="9c4b0-335">**NX_SUCCESS** (0X00) pomyślnie uzyskał dane MX</span><span class="sxs-lookup"><span data-stu-id="9c4b0-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="9c4b0-336">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-337">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-338">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="9c4b0-339">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-340">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-341">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-341">Allowed From</span></span>

<span data-ttu-id="9c4b0-342">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-343">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-343">Example</span></span>
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

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="9c4b0-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="9c4b0-345">Wyszukaj usługi dostarczone przez nazwę hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="9c4b0-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-346">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-347">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-347">Description</span></span>

<span data-ttu-id="9c4b0-348">Jeśli zdefiniowano NX_DNS_ENABLE_EXTENDED_RR_TYPES, ta usługa wysyła zapytanie typu SRV z określoną nazwą domeny w celu wyszukania usług i numery portów skojarzone z określoną domeną.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="9c4b0-349">Klient DNS kopiuje rekordy SRV zwrócone w odpowiedzi serwera DNS do lokalizacji *record_buffer* pamięci.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-350">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9c4b0-351">W przypadku klienta DNS NetX Duo typ rekordu usługi, wpis NX_DNS_SRV_, jest zapisywany jako sześć parametrów, łącznie 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="9c4b0-352">Dzięki temu dane SRV o zmiennej długości mogą być przechowywane w wydajny sposób pamięci:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="9c4b0-353">**Adres IPv4 serwera** nx_dns_srv_ipv4_address 4 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="9c4b0-354">**Priorytet serwera** nx_dns_srv_priority 2 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="9c4b0-355">**Waga serwera** nx_dns_srv_weight 2 bajtów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="9c4b0-356">**Numer portu usługi** nx_dns_srv_port_number 2 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="9c4b0-357">**Zarezerwowane dla 4-bajtowego wyrównania** nx_dns_srv_reserved0 2 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="9c4b0-358">**Wskaźnik do nazwy hosta serwera** \* nx_dns_srv_hostname_ptr 4 bajty</span><span class="sxs-lookup"><span data-stu-id="9c4b0-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="9c4b0-359">Cztery rekordy SRV są przechowywane w podanym buforze.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="9c4b0-360">Każdy rekord NX_DNS_SRV_ENTRY zawiera wskaźnik *nx_dns_srv_hostname_ptr*, który wskazuje odpowiadający ciąg nazwy hosta w dolnej części buforu rekordu:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Cztery rekordy SRV](media/image7.png)

<span data-ttu-id="9c4b0-362">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych SRV w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9c4b0-363">Wraz z liczbą rekordów SRV zwróconych w programie \**record_count* aplikacja może analizować parametry SRV, w tym nazwę hosta serwera każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-364">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-364">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-365">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-366">**HOST_NAME** Wskaźnik na nazwę hosta, w którym mają zostać uzyskane dane SRV</span><span class="sxs-lookup"><span data-stu-id="9c4b0-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="9c4b0-367">**record_buffer** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane SRV</span><span class="sxs-lookup"><span data-stu-id="9c4b0-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="9c4b0-368">**buffer_size** Rozmiar buforu do przechowywania danych SRV</span><span class="sxs-lookup"><span data-stu-id="9c4b0-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="9c4b0-369">**record_count** Wskaźnik do liczby pobranych rekordów SRV</span><span class="sxs-lookup"><span data-stu-id="9c4b0-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="9c4b0-370">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-371">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-371">Return Values</span></span>

- <span data-ttu-id="9c4b0-372">**NX_SUCCESS** (0X00) pomyślnie uzyskał dane SRV</span><span class="sxs-lookup"><span data-stu-id="9c4b0-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="9c4b0-373">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-374">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-375">NX_DNS_PARAM_ERROR (0xA8) nieprawidłowy parametr niebędący wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="9c4b0-376">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-377">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-378">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-378">Allowed From</span></span>

<span data-ttu-id="9c4b0-379">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-380">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-380">Example</span></span>
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="9c4b0-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="9c4b0-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="9c4b0-382">Zwróć rozmiar listy serwerów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-383">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="9c4b0-384">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-384">Description</span></span>

<span data-ttu-id="9c4b0-385">Ta usługa zwraca liczbę prawidłowych serwerów DNS (IPv4 i IPv6) na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-386">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-386">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-387">**dns_ptr** Wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="9c4b0-388">**rozmiar** Zwraca liczbę serwerów na liście</span><span class="sxs-lookup"><span data-stu-id="9c4b0-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-389">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-389">Return Values</span></span>

- <span data-ttu-id="9c4b0-390">**NX_SUCCESS** (0x00) pomyślnie zwrócono rozmiar listy serwerów DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="9c4b0-391">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9c4b0-392">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-393">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-393">Allowed From</span></span>

<span data-ttu-id="9c4b0-394">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-395">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="9c4b0-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="9c4b0-397">Zwrotny adres IP i port serwera DNS według nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-398">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-399">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-399">Description</span></span>

<span data-ttu-id="9c4b0-400">Ta usługa zwraca adres IP serwera i port (rekord usługi) na podstawie kwerendy wejściowej nazwy hosta według zapytania DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="9c4b0-401">Jeśli rekord usługi nie zostanie znaleziony, ta procedura zwraca zerowy adres IP w wskaźniku adresu wejściowego, a stan błędu różny od zera zwraca, aby sygnalizować błąd.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-402">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-402">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-403">**dns_ptr** Wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="9c4b0-404">**HOST_NAME** Wskaźnik do buforu nazw hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="9c4b0-405">**host_address_ptr** Wskaźnik na adres do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="9c4b0-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="9c4b0-406">**host_port_ptr** Wskaźnik do portu do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="9c4b0-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="9c4b0-407">**WAIT_OPTION** Opcja oczekiwania dla odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-408">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-408">Return Values</span></span>

- <span data-ttu-id="9c4b0-409">Rekord serwera DNS **NX_SUCCESS** (0x00) został pomyślnie zwrócony</span><span class="sxs-lookup"><span data-stu-id="9c4b0-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="9c4b0-410">**NX_DNS_NO_SERVER** (0XA1) nie zarejestrowano serwera DNS z klientem w celu wysłania zapytania na hoście</span><span class="sxs-lookup"><span data-stu-id="9c4b0-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="9c4b0-411">Kwerenda DNS **NX_DNS_QUERY_FAILED** (0xA3) nie powiodła się; Brak odpowiedzi z dowolnego serwera DNS na liście klientów lub nie jest dostępny żaden rekord usługi dla wejściowej nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="9c4b0-412">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-413">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący</span><span class="sxs-lookup"><span data-stu-id="9c4b0-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-414">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-414">Allowed From</span></span>

<span data-ttu-id="9c4b0-415">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-416">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="9c4b0-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="9c4b0-418">Wyszukaj adres IPv4 dla nazwy hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="9c4b0-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-419">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-420">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-420">Description</span></span>

<span data-ttu-id="9c4b0-421">Ta usługa wysyła zapytanie typu A z określoną nazwą hosta, aby uzyskać adresy IP dla wejściowej nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="9c4b0-422">Klient DNS Kopiuje adres IPv4 z rekordu A zwróconego w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="9c4b0-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="9c4b0-423">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9c4b0-424">Wiele adresów IPv4 jest przechowywanych w buforze wyrównanym 4-bajtowym, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![wiele adresów 4-bajtowe wyrównane do bufora](media/image8.png)

<span data-ttu-id="9c4b0-426">Jeśli podany bufor nie może zawierać wszystkich danych adresów IP, pozostałe rekordy nie są przechowywane w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="9c4b0-427">Dzięki temu aplikacja może pobrać jeden, niektóre lub wszystkie dostępne dane adresu IP w odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="9c4b0-428">Wraz z liczbą rekordów zwróconych w programie \**record_count* aplikacja może analizować dane adresów IPv4 z *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-429">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-429">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-430">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-431">**host_name_ptr** Wskaźnik do nazwy hosta w celu uzyskania adresu IPv4</span><span class="sxs-lookup"><span data-stu-id="9c4b0-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="9c4b0-432">**bufor** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane IPv4</span><span class="sxs-lookup"><span data-stu-id="9c4b0-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="9c4b0-433">**buffer_size** Rozmiar buforu do przechowywania danych IPv4</span><span class="sxs-lookup"><span data-stu-id="9c4b0-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="9c4b0-434">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-435">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-435">Return Values</span></span>

- <span data-ttu-id="9c4b0-436">**NX_SUCCESS** (0X00) pomyślnie uzyskał dane protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="9c4b0-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="9c4b0-437">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-438">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-439">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-440">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-441">NX_DNS_PARAM_ERROR (0xA8) nieprawidłowy parametr niebędący wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-442">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-442">Allowed From</span></span>

<span data-ttu-id="9c4b0-443">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-444">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-444">Example</span></span>
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

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="9c4b0-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="9c4b0-446">Wyszukaj adres IPv6 dla nazwy hosta wejściowego</span><span class="sxs-lookup"><span data-stu-id="9c4b0-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-447">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-448">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-448">Description</span></span>

<span data-ttu-id="9c4b0-449">Ta usługa wysyła zapytanie typu AAAA z określoną nazwą domeny, aby uzyskać adresy IP dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="9c4b0-450">Klient DNS Kopiuje adres IPv6 z rekordów AAAA zwróconych w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="9c4b0-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-451">*Record_buffer* musi mieć 4-bajtowy wyrównany do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9c4b0-452">Poniżej przedstawiono format adresów IPv6 przechowywanych w buforze wyrównanym 4 bajty:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![Format IPv6 — bufor wyrównany do 4 bajtów](media/image9.png)

<span data-ttu-id="9c4b0-454">Jeśli dane wejściowe *record_buffer* nie mogą zawierać wszystkich danych AAAA w odpowiedzi serwera, *record_buffer* przechowuje tyle rekordów, ile się zmieści, i zwraca liczbę rekordów w buforze.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9c4b0-455">Dzięki liczbie rekordów AAAA zwróconych w programie \**record_count* aplikacja może analizować adresy IPv6 z każdego rekordu w *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-456">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-456">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-457">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-458">**host_name_ptr** Wskaźnik do nazwy hosta w celu uzyskania adresu IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="9c4b0-459">**bufor** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="9c4b0-460">**buffer_size** Rozmiar buforu do przechowywania danych IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="9c4b0-461">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-462">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-462">Return Values</span></span>

- <span data-ttu-id="9c4b0-463">**NX_SUCCESS** (0X00) pomyślnie uzyskał dane protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="9c4b0-464">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-465">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-466">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-467">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-468">NX_DNS_PARAM_ERROR (0xA8) nieprawidłowy parametr niebędący wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-469">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-469">Allowed From</span></span>

<span data-ttu-id="9c4b0-470">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-471">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-471">Example</span></span>
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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="9c4b0-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="9c4b0-473">Wyszukiwanie nazwy hosta na podstawie adresu IP</span><span class="sxs-lookup"><span data-stu-id="9c4b0-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-474">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-475">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-475">Description</span></span>

<span data-ttu-id="9c4b0-476">Ta usługa żąda rozpoznawania nazw podanego adresu IP z co najmniej jednego serwera DNS określonego wcześniej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="9c4b0-477">Jeśli to się powiedzie, nazwa hosta zakończona wartością NULL zostanie zwrócona w ciągu określonym przez *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="9c4b0-478">Jest to funkcja otoki usługi *nxd_dns_host_by_address_get* i nie akceptuje adresów IPv6.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-479">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-479">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-480">**dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="9c4b0-481">**IP_address** Adres IP, który ma zostać rozpoznany jako nazwa</span><span class="sxs-lookup"><span data-stu-id="9c4b0-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="9c4b0-482">**host_name_ptr** Wskaźnik do obszaru docelowego dla nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="9c4b0-483">**max_host_name_size** Rozmiar obszaru docelowego dla nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="9c4b0-484">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać w taktach czasomierza odpowiedzi serwera DNS po każdej kwerendzie DNS i ponowieniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="9c4b0-485">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="9c4b0-486">wartość limitu czasu (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="9c4b0-487">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer DNS odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="9c4b0-488">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozwiązanie DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-489">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-489">Return Values</span></span>

- <span data-ttu-id="9c4b0-490">**NX_SUCCESS** (0X00) pomyślne rozpoznanie systemu DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="9c4b0-491">Przekroczono limit czasu **NX_DNS_TIMEOUT** (0xA2) podczas uzyskiwania obiektu mutex usługi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="9c4b0-492">**NX_DNS_NO_SERVER** (0XA1) nie określono adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="9c4b0-493">**NX_DNS_QUERY_FAILED** (0xA3) nie otrzymał odpowiedzi na zapytanie</span><span class="sxs-lookup"><span data-stu-id="9c4b0-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="9c4b0-494">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) wartość null — adres wejściowy</span><span class="sxs-lookup"><span data-stu-id="9c4b0-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="9c4b0-495">Indeks **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) wskazuje nieprawidłowy typ adresu (np. IPv6)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="9c4b0-496">**NX_DNS_PARAM_ERROR** (0XA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9c4b0-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-498">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9c4b0-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9c4b0-499">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-500">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-500">Allowed From</span></span>

<span data-ttu-id="9c4b0-501">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-501">Threads</span></span>

<span data-ttu-id="9c4b0-502">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="9c4b0-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="9c4b0-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="9c4b0-504">Wyszukiwanie nazwy hosta na podstawie adresu IP</span><span class="sxs-lookup"><span data-stu-id="9c4b0-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-505">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-506">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-506">Description</span></span>

<span data-ttu-id="9c4b0-507">Ta usługa żąda rozpoznawania nazw adresów IPv6 lub IPv4 w *IP_address* argumencie wejściowym z co najmniej jednego serwera DNS określonego wcześniej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="9c4b0-508">Jeśli to się powiedzie, nazwa hosta zakończona wartością NULL zostanie zwrócona w ciągu określonym przez *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-509">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-509">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-510">**dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="9c4b0-511">**IP_address** Adres IP, który ma zostać rozpoznany jako nazwa</span><span class="sxs-lookup"><span data-stu-id="9c4b0-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="9c4b0-512">**host_name_ptr** Wskaźnik do obszaru docelowego dla nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="9c4b0-513">**max_host_name_size** Rozmiar obszaru docelowego dla nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="9c4b0-514">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać w taktach czasomierza odpowiedzi serwera DNS po każdej kwerendzie DNS i ponowieniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="9c4b0-515">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="9c4b0-516">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="9c4b0-517">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer DNS odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="9c4b0-518">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozwiązanie DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-519">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-519">Return Values</span></span>

- <span data-ttu-id="9c4b0-520">**NX_SUCCESS** (0X00) pomyślne rozpoznanie systemu DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="9c4b0-521">Przekroczono limit czasu **NX_DNS_TIMEOUT** (0xA2) podczas uzyskiwania obiektu mutex usługi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="9c4b0-522">**NX_DNS_NO_SERVER** (0XA1) nie określono adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="9c4b0-523">**NX_DNS_QUERY_FAILED** (0xA3) nie otrzymał odpowiedzi na zapytanie</span><span class="sxs-lookup"><span data-stu-id="9c4b0-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="9c4b0-524">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) wartość null — adres wejściowy</span><span class="sxs-lookup"><span data-stu-id="9c4b0-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="9c4b0-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-526">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9c4b0-527">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-528">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-529">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-529">Allowed From</span></span>

<span data-ttu-id="9c4b0-530">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-530">Threads</span></span>

<span data-ttu-id="9c4b0-531">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="9c4b0-531">**Example**</span></span>
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

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="9c4b0-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="9c4b0-533">Wyszukaj adres IP z nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-534">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-535">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-535">Description</span></span>

<span data-ttu-id="9c4b0-536">Ta usługa żąda rozpoznawania nazw podanej nazwy z co najmniej jednego serwera DNS określonego wcześniej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="9c4b0-537">Jeśli to się powiedzie, skojarzony adres IP jest zwracany w miejscu docelowym wskazywanym przez host_address_ptr.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="9c4b0-538">Jest to funkcja otoki usługi *nxd_dns_host_by_name_get* i jest ograniczona do danych wejściowych adresów IPv4.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-539">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-539">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-540">**dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="9c4b0-541">**HOST_NAME** Wskaźnik do nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="9c4b0-542">**host_address_ptr** Zwrócony adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="9c4b0-543">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na rozpoznawanie nazw DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="9c4b0-544">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="9c4b0-545">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="9c4b0-546">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer DNS odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="9c4b0-547">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozwiązanie DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-548">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-548">Return Values</span></span>

- <span data-ttu-id="9c4b0-549">**NX_SUCCESS** (0X00) pomyślne rozpoznanie systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="9c4b0-550">**NX_DNS_NO_SERVER** (0XA1) nie określono adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="9c4b0-551">**NX_DNS_QUERY_FAILED** (0xA3) nie otrzymał odpowiedzi na zapytanie</span><span class="sxs-lookup"><span data-stu-id="9c4b0-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="9c4b0-552">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9c4b0-553">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9c4b0-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9c4b0-554">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-555">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-555">Allowed From</span></span>

<span data-ttu-id="9c4b0-556">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-556">Threads</span></span>

<span data-ttu-id="9c4b0-557">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="9c4b0-557">**Example**</span></span>
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

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="9c4b0-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="9c4b0-559">Wyszukaj adres IP z nazwy hosta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-560">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="9c4b0-561">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-561">Description</span></span>

<span data-ttu-id="9c4b0-562">Ta usługa żąda rozpoznawania nazw podanego adresu IP z co najmniej jednego serwera DNS określonego wcześniej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="9c4b0-563">Jeśli to się powiedzie, skojarzony adres IP jest zwracany w NXD_ADDRESS wskazywanym przez *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="9c4b0-564">Jeśli obiekt wywołujący jawnie ustawi lookup_type dane wejściowe do NX_IP_VERSION_V6, ta usługa wyśle zapytanie o adres IPv6 hosta (rekord AAAA).</span><span class="sxs-lookup"><span data-stu-id="9c4b0-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="9c4b0-565">Jeśli obiekt wywołujący jawnie ustawi lookup_type dane wejściowe do NX_IP_VERSION_V4, ta usługa wyśle zapytanie o adres IPv4 hosta (rekord A).</span><span class="sxs-lookup"><span data-stu-id="9c4b0-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-566">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-566">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-567">**dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="9c4b0-568">**HOST_NAME** Wskaźnik na nazwę hosta, aby znaleźć adres IP</span><span class="sxs-lookup"><span data-stu-id="9c4b0-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="9c4b0-569">**host_address_ptr** Wskaźnik do miejsca docelowego dla NXD_ADDRESS zawierającego adres IP</span><span class="sxs-lookup"><span data-stu-id="9c4b0-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="9c4b0-570">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać w taktach czasomierza odpowiedzi serwera DNS dla każdej transmisji i ponownej transmisji zapytań.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="9c4b0-571">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="9c4b0-572">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="9c4b0-573">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer DNS odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="9c4b0-574">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na rozwiązanie DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="9c4b0-575">**lookup_type** Wskaż typ odnośnika (A A AAAA).</span><span class="sxs-lookup"><span data-stu-id="9c4b0-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-576">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-576">Return Values</span></span>

- <span data-ttu-id="9c4b0-577">**NX_SUCCESS** (0X00) pomyślne rozpoznanie systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="9c4b0-578">**NX_DNS_NO_SERVER** (0XA1) nie określono adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="9c4b0-579">**NX_DNS_QUERY_FAILED** (0xA3) nie otrzymał odpowiedzi na zapytanie</span><span class="sxs-lookup"><span data-stu-id="9c4b0-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="9c4b0-580">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) wartość null — adres wejściowy</span><span class="sxs-lookup"><span data-stu-id="9c4b0-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="9c4b0-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-582">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9c4b0-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9c4b0-583">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-584">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-585">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-585">Allowed From</span></span>

<span data-ttu-id="9c4b0-586">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-586">Threads</span></span>

<span data-ttu-id="9c4b0-587">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="9c4b0-587">**Example**</span></span>
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

<span data-ttu-id="9c4b0-588">Inny przykład korzystania z tej usługi czasu, tym razem z użyciem adresów IPv4 i typów rekordów, przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="9c4b0-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="9c4b0-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="9c4b0-590">Wyszukaj ciąg tekstowy dla nazwy domeny wejściowej</span><span class="sxs-lookup"><span data-stu-id="9c4b0-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-591">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9c4b0-592">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-592">Description</span></span>

<span data-ttu-id="9c4b0-593">Ta usługa wysyła zapytanie typu TXT z określoną nazwą domeny i buforem, aby uzyskać dowolne dane ciągu.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="9c4b0-594">Klient DNS kopiuje ciąg tekstowy z rekordu TXT w odpowiedzi serwera DNS do lokalizacji pamięci *record_buffer* .</span><span class="sxs-lookup"><span data-stu-id="9c4b0-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-595">Record_buffer nie musi być wyrównany 4-bajtowo w celu uzyskania danych.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-596">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-596">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-597">**dns_ptr** Wskaźnik do klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9c4b0-598">**HOST_NAME** Wskaźnik na nazwę hosta do przeszukania</span><span class="sxs-lookup"><span data-stu-id="9c4b0-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="9c4b0-599">**record_buffer** Wskaźnik do lokalizacji, do której mają zostać wyodrębnione dane TXT</span><span class="sxs-lookup"><span data-stu-id="9c4b0-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="9c4b0-600">**buffer_size** Rozmiar buforu do przechowywania danych TXT</span><span class="sxs-lookup"><span data-stu-id="9c4b0-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="9c4b0-601">**WAIT_OPTION** Opcja oczekiwania na odebranie odpowiedzi serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-602">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-602">Return Values</span></span>

- <span data-ttu-id="9c4b0-603">**NX_SUCCESS** (0X00) pomyślnie uzyskano ciąg txt</span><span class="sxs-lookup"><span data-stu-id="9c4b0-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="9c4b0-604">Lista serwerów klienta **NX_DNS_NO_SERVER** (0xa1) jest pusta</span><span class="sxs-lookup"><span data-stu-id="9c4b0-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9c4b0-605">**NX_DNS_QUERY_FAILED** (0XA3) nie odebrano prawidłowej odpowiedzi DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9c4b0-606">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9c4b0-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9c4b0-607">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-608">NX_DNS_PARAM_ERROR (0xA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-609">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-609">Allowed From</span></span>

<span data-ttu-id="9c4b0-610">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-610">Threads</span></span>

######   
<span data-ttu-id="9c4b0-611">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-611">Example</span></span>
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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="9c4b0-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="9c4b0-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="9c4b0-613">Ustawianie puli pakietów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-614">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="9c4b0-615">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-615">Description</span></span>

<span data-ttu-id="9c4b0-616">Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="9c4b0-617">Klient DNS będzie używać tej puli pakietów do wysyłania zapytań DNS, więc ładunek pakietu nie powinien być mniejszy niż NX_DNS_PACKET_PAYLOAD, który obejmuje nagłówki Ethernet, IP i UDP i jest zdefiniowany w *nxd_dns. h.*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-618">*W* przypadku usunięcia klienta DNS Pula pakietów nie jest usuwana z nią i jest odpowiedzialna za usunięcie puli pakietów, gdy nie jest już potrzebna.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="9c4b0-619">Ta usługa jest dostępna tylko wtedy, gdy opcja konfiguracji NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest zdefiniowana w *nxd_dns. h*</span><span class="sxs-lookup"><span data-stu-id="9c4b0-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-620">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-620">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-621">**dns_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="9c4b0-622">**pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-623">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-623">Return Values</span></span>

- <span data-ttu-id="9c4b0-624">Zakończono pomyślne uzupełnianie **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="9c4b0-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="9c4b0-625">Klient **NX_NOT_ENABLED** (0x14) nie został skonfigurowany dla tej opcji</span><span class="sxs-lookup"><span data-stu-id="9c4b0-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="9c4b0-626">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="9c4b0-627">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-628">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-628">Allowed From</span></span>

<span data-ttu-id="9c4b0-629">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-630">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-630">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="9c4b0-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="9c4b0-631">nx_dns_server_add</span></span>

<span data-ttu-id="9c4b0-632">Dodaj adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-633">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="9c4b0-634">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-634">Description</span></span>

<span data-ttu-id="9c4b0-635">Ta usługa dodaje serwer DNS IPv4 do listy serwerów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-636">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-636">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-637">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="9c4b0-638">**server_address** Adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-639">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-639">Return Values</span></span>

- <span data-ttu-id="9c4b0-640">Pomyślnie dodano serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="9c4b0-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="9c4b0-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="9c4b0-642">**NX_NO_MORE_ENTRIES** (0X17) nie można uzyskać więcej serwerów DNS (lista jest pełna)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="9c4b0-643">**NX_DNS_PARAM_ERROR** (0XA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9c4b0-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-645">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9c4b0-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9c4b0-646">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) — wprowadzanie adresu serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="9c4b0-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-648">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-648">Allowed From</span></span>

<span data-ttu-id="9c4b0-649">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-650">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="9c4b0-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="9c4b0-651">nxd_dns_server_add</span></span>

<span data-ttu-id="9c4b0-652">Dodawanie serwera DNS do listy klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="9c4b0-654">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-654">Description</span></span>

<span data-ttu-id="9c4b0-655">Ta usługa dodaje adres IP serwera DNS do listy serwerów klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="9c4b0-656">Server_address może być adresem IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="9c4b0-657">Jeśli klient chce mieć dostęp do tego samego serwera przy użyciu adresu IPv4 lub adresu IPv6, należy dodać oba adresy IP jako wpisy do listy serwerów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-658">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-658">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-659">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="9c4b0-660">**server_address** Wskaźnik do NXD_ADDRESS zawierający adres IP serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-661">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-661">Return Values</span></span>

- <span data-ttu-id="9c4b0-662">Pomyślnie dodano serwer **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="9c4b0-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="9c4b0-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="9c4b0-664">**NX_NO_MORE_ENTRIES** (0X17) nie można uzyskać więcej serwerów DNS (lista jest pełna)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="9c4b0-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-666">**NX_DNS_PARAM_ERROR** (0XA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9c4b0-667">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9c4b0-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9c4b0-668">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) — wprowadzanie adresu serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="9c4b0-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="9c4b0-670">Indeks NX_DNS_INVALID_ADDRESS_TYPE (0xB2) wskazuje nieprawidłowy typ adresu (np. IPv6)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-671">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-671">Allowed From</span></span>

<span data-ttu-id="9c4b0-672">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-673">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-673">Example</span></span>
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

## <a name="nx_dns_server_get"></a><span data-ttu-id="9c4b0-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-674">nx_dns_server_get</span></span>

<span data-ttu-id="9c4b0-675">Zwracanie serwera DNS IPv4 z listy klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-676">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="9c4b0-677">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-677">Description</span></span>

<span data-ttu-id="9c4b0-678">Ta usługa zwraca adres serwera DNS IPv4 z listy serwerów o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-679">Indeks jest oparty na zero.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-679">The index is zero based.</span></span> <span data-ttu-id="9c4b0-680">Jeśli indeks wejściowy przekracza rozmiar listy klienta DNS, w tym indeksie zostanie znaleziony adres IPv6 lub w określonym indeksie zostanie znaleziony adres o wartości null, zostanie zwrócony błąd.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="9c4b0-681">Usługa *nx_dns_get_serverlist_size* może zostać wywołana najpierw uzyskać liczbę serwerów DNS na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="9c4b0-682">Ta usługa obsługuje tylko adresy IPv4.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="9c4b0-683">Wywołuje usługę *nxd_dns_server_get* , która obsługuje zarówno adresy IPv4, jak i IPv6.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-684">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-684">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-685">**dns_ptr** Wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="9c4b0-686">**indeks** Indeksowanie na liście serwerów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="9c4b0-687">**dns_server_address** Wskaźnik na adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-688">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-688">Return Values</span></span>

- <span data-ttu-id="9c4b0-689">Pomyślne zwrócenie serwera **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="9c4b0-690">Indeks **NX_DNS_SERVER_NOT_FOUND** (0xA9) wskazuje puste miejsce</span><span class="sxs-lookup"><span data-stu-id="9c4b0-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="9c4b0-691">Indeks **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) wskazuje na adres null</span><span class="sxs-lookup"><span data-stu-id="9c4b0-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="9c4b0-692">Indeks **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) wskazuje nieprawidłowy typ adresu (np. IPv6)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="9c4b0-693">**NX_DNS_PARAM_ERROR** (0XA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="9c4b0-694">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9c4b0-695">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-696">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-696">Allowed From</span></span>

<span data-ttu-id="9c4b0-697">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-698">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="9c4b0-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="9c4b0-699">nxd_dns_server_get</span></span>

<span data-ttu-id="9c4b0-700">Zwracanie serwera DNS z listy klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-701">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="9c4b0-702">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-702">Description</span></span>

<span data-ttu-id="9c4b0-703">Ta usługa zwraca adres IP serwera DNS z listy serwerów o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="9c4b0-704">Indeks jest oparty na zero.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-704">The index is zero based.</span></span> <span data-ttu-id="9c4b0-705">Jeśli indeks wejściowy przekracza rozmiar listy klientów DNS lub w określonym indeksie zostanie znaleziony adres null, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="9c4b0-706">Usługa *nx_dns_get_serverlist_size* może być wywoływana w pierwszej kolejności, aby uzyskać liczbę serwerów DNS na liście serwerów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="9c4b0-707">Ta usługa obsługuje adresy IPv4 i IPv6.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-708">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-708">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-709">**dns_ptr** Wskaźnik do bloku kontroli DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="9c4b0-710">**indeks** Indeksowanie na liście serwerów klienta DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="9c4b0-711">**dns_server_address** Wskaźnik na adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="9c4b0-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-712">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-712">Return Values</span></span>

- <span data-ttu-id="9c4b0-713">**NX_SUCCESS** (0X00) pomyślnie ZWRÓCIŁ adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="9c4b0-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="9c4b0-714">Indeks **NX_DNS_SERVER_NOT_FOUND** (0xA9) wskazuje puste miejsce</span><span class="sxs-lookup"><span data-stu-id="9c4b0-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="9c4b0-715">Indeks **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) wskazuje na adres serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="9c4b0-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="9c4b0-716">Indeks **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) wskazuje nieprawidłowy typ adresu (np. IPv6)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="9c4b0-717">**NX_DNS_PARAM_ERROR** (0XA8) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="9c4b0-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9c4b0-718">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9c4b0-719">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-720">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-720">Allowed From</span></span>

<span data-ttu-id="9c4b0-721">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-722">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="9c4b0-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="9c4b0-723">nx_dns_server_remove</span></span>

<span data-ttu-id="9c4b0-724">Usuwanie serwera DNS IPv4 z listy klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-725">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="9c4b0-726">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-726">Description</span></span>

<span data-ttu-id="9c4b0-727">Ta usługa usuwa serwer DNS IPv4 z listy klientów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="9c4b0-728">Jest to funkcja otoki dla *nxd_dns_server_remove*.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-729">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-729">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-730">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="9c4b0-731">**server_address** Adres IP serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-732">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-732">Return Values</span></span>

- <span data-ttu-id="9c4b0-733">Pomyślnie usunięto serwer DNS **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="9c4b0-734">Serwer **NX_DNS_SERVER_NOT_FOUND** (0xA9) nie znajduje się na liście klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="9c4b0-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — wprowadzanie adresu serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="9c4b0-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="9c4b0-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-737">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9c4b0-738">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-739">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-739">Allowed From</span></span>

<span data-ttu-id="9c4b0-740">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-741">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="9c4b0-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="9c4b0-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="9c4b0-743">Usuwanie serwera DNS z listy klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-744">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="9c4b0-745">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-745">Description</span></span>

<span data-ttu-id="9c4b0-746">Ta usługa usuwa serwer DNS z podanego adresu IP z listy klientów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="9c4b0-747">Wejściowy adres IP akceptuje zarówno adresy IPv4, jak i IPv6.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="9c4b0-748">Po usunięciu serwera pozostałe serwery przechodzą w dół o jeden indeks na liście, aby wypełnić miejsce opuszczone.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-749">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-749">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-750">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="9c4b0-751">**server_address** Wskaźnik do serwera DNS NXD_ADDRESS dane zawierające adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-752">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-752">Return Values</span></span>

- <span data-ttu-id="9c4b0-753">Pomyślnie usunięto serwer DNS **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="9c4b0-754">Serwer **NX_DNS_SERVER_NOT_FOUND** (0xA9) nie znajduje się na liście klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="9c4b0-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — wprowadzanie adresu serwera o wartości null</span><span class="sxs-lookup"><span data-stu-id="9c4b0-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="9c4b0-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) nie może przetworzyć rekordu przy wyłączonym protokole IPv6</span><span class="sxs-lookup"><span data-stu-id="9c4b0-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="9c4b0-757">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9c4b0-758">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9c4b0-759">Indeks NX_DNS_INVALID_ADDRESS_TYPE (0xB2) wskazuje nieprawidłowy typ adresu (np. IPv6)</span><span class="sxs-lookup"><span data-stu-id="9c4b0-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-760">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-760">Allowed From</span></span>

<span data-ttu-id="9c4b0-761">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-762">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-762">Example</span></span>
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

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="9c4b0-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="9c4b0-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="9c4b0-764">Usuń wszystkie serwery DNS z listy klientów</span><span class="sxs-lookup"><span data-stu-id="9c4b0-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9c4b0-765">Prototype</span><span class="sxs-lookup"><span data-stu-id="9c4b0-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="9c4b0-766">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4b0-766">Description</span></span>

<span data-ttu-id="9c4b0-767">Ta usługa usuwa wszystkie serwery DNS z listy klientów.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9c4b0-768">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="9c4b0-768">Input Parameters</span></span>

- <span data-ttu-id="9c4b0-769">**dns_ptr** Wskaźnik do bloku kontroli DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9c4b0-770">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="9c4b0-770">Return Values</span></span>

- <span data-ttu-id="9c4b0-771">Serwery DNS **NX_SUCCESS** (0x00) zostały pomyślnie usunięte</span><span class="sxs-lookup"><span data-stu-id="9c4b0-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="9c4b0-772">**NX_DNS_ERROR** (0XA0) nie może uzyskać obiektu mutex ochrony</span><span class="sxs-lookup"><span data-stu-id="9c4b0-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="9c4b0-773">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik adresu IP lub DNS.</span><span class="sxs-lookup"><span data-stu-id="9c4b0-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9c4b0-774">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="9c4b0-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9c4b0-775">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="9c4b0-775">Allowed From</span></span>

<span data-ttu-id="9c4b0-776">Wątki</span><span class="sxs-lookup"><span data-stu-id="9c4b0-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9c4b0-777">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c4b0-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```