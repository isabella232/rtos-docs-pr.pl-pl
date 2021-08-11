---
title: Rozdział 1 — Wprowadzenie do protokołów HTTP i HTTPS
description: Ten rozdział zawiera wprowadzenie do modułu Azure RTOS NetX Duo HTTP/HTTPS for Web.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5f50419be3171d3df8544d1b34d603822f339785923f8a8199dc5b5ddcac281
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801758"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>Rozdział 1 — Wprowadzenie do protokołów HTTP i HTTPS

Protokół HTTP (Hypertext Transfer Protocol) to protokół przeznaczony do przesyłania zawartości w Sieci Web. HTTP to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości. W związku z tym protokół HTTP jest wysoce niezawodnym protokołem transferu zawartości. Protokół HTTP jest jednym z najczęściej używanych protokołów aplikacji. Wszystkie operacje w Internecie korzystają z protokołu HTTP.

HTTPS to bezpieczna wersja protokołu HTTP, która implementuje protokół HTTP przy użyciu protokołu Transport Layer Security (TLS) w celu zabezpieczenia bazowego połączenia TCP. Poza dodatkową konfiguracją wymaganą do skonfigurowania protokołu TLS protokół HTTPS jest zasadniczo taki sam jak protokół HTTP w użyciu.

## <a name="general-http-requirements"></a>Ogólne wymagania dotyczące protokołu HTTP

Aby pakiet HTTP sieci Web NetX działał prawidłowo, musi być zainstalowany program NetX Duo (w wersji 5.10 lub nowszej). Ponadto należy utworzyć wystąpienie adresu IP i włączyć protokół TCP w tym samym wystąpieniu adresu IP. Aby zapewnić obsługę protokołu HTTPS, należy również zainstalować protokół NetX Secure TLS (wersja 5.11 lub nowsza) (zobacz następną sekcję). W pliku pokazowym w sekcji "Small Example System" (Mały przykładowy system) w **rozdziale 2** pokazano, jak to zrobić.

Część klienta HTTP pakietu HTTP sieci Web NetX nie ma żadnych dodatkowych wymagań.

Część http server pakietu HTTP sieci Web NetX ma kilka dodatkowych wymagań. Po pierwsze wymaga pełnego dostępu do dobrze znanego portu *80* protokołu TCP do obsługi wszystkich żądań HTTP klienta (może to zostać zmienione przez aplikację na dowolny inny prawidłowy port TCP). Serwer HTTP jest również przeznaczony do użytku z osadzonym systemem plików FileX. Jeśli plik FileX nie jest dostępny, użytkownik może portować części pliku FileX używane do własnego środowiska. Omówiono to w kolejnych sekcjach tego przewodnika.

## <a name="https-requirements"></a>Wymagania dotyczące protokołu HTTPS

Aby protokół HTTPS działał prawidłowo, internetowy pakiet HTTP NetX wymaga zainstalowania obu platform NetX Duo (w wersji 5.10 lub nowszej) i NetX Secure TLS (wersja 5.11 lub nowsza). Ponadto należy utworzyć wystąpienie adresu IP i włączyć protokół TCP w tym samym wystąpieniu adresu IP do użycia z protokołem TLS. Sesja TLS musi zostać zainicjowana przy użyciu odpowiednich procedur kryptograficznych, certyfikatu zaufanego urzędu certyfikacji i przydzielenia miejsca dla certyfikatów, które zostaną dostarczone przez hosty serwerów zdalnych podczas uściślinia TLS. Plik demonstracyjny w sekcji "Mały przykładowy system HTTPS" w **rozdziale 2** pokazuje, jak to zrobić.

Część klienta HTTPS internetowego pakietu HTTP NetX nie ma żadnych dodatkowych wymagań.

Część serwera HTTPS pakietu HTTP sieci Web NetX ma kilka dodatkowych wymagań. Po pierwsze wymaga pełnego dostępu do dobrze znanego portu *443* protokołu TCP do obsługi wszystkich żądań PROTOKOŁU HTTPS klienta (tak jak w przypadku zwykłego tekstu HTTP, ten port może zostać zmieniony przez aplikację). Po drugie sesja TLS musi zostać zainicjowana przy użyciu odpowiednich procedur kryptograficznych i certyfikatu tożsamości serwera (lub klucza wstępnego). Serwer HTTPS jest również przeznaczony do użytku z osadzonym systemem plików FileX. Jeśli plik FileX nie jest dostępny, użytkownik może portować części pliku FileX używane do własnego środowiska. Korzystanie z pliku FileX omówiono w kolejnych sekcjach tego przewodnika.

Zapoznaj się z dokumentacją rozwiązania NetX Secure, aby uzyskać więcej informacji na temat opcji konfiguracji dla zabezpieczeń TLS.

O ile nie zaznaczono inaczej, wszystkie funkcje PROTOKOŁU HTTP opisane w tym dokumencie mają również zastosowanie do protokołu HTTPS.

## <a name="http-and-https-constraints"></a>Ograniczenia protokołów HTTP i HTTPS

Protokół HTTP sieci Web NetX implementuje standard HTTP 1.1. Poniżej przedstawiono jednak następujące ograniczenia:

1. Potokowanie żądań nie jest obsługiwane
1. Serwer HTTP obsługuje zarówno uwierzytelnianie podstawowe, jak i uwierzytelnianie szyfrowane MD5, ale nie md5-sess. Obecnie klient HTTP obsługuje tylko uwierzytelnianie podstawowe. W przypadku korzystania z protokołu TLS dla protokołu HTTPS nadal można używać uwierzytelniania HTTP.
1. Kompresja zawartości nie jest obsługiwana.
1. Żądania TRACE, OPTIONS i CONNECT nie są obsługiwane.
1. Pula pakietów skojarzona z serwerem HTTP lub klientem musi być wystarczająco duża, aby pomieścić pełny nagłówek HTTP.
1. Usługi klienta HTTP są tylko do transferu zawartości — w tym pakiecie nie są dostępne żadne narzędzia do wyświetlania.

## <a name="http-url-resource-names"></a>Adres URL HTTP (nazwy zasobów)

Protokół HTTP jest przeznaczony do przesyłania zawartości w Internecie. Żądana zawartość jest określana przez uniwersalny lokalizator zasobów (URL). Jest to podstawowy składnik każdego żądania HTTP. Adresy URL zawsze zaczynają się od znaku "/" i zazwyczaj odpowiadają plikom na serwerze HTTP. Poniżej przedstawiono typowe rozszerzenia plików HTTP:

- **.htm** **(lub.html**) HTML (HTML)
- **.txt** Zwykły tekst ASCII
- **.gif** Binarny obraz GIF
- **.xbm** Binarny obraz Xbitmap

## <a name="http-client-requests"></a>Żądania klientów HTTP

Protokół HTTP ma prosty mechanizm żądania zawartości internetowej. Istnieje zestaw standardowych poleceń HTTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia na dobrze znanym porcie TCP *80 (port 443* dla protokołu HTTPS). Poniżej przedstawiono niektóre z podstawowych poleceń HTTP:

- **POBIERZ *zasób* HTTP/1.1** Pobierz określony zasób
- ***ZAsób* POST HTTP/1.1** Pobierz określony zasób i przekaż dołączone dane wejściowe do serwera HTTP
- ***Zasób* HEAD HTTP/1.1** Serwer HTTP jest traktowany jak get, ale nie zawartość jest zwracana
- **HTTP/1.1** zasobu PUT Umieść zasób na serwerze HTTP
- **DELETE *zasobu* HTTP/1.1** Usuwanie zasobu na serwerze

Te polecenia ASCII są generowane wewnętrznie przez przeglądarki internetowe i usługi klienta HTTP sieci Web NetX w celu wykonywania operacji HTTP na serwerze HTTP.

Należy pamiętać, że aplikacja klienta HTTP powinna używać portu 80 lub portu 443, jeśli jest używany protokół HTTPS. Interfejsy API HTTP klienta i serwera mają port jako parametr — dla wygody zdefiniowano makra NX_WEB_HTTP_SERVER_PORT (port 80) i NX_WEB_HTTPS_SERVER_PORT (port 443). Port serwera HTTP można również zmienić w czasie wykonywania przy użyciu *nx_web_http_client_set_connect_port().* Aby uzyskać więcej informacji na temat tej usługi, zobacz Rozdział 4.

## <a name="http-server-responses"></a>Odpowiedzi serwera HTTP

Serwer HTTP używa tego samego dobrze znanego portu *TCP 80 (443 dla protokołu HTTPS)* do wysyłania odpowiedzi na polecenia klienta. Gdy serwer HTTP przetwarza polecenie Client, zwraca ciąg odpowiedzi ASCII zawierający 3-cyfrowy numeryczny kod stanu. Odpowiedź liczbowa jest używana przez oprogramowanie klienckie HTTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej znajduje się lista różnych odpowiedzi serwera HTTP na polecenia klienta:

- **200** Żądanie powiodło się
- **Żądanie 400** nie zostało poprawnie utworzone
- **401** Nieautoryzowane żądanie, klient musi wysłać uwierzytelnianie
- **404 Nie** znaleziono określonego zasobu w żądaniu
- Wewnętrzny błąd serwera HTTP **500**
- **501 Żądanie** nie zostało zaimplementowane przez serwer HTTP
- **502 Usługa** nie jest dostępna

Na przykład pomyślne żądanie klienta dotyczące put pliku "test.htm" odpowiada komunikatem "HTTP/1.1 200 OK".

## <a name="http-communication"></a>Komunikacja HTTP

Jak wspomniano wcześniej, serwer HTTP używa dobrze znanego portu *TCP 80 (443* dla protokołu HTTPS) do pola Żądania klienta. Klienci HTTP mogą używać dowolnego dostępnego portu TCP dla połączeń wychodzących. Ogólna sekwencja zdarzeń HTTP jest następująca:

**Żądanie HTTP GET:**

1. Problemy z klientem: połączenie TCP z portem serwera 80 (lub 443 dla protokołu HTTPS).
1. Jeśli jest używany protokół HTTPS, po połączeniu TCP następuje uściślnianie protokołu TLS w celu uwierzytelnienia serwera i ustanowienia bezpiecznego kanału.
1. Klient wysyła żądanie **"GET *resource* HTTP/1.1"**(wraz z innymi informacjami nagłówka).
1. Serwer tworzy komunikat **"HTTP/1.1 200 OK"** z dodatkowymi informacjami, po których natychmiast następuje zawartość zasobu (jeśli jest).
1. Serwer rozłącza się z klientem (protokół TLS jest zamykany, jeśli jest używany protokół HTTPS).
1. Klient rozłącza się z gniazdem (TLS jest zamykany po alercie rozłączenia z serwerem).

**Żądanie HTTP PUT:**

1. Problemy z klientem: połączenie TCP z portem serwera 80 (lub 443).
1. Jeśli jest używany protokół HTTPS, po połączeniu TCP następuje uściślnianie protokołu TLS w celu uwierzytelnienia serwera i ustanowienia bezpiecznego kanału.
1. Klient wysyła żądanie "PUT resource HTTP/1.1" wraz z innymi informacjami nagłówka, a następnie zawartość zasobu.
1. Serwer tworzy komunikat "HTTP/1.1 200 OK" z dodatkowymi informacjami, po których natychmiast następuje zawartość zasobu.
1. Serwer wykonuje rozłączenie.
1. Klient wykonuje rozłączenie.

> [!NOTE]
> Jak wspomniano wcześniej, serwer HTTP może zmienić domyślny port połączenia (80 lub 443) w czasie wykonywania inny port przy użyciu metody *nx_web_http_client_set_connect_port()* dla serwerów sieci Web, które używają alternatywnych portów do łączenia się z klientami.

## <a name="http-authentication"></a>Uwierzytelnianie HTTP

Uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich żądań internetowych. Istnieją dwa rodzaje uwierzytelniania: *podstawowy i* *skrótowy*. Uwierzytelnianie podstawowe jest równoważne *uwierzytelnianiu nazwy* *i hasła* w wielu protokołach. W przypadku uwierzytelniania podstawowego protokołu HTTP nazwy i hasła są concatenated i zakodowane w formacie base64. Główną wadą uwierzytelniania podstawowego jest nazwa i hasło są przesyłane otwarcie w żądaniu. Ułatwia to kradzież nazwy i hasła. Uwierzytelnianie szyfrowane rozwiązuje ten problem, nigdy nie przesyłając nazwy i hasła w żądaniu. Zamiast tego algorytm jest używany do wyprowadzenia 128-bitowego skrótu na podstawie nazwy, hasła i innych informacji. Internetowy serwer HTTP NetX obsługuje standardowy algorytm skrótu MD5.

Kiedy jest wymagane uwierzytelnianie? Serwer HTTP decyduje, czy żądany zasób wymaga uwierzytelnienia. Jeśli uwierzytelnianie jest wymagane, a żądanie klienta nie zawiera odpowiedniego uwierzytelniania, do klienta jest wysyłana odpowiedź "HTTP/1.1 401 Brak autoryzacji" z wymaganym typem uwierzytelniania. Klient powinien następnie tworzyć nowe żądanie z odpowiednim uwierzytelnianiem.

W przypadku korzystania z protokołu HTTPS serwer HTTPS nadal może korzystać z uwierzytelniania HTTP. W takim przypadku protokół TLS jest używany do szyfrowania całego ruchu HTTP, więc użycie podstawowego uwierzytelniania *HTTP* nie stanowi zagrożenia bezpieczeństwa. *Uwierzytelnianie* szyfrowane jest również dozwolone, ale nie zapewnia znaczących ulepszeń zabezpieczeń w porównaniu z uwierzytelnianiem podstawowym za pośrednictwem protokołu TLS.

## <a name="http-authentication-callback"></a>Wywołanie zwrotne uwierzytelniania HTTP

Jak wspomniano wcześniej, uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane we wszystkich transferach sieci Web. Ponadto uwierzytelnianie jest zwykle zależne od zasobów. Dostęp do niektórych zasobów na serwerze wymaga uwierzytelniania, a inne nie. Pakiet NetX Web HTTP Server umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_web_http_server_create)*** procedury wywołania zwrotnego uwierzytelniania, która jest wywoływana na początku obsługi każdego żądania klienta HTTP.

Procedura wywołania zwrotnego dostarcza serwerowi HTTP sieci Web NetX nazwę użytkownika, hasło i ciągi znaków skojarzone z zasobem i zwraca typ wymaganego uwierzytelniania. Jeśli dla zasobu nie jest wymagane żadne uwierzytelnianie, wywołanie zwrotne uwierzytelniania powinno zwrócić wartość **NX_WEB_HTTP_DONT_AUTHENTICATE**. W przeciwnym razie, jeśli dla określonego zasobu jest wymagane uwierzytelnianie podstawowe, procedura powinna zwrócić **NX_WEB_HTTP_BASIC_AUTHENTICATE**. I na koniec, jeśli wymagane jest uwierzytelnianie szyfrowane MD5, procedura wywołania zwrotnego powinna zwrócić **NX_WEB_HTTP_DIGEST_AUTHENTICATE**. Jeśli żadne uwierzytelnianie nie jest wymagane dla żadnego zasobu dostarczonego przez serwer HTTP, wywołanie zwrotne nie jest potrzebne, a do wywołania tworzenia serwera HTTP można uzyskać wskaźnik NULL.

Format procedury wywołania zwrotnego uwierzytelniania aplikacji jest bardzo prosty i jest zdefiniowany poniżej:

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
- **zasób** Żądany zasób.
- **name (nazwa)** Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika.
- **hasło** Miejsce docelowe wskaźnika do wymaganego hasła.
- **realm (realm)** Miejsce docelowe dla wskaźnika do realm dla tego uwierzytelniania.

Wartość zwracana przez procedurę uwierzytelniania określa, czy wymagane jest uwierzytelnianie. Wskaźniki name, password i realm nie są używane, **NX_WEB_HTTP_DONT_AUTHENTICATE** są zwracane przez procedurę wywołania zwrotnego uwierzytelniania. W przeciwnym razie deweloper serwera HTTP musi upewnić się, **NX_WEB_HTTP_MAX_USERNAME** i **NX_WEB_HTTP_MAX_PASSWORD** zdefiniowane w pliku *nx_web_http_server.h* są wystarczająco duże dla nazwy użytkownika i hasła określonego w wywołaniu zwrotym uwierzytelniania. Oba mają domyślny rozmiar 20 znaków.

## <a name="http-invalid-usernamepassword-callback"></a>Nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła HTTP

Opcjonalne nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła na serwerze HTTP sieci Web NetX jest wywoływane, jeśli serwer HTTP otrzyma nieprawidłową kombinację nazwy użytkownika i hasła w żądaniu klienta. Jeśli aplikacja serwera HTTP zarejestruje wywołanie zwrotne na serwerze HTTP, zostanie ono wywołane, jeśli uwierzytelnianie podstawowe lub szyfrowane zakończy się niepowodzeniem w przypadku niepowodzenia uwierzytelniania *nx_web_http_server_get_process(),* w *nx_web_http_server_put_process()* lub w *nx_web_http_server_delete_process().*

Aby zarejestrować wywołanie zwrotne na serwerze HTTP, dla internetowego serwera HTTP NetX zdefiniowano następującą usługę.

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

## <a name="http-insert-gmt-date-header-callback"></a>Wywołanie zwrotne nagłówka daty HTTP Insert GMT

Na serwerze HTTP sieci Web NetX istnieje opcjonalne wywołanie zwrotne, które umożliwia wstawienie nagłówka daty do komunikatów odpowiedzi. To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie put lub get

Aby zarejestrować wywołanie zwrotne daty GMT na serwerze HTTP, zdefiniowano następującą usługę.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

Typ NX_WEB_HTTP_SERVER_DATE danych jest zdefiniowany w następujący sposób:

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

## <a name="http-cache-info-get-callback"></a>Informacje o pamięci podręcznej HTTP : uzyskiwanie wywołania zwrotnego

Serwer HTTP ma wywołanie zwrotne, aby zażądać maksymalnego wieku i daty z aplikacji HTTP dla określonego zasobu. Te informacje służą do określenia, czy serwer HTTP wysyła całą stronę w odpowiedzi na żądanie Get klienta. Jeśli w żądaniu klienta nie zostanie odnaleziona data "jeśli została zmodyfikowana od" lub nie jest ona dopasowana do daty "ostatniej modyfikacji" zwróconej przez wywołanie zwrotne get cache, wysyłana jest cała strona.

Aby zarejestrować wywołanie zwrotne na serwerze HTTP, zdefiniowano następującą usługę:

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>Obsługa fragmentatywnego kodowania transferu HTTP

Jeśli nie można określić całkowitej długości komunikatu HTTP przed jego wysłaniem, można użyć funkcji Chunked Transfer Coding do wysyłania komunikatów jako serii fragmentów bez pola nagłówka "Content-Length". Ta funkcja jest obsługiwana we wszystkich komunikatach żądań HTTP i odpowiedzi. Jako odbiornik ta funkcja jest obsługiwana, a nagłówek fragmentu jest przetwarzany w sposób przezroczysty przez logikę wewnętrzną. Jako nadawca interfejs *API* nx_web_http_client_request_chunked_set i *nx_web_http_server_response_chunked_set* muszą być wywoływane odpowiednio przez klienta i serwer.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

Aby uzyskać więcej informacji na temat tych usług, zobacz ich opisy w rozdziale 3 "Opis usług HTTP".

## <a name="http-multipart-support"></a>Obsługa wieloczęściowego protokołu HTTP

Wieloaspektowe internetowe rozszerzenia poczty (MIME) były pierwotnie przeznaczone dla protokołu SMTP, ale jego zastosowanie rozpowszechniło się na protokół HTTP. Funkcja MIME umożliwia komunikatom zawieranie komunikatów mieszanych (np. obraz/jpg i tekst/zwykły) w ramach tego samego komunikatu. Internetowy serwer HTTP NetX ma usługi do określania typu zawartości w komunikatach HTTP zawierających protokół MIME z klienta. Aby włączyć obsługę wieloczęściową protokołu HTTP i korzystać z tych usług, **należy zdefiniować NX_WEB_HTTP_MULTIPART_ENABLE** konfiguracji.

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

Aby uzyskać więcej informacji na temat korzystania z tych usług, zobacz ich opis w rozdziale 3 "Opis usług HTTP".

## <a name="http-multi-thread-support"></a>Obsługa wielu wątków HTTP

Usługi klienta HTTP sieci Web NetX mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta HTTP powinny być wykonywane kolejno z tego samego wątku.

W przypadku korzystania z protokołu HTTPS usługi klienta HTTP sieci Web NetX mogą być wywoływane z wielu wątków, ale ze względu na dodatkową złożoność podstawowej funkcjonalności protokołu TLS każdy wątek powinien mieć pojedyncze, niezależne wystąpienie klienta HTTP (NX_WEB_HTTP_CLIENT struktury sterowania).

## <a name="http-rfcs"></a>RFC HTTP

Protokół HTTP sieci Web NetX jest zgodny ze standardem RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2616 "Hypertext Transfer Protocol – HTTP/1.1", RFC 2581 "TCP Congestion Control", RFC 1122 "Requirements for Internet Hosts" (Wymagania dotyczące hostów internetowych) i powiązanymi RFC 2581 "Tcp Congestion Control".

W przypadku protokołu HTTPS protokół HTTP sieci Web NetX jest zgodny ze specyfikacją RFC 2818 "HTTP over TLS".
