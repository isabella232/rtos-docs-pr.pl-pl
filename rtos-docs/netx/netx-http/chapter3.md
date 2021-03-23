---
title: Rozdział 3 — Opis usług HTTP NetX
description: Ten rozdział zawiera opis wszystkich usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822615"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="a3b2a-103">Rozdział 3 — Opis usług HTTP NetX</span><span class="sxs-lookup"><span data-stu-id="a3b2a-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="a3b2a-104">Ten rozdział zawiera opis wszystkich usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="a3b2a-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="a3b2a-106">**Usługi klienta HTTP:**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="a3b2a-107">nx_http_client_create *utworzyć wystąpienia klienta http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="a3b2a-108">nx_http_client_delete *usunąć wystąpienia klienta http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="a3b2a-109">nx_http_client_get_start *uruchomić żądania HTTP GET*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="a3b2a-110">nx_http_client_get_start_extended *uruchomić żądania HTTP GET*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="a3b2a-111">nx_http_client_get_packet *Pobierz następny pakiet danych zasobów*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="a3b2a-112">nx_http_client_put_start *uruchomić żądanie HTTP Put*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="a3b2a-113">nx_http_client_put_start_extended *uruchomić żądanie HTTP Put*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="a3b2a-114">nx_http_client_put_packet *Wyślij następny pakiet danych zasobu*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="a3b2a-115">*nx_http_client_set_connect_port* *zmienić portu w celu nawiązania połączenia z serwerem HTTP*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="a3b2a-116">**Usługi serwera HTTP:**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="a3b2a-117">nx_http_server_cache_info_callback_set *ustawić wywołania zwrotnego, aby pobrać wiek i datę ostatniej modyfikacji określonego adresu URL*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="a3b2a-118">nx_http_server_callback_data_send *wysyłać danych http z funkcji wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="a3b2a-119">nx_http_server_callback_generate_response_header *utworzyć nagłówka odpowiedzi w funkcjach wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="a3b2a-120">nx_http_server_callback_generate_response_header_extended *utworzyć nagłówka odpowiedzi w funkcjach wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="a3b2a-121">nx_http_server_callback_packet_send *wysłać pakietu http z wywołania zwrotnego http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="a3b2a-122">nx_http_server_callback_response_send *wysyłanie odpowiedzi z funkcji wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="a3b2a-123">nx_http_server_callback_response_send_extended *wysyłanie odpowiedzi z funkcji wywołania zwrotnego*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="a3b2a-124">nx_http_server_content_get *pobrać zawartości z żądania*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="a3b2a-125">nx_http_server_content_get_extended *pobrać zawartości z żądania; obsługuje puste (zerowe długości zawartości)*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="a3b2a-126">nx_http_server_content_length_get *uzyskać długość zawartości w żądaniu*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="a3b2a-127">nx_http_server_content_length_get_extended *uzyskać długość zawartości w żądaniu; obsługuje puste (zerowe długości zawartości)*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="a3b2a-128">nx_http_server_create *utworzyć wystąpienia serwera http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="a3b2a-129">nx_http_server_delete *usunąć wystąpienia serwera http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="a3b2a-130">nx_http_server_get_entity_content *zwracanie rozmiaru i lokalizacji zawartości jednostki w adresie URL*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="a3b2a-131">nx_http_server_get_entity_header *Wyodrębnij nagłówka jednostki adresów URL do określonego buforu*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="a3b2a-132">nx_http_server_gmt_callback_set *ustawić wywołania zwrotnego, aby pobrać datę i godzinę GMT*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="a3b2a-133">nx_http_server_invalid_userpassword_notify_set *ustawić wywołania zwrotnego dla momentu odebrania nieprawidłowej nazwy użytkownika i hasła w żądaniu klienta*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="a3b2a-134">nx_http_server_mime_maps_additional_set *zdefiniować dodatkowe mapy MIME dla HTML*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="a3b2a-135">nx_http_server_packet_content_find *Wyodrębnij długość zawartości w nagłówku HTTP i ustaw wskaźnik na początek danych zawartości*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="a3b2a-136">nx_http_server_packet_get *odebrać pakiet klienta bezpośrednio*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="a3b2a-137">nx_http_server_param_get *uzyskać parametru z żądania*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="a3b2a-138">nx_http_server_query_get *uzyskać zapytania z żądania*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="a3b2a-139">nx_http_server_start *uruchomić serwer http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="a3b2a-140">nx_http_server_stop *zatrzymać serwer http*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="a3b2a-141">nx_http_server_type_get *Wyodrębnij typu http, np. Text/zwykły z nagłówka*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="a3b2a-142">nx_http_server_type_get_extended *Wyodrębnij typu http, np. Text/zwykły z nagłówka*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="a3b2a-143">nx_http_server_digest_authenticate_notify_set *Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="a3b2a-144">nx_http_server_authentication_check_set *Ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="a3b2a-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="a3b2a-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="a3b2a-146">Tworzenie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="a3b2a-147">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="a3b2a-148">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-148">**Description**</span></span>

<span data-ttu-id="a3b2a-149">Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="a3b2a-150">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-150">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-151">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-152">**CLIENT_NAME** Nazwa wystąpienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="a3b2a-153">**ip_ptr** Wskaźnik na wystąpienie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="a3b2a-154">**pool_ptr** Wskaźnik do domyślnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="a3b2a-155">Należy pamiętać, że pakiety w tej puli muszą mieć wystarczającą ilość ładunku, aby obsłużyć pełny nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="a3b2a-156">Jest on definiowany przez NX_HTTP_CLIENT_MIN_PACKET_SIZE w *nx_http_client. h*.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="a3b2a-157">**window_size** Rozmiar okna odbierania gniazda TCP klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="a3b2a-158">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-158">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-159">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="a3b2a-160">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="a3b2a-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="a3b2a-161">NX_HTTP_POOL_ERROR (0xE9) Nieprawidłowy rozmiar ładunku w puli pakietów</span><span class="sxs-lookup"><span data-stu-id="a3b2a-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="a3b2a-162">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-162">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-163">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-163">Initialization, Threads</span></span>

<span data-ttu-id="a3b2a-164">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="a3b2a-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="a3b2a-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="a3b2a-166">Usuwanie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="a3b2a-167">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="a3b2a-168">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-168">**Description**</span></span>

<span data-ttu-id="a3b2a-169">Ta usługa usuwa poprzednio utworzone wystąpienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="a3b2a-170">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-170">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-171">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="a3b2a-172">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-172">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-173">**NX_SUCCESS** (0X00) pomyślne usunięcie klienta http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="a3b2a-174">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="a3b2a-175">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-176">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-176">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-177">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-177">Threads</span></span>

<span data-ttu-id="a3b2a-178">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="a3b2a-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="a3b2a-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="a3b2a-180">Rozpocznij żądanie HTTP GET</span><span class="sxs-lookup"><span data-stu-id="a3b2a-180">Start an HTTP GET request</span></span>

<span data-ttu-id="a3b2a-181">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="a3b2a-182">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-182">**Description**</span></span>

<span data-ttu-id="a3b2a-183">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a3b2a-184">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a3b2a-185">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a3b2a-186">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-186">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-187">Deweloperzy są zachęcani do migracji do *nx_http_client_get_start_extended ()*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="a3b2a-188">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-188">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-189">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-190">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-191">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a3b2a-192">**input_ptr** Wskaźnik na dodatkowe dane żądania GET.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="a3b2a-193">Jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-193">This is optional.</span></span> <span data-ttu-id="a3b2a-194">Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="a3b2a-195">**input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez input_ptr.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="a3b2a-196">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a3b2a-197">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="a3b2a-198">
-\*\*WAIT_OPTION*\* Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a3b2a-199">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a3b2a-200">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="a3b2a-201">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="a3b2a-202">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="a3b2a-203">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="a3b2a-204">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-204">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-205">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a3b2a-206">Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="a3b2a-207">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="a3b2a-208">**NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-209">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="a3b2a-210">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-211">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="a3b2a-212">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-212">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-213">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-213">Threads</span></span>

<span data-ttu-id="a3b2a-214">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="a3b2a-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="a3b2a-216">Rozpocznij żądanie HTTP GET</span><span class="sxs-lookup"><span data-stu-id="a3b2a-216">Start an HTTP GET request</span></span>

<span data-ttu-id="a3b2a-217">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="a3b2a-218">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-218">**Description**</span></span>

<span data-ttu-id="a3b2a-219">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a3b2a-220">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_http_client_get_packet* , aby pobrać pakiety danych odpowiadające żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a3b2a-221">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a3b2a-222">Ta usługa zastępuje *nx_http_client_get_start ()*.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="a3b2a-223">Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="a3b2a-224">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-224">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-225">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-226">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-227">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a3b2a-228">**resource_length** Długość ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="a3b2a-229">**input_ptr** Wskaźnik na dodatkowe dane żądania GET.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="a3b2a-230">Jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-230">This is optional.</span></span> <span data-ttu-id="a3b2a-231">Jeśli wartość jest prawidłowa, określone dane wejściowe są umieszczane w obszarze zawartości wiadomości i zamiast operacji GET zostanie użyty wpis.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="a3b2a-232">**input_size** Liczba bajtów w opcjonalnym dodatkowym wejściu wskazywanym przez input_ptr.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="a3b2a-233">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a3b2a-234">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="a3b2a-235">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a3b2a-236">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="a3b2a-237">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a3b2a-238">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a3b2a-239">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="a3b2a-240">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="a3b2a-241">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="a3b2a-242">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="a3b2a-243">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-243">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-244">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a3b2a-245">Błąd wewnętrzny klienta HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="a3b2a-246">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="a3b2a-247">**NX_HTTP_FAILED** (0xE2) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-248">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="a3b2a-249">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-250">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="a3b2a-251">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-251">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-252">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-252">Threads</span></span>

<span data-ttu-id="a3b2a-253">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="a3b2a-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="a3b2a-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="a3b2a-255">Pobierz następny pakiet danych zasobów</span><span class="sxs-lookup"><span data-stu-id="a3b2a-255">Get next resource data packet</span></span>

<span data-ttu-id="a3b2a-256">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="a3b2a-257">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-257">**Description**</span></span>

<span data-ttu-id="a3b2a-258">Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie wywołanie *nx_http_client_get_start* .</span><span class="sxs-lookup"><span data-stu-id="a3b2a-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="a3b2a-259">Kolejne wywołania tej procedury należy wprowadzać do momentu otrzymania stanu powrotu NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="a3b2a-260">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-260">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-261">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-262">**packet_ptr** Miejsce docelowe dla wskaźnika pakietu zawierającego częściową zawartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="a3b2a-263">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na pobieranie pakietu przez klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="a3b2a-264">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a3b2a-265">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="a3b2a-266">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="a3b2a-267">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="a3b2a-268">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="a3b2a-269">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-269">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-270">**NX_SUCCESS** (0X00) pomyślne pobieranie pakietu przez klienta http.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="a3b2a-271">**NX_HTTP_GET_DONE** (0XEC) http Get pakiet klienta jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="a3b2a-272">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest w trybie pobierania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="a3b2a-273">**NX_HTTP_BAD_PACKET_LENGTH** (0XED) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="a3b2a-274">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-275">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-276">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-276">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-277">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-277">Threads</span></span>

<span data-ttu-id="a3b2a-278">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="a3b2a-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="a3b2a-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="a3b2a-280">Rozpocznij żądanie HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="a3b2a-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="a3b2a-281">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="a3b2a-282">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-282">**Description**</span></span>

<span data-ttu-id="a3b2a-283">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP o podanym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="a3b2a-284">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_http_client_put_packet* , aby faktycznie wysyłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a3b2a-285">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a3b2a-286">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-286">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-287">Deweloperzy są zachęcani do migracji do *nx_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="a3b2a-288">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-288">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-289">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-290">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-291">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a3b2a-292">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a3b2a-293">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a3b2a-294">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a3b2a-295">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="a3b2a-296">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="a3b2a-297">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a3b2a-298">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="a3b2a-299">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="a3b2a-300">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="a3b2a-301">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="a3b2a-302">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-302">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-303">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="a3b2a-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a3b2a-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="a3b2a-305">**(0xF1) nazwa użytkownika jest zbyt duża dla buforu**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="a3b2a-306">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="a3b2a-307">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-308">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a3b2a-309">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-310">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-310">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-311">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-311">Threads</span></span>

<span data-ttu-id="a3b2a-312">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="a3b2a-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="a3b2a-314">Rozpocznij żądanie HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="a3b2a-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="a3b2a-315">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="a3b2a-316">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-316">**Description**</span></span>

<span data-ttu-id="a3b2a-317">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP o podanym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="a3b2a-318">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_http_client_put_packet* , aby faktycznie wysyłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a3b2a-319">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a3b2a-320">Ta usługa zastępuje *nx_http_client_put_start ()*.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="a3b2a-321">Wymaga, aby obiekt wywołujący określił długość zasobu, nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="a3b2a-322">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-322">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-323">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-324">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-325">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a3b2a-326">**resource_length** Długość ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a3b2a-327">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a3b2a-328">**username_length** Długość opcjonalnej nazwy użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="a3b2a-329">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a3b2a-330">**password_length** Długość opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="a3b2a-331">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a3b2a-332">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_http_client_put_packet* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="a3b2a-333">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na uruchomienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="a3b2a-334">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a3b2a-335">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="a3b2a-336">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="a3b2a-337">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="a3b2a-338">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="a3b2a-339">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-339">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-340">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="a3b2a-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a3b2a-341">**NX_HTTP_USERNAME_TOO_LONG** (0XF1) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="a3b2a-342">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="a3b2a-343">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-344">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a3b2a-345">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-346">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-346">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-347">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-347">Threads</span></span>

<span data-ttu-id="a3b2a-348">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="a3b2a-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="a3b2a-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="a3b2a-350">Wyślij następny pakiet danych zasobu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-350">Send next resource data packet</span></span>

<span data-ttu-id="a3b2a-351">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="a3b2a-352">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-352">**Description**</span></span>

<span data-ttu-id="a3b2a-353">Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="a3b2a-354">Należy zauważyć, że ta procedura powinna być wywoływana kilkukrotnie do momentu, aż łączna długość wysłanych pakietów jest równa "total_bytes" określonej w poprzednim wywołaniu *nx_http_client_put_start ()* .</span><span class="sxs-lookup"><span data-stu-id="a3b2a-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="a3b2a-355">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-355">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-356">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-357">**packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="a3b2a-358">**WAIT_OPTION** Określa, jak długo usługa będzie czekać wewnętrznie na przetwarzanie pakietu klienta HTTP PUT.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="a3b2a-359">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a3b2a-360">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="a3b2a-361">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="a3b2a-362">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer HTTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="a3b2a-363">Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="a3b2a-364">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-364">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-365">**NX_SUCCESS** (0X00) pomyślnie wysłał pakiet klienta http.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="a3b2a-366">Klient HTTP **NX_HTTP_NOT_READY** (0xEA) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="a3b2a-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0XEE) otrzymał kod błędu serwera \* *-\*\*NX_HTTP_BAD_PACKET_LENGTH*\* (0xed) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="a3b2a-368">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) Nieprawidłowa nazwa i/lub hasło</span><span class="sxs-lookup"><span data-stu-id="a3b2a-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="a3b2a-369">Serwer **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) reaguje przed UKOŃCZeniem umieszczania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="a3b2a-370">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-371">Pakiet NX_INVALID_PACKET (0x12) jest za mały dla nagłówka TCP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="a3b2a-372">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-373">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-373">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-374">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-374">Threads</span></span>

<span data-ttu-id="a3b2a-375">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="a3b2a-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="a3b2a-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="a3b2a-377">Ustaw port połączenia na serwer</span><span class="sxs-lookup"><span data-stu-id="a3b2a-377">Set the connection port to the Server</span></span>

<span data-ttu-id="a3b2a-378">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="a3b2a-379">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-379">**Description**</span></span>

<span data-ttu-id="a3b2a-380">Ta usługa zmienia port połączenia podczas nawiązywania połączenia z serwerem HTTP do określonego portu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="a3b2a-381">W przeciwnym razie wartość domyślna portu połączenia to 80.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="a3b2a-382">Ta wartość musi być wywoływana przed *nx_http_client_get_start*() i *nx_http_client_put_start*(), np. gdy klient http nawiązuje połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="a3b2a-383">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-383">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-384">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a3b2a-385">**port** Port służący do nawiązywania połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="a3b2a-386">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-386">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-387">**NX_SUCCESS** (0X00) pomyślnie zmienił port połączenia</span><span class="sxs-lookup"><span data-stu-id="a3b2a-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="a3b2a-388">Port **NX_INVALID_PORT** (0x46) przekracza wartość maksymalną (0xFFFF) lub równą zero.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="a3b2a-389">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-390">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-390">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-391">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="a3b2a-391">Threads, Initialization</span></span>

<span data-ttu-id="a3b2a-392">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="a3b2a-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="a3b2a-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="a3b2a-394">Ustawianie wywołania zwrotnego do pobierania adresu URL maksymalny wiek i Data</span><span class="sxs-lookup"><span data-stu-id="a3b2a-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="a3b2a-395">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="a3b2a-396">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-396">**Description**</span></span>

<span data-ttu-id="a3b2a-397">Ta usługa ustawia wywołana usługa wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="a3b2a-398">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-398">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-399">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-400">**cache_info_get** Wskaźnik do wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="a3b2a-401">**max_age** Wskaźnik do maksymalnego wieku zasobu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="a3b2a-402">**dane** Zwrócono wskaźnik do daty ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="a3b2a-403">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-403">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-404">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a3b2a-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a3b2a-405">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-406">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-406">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-407">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="a3b2a-407">Initialization</span></span>

<span data-ttu-id="a3b2a-408">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="a3b2a-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="a3b2a-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="a3b2a-410">Wyślij dane z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-410">Send data from callback function</span></span>

<span data-ttu-id="a3b2a-411">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="a3b2a-412">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-412">**Description**</span></span>

<span data-ttu-id="a3b2a-413">Ta usługa wysyła dane z dostarczonego pakietu z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="a3b2a-414">Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="a3b2a-415">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="a3b2a-416">Ponadto procedura wywołania zwrotnego musi zwracać stan NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a3b2a-417">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-417">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-418">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-419">**data_ptr** Wskaźnik do danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="a3b2a-420">**data_length** Liczba bajtów do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="a3b2a-421">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-421">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-422">**NX_SUCCESS** (0X00) pomyślnie przesłał dane serwera</span><span class="sxs-lookup"><span data-stu-id="a3b2a-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="a3b2a-423">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-424">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-424">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-425">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-425">Threads</span></span>

<span data-ttu-id="a3b2a-426">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="a3b2a-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="a3b2a-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="a3b2a-428">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-428">Create a response header in a callback function</span></span>

<span data-ttu-id="a3b2a-429">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="a3b2a-430">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-430">**Description**</span></span>

<span data-ttu-id="a3b2a-431">Ta usługa wywołuje funkcję wewnętrzną _ *nx_http_server_generate_response_header* , gdy serwer http odpowiada na żądania GET, PUT i DELETE klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="a3b2a-432">Jest ona przeznaczona do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje odpowiedź na klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="a3b2a-433">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-433">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-434">Deweloperzy są zachęcani do migracji do *nxd_http_server_callback_generate_response_header_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="a3b2a-435">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-435">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-436">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-437">**packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości</span><span class="sxs-lookup"><span data-stu-id="a3b2a-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="a3b2a-438">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="a3b2a-439">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-439">Examples:</span></span>
- <span data-ttu-id="a3b2a-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="a3b2a-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="a3b2a-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="a3b2a-443">**CONTENT_LENGTH** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="a3b2a-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="a3b2a-444">**Content_Type** Typ HTTP np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="a3b2a-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="a3b2a-445">**additional_header** Wskaźnik na dodatkowy tekst nagłówka</span><span class="sxs-lookup"><span data-stu-id="a3b2a-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="a3b2a-446">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-446">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-447">**NX_SUCCESS** (0X00) pomyślnie UTWORZYŁ nagłówek HTML</span><span class="sxs-lookup"><span data-stu-id="a3b2a-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="a3b2a-448">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-449">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-449">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-450">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-450">Threads</span></span>

<span data-ttu-id="a3b2a-451">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="a3b2a-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="a3b2a-453">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-453">Create a response header in a callback function</span></span>

<span data-ttu-id="a3b2a-454">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-454">**Prototype**</span></span>

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

<span data-ttu-id="a3b2a-455">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-455">**Description**</span></span>

<span data-ttu-id="a3b2a-456">Ta usługa wywołuje funkcję wewnętrzną _ *nx_http_server_generate_response_header ()* , gdy serwer http odpowiada na żądania GET, PUT i DELETE klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="a3b2a-457">Jest ona przeznaczona do użycia w funkcjach wywołania zwrotnego serwera HTTP, gdy aplikacja serwera HTTP projektuje odpowiedź na klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="a3b2a-458">Ta usługa zastępuje *nx_http_server_callback_generate_response_header ()*.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="a3b2a-459">Ta wersja dostarcza dodatkowe informacje o długości do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="a3b2a-460">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-460">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-461">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-462">**packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości</span><span class="sxs-lookup"><span data-stu-id="a3b2a-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="a3b2a-463">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="a3b2a-464">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-464">Examples:</span></span>
  - <span data-ttu-id="a3b2a-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="a3b2a-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="a3b2a-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="a3b2a-468">**status_code** Długość kodu stanu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="a3b2a-469">**CONTENT_LENGTH** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="a3b2a-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="a3b2a-470">**Content_Type** Typ HTTP np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="a3b2a-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="a3b2a-471">**content_type_length** Długość typu HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="a3b2a-472">**additional_header** Wskaźnik na dodatkowy tekst nagłówka</span><span class="sxs-lookup"><span data-stu-id="a3b2a-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="a3b2a-473">**additional_header_length** Długość dodatkowego tekstu nagłówka</span><span class="sxs-lookup"><span data-stu-id="a3b2a-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="a3b2a-474">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-474">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-475">**NX_SUCCESS** (0X00) pomyślnie utworzył nagłówek</span><span class="sxs-lookup"><span data-stu-id="a3b2a-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="a3b2a-476">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-477">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-477">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-478">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-478">Threads</span></span>

<span data-ttu-id="a3b2a-479">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
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
                length, server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="a3b2a-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="a3b2a-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="a3b2a-481">Wyślij pakiet HTTP z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="a3b2a-482">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="a3b2a-483">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-483">**Description**</span></span>

<span data-ttu-id="a3b2a-484">Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="a3b2a-485">Serwer HTTP wyśle pakiet za pomocą _TIMEOUT_SEND NX_HTTP_SERVER.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="a3b2a-486">Nagłówek HTTP i dane muszą być dołączone do pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="a3b2a-487">Jeśli stan powrotu wskazuje na błąd, aplikacja HTTP musi zwolnić pakiet.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="a3b2a-488">Wywołanie zwrotne powinno zwracać NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a3b2a-489">Zobacz *nx_http_server_callback_generate_response_header ()* , aby zapoznać się z bardziej szczegółowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="a3b2a-490">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-490">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-491">**server_ptr** Wskaźnik do bloku kontroli serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="a3b2a-492">**packet_ptr** Wskaźnik do pakietu do wysłania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="a3b2a-493">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-493">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-494">**NX_SUCCESS** (0X00) pomyślnie wysłał pakiet serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="a3b2a-495">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-496">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-496">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-497">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-497">Threads</span></span>

<span data-ttu-id="a3b2a-498">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="a3b2a-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="a3b2a-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="a3b2a-500">Wyślij odpowiedź z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-500">Send response from callback function</span></span>

<span data-ttu-id="a3b2a-501">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="a3b2a-502">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-502">**Description**</span></span>

<span data-ttu-id="a3b2a-503">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="a3b2a-504">Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="a3b2a-505">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a3b2a-506">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-506">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-507">Deweloperzy są zachęcani do migracji do *nx_http_server_callback_response_send_extended ().*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="a3b2a-508">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-508">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-509">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-510">**nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="a3b2a-511">**informacje** Wskaźnik na ciąg informacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="a3b2a-512">**additional_info** Wskaźnik na ciąg informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="a3b2a-513">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-513">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-514">**NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="a3b2a-515">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-515">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-516">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-516">Threads</span></span>

<span data-ttu-id="a3b2a-517">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="a3b2a-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="a3b2a-519">Wyślij odpowiedź z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-519">Send response from callback function</span></span>

<span data-ttu-id="a3b2a-520">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="a3b2a-521">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-521">**Description**</span></span>

<span data-ttu-id="a3b2a-522">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="a3b2a-523">Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="a3b2a-524">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a3b2a-525">Ta usługa zastępuje *nx_http_server_callback_response_send ().*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="a3b2a-526">Ta wersja pobiera informacje o długości jako argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="a3b2a-527">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-527">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-528">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-529">**nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="a3b2a-530">**header_length** Długość ciągu nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="a3b2a-531">**informacje** Wskaźnik na ciąg informacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="a3b2a-532">**information_length** Długość ciągu informacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="a3b2a-533">**additional_info** Wskaźnik na ciąg informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="a3b2a-534">**additional_info_length** Długość ciągu informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="a3b2a-535">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-535">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-536">**NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera</span><span class="sxs-lookup"><span data-stu-id="a3b2a-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="a3b2a-537">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-537">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-538">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-538">Threads</span></span>

<span data-ttu-id="a3b2a-539">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="a3b2a-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="a3b2a-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="a3b2a-541">Pobierz zawartość z żądania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-541">Get content from the request</span></span>

<span data-ttu-id="a3b2a-542">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="a3b2a-543">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-543">**Description**</span></span>

<span data-ttu-id="a3b2a-544">Ta usługa próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="a3b2a-545">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="a3b2a-546">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-546">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-547">Deweloperzy są zachęcani do migracji do nx_http_server_content_get_extended ().</span><span class="sxs-lookup"><span data-stu-id="a3b2a-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="a3b2a-548">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-548">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-549">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-550">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a3b2a-551">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a3b2a-552">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="a3b2a-553">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="a3b2a-554">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="a3b2a-555">**actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="a3b2a-556">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-556">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-557">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="a3b2a-558">Błąd wewnętrzny serwera HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="a3b2a-559">0xE7 — koniec zawartości żądania **NX_HTTP_DATA_END**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="a3b2a-560">**NX_HTTP_TIMEOUT** (0xE1) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu zawartości</span><span class="sxs-lookup"><span data-stu-id="a3b2a-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="a3b2a-561">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-562">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-563">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-563">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-564">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-564">Threads</span></span>

<span data-ttu-id="a3b2a-565">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="a3b2a-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="a3b2a-567">Pobierz zawartość z żądania/obsługuje długość zawartości o zerowej długości</span><span class="sxs-lookup"><span data-stu-id="a3b2a-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="a3b2a-568">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="a3b2a-569">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-569">**Description**</span></span>

<span data-ttu-id="a3b2a-570">Ta usługa jest niemal identyczna z *nx_http_server_content_get ()*; próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="a3b2a-571">Jednak obsługuje żądania o długości wartości zerowej (puste żądanie) jako prawidłowe żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="a3b2a-572">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="a3b2a-573">Ta usługa zastępuje *nx_http_server_content_get ().*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="a3b2a-574">Ta wersja wymaga od wywołującego podania dodatkowych informacji o długości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="a3b2a-575">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-575">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-576">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-577">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a3b2a-578">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a3b2a-579">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="a3b2a-580">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="a3b2a-581">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="a3b2a-582">**actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="a3b2a-583">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-583">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-584">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="a3b2a-585">Błąd wewnętrzny serwera HTTP **NX_HTTP_ERROR** (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="a3b2a-586">0xE7 — koniec zawartości żądania **NX_HTTP_DATA_END**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="a3b2a-587">**NX_HTTP_TIMEOUT** (0xE1) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="a3b2a-588">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-589">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-590">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-590">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-591">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-591">Threads</span></span>

<span data-ttu-id="a3b2a-592">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="a3b2a-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="a3b2a-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="a3b2a-594">Pobierz długość zawartości w żądaniu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-594">Get length of content in the request</span></span>

<span data-ttu-id="a3b2a-595">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="a3b2a-596">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-596">**Description**</span></span>

<span data-ttu-id="a3b2a-597">Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="a3b2a-598">W przypadku braku zawartości HTTP Ta procedura zwraca wartość zero.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="a3b2a-599">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="a3b2a-600">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-600">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-601">Deweloperzy są zachęcani do migracji do nx_http_server_content_length_get_extended ().</span><span class="sxs-lookup"><span data-stu-id="a3b2a-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="a3b2a-602">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-602">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-603">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a3b2a-604">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="a3b2a-605">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-605">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-606">**długość zawartości** W przypadku błędu zwracana jest wartość zero.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="a3b2a-607">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-607">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-608">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-608">Threads</span></span>

<span data-ttu-id="a3b2a-609">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="a3b2a-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="a3b2a-611">Pobierz długość zawartości w żądaniu/obsługuje długość zawartości równą zero</span><span class="sxs-lookup"><span data-stu-id="a3b2a-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="a3b2a-612">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="a3b2a-613">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-613">**Description**</span></span>

<span data-ttu-id="a3b2a-614">Ta usługa jest podobna do *nx_http_server_content_length_get ()*; próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="a3b2a-615">Jednak wartość zwracana wskazuje stan pomyślnego ukończenia, a rzeczywista wartość długości jest zwracana w wskaźniku wejściowym content_length.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="a3b2a-616">Jeśli nie ma żadnej zawartości HTTP o długości zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wskaźnik wejściowy wskazuje prawidłową długość (zero).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="a3b2a-617">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="a3b2a-618">Ta usługa zastępuje *nx_http_server_content_length_get*().</span><span class="sxs-lookup"><span data-stu-id="a3b2a-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="a3b2a-619">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-619">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-620">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a3b2a-621">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a3b2a-622">**CONTENT_LENGTH** Wskaźnik do wartości pobranej z pola długości zawartości</span><span class="sxs-lookup"><span data-stu-id="a3b2a-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="a3b2a-623">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-623">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-624">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="a3b2a-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) niewłaściwy format nagłówka http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="a3b2a-626">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-627">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-627">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-628">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-628">Threads</span></span>

<span data-ttu-id="a3b2a-629">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="a3b2a-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="a3b2a-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="a3b2a-631">Tworzenie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="a3b2a-632">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-632">**Prototype**</span></span>

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

<span data-ttu-id="a3b2a-633">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-633">**Description**</span></span>

<span data-ttu-id="a3b2a-634">Ta usługa tworzy wystąpienie serwera HTTP, które działa w kontekście jego własnego wątku ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="a3b2a-635">Opcjonalne *authentication_check* i *request_notify* procedury wywołania zwrotnego aplikacji umożliwiają kontrolę oprogramowania aplikacji przez podstawowe operacje serwera http.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="a3b2a-636">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-636">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-637">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a3b2a-638">**http_server_name** Wskaźnik na nazwę serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="a3b2a-639">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a3b2a-640">**media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="a3b2a-641">**stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="a3b2a-642">**stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="a3b2a-643">**authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="a3b2a-644">Jeśli jest określony, ta procedura jest wywoływana dla każdego żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="a3b2a-645">Jeśli ten parametr ma wartość NULL, żadne uwierzytelnianie nie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="a3b2a-646">**request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="a3b2a-647">Jeśli jest określony, ta procedura jest wywoływana przed przetworzeniem żądania przez serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="a3b2a-648">Pozwala to na aktualizowanie nazwy zasobu lub pól w ramach zasobu przed ukończeniem żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="a3b2a-649">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-649">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-650">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera http.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="a3b2a-651">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="a3b2a-652">Ładunek pakietu NX_HTTP_POOL_ERROR (0xE9) puli nie jest wystarczająco duży, aby można było zawierać pełne żądanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="a3b2a-653">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-653">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-654">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-654">Initialization, Threads</span></span>

<span data-ttu-id="a3b2a-655">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="a3b2a-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="a3b2a-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="a3b2a-657">Usuwanie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="a3b2a-658">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="a3b2a-659">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-659">**Description**</span></span>

<span data-ttu-id="a3b2a-660">Ta usługa usuwa poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="a3b2a-661">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-661">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-662">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="a3b2a-663">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-663">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-664">**NX_SUCCESS** (0X00) pomyślne usunięcie serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="a3b2a-665">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="a3b2a-666">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-667">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-667">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-668">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-668">Threads</span></span>

<span data-ttu-id="a3b2a-669">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="a3b2a-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="a3b2a-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="a3b2a-671">Pobierz lokalizację i długość danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="a3b2a-672">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="a3b2a-673">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-673">**Description**</span></span>

<span data-ttu-id="a3b2a-674">Ta usługa określa lokalizację początkową danych w bieżącej jednostce wieloczęściowej w odebranych komunikatach klienta i długość danych bez uwzględniania ciągu granicy.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="a3b2a-675">Serwer HTTP wewnętrznie aktualizuje własne przesunięcia, aby można było ponownie wywołać tę funkcję na tym samym datagramie klienta dla komunikatów z wieloma jednostkami.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="a3b2a-676">Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="a3b2a-677">Należy pamiętać, że NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="a3b2a-678">Aby uzyskać więcej informacji, zobacz *nx_http_server_get_entity_header* .</span><span class="sxs-lookup"><span data-stu-id="a3b2a-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="a3b2a-679">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-679">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-680">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a3b2a-681">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="a3b2a-682">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a3b2a-683">**available_offset** Wskaźnik do przesunięcia danych jednostki ze wskaźnika dołączania do pakietu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="a3b2a-684">**available_length** Wskaźnik do długości danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="a3b2a-685">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-685">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-686">**NX_SUCCESS** (0X00) pomyślnie pobrała rozmiar i lokalizację zawartości jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="a3b2a-687">Zawartość **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) dla wewnętrznych znaczników wieloczęściowych serwera http została już znaleziona</span><span class="sxs-lookup"><span data-stu-id="a3b2a-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="a3b2a-688">Błąd wewnętrzny serwera HTTP NX_HTTP_ERROR (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="a3b2a-689">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-690">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-690">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-691">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-691">Threads</span></span>

<span data-ttu-id="a3b2a-692">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="a3b2a-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="a3b2a-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="a3b2a-694">Pobierz zawartość nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="a3b2a-695">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="a3b2a-696">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-696">**Description**</span></span>

<span data-ttu-id="a3b2a-697">Ta usługa pobiera nagłówek jednostki do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="a3b2a-698">Serwer HTTP wewnętrznie aktualizuje własne wskaźniki, aby znaleźć następną wieloczęściową jednostkę w datagramie klienta z wieloma nagłówkami jednostek.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="a3b2a-699">Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="a3b2a-700">Należy pamiętać, że NX_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="a3b2a-701">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-701">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-702">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a3b2a-703">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="a3b2a-704">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a3b2a-705">**entity_header_buffer** Wskaźnik do lokalizacji do zapisania nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="a3b2a-706">**buffer_size** Rozmiar buforu wejściowego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="a3b2a-707">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-707">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-708">**NX_SUCCESS** (0X00) pomyślnie pobrało nagłówek jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="a3b2a-709">**NX_HTTP_NOT_FOUND (0xE6)** Nie znaleziono pola nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="a3b2a-710">**NX_HTTP_TIMEOUT (0xE1)** Czas, który upłynął do odebrania następnego pakietu dla komunikatu klienta wielopakietowego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="a3b2a-711">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-712">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="a3b2a-713">Wewnętrzny błąd HTTP NX_HTTP_ERROR (wartość 0xE0)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="a3b2a-714">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-714">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-715">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-715">Threads</span></span>

<span data-ttu-id="a3b2a-716">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

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
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="a3b2a-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="a3b2a-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="a3b2a-718">Ustaw wywołanie zwrotne, aby uzyskać datę i godzinę GMT</span><span class="sxs-lookup"><span data-stu-id="a3b2a-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="a3b2a-719">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="a3b2a-720">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-720">**Description**</span></span>

<span data-ttu-id="a3b2a-721">Ta usługa ustawia wywołanie zwrotne, aby uzyskać datę i godzinę GMT z wcześniej utworzonym serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="a3b2a-722">Ta usługa jest wywoływana z serwerem HTTP tworzy nagłówek w odpowiedziach serwera HTTP dla klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="a3b2a-723">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-723">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-724">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a3b2a-725">**gmt_get** Wskaźnik do wywołania zwrotnego GMT</span><span class="sxs-lookup"><span data-stu-id="a3b2a-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="a3b2a-726">**Data** Wskaźnik do pobranej daty</span><span class="sxs-lookup"><span data-stu-id="a3b2a-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="a3b2a-727">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-727">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-728">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a3b2a-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a3b2a-729">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="a3b2a-730">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-730">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-731">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-731">Threads</span></span>

<span data-ttu-id="a3b2a-732">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="a3b2a-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="a3b2a-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="a3b2a-734">Ustaw wywołanie zwrotne w celu obsługi nieprawidłowego użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="a3b2a-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="a3b2a-735">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="a3b2a-736">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-736">**Description**</span></span>

<span data-ttu-id="a3b2a-737">Ta usługa ustawia wywołanie zwrotne wywoływane po odebraniu nieprawidłowej nazwy użytkownika i hasła do żądania GET, Put lub DELETE klienta w ramach uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="a3b2a-738">Należy wcześniej utworzyć serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="a3b2a-739">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-739">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-740">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a3b2a-741">**invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/przekazania wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="a3b2a-742">**zasób** Wskaźnik do zasobu określonego przez klienta</span><span class="sxs-lookup"><span data-stu-id="a3b2a-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="a3b2a-743">**client_address** Adres klienta</span><span class="sxs-lookup"><span data-stu-id="a3b2a-743">**client_address** Client address</span></span>
- <span data-ttu-id="a3b2a-744">**request_type** Wskazuje typ żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="a3b2a-745">Może:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-745">May be:</span></span>
  - <span data-ttu-id="a3b2a-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="a3b2a-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="a3b2a-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="a3b2a-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="a3b2a-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="a3b2a-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="a3b2a-749">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-749">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-750">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a3b2a-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a3b2a-751">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-752">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-752">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-753">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-753">Threads</span></span>

<span data-ttu-id="a3b2a-754">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="a3b2a-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="a3b2a-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="a3b2a-756">Ustaw dodatkowe mapy MIME dla HTML</span><span class="sxs-lookup"><span data-stu-id="a3b2a-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="a3b2a-757">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="a3b2a-758">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-758">**Description**</span></span>

<span data-ttu-id="a3b2a-759">Ta usługa umożliwia deweloperowi aplikacji protokołu HTTP Dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczonych przez NetX serwer HTTP (zobacz *nx_http_server_get_type* dla listy zdefiniowanych typów).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="a3b2a-760">Po odebraniu żądania klienta, np. żądanie GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu preferencyjnego dodatkowego zestawu mapowań MIME i jeśli nie jest zgodny, szuka dopasowania w domyślnej mapie MIME serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="a3b2a-761">Jeśli nie zostanie znalezione dopasowanie, typ MIME domyślnie przyjmuje wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a3b2a-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="a3b2a-762">Jeśli na serwerze HTTP zarejestrowano funkcję powiadamiania o żądaniu, wywołanie zwrotne powiadomienia o żądaniu może wywołać *nx_http_server_type_get* , aby przeanalizować typ pliku.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="a3b2a-763">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-763">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-764">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a3b2a-765">**mime_maps** Wskaźnik do tablicy mapy MIME</span><span class="sxs-lookup"><span data-stu-id="a3b2a-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="a3b2a-766">**mime_map_num** Liczba mapowań MIME w tablicy</span><span class="sxs-lookup"><span data-stu-id="a3b2a-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="a3b2a-767">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-767">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-768">**NX_SUCCESS** (0X00) pomyślne Ustawianie mapy MIME serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="a3b2a-769">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-770">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-770">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-771">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-771">Initialization, Threads</span></span>

<span data-ttu-id="a3b2a-772">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="a3b2a-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="a3b2a-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="a3b2a-774">Wyodrębnij długość zawartości i ustaw wskaźnik na początek danych</span><span class="sxs-lookup"><span data-stu-id="a3b2a-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="a3b2a-775">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="a3b2a-776">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-776">**Description**</span></span>

<span data-ttu-id="a3b2a-777">Ta usługa wyodrębnia długość zawartości z nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="a3b2a-778">Aktualizuje również podany pakiet w następujący sposób: wskaźnik dołączania pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) po prostu przekazały nagłówek HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="a3b2a-779">Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na odebranie następnego pakietu przy użyciu opcji oczekiwania NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="a3b2a-780">Należy zauważyć, że nie należy wywoływać przed wywołaniem *nx_http_server_get_entity_header ()* , ponieważ modyfikuje wskaźnik poprzedź przed nagłówkiem jednostki.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="a3b2a-781">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-781">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-782">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="a3b2a-783">**packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym wskaźnikiem dołączania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="a3b2a-784">**CONTENT_LENGTH** Wskaźnik do wyodrębnienia content_length</span><span class="sxs-lookup"><span data-stu-id="a3b2a-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="a3b2a-785">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-785">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-786">**NX_SUCCESS** (0x00) znaleziono długość zawartości http i pakiet został pomyślnie zaktualizowany</span><span class="sxs-lookup"><span data-stu-id="a3b2a-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="a3b2a-787">Czas **NX_HTTP_TIMEOUT** (0xE1) upłynął podczas oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="a3b2a-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="a3b2a-788">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-789">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-789">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-790">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-790">Threads</span></span>

<span data-ttu-id="a3b2a-791">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="a3b2a-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="a3b2a-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="a3b2a-793">Odbierz następny pakiet HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="a3b2a-794">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="a3b2a-795">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-795">**Description**</span></span>

<span data-ttu-id="a3b2a-796">Ta usługa zwraca następny pakiet odebrany w gnieździe serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="a3b2a-797">Opcja oczekiwania na odebranie pakietu jest NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="a3b2a-798">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-798">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-799">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="a3b2a-800">**packet_ptr** Wskaźnik do odebranego pakietu</span><span class="sxs-lookup"><span data-stu-id="a3b2a-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="a3b2a-801">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-801">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-802">**NX_SUCCESS** (0X00) pomyślnie otrzymał następny pakiet http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="a3b2a-803">Czas **NX_HTTP_TIMEOUT** (0xE1) upłynął podczas oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="a3b2a-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="a3b2a-804">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-805">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-805">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-806">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-806">Threads</span></span>

<span data-ttu-id="a3b2a-807">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="a3b2a-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="a3b2a-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="a3b2a-809">Pobierz parametr z żądania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-809">Get parameter from the request</span></span>

<span data-ttu-id="a3b2a-810">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="a3b2a-811">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-811">**Description**</span></span>

<span data-ttu-id="a3b2a-812">Ta usługa próbuje pobrać określony parametr HTTP URL w dostarczonym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="a3b2a-813">Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="a3b2a-814">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="a3b2a-815">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-815">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-816">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="a3b2a-817">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a3b2a-818">**param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="a3b2a-819">**param_ptr** Obszar docelowy do skopiowania parametru.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="a3b2a-820">**max_param_size** Maksymalny rozmiar obszaru docelowego parametru.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="a3b2a-821">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-821">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-822">**NX_SUCCESS** (0X00) pomyślne pobieranie PARAMETRU serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="a3b2a-823">Nie znaleziono podanego parametru **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="a3b2a-824">Parametr żądania **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) nie został poprawnie zakończony</span><span class="sxs-lookup"><span data-stu-id="a3b2a-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="a3b2a-825">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-826">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-827">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-827">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-828">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-828">Threads</span></span>

<span data-ttu-id="a3b2a-829">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="a3b2a-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="a3b2a-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="a3b2a-831">Pobierz zapytanie z żądania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-831">Get query from the request</span></span>

<span data-ttu-id="a3b2a-832">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="a3b2a-833">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-833">**Description**</span></span>

<span data-ttu-id="a3b2a-834">Ta usługa próbuje pobrać określoną kwerendę HTTP URL w dostarczonym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="a3b2a-835">Jeśli żądana kwerenda HTTP nie istnieje, ta procedura zwraca stan NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="a3b2a-836">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a3b2a-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="a3b2a-837">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-837">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-838">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="a3b2a-839">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a3b2a-840">**query_number** Numer logiczny parametru zaczynający się od zera od lewej do prawej na liście zapytań.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="a3b2a-841">**query_ptr** Obszar docelowy, w którym ma zostać skopiowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="a3b2a-842">**max_query_size** Maksymalny rozmiar obszaru docelowego zapytania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="a3b2a-843">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-843">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-844">**NX_SUCCESS** (0X00) pomyślne zapytanie serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="a3b2a-845">Rozmiar zapytania **NX_HTTP_FAILED** (0xE2) jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="a3b2a-846">Nie znaleziono określonego zapytania **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="a3b2a-847">**NX_HTTP_NO_QUERY_PARSED** (0XF2) brak zapytania w żądaniu klienta</span><span class="sxs-lookup"><span data-stu-id="a3b2a-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="a3b2a-848">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-849">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-850">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-850">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-851">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-851">Threads</span></span>

<span data-ttu-id="a3b2a-852">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="a3b2a-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="a3b2a-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="a3b2a-854">Uruchom serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-854">Start the HTTP Server</span></span>

<span data-ttu-id="a3b2a-855">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="a3b2a-856">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-856">**Description**</span></span>

<span data-ttu-id="a3b2a-857">Ta usługa uruchamia poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="a3b2a-858">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-858">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-859">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="a3b2a-860">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-860">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-861">**NX_SUCCESS** (0X00) pomyślne uruchomienie serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="a3b2a-862">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-863">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-863">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-864">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-864">Initialization, Threads</span></span>

<span data-ttu-id="a3b2a-865">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="a3b2a-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="a3b2a-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="a3b2a-867">Zatrzymaj serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-867">Stop the HTTP Server</span></span>

<span data-ttu-id="a3b2a-868">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="a3b2a-869">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-869">**Description**</span></span>

<span data-ttu-id="a3b2a-870">Ta usługa przerywa poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="a3b2a-871">Ta procedura powinna być wywoływana przed usunięciem wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="a3b2a-872">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-872">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-873">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="a3b2a-874">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-874">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-875">**NX_SUCCESS** (0X00) pomyślne zatrzymanie serwera http</span><span class="sxs-lookup"><span data-stu-id="a3b2a-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="a3b2a-876">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-877">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a3b2a-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="a3b2a-878">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-878">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-879">Wątki</span><span class="sxs-lookup"><span data-stu-id="a3b2a-879">Threads</span></span>

<span data-ttu-id="a3b2a-880">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="a3b2a-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="a3b2a-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="a3b2a-882">Wyodrębnij typ pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="a3b2a-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="a3b2a-883">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="a3b2a-884">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-884">**Description**</span></span>

<span data-ttu-id="a3b2a-885">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w zwracanej wartości z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="a3b2a-886">Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a3b2a-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="a3b2a-887">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="a3b2a-888">Domyślne mapy MIME na serwerze NetX HTTP są następujące:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="a3b2a-889">HTML text/html</span><span class="sxs-lookup"><span data-stu-id="a3b2a-889">html text/html</span></span>
- <span data-ttu-id="a3b2a-890">htm text/html</span><span class="sxs-lookup"><span data-stu-id="a3b2a-890">htm text/html</span></span>
- <span data-ttu-id="a3b2a-891">tekst txt/zwykły</span><span class="sxs-lookup"><span data-stu-id="a3b2a-891">txt text/plain</span></span>
- <span data-ttu-id="a3b2a-892">obraz GIF/GIF</span><span class="sxs-lookup"><span data-stu-id="a3b2a-892">gif image/gif</span></span>
- <span data-ttu-id="a3b2a-893">obraz JPG/JPEG</span><span class="sxs-lookup"><span data-stu-id="a3b2a-893">jpg image/jpeg</span></span>
- <span data-ttu-id="a3b2a-894">ikona obrazu ICO/x</span><span class="sxs-lookup"><span data-stu-id="a3b2a-894">ico image/x-icon</span></span>

<span data-ttu-id="a3b2a-895">Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="a3b2a-896">Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_http_server_mime_maps_addtional_set ()* .</span><span class="sxs-lookup"><span data-stu-id="a3b2a-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="a3b2a-897">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-897">This service is deprecated.</span></span> <span data-ttu-id="a3b2a-898">Deweloperzy są zachęcani do migracji do *nx_http_server_type_get_extended ().*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="a3b2a-899">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-899">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-900">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a3b2a-901">**Nazwa** Wskaźnik do buforu do przeszukania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="a3b2a-902">**http_type_string** (wskaźnik do wyodrębnionego typu html)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="a3b2a-903">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-903">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-904">**Długość ciągu w bajtach** Wartość różna od zera to sukces</span><span class="sxs-lookup"><span data-stu-id="a3b2a-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="a3b2a-905">**Zero oznacza błąd**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-905">**Zero indicates error**</span></span>

<span data-ttu-id="a3b2a-906">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-906">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-907">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a3b2a-907">Application</span></span>

<span data-ttu-id="a3b2a-908">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="a3b2a-909">Aby zapoznać się z bardziej szczegółowym przykładem, zobacz Opis</span><span class="sxs-lookup"><span data-stu-id="a3b2a-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="a3b2a-910">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="a3b2a-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="a3b2a-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="a3b2a-912">Wyodrębnij typ pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="a3b2a-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="a3b2a-913">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="a3b2a-914">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-914">**Description**</span></span>

<span data-ttu-id="a3b2a-915">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w zwracanej wartości z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="a3b2a-916">Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a3b2a-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="a3b2a-917">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="a3b2a-918">Domyślne mapy MIME na serwerze HTTP NetX Duo są następujące:</span><span class="sxs-lookup"><span data-stu-id="a3b2a-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="a3b2a-919">HTML text/html</span><span class="sxs-lookup"><span data-stu-id="a3b2a-919">html text/html</span></span>
- <span data-ttu-id="a3b2a-920">htm text/html</span><span class="sxs-lookup"><span data-stu-id="a3b2a-920">htm text/html</span></span>
- <span data-ttu-id="a3b2a-921">tekst txt/zwykły</span><span class="sxs-lookup"><span data-stu-id="a3b2a-921">txt text/plain</span></span>
- <span data-ttu-id="a3b2a-922">obraz GIF/GIF</span><span class="sxs-lookup"><span data-stu-id="a3b2a-922">gif image/gif</span></span>
- <span data-ttu-id="a3b2a-923">obraz JPG/JPEG</span><span class="sxs-lookup"><span data-stu-id="a3b2a-923">jpg image/jpeg</span></span>
- <span data-ttu-id="a3b2a-924">ikona obrazu ICO/x</span><span class="sxs-lookup"><span data-stu-id="a3b2a-924">ico image/x-icon</span></span>

<span data-ttu-id="a3b2a-925">Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="a3b2a-926">Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_http_server_mime_maps_addtional_set ()* .</span><span class="sxs-lookup"><span data-stu-id="a3b2a-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="a3b2a-927">Ta usługa zastępuje *nx_http_server_type_get ().*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="a3b2a-928">Ta wersja dostarcza dodatkowe informacje o długości.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-928">This version supplies additional length information.</span></span>

<span data-ttu-id="a3b2a-929">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-929">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-930">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a3b2a-931">**Nazwa** Wskaźnik do buforu do przeszukania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="a3b2a-932">**name_length** Długość buforu do wyszukania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="a3b2a-933">**http_type_string** (wskaźnik do wyodrębnionego typu html)</span><span class="sxs-lookup"><span data-stu-id="a3b2a-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="a3b2a-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="a3b2a-935">Rozmiar buforu *http_type_string*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="a3b2a-936">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-936">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-937">**Długość ciągu w bajtach** Wartość różna od zera to sukces</span><span class="sxs-lookup"><span data-stu-id="a3b2a-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="a3b2a-938">Zero oznacza błąd</span><span class="sxs-lookup"><span data-stu-id="a3b2a-938">Zero indicates error</span></span>

<span data-ttu-id="a3b2a-939">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-939">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-940">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a3b2a-940">Application</span></span>

<span data-ttu-id="a3b2a-941">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

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
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="a3b2a-942">Aby zapoznać się z bardziej szczegółowym przykładem, zobacz Opis</span><span class="sxs-lookup"><span data-stu-id="a3b2a-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="a3b2a-943">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="a3b2a-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="a3b2a-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="a3b2a-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="a3b2a-945">Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="a3b2a-946">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-946">**Prototype**</span></span>

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

<span data-ttu-id="a3b2a-947">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-947">**Description**</span></span>

<span data-ttu-id="a3b2a-948">Ta usługa ustawia wywołanie zwrotne wywoływane po wykonaniu uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="a3b2a-949">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-949">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-950">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a3b2a-951">**digest_authenticate_callback** Wskaźnik do wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="a3b2a-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="a3b2a-952">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-952">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-953">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a3b2a-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a3b2a-954">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a3b2a-955">NX_NOT_SUPPORTED (0x4B) uwierzytelnianie szyfrowane nie jest włączone</span><span class="sxs-lookup"><span data-stu-id="a3b2a-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="a3b2a-956">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-956">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-957">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a3b2a-957">Application</span></span>

<span data-ttu-id="a3b2a-958">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="a3b2a-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="a3b2a-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="a3b2a-960">Ustaw funkcję wywołania zwrotnego sprawdzania uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="a3b2a-960">Set authentication checking callback function</span></span>

<span data-ttu-id="a3b2a-961">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-961">**Prototype**</span></span>

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

<span data-ttu-id="a3b2a-962">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-962">**Description**</span></span>

<span data-ttu-id="a3b2a-963">Ta usługa ustawia funkcję wywołania zwrotnego sprawdzania uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3b2a-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="a3b2a-964">**Parametry wejściowe**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-964">**Input Parameters**</span></span>

- <span data-ttu-id="a3b2a-965">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a3b2a-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a3b2a-966">**authentication_check_extended** Wskaźnik do sprawdzania uwierzytelniania aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3b2a-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="a3b2a-967">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-967">**Return Values**</span></span>

- <span data-ttu-id="a3b2a-968">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a3b2a-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a3b2a-969">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a3b2a-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="a3b2a-970">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-970">**Allowed From**</span></span>

<span data-ttu-id="a3b2a-971">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a3b2a-971">Application</span></span>

<span data-ttu-id="a3b2a-972">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="a3b2a-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```