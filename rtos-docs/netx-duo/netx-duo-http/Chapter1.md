---
title: Rozdział 1 — Wprowadzenie do protokołu HTTP Azure RTOS NetX Duo
description: W tym rozdziale oprowadzono Azure RTOS HTTP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45f35f2c1bec142e10d29eedb6e5a88a8eb74771e5d4adf1d85b04a87ad59ab7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796212"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-http"></a>Rozdział 1 — Wprowadzenie do protokołu HTTP Azure RTOS NetX Duo

Http (Hypertext Transfer Protocol) to protokół przeznaczony do przesyłania zawartości w sieci Web. HTTP to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości. W związku z tym protokół HTTP jest wysoce niezawodnym protokołem transferu zawartości. PROTOKÓŁ HTTP jest jednym z najczęściej używanych protokołów aplikacji. Wszystkie operacje w Internecie korzystają z protokołu HTTP. Azure RTOS NetX Duo HTTP jest przeznaczony zarówno dla sieci IPv4, jak i IPv6. Protokół IPv6 nie zmienia bezpośrednio protokołu HTTP, chociaż niektóre zmiany w oryginalnym interfejsie API HTTP platformy Azure RTOS NetX są niezbędne do uwzględnienia protokołu IPv6 i zostaną opisane w tym dokumencie.

## <a name="http-requirements"></a>Wymagania dotyczące protokołu HTTP

Aby pakiet HTTP NetX Duo działał prawidłowo, wymaga zainstalowania netx duo (w wersji 5.2 lub nowszej). Ponadto wystąpienie adresu IP musi już zostać utworzone, a protokół TCP musi być włączony w tym samym wystąpieniu adresu IP. Aplikacja hosta IPv6 musi ustawić lokalny i globalny adres IPv6 połączenia przy użyciu interfejsu API IPv6 i/lub protokołu DHCPv6. Plik demonstracyjny w sekcji "Small Example System" (Mały przykładowy system) w **rozdziale 2** pokazuje, jak to zrobić.

Część HTTP Client pakietu HTTP NetX Duo nie ma dodatkowych wymagań.

Część HTTP Server pakietu HTTP NetX Duo ma kilka dodatkowych wymagań. Po pierwsze wymaga pełnego dostępu do dobrze znanego portu 80 protokołu TCP do obsługi wszystkich żądań HTTP klienta. Serwer HTTP jest również przeznaczony do użytku z osadzonym systemem plików. Jeśli plik FileX nie jest dostępny, użytkownik może portować części pliku FileX używane do własnego środowiska. Omówiono to w kolejnych sekcjach tego przewodnika.

## <a name="http-constraints"></a>Ograniczenia HTTP

Protokół HTTP NetX Duo implementuje standard HTTP 1.0. Istnieją jednak następujące ograniczenia:

1.  Połączenia trwałe nie są obsługiwane
2.  Potokowanie żądań nie jest obsługiwane
3.  Serwer HTTP obsługuje zarówno uwierzytelnianie podstawowe, jak i uwierzytelnianie szyfrowane MD5, ale nie uwierzytelnianie MD5-sess. Obecnie klient HTTP obsługuje tylko uwierzytelnianie podstawowe.
4.  Kompresja zawartości nie jest obsługiwana.
5.  Żądania TRACE, OPTIONS i CONNECT nie są obsługiwane.
6.  Pula pakietów skojarzona z serwerem HTTP lub klientem musi być wystarczająco duża, aby pomieścić pełny nagłówek HTTP.
7.  Usługi klienta HTTP są tylko do transferu zawartości — w tym pakiecie nie są dostępne żadne narzędzia do wyświetlania.

## <a name="http-url-resource-names"></a>Adres URL HTTP (nazwy zasobów)

Protokół HTTP jest przeznaczony do przesyłania zawartości w Internecie. Żądana zawartość jest określana przez uniwersalny lokalizator zasobów (URL). Jest to podstawowy składnik każdego żądania HTTP. Adresy URL zawsze zaczynają się od *znaku "/"* i zazwyczaj odpowiadają plikom na serwerze HTTP. Poniżej przedstawiono typowe rozszerzenia plików HTTP:

| Wewnętrzny | Znaczenie |
| --------- | ------- |
| .htm (lub .html) | HTML (Hypertext Markup Language) |
| txt | Zwykły tekst ASCII |
| gif | Binarny obraz GIF |
| .xbm | Binarny obraz Xbitmap |

## <a name="http-client-requests"></a>Żądania klientów HTTP

Protokół HTTP ma prosty mechanizm żądania zawartości internetowej. Zasadniczo istnieje zestaw standardowych poleceń HTTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia na dobrze znanym porcie TCP *80.* Poniżej przedstawiono niektóre z podstawowych poleceń HTTP:

| Polecenie HTTP | Znaczenie |
| ------------ | ------- |
| GET resource HTTP/1.0 | *Pobierz określony zasób* |
| HTTP/1.0 zasobu POST | *Pobierz określony zasób i przekaż dołączone dane wejściowe do serwera HTTP Serve* |
| Zasób HEAD HTTP/1.0 | *Serwer HTTP jest traktowany jak get, ale nie zawartość jest zwracana* |
| HTTP/1.0 zasobu PUT | *Umieść zasób na serwerze HTTP* |
| USUWANIE zasobu HTTP/1.0 | *Usuwanie zasobu na serwerze* |

Te polecenia ASCII są generowane wewnętrznie przez przeglądarki internetowe i usługi klienta HTTP NetX do wykonywania operacji HTTP na serwerze HTTP.

> [!NOTE]
> Aplikacja klienta HTTP domyślnie łączy się z portem 80. Można jednak zmienić port połączenia z serwerem HTTP w czasie wykonywania przy użyciu nx_http_client_set_connect_port usługi. Aby uzyskać więcej informacji na temat tej usługi, zobacz Rozdział 4. Ma to na celu zastosowanie serwerów internetowych, które czasami używają alternatywnych portów dla połączeń klienckich.

## <a name="http-server-responses"></a>Odpowiedzi serwera HTTP

Serwer HTTP używa tego samego dobrze znanego portu *TCP 80* do wysyłania odpowiedzi na polecenia klienta. Gdy serwer HTTP przetwarza polecenie Client, zwraca ciąg odpowiedzi ASCII zawierający 3-cyfrowy liczbowy kod stanu. Odpowiedź liczbowa jest używana przez oprogramowanie klienckie HTTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej znajduje się lista różnych odpowiedzi serwera HTTP na polecenia klienta:

| Pole liczbowe | Znaczenie |
| ------------- | ------- |
| *200* | *Żądanie powiodło się* |
| *400* |   *Żądanie nie zostało poprawnie utworzone* |
| *401* | *Nieautoryzowane żądanie, klient musi wysłać uwierzytelnianie* |
| *404* | *Nie znaleziono określonego zasobu w żądaniu* |
| *500* | *Wewnętrzny błąd serwera HTTP* |
| *501* | *Żądanie nie zaimplementowane przez serwer HTTP* |
| *502* | *Usługa nie jest dostępna* |

Na przykład pomyślne żądanie klienta put pliku "test.htm" odpowiada komunikatem "HTTP/1.0 200 OK".

## <a name="http-communication"></a>Komunikacja HTTP

Jak wspomniano wcześniej, serwer HTTP wykorzystuje dobrze znany port TCP 80 do pola Żądania klienta. Klienci HTTP mogą używać dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń HTTP jest następująca:

### <a name="http-get-request"></a>Żądanie HTTP GET:

1.  Problemy z klientem: połączenie TCP z portem 80 serwera.
2.  Klient wysyła żądanie **"GET resource HTTP/1.0"**(wraz z innymi informacjami nagłówka).
3.  Serwer tworzy komunikat **"HTTP/1.0 200 OK"** z dodatkowymi informacjami, po których natychmiast następuje zawartość zasobu (jeśli jest).
4.  Serwer wykonuje rozłączenie.
5.  Klient wykonuje rozłączenie.

### <a name="http-put-request"></a>Żądanie HTTP PUT:

1.  Problemy z klientem: połączenie TCP z portem 80 serwera.
2.  Klient wysyła żądanie **"PUT resource HTTP/1.0"** wraz z innymi informacjami nagłówka, a po nim zawartość zasobu.
3.  Serwer tworzy komunikat **"HTTP/1.0 200 OK"** z dodatkowymi informacjami, po których natychmiast następuje zawartość zasobu.
4.  Serwer wykonuje rozłączenie.
5.  Klient wykonuje rozłączenie.

> [!NOTE]
>Jak wspomniano wcześniej, klient HTTP może zmienić domyślny port połączenia z 80 na inny przy użyciu interfejsu *nx_http_client_set_connect_port* dla serwerów sieci Web, które używają alternatywnych portów do łączenia się z klientami.

## <a name="http-authentication"></a>Uwierzytelnianie HTTP

Uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich żądań internetowych. Istnieją dwa rodzaje uwierzytelniania: podstawowy i szyfrowane. Uwierzytelnianie podstawowe jest równoważne uwierzytelnianiu nazwy i hasła w wielu protokołach. W przypadku uwierzytelniania podstawowego protokołu HTTP nazwy i hasła są concatenated i zakodowane w formacie base64. Główną wadą uwierzytelniania podstawowego jest nazwa i hasło są przesyłane w żądaniu w sposób otwarty. Ułatwia to kradzież nazwy i hasła. Uwierzytelnianie szyfrowane rozwiązuje ten problem, nigdy nie przesyłając nazwy i hasła w żądaniu. Zamiast tego algorytm jest używany do wyprowadzenia 128-bitowego klucza lub skrótu z nazwy, hasła i innych informacji. Serwer HTTP NetX obsługuje standardowy algorytm skrótu MD5.

Kiedy jest wymagane uwierzytelnianie? Zasadniczo serwer HTTP decyduje, czy żądany zasób wymaga uwierzytelnienia. Jeśli uwierzytelnianie jest wymagane, a żądanie klienta nie zawiera odpowiedniego uwierzytelniania, do klienta jest wysyłana odpowiedź "HTTP/1.0 401 Brak autoryzacji" z typem wymaganego uwierzytelniania. Następnie oczekuje się, że klient będzie tworzyć nowe żądanie z odpowiednim uwierzytelnianiem.

## <a name="http-authentication-callback"></a>Wywołanie zwrotne uwierzytelniania HTTP

Jak wspomniano wcześniej, uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane we wszystkich transferach sieci Web. Ponadto uwierzytelnianie jest zwykle zależne od zasobów. Dostęp do niektórych zasobów na serwerze wymaga uwierzytelniania, a inne nie. Pakiet NetX HTTP Server umożliwia aplikacji określenie (za pośrednictwem wywołania *nx_http_server_create)* procedury wywołania zwrotnego uwierzytelniania, która jest wywoływana na początku obsługi każdego żądania klienta HTTP.

Procedura wywołania zwrotnego udostępnia serwerowi HTTP NetX nazwę użytkownika, hasło i ciągi dotyczące realm skojarzone z zasobem oraz zwraca typ wymaganego uwierzytelniania. Jeśli dla zasobu nie jest wymagane żadne uwierzytelnianie, wywołanie zwrotne uwierzytelniania powinno zwrócić wartość **NX_HTTP_DONT_AUTHENTICATE**. W przeciwnym razie, jeśli dla określonego zasobu jest wymagane uwierzytelnianie podstawowe, procedura powinna zwrócić **NX_HTTP_BASIC_AUTHENTICATE**. I na koniec, jeśli wymagane jest uwierzytelnianie szyfrowane MD5, procedura wywołania zwrotnego powinna zwrócić **NX_HTTP_DIGEST_AUTHENTICATE**. Jeśli żadne uwierzytelnianie nie jest wymagane dla żadnego zasobu dostarczonego przez serwer HTTP, wywołanie zwrotne nie jest potrzebne i można uzyskać wskaźnik NULL do wywołania tworzenia serwera HTTP.

Format procedury wywołania zwrotnego uwierzytelniania aplikacji jest bardzo prosty i jest zdefiniowany poniżej:

```c
UINT nx_http_server_authentication_check(NX_HTTP_SERVER *server_ptr,
                                          UINT request_type, CHAR *resource,
                                          CHAR **name, CHAR **password,
                                          CHAR **realm);
```
Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr | Znaczenie |
| --------- | --------|
| *request_type* | Określa żądanie klienta HTTP, prawidłowe żądania są zdefiniowane jako: <br/> **NX_HTTP_SERVER_GET_REQUEST**<br/>**NX_HTTP_SERVER_POST_REQUEST**<br/>**NX_HTTP_SERVER_HEAD_REQUEST**<br/>**NX_HTTP_SERVER_PUT_REQUEST**<br/>**NX_HTTP_SERVER_DELETE_REQUEST** |
| *zasób* | Żądany zasób. |
| *Nazwa* | Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika. |
| *hasło* | Miejsce docelowe wskaźnika do wymaganego hasła. |
| *Obszaru* | Miejsce docelowe wskaźnika do realm dla tego uwierzytelniania. |

Wartość zwracana przez procedurę uwierzytelniania określa, czy wymagane jest uwierzytelnianie. ```name, password, and realm``` Wskaźniki nie są używane, **jeśli NX_HTTP_DONT_AUTHENTICATE** zwracana przez procedurę wywołania zwrotnego uwierzytelniania. W przeciwnym razie deweloper serwera HTTP musi upewnić się, **że** NX_HTTP_MAX_USERNAME i **NX_HTTP_MAX_PASSWORD** zdefiniowane w pliku *nxd_http_server.h* są wystarczająco duże dla nazwy użytkownika i hasła określonego w wywołaniu zwrotym uwierzytelniania. Oba te znaki mają domyślnie rozmiar 20 znaków.

## <a name="http-invalid-usernamepassword-callback"></a>Nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła HTTP

Opcjonalne nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła na serwerze HTTP NetX jest wywoływane, jeśli serwer HTTP otrzyma nieprawidłową kombinację nazwy użytkownika i hasła w żądaniu klienta. Jeśli aplikacja serwera HTTP zarejestruje wywołanie zwrotne na serwerze HTTP, zostanie ono wywołane w przypadku niepowodzenia uwierzytelniania podstawowego lub szyfrowanego w usługach *nx_http_server_get_process*, *nx_http_server_put_process* lub nx_http_server_delete_process *.*

Aby zarejestrować wywołanie zwrotne na serwerze HTTP, następująca usługa jest zdefiniowana w serwerze HTTP NetX Duo.

```c
UINT nx_http_server_invalid_userpassword_notify_set(
                   NX_HTTP_SERVER *http_server_ptr,
                   UINT *invalid_username_password_callback)
                            (CHAR *resource,
                             NXD_ADDRESS *client_nxd_address,
                             UINT request_type))
```

Typy żądań są zdefiniowane w następujący sposób:
 - **NX_HTTP_SERVER_GET_REQUEST**
 - **NX_HTTP_SERVER_POST_REQUEST**
 - **NX_HTTP_SERVER_HEAD_REQUEST**
 - **NX_HTTP_SERVER_PUT_REQUEST**
 - **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>Wywołanie zwrotne nagłówka daty HTTP Insert GMT

Na serwerze HTTP NetX Duo istnieje opcjonalne wywołanie zwrotne, które umożliwia wstawienie nagłówka daty do komunikatów odpowiedzi. To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie put lub get

Na serwerze HTTP NetX Duo istnieje opcjonalne wywołanie zwrotne, które umożliwia wstawienie nagłówka daty do komunikatów odpowiedzi. To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie put lub get

Aby zarejestrować wywołanie zwrotne daty GMT na serwerze HTTP, następująca usługa jest zdefiniowana na serwerze HTTP NetX Duo.

```c
UINT  _nx_http_server_gmt_callback_set(
                    NX_HTTP_SERVER *server_ptr,
                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date)
```

Typ NX_HTTP_SERVER_DATE danych jest zdefiniowany w następujący sposób:

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT          nx_http_server_year;           /* Year                 */
    UCHAR           nx_http_server_month;          /* Month                */
    UCHAR           nx_http_server_day;            /* Day                  */
    UCHAR           nx_http_server_hour;           /* Hour              */
    UCHAR           nx_http_server_minute;         /* Minute               */
    UCHAR           nx_http_server_second;         /* Second               */
    UCHAR           nx_http_server_weekday;        /* Weekday              */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>Uzyskiwanie wywołania zwrotnego informacji o pamięci podręcznej HTTP

Serwer HTTP ma wywołanie zwrotne, aby zażądać maksymalnego wieku i daty z aplikacji HTTP dla określonego zasobu. Te informacje służą do określenia, czy serwer HTTP wysyła całą stronę w odpowiedzi na żądanie Get klienta. Jeśli w żądaniu klienta nie znaleziono daty "jeśli została zmodyfikowana od" lub nie jest ona dopasowana do daty ostatniej modyfikacji zwróconej przez wywołanie zwrotne get pamięci podręcznej, wysyłana jest cała strona.

Aby zarejestrować wywołanie zwrotne na serwerze HTTP, zdefiniowano następującą usługę:

```c
UINT  _nx_http_server_cache_info_callback_set(
                              NX_HTTP_SERVER *server_ptr,
                              UINT (*cache_info_get)
                                    (CHAR *, UINT *, NX_HTTP_SERVER_DATE *))
```

## <a name="http-multipart-support"></a>Obsługa wieloczęściowego protokołu HTTP

Protokół MIME (Multipurpose Internet Mail Extensions) pierwotnie był przeznaczony dla protokołu SMTP, ale jego zastosowanie rozpowszechniło się na protokół HTTP. MiME umożliwia wiadomościom zawieranie komunikatów mieszanych (np. obraz/jpg i tekst/zwykły) w ramach tego samego komunikatu. Serwer HTTP NetX Duo dodał usługi do określania typu zawartości w komunikatach HTTP zawierających mime z klienta. Aby włączyć obsługę wieloczęściową protokołu HTTP i korzystać z tych usług, NX_HTTP_MULTIPART_ENABLE **musi** być zdefiniowana opcja konfiguracji.

```c
UINT  nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       UCHAR *entity_header_buffer,
                                       ULONG buffer_size);

UINT  nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_pptr,
                                        ULONG *available_offset,
                                        ULONG *available_length)
```

Aby uzyskać więcej informacji na temat korzystania z tych usług, zobacz ich opis w rozdziale 3 "Opis usług HTTP".

## <a name="http-multi-thread-support"></a>Obsługa wielu wątków PROTOKOŁU HTTP

Usługi klienta HTTP NetX mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta HTTP powinny być wykonywane kolejno z tego samego wątku.

## <a name="http-rfcs"></a>RFC HTTP

Protokół HTTP NetX jest zgodny ze standardem RFC1945 "Hypertext Transfer Protocol/1.0, RFC 2581 "Tcp Congestion Control", RFC 1122 "Requirements for Internet Hosts" i powiązanymi RFC.
