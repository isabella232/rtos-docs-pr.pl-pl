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
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Rozdział 4: Opis usługi Azure RTO NetX Secure DTLS Services

Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Secure DTLS Services (wymienionych poniżej) w porządku alfabetycznym.

W sekcji "wartości zwracane" w poniższych opisach interfejsu API wartości **pogrubione** nie mają wpływ na to, **NX_SECURE_DISABLE_ERROR_CHECKING** makro, które jest używane do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_ session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

Rozpocznij sesję klienta NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję klienta DTLS, łącząc się z serwerem pod podanym adresem IP i portem UDP przy użyciu dostarczonego gniazda UDP do komunikacji sieciowej.

Przed wywołaniem tej usługi przy użyciu nx_secure_dtls_session_create należy zainicjować blok sterowania sesją DTLS. Ponadto klient DTLS wymaga, aby co najmniej jeden zaufany certyfikat urzędu certyfikacji został dodany do sesji przy użyciu nx_secure_dtls_session_trusted_certificate_add lub klucze wstępne są włączone i skonfigurowane.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.
- **udp_socket** Zainicjowane gniazdo UDP, które zostanie użyte do ustanowienia komunikacji sieciowej z serwerem zdalnym DTLS.
- **IP_address** Wskaźnik na strukturę adresów IP zawierający adres zdalnego serwera DTLS.
- **port** Zainicjowane gniazdo UDP, które zostanie użyte do ustanowienia komunikacji sieciowej z serwerem zdalnym DTLS.
- **WAIT_OPTION** Opcja zawieszenia dla próby połączenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne przypisanie certyfikatu do sesji.
- **NX_NOT_CONNECTED** (0x38) serwer nie może nawiązać połączenia z podanym adresem i portem.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) otrzymany typ komunikatu TLS/DTLS jest niepoprawny.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.
- Przetwarzanie komunikatu **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) podczas UZGADNIANIA protokołu TLS nie powiodło się.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) komunikat przychodzący nie powiódł się podczas sprawdzania skrótu Mac.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie można wysłać podstawowego gniazda TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) komunikat przychodzący miał nieprawidłową długość pola.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) odebrana wiadomość ChangeCipherSpec jest niepoprawna.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) przychodzący certyfikat TLS nie nadaje się do identyfikacji zdalnego serwera DTLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) szyfrowanie klucza publicznego dostarczone przez hosta zdalnego nie jest obsługiwane.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) host zdalny nie wskazywał ciphersuites, które są obsługiwane przez stos NetX Secure DTLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrany komunikat DTLS miał nieznaną wersję DTLS w nagłówku.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) odebrany komunikat DTLS miał znaną, ale nieobsługiwaną wersję DTLS w jej nagłówku.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się wewnętrzna alokacja pakietu TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny dostarczył nieprawidłowy certyfikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) wpis w tabeli ciphersuite ma wskaźnik funkcji o wartości null.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja, gniazdo lub wskaźnik adresu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_session_receive, nx_secure_dtls_session_send,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

Przydziel pakiet dla sesji NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Opis

Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji DTLS z określonego NX_PACKET_POOL. Ta usługa powinna być wywoływana przez aplikację w celu przydzielenia pakietów danych wysyłanych przez połączenie DTLS. Sesja DTLS musi zostać zainicjowana przed wywołaniem tej usługi.

Przydzielony pakiet jest prawidłowo zainicjowany, aby można było dodać dane nagłówka i stopki DTLS po wypełnieniu danych pakietu. Zachowanie jest takie samo jak *nx_packet_allocate*.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik na wystąpienie sesji DTLS.
- **pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma zostać przydzielony pakiet.
- **packet_ptr** Wskaźnik wyjściowy do nowo przydzielonych pakietów.
- **WAIT_OPTION** Opcja zawieszenia dla przydziału pakietu.


### <a name="return-values"></a>Wartości zwrócone

- Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).
- Alokacja podstawowego pakietu **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja DTLS nie została zainicjowana.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_session_send, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_end, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

Dodaj klucz wstępny do sesji NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku sterowania sesją DTLS. PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.
- **pre_shared_key** Rzeczywista wartość klucza PSK.
- **psk_length** Długość wartości klucza PSK.
- **psk_identity** Ciąg służący do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości PSK.
- **Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

Tworzenie serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera DTLS do obsługi przychodzących żądań DTLS na określonym porcie UDP. Ze względu na fakt, że protokół UDP jest bezstanowy, żądania DTLS z wielu klientów mogą znajdować się na jednym porcie, podczas gdy inne sesje DTLS są aktywne. Z tego względu serwer jest wymagany do obsługi aktywnych sesji i prawidłowo kieruje komunikaty przychodzące do odpowiedniej procedury obsługi.

Parametr ip_ptr wskazuje wystąpienie NX_IP, które ma być używane dla wewnętrznego gniazda UDP skojarzonego z serwerem DTLS (i przechowywane w bloku kontroli NX_SECURE_DTLS_SERVER). Wystąpienie i port IP są używane do definiowania interfejsu UDP, na którym serwer jest skonkretyzowany jako usługa nx_secure_dtls_server_start.

Parametr buforu sesji służy do przechowywania bloków sterowania dla wszystkich możliwych równoczesnych sesji DTLS dla serwera DTLS. Powinna być przypisana o rozmiarze, który jest parzystą wielokrotnością rozmiaru struktury bloku sterowania NX_SECURE_DTLS_SESSION.

Aby obliczyć wymagany rozmiar metadanych, można użyć interfejsu API nx_secure_tls_metadata_size_calculate.

Parametr packet_reassembly_buffer jest używany przez DTLS do ponownego łączenia datagramy UDP do kompletnego rekordu DTLS do celów odszyfrowywania i powinien być wystarczająco duży, aby pomieścić największy oczekiwany rekord DTLS (16 KB to DTLS maksymalny rozmiar rekordu, ale wiele aplikacji nie wysyła takich danych w jednym rekordzie).

Procedura wywołania zwrotnego connect_notify jest wywoływana za każdym razem, gdy nowy klient DTLS nawiązuje połączenie z serwerem. Do aplikacji można uruchomić sesję DTLS przy użyciu usługi *nx_secure_dtls_server_session_start*. Sesja może być uruchomiona w wywołaniu zwrotnym, dlatego zaleca się użycie wywołania zwrotnego tylko do powiadomienia wątku aplikacji (lub dedykowanego wątku DTLS utworzonego przez aplikację) połączenia, ponieważ wywołanie zwrotne jest wywoływane przez wątek IP, który jest używany do przetwarzania wszystkich procesów niskiego poziomu w sieci (np. UDP). Może to być bardzo proste jako zapisanie parametru sesji DTLS (dostarczonego jako parametr wywołania zwrotnego) i wywołanie nx_secure_dtls_server_session_start w innym wątku. Wywołanie zwrotne connect_notify powinno zazwyczaj zwracać NX_SUCCESS.

Procedura wywołania zwrotnego receive_notify jest wywoływana za każdym razem, gdy zostanie odebrany rekord DTLS zgodny z istniejącą ustanowioną sesją DTLS (zdalny adres IP hosta i port są używane do identyfikacji istniejącej sesji). Reprezentuje to "dane aplikacji", które są szyfrowane i wysyłane za pośrednictwem DTLS. Aplikacja musi wywoływać *nx_secure_dtls_session_receive* usługi na podanej sesji DTLS, aby pobrać odebrane dane. Podobnie jak w przypadku wywołania zwrotnego connect_receive, zaleca się, aby sesja była przenoszona do innego wątku, aby obsługiwała przetwarzanie komunikatów, gdy wywołanie zwrotne jest wywoływane z wątku IP. Wywołanie zwrotne receive_notify powinno zazwyczaj zwracać NX_SUCCESS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **ip_ptr** Wskaźnik do zainicjowanego bloku sterowania NX_IP, który ma być używany jako interfejs sieciowy serwera DTLS.
- **port** Lokalny port UDP, z którym jest powiązana gniazdo UDP serwera DTLS.
- **limit czasu** Wartość limitu czasu używana dla operacji sieciowych.
- **session_buffer** Miejsce w buforze zawierające bloki kontroli dla wszystkich wystąpień NX_SECURE_DTLS_SESSION przypisanych do tego wystąpienia serwera DTLS.
- **session_buffer_size** Rozmiar buforu sesji. Określa liczbę sesji DTLS przypisanych do serwera DTLS.
- **crypto_table** Wskaźnik do struktury tabeli szyfrowania TLS/DTLS używanej do wszystkich operacji kryptograficznych.
- **crypto_metadata_buffer** Miejsce w buforze dla obliczeń operacji kryptograficznych i informacji o stanie.
- **crypto_metadata_size** Rozmiar buforu metadanych.
- **packet_reassembly_buffer** Bufor używany przez DTLS do ponownego składania danych UDP do rekordów DTLS w celu odszyfrowania.
- **packet_reassembly_buffer_size** Rozmiar buforu ponownego zestawu. Ogólnie powinna być większa niż 16 KB, ale może być mniejsza w zależności od aplikacji.
- **connect_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy zdalny klient DTLS próbuje nawiązać połączenie z tym serwerem DTLS.
- **receive_notify** Wywołanie zwrotne wywoływane za każdym razem, gdy dane aplikacji są odbierane przez istniejącą sesję DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się utworzenie serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) za mało miejsca w buforze dla sesji, ponownego asemblowania pakietu lub kryptografii.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

Zwalnianie zasobów używanych przez serwer NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia zasoby przydzielone do wystąpienia serwera DTLS, w tym wewnętrzne gniazdo UDP używane przez serwer.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunięto serwer.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- Gniazdo UDP **NX_STILL_BOUND** (0x42) jest nadal powiązane.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

Dodawanie certyfikatu tożsamości serwera lokalnego do serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje certyfikat tożsamości serwera lokalnego do wystąpienia serwera DTLS. Do łączenia się z serwerem DTLS jest wymagany co najmniej jeden certyfikat tożsamości, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 znajdującą się w magazynie serwera DTLS. Więcej informacji na temat certyfikatów serwera X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_server_create* .

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

Usuwanie certyfikatu tożsamości serwera lokalnego z serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa certyfikat tożsamości serwera lokalnego z wystąpienia serwera DTLS. Do łączenia się z serwerem DTLS jest wymagany co najmniej jeden certyfikat tożsamości, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).

Certyfikat, który ma zostać usunięty, może być identyfikowany przez jego nazwę pospolitą X. 509 lub numeryczną cert_id, która została przypisana w wywołaniu *nx_secure_dtls_server_local_certificate_add*. Cert_id służy tylko do identyfikowania certyfikatu i jest obsługiwany przez aplikację. Jeśli nazwa pospolita jest używana zamiast numerycznego identyfikatora certyfikatu, parametr cert_id powinien mieć wartość 0.

> [!NOTE]
> Usunięcie certyfikatu podczas przetwarzania uzgadniania DTLS spowoduje nieoczekiwane zachowanie. Przed usunięciem certyfikatów należy wywołać *nx_secure_dtls_server_stop* usługi.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **common_name** Wartość Wspólnaname certyfikatu X. 509 do usunięcia. Jeśli jest używany, Przekaż cert_id jako zero.
- **common_name_length** Długość ciągu common_name w bajtach.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS. Jeśli jest używany, Przekaż NX_NULL dla parametru common_name.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się usunięcie certyfikatu z serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danym serwerze DTLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

Przypisywanie opcjonalnych procedur wywołania zwrotnego powiadomień do serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>Opis

Ta usługa może służyć do dodawania opcjonalnych procedur wywołania zwrotnego powiadomień do serwera DTLS. Parametr wywołania zwrotnego można przesłać jako NX_NULL, jeśli pożądane jest tylko jedno wywołanie zwrotne.

Wywołanie zwrotne disconnect_notify jest wywoływane, gdy Klient zdalny skończy sesję DTLS. Parametr dtls_session to wystąpienie sesji, które zostało zamknięte. Wywołanie zwrotne powinno zwykle zwracać NX_SUCCESS.

Wywołanie zwrotne error_notify jest wywoływane za każdym razem, gdy wystąpi błąd DTLS lub limit czasu. Dtls_session parametr jest wystąpieniem sesji, dla którego wystąpił błąd, a error_code to liczbowy kod stanu dla błędu, który spowodował problem (patrz dodatek A)

NetX bezpieczne kody powrotu/błędów dla listy kodów błędów, które mogą zostać zwrócone). Wywołanie zwrotne powinno zwykle zwracać NX_SUCCESS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **disconnect_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy zdalny host klienta zamknie sesję DTLS.
- **error_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy DTLS napotka błąd lub przekroczenie limitu czasu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne przypisanie procedur wywołania zwrotnego.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

Dodaj klucz wstępny do serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku sterowania serwerem DTLS. PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.

Dodany PSK jest replikowany na wszystkich sesjach DTLS przypisanych do serwera DTLS (za pośrednictwem buforu sesji podanego w wywołaniu nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **pre_shared_key** Rzeczywista wartość klucza PSK.
- **psk_length** Długość wartości klucza PSK.
- **psk_identity** Ciąg służący do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości PSK.
- **Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik serwera DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_psk_add, nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

Wysyłanie danych za pośrednictwem sesji DTLS z serwerem NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet danych przez ustanowioną sesję serwera DTLS do zdalnego hosta klienta DTLS. Używana sesja jest uzyskiwana w procedurze wywołania zwrotnego receive_notify dostarczonej do nx_secure_dtls_session_create.

Dane podane w pakiecie, które muszą zostać przydzieloną przy użyciu *nx_secure_dtls_packet_allocate*, są szyfrowane przy użyciu parametrów i procedur kryptograficznych sesji DTLS, a następnie wysyłane do hosta zdalnego przez wewnętrzny port UDP serwera DTLS do adresu IP i portu dołączonego klienta (przechowywanego w sesji DTLS).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji DTLS uzyskany z procedury wywołania zwrotnego receive_notify dostarczonej przez aplikację.
- **packet_ptr** Wskaźnik do wystąpienia NX_PACKET przydzielono wcześniej i uzupełniony o dane aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się utworzenie serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) wystąpił błąd w podstawowej operacji wysyłania protokołu UDP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,
- nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

Uruchamianie sesji DTLS z serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję serwera DTLS, wykonując uzgodnienie DTLS po stronie serwera, gdy zdalny klient DTLS nawiązał połączenie z serwerem i zażądał połączenia DTLS.

Sesja DTLS jest uzyskiwana w procedurze wywołania zwrotnego connect_notify dostarczonej do nx_secure_dtls_server_create.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji DTLS uzyskanego z serwera DTLS connect_notify wywołanie zwrotne.
- **WAIT_OPTION** Wartość ThreadX oczekiwania na użycie dla operacji sieciowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się utworzenie serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie może przydzielić pakietu uzgadniania DTLS (Pula pakietów jest pusta).
- **NX_SECURE_TLS_INVALID_PACKET** (0X104) odebrano dane, które nie były prawidłowym rekordem DTLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) nie można prawidłowo wykonać mieszania DTLS rekordu (błąd szyfrowania).
- Niepowodzenie sprawdzania uzupełniania szyfrowania **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A).
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) odebrano alert z hosta zdalnego podczas uzgadniania DTLS.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) otrzymał nierozpoznany komunikat podczas uzgadniania DTLS.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) odebrano rekord DTLS o nieprawidłowej długości.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) otrzymał komunikacie ClientHello bez obsługiwanego DTLS ciphersuites.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118) odebrano komunikacie ClientHello za pomocą nieznanej metody kompresji.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0X107) ogólny błąd uzgadniania (nieokreślony), zwykle z powodu problemów z przetwarzaniem rozszerzenia.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) funkcja, która nie jest jeszcze obsługiwana, została wywołana podczas uzgadniania DTLS.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) napotkano nieznany CIPHERSUITE (wskazano wewnętrzny błąd kryptografii).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) odebrano rekord DTLS z niezgodną wersją DTLS.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115) nie może zweryfikować skrótu uzgadniania DTLS, sesja jest nieprawidłowa.
- Nie powiodło się wysyłanie wewnętrznego protokołu UDP **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

Uruchom wystąpienie serwera NetX bezpiecznego DTLS nasłuchiwanie na skonfigurowanym porcie UDP

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Opis

Ta usługa uruchamia serwer DTLS. Po powrocie wywołania serwer jest aktywny i rozpocznie przetwarzanie przychodzących żądań od klientów DTLS. Wystąpienie serwera musi być skonfigurowane z *nx_secure_dtls_server_create* usługi.

> [!NOTE]
> Ta usługa wiąże wewnętrzny port UDP serwera DTLS ze skonfigurowanym portem lokalnym, w związku z czym wystąpi większość napotkanych problemów z konfiguracją komunikacji przy użyciu protokołu UDP i sieci.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie uruchomiono serwer.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- Nie włączono protokołu UDP **NX_NOT_ENABLED** (0x14).
- **NX_NO_FREE_PORTS** (0X45) Brak dostępnych portów UDP.
- **NX_INVALID_PORT** (0X46) nieprawidłowy port UDP.
- Port UDP **NX_ALREADY_BOUND** (0x22) jest już powiązany.
- Nie można używać portu UDP **NX_PORT_UNAVAILABLE** (0x23).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_stop, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

Zatrzymaj aktywne wystąpienie serwera usługi NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje serwer DTLS przed nasłuchiwaniem na porcie UDP i resetuje wszystkie skojarzone sesje DTLS, przerywając wszelką komunikację DTLS w toku.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik na aktywne wystąpienie serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie zatrzymano serwer **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

Dodawanie certyfikatu zaufanego urzędu certyfikacji do serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje Certyfikat zaufanego urzędu certyfikacji lub pośredniego urzędu certyfikacji do wystąpienia serwera DTLS i jest przypisany do wszystkich wewnętrznych sesji serwera DTLS. Jest to konieczne tylko wtedy, gdy uwierzytelnianie certyfikatu klienta X. 509 jest włączone przy użyciu *nx_secure_dtls_server_x509_client_verify_configure*. Dodany certyfikat będzie używany do weryfikowania przychodzących certyfikatów klienta X. 509.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 znajdującą się w magazynie serwera DTLS. Więcej informacji na temat certyfikatów serwera X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_server_create* .

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_server_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

Usuwanie certyfikatu zaufanego urzędu certyfikacji z serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa Certyfikat zaufanego urzędu certyfikacji z wystąpienia serwera DTLS. Certyfikaty zaufanych urzędów certyfikacji są niezbędne tylko dla serwera DTLS, dla którego weryfikacja certyfikatu klienta X. 509 została włączona przez wywołanie *nx_secure_dtls_server_x509_client_verify_configure*.

Certyfikat, który ma zostać usunięty, może być identyfikowany przez jego nazwę pospolitą X. 509 lub numeryczną cert_id, która została przypisana w wywołaniu *nx_secure_dtls_server_trusted_certificate_add*. Cert_id służy tylko do identyfikowania certyfikatu i jest obsługiwany przez aplikację. Jeśli nazwa pospolita jest używana zamiast numerycznego identyfikatora certyfikatu, parametr cert_id powinien mieć wartość 0.

> [!NOTE]
> Usuwanie certyfikatu podczas przetwarzania uzgadniania DTLS może spowodować nieoczekiwane zachowanie. Przed usunięciem certyfikatów należy wywołać *nx_secure_dtls_server_stop* usługi.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **common_name** Wartość Wspólnaname certyfikatu X. 509 do usunięcia. Jeśli jest używany, Przekaż cert_id jako zero.
- **common_name_length** Długość ciągu common_name w bajtach.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS. Jeśli jest używany, Przekaż NX_NULL dla parametru common_name.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się usunięcie certyfikatu z serwera DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danym serwerze DTLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

Konfigurowanie serwera NetX Secure DTLS do żądania i weryfikowania certyfikatów klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Opis

Ta usługa służy do konfigurowania serwera DTLS do żądania i weryfikowania certyfikatów klienta DTLS. Ta funkcja opcjonalna jest używana, gdy certyfikaty X. 509 są wymagane do uwierzytelnienia klienta zamiast innych mechanizmów (np. klucza wstępnego).

> [!IMPORTANT]
> *Gdy serwer DTLS jest skonfigurowany do weryfikowania certyfikatów klienta przy użyciu tej usługi, należy dodać co najmniej jeden zaufany certyfikat urzędu certyfikacji do serwera przy użyciu nx_secure_dtls_server_trusted_certificate_add lub serwer odrzuci wszystkie przychodzące połączenia klientów, ponieważ nie będzie mógł zweryfikować certyfikatów klienta w zaufanym magazynie.*

Po wywołaniu tej usługi wystąpienie serwera DTLS będzie (po uruchomieniu) zażądać certyfikatów klienta w ramach uzgadniania DTLS. Przy założeniu, że klient zostanie prawidłowo skonfigurowany przy użyciu certyfikatu tożsamości (i powiązanego łańcucha certyfikatów, jeśli ma zastosowanie), serwer DTLS wymaga przydzielenia pamięci do przetworzenia danych certyfikatu klienta. Ta pamięć jest przenoszona jako parametr *certs_buffer* .

Certs_buffer musi mieć rozmiar w celu uwzględnienia największego oczekiwanego łańcucha certyfikatów od klienta DTLS, *ile sesji serwera DTLS*. Bufor jest dzielony między dostępnymi sesjami przy użyciu parametru *certs_per_session* , który reprezentuje maksymalną oczekiwaną liczbę certyfikatów w łańcuchu certyfikatów klienta. Bufor musi także zapewnić miejsce dla NX_SECURE_X509_CERTej struktury danych, która jest używana do analizowania danych certyfikatu.

Obliczanie odpowiedniego rozmiaru buforu można wykonać przy użyciu następującej formuły:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- Liczba sesji DTLS jest określana przez rozmiar buforu sesji przekazaną do nx_secure_dtls_server_create.
- certs_per_session powinna być ustawiona na maksymalną oczekiwaną liczbę certyfikatów w łańcuchu certyfikatów klienta.
- Maksymalny oczekiwany rozmiar certyfikatu zależy od aplikacji, rozmiarów kluczy i innych czynników, ale 2KB jest ogólnie wystarczający.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.
- **certs_per_session** Liczba certyfikatów do przydzielenia do każdej sesji serwera DTLS.
- **certs_buffer** Miejsce w buforze dla danych certyfikatu przychodzącego.
- **buffer_size** Rozmiar buforu certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślna konfiguracja weryfikacji klienta X. 509.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) nieprawidłowy magazyn certyfikatów (wystąpienie DTLSserver nie initalized?).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_x509_client_verify_disable,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

Wyłącza weryfikację certyfikatu X. 509 klienta dla serwera NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza weryfikację certyfikatu klienta X. 509 na serwerze DTLS. Usługa nie działa, Jeśli weryfikacja certyfikatu klienta X. 509 nie jest włączona.

> [!NOTE]
> Wyłączenie uwierzytelniania klienta w aktywnym wystąpieniu serwera DTLS może spowodować nieprzewidywalne zachowanie. Przed zmianą stanu serwera należy wywołać usługę nx_secure_dtls_server_stop.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wyłączenie uwierzytelniania klienta X. 509.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_x509_client_verify_configure,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

Pobierz informacje o kliencie zdalnym z sesji serwera DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Opis

Ta usługa zwraca informacje o sieci dotyczące klienta DTLS, który jest połączony z określoną sesją serwera DTLS. Zwracane informacje składają się z adresu IP i portu protokołu UDP klienta zdalnego, a także portu serwera lokalnego, z którym jest połączony klient.

Ogólnie rzecz biorąc, wystąpienie sesji DTLS będzie to ten, który uzyskano w wywołaniu jednej z procedur wywołania zwrotnego powiadomień DTLS (np. wywołania zwrotne connect_notify lub receive_notify przekazywane do nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik na aktywne wystąpienie sesji serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunięto serwer.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_SOCKET** (0x13) SKOJARZONE gniazdo UDP jest nieprawidłowe (sesja nie została zainicjowana?).
- Gniazdo UDP **NX_NOT_CONNECTED** (0x38) nie jest połączone — połączenie klienta zostało usunięte lub jeszcze nie zostało nawiązane.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_server_start, nx_secure_dtls_server_stop,
- nx_secure_dtls_server_create, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

Tworzenie i Konfigurowanie sesji NetX Secure DTLS

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta usługa tworzy i konfiguruje sesję DTLS. Ogólnie rzecz biorąc, ta metoda zostanie użyta do utworzenia sesji klienta DTLS jako sesji serwera DTLS, które są zarządzane za pomocą mechanizmu serwera DTLS (zobacz *nx_secure_dtls_server_create*), ale mogą istnieć wystąpienia, w których aplikacja musi utworzyć jedno autonomiczne wystąpienie sesji serwera DTLS, w którym ta usługa może być używana <sup>7</sup>.

Parametry konfigurują alokację informacji i pamięci wymaganą do utworzenia wystąpienia sesji DTLS. Crypto_table parametr jest tabelą protokołu TLS zawierającą wszystkie procedury kryptograficzne, które są zbędne do szyfrowania i uwierzytelniania TLS/DTLS. Metadata_buffer jest używany do szyfrowania caclulations (patrz nx_secure_tls_metadata_size_calculate w podręczniku użytkownika NetX Secure TLS), a packet_reassembly_buffer służy do ponownego łączenia datagramów UDP z kompletnym rekordem DTLS w celu odszyfrowania.

Certs_number i remote_certificate_buffer są wymagane dla klientów DTLS, którzy muszą mieć miejsce do przechowywania i przetwarzania przychodzącego łańcucha certyfikatów serwera DTLS. Bufor musi być w stanie obsłużyć maksymalny oczekiwany rozmiar łańcucha certyfikatów dla każdego serwera, z którym zostanie nawiązane połączenie. Bufor jest dzielony przez liczbę oczekiwanych certyfikatów (certs_number parametr) i musi być wystarczająco duży, aby pomieścić jedną strukturę NX_SECURE_X509_CERT dla każdego certyfikatu. Rozmiar buforu można określić przy użyciu następującej formuły:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number to oczekiwana Maksymalna liczba certyfikatów w łańcuchu certyfikatów serwera
- Maksymalny rozmiar certyfikatu zależy od rozmiaru używanych kluczy i informacji w certyfikacie, ale 2KB jest ogólnie wystarczający.

**7** Tworzenie sesji serwera DTLS z tą procedurą nie jest zalecane i zawiera pewne ograniczenia. Podstawowym problemem jest to, że sesja nie będzie obsługiwać dodatkowych połączeń z klientami — ponieważ protokół UDP jest bezczynny, drugi klient może legalnie wysyłać dane do portu UDP serwera, gdy Poprzednia sesja DTLS nadal jest aktywna, co spowodowałoby zakończenie sesji serwera z powodu błędu.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik na niezainicjowaną strukturę sesji DTLS.
- **crypto_table** Wskaźnik do struktury tabeli szyfrowania TLS/DTLS używanej do wszystkich operacji kryptograficznych.
- **crypto_metadata_buffer** Miejsce w buforze dla obliczeń operacji kryptograficznych i informacji o stanie.
- **crypto_metadata_size** Rozmiar buforu metadanych.
- **packet_reassembly_buffer** Bufor używany przez DTLS do ponownego składania danych UDP do rekordów DTLS w celu odszyfrowania.
- **packet_reassembly_buffer_size** Rozmiar buforu ponownego zestawu. Ogólnie powinna być większa niż 16 KB, ale może być mniejsza w zależności od aplikacji.
- **certs_number** Maksymalna oczekiwana liczba certyfikatów w łańcuchu certyfikatów serwera zdalnego.
- **remote_certificate_buffer** Miejsce w buforze dla danych certyfikatu przychodzącego.
- **remote_certificate_buffer_size** Rozmiar buforu certyfikatu.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie utworzono sesję.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.
- **NX_INVALID_PARAMETERS** (0x4D) za mało miejsca w buforze na potrzeby ponownego asemblowania pakietów, certyfikatów lub kryptografii.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

Zwalnianie zasobów używanych przez sesję NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Opis

Ta usługa usuwa sesję DTLS i zwalnia wszystkie zasoby, które zostały przydzieloną podczas tworzenia.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunięto sesję.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Zamykanie aktywnej sesji usługi NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa służy do kończenia aktywnej sesji DTLS przez wysłanie alertu CloseNotify TLS/DTLS do hosta zdalnego. Używanym adresem IP i portem są te, które są używane w poprzednim wywołaniu do nx_secure_dtls_session_send.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.
- **WAIT_OPTION** Wartość ThreadX oczekiwania na użycie dla operacji sieciowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunięto sesję.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie może przydzielić pakietów dla alertu CloseNotify.
- Wystąpił błąd wewnętrzny **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) — nie rozpoznano procedury kryptograficznej.
- Nie można wysłać podstawowego protokołu UDP **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109).
- **NX_IP_ADDRESS_ERROR** (0X21) błąd z adresem IP hosta zdalnego.
- **NX_NOT_BOUND** (0X24) bazowego gniazda UDP nie jest powiązany z portem.
- **NX_INVALID_PORT** (0X46) nieprawidłowy port UDP.
- Nie można używać portu UDP **NX_PORT_UNAVAILABLE** (0x23).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

Dodawanie certyfikatu tożsamości lokalnej do sesji NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje certyfikat tożsamości lokalnej do wystąpienia sesji DTLS. Ogólnie rzecz biorąc, ta usługa zostanie użyta, gdy sesja klienta DTLS musi dostarczyć certyfikat tożsamości do hosta serwera zdalnego. Jest to opcjonalna konfiguracja dla programu DTLS, dzięki czemu certyfikat nie jest zazwyczaj wymagany dla klientów DTLS. Certyfikat tożsamości wymaga skojarzonego z nim klucza prywatnego.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS. Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do sesji DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

Usuń certyfikat tożsamości lokalnej z sesji usługi NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa certyfikat tożsamości lokalnej z wystąpienia sesji DTLS przy użyciu numeru identyfikatora certyfikatu (przypisanego, gdy certyfikat został dodany przy użyciu nx_secure_dtls_session_local_certificate_add) lub pola X. 509 CommonName.

Jeśli common_name jest używany do dopasowania certyfikatu, parametr cert_id powinien mieć wartość 0. Jeśli jest używana cert_id, common_name powinna zostać przeniesiona wartość NX_NULL.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS. Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.
- **common_name** Wskaźnik do dopasowania.
- **common_name_length** Długość ciągu common_name.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie certyfikatu z sesji DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danej sesji DTLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

Odbieraj dane aplikacji przez ustanowioną sesję NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa zwraca dane aplikacji odebrane przez aktywną sesję DTLS. Sesja DTLS może być sesją serwera DTLS (zarządzaną przez wystąpienie serwera DTLS) lub sesją klienta DTLS. Zwrócony pakiet może być przetwarzany przy użyciu dowolnych usług NX_PACKET API (więcej informacji znajduje się w dokumentacji NetX).

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.
- **packet_ptr_ptr** Wskaźnik do NX_PACKETego wskaźnika dla pakietu zwrotnego.
- **WAIT_OPTION** Wartość ThreadX oczekiwania na użycie dla operacji sieciowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne otrzymanie pakietu danych aplikacji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji lub pakietu.
- **NX_NOT_ENABLED** (0X14) UDP nie jest włączony.
- Gniazdo UDP **NX_NOT_BOUND** (0x24) nie jest powiązane z portem.
- **NX_SECURE_TLS_INVALID_PACKET** (0X104) odebrano dane, które nie były prawidłowym rekordem DTLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) nie można prawidłowo wykonać mieszania DTLS rekordu (błąd szyfrowania).
- Niepowodzenie sprawdzania uzupełniania szyfrowania **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A).
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) odebrano alert z hosta zdalnego.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0X102) otrzymał nierozpoznany komunikat.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) odebrano rekord DTLS o nieprawidłowej długości.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) napotkano nieznany CIPHERSUITE (wskazuje wewnętrzny błąd kryptografii).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) odebrano rekord DTLS z niezgodną wersją DTLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

Wyczyść dane w NetX bezpieczne wystąpienie sesji DTLS

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Opis

Ta usługa resetuje sesję DTLS, czyszcząc wszystkie tymczasowe dane kryptograficzne i umożliwiając ponowne użycie struktury dla nowej sesji. Trwałe dane (np. magazyny certyfikatów) są utrzymywane w taki sposób, aby nx_secure_dtls_session_create nie wymagały wielokrotnego wywoływania.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zresetował sesję.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja lub wskaźnik buforu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

Wysyłanie danych za pośrednictwem sesji DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet danych przez ustanowioną sesję DTLS do zdalnego hosta DTLS pod danym adresem IP i porcie. Używana sesja to aktywna sesja klienta usługi DTLS. Należy pamiętać, że adres IP i port są dostarczane z powodu bezstanowego charakteru protokołu UDP, ale zazwyczaj powinny być zgodne z adresem i portem używanym do uruchomienia sesji w nx_secure_dtls_session_start.

Dane podane w pakiecie, które muszą zostać przydzieloną przy użyciu *nx_secure_dtls_packet_allocate*, są szyfrowane przy użyciu parametrów i procedur kryptograficznych sesji DTLS, a następnie wysyłane do hosta zdalnego przez gniazdo UDP sesji DTLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik na aktywne wystąpienie sesji klienta DTLS.
- **packet_ptr** Wskaźnik do wystąpienia NX_PACKET przydzielono wcześniej i uzupełniony o dane aplikacji.
- **IP_address** Wskaźnik do struktury NXD_ADDRESS zawierającej adres IP hosta zdalnego.
- **port** Port UDP na hoście zdalnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego wysłania pakietu.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) wystąpił błąd w podstawowej operacji wysyłania protokołu UDP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

Dodawanie certyfikatu zaufanego urzędu certyfikacji do sesji NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje zaufany urząd certyfikacji lub pośredni certyfikat X. 509 urzędu certyfikacji do wystąpienia sesji DTLS. Klient DTLS wymaga co najmniej jednego zaufanego certyfikatu w celu weryfikacji certyfikatów serwera zdalnego, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne). Zaufany certyfikat nie ma zazwyczaj klucza prywatnego.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS. Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X. 509.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie dokończył Dodawanie certyfikatu do sesji DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) identyfikator certyfikatu 0 został przekazano.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

Usuń zaufany certyfikat urzędu certyfikacji z sesji NetX Secure DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa zaufany certyfikat urzędu certyfikacji z wystąpienia sesji DTLS przy użyciu numeru IDENTYFIKACYJNego certyfikatu (przypisanego, gdy certyfikat został dodany przy użyciu nx_secure_dtls_session_trusted_certificate_add) lub pola X. 509 CommonName.

Jeśli common_name jest używany do dopasowania certyfikatu, parametr cert_id powinien mieć wartość 0. Jeśli jest używana cert_id, common_name powinna zostać przeniesiona wartość NX_NULL.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w zdarzeniu, w którym istnieje wiele certyfikatów tożsamości z tą samą nazwą pospolitą X. 509 w magazynie certyfikatów DTLS. Więcej informacji na temat certyfikatów X. 509 można znaleźć w podręczniku użytkownika usługi NetX Secure TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji DTLS.
- **common_name** Wskaźnik do dopasowania.
- **common_name_length** Długość ciągu common_name.
- **Cert_ID** Unikatowy identyfikator o wartości innej niż zero dla tego certyfikatu na tym serwerze DTLS.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie certyfikatu z sesji DTLS.
- **NX_PTR_ERROR** (0x07) przeszedł nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) brak certyfikatu pasującego do cert_id lub common_name znaleziono w danej sesji DTLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

* Szczegółowe informacje można znaleźć w temacie *nx_secure_dtls_session_create* .

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

### <a name="see-also"></a>Zobacz też

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_x509_certificate_initialize
