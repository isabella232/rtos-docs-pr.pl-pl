---
title: Rozdział 2 — Instalowanie i korzystanie z protokołów HTTP i HTTPS
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika HTTP sieci Web NetX.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821607"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a><span data-ttu-id="5e6b9-103">Rozdział 2 — Instalowanie i korzystanie z protokołów HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="5e6b9-103">Chapter 2 - Installation and use of HTTP and HTTPS</span></span>

<span data-ttu-id="5e6b9-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika HTTP sieci Web NetX.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Web HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5e6b9-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="5e6b9-105">Product Distribution</span></span>

<span data-ttu-id="5e6b9-106">Protokół HTTP for NetX jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="5e6b9-106">HTTP for NetX is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="5e6b9-107">Pakiet zawiera trzy pliki źródłowe, dwa pliki dołączane i plik, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e6b9-107">The package includes three source files, two include files, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="5e6b9-108">**nx_web_http_common. h** Wspólny plik nagłówka dla sieci Web HTTP NetX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-108">**nx_web_http_common.h** Common header file for NetX Web HTTP</span></span>
- <span data-ttu-id="5e6b9-109">**nx_web_http_client. h** Plik nagłówka dla klienta HTTP dla sieci Web NetX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-109">**nx_web_http_client.h** Header file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="5e6b9-110">**nx_web_http_server. h** Plik nagłówka dla serwera HTTP dla sieci Web NetX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-110">**nx_web_http_server.h** Header file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="5e6b9-111">**nx_web_http_client. c** Plik źródłowy języka C dla klienta HTTP dla sieci Web NetX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-111">**nx_web_http_client.c** C Source file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="5e6b9-112">**nx_web_http_server. c** Plik źródłowy języka C dla serwera HTTP dla sieci Web NetX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-112">**nx_web_http_server.c** C Source file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="5e6b9-113">**nx_tcpserver. c** Plik źródłowy języka C dla wielu gniazd TCP</span><span class="sxs-lookup"><span data-stu-id="5e6b9-113">**nx_tcpserver.c** C Source file for multiple TCP sockets</span></span>
- <span data-ttu-id="5e6b9-114">**nx_tcpserver. h** Plik nagłówka do definiowania symboli serwera HTTPS</span><span class="sxs-lookup"><span data-stu-id="5e6b9-114">**nx_tcpserver.h** Header file for defining HTTPS Server symbols</span></span>
- <span data-ttu-id="5e6b9-115">**nx_md5. c** Algorytmy Digest MD5</span><span class="sxs-lookup"><span data-stu-id="5e6b9-115">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="5e6b9-116">**filex_stub. h** Plik zastępczy, jeśli nie istnieje FileX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-116">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="5e6b9-117">**nx_web_http.pdf** Opis protokołu HTTP dla sieci Web NetX</span><span class="sxs-lookup"><span data-stu-id="5e6b9-117">**nx_web_http.pdf** Description of HTTP for NetX Web</span></span>
- <span data-ttu-id="5e6b9-118">**demo_netx_web_http. c** Demonstracja HTTP NetX w sieci Web</span><span class="sxs-lookup"><span data-stu-id="5e6b9-118">**demo_netx_web_http.c** NetX Web HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="5e6b9-119">Instalacja HTTP</span><span class="sxs-lookup"><span data-stu-id="5e6b9-119">HTTP Installation</span></span>

<span data-ttu-id="5e6b9-120">Aby można było korzystać z sieci Web HTTP NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-120">In order to use NetX Web HTTP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="5e6b9-121">Na przykład jeśli NetX Duo jest zainstalowany w katalogu "*\threadx\arm7\green*", a następnie *nx_web_http_client. h* i *Nx_web_http_client. c dla aplikacji klienckich http w sieci Web, a nx_web_http_server. h*, *nx_web_http_server. c, nx_tcpserver. c i Nx_tcpserver. h dla NetX sieci Web serwera http. W przypadku aplikacji klienckich i serwerowych nx_web_http_common. h musi znajdować się również w tym katalogu.* jeśli jest używane uwierzytelnianie szyfrowane, nx_md5. c należy również skopiować do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-121">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nx_web_http_client.h* and *nx_web_http_client.c for NetX Web HTTP Client applications, and nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c and nx_tcpserver.h for NetX Web HTTP Server applications. For both client and server applications, nx_web_http_common.h must be in this directory as well. nx_md5.c* should also be copied into this directory if digest authentication is being used.</span></span> <span data-ttu-id="5e6b9-122">W przypadku demonstracyjnego "sterownika pamięci RAM aplikacji klienta HTTP i plików serwera należy skopiować do tego samego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-122">For the demo ‘ram driver’ application HTTP Client and Server files should be copied into the same directory.</span></span>

<span data-ttu-id="5e6b9-123">W przypadku korzystania z protokołu TLS należy mieć oddzielny NetX bezpieczny katalog zawierający pliki źródłowe protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-123">If using TLS, you should have a separate NetX Secure directory containing the TLS source files.</span></span>

## <a name="using-http"></a><span data-ttu-id="5e6b9-124">Korzystanie z protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="5e6b9-124">Using HTTP</span></span>

<span data-ttu-id="5e6b9-125">Używanie protokołu HTTP w sieci Web NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-125">Using NetX Web HTTP is easy.</span></span> <span data-ttu-id="5e6b9-126">W zasadzie kod aplikacji musi zawierać *nx_web_http_client. h* i/lub *nx_web_http_server. h* po uwzględnieniu *tx_api. h, fx_api. h* i *nx_api. h* (*nx_web_http_common. h* jest automatycznie dołączany).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-126">Basically, the application code must include *nx_web_http_client.h* and/or *nx_web_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h* (*nx_web_http_common.h* is automatically included).</span></span> <span data-ttu-id="5e6b9-127">Te nagłówki umożliwiają aplikacji użycie odpowiednio ThreadX, FileX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-127">Those headers enable the application to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="5e6b9-128">W przypadku obsługi protokołu HTTPS nagłówki muszą być zawarte po dołączeniu pliku *nx_secure_tls. h* , aby zapewnić obsługę protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-128">For HTTPS support, the headers must be included after the *nx_secure_tls.h* file is included to bring in TLS support.</span></span>

<span data-ttu-id="5e6b9-129">Po uwzględnieniu plików nagłówkowych HTTP, kod aplikacji może być w stanie wprowadzić wywołania funkcji HTTP określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-129">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="5e6b9-130">Aplikacja musi również łączyć się z *nx_web_http_client. c dla klientów http (s)*, *nx_web_http_server. c i nx_tcpserver. c dla serwerów HTTP (s)* i *nx_md5. c (na potrzeby uwierzytelniania szyfrowanego)* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-130">The application must also link with *nx_web_http_client.c for HTTP(S) clients*, *nx_web_http_server.c and nx_tcpserver.c for HTTP(S) servers*, and *nx_md5.c (for digest authentication)* in the build process.</span></span> <span data-ttu-id="5e6b9-131">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-131">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="5e6b9-132">To wszystko, co jest wymagane do używania protokołu HTTP w sieci Web NetX.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-132">This is all that is required to use NetX Web HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="5e6b9-133">Jeśli nie określono NX_WEB_HTTP_DIGEST_ENABLE w procesie kompilacji, plik *MD5. c* nie musi być dodany do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-133">If NX_WEB_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="5e6b9-134">Analogicznie, jeśli nie są wymagane możliwości klienta HTTP, plik *nx_web_http_client. c* może zostać pominięty i jeśli nie są wymagane żadne możliwości serwera HTTP, *nx_web_http_server. c* może zostać pominięty.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-134">Similarly, if no HTTP Client capabilities are required, the *nx_web_http_client.c* file may be omitted and if no HTTP Server capabilities are required, *nx_web_http_server.c* may be omitted.</span></span>
>
> <span data-ttu-id="5e6b9-135">Chyba że NX_WEB_HTTPS_ENABLE jest zdefiniowany w celu włączenia protokołu HTTPS (zamiast używania tylko zwykłego tekstu HTTP), NetX Secure TLS nie musi być w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-135">Unless NX_WEB_HTTPS_ENABLE is defined in order to enable HTTPS (instead of using only plaintext HTTP) then NetX Secure TLS does not need to be in the build.</span></span>
>
> <span data-ttu-id="5e6b9-136">Ponieważ protokół HTTP wykorzystuje usługi NetX TCP, należy włączyć TCP przy użyciu wywołania *nx_tcp_enable ()* przed użyciem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-136">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable()* call prior to using HTTP.</span></span>
>
> <span data-ttu-id="5e6b9-137">W przypadku korzystania z protokołu HTTPS z NetX Secure TLS należy zainicjować protokół TLS przy użyciu *nx_secure_tls_initialize ()* przed wywołaniem procedur https.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-137">When using HTTPS with NetX Secure TLS, TLS must be initialized with *nx_secure_tls_initialize()* prior to calling HTTPS routines.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="5e6b9-138">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="5e6b9-138">Small Example System</span></span>

<span data-ttu-id="5e6b9-139">Przykład użycia protokołu HTTP w sieci Web NetX został opisany na rysunku 1,1 poniżej.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-139">An example of how to use NetX Web HTTP is described in Figure 1.1 below.</span></span>

> [!CAUTION]
> <span data-ttu-id="5e6b9-140">Jest to możliwe tylko w celach demonstracyjnych i nie jest gwarantowane Kompilowanie i uruchamianie jako.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-140">This is provided for demonstration purposes only and is not guaranteed to compile and run as is.</span></span>
>
> <span data-ttu-id="5e6b9-141">Zapoznaj się z dystrybucją kodu HTTPS NetX Duo dla demonstracyjnych plików kodu źródłowego, które będą prawidłowo skompilowane w natywnym środowisku logiki Express.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-141">Please refer to the NetX Duo HTTPS release code distribution for  demo source code file(s) that will properly build in the native Express Logic environment.</span></span>  <span data-ttu-id="5e6b9-142">Należy również pamiętać, że te pokazy są celowo bardzo proste, ponieważ mają one wprowadzić aplikacje HTTPS i/lub NetX Duo dla nowych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-142">Also be aware that these demos are intentionally kept very simple as they are intended to introduce HTTPS and/or NetX Duo HTTPS application to new users.</span></span>

<span data-ttu-id="5e6b9-143">W tym przykładzie plik dołączany HTTP *nx_web_http_client. h i nx_web_http_server. h są* włączone (*netx_web_http_common. h* jest dołączany automatycznie).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-143">In this example, the HTTP include file *nx_web_http_client.h and nx_web_http_server.h are* brought in (*netx_web_http_common.h* is included automatically).</span></span> <span data-ttu-id="5e6b9-144">Następnie serwer HTTP jest tworzony w "*tx_application_define*".</span><span class="sxs-lookup"><span data-stu-id="5e6b9-144">Next, the HTTP Server is created in “*tx_application_define*”.</span></span> <span data-ttu-id="5e6b9-145">Należy zauważyć, że blok kontroli serwera HTTP "*serwer*" został wcześniej zdefiniowany jako zmienna globalna.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-145">Note that the HTTP Server control block “*Server*” was defined as a global variable previously.</span></span> <span data-ttu-id="5e6b9-146">Po pomyślnym utworzeniu serwer HTTPS zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-146">After successful creation, the HTTPS Server is started.</span></span> <span data-ttu-id="5e6b9-147">Następnie klient HTTPS jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-147">The HTTPS Client is then created.</span></span> <span data-ttu-id="5e6b9-148">Zapisuje plik i odczytuje go z powrotem.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-148">It writes the file and reads the file back.</span></span>

> [!NOTE]
> <span data-ttu-id="5e6b9-149">NX_WEB_HTTPS_ENABLE jest zdefiniowany w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-149">NX_WEB_HTTPS_ENABLE is defined on this system.</span></span>

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

<span data-ttu-id="5e6b9-150">**Rysunek 1,1 przykład użycia protokołu HTTPS z NetX i NetX Secure TLS**</span><span class="sxs-lookup"><span data-stu-id="5e6b9-150">**Figure 1.1 Example of HTTPS use with NetX and NetX Secure TLS**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="5e6b9-151">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5e6b9-151">Configuration Options</span></span>

<span data-ttu-id="5e6b9-152">Istnieje kilka opcji konfiguracji do kompilowania protokołu HTTP dla NetX.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-152">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="5e6b9-153">Poniżej znajduje się lista wszystkich opcji, w których poszczególne są szczegółowo opisane.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-153">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="5e6b9-154">Wartości domyślne są wyświetlane, ale można je zdefiniować ponownie przed włączeniem *nx_web_http_client. h i nx_web_http_server. h*:</span><span class="sxs-lookup"><span data-stu-id="5e6b9-154">The default values are listed but can be redefined prior to inclusion of *nx_web_http_client.h and nx_web_http_server.h*:</span></span>

- <span data-ttu-id="5e6b9-155">**NX_DISABLE_ERROR_CHECKING** Zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów HTTP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-155">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="5e6b9-156">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-156">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="5e6b9-157">**NX_WEB_HTTP_DIGEST_ENABLE** W przypadku zdefiniowania uwierzytelniania przy użyciu skrótu MD5 jest włączony na serwerze HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-157">**NX_WEB_HTTP_DIGEST_ENABLE** If defined, authentication using the MD5 digest is enabled on the HTTPS Server.</span></span> <span data-ttu-id="5e6b9-158">Domyślnie nie jest on zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-158">By default it is not defined.</span></span>
- <span data-ttu-id="5e6b9-159">**NX_WEB_HTTP_SERVER_PRIORITY** Priorytet wątku serwera HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-159">**NX_WEB_HTTP_SERVER_PRIORITY** The priority of the HTTPS Server thread.</span></span> <span data-ttu-id="5e6b9-160">Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-160">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="5e6b9-161">**NX_WEB_HTTP_NO_FILEX** Zdefiniowana, ta opcja udostępnia element zastępczy dla zależności FileX.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-161">**NX_WEB_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="5e6b9-162">Klient HTTPS będzie działać bez żadnej zmiany, jeśli ta opcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-162">The HTTPS Client will function without any change if this option is defined.</span></span> <span data-ttu-id="5e6b9-163">Należy zmodyfikować serwer HTTPS lub użytkownik będzie musiał utworzyć kilku usługi FileX, aby działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-163">The HTTPS Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="5e6b9-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Typ usługi wymaganej przez żądania protokołu HTTPS TCP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTPS TCP requests.</span></span> <span data-ttu-id="5e6b9-165">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="5e6b9-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** Liczba cykli czasomierza, które mogą być uruchamiane przez wątek serwera przed zwróceniem do wątków o takim samym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="5e6b9-167">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-167">The default value is 2.</span></span> <span data-ttu-id="5e6b9-168">Należy pamiętać, że ta opcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-168">Note this option is deprecated.</span></span>
- <span data-ttu-id="5e6b9-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Włączenie fragmentu dla żądań HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="5e6b9-170">Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentację TCP protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-170">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="5e6b9-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Rozmiar okna gniazda serwera.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="5e6b9-172">Wartość domyślna to 2048 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-172">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="5e6b9-173">**NX_WEB_HTTP_TIME_TO_LIVE** Określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-173">**NX_WEB_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="5e6b9-174">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-174">The default value is set to 0x80.</span></span>
- <span data-ttu-id="5e6b9-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Określa liczbę ThreadXych taktów, dla których będą zawieszane usługi wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="5e6b9-176">Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-176">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="5e6b9-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_server_socket_accept ()* .</span><span class="sxs-lookup"><span data-stu-id="5e6b9-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept()* calls.</span></span> <span data-ttu-id="5e6b9-178">Wartość domyślna to (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-178">The default value is set to (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="5e6b9-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_socket_disconnect ()* .</span><span class="sxs-lookup"><span data-stu-id="5e6b9-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect()* calls.</span></span> <span data-ttu-id="5e6b9-180">Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-180">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="5e6b9-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_socket_receive ()* .</span><span class="sxs-lookup"><span data-stu-id="5e6b9-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive()* calls.</span></span> <span data-ttu-id="5e6b9-182">Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-182">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="5e6b9-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Określa liczbę ThreadXych taktów, które zostaną zawieszone przez usługi wewnętrzne w ramach wywołań wewnętrznych *nx_tcp_socket_send ()* .</span><span class="sxs-lookup"><span data-stu-id="5e6b9-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send()* calls.</span></span> <span data-ttu-id="5e6b9-184">Wartość domyślna to 10 sekund (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-184">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="5e6b9-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **określa maksymalny rozmiar pola nagłówka HTTP. Wartość domyślna to 256.**</span><span class="sxs-lookup"><span data-stu-id="5e6b9-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Specifies the maximum size of the HTTP header field. The default value is 256.**</span></span>
- <span data-ttu-id="5e6b9-186">\* \* NX_WEB_HTTP_MULTIPART_ENABLE \* \* \* \* \* \*, jeśli jest zdefiniowany, włącza serwer HTTPS do obsługi wieloczęściowych żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*If defined, enables HTTPS Server to support multipart HTTP requests.</span></span> **
- <span data-ttu-id="5e6b9-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Określa liczbę połączeń, które mogą być umieszczone w kolejce dla serwera HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTPS Server.</span></span> <span data-ttu-id="5e6b9-188">Wartość domyślna to dwukrotnie większa liczba sesji serwera.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-188">The default value is set to twice the maximum number of server sessions.</span></span>
- <span data-ttu-id="5e6b9-189">**NX_WEB_HTTP_MAX_RESOURCE** Określa liczbę bajtów dozwolonych w *nazwie zasobu* dostarczonej przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-189">**NX_WEB_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="5e6b9-190">Wartość domyślna to 40.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-190">The default value is set to 40.</span></span>
- <span data-ttu-id="5e6b9-191">**NX_WEB_HTTP_MAX_NAME** Określa liczbę bajtów dozwolonych w *nazwie użytkownika* dostarczonej przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-191">**NX_WEB_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="5e6b9-192">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-192">The default value is set to 20.</span></span>
- <span data-ttu-id="5e6b9-193">**NX_WEB_HTTP_MAX_PASSWORD** Określa liczbę bajtów dozwolonych w *haśle* dostarczonym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-193">**NX_WEB_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="5e6b9-194">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-194">The default value is set to 20.</span></span>
- <span data-ttu-id="5e6b9-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Określa liczbę równoczesnych sesji dla serwera HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Specifies the number of simultaneous sessions for an HTTP or HTTPS Server.</span></span> <span data-ttu-id="5e6b9-196">Gniazdo TCP i sesja TLS (jeśli jest włączona obsługa protokołu HTTPS) są przydzieleni dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-196">A TCP socket and a TLS session (if HTTPS is enabled) are allocated for each session.</span></span> <span data-ttu-id="5e6b9-197">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-197">The default value is set to 2.</span></span>
- <span data-ttu-id="5e6b9-198">**NX_WEB_HTTPS_ENABLE** W przypadku zdefiniowania tego makra włącza protokoły TLS i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-198">**NX_WEB_HTTPS_ENABLE** If defined, this macro enables TLS and HTTPS.</span></span> <span data-ttu-id="5e6b9-199">Pozostaw niezdefiniowane, aby zwolnić zasoby, jeśli jest wymagany tylko zwykły tekst HTTP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-199">Leave undefined to free up resources if only plaintext HTTP is desired.</span></span> <span data-ttu-id="5e6b9-200">Domyślnie to makro nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-200">By default, this macro is not defined.</span></span>
- <span data-ttu-id="5e6b9-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** Jeśli ta opcja jest zdefiniowana, to makro wyłącza funkcję Keep-Alive protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** If defined, this macro disables HTTP keep-alive feature.</span></span> <span data-ttu-id="5e6b9-202">Domyślnie to makro nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-202">By default, this macro is not defined.</span></span>
- <span data-ttu-id="5e6b9-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia serwera.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at server creation.</span></span> <span data-ttu-id="5e6b9-204">Minimalny rozmiar jest wymagany w celu zapewnienia, że kompletny nagłówek HTTP może być zawarty w jednym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-204">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="5e6b9-205">Wartość domyślna to 600.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-205">The default value is set to 600.</span></span>
- <span data-ttu-id="5e6b9-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Określa minimalny rozmiar pakietów w puli określonej podczas tworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="5e6b9-207">Minimalny rozmiar jest wymagany w celu zapewnienia, że kompletny nagłówek HTTP może być zawarty w jednym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-207">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="5e6b9-208">Wartość domyślna to 600.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-208">The default value is set to 600.</span></span>
- <span data-ttu-id="5e6b9-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Ustaw limit czasu ponownej transmisji gniazda serwera (w sekundach).</span><span class="sxs-lookup"><span data-stu-id="5e6b9-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="5e6b9-210">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-210">The default value is set to 2.</span></span>
- <span data-ttu-id="5e6b9-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** Ustawia maksymalną liczbę ponownych transmisji w gnieździe serwera.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="5e6b9-212">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-212">The default value is set to 10.</span></span>
- <span data-ttu-id="5e6b9-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** Ta wartość jest używana do ustawiania następnego limitu czasu ponownej transmisji.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="5e6b9-214">Bieżący limit czasu jest mnożony przez liczbę ponownych transmisji do tej pory, przesuniętych przez wartość przedziału czasu gniazda.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-214">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="5e6b9-215">Wartość domyślna to 1 w przypadku podwajania limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-215">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="5e6b9-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** Określa maksymalną liczbę pakietów, które można umieścić w kolejce kolejki retransmisji w gnieździe serwera.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="5e6b9-217">Jeśli liczba pakietów w kolejce osiągnie tę liczbę, nie można wysyłać kolejnych pakietów, dopóki nie zostaną wydane co najmniej jeden pakiet z kolejki.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-217">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="5e6b9-218">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5e6b9-218">The default value is set to 20.</span></span>
