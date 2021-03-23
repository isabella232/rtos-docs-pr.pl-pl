---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX FTP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika FTP usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 812422566b9761baac5f9c2477dba1f0fcc0a778
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822627"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX FTP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika FTP usługi Azure RTO NetX.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO NetX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_ftp. h**: plik nagłówkowy FTP dla NetX
- plik źródłowy **nx_ftp_client. c**: c dla klienta FTP dla NetX
- plik źródłowy **nx_ftp_server. c**: c dla serwera FTP dla NetX
- **filex_stub. h**: plik zastępczy, jeśli nie istnieje filex
- **nx_ftp.pdf**: Opis formatu PDF FTP dla NetX
- **demo_netx_ftp. c**: system demonstracyjny FTP

## <a name="ftp-installation"></a>Instalacja FTP

Aby można było korzystać z protokołu FTP for NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_ftp. h*, *nx_ftp_client. c* i *nx_ftp_server. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-ftp"></a>Przy użyciu protokołu FTP

Korzystanie z protokołu FTP for NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać *nx_ftp. h* , po uwzględnieniu *tx_api. h, fx_api. h,* i *nx_api. h*, w celu użycia odpowiednio ThreadX, FileX i NetX. Po dołączeniu *nx_ftp. h* kod aplikacji może następnie wprowadzić wywołania funkcji FTP określone w dalszej części tego przewodnika. Aplikacja musi również zawierać *nx_ftp_client. c* i *nx_ftp_server. c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z usługi NetX FTP.

> [!NOTE]
> Ponieważ FTP wykorzystuje usługi NetX TCP, należy włączyć protokół TCP przy użyciu wywołania *nx_tcp_enable* przed użyciem protokołu FTP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład, jak łatwo jest użyć usługi FTP NetX 1,1 opisanej poniżej.

> [!NOTE]
> Jest to urządzenie hosta z pojedynczym interfejsem sieciowym.

W tym przykładzie plik dołączany FTP *nx_ftp_client. h* i *nx_ftp_server. h* są wprowadzane w wierszu 10 i 11. Następnie serwer FTP jest tworzony w lokalizacji "*tx_application_define*" w wierszu 134. Należy pamiętać, że blok kontroli serwera FTP "*serwer*" został zdefiniowany jako zmienna globalna w wierszu 31 wcześniej. Po pomyślnym utworzeniu serwer FTP jest uruchamiany w wierszu 363. W wierszu 183 jest tworzony klient FTP. A wreszcie klient zapisuje plik w wierszu 229 i odczytuje plik z powrotem w wierszu 318.

```c
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack. This demo
relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
and then back to the server. */

#include     "tx_api.h"
#include     "fx_api.h"
#include     "nx_api.h"
#include     "nx_ftp_client.h"
#include     "nx_ftp_server.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD          server_thread;
TX_THREAD          client_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_PACKET_POOL     client_pool;
NX_IP              client_ip;
FX_MEDIA           ram_disk;

/* Define the NetX FTP object control blocks. */

NX_FTP_CLIENT     ftp_client;
NX_FTP_SERVER     ftp_server;

/* Define the counters used in the demo application... */

ULONG     error_counter = 0;

/* Define the memory area for the FileX RAM disk. */

UCHAR     ram_disk_memory[32000];
UCHAR     ram_disk_sector_cache[512];

#define FTP_SERVER_ADDRESS IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS IP_ADDRESS(1,2,3,5)

extern UINT _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                    VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                    CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                    UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                    UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions. */
VOID     _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

void     client_thread_entry(ULONG thread_input);
void     thread_server_entry(ULONG thread_input);

/* Define server login/logout functions. These are stubs for functions that would
validate a client login request. */

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port, CHAR *name,
                CHAR *password, CHAR *extra_info);

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port, CHAR *name,
                    CHAR *password, CHAR *extra_info);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry,
                    0, pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize NetX. */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server. */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance",
                        FTP_SERVER_ADDRESS, 0xFFFFFF00UL, &server_pool,
                        _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance. */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP. */
    nx_tcp_enable(&server_ip);

    /* Create the FTP server. */
    status = nx_ftp_server_create(&ftp_server, "FTP Server Instance",
                    &server_ip, &ram_disk, pointer, DEMO_STACK_SIZE,
                    &server_pool, server_login, server_logout);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread. */
    status = tx_thread_create(&client_thread, "FTP Client thread ",
                            client_thread_entry, 0,
                            pointer, DEMO_STACK_SIZE,
                            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client. */
    status = nx_packet_pool_create(&client_pool, "NetX Client Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance for the FTP client. */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS,
            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP. */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance. */
    nx_tcp_enable(&client_ip);

    return;
}

/* Define the FTP client thread. */
void     client_thread_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = _fx_media_format(&ram_disk,
            _fx_ram_driver, /* Driver entry */
            ram_disk_memory, /* RAM disk memory pointer */
            ram_disk_sector_cache, /* Media buffer pointer */
            sizeof(ram_disk_sector_cache), /* Media buffer size */
            "MY_RAM_DISK", /* Volume Name */
            1, /* Number of FATs */
            32, /* Directory Entries */
            0, /* Hidden sectors */
            256, /* Total sectors */
            128, /* Sector size */
            1, /* Sectors per cluster */
            1, /* Heads */
            1); /* Sectors per track */

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                            ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

     /* Let the IP threads and driver initialize the system. */
    tx_thread_sleep(100);

    /* Create an FTP client. */
    status = nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Created the FTP Client\n");

    /* Now connect with the NetX FTP (IPv4) server. */
    status = nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS,
                                    "name", "password", 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet. */
    status = nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Write ABCs into the packet payload! */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length = 28;
    my_packet -> nx_packet_append_ptr = my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt. */
    status = nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");

    /* Close the file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");

    /* Now open the same file for reading. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file. */
    status = nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
        printf("Reread the FTP client test.txt file\n");
        nx_packet_release(my_packet);
    }

    /* Close this file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server. */
    status = nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    /* Delete the FTP client. */
    status = nx_ftp_client_delete(&ftp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
}

/* Define the helper FTP server thread. */
void     thread_server_entry(ULONG thread_input)
{

UINT     status;

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

    /* OK to start the FTP Server. */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute. */
    tx_thread_relinquish();

    return;
}

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port,
                CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success. */
    return(NX_SUCCESS);
}

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success. */
    return(NX_SUCCESS);
}
```

Rysunek 1,1 przykład klienta i serwera FTP z NetX (pojedynczy Host interfejsu sieciowego)

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania protokołu FTP dla NetX. Poniższa lista zawiera szczegółowy opis:  

- **NX_FTP_SERVER_PRIORITY**: priorytet wątku serwera FTP. Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.

- **NX_FTP_MAX_CLIENTS**: Maksymalna liczba klientów, które serwer może obsłużyć jednocześnie. Domyślnie ta wartość to 4 do obsługi 4 klientów jednocześnie.

- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: minimalny rozmiar ładunku puli pakietów serwera w bajtach, w tym nagłówki protokołu TCP, adresu IP i ramki sieciowej oraz dane protokołu HTTP. Wartość domyślna to 256 (maksymalna długość nazwy pliku w FileX) + 12 bajtów w celu uzyskania informacji o pliku i NX_PHYSICAL_TRAILER.

- **NX_FTP_NO_FILEX**: zdefiniowane, ta opcja udostępnia element zastępczy dla zależności FILEX. Klient FTP będzie działać bez żadnej zmiany, jeśli ta opcja jest zdefiniowana. Należy zmodyfikować serwer FTP lub użytkownik będzie musiał utworzyć kilku usługi FileX, aby działać prawidłowo.

- **NX_FTP_CONTROL_TOS**: typ usługi wymaganej przez żądania kontroli TCP FTP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ftp. h*.

- **NX_FTP_DATA_TOS**: typ usługi wymaganej przez żądania danych FTP TCP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ftp. h*.

- **NX_FTP_FRAGMENT_OPTION**: Włącz fragment dla żądań FTP TCP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć funkcję fragmentacji TCP FTP. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ftp. h*.

- **NX_FTP_CONTROL_WINDOW_SIZE**: sterowanie rozmiarem okna gniazda. Wartość domyślna to 400 bajtów. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ftp. h*.

- **NX_FTP_DATA_WINDOW_SIZE**: rozmiar okna gniazda danych. Wartość domyślna to 2048 bajtów. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ftp. h*.

- **NX_FTP_TIME_TO_LIVE**: określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80, ale można ją zdefiniować ponownie przed włączeniem *nx_ftp. h.*

- **NX_FTP_SERVER_TIMEOUT**: określa liczbę ThreadXych taktów, dla których będą zawieszane usługi wewnętrzne. Wartość domyślna to 100, ale można ją zdefiniować ponownie przed włączeniem *nx_ftp. h.*

- **NX_FTP_USERNAME_SIZE**: określa liczbę bajtów dozwolonych w *nazwie użytkownika* dostarczonej przez klienta. Wartość domyślna to 20, ale można ją zdefiniować ponownie przed włączeniem *nx_ftp. h.*

- **NX_FTP_PASSWORD_SIZE**: określa liczbę bajtów dozwolonych w *haśle* dostarczonym przez klienta. Wartość domyślna to 20, ale można ją zdefiniować ponownie przed włączeniem *nx_ftp. h.*

- **NX_FTP_ACTIVITY_TIMEOUT**: określa liczbę sekund utrzymywania połączenia z klientem w przypadku braku aktywności. Wartość domyślna to 240, ale można ją zdefiniować ponownie przed włączeniem *nx_ftp. h.*

- **NX_FTP_TIMEOUT_PERIOD**: określa liczbę sekund między sprawdzaniem serwera dla nieaktywności klienta. Wartość domyślna to 60, ale można ją zdefiniować ponownie przed włączeniem *nx_ftp. h.*
