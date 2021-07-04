---
title: Rozdział 3 — Opis usług HTTP
description: Ten rozdział zawiera opis wszystkich internetowych usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bb2743f05c5b56331d1c0e948601ad23bf340d1
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875276"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="7cd3e-103">Rozdział 3 — Opis usług HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="7cd3e-104">Ten rozdział zawiera opis wszystkich internetowych usług HTTP NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-105">W sekcji "Wartości zwracane" w następujących  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości pogrubione, a wartości bez pogrubienia są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="7cd3e-106">Interfejs API klienta HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="7cd3e-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="7cd3e-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="7cd3e-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="7cd3e-108">Otwieranie gniazda w postaci zwykłego tekstu na serwerze HTTP dla żądań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7cd3e-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-109">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-110">Description</span></span>

<span data-ttu-id="7cd3e-111">Ta metoda jest dla protokołu HTTP **w postaci zwykłego** tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-112">Ta usługa otwiera gniazdo TCP w postaci zwykłego tekstu do serwera HTTP, ale nie wysyła żadnych żądań.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="7cd3e-113">Żądania są tworzone za pomocą n *x_web_http_client_request_initialize()* i wysyłane przy *użyciu nx_web_http_client_request_send()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="7cd3e-114">Niestandardowe nagłówki HTTP można dodać do żądania przy użyciu *nx_web_http_client_request_header_add().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="7cd3e-115">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="7cd3e-116">**Umożliwia to dostosowane żądania HTTP przeznaczone dla określonych aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-117">Metody nx_web_http_client_\*_start są udostępniane dla wygody (np. *nx_web_http_client_get_start*()) i obsługują generowanie żądań i połączenie gniazda.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="7cd3e-118">Możesz użyć tych usług zamiast *nx_web_http_client_connect()* i powiązanych procedur, jeśli nie potrzebujesz niestandardowych nagłówków HTTP w żądaniach.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-119">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-119">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-120">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-121">**server_ip** Adres IP zdalnego serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="7cd3e-122">**server_port** Port na zdalnym serwerze HTTP (np. 80 dla protokołu HTTP).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="7cd3e-123">**wait_option** Określa, jak długo usługa będzie czekać na bazowe operacje sieciowe.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="7cd3e-124">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-125">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-127">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-127">Return Values</span></span>

- <span data-ttu-id="7cd3e-128">**NX_SUCCESS** (0x00) Pomyślne połączenie gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="7cd3e-129">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-130">NX_WEB_HTTP_NOT_READY (0x3000A) Inne żądanie jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-131">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-131">Allowed From</span></span>

<span data-ttu-id="7cd3e-132">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-133">Example</span></span>

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
    "https://192.168.1.150/test.txt ", "host.com",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="7cd3e-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="7cd3e-134">nx_web_http_client_create</span></span>

<span data-ttu-id="7cd3e-135">Tworzenie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-137">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-137">Description</span></span>

<span data-ttu-id="7cd3e-138">Ta usługa tworzy wystąpienie klienta HTTP w określonym wystąpieniu adresu IP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="7cd3e-139">Wystąpienie klienta może być używane dla protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="7cd3e-140">Zobacz usługi *nx_web_http_client_connect()* i *nx_web_http_client_secure_connect(),* aby uzyskać więcej informacji na temat uruchamiania wystąpienia protokołu HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="7cd3e-141">Zapoznaj się również z interfejsem API dla metod \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_,** aby uzyskać proste wywołania metod GET, PUT i POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-142">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-142">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-143">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-144">**client_name** Nazwa wystąpienia klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="7cd3e-145">**ip_ptr** Wskaźnik do wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="7cd3e-146">**pool_ptr** Wskaźnik do domyślnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="7cd3e-147">Należy pamiętać, że pakiety w tej puli muszą mieć ładunek wystarczająco duży, aby obsłużyć pełny nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="7cd3e-148">Jest to definiowane *przez NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* w *nx_web_http_client.h.*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="7cd3e-149">**window_size** Rozmiar okna odbierania gniazda TCP klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-150">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-150">Return Values</span></span>

- <span data-ttu-id="7cd3e-151">**NX_SUCCESS** (0x00) Pomyślne utworzenie klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="7cd3e-152">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="7cd3e-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="7cd3e-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Nieprawidłowy rozmiar ładunku w puli pakietów</span><span class="sxs-lookup"><span data-stu-id="7cd3e-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-154">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-154">Allowed From</span></span>

<span data-ttu-id="7cd3e-155">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="7cd3e-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="7cd3e-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="7cd3e-158">Usuwanie wystąpienia klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-160">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-160">Description</span></span>

<span data-ttu-id="7cd3e-161">Ta usługa usuwa wcześniej utworzone wystąpienie klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-162">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-162">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-163">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-164">Return Values</span></span>

- <span data-ttu-id="7cd3e-165">**NX_SUCCESS** (0x00) Pomyślne usunięcie klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="7cd3e-166">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="7cd3e-167">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-168">Allowed From</span></span>

<span data-ttu-id="7cd3e-169">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="7cd3e-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="7cd3e-172">Uruchamianie żądania HTTP DELETE w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-174">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-174">Description</span></span>

<span data-ttu-id="7cd3e-175">Ta metoda jest dla protokołu HTTP **w postaci zwykłego** tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-176">Ta usługa próbuje wysłać żądanie DELETE dla zasobu określonego przez wskaźnik "resource" we wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-177">Jeśli ta procedura NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get()* w celu pobrania odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="7cd3e-178">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-179">Ten interfejs API jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-179">This API is deprecated.</span></span> <span data-ttu-id="7cd3e-180">Zachęcamy deweloperów do korzystania *z nx_web_http_client_delete_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-181">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-181">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-182">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-183">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-184">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-185">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-186">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-187">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-188">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-189">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-190">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-191">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-192">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-193">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-195">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-195">Return Values</span></span>

- <span data-ttu-id="7cd3e-196">**NX_SUCCESS** (0x00) Komunikat żądania DELETE klienta HTTP został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="7cd3e-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="7cd3e-197">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-199">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-201">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-202">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-203">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-203">Allowed From</span></span>

<span data-ttu-id="7cd3e-204">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-205">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-205">Example</span></span>

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

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="7cd3e-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="7cd3e-207">Uruchamianie żądania HTTP DELETE w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-208">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-209">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-209">Description</span></span>

<span data-ttu-id="7cd3e-210">Ta metoda służy do **zwykłego tekstu** HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-211">Ta usługa próbuje wysłać żądanie DELETE dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-212">Jeśli ta procedura NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="7cd3e-213">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-214">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą być zakończone wartością NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-215">Ta usługa zastępuje *nx_web_http_client_delete_start* ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="7cd3e-216">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-217">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-217">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-218">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-219">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-220">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-221">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-222">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-223">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-224">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-225">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-226">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-227">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-228">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-229">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-230">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-231">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-232">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-233">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-235">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-235">Return Values</span></span>

- <span data-ttu-id="7cd3e-236">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat żądania DELETE klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="7cd3e-237">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-239">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-241">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-242">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-243">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-243">Allowed From</span></span>

<span data-ttu-id="7cd3e-244">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-245">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-245">Example</span></span>

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

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="7cd3e-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="7cd3e-247">Uruchamianie zaszyfrowanego żądania HTTPS DELETE</span><span class="sxs-lookup"><span data-stu-id="7cd3e-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-249">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-249">Description</span></span>

<span data-ttu-id="7cd3e-250">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-251">Ta usługa próbuje wysłać żądanie DELETE dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-252">Jeśli ta procedura NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="7cd3e-253">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-254">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-254">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-255">Zachęcamy deweloperów do korzystania z *nx_web_http_client_delete_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-256">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-256">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-257">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-258">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-259">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-260">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="7cd3e-261">Zasób musi być zakończony wartością NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="7cd3e-262">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-263">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-264">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-265">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-266">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-267">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-268">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-269">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-270">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-271">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-273">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-273">Return Values</span></span>

- <span data-ttu-id="7cd3e-274">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat żądania DELETE klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="7cd3e-275">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-277">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-279">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-280">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-281">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-281">Allowed From</span></span>

<span data-ttu-id="7cd3e-282">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-283">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-283">Example</span></span>

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

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="7cd3e-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="7cd3e-285">Uruchamianie zaszyfrowanego żądania HTTPS DELETE</span><span class="sxs-lookup"><span data-stu-id="7cd3e-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-286">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-286">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-287">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-287">Description</span></span>

<span data-ttu-id="7cd3e-288">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-289">Ta usługa próbuje wysłać żądanie DELETE dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-290">Jeśli ta procedura NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="7cd3e-291">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-292">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu musi odpowiadać długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-293">Ta usługa zastępuje *nx_web_http_client_delete_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="7cd3e-294">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-295">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-295">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-296">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-297">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-298">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-299">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="7cd3e-300">Zasób musi być zakończony wartością NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="7cd3e-301">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-302">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-303">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-304">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-305">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-306">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-307">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-308">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-309">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-310">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-311">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-312">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-313">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-314">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-316">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-316">Return Values</span></span>

- <span data-ttu-id="7cd3e-317">**NX_SUCCESS** (0x00) Komunikat żądania DELETE klienta HTTP został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="7cd3e-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="7cd3e-318">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-320">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-322">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-323">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="7cd3e-324">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-324">Allowed From</span></span>

<span data-ttu-id="7cd3e-325">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-326">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-326">Example</span></span>

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

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="7cd3e-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="7cd3e-328">Uruchamianie żądania HTTP GET w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-329">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-330">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-330">Description</span></span>

<span data-ttu-id="7cd3e-331">Ta metoda jest dla protokołu HTTP **w postaci zwykłego** tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-332">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "resource" we wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-333">Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań metody *nx_web_http_client_response_body_get()* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="7cd3e-334">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-335">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-335">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-336">Zachęcamy deweloperów do korzystania *z nx_web_http_client_get_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-337">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-337">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-338">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-339">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-340">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-341">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-342">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-343">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-344">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-345">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-346">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-347">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-348">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-349">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-351">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-351">Return Values</span></span>

- <span data-ttu-id="7cd3e-352">**NX_SUCCESS** (0x00) Komunikat startowy GET klienta HTTP został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="7cd3e-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="7cd3e-353">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-355">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-357">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-358">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-359">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-359">Allowed From</span></span>

<span data-ttu-id="7cd3e-360">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-361">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-361">Example</span></span>

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

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="7cd3e-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="7cd3e-363">Uruchamianie żądania HTTP GET w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-365">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-365">Description</span></span>

<span data-ttu-id="7cd3e-366">Ta metoda jest dla protokołu HTTP **w postaci zwykłego** tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-367">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "resource" we wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-368">Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań metody *nx_web_http_client_response_body_get()* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="7cd3e-369">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-370">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-371">Ta usługa *zastępuje* nx_web_http_client_get_start ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="7cd3e-372">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-373">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-373">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-374">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-375">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-376">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-377">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-378">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-379">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-380">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-381">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-382">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-383">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-384">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-385">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-386">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-387">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-388">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-389">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-391">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-391">Return Values</span></span>

- <span data-ttu-id="7cd3e-392">**NX_SUCCESS** (0x00) Komunikat startowy GET klienta HTTP został pomyślnie wysłany</span><span class="sxs-lookup"><span data-stu-id="7cd3e-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="7cd3e-393">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-395">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-397">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-398">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-399">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-399">Allowed From</span></span>

<span data-ttu-id="7cd3e-400">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-401">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-401">Example</span></span>

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

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="7cd3e-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="7cd3e-403">Uruchamianie zaszyfrowanego żądania GET protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="7cd3e-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-405">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-405">Description</span></span>

<span data-ttu-id="7cd3e-406">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-407">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-408">Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań metody *nx_web_http_client_response_body_get()* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="7cd3e-409">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-410">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-410">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-411">Zachęcamy deweloperów do korzystania z *nx_web_http_client_get_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-412">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-412">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-413">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-414">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-415">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-416">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-417">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-418">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-419">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-420">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-421">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-422">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-423">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-424">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-425">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-426">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-428">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-428">Return Values</span></span>

- <span data-ttu-id="7cd3e-429">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat uruchomienia GET klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="7cd3e-430">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-432">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-434">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-435">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-436">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-436">Allowed From</span></span>

<span data-ttu-id="7cd3e-437">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-438">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-438">Example</span></span>

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

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="7cd3e-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="7cd3e-440">Uruchamianie zaszyfrowanego żądania GET protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="7cd3e-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-441">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-442">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-442">Description</span></span>

<span data-ttu-id="7cd3e-443">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-444">Ta usługa próbuje uzyskać zasób określony przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-445">Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wykonać wiele wywołań metody *nx_web_http_client_response_body_get()* w celu pobrania pakietów danych odpowiadających zawartości żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="7cd3e-446">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-447">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą być zakończone wartością NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-448">Ta usługa zastępuje *nx_web_http_client_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="7cd3e-449">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-450">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-450">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-451">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-452">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-453">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-454">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-455">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-456">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-457">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-458">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-459">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-460">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-461">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-462">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-463">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-464">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-465">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-466">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-467">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-468">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-470">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-470">Return Values</span></span>

- <span data-ttu-id="7cd3e-471">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat uruchomienia GET klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="7cd3e-472">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-474">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-476">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-477">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-478">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-478">Allowed From</span></span>

<span data-ttu-id="7cd3e-479">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-480">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-480">Example</span></span>

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

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="7cd3e-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="7cd3e-482">Uruchamianie żądania HTTP HEAD w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-483">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-484">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-484">Description</span></span>

<span data-ttu-id="7cd3e-485">Ta metoda służy do **zwykłego tekstu** HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-486">Ta usługa próbuje pobrać metadane HEAD dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-487">Jeśli ta procedura NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="7cd3e-488">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-489">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-489">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-490">Zachęcamy deweloperów do korzystania z *nx_web_http_client_head_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-491">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-491">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-492">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-493">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-494">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-495">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-496">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-497">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-498">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-499">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-500">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-501">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-502">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-503">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-505">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-505">Return Values</span></span>

- <span data-ttu-id="7cd3e-506">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat żądania HEAD klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="7cd3e-507">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-509">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-511">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-512">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-513">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-513">Allowed From</span></span>

<span data-ttu-id="7cd3e-514">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-515">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-515">Example</span></span>

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

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="7cd3e-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="7cd3e-517">Uruchamianie żądania HTTP HEAD w postaci zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-518">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-519">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-519">Description</span></span>

<span data-ttu-id="7cd3e-520">Ta metoda służy do **zwykłego tekstu** HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-521">Ta usługa próbuje pobrać metadane HEAD dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-522">Jeśli ta procedura NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="7cd3e-523">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-524">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu musi odpowiadać długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-525">Ta usługa zastępuje *nx_web_http_client_head_start*().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="7cd3e-526">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-527">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-527">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-528">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-529">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-530">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-531">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-532">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-533">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-534">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-535">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-536">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-537">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-538">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-539">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-540">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-541">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-542">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-543">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-545">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-545">Return Values</span></span>

- <span data-ttu-id="7cd3e-546">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat żądania HEAD klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="7cd3e-547">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-549">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-551">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-552">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-553">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-553">Allowed From</span></span>

<span data-ttu-id="7cd3e-554">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-555">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-555">Example</span></span>

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

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="7cd3e-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="7cd3e-557">Uruchamianie zaszyfrowanego żądania HTTPS HEAD</span><span class="sxs-lookup"><span data-stu-id="7cd3e-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-559">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-559">Description</span></span>

<span data-ttu-id="7cd3e-560">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-561">Ta usługa próbuje pobrać metadane HEAD dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-562">Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź serwera odpowiadającą żądanej zawartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="7cd3e-563">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-564">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-564">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-565">Zachęcamy deweloperów do korzystania z *nx_web_http_client_head_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-566">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-566">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-567">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-568">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-569">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-570">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-571">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-572">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-573">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-574">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-575">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-576">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-577">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-578">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-579">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-580">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-582">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-582">Return Values</span></span>

- <span data-ttu-id="7cd3e-583">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat żądania HEAD klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="7cd3e-584">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-586">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-588">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-589">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-590">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-590">Allowed From</span></span>

<span data-ttu-id="7cd3e-591">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-592">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-592">Example</span></span>

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

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="7cd3e-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="7cd3e-594">Uruchamianie zaszyfrowanego żądania HTTPS HEAD</span><span class="sxs-lookup"><span data-stu-id="7cd3e-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-595">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-596">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-596">Description</span></span>

<span data-ttu-id="7cd3e-597">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-598">Ta usługa próbuje pobrać metadane HEAD dla zasobu określonego przez wskaźnik "resource" na wcześniej utworzonym wystąpieniu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-599">Jeśli ta procedura zwraca NX_SUCCESS, aplikacja może następnie wywołać *nx_web_http_client_response_body_get(),* aby pobrać odpowiedź serwera odpowiadającą żądanej zawartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="7cd3e-600">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` GET.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="7cd3e-601">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu musi odpowiadać długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-602">Ta usługa *zastępuje* nx_web_http_client_head_secure_start ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="7cd3e-603">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-604">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-604">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-605">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-606">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-607">**server_port** Port na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-608">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-609">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-610">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-611">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-612">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-613">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-614">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-615">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-616">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-617">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-618">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-619">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-620">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-621">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-622">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-624">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-624">Return Values</span></span>

- <span data-ttu-id="7cd3e-625">**NX_SUCCESS** (0x00) Pomyślnie wysłano komunikat żądania HEAD klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="7cd3e-626">**NX_WEB_HTTP_ERROR** (0x30000) Wewnętrzny błąd klienta HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="7cd3e-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-628">**NX_WEB_HTTP_FAILED** (0x30002) klienta HTTP komunikuje się z serwerem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub hasło.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="7cd3e-630">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-631">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-632">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-632">Allowed From</span></span>

<span data-ttu-id="7cd3e-633">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-634">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-634">Example</span></span>

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

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="7cd3e-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7cd3e-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="7cd3e-636">Przydzielanie pakietu HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-637">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-638">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-638">Description</span></span>

<span data-ttu-id="7cd3e-639">Ta usługa próbuje przydzielić pakiet dla protokołu HTTP(S) klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-640">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-640">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-641">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-642">**packet_ptr** Wskaźnik do przydzielonego pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="7cd3e-643">**wait_option** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="7cd3e-644">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="7cd3e-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="7cd3e-647">**limit czasu w taktach** (0x00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-648">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-648">Return Values</span></span>

- <span data-ttu-id="7cd3e-649">**NX_SUCCESS** (0x00) Pomyślne przydzielenie pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="7cd3e-650">**NX_NO_PACKET** (0x01) Brak dostępnych pakietów</span><span class="sxs-lookup"><span data-stu-id="7cd3e-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="7cd3e-651">**NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort *.*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="7cd3e-652">**NX_INVALID_PARAMETERS** (0x4D) Rozmiar pakietu nie obsługuje protokołu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="7cd3e-653">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-654">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-655">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-655">Allowed From</span></span>

<span data-ttu-id="7cd3e-656">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-657">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="7cd3e-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="7cd3e-659">Uruchamianie żądania HTTP POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-660">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-661">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-661">Description</span></span>

<span data-ttu-id="7cd3e-662">Ta metoda służy do **zwykłego tekstu** HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-663">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTP pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-664">Jeśli ta procedura powiedzie się, kod aplikacji  powinien wysyłać kolejne wywołania do nx_web_http_client_put_packet, aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-665">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-666">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-666">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-667">Zachęcamy deweloperów do korzystania z *nx_web_http_client_post_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-668">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-668">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-669">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-670">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-671">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-672">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="7cd3e-673">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-674">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-675">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-676">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-677">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-678">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-679">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-680">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-681">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-682">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-684">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-684">Return Values</span></span>

- <span data-ttu-id="7cd3e-685">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="7cd3e-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-688">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-689">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-690">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-691">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-691">Allowed From</span></span>

<span data-ttu-id="7cd3e-692">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-693">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-693">Example</span></span>

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

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="7cd3e-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="7cd3e-695">Uruchamianie żądania HTTP POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-696">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-697">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-697">Description</span></span>

<span data-ttu-id="7cd3e-698">Ta metoda służy do **zwykłego tekstu** HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-699">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTP pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-700">Jeśli ta procedura powiedzie się, kod aplikacji  powinien wysyłać kolejne wywołania do nx_web_http_client_put_packet, aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-701">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-702">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-703">Ta usługa zastępuje *nx_web_http_client_post_start* ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="7cd3e-704">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-705">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-705">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-706">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-707">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-708">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-709">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-710">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-711">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-712">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-713">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-714">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-715">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-716">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-717">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-718">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-719">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-720">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-721">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-722">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-723">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-725">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-725">Return Values</span></span>

- <span data-ttu-id="7cd3e-726">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="7cd3e-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-729">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-730">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-731">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-732">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-732">Allowed From</span></span>

<span data-ttu-id="7cd3e-733">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-734">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-734">Example</span></span>

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

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="7cd3e-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="7cd3e-736">Uruchamianie zaszyfrowanego żądania HTTPS POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-737">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-737">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-738">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-738">Description</span></span>

<span data-ttu-id="7cd3e-739">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-740">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTPS pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-741">Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do *procedury nx_web_http_client_put_packet(),* aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-742">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-743">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-743">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-744">Zachęcamy deweloperów do korzystania *z nx_web_http_client_post_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-745">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-745">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-746">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-747">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-748">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-749">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="7cd3e-750">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-751">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-752">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-753">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-754">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-755">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-756">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-757">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-758">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-759">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-760">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-761">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-763">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-763">Return Values</span></span>

- <span data-ttu-id="7cd3e-764">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="7cd3e-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-767">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-768">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-769">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-770">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-770">Allowed From</span></span>

<span data-ttu-id="7cd3e-771">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-772">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-772">Example</span></span>

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

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="7cd3e-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="7cd3e-774">Uruchamianie zaszyfrowanego żądania HTTPS POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-775">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-775">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-776">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-776">Description</span></span>

<span data-ttu-id="7cd3e-777">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-778">Ta usługa próbuje wysłać żądanie POST z określonym zasobem do serwera HTTPS pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-779">Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do *procedury nx_web_http_client_put_packet(),* aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-780">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-781">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-782">Ta usługa *zastępuje* nx_web_http_client_post_secure_start ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="7cd3e-783">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-784">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-784">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-785">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-786">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-787">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-788">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-789">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-790">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-791">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-792">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-793">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-794">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-795">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-796">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-797">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-798">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-799">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-800">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-801">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-802">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-803">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-804">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-806">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-806">Return Values</span></span>

- <span data-ttu-id="7cd3e-807">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie POST</span><span class="sxs-lookup"><span data-stu-id="7cd3e-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="7cd3e-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-810">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-811">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-812">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-813">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-813">Allowed From</span></span>

<span data-ttu-id="7cd3e-814">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-815">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-815">Example</span></span>

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

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="7cd3e-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="7cd3e-817">Uruchamianie żądania HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-819">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-819">Description</span></span>

<span data-ttu-id="7cd3e-820">Ta metoda jest dla protokołu HTTP **w postaci zwykłego** tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-821">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-822">Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do *procedury nx_web_http_client_put_packet(),* aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-823">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-824">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-824">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-825">Zachęcamy deweloperów do korzystania *z nx_web_http_client_put_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-826">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-826">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-827">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-828">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-829">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-830">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="7cd3e-831">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-832">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-833">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-834">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-835">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-836">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-837">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-838">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-839">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-840">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-842">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-842">Return Values</span></span>

- <span data-ttu-id="7cd3e-843">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="7cd3e-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-846">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-847">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-848">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-849">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-849">Allowed From</span></span>

<span data-ttu-id="7cd3e-850">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-851">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-851">Example</span></span>

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

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="7cd3e-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="7cd3e-853">Uruchamianie żądania HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-854">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-855">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-855">Description</span></span>

<span data-ttu-id="7cd3e-856">Ta metoda jest dla protokołu HTTP **w postaci zwykłego** tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="7cd3e-857">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTP pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-858">Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do *procedury nx_web_http_client_put_packet(),* aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-859">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-860">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-861">Ta usługa zastępuje *nx_web_http_client_put_start* ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="7cd3e-862">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-863">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-863">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-864">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-865">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-866">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-867">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-868">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-869">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-870">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-871">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-872">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-873">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-874">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-875">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-876">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-877">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-878">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-879">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-880">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-881">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-883">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-883">Return Values</span></span>

- <span data-ttu-id="7cd3e-884">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="7cd3e-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-887">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-888">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-889">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-890">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-890">Allowed From</span></span>

<span data-ttu-id="7cd3e-891">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-892">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-892">Example</span></span>

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

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="7cd3e-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="7cd3e-894">Uruchamianie zaszyfrowanego żądania HTTPS PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-896">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-896">Description</span></span>

<span data-ttu-id="7cd3e-897">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-898">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTPS pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-899">Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do *procedury nx_web_http_client_put_packet(),* aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-900">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-901">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-901">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-902">Zachęcamy deweloperów do korzystania z *nx_web_http_client_put_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-903">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-903">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-904">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-905">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-906">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-907">**zasób** Wskaźnik do ciągu adresu URL dla zasobu do wysłania do serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="7cd3e-908">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-909">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-910">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-911">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-912">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-913">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-914">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-915">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-916">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-917">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-918">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-919">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-921">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-921">Return Values</span></span>

- <span data-ttu-id="7cd3e-922">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="7cd3e-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-925">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-926">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-927">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-928">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-928">Allowed From</span></span>

<span data-ttu-id="7cd3e-929">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-930">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-930">Example</span></span>

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

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="7cd3e-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="7cd3e-932">Uruchamianie zaszyfrowanego żądania HTTPS PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-933">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-933">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-934">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-934">Description</span></span>

<span data-ttu-id="7cd3e-935">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-936">Ta usługa próbuje wysłać żądanie PUT z określonym zasobem do serwera HTTPS pod podanym adresem IP i portem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="7cd3e-937">Jeśli ta procedura powiedzie się, kod aplikacji powinien wysyłać kolejne wywołania do procedury *nx_web_http_client_put_packet(),* aby wysłać zawartość zasobu do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-938">Należy pamiętać, że ciąg zasobu może odwoływać się do pliku lokalnego, np. "/index.htm", lub może odwoływać się do innego adresu URL, np. jeśli serwer HTTP wskazuje, że obsługuje odwoływanie się do żądań `http://abc.website.com/index.htm` PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="7cd3e-939">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu musi odpowiadać długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-940">Ta usługa zastępuje *nx_web_http_client_put_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="7cd3e-941">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-942">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-942">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-943">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-944">**ip_address** Adres IP serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-945">**server_port** Port TCP na zdalnym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-946">**zasób** Wskaźnik do ciągu adresu URL dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="7cd3e-947">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-948">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-949">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-950">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-951">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-952">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-953">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-954">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-955">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-956">**total_bytes** Całkowita liczba bajtów wysyłanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="7cd3e-957">Należy pamiętać, że łączna długość wszystkich pakietów wysyłanych za pośrednictwem kolejnych wywołań *do nx_web_http_client_put_packet()* musi być równa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="7cd3e-958">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-959">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-960">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-961">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-962">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-964">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-964">Return Values</span></span>

- <span data-ttu-id="7cd3e-965">**NX_SUCCESS** (0x00) Pomyślnie wysłano żądanie PUT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="7cd3e-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nazwa użytkownika jest zbyt duża dla buforu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="7cd3e-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-968">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-969">NX_SIZE_ERROR (0x09) Nieprawidłowy całkowity rozmiar zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="7cd3e-970">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-971">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-971">Allowed From</span></span>

<span data-ttu-id="7cd3e-972">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-973">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-973">Example</span></span>

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

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="7cd3e-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="7cd3e-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="7cd3e-975">Wyślij następny pakiet danych zasobów</span><span class="sxs-lookup"><span data-stu-id="7cd3e-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-977">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-977">Description</span></span>

<span data-ttu-id="7cd3e-978">Ta usługa próbuje wysłać następny pakiet zawartości zasobów do serwera HTTP dla operacji PUT i POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="7cd3e-979">Należy pamiętać, że ta procedura powinna być wywoływana powtarzalnie, dopóki łączna długość wysłanych pakietów nie będzie równa "total_bytes" określonej w poprzednim wywołaniu *nx_web_http_client_put_start()* lub *nx_web_http_client_post_start()* (lub ich odpowiednich bezpiecznych wersjach).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="7cd3e-980">Ta usługa sprawdza również odpowiedź z serwera w przypadku wystąpienia problemu z nawiązaniem połączenia HTTP (lub HTTPS).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-981">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-981">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-982">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-983">**packet_ptr** Wskaźnik do następnej zawartości zasobu do wysłania do serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="7cd3e-984">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-985">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-986">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-988">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-988">Return Values</span></span>

- <span data-ttu-id="7cd3e-989">**NX_SUCCESS** (0x00) Pomyślnie wysłano pakiet klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="7cd3e-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span><span class="sxs-lookup"><span data-stu-id="7cd3e-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="7cd3e-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Odebrano kod błędu serwera\*\*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="7cd3e-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="7cd3e-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nieprawidłowa nazwa i/lub Hasło</span><span class="sxs-lookup"><span data-stu-id="7cd3e-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="7cd3e-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Serwer odpowiada przed zakończeniem put</span><span class="sxs-lookup"><span data-stu-id="7cd3e-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="7cd3e-995">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-996">NX_INVALID_PACKET (0x12) Zbyt mały pakiet dla nagłówka TCP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="7cd3e-997">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-998">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-998">Allowed From</span></span>

<span data-ttu-id="7cd3e-999">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1000">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="7cd3e-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="7cd3e-1002">Ustawianie fragmentowego transferu dla żądania HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1003">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1004">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1004">Description</span></span>

<span data-ttu-id="7cd3e-1005">Ta usługa używa fragmentatywnego kodu transferu do wysyłania niestandardowych żądań HTTP(S) do serwera określonego w wywołaniu *nx_web_http_client_connect()* lub *nx_web_http_client_secure_connect(),* które wcześniej nawiązyło połączenie gniazda z hostem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1006">Jeśli aplikacja używa fragmentów kodu transferu do wysyłania pakietu danych żądania, musi wywołać tę usługę po wywołaniu nx_web_http_client_request_packet_allocate *()* i przed wywołaniem nx_web_http_client_reqeust_packet_send *().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1007">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1007">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1008">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1009">**chunk_size** Rozmiar danych fragmentów w oktetach.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="7cd3e-1010">**packet_ptr** Wskaźnik pakietów danych żądania HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1011">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1011">Return Values</span></span>

- <span data-ttu-id="7cd3e-1012">**NX_SUCCESS** (0x00) Pomyślnie ustawiono fragment.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="7cd3e-1013">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1014">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1014">Allowed From</span></span>

<span data-ttu-id="7cd3e-1015">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1016">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
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

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="7cd3e-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="7cd3e-1018">Dodawanie niestandardowego nagłówka do niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1019">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1020">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1020">Description</span></span>

<span data-ttu-id="7cd3e-1021">Ta usługa dodaje niestandardowy nagłówek (w postaci nazwy i wartości pola) do niestandardowego żądania HTTP utworzonego za pomocą n *x_web_http_client_request_initialize()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="7cd3e-1022">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="7cd3e-1023">**Umożliwia to korzystanie z dostosowanych żądań HTTP przeznaczonych dla określonych aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1024">Dla nx_web_http_client_ \* _start metody są dostępne dla wygody.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="7cd3e-1025">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz *z nx_web_http_client_request_initialize()) do* tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1026">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1026">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1027">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1028">**field_name** Ciąg nazwy pola (np. "Content-Type").</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="7cd3e-1029">**name_length** Długość ciągu nazwy pola w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="7cd3e-1030">**field_value** Ciąg wartości pola (np. "application/octet-stream").</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="7cd3e-1031">**value_length** Długość ciągu wartości w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="7cd3e-1032">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1033">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1034">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1036">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1036">Return Values</span></span>

- <span data-ttu-id="7cd3e-1037">**NX_SUCCESS** (0x00) Pomyślne dodanie nagłówka do żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="7cd3e-1038">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1039">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1039">Allowed From</span></span>

<span data-ttu-id="7cd3e-1040">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1041">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
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
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="7cd3e-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="7cd3e-1043">Inicjowanie niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1044">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1045">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1045">Description</span></span>

<span data-ttu-id="7cd3e-1046">Ta usługa tworzy niestandardowe żądanie HTTP i kojarzy je z wystąpieniem klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-1047">W przeciwieństwie *do prostszych nx_web_http_client_get_start()* (wraz z metodami PUT, POST i skojarzonymi bezpiecznymi wersjami tych interfejsów API), żądanie niestandardowe nie jest wysyłane do momentu wywołania usługi *nx_web_http_client_request_send().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="7cd3e-1048">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu ***nx_web_http_client_request_header_add().***</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="7cd3e-1049">Umożliwia to korzystanie z dostosowanych żądań HTTP przeznaczonych dla określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1050">Dla nx_web_http_client_ \* _start metody są dostępne dla wygody.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="7cd3e-1051">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz *nx_web_http_client_request_send())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="7cd3e-1052">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1052">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-1053">Zachęcamy deweloperów do korzystania z *nx_web_http_client_request_initialize_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1054">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1054">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1055">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1056">**metoda** Metoda żądania HTTP do użycia.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="7cd3e-1057">Opcje są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="7cd3e-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="7cd3e-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="7cd3e-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="7cd3e-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="7cd3e-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="7cd3e-1064">**zasób** Nazwa przenoszonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="7cd3e-1065">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-1066">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-1067">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-1068">**input_size** Rozmiar danych wejściowych dla put i POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="7cd3e-1069">Przekaż 0 dla innych operacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="7cd3e-1070">**transfer_encoding_trunked** Parametr zarezerwowany dla przyszłej obsługi transferu magistralowego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="7cd3e-1071">**nazwa użytkownika** Nazwa użytkownika dla chronionych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="7cd3e-1072">**hasło** Hasło dla chronionych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="7cd3e-1073">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1074">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1075">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1077">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1077">Return Values</span></span>

- <span data-ttu-id="7cd3e-1078">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="7cd3e-1079">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Brakuje niektórych wymaganych informacji (np. input_size put lub POST).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1081">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1081">Allowed From</span></span>

<span data-ttu-id="7cd3e-1082">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1083">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1083">Example</span></span>

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="7cd3e-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="7cd3e-1085">Inicjowanie niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1086">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1087">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1087">Description</span></span>

<span data-ttu-id="7cd3e-1088">Ta usługa tworzy niestandardowe żądanie HTTP i kojarzy je z wystąpieniem klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="7cd3e-1089">W przeciwieństwie *do prostszych nx_web_http_client_get_start()* (wraz z metodami PUT, POST i skojarzonymi bezpiecznymi wersjami tych interfejsów API), żądanie niestandardowe nie jest wysyłane do momentu wywołania usługi *nx_web_http_client_request_send().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="7cd3e-1090">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu ***nx_web_http_client_request_header_add().***</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="7cd3e-1091">Umożliwia to korzystanie z dostosowanych żądań HTTP przeznaczonych dla określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1092">Dla nx_web_http_client_ \* _start metody są dostępne dla wygody.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="7cd3e-1093">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz *nx_web_http_client_request_send())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="7cd3e-1094">Ciągi zasobu, hosta, nazwy użytkownika i hasła muszą mieć wartość NULL, a długość każdego ciągu musi odpowiadać długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-1095">Ta usługa zastępuje *nx_web_http_client_request_initialize*().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="7cd3e-1096">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1097">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1097">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1098">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1099">**metoda** Metoda żądania HTTP do użycia.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="7cd3e-1100">Opcje są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="7cd3e-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="7cd3e-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="7cd3e-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="7cd3e-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="7cd3e-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="7cd3e-1107">**zasób** Nazwa przenoszonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="7cd3e-1108">**resource_length** Długość ciągu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="7cd3e-1109">**host** Ciąg nazwy domeny serwera z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="7cd3e-1110">Ten ciąg jest przesyłany w polu nagłówka hosta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="7cd3e-1111">Ciąg hosta nie może mieć wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="7cd3e-1112">**host_length** Długość ciągu hosta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="7cd3e-1113">**input_size** Rozmiar danych wejściowych dla put i POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="7cd3e-1114">Przekaż 0 dla innych operacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="7cd3e-1115">**transfer_encoding_trunked** Parametr zarezerwowany dla przyszłej obsługi transferu magistralowego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="7cd3e-1116">**nazwa użytkownika** Wskaźnik do opcjonalnej nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-1117">**username_length** Długość ciągu nazwy użytkownika do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="7cd3e-1118">**hasło** Wskaźnik do opcjonalnego hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="7cd3e-1119">**password_length** Długość ciągu hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="7cd3e-1120">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1121">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1122">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1124">Return Values</span></span>

- <span data-ttu-id="7cd3e-1125">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="7cd3e-1126">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Brakuje niektórych wymaganych informacji (np. input_size put lub POST).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1128">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1128">Allowed From</span></span>

<span data-ttu-id="7cd3e-1129">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1130">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1130">Example</span></span>

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="7cd3e-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="7cd3e-1132">Wyślij pakiet danych żądania HTTP(S) do serwera zdalnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1133">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1134">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1134">Description</span></span>

<span data-ttu-id="7cd3e-1135">Ta usługa wysyła niestandardowy pakiet danych żądania HTTP(S) utworzony za pomocą funkcji *nx_web_http_client_request_packet_allocate* () do serwera określonego w wywołaniu *funkcji nx_web_http_client_connect()* lub *nx_web_http_client_secure_connect(*), który wcześniej nawiąował połączenie gniazda z hostem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1136">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1136">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1137">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1138">**packet_ptr** Wskaźnik pakietów danych żądania HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="7cd3e-1139">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1140">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1141">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1143">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1143">Return Values</span></span>

- <span data-ttu-id="7cd3e-1144">**NX_SUCCESS** (0x00) Pomyślne wysłanie pakietu danych żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="7cd3e-1145">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1146">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1146">Allowed From</span></span>

<span data-ttu-id="7cd3e-1147">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1148">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
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

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="7cd3e-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="7cd3e-1150">Wysyłanie niestandardowego żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1151">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1152">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1152">Description</span></span>

<span data-ttu-id="7cd3e-1153">Ta usługa wysyła niestandardowe żądanie HTTP utworzone za pomocą funkcji *nx_web_http_client_request_initialize()* do serwera określonego w funkcji *nx_web_http_client_connect()* lub *nx_web_http_client_secure_connect(),* które wcześniej nawiązyły połączenie gniazda z hostem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="7cd3e-1154">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania przy użyciu ***nx_web_http_client_request_header_add().***</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="7cd3e-1155">Umożliwia to korzystanie z dostosowanych żądań HTTP przeznaczonych dla określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1156">Dla nx_web_http_client_ \* _start metody są dostępne dla wygody.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="7cd3e-1157">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz *z nx_web_http_client_request_initialize()) do* tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1158">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1158">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1159">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1160">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1161">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1162">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1164">Return Values</span></span>

- <span data-ttu-id="7cd3e-1165">**NX_SUCCESS** (0x00) Pomyślne wysłanie żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="7cd3e-1166">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1167">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1167">Allowed From</span></span>

<span data-ttu-id="7cd3e-1168">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1169">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="7cd3e-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="7cd3e-1171">Uzyskiwanie następnego pakietu danych zasobów</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1172">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1173">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1173">Description</span></span>

<span data-ttu-id="7cd3e-1174">Ta usługa pobiera następny pakiet zawartości zasobu żądanego przez poprzednie *wywołanie nx_web_http_client_get_start()* *lub nx_web_http_client_get_secure_start().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="7cd3e-1175">Kolejne wywołania tej procedury powinny być dokonywane do momentu, gdy zostanie odebrany NX_WEB_HTTP_GET_DONE zwracany stan.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1176">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1176">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1177">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1178">**packet_ptr** Miejsce docelowe wskaźnika pakietu zawierającego częściową zawartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="7cd3e-1179">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1180">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1181">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1183">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1183">Return Values</span></span>

- <span data-ttu-id="7cd3e-1184">**NX_SUCCESS** (0x00) Pomyślne uzyskiwanie pakietu klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="7cd3e-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) http client get packet is done</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="7cd3e-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client nie jest w trybie get.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="7cd3e-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Nieprawidłowa długość pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="7cd3e-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) Kod stanu HTTP 100 Kontynuuj</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="7cd3e-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) Kod stanu HTTP 101 Protokoły przełączania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="7cd3e-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) Kod stanu HTTP 201 Utworzono</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="7cd3e-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) Kod stanu HTTP 202 Zaakceptowane</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="7cd3e-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) Kod stanu HTTP 203 Informacje nie autorytatywne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="7cd3e-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) kod stanu HTTP 204 Brak zawartości</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="7cd3e-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) Kod stanu HTTP 205 Resetowanie zawartości</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="7cd3e-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) Kod stanu HTTP 206 Zawartość częściowa</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="7cd3e-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) Kod stanu HTTP 300 Wielokrotny wybór</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="7cd3e-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently (Kod stanu HTTP 301 przeniesiony trwale)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="7cd3e-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) Znaleziono kod stanu HTTP 302</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="7cd3e-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) Kod stanu HTTP 303 Zobacz inne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="7cd3e-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) Kod stanu HTTP 304 Nie zmodyfikowano</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="7cd3e-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) KOD STANU HTTP 305 Użyj serwera proxy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="7cd3e-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) http status code 307 Temporary Redirect</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="7cd3e-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) Http status code 400 Bad Request</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="7cd3e-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="7cd3e-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) KOD STANU HTTP 402 Wymagana płatność</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="7cd3e-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="7cd3e-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) Http status code 404 Not Found (Nie znaleziono kodu stanu HTTP 404)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="7cd3e-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) kod stanu HTTP 405, metoda jest niedozwolone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="7cd3e-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) kod stanu HTTP 406 Not Acceptable</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="7cd3e-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) Kod stanu HTTP 407 Wymagane uwierzytelnianie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="7cd3e-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) Kod stanu HTTP 408 — przeo min żądania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="7cd3e-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) Http status code 409 Conflict (Konflikt kodu stanu HTTP 409)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="7cd3e-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) Kod stanu HTTP 410 Gone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="7cd3e-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) Kod stanu HTTP 411 Wymagana długość</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="7cd3e-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) Kod stanu HTTP 412 Niepowodzenie warunku wstępnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="7cd3e-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large (Zbyt duża jednostka żądania)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="7cd3e-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) Kod stanu HTTP 414 Adres URL żądania jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="7cd3e-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type (Nieobsługiwany typ nośnika)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="7cd3e-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) Kod stanu HTTP 416 Żądany zakres nie jest dostępny</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="7cd3e-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed (Oczekiwanie nie powiodło się)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="7cd3e-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) kod stanu HTTP 500 Internal Server Error</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="7cd3e-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) Kod stanu HTTP 501 Nie zaimplementowano</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="7cd3e-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) KOD STANU HTTP 502 Zła brama</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="7cd3e-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) KOD STANU HTTP 503 Usługa niedostępna</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="7cd3e-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) Kod stanu HTTP 504 — prze wychodzący czas bramy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="7cd3e-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) Http status code 505 HTTP Version not supported (Kod stanu HTTP 505 WERSJA HTTP nie jest obsługiwana)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="7cd3e-1227">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1228">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1229">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1229">Allowed From</span></span>

<span data-ttu-id="7cd3e-1230">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1231">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="7cd3e-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="7cd3e-1233">Ustawianie wywołania zwrotnego w celu wywołania podczas przetwarzania nagłówków HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1234">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="7cd3e-1235">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1235">Description</span></span>

<span data-ttu-id="7cd3e-1236">Ta usługa przypisuje wywołanie zwrotne, które będzie wywoływane za każdym razem, gdy klient HTTP sieci Web NetX przetwarza nagłówek HTTP w odpowiedzi przychodzącej ze zdalnego serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="7cd3e-1237">Wywołanie zwrotne jest wywoływane raz dla każdego nagłówka w odpowiedzi podczas przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="7cd3e-1238">Wywołanie zwrotne umożliwia aplikacji klienckiej HTTP dostęp do każdego nagłówka w odpowiedzi serwera HTTP w celu podjęcia wszelkich żądanych akcji wykraczających poza podstawowe przetwarzanie, które robi internetowy klient HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1239">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1239">Input Parameters</span></span>

<span data-ttu-id="7cd3e-1240">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="7cd3e-1241">**callback_function** Wywołanie zwrotne wywoływane podczas przetwarzania nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="7cd3e-1242">Wywołanie zwrotne jest wywoływane z nazwą pola i wartością jako ciągami (i ich długościami).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="7cd3e-1243">Na przykład nagłówek "Content-Length: 100" spowoduje wywołanie funkcji z ciągiem "Content-Length" dla field_name i ciągiem "100" dla field_value *.* </span><span class="sxs-lookup"><span data-stu-id="7cd3e-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1244">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1244">Return Values</span></span>

- <span data-ttu-id="7cd3e-1245">**NX_SUCCESS** (0x00) Pomyślne przypisanie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="7cd3e-1246">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1247">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1247">Allowed From</span></span>

<span data-ttu-id="7cd3e-1248">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1249">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1249">Example</span></span>

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

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="7cd3e-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="7cd3e-1251">Otwieranie sesji protokołu TLS na serwerze HTTPS dla żądań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1252">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1253">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1253">Description</span></span>

<span data-ttu-id="7cd3e-1254">Ta metoda jest stosowana w przypadku protokołu HTTPS **zabezpieczonego protokołem TLS.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="7cd3e-1255">Ta usługa otwiera zabezpieczoną sesję protokołu TLS na serwerze HTTPS, ale nie wysyła żadnych żądań.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="7cd3e-1256">Żądania są tworzone za pomocą n *x_web_http_client_request_initialize()* i wysyłane przy *użyciu nx_web_http_client_request_send()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="7cd3e-1257">Niestandardowe nagłówki HTTP można dodać do żądania przy użyciu *nx_web_http_client_request_header_add().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="7cd3e-1258">Użycie tej usługi umożliwia aplikacji dodanie dowolnej liczby nagłówków niestandardowych do żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="7cd3e-1259">**Umożliwia to dostosowane żądania HTTP przeznaczone dla określonych aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1260">Dla wygody \* nx_web_http_client_ _start metody.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="7cd3e-1261">Wszystkie te funkcje używają tej procedury wewnętrznie (wraz *z nx_web_http_client_request_initialize())* do tworzenia i wysyłania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1262">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1262">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1263">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1264">**server_ip** Adres IP zdalnego serwera HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="7cd3e-1265">**server_port** Port na zdalnym serwerze HTTPS (np. 443 dla protokołu HTTPS).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="7cd3e-1266">**tls_setup** Wywołanie zwrotne używane do konfigurowania konfiguracji zabezpieczeń TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="7cd3e-1267">Aplikacja definiuje to wywołanie zwrotne w celu zainicjowania kryptografii i poświadczeń TLS (np. certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="7cd3e-1268">**wait_option** Określa, jak długo usługa będzie czekać na żądanie get start klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="7cd3e-1269">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1270">**Wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="7cd3e-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wywołujący wątek zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1272">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1272">Return Values</span></span>

- <span data-ttu-id="7cd3e-1273">**NX_SUCCESS** (0x00) Pomyślne połączenie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="7cd3e-1274">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Inne żądanie jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1276">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1276">Allowed From</span></span>

<span data-ttu-id="7cd3e-1277">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1278">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1278">Example</span></span>

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
    "https://192.168.1.150/test.txt ", "host.com",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="7cd3e-1279">Interfejs API serwera HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="7cd3e-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="7cd3e-1281">Ustawianie wywołania zwrotnego w celu pobrania maksymalnego wieku i daty adresu URL</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1282">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="7cd3e-1283">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1283">Description</span></span>

<span data-ttu-id="7cd3e-1284">Ta usługa ustawia wywołaną usługę wywołania zwrotnego w celu uzyskania maksymalnego wieku i daty ostatniej modyfikacji określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1285">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1285">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1286">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1287">**cache_info_get** Wskaźnik do wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="7cd3e-1288">**max_age** Wskaźnik do maksymalnego wieku zasobu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="7cd3e-1289">**dane** Zwrócony wskaźnik do daty ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1290">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1290">Return Values</span></span>

- <span data-ttu-id="7cd3e-1291">**NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="7cd3e-1292">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1293">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1293">Allowed From</span></span>

<span data-ttu-id="7cd3e-1294">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1295">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="7cd3e-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="7cd3e-1297">Wysyłanie danych z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1298">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1299">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1299">Description</span></span>

<span data-ttu-id="7cd3e-1300">Ta usługa wysyła dane w dostarczonym pakiecie z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="7cd3e-1301">Jest to zwykle używane do wysyłania danych dynamicznych skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="7cd3e-1302">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego jest odpowiedzialna za wysyłanie całej odpowiedzi w odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="7cd3e-1303">Ponadto procedura wywołania zwrotnego musi zwracać stan NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1304">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1304">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1305">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1306">**data_ptr** Wskaźnik do danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="7cd3e-1307">**data_length** Liczba bajtów do wysłania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1308">Return Values</span></span>

- <span data-ttu-id="7cd3e-1309">**NX_SUCCESS** (0x00) Pomyślnie wysłano dane serwera</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="7cd3e-1310">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1311">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1311">Allowed From</span></span>

<span data-ttu-id="7cd3e-1312">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1313">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1313">Example</span></span>

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

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="7cd3e-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="7cd3e-1315">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1316">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1317">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1317">Description</span></span>

<span data-ttu-id="7cd3e-1318">Ta usługa jest używana w procedury wywołania zwrotnego serwera HTTP(S) (zdefiniowanej przez aplikację) do generowania nagłówka odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="7cd3e-1319">Procedura wywołania zwrotnego serwera jest wywoływana, gdy serwer HTTP odpowiada na żądania GET, PUT i DELETE klienta, które wymagają odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="7cd3e-1320">Ta funkcja pobiera informacje o odpowiedzi z aplikacji i generuje odpowiedni nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="7cd3e-1321">Zobacz temat service *nx_web_http_server_create(),* aby uzyskać więcej informacji na temat procedury wywołania zwrotnego żądania serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="7cd3e-1322">Ten interfejs API jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1322">This API is deprecated.</span></span> <span data-ttu-id="7cd3e-1323">Zachęcamy deweloperów do korzystania *z nx_web_http_server_callback_generate_response_header_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1324">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1324">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1325">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1326">**packet_pptr** Wskaźnik wskaźnika pakietu przydzielonego do komunikatu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="7cd3e-1327">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="7cd3e-1328">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1328">Examples:</span></span>
  - <span data-ttu-id="7cd3e-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="7cd3e-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="7cd3e-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="7cd3e-1332">**content_length** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="7cd3e-1333">**content_type** Typ protokołu HTTP, np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="7cd3e-1334">**additional_header** Wskaźnik do dodatkowego tekstu nagłówka</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1335">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1335">Return Values</span></span>

- <span data-ttu-id="7cd3e-1336">**NX_SUCCESS** (0x00) Pomyślnie utworzono nagłówek HTML</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="7cd3e-1337">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1338">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1338">Allowed From</span></span>

<span data-ttu-id="7cd3e-1339">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1340">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1340">Example</span></span>

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

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="7cd3e-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="7cd3e-1342">Tworzenie nagłówka odpowiedzi w funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1343">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1343">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-1344">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1344">Description</span></span>

<span data-ttu-id="7cd3e-1345">Ta usługa jest używana w procedury wywołania zwrotnego serwera HTTP(S) (zdefiniowanej przez aplikację) do generowania nagłówka odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="7cd3e-1346">Procedura wywołania zwrotnego serwera jest wywoływana, gdy serwer HTTP odpowiada na żądania GET, PUT i DELETE klienta, które wymagają odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="7cd3e-1347">Ta funkcja pobiera informacje o odpowiedzi z aplikacji i generuje odpowiedni nagłówek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="7cd3e-1348">Zobacz temat service *nx_web_http_server_create(),* aby uzyskać więcej informacji na temat procedury wywołania zwrotnego żądania serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1349">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1349">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1350">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1351">**packet_pptr** Wskaźnik wskaźnika pakietu przydzielonego do komunikatu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="7cd3e-1352">**status_code** Wskazuje stan zasobu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="7cd3e-1353">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1353">Examples:</span></span>
  - <span data-ttu-id="7cd3e-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="7cd3e-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="7cd3e-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="7cd3e-1357">**status_code_length** Długość ciągu kodu stanu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="7cd3e-1358">**content_length** Rozmiar zawartości w bajtach</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="7cd3e-1359">**content_type** Typ protokołu HTTP, np. "tekst/zwykły"</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="7cd3e-1360">**content_type_length** Długość ciągu typu zawartości</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="7cd3e-1361">**additional_header** Wskaźnik do dodatkowego tekstu nagłówka</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="7cd3e-1362">**additional_header_length** Długość dodatkowego tekstu nagłówka</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1363">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1363">Return Values</span></span>

- <span data-ttu-id="7cd3e-1364">**NX_SUCCESS** (0x00) Pomyślnie utworzono nagłówek HTML</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="7cd3e-1365">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1366">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1366">Allowed From</span></span>

<span data-ttu-id="7cd3e-1367">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1368">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1368">Example</span></span>

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

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="7cd3e-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="7cd3e-1370">Wysyłanie pakietu HTTP z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1371">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1372">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1372">Description</span></span>

<span data-ttu-id="7cd3e-1373">Ta usługa wysyła pełną odpowiedź serwera HTTP z wywołania zwrotnego HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="7cd3e-1374">Serwer HTTP wyśle pakiet z NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="7cd3e-1375">Do pakietu należy dołączyć nagłówek HTTP i dane.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="7cd3e-1376">Jeśli stan zwracany wskazuje błąd, aplikacja HTTP musi zwolnić pakiet.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="7cd3e-1377">Wywołanie zwrotne powinno zwrócić NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="7cd3e-1378">Zobacz *nx_web_http_server_callback_generate_response_header(),* aby uzyskać bardziej szczegółowy przykład.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1379">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1379">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1380">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="7cd3e-1381">**packet_ptr** Wskaźnik do pakietu do wysłania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1382">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1382">Return Values</span></span>

- <span data-ttu-id="7cd3e-1383">**NX_SUCCESS** (0x00) Pomyślnie wysłano pakiet serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="7cd3e-1384">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1385">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1385">Allowed From</span></span>

<span data-ttu-id="7cd3e-1386">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1387">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1387">Example</span></span>

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

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="7cd3e-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="7cd3e-1389">Wysyłanie odpowiedzi z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1390">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1391">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1391">Description</span></span>

<span data-ttu-id="7cd3e-1392">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="7cd3e-1393">Jest to zazwyczaj używane do wysyłania odpowiedzi niestandardowych skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="7cd3e-1394">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwracać stan NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="7cd3e-1395">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1395">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-1396">Zachęcamy deweloperów do korzystania *z nx_web_http_server_callback_response_send_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1397">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1397">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1398">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1399">**nagłówek** Wskaźnik do ciągu nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="7cd3e-1400">**informacje o** Wskaźnik do ciągu informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="7cd3e-1401">**additional_info** Wskaźnik do dodatkowego ciągu informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1402">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1402">Return Values</span></span>

- <span data-ttu-id="7cd3e-1403">**NX_SUCCESS** (0x00) Pomyślnie wysłano odpowiedź serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1404">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1404">Allowed From</span></span>

<span data-ttu-id="7cd3e-1405">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1406">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1406">Example</span></span>

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

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="7cd3e-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="7cd3e-1408">Wysyłanie odpowiedzi z funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1409">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1410">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1410">Description</span></span>

<span data-ttu-id="7cd3e-1411">Ta usługa wysyła informacje o podanej odpowiedzi z procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="7cd3e-1412">Jest to zazwyczaj używane do wysyłania odpowiedzi niestandardowych skojarzonych z żądaniami GET/POST.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="7cd3e-1413">Należy pamiętać, że jeśli ta funkcja jest używana, procedura wywołania zwrotnego musi zwracać stan NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="7cd3e-1414">Ciągi nagłówka, informacji i additional_info muszą być zakończone wartością NULL, a długość każdego ciągu odpowiada długości określonej na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="7cd3e-1415">Ta usługa zastępuje *nx_web_http_server_callback_response_send*().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="7cd3e-1416">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1417">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1417">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1418">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1419">**nagłówek** Wskaźnik do ciągu nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="7cd3e-1420">**header_length** Długość ciągu nagłówka odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="7cd3e-1421">**informacje o** Wskaźnik do ciągu informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="7cd3e-1422">**Information_length** Długość ciągu informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="7cd3e-1423">**additional_info** Wskaźnik do dodatkowego ciągu informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="7cd3e-1424">**additional_info_length** Długość dodatkowego ciągu informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1425">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1425">Return Values</span></span>

- <span data-ttu-id="7cd3e-1426">**NX_SUCCESS** (0x00) Pomyślnie wysłano odpowiedź serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1427">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1427">Allowed From</span></span>

<span data-ttu-id="7cd3e-1428">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1429">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1429">Example</span></span>

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

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="7cd3e-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="7cd3e-1431">Pobierz zawartość z żądania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1432">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1433">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1433">Description</span></span>

<span data-ttu-id="7cd3e-1434">Ta usługa próbuje pobrać określoną ilość zawartości z żądania KLIENTA HTTP POST lub PUT.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="7cd3e-1435">Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1436">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1436">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1437">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1438">**packet_ptr** Wskaźnik do pakietu żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="7cd3e-1439">Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="7cd3e-1440">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="7cd3e-1441">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="7cd3e-1442">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="7cd3e-1443">**actual_size** Wskaźnik do zmiennej docelowej, która zostanie ustawiona na rzeczywisty rozmiar kopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1444">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1444">Return Values</span></span>

- <span data-ttu-id="7cd3e-1445">**NX_SUCCESS** (0x00) Pomyślna zawartość serwera HTTP Get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="7cd3e-1446">**NX_WEB_HTTP_ERROR** (0x30000) błąd wewnętrzny serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="7cd3e-1447">**NX_WEB_HTTP_DATA_END** (0x30007) Koniec żądania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="7cd3e-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) serwera HTTP podczas uzyskiwania następnego pakietu zawartości</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="7cd3e-1449">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1450">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1451">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1451">Allowed From</span></span>

<span data-ttu-id="7cd3e-1452">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1453">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="7cd3e-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="7cd3e-1455">Pobierz zawartość z żądania/obsługuje długość zawartości o zerowej długości</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1456">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1457">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1457">Description</span></span>

<span data-ttu-id="7cd3e-1458">Ta usługa jest niemal identyczna z *nx_web_http_server_content_get()*; Próbuje pobrać określoną ilość zawartości z żądania POST lub PUT klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="7cd3e-1459">Jednak obsługuje żądania z wartością content length o wartości zero ("puste żądanie") jako prawidłowym żądaniem.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="7cd3e-1460">Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="7cd3e-1461">Ta usługa *zastępuje* nx_web_http_server_content_get ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="7cd3e-1462">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1463">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1463">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1464">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1465">**packet_ptr** Wskaźnik do pakietu żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="7cd3e-1466">Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="7cd3e-1467">**byte_offset** Liczba bajtów do przesunięcia w obszarze zawartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="7cd3e-1468">**destination_ptr** Wskaźnik do obszaru docelowego zawartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="7cd3e-1469">**destination_size** Maksymalna liczba bajtów dostępnych w obszarze docelowym.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="7cd3e-1470">**actual_size** Wskaźnik do zmiennej docelowej, która zostanie ustawiona na rzeczywisty rozmiar kopiowanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1471">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1471">Return Values</span></span>

- <span data-ttu-id="7cd3e-1472">**NX_SUCCESS** (0x00) Pomyślne uzyskiwanie zawartości HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="7cd3e-1473">**NX_WEB_HTTP_ERROR** (0x30000) błąd wewnętrzny serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="7cd3e-1474">**NX_WEB_HTTP_DATA_END** (0x30007) Koniec żądania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="7cd3e-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) serwera HTTP podczas uzyskiwania następnego pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="7cd3e-1476">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1477">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1478">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1478">Allowed From</span></span>

<span data-ttu-id="7cd3e-1479">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1480">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="7cd3e-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="7cd3e-1482">Pobierz długość zawartości w żądaniu/obsługuje długość zawartości o wartości zero</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1483">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1484">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1484">Description</span></span>

<span data-ttu-id="7cd3e-1485">Ta usługa próbuje pobrać długość zawartości HTTP w dostarczonym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="7cd3e-1486">Wartość zwracana wskazuje stan pomyślnego ukończenia, a rzeczywista wartość długości jest zwracana w wskaźniku wejściowym content_length.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="7cd3e-1487">Jeśli nie ma zawartości HTTP/długość zawartości = 0, ta procedura nadal zwraca stan pomyślnego ukończenia, a content_length wejściowy wskaźnik wskazuje prawidłową długość (zero).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="7cd3e-1488">Powinien on być wywoływany z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1489">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1489">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1490">**packet_ptr** Wskaźnik do pakietu żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="7cd3e-1491">Należy pamiętać, że ten pakiet nie może zostać zwolniony przez wywołanie zwrotne powiadamiania o żądaniu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="7cd3e-1492">**content_length** Wskaźnik do wartości pobranej z pola Długość zawartości</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1493">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1493">Return Values</span></span>

- <span data-ttu-id="7cd3e-1494">**NX_SUCCESS** (0x00) Pomyślne uzyskiwanie długości zawartości serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="7cd3e-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Nieprawidłowy format nagłówka HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="7cd3e-1496">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1497">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1497">Allowed From</span></span>

<span data-ttu-id="7cd3e-1498">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1499">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="7cd3e-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="7cd3e-1501">Tworzenie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1502">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1502">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-1503">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1503">Description</span></span>

<span data-ttu-id="7cd3e-1504">Ta usługa tworzy wystąpienie serwera HTTP, które jest uruchamiane w kontekście własnego wątku ThreadX.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="7cd3e-1505">Opcjonalne procedury *authentication_check* i *request_notify* wywołania zwrotnego aplikacji zapewniają kontrolę oprogramowania aplikacji nad podstawowymi operacjami serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="7cd3e-1506">Ta usługa służy do tworzenia serwerów HTTP w postaci zwykłego tekstu i serwerów HTTPS zabezpieczonych przy użyciu protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="7cd3e-1507">Aby włączyć protokół HTTPS przy użyciu protokołu TLS, zobacz service *nx_web_http_server_secure_configure()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1508">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1508">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1509">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1510">**http_server_name** Wskaźnik do nazwy serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="7cd3e-1511">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7cd3e-1512">**server_port** Port nasłuchiwania TCP dla wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="7cd3e-1513">**media_ptr** Wskaźnik do wcześniej utworzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="7cd3e-1514">**stack_ptr** Wskaźnik do obszaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="7cd3e-1515">**stack_size** Wskaźnik do rozmiaru stosu wątków serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="7cd3e-1516">**authentication_check** Wskaźnik funkcji do procedury sprawdzania uwierzytelniania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="7cd3e-1517">Jeśli zostanie określona, ta procedura jest wywoływana dla każdego żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="7cd3e-1518">Jeśli ten parametr ma wartość NULL, uwierzytelnianie nie będzie przeprowadzane.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="7cd3e-1519">Ten parametr jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1519">This parameter is deprecated.</span></span> <span data-ttu-id="7cd3e-1520">Zamiast *nx_web_http_server_authenticate_check_set* wywołaj nx_web_http_server_authenticate_check_set ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="7cd3e-1521">**request_notify** Wskaźnik funkcji do procedury powiadamiania o żądaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="7cd3e-1522">Jeśli określono, ta procedura jest wywoływana przed przetwarzaniem żądania przez serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="7cd3e-1523">Umożliwia to przekierowywanie nazwy zasobu lub zaktualizowanie pól w zasobie przed ukończeniem żądania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1524">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1524">Return Values</span></span>

- <span data-ttu-id="7cd3e-1525">**NX_SUCCESS** (0x00) Pomyślne utworzenie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="7cd3e-1526">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP, adresu IP, nośnika, stosu lub puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="7cd3e-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Ładunek pakietu puli nie jest wystarczająco duży, aby zawierał kompletne żądanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1528">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1528">Allowed From</span></span>

<span data-ttu-id="7cd3e-1529">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1530">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="7cd3e-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="7cd3e-1532">Usuwanie wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1533">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1534">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1534">Description</span></span>

<span data-ttu-id="7cd3e-1535">Ta usługa usuwa utworzone wcześniej wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1536">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1536">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1537">**http_server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1538">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1538">Return Values</span></span>

- <span data-ttu-id="7cd3e-1539">**NX_SUCCESS** (0x00) Pomyślne usunięcie serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="7cd3e-1540">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="7cd3e-1541">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1542">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1542">Allowed From</span></span>

<span data-ttu-id="7cd3e-1543">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1544">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="7cd3e-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="7cd3e-1546">Pobieranie lokalizacji i długości danych jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1547">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1548">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1548">Description</span></span>

<span data-ttu-id="7cd3e-1549">Ta usługa określa lokalizację początku danych w ramach bieżącej jednostki wieloczęściowej w odebranych komunikatach klienta oraz długość danych, które nie łącznie z ciągiem granicy.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="7cd3e-1550">Wewnętrznie serwer HTTP aktualizuje własne przesunięcia, dzięki czemu ta funkcja może zostać ponownie wywołana na tym samym datagramie klienta dla komunikatów z wieloma jednostkami.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="7cd3e-1551">Wskaźnik pakietów jest aktualizowany do następnego pakietu, w którym komunikat klient jest datagramem z wieloma pakietami.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="7cd3e-1552">Pamiętaj, NX_WEB_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="7cd3e-1553">Należy również zauważyć, że aplikacja nie powinna zwalniać pakietu wskazywanego przez packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="7cd3e-1554">Jest to wykonywane wewnętrznie przez serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="7cd3e-1555">Aby uzyskać nx_web_http_server_get_entity_header, zobacz *nx_web_http_server_get_entity_header().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1556">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1556">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1557">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="7cd3e-1558">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="7cd3e-1559">Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="7cd3e-1560">**available_offset** Wskaźnik do przesunięcia danych jednostki od wskaźnika dołączania pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="7cd3e-1561">**available_length** Wskaźnik do długości danych jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1562">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1562">Return Values</span></span>

- <span data-ttu-id="7cd3e-1563">**NX_SUCCESS** (0x00) Pomyślnie pobrano rozmiar i lokalizację zawartości jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="7cd3e-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Zawartość dla wewnętrznych znaczników wieloczęściowych serwera HTTP jest już znaleziona</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="7cd3e-1565">NX_WEB_HTTP_ERROR (0x30000) błąd wewnętrzny serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="7cd3e-1566">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1567">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1567">Allowed From</span></span>

<span data-ttu-id="7cd3e-1568">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1569">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1569">Example</span></span>

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

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="7cd3e-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="7cd3e-1571">Pobieranie zawartości nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1572">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1573">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1573">Description</span></span>

<span data-ttu-id="7cd3e-1574">Ta usługa pobiera nagłówek jednostki do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="7cd3e-1575">Wewnętrznie serwer HTTP aktualizuje własne wskaźniki, aby zlokalizować następną jednostkę wieloczęściową w datagramie klienta z wieloma nagłówkami jednostek.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="7cd3e-1576">Wskaźnik pakietów jest aktualizowany do następnego pakietu, w którym komunikat klient jest datagramem z wieloma pakietami.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="7cd3e-1577">Pamiętaj, NX_WEB_HTTP_MULTIPART_ENABLE musi być włączona, aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="7cd3e-1578">Należy również zauważyć, że aplikacja nie powinna zwalniać pakietu wskazywanego przez packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1579">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1579">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1580">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="7cd3e-1581">**packet_pptr** Wskaźnik do lokalizacji wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="7cd3e-1582">Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="7cd3e-1583">**entity_header_buffer** Wskaźnik do lokalizacji do przechowywania nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="7cd3e-1584">**buffer_size** Rozmiar buforu wejściowego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1585">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1585">Return Values</span></span>

- <span data-ttu-id="7cd3e-1586">**NX_SUCCESS** (0x00) Pomyślnie pobrano nagłówek jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="7cd3e-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Nie znaleziono pola nagłówka jednostki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="7cd3e-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Upłynął czas odbierania następnego pakietu dla komunikatu klienta pakietu wielopakietowego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="7cd3e-1589">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1590">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="7cd3e-1591">NX_WEB_HTTP_ERROR (0x30000) Wewnętrzny błąd HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1592">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1592">Allowed From</span></span>

<span data-ttu-id="7cd3e-1593">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1594">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1594">Example</span></span>

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

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="7cd3e-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="7cd3e-1596">Ustawianie wywołania zwrotnego w celu uzyskania daty i godziny GMT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1597">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1598">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1598">Description</span></span>

<span data-ttu-id="7cd3e-1599">Ta usługa ustawia wywołanie zwrotne w celu uzyskania daty i godziny GMT na wcześniej utworzonym serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="7cd3e-1600">Ta usługa jest wywoływana, gdy serwer HTTP tworzy nagłówek w odpowiedziach serwera HTTP na klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1601">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1601">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1602">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="7cd3e-1603">**gmt_get** Wskaźnik do wywołania zwrotnego GMT</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="7cd3e-1604">**data** Wskaźnik do pobranej daty</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1605">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1605">Return Values</span></span>

- <span data-ttu-id="7cd3e-1606">**NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="7cd3e-1607">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik pakietu lub parametru.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1608">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1608">Allowed From</span></span>

<span data-ttu-id="7cd3e-1609">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1610">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1610">Example</span></span>

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

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="7cd3e-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="7cd3e-1612">Ustawianie wywołania zwrotnego do obsługi nieprawidłowego użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1613">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="7cd3e-1614">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1614">Description</span></span>

<span data-ttu-id="7cd3e-1615">Ta usługa ustawia wywołanie zwrotne wywoływane po otrzymaniu nieprawidłowej nazwy użytkownika i hasła w żądaniu get, put lub delete klienta za pomocą uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="7cd3e-1616">Serwer HTTP musi zostać utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1617">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1617">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1618">**server_ptr** Wskaźnik do serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="7cd3e-1619">**invalid_username_password_callback** Wskaźnik do nieprawidłowego użytkownika/wywołania zwrotnego przebiegu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="7cd3e-1620">**zasób** Wskaźnik do zasobu określonego przez klienta</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="7cd3e-1621">**client_address** Adres klienta</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1621">**client_address** Client address</span></span>
- <span data-ttu-id="7cd3e-1622">**request_type** Wskazuje typ żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="7cd3e-1623">Może:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1623">May be:</span></span>
  - <span data-ttu-id="7cd3e-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="7cd3e-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="7cd3e-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1627">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1627">Return Values</span></span>

- <span data-ttu-id="7cd3e-1628">**NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="7cd3e-1629">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1630">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1630">Allowed From</span></span>

<span data-ttu-id="7cd3e-1631">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1632">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1632">Example</span></span>

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

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="7cd3e-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="7cd3e-1634">Ustawianie dodatkowych map MIME dla języka HTML</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1635">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1636">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1636">Description</span></span>

<span data-ttu-id="7cd3e-1637">Ta usługa umożliwia deweloperowi aplikacji HTTP dodawanie dodatkowych typów MIME z domyślnych typów MIME dostarczonych przez internetowy serwer HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="7cd3e-1638">Zobacz *nx_web_http_server_get_type(),* aby uzyskać listę zdefiniowanych typów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="7cd3e-1639">Po otrzymaniu żądania klienta, np. żądania GET, serwer HTTP analizuje żądany typ pliku z nagłówka HTTP przy użyciu dodatkowego zestawu map MIME. Jeśli nie zostanie znalezione dopasowanie, szuka dopasowania w domyślnej mapie MIME serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="7cd3e-1640">Jeśli dopasowanie nie zostanie znalezione, typ MIME domyślnie będzie miał wartość "tekst/zwykły".</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="7cd3e-1641">Jeśli funkcja powiadamiania o żądaniu jest zarejestrowana na serwerze HTTP, wywołanie zwrotne powiadomienia żądania może wywołać funkcję *nx_web_http_server_type_get_extended()* w celu analizowania typu pliku.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1642">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1642">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1643">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="7cd3e-1644">**mime_maps** Wskaźnik do tablicy map MIME</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="7cd3e-1645">**mime_map_num** Liczba map MIME w tablicy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1646">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1646">Return Values</span></span>

- <span data-ttu-id="7cd3e-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set (Zestaw map MIME pomyślnego serwera HTTP)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="7cd3e-1648">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1649">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1649">Allowed From</span></span>

<span data-ttu-id="7cd3e-1650">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1651">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1651">Example</span></span>

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

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="7cd3e-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="7cd3e-1653">Przydzielanie pakietu HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1654">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1655">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1655">Description</span></span>

<span data-ttu-id="7cd3e-1656">Ta usługa próbuje przydzielić pakiet dla serwera HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="7cd3e-1657">Należy pamiętać, że jeśli kolejny interfejs API netx lub interfejs API serwera HTTP używający tego pakietu jako danych wejściowych zakończy się **niepowodzeniem,** na przykład nx_packet_data_append lub \*\*nx_web_http_server_callback_packet_send, aplikacja jest odpowiedzialna za zwolnienie pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1658">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1658">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1659">**server_ptr** Wskaźnik do bloku sterowania serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="7cd3e-1660">**packet_ptr** Wskaźnik do przydzielonego pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="7cd3e-1661">**wait_option** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="7cd3e-1662">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="7cd3e-1663">**NX_NO_WAIT** (0x00000000) Wybranie NX_NO_WAIT powoduje natychmiastowe zwrócenie wątku wywołującego, jeśli żądanie nie może zostać spełnione.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="7cd3e-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Wybranie NX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer HTTP nie odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="7cd3e-1665">**wartość** limitu czasu (od 0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (0x1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1666">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1666">Return Values</span></span>

- <span data-ttu-id="7cd3e-1667">**NX_SUCCESS** (0x00) Pomyślne przydzielenie pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="7cd3e-1668">**NX_NO_PACKET** (0x01) Brak dostępnych pakietów</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="7cd3e-1669">**NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort *.*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="7cd3e-1670">**NX_INVALID_PARAMETERS** (0x4D) Rozmiar pakietu nie obsługuje protokołu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="7cd3e-1671">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1672">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1673">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1673">Allowed From</span></span>

<span data-ttu-id="7cd3e-1674">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1675">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="7cd3e-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="7cd3e-1677">Wyodrębnianie długości zawartości i ustawianie wskaźnika na początek danych</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1678">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1679">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1679">Description</span></span>

<span data-ttu-id="7cd3e-1680">Ta usługa wyodrębnia długość zawartości z nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="7cd3e-1681">Ponadto pakiet jest aktualizowany w następujący sposób: dołączony wskaźnik pakietu (początek lokalizacji buforu pakietów do zapisu) jest ustawiony na zawartość HTTP (dane) przekazaną właśnie nagłówkiem HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="7cd3e-1682">Jeśli początek zawartości nie zostanie znaleziony w bieżącym pakiecie, funkcja czeka na otrzymanie następnego pakietu przy użyciu NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="7cd3e-1683">Należy pamiętać, że nie należy go wywoływania przed wywołaniem *nx_web_http_server_get_entity_header(),* ponieważ modyfikuje on wskaźnik dołączany przez pakiet obok nagłówka jednostki.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1684">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1684">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1685">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="7cd3e-1686">**packet_ptr** Wskaźnik do wskaźnika pakietu do zwracania pakietu ze zaktualizowanym wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="7cd3e-1687">**content_length** Wskaźnik do wyodrębnianych content_length</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1688">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1688">Return Values</span></span>

- <span data-ttu-id="7cd3e-1689">**NX_SUCCESS** (0x00) znaleziono długość zawartości HTTP i pomyślnie zaktualizowano pakiet</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="7cd3e-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Czas wygaśnięcia oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="7cd3e-1691">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1692">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1692">Allowed From</span></span>

<span data-ttu-id="7cd3e-1693">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1694">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1694">Example</span></span>

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

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="7cd3e-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="7cd3e-1696">Odbieranie następnego pakietu HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1697">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1698">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1698">Description</span></span>

<span data-ttu-id="7cd3e-1699">Ta usługa zwraca następny pakiet odebrany na gnieździe serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="7cd3e-1700">Opcja oczekiwania na otrzymanie pakietu jest NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="7cd3e-1701">Należy pamiętać, że w przypadku powodzenia aplikacja jest odpowiedzialna za wydanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1702">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1702">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1703">**server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="7cd3e-1704">**packet_ptr** Wskaźnik do odebranego pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1705">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1705">Return Values</span></span>

- <span data-ttu-id="7cd3e-1706">**NX_SUCCESS** (0x00) Pomyślnie odebrano następny pakiet HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="7cd3e-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Czas wygaśnięcia oczekiwania na następny pakiet</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="7cd3e-1708">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1709">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1709">Allowed From</span></span>

<span data-ttu-id="7cd3e-1710">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1711">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="7cd3e-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="7cd3e-1713">Pobierz parametr z żądania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1714">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1715">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1715">Description</span></span>

<span data-ttu-id="7cd3e-1716">Ta usługa próbuje pobrać określony parametr adresu URL HTTP w podanym pakiecie żądań.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="7cd3e-1717">Jeśli żądany parametr HTTP nie istnieje, ta procedura zwraca stan NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="7cd3e-1718">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1719">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1719">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1720">**packet_ptr** Wskaźnik do pakietu żądań klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="7cd3e-1721">Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="7cd3e-1722">**param_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="7cd3e-1723">**param_ptr** Obszar docelowy do skopiowania parametru.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="7cd3e-1724">**param_size** Zwróć łączną długość danych parametru (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="7cd3e-1725">**max_param_size** Maksymalny rozmiar obszaru docelowego parametru.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1726">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1726">Return Values</span></span>

- <span data-ttu-id="7cd3e-1727">**NX_SUCCESS** (0x00) Pomyślne uzyskiwanie parametru serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="7cd3e-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Nie znaleziono określonego parametru</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="7cd3e-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated (Parametr żądania NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM (0x30015) nie został prawidłowo zakończony</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="7cd3e-1730">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1731">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1732">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1732">Allowed From</span></span>

<span data-ttu-id="7cd3e-1733">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1734">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="7cd3e-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="7cd3e-1736">Uzyskiwanie zapytania z żądania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1737">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1738">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1738">Description</span></span>

<span data-ttu-id="7cd3e-1739">Ta usługa próbuje pobrać określone zapytanie adresu URL HTTP w podanym pakiecie żądania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="7cd3e-1740">Jeśli żądane zapytanie HTTP nie istnieje, ta procedura zwraca stan NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="7cd3e-1741">Ta procedura powinna być wywoływana z wywołania zwrotnego powiadomienia aplikacji określonego podczas tworzenia serwera HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1742">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1742">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1743">**packet_ptr** Wskaźnik do pakietu żądań klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="7cd3e-1744">Należy pamiętać, że aplikacja nie powinna zwalniać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="7cd3e-1745">**query_number** Numer logiczny parametru zaczynający się od zera, od lewej do prawej na liście zapytań.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="7cd3e-1746">**query_ptr** Obszar docelowy do skopiowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="7cd3e-1747">**query_size** Zwraca rozmiar danych zapytania (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="7cd3e-1748">**max_query_size** Maksymalny rozmiar miejsca docelowego zapytania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="7cd3e-1749">Obszar.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1750">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1750">Return Values</span></span>

- <span data-ttu-id="7cd3e-1751">**NX_SUCCESS** (0x00) Uzyskiwanie pomyślnego zapytania serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="7cd3e-1752">**NX_WEB_HTTP_FAILED** (0x30002) Rozmiar zapytania jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="7cd3e-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Nie znaleziono określonego zapytania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="7cd3e-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) Brak zapytania w żądaniu klienta</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="7cd3e-1755">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1756">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1757">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1757">Allowed From</span></span>

<span data-ttu-id="7cd3e-1758">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1759">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="7cd3e-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="7cd3e-1761">Ustawianie fragmentowego transferu dla odpowiedzi HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1762">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1763">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1763">Description</span></span>

<span data-ttu-id="7cd3e-1764">Ta usługa używa fragmentatywnego kodowania transferu do wysyłania niestandardowego pakietu danych odpowiedzi HTTP(S) utworzonego za *pomocą nx_web_http_server_response_packet_allocate*() do klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1765">Jeśli aplikacja używa fragmentatywnego kodu transferu do wysyłania pakietu danych odpowiedzi, musi wywołać tę usługę po wywołaniu nx_web_http_server_response_packet_allocate *()* i przed wywołaniem nx_web_http_server_callback_packet_send *().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1766">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1766">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1767">**client_ptr** Wskaźnik do bloku sterowania klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="7cd3e-1768">**chunk_size** Rozmiar danych fragmentów w oktetach.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="7cd3e-1769">**packet_ptr** Wskaźnik pakietów danych żądań HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1770">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1770">Return Values</span></span>

- <span data-ttu-id="7cd3e-1771">**NX_SUCCESS** (0x00) Zestaw pomyślny jest fragmentowany.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="7cd3e-1772">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1773">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1773">Allowed From</span></span>

<span data-ttu-id="7cd3e-1774">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1775">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="7cd3e-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="7cd3e-1777">Konfigurowanie serwera HTTP do używania protokołu TLS na użytek bezpiecznego protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1778">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1778">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-1779">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1779">Description</span></span>

<span data-ttu-id="7cd3e-1780">Ta usługa konfiguruje wcześniej utworzone wystąpienie internetowego serwera HTTP NetX w celu używania protokołu TLS do bezpiecznej komunikacji HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="7cd3e-1781">Parametry służą do konfigurowania wszystkich możliwych sesji protokołu TLS z identycznym stanem, tak aby każdy przychodzący klient HTTPS zapewniał spójne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="7cd3e-1782">Liczba sesji TLS jest kontrolowana przy użyciu makra NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="7cd3e-1783">Tabela procedur kryptograficznych (ciphersuite table) jest współdzielona między wszystkimi sesjami TLS, ponieważ zawiera tylko wskaźniki funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="7cd3e-1784">Bufory ponownego zsyłania pakietów i metadanych są równomiernie dzielone między wszystkie sesje protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="7cd3e-1785">Jeśli rozmiar buforu nie jest równomiernie podzielny przez liczbę sesji, reszta będzie nieużywana.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="7cd3e-1786">Przekazany certyfikat tożsamości jest używany przez wszystkie sesje.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="7cd3e-1787">Podczas operacji TLS certyfikat tożsamości serwera jest odczytywany tylko z , dlatego kopie nie są potrzebne dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="7cd3e-1788">Zaufane certyfikaty są dodawane do każdej sesji protokołu TLS na serwerze HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="7cd3e-1789">Są one używane do uwierzytelniania certyfikatu klienta, które jest automatycznie włączane po podano zdalne miejsce na certyfikat.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="7cd3e-1790">Macierz i bufor certyfikatów zdalnych są domyślnie współużytowane przez wszystkie sesje TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="7cd3e-1791">Certyfikaty zdalne są używane do uwierzytelniania certyfikatu klienta, który jest automatycznie włączany, gdy liczba certyfikatów zdalnych jest niezerowa.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="7cd3e-1792">Ze względu na to, że bufor jest udostępniany, niektóre sesje mogą zostać zablokowane podczas walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="7cd3e-1793">Aby wyłączyć uwierzytelnianie certyfikatu klienta, NX_NULL dla remote_certificates i wartość 0 dla parametru remote_certs_num.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="7cd3e-1794">Wartości zwracane będą zawierać kody błędów TLS wynikające z problemów z konfiguracją sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1795">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1795">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1796">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="7cd3e-1797">**crypto_table** Wskaźnik do tabeli szyfrowania TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="7cd3e-1798">**metadata_buffer** Wskaźnik do buforu metadanych kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="7cd3e-1799">**metadata_size** Rozmiar buforu metadanych kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="7cd3e-1800">**packet_buffer** Bufor ponownego zassembly pakietów TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="7cd3e-1801">**packet_buffer** Rozmiar buforu pakietów TLS — powinien być równy (<rozmiar buforu TLS\* NX_WEB_HTTP_SESSION_MAX).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="7cd3e-1802">**identity_certificate** Certyfikat tożsamości serwera TLS — będzie używany dla wszystkich sesji serwera HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="7cd3e-1803">**trusted_certificates** Wskaźnik do tablicy obiektów NX_SECURE_X509_CERT, używany do weryfikowania przychodzących certyfikatów klienta, jeśli uwierzytelnianie certyfikatu klienta jest włączone, przekazując wartość niezerową dla *parametru remote_certs_num* klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="7cd3e-1804">**trusted_certs_num** Liczba zaufanych certyfikatów  w trusted_certificates tablicy.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="7cd3e-1805">**remote_certificates** Wskaźnik do tablicy obiektów NX_SECURE_X509_CERT, używany dla przychodzących certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="7cd3e-1806">**remote_certs_num** Liczba certyfikatów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="7cd3e-1807">Powinna to być maksymalna liczba oczekiwanych certyfikatów od klientów.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="7cd3e-1808">Uwierzytelnianie certyfikatu klienta jest włączane automatycznie, gdy jest to wartość niezerowa.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="7cd3e-1809">**remote_certificate_buffer** Bufor do zawierania przychodzących certyfikatów zdalnych od klientów, jeśli jest włączone uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="7cd3e-1810">remote_cert_buffer_size rozmiar buforu certyfikatów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="7cd3e-1811">Powinna być równa (<maksymalny oczekiwany rozmiar certyfikatu \* remote_certs_num).</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="7cd3e-1812">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1812">Return Values</span></span>

- <span data-ttu-id="7cd3e-1813">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7cd3e-1814">**NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7cd3e-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Odebrany typ komunikatu TLS jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="7cd3e-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="7cd3e-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) przetwarzanie komunikatów podczas uściśniania TLS nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="7cd3e-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Sprawdzanie skrótu mac komunikatu przychodzącego nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="7cd3e-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Nie można wysłać bazowego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="7cd3e-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Komunikat przychodzący miał pole o nieprawidłowej długości.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="7cd3e-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) Przychodzący komunikat ChangeCipherSpec był niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="7cd3e-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) Przychodzący certyfikat TLS nie można zidentyfikować zdalnego serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="7cd3e-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Szyfr klucza publicznego dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="7cd3e-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Host zdalny nie zaznaczył żadnych szyfrów obsługiwanych przez stos bezpiecznego szyfrowania TLS netx.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="7cd3e-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat TLS miał w nagłówku nieznaną wersję TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="7cd3e-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Odebrany komunikat TLS miał w nagłówku znaną, ale nieobsługiwaną wersję TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="7cd3e-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Nie powiodło się wewnętrzne przydzielanie pakietów protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="7cd3e-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Host zdalny podał nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="7cd3e-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="7cd3e-1830">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1831">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1831">Allowed From</span></span>

<span data-ttu-id="7cd3e-1832">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1833">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1833">Example</span></span>

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

## <a name="nx_web_http_server_start"></a><span data-ttu-id="7cd3e-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="7cd3e-1835">Uruchamianie serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1836">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1837">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1837">Description</span></span>

<span data-ttu-id="7cd3e-1838">Ta usługa uruchamia utworzone wcześniej wystąpienie serwera HTTP lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="7cd3e-1839">Serwery HTTPS mają ten sam interfejs API co protokół HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="7cd3e-1840">Aby włączyć protokół HTTPS przy użyciu protokołu TLS na serwerze HTTP, zobacz temat service *nx_web_http_server_secure_configure().*</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1841">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1841">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1842">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1843">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1843">Return Values</span></span>

- <span data-ttu-id="7cd3e-1844">**NX_SUCCESS** (0x00) Pomyślne uruchomienie serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="7cd3e-1845">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1846">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1846">Allowed From</span></span>

<span data-ttu-id="7cd3e-1847">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1848">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="7cd3e-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="7cd3e-1850">Zatrzymywanie serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1851">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1852">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1852">Description</span></span>

<span data-ttu-id="7cd3e-1853">Ta usługa zatrzymuje wcześniej utworzyć wystąpienie serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="7cd3e-1854">Ta procedura powinna zostać wywołana przed usunięciem wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1855">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1855">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1856">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1857">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1857">Return Values</span></span>

- <span data-ttu-id="7cd3e-1858">**NX_SUCCESS** (0x00) Pomyślne zatrzymanie serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="7cd3e-1859">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1860">NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1861">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1861">Allowed From</span></span>

<span data-ttu-id="7cd3e-1862">Wątki</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1863">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="7cd3e-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="7cd3e-1865">Wyodrębnianie typu pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1866">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1867">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="7cd3e-1868">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1868">This service is deprecated.</span></span> <span data-ttu-id="7cd3e-1869">Zachęcamy użytkowników do korzystania z usługi *nx_web_http_server_type_get_extended()*.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="7cd3e-1870">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w string_size *z* nazwy buforu wejściowego *,* zazwyczaj adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="7cd3e-1871">Jeśli mapa MIME nie zostanie znaleziona, domyślnie jest to typ "tekst/zwykły".</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="7cd3e-1872">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="7cd3e-1873">Domyślne mapy MIME na serwerze HTTP sieci Web NetX to:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="7cd3e-1874">html text/html</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1874">html text/html</span></span>
- <span data-ttu-id="7cd3e-1875">htm text/html</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1875">htm text/html</span></span>
- <span data-ttu-id="7cd3e-1876">tekst txt/zwykły</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1876">txt text/plain</span></span>
- <span data-ttu-id="7cd3e-1877">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1877">gif image/gif</span></span>
- <span data-ttu-id="7cd3e-1878">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="7cd3e-1879">obraz ico/ikona x</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1879">ico image/x-icon</span></span>

<span data-ttu-id="7cd3e-1880">Jeśli zostanie podany, przeszukuje również zdefiniowany przez użytkownika zestaw dodatkowych map MIME.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="7cd3e-1881">Zobacz *nx_web_http_server_mime_maps_addtional_set(),* aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1882">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1882">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1883">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="7cd3e-1884">**name (nazwa)** Wskaźnik do buforu do wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="7cd3e-1885">**http_type_string** Wskaźnik do wyodrębnianych ciągów typów HTML</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="7cd3e-1886">**string_size** Wskaźnik zwracania długości ciągu wyodrębnianych typów HTML.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1887">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1887">Return Values</span></span>

- <span data-ttu-id="7cd3e-1888">**NX_SUCCESS** (0x00) Pomyślne wyodrębnianie typu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="7cd3e-1889">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Zwracany jest domyślny tekst/zwykły.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1891">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1891">Allowed From</span></span>

<span data-ttu-id="7cd3e-1892">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1893">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1893">Example</span></span>

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

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="7cd3e-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="7cd3e-1895">Wyodrębnianie typu pliku z żądania HTTP klienta</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1896">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="7cd3e-1897">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1897">Description</span></span>

<span data-ttu-id="7cd3e-1898">Ta usługa wyodrębnia typ żądania HTTP w buforze *http_type_string* i jego długość w string_size *z* nazwy buforu wejściowego *,* zazwyczaj adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="7cd3e-1899">Jeśli mapa MIME nie zostanie znaleziona, domyślnie jest to typ "tekst/zwykły".</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="7cd3e-1900">W przeciwnym razie porównuje wyodrębniony typ z domyślnymi mapami MIME serwera HTTP dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="7cd3e-1901">Domyślne mapy MIME na serwerze HTTP sieci Web NetX to:</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="7cd3e-1902">html text/html</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1902">html text/html</span></span>
- <span data-ttu-id="7cd3e-1903">htm text/html</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1903">htm text/html</span></span>
- <span data-ttu-id="7cd3e-1904">tekst txt/zwykły</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1904">txt text/plain</span></span>
- <span data-ttu-id="7cd3e-1905">obraz gif/gif</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1905">gif image/gif</span></span>
- <span data-ttu-id="7cd3e-1906">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="7cd3e-1907">obraz ico/ikona x</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1907">ico image/x-icon</span></span>

<span data-ttu-id="7cd3e-1908">Jeśli zostanie podany, przeszukuje również zdefiniowany przez użytkownika zestaw dodatkowych map MIME.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="7cd3e-1909">Zobacz *nx_web_http_server_mime_maps_addtional_set(),* aby uzyskać więcej informacji na temat map zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="7cd3e-1910">Ta usługa *zastępuje* nx_web_http_server_type_get ().</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="7cd3e-1911">Ta wersja wymaga, aby wywołujący podali informacje o długości funkcji.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1912">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1912">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1913">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="7cd3e-1914">**name (nazwa)** Wskaźnik do buforu do wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="7cd3e-1915">**name_length** Długość nazwy</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="7cd3e-1916">**http_type_string** Wskaźnik do wyodrębnionego ciągu typu HTML</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="7cd3e-1917">**http_type_string_max_size** Rozmiar buforu http_type_string danych</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="7cd3e-1918">**string_size** Wskaźnik zwracania wyodrębnianych ciągów typu HTML</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="7cd3e-1919">Długość.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1920">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1920">Return Values</span></span>

- <span data-ttu-id="7cd3e-1921">**NX_SUCCESS** (0x00) Pomyślne wyodrębnianie typu</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="7cd3e-1922">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Zwracany jest domyślny tekst/zwykły.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1924">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1924">Allowed From</span></span>

<span data-ttu-id="7cd3e-1925">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1926">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1926">Example</span></span>

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

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="7cd3e-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="7cd3e-1928">Ustawianie funkcji wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1929">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1929">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-1930">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1930">Description</span></span>

<span data-ttu-id="7cd3e-1931">Ta usługa ustawia wywołanie zwrotne wywoływane podczas uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1932">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1932">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1933">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="7cd3e-1934">**digest_authenticate_callback** Wskaźnik do uwierzytelniania szyfrowanego wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1935">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1935">Return Values</span></span>

- <span data-ttu-id="7cd3e-1936">**NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="7cd3e-1937">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7cd3e-1938">NX_NOT_SUPPORTED (0x4B) Uwierzytelnianie szyfrowane nie jest włączone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1939">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1939">Allowed From</span></span>

<span data-ttu-id="7cd3e-1940">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1941">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1941">Example</span></span>

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

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="7cd3e-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="7cd3e-1943">Ustawianie funkcji wywołania zwrotnego uwierzytelniania szyfrowanego</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7cd3e-1944">Prototype</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1944">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7cd3e-1945">Opis</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1945">Description</span></span>

<span data-ttu-id="7cd3e-1946">Ta usługa ustawia wywołanie zwrotne wywoływane podczas sprawdzania uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7cd3e-1947">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1947">Input Parameters</span></span>

- <span data-ttu-id="7cd3e-1948">**http_server_ptr** Wskaźnik do wystąpienia serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="7cd3e-1949">**authenticate_check_externded** Wskaźnik do uwierzytelniania wywołania zwrotnego sprawdzania</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="7cd3e-1950">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1950">Return Values</span></span>

- <span data-ttu-id="7cd3e-1951">**NX_SUCCESS** (0x00) Pomyślnie ustawiono wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="7cd3e-1952">NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7cd3e-1953">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1953">Allowed From</span></span>

<span data-ttu-id="7cd3e-1954">Aplikacja</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="7cd3e-1955">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd3e-1955">Example</span></span>

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
