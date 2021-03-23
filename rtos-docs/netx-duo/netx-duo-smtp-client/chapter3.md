---
title: Rozdział 3 — Opis klienta usług klienta SMTP
description: Ten rozdział zawiera opis wszystkich usług klienta SMTP w programie NetX Duo (wymienionych poniżej) w kolejności użycia w typowej aplikacji klienckiej SMTP.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821691"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Rozdział 3 — Opis klienta usług klienta SMTP

Ten rozdział zawiera opis wszystkich usług klienta SMTP w programie NetX Duo (wymienionych poniżej) w kolejności użycia w typowej aplikacji klienckiej SMTP.

> [!NOTE]
> W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **_NX_DISABLE_ERROR_CHECKING_** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

Tworzenie wystąpienia klienta SMTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta SMTP w określonym wystąpieniu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SMTP;
- **ip_ptr** Wskaźnik na wystąpienie IP;
- **packet_pool_ptr** Wskaźnik do puli pakietów klienta;
- **Nazwa użytkownika** Zakończony zerem * * nazwa użytkownika do uwierzytelnienia
- **hasło** Hasło zakończyło się wartością NULL na potrzeby uwierzytelniania
- **from_address** Adres nadawcy zakończony wartością NULL
- **client_domain** Nazwa domeny zakończona wartością NULL
- **authentication_type** Typ uwierzytelniania klienta. Obsługiwane typy to:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** Wskaźnik na adres IP serwera SMTP
- **SERVER_PORT** Port TCP serwera SMTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) klient SMTP został pomyślnie utworzony. Stan tworzenia gniazda TCP
- NX_SMTP_INVALID_PARAM (0xA5) Nieprawidłowa wejściowa niebędąca wskaźnikiem
- NX_IP_ADDRESS_ERROR (0x21) Nieprawidłowy typ adresu IP
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

Usuwanie wystąpienia klienta SMTP

### <a name="prototype"></a>Prototype

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta SMTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik na wystąpienie klienta SMTP.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto klienta **NX_SUCCESS** (0x00)
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

Tworzenie i wysyłanie elementu poczty SMTP

### <a name="prototype"></a>Prototype

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>Opis

Ta usługa tworzy i wysyła element poczty SMTP. Klient SMTP nawiązuje połączenie TCP z serwerem SMTP i wysyła serię poleceń SMTP. Jeśli nie zostaną napotkane żadne błędy, wyśle wiadomość e-mail na serwer. Bez względu na to, czy wiadomość e-mail została pomyślnie wysłana, nastąpi przerwanie połączenia TCP i zwrócenie stanu informującego o wyniku transmisji poczty. Aplikacja może wywoływać tę usługę dla tylu wiadomości e-mail, które wymagają wysłania bez ograniczeń.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do klienta SMTP
- **recipient_address** Adres odbiorcy zakończony wartością NULL.
- **temat** Tekst wiersza tematu zakończony znakiem NULL;.
- **priorytet** Poziom priorytetu dostarczania poczty
- **mail_body** Wskaźnik do wiadomości e-mail
- **mail_body_length** Rozmiar wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie wysłano wiadomość **NX_SUCCESS** (0x00)
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) nie zainicjowano wystąpienia klienta SMTP na potrzeby wyniku stanu sesji SMTP dla sesji SMTP
- NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika
- NX_SMTP_INVALID_PARAM (0xA5) Nieprawidłowa wejściowa niebędąca wskaźnikiem
- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
