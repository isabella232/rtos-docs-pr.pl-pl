---
title: Rozdział 2 — Instalowanie i używanie klienta Azure RTOS NetX Duo SNTP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem klienta NetX Duo SNTP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2058875c08d64e2c16f67b48323814ec77ec96882eec26aaf2c9454459511db3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799051"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a>Rozdział 2 — Instalowanie i używanie klienta Azure RTOS NetX Duo SNTP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem klienta Azure RTOS NetX Duo SNTP.

## <a name="product-distribution"></a>Dystrybucja produktów

Protokół SNTP dla netX Duo jest dostępny na stronie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nxd_sntp_client.c** Plik źródłowy klienta SNTP C  
- **nxd_sntp_client.h** Plik nagłówka klienta SNTP  
- **demo_netxduo_sntp_client.c** Pokaz aplikacji klienckiej SNTP  
- **nxd_sntp_client.pdf** Podręcznik użytkownika klienta NetX Duo SNTP  

## <a name="netx-duo-sntp-client-installation"></a>Instalacja klienta NetX Duo SNTP

Aby można było używać protokołu SNTP dla netX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano aplikację NetX Duo. Jeśli na przykład netx Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki klienta NetX Duo SNTP *nxd_sntp_client.c* i *nxd_sntp_client.h* (*nx_sntp_client.c* i *nx_sntp_client.h* in NetX).

## <a name="using-netx-duo-sntp-client"></a>Korzystanie z klienta NetX Duo SNTP

Korzystanie z klienta NetX Duo SNTP jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nxd_sntp_client.h* po dołączyć elementy *tx_api.h, fx_api.h* i *nx_api.h,* aby można było używać odpowiednio threadX i NetX Duo. Po *nxd_sntp_client.h* kod aplikacji może następnie wykonać wywołania funkcji SNTP określone w dalszej części tego przewodnika. Aplikacja musi również *uwzględniać nxd_sntp_client.c* w procesie kompilacji. Te pliki muszą zostać skompilowane w taki sam sposób, jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z klienta NetX Duo SNTP.

> [!NOTE]
> Ponieważ klient NetX Duo SNTP korzysta z usług NetX Duo UDP, należy włączyć protokół UDP za pomocą *wywołania nx_udp_enable* przed użyciem usług SNTP.

## <a name="small-example-system"></a>Mały przykładowy system

Poniżej przedstawiono przykład sposobu korzystania z funkcji NetX Duo SNTP. Należy pamiętać, że ten przykład **nie ma** gwarancji, że będzie działać tak, jak w systemie. Może być konieczne dostosowanie określonego systemu i sprzętu. Na przykład należy zastąpić sterownik NetX ram rzeczywistą funkcją sterownika. Ten przykład jest przeznaczony wyłącznie do celów demonstracyjnych.

W tym przykładzie dołączony jest plik nagłówkowy SNTP *nxd_sntp_client.h.* Klient SNTP jest tworzony w *tx_application_define*". Należy pamiętać, że podczas tworzenia klienta SNTP funkcje obsługi zgonu i przestępnych sekund są opcjonalne.

Tej wersji demonstracyjnej można używać z protokołu IPv6 lub IPv4. Aby uruchomić klienta SNTP za pośrednictwem protokołu IPv6, zdefiniuj USE_IPV6. Protokół IPv6 musi być również włączony w programie NetX Duo. Host klienta SNTP jest ustawiony do sprawdzania poprawności adresów IPv6 oraz usług ICMPv6 i IPv6 w NetX Duo. Aby uzyskać więcej informacji na temat obsługi protokołu IPv6 w netx duo, zobacz NetX Duo User Guide (Podręcznik użytkownika netX Duo).

Następnie należy zainicjować klienta SNTP dla trybu emisji pojedynczej lub emisji.

Klient SNTP początkowo zapisuje aktualizacje czasu serwera we własnej wewnętrznej strukturze danych. To nie to samo co czas lokalny urządzenia. Czas lokalny urządzenia można ustawić jako czas punktu odniesienia w kliencie SNTP przed uruchomieniem wątku klienta SNTP. Jest to przydatne, jeśli klient SNTP jest skonfigurowany (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP ustawiony na NX_FALSE), aby porównać pierwszą aktualizację serwera z NX_SNTP_CLIENT_MAX_ADJUSTMENT (wartość domyślna: 180 milisekund). W przeciwnym razie klient SNTP ustawi początkowy czas lokalny bezpośrednio po pobieraniu pierwszej aktualizacji z serwera.

Czas odniesienia jest stosowany do klienta SNTP przy użyciu *nx_sntp_client_set_local_time* usługi.

Klient SNTP jest uruchomiony odpowiednio dla trybu emisji pojedynczej i emisji. W określonym *interwale*(nieco krótszym niż interwał sondowania emisji pojedynczej) aplikacja aktualizuje lokalny czas klienta SNTP przy użyciu zegara nx_sntp_client_set_local_time z "zegara czasu rzeczywistego", który symuluje się przez zwiększanie sekund i milisekund bieżącego czasu. Po każdym interwale aplikacja okresowo sprawdza, czy na serwerze SNTP są dostępne aktualizacje. Usługa *nx_sntp_client_receiving _updates* sprawdza, czy klient SNTP obecnie otrzymuje prawidłowe aktualizacje. Jeśli tak, pobierze ona najnowszy czas aktualizacji przy użyciu *nx_sntp_client_get_local_time_extended* service.

Klienta SNTP można zatrzymać w dowolnym momencie przy użyciu usługi *nx_sntp_client_stop,* jeśli na przykład wykryje, że klient SNTP nie otrzymuje już prawidłowych aktualizacji. Aby ponownie uruchomić klienta, aplikacja musi wywołać usługę emisji pojedynczej lub emisji, a następnie wywołać usługi uruchamiania emisji pojedynczej lub emisji. Podczas zatrzymania zadania wątku klienta SNTP klient SNTP może w razie potrzeby przełączać serwery i tryby SNTP (emisji pojedynczej lub emisji), np. poprzedni serwer SNTP wydaje się nie działać.

```c
/* 
   This is a small demo of the NetX SNTP Client on the high-performance NetX
   TCP/IP stack. This demo relies on Thread, NetX and NetX SNTP Client API to
   execute the Simple Network Time Protocol in unicast and broadcast modes.  
 */

#include <stdio.h>
#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_sntp_client.h"
                
/* Define SNTP packet size. */
#define NX_SNTP_CLIENT_PACKET_SIZE      (NX_UDP_PACKET + 100)

/* Define SNTP packet pool size. */
#define NX_SNTP_CLIENT_PACKET_POOL_SIZE      (4 * (NX_SNTP_CLIENT_PACKET_SIZE + 
                                                            sizeof(NX_PACKET)))

/* Define how often the demo checks for SNTP updates. */
#define DEMO_PERIODIC_CHECK_INTERVAL      (1 * NX_IP_PERIODIC_RATE) 

/* Define how often we check on SNTP server status. 
   We expect updates from the SNTP server about every hour using 
   the SNTP Client defaults. For testing
   make this (much) shorter. */
#define CHECK_SNTP_UPDATES_TIMEOUT       (180 * NX_IP_PERIODIC_RATE) 

/* Set up generic network driver for demo program. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Application defined services of the NetX SNTP Client. */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator);
UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, 
                                        UINT KOD_code);
VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time);


/* Set up client thread and network resources. */

NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;
TX_THREAD           demo_client_thread;
NX_SNTP_CLIENT      demo_sntp_client;
TX_EVENT_FLAGS_GROUP sntp_flags;

#define DEMO_SNTP_UPDATE_EVENT  1

/* Configure the SNTP Client to use IPv6. If not enabled, the 
   Client will use IPv4.  Note: IPv6 must be enabled in NetX Duo
   for the Client to communicate over IPv6.    */
#ifdef FEATURE_NX_IPV6
/* #define USE_IPV6 */
#endif /* FEATURE_NX_IPV6 */


/* Configure the SNTP Client to use unicast SNTP. */
#define USE_UNICAST


#define CLIENT_IP_ADDRESS       IP_ADDRESS(192,2,2,66)
#define SERVER_IP_ADDRESS       IP_ADDRESS(192,2,2,92)
#define SERVER_IP_ADDRESS_2     SERVER_IP_ADDRESS

/* Set up the SNTP network and address index; */
UINT     iface_index =0;
UINT     prefix = 64;   
UINT     address_index;

/* Set up client thread entry point. */
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT     status;
UCHAR    *free_memory_pointer;


    free_memory_pointer = (UCHAR *)first_unused_memory;

    /* Create client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool, 
                                "SNTP Client Packet Pool",
                                NX_SNTP_CLIENT_PACKET_SIZE, 
                                free_memory_pointer, 
                                NX_SNTP_CLIENT_PACKET_POOL_SIZE);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + NX_SNTP_CLIENT_PACKET_POOL_SIZE;

    /* Create Client IP instances */
    status = nx_ip_create(&client_ip, "SNTP IP Instance", 
                                        CLIENT_IP_ADDRESS, 
                                        0xFFFFFF00UL, 
                                        &client_packet_pool, 
                                       _nx_ram_network_driver, 
                                       free_memory_pointer, 2048, 1);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    free_memory_pointer =  free_memory_pointer + 2048;

#ifndef NX_DISABLE_IPV4
    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 2048);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;
    
    /* Enable UDP for client. */
    status =  nx_udp_enable(&client_ip);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

#ifndef NX_DISABLE_IPV4
    status = nx_icmp_enable(&client_ip);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "SNTP Client Thread", 
                                                demo_client_thread_entry, 
                                              (ULONG)(&demo_sntp_client), 
                                                free_memory_pointer, 2048, 
                                                  4, 4, TX_NO_TIME_SLICE, 
                                                        TX_DONT_START);

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Create the event flags. */
    status = tx_event_flags_create(&sntp_flags, "SNTP event flags");

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* set the SNTP network interface to the primary interface. */
    iface_index = 0;

    /* Create the SNTP Client to run in broadcast mode.. */
status =  nx_sntp_client_create(&demo_sntp_client, &client_ip,
                           iface_index, &client_packet_pool,  
                               leap_second_handler, 
                               kiss_of_death_handler, 
                               NULL /* no random_number_generator callback */);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        /* Bail out!*/
        return;
    }

    tx_thread_resume(&demo_client_thread);

    return;
}

/* Define size of buffer to display client's local time. */
#define BUFSIZE 50

/* Define the client thread.  */
void    demo_client_thread_entry(ULONG info)
{

UINT   status;
UINT   spin;
UINT   server_status;
ULONG  base_seconds;
ULONG  base_fraction;
ULONG  seconds, milliseconds, microseconds, fraction;
UINT   wait = 0;
UINT   error_counter = 0;
ULONG  events = 0;
#ifdef USE_IPV6
NXD_ADDRESS sntp_server_address;
NXD_ADDRESS client_ip_address;
#endif

    NX_PARAMETER_NOT_USED(info);

    /* Give other threads (IP instance) initialize first. */
    tx_thread_sleep(NX_IP_PERIODIC_RATE); 

#ifdef USE_IPV6
    /* Set up IPv6 services. */
    status = nxd_ipv6_enable(&client_ip);

    status += nxd_icmp_enable(&client_ip);

    if (status  != NX_SUCCESS)
        return;

    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Set the IPv6 server address. */
    sntp_server_address.nxd_ip_address.v6[0] = 0x20010db8;  
    sntp_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    sntp_server_address.nxd_ip_address.v6[2] = 0x0;
    sntp_server_address.nxd_ip_address.v6[3] = 0x00000106;
    sntp_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address. */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, NULL);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

     /* Set the host global IP address. We are assuming a 64 
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, 
                                        &client_ip_address, 
                                    prefix, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

    /* Wait while NetX Duo validates the global and link local addresses. */
    tx_thread_sleep(5 * NX_IP_PERIODIC_RATE);

#endif

    /* Setup time update callback function. */
    nx_sntp_client_set_time_update_notify(&demo_sntp_client, 
                                        time_update_callback);

    /* Set up client time updates depending on mode. */
#ifdef USE_UNICAST

    /* Initialize the Client for unicast mode to 
       poll the SNTP server once an hour. */
#ifdef USE_IPV6
/* Use the duo service to set up the Client and set the IPv6 SNTP server.
   Note: this can take either an IPv4 or IPv6 address. */
    status = nxd_sntp_client_initialize_unicast(&demo_sntp_client, 
                                            &sntp_server_address);
#else
    /* Use the IPv4 service to set up the Client and set the IPv4 SNTP server. */
    status = nx_sntp_client_initialize_unicast(&demo_sntp_client, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */


#else   /* Broadcast mode */

/* Initialize the Client for broadcast mode, no roundtrip calculation
   required and a broadcast SNTP service. */
#ifdef USE_IPV6
    /* Use the duo service to initialize the Client 
       and set IPv6 SNTP all hosts multicast address. 
       (Note: This can take either an IPv4 or IPv6 address.)*/
    status = nxd_sntp_client_initialize_broadcast(&demo_sntp_client, 
                                                &sntp_server_address, 
                                                            NX_NULL);
#else

    /* Use the IPv4 service to initialize the Client and set 
       IPv4 SNTP broadcast address. */
    status = nx_sntp_client_initialize_broadcast(&demo_sntp_client,  
                                                NX_NULL, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */
#endif  /* USE_UNICAST */

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the base time which is approximately the number of seconds since
       the turn of the last century. If this is not available in SNTP format,
       the nx_sntp_client_utility_add_msecs_to_ntp_time service can convert
       milliseconds to fraction.  For how to compute NTP seconds from real
   time, read the NetX SNTP User Guide. Otherwise set the base time to 
   zero and set NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP to NX_TRUE for
       the SNTP CLient to accept the first time update without applying a
       minimum or maximum adjustment parameters
      (NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT and
       NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT). */

    base_seconds =  0xd2c96b90;  /* Jan 24, 2012 UTC */
    base_fraction = 0xa132db1e;

    /* Apply to the SNTP Client local time.  */
status = nx_sntp_client_set_local_time(&demo_sntp_client, base_seconds,
                                base_fraction);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Run whichever service the client is configured for. */
#ifdef USE_UNICAST
    status = nx_sntp_client_run_unicast(&demo_sntp_client);
#else
    status = nx_sntp_client_run_broadcast(&demo_sntp_client);
#endif  /* USE_UNICAST */

    if (status != NX_SUCCESS)
    {
        return;
    }

    spin = NX_TRUE;

    /* Now check periodically for time changes. */
    while(spin)
    {
        /* Wait for a server update event. */
        tx_event_flags_get(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, 
                                          TX_OR_CLEAR, &events, 
                                 DEMO_PERIODIC_CHECK_INTERVAL);

        if (events == DEMO_SNTP_UPDATE_EVENT)
        {

            /* Check for valid SNTP server status. */
            status = nx_sntp_client_receiving_updates(&demo_sntp_client,
                                               &server_status);

            if ((status != NX_SUCCESS) || (server_status == NX_FALSE))
            {

                /* We do not have a valid update. Skip processing any time
                   data. If this happens repeatedly, consider stopping the
                   SNTP Client thread, picking another SNTP server and
                   resuming the SNTP Client thread task (more details about
                   that in the comments at the end of this function).
                 
                   If SNTP Client configurable parameters are too restrictive,
                   such as Max Adjustment, that may also cause valid server
                   updates to be rejected. Configurable parameters, however,
                   cannot be changed at run time.
                 */
                 
                continue;
            }

            /* We have a valid update.  Get the SNTP Client time.  */
            status = nx_sntp_client_get_local_time_extended(&demo_sntp_client, 
                                                    &seconds, &fraction,  
                                                    NX_NULL, 0); 

            /* Convert fraction to microseconds. */
            nx_sntp_client_utility_fraction_to_usecs(fraction, &microseconds);

            milliseconds = ((microseconds + 500) / 1000);

            if (status != NX_SUCCESS)
            {
                printf("Internal error with getting local time 0x%x\n", 
                       status);
                error_counter++;
            }
            else
            {
                printf("\nSNTP updated\n");
                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }

            /* Clear all events in our event flag. */
            events = 0;
        }
        else
        {

            /* No SNTP update event.             
               In the meantime, if we have an RTC we might want to check
               its notion of time. In this demo, we simulate the passage of 
               time on our 'RTC' really just the CPU counter, assuming that 
               seconds and milliseconds have previously been set to a base 
              (starting) time (as was the SNTP Client before running it) 
             */

            seconds += 1;
            milliseconds += 1;

            /* Update our timer. */
            wait += DEMO_PERIODIC_CHECK_INTERVAL;

            /* Check if it is time to display the local 'RTC' time. */
            if (wait >= CHECK_SNTP_UPDATES_TIMEOUT)
            {
                /* It is. Reset the timeout and print local time. */
                wait = 0;

                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }           
        }
    }

/* We can stop the SNTP service if for example we think the SNTP server 
   has stopped sending updates.
     
       To restart the SNTP Client, simply call the
       nx_sntp_client_initialize_unicast or
       nx_sntp_client_initialize_broadcast using another SNTP server IP
       address as input, and resume the SNTP Client by calling
       nx_sntp_client_run_unicast or
       nx_sntp_client_run_braodcast. */
    status = nx_sntp_client_stop(&demo_sntp_client);

    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* When done with the SNTP Client, we delete it */
    status = nx_sntp_client_delete(&demo_sntp_client);

    return;
}


/* This application defined handler for handling an 
   impending leap second is not required by 
   the SNTP Client. The default handler below only logs the
   event for every time stamp received with the 
   leap indicator set.  */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator)
{
    NX_PARAMETER_NOT_USED(client_ptr);
    NX_PARAMETER_NOT_USED(leap_indicator);

    /* Handle the leap second handler... */

    return NX_SUCCESS;
}

/* This application defined handler for handling 
   a Kiss of Death packet is not required by the SNTP Client. 
   A KOD handler should determine if the Client task should continue vs. 
   abort sending/receiving time data from its current time server, 
   and if aborting if it should remove
   the server from its active server list. 

   Note that the KOD list of codes is subject to change. The list
   below is current at the time of this software release. */

UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, UINT KOD_code)
{

UINT    remove_server_from_list = NX_FALSE;
UINT    status = NX_SUCCESS;

    NX_PARAMETER_NOT_USED(client_ptr);

    /* Handle kiss of death by code group. */
    switch (KOD_code)
    {

        case NX_SNTP_KOD_RATE:
        case NX_SNTP_KOD_NOT_INIT:
        case NX_SNTP_KOD_STEP:

            /* Find another server while this one 
               is temporarily out of service.  */
            status =  NX_SNTP_KOD_SERVER_NOT_AVAILABLE;

        break;

        case NX_SNTP_KOD_AUTH_FAIL:
        case NX_SNTP_KOD_NO_KEY:
        case NX_SNTP_KOD_CRYP_FAIL:

            /* These indicate the server will not 
               service client with time updates
               without successful authentication. */


            remove_server_from_list =  NX_TRUE;

        break;


        default:

            /* All other codes. Remove server 
               before resuming time updates. */

            remove_server_from_list =  NX_TRUE;
        break;
    }

    /* Removing the server from the active server list? */
    if (remove_server_from_list)
    {

        /* Let the caller know it has to bail on 
           this server before resuming service. */
        status = NX_SNTP_KOD_REMOVE_SERVER;
    }

    return status;
}


/* This application defined handler for notifying SNTP time update event.  */

VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time)
{
    tx_event_flags_set(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, TX_OR);
}

```

Rysunek 1 Przykład użycia klienta SNTP z NetX Duo

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji definiowania klienta NetX Duo SNTP. Na poniższej liście szczegółowo opisano poszczególne z nich:  
  

**NX_SNTP_CLIENT_THREAD_STACK_SIZE**  
Ta opcja ustawia rozmiar stosu wątku klienta. Domyślny rozmiar klienta NetX Duo SNTP to 2048.

**NX_SNTP_CLIENT_THREAD_TIME_SLICE**  
Ta opcja ustawia wycinek czasu harmonogramu zezwala na wykonywanie wątków klienta. Domyślny rozmiar klienta NetX Duo SNTP to TX_NO_TIME_SLICE.

**NX_SNTP_CLIENT_ THREAD_PRIORITY**  
Ta opcja ustawia priorytet wątku klienta. Wartość domyślna klienta NetX Duo SNTP to 2.

**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**  
Ta opcja ustawia poziom priorytetu, z którym wątek klienta zezwala na wywłaszkę. Domyślna wartość klienta NetX Duo SNTP to `NX_SNTP_CLIENT_ THREAD_PRIORITY` .

**NX_SNTP_CLIENT_UDP_SOCKET_NAME**  
Ta opcja ustawia nazwę gniazda UDP. Domyślna nazwa gniazda UDP klienta NetX Duo SNTP to "Gniazdo klienta SNTP".

**NX_SNTP_CLIENT_UDP_PORT**  
To ustawienie określa port, z którym jest powiązane gniazdo klienta. Domyślny port klienta NetX Duo SNTP to 123.

**NX_SNTP_SERVER_UDP_PORT**  
Jest to port, na którym klient wysyła komunikaty SNTP do serwera SNTP. Domyślny port serwera NetX SNTP to 123.

**NX_SNTP_CLIENT_TIME_TO_LIVE**  
Określa liczbę routerów, które pakiet klienta może przekazać, zanim zostanie odrzucony. Domyślny klient NetX Duo SNTP jest ustawiony na wartość 0x80 *.*

**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**  
Maksymalna liczba pakietów UDP (datagramów), które można dodać do kolejki w gnieździe klienta NetX Duo SNTP. Dodatkowe odebrane pakiety oznaczają, że są zwalniane najstarsze pakiety. Domyślny klient NetX Duo SNTP ma wartość 5.

**NX_SNTP_CLIENT_PACKET_TIMEOUT**  
Utracą czas alokacji pakietów NetX Duo. Domyślny limit czasu pakietu klienta NetX Duo SNTP wynosi 1 sekundę.

**NX_SNTP_CLIENT_NTP_VERSION**  
Wersja SNTP używana przez klienta Interfejs API klienta NetX Duo SNTP bazuje na wersji 4. Wartość domyślna to 3.

**NX_SNTP_CLIENT_MIN_NTP_VERSION**  
Najstarsza wersja protokołu SNTP, z która będzie mogła współpracować klient. Wartość domyślna klienta NetX Duo SNTP to Wersja 3.

**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**  
Najniższy poziom (najwyższy poziom warstwy liczbowej) warstwy serwera SNTP klienta będzie akceptować. Wartość domyślna klienta NetX Duo SNTP to 2.

**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**  
Minimalny czas korekty w milisekundach klienta spowoduje jego czas zegara lokalnego. Korekty czasu poniżej tej wartości zostaną zignorowane. Wartość domyślna klienta NetX Duo SNTP to 10.

**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**  
Maksymalny czas korekty w milisekundach klienta spowoduje jego czas zegara lokalnego. W przypadku korekt czasu powyżej tej kwoty dostosowanie zegara lokalnego jest ograniczone do korekty maksymalnego czasu. Wartość domyślna klienta NetX Duo SNTP to 180000 (3 minuty).

**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**  
Pozwala to na rezygnację z korekty maksymalnego czasu, gdy klient otrzyma pierwszą aktualizację ze swojego serwera czasu. Następnie jest wymuszane dostosowanie maksymalnego czasu. Celem jest jak najszybciej pobrać klienta w synchronizowanie z zegarem serwera. Domyślnym ustawieniem klienta NetX Duo SNTP jest NX_TRUE.

**NX_SNTP_CLIENT_MAX_TIME_LAPSE**  
Maksymalny dopuszczalny czas (w sekundach) upłynął bez ważnej aktualizacji czasu otrzymanej przez klienta SNTP. Klient SNTP będzie kontynuować działanie, ale stan serwera SNTP jest ustawiony na NX_FALSE. Wartość domyślna to 7200.


**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**  
Interwał (w sekundach), w którym czasomierz klienta SNTP aktualizuje czas klienta SNTP pozostały od ostatniej otrzymanej prawidłowej aktualizacji, a klient emisji pojedynczej aktualizuje pozostały czas interwału sondowania przed wysłaniem następnego żądania aktualizacji SNTP. Wartość domyślna to 1.

**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**  
Interwał sondowania początkowego (w sekundach), w którym klient wysyła żądanie emisji pojedynczej do serwera SNTP. Wartość domyślna klienta NetX Duo SNTP to 3600.

**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**  
Współczynnik, o który zwiększa się bieżący interwał sondowania emisji pojedynczej klienta. Jeśli klient nie otrzyma aktualizacji czasu serwera lub otrzyma od serwera oznaczenia, że jest tymczasowo niedostępny (np. nie jest jeszcze zsynchronizowany) dla usługi aktualizacji czasu, spowoduje to zwiększenie bieżącego interwału sondowania o tę szybkość do wartości nieprzekraczającej NX_SNTP_CLIENT_MAX_TIME_LAPSE. Wartość domyślna to 2.

**NX_SNTP_CLIENT_RTT_REQUIRED**  
Ta opcja, jeśli jest włączona, wymaga, aby klient SNTP obliczał czas rundy komunikatów SNTP podczas stosowania aktualizacji serwera do zegara lokalnego. Wartość domyślna to NX_FALSE (wyłączona).

**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**  
Maksymalne rozproszenie zegara serwera (mikrosekund), które jest miarą dokładności zegara serwera, klient zaakceptuje. Aby wyłączyć to wymaganie, ustaw maksymalne rozproszenie głównego na 0x0. Wartość domyślna klienta NetX Duo SNTP to 50000.

**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**  
Limit liczby kolejnych nieprawidłowych aktualizacji odebranych z serwera klienta w trybie emisji pojedynczej lub emisji pojedynczej. Po osiągnięciu tego limitu klient ustawia bieżący stan serwera SNTP na nieprawidłowy (NX_FALSE), mimo że nadal będzie próbował otrzymywać aktualizacje z serwera. Wartość domyślna klienta NetX Duo SNTP to 3.

**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**  
Określa, czy klient SNTP w trybie emisji pojedynczej powinien wysłać pierwsze żądanie SNTP z bieżącym serwerem SNTP po losowym interwale oczekiwania. Jest on używany w przypadkach, gdy znaczna liczba klientów SNTP jest uruchamiana jednocześnie, aby ograniczyć przeciążenie ruchu na serwerze SNTP. Wartość domyślna to NX_FALSE.

**NX_SNTP_CLIENT_SLEEP_INTERVAL**  
Przedział czasu, w którym zadanie klienta SNTP jest uśpięce. Dzięki temu wywołania interfejsu API aplikacji mogą być wykonywane przez klienta SNTP. Wartość domyślna to 1 takt czasomierza.

**NX_SNTP_CURRENT_YEAR**  
Aby wyświetlić datę w formacie rok/miesiąc/data, ustaw tę wartość na wartość równą lub mniejszą niż bieżący rok (nie muszą być takie same jak w szacowanym czasie NTP). Wartość domyślna to 2015.

**NTP_SECONDS_AT_01011999**  
Jest to liczba sekund do pierwszej epoki NTP na główny zegar NTP. Jest on zdefiniowany jako 0xBA368E80. Aby wyłączyć wyświetlanie NTP sekund do daty i czasu, ustaw zero.
