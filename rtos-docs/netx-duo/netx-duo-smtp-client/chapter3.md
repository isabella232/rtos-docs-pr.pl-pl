---
title: Rozdział 3 — Opis klienta usług klienta SMTP
description: Ten rozdział zawiera opis wszystkich usług klienta SMTP NetX Duo (wymienionych poniżej) w kolejności użycia w typowej aplikacji klienckiej SMTP.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bc54e7763c4a3977ef4d760bc92025b1cda792b979d741fc7b82f8f1a3f2901b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797810"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Rozdział 3 — Opis klienta usług klienta SMTP

Ten rozdział zawiera opis wszystkich usług klienta SMTP NetX Duo (wymienionych poniżej) w kolejności użycia w typowej aplikacji klienckiej SMTP.

> [!NOTE]
> W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **_NX_DISABLE_ERROR_CHECKING,_** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.

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

Ta usługa tworzy wystąpienie klienta SMTP w określonym wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SMTP;
- **ip_ptr** Wskaźnik do wystąpienia adresu IP;
- **packet_pool_ptr** Wskaźnik do puli pakietów klienta;
- **nazwa użytkownika** Nazwa użytkownika do uwierzytelniania zakończona wartością NULL**
- **hasło** Hasło do uwierzytelniania z zakończeniem o wartości NULL
- **from_address** Adres nadawcy z zakończeniem o wartości NULL
- **client_domain** Nazwa domeny z zakończoną wartością NULL
- **authentication_type** Typ uwierzytelniania klienta. Obsługiwane typy to:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** Wskaźnik do adresu IP serwera SMTP
- **server_port** Port TCP serwera SMTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) SMTP Client pomyślnie utworzony. Stan tworzenia gniazda TCP
- NX_SMTP_INVALID_PARAM (0xA5) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_IP_ADDRESS_ERROR (0x21) Nieprawidłowy typ adresu IP
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

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

- **client_ptr** Wskaźnik do wystąpienia klienta SMTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie usunięto klienta
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

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

Ta usługa tworzy i wysyła element poczty SMTP. Klient SMTP ustanawia połączenie TCP z serwerem SMTP i wysyła szereg poleceń SMTP. Jeśli nie zostaną napotkane żadne błędy, wiadomość e-mail zostanie przesłana na serwer. Niezależnie od tego, czy wiadomość e-mail została wysłana pomyślnie, spowoduje to zakończenie połączenia TCP i zwrócenie stanu wskazującego wynik przesyłania wiadomości e-mail. Aplikacja może wywołać tę usługę dla tylu wiadomości e-mail, ile musi wysłać bez limitu.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do klienta SMTP
- **recipient_address** Adres odbiorcy z zakończeniem o wartości NULL.
- **temat** Tekst wiersza tematu z zakończeniem o wartości NULL;.
- **priorytet** Poziom priorytetu, na którym jest dostarczana poczta
- **mail_body** Wskaźnik do wiadomości e-mail
- **mail_body_length** Rozmiar wiadomości e-mail

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Wiadomość e-mail została pomyślnie wysłana
- **NX_SMTP_CLIENT_NOT_INITIALIZED** klienta SMTP 0xB2 (0xB2) nie zainicjowane dla stanu sesji SMTP Wynik sesji SMTP
- NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika
- NX_SMTP_INVALID_PARAM (0xA5) Nieprawidłowe dane wejściowe bez wskaźnika
- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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
