---
title: Rozdział 2 . Instalowanie i używanie Azure RTOS NetX Duo TFTP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika TFTP Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ae4e82a0f878af06bd178035cb9429cfe2a14d0bc4bbf848db7d321463586a20
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801261"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a>Rozdział 2 . Instalowanie i używanie Azure RTOS NetX Duo TFTP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika TFTP Azure RTOS NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS NetX Duo można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie https://github.com/azure-rtos/netxduo/ . Pakiet zawiera następujące pliki:


- **nxd_tftp_client.h** Plik nagłówkowy klienta TFTP NetX Duo

- **nxd_tftp_client.c** Plik źródłowy języka C dla klienta TFTP NetX Duo

- **nxd_tftp_server.h** Plik nagłówkowy serwera TFTP NetX Duo

- **nxd_tftp_server.c** Plik źródłowy języka C dla serwera TFTP NetX Duo

- **filex_stub.h** Plik wycinki, jeśli plik FileX nie istnieje

- **nxd_tftp.pdf** Opis w formacie PDF programu NetX Duo TFTP

- **demo_netxduo_tftp.c** Pokaz NetX Duo TFTP

## <a name="tftp-installation"></a>Instalacja TFTP

Aby użyć netX Duo TFTP, cała dystrybucja, o której wspomniano wcześniej, może zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Jeśli na przykład program NetX Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu można skopiować pliki *nxd_tftp_client.h,* *nxd_tftp_client.c,* *nxd_tftp_server.h* i *nxd_tftp_server.c.*

## <a name="using-tftp"></a>Korzystanie z tftp

Aby można było uruchomić aplikację TFTP, kod aplikacji musi zawierać pliki *nxd_tftp_client.h* i/lub nxd_tftp_server.h po dojecheniu do nich plików *tx_api.h, fx_api.h* i *nx_api.h,* aby można było używać odpowiednio threadX, FileX i NetX Duo. Projekt aplikacji musi również zawierać *nxd_tftp_client.c* *i/lub nxd_tftp_server.c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z programu NetX Duo TFTP. Gdy *pliki nagłówkowe są dołączone,* kod aplikacji może korzystać z usług TFTP.

> [!NOTE]
> Ponieważ TFTP korzysta z usług NetX Duo UDP, przed użyciem protokołu TFTP należy włączyć funkcję UDP *nx_udp_enable* wywołaniu protokołu TFTP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład łatwego korzystania z aplikacji NetX Duo TFTP opisano na rysunku 1.1, który znajduje się poniżej. W tym przykładzie pliki dołączane TFTP *nxd_tftp_client.h* i *nxd_tftp_server.h* są dostępne w wierszach 19 i 20. Następnie serwer TFTP jest tworzony w ciągu "*tx_application_define*" w wierszu 179. 

> [!NOTE]
> Blok sterowania serwera TFTP *"server"* został wcześniej zdefiniowany jako zmienna globalna w wierszu 45. W tym pokazie do komunikacji TFTP w wierszu 14 jest wybierany protokół IPv4. Po pomyślnym utworzeniu serwer TFTP jest uruchomiony w wierszu 304. W wierszu 411 tworzony jest klient TFTP. Na koniec klient zapisuje plik w wierszu 450 i odczytuje go z powrotem w wierszu 485.

Zadanie wątku serwera TFTP zostanie zatrzymane, a serwer TFTP zostanie usunięty w wierszu 324. Aplikacja powinna wywołać fx_media_close (wiersz 331), aby zamknąć wszystkie pliki i zaktualizować dane plików i katalogów na nośniku USB.

> [!NOTE]
> W tym przykładzie użyto pliku FileX do obsługi serwera TFTP odbierania i pobierania żądań plików klienta TFTP. Jeśli jednak NX_TFTP_NO_FILEX, aplikacja może zawierać file_stub.h zamiast fx_api.h.
>
> Należy również pamiętać, że istniejące aplikacje klienta i serwera NetX TFTP będą działać z programem NetX Duo TFTP. Zachęcamy jednak dewelopera aplikacji do przenoszenia aplikacji NetX TFTP do aplikacji NetX Duo. Odpowiednikami usług NetX TFTP są:

- *nxd_tftp_server_start*

- *nxd_tftp_server_stop*

- *nxd_tftp_client_file_read*

- *nxd_tftp_client_file_write*

- *nxd_tftp_client_file_open*

```C
/* This is a small demo of TFTP on the high-performance NetX TCP/IP stack. This demo
   relies on ThreadX and NetX Duo, to show a simple file transfer from the client
   and then back to the server. */



/* Indicate if using IPv6. */
#define USE_DUO

/* If the host application is using NetX Duo, determine which IP version to use.
   Make sure IPv6 in NetX Duo is enabled if planning to use TFTP over IPv6 */
#ifdef USE_DUO
#define     IP_TYPE     6
#endif /* USE_DUO        */

#include    "tx_api.h"
#include    "nx_api.h"
#include    "nxd_tftp_client.h"
#include    "nxd_tftp_server.h"
#ifndef     NX_TFTP_NO_FILEX
#include    "fx_api.h"
#endif


#define     DEMO_STACK_SIZE         4096

/* To use another file storage utility define this symbol:
#define NX_TFTP_NO_FILEX
*/

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;

/* Define the NetX TFTP object control blocks. */

NX_TFTP_CLIENT          client;
NX_TFTP_SERVER          server;

/* Define the application global variables */

#define                 CLIENT_ADDRESS  IP_ADDRESS(1, 2, 3, 5)
#define                 SERVER_ADDRESS  IP_ADDRESS(1, 2, 3, 4)

NXD_ADDRESS             server_ip_address;
NXD_ADDRESS             client_ip_address;

UINT                    error_counter = 0;

/* Define buffer used in the demo application. */
UCHAR                   buffer[255];
ULONG                   data_length;


/* Define the memory area for the FileX RAM disk. */
#ifndef NX_TFTP_NO_FILEX
UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];
#endif


/* Define function prototypes. */

VOID    _fx_ram_driver(FX_MEDIA *media_ptr);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
void    client_thread_entry(ULONG thread_input);
void    server_thread_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;
UCHAR   *pointer;


    /* Setup the working pointer. */
    pointer =  (UCHAR *) first_unused_memory;


    /* Create the main TFTP server thread. */
    status = tx_thread_create(&server_thread, "TFTP Server Thread", server_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              4,4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the main TFTP client thread at a slightly lower priority. */
    status = tx_thread_create(&client_thread, "TFTP Client Thread", client_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              5, 5, TX_NO_TIME_SLICE, TX_DONT_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&server_pool, "TFTP Server Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the TFTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&server_ip);

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the TFTP server. */
#ifdef USE_DUO
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
    /* Specify the tftp server global address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x102;
#endif
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_ADDRESS;

#endif

    status =  nxd_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#else
    status =  nx_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#endif

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for errors for the server. */
    if (status)
        error_counter++;

    /* Create a packet pool for the TFTP client. */

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&client_pool, "TFTP Client Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the TFTP client. */
    status = nx_ip_create(&client_ip, "TFTP Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable UDP for client IP instance. */
    status |=  nx_udp_enable(&client_ip);
    status |= nx_icmp_enable(&client_ip);

    tx_thread_resume(&client_thread);
}

void server_thread_entry(ULONG thread_input)
{

UINT        status, running;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#ifndef  NX_TFTP_NO_FILEX

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry             */
                            ram_disk_memory,                 /* RAM disk memory pointer  */
                            ram_disk_sector_cache,           /* Media buffer pointer     */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size        */
                            "MY_RAM_DISK",                   /* Volume Name              */
                            1,                               /* Number of FATs           */
                            32,                              /* Directory Entries        */
                            0,                               /* Hidden sectors           */
                            256,                            /* Total sectors            */
                            128,                             /* Sector size              */
                            1,                               /* Sectors per cluster      */
                            1,                               /* Heads                    */
                            1);                              /* Sectors per track        */

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory, ram_disk_sector_cache,
                               sizeof(ram_disk_sector_cache));

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

#endif /*  NX_TFTP_NO_FILEX */

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ICMPv6 services. */
    status |= nxd_icmp_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the server. */
    status = nxd_ipv6_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for DAD to validate the address. */
    tx_thread_sleep(500);
#endif

#endif /* IP_TYPE == 6 */

    /* Start the NetX TFTP server. */
#ifdef USE_DUO
    status =  nxd_tftp_server_start(&server);
#else
    status =  nx_tftp_server_start(&server);
#endif

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Run for a while */
    running = NX_TRUE;
    while(running)
        tx_thread_sleep(200);


    /* Stop and delete the TFTP server. */
#ifdef USE_DUO
    nxd_tftp_server_delete(&server);
#else
    nx_tftp_server_delete(&server);
#endif

    /* Close all open files and ensure directory information is also written out to the media.
    This will also flush the file data to USB media*/
    status = fx_media_close(&ram_disk);

    if (status)
    {
        error_counter++;
    }

    return;

}


/* Define the TFTP client thread. */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
UINT        all_done = NX_FALSE;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ECMPv6 services for the client. */
    status = nxd_icmp_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the client. */
    status = nxd_ipv6_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the Client IPv6 address */
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_address.v6[1] = 0xf101;
    client_ip_address.nxd_ip_address.v6[2] = 0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for the link local and global addresses to be validated. */
    tx_thread_sleep(500);
#endif
#endif /*(IP_TYPE == 6) */


    /* The TFTP services used below include the NetX equivalent service which will work with
       NetX Duo TFTP. However, it is recommended for developers to port their applications
       to the newer services that take the NXD_ADDRESS type and support both IPv4 and IPv6
       communication.
    */

    /* Create a TFTP client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool, IP_TYPE);
#else
    status =  nx_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool);
#endif

    /* Check status. */
    if (status)
        return;

    /* Open a TFTP file for writing. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_WRITE, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_WRITE, 100);
#endif

    /* Check status. */
    if (status)
        return;

    /* Allocate a TFTP packet. */
#ifdef USE_DUO
    status =  nxd_tftp_client_packet_allocate(&client_pool, &my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_packet_allocate(&client_pool, &my_packet, 100);
#endif
    /* Check status. */
    if (status)
        error_counter++;

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write this packet to the file via TFTP. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_write(&client, my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_write(&client, my_packet, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Close this file. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Open the same file for reading. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_READ, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_READ, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;
    do
    {

    /* Read the file back. */
#ifdef USE_DUO
        status =  nxd_tftp_client_file_read(&client, &my_packet, 100, IP_TYPE);
#else
        status =  nx_tftp_client_file_read(&client, &my_packet, 100);
#endif
        /* Check for retranmission/dropped packet error. Benign. Try again... */
        if (status == NX_TFTP_INVALID_BLOCK_NUMBER)
        {

            continue;
        }
        else if (status == NX_TFTP_END_OF_FILE)
        {

            /* All done. */
            all_done = NX_TRUE;
        }
        else if (status != NX_SUCCESS)
        {

            /* Internal error, invalid packet or error on read. */
            break;
        }


        /* Do something with the packet data and release when done. */
        nx_packet_data_retrieve(my_packet, buffer, &data_length);
        buffer[data_length] = 0;
        printf("Receive data: %s\n", buffer);

        printf("release packet in demo.\n");

        nx_packet_release(my_packet);

    } while (all_done == NX_FALSE);

    /* Close the file again. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Delete the client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_delete(&client);
#else
    status =  nx_tftp_client_delete(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    return;
}
```

Rysunek 1.1 Przykład użycia tftp z netx duo

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia aplikacji NetX Duo TFTP. Na poniższej liście szczegółowo opisano każdą z nich. O ile nie określono inaczej, te opcje można znaleźć w *plikach nxd_tftp_client.h* *i nxd_tftp_server.h.*


- **NX_DISABLE_ERROR_CHECKING** Zdefiniowano, ta opcja usuwa podstawowe sprawdzanie błędów TFTP. Jest on zwykle używany po debugowaniu aplikacji.

- **NX_TFTP_SERVER_PRIORITY** Priorytet wątku serwera TFTP. Domyślnie ta wartość jest zdefiniowana jako 16, aby określić priorytet 16.

- **NX_TFTP_SERVER_TIME_SLICE** Wycinek czasu dla serwera TFTP do uruchomienia przed uzyskaniem innych wątków o tym samym priorytecie. Wartość domyślna to 2.

- **NX_TFTP_MAX_CLIENTS** Maksymalna liczba klientów obsługiwanych przez serwer w tym samym czasie. Domyślnie ta wartość to 10 w celu obsługi 10 klientów jednocześnie.

- **NX_TFTP_ERROR_STRING_MAX** Maksymalna liczba znaków w ciągu błędu. Domyślnie ta wartość to 64.

- **NX_TFTP_NO_FILEX** Zdefiniowano, ta opcja udostępnia wycinki dla zależności FileX. Klient TFTP będzie działać bez żadnych zmian, jeśli ta opcja jest zdefiniowana. Serwer TFTP musi zostać zmodyfikowany lub użytkownik będzie musiał utworzyć kilka usług FileX, aby działać prawidłowo.

- **NX_TFTP_TYPE_OF_SERVICE** Typ usługi wymagany dla żądań protokołu UDP TFTP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.

- **NX_TFTP_FRAGMENT_OPTION** Włączanie fragmentu dla żądań protokołu UDP TFTP. Domyślnie ta wartość jest NX_DONT_FRAGMENT wyłączyć fragmentowanie protokołu UDP TFTP.

- **NX_TFTP_TIME_TO_LIVE** Określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.

- **NX_TFTP_SOURCE_PORT** Ta opcja umożliwia aplikacji klienckiej TFTP określenie portu gniazda UDP klienta TFTP. Domyślnie jest to NX_ANY_PORT.

- ***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Umożliwia czasomierzowi serwera TFTP sprawdzanie każdej sesji klienta TFTP z ostatnią aktywnością (ACK lub pakiet danych). Gdy limit czasu sesji wygasa po maksymalnej liczbie razy, zakłada się, że połączenie zostało utracone. Serwer wyczyści żądanie klienta, zamknie wszystkie otwarte pliki i udostępnia żądanie połączenia dla następnego klienta. Ustawienie domyślne jest wyłączone.

- **NX_TFTP_SERVER_TIMEOUT_PERIOD** Określa interwał, w którym funkcja wprowadzania czasomierza serwera TFTP sprawdza, czy połączenia klienckie odbierają jakiekolwiek pakiety. Wartość domyślna to 20 (takty czasomierza).

- **NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** Jest to limit czasu odebrania prawidłowego ACK lub pakietu danych z klienta. Wartość domyślna to 200 (takty czasomierza).

- **NX_TFTP_SERVER_MAX_RETRIES** Określa maksymalną liczbę odnowić limit czasu ponownego przekierowywaną sesję klienta. Następnie sesja jest zamykana przez serwer.

- **NX_TFTP_MAX_CLIENT_RETRANSMITS** Określa maksymalną liczbę odbierania przez serwer zduplikowanego pakietu ACK lub pakietu danych od klienta (który porzuca) bez wysyłania komunikatu o błędzie do klienta i zamykania sesji. Nie ma wpływu, jeśli NX_TFTP_SERVER_RETRANSMIT_ENABLE zdefiniowano.
