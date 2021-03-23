---
title: Rozdział 3 — Opis usług HTTP usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług HTTP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej z wyjątkiem "NetX" (tylko IPv4) równoważnej tej samej usłudze.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821871"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="02a7a-103">Rozdział 3 — Opis usług HTTP usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="02a7a-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="02a7a-104">Ten rozdział zawiera opis wszystkich usług HTTP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej z wyjątkiem "NetX" (tylko IPv4) równoważnej tej samej usłudze.</span><span class="sxs-lookup"><span data-stu-id="02a7a-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="02a7a-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości POGRUBIONe **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="02a7a-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="02a7a-106">**Usługi klienta HTTP:**</span><span class="sxs-lookup"><span data-stu-id="02a7a-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="02a7a-107">**nx_http_client_create** *utworzyć wystąpienia klienta http*</span><span class="sxs-lookup"><span data-stu-id="02a7a-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="02a7a-108">**nx_http_client_delete** *usunąć wystąpienia klienta http*</span><span class="sxs-lookup"><span data-stu-id="02a7a-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="02a7a-109">**nx_http_client_get_start** *uruchomić żądania HTTP GET (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="02a7a-110">**nx_http_client_get_start_extended** *uruchomić żądania HTTP GET (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="02a7a-111">**nxd_http_client_get_start** *uruchomić żądania HTTP GET (IPv4 lub IPv6)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="02a7a-112">**nxd_http_client_get_start_extended** *uruchomić żądania HTTP GET (IPv4 lub IPv6)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="02a7a-113">**nx_http_client_get_packet** *Pobierz następny pakiet danych zasobów*</span><span class="sxs-lookup"><span data-stu-id="02a7a-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="02a7a-114">**nx_http_client_put_start** *uruchomić żądanie HTTP Put (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="02a7a-115">**nx_http_client_put_start_extended** *uruchomić żądanie HTTP Put (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="02a7a-116">**nxd_http_client_put_start** *uruchomić żądania HTTP Put (IPv4 lub IPv6)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="02a7a-117">**nxd_http_client_put_start_extended** *uruchomić żądania HTTP Put (IPv4 lub IPv6)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="02a7a-118">**nx_http_client_put_packet** *Wyślij następny pakiet danych zasobu*</span><span class="sxs-lookup"><span data-stu-id="02a7a-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="02a7a-119">**nx_http_client_set_connect_port** *zmienić portu w celu nawiązania połączenia z serwerem HTTP*</span><span class="sxs-lookup"><span data-stu-id="02a7a-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="02a7a-120">**Usługi serwera HTTP:**</span><span class="sxs-lookup"><span data-stu-id="02a7a-120">**HTTP server services:**</span></span>

- <span data-ttu-id="02a7a-121">**nx_http_server_cache_info_callback_set** *ustawić wywołania zwrotnego, aby pobrać wiek i datę ostatniej modyfikacji określonego adresu URL*</span><span class="sxs-lookup"><span data-stu-id="02a7a-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="02a7a-122">**nx_http_server_callback_data_send** *wysyłać danych http z funkcji wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="02a7a-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="02a7a-123">**nx_http_server_callback_generate_response_header** *utworzyć nagłówka odpowiedzi w funkcjach wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="02a7a-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="02a7a-124">**nx_http_server_callback_generate_response_header_extended** *utworzyć nagłówka odpowiedzi w funkcjach wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="02a7a-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="02a7a-125">**nx_http_server_callback_packet_send** *wysłać pakietu http z wywołania zwrotnego http*</span><span class="sxs-lookup"><span data-stu-id="02a7a-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="02a7a-126">**nx_http_server_callback_response_send** *wysyłanie odpowiedzi z funkcji wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="02a7a-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="02a7a-127">**nx_http_server_callback_response_send_extended** *wysyłanie odpowiedzi z funkcji wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="02a7a-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="02a7a-128">**nx_http_server_content_get** *pobrać zawartości z żądania*</span><span class="sxs-lookup"><span data-stu-id="02a7a-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="02a7a-129">**nx_http_server_content_get_extended** *pobrać zawartości z żądania; obsługuje puste (zerowe długości zawartości)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="02a7a-130">**nx_http_server_content_length_get** *uzyskać długość zawartości w żądaniu*</span><span class="sxs-lookup"><span data-stu-id="02a7a-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="02a7a-131">**nx_http_server_content_length_get_extended** *uzyskać długość zawartości w żądaniu; obsługuje puste (zerowe długości zawartości)*</span><span class="sxs-lookup"><span data-stu-id="02a7a-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="02a7a-132">**nx_http_server_create** *utworzyć wystąpienia serwera http*</span><span class="sxs-lookup"><span data-stu-id="02a7a-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="02a7a-133">**nx_http_server_delete** \* usuwanie wystąpienia serwera http \*</span><span class="sxs-lookup"><span data-stu-id="02a7a-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="02a7a-134">**nx_http_server_get_entity_content** *zwracanie rozmiaru i lokalizacji zawartości jednostki w adresie URL*</span><span class="sxs-lookup"><span data-stu-id="02a7a-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="02a7a-135">**nx_http_server_get_entity_header** *Wyodrębnij nagłówka jednostki adresów URL do określonego buforu*</span><span class="sxs-lookup"><span data-stu-id="02a7a-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="02a7a-136">**nx_http_server_gmt_callback_set** *ustawić wywołania zwrotnego, aby pobrać datę i godzinę GMT*</span><span class="sxs-lookup"><span data-stu-id="02a7a-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="02a7a-137">**nx_http_server_invalid_userpassword_notify_set** *ustawić wywołania zwrotnego dla momentu odebrania nieprawidłowej nazwy użytkownika i hasła w żądaniu klienta*</span><span class="sxs-lookup"><span data-stu-id="02a7a-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="02a7a-138">**nx_http_server_mime_maps_additional_set** *zdefiniować dodatkowe mapy MIME dla HTML*</span><span class="sxs-lookup"><span data-stu-id="02a7a-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="02a7a-139">**nx_http_server_packet_content_find** *Wyodrębnij długość zawartości w nagłówku HTTP i ustaw wskaźnik na początek danych zawartości*</span><span class="sxs-lookup"><span data-stu-id="02a7a-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="02a7a-140">**nx_http_server_packet_get** *odebrać pakiet klienta bezpośrednio*</span><span class="sxs-lookup"><span data-stu-id="02a7a-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="02a7a-141">**nx_http_server_param_get** *uzyskać parametru z żądania*</span><span class="sxs-lookup"><span data-stu-id="02a7a-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="02a7a-142">**nx_http_server_query_get** *uzyskać zapytania z żądania*</span><span class="sxs-lookup"><span data-stu-id="02a7a-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="02a7a-143">**nx_http_server_start** *uruchomić serwer http*</span><span class="sxs-lookup"><span data-stu-id="02a7a-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="02a7a-144">**nx_http_server_stop** *zatrzymać serwer http*</span><span class="sxs-lookup"><span data-stu-id="02a7a-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="02a7a-145">**nx_http_server_type_get (przestarzałe)** *WYODRĘBNIj typ http, np. Text/zwykły z nagłówka*</span><span class="sxs-lookup"><span data-stu-id="02a7a-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="02a7a-146">**nx_http_server_type_get_extended** *WYODRĘBNIj typu http, np. Text/zwykły z nagłówka*</span><span class="sxs-lookup"><span data-stu-id="02a7a-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="02a7a-147">**nx_http_server_digest_authenticate_notify_set** *Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego*</span><span class="sxs-lookup"><span data-stu-id="02a7a-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="02a7a-148">**nx_http_server_authentication_check_set** *Ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania*</span><span class="sxs-lookup"><span data-stu-id="02a7a-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="02a7a-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="02a7a-149">nx_http_client_create</span></span>

<span data-ttu-id="02a7a-150">Tworzenie wystąpienia klienta PPPoE</span><span class="sxs-lookup"><span data-stu-id="02a7a-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-151">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-152">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-152">Description</span></span>

<span data-ttu-id="02a7a-153">Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-154">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-154">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-155">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-156">**CLIENT_NAME** Nazwa wystąpienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="02a7a-157">**ip_ptr** Wskaźnik na wystąpienie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="02a7a-158">**pool_ptr** Wskaźnik do domyślnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="02a7a-159">Należy pamiętać, że pakiety w tej puli muszą mieć wystarczającą ilość ładunku, aby obsłużyć pełny nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="02a7a-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="02a7a-160">Jest on definiowany przez NX_HTTP_CLIENT_MIN_PACKET_SIZE w *nx_http. h*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="02a7a-161">**window_size** Rozmiar okna odbierania gniazda TCP klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-162">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-162">Return Values</span></span>

 - <span data-ttu-id="02a7a-163">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta http</span><span class="sxs-lookup"><span data-stu-id="02a7a-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="02a7a-164">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="02a7a-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="02a7a-165">NX_HTTP_POOL_ERROR (0xE9) Nieprawidłowy rozmiar ładunku w puli pakietów</span><span class="sxs-lookup"><span data-stu-id="02a7a-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-166">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-166">Allowed From</span></span>

<span data-ttu-id="02a7a-167">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="02a7a-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="02a7a-169">nx_http_client_delete</span></span>

<span data-ttu-id="02a7a-170">Usuwanie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-171">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-172">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-172">Description</span></span>

<span data-ttu-id="02a7a-173">Ta usługa usuwa poprzednio utworzone wystąpienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-174">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-174">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-175">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-176">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-176">Return Values</span></span>

 - <span data-ttu-id="02a7a-177">**NX_SUCCESS** (0X00) pomyślne usunięcie klienta http</span><span class="sxs-lookup"><span data-stu-id="02a7a-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="02a7a-178">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="02a7a-179">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-180">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-180">Allowed From</span></span>

<span data-ttu-id="02a7a-181">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-182">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="02a7a-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="02a7a-183">nx_http_client_get_start</span></span>

<span data-ttu-id="02a7a-184">Rozpocznij żądanie HTTP GET za pośrednictwem protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="02a7a-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-185">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-186">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-186">Description</span></span>

<span data-ttu-id="02a7a-187">Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "Resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="02a7a-188">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-189">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="02a7a-190">Ta usługa działa tylko za pośrednictwem sieci IPv4.</span><span class="sxs-lookup"><span data-stu-id="02a7a-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="02a7a-191">W przypadku aplikacji, które muszą łączyć się z siecią IPv6, należy użyć *nxd_http_client_get_start_extended ()* .</span><span class="sxs-lookup"><span data-stu-id="02a7a-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="02a7a-192">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-192">This service is deprecated.</span></span> <span data-ttu-id="02a7a-193">Deweloperzy są zachęcani do migracji do *nx_http_client_get_start_extended ()* lub *nxd_http_client_get_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-194">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-194">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-195">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-196">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-197">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-198">**input_ptr** Wskaźnik na dodatkowe dane żądania GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="02a7a-199">Jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="02a7a-199">This is optional.</span></span> <span data-ttu-id="02a7a-200">Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.</span><span class="sxs-lookup"><span data-stu-id="02a7a-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="02a7a-201">**input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="02a7a-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="02a7a-202">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-203">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-204">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="02a7a-205">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="02a7a-206">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-207">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-208">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-209">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-210">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-210">Return Values</span></span>

 - <span data-ttu-id="02a7a-211">**NX_SUCCESS** (0X00) pomyślnie wysłał klienta http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="02a7a-212">Pobierz komunikat startowy.</span><span class="sxs-lookup"><span data-stu-id="02a7a-212">GET start message.</span></span>
 - <span data-ttu-id="02a7a-213">Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="02a7a-214">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-215">**NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-216">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="02a7a-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="02a7a-217">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-218">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="02a7a-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-219">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-219">Allowed From</span></span>

<span data-ttu-id="02a7a-220">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-221">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-221">Example</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="02a7a-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="02a7a-223">Rozpocznij żądanie HTTP GET za pośrednictwem protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="02a7a-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-224">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-225">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-225">Description</span></span>

<span data-ttu-id="02a7a-226">Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "Resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="02a7a-227">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-228">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="02a7a-229">Ta usługa działa tylko za pośrednictwem sieci IPv4.</span><span class="sxs-lookup"><span data-stu-id="02a7a-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="02a7a-230">W przypadku aplikacji, które muszą łączyć się z siecią IPv6, należy użyć *nxd_http_client_get_start_extended ()* .</span><span class="sxs-lookup"><span data-stu-id="02a7a-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="02a7a-231">Ta usługa zastępuje *nx_http_client_get_start ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="02a7a-232">Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="02a7a-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-233">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-233">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-234">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-235">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-236">**wskaźnik zasobu** do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-237">**resource_length** Długość ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-238">**input_ptr** Wskaźnik na dodatkowe dane żądania GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="02a7a-239">Jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="02a7a-239">This is optional.</span></span> <span data-ttu-id="02a7a-240">Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.</span><span class="sxs-lookup"><span data-stu-id="02a7a-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="02a7a-241">**input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="02a7a-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="02a7a-242">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-243">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-244">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-245">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-246">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="02a7a-247">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-248">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-249">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-250">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-251">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-252">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-252">Return Values</span></span>

 - <span data-ttu-id="02a7a-253">**NX_SUCCESS** (0X00) pomyślnie wysłał klienta http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="02a7a-254">Pobierz komunikat startowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-254">GET start message</span></span>
 - <span data-ttu-id="02a7a-255">Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="02a7a-256">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-257">**NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-258">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="02a7a-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="02a7a-259">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-260">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="02a7a-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-261">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-261">Allowed From</span></span>

<span data-ttu-id="02a7a-262">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-263">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-263">Example</span></span>

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="02a7a-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="02a7a-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="02a7a-265">Wyślij żądanie HTTP GET (IPv4 lub IPv6)</span><span class="sxs-lookup"><span data-stu-id="02a7a-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-266">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-267">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-267">Description</span></span>

<span data-ttu-id="02a7a-268">Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "Resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="02a7a-269">Może służyć do nawiązywania połączenia z siecią IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="02a7a-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="02a7a-270">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="02a7a-271">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="02a7a-272">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-272">This service is deprecated.</span></span> <span data-ttu-id="02a7a-273">Deweloperzy są zachęcani do migracji do *nxd_http_client_get_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-274">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-274">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-275">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-276">**Server_ip** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-277">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-278">**input_ptr** Wskaźnik na dodatkowe dane żądania GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="02a7a-279">Jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="02a7a-279">This is optional.</span></span> <span data-ttu-id="02a7a-280">Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.</span><span class="sxs-lookup"><span data-stu-id="02a7a-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="02a7a-281">**input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="02a7a-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="02a7a-282">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-283">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-284">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-285">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-286">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="02a7a-287">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-288">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-289">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-290">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-291">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-292">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-292">Return Values</span></span>

 - <span data-ttu-id="02a7a-293">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Get</span><span class="sxs-lookup"><span data-stu-id="02a7a-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="02a7a-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) — hasło przekracza rozmiar buforu</span><span class="sxs-lookup"><span data-stu-id="02a7a-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="02a7a-295">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-296">**NX_HTTP_FAILED** (0XE2) nieprawidłowe parametry pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="02a7a-297">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa lub hasło</span><span class="sxs-lookup"><span data-stu-id="02a7a-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="02a7a-298">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-299">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-300">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-300">Allowed From</span></span>

<span data-ttu-id="02a7a-301">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-302">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-302">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="02a7a-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="02a7a-304">Wyślij żądanie HTTP GET (IPv4 lub IPv6)</span><span class="sxs-lookup"><span data-stu-id="02a7a-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-305">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-306">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-306">Description</span></span>

<span data-ttu-id="02a7a-307">Ta usługa próbuje utworzyć i wysłać żądanie GET z zasobem określonym przez wskaźnik "Resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="02a7a-308">Może służyć do nawiązywania połączenia z siecią IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="02a7a-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="02a7a-309">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-310">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="02a7a-311">Ta usługa zastępuje *nxd_http_client_get_start ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="02a7a-312">Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="02a7a-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-313">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-313">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-314">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-315">**Server_ip** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-316">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-317">**resource_length** Długość ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-318">**input_ptr** Wskaźnik na dodatkowe dane żądania GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="02a7a-319">Jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="02a7a-319">This is optional.</span></span> <span data-ttu-id="02a7a-320">Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.</span><span class="sxs-lookup"><span data-stu-id="02a7a-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="02a7a-321">**input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="02a7a-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="02a7a-322">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-323">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-324">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-325">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-326">**WAIT_OPTION** Określa, jak długo usługa będzie czekać wewnętrznie na przetworzenie klienta HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="02a7a-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="02a7a-327">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-328">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-329">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-330">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-331">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-332">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-332">Return Values</span></span>

 - <span data-ttu-id="02a7a-333">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Get</span><span class="sxs-lookup"><span data-stu-id="02a7a-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="02a7a-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) — hasło przekracza rozmiar buforu</span><span class="sxs-lookup"><span data-stu-id="02a7a-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="02a7a-335">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-336">**NX_HTTP_FAILED** (0XE2) nieprawidłowe parametry pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="02a7a-337">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa lub hasło</span><span class="sxs-lookup"><span data-stu-id="02a7a-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="02a7a-338">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-339">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-340">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-340">Allowed From</span></span>

<span data-ttu-id="02a7a-341">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-342">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-342">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="02a7a-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="02a7a-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="02a7a-344">Pobierz następny pakiet danych zasobów</span><span class="sxs-lookup"><span data-stu-id="02a7a-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-345">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-346">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-346">Description</span></span>

<span data-ttu-id="02a7a-347">Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie wywołanie *nx_http_client_get_start* .</span><span class="sxs-lookup"><span data-stu-id="02a7a-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="02a7a-348">Kolejne wywołania tej procedury należy wprowadzać do momentu otrzymania stanu powrotu NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="02a7a-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-349">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-349">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-350">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-351">**packet_ptr** Miejsce docelowe dla wskaźnika pakietu zawierającego częściową zawartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="02a7a-352">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na pobieranie pakietu przez klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="02a7a-353">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-354">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-355">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-356">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-357">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-358">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-358">Return Values</span></span>

 - <span data-ttu-id="02a7a-359">**NX_SUCCESS** (0X00) pomyślne pobieranie pakietu przez klienta http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="02a7a-360">**NX_HTTP_GET_DONE** (0XEC) http Get pakiet klienta jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="02a7a-361">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest w trybie pobierania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="02a7a-362">**NX_HTTP_BAD_PACKET_LENGTH** (0XED) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="02a7a-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="02a7a-363">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-364">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-365">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-365">Allowed From</span></span>

<span data-ttu-id="02a7a-366">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-367">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="02a7a-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="02a7a-368">nx_http_client_put_start</span></span>

<span data-ttu-id="02a7a-369">Rozpocznij żądanie HTTP PUT za pośrednictwem protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="02a7a-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-370">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-371">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-371">Description</span></span>

<span data-ttu-id="02a7a-372">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP o podanym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="02a7a-373">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet ()* , aby faktycznie wysyłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-374">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="02a7a-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="02a7a-375">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-375">This service is deprecated.</span></span> <span data-ttu-id="02a7a-376">Deweloperzy są zachęcani do migracji do *nxd_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-377">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-377">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-378">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-379">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-380">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-381">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-382">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-383">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="02a7a-384">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="02a7a-385">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="02a7a-386">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-387">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-388">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-389">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-390">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-391">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-391">Return Values</span></span>

 - <span data-ttu-id="02a7a-392">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="02a7a-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="02a7a-393">**NX_HTTP_USERNAME_TOO_LONG** (0XF1) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="02a7a-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="02a7a-394">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-395">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-396">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="02a7a-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="02a7a-397">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-398">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-398">Allowed From</span></span>

<span data-ttu-id="02a7a-399">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-400">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="02a7a-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="02a7a-402">Rozpocznij żądanie HTTP PUT za pośrednictwem protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="02a7a-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-403">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-404">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-404">Description</span></span>

<span data-ttu-id="02a7a-405">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP o podanym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="02a7a-406">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet ()* , aby faktycznie wysyłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-407">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="02a7a-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="02a7a-408">Ta usługa zastępuje *nx_http_client_put_start ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="02a7a-409">Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="02a7a-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-410">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-410">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-411">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-412">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-413">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-414">**resource_length** Długość ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="02a7a-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="02a7a-415">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-416">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-417">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-418">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-419">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="02a7a-420">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="02a7a-421">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="02a7a-422">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-423">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-424">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-425">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-426">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-427">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-427">Return Values</span></span>

 - <span data-ttu-id="02a7a-428">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="02a7a-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="02a7a-429">**NX_HTTP_USERNAME_TOO_LONG** (0XF1) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="02a7a-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="02a7a-430">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-431">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-432">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="02a7a-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="02a7a-433">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-434">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-434">Allowed From</span></span>

<span data-ttu-id="02a7a-435">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-436">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="02a7a-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="02a7a-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="02a7a-438">Rozpocznij żądanie HTTP PUT (IPv4 lub IPv6)</span><span class="sxs-lookup"><span data-stu-id="02a7a-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-439">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-440">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-440">Description</span></span>

<span data-ttu-id="02a7a-441">Ta usługa próbuje umieścić (wysłać) określony zasób na serwerze HTTP pod podanym adresem IP za pośrednictwem protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="02a7a-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="02a7a-442">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet ()* , aby faktycznie wysyłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-443">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="02a7a-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="02a7a-444">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-444">This service is deprecated.</span></span> <span data-ttu-id="02a7a-445">Deweloperzy są zachęcani do migracji do *nxd_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-446">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-446">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-447">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-448">**server_IP** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-449">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="02a7a-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="02a7a-450">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-451">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-452">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="02a7a-453">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="02a7a-454">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="02a7a-455">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-456">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-457">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-458">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-459">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-460">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-460">Return Values</span></span>

 - <span data-ttu-id="02a7a-461">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie przełączenia klienta http</span><span class="sxs-lookup"><span data-stu-id="02a7a-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="02a7a-462">Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="02a7a-463">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-464">**NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem http</span><span class="sxs-lookup"><span data-stu-id="02a7a-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="02a7a-465">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-466">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="02a7a-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="02a7a-467">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-468">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-468">Allowed From</span></span>

<span data-ttu-id="02a7a-469">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-470">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-470">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="02a7a-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="02a7a-472">Rozpocznij żądanie HTTP PUT (IPv4 lub IPv6)</span><span class="sxs-lookup"><span data-stu-id="02a7a-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-473">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-474">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-474">Description</span></span>

<span data-ttu-id="02a7a-475">Ta usługa próbuje umieścić (wysłać) określony zasób na serwerze HTTP pod podanym adresem IP za pośrednictwem protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="02a7a-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="02a7a-476">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_http_client_put_packet ()* , aby faktycznie wysyłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-477">Ciąg zasobu może odwoływać się do pliku lokalnego, np. ``` “/index.htm” ``` lub może odwoływać się do innego adresu URL, np. ```http://abc.website.com/index.htm``` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="02a7a-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="02a7a-478">Ta usługa zastępuje *nxd_http_client_put_start ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="02a7a-479">Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="02a7a-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-480">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-480">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-481">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-482">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-483">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="02a7a-484">**resource_length** Długość ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="02a7a-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="02a7a-485">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-486">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="02a7a-487">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-488">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="02a7a-489">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="02a7a-490">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="02a7a-491">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="02a7a-492">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-493">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-494">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-495">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-496">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-497">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-497">Return Values</span></span>

 - <span data-ttu-id="02a7a-498">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie przełączenia klienta http</span><span class="sxs-lookup"><span data-stu-id="02a7a-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="02a7a-499">Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="02a7a-500">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-501">NX_HTTP_FAILED (0xE2) błąd klienta HTTP podczas komunikacji z serwerem HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="02a7a-502">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-503">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="02a7a-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="02a7a-504">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-505">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-505">Allowed From</span></span>

<span data-ttu-id="02a7a-506">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-507">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-507">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="02a7a-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="02a7a-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="02a7a-509">Wyślij następny pakiet danych zasobu</span><span class="sxs-lookup"><span data-stu-id="02a7a-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-510">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02a7a-511">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-511">Description</span></span>

<span data-ttu-id="02a7a-512">Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-513">Ta procedura powinna być wywoływana wielokrotnie do momentu, aż łączna długość wysłanych pakietów jest równa "total_bytes" określonego w poprzednim wywołaniu *nx_http_client_put_start* .</span><span class="sxs-lookup"><span data-stu-id="02a7a-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-514">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-514">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-515">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-516">**packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="02a7a-517">**WAIT_OPTION** Określa, jak długo usługa będzie czekać wewnętrznie na przetwarzanie pakietu klienta HTTP PUT.</span><span class="sxs-lookup"><span data-stu-id="02a7a-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="02a7a-518">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="02a7a-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="02a7a-519">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="02a7a-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="02a7a-520">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="02a7a-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="02a7a-521">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="02a7a-522">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-523">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-523">Return Values</span></span>

 - <span data-ttu-id="02a7a-524">**NX_SUCCESS** (0X00) pomyślnie wysłał pakiet klienta http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="02a7a-525">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="02a7a-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="02a7a-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0XEE) otrzymał kod błędu serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="02a7a-527">**NX_HTTP_BAD_PACKET_LENGTH** (0XED) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="02a7a-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="02a7a-528">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło</span><span class="sxs-lookup"><span data-stu-id="02a7a-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="02a7a-529">Serwer **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) reaguje przed UKOŃCZeniem umieszczania</span><span class="sxs-lookup"><span data-stu-id="02a7a-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="02a7a-530">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-531">Pakiet NX_INVALID_PACKET (0x12) jest za mały dla nagłówka TCP</span><span class="sxs-lookup"><span data-stu-id="02a7a-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="02a7a-532">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-533">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-533">Allowed From</span></span>

<span data-ttu-id="02a7a-534">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-535">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="02a7a-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="02a7a-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="02a7a-537">Ustaw port połączenia na serwer</span><span class="sxs-lookup"><span data-stu-id="02a7a-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-538">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="02a7a-539">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-539">Description</span></span>

<span data-ttu-id="02a7a-540">Ta usługa zmienia port połączenia podczas nawiązywania połączenia z serwerem HTTP do określonego portu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="02a7a-541">W przeciwnym razie wartość domyślna portu połączenia to 80.</span><span class="sxs-lookup"><span data-stu-id="02a7a-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="02a7a-542">Ta wartość musi być wywoływana przed *nx_http_client_get_start ()* i *nx_http_client_put_start ()* , np. gdy klient http nawiązuje połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="02a7a-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-543">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-543">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-544">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="02a7a-545">**port** Port służący do nawiązywania połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="02a7a-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-546">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-546">Return Values</span></span>

 - <span data-ttu-id="02a7a-547">**NX_SUCCESS** (0X00) pomyślnie zmienił port</span><span class="sxs-lookup"><span data-stu-id="02a7a-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="02a7a-548">Port NX_INVALID_PORT (0x46) przekracza wartość maksymalną (0xFFFF) lub równą zero</span><span class="sxs-lookup"><span data-stu-id="02a7a-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="02a7a-549">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-550">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-550">Allowed From</span></span>

<span data-ttu-id="02a7a-551">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="02a7a-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-552">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="02a7a-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="02a7a-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="02a7a-554">Ustawianie wywołania zwrotnego do pobierania adresu URL maksymalny wiek i Data</span><span class="sxs-lookup"><span data-stu-id="02a7a-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-555">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="02a7a-556">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-556">Description</span></span>

<span data-ttu-id="02a7a-557">Ta usługa ustawia wywołana usługa wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-558">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-558">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-559">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-560">**cache_info_get** Wskaźnik do wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="02a7a-561">**max_age** Wskaźnik do maksymalnego wieku zasobu</span><span class="sxs-lookup"><span data-stu-id="02a7a-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="02a7a-562">**dane** Zwrócono wskaźnik do daty ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-563">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-563">Return Values</span></span>

 - <span data-ttu-id="02a7a-564">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="02a7a-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="02a7a-565">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-566">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-566">Allowed From</span></span>

<span data-ttu-id="02a7a-567">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="02a7a-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-568">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="02a7a-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="02a7a-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="02a7a-570">Wyślij dane z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-571">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="02a7a-572">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-572">Description</span></span>

<span data-ttu-id="02a7a-573">Ta usługa wysyła dane z dostarczonego pakietu z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="02a7a-574">Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="02a7a-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-575">Jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="02a7a-576">Ponadto procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="02a7a-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-577">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-577">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-578">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-579">**data_ptr** Wskaźnik do danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="02a7a-580">**data_length**  Liczba bajtów do wysłania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-581">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-581">Return Values</span></span>

 - <span data-ttu-id="02a7a-582">**NX_SUCCESS** (0X00) pomyślnie przesłał dane serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="02a7a-583">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-584">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-584">Allowed From</span></span>

<span data-ttu-id="02a7a-585">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-586">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-586">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="02a7a-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="02a7a-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="02a7a-588">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-589">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="02a7a-590">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-590">Description</span></span>

<span data-ttu-id="02a7a-591">Ta usługa wywołuje funkcję wewnętrzną *_nx_http_server_generate_response_header* , gdy serwer http odpowiada na żądania GET, PUT i DELETE klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="02a7a-592">Jest ona przeznaczona do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje odpowiedź na klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="02a7a-593">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-593">This service is deprecated.</span></span> <span data-ttu-id="02a7a-594">Deweloperzy są zachęcani do migracji do *nxd_http_server_callback_generate_response_header_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-595">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-595">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-596">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-597">**packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości</span><span class="sxs-lookup"><span data-stu-id="02a7a-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="02a7a-598">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="02a7a-599">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="02a7a-599">Examples:</span></span>
    - <span data-ttu-id="02a7a-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="02a7a-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="02a7a-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="02a7a-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="02a7a-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="02a7a-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="02a7a-603">**CONTENT_LENGTH** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="02a7a-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="02a7a-604">**Content_Type** Typ HTTP np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="02a7a-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="02a7a-605">**additional_header** Wskaźnik na dodatkowy tekst nagłówka</span><span class="sxs-lookup"><span data-stu-id="02a7a-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-606">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-606">Return Values</span></span>

 - <span data-ttu-id="02a7a-607">**NX_SUCCESS** (0X00) pomyślnie utworzył nagłówek</span><span class="sxs-lookup"><span data-stu-id="02a7a-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="02a7a-608">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-609">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-609">Allowed From</span></span>

<span data-ttu-id="02a7a-610">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-611">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-611">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="02a7a-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="02a7a-613">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-614">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-614">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="02a7a-615">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-615">Description</span></span>

<span data-ttu-id="02a7a-616">Ta usługa wywołuje funkcję wewnętrzną *_nx_http_server_generate_response_header ()* , gdy serwer http odpowiada na żądania GET, PUT i DELETE klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="02a7a-617">Jest ona przeznaczona do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje odpowiedź na klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="02a7a-618">Ta usługa zastępuje *nx_http_server_callback_generate_response_header ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="02a7a-619">Ta wersja dostarcza dodatkowe informacje o długości do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="02a7a-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-620">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-620">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-621">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-622">**packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości</span><span class="sxs-lookup"><span data-stu-id="02a7a-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="02a7a-623">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="02a7a-624">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="02a7a-624">Examples:</span></span>
    - <span data-ttu-id="02a7a-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="02a7a-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="02a7a-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="02a7a-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="02a7a-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="02a7a-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="02a7a-628">**status_code** Długość kodu stanu</span><span class="sxs-lookup"><span data-stu-id="02a7a-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="02a7a-629">**CONTENT_LENGTH** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="02a7a-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="02a7a-630">**Content_Type** Typ HTTP np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="02a7a-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="02a7a-631">**content_type_length** Długość typu HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="02a7a-632">**additional_header** Wskaźnik na dodatkowy tekst nagłówka</span><span class="sxs-lookup"><span data-stu-id="02a7a-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="02a7a-633">**additional_header_length** Długość dodatkowego tekstu nagłówka</span><span class="sxs-lookup"><span data-stu-id="02a7a-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-634">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-634">Return Values</span></span>

 - <span data-ttu-id="02a7a-635">**NX_SUCCESS** (0X00) pomyślnie utworzył nagłówek</span><span class="sxs-lookup"><span data-stu-id="02a7a-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="02a7a-636">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-637">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-637">Allowed From</span></span>

<span data-ttu-id="02a7a-638">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-639">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-639">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="02a7a-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="02a7a-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="02a7a-641">Wyślij pakiet HTTP z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-643">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-643">Description</span></span>

<span data-ttu-id="02a7a-644">Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="02a7a-645">Serwer HTTP wyśle pakiet za pomocą _TIMEOUT_SEND NX_HTTP_SERVER.</span><span class="sxs-lookup"><span data-stu-id="02a7a-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="02a7a-646">Nagłówek HTTP i dane muszą być dołączone do pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="02a7a-647">Jeśli stan powrotu wskazuje na błąd, aplikacja HTTP musi zwolnić pakiet.</span><span class="sxs-lookup"><span data-stu-id="02a7a-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="02a7a-648">Wywołanie zwrotne powinno zwracać NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="02a7a-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="02a7a-649">Zobacz *nx_http_server_callback_generate_response_header ()* , aby zapoznać się z bardziej szczegółowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="02a7a-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-650">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-650">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-651">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-652">**packet_ptr** Wskaźnik do pakietu do wysłania</span><span class="sxs-lookup"><span data-stu-id="02a7a-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-653">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-653">Return Values</span></span>

 - <span data-ttu-id="02a7a-654">**NX_SUCCESS** (0X00) pomyślnie wysłał pakiet serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="02a7a-655">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-656">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-656">Allowed From</span></span>

<span data-ttu-id="02a7a-657">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-658">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-658">Example</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="02a7a-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="02a7a-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="02a7a-660">Wyślij odpowiedź z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-661">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="02a7a-662">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-662">Description</span></span>

<span data-ttu-id="02a7a-663">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="02a7a-664">Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="02a7a-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-665">Jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="02a7a-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="02a7a-666">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-666">This service is deprecated.</span></span> <span data-ttu-id="02a7a-667">Deweloperzy są zachęcani do migracji do *nxd_http_server_callback_response_send_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-668">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-668">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-669">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-670">**nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="02a7a-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="02a7a-671">**informacje** Wskaźnik na ciąg informacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="02a7a-672">**additional_info** Wskaźnik na ciąg informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="02a7a-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-673">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-673">Return Values</span></span>

 - <span data-ttu-id="02a7a-674">**NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-675">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-675">Allowed From</span></span>

<span data-ttu-id="02a7a-676">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-677">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-677">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="02a7a-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="02a7a-679">Wyślij odpowiedź z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-680">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-680">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="02a7a-681">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-681">Description</span></span>

<span data-ttu-id="02a7a-682">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="02a7a-683">Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="02a7a-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-684">Jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="02a7a-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="02a7a-685">Ta usługa zastępuje *nx_http_server_callback_response_send ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="02a7a-686">Ta wersja pobiera dodatkowe informacje o długości jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="02a7a-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-687">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-687">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-688">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-689">**nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="02a7a-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="02a7a-690">**header_length** Długość ciągu nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="02a7a-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="02a7a-691">**informacje** Wskaźnik na ciąg informacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="02a7a-692">**information_length** Długość ciągu informacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="02a7a-693">**additional_info** Wskaźnik na ciąg informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="02a7a-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="02a7a-694">**additional_info_length** Długość ciągu informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="02a7a-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-695">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-695">Return Values</span></span>

 - <span data-ttu-id="02a7a-696">**NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-697">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-697">Allowed From</span></span>

<span data-ttu-id="02a7a-698">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-699">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-699">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="02a7a-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="02a7a-700">nx_http_server_content_get</span></span>

<span data-ttu-id="02a7a-701">Pobierz zawartość z żądania</span><span class="sxs-lookup"><span data-stu-id="02a7a-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-702">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-703">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-703">Description</span></span>

<span data-ttu-id="02a7a-704">Ta usługa próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="02a7a-705">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="02a7a-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="02a7a-706">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-706">This service is deprecated.</span></span> <span data-ttu-id="02a7a-707">Deweloperzy są zachęcani do migracji do *nx_http_server_content_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-708">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-708">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-709">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-710">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="02a7a-711">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="02a7a-712">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="02a7a-713">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="02a7a-714">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="02a7a-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="02a7a-715">**actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-716">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-716">Return Values</span></span>

 - <span data-ttu-id="02a7a-717">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http</span><span class="sxs-lookup"><span data-stu-id="02a7a-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="02a7a-718">Błąd wewnętrzny serwera HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="02a7a-719">0xE7 — koniec zawartości żądania **NX_HTTP_DATA_END**</span><span class="sxs-lookup"><span data-stu-id="02a7a-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="02a7a-720">**NX_HTTP_TIMEOUT** (0xE1) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu zawartości</span><span class="sxs-lookup"><span data-stu-id="02a7a-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="02a7a-721">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-722">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-723">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-723">Allowed From</span></span>

<span data-ttu-id="02a7a-724">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-725">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="02a7a-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="02a7a-727">Pobierz zawartość z żądania/obsługuje długość zawartości o zerowej długości</span><span class="sxs-lookup"><span data-stu-id="02a7a-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-728">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-729">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-729">Description</span></span>

<span data-ttu-id="02a7a-730">Ta usługa jest niemal identyczna z *nx_http_server_content_get ();* próbuje pobrać określoną ilość zawartości z żądania post lub Put klienta http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="02a7a-731">Jednak obsługuje żądania o długości wartości zerowej (puste żądanie) jako prawidłowe żądanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="02a7a-732">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="02a7a-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="02a7a-733">Ta usługa zastępuje *nx_http_server_content_get ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="02a7a-734">Ta wersja wymaga od wywołującego podania dodatkowych informacji o długości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-735">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-735">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-736">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-737">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="02a7a-738">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="02a7a-739">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="02a7a-740">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="02a7a-741">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="02a7a-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="02a7a-742">**actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-743">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-743">Return Values</span></span>

 - <span data-ttu-id="02a7a-744">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości http</span><span class="sxs-lookup"><span data-stu-id="02a7a-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="02a7a-745">Błąd wewnętrzny serwera HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="02a7a-746">0xE7 — koniec zawartości żądania **NX_HTTP_DATA_END**</span><span class="sxs-lookup"><span data-stu-id="02a7a-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="02a7a-747">**NX_HTTP_TIMEOUT** (0xE1) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu</span><span class="sxs-lookup"><span data-stu-id="02a7a-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="02a7a-748">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="02a7a-749">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-750">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-750">Allowed From</span></span>

<span data-ttu-id="02a7a-751">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-752">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="02a7a-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="02a7a-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="02a7a-754">Pobierz długość zawartości w żądaniu</span><span class="sxs-lookup"><span data-stu-id="02a7a-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-755">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-756">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-756">Description</span></span>

<span data-ttu-id="02a7a-757">Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="02a7a-758">W przypadku braku zawartości HTTP Ta procedura zwraca wartość zero.</span><span class="sxs-lookup"><span data-stu-id="02a7a-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="02a7a-759">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="02a7a-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="02a7a-760">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-760">This service is deprecated.</span></span> <span data-ttu-id="02a7a-761">Deweloperzy są zachęcani do migracji do *nx_http_server_content_length_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-762">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-762">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-763">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="02a7a-764">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-765">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-765">Return Values</span></span>

 - <span data-ttu-id="02a7a-766">**długość zawartości** W przypadku błędu zwracana jest wartość zero.</span><span class="sxs-lookup"><span data-stu-id="02a7a-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="02a7a-767">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-767">Allowed From</span></span>

<span data-ttu-id="02a7a-768">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-769">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="02a7a-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="02a7a-771">Pobierz długość zawartości w żądaniu/obsługuje długość zawartości równą zero</span><span class="sxs-lookup"><span data-stu-id="02a7a-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-772">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="02a7a-773">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-773">Description</span></span>

<span data-ttu-id="02a7a-774">Ta usługa jest podobna do *nx_http_server_content_length_get;* próbuje pobrać długość zawartości http w dostarczonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="02a7a-775">Jednak wartość zwracana wskazuje stan pomyślnego ukończenia, a rzeczywista wartość długości jest zwracana w wskaźniku wejściowym ```content_length``` .</span><span class="sxs-lookup"><span data-stu-id="02a7a-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="02a7a-776">Jeśli nie ma żadnej zawartości HTTP o długości zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wskaźnik wejściowy wskazuje prawidłową długość (zero).</span><span class="sxs-lookup"><span data-stu-id="02a7a-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="02a7a-777">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="02a7a-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="02a7a-778">Ta usługa zastępuje *nx_http_server_content_length_get ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-779">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-779">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-780">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="02a7a-781">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="02a7a-782">**CONTENT_LENGTH** Wskaźnik do wartości pobranej z pola długości zawartości</span><span class="sxs-lookup"><span data-stu-id="02a7a-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-783">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-783">Return Values</span></span>

 - <span data-ttu-id="02a7a-784">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="02a7a-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) niewłaściwy format nagłówka http</span><span class="sxs-lookup"><span data-stu-id="02a7a-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="02a7a-786">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-787">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-787">Allowed From</span></span>

<span data-ttu-id="02a7a-788">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-789">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="02a7a-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="02a7a-790">nx_http_server_create</span></span>

<span data-ttu-id="02a7a-791">Tworzenie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-792">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-792">Prototype</span></span>

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="02a7a-793">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-793">Description</span></span>

<span data-ttu-id="02a7a-794">Ta usługa tworzy wystąpienie serwera HTTP, które działa w kontekście jego własnego wątku ThreadX.</span><span class="sxs-lookup"><span data-stu-id="02a7a-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="02a7a-795">Opcjonalne *authentication_check* i request_notify procedury wywołania zwrotnego aplikacji umożliwiają kontrolę oprogramowania aplikacji przez podstawowe operacje serwera http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-796">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-796">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-797">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="02a7a-798">**http_server_name** Wskaźnik na nazwę serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="02a7a-799">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="02a7a-800">**media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="02a7a-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="02a7a-801">**stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="02a7a-802">**stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="02a7a-803">**authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="02a7a-804">Jeśli jest określony, ta procedura jest wywoływana dla każdego żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="02a7a-805">Jeśli ten parametr ma wartość NULL, uwierzytelnianie nie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="02a7a-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="02a7a-806">**request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02a7a-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="02a7a-807">Jeśli jest określony, ta procedura jest wywoływana przed przetworzeniem żądania przez serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="02a7a-808">Pozwala to na aktualizowanie nazwy zasobu lub pól w ramach zasobu przed ukończeniem żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-809">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-809">Return Values</span></span>

 - <span data-ttu-id="02a7a-810">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera http.</span><span class="sxs-lookup"><span data-stu-id="02a7a-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="02a7a-811">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="02a7a-812">Ładunek pakietu NX_HTTP_POOL_ERROR (0xE9) puli nie jest wystarczająco duży, aby można było zawierać pełne żądanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-813">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-813">Allowed From</span></span>

<span data-ttu-id="02a7a-814">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-815">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="02a7a-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="02a7a-816">nx_http_server_delete</span></span>

<span data-ttu-id="02a7a-817">Usuwanie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-819">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-819">Description</span></span>

<span data-ttu-id="02a7a-820">Ta usługa usuwa poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-821">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-821">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-822">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-823">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-823">Return Values</span></span>

 - <span data-ttu-id="02a7a-824">**NX_SUCCESS** (0X00) pomyślne usunięcie serwera http</span><span class="sxs-lookup"><span data-stu-id="02a7a-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="02a7a-825">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="02a7a-826">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-827">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-827">Allowed From</span></span>

<span data-ttu-id="02a7a-828">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-829">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="02a7a-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="02a7a-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="02a7a-831">Pobierz lokalizację i długość danych jednostki</span><span class="sxs-lookup"><span data-stu-id="02a7a-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-832">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="02a7a-833">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-833">Description</span></span>

<span data-ttu-id="02a7a-834">Ta usługa określa lokalizację początkową danych w bieżącej jednostce wieloczęściowej w odebranych komunikatach klienta i długość danych bez uwzględniania ciągu granicy.</span><span class="sxs-lookup"><span data-stu-id="02a7a-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="02a7a-835">Serwer HTTP wewnętrznie aktualizuje własne przesunięcia, aby można było ponownie wywołać tę funkcję na tym samym datagramie klienta dla komunikatów z wieloma jednostkami.</span><span class="sxs-lookup"><span data-stu-id="02a7a-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="02a7a-836">Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-837">Aby można było korzystać z tej usługi, NX_HTTP_MULTIPART_ENABLE musi być włączona.</span><span class="sxs-lookup"><span data-stu-id="02a7a-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="02a7a-838">Aby uzyskać więcej informacji, zobacz [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) .</span><span class="sxs-lookup"><span data-stu-id="02a7a-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-839">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-839">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-840">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="02a7a-841">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="02a7a-842">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="02a7a-843">**available_offset** Wskaźnik do przesunięcia danych jednostki ze wskaźnika dołączania do pakietu</span><span class="sxs-lookup"><span data-stu-id="02a7a-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="02a7a-844">**available_length** Wskaźnik do długości danych jednostki</span><span class="sxs-lookup"><span data-stu-id="02a7a-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-845">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-845">Return Values</span></span>

 - <span data-ttu-id="02a7a-846">**NX_SUCCESS** (0X00) pomyślnie pobrała rozmiar i lokalizację zawartości jednostki</span><span class="sxs-lookup"><span data-stu-id="02a7a-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="02a7a-847">Zawartość **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) dla wewnętrznych znaczników wieloczęściowych serwera http została już znaleziona</span><span class="sxs-lookup"><span data-stu-id="02a7a-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="02a7a-848">Wewnętrzny błąd HTTP NX_HTTP_ERROR (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="02a7a-849">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-850">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-850">Allowed From</span></span>

<span data-ttu-id="02a7a-851">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-852">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-852">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="02a7a-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="02a7a-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="02a7a-854">Pobierz zawartość nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="02a7a-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-855">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-856">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-856">Description</span></span>

<span data-ttu-id="02a7a-857">Ta usługa pobiera nagłówek jednostki do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="02a7a-858">Serwer HTTP wewnętrznie aktualizuje własne wskaźniki, aby znaleźć następną wieloczęściową jednostkę w datagramie klienta z wieloma nagłówkami jednostek.</span><span class="sxs-lookup"><span data-stu-id="02a7a-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="02a7a-859">Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-860">Aby można było korzystać z tej usługi, NX_HTTP_MULTIPART_ENABLE musi być włączona.</span><span class="sxs-lookup"><span data-stu-id="02a7a-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-861">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-861">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-862">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="02a7a-863">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="02a7a-864">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="02a7a-865">**entity_header_buffer** Wskaźnik do lokalizacji do zapisania nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="02a7a-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="02a7a-866">**buffer_size** Rozmiar buforu wejściowego</span><span class="sxs-lookup"><span data-stu-id="02a7a-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-867">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-867">Return Values</span></span>

 - <span data-ttu-id="02a7a-868">**NX_SUCCESS** (0X00) pomyślnie pobrało nagłówek jednostki</span><span class="sxs-lookup"><span data-stu-id="02a7a-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="02a7a-869">Nie znaleziono pola nagłówka jednostki **NX_HTTP_NOT_FOUND** **(0xE6)**</span><span class="sxs-lookup"><span data-stu-id="02a7a-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="02a7a-870">Czas **NX_HTTP_TIMEOUT** **(0xE1)** , który utracił ważność następnego pakietu dla komunikatu klienta wielopakietowego</span><span class="sxs-lookup"><span data-stu-id="02a7a-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="02a7a-871">Wewnętrzny błąd HTTP NX_HTTP_ERROR (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="02a7a-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="02a7a-872">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-873">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-874">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-874">Allowed From</span></span>

<span data-ttu-id="02a7a-875">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-876">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-876">Example</span></span>

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
  NX_SUCCESS)
 {
                nx_packet_release(response_pkt);
     }
    }


}
else
{
    /* Indicate we have not processed the response to client yet.*/
    return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="02a7a-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="02a7a-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="02a7a-878">Ustaw wywołanie zwrotne, aby uzyskać datę i godzinę GMT</span><span class="sxs-lookup"><span data-stu-id="02a7a-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-879">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="02a7a-880">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-880">Description</span></span>

<span data-ttu-id="02a7a-881">Ta usługa ustawia wywołanie zwrotne, aby uzyskać datę i godzinę GMT z wcześniej utworzonym serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="02a7a-882">Ta usługa jest wywoływana z serwerem HTTP tworzy nagłówek w odpowiedziach serwera HTTP dla klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-883">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-883">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-884">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="02a7a-885">**gmt_getv** Wskaźnik do wywołania zwrotnego GMT</span><span class="sxs-lookup"><span data-stu-id="02a7a-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="02a7a-886">**DATEV** Wskaźnik do pobranej daty</span><span class="sxs-lookup"><span data-stu-id="02a7a-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-887">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-887">Return Values</span></span>

 - <span data-ttu-id="02a7a-888">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="02a7a-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="02a7a-889">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.</span><span class="sxs-lookup"><span data-stu-id="02a7a-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-890">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-890">Allowed From</span></span>

<span data-ttu-id="02a7a-891">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-892">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-892">Example</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="02a7a-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="02a7a-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="02a7a-894">Ustaw wywołanie zwrotne w celu obsługi nieprawidłowego użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="02a7a-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="02a7a-896">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-896">Description</span></span>

<span data-ttu-id="02a7a-897">Ta usługa ustawia wywołanie zwrotne wywoływane po odebraniu nieprawidłowej nazwy użytkownika i hasła do żądania GET, Put lub DELETE klienta w ramach uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="02a7a-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="02a7a-898">Należy wcześniej utworzyć serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-899">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-899">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-900">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="02a7a-901">**invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/przekazania wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="02a7a-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="02a7a-902">**zasób** Wskaźnik do zasobu określonego przez klienta</span><span class="sxs-lookup"><span data-stu-id="02a7a-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="02a7a-903">**client_address** Wskaźnik na adres klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="02a7a-904">Może być IPv4 lub IPv6</span><span class="sxs-lookup"><span data-stu-id="02a7a-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="02a7a-905">**request_type** Wskazuje typ żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="02a7a-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="02a7a-906">Może:</span><span class="sxs-lookup"><span data-stu-id="02a7a-906">May be:</span></span>
    - <span data-ttu-id="02a7a-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="02a7a-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="02a7a-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="02a7a-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="02a7a-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="02a7a-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="02a7a-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="02a7a-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="02a7a-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="02a7a-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-912">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-912">Return Values</span></span>

 - <span data-ttu-id="02a7a-913">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="02a7a-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="02a7a-914">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-915">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-915">Allowed From</span></span>

<span data-ttu-id="02a7a-916">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-917">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-917">Example</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="02a7a-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="02a7a-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="02a7a-919">Ustaw dodatkowe mapy MIME dla HTML</span><span class="sxs-lookup"><span data-stu-id="02a7a-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-920">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="02a7a-921">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-921">Description</span></span>

<span data-ttu-id="02a7a-922">Ta usługa umożliwia deweloperowi aplikacji protokołu HTTP Dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczonych przez serwer HTTP NetX Duo (zobacz *nx_http_server_get_type* dla listy zdefiniowanych typów).</span><span class="sxs-lookup"><span data-stu-id="02a7a-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="02a7a-923">Po odebraniu żądania klienta, np. żądanie GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu preferencyjnego dodatkowego zestawu mapowań MIME i jeśli nie jest zgodny, szuka dopasowania w domyślnej mapie MIME serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="02a7a-924">Jeśli nie zostanie znalezione dopasowanie, typ MIME domyślnie przyjmuje wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="02a7a-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="02a7a-925">Jeśli funkcja powiadamiania o żądaniu jest zarejestrowana na serwerze HTTP, wywołanie zwrotne powiadomienia o żądaniu może wywołać *nx_http_server_type_retrieve ()* w celu przeanalizowania typu pliku.</span><span class="sxs-lookup"><span data-stu-id="02a7a-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-926">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-926">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-927">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="02a7a-928">**mime_maps** Wskaźnik do tablicy mapy MIME</span><span class="sxs-lookup"><span data-stu-id="02a7a-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="02a7a-929">**mime_map_num** Liczba mapowań MIME w tablicy</span><span class="sxs-lookup"><span data-stu-id="02a7a-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-930">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-930">Return Values</span></span>

 - <span data-ttu-id="02a7a-931">**NX_SUCCESS** (0X00) pomyślne Ustawianie mapy MIME serwera http</span><span class="sxs-lookup"><span data-stu-id="02a7a-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="02a7a-932">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-933">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-933">Allowed From</span></span>

<span data-ttu-id="02a7a-934">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-935">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-935">Example</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="02a7a-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="02a7a-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="02a7a-937">Wyodrębnij długość zawartości i ustaw wskaźnik na początek danych</span><span class="sxs-lookup"><span data-stu-id="02a7a-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-938">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="02a7a-939">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-939">Description</span></span>

<span data-ttu-id="02a7a-940">Ta usługa wyodrębnia długość zawartości z nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="02a7a-941">Aktualizuje również podany pakiet w następujący sposób: wskaźnik dołączania pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) po prostu przekazały nagłówek HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="02a7a-942">Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na odebranie następnego pakietu przy użyciu opcji oczekiwania NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="02a7a-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-943">Nie należy go wywoływać przed wywołaniem *nx_http_server_get_entity_header* , ponieważ modyfikuje wskaźnik poprzedź przed nagłówkiem jednostki.</span><span class="sxs-lookup"><span data-stu-id="02a7a-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-944">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-944">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-945">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="02a7a-946">**packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym wskaźnikiem dołączania</span><span class="sxs-lookup"><span data-stu-id="02a7a-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="02a7a-947">**CONTENT_LENGTH** Wskaźnik do wyodrębnienia ```content_length```</span><span class="sxs-lookup"><span data-stu-id="02a7a-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-948">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-948">Return Values</span></span>

 - <span data-ttu-id="02a7a-949">**NX_SUCCESS** (0x00) znaleziono długość zawartości http i pakiet został pomyślnie zaktualizowany</span><span class="sxs-lookup"><span data-stu-id="02a7a-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="02a7a-950">Czas **NX_HTTP_TIMEOUT** (0xE1) upłynął podczas oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="02a7a-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="02a7a-951">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-952">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-952">Allowed From</span></span>

<span data-ttu-id="02a7a-953">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-954">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-954">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="02a7a-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="02a7a-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="02a7a-956">Odbierz następny pakiet HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-957">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-958">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-958">Description</span></span>

<span data-ttu-id="02a7a-959">Ta usługa zwraca następny pakiet odebrany w gnieździe serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="02a7a-960">Opcja oczekiwania na odebranie pakietu jest NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="02a7a-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-961">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-961">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-962">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="02a7a-963">**packet_ptr** Wskaźnik do odebranego pakietu</span><span class="sxs-lookup"><span data-stu-id="02a7a-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-964">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-964">Return Values</span></span>

 - <span data-ttu-id="02a7a-965">**NX_SUCCESS** (0X00) pomyślnie otrzymał następny pakiet</span><span class="sxs-lookup"><span data-stu-id="02a7a-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="02a7a-966">Czas **NX_HTTP_TIMEOUT** (0xE1) upłynął podczas oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="02a7a-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="02a7a-967">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-968">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-968">Allowed From</span></span>

<span data-ttu-id="02a7a-969">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-970">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="02a7a-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="02a7a-971">nx_http_server_param_get</span></span>

<span data-ttu-id="02a7a-972">Pobierz parametr z żądania</span><span class="sxs-lookup"><span data-stu-id="02a7a-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-973">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-974">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-974">Description</span></span>

<span data-ttu-id="02a7a-975">Ta usługa próbuje pobrać określony parametr HTTP URL w dostarczonym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="02a7a-976">Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="02a7a-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="02a7a-977">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="02a7a-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-978">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-978">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-979">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="02a7a-980">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="02a7a-981">**param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="02a7a-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="02a7a-982">**param_ptr** Obszar docelowy do skopiowania parametru.</span><span class="sxs-lookup"><span data-stu-id="02a7a-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="02a7a-983">**max_param_size** Maksymalny rozmiar obszaru docelowego parametru.</span><span class="sxs-lookup"><span data-stu-id="02a7a-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-984">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-984">Return Values</span></span>

 - <span data-ttu-id="02a7a-985">**NX_SUCCESS** (0X00) pomyślne pobieranie PARAMETRU serwera http</span><span class="sxs-lookup"><span data-stu-id="02a7a-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="02a7a-986">Nie znaleziono podanego parametru **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="02a7a-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="02a7a-987">Parametr żądania **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) nie został poprawnie zakończony</span><span class="sxs-lookup"><span data-stu-id="02a7a-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="02a7a-988">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-989">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-990">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-990">Allowed From</span></span>

<span data-ttu-id="02a7a-991">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-992">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="02a7a-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="02a7a-993">nx_http_server_query_get</span></span>

<span data-ttu-id="02a7a-994">Pobierz zapytanie z żądania</span><span class="sxs-lookup"><span data-stu-id="02a7a-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-995">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-996">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-996">Description</span></span>

<span data-ttu-id="02a7a-997">Ta usługa próbuje pobrać określoną kwerendę HTTP URL w dostarczonym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="02a7a-998">Jeśli żądana kwerenda HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="02a7a-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="02a7a-999">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="02a7a-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1000">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1000">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1001">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="02a7a-1002">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="02a7a-1003">**query_number** Numer logiczny parametru zaczynający się od zera od lewej do prawej na liście zapytań.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="02a7a-1004">**query_ptr** Obszar docelowy, w którym ma zostać skopiowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="02a7a-1005">**max_query_size** Maksymalny rozmiar obszaru docelowego zapytania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1006">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1006">Return Values</span></span>

 - <span data-ttu-id="02a7a-1007">**NX_SUCCESS** (0X00) pomyślne zapytanie serwera http</span><span class="sxs-lookup"><span data-stu-id="02a7a-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="02a7a-1008">Rozmiar zapytania **NX_HTTP_FAILED** (0xE2) jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="02a7a-1009">Nie znaleziono określonego zapytania **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="02a7a-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="02a7a-1010">**NX_HTTP_NO_QUERY_PARSED** (0XF2) brak zapytania w żądaniu klienta</span><span class="sxs-lookup"><span data-stu-id="02a7a-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="02a7a-1011">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-1012">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1013">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1013">Allowed From</span></span>

<span data-ttu-id="02a7a-1014">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1015">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="02a7a-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="02a7a-1016">nx_http_server_start</span></span>

<span data-ttu-id="02a7a-1017">Uruchom serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-1018">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-1019">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-1019">Description</span></span>

<span data-ttu-id="02a7a-1020">Ta usługa uruchamia poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1021">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1021">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1022">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1023">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1023">Return Values</span></span>

 - <span data-ttu-id="02a7a-1024">**NX_SUCCESS** (0X00) pomyślne uruchomienie serwera</span><span class="sxs-lookup"><span data-stu-id="02a7a-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="02a7a-1025">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1026">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1026">Allowed From</span></span>

<span data-ttu-id="02a7a-1027">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1028">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="02a7a-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="02a7a-1029">nx_http_server_stop</span></span>

<span data-ttu-id="02a7a-1030">Zatrzymaj serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-1031">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="02a7a-1032">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-1032">Description</span></span>

<span data-ttu-id="02a7a-1033">Ta usługa przerywa poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="02a7a-1034">Ta procedura powinna być wywoływana przed usunięciem wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1035">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1035">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1036">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1037">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1037">Return Values</span></span>

 - <span data-ttu-id="02a7a-1038">Zakończono pomyślne zatrzymywanie serwera **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="02a7a-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="02a7a-1039">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-1040">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="02a7a-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1041">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1041">Allowed From</span></span>

<span data-ttu-id="02a7a-1042">Wątki</span><span class="sxs-lookup"><span data-stu-id="02a7a-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1043">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="02a7a-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="02a7a-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="02a7a-1045">Wyodrębnij typ pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="02a7a-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-1046">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="02a7a-1047">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="02a7a-1048">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1048">This service is deprecated.</span></span> <span data-ttu-id="02a7a-1049">Zaleca się, aby użytkownicy korzystali z usługi *nx_http_server_type_retrieve ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="02a7a-1050">Ta usługa wyodrębnia typ żądania HTTP w buforze http_type_string i jego długość w zwracanej wartości z nazwy buforu wejściowego, zazwyczaj jest to adres URL.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="02a7a-1051">Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="02a7a-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="02a7a-1052">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="02a7a-1053">Domyślne mapy MIME na serwerze HTTP NetX Duo są następujące:</span><span class="sxs-lookup"><span data-stu-id="02a7a-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="02a7a-1054">**HTML** text/html</span><span class="sxs-lookup"><span data-stu-id="02a7a-1054">**html** text/html</span></span>
 - <span data-ttu-id="02a7a-1055">**htm** text/html</span><span class="sxs-lookup"><span data-stu-id="02a7a-1055">**htm** text/html</span></span>
 - <span data-ttu-id="02a7a-1056">tekst **txt** /zwykły</span><span class="sxs-lookup"><span data-stu-id="02a7a-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="02a7a-1057">obraz **GIF** /GIF</span><span class="sxs-lookup"><span data-stu-id="02a7a-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="02a7a-1058">obraz **jpg** /JPEG</span><span class="sxs-lookup"><span data-stu-id="02a7a-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="02a7a-1059">ikona obrazu **ICO** /x</span><span class="sxs-lookup"><span data-stu-id="02a7a-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="02a7a-1060">Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="02a7a-1061">Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_http_server_mime_maps_addtional_set ()* .</span><span class="sxs-lookup"><span data-stu-id="02a7a-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="02a7a-1062">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1062">This service is deprecated.</span></span> <span data-ttu-id="02a7a-1063">Deweloperzy są zachęcani do migracji do *nx_http_server_type_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1064">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1064">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1065">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="02a7a-1066">**wskaźnik nazwy** do przeszukania w buforze</span><span class="sxs-lookup"><span data-stu-id="02a7a-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="02a7a-1067">**http_type_string** (wskaźnik do wyodrębnionego typu html)</span><span class="sxs-lookup"><span data-stu-id="02a7a-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1068">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1068">Return Values</span></span>

 - <span data-ttu-id="02a7a-1069">**Długość ciągu w bajtach** Wartość różna od zera to sukces.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="02a7a-1070">Zero oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1071">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1071">Allowed From</span></span>

<span data-ttu-id="02a7a-1072">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="02a7a-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1073">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1073">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="02a7a-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="02a7a-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="02a7a-1075">Wyodrębnij typ pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="02a7a-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-1076">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="02a7a-1077">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-1077">Description</span></span>

<span data-ttu-id="02a7a-1078">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w zwracanej wartości z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="02a7a-1079">Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="02a7a-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="02a7a-1080">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="02a7a-1081">Domyślne mapy MIME na serwerze HTTP NetX Duo są następujące:</span><span class="sxs-lookup"><span data-stu-id="02a7a-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="02a7a-1082">**HTML** text/html</span><span class="sxs-lookup"><span data-stu-id="02a7a-1082">**html** text/html</span></span>
 - <span data-ttu-id="02a7a-1083">**htm** text/html</span><span class="sxs-lookup"><span data-stu-id="02a7a-1083">**htm** text/html</span></span>
 - <span data-ttu-id="02a7a-1084">tekst **txt** /zwykły</span><span class="sxs-lookup"><span data-stu-id="02a7a-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="02a7a-1085">obraz **GIF** /GIF</span><span class="sxs-lookup"><span data-stu-id="02a7a-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="02a7a-1086">obraz **jpg** /JPEG</span><span class="sxs-lookup"><span data-stu-id="02a7a-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="02a7a-1087">ikona obrazu **ICO** /x</span><span class="sxs-lookup"><span data-stu-id="02a7a-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="02a7a-1088">Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="02a7a-1089">Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_http_server_mime_maps_addtional_set ()* .</span><span class="sxs-lookup"><span data-stu-id="02a7a-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="02a7a-1090">Ta usługa zastępuje *nx_http_server_type_get ()*.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="02a7a-1091">Ta wersja dostarcza dodatkowe informacje o długości.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1092">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1092">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1093">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="02a7a-1094">**Nazwa** Wskaźnik do buforu do przeszukania</span><span class="sxs-lookup"><span data-stu-id="02a7a-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="02a7a-1095">**name_length** Długość buforu do wyszukania</span><span class="sxs-lookup"><span data-stu-id="02a7a-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="02a7a-1096">**http_type_string** (wskaźnik do wyodrębnionego typu html)</span><span class="sxs-lookup"><span data-stu-id="02a7a-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="02a7a-1097">**http_type_string_max_size** Rozmiar buforu http_type_string</span><span class="sxs-lookup"><span data-stu-id="02a7a-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1098">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1098">Return Values</span></span>

 - <span data-ttu-id="02a7a-1099">**Długość ciągu w bajtach** Wartość różna od zera to sukces.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="02a7a-1100">Zero oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1101">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1101">Allowed From</span></span>

<span data-ttu-id="02a7a-1102">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="02a7a-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1103">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1103">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="02a7a-1104">Aby zapoznać się z bardziej szczegółowym przykładem, zobacz Opis [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span><span class="sxs-lookup"><span data-stu-id="02a7a-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="02a7a-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="02a7a-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="02a7a-1106">Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="02a7a-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-1107">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-1107">Prototype</span></span>

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
```

### <a name="description"></a><span data-ttu-id="02a7a-1108">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-1108">Description</span></span>

<span data-ttu-id="02a7a-1109">Ta usługa ustawia wywołanie zwrotne wywoływane po wykonaniu uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1110">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1110">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1111">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="02a7a-1112">**digest_authenticate_callback** Wskaźnik do wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="02a7a-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1113">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1113">Return Values</span></span>

 - <span data-ttu-id="02a7a-1114">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="02a7a-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="02a7a-1115">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="02a7a-1116">NX_NOT_SUPPORTED (0x4B) uwierzytelnianie szyfrowane nie jest włączone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1117">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1117">Allowed From</span></span>

<span data-ttu-id="02a7a-1118">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="02a7a-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1119">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1119">Example</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="02a7a-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="02a7a-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="02a7a-1121">Ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="02a7a-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02a7a-1122">Prototype</span><span class="sxs-lookup"><span data-stu-id="02a7a-1122">Prototype</span></span>

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a><span data-ttu-id="02a7a-1123">Opis</span><span class="sxs-lookup"><span data-stu-id="02a7a-1123">Description</span></span>

<span data-ttu-id="02a7a-1124">Ta usługa ustawia funkcję wywołania zwrotnego sprawdzania uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="02a7a-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02a7a-1125">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="02a7a-1125">Input Parameters</span></span>

 - <span data-ttu-id="02a7a-1126">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="02a7a-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="02a7a-1127">**authentication_check_extended** Wskaźnik do sprawdzania uwierzytelniania aplikacji</span><span class="sxs-lookup"><span data-stu-id="02a7a-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="02a7a-1128">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="02a7a-1128">Return Values</span></span>

 - <span data-ttu-id="02a7a-1129">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="02a7a-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="02a7a-1130">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="02a7a-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02a7a-1131">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="02a7a-1131">Allowed From</span></span>

<span data-ttu-id="02a7a-1132">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="02a7a-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="02a7a-1133">Przykład</span><span class="sxs-lookup"><span data-stu-id="02a7a-1133">Example</span></span>

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
