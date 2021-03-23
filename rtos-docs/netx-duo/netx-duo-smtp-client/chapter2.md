---
title: Rozdział 2 — Instalowanie i korzystanie z klienta SMTP NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta SMTP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821690"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a><span data-ttu-id="ef92b-103">Rozdział 2 — Instalowanie i korzystanie z klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-103">Chapter 2 - Installation and use of NetX Duo SMTP client</span></span>

<span data-ttu-id="ef92b-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta SMTP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="ef92b-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo SMTP Client component.</span></span>

## <a name="netx-duo-smtp-client-installation"></a><span data-ttu-id="ef92b-105">Instalacja klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-105">NetX Duo SMTP Client Installation</span></span>

<span data-ttu-id="ef92b-106">Klient SMTP NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="ef92b-106">The NetX Duo SMTP Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="ef92b-107">Pakiet zawiera następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="ef92b-107">The package includes the following files:</span></span>

- <span data-ttu-id="ef92b-108">**nxd_smtp_client. c** Plik źródłowy języka C dla interfejsu API klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-108">**nxd_smtp_client.c** C Source file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="ef92b-109">**nxd_smtp_client. h** Plik nagłówkowy języka C dla interfejsu API klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-109">**nxd_smtp_client.h** C Header file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="ef92b-110">**demo_netxduo_smtp_client. c** Demonstracja dla klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-110">**demo_netxduo_smtp_client.c** Demo for NetX Duo SMTP Client</span></span>
- <span data-ttu-id="ef92b-111">**Podręcznik użytkownikanxd_smtp_client.pdf** Interfejs API klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-111">**nxd_smtp_client.pdf User Guide for** NetX Duo SMTP Client API</span></span>

<span data-ttu-id="ef92b-112">Aby użyć interfejsu API klienta SMTP NetX Duo, cała wymieniona wyżej dystrybucja może zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="ef92b-112">To use the NetX Duo SMTP Client API, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="ef92b-113">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "c:*\myproject*", wówczas pliki *nxd_smtp_client. h i nxd_smtp_client. c* powinny być skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ef92b-113">For example, if NetX Duo is installed in the directory “c:*\myproject*” then the *nxd_smtp_client.h, and nxd_smtp_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-smtp-client"></a><span data-ttu-id="ef92b-114">Korzystanie z klienta SMTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ef92b-114">Using NetX Duo SMTP Client</span></span>

<span data-ttu-id="ef92b-115">Aby utworzyć aplikację kliencką SMTP NetX Duo, należy najpierw skompilować biblioteki ThreadX i NetX Duo oraz uwzględnić je w projekcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef92b-115">To create the NetX Duo SMTP Client application, it must first build the ThreadX and NetX Duo libraries and include them in the build project.</span></span> <span data-ttu-id="ef92b-116">Aplikacja musi następnie uwzględnić TX *_api. h* i *nx_api. h w kodzie źródłowym aplikacji*.</span><span class="sxs-lookup"><span data-stu-id="ef92b-116">The application must then include tx *_api.h* and *nx_api.h in its application source code*.</span></span> <span data-ttu-id="ef92b-117">Spowoduje to włączenie usług ThreadX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="ef92b-117">This will enable ThreadX and NetX Duo services.</span></span> <span data-ttu-id="ef92b-118">Musi on również zawierać *nxd_smtp_client. c* i *nxd_smtp_client. h* po *tx_api. h* i *Nx_api. h do korzystania z usług klienta SMTP.*</span><span class="sxs-lookup"><span data-stu-id="ef92b-118">It must also include *nxd_smtp_client.c* and *nxd_smtp_client.h* after *tx_api.h* and *nx_api.h to use SMTP Client services.*</span></span>

<span data-ttu-id="ef92b-119">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i kod obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef92b-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="ef92b-120">Jest to wszystko wymagane do utworzenia aplikacji klienckiej SMTP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="ef92b-120">This is all that is required to create a NetX Duo SMTP Client application.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="ef92b-121">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="ef92b-121">Small Example System</span></span>

<span data-ttu-id="ef92b-122">Przykład korzystania z klienta SMTP NetX Duo został opisany na rysunku 1, który pojawia się poniżej.</span><span class="sxs-lookup"><span data-stu-id="ef92b-122">An example of using the NetX Duo SMTP Client is described in Figure 1 that appears below.</span></span> <span data-ttu-id="ef92b-123">Pula pakietów dla wystąpienia IP jest tworzona przy użyciu usługi nx_packet_pool_create w wierszu 68 i ma bardzo mały ładunek pakietu.</span><span class="sxs-lookup"><span data-stu-id="ef92b-123">The packet pool for the IP instance is created using the nx_packet_pool_create service, on line 68 and has a very small packet payload.</span></span> <span data-ttu-id="ef92b-124">Wynika to z faktu, że wystąpienie IP wysyła tylko pakiety sterujące, które nie wymagają dużo ładunku.</span><span class="sxs-lookup"><span data-stu-id="ef92b-124">This is because the IP instance only sends control packets which don’t require much payload.</span></span> <span data-ttu-id="ef92b-125">Pula pakietów klienta SMTP utworzona w wierszu 84 i służy do przesyłania komunikatów klienta SMTP do danych serwera i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ef92b-125">The SMTP Client packet pool created on line 84 and is used for transmitting SMTP Client messages to the server and message data.</span></span> <span data-ttu-id="ef92b-126">Jego ładunek pakietu jest dużo większy.</span><span class="sxs-lookup"><span data-stu-id="ef92b-126">Its packet payload is much larger.</span></span> <span data-ttu-id="ef92b-127">Wystąpienie protokołu IP jest tworzone w wierszu 118 przy użyciu tej samej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="ef92b-127">The IP instance is created in line 118 using the same packet pool.</span></span> <span data-ttu-id="ef92b-128">Protokół TCP, wymagany dla protokołu SMTP, jest włączony w wystąpieniu protokołu IP w wierszu 130.</span><span class="sxs-lookup"><span data-stu-id="ef92b-128">TCP, required for the SMTP protocol, is enabled on the IP instance in line 130.</span></span>

<span data-ttu-id="ef92b-129">W wątku aplikacji klient SMTP jest tworzony przy użyciu usługi *nxd_smtp_client_create* w wierszu 170.</span><span class="sxs-lookup"><span data-stu-id="ef92b-129">In the application thread, the SMTP Client is created using the *nxd_smtp_client_create* service, in line 170.</span></span> <span data-ttu-id="ef92b-130">Usługa *nxd_smtp_client_create* obsługuje połączenia z serwerem SMTP IPv4 i IPv6, chociaż ten przykład jest ograniczony do protokołu IPv4.</span><span class="sxs-lookup"><span data-stu-id="ef92b-130">The *nxd_smtp_client_create* service supports both IPv4 and IPv6 SMTP server connections although this example is limited to IPv4.</span></span> <span data-ttu-id="ef92b-131">Następnie wiadomość e-mail zostanie przesłana do klienta SMTP w celu transmisji w wierszu 184 przy użyciu usługi *nx_smtp_mail_send* .</span><span class="sxs-lookup"><span data-stu-id="ef92b-131">Then the mail message is submitted to the SMTP Client for transmission on line 184 using the *nx_smtp_mail_send* service.</span></span> <span data-ttu-id="ef92b-132">Należy pamiętać, że wiersz tematu z nagłówkiem zawartości poczty jest tworzony niezależnie od treści komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ef92b-132">Note that the subject line with the mail content header is created separately from the message body.</span></span> <span data-ttu-id="ef92b-133">Należy również zauważyć, że żądanie wysłania poczty akceptuje tylko jeden adres e-mail adresata, który jest traktowany pod kątem poprawności składniowej.</span><span class="sxs-lookup"><span data-stu-id="ef92b-133">Also note that the send mail request accepts only one recipient mail address which is assumed to be syntactically correct.</span></span>

<span data-ttu-id="ef92b-134">Następnie aplikacja kończy działanie klienta SMTP w wierszu 200.</span><span class="sxs-lookup"><span data-stu-id="ef92b-134">Then the application terminates the SMTP Client on line 200.</span></span> <span data-ttu-id="ef92b-135">Usługa *nx_smtp_client_delete* sprawdza, czy połączenie gniazda zostało zamknięte i czy port jest niepowiązany.</span><span class="sxs-lookup"><span data-stu-id="ef92b-135">The *nx_smtp_client_delete* service checks that the socket connection is closed and the port is unbound.</span></span> <span data-ttu-id="ef92b-136">Należy pamiętać, że do aplikacji klienckiej SMTP należy usunąć pulę pakietów, jeśli nie ma już jej użycia.</span><span class="sxs-lookup"><span data-stu-id="ef92b-136">Note that it is up to the SMTP Client application to delete the packet pool if it no longer has use for it.</span></span>

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

<span data-ttu-id="ef92b-137">**Rysunek 1. Przykład użycia klienta SMTP z NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="ef92b-137">**Figure 1. Example of SMTP Client use with NetX Duo**</span></span>

## <a name="client-configuration-options"></a><span data-ttu-id="ef92b-138">Opcje konfiguracji klienta</span><span class="sxs-lookup"><span data-stu-id="ef92b-138">Client Configuration Options</span></span>

<span data-ttu-id="ef92b-139">Istnieje kilka opcji konfiguracji z interfejsem API klienta SMTP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="ef92b-139">There are several configuration options with the NetX Duo SMTP Client API.</span></span> <span data-ttu-id="ef92b-140">Poniżej znajduje się lista wszystkich opcji opisanych szczegółowo:</span><span class="sxs-lookup"><span data-stu-id="ef92b-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="ef92b-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Ta opcja ustawia rozmiar okna odbierania klienta TCP.</span><span class="sxs-lookup"><span data-stu-id="ef92b-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="ef92b-142">Ta wartość powinna być mniejsza niż rozmiar jednostki MTU podstawowego sprzętu sieci Ethernet i umożliwia miejsce dla nagłówków IP i TCP.</span><span class="sxs-lookup"><span data-stu-id="ef92b-142">This should be set to below the MTU size of the underlying Ethernet hardware and allow room for IP and TCP headers.</span></span> <span data-ttu-id="ef92b-143">Domyślny rozmiar okna klienta SMTP w programie NetX Duo to 1460.</span><span class="sxs-lookup"><span data-stu-id="ef92b-143">The default NetX Duo SMTP Client TCP window size is 1460.</span></span>
- <span data-ttu-id="ef92b-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** Ta opcja ustawia limit czasu dla alokacji pakietu NetX.</span><span class="sxs-lookup"><span data-stu-id="ef92b-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** This option sets the timeout on NetX packet allocation.</span></span> <span data-ttu-id="ef92b-145">Domyślny limit czasu pakietu klienta SMTP w programie NetX Duo wynosi 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="ef92b-145">The default NetX Duo SMTP Client packet timeout is 2 seconds.</span></span>
- <span data-ttu-id="ef92b-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Ta opcja ustawia limit czasu połączenia gniazda TCP klienta.</span><span class="sxs-lookup"><span data-stu-id="ef92b-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** This option sets the Client TCP socket connect timeout.</span></span> <span data-ttu-id="ef92b-147">Domyślny limit czasu połączenia klienta SMTP w programie NetX Duo wynosi 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="ef92b-147">The default NetX Duo SMTP Client connect timeout is 10 seconds.</span></span>
- <span data-ttu-id="ef92b-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Ta opcja ustawia limit czasu rozłączenia gniazda TCP klienta.</span><span class="sxs-lookup"><span data-stu-id="ef92b-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** This option sets the Client TCP socket disconnect timeout.</span></span> <span data-ttu-id="ef92b-149">Domyślny limit czasu rozłączenia klienta SMTP w programie NetX Duo wynosi 5 sekund \*.</span><span class="sxs-lookup"><span data-stu-id="ef92b-149">The default NetX Duo SMTP Client disconnect timeout is 5 seconds\*.</span></span> <span data-ttu-id="ef92b-150">Należy pamiętać, że jeśli klient SMTP napotka błąd wewnętrzny, taki jak zerwane połączenie, może przerwać połączenie z upływem limitu czasu oczekiwania na zero.</span><span class="sxs-lookup"><span data-stu-id="ef92b-150">Note that if the SMTP Client encounters an internal error such as a broken connection it may terminate the connection with a zero wait timeout.</span></span>
- <span data-ttu-id="ef92b-151">**NX_SMTP_GREETING_TIMEOUT** Ta opcja określa limit czasu, przez który klient otrzymuje odpowiedź serwera na jego powitanie.</span><span class="sxs-lookup"><span data-stu-id="ef92b-151">**NX_SMTP_GREETING_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to its greeting.</span></span> <span data-ttu-id="ef92b-152">Wartość domyślna klienta SMTP NetX Duo to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="ef92b-152">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="ef92b-153">**NX_SMTP_ENVELOPE_TIMEOUT** Ta opcja określa limit czasu, przez który klient otrzymuje odpowiedź serwera na polecenie klienta.</span><span class="sxs-lookup"><span data-stu-id="ef92b-153">**NX_SMTP_ENVELOPE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to a Client command.</span></span> <span data-ttu-id="ef92b-154">Wartość domyślna klienta SMTP NetX Duo to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="ef92b-154">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="ef92b-155">**NX_SMTP_MESSAGE_TIMEOUT** Ta opcja określa limit czasu, przez który klient otrzymuje odpowiedź serwera w celu odebrania danych wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="ef92b-155">**NX_SMTP_MESSAGE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to receiving the mail message data.</span></span> <span data-ttu-id="ef92b-156">Wartość domyślna klienta SMTP NetX Duo to 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="ef92b-156">The default NetX Duo SMTP Client value is 30 seconds.</span></span>
- <span data-ttu-id="ef92b-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** Ta opcja definiuje opcję oczekiwania buforu do przechowywania hasła użytkownika podczas uwierzytelniania SMTP na serwerze.</span><span class="sxs-lookup"><span data-stu-id="ef92b-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** This option defines the wait option of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="ef92b-158">Wartość domyślna to 20 bajtów.</span><span class="sxs-lookup"><span data-stu-id="ef92b-158">The default value is 20 bytes.</span></span>
- <span data-ttu-id="ef92b-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Ta opcja określa rozmiar buforu dla wyodrębniania wezwania serwera podczas uwierzytelniania SMTP.</span><span class="sxs-lookup"><span data-stu-id="ef92b-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** This option defines the size of the buffer for extracting the Server challenge during SMTP authentication.</span></span> <span data-ttu-id="ef92b-160">Wartość domyślna to 200 bajtów.</span><span class="sxs-lookup"><span data-stu-id="ef92b-160">The default value is 200 bytes.</span></span> <span data-ttu-id="ef92b-161">W przypadku logowania i ZWYKŁEgo uwierzytelniania klient SMTP prawdopodobnie może użyć mniejszego buforu.</span><span class="sxs-lookup"><span data-stu-id="ef92b-161">For LOGIN and PLAIN authentication, the SMTP Client can probably use a smaller buffer.</span></span>
- <span data-ttu-id="ef92b-162">**NX_SMTP_CLIENT_MAX_PASSWORD** Ta opcja określa rozmiar buforu do przechowywania hasła użytkownika podczas uwierzytelniania przy użyciu protokołu SMTP na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="ef92b-162">**NX_SMTP_CLIENT_MAX_PASSWORD** This option defines the size of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="ef92b-163">Wartość domyślna to 20 bajtów.</span><span class="sxs-lookup"><span data-stu-id="ef92b-163">The default value is 20 bytes.</span></span> 
- <span data-ttu-id="ef92b-164">**NX_SMTP_CLIENT_MAX_USERNAME** Ta opcja określa rozmiar buforu do przechowywania nazwy użytkownika hosta podczas uwierzytelniania przy użyciu protokołu SMTP na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="ef92b-164">**NX_SMTP_CLIENT_MAX_USERNAME** This option defines the size of the buffer to store the host username during SMTP authentication with the Server.</span></span> <span data-ttu-id="ef92b-165">Wartość domyślna to 40 bajtów.</span><span class="sxs-lookup"><span data-stu-id="ef92b-165">The default value is 40 bytes.</span></span> 
