---
title: Rozdział 4 — Opis usług Azure RTO NetX Secure Services
description: Ten rozdział zawiera opis wszystkich NetX Secure Services (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822854"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Rozdział 4 — Opis usług Azure RTO NetX Secure Services

Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Secure Services (wymienionych poniżej) w porządku alfabetycznym.

W sekcji "wartości zwracane" w poniższych opisach interfejsu API wartości **pogrubione** nie mają wpływ na to, **NX_SECURE_DISABLE_ERROR_CHECKING** makro, które jest używane do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Wykonaj self_test metod kryptograficznych
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Oblicza wartość skrótu przy użyciu funkcji skrótu user_supplied
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Ustaw aktywny certyfikat tożsamości dla sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Ustaw klucz Pre_Shared dla sesji klienta Secure TLS NetX
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Inicjuje moduł bezpiecznego protokołu TLS NetX]
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Dodawanie certyfikatu lokalnego do NetX bezpiecznej sesji protokołu TLS
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Znajdowanie certyfikatu lokalnego w NetX bezpiecznej sesji TLS według nazwy pospolitej
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Usuń certyfikat lokalny z bezpiecznej sesji protokołu TLS NetX
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Obliczanie rozmiaru metadanych kryptograficznych dla sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Przydziel pakiet dla sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Dodaj klucz Pre_Shared do sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Przydzielanie miejsca dla certyfikatu dostarczonego przez hosta zdalnego protokołu TLS
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta protokołu TLS
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Wolne miejsce przydzielono dla certyfikatów przychodzących
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Dodawanie certyfikatu przeznaczonego dla serwerów TLS przy użyciu identyfikatora liczbowego
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Konfigurowanie wywołania zwrotnego protokołu TLS do użycia na potrzeby dodatkowej weryfikacji certyfikatu
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Konfigurowanie wywołania zwrotnego protokołu TLS do wywołania na początku uzgadniania klienta TLS
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Włącz weryfikację klienta X. 509 i Przydziel miejsce dla certyfikatów klienta
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Wyłączanie uwierzytelniania certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Włącz uwierzytelnianie certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Tworzenie bezpiecznej sesji protokołu TLS NetX na potrzeby bezpiecznej komunikacji
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Usuwanie sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Kończenie aktywnej sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Ustawianie buforu ponownego zestawu pakietów dla sesji bezpiecznego protokołu TLS NetX
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Zastąp domyślną wersję protokołu TLS dla sesji Secure TLS NetX
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Odbieranie danych z bezpiecznej sesji protokołu TLS NetX
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Przypisanie wywołania zwrotnego, które zostanie wywołane na początku ponownej negocjacji sesji
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Inicjowanie uzgadniania sesji z hostem zdalnym
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Wyczyść i zresetuj bezpieczną sesję protokołu TLS NetX
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Wysyłanie danych za pomocą zabezpieczonej sesji protokołu TLS NetX
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Skonfiguruj wywołanie zwrotne protokołu TLS do wywołania na początku uzgadniania serwera TLS
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego z klienta TLS
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Ustaw nazwę DNS rozszerzenia Oznaczanie nazwy serwera (SNI) na wysyłanie do serwera zdalnego
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Rozpocznij sesję bezpiecznego protokołu TLS NetX
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Przypisywanie funkcji sygnatury czasowej do NetX bezpiecznej sesji TLS
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Dodaj zaufany certyfikat do NetX bezpiecznej sesji TLS
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Usuń zaufany certyfikat z bezpiecznej sesji protokołu TLS NetX
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Zainicjuj certyfikat X. 509 dla usługi NetX Secure TLS
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Sprawdź nazwę DNS w odniesieniu do certyfikatu X. 509
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Sprawdź certyfikat X. 509 względem podanej listy odwołania certyfikatów (CRL)]
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Zainicjuj strukturę nazw DNS X. 509
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X. 509 w certyfikacie X. 509
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Znajdź i zwróć rozszerzenie X. 509 w certyfikacie X. 509
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Znajdź i Przeanalizuj rozszerzenie użycie klucza X. 509 w certyfikacie X. 509

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Wykonaj własne Testowanie metod kryptograficznych

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Opis

Ta usługa jest uruchamiana za pomocą testów metod kryptograficznych, aby sprawdzić poprawność. Test samodzielny jest dostępny tylko wtedy, gdy biblioteka NetX Secure została skompilowana z symbolem zdefiniowanym NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK.

Dla każdej obsługiwanej metody kryptograficznej, autotest dostarcza wstępnie zdefiniowane dane wejściowe i zweryfikowane dane wyjściowe są zgodne ze wstępnie zdefiniowaną wartością oczekiwaną.

Bezpieczny samotest kryptograficzny NetX obsługuje następujące algorytmy i rozmiary kluczy:

- DES: szyfrowanie i odszyfrowywanie
- Triple DES (3DES): szyfrowanie i odszyfrowywanie
- AES: 128-, 192-, 256-bitowy rozmiar klucza, szyfrowanie i odszyfrowywanie, w trybie CBC i w trybie licznika.
- HMAC-MD5: uwierzytelnianie i obliczanie wartości skrótu
- HMAC-SHA: SHA1-96, SHA1-160, algorytmu SHA2-256, algorytmu SHA2-384, algorytmu SHA2-512, uwierzytelnianie i obliczanie wartości skrótu
- MD5: uwierzytelnianie
- Funkcja pseudo-Losowa (PRF): PRF_HMAC_SHA1 i PRF_HMAC_SHA2-256
- RSA: 1024-, 2048-, 4096-bit-bitowego operacji dla modułu RSA
- SHA: SHA1 (96-i 160-bitowe), algorytmu SHA2 (256bit, 384bit, 512bit)

Ta funkcja ma wbudowane wektory dla algorytmów kryptograficznych wymienionych powyżej. Jednak testuje tylko te wymienione w *cipher_table* przekazaną do tej funkcji. Na przykład w przypadku sesji TLS używa tylko TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite, ta funkcja przeprowadzi autotest na RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) i SHA1.

### <a name="parameters"></a>Parametry

- **crypto_table** Wskaźnik do tabeli kryptograficznej używanej przez sesję TLS. Jest to ten sam crypto_table, który jest przesyłany do wywołania **_nx_secure_tls_session_create ()_** .
- **metadane** Wskaźnik na miejsce dla obszaru metadanych kryptografii. .
- **metadata_size** Rozmiar buforu metadanych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SECURE_TLS_SUCCESS** (0X00) pomyślnie przetestowała dostarczone metody kryptograficzne.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa struktura metody kryptograficznej
- **NX_NOT_SUCCESSFUL** (0x43) samotest kryptograficzny nie powiedzie się.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Oblicza wartość skrótu przy użyciu funkcji skrótu dostarczonej przez użytkownika

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>Opis

Ta funkcja oblicza wartość skrótu strumienia danych w określonym obszarze pamięci przy użyciu dostarczonej metody kryptograficznej HMAC i ciągu klucza. Funkcja obliczania skrótu modułu jest dostępna tylko wtedy, gdy biblioteka NetX Secure została skompilowana przy użyciu następującego zdefiniowanego symbolu: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Parametry

- **hmac_ptr** Wskaźnik do metody kryptograficznej HMAC używanej do obliczania wartości skrótu.
- **start_address** Adres początkowy buforu danych
- **end_address** Adres końcowy buforu danych. Należy zauważyć, że obliczenia skrótu nie obejmują danych w tym end_address.
- **klucz** Ciąg klucza używany w obliczeniach HMAC.
- **key_length** Rozmiar ciągu klucza w bajtach
- **metadane** Wskaźnik do miejsca używanego przez Algorytm HMAC.
- **metadata_size** Rozmiar buforu metadanych.
- **output_buffer** Lokalizacja pamięci, w której jest przechowywane dane wyjściowe skrótu.
- **output_buffer_size** Dostępne miejsce w buforze wyjściowym (w bajtach)
- **actual_size** Zwrócone przez funkcję wskazującą rzeczywistą liczbę bajtów zapisywanych w output_buffer.

### <a name="return-values"></a>Wartości zwrócone

- **0** pomyślnie przeliczył wartość skrótu.
- **1** Obliczanie skrótu nie powiodło się.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

Ustaw aktywny certyfikat tożsamości dla sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji (zobacz nx_secure_tls_session_client_callback_set i nx_secure_tls_session_server_callback_set). Gdy jest wywoływana z wcześniej zainicjowaną strukturą NX_SECURE_X509_CERT, ten certyfikat będzie używany zamiast domyślnego certyfikatu tożsamości. W większości przypadków certyfikat należy dodać do magazynu lokalnego (zobacz nx_secure_tls_local_certificate_add) lub uzgadnianie protokołu TLS może zakończyć się niepowodzeniem.

Ta usługa ma pozwolić, aby protokół TLS obsługiwał wiele certyfikatów tożsamości. Jest to przydatne w przypadku serwera TLS z wieloma adresami sieciowymi, dzięki czemu serwer może wybrać odpowiedni certyfikat do udostępnienia klientowi zdalnemu w zależności od punktu wejścia klienta. W przypadku klienta TLS ta procedura może służyć do zmiany certyfikatu wysłanego do zdalnego serwera w czasie wykonywania po zidentyfikowaniu serwera w uzgadnianiu TLS (jest to trudniejsze niż w przypadku użycia serwera TLS).

W przypadku, gdy wiele certyfikatów może współużytkować tę samą nazwę wyróżniającą X. 509, należy dodać certyfikaty przy użyciu nx_secure_tls_server_certificate_add, co wprowadza identyfikator liczbowy oddzielny od certyfikatu.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS przeszedł do wywołania zwrotnego sesji.
- **certyfikat** Wskaźnik na zainicjowany certyfikat X. 509, który ma być używany dla bieżącej sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne przypisanie certyfikatu do sesji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik certyfikatu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

Ustaw klucz wstępny dla sesji klienta Secure TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku kontroli sesji protokołu TLS i ustawia, że klucz PSK ma być używany w kolejnych połączeniach klientów TLS. PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.

W takim przypadku PSK jest skojarzony z określonym zdalnym serwerem protokołu TLS, z którym klient protokołu TLS chce się komunikować. Zestaw PSK ustawiony za pomocą tego interfejsu API zostanie udostępniony hostowi zdalnego protokołu TLS podczas kolejnego uzgadniania protokołu TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **pre_shared_key** Rzeczywista wartość klucza PSK.
- **psk_length** Długość wartości klucza PSK.
- **psk_identity** Ciąg służący do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości PSK.
- **Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

Inicjuje moduł bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Opis

Ta usługa Inicjuje moduł bezpiecznego protokołu TLS NetX. Musi zostać wywołana przed uzyskaniem dostępu do innych zabezpieczonych usług NetX.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Dodawanie certyfikatu lokalnego do NetX bezpiecznej sesji protokołu TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje zainicjowane wystąpienie struktury NX_SECURE_X509_CERT do lokalnego magazynu sesji TLS. Ten certyfikat może być używany przez stos TLS do identyfikowania urządzenia podczas uzgadniania TLS (jeśli został oznaczony jako certyfikat tożsamości podczas inicjowania struktury certyfikatu przy użyciu nx_secure_x509_certificate_initialize) lub jako wystawca w ramach łańcucha certyfikatów dostarczonego do hosta zdalnego podczas uzgadniania protokołu TLS.

Jeśli potrzebujesz wielu certyfikatów lokalnych o tej samej nazwie pospolitej, certyfikaty mogą być dodawane za pomocą usługi *nx_secure_tls_server_certificate_add* (Zobacz ostrzeżenie poniżej).

**Wymagany** jest certyfikat w trybie serwera TLS.

Certyfikat jest *opcjonalny* dla trybu klienta protokołu TLS.

> [!IMPORTANT]
> *Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a nx_secure_tls_local_certificate_add indeksy na podstawie nazwy pospolitej X. 509. Lokalne usługi certyfikatów zapewniają wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certificate_ptr** Wskaźnik do zainicjowane wystąpienie certyfikatu TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.
- W **NX_INVALID_PARAMETERS** (0x4D) podjęto próbę dodania nieprawidłowego lub zduplikowanego certyfikatu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik certyfikatu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

Znajdowanie certyfikatu lokalnego w NetX bezpiecznej sesji TLS według nazwy pospolitej

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Opis

Ta usługa umożliwia znalezienie certyfikatu w magazynie certyfikatów urządzeń lokalnych sesji TLS i zwrócenie wskaźnika do struktury NX_SECURE_X509_CERT w sklepie. Parametr common_name i jego długość (name_length) służą do identyfikowania certyfikatu w magazynie przez dopasowanie pola nazwy pospolitej tematu dla certyfikatu X. 509.

Jeśli istnieje więcej niż jeden certyfikat o tej samej nazwie pospolitej, tylko pierwszy z nich zostanie zwrócony — zamiast tego użyj *nx_secure_tls_server_certificate_find* .

> [!IMPORTANT]
> *Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a nx_secure_tls_local_certificate_add indeksy na podstawie nazwy pospolitej X. 509. Lokalne usługi certyfikatów zapewniają wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certyfikat** Zwróć wskaźnik do zgodnego certyfikatu.
- **common_name** Nazwa pospolita do dopasowania (nazwa DNS).
- **name_length** Długość common_name danych ciągu.

### <a name="return-values"></a>Wartości zwrócone

- Znaleziono certyfikat **NX_SUCCESS** (0x00) i wskaźnik został zwrócony w parametrze "Certificate".
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) nie znaleziono certyfikatu o podanej nazwie pospolitej.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja TLS, wskaźnik certyfikatu lub ciąg nazwy pospolitej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

Usuń certyfikat lokalny z bezpiecznej sesji protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie certyfikatu lokalnego z sesji TLS, które zostało podżądane dla pola Nazwa pospolita w certyfikacie.

> [!IMPORTANT]
> *Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a nx_secure_tls_local_certificate_add indeksy na podstawie nazwy pospolitej X. 509. Lokalne usługi certyfikatów zapewniają wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **common_name** Wartość nazwy pospolitej certyfikatu do usunięcia.
- **common_name_length** Długość ciągu nazwy pospolitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- Nie znaleziono certyfikatu **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

Obliczanie rozmiaru metadanych kryptograficznych dla sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Opis

Ta usługa oblicza i zwraca rozmiar metadanych kryptograficznych wymaganych dla określonej sesji TLS i tabeli kryptografii TLS (zobacz sekcję "Inicjowanie protokołu TLS z metodami kryptograficznymi", aby uzyskać więcej informacji na temat tabeli szyfrowania kryptograficznego).

Ta usługa powinna zostać wywołana z żądaną tabelą kryptograficzną, aby obliczyć rozmiar buforu metadanych przekazaną do nx_secure_tls_session_create.

### <a name="parameters"></a>Parametry

- **crypto_table** Wskaźnik do kompletnej tabeli kryptografii Secure TLS NetX.
- **metadata_size** Dane wyjściowe obliczeń rozmiaru w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie obliczyć rozmiar metadanych.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa tabela kryptograficzna lub wskaźnik zwracanego rozmiaru.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Oblicz wartość skrótu procedur NetX Secure Library

### <a name="prototype"></a>Prototype

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a>Opis

Ta usługa Inicjuje moduł bezpiecznego protokołu TLS NetX. Musi zostać wywołana przed uzyskaniem dostępu do innych zabezpieczonych usług NetX.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Przydziel pakiet dla sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji protokołu TLS z określonego NX_PACKET_POOL. Ta usługa powinna być wywoływana przez aplikację w celu przydzielenia pakietów danych do wysłania przez połączenie TLS. Sesja TLS musi zostać zainicjowana przed wywołaniem tej usługi.

Przydzielony pakiet jest prawidłowo zainicjowany, aby dane nagłówka i stopki TLS mogły zostać dodane po wypełnieniu danych pakietu. Zachowanie jest takie samo jak *nx_packet_allocate*.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma zostać przydzielony pakiet.
- **packet_ptr** Wskaźnik wyjściowy do nowo przydzielonych pakietów.
- **WAIT_OPTION** Opcja zawieszenia dla przydziału pakietu.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).
- Alokacja podstawowego pakietu **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

Dodaj klucz wstępny do NetX bezpiecznej sesji TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku kontroli sesji protokołu TLS. PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **pre_shared_key** Rzeczywista wartość klucza PSK.
- **psk_length** Długość wartości klucza PSK.
- **psk_identity** Ciąg służący do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości PSK.
- **Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

Przydzielanie miejsca dla certyfikatu dostarczonego przez hosta zdalnego protokołu TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Opis

Ta usługa dodaje niezainicjowane wystąpienie struktury NX_SECURE_X509_CERT do sesji protokołu TLS w celu przydzielenia miejsca dla certyfikatów dostarczonych przez hosta zdalnego podczas sesji TLS. Dane certyfikatu zdalnego są analizowane przez NetX Secure TLS i te informacje są używane do wypełniania wystąpienia struktury certyfikatu przekazanego do tej funkcji. Certyfikaty dodane w ten sposób są umieszczane na liście połączonej.

Jeśli oczekujesz, że host zdalny udostępni wiele certyfikatów, ta funkcja powinna być wywoływana wielokrotnie w celu przydzielenia miejsca dla wszystkich certyfikatów. Dodatkowe certyfikaty są dodawane na końcu listy połączonej z certyfikatem.

Niepowodzenie przydzielenia certyfikatu zdalnego spowoduje niepowodzenie trybu klienta protokołu TLS w trakcie uzgadniania TLS, chyba że jest używany klucz wstępny (PSK) ciphersuite.

Parametr *raw_certificate_buffer* wskazuje miejsce przydzielenia do przechowywania przychodzącego certyfikatu zdalnego. Typowe certyfikaty z kluczami RSA 2048 bitów przy użyciu algorytmu SHA-256 są w zakresie od 1000-2000 bajtów. Bufor powinien być wystarczająco duży, aby zmniejszyć rozmiar, ale w zależności od tego, czy certyfikaty hosta zdalnego mogą być znacznie mniejsze lub większe. Należy pamiętać, że jeśli bufor jest za mały, aby pomieścić certyfikat przychodzący, uzgadnianie TLS zakończy się błędem.

W przypadku trybu serwera TLS niezbędna jest alokacja certyfikatu zdalnego tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu klienta.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certificate_ptr** Wskaźnik do niezainicjowanego wystąpienia certyfikatu X. 509.
- **raw_certificate_buffer** Wskaźnik do bufora, aby przechowywać nieanalizowany certyfikat otrzymany z hosta zdalnego.
- **raw_buffer_size** Rozmiar nieprzetworzonego bufora certyfikatów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne przypisanie certyfikatu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) dostarczony bufor jest zbyt mały.
- **NX_INVALID_PARAMETERS** (0x4D) próbował dodać nieprawidłowy certyfikat.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize,
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta protokołu TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa przydziela miejsce do przetwarzania łańcuchów certyfikatów przychodzących z hostów serwera zdalnego w celu przeprowadzenia uwierzytelniania X. 509 i weryfikacji w wystąpieniu klienta TLS. W przypadku trybu serwera TLS, alokacja certyfikatów zdalnych jest wymagana tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu X. 509 w przypadku serwera TLS, zamiast tego należy użyć *nx_secure_tls_session_x509_client_verify_configure* usługi.

Niepowodzenie przydzielenia certyfikatów zdalnych spowoduje niepowodzenie trybu klienta protokołu TLS w trakcie uzgadniania TLS, chyba że jest używany klucz wstępny (PSK) ciphersuite.

Parametr *certificate_buffer* wskazuje miejsce przydzielenia do przechowywania przychodzących certyfikatów zdalnych i bloków sterowania wymaganych przez te certyfikaty. Bufor zostanie podzielony przez liczbę certyfikatów (*certs_number*) o równej części danego certyfikatu. Parametr *buffer_size*  wskazuje rozmiar buforu. Wymaganą ilość miejsca można znaleźć za pomocą następującej formuły:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Typowe certyfikaty z kluczami RSA 2048 bitów przy użyciu algorytmu SHA-256 są w zakresie od 1000-2000 bajtów. Bufor powinien być wystarczająco duży, aby zmniejszyć rozmiar każdego certyfikatu, ale w zależności od tego, czy certyfikaty hosta zdalnego mogą być znacznie mniejsze lub większe. Należy pamiętać, że jeśli bufor jest za mały, aby pomieścić certyfikat przychodzący, uzgadnianie TLS zakończy się błędem.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.
- **certificate_buffer** Wskaźnik do buforu w celu przechowywania certyfikatów odebranych z hosta zdalnego.
- **buffer_size** Rozmiar buforu certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne przypisanie certyfikatu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik buforu.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) dostarczony bufor jest zbyt mały.
- **NX_INVALID_PARAMETERS** (0x4D) bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

Wolne miejsce przydzielono dla certyfikatów przychodzących

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa służy do zwalniania wszystkich buforów certyfikatów przypisywanych do określonej sesji TLS przez nx_secure_tls_remote_certificate_allocated, zwracając je do wolnego obszaru certyfikatu tej sesji. Może to być konieczne, jeśli aplikacja ponownie używa obiektu sesji protokołu TLS bez usuwania go i ponownego tworzenia przy użyciu nx_secure_tls_session_delete i nx_secure_tls_session_create.

Należy pamiętać, że zdalne miejsce na certyfikacie jest automatycznie odzyskiwane w przypadku zresetowania sesji TLS w nx_secure_tls_session_end tak, aby większość aplikacji nie wymagała wywołania tej usługi.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- Operacja powiodła się **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- Błąd wewnętrzny **NX_INVALID_PARAMETERS** (0x4D) — magazyn certyfikatów jest niemożliwy do uszkodzenia.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

Dodawanie certyfikatu przeznaczonego dla serwerów TLS przy użyciu identyfikatora liczbowego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Opis

Ta usługa służy do dodawania certyfikatu do lokalnego magazynu sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu tematu X. 509 (nazwa pospolita) w ramach certyfikatu. Identyfikator liczbowy jest oddzielony od certyfikatu i umożliwia dodawanie wielu certyfikatów jako certyfikatów tożsamości do serwera TLS, a także Zezwalanie na dodawanie wielu certyfikatów o tej samej nazwie pospolitej do tego samego lokalnego magazynu sesji protokołu TLS. Ta sama usługa może być używana w przypadku certyfikatów klienta, ale jest rzadki, aby klient TLS miał wiele certyfikatów tożsamości.

Parametr cert_id jest niezerową liczbą całkowitą, która jest przypisana przez aplikację. Rzeczywista wartość nie ma znaczenia (inne niż zero), ale musi być unikatowa w magazynie dla podanej sesji TLS. Wartość cert_id może służyć do znajdowania i usuwania certyfikatów z lokalnego magazynu przy użyciu odpowiednio nx_secure_tls_server_certificate_find i nx_secure_tls_server_certificate_remove.

> [!IMPORTANT]
> *Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu oraz lokalnego indeksu usług certyfikatów na podstawie nazwy pospolitej X. 509. Usługi certyfikatów serwera umożliwiają istnienie wielu certyfikatów z danymi udostępnionymi (szczególnie nazwa pospolita) w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowanego wystąpienia certyfikatu X. 509.
- **Cert_ID** Dodatni, niezerowy, relatywnie unikatowy numer IDENTYFIKACYJNy certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- Operacja powiodła się **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik ORCERTIFICATE sesji TLS.
- **NX_SECURE_TLS_CERT_ID_INVALID** (0x138) podany identyfikator certyfikatu ma nieprawidłową wartość (najkorzystniej wynosi 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) podany identyfikator certyfikatu już istnieje w magazynie lokalnym.
- **NX_INVALID_PARAMETERS (0x4D)** Błąd wewnętrzny — magazyn certyfikatów jest uszkodzony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Opis

Ta usługa jest używana do znajdowania certyfikatu w lokalnym magazynie sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu tematu X. 509 (nazwa pospolita) w certyfikacie.

Cert_id parametr to niezerową dodatnia liczba całkowita przypisana przez aplikację, gdy certyfikat zostanie dodany do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu oraz lokalnego indeksu usług certyfikatów na podstawie nazwy pospolitej X. 509. Usługi certyfikatów serwera umożliwiają istnienie wielu certyfikatów z danymi udostępnionymi (szczególnie nazwa pospolita) w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certyfikat** Wskaźnik na wskaźnik certyfikatu X. 509, aby zwrócić odwołanie do znalezionego certyfikatu.
- **Cert_ID** Wartość identyfikatora certyfikatu o wartości innej niż zero.

### <a name="return-values"></a>Wartości zwrócone

- Operacja powiodła się **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik certyfikatu.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) podany identyfikator certyfikatu nie jest zgodny z żadnym z magazynów lokalnych podanej sesji TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Opis

Ta usługa służy do usuwania certyfikatu z lokalnego magazynu sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu tematu X. 509 (nazwa pospolita) w ramach certyfikatu.

Cert_id parametr to niezerową dodatnia liczba całkowita przypisana przez aplikację, gdy certyfikat zostanie dodany do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **Cert_ID** Wartość identyfikatora certyfikatu o wartości innej niż zero.

### <a name="return-values"></a>Wartości zwrócone

- Operacja powiodła się **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) podany identyfikator certyfikatu nie jest zgodny z żadnym z magazynów lokalnych podanej sesji TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

Pobierz wartość i poziom alertu TLS wysyłanego przez hosta zdalnego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Opis

Ta usługa jest używana do pobierania poziomu alertu TLS i wartości, gdy host zdalny wysyła alert w odpowiedzi na jakiś problem lub błąd.

Wartości parametrów alert_level i alert_value są prawidłowe tylko wtedy, gdy ta funkcja jest wywoływana natychmiast po wywołaniu interfejsu API TLS, który zwrócił stan NX_SECURE_TLS_ALERT_RECEIVED (0x114) wskazujący, że odebrano alert z hosta zdalnego.

Należy pamiętać, że jeśli protokół TLS hosta lokalnego wysyła alert, zwracane kody błędów są znacznie bardziej opisowe dla samego błędu niż alert protokołu TLS, ponieważ wartości alertów protokołu TLS zostały celowo pozostawione niejednoznaczne, aby zapobiec pewnym typom ataków (np. "uzupełnianie" lub "uzupełnienie").

Poziom alertu przyjmuje tylko jedną z dwóch wartości: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) lub NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2). Ogólnie rzecz biorąc, tylko alert CloseNotify (używany do wskazania pomyślne zakończenie sesji TLS) otrzyma poziom "ostrzeżenie", ale niektóre sytuacje związane z konfiguracją rozszerzeń mogą również być traktowane jako ostrzeżenia. Większość alertów będzie "krytyczna" wskazujących potencjalny błąd zabezpieczeń i powodująca natychmiastowe zamknięcie połączenia TLS (uzgadnianie lub sesja).

Wartości alertów protokołu TLS są zdefiniowane w specyfikacjach RFC protokołu TLS. Oto listę z RFC 5246 (TLSv 1.2) dla celów informacyjnych:

| Nazwa alertu                     | Wartość | Opis                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Brak błędów, wskazuje pomyślne zakończenie sesji                                                                                                                   |
| unexpected_message            | 10    | Protokół TLS odebrał nieoczekiwany lub nieaktualny komunikat                                                                                                           |
| bad_record_mac               | 20    | Nie można zweryfikować odszyfrowania i/lub komputera MAC                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **Przestarzałe** Odszyfrowanie nie powiodło się (przestarzałe z powodu dopełnienia ataków Oracle)                                                                                      |
| record_overflow               | 22    | Odebrano rekord, który jest większy niż maksymalny rozmiar rekordu TLS                                                                                        |
| decompression_failure         | 30    | Wystąpił problem podczas kompresji/dekompresji rekordu TLS                                                                                       |
| handshake_failure             | 40    | Wystąpił nieokreślony błąd uzgadniania, który nie jest objęty innym alertem                                                                            |
| no_certificate_RESERVED      | 41    | **Przestarzałe** w protokole TLS (tylko protokół SSL)                                                                                                                                 |
| bad_certificate               | 42    | Otrzymany certyfikat zawiera nieprawidłowe formatowanie lub podpisy                                                                                   |
| unsupported_certificate       | 43    | Odebrano certyfikat z nieprawidłowym typem (np. certyfikat tylko do podpisywania używany do uwierzytelniania serwera TLS)                                    |
| certificate_revoked           | 44    | Stan certyfikatu (podany przez listę CRL lub OCSP) został wskazany jako "odwołany"                                                                       |
| certificate_expired           | 45    | Otrzymany certyfikat był poza prawidłowym zakresem dat (nie jest jeszcze prawidłowy lub wygasł)                                                                 |
| certificate_unknown           | 46    | Napotkano nieznany problem z certyfikatem, który nie został objęty innymi alertami                                                                          |
| illegal_parameter             | 47    | Niektóre konfiguracje lub negocjowane wartości w uzgadnianiu protokołu TLS były nieprawidłowe lub poza zakresem                                                                      |
| unknown_ca                    | 48    | Nie można śledzić otrzymanego certyfikatu tożsamości za pośrednictwem łańcucha certyfikatów do certyfikatu zaufanego głównego urzędu certyfikacji.                                              |
| access_denied                 | 49    | Wskazuje, że odebrano prawidłowy certyfikat, ale kontrola dostępu do aplikacji wskazywała, że certyfikat był nieprawidłowy dla żądanych zasobów.            |
| decode_error                  | 50    | Niektóre pola lub wartości w nagłówku TLS lub komunikacie uzgadniania są poza zakresem lub nieprawidłowe, co prowadzi do błędu podczas dekodowania rekordu TLS.                      |
| decrypt_error                 | 51    | Nie można zweryfikować skrótu do sygnatury lub zakończonego komunikatu podczas uzgadniania protokołu TLS.                                                                         |
| export_restriction_RESERVED  | 60    | PRZESTARZAŁe w TLSv 1.2                                                                                                                                        |
| protocol_version              | 70    | Wersja protokołu TLS negocjowana podczas uzgadniania jest rozpoznawana, ale nie jest obsługiwana (np. TLSv 1.0 została przedstawiona, ale nie została włączona).                       |
| insufficient_security         | 71    | Wysyłany za każdym razem, gdy uzgadnianie nie powiedzie się z powodu braku bezpiecznych szyfrów (np. rozmiar klucza jest zbyt mały dla wymagań aplikacji)                                |
| internal_error                | 80    | Wystąpił błąd niezwiązany z protokołem TLS (np. problemy z alokacją pamięci, problemy z aplikacją), co spowodowało przerwaną sesję protokołu TLS.                                         |
| user_canceled                 | 90    | Zwracany, jeśli sesja TLS została anulowana przez użytkownika lub aplikację przed ukończeniem uzgadniania (podobnego do CloseNotify).                                 |
| no_renegotiation              | 100   | Indiates, że host zdalny nie chce wykonać uzgadniania renegocjacji protokołu TLS w odpowiedzi na żądanie ponownego negocjowania.                                 |
| unsupported_extension         | 110   | Wysyłany, gdy klient TLS odbiera ServerHello z rozszerzeniami, które nie są jawnie zadawane w początkowej komunikacie ClientHello (wskazuje na to, że wystąpił problem z serwerem). |

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **alert_level** Zwróć poziom odebranego alertu (ostrzeżenie lub krytyczny).
- **alert_value** Zwraca wartość otrzymanego alertu (patrz tabela).

### <a name="return-values"></a>Wartości zwrócone

- Operacja powiodła się **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

Konfigurowanie wywołania zwrotnego protokołu TLS do użycia na potrzeby dodatkowej weryfikacji certyfikatu

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wskaźnik funkcji do sesji protokołu TLS, która będzie wywoływała protokół TLS w przypadku odebrania certyfikatu z hosta zdalnego, co umożliwia aplikacji wykonywanie testów weryfikacji, takich jak Walidacja DNS, Odwoływanie certyfikatów i wymuszanie zasad certyfikatów.

NetX Secure TLS będzie przeprowadzać podstawowe sprawdzanie poprawności ścieżki X. 509 na certyfikacie przed wywołaniem wywołania zwrotnego w celu zapewnienia, że certyfikat może być śledzony do certyfikatu w magazynie zaufanych certyfikatów TLS, ale wszystkie inne walidacje będą obsługiwane przez to wywołanie zwrotne.

Wywołanie zwrotne udostępnia wskaźnik sesji TLS i wskaźnik do certyfikatu tożsamości hosta zdalnego (liścia w łańcuchu certyfikatów). Wywołanie zwrotne powinno zwracać NX_SUCCESS, jeśli sprawdzanie poprawności zakończy się powodzeniem, w przeciwnym razie powinna zwrócić kod błędu wskazujący błąd walidacji. Każda wartość inna niż NX_SUCCESS spowoduje natychmiastowe przerwanie uzgadniania protokołu TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego walidacji certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne alokacja wskaźnika funkcji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

Konfigurowanie wywołania zwrotnego protokołu TLS do wywołania na początku uzgadniania klienta TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływała protokół TLS, gdy uzgadnianie klienta TLS odebrało komunikat ServerHelloDone. Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie wszelkich rozszerzeń TLS z odebranego komunikatu ServerHello, który wymaga wprowadzenia danych lub podejmowania decyzji.

Wywołanie zwrotne jest wykonywane z wywoływaniem bloku sterowania sesją TLS i tablicą obiektów NX_SECURE_TLS_HELLO_EXTENSION. Tablica obiektów rozszerzeń jest przeznaczona do przekazywania do funkcji pomocnika, która będzie znajdować i analizować określone rozszerzenie. Obecnie nie ma określonych rozszerzeń, które są obsługiwane w NetX Secure, które wymagają danych wejściowych klienta TLS, ale wywołanie zwrotne jest dostępne dla projektantów aplikacji obsługujących niestandardowe lub nowe rozszerzenia, które mogą stać się dostępne. Przykładowa funkcja pomocnicza, która analizuje rozszerzenia protokołu TLS podane w komunikatach Hello, znajduje się w temacie *nx_secure_tls_session_sni_extension_parse*.

Wywołania zwrotnego klienta można również użyć do wybrania aktywnego certyfikatu tożsamości przy użyciu *nx_secure_tls_active_certificate_set* dla klienta protokołu TLS w przypadku, gdy serwer zdalny zażądał certyfikatu i podano informacje umożliwiające klientowi protokołu TLS wybranie określonego certyfikatu. Aby uzyskać więcej informacji, zobacz informacje o nx_secure_tls_active_certificate_set.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego klienta TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne alokacja wskaźnika funkcji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

Włącz weryfikację klienta X. 509 i Przydziel miejsce dla certyfikatów klienta

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa umożliwia opcjonalne uwierzytelnianie klienta X. 509 dla wystąpienia serwera TLS. Przydziela również miejsce niezbędne do przetwarzania łańcuchów certyfikatów przychodzących z hosta klienta zdalnego. Certyfikaty dostarczone przez klienta zdalnego zostaną zweryfikowane względem zaufanych certyfikatów wystąpienia serwera TLS przypisane do usługi *nx_secure_tls_trusted_certificate_add.*

W przypadku trybu klienta protokołu TLS wymagane jest przydzielenie certyfikatu zdalnego, a w zamian należy użyć *nx_secure_tls_remote_certificate_buffer_allocate* usługi. Włączenie uwierzytelniania klienta X. 509 w wystąpieniu klienta TLS nie będzie miało żadnego efektu.

Parametr *certificate_buffer* wskazuje miejsce przydzielenia do przechowywania przychodzących certyfikatów zdalnych i bloków sterowania wymaganych przez te certyfikaty. Bufor zostanie podzielony przez liczbę certyfikatów (*certs_number*) o równej części danego certyfikatu. Parametr *buffer_size* wskazuje rozmiar buforu. Wymaganą ilość miejsca można znaleźć za pomocą następującej formuły:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Typowe certyfikaty z kluczami RSA 2048 bitów przy użyciu algorytmu SHA-256 są w zakresie od 1000-2000 bajtów. Bufor powinien być wystarczająco duży, aby zmniejszyć rozmiar każdego certyfikatu, ale w zależności od tego, czy certyfikaty hosta zdalnego mogą być znacznie mniejsze lub większe. Należy pamiętać, że jeśli bufor jest za mały, aby pomieścić certyfikat przychodzący, uzgadnianie TLS zakończy się błędem.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.
- **certificate_buffer** Wskaźnik do buforu w celu przechowywania certyfikatów odebranych z hosta zdalnego.
- **buffer_size** Rozmiar buforu certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne przypisanie certyfikatu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik buforu.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) dostarczony bufor jest zbyt mały.
- **NX_INVALID_PARAMETERS** (0x4D) bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

Wyłączanie uwierzytelniania certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS. Aby uzyskać więcej informacji, zobacz nx_secure_tls_session_client_verify_enable.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna zmiana stanu **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

Włącz uwierzytelnianie certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS. Włączenie uwierzytelniania certyfikatu klienta dla wystąpienia serwera TLS spowoduje, że serwer TLS zażąda certyfikatu od dowolnego klienta zdalnego protokołu TLS podczas początkowego uzgadniania protokołu TLS. Certyfikat otrzymany od zdalnego klienta protokołu TLS jest dołączany przez komunikat CertificateVerify, którego serwer TLS używa do sprawdzenia, czy klient jest właścicielem certyfikatu (ma dostęp do klucza prywatnego skojarzonego z tym certyfikatem).

Jeśli podany certyfikat może zostać zweryfikowany i wyśledzony z powrotem do certyfikatu w zaufanym magazynie certyfikatów serwera TLS za pośrednictwem łańcucha certyfikatów X. 509, zdalny klient protokołu TLS jest uwierzytelniany, a uzgadnianie jest przeprowadzane. W przypadku wystąpienia błędów podczas przetwarzania certyfikatu lub komunikatu CertificateVerify, uzgadnianie TLS zostanie zakończone z błędem.

> [!NOTE]
> *Serwer TLS musi mieć co najmniej jeden certyfikat w zaufanym magazynie, który został dodany do nx_secure_tls_trusted_certificate_add lub uwierzytelnianie będzie zawsze kończyć się niepowodzeniem.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna zmiana stanu **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

Tworzenie bezpiecznej sesji protokołu TLS NetX na potrzeby bezpiecznej komunikacji

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje NX_SECURE_TLS_SESSION wystąpienia struktury do użycia podczas ustanawiania bezpiecznej komunikacji TLS za pośrednictwem połączenia sieciowego.

Metoda przyjmuje NX_SECURE_TLS_CRYPTO obiektu, który jest wypełniony metodami kryptograficznymi, które mają być używane na potrzeby protokołu TLS. *Encryption_metadata_area* wskazuje bufor przydzielony do użycia przez protokół TLS dla "metadanych" używanych przez metody kryptograficzne w tabeli NX_SECURE_TLS_CRYPTO dla obliczeń. Rozmiar tabeli można określić za pomocą usługi nx_secure_tls_metadata_size_calculate. Zobacz sekcję "Kryptografia w NetX Secure TLS" w rozdziale 3, aby uzyskać więcej szczegółów.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **cipher_table** Wskaźnik do metod kryptograficznych protokołu TLS.
- **encryption_metadata_area** Wskaźnik na miejsce dla metadanych kryptografii.
- **encryption_metadata_size** Rozmiar buforu metadanych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.
- **NX_INVALID_PARAMETERS** (0x4D) bufor metadanych był za mały dla określonych metod.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) wymagana Metoda szyfrowania dla włączonej wersji protokołu TLS nie została podana w tabeli szyfru.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- Kryptografia w NetX Secure TLS w rozdziale 3

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

Usuwanie sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa sesję TLS reprezentowaną przez wystąpienie struktury NX_SECURE_TLS_SESSION i zwalnia wszystkie zasoby systemowe należące do tego wystąpienia sesji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

Kończenie aktywnej sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa służy do kończenia sesji TLS reprezentowanej przez wystąpienie struktury NX_SECURE_TLS_SESSION przez wysłanie komunikatu CloseNotify TLS do hosta zdalnego. Następnie usługa czeka na odpowiedź hosta zdalnego przy użyciu własnego komunikatu CloseNotify.

Jeśli host zdalny nie wyśle komunikatu CloseNotify, protokół TLS uważa ten błąd i możliwe naruszenie zabezpieczeń, dlatego należy sprawdzić, czy wartość zwracana jest ważna dla bezpiecznego połączenia. Parametr **WAIT_OPTION** może służyć do kontrolowania, jak długo usługa powinna czekać na odpowiedź przed zwróceniem kontroli do wątku wywołującego.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **WAIT_OPTION** Wskazuje, jak długo usługa powinna oczekiwać na odpowiedź z hosta zdalnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) nie otrzymał odpowiedzi z hosta zdalnego przed upływem limitu czasu.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie może przydzielić pakietu do wysłania wiadomości CloseNotify.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie może wysłać komunikatu CloseNotify przez gniazdo TCP.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

Ustawianie buforu ponownego zestawu pakietów dla sesji bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa kojarzy bufor ponownego asemblowania pakietów z sesją TLS. Aby można było odszyfrować i przeanalizować przychodzące rekordy TLS, dane w każdym rekordzie muszą zostać zebrane z bazowych pakietów TCP. Rekordy TLS mogą być maksymalnie 16 KB (zazwyczaj są znacznie mniejsze), więc mogą nie pasować do pojedynczego pakietu TCP.

Jeśli wiesz, że rozmiar komunikatu przychodzącego będzie mniejszy niż limit rekordu TLS 16 KB, rozmiar buforu może być mniejszy, ale w celu obsłużenia nieznanych danych przychodzących bufor powinien być wykonany tak jak to możliwe. Jeśli rekord przychodzący jest większy niż podany bufor, sesja TLS zakończy się błędem.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **buffer_ptr** Wskaźnik do bufora protokołu TLS, który ma być używany na potrzeby ponownego asemblowania pakietu.
- **buffer_size** Rozmiar podanego buforu w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji buforu lub protokołu TLS.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

Zastąp domyślną wersję protokołu TLS dla sesji Secure TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Opis

Ta usługa zastępuje domyślną (najnowszą) wersję protokołu TLS używaną przez określoną sesję. Pozwala to NetX Secure TLS na używanie starszej wersji protokołu TLS dla określonej sesji TLS bez wyłączania nowszych wersji protokołu TLS w czasie kompilacji. Może to być przydatne w przypadku aplikacji, które mogą wymagać komunikacji z starszym hostem, który nie obsługuje najnowszej wersji protokołu TLS.

> [!IMPORTANT]
> *Począwszy od wersji 5.11 SP3, NetX Secure TLS obsługuje RFC 7507 (patrz Uwaga poniżej), a wszystkie przesłonięcia do starszej wersji za pomocą tego interfejsu API spowoduje, że SCSV zostanie wysłane w komunikacie ClientHello. Jeśli serwer obsługuje nowszą wersję protokołu TLS, a rezerwa SCSV jest dołączana do komunikacie ClientHello, ten serwer przerywa uzgadnianie protokołu TLS z alertem "nieodpowiedni rezerwowy". SCSV jest wysyłana tylko wtedy, gdy przesłonięcia wersji jest starszą wersją protokołu TLS niż włączona (np. w przypadku zastąpienia wersji do protokołu TLS 1,2, nie zostanie wysłany żaden SCSV).*

Prawidłowe wartości parametru protocol_version to następujące makra: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 i NX_SECURE_TLS_VERSION_TLS_1_2.

Makra NX_SECURE_TLS_DISABLE_TLS_1_1 i NX_SECURE_TLS_ENABLE_TLS_1_0 mogą służyć do kontrolowania wersji protokołu TLS, które są kompilowane w aplikacji. Protokół TLS w wersji 1,2 jest zawsze włączony.

Należy pamiętać, że jeśli host zdalny nie obsługuje podanej wersji, połączenie zakończy się niepowodzeniem — tylko podana wersja przesłonięcia zostanie wynegocjowana przez NetX Secure TLS.

> [!IMPORTANT]
> RFC 7507: SCSV rezerwowy protokołu TLS. Ta Specyfikacja RFC została wprowadzona w celu wyeliminowania problemu zabezpieczeń, który był pierwotnie spowodowany przez serwery, które nieprawidłowo obsługiwały negocjowanie obniżenia poziomu protokołu, a zamiast tego odrzucają nieprawidłowe komunikaty komunikacie ClientHello. W przypadku próby zachowania zgodności z tymi starymi serwerami niektóre aplikacje klienckie TLS zaczęły ponawiać próbę niepowodzenia uzgadniania z i starszą wersją protokołu TLS (np. TLS 1,2 nie powiodło się, więc Wypróbuj protokół TLS 1,1). To obejście spowodowało jednak wprowadzenie nowego problemu — atakujący może wymusić obniżenie poziomu klienta, przez sztuczne wprowadzenie do błędu sieci lub pakietu, powodując niepowodzenie połączenia serwera — nawet wtedy, gdy serwer obsługiwał nowszą wersję protokołu TLS. W wyniku obniżenia poziomu do starszej wersji osoba atakująca może wykorzystać luki w tej wersji (protokół SSLv3<sup>21</sup> w szczególności jest to słabe dla ataku POODLE). Aby zapobiec takiej sytuacji, w dokumencie RFC 7507 introdued "Fallback SCSV", pseudo ciphersuite<sup>22</sup> wysłany w komunikacie ClientHello, który POWIADAMIA serwer TLS, gdy klient TLS korzysta z wersji TLS, która nie jest wersją najnowszej wersji. W ten sposób serwer obsługujący nowszą wersję może odrzucić komunikacie ClientHello zawierający rezerwowy SCSV i zapobiec pomyślnym zaatakom na starszą wersję.

21. NetX Secure nie implementuje protokół SSLv3 z powodu istnienia znanych poważnych słabych wad, takich jak POODLE.

22. Pseudo-ciphersuite lub SCSV (sygnalizujący wartość pakietu szyfrowania) to zarezerwowany numer ciphersuite, który jest używany do sygnalizowania z włączonymi implementacjami protokołu TLS o funkcjach, które nie były dostępne w starszych wersjach protokołu TLS. SCSV Fallback i TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) są przykładami.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **protocol_version** Makro wersji protokołu TLS przeznaczone do użycia przez określoną wersję protokołu TLS.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna zmiana stanu **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) znana, ale nieobsługiwana wersja protokołu TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) Nieprawidłowa wersja protokołu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

Odbieranie danych z bezpiecznej sesji protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera dane z określonej aktywnej sesji protokołu TLS, obsługując odszyfrowywanie tych danych przed dostarczeniem ich do obiektu wywołującego w parametrze NX_PACKET. Jeśli żadne dane nie są umieszczane w kolejce w określonej sesji, wywołanie zawiesza się na podstawie podanej opcji oczekiwania.

> [!IMPORTANT]
> *Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **packet_ptr** Wskaźnik do przydzielony wskaźnik pakietu TLS.
- **WAIT_OPTION** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_NO_PACKET** (0X01) nie odebrano żadnych danych.
- **NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) odebrany komunikat nie powiódł się podczas sprawdzania skrótu uwierzytelniania.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrana wiadomość zawierała nieznaną wersję protokołu w nagłówku.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) otrzymał alert protokołu TLS od hosta zdalnego.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

Przypisanie wywołania zwrotnego, które zostanie wywołane na początku ponownej negocjacji sesji

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wywołanie zwrotne do sesji TLS, które zostanie wywołane przy każdym odebraniu pierwszego komunikatu uzgadniania sesji z hosta zdalnego.

Funkcja wywołania zwrotnego służy jako powiadomienie do aplikacji, która rozpoczyna uzgadnianie renegocjacji — aplikacja może zdecydować się na zakończenie sesji TLS przez zwrócenie dowolnej wartości innej niż zero z wywołania zwrotnego, co spowoduje, że protokół TLS zakończy sesję TLS z błędem. Jeśli aplikacja chce kontynuować ponowną negocjację, wywołanie zwrotne powinno zwracać NX_SUCCESS.

> [!NOTE]
> *Ze względu na semantykę renegocjacji protokołu TLS wywołanie zwrotne zostanie wywołane dla NetX bezpiecznego protokołu TLS za każdym razem, gdy HelloRequest zostanie odebrany z serwera zdalnego, ale nie gdy Klient zainicjuje ponowną negocjację. Na serwerach Secure TLS NetX są wywoływane wywołania zwrotne za każdym razem, gdy zostanie odebrana ponowna negocjacja komunikacie ClientHello (wszystkie komunikacie ClientHello odebrane w kontekście aktywnej sesji protokołu TLS). Oznacza to, że wywołanie zwrotne zostanie wywołane niezależnie od tego, czy host zdalny lub lokalna aplikacja zainicjowała ponowną negocjację, ponieważ serwer TLS wyśle HelloRequest, do którego będzie odpowiadał Klient zdalny.*

NetX Secure TLS implementuje rozszerzenie Secure renegocjacji Inidication z RFC 5746, aby upewnić się, że uzgadniania renegocjacji nie podlegają atakom typu man-in-the-middle.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik na wystąpienie sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne przypisanie wywołania zwrotnego.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika dla funkcji wywołania zwrotnego lub sesji TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

Inicjowanie uzgadniania sesji z hostem zdalnym

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa *inicjuje uzgadnianie* sesji z połączonym hostem zdalnego protokołu TLS. Ponowna negocjacja składa się z drugiego uzgadniania protokołu TLS w kontekście wcześniej ustanowionej sesji TLS. Każdy nowy komunikat uzgadniania jest szyfrowany przy użyciu sesji TLS do momentu wygenerowania nowych kluczy sesji i wymiany komunikatów ChangeCipherSpec, podczas gdy nowe klucze są używane do szyfrowania wszystkich komunikatów.

Ponowne negocjowanie można zainicjować w dowolnym momencie po ustanowieniu sesji TLS. Jeśli zostanie podjęta próba ponownej negocjacji podczas uzgadniania protokołu TLS lub przed ustanowieniem sesji TLS, nie zostanie podjęta żadna akcja.

> [!NOTE]
> *Całe uzgadnianie TLS zostanie wykonane, gdy ta usługa zostanie wywołana, co oznacza, że czas na ukończenie i zwrócony stan będą się różnić w zależności od bieżących ustawień protokołu TLS i parametrów sesji.*

NetX Secure TLS implementuje rozszerzenie Secure renegocjacji Inidication z RFC 5746, aby upewnić się, że uzgadniania renegocjacji nie podlegają atakom typu man-in-the-middle.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik na wystąpienie sesji TLS.
- **WAIT_OPTION** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem. Jest ona przenoszona do wszystkich usług NetX w ramach protokołu TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne ponowne negocjowanie.
- **NX_NO_PACKET** (0X01) nie odebrano żadnych danych.
- **NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) odebrany komunikat nie powiódł się podczas sprawdzania skrótu uwierzytelniania.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrana wiadomość zawierała nieznaną wersję protokołu w nagłówku.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) otrzymał alert protokołu TLS od hosta zdalnego.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) lokalna lub zdalna sesja TLS jest nieaktywna, co uniemożliwia ponowne negocjowanie.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) host zdalny nie dostarczył rozszerzenia SCSV lub bezpiecznego ponownego negocjowania, przez co nie można wykonać ponownej negocjacji.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.
- Alokacja podstawowego pakietu **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

Wyczyść i zresetuj bezpieczną sesję protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści sesję protokołu TLS i resetuje stan tak, jakby sesja została właśnie utworzona, a istniejący obiekt sesji TLS może zostać ponownie użyty dla nowej sesji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji protokołu TLS.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

Wysyłanie danych za pomocą zabezpieczonej sesji protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła dane w podanej NX_PACKET, przy użyciu określonej aktywnej sesji protokołu TLS i obsługującej szyfrowanie tych danych przed wysłaniem ich do hosta zdalnego. Jeśli rozmiar okna o ostatnio anonsowanym odbiorniku jest mniejszy niż to żądanie, usługa opcjonalnie zawiesza się na podstawie określonych opcji oczekiwania.

> [!IMPORTANT]
> *Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po przekazaniu.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **packet_ptr** Wskaźnik na pakiet TLS zawierający dane do wysłania.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądanie jest większe niż rozmiar okna odbiornika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_NO_PACKET** (0X01) nie odebrano żadnych danych.
- **NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie można wysłać podstawowego gniazda TCP.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

Skonfiguruj wywołanie zwrotne protokołu TLS do wywołania na początku uzgadniania serwera TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływała protokół TLS, gdy uzgadnianie serwera TLS odebrało komunikat komunikacie ClientHello. Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie wszelkich rozszerzeń TLS z odebranego komunikatu komunikacie ClientHello, który wymaga wprowadzenia danych lub podejmowania decyzji.

Wywołanie zwrotne jest wykonywane z wywoływaniem bloku sterowania sesją TLS i tablicą obiektów NX_SECURE_TLS_HELLO_EXTENSION. Tablica obiektów rozszerzeń jest przeznaczona do przekazywania do funkcji pomocnika, która będzie znajdować i analizować określone rozszerzenie. Przykładowa funkcja pomocnicza, która analizuje rozszerzenia protokołu TLS podane w komunikatach Hello, znajduje się w temacie *nx_secure_tls_session_sni_extension_parse*.

Wywołania zwrotnego serwera można także użyć do wybrania aktywnego certyfikatu tożsamości przy użyciu *nx_secure_tls_active_certificate_set* dla serwera TLS. Ta sytuacja najczęściej występuje w odpowiedzi na rozszerzenie Oznaczanie nazwy serwera (SNI), które umożliwia klientowi protokołu TLS wskazanie serwera, do którego próbuje się skontaktować. Aby uzyskać więcej informacji, zobacz odwołania do *nx_secure_tls_session_sni_extension_parse* i *nx_secure_tls_active_certificate_set* .

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego serwera TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne alokacja wskaźnika funkcji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego z klienta TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji serwera TLS, dodawanego do sesji TLS przy użyciu nx_secure_tls_session_server_callback_set. Wywołanie zwrotne jest wywoływane po odebraniu komunikatu komunikacie ClientHello ze zdalnego klienta protokołu TLS i dostarcza tablicę dostępnych rozszerzeń (oraz liczbę rozszerzeń w tablicy). Tę tablicę i jej długość można przesłać bezpośrednio do tej procedury, aby określić, czy istnieje rozszerzenie SNI (jeśli nie jest, zwracany jest NX_SECURE_TLS_EXTENSION_NOT_FOUND wskazujący, że klient nie zaznaczył rozszerzenia SNI (nie jest to błąd).

Jeśli rozszerzenie SNI zostanie znalezione, nazwa DNS X. 509 dostarczana przez klienta TLS zostanie zwrócona w strukturze dns_name. Obecnie rozszerzenie SNI dostarcza tylko jeden wpis nazwy DNS, który może być używany przez serwer TLS w celu określenia certyfikatu tożsamości do wysłania do zdalnego klienta. * *

Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg UCHAR w polu *nx_secure_x509_dns_name* i długość ciągu nazwy w *nx_secure_x509_dns_name_length*. Makro NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **rozszerzenia** Wskaźnik do tablicy rozszerzeń protokołu TLS Hello (od wywołania zwrotnego sesji).
- **num_extensions** Liczba rozszerzeń w tablicy (od wywołania zwrotnego sesji).
- **dns_name** Zwróć nazwę DNS podaną w rozszerzeniu SNI.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne analizowanie rozszerzenia.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa tablica rozszerzeń lub wskaźnik sesji TLS.
- Nie znaleziono rozszerzenia SNI **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136).
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0X137) SNI format rozszerzenia jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Ustaw nazwę DNS rozszerzenia Oznaczanie nazwy serwera (SNI) na wysyłanie do serwera zdalnego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji klienckiej TLS dostarczenie preferowanej nazwy serwera DNS do zdalnego serwera TLS przy użyciu rozszerzenia TLS Oznaczanie nazwy serwera (SNI). Rozszerzenie SNI umożliwia serwerowi wybór właściwego certyfikatu tożsamości i parametrów na podstawie preferencji wskazanego serwera klienta. Rozszerzenie SNI obecnie obsługuje tylko pojedynczą nazwę DNS do wysłania, w związku z czym parametr nazwy pojedynczej. Parametr dns_name musi być zainicjowany przy użyciu *nx_secure_x509_dns_name_initialize* i będzie zawierać preferowany serwer klienta. Aby cofnąć nazwę rozszerzenia, po prostu Wywołaj tę usługę przy użyciu wartości parametru "dns_name" NX_NULL.

Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg UCHAR w polu  *nx_secure_x509_dns_name* i długość ciągu nazwy w *nx_secure_x509_dns_name_length*. Makro NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name.

> [!NOTE]
> *Ta procedura musi zostać wywołana przed wywołaniem nx_secure_tls_session_start lub komunikacie ClientHello nie będzie zawierać rozszerzenia SNI.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **dns_name** Nazwa DNS dostarczana przez aplikację.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie nazwy serwera DNS.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa nazwa DNS lub wskaźnik sesji TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

Rozpocznij sesję bezpiecznego protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję protokołu TLS przy użyciu dostarczonego bloku kontroli sesji TLS i połączonego gniazda TCP. Połączenie TCP musi być już zakończone po pomyślnym wywołaniu do nx_tcp_client_socket_connect lub nx_tcp_server_socket_accept.

Ta usługa określi typ sesji TLS (klienta lub serwera) z gniazda TCP.

Opcja oczekiwania definiuje, jak działa usługa, gdy uzgadnianie TLS jest w toku.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **tcp_socket_ptr** Wskaźnik do połączonego gniazda TCP.
- **WAIT_OPTION** Definiuje sposób zachowania usługi podczas uzgadniania protokołu TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) otrzymany typ komunikatu TLS jest niepoprawny.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.
- Przetwarzanie komunikatu **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) podczas UZGADNIANIA protokołu TLS nie powiodło się.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) komunikat przychodzący nie powiódł się podczas sprawdzania skrótu Mac.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie można wysłać podstawowego gniazda TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) komunikat przychodzący miał nieprawidłową długość pola.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) odebrana wiadomość ChangeCipherSpec jest niepoprawna.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) przychodzący certyfikat TLS nie nadaje się do identyfikacji serwera zdalnego protokołu TLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) szyfrowanie klucza publicznego dostarczone przez hosta zdalnego nie jest obsługiwane.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) host zdalny nie wskazywał ciphersuites, które są obsługiwane przez stos NetX Secure TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrany komunikat TLS miał nieznaną wersję protokołu TLS w jego nagłówku.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) odebrany komunikat TLS miał znaną, ale nieobsługiwaną wersję protokołu TLS w jego nagłówku.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się wewnętrzna alokacja pakietu TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny dostarczył nieprawidłowy certyfikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) wpis w tabeli ciphersuite ma wskaźnik funkcji o wartości null.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) zdalna komunikacie CLIENTHELLO protokołu TLS obejmowała rezerwowe SCSV andattempted w wersji rezerwowej.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

Przypisywanie funkcji sygnatury czasowej do NetX bezpiecznej sesji TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Opis

Ta funkcja konfiguruje wskaźnik funkcji, który zostanie wywołany przez protokół TLS, gdy musi on uzyskać bieżący czas, który jest używany w różnych komunikatach uzgadniania protokołu TLS i w celu weryfikacji certyfikatów.

Oczekiwane jest, że funkcja zwraca bieżącą wartość GMT w formacie systemu UNIX 32-bitowym (sekundy od północy od 1 stycznia 1970, czas UTC, w sekundach), zgodnie z wymaganiami komunikacie ClientHello zawartymi w specyfikacji TLS RFC 5246.

Jeśli nie zostanie przypisana żadna funkcja znacznika czasu, zostanie użyta wartość 0 dla sygnatury czasowej w uzgadnianiu TLS, a sprawdzanie wygaśnięcia certyfikatu nie będzie działać.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **time_func_ptr** Wskaźnik do funkcji zwracającej bieżący czas (GMT) w formacie systemu UNIX 32-bitowym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji protokołu TLS.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

Dodaj zaufany certyfikat do NetX bezpiecznej sesji TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje zainicjowane wystąpienie struktury NX_SECURE_X509_CERT do sesji TLS. Ten certyfikat jest używany przez stos TLS do weryfikowania certyfikatów dostarczonych przez hosta zdalnego podczas uzgadniania protokołu TLS.

Certyfikaty zaufane są wymagane dla trybu klienta protokołu TLS.

Certyfikaty zaufane są wymagane tylko w trybie serwera TLS, jeśli jest włączone uwierzytelnianie certyfikatu klienta.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **certificate_ptr** Wskaźnik do zainicjowane wystąpienie certyfikatu TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.
- **NX_INVALID_PARAMETERS** (0x4D) próbował dodać nieprawidłowy certyfikat.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

Usuń zaufany certyfikat z bezpiecznej sesji protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Opis

Ta usługa usuwa zaufany certyfikat z sesji TLS, który został utworzony w polu Nazwa pospolita w certyfikacie.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.
- **common_name** Wartość nazwy pospolitej certyfikatu do usunięcia.
- **common_name_length** Długość ciągu nazwy pospolitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.
- Nie znaleziono certyfikatu **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

Zainicjuj certyfikat X. 509 dla usługi NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a>Opis

Ta usługa inicjuje strukturę NX_SECURE_X509_CERT z certyfikatu cyfrowego X. 509 kodowanego binarnie do użycia w sesji TLS.

Dane certyfikatu **muszą** być prawidłowym certyfikatem cyfrowym X. 509 w formacie binarnym SZYFROWANYm algorytmem DER. Dane mogą zostać określone z dowolnego źródła (np. systemu plików, skompilowanego stałego buforu itp.), o ile jest dostępny wskaźnik UCHAR do tych danych.

Parametr *raw_data_buffer* i jego rozmiar są opcjonalnymi parametrami, które określają dedykowany bufor, do którego kopiowane są dane certyfikatu przed rozpoczęciem analizy. Jeśli raw_data_buffer jest przenoszona jako NX_NULL, struktura NX_SECURE_X509_CERT będzie wskazywała bezpośrednio na tablicę certificate_data (buffer_size w tym przypadku jest ignorowana). Jeśli raw_data_buffer jest przenoszona jako NX_NULL ***, nie należy modyfikować*** danych wskazywanych przez wskaźnik certificate_data lub przetwarzanie certyfikatu prawdopodobnie zakończy się niepowodzeniem.

Parametr klucza prywatnego dotyczy lokalnych certyfikatów tożsamości — klucz prywatny jest używany przez serwery do odszyfrowywania danych klucza przychodzącego z klienta (szyfrowany przy użyciu klucza publicznego serwera) oraz przez klientów, aby zweryfikować swoją tożsamość na serwerze, gdy serwer żąda certyfikatu klienta. Dodanie klucza prywatnego z tym interfejsem API spowoduje automatyczne oznaczenie skojarzonego certyfikatu jako certyfikatu tożsamości dla aplikacji TLS. W przypadku inicjowania certyfikatów do innych celów (np. zaufanych magazynów) parametr *private_key_data* powinien zostać przekazana jako wartość NULL, *private_key_data_length* jako 0 i *private_key_type* powinien zostać przesłany jako NX_SECURE_X509_KEY_TYPE_NONE.

Parametr *private_key_type* wskazuje formatowanie klucza prywatnego. Na przykład jeśli klucz prywatny jest zakodowanym algorytmem DER w formacie PKCS # 1 — kluczem prywatnym RSA, private_key_type powinny być przesyłane jako NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, typ znany NetX Secure, który zostanie natychmiast przeanalizowany i zapisany do późniejszego użycia.

Private_key_type obsługuje również typy kluczy zdefiniowane przez użytkownika<sup>23</sup> dla platform i aplikacji, które mają określone formaty kluczy lub inne wymagania. Na przykład aparat szyfrowania sprzętowego może używać określonego formatu, który nie jest rozpoznawany przez NetX bezpieczne oprogramowanie, lub klucz prywatny może być zaszyfrowany lub reprezentowany przez token kryptograficzny, tak jak w przypadku sprzętu kryptograficznego w ramach programu Trusted Platform Module (TPM) lub PKCS # 11. Gdy używany jest typ klucza zdefiniowany przez użytkownika, dane klucza są przekazywane Verbatim do odpowiedniej procedury kryptograficznej — na przykład klucz prywatny RSA zostałby przekazana, bez analizy lub przetwarzania bezpośrednio do procedury kryptograficznej RSA dostarczonej do protokołu TLS w tabeli ciphersuite. Typ klucza zdefiniowany przez użytkownika jest również przekazywane do procedury kryptograficznej (w przypadku użycia algorytmu RSA jest to parametr "op").

Zakres kluczy zdefiniowanych przez użytkownika obejmuje najwyższą połowę 32-bitowej nieoznaczonej liczby całkowitej z 0x0001 0000-0xFFFF. Wartości mniejsze niż 0x0001 0000 są zarezerwowane do bezpiecznego użycia NetX.

Typy kluczy zdefiniowane przez użytkownika to zaawansowana funkcja, która wymaga użycia niestandardowych procedur kryptograficznych do obsługi danych pierwotnego klucza prywatnego. Jeśli potrzebujesz tej funkcji, skontaktuj się z przedstawicielem logiki Express.

### <a name="parameters"></a>Parametry

- **certificate_ptr** Wskaźnik do niezainicjowanego wystąpienia certyfikatu X. 509.
- **certificate_data** Wskaźnik do danych binarnych X. 509 zakodowanych algorytmem DER.
- **raw_data_buffer** Wskaźnik na opcjonalny dedykowany bufor danych certyfikatów.
- **buffer_size** Rozmiar opcjonalnego dedykowanego buforu danych certyfikatów.
- **certificate_data_length** Długość danych binarnych certyfikatu w bajtach.
- **private_key_data** Wskaźnik na opcjonalne dane klucza prywatnego.
- **private_key_data_length** Długość danych klucza prywatnego.
- **private_key_type** Identyfikator typu klucza.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.
- Dane certyfikatu X. 509 **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) nie zawierają ZAKODOWANego algorytmem DER.
- Certyfikat **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) nie ma szyfru klucza publicznego, który jest obsługiwany przez NetX Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) klucz prywatny lub certyfikat nie zawiera prawidłowej sekwencji ASN. 1.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) podany klucz prywatny nie jest prawidłowym kluczem RSA PKCS # 1.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) podany typ klucza prywatnego nie został zdefiniowany przez użytkownika i nie jest zgodny z żadnym znanym typem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>Zobacz też

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- Importowanie certyfikatów X. 509 do NetX Secure w rozdziale 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Sprawdź nazwę DNS w odniesieniu do certyfikatu X. 509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Opis

Ta usługa sprawdza nazwę pospolitą certyfikatu względem nazwy domeny najwyższego poziomu (TLD) dostarczonej przez obiekt wywołujący do celów weryfikacji DNS hosta zdalnego. Ta funkcja narzędziowa jest przeznaczona do wywoływania z poziomu procedury wywołania zwrotnego weryfikacji certyfikatu dostarczonej przez aplikację. Nazwa TLD powinna być górną częścią adresu URL służącego do uzyskiwania dostępu do hosta zdalnego ("." -rozdzielany ciąg przed pierwszym ukośnikiem). Jeśli nazwa pospolita zawiera symbol wieloznaczny (na przykład *. example.com), symbol wieloznaczny będzie pasował do dowolnego sufiksu. Należy zauważyć, że tylko pierwszy symbol wieloznaczny ("*") (odczytywanie od prawej do lewej) będzie brany pod uwagę dla dopasowania symboli wieloznacznych — na przykład ABC. *. przykład. com *będzie pasować do* nazwy kończącej się znakiem ". example.com".

Jeśli nazwa pospolita nie pasuje do podanego ciągu, rozszerzenie "subjectAltName" jest analizowane (jeśli istnieje w certyfikacie) i wszystkie wpisy DNSName są również porównywane. Jeśli żadna z tych wpisów nie jest zgodna, zwracany jest błąd.

Ważne jest, aby zrozumieć format nazwy pospolitej (i wpisów subjectAltName) w oczekiwanych certyfikatach. Na przykład niektóre certyfikaty mogą korzystać z surowego adresu IP lub symbolu wieloznacznego. Ciąg TLD DNS musi być sformatowany w taki sposób, aby pasował do oczekiwanych wartości w odebranych certyfikatach.

### <a name="parameters"></a>Parametry

- **certificate_ptr** Wskaźnik na wystąpienie certyfikatu X. 509.
- **dns_tld** Top-Level nazwy domeny do porównania.
- **dns_tld_length** Długość ciągu TLD.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne porównanie **NX_SUCCESS** (0x00) z nazwą pospolitą lub SubjectAltName.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0X195) nie znaleziono zgodnej nazwy.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

Sprawdź certyfikat X. 509 na podanej liście odwołania certyfikatów (CRL)

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Opis

Ta usługa przyjmuje listę odwołania certyfikatów zakodowaną algorytmem DER i wyszukuje określony certyfikat na tej liście. Wystawca listy CRL jest weryfikowany w odniesieniu do podanego magazynu certyfikatów, wystawca listy CRL jest zweryfikowany jako taki sam, jak w przypadku sprawdzanego certyfikatu i numer seryjny certyfikatu jest używany do przeszukiwania listy odwołanych certyfikatów. Jeśli wystawcy są zgodni, podpis wyewidencjonowany i certyfikat **nie** znajduje się na liście, wywołanie zakończyło się pomyślnie. Wszystkie inne przypadki powodują zwrócenie błędu.

### <a name="parameters"></a>Parametry

- **crl_data** Wskaźnik do listy CRL kodowanej algorytmem DER.
- **crl_length** Długość w bajtach danych listy CRL.
- **Magazyn** Wskaźnik do magazynu certyfikatów X. 509.
- **certificate_ptr** Wskaźnik na wystąpienie certyfikatu X. 509.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne sprawdzenie poprawności certyfikatu nie zostało odwołane.
- Nie znaleziono certyfikatu wystawcy listy CRL **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119).
- Nie znaleziono certyfikatu wystawcy certyfikatu **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) numer ASN listy CRL. 1 zawiera pole nieprawidłowej długości.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG (0x189)** Lista CRL zawiera nieprawidłowy numer ASN. 1.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18c) weryfikacja łańcucha certyfikatów nie powiodła się.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0X197) lista CRL i wystawcy certyfikatów nie są zgodne.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) podpis listy CRL był nieprawidłowy.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) sprawdzany certyfikat został znaleziony w liście CRL i dlatego jest odwołany.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

Zainicjuj strukturę nazw DNS X. 509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Opis

Ta usługa inicjuje nazwę DNS X. 509 do użycia z niektórymi usługami interfejsu API wymagającymi określonego formatu nazwy. Na przykład usługa *nx_secure_tls_sni_extension_parse* oczekuje obiektu NX_SECURE_X509_DNS_NAME w celu dopasowania nazwy dostarczonej przez hosta zdalnego w rozszerzeniu oznaczanie nazwy serwera podczas UZGADNIANIA protokołu TLS. Nazwa DNS jest po prostu ciągiem charater o długości — Maksymalna dozwolona długość nazwy DNS (i rozmiar buforu wewnętrznego w NX_SECURE_X509_DNS_NAME) jest kontrolowana przez NX_SECURE_X509_DNS_NAME_MAX makro (domyślnie 100 bajtów).

### <a name="parameters"></a>Parametry

- **dns_name** Struktura nazw DNS do zainicjowania.
- **name_string** Dane ciągu nazwy DNS.
- **Długość** Długość ciągu nazwy.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie zainicjowano **NX_SUCCESS** (0x00).
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) określony ciąg nazwy został przekroczony NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X. 509 w certyfikacie X. 509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)*. Wyszuka określony identyfikator OID rozszerzonego użycia klucza w ramach certyfikatu X. 509 i zwróci, czy identyfikator OID jest obecny. Key_usage parametr to liczba całkowita mapowania identyfikatorów OID, które są używane wewnętrznie przez NetX Secure X. 509 i TLS, aby uniknąć przekazywania ciągów identyfikatorów OID o zmiennej długości jako parametrów.

Odpowiednie identyfikatory OID rozszerzenia rozszerzonego użycia klucza podano w poniższej tabeli. Typowa implementacja klienta TLS, która chce sprawdzić użycie klucza rozszerzonego w otrzymanym certyfikacie serwera TLS, sprawdza obecność identyfikatora OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH — Jeśli rozszerzenie jest obecne, ale nie ma tego identyfikatora OID, certyfikat będzie uznawany za nieprawidłowy dla identyfikowanie hosta jako serwer TLS, a wywołanie zwrotne weryfikacji certyfikatu powinno zwrócić błąd. Jeśli rozszerzenie nie istnieje, wówczas jest do aplikacji, niezależnie od tego, czy należy kontynuować uzgadnianie TLS.

W wywołaniu zwrotnym weryfikacji certyfikatu Kod powrotu błędu NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użytku aplikacji. Jeśli wystąpi błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę niepowodzenia.

| Bezpieczny identyfikator NetX                                | Wartość identyfikatora OID         | Opis                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | Certyfikat może służyć do identyfikowania serwera TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | Certyfikat może służyć do identyfikowania klienta TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | Certyfikat może służyć do podpisywania kodu             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | Certyfikat może służyć do podpisywania wiadomości e-mail           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | Certyfikat może służyć do podpisywania znaczników czasu       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | Certyfikat może służyć do podpisywania odpowiedzi protokołu OCSP   |

Identyfikatory OID i mapowania dla rozszerzenia rozszerzonego użycia klucza X. 509

### <a name="parameters"></a>Parametry

- **certyfikat** Wskaźnik do zweryfikowanego certyfikatu.
- **KEY_USAGE** Mapowanie wartości całkowitej OID z tabeli powyżej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) znaleziono identyfikator OID użycia klucza.
- Napotkano **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 tag wielobajtowy (nieobsługiwany certyfikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) niedozwolone pole ASN. 1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) Nieprawidłowa Klasa tagu ASN. 1 (nieprawidłowy certyfikat).
- Napotkano nieprawidłowe rozszerzenie **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) (nieprawidłowy certyfikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) rozszerzenie rozszerzonego użycia klucza nie zostało znalezione w podanym certyfikacie.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik certyfikatu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

Znajdź i zwróć rozszerzenie X. 509 w certyfikacie X. 509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)* i jest zaawansowaną usługą X. 509.

Funkcja będzie wyszukiwać określone rozszerzenie w ramach certyfikatu X. 509 na podstawie identyfikatora OID i zwracać, czy identyfikator OID jest obecny, wraz ze strukturą zawierającą odwołania do odpowiednich nieprzetworzonych danych rozszerzenia. Extension_id parametr to liczba całkowita mapowania identyfikatorów OID, które są używane wewnętrznie przez NetX Secure X. 509 i TLS, aby uniknąć przekazywania ciągów identyfikatorów OID o zmiennej długości jako parametrów.

Funkcje pomocnika zapewniane dla określonych rozszerzeń (takich jak *nx_secure_x509_key_usage_extension_parse*) nx_secure_x509_extension_find wewnętrznie w celu uzyskania danych rozszerzenia.

Odpowiednie identyfikatory OID dla znanych rozszerzeń X. 509 podano w poniższej tabeli.

Struktura NX_SECURE_X509_EXTENSION zawiera wskaźniki do certyfikatu X. 509, które zezwalają na funkcje pomocnika, takie jak *nx_secure_x509_key_usage_extension_parse* , aby szybko zdekodować dane ASN. 1 ZAKODOWANe algorytmem DER.

Aby uzyskać informacje o określonych rozszerzeniach, zobacz RFC 5280 (Specyfikacja X. 509) lub odwołanie do odpowiednich funkcji pomocnika, jeśli są dostępne.

Bieżąca wersja NetX Secure X. 509 ma ograniczoną obsługę rozszerzeń X. 509. W przyszłości zostaną dodane więcej funkcji pomocnika.

> [!IMPORTANT]
> *Ta usługa jest zaawansowaną funkcją dla użytkowników zaznajomionych z rozszerzeniami X. 509 i numerem ASN szyfrowanym algorytmem DER. 1. Jest udostępniana, aby umożliwić tym użytkownikom dostęp do rozszerzeń, dla których NetX Secure X. 509 nie udostępnia obecnie funkcji pomocnika. W przypadku tych rozszerzeń bez funkcji pomocniczych należy samodzielnie przeanalizować pierwotny numer ASN szyfrowany algorytmem DER. 1.*

| Bezpieczny identyfikator NetX                              | Wartość identyfikatora OID | Opis                                                                    | Funkcja pomocnika? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Atrybuty katalogu — podstawowe atrybuty informacji o podmiotu certyfikatu  | Nie               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Służy do identyfikowania określonego klucza publicznego                                         | Nie               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Zawiera informacje dotyczące prawidłowych użycia klucza publicznego certyfikatu              | Tak              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Zapewnia alternatywne nazwy DNS do identyfikacji certyfikatu                     | Tak<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Udostępnia alternatywne nazwy DNS w celu identyfikowania wystawcy certyfikatu            | Nie               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Zawiera podstawowe informacje o ograniczeniach użycia certyfikatu                        | Nie               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Służy do ograniczania nazw certyfikatów do określonych domen                        | Nie               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Zawiera identyfikatory URI dystrybucji list CRL                                             | Nie               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Lista zasad certyfikatów dla dużych systemów infrastruktury kluczy publicznych                             | Nie               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Lista zasad certyfikatów urzędu certyfikacji                                                | Nie               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Służy do identyfikowania określonego klucza publicznego skojarzonego z podpisem certyfikatu | Nie               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Ograniczenia zasad urzędu certyfikacji                                                          | Nie               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Dodatkowe informacje o użyciu klucza opartego na identyfikatorze OID                                     | Tak              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Zawiera informacje dotyczące uzyskiwania różnicowych list CRL                                  | Nie               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Pole certyfikatu urzędu certyfikacji wskazujące, że nie można użyć AnyPolicy                  | Nie               |

Identyfikatory OID i mapowania dla rozszerzeń X. 509

24. Rozszerzenie SubjectAltName jest analizowane w ramach sprawdzania nazw DNS w usłudze nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Parametry

- **certyfikat** Wskaźnik do zweryfikowanego certyfikatu.
- **rozszerzenie** Zwróć strukturę zawierającą wskaźnik i długość danych rozszerzenia.
- **extension_id** Mapowanie wartości całkowitej OID z tabeli powyżej.

### <a name="return-values"></a>Wartości zwrócone

- Znaleziono identyfikator OID określonego rozszerzenia **NX_SUCCESS** (0x00) i zwrócone dane.
- Napotkano **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 tag wielobajtowy (nieobsługiwany certyfikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) niedozwolone pole ASN. 1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) Nieprawidłowa Klasa tagu ASN. 1 (nieprawidłowy certyfikat).
- Napotkano nieprawidłowe rozszerzenie **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192)
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) nie znaleziono podanego identyfikatora OID rozszerzenia w podanym certyfikacie.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik certyfikatu lub rozszerzenia.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

Znajdź i Przeanalizuj rozszerzenie użycie klucza X. 509 w certyfikacie X. 509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)*. Wyszuka rozszerzenie użycie klucza i jeśli zostanie znalezione, zwróci pole bitowe użycie klucza w parametrze "pole bitowe".

Bity, zgodnie z definicją w specyfikacji X. 509 (RFC 5280), podano w poniższej tabeli. Bitowe i z odpowiednią maską bitową (i sprawdzanie dla wartości innej niż zero) będą mieć wartość każdego bitu.

Należy zauważyć, że kodowanie DER pole bitowe eliminuje dodatkowe zera, więc rzeczywista pozycja bitów w danych pierwotnego certyfikatu będzie prawdopodobnie różna od ich pozycji w zdekodowanym pole bitowe. Podane masek bitowych mają być używane tylko w zdekodowanym pole bitowe zwróconym przez *nx_secure_x509_key_usage_extension_parse* , a nie z danymi certyfikatu z SZYFROWANYm algorytmem DER.

W wywołaniu zwrotnym weryfikacji certyfikatu Kod powrotu błędu NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użytku aplikacji. Jeśli wystąpi błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę niepowodzenia.

| Bezpieczny identyfikator NetX                            | Pozycja bitowa | Opis                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | Certyfikatu można używać na potrzeby podpisów cyfrowych                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | Certyfikat może służyć do weryfikowania podpisów cyfrowych innych niż te dla certyfikatów i list CRL                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | Certyfikatu można użyć do szyfrowania kluczy symetrycznych (transport kluczy)                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | Certyfikatu można użyć do bezpośredniego szyfrowania nieprzetworzonych danych użytkownika (nietypowego)                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | Certyfikat może służyć do uzgadniania kluczy (podobnie jak w przypadku Diffie-Hellmana)                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | Za pomocą certyfikatu można podpisać i weryfikować inne certyfikaty (certyfikat jest urzędem certyfikacji lub certyfikatem ICA).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | Klucz publiczny certyfikatu służy do weryfikowania podpisów na listach CRL                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Używany z bitem umów Key (bit 4) — w przypadku ustawienia klucza certyfikatu można używać tylko do szyfrowania podczas uzgadniania klucza. Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Używany z bitowym kluczem umowy (bit 4) — w przypadku ustawienia klucza certyfikatu można użyć tylko do odszyfrowania w trakcie uzgadniania klucza. Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony. |

Masek bitowych i wartości dla rozszerzenia użycie klucza X. 509

### <a name="parameters"></a>Parametry

- **certyfikat** Wskaźnik do zweryfikowanego certyfikatu.
- **pole bitowe** Zwróć cały pole bitowe z rozszerzenia.

### <a name="return-values"></a>Wartości zwrócone

- Znaleziono rozszerzenie użycie klucza **NX_SUCCESS** (0x00) i pole bitowe zwrócone.
- Napotkano **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 tag wielobajtowy (nieobsługiwany certyfikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) niedozwolone pole ASN. 1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) Nieprawidłowa Klasa tagu ASN. 1 (nieprawidłowy certyfikat).
- Napotkano nieprawidłowe rozszerzenie **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) (nieprawidłowy certyfikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) nie znaleziono rozszerzenia użycie klucza w podanym certyfikacie.
- **NX_PTR_ERROR** (0X07) nieprawidłowy certyfikat lub wskaźnik pole bitowe.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
