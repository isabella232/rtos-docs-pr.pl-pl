---
title: Rozdział 3 — Opis usługi Azure RTO NetX Duo PTP Client Services
description: Ten rozdział zawiera opis wszystkich usług klienta PTP NetX Duo w kolejności alfabetycznej.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821708"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="c51da-103">Rozdział 3 — Opis usługi Azure RTO NetX Duo PTP Client Services</span><span class="sxs-lookup"><span data-stu-id="c51da-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="c51da-104">Ten rozdział zawiera opis wszystkich usług klienta PTP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="c51da-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="c51da-105">*W sekcji **wartości zwracane** w poniższych opisach funkcji interfejsu API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.*</span><span class="sxs-lookup"><span data-stu-id="c51da-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="c51da-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="c51da-106">nx_ptp_client_create</span></span>

<span data-ttu-id="c51da-107">Utwórz wystąpienie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="c51da-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-109">Description</span></span>

<span data-ttu-id="c51da-110">Ta usługa tworzy wystąpienie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="c51da-111">Należy pamiętać, że aplikacja musi najpierw utworzyć wystąpienie IP i pulę pakietów dla klienta protokołu PTP do przesyłania pakietów.</span><span class="sxs-lookup"><span data-stu-id="c51da-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="c51da-112">W przypadku puli pakietów aplikacja może używać tej samej puli pakietów w wystąpieniu IP. lub można utworzyć dedykowaną pulę pakietów dla klienta PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="c51da-113">Rozwiązanie dedykowanej puli pakietów ma zalety używania małych pakietów (128 bajtów pakietów, jeśli używany jest protokół IPv6 lub 108 bajtów tylko dla protokołu IPv4).</span><span class="sxs-lookup"><span data-stu-id="c51da-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-114">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-114">Input Parameters</span></span>
* <span data-ttu-id="c51da-115">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-116">**ip_ptr** Wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="c51da-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="c51da-117">**interface_index** Indeks interfejsu sieciowego PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="c51da-118">**packet_pool_ptr** Wskaźnik do puli pakietów klienta</span><span class="sxs-lookup"><span data-stu-id="c51da-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="c51da-119">**thread_priority**  Priorytet wątku PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="c51da-120">**thread_stack** Wskaźnik do stosu wątków</span><span class="sxs-lookup"><span data-stu-id="c51da-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="c51da-121">**stack_size** Rozmiar stosu wątków</span><span class="sxs-lookup"><span data-stu-id="c51da-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="c51da-122">**clock_callback** Wywołanie zwrotne zegara PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="c51da-123">**clock_callback_data** Dane dla wywołania zwrotnego zegara</span><span class="sxs-lookup"><span data-stu-id="c51da-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-124">Return Values</span></span>
* <span data-ttu-id="c51da-125">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c51da-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="c51da-126">Ładunek pakietu **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) jest za mały</span><span class="sxs-lookup"><span data-stu-id="c51da-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="c51da-127">Błąd wywołania zwrotnego zegara **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05)</span><span class="sxs-lookup"><span data-stu-id="c51da-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="c51da-128">**stan** Kończenie stanu NetX Duo i wywołań usługi ThreadX</span><span class="sxs-lookup"><span data-stu-id="c51da-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="c51da-129">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="c51da-130">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs</span><span class="sxs-lookup"><span data-stu-id="c51da-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-131">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-131">Allowed From</span></span>
<span data-ttu-id="c51da-132">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="c51da-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="c51da-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="c51da-135">Usuwa wystąpienie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-137">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-137">Description</span></span>

<span data-ttu-id="c51da-138">Ta usługa usuwa wystąpienie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-139">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-139">Input Parameters</span></span>
* <span data-ttu-id="c51da-140">**client_ptr** Wskaźnik do usunięcia klienta programu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-141">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-141">Return Values</span></span>
* <span data-ttu-id="c51da-142">Pomyślnie usunięto klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c51da-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="c51da-143">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-144">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-144">Allowed From</span></span>
<span data-ttu-id="c51da-145">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="c51da-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="c51da-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="c51da-148">Pobierz informacje o zegarze głównym.</span><span class="sxs-lookup"><span data-stu-id="c51da-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-149">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="c51da-150">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-150">Description</span></span>
<span data-ttu-id="c51da-151">Ta usługa pobiera informacje o zegarze głównym.</span><span class="sxs-lookup"><span data-stu-id="c51da-151">This service gets information of master clock.</span></span> <span data-ttu-id="c51da-152">Blok kontroli wzorca jest przesyłany do aplikacji użytkownika za pomocą funkcji wywołania zwrotnego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c51da-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-153">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-153">Input Parameters</span></span>
* <span data-ttu-id="c51da-154">**master_ptr** Wskaźnik do zegara wzorca PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="c51da-155">**adres** Adres zegara głównego</span><span class="sxs-lookup"><span data-stu-id="c51da-155">**address** Address of master clock</span></span>
* <span data-ttu-id="c51da-156">**port_identity** Port i tożsamość wzorca PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="c51da-157">**port_identity_length** Długość portu i tożsamości wzorca PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="c51da-158">**priority1** Priority1 zegara głównego programu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="c51da-159">**priority2** Priority2 zegara głównego programu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="c51da-160">**clock_class** Klasa zegara głównego programu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="c51da-161">**clock_accuracy** Dokładność zegara wzorca PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="c51da-162">**clock_variance** WARIANCJA zegara głównego programu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="c51da-163">**grandmaster_identity** Tożsamość zegara Grandmaster</span><span class="sxs-lookup"><span data-stu-id="c51da-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="c51da-164">**grandmaster_identity_length** Długość tożsamości Grandmaster</span><span class="sxs-lookup"><span data-stu-id="c51da-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="c51da-165">**steps_removed** Kroki usunięte z nagłówka PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="c51da-166">**time_source** Źródło czasomierza używane przez zegar Grandmaster</span><span class="sxs-lookup"><span data-stu-id="c51da-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-167">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-167">Return Values</span></span>
* <span data-ttu-id="c51da-168">**NX_SUCCESS** (0x00) pomyślnie Pobierz informacje o zegarze głównym</span><span class="sxs-lookup"><span data-stu-id="c51da-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="c51da-169">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-170">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-170">Allowed From</span></span>
<span data-ttu-id="c51da-171">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="c51da-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="c51da-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="c51da-174">Powiadamiaj klienta PTP o sygnaturze czasowej pakietu.</span><span class="sxs-lookup"><span data-stu-id="c51da-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-176">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-176">Description</span></span>
<span data-ttu-id="c51da-177">Ta usługa powiadamia klienta programu PTP o tym, że pakiet jest przesyłany z sygnaturą czasową.</span><span class="sxs-lookup"><span data-stu-id="c51da-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="c51da-178">Ta usługa jest przeznaczona dla sterownika sieci i wywoływana podczas przesyłania pakietu.</span><span class="sxs-lookup"><span data-stu-id="c51da-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="c51da-179">Sygnatura czasowa jest zwykle generowana przez sprzęt.</span><span class="sxs-lookup"><span data-stu-id="c51da-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-180">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-180">Input Parameters</span></span>
* <span data-ttu-id="c51da-181">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-182">**packet_ptr** Wskaźnik do przesyłanego pakietu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="c51da-183">**timestamp_ptr** Wskaźnik do sygnatury czasowej pakietu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-184">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-184">Return Values</span></span>
<span data-ttu-id="c51da-185">Brak</span><span class="sxs-lookup"><span data-stu-id="c51da-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-186">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-186">Allowed From</span></span>
<span data-ttu-id="c51da-187">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-188">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="c51da-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="c51da-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="c51da-190">Implementacja oprogramowania zegara protokołu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-191">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="c51da-192">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-192">Description</span></span>
<span data-ttu-id="c51da-193">Ta funkcja wywołania zwrotnego służy jako symulowane Źródło zegara niskiej rozdzielczości dla programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="c51da-194">Ta procedura jest udostępniana jako odwołanie i nie może być używana w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="c51da-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-195">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-195">Input Parameters</span></span>
* <span data-ttu-id="c51da-196">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-197">**operacja** Operacja wywołania zwrotnego, prawidłowe wartości są zdefiniowane jako:</span><span class="sxs-lookup"><span data-stu-id="c51da-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="c51da-198">**NX_PTP_CLIENT_CLOCK_INIT** Zainicjuj zegar.</span><span class="sxs-lookup"><span data-stu-id="c51da-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="c51da-199">**NX_PTP_CLIENT_CLOCK_SET** Ustaw bieżącą sygnaturę czasową określoną przez `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="c51da-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="c51da-200">**NX_PTP_CLIENT_CLOCK_GET** Zwróć bieżącą sygnaturę czasową do `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="c51da-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="c51da-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Wyodrębnij sygnaturę czasową z `packet_ptr` do `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="c51da-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="c51da-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Dostosuj bieżącą sygnaturę czasową mniejszą niż *1* sekunda.</span><span class="sxs-lookup"><span data-stu-id="c51da-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="c51da-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Oznacz, `packet_ptr` które są wymagane do powiadomienia klienta PTP o sygnaturze czasowej podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="c51da-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="c51da-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Aktualizuj czasomierz elastyczny.</span><span class="sxs-lookup"><span data-stu-id="c51da-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="c51da-205">Może być ignorowany przez zegar sprzętu.</span><span class="sxs-lookup"><span data-stu-id="c51da-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="c51da-206">**time_ptr** Wskaźnik do sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="c51da-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="c51da-207">**packet_ptr** Wskaźnik do pakietu.</span><span class="sxs-lookup"><span data-stu-id="c51da-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="c51da-208">**callback_data** Wskaźnik na nieprzezroczyste dane wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c51da-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-209">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-209">Return Values</span></span>
* <span data-ttu-id="c51da-210">Operacja **NX_SUCCESS** (0x00) zakończyła się pomyślnie</span><span class="sxs-lookup"><span data-stu-id="c51da-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="c51da-211">**NX_PTP_PARAM_ERROR** (0XD03) nieprawidłowy parametr</span><span class="sxs-lookup"><span data-stu-id="c51da-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-212">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-212">Allowed From</span></span>
<span data-ttu-id="c51da-213">Wewnętrzne PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="c51da-214">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="c51da-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="c51da-215">nx_ptp_client_start</span></span>

<span data-ttu-id="c51da-216">Uruchom klienta PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-217">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="c51da-218">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-218">Description</span></span>
<span data-ttu-id="c51da-219">Ta usługa uruchamia wcześniej utworzone wystąpienie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-220">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-220">Input Parameters</span></span>
* <span data-ttu-id="c51da-221">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-222">**client_port_identity_ptr** Wskaźnik do portu i tożsamości klienta, może mieć wartość NULL</span><span class="sxs-lookup"><span data-stu-id="c51da-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="c51da-223">**client_port_identity_length** Długość portu i tożsamości klienta.</span><span class="sxs-lookup"><span data-stu-id="c51da-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="c51da-224">Musi mieć wartość 0, jeśli client_port_identity_ptr ma wartość NULL lub NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span><span class="sxs-lookup"><span data-stu-id="c51da-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="c51da-225">**domena** Domena zegara PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="c51da-226">**transport_specific** 4 bity specyficzne dla transportu</span><span class="sxs-lookup"><span data-stu-id="c51da-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="c51da-227">**event_callback** Wywołana funkcja wywołania zwrotnego dla zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="c51da-228">**event_callback_data** Dane wywołania zwrotnego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-229">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-229">Return Values</span></span>
* <span data-ttu-id="c51da-230">**NX_SUCCESS** (0x00) — pomyślnie uruchomiono klienta</span><span class="sxs-lookup"><span data-stu-id="c51da-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="c51da-231">Klient PTP **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="c51da-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="c51da-232">**stan** Kończenie stanu NetX Duo i wywołań usługi ThreadX</span><span class="sxs-lookup"><span data-stu-id="c51da-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="c51da-233">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-234">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-234">Allowed From</span></span>
<span data-ttu-id="c51da-235">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-236">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="c51da-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="c51da-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="c51da-238">Zatrzymaj klienta PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-238">Stop PTP client.</span></span>  <span data-ttu-id="c51da-239">Po zatrzymaniu klienta programu PTP nie przetwarza on pakietów PTP ani nie przesyła pakietów PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-241">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-241">Description</span></span>
<span data-ttu-id="c51da-242">Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-243">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-243">Input Parameters</span></span>
* <span data-ttu-id="c51da-244">**client_ptr** Wskaźnik do zatrzymania klienta programu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-245">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-245">Return Values</span></span>
* <span data-ttu-id="c51da-246">**NX_SUCCESS** (0X00) klient został pomyślnie zatrzymany</span><span class="sxs-lookup"><span data-stu-id="c51da-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="c51da-247">Klient **NX_PTP_CLIENT_NOT_STARTED** (0xD01) nie został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="c51da-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="c51da-248">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-249">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-249">Allowed From</span></span>
<span data-ttu-id="c51da-250">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-251">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="c51da-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="c51da-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="c51da-253">Pobierz informacje o synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="c51da-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-254">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="c51da-255">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-255">Description</span></span>
<span data-ttu-id="c51da-256">Ta usługa pobiera informacje o komunikacie synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="c51da-256">This service gets information of Sync message.</span></span> <span data-ttu-id="c51da-257">Blok kontroli synchronizacji jest przesyłany do aplikacji użytkownika za pomocą funkcji wywołania zwrotnego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c51da-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-258">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-258">Input Parameters</span></span>
* <span data-ttu-id="c51da-259">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-260">**flagi** Flagi w komunikacie synchronizacji</span><span class="sxs-lookup"><span data-stu-id="c51da-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="c51da-261">**utc_offset** Przesunięcie między TAI i UTC</span><span class="sxs-lookup"><span data-stu-id="c51da-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-262">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-262">Return Values</span></span>
* <span data-ttu-id="c51da-263">**NX_SUCCESS** (0x00) pomyślnie Pobierz informacje o synchronizacji</span><span class="sxs-lookup"><span data-stu-id="c51da-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="c51da-264">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-265">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-265">Allowed From</span></span>
<span data-ttu-id="c51da-266">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-267">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="c51da-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="c51da-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="c51da-269">Pobierz bieżącą godzinę.</span><span class="sxs-lookup"><span data-stu-id="c51da-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-270">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-271">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-271">Description</span></span>
<span data-ttu-id="c51da-272">Ta usługa pobiera bieżącą wartość zegara PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="c51da-273">Jest on dostępny niezależnie od tego, że klient PTP jest synchronizowany z zegarem głównym.</span><span class="sxs-lookup"><span data-stu-id="c51da-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-274">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-274">Input Parameters</span></span>
* <span data-ttu-id="c51da-275">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-276">**time_ptr** Wskaźnik do czasu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-277">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-277">Return Values</span></span>
* <span data-ttu-id="c51da-278">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c51da-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="c51da-279">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-280">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-280">Allowed From</span></span>
<span data-ttu-id="c51da-281">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-282">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="c51da-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="c51da-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="c51da-284">Ustaw bieżącą godzinę.</span><span class="sxs-lookup"><span data-stu-id="c51da-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-285">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-286">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-286">Description</span></span>
<span data-ttu-id="c51da-287">Ta usługa ustawia bieżącą wartość zegara PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="c51da-288">Musi być wywoływana przed uruchomieniem klienta PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-289">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-289">Input Parameters</span></span>
* <span data-ttu-id="c51da-290">**client_ptr** Wskaźnik do programu PTP Client do utworzenia</span><span class="sxs-lookup"><span data-stu-id="c51da-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="c51da-291">**time_ptr** Wskaźnik do czasu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-292">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-292">Return Values</span></span>
* <span data-ttu-id="c51da-293">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c51da-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="c51da-294">Klient PTP **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) jest już uruchomiony</span><span class="sxs-lookup"><span data-stu-id="c51da-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="c51da-295">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-296">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-296">Allowed From</span></span>
<span data-ttu-id="c51da-297">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-298">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="c51da-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="c51da-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="c51da-300">Konwertuj czas PTP na datę i godzinę UTC.</span><span class="sxs-lookup"><span data-stu-id="c51da-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-301">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-302">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-302">Description</span></span>
<span data-ttu-id="c51da-303">Ta usługa konwertuje czas PTP na datę i godzinę UTC.</span><span class="sxs-lookup"><span data-stu-id="c51da-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-304">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-304">Input Parameters</span></span>
* <span data-ttu-id="c51da-305">**time_ptr** Wskaźnik do czasu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="c51da-306">**przesunięcie** Drugie przesunięcie podpisane w celu dodania czasu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="c51da-307">**date_time_ptr** Wskaźnik do daty wyników</span><span class="sxs-lookup"><span data-stu-id="c51da-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-308">Return Values</span></span>
* <span data-ttu-id="c51da-309">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c51da-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="c51da-310">**Wskaźnik do daty otrzymanej** (0XD03) nieprawidłowy parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="c51da-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="c51da-311">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-312">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-312">Allowed From</span></span>
<span data-ttu-id="c51da-313">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-314">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="c51da-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="c51da-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="c51da-316">Dwa razy.</span><span class="sxs-lookup"><span data-stu-id="c51da-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="c51da-317">Prototype</span><span class="sxs-lookup"><span data-stu-id="c51da-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="c51da-318">Opis</span><span class="sxs-lookup"><span data-stu-id="c51da-318">Description</span></span>
<span data-ttu-id="c51da-319">Ta usługa oblicza różnicę między dwoma czasami PTP.</span><span class="sxs-lookup"><span data-stu-id="c51da-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c51da-320">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="c51da-320">Input Parameters</span></span>
* <span data-ttu-id="c51da-321">**time1_ptr** Wskaźnik do pierwszego czasu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="c51da-322">**time2_ptr** Wskaźnik do drugiego czasu PTP</span><span class="sxs-lookup"><span data-stu-id="c51da-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="c51da-323">**result_ptr** Wskaźnik do wyniku time1-time2</span><span class="sxs-lookup"><span data-stu-id="c51da-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="c51da-324">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="c51da-324">Return Values</span></span>
* <span data-ttu-id="c51da-325">Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="c51da-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="c51da-326">NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego</span><span class="sxs-lookup"><span data-stu-id="c51da-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c51da-327">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="c51da-327">Allowed From</span></span>
<span data-ttu-id="c51da-328">Wątki</span><span class="sxs-lookup"><span data-stu-id="c51da-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c51da-329">Przykład</span><span class="sxs-lookup"><span data-stu-id="c51da-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```