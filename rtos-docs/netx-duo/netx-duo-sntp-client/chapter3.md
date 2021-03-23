---
title: Rozdział 3 — Opis usług klienta usługi Azure RTO NetX Duo (SNTP)
description: Ten rozdział zawiera opis wszystkich usług klienta SNTP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821649"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="18948-103">Rozdział 3 — Opis usług klienta usługi Azure RTO NetX Duo (SNTP)</span><span class="sxs-lookup"><span data-stu-id="18948-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="18948-104">Ten rozdział zawiera opis wszystkich usług klienta usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="18948-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="18948-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="18948-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="18948-106">**nx_sntp_client_create**: *Tworzenie klienta SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="18948-107">**nx_sntp_client_delete**: *Usuwanie klienta SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="18948-108">**nx_sntp_client_get_local_time**: *pobieranie czasu lokalnego klienta SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="18948-109">**nx_sntp_client_get_local_time_extended**: *pobieranie czasu lokalnego klienta SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="18948-110">**nx_sntp_client_initialize_broadcast**: *zainicjuj klienta dla operacji emisji IPv4*</span><span class="sxs-lookup"><span data-stu-id="18948-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="18948-111">**nxd_sntp_client_initialize_broadcast**: *zainicjuj klienta dla operacji emisji IPv6 lub IPv4*</span><span class="sxs-lookup"><span data-stu-id="18948-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="18948-112">**nx_sntp_client_initialize_unicast**: *zainicjuj klienta dla operacji IPv4 emisji pojedynczej*</span><span class="sxs-lookup"><span data-stu-id="18948-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="18948-113">**nxd_sntp_client_initialize_unicast**: *zainicjuj klienta dla operacji IPv4 lub IPv6 emisji pojedynczej*</span><span class="sxs-lookup"><span data-stu-id="18948-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="18948-114">**nx_sntp_client_receiving_udpates**: *klient otrzymuje obecnie prawidłowe aktualizacje SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="18948-115">**nx_sntp_client_request_unicast_time**: *Wyślij żądanie emisji pojedynczej bezpośrednio do serwera NTP*</span><span class="sxs-lookup"><span data-stu-id="18948-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="18948-116">**nx_sntp_client_run_broadcast**: *Uruchamianie klienta w trybie emisji*</span><span class="sxs-lookup"><span data-stu-id="18948-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="18948-117">**nx_sntp_client_run_unicast**: *Uruchamianie klienta w trybie emisji pojedynczej*</span><span class="sxs-lookup"><span data-stu-id="18948-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="18948-118">**nx_sntp_client_set_local_time**: *Ustaw początkowy czas lokalny klienta SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="18948-119">**nx_sntp_client_set_time_update_notify**: *Ustaw wywołanie ZWROTne aktualizacji SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="18948-120">**nx_sntp_client_stop**: *Zatrzymywanie wątku klienta SNTP*</span><span class="sxs-lookup"><span data-stu-id="18948-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="18948-121">**nx_sntp_client_utility_display_date_and_time**: *Wyświetlanie czasu NTP w sekundach*</span><span class="sxs-lookup"><span data-stu-id="18948-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="18948-122">**nx_sntp_client_utility_msecs_to_fraction**: *konwertowanie MILISEKUND na składnik NTP*</span><span class="sxs-lookup"><span data-stu-id="18948-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="18948-123">**nx_sntp_client_utility_usecs_to_fraction**: *Konwertuj mikrosekundy na składnik ułamka NTP*</span><span class="sxs-lookup"><span data-stu-id="18948-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="18948-124">**nx_sntp_client_utility_fraction_to_usecs**: *konwertowanie składnika częściowego NTP na mikrosekundy*</span><span class="sxs-lookup"><span data-stu-id="18948-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="18948-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="18948-125">nx_sntp_client_create</span></span>

<span data-ttu-id="18948-126">Tworzenie klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="18948-128">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-128">Description</span></span>

<span data-ttu-id="18948-129">Ta usługa tworzy wystąpienie klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-130">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-130">Input Parameters</span></span>

- <span data-ttu-id="18948-131">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-132">**ip_ptr** Wskaźnik do wystąpienia adresu IP klienta</span><span class="sxs-lookup"><span data-stu-id="18948-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="18948-133">**iface_index** Indeksowanie do interfejsu sieciowego SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="18948-134">**packet_pool_ptr** Wskaźnik do puli pakietów klienta</span><span class="sxs-lookup"><span data-stu-id="18948-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="18948-135">**leap_second_handler** Wywołanie zwrotne dla odpowiedzi aplikacji w trakcie oczekiwania na sekundę</span><span class="sxs-lookup"><span data-stu-id="18948-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="18948-136">**kiss_of_death_handler** Wywołanie zwrotne dla odpowiedzi aplikacji do odebrania pakietu zgonu</span><span class="sxs-lookup"><span data-stu-id="18948-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="18948-137">**random_number_generator** Wywołanie zwrotne do usługi generatora liczb losowych</span><span class="sxs-lookup"><span data-stu-id="18948-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-138">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-138">Return Values</span></span>

- <span data-ttu-id="18948-139">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="18948-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="18948-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0XD2A) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="18948-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="18948-141">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-142">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="18948-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-143">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-143">Allowed From</span></span>

<span data-ttu-id="18948-144">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="18948-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="18948-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="18948-147">Usuwanie klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="18948-149">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-149">Description</span></span>

<span data-ttu-id="18948-150">Ta usługa usuwa wystąpienie klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-151">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-151">Input Parameters</span></span>

- <span data-ttu-id="18948-152">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-153">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-153">Return Values</span></span>

- <span data-ttu-id="18948-154">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="18948-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="18948-155">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-156">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-157">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-157">Allowed From</span></span>

<span data-ttu-id="18948-158">Wątki</span><span class="sxs-lookup"><span data-stu-id="18948-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="18948-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="18948-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="18948-161">Pobieranie czasu lokalnego klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-162">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="18948-163">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-163">Description</span></span>

<span data-ttu-id="18948-164">Ta usługa Pobiera czas lokalny klienta SNTP z wejściem wskaźnika buforu opcji w celu odbierania danych w formacie ciągu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="18948-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="18948-165">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="18948-165">This service is deprecated.</span></span> <span data-ttu-id="18948-166">Deweloperzy są zachęcani do migracji do *nx_sntp_client_get_local_time_extended*().</span><span class="sxs-lookup"><span data-stu-id="18948-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-167">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-167">Input Parameters</span></span>

- <span data-ttu-id="18948-168">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-169">**sekund** Wskaźnik na czas lokalny w sekundach</span><span class="sxs-lookup"><span data-stu-id="18948-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="18948-170">**ułamek** Składnik lokalnej części czasu</span><span class="sxs-lookup"><span data-stu-id="18948-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="18948-171">**bufor** Wskaźnik do buforu w celu zapisania danych czasu</span><span class="sxs-lookup"><span data-stu-id="18948-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-172">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-172">Return Values</span></span>

- <span data-ttu-id="18948-173">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="18948-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="18948-174">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-175">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-176">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-176">Allowed From</span></span>

<span data-ttu-id="18948-177">Wątki</span><span class="sxs-lookup"><span data-stu-id="18948-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="18948-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="18948-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="18948-180">Pobieranie rozszerzonego czasu lokalnego klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="18948-182">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-182">Description</span></span>

<span data-ttu-id="18948-183">Ta usługa pobiera rozszerzony czas lokalny klienta SNTP z wejściem wskaźnika buforu opcji w celu odbierania danych w formacie ciągu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="18948-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-184">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-184">Input Parameters</span></span>

- <span data-ttu-id="18948-185">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-186">**sekund** Wskaźnik na czas lokalny w sekundach</span><span class="sxs-lookup"><span data-stu-id="18948-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="18948-187">**ułamek** Wskaźnik do składnika ułamkowego</span><span class="sxs-lookup"><span data-stu-id="18948-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="18948-188">**bufor** Wskaźnik do buforu w celu zapisania danych czasu</span><span class="sxs-lookup"><span data-stu-id="18948-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="18948-189">**buffer_size** Długość buforu</span><span class="sxs-lookup"><span data-stu-id="18948-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-190">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-190">Return Values</span></span>

- <span data-ttu-id="18948-191">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="18948-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="18948-192">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-193">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="18948-194">Sprawdzanie NX_SIZE_ERROR (0x09) nie powiodło się buffer_size</span><span class="sxs-lookup"><span data-stu-id="18948-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-195">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-195">Allowed From</span></span>

<span data-ttu-id="18948-196">Wątki</span><span class="sxs-lookup"><span data-stu-id="18948-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="18948-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="18948-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="18948-199">Zainicjuj klienta dla operacji emisji</span><span class="sxs-lookup"><span data-stu-id="18948-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="18948-201">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-201">Description</span></span>

<span data-ttu-id="18948-202">Ta usługa inicjuje klienta na potrzeby operacji emisji, ustawiając adres IP serwera SNTP i inicjując parametry uruchamiania i limity czasu usługi SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="18948-203">Jeśli adresy multiemisji i emisji są inne niż null, wybierany jest adres multiemisji.</span><span class="sxs-lookup"><span data-stu-id="18948-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="18948-204">Jeśli oba adresy mają wartość null, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="18948-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="18948-205">Zwróć uwagę na to, że obsługuje tylko adresy serwera IPv4.</span><span class="sxs-lookup"><span data-stu-id="18948-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-206">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-206">Input Parameters</span></span>

- <span data-ttu-id="18948-207">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-208">**multicast_server_address** Adres multiemisji SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="18948-209">**broadcast_time_server** Adres emisji serwera SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-210">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-210">Return Values</span></span>

- <span data-ttu-id="18948-211">**NX_SUCCESS** (0X00) pomyślne utworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="18948-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="18948-212">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="18948-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="18948-213">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-214">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-215">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-215">Allowed From</span></span>

<span data-ttu-id="18948-216">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-217">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="18948-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="18948-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="18948-219">Zainicjuj klienta dla operacji emisji IPv4 lub IPv6</span><span class="sxs-lookup"><span data-stu-id="18948-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-220">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="18948-221">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-221">Description</span></span>

<span data-ttu-id="18948-222">Ta usługa inicjuje klienta na potrzeby operacji emisji przez skonfigurowanie adresu IP serwera SNTP i Inicjowanie parametrów uruchamiania i limitów czasu usługi SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="18948-223">Jeśli wskaźniki emisji i adresów multiemisji nie mają wartości null, wybierany jest adres multiemisji.</span><span class="sxs-lookup"><span data-stu-id="18948-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="18948-224">Jeśli oba wskaźniki adresów mają wartość null, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="18948-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="18948-225">Obsługuje to zarówno typy adresów IPv4, jak i IPv6.</span><span class="sxs-lookup"><span data-stu-id="18948-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="18948-226">Należy zauważyć, że protokół IPv6 nie obsługuje emisji, więc wskaźnik adresu emisji jest ustawiony na wartość IPv6, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="18948-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-227">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-227">Input Parameters</span></span>

- <span data-ttu-id="18948-228">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-229">**multicast_server_address** Adres multiemisji serwera SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="18948-230">**broadcast_server_address** Adres emisji serwera SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-231">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-231">Return Values</span></span>

- <span data-ttu-id="18948-232">**NX_SUCCESS** (0x00) — pomyślnie zainicjowano klienta</span><span class="sxs-lookup"><span data-stu-id="18948-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="18948-233">NX_SNTP_PARAM_ERROR (0xD0D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="18948-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="18948-234">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-235">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="18948-236">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-236">Allowed From</span></span>

<span data-ttu-id="18948-237">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-238">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="18948-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="18948-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="18948-240">Konfigurowanie klienta SNTP do uruchamiania w emisji pojedynczej</span><span class="sxs-lookup"><span data-stu-id="18948-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-241">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="18948-242">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-242">Description</span></span>

<span data-ttu-id="18948-243">Ta usługa inicjuje klienta dla operacji emisji pojedynczej, ustawiając adres IP serwera SNTP i inicjując parametry uruchamiania i limity czasu usługi SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="18948-244">Zwróć uwagę na to, że obsługuje tylko adresy serwera IPv4.</span><span class="sxs-lookup"><span data-stu-id="18948-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-245">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-245">Input Parameters</span></span>

- <span data-ttu-id="18948-246">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-247">**unicast_time_server** Adres IP serwera SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-248">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-248">Return Values</span></span>

- <span data-ttu-id="18948-249">**NX_SUCCESS** (0x00) — pomyślnie zainicjowano klienta</span><span class="sxs-lookup"><span data-stu-id="18948-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="18948-250">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="18948-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="18948-251">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-252">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-253">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-253">Allowed From</span></span>

<span data-ttu-id="18948-254">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-255">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="18948-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="18948-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="18948-257">Konfigurowanie klienta SNTP do uruchamiania w protokole IPv4 lub IPv6 emisji pojedynczej</span><span class="sxs-lookup"><span data-stu-id="18948-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-258">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="18948-259">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-259">Description</span></span>

<span data-ttu-id="18948-260">Ta usługa inicjuje klienta dla operacji emisji pojedynczej przez skonfigurowanie adresu IP serwera SNTP i Inicjowanie parametrów uruchamiania i limitów czasu usługi SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="18948-261">Obsługuje to zarówno typy adresów IPv4, jak i IPv6.</span><span class="sxs-lookup"><span data-stu-id="18948-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-262">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-262">Input Parameters</span></span>

- <span data-ttu-id="18948-263">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-264">**unicast_time_server** Adres IP serwera SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-265">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-265">Return Values</span></span>

- <span data-ttu-id="18948-266">**NX_SUCCESS** (0x00) — pomyślnie zainicjowano klienta</span><span class="sxs-lookup"><span data-stu-id="18948-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="18948-267">NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="18948-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="18948-268">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-269">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-270">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-270">Allowed From</span></span>

<span data-ttu-id="18948-271">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-272">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="18948-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="18948-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="18948-274">Wskaż, czy klient otrzymuje prawidłowe aktualizacje</span><span class="sxs-lookup"><span data-stu-id="18948-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-275">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="18948-276">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-276">Description</span></span>

<span data-ttu-id="18948-277">Ta usługa wskazuje, czy klient otrzymuje prawidłowe aktualizacje SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="18948-278">Jeśli maksymalny czas przestanie obowiązywać bez prawidłowej aktualizacji lub limitu kolejnych nieprawidłowych aktualizacji, stan odbierania zostanie zwrócony jako FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="18948-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="18948-279">Należy pamiętać, że klient protokołu SNTP nadal działa i jeśli aplikacja chce ponownie uruchomić klienta SNTP z innym emisją pojedynczą lub serwerem emisji/multiemisji, musi zatrzymać klienta protokołu SNTP przy użyciu usługi *nx_sntp_client_stop* , ponownie zainicjować klienta przy użyciu jednej z zainicjowanych usług z innym serwerem.</span><span class="sxs-lookup"><span data-stu-id="18948-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-280">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-280">Input Parameters</span></span>

- <span data-ttu-id="18948-281">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="18948-282">**receive_status** Wskaźnik do wskaźnika, jeśli klient otrzymuje prawidłowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="18948-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-283">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-283">Return Values</span></span>

- <span data-ttu-id="18948-284">Klient **NX_SUCCESS** (0x00) pomyślnie otrzymał stan aktualizacji</span><span class="sxs-lookup"><span data-stu-id="18948-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="18948-285">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-286">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-286">Allowed From</span></span>

<span data-ttu-id="18948-287">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-288">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="18948-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="18948-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="18948-290">Wyślij żądanie emisji pojedynczej bezpośrednio do serwera NTP</span><span class="sxs-lookup"><span data-stu-id="18948-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="18948-291">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="18948-292">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-292">Description</span></span>

<span data-ttu-id="18948-293">Ta usługa umożliwia aplikacji bezpośrednie wysyłanie żądania emisji pojedynczej do serwera NTP asynchronicznie z zadania wątku klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="18948-294">Opcja oczekiwania określa czas oczekiwania na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="18948-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="18948-295">Jeśli to się powiedzie, aplikacja może używać innych usług klienta SNTP do uzyskania najnowszego czasu.</span><span class="sxs-lookup"><span data-stu-id="18948-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="18948-296">Aby uzyskać więcej informacji, zobacz sekcję **żądania asynchronicznej emisji pojedynczej** .</span><span class="sxs-lookup"><span data-stu-id="18948-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-297">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-297">Input Parameters</span></span>

- <span data-ttu-id="18948-298">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="18948-299">**Wait_option** Opcja oczekiwania dla odpowiedzi NTP w taktach czasomierza.</span><span class="sxs-lookup"><span data-stu-id="18948-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-300">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-300">Return Values</span></span>

- <span data-ttu-id="18948-301">Klient **NX_SUCCESS** (0x00) pomyślnie wysyła i odbiera aktualizację emisji pojedynczej</span><span class="sxs-lookup"><span data-stu-id="18948-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="18948-302">Wątek klienta **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) nie został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="18948-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="18948-303">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-304">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-305">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-305">Allowed From</span></span>

<span data-ttu-id="18948-306">Wątki</span><span class="sxs-lookup"><span data-stu-id="18948-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-307">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="18948-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="18948-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="18948-309">Uruchamianie klienta w trybie emisji</span><span class="sxs-lookup"><span data-stu-id="18948-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-310">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="18948-311">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-311">Description</span></span>

<span data-ttu-id="18948-312">Ta usługa uruchamia klienta w trybie rozgłaszania, w którym będzie czekać na odebranie emisji z serwera SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="18948-313">Jeśli zostanie odebrany prawidłowy komunikat protokołu SNTP, limit czasu klienta protokołu SNTP dla maksymalnego wygaśnięcia bez aktualizacji i liczby kolejnych nieprawidłowych komunikatów odebranych są resetowane.</span><span class="sxs-lookup"><span data-stu-id="18948-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="18948-314">W przypadku przekroczenia jednego z tych limitów klient SNTP ustawia stan serwera na nieprawidłowy, mimo że nadal będzie czekać na otrzymywanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="18948-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="18948-315">Aplikacja może sondować zadanie klienta SNTP dla stanu serwera, a jeśli jest nieprawidłowa, Zatrzymaj klienta SNTP i ponownie zainicjuj go przy użyciu innego adresu emisji protokołu SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="18948-316">Może również przełączać się na serwer SNTP emisji pojedynczej.</span><span class="sxs-lookup"><span data-stu-id="18948-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-317">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-317">Input Parameters</span></span>

- <span data-ttu-id="18948-318">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-319">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-319">Return Values</span></span>

- <span data-ttu-id="18948-320">**stan--------rzeczywisty** stan ukończenia</span><span class="sxs-lookup"><span data-stu-id="18948-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="18948-321">Klient **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="18948-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="18948-322">Nie zainicjowano klienta **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01)</span><span class="sxs-lookup"><span data-stu-id="18948-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="18948-323">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-324">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-325">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-325">Allowed From</span></span>

<span data-ttu-id="18948-326">Wątki</span><span class="sxs-lookup"><span data-stu-id="18948-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-327">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="18948-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="18948-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="18948-329">Uruchamianie klienta w trybie emisji pojedynczej</span><span class="sxs-lookup"><span data-stu-id="18948-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-330">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="18948-331">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-331">Description</span></span>

<span data-ttu-id="18948-332">Ta usługa uruchamia klienta w trybie emisji pojedynczej, w którym okresowo wysyła żądanie emisji pojedynczej do serwera SNTP w celu zaktualizowania czasu.</span><span class="sxs-lookup"><span data-stu-id="18948-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="18948-333">Jeśli zostanie odebrany prawidłowy komunikat SNTP, zostanie zresetowany limit czasu klienta SNTP dla maksymalnego wygaśnięcia bez aktualizacji, początkowy interwał sondowania oraz liczba kolejnych nieprawidłowych komunikatów odebranych.</span><span class="sxs-lookup"><span data-stu-id="18948-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="18948-334">W przypadku przekroczenia jednego z tych limitów klient SNTP ustawia stan serwera na nieprawidłowy, mimo że nadal będzie sondował i czekał na otrzymywanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="18948-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="18948-335">Aplikacja może sondować zadanie klienta SNTP dla stanu serwera, a jeśli jest nieprawidłowa, Zatrzymaj klienta SNTP i ponownie zainicjuj go przy użyciu innego adresu SNTP emisji pojedynczej.</span><span class="sxs-lookup"><span data-stu-id="18948-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="18948-336">Może również przełączać się na serwer emisji SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="18948-337">.</span><span class="sxs-lookup"><span data-stu-id="18948-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-338">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-338">Input Parameters</span></span>

- <span data-ttu-id="18948-339">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-340">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-340">Return Values</span></span>

- <span data-ttu-id="18948-341">**NX_SUCCESS** (0X00) pomyślnie uruchomił klienta w trybie emisji pojedynczej</span><span class="sxs-lookup"><span data-stu-id="18948-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="18948-342">Klient **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="18948-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="18948-343">Nie zainicjowano klienta **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01)</span><span class="sxs-lookup"><span data-stu-id="18948-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="18948-344">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="18948-345">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi</span><span class="sxs-lookup"><span data-stu-id="18948-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="18948-346">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-346">Allowed From</span></span>

<span data-ttu-id="18948-347">Wątki</span><span class="sxs-lookup"><span data-stu-id="18948-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-348">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="18948-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="18948-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="18948-350">Ustawianie czasu lokalnego klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-351">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="18948-352">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-352">Description</span></span>

<span data-ttu-id="18948-353">Ta usługa ustawia czas lokalny klienta SNTP z czasem wejścia w formacie SNTP, np. sekund i "ułamek", który jest formatem do umieszczania ułamków sekundy w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="18948-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="18948-354">Jest on przeznaczony do aktualizowania czasu lokalnego klienta SNTP z niezależnego, na przykład zegara czasu rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="18948-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="18948-355">Protokół SNTP jest przeznaczony do aktualizacji czasu SNTP, aby zachować czas lokalnego zegara od "dryfing".</span><span class="sxs-lookup"><span data-stu-id="18948-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="18948-356">Aktualizacje czasu serwera SNTP mogą być, ale nie mają być jedynym wejściem do czasu lokalnego klienta SNTP, jeśli na urządzeniu aplikacji nie ma niezależnego czasu.</span><span class="sxs-lookup"><span data-stu-id="18948-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="18948-357">Tego interfejsu API można również użyć, aby nadać klientowi SNTP czas podstawowy przed uruchomieniem wątku klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="18948-358">Czas lokalny klienta SNTP jest porównywany z otrzymanymi aktualizacjami prawidłowych danych czasu.</span><span class="sxs-lookup"><span data-stu-id="18948-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="18948-359">Po pierwszym odebraniu aktualizacji może wystąpić bardzo duża rozbieżność.</span><span class="sxs-lookup"><span data-stu-id="18948-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="18948-360">W związku z tym istnieje możliwość, że klient SNTP zignoruje niezgodność z pierwszą aktualizacją.</span><span class="sxs-lookup"><span data-stu-id="18948-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="18948-361">W ten sposób klient SNTP można uruchomić bez czasu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="18948-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="18948-362">Czas wejścia można uzyskać od znanych czasów epoki (zwykle dostępnych w Internecie) i są one obliczane jako liczba sekund od 1 stycznia 1900 (do 2036, gdy zostanie rozpoczęte nowe "Epoka").</span><span class="sxs-lookup"><span data-stu-id="18948-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-363">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-363">Input Parameters</span></span>

- <span data-ttu-id="18948-364">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-365">**sekund** Składnik sekund danych wejściowych czasu</span><span class="sxs-lookup"><span data-stu-id="18948-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="18948-366">**ułamek** Składnik podsekund w formacie ułameku SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-367">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-367">Return Values</span></span>

- <span data-ttu-id="18948-368">**NX_SUCCESS** (0X00) pomyślnie ustawił czas lokalny</span><span class="sxs-lookup"><span data-stu-id="18948-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="18948-369">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-370">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-370">Allowed From</span></span>

<span data-ttu-id="18948-371">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="18948-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="18948-372">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="18948-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="18948-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="18948-374">Ustawianie wywołania zwrotnego aktualizacji SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-375">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="18948-376">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-376">Description</span></span>

<span data-ttu-id="18948-377">Ta usługa ustawia wywołanie zwrotne w celu powiadomienia aplikacji, gdy klient SNTP otrzymuje prawidłową aktualizację czasu.</span><span class="sxs-lookup"><span data-stu-id="18948-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="18948-378">Dostarcza rzeczywisty komunikat protokołu SNTP i czas lokalny klienta SNTP (zwykle taki sam) w formacie NTP.</span><span class="sxs-lookup"><span data-stu-id="18948-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="18948-379">Aplikacja może korzystać z danych NTP bezpośrednio lub wywołać *usługę nx_sntp_client_utility_display_date_time* , aby przekonwertować czas na czytelny format.</span><span class="sxs-lookup"><span data-stu-id="18948-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-380">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-380">Input Parameters</span></span>

- <span data-ttu-id="18948-381">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="18948-382">**time_update_cb** Wskaźnik do funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="18948-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-383">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-383">Return Values</span></span>

- <span data-ttu-id="18948-384">**NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="18948-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="18948-385">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-386">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-386">Allowed From</span></span>

<span data-ttu-id="18948-387">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="18948-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="18948-388">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="18948-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="18948-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="18948-390">Zatrzymaj wątek klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="18948-392">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-392">Description</span></span>

<span data-ttu-id="18948-393">Ta usługa przerywa wątek klienta SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="18948-394">Zadania wątku klienta SNTP, które są uruchamiane w pętli nieskończonej, wstrzymują wszystkie iteracje w celu wydania kontroli stanu klienta SNTP i zezwalają aplikacjom na wykonywanie wywołań interfejsu API na kliencie SNTP.</span><span class="sxs-lookup"><span data-stu-id="18948-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-395">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-395">Input Parameters</span></span>

- <span data-ttu-id="18948-396">**client_ptr** Wskaźnik do bloku kontroli klienta SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-397">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-397">Return Values</span></span>

- <span data-ttu-id="18948-398">**NX_SUCCESS** (0X00) pomyślnie zatrzymano wątek klienta</span><span class="sxs-lookup"><span data-stu-id="18948-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="18948-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) wątek klienta SNTP nie został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="18948-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="18948-400">NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="18948-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-401">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-401">Allowed From</span></span>

<span data-ttu-id="18948-402">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-403">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="18948-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="18948-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="18948-405">Konwertowanie czasu NTP na ciąg daty i godziny</span><span class="sxs-lookup"><span data-stu-id="18948-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-406">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="18948-407">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-407">Description</span></span>

<span data-ttu-id="18948-408">Ta usługa konwertuje czas lokalny klienta SNTP na format daty miesiąca roku i zwraca datę z podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="18948-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="18948-409">NX_SNTP_CURRENT_YEAR nie może być tym samym rokiem co bieżący czas klienta, ale musi być zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="18948-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-410">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-410">Input Parameters</span></span>

- <span data-ttu-id="18948-411">**client_ptr wskaźnik do klienta SNTP**</span><span class="sxs-lookup"><span data-stu-id="18948-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="18948-412">**bufor** Wskaźnik do buforu do przechowywania daty</span><span class="sxs-lookup"><span data-stu-id="18948-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="18948-413">**Długość** Rozmiar buforu wejściowego</span><span class="sxs-lookup"><span data-stu-id="18948-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-414">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-414">Return Values</span></span>

- <span data-ttu-id="18948-415">Konwersja **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="18948-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="18948-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) nie NX_SNTP_CURRENT_YEAR zdefiniowany lub nie został określony czas lokalnego klienta</span><span class="sxs-lookup"><span data-stu-id="18948-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="18948-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) niewystarczająca długość buforu</span><span class="sxs-lookup"><span data-stu-id="18948-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="18948-418">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-418">Allowed From</span></span>

<span data-ttu-id="18948-419">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-420">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="18948-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="18948-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="18948-422">Konwertuj milisekundy na składnik datafrakcji NTP</span><span class="sxs-lookup"><span data-stu-id="18948-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-423">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="18948-424">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-424">Description</span></span>

<span data-ttu-id="18948-425">Ta usługa konwertuje dane wejściowe w milisekundach na składnik NTP.</span><span class="sxs-lookup"><span data-stu-id="18948-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="18948-426">Jest ona przeznaczona do użycia z aplikacjami, które mają początkowy czas podstawowy dla klienta SNTP, ale nie w formacie sekundy NTP/ułamek.</span><span class="sxs-lookup"><span data-stu-id="18948-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="18948-427">Liczba milisekund musi być mniejsza niż 1000, aby można było wprowadzić prawidłowy ułamek.</span><span class="sxs-lookup"><span data-stu-id="18948-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-428">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-428">Input Parameters</span></span>

- <span data-ttu-id="18948-429">**milisekundy do przekonwertowania**</span><span class="sxs-lookup"><span data-stu-id="18948-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="18948-430">**ułamek** Wskaźnik do milisekund przekonwertowanych na ułamek</span><span class="sxs-lookup"><span data-stu-id="18948-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-431">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-431">Return Values</span></span>

- <span data-ttu-id="18948-432">Konwersja **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="18948-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="18948-433">Błąd **NX_SNTP_OVERFLOW_ERROR** (0XD32) podczas konwertowania czasu na datę</span><span class="sxs-lookup"><span data-stu-id="18948-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="18948-434">NX_SNTP_INVALID_TIME (0xD30) nieprawidłowe dane wejściowe SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-435">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-435">Allowed From</span></span>

<span data-ttu-id="18948-436">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-437">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="18948-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="18948-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="18948-439">Konwertuj mikrosekundy na składnik część ułamka NTP</span><span class="sxs-lookup"><span data-stu-id="18948-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-440">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="18948-441">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-441">Description</span></span>

<span data-ttu-id="18948-442">Ta usługa konwertuje mikrosekundy wejściowe na składnik część ułamka NTP.</span><span class="sxs-lookup"><span data-stu-id="18948-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="18948-443">Jest ona przeznaczona do użycia z aplikacjami, które mają początkowy czas podstawowy dla klienta SNTP, ale nie w formacie sekundy NTP/ułamek.</span><span class="sxs-lookup"><span data-stu-id="18948-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="18948-444">Liczba mikrosekund musi być mniejsza niż 1000000, aby można było wprowadzić prawidłowy ułamek.</span><span class="sxs-lookup"><span data-stu-id="18948-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-445">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-445">Input Parameters</span></span>

- <span data-ttu-id="18948-446">**mikrosekundy** Mikrosekundy do przekonwertowania</span><span class="sxs-lookup"><span data-stu-id="18948-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="18948-447">**ułamek** Wskaźnik do mikrosekund przekonwertowany na ułamek</span><span class="sxs-lookup"><span data-stu-id="18948-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-448">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-448">Return Values</span></span>

- <span data-ttu-id="18948-449">Konwersja **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="18948-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="18948-450">Błąd **NX_SNTP_OVERFLOW_ERROR** (0XD32) podczas konwertowania czasu na datę</span><span class="sxs-lookup"><span data-stu-id="18948-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="18948-451">NX_SNTP_INVALID_TIME (0xD30) nieprawidłowe dane wejściowe SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-452">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-452">Allowed From</span></span>

<span data-ttu-id="18948-453">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-454">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="18948-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="18948-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="18948-456">Konwertuj składnik część ułamka NTP na mikrosekundy</span><span class="sxs-lookup"><span data-stu-id="18948-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="18948-457">Prototype</span><span class="sxs-lookup"><span data-stu-id="18948-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="18948-458">Opis</span><span class="sxs-lookup"><span data-stu-id="18948-458">Description</span></span>

<span data-ttu-id="18948-459">Ta usługa konwertuje wejściowy składnik NTP do mikrosekund.</span><span class="sxs-lookup"><span data-stu-id="18948-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18948-460">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="18948-460">Input Parameters</span></span>

- <span data-ttu-id="18948-461">**ułamek dziesiętny do przekonwertowania**</span><span class="sxs-lookup"><span data-stu-id="18948-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="18948-462">**mikrosekundy** Wskaźnik do ułamka konwertowany na mikrosekundy</span><span class="sxs-lookup"><span data-stu-id="18948-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="18948-463">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="18948-463">Return Values</span></span>

- <span data-ttu-id="18948-464">Konwersja **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="18948-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="18948-465">NX_SNTP_INVALID_TIME (0xD30) nieprawidłowe dane wejściowe SNTP</span><span class="sxs-lookup"><span data-stu-id="18948-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18948-466">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="18948-466">Allowed From</span></span>

<span data-ttu-id="18948-467">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="18948-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="18948-468">Przykład</span><span class="sxs-lookup"><span data-stu-id="18948-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```