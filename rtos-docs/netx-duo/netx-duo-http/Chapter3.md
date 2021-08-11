---
title: Rozdział 3 — opis usługi HTTP Azure RTOS NetX Duo
description: Ten rozdział zawiera opis wszystkich usług HTTP Azure RTOS NetX Duo (wymienionych poniżej) w kolejności alfabetycznej, z wyjątkiem tego, że odpowiednik "NetX" (tylko IPv4) tej samej usługi jest ze sobą sparowany).
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 09add7bb20a8e104ba41583c0dbf4d574b8e6c9e6b3a3deed71d8fa8c8942ce2
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796484"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a>Rozdział 3 — opis usługi HTTP Azure RTOS NetX Duo

Ten rozdział zawiera opis wszystkich usług HTTP Azure RTOS NetX Duo (wymienionych poniżej) w kolejności alfabetycznej, z wyjątkiem tego, że odpowiednik "NetX" (tylko IPv4) tej samej usługi jest ze sobą sparowany).

W sekcji "Wartości zwracane" w poniższych opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

**Usługi klienta HTTP:**

- **nx_http_client_create** *tworzenie wystąpienia klienta HTTP*
- **nx_http_client_delete** *usuwanie wystąpienia klienta HTTP*
- **nx_http_client_get_start** *uruchom żądanie HTTP GET (tylko protokół IPv4)*
- **nx_http_client_get_start_extended** *żądania HTTP GET (tylko protokół IPv4)*
- **nxd_http_client_get_start** *uruchomić żądanie HTTP GET (IPv4 lub IPv6)*
- **nxd_http_client_get_start_extended** *uruchomić żądanie HTTP GET (IPv4 lub IPv6)*
- **nx_http_client_get_packet** *Pobierz następny pakiet danych zasobów*
- **nx_http_client_put_start** *żądania HTTP PUT (tylko protokół IPv4)*
- **nx_http_client_put_start_extended** *żądania HTTP PUT (tylko protokół IPv4)*
- **nxd_http_client_put_start** *żądania HTTP PUT (IPv4 lub IPv6)*
- **nxd_http_client_put_start_extended** *żądania HTTP PUT (IPv4 lub IPv6)*
- **nx_http_client_put_packet** *Wyślij następny pakiet danych zasobów*
- **nx_http_client_set_connect_port** *zmienić port, aby nawiązać połączenie z serwerem HTTP*

**Usługi serwera HTTP:**

- **nx_http_server_cache_info_callback_set** *ustawić wywołanie zwrotne, aby pobrać wiek i datę ostatniej modyfikacji określonego adresu URL*
- **nx_http_server_callback_data_send** *wysyłanie danych HTTP z funkcji wywołania zwrotnego*
- **nx_http_server_callback_generate_response_header** *tworzenie nagłówka odpowiedzi w funkcjach wywołania zwrotnego*
- **nx_http_server_callback_generate_response_header_extended** *tworzenie nagłówka odpowiedzi w funkcjach wywołania zwrotnego*
- **nx_http_server_callback_packet_send** *wysyłanie pakietu HTTP z wywołania zwrotnego HTTP*
- **nx_http_server_callback_response_send** *Wysyłanie odpowiedzi z funkcji wywołania zwrotnego*
- **nx_http_server_callback_response_send_extended** *Wysyłanie odpowiedzi z funkcji wywołania zwrotnego*
- **nx_http_server_content_get** *Pobierz zawartość z żądania*
- **nx_http_server_content_get_extended** *pobierz zawartość z żądania; obsługuje puste żądania (zero długości zawartości)*
- **nx_http_server_content_length_get** *Uzyskiwanie długości zawartości w żądaniu*
- **nx_http_server_content_length_get_extended** żądania pobierz długość zawartości; obsługuje *puste żądania (zero długości zawartości)*
- **nx_http_server_create** *tworzenie wystąpienia serwera HTTP*
- **nx_http_server_delete** * Usuwanie wystąpienia serwera HTTP*
- **nx_http_server_get_entity_content** *zwracany rozmiar i lokalizacja zawartości jednostki w adresie URL*
- **nx_http_server_get_entity_header** *wyodrębnianie nagłówka jednostki adresu URL do określonego buforu*
- **nx_http_server_gmt_callback_set** *ustawić wywołanie zwrotne w celu pobrania daty i godziny GMT*
- **nx_http_server_invalid_userpassword_notify_set** ustawić wywołanie zwrotne w przypadku odebrania nieprawidłowej nazwy użytkownika i *hasła w żądaniu klienta*
- **nx_http_server_mime_maps_additional_set** *Definiowanie dodatkowych map mime dla języka HTML*
- **nx_http_server_packet_content_find** *wyodrębnianie długości zawartości w nagłówku HTTP* i ustawianie wskaźnika na początek danych zawartości
- **nx_http_server_packet_get** *bezpośrednio odbierać pakiet klienta*
- **nx_http_server_param_get** *pobierz parametr z żądania*
- **nx_http_server_query_get** *pobierz zapytanie z żądania*
- **nx_http_server_start** *uruchom serwer HTTP*
- **nx_http_server_stop** *zatrzymać serwer HTTP*
- **nx_http_server_type_get (przestarzałe)** Wyodrębnianie typu *HTTP, np. tekst/zwykły z nagłówka*
- **nx_http_server_type_get_extended** *typu HTTP, np. tekst/zwykły z nagłówka*
- **nx_http_server_digest_authenticate_notify_set** *funkcji wywołania zwrotnego uwierzytelniania szyfrowanego*
- **nx_http_server_authentication_check_set** *ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania*

## <a name="nx_http_client_create"></a>nx_http_client_create

Tworzenie wystąpienia klienta PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **client_name** Nazwa wystąpienia klienta HTTP.
 - **ip_ptr** Wskaźnik do wystąpienia adresu IP.
 - **pool_ptr** Wskaźnik do domyślnej puli pakietów. Należy pamiętać, że pakiety w tej puli muszą mieć ładunek wystarczająco duży, aby obsłużyć pełny nagłówek odpowiedzi. Jest to definiowane przez NX_HTTP_CLIENT_MIN_PACKET_SIZE w *nx_http.h.*
 - **window_size** Rozmiar okna odbierania gniazda TCP klienta.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów
 - NX_HTTP_POOL_ERROR (0xE9) Nieprawidłowy rozmiar ładunku w puli pakietów

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

Usuwanie wystąpienia klienta HTTP

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie klienta HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne usunięcie klienta HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik HTTP
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

Uruchamianie żądania HTTP GET za pośrednictwem protokołu IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań do usługi *nx_http_client_get_packet* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań GET.

Ta usługa działa tylko za pośrednictwem sieci IPv4. W przypadku aplikacji, które muszą łączyć się z siecią IPv6, *nxd_http_client_get_start_extended().*

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_client_get_start_extended()* *lub nxd_http_client_get_start_extended().*

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **ip_address** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
 - **input_ptr** Wskaźnik do dodatkowych danych dla żądania GET. Jest to opcjonalne. Jeśli jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości komunikatu, a zamiast operacji GET jest używany wpis POST.
 - **input_size** Liczba bajtów w opcjonalnych dodatkowych danych wejściowych wskazywanych przez ```input_ptr``` .
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano klienta HTTP. Komunikat startowy GET.
 - **NX_HTTP_ERROR** (0xE0) Wewnętrzny błąd klienta HTTP
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - **NX_HTTP_FAILED** (0xE2) klienta HTTP komunikuje się z serwerem HTTP.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa i/lub hasło.
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

Uruchamianie żądania HTTP GET za pośrednictwem protokołu IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP. Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań do usługi *nx_http_client_get_packet* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań GET.

Ta usługa działa tylko za pośrednictwem sieci IPv4. W przypadku aplikacji, które muszą łączyć się z siecią IPv6, *nxd_http_client_get_start_extended().*

Ta usługa zastępuje *nx_http_client_get_start()*. Wymaga to od wywołującego określenia długości zasobu, nazwy użytkownika i hasła.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **ip_address** Adres IP serwera HTTP.
 - **resource Pointer** to URL string for requested resource (Wskaźnik zasobu do ciągu adresu URL dla żądanego zasobu).
 - **resource_length** Długość ciągu adresu URL dla żądanego zasobu.
 - **input_ptr** Wskaźnik do dodatkowych danych dla żądania GET. Jest to opcjonalne. Jeśli jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości komunikatu, a zamiast operacji GET jest używany wpis POST.
 - **input_size** Liczba bajtów w opcjonalnych dodatkowych danych wejściowych wskazywanych przez ```input_ptr``` .
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **password_length** Długość opcjonalnego hasła do uwierzytelniania.
 - **wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano klienta HTTP. Komunikat startowy GET
 - **NX_HTTP_ERROR** (0xE0) Wewnętrzny błąd klienta HTTP
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - **NX_HTTP_FAILED** (0xE2) klienta HTTP komunikuje się z serwerem HTTP.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa i/lub hasło.
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a>nxd_http_client_get_start

Wysyłanie żądania HTTP GET (IPv4 lub IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP. Może służyć do nawiązywania połączenia z siecią IPv4 lub IPv6. Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań do usługi *nx_http_client_get_packet* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.

> [!NOTE]
>Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań GET.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nxd_http_client_get_start_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **Server_ip** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
 - **input_ptr** Wskaźnik do dodatkowych danych dla żądania GET. Jest to opcjonalne. Jeśli jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości komunikatu, a zamiast operacji GET jest używany wpis POST.
 - **input_size** Liczba bajtów w opcjonalnych dodatkowych danych wejściowych wskazywanych przez ```input_ptr``` .
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **password_length** Długość opcjonalnego hasła do uwierzytelniania.
 - **wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie GET
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Hasło przekracza rozmiar buforu
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - **NX_HTTP_FAILED** (0xE2) Nieprawidłowe parametry pakietu.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa lub hasło
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a>nxd_http_client_get_start_extended

Wysyłanie żądania HTTP GET (IPv4 lub IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP. Może służyć do nawiązywania połączenia z siecią IPv4 lub IPv6. Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań do usługi *nx_http_client_get_packet* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań GET.

Ta usługa zastępuje *nxd_http_client_get_start()*. Wymaga to od wywołującego określenia długości zasobu, nazwy użytkownika i hasła.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **Server_ip** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
 - **resource_length** Długość ciągu adresu URL dla żądanego zasobu.
 - **input_ptr** Wskaźnik do dodatkowych danych dla żądania GET. Jest to opcjonalne. Jeśli jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości komunikatu, a zamiast operacji GET jest używany wpis POST.
 - **input_size** Liczba bajtów w opcjonalnych dodatkowych danych wejściowych wskazywanych przez ```input_ptr``` .
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **password_length** Długość opcjonalnego hasła do uwierzytelniania.
 - **wait_option** Określa, jak długo usługa będzie czekać wewnętrznie na rozpoczęcie przetwarzania klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie GET
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Hasło przekracza rozmiar buforu
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - **NX_HTTP_FAILED** (0xE2) Nieprawidłowe parametry pakietu.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa lub hasło
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

Uzyskiwanie następnego pakietu danych zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a>Opis

Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie *nx_http_client_get_start* wywołania. Kolejne wywołania tej procedury powinny być dokonywane do momentu, gdy zostanie odebrany NX_HTTP_GET_DONE stan zwracany.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **packet_ptr** Miejsce docelowe wskaźnika pakietu zawierającego częściową zawartość zasobu.
 - **wait_option** Określa, jak długo usługa będzie czekać na pakiet get klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie pobierz pakiet klienta HTTP.
 - **NX_HTTP_GET_DONE** (0xEC) http client get packet is done
 - **NX_HTTP_NOT_READY** (0xEA) KLIENTA HTTP nie jest w trybie get.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Nieprawidłowa długość pakietu
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

Uruchamianie żądania HTTP PUT za pośrednictwem protokołu IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP pod podanym adresem IP. Jeśli ta procedura powiedzie się, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet(),* aby rzeczywiście wysłać zawartość zasobu do serwera HTTP.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań PUT.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nxd_http_client_put_start_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **ip_address** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **total_bytes** Całkowita liczba bajtów wysyłanych zasobów. Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań do nx_http_client_put_packet *musi* być równa tej wartości.
 - **wait_option** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP PUT. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) Nazwa użytkownika jest zbyt duża dla buforu
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

Uruchamianie żądania HTTP PUT za pośrednictwem protokołu IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP pod podanym adresem IP. Jeśli ta procedura powiedzie się, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet(),* aby rzeczywiście wysłać zawartość zasobu do serwera HTTP.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań PUT.

Ta usługa zastępuje *nx_http_client_put_start()*. Wymaga to od wywołującego określenia długości zasobu, nazwy użytkownika i hasła.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **ip_address** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
 - **resource_length** Długość ciągu adresu URL dla zasobu do wysłania do serwera.
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **password_length** Długość opcjonalnego hasła do uwierzytelniania.
 - **total_bytes** Całkowita liczba bajtów wysyłanych zasobów. Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań do nx_http_client_put_packet *musi* być równa tej wartości.
 - **wait_option** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP PUT. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) Nazwa użytkownika jest zbyt duża dla buforu
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a>nxd_http_client_put_start

Uruchamianie żądania HTTP PUT (IPv4 lub IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje umieścić (wysłać) określony zasób na serwerze HTTP pod podanym adresem IP za pośrednictwem protokołu IPv6. Jeśli ta procedura powiedzie się, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet(),* aby rzeczywiście wysłać zawartość zasobu do serwera HTTP.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań PUT.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nxd_http_client_put_start_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **server_ip** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **total_bytes** Całkowita liczba bajtów wysyłanych zasobów. Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań do nx_http_client_put_packet *musi* być równa tej wartości.
 - **wait_option** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP PUT. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie HTTP Client PUT
 - **NX_HTTP_ERROR** (0xE0) klienta HTTP
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - **NX_HTTP_FAILED** (0xE2) klienta HTTP komunikuje się z serwerem HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a>nxd_http_client_put_start_extended

Uruchamianie żądania HTTP PUT (IPv4 lub IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje umieścić (wysłać) określony zasób na serwerze HTTP pod podanym adresem IP za pośrednictwem protokołu IPv6. Jeśli ta procedura powiedzie się, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet(),* aby rzeczywiście wysłać zawartość zasobu do serwera HTTP.

> [!NOTE]
> Ciąg zasobu może odwoływać się do pliku lokalnego, np. lub do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` żądań PUT.

Ta usługa zastępuje *nxd_http_client_put_start()*. Wymaga to od wywołującego określenia długości zasobu, nazwy użytkownika i hasła.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **ip_address** Adres IP serwera HTTP.
 - **zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.
 - **resource_length** Długość ciągu adresu URL dla zasobu do wysłania do serwera.
 - **nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **username_length** Długość opcjonalnej nazwy użytkownika do uwierzytelniania.
 - **hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.
 - **password_length** Długość opcjonalnego hasła do uwierzytelniania.
 - **total_bytes** Całkowita liczba bajtów wysyłanych zasobów. Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań do nx_http_client_put_packet *musi* być równa tej wartości.
 - **wait_option** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP PUT. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie HTTP Client PUT
 - **NX_HTTP_ERROR** (0xE0) klienta HTTP
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready (Klient HTTP nie jest gotowy)
 - NX_HTTP_FAILED (0xE2) klienta HTTP komunikuje się z serwerem HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

Wyślij następny pakiet danych zasobów

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP.

> [!NOTE]
> Ta procedura powinna być wywoływana powtarzalnie, dopóki łączna długość wysłanych pakietów nie będzie równa "total_bytes" określonej w poprzednim *wywołaniu nx_http_client_put_start* wywołania.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.
 - **wait_option** Określa, jak długo usługa będzie czekać wewnętrznie na przetwarzanie pakietu PUT klienta HTTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość przechyłki** czasu (0x00000001 do 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.

    Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano pakiet klienta HTTP.
 - **NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready
 - **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Odebrano kod błędu serwera
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Nieprawidłowa długość pakietu
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nieprawidłowa nazwa i/lub Hasło
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) serwer odpowiada przed ukończeniem procesu PUT
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_INVALID_PACKET (0x12) Pakiet jest zbyt mały dla nagłówka TCP
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

Ustawianie portu połączenia na serwer

### <a name="prototype"></a>Prototype

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a>Opis

Ta usługa zmienia port połączenia podczas nawiązywania połączenia z serwerem HTTP na określonym porcie w czasie wykonywania. W przeciwnym razie port połączenia domyślnie ma wartość 80. Ta nazwa musi być wywoływana przed *nx_http_client_get_start()* *i nx_http_client_put_start(),* np. podczas połączenia klienta HTTP z serwerem.

### <a name="input-parameters"></a>Parametry wejściowe

 - **client_ptr** Wskaźnik do bloku sterowania klienta HTTP.
 - **port** Port do nawiązywania połączenia z serwerem.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie zmień port
 - NX_INVALID_PORT (0x46) przekracza wartość maksymalną (0xFFFF) lub jest równa zero
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

Ustawianie wywołania zwrotnego w celu pobrania maksymalnego wieku i daty adresu URL

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołaną usługę wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **cache_info_get** Wskaźnik do wywołania zwrotnego
 - **max_age** Wskaźnik do maksymalnego wieku zasobu
 - **dane** Zwrócony wskaźnik do daty ostatniej modyfikacji.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja

### <a name="example"></a>Przykład

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

Wysyłanie danych z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a>Opis

Ta usługa wysyła dane w dostarczonym pakiecie z procedury wywołania zwrotnego aplikacji. Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST.

> [!NOTE]
> Jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie. Ponadto procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **data_ptr** Wskaźnik do danych do wysłania.
 - **data_length**  Liczba bajtów do wysłania.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano dane serwera
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Opis

Ta usługa wywołuje funkcję wewnętrzną *_nx_http_server_generate_response_header* gdy serwer HTTP odpowiada na żądania get, put i delete klienta. Jest on przeznaczony do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje swoją odpowiedź na klienta.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nxd_http_server_callback_generate_response_header_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **packet_pptr** Wskaźnik wskaźnika pakietu przydzielonego do komunikatu
 - **status_code** Wskazuje stan zasobu. Przykłady:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **content_length** Rozmiar zawartości w bajtach
 - **content_type** Typ protokołu HTTP, np. "tekst/zwykły"
 - **additional_header** Wskaźnik do dodatkowego tekstu nagłówka

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie utworzono nagłówek
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
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

Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta usługa wywołuje funkcję wewnętrzną *_nx_http_server_generate_response_header(),* gdy serwer HTTP odpowiada na żądania get, put i delete klienta. Jest on przeznaczony do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje swoją odpowiedź na klienta.

Ta usługa zastępuje *nx_http_server_callback_generate_response_header()*. Ta wersja dostarcza dodatkowe informacje o długości do funkcji wywołania zwrotnego.

### <a name="input-parameters"></a>Parametry wejściowe

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

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie utworzono nagłówek
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
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
                 length,  server_ptr ->
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

Wysyłanie pakietu HTTP z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego HTTP. Serwer HTTP wyśle pakiet z NX_HTTP_SERVER _TIMEOUT_SEND. Nagłówek HTTP i dane muszą zostać dołączone do pakietu. Jeśli stan zwracany wskazuje błąd, aplikacja HTTP musi zwolnić pakiet.

Wywołanie zwrotne powinno zwrócić NX_HTTP_CALLBACK_COMPLETED.

Zobacz *nx_http_server_callback_generate_response_header(),* aby uzyskać bardziej szczegółowy przykład.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **packet_ptr** Wskaźnik do pakietu do wysłania

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano pakiet serwera
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

Wysyłanie odpowiedzi z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a>Opis

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zazwyczaj używane do wysyłania odpowiedzi niestandardowych skojarzonych z żądaniami GET/POST.

> [!NOTE]
> Jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nxd_http_server_callback_response_send_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **nagłówek** Wskaźnik do ciągu nagłówka odpowiedzi.
 - **informacje o** Wskaźnik do ciągu informacyjnego.
 - **additional_info** Wskaźnik do dodatkowego ciągu informacyjnego.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano odpowiedź serwera

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
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

Wysyłanie odpowiedzi z funkcji wywołania zwrotnego

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a>Opis

Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji. Jest to zazwyczaj używane do wysyłania odpowiedzi niestandardowych skojarzonych z żądaniami GET/POST.

> [!NOTE]
> Jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.

Ta usługa zastępuje *nx_http_server_callback_response_send()*. Ta wersja przyjmuje dodatkowe informacje o długości jako argumenty.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **nagłówek** Wskaźnik do ciągu nagłówka odpowiedzi.
 - **header_length** Długość ciągu nagłówka odpowiedzi.
 - **informacje o** Wskaźnik do ciągu informacyjnego.
 - **information_length** Długość ciągu informacyjnego.
 - **additional_info** Wskaźnik do dodatkowego ciągu informacyjnego.
 - **additional_info_length** Długość dodatkowego ciągu informacyjnego.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie wysłano odpowiedź serwera

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
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

Pobierz zawartość z żądania

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać określoną ilość zawartości z żądania KLIENTA HTTP POST lub PUT. Powinien on zostać wywołany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create*).

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_server_content_get_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadomienia o żądaniu.
 - **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
 - **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
 - **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
 - **actual_size** Wskaźnik do zmiennej docelowej, która zostanie ustawiona na rzeczywisty rozmiar skopiowanej zawartości.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie zawartości serwera HTTP
 - **NX_HTTP_ERROR** (0xE0) serwera HTTP
 - **NX_HTTP_DATA_END** (0xE7) Zawartość zakończenia żądania
 - **NX_HTTP_TIMEOUT** (0xE1) serwera HTTP podczas uzyskiwania następnego pakietu zawartości
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

Pobierz zawartość z żądania/obsługuje długość treści o zerowej długości

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a>Opis

Ta usługa jest niemal identyczna *z nx_http_server_content_get();* próbuje pobrać określoną ilość zawartości z żądania KLIENTA HTTP POST lub PUT. Jednak obsługuje żądania o długości zawartości o wartości zerowej ("pustym żądaniu") jako prawidłowe żądanie. Powinno ono zostać wywołane z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

Ta usługa zastępuje *nx_http_server_content_get()*. Ta wersja wymaga od wywołującego dostarczania dodatkowych informacji o długości.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadomienia o żądaniu.
 - **byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.
 - **destination_ptr** Wskaźnik do obszaru docelowego zawartości.
 - **destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.
 - **actual_size** Wskaźnik do zmiennej docelowej, która zostanie ustawiona na rzeczywisty rozmiar skopiowanej zawartości.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie zawartości HTTP
 - **NX_HTTP_ERROR** (0xE0) serwera HTTP
 - **NX_HTTP_DATA_END** (0xE7) Zawartość zakończenia żądania
 - **NX_HTTP_TIMEOUT** (0xE1) serwera HTTP podczas uzyskiwania następnego pakietu
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

Uzyskiwanie długości zawartości w żądaniu

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. Jeśli nie ma zawartości HTTP, ta procedura zwraca wartość zero. Powinno ono zostać wywołane z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create()*).

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_server_content_length_get_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadomienia o żądaniu.

### <a name="return-values"></a>Wartości zwrócone

 - **długość zawartości** W przypadku błędu zwracana jest wartość zero  

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

Uzyskiwanie długości zawartości w żądaniu/obsługuje długość zawartości o wartości zero

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a>Opis

Ta usługa jest podobna *do nx_http_server_content_length_get;* próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie. Jednak wartość zwracana wskazuje stan pomyślnego ukończenia, a rzeczywista wartość długości jest zwracana we wskaźniku wejściowym ```content_length``` . Jeśli nie ma zawartości HTTP/długość zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a wskaźnik wejściowy content_length wskazuje prawidłową długość (zero). Powinien on zostać wywołany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create*).

Ta usługa zastępuje *nx_http_server_content_length_get()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadomienia o żądaniu.
 - **content_length** Wskaźnik do wartości pobranej z pola Długość zawartości

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Serwer pomyślny pobierz
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Nieprawidłowy format nagłówka HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

Tworzenie wystąpienia serwera HTTP

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera HTTP, które jest uruchamiane w kontekście własnego wątku ThreadX. Opcjonalna *authentication_check* i request_notify wywołania zwrotnego aplikacji zapewniają kontrolę oprogramowania aplikacji nad podstawowymi operacjami serwera HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.
 - **http_server_name** Wskaźnik do nazwy serwera HTTP.
 - **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
 - **media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.
 - **stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.
 - **stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.
 - **authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji. Jeśli zostanie określona, ta procedura jest wywoływana dla każdego żądania klienta HTTP. Jeśli ten parametr ma wartość NULL, uwierzytelnianie nie będzie przeprowadzane.
 - **request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji. Jeśli określono, ta procedura jest wywoływana przed przetwarzaniem żądania przez serwer HTTP. Umożliwia to przekierowywanie nazwy zasobu lub zaktualizowanie pól w zasobie przed ukończeniem żądania klienta HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera HTTP.
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.
 - NX_HTTP_POOL_ERROR (0xE9) Ładunek pakietu puli nie jest wystarczająco duży, aby zawierał kompletne żądanie HTTP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

Usuwanie wystąpienia serwera HTTP

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie serwera HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne usunięcie serwera HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

Pobieranie lokalizacji i długości danych jednostki

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a>Opis

Ta usługa określa lokalizację początku danych w ramach bieżącej jednostki wieloczęściowej w odebranych komunikatach klienta oraz długość danych, które nie łącznie z ciągiem granicy. Wewnętrznie serwer HTTP aktualizuje własne przesunięcia, dzięki czemu ta funkcja może zostać ponownie wywołana na tym samym datagramie klienta dla komunikatów z wieloma jednostkami. Wskaźnik pakietów jest aktualizowany do następnego pakietu, w którym komunikat klient jest datagramem wielu pakietów.

> [!NOTE]
> NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.

Zobacz [*nx_http_server_get_entity_header,*](#nx_http_server_get_entity_header) aby uzyskać więcej szczegółów.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do serwera HTTP
 - **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Pamiętaj, że aplikacja nie powinna zwalniać tego pakietu.
 - **available_offset** Wskaźnik do przesunięcia danych jednostki od wskaźnika dołączania pakietu
 - **available_length** Wskaźnik do długości danych jednostki

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie pobrano rozmiar i lokalizację zawartości jednostki
 - **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Zawartość wewnętrznych znaczników wieloczęściowych serwera HTTP została już znaleziona
 - NX_HTTP_ERROR (0xE0) Wewnętrzny błąd HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

Pobieranie zawartości nagłówka jednostki

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera nagłówek jednostki do określonego buforu. Wewnętrznie serwer HTTP aktualizuje własne wskaźniki, aby zlokalizować następną jednostkę wieloczęściową w datagramie klienta z wieloma nagłówkami jednostek. Wskaźnik pakietów jest aktualizowany do następnego pakietu, w którym komunikat klient jest datagramem wielu pakietów.

> [!NOTE]
> NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do serwera HTTP
 - **packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu. Pamiętaj, że aplikacja nie powinna zwalniać tego pakietu.
 - **entity_header_buffer** Wskaźnik do lokalizacji do przechowywania nagłówka jednostki
 - **buffer_size** Rozmiar buforu wejściowego

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie pobrano heade jednostki
 - **NX_HTTP_NOT_FOUND** **(0xE6) Nie** znaleziono pola nagłówka jednostki
 - **NX_HTTP_TIMEOUT** **(0xE1) Upłynął** czas odbierania następnego pakietu dla komunikatu klienta pakietu wielopakietowego
 - NX_HTTP_ERROR (0xE0) Wewnętrzny błąd HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

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
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

Ustawianie wywołania zwrotnego w celu uzyskania daty i godziny GMT

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne w celu uzyskania daty i godziny GMT na wcześniej utworzonym serwerze HTTP. Ta usługa jest wywoływana, gdy serwer HTTP tworzy nagłówek w odpowiedziach serwera HTTP na klienta.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do serwera HTTP
 - **gmt_getv** Wskaźnik do wywołania zwrotnego GMT
 - **datev** Wskaźnik do pobranej daty

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

Ustaw wywołanie zwrotne na w celu obsługi nieprawidłowego użytkownika/hasła

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne wywoływane po otrzymaniu nieprawidłowej nazwy użytkownika i hasła w żądaniu get, put lub delete klienta za pomocą uwierzytelniania szyfrowanego lub podstawowego. Serwer HTTP musi zostać utworzony wcześniej.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do serwera HTTP
 - **invalid_username_password_callback** Wskaźnik do nieprawidłowego wywołania zwrotnego użytkownika/przebiegu
 - **zasób** Wskaźnik do zasobu określonego przez klienta
 - **client_address** Wskaźnik do adresu klienta. Może to być protokół IPv4 lub IPv6
 - **request_type** Wskazuje typ żądania klienta. Może:
    - NX_HTTP_SERVER_GET_REQUEST
    - NX_HTTP_SERVER_POST_REQUEST
    - NX_HTTP_SERVER_HEAD_REQUEST
    - NX_HTTP_SERVER_PUT_REQUEST
    - NX_HTTP_SERVER_DELETE_REQUEST

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

Ustawianie dodatkowych map MIME dla języka HTML

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a>Opis

Ta usługa umożliwia deweloperowi aplikacji HTTP dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczanych przez serwer HTTP NetX Duo (zobacz *nx_http_server_get_type,* aby uzyskać listę zdefiniowanych typów).

Po otrzymaniu żądania klienta, np. żądania GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu dodatkowego zestawu map MIME, a jeśli nie zostanie znalezione dopasowanie, szuka dopasowania w domyślnej mapie MIME serwera HTTP. Jeśli dopasowanie nie zostanie znalezione, typ MIME domyślnie ma wartość "text/plain".

Jeśli funkcja powiadamiania o żądaniu jest zarejestrowana na serwerze HTTP, wywołanie zwrotne powiadomienia żądania może wywołać funkcję *nx_http_server_type_retrieve()* w celu analizy typu pliku.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **mime_maps** Wskaźnik do tablicy map MIME
 - **mime_map_num** Liczba map MIME w tablicy

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Zestaw map MIME serwera HTTP
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

Wyodrębnianie długości zawartości i ustawianie wskaźnika na początek danych

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a>Opis

Ta usługa wyodrębnia długość zawartości z nagłówka HTTP. Ponadto pakiet jest aktualizowany w następujący sposób: dołączony wskaźnik pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) przekazaną właśnie do nagłówka HTTP.

Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na otrzymanie następnego pakietu przy użyciu NX_HTTP_SERVER_TIMEOUT_RECEIVE oczekiwania.

> [!NOTE]
> Nie należy tego wywoływania przed *wywołaniem* nx_http_server_get_entity_header, ponieważ modyfikuje on wstępnie wskaźnik obok nagłówka jednostki.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym, wstępnym wskaźnikiem
 - **content_length** Wskaźnik do wyodrębnienia ```content_length```

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) znaleziono długość zawartości HTTP i pomyślnie zaktualizowano pakiet
 - **NX_HTTP_TIMEOUT** (0xE1) Czas wygaśnięcia oczekiwania na następny pakiet
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

Odbieranie następnego pakietu HTTP

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca następny pakiet odebrany na gnieździe serwera HTTP. Opcja oczekiwania na otrzymanie pakietu jest NX_HTTP_SERVER_TIMEOUT_RECEIVE.

### <a name="input-parameters"></a>Parametry wejściowe

 - **server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **packet_ptr** Wskaźnik do odebranego pakietu

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie odebrano następny pakiet
 - **NX_HTTP_TIMEOUT** (0xE1) Czas wygaśnięcia oczekiwania na następny pakiet
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

Pobierz parametr z żądania

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać określony parametr adresu URL HTTP w podanym pakiecie żądań. Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create*).

### <a name="input-parameters"></a>Parametry wejściowe

 - **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu.
 - **param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.
 - **param_ptr** Obszar docelowy do skopiowania parametru.
 - **max_param_size** Maksymalny rozmiar obszaru docelowego parametru.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie parametru serwera HTTP
 - **NX_HTTP_NOT_FOUND** (0xE6) Nie znaleziono określonego parametru
 - **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parametr żądania nie został prawidłowo zakończony
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

Uzyskiwanie zapytania z żądania

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a>Opis

Ta usługa próbuje pobrać określone zapytanie adresu URL HTTP w podanym pakiecie żądania. Jeśli żądanego zapytania HTTP nie ma, ta procedura zwraca stan NX_HTTP_NOT_FOUND. Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_http_server_create*).

### <a name="input-parameters"></a>Parametry wejściowe

 - **packet_ptr** Wskaźnik do pakietu żądań klienta HTTP. Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu.
 - **query_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście zapytań.
 - **query_ptr** Obszar docelowy do skopiowania zapytania.
 - **max_query_size** Maksymalny rozmiar obszaru docelowego zapytania.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Uzyskiwanie pomyślnego zapytania serwera HTTP
 - **NX_HTTP_FAILED** (0xE2) Rozmiar zapytania jest zbyt mały.
 - **NX_HTTP_NOT_FOUND** (0xE6) Nie znaleziono określonego zapytania
 - **NX_HTTP_NO_QUERY_PARSED** (0xF2) Brak zapytania w żądaniu klienta
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a>nx_http_server_start

Uruchamianie serwera HTTP

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzyć wystąpienie serwera HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne uruchomienie serwera
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

Zatrzymywanie serwera HTTP

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje wcześniej utworzyć wystąpienie serwera HTTP. Ta procedura powinna zostać wywołana przed usunięciem wystąpienia serwera HTTP.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślne zatrzymanie serwera
 - NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy
 - NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

Wyodrębnianie typu pliku z żądania HTTP klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a>Opis

> [!NOTE]
> Ta usługa jest przestarzała. Zachęcamy użytkowników do korzystania z usługi *nx_http_server_type_retrieve()*.

Ta usługa wyodrębnia typ żądania HTTP w buforze http_type_string i jego długość w wartości zwracanej z nazwy buforu wejściowego, zazwyczaj adresu URL. Jeśli mapa MIME nie zostanie znaleziona, domyślnie jest to typ "tekst/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX Duo to:

 - **html** text/html
 - **htm** text/html
 - **tekst txt/zwykły**
 - **gif** image/gif
 - **jpg** image/jpeg
 - **obraz ico/ikona** x

Jeśli zostanie podany, przeszukuje również zdefiniowany przez użytkownika zestaw dodatkowych map MIME. Zobacz *nx_http_server_mime_maps_addtional_set(),* aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_http_server_type_get_extended()*.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **name Pointer** to buffer to search (Wskaźnik nazwy do buforu do wyszukiwania)
 - **http_type_string** (wskaźnik do wyodrębnianych typów HTML)

### <a name="return-values"></a>Wartości zwrócone

 - **Długość ciągu w bajtach** Wartość niezerowa to powodzenie. Zero oznacza błąd.

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

Wyodrębnianie typu pliku z żądania HTTP klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a>Opis

Ta usługa wyodrębnia typ żądania  HTTP w buforze http_type_string i jego długość w wartości zwracanej z nazwy buforu wejściowego *,* zazwyczaj adresu URL. Jeśli mapa MIME nie zostanie znaleziona, domyślnie jest to typ "tekst/zwykły". W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapami MIME serwera HTTP dla dopasowania. Domyślne mapy MIME na serwerze HTTP NetX Duo to:

 - **html** text/html
 - **htm** text/html
 - **tekst txt/zwykły**
 - **gif** image/gif
 - **jpg** image/jpeg
 - **obraz ico/ikona** x

Jeśli zostanie podany, przeszukuje również zdefiniowany przez użytkownika zestaw dodatkowych map MIME. Zobacz *nx_http_server_mime_maps_addtional_set(),* aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika.

Ta usługa zastępuje *nx_http_server_type_get()*. Ta wersja zawiera dodatkowe informacje o długości.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **name (nazwa)** Wskaźnik do buforu do wyszukiwania
 - **name_length** Długość buforu do wyszukania
 - **http_type_string** (wskaźnik do wyodrębnianych typów HTML)
 - **http_type_string_max_size** Rozmiar buforu http_type_string danych

### <a name="return-values"></a>Wartości zwrócone

 - **Długość ciągu w bajtach** Wartość niezerowa to powodzenie. Zero oznacza błąd.

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

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
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

Aby uzyskać bardziej szczegółowy przykład, zobacz opis [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

Ustawianie funkcji wywołania zwrotnego uwierzytelniania szyfrowanego

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne wywoływane podczas uwierzytelniania szyfrowanego.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **digest_authenticate_callback** Wskaźnik do uwierzytelniania szyfrowanego wywołania zwrotnego

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika
 - NX_NOT_SUPPORTED (0x4B) Uwierzytelnianie szyfrowane nie jest włączone

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

Ustawianie funkcji wywołania zwrotnego sprawdzania uwierzytelniania

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta usługa ustawia funkcję wywołania zwrotnego sprawdzania uwierzytelniania.

### <a name="input-parameters"></a>Parametry wejściowe

 - **http_server_ptr** Wskaźnik do wystąpienia serwera HTTP
 - **authentication_check_extended** Wskaźnik do sprawdzania uwierzytelniania aplikacji

### <a name="return-values"></a>Wartości zwrócone

 - **NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne
 - NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Aplikacja

### <a name="example"></a>Przykład

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
