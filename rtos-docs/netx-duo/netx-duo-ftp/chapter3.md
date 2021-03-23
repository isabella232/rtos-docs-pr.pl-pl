---
title: Rozdział 3 — Opis usług FTP
description: Ten rozdział zawiera opis wszystkich usług FTP NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821883"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="c8f73-103">Rozdział 3 — Opis usług FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="c8f73-104">Ten rozdział zawiera opis wszystkich usług FTP NetX (wymienionych poniżej) w porządku alfabetycznym (z wyjątkiem przypadków, gdy równorzędne Protokoły IPv4 i IPv6 są połączone).</span><span class="sxs-lookup"><span data-stu-id="c8f73-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="c8f73-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c8f73-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="c8f73-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="c8f73-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="c8f73-107">Nawiązywanie połączenia z serwerem FTP za pośrednictwem protokołu IPv4</span><span class="sxs-lookup"><span data-stu-id="c8f73-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-109">Description</span></span>

<span data-ttu-id="c8f73-110">Ta usługa nawiązuje połączenie utworzonego wcześniej wystąpienia klienta FTP NetX z serwerem FTP przy użyciu podanego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-111">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-111">Input Parameters</span></span>

- <span data-ttu-id="c8f73-112">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-113">**server_IP** Adres IP serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="c8f73-114">**Nazwa użytkownika** Nazwa użytkownika klienta na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c8f73-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="c8f73-115">**hasło** Hasło klienta na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c8f73-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="c8f73-116">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na połączenie z klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="c8f73-117">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-118">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-119">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-120">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-120">Return Values</span></span>

- <span data-ttu-id="c8f73-121">**NX_SUCCESS** (0X00) POMYŚLNE połączenie FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="c8f73-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) nie otrzymał odpowiedzi 22X (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="c8f73-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) nie otrzymał odpowiedzi 23X (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="c8f73-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) nie otrzymał odpowiedzi 33X (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="c8f73-125">Klient **NX_FTP_NOT_DISCONNECTED** (0xD4) jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="c8f73-126">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c8f73-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="c8f73-127">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="c8f73-128">NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-129">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-129">Allowed From</span></span>

<span data-ttu-id="c8f73-130">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="c8f73-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8f73-132">See Also</span></span>

<span data-ttu-id="c8f73-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="c8f73-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="c8f73-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="c8f73-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="c8f73-135">Nawiązywanie połączenia z serwerem FTP przy użyciu protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="c8f73-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-137">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-137">Description</span></span>

<span data-ttu-id="c8f73-138">Ta usługa nawiązuje połączenie utworzonego wcześniej wystąpienia klienta FTP NetX Duo z serwerem FTP na podanym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="c8f73-139">Obsługiwane są zarówno sieci IPv4, jak i IPv6.</span><span class="sxs-lookup"><span data-stu-id="c8f73-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-140">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-140">Input Parameters</span></span>

- <span data-ttu-id="c8f73-141">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-142">**server_ipduo** Adres IP serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="c8f73-143">**Nazwa użytkownika** Nazwa użytkownika klienta na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c8f73-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="c8f73-144">**hasło** Hasło klienta na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c8f73-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="c8f73-145">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na połączenie z klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="c8f73-146">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-147">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-148">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-149">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-149">Return Values</span></span>

- <span data-ttu-id="c8f73-150">**NX_SUCCESS** (0X00) POMYŚLNE połączenie FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="c8f73-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) nie otrzymał odpowiedzi 22X (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="c8f73-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) nie otrzymał odpowiedzi 23X (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="c8f73-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) nie otrzymał odpowiedzi 33X (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="c8f73-154">Klient **NX_FTP_NOT_DISCONNECTED** (0xD4) jest już połączony</span><span class="sxs-lookup"><span data-stu-id="c8f73-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="c8f73-155">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik Inout.</span><span class="sxs-lookup"><span data-stu-id="c8f73-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="c8f73-156">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="c8f73-157">NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-158">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-158">Allowed From</span></span>

<span data-ttu-id="c8f73-159">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="c8f73-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8f73-161">See Also</span></span>

<span data-ttu-id="c8f73-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="c8f73-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="c8f73-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="c8f73-163">nx_ftp_client_create</span></span>

<span data-ttu-id="c8f73-164">Tworzenie wystąpienia klienta FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-165">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c8f73-166">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-166">Description</span></span>

<span data-ttu-id="c8f73-167">Ta usługa tworzy wystąpienie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-168">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-168">Input Parameters</span></span>

- <span data-ttu-id="c8f73-169">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-170">**ftp_client_name** Nazwa klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="c8f73-171">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="c8f73-172">**window_size** Anonsowany rozmiar okna dla gniazd TCP dla tego klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="c8f73-173">**pool_ptr** Wskaźnik do domyślnej puli pakietów dla tego klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="c8f73-174">Należy pamiętać, że minimalny ładunek pakietu musi być wystarczająco duży, aby pomieścić pełną ścieżkę i nazwę pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-175">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-175">Return Values</span></span>

- <span data-ttu-id="c8f73-176">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="c8f73-177">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c8f73-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-178">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-178">Allowed From</span></span>

<span data-ttu-id="c8f73-179">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-180">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="c8f73-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="c8f73-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="c8f73-182">Usuwanie wystąpienia klienta FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-183">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="c8f73-184">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-184">Description</span></span>

<span data-ttu-id="c8f73-185">Ta usługa usuwa wystąpienie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-186">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-186">Input Parameters</span></span>

- <span data-ttu-id="c8f73-187">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-188">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-188">Return Values</span></span>

- <span data-ttu-id="c8f73-189">**NX_SUCCESS** (0X00) pomyślne usunięcie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="c8f73-190">Klient FTP **NX_FTP_NOT_DISCONNECTED** (0xD4) nie został odłączony</span><span class="sxs-lookup"><span data-stu-id="c8f73-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="c8f73-191">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-192">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-193">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-193">Allowed From</span></span>

<span data-ttu-id="c8f73-194">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="c8f73-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="c8f73-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="c8f73-197">Tworzenie katalogu na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-198">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-199">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-199">Description</span></span>

<span data-ttu-id="c8f73-200">Ta usługa tworzy określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-201">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-201">Input Parameters</span></span>

- <span data-ttu-id="c8f73-202">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-203">**directory_name** Nazwa katalogu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="c8f73-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="c8f73-204">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na utworzenie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="c8f73-205">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-206">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-207">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-208">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-208">Return Values</span></span>

- <span data-ttu-id="c8f73-209">**NX_SUCCESS** (0X00) pomyślne utworzenie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="c8f73-210">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-212">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-213">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-214">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-214">Allowed From</span></span>

<span data-ttu-id="c8f73-215">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="c8f73-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="c8f73-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="c8f73-218">Ustawianie domyślnego katalogu na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-220">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-220">Description</span></span>

<span data-ttu-id="c8f73-221">Ta usługa ustawia domyślny katalog na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="c8f73-222">Ten domyślny katalog ma zastosowanie tylko do połączenia tego klienta.</span><span class="sxs-lookup"><span data-stu-id="c8f73-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-223">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-223">Input Parameters</span></span>

- <span data-ttu-id="c8f73-224">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-225">**directory_path** Nazwa ścieżki katalogu do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c8f73-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="c8f73-226">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na domyślny zestaw katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="c8f73-227">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-228">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-229">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-230">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-230">Return Values</span></span>

- <span data-ttu-id="c8f73-231">**NX_SUCCESS** (0X00) pomyślne ustawienie domyślne FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="c8f73-232">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-234">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-235">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-236">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-236">Allowed From</span></span>

<span data-ttu-id="c8f73-237">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-238">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="c8f73-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="c8f73-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="c8f73-240">Usuwanie katalogu na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-241">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-242">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-242">Description</span></span>

<span data-ttu-id="c8f73-243">Ta usługa usuwa określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-244">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-244">Input Parameters</span></span>

- <span data-ttu-id="c8f73-245">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-246">**directory_name** Nazwa katalogu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="c8f73-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="c8f73-247">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na usunięcie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="c8f73-248">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-249">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-250">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-251">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-251">Return Values</span></span>

- <span data-ttu-id="c8f73-252">**NX_SUCCESS** (0X00) pomyślne usunięcie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="c8f73-253">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-255">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-256">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-257">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-257">Allowed From</span></span>

<span data-ttu-id="c8f73-258">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-259">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="c8f73-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="c8f73-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="c8f73-261">Pobierz listę katalogów z serwera FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-263">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-263">Description</span></span>

<span data-ttu-id="c8f73-264">Ta usługa pobiera zawartość określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="c8f73-265">Dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="c8f73-266">Każdy wpis jest rozdzielony \<cr/lf\> kombinacją.</span><span class="sxs-lookup"><span data-stu-id="c8f73-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="c8f73-267">Należy wywołać ***nx_ftp_client_directory_listing_continue*** , aby ukończyć operację pobierania katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-268">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-268">Input Parameters</span></span>

- <span data-ttu-id="c8f73-269">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-270">**directory_name** Nazwa katalogu, do którego ma zostać pobrana zawartość.</span><span class="sxs-lookup"><span data-stu-id="c8f73-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="c8f73-271">**packet_ptr** Wskaźnik do wskaźnika pakietu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c8f73-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="c8f73-272">Jeśli to się powiedzie, ładunek pakietu będzie zawierać jeden lub więcej wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="c8f73-273">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na listę katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="c8f73-274">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-275">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-276">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-277">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-277">Return Values</span></span>

- <span data-ttu-id="c8f73-278">**NX_SUCCESS** (0x00) pomyślna lista katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="c8f73-279">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-280">Nie włączono usługi **NX_NOT_ENABLED** (IPv6)</span><span class="sxs-lookup"><span data-stu-id="c8f73-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="c8f73-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) nie otrzymał odpowiedzi 1XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="c8f73-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-283">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-284">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-285">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-285">Allowed From</span></span>

<span data-ttu-id="c8f73-286">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-287">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="c8f73-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="c8f73-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="c8f73-289">Kontynuuj Wyświetlanie listy katalogów z serwera FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-291">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-291">Description</span></span>

<span data-ttu-id="c8f73-292">Ta usługa kontynuuje pobieranie zawartości określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="c8f73-293">Powinien być bezpośrednio poprzedzony wywołaniem ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="c8f73-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="c8f73-294">Jeśli to się powiedzie, dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="c8f73-295">Ta procedura powinna być wywoływana do momentu otrzymania NX_FTP_END_OF_LISTING stanu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-296">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-296">Input Parameters</span></span>

- <span data-ttu-id="c8f73-297">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-298">**packet_ptr** Wskaźnik do wskaźnika pakietu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c8f73-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="c8f73-299">Jeśli to się powiedzie, ładunek pakietu będzie zawierać co najmniej jeden wpis w katalogu oddzielony> <CR/LF.</span><span class="sxs-lookup"><span data-stu-id="c8f73-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="c8f73-300">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na listę katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="c8f73-301">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-302">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-303">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-304">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-304">Return Values</span></span>

- <span data-ttu-id="c8f73-305">**NX_SUCCESS** (0x00) pomyślna lista katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="c8f73-306">**NX_FTP_END_OF_LISTING** (0XD8) nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="c8f73-307">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-309">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-310">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-311">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-311">Allowed From</span></span>

<span data-ttu-id="c8f73-312">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-313">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="c8f73-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="c8f73-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="c8f73-315">Rozłącz z serwerem FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-316">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-317">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-317">Description</span></span>

<span data-ttu-id="c8f73-318">Ta usługa rozłącza wcześniej ustanowione połączenie z serwerem FTP z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-319">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-319">Input Parameters</span></span>

- <span data-ttu-id="c8f73-320">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-321">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na rozłączenie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="c8f73-322">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-323">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-324">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-325">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-325">Return Values</span></span>

- <span data-ttu-id="c8f73-326">**NX_SUCCESS** (0X00) pomyślne rozłączenie FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="c8f73-327">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-329">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-330">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-331">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-331">Allowed From</span></span>

<span data-ttu-id="c8f73-332">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-333">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="c8f73-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="c8f73-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="c8f73-335">Zamknij plik klienta</span><span class="sxs-lookup"><span data-stu-id="c8f73-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-336">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-337">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-337">Description</span></span>

<span data-ttu-id="c8f73-338">Ta usługa zamyka poprzednio otwarty plik na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-339">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-339">Input Parameters</span></span>

- <span data-ttu-id="c8f73-340">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-341">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na zamknięcie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="c8f73-342">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-343">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-344">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-345">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-345">Return Values</span></span>

- <span data-ttu-id="c8f73-346">**NX_SUCCESS** (0X00) pomyślne zamknięcie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="c8f73-347">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-348">**NX_FTP_NOT_OPEN (0xD5)** Plik nie jest otwarty; nie można zamknąć</span><span class="sxs-lookup"><span data-stu-id="c8f73-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="c8f73-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-350">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-351">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-352">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-352">Allowed From</span></span>

<span data-ttu-id="c8f73-353">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-354">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="c8f73-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="c8f73-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="c8f73-356">Usuń plik na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-357">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-358">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-358">Description</span></span>

<span data-ttu-id="c8f73-359">Ta usługa usuwa określony plik na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-360">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-360">Input Parameters</span></span>

- <span data-ttu-id="c8f73-361">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-362">**file_name** Nazwa pliku do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="c8f73-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="c8f73-363">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na usunięcie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="c8f73-364">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-365">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-366">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-367">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-367">Return Values</span></span>

- <span data-ttu-id="c8f73-368">**NX_SUCCESS** (0X00) pomyślne usunięcie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="c8f73-369">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-371">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-372">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-373">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-373">Allowed From</span></span>

<span data-ttu-id="c8f73-374">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-375">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="c8f73-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="c8f73-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="c8f73-377">Otwiera plik na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-378">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-379">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-379">Description</span></span>

<span data-ttu-id="c8f73-380">Ta usługa otwiera określony plik — do odczytu lub zapisu — na serwerze FTP, który został wcześniej połączony z określonym wystąpieniem klienta.</span><span class="sxs-lookup"><span data-stu-id="c8f73-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-381">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-381">Input Parameters</span></span>

- <span data-ttu-id="c8f73-382">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-383">**file_name** Nazwa pliku do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="c8f73-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="c8f73-384">**open_type** **NX_FTP_OPEN_FOR_READ** lub **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="c8f73-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="c8f73-385">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="c8f73-386">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-387">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-388">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-389">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-389">Return Values</span></span>

- <span data-ttu-id="c8f73-390">**NX_SUCCESS** (0X00) pomyślne otwarcie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="c8f73-391">**NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ otwarty.</span><span class="sxs-lookup"><span data-stu-id="c8f73-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="c8f73-392">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-393">Klient FTP **NX_FTP_NOT_CLOSED** (0xD6) jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="c8f73-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="c8f73-394">**NX_NO_FREE_PORTS** (0X45) Brak dostępnych portów TCP do przypisania</span><span class="sxs-lookup"><span data-stu-id="c8f73-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="c8f73-395">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-396">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-397">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-397">Allowed From</span></span>

<span data-ttu-id="c8f73-398">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-399">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="c8f73-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="c8f73-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="c8f73-401">Odczytaj z pliku</span><span class="sxs-lookup"><span data-stu-id="c8f73-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-402">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-403">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-403">Description</span></span>

<span data-ttu-id="c8f73-404">Ta usługa odczytuje pakiet z wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="c8f73-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="c8f73-405">Powinien być wywoływany kilkukrotnie do momentu otrzymania stanu NX_FTP_END_OF_FILE.</span><span class="sxs-lookup"><span data-stu-id="c8f73-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="c8f73-406">Należy zauważyć, że obiekt wywołujący nie przydziela pakietu dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="c8f73-407">Musi on dostarczyć jedynie wskaźnik do wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="c8f73-408">Ta usługa zaktualizuje ten wskaźnik pakietu, aby wskazywał pakiet pobrany z kolejki odbioru gniazda.</span><span class="sxs-lookup"><span data-stu-id="c8f73-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="c8f73-409">Jeśli zwracany jest stan pomyślne, oznacza to, że dostępny jest pakiet i jest on odpowiedzialny za wydanie pakietu po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="c8f73-410">Jeśli zwracany jest stan o wartości innej niż zero (stan błędu lub NX_FTP_END_OF_FILE), obiekt wywołujący nie zwolni pakietu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="c8f73-411">W przeciwnym razie zostanie wygenerowany błąd, gdy wskaźnik pakietu ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="c8f73-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-412">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-412">Input Parameters</span></span>

- <span data-ttu-id="c8f73-413">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-414">**packet_ptr** Wskaźnik do miejsca docelowego dla wskaźnika pakietu danych, który ma być przechowywany.</span><span class="sxs-lookup"><span data-stu-id="c8f73-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="c8f73-415">Jeśli to się powiedzie, pakiet część lub wszystkie zawarte w nim pliki.</span><span class="sxs-lookup"><span data-stu-id="c8f73-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="c8f73-416">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na odczytanie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="c8f73-417">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-418">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-419">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-420">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-420">Return Values</span></span>

- <span data-ttu-id="c8f73-421">**NX_SUCCESS** (0x00) pomyślnego odczytania pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="c8f73-422">Klient FTP **NX_FTP_NOT_OPEN** (0xD5) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="c8f73-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="c8f73-423">**NX_FTP_END_OF_FILE** (0XD7) koniec warunku pliku.</span><span class="sxs-lookup"><span data-stu-id="c8f73-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="c8f73-424">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-425">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-426">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-426">Allowed From</span></span>

<span data-ttu-id="c8f73-427">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-428">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="c8f73-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="c8f73-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="c8f73-430">Zmień nazwę pliku na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-432">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-432">Description</span></span>

<span data-ttu-id="c8f73-433">Ta usługa zmienia nazwę pliku na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-434">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-434">Input Parameters</span></span>

- <span data-ttu-id="c8f73-435">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-436">**Nazwa pliku** Bieżąca nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="c8f73-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="c8f73-437">**new_filename** Nowa nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="c8f73-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="c8f73-438">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na zmianę nazwy pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="c8f73-439">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-440">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-441">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-442">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-442">Return Values</span></span>

- <span data-ttu-id="c8f73-443">**NX_SUCCESS** (0x00) pomyślna zmiana nazwy pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="c8f73-444">Klient FTP **NX_FTP_NOT_CONNECTED** (0xD3) nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c8f73-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) nie otrzymał odpowiedzi 3xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="c8f73-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="c8f73-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c8f73-447">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-448">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-449">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-449">Allowed From</span></span>

<span data-ttu-id="c8f73-450">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-451">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="c8f73-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="c8f73-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="c8f73-453">Zapisz do pliku</span><span class="sxs-lookup"><span data-stu-id="c8f73-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-454">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c8f73-455">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-455">Description</span></span>

<span data-ttu-id="c8f73-456">Ta usługa zapisuje pakiet danych do wcześniej otwartego pliku na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-457">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-457">Input Parameters</span></span>

- <span data-ttu-id="c8f73-458">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-459">**packet_ptr** Wskaźnik pakietu zawierający dane do zapisu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="c8f73-460">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na zapis pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="c8f73-461">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8f73-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c8f73-462">**wartość limitu czasu** (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="c8f73-463">**TX_WAIT_FOREVER** (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c8f73-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-464">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-464">Return Values</span></span>

- <span data-ttu-id="c8f73-465">**NX_SUCCESS** (0X00) pomyślne zapis pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="c8f73-466">Klient FTP **NX_FTP_NOT_OPEN** (0xD5) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="c8f73-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="c8f73-467">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-468">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-469">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-469">Allowed From</span></span>

<span data-ttu-id="c8f73-470">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-471">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="c8f73-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="c8f73-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="c8f73-473">Włącz lub wyłącz tryb transferu pasywnego</span><span class="sxs-lookup"><span data-stu-id="c8f73-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-474">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="c8f73-475">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-475">Description</span></span>

<span data-ttu-id="c8f73-476">Ta usługa włącza tryb transferu pasywnego, jeśli passive_mode_enabled dane wejściowe są ustawione na NX_TRUE na wcześniej utworzonym wystąpieniu klienta FTP, tak że kolejne wywołania odczytu lub zapisu plików (RETR, STOR) lub pobrania listy katalogów (NLST) są wykonywane w trybie transferu.</span><span class="sxs-lookup"><span data-stu-id="c8f73-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="c8f73-477">Aby wyłączyć transfer w trybie pasywnym i wrócić do domyślnego zachowania aktywnego trybu transferu, Wywołaj tę funkcję z zestawem danych wejściowych passive_mode_enabled, aby NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="c8f73-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-478">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-478">Input Parameters</span></span>

- <span data-ttu-id="c8f73-479">**ftp_client_ptr** Wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c8f73-480">**passive_mode_enabled** Jeśli ustawiona na NX_TRUE, tryb pasywny jest włączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="c8f73-481">Jeśli ustawiona na NX_FALSE, tryb pasywny jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="c8f73-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-482">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-482">Return Values</span></span>

- <span data-ttu-id="c8f73-483">**NX_SUCCESS** (0X00) pomyślnie ustawiono tryb pasywny.</span><span class="sxs-lookup"><span data-stu-id="c8f73-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="c8f73-484">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-485">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c8f73-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-486">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-486">Allowed From</span></span>

<span data-ttu-id="c8f73-487">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-488">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="c8f73-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="c8f73-489">nx_ftp_server_create</span></span>

<span data-ttu-id="c8f73-490">Utwórz serwer FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-491">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="c8f73-492">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-492">Description</span></span>

<span data-ttu-id="c8f73-493">Ta usługa tworzy wystąpienie serwera FTP w określonym i wcześniej utworzonym wystąpieniu adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="c8f73-494">Zwróć uwagę na to, że serwer FTP musi zostać uruchomiony z wywołaniem do ***nx_ftp_server_start*** , aby rozpocząć operację.</span><span class="sxs-lookup"><span data-stu-id="c8f73-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-495">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-495">Input Parameters</span></span>

- <span data-ttu-id="c8f73-496">**ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="c8f73-497">**ftp_server_name** Nazwa serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="c8f73-498">**ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="c8f73-499">Należy pamiętać, że dla wystąpienia IP może istnieć tylko jeden serwer FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="c8f73-500">**media_ptr** Wskaźnik do skojarzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="c8f73-501">**stack_ptr** Wskaźnik do pamięci dla obszaru stosu wewnętrznego wątku serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="c8f73-502">**stack_size** Rozmiar obszaru stosu określonego przez *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="c8f73-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="c8f73-503">**pool_ptr** Wskaźnik do domyślnej puli pakietów NetX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="c8f73-504">Zwróć uwagę, że rozmiar ładunku pakietów w puli musi być wystarczająco duży, aby pomieścić największą nazwę pliku/ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="c8f73-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="c8f73-505">**ftp_login** Wskaźnik funkcji do funkcji logowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8f73-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="c8f73-506">Ta funkcja jest podana nazwa użytkownika i hasło z klienta wysyłającego żądanie połączenia oraz adres klienta w typie danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="c8f73-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="c8f73-507">Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="c8f73-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="c8f73-508">**ftp_logout** Wskaźnik funkcji do funkcji wylogowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8f73-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="c8f73-509">Ta funkcja jest podana nazwa użytkownika i hasło z klienta żądającego rozłączenia, a adres klienta w typie danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="c8f73-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="c8f73-510">Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="c8f73-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-511">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-511">Return Values</span></span>

- <span data-ttu-id="c8f73-512">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="c8f73-513">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-514">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-514">Allowed From</span></span>

<span data-ttu-id="c8f73-515">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-516">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="c8f73-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="c8f73-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="c8f73-518">Tworzenie serwera FTP z obsługą protokołów IPv4 i IPv6</span><span class="sxs-lookup"><span data-stu-id="c8f73-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-519">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="c8f73-520">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-520">Description</span></span>

<span data-ttu-id="c8f73-521">Ta usługa tworzy wystąpienie serwera FTP w określonym i wcześniej utworzonym wystąpieniu adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="c8f73-522">Należy pamiętać, że serwer FTP nadal musi zostać uruchomiony z wywołaniem do ***nx_ftp_server_start*** , aby rozpocząć operację po utworzeniu serwera.</span><span class="sxs-lookup"><span data-stu-id="c8f73-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-523">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-523">Input Parameters</span></span>

- <span data-ttu-id="c8f73-524">**ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="c8f73-525">**ftp_server_name** Nazwa serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="c8f73-526">**ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="c8f73-527">Należy pamiętać, że dla wystąpienia IP może istnieć tylko jeden serwer FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="c8f73-528">**media_ptr** Wskaźnik do skojarzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="c8f73-529">**stack_ptr** Wskaźnik do pamięci dla obszaru stosu wewnętrznego wątku serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="c8f73-530">**stack_size** Rozmiar obszaru stosu określonego przez *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="c8f73-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="c8f73-531">**pool_ptr** Wskaźnik do domyślnej puli pakietów NetX.</span><span class="sxs-lookup"><span data-stu-id="c8f73-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="c8f73-532">Zwróć uwagę, że rozmiar ładunku pakietów w puli musi być wystarczająco duży, aby pomieścić największą nazwę pliku/ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="c8f73-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="c8f73-533">**ftp_login_duo** Wskaźnik funkcji do funkcji logowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8f73-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="c8f73-534">Ta funkcja jest podana nazwa użytkownika i hasło z klienta wysyłającego żądanie połączenia oraz wskaźnik do adresu klienta w NXD_ADDRESS typie danych.</span><span class="sxs-lookup"><span data-stu-id="c8f73-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="c8f73-535">Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="c8f73-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="c8f73-536">**ftp_logout_duo** Wskaźnik funkcji do funkcji wylogowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8f73-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="c8f73-537">Ta funkcja jest podana nazwa użytkownika i hasło z klienta żądającego rozłączenia oraz wskaźnik do adresu klienta w NXD_ADDRESS typie danych.</span><span class="sxs-lookup"><span data-stu-id="c8f73-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="c8f73-538">Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="c8f73-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-539">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-539">Return Values</span></span>

- <span data-ttu-id="c8f73-540">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="c8f73-541">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-542">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-543">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-543">Allowed From</span></span>

<span data-ttu-id="c8f73-544">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-545">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="c8f73-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="c8f73-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="c8f73-547">Usuń serwer FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-548">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c8f73-549">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-549">Description</span></span>

<span data-ttu-id="c8f73-550">Ta usługa usuwa wcześniej utworzone wystąpienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-551">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-551">Input Parameters</span></span>

- <span data-ttu-id="c8f73-552">**ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-553">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-553">Return Values</span></span>

- <span data-ttu-id="c8f73-554">**NX_SUCCESS** (0X00) pomyślne usunięcie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="c8f73-555">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-556">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-557">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-557">Allowed From</span></span>

<span data-ttu-id="c8f73-558">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-559">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="c8f73-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="c8f73-560">nx_ftp_server_start</span></span>

<span data-ttu-id="c8f73-561">Uruchom serwer FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-562">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c8f73-563">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-563">Description</span></span>

<span data-ttu-id="c8f73-564">Ta usługa uruchamia wcześniej utworzone wystąpienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-565">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-565">Input Parameters</span></span>

- <span data-ttu-id="c8f73-566">**ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-567">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-567">Return Values</span></span>

- <span data-ttu-id="c8f73-568">**NX_SUCCESS** (0X00) pomyślne uruchomienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="c8f73-569">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-570">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-570">Allowed From</span></span>

<span data-ttu-id="c8f73-571">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-572">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="c8f73-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="c8f73-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="c8f73-574">Zatrzymaj serwer FTP</span><span class="sxs-lookup"><span data-stu-id="c8f73-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c8f73-575">Prototype</span><span class="sxs-lookup"><span data-stu-id="c8f73-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c8f73-576">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f73-576">Description</span></span>

<span data-ttu-id="c8f73-577">Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c8f73-578">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c8f73-578">Input Parameters</span></span>

- <span data-ttu-id="c8f73-579">**ftp_server_ptr** Wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c8f73-580">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c8f73-580">Return Values</span></span>

- <span data-ttu-id="c8f73-581">**NX_SUCCESS** (0X00) pomyślne zatrzymywanie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="c8f73-582">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="c8f73-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c8f73-583">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c8f73-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c8f73-584">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c8f73-584">Allowed From</span></span>

<span data-ttu-id="c8f73-585">Wątki</span><span class="sxs-lookup"><span data-stu-id="c8f73-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c8f73-586">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8f73-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
