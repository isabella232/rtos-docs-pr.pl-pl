---
title: Rozdział 4 — Opis Azure RTOS NetX Secure DTLS
description: Ten rozdział zawiera opis wszystkich usług bezpiecznego Azure RTOS DTLS NetX wymienionych w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45966e7c8ea9be18bf294e8a7540e7226e803f29ae4f3ad3faaa29e4939c2ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801850"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Rozdział 4. Opis bezpiecznego Azure RTOS DTLS NetX

Ten rozdział zawiera opis wszystkich usług Secure DTLS Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API makro NX_SECURE_DISABLE_ERROR_CHECKING używane do wyłączania sprawdzania błędów interfejsu API nie ma wpływu na wartości z pogrubieniem, **natomiast** wartości bez pogrubienia są całkowicie wyłączone.

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

Uruchamianie sesji klienta bezpiecznego dtls netx

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję klienta USŁUGI DTLS, łącząc się z serwerem pod dostarczonym adresem IP i portem UDP przy użyciu dostarczonego gniazda UDP do komunikacji sieciowej.

Blok kontroli sesji DTLS musi zostać zainicjowany przed wywołaniem tej usługi przy użyciu nx_secure_dtls_session_create. Ponadto klient DTLS wymaga, aby co najmniej jeden certyfikat zaufanego urzędu certyfikacji został dodany do sesji przy użyciu nx_secure_dtls_session_trusted_certificate_add lub kluczy wstępnych zostały włączone i skonfigurowane.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.
- **udp_socket** Zainicjowano gniazdo UDP, które będzie używane do nawiązywania komunikacji sieciowej ze zdalnym serwerem DTLS.
- **ip_address** Wskaźnik do struktury adresów IP zawierającej adres zdalnego serwera DTLS.
- **port** Zainicjowano gniazdo UDP, które będzie używane do nawiązywania komunikacji sieciowej ze zdalnym serwerem DTLS.
- **wait_option** Opcja zawieszenia dla próby połączenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przypisanie certyfikatu do sesji.
- **NX_NOT_CONNECTED** (0x38) Nie można uzyskać dostępu do serwera pod danym adresem i portem.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Odebrany typ komunikatu TLS/DTLS jest niepoprawny.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Przetwarzanie komunikatów podczas uściśniania TLS nie powiodło się.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Komunikat przychodzący nie może sprawdzić skrótu MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Nie można wysłać bazowego gniazda TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Komunikat przychodzący miał pole o nieprawidłowej długości.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Przychodzący komunikat ChangeCipherSpec był niepoprawny.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Przychodzący certyfikat TLS nie można zidentyfikować zdalnego serwera DTLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Szyfr klucza publicznego dostarczony przez hosta zdalnego nie jest obsługiwany.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Host zdalny nie zaznaczył żadnych szyfrów, które są obsługiwane przez stos SECURE DTLS NetX.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat DTLS miał w nagłówku nieznaną wersję usługi DTLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Odebrany komunikat DTLS miał w nagłówku znaną, ale nieobsługiwaną wersję usługi DTLS.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Wewnętrzna alokacja pakietów TLS nie powiodła się.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny podał nieprawidłowy certyfikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Wpis w tabeli ciphersuite miał wskaźnik funkcji NULL.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji, gniazda lub adresu.

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

Przydzielanie pakietu dla bezpiecznej sesji DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Opis

Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji DTLS z określonego NX_PACKET_POOL. Ta usługa powinna być wywoływana przez aplikację w celu przydzielenia pakietów danych do wysłania za pośrednictwem połączenia DTLS. Sesja DTLS musi zostać zainicjowana przed wywołaniem tej usługi.

Przydzielony pakiet jest prawidłowo zainicjowany, aby można było dodać dane nagłówka i stopki DTLS po wypełnieniu danych pakietu. W przeciwnym razie zachowanie jest identyczne *nx_packet_allocate*.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji USŁUGI DTLS.
- **pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma być przydzielany pakiet.
- **packet_ptr** Wskaźnik wyjściowy do nowo przydzielonego pakietu.
- **wait_option** Opcja zawieszenia alokacji pakietów.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przydzielenie pakietu.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Alokacja pakietów bazowych nie powiodła się.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Nie zainicjowano podanej sesji usługi DTLS.

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

Dodawanie klucza wstępnego do bezpiecznej sesji DTLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę tożsamości do bloku kontroli sesji USŁUGI DTLS. Jeśli są włączone i używane szyfry PSK, jest on używany w miejsce certyfikatu cyfrowego.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji USŁUGI DTLS.
- **pre_shared_key** Rzeczywista wartość PSK.
- **psk_length** Długość wartości PSK.
- **psk_identity** Ciąg używany do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości psk.
- **wskazówka** Ciąg używany do wskazywania grupy psk do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie psk.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Nie można dodać kolejnego psk.

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

Tworzenie bezpiecznego serwera DTLS NetX

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

Ta usługa tworzy wystąpienie serwera DTLS do obsługi przychodzących żądań DTLS na określonym porcie UDP. Ze względu na to, że usługa UDP jest bez stanowa, żądania DTLS od wielu klientów mogą przychodzić na jeden port, podczas gdy inne sesje dtls są aktywne. W związku z tym serwer jest potrzebny do utrzymania aktywnych sesji i prawidłowego rozsyłania komunikatów przychodzących do odpowiedniej procedury obsługi.

Parametr ip_ptr wskazuje wystąpienie NX_IP, które ma być używane dla wewnętrznego gniazda UDP skojarzonego z serwerem DTLS (i przechowywanego w bloku sterowania NX_SECURE_DTLS_SERVER). Wystąpienie adresu IP i port są używane do definiowania interfejsu UDP, na którym serwer jest wystąpieniem usługi nx_secure_dtls_server_start usługi.

Parametr buforu sesji służy do przechowywania bloków sterujących dla wszystkich możliwych równoczesnych sesji DTLS dla serwera DTLS. Należy ją przydzielić z rozmiarem, który jest nawet wielokrotnością rozmiaru NX_SECURE_DTLS_SESSION bloku sterowania.

Aby obliczyć niezbędny rozmiar metadanych, można użyć nx_secure_tls_metadata_size_calculate API.

Parametr packet_reassembly_buffer jest używany przez dtls do ponownego zbierania datagramów UDP w kompletny rekord DTLS na potrzeby odszyfrowywania i powinien być wystarczająco duży, aby pomieścić największy oczekiwany rekord DTLS (16 KB to maksymalny rozmiar rekordu DTLS, ale wiele aplikacji nie wysyła tak dużej ilości danych w jednym rekordzie).

Procedura connect_notify wywołania zwrotnego jest wywoływana za każdym razem, gdy nowy klient DTLS łączy się z serwerem. Aplikacja musi uruchomić sesję usługi DTLS przy użyciu usługi *nx_secure_dtls_server_session_start*. Chociaż sesja może zostać uruchomiona w samym wywołaniu zwrotowym, zaleca się, aby wywołanie zwrotne było używane tylko do powiadamiania wątku aplikacji (lub dedykowanego wątku DTLS utworzonego przez aplikację) połączenia, ponieważ wywołanie zwrotne jest wywoływane przez wątek IP, który jest używany do przetwarzania całego przetwarzania sieci niższego poziomu (np. UDP). Może to być tak proste jak zapisanie parametru sesji DTLS (podanego jako parametr wywołania zwrotnego) i wywołanie nx_secure_dtls_server_session_start w drugim wątku. Wywołanie connect_notify zwrotnego powinno zazwyczaj zwracać NX_SUCCESS.

Procedura receive_notify wywołania zwrotnego jest wywoływana za każdym razem, gdy zostanie odebrany rekord DTLS, który pasuje do istniejącej ustanowionej sesji DTLS (adres IP hosta zdalnego i port są używane do identyfikowania istniejącej sesji). Reprezentuje to "dane aplikacji", które są szyfrowane i wysyłane za pośrednictwem usługi DTLS. Aplikacja musi wywołać usługę *nx_secure_dtls_session_receive* w podanej sesji DTLS, aby pobrać odebrane dane. Podobnie jak connect_receive zwrotnego, zaleca się, aby sesja została przekazana do innego wątku w celu obsługi przetwarzania komunikatów, ponieważ wywołanie zwrotne jest wywoływane z wątku IP. Wywołanie receive_notify powinno zazwyczaj zwracać NX_SUCCESS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **ip_ptr** Wskaźnik do zainicjowanych bloków NX_IP do użycia jako interfejs sieciowy serwera DTLS.
- **port** Lokalny port UDP, z którym jest powiązane gniazdo UDP serwera DTLS.
- **limit czasu** Wartość limitu czasu do użycia dla operacji sieciowych.
- **session_buffer** Miejsce buforu zawierające bloki sterujące dla wszystkich wystąpień NX_SECURE_DTLS_SESSION przypisanych do tego wystąpienia serwera DTLS.
- **session_buffer_size** Rozmiar buforu sesji. Określa liczbę sesji DTLS przypisanych do serwera DTLS.
- **crypto_table** Wskaźnik do struktury tabeli szyfrowania TLS/DTLS używanej dla wszystkich operacji kryptograficznych.
- **crypto_metadata_buffer** Buforuj miejsce na obliczenia operacji kryptograficznych i informacje o stanie.
- **crypto_metadata_size** Rozmiar buforu metadanych.
- **packet_reassembly_buffer** Bufor używany przez usługi DTLS do ponownego zbierania danych UDP do rekordów DTLS na potrzeby odszyfrowywania.
- **packet_reassembly_buffer_size** Rozmiar buforu ponownego zassembly. Zwykle wartość powinna być większa niż 16 KB, ale może być mniejsza w zależności od aplikacji.
- **connect_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy zdalny klient DTLS próbuje nawiązać połączenie z tym serwerem DTLS.
- **receive_notify** Wywołanie zwrotne jest wywoływane za każdym razem, gdy dane aplikacji są odbierane za pośrednictwem istniejącej sesji DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) Za mało miejsca buforu dla sesji, ponownego zsadu pakietów lub kryptografii.

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

Free up resources used by a NetX Secure DTLS Server

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa pozwala uwolnić zasoby przydzielone do wystąpienia serwera USŁUGI DTLS, w tym wewnętrzne gniazdo UDP używane przez serwer.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie serwera.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_STILL_BOUND** (0x42) UDP jest nadal powiązane.

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

Dodawanie certyfikatu tożsamości serwera lokalnego do bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje certyfikat tożsamości serwera lokalnego do wystąpienia serwera DTLS. Aby klienci połączyli się z serwerem DTLS, wymagany jest co najmniej jeden certyfikat tożsamości, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w przypadku, gdy istnieje wiele certyfikatów tożsamości o tej samej nazwie pospolitej X.509 obecne w magazynie serwera DTLS. Aby uzyskać więcej informacji na temat certyfikatów serwera X.509, zobacz NetX Secure TLS User Guide (Podręcznik użytkownika bezpiecznego systemu TLS netX).

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X.509.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu do serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) Przekazano identyfikator certyfikatu o numerze 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

*Zobacz informacje dotyczące *nx_secure_dtls_server_create,* aby uzyskać bardziej kompletny przykład.

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

Usuwanie certyfikatu tożsamości serwera lokalnego z bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa certyfikat tożsamości serwera lokalnego z wystąpienia serwera USŁUGI DTLS. Co najmniej jeden certyfikat tożsamości jest wymagany, aby klienci łączyli się z serwerem DTLS, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne).

Certyfikat do usunięcia można zidentyfikować za pomocą nazwy pospolitej X.509 lub numerycznej cert_id, która została przypisana w wywołaniu funkcji *nx_secure_dtls_server_local_certificate_add*. Certyfikat cert_id służy tylko do identyfikowania certyfikatu i jest utrzymywany przez aplikację. Jeśli zamiast numerycznego identyfikatora certyfikatu jest używana nazwa pospolita, parametr cert_id powinien mieć wartość 0.

> [!NOTE]
> Usunięcie certyfikatu podczas przetwarzania ugody usługi DTLS spowoduje nieoczekiwane zachowanie. Przed *usunięciem certyfikatów* należy nx_secure_dtls_server_stop usługę.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **common_name** X.509 CommonName certyfikatu do usunięcia. Jeśli jest to używane, przekaż cert_id jako zero.
- **common_name_length** Długość ciągu common_name w bajtach.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy. Jeśli jest używany, przekaż NX_NULL dla common_name parametru.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie certyfikatu z serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Na danym serwerze DTLS nie znaleziono certyfikatu cert_id lub common_name zgodnego z tym certyfikatem.

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

Przypisywanie opcjonalnych procedur wywołania zwrotnego powiadomień do bezpiecznego serwera DTLS NetX

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

Ta usługa może służyć do dodawania opcjonalnych procedur wywołania zwrotnego powiadomień do serwera DTLS. Oba parametry wywołania zwrotnego mogą być przekazywane jako NX_NULL jeśli jest wymagane tylko jedno wywołanie zwrotne.

Wywołanie disconnect_notify zwrotne jest wywoływane, gdy klient zdalny kończy sesję usługi DTLS. Parametr dtls_session to zamknięte wystąpienie sesji. Wywołanie zwrotne powinno zazwyczaj zwracać NX_SUCCESS.

Wywołanie error_notify zwrotne jest wywoływane za każdym razem, gdy wystąpi błąd lub limit czasu usługi DTLS. Parametr dtls_session jest wystąpieniem sesji, dla którego wystąpił błąd, a error_code jest kodem stanu liczbowego błędu, który spowodował problem (zobacz dodatek A)

Bezpieczne kody powrotu/błędu NetX dla listy kodów błędów, które mogą być zwracane). Wywołanie zwrotne powinno zazwyczaj zwracać NX_SUCCESS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **disconnect_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy host klienta zdalnego zamyka sesję usługi DTLS.
- **error_notify** Procedura wywołania zwrotnego wywoływana za każdym razem, gdy dtls napotka błąd lub limit czasu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przypisanie procedur wywołania zwrotnego.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.

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

Dodawanie klucza wstępnego do bezpiecznego serwera DTLS NetX

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

Ta usługa dodaje klucz wstępny, jego ciąg tożsamości i wskazówkę tożsamości do bloku sterowania serwera DTLS. W przypadku włączonego i używanego szyfrowania PSK certyfikat cyfrowy jest używany w miejsce certyfikatu cyfrowego.

Dodawany kod PSK jest replikowany we wszystkich sesjach usługi DTLS przypisanych do serwera USŁUGI DTLS (za pośrednictwem buforu sesji podanego w wywołaniu nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **pre_shared_key** Rzeczywista wartość PSK.
- **psk_length** Długość wartości PSK.
- **psk_identity** Ciąg używany do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości psk.
- **wskazówka** Ciąg używany do wskazywania grupy psk do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie psk.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik serwera DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Nie można dodać kolejnego psk.

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

Wysyłanie danych za pośrednictwem sesji DTLS ustanowionej za pomocą bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet danych za pośrednictwem ustanowionej sesji serwera DTLS do zdalnego hosta klienta usługi DTLS. Używana sesja jest uzyskiwana w receive_notify wywołania zwrotnego dostarczonego do nx_secure_dtls_session_create.

Dane dostarczone w pakiecie, który musi zostać przydzielony przy użyciu usługi *nx_secure_dtls_packet_allocate,* są szyfrowane przy użyciu procedur i parametrów kryptograficznych sesji DTLS, a następnie wysyłane do hosta zdalnego za pośrednictwem wewnętrznego portu UDP serwera DTLS na adres IP i port dołączonego klienta (przechowywane w sesji DTLS).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji DTLS uzyskany z receive_notify wywołania zwrotnego dostarczonego przez aplikację.
- **packet_ptr** Wskaźnik do NX_PACKET przydzielonego wcześniej i wypełnionego danymi aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Wystąpił błąd w podstawowej operacji wysyłania protokołu UDP.

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

Uruchamianie sesji DTLS z bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję serwera DTLS, wykonując ugodę DTLS po stronie serwera, gdy zdalny klient usługi DTLS nawiąował połączenie z serwerem i zażądał połączenia z usługą DTLS.

Sesja DTLS jest uzyskiwana w connect_notify procedury wywołania zwrotnego udostępnianej nx_secure_dtls_server_create.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji USŁUGI DTLS uzyskanego z serwera DTLS connect_notify zwrotnego.
- **wait_option** Wartość oczekiwania ThreadX do użycia na użytek operacji sieciowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Nie można przydzielić pakietu uściśniania usługi DTLS (pula pakietów jest pusta).
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) Poszukano danych, które nie były prawidłowym rekordem DTLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Prawidłowe wyznaczanie wartości skrótu rekordu DTLS nie powiodło się (błąd szyfrowania).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Sprawdzanie wypełnienia szyfrowania.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Ponowiązywano alert z hosta zdalnego podczas uściśniania usługi DTLS.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Odebrano nierozpoznany komunikat podczas uściśniania usługi DTLS.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Odszukaliśmy rekord DTLS o nieprawidłowej długości.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Odebrano clientHello bez obsługiwanych mechanizmów szyfrowania DTLS.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method (0x118) Recevied a ClientHello with a unknown compression method (Recevied a ClientHello z nieznaną metodą kompresji).
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Ogólne (nieokreślone) niepowodzenie ugody, zwykle z powodu problemów z przetwarzaniem rozszerzenia.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) Funkcja, która nie jest jeszcze obsługiwana, została wywołana podczas uściśniania usługi DTLS.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Napotkano nieznanyphersuite (wskazany wewnętrzny błąd kryptografii).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Ponowiązywano rekord DTLS z niezgodną wersją usługi DTLS.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Nie można zweryfikować skrótu uściśniania usługi DTLS, sesja jest nieprawidłowa.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Wewnętrzne wysyłanie protokołu UDP nie powiodło się.

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

Uruchamianie wystąpienia serwera bezpiecznego protokołu DTLS NetX nasłuchujących na skonfigurowanym porcie UDP

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Opis

Ta usługa uruchamia serwer DTLS. Po zakończeniu wywołania serwer jest aktywny i rozpocznie przetwarzanie żądań przychodzących od klientów usługi DTLS. Wystąpienie serwera musi być skonfigurowane przy użyciu usługi *nx_secure_dtls_server_create*.

> [!NOTE]
> Ta usługa wiąże wewnętrzny port UDP serwera DTLS ze skonfigurowanym portem lokalnym, więc większość napotkanych problemów będzie dotyczyć komunikacji UDP i konfiguracji sieci.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uruchomienie serwera.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_NOT_ENABLED** (0x14) UDP nie jest włączona.
- **NX_NO_FREE_PORTS** (0x45) Brak dostępnych portów UDP.
- **NX_INVALID_PORT** (0x46) Nieprawidłowy port UDP.
- **NX_ALREADY_BOUND** (0x22) UDP jest już powiązany.
- **NX_PORT_UNAVAILABLE** (0x23) UDP jest niedostępny do użycia.

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

Zatrzymywanie aktywnego wystąpienia bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje nasłuchiwanie przez serwer DTLS na skonfigurowanym porcie UDP i resetuje wszystkie skojarzone sesje protokołu DTLS, wstrzymując całą w toku komunikację z usługą DTLS.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do aktywnego wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie serwera.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.

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

Dodawanie certyfikatu zaufanego urzędu certyfikacji do bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje certyfikat zaufanego urzędu certyfikacji lub pośredniego urzędu certyfikacji do wystąpienia serwera USŁUGI DTLS i przypisuje go do wszystkich wewnętrznych sesji serwera DTLS. Jest to konieczne tylko wtedy, gdy uwierzytelnianie certyfikatu klienta X.509 jest włączone przy użyciu *nx_secure_dtls_server_x509_client_verify_configure*. Dodany certyfikat będzie używany do weryfikowania przychodzących certyfikatów X.509 klienta.

Parametr cert_id jest liczbowym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w przypadku, gdy istnieje wiele certyfikatów tożsamości o tej samej nazwie pospolitej X.509 obecne w magazynie serwera DTLS. Aby uzyskać więcej informacji na temat certyfikatów serwera X.509, zobacz NetX Secure TLS User Guide (Podręcznik użytkownika bezpiecznego serwera NetX).

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X.509.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu do serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) Przekazano identyfikator certyfikatu o numerze 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

*Zobacz informacje dotyczące *nx_secure_dtls_server_create,* aby uzyskać bardziej kompletny przykład.

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

Usuwanie certyfikatu zaufanego urzędu certyfikacji z bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa certyfikat zaufanego urzędu certyfikacji z wystąpienia serwera DTLS. Certyfikaty zaufanego urzędu certyfikacji są niezbędne tylko dla serwera DTLS, dla którego włączono weryfikację certyfikatu klienta X.509 przez wywołanie nx_secure_dtls_server_x509_client_verify_configure *.*

Certyfikat do usunięcia można zidentyfikować za pomocą nazwy pospolitej X.509 lub wartości liczbowej cert_id przypisanej w wywołaniu funkcji *nx_secure_dtls_server_trusted_certificate_add*. Certyfikat cert_id służy tylko do identyfikowania certyfikatu i jest utrzymywany przez aplikację. Jeśli zamiast numerycznego identyfikatora certyfikatu jest używana nazwa pospolita, parametr cert_id powinien mieć wartość 0.

> [!NOTE]
> Usunięcie certyfikatu podczas przetwarzania ugody usługi DTLS może spowodować nieoczekiwane zachowanie. Przed *usunięciem certyfikatów* należy nx_secure_dtls_server_stop usługę.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **common_name** X.509 CommonName certyfikatu do usunięcia. Jeśli jest to używane, przekaż cert_id jako zero.
- **common_name_length** Długość ciągu common_name w bajtach.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy. Jeśli jest używany, przekaż NX_NULL dla common_name parametru.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie certyfikatu z serwera DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Na danym serwerze DTLS nie znaleziono certyfikatu cert_id lub common_name zgodnego z tym certyfikatem.

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

Konfigurowanie bezpiecznego serwera DTLS NetX w celu żądania i weryfikowania certyfikatów klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Opis

Ta usługa konfiguruje serwer DTLS w celu żądania i weryfikowania certyfikatów klienta usługi DTLS. Ta opcjonalna funkcja jest używana, gdy certyfikaty X.509 są wymagane do uwierzytelniania klienta, a nie innych mechanizmów (np. klucza wstępnego).

> [!IMPORTANT]
> *Jeśli serwer DTLS jest skonfigurowany do weryfikowania certyfikatów klienta przy użyciu tej usługi, należy dodać do serwera co najmniej jeden certyfikat zaufanego urzędu certyfikacji przy użyciu usługi nx_secure_dtls_server_trusted_certificate_add lub serwer odrzuci wszystkie przychodzące połączenia klienckie, ponieważ nie będzie mógł zweryfikować certyfikatów klienta w zaufanym magazynie.*

Podczas wywoływania tej usługi wystąpienie serwera USŁUGI DTLS będzie (po jego zakończeniu) żądać certyfikatów klienta w ramach uściśniania usługi DTLS. Zakładając, że klient jest prawidłowo skonfigurowany przy użyciu certyfikatu tożsamości (i skojarzonego łańcucha certyfikatów, jeśli ma to zastosowanie), serwer DTLS wymaga przydzielenia pamięci w celu przetwarzania danych certyfikatu klienta. Ta pamięć jest przekazywana jako *certs_buffer* parametru.

Rozmiar certs_buffer musi być przystosowany do największego oczekiwanego łańcucha certyfikatów od klienta dtls, czyli liczbę sesji *serwera DTLS.* Bufor jest dzielony między dostępne sesje przy użyciu *certs_per_session,* który reprezentuje maksymalną oczekiwaną liczbę certyfikatów w łańcuchu certyfikatów klienta. Bufor musi również zapewnić miejsce dla struktury NX_SECURE_X509_CERT danych, która jest używana do analizowania danych certyfikatu.

Prawidłowy rozmiar buforu można obliczyć przy użyciu następującej formuły:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- Liczba sesji usługi DTLS zależy od rozmiaru buforu sesji przekazanego do nx_secure_dtls_server_create.
- certs_per_session należy ustawić maksymalną oczekiwaną liczbę certyfikatów w dowolnym łańcuchu certyfikatów klienta.
- Maksymalny oczekiwany rozmiar certyfikatu zależy od aplikacji, rozmiarów kluczy i innych czynników, ale 2 KB jest ogólnie wystarczające.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.
- **certs_per_session** Liczba certyfikatów do przydzielenia do każdej sesji serwera DTLS.
- **certs_buffer** Miejsce buforu dla przychodzących danych certyfikatu.
- **buffer_size** Rozmiar buforu certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna konfiguracja weryfikacji klienta X.509.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy magazyn certyfikatów (wystąpienie DTLSserver nie jest initalized?).

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

Wyłącza weryfikację certyfikatu X.509 klienta dla bezpiecznego serwera DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza weryfikację certyfikatu klienta X.509 na serwerze DTLS. Usługa nie aktywna, jeśli weryfikacja certyfikatu klienta X.509 nie jest włączona.

> [!NOTE]
> Wyłączenie uwierzytelniania klienta w aktywnym wystąpieniu serwera DTLS może spowodować nieprzewidywalne zachowanie. Usługa nx_secure_dtls_server_stop powinna zostać wywołana przed zmianą stanu serwera.

### <a name="parameters"></a>Parametry

- **server_ptr** Wskaźnik do utworzonego wcześniej wystąpienia serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wyłączenie uwierzytelniania klienta X.509.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.

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

Uzyskiwanie informacji o kliencie zdalnym z sesji serwera DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Opis

Ta usługa zwraca informacje o sieci klienta DTLS, który jest połączony z określoną sesją serwera DTLS. Zwrócone informacje składają się z adresu IP i portu UDP klienta zdalnego, a także portu serwera lokalnego, z którym klient jest połączony.

Ogólnie rzecz biorąc, wystąpienie sesji USŁUGI DTLS będzie wystąpieniem uzyskanymi w wywołaniu jednej z procedur wywołania zwrotnego powiadomień USŁUGI DTLS (np. wywołań zwrotnych connect_notify lub receive_notify przekazywanych do nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do aktywnego wystąpienia sesji serwera DTLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie serwera.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_SOCKET** (0x13) Skojarzone gniazdo UDP jest nieprawidłowe (sesja nie została zainicjowana?).
- **NX_NOT_CONNECTED** (0x38) gniazda UDP nie jest połączone — połączenie klienta zostało przerwane lub nie zostało jeszcze nawiązane.

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

Tworzenie i konfigurowanie bezpiecznej sesji DTLS netx

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

Ta usługa tworzy i konfiguruje sesję dtls. Ogólnie rzecz biorąc, będzie to używane do tworzenia sesji klienta USŁUGI DTLS, ponieważ sesje serwera DTLS są zarządzane przy użyciu mechanizmu serwera DTLS (zobacz *nx_secure_dtls_server_create), ale* mogą wystąpić wystąpienia, w których aplikacja musi utworzyć jedno autonomiczne wystąpienie sesji serwera DTLS, w takim przypadku można użyć tej usługi <sup>7</sup>.

Parametry konfigurują informacje i alokację pamięci potrzebne do wystąpienia sesji DTLS. Parametr crypto_table to tabela protokołu TLS zawierająca wszystkie procedury kryptograficzne wymagane do szyfrowania i uwierzytelniania protokołów TLS/DTLS. Interfejs metadata_buffer jest używany do szyfrowania caclulations (zobacz nx_secure_tls_metadata_size_calculate w Przewodniku użytkownika protokołu NetX Secure TLS), a packet_reassembly_buffer służy do ponownego zbierania datagramów UDP do pełnego rekordu DTLS na potrzeby odszyfrowywania.

Pakiety certs_number i remote_certificate_buffer są wymagane dla klientów DTLS, którzy potrzebują miejsca do przechowywania i przetwarzania przychodzącego łańcucha certyfikatów serwera DTLS. Bufor musi być w stanie obsłużyć maksymalny oczekiwany rozmiar łańcucha certyfikatów dla dowolnego serwera, z którym będzie się łączyć. Bufor jest podzielony przez liczbę oczekiwanych certyfikatów (parametr certs_number) i musi być wystarczająco duży, aby pomieścić jeden NX_SECURE_X509_CERT struktury na certyfikat. Rozmiar buforu można określić przy użyciu następującej formuły:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number to oczekiwana maksymalna liczba certyfikatów w łańcuchu certyfikatów serwera
- Maksymalny rozmiar certyfikatu zależy od rozmiaru używanych kluczy i informacji w certyfikacie, ale zwykle wystarczy 2 KB.

**7** Tworzenie sesji serwera DTLS za pomocą tej procedury nie jest zalecane i ma pewne ograniczenia. Podstawowym problemem jest to, że sesja nie będzie bezpiecznie obsługiwać dodatkowych połączeń klienta — ponieważ połączenie UDP jest bez połączenia drugi klient może legalnie wysyłać dane do portu UDP serwera, gdy poprzednia sesja dtls jest nadal aktywna, co może spowodować zakończenie sesji serwera z błędem.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do niezainicjowanej struktury sesji usługi DTLS.
- **crypto_table** Wskaźnik do struktury tabeli szyfrowania TLS/DTLS używanej dla wszystkich operacji kryptograficznych.
- **crypto_metadata_buffer** Buforuj miejsce na obliczenia operacji kryptograficznych i informacje o stanie.
- **crypto_metadata_size** Rozmiar buforu metadanych.
- **packet_reassembly_buffer** Bufor używany przez usługi DTLS do ponownego zbierania danych UDP do rekordów DTLS na potrzeby odszyfrowywania.
- **packet_reassembly_buffer_size** Rozmiar buforu ponownego zassembly. Zwykle wartość powinna być większa niż 16 KB, ale może być mniejsza w zależności od aplikacji.
- **certs_number** Maksymalna oczekiwana liczba certyfikatów w łańcuchu certyfikatów serwera zdalnego.
- **remote_certificate_buffer** Buforuj miejsce dla przychodzących danych certyfikatu.
- **remote_certificate_buffer_size** Rozmiar buforu certyfikatu.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie sesji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu.
- **NX_INVALID_PARAMETERS** (0x4D) Za mało miejsca buforu dla ponownego zsadu pakietów, certyfikatów lub kryptografii.

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

Free up resources used by a NetX Secure DTLS Session

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Opis

Ta usługa usuwa sesję DTLS, co powoduje usunięcie wszystkich zasobów, które zostały przydzielone podczas jej tworzenia.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie sesji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu.

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

Zamykanie aktywnej sesji bezpiecznego dtls netx

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa kończy aktywną sesję dtls, wysyłając alert TLS/DTLS CloseNotify do hosta zdalnego. Używany adres IP i port są używane w poprzednim wywołaniu nx_secure_dtls_session_send.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.
- **wait_option** Wartość oczekiwania ThreadX do użycia dla operacji sieciowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie sesji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Nie można przydzielić pakietów dla alertu CloseNotify.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Prawdopodobny błąd wewnętrzny — procedura kryptograficzna nie jest rozpoznawana.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Nie można wysłać podstawowego protokołu UDP.
- **NX_IP_ADDRESS_ERROR** (0x21) z adresem IP hosta zdalnego.
- **NX_NOT_BOUND** (0x24) Bazowe gniazdo UDP nie jest powiązane z portem.
- **NX_INVALID_PORT** (0x46) Nieprawidłowy port UDP.
- **NX_PORT_UNAVAILABLE** (0x23) UDP nie jest dostępny do użycia.

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

Dodawanie certyfikatu tożsamości lokalnej do bezpiecznej sesji DTLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje certyfikat tożsamości lokalnej do wystąpienia sesji USŁUGI DTLS. Ogólnie rzecz biorąc, ta usługa będzie używana, gdy sesja klienta USŁUGI DTLS musi udostępnić certyfikat tożsamości hostowi serwera zdalnego. Jest to opcjonalna konfiguracja dla usługi DTLS, więc certyfikat nie jest zazwyczaj wymagany dla klientów USŁUGI DTLS. Certyfikat tożsamości wymaga skojarzonego klucza prywatnego.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w przypadku, gdy istnieje wiele certyfikatów tożsamości o tej samej nazwie pospolitej X.509 obecne w magazynie certyfikatów DTLS. Aby uzyskać więcej informacji na temat certyfikatów X.509, zobacz NetX Secure TLS User Guide (Podręcznik użytkownika bezpiecznego systemu TLS netX).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji USŁUGI DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X.509.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu do sesji DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) Przekazano identyfikator certyfikatu o identyfikatorze 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

*Zobacz informacje dotyczące *nx_secure_dtls_session_create,* aby uzyskać bardziej kompletny przykład.

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

Usuwanie certyfikatu tożsamości lokalnej z sesji bezpiecznego dtls netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa certyfikat tożsamości lokalnej z wystąpienia sesji USŁUGI DTLS przy użyciu numeru identyfikatora certyfikatu (przypisanego podczas dodaniu certyfikatu za pomocą nx_secure_dtls_session_local_certificate_add) lub pola X.509 CommonName.

Jeśli parametr common_name jest używany do dopasowania certyfikatu, parametr cert_id powinien być ustawiony na 0. Jeśli cert_id jest używany, common_name powinna zostać przekazana wartość NX_NULL.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w przypadku, gdy istnieje wiele certyfikatów tożsamości o tej samej nazwie pospolitej X.509 obecne w magazynie certyfikatów DTLS. Aby uzyskać więcej informacji na temat certyfikatów X.509, zobacz NetX Secure TLS User Guide (Podręcznik użytkownika bezpiecznego systemu TLS netX).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji USŁUGI DTLS.
- **common_name** Wskaźnik do ciągu CommonName do dopasowania.
- **common_name_length** Długość ciągu common_name ciągu.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie certyfikatu z sesji DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) W danej sesji DTLS nie znaleziono certyfikatu zgodnego cert_id ani common_name certyfikatu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

*Zobacz informacje dotyczące *nx_secure_dtls_session_create,* aby uzyskać bardziej kompletny przykład.

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

Odbieranie danych aplikacji za pośrednictwem ustanowionej sesji bezpiecznego dtls netx

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Opis

Ta usługa zwraca dane aplikacji odebrane przez aktywną sesję DTLS. Sesja DTLS może być sesją serwera DTLS (zarządzaną przez wystąpienie serwera DTLS) lub sesją klienta usługi DTLS. Zwrócony pakiet może być przetwarzany przy użyciu dowolnej usługi interfejsu API NX_PACKET (więcej informacji można znaleźć w dokumentacji netX).

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.
- **packet_ptr_ptr** Wskaźnik do NX_PACKET wskaźnika dla pakietu powrotu.
- **wait_option** Wartość oczekiwania ThreadX do użycia dla operacji sieciowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne odebranie pakietu danych aplikacji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub pakietu.
- **NX_NOT_ENABLED** (0x14) UDP nie jest włączona.
- **NX_NOT_BOUND** (0x24) UDP nie jest powiązane z portem.
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) Poszukano danych, które nie były prawidłowym rekordem DTLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Prawidłowe wyznaczanie wartości skrótu rekordu DTLS (błąd szyfrowania) nie powiodło się.
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Sprawdzanie wypełnienia szyfrowania.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Odszukaliśmy alert z hosta zdalnego.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Odebrano nierozpoznany komunikat.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Odszukaliśmy rekord DTLS z nieprawidłową długością.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Napotkano nieznany ciphersuite (wskazuje wewnętrzny błąd kryptografii).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Ponownie pozysł rekord DTLS z niezgodną wersją usługi DTLS.

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

Wyczyść dane w wystąpieniu bezpiecznej sesji DTLS NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Opis

Ta usługa resetuje sesję USŁUGI DTLS, czyszcząc wszystkie efemeryjne dane kryptograficzne i umożliwiając ponownego wykorzystać strukturę dla nowej sesji. Trwałe dane (np. magazyny certyfikatów) są przechowywane, dzięki czemu nx_secure_dtls_session_create nie trzeba wielokrotnie wywoływania.

### <a name="parameters"></a>Parametry

- **dtls_session** Wskaźnik do struktury sesji DTLS, która została zainicjowana wcześniej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zresetowanie sesji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu.

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

Ta usługa wysyła pakiet danych za pośrednictwem ustanowionej sesji DTLS do zdalnego hosta DTLS pod danym adresem IP i portem. Używana sesja jest aktywną sesją klienta USŁUGI DTLS. Należy pamiętać, że adres IP i port są udostępniane ze względu na bez stanowy charakter protokołu UDP, ale powinny być zgodne z adresem i portem używanym do uruchamiania sesji w nx_secure_dtls_session_start.

Dane podane w pakiecie, który musi zostać przydzielony przy użyciu usługi *nx_secure_dtls_packet_allocate,* są szyfrowane przy użyciu parametrów kryptograficznych sesji DTLS i procedur, a następnie wysyłane do hosta zdalnego za pośrednictwem gniazda UDP sesji USŁUGI DTLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do aktywnego wystąpienia sesji klienta USŁUGI DTLS.
- **packet_ptr** Wskaźnik do wystąpienia NX_PACKET przydzielonego wcześniej i wypełnionego danymi aplikacji.
- **ip_address** Wskaźnik do NXD_ADDRESS struktury zawierającej adres IP hosta zdalnego.
- **port** Port UDP na hoście zdalnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wysłanie pakietu.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Wystąpił błąd w podstawowej operacji wysyłania protokołu UDP.

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

Dodawanie certyfikatu zaufanego urzędu certyfikacji do bezpiecznej sesji DTLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa dodaje zaufany lub pośredni certyfikat X.509 urzędu certyfikacji do wystąpienia sesji DTLS. Klient DTLS wymaga co najmniej jednego zaufanego certyfikatu w celu zweryfikowania certyfikatów serwera zdalnego, chyba że jest używany alternatywny mechanizm uwierzytelniania (np. klucze wstępne). Zaufany certyfikat zazwyczaj nie ma klucza prywatnego.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w przypadku, gdy istnieje wiele certyfikatów tożsamości o tej samej nazwie pospolitej X.509 obecne w magazynie certyfikatów DTLS. Aby uzyskać więcej informacji na temat certyfikatów X.509, zobacz NetX Secure TLS User Guide (Podręcznik użytkownika bezpiecznego systemu TLS netX).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji USŁUGI DTLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanej struktury certyfikatu X.509.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu do sesji DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_INVALID_PARAMETERS** (0x4D) Przekazano identyfikator certyfikatu o identyfikatorze 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

*Zobacz informacje dotyczące *nx_secure_dtls_session_create,* aby uzyskać bardziej kompletny przykład.

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

Usuwanie certyfikatu zaufanego urzędu certyfikacji z sesji bezpiecznego dtls netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Opis

Ta usługa usuwa zaufany certyfikat urzędu certyfikacji z wystąpienia sesji USŁUGI DTLS przy użyciu numeru identyfikatora certyfikatu (przypisanego podczas dodaniu certyfikatu za pomocą programu nx_secure_dtls_session_trusted_certificate_add) lub pola X.509 CommonName.

Jeśli parametr common_name jest używany do dopasowania certyfikatu, parametr cert_id powinien być ustawiony na 0. Jeśli cert_id jest używany, common_name powinna zostać przekazana wartość NX_NULL.

Parametr cert_id jest numerycznym, niezerowym identyfikatorem certyfikatu. Dzięki temu certyfikat można łatwo usunąć lub znaleźć w przypadku, gdy istnieje wiele certyfikatów tożsamości o tej samej nazwie pospolitej X.509 obecne w magazynie certyfikatów DTLS. Aby uzyskać więcej informacji na temat certyfikatów X.509, zobacz NetX Secure TLS User Guide (Podręcznik użytkownika bezpiecznego systemu TLS netX).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji USŁUGI DTLS.
- **common_name** Wskaźnik do ciągu CommonName do dopasowania.
- **common_name_length** Długość ciągu common_name ciągu.
- **cert_id** Unikatowy identyfikator numeryczny dla tego certyfikatu na tym serwerze DTLS jest niezerowy.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie certyfikatu z sesji DTLS.
- **NX_PTR_ERROR** (0x07) Przekazany nieprawidłowy wskaźnik.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) W danej sesji DTLS nie znaleziono certyfikatu zgodnego cert_id ani common_name certyfikatu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

*Zobacz informacje dotyczące *nx_secure_dtls_session_create,* aby uzyskać bardziej kompletny przykład.

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
