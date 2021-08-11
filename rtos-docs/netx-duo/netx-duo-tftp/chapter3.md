---
title: Rozdział 3 — Opis Azure RTOS NetX Duo TFTP
description: Ten rozdział zawiera opis wszystkich usług NetX Duo TFTP (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db7b7469bda02597db6428ecbf080b37a095413411eef2abefb1c4804d7bb1d3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799067"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Rozdział 3 — Opis Azure RTOS NetX Duo TFTP

Ten rozdział zawiera opis wszystkich usług NetX Duo TFTP (wymienionych poniżej) w kolejności alfabetycznej. O ile nie określono inaczej, wszystkie usługi obsługują komunikację IPv6 i IPv4.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nxd_tftp_client_file_open:** *Otwórz plik klienta TFTP*

- **nxd_tftp_client_create:** Tworzenie *wystąpienia klienta TFTP*

- **nxd_tftp_client_delete:** Usuwanie *wystąpienia klienta TFTP*

- **nxd_tftp_client_error_info_get:** *uzyskiwanie informacji o błędzie klienta*

- **nxd_tftp_client_file_close:** Zamknij *plik klienta*

- **nxd_tftp_client_file_open:** Otwórz *plik klienta*

- **nxd_tftp_client_file_read:** *odczytywanie bloku z pliku klienta*

- **nxd_tftp_client_file_write:** bloku *zapisu w pliku klienta*

- **nxd_tftp_client_packet_allocate:** *przydzielanie pakietu do zapisu plików klienta*

- **nxd_tftp_client_set_interface:** *ustawianie interfejsu fizycznego dla żądań TFTP*

- **nxd_tftp_server_create:** tworzenie *serwera TFTP*

- **nxd_tftp_server_delete:** Usuwanie *serwera TFTP*

- **nxd_tftp_server_start:** *uruchamianie serwera TFTP*

- **nxd_tftp_server_stop:** *zatrzymywanie serwera TFTP*

> [!NOTE] 
> Odpowiedniki protokołu IPv4 wszystkich wymienionych powyżej usług są dostępne w klientach NetX Duo TFTP Client i Server, np. *nx_tftp_server_create* *i nx_tftp_client_file_open*. Na poniższych stronach znajdują się tylko opisy interfejsu API *"Duo",* np. usługi rozpoczynające się od nxd_ , . Jeśli określono NXD_ADDRESS \* danych wejściowych, równoważny interfejs API IPv4 wywołuje dane wejściowe ULONG. W przeciwnym razie nie ma różnicy w używaniu interfejsu API.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Tworzenie wystąpienia klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta TFTP dla wcześniej utworzonego wystąpienia adresu IP.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że podany adres IP i pula pakietów zostały już utworzone. Ponadto protokół UDP musi być włączony dla wystąpienia adresu IP przed wywołaniem tej usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania klienta TFTP.

- **tftp_client_name** Nazwa tego wystąpienia klienta TFTP

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

- **pool_ptr** Wskaźnik do wystąpienia klienta TFTP puli pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**(0x00) Pomyślne utworzenie TFTP.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Nieprawidłowa lub nieobsługiwana wersja adresu IP

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nie odebrano ACK serwera

- NX_PTR_ERROR (0x16) Nieprawidłowy adres IP, pula lub wskaźnik TFTP.

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

- **NX_SUCCESS** (0x00) Pomyślne usunięcie klienta TFTP.

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Uzyskiwanie informacji o błędzie klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Opis

Ta usługa zwraca ostatni otrzymany kod błędu i ustawia wskaźnik na ciąg błędu wewnętrznego klienta. W warunkach błędu użytkownik może wyświetlić ostatni błąd wysłany przez serwer. Ciąg błędu o wartości null wskazuje, że nie ma żadnego błędu.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.

- **error_code** Wskaźnik do obszaru docelowego dla kodu błędu

- **error_string** Wskaźnik do miejsca docelowego dla ciągu błędu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Uzyskać informacje o pomyślnym błędzie TFTP.  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik klienta TFTP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Zamykanie pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa zamyka wcześniej otwarty plik przez to wystąpienie klienta TFTP. Wystąpienie klienta TFTP może mieć tylko jeden plik otwarty na raz.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.

- **ip_type** Wskaż protokół IP do użycia. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zamknięcie pliku TFTP.

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Otwieranie pliku klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje otworzyć określony plik na serwerze TFTP pod określonym adresem IP. Plik zostanie otwarty do odczytu lub zapisu. 

> [!NOTE] 
> Jest to ograniczone tylko do pakietów IPv4 i jest przeznaczone do obsługi aplikacji NetX TFTP. Zachęcamy deweloperów do przenoszenia aplikacji do odpowiednika "duetu" usługi *nxd_tftp_client_file_open.*

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania TFTP.

- **file_name** Nazwa pliku ASCII, zakończone z wartością NULL i z odpowiednimi informacjami o ścieżce.

- **server_ip_address** Adres TFTP serwera.

- **open_type** Typ otwartego żądania:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta TFTP. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer TFTP nie odpowie na żądanie. 
  
  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera TFTP.

- **ip_type** Wskaż protokół IP do użycia. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie otwarty plik klienta

- **NX_TFTP_NOT_CLOSED** (0xC3) Klient ma już otwarty plik

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nie odebrano żadnego ACK z serwera

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera

- **NX_TFTP_CODE_ERROR** (0x05) Odebrano kod błędu

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

- NX_IP_ADDRESS_ERROR (0x21) Nieprawidłowy adres IP serwera

- NX_OPTION_ERROR (0x0A) Nieprawidłowy typ otwierania

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

Otwieranie pliku klienta TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa próbuje otworzyć określony plik na serwerze TFTP pod określonym adresem IPv6. Plik zostanie otwarty do odczytu lub zapisu.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania TFTP.

- **file_name** Nazwa pliku ASCII, zakończone z wartością NULL i z odpowiednimi informacjami o ścieżce.

- **server_ip_address** Adres TFTP serwera.

- **open_type** Typ otwartego żądania:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta TFTP. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer TFTP nie odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera TFTP.

- **ip_type** Wskaż protokół IP do użycia. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie otwarty plik klienta

- **NX_TFTP_NOT_CLOSED** (0xC3) Klient ma już otwarty plik

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nie odebrano żadnego ACK z serwera

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Nieprawidłowa wersja adresu IP

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera

- **NX_TFTP_CODE_ERROR** (0x05) Odebrano kod błędu

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

- NX_IP_ADDRESS_ERROR (0x21) Nieprawidłowy adres IP serwera

- NX_OPTION_ERROR (0x0A) Nieprawidłowy typ otwierania

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

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

Odczytywanie bloku z pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa odczytuje blok 512-bajtowy z wcześniej otwartego pliku klienta TFTP. Blok zawierający mniej niż 512 bajtów sygnalizuje koniec pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania klienta TFTP.

- **packet_ptr** Miejsce docelowe pakietu zawierającego blok odczytany z pliku.

- **wait_option** Określa, jak długo usługa będzie czekać na ukończenie odczytu. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer TFTP nie odpowie na żądanie.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na wysłanie bloku pliku przez serwer TFTP.

- **ip_type** Wskaż protokół IP do użycia. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne odczytanie bloku klienta

- **NX_TFTP_NOT_OPEN** (0xC3) Określony plik klienta nie jest otwarty do odczytu

- **NX_NO_PACKET** (0x01) Brak pakietów odebranych z serwera.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nie odebrano żadnego ACK z serwera

- **NX_TFTP_END_OF_FILE** (0xC5) Wykryto koniec pliku (nie błąd).

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Nieprawidłowa wersja adresu IP

- **NX_TFTP_CODE_ERROR** (0x05) Odebrano kod błędu

- **NX_TFTP_FAILED** (0xC2) Odebrano nieznany kod TFTP

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Odebrano nieprawidłowy numer bloku

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

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

Zapis bloku w pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa zapisuje blok 512-bajtowy do wcześniej otwartego pliku klienta TFTP. Określenie bloku zawierającego mniej niż 512 bajtów sygnalizuje koniec pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do bloku sterowania klienta TFTP.

- **packet_ptr** Pakiet zawierający blok do zapisu w pliku.

- **wait_option** Określa, jak długo usługa będzie czekać na ukończenie zapisu. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer TFTP nie odpowie na żądanie.
 
  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na wysłanie przez serwer TFTP ACK żądania zapisu.

- **ip_type** Wskaż protokół IP do użycia. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zapis bloku klienta

- **NX_TFTP_NOT_OPEN** (0xC3) Określony plik klienta nie jest otwarty do zapisu

- **NX_TFTP_TIMEOUT** (0xC1) czasu oczekiwania na serwer ACK

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nie odebrano żadnego ACK z serwera

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Nieprawidłowa wersja adresu IP

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera

- **NX_TFTP_CODE_ERROR** (0x05) Odebrano kod błędu

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

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

Przydzielanie pakietu dla zapisu pliku klienta

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Opis

Ta usługa przydziela pakiet UDP z określonej puli pakietów i robi miejsce na 4-bajtowy nagłówek TFTP, zanim pakiet zostanie zwrócony do wywołującego. Następnie wywołujący może utworzyć bufor do zapisu w pliku klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **pool_ptr** Wskaźnik do puli pakietów.

- **packet_ptr** Miejsce docelowe wskaźnika do przydzielonego pakietu.

- **wait_option** Określa, jak długo usługa będzie czekać na ukończenie przydzielania pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:

  **wartość limitu czasu** (0x00000001 do 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony do momentu zakończenia alokacji.

  Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na alokację pakietów.

- **ip_type** Wskaż protokół IP do użycia. Prawidłowe opcje to IPv4 (4) lub IPv6 (6).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przydzielenie pakietu

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

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
> Aby korzystać z tej usługi, rozwiązanie NetX Duo musi obsługiwać adresowanie wieloadresowe (w wersji 5.6 lub nowszej).

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_client_ptr** Wskaźnik do wystąpienia klienta TFTP

- **if_index** Indeks interfejsu fizycznego do użycia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono interfejs (0x0B) Nieprawidłowe dane wejściowe interfejsu

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

- NX_TFTP_INVALID_INTERFACE (0x0B) Nieprawidłowe dane wejściowe interfejsu

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

Tworzenie serwera TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy serwer TFTP, który odpowiada na żądania klientów TFTP na porcie 69. Serwer musi zostać uruchomiony przez kolejne wywołanie nxd_tftp_server_start *.*

> [!IMPORTANT]
> Aplikacja musi upewnić się, że podane wystąpienie adresu IP, pula pakietów i wystąpienie nośnika FileX zostały już utworzone. Ponadto protokół UDP musi być włączony dla wystąpienia adresu IP przed wywołaniem tej usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwera TFTP.

- **tftp_server_name** Nazwa tego wystąpienia serwera TFTP

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

- **media_ptr** Wskaźnik do wystąpienia nośnika FileX.

- **stack_ptr** Wskaźnik do obszaru stosu serwera TFTP.

- **stack_size** Liczba bajtów w stosie serwera TFTP.

- **pool_ptr** Wskaźnik do puli pakietów TFTP. 

> [!NOTE]
> Dostarczona pula musi mieć ładunki pakietów o rozmiarze co najmniej 580 bajtów. <sup>1</sup>

<sup>1</sup> Część danych pakietu to dokładnie 512 bajtów, ale rozmiar ładunku pakietu musi być co najmniej 572 bajty. Pozostałe bajty są używane dla nagłówków UDP, IPv6 i Ethernet oraz potencjalnych bajtów na końcowej stronie wymaganych przez sterownik do wyrównania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie serwera

- **NX_TFTP_POOL_ERROR** (0xC6) Rozmiar pakietu puli pakietów jest mniejszy niż 560 bajtów

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

Usuwanie serwera TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzony serwer TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwera TFTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie serwera

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

Uruchamianie serwera TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzony serwer TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwera TFTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uruchomienie serwera

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy .
 
### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

Zatrzymywanie serwera TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje wcześniej utworzony serwer TFTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **tftp_server_ptr** Wskaźnik do bloku sterowania serwera TFTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie serwera

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```