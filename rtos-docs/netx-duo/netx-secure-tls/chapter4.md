---
title: Rozdział 4 — Opis Azure RTOS NetX Secure
description: Ten rozdział zawiera opis wszystkich usług NetX Secure (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223396"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Rozdział 4 — Opis Azure RTOS NetX Secure

Ten rozdział zawiera opis wszystkich bezpiecznego Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API makro NX_SECURE_DISABLE_ERROR_CHECKING używane do wyłączania sprawdzania błędów interfejsu API nie ma wpływu na wartości z pogrubieniem, **natomiast** wartości bez pogrubienia są całkowicie wyłączone.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Wykonywanie self_test na metodach kryptograficznych
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Oblicza wartość skrótu przy użyciu user_supplied funkcji skrótu
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Ustawianie aktywnego certyfikatu tożsamości dla bezpiecznej sesji TLS NetX
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Ustawianie klucza Pre_Shared sesji klienta bezpiecznego TLS NetX
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Inicjuje moduł NetX Secure TLS]
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Dodawanie certyfikatu lokalnego do bezpiecznej sesji TLS netx
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Znajdowanie certyfikatu lokalnego w bezpiecznej sesji TLS netx według nazwy pospolitej
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Usuwanie certyfikatu lokalnego z bezpiecznej sesji TLS netx
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Obliczanie rozmiaru metadanych kryptograficznych dla bezpiecznej sesji TLS NetX
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Przydzielanie pakietu dla sesji protokołu NetX Secure TLS
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Dodawanie klucza Pre_Shared do bezpiecznej sesji TLS netx
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Przydzielanie miejsca dla certyfikatu dostarczonego przez zdalnego hosta TLS
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta TLS
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Wolne miejsce przydzielone dla certyfikatów przychodzących
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Dodawanie certyfikatu przeznaczonego specjalnie dla serwerów TLS przy użyciu identyfikatora liczbowego
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Konfigurowanie wywołania zwrotnego dla usługi TLS na użytek dodatkowej weryfikacji certyfikatu
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Konfigurowanie wywołania zwrotnego dla usługi TLS do wywoływania na początku uściślinia klienta TLS
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Włączanie weryfikacji X.509 klienta i przydzielanie miejsca dla certyfikatów klienta
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Wyłączanie uwierzytelniania certyfikatu klienta dla bezpiecznej sesji protokołu TLS netx
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Włączanie uwierzytelniania certyfikatu klienta dla bezpiecznej sesji protokołu TLS netx
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Tworzenie bezpiecznej sesji TLS netx na celu bezpieczną komunikację
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Usuwanie bezpiecznej sesji TLS netx
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Zakończenie aktywnej bezpiecznej sesji TLS netx
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Ustawianie buforu ponownego zestawu pakietów dla bezpiecznej sesji protokołu TLS NetX
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Zastąp domyślną wersję protokołu TLS dla bezpiecznej sesji TLS NetX
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Odbieranie danych z bezpiecznej sesji TLS netx
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Przypisywanie wywołania zwrotnego, które będzie wywoływane na początku ponownego negocjowania sesji
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Inicjowanie negocjacji ponownego negocjowania sesji z hostem zdalnym
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Wyczyszczanie i resetowanie bezpiecznej sesji TLS netx
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Wysyłanie danych za pośrednictwem bezpiecznej sesji TLS netx
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Konfigurowanie wywołania zwrotnego dla TLS do wywołania na początku uściślniania serwera TLS
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego od klienta TLS
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Ustawianie nazwy DNS Oznaczanie nazwy serwera (SNI) do wysyłania do serwera zdalnego
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Uruchamianie bezpiecznej sesji TLS netx
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Przypisywanie funkcji znacznika czasu do bezpiecznej sesji TLS netx
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Dodawanie zaufanego certyfikatu do bezpiecznej sesji TLS netx
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Usuwanie zaufanego certyfikatu z bezpiecznej sesji TLS netx
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Inicjowanie certyfikatu X.509 dla bezpiecznego TLS NetX
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Sprawdzanie nazwy DNS względem certyfikatu X.509
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Sprawdź certyfikat X.509 względem podanej listy odwołania certyfikatów (CRL)]
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Inicjowanie struktury nazw DNS X.509
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X.509 w certyfikacie X.509
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Znajdowanie i zwracanie rozszerzenia X.509 w certyfikacie X.509
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Znajdowanie i analizowanie rozszerzenia X.509 użycia klucza w certyfikacie X.509

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Wykonywanie samodzielnego testowania metod kryptograficznych

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Opis

Ta usługa jest uruchamiana za pośrednictwem metody kryptograficznego samokontroli w celu zweryfikowania. Samodzielny test jest dostępny tylko wtedy, gdy biblioteka NetX Secure została s zbudowana z NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK biblioteki.

Dla każdej obsługiwanej metody kryptograficzne autotest udostępnia wstępnie zdefiniowane dane wejściowe i sprawdza, czy dane wyjściowe są zgodnie ze wstępnie zdefiniowaną oczekiwaną wartością.

Samodzielny test kryptograficzny netX Secure obsługuje następujące algorytmy i rozmiary kluczy:

- DES: szyfrowanie i odszyfrowywanie
- Triple DES (3DES): szyfrowanie i odszyfrowywanie
- AES: 128-, 192-, 256-bitowy rozmiar klucza, szyfrowanie i odszyfrowywanie, w trybie CBC i trybie licznika.
- HMAC-MD5: uwierzytelnianie i obliczanie skrótów
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, uwierzytelnianie i obliczanie skrótów
- MD5: uwierzytelnianie
- Funkcja pseudolosowa (PRF): PRF_HMAC_SHA1 i PRF_HMAC_SHA2-256
- RSA: 1024-, 2048-, 4096-bitowa operacja modulo mocy RSA
- SHA: uwierzytelnianie SHA1 (96- i 160-bitowe), SHA2 (256-bitowe, 384-bitowe, 512-bitowe)

Ta funkcja ma wbudowane wektory dla wymienionych powyżej algorytmów kryptograficznych. Testuje jednak tylko te, które zostały wymienione *w cipher_table* przekazane do tej funkcji. Na przykład w przypadku sesji TLS używany jest tylko szyfrsuite TLS_RSA_WITH_AES_128_CBC_SHA, ta funkcja wykona własny test na RSA (1024-, 2048-, 4096-bitowych), AES-CBC (128-bitowych) i SHA1.

### <a name="parameters"></a>Parametry

- **crypto_table** Wskaźnik do tabeli kryptograficznych używanej przez sesję TLS. Jest to ta sama crypto_table przekazywana do **_wywołania nx_secure_tls_session_create()._**
- **metadane** Wskaźnik do miejsca dla obszaru metadanych kryptografii. .
- **metadata_size** Rozmiar buforu metadanych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SECURE_TLS_SUCCESS** (0x00) Pomyślnie przetestowano podane metody kryptograficzne.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa struktura metody kryptograficznych
- **NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails (Samodzielne testowanie kryptograficzne kończy się niepowodzeniem).

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

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

Ta funkcja oblicza wartość skrótu strumienia danych w określonym obszarze pamięci przy użyciu podanej metody kryptograficznej HMAC i ciągu klucza. Funkcja obliczeniowa skrótu modułu jest dostępna tylko wtedy, gdy biblioteka NetX Secure jest budowaną przy użyciu następującego symbolu: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Parametry

- **hmac_ptr** Wskaźnik do metody kryptograficznej HMAC używanej do obliczania wartości skrótu.
- **start_address** Adres początkowy buforu danych
- **end_address** Końcowy adres buforu danych. Należy pamiętać, że obliczenia wartości skrótu nie obejmują danych w tym end_address.
- **klucz** Ciąg klucza używany w obliczeniach HMAC.
- **key_length** Rozmiar ciągu klucza w bajtach
- **metadane** Wskaźnik do miejsca używanego przez algorytm HMAC.
- **metadata_size** Rozmiar buforu metadanych.
- **output_buffer** Lokalizacja pamięci, w której są przechowywane dane wyjściowe skrótu.
- **output_buffer_size** Dostępne miejsce buforu wyjściowego w bajtach
- **actual_size** Zwracana przez funkcję wskazująca rzeczywistą liczbę bajtów zapisywanych w output_buffer.

### <a name="return-values"></a>Wartości zwrócone

- **0** Pomyślnie obliczono wartość skrótu.
- **1 Obliczanie** skrótu nie powiodło się.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

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

Ustawianie aktywnego certyfikatu tożsamości dla bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji (zobacz nx_secure_tls_session_client_callback_set i nx_secure_tls_session_server_callback_set). W przypadku wywoływania z wcześniej zainicjowaną NX_SECURE_X509_CERT, ten certyfikat będzie używany zamiast domyślnego certyfikatu tożsamości. W większości przypadków certyfikat musi zostać dodany do magazynu lokalnego (zobacz nx_secure_tls_local_certificate_add) lub uściślić TLS może się nie powieść.

Ta usługa jest przeznaczona do zezwalania na obsługę wielu certyfikatów tożsamości przez usługę TLS. Jest to przydatne w przypadku serwera TLS, który zapewnia wiele adresów sieciowych, dzięki czemu serwer może wybrać odpowiedni certyfikat do zapewnienia klientowi zdalnej w zależności od punktu wejścia klienta. W przypadku klienta TLS ta procedura może służyć do zmiany certyfikatu wysyłanego do serwera zdalnego w czasie wykonywania po tym, jak serwer zidentyfikował się w uściśleniu TLS (jest to bardziej rzadkie niż przypadek użycia serwera TLS).

W przypadku, gdy wiele certyfikatów może mieć tę samą nazwę wyróżniającą X.509, należy dodać certyfikaty przy użyciu programu nx_secure_tls_server_certificate_add, co wprowadza identyfikator liczbowy oddzielony od certyfikatu.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS przekazany do wywołania zwrotnego sesji.
- **certyfikat** Wskaźnik do zainicjowany certyfikat X.509, który ma być używany w bieżącej sesji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przypisanie certyfikatu do sesji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.

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

Ustawianie klucza wstępnego dla bezpiecznej sesji klienta TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny, jego ciąg tożsamości i wskazówkę tożsamości do bloku kontroli sesji TLS oraz ustawia klucz wstępny do późniejszego połączenia klienta TLS. Jeśli są włączone i używane szyfry PSK, używany jest certyfikat cyfrowy, a nie certyfikat cyfrowy.

W takim przypadku k OKI jest skojarzony z określonym zdalnym serwerem TLS, z którym klient TLS chce się komunikować. Klucz psk ustawiony za pośrednictwem tego interfejsu API zostanie przekazany do zdalnego hosta serwera TLS podczas następnego ugody TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **pre_shared_key** Rzeczywista wartość PSK.
- **psk_length** Długość wartości PSK.
- **psk_identity** Ciąg używany do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości psk.
- **wskazówka** Ciąg używany do wskazywania grupy psk do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie psk.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Nie można dodać kolejnego psk.

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

Inicjuje moduł NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Opis

Ta usługa inicjuje moduł NetX Secure TLS. Musi zostać wywołana, aby można było uzyskać dostęp do innych usług NetX Secure.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Dodawanie certyfikatu lokalnego do bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje zainicjowane NX_SECURE_X509_CERT struktury do magazynu lokalnego sesji TLS. Ten certyfikat może być używany przez stos TLS do identyfikowania urządzenia podczas procesu ugody TLS (jeśli został oznaczony jako certyfikat tożsamości podczas inicjowania struktury certyfikatów przy użyciu programu nx_secure_x509_certificate_initialize) lub jako wystawca w ramach łańcucha certyfikatów dostarczonego do hosta zdalnego podczas procesu ugody TLS.

Jeśli wymaganych jest wiele certyfikatów lokalnych o tej samej nazwie pospolitej, można dodać certyfikaty przy użyciu *usługi nx_secure_tls_server_certificate_add* (zobacz ostrzeżenie poniżej).

Certyfikat jest wymagany **w trybie** serwera TLS.

Certyfikat jest opcjonalny *dla* trybu klienta TLS.

> [!IMPORTANT]
> *Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a indeksy nx_secure_tls_local_certificate_add oparte na nazwie pospolitej X.509. Lokalne usługi certyfikatów stanowią wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — dzięki użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certificate_ptr** Wskaźnik do zainicjowanych wystąpień certyfikatu TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.
- **NX_INVALID_PARAMETERS** (0x4D) Próbowano dodać nieprawidłowy lub zduplikowany certyfikat.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.

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

Znajdowanie certyfikatu lokalnego w bezpiecznej sesji TLS netx według nazwy pospolitej

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Opis

Ta usługa znajduje certyfikat w magazynie certyfikatów urządzenia lokalnego sesji TLS i zwraca wskaźnik do struktury NX_SECURE_X509_CERT w magazynie. Parametr common_name i jego długość (name_length) są używane do identyfikowania certyfikatu w magazynie przez dopasowanie pola pospolita X.509 certyfikatu.

Jeśli istnieje więcej niż jeden certyfikat o tej samej nazwie pospolitej, zostanie zwrócony tylko pierwszy certyfikat — zamiast tego użyj *nx_secure_tls_server_certificate_find* pospolitej.

> [!IMPORTANT]
> *Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i nx_secure_tls_local_certificate_add na podstawie nazwy pospolitej X.509. Lokalne usługi certyfikatów stanowią wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certyfikat** Zwraca wskaźnik do dopasowanego certyfikatu.
- **common_name** Ciąg nazwy pospolitej do dopasowania (nazwa DNS).
- **name_length** Długość common_name ciągu tekstowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Znaleziono certyfikat i zwrócono wskaźnik w parametrze "certificate".
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Nie znaleziono certyfikatu z podaną nazwą pospolitą.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa sesja TLS, wskaźnik certyfikatu lub ciąg nazwy pospolitej.

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

Usuwanie certyfikatu lokalnego z bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Opis

Ta usługa usuwa lokalne wystąpienie certyfikatu z sesji TLS z kluczem w polu Nazwa pospolita w certyfikacie.

> [!IMPORTANT]
> *Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i nx_secure_tls_local_certificate_add na podstawie nazwy pospolitej X.509. Lokalne usługi certyfikatów stanowią wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **common_name** Wartość nazwa pospolita certyfikatu do usunięcia.
- **common_name_length** Długość ciągu nazwy pospolitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Nie znaleziono certyfikatu.

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

Obliczanie rozmiaru metadanych kryptograficznych dla bezpiecznej sesji TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Opis

Ta usługa oblicza i zwraca rozmiar metadanych kryptograficznych wymaganych dla określonej sesji TLS i tabeli kryptografii TLS (zobacz sekcję "Inicjowanie szyfrowania TLS za pomocą metod kryptograficznych", aby uzyskać więcej informacji na temat tabeli szyfrowania kryptograficznego).

Ta usługa powinna być wywoływana z żądaną tabelą kryptograficznymi, aby obliczyć rozmiar buforu metadanych przekazanego do nx_secure_tls_session_create.

### <a name="parameters"></a>Parametry

- **crypto_table** Wskaźnik do pełnej tabeli kryptografii NetX Secure TLS.
- **metadata_size** Dane wyjściowe obliczenia rozmiaru w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne obliczenie rozmiaru metadanych.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik rozmiaru lub tabeli kryptograficznych.

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

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Przydzielanie pakietu dla sesji protokołu NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji TLS z określonego NX_PACKET_POOL. Ta usługa powinna zostać wywołana przez aplikację, aby przydzielić pakiety danych do wysłania za pośrednictwem połączenia TLS. Sesja TLS musi zostać zainicjowana przed wywołaniem tej usługi.

Przydzielony pakiet jest prawidłowo zainicjowany, dzięki czemu dane nagłówka i stopki protokołu TLS mogą zostać dodane po wypełnieniu danych pakietu. W przeciwnym razie zachowanie jest identyczne *nx_packet_allocate*.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma być przydzielany pakiet.
- **packet_ptr** Wskaźnik wyjściowy do nowo przydzielonego pakietu.
- **wait_option** Opcja zawieszenia dla alokacji pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przydzielanie pakietów.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Alokacja pakietów bazowych nie powiodła się.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Dostarczona sesja TLS nie została zainicjowana.

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

Dodawanie klucza wstępnego do bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Opis

Ta usługa dodaje klucz wstępny , jego ciąg tożsamości i wskazówkę tożsamości do bloku kontroli sesji TLS. Jeśli są włączone i używane szyfry PSK, używany jest certyfikat cyfrowy, a nie certyfikat cyfrowy.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **pre_shared_key** Rzeczywista wartość PSK.
- **psk_length** Długość wartości PSK.
- **psk_identity** Ciąg używany do identyfikowania tej wartości PSK.
- **identity_length** Długość tożsamości psk.
- **wskazówka** Ciąg używany do wskazywania grupy psk do wyboru na serwerze TLS.
- **hint_length** Długość ciągu wskazówki.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie psk.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Nie można dodać kolejnego psk.

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

Przydzielanie miejsca dla certyfikatu dostarczonego przez zdalnego hosta TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Opis

Ta usługa dodaje niezainicjowane wystąpienie struktury NX_SECURE_X509_CERT do sesji TLS w celu przydzielenia miejsca na certyfikaty udostępniane przez hosta zdalnego podczas sesji TLS. Dane certyfikatu zdalnego są analizowane przez funkcję NetX Secure TLS i te informacje są używane do wypełnienia wystąpienia struktury certyfikatu dostarczonego do tej funkcji. Certyfikaty dodane w ten sposób są umieszczane na połączonej liście.

Jeśli oczekuje się, że host zdalny udostępni wiele certyfikatów, ta funkcja powinna być wywoływana wielokrotnie, aby przydzielić miejsce dla wszystkich certyfikatów. Dodatkowe certyfikaty są dodawane na końcu połączonej listy certyfikatów.

Nie można przydzielić certyfikatu zdalnego spowoduje, że tryb klienta TLS nie powiedzie się podczas ugody TLS, chyba że jest w użyciu klucz wstępny (PSK).

Parametr *raw_certificate_buffer* wskazuje miejsce przydzielone do przechowywania przychodzącego certyfikatu zdalnego. Typowe certyfikaty z kluczami RSA 2048 bitów używające sha-256 dla podpisów są w zakresie od 1000 do 2000 bajtów. Bufor powinien być wystarczająco duży, aby co najmniej pomieścić ten rozmiar, ale w zależności od certyfikatów hosta zdalnego może być znacznie mniejszy lub większy. Należy pamiętać, że jeśli bufor jest zbyt mały do przechowywania certyfikatu przychodzącego, uściślenie TLS zakończy się błędem.

W trybie serwera TLS zdalna alokacja certyfikatu jest potrzebna tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu klienta.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certificate_ptr** Wskaźnik do niezainicjowanych wystąpień certyfikatu X.509.
- **raw_certificate_buffer** Wskaźnik do buforu do przechowywania nieza analizowanych certyfikatów odebranych z hosta zdalnego.
- **raw_buffer_size** Rozmiar nieprzetworzowego bufora certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna alokacja certyfikatu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Podany bufor był zbyt mały.
- **NX_INVALID_PARAMETERS** (0x4D) Próbowano dodać nieprawidłowy certyfikat.

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

Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa przydziela miejsce na przetwarzanie łańcuchów certyfikatów przychodzących z hostów serwerów zdalnych w celu przeprowadzenia uwierzytelniania i weryfikacji X.509 w wystąpieniu klienta TLS. W trybie serwera TLS zdalna alokacja certyfikatów jest potrzebna tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu X.509 klienta — w przypadku wystąpień serwera TLS należy zamiast tego użyć nx_secure_tls_session_x509_client_verify_configure *certyfikatu.*

Nie można przydzielić certyfikatów zdalnych spowoduje, że tryb klienta TLS będzie się nie powiódł podczas uściśnia TLS, chyba że jest w użyciu klucz wstępny (PSK).

Parametr *certificate_buffer* wskazuje miejsce przydzielone do przechowywania przychodzących certyfikatów zdalnych oraz bloki sterowania wymagane dla tych certyfikatów. Bufor zostanie podzielony przez liczbę certyfikatów *(certs_number*) z równą częścią nadaną każdemu certyfikatowi. Parametr *buffer_size*  wskazuje rozmiar buforu. Potrzebne miejsce można znaleźć przy użyciu następującej formuły:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Typowe certyfikaty z kluczami RSA 2048 bitów używające sha-256 dla podpisów są w zakresie od 1000 do 2000 bajtów. Bufor powinien być wystarczająco duży, aby pomieścić co najmniej ten rozmiar dla każdego certyfikatu, ale w zależności od certyfikatów hosta zdalnego może być znacznie mniejszy lub większy. Należy pamiętać, że jeśli bufor jest zbyt mały do przechowywania certyfikatu przychodzącego, uściślenie TLS zakończy się błędem.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.
- **certificate_buffer** Wskaźnik do buforu do przechowywania certyfikatów odebranych z hosta zdalnego.
- **buffer_size** Rozmiar buforu certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przydzielenie certyfikatu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu TLS.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Podany bufor był zbyt mały.
- **NX_INVALID_PARAMETERS** (0x4D) Bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.

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

Wolne miejsce przydzielone dla certyfikatów przychodzących

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa służy do wolnej wszystkich buforów certyfikatów przydzielonych do określonej sesji TLS przez nx_secure_tls_remote_certificate_allocated przez zwrócenie ich do wolnego miejsca na certyfikat tej sesji. Może to być konieczne, jeśli aplikacja ponownie używa obiektu sesji TLS bez usuwania go i ponownego nx_secure_tls_session_delete i nx_secure_tls_session_create.

Należy pamiętać, że miejsce na zdalnym certyfikacie jest odzyskiwane automatycznie, gdy sesja TLS jest resetowana zgodnie z nx_secure_tls_session_end, więc większość aplikacji nie powinna wymagać wywołania tej usługi.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna operacja.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Błąd wewnętrzny — magazyn certyfikatów jest prawdopodobnie uszkodzony.

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

Dodawanie certyfikatu przeznaczonego specjalnie dla serwerów TLS przy użyciu identyfikatora liczbowego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Opis

Ta usługa służy do dodawania certyfikatu do magazynu lokalnego sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu podmiotu X.509 (nazwa pospolita) w certyfikacie. Identyfikator liczbowy jest oddzielony od certyfikatu i umożliwia dodanie wielu certyfikatów jako certyfikatów tożsamości do serwera TLS, a także umożliwia dodanie wielu certyfikatów o tej samej nazwie pospolitej do tego samego magazynu lokalnego sesji TLS. Ta sama usługa może być używana w przypadku certyfikatów klienta, ale rzadko klient TLS ma wiele certyfikatów tożsamości.

Parametr cert_id jest niezerową dodatnią liczbą całkowitą przypisaną przez aplikację. Rzeczywista wartość nie ma znaczenia (innej niż zero), ale musi być unikatowa w magazynie dla podanej sesji TLS. Wartość cert_id może służyć do znalezienia i usunięcia certyfikatów z magazynu lokalnego przy użyciu nx_secure_tls_server_certificate_find i nx_secure_tls_server_certificate_remove.

> [!IMPORTANT]
> *Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i indeksu lokalnych usług certyfikatów na podstawie nazwy pospolitej X.509. Usługi certyfikatów serwera umożliwiają istnienia wielu certyfikatów z danymi udostępnionym (szczególnie nazwa pospolita) w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certyfikat** Wskaźnik do wcześniej zainicjowane wystąpienie certyfikatu X.509.
- **cert_id** Dodatni, niezerowy, stosunkowo unikatowy numer identyfikatora certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00)Operacja powiodła się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.
- **NX_SECURE_TLS_CERT_ID_INVALID** (0x138) Podany identyfikator certyfikatu miał nieprawidłową wartość (prawdopodobnie 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) Podany identyfikator certyfikatu był już obecny w magazynie lokalnym.
- **NX_INVALID_PARAMETERS(0x4D)** Błąd wewnętrzny — magazyn certyfikatów jest prawdopodobnie uszkodzony.

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

Ta usługa służy do wyszukiwania certyfikatu w magazynie lokalnym sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu podmiotu X.509 (nazwa pospolita) w certyfikacie.

Parametr cert_id jest niezerową dodatnią liczbą całkowitą przypisaną przez aplikację po dodaniu certyfikatu do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i indeksu lokalnych usług certyfikatów na podstawie nazwy pospolitej X.509. Usługi certyfikatów serwera umożliwiają wielu certyfikatom z danymi udostępnionym (zwłaszcza nazwą pospolitą) istniejące w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certyfikat** Wskaźnik do wskaźnika certyfikatu X.509 w celu zwrócenia odwołania do znalezionego certyfikatu.
- **cert_id** Niezerowa dodatnia wartość identyfikatora certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00)Operacja powiodła się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Podany identyfikator certyfikatu nie pasuje do żadnego z identyfikatorów w magazynie lokalnym podanej sesji TLS.

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

Ta usługa służy do usuwania certyfikatu z magazynu lokalnego sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu podmiotu X.509 (nazwa pospolita) w certyfikacie.

Parametr cert_id jest niezerową dodatnią liczbą całkowitą przypisaną przez aplikację po dodaniu certyfikatu do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **cert_id** Niezerowa dodatnia wartość identyfikatora certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00)Operacja powiodła się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa sesja TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Podany identyfikator certyfikatu nie pasuje do żadnego z identyfikatorów w magazynie lokalnym podanej sesji TLS.

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

Uzyskiwanie wartości i poziomu alertu TLS wysyłanych przez hosta zdalnego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Opis

Ta usługa służy do pobierania wartości i poziomu alertu TLS, gdy host zdalny wysyła alert w odpowiedzi na jakiś problem lub błąd.

Wartości parametrów alert_level i alert_value są prawidłowe tylko wtedy, gdy ta funkcja jest wywoływana natychmiast po wywołaniu interfejsu API TLS, które zwróciło stan NX_SECURE_TLS_ALERT_RECEIVED (0x114) wskazujący, że otrzymano alert z hosta zdalnego.

Należy pamiętać, że jeśli lokalny host TLS wysyła alert, zwrócone kody błędów są znacznie bardziej opisowe dla rzeczywistego błędu niż sam alert TLS, ponieważ wartości alertów TLS celowo pozostawiają niejednoznaczne, aby zapobiec niektórym typom ataków (takim jak atak typu "wyrocznia wypełnienia" lub podobne).

Poziom alertu przyjmuje tylko jedną z dwóch wartości: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) lub NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2). Ogólnie rzecz biorąc, tylko alert CloseNotify (używany do wskazania pomyślnego zakończenia sesji TLS) będzie miał poziom "Ostrzeżenie", chociaż niektóre sytuacje konfiguracji rozszerzenia mogą również być traktowane jako ostrzeżenia. Ogromna większość alertów będzie "Krytyczny" wskazujący potencjalny błąd zabezpieczeń i skutkować natychmiastowym zamknięciem połączenia TLS (ugoda lub sesja).

Wartości alertów TLS są zdefiniowane w dokumencie RFC 5246 (TLSv1.2) w dokumencie RLS. Poniżej znajduje się lista referencyjna:

| Nazwa alertu                     | Wartość | Opis                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Brak błędu, oznacza pomyślne zakończenie sesji                                                                                                                   |
| unexpected_message            | 10    | TLS odebrał nieoczekiwany lub nieodpowiedny komunikat                                                                                                           |
| bad_record_mac               | 20    | Odszyfrowywanie i/lub weryfikacja adresu MAC nie powiodła się                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **PRZESTARZAŁE** Odszyfrowywanie nie powiodło się (jest przestarzałe z powodu ataków na wyrocznię uzupełniania)                                                                                      |
| record_overflow               | 22    | Odebrano rekord, który jest większy niż maksymalny rozmiar rekordu TLS                                                                                        |
| decompression_failure         | 30    | Wystąpił problem podczas kompresji/dekompresji rekordu TLS                                                                                       |
| handshake_failure             | 40    | Wystąpił nieokreślony błąd uściślinia, który nie jest objęty innym alertem                                                                            |
| no_certificate_RESERVED      | 41    | **PRZESTARZAŁE w** protokołach TLS (tylko protokół SSL)                                                                                                                                 |
| bad_certificate               | 42    | Odebrany certyfikat zawiera nieprawidłowe formatowanie lub nieprawidłowe podpisy                                                                                   |
| unsupported_certificate       | 43    | Odebrano certyfikat o nieprawidłowym typie (np. certyfikat tylko do podpisywania używany do uwierzytelniania serwera TLS)                                    |
| certificate_revoked           | 44    | Stan certyfikatu (dostarczony przez listy CRL lub OCSP) został wskazany jako "odwołany"                                                                       |
| certificate_expired           | 45    | Odebrany certyfikat był poza prawidłowym zakresem dat (nie jest jeszcze ważny lub wygasł)                                                                 |
| certificate_unknown           | 46    | Wystąpił nieznany problem z certyfikatem, który nie był objęty innymi alertami                                                                          |
| illegal_parameter             | 47    | Niektóre wartości konfiguracji lub negocjowane w uściśliwce TLS były nieprawidłowe lub poza zakresem                                                                      |
| unknown_ca                    | 48    | Nie można śledzić odebranego certyfikatu tożsamości za pośrednictwem łańcucha certyfikatów do certyfikatu zaufanego głównego urzędu certyfikacji.                                              |
| Access_denied                 | 49    | Wskazuje, że odebrano prawidłowy certyfikat, ale kontrola dostępu do aplikacji wskazuje, że certyfikat jest nieprawidłowy dla żądanych zasobów.            |
| decode_error                  | 50    | Niektóre pola lub wartości w nagłówku lub komunikacie uściślniania TLS były poza zakresem lub nieprawidłowe, co prowadziło do błędu dekodowania rekordu TLS.                      |
| decrypt_error                 | 51    | Nie można zweryfikować skrótu podpisu lub zakończonego komunikatu podczas ugody TLS.                                                                         |
| export_restriction_RESERVED  | 60    | PRZESTARZAŁE W TLSv1.2                                                                                                                                        |
| protocol_version              | 70    | Wersja protokołu TLS negocjowana podczas procesu uzgodnienia jest rozpoznawana, ale nie jest obsługiwana (np. TLSv1.0 została przedstawiona, ale nie włączona).                       |
| insufficient_security         | 71    | Wysyłane za każdym razem, gdy handshake zakończy się niepowodzeniem z powodu braku bezpiecznych szyfrów (np. rozmiar klucza jest zbyt mały, aby spełnić wymagania aplikacji)                                |
| internal_error                | 80    | Niektóre błędy inne niż TLS (np. problemy z alokacją pamięci, problemy z aplikacją) wystąpiły, co skutkowało przerwaną sesją TLS.                                         |
| user_canceled                 | 90    | Zwracany, jeśli sesja TLS zostanie anulowana przez użytkownika lub aplikację przed zakończeniem procesu handshake (podobnie jak w przypadku closeNotify).                                 |
| no_renegotiation              | 100   | Indietes, że host zdalny nie chce wykonać renegocjacji TLS uściślić w odpowiedzi na żądanie ponownego negocjowania.                                 |
| unsupported_extension         | 110   | Wysyłane, jeśli klient TLS odbierze serwerHello zawierający rozszerzenia, o które nie pytano jawnie w początkowej aplikacji ClientHello (co wskazuje, że serwer ma problem). |

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **alert_level** Zwróć poziom odebranego alertu (ostrzeżenie lub błąd krytyczny).
- **alert_value** Zwraca wartość odebranego alertu (zobacz tabelę).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna operacja.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa sesja TLS.

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

Konfigurowanie wywołania zwrotnego dla usługi TLS na użytek dodatkowej weryfikacji certyfikatu

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływana przez usługę TLS po odebraniu certyfikatu z hosta zdalnego, co umożliwia aplikacji przeprowadzanie testów poprawności, takich jak weryfikacja systemu DNS, odwoływanie certyfikatów i wymuszanie zasad certyfikatów.

Zabezpieczenia NetX TLS będą wykonywać podstawową weryfikację ścieżki X.509 certyfikatu przed wywołaniem wywołania zwrotnego, aby mieć pewność, że certyfikat może być śledzony do certyfikatu w magazynie zaufanych certyfikatów TLS, ale wszystkie pozostałe weryfikacje będą obsługiwane przez to wywołanie zwrotne.

Wywołanie zwrotne udostępnia wskaźnik sesji TLS i wskaźnik do certyfikatu tożsamości hosta zdalnego (liścia w łańcuchu certyfikatów). Wywołanie zwrotne powinno zwrócić NX_SUCCESS, jeśli cała walidacja powiedzie się. W przeciwnym razie powinien zostać zwrócony kod błędu wskazujący niepowodzenie walidacji. Każda wartość inna NX_SUCCESS spowoduje natychmiastowe przerwanie uściśniania TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego weryfikacji certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna alokacja wskaźnika funkcji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.

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

Konfigurowanie wywołania zwrotnego dla usługi TLS do wywoływania na początku uściślniania klienta TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływana po otrzymaniu komunikatu ServerHelloDone klienta TLS Client. Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie wszelkich rozszerzeń TLS z odebranego komunikatu ServerHello, które wymagają danych wejściowych lub podejmowania decyzji.

Wywołanie zwrotne jest wykonywane przy użyciu wywołującego bloku kontroli sesji TLS i tablicy NX_SECURE_TLS_HELLO_EXTENSION obiektów. Tablica obiektów rozszerzenia ma być przekazywana do funkcji pomocnika, która znajdzie i przejmie określone rozszerzenie. Obecnie w środowisku NetX Secure nie są obsługiwane żadne określone rozszerzenia, które wymagają danych wejściowych klienta TLS, ale wywołanie zwrotne jest dostępne dla projektantów aplikacji w celu obsługi rozszerzeń niestandardowych lub nowych, które mogą stać się dostępne. Przykładowa funkcja pomocnika, która analizuje rozszerzenia TLS podane w komunikatach powitalnych, zobacz *nx_secure_tls_session_sni_extension_parse*.

Wywołanie zwrotne klienta może również służyć do wybierania aktywnego certyfikatu tożsamości przy użyciu usługi *nx_secure_tls_active_certificate_set* dla klienta TLS w przypadku, gdy serwer zdalny zażądał certyfikatu i podał informacje umożliwiające klientowi TLS wybranie określonego certyfikatu. Aby uzyskać więcej informacji, zobacz nx_secure_tls_active_certificate_set informacje.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego klienta TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna alokacja wskaźnika funkcji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.

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

Włączanie weryfikacji X.509 klienta i przydzielanie miejsca dla certyfikatów klienta

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa umożliwia opcjonalne uwierzytelnianie klienta X.509 dla wystąpienia serwera TLS. Przydziela również miejsce potrzebne do przetwarzania łańcuchów certyfikatów przychodzących z hosta klienta zdalnego. Certyfikaty dostarczone przez klienta zdalnego zostaną zweryfikowane względem zaufanych certyfikatów wystąpienia serwera TLS przypisanych do usługi *nx_secure_tls_trusted_certificate_add.*

W trybie klienta TLS wymagana jest zdalna alokacja certyfikatów, a zamiast *nx_secure_tls_remote_certificate_buffer_allocate* należy użyć usługi. Włączenie uwierzytelniania klienta X.509 w wystąpieniu klienta TLS nie będzie mieć żadnego efektu.

Parametr *certificate_buffer* wskazuje miejsce przydzielone do przechowywania przychodzących certyfikatów zdalnych oraz bloki sterowania wymagane dla tych certyfikatów. Bufor zostanie podzielony przez liczbę certyfikatów *(certs_number*) z równą częścią nadaną każdemu certyfikatowi. Parametr *buffer_size* wskazuje rozmiar buforu. Potrzebne miejsce można znaleźć przy użyciu następującej formuły:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Typowe certyfikaty z kluczami RSA 2048 bitów używające sha-256 dla podpisów są w zakresie od 1000 do 2000 bajtów. Bufor powinien być wystarczająco duży, aby pomieścić co najmniej ten rozmiar dla każdego certyfikatu, ale w zależności od certyfikatów hosta zdalnego może być znacznie mniejszy lub większy. Należy pamiętać, że jeśli bufor jest zbyt mały do przechowywania certyfikatu przychodzącego, uściślicie TLS zakończy się błędem.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.
- **certificate_buffer** Wskaźnik do buforu do przechowywania certyfikatów odebranych z hosta zdalnego.
- **buffer_size** Rozmiar buforu certyfikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00)Pomyślna alokacja certyfikatu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu TLS.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Podany bufor był zbyt mały.
- **NX_INVALID_PARAMETERS** (0x4D) Bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.

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

Wyłączanie uwierzytelniania certyfikatu klienta dla sesji protokołu NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS. Zobacz nx_secure_tls_session_client_verify_enable, aby uzyskać więcej informacji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna zmiana stanu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.

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

Włączanie uwierzytelniania certyfikatu klienta dla bezpiecznej sesji protokołu TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS. Włączenie uwierzytelniania certyfikatu klienta dla wystąpienia serwera TLS spowoduje, że serwer TLS zażąda certyfikatu od dowolnego zdalnego klienta protokołu TLS podczas początkowego uwierzytelniania TLS. Do certyfikatu otrzymanego od zdalnego klienta TLS jest dołączany komunikat CertificateVerify, którego serwer TLS używa do sprawdzenia, czy klient jest właścicielem certyfikatu (ma dostęp do klucza prywatnego skojarzonego z tym certyfikatem).

Jeśli dostarczony certyfikat można zweryfikować i prześledzić z powrotem do certyfikatu w magazynie zaufanych certyfikatów serwera TLS za pośrednictwem łańcucha certyfikatów X.509, uwierzytelniany jest zdalny klient TLS i będzie kontynuowane ugodę. W przypadku błędów podczas przetwarzania certyfikatu lub komunikatu CertificateVerify, uściślicie TLS kończy się błędem.

> [!NOTE]
> *Serwer TLS musi mieć w swoim zaufanym magazynie co najmniej jeden certyfikat dodany z nx_secure_tls_trusted_certificate_add w przypadku, gdy uwierzytelnianie zawsze nie powiedzie się.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna zmiana stanu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.

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

Tworzenie bezpiecznej sesji TLS netx na celu bezpieczną komunikację

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje wystąpienie NX_SECURE_TLS_SESSION struktury do użycia podczas ustanawiania bezpiecznej komunikacji TLS za pośrednictwem połączenia sieciowego.

Metoda przyjmuje obiekt NX_SECURE_TLS_CRYPTO, który jest wypełniany dostępnymi metodami kryptograficznymi, które mają być używane w przypadku szyfrowania TLS. Interfejs *encryption_metadata_area* bufor przydzielony do użycia przez usługę TLS dla "metadanych" używanych przez metody kryptograficzne w tabeli NX_SECURE_TLS_CRYPTO do obliczeń. Rozmiar tabeli można określić przy użyciu usługi nx_secure_tls_metadata_size_calculate service. Aby uzyskać więcej informacji, zobacz sekcję "Kryptografia w zabezpieczonych zabezpieczeniach TLS netX" w rozdziale 3.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **cipher_table** Wskaźnik do metod kryptograficznych TLS.
- **encryption_metadata_area** Wskaźnik do miejsca dla metadanych kryptografii.
- **encryption_metadata_size** Rozmiar buforu metadanych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00)Pomyślne zainicjowanie sesji TLS.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.
- **NX_INVALID_PARAMETERS** (0x4D) Bufor metadanych był zbyt mały dla danej metody.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) W tabeli szyfrowania nie połączono wymaganej metody szyfrowania dla włączonej wersji TLS.

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
- Kryptografia w zabezpieczonych zabezpieczeniach TLS NetX w rozdziale 3

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

Usuwanie bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa sesję TLS reprezentowaną przez wystąpienie struktury NX_SECURE_TLS_SESSION i zwalnia wszystkie zasoby systemowe należące do tego wystąpienia sesji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.

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

Zakończenie aktywnej bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa kończy sesję TLS reprezentowaną przez wystąpienie struktury NX_SECURE_TLS_SESSION, wysyłając komunikat TLS CloseNotify do hosta zdalnego. Następnie usługa czeka, aż host zdalny odpowie własnym komunikatem CloseNotify.

Jeśli host zdalny nie wyśle komunikatu CloseNotify, usługa TLS uzna ten błąd za błąd i możliwe naruszenie zabezpieczeń, dlatego sprawdzenie wartości zwracanej jest ważne dla bezpiecznego połączenia. Parametr **wait_option** służy do kontrolowania, jak długo usługa powinna czekać na odpowiedź przed zwróceniem kontrolki do wątku wywołującego.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **wait_option** Wskazuje, jak długo usługa powinna czekać na odpowiedź z hosta zdalnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Nie otrzymał odpowiedzi z hosta zdalnego przed przekierowywem.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Nie można przydzielić pakietu w celu wysłania komunikatu CloseNotify.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Nie można wysłać komunikatu CloseNotify za pośrednictwem gniazda TCP.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.

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

Ustawianie buforu ponownego zestawu pakietów dla bezpiecznej sesji protokołu TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa kojarzy bufor ponownego skojarzenia pakietów z sesją protokołu TLS. W celu odszyfrowania i analizy przychodzących rekordów protokołu TLS dane w każdym rekordzie muszą zostać zebrane z podstawowych pakietów TCP. Rekordy TLS mogą mieć rozmiar do 16 KB (chociaż zwykle są znacznie mniejsze), więc mogą nie mieścić się w jednym pakiecie TCP.

Jeśli wiesz, że rozmiar komunikatu przychodzącego będzie mniejszy niż limit rekordów TLS 16 KB, rozmiar buforu może być mniejszy, ale w celu obsługi nieznanych danych przychodzących bufor powinien być tak duży, jak to możliwe. Jeśli przychodzący rekord jest większy niż podany bufor, sesja TLS zakończy się błędem.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **buffer_ptr** Wskaźnik do bufora dla protokołu TLS do użycia na użytek ponownego zsembmbly pakietów.
- **buffer_size** Rozmiar dostarczonego buforu w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy bufor lub wskaźnik sesji TLS.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.

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

Zastąp domyślną wersję protokołu TLS dla bezpiecznej sesji protokołu TLS NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Opis

Ta usługa zastępuje domyślną (najnowszą) wersję protokołu TLS używaną przez określoną sesję. Dzięki temu funkcja NetX Secure TLS może używać starszej wersji TLS dla określonej sesji TLS bez wyłączania nowszej wersji TLS w czasie kompilacji. Może to być przydatne w aplikacjach, które mogą wymagać komunikacji ze starszym hostem, który nie obsługuje najnowszej wersji TLS.

> [!IMPORTANT]
> *Od wersji 5.11SP3 usługa NetX Secure TLS obsługuje zabezpieczenia RFC 7507 (patrz uwaga poniżej), a wszelkie przesłonięcia starszej wersji za pomocą tego interfejsu API spowodują, że rezerwowy scSV zostanie wysłany w aplikacji ClientHello. Jeśli serwer obsługuje nowszą wersję zabezpieczeń TLS, a rezerwowy scSV jest uwzględniony w aplikacji ClientHello, ten serwer przerwać ugodę TLS z alertem "Nieodpowiednie rezerwowe". ScSV jest wysyłany tylko wtedy, gdy przesłonięcie wersji jest starszą wersją TLS niż jest włączona (np. jeśli zastąpisz wersję TLS 1.2, nie będą wysyłane żadne scSV).*

Prawidłowe wartości parametru protocol_version to następujące makra: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 i NX_SECURE_TLS_VERSION_TLS_1_2.

Makra NX_SECURE_TLS_DISABLE_TLS_1_1 i NX_SECURE_TLS_ENABLE_TLS_1_0 mogą służyć do kontrolowania wersji TLS, które są kompilowane w aplikacji. TLS w wersji 1.2 jest zawsze włączony.

Należy pamiętać, że jeśli host zdalny nie obsługuje podanej wersji, połączenie nie powiedzie się — tylko dostarczona wersja zastąpienia będzie negocjowana przez zabezpieczenia TLS netx.

> [!IMPORTANT]
> RFC 7507: TLS Fallback SCSV. Ten dokument RFC został wprowadzony w celu ograniczenia problemu z zabezpieczeniami, który był pierwotnie spowodowany przez serwery, które nieprawidłowo obsługiowały negocjacje obniżania poziomu protokołu, a zamiast tego odrzucały prawidłowe komunikaty ClientHello. Aby zachować zgodność z tymi starymi serwerami, niektóre aplikacje klienckie TLS zaczęły ponawiać próby nieudanych prób ugodowych z i starszą wersją TLS (np. TLS 1.2 nie powiodło się, więc wypróbuj TLS 1.1). To obejście wprowadziło jednak nowy problem — osoba atakująca może wymusić obniżenie poziomu klienta przez sztuczne wprowadzenie błędu sieci lub pakietu powodującego niepowodzenie połączenia z serwerem — nawet jeśli serwer obsługiwał nowszą wersję protokołu TLS. Dzięki spadkowi do starszej wersji osoba atakująca może wykorzystać słabe strony w tej wersji (w szczególności SSLv3<sup>21</sup> jest słaba do ataku POODLE). Aby zapobiec tej sytuacji, w dokumencie RFC 7507 wprowadzenie "rezerwowego scSV", pseudo-ciphersuite<sup>22</sup> wysyłanego w aplikacji ClientHello, który powiadamia serwer TLS, gdy klient TLS korzysta z wersji TLS, która nie jest najnowszą wersją, która obsługuje. Dzięki temu serwer obsługujący nowszą wersję może odrzucić klienta ClientHello zawierającego rezerwowy scSV i zapobiec sukcesowi ataku na starszą wersję.

21. NetX Secure nie implementuje SSLv3 ze względu na istnienie znanych poważnych słabych stron, takich jak POODLE.

22. Pseudoszyfrowanie (SCSV, Signaling Cipher Suite Value) to zastrzeżony numer szyfru, który służy do sygnalizowania włączonych implementacji TLS dotyczących funkcji, które nie były dostępne w starszych wersjach TLS. Przykładami są rezerwowy scSV i TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746).

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **protocol_version** Makro wersji TLS dla określonej wersji TLS do użycia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna zmiana stanu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Znana, ale nieobsługiwana wersja TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Nieprawidłowa wersja protokołu.

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

Odbieranie danych z bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera dane z określonej aktywnej sesji protokołu TLS, obsługujący odszyfrowywanie tych danych przed dostarczeniem ich do wywołującego w NX_PACKET parametru. Jeśli w określonej sesji nie ma żadnych danych w kolejce, wywołanie zostanie wstrzymane na podstawie podanej opcji oczekiwania.

> [!IMPORTANT]
> *Jeśli NX_SUCCESS zostanie zwrócony, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebny.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **packet_ptr** Wskaźnik do przydzielonego wskaźnika pakietu TLS.
- **wait_option** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.
- **NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Odebrany komunikat zakończył się niepowodzeniem podczas sprawdzania skrótu uwierzytelniania.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat zawierał w nagłówku nieznaną wersję protokołu.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Odebrała alert TLS z hosta zdalnego.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Dostarczona sesja TLS nie została zainicjowana.

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

Przypisywanie wywołania zwrotnego, które będzie wywoływane na początku ponownego negocjowania sesji

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wywołanie zwrotne do sesji TLS, które będzie wywoływane za każdym razem, gdy pierwszy komunikat ponownego negocjowania sesji zostanie odebrany z hosta zdalnego.

Funkcja wywołania zwrotnego jest przeznaczona jako powiadomienie do aplikacji o tym, że rozpoczyna się ponowne negocjowanie — aplikacja może zakończyć sesję TLS, zwracając dowolną wartość niezerową z wywołania zwrotnego, co spowoduje zakończenie sesji TLS z błędem. Jeśli aplikacja chce kontynuować ponowną negocjację, wywołanie zwrotne powinno zwrócić NX_SUCCESS.

> [!NOTE]
> *Ze względu na semantykę renegocjowania TLS wywołanie zwrotne zostanie wywołane dla klientów bezpiecznego TLS NetX za każdym razem, gdy z serwera zdalnego zostanie odebrane helloRequest, ale nie wtedy, gdy klient zainicjuje ponowną negocjację. Na serwerach NetX Secure TLS wywołanie zwrotne będzie wywoływane za każdym razem, gdy zostanie odebrane ponowne negocjowanie ClientHello (dowolny klientHello odebrany w kontekście aktywnej sesji TLS). Oznacza to, że wywołanie zwrotne zostanie wywołane niezależnie od tego, czy host zdalny lub aplikacja lokalna zainicjowała ponowne negocjowanie, ponieważ serwer TLS wyśle odpowiedź HelloRequest, na który odpowie klient zdalny.*

NetX Secure TLS implementuje rozszerzenie Secure Renegotiation Inidication z specyfikacji RFC 5746, aby zapewnić, że renegocjacja nie będzie podlegała atakom typu man-in-the-middle.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przypisanie wywołania zwrotnego.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika dla funkcji wywołania zwrotnego lub sesji TLS.

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

Inicjowanie negocjacji ponownego negocjowania sesji z hostem zdalnym

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa inicjuje ponowne *negocjowanie sesji* z połączonym zdalnym hostem TLS. Renegocjacja składa się z drugiego ugody TLS w kontekście wcześniej ustanowionej sesji TLS. Każdy z nowych komunikatów uściślniania jest szyfrowany przy użyciu sesji TLS do momentu wygenerowania nowych kluczy sesji i wymiany komunikatów ChangeCipherSpec, w którym nowe klucze są używane do szyfrowania wszystkich komunikatów.

Ponowne negocjowanie można zainicjować w dowolnym momencie po nawiązywaną sesję TLS. Jeśli próba ponownego negocjowania zostanie podjęta podczas ugody TLS lub przed rozpoczęciem sesji TLS, żadna akcja nie zostanie podjęta.

> [!NOTE]
> *Podczas wywoływania tej usługi zostanie wykonane całe uściślnienie TLS, więc czas do ukończenia i zwrócony stan będą się różnić w zależności od bieżących ustawień I parametrów sesji.*

NetX Secure TLS implementuje rozszerzenie inidication Secure Renegotiation z RFC 5746, aby zapewnić, że renegocjacja nie będzie podlegać atakom typu man-in-the-middle.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **wait_option** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem. Jest on przekazywany do wszystkich usług NetX w ramach TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne ponowne negocjowanie.
- **NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.
- **NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Odebrany komunikat zakończył się niepowodzeniem podczas sprawdzania skrótu uwierzytelniania.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat zawierał w nagłówku nieznaną wersję protokołu.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Odebrała alert TLS z hosta zdalnego.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) Lokalna lub zdalna sesja TLS jest nieaktywna, co uniemożliwia ponowne negocjowanie.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) host zdalny nie podał rozszerzenia SCSV ani rozszerzenia bezpiecznego ponownego negocjowania i w związku z tym nie można przeprowadzić ponownego negocjowania.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Nie zainicjowano podanej sesji TLS.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Alokacja pakietów bazowych nie powiodła się.

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

Wyczyść i zresetuj bezpieczną sesję TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyczyszczysz sesję TLS i resetuje stan tak, jakby sesja została właśnie utworzona, aby można było ponownie użyć istniejącego obiektu sesji TLS dla nowej sesji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji TLS.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.

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

Wysyłanie danych za pośrednictwem bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła dane w podanym NX_PACKET, używając określonej aktywnej sesji TLS i obsługą szyfrowania tych danych przed wysłaniem ich do hosta zdalnego. Jeśli rozmiar ostatniego anonsowanego okna odbiornika jest mniejszy niż to żądanie, usługa opcjonalnie wstrzymuje się na podstawie określonych opcji oczekiwania.

> [!IMPORTANT]
> *Jeśli nie zostanie zwrócony błąd, aplikacja nie powinna zwalniać pakietu po tym wywołaniu. Spowoduje to nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po zakończeniu transmisji.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **packet_ptr** Wskaźnik do pakietu TLS zawierającego dane do wysłania.
- **wait_option** Definiuje sposób zachowania usługi, jeśli żądanie jest większe niż rozmiar okna odbiornika.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.
- **NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Wysyłanie bazowego gniazda TCP nie powiodło się.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Dostarczona sesja TLS nie została zainicjowana.

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

Konfigurowanie wywołania zwrotnego dla usługi TLS do wywołania na początku uściślinia serwera TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływana przez usługę TLS po otrzymaniu komunikatu ClientHello serwera TLS Server. Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie dowolnych rozszerzeń TLS z odebranego komunikatu ClientHello, które wymagają danych wejściowych lub podejmowania decyzji.

Wywołanie zwrotne jest wykonywane z wywołującym blokiem sterowania sesją TLS i tablicą NX_SECURE_TLS_HELLO_EXTENSION obiektów. Tablica obiektów rozszerzeń ma być przekazywana do funkcji pomocnika, która znajdzie i przejmie określone rozszerzenie. Aby uzyskać przykładową funkcję pomocnika, która analizuje rozszerzenia TLS podane w komunikatach powitalnych, zobacz *nx_secure_tls_session_sni_extension_parse*.

Wywołanie zwrotne serwera może również służyć do wybierania aktywnego certyfikatu tożsamości przy *użyciu nx_secure_tls_active_certificate_set* serwera TLS. Najczęściej występuje to w odpowiedzi na rozszerzenie Oznaczanie nazwy serwera (SNI), które umożliwia klientowi TLS wskazanie serwera, z którym próbuje się skontaktować. Zobacz odwołania do *nx_secure_tls_session_sni_extension_parse* i *nx_secure_tls_active_certificate_set,* aby uzyskać więcej informacji.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **func_ptr** Wskaźnik do funkcji wywołania zwrotnego serwera TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna alokacja wskaźnika funkcji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.

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

Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego od klienta TLS

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

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji serwera TLS, które jest dodawane do sesji TLS przy użyciu nx_secure_tls_session_server_callback_set. Wywołanie zwrotne jest wywoływane po otrzymaniu komunikatu ClientHello od zdalnego klienta TLS i dostarcza tablicę dostępnych rozszerzeń (i liczbę rozszerzeń w tablicy). Ta tablica i jej długość mogą być przekazywane bezpośrednio do tej procedury, aby określić, czy istnieje rozszerzenie SNI — jeśli nie, zwracany jest element NX_SECURE_TLS_EXTENSION_NOT_FOUND wskazujący po prostu, że klient nie wybrał urządzenia rozszerzenia SNI (nie jest to błąd).

Jeśli rozszerzenie SNI zostanie znalezione, nazwa DNS X.509 dostarczona przez klienta TLS jest zwracana w dns_name struktury. Obecnie rozszerzenie SNI dostarcza tylko jeden wpis nazwy DNS, który może być używany przez serwer TLS do określenia certyfikatu tożsamości do wysłania do klienta zdalnego.**

Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg SYSTEMR w polu *nx_secure_x509_dns_name* oraz długość ciągu nazwy w nx_secure_x509_dns_name_length *.* Kontrolka NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name danych.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **rozszerzenia** Wskaźnik do tablicy rozszerzeń hello TLS (z wywołania zwrotnego sesji).
- **num_extensions** Liczba rozszerzeń w tablicy (z wywołania zwrotnego sesji).
- **dns_name** Zwróć nazwę DNS podaną w rozszerzeniu SNI.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne analizowanie rozszerzenia.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa tablica rozszerzeń lub wskaźnik sesji TLS.
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) nie znaleziono rozszerzenia SNI.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI był nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

### <a name="see-also"></a>Zobacz też

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Ustawianie nazwy DNS Oznaczanie nazwy serwera (SNI) do wysyłania do serwera zdalnego

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji klienckiej TLS podanie preferowanej nazwy DNS serwera zdalnemu serwerowi TLS przy użyciu rozszerzenia TLS Oznaczanie nazwy serwera (SNI). Rozszerzenie SNI umożliwia serwerowi wybranie odpowiedniego certyfikatu tożsamości i parametrów na podstawie preferencji serwera wskazanego przez klienta. Rozszerzenie SNI obecnie obsługuje tylko jedną nazwę DNS do wysłania, dlatego nazwa pojedyncza parametru. Parametr dns_name musi zostać zainicjowany za pomocą *nx_secure_x509_dns_name_initialize* i będzie zawierać preferowany serwer klienta. Aby cofnić ustawienia nazwy rozszerzenia, po prostu wywołaj tę usługę z wartością parametru "dns_name" NX_NULL.

Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg SYSTEMR w polu *nx_secure_x509_dns_name* oraz długość ciągu nazwy w nx_secure_x509_dns_name_length *.* Kontrolka NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name danych.

> [!NOTE]
> *Ta procedura musi zostać wywołana nx_secure_tls_session_start wywoływania lub ClientHello nie będzie zawierać rozszerzenia SNI.*

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **dns_name** Nazwa DNS dostarczana przez aplikację.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie nazwy serwera DNS.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa nazwa DNS lub wskaźnik sesji TLS.

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

Uruchamianie bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sesję protokołu TLS przy użyciu dostarczonego bloku sterowania sesją protokołu TLS i połączonego gniazda TCP. Połączenie TCP musi być już ukończone po pomyślnym wywołaniu nx_tcp_client_socket_connect lub nx_tcp_server_socket_accept.

Ta usługa określi typ sesji protokołu TLS (klient lub serwer) z gniazda TCP.

Opcja oczekiwania definiuje sposób zachowania usługi w czasie, gdy trwa uściślanie TLS.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **tcp_socket_ptr** Wskaźnik do połączonego gniazda TCP.
- **wait_option** Definiuje sposób zachowania usługi w czasie, gdy trwa uściślanie TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Odebrany typ komunikatu TLS jest niepoprawny.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Przetwarzanie komunikatów podczas uściśniania TLS nie powiodło się.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Komunikat przychodzący nie może sprawdzić skrótu ADRESU MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Nie można wysłać bazowego gniazda TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Komunikat przychodzący miał pole o nieprawidłowej długości.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Przychodzący komunikat ChangeCipherSpec był niepoprawny.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Przychodzący certyfikat TLS nie można zidentyfikować zdalnego serwera TLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Szyfr klucza publicznego dostarczony przez hosta zdalnego nie jest obsługiwany.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Host zdalny nie zaznaczył żadnych szyfrów, które są obsługiwane przez stos bezpiecznego szyfrowania TLS netx.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat TLS miał w nagłówku nieznaną wersję TLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Odebrany komunikat TLS miał w nagłówku znaną, ale nieobsługiwaną wersję TLS.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Wewnętrzna alokacja pakietów TLS nie powiodła się.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny podał nieprawidłowy certyfikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Host zdalny wysłał alert wskazujący błąd i kończący sesję TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Wpis w tabeli ciphersuite miał wskaźnik funkcji NULL.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) Zdalny klient TLSHello obejmował rezerwowy system SCSV i dodał rezerwowy dostęp do wersji.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.

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

Przypisywanie funkcji znacznika czasu do bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Opis

Ta funkcja konfiguruje wskaźnik funkcji, który będzie wywoływany przez TLS, gdy będzie on wymagał uzyskania bieżącego czasu, który jest używany w różnych komunikatach uściślniania TLS i do weryfikacji certyfikatów.

Oczekuje się, że funkcja zwróci bieżący czas GMT w 32-bitowym formacie systemu UNIX (w sekundach od północy od 1 stycznia 1970 r. czasu UTC, ignorując sekundy przestępne) zgodnie z wymaganiami clientHello w dokumencie TLS RFC 5246.

Jeśli żadna funkcja znacznika czasu nie zostanie przypisana, zostanie użyta wartość 0 dla sygnatury czasowej w uściśli TLS, a sprawdzanie wygaśnięcia certyfikatu nie będzie działać.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do wystąpienia sesji TLS.
- **time_func_ptr** Wskaźnik do funkcji, która zwraca bieżący czas (GMT) w 32-bitowym formacie systemu UNIX.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji TLS.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.

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

Dodawanie zaufanego certyfikatu do bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Opis

Ta usługa dodaje zainicjowane wystąpienie NX_SECURE_X509_CERT struktury do sesji TLS. Ten certyfikat jest używany przez stos TLS do weryfikowania certyfikatów dostarczonych przez hosta zdalnego podczas uściśniania TLS.

Zaufane certyfikaty są wymagane w trybie klienta TLS.

Zaufane certyfikaty są wymagane tylko w trybie serwera TLS, jeśli jest włączone uwierzytelnianie certyfikatu klienta.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **certificate_ptr** Wskaźnik do zainicjowanych wystąpień certyfikatu TLS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.
- **NX_INVALID_PARAMETERS** (0x4D) Próbowano dodać nieprawidłowy certyfikat.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.

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

Usuwanie zaufanego certyfikatu z bezpiecznej sesji TLS netx

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Opis

Ta usługa usuwa zaufany certyfikat z sesji TLS z kluczem w polu Nazwa pospolita w certyfikacie.

### <a name="parameters"></a>Parametry

- **session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.
- **common_name** Wartość nazwa pospolita certyfikatu do usunięcia.
- **common_name_length** Długość ciągu nazwy pospolitej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Nie znaleziono certyfikatu.

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

Inicjowanie certyfikatu X.509 dla bezpiecznego TLS NetX

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

Ta usługa inicjuje strukturę NX_SECURE_X509_CERT z zakodowanym binarnie certyfikatem cyfrowym X.509 do użycia w sesji TLS.

Dane certyfikatu muszą **być prawidłowym** certyfikatem cyfrowym X.509 w formacie binarnym zakodowanym w formacie DER. Dane mogą pochodzić z dowolnego źródła (np. systemu plików, skompilowanego bufora stałego itp.), o ile jest dostarczany wskaźnik FUNKCJI SYSTEMR do tych danych.

Parametr *raw_data_buffer* i jego rozmiar są opcjonalnymi parametrami określającymi dedykowany bufor, do którego dane certyfikatu są kopiowane przed analizą. Jeśli raw_data_buffer jako NX_NULL, struktura NX_SECURE_X509_CERT będzie bezpośrednio wskazać tablicę certificate_data (w tym przypadku buffer_size jest ignorowana). Jeśli raw_data_buffer jako ***NX_NULL,*** nie należy modyfikować danych wskazywanych przez wskaźnik certificate_data lub przetwarzanie certyfikatu prawdopodobnie nie powiedzie się!

Parametr klucza prywatnego jest używany dla certyfikatów tożsamości lokalnej — klucz prywatny jest używany przez serwery do odszyfrowywania danych klucza przychodzącego od klienta (zaszyfrowanych przy użyciu klucza publicznego serwera) i przez klientów w celu zweryfikowania ich tożsamości na serwerze, gdy serwer zażąda certyfikatu klienta. Dodanie klucza prywatnego za pomocą tego interfejsu API spowoduje automatyczne oznaczenie skojarzonego certyfikatu jako certyfikatu tożsamości dla aplikacji TLS. Podczas inicjowania certyfikatów do innych celów (np. zaufanego magazynu) parametr private_key_data powinien być  przekazywany jako wartość NULL, private_key_data_length  jako 0, *a* private_key_type jako NX_SECURE_X509_KEY_TYPE_NONE.

Parametr *private_key_type* wskazuje formatowanie klucza prywatnego. Jeśli na przykład klucz prywatny jest kluczem prywatnym RSA w formacie PKCS#1 w formacie DER, klucz private_key_type powinien zostać przekazany jako NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, typ znany netx secure, który zostanie natychmiast przejrzeny i zapisany do późniejszego użycia.

Interfejs private_key_type również zdefiniowane przez użytkownika typy kluczy<sup>23</sup> dla platform i aplikacji, które mają określone formaty kluczy lub inne potrzeby. Na przykład sprzętowy aparat szyfrowania może używać określonego formatu, który nie jest zrozumiały dla oprogramowania NetX Secure, lub klucz prywatny może być zaszyfrowany lub reprezentowany przez token kryptograficzny, jak w przypadku sprzętu kryptograficznego Trusted Platform Module (TPM) lub PKCS#11. W przypadku użycia typu klucza zdefiniowanego przez użytkownika dane klucza są przekazywane dosłownie do odpowiedniej procedury kryptograficznej — na przykład klucz prywatny RSA zostanie przekazany, bez analizowania lub przetwarzania, bezpośrednio do procedury kryptograficznej RSA dostarczonej do TLS w tabeli szyfrowania. Typ klucza zdefiniowanego przez użytkownika jest również przekazywany do procedury kryptograficznych (w przypadku RSA jest to parametr "op").

Zakres kluczy zdefiniowanych przez użytkownika obejmuje górną połowę 32-bitowej liczby całkowitej bez znaku, od 0x0001 0000-0xFFFF FFFF. Wartości mniejsze niż 0x0001 0000 są zarezerwowane do użycia z użyciem funkcji NetX Secure.

Typy kluczy zdefiniowane przez użytkownika to zaawansowana funkcja, która wymaga niestandardowych procedur kryptograficznych do obsługi nieprzetworzonych danych klucza prywatnego. Jeśli potrzebujesz tej funkcji, skontaktuj się z przedstawicielem firmy Express Logic.

### <a name="parameters"></a>Parametry

- **certificate_ptr** Wskaźnik do niezainicjowanych wystąpień certyfikatu X.509.
- **certificate_data** Wskaźnik do danych binarnych X.509 zakodowanych w formacie DER.
- **raw_data_buffer** Wskaźnik do opcjonalnego buforu danych dedykowanego certyfikatu.
- **buffer_size** Rozmiar opcjonalnego buforu danych dedykowanego certyfikatu.
- **certificate_data_length** Długość danych binarnych certyfikatu w bajtach.
- **private_key_data** Wskaźnik do opcjonalnych danych klucza prywatnego.
- **private_key_data_length** Długość danych klucza prywatnego.
- **private_key_type** Identyfikator typu klucza.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate (Dane certyfikatu X.509 zakodowane w formacie DER).
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) nie ma szyfru klucza publicznego, który jest obsługiwany przez usługę NetX Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Klucz prywatny lub certyfikat nie zawiera prawidłowej sekwencji ASN.1.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) Podany klucz prywatny nie był prawidłowym kluczem PKCS#1 RSA.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) Podany typ klucza prywatnego nie został zdefiniowany przez użytkownika i nie pasuje do żadnego znanego typu.

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
- Importowanie certyfikatów X.509 do usługi NetX Secure w rozdziale 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Sprawdzanie nazwy DNS względem certyfikatu X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Opis

Ta usługa sprawdza nazwę pospolitą certyfikatu względem nazwy top-domain name (TLD) dostarczonej przez wywołującego na potrzeby weryfikacji DNS hosta zdalnego. Ta funkcja narzędzia jest przeznaczona do wywoływania z procedury wywołania zwrotnego weryfikacji certyfikatu dostarczonej przez aplikację. Nazwa TLD powinna być górną częścią adresu URL używanego do uzyskiwania dostępu do hosta zdalnego ("." ciąg rozdzielany przed pierwszym ukośnikiem). Jeśli nazwa pospolita zawiera symbol wieloznaczny (na przykład example.com), symbol wieloznaczny będzie odpowiadać dowolnej z *tym samym sufiksem. Należy* pamiętać, że tylko pierwszy symbol wieloznaczny (" ") napotkany (odczytywanie od prawej do lewej)  będzie traktowany jako dopasowywanie symboli wieloznacznych — na przykład abc.*.example.com będzie pasować do dowolnej nazwy kończącej się na ".example.com".

Jeśli nazwa pospolita nie pasuje do podanego ciągu, rozszerzenie "subjectAltName" jest analizowane (jeśli istnieje w certyfikacie), a wszystkie wpisy DNSName również są porównywane. Jeśli żaden z tych wpisów nie pasuje, zwracany jest błąd.

Ważne jest, aby zrozumieć format nazwy pospolitej (i wpisów subjectAltName) w oczekiwanych certyfikatach. Na przykład niektóre certyfikaty mogą używać nieprzetworzowego adresu IP lub symbolu wieloznaowego. Ciąg TLD systemu DNS musi być sformatowany w taki sposób, aby był on taki, aby był zgodne z oczekiwanymi wartościami w odebranych certyfikatach.

### <a name="parameters"></a>Parametry

- **certificate_ptr** Wskaźnik do wystąpienia certyfikatu X.509.
- **dns_tld** Top-Level nazwa domeny do porównania.
- **dns_tld_length** Długość ciągu TLD.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne porównanie z nazwą pospolitą lub subjectAltName.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) Nie znaleziono pasującej nazwy.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.

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

Sprawdź certyfikat X.509 względem podanej listy odwołania certyfikatów (CRL)

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Opis

Ta usługa pobiera listę odwołania certyfikatów zakodowaną w formacie DER i wyszukuje określony certyfikat na tej liście. Wystawca listy CRL jest weryfikowany względem podanego magazynu certyfikatów, wystawca listy CRL jest weryfikowany jako taki sam jak wystawca sprawdzanego certyfikatu, a numer seryjny certyfikatu jest używany do przeszukiwania listy odwołanych certyfikatów. Jeśli wystawcy są zgodne, podpis jest sprawdzany, a certyfikatu nie ma na liście, wywołanie zostanie pomyślnie wywołane.  Wszystkie inne przypadki powodują zwrócenie błędu.

### <a name="parameters"></a>Parametry

- **crl_data** Wskaźnik do listy CRL zakodowanej w formacie DER.
- **crl_length** Długość w bajtach danych listy CRL.
- **store (sklep)** Wskaźnik do magazynu certyfikatów X.509.
- **certificate_ptr** Wskaźnik do wystąpienia certyfikatu X.509.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna weryfikacja, czy certyfikat nie został odwołany.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) nie znaleziono certyfikatu wystawcy listy CRL.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Nie znaleziono certyfikatu wystawcy certyfikatu.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Listy CRL ASN.1 zawierała pole o nieprawidłowej długości.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** Listy CRL zawiera nieprawidłowy asn.1.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Weryfikacja łańcucha certyfikatów nie powiodła się.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) listy CRL i wystawców certyfikatów nie są zgodne.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) Podpis listy CRL był nieprawidłowy.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) Sprawdzany certyfikat został znaleziony na cRL i dlatego został odwołany.
- **NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.

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

Inicjowanie struktury nazw DNS X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Opis

Ta usługa inicjuje nazwę DNS X.509 do użycia z niektórymi usługami interfejsu API wymagającymi określonego formatu nazwy. Na przykład usługa *nx_secure_tls_sni_extension_parse* oczekuje obiektu NX_SECURE_X509_DNS_NAME, aby dopasować nazwę podaną przez hosta zdalnego w rozszerzeniu Oznaczanie nazwy serwera podczas ugody TLS. Nazwa DNS jest po prostu ciągiem znaków o długości — maksymalna dozwolona długość nazwy DNS (i rozmiar wewnętrznego buforu w programie NX_SECURE_X509_DNS_NAME) jest kontrolowana przez znak makra NX_SECURE_X509_DNS_NAME_MAX (domyślnie 100 bajtów).

### <a name="parameters"></a>Parametry

- **dns_name** Struktura nazw DNS do zainicjowania.
- **name_string** Dane ciągu nazwy DNS.
- **długość** Długość ciągu nazwy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) Podany ciąg nazwy przekroczył NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.

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

Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X.509 w certyfikacie X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set).* Wyszuka określony rozszerzony OID użycia klucza w ramach certyfikatu X.509 i zwróci, czy OID jest obecny. Parametr key_usage jest mapowaniem liczb całkowitych identyfikatorów OID, które są używane wewnętrznie przez netX Secure X.509 i TLS, aby uniknąć przekazywania ciągów identyfikatorów OID o zmiennej długości jako parametrów.

Odpowiednie identyfikatory ID dla rozszerzenia rozszerzonego użycia klucza zostały podane w poniższej tabeli. Typowa implementacja klienta TLS, która chce sprawdzić rozszerzone użycie klucza w odebranym certyfikacie serwera TLS, sprawdza istnienie OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH — jeśli rozszerzenie jest obecne, ale ten identyfikator OID nie jest, certyfikat zostanie uznany za nieprawidłowy dla identyfikacji hosta jako serwera TLS, a wywołanie zwrotne weryfikacji certyfikatu powinno zwrócić błąd. Jeśli brakuje samego rozszerzenia, to aplikacja może kontynuować ugodę TLS.

W wywołaniu zwrotym weryfikacji certyfikatu kod powrotny NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użycia aplikacji. Jeśli wystąpił błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę błędu.

| NetX Secure Identifier                                | Wartość OID         | Opis                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | Certyfikat może służyć do identyfikowania serwera TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | Certyfikat może służyć do identyfikowania klienta TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | Certyfikat może służyć do podpisywania kodu             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | Certyfikat może służyć do podpisywania wiadomości e-mail           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | Certyfikat może służyć do podpisywania znaczników czasu       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | Certyfikat może służyć do podpisywania odpowiedzi OCSP   |

Identyfikatory ID i mapowania dla rozszerzenia rozszerzonego użycia klucza X.509

### <a name="parameters"></a>Parametry

- **certyfikat** Wskaźnik do weryfikowanego certyfikatu.
- **key_usage** Mapowanie liczb całkowitych OID z tabeli powyżej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Znaleziono określony OID użycia klucza.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) NAPOTKANO tag ASN.1 (nieobsługiwany certyfikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Napotkano pole Invaild ASN.1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Napotkano nieprawidłową klasę tagów ASN.1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Napotkano nieprawidłowe rozszerzenie (nieprawidłowy certyfikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Rozszerzenie Rozszerzone użycie klucza nie zostało znalezione w dostarczonym certyfikacie.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik certyfikatu.

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

Znajdowanie i zwracanie rozszerzenia X.509 w certyfikacie X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)* i jest zaawansowaną usługą X.509.

Funkcja wyszuka określone rozszerzenie w certyfikacie X.509 na podstawie OID i zwróci, czy OID jest obecny, wraz ze strukturą zawierającą odwołania do odpowiednich nieprzetworzonych danych rozszerzenia. Parametr extension_id jest mapowaniem liczb całkowitych identyfikatorów OID, które są używane wewnętrznie przez netx secure X.509 i TLS, aby uniknąć przekazywania ciągów OID o zmiennej długości jako parametrów.

Funkcje pomocnika udostępniane dla określonych rozszerzeń (takich jak *nx_secure_x509_key_usage_extension_parse*) wywołują nx_secure_x509_extension_find w celu uzyskania danych rozszerzenia.

Odpowiednie identyfikatory ID dla znanych rozszerzeń X.509 zostały podane w poniższej tabeli.

Struktura NX_SECURE_X509_EXTENSION zawiera wskaźniki do certyfikatu X.509, które umożliwiają funkcji pomocników, takich jak *nx_secure_x509_key_usage_extension_parse,* szybkie dekodowanie nieprzetworzonych danych ASN.1 zakodowanych w formacie DER rozszerzenia.

Aby uzyskać informacje na temat określonych rozszerzeń, zobacz RFC 5280 (specyfikacja X.509) lub odwołanie do odpowiednich funkcji pomocnika, jeśli są dostępne.

Bieżąca wersja netX Secure X.509 ma ograniczoną obsługę rozszerzeń X.509. Więcej funkcji pomocnika zostanie dodanych w przyszłości.

> [!IMPORTANT]
> *Ta usługa jest zaawansowaną funkcją dla użytkowników zaznajomieni z rozszerzeniami X.509 i asn.1 zakodowanym w formacie DER. Jest on dostarczany w celu umożliwienia tym użytkownikom dostępu do rozszerzeń, dla których program NetX Secure X.509 obecnie nie zapewnia funkcji pomocnika. W przypadku tych rozszerzeń bez funkcji pomocnika musisz samodzielnie analizujeć kodowanie ASN.1 w formacie DER.*

| NetX Secure Identifier                              | Wartość OID | Opis                                                                    | Funkcja pomocnika? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Atrybuty katalogu — podstawowe atrybuty informacyjne dotyczące podmiotu certyfikatu  | Nie               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Służy do identyfikowania określonego klucza publicznego                                         | Nie               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Zawiera informacje na temat prawidłowych zastosowań klucza publicznego certyfikatu              | Tak              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Udostępnia alternatywne nazwy DNS do identyfikowania certyfikatu                     | Tak<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Udostępnia alternatywne nazwy DNS do identyfikowania wystawcy certyfikatu            | Nie               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Zawiera podstawowe informacje o ograniczeniach użycia certyfikatu                        | Nie               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Służy do ograniczania nazw certyfikatów do określonych domen                        | Nie               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Udostępnia adresy URI dla dystrybucji listy CRL                                             | Nie               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Lista zasad certyfikatów dla dużych systemów PKI                             | Nie               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Lista zasad certyfikatów urzędu certyfikacji                                                | Nie               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Służy do identyfikowania określonego klucza publicznego skojarzonego z podpisem certyfikatu | Nie               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Ograniczenia zasad urzędu certyfikacji                                                          | Nie               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Dodatkowe informacje o użyciu klucza oparte na OID                                     | Tak              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Zawiera informacje dotyczące uzyskiwania różnicowych listy CRL                                  | Nie               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Pole certyfikatu urzędu certyfikacji wskazujące, że nie można użyć anyPolicy                  | Nie               |

Identyfikatory ID i mapowania rozszerzeń X.509

24. Rozszerzenie SubjectAltName jest analizowane w ramach sprawdzania nazwy DNS w usłudze nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Parametry

- **certyfikat** Wskaźnik do weryfikowanego certyfikatu.
- **rozszerzenie** Zwracana struktura zawierająca wskaźnik danych rozszerzenia i długość.
- **extension_id** Mapowanie liczb całkowitych OID z tabeli powyżej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Znaleziono określony OID rozszerzenia i zwrócono dane.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) NAPOTKANO tag ASN.1 (nieobsługiwany certyfikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Napotkano pole Invaild ASN.1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Napotkano nieprawidłową klasę tagów ASN.1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Napotkano nieprawidłowe rozszerzenie
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Podany OID rozszerzenia nie został znaleziony w dostarczonym certyfikacie.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy certyfikat lub wskaźnik rozszerzenia.

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

Znajdowanie i analizowanie rozszerzenia X.509 Key Usage w certyfikacie X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Opis

Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set).* Wyszuka rozszerzenie Użycie klucza i jeśli zostanie znalezione, zwróci pole bitowe Użycie klucza w parametrze "bitfield".

Bity zgodnie ze specyfikacją X.509 (RFC 5280) zostały podane w poniższej tabeli. Bitowe AND z odpowiednią maski bitów (i sprawdzanie, czy wartość jest równa zero) daje wartość każdego bitu.

Należy pamiętać, że kodowanie DER pola bitowego eliminuje dodatkowe zera, więc rzeczywista pozycja bitów w nieprzetworzonych danych certyfikatu prawdopodobnie będzie się różnić od ich pozycji w zdekodowanych polach bitowych. Podane maski bitowe są przeznaczone tylko do używać w zdekodowanych polach bitowych zwracanych przez *nx_secure_x509_key_usage_extension_parse,* a nie w nieprzetworzonych danych certyfikatu zakodowanych w formacie DER.

W wywołaniu zwrotym weryfikacji certyfikatu kod powrotny NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użycia aplikacji. Jeśli wystąpił błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę błędu.

| NetX Secure Identifier                            | Położenie bitowe | Opis                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | Certyfikat może służyć do podpisów cyfrowych                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | Certyfikat może służyć do weryfikowania podpisów cyfrowych innych niż te dla certyfikatów i list CRL                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | Certyfikat może służyć do szyfrowania kluczy symetrycznych (transportu kluczy)                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | Certyfikat może służyć do bezpośredniego szyfrowania nieprzetworzonych danych użytkownika (nietypowe)                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | Certyfikat może być używany do umowy kluczy (podobnie jak w przypadku Diffie'ego-Hellmana)                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | Certyfikat może służyć do podpisywania i weryfikowania innych certyfikatów (certyfikat jest certyfikatem urzędu certyfikacji lub ICA).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | Klucz publiczny certyfikatu służy do weryfikowania podpisów list CRL                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Używany z bitem umowy klucza (bit 4) — po jego skonfigurowaniu klucz certyfikatu może być używany tylko do szyfrowania podczas umowy klucza. Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Używany z bitem umowy klucza (bit 4) — w przypadku ustawienia klucz certyfikatu może być używany tylko do odszyfrowywania podczas umowy klucza. Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony. |

Maski bitowe i wartości rozszerzenia X.509 użycia klucza

### <a name="parameters"></a>Parametry

- **certyfikat** Wskaźnik do weryfikowanego certyfikatu.
- **bitfield** Zwróć całe pola bitowe z rozszerzenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Znaleziono rozszerzenie użycia klucza i zwrócono element bitfield.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) NAPOTKANO tag ASN.1 (nieobsługiwany certyfikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Napotkano pole Invaild ASN.1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Napotkano nieprawidłową klasę tagów ASN.1 (nieprawidłowy certyfikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Napotkano nieprawidłowe rozszerzenie (nieprawidłowy certyfikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)Rozszerzenie Użycie klucza nie zostało znalezione w dostarczonym certyfikacie.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy certyfikat lub wskaźnik pola bitowego.

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
