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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Secure

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika bezpiecznego usługi Azure RTO NetX.

## <a name="product-version-number"></a>Numer wersji produktu

Użytkownik może zweryfikować numer wersji produktu, wyszukując następujące symbole w nx_secure_tls. h:

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

Wersje dodatku Service Pack mają następujący symbol zdefiniowany w celu wskazania numeru dodatku Service Pack:

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>Dystrybucja produktu

Zabezpieczenia NetX są dostępne pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera pliki źródłowe, pliki dołączane oraz plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_secure_tls_api. h** Publiczny plik nagłówkowy interfejsu API dla usługi NetX Secure TLS
- **nx_secure_tls_user. h** Użytkownik definiuje plik nagłówka dla NetX Secure TLS
- **nx_secure_tls_port. h** Definicje specyficzne dla platformy dla NetX Secure
- **nx_secure_tls. h** Plik nagłówka dla protokołu Secure TLS NetX
- **nx_secure_tls&#42;. c/h** Pliki źródłowe C/H dla NetX Secure TLS
- **nx_crypto&#42;. c/h** Pliki źródłowe C/H dla bezpiecznego kryptografii NetX
- **nx_secure_x509&#42;. c/h** Pliki źródłowe C/H dla certyfikatów cyfrowych X. 509.
- **demo_netx_secure_tls. c** Plik źródłowy języka C dla demonstracji bezpiecznego protokołu TLS NetX
- **NetX_Secure_User_Guide.pdf** Opis pliku PDF NetX bezpiecznego produktu

> [!NOTE]
> Pliki nx_crypto * są dostępne dla różnych platform sprzętowych w podkatalogu bezpiecznego katalogu nadrzędnego NetX.

## <a name="netx-secure-installation"></a>Bezpieczna instalacja NetX

Aby można było używać usługi NetX Secure, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego poziomu katalogu, gdzie zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\NetX*", wówczas *nx_secure * *.* katalogi powinny być kopiowane do "*\threadx\arm7\NetXSecure*".

## <a name="using-netx-secure"></a>Korzystanie z usługi NetX Secure

Używanie protokołu Secure TLS NetX jest proste. W zasadzie kod aplikacji musi zawierać *nx_secure_tls_api. h* po zawiera *tx_api. h* i *nx_api. h*, aby można było użyć ThreadX i NetX. Po dołączeniu *nx_secure_tls_api. h* kod aplikacji jest następnie w stanie zapewnić, że wywołania funkcji bezpiecznego NetX określone w dalszej części tego przewodnika. Aplikacja musi również zaimportować *nx_secure * *.* pliki do biblioteki NetXSecure i specyficzne dla platformy *nx_crypto * *.* pliki do biblioteki NetXCrypto.

## <a name="small-example-system-tls-client"></a>Mały przykładowy system (klient TLS)

Przykładem łatwego używania NetX Secure jest opisany na rysunku 1,1, który jest widoczny poniżej. To pokazuje prostego klienta protokołu TLS przy użyciu modułów kryptograficznych oprogramowania (nie specyficznych dla sprzętu) do szyfrowania. Została zaprojektowana do pracy z serwerem OpenSSL reecha-Echo (OpenSSL s_server-rev).

Należy pamiętać, że w celu uruchomienia tego przykładu do uwierzytelnienia certyfikatu serwera docelowego potrzebny jest certyfikat certyfikatu X. 509 urzędu certyfikacji. W przypadku przykładu OpenSSL wystarcza prosta infrastruktura PKI 2-pozioma (certyfikat głównego urzędu certyfikacji-> >serwera). Musisz wypełnić tablicę "trusted_ca_data" przy użyciu binarnej wersji algorytmów DER certyfikatu urzędu certyfikacji i zaktualizować zmienną "trusted_ca_length", aby odzwierciedlić rzeczywistą długość certyfikatu.

Wymagany jest również sterownik sieciowy sprzętu (Zastąp parametr "nx_driver_xx" w wywołaniu nx_ip_create).

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

**Rysunek 1,1 przykład bezpiecznego użycia NetX z NetX**

## <a name="small-example-system-tls-web-server"></a>Mały przykładowy system (serwer sieci Web TLS)

Przykładem łatwego używania NetX Secure jest opisany na rysunku 1,1, który pojawia się poniżej i pokazuje prosty serwer sieci Web TLS (HTTPS).

Należy pamiętać, że w celu uruchomienia tego przykładu należy uzyskać certyfikat X. 509 w celu zidentyfikowania serwera na klientach TLS. W przypadku większości Browers sieci Web należy uzyskać prosty certyfikat z podpisem własnym. Twoja przeglądarka nie będzie mogła uwierzytelnić serwera, a w niektórych przypadkach może nie być w stanie nawiązać połączenia TLS/HTTPS z serwerem<sup>3</sup>. Musisz wypełnić tablicę "certificate_data" przy użyciu binarnej wersji algorytmów DER certyfikatu serwera i zaktualizować zmienną "certificate_length", aby odzwierciedlić rzeczywistą długość certyfikatu. Należy również wypełnić tablicę "private_key" z użyciem zakodowanej algorytmem DER wersji klucza prywatnego certyfikatu w formacie PKCS # 1 dla klucza RSA i RFC 5915 dla kluczy ECC. Wypełnij zmienną "private_key_length" rzeczywistą długością danych klucza.

> [!IMPORTANT]
> Niektóre przeglądarki (szczególnie niektóre wersje przeglądarki Chrome) mogą odrzucać certyfikaty z podpisem własnym. W takim przypadku można utworzyć 2-poziomową infrastrukturę PKI z certyfikatem głównego urzędu certyfikacji, który jest używany do podpisywania certyfikatu serwera. W takiej sytuacji certyfikat głównego urzędu certyfikacji jest instalowany jako zaufany certyfikat główny w przeglądarce. !!! Ważne — Usuń certyfikat głównego urzędu certyfikacji z przeglądarki po zakończeniu i nie używaj go do żadnych aplikacji produkcyjnych!!!

Wymagany jest również sterownik sieciowy sprzętu (Zastąp parametr "nx_driver_xx" w wywołaniu nx_ip_create).

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

**Rysunek 1,2 przykład bezpiecznego użycia NetX z NetX**

## <a name="a-note-on-tls-session-error-recovery"></a>Uwaga dotycząca odzyskiwania błędów sesji TLS

W przykładowych systemach opisanych powyżej przedstawiono podstawowe podstawy dla klienta i serwera TLS, ale dla jasności pominięto obsługę błędów. Jednak część zabezpieczeń protokołu TLS jest zależna od właściwej obsługi warunków błędu. Ogólnie rzecz biorąc, najważniejsze potencjalne problemy będą obsługiwane w ramach stosu TLS, ale ważne jest, aby aplikacja TLS mogła prawidłowo reagować na i odzyskiwać dane z błędów TLS, które nie są obsługiwane w ramach implementacji protokołu TLS.

Aby zilustrować niezbędną logikę w celu zapewnienia prawidłowej obsługi błędów, Poniższa funkcja pokazuje typową kolekcję usług interfejsu API, która może być używana do prawidłowego obsługi błędów TLS i czysty resetowanie stanu TLS po napotkaniu warunku błędu. Inaczej niż w przypadku, gdy zanotowano, logika dotyczy zarówno wystąpienia klienta TLS, jak i serwera TLS.

Należy zauważyć, że najważniejszymi wywołaniami interfejsu API w funkcji są *nx_secure_tls_session_end*, które w sposób czysty zamykają sesję lub UZGADNIANIE protokołu TLS, a *nx_secure_tls_session_reset*, co czyści stan sesji TLS, dzięki czemu można ponownie użyć wystąpienia tls_session struktury kontroli dla nowej sesji TLS. Należy również zauważyć, że *nx_secure_tls_session_reset* nie czyści stanu skonfigurowanego przez użytkownika, takiego jak certyfikaty lub przypisane bufory, umożliwiając ponowne użycie sesji bez wywoływania *nx_secure_tls_session_create* . Aby całkowicie wyczyścić wszystkie Stany sesji TLS, można użyć *nx_secure_tls_session_delete* usługi.

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

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia bezpiecznych NetX. Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:

| Zdefiniować | Znaczenie |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | Zdefiniowana, ta opcja usuwa podstawowe sprawdzanie bezpiecznego błędu NetX. Jest on zazwyczaj używany po debugowaniu aplikacji. |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | Zdefiniowane, ta opcja zapewnia maksymalny rozmiar modułu RSA oczekiwany w bitach. Wartość domyślna to 4096 dla modułu 4096-bitowego. Inne wartości mogą być 3072, 2048 lub 1024 (niezalecane). |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | Zdefiniowana, ta opcja umożliwia protokołowi TLS akceptowanie certyfikatów z podpisem własnym z hosta zdalnego. Domyślnie protokół TLS odrzuci certyfikaty serwera z podpisem własnym jako środek zabezpieczeń. Jeśli to makro jest zdefiniowane, certyfikaty z podpisem własnym muszą być nadal dodawane do zaufanego magazynu, aby zostały zaakceptowane. |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | Zdefiniowana, ta opcja włącza opcjonalną weryfikację certyfikatu klienta X. 509 dla serwerów TLS<sup>4</sup>.  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | Zdefiniowana, ta opcja włącza funkcję klucz wstępny (PSK). Nie powoduje wyłączenia certyfikatów cyfrowych. |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | Zdefiniowana, ta opcja usuwa cały kod stosu TLS związany z trybem klienta protokołu TLS, skracając kod i użycie danych. |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | Zdefiniowana, ta opcja usuwa cały kod stosu TLS związany z trybem serwera TLS, skracając kod i użycie danych.  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | Zdefiniowana, ta opcja powoduje usunięcie wszystkich logiki TLS dla ciphersuitesowych kryptografii krzywej eliptycznej (ECC). Te ciphersuites są opcjonalne w protokole TLS 1,2 i wcześniej, a ich wyłączenie może spowodować zmniejszenie znaczących kodów i rozmiarów danych.|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | Zdefiniowana, ta opcja włącza tryb TLSv 1.3. TLS 1,3 to Najnowsza wersja protokołu TLS i jest domyślnie wyłączona. |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | Zdefiniowana, ta opcja włącza tryb starszej wersji TLSv 1.0. TLSv 1.0 jest uznawany za przestarzały, więc należy ją włączyć tylko w celu zapewnienia zgodności ze starszymi aplikacjami. |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | Zdefiniowana, ta opcja włącza tryb starszej wersji 1.1 TLSv. TLSv 1.1 jest uznawany za przestarzały, więc należy ją włączyć tylko w celu zapewnienia zgodności ze starszymi aplikacjami. |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | Zdefiniowana, ta opcja powoduje wyłączenie trybu TLSv 1.1. Jest on definiowany domyślnie. TLSv 1.1 jest wyłączone na korzyść korzystania tylko z bezpieczniejszej TLSv 1.2<sup>5</sup>.  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | Zdefiniowana, ta opcja umożliwia dokładne porównanie nazw wyróżniających certyfikatów X. 509 w celu przeszukiwania certyfikatów i weryfikacji. Domyślnie porównywane są pola nazw wspólnych nazw wyróżniających.|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | Zdefiniowana, ta opcja włącza opcjonalną nazwę wyróżniającą X. 509, przy kosztach użycia dodatkowej pamięci dla certyfikatów X. 509. |

4. Należy zauważyć, że ta opcja umożliwia tylko łączenie kodu z aplikacją. Aby można było użyć weryfikacji certyfikatu klienta, należy włączyć tę funkcję za pomocą usługi interfejsu API nx_secure_tls_session_client_verify_enable lub skonfigurowania jej przy użyciu nx_secure_tls_session_x509_client_verify_configure.

5. Należy pamiętać, że można również wyłączyć TLSv 1.2, jeśli używany jest tylko protokół TLS 1,0 lub TLS 1,1. Nie jest to jednak zalecane i nie jest bezpośrednio obsługiwane.
