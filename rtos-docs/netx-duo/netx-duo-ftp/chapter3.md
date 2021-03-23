---
title: Rozdział 3 — Opis usług FTP
description: Ten rozdział zawiera opis wszystkich usług FTP NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821883"
---
# <a name="chapter-3---description-of-ftp-services"></a>Rozdział 3 — Opis usług FTP

Ten rozdział zawiera opis wszystkich usług FTP NetX (wymienionych poniżej) w porządku alfabetycznym (z wyjątkiem przypadków, gdy równorzędne Protokoły IPv4 i IPv6 są połączone).

> [!NOTE]
> W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Nawiązywanie połączenia z serwerem FTP za pośrednictwem protokołu IPv4

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa nawiązuje połączenie utworzonego wcześniej wystąpienia klienta FTP NetX z serwerem FTP przy użyciu podanego adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **server_IP** Adres IP serwera FTP.
- **Nazwa użytkownika** Nazwa użytkownika klienta na potrzeby uwierzytelniania.
- **hasło** Hasło klienta na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na połączenie z klientem FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) POMYŚLNE połączenie FTP.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) nie otrzymał odpowiedzi 22X (ok)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) nie otrzymał odpowiedzi 23X (ok)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) nie otrzymał odpowiedzi 33X (ok)
- Klient **NX_FTP_NOT_DISCONNECTED** (0xD4) jest już połączony.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.
- NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>Zobacz też

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect

## <a name="nxd_ftp_client_connect"></a>nxd_ftp_client_connect

Nawiązywanie połączenia z serwerem FTP przy użyciu protokołu IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa nawiązuje połączenie utworzonego wcześniej wystąpienia klienta FTP NetX Duo z serwerem FTP na podanym adresie IP. Obsługiwane są zarówno sieci IPv4, jak i IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **server_ipduo** Adres IP serwera FTP.
- **Nazwa użytkownika** Nazwa użytkownika klienta na potrzeby uwierzytelniania.
- **hasło** Hasło klienta na potrzeby uwierzytelniania.
- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na połączenie z klientem FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) POMYŚLNE połączenie FTP.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) nie otrzymał odpowiedzi 22X (ok)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) nie otrzymał odpowiedzi 23X (ok)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) nie otrzymał odpowiedzi 33X (ok)
- Klient **NX_FTP_NOT_DISCONNECTED** (0xD4) jest już połączony
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik Inout.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.
- NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>Zobacz też

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Tworzenie wystąpienia klienta FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **ftp_client_name** Nazwa klienta FTP.
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **window_size** Anonsowany rozmiar okna dla gniazd TCP dla tego klienta FTP.
- **pool_ptr** Wskaźnik do domyślnej puli pakietów dla tego klienta FTP. Należy pamiętać, że minimalny ładunek pakietu musi być wystarczająco duży, aby pomieścić pełną ścieżkę i nazwę pliku lub katalogu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta FTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Usuwanie wystąpienia klienta FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie klienta FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie klienta FTP.
- Klient FTP **NX_FTP_NOT_DISCONNECTED** (0xD4) nie został odłączony
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Tworzenie katalogu na serwerze FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa tworzy określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **directory_name** Nazwa katalogu do utworzenia.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na utworzenie katalogu FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie katalogu FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Ustawianie domyślnego katalogu na serwerze FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślny katalog na serwerze FTP, który jest połączony z określonym klientem FTP. Ten domyślny katalog ma zastosowanie tylko do połączenia tego klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **directory_path** Nazwa ścieżki katalogu do ustawienia.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na domyślny zestaw katalogów FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne ustawienie domyślne FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Usuwanie katalogu na serwerze FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa usuwa określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **directory_name** Nazwa katalogu do usunięcia.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na usunięcie katalogu FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie katalogu FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Pobierz listę katalogów z serwera FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa pobiera zawartość określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP. Dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów w katalogu. Każdy wpis jest rozdzielony \<cr/lf\> kombinacją. Należy wywołać ***nx_ftp_client_directory_listing_continue*** , aby ukończyć operację pobierania katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **directory_name** Nazwa katalogu, do którego ma zostać pobrana zawartość.
- **packet_ptr** Wskaźnik do wskaźnika pakietu docelowego. Jeśli to się powiedzie, ładunek pakietu będzie zawierać jeden lub więcej wpisów w katalogu.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na listę katalogów FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślna lista katalogów FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- Nie włączono usługi **NX_NOT_ENABLED** (IPv6)
- **NX_FTP_EXPECTED_1XX_CODE** (0xD9) nie otrzymał odpowiedzi 1XX (ok)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Kontynuuj Wyświetlanie listy katalogów z serwera FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa kontynuuje pobieranie zawartości określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP. Powinien być bezpośrednio poprzedzony wywołaniem ***nx_ftp_client_directory_listing_get***. Jeśli to się powiedzie, dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów w katalogu. Ta procedura powinna być wywoływana do momentu otrzymania NX_FTP_END_OF_LISTING stanu.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **packet_ptr** Wskaźnik do wskaźnika pakietu docelowego. Jeśli to się powiedzie, ładunek pakietu będzie zawierać co najmniej jeden wpis w katalogu oddzielony> <CR/LF.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na listę katalogów FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślna lista katalogów FTP.
- **NX_FTP_END_OF_LISTING** (0XD8) nie ma więcej wpisów w tym katalogu.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Rozłącz z serwerem FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa rozłącza wcześniej ustanowione połączenie z serwerem FTP z określonym klientem FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na rozłączenie klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne rozłączenie FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Zamknij plik klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zamyka poprzednio otwarty plik na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na zamknięcie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zamknięcie pliku FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_NOT_OPEN (0xD5)** Plik nie jest otwarty; nie można zamknąć
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Usuń plik na serwerze FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa usuwa określony plik na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **file_name** Nazwa pliku do usunięcia.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na usunięcie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie pliku FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Otwiera plik na serwerze FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa otwiera określony plik — do odczytu lub zapisu — na serwerze FTP, który został wcześniej połączony z określonym wystąpieniem klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **file_name** Nazwa pliku do otwarcia.
- **open_type** **NX_FTP_OPEN_FOR_READ** lub **NX_FTP_OPEN_FOR_WRITE**.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne otwarcie pliku FTP.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ otwarty.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- Klient FTP **NX_FTP_NOT_CLOSED** (0xD6) jest już otwarty.
- **NX_NO_FREE_PORTS** (0X45) Brak dostępnych portów TCP do przypisania
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Odczytaj z pliku

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odczytuje pakiet z wcześniej otwartego pliku. Powinien być wywoływany kilkukrotnie do momentu otrzymania stanu NX_FTP_END_OF_FILE.

Należy zauważyć, że obiekt wywołujący nie przydziela pakietu dla tej usługi.  Musi on dostarczyć jedynie wskaźnik do wskaźnika pakietu. Ta usługa zaktualizuje ten wskaźnik pakietu, aby wskazywał pakiet pobrany z kolejki odbioru gniazda.  Jeśli zwracany jest stan pomyślne, oznacza to, że dostępny jest pakiet i jest on odpowiedzialny za wydanie pakietu po jego zakończeniu.

Jeśli zwracany jest stan o wartości innej niż zero (stan błędu lub NX_FTP_END_OF_FILE), obiekt wywołujący nie zwolni pakietu. W przeciwnym razie zostanie wygenerowany błąd, gdy wskaźnik pakietu ma wartość NULL.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **packet_ptr** Wskaźnik do miejsca docelowego dla wskaźnika pakietu danych, który ma być przechowywany. Jeśli to się powiedzie, pakiet część lub wszystkie zawarte w nim pliki.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na odczytanie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego odczytania pliku FTP.
- Klient FTP **NX_FTP_NOT_OPEN** (0xD5) nie jest otwarty.
- **NX_FTP_END_OF_FILE** (0XD7) koniec warunku pliku.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Zmień nazwę pliku na serwerze FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zmienia nazwę pliku na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **Nazwa pliku** Bieżąca nazwa pliku.
- **new_filename** Nowa nazwa pliku.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na zmianę nazwy pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślna zmiana nazwy pliku FTP.
- Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.
- **NX_FTP_EXPECTED_3XX_CODE** (0XDD) nie otrzymał odpowiedzi 3xx (ok)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Zapisz do pliku

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zapisuje pakiet danych do wcześniej otwartego pliku na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **packet_ptr** Wskaźnik pakietu zawierający dane do zapisu.
- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na zapis pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.
  - **TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zapis pliku FTP.
- Klient FTP **NX_FTP_NOT_OPEN** (0xD5) nie jest otwarty.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Włącz lub wyłącz tryb transferu pasywnego

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a>Opis

Ta usługa włącza tryb transferu pasywnego, jeśli passive_mode_enabled dane wejściowe są ustawione na NX_TRUE na wcześniej utworzonym wystąpieniu klienta FTP, tak że kolejne wywołania odczytu lub zapisu plików (RETR, STOR) lub pobrania listy katalogów (NLST) są wykonywane w trybie transferu. Aby wyłączyć transfer w trybie pasywnym i wrócić do domyślnego zachowania aktywnego trybu transferu, Wywołaj tę funkcję z zestawem danych wejściowych passive_mode_enabled, aby NX_FALSE.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.
- **passive_mode_enabled** Jeśli ustawiona na NX_TRUE, tryb pasywny jest włączony.<br />Jeśli ustawiona na NX_FALSE, tryb pasywny jest wyłączony.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawiono tryb pasywny.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Utwórz serwer FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera FTP w określonym i wcześniej utworzonym wystąpieniu adresu IP NetX. Zwróć uwagę na to, że serwer FTP musi zostać uruchomiony z wywołaniem do ***nx_ftp_server_start*** , aby rozpocząć operację.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.
- **ftp_server_name** Nazwa serwera FTP.
- **ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP NetX. Należy pamiętać, że dla wystąpienia IP może istnieć tylko jeden serwer FTP.
- **media_ptr** Wskaźnik do skojarzonego wystąpienia nośnika FileX.
- **stack_ptr** Wskaźnik do pamięci dla obszaru stosu wewnętrznego wątku serwera FTP.
- **stack_size** Rozmiar obszaru stosu określonego przez *stack_ptr*.
- **pool_ptr** Wskaźnik do domyślnej puli pakietów NetX. Zwróć uwagę, że rozmiar ładunku pakietów w puli musi być wystarczająco duży, aby pomieścić największą nazwę pliku/ścieżkę.
- **ftp_login** Wskaźnik funkcji do funkcji logowania aplikacji. Ta funkcja jest podana nazwa użytkownika i hasło z klienta wysyłającego żądanie połączenia oraz adres klienta w typie danych ULONG. Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.
- **ftp_logout** Wskaźnik funkcji do funkcji wylogowania aplikacji. Ta funkcja jest podana nazwa użytkownika i hasło z klienta żądającego rozłączenia, a adres klienta w typie danych ULONG. Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera FTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a>nxd_ftp_server_create

Tworzenie serwera FTP z obsługą protokołów IPv4 i IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera FTP w określonym i wcześniej utworzonym wystąpieniu adresu IP NetX. Należy pamiętać, że serwer FTP nadal musi zostać uruchomiony z wywołaniem do ***nx_ftp_server_start*** , aby rozpocząć operację po utworzeniu serwera.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.
- **ftp_server_name** Nazwa serwera FTP.
- **ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP NetX. Należy pamiętać, że dla wystąpienia IP może istnieć tylko jeden serwer FTP.
- **media_ptr** Wskaźnik do skojarzonego wystąpienia nośnika FileX.
- **stack_ptr** Wskaźnik do pamięci dla obszaru stosu wewnętrznego wątku serwera FTP.
- **stack_size** Rozmiar obszaru stosu określonego przez *stack_ptr*.
- **pool_ptr** Wskaźnik do domyślnej puli pakietów NetX. Zwróć uwagę, że rozmiar ładunku pakietów w puli musi być wystarczająco duży, aby pomieścić największą nazwę pliku/ścieżkę.
- **ftp_login_duo** Wskaźnik funkcji do funkcji logowania aplikacji. Ta funkcja jest podana nazwa użytkownika i hasło z klienta wysyłającego żądanie połączenia oraz wskaźnik do adresu klienta w NXD_ADDRESS typie danych. Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.
- **ftp_logout_duo** Wskaźnik funkcji do funkcji wylogowania aplikacji. Ta funkcja jest podana nazwa użytkownika i hasło z klienta żądającego rozłączenia oraz wskaźnik do adresu klienta w NXD_ADDRESS typie danych. Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera FTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Usuń serwer FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie serwera FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie serwera FTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Uruchom serwer FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzone wystąpienie serwera FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie serwera FTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Zatrzymaj serwer FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie serwera FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zatrzymywanie serwera FTP.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
