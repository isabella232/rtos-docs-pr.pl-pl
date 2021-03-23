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
# <a name="chapter-3---client-description-of-smtp-client-services"></a><span data-ttu-id="c9afb-103">Rozdział 3 — Opis klienta usług klienta SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-103">Chapter 3 - Client description of SMTP Client services</span></span>

<span data-ttu-id="c9afb-104">Ten rozdział zawiera opis wszystkich usług klienta SMTP w programie NetX Duo (wymienionych poniżej) w kolejności użycia w typowej aplikacji klienckiej SMTP.</span><span class="sxs-lookup"><span data-stu-id="c9afb-104">This chapter contains a description of all NetX Duo SMTP Client services (listed below) in order of usage in a typical SMTP Client application.</span></span>

> [!NOTE]
> <span data-ttu-id="c9afb-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **_NX_DISABLE_ERROR_CHECKING_** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c9afb-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **_NX_DISABLE_ERROR_CHECKING_** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nxd_smtp_client_create"></a><span data-ttu-id="c9afb-106">nxd_smtp_client_create</span><span class="sxs-lookup"><span data-stu-id="c9afb-106">nxd_smtp_client_create</span></span>

<span data-ttu-id="c9afb-107">Tworzenie wystąpienia klienta SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-107">Create an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c9afb-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9afb-108">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="c9afb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c9afb-109">Description</span></span>

<span data-ttu-id="c9afb-110">Ta usługa tworzy wystąpienie klienta SMTP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="c9afb-110">This service creates an SMTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9afb-111">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c9afb-111">Input Parameters</span></span>

- <span data-ttu-id="c9afb-112">**client_ptr** Wskaźnik do bloku kontroli klienta SMTP;</span><span class="sxs-lookup"><span data-stu-id="c9afb-112">**client_ptr** Pointer to SMTP Client control block;</span></span>
- <span data-ttu-id="c9afb-113">**ip_ptr** Wskaźnik na wystąpienie IP;</span><span class="sxs-lookup"><span data-stu-id="c9afb-113">**ip_ptr** Pointer to IP instance;</span></span>
- <span data-ttu-id="c9afb-114">**packet_pool_ptr** Wskaźnik do puli pakietów klienta;</span><span class="sxs-lookup"><span data-stu-id="c9afb-114">**packet_pool_ptr** Pointer to Client packet pool;</span></span>
- <span data-ttu-id="c9afb-115">**Nazwa użytkownika** Zakończony zerem \* \* nazwa użytkownika do uwierzytelnienia</span><span class="sxs-lookup"><span data-stu-id="c9afb-115">**username** NULL-terminated\*\* Username for authentication</span></span>
- <span data-ttu-id="c9afb-116">**hasło** Hasło zakończyło się wartością NULL na potrzeby uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="c9afb-116">**password** NULL-terminated password for authentication</span></span>
- <span data-ttu-id="c9afb-117">**from_address** Adres nadawcy zakończony wartością NULL</span><span class="sxs-lookup"><span data-stu-id="c9afb-117">**from_address** NULL-terminated sender’s address</span></span>
- <span data-ttu-id="c9afb-118">**client_domain** Nazwa domeny zakończona wartością NULL</span><span class="sxs-lookup"><span data-stu-id="c9afb-118">**client_domain** NULL-terminated domain name</span></span>
- <span data-ttu-id="c9afb-119">**authentication_type** Typ uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="c9afb-119">**authentication_type** Client authentication type.</span></span> <span data-ttu-id="c9afb-120">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="c9afb-120">Supported types are:</span></span>
  - <span data-ttu-id="c9afb-121">NX_SMTP_CLIENT_AUTH_LOGIN</span><span class="sxs-lookup"><span data-stu-id="c9afb-121">NX_SMTP_CLIENT_AUTH_LOGIN</span></span>
  - <span data-ttu-id="c9afb-122">NX_SMTP_CLIENT_AUTH_PLAIN</span><span class="sxs-lookup"><span data-stu-id="c9afb-122">NX_SMTP_CLIENT_AUTH_PLAIN</span></span>
  - <span data-ttu-id="c9afb-123">NX_SMTP_CLIENT_AUTH_NONE</span><span class="sxs-lookup"><span data-stu-id="c9afb-123">NX_SMTP_CLIENT_AUTH_NONE</span></span>
- <span data-ttu-id="c9afb-124">**server_address** Wskaźnik na adres IP serwera SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-124">**server_address** Pointer to SMTP Server IP address</span></span>
- <span data-ttu-id="c9afb-125">**SERVER_PORT** Port TCP serwera SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-125">**server_port** SMTP Server TCP port</span></span>

### <a name="return-values"></a><span data-ttu-id="c9afb-126">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c9afb-126">Return Values</span></span>

- <span data-ttu-id="c9afb-127">**NX_SUCCESS** (0X00) klient SMTP został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="c9afb-127">**NX_SUCCESS** (0x00) SMTP Client successfully created.</span></span> <span data-ttu-id="c9afb-128">Stan tworzenia gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="c9afb-128">TCP socket creation status</span></span>
- <span data-ttu-id="c9afb-129">NX_SMTP_INVALID_PARAM (0xA5) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c9afb-129">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="c9afb-130">NX_IP_ADDRESS_ERROR (0x21) Nieprawidłowy typ adresu IP</span><span class="sxs-lookup"><span data-stu-id="c9afb-130">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address type</span></span>
- <span data-ttu-id="c9afb-131">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c9afb-131">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9afb-132">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c9afb-132">Allowed From</span></span>

<span data-ttu-id="c9afb-133">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="c9afb-133">Application Code</span></span>

### <a name="example"></a><span data-ttu-id="c9afb-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9afb-134">Example</span></span>

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

## <a name="nx_smtp_client_delete"></a><span data-ttu-id="c9afb-135">nx_smtp_client_delete</span><span class="sxs-lookup"><span data-stu-id="c9afb-135">nx_smtp_client_delete</span></span>

<span data-ttu-id="c9afb-136">Usuwanie wystąpienia klienta SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-136">Delete an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c9afb-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9afb-137">Prototype</span></span>

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="c9afb-138">Opis</span><span class="sxs-lookup"><span data-stu-id="c9afb-138">Description</span></span>

<span data-ttu-id="c9afb-139">Ta usługa usuwa wcześniej utworzone wystąpienie klienta SMTP.</span><span class="sxs-lookup"><span data-stu-id="c9afb-139">This service deletes a previously created SMTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9afb-140">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c9afb-140">Input Parameters</span></span>

- <span data-ttu-id="c9afb-141">**client_ptr** Wskaźnik na wystąpienie klienta SMTP.</span><span class="sxs-lookup"><span data-stu-id="c9afb-141">**client_ptr** Pointer to SMTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9afb-142">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c9afb-142">Return Values</span></span>

- <span data-ttu-id="c9afb-143">Pomyślnie usunięto klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c9afb-143">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="c9afb-144">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c9afb-144">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9afb-145">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c9afb-145">Allowed From</span></span>

<span data-ttu-id="c9afb-146">Wątki</span><span class="sxs-lookup"><span data-stu-id="c9afb-146">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9afb-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9afb-147">Example</span></span>

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a><span data-ttu-id="c9afb-148">nx_smtp_mail_send</span><span class="sxs-lookup"><span data-stu-id="c9afb-148">nx_smtp_mail_send</span></span>

<span data-ttu-id="c9afb-149">Tworzenie i wysyłanie elementu poczty SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-149">Create and send an SMTP mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="c9afb-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9afb-150">Prototype</span></span>

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a><span data-ttu-id="c9afb-151">Opis</span><span class="sxs-lookup"><span data-stu-id="c9afb-151">Description</span></span>

<span data-ttu-id="c9afb-152">Ta usługa tworzy i wysyła element poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="c9afb-152">This service creates and sends an SMTP mail item.</span></span> <span data-ttu-id="c9afb-153">Klient SMTP nawiązuje połączenie TCP z serwerem SMTP i wysyła serię poleceń SMTP.</span><span class="sxs-lookup"><span data-stu-id="c9afb-153">The SMTP Client establishes a TCP connection with the SMTP Server and sends a series of SMTP commands.</span></span> <span data-ttu-id="c9afb-154">Jeśli nie zostaną napotkane żadne błędy, wyśle wiadomość e-mail na serwer.</span><span class="sxs-lookup"><span data-stu-id="c9afb-154">If no errors are encountered, it will transmit the mail message to the Server.</span></span> <span data-ttu-id="c9afb-155">Bez względu na to, czy wiadomość e-mail została pomyślnie wysłana, nastąpi przerwanie połączenia TCP i zwrócenie stanu informującego o wyniku transmisji poczty.</span><span class="sxs-lookup"><span data-stu-id="c9afb-155">Regardless if the mail is sent successfully it will terminate the TCP connection and return a status indicating outcome of the mail transmission.</span></span> <span data-ttu-id="c9afb-156">Aplikacja może wywoływać tę usługę dla tylu wiadomości e-mail, które wymagają wysłania bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="c9afb-156">The application may call this service for as many mail messages as it needs to send without limit.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9afb-157">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c9afb-157">Input Parameters</span></span>

- <span data-ttu-id="c9afb-158">**client_ptr** Wskaźnik do klienta SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-158">**client_ptr** Pointer to SMTP Client</span></span>
- <span data-ttu-id="c9afb-159">**recipient_address** Adres odbiorcy zakończony wartością NULL.</span><span class="sxs-lookup"><span data-stu-id="c9afb-159">**recipient_address** NULL-terminated recipient address.</span></span>
- <span data-ttu-id="c9afb-160">**temat** Tekst wiersza tematu zakończony znakiem NULL;.</span><span class="sxs-lookup"><span data-stu-id="c9afb-160">**subject** NULL-terminated subject line text;.</span></span>
- <span data-ttu-id="c9afb-161">**priorytet** Poziom priorytetu dostarczania poczty</span><span class="sxs-lookup"><span data-stu-id="c9afb-161">**priority** Priority level at which mail is delivered</span></span>
- <span data-ttu-id="c9afb-162">**mail_body** Wskaźnik do wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="c9afb-162">**mail_body** Pointer to mail message</span></span>
- <span data-ttu-id="c9afb-163">**mail_body_length** Rozmiar wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="c9afb-163">**mail_body_length** Size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="c9afb-164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c9afb-164">Return Values</span></span>

- <span data-ttu-id="c9afb-165">Pomyślnie wysłano wiadomość **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c9afb-165">**NX_SUCCESS** (0x00) Mail successfully sent</span></span>
- <span data-ttu-id="c9afb-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) nie zainicjowano wystąpienia klienta SMTP na potrzeby wyniku stanu sesji SMTP dla sesji SMTP</span><span class="sxs-lookup"><span data-stu-id="c9afb-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP Client instance not initialized for SMTP session status Outcome of SMTP session</span></span>
- <span data-ttu-id="c9afb-167">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika</span><span class="sxs-lookup"><span data-stu-id="c9afb-167">NX_PTR_ERROR (0x07) Invalid pointer parameter</span></span>
- <span data-ttu-id="c9afb-168">NX_SMTP_INVALID_PARAM (0xA5) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c9afb-168">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="c9afb-169">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c9afb-169">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9afb-170">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c9afb-170">Allowed From</span></span>

<span data-ttu-id="c9afb-171">Wątki</span><span class="sxs-lookup"><span data-stu-id="c9afb-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9afb-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9afb-172">Example</span></span>

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
