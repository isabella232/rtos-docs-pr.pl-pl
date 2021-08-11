---
title: Rozdział 1 — Wprowadzenie do protokołu HTTP NetX
description: W tym dokumencie wyjaśniono, jak protokół HTTP jest protokołem przeznaczonym do przesyłania zawartości w Internecie.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1e37328ab9cff0ab635a00113a83ee256c39303ce24b0cb292b6c2eaa71236f5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799391"
---
# <a name="chapter-1---introduction-to-netx-http"></a>Rozdział 1 — Wprowadzenie do protokołu HTTP NetX

Protokół HTTP (Hypertext Transfer Protocol) to protokół przeznaczony do przesyłania zawartości w Sieci Web. HTTP to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości. W związku z tym protokół HTTP jest wysoce niezawodnym protokołem transferu zawartości. Protokół HTTP jest jednym z najczęściej używanych protokołów aplikacji. Wszystkie operacje w Internecie korzystają z protokołu HTTP.

## <a name="http-requirements"></a>Wymagania dotyczące protokołu HTTP

Aby pakiet HTTP NetX działał prawidłowo, musi być zainstalowany pakiet NetX (w wersji 5.2 lub nowszej). Ponadto należy już utworzyć wystąpienie adresu IP i włączyć protokół TCP w tym samym wystąpieniu adresu IP. Plik demonstracyjny w sekcji "Small Example System" (Mały przykładowy system) w **rozdziale 2** pokazuje, jak to zrobić.

Część klienta HTTP pakietu HTTP NetX nie ma dodatkowych wymagań.

Część serwera HTTP pakietu HTTP NetX ma kilka dodatkowych wymagań. Po pierwsze wymaga pełnego dostępu do dobrze znanego *portu 80* protokołu TCP do obsługi wszystkich żądań HTTP klienta. Serwer HTTP jest również przeznaczony do użytku z osadzonym systemem plików FileX. Jeśli plik FileX nie jest dostępny, użytkownik może portować części pliku FileX używane do własnego środowiska. Omówiono to w kolejnych sekcjach tego przewodnika.

## <a name="http-constraints"></a>Ograniczenia HTTP 

Protokół HTTP NetX implementuje standard HTTP 1.0. Istnieją jednak następujące ograniczenia:

1.  Połączenia trwałe nie są obsługiwane

2.  Potokowanie żądań nie jest obsługiwane

3.  Serwer HTTP obsługuje zarówno uwierzytelnianie podstawowe, jak i uwierzytelnianie szyfrowane MD5, ale nie md5-sess. Obecnie klient HTTP obsługuje tylko uwierzytelnianie podstawowe.

4.  Kompresja zawartości nie jest obsługiwana.

5.  Żądania TRACE, OPTIONS i CONNECT nie są obsługiwane.

6.  Pula pakietów skojarzona z serwerem HTTP lub klientem musi być wystarczająco duża, aby pomieścić pełny nagłówek HTTP.

7.  Usługi klienta HTTP są tylko do transferu zawartości — w tym pakiecie nie są dostępne żadne narzędzia do wyświetlania.

## <a name="http-url-resource-names"></a>Adres URL HTTP (nazwy zasobów)

Protokół HTTP jest przeznaczony do przesyłania zawartości w Internecie. Żądana zawartość jest określana przez uniwersalny lokalizator zasobów (URL). Jest to podstawowy składnik każdego żądania HTTP. Adresy URL zawsze zaczynają się od znaku "/" i zazwyczaj odpowiadają plikom na serwerze HTTP. Poniżej przedstawiono typowe rozszerzenia plików HTTP:

- **.htm (lub .html)** HTML (HTML)
- **.txt** Zwykły tekst ASCII
- **.gif** Binarny obraz GIF
- **.xbm** Binarny obraz Xbitmap

## <a name="http-client-requests"></a>Żądania klientów HTTP

Protokół HTTP ma prosty mechanizm żądania zawartości internetowej. Zasadniczo istnieje zestaw standardowych poleceń HTTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia na dobrze znanym porcie TCP *80.* Poniżej przedstawiono niektóre z podstawowych poleceń HTTP:

- POBIERZ zasób HTTP/1.0 *Pobierz określony zasób*
- Zasób POST HTTP/1.0 *Pobierz określony zasób* i przekaż dołączone dane wejściowe do serwera HTTP
- Zasób HEAD HTTP/1.0 *Traktowany jak get,* ale nie zawartość jest zwracany przez serwer HTTP
- Umieść zasób PUT HTTP/1.0, *umieść zasób na serwerze HTTP*
- USUŃ zasób HTTP/1.0 *Usuń zasób na serwerze*

Te polecenia ASCII są generowane wewnętrznie przez przeglądarki internetowe i usługi klienta HTTP NetX w celu wykonywania operacji HTTP na serwerze HTTP.

>[!NOTE] 
> Aplikacja klienta HTTP domyślnie łączy port 80. Można jednak zmienić port połączenia z serwerem HTTP w czasie wykonywania przy użyciu *nx_http_client_set_connect_port* usługi. Aby uzyskać więcej informacji na temat tej usługi, zobacz Rozdział 4. Ma to na celu zastosowanie serwerów internetowych, które czasami używają alternatywnych portów dla połączeń klienckich.

## <a name="http-server-responses"></a>Odpowiedzi serwera HTTP

Serwer HTTP używa tego samego dobrze znanego portu *TCP 80* do wysyłania odpowiedzi na polecenia klienta. Gdy serwer HTTP przetwarza polecenie Client, zwraca ciąg odpowiedzi ASCII zawierający 3-cyfrowy numeryczny kod stanu. Odpowiedź liczbowa jest używana przez oprogramowanie klienckie HTTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej znajduje się lista różnych odpowiedzi serwera HTTP na polecenia klienta:

- 200 *Żądanie powiodło się*
- Żądanie 400 *nie zostało poprawnie utworzone*
- 401 *Nieautoryzowane żądanie, klient musi wysłać uwierzytelnianie*
- 404 *Nie znaleziono określonego zasobu w żądaniu*
- Wewnętrzny błąd *serwera HTTP* 500
- 501 *Żądanie nie zostało zaimplementowane przez serwer HTTP*
- 502 *Usługa nie jest dostępna*

Na przykład pomyślne żądanie klienta put pliku "test.htm" odpowiada komunikatem "HTTP/1.0 200 OK".

## <a name="http-communication"></a>Komunikacja HTTP

Jak wspomniano wcześniej, serwer HTTP używa dobrze znanego portu *TCP 80* do pola Żądania klienta. Klienci HTTP mogą używać dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń HTTP jest następująca:

**Żądanie HTTP GET:**

1.  Problemy z klientem podczas nawiązywania połączenia TCP z portem 80 serwera.

2.  Klient wysyła żądanie **"GET resource HTTP/1.0"**(wraz z innymi informacjami nagłówka).

3.  Serwer tworzy komunikat **"HTTP/1.0 200 OK"** z dodatkowymi informacjami, po których natychmiast następuje zawartość zasobu (jeśli jest).

4.  Serwer wykonuje rozłączenie.

5.  Klient wykonuje rozłączenie.

**Żądanie HTTP PUT:**

1. Problemy z klientem podczas nawiązywania połączenia TCP z portem 80 serwera.

2. Klient wysyła żądanie **"PUT resource HTTP/1.0"** wraz z innymi informacjami nagłówka, a następnie zawartość zasobu.

3. Serwer tworzy komunikat **"HTTP/1.0 200 OK"** z dodatkowymi informacjami, po których natychmiast następuje zawartość zasobu.

4. Serwer wykonuje rozłączenie.

5. Klient wykonuje rozłączenie.

>[!NOTE] 
> Jak wspomniano wcześniej, klient HTTP może zmienić domyślny port połączenia z 80 na inny przy użyciu interfejsu *nx_http_client_set_connect_port* dla serwerów sieci Web, które używają alternatywnych portów do łączenia się z klientami.

## <a name="http-authentication"></a>Uwierzytelnianie HTTP

Uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich żądań internetowych. Istnieją dwa rodzaje uwierzytelniania: *podstawowy i* *skrótowy*. Uwierzytelnianie podstawowe jest równoważne *uwierzytelnianiu nazwy* *i hasła* w wielu protokołach. W przypadku uwierzytelniania podstawowego protokołu HTTP nazwy i hasła są concatenated i zakodowane w formacie base64. Główną wadą uwierzytelniania podstawowego jest nazwa i hasło są przesyłane otwarcie w żądaniu. Ułatwia to kradzież nazwy i hasła. Uwierzytelnianie szyfrowane rozwiązuje ten problem, nigdy nie przesyłając nazwy i hasła w żądaniu. Zamiast tego algorytm jest używany do wyprowadzenia klucza 128-bitowego lub skrótu z nazwy, hasła i innych informacji. Serwer HTTP NetX obsługuje standardowy algorytm skrótu MD5.

Kiedy jest wymagane uwierzytelnianie? Zasadniczo serwer HTTP decyduje, czy żądany zasób wymaga uwierzytelnienia. Jeśli uwierzytelnianie jest wymagane, a żądanie klienta nie zawiera odpowiedniego uwierzytelniania, do klienta jest wysyłana odpowiedź "HTTP/1.0 401 Unauthorized" z typem wymaganego uwierzytelniania. Klient powinien następnie tworzyć nowe żądanie z odpowiednim uwierzytelnianiem.

## <a name="http-authentication-callback"></a>Wywołanie zwrotne uwierzytelniania HTTP

Jak wspomniano wcześniej, uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane we wszystkich transferach sieci Web. Ponadto uwierzytelnianie jest zwykle zależne od zasobów. Dostęp do niektórych zasobów na serwerze wymaga uwierzytelniania, a inne nie. Pakiet NetX HTTP Server umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_http_server_create)*** procedury wywołania zwrotnego uwierzytelniania, która jest wywoływana na początku obsługi każdego żądania klienta HTTP.

Procedura wywołania zwrotnego udostępnia serwerowi HTTP NetX nazwę użytkownika, hasło i ciągi dotyczące realm skojarzone z zasobem oraz zwraca typ wymaganego uwierzytelniania. Jeśli dla zasobu nie jest wymagane żadne uwierzytelnianie, wywołanie zwrotne uwierzytelniania powinno zwrócić wartość **NX_HTTP_DONT_AUTHENTICATE**. W przeciwnym razie, jeśli dla określonego zasobu jest wymagane uwierzytelnianie podstawowe, procedura powinna zwrócić **NX_HTTP_BASIC_AUTHENTICATE**. I na koniec, jeśli wymagane jest uwierzytelnianie szyfrowane MD5, procedura wywołania zwrotnego powinna zwrócić **NX_HTTP_DIGEST_AUTHENTICATE**. Jeśli żadne uwierzytelnianie nie jest wymagane dla żadnego zasobu dostarczonego przez serwer HTTP, wywołanie zwrotne nie jest potrzebne i można uzyskać wskaźnik NULL do wywołania tworzenia serwera HTTP.

Format procedury wywołania zwrotnego uwierzytelniania aplikacji jest bardzo prosty i jest zdefiniowany poniżej:

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
- *zasób* Żądany zasób.
- *name (nazwa)* Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika.
- *hasło* Miejsce docelowe wskaźnika do wymaganego hasła.
- *realm (realm)* Miejsce docelowe wskaźnika do realm dla tego uwierzytelniania.

Wartość zwracana przez procedurę uwierzytelniania określa, czy wymagane jest uwierzytelnianie. Wskaźniki name, password i realm nie są **używane, jeśli NX_HTTP_DONT_AUTHENTICATE** zwracana przez procedurę wywołania zwrotnego uwierzytelniania. W przeciwnym razie deweloper serwera HTTP musi upewnić się, **NX_HTTP_MAX_USERNAME** i **NX_HTTP_MAX_PASSWORD** zdefiniowane w pliku *nx_http_server.h* są wystarczająco duże dla nazwy użytkownika i hasła określonego w wywołaniu zwrotym uwierzytelniania. Oba te znaki mają domyślnie rozmiar 20 znaków.

## <a name="http-invalid-usernamepassword-callback"></a>Nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła HTTP

Opcjonalne nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła na serwerze HTTP NetX jest wywoływane, jeśli serwer HTTP otrzyma nieprawidłową kombinację nazwy użytkownika i hasła w żądaniu klienta. Jeśli aplikacja serwera HTTP zarejestruje wywołanie zwrotne na serwerze *HTTP,* zostanie ono wywołane w przypadku niepowodzenia uwierzytelniania podstawowego lub szyfrowanego w usługach *nx_http_server_get_process*, nx_http_server_put_process lub *nx_http_server_delete_process.*

Aby zarejestrować wywołanie zwrotne na serwerze HTTP, następująca usługa jest zdefiniowana na serwerze HTTP NetX.

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

## <a name="http-insert-gmt-date-header-callback"></a>Wywołanie zwrotne nagłówka daty HTTP Insert GMT

Na serwerze HTTP NetX istnieje opcjonalne wywołanie zwrotne, które umożliwia wstawienie nagłówka daty do komunikatów odpowiedzi. To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie put lub get

Aby zarejestrować wywołanie zwrotne daty GMT na serwerze HTTP, następująca usługa jest zdefiniowana na serwerze HTTP NetX.

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

Typ NX_HTTP_SERVER_DATE danych jest zdefiniowany w następujący sposób:

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

## <a name="http-cache-info-get-callback"></a>Uzyskiwanie wywołania zwrotnego informacji o pamięci podręcznej HTTP

Serwer HTTP ma wywołanie zwrotne, aby zażądać maksymalnego wieku i daty z aplikacji HTTP dla określonego zasobu. Te informacje służą do określenia, czy serwer HTTP wysyła całą stronę w odpowiedzi na żądanie Get klienta. Jeśli w żądaniu klienta nie znaleziono daty "jeśli zmodyfikowano od" lub nie jest ona dopasowana do daty "ostatniej modyfikacji" zwróconej przez wywołanie zwrotne get pamięci podręcznej, wysyłana jest cała strona.

Aby zarejestrować wywołanie zwrotne na serwerze HTTP, zdefiniowano następującą usługę:

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a>Obsługa wieloczęściowego protokołu HTTP

Protokół MIME (Multipurpose Internet Mail Extensions) pierwotnie był przeznaczony dla protokołu SMTP, ale jego zastosowanie rozpowszechniło się na protokół HTTP. MiME umożliwia wiadomościom zawieranie różnych typów komunikatów (np. image/jpg i text/plain) w ramach tego samego komunikatu. Serwer HTTP NetX dodał usługi służące do określania typu zawartości w komunikatach HTTP zawierających mime z klienta. Aby włączyć obsługę wieloczęściową protokołu HTTP i korzystać z tych usług, NX_HTTP_MULTIPART_ENABLE **należy** zdefiniować opcję konfiguracji.

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

Aby uzyskać więcej informacji na temat korzystania z tych usług, zobacz ich opis w rozdziale 3 "Opis usług HTTP".

## <a name="http-multi-thread-support"></a>Obsługa wielu wątków PROTOKOŁU HTTP

Usługi klienta HTTP NetX mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta HTTP powinny być wykonywane kolejno z tego samego wątku.

## <a name="http-rfcs"></a>RFC HTTP

Protokół HTTP NetX jest zgodny ze standardem RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2581 "Kontrola przeciążenia tcp", RFC 1122 "Wymagania dotyczące hostów internetowych" i powiązanymi RFC.