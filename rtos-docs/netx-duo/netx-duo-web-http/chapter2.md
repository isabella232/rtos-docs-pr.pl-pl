---
title: Rozdział 2 — Instalowanie i używanie protokołów HTTP i HTTPS
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika HTTP sieci Web NetX.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fd8ab093d15c5413b0d5dac6d35b080674c3a332ec7a028fc462237135880d34
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783428"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a>Rozdział 2 — Instalowanie i używanie protokołów HTTP i HTTPS

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika HTTP sieci Web NetX.

## <a name="product-distribution"></a>Dystrybucja produktów

Protokół HTTP dla NetX jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera trzy pliki źródłowe, dwa pliki dołączane i plik zawierający ten dokument w następujący sposób:

- **nx_web_http_common.h** Wspólny plik nagłówkowy dla internetowego protokołu HTTP NetX
- **nx_web_http_client.h** Plik nagłówkowy klienta HTTP dla sieci Web NetX
- **nx_web_http_server.h** Plik nagłówkowy serwera HTTP dla sieci Web NetX
- **nx_web_http_client.c** Plik źródłowy języka C dla klienta HTTP dla sieci Web NetX
- **nx_web_http_server.c** Plik źródłowy języka C dla serwera HTTP dla sieci Web NetX
- **nx_tcpserver.c** Plik źródłowy języka C dla wielu gniazd TCP
- **nx_tcpserver.h** Plik nagłówkowy do definiowania symboli serwera HTTPS
- **nx_md5.c** Algorytmy skrótu MD5
- **filex_stub.h** Plik wycinki, jeśli plik FileX nie istnieje
- **nx_web_http.pdf** Opis protokołu HTTP dla sieci Web NetX
- **demo_netx_web_http.c** Pokaz protokołu HTTP sieci Web netx

## <a name="http-installation"></a>Instalacja HTTP

Aby można było korzystać z protokołu HTTP sieci Web NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano netX Duo. Jeśli na przykład netx Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* to wartości nx_web_http_client.h i nx_web_http_client.c dla aplikacji klienckich HTTP sieci Web NetX oraz *nx_web_http_server.h*, nx_web_http_server.c, *nx_tcpserver.c* i nx_tcpserver.h dla aplikacji serwera HTTP sieci *Web NetX. W przypadku aplikacji klienckich i serwerowych nx_web_http_common.h również musi znajdować się w tym katalogu. nx_md5.c* należy również skopiować do tego katalogu, jeśli jest używane uwierzytelnianie szyfrowane. W przypadku aplikacji demonstracyjnej "sterownik pamięci RAM" pliki klienta i serwera HTTP powinny zostać skopiowane do tego samego katalogu.

W przypadku korzystania z usługi TLS należy mieć oddzielny katalog NetX Secure zawierający pliki źródłowe TLS.

## <a name="using-http"></a>Korzystanie z protokołu HTTP

Korzystanie z internetowego protokołu HTTP NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać elementy *nx_web_http_client.h* i/lub *nx_web_http_server.h* po dołączyć do niego automatycznie elementy *tx_api.h, fx_api.h* i *nx_api.h* (*nx_web_http_common.h).* Te nagłówki umożliwiają aplikacji użycie odpowiednio ThreadX, FileX i NetX Duo. W celu obsługi protokołu HTTPS nagłówki muszą być dołączone po dojechieniu *pliku nx_secure_tls.h* w celu obsługi protokołu TLS.

Gdy pliki nagłówkowe HTTP zostaną dołączone, kod aplikacji będzie mógł wykonać wywołania funkcji HTTP określone w dalszej części tego przewodnika. Aplikacja musi również połączyć się z programem nx_web_http_client.c dla klientów *HTTP(S),* nx_web_http_server.c i nx_tcpserver.c dla serwerów *HTTP(S)* i *nx_md5.c (na* potrzeby uwierzytelniania szyfrowanego) w procesie kompilacji. Te pliki muszą zostać skompilowane w taki sam sposób, jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z internetowego protokołu HTTP NetX.

> [!NOTE]
> Jeśli NX_WEB_HTTP_DIGEST_ENABLE nie zostanie określony w procesie kompilacji, nie trzeba dodawać pliku *md5.c* do aplikacji. Podobnie, jeśli nie są wymagane możliwości klienta HTTP, *plik nx_web_http_client.c* może zostać pominięty i jeśli nie są wymagane możliwości serwera HTTP, *nx_web_http_server.c* może zostać pominięty.
>
> Jeśli NX_WEB_HTTPS_ENABLE jest zdefiniowany w celu włączenia protokołu HTTPS (zamiast używania tylko protokołu HTTP w postaci zwykłego tekstu), protokół NetX Secure TLS nie musi być w kompilacji.
>
> Ponieważ protokół HTTP korzysta z usług TCP NetX, protokół TCP musi zostać włączony przy *użyciu wywołania nx_tcp_enable()* przed użyciem protokołu HTTP.
>
> W przypadku korzystania z protokołu HTTPS z protokołem NetX Secure TLS należy zainicjować protokół TLS *nx_secure_tls_initialize()* przed wywołaniem procedur PROTOKOŁU HTTPS.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład sposobu korzystania z internetowego protokołu HTTP NetX opisano na rysunku 1.1 poniżej.

> [!CAUTION]
> Jest on dostarczany tylko w celach demonstracyjnych i nie ma gwarancji, że zostanie skompilowany i uruchomiony w takim stanie, w jakim jest.
>
> Zapoznaj się z dystrybucją kodu wydania NetX Duo HTTPS dla plików demonstracyjnego kodu źródłowego, które będą poprawnie kompilowane w natywnym środowisku logiki Express.  Należy również pamiętać, że te pokazy są celowo bardzo proste, ponieważ mają na celu wprowadzenie do nowych użytkowników aplikacji HTTPS i/lub NetX Duo HTTPS.

W tym przykładzie pliki dołączane HTTP *nx_web_http_client.h i nx_web_http_server.h* są włączane (plik *netx_web_http_common.h* jest dołączany automatycznie). Następnie serwer HTTP jest tworzony w "*tx_application_define*". Zwróć uwagę, że blok sterowania serwera HTTP *"Serwer"* został wcześniej zdefiniowany jako zmienna globalna. Po pomyślnym utworzeniu zostanie uruchomiony serwer HTTPS. Następnie jest tworzony klient HTTPS. Zapisuje plik i odczytuje go z powrotem.

> [!NOTE]
> NX_WEB_HTTPS_ENABLE jest zdefiniowany w tym systemie.

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
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

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

**Rysunek 1.1 Przykład użycia protokołu HTTPS z protokołem NetX i NetX Secure TLS**

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia protokołu HTTP dla NetX. Poniżej znajduje się lista wszystkich opcji, gdzie każda z nich jest szczegółowo opisana. Wartości domyślne są wyświetlane na liście, ale można je ponownie zdefiniować przed dodaniem parametrów *nx_web_http_client.h i nx_web_http_server.h:*

- **NX_DISABLE_ERROR_CHECKING** Zdefiniowano— ta opcja usuwa podstawowe sprawdzanie błędów HTTP. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_WEB_HTTP_DIGEST_ENABLE** Jeśli ta opcja jest zdefiniowana, uwierzytelnianie przy użyciu skrótu MD5 jest włączone na serwerze HTTPS. Domyślnie nie jest zdefiniowany.
- **NX_WEB_HTTP_SERVER_PRIORITY** Priorytet wątku serwera HTTPS. Domyślnie ta wartość jest zdefiniowana jako 16, aby określić priorytet 16.
- **NX_WEB_HTTP_NO_FILEX** Zdefiniowano, ta opcja zapewnia wycinki dla zależności FileX. Klient HTTPS będzie działać bez żadnych zmian, jeśli ta opcja jest zdefiniowana. Serwer HTTPS musi zostać zmodyfikowany lub użytkownik będzie musiał utworzyć kilka usług FileX, aby działać prawidłowo.
- **NX_WEB_HTTP_TYPE_OF_SERVICE** Typ usługi wymagany dla żądań TCP protokołu HTTPS. Domyślnie ta wartość jest zdefiniowana jako wartość NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.
- **NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** Liczba znaczników czasomierza, które wątek serwera może uruchomić przed uzyskaniem wątków o tym samym priorytecie. Wartość domyślna to 2. Pamiętaj, że ta opcja jest przestarzała.
- **NX_WEB_HTTP_FRAGMENT_OPTION** Włącz fragment dla żądań HTTP TCP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentowanie TCP protokołu HTTP.
- **NX_WEB_HTTP_SERVER_WINDOW_SIZE** Rozmiar okna gniazda serwera. Domyślnie ta wartość to 2048 bajtów.
- **NX_WEB_HTTP_TIME_TO_LIVE** Określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.
- **NX_WEB_HTTP_SERVER_TIMEOUT** Określa liczbę znaczników ThreadX, dla których usługi wewnętrzne będą wstrzymywane. Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać w wewnętrznych *wywołaniach nx_tcp_server_socket_accept().* Wartość domyślna to (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać w wewnętrznych *wywołaniach nx_tcp_socket_disconnect().* Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać w wewnętrznych *wywołaniach nx_tcp_socket_receive().* Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Określa liczbę znaczników ThreadX, które usługi wewnętrzne będą wstrzymywać w wewnętrznych *wywołaniach nx_tcp_socket_send().* Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_MAX_HEADER_FIELD** **określa maksymalny rozmiar pola nagłówka HTTP. Wartość domyślna to 256.**
- **NX_WEB_HTTP_MULTIPART_ENABLE ** ** Jeśli jest zdefiniowana, umożliwia serwerowi HTTPS obsługę wieloczęściowych żądań HTTP. **
- **NX_WEB_HTTP_SERVER_MAX_PENDING** Określa liczbę połączeń, które mogą być w kolejce dla serwera HTTPS. Wartość domyślna jest ustawiana na dwa razy maksymalną liczbę sesji serwera.
- **NX_WEB_HTTP_MAX_RESOURCE** Określa liczbę bajtów dozwolonych w nazwie zasobu *podanego przez klienta.* Wartość domyślna to 40.
- **NX_WEB_HTTP_MAX_NAME** Określa liczbę bajtów dozwolonych w podanej przez klienta nazwie *użytkownika*. Wartość domyślna to 20.
- **NX_WEB_HTTP_MAX_PASSWORD** Określa liczbę bajtów dozwolonych w hasłach podanych przez *klienta.* Wartość domyślna to 20.
- **NX_WEB_HTTP_SERVER_SESSION_MAX** Określa liczbę równoczesnych sesji dla serwera HTTP lub HTTPS. Gniazda TCP i sesja protokołu TLS (jeśli protokół HTTPS jest włączony) są przydzielane dla każdej sesji. Wartość domyślna to 2.
- **NX_WEB_HTTPS_ENABLE** Jeśli to makro jest zdefiniowane, włącza protokoły TLS i HTTPS. Pozostaw niezdefiniowane, aby uwolnić zasoby, jeśli wymagany jest tylko zwykły tekst HTTP. Domyślnie to makro nie jest zdefiniowane.
- **NX_WEB_HTTPS_KEEPALIVE_DISABLE** Jeśli to makro jest zdefiniowane, wyłącza funkcję utrzymania aktywności protokołu HTTP. Domyślnie to makro nie jest zdefiniowane.
- **NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia serwera. Minimalny rozmiar jest wymagany do zapewnienia, że pełny nagłówek HTTP może być zawarty w jednym pakiecie. Wartość domyślna to 600.
- **NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia klienta. Minimalny rozmiar jest wymagany do zapewnienia, że pełny nagłówek HTTP może być zawarty w jednym pakiecie. Wartość domyślna to 600.
- **NX_WEB_HTTP_SERVER_RETRY_SECONDS** Ustaw limit czasu retransmisji gniazda serwera w sekundach. Wartość domyślna to 2.
- **NX_WEB_HTTP_ SERVER_RETRY_MAX** Określa maksymalną liczbę retransmisji na gniazda serwera. Wartość domyślna to 10.
- **NX_WEB_HTTP_ SERVER_RETRY_SHIFT** Ta wartość jest używana do ustawienia następnego limitu czasu ponownej transmisji. Bieżący limit czasu jest mnożony przez liczbę do tej pory retransmisji, przesunięte przez wartość przesunięcia limitu czasu gniazda. Wartość domyślna jest ustawiona na 1 dla podwojenia limitu czasu.
- **NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** Określa maksymalną liczbę pakietów, które mogą być w kolejce w kolejce retransmisji gniazda serwera. Jeśli liczba pakietów w kolejkach osiągnie tę liczbę, nie będzie można wysłać więcej pakietów, dopóki co najmniej jeden pakiet w kolejkach nie zostanie zwolniony. Wartość domyślna to 20.
