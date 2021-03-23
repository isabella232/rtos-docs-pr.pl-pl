---
title: Rozdział 1 — wprowadzenie do protokołów HTTP i HTTPS
description: W tym rozdziale wprowadzono usługę Azure RTO NetX Duo HTTP/HTTPS dla modułu sieci Web.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c784843e4d3f11ee306e866223c0a19bfcba3b85
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822897"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>Rozdział 1 — wprowadzenie do protokołów HTTP i HTTPS

Protokół HTTP (Hypertext Transfer Protocol) to protokół przeznaczony do przesyłania zawartości w sieci Web. HTTP to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości. W związku z tym protokół HTTP jest wysoce niezawodnym protokołem transferu zawartości. Protokół HTTP jest jednym z najczęściej używanych protokołów aplikacji. Wszystkie operacje w sieci Web korzystają z protokołu HTTP.

HTTPS to bezpieczna wersja protokołu HTTP, która implementuje protokół HTTP przy użyciu Transport Layer Security (TLS) w celu zabezpieczenia bazowego połączenia TCP. Oprócz dodatkowej konfiguracji wymaganej do skonfigurowania protokołu TLS protokół HTTPS jest zasadniczo identyczny z protokołem HTTP w użyciu.

## <a name="general-http-requirements"></a>Ogólne wymagania dotyczące protokołu HTTP

Aby zapewnić prawidłowe działanie, pakiet HTTP sieci Web NetX wymaga zainstalowania programu NetX Duo (wersja 5,10 lub nowsza). Ponadto należy utworzyć wystąpienie adresu IP, a dla tego samego wystąpienia IP musi być włączone TCP. W przypadku obsługi protokołu HTTPS musi być również zainstalowana NetX Secure TLS (wersja 5,11 lub nowsza) (zobacz następną sekcję). W sekcji "mały przykładowy system" w **rozdziale 2** pokazano, jak to zrobić.

Część klienta HTTP pakietu HTTP NetX Web nie ma żadnych dalszych wymagań.

Część serwera HTTP NetX pakietu HTTP sieci Web ma kilka dodatkowych wymagań. Najpierw wymaga pełnego dostępu do *dobrze znanego portu tcp 80* do obsługi wszystkich żądań HTTP klienta (może to być zmienione przez aplikację na inny prawidłowy port TCP). Serwer HTTP jest również przeznaczony do użycia z osadzonym systemem plików FileX. Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku. Zostało to omówione w kolejnych sekcjach tego przewodnika.

## <a name="https-requirements"></a>Wymagania dotyczące protokołu HTTPS

Aby protokół HTTPS działał prawidłowo, pakiet HTTP sieci Web NetX wymaga programu NetX Duo (wersja 5,10 lub nowsza) i NetX Secure TLS (wersja 5,11 lub nowsza). Ponadto należy utworzyć wystąpienie protokołu IP, a protokół TCP musi być włączony dla tego samego wystąpienia IP, aby można było go używać z protokołem TLS. Sesja TLS musi zostać zainicjowana przy użyciu odpowiednich procedur kryptograficznych, certyfikatu zaufanego urzędu certyfikacji i miejsca do zaalokowania dla certyfikatów, które będą udostępniane przez hosty serwera zdalnego podczas uzgadniania TLS. Plik demonstracyjny w sekcji "mały przykładowy system HTTPS" w **rozdziale 2** pokazuje, jak to zrobić.

Część klienta HTTPS pakietu HTTP NetX Web nie ma żadnych dalszych wymagań.

Część serwera HTTPS w pakiecie HTTP NetX Web ma kilka dodatkowych wymagań. Najpierw wymaga pełnego dostępu do *dobrze znanego portu TCP 443* do obsługi wszystkich żądań HTTPS klienta (podobnie jak w przypadku zwykłego tekstu http, ten port może zostać zmieniony przez aplikację). Po drugie, sesja TLS musi zostać zainicjowana przy użyciu odpowiednich procedur kryptograficznych i certyfikatu tożsamości serwera (lub klucza wstępnego). Serwer HTTPS jest również przeznaczony do użycia z osadzonym systemem plików FileX. Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku. Użycie FileX jest omówione w kolejnych sekcjach tego przewodnika.

Więcej informacji o opcjach konfiguracji protokołu TLS znajduje się w dokumentacji NetX Secure.

O ile nie zaznaczono inaczej, wszystkie funkcje HTTP opisane w tym dokumencie dotyczą również protokołu HTTPS.

## <a name="http-and-https-constraints"></a>Ograniczenia HTTP i HTTPS

NetX internetowy HTTP implementuje Standard HTTP 1,1. Poniżej znajdują się następujące ograniczenia:

1. Przetwarzanie potokowe żądań nie jest obsługiwane
1. Serwer HTTP obsługuje zarówno uwierzytelnianie podstawowe, jak i MD5 szyfrowanego, ale nie MD5-sess. W tej chwili klient HTTP obsługuje tylko uwierzytelnianie podstawowe. W przypadku korzystania z protokołu TLS dla protokołu HTTPS nadal może być używane uwierzytelnianie HTTP.
1. Kompresja zawartości nie jest obsługiwana.
1. ŚLEDZENIE, opcje i żądania połączenia nie są obsługiwane.
1. Pula pakietów skojarzona z serwerem HTTP lub klientem musi być wystarczająco duża, aby można było przechowywać kompletny nagłówek HTTP.
1. Usługi klienta HTTP są przeznaczone tylko do transferu zawartości — w tym pakiecie nie ma dostępnych narzędzi do wyświetlania.

## <a name="http-url-resource-names"></a>Adres URL HTTP (nazwy zasobów)

Protokół HTTP jest przeznaczony do przesyłania zawartości w sieci Web. Żądana zawartość jest określana przez adres URL (Universal Resource Locator). Jest to podstawowy składnik każdego żądania HTTP. Adresy URL zawsze zaczynają się od znaku "/" i zwykle odpowiadają plikom na serwerze HTTP. Poniżej przedstawiono typowe rozszerzenia plików HTTP:

- **. htm** (lub **. html**) HTML (html)
- **. txt** Zwykły tekst ASCII
- **. gif** Binarny obraz GIF
- **. XBM** Binarny obraz Xbitmap

## <a name="http-client-requests"></a>Żądania klientów HTTP

Protokół HTTP ma prosty mechanizm do żądania zawartości sieci Web. Istnieje zestaw standardowych poleceń HTTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia z *dobrze znanym portem TCP 80 (port 443 dla protokołu HTTPS)*. Poniżej przedstawiono niektóre z podstawowych poleceń HTTP:

- **Pobierz *zasób* http/1.1** Pobierz określony zasób
- **Wyślij *zasób* http/1.1** Pobierz określony zasób i przekaż dołączone dane wejściowe do serwera HTTP
- ***Zasób* główny http/1.1** Traktowane jak pobieranie, ale nie zawartość jest zwracane przez serwer HTTP
- **Umieść *zasób* http/1.1** Umieść zasób na serwerze HTTP
- **Usuń *zasób* http/1.1** Usuń zasób na serwerze

Te polecenia ASCII są generowane wewnętrznie przez przeglądarki sieci Web i usługi klienta HTTP sieci Web NetX do wykonywania operacji HTTP przy użyciu serwera HTTP.

Należy pamiętać, że aplikacja kliencka HTTP powinna używać portu 80 lub portu 443, jeśli jest używany protokół HTTPS. Interfejs API protokołu HTTP klienta i serwera przyjmuje port jako parametr — makra NX_WEB_HTTP_SERVER_PORT (port 80) i NX_WEB_HTTPS_SERVER_PORT (port 443) są zdefiniowane dla wygody. Port serwera HTTP można także zmienić w czasie wykonywania za pomocą usługi *nx_web_http_client_set_connect_port ()* . Zobacz rozdział 4, aby uzyskać szczegółowe informacje dotyczące tej usługi.

## <a name="http-server-responses"></a>Odpowiedzi serwera HTTP

Serwer HTTP korzysta z tego samego *dobrze znanego portu TCP 80 (443 dla protokołu HTTPS)* do wysyłania odpowiedzi na polecenie klienta. Gdy serwer HTTP przetwarza polecenie klienta, zwraca ciąg odpowiedzi ASCII, który zawiera 3-cyfrowy kod stanu numerycznego. Odpowiedź numeryczna jest używana przez oprogramowanie klienckie HTTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej znajduje się lista różnych odpowiedzi serwera HTTP do poleceń klienta:

- **200** żądanie powiodło się
- **400** żądanie nie zostało poprawnie sformułowane
- **401** żądanie nieautoryzowane, klient musi wysłać uwierzytelnianie
- **404** nie znaleziono określonego zasobu w żądaniu
- **500** wewnętrzny błąd serwera http
- **501** żądanie niezaimplementowane przez serwer http
- Usługa **502** jest niedostępna

Na przykład pomyślne żądanie klienta dotyczące umieszczenia pliku "test.htm" jest odpowiedzią na komunikat "HTTP/1.1 200 OK".

## <a name="http-communication"></a>Komunikacja HTTP

Jak wspomniano wcześniej, serwer HTTP używa *dobrze znanego portu TCP 80 (443 dla protokołu HTTPS)* do pola żądania klientów. Klienci HTTP mogą używać dowolnego dostępnego portu TCP dla połączeń wychodzących. Ogólna sekwencja zdarzeń HTTP jest następująca:

**Żądanie HTTP GET**:

1. Problemy z klientem TCP nawiązywania połączenia z portem serwera 80 (lub 443 dla protokołu HTTPS).
1. Jeśli jest używany protokół HTTPS, połączenie TCP następuje uzgadnianie protokołu TLS w celu uwierzytelnienia serwera i ustanowienia bezpiecznego kanału.
1. Klient wysyła żądanie "**Pobierz *zasób* http/1.1**" (wraz z innymi informacjami nagłówka).
1. Serwer kompiluje komunikat "**http/1.1 200 OK**" z dodatkowymi informacjami, a następnie bezpośrednio przez zawartość zasobu (jeśli istnieje).
1. Serwer rozłącza się z klientem (protokół TLS jest wyłączony, jeśli jest używany protokół HTTPS).
1. Klient rozłącza połączenie z gniazdem (protokół TLS zostaje zamknięty po alercie rozłączenia z serwera).

**Żądanie HTTP Put**:

1. Problemy z klientem połączenia TCP z portem serwera 80 (lub 443).
1. Jeśli jest używany protokół HTTPS, połączenie TCP następuje uzgadnianie protokołu TLS w celu uwierzytelnienia serwera i ustanowienia bezpiecznego kanału.
1. Klient wysyła żądanie "Umieść zasób HTTP/1.1" wraz z innymi informacjami nagłówka, a następnie zawartość zasobu.
1. Serwer kompiluje komunikat "HTTP/1.1 200 OK" z dodatkowymi informacjami, a następnie bezpośrednio przez zawartość zasobów.
1. Serwer wykonuje odłączenie.
1. Klient wykonuje odłączenie.

> [!NOTE]
> Jak wspomniano wcześniej, serwer HTTP może zmienić domyślny port Connect (80 lub 443) w czasie wykonywania innego portu przy użyciu *nx_web_http_client_set_connect_port ()* dla serwerów sieci Web, które używają alternatywnych portów do łączenia się z klientami.

## <a name="http-authentication"></a>Uwierzytelnianie HTTP

Uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich żądań sieci Web. Istnieją dwa typy uwierzytelniania, czyli *podstawowe* i *szyfrowane*. Uwierzytelnianie podstawowe jest równoważne z *nazwą* i *hasłem* uwierzytelnianiem w wielu protokołach. W podstawowym uwierzytelnianiu HTTP Nazwa i hasła są łączone i kodowane w formacie base64. Główną wadą uwierzytelniania podstawowego jest nazwa i hasło, które są przesyłane w ramach żądania w sposób otwarty. Sprawia to, że jest nieco łatwe do kradzieży nazwy i hasła. Uwierzytelnianie szyfrowane rozwiązuje ten problem, przez co nigdy nie przesyłamy nazwy i hasła w żądaniu. Zamiast tego algorytm służy do tworzenia skrótu 128-bitowego z nazwy, hasła i innych informacji. Serwer HTTP sieci Web NetX obsługuje standardowy algorytm Digest MD5.

Kiedy jest wymagane uwierzytelnianie? Serwer HTTP decyduje, czy żądany zasób wymaga uwierzytelnienia. Jeśli uwierzytelnianie jest wymagane, a żądanie klienta nie zawierało odpowiedniego uwierzytelniania, odpowiedź "HTTP/1.1 401 bez autoryzacji" z typem wymaganego uwierzytelniania jest wysyłana do klienta. Klient powinien następnie utworzyć nowe żądanie z właściwym uwierzytelnianiem.

W przypadku użycia protokołu HTTPS serwer HTTPS nadal może korzystać z uwierzytelniania HTTP. W takim przypadku protokół TLS jest używany do szyfrowania całego ruchu HTTP, dlatego użycie *podstawowego* uwierzytelniania HTTP nie stanowi zagrożenia bezpieczeństwa. Uwierzytelnianie *szyfrowane* jest również dozwolone, ale nie zapewnia znaczących ulepszeń zabezpieczeń w porównaniu z uwierzytelnianiem podstawowym za pośrednictwem protokołu TLS.

## <a name="http-authentication-callback"></a>Wywołanie zwrotne uwierzytelniania HTTP

Jak wspomniano wcześniej, uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich transferów w sieci Web. Ponadto uwierzytelnianie jest zwykle zależne od zasobów. Dostęp do niektórych zasobów na serwerze wymaga uwierzytelnienia, a inne nie. Pakiet serwera HTTP sieci Web NetX umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_web_http_server_create*** ) procedury wywołania zwrotnego uwierzytelniania, która jest wywoływana na początku obsługi każdego żądania klienta http.

Procedura wywołania zwrotnego udostępnia serwer HTTP sieci Web NetX z nazwami użytkowników, hasła i obszarów skojarzonych z zasobem i zwracają wymagany typ uwierzytelniania. Jeśli dla zasobu nie jest wymagane żadne uwierzytelnianie, wywołanie zwrotne uwierzytelniania powinno zwrócić wartość **NX_WEB_HTTP_DONT_AUTHENTICATE**. W przeciwnym razie, jeśli dla określonego zasobu jest wymagane uwierzytelnianie podstawowe, procedura powinna zwrócić **NX_WEB_HTTP_BASIC_AUTHENTICATE**. A wreszcie, jeśli wymagane jest uwierzytelnianie MD5 Digest, procedura wywołania zwrotnego powinna zwracać **NX_WEB_HTTP_DIGEST_AUTHENTICATE**. Jeśli nie jest wymagane żadne uwierzytelnianie dla żadnego zasobu dostarczonego przez serwer HTTP, wywołanie zwrotne nie jest wymagane, a do utworzenia wywołania serwera HTTP można dostarczyć wskaźnik o wartości NULL.

Format procedury wywołania zwrotnego uwierzytelniania aplikacji jest bardzo prosty i został zdefiniowany poniżej:

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **request_type** Określa żądanie klienta HTTP, prawidłowe żądania są zdefiniowane jako:
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **zasób** Zażądano określonego zasobu.
- **Nazwa** Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika.
- **hasło** Miejsce docelowe wskaźnika do wymaganego hasła.
- **obszar** Miejsce docelowe wskaźnika w obszarze dla tego uwierzytelniania.

Wartość zwracana przez procedurę uwierzytelniania określa, czy jest wymagane uwierzytelnianie. nazwy, hasła i wskaźniki obszaru nie są używane, jeśli **NX_WEB_HTTP_DONT_AUTHENTICATE** jest zwracany przez procedurę wywołania zwrotnego uwierzytelniania. W przeciwnym razie deweloper serwera HTTP musi upewnić się, że **NX_WEB_HTTP_MAX_USERNAME** i **NX_WEB_HTTP_MAX_PASSWORD** zdefiniowane w *nx_web_http_server. h* są wystarczająco duże dla nazwy użytkownika i hasła określonych w wywołaniu wywołania zwrotnego uwierzytelniania. Oba mają rozmiar domyślny 20 znaków.

## <a name="http-invalid-usernamepassword-callback"></a>Nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła HTTP

Opcjonalne nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła na serwerze HTTP sieci Web NetX jest wywoływane, jeśli serwer HTTP odbiera nieprawidłową kombinację nazwy użytkownika i hasła w żądaniu klienta. Jeśli aplikacja serwera HTTP rejestruje wywołanie zwrotne z serwerem HTTP, zostanie wywołane w przypadku niepowodzenia uwierzytelniania podstawowego lub szyfrowanego *w nx_web_http_server_get_process ()*, w *nx_web_http_server_put_process ()* lub *w nx_web_http_server_delete_process ().*

W celu zarejestrowania wywołania zwrotnego z serwerem HTTP następująca usługa jest definiowana dla serwera HTTP sieci Web NetX.

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

Typy żądań są zdefiniowane w następujący sposób:

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>Wywołanie zwrotne nagłówka daty GMT w protokole HTTP

Istnieje opcjonalne wywołanie zwrotne na serwerze HTTP NetX sieci Web, aby wstawić nagłówek daty w komunikatach odpowiedzi. To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie Put lub Get

Aby zarejestrować wywołanie zwrotne daty GMT z serwerem HTTP, zdefiniowana jest następująca usługa.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

Typ danych NX_WEB_HTTP_SERVER_DATE jest zdefiniowany w następujący sposób:

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>Wywołanie zwrotne informacji o pamięci podręcznej HTTP

Serwer HTTP ma wywołanie zwrotne, aby zażądać maksymalnego wieku i daty z aplikacji HTTP dla określonego zasobu. Te informacje służą do określenia, czy serwer HTTP wysyła całą stronę w odpowiedzi na żądanie klienta get. Jeśli wartość "If Modified" w żądaniu klienta nie zostanie znaleziona lub nie jest zgodna z datą "Ostatnia modyfikacja" zwracaną przez wywołanie zwrotne pobierania pamięci podręcznej, zostanie wysłana cała strona.

W celu zarejestrowania wywołania zwrotnego z serwerem HTTP jest definiowana następująca usługa:

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>Obsługa kodowania fragmentarycznego transferu HTTP

Gdy nie można ustalić łącznej długości komunikatu HTTP przed wysłaniem go, funkcja kodowania transferu fragmentarycznego może służyć do wysyłania komunikatów jako serii fragmentów bez pola nagłówka "Content-Length". Ta funkcja jest obsługiwana we wszystkich komunikatach żądania HTTP i odpowiedzi. Jako odbiornik, ta funkcja jest obsługiwana, a nagłówek fragmentu jest przetwarzany w sposób przezroczysty przez wewnętrzną logikę. Jako nadawca interfejs API *nx_web_http_client_request_chunked_set* i *nx_web_http_server_response_chunked_set* musi być wywoływany odpowiednio przez klienta i serwer.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

Aby uzyskać więcej informacji na temat tych usług, zobacz opis w rozdziale 3 "Opis usług HTTP".

## <a name="http-multipart-support"></a>Obsługa wieloczęściowego protokołu HTTP

Rozszerzenia Multipurpose Internet Mail Extensions (MIME) zostały pierwotnie zamierzone dla protokołu SMTP, ale jego użycie ma rozproszenie do protokołu HTTP. Kodowanie MIME umożliwia komunikatów zawierających mieszane typy wiadomości (np. Image/jpg i Text/zwykły) w obrębie tego samego komunikatu. Serwer HTTP sieci Web NetX ma usługi do określenia typu zawartości w komunikatach HTTP zawierających MIME z klienta. Aby włączyć obsługę wieloczęściowego protokołu HTTP i korzystać z tych usług, należy zdefiniować **NX_WEB_HTTP_MULTIPART_ENABLE** opcji konfiguracji.

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

Aby uzyskać więcej informacji na temat korzystania z tych usług, zobacz opis w rozdziale 3 "Opis usług HTTP".

## <a name="http-multi-thread-support"></a>Obsługa wielowątkowości HTTP

Usługi klienta HTTP sieci Web NetX można wywoływać z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta HTTP powinny być wykonywane w kolejności z tego samego wątku.

W przypadku korzystania z protokołu HTTPS usługi klienta HTTP w sieci Web NetX mogą być wywoływane z wielu wątków, ale z powodu dodanej złożoności podstawowej funkcjonalności protokołu TLS każdy wątek powinien mieć pojedyncze, niezależne wystąpienie klienta HTTP (NX_WEB_HTTP_CLIENT strukturę formantu).

## <a name="http-rfcs"></a>Specyfikacje RFC protokołu HTTP

NetX internetowy HTTP jest zgodny z RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2616 "Hypertext Transfer Protocol-HTTP/1.1", RFC 2581 "kontrola przeciążenia TCP", RFC 1122 "wymagania dla hostów internetowych" i powiązane dokumenty RFC.

W przypadku protokołu HTTPS NetX internetowy protokół HTTP jest zgodny ze standardem RFC 2818 "HTTP over TLS".
