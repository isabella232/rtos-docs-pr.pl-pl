---
title: Dodatek A — opis funkcji przywracania stanu
description: Opcja konfiguracji klienta usługi Azure RTO NetX DHDP, NX_DHCP_CLIENT_RESTORE_STATE umożliwia systemowi przywrócenie utworzonego wcześniej rekordu klienta DHCP w stanie związanym między ponownymi uruchomieniami systemu.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be8b5dc4885951bee3dba38af6fe5e21b81aa767
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822711"
---
# <a name="appendix-a---description-of-the-restore-state-feature"></a><span data-ttu-id="a7af2-103">Dodatek A — opis funkcji przywracania stanu</span><span class="sxs-lookup"><span data-stu-id="a7af2-103">Appendix A - Description of the Restore State Feature</span></span>

<span data-ttu-id="a7af2-104">Opcja konfiguracji klienta usługi Azure RTO NetX DHDP, NX_DHCP_CLIENT_RESTORE_STATE umożliwia systemowi przywrócenie utworzonego wcześniej rekordu klienta DHCP w stanie związanym między ponownymi uruchomieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="a7af2-104">The Azure RTOS NetX DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="a7af2-105">Gdy ta opcja jest włączona, aplikacja może wstrzymywać i wznawiać wątek klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="a7af2-106">Istnieje również usługa do aktualizowania klienta DHCP z upływem czasu między wstrzymaniem i wznowieniem wątku.</span><span class="sxs-lookup"><span data-stu-id="a7af2-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="a7af2-107">Przywracanie klienta DHCP między ponownymi uruchomieniami</span><span class="sxs-lookup"><span data-stu-id="a7af2-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="a7af2-108">Przed przystąpieniem do przywracania klienta DHCP po ponownym uruchomieniu komputera został wcześniej utworzony klient DHCP, który musi dotrzeć do powiązanego stanu i ma przypisany adres IP z serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="a7af2-109">Zanim będzie to możliwe, aplikacja DHCP musi zapisać bieżący rekord klienta DHCP w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="a7af2-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="a7af2-110">W systemie musi być również niezależny opiekun czasowy, aby śledzić czas, który upłynął podczas tego stanu zasilania.</span><span class="sxs-lookup"><span data-stu-id="a7af2-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="a7af2-111">W przypadku włączania aplikacji tworzy nowe wystąpienie klienta DHCP, a następnie aktualizuje je przy użyciu utworzonego wcześniej rekordu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="a7af2-112">Czas, który upłynął, jest uzyskiwany z "czasu opiekuna", a następnie stosowany do pozostałego czasu dzierżawy klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="a7af2-113">Należy zauważyć, że może to spowodować zmianę Stanów przez klienta DHCP, np. z powiązanym z ODNAWIAniem.</span><span class="sxs-lookup"><span data-stu-id="a7af2-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="a7af2-114">W tym momencie aplikacja może wznowić działanie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="a7af2-115">Jeśli czas, który upłynął podczas włączania usługi, powoduje, że stan klienta DHCP w stanie ODNOWIENIa lub ponownego powiązania, klient DHCP automatycznie inicjuje komunikaty DHCP żądające odnowienia lub ponownego powiązania dzierżawy adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="a7af2-116">Jeśli adres IP wygasł, klient DHCP automatycznie wyczyści adres IP w wystąpieniu IP i rozpocznie proces DHCP ze stanu INIT, żądając nowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="a7af2-117">W ten sposób klient DHCP może działać między ponownymi uruchomieniami tak, jakby nie został przerwany.</span><span class="sxs-lookup"><span data-stu-id="a7af2-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="a7af2-118">Poniżej znajduje się ilustracja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a7af2-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="a7af2-119">To zakłada, że klient DHCP działa tylko w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="a7af2-119">This assumes DHCP Client is running only on the primary interface.</span></span>

```C
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{


  /* No previously saved Client record. Start the DHCP Client in the INIT state. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  do
  {
  
    /* Wait for DHCP to assign the IP address. */
  } while (status != NX_SUCCESS);

  /* We have a valid IP address. */

  /* At some point decide we power down the system. */

  /* Save the Client state data which we will subsequently need to restore the DHCP  
     Client. */
  status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);         

  /* Copy this memory to non-volatile memory (not shown). */

  /* Delete the IP and DHCP Client instances before powering down. */
  nx_dhcp_delete(&dhcp_0);

  nx_ip_delete(&ip_0);

  /* Ready to power down, having released other resources as necessary. */

}
else
{

  /* The application has determined there is a previously saved record. We will 
     restore it to the current DHCP Client instance. */

  /* Get the previous Client state data from non-volatile memory. */

  /* Apply the record to the current Client instance. This will also 
     update the IP instance with IP address, mask etc. */
  status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

     if (status != NX_SUCCESS)
      return;

     /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
     status = nx_dhcp_resume(&dhcp_0);

     if (status != NX_SUCCESS)
      return;

}
```

## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="a7af2-120">Wznawianie wątku klienta DHCP po zawieszeniu</span><span class="sxs-lookup"><span data-stu-id="a7af2-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="a7af2-121">Aby wstrzymać wątek klienta DHCP bez wyłączania, aplikacja wywołuje *nx_dhcp_suspend* na kliencie DHCP, który osiągnął stan powiązany i ma prawidłowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="a7af2-122">Gdy jest gotowy do wznowienia klienta DHCP, najpierw wywołuje *nx_dhcp_client_update_time_remaining* , aby zaktualizować pozostały czas w dzierżawie adresu DHCP (Uzyskiwanie czasu od niezależnego opiekuna).</span><span class="sxs-lookup"><span data-stu-id="a7af2-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="a7af2-123">Następnie wywołuje *nx_dhcp_resume* , aby wznowić wątek klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="a7af2-124">W przypadku przełączenia stanu klienta DHCP w stanie ODNOWIENIa lub ponownego powiązania klient DHCP automatycznie inicjuje komunikaty DHCP żądające odnowienia lub ponownego powiązania dzierżawy adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="a7af2-125">Jeśli adres IP wygasł, klient DHCP automatycznie wyczyści adres IP i rozpocznie proces DHCP ze stanu INIT, żądając nowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="a7af2-126">Poniżej znajduje się ilustracja przedstawiająca korzystanie z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a7af2-126">Below is an illustration of using this feature.</span></span>

```C
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   
    /* Wait for DHCP to obtain an IP address. */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the 
     network... */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the
     elapsed time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}
```

<span data-ttu-id="a7af2-127">Poniżej znajduje się lista usług służących do przywracania stanu klienta DHCP z pamięci oraz do wstrzymywania i wznawiania klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="a7af2-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="a7af2-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="a7af2-129">Utwórz rekord bieżącego stanu klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-130">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-130">Prototype</span></span>

```C
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, 
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="a7af2-131">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-131">Description</span></span>

<span data-ttu-id="a7af2-132">Ta usługa umożliwia zapisanie klienta DHCP uruchomionego na pierwszym interfejsie z włączonym protokołem DHCP, który znajduje się w wystąpieniu klienta DHCP, do rekordu wskazywanego przez record_ptr.</span><span class="sxs-lookup"><span data-stu-id="a7af2-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="a7af2-133">Dzięki temu aplikacja kliencka DHCP przywraca swój stan klienta DHCP po wystąpieniu programu, na przykład o wyłączeniu i ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="a7af2-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="a7af2-134">Aby zapisać rekord klienta DHCP w określonym interfejsie, jeśli dla usługi DHCP jest włączony więcej niż jeden interfejs, Użyj usługi *nx_dhcp_interface_client_get_record* .</span><span class="sxs-lookup"><span data-stu-id="a7af2-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-135">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-135">Input Parameters</span></span>

- <span data-ttu-id="a7af2-136">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-136">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="a7af2-137">**record_ptr** Wskaźnik do rekordu klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-137">**record_ptr** Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-138">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-138">Return Values</span></span>

- <span data-ttu-id="a7af2-139">Utworzono rekord klienta **NX_SUCCESS** (0x0)</span><span class="sxs-lookup"><span data-stu-id="a7af2-139">**NX_SUCCESS** (0x0) Client record created</span></span>

- <span data-ttu-id="a7af2-140">Klient **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="a7af2-140">**NX_DHCP_NOT_BOUND** (0x94) Client not in Bound state</span></span>

- <span data-ttu-id="a7af2-141">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-141">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="a7af2-142">**NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a7af2-142">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-143">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-143">Allowed From</span></span>

<span data-ttu-id="a7af2-144">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-145">Example</span></span>

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="a7af2-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="a7af2-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="a7af2-147">Utwórz rekord bieżącego stanu klienta DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="a7af2-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-148">Prototype</span></span>

```C
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, 
                                 UINT interface_index,
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```
### <a name="description"></a><span data-ttu-id="a7af2-149">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-149">Description</span></span>

<span data-ttu-id="a7af2-150">Ta usługa umożliwia zapisanie klienta DHCP działającego w określonym interfejsie do rekordu wskazywanego przez record_ptr.</span><span class="sxs-lookup"><span data-stu-id="a7af2-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="a7af2-151">Dzięki temu aplikacja kliencka DHCP przywraca swój stan klienta DHCP po wystąpieniu programu, na przykład o wyłączeniu i ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="a7af2-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-152">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-152">Input Parameters</span></span>

- <span data-ttu-id="a7af2-153">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-153">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="a7af2-154">**interface_index** Indeks, na którym ma zostać pobrany rekord</span><span class="sxs-lookup"><span data-stu-id="a7af2-154">**interface_index** Index on which to get record</span></span>

- <span data-ttu-id="a7af2-155">**record_ptr** Wskaźnik do rekordu klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-155">**record_ptr** Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-156">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-156">Return Values</span></span>

- <span data-ttu-id="a7af2-157">Utworzono rekord klienta **NX_SUCCESS** (0x0)</span><span class="sxs-lookup"><span data-stu-id="a7af2-157">**NX_SUCCESS** (0x0) Client record created</span></span>

- <span data-ttu-id="a7af2-158">Klient **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany</span><span class="sxs-lookup"><span data-stu-id="a7af2-158">**NX_DHCP_NOT_BOUND** (0x94) Client not in Bound state</span></span>

- <span data-ttu-id="a7af2-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0X9A) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="a7af2-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Invalid interface index</span></span>

- <span data-ttu-id="a7af2-160">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-160">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="a7af2-161">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="a7af2-161">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-162">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-162">Allowed From</span></span>

<span data-ttu-id="a7af2-163">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-164">Example</span></span>

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="a7af2-165">nx_dhcp_ client_restore_record</span><span class="sxs-lookup"><span data-stu-id="a7af2-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="a7af2-166">Przywróć klienta DHCP z wcześniej zapisanego rekordu</span><span class="sxs-lookup"><span data-stu-id="a7af2-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-167">Prototype</span></span>

```C
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD       
                                    *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="a7af2-168">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-168">Description</span></span>

<span data-ttu-id="a7af2-169">Ta usługa umożliwia aplikacji przywrócenie klienta DHCP z poprzedniej sesji przy użyciu rekordu klienta DHCP wskazywanego przez record_ptr.</span><span class="sxs-lookup"><span data-stu-id="a7af2-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="a7af2-170">Dane wejściowe time_elapsed są stosowane do pozostałego czasu dzierżawy klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="a7af2-171">Wymaga to, aby aplikacja klienta DHCP utworzyła rekord klienta DHCP przed wyłączeniem i zapisała ten rekord w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="a7af2-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="a7af2-172">Jeśli dla klienta DHCP jest włączony więcej niż jeden interfejs, ta usługa zostanie zastosowana do pierwszego prawidłowego interfejsu znalezionego w wystąpieniu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-173">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-173">Input Parameters</span></span>

- <span data-ttu-id="a7af2-174">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-174">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="a7af2-175">**record_ptr** Wskaźnik do rekordu klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-175">**record_ptr** Pointer to DHCP Client record</span></span>

- <span data-ttu-id="a7af2-176">**time_elapsed** Czas odejmowania od pozostałego czasu dzierżawy w rekordzie wejściowego klienta</span><span class="sxs-lookup"><span data-stu-id="a7af2-176">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-177">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-177">Return Values</span></span>

- <span data-ttu-id="a7af2-178">Przywrócono rekord klienta **NX_SUCCESS** (0x0)</span><span class="sxs-lookup"><span data-stu-id="a7af2-178">**NX_SUCCESS** (0x0) Client record restored</span></span>

- <span data-ttu-id="a7af2-179">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) Brak interfejsów z uruchomionym protokołem DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-179">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces running DHCP</span></span>

- <span data-ttu-id="a7af2-180">**NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a7af2-180">**NX_PTR_ERROR** (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-181">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-181">Allowed From</span></span>

<span data-ttu-id="a7af2-182">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-183">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-183">Example</span></span>
```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="a7af2-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="a7af2-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="a7af2-185">Przywróć klienta DHCP z wcześniej zapisanego rekordu w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="a7af2-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-186">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-186">Prototype</span></span>

```C
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD       
                                              *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="a7af2-187">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-187">Description</span></span>

<span data-ttu-id="a7af2-188">Ta usługa umożliwia aplikacji przywrócenie klienta DHCP w określonym interfejsie przy użyciu rekordu klienta DHCP wskazywanego przez record_ptr.</span><span class="sxs-lookup"><span data-stu-id="a7af2-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="a7af2-189">Dane wejściowe time_elapsed są stosowane do pozostałego czasu dzierżawy klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="a7af2-190">Wymaga to, aby aplikacja klienta DHCP utworzyła rekord klienta DHCP przed wyłączeniem i zapisała ten rekord w pamięci nieulotnej.</span><span class="sxs-lookup"><span data-stu-id="a7af2-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="a7af2-191">Jeśli dla klienta DHCP jest włączony więcej niż jeden interfejs, ta usługa zostanie zastosowana do pierwszego prawidłowego interfejsu znalezionego w wystąpieniu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-192">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-192">Input Parameters</span></span>

- <span data-ttu-id="a7af2-193">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-193">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="a7af2-194">**record_ptr** Wskaźnik do rekordu klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-194">**record_ptr** Pointer to DHCP Client record</span></span>

- <span data-ttu-id="a7af2-195">**time_elapsed** Czas odejmowania od pozostałego czasu dzierżawy w rekordzie wejściowego klienta</span><span class="sxs-lookup"><span data-stu-id="a7af2-195">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-196">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-196">Return Values</span></span>

- <span data-ttu-id="a7af2-197">Przywrócono rekord klienta **NX_SUCCESS** (0x0)</span><span class="sxs-lookup"><span data-stu-id="a7af2-197">**NX_SUCCESS** (0x0) Client record restored</span></span>

- <span data-ttu-id="a7af2-198">Klient **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany z adresem IP</span><span class="sxs-lookup"><span data-stu-id="a7af2-198">**NX_DHCP_NOT_BOUND** (0x94) Client not bound to IP address</span></span>

- <span data-ttu-id="a7af2-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0X9A) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="a7af2-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Invalid interface index</span></span>

- <span data-ttu-id="a7af2-200">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-200">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="a7af2-201">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="a7af2-201">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-202">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-202">Allowed From</span></span>

<span data-ttu-id="a7af2-203">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-204">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-204">Example</span></span>

```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="a7af2-205">nx_dhcp_ client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="a7af2-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="a7af2-206">Aktualizowanie pozostałego czasu na dzierżawie klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-207">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-207">Prototype</span></span>

```C
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr
                                           ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="a7af2-208">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-208">Description</span></span>

<span data-ttu-id="a7af2-209">Ta usługa aktualizuje pozostały czas w dzierżawie adresu IP klienta DHCP przy użyciu time_elapsed danych wejściowych pierwszego interfejsu włączonego dla protokołu DHCP w wystąpieniu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="a7af2-210">Aplikacja musi wstrzymać wątek klienta DHCP przed użyciem tej usługi przy użyciu *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="a7af2-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="a7af2-211">Po wywołaniu tej usługi aplikacja może wznowić wątek klienta DHCP, wywołując *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="a7af2-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="a7af2-212">Jest to przeznaczone dla aplikacji klienckich DHCP, które muszą wstrzymać wątek klienta DHCP przez pewien czas, a następnie zaktualizować pozostały czas dzierżawy adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

> [!NOTE]
> <span data-ttu-id="a7af2-213">Ta usługa nie jest przeznaczona do użycia z *nx_dhcp_client_get_record* i *nx_dhcp_client_restore_record* opisanymi wcześniej).</span><span class="sxs-lookup"><span data-stu-id="a7af2-213">This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="a7af2-214">Te usługi zostały opisane wcześniej w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a7af2-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-215">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-215">Input Parameters</span></span>

- <span data-ttu-id="a7af2-216">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-216">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="a7af2-217">**time_elapsed** Czas odejmowania od pozostałej części czasu dzierżawy adresu IP</span><span class="sxs-lookup"><span data-stu-id="a7af2-217">**time_elapsed** Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-218">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-218">Return Values</span></span>

- <span data-ttu-id="a7af2-219">**NX_SUCCESS** (0x0) aktualizacja dzierżawy adresu IP klienta</span><span class="sxs-lookup"><span data-stu-id="a7af2-219">**NX_SUCCESS** (0x0) Client IP lease updated</span></span>

- <span data-ttu-id="a7af2-220">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) brak włączonych interfejsów dla protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-220">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="a7af2-221">**NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a7af2-221">**NX_PTR_ERROR** (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-222">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-222">Allowed From</span></span>

<span data-ttu-id="a7af2-223">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-224">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-224">Example</span></span>

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="a7af2-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="a7af2-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="a7af2-226">Zaktualizuj pozostały czas w dzierżawie klienta DHCP w określonym interfejsie</span><span class="sxs-lookup"><span data-stu-id="a7af2-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-227">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-227">Prototype</span></span>

```C
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="a7af2-228">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-228">Description</span></span>

<span data-ttu-id="a7af2-229">Ta usługa aktualizuje pozostały czas w dzierżawie adresu IP klienta DHCP przy użyciu time_elapsed danych wejściowych w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="a7af2-230">Aplikacja musi wstrzymać wątek klienta DHCP przed użyciem tej usługi przy użyciu *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="a7af2-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="a7af2-231">Po wywołaniu tej usługi aplikacja może wznowić wątek klienta DHCP, wywołując *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="a7af2-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="a7af2-232">Zwróć uwagę, że Wstrzymywanie i wznawianie wątku klienta DHCP ma zastosowanie do wszystkich interfejsów włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="a7af2-233">Jest to przeznaczone dla aplikacji klienckich DHCP, które muszą wstrzymać wątek klienta DHCP przez pewien czas, a następnie zaktualizować pozostały czas dzierżawy adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

> [!NOTE] 
> <span data-ttu-id="a7af2-234">Ta usługa nie jest przeznaczona do użycia z *nx_dhcp_client_get_record* i *nx_dhcp_client_restore_record* opisanymi wcześniej).</span><span class="sxs-lookup"><span data-stu-id="a7af2-234">This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="a7af2-235">Te usługi zostały opisane wcześniej w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a7af2-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-236">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-236">Input Parameters</span></span>

- <span data-ttu-id="a7af2-237">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-237">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="a7af2-238">**interface_index** Indeks do interfejsu do zastosowania, który upłynął czas do</span><span class="sxs-lookup"><span data-stu-id="a7af2-238">**interface_index** Index to interface to apply elapsed time to</span></span>

- <span data-ttu-id="a7af2-239">**time_elapsed** Czas odejmowania od pozostałej części czasu dzierżawy adresu IP</span><span class="sxs-lookup"><span data-stu-id="a7af2-239">**time_elapsed** Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-240">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-240">Return Values</span></span>

- <span data-ttu-id="a7af2-241">**NX_SUCCESS** (0x0) aktualizacja dzierżawy adresu IP klienta</span><span class="sxs-lookup"><span data-stu-id="a7af2-241">**NX_SUCCESS** (0x0) Client IP lease updated</span></span>

- <span data-ttu-id="a7af2-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0X9A) Nieprawidłowy indeks interfejsu</span><span class="sxs-lookup"><span data-stu-id="a7af2-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Invalid interface index</span></span>

- <span data-ttu-id="a7af2-243">NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-243">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="a7af2-244">NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy</span><span class="sxs-lookup"><span data-stu-id="a7af2-244">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-245">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-245">Allowed From</span></span>

<span data-ttu-id="a7af2-246">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-247">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-247">Example</span></span>

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_suspend"></a><span data-ttu-id="a7af2-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="a7af2-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="a7af2-249">Wstrzymywanie wątku klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-250">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-250">Prototype</span></span>

```C
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a><span data-ttu-id="a7af2-251">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-251">Description</span></span>

<span data-ttu-id="a7af2-252">Ta usługa wstrzymuje bieżący wątek klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="a7af2-253">Należy pamiętać, że w przeciwieństwie do *nx_dhcp_stop* nie ma zmiany stanu klienta DHCP, gdy ta usługa jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a7af2-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="a7af2-254">Ta usługa zawiesza serwer DHCP działa na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="a7af2-255">Aby zaktualizować stan klienta DHCP z upływem czasu, który upłynął podczas wstrzymania klienta DHCP, zobacz *nx_dhcp_client_update_time_remaining* opisany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a7af2-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="a7af2-256">Aby wznowić wstrzymany wątek klienta DHCP, aplikacja powinna wywołać *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="a7af2-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-257">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-257">Input Parameters</span></span>

- <span data-ttu-id="a7af2-258">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-258">**dhcp_ptr** Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-259">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-259">Return Values</span></span>

- <span data-ttu-id="a7af2-260">**NX_SUCCESS** (0x0) wątek klienta jest zawieszony</span><span class="sxs-lookup"><span data-stu-id="a7af2-260">**NX_SUCCESS** (0x0) Client thread is suspended</span></span>

- <span data-ttu-id="a7af2-261">**NX_PTR_ERROR** (0X16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a7af2-261">**NX_PTR_ERROR** (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-262">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-262">Allowed From</span></span>

<span data-ttu-id="a7af2-263">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-264">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-264">Example</span></span>

```C
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```


## <a name="nx_dhcp_resume"></a><span data-ttu-id="a7af2-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="a7af2-265">nx_dhcp_resume</span></span>

<span data-ttu-id="a7af2-266">Wznów zawieszony wątek klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="a7af2-267">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7af2-267">Prototype</span></span>

```C
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a><span data-ttu-id="a7af2-268">Opis</span><span class="sxs-lookup"><span data-stu-id="a7af2-268">Description</span></span>

<span data-ttu-id="a7af2-269">Ta usługa wznawia zawieszony wątek klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="a7af2-270">Należy pamiętać, że po wznowieniu wątku klienta nie ma zmiany rzeczywistego stanu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="a7af2-271">Aby zaktualizować pozostały czas dla dzierżawy adresu IP klienta DHCP z upływem czasu przed wywołaniem *nx_dhcp_resume*, zobacz *nx_dhcp_client_update_time_remaining* opisany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a7af2-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="a7af2-272">Ta usługa wznawia działanie protokołu DHCP na wszystkich interfejsach włączonych dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="a7af2-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a7af2-273">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a7af2-273">Input Parameters</span></span>

- <span data-ttu-id="a7af2-274">**dhcp_ptr** Wskaźnik do klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="a7af2-274">**dhcp_ptr** Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="a7af2-275">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7af2-275">Return Values</span></span>

- <span data-ttu-id="a7af2-276">**NX_SUCCESS** (0x0) wątek klienta został wznowiony</span><span class="sxs-lookup"><span data-stu-id="a7af2-276">**NX_SUCCESS** (0x0) Client thread is resumed</span></span>

- <span data-ttu-id="a7af2-277">NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a7af2-277">NX_PTR_ERROR (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a7af2-278">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a7af2-278">Allowed From</span></span>

<span data-ttu-id="a7af2-279">Wątki</span><span class="sxs-lookup"><span data-stu-id="a7af2-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a7af2-280">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7af2-280">Example</span></span>

```C
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```