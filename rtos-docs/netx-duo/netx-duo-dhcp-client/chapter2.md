---
title: Rozdział 2 — Instalowanie i używanie klienta DHCP usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta DHCP platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c3df64be337b557f492617c1ef20adc7c0f8d6e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822027"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a><span data-ttu-id="de7bf-103">Rozdział 2 — Instalowanie i używanie klienta DHCP usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="de7bf-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo DHCP Client</span></span>

<span data-ttu-id="de7bf-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta DHCP platformy Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="de7bf-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DHCP Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="de7bf-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="de7bf-105">Product Distribution</span></span>

<span data-ttu-id="de7bf-106">Usługę Azure RTO NetX Duo można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/netxduo> .</span><span class="sxs-lookup"><span data-stu-id="de7bf-106">Azure RTOS NetX Duo can be obtained from our public source code repository at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="de7bf-107">Pakiet zawiera następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="de7bf-107">The package includes the following files:</span></span>

- <span data-ttu-id="de7bf-108">**nxd_dhcp_client. h**: plik nagłówkowy dla NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="de7bf-108">**nxd_dhcp_client.h**: Header file for NetX Duo DHCP</span></span>
- <span data-ttu-id="de7bf-109">plik źródłowy **nxd_dhcp_client. c**: c dla usługi DHCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="de7bf-109">**nxd_dhcp_client.c**: C Source file for DHCP NetX Duo</span></span>
- <span data-ttu-id="de7bf-110">**nxd_dhcp_client.pdf**: Przewodnik użytkownika dotyczący protokołu DHCP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="de7bf-110">**nxd_dhcp_client.pdf**: User Guide for NetX Duo DHCP</span></span> 
    - <span data-ttu-id="de7bf-111">**demo_netxduo_dhcp. c**: pokaz klienta DHCP w programie NetX Duo</span><span class="sxs-lookup"><span data-stu-id="de7bf-111">**demo_netxduo_dhcp.c**: NetX Duo DHCP Client demonstration</span></span>
    - <span data-ttu-id="de7bf-112">**demo_netxduo_multihome_dhcp_client. c**: NetX Duo — pokaz klienta DHCP na wielu interfejsach</span><span class="sxs-lookup"><span data-stu-id="de7bf-112">**demo_netxduo_multihome_dhcp_client.c**: NetX Duo DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="de7bf-113">Instalacja DHCP</span><span class="sxs-lookup"><span data-stu-id="de7bf-113">DHCP Installation</span></span>

<span data-ttu-id="de7bf-114">Aby można było korzystać z klienta DHCP z systemem NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="de7bf-114">To use NetX Duo DHCP Client, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="de7bf-115">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_dhcp_client. h* i *nxd_dhcp_client. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="de7bf-115">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcp_client.h* and *nxd_dhcp_client.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="de7bf-116">Korzystanie z protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="de7bf-116">Using DHCP</span></span>

<span data-ttu-id="de7bf-117">Korzystanie z protokołu DHCP dla NetX Duo jest proste.</span><span class="sxs-lookup"><span data-stu-id="de7bf-117">Using DHCP for NetX Duo is easy.</span></span> <span data-ttu-id="de7bf-118">Zasadniczo kod aplikacji musi zawierać *nxd_dhcp_client. h* , po uwzględnieniu *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="de7bf-118">Basically, the application code must include *nxd_dhcp_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="de7bf-119">Po dołączeniu *nxd_dhcp_client. h* kod aplikacji będzie następnie mógł określić wywołania funkcji DHCP w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="de7bf-119">Once *nxd_dhcp_client.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="de7bf-120">Aplikacja musi również zawierać *nxd_dhcp_client. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="de7bf-120">The application must also include *nxd_dhcp_client.c* in the build process.</span></span> <span data-ttu-id="de7bf-121">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de7bf-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="de7bf-122">To wszystko, co jest wymagane do korzystania z protokołu DHCP NetX.</span><span class="sxs-lookup"><span data-stu-id="de7bf-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="de7bf-123">Należy pamiętać, że ponieważ protokół DHCP korzysta z usług UDP NetX Duo, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-123">Note that since DHCP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="de7bf-124">Aby uzyskać przypisany wcześniej adres IP, klient DHCP może zainicjować proces DHCP z komunikatem żądania i opcją 50 "żądany adres IP" na serwerze DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="de7bf-125">Serwer DHCP odpowie komunikatem ACK, jeśli adres IP jest przydzielany klientowi lub NACK w przypadku odmowy.</span><span class="sxs-lookup"><span data-stu-id="de7bf-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="de7bf-126">W tym drugim przypadku klient DHCP uruchamia ponownie proces DHCP w stanie init z komunikatem odnajdowania i nie ma żądanego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="de7bf-127">Aplikacja hosta najpierw tworzy klienta DHCP, a następnie wywołuje usługę API *nx_dhcp_request_client_ip* , aby ustawić żądany adres IP przed rozpoczęciem procesu DHCP z *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="de7bf-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="de7bf-128">Przykładowa aplikacja DHCP została udostępniona w innym miejscu w tym dokumencie, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="de7bf-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="de7bf-129">W stanie związanym</span><span class="sxs-lookup"><span data-stu-id="de7bf-129">In the Bound State</span></span>

<span data-ttu-id="de7bf-130">Gdy klient DHCP jest w stanie powiązanym, wątek klienta DHCP przetwarza stan klienta raz na interwał (określony przez NX_DHCP_TIME_INTERVAL) i zmniejsza pozostały czas w dzierżawie IP przypisanym do klienta.</span><span class="sxs-lookup"><span data-stu-id="de7bf-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="de7bf-131">Po upływie czasu odnowienia stan klienta DHCP zostanie zaktualizowany do stanu ODNOWIENIa, gdy klient zażąda odnowienia z serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>

## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="de7bf-132">Wysyłanie komunikatów DHCP do serwera</span><span class="sxs-lookup"><span data-stu-id="de7bf-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="de7bf-133">Klient DHCP ma usługi interfejsu API, które umożliwiają aplikacji hosta wysyłanie komunikatów do serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="de7bf-134">Zwróć uwagę, że te usługi nie są przeznaczone dla aplikacji hosta do ręcznego uruchomienia protokołu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol.</span></span>

  - <span data-ttu-id="de7bf-135">*nx_dhcp_release*: wysyła komunikat o zwolnieniu do serwera, gdy aplikacja hosta opuszcza sieć lub potrzebuje jej adresu IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>
  - <span data-ttu-id="de7bf-136">*nx_dhcp_decline*: wysyła komunikat o odrzuceniu do serwera, jeśli aplikacja hosta określi niezależnie od klienta DHCP, że jego adres IP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="de7bf-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>
  - <span data-ttu-id="de7bf-137">*nx_dhcp_forcerenew*: wysyła komunikat Forcerenew do serwera</span><span class="sxs-lookup"><span data-stu-id="de7bf-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>
  - <span data-ttu-id="de7bf-138">*nx_dhcp_send_request*: przyjmuje jako argument typ komunikatu DHCP określony w *nxd_dhcp_client. h* i wysyła komunikat do serwera.</span><span class="sxs-lookup"><span data-stu-id="de7bf-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nxd_dhcp_client.h*, and sends the message to the Server.</span></span> <span data-ttu-id="de7bf-139">Jest to przeznaczone głównie do wysyłania komunikatu o błędzie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="de7bf-140">Aby uzyskać więcej informacji na temat tych usług, zobacz [Opis usług DHCP](chapter3.md)</span><span class="sxs-lookup"><span data-stu-id="de7bf-140">See [Description of DHCP Services](chapter3.md) for more information about these services</span></span> 

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="de7bf-141">Uruchamianie i zatrzymywanie klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="de7bf-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="de7bf-142">Aby zatrzymać klienta DHCP, niezależnie od tego, czy osiągnie on stan związany, aplikacja hosta wywołuje *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="de7bf-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="de7bf-143">Aby ponownie uruchomić klienta DHCP, aplikacja hosta musi najpierw zatrzymać klienta DHCP przy użyciu usługi *nx_dhcp_stop* opisanej powyżej.</span><span class="sxs-lookup"><span data-stu-id="de7bf-143">To restart a DHCP Client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="de7bf-144">Następnie host może wywoływać *nx_dhcp_start* , aby wznowić działanie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="de7bf-145">Jeśli aplikacja hosta chce wyczyścić poprzedni profil klienta DHCP, na przykład jeden uzyskany przez poprzedni serwer DHCP w innej sieci, aplikacja hosta powinna wywołać *nx_dhcp_reinitialize* , aby wykonać to zadanie wewnętrznie przed wywołaniem *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="de7bf-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="de7bf-146">Typową sekwencją może być:</span><span class="sxs-lookup"><span data-stu-id="de7bf-146">A typical sequence might be:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="de7bf-147">W przypadku aplikacji DHCP uruchamianych tylko na jednym interfejsie DHCP zatrzymanie klienta DHCP powoduje także dezaktywację czasomierza klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="de7bf-148">W rezultacie nie jest już śledzony czas pozostały w dzierżawie IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="de7bf-149">Zatrzymanie klienta DHCP w określonym interfejsie nie spowoduje dezaktywacji czasomierza klienta DHCP, ale spowoduje zatrzymanie aktualizacji czasomierza do czasu pozostałej w dzierżawie IP tego interfejsu</span><span class="sxs-lookup"><span data-stu-id="de7bf-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface</span></span>

<span data-ttu-id="de7bf-150">W związku z tym zatrzymanie klienta DHCP nie jest zalecane, chyba że aplikacja hosta wymaga ponownego uruchomienia lub przełączenia sieci.</span><span class="sxs-lookup"><span data-stu-id="de7bf-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="de7bf-151">Korzystanie z klienta DHCP z opcją AutoIP</span><span class="sxs-lookup"><span data-stu-id="de7bf-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="de7bf-152">Klient DHCP z systemem NetX Duo działa równolegle z protokołem AutoIP w aplikacjach, w których DHCP i AutoIP gwarantują adres, w którym serwer DHCP nie jest gwarantowany do udostępnienia lub reagowania.</span><span class="sxs-lookup"><span data-stu-id="de7bf-152">The NetX Duo DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="de7bf-153">Jeśli jednak host nie może wykryć serwera lub uzyskać przypisanego adresu IP, może przełączyć się do protokołu automatyczne IP dla lokalnego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="de7bf-154">Jednak przed wykonaniem tej czynności zaleca się tymczasowe zatrzymanie klienta DHCP w ramach etapów "sondy" i "Obrona".</span><span class="sxs-lookup"><span data-stu-id="de7bf-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="de7bf-155">Po przypisaniu automatycznie adresu IP do hosta klient DHCP może zostać ponownie uruchomiony, a jeśli serwer DHCP stanie się dostępny, adres IP hosta może akceptować adres IP oferowany przez serwer DHCP, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="de7bf-156">Automatycznie adres IP NetX Duo ma powiadomienie o zmianie adresu dla hosta służącego do monitorowania jego działań w przypadku zmiany adresu IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-156">The NetX Duo Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="packet-chaining"></a><span data-ttu-id="de7bf-157">Tworzenie łańcucha pakietów</span><span class="sxs-lookup"><span data-stu-id="de7bf-157">Packet Chaining</span></span>

<span data-ttu-id="de7bf-158">Aby zwiększyć efektywność używania puli pakietów i zasobów pamięci, klient DHCP może obsługiwać przychodzące pakiety łańcucha (datagramy przekraczające jednostkę MTU sterownika) ze sterownika Ethernet.</span><span class="sxs-lookup"><span data-stu-id="de7bf-158">For more efficient use of packet pool and memory resources, the DHCP Client can handle incoming chained packets (datagrams exceeding the driver MTU) from the Ethernet driver.</span></span> <span data-ttu-id="de7bf-159">Jeśli sterownik ma tę możliwość, aplikacja może ustawić pulę pakietów dla odbieranych pakietów poniżej wartości obowiązkowej NX_DHCP_PACKET_PAYLOAD bajtów.</span><span class="sxs-lookup"><span data-stu-id="de7bf-159">If the driver has this capability, the application can set the packet pool for receiving packets to below the mandatory NX_DHCP_PACKET_PAYLOAD bytes.</span></span> <span data-ttu-id="de7bf-160">NX_DHCP_PACKET_PAYLOAD powinny obsługiwać ramkę sieci fizycznej (zazwyczaj Ethernet) oraz 548 bajtów danych komunikatów DHCP oraz protokołów IP i UDP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-160">NX_DHCP_PACKET_PAYLOAD should accommodate the physical network (typically Ethernet) frame, plus 548 bytes of DHCP message data, and IP and UDP.</span></span>

<span data-ttu-id="de7bf-161">Należy zauważyć, że aplikacja może zoptymalizować ładunek pakietu i liczbę pakietów w puli pakietów będącej częścią klienta DHCP, która jest używana do wysyłania komunikatów protokołu DHCP. Może zoptymalizować rozmiar na podstawie oczekiwanego użycia i rozmiaru komunikatów klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-161">Note that the application can optimize the packet payload and number of packets in the packet pool that is part of the DHCP Client, and which is used for sending DHCP messages out. It can optimize the size based on expected usage and size of the DHCP Client messages.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="de7bf-162">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="de7bf-162">Small Example System</span></span>

<span data-ttu-id="de7bf-163">Przykład użycia NetX Duo przedstawiono na rysunku 1,1 poniżej.</span><span class="sxs-lookup"><span data-stu-id="de7bf-163">An example of how to use NetX Duo is shown in Figure 1.1 below.</span></span> <span data-ttu-id="de7bf-164">Funkcja wpisu wątku aplikacji "*my_thread_entry*" jest tworzona w wierszu 101.</span><span class="sxs-lookup"><span data-stu-id="de7bf-164">The application thread entry function “*my_thread_entry*” is created at line 101.</span></span> <span data-ttu-id="de7bf-165">Po pomyślnym utworzeniu przetwarzanie DHCP jest inicjowane z wywołaniem *nx_dhcp_start* w wierszu 108.</span><span class="sxs-lookup"><span data-stu-id="de7bf-165">After successful creation, DHCP processing is initiated with the *nx_dhcp_start* call at line 108.</span></span> <span data-ttu-id="de7bf-166">W tym momencie zadanie wątku klienta DHCP oddzielnie próbuje skontaktować się z serwerem DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-166">At this point, the DHCP Client thread task separately attempts to contact a DHCP server.</span></span> <span data-ttu-id="de7bf-167">W trakcie tego procesu kod aplikacji czeka na zarejestrowanie prawidłowego adresu IP w wystąpieniu IP przy użyciu usługi *nx_ip_status_check* (lub *nx_ip_interface_status_check* dla pomocniczego interfejsu) w wierszu 95.</span><span class="sxs-lookup"><span data-stu-id="de7bf-167">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) on line 95.</span></span> <span data-ttu-id="de7bf-168">Jest to bardziej często wykonywane w pętli z krótszą opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="de7bf-168">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="de7bf-169">Po wierszu 127 usługa DHCP odebrała prawidłowy adres IP, a następnie może działać, wykorzystując usługi NetX Duo TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-169">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX Duo TCP/IP services as desired.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a><span data-ttu-id="de7bf-170">Środowiska z obsługą wielu serwerów</span><span class="sxs-lookup"><span data-stu-id="de7bf-170">Multi-Server Environments</span></span>

<span data-ttu-id="de7bf-171">W sieciach, w których istnieje więcej niż jeden serwer DHCP, klient DHCP akceptuje pierwszy odebrany komunikat oferty serwera DHCP, postępuje zgodnie ze stanem żądania i ignoruje wszelkie inne odebrane oferty.</span><span class="sxs-lookup"><span data-stu-id="de7bf-171">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="de7bf-172">Sondy protokołu ARP</span><span class="sxs-lookup"><span data-stu-id="de7bf-172">ARP Probes</span></span>

<span data-ttu-id="de7bf-173">Klienta DHCP można skonfigurować tak, aby wysyłał co najmniej jedną sondę protokołu ARP po przypisaniu adresu IP z serwera DHCP w celu sprawdzenia, czy adres IP nie jest jeszcze używany.</span><span class="sxs-lookup"><span data-stu-id="de7bf-173">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="de7bf-174">Krok sondowania ARP jest zalecany przez RFC 2131 i jest szczególnie istotny w środowiskach z więcej niż jednym serwerem DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-174">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="de7bf-175">Jeśli aplikacja hosta włącza opcję NX_DHCP_CLIENT_SEND_ARP_PROBE (zobacz **Opcje konfiguracji** w rozdziale dwa w przypadku dodatkowych opcji sondowania ARP), klient DHCP wyśle sondę ARP "z własnymi żądaniami" i poczeka przez określony czas na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="de7bf-175">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="de7bf-176">Jeśli żaden nie zostanie odebrany, klient DHCP postępuje ze stanem związanym.</span><span class="sxs-lookup"><span data-stu-id="de7bf-176">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="de7bf-177">W przypadku odebrania odpowiedzi klient DHCP zakłada, że adres jest już używany.</span><span class="sxs-lookup"><span data-stu-id="de7bf-177">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="de7bf-178">Automatycznie wysyła komunikat odrzucania do serwera i ponownie inicjuje klienta, aby ponownie uruchomić sondy DHCP ze stanu INIT.</span><span class="sxs-lookup"><span data-stu-id="de7bf-178">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="de7bf-179">Spowoduje to ponowne uruchomienie komputera stanu DHCP, a klient wysyła do serwera inny komunikat ODNAJDOWAnia.</span><span class="sxs-lookup"><span data-stu-id="de7bf-179">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="de7bf-180">Protokół BOOTP</span><span class="sxs-lookup"><span data-stu-id="de7bf-180">BOOTP Protocol</span></span>

<span data-ttu-id="de7bf-181">Klient DHCP obsługuje również protokół BOOTP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-181">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="de7bf-182">Aby włączyć tę opcję i użyć protokołu BOOTP zamiast DHCP, aplikacja hosta musi ustawić opcję konfiguracji NX_DHCP_BOOTP_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="de7bf-182">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="de7bf-183">Aplikacja hosta może nadal żądać określonych adresów IP w protokole BOOTP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-183">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="de7bf-184">Klient DHCP nie obsługuje jednak ładowania systemu operacyjnego hosta, ponieważ protokół BOOTP jest czasami używany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="de7bf-184">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="de7bf-185">Protokół DHCP w interfejsie pomocniczym</span><span class="sxs-lookup"><span data-stu-id="de7bf-185">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="de7bf-186">Klient DHCP NetX Duo można uruchomić na interfejsach pomocniczych, a nie w domyślnym interfejsie głównym.</span><span class="sxs-lookup"><span data-stu-id="de7bf-186">The NetX Duo DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="de7bf-187">Aby uruchomić klienta DHCP z systemem NetX Duo w dodatkowym interfejsie sieciowym, aplikacja hosta musi ustawić indeks interfejsu klienta DHCP na pomocniczy interfejs przy użyciu usługi interfejsu API *nx_dhcp_set_interface_index* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-187">To run NetX Duo DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="de7bf-188">Interfejs musi być już dołączony do podstawowego interfejsu sieciowego przy użyciu usługi *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-188">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="de7bf-189">Więcej informacji na temat dołączania interfejsów pomocniczych można znaleźć w podręczniku użytkownika NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="de7bf-189">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="de7bf-190">Poniżej znajduje się przykładowy system (rysunek 1,2), w którym aplikacja hosta nawiązuje połączenie z serwerem DHCP w interfejsie pomocniczym.</span><span class="sxs-lookup"><span data-stu-id="de7bf-190">Below is an example system (Figure 1.2) in which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="de7bf-191">W wierszu 65 pomocniczy interfejs jest dołączany do zadania IP z adresem IP o wartości null.</span><span class="sxs-lookup"><span data-stu-id="de7bf-191">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="de7bf-192">W wierszu 104 po utworzeniu wystąpienia klienta DHCP indeks interfejsu klienta DHCP jest ustawiony na 1 (np. przesunięcie od podstawowego interfejsu, który sam jest indeksem 0) przez wywołanie *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="de7bf-192">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="de7bf-193">Następnie klient DHCP jest gotowy do uruchomienia w wierszu 108.</span><span class="sxs-lookup"><span data-stu-id="de7bf-193">Then the DHCP Client is ready to be started in line 108.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="de7bf-194">Klient DHCP w wielu interfejsach jednocześnie</span><span class="sxs-lookup"><span data-stu-id="de7bf-194">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="de7bf-195">Aby uruchomić klienta DHCP na wielu interfejsach, NX_MAX_PHYSICAL_INTERFACES w *nx_api. h* musi być ustawiona na liczbę fizycznych interfejsów podłączonych do urządzenia.</span><span class="sxs-lookup"><span data-stu-id="de7bf-195">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="de7bf-196">Domyślnie ta wartość jest równa 1 (np. podstawowy interfejs).</span><span class="sxs-lookup"><span data-stu-id="de7bf-196">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="de7bf-197">Aby zarejestrować dodatkowy interfejs w wystąpieniu protokołu IP, Użyj usługi *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-197">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="de7bf-198">Więcej informacji na temat dołączania interfejsów pomocniczych można znaleźć w podręczniku użytkownika NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="de7bf-198">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="de7bf-199">Następnym krokiem jest ustawienie NX_DHCP_CLIENT_MAX_RECORDS w *nxd_dhcp_client. h* na maksymalną liczbę interfejsów oczekiwanych na równoczesne uruchomienie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-199">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nxd_dhcp_client.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="de7bf-200">Należy pamiętać, że NX_DHCP_CLIENT_MAX_RECORDS nie muszą być równe NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="de7bf-200">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="de7bf-201">Na przykład NX_MAX_PHYSICAL_INTERFACES może mieć wartość 3 i NX_DHCP_CLIENT_MAX_RECORDS równe 2.</span><span class="sxs-lookup"><span data-stu-id="de7bf-201">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="de7bf-202">W tej konfiguracji tylko dwa interfejsy (i mogą być dowolne dwa z trzech interfejsów fizycznych w dowolnym momencie) spośród trzech interfejsów fizycznych można w dowolnym momencie uruchomić usługę DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-202">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="de7bf-203">Rekordy klienta DHCP nie mają mapowania jeden do jednego do interfejsów sieciowych, np. rekord klienta 1 nie jest automatycznie skorelowany z indeksem interfejsu fizycznego 1.</span><span class="sxs-lookup"><span data-stu-id="de7bf-203">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="de7bf-204">NX_DHCP_CLIENT_MAX_RECORDS można również ustawić na wartość większą niż NX_MAX_PHYSICAL_INTERFACES, ale spowoduje to utworzenie nieużywanych rekordów klienta i niewydajne użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="de7bf-204">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="de7bf-205">Aby można było uruchomić protokół DHCP w dowolnym interfejsie, aplikacja musi włączyć te interfejsy, wywołując *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="de7bf-205">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="de7bf-206">Należy zauważyć, że wyjątek jest interfejsem podstawowym, który jest automatycznie włączany w wywołaniu *nx_dhcp_create* (i które można wyłączyć za pomocą usługi *nx_dhcp_interface_disable* opisanej poniżej).</span><span class="sxs-lookup"><span data-stu-id="de7bf-206">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="de7bf-207">W dowolnym momencie można wyłączyć interfejs DHCP lub można zatrzymać protokół DHCP niezależnie od innych interfejsów z uruchomionym protokołem DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-207">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="de7bf-208">Jak wspomniano powyżej, aby włączyć określony interfejs dla usługi DHCP, należy użyć usługi *nx_dhcp_interface_enable* i określić indeks interfejsu fizycznego w argumencie wejściowym.</span><span class="sxs-lookup"><span data-stu-id="de7bf-208">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="de7bf-209">Można włączyć do NX_DHCP_CLIENT_MAX_RECORDS interfejsów z jedynym ograniczeniem, że argument wejściowy indeksu interfejsu jest krótszy niż NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="de7bf-209">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="de7bf-210">Aby uruchomić protokół DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_start* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-210">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="de7bf-211">Aby uruchomić protokół DHCP we wszystkich włączonych interfejsach, Użyj usługi *nx_dhcp_start* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-211">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="de7bf-212">(Interfejsy, które już uruchomiły protokół DHCP, nie będą miały wpływ na *nx_dhcp_start*).</span><span class="sxs-lookup"><span data-stu-id="de7bf-212">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="de7bf-213">Aby zatrzymać usługę DHCP w interfejsie, Użyj usługi *nx_dhcp_interface_stop* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-213">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="de7bf-214">Protokół DHCP musi już być uruchomiony w tym interfejsie lub zwracany jest stan błędu.</span><span class="sxs-lookup"><span data-stu-id="de7bf-214">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="de7bf-215">Aby zatrzymać protokół DHCP we wszystkich włączonych interfejsach, Użyj usługi *nx_dhcp_stop* .</span><span class="sxs-lookup"><span data-stu-id="de7bf-215">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="de7bf-216">Protokół DHCP można zatrzymać niezależnie od innych interfejsów w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="de7bf-216">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="de7bf-217">Większość istniejących usług klienta DHCP ma odpowiednik "Interface", np. *nx_dhcp_interface_release* jest odpowiednikiem określonego interfejsu *nx_dhcp_release.*</span><span class="sxs-lookup"><span data-stu-id="de7bf-217">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="de7bf-218">Jeśli klient DHCP jest skonfigurowany dla jednego interfejsu, wykonuje tę samą akcję.</span><span class="sxs-lookup"><span data-stu-id="de7bf-218">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="de7bf-219">Należy pamiętać, że usługi klienta DHCP niezwiązane z interfejsem zwykle mają zastosowanie do wszystkich interfejsów, ale nie wszystkich.</span><span class="sxs-lookup"><span data-stu-id="de7bf-219">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="de7bf-220">W tym drugim przypadku usługa niezależna od interfejsu dotyczy pierwszego interfejsu z włączonym protokołem DHCP, który znajduje się w przeszukiwaniu listy klientów DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-220">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="de7bf-221">Zobacz **Opis usług** w rozdziale trzeci, w jaki sposób usługa niezależna od interfejsu jest wykonywana w przypadku włączenia wielu interfejsów dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-221">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="de7bf-222">W przykładowej sekwencji poniżej wystąpienie protokołu IP ma dwa interfejsy sieciowe i najpierw uruchamia DHCP w interfejsie pomocniczym.</span><span class="sxs-lookup"><span data-stu-id="de7bf-222">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="de7bf-223">W pewnym momencie później zostanie uruchomiony protokół DHCP w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="de7bf-223">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="de7bf-224">Następnie zwalnia adres IP w interfejsie podstawowym i ponownie uruchamia DHCP w interfejsie głównym:</span><span class="sxs-lookup"><span data-stu-id="de7bf-224">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

<span data-ttu-id="de7bf-225">Aby uzyskać pełną listę specyficznych dla interfejsu usług, zobacz **Opis usług** w rozdziale 3.</span><span class="sxs-lookup"><span data-stu-id="de7bf-225">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="de7bf-226">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="de7bf-226">Configuration Options</span></span>

<span data-ttu-id="de7bf-227">Użytkownik konfigurowalny opcje DHCP w *nxd_dhcp_client. h* zezwala aplikacji hosta na precyzyjne dopasowanie klienta DHCP do określonych wymagań.</span><span class="sxs-lookup"><span data-stu-id="de7bf-227">User configurable DHCP options in *nxd_dhcp_client.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="de7bf-228">Poniżej znajduje się lista tych parametrów:</span><span class="sxs-lookup"><span data-stu-id="de7bf-228">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="de7bf-229">**NX_DHCP_ENABLE_BOOTP**: zdefiniowane, ta opcja włącza protokół BOOTP zamiast DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-229">**NX_DHCP_ENABLE_BOOTP**: Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="de7bf-230">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-230">By default this option is disabled.</span></span>
- <span data-ttu-id="de7bf-231">**NX_DHCP_CLIENT_RESTORE_STATE**: Jeśli jest zdefiniowany, umożliwia klientowi DHCP zapisanie bieżącej licencji klienta DHCP, w tym pozostały czas w dzierżawie, i przywrócenie tego stanu między ponownymi uruchomieniami aplikacji klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-231">**NX_DHCP_CLIENT_RESTORE_STATE**: If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="de7bf-232">Wartość domyślna jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-232">The default value is disabled.</span></span>
- <span data-ttu-id="de7bf-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: w przypadku ustawienia Klient DHCP nie będzie tworzyć własnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="de7bf-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="de7bf-234">Aplikacja hosta musi używać usługi *nx_dhcp_packet_pool_set* , aby ustawić pulę pakietów klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-234">The host application must use the *nx_dhcp_packet_pool_set* service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="de7bf-235">Wartość domyślna jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-235">The default value is disabled.</span></span>
- <span data-ttu-id="de7bf-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: zdefiniowane, umożliwia klientowi DHCP wysyłanie sondy ARP po przypisaniu adresów IP w celu sprawdzenia, czy przypisany adres DHCP nie jest własnością innego hosta.</span><span class="sxs-lookup"><span data-stu-id="de7bf-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="de7bf-237">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-237">By default, this option is disabled.</span></span>
- <span data-ttu-id="de7bf-238">**NX_DHCP_ARP_PROBE_WAIT**: określa, jak długo klient DHCP czeka na odpowiedź po wysłaniu sondy ARP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-238">**NX_DHCP_ARP_PROBE_WAIT**: Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="de7bf-239">Wartość domyślna to jedna sekunda (1 \* NX_IP_PERIODIC_RATE)</span><span class="sxs-lookup"><span data-stu-id="de7bf-239">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>
- <span data-ttu-id="de7bf-240">**NX_DHCP_ARP_PROBE_MIN**: Określa minimalną zmianę interwału między wysłaniem SOND protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-240">**NX_DHCP_ARP_PROBE_MIN**: Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="de7bf-241">Wartość jest domyślnie równa 1 sekunda.</span><span class="sxs-lookup"><span data-stu-id="de7bf-241">The value is defaulted to 1 second.</span></span>
- <span data-ttu-id="de7bf-242">**NX_DHCP_ARP_PROBE_MAX**: określa maksymalną liczbę zmian w interwale między wysłaniem SOND protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-242">**NX_DHCP_ARP_PROBE_MAX**: Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="de7bf-243">Wartość jest domyślnie równa 2 sekund.</span><span class="sxs-lookup"><span data-stu-id="de7bf-243">The value is defaulted to 2 seconds.</span></span>
- <span data-ttu-id="de7bf-244">**NX_DHCP_ARP_PROBE_NUM**: określa liczbę sond protokołu ARP wysyłanych do określenia, czy adres IP przypisany przez serwer DHCP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="de7bf-244">**NX_DHCP_ARP_PROBE_NUM**: Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="de7bf-245">Wartość jest domyślnie równa 3 sondy.</span><span class="sxs-lookup"><span data-stu-id="de7bf-245">The value is defaulted to 3 probes.</span></span>
- <span data-ttu-id="de7bf-246">**NX_DHCP_RESTART_WAIT**: określa, kiedy klient DHCP ma czekać na ponowne uruchomienie usługi DHCP, jeśli adres IP przypisany do klienta DHCP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="de7bf-246">**NX_DHCP_RESTART_WAIT**: Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="de7bf-247">Wartość jest domyślnie równa 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="de7bf-247">The value is defaulted to 10 seconds.</span></span>
- <span data-ttu-id="de7bf-248">**NX_DHCP_CLIENT_MAX_RECORDS**: określa maksymalną liczbę rekordów interfejsów do zapisania w wystąpieniu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-248">**NX_DHCP_CLIENT_MAX_RECORDS**: Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="de7bf-249">Rekord interfejsu klienta DHCP jest rekordem klienta DHCP działającego w określonym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="de7bf-249">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="de7bf-250">Wartość domyślna jest ustawiana jako liczba interfejsów fizycznych (NX_MAX_PHYSICAL_INTERFACES).</span><span class="sxs-lookup"><span data-stu-id="de7bf-250">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>
- <span data-ttu-id="de7bf-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: zdefiniowane, umożliwia klientowi DHCP wysyłanie maksymalnej wielkości komunikatu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="de7bf-252">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-252">By default, this option is disabled.</span></span>
- <span data-ttu-id="de7bf-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: zdefiniowane, umożliwia klientowi DHCP sprawdzenie nazwy wejściowego hosta w wywołaniu nx_dhcp_create w przypadku nieprawidłowych znaków lub długości.</span><span class="sxs-lookup"><span data-stu-id="de7bf-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="de7bf-254">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="de7bf-254">By default, this option is disabled.</span></span>
- <span data-ttu-id="de7bf-255">**NX_DHCP_THREAD_PRIORITY**: priorytet wątku DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-255">**NX_DHCP_THREAD_PRIORITY**: Priority of the DHCP thread.</span></span> <span data-ttu-id="de7bf-256">Domyślnie ta wartość określa, że wątek DHCP działa z priorytetem 3.</span><span class="sxs-lookup"><span data-stu-id="de7bf-256">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>
- <span data-ttu-id="de7bf-257">**NX_DHCP_THREAD_STACK_SIZE**: rozmiar stosu wątków DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-257">**NX_DHCP_THREAD_STACK_SIZE**: Size of the DHCP thread stack.</span></span> <span data-ttu-id="de7bf-258">Domyślnie rozmiar to 2048 bajtów.</span><span class="sxs-lookup"><span data-stu-id="de7bf-258">By default, the size is 2048 bytes.</span></span>
- <span data-ttu-id="de7bf-259">**NX_DHCP_TIME_INTERVAL**: interwał (w sekundach), po którym jest wykonywana funkcja wygaśnięcia czasomierza klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-259">**NX_DHCP_TIME_INTERVAL**: Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="de7bf-260">Ta funkcja aktualizuje wszystkie limity czasu w procesie DHCP, np. w przypadku, gdy komunikaty powinny być ponownie przesyłane lub stan klienta DHCP uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="de7bf-260">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="de7bf-261">Domyślnie ta wartość jest równa 1 sekunda.</span><span class="sxs-lookup"><span data-stu-id="de7bf-261">By default, this value is 1 second.</span></span>
- <span data-ttu-id="de7bf-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: rozmiar buforu opcji DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: Size of DHCP options buffer.</span></span> <span data-ttu-id="de7bf-263">Wartość domyślna to 312 bajtów.</span><span class="sxs-lookup"><span data-stu-id="de7bf-263">By default, this value is 312 bytes.</span></span>
- <span data-ttu-id="de7bf-264">**NX_DHCP_PACKET_PAYLOAD**: Określa rozmiar w bajtach ładunku pakietu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-264">**NX_DHCP_PACKET_PAYLOAD**: Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="de7bf-265">Wartość domyślna to NX_DHCP_MINIMUM_IP_DATAGRAM + rozmiar nagłówka fizycznego.</span><span class="sxs-lookup"><span data-stu-id="de7bf-265">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="de7bf-266">Rozmiar nagłówka fizycznego w sieci wireline jest zwykle rozmiarem ramki sieci Ethernet.</span><span class="sxs-lookup"><span data-stu-id="de7bf-266">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>
- <span data-ttu-id="de7bf-267">**NX_DHCP_PACKET_POOL_SIZE**: Określa rozmiar puli pakietów klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-267">**NX_DHCP_PACKET_POOL_SIZE**: Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="de7bf-268">Wartość domyślna to (5 \* NX_DHCP_PACKET_PAYLOAD), która zapewni cztery pakiety Plus pomieszczenie dla obciążenia wewnętrznej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="de7bf-268">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>
- <span data-ttu-id="de7bf-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: Określa minimalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed ponownym przesłaniem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de7bf-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="de7bf-270">Wartość domyślna to RFC 2131 zalecane 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="de7bf-270">The default value is the RFC 2131 recommended 4 seconds.</span></span>
- <span data-ttu-id="de7bf-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: określa maksymalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed ponownym przesłaniem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de7bf-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="de7bf-272">Wartość domyślna to 64 sekund.</span><span class="sxs-lookup"><span data-stu-id="de7bf-272">The default value is 64 seconds.</span></span>
- <span data-ttu-id="de7bf-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: określa opcję minimalnej oczekiwania w przypadku odebrania komunikatu serwera DHCP i wysłania żądania odnowienia po powiązaniu klienta DHCP z adresem IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="de7bf-274">Wartość domyślna to 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="de7bf-274">The default value is 60 seconds.</span></span> <span data-ttu-id="de7bf-275">Jednak klient DHCP używa odnawiania i ponownego powiązania czasu wygaśnięcia z komunikatów serwera DHCP przed ustawieniem minimalny limit czasu odnawiania.</span><span class="sxs-lookup"><span data-stu-id="de7bf-275">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>
- <span data-ttu-id="de7bf-276">**NX_DHCP_TYPE_OF_SERVICE**: typ usługi wymaganej przez żądania UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-276">**NX_DHCP_TYPE_OF_SERVICE**: Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="de7bf-277">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-277">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="de7bf-278">**NX_DHCP_FRAGMENT_OPTION**: włączono fragment dla żądań UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-278">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="de7bf-279">Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentację protokołu UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="de7bf-279">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>
- <span data-ttu-id="de7bf-280">**NX_DHCP_TIME_TO_LIVE**: określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="de7bf-280">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="de7bf-281">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="de7bf-281">The default value is set to 0x80.</span></span>
- <span data-ttu-id="de7bf-282">**NX_DHCP_QUEUE_DEPTH**: określa maksymalną głębokość kolejki odbioru.</span><span class="sxs-lookup"><span data-stu-id="de7bf-282">**NX_DHCP_QUEUE_DEPTH**: Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="de7bf-283">Wartość domyślna to 4.</span><span class="sxs-lookup"><span data-stu-id="de7bf-283">The default value is set to 4.</span></span>