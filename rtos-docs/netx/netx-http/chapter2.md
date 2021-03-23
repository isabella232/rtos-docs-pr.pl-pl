---
title: Rozdział 2 — Instalowanie i korzystanie z NetX HTTP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika HTTP NetX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822620"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a><span data-ttu-id="ce9fe-103">Rozdział 2 — Instalowanie i korzystanie z NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="ce9fe-103">Chapter 2 - Installation and use of NetX HTTP</span></span>

<span data-ttu-id="ce9fe-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="ce9fe-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="ce9fe-105">Product Distribution</span></span>

<span data-ttu-id="ce9fe-106">Usługę Azure RTO NetX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="ce9fe-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span>

- <span data-ttu-id="ce9fe-107">**nx_http_client. h** Plik nagłówka dla klienta HTTP dla NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-107">**nx_http_client.h** Header file for HTTP Client for NetX</span></span>
- <span data-ttu-id="ce9fe-108">**nx_http_server. h** Plik nagłówka dla serwera HTTP dla NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-108">**nx_http_server.h** Header file for HTTP Server for NetX</span></span>
- <span data-ttu-id="ce9fe-109">**nx_http_client. c** Plik źródłowy języka C dla klienta HTTP dla NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-109">**nx_http_client.c** C Source file for HTTP Client for NetX</span></span>
- <span data-ttu-id="ce9fe-110">**nx_http_server. c** Plik źródłowy języka C dla serwera HTTP dla NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-110">**nx_http_server.c** C Source file for HTTP Server for NetX</span></span>
- <span data-ttu-id="ce9fe-111">**nx_md5. c** Algorytmy Digest MD5</span><span class="sxs-lookup"><span data-stu-id="ce9fe-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="ce9fe-112">**filex_stub. h** Plik zastępczy, jeśli nie istnieje FileX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="ce9fe-113">**nx_http.pdf** Opis protokołu HTTP dla NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-113">**nx_http.pdf** Description of HTTP for NetX</span></span>
- <span data-ttu-id="ce9fe-114">**demo_netx_http. c** Demonstracja HTTP NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-114">**demo_netx_http.c** NetX HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="ce9fe-115">Instalacja HTTP</span><span class="sxs-lookup"><span data-stu-id="ce9fe-115">HTTP Installation</span></span>

<span data-ttu-id="ce9fe-116">Aby można było używać protokołu HTTP for NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-116">In order to use HTTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="ce9fe-117">Na przykład, jeśli NetX jest zainstalowany w katalogu "*\threadx\arm7\green*", następnie *nx_http_client. h* i *nx_http_client. c* dla NetX aplikacji klienckich http, a *nx_http_server. h* i *nx_http_server. c* dla NetX http Server Applications.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-117">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_http_client.h* and *nx_http_client.c* for NetX HTTP Client applications, and *nx_http_server.h* and *nx_http_server.c* for NetX HTTP Server applications.</span></span> <span data-ttu-id="ce9fe-118">*nx_md5. c* należy skopiować do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="ce9fe-119">W przypadku demonstracyjnej aplikacji "sterownik ram" NetX pliki klienta i serwera HTTP powinny być kopiowane do tego samego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-119">For the demo ‘ram driver’ application NetX HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="ce9fe-120">Korzystanie z protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="ce9fe-120">Using HTTP</span></span>

<span data-ttu-id="ce9fe-121">Korzystanie z protokołu HTTP for NetX jest łatwe.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-121">Using HTTP for NetX is easy.</span></span> <span data-ttu-id="ce9fe-122">W zasadzie kod aplikacji musi zawierać *nx_http_client. h* i/lub *nx_http_server. h* , gdy zawiera *tx_api. h, fx_api. h* i *nx_api. h*, w celu używania odpowiednio ThreadX, FileX i NetX.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-122">Basically, the application code must include *nx_http_client.h* and/or *nx_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="ce9fe-123">Po uwzględnieniu plików nagłówkowych HTTP, kod aplikacji może być w stanie wprowadzić wywołania funkcji HTTP określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="ce9fe-124">Aplikacja musi również zawierać *nx_http_client. c*, *nx_http_server. c* i *MD5. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-124">The application must also include *nx_http_client.c*, *nx_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="ce9fe-125">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="ce9fe-126">To wszystko, co jest wymagane do korzystania z protokołu HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-126">This is all that is required to use NetX HTTP.</span></span>

>[!NOTE] 
> <span data-ttu-id="ce9fe-127">Jeśli nie określono NX_HTTP_DIGEST_ENABLE w procesie kompilacji, plik *MD5. c* nie musi być dodany do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="ce9fe-128">Analogicznie, jeśli nie są wymagane możliwości klienta HTTP, plik *nx_http_client. c* może zostać pominięty.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-128">Similarly, if no HTTP Client capabilities are required, the *nx_http_client.c* file may be omitted.</span></span>

>[!NOTE] 
> <span data-ttu-id="ce9fe-129">Ponieważ protokół HTTP wykorzystuje usługi NetX TCP, należy włączyć protokół TCP przy użyciu wywołania *nx_tcp_enable* przed użyciem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-129">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="ce9fe-130">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="ce9fe-130">Small Example System</span></span>

<span data-ttu-id="ce9fe-131">Przykładem łatwego użycia protokołu HTTP NetX jest opisany poniżej rysunek 1,1.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-131">An example of how easy it is to use NetX HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="ce9fe-132">W tym przykładzie plik dołączany do protokołu HTTP *nx_http_client. h i nx_http_server. h są* wprowadzane w wierszu 8.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-132">In this example, the HTTP include file *nx_http_client.h and nx_http_server.h are* brought in at line 8.</span></span> <span data-ttu-id="ce9fe-133">Następnie serwer HTTP jest tworzony w lokalizacji "*tx_application_define*" w wierszu 131.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-133">Next, the HTTP Server is created in “*tx_application_define*” at line 131.</span></span>

>[!NOTE] 
> <span data-ttu-id="ce9fe-134">Blok kontroli serwera HTTP "*Server*" został zdefiniowany jako zmienna globalna w wierszu 25.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-134">The HTTP Server control block “*Server*” was defined as a global variable at line 25 previously.</span></span>

<span data-ttu-id="ce9fe-135">Po pomyślnym utworzeniu serwer HTTP jest uruchamiany w wierszu 136.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-135">After successful creation, an HTTP Server is started at line 136.</span></span> <span data-ttu-id="ce9fe-136">W wierszu 149 klient HTTP zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-136">At line 149 the HTTP Client is created.</span></span> <span data-ttu-id="ce9fe-137">A wreszcie klient zapisuje plik w wierszu 157 i odczytuje plik z powrotem w wierszu 195.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-137">And finally, the Client writes the file at line 157 and reads the file back at line 195.</span></span>

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
                         "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

<span data-ttu-id="ce9fe-138">Rysunek 1,1 przykład użycia protokołu HTTP z NetX</span><span class="sxs-lookup"><span data-stu-id="ce9fe-138">Figure 1.1 Example of HTTP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="ce9fe-139">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ce9fe-139">Configuration Options</span></span>

<span data-ttu-id="ce9fe-140">Istnieje kilka opcji konfiguracji do kompilowania protokołu HTTP dla NetX.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-140">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="ce9fe-141">Poniżej znajduje się lista wszystkich opcji, w których poszczególne są szczegółowo opisane.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-141">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="ce9fe-142">Wartości domyślne są wyświetlane, ale można je zdefiniować ponownie przed włączeniem *nx_http_client. h i nx_http_server. h*:</span><span class="sxs-lookup"><span data-stu-id="ce9fe-142">The default values are listed, but can be redefined prior to inclusion of *nx_http_client.h and nx_http_server.h*:</span></span>

- <span data-ttu-id="ce9fe-143">**NX_DISABLE_ERROR_CHECKING** Zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-143">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="ce9fe-144">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-144">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="ce9fe-145">**NX_HTTP_SERVER_PRIORITY** Priorytet wątku serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-145">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="ce9fe-146">Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-146">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="ce9fe-147">**NX_HTTP_NO_FILEX** Zdefiniowana, ta opcja udostępnia element zastępczy dla zależności FileX.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-147">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="ce9fe-148">Klient HTTP będzie działać bez żadnej zmiany, jeśli ta opcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-148">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="ce9fe-149">Należy zmodyfikować serwer HTTP lub użytkownik będzie musiał utworzyć kilku usługi FileX, aby działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-149">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="ce9fe-150">**NX_HTTP_TYPE_OF_SERVICE** Typ usługi wymaganej przez żądania HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-150">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="ce9fe-151">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="ce9fe-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** Liczba cykli czasomierza, które mogą być uruchamiane przez wątek serwera przed zwróceniem do wątków o takim samym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="ce9fe-153">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-153">The default value is 2.</span></span>
- <span data-ttu-id="ce9fe-154">**NX_HTTP_FRAGMENT_OPTION** Włączenie fragmentu dla żądań HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-154">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="ce9fe-155">Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentację TCP protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-155">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="ce9fe-156">**NX_HTTP_SERVER_WINDOW_SIZE** Rozmiar okna gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-156">**NX_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="ce9fe-157">Wartość domyślna to 2048 bajtów.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-157">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="ce9fe-158">**NX_HTTP_TIME_TO_LIVE** Określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-158">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="ce9fe-159">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-159">The default value is set to 0x80.</span></span>
- <span data-ttu-id="ce9fe-160">**NX_HTTP_SERVER_TIMEOUT** Określa liczbę ThreadXych taktów, dla których będą zawieszane usługi wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-160">**NX_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="ce9fe-161">Wartość domyślna to 10 sekund (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="ce9fe-161">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="ce9fe-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_server_socket_accept* .</span><span class="sxs-lookup"><span data-stu-id="ce9fe-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="ce9fe-163">Wartość domyślna to (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="ce9fe-163">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="ce9fe-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_socket_disconnect* .</span><span class="sxs-lookup"><span data-stu-id="ce9fe-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="ce9fe-165">Wartość domyślna to 10 sekund (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="ce9fe-165">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="ce9fe-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_socket_receive* .</span><span class="sxs-lookup"><span data-stu-id="ce9fe-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="ce9fe-167">Wartość domyślna to 10 sekund (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="ce9fe-167">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="ce9fe-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_socket_send* .</span><span class="sxs-lookup"><span data-stu-id="ce9fe-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="ce9fe-169">Wartość domyślna to 10 sekund (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="ce9fe-169">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="ce9fe-170">**NX_HTTP_MAX_HEADER_FIELD** Określa maksymalny rozmiar pola nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-170">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="ce9fe-171">Wartość domyślna to 256.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-171">The default value is 256.</span></span>
- <span data-ttu-id="ce9fe-172">**NX_HTTP_MULTIPART_ENABLE** Jeśli jest zdefiniowany, umożliwia serwerowi HTTP obsługę wieloczęściowych żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-172">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
- <span data-ttu-id="ce9fe-173">**NX_HTTP_SERVER_MAX_PENDING** Określa liczbę połączeń, które mogą być umieszczone w kolejce dla serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-173">**NX_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="ce9fe-174">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-174">The default value is set to 5.</span></span>
- <span data-ttu-id="ce9fe-175">**NX_HTTP_MAX_RESOURCE** Określa liczbę bajtów dozwolonych w *nazwie zasobu* dostarczonej przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-175">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="ce9fe-176">Wartość domyślna to 40.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-176">The default value is set to 40.</span></span>
- <span data-ttu-id="ce9fe-177">**NX_HTTP_MAX_NAME** Określa liczbę bajtów dozwolonych w *nazwie użytkownika* dostarczonej przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-177">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="ce9fe-178">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-178">The default value is set to 20.</span></span>
- <span data-ttu-id="ce9fe-179">**NX_HTTP_MAX_PASSWORD** Określa liczbę bajtów dozwolonych w *haśle* dostarczonym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-179">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="ce9fe-180">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-180">The default value is set to 20.</span></span>
- <span data-ttu-id="ce9fe-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia serwera.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="ce9fe-182">Minimalny rozmiar jest wymagany w celu zapewnienia, że kompletny nagłówek HTTP może być zawarty w jednym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-182">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="ce9fe-183">Wartość domyślna to 600.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-183">The default value is set to 600.</span></span>
- <span data-ttu-id="ce9fe-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="ce9fe-185">Minimalny rozmiar jest wymagany w celu zapewnienia, że kompletny nagłówek HTTP może być zawarty w jednym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-185">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="ce9fe-186">Wartość domyślna to 300.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-186">The default value is set to 300.</span></span>
- <span data-ttu-id="ce9fe-187">**NX_HTTP_SERVER_RETRY_SECONDS** *ustawić limit czasu ponownej transmisji gniazda serwera (w sekundach). Wartość domyślna to* 2.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Set the Server socket retransmission timeout in seconds. The* default value is set to 2.</span></span>
- <span data-ttu-id="ce9fe-188">**NX_HTTP_SERVER_RETRY_MAX** Ustawia maksymalną liczbę ponownych transmisji w gnieździe serwera.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-188">**NX_HTTP_SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="ce9fe-189">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-189">The default value is set to 10.</span></span>
- <span data-ttu-id="ce9fe-190">**NX_HTTP_SERVER_RETRY_SHIFT** Ta wartość jest używana do ustawiania następnego limitu czasu ponownej transmisji.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-190">**NX_HTTP_SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="ce9fe-191">Bieżący limit czasu jest mnożony przez liczbę ponownych transmisji do tej pory, przesuniętych przez wartość przedziału czasu gniazda.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-191">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="ce9fe-192">Wartość domyślna to 1 w przypadku podwajania limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-192">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="ce9fe-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** Określa maksymalną liczbę pakietów, które można umieścić w kolejce kolejki retransmisji w gnieździe serwera.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="ce9fe-194">Jeśli liczba pakietów w kolejce osiągnie tę liczbę, nie można wysyłać kolejnych pakietów, dopóki nie zostaną wydane co najmniej jeden pakiet z kolejki.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-194">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="ce9fe-195">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="ce9fe-195">The default value is set to 20.</span></span>