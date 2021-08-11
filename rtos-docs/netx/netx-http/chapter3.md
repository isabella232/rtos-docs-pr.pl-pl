---
title: Rozdział 3 — Opis usług HTTP NetX
description: Ten rozdział zawiera opis wszystkich usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: eabb455b6e21b4fe51db944a0da12afa85ee390a78db633ee670de5aadcde07b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791520"
---
# <a name="chapter-3---description-of-netx-http-services"></a>Rozdział 3 — Opis usług HTTP NetX

Ten rozdział zawiera opis wszystkich usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

**Usługi klienta HTTP:**

- nx_http_client_create tworzenie *wystąpienia klienta HTTP*
- nx_http_client_delete usuwanie *wystąpienia klienta HTTP*
- nx_http_client_get_start uruchamianie *żądania HTTP GET*
- nx_http_client_get_start_extended uruchamianie *żądania HTTP GET*
- nx_http_client_get_packet *Pobierz następny pakiet danych zasobów*
- nx_http_client_put_start uruchamianie *żądania HTTP PUT*
- nx_http_client_put_start_extended uruchamianie *żądania HTTP PUT*
- nx_http_client_put_packet Wyślij *następny pakiet danych zasobów*
- *nx_http_client_set_connect_port* *zmienić port, aby nawiązać połączenie z serwerem HTTP*

**Usługi serwera HTTP:**

- nx_http_server_cache_info_callback_set ustaw *wywołanie zwrotne, aby pobrać wiek i datę ostatniej modyfikacji określonego adresu URL*
- nx_http_server_callback_data_send Wysyłanie *danych HTTP z funkcji wywołania zwrotnego*
- nx_http_server_callback_generate_response_header tworzenie *nagłówka odpowiedzi w funkcjach wywołania zwrotnego*
- nx_http_server_callback_generate_response_header_extended tworzenie *nagłówka odpowiedzi w funkcjach wywołania zwrotnego*
- nx_http_server_callback_packet_send *wysyłanie pakietu HTTP z wywołania zwrotnego HTTP*
- nx_http_server_callback_response_send Wysyłanie *odpowiedzi z funkcji wywołania zwrotnego*
- nx_http_server_callback_response_send_extended *Wysyłanie odpowiedzi z funkcji wywołania zwrotnego*
- nx_http_server_content_get Pobierz *zawartość z żądania*
- nx_http_server_content_get_extended pobierz *zawartość z żądania; obsługuje puste żądania (zero długości zawartości)*
- nx_http_server_content_length_get *Uzyskiwanie długości zawartości w żądaniu*
- nx_http_server_content_length_get_extended *żądania pobierz długość zawartości; obsługuje puste żądania (zero długości zawartości)*
- nx_http_server_create tworzenie *wystąpienia serwera HTTP*
- nx_http_server_delete usuwanie *wystąpienia serwera HTTP*
- nx_http_server_get_entity_content *zwracany rozmiar i lokalizacja zawartości jednostki w adresie URL*
- nx_http_server_get_entity_header *wyodrębnianie nagłówka jednostki adresu URL do określonego buforu*
- nx_http_server_gmt_callback_set *ustawić wywołanie zwrotne w celu pobrania daty i godziny GMT*
- nx_http_server_invalid_userpassword_notify_set ustawić wywołanie zwrotne w przypadku odebrania nieprawidłowej nazwy użytkownika i *hasła w żądaniu klienta*
- nx_http_server_mime_maps_additional_set *Definiowanie dodatkowych map mime dla języka HTML*
- nx_http_server_packet_content_find *wyodrębnianie długości zawartości w nagłówku HTTP i ustawianie wskaźnika na początek danych zawartości*
- nx_http_server_packet_get bezpośrednio *odbierać pakiet klienta*
- nx_http_server_param_get pobierz *parametr z żądania*
- nx_http_server_query_get pobierz *zapytanie z żądania*
- nx_http_server_start *serwera HTTP*
- nx_http_server_stop *zatrzymać serwer HTTP*
- nx_http_server_type_get typu *HTTP, np. tekst/zwykły z nagłówka*
- nx_http_server_type_get_extended *typu HTTP, np. tekst/zwykły z nagłówka*
- nx_http_server_digest_authenticate_notify_set funkcji *wywołania zwrotnego uwierzytelniania szyfrowanego*
- nx_http_server_authentication_check_set *ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania*

## <a name="nx_http_client_create"></a>nx_http_client_create

### <a name="create-an-http-client-instance"></a>Tworzenie wystąpienia klienta HTTP

**Prototyp**

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

**Opis**

Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu adresu IP.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **client_name** Nazwa wystąpienia klienta HTTP.
- **ip_ptr** Wskaźnik do wystąpienia adresu IP.
- **pool_ptr** Wskaźnik do domyślnej puli pakietów. Należy pamiętać, że pakiety w tej puli muszą mieć ładunek wystarczająco duży, aby obsłużyć pełny nagłówek odpowiedzi. Jest to definiowane przez NX_HTTP_CLIENT_MIN_PACKET_SIZE w *nx_http_client.h.*
- **window_size** Rozmiar okna odbierania gniazda TCP klienta.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta HTTP
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów
- NX_HTTP_POOL_ERROR(0xE9) Nieprawidłowy rozmiar ładunku w puli pakietów

**Dozwolone z**

Inicjowanie, wątki

**Przykład**

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

### <a name="delete-an-http-client-instance"></a>Usuwanie wystąpienia klienta HTTP

**Prototyp**

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

**Opis**

Ta usługa usuwa utworzone wcześniej wystąpienie klienta HTTP.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne usunięcie klienta HTTP
- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

**Dozwolone z**

Wątki

**Przykład**

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

### <a name="start-an-http-get-request"></a>Uruchamianie żądania HTTP GET

**Prototyp**

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

**Opis**

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań do usługi *nx_http_client_get_packet* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_client_get_start_extended()*

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **ip_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **input_ptr** Wskaźnik do dodatkowych danych dla żądania GET. Jest to opcjonalne. Jeśli jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości komunikatu, a zamiast operacji GET jest używany wpis POST.
- **input_size** Liczba bajtów w opcjonalnych dodatkowych danych wejściowych wskazywanych przez input_ptr.
- **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
- **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
-**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat uruchomienia GET klienta HTTP
- **NX_HTTP_ERROR** (0xE0) Wewnętrzny błąd klienta HTTP
- **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready
- **NX_HTTP_FAILED** (0xE2) klienta HTTP komunikuje się z serwerem HTTP.
- **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

### <a name="start-an-http-get-request"></a>Uruchamianie żądania HTTP GET

**Prototyp**

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

**Opis**

Ta usługa próbuje uzyskać zasób określony przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań do usługi *nx_http_client_get_packet* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.

Ta usługa zastępuje *nx_http_client_get_start()*. Wymaga on, aby wywołujący określał długość zasobu, nazwę użytkownika i hasło.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **ip_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
- **resource_length** Długość ciągu adresu URL dla żądanego zasobu.
- **input_ptr** Wskaźnik do dodatkowych danych dla żądania GET. Jest to opcjonalne. Jeśli jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości komunikatu, a zamiast operacji GET jest używany wpis POST.
- **input_size** Liczba bajtów w opcjonalnych dodatkowych danych wejściowych wskazywanych przez input_ptr.
- **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
- **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
- **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
- **password_length** Długość opcjonalnego hasła do uwierzytelniania.
- **wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat uruchomienia GET klienta HTTP
- **NX_HTTP_ERROR** (0xE0) Wewnętrzny błąd klienta HTTP
- **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready
- **NX_HTTP_FAILED** (0xE2) klienta HTTP komunikuje się z serwerem HTTP.
- **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa i/lub hasło.
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

### <a name="get-next-resource-data-packet"></a>Uzyskiwanie następnego pakietu danych zasobów

**Prototyp**

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

**Opis**

Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie *nx_http_client_get_start* wywołania. Kolejne wywołania tej procedury powinny być dokonywane do momentu, gdy zostanie odebrany NX_HTTP_GET_DONE stan zwracany.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **packet_ptr** Miejsce docelowe wskaźnika pakietu zawierającego częściową zawartość zasobu.
- **wait_option** Określa, jak długo usługa będzie czekać na pakiet get klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie pobierz pakiet klienta HTTP.
- **NX_HTTP_GET_DONE** (0xEC) http client get packet is done
- **NX_HTTP_NOT_READY** (0xEA) HTTP Client nie jest w trybie get.
- **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Nieprawidłowa długość pakietu
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="start-an-http-put-request"></a>Uruchamianie żądania HTTP PUT 

**Prototyp**

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

**Opis**

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP pod podanym adresem IP. Jeśli ta procedura powiedzie się, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_http_client_put_packet,* aby rzeczywiście wysłać zawartość zasobu do serwera HTTP.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_client_put_start_extended()*.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **ip_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.
- **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
- **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanych zasobów. Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań do nx_http_client_put_packet *musi* być równa tej wartości.
- **wait_option** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP PUT. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT
- **NX_HTTP_USERNAME_TOO_LONG**
- **(0xF1) Nazwa użytkownika jest zbyt duża dla buforu**
- **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="start-an-http-put-request"></a>Uruchamianie żądania HTTP PUT

**Prototyp**

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

**Opis**

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP pod podanym adresem IP. Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do procedury *nx_http_client_put_packet,* aby rzeczywiście wysłać zawartość zasobu do serwera HTTP.

Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.

Ta usługa zastępuje *nx_http_client_put_start()*. Wymaga to od wywołującego określenia długości zasobu, nazwy użytkownika i hasła.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **ip_address** Adres IP serwera HTTP.
- **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.
- **resource_length** Długość ciągu adresu URL dla zasobu do wysłania do serwera.
- **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
- **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
- **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
- **password_length** Długość opcjonalnego hasła do uwierzytelniania.
- **total_bytes** Całkowita liczba bajtów wysyłanych zasobów. Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do* nx_http_client_put_packet musi być równa tej wartości.
- **wait_option** Określa, jak długo usługa będzie czekać na uruchomienie żądania PUT klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.<br />Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT
- **NX_HTTP_USERNAME_TOO_LONG** (0xF1) Nazwa użytkownika jest zbyt duża dla buforu
- **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="send-next-resource-data-packet"></a>Wyślij następny pakiet danych zasobów

**Prototyp**

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

**Opis**

Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP. Należy pamiętać, że ta procedura powinna być wywoływana powtarzalnie, dopóki łączna długość wysłanych pakietów nie będzie równa "total_bytes" określonej w poprzednim *wywołaniu nx_http_client_put_start().*

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.
- **wait_option** Określa, jak długo usługa będzie czekać wewnętrznie na przetwarzanie pakietu PUT klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.<br /> Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano pakiet klienta HTTP.
- **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready
- **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Odebrano kod błędu serwera****— NX_HTTP_BAD_PACKET_LENGTH** (0xED) Nieprawidłowa długość pakietu
- **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa i/lub Hasło
- **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) serwer odpowiada przed ukończeniem procesu PUT
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_INVALID_PACKET (0x12) Pakiet jest zbyt mały dla nagłówka TCP
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="set-the-connection-port-to-the-server"></a>Ustawianie portu połączenia na serwer

**Prototyp**

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

**Opis**

Ta usługa zmienia port połączenia podczas nawiązywania połączenia z serwerem HTTP na określonym porcie w czasie wykonywania. W przeciwnym razie port połączenia domyślnie ma wartość 80. Ta nazwa musi być wywoływana *przed nx_http_client_get_start*() i *nx_http_client_put_start*(), np. podczas połączenia klienta HTTP z serwerem.

**Parametry wejściowe**

- **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
- **port** Port do nawiązywania połączenia z serwerem.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie zmieniono port połączenia
- **NX_INVALID_PORT** (0x46) port przekracza wartość maksymalną (0xFFFF) lub jest równa zero.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

**Dozwolone z**

Wątki, inicjowanie

**Przykład**

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a>Ustawianie wywołania zwrotnego w celu pobrania maksymalnego wieku i daty adresu URL

**Prototyp**

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

**Opis**

Ta usługa ustawia wywołaną usługę wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **cache_info_get** Wskaźnik do wywołania zwrotnego
- **max_age** Wskaźnik do maksymalnego wieku zasobu
- **dane** Zwrócony wskaźnik do daty ostatniej modyfikacji.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

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

### <a name="send-data-from-callback-function"></a>Wysyłanie danych z funkcji wywołania zwrotnego

**Prototyp**

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

**Opis**

Ta usługa wysyła dane w dostarczonym pakiecie z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie. Ponadto procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **data_ptr** Wskaźnik do danych do wysłania.
- **data_length** Liczba bajtów do wysłania.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano dane serwera
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

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

**Prototyp**

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

**Opis**

Ta usługa wywołuje funkcję wewnętrzną _ *nx_http_server_generate_response_header* gdy serwer HTTP odpowiada na żądania get, put i delete klienta. Jest on przeznaczony do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje swoją odpowiedź na klienta.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nxd_http_server_callback_generate_response_header_extended()*.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_pptr** Wskaźnik wskaźnika pakietu przydzielonego do komunikatu
- **status_code** Wskazuje stan zasobu. Przykłady:
- **NX_HTTP_STATUS_OK**
- **NX_HTTP_STATUS_MODIFIED**
- **NX_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** Rozmiar zawartości w bajtach
- **content_type** Typ protokołu HTTP, np. "tekst/zwykły"
- **additional_header** Wskaźnik do dodatkowego tekstu nagłówka

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie utworzono nagłówek HTML
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

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

**Prototyp**

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

Ta usługa wywołuje funkcję wewnętrzną _ *nx_http_server_generate_response_header(),* gdy serwer HTTP odpowiada na żądania get, put i delete klienta. Jest on przeznaczony do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje swoją odpowiedź na klienta.

Ta usługa zastępuje *nx_http_server_callback_generate_response_header()*. Ta wersja dostarcza dodatkowe informacje o długości funkcji wywołania zwrotnego.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_pptr** Wskaźnik wskaźnika pakietu przydzielonego do komunikatu
- **status_code** Wskazuje stan zasobu. Przykłady:
  - **NX_HTTP_STATUS_OK**
  - **NX_HTTP_STATUS_MODIFIED**
  - **NX_HTTP_STATUS_INTERNAL_ERROR**
- **status_code** Długość kodu stanu
- **content_length** Rozmiar zawartości w bajtach
- **content_type** Typ protokołu HTTP, np. "tekst/zwykły"
- **content_type_length** Długość typu HTTP
- **additional_header** Wskaźnik do dodatkowego tekstu nagłówka
- **additional_header_length** Długość dodatkowego tekstu nagłówka

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie utworzono nagłówek
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

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

### <a name="send-an-http-packet-from-callback-function"></a>Wysyłanie pakietu HTTP z funkcji wywołania zwrotnego

**Prototyp**

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

**Opis**

Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego HTTP. Serwer HTTP wyśle pakiet z NX_HTTP_SERVER _TIMEOUT_SEND. Do pakietu należy dołączyć nagłówek HTTP i dane. Jeśli stan zwracany wskazuje błąd, aplikacja HTTP musi zwolnić pakiet.

Wywołanie zwrotne powinno zwrócić NX_HTTP_CALLBACK_COMPLETED.

Zobacz *nx_http_server_callback_generate_response_header(),* aby uzyskać bardziej szczegółowy przykład.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP
- **packet_ptr** Wskaźnik do pakietu do wysłania

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano pakiet serwera HTTP
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy

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

### <a name="send-response-from-callback-function"></a>Wysyłanie odpowiedzi z funkcji wywołania zwrotnego

**Prototyp**

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

**Opis**

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zazwyczaj używane do wysyłania odpowiedzi niestandardowych skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_server_callback_response_send_extended().*

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **nagłówek** Wskaźnik do ciągu nagłówka odpowiedzi.
- **informacje o** Wskaźnik do ciągu informacyjnego.
- **additional_info** Wskaźnik do dodatkowego ciągu informacyjnego.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano odpowiedź serwera HTTP

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

### <a name="send-response-from-callback-function"></a>Wysyłanie odpowiedzi z funkcji wywołania zwrotnego

**Prototyp**

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

**Opis**

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zazwyczaj używane do wysyłania odpowiedzi niestandardowych skojarzonych z żądaniami GET/POST. Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

Ta usługa zastępuje *nx_http_server_callback_response_send().* Ta wersja przyjmuje informacje o długości jako argument wejściowy.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **nagłówek** Wskaźnik do ciągu nagłówka odpowiedzi.
- **header_length** Długość ciągu nagłówka odpowiedzi.
- **informacje o** Wskaźnik do ciągu informacyjnego.
- **information_length** Długość ciągu informacyjnego.
- **additional_info** Wskaźnik do dodatkowego ciągu informacyjnego.
- **additional_info_length** Długość ciągu dodatkowych informacji.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie wysłano odpowiedź serwera

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

**Prototyp**

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

**Opis**

Ta usługa próbuje pobrać określoną ilość zawartości z żądania KLIENTA HTTP POST lub PUT. Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do nx_http_server_content_get_extended().

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik do pakietu żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.
- **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
- **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
- **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
- **actual_size** Wskaźnik do zmiennej docelowej, która zostanie ustawiona na rzeczywisty rozmiar kopiowanej zawartości.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie zawartości serwera HTTP
- **NX_HTTP_ERROR** (0xE0) serwera HTTP
- **NX_HTTP_DATA_END** (0xE7) Koniec żądania
- **NX_HTTP_TIMEOUT** (0xE1) serwera HTTP podczas uzyskiwania następnego pakietu zawartości
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

**Prototyp**

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

**Opis**

Ta usługa jest niemal identyczna z *nx_http_server_content_get()*; Próbuje pobrać określoną ilość zawartości z żądania KLIENTA HTTP POST lub PUT. Jednak obsługuje żądania z wartością content length o wartości zero ("puste żądanie") jako prawidłowym żądaniem. Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

Ta usługa zastępuje *nx_http_server_content_get().* Ta wersja wymaga, aby element wywołujący podał dodatkowe informacje o długości.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **packet_ptr** Wskaźnik do pakietu żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.
- **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
- **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
- **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
- **actual_size** Wskaźnik do zmiennej docelowej, która zostanie ustawiona na rzeczywisty rozmiar kopiowanej zawartości.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie zawartości HTTP
- **NX_HTTP_ERROR** (0xE0) serwera HTTP
- **NX_HTTP_DATA_END** (0xE7) Koniec żądania
- **NX_HTTP_TIMEOUT** (0xE1) serwera HTTP podczas uzyskiwania następnego pakietu
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="get-length-of-content-in-the-request"></a>Uzyskiwanie długości zawartości w żądaniu

**Prototyp**

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
**Opis**

Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. Jeśli nie ma zawartości HTTP, ta procedura zwraca wartość zero. Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do nx_http_server_content_length_get_extended().

**Parametry wejściowe**

- **packet_ptr** Wskaźnik do pakietu żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.

**Wartości zwracane**

- **długość zawartości** W przypadku błędu zwracana jest wartość zero

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

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a>Pobierz długość zawartości w żądaniu/obsługuje długość zawartości o wartości zero

**Prototyp**

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

**Opis**

Ta usługa jest podobna do *nx_http_server_content_length_get()*; próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. Jednak wartość zwracana wskazuje stan pomyślnego ukończenia, a rzeczywista wartość długości jest zwracana w wskaźniku wejściowym content_length. Jeśli nie ma zawartości HTTP/długość zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wejściowy wskaźnik wskazuje prawidłową długość (zero). Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

Ta usługa *zastępuje* nx_http_server_content_length_get ().

**Parametry wejściowe**

- **packet_ptr** Wskaźnik do pakietu żądania klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.
- **content_length** Wskaźnik do wartości pobranej z pola Długość zawartości

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie zawartości serwera HTTP
- **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Nieprawidłowy format nagłówka HTTP
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

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

**Prototyp**

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

Ta usługa tworzy wystąpienie serwera HTTP, które jest uruchamiane w kontekście własnego wątku ThreadX. Opcjonalne procedury *authentication_check* i *request_notify* wywołania zwrotnego aplikacji zapewniają kontrolę oprogramowania aplikacji nad podstawowymi operacjami serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
- **http_server_name** Wskaźnik do nazwy serwera HTTP.
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.
- **stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.
- **stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.
- **authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji. Jeśli zostanie określona, ta procedura jest wywoływana dla każdego żądania klienta HTTP. Jeśli ten parametr ma wartość NULL, uwierzytelnianie nie będzie przeprowadzane.
- **request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji. Jeśli określono, ta procedura jest wywoływana przed przetwarzaniem żądania przez serwer HTTP. Umożliwia to przekierowywanie nazwy zasobu lub zaktualizowanie pól w zasobie przed ukończeniem żądania klienta HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera HTTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.
- NX_HTTP_POOL_ERROR (0xE9) Ładunek pakietu puli nie jest wystarczająco duży, aby zawierał kompletne żądanie HTTP.

**Dozwolone z**

Inicjowanie, wątki

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

**Prototyp**

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

**Opis**

Ta usługa usuwa utworzone wcześniej wystąpienie serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne usunięcie serwera HTTP
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

**Dozwolone z**

Wątki

**Przykład**

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

### <a name="retrieve-the-location-and-length-of-entity-data"></a>Pobieranie lokalizacji i długości danych jednostki

**Prototyp**

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

**Opis**

Ta usługa określa lokalizację początku danych w ramach bieżącej jednostki wieloczęściowej w odebranych komunikatach klienta oraz długość danych, które nie łącznie z ciągiem granicy. Wewnętrznie serwer HTTP aktualizuje własne przesunięcia, dzięki czemu ta funkcja może zostać ponownie wywołana na tym samym datagramie klienta dla komunikatów z wieloma jednostkami. Wskaźnik pakietów jest aktualizowany do następnego pakietu, w którym komunikat klient jest datagramem z wieloma pakietami.

Pamiętaj, NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.

Zobacz *nx_http_server_get_entity_header,* aby uzyskać więcej informacji.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Pamiętaj, że aplikacja nie powinna zwalniać tego pakietu.
- **available_offset** Wskaźnik do przesunięcia danych jednostki od wskaźnika dołączania pakietu
- **available_length** Wskaźnik do długości danych jednostki

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie pobrano rozmiar i lokalizację zawartości jednostki
- **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Zawartość wewnętrznych znaczników wieloczęściowych serwera HTTP została już znaleziona
- NX_HTTP_ERROR (0xE0) serwera HTTP
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

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

### <a name="retrieve-the-contents-of-entity-header"></a>Pobieranie zawartości nagłówka jednostki

**Prototyp**

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

**Opis**

Ta usługa pobiera nagłówek jednostki do określonego buforu. Wewnętrznie serwer HTTP aktualizuje własne wskaźniki, aby zlokalizować następną wieloczęściową jednostkę w datagramie klienta z wieloma nagłówkami jednostek. Wskaźnik pakietów jest aktualizowany do następnego pakietu, w którym komunikat klient jest datagramem z wieloma pakietami.

Pamiętaj, NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Pamiętaj, że aplikacja nie powinna zwalniać tego pakietu.
- **entity_header_buffer** Wskaźnik do lokalizacji do przechowywania nagłówka jednostki
- **buffer_size** Rozmiar buforu wejściowego

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie pobrano heade jednostki
- **NX_HTTP_NOT_FOUND (0xE6)** Nie znaleziono pola nagłówka jednostki
- **NX_HTTP_TIMEOUT (0xE1)** Upłynął czas odbierania następnego pakietu dla komunikatu klienta pakietu wielopakietowego 
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę
- NX_HTTP_ERROR (0xE0) Wewnętrzny błąd HTTP

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

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a>Ustawianie wywołania zwrotnego w celu uzyskania daty i godziny GMT

**Prototyp**

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

**Opis**

Ta usługa ustawia wywołanie zwrotne w celu uzyskania daty i godziny GMT na wcześniej utworzonym serwerze HTTP. Ta usługa jest wywoływana, gdy serwer HTTP tworzy nagłówek w odpowiedziach serwera HTTP na klienta.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **gmt_get** Wskaźnik do wywołania zwrotnego GMT
- **data** Wskaźnik do pobranej daty

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne
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

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a>Ustaw wywołanie zwrotne na , aby obsługiwać nieprawidłowe hasło/użytkownika

**Prototyp**

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

**Opis**

Ta usługa ustawia wywołanie zwrotne wywoływane po otrzymaniu nieprawidłowej nazwy użytkownika i hasła w żądaniu get, put lub delete klienta za pomocą uwierzytelniania szyfrowanego lub podstawowego. Serwer HTTP musi zostać utworzony wcześniej.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do serwera HTTP
- **invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/wywołania zwrotnego przebiegu
- **zasób** Wskaźnik do zasobu określonego przez klienta
- **client_address** Adres klienta
- **request_type** Wskazuje typ żądania klienta. Może:
  - NX_HTTP_SERVER_GET_REQUEST
  - NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST
  - NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

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

### <a name="set-additional-mime-maps-for-html"></a>Ustawianie dodatkowych map MIME dla języka HTML 

**Prototyp**

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

**Opis**

Ta usługa umożliwia deweloperowi aplikacji HTTP dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczanych przez serwer HTTP NetX (zobacz *nx_http_server_get_type* lista zdefiniowanych typów).

Po otrzymaniu żądania klienta, np. żądania GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu dodatkowego zestawu map MIME. Jeśli nie zostanie znalezione dopasowanie, szuka dopasowania w domyślnej mapie MIME serwera HTTP. Jeśli dopasowanie nie zostanie znalezione, typ MIME domyślnie będzie miał wartość "tekst/zwykły".

Jeśli funkcja powiadamiania o żądaniu jest zarejestrowana na serwerze  HTTP, wywołanie zwrotne powiadomienia żądania może nx_http_server_type_get w celu analizy typu pliku.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **mime_maps** Wskaźnik do tablicy map MIME
- **mime_map_num** Liczba map MIME w tablicy

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Successful HTTP Server MIME map set (Zestaw map MIME pomyślnego serwera HTTP)
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

**Dozwolone z**

Inicjowanie, wątki

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

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a>Wyodrębnianie długości zawartości i ustawianie wskaźnika na początek danych

**Prototyp**

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

**Opis**

Ta usługa wyodrębnia długość zawartości z nagłówka HTTP. Ponadto pakiet jest aktualizowany w następujący sposób: dołączony wskaźnik pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) przekazaną właśnie nagłówkiem HTTP.

Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na otrzymanie następnego pakietu przy użyciu NX_HTTP_SERVER_TIMEOUT_RECEIVE oczekiwania.

Należy pamiętać, że nie należy jej wywoływania przed wywołaniem *nx_http_server_get_entity_header(),* ponieważ modyfikuje ona dołączany wskaźnik obok nagłówka jednostki.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym, wstępnym wskaźnikiem
- **content_length** Wskaźnik do wyodrębnianych content_length

**Wartości zwracane**

- **NX_SUCCESS** (0x00) znaleziono długość zawartości HTTP i pomyślnie zaktualizowano pakiet
- **NX_HTTP_TIMEOUT** (0xE1) Czas wygaśnięcia oczekiwania na następny pakiet
- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

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

### <a name="receive-the-next-http-packet"></a>Odbieranie następnego pakietu HTTP

**Prototyp**

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

**Opis**

Ta usługa zwraca następny pakiet odebrany na gnieździe serwera HTTP. Opcja oczekiwania na otrzymanie pakietu jest NX_HTTP_SERVER_TIMEOUT_RECEIVE.

**Parametry wejściowe**

- **server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **packet_ptr** Wskaźnik do odebranego pakietu

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie odebrano następny pakiet HTTP
- **NX_HTTP_TIMEOUT** (0xE1) Czas wygaśnięcia oczekiwania na następny pakiet
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

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

**Prototyp**

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

**Opis**

Ta usługa próbuje pobrać określony parametr adresu URL HTTP w podanym pakiecie żądań. Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

**Parametry wejściowe**

- **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu.
- **param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.
- **param_ptr** Obszar docelowy do skopiowania parametru.
- **max_param_size** Maksymalny rozmiar obszaru docelowego parametru.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie parametru serwera HTTP
- **NX_HTTP_NOT_FOUND** (0xE6) Nie znaleziono określonego parametru
- **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parametr żądania nie został prawidłowo zakończony
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="get-query-from-the-request"></a>Uzyskiwanie zapytania z żądania

**Prototyp**

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

**Opis**

Ta usługa próbuje pobrać określone zapytanie adresu URL HTTP w podanym pakiecie żądania. Jeśli żądanego zapytania HTTP nie ma, ta procedura zwraca stan NX_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

**Parametry wejściowe**

- **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu.
- **query_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście zapytań.
- **query_ptr** Obszar docelowy do skopiowania zapytania.
- **max_query_size** Maksymalny rozmiar obszaru docelowego zapytania.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Uzyskiwanie pomyślnego zapytania serwera HTTP
- **NX_HTTP_FAILED** (0xE2) Rozmiar zapytania jest zbyt mały.
- **NX_HTTP_NOT_FOUND** (0xE6) Nie znaleziono określonego zapytania
- **NX_HTTP_NO_QUERY_PARSED** (0xF2) Brak zapytania w żądaniu klienta
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

### <a name="start-the-http-server"></a>Uruchamianie serwera HTTP

**Prototyp**

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

**Opis**

Ta usługa uruchamia wcześniej utworzyć wystąpienie serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne uruchomienie serwera HTTP
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

**Dozwolone z**

Inicjowanie, wątki

**Przykład**

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

### <a name="stop-the-http-server"></a>Zatrzymywanie serwera HTTP

**Prototyp**

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

**Opis**

Ta usługa zatrzymuje wcześniej utworzyć wystąpienie serwera HTTP. Ta procedura powinna zostać wywołana przed usunięciem wystąpienia serwera HTTP.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie serwera HTTP
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

**Dozwolone z**

Wątki

**Przykład**

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

### <a name="extract-file-type-from-client-http-request"></a>Wyodrębnianie typu pliku z żądania HTTP klienta

**Prototyp**

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

**Opis**

Ta usługa wyodrębnia typ żądania  HTTP w buforze http_type_string i jego długość w wartości zwracanej z nazwy buforu wejściowego *,* zazwyczaj adresu URL. Jeśli mapa MIME nie zostanie znaleziona, domyślnie jest to typ "tekst/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX to:

- html text/html
- htm text/html
- tekst txt/zwykły
- gif image/gif
- jpg image/jpeg
- obraz ico/ikona x

Jeśli zostanie podany, przeszukuje również zdefiniowany przez użytkownika zestaw dodatkowych map MIME. Zobacz *nx_http_server_mime_maps_addtional_set(),* aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_server_type_get_extended().*

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **name (nazwa)** Wskaźnik do buforu do wyszukiwania
- **http_type_string** (wskaźnik do wyodrębnianych typów HTML)

**Wartości zwracane**

- **Długość ciągu w bajtach** Wartość niezerowa to powodzenie
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

Bardziej szczegółowy przykład można znaleźć w opisie

*nx_http_server_callback_generate_response_header.*

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

### <a name="extract-file-type-from-client-http-request"></a>Wyodrębnianie typu pliku z żądania HTTP klienta

**Prototyp**

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

**Opis**

Ta usługa wyodrębnia typ żądania  HTTP w buforze http_type_string i jego długość w wartości zwracanej z nazwy buforu wejściowego *,* zazwyczaj adresu URL. Jeśli mapa MIME nie zostanie znaleziona, domyślnie jest to typ "tekst/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX Duo to:

- html text/html
- htm text/html
- tekst txt/zwykły
- gif image/gif
- jpg image/jpeg
- obraz ico/ikona x

Jeśli zostanie podany, przeszukuje również zdefiniowany przez użytkownika zestaw dodatkowych map MIME. Zobacz *nx_http_server_mime_maps_addtional_set(),* aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika.

Ta usługa zastępuje *nx_http_server_type_get().* Ta wersja zawiera dodatkowe informacje o długości.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **name (nazwa)** Wskaźnik do buforu do wyszukiwania
- **name_length** Długość buforu do wyszukania
- **http_type_string** (wskaźnik do wyodrębnianych typów HTML)
- **http_type_string_max_size**

Rozmiar *buforu http_type_string* danych

**Wartości zwracane**

- **Długość ciągu w bajtach** Wartość niezerowa to powodzenie<br />Zero oznacza błąd

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

Bardziej szczegółowy przykład można znaleźć w opisie

*nx_http_server_callback_generate_response_header.*

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

### <a name="set-digest-authenticate-callback-function"></a>Ustawianie funkcji wywołania zwrotnego uwierzytelniania szyfrowanego

**Prototyp**

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

Ta usługa ustawia wywołanie zwrotne wywoływane podczas uwierzytelniania szyfrowanego.

**Parametry wejściowe**

- **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
- **digest_authenticate_callback** Wskaźnik do uwierzytelniania szyfrowanego wywołania zwrotnego uwierzytelniania

**Wartości zwracane**

- **NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
- NX_NOT_SUPPORTED (0x4B) Uwierzytelnianie szyfrowane nie jest włączone

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

### <a name="set-authentication-checking-callback-function"></a>Ustawianie funkcji wywołania zwrotnego sprawdzania uwierzytelniania

**Prototyp**

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

- **NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

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