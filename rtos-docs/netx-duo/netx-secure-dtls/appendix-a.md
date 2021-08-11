---
title: Dodatek A — kody Azure RTOS i błędów bezpiecznego protokołu DTLS netx
description: Wyświetla listę możliwych kodów błędów, które mogą być zwracane przez Azure RTOS NetX Secure DTLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: reference
ms.service: rtos
ms.openlocfilehash: f4994a5014d3691b4a78f225fb68b475bf5a8cdab630162a94130f321be09da5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782442"
---
# <a name="appendix-a-azure-rtos-netx-secure-dtls-returnerror-codes"></a>Dodatek A: Azure RTOS kodów powrotnych/błędów bezpiecznego protokołu DTLS netx

## <a name="netx-secure-tlsdtls-return-codes"></a>Kody powrotne bezpiecznego TLS/DTLS netX

Tabela 1 poniżej zawiera listę możliwych kodów błędów, które mogą być zwracane przez Azure RTOS bezpiecznego dtls NetX. Należy pamiętać, że usługi mogą również zwracać kody błędów protokołu UDP lub IP — wartości protokołu TLS zaczynają się od 0x101, a wartości TCP/IP/UDP są 0x100. Wartości zwracane X.509 zaczynają się od 0x181. Zapoznaj się z dokumentacją NetX TCP/IP/UDP, aby uzyskać informacje na temat wartości zwracanych adresów IP i UDP, a poniżej przedstawiono wartości X.509.

| **Nazwa błędu**                                        | **Wartość** | **Opis**                                                                                                                                               |
| ----------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_TLS_SUCCESS                              | 0x00      | Funkcja została zwrócona pomyślnie. (Tak samo jak NX_SUCCESS).                                                                                                        |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101     | Pętla główna TLS wywoływana z niezainicjowanym gniazdem.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102     | Warstwa rekordów TLS odebrała nierozpoznany typ komunikatu.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103     | Błąd wewnętrzny — stan nie został rozpoznany.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104     | Błąd wewnętrzny — odebrany pakiet nie zawiera danych protokołu TLS.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105     | Wybrany szyfr nie jest obsługiwany — wewnętrzny błąd serwera, w przypadku klienta oznacza to, że host zdalny wysłał zły szyfr (błąd lub atak).            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106     | Podczas szyfrowania lub odszyfrowywania wybrany szyfr jest wyłączony lub niedostępny.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107     | Coś w przetwarzaniu komunikatów podczas procesu praktycznego nie powiodło się.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108     | Przychodzący rekord miał adres MAC, który nie pasuje do wygenerowanego przez nas.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109     | Wychodzące wysyłanie tcp rekordu nie powiodło się z jakiegoś powodu.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH           | 0x10A     | Komunikat przychodzący miał nieprawidłową długość (zazwyczaj inną niż jedna w nagłówku, jak w komunikatach certyfikatów)                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B     | Przychodzący komunikat ChangeCipherSpec był nieprawidłowy.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C     | Certyfikat serwera przychodzącego nie został poprawnie analizowane.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D     | Certyfikat dostarczony przez serwer określa operację klucza publicznego, która nie jest wspierana.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E     | Odebrano klientaHello bez obsługiwanych szyfrów.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F     | Rekord przychodzący miał wersję TLS, która nie jest rozpoznawana.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110     | Przychodzący rekord miał prawidłową wersję TLS, ale taki, który nie jest obsługiwany.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111     | Wewnętrzna alokacja pakietów dla komunikatu TLS nie powiodła się.                                                                                                       |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112     | Certyfikat X509 nie został poprawnie analizowane.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113     | Podczas zamykania sesji TLS program nie otrzymał powiadomienia CloseNotify z hosta zdalnego.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114     | Host zdalny wysłał alert wskazujący błąd i zamykający połączenie.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115     | Odebrany skrót komunikatu Finish (Zakończ) nie jest zgodne z lokalnym wygenerowanym skrótem — uszkodzeniem algorytmu handshake.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM        | 0x116     | Certyfikat podczas weryfikacji miał nieobsługiwany algorytm podpisu.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED      | 0x117     | Sprawdzenie podpisu certyfikatu nie powiodło się — dane certyfikatu nie są zgodne z podpisem.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD             | 0x118     | Odebrano komunikat Hello z nieobsługiwaną metodą kompresji.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND              | 0x119     | W operacji na liście certyfikatów nie znaleziono pasującego certyfikatu.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT          | 0x11A     | Host zdalny wysłał certyfikat z podpisem własnym i NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES nie jest zdefiniowany.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND      | 0x11B     | Odebrano certyfikat zdalny z wystawcą, który nie należy do lokalnego zaufanego magazynu.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE              | 0x11C     | Odebrano komunikat DTLS w niewłaściwej kolejności — prawdopodobnie jego winą jest porzucony datagram.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                | 0x11D     | Odebrano pakiet z hosta zdalnego, który nie jest rozpoznany.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                       | 0x11E     | Odebrano komunikat DTLS i dopasowano go do sesji DTLS, ale miał on nieprawidłową epokę i należy go zignorować.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED            | 0x11F     | Odebrano komunikat DTLS z numerem sekwencji, który już widzieliśmy. Zignoruj go.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                  | 0x120     | Sesja TLS została użyta w interfejsie API usługi DTLS, który nie został zainicjowany dla usługi DTLS.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                   | 0x121     | Sesja TLS została użyta w interfejsie API TLS, który został zainicjowany dla usługi DTLS, a nie TLS.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH              | 0x122     | Element wywołujący próbował wysłać dane za pośrednictwem sesji USŁUGI DTLS z adresem IP lub portem, które nie są zgodne z sesją.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS             | 0x123     | Nowe połączenie próbowało pobrać sesję DTLS z pamięci podręcznej, ale nie było żadnych bezpłatnych.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                 | 0x124     | Wywołujący wyszukał sesję usługi DTLS, ale dany adres IP i port nie są zgodne z żadnymi wpisami w pamięci podręcznej.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                 | 0x125     | Wywołujący próbował dodać psk do sesji TLS, ale w danej sesji nie było więcej miejsca.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                    | 0x126     | Host zdalny podał wskazówkę tożsamości psk, która nie pasuje do żadnego z naszych magazynów lokalnych.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED              | 0x127     | Sesja TLS odebrała alert CloseNotify z hosta zdalnego wskazujący, że sesja została ukończona.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS              | 0x128     | Sesje TLS w obiekcie TLS nie są dostępne do obsługi połączenia.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED           | 0x129     | Nie przydzielono miejsca na certyfikatach zdalnych przychodzących.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED               | 0x12A     | Dopełnienie szyfrowania w komunikacie przychodzącym nie było poprawne.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE        | 0x12B     | Podczas przetwarzania certyfikatuVerifyRequest serwer zdalny nie dostarczył obsługiwanego typu certyfikatu.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG         | 0x12C     | Podczas przetwarzania żądania CertificateVerifyRequest serwer zdalny nie dostarczył obsługiwanego algorytmu podpisu.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE            | 0x12D     | Za mało miejsca w buforze certyfikatu przydzielonego dla certyfikatu.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED           | 0x12E     | Wersja protokołu w przychodzącym rekordzie protokołu TLS nie jest dopasowana do wersji ustanowionej sesji.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR             | 0x12F     | Odebrano komunikat HelloRequest, ale nie będziemy negocjować ponownie.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                 | 0x130     | Funkcja, która została wyłączona, została napotkana podczas sesji lub uściślinia TLS.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE         | 0x131     | Komunikat CertificateVerify od klienta zdalnego nie może zweryfikować certyfikatu klienta.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED | 0x132     | Host zdalny wysłał pusty komunikat certyfikatu.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR      | 0x133     | Wystąpił błąd podczas przetwarzania lub wysyłania rozszerzenia oznaczania bezpiecznej renegocji.                                                                     |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE     | 0x134     | Podczas ponownego negocjowania sesji podjęto próbę z sesją TLS, która nie była aktywna.                                                                                |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL           | 0x135     | TLS odebrał rekord, który był zbyt duży dla bufora przypisanego pakietu. Nie można przetworzyć rekordu.                                                   |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                | 0x136     | Określone rozszerzenie nie zostało odebrane z hosta zdalnego podczas ugody TLS.                                                                         |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID              | 0x137     | TLS odebrał nieprawidłowe Oznaczanie nazwy serwera rozszerzenia.                                                                                                     |
| NX_SECURE_TLS_CERT_ID_INVALID                    | 0x138     | Aplikacja próbowała dodać certyfikat serwera z nieprawidłową wartością identyfikatora certyfikatu (prawdopodobnie 0).                                                                |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                  | 0x139     | Aplikacja próbowała dodać certyfikat serwera z identyfikatorem certyfikatu, który jest już obecny w magazynie lokalnym.                                                       |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE               | 0x13A     | Host zdalny nie podał rozszerzenia oznaczania bezpiecznego ponownego negocjowania ani pseudoszyfrowania SCSV, więc nie można przeprowadzić bezpiecznej ponownej negocjacji.     |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE             | 0x13B     | Podczas próby wykonania operacji kryptograficznych jeden z wpisów w tabeli ciphersuite (lub jeden ze wskaźników funkcji) został nieprawidłowo ustawiony na wartość NULL. |

**Tabela 1 — kody powrotne błędów bezpiecznego TLS netX**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X.509 Return Codes

Tabela 2 poniżej zawiera listę możliwych kodów błędów, które mogą być zwracane przez usługi NetX Secure X.509. Należy pamiętać, że usługi mogą również zwracać inne kody błędów. Wartości zwracane X.509 rozpoczynają się 0x181, wartości TLS zaczynają się od 0x101, a wartości TCP/IP są 0x100. Zapoznaj się z dokumentacją netx TCP/IP, aby uzyskać informacje na temat zwracanych wartości TCP/IP i powyższych dla wartości zwracanych protokołu TLS.

| **Nazwa błędu**                                   | **Wartość** | **Opis**                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | Stan powrotu po pomyślnym powrocie. (Tak samo jak NX_SUCCESS)                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | Napotkaliśmy wielo bajtowy tag ASN.1 — obecnie nie jest obsługiwany.                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | Napotkano wartość długości dłuższą, niż możemy obsłużyć.                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | Oczekiwano dopełnienia o wartości 0 — coś się różniło.                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X509 oczekiwał klucza publicznego, ale go nie znalazł.                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | Znaleziono klucz publiczny, ale jest on nieprawidłowy lub ma nieprawidłowy format.                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | Blok ASN.1 najwyższego poziomu nie jest sekwencją — nieprawidłowy certyfikat X509.                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | Oczekiwanie identyfikatora algorytmu podpisu nie znalazło go.                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | Dane tożsamości certyfikatu mają nieprawidłowy format.                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | Oczekiwaliśmy określonego tagu ASN.1 dla formatu X509, ale mamy coś innego.                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | Przekazano plik klucza prywatnego PKCS#1, ale formatowanie było nieprawidłowe.                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | Łańcuch certyfikatów X509 był zbyt krótki, aby pomieścić cały łańcuch podczas tworzenia łańcucha.                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | Nie można zweryfikować łańcucha certyfikatów X509 (błąd catch-all).                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | Analizowanie podpisu X.509 PKCS #7 nie powiodło się.                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | Podczas szukania certyfikatu nie znaleziono pasującego wpisu.                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | Certyfikat zawierał pole, które nie jest zgodne z podaną wersją.                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | Certyfikat zawierał tag ASN.1 z nieprawidłową wartością klasy tagu.                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | Certyfikat zawierał rozszerzenie TLV, ale nie zawierało sekwencji.                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | Certyfikat zawierał nieprawidłową sekwencję rozszerzeń X.509.                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | Certyfikat miał pole "nie po", które było mniejsze niż bieżąca godzina.                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | Certyfikat miał pole "nie wcześniej", które było większe niż bieżący czas.                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | Nazwa pospolita certyfikatu lub nazwa alt podmiotu nie są zgodne z danym TLD DNS.                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | Certyfikat zawierał pole daty, które nie jest w formacie recognixed.                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | Podane listy CRL i certyfikat nie zostały wystawione przez ten sam urząd certyfikacji.                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | Sprawdzanie podpisu listy CRL nie powiodło się względem wystawcy.                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | Certyfikat został znaleziony w prawidłowej listy CRL i w związku z tym został odwołany.                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | Podczas próby zweryfikowania podpisu metoda podpisu nie jest dopasowana do oczekiwanej metody.                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | Podczas szukania rozszerzenia nie znaleziono rozszerzenia o zgodnym identyfikatorze.                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | Nazwa została wyszukana w rozszerzeniu subjectAltName, ale nie została znaleziona.                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | Podany typ klucza prywatnego był nieznany lub nieprawidłowy.                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | Przekazano ciąg nazwy, który był zbyt długi dla buforu wewnętrznego (nazwa DNS itp.).                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | Podczas wyszukiwania rozszerzenia rozszerzonego użycia klucza nie znaleziono określonego OID użycia klucza.                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | Do zwrócenia przez wywołanie zwrotne aplikacji w przypadku błędu użycia klucza podczas sprawdzania weryfikacji certyfikatu. |

**Tabela 2 — kody powrotne błędów NetX Secure X.509**
