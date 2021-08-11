---
title: Rozdział 3 — Opis Azure RTOS FTP NetX
description: Ten rozdział zawiera opis wszystkich usług FTP Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1aec01088236dcae359c0273a0206c10ea09201eb486478ebd678529413badae
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799459"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a>Rozdział 3 — Opis Azure RTOS FTP NetX

Ten rozdział zawiera opis wszystkich usług FTP Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_ftp_client_connect:** Połączenie *do serwera FTP*
- **nx_ftp_client_create:** Tworzenie *wystąpienia klienta FTP*
- **nx_ftp_client_delete:** *usuwanie wystąpienia klienta FTP*
- **nx_ftp_client_directory_create:** *Tworzenie katalogu na serwerze*
- **nx_ftp_client_directory_default_set:** ustaw *katalog domyślny na serwerze*
- **nx_ftp_client_directory_delete:** Usuwanie *katalogu na serwerze*
- **nx_ftp_client_directory_listing_get:** Pobierz *listę katalogów z serwera*
- **nx_ftp_client_directory_listing_continue:** Kontynuuj *wyświetlanie listy katalogów z serwera*
- **nx_ftp_client_disconnect:** *rozłączanie z serwerem FTP*
- **nx_ftp_client_file_close:** Zamknij *plik klienta*
- **nx_ftp_client_file_delete:** Usuwanie *pliku na serwerze*
- **nx_ftp_client_file_open:** *Otwórz plik klienta*
- **nx_ftp_client_file_read:** Odczyt *z pliku*
- **nx_ftp_client_file_rename:** Zmiana *nazwy pliku na serwerze*
- **nx_ftp_client_file_write:** *zapis do pliku*
- **nx_ftp_server_create:** Tworzenie *serwera FTP*
- **nx_ftp_server_delete:** Usuwanie *serwera FTP*
- **nx_ftp_server_start:** Uruchom *serwer FTP*
- **nx_ftp_server_stop:** *Zatrzymaj serwer FTP*

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Połączenie z serwerem FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa łączy wcześniej utworzone wystąpienie klienta FTP z serwerem FTP pod wskazanym adresem IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **server_ip:** adres IP serwera FTP.
- **username**: nazwa użytkownika klienta do uwierzytelniania.
- **password:** hasło klienta do uwierzytelniania.
- **wait_option:** określa, jak długo usługa będzie czekać na połączenie klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne połączenie FTP.
- **NX_TFTP_EXPECTED_22X_CODE:**(0xDB) Nie otrzymuję odpowiedzi 22X (ok)
- **NX_FTP_EXPECTED_23X_CODE:**(0xDC) Nie otrzymuję odpowiedzi 23X (ok)
- **NX_FTP_EXPECTED_33X_CODE:**(0xDE) Nie otrzymuję odpowiedzi 33X (ok)
- **NX_FTP_NOT_DISCONNECTED:**(0xD4) Klient jest już połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik inout.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.
- NX_IP_ADDRESS_ERROR: (0x21) Nieprawidłowy adres IP.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Tworzenie wystąpienia klienta FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **ftp_client_name:** Nazwa klienta FTP.
- **ip_ptr:** wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **window_size:** anonsowany rozmiar okna dla gniazda TCP tego klienta FTP.
- **pool_ptr:** wskaźnik do domyślnej puli pakietów dla tego klienta FTP. Należy pamiętać, że minimalny ładunek pakietu musi być wystarczająco duży, aby pomieścić pełną ścieżkę i nazwę pliku lub katalogu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie klienta FTP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP, wskaźnik IP lub wskaźnik puli pakietów. wskaźnik hasła.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="example"></a>Przykład

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Usuwanie wystąpienia klienta FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie klienta FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie klienta FTP.
- **NX_FTP_NOT_DISCONNECTED:**(0xD4) Błąd usuwania klienta FTP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Tworzenie katalogu na serwerze FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa tworzy określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **directory_name:** nazwa katalogu do utworzenia.
- **wait_option:** określa, jak długo usługa będzie czekać na utworzenie katalogu FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie katalogu FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok) 
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP. 
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Ustawianie domyślnego katalogu na serwerze FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślny katalog na serwerze FTP, który jest połączony z określonym klientem FTP. Ten katalog domyślny ma zastosowanie tylko do połączenia tego klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **directory_path:** nazwa ścieżki katalogu do ustawienia.
- **wait_option:** określa, jak długo usługa będzie czekać na domyślny katalog FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zestaw domyślny FTP powodzenie.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok) 
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP. 
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Usuwanie katalogu na serwerze FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa usuwa określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **directory_name:** nazwa katalogu do usunięcia.
- **wait_option:** określa, jak długo usługa będzie czekać na usunięcie katalogu FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie katalogu FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok) 
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP. 
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Uzyskiwanie listy katalogów z serwera FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa pobiera zawartość określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP. Dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów katalogu. Każdy wpis jest oddzielony &lt; kombinacją cr/lf\. Aby ***nx_ftp_client_directory_listing_continue*** operację get katalogu, należy nx_ftp_client_directory_listing_continue : .

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **directory_name:** Nazwa katalogu, w którym ma być zawartości.
- **packet_ptr:** wskaźnik do docelowego wskaźnika pakietów. W przypadku powodzenia ładunek pakietu będzie zawierać co najmniej jeden wpis katalogu.
- **wait_option:** określa, jak długo usługa będzie czekać na listę katalogów FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Lista pomyślnych katalogów FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_NOT_ENABLED:** usługa (0x14) (IPv6) nie jest włączona
- **NX_FTP_EXPECTED_1XX_CODE:**(0xD9) Nie otrzymuję odpowiedzi 1XX (ok)
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok)
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Kontynuuj wyświetlanie listy katalogów z serwera FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa kontynuuje pobieranie zawartości określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP. Powinno ono zostać bezpośrednio poprzedzone wywołaniem nx_ftp_client_directory_listing_get ***.*** Jeśli to się powiedzie, dostarczony wskaźnik pakietu będzie zawierać co najmniej jeden wpis w katalogu. Ta procedura powinna być wywoływana do momentu NX_FTP_END_OF_LISTING, gdy zostanie odebrany stan.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **packet_ptr:** wskaźnik do docelowego wskaźnika pakietów. W przypadku powodzenia ładunek pakietu będzie zawierać co najmniej jeden wpis katalogu, oddzielony od siebie &lt; przecinkiem cr/lf. &gt;
- **wait_option:** określa, jak długo usługa będzie czekać na listę katalogów FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Lista pomyślnych katalogów FTP.
- **NX_FTP_END_OF_LISTING:**(0xD8) Nie ma więcej wpisów w tym katalogu.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Nie otrzymuję odpowiedzi 2XX (ok)
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Rozłączanie z serwerem FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa rozłącza wcześniej nawiązane połączenie z serwerem FTP z określonym klientem FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **wait_option:** określa, jak długo usługa będzie czekać na rozłączenie klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne rozłączenie protokołu FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok)
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Zamknij plik klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zamyka wcześniej otwarty plik na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **wait_option:** określa, jak długo usługa będzie czekać na zamknięcie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne zamknięcie pliku FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_NOT_OPEN (0xD5) :** Plik nie jest otwarty; nie można go zamknąć
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok)
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Usuwanie pliku na serwerze FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa usuwa określony plik na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **file_name:** nazwa pliku do usunięcia.
- **wait_option:** określa, jak długo usługa będzie czekać na usunięcie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie pliku FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok)
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Otwiera plik na serwerze FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa otwiera określony plik — do odczytu lub zapisu — na serwerze FTP, który został wcześniej połączony z określonym wystąpieniem klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **file_name:** Nazwa pliku do otwarcia.
- **open_type:** **NX_FTP_OPEN_FOR_READ** lub **NX_FTP_OPEN_FOR_WRITE**.
- **wait_option:** określa, jak długo usługa będzie czekać na otwarcie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślnie otwarty plik FTP.
- **NX_OPTION_ERROR:**(0x0A) Nieprawidłowy typ otwierania.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_NOT_CLOSED:**(0xD6) Klient FTP jest już otwarty.
- **NX_NO_FREE_PORTS:**(0x45) Brak dostępnych portów TCP do przypisania
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Odczyt z pliku

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odczytuje pakiet z wcześniej otwartego pliku. Powinien być wywoływany powtarzalnie do momentu NX_FTP_END_OF_FILE stanu.

Należy pamiętać, że obiekt wywołujący nie przydziela pakietu dla tej usługi.  Potrzebuje tylko wskaźnika do wskaźnika pakietu. Ta usługa zaktualizuje ten wskaźnik pakietów, aby wskazać pakiet pobrany z kolejki odbierania gniazd.  Jeśli zostanie zwrócony stan pomyślny, oznacza to, że dostępny był pakiet, a wywołujący odpowiada za zwolnienie pakietu po jego użyciu.

Jeśli zwracany jest stan niezerowy (stan błędu lub NX_FTP_END_OF_FILE), wywołujący nie zwalnia pakietu. W przeciwnym razie jest generowany błąd, gdy wskaźnik pakietu ma wartość NULL.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **packet_ptr:** Wskaźnik do miejsca docelowego dla wskaźnika pakietu danych pobranego z kolejki. W przypadku powodzenia dane pakietu zawierają część lub wszystkie pliki.
- **wait_option:** określa, jak długo usługa będzie czekać na odczytanie pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślny odczyt pliku FTP.
- **NX_FTP_NOT_OPEN:**(0xD5) Klient FTP nie jest otwarty.
- **NX_FTP_END_OF_FILE:**(0xD7) Warunek końca pliku.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

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

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Zmienianie nazwy pliku na serwerze FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zmienia nazwę pliku na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **filename:** bieżąca nazwa pliku.
- **new_filename:** nowa nazwa pliku.
- **wait_option:** określa, jak długo usługa będzie czekać na zmianę nazwy pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślna zmiana nazwy pliku FTP.
- **NX_FTP_NOT_CONNECTED:**(0xD3) Klient FTP nie jest połączony.
- **NX_FTP_EXPECTED_3XX_CODE:**(0XDD) Nie odedano odpowiedzi 3XX (ok)
- **NX_FTP_EXPECTED_2XX_CODE:**(0xDA) Nie otrzymuję odpowiedzi 2XX (ok)
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Zapis do pliku

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa zapisuje pakiet danych do wcześniej otwartego pliku na serwerze FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **packet_ptr:** wskaźnik pakietu zawierający dane do zapisu.
- **wait_option:** określa, jak długo usługa będzie czekać na zapis pliku klienta FTP. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **wartość limitu czasu:**(0x00000001 do 0xFFFFFFFE)
  - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer FTP nie odpowie na żądanie. Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślny zapis pliku FTP.
- **NX_FTP_NOT_OPEN:**(0xD5) Klient FTP nie jest otwarty.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Włączanie lub wyłączanie pasywnego trybu transferu

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a>Opis

Ta usługa włącza pasywny tryb transferu, jeśli dane wejściowe usługi passive_mode_enabled zostały ustawione na NX_TRUE na wcześniej utworzonym wystąpieniu klienta FTP, tak aby kolejne wywołania odczytu lub zapisu plików (RETR, STOR) lub pobrania listy katalogów (NLST) były wykonywane w trybie transferu. Aby wyłączyć transfer w trybie pasywnym i przywrócić domyślne zachowanie trybu aktywnego transferu, wywołaj tę funkcję z passive_mode_enabled wejściowymi ustawionymi na NX_FALSE.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_client_ptr:** wskaźnik do bloku sterowania klienta FTP.
- **passive_mode_enabled:**
  - Jeśli ustawisz wartość NX_TRUE, tryb pasywny zostanie włączony.
  - Jeśli ustawisz wartość NX_FALSE, tryb pasywny zostanie wyłączony.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Zestaw pomyślnego trybu pasywnego.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.
- NX_INVALID_PARAMETERS: (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Tworzenie serwera FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera FTP w określonym i wcześniej utworzonym wystąpieniu adresu IP NetX. Należy pamiętać, że serwer FTP musi zostać uruchomiony za pomocą wywołania ***nx_ftp_server_start,*** aby rozpocząć działanie.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr:** wskaźnik do bloku sterowania serwera FTP.
- **ftp_server_name:** Nazwa serwera FTP.
- **ip_ptr:** wskaźnik do skojarzonego wystąpienia adresu IP NetX. Należy pamiętać, że dla wystąpienia adresu IP może być tylko jeden serwer FTP.
- **media_ptr:** wskaźnik do skojarzonego wystąpienia nośnika FileX.
- **stack_ptr:** wskaźnik do pamięci dla obszaru stosu wewnętrznego wątku serwera FTP.
- **stack_size:** rozmiar obszaru stosu określony przez *stack_ptr*.
- **pool_ptr:** wskaźnik do domyślnej puli pakietów NetX. Należy pamiętać, że rozmiar ładunku pakietów w puli musi być wystarczająco duży, aby pomieścić największą nazwę pliku/ścieżkę.
- **ftp_login:** Wskaźnik funkcji do funkcji logowania aplikacji. Ta funkcja jest dostarczana z klienta żądającego połączenia nazwy użytkownika i hasła. Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwrócić NX_SUCCESS.
- **ftp_logout:** Wskaźnik funkcji do funkcji wylogowywu aplikacji. Ta funkcja jest dostarczana z klienta z żądaniem rozłączenia nazwy użytkownika i hasła. Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwrócić NX_SUCCESS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie serwera FTP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="example"></a>Przykład

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Usuwanie serwera FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa utworzone wcześniej wystąpienie serwera FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr:** wskaźnik do bloku sterowania serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie serwera FTP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Uruchamianie serwera FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzone wystąpienie serwera FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr:** wskaźnik do bloku sterowania serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne uruchomienie serwera FTP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="example"></a>Przykład

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Zatrzymywanie serwera FTP

### <a name="prototype"></a>Prototype

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje utworzone wcześniej i uruchomione wystąpienie serwera FTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **ftp_server_ptr:** wskaźnik do bloku sterowania serwera FTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne zatrzymanie serwera FTP.
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
