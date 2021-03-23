---
title: Rozdział 1 — wprowadzenie do NetX HTTP
description: W tym dokumencie wyjaśniono, jak protokół HTTP jest protokołem przeznaczonym do przesyłania zawartości w sieci Web.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822621"
---
# <a name="chapter-1---introduction-to-netx-http"></a>Rozdział 1 — wprowadzenie do NetX HTTP

Protokół HTTP (Hypertext Transfer Protocol) to protokół przeznaczony do przesyłania zawartości w sieci Web. HTTP to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości. W związku z tym protokół HTTP jest wysoce niezawodnym protokołem transferu zawartości. Protokół HTTP jest jednym z najczęściej używanych protokołów aplikacji. Wszystkie operacje w sieci Web korzystają z protokołu HTTP.

## <a name="http-requirements"></a>Wymagania dotyczące protokołu HTTP

Aby zapewnić prawidłowe działanie, pakiet HTTP NetX wymaga zainstalowania NetX (wersja 5,2 lub nowsza). Ponadto należy już utworzyć wystąpienie adresu IP, a dla tego samego wystąpienia IP musi być włączony protokół TCP. Plik demonstracyjny w sekcji "mały przykładowy system" w **rozdziale 2** pokazuje, jak to zrobić.

Część klienta HTTP NetX pakietu HTTP nie ma żadnych dalszych wymagań.

Część serwera HTTP NetX pakietu HTTP ma kilka dodatkowych wymagań. Najpierw wymaga pełnego dostępu do *dobrze znanego portu TCP 80* do obsługi wszystkich żądań HTTP klienta. Serwer HTTP jest również przeznaczony do użycia z osadzonym systemem plików FileX. Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku. Zostało to omówione w kolejnych sekcjach tego przewodnika.

## <a name="http-constraints"></a>Ograniczenia HTTP 

Protokół HTTP NetX implementuje Standard HTTP 1,0. Istnieją jednak następujące ograniczenia:

1.  Połączenia trwałe nie są obsługiwane

2.  Przetwarzanie potokowe żądań nie jest obsługiwane

3.  Serwer HTTP obsługuje zarówno uwierzytelnianie podstawowe, jak i MD5 szyfrowanego, ale nie MD5-sess. W tej chwili klient HTTP obsługuje tylko uwierzytelnianie podstawowe.

4.  Kompresja zawartości nie jest obsługiwana.

5.  ŚLEDZENIE, opcje i żądania połączenia nie są obsługiwane.

6.  Pula pakietów skojarzona z serwerem HTTP lub klientem musi być wystarczająco duża, aby można było przechowywać kompletny nagłówek HTTP.

7.  Usługi klienta HTTP są przeznaczone tylko do transferu zawartości — w tym pakiecie nie ma dostępnych narzędzi do wyświetlania.

## <a name="http-url-resource-names"></a>Adres URL HTTP (nazwy zasobów)

Protokół HTTP jest przeznaczony do przesyłania zawartości w sieci Web. Żądana zawartość jest określana przez adres URL (Universal Resource Locator). Jest to podstawowy składnik każdego żądania HTTP. Adresy URL zawsze zaczynają się od znaku "/" i zwykle odpowiadają plikom na serwerze HTTP. Poniżej przedstawiono typowe rozszerzenia plików HTTP:

- **. htm (lub. html)** HTML (HTML)
- **. txt** Zwykły tekst ASCII
- **. gif** Binarny obraz GIF
- **. XBM** Binarny obraz Xbitmap

## <a name="http-client-requests"></a>Żądania klientów HTTP

Protokół HTTP ma prosty mechanizm do żądania zawartości sieci Web. Istnieje zasadniczo zestaw standardowych poleceń HTTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia z *dobrze znanym portem TCP 80*. Poniżej przedstawiono niektóre z podstawowych poleceń HTTP:

- Pobieranie zasobu HTTP/1.0 *pobieranie określonego zasobu*
- Zaksięguj zasób HTTP/1.0 *Pobierz określony zasób i przekaż dołączone dane wejściowe do serwera http*
- Zasób główny HTTP/1.0 *traktowany jak GET, ale nie zawartość jest zwracany przez serwer http*
- Umieść zasób miejsca HTTP/1.0 *na serwerze HTTP*
- Usuń zasób HTTP/1.0 *usuwanie zasobu na serwerze*

Te polecenia ASCII są generowane wewnętrznie przez przeglądarki sieci Web i usługi klienta HTTP NetX do wykonywania operacji HTTP przy użyciu serwera HTTP.

>[!NOTE] 
> Aplikacja kliencka HTTP domyślnie jest portem Connect 80. Można jednak zmienić port połączenia na serwer HTTP w środowisku uruchomieniowym przy użyciu usługi *nx_http_client_set_connect_port* . Aby uzyskać szczegółowe informacje o tej usłudze, zobacz rozdział 4. Ma to na celu uwzględnienie serwerów sieci Web, które czasami używają alternatywnych portów do połączeń klienckich.

## <a name="http-server-responses"></a>Odpowiedzi serwera HTTP

Serwer HTTP używa tego samego *dobrze znanego portu TCP 80* do wysyłania odpowiedzi na polecenie klienta. Gdy serwer HTTP przetwarza polecenie klienta, zwraca ciąg odpowiedzi ASCII, który zawiera 3-cyfrowy kod stanu numerycznego. Odpowiedź numeryczna jest używana przez oprogramowanie klienckie HTTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej znajduje się lista różnych odpowiedzi serwera HTTP do poleceń klienta:

- 200 *żądanie powiodło* się
- 400 *żądanie nie zostało poprawnie sformułowane*
- 401 *żądanie nieautoryzowane, klient musi wysłać uwierzytelnianie*
- 404 *nie znaleziono określonego zasobu w żądaniu*
- 500 *wewnętrzny błąd serwera http*
- 501 *żądanie niezaimplementowane przez serwer http*
- *usługa 502 jest niedostępna*

Na przykład pomyślne żądanie klienta dotyczące umieszczenia pliku "test.htm" jest odpowiedzią na komunikat "HTTP/1.0 200 OK".

## <a name="http-communication"></a>Komunikacja HTTP

Jak wspomniano wcześniej, serwer HTTP korzysta z *dobrze znanego portu TCP 80* do pól żądań klientów. Klienci HTTP mogą korzystać z dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń HTTP jest następująca:

**Żądanie HTTP GET**:

1.  Problemy z klientem połączenia TCP z portem serwera 80.

2.  Klient wysyła żądanie "**Pobierz zasób http/1.0**" (wraz z innymi informacjami nagłówka).

3.  Serwer kompiluje komunikat "**http/1.0 200 OK**" z dodatkowymi informacjami, a następnie bezpośrednio przez zawartość zasobu (jeśli istnieje).

4.  Serwer wykonuje odłączenie.

5.  Klient wykonuje odłączenie.

**Żądanie HTTP Put**:

1. Problemy z klientem połączenia TCP z portem serwera 80.

2. Klient wysyła żądanie "**Umieść zasób http/1.0**" wraz z innymi informacjami nagłówka, a następnie zawartość zasobu.

3. Serwer kompiluje komunikat "**http/1.0 200 OK**" z dodatkowymi informacjami, a następnie bezpośrednio przez zawartość zasobów.

4. Serwer wykonuje odłączenie.

5. Klient wykonuje odłączenie.

>[!NOTE] 
> Jak wspomniano wcześniej, klient HTTP może zmienić domyślny port Connect z 80 na inny port przy użyciu *nx_http_client_set_connect_port* dla serwerów sieci Web, które używają alternatywnych portów do łączenia się z klientami.

## <a name="http-authentication"></a>Uwierzytelnianie HTTP

Uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich żądań sieci Web. Istnieją dwa typy uwierzytelniania, czyli *podstawowe* i *szyfrowane*. Uwierzytelnianie podstawowe jest równoważne z *nazwą* i *hasłem* uwierzytelnianiem w wielu protokołach. W podstawowym uwierzytelnianiu HTTP Nazwa i hasła są łączone i kodowane w formacie base64. Główną wadą uwierzytelniania podstawowego jest nazwa i hasło, które są przesyłane w ramach żądania w sposób otwarty. Sprawia to, że jest nieco łatwe do kradzieży nazwy i hasła. Uwierzytelnianie szyfrowane rozwiązuje ten problem, przez co nigdy nie przesyłamy nazwy i hasła w żądaniu. Zamiast tego algorytm służy do wyprowadzania klucza 128-bitowego lub skrótu z nazwy, hasła i innych informacji. Serwer HTTP NetX obsługuje standardowy algorytm MD5.

Kiedy jest wymagane uwierzytelnianie? W zasadzie serwer HTTP decyduje, czy żądany zasób wymaga uwierzytelnienia. Jeśli uwierzytelnianie jest wymagane, a żądanie klienta nie zawierało odpowiedniego uwierzytelniania, odpowiedź "HTTP/1.0 401 bez autoryzacji" z typem wymaganego uwierzytelniania jest wysyłana do klienta. Klient powinien następnie utworzyć nowe żądanie z właściwym uwierzytelnianiem.

## <a name="http-authentication-callback"></a>Wywołanie zwrotne uwierzytelniania HTTP

Jak wspomniano wcześniej, uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich transferów w sieci Web. Ponadto uwierzytelnianie jest zwykle zależne od zasobów. Dostęp do niektórych zasobów na serwerze wymaga uwierzytelnienia, a inne nie. Pakiet serwera HTTP NetX umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_http_server_create*** ) procedury wywołania zwrotnego uwierzytelniania, która jest wywoływana na początku obsługi każdego żądania klienta http.

Procedura wywołania zwrotnego udostępnia serwer HTTP NetX z nazwami użytkowników, hasła i obszarów skojarzonych z zasobem i zwracają wymagany typ uwierzytelniania. Jeśli dla zasobu nie jest wymagane żadne uwierzytelnianie, wywołanie zwrotne uwierzytelniania powinno zwrócić wartość **NX_HTTP_DONT_AUTHENTICATE**. W przeciwnym razie, jeśli dla określonego zasobu jest wymagane uwierzytelnianie podstawowe, procedura powinna zwrócić **NX_HTTP_BASIC_AUTHENTICATE**. A wreszcie, jeśli wymagane jest uwierzytelnianie MD5 Digest, procedura wywołania zwrotnego powinna zwracać **NX_HTTP_DIGEST_AUTHENTICATE**. Jeśli nie jest wymagane żadne uwierzytelnianie dla żadnego zasobu dostarczonego przez serwer HTTP, wywołanie zwrotne nie jest wymagane, a do utworzenia wywołania serwera HTTP można dostarczyć wskaźnik o wartości NULL.

Format procedury wywołania zwrotnego uwierzytelniania aplikacji jest bardzo prosty i został zdefiniowany poniżej:

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- *request_type* Określa żądanie klienta HTTP, prawidłowe żądania są zdefiniowane jako:
  - **NX_HTTP_SERVER_GET_REQUEST**
  - **NX_HTTP_SERVER_POST_REQUEST**
  - **NX_HTTP_SERVER_HEAD_REQUEST**
  - **NX_HTTP_SERVER_PUT_REQUEST**
  - **NX_HTTP_SERVER_DELETE_REQUEST**
- *zasób* Zażądano określonego zasobu.
- *Nazwa* Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika.
- *hasło* Miejsce docelowe wskaźnika do wymaganego hasła.
- *obszar* Miejsce docelowe wskaźnika w obszarze dla tego uwierzytelniania.

Wartość zwracana przez procedurę uwierzytelniania określa, czy jest wymagane uwierzytelnianie. nazwy, hasła i wskaźniki obszaru nie są używane, jeśli **NX_HTTP_DONT_AUTHENTICATE** jest zwracany przez procedurę wywołania zwrotnego uwierzytelniania. W przeciwnym razie deweloper serwera HTTP musi upewnić się, że **NX_HTTP_MAX_USERNAME** i **NX_HTTP_MAX_PASSWORD** zdefiniowane w *nx_http_server. h* są wystarczająco duże dla nazwy użytkownika i hasła określonych w wywołaniu wywołania zwrotnego uwierzytelniania. Są one domyślnie przyłączone do rozmiaru 20 znaków.

## <a name="http-invalid-usernamepassword-callback"></a>Nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła HTTP

Opcjonalne nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła w NetX serwerze HTTP jest wywoływane, jeśli serwer HTTP odbiera nieprawidłową kombinację nazwy użytkownika i hasła w żądaniu klienta. Jeśli aplikacja serwera HTTP rejestruje wywołanie zwrotne z serwerem HTTP, zostanie wywołane w przypadku niepowodzenia uwierzytelniania podstawowego lub szyfrowanego *w nx_http_server_get_process*, w *nx_http_server_put_process* lub *w nx_http_server_delete_process.*

W celu zarejestrowania wywołania zwrotnego z serwerem HTTP następująca usługa jest definiowana w NetX serwerze HTTP.

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
Typy żądań są zdefiniowane w następujący sposób:

- **NX_HTTP_SERVER_GET_REQUEST**
- **NX_HTTP_SERVER_POST_REQUEST**
- **NX_HTTP_SERVER_HEAD_REQUEST**
- **NX_HTTP_SERVER_PUT_REQUEST**
- **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>Wywołanie zwrotne nagłówka daty GMT w protokole HTTP

Istnieje opcjonalne wywołanie zwrotne w NetX serwerze HTTP, aby wstawić nagłówek daty w komunikatach odpowiedzi. To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie Put lub Get

Aby zarejestrować wywołanie zwrotne daty GMT z serwerem HTTP, następująca usługa jest zdefiniowana na serwerze HTTP NetX.

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

Typ danych NX_HTTP_SERVER_DATE jest zdefiniowany w następujący sposób:

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>Wywołanie zwrotne informacji o pamięci podręcznej HTTP

Serwer HTTP ma wywołanie zwrotne, aby zażądać maksymalnego wieku i daty z aplikacji HTTP dla określonego zasobu. Te informacje służą do określenia, czy serwer HTTP wysyła całą stronę w odpowiedzi na żądanie Get klienta. Jeśli wartość "If Modified" w żądaniu klienta nie zostanie znaleziona lub nie jest zgodna z datą "Ostatnia modyfikacja" zwracaną przez wywołanie zwrotne pobierania pamięci podręcznej, zostanie wysłana cała strona.

W celu zarejestrowania wywołania zwrotnego z serwerem HTTP jest definiowana następująca usługa:

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a>Obsługa wieloczęściowego protokołu HTTP

Rozszerzenia Multipurpose Internet Mail Extensions (MIME) zostały pierwotnie zamierzone dla protokołu SMTP, ale jego użycie ma rozproszenie do protokołu HTTP. Kodowanie MIME umożliwia komunikatów zawierających mieszane typy wiadomości (np. Image/jpg i Text/zwykły) w obrębie tego samego komunikatu. Serwer HTTP NetX dodał usługi do określenia typu zawartości w komunikatach HTTP zawierających MIME z klienta. Aby włączyć obsługę wieloczęściowego protokołu HTTP i korzystać z tych usług, należy zdefiniować **NX_HTTP_MULTIPART_ENABLE** opcji konfiguracji.

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

Aby uzyskać więcej informacji na temat korzystania z tych usług, zobacz opis w rozdziale 3 "Opis usług HTTP".

## <a name="http-multi-thread-support"></a>Obsługa wielowątkowości HTTP

Usługi klienta HTTP NetX można wywoływać z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta HTTP powinny być wykonywane w kolejności z tego samego wątku.

## <a name="http-rfcs"></a>Specyfikacje RFC protokołu HTTP

NetX HTTP jest zgodny z RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2581 "kontrola przeciążenia TCP", RFC 1122 "wymagania dotyczące hostów internetowych" i powiązane dokumenty RFC.