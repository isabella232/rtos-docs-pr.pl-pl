---
title: Rozdział 3 — Opis usług HTTP
description: Ten rozdział zawiera opis wszystkich usług HTTP sieci Web NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30168ad5a564b0f4c0a8c999046c5103385f4f90
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822890"
---
# <a name="chapter-3---description-of-http-services"></a>Rozdział 3 — Opis usług HTTP

Ten rozdział zawiera opis wszystkich usług HTTP sieci Web NetX (wymienionych poniżej) w kolejności alfabetycznej.

> [!NOTE]
> W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

## <a name="http-and-https-client-api"></a>Interfejs API klienta protokołu HTTP i HTTPS

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

Otwórz gniazdo zwykłego tekstu na serwerze HTTP dla żądań niestandardowych

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa otwiera gniazdo TCP w postaci zwykłego tekstu do serwera HTTP, ale nie wysyła żadnych żądań. Żądania są tworzone za pomocą n *x_web_http_client_request_initialize ()* i wysyłane przy użyciu *nx_web_http_client_request_send ()*. Niestandardowe nagłówki HTTP można dodać do żądania przy użyciu *nx_web_http_client_request_header_add ()*.

Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby niestandardowych nagłówków do żądania. **Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.**

> [!NOTE]
> Metody nx_web_http_client_ * _start są udostępniane dla wygody (np. *nx_web_http_client_get_start*()) i obsługują generowanie żądań i połączenie gniazda. Możesz użyć tych usług zamiast *nx_web_http_client_connect ()* i powiązanych procedur, jeśli nie potrzebujesz niestandardowych nagłówków HTTP w żądaniach.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **server_IP** Adres IP zdalnego serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP (np. 80 dla protokołu HTTP).
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na operacje w sieci. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się połączenie gniazda TCP.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_WEB_HTTP_NOT_READY (0x3000A) inne żądanie jest już w toku.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

Tworzenie wystąpienia klienta HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu IP. Wystąpienia klienta można użyć w przypadku protokołu HTTP lub HTTPS. Zobacz usługi *nx_web_http_client_connect ()* i *nx_web_http_client_secure_connect ()* , aby uzyskać więcej informacji na temat uruchamiania wystąpienia http lub https. Zapoznaj się również z interfejsem API dla * nx_web_http_client_get_ * *, *nx_web_http_client_put_ * *, *nx_web_http_client_post_** dla prostych wywołań metod get, PUT i post.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **CLIENT_NAME** Nazwa wystąpienia klienta HTTP.
- **ip_ptr** Wskaźnik na wystąpienie adresu IP.
- **pool_ptr** Wskaźnik do domyślnej puli pakietów. Należy pamiętać, że pakiety w tej puli muszą mieć wystarczającą ilość ładunku, aby obsłużyć pełny nagłówek odpowiedzi. Jest on definiowany przez *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* w *nx_web_http_client. h*.
- **window_size** Rozmiar okna odbierania gniazda TCP klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta http
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów
- NX_WEB_HTTP_POOL_ERROR (0x30009) Nieprawidłowy rozmiar ładunku w puli pakietów

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

Usuwanie wystąpienia klienta HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa poprzednio utworzone wystąpienie klienta HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie klienta http
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

Rozpocznij żądanie HTTP DELETE w postaci zwykłego tekstu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ten interfejs API jest przestarzały. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_delete_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

Rozpocznij żądanie HTTP DELETE w postaci zwykłego tekstu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_delete_start* (). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

Rozpocznij zaszyfrowane żądanie usunięcia protokołu HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_delete_secure_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu. zasób musi być zakończony wartością NULL.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

Rozpocznij zaszyfrowane żądanie usunięcia protokołu HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_delete_secure_start*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu. zasób musi być zakończony wartością NULL.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

Uruchamianie żądania HTTP GET w postaci zwykłego tekstu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_get_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

Uruchamianie żądania HTTP GET w postaci zwykłego tekstu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_get_start*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

Uruchamianie szyfrowanego żądania GET HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_get_secure_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

Uruchamianie szyfrowanego żądania GET HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_secure_start*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

Uruchom żądanie HTTP z NAGŁÓWKIem zwykłego tekstu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_head_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

Uruchom żądanie HTTP z NAGŁÓWKIem zwykłego tekstu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_head_start*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

Rozpocznij zaszyfrowane żądanie HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* , aby pobrać odpowiedź serwera odpowiadającą żądanym treści zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_head_secure_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

Rozpocznij zaszyfrowane żądanie HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* , aby pobrać odpowiedź serwera odpowiadającą żądanym treści zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_head_secure_start*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http
- Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

Przydziel pakiet HTTP (S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje przydzielić pakiet dla klienta HTTP (S).

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **packet_ptr** Wskaźnik do przydzielony pakiet.
- **WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xffffffff)
  - **limit czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przydzielenie pakietu **NX_SUCCESS** (0x00)
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.
- Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

Rozpocznij żądanie HTTP POST

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_web_http_client_put_packet* , aby wysłać zawartość zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_post_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

Rozpocznij żądanie HTTP POST

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_web_http_client_put_packet* , aby wysłać zawartość zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_post_start* (). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

Rozpocznij zaszyfrowane żądanie POST HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_post_secure_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_post_secure_start_extended

Rozpocznij zaszyfrowane żądanie POST HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_post_secure_start* (). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

Rozpocznij żądanie HTTP PUT

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_put_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_put_start_extended

Rozpocznij żądanie HTTP PUT

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda jest dla **zwykłego tekstu** http.

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_put_start* (). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

Uruchamianie szyfrowanego żądania PUT HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_put_secure_start_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

Uruchamianie szyfrowanego żądania PUT HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_put_secure_start*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **SERVER_PORT** Port TCP na zdalnym serwerze HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

Wyślij następny pakiet danych zasobu

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP w przypadku operacji PUT i POST. Należy zauważyć, że ta procedura powinna być wywoływana kilkukrotnie do momentu, aż łączna długość wysłanych pakietów jest równa "total_bytes" określonej w poprzednim wywołaniu *nx_web_http_client_put_start ()* lub *nx_web_http_client_post_start ()* (lub w odpowiednich bezpiecznych wersjach).

Ta usługa sprawdza także odpowiedź z serwera w przypadku wystąpienia problemu podczas ustanawiania połączenia HTTP (lub HTTPS).

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał pakiet klienta http.
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0X3000E) otrzymał kod błędu serwera * *
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) Nieprawidłowa długość pakietu
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło
- Serwer **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) reaguje przed UKOŃCZeniem umieszczania
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- Pakiet NX_INVALID_PACKET (0x12) jest za mały dla nagłówka TCP
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

Ustaw przemieszczenie fragmentaryczne dla żądania HTTP (S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa używa kodowania fragmentarycznego transferu do wysyłania niestandardowego żądania HTTP (S) do serwera określonego w wywołaniu *nx_web_http_client_connect ()* lub *nx_web_http_client_secure_connect ()* , który wcześniej ustanowił połączenie gniazda z hostem zdalnym.

> [!NOTE]
> Jeśli aplikacja używa kodowania fragmentarycznego transferu do wysyłania pakietu danych żądania, musi wywołać tę usługę po wywołaniu *nx_web_http_client_request_packet_allocate*() i przed wywołaniem *nx_web_http_client_reqeust_packet_send* ().

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **chunk_size** Rozmiar fragmentu danych w oktetach.
- **packet_ptr** Wskaźnik pakietów danych żądania HTTP (S).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił fragment.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT, "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

Dodawanie niestandardowego nagłówka do niestandardowego żądania HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa dodaje niestandardowy nagłówek (w postaci nazwy pola i wartości) do niestandardowego żądania HTTP utworzonego przy użyciu n *x_web_http_client_request_initialize ()*.

Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby niestandardowych nagłówków do żądania. **Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.**

> [!NOTE]
> \*Metody _start nx_web_http_client_ są udostępniane dla wygody. Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_initialize ())* do tworzenia i wysyłania żądań HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **field_name** Ciąg nazwy pola (np. "Content-Type").
- **name_length** Długość ciągu nazwy pola w bajtach.
- **field_value** Ciąg wartości pola (np. "application/octet-stream").
- **value_length** Długość ciągu wartości w bajtach.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie dodawania nagłówka do żądania.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

Inicjowanie niestandardowego żądania HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa tworzy niestandardowe żądanie HTTP i kojarzy je z wystąpieniem klienta HTTP. W przeciwieństwie do prostszej *nx_web_http_client_get_start ()* (wraz z METODAmi umieszczania, post i skojarzonych bezpiecznych wersji tego interfejsu API) żądanie niestandardowe nie jest wysyłane do momentu wywołania usługi *nx_web_http_client_request_send ()* .

Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu usługi ***nx_web_http_client_request_header_add ()*** . Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.

> [!NOTE]
> \*Metody _start nx_web_http_client_ są udostępniane dla wygody. Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_send ())* do tworzenia i wysyłania żądań HTTP.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_client_request_initialize_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **Metoda** Metoda żądania HTTP, która ma zostać użyta. Opcje są zdefiniowane w następujący sposób:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **zasób** Nazwa przesyłanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **input_size** Rozmiar danych wejściowych dla operacji PUT i POST. Przekazanie wartości 0 dla innych operacji.
- **transfer_encoding_trunked** Parametr zastrzeżony dla przyszłej obsługi transferu z przekazywaniem.
- **Nazwa użytkownika** Nazwa użytkownika chronionych zasobów.
- **hasło** Hasło do chronionych zasobów.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zainicjowano żądanie.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_WEB_HTTP_METHOD_ERROR (0x30014) brakuje niektórych wymaganych informacji (np. input_size do PUT lub POST).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

Inicjowanie niestandardowego żądania HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa tworzy niestandardowe żądanie HTTP i kojarzy je z wystąpieniem klienta HTTP. W przeciwieństwie do prostszej *nx_web_http_client_get_start ()* (wraz z METODAmi umieszczania, post i skojarzonych bezpiecznych wersji tego interfejsu API) żądanie niestandardowe nie jest wysyłane do momentu wywołania usługi *nx_web_http_client_request_send ()* .

Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu usługi ***nx_web_http_client_request_header_add ()*** . Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.

> [!NOTE]
> \*Metody _start nx_web_http_client_ są udostępniane dla wygody. Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_send ())* do tworzenia i wysyłania żądań HTTP.

Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_client_request_initialize*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **Metoda** Metoda żądania HTTP, która ma zostać użyta. Opcje są zdefiniowane w następujący sposób:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **zasób** Nazwa przesyłanego zasobu.
- **resource_length** Długość ciągu żądanego zasobu.
- **host** Ciąg zakończony znakiem null nazwy domeny serwera. Ten ciąg jest przesyłany w polu nagłówka hosta HTTP. Ciąg hosta nie może mieć wartości NULL.
- **host_length** Długość ciągu hosta.
- **input_size** Rozmiar danych wejściowych dla operacji PUT i POST. Przekazanie wartości 0 dla innych operacji.
- **transfer_encoding_trunked** Parametr zastrzeżony dla przyszłej obsługi transferu z przekazywaniem.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość ciągu hasła na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zainicjowano żądanie.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_WEB_HTTP_METHOD_ERROR (0x30014) brakuje niektórych wymaganych informacji (np. input_size do PUT lub POST).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

Wyślij pakiet danych żądania HTTP (S) do serwera zdalnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła niestandardowy pakiet danych żądania HTTP (S) utworzony za pomocą *nx_web_http_client_request_packet_allocate* () na serwer określony w wywołaniu *nx_web_http_client_connect ()* lub *nx_web_http_client_secure_connect (*), który wcześniej ustanowił połączenie gniazda z hostem zdalnym.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **packet_ptr** Wskaźnik pakietów danych żądania HTTP (S).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie pakietu danych żądania.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

Wyślij niestandardowe żądanie HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła niestandardowe żądanie HTTP utworzone za pomocą *nx_web_http_client_request_initialize ()* na serwer określony w *nx_web_http_client_connect ()* lub *nx_web_http_client_secure_connect ()* , z których wcześniej nawiązano połączenie gniazda z hostem zdalnym.

Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu usługi ***nx_web_http_client_request_header_add ()*** . Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.

> [!NOTE]
> \*Metody _start nx_web_http_client_ są udostępniane dla wygody. Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_initialize ())* do tworzenia i wysyłania żądań HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie żądania.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

Pobierz następny pakiet danych zasobów

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>Opis

Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie wywołanie *nx_web_http_client_get_start ()* lub *nx_web_http_client_get_secure_start ()* . Kolejne wywołania tej procedury należy wprowadzać do momentu otrzymania stanu powrotu NX_WEB_HTTP_GET_DONE.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **packet_ptr** Miejsce docelowe dla wskaźnika pakietu zawierającego częściową zawartość zasobu.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie pakietu klienta http.
- **NX_WEB_HTTP_GET_DONE** (0X3000C) http Get pakiet klienta jest gotowy
- Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest w trybie pobierania.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) Nieprawidłowa długość pakietu
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) kod stanu HTTP 100 Kontynuuj
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) kod stanu HTTP 101 Przełączanie protokołów
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) kod stanu HTTP 201 został utworzony
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) kod stanu HTTP 202 zaakceptowany
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) kod stanu HTTP 203 informacje nieautorytatywne
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) kod stanu HTTP 204 Brak zawartości
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) kod stanu HTTP 205 Resetowanie zawartości
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) kod stanu HTTP 206 częściowa zawartość
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) kod stanu HTTP 300 z wieloma opcjami
- Kod stanu HTTP **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) 301 został trwale przeniesiony
- Znaleziono kod stanu HTTP **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) 302
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) kod stanu HTTP 303 Zobacz inne
- Kod stanu HTTP **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) 304 nie został zmodyfikowany
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) kod stanu HTTP 305 Użyj serwera proxy
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0X30028) http kod stanu 307 tymczasowe przekierowanie
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) kod stanu HTTP 400 Nieprawidłowe żądanie
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) kod stanu HTTP 401 nieautoryzowany
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) kod stanu HTTP 402 wymagana opłata
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) kod stanu HTTP 403 zabroniony
- Nie znaleziono kodu stanu HTTP **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) 404
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) kod stanu HTTP 405 Metoda niedozwolona
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) kod stanu HTTP 406 nie jest akceptowalny
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) kod stanu HTTP 407 wymagane uwierzytelnianie serwera proxy
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) kod stanu HTTP 408 upłynął limit czasu żądania
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) kod stanu HTTP 409 konflikt
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) kod stanu HTTP 410 został usunięty
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) kod stanu HTTP 411 wymagana długość
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) kod stanu HTTP 412 niepowodzenie warunku wstępnego
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) kod stanu HTTP 413 jednostka żądania jest zbyt duża
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) kod stanu HTTP 414 adres URL żądania jest zbyt duży
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) kod stanu HTTP 415 nieobsługiwany typ nośnika
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) kod stanu HTTP 416 żądany zakres nie niewłaściwego
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) kod stanu HTTP 417 nie powiodło się
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) kod stanu HTTP 500 wewnętrzny błąd serwera
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) kod stanu HTTP 501 nie został zaimplementowany
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) kod stanu HTTP 502 zła Brama
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) kod stanu HTTP 503 Usługa niedostępna
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) kod stanu HTTP 504 upłynął limit czasu bramy
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) kod stanu HTTP 505 wersja http nieobsługiwana
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

Ustawianie wywołania zwrotnego do wywołania podczas przetwarzania nagłówków HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Opis

Ta usługa przypisuje wywołanie zwrotne, które zostanie wywołane za każdym razem, gdy klient HTTP NetX sieci Web przetwarza nagłówek HTTP w odpowiedzi przychodzącej ze zdalnego serwera HTTP. Wywołanie zwrotne jest wywoływane jednokrotnie dla każdego nagłówka w odpowiedzi w miarę ich przetwarzania. Wywołanie zwrotne umożliwia aplikacji klienckiej HTTP uzyskanie dostępu do każdego z nagłówków odpowiedzi serwera HTTP w celu podjęcia wszelkich żądanych akcji poza podstawowym przetwarzaniem, które NetX klienta HTTP sieci Web.

### <a name="input-parameters"></a>Parametry wejściowe

**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.

**callback_function** Wywołanie zwrotne zostało wywołane podczas przetwarzania nagłówka odpowiedzi. Wywołanie zwrotne jest wywoływane z nazwą pola i wartością jako ciągi (i ich długości). Na przykład nagłówek "Content-Length: 100" spowoduje, że funkcja zostanie wywołana z "Content-Length" dla *field_name* i ciągu "100" dla *field_value*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne przypisanie wywołania zwrotnego.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

Otwieranie sesji protokołu TLS na serwerze HTTPS dla żądań niestandardowych

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.

Ta usługa otwiera zabezpieczoną sesję protokołu TLS z serwerem HTTPS, ale nie wysyła żadnych żądań. Żądania są tworzone za pomocą n *x_web_http_client_request_initialize ()* i wysyłane przy użyciu *nx_web_http_client_request_send ()*. Niestandardowe nagłówki HTTP można dodać do żądania przy użyciu *nx_web_http_client_request_header_add ()*.

Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby niestandardowych nagłówków do żądania. **Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.**

> [!NOTE]
> \*Metody _start nx_web_http_client_ są udostępniane dla wygody. Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_initialize ())* do tworzenia i wysyłania żądań HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **server_IP** Adres IP zdalnego serwera HTTPS.
- **SERVER_PORT** Port na zdalnym serwerze HTTPS (np. 443 dla protokołu HTTPS).
- **tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS. Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się połączenie sesji TLS.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_WEB_HTTP_NOT_READY (0x3000A) inne żądanie jest już w toku.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>Interfejs API serwera HTTP i HTTPS

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

Ustawianie wywołania zwrotnego do pobierania adresu URL maksymalny wiek i Data

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołana usługa wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **cache_info_get** Wskaźnik do wywołania zwrotnego
- **max_age** Wskaźnik do maksymalnego wieku zasobu
- **dane** Zwrócono wskaźnik do daty ostatniej modyfikacji.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja

### <a name="example"></a>Przykład

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

Wyślij dane z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Opis

Ta usługa wysyła dane z dostarczonego pakietu z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie. Ponadto procedura wywołania zwrotnego musi zwracać stan NX_WEB_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **data_ptr** Wskaźnik do danych do wysłania.
- **data_length** Liczba bajtów do wysłania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie przesłał dane serwera
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Opis

Ta usługa jest używana w procedurze wywołania zwrotnego serwera HTTP (S) (zdefiniowanej przez aplikację) w celu wygenerowania nagłówka odpowiedzi HTTP. Procedura wywołania zwrotnego serwera jest wywoływana, gdy serwer HTTP odpowiada na żądania GET, PUT i DELETE klienta wymagające odpowiedzi HTTP. Ta funkcja pobiera informacje o odpowiedzi z aplikacji i generuje odpowiedni nagłówek odpowiedzi. Zobacz nx_web_http_server_create usługi *()* , aby uzyskać więcej informacji na temat procedury wywołania zwrotnego żądania serwera.

Ten interfejs API jest przestarzały. Deweloperzy są zachęcani do korzystania z *nx_web_http_server_callback_generate_response_header_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości
- **status_code** Wskazuje stan zasobu. Przykłady:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **CONTENT_LENGTH** Rozmiar zawartości w bajtach
- **Content_Type** Typ HTTP np. "tekst/zwykły"
- **additional_header** Wskaźnik na dodatkowy tekst nagłówka

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie UTWORZYŁ nagłówek HTML
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>Opis

Ta usługa jest używana w procedurze wywołania zwrotnego serwera HTTP (S) (zdefiniowanej przez aplikację) w celu wygenerowania nagłówka odpowiedzi HTTP. Procedura wywołania zwrotnego serwera jest wywoływana, gdy serwer HTTP odpowiada na żądania GET, PUT i DELETE klienta wymagające odpowiedzi HTTP. Ta funkcja pobiera informacje o odpowiedzi z aplikacji i generuje odpowiedni nagłówek odpowiedzi. Zobacz nx_web_http_server_create usługi *()* , aby uzyskać więcej informacji na temat procedury wywołania zwrotnego żądania serwera.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości
- **status_code** Wskazuje stan zasobu. Przykłady:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** Długość ciągu kodu stanu
- **CONTENT_LENGTH** Rozmiar zawartości w bajtach
- **Content_Type** Typ HTTP np. "tekst/zwykły"
- **content_type_length** Długość ciągu typu zawartości
- **additional_header** Wskaźnik na dodatkowy tekst nagłówka
- **additional_header_length** Długość dodatkowego tekstu nagłówka

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie UTWORZYŁ nagłówek HTML
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

Wyślij pakiet HTTP z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego protokołu HTTP. Serwer HTTP wyśle pakiet za pomocą _TIMEOUT_SEND NX_WEB_HTTP_SERVER. Nagłówek HTTP i dane muszą być dołączone do pakietu. Jeśli stan powrotu wskazuje na błąd, aplikacja HTTP musi zwolnić pakiet.

Wywołanie zwrotne powinno zwracać NX_WEB_HTTP_CALLBACK_COMPLETED.

Zobacz *nx_web_http_server_callback_generate_response_header ()* , aby zapoznać się z bardziej szczegółowym przykładem.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku kontroli serwera HTTP
- **packet_ptr** Wskaźnik do pakietu do wysłania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał pakiet serwera http
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

Wyślij odpowiedź z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Opis

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_WEB_HTTP_CALLBACK_COMPLETED.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do korzystania z *nx_web_http_server_callback_response_send_extended ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.
- **informacje** Wskaźnik na ciąg informacji.
- **additional_info** Wskaźnik na ciąg informacji dodatkowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera http

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

Wyślij odpowiedź z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>Opis

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_WEB_HTTP_CALLBACK_COMPLETED.

Ciągi nagłówka, informacje i additional_info muszą być zakończone znakiem NULL i długość każdego ciągu jest zgodna z długością określoną na liście argumentów.

Ta usługa zastępuje *nx_web_http_server_callback_response_send*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.
- **header_length** Długość ciągu nagłówka odpowiedzi.
- **informacje** Wskaźnik na ciąg informacji.
- **Information_length** Długość ciągu informacji.
- **additional_info** Wskaźnik na ciąg informacji dodatkowych.
- **additional_info_length** Długość ciągu informacji dodatkowych.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera http

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

Pobierz zawartość z żądania

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP. Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.
- **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
- **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
- **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
- **actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http
- Błąd wewnętrzny serwera HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- 0x30007 — koniec zawartości żądania **NX_WEB_HTTP_DATA_END**
- **NX_WEB_HTTP_TIMEOUT** (0x30001) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu zawartości
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

Pobierz zawartość z żądania/obsługuje długość zawartości o zerowej długości

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Opis

Ta usługa jest niemal identyczna z *nx_web_http_server_content_get ()*; próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP. Jednak obsługuje żądania o długości wartości zerowej (puste żądanie) jako prawidłowe żądanie. Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).

Ta usługa zastępuje *nx_web_http_server_content_get*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.
- **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
- **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
- **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
- **actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie zawartości http
- Błąd wewnętrzny serwera HTTP **NX_WEB_HTTP_ERROR** (0x30000)
- 0x30007 — koniec zawartości żądania **NX_WEB_HTTP_DATA_END**
- **NX_WEB_HTTP_TIMEOUT** (0x30001) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

Pobierz długość zawartości w żądaniu/obsługuje długość zawartości równą zero

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. Wartość zwracana wskazuje stan pomyślnego ukończenia i rzeczywista wartość długości jest zwracana w wskaźniku wejściowym content_length. Jeśli nie ma żadnej zawartości HTTP o długości zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wskaźnik wejściowy wskazuje prawidłową długość (zero). Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Parametry wejściowe

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.
- **CONTENT_LENGTH** Wskaźnik do wartości pobranej z pola długości zawartości

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie długości zawartości serwera http
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) niewłaściwy format nagłówka http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

Tworzenie wystąpienia serwera HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera HTTP, które działa w kontekście jego własnego wątku ThreadX. Opcjonalne *authentication_check* i *request_notify* procedury wywołania zwrotnego aplikacji umożliwiają kontrolę oprogramowania aplikacji przez podstawowe operacje serwera http.

Ta usługa służy do tworzenia zarówno serwerów HTTP ze zwykłym tekstem, jak i serwerów HTTPS zabezpieczonych za pomocą protokołu TLS. Aby włączyć protokół HTTPS przy użyciu protokołu TLS, zobacz *nx_web_http_server_secure_configure usługi ()*.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **http_server_name** Wskaźnik na nazwę serwera HTTP.
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **SERVER_PORT** Port nasłuchiwania protokołu TCP dla wystąpienia serwera.
- **media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.
- **stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.
- **stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.
- **authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji. Jeśli jest określony, ta procedura jest wywoływana dla każdego żądania klienta HTTP. Jeśli ten parametr ma wartość NULL, uwierzytelnianie nie zostanie wykonane. Ten parametr jest przestarzały. Wywołaj *nx_web_http_server_authenticate_check_set*().
- **request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji. Jeśli jest określony, ta procedura jest wywoływana przed przetworzeniem żądania przez serwer HTTP. Pozwala to na aktualizowanie nazwy zasobu lub pól w ramach zasobu przed ukończeniem żądania klienta HTTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera http.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.
- Ładunek pakietu NX_WEB_HTTP_POOL_ERROR (0x30009) puli nie jest wystarczająco duży, aby można było zawierać pełne żądanie HTTP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

Usuwanie wystąpienia serwera HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa poprzednio utworzone wystąpienie serwera HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie serwera http
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

Pobierz lokalizację i długość danych jednostki

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Opis

Ta usługa określa lokalizację początkową danych w bieżącej jednostce wieloczęściowej w odebranych komunikatach klienta i długość danych bez uwzględniania ciągu granicy. Wewnętrznie serwer HTTP aktualizuje własne przesunięcia, aby można było ponownie wywołać tę funkcję na tym samym datagramie klienta dla komunikatów z wieloma jednostkami. Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.

Należy pamiętać, że NX_WEB_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi. Należy również zauważyć, że aplikacja nie powinna zwolnić pakietu wskazywanego przez packet_pptr. Jest to wykonywane wewnętrznie przez serwer HTTP.

Aby uzyskać więcej informacji, zobacz *nx_web_http_server_get_entity_header ()* .

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do serwera HTTP
- **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Zwróć uwagę, że aplikacja nie powinna wydać tego pakietu
- **available_offset** Wskaźnik do przesunięcia danych jednostki ze wskaźnika dołączania do pakietu
- **available_length** Wskaźnik do długości danych jednostki

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie pobrała rozmiar i lokalizację zawartości jednostki
- Zawartość **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) dla wewnętrznych znaczników wieloczęściowych serwera http została już znaleziona
- Błąd wewnętrzny serwera HTTP NX_WEB_HTTP_ERROR (0x30000)
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

Pobierz zawartość nagłówka jednostki

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera nagłówek jednostki do określonego buforu. Serwer HTTP wewnętrznie aktualizuje własne wskaźniki, aby znaleźć następną wieloczęściową jednostkę w datagramie klienta z wieloma nagłówkami jednostek. Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.

Należy pamiętać, że NX_WEB_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi. Należy również pamiętać, że aplikacja nie powinna zwolnić pakietu wskazywanego przez packet_pptr.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do serwera HTTP
- **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Zwróć uwagę, że aplikacja nie powinna wydać tego pakietu
- **entity_header_buffer** Wskaźnik do lokalizacji do zapisania nagłówka jednostki
- **buffer_size** Rozmiar buforu wejściowego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie pobrał nagłówek jednostki
- Nie znaleziono pola nagłówka jednostki **NX_WEB_HTTP_NOT_FOUND** (0x30006)
- Czas **NX_WEB_HTTP_TIMEOUT** (0x30001), który utracił ważność następnego pakietu dla komunikatu klienta wielopakietowego
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi
- Wewnętrzny błąd HTTP NX_WEB_HTTP_ERROR (0x30000)

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

Ustaw wywołanie zwrotne, aby uzyskać datę i godzinę GMT

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne, aby uzyskać datę i godzinę GMT z wcześniej utworzonym serwerem HTTP. Ta usługa jest wywoływana z serwerem HTTP tworzy nagłówek w odpowiedziach serwera HTTP dla klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do serwera HTTP
- **gmt_get** Wskaźnik do wywołania zwrotnego GMT
- **Data** Wskaźnik do pobranej daty

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

Ustawianie wywołania zwrotnego do obsługi nieprawidłowego użytkownika/hasła

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne wywoływane po odebraniu nieprawidłowej nazwy użytkownika i hasła do żądania GET, Put lub DELETE klienta w ramach uwierzytelniania szyfrowanego lub podstawowego. Należy wcześniej utworzyć serwer HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do serwera HTTP
- **invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/przekazania wywołania zwrotnego
- **zasób** Wskaźnik do zasobu określonego przez klienta
- **client_address** Adres klienta
- **request_type** Wskazuje typ żądania klienta. Może:
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

Ustaw dodatkowe mapy MIME dla HTML

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Opis

Ta usługa umożliwia deweloperowi aplikacji protokołu HTTP Dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczonych przez serwer HTTP sieci Web NetX. Zobacz *nx_web_http_server_get_type ()* , aby zapoznać się z listą zdefiniowanych typów.

Po odebraniu żądania klienta, np. żądanie GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu preferencyjnego dodatkowego zestawu mapowań MIME i jeśli nie jest zgodny, szuka dopasowania w domyślnej mapie MIME serwera HTTP. Jeśli nie zostanie znalezione dopasowanie, typ MIME domyślnie przyjmuje wartość "text/zwykły".

Jeśli funkcja powiadamiania o żądaniu jest zarejestrowana na serwerze HTTP, wywołanie zwrotne powiadomienia o żądaniu może wywołać *nx_web_http_server_type_get_extended ()* w celu przeanalizowania typu pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **mime_maps** Wskaźnik do tablicy mapy MIME
- **mime_map_num** Liczba mapowań MIME w tablicy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne Ustawianie mapy MIME serwera http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

Przydziel pakiet HTTP (S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje przydzielić pakiet dla serwera HTTP (S).

Należy pamiętać, że jeśli kolejny interfejs API serwera NetX lub HTTP używający tego pakietu jako danych wejściowych **nie powiedzie się**, na przykład nx_packet_data_append lub * * nx_web_http_server_callback_packet_send, aplikacja jest odpowiedzialna za wydanie pakietu. **

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik do przydzielony pakiet.
- **WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **NX_NO_WAIT** (0x00000000) wybranie NX_NO_WAIT powoduje natychmiastowe zwrócenie przez wątek wywołujący, jeśli nie można spełnić żądania.
  - **NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przydzielenie pakietu **NX_SUCCESS** (0x00)
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.
- Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

Wyodrębnij długość zawartości i ustaw wskaźnik na początek danych

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Opis

Ta usługa wyodrębnia długość zawartości z nagłówka HTTP. Aktualizuje również podany pakiet w następujący sposób: wskaźnik dołączania pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) po prostu przekazały nagłówek HTTP.

Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na odebranie następnego pakietu przy użyciu opcji oczekiwania NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Należy zauważyć, że nie należy wywoływać przed wywołaniem *nx_web_http_server_get_entity_header ()* , ponieważ modyfikuje wskaźnik dołączania pakietu poza nagłówkiem Entity.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym wskaźnikiem dołączania
- **CONTENT_LENGTH** Wskaźnik do wyodrębnienia content_length

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) znaleziono długość zawartości http i pakiet został pomyślnie zaktualizowany
- Czas **NX_WEB_HTTP_TIMEOUT** (0x30001) upłynął podczas oczekiwania na następny pakiet
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

Odbierz następny pakiet HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca następny pakiet odebrany w gnieździe serwera HTTP. Opcja oczekiwania na odebranie pakietu jest NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Należy pamiętać, że jeśli aplikacja jest odpowiedzialna za wydanie pakietu.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **packet_ptr** Wskaźnik do odebranego pakietu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie otrzymał następny pakiet http
- Czas **NX_WEB_HTTP_TIMEOUT** (0x30001) upłynął podczas oczekiwania na następny pakiet
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

Pobierz parametr z żądania

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać określony parametr HTTP URL w dostarczonym pakiecie żądania. Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_WEB_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Parametry wejściowe

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.
- **param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.
- **param_ptr** Obszar docelowy do skopiowania parametru.
- **param_size** Zwróć łączną długość danych parametru (w bajtach).
- **max_param_size** Maksymalny rozmiar obszaru docelowego parametru.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie PARAMETRU serwera http
- Nie znaleziono podanego parametru **NX_WEB_HTTP_NOT_FOUND** (0x30006)
- Parametr żądania **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) nie został poprawnie zakończony
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

Pobierz zapytanie z żądania

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać określoną kwerendę HTTP URL w dostarczonym pakiecie żądania. Jeśli żądana kwerenda HTTP nie istnieje, ta procedura zwraca stan NX_WEB_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Parametry wejściowe

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.
- **query_number** Numer logiczny parametru zaczynający się od zera od lewej do prawej na liście zapytań.
- **query_ptr** Obszar docelowy, w którym ma zostać skopiowane zapytanie.
- **query_size** Zwraca rozmiar danych zapytania (w bajtach).
- **max_query_size** Maksymalny rozmiar lokalizacji docelowej zapytania

stref.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zapytanie serwera http
- Rozmiar zapytania **NX_WEB_HTTP_FAILED** (0x30002) jest zbyt mały.
- Nie znaleziono określonego zapytania **NX_WEB_HTTP_NOT_FOUND** (0x30006)
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0X30013) brak zapytania w żądaniu klienta
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

Ustaw przemieszczenie fragmentaryczne dla odpowiedzi HTTP (S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa używa kodowania fragmentarycznego transferu do wysyłania niestandardowego pakietu danych odpowiedzi HTTP (S) utworzonego za pomocą *nx_web_http_server_response_packet_allocate*() do klienta programu.

> [!NOTE]
> Jeśli aplikacja używa kodowania fragmentarycznego transferu do wysyłania pakietu danych odpowiedzi, musi wywołać tę usługę po wywołaniu *nx_web_http_server_response_packet_allocate*() i przed wywołaniem metody *nx_web_http_server_callback_packet_send*().

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **chunk_size** Rozmiar fragmentu danych w oktetach.
- **packet_ptr** Wskaźnik pakietów danych żądania HTTP (S).

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna konfiguracja zestawu **NX_SUCCESS** (0x00).
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

Konfigurowanie serwera HTTP do korzystania z protokołu TLS dla bezpiecznego protokołu HTTPS

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>Opis

Ta usługa konfiguruje wcześniej utworzone wystąpienie serwera HTTP sieci Web NetX w celu używania protokołu TLS do bezpiecznej komunikacji HTTPS. Parametry służą do konfigurowania wszystkich możliwych sesji protokołu TLS o identycznym stanie, tak aby każde przychodzące działanie klienta HTTPS było spójne. Liczba sesji TLS jest kontrolowana przy użyciu makra NX_WEB_HTTP_SESSION_MAX.

Tabela procedur kryptograficznych (tabela ciphersuite) jest współdzielona między wszystkimi sesjami TLS, ponieważ zawiera ona wskaźniki funkcji.

Bufory odzestawów metadanych i pakietów są rozdzielone równomiernie między wszystkimi sesjami TLS. Jeśli rozmiar buforu nie jest równo widoczny w liczbie sesji, pozostała część będzie niedostępna.

Certyfikat tożsamości przekazywania jest używany przez wszystkie sesje. Podczas operacji TLS certyfikat tożsamości serwera jest odczytywany tylko z tego miejsca, dlatego kopie nie są konieczne dla każdej sesji.

Zaufane certyfikaty są dodawane do każdej sesji TLS na serwerze HTTPS. Są one używane do uwierzytelniania certyfikatów klientów, które są automatycznie włączane, gdy jest udostępniane zdalne miejsce na certyfikat.

Zdalna tablica i bufor certyfikatów są domyślnie udostępniane między wszystkimi sesjami protokołu TLS. Certyfikaty zdalne są używane do uwierzytelniania certyfikatów klientów, które są automatycznie włączane, gdy liczba certyfikatów zdalnych jest różna od zera. Ze względu na to, że bufor udostępnia niektóre sesje, może być blokowany podczas walidacji certyfikatu.

Aby wyłączyć uwierzytelnianie certyfikatu klienta, należy przekazać NX_NULL dla parametru remote_certificates i wartość 0 dla parametru remote_certs_num.

Wartości zwracane będą zawierać wszelkie kody błędów protokołu TLS, które wynikają z problemów w konfiguracji sesji TLS.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.
- **crypto_table** Wskaźnik na tabelę protokołu TLS ciphersuite.
- **metadata_buffer** Wskaźnik do bufora metadanych kryptograficznych.
- **metadata_size** Rozmiar buforu metadanych kryptograficznych.
- **packet_buffer** Bufor ponownego zestawu pakietów TLS.
- **packet_buffer** Rozmiar buforu pakietów TLS — powinien być równy (<żądany rozmiar buforu TLS * NX_WEB_HTTP_SESSION_MAX).
- **identity_certificate** Certyfikat tożsamości serwera TLS — będzie używany dla wszystkich sesji serwera HTTPS.
- **trusted_certificates** Wskaźnik do tablicy obiektów NX_SECURE_X509_CERT, służący do weryfikowania przychodzących certyfikatów klienta w przypadku włączenia uwierzytelniania certyfikatu klienta przez przekazanie wartości innej niż zero dla parametru *remote_certs_num* .
- **trusted_certs_num** Liczba zaufanych certyfikatów w tablicy *trusted_certificates* .
- **remote_certificates** Wskaźnik do tablicy obiektów NX_SECURE_X509_CERT, używany do przychodzących certyfikatów klienta.
- **remote_certs_num** Liczba certyfikatów zdalnych. Powinna być maksymalną liczbą oczekiwanych certyfikatów od klientów. Uwierzytelnianie certyfikatu klienta jest włączane automatycznie, gdy wartość jest różna od zera.
- **remote_certificate_buffer** Bufor zawierający przychodzące certyfikaty zdalne od klientów, jeśli jest włączone uwierzytelnianie certyfikatu klienta. remote_cert_buffer_size rozmiar buforu certyfikatów zdalnych. Wartość musi być równa (<maksymalny oczekiwany rozmiar certyfikatu \* remote_certs_num).


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.
- **NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) otrzymany typ komunikatu TLS jest niepoprawny.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.
- Przetwarzanie komunikatu **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) podczas UZGADNIANIA protokołu TLS nie powiodło się.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) komunikat przychodzący nie powiódł się podczas sprawdzania skrótu Mac.
- **NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) nie można wysłać podstawowego gniazda TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) komunikat przychodzący miał nieprawidłową długość pola.
- **NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) odebrana wiadomość ChangeCipherSpec jest niepoprawna.
- **NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) przychodzący certyfikat TLS nie nadaje się do identyfikacji serwera zdalnego protokołu TLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) szyfrowanie klucza publicznego dostarczone przez hosta zdalnego nie jest obsługiwane.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) host zdalny nie wskazywał ciphersuites, które są obsługiwane przez stos NetX Secure TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrany komunikat TLS miał nieznaną wersję protokołu TLS w jego nagłówku.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) odebrany komunikat TLS miał znaną, ale nieobsługiwaną wersję protokołu TLS w jego nagłówku.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się wewnętrzna alokacja pakietu TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny dostarczył nieprawidłowy certyfikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.
- **NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

Uruchom serwer HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzone wystąpienie serwera HTTP lub HTTPS.

Serwery HTTPS korzystają z tego samego interfejsu API co HTTP. Aby włączyć protokół HTTPS przy użyciu protokołu TLS na serwerze HTTP, zobacz *nx_web_http_server_secure_configure usługi ().*

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie serwera http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

Zatrzymaj serwer HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa poprzednio utworzone wystąpienie serwera HTTP. Ta procedura powinna być wywoływana przed usunięciem wystąpienia serwera HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zatrzymanie serwera http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

Wyodrębnij typ pliku z żądania HTTP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Opis

> [!NOTE]
> Ta usługa jest przestarzała. Zaleca się, aby użytkownicy korzystali z usługi *nx_web_http_server_type_get_extended ()*.

Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w *string_size* z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL. Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX Web są następujące:

- HTML text/html
- htm text/html
- tekst txt/zwykły
- obraz GIF/GIF
- obraz JPG/JPEG
- ikona obrazu ICO/x

Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika. Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_web_http_server_mime_maps_addtional_set ()* .

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **Nazwa** Wskaźnik do buforu do przeszukania
- **http_type_string** Wskaźnik do wyodrębnionego ciągu typu HTML
- **string_size** Wskaźnik zwracający wyekstrahowaną długość ciągu typu HTML.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna Ekstrakcja typu **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) domyślnie zwrócony "tekst/zwykły".

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

Wyodrębnij typ pliku z żądania HTTP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Opis

Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w *string_size* z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL. Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX Web są następujące:

- HTML text/html
- htm text/html
- tekst txt/zwykły
- obraz GIF/GIF
- obraz JPG/JPEG
- ikona obrazu ICO/x

Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika. Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_web_http_server_mime_maps_addtional_set ()* .

Ta usługa zastępuje *nx_web_http_server_type_get*(). Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **Nazwa** Wskaźnik do buforu do przeszukania
- **name_length** Długość nazwy
- **http_type_string** Wskaźnik do wyodrębnionego ciągu typu HTML
- **http_type_string_max_size** Rozmiar buforu http_type_string
- **string_size** Wskaźnik zwracający wyodrębniony ciąg typu HTML

Długość.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna Ekstrakcja typu **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) domyślnie zwrócony "tekst/zwykły".

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne wywoływane po wykonaniu uwierzytelniania szyfrowanego.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **digest_authenticate_callback** Wskaźnik do wywołania zwrotnego uwierzytelniania szyfrowanego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_NOT_SUPPORTED (0x4B) uwierzytelnianie szyfrowane nie jest włączone

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne wywoływane, gdy jest przeprowadzane sprawdzanie uwierzytelniania.

### <a name="input-parameters"></a>Parametry wejściowe

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **authenticate_check_externded** Wskaźnik do uwierzytelniania — wywołanie zwrotne

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
