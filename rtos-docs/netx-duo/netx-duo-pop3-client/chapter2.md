---
title: Rozdział 2 — Instalowanie i używanie klienta POP3 NetX Duo
description: Klient POP3 NetX Duo zawiera jeden plik źródłowy, jeden plik nagłówkowy i plik demonstracyjny.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6ef4b6ba7aadf77ab95a4a12235eda847f32f3d5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821750"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-pop3-client"></a><span data-ttu-id="2cd03-103">Rozdział 2 — Instalowanie i używanie klienta POP3 NetX Duo</span><span class="sxs-lookup"><span data-stu-id="2cd03-103">Chapter 2 - Installation and Use of NetX Duo POP3 Client</span></span>

<span data-ttu-id="2cd03-104">Klient POP3 NetX zawiera jeden plik źródłowy, jeden plik nagłówkowy i plik demonstracyjny.</span><span class="sxs-lookup"><span data-stu-id="2cd03-104">NetX POP3 Client includes one source file, one header file, and a demo file.</span></span> <span data-ttu-id="2cd03-105">Istnieją dwa dodatkowe pliki dla usług MD5 Digest.</span><span class="sxs-lookup"><span data-stu-id="2cd03-105">There are two additional files for MD5 digest services.</span></span> <span data-ttu-id="2cd03-106">Istnieje również plik PDF podręcznika użytkownika (ten dokument).</span><span class="sxs-lookup"><span data-stu-id="2cd03-106">There is also a User Guide PDF file (this document).</span></span>

- <span data-ttu-id="2cd03-107">**nxd_pop3_client. c** Plik źródłowy języka C dla interfejsu API klienta POP3 NetX Duo</span><span class="sxs-lookup"><span data-stu-id="2cd03-107">**nxd_pop3_client.c** C Source file for NetX Duo POP3 Client API</span></span>
- <span data-ttu-id="2cd03-108">**nxd_pop3_client. h** Plik nagłówkowy języka C dla interfejsu API klienta POP3 NetX Duo</span><span class="sxs-lookup"><span data-stu-id="2cd03-108">**nxd_pop3_client.h** C Header file for NetX Duo POP3 Client API</span></span>
- <span data-ttu-id="2cd03-109">**demo_netxduo_pop3_client. c** Plik demonstracyjny dotyczący tworzenia klienta POP3 i inicjowania sesji</span><span class="sxs-lookup"><span data-stu-id="2cd03-109">**demo_netxduo_pop3_client.c** Demo file for POP3 Client creation and session initiation</span></span>
- <span data-ttu-id="2cd03-110">**nx_md5. c** Plik źródłowy języka C definiujący usługi MD5 Digest</span><span class="sxs-lookup"><span data-stu-id="2cd03-110">**nx_md5.c** C Source file defining MD5 digest services</span></span>
- <span data-ttu-id="2cd03-111">**nx_md5. h** Plik nagłówkowy języka C definiujący usługi MD5 Digest</span><span class="sxs-lookup"><span data-stu-id="2cd03-111">**nx_md5.h** C Header file defining MD5 digest services</span></span>
- <span data-ttu-id="2cd03-112">**nxd_pop3_client.pdf** Podręcznik użytkownika klienta POP3 NetX Duo</span><span class="sxs-lookup"><span data-stu-id="2cd03-112">**nxd_pop3_client.pdf** NetX Duo POP3 Client User Guide</span></span>

<span data-ttu-id="2cd03-113">Aby można było korzystać z klienta POP3 NetX Duo, cała wymieniona wyżej dystrybucja może zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2cd03-113">To use NetX Duo POP3 Client, the entire distribution mentioned previously can be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="2cd03-114">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\mcf5272\green*", wówczas pliki *nx_md5. h*, *nx_md5. c,* *nxd_pop3_client. h i nxd_pop3_client. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2cd03-114">For example, if NetX Duo is installed in the directory “*\threadx\mcf5272\green*” then the *nx_md5.h*, *nx_md5.c,* *nxd_pop3_client.h, and nxd_pop3_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-pop3-client"></a><span data-ttu-id="2cd03-115">Korzystanie z klienta POP3 NetX Duo</span><span class="sxs-lookup"><span data-stu-id="2cd03-115">Using NetX Duo POP3 Client</span></span>

<span data-ttu-id="2cd03-116">Aby można było użyć usługi klienta POP3 NetX Duo, aplikacja musi dodać *nxd_pop3_client. c* do projektu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2cd03-116">To use the NetX Duo POP3 Client service, the application must add *nxd_pop3_client.c* to its build project.</span></span> <span data-ttu-id="2cd03-117">Kod aplikacji musi zawierać *nx_md5. h i nxd_pop3_client. h* po *tx_api. h* i *nx_api. h*, aby można było korzystać z ThreadX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2cd03-117">The application code must include *nx_md5.h, and nxd_pop3_client.h* after *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span>

<span data-ttu-id="2cd03-118">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i kod obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2cd03-118">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="2cd03-119">Jest to wszystko wymagane do korzystania z klienta POP3 NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2cd03-119">This is all that is required to use the NetX Duo POP3 Client.</span></span>

## <a name="small-example-of-the-netx-duo-pop3-client"></a><span data-ttu-id="2cd03-120">Mały przykład klienta POP3 NetX Duo</span><span class="sxs-lookup"><span data-stu-id="2cd03-120">Small Example of the NetX Duo POP3 Client</span></span>

<span data-ttu-id="2cd03-121">Przykład korzystania z usług klienta POP3 w programie NetX Duo został opisany poniżej.</span><span class="sxs-lookup"><span data-stu-id="2cd03-121">An example of how to use NetX Duo POP3 Client services is described in Figure 1 that appears below.</span></span> <span data-ttu-id="2cd03-122">Ten pokaz konfiguruje dwa wywołania zwrotne w celu powiadomienia o pobraniach poczty i zakończeniu sesji w wierszach 37 i 38.</span><span class="sxs-lookup"><span data-stu-id="2cd03-122">This demo sets up the two callbacks for notification of mail download and session completion on lines 37 and 38.</span></span> <span data-ttu-id="2cd03-123">Pula pakietów klienta POP3 jest tworzona w wierszu 76.</span><span class="sxs-lookup"><span data-stu-id="2cd03-123">The POP3 Client packet pool is created on line 76.</span></span> <span data-ttu-id="2cd03-124">Zadanie wątku IP jest tworzone w wierszu 88.</span><span class="sxs-lookup"><span data-stu-id="2cd03-124">The IP thread task is created on line 88.</span></span> <span data-ttu-id="2cd03-125">Należy zauważyć, że ta pula pakietów jest również używana dla puli pakietów klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="2cd03-125">Note that this packet pool is also used for the POP3 Client packet pool.</span></span> <span data-ttu-id="2cd03-126">Protokół TCP jest włączony w zadaniu IP w wierszu 107.</span><span class="sxs-lookup"><span data-stu-id="2cd03-126">TCP is enabled on the IP task in line 107.</span></span>

<span data-ttu-id="2cd03-127">Klient POP3 jest tworzony w wierszu 133 wewnątrz funkcji wprowadzania wątku aplikacji, *demo_thread_entry*.</span><span class="sxs-lookup"><span data-stu-id="2cd03-127">The POP3 Client is created on line 133 inside the application thread entry function, *demo_thread_entry*.</span></span> <span data-ttu-id="2cd03-128">Wynika to z faktu, że usługa *nx_pop3_client_create* próbuje nawiązać połączenie TCP z serwerem POP3.</span><span class="sxs-lookup"><span data-stu-id="2cd03-128">This is because the *nx_pop3_client_create* service also attempts to make a TCP connection with the POP3 server.</span></span> <span data-ttu-id="2cd03-129">Jeśli to się powiedzie, aplikacja wysyła zapytanie do serwera POP3 o liczbę elementów w maildrop w wierszu 149 przy użyciu usługi *nx_pop3_client_mail_items_get* .</span><span class="sxs-lookup"><span data-stu-id="2cd03-129">If successful, the application queries the POP3 server for the number of items in its maildrop on line 149 using the *nx_pop3_client_mail_items_get* service.</span></span>

<span data-ttu-id="2cd03-130">Jeśli istnieje co najmniej jeden element, aplikacja iteruje przez pętlę while dla każdego elementu poczty, aby pobrać wiadomość e-mail.</span><span class="sxs-lookup"><span data-stu-id="2cd03-130">If there are one or more items, the application iterates through the while loop for each mail item to download the mail message.</span></span> <span data-ttu-id="2cd03-131">Żądanie RETR jest wykonywane w wierszu 149 w wywołaniu *nx_pop3_client_mail_item_get* .</span><span class="sxs-lookup"><span data-stu-id="2cd03-131">The RETR request is made on line 149 in the *nx_pop3_client_mail_item_get* call.</span></span> <span data-ttu-id="2cd03-132">Jeśli to się powiedzie, aplikacja pobiera pakiety przy użyciu usługi *nx_pop3_client_mail_item_message_get* w wierszu 177 do czasu, aż wykryje ostatni pakiet w komunikacie w wierszu 196.</span><span class="sxs-lookup"><span data-stu-id="2cd03-132">If successful, the application downloads packets using the *nx_pop3_client_mail_item_message_get* service on line 177 till it detects the last packet in the message has been received on line 196.</span></span> <span data-ttu-id="2cd03-133">Na koniec aplikacja usuwa element poczty, przy założeniu, że w wierszu 199 w wywołaniu *nx_pop3_client_mail_item_delete* nastąpiło pomyślne pobranie.</span><span class="sxs-lookup"><span data-stu-id="2cd03-133">Lastly, the application deletes the mail item, assuming a successful download has occurred on line 199 in *the nx_pop3_client_mail_item_delete* call.</span></span> <span data-ttu-id="2cd03-134">W dokumencie RFC 1939 zaleca się, aby klienci POP3 instruują serwer, aby usunął pobrane elementy poczty, aby zapobiec wysyłaniu poczty w maildrop klienta.</span><span class="sxs-lookup"><span data-stu-id="2cd03-134">The RFC 1939 recommends that POP3 Clients instruct the Server to delete downloaded mail items to prevent mail accumulating in the Client’s maildrop.</span></span> <span data-ttu-id="2cd03-135">Serwer może to zrobić automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2cd03-135">The Server may automatically do so anyway.</span></span>

<span data-ttu-id="2cd03-136">Po pobraniu wszystkich elementów poczty lub niepowodzeniu wywołania usługi klienta POP3 aplikacja kończy działanie pętli i usuwa klienta POP3 w wierszu 217 przy użyciu usługi *nx_pop3_client_delete* .</span><span class="sxs-lookup"><span data-stu-id="2cd03-136">Once all the mail items are downloaded, or if a POP3 Client service call fails, the application exits of the loop and deletes the POP3 Client on line 217 using the *nx_pop3_client_delete* service.</span></span>

```C
/*
   demo_netxduo_pop3.c

   This is a small demo of POP3 Client on the NetX Duo TCP/IP stack.
   This demo relies on Thread, NetX Duo and POP3 Client API to conduct
   a POP3 mail session.
 */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_pop3_client.h"

#define DEMO_STACK_SIZE             4096
#define CLIENT_ADDRESS              IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS              IP_ADDRESS(192,2,2,89)
#define SERVER_PORT                 110

/* Replace the 'ram' driver with your own Ethernet driver. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client.  */

TX_THREAD           demo_client_thread;
NX_POP3_CLIENT      demo_client;
NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void    demo_thread_entry(ULONG info);


  /* Shared secret is the same as password. */

#define LOCALHOST                               "recipient@domain.com"
#define LOCALHOST_PASSWORD                      "testpwd"

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT     status;
    UCHAR    *free_memory_pointer;


    /* Setup the working pointer.  */
    free_memory_pointer =  first_unused_memory;

    /* Create a client thread.  */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                     free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                     TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer =  free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                                    PAYLOAD_SIZE, free_memory_pointer,
                                    (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);


    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                          CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                          _nx_ram_network_driver, free_memory_pointer,
                          2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}



/* Define the application thread entry function. */

void    demo_thread_entry(ULONG info)
{

    UINT        status;
    UINT        mail_item, number_mail_items;
    UINT        bytes_downloaded = 0;
    UINT        final_packet = NX_FALSE;
    ULONG       total_size, mail_item_size, bytes_retrieved;
    NX_PACKET   *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);


    /* Create a NetX POP3 Client instance with no byte or block memory pools.
       Note that it uses its password for its APOP shared secret. */
    status =  nx_pop3_client_create(&demo_client,
                                    NX_TRUE,
                                    &client_ip, &client_packet_pool, SERVER_ADDRESS,
                                    SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox.  */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items,
                                            &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {

        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items.  */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {


        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item,
                                               &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely
           downloaded. */
        while((final_packet ==  NX_FALSE) && (status == NX_SUCCESS))
        {

            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {

                break;
            }

            if (bytes_retrieved != 0)
            {

                printf("Received %d bytes of data for item %d: %s\n",
                        packet_ptr -> nx_packet_length,
                        mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);

    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client.  This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

<span data-ttu-id="2cd03-137">**Rysunek 1. Przykład aplikacji klienckiej usługi POP3 NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="2cd03-137">**Figure 1. Example of a NetX Duo POP3 Client application**</span></span>

## <a name="pop3-client-configuration-options"></a><span data-ttu-id="2cd03-138">Opcje konfiguracji klienta POP3</span><span class="sxs-lookup"><span data-stu-id="2cd03-138">POP3 Client Configuration Options</span></span>

<span data-ttu-id="2cd03-139">Istnieje kilka opcji konfiguracji z klientem POP3 NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2cd03-139">There are several configuration options with the NetX Duo POP3 Client.</span></span> <span data-ttu-id="2cd03-140">Poniżej znajduje się lista wszystkich opcji opisanych szczegółowo:</span><span class="sxs-lookup"><span data-stu-id="2cd03-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="2cd03-141">**NX_POP3_CLIENT_PACKET_TIMEOUT** Definiuje opcję oczekiwania w sekundach dla klienta POP3 do przydzielenia pakietu.</span><span class="sxs-lookup"><span data-stu-id="2cd03-141">**NX_POP3_CLIENT_PACKET_TIMEOUT** This defines the wait option in seconds for the POP3 Client to allocate a packet.</span></span> <span data-ttu-id="2cd03-142">Wartość domyślna to 1 sekunda.</span><span class="sxs-lookup"><span data-stu-id="2cd03-142">The default value is 1 second.</span></span>
- <span data-ttu-id="2cd03-143">**NX_POP3_CLIENT_CONNECTION_TIMEOUT** Definiuje opcję oczekiwania w sekundach, aby klient POP3 mógł nawiązać połączenie z serwerem POP3.</span><span class="sxs-lookup"><span data-stu-id="2cd03-143">**NX_POP3_CLIENT_CONNECTION_TIMEOUT** This defines the wait option in seconds for the POP3 Client to connect with the POP3 Server.</span></span> <span data-ttu-id="2cd03-144">Wartość domyślna to 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="2cd03-144">The default value is 30 seconds.</span></span>
- <span data-ttu-id="2cd03-145">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT** Definiuje opcję oczekiwania w sekundach, przez który klient POP3 ma rozłączyć się z serwerem POP3.</span><span class="sxs-lookup"><span data-stu-id="2cd03-145">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT** This defines the wait option in seconds for the POP3 Client to disconnect from the POP3 Server.</span></span> <span data-ttu-id="2cd03-146">Wartość domyślna to 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="2cd03-146">The default value is 2 seconds.</span></span>
- <span data-ttu-id="2cd03-147">**NX_POP3_TCP_SOCKET_SEND_WAIT** Ta opcja ustawia opcję oczekiwania w sekundach w *nx_tcp_socket_send* wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="2cd03-147">**NX_POP3_TCP_SOCKET_SEND_WAIT** This option sets the wait option in seconds in *nx_tcp_socket_send* service calls.</span></span> <span data-ttu-id="2cd03-148">Wartość domyślna to 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="2cd03-148">The default value is 2 seconds.</span></span>
- <span data-ttu-id="2cd03-149">**NX_POP3_SERVER_REPLY_TIMEOUT** Ta opcja ustawia opcję oczekiwania w *nx_tcp_socket_receive* wywołań usługi dla odpowiedzi serwera na żądanie klienta.</span><span class="sxs-lookup"><span data-stu-id="2cd03-149">**NX_POP3_SERVER_REPLY_TIMEOUT** This option sets the wait option in *nx_tcp_socket_receive* service calls for the Server reply to a Client request.</span></span> <span data-ttu-id="2cd03-150">Wartość domyślna to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="2cd03-150">The default value is 10 seconds.</span></span>
- <span data-ttu-id="2cd03-151">**NX_POP3_CLIENT_TCP_WINDOW_SIZE** Ta opcja ustawia rozmiar okna odbierania klienta TCP.</span><span class="sxs-lookup"><span data-stu-id="2cd03-151">**NX_POP3_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="2cd03-152">Ta wartość powinna być równa rozmiarowi jednostki MTU wystąpienia IP pomniejszonej o adres IP i nagłówek TCP.</span><span class="sxs-lookup"><span data-stu-id="2cd03-152">This should be set to the IP instance MTU size minus the IP and TCP header.</span></span> <span data-ttu-id="2cd03-153">Wartość domyślna to 1460.</span><span class="sxs-lookup"><span data-stu-id="2cd03-153">The default value is 1460.</span></span> <span data-ttu-id="2cd03-154">Ta wartość powinna być mniejsza, jeśli aplikacja wysyła pakiety POP3 za pośrednictwem protokołu IPv6 (1440 bajtów) do konta dla większego nagłówka IPv6.</span><span class="sxs-lookup"><span data-stu-id="2cd03-154">This should be less if the application is sending POP3 packets over IPv6 (1440 bytes) to account for the larger IPv6 header.</span></span>
- <span data-ttu-id="2cd03-155">**NX_POP3_MAX_USERNAME** Ta opcja ustawia rozmiar buforu nazwy użytkownika klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="2cd03-155">**NX_POP3_MAX_USERNAME** This option sets the size of the buffer of the POP3 Client user name.</span></span> <span data-ttu-id="2cd03-156">Wartość domyślna to 40 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2cd03-156">The default value is 40 bytes.</span></span>
- <span data-ttu-id="2cd03-157">**NX_POP3_MAX_PASSWORD** Ta opcja ustawia rozmiar buforu hasła klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="2cd03-157">**NX_POP3_MAX_PASSWORD** This option sets the size of the buffer of the POP3 Client password.</span></span> <span data-ttu-id="2cd03-158">Wartość domyślna to 20 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2cd03-158">The default value is 20 bytes.</span></span>
