---
title: Rozdział 2 — Instalowanie i korzystanie z klienta SNTP usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta SNTP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd917e7e70ce21dbff6c8081c2ff115c0acad8a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821654"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a>Rozdział 2 — Instalowanie i korzystanie z klienta SNTP usługi Azure RTO NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem klienta SNTP usługi Azure RTO NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktu

Protokół SNTP dla NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nxd_sntp_client. c** Plik źródłowy C klienta SNTP  
- **nxd_sntp_client. h** Plik nagłówkowy klienta SNTP  
- **demo_netxduo_sntp_client. c** Demonstracja aplikacja kliencka SNTP  
- **nxd_sntp_client.pdf** Podręcznik użytkownika klienta SNTP NetX Duo  

## <a name="netx-duo-sntp-client-installation"></a>Instalacja klienta SNTP NetX Duo

Aby można było używać SNTP dla NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", następnie pliki klienta SNTP NetX Duo *nxd_sntp_client. c* i *nxd_sntp_client. h* (*nx_sntp_client. c* i *nx_sntp_client. h* w NetX) powinny zostać skopiowane do tego katalogu.

## <a name="using-netx-duo-sntp-client"></a>Korzystanie z klienta SNTP NetX Duo

Korzystanie z klienta SNTP NetX Duo jest proste. W zasadzie kod aplikacji musi zawierać *nxd_sntp_client. h* , po uwzględnieniu *tx_api. h, fx_api. h,* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo. Po dołączeniu *nxd_sntp_client. h* kod aplikacji może następnie wprowadzić wywołania funkcji SNTP w dalszej części tego przewodnika. Aplikacja musi również zawierać *nxd_sntp_client. c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z klienta SNTP NetX Duo.

> [!NOTE]
> Ponieważ klient SNTP NetX Duo korzysta z usług UDP NetX Duo, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem usług SNTP.

## <a name="small-example-system"></a>Mały przykładowy system

Poniżej przedstawiono przykład użycia NetX Duo SNTP. Należy zauważyć, że w tym przykładzie **nie** ma gwarancji, że jest on używany w systemie. Może być konieczne wprowadzenie zmian w określonym systemie i sprzęcie. Na przykład trzeba będzie zastąpić sterownik NetX pamięci RAM rzeczywistą funkcją sterownika. Ten przykład jest przeznaczony wyłącznie do celów demonstracyjnych.

W tym przykładzie jest dołączony plik nagłówka SNTP *nxd_sntp_client. h* . Klient SNTP jest tworzony w "*tx_application_define*". Należy zauważyć, że podczas tworzenia klienta SNTP są opcjonalne funkcje obsługi wynoszącej śmierć i przestępnej drugiej

Tego pokazu można użyć w połączeniu z protokołem IPv6 lub IPv4. Aby uruchomić klienta SNTP za pośrednictwem protokołu IPv6, zdefiniuj USE_IPV6. Protokół IPv6 musi być również włączony w NetX Duo. Host klienta SNTP jest skonfigurowany do sprawdzania poprawności adresów IPv6 oraz usług ICMPv6 i IPv6 w NetX Duo. Zobacz Podręcznik użytkownika programu NetX Duo, aby uzyskać więcej informacji na temat obsługi protokołu IPv6 w programie NetX Duo.

Następnie należy zainicjować klienta protokołu SNTP dla trybu emisji pojedynczej lub emisji.

Klient SNTP początkowo zapisuje aktualizacje czasu serwera do własnej wewnętrznej struktury danych. Ta wartość nie jest taka sama jak czas lokalny urządzenia. Czas lokalny urządzenia można ustawić jako godzinę bazową w kliencie SNTP przed uruchomieniem wątku klienta SNTP. Jest to przydatne, jeśli skonfigurowano klienta SNTP (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP ustawić na NX_FALSE) w celu porównania pierwszej aktualizacji serwera z NX_SNTP_CLIENT_MAX_ADJUSTMENT (wartość domyślna to 180 MS). W przeciwnym razie klient SNTP ustawi początkowy czas lokalny bezpośrednio przy pobieraniu pierwszej aktualizacji z serwera.

Do klienta SNTP jest stosowany czas bazowy przy użyciu usługi *nx_sntp_client_set_local_time* .

Klient SNTP jest uruchamiany odpowiednio w trybie emisji pojedynczej i trybu emisji. W przypadku pewnego interwału (nieco mniej niż interwał sondowania emisji pojedynczej) aplikacja aktualizuje czas lokalny klienta SNTP przy użyciu *nx_sntp_client_set_local_time* z "zegara czasu rzeczywistego", który symulowany przez zwiększenie liczby sekund i milisekund bieżącego czasu. Po każdym interwale aplikacja okresowo sprawdza dostępność aktualizacji na serwerze SNTP. Usługa *nx_sntp_client_receiving _updates* sprawdza, czy klient SNTP aktualnie otrzymuje prawidłowe aktualizacje. W takim przypadku zostanie pobrany najnowszy czas aktualizacji przy użyciu usługi *nx_sntp_client_get_local_time_extended* .

Klienta SNTP można zatrzymać w dowolnym momencie za pomocą usługi *nx_sntp_client_stop* , jeśli na przykład wykryje, że klient SNTP nie otrzymuje już prawidłowych aktualizacji. Aby ponownie uruchomić klienta, aplikacja musi wywoływać usługę emisji pojedynczej lub inicjatora emisji, a następnie wywołać usługi emisji pojedynczej lub emisji. Gdy zadanie wątku klienta SNTP zostało zatrzymane, klient SNTP może przełączyć serwery i tryby protokołu SNTP (emisji pojedynczej lub emisji), jeśli jest to konieczne, np. poprzedni serwer SNTP prawdopodobnie nie działa.

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

Rysunek 1 przykład korzystania z klienta SNTP z NetX Duo

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji służących do definiowania klienta SNTP NetX Duo. Poniższa lista zawiera szczegółowy opis:  
  

**NX_SNTP_CLIENT_THREAD_STACK_SIZE**  
Ta opcja ustawia rozmiar stosu wątków klienta. Domyślny rozmiar klienta SNTP NetX Duo to 2048.

**NX_SNTP_CLIENT_THREAD_TIME_SLICE**  
Ta opcja umożliwia ustawienie wycinka czasu harmonogramu na potrzeby wykonywania wątków klienta. Domyślny rozmiar klienta SNTP NetX Duo to TX_NO_TIME_SLICE.

**NX_SNTP_CLIENT_ THREAD_PRIORITY**  
Ta opcja ustawia priorytet wątku klienta. Wartość domyślna klienta SNTP NetX Duo to 2.

**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**  
Ta opcja ustawia poziom priorytetu, w którym wątek klienta umożliwia przewagę. Domyślna wartość klienta SNTP NetX Duo jest ustawiona na `NX_SNTP_CLIENT_ THREAD_PRIORITY` .

**NX_SNTP_CLIENT_UDP_SOCKET_NAME**  
Ta opcja ustawia nazwę gniazda UDP. Domyślna nazwa gniazda UDP klienta SNTP NetX Duo to "gniazdo klienta SNTP".

**NX_SNTP_CLIENT_UDP_PORT**  
Ustawia port, z którym jest powiązany gniazdo klienta. Domyślnym portem klienta SNTP NetX Duo jest 123.

**NX_SNTP_SERVER_UDP_PORT**  
Jest to port, na którym klient wysyła komunikaty SNTP do serwera SNTP w systemie. Domyślnym portem serwera NetX SNTP jest 123.

**NX_SNTP_CLIENT_TIME_TO_LIVE**  
Określa liczbę routerów, które może przekazać pakiet klienta, zanim zostanie on odrzucony. Domyślny klient SNTP NetX Duo jest ustawiony na 0x80 *.*

**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**  
Maksymalna liczba pakietów UDP (Datagrams), które można umieścić w kolejce w gnieździe klienta NetX Duo SNTP. Odebrane dodatkowe pakiety oznaczają, że wydano najstarsze pakiety. Domyślny klient SNTP NetX Duo jest ustawiony na 5.

**NX_SNTP_CLIENT_PACKET_TIMEOUT**  
Limit czasu dla przydziału pakietu NetX Duo. Domyślny limit czasu pakietu klienta SNTP NetX Duo wynosi 1 s.

**NX_SNTP_CLIENT_NTP_VERSION**  
Wersja SNTP używana przez klienta interfejs API klienta SNTP NetX Duo został oparty na wersji 4. Wartość domyślna to 3.

**NX_SNTP_CLIENT_MIN_NTP_VERSION**  
Najstarsza wersja SNTP, z którą klient będzie mógł współpracować. Wartość domyślna klienta SNTP NetX Duo to wersja 3.

**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**  
Najniższy poziom (najwyższy poziom warstwy) Serwer SNTP, który zostanie zaakceptowany przez klienta. Wartość domyślna klienta SNTP NetX Duo to 2.

**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**  
Minimalne dopasowanie czasu w milisekundach, po których klient będzie miał czas zegara lokalnego. Poniższe zmiany czasu zostaną zignorowane. Wartość domyślna klienta SNTP NetX Duo to 10.

**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**  
Maksymalne dopasowanie czasu (w milisekundach) przez klienta do czasu lokalnego zegara. W przypadku korekt czasowych powyżej tej kwoty dostosowanie zegara lokalnego jest ograniczone do maksymalnego dopasowania czasu. Wartość domyślna klienta SNTP NetX Duo to 180000 (3 minuty).

**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**  
Dzięki temu maksymalne dostosowanie czasu należy uchylić, gdy klient otrzymuje pierwszą aktualizację z serwera czasu. Następnie Maksymalne ustawienie czasu jest wymuszane. Zamierzenie polega na tym, że klient jest zsynchronizowany z zegarem serwera najszybciej, jak to możliwe. Domyślnym ustawieniem klienta SNTP NetX Duo jest NX_TRUE.

**NX_SNTP_CLIENT_MAX_TIME_LAPSE**  
Maksymalny dozwolony czas (w sekundach), który upłynął, bez prawidłowej aktualizacji czasu odebranej przez klienta SNTP. Klient SNTP będzie kontynuował działanie, ale stan serwera SNTP jest ustawiony na NX_FALSE. Wartość domyślna to 7200.


**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**  
Interwał (w sekundach), w którym czasomierz klienta SNTP aktualizuje czas klienta SNTP pozostały od momentu odebrania ostatniej prawidłowej aktualizacji, a klient emisji pojedynczej aktualizuje pozostały czas oczekiwania na sondowanie przed wysłaniem kolejnego żądania aktualizacji SNTP. Wartość domyślna to 1.

**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**  
Początkowy interwał sondowania (w sekundach), w którym klient wysyła żądanie emisji pojedynczej do swojego serwera SNTP. Domyślnym ustawieniem klienta SNTP NetX Duo jest 3600.

**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**  
Współczynnik, za pomocą którego jest zwiększany interwał sondowania emisji pojedynczej przez klienta. Gdy klient nie otrzymuje aktualizacji czasu serwera ani nie otrzymuje wskazań z serwera, który jest tymczasowo niedostępny (np. nie jest jeszcze zsynchronizowany) dla usługi aktualizacji czasowej, spowoduje to zwiększenie bieżącego interwału sondowania przez tę częstotliwość, ale nie do przekroczenia NX_SNTP_CLIENT_MAX_TIME_LAPSE. Wartość domyślna to 2.

**NX_SNTP_CLIENT_RTT_REQUIRED**  
Ta opcja, jeśli jest włączona, wymaga, aby klient SNTP obliczał czas błądzenia komunikatów SNTP w przypadku zastosowania aktualizacji serwera do zegara lokalnego. Wartość domyślna to NX_FALSE (wyłączone).

**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**  
Maksymalne rozproszenie zegara serwera (mikrosekund), które jest miarą precyzji zegara serwera, klient zostanie zaakceptowany. Aby wyłączyć to wymaganie, ustaw maksymalną dyspersję główną na 0x0. Domyślnym ustawieniem klienta SNTP NetX Duo jest 50000.

**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**  
Limit liczby kolejnych nieprawidłowych aktualizacji odebranych z serwera klienta w trybie emisji lub emisji pojedynczej. Po osiągnięciu tego limitu klient ustawia bieżący stan serwera SNTP na nieprawidłowy (NX_FALSE), mimo że będzie nadal próbować otrzymywać aktualizacje z serwera. Wartość domyślna klienta SNTP NetX Duo to 3.

**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**  
Określa, czy klient SNTP w trybie emisji pojedynczej powinien wysyłać swoje pierwsze żądanie SNTP z bieżącym serwerem SNTP po losowym interwale oczekiwania. Jest on używany w przypadkach, gdy liczba klientów SNTP jest uruchamiana jednocześnie w celu ograniczenia przeciążenia ruchu na serwerze SNTP. Wartość domyślna to NX_FALSE.

**NX_SNTP_CLIENT_SLEEP_INTERVAL**  
Przedział czasu, w którym zadanie klienta SNTP jest w stanie uśpienia. Pozwala to wykonywać wywołania interfejsu API aplikacji przez klienta SNTP. Wartość domyślna to 1 znacznik czasomierza.

**NX_SNTP_CURRENT_YEAR**  
Aby wyświetlić datę w formacie rok/miesiąc/Data, należy ustawić tę wartość na równą lub mniejszą od bieżącego roku (nie musi być to rok w trakcie oceniania czasu NTP). Wartość domyślna to 2015.

**NTP_SECONDS_AT_01011999**  
Jest to liczba sekund do pierwszej epoki NTP na głównym zegarze NTP. Jest on zdefiniowany jako 0xBA368E80. Aby wyłączyć wyświetlanie sekund NTP w dacie i godzinie, ustaw wartość zero.
