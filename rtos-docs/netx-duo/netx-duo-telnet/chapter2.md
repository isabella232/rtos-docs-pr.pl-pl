---
title: Rozdział 2 — Instalowanie i używanie programu Azure RTOS NetX Duo Telnet
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTOS NetX Duo Telnet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4781f45dc37f8c48a9f491d6cb67299432f3ae6743d12d9d92134298474182a5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799357"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a>Rozdział 2 — Instalowanie i używanie programu Azure RTOS NetX Duo Telnet

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTOS NetX Duo Telnet.

## <a name="product-distribution"></a>Dystrybucja produktów

Pakiet Azure RTOS NetX Duo Telnet jest dostępny pod numerem <https://github.com/azure-rtos/netxduo> . Pakiet zawiera następujące pliki:

- **nxd_telnet_client.h:** plik nagłówkowy dla klienta Telnet dla NetX Duo
- **nxd_telnet_client.c:** plik źródłowy języka C dla klienta Telnet dla NetX Duo
- **nxd_telnet_server.h:** Plik nagłówka dla serwera Telnet dla NetX Duo
- **nxd_telnet_server.c:** plik źródłowy języka C dla serwera Telnet server for NetX Duo
- **nxd_telnet.pdf:** opis PDF telnetu dla netx duo
- **demo_netxduo_telnet.c:** pokaz NetX Duo Telnet

## <a name="telnet-installation"></a>Instalacja Telnet

Aby można było korzystać z programu Telnet dla netX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Jeśli na przykład program NetX Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* pliki *nxd_telnet_client.h,* *nxd_telnet_client.c,* *nxd_telnet_server.c i nxd_telnet_server.h* powinny zostać skopiowane do tego katalogu.

## <a name="using-telnet"></a>Korzystanie z programu Telnet

Korzystanie z programu Telnet dla netX Duo jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nxd_telnet_server.h* dla aplikacji Serwera Telnet i *nxd_telnet_client.h* dla aplikacji klienckich Telnet po dojecheniu do nich plików *tx_api.h* *i nx_api.h,* aby można było używać threadX i NetX Duo. Gdy *nagłówek zostanie* dołączony, kod aplikacji będzie mógł wykonać wywołania funkcji Telnet określone w dalszej części tego przewodnika. Aplikacja musi również uwzględniać *nxd_telnet_client.c* *i nxd_telnet_server.c w* procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z programu NetX Duo Telnet.

Jeśli nie są wymagane możliwości klienta Telnet, *nxd_telnet_client.c* plik może zostać pominięty.

Należy również pamiętać, że ze względu na to, że telnet korzysta z usług TCP NetX Duo, protokół TCP musi być włączony za *pomocą wywołania nx_tcp_enable* przed użyciem Telnet.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład użycia programu NetX Duo Telnet przedstawiono na rysunku 1.1 poniżej. W tym przykładzie pliki dołączania Telnet *są dostępne* w wierszach 7 i 8. Następnie serwer Telnet jest tworzony w ciągu "*tx_application_define*" w wierszu 146. Należy pamiętać, że bloki sterowania Serwer Telnet i Klient są zdefiniowane jako zmienne globalne w wierszu 23–24 wcześniej.

Przed rozpoczęciem pracy z serwerem Telnet lub klientem muszą oni zweryfikować swój adres IP za pomocą programu NetX Duo. W przypadku połączeń IPv4 jest to realizowane przez krótkie oczekiwanie na zainicjowanie systemu przez sterownik NetX w wierszu 166. W przypadku połączeń IPv6 wymaga to włączenia protokołu IPv6 i ICMPv6 w wierszach 171–172. Klient ustawia globalne i łączy lokalne adresy IPv6 w interfejsie podstawowym w wierszach 181–186 i czeka na zakończenie weryfikacji NetX Duo w tle. Serwer ustawia również swoje globalne adresy lokalne i łączy je z interfejsem podstawowym w wierszach 192–198. Należy pamiętać, że te dwie *usługi, nxd_ipv6_global_address_set* i *nxd_ipv6_linklocal_address_set* są zastępowane nxd_ipv6_address_set *usługą*. Poprzednie dwie usługi są nadal dostępne dla starszych aplikacji NetX Duo, ale ostatecznie przestarzałe. Zachęcamy deweloperów do korzystania z *nxd_ipv6_address_set* zamiast tego.

Po pomyślnej weryfikacji adresu IP w programie NetX Duo serwer Telnet jest uruchomiony w wierszu 215 przy *użyciu nxd_telnet_server_start* service. W wierszu 226 klient Telnet jest tworzony przy użyciu *nx_telnet_client_create* usługi. Następnie łączy się z serwerem Telnet w wierszu 242 dla aplikacji IPv4 i wierszem 238 dla aplikacji IPv6 przy użyciu usług *nxd_telnet_client_connect* *i nx_telnet_client_connect.* Po pomyślnej weryfikacji i nawiązaniu połączenia z serwerem program dokonuje kilku wymian przed rozłączeniem.

```c
/* This is a small demo of TELNET on the high-performance NetX Duo TCP/IP stack.  
       This demo relies on ThreadX and NetX Duo to show a simple TELNET connection,
       send, server echo, and then disconnection from the TELNET server.  */
    
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_telnet_client.h"
#include  "nxd_telnet_server.h"
#define     DEMO_STACK_SIZE         4096    
   
/* Define the ThreadX and NetX object control blocks...  */
TX_THREAD               test_thread;
NX_PACKET_POOL          pool_server;
NX_PACKET_POOL          pool_client;
NX_IP                   ip_server;
NX_IP                   ip_client;
   
/* Define TELNET objects.  */

NX_TELNET_SERVER        my_server;
NX_TELNET_CLIENT        my_client;


#ifdef FEATURE_NX_IPV6

/* Define NetX Duo IP address for the NetX Duo Telnet Server and Client. */

NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;

#endif

#define         SERVER_ADDRESS          IP_ADDRESS(1,2,3,4)
#define         CLIENT_ADDRESS          IP_ADDRESS(1,2,3,5)

/* Define the counters used in the demo application...  */
ULONG                   error_counter;

/* Define timeout in ticks for connecting and sending/receiving data. */

#define                 TELNET_TIMEOUT  200

/* Define function prototypes.  */

void    thread_test_entry(ULONG thread_input);
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define the application's TELNET Server callback routines.  */

void    telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection); 
void    telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection, 
                            NX_PACKET *packet_ptr);
void    telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection);

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
CHAR    *pointer;
UINT    iface_index, address_index;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;
    
    /* Create the main thread.  */
    tx_thread_create(&test_thread, "test thread", thread_test_entry, 0,  
                     pointer, DEMO_STACK_SIZE, 
                     2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;
    
    /* Initialize the NetX system.  */
    nx_system_initialize();
    
    /* Create packet pool.  */
    nx_packet_pool_create(&pool_server, "Server NetX Packet Pool", 600, pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create an IP instance.  */
    nx_ip_create(&ip_server, "Server NetX IP Instance", SERVER_ADDRESS, 
                 0xFFFFFF00UL, &pool_server, _nx_ram_network_driver,
                 pointer, 4096, 1);
    
    pointer =  pointer + 4096;
    
    /* Create another packet pool. */
    nx_packet_pool_create(&pool_client, "Client NetX Packet Pool", 600, 
                          pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create another IP instance.  */
    nx_ip_create(&ip_client, "Client NetX IP Instance", CLIENT_ADDRESS, 
                 0xFFFFFF00UL, &pool_client, _nx_ram_network_driver, 
                 pointer, 4096, 1);
    
    pointer = pointer + 4096;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_server, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_client, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_server);
    nx_tcp_enable(&ip_client);

#ifdef FEATURE_NX_IPV6

    /* Next set the NetX Duo Telnet Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

#endif

    /* Create the NetX Duo TELNET Server.  */
    status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_server, 
                                      pointer, 2048, telnet_new_connection, telnet_receive_data, 
                                      telnet_connection_end);
    
    /* Check for errors.  */
    if (status)
        error_counter++;
    
    return;
}

/* Define the test thread.  */
void    thread_test_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
    
    /* Allow other threads (e.g. IP thread task) to run first. */
    tx_thread_sleep(100);
    
    #ifdef FEATURE_NX_IPV6
    /* Here's where we make the Telnet Client IPv6 enabled. */
    nxd_ipv6_enable(&ip_client);
    nxd_icmp_enable(&ip_client);     
    
    /* Wait till the IP task thread initializes the system. */
    tx_thread_sleep(100);
        
    /* Set up the Client addresses on the Client IP for the primary interface. */
    if_index = 0;
    
    status = nxd_ipv6_address_set(&ip_ client, iface_index, NX_NULL, 10, 
                                  &address_index);
    status = nxd_ipv6_address_set(&ip_ client, iface_index, & client _ip_address, 
                                   64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */
    tx_thread_sleep(400);
    
    /* Set up the Server addresses on the Client IP. */
    iface_index = 0;
    status = nxd_ipv6_address_set (&ip_server, iface_index, NX_NULL, 10, 
                                   &address_index);
    
    status = nxd_ ipv6_address _set(&ip_server, iface_index, & server _ip_address, 
                                     64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */     
    tx_thread_sleep(400);
    
    #endif
    
    /* Start the TELNET Server.  */
    status =  nx_telnet_server_start(&my_server);
    
    /* Check for errors.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Create a TELENT client instance.  */
    status =  nx_telnet_client_create(&my_client, "My TELNET Client", 
                                      &ip_client, 600);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    #ifdef FEATURE_NX_IPV6
    
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 
                                             TELNET_TIMEOUT);
    
    #else
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nx_telnet_client_connect(&my_client, SERVER_ADDRESS, 23,
                                            TELNET_TIMEOUT);
    #endif
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Allocate a packet.  */
    status =  nx_packet_allocate(&pool_client, &my_packet, NX_TCP_PACKET, 
                                  NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Build a simple 1-byte message.  */
    nx_packet_data_append(my_packet, "a", 1, &pool_client, NX_WAIT_FOREVER);
    
    /* Send the packet to the TELNET Server.  */
    status =  nx_telnet_client_packet_send(&my_client, my_packet, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Pickup the Server header.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the Server's banner
        message sent by the Server callback function below.  Just
        release it for this demo.  */
    nx_packet_release(my_packet);
    
    /* Pickup the Server echo of the character.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the character 'a' that
        we sent earlier.  Just release the packet for now.  */
    nx_packet_release(my_packet);
    
    /* Now disconnect form the TELNET Server.  */
    status =  nx_telnet_client_disconnect(&my_client, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Delete the TELNET Client.  */
    status =  nx_telnet_client_delete(&my_client);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
}

/* This routine is called by the NetX Telnet Server whenever a new Telnet client 
    connection is established.  */
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{

UINT        status;
NX_PACKET   *packet_ptr;

    /* Allocate a packet for client greeting. */
    status =  nx_packet_allocate(&pool_server, &packet_ptr, NX_TCP_PACKET, 
                                  NX_NO_WAIT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Build a banner message and a prompt.  */
    nx_packet_data_append(packet_ptr,"**** Welcome to NetX TELNET Server ****\r\n\r\n\r\n", 45,                            
                         &pool_server, NX_NO_WAIT);

    nx_packet_data_append(packet_ptr, "NETX> ", 6, &pool_server, NX_NO_WAIT);
    
    /* Send the packet to the client.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }
    return;
}

/* This routine is called by the NetX Telnet Server whenever data is present on a 
    Telnet client connection.  */          
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection,
                          NX_PACKET *packet_ptr)
{

UINT    status;
UCHAR   alpha;

    /* This demo echoes the character back; on <cr,lf> sends a new prompt back to 
        the client.  A real system would likely buffer the character(s) received in a 
        buffer associated with the supplied logical connection and process it.  */

    /* Just throw away carriage returns.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\r') && (packet_ptr -> nx_packet_length == 1))
    {
        printf("telnet server received just a CRLF\n");

        nx_packet_release(packet_ptr);
        return;
    }

    /* Setup new line on line feed.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\n') || (packet_ptr -> nx_packet_prepend_ptr[1] == '\n'))
    {
        /* Clean up the packet.  */
        packet_ptr -> nx_packet_length =  0;
        packet_ptr -> nx_packet_prepend_ptr =  packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;
        packet_ptr -> nx_packet_append_ptr =   packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;

        /* Build the next prompt.  */
        nx_packet_data_append(packet_ptr, "\r\nNETX> ", 8, &pool_server, 
                              NX_NO_WAIT);

        /* Send the packet to the client.  */
        status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                               packet_ptr, TELNET_TIMEOUT);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            nx_packet_release(packet_ptr);
        }
        return;
    }

    /* Pickup first character (usually only one from client).  */
    alpha =  packet_ptr -> nx_packet_prepend_ptr[0];

    /* Echo character.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }

    /* Check for a disconnection.  */
    if (alpha == 'q')
    {
        /* Initiate server disconnection.  */
        nx_telnet_server_disconnect(server_ptr, logical_connection);
    }
}


/* This routine is called by the NetX Telnet Server when the client disconnects.  */
void  telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{
    /* Cleanup any application specific connection or buffer information.  */
    return;
}
```

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia telnetu dla netx duo. Te #defines można ustawić przez aplikację przed dodaniem do nich *nxd_telnet_server.h* i *nxd_telnet_client.h.*

Poniżej znajduje się lista wszystkich opcji, z których każda jest szczegółowo opisana:  
  
- **NX_DISABLE_ERROR_CHECKING:** zdefiniowana, ta opcja usuwa podstawowe sprawdzanie błędów Telnet. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_TELNET_MAX_CLIENTS:** maksymalna liczba klientów Telnet obsługiwanych przez wątek serwera. Domyślnie ta wartość jest zdefiniowana jako 4, aby określić maksymalnie 4 klientów na raz.
- **NX_TELNET_SERVER_PRIORITY:** priorytet wątku serwera Telnet. Domyślnie ta wartość jest zdefiniowana jako 16, aby określić priorytet 16.
- **NX_TELNET_TOS:** typ usługi wymagany dla żądań TCP Telnet. Domyślnie ta wartość jest zdefiniowana jako NX_IP_NORMAL, aby wskazać  
normalna usługa pakietów IP.
- **NX_TELNET_FRAGMENT_OPTION:** włącz fragment dla żądań TCP Telnet. Domyślnie ta wartość jest NX_DONT_FRAGMENT fragmentowanie TCP Telnet.
- **NX_TELNET_SERVER_WINDOW_SIZE:** rozmiar okna gniazda serwera. Domyślnie ta wartość to 2048 bajtów.
- **NX_TELNET_TIME_TO_LIVE:** określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.
- **NX_TELNET_SERVER_TIMEOUT:** określa liczbę znaczników ThreadX, dla których usługi wewnętrzne będą wstrzymywane. Wartość domyślna to 10 sekund.
- **NX_TELNET_ACTIVITY_TIMEOUT:** określa liczbę sekund, które mogą upłynąć bez żadnej aktywności, zanim serwer rozłączy połączenie klienta. Wartość domyślna to 600 sekund.
- **NX_TELNET_TIMEOUT_PERIOD:** Określa liczbę sekund między sprawdzeniem przecje aktywności klienta. Wartość domyślna to 60 sekund.
- **NX_TELNET_SERVER_OPTION_DISABLE:** zdefiniowana, negocjacja opcji Telnet jest wyłączona. Domyślnie ta opcja nie jest zdefiniowana.
- **NX_TELNET_SERVER_USER_CREATE_PACKET_POOL:** jeśli jest zdefiniowana, pula pakietów serwera Telnet musi zostać utworzona zewnętrznie. Jest to istotne tylko wtedy, NX_TELNET_SERVER_OPTION_DISABLE nie jest zdefiniowany. Domyślnie ta opcja nie jest zdefiniowana, a wątek serwera Telnet tworzy własną pulę pakietów.
- **NX_TELNET_SERVER_PACKET_PAYLOAD:** definiuje rozmiar ładunku pakietu utworzonego przez serwer Telnet na czas negocjacji opcji. Należy pamiętać, że serwer Telnet tworzy tę pulę pakietów tylko wtedy, NX_TELNET_SERVER _OPTION_DISABLE nie jest zdefiniowany (opcje Telnet są włączone). Wartość domyślna tej opcji to 300.
- **NX_TELNET_SERVER_PACKET_POOL_SIZE:** definiuje rozmiar puli pakietów serwera Telnet używanej do negocjacji Telnet. Należy pamiętać, że serwer Telnet tworzy tę pulę pakietów tylko wtedy, NX_TELNET_SERVER _OPTION_DISABLE nie jest zdefiniowany (opcje Telnet są włączone). Wartość domyślna tej opcji to 2048 \~ (5–6 pakietów).
