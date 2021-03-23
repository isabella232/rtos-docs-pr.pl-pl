---
title: Rozdział 4 — opis usługi Azure RTO NetX Secure DTLS Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Secure DTLS Services wymienionych w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821594"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="ce4e5-103">Rozdział 4: Opis usługi Azure RTO NetX Secure DTLS Services</span><span class="sxs-lookup"><span data-stu-id="ce4e5-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="ce4e5-104">Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Secure DTLS Services (wymienionych poniżej) w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ce4e5-105">W sekcji "wartości zwracane" w poniższych opisach interfejsu API wartości **pogrubione** nie mają wpływ na to, **NX_SECURE_DISABLE_ERROR_CHECKING** makro, które jest używane do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="ce4e5-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="ce4e5-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ce4e5-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="ce4e5-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="ce4e5-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="ce4e5-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="ce4e5-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="ce4e5-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="ce4e5-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="ce4e5-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="ce4e5-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="ce4e5-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="ce4e5-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="ce4e5-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="ce4e5-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="ce4e5-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="ce4e5-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="ce4e5-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="ce4e5-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="ce4e5-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="ce4e5-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="ce4e5-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="ce4e5-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="ce4e5-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="ce4e5-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="ce4e5-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="ce4e5-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="ce4e5-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="ce4e5-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="ce4e5-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="ce4e5-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="ce4e5-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ce4e5-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="ce4e5-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="ce4e5-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="ce4e5-131">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="ce4e5-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="ce4e5-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="ce4e5-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="ce4e5-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="ce4e5-135">Rozpocznij sesję klienta NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="ce4e5-137">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-137">Description</span></span>

<span data-ttu-id="ce4e5-138">Ta usługa uruchamia sesję klienta DTLS, łącząc się z serwerem pod podanym adresem IP i portem UDP przy użyciu dostarczonego gniazda UDP do komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="ce4e5-139">Przed wywołaniem tej usługi przy użyciu nx_secure_dtls_session_create należy zainicjować blok sterowania sesją DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="ce4e5-140">Ponadto klient DTLS wymaga, aby co najmniej jeden zaufany certyfikat urzędu certyfikacji został dodany do sesji przy użyciu nx_secure_dtls_session_trusted_certificate_add lub klucze wstępne są włączone i skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-141">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-141">Parameters</span></span>

- <span data-ttu-id="ce4e5-142">**dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="ce4e5-143">**udp_socket** Zainicjowane gniazdo UDP, które zostanie użyte do ustanowienia komunikacji sieciowej z serwerem zdalnym DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="ce4e5-144">**IP_address** Wskaźnik na strukturę adresów IP zawierający adres zdalnego serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="ce4e5-145">**port** Zainicjowane gniazdo UDP, które zostanie użyte do ustanowienia komunikacji sieciowej z serwerem zdalnym DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="ce4e5-146">**WAIT_OPTION** Opcja zawieszenia dla próby połączenia.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-147">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-147">Return Values</span></span>

- <span data-ttu-id="ce4e5-148">**NX_SUCCESS** (0x00) — pomyślne przypisanie certyfikatu do sesji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="ce4e5-149">**NX_NOT_CONNECTED** (0x38) serwer nie może nawiązać połączenia z podanym adresem i portem.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="ce4e5-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) otrzymany typ komunikatu TLS/DTLS jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="ce4e5-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="ce4e5-152">Przetwarzanie komunikatu **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) podczas UZGADNIANIA protokołu TLS nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="ce4e5-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) komunikat przychodzący nie powiódł się podczas sprawdzania skrótu Mac.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="ce4e5-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie można wysłać podstawowego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="ce4e5-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) komunikat przychodzący miał nieprawidłową długość pola.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="ce4e5-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) odebrana wiadomość ChangeCipherSpec jest niepoprawna.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="ce4e5-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) przychodzący certyfikat TLS nie nadaje się do identyfikacji zdalnego serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="ce4e5-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) szyfrowanie klucza publicznego dostarczone przez hosta zdalnego nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="ce4e5-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) host zdalny nie wskazywał ciphersuites, które są obsługiwane przez stos NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="ce4e5-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrany komunikat DTLS miał nieznaną wersję DTLS w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="ce4e5-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) odebrany komunikat DTLS miał znaną, ale nieobsługiwaną wersję DTLS w jej nagłówku.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="ce4e5-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się wewnętrzna alokacja pakietu TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="ce4e5-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny dostarczył nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="ce4e5-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="ce4e5-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) wpis w tabeli ciphersuite ma wskaźnik funkcji o wartości null.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="ce4e5-166">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja, gniazdo lub wskaźnik adresu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-167">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-167">Allowed From</span></span>

<span data-ttu-id="ce4e5-168">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-169">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-170">See Also</span></span>

- <span data-ttu-id="ce4e5-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="ce4e5-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="ce4e5-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ce4e5-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="ce4e5-174">Przydziel pakiet dla sesji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="ce4e5-176">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-176">Description</span></span>

<span data-ttu-id="ce4e5-177">Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji DTLS z określonego NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="ce4e5-178">Ta usługa powinna być wywoływana przez aplikację w celu przydzielenia pakietów danych wysyłanych przez połączenie DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="ce4e5-179">Sesja DTLS musi zostać zainicjowana przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="ce4e5-180">Przydzielony pakiet jest prawidłowo zainicjowany, aby można było dodać dane nagłówka i stopki DTLS po wypełnieniu danych pakietu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="ce4e5-181">Zachowanie jest takie samo jak *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-182">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-182">Parameters</span></span>

- <span data-ttu-id="ce4e5-183">**session_ptr** Wskaźnik na wystąpienie sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="ce4e5-184">**pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma zostać przydzielony pakiet.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="ce4e5-185">**packet_ptr** Wskaźnik wyjściowy do nowo przydzielonych pakietów.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="ce4e5-186">**WAIT_OPTION** Opcja zawieszenia dla przydziału pakietu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="ce4e5-187">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-187">Return Values</span></span>

- <span data-ttu-id="ce4e5-188">Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="ce4e5-189">Alokacja podstawowego pakietu **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="ce4e5-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja DTLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-191">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-191">Allowed From</span></span>

<span data-ttu-id="ce4e5-192">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-193">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-194">See Also</span></span>

- <span data-ttu-id="ce4e5-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="ce4e5-196">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="ce4e5-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="ce4e5-200">Dodaj klucz wstępny do sesji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-201">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="ce4e5-202">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-202">Description</span></span>

<span data-ttu-id="ce4e5-203">Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku sterowania sesją DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="ce4e5-204">PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-205">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-205">Parameters</span></span>

- <span data-ttu-id="ce4e5-206">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="ce4e5-207">**pre_shared_key** Rzeczywista wartość klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="ce4e5-208">**psk_length** Długość wartości klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="ce4e5-209">**psk_identity** Ciąg służący do identyfikowania tej wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="ce4e5-210">**identity_length** Długość tożsamości PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="ce4e5-211">**Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="ce4e5-212">**hint_length** Długość ciągu wskazówki.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-213">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-213">Return Values</span></span>

- <span data-ttu-id="ce4e5-214">**NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="ce4e5-215">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="ce4e5-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-217">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-217">Allowed From</span></span>

<span data-ttu-id="ce4e5-218">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-219">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="ce4e5-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-220">See Also</span></span>

- <span data-ttu-id="ce4e5-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="ce4e5-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="ce4e5-223">Tworzenie serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-224">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-224">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a><span data-ttu-id="ce4e5-225">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-225">Description</span></span>

<span data-ttu-id="ce4e5-226">Ta usługa tworzy wystąpienie serwera DTLS do obsługi przychodzących żądań DTLS na określonym porcie UDP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="ce4e5-227">Ze względu na fakt, że protokół UDP jest bezstanowy, żądania DTLS z wielu klientów mogą znajdować się na jednym porcie, podczas gdy inne sesje DTLS są aktywne.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="ce4e5-228">Z tego względu serwer jest wymagany do obsługi aktywnych sesji i prawidłowo kieruje komunikaty przychodzące do odpowiedniej procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="ce4e5-229">Parametr ip_ptr wskazuje wystąpienie NX_IP, które ma być używane dla wewnętrznego gniazda UDP skojarzonego z serwerem DTLS (i przechowywane w bloku kontroli NX_SECURE_DTLS_SERVER).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="ce4e5-230">Wystąpienie i port IP są używane do definiowania interfejsu UDP, na którym serwer jest skonkretyzowany jako usługa nx_secure_dtls_server_start.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="ce4e5-231">Parametr buforu sesji służy do przechowywania bloków sterowania dla wszystkich możliwych równoczesnych sesji DTLS dla serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="ce4e5-232">Powinna być przypisana o rozmiarze, który jest parzystą wielokrotnością rozmiaru struktury bloku sterowania NX_SECURE_DTLS_SESSION.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="ce4e5-233">Aby obliczyć wymagany rozmiar metadanych, można użyć interfejsu API nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="ce4e5-234">Parametr packet_reassembly_buffer jest używany przez DTLS do ponownego łączenia datagramy UDP do kompletnego rekordu DTLS do celów odszyfrowywania i powinien być wystarczająco duży, aby pomieścić największy oczekiwany rekord DTLS (16 KB to DTLS maksymalny rozmiar rekordu, ale wiele aplikacji nie wysyła takich danych w jednym rekordzie).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="ce4e5-235">Procedura wywołania zwrotnego connect_notify jest wywoływana za każdym razem, gdy nowy klient DTLS nawiązuje połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="ce4e5-236">Do aplikacji można uruchomić sesję DTLS przy użyciu usługi *nx_secure_dtls_server_session_start*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="ce4e5-237">Sesja może być uruchomiona w wywołaniu zwrotnym, dlatego zaleca się użycie wywołania zwrotnego tylko do powiadomienia wątku aplikacji (lub dedykowanego wątku DTLS utworzonego przez aplikację) połączenia, ponieważ wywołanie zwrotne jest wywoływane przez wątek IP, który jest używany do przetwarzania wszystkich procesów niskiego poziomu w sieci (np. UDP).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="ce4e5-238">Może to być bardzo proste jako zapisanie parametru sesji DTLS (dostarczonego jako parametr wywołania zwrotnego) i wywołanie nx_secure_dtls_server_session_start w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="ce4e5-239">Wywołanie zwrotne connect_notify powinno zazwyczaj zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="ce4e5-240">Procedura wywołania zwrotnego receive_notify jest wywoływana za każdym razem, gdy zostanie odebrany rekord DTLS zgodny z istniejącą ustanowioną sesją DTLS (zdalny adres IP hosta i port są używane do identyfikacji istniejącej sesji).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="ce4e5-241">Reprezentuje to "dane aplikacji", które są szyfrowane i wysyłane za pośrednictwem DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="ce4e5-242">Aplikacja musi wywoływać *nx_secure_dtls_session_receive* usługi na podanej sesji DTLS, aby pobrać odebrane dane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="ce4e5-243">Podobnie jak w przypadku wywołania zwrotnego connect_receive, zaleca się, aby sesja była przenoszona do innego wątku, aby obsługiwała przetwarzanie komunikatów, gdy wywołanie zwrotne jest wywoływane z wątku IP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="ce4e5-244">Wywołanie zwrotne receive_notify powinno zazwyczaj zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-245">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-245">Parameters</span></span>

- <span data-ttu-id="ce4e5-246">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-247">**ip_ptr** Wskaźnik do zainicjowanego bloku sterowania NX_IP, który ma być używany jako interfejs sieciowy serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="ce4e5-248">**port** Lokalny port UDP, z którym jest powiązana gniazdo UDP serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="ce4e5-249">**limit czasu** Wartość limitu czasu używana dla operacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="ce4e5-250">**session_buffer** Miejsce w buforze zawierające bloki kontroli dla wszystkich wystąpień NX_SECURE_DTLS_SESSION przypisanych do tego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-251">**session_buffer_size** Rozmiar buforu sesji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="ce4e5-252">Określa liczbę sesji DTLS przypisanych do serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="ce4e5-253">**crypto_table** Wskaźnik do struktury tabeli szyfrowania TLS/DTLS używanej do wszystkich operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="ce4e5-254">**crypto_metadata_buffer** Miejsce w buforze dla obliczeń operacji kryptograficznych i informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="ce4e5-255">**crypto_metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="ce4e5-256">**packet_reassembly_buffer** Bufor używany przez DTLS do ponownego składania danych UDP do rekordów DTLS w celu odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="ce4e5-257">**packet_reassembly_buffer_size** Rozmiar buforu ponownego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="ce4e5-258">Ogólnie powinna być większa niż 16 KB, ale może być mniejsza w zależności od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="ce4e5-259">**connect_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy zdalny klient DTLS próbuje nawiązać połączenie z tym serwerem DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="ce4e5-260">**receive_notify** Wywołanie zwrotne wywoływane za każdym razem, gdy dane aplikacji są odbierane przez istniejącą sesję DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-261">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-261">Return Values</span></span>

- <span data-ttu-id="ce4e5-262">**NX_SUCCESS** (0x00) powiodło się utworzenie serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="ce4e5-263">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-264">**NX_INVALID_PARAMETERS** (0x4D) za mało miejsca w buforze dla sesji, ponownego asemblowania pakietu lub kryptografii.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-265">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-265">Allowed From</span></span>

<span data-ttu-id="ce4e5-266">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-267">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-267">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
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

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
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
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

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
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-268">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-268">See Also</span></span>

- <span data-ttu-id="ce4e5-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="ce4e5-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-271">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-272">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="ce4e5-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="ce4e5-275">Zwalnianie zasobów używanych przez serwer NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-276">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="ce4e5-277">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-277">Description</span></span>

<span data-ttu-id="ce4e5-278">Ta usługa zwalnia zasoby przydzielone do wystąpienia serwera DTLS, w tym wewnętrzne gniazdo UDP używane przez serwer.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-279">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-279">Parameters</span></span>

- <span data-ttu-id="ce4e5-280">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-281">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-281">Return Values</span></span>

- <span data-ttu-id="ce4e5-282">**NX_SUCCESS** (0X00) pomyślnie usunięto serwer.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="ce4e5-283">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-284">Gniazdo UDP **NX_STILL_BOUND** (0x42) jest nadal powiązane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-285">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-285">Allowed From</span></span>

<span data-ttu-id="ce4e5-286">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-287">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-287">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
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

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


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
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-288">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-288">See Also</span></span>

- <span data-ttu-id="ce4e5-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="ce4e5-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="ce4e5-293">Dodawanie certyfikatu tożsamości serwera lokalnego do serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-294">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-295">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-295">Description</span></span>

<span data-ttu-id="ce4e5-296">Ta usługa dodaje certyfikat tożsamości serwera lokalnego do wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="ce4e5-297">Do łączenia się z serwerem DTLS jest wymagany co najmniej jeden certyfikat tożsamości, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="ce4e5-298">Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="ce4e5-299">Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 znajdującą się w magazynie serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="ce4e5-300">Więcej informacji na temat certyfikatów serwera X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-301">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-301">Parameters</span></span>

- <span data-ttu-id="ce4e5-302">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-303">**certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="ce4e5-304">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-305">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-305">Return Values</span></span>

- <span data-ttu-id="ce4e5-306">**NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="ce4e5-307">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-308">**NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-309">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-309">Allowed From</span></span>

<span data-ttu-id="ce4e5-310">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-311">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-311">Example</span></span>

<span data-ttu-id="ce4e5-312">\* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_server_create* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-313">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-313">See Also</span></span>

- <span data-ttu-id="ce4e5-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-316">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-317">nx_secure_dtls_server_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="ce4e5-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="ce4e5-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="ce4e5-320">Usuwanie certyfikatu tożsamości serwera lokalnego z serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-321">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-322">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-322">Description</span></span>

<span data-ttu-id="ce4e5-323">Ta usługa usuwa certyfikat tożsamości serwera lokalnego z wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="ce4e5-324">Do łączenia się z serwerem DTLS jest wymagany co najmniej jeden certyfikat tożsamości, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="ce4e5-325">Certyfikat, który ma zostać usunięty, może być identyfikowany przez jego nazwę pospolitą X. 509 lub numeryczną cert_id, która została przypisana w wywołaniu *nx_secure_dtls_server_local_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="ce4e5-326">Cert_id służy tylko do identyfikowania certyfikatu i jest obsługiwany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="ce4e5-327">Jeśli nazwa pospolita jest używana zamiast numerycznego identyfikatora certyfikatu, parametr cert_id powinien mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="ce4e5-328">Usunięcie certyfikatu podczas przetwarzania uzgadniania DTLS spowoduje nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="ce4e5-329">Przed usunięciem certyfikatów należy wywołać *nx_secure_dtls_server_stop* usługi.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-330">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-330">Parameters</span></span>

- <span data-ttu-id="ce4e5-331">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-332">**common_name** Wartość Wspólnaname certyfikatu X. 509 do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="ce4e5-333">Jeśli jest używany, Przekaż cert_id jako zero.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="ce4e5-334">**common_name_length** Długość ciągu common_name w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="ce4e5-335">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="ce4e5-336">Jeśli jest używany, Przekaż NX_NULL dla parametru common_name.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-337">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-337">Return Values</span></span>

- <span data-ttu-id="ce4e5-338">**NX_SUCCESS** (0x00) powiodło się usunięcie certyfikatu z serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="ce4e5-339">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-341">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-341">Allowed From</span></span>

<span data-ttu-id="ce4e5-342">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-343">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-343">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-344">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-344">See Also</span></span>

- <span data-ttu-id="ce4e5-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-346">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-347">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-348">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="ce4e5-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="ce4e5-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="ce4e5-351">Przypisywanie opcjonalnych procedur wywołania zwrotnego powiadomień do serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-352">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="ce4e5-353">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-353">Description</span></span>

<span data-ttu-id="ce4e5-354">Ta usługa może służyć do dodawania opcjonalnych procedur wywołania zwrotnego powiadomień do serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="ce4e5-355">Parametr wywołania zwrotnego można przesłać jako NX_NULL, jeśli pożądane jest tylko jedno wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="ce4e5-356">Wywołanie zwrotne disconnect_notify jest wywoływane, gdy Klient zdalny skończy sesję DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="ce4e5-357">Parametr dtls_session to wystąpienie sesji, które zostało zamknięte.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="ce4e5-358">Wywołanie zwrotne powinno zwykle zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="ce4e5-359">Wywołanie zwrotne error_notify jest wywoływane za każdym razem, gdy wystąpi błąd DTLS lub limit czasu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="ce4e5-360">Dtls_session parametr jest wystąpieniem sesji, dla którego wystąpił błąd, a error_code to liczbowy kod stanu dla błędu, który spowodował problem (patrz dodatek A)</span><span class="sxs-lookup"><span data-stu-id="ce4e5-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="ce4e5-361">NetX bezpieczne kody powrotu/błędów dla listy kodów błędów, które mogą zostać zwrócone).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="ce4e5-362">Wywołanie zwrotne powinno zwykle zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-363">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-363">Parameters</span></span>

- <span data-ttu-id="ce4e5-364">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-365">**disconnect_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy zdalny host klienta zamknie sesję DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="ce4e5-366">**error_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy DTLS napotka błąd lub przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-367">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-367">Return Values</span></span>

- <span data-ttu-id="ce4e5-368">**NX_SUCCESS** (0x00) — pomyślne przypisanie procedur wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="ce4e5-369">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-370">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-370">Allowed From</span></span>

<span data-ttu-id="ce4e5-371">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-372">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-372">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-373">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-373">See Also</span></span>

- <span data-ttu-id="ce4e5-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-375">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="ce4e5-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="ce4e5-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="ce4e5-378">Dodaj klucz wstępny do serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-379">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="ce4e5-380">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-380">Description</span></span>

<span data-ttu-id="ce4e5-381">Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku sterowania serwerem DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="ce4e5-382">PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="ce4e5-383">Dodany PSK jest replikowany na wszystkich sesjach DTLS przypisanych do serwera DTLS (za pośrednictwem buforu sesji podanego w wywołaniu nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-384">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-384">Parameters</span></span>

- <span data-ttu-id="ce4e5-385">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-386">**pre_shared_key** Rzeczywista wartość klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="ce4e5-387">**psk_length** Długość wartości klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="ce4e5-388">**psk_identity** Ciąg służący do identyfikowania tej wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="ce4e5-389">**identity_length** Długość tożsamości PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="ce4e5-390">**Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="ce4e5-391">**hint_length** Długość ciągu wskazówki.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-392">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-392">Return Values</span></span>

- <span data-ttu-id="ce4e5-393">**NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="ce4e5-394">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="ce4e5-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-396">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-396">Allowed From</span></span>

<span data-ttu-id="ce4e5-397">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-398">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-399">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-399">See Also</span></span>

- <span data-ttu-id="ce4e5-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="ce4e5-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="ce4e5-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="ce4e5-402">Wysyłanie danych za pośrednictwem sesji DTLS z serwerem NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-403">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="ce4e5-404">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-404">Description</span></span>

<span data-ttu-id="ce4e5-405">Ta usługa wysyła pakiet danych przez ustanowioną sesję serwera DTLS do zdalnego hosta klienta DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="ce4e5-406">Używana sesja jest uzyskiwana w procedurze wywołania zwrotnego receive_notify dostarczonej do nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="ce4e5-407">Dane podane w pakiecie, które muszą zostać przydzieloną przy użyciu *nx_secure_dtls_packet_allocate*, są szyfrowane przy użyciu parametrów i procedur kryptograficznych sesji DTLS, a następnie wysyłane do hosta zdalnego przez wewnętrzny port UDP serwera DTLS do adresu IP i portu dołączonego klienta (przechowywanego w sesji DTLS).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-408">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-408">Parameters</span></span>

- <span data-ttu-id="ce4e5-409">**session_ptr** Wskaźnik do wystąpienia sesji DTLS uzyskany z procedury wywołania zwrotnego receive_notify dostarczonej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="ce4e5-410">**packet_ptr** Wskaźnik do wystąpienia NX_PACKET przydzielono wcześniej i uzupełniony o dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-411">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-411">Return Values</span></span>

- <span data-ttu-id="ce4e5-412">**NX_SUCCESS** (0x00) powiodło się utworzenie serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="ce4e5-413">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) wystąpił błąd w podstawowej operacji wysyłania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-415">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-415">Allowed From</span></span>

<span data-ttu-id="ce4e5-416">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-417">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-417">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


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

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


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

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-418">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-418">See Also</span></span>

- <span data-ttu-id="ce4e5-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="ce4e5-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="ce4e5-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="ce4e5-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="ce4e5-424">Uruchamianie sesji DTLS z serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-425">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="ce4e5-426">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-426">Description</span></span>

<span data-ttu-id="ce4e5-427">Ta usługa uruchamia sesję serwera DTLS, wykonując uzgodnienie DTLS po stronie serwera, gdy zdalny klient DTLS nawiązał połączenie z serwerem i zażądał połączenia DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="ce4e5-428">Sesja DTLS jest uzyskiwana w procedurze wywołania zwrotnego connect_notify dostarczonej do nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-429">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-429">Parameters</span></span>

- <span data-ttu-id="ce4e5-430">**session_ptr** Wskaźnik do wystąpienia sesji DTLS uzyskanego z serwera DTLS connect_notify wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="ce4e5-431">**WAIT_OPTION** Wartość ThreadX oczekiwania na użycie dla operacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-432">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-432">Return Values</span></span>

- <span data-ttu-id="ce4e5-433">**NX_SUCCESS** (0x00) powiodło się utworzenie serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="ce4e5-434">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie może przydzielić pakietu uzgadniania DTLS (Pula pakietów jest pusta).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="ce4e5-436">**NX_SECURE_TLS_INVALID_PACKET** (0X104) odebrano dane, które nie były prawidłowym rekordem DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="ce4e5-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) nie można prawidłowo wykonać mieszania DTLS rekordu (błąd szyfrowania).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="ce4e5-438">Niepowodzenie sprawdzania uzupełniania szyfrowania **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="ce4e5-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) odebrano alert z hosta zdalnego podczas uzgadniania DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="ce4e5-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) otrzymał nierozpoznany komunikat podczas uzgadniania DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="ce4e5-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) odebrano rekord DTLS o nieprawidłowej długości.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="ce4e5-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) otrzymał komunikacie ClientHello bez obsługiwanego DTLS ciphersuites.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="ce4e5-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118) odebrano komunikacie ClientHello za pomocą nieznanej metody kompresji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="ce4e5-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0X107) ogólny błąd uzgadniania (nieokreślony), zwykle z powodu problemów z przetwarzaniem rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="ce4e5-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) funkcja, która nie jest jeszcze obsługiwana, została wywołana podczas uzgadniania DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="ce4e5-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) napotkano nieznany CIPHERSUITE (wskazano wewnętrzny błąd kryptografii).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="ce4e5-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) odebrano rekord DTLS z niezgodną wersją DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="ce4e5-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115) nie może zweryfikować skrótu uzgadniania DTLS, sesja jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="ce4e5-449">Nie powiodło się wysyłanie wewnętrznego protokołu UDP **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-450">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-450">Allowed From</span></span>

<span data-ttu-id="ce4e5-451">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-452">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-452">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
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

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

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
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-453">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-453">See Also</span></span>

- <span data-ttu-id="ce4e5-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="ce4e5-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="ce4e5-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="ce4e5-459">Uruchom wystąpienie serwera NetX bezpiecznego DTLS nasłuchiwanie na skonfigurowanym porcie UDP</span><span class="sxs-lookup"><span data-stu-id="ce4e5-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-460">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="ce4e5-461">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-461">Description</span></span>

<span data-ttu-id="ce4e5-462">Ta usługa uruchamia serwer DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="ce4e5-463">Po powrocie wywołania serwer jest aktywny i rozpocznie przetwarzanie przychodzących żądań od klientów DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="ce4e5-464">Wystąpienie serwera musi być skonfigurowane z *nx_secure_dtls_server_create* usługi.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="ce4e5-465">Ta usługa wiąże wewnętrzny port UDP serwera DTLS ze skonfigurowanym portem lokalnym, w związku z czym wystąpi większość napotkanych problemów z konfiguracją komunikacji przy użyciu protokołu UDP i sieci.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-466">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-466">Parameters</span></span>

- <span data-ttu-id="ce4e5-467">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-468">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-468">Return Values</span></span>

- <span data-ttu-id="ce4e5-469">**NX_SUCCESS** (0X00) pomyślnie uruchomiono serwer.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="ce4e5-470">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-471">Nie włączono protokołu UDP **NX_NOT_ENABLED** (0x14).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="ce4e5-472">**NX_NO_FREE_PORTS** (0X45) Brak dostępnych portów UDP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="ce4e5-473">**NX_INVALID_PORT** (0X46) nieprawidłowy port UDP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="ce4e5-474">Port UDP **NX_ALREADY_BOUND** (0x22) jest już powiązany.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="ce4e5-475">Nie można używać portu UDP **NX_PORT_UNAVAILABLE** (0x23).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-476">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-476">Allowed From</span></span>

<span data-ttu-id="ce4e5-477">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-478">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-478">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
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

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

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

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-479">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-479">See Also</span></span>

- <span data-ttu-id="ce4e5-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-482">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="ce4e5-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="ce4e5-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="ce4e5-485">Zatrzymaj aktywne wystąpienie serwera usługi NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-486">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="ce4e5-487">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-487">Description</span></span>

<span data-ttu-id="ce4e5-488">Ta usługa zatrzymuje serwer DTLS przed nasłuchiwaniem na porcie UDP i resetuje wszystkie skojarzone sesje DTLS, przerywając wszelką komunikację DTLS w toku.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-489">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-489">Parameters</span></span>

- <span data-ttu-id="ce4e5-490">**server_ptr** Wskaźnik na aktywne wystąpienie serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-491">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-491">Return Values</span></span>

- <span data-ttu-id="ce4e5-492">Pomyślnie zatrzymano serwer **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="ce4e5-493">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-494">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-494">Allowed From</span></span>

<span data-ttu-id="ce4e5-495">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-496">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-496">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
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

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


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

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-497">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-497">See Also</span></span>

- <span data-ttu-id="ce4e5-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-500">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="ce4e5-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="ce4e5-503">Dodawanie certyfikatu zaufanego urzędu certyfikacji do serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-504">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-505">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-505">Description</span></span>

<span data-ttu-id="ce4e5-506">Ta usługa dodaje Certyfikat zaufanego urzędu certyfikacji lub pośredniego urzędu certyfikacji do wystąpienia serwera DTLS i jest przypisany do wszystkich wewnętrznych sesji serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="ce4e5-507">Jest to konieczne tylko wtedy, gdy uwierzytelnianie certyfikatu klienta X. 509 jest włączone przy użyciu *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="ce4e5-508">Dodany certyfikat będzie używany do weryfikowania przychodzących certyfikatów klienta X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="ce4e5-509">Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="ce4e5-510">Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 znajdującą się w magazynie serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="ce4e5-511">Więcej informacji na temat certyfikatów serwera X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-512">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-512">Parameters</span></span>

- <span data-ttu-id="ce4e5-513">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-514">**certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="ce4e5-515">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-516">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-516">Return Values</span></span>

- <span data-ttu-id="ce4e5-517">**NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="ce4e5-518">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-519">**NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-520">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-520">Allowed From</span></span>

<span data-ttu-id="ce4e5-521">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-522">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-522">Example</span></span>

<span data-ttu-id="ce4e5-523">\* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_server_create* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-524">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-524">See Also</span></span>

- <span data-ttu-id="ce4e5-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-527">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-528">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-529">nx_secure_dtls_server_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="ce4e5-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="ce4e5-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="ce4e5-532">Usuwanie certyfikatu zaufanego urzędu certyfikacji z serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-533">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-534">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-534">Description</span></span>

<span data-ttu-id="ce4e5-535">Ta usługa usuwa Certyfikat zaufanego urzędu certyfikacji z wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="ce4e5-536">Certyfikaty zaufanych urzędów certyfikacji są niezbędne tylko dla serwera DTLS, dla którego weryfikacja certyfikatu klienta X. 509 została włączona przez wywołanie *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="ce4e5-537">Certyfikat, który ma zostać usunięty, może być identyfikowany przez jego nazwę pospolitą X. 509 lub numeryczną cert_id, która została przypisana w wywołaniu *nx_secure_dtls_server_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="ce4e5-538">Cert_id służy tylko do identyfikowania certyfikatu i jest obsługiwany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="ce4e5-539">Jeśli nazwa pospolita jest używana zamiast numerycznego identyfikatora certyfikatu, parametr cert_id powinien mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="ce4e5-540">Usuwanie certyfikatu podczas przetwarzania uzgadniania DTLS może spowodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="ce4e5-541">Przed usunięciem certyfikatów należy wywołać *nx_secure_dtls_server_stop* usługi.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-542">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-542">Parameters</span></span>

- <span data-ttu-id="ce4e5-543">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-544">**common_name** Wartość Wspólnaname certyfikatu X. 509 do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="ce4e5-545">Jeśli jest używany, Przekaż cert_id jako zero.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="ce4e5-546">**common_name_length** Długość ciągu common_name w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="ce4e5-547">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="ce4e5-548">Jeśli jest używany, Przekaż NX_NULL dla parametru common_name.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="ce4e5-549">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-549">Return Values</span></span>

- <span data-ttu-id="ce4e5-550">**NX_SUCCESS** (0x00) powiodło się usunięcie certyfikatu z serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="ce4e5-551">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-553">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-553">Allowed From</span></span>

<span data-ttu-id="ce4e5-554">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-555">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-555">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-556">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-556">See Also</span></span>

- <span data-ttu-id="ce4e5-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-558">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-559">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-560">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="ce4e5-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="ce4e5-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="ce4e5-563">Konfigurowanie serwera NetX Secure DTLS do żądania i weryfikowania certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="ce4e5-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-564">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="ce4e5-565">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-565">Description</span></span>

<span data-ttu-id="ce4e5-566">Ta usługa służy do konfigurowania serwera DTLS do żądania i weryfikowania certyfikatów klienta DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="ce4e5-567">Ta funkcja opcjonalna jest używana, gdy certyfikaty X. 509 są wymagane do uwierzytelnienia klienta zamiast innych mechanizmów (np. klucza wstępnego).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce4e5-568">*Gdy serwer DTLS jest skonfigurowany do weryfikowania certyfikatów klienta przy użyciu tej usługi, należy dodać co najmniej jeden zaufany certyfikat urzędu certyfikacji do serwera przy użyciu nx_secure_dtls_server_trusted_certificate_add lub serwer odrzuci wszystkie przychodzące połączenia klientów, ponieważ nie będzie mógł zweryfikować certyfikatów klienta w zaufanym magazynie.*</span><span class="sxs-lookup"><span data-stu-id="ce4e5-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="ce4e5-569">Po wywołaniu tej usługi wystąpienie serwera DTLS będzie (po uruchomieniu) zażądać certyfikatów klienta w ramach uzgadniania DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="ce4e5-570">Przy założeniu, że klient zostanie prawidłowo skonfigurowany przy użyciu certyfikatu tożsamości (i powiązanego łańcucha certyfikatów, jeśli ma zastosowanie), serwer DTLS wymaga przydzielenia pamięci do przetworzenia danych certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="ce4e5-571">Ta pamięć jest przenoszona jako parametr *certs_buffer* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="ce4e5-572">Certs_buffer musi mieć rozmiar w celu uwzględnienia największego oczekiwanego łańcucha certyfikatów od klienta DTLS, *ile sesji serwera DTLS*.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="ce4e5-573">Bufor jest dzielony między dostępnymi sesjami przy użyciu parametru *certs_per_session* , który reprezentuje maksymalną oczekiwaną liczbę certyfikatów w łańcuchu certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="ce4e5-574">Bufor musi także zapewnić miejsce dla NX_SECURE_X509_CERTej struktury danych, która jest używana do analizowania danych certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="ce4e5-575">Obliczanie odpowiedniego rozmiaru buforu można wykonać przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="ce4e5-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="ce4e5-576">Liczba sesji DTLS jest określana przez rozmiar buforu sesji przekazaną do nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="ce4e5-577">certs_per_session powinna być ustawiona na maksymalną oczekiwaną liczbę certyfikatów w łańcuchu certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="ce4e5-578">Maksymalny oczekiwany rozmiar certyfikatu zależy od aplikacji, rozmiarów kluczy i innych czynników, ale 2KB jest ogólnie wystarczający.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-579">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-579">Parameters</span></span>

- <span data-ttu-id="ce4e5-580">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="ce4e5-581">**certs_per_session** Liczba certyfikatów do przydzielenia do każdej sesji serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="ce4e5-582">**certs_buffer** Miejsce w buforze dla danych certyfikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="ce4e5-583">**buffer_size** Rozmiar buforu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-584">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-584">Return Values</span></span>

- <span data-ttu-id="ce4e5-585">**NX_SUCCESS** (0x00) pomyślna konfiguracja weryfikacji klienta X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="ce4e5-586">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-587">**NX_INVALID_PARAMETERS** (0x4D) nieprawidłowy magazyn certyfikatów (wystąpienie DTLSserver nie initalized?).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-588">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-588">Allowed From</span></span>

<span data-ttu-id="ce4e5-589">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-590">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-590">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-591">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-591">See Also</span></span>

- <span data-ttu-id="ce4e5-592">nx_secure_dtls_server_x509_client_verify_disable,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="ce4e5-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-594">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-595">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-596">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="ce4e5-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="ce4e5-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="ce4e5-599">Wyłącza weryfikację certyfikatu X. 509 klienta dla serwera NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-600">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="ce4e5-601">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-601">Description</span></span>

<span data-ttu-id="ce4e5-602">Ta usługa wyłącza weryfikację certyfikatu klienta X. 509 na serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="ce4e5-603">Usługa nie działa, Jeśli weryfikacja certyfikatu klienta X. 509 nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="ce4e5-604">Wyłączenie uwierzytelniania klienta w aktywnym wystąpieniu serwera DTLS może spowodować nieprzewidywalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="ce4e5-605">Przed zmianą stanu serwera należy wywołać usługę nx_secure_dtls_server_stop.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-606">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-606">Parameters</span></span>

- <span data-ttu-id="ce4e5-607">**server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-608">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-608">Return Values</span></span>

- <span data-ttu-id="ce4e5-609">**NX_SUCCESS** (0X00) pomyślne wyłączenie uwierzytelniania klienta X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="ce4e5-610">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-611">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-611">Allowed From</span></span>

<span data-ttu-id="ce4e5-612">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-613">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-613">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-614">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-614">See Also</span></span>

- <span data-ttu-id="ce4e5-615">nx_secure_dtls_server_x509_client_verify_configure,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="ce4e5-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="ce4e5-617">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="ce4e5-618">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="ce4e5-619">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="ce4e5-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="ce4e5-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="ce4e5-622">Pobierz informacje o kliencie zdalnym z sesji serwera DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-623">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="ce4e5-624">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-624">Description</span></span>

<span data-ttu-id="ce4e5-625">Ta usługa zwraca informacje o sieci dotyczące klienta DTLS, który jest połączony z określoną sesją serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="ce4e5-626">Zwracane informacje składają się z adresu IP i portu protokołu UDP klienta zdalnego, a także portu serwera lokalnego, z którym jest połączony klient.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="ce4e5-627">Ogólnie rzecz biorąc, wystąpienie sesji DTLS będzie to ten, który uzyskano w wywołaniu jednej z procedur wywołania zwrotnego powiadomień DTLS (np. wywołania zwrotne connect_notify lub receive_notify przekazywane do nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-628">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-628">Parameters</span></span>

- <span data-ttu-id="ce4e5-629">**session_ptr** Wskaźnik na aktywne wystąpienie sesji serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-630">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-630">Return Values</span></span>

- <span data-ttu-id="ce4e5-631">**NX_SUCCESS** (0X00) pomyślnie usunięto serwer.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="ce4e5-632">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-633">**NX_INVALID_SOCKET** (0x13) SKOJARZONE gniazdo UDP jest nieprawidłowe (sesja nie została zainicjowana?).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="ce4e5-634">Gniazdo UDP **NX_NOT_CONNECTED** (0x38) nie jest połączone — połączenie klienta zostało usunięte lub jeszcze nie zostało nawiązane.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-635">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-635">Allowed From</span></span>

<span data-ttu-id="ce4e5-636">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-637">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-637">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
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
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


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

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-638">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-638">See Also</span></span>

- <span data-ttu-id="ce4e5-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="ce4e5-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="ce4e5-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="ce4e5-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="ce4e5-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="ce4e5-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="ce4e5-644">Tworzenie i Konfigurowanie sesji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-645">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-645">Prototype</span></span>

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a><span data-ttu-id="ce4e5-646">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-646">Description</span></span>

<span data-ttu-id="ce4e5-647">Ta usługa tworzy i konfiguruje sesję DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="ce4e5-648">Ogólnie rzecz biorąc, ta metoda zostanie użyta do utworzenia sesji klienta DTLS jako sesji serwera DTLS, które są zarządzane za pomocą mechanizmu serwera DTLS (zobacz *nx_secure_dtls_server_create*), ale mogą istnieć wystąpienia, w których aplikacja musi utworzyć jedno autonomiczne wystąpienie sesji serwera DTLS, w którym ta usługa może być używana <sup>7</sup>.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="ce4e5-649">Parametry konfigurują alokację informacji i pamięci wymaganą do utworzenia wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="ce4e5-650">Crypto_table parametr jest tabelą protokołu TLS zawierającą wszystkie procedury kryptograficzne, które są zbędne do szyfrowania i uwierzytelniania TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="ce4e5-651">Metadata_buffer jest używany do szyfrowania caclulations (patrz nx_secure_tls_metadata_size_calculate w podręczniku użytkownika NetX Secure TLS), a packet_reassembly_buffer służy do ponownego łączenia datagramów UDP z kompletnym rekordem DTLS w celu odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="ce4e5-652">Certs_number i remote_certificate_buffer są wymagane dla klientów DTLS, którzy muszą mieć miejsce do przechowywania i przetwarzania przychodzącego łańcucha certyfikatów serwera DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="ce4e5-653">Bufor musi być w stanie obsłużyć maksymalny oczekiwany rozmiar łańcucha certyfikatów dla każdego serwera, z którym zostanie nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="ce4e5-654">Bufor jest dzielony przez liczbę oczekiwanych certyfikatów (certs_number parametr) i musi być wystarczająco duży, aby pomieścić jedną strukturę NX_SECURE_X509_CERT dla każdego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="ce4e5-655">Rozmiar buforu można określić przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="ce4e5-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="ce4e5-656">certs_number to oczekiwana Maksymalna liczba certyfikatów w łańcuchu certyfikatów serwera</span><span class="sxs-lookup"><span data-stu-id="ce4e5-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="ce4e5-657">Maksymalny rozmiar certyfikatu zależy od rozmiaru używanych kluczy i informacji w certyfikacie, ale 2KB jest ogólnie wystarczający.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="ce4e5-658">**7** Tworzenie sesji serwera DTLS z tą procedurą nie jest zalecane i zawiera pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="ce4e5-659">Podstawowym problemem jest to, że sesja nie będzie obsługiwać dodatkowych połączeń z klientami — ponieważ protokół UDP jest bezczynny, drugi klient może legalnie wysyłać dane do portu UDP serwera, gdy Poprzednia sesja DTLS nadal jest aktywna, co spowodowałoby zakończenie sesji serwera z powodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-660">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-660">Parameters</span></span>

- <span data-ttu-id="ce4e5-661">**dtls_session** Wskaźnik na niezainicjowaną strukturę sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="ce4e5-662">**crypto_table** Wskaźnik do struktury tabeli szyfrowania TLS/DTLS używanej do wszystkich operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="ce4e5-663">**crypto_metadata_buffer** Miejsce w buforze dla obliczeń operacji kryptograficznych i informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="ce4e5-664">**crypto_metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="ce4e5-665">**packet_reassembly_buffer** Bufor używany przez DTLS do ponownego składania danych UDP do rekordów DTLS w celu odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="ce4e5-666">**packet_reassembly_buffer_size** Rozmiar buforu ponownego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="ce4e5-667">Ogólnie powinna być większa niż 16 KB, ale może być mniejsza w zależności od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="ce4e5-668">**certs_number** Maksymalna oczekiwana liczba certyfikatów w łańcuchu certyfikatów serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="ce4e5-669">**remote_certificate_buffer** Miejsce w buforze dla danych certyfikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="ce4e5-670">**remote_certificate_buffer_size** Rozmiar buforu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="ce4e5-671">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-671">Return Values</span></span>

- <span data-ttu-id="ce4e5-672">**NX_SUCCESS** (0X00) pomyślnie utworzono sesję.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="ce4e5-673">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="ce4e5-674">**NX_INVALID_PARAMETERS** (0x4D) za mało miejsca w buforze na potrzeby ponownego asemblowania pakietów, certyfikatów lub kryptografii.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-675">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-675">Allowed From</span></span>

<span data-ttu-id="ce4e5-676">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-677">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-677">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-678">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-678">See Also</span></span>

- <span data-ttu-id="ce4e5-679">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="ce4e5-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="ce4e5-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="ce4e5-682">Zwalnianie zasobów używanych przez sesję NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-683">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="ce4e5-684">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-684">Description</span></span>

<span data-ttu-id="ce4e5-685">Ta usługa usuwa sesję DTLS i zwalnia wszystkie zasoby, które zostały przydzieloną podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-686">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-686">Parameters</span></span>

- <span data-ttu-id="ce4e5-687">**dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-688">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-688">Return Values</span></span>

- <span data-ttu-id="ce4e5-689">**NX_SUCCESS** (0X00) pomyślnie usunięto sesję.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="ce4e5-690">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-691">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-691">Allowed From</span></span>

<span data-ttu-id="ce4e5-692">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-693">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-693">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-694">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-694">See Also</span></span>

- <span data-ttu-id="ce4e5-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="ce4e5-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="ce4e5-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="ce4e5-698">Zamykanie aktywnej sesji usługi NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-699">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="ce4e5-700">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-700">Description</span></span>

<span data-ttu-id="ce4e5-701">Ta usługa służy do kończenia aktywnej sesji DTLS przez wysłanie alertu CloseNotify TLS/DTLS do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="ce4e5-702">Używanym adresem IP i portem są te, które są używane w poprzednim wywołaniu do nx_secure_dtls_session_send.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-703">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-703">Parameters</span></span>

- <span data-ttu-id="ce4e5-704">**dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="ce4e5-705">**WAIT_OPTION** Wartość ThreadX oczekiwania na użycie dla operacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-706">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-706">Return Values</span></span>

- <span data-ttu-id="ce4e5-707">**NX_SUCCESS** (0X00) pomyślnie usunięto sesję.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="ce4e5-708">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="ce4e5-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie może przydzielić pakietów dla alertu CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="ce4e5-710">Wystąpił błąd wewnętrzny **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) — nie rozpoznano procedury kryptograficznej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="ce4e5-711">Nie można wysłać podstawowego protokołu UDP **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="ce4e5-712">**NX_IP_ADDRESS_ERROR** (0X21) błąd z adresem IP hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="ce4e5-713">**NX_NOT_BOUND** (0X24) bazowego gniazda UDP nie jest powiązany z portem.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="ce4e5-714">**NX_INVALID_PORT** (0X46) nieprawidłowy port UDP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="ce4e5-715">Nie można używać portu UDP **NX_PORT_UNAVAILABLE** (0x23).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-716">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-716">Allowed From</span></span>

<span data-ttu-id="ce4e5-717">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-718">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-718">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-719">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-719">See Also</span></span>

- <span data-ttu-id="ce4e5-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="ce4e5-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="ce4e5-723">Dodawanie certyfikatu tożsamości lokalnej do sesji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-724">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-725">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-725">Description</span></span>

<span data-ttu-id="ce4e5-726">Ta usługa dodaje certyfikat tożsamości lokalnej do wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="ce4e5-727">Ogólnie rzecz biorąc, ta usługa zostanie użyta, gdy sesja klienta DTLS musi dostarczyć certyfikat tożsamości do hosta serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="ce4e5-728">Jest to opcjonalna konfiguracja dla programu DTLS, dzięki czemu certyfikat nie jest zazwyczaj wymagany dla klientów DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="ce4e5-729">Certyfikat tożsamości wymaga skojarzonego z nim klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="ce4e5-730">Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="ce4e5-731">Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="ce4e5-732">Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-733">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-733">Parameters</span></span>

- <span data-ttu-id="ce4e5-734">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="ce4e5-735">**certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="ce4e5-736">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-737">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-737">Return Values</span></span>

- <span data-ttu-id="ce4e5-738">**NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="ce4e5-739">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-740">**NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-741">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-741">Allowed From</span></span>

<span data-ttu-id="ce4e5-742">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-743">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-743">Example</span></span>

<span data-ttu-id="ce4e5-744">\* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-745">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-745">See Also</span></span>

- <span data-ttu-id="ce4e5-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="ce4e5-748">nx_secure_dtls_session_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="ce4e5-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="ce4e5-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="ce4e5-751">Usuń certyfikat tożsamości lokalnej z sesji usługi NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-752">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-753">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-753">Description</span></span>

<span data-ttu-id="ce4e5-754">Ta usługa usuwa certyfikat tożsamości lokalnej z wystąpienia sesji DTLS przy użyciu numeru identyfikatora certyfikatu (przypisanego, gdy certyfikat został dodany przy użyciu nx_secure_dtls_session_local_certificate_add) lub pola X. 509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="ce4e5-755">Jeśli common_name jest używany do dopasowania certyfikatu, parametr cert_id powinien mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="ce4e5-756">Jeśli jest używana cert_id, common_name powinna zostać przeniesiona wartość NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="ce4e5-757">Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="ce4e5-758">Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="ce4e5-759">Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-760">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-760">Parameters</span></span>

- <span data-ttu-id="ce4e5-761">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="ce4e5-762">**common_name** Wskaźnik do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="ce4e5-763">**common_name_length** Długość ciągu common_name.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="ce4e5-764">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-765">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-765">Return Values</span></span>

- <span data-ttu-id="ce4e5-766">**NX_SUCCESS** (0X00) pomyślne usunięcie certyfikatu z sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="ce4e5-767">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danej sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-769">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-769">Allowed From</span></span>

<span data-ttu-id="ce4e5-770">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-771">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-771">Example</span></span>

<span data-ttu-id="ce4e5-772">\* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-773">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-773">See Also</span></span>

- <span data-ttu-id="ce4e5-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="ce4e5-776">nx_secure_dtls_session_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="ce4e5-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ce4e5-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="ce4e5-779">Odbieraj dane aplikacji przez ustanowioną sesję NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-780">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="ce4e5-781">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-781">Description</span></span>

<span data-ttu-id="ce4e5-782">Ta usługa zwraca dane aplikacji odebrane przez aktywną sesję DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="ce4e5-783">Sesja DTLS może być sesją serwera DTLS (zarządzaną przez wystąpienie serwera DTLS) lub sesją klienta DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="ce4e5-784">Zwrócony pakiet może być przetwarzany przy użyciu dowolnych usług NX_PACKET API (więcej informacji znajduje się w dokumentacji NetX).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-785">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-785">Parameters</span></span>

- <span data-ttu-id="ce4e5-786">**dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="ce4e5-787">**packet_ptr_ptr** Wskaźnik do NX_PACKETego wskaźnika dla pakietu zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="ce4e5-788">**WAIT_OPTION** Wartość ThreadX oczekiwania na użycie dla operacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-789">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-789">Return Values</span></span>

- <span data-ttu-id="ce4e5-790">**NX_SUCCESS** (0X00) pomyślne otrzymanie pakietu danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="ce4e5-791">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji lub pakietu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="ce4e5-792">**NX_NOT_ENABLED** (0X14) UDP nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="ce4e5-793">Gniazdo UDP **NX_NOT_BOUND** (0x24) nie jest powiązane z portem.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="ce4e5-794">**NX_SECURE_TLS_INVALID_PACKET** (0X104) odebrano dane, które nie były prawidłowym rekordem DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="ce4e5-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) nie można prawidłowo wykonać mieszania DTLS rekordu (błąd szyfrowania).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="ce4e5-796">Niepowodzenie sprawdzania uzupełniania szyfrowania **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="ce4e5-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) odebrano alert z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="ce4e5-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0X102) otrzymał nierozpoznany komunikat.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="ce4e5-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) odebrano rekord DTLS o nieprawidłowej długości.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="ce4e5-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) napotkano nieznany CIPHERSUITE (wskazuje wewnętrzny błąd kryptografii).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="ce4e5-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) odebrano rekord DTLS z niezgodną wersją DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-802">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-802">Allowed From</span></span>

<span data-ttu-id="ce4e5-803">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-804">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-804">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-805">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-805">See Also</span></span>

- <span data-ttu-id="ce4e5-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="ce4e5-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="ce4e5-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="ce4e5-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="ce4e5-809">Wyczyść dane w NetX bezpieczne wystąpienie sesji DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-810">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="ce4e5-811">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-811">Description</span></span>

<span data-ttu-id="ce4e5-812">Ta usługa resetuje sesję DTLS, czyszcząc wszystkie tymczasowe dane kryptograficzne i umożliwiając ponowne użycie struktury dla nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="ce4e5-813">Trwałe dane (np. magazyny certyfikatów) są utrzymywane w taki sposób, aby nx_secure_dtls_session_create nie wymagały wielokrotnego wywoływania.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-814">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-814">Parameters</span></span>

- <span data-ttu-id="ce4e5-815">**dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-816">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-816">Return Values</span></span>

- <span data-ttu-id="ce4e5-817">**NX_SUCCESS** (0X00) pomyślnie zresetował sesję.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="ce4e5-818">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-819">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-819">Allowed From</span></span>

<span data-ttu-id="ce4e5-820">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-821">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-821">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-822">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-822">See Also</span></span>

- <span data-ttu-id="ce4e5-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ce4e5-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="ce4e5-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="ce4e5-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="ce4e5-826">Wysyłanie danych za pośrednictwem sesji DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-827">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="ce4e5-828">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-828">Description</span></span>

<span data-ttu-id="ce4e5-829">Ta usługa wysyła pakiet danych przez ustanowioną sesję DTLS do zdalnego hosta DTLS pod danym adresem IP i porcie.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="ce4e5-830">Używana sesja to aktywna sesja klienta usługi DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="ce4e5-831">Należy pamiętać, że adres IP i port są dostarczane z powodu bezstanowego charakteru protokołu UDP, ale zazwyczaj powinny być zgodne z adresem i portem używanym do uruchomienia sesji w nx_secure_dtls_session_start.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="ce4e5-832">Dane podane w pakiecie, które muszą zostać przydzieloną przy użyciu *nx_secure_dtls_packet_allocate*, są szyfrowane przy użyciu parametrów i procedur kryptograficznych sesji DTLS, a następnie wysyłane do hosta zdalnego przez gniazdo UDP sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-833">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-833">Parameters</span></span>

- <span data-ttu-id="ce4e5-834">**session_ptr** Wskaźnik na aktywne wystąpienie sesji klienta DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="ce4e5-835">**packet_ptr** Wskaźnik do wystąpienia NX_PACKET przydzielono wcześniej i uzupełniony o dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="ce4e5-836">**IP_address** Wskaźnik do struktury NXD_ADDRESS zawierającej adres IP hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="ce4e5-837">**port** Port UDP na hoście zdalnym.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-838">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-838">Return Values</span></span>

- <span data-ttu-id="ce4e5-839">**NX_SUCCESS** (0x00) pomyślnego wysłania pakietu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="ce4e5-840">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) wystąpił błąd w podstawowej operacji wysyłania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-842">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-842">Allowed From</span></span>

<span data-ttu-id="ce4e5-843">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-844">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-844">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-845">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-845">See Also</span></span>

- <span data-ttu-id="ce4e5-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="ce4e5-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="ce4e5-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ce4e5-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="ce4e5-849">Dodawanie certyfikatu zaufanego urzędu certyfikacji do sesji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-851">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-851">Description</span></span>

<span data-ttu-id="ce4e5-852">Ta usługa dodaje zaufany urząd certyfikacji lub pośredni certyfikat X. 509 urzędu certyfikacji do wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="ce4e5-853">Klient DTLS wymaga co najmniej jednego zaufanego certyfikatu w celu weryfikacji certyfikatów serwera zdalnego, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).</span><span class="sxs-lookup"><span data-stu-id="ce4e5-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="ce4e5-854">Zaufany certyfikat nie ma zazwyczaj klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="ce4e5-855">Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="ce4e5-856">Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="ce4e5-857">Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-858">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-858">Parameters</span></span>

- <span data-ttu-id="ce4e5-859">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="ce4e5-860">**certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="ce4e5-861">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ce4e5-862">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-862">Return Values</span></span>

- <span data-ttu-id="ce4e5-863">**NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="ce4e5-864">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-865">**NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-866">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-866">Allowed From</span></span>

<span data-ttu-id="ce4e5-867">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-868">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-868">Example</span></span>

<span data-ttu-id="ce4e5-869">\* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-870">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-870">See Also</span></span>

- <span data-ttu-id="ce4e5-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="ce4e5-873">nx_secure_dtls_session_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="ce4e5-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="ce4e5-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ce4e5-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="ce4e5-876">Usuń zaufany certyfikat urzędu certyfikacji z sesji NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="ce4e5-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ce4e5-877">Prototype</span><span class="sxs-lookup"><span data-stu-id="ce4e5-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="ce4e5-878">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4e5-878">Description</span></span>

<span data-ttu-id="ce4e5-879">Ta usługa usuwa zaufany certyfikat urzędu certyfikacji z wystąpienia sesji DTLS przy użyciu numeru IDENTYFIKACYJNego certyfikatu (przypisanego, gdy certyfikat został dodany przy użyciu nx_secure_dtls_session_trusted_certificate_add) lub pola X. 509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="ce4e5-880">Jeśli common_name jest używany do dopasowania certyfikatu, parametr cert_id powinien mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="ce4e5-881">Jeśli jest używana cert_id, common_name powinna zostać przeniesiona wartość NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="ce4e5-882">Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="ce4e5-883">Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="ce4e5-884">Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ce4e5-885">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4e5-885">Parameters</span></span>

- <span data-ttu-id="ce4e5-886">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="ce4e5-887">**common_name** Wskaźnik do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="ce4e5-888">**common_name_length** Długość ciągu common_name.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="ce4e5-889">**Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="ce4e5-890">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="ce4e5-890">Return Values</span></span>

- <span data-ttu-id="ce4e5-891">**NX_SUCCESS** (0X00) pomyślne usunięcie certyfikatu z sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="ce4e5-892">**NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="ce4e5-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danej sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="ce4e5-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ce4e5-894">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="ce4e5-894">Allowed From</span></span>

<span data-ttu-id="ce4e5-895">Wątki</span><span class="sxs-lookup"><span data-stu-id="ce4e5-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ce4e5-896">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce4e5-896">Example</span></span>

<span data-ttu-id="ce4e5-897">\* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .</span><span class="sxs-lookup"><span data-stu-id="ce4e5-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="ce4e5-898">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce4e5-898">See Also</span></span>

- <span data-ttu-id="ce4e5-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="ce4e5-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="ce4e5-901">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="ce4e5-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="ce4e5-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ce4e5-902">nx_secure_x509_certificate_initialize</span></span>
