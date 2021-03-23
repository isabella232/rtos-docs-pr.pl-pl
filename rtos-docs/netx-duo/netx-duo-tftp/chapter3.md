---
title: Rozdział 3 — Opis usług Azure RTO NetX Duo TFTP
description: Ten rozdział zawiera opis wszystkich usług NetX Duo TFTP (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821612"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Rozdział 3 — Opis usług Azure RTO NetX Duo TFTP

Ten rozdział zawiera opis wszystkich usług NetX Duo TFTP (wymienionych poniżej) w kolejności alfabetycznej. O ile nie określono inaczej, wszystkie usługi obsługują komunikację IPv6 i IPv4.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nxd_tftp_client_file_open**: *Otwórz plik klienta TFTP*

- **nxd_tftp_client_create**: *Tworzenie wystąpienia klienta TFTP*

- **nxd_tftp_client_delete**: *usuwanie wystąpienia klienta TFTP*

- **nxd_tftp_client_error_info_get**: *Uzyskiwanie informacji o błędzie klienta*

- **nxd_tftp_client_file_close**: *Zamknij plik klienta*

- **nxd_tftp_client_file_open**: *Otwórz plik klienta*

- **nxd_tftp_client_file_read**: *Odczytaj blok z pliku klienta*

- **nxd_tftp_client_file_write**: *Zapisz blok do pliku klienta*

- **nxd_tftp_client_packet_allocate**: *Przydziel pakiet do zapisu pliku klienta*

- **nxd_tftp_client_set_interface**: *Ustaw interfejs fizyczny dla żądań TFTP*

- **nxd_tftp_server_create**: *Utwórz serwer TFTP*

- **nxd_tftp_server_delete**: *usuwanie serwera TFTP*

- **nxd_tftp_server_start**: *Uruchom serwer TFTP*

- **nxd_tftp_server_stop**: *ZAtrzymywanie serwera TFTP*

> [!NOTE] 
> Równoważne wszystkie usługi wymienione powyżej są dostępne w protokole IPv4 klienta i serwera NetX Duo, np. *nx_tftp_server_create* i *nx_tftp_client_file_open*. Na poniższych stronach znajdują się tylko opisy interfejsów API "Duo", np. usługi zaczynające się od *nxd_*. Jeśli określono NXD_ADDRESS \* dane wejściowe, odpowiednik interfejsu API protokołu IPv4 jest wywoływany dla danych wejściowych ulong. W przeciwnym razie nie ma żadnych różnic w korzystaniu z interfejsu API.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Tworzenie wystąpienia klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta TFTP dla utworzonego wcześniej wystąpienia adresu IP.

> [!IMPORTANT]
> Aplikacja musi utworzyć określony adres IP i pulę pakietów, które zostały już utworzone. Ponadto należy włączyć protokół UDP przed wywołaniem tej usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku kontroli klienta TFTP.

- **tftp_client_name** Nazwa tego wystąpienia klienta TFTP

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

- **pool_ptr** Wskaźnik do wystąpienia klienta TFTP puli pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**(0X00) pomyślnie utworzono TFTP.

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) nieprawidłowa lub nieobsługiwana wersja protokołu IP

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera

- Nie odebrano potwierdzenia serwera **NX_TFTP_NO_ACK_RECEIVED** (0x09)

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP, puli lub TFTP.

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

Usuwanie wystąpienia klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie klienta TFTP.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

Pobierz informacje o błędzie klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Opis

Ta usługa zwraca kod ostatniego odebranego błędu i ustawia wskaźnik na wewnętrzny ciąg błędu klienta. W warunkach błędów użytkownik może wyświetlić ostatni błąd wysyłany przez serwer. Pusty ciąg błędu wskazuje, że błąd nie jest obecny.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.

- **error_code** Wskaźnik do obszaru docelowego dla kodu błędu

- **ERROR_STRING** Wskaźnik do miejsca docelowego dla ciągu błędu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiodło się pobieranie informacji o błędzie TFTP.  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik klienta TFTP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

Zamknij plik klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa zamyka poprzednio otwarty plik przez to wystąpienie klienta TFTP. W przypadku wystąpienia klienta TFTP może być otwarty tylko jeden plik naraz.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.

- **ip_type** Wskaż, którego protokołu IP użyć. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zamknięto plik TFTP.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Otwórz plik klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje otworzyć określony plik na serwerze TFTP o określonym adresie IP. Plik zostanie otwarty na potrzeby odczytu lub zapisu. 

> [!NOTE] 
> Jest to ograniczone tylko do pakietów IPv4 i jest przeznaczony do obsługi aplikacji NetX TFTP. Deweloperzy są zachęcani do przenoszenia aplikacji do korzystania z równorzędnej usługi "Duo" *nxd_tftp_client_file_open.*

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania TFTP.

- **file_name** Nazwa pliku ASCII, zakończona zerem i z odpowiednimi informacjami o ścieżce.

- **server_ip_address** Adres TFTP serwera.

- **open_type** Typ żądania otwartego:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta TFTP. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xffffffff) 
  
  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie. 
  
  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera TFTP.

- **ip_type** Wskaż, którego protokołu IP użyć. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne otwarcie pliku klienta

- Klient **NX_TFTP_NOT_CLOSED** (0xC3) ma już otwarty plik

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera

- **NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP serwera

- NX_OPTION_ERROR (0x0A) Nieprawidłowy typ otwarty

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

Otwórz plik klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa próbuje otworzyć określony plik na serwerze TFTP przy użyciu określonego adresu IPv6. Plik zostanie otwarty na potrzeby odczytu lub zapisu.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania TFTP.

- **file_name** Nazwa pliku ASCII, zakończona zerem i z odpowiednimi informacjami o ścieżce.

- **server_ip_address** Adres TFTP serwera.

- **open_type** Typ żądania otwartego:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta TFTP. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xffffffff)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera TFTP.

- **ip_type** Wskaż, którego protokołu IP użyć. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne otwarcie pliku klienta

- Klient **NX_TFTP_NOT_CLOSED** (0xC3) ma już otwarty plik

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) Nieprawidłowa wersja adresu IP

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera

- **NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP serwera

- NX_OPTION_ERROR (0x0A) Nieprawidłowy typ otwarty

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

Odczytaj blok z pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa odczytuje blok 512-bajtowy z wcześniej otwartego pliku klienta TFTP. Blok zawierający mniej niż 512 bajtów sygnalizuje koniec pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku kontroli klienta TFTP.

- **packet_ptr** Lokalizacja docelowa pakietu zawierającego blok odczytany z pliku.

- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na zakończenie odczytu. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xffffffff)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na wysłanie bloku pliku przez serwer TFTP.

- **ip_type** Wskaż, którego protokołu IP użyć. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne odczytanie bloku klienta

- **NX_TFTP_NOT_OPEN** (0XC3) określony plik klienta nie jest otwarty do odczytu

- **NX_NO_PACKET** (0X01) żaden pakiet nie został odebrany z serwera.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera

- Wykryto koniec pliku **NX_TFTP_END_OF_FILE** (0xc5) (nie jest to błąd).

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) Nieprawidłowa wersja adresu IP

- **NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu

- **NX_TFTP_FAILED** (0xC2) odebrano nieznany kod TFTP

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Odebrano nieprawidłowy numer bloku

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

Napisz blok do pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa zapisuje blok 512-bajtowy do wcześniej otwartego pliku klienta TFTP. Określenie bloku zawierającego mniej niż 512 bajtów sygnalizuje koniec pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku kontroli klienta TFTP.

- **packet_ptr** Pakiet zawierający blok do zapisu w pliku.

- **WAIT_OPTION** Określa, jak długo usługa będzie czekać na zakończenie zapisu. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xffffffff)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.
 
  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na wysłanie potwierdzenia dla żądania zapisu przez serwer TFTP.

- **ip_type** Wskaż, którego protokołu IP użyć. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne zapis bloku klienta

- **NX_TFTP_NOT_OPEN** (0XC3) określony plik klienta nie jest otwarty do zapisu

- **NX_TFTP_TIMEOUT** (0XC1) upłynął limit czasu oczekiwania na potwierdzenie serwera

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) Nieprawidłowa wersja adresu IP

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

Przydziel pakiet do zapisu pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa przydziela pakiet UDP z określonej puli pakietów i tworzy miejsce dla 4-bajtowego nagłówka TFTP przed zwróceniem pakietu do obiektu wywołującego. Obiekt wywołujący może następnie utworzyć bufor do zapisu w pliku klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **pool_ptr** Wskaźnik do puli pakietów.

- **packet_ptr** Miejsce docelowe dla wskaźnika do przydzielnego pakietu.

- **WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na zakończenie przydzielenia pakietu. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xffffffff)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu zakończenia alokacji.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na alokację pakietu.

- **ip_type** Wskaż, którego protokołu IP użyć. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przydzielenie pakietu **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

Ustawianie interfejsu fizycznego dla żądań TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>Opis

Ta usługa używa indeksu interfejsu wejściowego do ustawienia interfejsu fizycznego dla klienta TFTP do wysyłania i odbierania pakietów TFTP. Wartość domyślna to zero dla interfejsu podstawowego.

> [!NOTE]
> NetX Duo musi obsługiwać adresy wielodomowe (wersja 3.0 lub nowsza), aby można było korzystać z tej usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wystąpienia klienta TFTP

- **if_index** Indeks interfejsu fizycznego do użycia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił interfejs (0X0B) nieprawidłowe dane wejściowe interfejsu

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_TFTP_INVALID_INTERFACE (0x0B) nieprawidłowe dane wejściowe interfejsu

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

Utwórz serwer TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy serwer TFTP, który odpowiada na żądania klientów TFTP na porcie 69. Serwer musi być uruchomiony przez kolejne wywołanie do *nxd_tftp_server_start*.

> [!IMPORTANT]
> Aplikacja musi wykonać niektóre dostarczone wystąpienie adresu IP, pulę pakietów i wystąpienie nośnika FileX. Ponadto należy włączyć protokół UDP przed wywołaniem tej usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.

- **tftp_server_name** Nazwa tego wystąpienia serwera TFTP

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

- **media_ptr** Wskaźnik na FileX wystąpienie nośnika.

- **stack_ptr** Wskaźnik do obszaru stosu serwera TFTP.

- **stack_size** Liczba bajtów w stosie serwera TFTP.

- **pool_ptr** Wskaźnik do puli pakietów TFTP. 

> [!NOTE]
> Długość dostarczonej puli musi wynosić co najmniej 580 bajtów. <sup>1</sup>

<sup>1</sup> część danych pakietu ma dokładnie 512 bajtów, ale rozmiar ładunku pakietu musi wynosić co najmniej 572 bajtów. Pozostałe bajty są używane dla nagłówków UDP, IPv6 i Ethernet oraz potencjalne bajty końcowe wymagane przez sterownik do wyrównania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie serwera

- Pula pakietów **NX_TFTP_POOL_ERROR** (0xC6) ma rozmiar pakietu mniejszy niż 560 bajtów

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

Usuń serwer TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzony serwer TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie serwera

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

Uruchom serwer TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzony serwer TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie serwera

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.
 
### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

Zatrzymaj serwer TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzyma wcześniej utworzony serwer TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono pomyślne zatrzymywanie serwera **NX_SUCCESS** (0x00)

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```