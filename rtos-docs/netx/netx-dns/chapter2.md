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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a><span data-ttu-id="b453e-103">Rozdział 2 — Instalowanie i używanie klienta DNS usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="b453e-103">Chapter 2 - Installation and Use of Azure RTOS NetX DNS Client</span></span>

<span data-ttu-id="b453e-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta DNS usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="b453e-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b453e-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="b453e-105">Product Distribution</span></span>

<span data-ttu-id="b453e-106">Klient DNS NetX jest dostępny pod adresem <https://github.com/azure-rtos/netx> .</span><span class="sxs-lookup"><span data-stu-id="b453e-106">The NetX DNS Client is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="b453e-107">Pakiet zawiera następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="b453e-107">The package includes the following files:</span></span>

- <span data-ttu-id="b453e-108">**nx_dns. h**: plik nagłówkowy dla klienta DNS NetX</span><span class="sxs-lookup"><span data-stu-id="b453e-108">**nx_dns.h**: Header file for NetX DNS Client</span></span>
- <span data-ttu-id="b453e-109">plik źródłowy **nx_dns. c**: c dla klienta DNS NetX</span><span class="sxs-lookup"><span data-stu-id="b453e-109">**nx_dns.c**: C Source file for NetX DNS Client</span></span>
- <span data-ttu-id="b453e-110">**nx_dns.pdf**: Opis pliku PDF NetX klienta DNS</span><span class="sxs-lookup"><span data-stu-id="b453e-110">**nx_dns.pdf**: PDF description of NetX DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="b453e-111">Instalacja klienta DNS</span><span class="sxs-lookup"><span data-stu-id="b453e-111">DNS Client Installation</span></span>

<span data-ttu-id="b453e-112">Aby użyć NetX klienta DNS, skopiuj pliki kodu źródłowego *nx_dns. c* i *nx_dns. h* do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="b453e-112">To use NetX DNS Client, copy the source code files *nx_dns.c* and *nx_dns.h* to the same directory where NetX is installed.</span></span> <span data-ttu-id="b453e-113">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_dns. h* i *nx_dns. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b453e-113">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dns.h* and *nx_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="b453e-114">Korzystanie z klienta DNS</span><span class="sxs-lookup"><span data-stu-id="b453e-114">Using the DNS Client</span></span>

<span data-ttu-id="b453e-115">Korzystanie z klienta DNS NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="b453e-115">Using NetX DNS Client is easy.</span></span> <span data-ttu-id="b453e-116">W zasadzie kod aplikacji musi zawierać *nx_dns. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="b453e-116">Basically, the application code must include *nx_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="b453e-117">Po dołączeniu *nx_dns. h* kod aplikacji może następnie wprowadzić wywołania funkcji DNS w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b453e-117">Once *nx_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="b453e-118">Aplikacja musi również dodać *nx_dns. c* do procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b453e-118">The application must also add *nx_dns.c* to the build process.</span></span> <span data-ttu-id="b453e-119">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b453e-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="b453e-120">To wszystko, co jest wymagane do korzystania z usługi NetX DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-120">This is all that is required to use NetX DNS.</span></span>

>[!NOTE]
> <span data-ttu-id="b453e-121">Ponieważ usługa DNS korzysta z usług NetX UDP, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-121">Since DNS utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-dns-client"></a><span data-ttu-id="b453e-122">Mały przykładowy system dla klienta DNS</span><span class="sxs-lookup"><span data-stu-id="b453e-122">Small Example System for DNS Client</span></span> 

<span data-ttu-id="b453e-123">W przykładowym programie aplikacji DNS dostarczonym w tej sekcji *nx_dns. h* jest zawarty w wierszu 6.</span><span class="sxs-lookup"><span data-stu-id="b453e-123">In the example DNS application program provided in this section, *nx_dns.h* is included at line 6.</span></span> <span data-ttu-id="b453e-124">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, co umożliwia aplikacji klienta DNS utworzenie puli pakietów dla klienta DNS, jest zadeklarowana w wierszach 21-23.</span><span class="sxs-lookup"><span data-stu-id="b453e-124">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 21-23.</span></span> <span data-ttu-id="b453e-125">Ta Pula pakietów służy do alokowania pakietów do wysyłania komunikatów DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-125">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="b453e-126">Jeśli zdefiniowano NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, Pula pakietów zostanie utworzona w wierszach 71-91.</span><span class="sxs-lookup"><span data-stu-id="b453e-126">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 71-91.</span></span> <span data-ttu-id="b453e-127">Jeśli ta opcja nie jest włączona, klient DNS tworzy własną pulę pakietów zgodnie z rozmiarem ładunku pakietu i pulą ustawioną przez parametry konfiguracji w *nx_dns. h* i opisany w innym miejscu w tym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="b453e-127">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nx_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="b453e-128">Inna Pula pakietów jest tworzona w wierszach 93-105 dla wystąpienia IP klienta, które jest używane dla wewnętrznych operacji NetX.</span><span class="sxs-lookup"><span data-stu-id="b453e-128">Another packet pool is created in lines 93-105 for the Client IP instance which is used for internal NetX operations.</span></span> <span data-ttu-id="b453e-129">Następne wystąpienie protokołu IP jest tworzone przy użyciu wywołania *nx_ip_create* w wierszu 107-119.</span><span class="sxs-lookup"><span data-stu-id="b453e-129">Next the IP instance is created using the *nx_ip_create* call in line 107-119.</span></span> <span data-ttu-id="b453e-130">Istnieje możliwość, aby zadanie IP i klient DNS mogli współużytkować tę samą pulę pakietów, ale ponieważ klient DNS zazwyczaj wysyła więcej komunikatów niż pakiety sterujące wysyłane przez zadanie IP, używając oddzielnych pul pakietów, co zwiększa efektywność korzystania z pamięci.</span><span class="sxs-lookup"><span data-stu-id="b453e-130">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="b453e-131">Protokoły ARP i UDP (używane przez sieci IPv4) są włączane odpowiednio w wierszach 122 i 134.</span><span class="sxs-lookup"><span data-stu-id="b453e-131">ARP and UDP (which is used by IPv4 networks) are enabled in lines 122 and 134 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="b453e-132">W tej wersji demonstracyjnej użyto sterownika "ram" zadeklarowanego w wierszu 37 i użytego w wywołaniu *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="b453e-132">This demo uses the ‘ram’ driver declared on line 37 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="b453e-133">Ten sterownik pamięci RAM jest dystrybuowany z kodem źródłowym NetX.</span><span class="sxs-lookup"><span data-stu-id="b453e-133">This ram driver is distributed with the NetX source code.</span></span> <span data-ttu-id="b453e-134">Aby w rzeczywistości uruchomić klienta DNS, aplikacja musi dostarczyć rzeczywisty sterownik sieci fizycznej do przesyłania i odbierania pakietów z serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-134">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="b453e-135">Funkcja wpisu wątku klienta *thread_client_entry* jest definiowana poniżej funkcji *tx_application_define* .</span><span class="sxs-lookup"><span data-stu-id="b453e-135">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="b453e-136">Początkowo program zrzeka się kontroli do systemu, aby umożliwić zainicjowanie wątku zadania IP przez sterownik sieciowy.</span><span class="sxs-lookup"><span data-stu-id="b453e-136">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="b453e-137">Następnie tworzy klienta DNS w wierszach 176-187, inicjuje pamięć podręczną w wierszach 189-200 i ustawia pulę pakietów utworzoną wcześniej w wystąpieniu klienta DNS w wierszach 202-217.</span><span class="sxs-lookup"><span data-stu-id="b453e-137">It then creates the DNS Client on lines 176-187, initializes the cache on lines 189-200, and sets the packet pool previously created to the DNS Client instance on lines 202-217.</span></span> <span data-ttu-id="b453e-138">Następnie dodaje serwer DNS IPv4 w wierszach 220-229.</span><span class="sxs-lookup"><span data-stu-id="b453e-138">It then adds an IPv4 DNS server on lines 220-229.</span></span>

<span data-ttu-id="b453e-139">Pozostała część przykładowego programu używa usług klienta DNS do wykonywania zapytań DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-139">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="b453e-140">Wyszukiwania adresów IP hosta są wykonywane w wierszach 240 i 262.</span><span class="sxs-lookup"><span data-stu-id="b453e-140">Host IP address lookups are performed on lines 240 and 262.</span></span> <span data-ttu-id="b453e-141">Różnica między tymi dwoma usługami, *nx_dns_host_by_name_get* i *nx_dns_ipv4_address_by_name_get*, polega na tym, że pierwsza tylko zapisuje jeden adres IP, podczas gdy serwer DNS odpowiedział na wiele adresów.</span><span class="sxs-lookup"><span data-stu-id="b453e-141">The difference between these two services, *nx_dns_host_by_name_get* and *nx_dns_ipv4_address_by_name_get*, is that the former only saves one IP address, while the latter saves multiple addresses if DNS Server replied.</span></span>

<span data-ttu-id="b453e-142">Wyszukiwania wsteczne (nazwa hosta na podstawie adresu IP) są wykonywane w wierszach 354 (*nx_dns_host_by_address_get*).</span><span class="sxs-lookup"><span data-stu-id="b453e-142">Reverse lookups (host name from IP address) are performed on lines 354 (*nx_dns_host_by_address_get*).</span></span>

<span data-ttu-id="b453e-143">Dwie więcej usług dla wyszukiwania DNS, CNAME i TXT są odpowiednio przedstawiane w wierszach 375 i 420, aby odnaleźć CNAME i TXT dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="b453e-143">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 375 and 420 respectively, to discover CNAME and TXT for the input domain name.</span></span> <span data-ttu-id="b453e-144">NetX klienta DNS jako podobne usługi dla innych typów rekordów, np. NS, MX, SRV i SOA.</span><span class="sxs-lookup"><span data-stu-id="b453e-144">NetX DNS Client as similar services for other record types, e.g. NS, MX, SRV and SOA.</span></span> <span data-ttu-id="b453e-145">Zobacz rozdział 3, aby uzyskać szczegółowe opisy wszystkich wyszukiwań typu rekordu dostępnych w NetX DNS Client.</span><span class="sxs-lookup"><span data-stu-id="b453e-145">See Chapter 3 for detailed descriptions of all record type lookups available in NetX DNS Client.</span></span>

<span data-ttu-id="b453e-146">Po usunięciu klienta DNS w wierszu 594 przy użyciu usługi *nx_dns_delete* Pula pakietów dla klienta DNS nie zostanie usunięta, chyba że klient DNS utworzył własną pulę pakietów.</span><span class="sxs-lookup"><span data-stu-id="b453e-146">When the DNS Client is deleted on line 594, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="b453e-147">W przeciwnym razie aplikacja może usunąć pulę pakietów, jeśli nie ma do niej zastosowania.</span><span class="sxs-lookup"><span data-stu-id="b453e-147">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

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

## <a name="configuration-options"></a><span data-ttu-id="b453e-148">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b453e-148">Configuration Options</span></span>

<span data-ttu-id="b453e-149">Istnieje kilka opcji konfiguracji do kompilowania systemu DNS dla NetX.</span><span class="sxs-lookup"><span data-stu-id="b453e-149">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="b453e-150">Te opcje można ponownie zdefiniować w *nx_dns. h.*</span><span class="sxs-lookup"><span data-stu-id="b453e-150">These options can be redefined in *nx_dns.h.*</span></span> <span data-ttu-id="b453e-151">Poniższa lista zawiera szczegółowy opis:</span><span class="sxs-lookup"><span data-stu-id="b453e-151">The following list describes each in detail:</span></span>  

- <span data-ttu-id="b453e-152">**NX_DNS_TYPE_OF_SERVICE**: typ usługi wymaganej przez żądania UDP DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-152">**NX_DNS_TYPE_OF_SERVICE**: Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="b453e-153">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL dla normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="b453e-153">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="b453e-154">**NX_DNS_TIME_TO_LIVE**: określa maksymalną liczbę routerów, jaką może przekazać pakiet, zanim zostanie on odrzucony.</span><span class="sxs-lookup"><span data-stu-id="b453e-154">**NX_DNS_TIME_TO_LIVE**: Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="b453e-155">Wartość domyślna to 0x80</span><span class="sxs-lookup"><span data-stu-id="b453e-155">The default value is 0x80</span></span>

- <span data-ttu-id="b453e-156">**NX_DNS_FRAGMENT_OPTION**: ustawia właściwość gniazda, aby zezwalać na fragmentację pakietów wychodzących lub go nie zezwalać.</span><span class="sxs-lookup"><span data-stu-id="b453e-156">**NX_DNS_FRAGMENT_OPTION**: Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="b453e-157">Wartość domyślna to NX_DONT_FRAGMENT.</span><span class="sxs-lookup"><span data-stu-id="b453e-157">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="b453e-158">**NX_DNS_QUEUE_DEPTH**: ustawia maksymalną liczbę pakietów do zapisania w kolejce odbioru gniazda.</span><span class="sxs-lookup"><span data-stu-id="b453e-158">**NX_DNS_QUEUE_DEPTH**: Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="b453e-159">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="b453e-159">The default value is 5.</span></span>

- <span data-ttu-id="b453e-160">**NX_DNS_MAX_SERVERS**: określa maksymalną liczbę serwerów DNS na liście serwerów klienta.</span><span class="sxs-lookup"><span data-stu-id="b453e-160">**NX_DNS_MAX_SERVERS**: Specifies the maximum number of DNS Servers in the Client server list.</span></span>

- <span data-ttu-id="b453e-161">**NX_DNS_MESSAGE_MAX**: maksymalny rozmiar komunikatu DNS na potrzeby wysyłania zapytań DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-161">**NX_DNS_MESSAGE_MAX**: The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="b453e-162">Wartość domyślna to 512, który jest również maksymalnym rozmiarem określonym w dokumencie RFC 1035 sekcja 2.3.4.</span><span class="sxs-lookup"><span data-stu-id="b453e-162">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="b453e-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: Jeśli nie zostanie zdefiniowany, rozmiar ładunku pakietu klienta, który zawiera nagłówki Ethernet, IP (lub IPv6) i UDP, oraz maksymalny rozmiar komunikatu DNS określony przez NX_DNS_MESSAGE_MAX.</span><span class="sxs-lookup"><span data-stu-id="b453e-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="b453e-164">Niezależnie od tego, czy jest zdefiniowany, ładunek pakietu jest wyrównany 4-bajtowy i przechowywany w NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="b453e-164">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="b453e-165">**NX_DNS_PACKET_POOL_SIZE**: rozmiar puli pakietów klienta na potrzeby wysyłania zapytań DNS, jeśli nie określono NX_DNS_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="b453e-165">**NX_DNS_PACKET_POOL_SIZE**: Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="b453e-166">Wartość domyślna jest wystarczająco duża dla 16 pakietów o rozmiarze ładunku zdefiniowanym przez NX_DNS_PACKET_PAYLOAD i ma 4-bajtowe wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="b453e-166">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="b453e-167">**NX_DNS_MAX_RETRIES**: Maksymalna liczba przypadków, gdy klient DNS wyśle zapytanie do bieżącego serwera DNS przed podjęciem próby innego serwera lub przerwaniem zapytania DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-167">**NX_DNS_MAX_RETRIES**: The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span>

- <span data-ttu-id="b453e-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: maksymalny limit czasu retransmisji dla zapytania DNS do określonego serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="b453e-169">Wartość domyślna to 64 sekund (64 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="b453e-169">The default value is 64 seconds (64 \*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="b453e-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: Jeśli jest zdefiniowany, a adres bramy IPv4 klienta jest różny od zera, klient DNS ustawia bramę IPv4 jako podstawowy serwer DNS klienta.</span><span class="sxs-lookup"><span data-stu-id="b453e-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="b453e-171">Wartość domyślna jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="b453e-171">The default value is disabled.</span></span>

- <span data-ttu-id="b453e-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: ustawia opcję limitu czasu dla przydzielania pakietu z puli pakietów klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="b453e-173">Wartość domyślna to 1 sekunda (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="b453e-173">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="b453e-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: pozwala klientowi DNS zezwolić aplikacji na tworzenie i Ustawianie puli pakietów klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="b453e-175">Domyślnie ta opcja jest wyłączona, a klient DNS tworzy własną pulę pakietów w *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="b453e-175">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="b453e-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: umożliwia klientowi DNS czyszczenie starych komunikatów DNS z kolejki odbierania przed wysłaniem nowej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="b453e-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="b453e-177">Usunięcie tych pakietów z poprzednich zapytań DNS uniemożliwia kolejkowanie gniazda klienta DNS z przepełniania i usuwania prawidłowych pakietów.</span><span class="sxs-lookup"><span data-stu-id="b453e-177">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="b453e-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: Dzięki temu Klient DNS może wysyłać zapytania dotyczące dodatkowych typów rekordów DNS w (np. CNAME, NS, MX, SOA, SRV i txt).</span><span class="sxs-lookup"><span data-stu-id="b453e-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="b453e-179">**NX_DNS_CACHE_ENABLE**: umożliwia klientowi DNS przechowywanie rekordów odpowiedzi w pamięci podręcznej DNS.</span><span class="sxs-lookup"><span data-stu-id="b453e-179">**NX_DNS_CACHE_ENABLE**: This enables the DNS Client to store the answer records into DNS cache.</span></span>
