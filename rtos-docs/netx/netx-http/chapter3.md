---
title: Rozdział 3 — Opis usług HTTP NetX
description: Ten rozdział zawiera opis wszystkich usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822615"
---
# <a name="chapter-3---description-of-netx-http-services"></a>Rozdział 3 — Opis usług HTTP NetX

Ten rozdział zawiera opis wszystkich usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

**Usługi klienta HTTP:**

- nx_http_client_create *utworzyć wystąpienia klienta http*
- nx_http_client_delete *usunąć wystąpienia klienta http*
- nx_http_client_get_start *uruchomić żądania HTTP GET*
- nx_http_client_get_start_extended *uruchomić żądania HTTP GET*
- nx_http_client_get_packet *Pobierz następny pakiet danych zasobów*
- nx_http_client_put_start *uruchomić żądanie HTTP Put*
- nx_http_client_put_start_extended *uruchomić żądanie HTTP Put*
- nx_http_client_put_packet *Wyślij następny pakiet danych zasobu*
- *nx_http_client_set_connect_port* *zmienić portu w celu nawiązania połączenia z serwerem HTTP*

**Usługi serwera HTTP:**

- nx_http_server_cache_info_callback_set *ustawić wywołania zwrotnego, aby pobrać wiek i datę ostatniej modyfikacji określonego adresu URL*
- nx_http_server_callback_data_send *wysyłać danych http z funkcji wywołania zwrotnego*
- nx_http_server_callback_generate_response_header *utworzyć nagłówka odpowiedzi w funkcjach wywołania zwrotnego*
- nx_http_server_callback_generate_response_header_extended *utworzyć nagłówka odpowiedzi w funkcjach wywołania zwrotnego*
- nx_http_server_callback_packet_send *wysłać pakietu http z wywołania zwrotnego http*
- nx_http_server_callback_response_send *wysyłanie odpowiedzi z funkcji wywołania zwrotnego*
- nx_http_server_callback_response_send_extended *wysyłanie odpowiedzi z funkcji wywołania zwrotnego*
- nx_http_server_content_get *pobrać zawartości z żądania*
- nx_http_server_content_get_extended *pobrać zawartości z żądania; obsługuje puste (zerowe długości zawartości)*
- nx_http_server_content_length_get *uzyskać długość zawartości w żądaniu*
- nx_http_server_content_length_get_extended *uzyskać długość zawartości w żądaniu; obsługuje puste (zerowe długości zawartości)*
- nx_http_server_create *utworzyć wystąpienia serwera http*
- nx_http_server_delete *usunąć wystąpienia serwera http*
- nx_http_server_get_entity_content *zwracanie rozmiaru i lokalizacji zawartości jednostki w adresie URL*
- nx_http_server_get_entity_header *Wyodrębnij nagłówka jednostki adresów URL do określonego buforu*
- nx_http_server_gmt_callback_set *ustawić wywołania zwrotnego, aby pobrać datę i godzinę GMT*
- nx_http_server_invalid_userpassword_notify_set *ustawić wywołania zwrotnego dla momentu odebrania nieprawidłowej nazwy użytkownika i hasła w żądaniu klienta*
- nx_http_server_mime_maps_additional_set *zdefiniować dodatkowe mapy MIME dla HTML*
- nx_http_server_packet_content_find *Wyodrębnij długość zawartości w nagłówku HTTP i ustaw wskaźnik na początek danych zawartości*
- nx_http_server_packet_get *odebrać pakiet klienta bezpośrednio*
- nx_http_server_param_get *uzyskać parametru z żądania*
- nx_http_server_query_get *uzyskać zapytania z żądania*
- nx_http_server_start *uruchomić serwer http*
- nx_http_server_stop *zatrzymać serwer http*
- nx_http_server_type_get *Wyodrębnij typu http, np. Text/zwykły z nagłówka*
- nx_http_server_type_get_extended *Wyodrębnij typu http, np. Text/zwykły z nagłówka*
- nx_http_server_digest_authenticate_notify_set *Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego*
- nx_http_server_authentication_check_set *Ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania*

## <a name="nx_http_client_create"></a>nx_http_client_create

### <a name="create-an-http-client-instance"></a>Tworzenie wystąpienia klienta HTTP

**Prototype**

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

**Opis**

Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu IP.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **CLIENT_NAME** Nazwa wystąpienia klienta HTTP.
- **ip_ptr** Wskaźnik na wystąpienie adresu IP.
- **pool_ptr** Wskaźnik do domyślnej puli pakietów. Należy pamiętać, że pakiety w tej puli muszą mieć wystarczającą ilość ładunku, aby obsłużyć pełny nagłówek odpowiedzi. Jest on definiowany przez NX_HTTP_CLIENT_MIN_PACKET_SIZE w *nx_http_client. h*.
- **window_size** Rozmiar okna odbierania gniazda TCP klienta.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta http
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów
- NX_HTTP_POOL_ERROR (0xE9) Nieprawidłowy rozmiar ładunku w puli pakietów

**Dozwolone z**

Inicjalizacja, wątki

**Przykład**

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

### <a name="delete-an-http-client-instance"></a>Usuwanie wystąpienia klienta HTTP

**Prototype**

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

**Opis**

Ta usługa usuwa poprzednio utworzone wystąpienie klienta HTTP.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne usunięcie klienta http
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

### <a name="start-an-http-get-request"></a>Rozpocznij żądanie HTTP GET

**Prototype**

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

**Opis**

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_http_client_get_start_extended ()*

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **input_ptr** Wskaźnik na dodatkowe dane żądania GET. Jest to opcjonalne. Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.
- **input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez input_ptr.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
-**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xffffffff)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http
- Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)
- Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy
- **NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

**Dozwolone z**

Wątki

**Przykład**

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

### <a name="start-an-http-get-request"></a>Rozpocznij żądanie HTTP GET

**Prototype**

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

**Opis**

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.

Ta usługa zastępuje *nx_http_client_get_start ()*. Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu adresu URL dla żądanego zasobu.
- **input_ptr** Wskaźnik na dodatkowe dane żądania GET. Jest to opcjonalne. Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.
- **input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez input_ptr.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość opcjonalnego hasła do uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xffffffff)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http
- Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)
- Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy
- **NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem HTTP.
- **NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

**Dozwolone z**

Wątki

**Przykład**
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

### <a name="get-next-resource-data-packet"></a>Pobierz następny pakiet danych zasobów

**Prototype**

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

**Opis**

Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie wywołanie *nx_http_client_get_start* . Kolejne wywołania tej procedury należy wprowadzać do momentu otrzymania stanu powrotu NX_HTTP_GET_DONE.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **packet_ptr** Miejsce docelowe dla wskaźnika pakietu zawierającego częściową zawartość zasobu.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na pobieranie pakietu przez klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xffffffff)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne pobieranie pakietu przez klienta http.
- **NX_HTTP_GET_DONE** (0XEC) http Get pakiet klienta jest gotowy
- Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest w trybie pobierania.
- **NX_HTTP_BAD_PACKET_LENGTH** (0XED) Nieprawidłowa długość pakietu
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

### <a name="start-an-http-put-request"></a>Rozpocznij żądanie HTTP PUT 

**Prototype**

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

**Opis**

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP o podanym adresie IP. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_http_client_put_packet* , aby faktycznie wysyłać zawartość zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_http_client_put_start_extended ()*.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xffffffff)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put
- **NX_HTTP_USERNAME_TOO_LONG**
- **(0xF1) nazwa użytkownika jest zbyt duża dla buforu**
- Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

### <a name="start-an-http-put-request"></a>Rozpocznij żądanie HTTP PUT

**Prototype**

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

**Opis**

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP o podanym adresie IP. Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_http_client_put_packet* , aby faktycznie wysyłać zawartość zasobów do serwera http.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.

Ta usługa zastępuje *nx_http_client_put_start ()*. Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **IP_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.
- **resource_length** Długość ciągu adresu URL dla zasobu do wysłania na serwer.
- **Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.
- **username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.
- **hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.
- **password_length** Długość opcjonalnego hasła do uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanego zasobu. Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xffffffff)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put
- **NX_HTTP_USERNAME_TOO_LONG** (0XF1) nazwa użytkownika jest zbyt duża dla buforu
- Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

### <a name="send-next-resource-data-packet"></a>Wyślij następny pakiet danych zasobu

**Prototype**

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

**Opis**

Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP. Należy zauważyć, że ta procedura powinna być wywoływana kilkukrotnie do momentu, aż łączna długość wysłanych pakietów jest równa "total_bytes" określonej w poprzednim wywołaniu *nx_http_client_put_start ()* .

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać wewnętrznie na przetwarzanie pakietu klienta HTTP PUT. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xffffffff)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.<br /> Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie wysłał pakiet klienta http.
- Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy
- **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0XEE) otrzymał kod błędu serwera * *-**NX_HTTP_BAD_PACKET_LENGTH** (0xed) Nieprawidłowa długość pakietu
- **NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło
- Serwer **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) reaguje przed UKOŃCZeniem umieszczania
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- Pakiet NX_INVALID_PACKET (0x12) jest za mały dla nagłówka TCP
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

### <a name="set-the-connection-port-to-the-server"></a>Ustaw port połączenia na serwer

**Prototype**

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

**Opis**

Ta usługa zmienia port połączenia podczas nawiązywania połączenia z serwerem HTTP do określonego portu w czasie wykonywania. W przeciwnym razie wartość domyślna portu połączenia to 80. Ta wartość musi być wywoływana przed *nx_http_client_get_start*() i *nx_http_client_put_start*(), np. gdy klient http nawiązuje połączenie z serwerem.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku kontroli klienta HTTP.
- **port** Port służący do nawiązywania połączenia z serwerem.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie zmienił port połączenia
- Port **NX_INVALID_PORT** (0x46) przekracza wartość maksymalną (0xFFFF) lub równą zero.
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki, Inicjalizacja

**Przykład**

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a>Ustawianie wywołania zwrotnego do pobierania adresu URL maksymalny wiek i Data

**Prototype**

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

**Opis**

Ta usługa ustawia wywołana usługa wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **cache_info_get** Wskaźnik do wywołania zwrotnego
- **max_age** Wskaźnik do maksymalnego wieku zasobu
- **dane** Zwrócono wskaźnik do daty ostatniej modyfikacji.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Inicjalizacja

**Przykład**

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a>nx_http_server_callback_data_send

### <a name="send-data-from-callback-function"></a>Wyślij dane z funkcji wywołania zwrotnego

**Prototype**

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

**Opis**

Ta usługa wysyła dane z dostarczonego pakietu z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie. Ponadto procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **data_ptr** Wskaźnik do danych do wysłania.
- **data_length** Liczba bajtów do wysłania.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie przesłał dane serwera
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

### <a name="create-a-response-header-in-a-callback-function"></a>Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego

**Prototype**

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

**Opis**

Ta usługa wywołuje funkcję wewnętrzną _ *nx_http_server_generate_response_header* , gdy serwer http odpowiada na żądania GET, PUT i DELETE klienta. Jest ona przeznaczona do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje odpowiedź na klienta.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nxd_http_server_callback_generate_response_header_extended ()*.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości
- **status_code** Wskazuje stan zasobu. Przykłady:
- **NX_HTTP_STATUS_OK**
- **NX_HTTP_STATUS_MODIFIED**
- **NX_HTTP_STATUS_INTERNAL_ERROR**
- **CONTENT_LENGTH** Rozmiar zawartości w bajtach
- **Content_Type** Typ HTTP np. "tekst/zwykły"
- **additional_header** Wskaźnik na dodatkowy tekst nagłówka

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie UTWORZYŁ nagłówek HTML
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
            nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

/* Now send the packet! */
   status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
            resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
/* Let HTTP server know the response has been sent. */
   return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a>nx_http_server_callback_generate_response_header_extended

### <a name="create-a-response-header-in-a-callback-function"></a>Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego

**Prototype**

```c
UINT nx_http_server_callback_generate_response_header_extended(
     NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr,
     CHAR *status_code, UINT status_code_length,
     UINT content_length,
     CHAR *content_type, UINT content_type_length,
     CHAR *additional_header,
     UINT additional_header_length);
```

**Opis**

Ta usługa wywołuje funkcję wewnętrzną _ *nx_http_server_generate_response_header ()* , gdy serwer http odpowiada na żądania GET, PUT i DELETE klienta. Jest ona przeznaczona do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje odpowiedź na klienta.

Ta usługa zastępuje *nx_http_server_callback_generate_response_header ()*. Ta wersja dostarcza dodatkowe informacje o długości do funkcji wywołania zwrotnego.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości
- **status_code** Wskazuje stan zasobu. Przykłady:
  - **NX_HTTP_STATUS_OK**
  - **NX_HTTP_STATUS_MODIFIED**
  - **NX_HTTP_STATUS_INTERNAL_ERROR**
- **status_code** Długość kodu stanu
- **CONTENT_LENGTH** Rozmiar zawartości w bajtach
- **Content_Type** Typ HTTP np. "tekst/zwykły"
- **content_type_length** Długość typu HTTP
- **additional_header** Wskaźnik na dodatkowy tekst nagłówka
- **additional_header_length** Długość dodatkowego tekstu nagłówka

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie utworzył nagłówek
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
                       nx_http_server_request_resource, temp_string,
                       sizeof(temp_string));

    /* Null terminate the string. */
       temp_string[temp] = 0;

    /* Now build a response header with server status is OK and no additional header
      info. */
      status = nx_http_server_callback_generate_response_header_extended(
               http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
               sizeof(NX_HTTP_STATUS_OK) - 1, length,
               temp_string, string_length, NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
       status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                length, server_ptr ->
                nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
       status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                   resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
    /* Let HTTP server know the response has been sent. */
       return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_packet_send"></a>nx_http_server_callback_packet_send

### <a name="send-an-http-packet-from-callback-function"></a>Wyślij pakiet HTTP z funkcji wywołania zwrotnego

**Prototype**

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

**Opis**

Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego protokołu HTTP. Serwer HTTP wyśle pakiet za pomocą _TIMEOUT_SEND NX_HTTP_SERVER. Nagłówek HTTP i dane muszą być dołączone do pakietu. Jeśli stan powrotu wskazuje na błąd, aplikacja HTTP musi zwolnić pakiet.

Wywołanie zwrotne powinno zwracać NX_HTTP_CALLBACK_COMPLETED.

Zobacz *nx_http_server_callback_generate_response_header ()* , aby zapoznać się z bardziej szczegółowym przykładem.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku kontroli serwera HTTP
- **packet_ptr** Wskaźnik do pakietu do wysłania

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie wysłał pakiet serwera http
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

### <a name="send-response-from-callback-function"></a>Wyślij odpowiedź z funkcji wywołania zwrotnego

**Prototype**

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

**Opis**

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_HTTP_CALLBACK_COMPLETED.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_http_server_callback_response_send_extended ().*

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.
- **informacje** Wskaźnik na ciąg informacji.
- **additional_info** Wskaźnik na ciąg informacji dodatkowych.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera http

**Dozwolone z**

Wątki

**Przykład**

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
       {

            /* In this example, we will complete the GET processing with
               a resource not found response. */
               nx_http_server_callback_response_send(server_ptr,
                                                    "HTTP/1.0 404 ",
                                                    "NetX HTTP Server unable to find
                                                    file: ", resource);
            /* Return completion status. */
               return(NX_HTTP_CALLBACK_COMPLETED);
        }
        return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a>nx_http_server_callback_response_send_extended

### <a name="send-response-from-callback-function"></a>Wyślij odpowiedź z funkcji wywołania zwrotnego

**Prototype**

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

**Opis**

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_HTTP_CALLBACK_COMPLETED.

Ta usługa zastępuje *nx_http_server_callback_response_send ().* Ta wersja pobiera informacje o długości jako argument wejściowy.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.
- **header_length** Długość ciągu nagłówka odpowiedzi.
- **informacje** Wskaźnik na ciąg informacji.
- **information_length** Długość ciągu informacji.
- **additional_info** Wskaźnik na ciąg informacji dodatkowych.
- **additional_info_length** Długość ciągu informacji dodatkowych.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera

**Dozwolone z**

Wątki

**Przykład**

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a>nx_http_server_content_get

### <a name="get-content-from-the-request"></a>Pobierz zawartość z żądania

**Prototype**

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

**Opis**

Ta usługa próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP. Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do nx_http_server_content_get_extended ().

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.
- **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
- **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
- **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
- **actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http
- Błąd wewnętrzny serwera HTTP **NX_HTTP_ERROR** (wartość 0xE0)
- 0xE7 — koniec zawartości żądania **NX_HTTP_DATA_END**
- **NX_HTTP_TIMEOUT** (0xE1) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu zawartości
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a>Pobierz zawartość z żądania/obsługuje długość zawartości o zerowej długości

**Prototype**

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

**Opis**

Ta usługa jest niemal identyczna z *nx_http_server_content_get ()*; próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP. Jednak obsługuje żądania o długości wartości zerowej (puste żądanie) jako prawidłowe żądanie. Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).

Ta usługa zastępuje *nx_http_server_content_get ().* Ta wersja wymaga od wywołującego podania dodatkowych informacji o długości.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.
- **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
- **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
- **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
- **actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne pobieranie zawartości http
- Błąd wewnętrzny serwera HTTP **NX_HTTP_ERROR** (wartość 0xE0)
- 0xE7 — koniec zawartości żądania **NX_HTTP_DATA_END**
- **NX_HTTP_TIMEOUT** (0xE1) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

### <a name="get-length-of-content-in-the-request"></a>Pobierz długość zawartości w żądaniu

**Prototype**

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
**Opis**

Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. W przypadku braku zawartości HTTP Ta procedura zwraca wartość zero. Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do nx_http_server_content_length_get_extended ().

**Parametry wejściowe**

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.

**Wartości zwracane**

- **długość zawartości** W przypadku błędu zwracana jest wartość zero.

**Dozwolone z**

Wątki

**Przykład**

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a>Pobierz długość zawartości w żądaniu/obsługuje długość zawartości równą zero

**Prototype**

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

**Opis**

Ta usługa jest podobna do *nx_http_server_content_length_get ()*; próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. Jednak wartość zwracana wskazuje stan pomyślnego ukończenia, a rzeczywista wartość długości jest zwracana w wskaźniku wejściowym content_length. Jeśli nie ma żadnej zawartości HTTP o długości zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wskaźnik wejściowy wskazuje prawidłową długość (zero). Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).

Ta usługa zastępuje *nx_http_server_content_length_get*().

**Parametry wejściowe**

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.
- **CONTENT_LENGTH** Wskaźnik do wartości pobranej z pola długości zawartości

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http
- **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) niewłaściwy format nagłówka http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

### <a name="create-an-http-server-instance"></a>Tworzenie wystąpienia serwera HTTP

**Prototype**

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
     CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
     VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
     UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, CHAR **name,
     CHAR **password, CHAR **realm),
     UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

**Opis**

Ta usługa tworzy wystąpienie serwera HTTP, które działa w kontekście jego własnego wątku ThreadX. Opcjonalne *authentication_check* i *request_notify* procedury wywołania zwrotnego aplikacji umożliwiają kontrolę oprogramowania aplikacji przez podstawowe operacje serwera http.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **http_server_name** Wskaźnik na nazwę serwera HTTP.
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.
- **stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.
- **stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.
- **authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji. Jeśli jest określony, ta procedura jest wywoływana dla każdego żądania klienta HTTP. Jeśli ten parametr ma wartość NULL, żadne uwierzytelnianie nie zostanie wykonane.
- **request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji. Jeśli jest określony, ta procedura jest wywoływana przed przetworzeniem żądania przez serwer HTTP. Pozwala to na aktualizowanie nazwy zasobu lub pól w ramach zasobu przed ukończeniem żądania klienta HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera http.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.
- Ładunek pakietu NX_HTTP_POOL_ERROR (0xE9) puli nie jest wystarczająco duży, aby można było zawierać pełne żądanie HTTP.

**Dozwolone z**

Inicjalizacja, wątki

**Przykład**

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

### <a name="delete-an-http-server-instance"></a>Usuwanie wystąpienia serwera HTTP

**Prototype**

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

**Opis**

Ta usługa usuwa poprzednio utworzone wystąpienie serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne usunięcie serwera http
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

### <a name="retrieve-the-location-and-length-of-entity-data"></a>Pobierz lokalizację i długość danych jednostki

**Prototype**

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

**Opis**

Ta usługa określa lokalizację początkową danych w bieżącej jednostce wieloczęściowej w odebranych komunikatach klienta i długość danych bez uwzględniania ciągu granicy. Serwer HTTP wewnętrznie aktualizuje własne przesunięcia, aby można było ponownie wywołać tę funkcję na tym samym datagramie klienta dla komunikatów z wieloma jednostkami. Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.

Należy pamiętać, że NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.

Aby uzyskać więcej informacji, zobacz *nx_http_server_get_entity_header* .

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.
- **available_offset** Wskaźnik do przesunięcia danych jednostki ze wskaźnika dołączania do pakietu
- **available_length** Wskaźnik do długości danych jednostki

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie pobrała rozmiar i lokalizację zawartości jednostki
- Zawartość **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) dla wewnętrznych znaczników wieloczęściowych serwera http została już znaleziona
- Błąd wewnętrzny serwera HTTP NX_HTTP_ERROR (wartość 0xE0)
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

### <a name="retrieve-the-contents-of-entity-header"></a>Pobierz zawartość nagłówka jednostki

**Prototype**

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

**Opis**

Ta usługa pobiera nagłówek jednostki do określonego buforu. Serwer HTTP wewnętrznie aktualizuje własne wskaźniki, aby znaleźć następną wieloczęściową jednostkę w datagramie klienta z wieloma nagłówkami jednostek. Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.

Należy pamiętać, że NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.
- **entity_header_buffer** Wskaźnik do lokalizacji do zapisania nagłówka jednostki
- **buffer_size** Rozmiar buforu wejściowego

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie pobrało nagłówek jednostki
- **NX_HTTP_NOT_FOUND (0xE6)** Nie znaleziono pola nagłówka jednostki
- **NX_HTTP_TIMEOUT (0xE1)** Czas, który upłynął do odebrania następnego pakietu dla komunikatu klienta wielopakietowego 
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi
- Wewnętrzny błąd HTTP NX_HTTP_ERROR (wartość 0xE0)

**Dozwolone z**

Wątki

**Przykład**

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

/* Process multipart data. */
if(request_type == NX_HTTP_SERVER_POST_REQUEST)
{

    /* Get the content header. */
    while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                          sizeof(buffer)) == NX_SUCCESS)
    {

        /* Header obtained successfully. Get the content data location. */
        while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                               &length) == NX_SUCCESS)
        {

            /* Write content data to buffer. */
            nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
            buffer[length] = 0;
        }
    }
    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
             &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a>Ustaw wywołanie zwrotne, aby uzyskać datę i godzinę GMT

**Prototype**

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

**Opis**

Ta usługa ustawia wywołanie zwrotne, aby uzyskać datę i godzinę GMT z wcześniej utworzonym serwerem HTTP. Ta usługa jest wywoływana z serwerem HTTP tworzy nagłówek w odpowiedziach serwera HTTP dla klienta.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **gmt_get** Wskaźnik do wywołania zwrotnego GMT
- **Data** Wskaźnik do pobranej daty

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.

**Dozwolone z**

Wątki

**Przykład**

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a>Ustaw wywołanie zwrotne w celu obsługi nieprawidłowego użytkownika/hasła

**Prototype**

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

**Opis**

Ta usługa ustawia wywołanie zwrotne wywoływane po odebraniu nieprawidłowej nazwy użytkownika i hasła do żądania GET, Put lub DELETE klienta w ramach uwierzytelniania szyfrowanego lub podstawowego. Należy wcześniej utworzyć serwer HTTP.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/przekazania wywołania zwrotnego
- **zasób** Wskaźnik do zasobu określonego przez klienta
- **client_address** Adres klienta
- **request_type** Wskazuje typ żądania klienta. Może:
  - NX_HTTP_SERVER_GET_REQUEST
  - NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST
  - NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

### <a name="set-additional-mime-maps-for-html"></a>Ustaw dodatkowe mapy MIME dla HTML 

**Prototype**

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

**Opis**

Ta usługa umożliwia deweloperowi aplikacji protokołu HTTP Dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczonych przez NetX serwer HTTP (zobacz *nx_http_server_get_type* dla listy zdefiniowanych typów).

Po odebraniu żądania klienta, np. żądanie GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu preferencyjnego dodatkowego zestawu mapowań MIME i jeśli nie jest zgodny, szuka dopasowania w domyślnej mapie MIME serwera HTTP. Jeśli nie zostanie znalezione dopasowanie, typ MIME domyślnie przyjmuje wartość "text/zwykły".

Jeśli na serwerze HTTP zarejestrowano funkcję powiadamiania o żądaniu, wywołanie zwrotne powiadomienia o żądaniu może wywołać *nx_http_server_type_get* , aby przeanalizować typ pliku.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **mime_maps** Wskaźnik do tablicy mapy MIME
- **mime_map_num** Liczba mapowań MIME w tablicy

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne Ustawianie mapy MIME serwera http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Inicjalizacja, wątki

**Przykład**

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a>Wyodrębnij długość zawartości i ustaw wskaźnik na początek danych

**Prototype**

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

**Opis**

Ta usługa wyodrębnia długość zawartości z nagłówka HTTP. Aktualizuje również podany pakiet w następujący sposób: wskaźnik dołączania pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) po prostu przekazały nagłówek HTTP.

Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na odebranie następnego pakietu przy użyciu opcji oczekiwania NX_HTTP_SERVER_TIMEOUT_RECEIVE.

Należy zauważyć, że nie należy wywoływać przed wywołaniem *nx_http_server_get_entity_header ()* , ponieważ modyfikuje wskaźnik poprzedź przed nagłówkiem jednostki.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym wskaźnikiem dołączania
- **CONTENT_LENGTH** Wskaźnik do wyodrębnienia content_length

**Wartości zwracane**

- **NX_SUCCESS** (0x00) znaleziono długość zawartości http i pakiet został pomyślnie zaktualizowany
- Czas **NX_HTTP_TIMEOUT** (0xE1) upłynął podczas oczekiwania na następny pakiet
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

### <a name="receive-the-next-http-packet"></a>Odbierz następny pakiet HTTP

**Prototype**

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

**Opis**

Ta usługa zwraca następny pakiet odebrany w gnieździe serwera HTTP. Opcja oczekiwania na odebranie pakietu jest NX_HTTP_SERVER_TIMEOUT_RECEIVE.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **packet_ptr** Wskaźnik do odebranego pakietu

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie otrzymał następny pakiet http
- Czas **NX_HTTP_TIMEOUT** (0xE1) upłynął podczas oczekiwania na następny pakiet
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Wątki

**Przykład**

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

### <a name="get-parameter-from-the-request"></a>Pobierz parametr z żądania

**Prototype**

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

**Opis**

Ta usługa próbuje pobrać określony parametr HTTP URL w dostarczonym pakiecie żądania. Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_http_server_create ()*).

**Parametry wejściowe**

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.
- **param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.
- **param_ptr** Obszar docelowy do skopiowania parametru.
- **max_param_size** Maksymalny rozmiar obszaru docelowego parametru.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne pobieranie PARAMETRU serwera http
- Nie znaleziono podanego parametru **NX_HTTP_NOT_FOUND** (0xE6)
- Parametr żądania **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) nie został poprawnie zakończony
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

### <a name="get-query-from-the-request"></a>Pobierz zapytanie z żądania

**Prototype**

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

**Opis**

Ta usługa próbuje pobrać określoną kwerendę HTTP URL w dostarczonym pakiecie żądania. Jeśli żądana kwerenda HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_http_server_create ()*).

**Parametry wejściowe**

- **packet_ptr** Wskaźnik na pakiet żądania klienta HTTP. Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.
- **query_number** Numer logiczny parametru zaczynający się od zera od lewej do prawej na liście zapytań.
- **query_ptr** Obszar docelowy, w którym ma zostać skopiowane zapytanie.
- **max_query_size** Maksymalny rozmiar obszaru docelowego zapytania.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne zapytanie serwera http
- Rozmiar zapytania **NX_HTTP_FAILED** (0xE2) jest zbyt mały.
- Nie znaleziono określonego zapytania **NX_HTTP_NOT_FOUND** (0xE6)
- **NX_HTTP_NO_QUERY_PARSED** (0XF2) brak zapytania w żądaniu klienta
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
nx_http_server_start

### <a name="start-the-http-server"></a>Uruchom serwer HTTP

**Prototype**

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

**Opis**

Ta usługa uruchamia poprzednio utworzone wystąpienie serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne uruchomienie serwera http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Inicjalizacja, wątki

**Przykład**

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

### <a name="stop-the-http-server"></a>Zatrzymaj serwer HTTP

**Prototype**

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

**Opis**

Ta usługa przerywa poprzednio utworzone wystąpienie serwera HTTP. Ta procedura powinna być wywoływana przed usunięciem wystąpienia serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślne zatrzymanie serwera http
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

**Dozwolone z**

Wątki

**Przykład**

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

### <a name="extract-file-type-from-client-http-request"></a>Wyodrębnij typ pliku z żądania HTTP klienta

**Prototype**

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

**Opis**

Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w zwracanej wartości z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL. Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze NetX HTTP są następujące:

- HTML text/html
- htm text/html
- tekst txt/zwykły
- obraz GIF/GIF
- obraz JPG/JPEG
- ikona obrazu ICO/x

Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika. Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_http_server_mime_maps_addtional_set ()* .

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_http_server_type_get_extended ().*

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **Nazwa** Wskaźnik do buforu do przeszukania
- **http_type_string** (wskaźnik do wyodrębnionego typu html)

**Wartości zwracane**

- **Długość ciągu w bajtach** Wartość różna od zera to sukces
- **Zero oznacza błąd**

**Dozwolone z**

Aplikacja

**Przykład**

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

Aby zapoznać się z bardziej szczegółowym przykładem, zobacz Opis

*nx_http_server_callback_generate_response_header.*

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

### <a name="extract-file-type-from-client-http-request"></a>Wyodrębnij typ pliku z żądania HTTP klienta

**Prototype**

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

**Opis**

Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w zwracanej wartości z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL. Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX Duo są następujące:

- HTML text/html
- htm text/html
- tekst txt/zwykły
- obraz GIF/GIF
- obraz JPG/JPEG
- ikona obrazu ICO/x

Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika. Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_http_server_mime_maps_addtional_set ()* .

Ta usługa zastępuje *nx_http_server_type_get ().* Ta wersja dostarcza dodatkowe informacje o długości.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **Nazwa** Wskaźnik do buforu do przeszukania
- **name_length** Długość buforu do wyszukania
- **http_type_string** (wskaźnik do wyodrębnionego typu html)
- **http_type_string_max_size**

Rozmiar buforu *http_type_string*

**Wartości zwracane**

- **Długość ciągu w bajtach** Wartość różna od zera to sukces<br />Zero oznacza błąd

**Dozwolone z**

Aplikacja

**Przykład**

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
       my_server.nx_http_server_request_resource, &resource_length,
       sizeof(my_server.nx_http_server_request_resource) - 1))
    {
        return;
    }
/* Extract the HTTP type. */
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

Aby zapoznać się z bardziej szczegółowym przykładem, zobacz Opis

*nx_http_server_callback_generate_response_header.*

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

### <a name="set-digest-authenticate-callback-function"></a>Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego

**Prototype**

```c
UINT nx_http_server_digest_authenticate_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                         CHAR *name_ptr,
                                         CHAR *realm_ptr,
                                         CHAR *password_ptr,
                                         CHAR *method,
                                         CHAR *authorization_uri,
                                         CHAR *authorization_nc,
                                         CHAR *authorization_cnonce
                                         ));
```

**Opis**

Ta usługa ustawia wywołanie zwrotne wywoływane po wykonaniu uwierzytelniania szyfrowanego.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **digest_authenticate_callback** Wskaźnik do wywołania zwrotnego uwierzytelniania szyfrowanego

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_NOT_SUPPORTED (0x4B) uwierzytelnianie szyfrowane nie jest włączone

**Dozwolone z**

Aplikacja

**Przykład**

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

### <a name="set-authentication-checking-callback-function"></a>Ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania

**Prototype**

```c
UINT nx_http_server_authentication_check_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*authentication_check_extended)(
                                          NX_HTTP_SERVER *server_ptr,
                                          UINT request_type,
                                          CHAR *resource,
                                          CHAR **name,
                                          UINT *name_length,
                                          CHAR **password,
                                          UINT *password_length,
                                          CHAR **realm,
                                          UINT *realm_length
                                          ));
```

**Opis**

Ta usługa ustawia funkcję wywołania zwrotnego sprawdzania uwierzytelniania.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **authentication_check_extended** Wskaźnik do sprawdzania uwierzytelniania aplikacji

**Wartości zwracane**

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne
- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Aplikacja

**Przykład**

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```