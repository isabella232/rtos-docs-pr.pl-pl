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
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="fb5d0-103">Rozdział 3 — Opis usług klienta POP3 usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="fb5d0-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="fb5d0-104">Ten rozdział zawiera opis wszystkich usług klienta POP3 usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="fb5d0-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="fb5d0-106">nx_pop3_client_create: *Tworzenie wystąpienia klienta POP3*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="fb5d0-107">nx_pop3_client_delete: *usuwanie wystąpienia klienta POP3*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="fb5d0-108">nx_pop3_client_ mail_item_get: *usuwanie elementu poczty klienta z serwera maildrop*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="fb5d0-109">nx_pop3_client_mail_item_get: *pobieranie określonego rozmiaru wiadomości e-mail*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="fb5d0-110">nx_pop3_client_mail_items_get: *Uzyskaj liczbę elementów poczty w maildrop*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="fb5d0-111">nx_pop3_client_mail_item_message _get: *Pobierz określoną wiadomość e-mail*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="fb5d0-112">nx_pop3_client_mail_item_size_get: *Uzyskaj rozmiar określonego elementu poczty*</span><span class="sxs-lookup"><span data-stu-id="fb5d0-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="fb5d0-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="fb5d0-113">nx_pop3_client_create</span></span>

<span data-ttu-id="fb5d0-114">Tworzenie wystąpienia klienta POP3</span><span class="sxs-lookup"><span data-stu-id="fb5d0-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-115">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="fb5d0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-116">Description</span></span>

<span data-ttu-id="fb5d0-117">Ta usługa tworzy wystąpienie klienta POP3 i konfiguruje jego konfigurację przy użyciu parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-118">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-118">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-119">**client_ptr**: wskaźnik do klienta do utworzenia</span><span class="sxs-lookup"><span data-stu-id="fb5d0-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="fb5d0-120">**APOP_authentication**: Włączanie uwierzytelniania APOP</span><span class="sxs-lookup"><span data-stu-id="fb5d0-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="fb5d0-121">**ip_ptr**: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="fb5d0-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="fb5d0-122">**packet_pool_ptr**: wskaźnik do puli pakietów klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="fb5d0-123">**server_ip_address**: adres serwera POP3</span><span class="sxs-lookup"><span data-stu-id="fb5d0-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="fb5d0-124">**SERVER_PORT**: Port serwera POP3</span><span class="sxs-lookup"><span data-stu-id="fb5d0-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="fb5d0-125">**CLIENT_NAME**: wskaźnik do nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="fb5d0-126">**client_password**: wskaźnik do hasła klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-127">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-127">Return Values</span></span>

- <span data-ttu-id="fb5d0-128">**NX_SUCCESS**: (0x00) pomyślnie utworzono klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="fb5d0-129">**stan**: zapełnianie stanu dla wywołań usługi NetX i ThreadX</span><span class="sxs-lookup"><span data-stu-id="fb5d0-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="fb5d0-130">NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="fb5d0-131">NX_POP3_PARAM_ERROR: (0xB1) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="fb5d0-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-132">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-132">Allowed From</span></span>

<span data-ttu-id="fb5d0-133">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-134">Example</span></span>

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

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="fb5d0-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="fb5d0-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="fb5d0-136">Usuwanie wystąpienia klienta POP3</span><span class="sxs-lookup"><span data-stu-id="fb5d0-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="fb5d0-138">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-138">Description</span></span>

<span data-ttu-id="fb5d0-139">Ta usługa usuwa wcześniej utworzony klient POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="fb5d0-140">Nie jest to usługa, która nie usuwa puli pakietów klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="fb5d0-141">Aplikacja urządzenia musi usunąć ten zasób oddzielnie, jeśli nie ma już zastosowania do puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-142">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-142">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-143">**client_ptr**: wskaźnik do klienta do usunięcia</span><span class="sxs-lookup"><span data-stu-id="fb5d0-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-144">Return Values</span></span>

- <span data-ttu-id="fb5d0-145">**NX_SUCCESS**: (0x00) pomyślnie usunięto klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="fb5d0-146">NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-147">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-147">Allowed From</span></span>

<span data-ttu-id="fb5d0-148">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="fb5d0-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="fb5d0-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="fb5d0-151">Usuwanie określonego elementu poczty z maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-152">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="fb5d0-153">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-153">Description</span></span>

<span data-ttu-id="fb5d0-154">Ta usługa usuwa określony element poczty z maildrop klienta.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="fb5d0-155">Jest on przeznaczony dla programu po pobraniu elementu poczty, chociaż niektóre serwery POP3 mogą automatycznie usuwać elementy poczty po zażądaniu przez klienta.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-156">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-156">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-157">**client_ptr**: wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="fb5d0-158">**mail_index**: Indeksuj do maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-159">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-159">Return Values</span></span>

- <span data-ttu-id="fb5d0-160">Żądanie usunięcia **NX_SUCCESS**: (0x00) powiodło się</span><span class="sxs-lookup"><span data-stu-id="fb5d0-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="fb5d0-161">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="fb5d0-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="fb5d0-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="fb5d0-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="fb5d0-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) nieprawidłowe dane wejściowe indeksu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="fb5d0-165">NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-166">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-166">Allowed From</span></span>

<span data-ttu-id="fb5d0-167">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="fb5d0-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="fb5d0-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="fb5d0-170">Pobieranie określonego elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-171">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="fb5d0-172">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-172">Description</span></span>

<span data-ttu-id="fb5d0-173">Ta usługa wysyła żądanie RETR do pobrania elementu poczty z maildrop klienta określonego przez indeks mail_item.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="fb5d0-174">Po wykonaniu żądania RETR i otrzymaniu pozytywnej odpowiedzi z serwera klient może rozpocząć pobieranie wiadomości e-mail przy użyciu usługi *nx_pop3_client_mail_item_message_get* .</span><span class="sxs-lookup"><span data-stu-id="fb5d0-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="fb5d0-175">Należy pamiętać, że usługa udostępnia również rozmiar żądanego elementu poczty wyodrębnionego z odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-176">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-176">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-177">**client_ptr**: wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="fb5d0-178">**mail_item**: Indeksuj do maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="fb5d0-179">**item_size**: wskaźnik do rozmiaru wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="fb5d0-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-180">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-180">Return Values</span></span>

- <span data-ttu-id="fb5d0-181">**NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="fb5d0-182">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="fb5d0-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="fb5d0-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="fb5d0-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="fb5d0-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) nieprawidłowe dane wejściowe indeksu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="fb5d0-186">NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-187">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-187">Allowed From</span></span>

<span data-ttu-id="fb5d0-188">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="fb5d0-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="fb5d0-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="fb5d0-191">Pobieranie liczby elementów poczty w maildrop</span><span class="sxs-lookup"><span data-stu-id="fb5d0-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="fb5d0-193">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-193">Description</span></span>

<span data-ttu-id="fb5d0-194">Ta usługa udostępnia żądanie STATnia, aby pobrać liczbę elementów poczty i łączny rozmiar danych wiadomości e-mail z maildrop klienta.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-195">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-195">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-196">**client_ptr**: wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="fb5d0-197">**number_mail_item**: liczba wiadomości w maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="fb5d0-198">**maildrop_total_size**: wskaźnik do rozmiaru całej wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="fb5d0-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-199">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-199">Return Values</span></span>

- <span data-ttu-id="fb5d0-200">**NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="fb5d0-201">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="fb5d0-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="fb5d0-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="fb5d0-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="fb5d0-204">NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-205">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-205">Allowed From</span></span>

<span data-ttu-id="fb5d0-206">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="fb5d0-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="fb5d0-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="fb5d0-209">Pobieranie wiadomości określonego elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-210">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="fb5d0-211">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-211">Description</span></span>

<span data-ttu-id="fb5d0-212">Ta usługa pobiera komunikat elementu poczty, rozmiar wiadomości e-mail i, jeśli jest to ostatni pakiet wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="fb5d0-213">Jeśli `final_packet` jest NX_TRUE pakiet wskazywany przez `recv_packet_ptr` jest pakietem końcowym w wiadomości elementu poczty.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-214">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-214">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-215">**client_ptr**: wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="fb5d0-216">**recv_packet_ptr**: Odebrano pakiet danych komunikatów</span><span class="sxs-lookup"><span data-stu-id="fb5d0-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="fb5d0-217">**number_mail_item**: liczba wiadomości w maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="fb5d0-218">**maildrop_total_size**: wskaźnik do rozmiaru całej wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="fb5d0-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-219">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-219">Return Values</span></span>

- <span data-ttu-id="fb5d0-220">**NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="fb5d0-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="fb5d0-222">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-223">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-223">Allowed From</span></span>

<span data-ttu-id="fb5d0-224">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-225">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="fb5d0-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="fb5d0-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="fb5d0-227">Pobierz rozmiar określonego elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="fb5d0-228">Prototype</span><span class="sxs-lookup"><span data-stu-id="fb5d0-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="fb5d0-229">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5d0-229">Description</span></span>

<span data-ttu-id="fb5d0-230">Ta usługa tworzy żądanie listy w celu uzyskania rozmiaru określonego elementu poczty.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fb5d0-231">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="fb5d0-231">Input Parameters</span></span>

- <span data-ttu-id="fb5d0-232">**client_ptr**: wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="fb5d0-233">**mail_item**: Indeksuj do maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="fb5d0-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="fb5d0-234">**rozmiar**: wskaźnik do rozmiaru wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="fb5d0-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="fb5d0-235">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fb5d0-235">Return Values</span></span>

- <span data-ttu-id="fb5d0-236">**NX_SUCCESS**: (0x00) pomyślnie pobrano element poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="fb5d0-237">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="fb5d0-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="fb5d0-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="fb5d0-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="fb5d0-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="fb5d0-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) nieprawidłowe dane wejściowe indeksu poczty</span><span class="sxs-lookup"><span data-stu-id="fb5d0-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="fb5d0-241">NX_PTR_ERROR: (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="fb5d0-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fb5d0-242">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="fb5d0-242">Allowed From</span></span>

<span data-ttu-id="fb5d0-243">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5d0-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="fb5d0-244">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5d0-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
