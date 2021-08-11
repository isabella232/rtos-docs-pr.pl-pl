---
title: Rozdział 2 — Instalowanie i używanie klienta DNS Azure RTOS NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem klienta DNS Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ffd6e7308775d919818420a2276f28d07ca3e9f467af71bb6e0524b7b3a79de8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799510"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a>Rozdział 2 — Instalowanie i używanie klienta DNS Azure RTOS NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem klienta DNS Azure RTOS NetX.

## <a name="product-distribution"></a>Dystrybucja produktów

Klient DNS NetX jest dostępny w witrynie <https://github.com/azure-rtos/netx> . Pakiet zawiera następujące pliki:

- **nx_dns.h:** plik nagłówka dla klienta DNS NetX
- **nx_dns.c:** plik źródłowy języka C dla klienta DNS NetX
- **nx_dns.pdf:** opis PDF klienta DNS NetX

## <a name="dns-client-installation"></a>Instalacja klienta DNS

Aby użyć klienta DNS NetX, skopiuj pliki kodu źródłowego *nx_dns.c* i *nx_dns.h* do tego samego katalogu, w którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_dns.h* i *nx_dns.c.*

## <a name="using-the-dns-client"></a>Korzystanie z klienta DNS

Korzystanie z klienta DNS NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_dns.h* po dojecheniu do niego plików *tx_api.h* i *nx_api.h,* aby można było używać odpowiednio threadX i NetX. Po *nx_dns.h* kod aplikacji może następnie wykonać wywołania funkcji DNS określone w dalszej części tego przewodnika. Aplikacja musi również dodać *nx_dns.c* do procesu kompilacji. Ten plik musi zostać skompilowany w taki sam sposób, jak inne pliki aplikacji, a jego formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z systemu DNS NetX.

>[!NOTE]
> Ponieważ system DNS korzysta z usług NetX UDP, przed użyciem usługi DNS należy włączyć nx_udp_enable *UDP* za pomocą wywołania protokołu NX_UDP_ENABLE UDP.

## <a name="small-example-system-for-dns-client"></a>Mały przykładowy system klienta DNS 

W przykładowym programie aplikacji DNS, który został podany w tej sekcji, *nx_dns.h* znajduje się w wierszu 6. NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, która umożliwia aplikacji klienckiej DNS tworzenie puli pakietów dla klienta DNS, jest zadeklarowana w wierszach 21–23. Ta pula pakietów służy do przydzielania pakietów do wysyłania komunikatów DNS. Jeśli NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, pula pakietów jest tworzona w wierszach 71–91. Jeśli ta opcja nie jest włączona, klient DNS tworzy własną pulę pakietów zgodnie z ładunkiem pakietu i rozmiarem puli ustawionym przez parametry konfiguracji w pliku *nx_dns.h* i opisanym w innym miejscu w tym rozdziale.

Inna pula pakietów jest tworzona w wierszach 93–105 dla wystąpienia adresu IP klienta, które jest używane do wewnętrznych operacji NetX. Następnie wystąpienie adresu IP jest tworzone przy użyciu *nx_ip_create* w wierszu 107-119. Zadanie IP i klient DNS mogą współużytkować tę samą pulę pakietów, ale ponieważ klient DNS zazwyczaj wysyła większe komunikaty niż pakiety sterujące wysyłane przez zadanie IP, użycie oddzielnych pul pakietów sprawia, że pamięć jest wydajniejsza.

Protokół ARP i UDP (używany przez sieci IPv4) są włączane odpowiednio w wierszach 122 i 134.

>[!NOTE]
> W tej wersji demonstracyjnej użyto sterownika "ram" zadeklarowanej w wierszu 37 i użytej w *wywołaniu nx_ip_create.* Ten sterownik pamięci RAM jest dystrybuowany przy użyciu kodu źródłowego NetX. Aby w rzeczywistości uruchomić klienta DNS, aplikacja musi dostarczyć rzeczywisty fizyczny sterownik sieciowy do przesyłania i odbierania pakietów z serwera DNS.

Funkcja wpisu wątku klienta *thread_client_entry* jest zdefiniowana poniżej *tx_application_define* funkcji. Początkowo wyzejmuje kontrolę nad systemem, aby umożliwić inicjowanie wątku zadania IP przez sterownik sieciowy.

Następnie tworzy klienta DNS w wierszach 176-187, inicjuje pamięć podręczną w wierszach 189-200 i ustawia wcześniej utworzoną pulę pakietów na wystąpienie klienta DNS w wierszach 202–217. Następnie dodaje serwer DNS IPv4 w wierszach 220–229.

Pozostała część przykładowego programu używa usług klienta DNS do zapytań DNS. Wyszukiwania adresów IP hostów są wykonywane w wierszach 240 i 262. Różnica między tymi dwiema  usługami, nx_dns_host_by_name_get i *nx_dns_ipv4_address_by_name_get*, polega na tym, że pierwsza z nich zapisuje tylko jeden adres IP, a druga zapisuje wiele adresów, jeśli serwer DNS odpowiedział.

Wyszukiwania wsteczne (nazwa hosta z adresu IP) są wykonywane w wierszach 354 *(nx_dns_host_by_address_get*).

Dwie kolejne usługi wyszukiwania DNS, CNAME i TXT, są zademonstrowane w wierszach 375 i 420 odpowiednio, aby odnaleźć CNAME i TXT dla nazwy domeny wejściowej. NetX DNS Client jako podobne usługi dla innych typów rekordów, np. NS, MX, SRV i SOA. Zobacz Rozdział 3, aby uzyskać szczegółowe opisy wszystkich odnośników typu rekordu dostępnych w kliencie DNS NetX.

Gdy klient DNS zostanie usunięty w wierszu 594 przy użyciu usługi *nx_dns_delete,* pula pakietów dla klienta DNS nie zostanie usunięta, chyba że klient DNS utworzył własną pulę pakietów. W przeciwnym razie aplikacja będzie usuwać pulę pakietów, jeśli nie będzie dalej jej używać.

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

Istnieje kilka opcji konfiguracji do tworzenia systemu DNS dla NetX. Te opcje można przedefiniować w *nx_dns.h.* Na poniższej liście szczegółowo opisano poszczególne z nich:  

- **NX_DNS_TYPE_OF_SERVICE:** typ usługi wymagany dla żądań protokołu UDP systemu DNS. Domyślnie ta wartość jest definiowana jako wartość NX_IP_NORMAL dla normalnej usługi pakietów IP.

- **NX_DNS_TIME_TO_LIVE:** określa maksymalną liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80

- **NX_DNS_FRAGMENT_OPTION:** ustawia właściwość gniazda, aby zezwalać na fragmentację pakietów wychodzących lub ich nie zezwalać. Wartość domyślna to NX_DONT_FRAGMENT.

- **NX_DNS_QUEUE_DEPTH:** ustawia maksymalną liczbę pakietów do przechowywania w kolejce odbierania gniazd. Wartość domyślna to 5.

- **NX_DNS_MAX_SERVERS:** Określa maksymalną liczbę serwerów DNS na liście Serwer klienta.

- **NX_DNS_MESSAGE_MAX:** maksymalny rozmiar komunikatu DNS do wysyłania zapytań DNS. Wartość domyślna to 512, która jest również maksymalnym rozmiarem określonym w dokumencie RFC 1035 w sekcji 2.3.4.

- **NX_DNS_PACKET_PAYLOAD_UNALIGNED:** jeśli nie zdefiniowano, rozmiar ładunku pakietu klienta, który obejmuje nagłówki Ethernet, IP (lub IPv6) i UDP oraz maksymalny rozmiar komunikatu DNS określony przez NX_DNS_MESSAGE_MAX. Niezależnie od tego, czy pakiet jest zdefiniowany, ładunek pakietu jest wyrównany do 4 bajtów i przechowywany w NX_DNS_PACKET_PAYLOAD.

- **NX_DNS_PACKET_POOL_SIZE:** rozmiar puli pakietów klienta do wysyłania zapytań DNS, NX_DNS_CLIENT_USER_CREATE_PACKET_POOL nie jest zdefiniowany. Wartość domyślna jest wystarczająco duża dla 16 pakietów o rozmiarze ładunku zdefiniowanym przez NX_DNS_PACKET_PAYLOAD i jest wyrównana o 4 bajty.

- **NX_DNS_MAX_RETRIES:** maksymalna liczba zapytań klienta DNS bieżącego serwera DNS przed podjęciem próby innego serwera lub przerwaniem zapytania DNS.

- **NX_DNS_MAX_RETRANS_TIMEOUT:** maksymalny limit czasu retransmisji dla zapytania DNS do określonego serwera DNS. Wartość domyślna to 64 sekundy (64 *NX_IP_PERIODIC_RATE).

- **NX_DNS_IP_GATEWAY_AND_DNS_SERVER:** jeśli zdefiniowano adres bramy IPv4 klienta jest niezerowy, klient DNS ustawia bramę IPv4 jako podstawowy serwer DNS klienta. Wartość domyślna jest wyłączona.

- **NX_DNS_PACKET_ALLOCATE_TIMEOUT:** ustawia opcję limitu czasu przydzielania pakietu z puli pakietów klienta DNS. Wartość domyślna to 1 sekunda (1*NX_IP_PERIODIC_RATE).

- **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL:** umożliwia klientowi DNS utworzenie i ustawienie puli pakietów klienta DNS przez aplikację. Domyślnie ta opcja jest wyłączona, a klient DNS tworzy własną pulę pakietów w nx_dns_create *.*

- **NX_DNS_CLIENT_CLEAR_QUEUE:** umożliwia klientowi DNS wyczyszczenie starych komunikatów DNS z kolejki odbierania przed wysłaniem nowego zapytania. Usunięcie tych pakietów z poprzednich zapytań DNS zapobiega przepełnianie i porzucanie prawidłowych pakietów przez kolejkę gniazd klienta DNS.

- **NX_DNS_ENABLE_EXTENDED_RR_TYPES:** umożliwia klientowi DNS wykonywanie zapytań o dodatkowe typy rekordów DNS w programie (np. CNAME, NS, MX, SOA, SRV i TXT).

- **NX_DNS_CACHE_ENABLE:** umożliwia klientowi DNS przechowywanie rekordów odpowiedzi w pamięci podręcznej DNS.
