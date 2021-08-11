---
title: Rozdział 2 — Instalacja i korzystanie z protokołu FTP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfigurowaniem i użyciem usług FTP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bef7dcce9354e6653dd92c5a47a29d120268faeb4a30b4d146c9e10d2d69084e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790228"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a>Rozdział 2 — Instalacja i korzystanie z protokołu FTP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfigurowaniem i użyciem usług FTP NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktów

Protokół FTP NetX Duo jest dostępny pod witrynie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nxd_ftp_client.h** Plik nagłówkowy klienta FTP NetX Duo
- **nxd_ftp_client.c** Plik źródłowy języka C dla klienta FTP NetX Duo
- **nxd_ftp_server.h** Plik nagłówkowy serwera FTP NetX Duo
- **nxd_ftp_server.c** Plik źródłowy języka C dla serwera FTP NetX Duo
- **filex_stub.h** Plik wycinki, jeśli plik FileX nie istnieje
- **nxd_ftp.pdf** Opis w formacie PDF protokołu FTP dla netx duo
- **demo_netxduo_ftp.c** Pokazowy system FTP

## <a name="netx-duo-ftp-installation"></a>Instalacja protokołu FTP w programie NetX Duo

Aby można było korzystać z interfejsu API FTP NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Jeśli na przykład netx Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* pliki *nxd_ftp_client.h* i *nxd_ftp_client.c* powinny zostać skopiowane do tego katalogu dla aplikacji klienckich FTP, a pliki *nxd_ftp_server.h* i *nxd_ftp_server.c* powinny zostać skopiowane do tego katalogu dla aplikacji serwera FTP.

## <a name="using-netx-duo-ftp"></a>Korzystanie z protokołu FTP NetX Duo

Korzystanie z interfejsu API FTP NetX Duo jest łatwe. Zasadniczo kod aplikacji musi zawierać plik *nxd_ftp_client.h* dla aplikacji klienckich FTP lub plik *nxd_ftp_server dla* aplikacji serwera FTP, po dołączyć pliki *tx_api.h, fx_api.h* i *nx_api.h,* aby można było używać odpowiednio threadX, FileX i NetX Duo. Projekt kompilacji musi zawierać kod źródłowy FTP i plik aplikacji hosta oraz oczywiście pliki bibliotek ThreadX i NetX. To wszystko, co jest wymagane do korzystania z protokołu FTP NetX Duo.

Należy pamiętać, że ze względu na to, że protokół FTP korzysta z usług TCP NetX Duo, protokół TCP musi być włączony nx_tcp_enable *połączenia* przed użyciem protokołu FTP.

Pamiętaj, że bibliotekę NetX Duo można włączyć dla protokołu IPv6 i nadal obsługiwać sieci IPv4. Jednak NetX Duo nie może obsługiwać protokołu IPv6, chyba że jest włączony. Aby wyłączyć przetwarzanie protokołu IPv6  w programie NetX Duo, NX_DISABLE_IPV6 musi być zdefiniowany w pliku *nx_user.h,* a ten  plik musi zostać uwzględniony w kompilacji biblioteki NetX Duo przez zdefiniowanie NX_INCLUDE_USER_DEFINE_FILE w pliku *nx_port.h.* Domyślnie nie **NX_DISABLE_IPV6** zdefiniowany (protokół IPv6 jest włączony). Różni się to od *usługi nxd_ipv6_enable,* która konfiguruje protokoły i usługi IPv6 w zadaniu adresu IP i NX_DISABLE_IPV6 nie musi być zdefiniowana. 

## <a name="small-example-system-of-netx-duo-ftp"></a>Mały przykładowy system protokołu FTP NetX Duo

Przykład łatwego korzystania z protokołu FTP NetX Duo opisano na rysunku 1.1, który znajduje się poniżej. W tym przykładzie tworzone są zarówno serwer FTP, jak i klient FTP. W związku z tym oba pliki *FTP nxd_ftp_client.h i nxd_ftp_server.h są* dostępne w wierszach 10 i 11. Następnie serwer FTP jest tworzony w ciągu "*tx_application_define*" w wierszu 99. Należy pamiętać, że bloki sterowania serwer FTP i klient są zdefiniowane jako zmienne globalne w wierszu 26 wcześniej.

W tym pokazie pokazano, jak używać funkcji duo dostępnych w protokole FTP NetX Duo, a także starszych ograniczonych usług FTP IPv4. Aby użyć funkcji IPv6, pokaz definiuje USE_IPV6 wierszu 16

W wierszu 162 serwer FTP jest tworzony za pomocą funkcji ***nxd_ftp_server_create** _, jeśli aplikacja hosta definiuje USE_IPV6 która obsługuje protokoły IPv4 i IPv6. Jeśli tak nie jest, serwer FTP jest tworzony z _ *_nx_ftp_server_create_** w wierszu 166 z ograniczoną usługą IPv4. Pamiętaj, że funkcja "duo" używa innych argumentów funkcji logowania i wylogowania niż usługa IPv4, które są zdefiniowane w dolnej części pliku w wierszach 534-568.

Serwer FTP musi następnie ustanowić swój adres IPv6 (globalny i link lokalny) za pomocą netX Duo, zaczynając od wiersza 466 w funkcji wątków serwera FTP. Serwer FTP jest następnie uruchomiony w wierszu 518 i jest gotowy do obsługi żądań klientów FTP.

Klient FTP jest tworzony w wierszu 316 i przechodzi przez ten sam proces co serwer FTP, aby włączyć zadanie IPv6 klienta FTP i jego adresy IPv6 zweryfikowane, począwszy od wierszy 263-313.

Następnie klient łączy się z serwerem FTP przy użyciu ciągu ***nxd_ftp_client_connect** _ w wierszu 334, jeśli zdefiniowano wartość USE_IPV6, lub 340, jeśli korzysta z ograniczonej usługi IPv4 __*_ nx_ftp_client_connect **. W ramach funkcji wątku klienta FTP zapisuje plik na serwerze FTP i odczytuje go z powrotem przed rozłączeniem.

```C
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack.  This demo
   relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
   and then back to the server.  */



#include    "tx_api.h"
#include    "fx_api.h"
#include    "nx_api.h"
#include    "nxd_ftp_client.h"
#include    "nxd_ftp_server.h"

#define     DEMO_STACK_SIZE         4096

#ifdef FEATURE_NX_IPV6
#define USE_IPV6
#endif /* FEATURE_NX_IPV6 */


/* Define the ThreadX, NetX, and FileX object control blocks...  */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;


/* Define the NetX FTP object control blocks.  */

NX_FTP_CLIENT           ftp_client;
NX_FTP_SERVER           ftp_server;


/* Define the counters used in the demo application...  */

ULONG                   error_counter = 0;


/* Define the memory area for the FileX RAM disk.  */

UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];


#define FTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)

extern UINT  _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                        VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                        CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                        UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                        UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions.  */
VOID    _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);


void    client_thread_entry(ULONG thread_input);
void    thread_server_entry(ULONG thread_input);


#ifdef USE_IPV6
/* Define NetX Duo IP address for the NetX Duo FTP Server and Client. */
NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;
endif


/* Define server login/logout functions.  These are stubs for functions that would
   validate a client login request.   */

#ifdef USE_IPV6
UINT    server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
#else
UINT    server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
#endif


/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return(0);
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    UCHAR   *pointer;


    /* Setup the working pointer.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize NetX.  */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server.  */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool", 256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server.  */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", FTP_SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance.  */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP.  */
    nx_tcp_enable(&server_ip);

#ifdef USE_IPV6

    /* Next set the NetX Duo FTP Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Create the FTP server.  */
    status =  nxd_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login6, server_logout6);
#else
    /* Create the FTP server.  */
    status =  nx_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login, server_logout);
#endif
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread.  */
    status = tx_thread_create(&client_thread, "FTP Client thread ", client_thread_entry, 0,
            pointer, DEMO_STACK_SIZE,
            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE ;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client.  */
    status =  nx_packet_pool_create(&client_pool, "NetX Client Packet Pool", 256, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the FTP client.  */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP.  */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance.  */
    nx_tcp_enable(&client_ip);

    return;

}

/* Define the FTP client thread.  */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;

#ifdef USE_IPV6
UINT        iface_index, address_index;
#endif


    /* Format the RAM disk - the memory for the RAM disk was defined above.  */
    status = _fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry                */
                            ram_disk_memory,                 /* RAM disk memory pointer     */
                            ram_disk_sector_cache,           /* Media buffer pointer        */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size           */
                            "MY_RAM_DISK",                   /* Volume Name                 */
                            1,                               /* Number of FATs              */
                            32,                              /* Directory Entries           */
                            0,                               /* Hidden sectors              */
                            256,                             /* Total sectors               */
                            128,                             /* Sector size                 */
                            1,                               /* Sectors per cluster         */
                            1,                               /* Heads                       */
                            1);                              /* Sectors per track           */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk.  */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
        ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Let the IP threads and driver initialize the system.    */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    status = nxd_icmp_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Set the Client link local and global addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Let NetX Duo validate the addresses. */
    tx_thread_sleep(400);

#endif  /* USE_IPV6 */

    /* Create an FTP client.  */
    status =  nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Created the FTP Client\n");

#ifdef USE_IPV6

    do
    {

        /* Now connect with the NetX Duo FTP (IPv6) server. */
        status =  nxd_ftp_client_connect(&ftp_client, &server_ip_address, "name", "password", 100);
    } while (status != NX_SUCCESS);

#else

    /* Now connect with the NetX FTP (IPv4) server. */
    status =  nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS, "name", "password", 100);

#endif  /* USE_IPV6 */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet.  */
    status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer.  */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt.  */
    status =  nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");


    /* Close the file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");


    /* Now open the same file for reading.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file.  */
    status =  nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
            printf("Reread the FTP client test.txt file\n");
            nx_packet_release(my_packet);
    }

    /* Close this file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server.  */
    status =  nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;


    /* Delete the FTP client.  */
    status =  nx_ftp_client_delete(&ftp_client);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
}


/* Define the helper FTP server thread.  */
void    thread_server_entry(ULONG thread_input)
{

    UINT            status;
#ifdef  USE_IPV6
    UINT            iface_index, address_index;
#endif

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP server IPv6 enabled. */
    status = nxd_ipv6_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    status = nxd_icmp_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);

#endif /* USE_IPV6 */

    /* OK to start the FTP Server.   */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute.    */
    tx_thread_relinquish();

    return;
}


#ifdef USE_IPV6
UINT  server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    NXD_ADDRESS *client_ipduo_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged in6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
                     UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#else
UINT  server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#endif  /* USE_IPV6 */
```

**Rysunek 1.1 Przykład protokołu FTP NetX Duo**

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia protokołu NETX FTP i NetX Duo FTP. Zostaną wyświetlone wartości domyślne, ale każdą definicję można ustawić za pomocą

przed dodaniem określonego pliku nagłówkowego FTP NetX Duo. Jeśli nie określono pliku nagłówkowego, opcja jest dostępna zarówno w *plikach nxd_ftp_client.h, jak i nxd_ftp_server.h.* Na poniższej liście szczegółowo opisano poszczególne z nich:

- **NX_FTP_SERVER_PRIORITY** Priorytet wątku serwera FTP. Domyślnie ta wartość jest zdefiniowana jako 16, aby określić priorytet 16.
- **NX_FTP_MAX_CLIENTS** Maksymalna liczba klientów obsługiwanych przez serwer w tym samym czasie. Domyślnie ta wartość to 4 w celu obsługi 4 klientów jednocześnie.
- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD** Minimalny rozmiar ładunku puli pakietów serwera w bajtach, w tym nagłówków TCP, IP i ramek sieciowych oraz danych HTTP. Wartość domyślna to 256 (maksymalna długość nazwy pliku w pliku FileX) + 12 bajtów dla informacji o pliku i NX_PHYSICAL_TRAILER.
- **NX_FTP_SERVER_TIMEOUT** Określa liczbę znaczników ThreadX, dla których usługi wewnętrzne będą wstrzymywane. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).
- **NX_FTP_ACTIVITY_TIMEOUT** Określa liczbę sekund, przez które połączenie klienta jest utrzymywane, jeśli nie ma żadnej aktywności. Wartość domyślna to 240.
- **NX_FTP_TIMEOUT_PERIOD** Określa interwały w sekundach, gdy serwer sprawdza aktywność klienta. Wartość domyślna to 60.
- **NX_FTP_SERVER_RETRY_SECONDS** Określa początkowy limit czasu w sekundach przed retransmisją odpowiedzi serwera. Wartość domyślna to 2.
- **NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH** Określa maksymalną głębokość pakietów przesyłanych w kolejce na gnieździe serwera. Wartość domyślna to 20.
- **NX_FTP_SERVER_RETRY_MAX** Określa maksymalną liczbę ponownych prób na pakiet. Wartość domyślna to 10.
- **NX_FTP_SERVER_RETRY_SHIFT** Określa liczbę bitów, które mają być przesunięte w ustawieniu limitu czasu ponawiania. Wartość domyślna to 2, np. limit czasu ponawiania jest dwa razy dłuższy niż poprzednie ponawianie.
- **NX_FTP_NO_FILEX** Zdefiniowano, ta opcja udostępnia wycinki dla zależności FileX. Klient FTP będzie działać bez żadnych zmian, jeśli ta opcja jest zdefiniowana. Serwer FTP musi zostać zmodyfikowany lub użytkownik będzie musiał utworzyć kilka usług FileX, aby działać prawidłowo.
- **NX_FTP_CONTROL_TOS** Typ usługi wymagany dla żądań sterowania FTP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.
- **NX_FTP_DATA_TOS** Typ usługi wymagany dla żądań danych FTP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.
- **NX_FTP_FRAGMENT_OPTION** Włącz fragment dla żądań FTP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentowanie TCP protokołu FTP.
- **NX_FTP_CONTROL_WINDOW_SIZE** Rozmiar okna gniazda sterowania TCP. Domyślnie ta wartość to 400 bajtów.
- **NX_FTP_DATA_WINDOW_SIZE** Rozmiar okna gniazda danych TCP. Domyślnie ta wartość to 2048 bajtów.
- **NX_FTP_TIME_TO_LIVE** Określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.
- **NX_FTP_USERNAME_SIZE** Określa dozwoloną liczbę bajtów w podanej przez klienta nazwie *użytkownika*. Wartość domyślna to 20 *.*
- **NX_FTP_PASSWORD_SIZE** Określa liczbę bajtów dozwolonych w hasłach podanych przez *klienta*. Wartość domyślna to 20.
