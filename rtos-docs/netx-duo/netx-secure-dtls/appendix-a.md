---
title: Dodatek A — usługa Azure RTO NetX Secure DTLS kody powrotu/błędów
description: Wyświetla listę możliwych kodów błędów, które mogą być zwracane przez usługę Azure RTO NetX Secure DTLS Services.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: reference
ms.service: rtos
ms.openlocfilehash: f14f27167a95a1b9d3ebbdf0d903be7b043ccb28
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821601"
---
# <a name="appendix-a-azure-rtos-netx-secure-dtls-returnerror-codes"></a>Dodatek A: Azure RTO NetX Secure DTLS zwroty/kody błędów

## <a name="netx-secure-tlsdtls-return-codes"></a>NetX Secure TLS/DTLS kody powrotne

W tabeli 1 poniżej wymieniono możliwe kody błędów, które mogą zostać zwrócone przez usługę Azure RTO NetX Secure DTLS Services. Należy zauważyć, że usługi mogą również zwracać kody błędów UDP lub IP — wartości TLS zaczynają się od 0x101, a wartości TCP/IP/UDP są poniżej 0x100. Wartości zwrotne X. 509 zaczynają się od 0x181. Zapoznaj się z dokumentacją protokołu TCP/IP/UDP NetX, aby uzyskać informacje na temat wartości zwrotnych adresów IP i UDP i poniżej przedstawiono wartości X. 509.

| **Nazwa błędu**                                        | **Wartość** | **Opis**                                                                                                                                               |
| ----------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_TLS_SUCCESS                              | 0x00      | Pomyślnie zwrócono funkcję. (Analogicznie jak NX_SUCCESS).                                                                                                        |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101     | Główna pętla protokołu TLS została wywołana z niezainicjowanym gniazdem.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102     | Warstwa rekordu TLS otrzymała nierozpoznany typ komunikatu.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103     | Błąd wewnętrzny — stan nie został rozpoznany.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104     | Błąd wewnętrzny — odebrany pakiet nie zawiera danych TLS.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105     | Wybrany ciphersuite nie jest obsługiwany — wewnętrzny błąd serwera dla klienta oznacza, że host zdalny wysłał zły ciphersuite (błąd lub atak).            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106     | W trakcie szyfrowania lub odszyfrowywania wybrana wartość szyfrowania jest wyłączona lub niedostępna.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107     | Coś w przetwarzaniu komunikatów podczas uzgadniania nie powiodło się.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108     | Rekord przychodzący ma komputer MAC, który nie jest zgodny z wygenerowanym.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109     | Z jakiegoś powodu wychodzące wysyłanie protokołu TCP rekordu nie powiodło się.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH           | 0x10A     | Komunikat przychodzący miał nieprawidłową długość (zazwyczaj długość inną niż jedna w nagłówku, jak w komunikatach certyfikatu).                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B     | Komunikat przychodzący ChangeCipherSpec jest nieprawidłowy.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C     | Certyfikat serwera przychodzącego nie został poprawnie przeanalizowany.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D     | Certyfikat dostarczony przez serwer określił niewspieraną operację klucza publicznego.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E     | Odebrano element komunikacie ClientHello bez obsługiwanego ciphersuites.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F     | Rekord przychodzący ma nierozpoznaną wersję protokołu TLS.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110     | Rekord przychodzący ma prawidłową wersję protokołu TLS, ale nie jest obsługiwany.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111     | Wewnętrzny przydział pakietu dla komunikatu TLS nie powiódł się.                                                                                                       |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112     | Certyfikat x509 nie został poprawnie przeanalizowany.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113     | Podczas zamykania sesji TLS nie odebrano elementu CloseNotify z hosta zdalnego.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114     | Host zdalny wysłał alert, wskazując błąd i zamykając połączenie.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115     | Odebrana wartość skrótu komunikatu kończącego nie jest zgodna z wygenerowanym uszkodzeniem zgodności.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM        | 0x116     | Certyfikat podczas weryfikacji miał nieobsługiwany algorytm podpisu.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED      | 0x117     | Sprawdzenie poprawności podpisu certyfikatu nie powiodło się — dane certyfikatu nie pasują do sygnatury.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD             | 0x118     | Odebrano komunikat Hello z nieobsługiwaną metodą kompresji.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND              | 0x119     | W operacji na liście certyfikatów nie znaleziono zgodnego certyfikatu.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT          | 0x11A     | Host zdalny wysłał certyfikat z podpisem własnym, a NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES nie jest zdefiniowany.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND      | 0x11B     | Odebrano certyfikat zdalny z wystawcą nieznajdującym się w lokalnym zaufanym magazynie.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE              | 0x11C     | Komunikat DTLS został odebrany w niewłaściwej kolejności — prawdopodobnie przyczyna.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                | 0x11D     | Odebrano pakiet z hosta zdalnego, którego nie rozpoznajemy.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                       | 0x11E     | Komunikat DTLS został odebrany i dopasowany do sesji DTLS, ale miał nieprawidłową epokę i powinien zostać zignorowany.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED            | 0x11F     | Odebrano komunikat DTLS z numerem sekwencyjnym, który już się widzimy.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                  | 0x120     | Sesja TLS została użyta w interfejsie API DTLS, który nie został zainicjowany dla DTLS.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                   | 0x121     | Sesja TLS została użyta w interfejsie API TLS, który został zainicjowany dla DTLS, a nie TLS.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH              | 0x122     | Obiekt wywołujący próbował wysłać dane za pośrednictwem sesji DTLS z adresem IP lub portem, który nie jest zgodny z sesją.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS             | 0x123     | Nowe połączenie podjęło próbę pobrania sesji DTLS z pamięci podręcznej, ale nie było żadnych bezpłatnych.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                 | 0x124     | Obiekt wywołujący przeszukał sesję DTLS, ale dany adres IP i port nie pasują do żadnych wpisów w pamięci podręcznej.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                 | 0x125     | Obiekt wywołujący próbował dodać PSK do sesji TLS, ale nie było więcej miejsca w danej sesji.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                    | 0x126     | Host zdalny podał wskazówkę dotyczącą tożsamości PSK, która nie pasuje do żadnego z naszych magazynów lokalnych.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED              | 0x127     | Sesja TLS otrzymała alert CloseNotify od hosta zdalnego wskazującego, że sesja została ukończona.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS              | 0x128     | W obiekcie TLS nie są dostępne żadne sesje TLS obsługujące połączenie.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED           | 0x129     | Nie przydzielono żadnego miejsca na certyfikacie dla przychodzących certyfikatów zdalnych.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED               | 0x12A     | Dopełnienie szyfrowania w komunikacie przychodzącym jest niepoprawne.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE        | 0x12B     | W trakcie przetwarzania CertificateVerifyRequest serwer zdalny nie dostarczył obsługiwanego typu certyfikatu.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG         | 0x12C     | W trakcie przetwarzania elementu CertificateVerifyRequest żaden obsługiwany algorytm podpisu nie został dostarczony przez serwer zdalny.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE            | 0x12D     | Nie przydzielono wystarczającej ilości miejsca w buforze certyfikatów dla certyfikatu.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED           | 0x12E     | Wersja protokołu w rekordzie przychodzącego protokołu TLS nie jest zgodna z wersją ustanowionej sesji.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR             | 0x12F     | Odebrano komunikat HelloRequest, ale nie można przeprowadzić ponownej negocjacji.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                 | 0x130     | Napotkano funkcję, która została wyłączona podczas sesji TLS lub uzgadniania.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE         | 0x131     | Komunikat CertificateVerify ze zdalnego klienta nie mógł zweryfikować certyfikatu klienta.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED | 0x132     | Host zdalny wysłał komunikat o pustym certyfikacie.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR      | 0x133     | Wystąpił błąd podczas przetwarzania lub wysyłania rozszerzenia wskazania bezpiecznego Renegotation.                                                                     |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE     | 0x134     | Podjęto próbę przeprowadzenia ponownej negocjacji sesji z sesją TLS, która nie jest aktywna.                                                                                |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL           | 0x135     | Protokół TLS otrzymał rekord, który był za duży dla przypisanego buforu pakietów. Nie można przetworzyć rekordu.                                                   |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                | 0x136     | Określone rozszerzenie nie zostało odebrane z hosta zdalnego podczas uzgadniania TLS.                                                                         |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID              | 0x137     | Protokół TLS otrzymał nieprawidłowe rozszerzenie Oznaczanie nazwy serwera.                                                                                                     |
| NX_SECURE_TLS_CERT_ID_INVALID                    | 0x138     | Aplikacja podjęła próbę dodania certyfikatu serwera z nieprawidłową wartością identyfikatora certyfikatu (może to być 0).                                                                |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                  | 0x139     | Aplikacja podjęła próbę dodania certyfikatu serwera z IDENTYFIKATORem certyfikatu znajdującego się już w magazynie lokalnym.                                                       |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE               | 0x13A     | Host zdalny nie dostarczył rozszerzenia wskazania bezpiecznego renegocjacji lub ciphersuite SCSV, więc nie można wykonać bezpiecznej ponownej negocjacji.     |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE             | 0x13B     | Podczas próby wykonania operacji kryptograficznej jeden z wpisów w tabeli ciphersuite (lub jeden z jego wskaźników funkcji) został nieprawidłowo ustawiony na wartość NULL. |

**Tabela 1 — kody powrotu bezpiecznego protokołu TLS NetX**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X. 509 kodów powrotu

W tabeli 2 poniżej wymieniono możliwe kody błędów, które mogą zostać zwrócone przez NetX Secure X. 509 usług. Należy zauważyć, że usługi mogą również zwracać inne kody błędów. Wartości zwracane X. 509 zaczynają się od 0x181, wartości TLS zaczynają się od 0x101, a wartości protokołu TCP/IP są poniżej 0x100. Zapoznaj się z dokumentacją protokołu TCP/IP NetX, aby uzyskać informacje na temat wartości zwracanych przez protokół TCP/IP i powyżej dla wartości zwracanych przez protokół TLS.

| **Nazwa błędu**                                   | **Wartość** | **Opis**                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | Stan pomyślnego powrotu. (Analogicznie jak NX_SUCCESS)                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | Znaleźliśmy wiele bajtów ASN. 1 — nie jest to obecnie obsługiwane.                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | Napotkano wartość długości dłuższą niż możemy obsłużyć.                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | Oczekiwano wartości dopełnienia równej 0 — uzyskano coś innego.                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | W przypadku certyfikatu x509 oczekiwano klucza publicznego, ale go nie znaleziono.                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | Znaleziono klucz publiczny, ale jest nieprawidłowy lub ma niepoprawny format.                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | Blok ASN. 1 najwyższego poziomu nie jest sekwencją nieprawidłowego certyfikatu x509.                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | Oczekiwano identyfikatora algorytmu podpisu, jego nie znaleziono.                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | Dane tożsamości certyfikatu mają nieprawidłowy format.                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | Oczekujemy, że w formacie x509 został określony tag ASN. 1, ale mamy coś innego.                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | Przekazano plik klucza prywatnego PKCS # 1, ale formatowanie było nieprawidłowe.                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | Łańcuch certyfikatów x509 był zbyt krótki, aby pomieścić cały łańcuch podczas tworzenia łańcucha.                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | Nie można zweryfikować łańcucha certyfikatów x509 (błąd przechwytywania wszystkiego).                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | Analizowanie sygnatury kodowanej w formacie X. 509 PKCS # 7 nie powiodło się.                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | W trakcie wyszukiwania certyfikatu nie znaleziono pasującego wpisu.                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | Certyfikat zawiera pole, które nie jest zgodne z podaną wersją.                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | Certyfikat zawiera tag ASN. 1 z nieprawidłową wartością klasy tag.                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | Certyfikat zawierał obiekt TLV rozszerzeń, ale nie zawiera sekwencji.                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | Certyfikat zawiera sekwencję rozszerzenia, która była nieprawidłowym X. 509.                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | Certyfikat ma pole "nie po", które było mniejsze od bieżącego czasu.                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | Dla certyfikatu określono wartość pola "nie wcześniej", która była późniejsza niż bieżąca godzina.                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | Nazwa pospolita certyfikatu lub alternatywna nazwa podmiotu nie pasuje do danego systemu DNS.                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | Certyfikat zawierał pole daty, które nie jest w formacie recognixed.                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | Podana lista CRL i certyfikat nie zostały wystawione przez ten sam urząd certyfikacji.                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | Sprawdzenie podpisu listy CRL nie powiodło się dla jego wystawcy.                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | Znaleziono certyfikat w prawidłowej liście CRL i dlatego został on odwołany.                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | Podczas próby zweryfikowania sygnatury Metoda podpisu nie pasuje do oczekiwanej metody.                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | Podczas wyszukiwania rozszerzenia nie znaleziono rozszerzenia o pasującym IDENTYFIKATORze.                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | Wyszukano nazwę w rozszerzeniu subjectAltName, ale nie znaleziono tego elementu.                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | Podany typ klucza prywatnego jest nieznany lub nieprawidłowy.                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | Przekazano ciąg nazwy, który był zbyt długi dla buforu wewnętrznego (nazwa DNS itd.).                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | Podczas wyszukiwania rozszerzenia rozszerzonego użycia klucza nie znaleziono określonego identyfikatora OID.                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | Do zwrócenia przez wywołanie zwrotne aplikacji w przypadku wystąpienia błędu podczas sprawdzania weryfikacji certyfikatu. |

**Tabela 2 — kody powrotne błędu NetX Secure X. 509**
