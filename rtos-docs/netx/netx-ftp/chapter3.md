---
title: Rozdział 3 — Opis usług FTP usługi Azure RTO NetX
description: Ten rozdział zawiera opis wszystkich usług FTP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822626"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="e15cb-103">Rozdział 3 — Opis usług FTP usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="e15cb-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="e15cb-104">Ten rozdział zawiera opis wszystkich usług FTP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="e15cb-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="e15cb-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e15cb-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="e15cb-106">**nx_ftp_client_connect**: *łączenie z serwerem FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="e15cb-107">**nx_ftp_client_create**: *Tworzenie wystąpienia klienta FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="e15cb-108">**nx_ftp_client_delete**: *usuwanie wystąpienia klienta FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="e15cb-109">**nx_ftp_client_directory_create**: *Utwórz katalog na serwerze*</span><span class="sxs-lookup"><span data-stu-id="e15cb-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="e15cb-110">**nx_ftp_client_directory_default_set**: *Ustaw domyślny katalog na serwerze*</span><span class="sxs-lookup"><span data-stu-id="e15cb-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="e15cb-111">**nx_ftp_client_directory_delete**: *usuwanie katalogu na serwerze*</span><span class="sxs-lookup"><span data-stu-id="e15cb-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="e15cb-112">**nx_ftp_client_directory_listing_get**: *Pobieranie listy katalogów z serwera*</span><span class="sxs-lookup"><span data-stu-id="e15cb-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="e15cb-113">**nx_ftp_client_directory_listing_continue**: *Kontynuuj Wyświetlanie listy katalogów z serwera*</span><span class="sxs-lookup"><span data-stu-id="e15cb-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="e15cb-114">**nx_ftp_client_disconnect**: *Rozłącz z serwerem FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="e15cb-115">**nx_ftp_client_file_close**: *Zamknij plik klienta*</span><span class="sxs-lookup"><span data-stu-id="e15cb-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="e15cb-116">**nx_ftp_client_file_delete**: *usuwanie pliku na serwerze*</span><span class="sxs-lookup"><span data-stu-id="e15cb-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="e15cb-117">**nx_ftp_client_file_open**: *Otwórz plik klienta*</span><span class="sxs-lookup"><span data-stu-id="e15cb-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="e15cb-118">**nx_ftp_client_file_read**: *Odczytaj z pliku*</span><span class="sxs-lookup"><span data-stu-id="e15cb-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="e15cb-119">**nx_ftp_client_file_rename**: *Zmień nazwę pliku na serwerze*</span><span class="sxs-lookup"><span data-stu-id="e15cb-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="e15cb-120">**nx_ftp_client_file_write**: *Zapisz do pliku*</span><span class="sxs-lookup"><span data-stu-id="e15cb-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="e15cb-121">**nx_ftp_server_create**: *Utwórz serwer FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="e15cb-122">**nx_ftp_server_delete**: *usuwanie serwera FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="e15cb-123">**nx_ftp_server_start**: *Uruchom serwer FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="e15cb-124">**nx_ftp_server_stop**: *ZAtrzymywanie serwera FTP*</span><span class="sxs-lookup"><span data-stu-id="e15cb-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="e15cb-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="e15cb-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="e15cb-126">Nawiązywanie połączenia z serwerem FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-128">Description</span></span>

<span data-ttu-id="e15cb-129">Ta usługa nawiązuje połączenie utworzonego wcześniej wystąpienia klienta FTP z serwerem FTP przy użyciu podanego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-130">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-130">Input Parameters</span></span>

- <span data-ttu-id="e15cb-131">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-132">**server_IP**: adres IP serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="e15cb-133">**Nazwa użytkownika**: Nazwa użytkownika klienta na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e15cb-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="e15cb-134">**hasło**: hasło klienta na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e15cb-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="e15cb-135">**WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać na połączenie z klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="e15cb-136">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-137">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-138">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-139">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-140">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-140">Return Values</span></span>

- <span data-ttu-id="e15cb-141">**NX_SUCCESS**: (0X00) POMYŚLNE połączenie FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="e15cb-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) nie otrzymał odpowiedzi 22X (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="e15cb-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) nie otrzymał odpowiedzi 23X (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="e15cb-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) nie otrzymał odpowiedzi 33X (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="e15cb-145">**NX_FTP_NOT_DISCONNECTED**: klient (0xD4) jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="e15cb-146">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik Inout.</span><span class="sxs-lookup"><span data-stu-id="e15cb-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="e15cb-147">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="e15cb-148">NX_IP_ADDRESS_ERROR: (0x21) nieprawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-149">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-149">Allowed From</span></span>

<span data-ttu-id="e15cb-150">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="e15cb-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="e15cb-152">nx_ftp_client_create</span></span>

<span data-ttu-id="e15cb-153">Tworzenie wystąpienia klienta FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-154">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="e15cb-155">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-155">Description</span></span>

<span data-ttu-id="e15cb-156">Ta usługa tworzy wystąpienie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-157">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-157">Input Parameters</span></span>

- <span data-ttu-id="e15cb-158">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-159">**ftp_client_name**: Nazwa klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="e15cb-160">**ip_ptr**: wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="e15cb-161">**window_size**: anonsowany rozmiar okna dla gniazda TCP tego klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="e15cb-162">**pool_ptr**: wskaźnik do domyślnej puli pakietów dla tego klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="e15cb-163">Należy pamiętać, że minimalny ładunek pakietu musi być wystarczająco duży, aby pomieścić pełną ścieżkę i nazwę pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-164">Return Values</span></span>

- <span data-ttu-id="e15cb-165">**NX_SUCCESS**: (0X00) pomyślne utworzenie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="e15cb-166">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP, adresu IP lub puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="e15cb-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="e15cb-167">wskaźnik hasła.</span><span class="sxs-lookup"><span data-stu-id="e15cb-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-168">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-168">Allowed From</span></span>

<span data-ttu-id="e15cb-169">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="e15cb-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="e15cb-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="e15cb-172">Usuwanie wystąpienia klienta FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="e15cb-174">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-174">Description</span></span>

<span data-ttu-id="e15cb-175">Ta usługa usuwa wystąpienie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-176">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-176">Input Parameters</span></span>

- <span data-ttu-id="e15cb-177">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-178">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-178">Return Values</span></span>

- <span data-ttu-id="e15cb-179">**NX_SUCCESS**: (0X00) pomyślne usunięcie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="e15cb-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) błąd usuwania klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="e15cb-181">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-182">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-183">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-183">Allowed From</span></span>

<span data-ttu-id="e15cb-184">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="e15cb-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="e15cb-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="e15cb-187">Tworzenie katalogu na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-189">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-189">Description</span></span>

<span data-ttu-id="e15cb-190">Ta usługa tworzy określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-191">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-191">Input Parameters</span></span>

- <span data-ttu-id="e15cb-192">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-193">**directory_name**: Nazwa katalogu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="e15cb-194">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na utworzenie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="e15cb-195">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-196">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-197">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-198">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-199">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-199">Return Values</span></span>

- <span data-ttu-id="e15cb-200">**NX_SUCCESS**: (0X00) pomyślne utworzenie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="e15cb-201">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="e15cb-203">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="e15cb-204">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-205">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-205">Allowed From</span></span>

<span data-ttu-id="e15cb-206">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="e15cb-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="e15cb-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="e15cb-209">Ustawianie domyślnego katalogu na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-210">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-211">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-211">Description</span></span>

<span data-ttu-id="e15cb-212">Ta usługa ustawia domyślny katalog na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="e15cb-213">Ten domyślny katalog ma zastosowanie tylko do połączenia tego klienta.</span><span class="sxs-lookup"><span data-stu-id="e15cb-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-214">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-214">Input Parameters</span></span>

- <span data-ttu-id="e15cb-215">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-216">**directory_path**: Nazwa ścieżki katalogu do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="e15cb-217">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na domyślny zestaw katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="e15cb-218">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-219">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-220">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-221">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-222">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-222">Return Values</span></span>

- <span data-ttu-id="e15cb-223">**NX_SUCCESS**: (0X00) pomyślne ustawienie domyślne protokołu FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="e15cb-224">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="e15cb-226">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="e15cb-227">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-228">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-228">Allowed From</span></span>

<span data-ttu-id="e15cb-229">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-230">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="e15cb-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="e15cb-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="e15cb-232">Usuwanie katalogu na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-233">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-234">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-234">Description</span></span>

<span data-ttu-id="e15cb-235">Ta usługa usuwa określony katalog na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-236">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-236">Input Parameters</span></span>

- <span data-ttu-id="e15cb-237">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-238">**directory_name**: Nazwa katalogu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="e15cb-239">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na usunięcie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="e15cb-240">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-241">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-242">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-243">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-244">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-244">Return Values</span></span>

- <span data-ttu-id="e15cb-245">**NX_SUCCESS**: (0X00) pomyślne usunięcie katalogu FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="e15cb-246">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="e15cb-248">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="e15cb-249">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-250">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-250">Allowed From</span></span>

<span data-ttu-id="e15cb-251">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-252">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="e15cb-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="e15cb-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="e15cb-254">Pobierz listę katalogów z serwera FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-255">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-256">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-256">Description</span></span>

<span data-ttu-id="e15cb-257">Ta usługa pobiera zawartość określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="e15cb-258">Dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="e15cb-259">Każdy wpis jest oddzielony przez &lt; kombinację CR/LF \.</span><span class="sxs-lookup"><span data-stu-id="e15cb-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="e15cb-260">***Nx_ftp_client_directory_listing_continue***: należy wywołać, aby ukończyć operację pobierania katalogu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-261">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-261">Input Parameters</span></span>

- <span data-ttu-id="e15cb-262">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-263">**directory_name**: Nazwa katalogu, do którego ma zostać pobrana zawartość.</span><span class="sxs-lookup"><span data-stu-id="e15cb-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="e15cb-264">**packet_ptr**: wskaźnik do docelowego wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="e15cb-265">Jeśli to się powiedzie, ładunek pakietu będzie zawierać jeden lub więcej wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="e15cb-266">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na listę katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="e15cb-267">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-268">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-269">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-270">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-271">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-271">Return Values</span></span>

- <span data-ttu-id="e15cb-272">**NX_SUCCESS**: (0x00) pomyślna lista katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="e15cb-273">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-274">**NX_NOT_ENABLED**: (0x14) nie włączono usługi (IPv6)</span><span class="sxs-lookup"><span data-stu-id="e15cb-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="e15cb-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) nie otrzymał odpowiedzi 1XX (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="e15cb-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="e15cb-277">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-278">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-279">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-279">Allowed From</span></span>

<span data-ttu-id="e15cb-280">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-281">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="e15cb-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="e15cb-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="e15cb-283">Kontynuuj Wyświetlanie listy katalogów z serwera FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-284">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-285">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-285">Description</span></span>

<span data-ttu-id="e15cb-286">Ta usługa kontynuuje pobieranie zawartości określonego katalogu na serwerze FTP, który jest połączony z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="e15cb-287">Powinien być bezpośrednio poprzedzony wywołaniem ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="e15cb-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="e15cb-288">Jeśli to się powiedzie, dostarczony wskaźnik pakietu będzie zawierać jeden lub więcej wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="e15cb-289">Ta procedura powinna być wywoływana do momentu otrzymania NX_FTP_END_OF_LISTING stanu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-290">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-290">Input Parameters</span></span>

- <span data-ttu-id="e15cb-291">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-292">**packet_ptr**: wskaźnik do docelowego wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="e15cb-293">Jeśli to się powiedzie, ładunek pakietu będzie zawierać co najmniej jeden wpis w katalogu oddzielony znakiem &lt; CR/LF &gt; .</span><span class="sxs-lookup"><span data-stu-id="e15cb-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="e15cb-294">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na listę katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="e15cb-295">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-296">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-297">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-298">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-299">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-299">Return Values</span></span>

- <span data-ttu-id="e15cb-300">**NX_SUCCESS**: (0x00) pomyślna lista katalogów FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="e15cb-301">**NX_FTP_END_OF_LISTING**: (0XD8) nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="e15cb-302">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="e15cb-304">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-305">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-306">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-306">Allowed From</span></span>

<span data-ttu-id="e15cb-307">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-308">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="e15cb-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="e15cb-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="e15cb-310">Rozłącz z serwerem FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-311">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-312">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-312">Description</span></span>

<span data-ttu-id="e15cb-313">Ta usługa rozłącza wcześniej ustanowione połączenie z serwerem FTP z określonym klientem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-314">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-314">Input Parameters</span></span>

- <span data-ttu-id="e15cb-315">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-316">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na rozłączenie klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="e15cb-317">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-318">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-319">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-320">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-321">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-321">Return Values</span></span>

- <span data-ttu-id="e15cb-322">**NX_SUCCESS**: (0X00) pomyślne rozłączenie FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="e15cb-323">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="e15cb-325">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-326">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-327">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-327">Allowed From</span></span>

<span data-ttu-id="e15cb-328">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-329">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="e15cb-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="e15cb-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="e15cb-331">Zamknij plik klienta</span><span class="sxs-lookup"><span data-stu-id="e15cb-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-332">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-333">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-333">Description</span></span>

<span data-ttu-id="e15cb-334">Ta usługa zamyka poprzednio otwarty plik na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-335">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-335">Input Parameters</span></span>

- <span data-ttu-id="e15cb-336">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-337">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na zamknięcie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="e15cb-338">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-339">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-340">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-341">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-342">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-342">Return Values</span></span>

- <span data-ttu-id="e15cb-343">**NX_SUCCESS**: (0X00) pomyślne zamknięcie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="e15cb-344">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-345">**NX_FTP_NOT_OPEN (0xD5)**: plik nie jest otwarty; nie można zamknąć</span><span class="sxs-lookup"><span data-stu-id="e15cb-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="e15cb-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="e15cb-347">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-348">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-349">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-349">Allowed From</span></span>

<span data-ttu-id="e15cb-350">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-351">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="e15cb-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="e15cb-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="e15cb-353">Usuń plik na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-354">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-355">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-355">Description</span></span>

<span data-ttu-id="e15cb-356">Ta usługa usuwa określony plik na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-357">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-357">Input Parameters</span></span>

- <span data-ttu-id="e15cb-358">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-359">**file_name**: nazwa pliku do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="e15cb-360">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na usunięcie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="e15cb-361">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-362">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-363">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-364">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-365">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-365">Return Values</span></span>

- <span data-ttu-id="e15cb-366">**NX_SUCCESS**: (0X00) pomyślne usunięcie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="e15cb-367">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="e15cb-369">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-370">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-371">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-371">Allowed From</span></span>

<span data-ttu-id="e15cb-372">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-373">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="e15cb-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="e15cb-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="e15cb-375">Otwiera plik na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-376">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-377">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-377">Description</span></span>

<span data-ttu-id="e15cb-378">Ta usługa otwiera określony plik — do odczytu lub zapisu — na serwerze FTP, który został wcześniej połączony z określonym wystąpieniem klienta.</span><span class="sxs-lookup"><span data-stu-id="e15cb-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-379">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-379">Input Parameters</span></span>

- <span data-ttu-id="e15cb-380">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-381">**file_name**: nazwa pliku do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="e15cb-382">**open_type**: **NX_FTP_OPEN_FOR_READ** lub **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="e15cb-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="e15cb-383">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na otwarcie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="e15cb-384">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-385">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-386">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-387">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-388">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-388">Return Values</span></span>

- <span data-ttu-id="e15cb-389">**NX_SUCCESS**: (0X00) pomyślne otwarcie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="e15cb-390">**NX_OPTION_ERROR**: (0X0a) Nieprawidłowy typ otwarty.</span><span class="sxs-lookup"><span data-stu-id="e15cb-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="e15cb-391">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-392">**NX_FTP_NOT_CLOSED**: (0XD6) klient FTP jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="e15cb-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="e15cb-393">**NX_NO_FREE_PORTS**: (0X45) Brak dostępnych portów TCP do przypisania</span><span class="sxs-lookup"><span data-stu-id="e15cb-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="e15cb-394">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-395">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-396">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-396">Allowed From</span></span>

<span data-ttu-id="e15cb-397">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-398">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="e15cb-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="e15cb-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="e15cb-400">Odczytaj z pliku</span><span class="sxs-lookup"><span data-stu-id="e15cb-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-401">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-402">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-402">Description</span></span>

<span data-ttu-id="e15cb-403">Ta usługa odczytuje pakiet z wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="e15cb-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="e15cb-404">Powinien być wywoływany kilkukrotnie do momentu otrzymania stanu NX_FTP_END_OF_FILE.</span><span class="sxs-lookup"><span data-stu-id="e15cb-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="e15cb-405">Należy zauważyć, że obiekt wywołujący nie przydziela pakietu dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="e15cb-406">Musi on dostarczyć jedynie wskaźnik do wskaźnika pakietu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="e15cb-407">Ta usługa zaktualizuje ten wskaźnik pakietu, aby wskazywał pakiet pobrany z kolejki odbioru gniazda.</span><span class="sxs-lookup"><span data-stu-id="e15cb-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="e15cb-408">Jeśli zwracany jest stan pomyślne, oznacza to, że dostępny jest pakiet i jest on odpowiedzialny za wydanie pakietu po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="e15cb-409">Jeśli zwracany jest stan o wartości innej niż zero (stan błędu lub NX_FTP_END_OF_FILE), obiekt wywołujący nie zwolni pakietu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="e15cb-410">W przeciwnym razie zostanie wygenerowany błąd, gdy wskaźnik pakietu ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="e15cb-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-411">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-411">Input Parameters</span></span>

- <span data-ttu-id="e15cb-412">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-413">**packet_ptr**: wskaźnik do miejsca docelowego dla wskaźnika pakietu danych pobranego z kolejki.</span><span class="sxs-lookup"><span data-stu-id="e15cb-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="e15cb-414">Jeśli to się powiedzie, dane pakietu zawierają część lub wszystkie pliki.</span><span class="sxs-lookup"><span data-stu-id="e15cb-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="e15cb-415">**WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać na odczytanie pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="e15cb-416">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-417">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-418">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-419">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-420">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-420">Return Values</span></span>

- <span data-ttu-id="e15cb-421">**NX_SUCCESS**: (0X00) pomyślne odczytanie pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="e15cb-422">**NX_FTP_NOT_OPEN**: (0XD5) klient FTP nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="e15cb-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="e15cb-423">**NX_FTP_END_OF_FILE**: (0XD7) koniec warunku pliku.</span><span class="sxs-lookup"><span data-stu-id="e15cb-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="e15cb-424">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-425">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-426">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-426">Allowed From</span></span>

<span data-ttu-id="e15cb-427">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-428">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

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

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="e15cb-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="e15cb-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="e15cb-430">Zmień nazwę pliku na serwerze FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-432">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-432">Description</span></span>

<span data-ttu-id="e15cb-433">Ta usługa zmienia nazwę pliku na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-434">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-434">Input Parameters</span></span>

- <span data-ttu-id="e15cb-435">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-436">**Nazwa** pliku: Bieżąca nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="e15cb-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="e15cb-437">**new_filename**: Nowa nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="e15cb-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="e15cb-438">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na zmianę nazwy pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="e15cb-439">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-440">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-441">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-442">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-443">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-443">Return Values</span></span>

- <span data-ttu-id="e15cb-444">**NX_SUCCESS**: (0x00) pomyślna zmiana nazwy pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="e15cb-445">**NX_FTP_NOT_CONNECTED**: (0XD3) klient FTP nie jest połączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="e15cb-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) nie otrzymał odpowiedzi 3xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="e15cb-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) nie otrzymał odpowiedzi 2xx (ok)</span><span class="sxs-lookup"><span data-stu-id="e15cb-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="e15cb-448">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-449">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-450">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-450">Allowed From</span></span>

<span data-ttu-id="e15cb-451">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-452">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="e15cb-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="e15cb-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="e15cb-454">Zapisz do pliku</span><span class="sxs-lookup"><span data-stu-id="e15cb-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-455">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e15cb-456">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-456">Description</span></span>

<span data-ttu-id="e15cb-457">Ta usługa zapisuje pakiet danych do wcześniej otwartego pliku na serwerze FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-458">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-458">Input Parameters</span></span>

- <span data-ttu-id="e15cb-459">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-460">**packet_ptr**: wskaźnik pakietu zawierający dane do zapisu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="e15cb-461">**WAIT_OPTION**: określa, jak długo usługa będzie czekać na zapis pliku klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="e15cb-462">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e15cb-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="e15cb-463">**wartość limitu czasu**: (od 0X00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e15cb-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="e15cb-464">**TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, aż serwer FTP odpowie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e15cb-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="e15cb-465">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-466">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-466">Return Values</span></span>

- <span data-ttu-id="e15cb-467">**NX_SUCCESS**: (0X00) pomyślne zapis pliku FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="e15cb-468">**NX_FTP_NOT_OPEN**: (0XD5) klient FTP nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="e15cb-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="e15cb-469">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-470">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-471">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-471">Allowed From</span></span>

<span data-ttu-id="e15cb-472">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-473">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="e15cb-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="e15cb-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="e15cb-475">Włącz lub wyłącz tryb transferu pasywnego</span><span class="sxs-lookup"><span data-stu-id="e15cb-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-476">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="e15cb-477">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-477">Description</span></span>

<span data-ttu-id="e15cb-478">Ta usługa włącza tryb transferu pasywnego, jeśli passive_mode_enabled dane wejściowe są ustawione na NX_TRUE na wcześniej utworzonym wystąpieniu klienta FTP, tak że kolejne wywołania odczytu lub zapisu plików (RETR, STOR) lub pobrania listy katalogów (NLST) są wykonywane w trybie transferu.</span><span class="sxs-lookup"><span data-stu-id="e15cb-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="e15cb-479">Aby wyłączyć transfer w trybie pasywnym i wrócić do domyślnego zachowania aktywnego trybu transferu, Wywołaj tę funkcję z zestawem danych wejściowych passive_mode_enabled, aby NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="e15cb-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-480">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-480">Input Parameters</span></span>

- <span data-ttu-id="e15cb-481">**ftp_client_ptr**: wskaźnik do bloku kontroli klienta FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="e15cb-482">**passive_mode_enabled**:</span><span class="sxs-lookup"><span data-stu-id="e15cb-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="e15cb-483">Jeśli ustawiona na NX_TRUE, tryb pasywny jest włączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="e15cb-484">Jeśli ustawiona na NX_FALSE, tryb pasywny jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="e15cb-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-485">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-485">Return Values</span></span>

- <span data-ttu-id="e15cb-486">**NX_SUCCESS**: (0X00) pomyślnie ustawiono tryb pasywny.</span><span class="sxs-lookup"><span data-stu-id="e15cb-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="e15cb-487">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-488">NX_INVALID_PARAMETERS: (0x4D) nieprawidłowe dane wejściowe bez wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e15cb-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-489">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-489">Allowed From</span></span>

<span data-ttu-id="e15cb-490">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-491">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="e15cb-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="e15cb-492">nx_ftp_server_create</span></span>

<span data-ttu-id="e15cb-493">Utwórz serwer FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-494">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="e15cb-495">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-495">Description</span></span>

<span data-ttu-id="e15cb-496">Ta usługa tworzy wystąpienie serwera FTP w określonym i wcześniej utworzonym wystąpieniu adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="e15cb-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="e15cb-497">Zwróć uwagę na to, że serwer FTP musi zostać uruchomiony z wywołaniem do ***nx_ftp_server_start*** , aby rozpocząć operację.</span><span class="sxs-lookup"><span data-stu-id="e15cb-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-498">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-498">Input Parameters</span></span>

- <span data-ttu-id="e15cb-499">**ftp_server_ptr**: wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="e15cb-500">**ftp_server_name**: Nazwa serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="e15cb-501">**ip_ptr**: wskaźnik do skojarzonego wystąpienia adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="e15cb-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="e15cb-502">Należy pamiętać, że dla wystąpienia IP może istnieć tylko jeden serwer FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="e15cb-503">**media_ptr**: wskaźnik do skojarzonego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="e15cb-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="e15cb-504">**stack_ptr**: wskaźnik do pamięci dla obszaru stosu wewnętrznego wątku serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="e15cb-505">**stack_size**: rozmiar obszaru stosu określonego przez *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="e15cb-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="e15cb-506">**pool_ptr**: wskaźnik do domyślnej puli pakietów NetX.</span><span class="sxs-lookup"><span data-stu-id="e15cb-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="e15cb-507">Zwróć uwagę, że rozmiar ładunku pakietów w puli musi być wystarczająco duży, aby pomieścić największą nazwę pliku/ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="e15cb-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="e15cb-508">**ftp_login**: wskaźnik funkcji do funkcji logowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e15cb-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="e15cb-509">Ta funkcja jest podana nazwa użytkownika i hasło z klienta żądającego połączenia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="e15cb-510">Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="e15cb-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="e15cb-511">**ftp_logout**: wskaźnik funkcji do funkcji wylogowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e15cb-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="e15cb-512">Ta funkcja jest podana nazwa użytkownika i hasło z klienta żądającego odłączenia.</span><span class="sxs-lookup"><span data-stu-id="e15cb-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="e15cb-513">Jeśli jest to prawidłowe, funkcja logowania aplikacji powinna zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="e15cb-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-514">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-514">Return Values</span></span>

- <span data-ttu-id="e15cb-515">**NX_SUCCESS**: (0X00) pomyślne utworzenie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="e15cb-516">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-517">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-517">Allowed From</span></span>

<span data-ttu-id="e15cb-518">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-519">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="e15cb-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="e15cb-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="e15cb-521">Usuń serwer FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-522">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="e15cb-523">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-523">Description</span></span>

<span data-ttu-id="e15cb-524">Ta usługa usuwa wcześniej utworzone wystąpienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-525">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-525">Input Parameters</span></span>

- <span data-ttu-id="e15cb-526">**ftp_server_ptr**: wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-527">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-527">Return Values</span></span>

- <span data-ttu-id="e15cb-528">**NX_SUCCESS**: (0X00) pomyślne usunięcie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="e15cb-529">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-530">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-531">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-531">Allowed From</span></span>

<span data-ttu-id="e15cb-532">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-533">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="e15cb-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="e15cb-534">nx_ftp_server_start</span></span>

<span data-ttu-id="e15cb-535">Uruchom serwer FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-536">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="e15cb-537">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-537">Description</span></span>

<span data-ttu-id="e15cb-538">Ta usługa uruchamia wcześniej utworzone wystąpienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-539">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-539">Input Parameters</span></span>

- <span data-ttu-id="e15cb-540">**ftp_server_ptr**: wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-541">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-541">Return Values</span></span>

- <span data-ttu-id="e15cb-542">**NX_SUCCESS**: (0X00) pomyślne uruchomienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="e15cb-543">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-544">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-544">Allowed From</span></span>

<span data-ttu-id="e15cb-545">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-546">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="e15cb-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="e15cb-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="e15cb-548">Zatrzymaj serwer FTP</span><span class="sxs-lookup"><span data-stu-id="e15cb-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e15cb-549">Prototype</span><span class="sxs-lookup"><span data-stu-id="e15cb-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="e15cb-550">Opis</span><span class="sxs-lookup"><span data-stu-id="e15cb-550">Description</span></span>

<span data-ttu-id="e15cb-551">Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e15cb-552">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e15cb-552">Input Parameters</span></span>

- <span data-ttu-id="e15cb-553">**ftp_server_ptr**: wskaźnik do bloku sterowania serwerem FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e15cb-554">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e15cb-554">Return Values</span></span>

- <span data-ttu-id="e15cb-555">**NX_SUCCESS**: (0X00) pomyślne zatrzymanie serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="e15cb-556">NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik FTP.</span><span class="sxs-lookup"><span data-stu-id="e15cb-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="e15cb-557">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e15cb-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e15cb-558">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e15cb-558">Allowed From</span></span>

<span data-ttu-id="e15cb-559">Wątki</span><span class="sxs-lookup"><span data-stu-id="e15cb-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e15cb-560">Przykład</span><span class="sxs-lookup"><span data-stu-id="e15cb-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
