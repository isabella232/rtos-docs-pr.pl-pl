---
title: Rozdział 3 — Opis usług Azure RTO NetX Duo TFTP
description: Ten rozdział zawiera opis wszystkich usług NetX Duo TFTP (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821612"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="c4095-103">Rozdział 3 — Opis usług Azure RTO NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="c4095-104">Ten rozdział zawiera opis wszystkich usług NetX Duo TFTP (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="c4095-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="c4095-105">O ile nie określono inaczej, wszystkie usługi obsługują komunikację IPv6 i IPv4.</span><span class="sxs-lookup"><span data-stu-id="c4095-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="c4095-106">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c4095-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="c4095-107">**nxd_tftp_client_file_open**: *Otwórz plik klienta TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="c4095-108">**nxd_tftp_client_create**: *Tworzenie wystąpienia klienta TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="c4095-109">**nxd_tftp_client_delete**: *usuwanie wystąpienia klienta TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="c4095-110">**nxd_tftp_client_error_info_get**: *Uzyskiwanie informacji o błędzie klienta*</span><span class="sxs-lookup"><span data-stu-id="c4095-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="c4095-111">**nxd_tftp_client_file_close**: *Zamknij plik klienta*</span><span class="sxs-lookup"><span data-stu-id="c4095-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="c4095-112">**nxd_tftp_client_file_open**: *Otwórz plik klienta*</span><span class="sxs-lookup"><span data-stu-id="c4095-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="c4095-113">**nxd_tftp_client_file_read**: *Odczytaj blok z pliku klienta*</span><span class="sxs-lookup"><span data-stu-id="c4095-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="c4095-114">**nxd_tftp_client_file_write**: *Zapisz blok do pliku klienta*</span><span class="sxs-lookup"><span data-stu-id="c4095-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="c4095-115">**nxd_tftp_client_packet_allocate**: *Przydziel pakiet do zapisu pliku klienta*</span><span class="sxs-lookup"><span data-stu-id="c4095-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="c4095-116">**nxd_tftp_client_set_interface**: *Ustaw interfejs fizyczny dla żądań TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="c4095-117">**nxd_tftp_server_create**: *Utwórz serwer TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="c4095-118">**nxd_tftp_server_delete**: *usuwanie serwera TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="c4095-119">**nxd_tftp_server_start**: *Uruchom serwer TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="c4095-120">**nxd_tftp_server_stop**: *ZAtrzymywanie serwera TFTP*</span><span class="sxs-lookup"><span data-stu-id="c4095-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="c4095-121">Równoważne wszystkie usługi wymienione powyżej są dostępne w protokole IPv4 klienta i serwera NetX Duo, np. *nx_tftp_server_create* i *nx_tftp_client_file_open*.</span><span class="sxs-lookup"><span data-stu-id="c4095-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="c4095-122">Na poniższych stronach znajdują się tylko opisy interfejsów API "Duo", np. usługi zaczynające się od *nxd_*.</span><span class="sxs-lookup"><span data-stu-id="c4095-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="c4095-123">Jeśli określono NXD_ADDRESS \* dane wejściowe, odpowiednik interfejsu API protokołu IPv4 jest wywoływany dla danych wejściowych ulong.</span><span class="sxs-lookup"><span data-stu-id="c4095-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="c4095-124">W przeciwnym razie nie ma żadnych różnic w korzystaniu z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="c4095-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="c4095-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="c4095-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="c4095-126">Tworzenie wystąpienia klienta TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c4095-128">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-128">Description</span></span>

<span data-ttu-id="c4095-129">Ta usługa tworzy wystąpienie klienta TFTP dla utworzonego wcześniej wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="c4095-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4095-130">Aplikacja musi utworzyć określony adres IP i pulę pakietów, które zostały już utworzone.</span><span class="sxs-lookup"><span data-stu-id="c4095-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="c4095-131">Ponadto należy włączyć protokół UDP przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-132">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-132">Input Parameters</span></span>

- <span data-ttu-id="c4095-133">**tftp_client_ptr** Wskaźnik do bloku kontroli klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="c4095-134">**tftp_client_name** Nazwa tego wystąpienia klienta TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="c4095-135">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="c4095-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="c4095-136">**pool_ptr** Wskaźnik do wystąpienia klienta TFTP puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="c4095-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-137">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-137">Return Values</span></span>

- <span data-ttu-id="c4095-138">**NX_SUCCESS**(0X00) pomyślnie utworzono TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="c4095-139">**NX_TFTP_INVALID_IP_VERSION** (0X0C) nieprawidłowa lub nieobsługiwana wersja protokołu IP</span><span class="sxs-lookup"><span data-stu-id="c4095-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="c4095-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="c4095-141">Nie odebrano potwierdzenia serwera **NX_TFTP_NO_ACK_RECEIVED** (0x09)</span><span class="sxs-lookup"><span data-stu-id="c4095-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="c4095-142">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP, puli lub TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="c4095-143">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c4095-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="c4095-144">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-145">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-145">Allowed From</span></span>

<span data-ttu-id="c4095-146">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="c4095-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="c4095-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="c4095-149">Usuwanie wystąpienia klienta TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="c4095-151">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-151">Description</span></span>

<span data-ttu-id="c4095-152">Ta usługa usuwa wcześniej utworzone wystąpienie klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-153">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-153">Input Parameters</span></span>

- <span data-ttu-id="c4095-154">**tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-155">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-155">Return Values</span></span>

- <span data-ttu-id="c4095-156">**NX_SUCCESS** (0X00) pomyślne usunięcie klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="c4095-157">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-158">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-159">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-159">Allowed From</span></span>

<span data-ttu-id="c4095-160">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="c4095-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="c4095-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="c4095-163">Pobierz informacje o błędzie klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="c4095-165">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-165">Description</span></span>

<span data-ttu-id="c4095-166">Ta usługa zwraca kod ostatniego odebranego błędu i ustawia wskaźnik na wewnętrzny ciąg błędu klienta.</span><span class="sxs-lookup"><span data-stu-id="c4095-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="c4095-167">W warunkach błędów użytkownik może wyświetlić ostatni błąd wysyłany przez serwer.</span><span class="sxs-lookup"><span data-stu-id="c4095-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="c4095-168">Pusty ciąg błędu wskazuje, że błąd nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="c4095-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-169">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-169">Input Parameters</span></span>

- <span data-ttu-id="c4095-170">**tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="c4095-171">**error_code** Wskaźnik do obszaru docelowego dla kodu błędu</span><span class="sxs-lookup"><span data-stu-id="c4095-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="c4095-172">**ERROR_STRING** Wskaźnik do miejsca docelowego dla ciągu błędu</span><span class="sxs-lookup"><span data-stu-id="c4095-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-173">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-173">Return Values</span></span>

- <span data-ttu-id="c4095-174">**NX_SUCCESS** (0x00) powiodło się pobieranie informacji o błędzie TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="c4095-175">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="c4095-176">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-177">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-177">Allowed From</span></span>

<span data-ttu-id="c4095-178">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-179">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="c4095-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="c4095-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="c4095-181">Zamknij plik klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-182">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="c4095-183">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-183">Description</span></span>

<span data-ttu-id="c4095-184">Ta usługa zamyka poprzednio otwarty plik przez to wystąpienie klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="c4095-185">W przypadku wystąpienia klienta TFTP może być otwarty tylko jeden plik naraz.</span><span class="sxs-lookup"><span data-stu-id="c4095-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-186">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-186">Input Parameters</span></span>

- <span data-ttu-id="c4095-187">**tftp_client_ptr** Wskaźnik do wcześniej utworzonego wystąpienia klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="c4095-188">**ip_type** Wskaż, którego protokołu IP użyć.</span><span class="sxs-lookup"><span data-stu-id="c4095-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="c4095-189">Prawidłowe opcje to IPv4 (4) lub IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="c4095-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-190">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-190">Return Values</span></span>

- <span data-ttu-id="c4095-191">**NX_SUCCESS** (0X00) pomyślnie zamknięto plik TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="c4095-192">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-193">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="c4095-194">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="c4095-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-195">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-195">Allowed From</span></span>

<span data-ttu-id="c4095-196">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="c4095-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="c4095-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="c4095-199">Otwórz plik klienta TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c4095-201">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-201">Description</span></span>

<span data-ttu-id="c4095-202">Ta usługa próbuje otworzyć określony plik na serwerze TFTP o określonym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="c4095-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="c4095-203">Plik zostanie otwarty na potrzeby odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="c4095-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="c4095-204">Jest to ograniczone tylko do pakietów IPv4 i jest przeznaczony do obsługi aplikacji NetX TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="c4095-205">Deweloperzy są zachęcani do przenoszenia aplikacji do korzystania z równorzędnej usługi "Duo" *nxd_tftp_client_file_open.*</span><span class="sxs-lookup"><span data-stu-id="c4095-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-206">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-206">Input Parameters</span></span>

- <span data-ttu-id="c4095-207">**tftp_client_ptr** Wskaźnik do bloku sterowania TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="c4095-208">**file_name** Nazwa pliku ASCII, zakończona zerem i z odpowiednimi informacjami o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="c4095-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="c4095-209">**server_ip_address** Adres TFTP serwera.</span><span class="sxs-lookup"><span data-stu-id="c4095-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="c4095-210">**open_type** Typ żądania otwartego:</span><span class="sxs-lookup"><span data-stu-id="c4095-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="c4095-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="c4095-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="c4095-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="c4095-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="c4095-213">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="c4095-214">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4095-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="c4095-215">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4095-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="c4095-216">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="c4095-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="c4095-217">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c4095-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="c4095-218">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="c4095-219">**ip_type** Wskaż, którego protokołu IP użyć.</span><span class="sxs-lookup"><span data-stu-id="c4095-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="c4095-220">Prawidłowe opcje to IPv4 (4) lub IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="c4095-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-221">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-221">Return Values</span></span>

- <span data-ttu-id="c4095-222">**NX_SUCCESS** (0X00) pomyślne otwarcie pliku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="c4095-223">Klient **NX_TFTP_NOT_CLOSED** (0xC3) ma już otwarty plik</span><span class="sxs-lookup"><span data-stu-id="c4095-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="c4095-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="c4095-225">**NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="c4095-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="c4095-227">**NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu</span><span class="sxs-lookup"><span data-stu-id="c4095-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="c4095-228">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-229">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="c4095-230">NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="c4095-231">NX_OPTION_ERROR (0x0A) Nieprawidłowy typ otwarty</span><span class="sxs-lookup"><span data-stu-id="c4095-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-232">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-232">Allowed From</span></span>

<span data-ttu-id="c4095-233">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-234">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="c4095-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="c4095-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="c4095-236">Otwórz plik klienta TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-237">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="c4095-238">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-238">Description</span></span>

<span data-ttu-id="c4095-239">Ta usługa próbuje otworzyć określony plik na serwerze TFTP przy użyciu określonego adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="c4095-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="c4095-240">Plik zostanie otwarty na potrzeby odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="c4095-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-241">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-241">Input Parameters</span></span>

- <span data-ttu-id="c4095-242">**tftp_client_ptr** Wskaźnik do bloku sterowania TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="c4095-243">**file_name** Nazwa pliku ASCII, zakończona zerem i z odpowiednimi informacjami o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="c4095-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="c4095-244">**server_ip_address** Adres TFTP serwera.</span><span class="sxs-lookup"><span data-stu-id="c4095-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="c4095-245">**open_type** Typ żądania otwartego:</span><span class="sxs-lookup"><span data-stu-id="c4095-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="c4095-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="c4095-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="c4095-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="c4095-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="c4095-248">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na otwarcie pliku klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="c4095-249">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4095-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="c4095-250">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4095-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="c4095-251">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="c4095-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="c4095-252">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c4095-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="c4095-253">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="c4095-254">**ip_type** Wskaż, którego protokołu IP użyć.</span><span class="sxs-lookup"><span data-stu-id="c4095-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="c4095-255">Prawidłowe opcje to IPv4 (4) lub IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="c4095-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-256">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-256">Return Values</span></span>

- <span data-ttu-id="c4095-257">**NX_SUCCESS** (0X00) pomyślne otwarcie pliku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="c4095-258">Klient **NX_TFTP_NOT_CLOSED** (0xC3) ma już otwarty plik</span><span class="sxs-lookup"><span data-stu-id="c4095-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="c4095-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="c4095-260">**NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="c4095-261">**NX_TFTP_INVALID_IP_VERSION** (0X0C) Nieprawidłowa wersja adresu IP</span><span class="sxs-lookup"><span data-stu-id="c4095-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="c4095-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="c4095-263">**NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu</span><span class="sxs-lookup"><span data-stu-id="c4095-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="c4095-264">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-265">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="c4095-266">NX_IP_ADDRESS_ERROR (0x21) nieprawidłowy adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="c4095-267">NX_OPTION_ERROR (0x0A) Nieprawidłowy typ otwarty</span><span class="sxs-lookup"><span data-stu-id="c4095-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="c4095-268">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c4095-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-269">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-269">Allowed From</span></span>

<span data-ttu-id="c4095-270">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-271">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="c4095-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="c4095-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="c4095-273">Odczytaj blok z pliku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-274">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="c4095-275">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-275">Description</span></span>

<span data-ttu-id="c4095-276">Ta usługa odczytuje blok 512-bajtowy z wcześniej otwartego pliku klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="c4095-277">Blok zawierający mniej niż 512 bajtów sygnalizuje koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="c4095-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-278">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-278">Input Parameters</span></span>

- <span data-ttu-id="c4095-279">**tftp_client_ptr** Wskaźnik do bloku kontroli klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="c4095-280">**packet_ptr** Lokalizacja docelowa pakietu zawierającego blok odczytany z pliku.</span><span class="sxs-lookup"><span data-stu-id="c4095-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="c4095-281">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na zakończenie odczytu.</span><span class="sxs-lookup"><span data-stu-id="c4095-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="c4095-282">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4095-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="c4095-283">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4095-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="c4095-284">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="c4095-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="c4095-285">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c4095-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="c4095-286">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na wysłanie bloku pliku przez serwer TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="c4095-287">**ip_type** Wskaż, którego protokołu IP użyć.</span><span class="sxs-lookup"><span data-stu-id="c4095-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="c4095-288">Prawidłowe opcje to IPv4 (4) lub IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="c4095-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-289">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-289">Return Values</span></span>

- <span data-ttu-id="c4095-290">**NX_SUCCESS** (0X00) pomyślne odczytanie bloku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="c4095-291">**NX_TFTP_NOT_OPEN** (0XC3) określony plik klienta nie jest otwarty do odczytu</span><span class="sxs-lookup"><span data-stu-id="c4095-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="c4095-292">**NX_NO_PACKET** (0X01) żaden pakiet nie został odebrany z serwera.</span><span class="sxs-lookup"><span data-stu-id="c4095-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="c4095-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="c4095-294">**NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="c4095-295">Wykryto koniec pliku **NX_TFTP_END_OF_FILE** (0xc5) (nie jest to błąd).</span><span class="sxs-lookup"><span data-stu-id="c4095-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="c4095-296">**NX_TFTP_INVALID_IP_VERSION** (0X0C) Nieprawidłowa wersja adresu IP</span><span class="sxs-lookup"><span data-stu-id="c4095-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="c4095-297">**NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu</span><span class="sxs-lookup"><span data-stu-id="c4095-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="c4095-298">**NX_TFTP_FAILED** (0xC2) odebrano nieznany kod TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="c4095-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Odebrano nieprawidłowy numer bloku</span><span class="sxs-lookup"><span data-stu-id="c4095-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="c4095-300">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-301">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="c4095-302">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c4095-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-303">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-303">Allowed From</span></span>

<span data-ttu-id="c4095-304">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-305">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="c4095-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="c4095-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="c4095-307">Napisz blok do pliku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-308">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="c4095-309">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-309">Description</span></span>

<span data-ttu-id="c4095-310">Ta usługa zapisuje blok 512-bajtowy do wcześniej otwartego pliku klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="c4095-311">Określenie bloku zawierającego mniej niż 512 bajtów sygnalizuje koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="c4095-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-312">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-312">Input Parameters</span></span>

- <span data-ttu-id="c4095-313">**tftp_client_ptr** Wskaźnik do bloku kontroli klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="c4095-314">**packet_ptr** Pakiet zawierający blok do zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="c4095-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="c4095-315">**WAIT_OPTION** Określa, jak długo usługa będzie czekać na zakończenie zapisu.</span><span class="sxs-lookup"><span data-stu-id="c4095-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="c4095-316">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4095-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="c4095-317">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4095-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="c4095-318">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="c4095-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="c4095-319">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer TFTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c4095-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="c4095-320">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na wysłanie potwierdzenia dla żądania zapisu przez serwer TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="c4095-321">**ip_type** Wskaż, którego protokołu IP użyć.</span><span class="sxs-lookup"><span data-stu-id="c4095-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="c4095-322">Prawidłowe opcje to IPv4 (4) lub IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="c4095-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-323">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-323">Return Values</span></span>

- <span data-ttu-id="c4095-324">**NX_SUCCESS** (0X00) pomyślne zapis bloku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="c4095-325">**NX_TFTP_NOT_OPEN** (0XC3) określony plik klienta nie jest otwarty do zapisu</span><span class="sxs-lookup"><span data-stu-id="c4095-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="c4095-326">**NX_TFTP_TIMEOUT** (0XC1) upłynął limit czasu oczekiwania na potwierdzenie serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="c4095-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="c4095-328">**NX_TFTP_NO_ACK_RECEIVED** (0X09) nie odebrano potwierdzenia z serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="c4095-329">**NX_TFTP_INVALID_IP_VERSION** (0X0C) Nieprawidłowa wersja adresu IP</span><span class="sxs-lookup"><span data-stu-id="c4095-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="c4095-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Odebrano nieprawidłowy adres serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="c4095-331">**NX_TFTP_CODE_ERROR** (0X05) otrzymał kod błędu</span><span class="sxs-lookup"><span data-stu-id="c4095-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="c4095-332">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-333">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="c4095-334">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c4095-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-335">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-335">Allowed From</span></span>

<span data-ttu-id="c4095-336">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-337">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="c4095-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="c4095-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="c4095-339">Przydziel pakiet do zapisu pliku klienta</span><span class="sxs-lookup"><span data-stu-id="c4095-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-340">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="c4095-341">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-341">Description</span></span>

<span data-ttu-id="c4095-342">Ta usługa przydziela pakiet UDP z określonej puli pakietów i tworzy miejsce dla 4-bajtowego nagłówka TFTP przed zwróceniem pakietu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c4095-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="c4095-343">Obiekt wywołujący może następnie utworzyć bufor do zapisu w pliku klienta.</span><span class="sxs-lookup"><span data-stu-id="c4095-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-344">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-344">Input Parameters</span></span>

- <span data-ttu-id="c4095-345">**pool_ptr** Wskaźnik do puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="c4095-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="c4095-346">**packet_ptr** Miejsce docelowe dla wskaźnika do przydzielnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="c4095-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="c4095-347">**WAIT_OPTION** Określa, jak długo usługa będzie oczekiwać na zakończenie przydzielenia pakietu.</span><span class="sxs-lookup"><span data-stu-id="c4095-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="c4095-348">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4095-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="c4095-349">**wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4095-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="c4095-350">**TX_WAIT_FOREVER** (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="c4095-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="c4095-351">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu zakończenia alokacji.</span><span class="sxs-lookup"><span data-stu-id="c4095-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="c4095-352">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na alokację pakietu.</span><span class="sxs-lookup"><span data-stu-id="c4095-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="c4095-353">**ip_type** Wskaż, którego protokołu IP użyć.</span><span class="sxs-lookup"><span data-stu-id="c4095-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="c4095-354">Prawidłowe opcje to IPv4 (4) lub IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="c4095-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-355">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-355">Return Values</span></span>

- <span data-ttu-id="c4095-356">Pomyślne przydzielenie pakietu **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c4095-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="c4095-357">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-358">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="c4095-359">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="c4095-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-360">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-360">Allowed From</span></span>

<span data-ttu-id="c4095-361">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-362">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="c4095-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="c4095-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="c4095-364">Ustawianie interfejsu fizycznego dla żądań TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-365">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="c4095-366">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-366">Description</span></span>

<span data-ttu-id="c4095-367">Ta usługa używa indeksu interfejsu wejściowego do ustawienia interfejsu fizycznego dla klienta TFTP do wysyłania i odbierania pakietów TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="c4095-368">Wartość domyślna to zero dla interfejsu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c4095-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="c4095-369">NetX Duo musi obsługiwać adresy wielodomowe (wersja 3.0 lub nowsza), aby można było korzystać z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-370">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-370">Input Parameters</span></span>

- <span data-ttu-id="c4095-371">**tftp_client_ptr** Wskaźnik do wystąpienia klienta TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="c4095-372">**if_index** Indeks interfejsu fizycznego do użycia</span><span class="sxs-lookup"><span data-stu-id="c4095-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-373">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-373">Return Values</span></span>

- <span data-ttu-id="c4095-374">**NX_SUCCESS** (0X00) pomyślnie ustawił interfejs (0X0B) nieprawidłowe dane wejściowe interfejsu</span><span class="sxs-lookup"><span data-stu-id="c4095-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="c4095-375">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-376">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="c4095-377">NX_TFTP_INVALID_INTERFACE (0x0B) nieprawidłowe dane wejściowe interfejsu</span><span class="sxs-lookup"><span data-stu-id="c4095-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-378">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-378">Allowed From</span></span>

<span data-ttu-id="c4095-379">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-380">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="c4095-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="c4095-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="c4095-382">Utwórz serwer TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-383">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c4095-384">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-384">Description</span></span>

<span data-ttu-id="c4095-385">Ta usługa tworzy serwer TFTP, który odpowiada na żądania klientów TFTP na porcie 69.</span><span class="sxs-lookup"><span data-stu-id="c4095-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="c4095-386">Serwer musi być uruchomiony przez kolejne wywołanie do *nxd_tftp_server_start*.</span><span class="sxs-lookup"><span data-stu-id="c4095-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4095-387">Aplikacja musi wykonać niektóre dostarczone wystąpienie adresu IP, pulę pakietów i wystąpienie nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="c4095-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="c4095-388">Ponadto należy włączyć protokół UDP przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4095-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-389">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-389">Input Parameters</span></span>

- <span data-ttu-id="c4095-390">**tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="c4095-391">**tftp_server_name** Nazwa tego wystąpienia serwera TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="c4095-392">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="c4095-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="c4095-393">**media_ptr** Wskaźnik na FileX wystąpienie nośnika.</span><span class="sxs-lookup"><span data-stu-id="c4095-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="c4095-394">**stack_ptr** Wskaźnik do obszaru stosu serwera TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="c4095-395">**stack_size** Liczba bajtów w stosie serwera TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="c4095-396">**pool_ptr** Wskaźnik do puli pakietów TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="c4095-397">Długość dostarczonej puli musi wynosić co najmniej 580 bajtów. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c4095-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="c4095-398"><sup>1</sup> część danych pakietu ma dokładnie 512 bajtów, ale rozmiar ładunku pakietu musi wynosić co najmniej 572 bajtów.</span><span class="sxs-lookup"><span data-stu-id="c4095-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="c4095-399">Pozostałe bajty są używane dla nagłówków UDP, IPv6 i Ethernet oraz potencjalne bajty końcowe wymagane przez sterownik do wyrównania.</span><span class="sxs-lookup"><span data-stu-id="c4095-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-400">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-400">Return Values</span></span>

- <span data-ttu-id="c4095-401">**NX_SUCCESS** (0X00) pomyślne utworzenie serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="c4095-402">Pula pakietów **NX_TFTP_POOL_ERROR** (0xC6) ma rozmiar pakietu mniejszy niż 560 bajtów</span><span class="sxs-lookup"><span data-stu-id="c4095-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="c4095-403">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-404">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-404">Allowed From</span></span>

<span data-ttu-id="c4095-405">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-406">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="c4095-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="c4095-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="c4095-408">Usuń serwer TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-409">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c4095-410">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-410">Description</span></span>

<span data-ttu-id="c4095-411">Ta usługa usuwa wcześniej utworzony serwer TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-412">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-412">Input Parameters</span></span>

- <span data-ttu-id="c4095-413">**tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-414">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-414">Return Values</span></span>

- <span data-ttu-id="c4095-415">**NX_SUCCESS** (0X00) pomyślne usunięcie serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="c4095-416">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-417">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-418">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-418">Allowed From</span></span>

<span data-ttu-id="c4095-419">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-420">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="c4095-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="c4095-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="c4095-422">Uruchom serwer TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-423">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c4095-424">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-424">Description</span></span>

<span data-ttu-id="c4095-425">Ta usługa uruchamia wcześniej utworzony serwer TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-426">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-426">Input Parameters</span></span>

- <span data-ttu-id="c4095-427">**tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-428">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-428">Return Values</span></span>

- <span data-ttu-id="c4095-429">**NX_SUCCESS** (0X00) pomyślne uruchomienie serwera</span><span class="sxs-lookup"><span data-stu-id="c4095-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="c4095-430">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="c4095-431">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-431">Allowed From</span></span>

<span data-ttu-id="c4095-432">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-433">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="c4095-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="c4095-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="c4095-435">Zatrzymaj serwer TFTP</span><span class="sxs-lookup"><span data-stu-id="c4095-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c4095-436">Prototype</span><span class="sxs-lookup"><span data-stu-id="c4095-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c4095-437">Opis</span><span class="sxs-lookup"><span data-stu-id="c4095-437">Description</span></span>

<span data-ttu-id="c4095-438">Ta usługa zatrzyma wcześniej utworzony serwer TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c4095-439">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c4095-439">Input Parameters</span></span>

- <span data-ttu-id="c4095-440">**tftp_server_ptr** Wskaźnik do bloku sterowania serwerem TFTP.</span><span class="sxs-lookup"><span data-stu-id="c4095-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c4095-441">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c4095-441">Return Values</span></span>

- <span data-ttu-id="c4095-442">Zakończono pomyślne zatrzymywanie serwera **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c4095-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="c4095-443">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c4095-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="c4095-444">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi</span><span class="sxs-lookup"><span data-stu-id="c4095-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c4095-445">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c4095-445">Allowed From</span></span>

<span data-ttu-id="c4095-446">Wątki</span><span class="sxs-lookup"><span data-stu-id="c4095-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c4095-447">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4095-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```