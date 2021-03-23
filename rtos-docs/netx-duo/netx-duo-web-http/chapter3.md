---
title: Rozdział 3 — Opis usług HTTP
description: Ten rozdział zawiera opis wszystkich usług HTTP sieci Web NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30168ad5a564b0f4c0a8c999046c5103385f4f90
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822890"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="a9ad4-103">Rozdział 3 — Opis usług HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="a9ad4-104">Ten rozdział zawiera opis wszystkich usług HTTP sieci Web NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="a9ad4-106">Interfejs API klienta protokołu HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="a9ad4-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="a9ad4-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="a9ad4-108">Otwórz gniazdo zwykłego tekstu na serwerze HTTP dla żądań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a9ad4-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-109">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-110">Description</span></span>

<span data-ttu-id="a9ad4-111">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-112">Ta usługa otwiera gniazdo TCP w postaci zwykłego tekstu do serwera HTTP, ale nie wysyła żadnych żądań.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="a9ad4-113">Żądania są tworzone za pomocą n *x_web_http_client_request_initialize ()* i wysyłane przy użyciu *nx_web_http_client_request_send ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="a9ad4-114">Niestandardowe nagłówki HTTP można dodać do żądania przy użyciu *nx_web_http_client_request_header_add ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="a9ad4-115">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby niestandardowych nagłówków do żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="a9ad4-116">**Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-117">Metody nx_web_http_client_ \* _start są udostępniane dla wygody (np. *nx_web_http_client_get_start*()) i obsługują generowanie żądań i połączenie gniazda.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="a9ad4-118">Możesz użyć tych usług zamiast *nx_web_http_client_connect ()* i powiązanych procedur, jeśli nie potrzebujesz niestandardowych nagłówków HTTP w żądaniach.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-119">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-119">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-120">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-121">**server_IP** Adres IP zdalnego serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="a9ad4-122">**SERVER_PORT** Port na zdalnym serwerze HTTP (np. 80 dla protokołu HTTP).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="a9ad4-123">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na operacje w sieci.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="a9ad4-124">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-125">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-126">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-127">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-127">Return Values</span></span>

- <span data-ttu-id="a9ad4-128">**NX_SUCCESS** (0x00) powiodło się połączenie gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="a9ad4-129">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-130">NX_WEB_HTTP_NOT_READY (0x3000A) inne żądanie jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-131">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-131">Allowed From</span></span>

<span data-ttu-id="a9ad4-132">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-133">Example</span></span>

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="a9ad4-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="a9ad4-134">nx_web_http_client_create</span></span>

<span data-ttu-id="a9ad4-135">Tworzenie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-137">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-137">Description</span></span>

<span data-ttu-id="a9ad4-138">Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="a9ad4-139">Wystąpienia klienta można użyć w przypadku protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="a9ad4-140">Zobacz usługi *nx_web_http_client_connect ()* i *nx_web_http_client_secure_connect ()* , aby uzyskać więcej informacji na temat uruchamiania wystąpienia http lub https.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="a9ad4-141">Zapoznaj się również z interfejsem API dla \* nx_web_http_client_get_ \* \*, \*nx_web_http_client_put_ \* *, *nx_web_http_client_post_** dla prostych wywołań metod get, PUT i post.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-142">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-142">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-143">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-144">**CLIENT_NAME** Nazwa wystąpienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="a9ad4-145">**ip_ptr** Wskaźnik na wystąpienie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="a9ad4-146">**pool_ptr** Wskaźnik do domyślnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="a9ad4-147">Należy pamiętać, że pakiety w tej puli muszą mieć wystarczającą ilość ładunku, aby obsłużyć pełny nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="a9ad4-148">Jest on definiowany przez *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* w *nx_web_http_client. h*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="a9ad4-149">**window_size** Rozmiar okna odbierania gniazda TCP klienta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-150">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-150">Return Values</span></span>

- <span data-ttu-id="a9ad4-151">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="a9ad4-152">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="a9ad4-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="a9ad4-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Nieprawidłowy rozmiar ładunku w puli pakietów</span><span class="sxs-lookup"><span data-stu-id="a9ad4-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-154">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-154">Allowed From</span></span>

<span data-ttu-id="a9ad4-155">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="a9ad4-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="a9ad4-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="a9ad4-158">Usuwanie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-160">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-160">Description</span></span>

<span data-ttu-id="a9ad4-161">Ta usługa usuwa poprzednio utworzone wystąpienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-162">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-162">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-163">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-164">Return Values</span></span>

- <span data-ttu-id="a9ad4-165">**NX_SUCCESS** (0X00) pomyślne usunięcie klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="a9ad4-166">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="a9ad4-167">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-168">Allowed From</span></span>

<span data-ttu-id="a9ad4-169">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="a9ad4-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="a9ad4-172">Rozpocznij żądanie HTTP DELETE w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-174">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-174">Description</span></span>

<span data-ttu-id="a9ad4-175">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-176">Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-177">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a9ad4-178">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-179">Ten interfejs API jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-179">This API is deprecated.</span></span> <span data-ttu-id="a9ad4-180">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_delete_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-181">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-181">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-182">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-183">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-184">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-185">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-186">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-187">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-188">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-189">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-190">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-191">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-192">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-193">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-194">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-195">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-195">Return Values</span></span>

- <span data-ttu-id="a9ad4-196">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a9ad4-197">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-198">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-199">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-201">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-202">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-203">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-203">Allowed From</span></span>

<span data-ttu-id="a9ad4-204">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-205">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-205">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="a9ad4-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="a9ad4-207">Rozpocznij żądanie HTTP DELETE w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-208">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-209">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-209">Description</span></span>

<span data-ttu-id="a9ad4-210">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-211">Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-212">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a9ad4-213">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-214">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-215">Ta usługa zastępuje *nx_web_http_client_delete_start* ().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="a9ad4-216">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-217">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-217">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-218">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-219">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-220">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-221">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-222">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-223">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-224">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-225">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-226">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-227">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-228">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-229">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-230">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-231">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-232">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-233">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-234">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-235">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-235">Return Values</span></span>

- <span data-ttu-id="a9ad4-236">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a9ad4-237">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-238">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-239">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-241">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-242">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-243">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-243">Allowed From</span></span>

<span data-ttu-id="a9ad4-244">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-245">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-245">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="a9ad4-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="a9ad4-247">Rozpocznij zaszyfrowane żądanie usunięcia protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-249">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-249">Description</span></span>

<span data-ttu-id="a9ad4-250">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-251">Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-252">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a9ad4-253">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-254">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-254">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-255">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_delete_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-256">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-256">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-257">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-258">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-259">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-260">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="a9ad4-261">zasób musi być zakończony wartością NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="a9ad4-262">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-263">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-264">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-265">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-266">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-267">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-268">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-269">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-270">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-271">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-272">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-273">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-273">Return Values</span></span>

- <span data-ttu-id="a9ad4-274">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a9ad4-275">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-276">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-277">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-279">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-280">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-281">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-281">Allowed From</span></span>

<span data-ttu-id="a9ad4-282">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-283">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-283">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="a9ad4-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="a9ad4-285">Rozpocznij zaszyfrowane żądanie usunięcia protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-286">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-286">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-287">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-287">Description</span></span>

<span data-ttu-id="a9ad4-288">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-289">Ta usługa próbuje wysłać żądanie usunięcia dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-290">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a9ad4-291">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-292">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-293">Ta usługa zastępuje *nx_web_http_client_delete_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="a9ad4-294">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-295">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-295">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-296">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-297">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-298">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-299">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="a9ad4-300">zasób musi być zakończony wartością NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="a9ad4-301">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-302">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-303">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-304">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-305">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-306">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-307">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-308">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-309">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-310">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-311">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-312">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-313">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-314">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-315">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-316">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-316">Return Values</span></span>

- <span data-ttu-id="a9ad4-317">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania usunięcia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a9ad4-318">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-319">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-320">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-322">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-323">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a9ad4-324">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-324">Allowed From</span></span>

<span data-ttu-id="a9ad4-325">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-326">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-326">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="a9ad4-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="a9ad4-328">Uruchamianie żądania HTTP GET w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-329">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-330">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-330">Description</span></span>

<span data-ttu-id="a9ad4-331">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-332">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-333">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a9ad4-334">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-335">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-335">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-336">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_get_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-337">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-337">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-338">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-339">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-340">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-341">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-342">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-343">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-344">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-345">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-346">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-347">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-348">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-349">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-350">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-351">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-351">Return Values</span></span>

- <span data-ttu-id="a9ad4-352">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a9ad4-353">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-354">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-355">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-357">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-358">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-359">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-359">Allowed From</span></span>

<span data-ttu-id="a9ad4-360">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-361">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-361">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="a9ad4-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="a9ad4-363">Uruchamianie żądania HTTP GET w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-365">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-365">Description</span></span>

<span data-ttu-id="a9ad4-366">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-367">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-368">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a9ad4-369">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-370">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-371">Ta usługa zastępuje *nx_web_http_client_get_start*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="a9ad4-372">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-373">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-373">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-374">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-375">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-376">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-377">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-378">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-379">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-380">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-381">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-382">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-383">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-384">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-385">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-386">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-387">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-388">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-389">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-390">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-391">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-391">Return Values</span></span>

- <span data-ttu-id="a9ad4-392">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a9ad4-393">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-394">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-395">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-397">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-398">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-399">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-399">Allowed From</span></span>

<span data-ttu-id="a9ad4-400">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-401">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-401">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="a9ad4-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="a9ad4-403">Uruchamianie szyfrowanego żądania GET HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-405">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-405">Description</span></span>

<span data-ttu-id="a9ad4-406">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-407">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-408">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a9ad4-409">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-410">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-410">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-411">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_get_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-412">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-412">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-413">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-414">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-415">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-416">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-417">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-418">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-419">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-420">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-421">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-422">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-423">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-424">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-425">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-426">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-427">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-428">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-428">Return Values</span></span>

- <span data-ttu-id="a9ad4-429">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a9ad4-430">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-431">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-432">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-434">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-435">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-436">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-436">Allowed From</span></span>

<span data-ttu-id="a9ad4-437">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-438">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-438">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="a9ad4-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="a9ad4-440">Uruchamianie szyfrowanego żądania GET HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-441">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-442">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-442">Description</span></span>

<span data-ttu-id="a9ad4-443">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-444">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-445">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań *nx_web_http_client_response_body_get ()* , aby pobrać pakiety danych odpowiadające żądanym zawartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a9ad4-446">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-447">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-448">Ta usługa zastępuje *nx_web_http_client_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="a9ad4-449">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-450">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-450">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-451">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-452">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-453">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-454">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-455">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-456">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-457">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-458">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-459">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-460">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-461">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-462">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-463">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-464">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-465">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-466">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-467">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-468">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-469">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-470">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-470">Return Values</span></span>

- <span data-ttu-id="a9ad4-471">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat dotyczący uruchomienia klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a9ad4-472">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-473">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-474">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-476">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-477">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-478">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-478">Allowed From</span></span>

<span data-ttu-id="a9ad4-479">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-480">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-480">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="a9ad4-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="a9ad4-482">Uruchom żądanie HTTP z NAGŁÓWKIem zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-483">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-484">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-484">Description</span></span>

<span data-ttu-id="a9ad4-485">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-486">Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-487">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="a9ad4-488">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-489">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-489">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-490">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_head_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-491">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-491">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-492">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-493">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-494">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-495">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-496">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-497">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-498">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-499">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-500">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-501">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-502">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-503">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-504">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-505">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-505">Return Values</span></span>

- <span data-ttu-id="a9ad4-506">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a9ad4-507">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-508">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-509">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-511">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-512">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-513">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-513">Allowed From</span></span>

<span data-ttu-id="a9ad4-514">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-515">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-515">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="a9ad4-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="a9ad4-517">Uruchom żądanie HTTP z NAGŁÓWKIem zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-518">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-519">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-519">Description</span></span>

<span data-ttu-id="a9ad4-520">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-521">Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-522">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* w celu pobrania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="a9ad4-523">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-524">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-525">Ta usługa zastępuje *nx_web_http_client_head_start*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="a9ad4-526">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-527">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-527">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-528">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-529">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-530">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-531">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-532">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-533">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-534">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-535">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-536">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-537">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-538">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-539">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-540">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-541">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-542">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-543">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-544">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-545">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-545">Return Values</span></span>

- <span data-ttu-id="a9ad4-546">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a9ad4-547">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-548">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-549">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-551">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-552">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-553">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-553">Allowed From</span></span>

<span data-ttu-id="a9ad4-554">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-555">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-555">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="a9ad4-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="a9ad4-557">Rozpocznij zaszyfrowane żądanie HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-559">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-559">Description</span></span>

<span data-ttu-id="a9ad4-560">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-561">Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-562">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* , aby pobrać odpowiedź serwera odpowiadającą żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="a9ad4-563">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-564">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-564">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-565">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_head_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-566">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-566">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-567">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-568">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-569">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-570">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-571">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-572">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-573">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-574">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-575">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-576">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-577">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-578">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-579">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-580">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-581">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-582">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-582">Return Values</span></span>

- <span data-ttu-id="a9ad4-583">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a9ad4-584">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-585">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-586">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-588">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-589">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-590">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-590">Allowed From</span></span>

<span data-ttu-id="a9ad4-591">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-592">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-592">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="a9ad4-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="a9ad4-594">Rozpocznij zaszyfrowane żądanie HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-595">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-596">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-596">Description</span></span>

<span data-ttu-id="a9ad4-597">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-598">Ta usługa próbuje pobrać metadane główne dla zasobu określonego przez wskaźnik "zasób" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-599">Jeśli ta procedura zwróci NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get ()* , aby pobrać odpowiedź serwera odpowiadającą żądanym treści zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="a9ad4-600">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje żądania GET odwołujące się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a9ad4-601">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-602">Ta usługa zastępuje *nx_web_http_client_head_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="a9ad4-603">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-604">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-604">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-605">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-606">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-607">**SERVER_PORT** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-608">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-609">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-610">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-611">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-612">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-613">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-614">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-615">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-616">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-617">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-618">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-619">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-620">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-621">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-622">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-623">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-624">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-624">Return Values</span></span>

- <span data-ttu-id="a9ad4-625">**NX_SUCCESS** (0X00) pomyślnie wysłał komunikat żądania głównego klienta http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a9ad4-626">Błąd wewnętrzny klienta HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a9ad4-627">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-628">**NX_WEB_HTTP_FAILED** (0x30002) błąd klienta http podczas komunikacji z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a9ad4-630">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-631">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-632">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-632">Allowed From</span></span>

<span data-ttu-id="a9ad4-633">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-634">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-634">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="a9ad4-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a9ad4-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="a9ad4-636">Przydziel pakiet HTTP (S)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-637">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-638">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-638">Description</span></span>

<span data-ttu-id="a9ad4-639">Ta usługa próbuje przydzielić pakiet dla klienta HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-640">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-640">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-641">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-642">**packet_ptr** Wskaźnik do przydzielony pakiet.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="a9ad4-643">**WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="a9ad4-644">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="a9ad4-646">**NX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="a9ad4-647">**limit czasu w taktach** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-648">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-648">Return Values</span></span>

- <span data-ttu-id="a9ad4-649">Pomyślne przydzielenie pakietu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="a9ad4-650">**NX_NO_PACKET** (0X01) Brak dostępnego pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="a9ad4-651">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a9ad4-652">Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a9ad4-653">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-654">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-655">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-655">Allowed From</span></span>

<span data-ttu-id="a9ad4-656">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-657">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="a9ad4-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="a9ad4-659">Rozpocznij żądanie HTTP POST</span><span class="sxs-lookup"><span data-stu-id="a9ad4-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-660">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-661">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-661">Description</span></span>

<span data-ttu-id="a9ad4-662">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-663">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-664">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_web_http_client_put_packet* , aby wysłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-665">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-666">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-666">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-667">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_post_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-668">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-668">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-669">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-670">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-671">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-672">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a9ad4-673">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-674">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-675">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-676">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-677">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-678">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-679">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-680">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-681">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-682">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-683">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-684">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-684">Return Values</span></span>

- <span data-ttu-id="a9ad4-685">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post</span><span class="sxs-lookup"><span data-stu-id="a9ad4-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a9ad4-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-687">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-688">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-689">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-690">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-691">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-691">Allowed From</span></span>

<span data-ttu-id="a9ad4-692">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-693">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-693">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="a9ad4-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="a9ad4-695">Rozpocznij żądanie HTTP POST</span><span class="sxs-lookup"><span data-stu-id="a9ad4-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-696">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-697">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-697">Description</span></span>

<span data-ttu-id="a9ad4-698">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-699">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-700">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania do procedury *nx_web_http_client_put_packet* , aby wysłać zawartość zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-701">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-702">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-703">Ta usługa zastępuje *nx_web_http_client_post_start* ().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="a9ad4-704">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-705">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-705">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-706">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-707">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-708">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-709">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-710">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-711">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-712">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-713">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-714">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-715">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-716">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-717">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-718">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-719">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-720">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-721">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-722">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-723">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-724">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-725">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-725">Return Values</span></span>

- <span data-ttu-id="a9ad4-726">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post</span><span class="sxs-lookup"><span data-stu-id="a9ad4-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a9ad4-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-728">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-729">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-730">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-731">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-732">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-732">Allowed From</span></span>

<span data-ttu-id="a9ad4-733">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-734">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-734">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="a9ad4-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="a9ad4-736">Rozpocznij zaszyfrowane żądanie POST HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-737">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-737">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-738">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-738">Description</span></span>

<span data-ttu-id="a9ad4-739">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-740">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-741">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-742">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-743">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-743">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-744">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_post_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-745">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-745">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-746">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-747">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-748">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-749">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a9ad4-750">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-751">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-752">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-753">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-754">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-755">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-756">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-757">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-758">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-759">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-760">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-761">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-762">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-763">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-763">Return Values</span></span>

- <span data-ttu-id="a9ad4-764">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post</span><span class="sxs-lookup"><span data-stu-id="a9ad4-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a9ad4-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-766">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-767">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-768">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-769">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-770">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-770">Allowed From</span></span>

<span data-ttu-id="a9ad4-771">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-772">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-772">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="a9ad4-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="a9ad4-774">Rozpocznij zaszyfrowane żądanie POST HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-775">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-775">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-776">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-776">Description</span></span>

<span data-ttu-id="a9ad4-777">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-778">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-779">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-780">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-781">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-782">Ta usługa zastępuje *nx_web_http_client_post_secure_start* ().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="a9ad4-783">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-784">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-784">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-785">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-786">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-787">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-788">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-789">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-790">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-791">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-792">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-793">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-794">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-795">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-796">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-797">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-798">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-799">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-800">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-801">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-802">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-803">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-804">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-805">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-806">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-806">Return Values</span></span>

- <span data-ttu-id="a9ad4-807">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie post</span><span class="sxs-lookup"><span data-stu-id="a9ad4-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a9ad4-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-809">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-810">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-811">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-812">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-813">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-813">Allowed From</span></span>

<span data-ttu-id="a9ad4-814">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-815">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-815">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="a9ad4-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="a9ad4-817">Rozpocznij żądanie HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="a9ad4-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-819">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-819">Description</span></span>

<span data-ttu-id="a9ad4-820">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-821">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-822">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-823">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-824">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-824">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-825">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-826">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-826">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-827">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-828">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-829">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-830">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a9ad4-831">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-832">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-833">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-834">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-835">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-836">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-837">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-838">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-839">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-840">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-841">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-842">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-842">Return Values</span></span>

- <span data-ttu-id="a9ad4-843">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="a9ad4-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a9ad4-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-845">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-846">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-847">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-848">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-849">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-849">Allowed From</span></span>

<span data-ttu-id="a9ad4-850">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-851">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-851">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="a9ad4-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="a9ad4-853">Rozpocznij żądanie HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="a9ad4-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-854">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-855">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-855">Description</span></span>

<span data-ttu-id="a9ad4-856">Ta metoda jest dla **zwykłego tekstu** http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a9ad4-857">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP przy użyciu podanego adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-858">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-859">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-860">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-861">Ta usługa zastępuje *nx_web_http_client_put_start* ().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="a9ad4-862">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-863">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-863">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-864">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-865">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-866">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-867">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-868">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-869">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-870">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-871">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-872">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-873">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-874">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-875">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-876">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-877">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-878">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-879">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-880">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-881">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-882">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-883">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-883">Return Values</span></span>

- <span data-ttu-id="a9ad4-884">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="a9ad4-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a9ad4-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-886">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-887">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-888">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-889">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-890">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-890">Allowed From</span></span>

<span data-ttu-id="a9ad4-891">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-892">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-892">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="a9ad4-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="a9ad4-894">Uruchamianie szyfrowanego żądania PUT HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-895">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-896">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-896">Description</span></span>

<span data-ttu-id="a9ad4-897">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-898">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-899">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-900">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-901">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-901">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-902">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_put_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-903">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-903">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-904">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-905">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-906">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-907">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania na serwer.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a9ad4-908">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-909">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-910">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-911">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-912">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-913">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-914">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-915">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-916">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-917">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-918">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-919">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-920">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-921">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-921">Return Values</span></span>

- <span data-ttu-id="a9ad4-922">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="a9ad4-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a9ad4-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-924">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-925">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-926">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-927">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-928">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-928">Allowed From</span></span>

<span data-ttu-id="a9ad4-929">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-930">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-930">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="a9ad4-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="a9ad4-932">Uruchamianie szyfrowanego żądania PUT HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-933">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-933">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-934">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-934">Description</span></span>

<span data-ttu-id="a9ad4-935">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-936">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTPS o podanym adresie IP i porcie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a9ad4-937">Jeśli ta procedura zakończy się pomyślnie, kod aplikacji powinien wykonać kolejne wywołania procedury *nx_web_http_client_put_packet ()* w celu wysłania zawartości zasobów do serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-938">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, na przykład "/index.htm", lub może odwoływać się do innego adresu URL, np. `http://abc.website.com/index.htm` Jeśli serwer HTTP wskazuje, że obsługuje odwołania do żądań PUT.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a9ad4-939">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-940">Ta usługa zastępuje *nx_web_http_client_put_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="a9ad4-941">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-942">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-942">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-943">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-944">**IP_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-945">**SERVER_PORT** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-946">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a9ad4-947">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-948">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-949">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-950">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-951">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-952">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-953">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-954">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-955">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-956">**total_bytes** Całkowita liczba bajtów wysyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a9ad4-957">Należy zauważyć, że łączna długość wszystkich pakietów wysłanych przez kolejne wywołania do *nx_web_http_client_put_packet ()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a9ad4-958">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-959">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-960">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-961">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-962">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-963">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-964">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-964">Return Values</span></span>

- <span data-ttu-id="a9ad4-965">**NX_SUCCESS** (0X00) pomyślnie wysłał żądanie Put</span><span class="sxs-lookup"><span data-stu-id="a9ad4-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a9ad4-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a9ad4-967">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-968">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-969">NX_SIZE_ERROR (0x09) nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a9ad4-970">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-971">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-971">Allowed From</span></span>

<span data-ttu-id="a9ad4-972">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-973">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-973">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="a9ad4-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="a9ad4-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="a9ad4-975">Wyślij następny pakiet danych zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-977">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-977">Description</span></span>

<span data-ttu-id="a9ad4-978">Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP w przypadku operacji PUT i POST.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="a9ad4-979">Należy zauważyć, że ta procedura powinna być wywoływana kilkukrotnie do momentu, aż łączna długość wysłanych pakietów jest równa "total_bytes" określonej w poprzednim wywołaniu *nx_web_http_client_put_start ()* lub *nx_web_http_client_post_start ()* (lub w odpowiednich bezpiecznych wersjach).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="a9ad4-980">Ta usługa sprawdza także odpowiedź z serwera w przypadku wystąpienia problemu podczas ustanawiania połączenia HTTP (lub HTTPS).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-981">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-981">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-982">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-983">**packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="a9ad4-984">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-985">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-986">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-987">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-988">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-988">Return Values</span></span>

- <span data-ttu-id="a9ad4-989">**NX_SUCCESS** (0X00) pomyślnie wysłał pakiet klienta http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="a9ad4-990">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a9ad4-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0X3000E) otrzymał kod błędu serwera \* \*</span><span class="sxs-lookup"><span data-stu-id="a9ad4-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="a9ad4-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="a9ad4-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) Nieprawidłowa nazwa i/lub hasło</span><span class="sxs-lookup"><span data-stu-id="a9ad4-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="a9ad4-994">Serwer **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) reaguje przed UKOŃCZeniem umieszczania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="a9ad4-995">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-996">Pakiet NX_INVALID_PACKET (0x12) jest za mały dla nagłówka TCP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="a9ad4-997">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-998">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-998">Allowed From</span></span>

<span data-ttu-id="a9ad4-999">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1000">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="a9ad4-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="a9ad4-1002">Ustaw przemieszczenie fragmentaryczne dla żądania HTTP (S)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1003">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1004">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1004">Description</span></span>

<span data-ttu-id="a9ad4-1005">Ta usługa używa kodowania fragmentarycznego transferu do wysyłania niestandardowego żądania HTTP (S) do serwera określonego w wywołaniu *nx_web_http_client_connect ()* lub *nx_web_http_client_secure_connect ()* , który wcześniej ustanowił połączenie gniazda z hostem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1006">Jeśli aplikacja używa kodowania fragmentarycznego transferu do wysyłania pakietu danych żądania, musi wywołać tę usługę po wywołaniu *nx_web_http_client_request_packet_allocate*() i przed wywołaniem *nx_web_http_client_reqeust_packet_send* ().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1007">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1007">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1008">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1009">**chunk_size** Rozmiar fragmentu danych w oktetach.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="a9ad4-1010">**packet_ptr** Wskaźnik pakietów danych żądania HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1011">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1011">Return Values</span></span>

- <span data-ttu-id="a9ad4-1012">**NX_SUCCESS** (0X00) pomyślnie ustawił fragment.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="a9ad4-1013">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1014">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1014">Allowed From</span></span>

<span data-ttu-id="a9ad4-1015">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1016">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT, "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="a9ad4-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="a9ad4-1018">Dodawanie niestandardowego nagłówka do niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1019">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1020">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1020">Description</span></span>

<span data-ttu-id="a9ad4-1021">Ta usługa dodaje niestandardowy nagłówek (w postaci nazwy pola i wartości) do niestandardowego żądania HTTP utworzonego przy użyciu n *x_web_http_client_request_initialize ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="a9ad4-1022">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby niestandardowych nagłówków do żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="a9ad4-1023">**Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1024">\*Metody _start nx_web_http_client_ są udostępniane dla wygody.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a9ad4-1025">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_initialize ())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1026">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1026">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1027">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1028">**field_name** Ciąg nazwy pola (np. "Content-Type").</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="a9ad4-1029">**name_length** Długość ciągu nazwy pola w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="a9ad4-1030">**field_value** Ciąg wartości pola (np. "application/octet-stream").</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="a9ad4-1031">**value_length** Długość ciągu wartości w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="a9ad4-1032">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1033">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1034">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1035">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1036">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1036">Return Values</span></span>

- <span data-ttu-id="a9ad4-1037">**NX_SUCCESS** (0X00) pomyślnie dodawania nagłówka do żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="a9ad4-1038">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1039">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1039">Allowed From</span></span>

<span data-ttu-id="a9ad4-1040">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1041">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="a9ad4-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="a9ad4-1043">Inicjowanie niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1044">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1045">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1045">Description</span></span>

<span data-ttu-id="a9ad4-1046">Ta usługa tworzy niestandardowe żądanie HTTP i kojarzy je z wystąpieniem klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-1047">W przeciwieństwie do prostszej *nx_web_http_client_get_start ()* (wraz z METODAmi umieszczania, post i skojarzonych bezpiecznych wersji tego interfejsu API) żądanie niestandardowe nie jest wysyłane do momentu wywołania usługi *nx_web_http_client_request_send ()* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="a9ad4-1048">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu usługi ***nx_web_http_client_request_header_add ()*** .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="a9ad4-1049">Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1050">\*Metody _start nx_web_http_client_ są udostępniane dla wygody.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a9ad4-1051">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_send ())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="a9ad4-1052">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1052">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-1053">Deweloperzy są zachęcani do korzystania z *nx_web_http_client_request_initialize_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1054">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1054">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1055">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1056">**Metoda** Metoda żądania HTTP, która ma zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="a9ad4-1057">Opcje są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="a9ad4-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="a9ad4-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="a9ad4-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="a9ad4-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="a9ad4-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="a9ad4-1064">**zasób** Nazwa przesyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="a9ad4-1065">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-1066">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-1067">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-1068">**input_size** Rozmiar danych wejściowych dla operacji PUT i POST.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="a9ad4-1069">Przekazanie wartości 0 dla innych operacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="a9ad4-1070">**transfer_encoding_trunked** Parametr zastrzeżony dla przyszłej obsługi transferu z przekazywaniem.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="a9ad4-1071">**Nazwa użytkownika** Nazwa użytkownika chronionych zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="a9ad4-1072">**hasło** Hasło do chronionych zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="a9ad4-1073">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1074">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1075">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1076">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1077">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1077">Return Values</span></span>

- <span data-ttu-id="a9ad4-1078">**NX_SUCCESS** (0X00) pomyślnie zainicjowano żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="a9ad4-1079">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) brakuje niektórych wymaganych informacji (np. input_size do PUT lub POST).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1081">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1081">Allowed From</span></span>

<span data-ttu-id="a9ad4-1082">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1083">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1083">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="a9ad4-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="a9ad4-1085">Inicjowanie niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1086">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1087">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1087">Description</span></span>

<span data-ttu-id="a9ad4-1088">Ta usługa tworzy niestandardowe żądanie HTTP i kojarzy je z wystąpieniem klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="a9ad4-1089">W przeciwieństwie do prostszej *nx_web_http_client_get_start ()* (wraz z METODAmi umieszczania, post i skojarzonych bezpiecznych wersji tego interfejsu API) żądanie niestandardowe nie jest wysyłane do momentu wywołania usługi *nx_web_http_client_request_send ()* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="a9ad4-1090">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu usługi ***nx_web_http_client_request_header_add ()*** .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="a9ad4-1091">Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1092">\*Metody _start nx_web_http_client_ są udostępniane dla wygody.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a9ad4-1093">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_send ())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="a9ad4-1094">Ciągi zasobów, hosta, nazwy użytkownika i hasła muszą być zakończone znakiem NULL, a długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-1095">Ta usługa zastępuje *nx_web_http_client_request_initialize*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="a9ad4-1096">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1097">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1097">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1098">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1099">**Metoda** Metoda żądania HTTP, która ma zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="a9ad4-1100">Opcje są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="a9ad4-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="a9ad4-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="a9ad4-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="a9ad4-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="a9ad4-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="a9ad4-1107">**zasób** Nazwa przesyłanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="a9ad4-1108">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a9ad4-1109">**host** Ciąg zakończony znakiem null nazwy domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a9ad4-1110">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a9ad4-1111">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a9ad4-1112">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="a9ad4-1113">**input_size** Rozmiar danych wejściowych dla operacji PUT i POST.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="a9ad4-1114">Przekazanie wartości 0 dla innych operacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="a9ad4-1115">**transfer_encoding_trunked** Parametr zastrzeżony dla przyszłej obsługi transferu z przekazywaniem.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="a9ad4-1116">**Nazwa użytkownika** Wskaźnik na opcjonalną nazwę użytkownika na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-1117">**username_length** Długość ciągu nazwy użytkownika do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a9ad4-1118">**hasło** Wskaźnik na opcjonalne hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a9ad4-1119">**password_length** Długość ciągu hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a9ad4-1120">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1121">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1122">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1123">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1124">Return Values</span></span>

- <span data-ttu-id="a9ad4-1125">**NX_SUCCESS** (0X00) pomyślnie zainicjowano żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="a9ad4-1126">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) brakuje niektórych wymaganych informacji (np. input_size do PUT lub POST).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1128">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1128">Allowed From</span></span>

<span data-ttu-id="a9ad4-1129">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1130">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1130">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="a9ad4-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="a9ad4-1132">Wyślij pakiet danych żądania HTTP (S) do serwera zdalnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1133">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1134">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1134">Description</span></span>

<span data-ttu-id="a9ad4-1135">Ta usługa wysyła niestandardowy pakiet danych żądania HTTP (S) utworzony za pomocą *nx_web_http_client_request_packet_allocate* () na serwer określony w wywołaniu *nx_web_http_client_connect ()* lub *nx_web_http_client_secure_connect (*), który wcześniej ustanowił połączenie gniazda z hostem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1136">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1136">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1137">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1138">**packet_ptr** Wskaźnik pakietów danych żądania HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="a9ad4-1139">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1140">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1141">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1142">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1143">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1143">Return Values</span></span>

- <span data-ttu-id="a9ad4-1144">**NX_SUCCESS** (0X00) pomyślne wysłanie pakietu danych żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="a9ad4-1145">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1146">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1146">Allowed From</span></span>

<span data-ttu-id="a9ad4-1147">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1148">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="a9ad4-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="a9ad4-1150">Wyślij niestandardowe żądanie HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1151">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1152">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1152">Description</span></span>

<span data-ttu-id="a9ad4-1153">Ta usługa wysyła niestandardowe żądanie HTTP utworzone za pomocą *nx_web_http_client_request_initialize ()* na serwer określony w *nx_web_http_client_connect ()* lub *nx_web_http_client_secure_connect ()* , z których wcześniej nawiązano połączenie gniazda z hostem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="a9ad4-1154">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu usługi ***nx_web_http_client_request_header_add ()*** .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="a9ad4-1155">Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1156">\*Metody _start nx_web_http_client_ są udostępniane dla wygody.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a9ad4-1157">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_initialize ())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1158">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1158">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1159">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1160">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1161">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1162">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1163">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1164">Return Values</span></span>

- <span data-ttu-id="a9ad4-1165">**NX_SUCCESS** (0X00) pomyślne wysłanie żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="a9ad4-1166">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1167">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1167">Allowed From</span></span>

<span data-ttu-id="a9ad4-1168">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1169">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="a9ad4-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="a9ad4-1171">Pobierz następny pakiet danych zasobów</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1172">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1173">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1173">Description</span></span>

<span data-ttu-id="a9ad4-1174">Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie wywołanie *nx_web_http_client_get_start ()* lub *nx_web_http_client_get_secure_start ()* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="a9ad4-1175">Kolejne wywołania tej procedury należy wprowadzać do momentu otrzymania stanu powrotu NX_WEB_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1176">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1176">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1177">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1178">**packet_ptr** Miejsce docelowe dla wskaźnika pakietu zawierającego częściową zawartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="a9ad4-1179">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1180">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1181">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1182">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1183">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1183">Return Values</span></span>

- <span data-ttu-id="a9ad4-1184">**NX_SUCCESS** (0X00) pomyślne pobieranie pakietu klienta http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="a9ad4-1185">**NX_WEB_HTTP_GET_DONE** (0X3000C) http Get pakiet klienta jest gotowy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="a9ad4-1186">Klient HTTP **NX_WEB_HTTP_NOT_READY** (0x3000A) nie jest w trybie pobierania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="a9ad4-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="a9ad4-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) kod stanu HTTP 100 Kontynuuj</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="a9ad4-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) kod stanu HTTP 101 Przełączanie protokołów</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="a9ad4-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) kod stanu HTTP 201 został utworzony</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="a9ad4-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) kod stanu HTTP 202 zaakceptowany</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="a9ad4-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) kod stanu HTTP 203 informacje nieautorytatywne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="a9ad4-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) kod stanu HTTP 204 Brak zawartości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="a9ad4-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) kod stanu HTTP 205 Resetowanie zawartości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="a9ad4-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) kod stanu HTTP 206 częściowa zawartość</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="a9ad4-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) kod stanu HTTP 300 z wieloma opcjami</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="a9ad4-1197">Kod stanu HTTP **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) 301 został trwale przeniesiony</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="a9ad4-1198">Znaleziono kod stanu HTTP **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) 302</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="a9ad4-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) kod stanu HTTP 303 Zobacz inne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="a9ad4-1200">Kod stanu HTTP **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) 304 nie został zmodyfikowany</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="a9ad4-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) kod stanu HTTP 305 Użyj serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="a9ad4-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0X30028) http kod stanu 307 tymczasowe przekierowanie</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="a9ad4-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) kod stanu HTTP 400 Nieprawidłowe żądanie</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="a9ad4-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) kod stanu HTTP 401 nieautoryzowany</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="a9ad4-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) kod stanu HTTP 402 wymagana opłata</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="a9ad4-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) kod stanu HTTP 403 zabroniony</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="a9ad4-1207">Nie znaleziono kodu stanu HTTP **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) 404</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="a9ad4-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) kod stanu HTTP 405 Metoda niedozwolona</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="a9ad4-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) kod stanu HTTP 406 nie jest akceptowalny</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="a9ad4-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) kod stanu HTTP 407 wymagane uwierzytelnianie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="a9ad4-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) kod stanu HTTP 408 upłynął limit czasu żądania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="a9ad4-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) kod stanu HTTP 409 konflikt</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="a9ad4-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) kod stanu HTTP 410 został usunięty</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="a9ad4-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) kod stanu HTTP 411 wymagana długość</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="a9ad4-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) kod stanu HTTP 412 niepowodzenie warunku wstępnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="a9ad4-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) kod stanu HTTP 413 jednostka żądania jest zbyt duża</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="a9ad4-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) kod stanu HTTP 414 adres URL żądania jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="a9ad4-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) kod stanu HTTP 415 nieobsługiwany typ nośnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="a9ad4-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) kod stanu HTTP 416 żądany zakres nie niewłaściwego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="a9ad4-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) kod stanu HTTP 417 nie powiodło się</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="a9ad4-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) kod stanu HTTP 500 wewnętrzny błąd serwera</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="a9ad4-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) kod stanu HTTP 501 nie został zaimplementowany</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="a9ad4-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) kod stanu HTTP 502 zła Brama</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="a9ad4-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) kod stanu HTTP 503 Usługa niedostępna</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="a9ad4-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) kod stanu HTTP 504 upłynął limit czasu bramy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="a9ad4-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) kod stanu HTTP 505 wersja http nieobsługiwana</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="a9ad4-1227">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1228">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1229">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1229">Allowed From</span></span>

<span data-ttu-id="a9ad4-1230">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1231">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="a9ad4-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="a9ad4-1233">Ustawianie wywołania zwrotnego do wywołania podczas przetwarzania nagłówków HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1234">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="a9ad4-1235">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1235">Description</span></span>

<span data-ttu-id="a9ad4-1236">Ta usługa przypisuje wywołanie zwrotne, które zostanie wywołane za każdym razem, gdy klient HTTP NetX sieci Web przetwarza nagłówek HTTP w odpowiedzi przychodzącej ze zdalnego serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="a9ad4-1237">Wywołanie zwrotne jest wywoływane jednokrotnie dla każdego nagłówka w odpowiedzi w miarę ich przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="a9ad4-1238">Wywołanie zwrotne umożliwia aplikacji klienckiej HTTP uzyskanie dostępu do każdego z nagłówków odpowiedzi serwera HTTP w celu podjęcia wszelkich żądanych akcji poza podstawowym przetwarzaniem, które NetX klienta HTTP sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1239">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1239">Input Parameters</span></span>

<span data-ttu-id="a9ad4-1240">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="a9ad4-1241">**callback_function** Wywołanie zwrotne zostało wywołane podczas przetwarzania nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="a9ad4-1242">Wywołanie zwrotne jest wywoływane z nazwą pola i wartością jako ciągi (i ich długości).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="a9ad4-1243">Na przykład nagłówek "Content-Length: 100" spowoduje, że funkcja zostanie wywołana z "Content-Length" dla *field_name* i ciągu "100" dla *field_value*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1244">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1244">Return Values</span></span>

- <span data-ttu-id="a9ad4-1245">**NX_SUCCESS** (0x00) — pomyślne przypisanie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="a9ad4-1246">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1247">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1247">Allowed From</span></span>

<span data-ttu-id="a9ad4-1248">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1249">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1249">Example</span></span>

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="a9ad4-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="a9ad4-1251">Otwieranie sesji protokołu TLS na serwerze HTTPS dla żądań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1252">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1253">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1253">Description</span></span>

<span data-ttu-id="a9ad4-1254">Ta metoda dotyczy protokołu HTTPS **zabezpieczonego** protokołem TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a9ad4-1255">Ta usługa otwiera zabezpieczoną sesję protokołu TLS z serwerem HTTPS, ale nie wysyła żadnych żądań.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="a9ad4-1256">Żądania są tworzone za pomocą n *x_web_http_client_request_initialize ()* i wysyłane przy użyciu *nx_web_http_client_request_send ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="a9ad4-1257">Niestandardowe nagłówki HTTP można dodać do żądania przy użyciu *nx_web_http_client_request_header_add ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="a9ad4-1258">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby niestandardowych nagłówków do żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="a9ad4-1259">**Pozwala to na niestandardowe żądania HTTP przeznaczone dla określonych aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1260">\*Metody _start nx_web_http_client_ są udostępniane dla wygody.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a9ad4-1261">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz z *nx_web_http_client_request_initialize ())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1262">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1262">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1263">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1264">**server_IP** Adres IP zdalnego serwera HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="a9ad4-1265">**SERVER_PORT** Port na zdalnym serwerze HTTPS (np. 443 dla protokołu HTTPS).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="a9ad4-1266">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a9ad4-1267">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii TLS i poświadczeń (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a9ad4-1268">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na żądanie uruchomienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a9ad4-1269">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1270">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a9ad4-1271">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1272">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1272">Return Values</span></span>

- <span data-ttu-id="a9ad4-1273">**NX_SUCCESS** (0x00) powiodło się połączenie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="a9ad4-1274">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1275">NX_WEB_HTTP_NOT_READY (0x3000A) inne żądanie jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1276">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1276">Allowed From</span></span>

<span data-ttu-id="a9ad4-1277">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1278">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1278">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="a9ad4-1279">Interfejs API serwera HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="a9ad4-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="a9ad4-1281">Ustawianie wywołania zwrotnego do pobierania adresu URL maksymalny wiek i Data</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1282">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="a9ad4-1283">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1283">Description</span></span>

<span data-ttu-id="a9ad4-1284">Ta usługa ustawia wywołana usługa wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1285">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1285">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1286">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1287">**cache_info_get** Wskaźnik do wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="a9ad4-1288">**max_age** Wskaźnik do maksymalnego wieku zasobu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="a9ad4-1289">**dane** Zwrócono wskaźnik do daty ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1290">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1290">Return Values</span></span>

- <span data-ttu-id="a9ad4-1291">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a9ad4-1292">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1293">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1293">Allowed From</span></span>

<span data-ttu-id="a9ad4-1294">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1295">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="a9ad4-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="a9ad4-1297">Wyślij dane z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1298">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1299">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1299">Description</span></span>

<span data-ttu-id="a9ad4-1300">Ta usługa wysyła dane z dostarczonego pakietu z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="a9ad4-1301">Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="a9ad4-1302">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="a9ad4-1303">Ponadto procedura wywołania zwrotnego musi zwracać stan NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1304">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1304">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1305">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1306">**data_ptr** Wskaźnik do danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="a9ad4-1307">**data_length** Liczba bajtów do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1308">Return Values</span></span>

- <span data-ttu-id="a9ad4-1309">**NX_SUCCESS** (0X00) pomyślnie przesłał dane serwera</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="a9ad4-1310">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1311">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1311">Allowed From</span></span>

<span data-ttu-id="a9ad4-1312">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1313">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1313">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="a9ad4-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="a9ad4-1315">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1316">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1317">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1317">Description</span></span>

<span data-ttu-id="a9ad4-1318">Ta usługa jest używana w procedurze wywołania zwrotnego serwera HTTP (S) (zdefiniowanej przez aplikację) w celu wygenerowania nagłówka odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="a9ad4-1319">Procedura wywołania zwrotnego serwera jest wywoływana, gdy serwer HTTP odpowiada na żądania GET, PUT i DELETE klienta wymagające odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="a9ad4-1320">Ta funkcja pobiera informacje o odpowiedzi z aplikacji i generuje odpowiedni nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="a9ad4-1321">Zobacz nx_web_http_server_create usługi *()* , aby uzyskać więcej informacji na temat procedury wywołania zwrotnego żądania serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="a9ad4-1322">Ten interfejs API jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1322">This API is deprecated.</span></span> <span data-ttu-id="a9ad4-1323">Deweloperzy są zachęcani do korzystania z *nx_web_http_server_callback_generate_response_header_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1324">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1324">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1325">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1326">**packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="a9ad4-1327">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="a9ad4-1328">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1328">Examples:</span></span>
  - <span data-ttu-id="a9ad4-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="a9ad4-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="a9ad4-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="a9ad4-1332">**CONTENT_LENGTH** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="a9ad4-1333">**Content_Type** Typ HTTP np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="a9ad4-1334">**additional_header** Wskaźnik na dodatkowy tekst nagłówka</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1335">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1335">Return Values</span></span>

- <span data-ttu-id="a9ad4-1336">**NX_SUCCESS** (0X00) pomyślnie UTWORZYŁ nagłówek HTML</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="a9ad4-1337">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1338">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1338">Allowed From</span></span>

<span data-ttu-id="a9ad4-1339">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1340">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1340">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="a9ad4-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="a9ad4-1342">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1343">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1343">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1344">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1344">Description</span></span>

<span data-ttu-id="a9ad4-1345">Ta usługa jest używana w procedurze wywołania zwrotnego serwera HTTP (S) (zdefiniowanej przez aplikację) w celu wygenerowania nagłówka odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="a9ad4-1346">Procedura wywołania zwrotnego serwera jest wywoływana, gdy serwer HTTP odpowiada na żądania GET, PUT i DELETE klienta wymagające odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="a9ad4-1347">Ta funkcja pobiera informacje o odpowiedzi z aplikacji i generuje odpowiedni nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="a9ad4-1348">Zobacz nx_web_http_server_create usługi *()* , aby uzyskać więcej informacji na temat procedury wywołania zwrotnego żądania serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1349">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1349">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1350">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1351">**packet_pptr** Wskaźnik do wskaźnika pakietu przydzieloną dla wiadomości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="a9ad4-1352">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="a9ad4-1353">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1353">Examples:</span></span>
  - <span data-ttu-id="a9ad4-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="a9ad4-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="a9ad4-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="a9ad4-1357">**status_code_length** Długość ciągu kodu stanu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="a9ad4-1358">**CONTENT_LENGTH** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="a9ad4-1359">**Content_Type** Typ HTTP np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="a9ad4-1360">**content_type_length** Długość ciągu typu zawartości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="a9ad4-1361">**additional_header** Wskaźnik na dodatkowy tekst nagłówka</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="a9ad4-1362">**additional_header_length** Długość dodatkowego tekstu nagłówka</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1363">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1363">Return Values</span></span>

- <span data-ttu-id="a9ad4-1364">**NX_SUCCESS** (0X00) pomyślnie UTWORZYŁ nagłówek HTML</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="a9ad4-1365">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1366">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1366">Allowed From</span></span>

<span data-ttu-id="a9ad4-1367">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1368">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1368">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="a9ad4-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="a9ad4-1370">Wyślij pakiet HTTP z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1371">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1372">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1372">Description</span></span>

<span data-ttu-id="a9ad4-1373">Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="a9ad4-1374">Serwer HTTP wyśle pakiet za pomocą _TIMEOUT_SEND NX_WEB_HTTP_SERVER.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="a9ad4-1375">Nagłówek HTTP i dane muszą być dołączone do pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="a9ad4-1376">Jeśli stan powrotu wskazuje na błąd, aplikacja HTTP musi zwolnić pakiet.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="a9ad4-1377">Wywołanie zwrotne powinno zwracać NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a9ad4-1378">Zobacz *nx_web_http_server_callback_generate_response_header ()* , aby zapoznać się z bardziej szczegółowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1379">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1379">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1380">**server_ptr** Wskaźnik do bloku kontroli serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="a9ad4-1381">**packet_ptr** Wskaźnik do pakietu do wysłania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1382">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1382">Return Values</span></span>

- <span data-ttu-id="a9ad4-1383">**NX_SUCCESS** (0X00) pomyślnie wysłał pakiet serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="a9ad4-1384">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1385">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1385">Allowed From</span></span>

<span data-ttu-id="a9ad4-1386">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1387">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1387">Example</span></span>

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="a9ad4-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="a9ad4-1389">Wyślij odpowiedź z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1390">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1391">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1391">Description</span></span>

<span data-ttu-id="a9ad4-1392">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="a9ad4-1393">Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="a9ad4-1394">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a9ad4-1395">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1395">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-1396">Deweloperzy są zachęcani do korzystania z *nx_web_http_server_callback_response_send_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1397">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1397">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1398">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1399">**nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="a9ad4-1400">**informacje** Wskaźnik na ciąg informacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="a9ad4-1401">**additional_info** Wskaźnik na ciąg informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1402">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1402">Return Values</span></span>

- <span data-ttu-id="a9ad4-1403">**NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1404">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1404">Allowed From</span></span>

<span data-ttu-id="a9ad4-1405">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1406">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1406">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="a9ad4-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="a9ad4-1408">Wyślij odpowiedź z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1409">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1410">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1410">Description</span></span>

<span data-ttu-id="a9ad4-1411">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="a9ad4-1412">Jest to zwykle używane do wysyłania niestandardowych odpowiedzi skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="a9ad4-1413">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwrócić stan NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a9ad4-1414">Ciągi nagłówka, informacje i additional_info muszą być zakończone znakiem NULL i długość każdego ciągu jest zgodna z długością określoną na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a9ad4-1415">Ta usługa zastępuje *nx_web_http_server_callback_response_send*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="a9ad4-1416">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1417">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1417">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1418">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1419">**nagłówek** Wskaźnik na ciąg nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="a9ad4-1420">**header_length** Długość ciągu nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="a9ad4-1421">**informacje** Wskaźnik na ciąg informacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="a9ad4-1422">**Information_length** Długość ciągu informacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="a9ad4-1423">**additional_info** Wskaźnik na ciąg informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="a9ad4-1424">**additional_info_length** Długość ciągu informacji dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1425">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1425">Return Values</span></span>

- <span data-ttu-id="a9ad4-1426">**NX_SUCCESS** (0X00) pomyślnie przesłał odpowiedź serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1427">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1427">Allowed From</span></span>

<span data-ttu-id="a9ad4-1428">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1429">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1429">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="a9ad4-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="a9ad4-1431">Pobierz zawartość z żądania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1432">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1433">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1433">Description</span></span>

<span data-ttu-id="a9ad4-1434">Ta usługa próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="a9ad4-1435">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1436">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1436">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1437">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1438">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a9ad4-1439">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a9ad4-1440">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="a9ad4-1441">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="a9ad4-1442">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="a9ad4-1443">**actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1444">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1444">Return Values</span></span>

- <span data-ttu-id="a9ad4-1445">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="a9ad4-1446">Błąd wewnętrzny serwera HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="a9ad4-1447">0x30007 — koniec zawartości żądania **NX_WEB_HTTP_DATA_END**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="a9ad4-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu zawartości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="a9ad4-1449">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1450">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1451">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1451">Allowed From</span></span>

<span data-ttu-id="a9ad4-1452">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1453">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="a9ad4-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="a9ad4-1455">Pobierz zawartość z żądania/obsługuje długość zawartości o zerowej długości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1456">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1457">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1457">Description</span></span>

<span data-ttu-id="a9ad4-1458">Ta usługa jest niemal identyczna z *nx_web_http_server_content_get ()*; próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="a9ad4-1459">Jednak obsługuje żądania o długości wartości zerowej (puste żądanie) jako prawidłowe żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="a9ad4-1460">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="a9ad4-1461">Ta usługa zastępuje *nx_web_http_server_content_get*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="a9ad4-1462">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1463">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1463">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1464">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1465">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a9ad4-1466">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a9ad4-1467">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="a9ad4-1468">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="a9ad4-1469">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="a9ad4-1470">**actual_size** Wskaźnik do zmiennej docelowej, który zostanie ustawiony na rzeczywisty rozmiar skopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1471">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1471">Return Values</span></span>

- <span data-ttu-id="a9ad4-1472">**NX_SUCCESS** (0X00) pomyślne pobieranie zawartości http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="a9ad4-1473">Błąd wewnętrzny serwera HTTP **NX_WEB_HTTP_ERROR** (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="a9ad4-1474">0x30007 — koniec zawartości żądania **NX_WEB_HTTP_DATA_END**</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="a9ad4-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) przekroczenie limitu czasu serwera http podczas pobierania następnego pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="a9ad4-1476">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1477">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1478">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1478">Allowed From</span></span>

<span data-ttu-id="a9ad4-1479">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1480">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="a9ad4-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="a9ad4-1482">Pobierz długość zawartości w żądaniu/obsługuje długość zawartości równą zero</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1483">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1484">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1484">Description</span></span>

<span data-ttu-id="a9ad4-1485">Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="a9ad4-1486">Wartość zwracana wskazuje stan pomyślnego ukończenia i rzeczywista wartość długości jest zwracana w wskaźniku wejściowym content_length.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="a9ad4-1487">Jeśli nie ma żadnej zawartości HTTP o długości zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wskaźnik wejściowy wskazuje prawidłową długość (zero).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="a9ad4-1488">Powinien być wywoływany z wywołania zwrotnego powiadomienia żądania aplikacji określonego podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1489">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1489">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1490">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a9ad4-1491">Należy pamiętać, że ten pakiet nie może zostać wydzierżawiony przez wywołanie zwrotne powiadomienia o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a9ad4-1492">**CONTENT_LENGTH** Wskaźnik do wartości pobranej z pola długości zawartości</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1493">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1493">Return Values</span></span>

- <span data-ttu-id="a9ad4-1494">**NX_SUCCESS** (0X00) pomyślne pobieranie długości zawartości serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="a9ad4-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) niewłaściwy format nagłówka http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="a9ad4-1496">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1497">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1497">Allowed From</span></span>

<span data-ttu-id="a9ad4-1498">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1499">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="a9ad4-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="a9ad4-1501">Tworzenie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1502">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1502">Prototype</span></span>

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="a9ad4-1503">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1503">Description</span></span>

<span data-ttu-id="a9ad4-1504">Ta usługa tworzy wystąpienie serwera HTTP, które działa w kontekście jego własnego wątku ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="a9ad4-1505">Opcjonalne *authentication_check* i *request_notify* procedury wywołania zwrotnego aplikacji umożliwiają kontrolę oprogramowania aplikacji przez podstawowe operacje serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="a9ad4-1506">Ta usługa służy do tworzenia zarówno serwerów HTTP ze zwykłym tekstem, jak i serwerów HTTPS zabezpieczonych za pomocą protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="a9ad4-1507">Aby włączyć protokół HTTPS przy użyciu protokołu TLS, zobacz *nx_web_http_server_secure_configure usługi ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1508">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1508">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1509">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1510">**http_server_name** Wskaźnik na nazwę serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="a9ad4-1511">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9ad4-1512">**SERVER_PORT** Port nasłuchiwania protokołu TCP dla wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="a9ad4-1513">**media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="a9ad4-1514">**stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="a9ad4-1515">**stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="a9ad4-1516">**authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="a9ad4-1517">Jeśli jest określony, ta procedura jest wywoływana dla każdego żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="a9ad4-1518">Jeśli ten parametr ma wartość NULL, uwierzytelnianie nie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="a9ad4-1519">Ten parametr jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1519">This parameter is deprecated.</span></span> <span data-ttu-id="a9ad4-1520">Wywołaj *nx_web_http_server_authenticate_check_set*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="a9ad4-1521">**request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="a9ad4-1522">Jeśli jest określony, ta procedura jest wywoływana przed przetworzeniem żądania przez serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="a9ad4-1523">Pozwala to na aktualizowanie nazwy zasobu lub pól w ramach zasobu przed ukończeniem żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1524">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1524">Return Values</span></span>

- <span data-ttu-id="a9ad4-1525">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="a9ad4-1526">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="a9ad4-1527">Ładunek pakietu NX_WEB_HTTP_POOL_ERROR (0x30009) puli nie jest wystarczająco duży, aby można było zawierać pełne żądanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1528">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1528">Allowed From</span></span>

<span data-ttu-id="a9ad4-1529">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1530">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="a9ad4-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="a9ad4-1532">Usuwanie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1533">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1534">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1534">Description</span></span>

<span data-ttu-id="a9ad4-1535">Ta usługa usuwa poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1536">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1536">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1537">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1538">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1538">Return Values</span></span>

- <span data-ttu-id="a9ad4-1539">**NX_SUCCESS** (0X00) pomyślne usunięcie serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="a9ad4-1540">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="a9ad4-1541">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1542">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1542">Allowed From</span></span>

<span data-ttu-id="a9ad4-1543">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1544">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="a9ad4-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="a9ad4-1546">Pobierz lokalizację i długość danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1547">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1548">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1548">Description</span></span>

<span data-ttu-id="a9ad4-1549">Ta usługa określa lokalizację początkową danych w bieżącej jednostce wieloczęściowej w odebranych komunikatach klienta i długość danych bez uwzględniania ciągu granicy.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="a9ad4-1550">Wewnętrznie serwer HTTP aktualizuje własne przesunięcia, aby można było ponownie wywołać tę funkcję na tym samym datagramie klienta dla komunikatów z wieloma jednostkami.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="a9ad4-1551">Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="a9ad4-1552">Należy pamiętać, że NX_WEB_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="a9ad4-1553">Należy również zauważyć, że aplikacja nie powinna zwolnić pakietu wskazywanego przez packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="a9ad4-1554">Jest to wykonywane wewnętrznie przez serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="a9ad4-1555">Aby uzyskać więcej informacji, zobacz *nx_web_http_server_get_entity_header ()* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1556">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1556">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1557">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a9ad4-1558">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="a9ad4-1559">Zwróć uwagę, że aplikacja nie powinna wydać tego pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="a9ad4-1560">**available_offset** Wskaźnik do przesunięcia danych jednostki ze wskaźnika dołączania do pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="a9ad4-1561">**available_length** Wskaźnik do długości danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1562">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1562">Return Values</span></span>

- <span data-ttu-id="a9ad4-1563">**NX_SUCCESS** (0X00) pomyślnie pobrała rozmiar i lokalizację zawartości jednostki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="a9ad4-1564">Zawartość **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) dla wewnętrznych znaczników wieloczęściowych serwera http została już znaleziona</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="a9ad4-1565">Błąd wewnętrzny serwera HTTP NX_WEB_HTTP_ERROR (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="a9ad4-1566">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1567">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1567">Allowed From</span></span>

<span data-ttu-id="a9ad4-1568">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1569">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1569">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="a9ad4-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="a9ad4-1571">Pobierz zawartość nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1572">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1573">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1573">Description</span></span>

<span data-ttu-id="a9ad4-1574">Ta usługa pobiera nagłówek jednostki do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="a9ad4-1575">Serwer HTTP wewnętrznie aktualizuje własne wskaźniki, aby znaleźć następną wieloczęściową jednostkę w datagramie klienta z wieloma nagłówkami jednostek.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="a9ad4-1576">Wskaźnik pakietu zostanie zaktualizowany do następnego pakietu, w którym komunikat klienta jest datagramem zawierającym wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="a9ad4-1577">Należy pamiętać, że NX_WEB_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="a9ad4-1578">Należy również pamiętać, że aplikacja nie powinna zwolnić pakietu wskazywanego przez packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1579">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1579">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1580">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a9ad4-1581">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="a9ad4-1582">Zwróć uwagę, że aplikacja nie powinna wydać tego pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="a9ad4-1583">**entity_header_buffer** Wskaźnik do lokalizacji do zapisania nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="a9ad4-1584">**buffer_size** Rozmiar buforu wejściowego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1585">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1585">Return Values</span></span>

- <span data-ttu-id="a9ad4-1586">**NX_SUCCESS** (0X00) pomyślnie pobrał nagłówek jednostki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="a9ad4-1587">Nie znaleziono pola nagłówka jednostki **NX_WEB_HTTP_NOT_FOUND** (0x30006)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="a9ad4-1588">Czas **NX_WEB_HTTP_TIMEOUT** (0x30001), który utracił ważność następnego pakietu dla komunikatu klienta wielopakietowego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="a9ad4-1589">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1590">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="a9ad4-1591">Wewnętrzny błąd HTTP NX_WEB_HTTP_ERROR (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1592">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1592">Allowed From</span></span>

<span data-ttu-id="a9ad4-1593">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1594">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1594">Example</span></span>

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="a9ad4-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="a9ad4-1596">Ustaw wywołanie zwrotne, aby uzyskać datę i godzinę GMT</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1597">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1598">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1598">Description</span></span>

<span data-ttu-id="a9ad4-1599">Ta usługa ustawia wywołanie zwrotne, aby uzyskać datę i godzinę GMT z wcześniej utworzonym serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="a9ad4-1600">Ta usługa jest wywoływana z serwerem HTTP tworzy nagłówek w odpowiedziach serwera HTTP dla klienta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1601">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1601">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1602">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a9ad4-1603">**gmt_get** Wskaźnik do wywołania zwrotnego GMT</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="a9ad4-1604">**Data** Wskaźnik do pobranej daty</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1605">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1605">Return Values</span></span>

- <span data-ttu-id="a9ad4-1606">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a9ad4-1607">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1608">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1608">Allowed From</span></span>

<span data-ttu-id="a9ad4-1609">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1610">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1610">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="a9ad4-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="a9ad4-1612">Ustawianie wywołania zwrotnego do obsługi nieprawidłowego użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1613">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="a9ad4-1614">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1614">Description</span></span>

<span data-ttu-id="a9ad4-1615">Ta usługa ustawia wywołanie zwrotne wywoływane po odebraniu nieprawidłowej nazwy użytkownika i hasła do żądania GET, Put lub DELETE klienta w ramach uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="a9ad4-1616">Należy wcześniej utworzyć serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1617">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1617">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1618">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a9ad4-1619">**invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/przekazania wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="a9ad4-1620">**zasób** Wskaźnik do zasobu określonego przez klienta</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="a9ad4-1621">**client_address** Adres klienta</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1621">**client_address** Client address</span></span>
- <span data-ttu-id="a9ad4-1622">**request_type** Wskazuje typ żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="a9ad4-1623">Może:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1623">May be:</span></span>
  - <span data-ttu-id="a9ad4-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="a9ad4-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="a9ad4-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1627">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1627">Return Values</span></span>

- <span data-ttu-id="a9ad4-1628">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a9ad4-1629">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1630">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1630">Allowed From</span></span>

<span data-ttu-id="a9ad4-1631">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1632">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1632">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="a9ad4-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="a9ad4-1634">Ustaw dodatkowe mapy MIME dla HTML</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1635">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1636">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1636">Description</span></span>

<span data-ttu-id="a9ad4-1637">Ta usługa umożliwia deweloperowi aplikacji protokołu HTTP Dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczonych przez serwer HTTP sieci Web NetX.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="a9ad4-1638">Zobacz *nx_web_http_server_get_type ()* , aby zapoznać się z listą zdefiniowanych typów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="a9ad4-1639">Po odebraniu żądania klienta, np. żądanie GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu preferencyjnego dodatkowego zestawu mapowań MIME i jeśli nie jest zgodny, szuka dopasowania w domyślnej mapie MIME serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="a9ad4-1640">Jeśli nie zostanie znalezione dopasowanie, typ MIME domyślnie przyjmuje wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="a9ad4-1641">Jeśli funkcja powiadamiania o żądaniu jest zarejestrowana na serwerze HTTP, wywołanie zwrotne powiadomienia o żądaniu może wywołać *nx_web_http_server_type_get_extended ()* w celu przeanalizowania typu pliku.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1642">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1642">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1643">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a9ad4-1644">**mime_maps** Wskaźnik do tablicy mapy MIME</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="a9ad4-1645">**mime_map_num** Liczba mapowań MIME w tablicy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1646">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1646">Return Values</span></span>

- <span data-ttu-id="a9ad4-1647">**NX_SUCCESS** (0X00) pomyślne Ustawianie mapy MIME serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="a9ad4-1648">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1649">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1649">Allowed From</span></span>

<span data-ttu-id="a9ad4-1650">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1651">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1651">Example</span></span>

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="a9ad4-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="a9ad4-1653">Przydziel pakiet HTTP (S)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1654">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1655">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1655">Description</span></span>

<span data-ttu-id="a9ad4-1656">Ta usługa próbuje przydzielić pakiet dla serwera HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="a9ad4-1657">Należy pamiętać, że jeśli kolejny interfejs API serwera NetX lub HTTP używający tego pakietu jako danych wejściowych **nie powiedzie się**, na przykład nx_packet_data_append lub \* \* nx_web_http_server_callback_packet_send, aplikacja jest odpowiedzialna za wydanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1658">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1658">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1659">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a9ad4-1660">**packet_ptr** Wskaźnik do przydzielony pakiet.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="a9ad4-1661">**WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="a9ad4-1662">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a9ad4-1663">**NX_NO_WAIT** (0x00000000) wybranie NX_NO_WAIT powoduje natychmiastowe zwrócenie przez wątek wywołujący, jeśli nie można spełnić żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="a9ad4-1664">**NX_WAIT_FOREVER** (0Xffffffff) wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer http odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="a9ad4-1665">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę taktów czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera http.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1666">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1666">Return Values</span></span>

- <span data-ttu-id="a9ad4-1667">Pomyślne przydzielenie pakietu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="a9ad4-1668">**NX_NO_PACKET** (0X01) Brak dostępnego pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="a9ad4-1669">Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a9ad4-1670">Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a9ad4-1671">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1672">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1673">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1673">Allowed From</span></span>

<span data-ttu-id="a9ad4-1674">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1675">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="a9ad4-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="a9ad4-1677">Wyodrębnij długość zawartości i ustaw wskaźnik na początek danych</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1678">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1679">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1679">Description</span></span>

<span data-ttu-id="a9ad4-1680">Ta usługa wyodrębnia długość zawartości z nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="a9ad4-1681">Aktualizuje również podany pakiet w następujący sposób: wskaźnik dołączania pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) po prostu przekazały nagłówek HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="a9ad4-1682">Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na odebranie następnego pakietu przy użyciu opcji oczekiwania NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="a9ad4-1683">Należy zauważyć, że nie należy wywoływać przed wywołaniem *nx_web_http_server_get_entity_header ()* , ponieważ modyfikuje wskaźnik dołączania pakietu poza nagłówkiem Entity.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1684">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1684">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1685">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="a9ad4-1686">**packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym wskaźnikiem dołączania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="a9ad4-1687">**CONTENT_LENGTH** Wskaźnik do wyodrębnienia content_length</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1688">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1688">Return Values</span></span>

- <span data-ttu-id="a9ad4-1689">**NX_SUCCESS** (0x00) znaleziono długość zawartości http i pakiet został pomyślnie zaktualizowany</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="a9ad4-1690">Czas **NX_WEB_HTTP_TIMEOUT** (0x30001) upłynął podczas oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="a9ad4-1691">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1692">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1692">Allowed From</span></span>

<span data-ttu-id="a9ad4-1693">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1694">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1694">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="a9ad4-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="a9ad4-1696">Odbierz następny pakiet HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1697">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1698">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1698">Description</span></span>

<span data-ttu-id="a9ad4-1699">Ta usługa zwraca następny pakiet odebrany w gnieździe serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="a9ad4-1700">Opcja oczekiwania na odebranie pakietu jest NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="a9ad4-1701">Należy pamiętać, że jeśli aplikacja jest odpowiedzialna za wydanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1702">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1702">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1703">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="a9ad4-1704">**packet_ptr** Wskaźnik do odebranego pakietu</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1705">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1705">Return Values</span></span>

- <span data-ttu-id="a9ad4-1706">**NX_SUCCESS** (0X00) pomyślnie otrzymał następny pakiet http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="a9ad4-1707">Czas **NX_WEB_HTTP_TIMEOUT** (0x30001) upłynął podczas oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="a9ad4-1708">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1709">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1709">Allowed From</span></span>

<span data-ttu-id="a9ad4-1710">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1711">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="a9ad4-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="a9ad4-1713">Pobierz parametr z żądania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1714">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1715">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1715">Description</span></span>

<span data-ttu-id="a9ad4-1716">Ta usługa próbuje pobrać określony parametr HTTP URL w dostarczonym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="a9ad4-1717">Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="a9ad4-1718">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1719">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1719">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1720">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="a9ad4-1721">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a9ad4-1722">**param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="a9ad4-1723">**param_ptr** Obszar docelowy do skopiowania parametru.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="a9ad4-1724">**param_size** Zwróć łączną długość danych parametru (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="a9ad4-1725">**max_param_size** Maksymalny rozmiar obszaru docelowego parametru.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1726">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1726">Return Values</span></span>

- <span data-ttu-id="a9ad4-1727">**NX_SUCCESS** (0X00) pomyślne pobieranie PARAMETRU serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="a9ad4-1728">Nie znaleziono podanego parametru **NX_WEB_HTTP_NOT_FOUND** (0x30006)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="a9ad4-1729">Parametr żądania **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) nie został poprawnie zakończony</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="a9ad4-1730">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1731">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1732">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1732">Allowed From</span></span>

<span data-ttu-id="a9ad4-1733">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1734">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="a9ad4-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="a9ad4-1736">Pobierz zapytanie z żądania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1737">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1738">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1738">Description</span></span>

<span data-ttu-id="a9ad4-1739">Ta usługa próbuje pobrać określoną kwerendę HTTP URL w dostarczonym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="a9ad4-1740">Jeśli żądana kwerenda HTTP nie istnieje, ta procedura zwraca stan NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="a9ad4-1741">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia o żądaniu aplikacji określonej podczas tworzenia serwera HTTP (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1742">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1742">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1743">**packet_ptr** Wskaźnik na pakiet żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="a9ad4-1744">Należy zauważyć, że aplikacja nie powinna wydać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a9ad4-1745">**query_number** Numer logiczny parametru zaczynający się od zera od lewej do prawej na liście zapytań.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="a9ad4-1746">**query_ptr** Obszar docelowy, w którym ma zostać skopiowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="a9ad4-1747">**query_size** Zwraca rozmiar danych zapytania (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="a9ad4-1748">**max_query_size** Maksymalny rozmiar lokalizacji docelowej zapytania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="a9ad4-1749">stref.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1750">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1750">Return Values</span></span>

- <span data-ttu-id="a9ad4-1751">**NX_SUCCESS** (0X00) pomyślne zapytanie serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="a9ad4-1752">Rozmiar zapytania **NX_WEB_HTTP_FAILED** (0x30002) jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="a9ad4-1753">Nie znaleziono określonego zapytania **NX_WEB_HTTP_NOT_FOUND** (0x30006)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="a9ad4-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0X30013) brak zapytania w żądaniu klienta</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="a9ad4-1755">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1756">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1757">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1757">Allowed From</span></span>

<span data-ttu-id="a9ad4-1758">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1759">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="a9ad4-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="a9ad4-1761">Ustaw przemieszczenie fragmentaryczne dla odpowiedzi HTTP (S)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1762">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1763">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1763">Description</span></span>

<span data-ttu-id="a9ad4-1764">Ta usługa używa kodowania fragmentarycznego transferu do wysyłania niestandardowego pakietu danych odpowiedzi HTTP (S) utworzonego za pomocą *nx_web_http_server_response_packet_allocate*() do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1765">Jeśli aplikacja używa kodowania fragmentarycznego transferu do wysyłania pakietu danych odpowiedzi, musi wywołać tę usługę po wywołaniu *nx_web_http_server_response_packet_allocate*() i przed wywołaniem metody *nx_web_http_server_callback_packet_send*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1766">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1766">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1767">**client_ptr** Wskaźnik do bloku kontroli klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a9ad4-1768">**chunk_size** Rozmiar fragmentu danych w oktetach.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="a9ad4-1769">**packet_ptr** Wskaźnik pakietów danych żądania HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1770">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1770">Return Values</span></span>

- <span data-ttu-id="a9ad4-1771">Pomyślna konfiguracja zestawu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="a9ad4-1772">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1773">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1773">Allowed From</span></span>

<span data-ttu-id="a9ad4-1774">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1775">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="a9ad4-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="a9ad4-1777">Konfigurowanie serwera HTTP do korzystania z protokołu TLS dla bezpiecznego protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1778">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1778">Prototype</span></span>

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1779">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1779">Description</span></span>

<span data-ttu-id="a9ad4-1780">Ta usługa konfiguruje wcześniej utworzone wystąpienie serwera HTTP sieci Web NetX w celu używania protokołu TLS do bezpiecznej komunikacji HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="a9ad4-1781">Parametry służą do konfigurowania wszystkich możliwych sesji protokołu TLS o identycznym stanie, tak aby każde przychodzące działanie klienta HTTPS było spójne.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="a9ad4-1782">Liczba sesji TLS jest kontrolowana przy użyciu makra NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="a9ad4-1783">Tabela procedur kryptograficznych (tabela ciphersuite) jest współdzielona między wszystkimi sesjami TLS, ponieważ zawiera ona wskaźniki funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="a9ad4-1784">Bufory odzestawów metadanych i pakietów są rozdzielone równomiernie między wszystkimi sesjami TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="a9ad4-1785">Jeśli rozmiar buforu nie jest równo widoczny w liczbie sesji, pozostała część będzie niedostępna.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="a9ad4-1786">Certyfikat tożsamości przekazywania jest używany przez wszystkie sesje.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="a9ad4-1787">Podczas operacji TLS certyfikat tożsamości serwera jest odczytywany tylko z tego miejsca, dlatego kopie nie są konieczne dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="a9ad4-1788">Zaufane certyfikaty są dodawane do każdej sesji TLS na serwerze HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="a9ad4-1789">Są one używane do uwierzytelniania certyfikatów klientów, które są automatycznie włączane, gdy jest udostępniane zdalne miejsce na certyfikat.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="a9ad4-1790">Zdalna tablica i bufor certyfikatów są domyślnie udostępniane między wszystkimi sesjami protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="a9ad4-1791">Certyfikaty zdalne są używane do uwierzytelniania certyfikatów klientów, które są automatycznie włączane, gdy liczba certyfikatów zdalnych jest różna od zera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="a9ad4-1792">Ze względu na to, że bufor udostępnia niektóre sesje, może być blokowany podczas walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="a9ad4-1793">Aby wyłączyć uwierzytelnianie certyfikatu klienta, należy przekazać NX_NULL dla parametru remote_certificates i wartość 0 dla parametru remote_certs_num.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="a9ad4-1794">Wartości zwracane będą zawierać wszelkie kody błędów protokołu TLS, które wynikają z problemów w konfiguracji sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1795">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1795">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1796">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="a9ad4-1797">**crypto_table** Wskaźnik na tabelę protokołu TLS ciphersuite.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="a9ad4-1798">**metadata_buffer** Wskaźnik do bufora metadanych kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="a9ad4-1799">**metadata_size** Rozmiar buforu metadanych kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="a9ad4-1800">**packet_buffer** Bufor ponownego zestawu pakietów TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="a9ad4-1801">**packet_buffer** Rozmiar buforu pakietów TLS — powinien być równy (<żądany rozmiar buforu TLS \* NX_WEB_HTTP_SESSION_MAX).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="a9ad4-1802">**identity_certificate** Certyfikat tożsamości serwera TLS — będzie używany dla wszystkich sesji serwera HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="a9ad4-1803">**trusted_certificates** Wskaźnik do tablicy obiektów NX_SECURE_X509_CERT, służący do weryfikowania przychodzących certyfikatów klienta w przypadku włączenia uwierzytelniania certyfikatu klienta przez przekazanie wartości innej niż zero dla parametru *remote_certs_num* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="a9ad4-1804">**trusted_certs_num** Liczba zaufanych certyfikatów w tablicy *trusted_certificates* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="a9ad4-1805">**remote_certificates** Wskaźnik do tablicy obiektów NX_SECURE_X509_CERT, używany do przychodzących certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="a9ad4-1806">**remote_certs_num** Liczba certyfikatów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="a9ad4-1807">Powinna być maksymalną liczbą oczekiwanych certyfikatów od klientów.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="a9ad4-1808">Uwierzytelnianie certyfikatu klienta jest włączane automatycznie, gdy wartość jest różna od zera.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="a9ad4-1809">**remote_certificate_buffer** Bufor zawierający przychodzące certyfikaty zdalne od klientów, jeśli jest włączone uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="a9ad4-1810">remote_cert_buffer_size rozmiar buforu certyfikatów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="a9ad4-1811">Wartość musi być równa (<maksymalny oczekiwany rozmiar certyfikatu \* remote_certs_num).</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="a9ad4-1812">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1812">Return Values</span></span>

- <span data-ttu-id="a9ad4-1813">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a9ad4-1814">**NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="a9ad4-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) otrzymany typ komunikatu TLS jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="a9ad4-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="a9ad4-1817">Przetwarzanie komunikatu **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) podczas UZGADNIANIA protokołu TLS nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="a9ad4-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) komunikat przychodzący nie powiódł się podczas sprawdzania skrótu Mac.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="a9ad4-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) nie można wysłać podstawowego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="a9ad4-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) komunikat przychodzący miał nieprawidłową długość pola.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="a9ad4-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) odebrana wiadomość ChangeCipherSpec jest niepoprawna.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="a9ad4-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) przychodzący certyfikat TLS nie nadaje się do identyfikacji serwera zdalnego protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="a9ad4-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) szyfrowanie klucza publicznego dostarczone przez hosta zdalnego nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="a9ad4-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) host zdalny nie wskazywał ciphersuites, które są obsługiwane przez stos NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="a9ad4-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrany komunikat TLS miał nieznaną wersję protokołu TLS w jego nagłówku.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="a9ad4-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) odebrany komunikat TLS miał znaną, ale nieobsługiwaną wersję protokołu TLS w jego nagłówku.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="a9ad4-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się wewnętrzna alokacja pakietu TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="a9ad4-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny dostarczył nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="a9ad4-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="a9ad4-1830">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1831">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1831">Allowed From</span></span>

<span data-ttu-id="a9ad4-1832">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1833">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1833">Example</span></span>

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a><span data-ttu-id="a9ad4-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="a9ad4-1835">Uruchom serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1836">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1837">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1837">Description</span></span>

<span data-ttu-id="a9ad4-1838">Ta usługa uruchamia wcześniej utworzone wystąpienie serwera HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="a9ad4-1839">Serwery HTTPS korzystają z tego samego interfejsu API co HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="a9ad4-1840">Aby włączyć protokół HTTPS przy użyciu protokołu TLS na serwerze HTTP, zobacz *nx_web_http_server_secure_configure usługi ().*</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1841">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1841">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1842">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1843">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1843">Return Values</span></span>

- <span data-ttu-id="a9ad4-1844">**NX_SUCCESS** (0X00) pomyślne uruchomienie serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="a9ad4-1845">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1846">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1846">Allowed From</span></span>

<span data-ttu-id="a9ad4-1847">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1848">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="a9ad4-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="a9ad4-1850">Zatrzymaj serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1851">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1852">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1852">Description</span></span>

<span data-ttu-id="a9ad4-1853">Ta usługa przerywa poprzednio utworzone wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="a9ad4-1854">Ta procedura powinna być wywoływana przed usunięciem wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1855">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1855">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1856">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1857">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1857">Return Values</span></span>

- <span data-ttu-id="a9ad4-1858">**NX_SUCCESS** (0X00) pomyślne zatrzymanie serwera http</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="a9ad4-1859">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1860">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1861">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1861">Allowed From</span></span>

<span data-ttu-id="a9ad4-1862">Wątki</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1863">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="a9ad4-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="a9ad4-1865">Wyodrębnij typ pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1866">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1867">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="a9ad4-1868">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1868">This service is deprecated.</span></span> <span data-ttu-id="a9ad4-1869">Zaleca się, aby użytkownicy korzystali z usługi *nx_web_http_server_type_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="a9ad4-1870">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w *string_size* z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="a9ad4-1871">Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="a9ad4-1872">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="a9ad4-1873">Domyślne mapy MIME na serwerze HTTP NetX Web są następujące:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="a9ad4-1874">HTML text/html</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1874">html text/html</span></span>
- <span data-ttu-id="a9ad4-1875">htm text/html</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1875">htm text/html</span></span>
- <span data-ttu-id="a9ad4-1876">tekst txt/zwykły</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1876">txt text/plain</span></span>
- <span data-ttu-id="a9ad4-1877">obraz GIF/GIF</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1877">gif image/gif</span></span>
- <span data-ttu-id="a9ad4-1878">obraz JPG/JPEG</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="a9ad4-1879">ikona obrazu ICO/x</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1879">ico image/x-icon</span></span>

<span data-ttu-id="a9ad4-1880">Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="a9ad4-1881">Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_web_http_server_mime_maps_addtional_set ()* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1882">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1882">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1883">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a9ad4-1884">**Nazwa** Wskaźnik do buforu do przeszukania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="a9ad4-1885">**http_type_string** Wskaźnik do wyodrębnionego ciągu typu HTML</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="a9ad4-1886">**string_size** Wskaźnik zwracający wyekstrahowaną długość ciągu typu HTML.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1887">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1887">Return Values</span></span>

- <span data-ttu-id="a9ad4-1888">Pomyślna Ekstrakcja typu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="a9ad4-1889">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) domyślnie zwrócony "tekst/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1891">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1891">Allowed From</span></span>

<span data-ttu-id="a9ad4-1892">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1893">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1893">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="a9ad4-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="a9ad4-1895">Wyodrębnij typ pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1896">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="a9ad4-1897">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1897">Description</span></span>

<span data-ttu-id="a9ad4-1898">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w *string_size* z *nazwy* buforu wejściowego, zazwyczaj jest to adres URL.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="a9ad4-1899">Jeśli nie zostanie znaleziona żadna mapa MIME, domyślnie zostanie ustawiona wartość "text/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="a9ad4-1900">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapowaniami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="a9ad4-1901">Domyślne mapy MIME na serwerze HTTP NetX Web są następujące:</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="a9ad4-1902">HTML text/html</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1902">html text/html</span></span>
- <span data-ttu-id="a9ad4-1903">htm text/html</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1903">htm text/html</span></span>
- <span data-ttu-id="a9ad4-1904">tekst txt/zwykły</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1904">txt text/plain</span></span>
- <span data-ttu-id="a9ad4-1905">obraz GIF/GIF</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1905">gif image/gif</span></span>
- <span data-ttu-id="a9ad4-1906">obraz JPG/JPEG</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="a9ad4-1907">ikona obrazu ICO/x</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1907">ico image/x-icon</span></span>

<span data-ttu-id="a9ad4-1908">Jeśli ta wartość jest określona, przeszuka także zestaw dodatkowych mapowań MIME zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="a9ad4-1909">Aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika, zobacz *nx_web_http_server_mime_maps_addtional_set ()* .</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="a9ad4-1910">Ta usługa zastępuje *nx_web_http_server_type_get*().</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="a9ad4-1911">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1912">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1912">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1913">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a9ad4-1914">**Nazwa** Wskaźnik do buforu do przeszukania</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="a9ad4-1915">**name_length** Długość nazwy</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="a9ad4-1916">**http_type_string** Wskaźnik do wyodrębnionego ciągu typu HTML</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="a9ad4-1917">**http_type_string_max_size** Rozmiar buforu http_type_string</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="a9ad4-1918">**string_size** Wskaźnik zwracający wyodrębniony ciąg typu HTML</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="a9ad4-1919">Długość.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1920">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1920">Return Values</span></span>

- <span data-ttu-id="a9ad4-1921">Pomyślna Ekstrakcja typu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="a9ad4-1922">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) domyślnie zwrócony "tekst/zwykły".</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1924">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1924">Allowed From</span></span>

<span data-ttu-id="a9ad4-1925">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1926">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1926">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="a9ad4-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="a9ad4-1928">Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1929">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1929">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a><span data-ttu-id="a9ad4-1930">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1930">Description</span></span>

<span data-ttu-id="a9ad4-1931">Ta usługa ustawia wywołanie zwrotne wywoływane po wykonaniu uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1932">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1932">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1933">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a9ad4-1934">**digest_authenticate_callback** Wskaźnik do wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1935">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1935">Return Values</span></span>

- <span data-ttu-id="a9ad4-1936">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a9ad4-1937">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9ad4-1938">NX_NOT_SUPPORTED (0x4B) uwierzytelnianie szyfrowane nie jest włączone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1939">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1939">Allowed From</span></span>

<span data-ttu-id="a9ad4-1940">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1941">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1941">Example</span></span>

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="a9ad4-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="a9ad4-1943">Ustaw funkcję wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9ad4-1944">Prototype</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1944">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a><span data-ttu-id="a9ad4-1945">Opis</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1945">Description</span></span>

<span data-ttu-id="a9ad4-1946">Ta usługa ustawia wywołanie zwrotne wywoływane, gdy jest przeprowadzane sprawdzanie uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a9ad4-1947">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1947">Input Parameters</span></span>

- <span data-ttu-id="a9ad4-1948">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a9ad4-1949">**authenticate_check_externded** Wskaźnik do uwierzytelniania — wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="a9ad4-1950">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1950">Return Values</span></span>

- <span data-ttu-id="a9ad4-1951">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a9ad4-1952">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9ad4-1953">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1953">Allowed From</span></span>

<span data-ttu-id="a9ad4-1954">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="a9ad4-1955">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ad4-1955">Example</span></span>

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
