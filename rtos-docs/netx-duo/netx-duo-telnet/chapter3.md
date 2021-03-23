---
title: Rozdział 3 — Opis usług Telnet usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług Telnet usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821618"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="0786b-103">Rozdział 3 — Opis usług Telnet usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="0786b-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="0786b-104">Ten rozdział zawiera opis wszystkich usług Telnet usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="0786b-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0786b-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0786b-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0786b-106">**nx_telnet_client_connect**: *łączenie klienta Telnet z adresem IPv4*</span><span class="sxs-lookup"><span data-stu-id="0786b-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="0786b-107">**nxd_telnet_client_connect**: *łączenie klienta Telnet IPv6 z adresem IPv6*</span><span class="sxs-lookup"><span data-stu-id="0786b-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="0786b-108">**nx_telnet_client_create**: *Tworzenie klienta Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="0786b-109">**nx_telnet_client_delete**: *Usuwanie klienta Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="0786b-110">**nx_telnet_client_disconnect**: *Rozłączanie klienta Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="0786b-111">**nx_telnet_client_packet_receive**: *otrzymywanie pakietu za pośrednictwem klienta Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="0786b-112">**nx_telnet_client_packet_send**: *Wyślij pakiet za pośrednictwem klienta Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="0786b-113">**nx_telnet_server_create**: *Tworzenie serwera Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="0786b-114">**nx_telnet_server_delete**: *usuwanie serwera Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="0786b-115">**nx_telnet_server_disconnect**: *Rozłączanie klienta Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="0786b-116">**nx_telnet_server_get_open_connection_count**: *pobieranie liczby otwartych połączeń*</span><span class="sxs-lookup"><span data-stu-id="0786b-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="0786b-117">**nx_telnet_server_packet_send**: *Wyślij pakiet przez połączenie klienta*</span><span class="sxs-lookup"><span data-stu-id="0786b-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="0786b-118">**nx_telnet_server_packet_pool_set**: *Ustaw pulę pakietów jako pulę pakietów serwera Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="0786b-119">**nx_telnet_server_start**: *Uruchamianie serwera Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="0786b-120">**nx_telnet_server_stop**: *zatrzymywanie serwera Telnet*</span><span class="sxs-lookup"><span data-stu-id="0786b-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="0786b-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="0786b-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="0786b-122">Łączenie klienta Telnet z adresem IPv4</span><span class="sxs-lookup"><span data-stu-id="0786b-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-123">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0786b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-124">Description</span></span>

<span data-ttu-id="0786b-125">Ta usługa próbuje połączyć wcześniej utworzone wystąpienie klienta programu Telnet z serwerem w określonym adresie IP i porcie przy użyciu adresu IPv4 serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="0786b-126">Ta usługa w rzeczywistości wstawia adres IP serwera ULONG w bloku sterowania NXD_ADDRESS i ustawia wersję protokołu IP na 4 przed wywołaniem usługi *nxd_telnet_client_connect* opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="0786b-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-127">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-127">Input Parameters</span></span>

- <span data-ttu-id="0786b-128">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="0786b-129">**server_IP**: adres IPv4 serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="0786b-130">**SERVER_PORT**: port TCP serwera (serwer Telnet jest portem 23).</span><span class="sxs-lookup"><span data-stu-id="0786b-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="0786b-131">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na połączenie klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="0786b-132">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0786b-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="0786b-133">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="0786b-134">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0786b-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-135">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-135">Return Values</span></span>

- <span data-ttu-id="0786b-136">**NX_SUCCESS**: (0x00) pomyślnego nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="0786b-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="0786b-137">**NX_TELNET_NOT_DISCONNECTED**: (0XF4) klient jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="0786b-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="0786b-138">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="0786b-139">NX_IP_ADDRESS_ERROR: (0x21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="0786b-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0786b-140">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-141">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-141">Allowed From</span></span>

<span data-ttu-id="0786b-142">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="0786b-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="0786b-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="0786b-145">Łączenie klienta Telnet z adresem IPv6 lub IPv4</span><span class="sxs-lookup"><span data-stu-id="0786b-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-146">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0786b-147">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-147">Description</span></span>

<span data-ttu-id="0786b-148">Ta usługa próbuje połączyć wcześniej utworzone wystąpienie klienta programu Telnet z serwerem w określonym adresie IP i porcie przy użyciu adresu IPv6 serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="0786b-149">Ta usługa może przyjmować adres IPv4 lub IPv6, ale musi być zawarta w server_ip_address zmiennej NXD_ADDRESS *.*</span><span class="sxs-lookup"><span data-stu-id="0786b-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-150">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-150">Input Parameters</span></span>

- <span data-ttu-id="0786b-151">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="0786b-152">**server_ip_address**: adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="0786b-153">**SERVER_PORT**: port TCP serwera (serwer Telnet jest portem 23).</span><span class="sxs-lookup"><span data-stu-id="0786b-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="0786b-154">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na połączenie klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="0786b-155">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0786b-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="0786b-156">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="0786b-157">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0786b-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-158">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-158">Return Values</span></span>

- <span data-ttu-id="0786b-159">**NX_SUCCESS**: (0x00) pomyślnego nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="0786b-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="0786b-160">**NX_TELNET_ERROR**: (0xF0) błąd połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="0786b-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="0786b-161">**NX_TELNET_NOT_DISCONNECTED**: (0XF4) klient jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="0786b-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="0786b-162">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="0786b-163">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0786b-164">NX_TELNET_INVALID_PARAMETER: (0xF5) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="0786b-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-165">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-165">Allowed From</span></span>

<span data-ttu-id="0786b-166">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="0786b-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="0786b-168">nx_telnet_client_create</span></span>

<span data-ttu-id="0786b-169">Tworzenie klienta Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-170">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="0786b-171">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-171">Description</span></span>

<span data-ttu-id="0786b-172">Ta usługa tworzy wystąpienie klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-173">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-173">Input Parameters</span></span>

- <span data-ttu-id="0786b-174">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="0786b-175">**CLIENT_NAME**: nazwa wystąpienia klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="0786b-176">**ip_ptr**: wskaźnik do wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="0786b-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="0786b-177">**window_size**: rozmiar okna odbierania protokołu TCP dla tego klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-178">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-178">Return Values</span></span>

- <span data-ttu-id="0786b-179">**NX_SUCCESS**: (0X00) pomyślne utworzenie klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="0786b-180">Błąd tworzenia gniazda **NX_TELNET_ERROR**: (0xF0).</span><span class="sxs-lookup"><span data-stu-id="0786b-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="0786b-181">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta lub adresu IP.</span><span class="sxs-lookup"><span data-stu-id="0786b-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-182">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-182">Allowed From</span></span>

<span data-ttu-id="0786b-183">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-184">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="0786b-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="0786b-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="0786b-186">Usuwanie klienta Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-187">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="0786b-188">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-188">Description</span></span>

<span data-ttu-id="0786b-189">Ta usługa usuwa wcześniej utworzone wystąpienie klienta programu Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-190">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-190">Input Parameters</span></span>

- <span data-ttu-id="0786b-191">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-192">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-192">Return Values</span></span>

- <span data-ttu-id="0786b-193">**NX_SUCCESS**: (0X00) pomyślne usunięcie klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="0786b-194">**NX_TELNET_NOT_DISCONNECTED**: (0XF4) klient jest nadal połączony.</span><span class="sxs-lookup"><span data-stu-id="0786b-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="0786b-195">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="0786b-196">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-197">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-197">Allowed From</span></span>

<span data-ttu-id="0786b-198">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-199">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="0786b-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="0786b-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="0786b-201">Rozłączanie klienta Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-202">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0786b-203">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-203">Description</span></span>

<span data-ttu-id="0786b-204">Ta usługa rozłącza połączenie z wcześniej połączonym wystąpieniem klienta programu Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-205">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-205">Input Parameters</span></span>

- <span data-ttu-id="0786b-206">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="0786b-207">**WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać na rozłączenie przez klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="0786b-208">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0786b-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="0786b-209">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="0786b-210">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0786b-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-211">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-211">Return Values</span></span>

- <span data-ttu-id="0786b-212">**NX_SUCCESS**: (0X00) pomyślne rozłączenie klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="0786b-213">**NX_TELNET_NOT_CONNECTED**: (0XF3) klient nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="0786b-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="0786b-214">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="0786b-215">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0786b-216">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-216">Allowed From</span></span>

<span data-ttu-id="0786b-217">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-218">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="0786b-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="0786b-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="0786b-220">Odbieranie pakietu za pośrednictwem klienta Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0786b-222">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-222">Description</span></span>

<span data-ttu-id="0786b-223">Ta usługa odbiera pakiet z wcześniej połączonego wystąpienia klienta programu Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-224">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-224">Input Parameters</span></span>

- <span data-ttu-id="0786b-225">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="0786b-226">**packet_ptr**: wskaźnik do miejsca docelowego dla odebranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="0786b-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="0786b-227">**WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać na odebranie pakietu klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="0786b-228">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0786b-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="0786b-229">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="0786b-230">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0786b-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-231">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-231">Return Values</span></span>

- <span data-ttu-id="0786b-232">**NX_SUCCESS**: (0x00) odbieranie pakietu klienta powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0786b-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="0786b-233">NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="0786b-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0786b-234">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-235">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-235">Allowed From</span></span>

<span data-ttu-id="0786b-236">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-237">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="0786b-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="0786b-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="0786b-239">Wyślij pakiet za pośrednictwem klienta Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0786b-241">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-241">Description</span></span>

<span data-ttu-id="0786b-242">Ta usługa wysyła pakiet za pośrednictwem wcześniej połączonego wystąpienia klienta programu Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-243">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-243">Input Parameters</span></span>

- <span data-ttu-id="0786b-244">**client_ptr**: wskaźnik do bloku kontroli klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="0786b-245">**packet_ptr**: wskaźnik do pakietu do wysłania.</span><span class="sxs-lookup"><span data-stu-id="0786b-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="0786b-246">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na wysłanie pakietu klienta Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="0786b-247">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0786b-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="0786b-248">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="0786b-249">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0786b-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-250">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-250">Return Values</span></span>

- <span data-ttu-id="0786b-251">**NX_SUCCESS**: (0X00) pomyślne wysłanie pakietu klienta.</span><span class="sxs-lookup"><span data-stu-id="0786b-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="0786b-252">**NX_TELNET_ERROR**: (0XF0) wysyłanie pakietu nie powiodło się — obiekt wywołujący jest odpowiedzialny za wydanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="0786b-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="0786b-253">NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="0786b-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0786b-254">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-255">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-255">Allowed From</span></span>

<span data-ttu-id="0786b-256">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-257">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="0786b-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="0786b-258">nx_telnet_server_create</span></span>

<span data-ttu-id="0786b-259">Tworzenie serwera Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-260">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="0786b-261">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-261">Description</span></span>

<span data-ttu-id="0786b-262">Ta usługa tworzy wystąpienie serwera Telnet na określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="0786b-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-263">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-263">Input Parameters</span></span>

- <span data-ttu-id="0786b-264">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="0786b-265">**server_name**: nazwa wystąpienia serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="0786b-266">**ip_ptr**: wskaźnik do skojarzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="0786b-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="0786b-267">**stack_ptr**: wskaźnik do stosu dla wewnętrznego wątku serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="0786b-268">**sack_size**: rozmiar stosu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0786b-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="0786b-269">**new_connection**: wskaźnik funkcji procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0786b-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="0786b-270">Ta procedura jest wywoływana za każdym razem, gdy na serwerze zostanie wykryte nowe żądanie połączenia klienta programu Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="0786b-271">**receive_data**: wskaźnik funkcji procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0786b-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="0786b-272">Ta procedura jest wywoływana za każdym razem, gdy w ramach połączenia są obecne nowe dane klienta programu Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="0786b-273">Ta procedura jest odpowiedzialna za wydanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="0786b-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="0786b-274">**end_connection**: wskaźnik funkcji procedury wywołania zwrotnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0786b-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="0786b-275">Ta procedura jest wywoływana za każdym razem, gdy połączenie z klientem Telnet zostanie odłączone przez klienta lub przekroczenie limitu czasu połączenia klienta ("limit czasu aktywności").</span><span class="sxs-lookup"><span data-stu-id="0786b-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="0786b-276">Serwer można także rozłączyć za pośrednictwem usługi *nx_telnet_server_disconnect* opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="0786b-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-277">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-277">Return Values</span></span>

- <span data-ttu-id="0786b-278">**NX_SUCCESS**: (0X00) pomyślne utworzenie serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="0786b-279">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik wywołania zwrotnego serwera, adresu IP, stosu lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0786b-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-280">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-280">Allowed From</span></span>

<span data-ttu-id="0786b-281">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-282">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="0786b-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="0786b-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="0786b-284">Usuwanie serwera Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-285">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="0786b-286">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-286">Description</span></span>

<span data-ttu-id="0786b-287">Ta usługa usuwa wcześniej utworzone wystąpienie serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-288">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-288">Input Parameters</span></span>

- <span data-ttu-id="0786b-289">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-290">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-290">Return Values</span></span>

- <span data-ttu-id="0786b-291">**NX_SUCCESS**: (0X00) pomyślne usunięcie serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="0786b-292">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="0786b-293">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-294">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-294">Allowed From</span></span>

<span data-ttu-id="0786b-295">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-296">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="0786b-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="0786b-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="0786b-298">Rozłączanie klienta Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-299">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="0786b-300">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-300">Description</span></span>

<span data-ttu-id="0786b-301">Ta usługa rozłącza wcześniej połączony klient z tym wystąpieniem serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="0786b-302">Ta procedura jest zazwyczaj wywoływana z funkcji wywołania zwrotnego odbierania danych aplikacji w odpowiedzi na warunek wykryty w odebranych danych.</span><span class="sxs-lookup"><span data-stu-id="0786b-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-303">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-303">Input Parameters</span></span>

- <span data-ttu-id="0786b-304">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="0786b-305">**logical_connection**: połączenie logiczne odpowiada połączeniu z klientem na tym serwerze.</span><span class="sxs-lookup"><span data-stu-id="0786b-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="0786b-306">Prawidłowy zakres wartości z zakresu od 0 do NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="0786b-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-307">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-307">Return Values</span></span>

- <span data-ttu-id="0786b-308">**NX_SUCCESS**: (0X00) pomyślne rozłączenie serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="0786b-309">**NX_TELNET_ERROR**: (0xF0) rozłączenie serwera nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0786b-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="0786b-310">NX_OPTION_ERROR: (0x0A) nieprawidłowe połączenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="0786b-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="0786b-311">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="0786b-312">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-313">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-313">Allowed From</span></span>

<span data-ttu-id="0786b-314">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-315">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="0786b-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="0786b-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="0786b-317">Zwróć liczbę aktualnie otwartych połączeń</span><span class="sxs-lookup"><span data-stu-id="0786b-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="0786b-319">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-319">Description</span></span>

<span data-ttu-id="0786b-320">Ta usługa zwraca liczbę aktualnie połączonych klientów Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-321">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-321">Input Parameters</span></span>

- <span data-ttu-id="0786b-322">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="0786b-323">**Connection_count**: wskaźnik do pamięci, aby przechowywać liczbę połączeń</span><span class="sxs-lookup"><span data-stu-id="0786b-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-324">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-324">Return Values</span></span>

- <span data-ttu-id="0786b-325">**NX_SUCCESS**: (0X00) pomyślne zakończenie.</span><span class="sxs-lookup"><span data-stu-id="0786b-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="0786b-326">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="0786b-327">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-328">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-328">Allowed From</span></span>

<span data-ttu-id="0786b-329">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-330">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="0786b-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="0786b-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="0786b-332">Wyślij pakiet przez połączenie klienta</span><span class="sxs-lookup"><span data-stu-id="0786b-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0786b-334">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-334">Description</span></span>

<span data-ttu-id="0786b-335">Ta usługa wysyła pakiet do połączenia klienta w tym wystąpieniu serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="0786b-336">Ta procedura jest zazwyczaj wywoływana z funkcji wywołania zwrotnego odbierania danych aplikacji w odpowiedzi na warunek wykryty w odebranych danych.</span><span class="sxs-lookup"><span data-stu-id="0786b-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-337">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-337">Input Parameters</span></span>

- <span data-ttu-id="0786b-338">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="0786b-339">**logical_connection**: połączenie logiczne odpowiada połączeniu z klientem na tym serwerze.</span><span class="sxs-lookup"><span data-stu-id="0786b-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="0786b-340">Prawidłowy zakres wartości z zakresu od 0 do NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="0786b-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="0786b-341">**packet_ptr**: wskaźnik do odebranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="0786b-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="0786b-342">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na wysłanie pakietu serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="0786b-343">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0786b-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="0786b-344">**wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="0786b-345">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0786b-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="0786b-346">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-346">Return Values</span></span>

- <span data-ttu-id="0786b-347">**NX_SUCCESS**: (0X00) pomyślne wysłanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="0786b-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="0786b-348">**NX_TELNET_FAILED**: (0xF2) wysyłanie gniazda TCP nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0786b-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="0786b-349">NX_OPTION_ERROR: (0x0A) nieprawidłowe połączenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="0786b-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="0786b-350">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="0786b-351">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.</span><span class="sxs-lookup"><span data-stu-id="0786b-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-352">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-352">Allowed From</span></span>

<span data-ttu-id="0786b-353">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-354">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="0786b-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="0786b-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="0786b-356">Ustaw wcześniej utworzoną pulę pakietów jako pulę serwerów Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-357">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="0786b-358">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-358">Description</span></span>

<span data-ttu-id="0786b-359">Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów serwera Telnet, jeśli NX_TELNET_SERVER_USER_CREATE_PACKET_POOL jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="0786b-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="0786b-360">Wymaga również, aby nie NX_TELNET_SERVER_OPTION_DISABLE być zdefiniowany, aby serwer Telnet mógł przesyłać opcje Telnet do klientów Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="0786b-361">Pozwala to aplikacjom na tworzenie puli pakietów w innej pamięci, np. Brak pamięci podręcznej, niż stos serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="0786b-362">Należy pamiętać, że jeśli ta funkcja nie sprawdza, czy pula pakietów serwera Telnet została już ustawiona.</span><span class="sxs-lookup"><span data-stu-id="0786b-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="0786b-363">Jeśli zostanie wywołana dla wskaźnika puli pakietów serwera Telnet o wartości innej niż null, spowoduje to zastąpienie i zastąpienie istniejącej puli pakietów pulą pakietów wskazywanym przez wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="0786b-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-364">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-364">Input Parameters</span></span>

- <span data-ttu-id="0786b-365">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="0786b-366">**packet_pool_ptr**: wskaźnik do wcześniej utworzonej puli pakietów</span><span class="sxs-lookup"><span data-stu-id="0786b-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-367">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-367">Return Values</span></span>

- <span data-ttu-id="0786b-368">**NX_SUCCESS**: (0X00) pomyślnie ustawił pulę.</span><span class="sxs-lookup"><span data-stu-id="0786b-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="0786b-369">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-370">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-370">Allowed From</span></span>

<span data-ttu-id="0786b-371">Init, wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-372">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="0786b-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="0786b-373">nx_telnet_server_start</span></span>

<span data-ttu-id="0786b-374">Uruchom serwer Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-375">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="0786b-376">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-376">Description</span></span>

<span data-ttu-id="0786b-377">Ta usługa uruchamia wcześniej utworzone wystąpienie serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-378">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-378">Input Parameters</span></span>

- <span data-ttu-id="0786b-379">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-380">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-380">Return Values</span></span>

- <span data-ttu-id="0786b-381">**NX_SUCCESS**: (0X00) zostało pomyślnie rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="0786b-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="0786b-382">**NX_TELNET_NO_PACKET_POOL**: (0XF6) brak zestawu puli pakietów</span><span class="sxs-lookup"><span data-stu-id="0786b-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="0786b-383">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-384">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-384">Allowed From</span></span>

<span data-ttu-id="0786b-385">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-386">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="0786b-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="0786b-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="0786b-388">Zatrzymaj serwer Telnet</span><span class="sxs-lookup"><span data-stu-id="0786b-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0786b-389">Prototype</span><span class="sxs-lookup"><span data-stu-id="0786b-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="0786b-390">Opis</span><span class="sxs-lookup"><span data-stu-id="0786b-390">Description</span></span>

<span data-ttu-id="0786b-391">Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie serwera Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0786b-392">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="0786b-392">Input Parameters</span></span>

- <span data-ttu-id="0786b-393">**server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.</span><span class="sxs-lookup"><span data-stu-id="0786b-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0786b-394">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="0786b-394">Return Values</span></span>

- <span data-ttu-id="0786b-395">**NX_SUCCESS**: (0X00) zostało pomyślnie zatrzymane</span><span class="sxs-lookup"><span data-stu-id="0786b-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="0786b-396">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.</span><span class="sxs-lookup"><span data-stu-id="0786b-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="0786b-397">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="0786b-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0786b-398">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="0786b-398">Allowed From</span></span>

<span data-ttu-id="0786b-399">Wątki</span><span class="sxs-lookup"><span data-stu-id="0786b-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0786b-400">Przykład</span><span class="sxs-lookup"><span data-stu-id="0786b-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```