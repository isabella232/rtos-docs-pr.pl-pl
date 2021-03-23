---
title: Dodatek A — opis funkcji przywracania stanu dla klienta DHCPv6 usługi Azure RTO NetX Duo
description: Opcja konfiguracji klienta usługi Azure RTO NetX Duo DHDPv6, NX_DHCPV6_CLIENT_RESTORE_STATE umożliwia systemowi przywrócenie utworzonego wcześniej klienta DHCP w stanie związanym między ponownymi uruchomieniami systemu.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822003"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="db19c-103">Dodatek A — opis funkcji przywracania stanu dla klienta DHCPv6 usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="db19c-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="db19c-104">Opcja konfiguracji klienta usługi Azure RTO NetX Duo DHDPv6, NX_DHCPV6_CLIENT_RESTORE_STATE umożliwia systemowi przywrócenie utworzonego wcześniej klienta DHCP w stanie związanym między ponownymi uruchomieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="db19c-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="db19c-105">Ta opcja umożliwia również aplikacji zawieszenie wątku klienta DHCPv6 i wznowienie go, zaktualizowanie o czas, który upłynął od zawieszenia i wznowienia wątku bez wyłączania.</span><span class="sxs-lookup"><span data-stu-id="db19c-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="db19c-106">Przywracanie klienta DHCPv6 między ponownymi uruchomieniami</span><span class="sxs-lookup"><span data-stu-id="db19c-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="db19c-107">Aby przywrócić klienta DHCPv6 między ponownymi uruchomieniami, aplikacja DHCPv6 tworzy wystąpienie klienta DHCPv6, a następnie uzyskuje dzierżawę adresu IP przy użyciu normalnego protokołu DHCPv6 i wywołując *nx_dhcpv6_start*.</span><span class="sxs-lookup"><span data-stu-id="db19c-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="db19c-108">Następnie aplikacja DHCPv6 czeka na zakończenie tego protokołu.</span><span class="sxs-lookup"><span data-stu-id="db19c-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="db19c-109">Jeśli wszystko przebiegnie prawidłowo, urządzenie osiągnie stan związany z przypisanym prawidłowym adresem IP z serwera DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="db19c-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="db19c-110">Przed podjęciem dalszych działań aplikacja kliencka DHCPv6 zapisuje bieżące wystąpienie klienta DHCPv6 do rekordu klienta DHCPv6, który następnie jest przechowywany w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="db19c-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="db19c-111">Niezależny obiekt "hodowca" w innym miejscu w systemie śledzi czas, który upłynął podczas tego stanu zasilania.</span><span class="sxs-lookup"><span data-stu-id="db19c-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="db19c-112">W przypadku włączania programu aplikacja tworzy nowe wystąpienie klienta DHCPv6, a następnie aktualizuje je przy użyciu utworzonego wcześniej rekordu klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="db19c-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="db19c-113">Czas, który upłynął, jest uzyskiwany z "czasu opiekuna", a następnie stosowany do pozostałego czasu dzierżawy DHCP Clientv6.</span><span class="sxs-lookup"><span data-stu-id="db19c-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="db19c-114">W tym momencie aplikacja może wznowić działanie klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="db19c-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="db19c-115">Jeśli czas, który upłynął podczas włączania, spowoduje umieszczenie stanu klienta DHCPv6 w stanie ODNOWIENIa lub ponownego powiązania, klient DHCPv6 automatycznie zainicjuje komunikaty protokołu DHCPv6 żądające odnowienia lub ponownego powiązania dzierżawy adresu IP.</span><span class="sxs-lookup"><span data-stu-id="db19c-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="db19c-116">Jeśli adres IP wygasł, klient DHCPv6 automatycznie usunie adres IP w wystąpieniu IP i rozpocznie proces DHCPv6 od stanu INIT, żądając nowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="db19c-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="db19c-117">W ten sposób klient DHCPv6 może działać między ponownymi uruchomieniami tak, jakby nie został przerwany.</span><span class="sxs-lookup"><span data-stu-id="db19c-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="db19c-118">Poniżej znajduje się ilustracja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="db19c-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="db19c-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="db19c-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="db19c-120">Utwórz rekord bieżącego stanu klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="db19c-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="db19c-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="db19c-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="db19c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="db19c-122">Description</span></span>

<span data-ttu-id="db19c-123">Ta usługa zapisuje klienta DHCPv6 do rekordu wskazywanego przez record_ptr.</span><span class="sxs-lookup"><span data-stu-id="db19c-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="db19c-124">Dzięki temu aplikacja kliencka DHCPv6 przywraca swój stan klienta DHCPv6 po wystąpieniu programu, na przykład o wyłączeniu i ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="db19c-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="db19c-125">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="db19c-125">Input Parameters</span></span>

- <span data-ttu-id="db19c-126">**dhcpv6_ptr** Wskaźnik do klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="db19c-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="db19c-127">**record_ptr** Wskaźnik do rekordu klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="db19c-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="db19c-128">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="db19c-128">Return Values</span></span>

- <span data-ttu-id="db19c-129">**NX_SUCCESS (0x0)** Utworzono prawidłowy rekord klienta</span><span class="sxs-lookup"><span data-stu-id="db19c-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="db19c-130">Klient **NX_DHCPV6_NOT_BOUND** (0xE94) nie jest w stanie powiązanym, w związku z czym nie został przypisany prawidłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="db19c-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="db19c-131">**NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="db19c-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="db19c-132">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="db19c-132">Allowed From</span></span>

<span data-ttu-id="db19c-133">Wątki</span><span class="sxs-lookup"><span data-stu-id="db19c-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="db19c-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="db19c-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="db19c-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db19c-135">See Also</span></span>

- <span data-ttu-id="db19c-136">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="db19c-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="db19c-137">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="db19c-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="db19c-138">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="db19c-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="db19c-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="db19c-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="db19c-140">Przywróć stan klienta DHCPv6 z zapisanego rekordu</span><span class="sxs-lookup"><span data-stu-id="db19c-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="db19c-141">Prototype</span><span class="sxs-lookup"><span data-stu-id="db19c-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="db19c-142">Opis</span><span class="sxs-lookup"><span data-stu-id="db19c-142">Description</span></span>

<span data-ttu-id="db19c-143">Ta usługa umożliwia aplikacji DHCPv6 ponowne utworzenie stanu klienta DHCPv6 z poprzedniej sesji przez zaktualizowanie klienta protokołu DHCPv6 przy użyciu rekordu klienta DHCPv6 wskazywanego przez record_ptr, a następnie zaktualizowanie pozostałego czasu w dzierżawie klienta DHCPv6 przy użyciu time_elapsed danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="db19c-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="db19c-144">Dzięki temu aplikacja kliencka DHCPv6 ma odtworzyć swój klient DHCPv6, na przykład po wyłączeniu.</span><span class="sxs-lookup"><span data-stu-id="db19c-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="db19c-145">Wymaga to, aby aplikacja kliencka DHCPv6 utworzyła rekord klienta DHCPv6 przed wyłączeniem i zapisała ten rekord w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="db19c-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="db19c-146">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="db19c-146">Input Parameters</span></span>

- <span data-ttu-id="db19c-147">**dhcpv6_ptr** Wskaźnik do klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="db19c-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="db19c-148">**record_ptr** Wskaźnik do rekordu klienta DHCPv6</span><span class="sxs-lookup"><span data-stu-id="db19c-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="db19c-149">**time_elapsed** Czas odejmowania od pozostałego czasu dzierżawy w rekordzie wejściowego klienta</span><span class="sxs-lookup"><span data-stu-id="db19c-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="db19c-150">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="db19c-150">Return Values</span></span>

- <span data-ttu-id="db19c-151">**NX_SUCCESS (0x0)** Przywrócono rekord klienta</span><span class="sxs-lookup"><span data-stu-id="db19c-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="db19c-152">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="db19c-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="db19c-153">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="db19c-153">Allowed From</span></span>

<span data-ttu-id="db19c-154">Wątki</span><span class="sxs-lookup"><span data-stu-id="db19c-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="db19c-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="db19c-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="db19c-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db19c-156">See Also</span></span>

- <span data-ttu-id="db19c-157">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="db19c-157">nx_dhcpv6_client_get_record</span></span>