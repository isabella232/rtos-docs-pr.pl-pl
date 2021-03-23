---
title: Rozdział 2 — Instalowanie i używanie klienta DNS usługi Azure RTO NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta DNS usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 054b7366eb9a28bc0dc2fb8c4b2479c12532499b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822657"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a>Rozdział 2 — Instalowanie i używanie klienta DNS usługi Azure RTO NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta DNS usługi Azure RTO NetX.

## <a name="product-distribution"></a>Dystrybucja produktu

Klient DNS NetX jest dostępny pod adresem <https://github.com/azure-rtos/netx> . Pakiet zawiera następujące pliki:

- **nx_dns. h**: plik nagłówkowy dla klienta DNS NetX
- plik źródłowy **nx_dns. c**: c dla klienta DNS NetX
- **nx_dns.pdf**: Opis pliku PDF NetX klienta DNS

## <a name="dns-client-installation"></a>Instalacja klienta DNS

Aby użyć NetX klienta DNS, skopiuj pliki kodu źródłowego *nx_dns. c* i *nx_dns. h* do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_dns. h* i *nx_dns. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-the-dns-client"></a>Korzystanie z klienta DNS

Korzystanie z klienta DNS NetX jest proste. W zasadzie kod aplikacji musi zawierać *nx_dns. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX. Po dołączeniu *nx_dns. h* kod aplikacji może następnie wprowadzić wywołania funkcji DNS w dalszej części tego przewodnika. Aplikacja musi również dodać *nx_dns. c* do procesu kompilacji. Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z usługi NetX DNS.

>[!NOTE]
> Ponieważ usługa DNS korzysta z usług NetX UDP, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem usługi DNS.

## <a name="small-example-system-for-dns-client"></a>Mały przykładowy system dla klienta DNS 

W przykładowym programie aplikacji DNS dostarczonym w tej sekcji *nx_dns. h* jest zawarty w wierszu 6. NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, co umożliwia aplikacji klienta DNS utworzenie puli pakietów dla klienta DNS, jest zadeklarowana w wierszach 21-23. Ta Pula pakietów służy do alokowania pakietów do wysyłania komunikatów DNS. Jeśli zdefiniowano NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, Pula pakietów zostanie utworzona w wierszach 71-91. Jeśli ta opcja nie jest włączona, klient DNS tworzy własną pulę pakietów zgodnie z rozmiarem ładunku pakietu i pulą ustawioną przez parametry konfiguracji w *nx_dns. h* i opisany w innym miejscu w tym rozdziale.

Inna Pula pakietów jest tworzona w wierszach 93-105 dla wystąpienia IP klienta, które jest używane dla wewnętrznych operacji NetX. Następne wystąpienie protokołu IP jest tworzone przy użyciu wywołania *nx_ip_create* w wierszu 107-119. Istnieje możliwość, aby zadanie IP i klient DNS mogli współużytkować tę samą pulę pakietów, ale ponieważ klient DNS zazwyczaj wysyła więcej komunikatów niż pakiety sterujące wysyłane przez zadanie IP, używając oddzielnych pul pakietów, co zwiększa efektywność korzystania z pamięci.

Protokoły ARP i UDP (używane przez sieci IPv4) są włączane odpowiednio w wierszach 122 i 134.

>[!NOTE]
> W tej wersji demonstracyjnej użyto sterownika "ram" zadeklarowanego w wierszu 37 i użytego w wywołaniu *nx_ip_create* . Ten sterownik pamięci RAM jest dystrybuowany z kodem źródłowym NetX. Aby w rzeczywistości uruchomić klienta DNS, aplikacja musi dostarczyć rzeczywisty sterownik sieci fizycznej do przesyłania i odbierania pakietów z serwera DNS.

Funkcja wpisu wątku klienta *thread_client_entry* jest definiowana poniżej funkcji *tx_application_define* . Początkowo program zrzeka się kontroli do systemu, aby umożliwić zainicjowanie wątku zadania IP przez sterownik sieciowy.

Następnie tworzy klienta DNS w wierszach 176-187, inicjuje pamięć podręczną w wierszach 189-200 i ustawia pulę pakietów utworzoną wcześniej w wystąpieniu klienta DNS w wierszach 202-217. Następnie dodaje serwer DNS IPv4 w wierszach 220-229.

Pozostała część przykładowego programu używa usług klienta DNS do wykonywania zapytań DNS. Wyszukiwania adresów IP hosta są wykonywane w wierszach 240 i 262. Różnica między tymi dwoma usługami, *nx_dns_host_by_name_get* i *nx_dns_ipv4_address_by_name_get*, polega na tym, że pierwsza tylko zapisuje jeden adres IP, podczas gdy serwer DNS odpowiedział na wiele adresów.

Wyszukiwania wsteczne (nazwa hosta na podstawie adresu IP) są wykonywane w wierszach 354 (*nx_dns_host_by_address_get*).

Dwie więcej usług dla wyszukiwania DNS, CNAME i TXT są odpowiednio przedstawiane w wierszach 375 i 420, aby odnaleźć CNAME i TXT dla nazwy domeny wejściowej. NetX klienta DNS jako podobne usługi dla innych typów rekordów, np. NS, MX, SRV i SOA. Zobacz rozdział 3, aby uzyskać szczegółowe opisy wszystkich wyszukiwań typu rekordu dostępnych w NetX DNS Client.

Po usunięciu klienta DNS w wierszu 594 przy użyciu usługi *nx_dns_delete* Pula pakietów dla klienta DNS nie zostanie usunięta, chyba że klient DNS utworzył własną pulę pakietów. W przeciwnym razie aplikacja może usunąć pulę pakietów, jeśli nie ma do niej zastosowania.

```c
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack.*/
#include "tx_api.h"
#include "nx_api.h"
#include "nx_udp.h"
#include "nx_dns.h"

#define     DEMO_STACK_SIZE         4096
#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS             client_dns;
TX_THREAD          client_thread;
NX_IP              client_ip;
NX_PACKET_POOL     main_pool;

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
    NX_PACKET_POOL client_pool;
#endif

UCHAR       local_cache[LOCAL_CACHE_SIZE];
UINT        error_counter = 0;
#define     CLIENT_ADDRESS IP_ADDRESS(192,168,0,11)
#define     DNS_SERVER_ADDRESS IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */
void        thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern     VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */
int main()
{
/* Enter the ThreadX kernel. */
    tx_kernel_enter();
}
/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    CHAR     *pointer;
    UINT     status;
    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;
    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", 
                     thread_client_entry, 0, pointer, 
                     DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, 
                     TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /*Create the packet pool for the DNS Client to send packets. If the DNS Client is configured for letting the host application create the DNS packet pool, 
        (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see 77 nx_dns_create() for guidelines on packet payload size and pool size. 
        packet traffic for NetX processes.
    */

    status = nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                   NX_DNS_PACKET_PAYLOAD, pointer, 
                                   NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;
    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

#endif
/* Create the packet pool which the IP task will use to send packets. Also available to the host 94 application to send packet. */

    status = nx_packet_pool_create(&main_pool, "Main Packet Pool", 
                                   NX_PACKET_PAYLOAD, pointer, 
                                   NX_PACKET_POOL_SIZE);
    pointer = pointer + NX_PACKET_POOL_SIZE;

/* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

/* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", 
                          CLIENT_ADDRESS, 0xFFFFFF00UL, 
                          &main_pool, _nx_ram_network_driver, 
                          pointer, 2048, 1);
    pointer = pointer + 2048;

/* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status = nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

/* Check for ARP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable UDP traffic because DNS is a UDP based protocol. */

    status = nx_udp_enable(&client_ip);
/* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

}

#define BUFFER_SIZE 200
#define RECORD_COUNT 10

/* Define the Client thread. */
void thread_client_entry(ULONG thread_input)
{
    UCHAR         record_buffer[200];
    UINT          record_count;
    UINT          status;
    ULONG         host_ip_address;
    UINT          i;
    ULONG         *ipv4_address_ptr[RECORD_COUNT];

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
    NX_DNS_NS_ENTRY    *nx_dns_ns_entry_ptr[RECORD_COUNT];
    NX_DNS_MX_ENTRY    *nx_dns_mx_entry_ptr[RECORD_COUNT];
    NX_DNS_SRV_ENTRY    *nx_dns_srv_entry_ptr[RECORD_COUNT];
    NX_DNS_SOA_ENTRY    *nx_dns_soa_entry_ptr;
    ULONG                host_address;
    USHORT               host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);
    /* Create a DNS instance for the Client. Note this function will create the DNS Client packet pool for creating DNS message packets intended for querying its DNS server. */
    status = nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

    /* Check for DNS create error. */
    if (status)
    {
        error_counter++;
        return;
    }

#ifdef NX_DNS_CACHE_ENABLE
    /* Initialize the cache. */
    status = nx_dns_cache_initialize(&client_dns, local_cache, LOCAL_CACHE_SIZE);

    /* Check for DNS cache error. */
    if (status)
    {
        error_counter++;
        return;
    }
#endif

/* Is the DNS client configured for the host application to create the pecket pool? */
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Yes, use the packet pool created above which has appropriate payload size for DNS messages. */
    status = nx_dns_packet_pool_set(&client_dns, &client_pool);
    /* Check for set DNS packet pool error. */
        
    if (status)
    {
        error_counter++;
        return;
    }
#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);
    /* Check for DNS add server error. */
    if (status)
    {
        error_counter++;
        return;
    }
/********************************************************************************/
/* Type A */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }
    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
               *ipv4_address_ptr[i] >> 24,
               *ipv4_address_ptr[i] >> 16 & 0xFF,
               *ipv4_address_ptr[i] >> 8 & 0xFF,
               *ipv4_address_ptr[i] & 0xFF);
    }
/********************************************************************************/
/* Type A + CNAME response */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
    
    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }

    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 
                                             &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test Test A + CNAME response: ");
        printf("record_count = %d \n", record_count);
    }
    
    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }

/********************************************************************************/
/* Type PTR */
/* Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

    /* Look up host name over IPv4. */
    host_ip_address = IP_ADDRESS(74, 125, 71, 106);
    status = nx_dns_host_by_address_get(&client_dns, host_ip_address, &record_buffer[0], BUFFER_SIZE, 450);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/* Type CNAME */
/* Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

    /* Send CNAME type to record the canonical name of host in record_buffer. */

    status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", 
                              &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test CNAME: %s\n", record_buffer);
    }
/********************************************************************************/
/* Type TXT */
/* Send TXT type DNS Query to its DNS server and get descriptive text. */
/********************************************************************************/

    /* Send TXT type to record the descriptive test of host in record_buffer. */
    status = nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test TXT: %s\n", record_buffer);
    }

/********************************************************************************/
/* Type NS */
/* Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

    /* Send NS type to record multiple name servers in record_buffer and return the name server count. If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */

    status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                           &record_buffer[0], BUFFER_SIZE, 
                                           &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/* Type MX */
/* Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

    /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count. If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */

    status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test MX: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the mail exchange. */
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

/********************************************************************************/
/* Type SRV */
/* Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

    /* Send SRV DNS query type to record the location of services in record_buffer and return count. If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */

    status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                       &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);
    }
    
    /* Get the location of services. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

        printf("port number = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
        printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
        printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

        if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
            printf("hostname = %s\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

    /* Get the service info, NetX old API.*/
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                     &host_address, &host_port, 200);
    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }
    
/********************************************************************************/
/* Type SOA */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

    /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */

    status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    
    /* Get the loc*/
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    printf("------------------------------------------------------> n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
        printf("host mname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    else
        printf("host mame is not set\n");
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
        printf("host rname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    else
        printf("host rname is not set\n");
    #endif

    /* Shutting down...*/
    /* Terminate the DNS Client thread. */
    status = nx_dns_delete(&client_dns);
    return;
}
```

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania systemu DNS dla NetX. Te opcje można ponownie zdefiniować w *nx_dns. h.* Poniższa lista zawiera szczegółowy opis:  

- **NX_DNS_TYPE_OF_SERVICE**: typ usługi wymaganej przez żądania UDP DNS. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL dla normalnej usługi pakietów IP.

- **NX_DNS_TIME_TO_LIVE**: określa maksymalną liczbę routerów, jaką może przekazać pakiet, zanim zostanie on odrzucony. Wartość domyślna to 0x80

- **NX_DNS_FRAGMENT_OPTION**: ustawia właściwość gniazda, aby zezwalać na fragmentację pakietów wychodzących lub go nie zezwalać. Wartość domyślna to NX_DONT_FRAGMENT.

- **NX_DNS_QUEUE_DEPTH**: ustawia maksymalną liczbę pakietów do zapisania w kolejce odbioru gniazda. Wartość domyślna to 5.

- **NX_DNS_MAX_SERVERS**: określa maksymalną liczbę serwerów DNS na liście serwerów klienta.

- **NX_DNS_MESSAGE_MAX**: maksymalny rozmiar komunikatu DNS na potrzeby wysyłania zapytań DNS. Wartość domyślna to 512, który jest również maksymalnym rozmiarem określonym w dokumencie RFC 1035 sekcja 2.3.4.

- **NX_DNS_PACKET_PAYLOAD_UNALIGNED**: Jeśli nie zostanie zdefiniowany, rozmiar ładunku pakietu klienta, który zawiera nagłówki Ethernet, IP (lub IPv6) i UDP, oraz maksymalny rozmiar komunikatu DNS określony przez NX_DNS_MESSAGE_MAX. Niezależnie od tego, czy jest zdefiniowany, ładunek pakietu jest wyrównany 4-bajtowy i przechowywany w NX_DNS_PACKET_PAYLOAD.

- **NX_DNS_PACKET_POOL_SIZE**: rozmiar puli pakietów klienta na potrzeby wysyłania zapytań DNS, jeśli nie określono NX_DNS_CLIENT_USER_CREATE_PACKET_POOL. Wartość domyślna jest wystarczająco duża dla 16 pakietów o rozmiarze ładunku zdefiniowanym przez NX_DNS_PACKET_PAYLOAD i ma 4-bajtowe wyrównanie.

- **NX_DNS_MAX_RETRIES**: Maksymalna liczba przypadków, gdy klient DNS wyśle zapytanie do bieżącego serwera DNS przed podjęciem próby innego serwera lub przerwaniem zapytania DNS.

- **NX_DNS_MAX_RETRANS_TIMEOUT**: maksymalny limit czasu retransmisji dla zapytania DNS do określonego serwera DNS. Wartość domyślna to 64 sekund (64 * NX_IP_PERIODIC_RATE).

- **NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: Jeśli jest zdefiniowany, a adres bramy IPv4 klienta jest różny od zera, klient DNS ustawia bramę IPv4 jako podstawowy serwer DNS klienta. Wartość domyślna jest wyłączona.

- **NX_DNS_PACKET_ALLOCATE_TIMEOUT**: ustawia opcję limitu czasu dla przydzielania pakietu z puli pakietów klienta DNS. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).

- **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: pozwala klientowi DNS zezwolić aplikacji na tworzenie i Ustawianie puli pakietów klienta DNS. Domyślnie ta opcja jest wyłączona, a klient DNS tworzy własną pulę pakietów w *nx_dns_create*.

- **NX_DNS_CLIENT_CLEAR_QUEUE**: umożliwia klientowi DNS czyszczenie starych komunikatów DNS z kolejki odbierania przed wysłaniem nowej kwerendy. Usunięcie tych pakietów z poprzednich zapytań DNS uniemożliwia kolejkowanie gniazda klienta DNS z przepełniania i usuwania prawidłowych pakietów.

- **NX_DNS_ENABLE_EXTENDED_RR_TYPES**: Dzięki temu Klient DNS może wysyłać zapytania dotyczące dodatkowych typów rekordów DNS w (np. CNAME, NS, MX, SOA, SRV i txt).

- **NX_DNS_CACHE_ENABLE**: umożliwia klientowi DNS przechowywanie rekordów odpowiedzi w pamięci podręcznej DNS.
