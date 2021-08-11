---
title: Rozdział 3 — Opis funkcjonalny bezpiecznego Azure RTOS DTLS netx
description: Ten rozdział zawiera opis funkcjonalny bezpiecznego Azure RTOS DTLS netx.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7db319e45c6d1f4a2030734fc01fefc4f3907aebeec1b3f47a5bde57dd5bfcc4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797095"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>Rozdział 3. Opis funkcjonalny bezpiecznego Azure RTOS DTLS netx

## <a name="execution-overview"></a>Omówienie wykonywania

Ten rozdział zawiera opis funkcjonalny bezpiecznego Azure RTOS DTLS netx. Istnieją dwa podstawowe typy wykonywania programu w aplikacji NetX Secure DTLS: inicjowanie i wywołania interfejsu aplikacji. 

NetX Secure zakłada istnienie ThreadX i NetX/NetXDuo. Z ThreadX wymaga wykonywania wątków, zawieszenia, okresowych czasomierzy i obiektów wzajemnego wykluczania. Z NetX/NetXDuo wymaga UDP i IP sieci obiektów i sterowników.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>Datagram Transport Layer Security (DTLS) i Transport Layer Security (TLS)

Protokół SECURE DTLS NetX implementuje protokół Datagram Transport Layer Security w wersji 1.2 zdefiniowany w dokumencie RFC 6347. Wersja 1.0 usługi DTLS została zdefiniowana w dokumencie RFC 4347 i odpowiada wersji 1.1. Ze względu na to, że dtls jest zasadniczo rozszerzeniem TLS, zdecydowano, że następna wersja będzie używać tego samego numeru wersji co odpowiednia wersja TLS. W związku z tym nie ma wersji 1.1 usługi DTLS, ponieważ wersja 1.2 usługi DTLS odpowiada wersji 1.2.

> [!NOTE]
> NetX Secure obsługuje dtls w wersji 1.2. DtLS 1.0 (RFC 4347) **nie jest obecnie** obsługiwany.

*Secure Sockets Layer* (SSL) była oryginalną nazwą protokołu TLS, zanim stała się standardem w dokumencie RFC 2246, a "SSL" jest często używana jako ogólna nazwa protokołów TLS. Ostatnia wersja protokołu SSL to 3.0, a protokół TLS 1.0 jest czasami nazywany protokołem SSL w wersji 3.1. Wszystkie wersje oficjalnego protokołu "SSL" są uznawane za przestarzałe i niezabezpieczone, a obecnie protokół NetX Secure nie zapewnia implementacji protokołu SSL.

Protokół TLS określa  protokół do generowania kluczy sesji, które są tworzone podczas uściślania protokołu *TLS* między klientem a serwerem TLS, a te klucze są używane do szyfrowania danych wysyłanych przez aplikację podczas sesji protokołu *TLS.*

Protokół DTLS jest ściśle powiązany z protokołem TLS, ponieważ podstawowe mechansimy zabezpieczeń są współdzielone przez protokoły. Jednak protokół TLS jest przeznaczony do pracy za pośrednictwem protokołu warstwy transportu, który zapewnia gwarancje dotyczące dostarczania i zamawiania pakietów (prawie zawsze w praktyce TCP) i nie będzie działać za pośrednictwem zawodnego protokołu, takiego jak UDP. Właśnie z powodu protokołu UDP wprowadzono protokół DTLS: protokół DTLS został zaprojektowany z myślą o obsłudze zawodnego charakteru protokołu UDP i podobnych protokołów. Robi to, uwzględniając logikę zamawiania i niezawodności (np. retransmisję porzucanych danych) podobną do niezawodnych protokołów, takich jak TCP.

Pełne omówienie procesu TLS znajduje się w rozdziale 3 podręcznika użytkownika bezpiecznego procesu TLS firmy NetX, dlatego ten dokument koncentruje się na różnicach między zabezpieczeniami TLS i DTLS.

### <a name="dtls-record-header"></a>Nagłówek rekordu DTLS

Każdy prawidłowy rekord DTLS musi mieć nagłówek DTLS, jak pokazano na rysunku 1. Nagłówek jest taki sam jak TLS z dodawaniem dwóch nowych pól: 16-bitowej  *epoki* i 48-bitowego numeru sekwencji opisanej poniżej.

![Diagram nagłówka rekordu DTLS.](media/image2.png)

**Rysunek 1. Nagłówek rekordu DTLS**

Pola nagłówka rekordu TLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie  |
| ---------------- | --------- |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu DTLS. Prawidłowe typy są następujące:<br />- ChangeCipherSpec: 0x14<br />— Alert: 0x15<br />— Uściślij: 0x16<br />— Dane aplikacji: 0x17<br /> |
| **Wersja protokołu 16-bitowego** | To pole zawiera wersję protokołu DTLS. Prawidłowe wartości są następujące:<br />— DTLS 1.1: 0xFEFD |
|  **Epoka 16-bitowa** |  To pole zawiera "epokę" dtls, czyli licznik, który jest zwiększany przy każdej zmianie stanu szyfrowania (np. podczas generowania nowych kluczy sesji).  |
|  **48-bitowy numer sekwencji** |  To pole zawiera numer sekwencji, który identyfikuje ten konkretny rekord. Jest on używany przez usługi DTLS do obsługi kolejności rekordów i sprawdzania potrzeby ponownego przetransmisji. |
|  **Długość 16-bitowa** |  To pole zawiera długość danych hermetyzowanych w rekordzie DTLS.  |

### <a name="dtls-handshake-record-header"></a>Nagłówek rekordu uściślniania usługi DTLS

Każdy prawidłowy rekord uściślinia usługi DTLS musi mieć nagłówek uściślniania usługi DTLS, jak pokazano na rysunku 2.

![Diagram nagłówka rekordu uściślniania usługi DTLS.](media/image3.png)

**Rysunek 2. Nagłówek rekordu uściślniania usługi DTLS**

Pola nagłówka rekordu handshake usługi DTLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie  |
| ---------------- | ------------------------------------------------ |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu DTLS. Prawidłowe typy są następujące:<br />- ChangeCipherSpec: 0x14<br />— Alert: 0x15<br />— Uściślij: 0x16<br />— Dane aplikacji: 0x17 |
|  **Epoka 16-bitowa** | To pole zawiera "epokę" dtls, czyli licznik, który jest zwiększany przy każdej zmianie stanu szyfrowania (np. podczas generowania nowych kluczy sesji). |
|  **48-bitowy numer sekwencji** | To pole zawiera numer sekwencji, który identyfikuje ten konkretny rekord. Jest on używany przez usługi DTLS do obsługi kolejności rekordów i sprawdzania potrzeby ponownego przetransmisji. |
|  **Wersja protokołu 16-bitowego** | To pole zawiera wersję protokołu DTLS. Prawidłowe wartości są następujące:<br />— DTLS 1.1: 0xFEFD |
| **Długość 16-bitowa** | To pole zawiera długość danych hermetyzowanych w rekordzie DTLS. |
| **8-bitowy typ ugody** | To pole zawiera typ komunikatu uściśli. Prawidłowe wartości są następujące:<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- Certyfikat: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />- ClientKeyExchange: 0x10<br />— Gotowe: 0x14 |
| **Długość 24-bitowa** | To pole zawiera długość danych komunikatu z ugodą. |
| **16-bitowy numer sekwencji** | To pole zawiera numer sekwencji. |

### <a name="the-dtls-handshake-and-dtls-session"></a>Sesja ugody i dtls usługi DTLS

Na rysunku 3 przedstawiono typowy uściślnienie usługi DTLS. Jest to niemal identyczne z typowymi uściślaniami TLS z istotną różnicą — przy pierwszym wysłaniu komunikatu ClientHello serwer odpowiada nowym komunikatem specyficznym dla usługi DTLS *HelloVerifyRequest,* który zawiera "plik cookie". Klient USŁUGI DTLS musi odpowiedzieć drugim komunikatem ClientHello zawierającym ten plik cookie, zanim będzie można kontynuować ugodę. Ten mechanizm został dodany do protokołu DTLS, aby zapobiec niektórym atakom typu "odmowa usługi" (DoS), ponieważ protokół UDP jest protokołem bezpołędnym (protokół TCP wymaga dedykowanego połączenia/portu, więc protokół TLS nie ma tego samego problemu).

A DTLS handshake begins when the Client sends a ClientHello message to a DTLS server, indicating its desire to start a DTLS session (Uściślij uściślanie DTLS rozpoczyna się, gdy klient wysyła komunikat *ClientHello* do serwera DTLS, wskazując chęć uruchomienia sesji USŁUGI DTLS). Komunikat zawiera informacje o szyfrowaniu, które ma być używane przez klienta dla sesji, wraz z informacjami używanymi do generowania kluczy sesji w dalszej części procesu praktycznego. Dopóki klucze sesji nie zostaną wygenerowane, wszystkie komunikaty w uściśle dtls nie są szyfrowane. Jak wspomniano powyżej, serwer DTLS może wysyłać żądania HelloVerifyRequest w odpowiedzi na żądania ClientHello, co wymuś na kliencie udzielenie odpowiedzi za pomocą drugiej zaktualizowanej aplikacji ClientHello.

Po odebraniu drugiego komunikatu ClientHello serwer DTLS zweryfikuje plik cookie i jeśli jest poprawny, odpowie komunikatem ServerHello wskazującym wybór opcji szyfrowania dostarczonych przez klienta. Po aplikacji ServerHello następuje komunikat Certyfikat, w którym serwer udostępnia certyfikat cyfrowy w celu uwierzytelnienia swojej tożsamości na kliencie (jeśli jest używana weryfikacja X.509). Na koniec serwer wysyła komunikat ServerHelloDone, aby wskazać, że nie ma więcej komunikatów do wysłania. Serwer może opcjonalnie wysyłać inne komunikaty po funkcji ServerHello, a w niektórych przypadkach może nie wysłać komunikatu certyfikatu (na przykład w przypadku użycia kluczy wstępnych), dlatego konieczne jest wysłanie komunikatu ServerHelloDone.

Gdy klient odebrał wszystkie komunikaty serwera, ma wystarczająco dużo informacji, aby wygenerować klucze sesji. W tym celu TLS/DTLS tworzy udostępniony bit danych losowych o nazwie *Pre-Master Secret*, który ma stały rozmiar i jest używany jako iniekt do generowania wszystkich kluczy potrzebnych po włączeniu szyfrowania. Klucz tajny wstępnego klucza tajnego jest szyfrowany przy użyciu algorytmu klucza publicznego (np. RSA) określonego w komunikatach Hello (zobacz poniżej, aby uzyskać informacje na temat algorytmów kluczy publicznych) i klucza publicznego dostarczonego przez serwer w certyfikacie. Opcjonalna funkcja TLS/DTLS o nazwie Klucze wstępne (PSK) umożliwia szyfrowanie, które nie używają certyfikatu, ale zamiast tego używają wartości klucza tajnego współużytkowania hostów (zazwyczaj za pośrednictwem transferu fizycznego lub innej zabezpieczonej metody). Po włączeniu klucza wstępnego klucz tajny jest używany do generowania wstępnego klucza tajnego. Zobacz sekcję na temat kluczy wstępnych w sekcji "Metody uwierzytelniania" poniżej.

W przypadku zwykłego ugody TLS/DTLS zaszyfrowany klucz tajny wstępnego klucza tajnego jest wysyłany do serwera w komunikacie ClientKeyExchange. Serwer po otrzymaniu komunikatu ClientKeyExchange odszyfrowuje klucz tajny przedwłaśnia przy użyciu klucza prywatnego i kontynuuje generowanie kluczy sesji równolegle z klientem protokołu TLS/DTLS.

Po wygenerowaniu kluczy sesji wszystkie dalsze komunikaty mogą być szyfrowane przy użyciu algorytmu klucza prywatnego (np. AES) wybranego w komunikatach Hello. Ostatni niezaszyfrowany komunikat o nazwie ChangeCipherSpec jest wysyłany zarówno przez klienta, jak i przez serwer, aby wskazać, że wszystkie dalsze komunikaty będą szyfrowane.

Pierwszy zaszyfrowany komunikat wysłany przez klienta i serwer jest również ostatnim komunikatem uściśniania TLS o nazwie Finished (Zakończono). Ten komunikat zawiera skrót wszystkich odebranych i wysłanych komunikatów w uściśli. Ten skrót służy do sprawdzania, czy żaden z komunikatów w uściśli nie został naruszony ani uszkodzony (co wskazuje na możliwe naruszenie zabezpieczeń).

Po odebraniu komunikatów Finished (Zakończone) i zweryfikowaniu skrótów uściślinia rozpoczyna się sesja TLS/DTLS, a aplikacja zaczyna wysyłać i odbierać dane. Wszystkie dane wysyłane bezpośrednio podczas sesji TLS/DTLS są najpierw szyfrowane przy użyciu algorytmu wyznaczania wartości skrótu wybranego w komunikatach Hello (w celu zapewnienia integralności komunikatów) i szyfrowanego przy użyciu wybranego algorytmu klucza prywatnego z wygenerowanym kluczem sesji.

Sesję TLS/DTLS można zakończyć pomyślnie tylko wtedy, gdy klient lub serwer wybierze tę opcję. Obcinana sesja jest uznawana za naruszenie zabezpieczeń (ponieważ osoba atakująca może próbować zapobiec odbierania wszystkich wysyłanych danych), więc gdy którakolwiek ze stron chce zakończyć sesję, wysyła specjalne powiadomienie o alercie CloseNotify. Zarówno klient, jak i serwer muszą wysłać i przetworzyć alert CloseNotify w przypadku pomyślnego zamknięcia sesji.

![Diagram typowej sesji ugody z zastosowaniem usługi DTLS.](media/image4.png)

**Rysunek 3. Typowe uściślicie w uściśliwce usługi DTLS**

### <a name="initialization"></a>Inicjalizacja

Stos NetX lub NetXDuo musi zostać zainicjowany przed użyciem bezpiecznego dtls NetX. Zapoznaj się z Podręcznikiem użytkownika netx lub NetXDuo, aby uzyskać informacje na temat prawidłowego inicjowania stosu TCP/IP dla operacji UDP.

Po zainicjowania protokołu UDP NetX można włączyć usługę DTLS. Wewnętrznie cały ruch sieciowy i przetwarzanie DTLS są obsługiwane przez stos NetX/NetXDuo bez konieczności interwencji użytkownika. Jednak w przypadku usługi DTLS istnieją pewne specyficzne wymagania, które muszą być obsługiwane niezależnie od podstawowego stosu sieciowego. Operacja klienta DTLS te parametry są przypisywane do bloku sterowania DTLS o nazwie ***NX_SECURE_DTLS_SESSION** _. W przypadku operacji serwera DTLS blok sterowania jest nazywany *__NX_SECURE_DTLS_SERVER_** i zawiera infrastrukturę potrzebną do obsługi wielu sesji protokołu DTLS na jednym porcie UDP — należy pamiętać, że różni się to od protokołu TLS, w którym każda sesja protokołu TLS jest powiązana z pojedynczym portem TCP.

Dwa tryby DTLS, Serwer i Klient, mogą być włączone w aplikacji (ale tylko jeden tryb dla każdego gniazda NetX), a każdy z nich ma własne specyficzne wymagania szczegółowo opisane poniżej.

### <a name="initialization--dtls-server"></a>Inicjowanie — serwer DTLS

Tryb serwera Secure DTLS NetX różni się od trybu serwera TLS ze względu na użycie protokołu UDP dla podstawowego protokołu transportu sieciowego. W przypadku protokołu TCP port jest powiązany z jednym hostem zdalnym na czas trwania sesji protokołu TLS. Protokołu UDP nie ma pojęcia stanu w odniesieniu do hosta zdalnego, więc żądania DTLS z różnych hostów będą odbierane w tym samym interfejsie UDP. W związku z tym protokół DTLS musi utrzymywać stan sesji, a nie polegać na gnieździe, tak jak w przypadku protokołów TLS i TCP. Z tego powodu blok sterowania serwera DTLS (NX_SECURE_DTLS_SERVER) zachowuje mapowanie informacji o zdalnym hoście (adres IP i port) na sesje usługi DTLS. Wszystkie dane przychodzące na gnieździe UDP przypisanym do serwera USŁUGI DTLS zostaną zamapowane na istniejącą lub nową sesję usługi DTLS na podstawie hosta zdalnego. Z tego powodu tworzenie serwera DTLS wymaga kilku dodatkowych parametrów wykraczających poza to, czego potrzebują klienci TLS i DTLS.

Oprócz bloku sterowania serwera DTLS, szyfrów TLS i buforu przestrzeni szyfrowania/metadanych serwery DTLS wymagają buforu do obsługi sesji DTLS oraz buforu ponownego zsełowania pakietów używanego do odszyfrowywania przychodzących rekordów DTLS.

Oprócz buforów sesji serwery DTLS wymagają certyfikatu cyfrowego *,* który jest dokumentem używanym do identyfikowania serwera TLS z łączącym się klientem TLS, oraz odpowiednich certyfikatów klucza prywatnego *,* zazwyczaj dla algorytmu szyfrowania RSA. Standard International Telecommunications Union X.509 określa format certyfikatu używany przez TLS/DTLS. Istnieje wiele narzędzi do tworzenia certyfikatów cyfrowych X.509.

W przypadku bezpiecznego systemu DTLS NetX certyfikat X.509 musi być zakodowany binarnie przy użyciu Distinguished Encoding Rules (DER) asn.1. DER to standardowy format binarny TLS over-the-wire dla certyfikatów.

Klucz prywatny skojarzony z dostarczonym certyfikatem musi być w formacie DER-Encoded PKCS#1. Klucz prywatny jest używany tylko na urządzeniu i nigdy nie będzie przesyłany za pośrednictwem sieci. Zachowaj bezpieczeństwo kluczy prywatnych, ponieważ zapewniają one bezpieczeństwo komunikacji TLS/DTLS.

Aby zainicjować certyfikat serwera DTLS, aplikacja musi dostarczyć wskaźnik do buforu zawierającego certyfikat X.509 zakodowany w formacie DER i opcjonalne dane klucza prywatnego PKCS#1 RSA zakodowane w formacie DER przy użyciu usługi ***nx_secure_x509_certificate_intialize,*** która wypełnia strukturę NX_SECURE_X509_CERT odpowiednimi danymi certyfikatu do użycia przez usługę TLS. 

Po zainicjowania certyfikatu serwera należy go dodać do bloku sterowania TLS przy użyciu ***nx_secure_dtls_server_local_certificate_add*** usługi.

Po dodaniu certyfikatu serwera do bloku sterowania serwera DTLS można go użyć do bezpiecznej komunikacji z usługą DTLS (zobacz przykład powyżej).

### <a name="initialization--dtls-client"></a>Inicjowanie — klient USŁUGI DTLS

Tryb klienta bezpiecznego protokołu DTLS NetX jest prosty w działaniu w porównaniu z serwerem USŁUGI DTLS, ponieważ istnieje tylko jedno połączenie wychodzące z hostem zdalnym za pośrednictwem gniazda UDP.

Aby skonfigurować klienta USŁUGI DTLS, wymagany jest zaufany magazyn certyfikatów *,* który jest kolekcją certyfikatów cyfrowych zakodowanych w formacie X.509 od zaufanych urzędów certyfikacji. Te certyfikaty są zakładane przez protokół DTLS jako "zaufane" i służą jako podstawa uwierzytelniania certyfikatów dostarczanych przez jednostki serwera DTLS do aplikacji klienckiej bezpiecznego protokołu DTLS NetX.

Certyfikat zaufanego urzędu  certyfikacji może być z podpisem własnym lub podpisany przez inny urząd certyfikacji. W takim przypadku ten certyfikat jest nazywany pośrednim urzędu *certyfikacji* (ICA). W typowej aplikacji protokołu TLS/DTLS serwer udostępnia certyfikaty ICA wraz z certyfikatem serwera, ale jedynym wymaganiem do pomyślnego uwierzytelnienia jest możliwość śledzenia łańcucha wystawców (certyfikatów używanych do podpisywania innych certyfikatów) z certyfikatu serwera z powrotem do certyfikatu zaufanego urzędu certyfikacji w magazynie zaufanych certyfikatów. Ten łańcuch jest nazywany *łańcuchem zaufania lub* *łańcuchem certyfikatów.*

Aby zainicjować zaufany urząd certyfikacji lub certyfikat ICA, aplikacja musi dostarczyć wskaźnik do buforu zawierającego certyfikat X.509 zakodowany w formacie DER przy użyciu usługi ***nx_secure_x509_certificate_intialize** _, która wypełnia strukturę _ *NX_SECURE_X509_CERT** odpowiednimi danymi certyfikatu do użycia przez usługę TLS.

Klient USŁUGI DTLS musi również mieć miejsce na przydzielenie przychodzącego certyfikatu serwera (przy założeniu, że nie jest używany tryb klucza wstępnego) oraz bufor do składania pakietów do rekordów DTLS do odszyfrowania. Te bufory są przekazywane jako parametry do ***usługi nx_secure_dtls_session_create*** (zobacz dokumentacja interfejsu API, aby uzyskać więcej informacji).

Zaufane certyfikaty, które zostały zainicjowane, są następnie dodawane do utworzonego bloku kontroli sesji usługi DTLS przy użyciu ***nx_secure_dtls_session_trusted_certificate_add*** usługi. Nie można dodać certyfikatu spowoduje, że sesja klienta usługi DTLS nie powiedzie się, ponieważ nie będzie możliwości uwierzytelniania hostów serwera zdalnego przez protokół DTLS.

Po utworzeniu zaufanego magazynu certyfikatów można użyć sesji do nawiązania bezpiecznego połączenia klienta TLS.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Aplikacje bezpiecznego dtls NetX zazwyczaj będą uruchamiać wywołania funkcji z poziomu wątków aplikacji uruchomionych w ramach threadX RTOS. Niektóre inicjowanie, szczególnie w przypadku podstawowych protokołów komunikacji sieciowej (np. UDP i IP), może być wywoływane z ***tx_application_define*.** Aby uzyskać więcej informacji na temat inicjowania komunikacji sieciowej, zobacz NetX/NetXDuo User Guide (Podręcznik użytkownika netX/NetXDuo).

DtLS intensywnie korzysta z procedur szyfrowania, które są operacjami intensywnie obciążający procesor. Ogólnie rzecz biorąc, te operacje będą wykonywane w kontekście wywoływania wątku.

### <a name="dtls-session-start"></a>Rozpoczęcie sesji DTLS

Aby móc działać, protokół DTLS wymaga podstawowego protokołu sieciowego warstwy transportu. Zazwyczaj używanym protokołem jest TCP. Aby ustanowić sesję bezpiecznego TLS netX, **należy NX_UDP_SOCKET** i przekazana do usługi **_nx_secure_dtls_client_session_start_** dla klientów DTLS.

Serwery DTLS działają inaczej. Gniazdo UDP używane dla przychodzących żądań klienta DTLS znajduje się w bloku sterowania usługi NX_SECURE_DTLS_SERVER i jest inicjowane w wywołaniu funkcji ***nx_secure_dtls_server_create** _, która przyjmuje lokalny port UDP jako parametr. Następnie usługa _*_nx_secure_dtls_server_start_*_ jest używana do uruchamiania serwera DTLS w celu obsługi żądań przychodzących. Wszystkie żądania przychodzące są obsługiwane w procedurach wywołania zwrotnego dostarczanych do usługi nx_secure_dtls_server_create*: jeden dla połączeń i jeden dla _odbierania powiadomień. Aplikacja musi obsługiwać uruchamianie_ sesji DTLS po otrzymaniu powiadomienia o połączeniu (wywołanie zwrotne powiadomienia połączenia jest wywoływane przez usługę DTLS) przez wywołanie * nx_secure_dtls_server_session_start . Aplikacja musi również obsługiwać dane przychodzące po wywołaniu wywołania zwrotnego powiadomienia o odbierania (co następuje po zakończeniu uściślinia dtls) przez wywołanie metody __*_ nx_secure_dtls_session_receive **. Szczegółowe informacje na ten temat znajdują się w powyższym przykładzie i w odwołaniach interfejsu API dla każdej z powyższych usług.

### <a name="dtls-packet-allocation"></a>Alokacja pakietów DTLS

Protokół SECURE DTLS netX używa tej samej struktury pakietów co protokół TCP NetX/NetXDuo (***NX_PACKET** _), z tą różnicą, że zamiast wywoływania usługi _*_nx_packet_allocate_*_ należy wywołać usługę *__nx_secure_dtls_packet_allocate_**, aby miejsce dla nagłówka DTLS było przydzielone prawidłowo.

### <a name="dtls-session-send"></a>Wysyłanie sesji DTLS

Po zakończeniu sesji TLS aplikacja może wysyłać dane przy użyciu ***nx_secure_dtls_session_send*** usługi. Usługa wysyłania jest identyczna w użyciu z usługą ***nx_udp_socket_send** _, biorąc strukturę danych *__NX_PACKET_** zawierającą wysyłane dane, docelowy adres IP i docelowy port UDP.

> [!IMPORTANT]
> Podczas wysyłania danych przy użyciu usługi nx_secure_dtls_session_send ważne jest, aby użyć tego samego adresu IP i portu, które zostały użyte do ustanowienia sesji dtls, chyba że istnieje mechanizm przenoszenia sesji na nowy adres i port UDP na bieżąco (nie jest to typowe).

Wszystkie dane wysyłane za pośrednictwem usługi DTLS zostaną zaszyfrowane przez stos SECURE DTLS nx i skonfigurowane procedury szyfrowania przed ich wysłaniem.

### <a name="dtls-session-receive"></a>Odbieranie sesji DTLS

Po rozpoczęciu sesji DTLS aplikacja może rozpocząć odbieranie danych przy użyciu usługi ***nx_secure_Dtls_session_receive** _. Podobnie jak w przypadku wysyłania sesji DTLS, ta usługa jest identyczna w użyciu z _*_nx_udp_socket_receive_**, z tą różnicą, że dane przychodzące są odszyfrowywane i weryfikowane przez stos DTLS przed zwróceniem w strukturze pakietów.

### <a name="tls-session-close"></a>Zamykanie sesji TLS

Po zakończeniu sesji USŁUGI DTLS zarówno klient usługi DTLS, jak i serwer muszą wysłać alert CloseNotify do drugiej strony, aby zamknąć sesję. Obie strony muszą odebrać i przetworzyć alert, aby zapewnić pomyślne zamknięcie sesji.

Jeśli host zdalny wyśle alert CloseNotify, wszystkie wywołania usługi ***nx_secure_dtls_session_receive** _ przetworzyć alert, wysłać odpowiedni alert z powrotem do hosta zdalnego i zwrócić wartość __*_ NX_SECURE_TLS_SESSION_CLOSED **. Po zamknięciu sesji wszystkie kolejne próby wysłania lub odbierania danych z tej sesji USŁUGI DTLS nie powiodą się.

Jeśli aplikacja chce zamknąć sesję TLS, należy nx_secure_dtls_session_end **_** service. Usługa wyśle alert CloseNotify i przetnie odpowiedź CloseNotify. Jeśli odpowiedź nie zostanie odebrana, zostanie zwrócona wartość błędu *__NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, wskazująca, że sesja usługi DTLS nie została w sposób czysty zamknięty, co oznacza możliwe naruszenie zabezpieczeń.

### <a name="tlsdtls-alerts"></a>Alerty TLS/DTLS

Protokół TLS/DTLS zaprojektowano w celu zapewnienia maksymalnego bezpieczeństwa, więc każde błędne zachowanie protokołu jest uznawane za potencjalne naruszenie zabezpieczeń. Z tego powodu wszelkie błędy przetwarzania komunikatów lub szyfrowania/odszyfrowywania są uznawane za błędy krytyczne, które natychmiast przerywają ugodę lub sesję.

Chociaż obsługa błędów w aplikacji lokalnej jest stosunkowo prosta, host zdalny musi wiedzieć, że wystąpił błąd, aby prawidłowo obsłużyć tę sytuację i zapobiec kolejnym możliwym naruszeniom zabezpieczeń. Z tego powodu usługa TLS/DTLS wyśle do hosta zdalnego *komunikat o alertach* po każdym błędzie.

Alerty są traktowane w taki sam sposób jak inne komunikaty TLS/DTLS i są szyfrowane podczas sesji, aby uniemożliwić osobie atakującej zbieranie informacji z typu podanego alertu. Podczas tego procesu wysyłane alerty mają ograniczony zakres, aby ograniczyć ilość informacji, które mogą zostać uzyskane przez potencjalnego atakującego.

Alert CloseNotify używany do zamknięcia sesji TLS/DTLS jest jedynym alertem nie krytycznym. Chociaż jest uznawany za alert i wysyłany jako komunikat alertu, element CloseNotify różni się od innych alertów tym, że nie wskazuje, że wystąpił błąd.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>Ponowne negocjowanie i wznawianie sesji TLS/DTLS

TLS obsługuje "renegocjacja", czyli po prostu ponowną negocjowanie parametrów sesji TLS w kontekście istniejącej sesji TLS.

Wznowienie *sesji TLS nie* powinno być mylone z *renegocją sesji,* pomimo pewnych podobieństw. Jeśli *ponowna* negocjacja sesji obejmuje rozpoczęcie nowego ugody  w ramach istniejącej sesji TLS, wznowienie sesji jest wyłącznie opcjonalną funkcją, która polega na ponownym uruchomieniu zamkniętej sesji TLS bez przeprowadzania pełnego ugody TLS.

Secure DTLS NX obsługuje przychodzące żądania ponownego negocjowania z hostów zdalnych. Nie **obsługuje** wznawiania sesji. Bardziej kompleksowe omówienie tych funkcji można znaleźć w rozdziale 3 podręcznika użytkownika bezpiecznego TLS firmy NetX.

### <a name="protocol-layering"></a>Warstwy protokołów

Protokół TLS (a zatem również DTLS) pasuje do stosu sieciowego między warstwą transportu (np. TCP lub UDP) a warstwą aplikacji. Protokół TLS jest czasami traktowany jako protokół warstwy transportowej (stąd *Transport Layer* Security), ale ponieważ działa jako aplikacja w odniesieniu do podstawowych protokołów sieciowych, jest czasami grupowany w warstwie aplikacji.

Protokół TLS wymaga protokołu warstwy transportu, który obsługuje dostarczanie w porządek i bezstratne, takie jak TCP. Ze względu na to wymaganie nie można uruchomić protokołu TLS na podstawie protokołu UDP, ponieważ protokołu UDP nie gwarantuje dostarczenia datagramów. *DTLS* to zmodyfikowana wersja protokołu TLS, używana w przypadku aplikacji, które wymagają zabezpieczeń protokołu TLS za pośrednictwem protokołu datagramu, takiego jak UDP.

![Diagram warstw protokołu TLS.](media/image6.png)

**Rysunek 4 . Warstwy protokołu TCP/IP, UDP i TLS/DTLS**

## <a name="network-communications-security-and-encryption"></a>Zabezpieczenia i szyfrowanie komunikacji sieciowej

Zabezpieczanie komunikacji za pośrednictwem sieci publicznych i Internetu jest niezwykle ważnym tematem i tematem ogromnej liczby książek, artykułów i rozwiązań. Temat jest bardzo złożony, ale można go ograniczyć do prostego pomysłu: wysyłania informacji za pośrednictwem sieci, aby tylko zamierzony element docelowy miał dostęp do tych informacji lub je zmieniał. Dzieli się to na trzy ważne pojęcia: uwierzytelnianie, uwierzytelnianie i uwierzytelnianie. Protokół TLS/DTLS zapewnia rozwiązania dla wszystkich trzech.

Szyfrowanie jest używane na różne sposoby w celu zapewnienia tajemnicy, integralności i uwierzytelniania w protokołach TLS i DTLS. Szyfrowanie musi zostać dostarczone do usługi TLS lub DTLS podczas tworzenia sesji lub wystąpienia serwera, ponieważ TLS zapewnia elastyczną platformę do używania szyfrowania, a nie samego szyfrowania. Bezpieczny kod DTLS NetX zapewnia niezbędne procedury szyfrowania dla większości aplikacji, dzięki czemu nie trzeba martwić się o znalezienie odpowiedniego szyfrowania.

Bardziej szczegółowy opis tych tematów można znaleźć w rozdziale 3 Podręcznika użytkownika bezpiecznego TLS netx.

## <a name="tls-and-dtls-extensions"></a>Rozszerzenia TLS i DTLS

TLS (a tym samym DTLS) zapewnia szereg rozszerzeń, które zapewniają dodatkowe funkcje dla niektórych aplikacji. Te rozszerzenia są zwykle wysyłane jako część komunikatów ClientHello lub ServerHello, co wskazuje hostowi zdalneowi chęć użycia rozszerzenia lub podanie dodatkowych szczegółów do użycia podczas ustanawiania bezpiecznej sesji TLS.

Bezpieczny kod DTLS NetX obsługuje wszystkie rozszerzenia w bezpiecznym bezpiecznego zabezpieczeniach TLS netX, a pełny opis tych rozszerzeń można znaleźć w przewodniku użytkownika bezpiecznego TLS netx, rozdział 3.

## <a name="authentication-methods"></a>Metody uwierzytelniania

TLS i DTLS zapewniają platformę do nawiązywania bezpiecznego połączenia między dwoma urządzeniami za pośrednictwem niezabezpieczonych sieci, ale częścią problemu jest znajomość tożsamości urządzenia po drugiej stronie tego połączenia. Bez mechanizmu uwierzytelniania tożsamości hostów zdalnych osoba atakująca staje się błahą operacją, która stanowi zaufane urządzenie.

Początkowo może się wydawać, że użycie adresów IP, sprzętowych adresów MAC lub systemu DNS zapewni stosunkowo wysoki poziom zaufania do identyfikowania hostów w sieci, ale ze względu na charakter technologii TCP/IP i łatwość fałszowania adresów i uszkodzenia wpisów DNS (np. za pomocą zatrucia pamięci podręcznej DNS) staje się jasne, że protokół TLS wymaga dodatkowej warstwy ochrony przed fałszywymi tożsamościami.

Istnieją różne mechanizmy, które mogą zapewnić tę dodatkową warstwę uwierzytelniania dla protokołu TLS, ale najczęściej jest to *certyfikat cyfrowy.* Inne mechanizmy obejmują klucze wstępne (PSK) i schematy haseł.

### <a name="digital-cerificates"></a>Cyfrowe ceryfikaty

Certyfikaty cyfrowe to najczęstsza metoda uwierzytelniania hosta zdalnego na platformie TLS. Zasadniczo certyfikat cyfrowy to dokument z określonym formatowaniem, który dostarcza informacje o tożsamości dla urządzenia w sieci komputerowej.

Standard TLS zwykle używa formatu O nazwie X.509, standardu opracowanego przez Międzynarodowy Związek Telekomunikacyjny, chociaż można użyć innych formatów certyfikatów, jeśli hosty TLS mogą wyrazić zgodę na używany format. X.509 definiuje określony format certyfikatów i różnych kodowań, których można użyć do tworzenia dokumentu cyfrowego. Większość certyfikatów X.509 używanych z TLS jest kodowana przy użyciu wariantu ASN.1, innego standardu telekomunikacyjnego. W ramach usługi ASN.1 istnieją różne kodowania cyfrowe, ale najbardziej powszechnym kodowaniem certyfikatów TLS jest standard Distinguished Encoding Rules (DER). DER to uproszczony podzbiór podstawowych reguł kodowania ASN.1 (Basic Encoding Rules, BER), który został zaprojektowany tak, aby był jednoznaczny, co ułatwia analizowanie. Za pośrednictwem połączenia certyfikaty TLS są zwykle kodowane w binarnym algorytmie DER i jest to format, który NetX Secure oczekuje w przypadku certyfikatów X.509.

Chociaż certyfikaty binarne w formacie DER są używane w rzeczywistym protokole TLS, mogą być generowane i przechowywane w wielu różnych kodowaniach z rozszerzeniami plików, takimi jak PEM, CRT i .p12. Różne warianty są używane przez różne aplikacje różnych producentów, ale ogólnie wszystkie można przekonwertować na der przy użyciu powszechnie dostępnych narzędzi.

Najczęstszym z alternatywnych kodowań certyfikatów jest PEM. Format PEM (od usługi Privacy-Enhanced Mail) to zakodowana w formacie Base-64 wersja kodowania DER, która jest często używana, ponieważ kodowanie powoduje drukowalny tekst, który można łatwo wysłać przy użyciu poczty e-mail lub protokołów internetowych.

Generowanie certyfikatu dla aplikacji NetX Secure zwykle znajduje się poza zakresem tego podręcznika, ale narzędzie wiersza polecenia OpenSSL ( www.openssl.org) jest powszechnie dostępne i można go konwertować między większość[formatów.](http://www.openssl.org)

W zależności od aplikacji można wygenerować własne certyfikaty, zostać dostarczone przez producenta lub organizację rządową albo zakupić certyfikaty od komercyjnego urzędu certyfikacji.

Aby użyć certyfikatu cyfrowego w aplikacji NetX Secure, należy najpierw przekonwertować certyfikat na binarny format DER i opcjonalnie przekonwertować skojarzony klucz prywatny (na przykład "wykładnik prywatny" dla RSA) na format binarny, zazwyczaj klucz RSA w formacie PKCS#1. Po zakończeniu konwersji do urządzenia należy załadowanie certyfikatu i klucza prywatnego. Możliwe opcje obejmują użycie systemu plików opartego na technologii flash lub wygenerowanie tablicy C na podstawie danych (przy użyciu narzędzia takiego jak "xxd" z systemu Linux) i skompilowanie certyfikatu i klucza w aplikacji jako danych stałych.

Po załadowaniu certyfikatu na urządzenie można użyć interfejsu API usługi DTLS do skojarzenia certyfikatu z sesją lub serwerem usługi DTLS.

Aby uzyskać szczegółowe informacje i przykłady dotyczące używania certyfikatów X.509 z bezpiecznymi zabezpieczeniami DTLS netx, zobacz sekcję "Importowanie certyfikatów X.509 do usługi NetX Secure" w Podręczniku użytkownika bezpiecznego TLS netX.

Aby uzyskać więcej informacji, zapoznaj się z następującymi usługami DTLS w interfejsie API:

- nx_secure_x509_certificate_initialize,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Specyfika certyfikatu klienta TLS

Implementacje klienta DTLS zwykle nie wymagają załadowania lokalnego certyfikatu na urządzenie. Certyfikat lokalny to certyfikat, który identyfikuje urządzenie lokalne. W szczególności certyfikat lokalny dostarcza informacje o tożsamości dla urządzenia, na którym jest ładowana aplikacja TLS/DTLS. Wyjątkiem jest to, gdy jest włączone uwierzytelnianie certyfikatu klienta, ale jest to rzadziej spotykane.

Klient USŁUGI DTLS wymaga załadowania co najmniej jednego zaufanego certyfikatu (w razie potrzeby może zostać załadowanych więcej certyfikatów) oraz miejsca na przydzielenie certyfikatu zdalnego. Zaufany certyfikat to certyfikat, który stanowi podstawę zaufania i uwierzytelniania urządzenia zdalnego, bezpośrednio lub za pośrednictwem infrastruktury kluczy publicznych (PKI). Katalog główny łańcucha zaufania jest zwykle nazywany urzędem certyfikacji lub certyfikatem urzędu certyfikacji. Certyfikat zdalny odwołuje się do certyfikatu wysyłanego przez hosta zdalnego podczas ugody TLS. Zapewnia tożsamość dla tego hosta zdalnego i jest uwierzytelniany przez porównanie jej z zaufanym certyfikatem na urządzeniu lokalnym.

Aby uzyskać więcej informacji na temat dodawania zaufanych certyfikatów i przydzielania miejsca dla certyfikatów zdalnych, zobacz dokumentacja interfejsu API TLS dla następujących usług: nx_secure_dtls_session_create, nx_secure_dtls_session_trusted_certificate_add.

### <a name="tlsdtls-server-certificate-specifics"></a>Specyfika certyfikatu serwera TLS/DTLS

Implementacje serwera DTLS zwykle nie wymagają załadowania "zaufanych" certyfikatów na urządzenie lub certyfikatów zdalnych do przydzielenia. Wyjątek stanowi sytuacja, w przypadku gdy jest włączone uwierzytelnianie certyfikatu klienta.

Serwer TLS wymaga załadowania certyfikatu "lokalnego" (lub "tożsamości"), aby serwer był w stanie udostępnić go klientowi zdalnej podczas uściśniania TLS w celu uwierzytelnienia serwera na kliencie.

Aby uzyskać więcej informacji na temat ładowania certyfikatów lokalnych do użycia z aplikacjami serwera NetX TLS, zobacz dokumentacja interfejsu API dla następujących usług: nx_secure_dtls_server_local_certificate_add, nx_secure_dtls_server_local_certificate_remove.


### <a name="pre-shared-keys-psk"></a>Klucze wstępne (PSK)

Alternatywnym mechanizmem zapewniania uwierzytelniania identyfikacji w protokołach TLS jest określenie kluczy wstępnych (PSK). Użycie szyfru PSK nie wymaga stosowania operacji szyfrowania klucza publicznego intensywnie korzystających z procesora, czyli boonu dla urządzeń osadzonych z ograniczeniami zasobów. Klucz wstępny zastępuje certyfikat w uściśle TLS/DTLS i jest używany w miejsce zaszyfrowanego klucza tajnego przedwłaściwego do generowania klucza sesji TLS/DTLS.

Szyfry PSK są ograniczone w tym sensie, że wspólny klucz tajny musi być obecny na obu urządzeniach, zanim będzie można ustalić sesję TLS/DTLS. Oznacza to, że urządzenia muszą zostać załadowane przy użyciu tego tajnego kluczu przy użyciu pewnych bezpiecznych środków innych niż połączenie TLS PSK — klucz psk może być aktualizowany za pośrednictwem połączenia TLS PSK, ale urządzenie musi rozpoczynać się od kluczu psk, który jest ładowany za pośrednictwem innego mechanizmu. Na przykład urządzenie czujnika i jego urządzenie bramy można załadować z zestawami PSK w fabryce przed wysyłką lub użyć standardowego połączenia TLS (z certyfikatem) do załadowania zestawu PSK.

Szyfry PSK mają kilka form opisanych w dokumencie RFC 4279. Pierwszy z nich używa RSA lub Diffie-Hellman kluczy, które są używane w taki sam sposób jak klucze publiczne przesyłane w certyfikacie w standardowych uściśniach TLS. Druga forma, która jest bardziej używana w środowisku z ograniczonymi zasobami, używa klucza psk, który jest używany do bezpośredniego generowania kluczy sesji (na przykład do użytku przez AES), unikając używania kosztownych operacji RSA lub Diffie-Hellman.

NetX Secure obsługuje drugą formę szyfrów PSK, umożliwiając aplikacjom usunięcie całego kodu kryptografii klucza publicznego i użycia pamięci. Klucz psk nie jest kluczem AES, ale można go traktować jako bardziej podobne do hasła, z którego są generowane rzeczywiste klucze. Istnieje kilka ograniczeń dotyczących wartości psk, chociaż dłuższe wartości zapewniają większe bezpieczeństwo (tak samo jak w przypadku haseł).

Aby używać funkcji PSK z aplikacją NetX Secure, należy najpierw zdefiniować globalne makro dla **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Zwykle odbywa się to za pośrednictwem ustawień kompilatora, ale definicję można również umieścić w nx_secure_tls.h. Po zdefiniowanym makrze obsługa szyfrowania PSK zostanie skompilowana w aplikacji NetX Secure DTLS.

Po włączeniu obsługi zestawu PSK można następnie skonfigurować zestawy PSK dla aplikacji przy użyciu interfejsu API usługi DTLS. Każdy klucz psk będzie wymagał wartości klucza psk (rzeczywistego klucza tajnego — ta wartość jest bezpieczna), wartości "tożsamości" używanej do identyfikowania określonego klucza psk oraz "wskazówki dotyczącej tożsamości", która jest używana przez serwer TLS do wybrania określonej wartości klucza psk.

Samo psk może być dowolną wartością binarną, ponieważ nigdy nie jest wysyłana za pośrednictwem połączenia sieciowego. Może to być dowolna wartość o długości do 64 bajtów.

Tożsamość i wskazówka muszą być drukowalnymi ciągami znaków sformatowanym przy użyciu formatu UTF-8. Wartości tożsamości i wskazówki mogą mieć dowolną długość do 128 bajtów.

Tożsamość i kluczy psk tworzą unikatową parę, która jest ładowana do każdego urządzenia w sieci, które musi komunikować się ze sobą.

"Wskazówka" jest używana głównie do definiowania profilów określonych aplikacji w celu grupowania psk według funkcji lub usługi. Te wartości muszą być uzgadniane z wyprzedzeniem i zależą od aplikacji. Na przykład aplikacja serwera wiersza polecenia OpenSSL (z włączoną linią psk) używa domyślnego ciągu "Client_identity", który musi zostać dostarczony przez klienta TLS, aby można było kontynuować uściślanie TLS.

Aby uzyskać więcej informacji na temat psk, zobacz NetX Secure API reference for the following services: nx_secure_dtls_psk_add, nx_secure_dtls_server_psk_add (Dokumentacja bezpiecznego interfejsu API netX dla następujących usług: nx_secure_dtls_psk_add, nx_secure_dtls_server_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importowanie certyfikatów X.509 do usługi NetX Secure

Certyfikaty cyfrowe są wymagane w przypadku większości połączeń TLS w Internecie. Certyfikaty zapewniają metodę uwierzytelniania wcześniej nieznanych hostów za pośrednictwem Internetu  za pomocą zaufanych pośredników, zwykle nazywanych urzędami certyfikacji lub urzędami certyfikacji. Aby połączyć urządzenie NetX Secure z komercyjną usługą w chmurze (taką jak Amazon Web Services), należy zaimportować certyfikaty do aplikacji przez załadowanie ich na urządzenie.

Oprócz certyfikatów czasami potrzebny jest również klucz *prywatny* skojarzony z certyfikatem. W niektórych aplikacjach (takich jak klient TLS, gdy nie jest używane uwierzytelnianie certyfikatu klienta) sam certyfikat będzie wystarczający, ale jeśli certyfikat jest używany do identyfikowania urządzenia, potrzebny będzie klucz prywatny. Klucze prywatne są zwykle generowane podczas tworzenia certyfikatu i są przechowywane w oddzielnym pliku, często zaszyfrowanym przy użyciu hasła.

Szczegółowy opis importowania certyfikatów do aplikacji NetX Secure można znaleźć w rozdziale 3 w Podręczniku użytkownika bezpiecznego TLS netx.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Uwierzytelnianie certyfikatu klienta w zabezpieczonych zabezpieczeniach TLS netx

W przypadku korzystania z uwierzytelniania certyfikatu X.509 protokół TLS/DTLS wymaga, aby wystąpienie serwera DTLS dostarczało certyfikat do identyfikacji, ale domyślnie wystąpienie klienta USŁUGI DTLS nie musi dostarczać certyfikatu na potrzeby uwierzytelniania przy użyciu innej formy uwierzytelniania (np. kombinacji nazwy użytkownika/hasła). Jest to najbardziej typowe użycie TLS w Internecie dla witryn sieci Web. Na przykład witryna sklepu detalicznego online musi udowodnić potencjalnego klienta korzystającego z przeglądarki internetowej, że serwer jest legalny, ale użytkownik użyje nazwy logowania/hasła, aby uzyskać dostęp do określonego konta.

Jednak przypadek domyślny nie zawsze jest pożądany, więc TLS/DTLS opcjonalnie umożliwia wystąpieniu serwera DTLS zażądanie certyfikatu od klienta zdalnego. Po włączeniu tej funkcji serwer DTLS wyśle komunikat CertificateRequest do klienta USŁUGI DTLS podczas procesu praktycznego. Klient musi odpowiedzieć własnym certyfikatem i komunikatem CertificateVerify zawierającym token kryptograficzny potwierdzający, że klient jest właścicielem pasującego klucza prywatnego skojarzonego z tym certyfikatem. Jeśli weryfikacja nie powiedzie się lub certyfikat nie jest połączony z zaufanym certyfikatem na serwerze, uściślinie TLS zakończy się niepowodzeniem.

Istnieją dwa oddzielne przypadki uwierzytelniania certyfikatu klienta w protokołach TLS — w poniższych sekcjach o przedstawiono oba przypadki.

### <a name="client-certificate-authentication-for-dtls-clients"></a>Uwierzytelnianie certyfikatu klienta dla klientów USŁUGI DTLS

Klient usługi DTLS może próbować nawiązaniu połączenia z serwerem, który żąda certyfikatu w celu uwierzytelnienia klienta. W takim przypadku klient musi udostępnić certyfikat serwerowi i sprawdzić, czy jest właścicielem zgodnego klucza prywatnego. W takim przypadku serwer zakończy uzgadnianie z usługą DTLS.

W usłudze NetX Secure DTLS nie ma specjalnej konfiguracji do obsługi tej funkcji, ale aplikacja będzie musi udostępnić lokalny certyfikat identyfikacji dla wystąpienia klienta TLS przy użyciu usługi *nx_secure_tls_session_local_certificate_add* service. Jeśli aplikacja nie dostarcza żadnego certyfikatu, ale serwer zdalny korzysta z uwierzytelniania certyfikatu klienta i żąda certyfikatu, uściślicie protokołu DTLS nie powiedzie się. Certyfikat dostarczony do sesji usługi DTLS z *nx_secure_dtls_session_local_certificate_add* musi zostać rozpoznany przez serwer zdalny, aby można było ukończyć ugodę usługi DTLS.

### <a name="client-certificate-authentication-for-tls-servers"></a>Uwierzytelnianie certyfikatu klienta dla serwerów TLS

Przypadek serwera DTLS dla uwierzytelniania certyfikatu klienta jest nieco bardziej złożony niż przypadek klienta USŁUGI DTLS, ponieważ funkcja jest opcjonalna. W takim przypadku serwer TLS musi zażądać certyfikatu od zdalnego klienta TLS, następnie przetworzyć komunikat CertificateVerify, aby sprawdzić, czy klient zdalny jest właścicielem pasującego klucza prywatnego, a następnie serwer musi sprawdzić, czy certyfikat dostarczony przez klienta może być śledzony do certyfikatu w lokalnym zaufanym magazynie certyfikatów.

W wystąpieniach serwera NetX Secure TLS uwierzytelnianie certyfikatu klienta jest kontrolowane przez nx_secure_dtls_server_x509_client_verify_configure *i* *nx_secure_dtls_server_x509_client_verify_disable* usług.

Aby włączyć uwierzytelnianie certyfikatu klienta, aplikacja musi wywołać metodę *nx_secure_dtls_server_x509_client_verify_configure* z wystąpieniem sesji serwera DTLS przed wywołaniem *nx_secure_dtls_server_start*. Weryfikacja wymaga przydzielenia miejsca dla przychodzących certyfikatów klienta, które są udostępniane jako parametr *nx_secure_dtls_server_x509_client_verify_configure.* Należy pamiętać, że bufor musi być wystarczająco duży, aby można było przechowywać łańcuch certyfikatów o maksymalnym rozmiarze dostarczonym przez klienta pomnów liczbę *sesji serwera USŁUGI DTLS.* Każda sesja serwera wymaga miejsca, które zostanie przydzielone z jednego dostarczonego buforu. Upewnij się, że bufor jest wystarczająco duży lub jeśli podany łańcuch certyfikatów klienta jest zbyt duży, wystąpi błąd.

Po włączeniu uwierzytelniania certyfikatu klienta serwer DTLS zażąda certyfikatu od zdalnego klienta USŁUGI DTLS podczas uściśniania protokołu DTLS. Na serwerze Secure DTLS NetX certyfikat klienta jest sprawdzany względem magazynu zaufanych certyfikatów utworzonych za pomocą *nx_secure_dtls_server_trusted_certificate_add,* korzystając z łańcucha wystawców X.509. Klient zdalny musi udostępnić łańcuch, który łączy swój certyfikat tożsamości z certyfikatem w zaufanym magazynie. W przypadku, gdy uściśnięcie usługi DTLS nie powiedzie się. Ponadto jeśli przetwarzanie komunikatów CertificateVerify zakończy się niepowodzeniem, uściślnienie usługi DTLS również zakończy się niepowodzeniem.

Metody podpisu używane dla metody CertificateVerify są stałe dla wersji 1.0 i 1.1. Są one określane przez serwer TLS w wersji 1.2, na której bazuje secure DTLS netX. W przypadku usługi DTLS 1.2 obsługiwane metody podpisu zazwyczaj są zgodne z odpowiednimi metodami dostarczonymi w tabeli metod kryptograficznych, ale zwykle algorytmem SHA-256 RSA (zobacz sekcję "Kryptografia w zabezpieczonych zabezpieczeniach TLS NetX", aby uzyskać więcej informacji na temat inicjowania szyfrowania TLS za pomocą metod kryptograficznych).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografia w zabezpieczonych zabezpieczeniach TLS netx

Protokół TLS definiuje protokół, w którym kryptografia może służyć do zabezpieczania komunikacji sieciowej. W związku z tym pozostawia rzeczywistą kryptografię do dość szerokiego wykorzystania dla użytkowników TLS. Specyfikacja wymaga tylko zaimplementowania jednego szyfru — w przypadku protokołu TLS 1.2 ten klucz szyfrowania jest TLS_RSA_WITH_AES_128_CBC_SHA, co wskazuje na użycie algorytmu RSA do operacji na kluczach publicznych, szyfrowanie AES w trybie CBC z 128-bitowym kluczem szyfrowania sesji i algorytm SHA-1 dla skrótów uwierzytelniania wiadomości.

Ponieważ zabezpieczenia NetX Secure są zgodne z TLS 1.2, domyślnie umożliwiają stosowanie obowiązkowego szyfrowania TLS_RSA_WITH_AES_128_CBC_SHA, ale biorąc pod uwagę liczbę możliwych implementacji dla każdej z metod kryptograficznych ze względu na możliwości sprzętowe i inne zagadnienia, usługa NetX Secure udostępnia ogólny interfejs API kryptograficzny, który umożliwia użytkownikowi określenie metod kryptograficznych do użycia z szyfrowaniem TLS.

> [!NOTE]
> Ogólny mechanizm kryptograficznych interfejsów API umożliwia również użytkownikom implementowanie własnych szyfrów, ale jest to zalecane dla zaawansowanych użytkowników, którzy znają szyfry i rozszerzenia TLS. Jeśli chcesz wspierać własne szyfry, skontaktuj się z przedstawicielem firmy Express Logic.

Aby uzyskać szczegółowe omówienie sposobu konfigurowania metod kryptograficznych dla usługi DTLS, zobacz NetX Secure TLS User Guide( Rozdział 3). Ten sam proces dotyczy zarówno TLS, jak i DTLS.
