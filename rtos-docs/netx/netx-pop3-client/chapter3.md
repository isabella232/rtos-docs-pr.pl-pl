---
title: Rozdział 3 — Opis usług klienta POP3 usługi Azure RTO NetX
description: Ten rozdział zawiera opis wszystkich usług klienta POP3 usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822566"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a>Rozdział 3 — Opis usług klienta POP3 usługi Azure RTO NetX

Ten rozdział zawiera opis wszystkich usług klienta POP3 usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- nx_pop3_client_create: *Tworzenie wystąpienia klienta POP3*
- nx_pop3_client_delete: *usuwanie wystąpienia klienta POP3*
- nx_pop3_client_ mail_item_get: *usuwanie elementu poczty klienta z serwera maildrop*
- nx_pop3_client_mail_item_get: *pobieranie określonego rozmiaru wiadomości e-mail*
- nx_pop3_client_mail_items_get: *Uzyskaj liczbę elementów poczty w maildrop*
- nx_pop3_client_mail_item_message _get: *Pobierz określoną wiadomość e-mail*
- nx_pop3_client_mail_item_size_get: *Uzyskaj rozmiar określonego elementu poczty*

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

- **client_ptr**: wskaźnik do klienta do utworzenia
- **APOP_authentication**: Włączanie uwierzytelniania APOP
- **ip_ptr**: wskaźnik do wystąpienia adresu IP
- **packet_pool_ptr**: wskaźnik do puli pakietów klienta
- **server_ip_address**: adres serwera POP3
- **SERVER_PORT**: Port serwera POP3
- **CLIENT_NAME**: wskaźnik do nazwy klienta
- **client_password**: wskaźnik do hasła klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie utworzono klienta
- **stan**: zapełnianie stanu dla wywołań usługi NetX i ThreadX
- NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego
- NX_POP3_PARAM_ERROR: (0xB1) nieprawidłowe dane wejściowe bez wskaźnika

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

Ta usługa usuwa wcześniej utworzony klient POP3. Nie jest to usługa, która nie usuwa puli pakietów klienta POP3. Aplikacja urządzenia musi usunąć ten zasób oddzielnie, jeśli nie ma już zastosowania do puli pakietów.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do klienta do usunięcia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie usunięto klienta
- NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Usuwanie określonego elementu poczty z maildrop klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a>Opis

Ta usługa usuwa określony element poczty z maildrop klienta. Jest on przeznaczony dla programu po pobraniu elementu poczty, chociaż niektóre serwery POP3 mogą automatycznie usuwać elementy poczty po zażądaniu przez klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do wystąpienia klienta
- **mail_index**: Indeksuj do maildrop klienta

### <a name="return-values"></a>Wartości zwrócone

- Żądanie usunięcia **NX_SUCCESS**: (0x00) powiodło się
- **NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) nieprawidłowe dane wejściowe indeksu poczty
- NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego

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

Pobieranie określonego elementu poczty

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie RETR do pobrania elementu poczty z maildrop klienta określonego przez indeks mail_item. Po wykonaniu żądania RETR i otrzymaniu pozytywnej odpowiedzi z serwera klient może rozpocząć pobieranie wiadomości e-mail przy użyciu usługi *nx_pop3_client_mail_item_message_get* . Należy pamiętać, że usługa udostępnia również rozmiar żądanego elementu poczty wyodrębnionego z odpowiedzi serwera.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do wystąpienia klienta
- **mail_item**: Indeksuj do maildrop klienta
- **item_size**: wskaźnik do rozmiaru wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty
- **NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) nieprawidłowe dane wejściowe indeksu poczty
- NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego

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

Pobieranie liczby elementów poczty w maildrop

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a>Opis

Ta usługa udostępnia żądanie STATnia, aby pobrać liczbę elementów poczty i łączny rozmiar danych wiadomości e-mail z maildrop klienta.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do wystąpienia klienta
- **number_mail_item**: liczba wiadomości w maildrop klienta
- **maildrop_total_size**: wskaźnik do rozmiaru całej wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty
- **NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu 
- NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego

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

Pobieranie wiadomości określonego elementu poczty

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a>Opis

Ta usługa pobiera komunikat elementu poczty, rozmiar wiadomości e-mail i, jeśli jest to ostatni pakiet wiadomości e-mail. Jeśli `final_packet` jest NX_TRUE pakiet wskazywany przez `recv_packet_ptr` jest pakietem końcowym w wiadomości elementu poczty.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do wystąpienia klienta
- **recv_packet_ptr**: Odebrano pakiet danych komunikatów
- **number_mail_item**: liczba wiadomości w maildrop klienta
- **maildrop_total_size**: wskaźnik do rozmiaru całej wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty
- **NX_POP3_CLIENT_INVALID_STATE**: (0xB7) pakiet klienta jest za mały dla żądania POP3.
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

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

Pobierz rozmiar określonego elementu poczty

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a>Opis

Ta usługa tworzy żądanie listy w celu uzyskania rozmiaru określonego elementu poczty.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do wystąpienia klienta
- **mail_item**: Indeksuj do maildrop klienta
- **rozmiar**: wskaźnik do rozmiaru wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty
- **NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) nieprawidłowe dane wejściowe indeksu poczty
- NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego

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
