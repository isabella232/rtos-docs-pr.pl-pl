---
title: Rozdział 2 — Instalowanie i używanie klienta DNS usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta DNS platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b85829f80462015d66e1623b880d5139349ce0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822903"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dns-client"></a><span data-ttu-id="56485-103">Rozdział 2 — Instalowanie i używanie klienta DNS usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="56485-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo DNS Client</span></span>

<span data-ttu-id="56485-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta DNS platformy Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="56485-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="56485-105">Product Distribution</span></span>

<span data-ttu-id="56485-106">Klient DNS NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="56485-106">NetX Duo DNS Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="56485-107">Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="56485-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="56485-108">**nxd_dns. h** Plik nagłówka dla klienta DNS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="56485-108">**nxd_dns.h** Header file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="56485-109">**nxd_dns. c** Plik źródłowy języka C dla klienta DNS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="56485-109">**nxd_dns.c** C Source file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="56485-110">**nxd_dns.pdf** Opis pliku PDF klienta DNS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="56485-110">**nxd_dns.pdf** PDF description of NetX Duo DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="56485-111">Instalacja klienta DNS</span><span class="sxs-lookup"><span data-stu-id="56485-111">DNS Client Installation</span></span>

<span data-ttu-id="56485-112">Aby użyć klienta DNS NetX Duo, skopiuj pliki kodu źródłowego *nxd_dns. c* i *nxd_dns. h* do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-112">To use NetX Duo DNS Client, copy the source code files *nxd_dns.c* and *nxd_dns.h* to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="56485-113">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_dns. h* i *nxd_dns. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="56485-113">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dns.h* and *nxd_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="56485-114">Korzystanie z klienta DNS</span><span class="sxs-lookup"><span data-stu-id="56485-114">Using the DNS Client</span></span>

<span data-ttu-id="56485-115">Korzystanie z klienta DNS NetX Duo jest proste.</span><span class="sxs-lookup"><span data-stu-id="56485-115">Using NetX Duo DNS Client is easy.</span></span> <span data-ttu-id="56485-116">Zasadniczo kod aplikacji musi zawierać *nxd_dns. h* , po uwzględnieniu *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-116">Basically, the application code must include *nxd_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="56485-117">Po dołączeniu *nxd_dns. h* kod aplikacji może następnie wprowadzić wywołania funkcji DNS w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="56485-117">Once *nxd_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="56485-118">Aplikacja musi również dodać *nxd_dns. c* do procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="56485-118">The application must also add *nxd_dns.c* to the build process.</span></span> <span data-ttu-id="56485-119">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56485-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="56485-120">To wszystko, co jest wymagane do korzystania z usługi DNS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-120">This is all that is required to use NetX Duo DNS.</span></span>

> [!NOTE]
> <span data-ttu-id="56485-121">Ponieważ usługa DNS korzysta z usług UDP NetX Duo, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-121">Since DNS utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-netx-duo-dns-client"></a><span data-ttu-id="56485-122">Mały przykładowy system dla klienta DNS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="56485-122">Small Example System for NetX Duo DNS Client</span></span> 

<span data-ttu-id="56485-123">Klient DNS NetX Duo jest zgodny z istniejącymi aplikacjami DNS NetX.</span><span class="sxs-lookup"><span data-stu-id="56485-123">NetX Duo DNS Client is compatible with existing NetX DNS applications.</span></span> <span data-ttu-id="56485-124">Poniżej przedstawiono listę starszych usług i ich odpowiednik NetX Duo:</span><span class="sxs-lookup"><span data-stu-id="56485-124">The list of legacy services and their NetX Duo equivalent is shown below:</span></span>

| <span data-ttu-id="56485-125">Usługa API NetX DNS (tylko IPv4)</span><span class="sxs-lookup"><span data-stu-id="56485-125">NetX DNS API service (IPv4 only)</span></span> | <span data-ttu-id="56485-126">Usługa interfejsu API DNS NetX Duo (obsługiwana obsługa adresów IPv4 i IPv6)</span><span class="sxs-lookup"><span data-stu-id="56485-126">NetX Duo DNS API service (IPv4 and IPv6 supported)</span></span> |
|----------------------------------|----------------------------------------------------|
| <span data-ttu-id="56485-127">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="56485-127">nx_dns_host_by_name_get</span></span>          | <span data-ttu-id="56485-128">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="56485-128">nxd_dns_host_by_name_get</span></span>                           |
| <span data-ttu-id="56485-129">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="56485-129">nx_dns_host_by_address_get</span></span>       | <span data-ttu-id="56485-130">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="56485-130">nxd_dns_host_by_address_get</span></span>                        |
| <span data-ttu-id="56485-131">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="56485-131">nx_dns_server_get</span></span>                | <span data-ttu-id="56485-132">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="56485-132">nxd_dns_server_get</span></span>                                 |
| <span data-ttu-id="56485-133">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="56485-133">nx_dns_server_add</span></span>                | <span data-ttu-id="56485-134">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="56485-134">nxd_dns_server_add</span></span>                                 |
| <span data-ttu-id="56485-135">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="56485-135">nx_dns_server_remove</span></span>             | <span data-ttu-id="56485-136">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="56485-136">nxd_dns_server_remove</span></span>                              |

<span data-ttu-id="56485-137">Aby uzyskać więcej informacji, zobacz Opis usług API klienta DNS NetX Duo w rozdziale 3.</span><span class="sxs-lookup"><span data-stu-id="56485-137">See the description of NetX Duo DNS Client API services in Chapter 3 for more details.</span></span>

<span data-ttu-id="56485-138">W przykładowym programie aplikacji DNS dostarczonym w tej sekcji *nxd_dns. h* jest zawarty w wierszu 6.</span><span class="sxs-lookup"><span data-stu-id="56485-138">In the example DNS application program provided in this section, *nxd_dns.h* is included at line 6.</span></span> <span data-ttu-id="56485-139">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, co umożliwia aplikacji klienta DNS utworzenie puli pakietów dla klienta DNS, jest zadeklarowana w wierszach 24-26.</span><span class="sxs-lookup"><span data-stu-id="56485-139">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 24-26.</span></span> <span data-ttu-id="56485-140">Ta Pula pakietów służy do alokowania pakietów do wysyłania komunikatów DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-140">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="56485-141">Jeśli zdefiniowano NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, Pula pakietów zostanie utworzona w wierszach 78-98.</span><span class="sxs-lookup"><span data-stu-id="56485-141">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 78-98.</span></span> <span data-ttu-id="56485-142">Jeśli ta opcja nie jest włączona, klient DNS tworzy własną pulę pakietów zgodnie z rozmiarem ładunku pakietu i pulą ustawioną przez parametry konfiguracji w *nxd_dns. h* i opisany w innym miejscu w tym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="56485-142">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nxd_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="56485-143">Inna Pula pakietów jest tworzona w wierszach 100-112 dla wystąpienia IP klienta, które jest używane dla wewnętrznych operacji NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-143">Another packet pool is created in lines 100-112 for the Client IP instance which is used for internal NetX Duo operations.</span></span> <span data-ttu-id="56485-144">Następne wystąpienie protokołu IP jest tworzone przy użyciu wywołania *nx_ip_create* w wierszu 115.</span><span class="sxs-lookup"><span data-stu-id="56485-144">Next the IP instance is created using the *nx_ip_create* call in line 115.</span></span> <span data-ttu-id="56485-145">Istnieje możliwość, aby zadanie IP i klient DNS mogli współużytkować tę samą pulę pakietów, ale ponieważ klient DNS zazwyczaj wysyła więcej komunikatów niż pakiety sterujące wysyłane przez zadanie IP, używając oddzielnych pul pakietów, co zwiększa efektywność korzystania z pamięci.</span><span class="sxs-lookup"><span data-stu-id="56485-145">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="56485-146">Protokoły ARP i UDP (używane przez sieci IPv4) są włączane odpowiednio w wierszach 129 i 141.</span><span class="sxs-lookup"><span data-stu-id="56485-146">ARP and UDP (which is used by IPv4 networks) are enabled in lines 129 and 141 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="56485-147">W tej wersji demonstracyjnej użyto sterownika "ram" zadeklarowanego w wierszu 44 i użytego w wywołaniu *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="56485-147">This demo uses the ‘ram’ driver declared on line 44 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="56485-148">Ten sterownik pamięci RAM jest dystrybuowany z kodem źródłowym NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-148">This ram driver is distributed with the NetX Duo source code.</span></span> <span data-ttu-id="56485-149">Aby w rzeczywistości uruchomić klienta DNS, aplikacja musi dostarczyć rzeczywisty sterownik sieci fizycznej do przesyłania i odbierania pakietów z serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-149">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="56485-150">Funkcja wpisu wątku klienta *thread_client_entry* jest definiowana poniżej funkcji *tx_application_define* .</span><span class="sxs-lookup"><span data-stu-id="56485-150">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="56485-151">Początkowo program zrzeka się kontroli do systemu, aby umożliwić zainicjowanie wątku zadania IP przez sterownik sieciowy.</span><span class="sxs-lookup"><span data-stu-id="56485-151">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="56485-152">Następnie tworzy klienta DNS w wierszu 257, inicjuje pamięć podręczną DNS w wierszach 267-278 i ustawia pulę pakietów utworzoną wcześniej w wystąpieniu klienta DNS w wierszach 281-295.</span><span class="sxs-lookup"><span data-stu-id="56485-152">It then creates the DNS Client in line 257, initializes the DNS cache on lines 267- 278, and sets the packet pool previously created to the DNS Client instance on lines 281-295.</span></span> <span data-ttu-id="56485-153">Następnie dodaje serwer DNS w wierszach 297-341.</span><span class="sxs-lookup"><span data-stu-id="56485-153">It then adds DNS server on lines 297-341.</span></span>

<span data-ttu-id="56485-154">Pozostała część przykładowego programu używa usług klienta DNS do wykonywania zapytań DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-154">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="56485-155">Wyszukiwania adresów IP hosta są wykonywane w wierszach 193 i 207.</span><span class="sxs-lookup"><span data-stu-id="56485-155">Host IP address lookups are performed on lines 193 and 207.</span></span> <span data-ttu-id="56485-156">Różnica między tymi dwoma usługami, *nxd_dns_host_by_name_get* i *nx_dns_host_by_name_get*, polega na tym, że dawniej zapisuje dane adresu w NXD_ADDRESS typie danych, podczas gdy zapisuje dane w tym samym typie danych ulong.</span><span class="sxs-lookup"><span data-stu-id="56485-156">The difference between these two services, *nxd_dns_host_by_name_get* and *nx_dns_host_by_name_get*, is that the former saves the address data in an NXD_ADDRESS data type, while the latter saves the data in a ULONG data type.</span></span> <span data-ttu-id="56485-157">Druga z nich jest ograniczona do sieci IPv4, podczas gdy ta usługa może być używana z sieciami IPv6 i IPv4.</span><span class="sxs-lookup"><span data-stu-id="56485-157">Further the latter is limited to IPv4 networks, while the former can be used with IPv6 or IPv4 networks.</span></span> <span data-ttu-id="56485-158">Jest to możliwe tylko wtedy, gdy dla danego wystąpienia IP włączono obsługę protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="56485-158">This is only possible if the IP instance is enabled for IPv6.</span></span> <span data-ttu-id="56485-159">Zobacz Podręcznik użytkownika programu NetX Duo, aby uzyskać więcej informacji na temat włączania wystąpienia IP dla sieci IPv6.</span><span class="sxs-lookup"><span data-stu-id="56485-159">See the NetX Duo User Guide for more details on enabling the IP instance for IPv6 networking.</span></span>

<span data-ttu-id="56485-160">Inna usługa wyszukiwania adresów IP hosta jest wyświetlana w wierszu 464, *nx_dns_ipv4_address_by_name_get*.</span><span class="sxs-lookup"><span data-stu-id="56485-160">Another service for host IP address lookups is shown on line 464, *nx_dns_ipv4_address_by_name_get*.</span></span> <span data-ttu-id="56485-161">Ta usługa różni się od *nx_dns_host_by_name_get* , że zwraca wszystkie (lub tyle, ile będzie pasować do podanego buforu) adresów IPv4 odnalezionych dla nazwy domeny, a nie tylko pierwszego adresu otrzymanego w odpowiedzi serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-161">This service differs from *nx_dns_host_by_name_get* in that it returns all (or as many will fit in the supplied buffer) of the IPv4 addresses discovered for the domain name, not just the first address received in the DNS Server reply.</span></span>

<span data-ttu-id="56485-162">Podobnie usługa *nxd_dns_ipv6_address_by_name_get* wywołana w wierszu 380 zwraca wszystkie adresy IPv6 wykryte przez klienta DNS, a nie tylko pierwszy z nich.</span><span class="sxs-lookup"><span data-stu-id="56485-162">Similarly, the *nxd_dns_ipv6_address_by_name_get* service, called on line 380, returns all the IPv6 addresses discovered by the DNS Client, not just the first one.</span></span>

<span data-ttu-id="56485-163">Wyszukiwania wsteczne (nazwa hosta na podstawie adresu IP) są wykonywane w wierszach 606 (*nx_dns_host_by_address_get*) i ponownie w wierszu 564 i 588 (*nxd_dns_host_by_address_get*).</span><span class="sxs-lookup"><span data-stu-id="56485-163">Reverse lookups (host name from IP address) are performed on lines 606 (*nx_dns_host_by_address_get*) and again on line 564 and 588 (*nxd_dns_host_by_address_get*).</span></span> <span data-ttu-id="56485-164">*nx_dns_host_by_address_get* będzie działała tylko w sieciach IPv4, podczas gdy *nxd_dns_host_by_address_get* będzie działała w sieciach IPv4 lub IPv6 (np. dla tego wystąpienia IP włączono obsługę protokołu IPv6 oraz sieci IPv4).</span><span class="sxs-lookup"><span data-stu-id="56485-164">*nx_dns_host_by_address_get* will only work on IPv4 networks, while *nxd_dns_host_by_address_get* will work on either IPv4 or IPv6 networks (e.g. the IP instance is enabled for IPv6 as well as IPv4 networks).</span></span>

<span data-ttu-id="56485-165">Dwie więcej usług dla wyszukiwania DNS, CNAME i TXT są odpowiednio przedstawiane w wierszach 627 i 649, aby odnaleźć dane CNAME i nazwy domeny dla nazwy domeny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="56485-165">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 627 and 649 respectively, to discover CNAME and domain name data for the input domain name.</span></span> <span data-ttu-id="56485-166">Klient DNS NetX Duo jako podobne usługi dla innych typów rekordów, np. MX, NS, SRV i SOA.</span><span class="sxs-lookup"><span data-stu-id="56485-166">NetX Duo DNS Client as similar services for other record types, e.g. MX, NS, SRV and SOA.</span></span> <span data-ttu-id="56485-167">Zobacz rozdział 3, aby uzyskać szczegółowe opisy wszystkich wyszukiwań typu rekordu dostępnych w kliencie DNS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="56485-167">See Chapter 3 for detailed descriptions of all record type lookups available in NetX Duo DNS Client.</span></span>

<span data-ttu-id="56485-168">Po usunięciu klienta DNS w wierszu 846 przy użyciu usługi *nx_dns_delete* Pula pakietów dla klienta DNS nie zostanie usunięta, chyba że klient DNS utworzył własną pulę pakietów.</span><span class="sxs-lookup"><span data-stu-id="56485-168">When the DNS Client is deleted on line 846, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="56485-169">W przeciwnym razie aplikacja może usunąć pulę pakietów, jeśli nie ma do niej zastosowania.</span><span class="sxs-lookup"><span data-stu-id="56485-169">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```C
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack. */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_udp.h"
#include   "nxd_dns.h"

#ifdef FEATURE_NX_IPV6
#include   "nx_ipv6.h"
#endif

#define     DEMO_STACK_SIZE         4096

#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS                  client_dns;
TX_THREAD               client_thread;
NX_IP                   client_ip;
NX_PACKET_POOL          main_pool;
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
NX_PACKET_POOL          client_pool;
#endif
UCHAR                   local_cache[LOCAL_CACHE_SIZE];

UINT                    error_counter = 0;

#ifdef FEATURE_NX_IPV6
/* If IPv6 is enabled in NetX Duo, allow DNS Client to try using IPv6 */
//#define USE_IPV6
#endif

#define CLIENT_ADDRESS      IP_ADDRESS(192,168,0,11)
#define DNS_SERVER_ADDRESS  IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */

void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern  VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", thread_client_entry, 0,
            pointer, DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Create the packet pool for the DNS Client to send packets.

        If the DNS Client is configured for letting the host application create
        the DNS packet pool, (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see
       nx_dns_create() for guidelines on packet payload size and pool size.
       packet traffic for NetX processes.
    */
    status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", NX_DNS_PACKET_PAYLOAD, pointer, NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
     /* Create the packet pool which the IP task will use to send packets. Also available to the host
       application to send packet. */
    status =  nx_packet_pool_create(&main_pool, "Main Packet Pool", NX_PACKET_PAYLOAD, pointer, NX_PACKET_POOL_SIZE);

    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                          &main_pool, _nx_ram_network_driver, pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable UDP traffic because DNS is a UDP based protocol. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
}

#define BUFFER_SIZE     200
#define RECORD_COUNT    10

/* Define the Client thread. */

void    thread_client_entry(ULONG thread_input)
{

UCHAR           record_buffer[200];
UINT            record_count;
UINT            status;
ULONG           host_ip_address;
#ifdef FEATURE_NX_IPV6
NXD_ADDRESS     host_ipduo_address;
NXD_ADDRESS     test_ipduo_server_address;
#ifdef USE_IPV6
NXD_ADDRESS     client_ipv6_address;
NXD_ADDRESS     dns_ipv6_server_address;
UINT            iface_index, address_index;
#endif
#endif
UINT            i;
ULONG           *ipv4_address_ptr[RECORD_COUNT];
NX_DNS_IPV6_ADDRESS
                *ipv6_address_ptr[RECORD_COUNT];
#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
NX_DNS_NS_ENTRY
                *nx_dns_ns_entry_ptr[RECORD_COUNT];
NX_DNS_MX_ENTRY
                *nx_dns_mx_entry_ptr[RECORD_COUNT];
NX_DNS_SRV_ENTRY
                *nx_dns_srv_entry_ptr[RECORD_COUNT];
NX_DNS_SOA_ENTRY
                *nx_dns_soa_entry_ptr;
ULONG           host_address;
USHORT          host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Make the DNS Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
    status = nxd_icmp_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
    }

    client_ipv6_address.nxd_ip_address.v6[3] = 0x101;
    client_ipv6_address.nxd_ip_address.v6[2] = 0x0;
    client_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;


     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ipv6_address, 64, &address_index);

    /* Check for global address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);
#endif
#endif

    /* Create a DNS instance for the Client. Note this function will create
       the DNS Client packet pool for creating DNS message packets intended
       for querying its DNS server. */
    status =  nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

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

    /* Yes, use the packet pool created above which has appropriate payload size
       for DNS messages. */
     status = nx_dns_packet_pool_set(&client_dns, &client_pool);

     /* Check for set DNS packet pool error. */
     if (status)
     {

         error_counter++;
         return;
      }

#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Add an IPv6 DNS server to the DNS client. */
    dns_ipv6_server_address.nxd_ip_address.v6[3] = 0x106;
    dns_ipv6_server_address.nxd_ip_address.v6[2] = 0x0;
    dns_ipv6_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    dns_ipv6_server_address.nxd_ip_address.v6[0] = 0x20010db8;
    dns_ipv6_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    status = nxd_dns_server_add(&client_dns, &dns_ipv6_server_address);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif


/********************************************************************************/
/*                                  Type AAAA                                   */
/*     Send AAAA type DNS Query to its DNS server and get the IPv6 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6

    /* Send a DNS Client name query. Indicate the Client expects an IPv6 address (containing an AAAA record). The DNS
       Client will send AAAA type query to its DNS server. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V6);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: \n");

        printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n",
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
    }

#endif

    /* Look up IPv6 addresses(AAAA TYPE) to record multiple IPv6 addresses in record_buffer and return the IPv6 address count. */
    status = nxd_dns_ipv6_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv6_address_ptr[i] = (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS));

        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i,
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF));
    }


/********************************************************************************/
/*                                  Type A                                      */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6
    /* Send a DNS Client name query. Indicate the Client expects an IPv4 address (containing an A record). If the DNS client
       is using an IPv6 DNS server it will send this query over IPv6; otherwise it will be sent over IPv4. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V4);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
              host_ipduo_address.nxd_ip_address.v4 >> 24,
              host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 & 0xFF);
    }

#endif

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
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
/*                                  Type A + CNAME response                     */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
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

        printf("------------------------------------------------------\n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
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
/*                                  Type PTR                                    */
/*       Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

#ifdef FEATURE_NX_IPV6

    /* Look up a host name from an IPv6 address (reverse lookup). */

    /* Create an IPv6 address for a reverse lookup. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V6;
    test_ipduo_server_address.nxd_ip_address.v6[0] = 0x24046800;
    test_ipduo_server_address.nxd_ip_address.v6[1] = 0x40050c00;
    test_ipduo_server_address.nxd_ip_address.v6[2] = 0x00000000;
    test_ipduo_server_address.nxd_ip_address.v6[3] = 0x00000065;

    /* This will be sent over IPv6 to the DNS server who should return a PTR record if it can find the information. */
    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

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
#endif

#ifdef FEATURE_NX_IPV6

    /* Create an IPv4 address for the reverse lookup. If the DNS client is IPv6 enabled, it will send this over
       IPv6 to the DNS server; otherwise it will send it over IPv4. In either case the respective server will
       return a PTR record if it has the information. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V4;
    test_ipduo_server_address.nxd_ip_address.v4 = IP_ADDRESS(74, 125, 71, 106);

    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

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
#endif

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
        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/*                                  Type CNAME                                  */
/*   Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

     /* Send CNAME type to record the canonical name of host in record_buffer. */
     status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test CNAME: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type TXT                                    */
/*      Send TXT type DNS Query to its DNS server and get descriptive text. */
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

        printf("------------------------------------------------------\n");
        printf("Test TXT: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type NS                                     */
/*   Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

     /* Send NS type to record multiple name servers in record_buffer and return the name server count.
        If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */
     status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type MX                                     */
/*   Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

     /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count.
        If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */
     status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
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
/*                                  Type SRV                                    */
/*  Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

     /* Send SRV DNS query type to record the location of services in record_buffer and return count.
        If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */
     status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
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
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_address, &host_port, 200);

    /* Check for DNS add server error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }

/********************************************************************************/
/*                                  Type SOA                                    */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

     /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */
     status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

     /* Get the loc*/
     nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
     printf("------------------------------------------------------\n");
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
## <a name="configuration-options"></a><span data-ttu-id="56485-170">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="56485-170">Configuration Options</span></span>

<span data-ttu-id="56485-171">Istnieje kilka opcji konfiguracji do kompilowania systemu DNS dla NetX.</span><span class="sxs-lookup"><span data-stu-id="56485-171">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="56485-172">Te opcje można ponownie zdefiniować w *nxd_dns. h.*</span><span class="sxs-lookup"><span data-stu-id="56485-172">These options can be redefined in *nxd_dns.h.*</span></span> <span data-ttu-id="56485-173">Poniższa lista zawiera szczegółowy opis:</span><span class="sxs-lookup"><span data-stu-id="56485-173">The following list describes each in detail:</span></span>  

- <span data-ttu-id="56485-174">**NX_DNS_TYPE_OF_SERVICE** Typ usługi wymagany dla żądań UDP DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-174">**NX_DNS_TYPE_OF_SERVICE** Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="56485-175">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL dla normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="56485-175">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="56485-176">**NX_DNS_TIME_TO_LIVE** Określa maksymalną liczbę routerów, jaką może przekazać pakiet, zanim zostanie on odrzucony.</span><span class="sxs-lookup"><span data-stu-id="56485-176">**NX_DNS_TIME_TO_LIVE** Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="56485-177">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="56485-177">The default value is 0x80.</span></span>

- <span data-ttu-id="56485-178">**NX_DNS_FRAGMENT_OPTION** Ustawia właściwość gniazda na wartość Zezwalaj lub nie Zezwalaj na fragmentację pakietów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="56485-178">**NX_DNS_FRAGMENT_OPTION** Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="56485-179">Wartość domyślna to NX_DONT_FRAGMENT.</span><span class="sxs-lookup"><span data-stu-id="56485-179">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="56485-180">**NX_DNS_QUEUE_DEPTH** Ustawia maksymalną liczbę pakietów do przechowywania w kolejce odbioru gniazda.</span><span class="sxs-lookup"><span data-stu-id="56485-180">**NX_DNS_QUEUE_DEPTH** Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="56485-181">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="56485-181">The default value is 5.</span></span>

- <span data-ttu-id="56485-182">**NX_DNS_MAX_SERVERS** Określa maksymalną liczbę serwerów DNS na liście serwerów klienta.</span><span class="sxs-lookup"><span data-stu-id="56485-182">**NX_DNS_MAX_SERVERS** Specifies the maximum number of DNS Servers in the Client server list.</span></span> <span data-ttu-id="56485-183">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="56485-183">The default value is 5.</span></span>

- <span data-ttu-id="56485-184">**NX_DNS_MESSAGE_MAX** Maksymalny rozmiar komunikatu DNS na potrzeby wysyłania zapytań DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-184">**NX_DNS_MESSAGE_MAX** The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="56485-185">Wartość domyślna to 512, który jest również maksymalnym rozmiarem określonym w dokumencie RFC 1035 sekcja 2.3.4.</span><span class="sxs-lookup"><span data-stu-id="56485-185">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="56485-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** Jeśli nie jest zdefiniowany, rozmiar ładunku pakietu klienta, który zawiera nagłówki Ethernet, IP (lub IPv6) i UDP oraz maksymalny rozmiar komunikatu DNS określony przez NX_DNS_MESSAGE_MAX.</span><span class="sxs-lookup"><span data-stu-id="56485-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="56485-187">Niezależnie od tego, czy jest zdefiniowany, ładunek pakietu jest wyrównany 4-bajtowy i przechowywany w NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="56485-187">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="56485-188">**NX_DNS_PACKET_POOL_SIZE** Rozmiar puli pakietów klienta na potrzeby wysyłania zapytań DNS, jeśli nie zdefiniowano NX_DNS_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="56485-188">**NX_DNS_PACKET_POOL_SIZE** Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="56485-189">Wartość domyślna jest wystarczająco duża dla 16 pakietów o rozmiarze ładunku zdefiniowanym przez NX_DNS_PACKET_PAYLOAD i ma 4-bajtowe wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="56485-189">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="56485-190">**NX_DNS_MAX_RETRIES** Maksymalna liczba przeszukiwania przez klienta DNS bieżącego serwera DNS przed podjęciem próby innego serwera lub przerwaniem zapytania DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-190">**NX_DNS_MAX_RETRIES** The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span> <span data-ttu-id="56485-191">Wartość domyślna to 3.</span><span class="sxs-lookup"><span data-stu-id="56485-191">The default value is 3.</span></span>

- <span data-ttu-id="56485-192">**NX_DNS_MAX_RETRANS_TIMEOUT** Maksymalny limit czasu retransmisji dla zapytania DNS do określonego serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-192">**NX_DNS_MAX_RETRANS_TIMEOUT** The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="56485-193">Wartość domyślna to 64 sekund (64 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="56485-193">The default value is 64 seconds (64 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="56485-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** Jeśli zdefiniowane, a adres bramy IPv4 klienta jest różny od zera, klient DNS ustawia bramę IPv4 jako podstawowy serwer DNS klienta.</span><span class="sxs-lookup"><span data-stu-id="56485-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="56485-195">Wartość domyślna jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="56485-195">The default value is disabled.</span></span>

- <span data-ttu-id="56485-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** Ustawia opcję limitu czasu dla przydzielania pakietu z puli pakietów klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="56485-197">Wartość domyślna to 1 sekunda (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="56485-197">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="56485-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** Dzięki temu Klient DNS może zezwolić aplikacji na tworzenie i Ustawianie puli pakietów klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="56485-199">Domyślnie ta opcja jest wyłączona, a klient DNS tworzy własną pulę pakietów w *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="56485-199">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="56485-200">**NX_DNS_CLIENT_CLEAR_QUEUE** Umożliwia to klientowi DNS czyszczenie starych komunikatów DNS z kolejki odbierania przed wysłaniem nowej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="56485-200">**NX_DNS_CLIENT_CLEAR_QUEUE** This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="56485-201">Usunięcie tych pakietów z poprzednich zapytań DNS uniemożliwia kolejkowanie gniazda klienta DNS z przepełniania i usuwania prawidłowych pakietów.</span><span class="sxs-lookup"><span data-stu-id="56485-201">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="56485-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** Dzięki temu Klient DNS może wysyłać zapytania dotyczące dodatkowych typów rekordów DNS w (np. CNAME, NS, MX, SOA, SRV i TXT).</span><span class="sxs-lookup"><span data-stu-id="56485-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="56485-203">**NX_DNS_CACHE_ENABLE** Dzięki temu Klient DNS może przechowywać rekordy odpowiedzi w pamięci podręcznej DNS.</span><span class="sxs-lookup"><span data-stu-id="56485-203">**NX_DNS_CACHE_ENABLE** This enables the DNS Client to store the answer records into DNS cache.</span></span>