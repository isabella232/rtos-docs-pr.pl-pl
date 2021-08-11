---
title: Rozdział 3 — opis Azure RTOS klienta NetX POP3
description: Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX POP3 (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f68d6ac942c829dbf6eb9be334328b1b58a47ea370a73d37f471ec32cd46a360
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782391"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a>Rozdział 3 — opis Azure RTOS klienta NetX POP3

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX POP3 (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

- nx_pop3_client_create: tworzenie *wystąpienia klienta POP3*
- nx_pop3_client_delete: *Usuwanie wystąpienia klienta POP3*
- nx_pop3_client_ mail_item_get: *Usuwanie elementu poczty klienta z usługi Poczta serwera*
- nx_pop3_client_mail_item_get: pobieranie *określonego rozmiaru wiadomości e-mail*
- nx_pop3_client_mail_items_get: Uzyskiwanie *liczby elementów poczty e-mail w wiadomości e-mail*
- nx_pop3_client_mail_item_message _get: pobieranie *określonej wiadomości e-mail*
- nx_pop3_client_mail_item_size_get: uzyskiwanie *rozmiaru określonego elementu poczty e-mail*

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

Tworzenie wystąpienia klienta POP3

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta POP3 i konfiguruje jego konfigurację przy użyciu parametrów wejściowych.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do klienta do utworzenia
- **APOP_authentication:** Włączanie uwierzytelniania APOP
- **ip_ptr:** wskaźnik do wystąpienia adresu IP
- **packet_pool_ptr:** Wskaźnik do puli pakietów klienta
- **server_ip_address:** adres serwera POP3
- **server_port:** port serwera POP3
- **client_name:** Wskaźnik do nazwy klienta
- **client_password:** Wskaźnik do hasła klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślnie utworzono klienta
- **status:** Uzupełnianie stanu wywołań usług NetX i ThreadX
- NX_PTR_ERROR: (0x07) Nieprawidłowy parametr wskaźnika wejściowego
- NX_POP3_PARAM_ERROR: (0xB1) Nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

Usuwanie wystąpienia klienta POP3

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzonego klienta POP3. Nie oznacza to, że ta usługa nie usuwa puli pakietów klienta POP3. Aplikacja urządzenia musi usunąć ten zasób oddzielnie, jeśli nie ma już użycia dla puli pakietów.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do klienta do usunięcia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Klient został pomyślnie usunięty
- NX_PTR_ERROR: (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Usuwanie określonego elementu poczty e-mail z listy maildrop klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a>Opis

Ta usługa usuwa określony element poczty e-mail z listy maildrop klienta. Jest on przeznaczony do użytku po pobraniu elementu poczty e-mail, chociaż niektóre serwery POP3 mogą automatycznie usuwać elementy poczty po zażądaniu przez klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do wystąpienia klienta
- **mail_index:** Indeksowanie do poczty klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Żądanie usunięcia powiodło się
- **NX_POP3_INVALID_MAIL_ITEM:**(0xB2) Nieprawidłowy indeks elementów poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD:**(0xB6) Ładunek pakietu klienta jest zbyt mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS:**(0xB4) Serwer odpowiada ze stanem błędu
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Nieprawidłowe dane wejściowe indeksu poczty
- NX_PTR_ERROR: (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

Pobieranie określonego elementu poczty e-mail

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie RETR w celu pobrania elementu poczty z adresu e-mail klienta określonego przez indeks mail_item. Po otrzymaniu żądania RETR i otrzymaniu pozytywnej odpowiedzi z serwera klient może rozpocząć pobieranie wiadomości e-mail przy użyciu *nx_pop3_client_mail_item_message_get* usługi. Należy pamiętać, że usługa dostarcza również rozmiar żądanego elementu poczty wyodrębniony z odpowiedzi serwera.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do wystąpienia klienta
- **mail_item:** indeksowanie do poczty klienta
- **item_size:** Wskaźnik do rozmiaru wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Element poczty został pomyślnie pobrany
- **NX_POP3_INVALID_MAIL_ITEM:**(0xB2) Nieprawidłowy indeks elementów poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD:**(0xB6) Ładunek pakietu klienta jest zbyt mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS:**(0xB4) Serwer odpowiada ze stanem błędu
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Nieprawidłowe dane wejściowe indeksu poczty
- NX_PTR_ERROR: (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

Pobieranie liczby elementów poczty e-mail w wiadomości e-mail

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie STAT w celu pobrania liczby elementów poczty e-mail i całkowitego rozmiaru danych wiadomości e-mail z usługi maildrop klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do wystąpienia klienta
- **number_mail_item:** Liczba wiadomości e-mail w maildrop klienta
- **maildrop_total_size:** Wskaźnik do rozmiaru całej wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Element poczty został pomyślnie pobrany
- **NX_POP3_INVALID_MAIL_ITEM:**(0xB2) Nieprawidłowy indeks elementów poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD:**(0xB6) Ładunek pakietu klienta jest zbyt mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS:**(0xB4) Serwer odpowiada ze stanem błędu 
- NX_PTR_ERROR: (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

Pobieranie określonej wiadomości e-mail elementu

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a>Opis

Ta usługa pobiera wiadomość e-mail, rozmiar wiadomości e-mail oraz informacje o tym, czy jest to ostatni pakiet wiadomości e-mail. Jeśli `final_packet` jest NX_TRUE wskazywany przez pakiet jest ostatnim `recv_packet_ptr` pakietem w wiadomości e-mail elementu.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do wystąpienia klienta
- **recv_packet_ptr:** Odebrano pakiet danych komunikatów
- **number_mail_item:** Liczba wiadomości e-mail w maildrop klienta
- **maildrop_total_size:** Wskaźnik do rozmiaru całej wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Element poczty został pomyślnie pobrany
- **NX_POP3_CLIENT_INVALID_STATE:**(0xB7) Ładunek pakietu klienta jest zbyt mały dla żądania POP3.
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

Pobieranie rozmiaru określonego elementu poczty e-mail

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie LIST w celu uzyskania rozmiaru określonego elementu poczty e-mail.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** Wskaźnik do wystąpienia klienta
- **mail_item:** indeksowanie do poczty klienta
- **rozmiar:** wskaźnik do rozmiaru wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Element poczty został pomyślnie pobrany
- **NX_POP3_INVALID_MAIL_ITEM:**(0xB2) Nieprawidłowy indeks elementów poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD:**(0xB6) Ładunek pakietu klienta jest zbyt mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS:**(0xB4) Serwer odpowiada ze stanem błędu
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Nieprawidłowe dane wejściowe indeksu poczty
- NX_PTR_ERROR: (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
