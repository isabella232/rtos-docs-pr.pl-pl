---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Secure
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem bezpiecznego składnika NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3ef82bd113518b35105fb2eefe23bd3e755ca06
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822855"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a><span data-ttu-id="82825-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Secure</span><span class="sxs-lookup"><span data-stu-id="82825-103">Chapter 2 - Installation and use of Azure RTOS NetX Secure</span></span>

<span data-ttu-id="82825-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika bezpiecznego usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="82825-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Secure component.</span></span>

## <a name="product-version-number"></a><span data-ttu-id="82825-105">Numer wersji produktu</span><span class="sxs-lookup"><span data-stu-id="82825-105">Product Version Number</span></span>

<span data-ttu-id="82825-106">Użytkownik może zweryfikować numer wersji produktu, wyszukując następujące symbole w nx_secure_tls. h:</span><span class="sxs-lookup"><span data-stu-id="82825-106">User may verify the product version number by finding the following symbols in nx_secure_tls.h:</span></span>

<span data-ttu-id="82825-107">***NETX_SECURE_MAJOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="82825-107">***NETX_SECURE_MAJOR_VERSION***</span></span>

<span data-ttu-id="82825-108">***NETX_SECURE_MINOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="82825-108">***NETX_SECURE_MINOR_VERSION***</span></span>

<span data-ttu-id="82825-109">Wersje dodatku Service Pack mają następujący symbol zdefiniowany w celu wskazania numeru dodatku Service Pack:</span><span class="sxs-lookup"><span data-stu-id="82825-109">Service Pack releases has the following symbol defined to indicate the service pack number:</span></span>

<span data-ttu-id="82825-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span><span class="sxs-lookup"><span data-stu-id="82825-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span></span>

## <a name="product-distribution"></a><span data-ttu-id="82825-111">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="82825-111">Product Distribution</span></span>

<span data-ttu-id="82825-112">Zabezpieczenia NetX są dostępne pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="82825-112">NetX Secure is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="82825-113">Pakiet zawiera pliki źródłowe, pliki dołączane oraz plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="82825-113">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="82825-114">**nx_secure_tls_api. h** Publiczny plik nagłówkowy interfejsu API dla usługi NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="82825-114">**nx_secure_tls_api.h** Public API header file for NetX Secure TLS</span></span>
- <span data-ttu-id="82825-115">**nx_secure_tls_user. h** Użytkownik definiuje plik nagłówka dla NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="82825-115">**nx_secure_tls_user.h** User defines header file for NetX Secure TLS</span></span>
- <span data-ttu-id="82825-116">**nx_secure_tls_port. h** Definicje specyficzne dla platformy dla NetX Secure</span><span class="sxs-lookup"><span data-stu-id="82825-116">**nx_secure_tls_port.h** Platform-specific definitions for NetX Secure</span></span>
- <span data-ttu-id="82825-117">**nx_secure_tls. h** Plik nagłówka dla protokołu Secure TLS NetX</span><span class="sxs-lookup"><span data-stu-id="82825-117">**nx_secure_tls.h** Header file for NetX Secure TLS</span></span>
- <span data-ttu-id="82825-118">**nx_secure_tls&#42;. c/h** Pliki źródłowe C/H dla NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="82825-118">**nx_secure_tls&#42;.c/h** C/H Source files for NetX Secure TLS</span></span>
- <span data-ttu-id="82825-119">**nx_crypto&#42;. c/h** Pliki źródłowe C/H dla bezpiecznego kryptografii NetX</span><span class="sxs-lookup"><span data-stu-id="82825-119">**nx_crypto&#42;.c/h** C/H Source files for NetX Secure Cryptography</span></span>
- <span data-ttu-id="82825-120">**nx_secure_x509&#42;. c/h** Pliki źródłowe C/H dla certyfikatów cyfrowych X. 509.</span><span class="sxs-lookup"><span data-stu-id="82825-120">**nx_secure_x509&#42;.c/h** C/H Source files for X.509 digital certificates.</span></span>
- <span data-ttu-id="82825-121">**demo_netx_secure_tls. c** Plik źródłowy języka C dla demonstracji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="82825-121">**demo_netx_secure_tls.c** C Source file for NetX Secure TLS Demo</span></span>
- <span data-ttu-id="82825-122">**NetX_Secure_User_Guide.pdf** Opis pliku PDF NetX bezpiecznego produktu</span><span class="sxs-lookup"><span data-stu-id="82825-122">**NetX_Secure_User_Guide.pdf** PDF description of NetX Secure product</span></span>

> [!NOTE]
> <span data-ttu-id="82825-123">Pliki nx_crypto \* są dostępne dla różnych platform sprzętowych w podkatalogu bezpiecznego katalogu nadrzędnego NetX.</span><span class="sxs-lookup"><span data-stu-id="82825-123">The nx_crypto\* files are provided for different hardware platforms in a subdirectory of the NetX Secure parent directory.</span></span>

## <a name="netx-secure-installation"></a><span data-ttu-id="82825-124">Bezpieczna instalacja NetX</span><span class="sxs-lookup"><span data-stu-id="82825-124">NetX Secure Installation</span></span>

<span data-ttu-id="82825-125">Aby można było używać usługi NetX Secure, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego poziomu katalogu, gdzie zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="82825-125">In order to use NetX Secure, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="82825-126">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\NetX*", wówczas \*nx_secure \* *.*</span><span class="sxs-lookup"><span data-stu-id="82825-126">For example, if NetX is installed in the directory "*\threadx\arm7\NetX*" then the *nx_secure\*\*.*</span></span> <span data-ttu-id="82825-127">katalogi powinny być kopiowane do "*\threadx\arm7\NetXSecure*".</span><span class="sxs-lookup"><span data-stu-id="82825-127">directories should be copied into "*\threadx\arm7\NetXSecure*".</span></span>

## <a name="using-netx-secure"></a><span data-ttu-id="82825-128">Korzystanie z usługi NetX Secure</span><span class="sxs-lookup"><span data-stu-id="82825-128">Using NetX Secure</span></span>

<span data-ttu-id="82825-129">Używanie protokołu Secure TLS NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="82825-129">Using NetX Secure TLS is straightforward.</span></span> <span data-ttu-id="82825-130">W zasadzie kod aplikacji musi zawierać *nx_secure_tls_api. h* po zawiera *tx_api. h* i *nx_api. h*, aby można było użyć ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="82825-130">Basically, the application code must include *nx_secure_tls_api.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="82825-131">Po dołączeniu *nx_secure_tls_api. h* kod aplikacji jest następnie w stanie zapewnić, że wywołania funkcji bezpiecznego NetX określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="82825-131">Once *nx_secure_tls_api.h* is included, the application code is then able to make the NetX Secure function calls specified later in this guide.</span></span> <span data-ttu-id="82825-132">Aplikacja musi również zaimportować \*nx_secure \* *.*</span><span class="sxs-lookup"><span data-stu-id="82825-132">The application must also import the *nx_secure\*\*.*</span></span> <span data-ttu-id="82825-133">pliki do biblioteki NetXSecure i specyficzne dla platformy \*nx_crypto \* *.*</span><span class="sxs-lookup"><span data-stu-id="82825-133">files into a NetXSecure library, and the platform-specific *nx_crypto\*\*.*</span></span> <span data-ttu-id="82825-134">pliki do biblioteki NetXCrypto.</span><span class="sxs-lookup"><span data-stu-id="82825-134">files into a NetXCrypto library.</span></span>

## <a name="small-example-system-tls-client"></a><span data-ttu-id="82825-135">Mały przykładowy system (klient TLS)</span><span class="sxs-lookup"><span data-stu-id="82825-135">Small Example System (TLS Client)</span></span>

<span data-ttu-id="82825-136">Przykładem łatwego używania NetX Secure jest opisany na rysunku 1,1, który jest widoczny poniżej.</span><span class="sxs-lookup"><span data-stu-id="82825-136">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="82825-137">To pokazuje prostego klienta protokołu TLS przy użyciu modułów kryptograficznych oprogramowania (nie specyficznych dla sprzętu) do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="82825-137">This demonstrates a simple TLS Client, using software crypto modules (not hardware specific) for encryption.</span></span> <span data-ttu-id="82825-138">Została zaprojektowana do pracy z serwerem OpenSSL reecha-Echo (OpenSSL s_server-rev).</span><span class="sxs-lookup"><span data-stu-id="82825-138">It is designed to work with the OpenSSL reverse-echo server (openssl s_server -rev).</span></span>

<span data-ttu-id="82825-139">Należy pamiętać, że w celu uruchomienia tego przykładu do uwierzytelnienia certyfikatu serwera docelowego potrzebny jest certyfikat certyfikatu X. 509 urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="82825-139">Note that in order to run this example, you will need an X.509 CA certificate to authenticate your target server's certificate.</span></span> <span data-ttu-id="82825-140">W przypadku przykładu OpenSSL wystarcza prosta infrastruktura PKI 2-pozioma (certyfikat głównego urzędu certyfikacji-> >serwera).</span><span class="sxs-lookup"><span data-stu-id="82825-140">For the OpenSSL example, a simple 2-level PKI (root CA certificate-> >server certificate) will suffice.</span></span> <span data-ttu-id="82825-141">Musisz wypełnić tablicę "trusted_ca_data" przy użyciu binarnej wersji algorytmów DER certyfikatu urzędu certyfikacji i zaktualizować zmienną "trusted_ca_length", aby odzwierciedlić rzeczywistą długość certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="82825-141">You will need to fill in the "trusted_ca_data" array with a DER-encoded binary version of your CA certificate and update the "trusted_ca_length" variable to reflect your certificate's actual length.</span></span>

<span data-ttu-id="82825-142">Wymagany jest również sterownik sieciowy sprzętu (Zastąp parametr "nx_driver_xx" w wywołaniu nx_ip_create).</span><span class="sxs-lookup"><span data-stu-id="82825-142">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
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

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

<span data-ttu-id="82825-143">**Rysunek 1,1 przykład bezpiecznego użycia NetX z NetX**</span><span class="sxs-lookup"><span data-stu-id="82825-143">**Figure 1.1 Example of NetX Secure use with NetX**</span></span>

## <a name="small-example-system-tls-web-server"></a><span data-ttu-id="82825-144">Mały przykładowy system (serwer sieci Web TLS)</span><span class="sxs-lookup"><span data-stu-id="82825-144">Small Example System (TLS Web Server)</span></span>

<span data-ttu-id="82825-145">Przykładem łatwego używania NetX Secure jest opisany na rysunku 1,1, który pojawia się poniżej i pokazuje prosty serwer sieci Web TLS (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="82825-145">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below and demonstrates a simple TLS Web Server (HTTPS).</span></span>

<span data-ttu-id="82825-146">Należy pamiętać, że w celu uruchomienia tego przykładu należy uzyskać certyfikat X. 509 w celu zidentyfikowania serwera na klientach TLS.</span><span class="sxs-lookup"><span data-stu-id="82825-146">Note that in order to run this example, you will need an X.509 certificate to identify your server to TLS clients.</span></span> <span data-ttu-id="82825-147">W przypadku większości Browers sieci Web należy uzyskać prosty certyfikat z podpisem własnym.</span><span class="sxs-lookup"><span data-stu-id="82825-147">For most web browers a simple self-signed certificate should be sufficient.</span></span> <span data-ttu-id="82825-148">Twoja przeglądarka nie będzie mogła uwierzytelnić serwera, a w niektórych przypadkach może nie być w stanie nawiązać połączenia TLS/HTTPS z serwerem<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="82825-148">Your browser will complain about not being able to authenticate the server and in some cases may be unable to establish a TLS/HTTPS connection to your server<sup>3</sup>.</span></span> <span data-ttu-id="82825-149">Musisz wypełnić tablicę "certificate_data" przy użyciu binarnej wersji algorytmów DER certyfikatu serwera i zaktualizować zmienną "certificate_length", aby odzwierciedlić rzeczywistą długość certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="82825-149">You will need to fill in the "certificate_data" array with a DER-encoded binary version of your server certificate and update the "certificate_length" variable to reflect your certificate's actual length.</span></span> <span data-ttu-id="82825-150">Należy również wypełnić tablicę "private_key" z użyciem zakodowanej algorytmem DER wersji klucza prywatnego certyfikatu w formacie PKCS # 1 dla klucza RSA i RFC 5915 dla kluczy ECC.</span><span class="sxs-lookup"><span data-stu-id="82825-150">You also need to fill in the "private_key" array with a DER-encoded version of your certificate's private key, formatted using PKCS#1 for RSA key and RFC 5915 for ECC keys.</span></span> <span data-ttu-id="82825-151">Wypełnij zmienną "private_key_length" rzeczywistą długością danych klucza.</span><span class="sxs-lookup"><span data-stu-id="82825-151">Fill in the "private_key_length" variable with the actual length of your key data.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82825-152">Niektóre przeglądarki (szczególnie niektóre wersje przeglądarki Chrome) mogą odrzucać certyfikaty z podpisem własnym.</span><span class="sxs-lookup"><span data-stu-id="82825-152">Some browsers (particularly some versions of the Chrome browser) may reject self-signed certificates.</span></span> <span data-ttu-id="82825-153">W takim przypadku można utworzyć 2-poziomową infrastrukturę PKI z certyfikatem głównego urzędu certyfikacji, który jest używany do podpisywania certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="82825-153">In this case you can create a 2-level PKI with a root CA certificate that is used to sign your server certificate.</span></span> <span data-ttu-id="82825-154">W takiej sytuacji certyfikat głównego urzędu certyfikacji jest instalowany jako zaufany certyfikat główny w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="82825-154">In this situation, the root CA certificate is installed as a trusted root certificate in your browser.</span></span> <span data-ttu-id="82825-155">!!!</span><span class="sxs-lookup"><span data-stu-id="82825-155">!!!</span></span> <span data-ttu-id="82825-156">Ważne — Usuń certyfikat głównego urzędu certyfikacji z przeglądarki po zakończeniu i nie używaj go do żadnych aplikacji produkcyjnych!!!</span><span class="sxs-lookup"><span data-stu-id="82825-156">IMPORTANT – remove your root CA certificate from your browser when done and do not use it for any production applications !!!</span></span>

<span data-ttu-id="82825-157">Wymagany jest również sterownik sieciowy sprzętu (Zastąp parametr "nx_driver_xx" w wywołaniu nx_ip_create).</span><span class="sxs-lookup"><span data-stu-id="82825-157">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
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
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

<span data-ttu-id="82825-158">**Rysunek 1,2 przykład bezpiecznego użycia NetX z NetX**</span><span class="sxs-lookup"><span data-stu-id="82825-158">**Figure 1.2 Example of NetX Secure use with NetX**</span></span>

## <a name="a-note-on-tls-session-error-recovery"></a><span data-ttu-id="82825-159">Uwaga dotycząca odzyskiwania błędów sesji TLS</span><span class="sxs-lookup"><span data-stu-id="82825-159">A Note on TLS Session Error Recovery</span></span>

<span data-ttu-id="82825-160">W przykładowych systemach opisanych powyżej przedstawiono podstawowe podstawy dla klienta i serwera TLS, ale dla jasności pominięto obsługę błędów.</span><span class="sxs-lookup"><span data-stu-id="82825-160">The example systems described above show the basic outlines for a TLS Client and Server, respectively, but for clarity the error handling is omitted.</span></span> <span data-ttu-id="82825-161">Jednak część zabezpieczeń protokołu TLS jest zależna od właściwej obsługi warunków błędu.</span><span class="sxs-lookup"><span data-stu-id="82825-161">However, part of the security TLS provides is dependent on the proper handling of error conditions.</span></span> <span data-ttu-id="82825-162">Ogólnie rzecz biorąc, najważniejsze potencjalne problemy będą obsługiwane w ramach stosu TLS, ale ważne jest, aby aplikacja TLS mogła prawidłowo reagować na i odzyskiwać dane z błędów TLS, które nie są obsługiwane w ramach implementacji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="82825-162">Generally, the most serious potential problems will be handled within the TLS stack itself, but it is important for the TLS application to properly respond to and recover from TLS errors that are not handled within the TLS implementation.</span></span>

<span data-ttu-id="82825-163">Aby zilustrować niezbędną logikę w celu zapewnienia prawidłowej obsługi błędów, Poniższa funkcja pokazuje typową kolekcję usług interfejsu API, która może być używana do prawidłowego obsługi błędów TLS i czysty resetowanie stanu TLS po napotkaniu warunku błędu.</span><span class="sxs-lookup"><span data-stu-id="82825-163">In order to illustrate the necessary logic for proper error handling, the following function demonstrates a typical collection of API services that can be used to properly handle TLS errors and cleanly reset the TLS state after an error condition is encountered.</span></span> <span data-ttu-id="82825-164">Inaczej niż w przypadku, gdy zanotowano, logika dotyczy zarówno wystąpienia klienta TLS, jak i serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="82825-164">Other than the section where noted, the logic applies to both TLS Client and TLS Server instances.</span></span>

<span data-ttu-id="82825-165">Należy zauważyć, że najważniejszymi wywołaniami interfejsu API w funkcji są *nx_secure_tls_session_end*, które w sposób czysty zamykają sesję lub UZGADNIANIE protokołu TLS, a *nx_secure_tls_session_reset*, co czyści stan sesji TLS, dzięki czemu można ponownie użyć wystąpienia tls_session struktury kontroli dla nowej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="82825-165">Note that the most important API calls in the function are to the services *nx_secure_tls_session_end*, which cleanly closes the TLS session or handshake, and *nx_secure_tls_session_reset*, which clears the TLS session state so the tls_session control structure instance can be reused for a new TLS session.</span></span> <span data-ttu-id="82825-166">Należy również zauważyć, że *nx_secure_tls_session_reset* nie czyści stanu skonfigurowanego przez użytkownika, takiego jak certyfikaty lub przypisane bufory, umożliwiając ponowne użycie sesji bez wywoływania *nx_secure_tls_session_create* .</span><span class="sxs-lookup"><span data-stu-id="82825-166">Also note that *nx_secure_tls_session_reset* does not clear the user-configured state such as certificates or assigned buffers, allowing the session to be reused without calling *nx_secure_tls_session_create* again.</span></span> <span data-ttu-id="82825-167">Aby całkowicie wyczyścić wszystkie Stany sesji TLS, można użyć *nx_secure_tls_session_delete* usługi.</span><span class="sxs-lookup"><span data-stu-id="82825-167">To completely clear all TLS session state, the service *nx_secure_tls_session_delete* may be used instead.</span></span>

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a><span data-ttu-id="82825-168">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82825-168">Configuration Options</span></span>

<span data-ttu-id="82825-169">Istnieje kilka opcji konfiguracji do tworzenia bezpiecznych NetX.</span><span class="sxs-lookup"><span data-stu-id="82825-169">There are several configuration options for building NetX Secure.</span></span> <span data-ttu-id="82825-170">Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:</span><span class="sxs-lookup"><span data-stu-id="82825-170">Following is a list of all options, where each is described in detail:</span></span>

| <span data-ttu-id="82825-171">Zdefiniować</span><span class="sxs-lookup"><span data-stu-id="82825-171">Define</span></span> | <span data-ttu-id="82825-172">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="82825-172">Meaning</span></span> |
|----------------------|------------------------------------------------|
| <span data-ttu-id="82825-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="82825-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span></span>                | <span data-ttu-id="82825-174">Zdefiniowana, ta opcja usuwa podstawowe sprawdzanie bezpiecznego błędu NetX.</span><span class="sxs-lookup"><span data-stu-id="82825-174">Defined, this option removes the basic NetX Secure error checking.</span></span> <span data-ttu-id="82825-175">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82825-175">It is typically used after the application has been debugged.</span></span> |
| <span data-ttu-id="82825-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span><span class="sxs-lookup"><span data-stu-id="82825-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span></span>                  | <span data-ttu-id="82825-177">Zdefiniowane, ta opcja zapewnia maksymalny rozmiar modułu RSA oczekiwany w bitach.</span><span class="sxs-lookup"><span data-stu-id="82825-177">Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="82825-178">Wartość domyślna to 4096 dla modułu 4096-bitowego.</span><span class="sxs-lookup"><span data-stu-id="82825-178">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="82825-179">Inne wartości mogą być 3072, 2048 lub 1024 (niezalecane).</span><span class="sxs-lookup"><span data-stu-id="82825-179">Other values can be 3072, 2048, or 1024 (not recommended).</span></span> |
| <span data-ttu-id="82825-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span><span class="sxs-lookup"><span data-stu-id="82825-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span></span>        | <span data-ttu-id="82825-181">Zdefiniowana, ta opcja umożliwia protokołowi TLS akceptowanie certyfikatów z podpisem własnym z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="82825-181">Defined, this option allows TLS to accept self-signed certificates from a remote host.</span></span> <span data-ttu-id="82825-182">Domyślnie protokół TLS odrzuci certyfikaty serwera z podpisem własnym jako środek zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="82825-182">By default, TLS will reject self-signed server certificates as a security precaution.</span></span> <span data-ttu-id="82825-183">Jeśli to makro jest zdefiniowane, certyfikaty z podpisem własnym muszą być nadal dodawane do zaufanego magazynu, aby zostały zaakceptowane.</span><span class="sxs-lookup"><span data-stu-id="82825-183">If this macro is defined, self-signed certificates must still be added to the trusted store to be accepted.</span></span> |
| <span data-ttu-id="82825-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span><span class="sxs-lookup"><span data-stu-id="82825-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span></span>      | <span data-ttu-id="82825-185">Zdefiniowana, ta opcja włącza opcjonalną weryfikację certyfikatu klienta X. 509 dla serwerów TLS<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="82825-185">Defined, this option enables the optional X.509 Client Certificate Verification for TLS Servers<sup>4</sup>.</span></span>  |
| <span data-ttu-id="82825-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span><span class="sxs-lookup"><span data-stu-id="82825-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span></span>               | <span data-ttu-id="82825-187">Zdefiniowana, ta opcja włącza funkcję klucz wstępny (PSK).</span><span class="sxs-lookup"><span data-stu-id="82825-187">Defined, this option enables Pre-Shared Key (PSK) functionality.</span></span> <span data-ttu-id="82825-188">Nie powoduje wyłączenia certyfikatów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="82825-188">It does not disable digital certificates.</span></span> |
| <span data-ttu-id="82825-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="82825-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span></span>                   | <span data-ttu-id="82825-190">Zdefiniowana, ta opcja usuwa cały kod stosu TLS związany z trybem klienta protokołu TLS, skracając kod i użycie danych.</span><span class="sxs-lookup"><span data-stu-id="82825-190">Defined, this option removes all TLS stack code related to TLS Client mode, reducing code and data usage.</span></span> |
| <span data-ttu-id="82825-191">**NX_SECURE_TLS_SERVER_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="82825-191">**NX_SECURE_TLS_SERVER_DISABLED**</span></span>                   | <span data-ttu-id="82825-192">Zdefiniowana, ta opcja usuwa cały kod stosu TLS związany z trybem serwera TLS, skracając kod i użycie danych.</span><span class="sxs-lookup"><span data-stu-id="82825-192">Defined, this option removes all TLS stack code related to TLS Server mode, reducing code and data usage.</span></span>  |
| <span data-ttu-id="82825-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span><span class="sxs-lookup"><span data-stu-id="82825-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span></span>               | <span data-ttu-id="82825-194">Zdefiniowana, ta opcja powoduje usunięcie wszystkich logiki TLS dla ciphersuitesowych kryptografii krzywej eliptycznej (ECC).</span><span class="sxs-lookup"><span data-stu-id="82825-194">Defined, this option removes all TLS logic for Elliptic Curve Cryptography (ECC) ciphersuites.</span></span> <span data-ttu-id="82825-195">Te ciphersuites są opcjonalne w protokole TLS 1,2 i wcześniej, a ich wyłączenie może spowodować zmniejszenie znaczących kodów i rozmiarów danych.</span><span class="sxs-lookup"><span data-stu-id="82825-195">These ciphersuites are optional in TLS 1.2 and earlier and disabling them can result in significant code and data size reduction.</span></span>|
| <span data-ttu-id="82825-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span><span class="sxs-lookup"><span data-stu-id="82825-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span></span>                    | <span data-ttu-id="82825-197">Zdefiniowana, ta opcja włącza tryb TLSv 1.3.</span><span class="sxs-lookup"><span data-stu-id="82825-197">Defined, this option enables TLSv1.3 mode.</span></span> <span data-ttu-id="82825-198">TLS 1,3 to Najnowsza wersja protokołu TLS i jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="82825-198">TLS 1.3 is the newest version of TLS and is disabled by default.</span></span> |
| <span data-ttu-id="82825-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span><span class="sxs-lookup"><span data-stu-id="82825-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span></span>                    | <span data-ttu-id="82825-200">Zdefiniowana, ta opcja włącza tryb starszej wersji TLSv 1.0.</span><span class="sxs-lookup"><span data-stu-id="82825-200">Defined, this option enables the legacy TLSv1.0 mode.</span></span> <span data-ttu-id="82825-201">TLSv 1.0 jest uznawany za przestarzały, więc należy ją włączyć tylko w celu zapewnienia zgodności ze starszymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="82825-201">TLSv1.0 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="82825-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="82825-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span></span>                    | <span data-ttu-id="82825-203">Zdefiniowana, ta opcja włącza tryb starszej wersji 1.1 TLSv.</span><span class="sxs-lookup"><span data-stu-id="82825-203">Defined, this option enables the legacy TLSv1.1 mode.</span></span> <span data-ttu-id="82825-204">TLSv 1.1 jest uznawany za przestarzały, więc należy ją włączyć tylko w celu zapewnienia zgodności ze starszymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="82825-204">TLSv1.1 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="82825-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="82825-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span></span>                   | <span data-ttu-id="82825-206">Zdefiniowana, ta opcja powoduje wyłączenie trybu TLSv 1.1.</span><span class="sxs-lookup"><span data-stu-id="82825-206">Defined, this option disables TLSv1.1 mode.</span></span> <span data-ttu-id="82825-207">Jest on definiowany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="82825-207">It is defined by default.</span></span> <span data-ttu-id="82825-208">TLSv 1.1 jest wyłączone na korzyść korzystania tylko z bezpieczniejszej TLSv 1.2<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="82825-208">TLSv1.1 is disabled in favor of using only the more-secure TLSv1.2<sup>5</sup>.</span></span>  |
| <span data-ttu-id="82825-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span><span class="sxs-lookup"><span data-stu-id="82825-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span></span>              | <span data-ttu-id="82825-210">Zdefiniowana, ta opcja umożliwia dokładne porównanie nazw wyróżniających certyfikatów X. 509 w celu przeszukiwania certyfikatów i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="82825-210">Defined, this option enables strict distinguished name comparison for X.509 certificates for certificate searching and verification.</span></span> <span data-ttu-id="82825-211">Domyślnie porównywane są pola nazw wspólnych nazw wyróżniających.</span><span class="sxs-lookup"><span data-stu-id="82825-211">The default is to only compare the Common Name fields of the Distinguished Names.</span></span>|
| <span data-ttu-id="82825-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span><span class="sxs-lookup"><span data-stu-id="82825-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span></span> | <span data-ttu-id="82825-213">Zdefiniowana, ta opcja włącza opcjonalną nazwę wyróżniającą X. 509, przy kosztach użycia dodatkowej pamięci dla certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="82825-213">Defined, this option enables the optional X.509 Distinguished Name fields, at the expense of extra memory use for X.509 certificates.</span></span> |

4. <span data-ttu-id="82825-214">Należy zauważyć, że ta opcja umożliwia tylko łączenie kodu z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="82825-214">Note that this option only enables the code to be linked into the application.</span></span> <span data-ttu-id="82825-215">Aby można było użyć weryfikacji certyfikatu klienta, należy włączyć tę funkcję za pomocą usługi interfejsu API nx_secure_tls_session_client_verify_enable lub skonfigurowania jej przy użyciu nx_secure_tls_session_x509_client_verify_configure.</span><span class="sxs-lookup"><span data-stu-id="82825-215">The feature will need to be enabled with the API service nx_secure_tls_session_client_verify_enable or configured using nx_secure_tls_session_x509_client_verify_configure in order to use Client Certificate Verification.</span></span>

5. <span data-ttu-id="82825-216">Należy pamiętać, że można również wyłączyć TLSv 1.2, jeśli używany jest tylko protokół TLS 1,0 lub TLS 1,1.</span><span class="sxs-lookup"><span data-stu-id="82825-216">Note that it is also possible to disable TLSv1.2 if using TLS 1.0 or TLS 1.1 only.</span></span> <span data-ttu-id="82825-217">Nie jest to jednak zalecane i nie jest bezpośrednio obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="82825-217">However, this is not recommended and not directly supported.</span></span>
