---
title: Rozdział 2 — Instalowanie i używanie protokołu HTTP NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika HTTP NetX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5d4913c01de5cc7c41d44bda473bbaca06dd474a26570b056bfde3cd48acc4e4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799408"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a>Rozdział 2 — Instalowanie i używanie protokołu HTTP NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika HTTP NetX.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS NetX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .

- **nx_http_client.h** Plik nagłówka klienta HTTP dla NetX
- **nx_http_server.h** Plik nagłówka dla serwera HTTP dla NetX
- **nx_http_client.c** Plik źródłowy języka C dla klienta HTTP dla NetX
- **nx_http_server.c** Plik źródłowy języka C dla serwera HTTP dla NetX
- **nx_md5.c** Algorytmy skrótu MD5
- **filex_stub.h** Plik wycinki, jeśli plik FileX nie istnieje
- **nx_http.pdf** Opis protokołu HTTP dla NetX
- **demo_netx_http.c** Pokaz protokołu HTTP NetX

## <a name="http-installation"></a>Instalacja HTTP

Aby można było używać protokołu HTTP dla NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano platformę NetX. Na przykład jeśli netx jest zainstalowany w katalogu *"\threadx\arm7\green",* to *nx_http_client.h* i *nx_http_client.c* dla aplikacji klienta HTTP NetX oraz *nx_http_server.h* i *nx_http_server.c* dla aplikacji serwera HTTP NetX. *nx_md5.c* należy skopiować do tego katalogu. W przypadku aplikacji demonstracyjnej "sterownik pamięci RAM" pliki Klienta HTTP i serwera NetX powinny zostać skopiowane do tego samego katalogu.

## <a name="using-http"></a>Korzystanie z protokołu HTTP

Korzystanie z protokołu HTTP dla NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać pliki *nx_http_client.h* i/lub *nx_http_server.h,* gdy zawiera pliki *tx_api.h, fx_api.h* i *nx_api.h,* aby można było używać odpowiednio threadX, FileX i NetX. Gdy zostaną dołączone pliki nagłówka HTTP, kod aplikacji będzie mógł wykonać wywołania funkcji HTTP określone w dalszej części tego przewodnika. Aplikacja musi również uwzględniać *pliki nx_http_client.c,* *nx_http_server.c* i *md5.c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z protokołu HTTP NetX.

>[!NOTE] 
> Jeśli NX_HTTP_DIGEST_ENABLE nie zostanie określony w procesie kompilacji, nie trzeba dodawać pliku *md5.c* do aplikacji. Podobnie, jeśli nie są wymagane żadne możliwości klienta HTTP, *nx_http_client.c* plik może zostać pominięty.

>[!NOTE] 
> Ponieważ protokół HTTP korzysta z usług NetX TCP, protokół TCP musi być włączony za *pomocą nx_tcp_enable* przed użyciem protokołu HTTP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład łatwego korzystania z protokołu HTTP NetX opisano na rysunku 1.1, który znajduje się poniżej. W tym przykładzie pliki dołączane HTTP *nx_http_client.h i nx_http_server.h* są dostępne w wierszu 8. Następnie serwer HTTP jest tworzony w ciągu "*tx_application_define*" w wierszu 131.

>[!NOTE] 
> Blok sterowania serwera HTTP *"Serwer"* został wcześniej zdefiniowany jako zmienna globalna w wierszu 25.

Po pomyślnym utworzeniu serwer HTTP jest uruchomiony w wierszu 136. W wierszu 149 tworzony jest klient HTTP. Na koniec klient zapisuje plik w wierszu 157 i odczytuje go z powrotem w wierszu 195.

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

Rysunek 1.1 Przykład użycia protokołu HTTP z netx

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia protokołu HTTP dla NetX. Poniżej znajduje się lista wszystkich opcji, z których każda jest szczegółowo opisana. Zostaną wyświetlone wartości domyślne, ale można je ponownie zdefiniować przed dodaniem parametrów *nx_http_client.h i nx_http_server.h:*

- **NX_DISABLE_ERROR_CHECKING** Zdefiniowano, ta opcja usuwa podstawowe sprawdzanie błędów HTTP. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_HTTP_SERVER_PRIORITY** Priorytet wątku serwera HTTP. Domyślnie ta wartość jest zdefiniowana jako 16, aby określić priorytet 16.
- **NX_HTTP_NO_FILEX** Zdefiniowano, ta opcja udostępnia wycinki dla zależności FileX. Klient HTTP będzie działać bez żadnych zmian, jeśli ta opcja jest zdefiniowana. Serwer HTTP musi zostać zmodyfikowany lub użytkownik będzie musiał utworzyć kilka usług FileX, aby działać prawidłowo.
- **NX_HTTP_TYPE_OF_SERVICE** Typ usługi wymagany dla żądań HTTP TCP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.
- **NX_HTTP_SERVER_THREAD_TIME_SLICE** Liczba znaczników czasomierza, które wątek serwera może uruchomić przed uzyskaniem wątków o tym samym priorytecie. Wartość domyślna to 2.
- **NX_HTTP_FRAGMENT_OPTION** Włącz fragment dla żądań HTTP TCP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentowanie PROTOKOŁU HTTP TCP.
- **NX_HTTP_SERVER_WINDOW_SIZE** Rozmiar okna gniazda serwera. Domyślnie ta wartość to 2048 bajtów.
- **NX_HTTP_TIME_TO_LIVE** Określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.
- **NX_HTTP_SERVER_TIMEOUT** Określa liczbę znaczników ThreadX, dla których usługi wewnętrzne będą wstrzymywane. Wartość domyślna to 10 sekund (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać w wewnętrznych *nx_tcp_server_socket_accept* wywołań. Wartość domyślna to (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać dla w wewnętrznych *nx_tcp_socket_disconnect* wywołań. Wartość domyślna to 10 sekund (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać w wewnętrznych *nx_tcp_socket_receive* wywołań. Wartość domyślna to 10 sekund (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_SEND** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać dla w wewnętrznych *nx_tcp_socket_send* wywołań. Wartość domyślna to 10 sekund (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_MAX_HEADER_FIELD** Określa maksymalny rozmiar pola nagłówka HTTP. Wartość domyślna to 256.
- **NX_HTTP_MULTIPART_ENABLE** Umożliwia serwerowi HTTP obsługę wieloczęściowych żądań HTTP.
- **NX_HTTP_SERVER_MAX_PENDING** Określa liczbę połączeń, które mogą być w kolejce dla serwera HTTP. Wartość domyślna to 5.
- **NX_HTTP_MAX_RESOURCE** Określa dozwoloną liczbę bajtów w nazwie zasobu *podanej przez klienta.* Wartość domyślna to 40.
- **NX_HTTP_MAX_NAME** Określa dozwoloną liczbę bajtów w podanej przez klienta nazwie *użytkownika*. Wartość domyślna to 20.
- **NX_HTTP_MAX_PASSWORD** Określa liczbę bajtów dozwolonych w hasłach podanych przez *klienta*. Wartość domyślna to 20.
- **NX_HTTP_SERVER_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia serwera. Minimalny rozmiar jest wymagany do zapewnienia, że pełny nagłówek HTTP może być zawarty w jednym pakiecie. Wartość domyślna to 600.
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia klienta. Minimalny rozmiar jest wymagany do zapewnienia, że pełny nagłówek HTTP może być zawarty w jednym pakiecie. Wartość domyślna to 300.
- **NX_HTTP_SERVER_RETRY_SECONDS** *ustaw limit czasu retransmisji gniazda serwera w sekundach. Wartość* domyślna to 2.
- **NX_HTTP_SERVER_RETRY_MAX** Określa maksymalną liczbę retransmisji na gniazda serwera. Wartość domyślna to 10.
- **NX_HTTP_SERVER_RETRY_SHIFT** Ta wartość jest używana do ustawienia następnego limitu czasu ponownej transmisji. Bieżący limit czasu jest mnożony przez liczbę do tej pory retransmisji, przesunięte przez wartość przesunięcia limitu czasu gniazda. Wartość domyślna jest ustawiona na 1 dla podwojenia limitu czasu.
- **NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** Określa maksymalną liczbę pakietów, które mogą być w kolejce w kolejce retransmisji gniazda serwera. Jeśli liczba pakietów w kolejkach osiągnie tę liczbę, nie będzie można wysłać więcej pakietów, dopóki co najmniej jeden pakiet w kolejkach nie zostanie zwolniony. Wartość domyślna to 20.