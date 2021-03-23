---
title: Rozdział 3 — Opis usług klienta POP3
description: Ten rozdział zawiera opis wszystkich usług klienta POP3 NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821745"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="01698-103">Rozdział 3 — Opis usług klienta POP3</span><span class="sxs-lookup"><span data-stu-id="01698-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="01698-104">Ten rozdział zawiera opis wszystkich usług klienta POP3 NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="01698-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="01698-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="01698-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="01698-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="01698-106">nx_pop3_client_create</span></span>

<span data-ttu-id="01698-107">Tworzenie wystąpienia klienta POP3 dla protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="01698-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="01698-109">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-109">Description</span></span>

<span data-ttu-id="01698-110">Ta usługa tworzy wystąpienie klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="01698-111">Obsługuje tylko adresy serwera POP3 protokołu IPv4.</span><span class="sxs-lookup"><span data-stu-id="01698-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="01698-112">Należy pamiętać, że aplikacja urządzenia musi najpierw utworzyć wystąpienie IP i pulę pakietów dla klienta POP3 do przesyłania pakietów.</span><span class="sxs-lookup"><span data-stu-id="01698-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="01698-113">Ta Pula pakietów została utworzona do użycia wyłącznie przez zadanie klienta POP3 lub tę samą pulę pakietów używaną w tworzeniu wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="01698-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="01698-114">Pula pakietów może być również współdzielona z pulą pakietów sterowników Ethernet, ale jest to wadą użycia dużych pul pakietów, których ładunek jest przeznaczony do otrzymywania ładunku potencjalnie dużych pakietów dla klienta POP3 do wysyłania stosunkowo małych pakietów wiadomości POP3 do serwera.</span><span class="sxs-lookup"><span data-stu-id="01698-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-115">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-115">Input Parameters</span></span>

- <span data-ttu-id="01698-116">**client_ptr** Wskaźnik do klienta do utworzenia</span><span class="sxs-lookup"><span data-stu-id="01698-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="01698-117">**APOP_authentication** Włącz uwierzytelnianie APOP</span><span class="sxs-lookup"><span data-stu-id="01698-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="01698-118">**Ip_ptr wskaźnika** do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="01698-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="01698-119">**packet_pool_ptr** Wskaźnik do puli pakietów klienta</span><span class="sxs-lookup"><span data-stu-id="01698-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="01698-120">**server_ip_address** Adres IPv4 serwera POP3</span><span class="sxs-lookup"><span data-stu-id="01698-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="01698-121">**SERVER_PORT** Port serwera POP3</span><span class="sxs-lookup"><span data-stu-id="01698-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="01698-122">**CLIENT_NAME** Wskaźnik na nazwę klienta</span><span class="sxs-lookup"><span data-stu-id="01698-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="01698-123">**client_password** Wskaźnik na hasło klienta</span><span class="sxs-lookup"><span data-stu-id="01698-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-124">Return Values</span></span>

- <span data-ttu-id="01698-125">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="01698-126">**stan** Kończenie stanu NetX Duo i wywołań usługi ThreadX</span><span class="sxs-lookup"><span data-stu-id="01698-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="01698-127">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="01698-128">NX_POP3_PARAM_ERROR (0xB1) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="01698-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-129">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-129">Allowed From</span></span>

<span data-ttu-id="01698-130">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="01698-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="01698-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="01698-133">Tworzenie wystąpienia klienta POP3 dla protokołu IPv4 lub IPv6</span><span class="sxs-lookup"><span data-stu-id="01698-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-134">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="01698-135">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-135">Description</span></span>

<span data-ttu-id="01698-136">Ta usługa tworzy wystąpienie klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="01698-137">Obsługuje zarówno adresy serwera POP3 protokołu IPv4, jak i IPv6.</span><span class="sxs-lookup"><span data-stu-id="01698-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="01698-138">Aby uzyskać więcej informacji na temat procesu tworzenia klienta POP3, zobacz wcześniej opisaną usługę *nx_pop3_client_create* .</span><span class="sxs-lookup"><span data-stu-id="01698-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-139">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-139">Input Parameters</span></span>

- <span data-ttu-id="01698-140">**client_ptr** Wskaźnik do klienta do utworzenia</span><span class="sxs-lookup"><span data-stu-id="01698-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="01698-141">**APOP_authentication** Włącz uwierzytelnianie APOP</span><span class="sxs-lookup"><span data-stu-id="01698-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="01698-142">**ip_ptr** Wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="01698-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="01698-143">**packet_pool_ptr** Wskaźnik do puli pakietów klienta</span><span class="sxs-lookup"><span data-stu-id="01698-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="01698-144">**server_ip_address** Serwer POP3 IPv6 lub adres IPv4</span><span class="sxs-lookup"><span data-stu-id="01698-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="01698-145">**SERVER_PORT** Port serwera POP3</span><span class="sxs-lookup"><span data-stu-id="01698-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="01698-146">**CLIENT_NAME**  Wskaźnik na nazwę klienta</span><span class="sxs-lookup"><span data-stu-id="01698-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="01698-147">**client_password** Wskaźnik na hasło klienta</span><span class="sxs-lookup"><span data-stu-id="01698-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-148">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-148">Return Values</span></span>

- <span data-ttu-id="01698-149">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="01698-150">**stan** Kończenie stanu NetX Duo i wywołań usługi ThreadX</span><span class="sxs-lookup"><span data-stu-id="01698-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="01698-151">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="01698-152">NX_POP3_PARAM_ERROR (0xB1) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="01698-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-153">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-153">Allowed From</span></span>

<span data-ttu-id="01698-154">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="01698-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="01698-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="01698-157">Usuwanie wystąpienia klienta POP3</span><span class="sxs-lookup"><span data-stu-id="01698-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-158">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="01698-159">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-159">Description</span></span>

<span data-ttu-id="01698-160">Ta usługa usuwa wcześniej utworzony klient POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="01698-161">Nie jest to usługa, która nie usuwa puli pakietów klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="01698-162">Aplikacja urządzenia musi usunąć ten zasób oddzielnie, jeśli nie ma już zastosowania do puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="01698-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-163">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-163">Input Parameters</span></span>

- <span data-ttu-id="01698-164">**client_ptr** Wskaźnik do klienta do usunięcia</span><span class="sxs-lookup"><span data-stu-id="01698-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-165">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-165">Return Values</span></span>

- <span data-ttu-id="01698-166">Pomyślnie usunięto klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="01698-167">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-168">Allowed From</span></span>

<span data-ttu-id="01698-169">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="01698-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="01698-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="01698-172">Usuwanie określonego elementu poczty z maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="01698-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="01698-174">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-174">Description</span></span>

<span data-ttu-id="01698-175">Ta usługa usuwa określony element poczty z maildrop klienta.</span><span class="sxs-lookup"><span data-stu-id="01698-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="01698-176">Jest on przeznaczony dla programu po pobraniu elementu poczty, chociaż niektóre serwery POP3 mogą automatycznie usuwać elementy poczty po zażądaniu przez klienta.</span><span class="sxs-lookup"><span data-stu-id="01698-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-177">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-177">Input Parameters</span></span>

- <span data-ttu-id="01698-178">**client_ptr** Wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="01698-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="01698-179">**mail_index** Indeksuj do maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="01698-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-180">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-180">Return Values</span></span>

- <span data-ttu-id="01698-181">Żądanie usunięcia **NX_SUCCESS** (0x00) zakończyło się pomyślnie</span><span class="sxs-lookup"><span data-stu-id="01698-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="01698-182">**NX_POP3_INVALID_MAIL_ITEM**(0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="01698-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="01698-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="01698-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="01698-185">NX_POP3_CLIENT_INVALID_INDEX (0xB8) nieprawidłowe dane wejściowe indeksu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="01698-186">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-187">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-187">Allowed From</span></span>

<span data-ttu-id="01698-188">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="01698-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="01698-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="01698-191">Pobieranie określonego elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="01698-193">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-193">Description</span></span>

<span data-ttu-id="01698-194">Ta usługa wysyła żądanie RETR do pobrania elementu poczty z maildrop klienta określonego przez indeks mail_item.</span><span class="sxs-lookup"><span data-stu-id="01698-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="01698-195">Po wykonaniu żądania RETR i otrzymaniu pozytywnej odpowiedzi z serwera klient może rozpocząć pobieranie wiadomości e-mail przy użyciu usługi *nx_pop3_client_mail_item_message_get* .</span><span class="sxs-lookup"><span data-stu-id="01698-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="01698-196">Należy pamiętać, że usługa udostępnia również rozmiar żądanego elementu poczty wyodrębnionego z odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="01698-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-197">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-197">Input Parameters</span></span>

- <span data-ttu-id="01698-198">**client_ptr** Wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="01698-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="01698-199">**mail_item** Indeksuj do maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="01698-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="01698-200">**item_size** Wskaźnik do rozmiaru wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="01698-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-201">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-201">Return Values</span></span>

- <span data-ttu-id="01698-202">Pomyślnie pobrano element poczty **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="01698-203">**NX_POP3_INVALID_MAIL_ITEM** (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="01698-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="01698-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="01698-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="01698-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) nieprawidłowe dane wejściowe indeksu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="01698-207">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-208">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-208">Allowed From</span></span>

<span data-ttu-id="01698-209">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-210">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="01698-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="01698-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="01698-212">Pobieranie liczby elementów poczty w maildrop</span><span class="sxs-lookup"><span data-stu-id="01698-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-213">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="01698-214">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-214">Description</span></span>

<span data-ttu-id="01698-215">Ta usługa udostępnia żądanie STATnia, aby pobrać liczbę elementów poczty i łączny rozmiar danych wiadomości e-mail z maildrop klienta.</span><span class="sxs-lookup"><span data-stu-id="01698-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-216">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-216">Input Parameters</span></span>

- <span data-ttu-id="01698-217">**client_ptr** Wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="01698-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="01698-218">**number_mail_item** Liczba wiadomości w maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="01698-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="01698-219">**maildrop_total_size** Wskaźnik do rozmiaru całej wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="01698-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-220">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-220">Return Values</span></span>

- <span data-ttu-id="01698-221">Pomyślnie pobrano element poczty **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="01698-222">**NX_POP3_INVALID_MAIL_ITEM** (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="01698-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="01698-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="01698-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="01698-225">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-226">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-226">Allowed From</span></span>

<span data-ttu-id="01698-227">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-228">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="01698-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="01698-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="01698-230">Pobieranie wiadomości określonego elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-231">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="01698-232">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-232">Description</span></span>

<span data-ttu-id="01698-233">Ta usługa pobiera komunikat elementu poczty, rozmiar wiadomości e-mail i, jeśli jest to ostatni pakiet wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="01698-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="01698-234">Jeśli final_packet jest NX_TRUE pakiet wskazany przez recv_packet_ptr jest ostatnim pakietem w wiadomości elementu poczty.</span><span class="sxs-lookup"><span data-stu-id="01698-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-235">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-235">Input Parameters</span></span>

- <span data-ttu-id="01698-236">**client_ptr** Wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="01698-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="01698-237">**recv_packet_ptr** Odebrano pakiet danych komunikatów</span><span class="sxs-lookup"><span data-stu-id="01698-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="01698-238">**number_mail_item** Liczba wiadomości w maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="01698-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="01698-239">**maildrop_total_size** Wskaźnik do rozmiaru całej wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="01698-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-240">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-240">Return Values</span></span>

- <span data-ttu-id="01698-241">Pomyślnie pobrano element poczty **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="01698-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="01698-243">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-244">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-244">Allowed From</span></span>

<span data-ttu-id="01698-245">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-246">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="01698-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="01698-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="01698-248">Pobierz rozmiar określonego elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="01698-249">Prototype</span><span class="sxs-lookup"><span data-stu-id="01698-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="01698-250">Opis</span><span class="sxs-lookup"><span data-stu-id="01698-250">Description</span></span>

<span data-ttu-id="01698-251">Ta usługa tworzy żądanie listy w celu uzyskania rozmiaru określonego elementu poczty.</span><span class="sxs-lookup"><span data-stu-id="01698-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="01698-252">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="01698-252">Input Parameters</span></span>

- <span data-ttu-id="01698-253">**client_ptr** Wskaźnik do wystąpienia klienta</span><span class="sxs-lookup"><span data-stu-id="01698-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="01698-254">**mail_item** Indeksuj do maildrop klienta</span><span class="sxs-lookup"><span data-stu-id="01698-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="01698-255">**rozmiar** Wskaźnik do rozmiaru wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="01698-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="01698-256">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="01698-256">Return Values</span></span>

- <span data-ttu-id="01698-257">Pomyślnie pobrano element poczty **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="01698-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="01698-258">**NX_POP3_INVALID_MAIL_ITEM** (0XB2) Nieprawidłowy indeks elementu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="01698-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) pakiet klienta jest za mały dla żądania POP3.</span><span class="sxs-lookup"><span data-stu-id="01698-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="01698-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — odpowiedzi serwera ze stanem błędu</span><span class="sxs-lookup"><span data-stu-id="01698-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="01698-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) nieprawidłowe dane wejściowe indeksu poczty</span><span class="sxs-lookup"><span data-stu-id="01698-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="01698-262">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="01698-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="01698-263">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="01698-263">Allowed From</span></span>

<span data-ttu-id="01698-264">Kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="01698-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="01698-265">Przykład</span><span class="sxs-lookup"><span data-stu-id="01698-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
