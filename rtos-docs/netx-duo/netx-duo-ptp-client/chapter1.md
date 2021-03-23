---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo PTP Client
description: Ten rozdział zawiera wprowadzenie do klienta PTP usługi Azure RTO NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821709"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="baf6c-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo PTP Client</span><span class="sxs-lookup"><span data-stu-id="baf6c-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="baf6c-104">Program Azure RTO NetX Duo jest implementacją klienta w wersji 2, IEEE 1588-2008.</span><span class="sxs-lookup"><span data-stu-id="baf6c-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="baf6c-105">Służy do synchronizowania zegarów między MCUs w sieci lokalnej przez wzajemne komunikowanie się za pośrednictwem protokołu IPv4 lub IPv6 pakietów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="baf6c-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="baf6c-106">Instalator klienta PTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="baf6c-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="baf6c-107">Aby zapewnić prawidłowe działanie, pakiet klienta protokołu PTP wymaga, aby wystąpienie NetX Duo zostało już utworzone.</span><span class="sxs-lookup"><span data-stu-id="baf6c-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="baf6c-108">Domyślnie klient protokołu PTP sprzęga grupę multiemisji IPv4.</span><span class="sxs-lookup"><span data-stu-id="baf6c-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="baf6c-109">Aby można było uruchomić klienta protokołu PTP w sieci IPv6, `NX_ENABLE_IPV6_MULTICAST` należy go zdefiniować podczas kompilowania biblioteki NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="baf6c-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="baf6c-110">Podczas tworzenia klienta programu PTP aplikacja musi zapewnić funkcję wywołania zwrotnego, aby obsługiwać sygnatury czasowe pakietów przychodzących i wychodzących.</span><span class="sxs-lookup"><span data-stu-id="baf6c-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="baf6c-111">Aby osiągnąć wysoką rozdzielczość, zalecamy stosowanie aplikacji do generowania sygnatur czasowych przy użyciu czasomierza o wysokiej rozdzielczości.</span><span class="sxs-lookup"><span data-stu-id="baf6c-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="baf6c-112">Do uruchomienia protokołu PTP w symulatorze zostanie udostępniona implementacja oparta na oprogramowaniu `nx_ptp_client_soft_clock_callback` .</span><span class="sxs-lookup"><span data-stu-id="baf6c-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="baf6c-113">Klient PTP wymaga puli pakietów do przesyłania komunikatów PTP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="baf6c-114">Rozmiar ładunku puli pakietów nie może być mniejszy niż `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` , czyli 108 bajtów dla IPv4, i 128 bajtów, jeśli jest włączony protokół IPv6.</span><span class="sxs-lookup"><span data-stu-id="baf6c-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="baf6c-115">Po utworzeniu klienta programu PTP aplikacja może uruchomić klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="baf6c-116">Synchronizacja jest wykonywana w wątku pomocnika PTP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="baf6c-117">Można określić funkcję wywołania zwrotnego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="baf6c-117">An event callback function can be specified.</span></span> <span data-ttu-id="baf6c-118">Zostanie wywołana w przypadku wystąpienia jednego z następujących zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="baf6c-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="baf6c-119">Wybrano wzorzec;</span><span class="sxs-lookup"><span data-stu-id="baf6c-119">A master is selected;</span></span> 
* <span data-ttu-id="baf6c-120">Czas jest kalibrowany.</span><span class="sxs-lookup"><span data-stu-id="baf6c-120">The time is calibrated.</span></span>
* <span data-ttu-id="baf6c-121">Główny limit czasu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="baf6c-122">Komunikaty klienta PTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="baf6c-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="baf6c-123">Klient PTP NetX Duo implementuje tylko mechanizm opóźnienia żądania-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="baf6c-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="baf6c-124">Klient protokołu PTP otwiera dwa porty UDP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="baf6c-125">*319* dla komunikatu o **zdarzeniu** i *320* dla komunikatu **ogólnego** .</span><span class="sxs-lookup"><span data-stu-id="baf6c-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="baf6c-126">Dla tego mechanizmu istnieje pięć typów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="baf6c-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="baf6c-127">**Ogłoszenie**.</span><span class="sxs-lookup"><span data-stu-id="baf6c-127">**Announce**.</span></span> <span data-ttu-id="baf6c-128">Jest to komunikat o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-128">This is an event message.</span></span> <span data-ttu-id="baf6c-129">Służy do wyboru zegara głównego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="baf6c-130">**Synchronizuj**. Jest to komunikat o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="baf6c-131">Służy do wysyłania znacznika czasu pochodzenia i obliczania opóźnienia ścieżki od wzorca do klienta.</span><span class="sxs-lookup"><span data-stu-id="baf6c-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="baf6c-132">**Follow_Up**.</span><span class="sxs-lookup"><span data-stu-id="baf6c-132">**Follow_Up**.</span></span> <span data-ttu-id="baf6c-133">Jest to komunikat ogólny.</span><span class="sxs-lookup"><span data-stu-id="baf6c-133">This is a general message.</span></span> <span data-ttu-id="baf6c-134">Jest on opcjonalny i używany do korygowania sygnatury czasowej źródła w powiązanym komunikacie synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="baf6c-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="baf6c-135">Jest on wysyłany tylko wtedy, gdy ustawiono flagę dwóch etapów synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="baf6c-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="baf6c-136">**Delay_Req**.</span><span class="sxs-lookup"><span data-stu-id="baf6c-136">**Delay_Req**.</span></span> <span data-ttu-id="baf6c-137">Jest to komunikat o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-137">This is an event message.</span></span> <span data-ttu-id="baf6c-138">Jest wysyłany z klienta programu PTP w celu obliczenia opóźnienia ścieżki od klienta do serwera głównego przy odebraniu Delay_Resp.</span><span class="sxs-lookup"><span data-stu-id="baf6c-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="baf6c-139">**Delay_Resp**.</span><span class="sxs-lookup"><span data-stu-id="baf6c-139">**Delay_Resp**.</span></span> <span data-ttu-id="baf6c-140">Jest to komunikat o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-140">This is an event message.</span></span> <span data-ttu-id="baf6c-141">Jest on wysyłany z serwera głównego do klienta w celu obliczenia opóźnienia ścieżki od klienta do serwera głównego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="baf6c-142">*Uwaga "nie zaimplementowano algorytmu" najlepszy wzorzec zegara ". Tylko pierwszy zegar główny jest akceptowany, gdy klient programu PTP jest w stanie nasłuchiwania.*</span><span class="sxs-lookup"><span data-stu-id="baf6c-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="baf6c-143">Wywołanie zwrotne zegara klienta PTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="baf6c-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="baf6c-144">Aby synchronizować zegar z serwera głównego, klient PTP potrzebuje zegara lokalnego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="baf6c-145">Funkcja wywołania zwrotnego zegara jest przenoszona do klienta PTP podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="baf6c-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="baf6c-146">Poniżej określono format procedury wywołania zwrotnego zegara.</span><span class="sxs-lookup"><span data-stu-id="baf6c-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="baf6c-147">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="baf6c-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="baf6c-148">*client_ptr* punkty do klienta PTP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="baf6c-149">*operacja* określa operację wywołania zwrotnego, prawidłowe wartości są zdefiniowane, jak pokazano na poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="baf6c-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="baf6c-150">**NX_PTP_CLIENT_CLOCK_INIT** Zainicjuj zegar.</span><span class="sxs-lookup"><span data-stu-id="baf6c-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="baf6c-151">**NX_PTP_CLIENT_CLOCK_SET** Ustaw bieżącą sygnaturę czasową określoną przez `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="baf6c-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="baf6c-152">**NX_PTP_CLIENT_CLOCK_GET** Zwróć bieżącą sygnaturę czasową do `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="baf6c-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="baf6c-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Wyodrębnij sygnaturę czasową z `packet_ptr` do `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="baf6c-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="baf6c-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Dostosuj bieżącą sygnaturę czasową mniejszą niż *1* sekunda.</span><span class="sxs-lookup"><span data-stu-id="baf6c-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="baf6c-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Oznacz, `packet_ptr` które są wymagane do powiadomienia klienta PTP o sygnaturze czasowej podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="baf6c-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="baf6c-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Aktualizuj czasomierz elastyczny.</span><span class="sxs-lookup"><span data-stu-id="baf6c-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="baf6c-157">Może być ignorowany przez zegar sprzętu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="baf6c-158">*time_ptr* punkty do sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="baf6c-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="baf6c-159">*packet_ptr* punkty do pakietu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="baf6c-160">*callback_data* punkty na nieprzezroczyste dane wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="baf6c-161">NX_PTP_TIME typ danych jest zdefiniowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="baf6c-161">The NX_PTP_TIME data type is defined as follows.</span></span>
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="baf6c-162">Wywołanie zwrotne zdarzenia klienta PTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="baf6c-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="baf6c-163">Funkcję wywołania zwrotnego zdarzenia można skonfigurować w celu powiadomienia aplikacji o stanie klienta programu PTP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="baf6c-164">Format procedury wywołania zwrotnego zdarzenia jest definiowany jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="baf6c-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="baf6c-165">Parametry wejściowe to.</span><span class="sxs-lookup"><span data-stu-id="baf6c-165">The input parameters are.</span></span>
* <span data-ttu-id="baf6c-166">*client_ptr* punkty do klienta PTP.</span><span class="sxs-lookup"><span data-stu-id="baf6c-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="baf6c-167">*zdarzenie* określa zdarzenie wywołania zwrotnego, prawidłowe wartości są zdefiniowane jako:</span><span class="sxs-lookup"><span data-stu-id="baf6c-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="baf6c-168">**NX_PTP_CLIENT_EVENT_MASTER** Wybrano zegar główny.</span><span class="sxs-lookup"><span data-stu-id="baf6c-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="baf6c-169">**NX_PTP_CLIENT_EVENT_SYNC** Klient PTP jest skalibrowany.</span><span class="sxs-lookup"><span data-stu-id="baf6c-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="baf6c-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Zegar główny to limit czasu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="baf6c-171">*event_data* określa dane związane ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="baf6c-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="baf6c-172">Gdy zdarzenie jest **NX_PTP_CLIENT_EVENT_MASTER**, event_data wskazuje na `NX_PTP_CLIENT_MASTER` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="baf6c-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="baf6c-173">Gdy zdarzenie jest **NX_PTP_CLIENT_EVENT_SYNC**, dane zdarzenia wskazują na `NX_PTP_CLIENT_SYNC` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="baf6c-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="baf6c-174">Komunikacja klienta PTP w NetX Duo</span><span class="sxs-lookup"><span data-stu-id="baf6c-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="baf6c-175">Jak wspomniano wcześniej, klient PTP NetX Duo obsługuje tylko mechanizm opóźnienia żądania.</span><span class="sxs-lookup"><span data-stu-id="baf6c-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="baf6c-176">Ten mechanizm mierzy Średnie opóźnienie ścieżki między klientem a zegarem głównym, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="baf6c-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="baf6c-177">Klient otrzymuje komunikat *ogłoszenia* od wzorca i wybiera go jako najlepszy serwer główny.</span><span class="sxs-lookup"><span data-stu-id="baf6c-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="baf6c-178">Klient odbiera komunikat *synchronizacji* z serwera głównego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="baf6c-179">Sygnatura czasowa *T1* jest sygnaturą czasową źródła w tej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="baf6c-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="baf6c-180">Sygnatura czasowa *T2* jest odczytywana z zegara lokalnego po odebraniu tego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="baf6c-181">Klient odbiera komunikat *Follow_Up* od serwera głównego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="baf6c-182">Ten komunikat jest opcjonalny i prawidłowy tylko wtedy, gdy ustawiono dwa kroki flagi *synchronizacji* .</span><span class="sxs-lookup"><span data-stu-id="baf6c-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="baf6c-183">Następnie sygnatura czasowa *T1* jest aktualizowana do sygnatury czasowej źródła w tej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="baf6c-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="baf6c-184">Klient wysyła komunikat *Delay_Req* do serwera głównego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="baf6c-185">Sygnatura czasowa *T3* jest odczytywana z zegara lokalnego podczas przesyłania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="baf6c-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="baf6c-186">Klient odbiera komunikat *Delay_Resp* od serwera głównego.</span><span class="sxs-lookup"><span data-stu-id="baf6c-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="baf6c-187">Sygnatura czasowa *T4* jest sygnaturą czasową odbioru w tej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="baf6c-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="baf6c-188">Średnie opóźnienie ścieżki jest obliczane, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="baf6c-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="baf6c-189">Przesunięcie od wzorca jest obliczane, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="baf6c-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="baf6c-190">***CorrectionField*** jest ignorowany podczas calculation._</span><span class="sxs-lookup"><span data-stu-id="baf6c-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>