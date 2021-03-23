---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Secure DTLS
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika bezpiecznego DTLS usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3533471edf17ec6e812027ef0af672a00773f968
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821595"
---
# <a name="chapter-2-installation-and-use-of-azure-rtos-netx-secure-dtls"></a><span data-ttu-id="b15df-103">Rozdział 2: Instalowanie i korzystanie z usługi Azure RTO NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-103">Chapter 2: Installation and use of Azure RTOS NetX Secure DTLS</span></span>

<span data-ttu-id="b15df-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika bezpiecznego DTLS usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="b15df-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Secure DTLS component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b15df-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="b15df-105">Product Distribution</span></span>

<span data-ttu-id="b15df-106">Zabezpieczenia NetX są dostępne pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="b15df-106">NetX Secure is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="b15df-107">Pakiet zawiera pliki źródłowe, pliki dołączane oraz plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b15df-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="b15df-108">**nx_secure_dtls_api. h** Publiczny plik nagłówkowy interfejsu API dla NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-108">**nx_secure_dtls_api.h** Public API header file for NetX Secure DTLS</span></span>
- <span data-ttu-id="b15df-109">**nx_secure_dtls_user. h** Użytkownik definiuje plik nagłówka dla NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-109">**nx_secure_dtls_user.h** User defines header file for NetX Secure DTLS</span></span>
- <span data-ttu-id="b15df-110">**nx_secure_ port. h** Definicje specyficzne dla platformy dla NetX Secure</span><span class="sxs-lookup"><span data-stu-id="b15df-110">**nx_secure_ port.h** Platform-specific definitions for NetX Secure</span></span>
- <span data-ttu-id="b15df-111">**nx_secure_dtls. h** Plik nagłówka dla NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-111">**nx_secure_dtls.h** Header file for NetX Secure DTLS</span></span>
- <span data-ttu-id="b15df-112">**nx_secure_tls. h** Plik nagłówka dla protokołu Secure TLS NetX</span><span class="sxs-lookup"><span data-stu-id="b15df-112">**nx_secure_tls.h** Header file for NetX Secure TLS</span></span>
- <span data-ttu-id="b15df-113">**nx_secure_dtls \* . c/h** pliki źródłowe c/h dla NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-113">**nx_secure_dtls\*.c/h** C/H Source files for NetX Secure DTLS</span></span>
- <span data-ttu-id="b15df-114">**nx_secure_tls \* . c/h** pliki źródłowe c/h dla NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="b15df-114">**nx_secure_tls\*.c/h** C/H Source files for NetX Secure TLS</span></span>
- <span data-ttu-id="b15df-115">**nx_crypto \* . c/h** pliki źródłowe c/h dla bezpiecznego kryptografii NetX</span><span class="sxs-lookup"><span data-stu-id="b15df-115">**nx_crypto\*.c/h** C/H Source files for NetX Secure Cryptography</span></span>
- <span data-ttu-id="b15df-116">**nx_secure_x509 \* . c/h** pliki źródłowe c/h dla certyfikatów cyfrowych X. 509.</span><span class="sxs-lookup"><span data-stu-id="b15df-116">**nx_secure_x509\*.c/h** C/H Source files for X.509 digital certificates.</span></span>
- <span data-ttu-id="b15df-117">**demo_netx_secure_dtls. c** Plik źródłowy języka C dla demonstracji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-117">**demo_netx_secure_dtls.c** C Source file for NetX Secure DTLS Demo</span></span>
- <span data-ttu-id="b15df-118">**NetX_Secure_DTLS_User_Guide.pdf** Opis pliku PDF NetX bezpiecznego produktu</span><span class="sxs-lookup"><span data-stu-id="b15df-118">**NetX_Secure_DTLS_User_Guide.pdf** PDF description of NetX Secure product</span></span>

> [!NOTE]
> <span data-ttu-id="b15df-119">Pliki nx_crypto \* są dostępne dla różnych platform sprzętowych w podkatalogu bezpiecznego katalogu nadrzędnego NetX.</span><span class="sxs-lookup"><span data-stu-id="b15df-119">The nx_crypto\* files are provided for different hardware platforms in a subdirectory of the NetX Secure parent directory.</span></span>

## <a name="netx-secure-dtls-installation"></a><span data-ttu-id="b15df-120">NetX bezpieczną DTLS</span><span class="sxs-lookup"><span data-stu-id="b15df-120">NetX Secure DTLS Installation</span></span>

<span data-ttu-id="b15df-121">Aby można było użyć usługi NetX Secure DTLS, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego poziomu katalogu, gdzie zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="b15df-121">In order to use NetX Secure DTLS, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="b15df-122">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\NetX*", to *nx_secure \* \* .* katalogi powinny być kopiowane do "*\threadx\arm7\NetXSecure*".</span><span class="sxs-lookup"><span data-stu-id="b15df-122">For example, if NetX is installed in the directory “*\threadx\arm7\NetX*” then the *nx_secure\*.\** directories should be copied into “*\threadx\arm7\NetXSecure*”.</span></span>

## <a name="using-netx-secure-dlts"></a><span data-ttu-id="b15df-123">Korzystanie z NetX Secure DLTS</span><span class="sxs-lookup"><span data-stu-id="b15df-123">Using NetX Secure DLTS</span></span>

<span data-ttu-id="b15df-124">Używanie NetX Secure DTLS jest proste.</span><span class="sxs-lookup"><span data-stu-id="b15df-124">Using NetX Secure DTLS is straightforward.</span></span> <span data-ttu-id="b15df-125">Kod aplikacji musi zawierać *nx_secure_dtls_api. h* po tym *tx_api. h* i *nx_api. h* (odpowiednio dla ThreadX i NetX).</span><span class="sxs-lookup"><span data-stu-id="b15df-125">The application code must include *nx_secure_dtls_api.h* after it includes *tx_api.h* and *nx_api.h* (which are for ThreadX and NetX, respectively).</span></span> <span data-ttu-id="b15df-126">Po dołączeniu *nx_secure_dtls_api. h* kod aplikacji jest następnie w stanie zapewnić, że wywołania funkcji NetX bezpiecznego DTLS określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b15df-126">Once *nx_secure_dtls_api.h* is included, the application code is then able to make the NetX Secure DTLS function calls specified later in this guide.</span></span> <span data-ttu-id="b15df-127">Aplikacja musi również zaimportować pliki *nx_secure \* . \** Files do biblioteki NetXSecure, a *\* \** specyficzne dla platformy nx_crypto pliki do biblioteki NetXCrypto, które następnie są połączone z plikiem binarnym aplikacji końcowej.</span><span class="sxs-lookup"><span data-stu-id="b15df-127">The application must also import the *nx_secure\*.\** files into a NetXSecure library, and the platform-specific *nx_crypto\*.\** files into a NetXCrypto library which are then linked into the final application binary.</span></span>

## <a name="small-example-system-dtls-client"></a><span data-ttu-id="b15df-128">Mały przykładowy system (klient DTLS)</span><span class="sxs-lookup"><span data-stu-id="b15df-128">Small Example System (DTLS Client)</span></span>

<span data-ttu-id="b15df-129">Przykładem łatwego użycia NetX Secure DTLS jest opisany na rysunku 1,1, który pojawia się poniżej i demonstruje prostego klienta DTLS, zaprojektowanego do pracy z serwerem OpenSSL (lub podobnym) DTLS.</span><span class="sxs-lookup"><span data-stu-id="b15df-129">An example of how easy it is to use NetX Secure DTLS is described in Figure 1.1, which appears below and demonstrates a simple DTLS Client, designed to work with an OpenSSL (or similar) DTLS server.</span></span> <span data-ttu-id="b15df-130">Należy pamiętać, że struktura programu klienckiego DTLS jest bardzo podobna do klienta NetX Secure TLS (zobacz NetX Secure TLS Documentation).</span><span class="sxs-lookup"><span data-stu-id="b15df-130">Note that the DTLS client program structure is very similar to a NetX Secure TLS Client (see NetX Secure TLS documentation).</span></span> <span data-ttu-id="b15df-131">Wynika to z faktu, że protokół DTLS jest zasadniczo wersją protokołu TLS do użycia za pośrednictwem niezawodnych protokołów sieciowych transportu, takich jak UDP.</span><span class="sxs-lookup"><span data-stu-id="b15df-131">This is because the DTLS protocol is essentially a version of TLS for use over unreliable transport network protocols such as UDP.</span></span>

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_dtls_api.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS      IP_ADDRESS(192, 168, 1, 1)

/* Define the remote server port. */
#define     REMOTE_SERVER_PORT           4443

/* Define the size of the buffer used for incoming certificates. The
   Buffer will contain both the raw certificate data and an instance
   of the NX_SECURE_X509_CERT structure used for X.509 parsing. */
#define     REMOTE_CERT_BUFFER_SIZE     (sizeof(NX_SECURE_X509_CERT) + 2000)

/* Define the number of certificates we expect to receive from the server
   so we can allocate enough space for them. */
#define     REMOTE_CERT_NUMBER          2

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_UDP_SOCKET udp_socket;
NX_SECURE_DTLS_SESSION dtls_session;
NX_SECURE_X509_CERTIFICATE dtls_certificate;

/* Define space for remote certificate storage. The size of the
buffer is determined by the expected number of certificates times
the expected size of each certificate.   */
UCHAR remote_certificate_buffer[REMOTE_CERT_BUFFER_SIZE * REMOTE_CERT_NUMBER];

/* Define some data to send to the DTLS server. */
UCHAR request_data[] = { … };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the DTLS Client thread.  */
ULONG             dtls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         dtls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the DTLS packet reassembly buffer. */
UCHAR dtls_packet_buffer[4000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR dtls_crypto_metadata[14000];

/* Pointer to the TLS/DTLS ciphersuite table that is included in the platform-
specific cryptography subdirectory. The table maps the cryptographic routines for
the platform to function pointers usable by the DTLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Binary data for the DTLS Client X.509 trusted root CA certificate: ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS/DTLS Client applications
   (unless an alternate authentication mechanism is used, such as PSK) or DTLS will
treat all certificates as untrusted and the handshake will fail.
*/
const UCHAR trusted_ca_data[] = { … }; /* DER-encoded binary certificate. */
const UINT trusted_ca_length[] = 0x574;

/* Define the application – initialize drivers and UDP setup.  */
void    tx_application_define(void *first_unused_memory)
{
    UINT  status;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
   NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, …);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable UDP traffic. Check status for errors. */
    status =  nx_udp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS/DTLS system.  */
   nx_secure_tls_initialize();

    /* Create the client thread to start handling incoming requests. */
    tx_thread_create(&dtls_client_thread, "DTLS Client thread", client_thread_entry,
        0, dtls_client_thread_stack, sizeof(dtls_client_thread_stack),
        16, 16, 4, TX_AUTO_START);
}

     /* Thread to handle the DTLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
    UINT       status;
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UCHAR receive_buffer[100];
    ULONG bytes;
    ULONG server_ipv4_address;

     /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
        NX_IP_PERIODIC_RATE);

    /* Check status for errors... */

    /* Create a UDP socket to use for our DTLS session.  */
    status =  nx_udp_socket_create(&ip_0, &udp_socket, "DTLS Client Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192);

    /* Check status for errors... */

    /* Create a DTLS session for our socket. This sets up the DTLS session object for
            later use with encryption, packet buffer space for decryption, and buffer
    space for incoming server X.509 certificates. */
    status =  nx_secure_dtls_session_create(&dtls_session,
        &nx_crypto_tls_ciphers,
        tls_crypto_metadata,
        sizeof(tls_crypto_metadata),
        dtls_packet_buffer,
        sizeof(dtls_packet_buffer),
        REMOTE_CERT_NUMBER,
        remote_certificate_buffer,
        sizeof(remote_certificate_buffer) );

    /* Initialize an X.509 certificate with our CA root certificate data. */
    nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
        trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the initialized certificate as a trusted root certificate. */
    nx_secure_dtls_session_trusted_certificate_add(&dtls_session, &certificate);

    /* Setup this thread to open a connection on the UDP socket to a remote server.
       The IP address can be used directly or it can be obtained via DNS or other
       means.  */
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;

   /* Check for errors…  */

    /* Start the DTLS Session using the given UDP socket, remote server IP Address,
        and remote server port. */
    status = nx_secure_dtls_client_session_start(&dtls_session, &udp_socket,
        &ip_address, REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

        /* Allocate a DTLS packet to send some encrypted data to the server. */
        status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &send_packet,
     NX_TLS_PACKET, NX_WAIT_FOREVER);

        /* Check for errors…  */

         /* Populate the packet with some data. */
        nx_packet_data_append(send_packet, request_data, sizeof(request_data), &pool_0,
            NX_WAIT_FOREVER);

         /* Send the request over the DTLS Session, encrypting it before sending. */
    status = nx_secure_dtls_session_send(&dtls_session, send_packet, NX_WAIT_FOREVER);

        /* Check for errors…  */
        if (status)
        {
              /* Release the packet since we could not send it.  */
              nx_packet_release(send_packet);
        }

     /* Receive the response from the server. */
    status = nx_secure_dtls_session_receive(&dtls_session, &receive_packet,
       NX_WAIT_FOREVER);

    /* Extract the data we received from the remote server. */
    status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer, 100,
        &bytes);
    /* Display the response data. */
    receive_buffer[bytes] = 0;
    printf("Received data: %s\n", receive_buffer)
     /* End the DTLS session now that we have received our response. */
    status = nx_secure_dtls_session_end(&tls_session, NX_WAIT_FOREVER)

     /* Check for errors to make sure the session ended cleanly. */
     /* Clean up the UDP socket. */
    status =  nx_udp_socket_delete(&udp_socket)

    /* Check for errors... */

}
```

<span data-ttu-id="b15df-132">**Rysunek 1,1 przykład bezpiecznego użycia NetX z NetX**</span><span class="sxs-lookup"><span data-stu-id="b15df-132">**Figure 1.1 Example of NetX Secure use with NetX**</span></span>

## <a name="small-example-system-dtls-server"></a><span data-ttu-id="b15df-133">Mały przykładowy system (DTLS Server)</span><span class="sxs-lookup"><span data-stu-id="b15df-133">Small Example System (DTLS Server)</span></span>

<span data-ttu-id="b15df-134">Przykład łatwego korzystania z NetX Secure jest opisany na rysunku 1,2, który pojawia się poniżej i demonstruje prosty serwer DTLS.</span><span class="sxs-lookup"><span data-stu-id="b15df-134">An example of how easy it is to use NetX Secure is described in Figure 1.2, which appears below and demonstrates a simple DTLS Server.</span></span> <span data-ttu-id="b15df-135">Należy zauważyć, że funkcjonalność serwera DTLS jest zupełnie inna od klienta DTLS i klienta/serwera TLS, ponieważ serwer DTLS musi zarządzać wieloma przychodzącymi żądaniami klientów na pojedynczym porcie UDP (przechowywanym w wystąpieniu serwera DTLS).</span><span class="sxs-lookup"><span data-stu-id="b15df-135">Note that the DTLS Server functionality is quite different from DTLS Client and TLS Client/Server since the DTLS Server needs to manage multiple incoming client requests on a single UDP port (stored in the DTLS Server instance).</span></span>

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_dtls_api.h"

#define     DEMO_STACK_SIZE         4096

/* Define the ThreadX and NetX object control blocks.
   NOTE: These must be initialized for the target platform. See the
   NetX documentation for details. */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the DTLS Server thread.  */
ULONG             dtls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         dtls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the DTLS packet reassembly buffer. */
UCHAR packet_buffer[4000];

/* Define the metadata area for TLS/DTLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR crypto_metadata_buffer[4000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library. The TLS structure is also
   used for DTLS. See the NetX Secure TLS User Guide for more information.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define our server certificate structure. */
NX_SECURE_X509_CERTIFICATE certificate;

/* DER-encoded certificate data for the server identity X.509 certificate. */
UCHAR device_cert_der[] = { … };
UCHAR device_cert_der_length[] = { … };
UCHAR device_cert_key_der[] = { … };
UCHAR device_cert_key_der_length[] = { … };

/* Define the number of sessions we want to allocate to our DTLS Server. */
#define DTLS_SERVER_SESSIONS (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION) * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive. NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Define the application – initialize drivers and UDP setup.  */
void    tx_application_define(void *first_unused_memory)
{
    UINT  status;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
   NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, …);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable UDP traffic. Check status for errors. */
    status =  nx_udp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS/DTLS system.  */
    nx_secure_tls_initialize();

     /* Create the server thread to start handling incoming requests. */
    tx_thread_create(&dtls_server_thread, "DTLS Server thread", server_thread_entry,
       0, dtls_server_thread_stack, sizeof(dtls_server_thread_stack),
       16, 16, 4, TX_AUTO_START);
}


/* Primary application thread for handling DTLS server operations. */
void server_thread_entry(ULONG thread_input)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UCHAR receive_buffer[100];
    ULONG bytes;
    UINT status;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
        NX_IP_PERIODIC_RATE);

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance, LOCAL_SERVER_PORT,
        NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
        sizeof(dtls_server_session_buffer),
        &tls_crypto_table, crypto_metadata_buffer,
        sizeof(crypto_metadata_buffer), packet_buffer,
        sizeof(packet_buffer),
        dtls_server_connect_notify,
        dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server, &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            status = nx_secure_dtls_session_receive(receive_dtls_session, &receive_packet,
            NX_IP_PERIODIC_RATE);


            /* Process received data… */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer, 100,
                 &bytes);
            /* Display the Client request data. */
           receive_buffer[bytes] = 0;
           printf("Received data: %s\n", receive_buffer);


            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);


           /* Populate the packet with our response data. */
           nx_packet_data_append(send_packet, response_data, response_data_length,
                &pool_0, NX_WAIT_FOREVER);

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}
```

<span data-ttu-id="b15df-136">**Rysunek 1,2 przykład NetX bezpiecznego DTLS serwera**</span><span class="sxs-lookup"><span data-stu-id="b15df-136">**Figure 1.2 Example of NetX Secure DTLS Server**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="b15df-137">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b15df-137">Configuration Options</span></span>

<span data-ttu-id="b15df-138">Istnieje kilka opcji konfiguracji do tworzenia bezpiecznych NetX.</span><span class="sxs-lookup"><span data-stu-id="b15df-138">There are several configuration options for building NetX Secure.</span></span>
<span data-ttu-id="b15df-139">Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:</span><span class="sxs-lookup"><span data-stu-id="b15df-139">Following is a list of all options, where each is described in detail:</span></span>

| <span data-ttu-id="b15df-140">Zdefiniować</span><span class="sxs-lookup"><span data-stu-id="b15df-140">Define</span></span>                                                 | <span data-ttu-id="b15df-141">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="b15df-141">Meaning</span></span>                                                                                                                                                                                                                |
|--------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b15df-142">**NX_SECURE_ENABLE_DTLS**</span><span class="sxs-lookup"><span data-stu-id="b15df-142">**NX_SECURE_ENABLE_DTLS**</span></span>                           | <span data-ttu-id="b15df-143">To makro musi być zdefiniowane w celu włączenia logiki DTLS w NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="b15df-143">This macro must be defined to enable DTLS logic in NetX Secure.</span></span>                                                                                                                                                       |
| <span data-ttu-id="b15df-144">**NX_SECURE_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="b15df-144">**NX_SECURE_DISABLE_ERROR_CHECKING**</span></span>               | <span data-ttu-id="b15df-145">Zdefiniowana, ta opcja usuwa podstawowe sprawdzanie bezpiecznego błędu NetX.</span><span class="sxs-lookup"><span data-stu-id="b15df-145">Defined, this option removes the basic NetX Secure error checking.</span></span> <span data-ttu-id="b15df-146">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b15df-146">It is typically used after the application has been debugged.</span></span>                                                                                     |
| <span data-ttu-id="b15df-147">**NX_SECURE_TLS_CLIENT_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="b15df-147">**NX_SECURE_TLS_CLIENT_DISABLED**</span></span>                  | <span data-ttu-id="b15df-148">Zdefiniowana, ta opcja usuwa wszystkie kody stosu TLS/DTLS związane z trybem klienta, skracając kod i użycie danych.</span><span class="sxs-lookup"><span data-stu-id="b15df-148">Defined, this option removes all TLS/DTLS stack code related to Client mode, reducing code and data usage.</span></span>                                                                                                            |
| <span data-ttu-id="b15df-149">**NX_SECURE_TLS_SERVER_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="b15df-149">**NX_SECURE_TLS_SERVER_DISABLED**</span></span>                  | <span data-ttu-id="b15df-150">Zdefiniowana, ta opcja usuwa wszystkie kody stosu TLS/DTLS związane z trybem serwera, skracając kod i użycie danych.</span><span class="sxs-lookup"><span data-stu-id="b15df-150">Defined, this option removes all TLS/DTLS stack code related to Server mode, reducing code and data usage.</span></span>                                                                                                            |
| <span data-ttu-id="b15df-151">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span><span class="sxs-lookup"><span data-stu-id="b15df-151">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span></span>              | <span data-ttu-id="b15df-152">Zdefiniowana, ta opcja włącza funkcję klucz wstępny (PSK).</span><span class="sxs-lookup"><span data-stu-id="b15df-152">Defined, this option enables Pre-Shared Key (PSK) functionality.</span></span> <span data-ttu-id="b15df-153">Nie powoduje wyłączenia certyfikatów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="b15df-153">It does not disable digital certificates.</span></span>                                                                                                        |
| <span data-ttu-id="b15df-154">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span><span class="sxs-lookup"><span data-stu-id="b15df-154">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span></span>            | <span data-ttu-id="b15df-155">Zdefiniowana, ta opcja umożliwia dokładne porównanie nazw wyróżniających certyfikatów X. 509 w celu przeszukiwania certyfikatów i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="b15df-155">Defined, this option enables strict distinguished name comparison for X.509 certificates for certificate searching and verification.</span></span> <span data-ttu-id="b15df-156">Wartość domyślna to porównanie tylko pól Nazwa pospolita.</span><span class="sxs-lookup"><span data-stu-id="b15df-156">The default is to only compare the Common Name fields the Distinguished Names.</span></span> |
| <span data-ttu-id="b15df-157">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span><span class="sxs-lookup"><span data-stu-id="b15df-157">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span></span>     | <span data-ttu-id="b15df-158">Zdefiniowana, ta opcja włącza opcjonalną nazwę wyróżniającą X. 509, przy kosztach użycia dodatkowej pamięci dla certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="b15df-158">Defined, this option enables the optional X.509 Distinguished Name fields, at the expense of extra memory use for X.509 certificates.</span></span>                                                                               |
| <span data-ttu-id="b15df-159">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span><span class="sxs-lookup"><span data-stu-id="b15df-159">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span></span>                | <span data-ttu-id="b15df-160">Zdefiniowane, ta opcja zapewnia maksymalny rozmiar modułu RSA oczekiwany w bitach.</span><span class="sxs-lookup"><span data-stu-id="b15df-160">Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="b15df-161">Wartość domyślna to 4096 dla \- modułu 4096 bitowego.</span><span class="sxs-lookup"><span data-stu-id="b15df-161">The default value is 4096 for a 4096\-bit modulus.</span></span> <span data-ttu-id="b15df-162">Inne wartości mogą być 3072, 2048 lub 1024 (niezalecane).</span><span class="sxs-lookup"><span data-stu-id="b15df-162">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>                               |