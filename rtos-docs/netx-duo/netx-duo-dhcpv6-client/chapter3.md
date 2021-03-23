---
title: Rozdział 3 — opcje konfiguracji protokołu DHCPv6 w systemie Azure RTO NetX Duo
description: Istnieje kilka opcji konfiguracji do kompilowania protokołu DHCPv6 platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821991"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="8a86e-103">Rozdział 3 — opcje konfiguracji protokołu DHCPv6 w systemie Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="8a86e-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="8a86e-104">Istnieje kilka opcji konfiguracji do kompilowania protokołu DHCPv6 platformy Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8a86e-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="8a86e-105">Poniższa lista zawiera szczegółowy opis:</span><span class="sxs-lookup"><span data-stu-id="8a86e-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="8a86e-106">**NX_DHCPV6_THREAD_PRIORITY** Priorytet wątku klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="8a86e-107">Domyślnie ta wartość określa, że wątek klienta działa o priorytecie 2.</span><span class="sxs-lookup"><span data-stu-id="8a86e-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="8a86e-108">**NX_DHCPV6_MUTEX_WAIT** Opcja przekroczenia limitu czasu w celu uzyskania blokady na wyłączność dla klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="8a86e-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="8a86e-109">Wartość domyślna to TX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="8a86e-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="8a86e-110">**NX_DHCPV6_TICKS_PER_SECOND** Stosunek taktów do sekund.</span><span class="sxs-lookup"><span data-stu-id="8a86e-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="8a86e-111">Jest to zależne od procesora.</span><span class="sxs-lookup"><span data-stu-id="8a86e-111">This is processor dependent.</span></span> <span data-ttu-id="8a86e-112">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="8a86e-112">The default value is 100.</span></span>

- <span data-ttu-id="8a86e-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Przedział czasu (w sekundach), w którym czasomierz okresu istnienia IP aktualizuje czas, przez jaki bieżący adres IP został przypisany do klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="8a86e-114">Domyślnie ta wartość jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="8a86e-114">By default, this value is 1.</span></span>

- <span data-ttu-id="8a86e-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Przedział czasu (w sekundach), po upływie którego czasomierz sesji aktualizuje czas sesji komunikacji klienta z serwerem.</span><span class="sxs-lookup"><span data-stu-id="8a86e-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="8a86e-116">Domyślnie ta wartość jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="8a86e-116">By default, this value is 1.</span></span>

- <span data-ttu-id="8a86e-117">**NX_DHCPV6_MAX_IA_ADDRESS** Maksymalna liczba adresów (IA), które można dodać do rekordu klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="8a86e-118">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="8a86e-118">The default value is 1.</span></span> 

- <span data-ttu-id="8a86e-119">**NX_DHCPV6_NUM_DNS_SERVERS** Liczba serwerów DNS, które mają być przechowywane w rekordzie klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="8a86e-120">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="8a86e-120">The default value is 2.</span></span>

- <span data-ttu-id="8a86e-121">**NX_DHCPV6_NUM_TIME_SERVERS** Liczba serwerów czasu do zapisania w rekordzie klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="8a86e-122">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="8a86e-122">The default value is 1.</span></span>

- <span data-ttu-id="8a86e-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Rozmiar buforu w rekordzie klienta do przechowywania nazwy domeny sieciowej klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="8a86e-124">Wartość domyślna to 30.</span><span class="sxs-lookup"><span data-stu-id="8a86e-124">The default value is 30.</span></span>

- <span data-ttu-id="8a86e-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Rozmiar buforu w rekordzie klienta, aby pomieścić strefę czasową klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="8a86e-126">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="8a86e-126">The default value is 10.</span></span>

- <span data-ttu-id="8a86e-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Rozmiar buforu w rekordzie klienta do przechowywania opcji komunikatu o stanie w odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="8a86e-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="8a86e-128">Wartość domyślna to 100 bajtów.</span><span class="sxs-lookup"><span data-stu-id="8a86e-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="8a86e-129">**NX_DHCPV6_PACKET_TIME_OUT** Limit czasu w sekundach na przydzielenie pakietu z puli pakietów klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="8a86e-130">Wartość domyślna to 3 sekundy.</span><span class="sxs-lookup"><span data-stu-id="8a86e-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="8a86e-131">**NX_DHCPV6_TYPE_OF_SERVICE** Definiuje typ usługi do transmisji pakietów UDP z gniazda klienta DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="8a86e-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="8a86e-132">Wartość domyślna to **NX_IP_NORMAL**.</span><span class="sxs-lookup"><span data-stu-id="8a86e-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="8a86e-133">**NX_DHCPV6_TIME_TO_LIVE** Liczba przypadków, gdy pakiet klienta jest przesyłany przez router sieciowy przed odrzuconym pakietem.</span><span class="sxs-lookup"><span data-stu-id="8a86e-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="8a86e-134">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="8a86e-134">The default value is 0x80.</span></span>

- <span data-ttu-id="8a86e-135">**NX_DHCPV6_QUEUE_DEPTH** Określa liczbę pakietów, które mają być przechowywane w kolejce odbierania w gnieździe UDP klienta zanim NetX Duo odrzuca pakiety.</span><span class="sxs-lookup"><span data-stu-id="8a86e-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="8a86e-136">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="8a86e-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="8a86e-137">Transmisja komunikatów protokołu DHCPv6</span><span class="sxs-lookup"><span data-stu-id="8a86e-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="8a86e-138">Istnieje zestaw opcji klienta protokołu DHCPv6 do ustawiania parametrów w transmisji komunikatów DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="8a86e-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="8a86e-139">Są to:</span><span class="sxs-lookup"><span data-stu-id="8a86e-139">These are:</span></span> 

  - <span data-ttu-id="8a86e-140">początkowy limit czasu</span><span class="sxs-lookup"><span data-stu-id="8a86e-140">initial timeout</span></span>

  - <span data-ttu-id="8a86e-141">Maksymalne opóźnienie w pierwszej transmisji</span><span class="sxs-lookup"><span data-stu-id="8a86e-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="8a86e-142">maksymalny limit czasu retransmisji</span><span class="sxs-lookup"><span data-stu-id="8a86e-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="8a86e-143">Maksymalna liczba ponownych transmisji</span><span class="sxs-lookup"><span data-stu-id="8a86e-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="8a86e-144">Maksymalny czas oczekiwania na odpowiedź serwera</span><span class="sxs-lookup"><span data-stu-id="8a86e-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="8a86e-145">Te parametry mają zastosowanie do każdego z komunikatów klienta DHCPv6:</span><span class="sxs-lookup"><span data-stu-id="8a86e-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="8a86e-146">NIECHCIAN</span><span class="sxs-lookup"><span data-stu-id="8a86e-146">SOLICIT</span></span>

- <span data-ttu-id="8a86e-147">ŻĄDAJĄC</span><span class="sxs-lookup"><span data-stu-id="8a86e-147">REQUEST</span></span>

- <span data-ttu-id="8a86e-148">JĄ</span><span class="sxs-lookup"><span data-stu-id="8a86e-148">RENEW</span></span>

- <span data-ttu-id="8a86e-149">REBIND</span><span class="sxs-lookup"><span data-stu-id="8a86e-149">REBIND</span></span>

- <span data-ttu-id="8a86e-150">Usuwanie</span><span class="sxs-lookup"><span data-stu-id="8a86e-150">RELEASE</span></span>

- <span data-ttu-id="8a86e-151">ZAPROSZENIE</span><span class="sxs-lookup"><span data-stu-id="8a86e-151">DECLINE</span></span>

- <span data-ttu-id="8a86e-152">SPRAWDZENIA</span><span class="sxs-lookup"><span data-stu-id="8a86e-152">CONFIRM</span></span>

- <span data-ttu-id="8a86e-153">POINFORMOWAĆ</span><span class="sxs-lookup"><span data-stu-id="8a86e-153">INFORM</span></span>

<span data-ttu-id="8a86e-154">Poniżej znajduje się pełna lista tych konfigurowalnych opcji i ich domyślnych</span><span class="sxs-lookup"><span data-stu-id="8a86e-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="8a86e-155">values:</span><span class="sxs-lookup"><span data-stu-id="8a86e-155">values:</span></span>

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

<span data-ttu-id="8a86e-156">Aby nie ograniczyć limitu czasu ponownej transmisji, należy ustawić liczbę ponownych transmisji komunikatów na 0.</span><span class="sxs-lookup"><span data-stu-id="8a86e-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="8a86e-157">W przypadku braku limitu liczby ponownych prób wysłania komunikatu klienta protokołu DHCPv6 (ponawianie), ustaw liczbę retransmisji wiadomości na 0.</span><span class="sxs-lookup"><span data-stu-id="8a86e-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="8a86e-158">Bez względu na długość limitu czasu lub liczbę ponownych prób w przypadku wygaśnięcia prawidłowego okresu istnienia adresu IPv6 jest on usuwany z tabeli adresów IP i nie może być już używany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="8a86e-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="8a86e-159">Klient DHCPv6 NetX Duo rozpocznie automatyczne wysyłanie komunikatów żądania, które żądają nowego adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="8a86e-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>